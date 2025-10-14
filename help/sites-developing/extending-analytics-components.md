---
title: Adobe Analytics-tracking toevoegen aan componenten
description: Leer hoe u Adobe Analytics Tracking toevoegt aan componenten in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: e6c1258c-81d5-48e4-bdf1-90d7cc13a22d
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Developer
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1244'
ht-degree: 0%

---

# Adobe Analytics-tracking toevoegen aan componenten{#adding-adobe-analytics-tracking-to-components}

## De Adobe Analytics-module opnemen in een pagina-component {#including-the-adobe-analytics-module-in-a-page-component}

De componenten van het paginasjabloon (bijvoorbeeld, `head.jsp, body.jsp`) hebben JSP omvat nodig om ContextHub en de integratie van Adobe Analytics (die een deel van Cloud Servicen is) te laden. Alles omvat ook JavaScript-bestanden laden.

Het ContextHub-item moet direct onder de tag `<head>` worden opgenomen, terwijl Cloud Servicen in de sectie `<head>` en voor de sectie `</body>` moeten worden opgenomen, bijvoorbeeld:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
...
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
...
</head>
<body>
...
    <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
</body>
```

Het `contexthub` -script dat u invoegt na het `<head>` -element voegt de ContextHub-functies toe aan de pagina.

De `cloudservices` -scripts die u in de secties `<head>` en `<body>` toevoegt, zijn van toepassing op de configuraties van de cloudservices die aan de pagina worden toegevoegd. (Als de pagina meer dan één configuratie van Cloud Servicen gebruikt, moet u ContextHub jsp en de Cloud Servicen jsp slechts eenmaal omvatten.)

Wanneer een Adobe Analytics-framework aan de pagina wordt toegevoegd, genereren de `cloudservices` -scripts Adobe Analytics-gerelateerde JavaScript en verwijzingen naar client-side bibliotheken, net als in het volgende voorbeeld:

```xml
<div class="sitecatalyst cloudservice">
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/util.js"></script>
<script type="text/javascript" src="/content/geometrixx-outdoors/_jcr_content/analytics.sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/mac/mac-sc.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/plugins.js"></script>
<script type="text/javascript">
<!--
CQ_Analytics.Sitecatalyst.frameworkComponents = ['foundation/components/page'];
/**
 * Sets Adobe Analytics variables accordingly to mapped components. If <code>options</code>
 * object is provided only variables matching the options.componentPath are set.
 *
 * @param {Object} options Parameter object from CQ_Analytics.record() call. Optional.
 */
CQ_Analytics.Sitecatalyst.updateEvars = function(options) {
    this.frameworkMappings = [];
 this.frameworkMappings.push({scVar:"pageName",cqVar:"pagedata.title",resourceType:"foundation/components/page"});
    for (var i=0; i<this.frameworkMappings.length; i++){
  var m = this.frameworkMappings[i];
  if (!options || options.compatibility || (options.componentPath == m.resourceType)) {
   CQ_Analytics.Sitecatalyst.setEvar(m);
  }
    }
}

CQ_Analytics.CCM.addListener("storesinitialize", function(e) {
 var collect = true;
    var lte = s.linkTrackEvents;
    s.pageName="content:geometrixx-outdoors:en";
    CQ_Analytics.Sitecatalyst.collect(collect);
    if (collect) {
  CQ_Analytics.Sitecatalyst.updateEvars();
     /************* DO NOT ALTER ANYTHING BELOW THIS LINE ! **************/
     var s_code=s.t();if(s_code)document.write(s_code);
     s.linkTrackEvents = lte;
     if(s.linkTrackVars.indexOf('events')==-1){delete s.events};
     $CQ(document).trigger("sitecatalystAfterCollect");
    }
});
//-->
</script>
<script type="text/javascript">
<!--
if(navigator.appVersion.indexOf('MSIE')>=0)document.write(unescape('%3C')+'\!-'+'-')
//-->
</script>
<noscript><img src="https://daydocumentation.112.2o7.net/b/ss/daydocumentation/1/H.25--NS/1380120772954?cdp=3&gn=content%3Ageometrixx-outdoors%3Aen" height="1" width="1" border="0" alt=""/></noscript>
<span data-tracking="{event:'pageView', values:{}, componentPath:'foundation/components/page'}"></span>
<div id="cq-analytics-texthint" style="background:white; padding:0 10px; display:none;">
 <h3 class="cq-texthint-placeholder">Component clientcontext is missing or misplaced.</h3>
</div>
<script type="text/javascript">
$CQ(function(){
 if( CQ_Analytics &&
  CQ_Analytics.ClientContextMgr &&
  !CQ_Analytics.ClientContextMgr.isConfigLoaded )
  {
   $CQ("#cq-analytics-texthint").show();
  }
});
</script>
</div>
```

Deze code is opgenomen in alle AEM voorbeeldsites, zoals Geometrixx Outdoors.

### De gebeurtenis sitecatalystAfterCollect {#the-sitecatalystaftercollect-event}

Het script `cloudservices` activeert de gebeurtenis `sitecatalystAfterCollect` :

```
$CQ(document).trigger("sitecatalystAfterCollect");
```

Deze gebeurtenis wordt geactiveerd om aan te geven dat het bijhouden van pagina&#39;s is voltooid. Als u aanvullende traceringsbewerkingen uitvoert op deze pagina, moet u naar deze gebeurtenis luisteren in plaats van naar de gebeurtenis document laden of document gereed. Met de gebeurtenis `sitecatalystAfterCollect` vermijdt u botsingen of ander onvoorspelbaar gedrag.

>[!NOTE]
>
>De `/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js` -bibliotheek bevat de code uit het Adobe Analytics `s_code.js` -bestand.

## Adobe Analytics-tracking voor aangepaste componenten implementeren {#implementing-adobe-analytics-tracking-for-custom-components}

Laat uw AEM componenten toe om met het kader van Adobe Analytics in wisselwerking te staan. Configureer vervolgens uw framework zodat Adobe Analytics de componentgegevens bijhoudt.

Componenten die met het Adobe Analytics-framework werken, worden in de Sidekick weergegeven wanneer u een framework bewerkt. Nadat u de component naar het framework hebt gesleept, worden de componenteigenschappen weergegeven en kunt u deze vervolgens toewijzen met Adobe Analytics-eigenschappen. (Zie [&#x200B; Vestiging een Kader voor Basis het Volgen &#x200B;](/help/sites-administering/adobeanalytics-connect.md#creating-a-adobe-analytics-framework).)

Componenten kunnen communiceren met het Adobe Analytics-framework wanneer de component een onderliggende node heeft met de naam `analytics` . Het knooppunt `analytics` heeft de volgende eigenschappen:

* `cq:trackevents`: identificeert de CQ-gebeurtenissen die de component beschikbaar maakt. (Zie Aangepaste gebeurtenissen.)
* `cq:trackvars`: geeft de CQ-variabelen een naam die zijn toegewezen aan Adobe Analytics-eigenschappen.
* `cq:componentName`: De naam voor de component die in Sidekick wordt weergegeven.
* `cq:componentGroup`: De groep in Sidekick die de component bevat.

De code in de component JSP voegt de JavaScript toe aan de pagina die het bijhouden activeert en definieert de gegevens die worden bijgehouden. De naam van de gebeurtenis en de gegevensnamen die in de JavaScript worden gebruikt, moeten overeenkomen met de corresponderende waarden van de eigenschappen van het knooppunt `analytics` .

* Gebruik het kenmerk voor het bijhouden van gegevens om gebeurtenisgegevens bij te houden wanneer een pagina wordt geladen. (Zie [&#x200B; het Volgen de Gebeurtenissen van de Douane op de Lading van de Pagina &#x200B;](/help/sites-developing/extending-analytics.md#tracking-custom-events-on-page-load).)
* Gebruik de functie CQ_Analytics.record om gebeurtenisgegevens bij te houden wanneer gebruikers met paginafuncties werken. (Zie [&#x200B; het Volgen de Gebeurtenissen van de Douane na de Lading van de Pagina &#x200B;](/help/sites-developing/extending-analytics.md#tracking-custom-events-after-page-load).)

Wanneer u deze gegevens-volgende methodes gebruikt, voert de de integratiemodule van Adobe Analytics automatisch de vraag aan Adobe Analytics uit om de gebeurtenissen en de gegevens te registreren.

### Voorbeeld: klikken op topnav bijhouden {#example-tracking-topnav-clicks}

Breid de stichting uit topnav component zodat de sporen van Adobe Analytics op navigatiekoppelingen bij de bovenkant van de pagina klikken. Wanneer op een navigatiekoppeling wordt geklikt, registreert Adobe Analytics de koppeling waarop is geklikt en de pagina waarop erop is geklikt.

De volgende procedures vereisen dat u reeds de volgende taken hebt uitgevoerd:

* Een CQ-toepassing gemaakt.
* Adobe Analytics Configuration and an Adobe Analytics Framework.

#### De bovenste component kopiëren {#copy-the-topnav-component}

Kopieer de bovenste component naar de CQ-toepassing. De procedure vereist dat uw toepassing is ingesteld in CRXDE Lite.

1. Klik met de rechtermuisknop op het knooppunt `/libs/foundation/components/topnav` en klik op Copy.
1. Klik met de rechtermuisknop op de map Components onder de toepassingsmap en klik op Plakken.
1. Klik op Alles opslaan.

#### Integratie van topnav met het Adobe Analytics-kader {#integrating-topnav-with-the-adobe-analytics-framework}

Configureer de component topnav en bewerk het JSP-bestand om de volgende gebeurtenissen en gegevens te definiëren.

1. Klik met de rechtermuisknop op het bovenste knooppunt en klik op Maken > Node maken. Geef de volgende eigenschapswaarden op en klik op OK:

   * Naam: `analytics`
   * Type: `nt:unstructured`

1. Voeg de volgende eigenschap toe aan het analytische knooppunt zodat u de gebeurtenis tracking een naam kunt geven:

   * Naam: cq:trackevents
   * Type: String
   * Waarde: topnavClick

1. Voeg de volgende eigenschap toe aan het knooppunt Analytics, zodat u de gegevensvariabelen een naam kunt geven:

   * Naam: cq:trackvars
   * Type: String
   * Waarde: topnavTarget,topnavLocation

1. Voeg het volgende bezit aan de analytische knoop toe om de component voor Sidekick te noemen:

   * Naam: cq:componentName
   * Type: String
   * Waarde: topnav (tracking)

1. Voeg het volgende bezit aan de analytische knoop toe om de componentengroep voor Sidekick te noemen:

   * Naam: cq:componentGroup
   * Type: String
   * Waarde: Algemeen

1. Klik op Alles opslaan.
1. Open het `topnav.jsp` -bestand.
1. Voeg in het element het volgende kenmerk toe:

   ```xml
   onclick = "tracknav('<%= child.getPath() %>.html')"
   ```

1. Voeg onder aan de pagina de volgende JavaScript-code toe:

   ```xml
   <script type="text/javascript">
       function tracknav(target) {
               if (CQ_Analytics.Sitecatalyst) {
                   CQ_Analytics.record({
                       event: 'topnavClick',
                       values: {
                           topnavTarget: target,
                           topnavLocation:'<%=currentPage.getPath() %>.html'
                       },
                       componentPath: '<%=resource.getResourceType()%>'
                   });
               }
       }
   </script>
   ```

1. Klik op Alles opslaan.

De inhoud van het bestand `topnav.jsp` moet er als volgt uitzien:

```xml
<%@page session="false"%><%--
  Copyright 1997-2008 Day Management AG
  Barfuesserplatz 6, 4001 Basel, Switzerland
  All Rights Reserved.

  This software is the confidential and proprietary information of
  Day Management AG ("Confidential Information"). You shall not
  disclose such Confidential Information and shall use it only in
  accordance with the terms of the license agreement you entered into
  with Day.

  ==============================================================================

  Top Navigation component

  Draws the top navigation

--%><%@include file="/libs/foundation/global.jsp"%><%
%><%@ page import="java.util.Iterator,
        com.day.text.Text,
        com.day.cq.wcm.api.PageFilter,
        com.day.cq.wcm.api.Page,
        com.day.cq.commons.Doctype,
        org.apache.commons.lang3.StringEscapeUtils" %><%

    // get starting point of navigation
    long absParent = currentStyle.get("absParent", 2L);
    String navstart = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);

    //if not deep enough take current node
    if (navstart.equals("")) navstart=currentPage.getPath();

    Resource rootRes = slingRequest.getResourceResolver().getResource(navstart);
    Page rootPage = rootRes == null ? null : rootRes.adaptTo(Page.class);
    String xs = Doctype.isXHTML(request) ? "/" : "";
    if (rootPage != null) {
        Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
        while (children.hasNext()) {
            Page child = children.next();
            %><a onclick = "tracknav('<%= child.getPath() %>.html')"  href="<%= child.getPath() %>.html"><%
            %><img alt="<%= StringEscapeUtils.escapeXml(child.getTitle()) %>" src="<%= child.getPath() %>.navimage.png"<%= xs %>></a><%
        }
    }
%><script type="text/javascript">
    function tracknav(target) {
            if (CQ_Analytics.Sitecatalyst) {
                CQ_Analytics.record({
                    event: 'topnavClick',
                    values: {
                        topnavTarget:target,
                        topnavLocation:'<%=currentPage.getPath() %>.html'
                    },
                    componentPath: '<%=resource.getResourceType()%>'
                });
            }
    }
</script>
```

>[!NOTE]
>
>Het is vaak wenselijk om gegevens van ContextHub te volgen. Voor informatie over het gebruiken van JavaScript om deze informatie te verkrijgen, zie [&#x200B; Toegang hebbend tot Waarden in ContextHub &#x200B;](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).

#### De volgende component toevoegen aan de Sidekick {#adding-the-tracking-component-to-sidekick}

Voeg componenten die voor het volgen met Adobe Analytics aan Sidekick worden toegelaten zodat u hen aan uw kader kunt toevoegen.

1. Open uw Adobe Analytics-framework vanuit uw Adobe Analytics-configuratie. ([&#x200B; http://localhost:4502/etc/cloudservices/sitecatalyst.html](http://localhost:4502/etc/cloudservices/sitecatalyst.html))
1. Klik in de Sidekick op de knop Ontwerpen.

   ![&#x200B; de knoop van het Ontwerp die een juist-hoekvierkant kenmerkt.](assets/chlimage_1a.png)

1. In het gebied van de Configuratie van het Volgen van de Verbinding, vormt de klik Overerving.

   ![&#x200B; chlimage_1 &#x200B;](assets/chlimage_1aa.png)

1. Selecteer in de lijst Toegestane componenten de optie Bovenliggend (bijhouden) in de sectie Algemeen en klik vervolgens op OK.
1. Breid Sidekick uit om bewerkingswijze in te gaan. De component is nu beschikbaar in de groep Algemeen.

#### De component topnav toevoegen aan uw framework {#adding-the-topnav-component-to-your-framework}

Sleep de bovenste component naar het Adobe Analytics-framework en wijs de componentvariabelen en -gebeurtenissen toe aan Adobe Analytics-variabelen en -gebeurtenissen. (Zie [&#x200B; Vestiging een Kader voor Basis het Volgen &#x200B;](/help/sites-administering/adobeanalytics-connect.md).)

![&#x200B; chlimage_1-1 &#x200B;](assets/chlimage_1-1a.png)

De bovenstaande component is nu geïntegreerd met het Adobe Analytics-framework. Wanneer u de component aan een pagina toevoegt en op de items in de bovenste navigatiebalk klikt, worden volggegevens naar Adobe Analytics verzonden.

### S.products-gegevens naar Adobe Analytics verzenden {#sending-s-products-data-to-adobe-analytics}

Componenten kunnen gegevens genereren voor de variabele s.products die naar Adobe Analytics wordt verzonden. Ontwerp uw componenten om aan de variabele s.products bij te dragen:

* Neem een waarde op met de naam `product` van een specifieke structuur.
* Stel de leden van de gegevens van de waarde `product` beschikbaar, zodat deze met Adobe Analytics-variabelen in het Adobe Analytics-framework kunnen worden toegewezen.

De variabele Adobe Analytics s.products gebruikt de volgende syntaxis:

```
s.products="category;product;quantity;price;eventY={value}|eventZ={value};evarA={value}|evarB={value}"
```

De Adobe Analytics-integratiemodule maakt de `s.products` -variabele met behulp van de `product` -waarden die AEM componenten genereren. De `product` -waarde in de JavaScript die AEM componenten genereren, is een array van waarden met de volgende structuur:

```
"product": [{
    "category": "",
    "sku"     : "path to product node",
    "quantity": quantity,
    "price"   : price,
    "events   : {
      "eventName1": "eventValue1",
      "eventName_n": "eventValue_n"
    }
    "evars"   : {
      "eVarName1": "eVarValue1",
      "eVarName_n": "eVarValue_n"
    }
}]
```

Wanneer een gegevensitem wordt weggelaten uit de `product` -waarde, wordt het als een lege tekenreeks in s.products verzonden.

>[!NOTE]
>
>Als er geen gebeurtenis aan een productwaarde is gekoppeld, gebruikt Adobe Analytics standaard de gebeurtenis `prodView` .

Het knooppunt `analytics` van de component moet de variabelenamen zichtbaar maken met de eigenschap `cq:trackvars` :

* product.category
* product.sku
* product.quantity
* product.price
* product.events.eventName1
* product.events.eventName_n
* product.evars.eVarName1
* product.evars.eVarName_n

De module eCommerce biedt verschillende componenten die variabele gegevens van s.products genereren. Bijvoorbeeld, produceert de `submitorder` component ([&#x200B; http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp &#x200B;](http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp)) JavaScript die aan het volgende voorbeeld gelijkaardig is:

```
<script type="text/javascript">
    function trackCartPurchase() {
        if (CQ_Analytics.Sitecatalyst) {
            CQ_Analytics.record({
                "event": ["productsCartPurchase"],
                "values": {
                    "product": [
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/1",
                            "quantity": 3,
                            "price"   : 179.7,
                            "evars"   : {
                                "childSku": "/path/to/prod/1/green/xs",
                                "size"    : "XS"
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/2",
                            "quantity": 10,
                            "price"   : 150,
                            "evars"   : {
                                "childSku": "/path/to/prod/2",
                                "size"    : ""
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/3",
                            "quantity": 2,
                            "price"   : 102,
                            "evars"   : {
                                "childSku": "/path/to/prod/3/m",
                                "size"    : "M"
                            }
                        }
                    ]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["discountRedemption"],
                "values": {
                    "discount": "/path/to/discount/1 - /path/to/discount/2",
                    "product" : [{
                        "category": "",
                        "sku"     : "Promotional Discount",
                        "events"  : {"discountRedemption": 20.00}
                    }]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["cartPurchase"],
                "values": {
                    "orderId"       : "00e40e2d-13a2-4a00-a8ee-01a9ebb0bf68",
                    "shippingMethod": "overnight",
                    "paymentMethod" : "Amex",
                    "billingState"  : "NY",
                    "billingZip"    : "10458",
                    "product"       : [{"category": "", "sku": "", "quantity": "", "price": ""}]
                },
                "componentPath": "commerce/components/submitorder"
            });
        }
        return true;
    }
</script>
```

#### Het beperken van de Grootte van het Volgen Vraag {#limiting-the-size-of-tracking-calls}

Webbrowsers beperken doorgaans de grootte van GET-aanvragen. Omdat CQ-product- en SKU-waarden opslagpaden zijn, kunnen productarrays met meerdere waarden de limiet van de aanvraaggrootte overschrijden. Daarom moeten uw componenten het aantal items in de `product` -array van elke `CQ_Analytics.record function` beperken. Maak meerdere functies als het aantal items dat u moet bijhouden de limiet kan overschrijden.

De component eCommerce `submitorder` beperkt bijvoorbeeld het aantal `product` -items in een aanroep tot vier. Wanneer de winkelwagen meer dan vier producten bevat, worden er meerdere `CQ_Analytics.record` -functies gegenereerd.
