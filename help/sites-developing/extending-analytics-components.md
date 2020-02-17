---
title: Adobe Analytics-tracking toevoegen aan componenten
seo-title: Adobe Analytics-tracking toevoegen aan componenten
description: 'null'
seo-description: 'null'
uuid: 447b140c-678c-428d-a1c9-ecbdec75cd42
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: a11c39b4-c23b-4207-8898-33aea25f2ad0
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# Adobe Analytics-tracking toevoegen aan componenten{#adding-adobe-analytics-tracking-to-components}

## De Adobe Analytics-module opnemen in een pagina-component {#including-the-adobe-analytics-module-in-a-page-component}

Componenten van paginasjablonen (bijvoorbeeld `head.jsp, body.jsp`) hebt JSP nodig om de ContextHub en de integratie van de Analytics van Adobe (die deel uitmaakt van de Diensten van de Wolk) te laden. Alles omvat JavaScript-bestanden laden.

De ingang ContextHub zou onmiddellijk onder de `<head>` markering moeten worden omvat, terwijl de Diensten van de Wolk in de `<head>` en vóór de `</body>` sectie zouden moeten worden omvat; bijvoorbeeld:

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

Het `contexthub` manuscript dat u na het `<head>` element opneemt voegt de eigenschappen ContextHub aan de pagina toe.

De `cloudservices` scripts die u in de secties `<head>` en `<body>` secties toevoegt, zijn van toepassing op de configuraties van de cloudservices die aan de pagina worden toegevoegd. (Als de pagina meer dan één configuratie van de Diensten van de Wolk gebruikt, moet u ContextHub jsp en de Diensten van de Wolk slechts eenmaal omvatten.)

Wanneer een Adobe Analytics-framework aan de pagina wordt toegevoegd, genereren de `cloudservices` scripts Adobe Analytics-gerelateerde javascript en verwijzingen naar client-side bibliotheken, vergelijkbaar met het volgende voorbeeld:

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

Deze code is opgenomen op alle AEM-voorbeeldsites, zoals Geometrixx Outdoor.

### De gebeurtenis sitecatalystAfterCollect {#the-sitecatalystaftercollect-event}

Het `cloudservices` script activeert de `sitecatalystAfterCollect` gebeurtenis:

```
$CQ(document).trigger("sitecatalystAfterCollect");
```

Deze gebeurtenis wordt geactiveerd om aan te geven dat het bijhouden van pagina&#39;s is voltooid. Als u aanvullende traceringsbewerkingen uitvoert op deze pagina, moet u naar deze gebeurtenis luisteren in plaats van naar de gebeurtenis document laden of document gereed. Met de `sitecatalystAfterCollect` gebeurtenis vermijdt u botsingen of ander onvoorspelbaar gedrag.

>[!NOTE]
>
>De `/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js` bibliotheek bevat de code uit het Adobe Analytics- `s_code.js` bestand.

## Adobe Analytics Tracking for Custom Components implementeren {#implementing-adobe-analytics-tracking-for-custom-components}

Schakel AEM-componenten in om te communiceren met het Adobe Analytics-framework. Configureer vervolgens uw framework zodat Adobe Analytics de componentgegevens bijhoudt.

Componenten die reageren op het Adobe Analytics-framework worden weergegeven in SideKick wanneer u een framework bewerkt. Nadat u de component naar het framework hebt gesleept, worden de eigenschappen van de component weergegeven en kunt u deze vervolgens toewijzen met de eigenschappen van Adobe Analytics. (Zie Een framework [instellen voor basistracking](/help/sites-administering/adobeanalytics-connect.md#creating-a-adobe-analytics-framework).)

Componenten kunnen communiceren met het Adobe Analytics-framework wanneer de component een onderliggend knooppunt heeft met de naam `analytics`. Het `analytics` knooppunt heeft de volgende eigenschappen:

* `cq:trackevents`: Identificeert de gebeurtenissen CQ die de component blootstelt. (Zie Aangepaste gebeurtenissen.)
* `cq:trackvars`: Hiermee geeft u de CQ-variabelen een naam die zijn toegewezen aan de eigenschappen van Adobe Analytics.
* `cq:componentName`: De naam voor de component die in Sidetrap wordt weergegeven.
* `cq:componentGroup`: De groep in Sidetrap die de component bevat.

De code in de component JSP voegt javascript aan de pagina toe die het volgen teweegbrengt, en bepaalt de gegevens die worden gevolgd. De naam van de gebeurtenis en de gegevensnamen die in javascript worden gebruikt moeten de overeenkomstige waarden van de `analytics` knoopeigenschappen aanpassen.

* Gebruik het kenmerk voor het bijhouden van gegevens om gebeurtenisgegevens bij te houden wanneer een pagina wordt geladen. (Zie Aangepaste gebeurtenissen [bijhouden bij laden](/help/sites-developing/extending-analytics.md#tracking-custom-events-on-page-load)van pagina.)
* Gebruik de functie CQ_Analytics.record om gebeurtenisgegevens bij te houden wanneer gebruikers met paginafuncties werken. (Zie Aangepaste gebeurtenissen [bijhouden na laden](/help/sites-developing/extending-analytics.md#tracking-custom-events-after-page-load)van pagina.)

Wanneer u deze methoden voor het bijhouden van gegevens gebruikt, wordt in de integratiemodule van Adobe Analytics automatisch aangeroepen om de gebeurtenissen en gegevens op te nemen.

### Voorbeeld: Te openen klikken bijhouden {#example-tracking-topnav-clicks}

Breid de stichting uit hoogste component zodat de Analytics van Adobe klikt op navigatiekoppelingen bij de bovenkant van de pagina. Wanneer op een navigatiekoppeling wordt geklikt, registreert Adobe Analytics de koppeling waarop is geklikt en de pagina waarop erop is geklikt.

De volgende procedures vereisen dat u reeds de volgende taken hebt uitgevoerd:

* Een CQ-toepassing gemaakt.
* Een Adobe Analytics-configuratie en een Adobe Analytics-framework zijn gemaakt.

#### De bovenste component kopiëren {#copy-the-topnav-component}

Kopieer de bovenste component naar de CQ-toepassing. De procedure vereist dat uw toepassing in CRXDE Lite opstelling is.

1. Klik met de rechtermuisknop op het `/libs/foundation/components/topnav` knooppunt en klik op Kopiëren.
1. Klik met de rechtermuisknop op de map Components onder de toepassingsmap en klik op Plakken.
1. Klik op Alles opslaan.

#### Het onderwerp integreren met het Adobe Analytics Framework {#integrating-topnav-with-the-adobe-analytics-framework}

Configureer de bovenste component en bewerk het JSP-bestand om de volgende gebeurtenissen en gegevens te definiëren.

1. Klik met de rechtermuisknop op het bovenste knooppunt en klik op Maken > Node maken. Geef de volgende eigenschapswaarden op en klik op OK:

   * Naam: `analytics`
   * Type: `nt:unstructured`

1. Voeg de volgende eigenschap toe aan het analytische knooppunt om de gebeurtenis tracking een naam te geven:

   * Naam: cq:trackevents
   * Type:String
   * Waarde: topnavClick

1. Voeg de volgende eigenschap toe aan het knooppunt Analytics om de gegevensvariabelen een naam te geven:

   * Naam: cq:trackvars
   * Type:String
   * Waarde: topnavTarget,topnavLocation

1. Voeg de volgende eigenschap toe aan het analytische knooppunt om de component voor Sidetrap een naam te geven:

   * Naam: cq:componentName
   * Type:String
   * Waarde: topnav (tracking)

1. Voeg de volgende eigenschap toe aan het analytische knooppunt om de componentgroep voor Sidetrap een naam te geven:

   * Naam: cq:componentGroup
   * Type:String
   * Waarde:Algemeen

1. Klik op Alles opslaan.
1. Open the `topnav.jsp` file.
1. Voeg in het element a het volgende kenmerk toe:

   ```xml
   onclick = "tracknav('<%= child.getPath() %>.html')"
   ```

1. Voeg onder aan de pagina de volgende javascript-code toe:

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

De inhoud van het `topnav.jsp` bestand moet als volgt worden weergegeven:

```xml
<%@page session="false"%><%--
  Copyright 1997-2008 Day Management AG
  Barfuesserplatz 6, 4001 Basel, Switzerland
  All Rights Reserved.

  This software is the confidential and proprietary information of
  Day Management AG, ("Confidential Information"). You shall not
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
>Het is vaak wenselijk om gegevens van ContextHub te volgen. Voor informatie over het gebruiken van javascript om deze informatie te verkrijgen, zie de [Toegang tot van Waarden in ContextHub](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).

#### De volgende component toevoegen aan Sidetrap {#adding-the-tracking-component-to-sidekick}

Voeg componenten die u kunt bijhouden met Adobe Analytics toe aan Sidetrap, zodat u deze aan uw framework kunt toevoegen.

1. Open uw Adobe Analytics-framework vanuit uw Adobe Analytics-configuratie. ([http://localhost:4502/etc/cloudservices/sitecatalyst.html](http://localhost:4502/etc/cloudservices/sitecatalyst.html))
1. Klik op de knop Ontwerpen bij Sidetrap.

   ![](assets/chlimage_1a.png)

1. In het gebied van de Configuratie van het Volgen van de Verbinding, vormt de klik Overerving.

   ![chlimage_1](assets/chlimage_1aa.png)

1. Selecteer in de lijst Toegestane componenten de optie Bovenliggend (bijhouden) in de sectie Algemeen en klik vervolgens op OK.
1. Vouw Sidetrap uit om de bewerkingsmodus te activeren. De component is nu beschikbaar in de groep Algemeen.

#### De component topnav toevoegen aan uw framework {#adding-the-topnav-component-to-your-framework}

Sleep de bovenste component naar het Adobe Analytics-framework en wijs de componentvariabelen en -gebeurtenissen toe aan Adobe Analytics-variabelen en -gebeurtenissen. (Zie Een framework [instellen voor basistracking](/help/sites-administering/adobeanalytics-connect.md).)

![chlimage_1-1](assets/chlimage_1-1a.png)

De bovenstaande component is nu geïntegreerd met het Adobe Analytics-framework. Wanneer u de component aan een pagina toevoegt en u klikt op de items in de bovenste navigatiebalk, worden volggegevens naar Adobe Analytics verzonden.

### S.products-gegevens naar Adobe Analytics verzenden {#sending-s-products-data-to-adobe-analytics}

Componenten kunnen gegevens genereren voor de variabele s.products die naar Adobe Analytics wordt verzonden. Ontwerp uw componenten om aan de variabele s.products bij te dragen:

* Neem een waarde op met de naam `product` van een specifieke structuur.
* Stel de leden van de gegevens in de `product` waarde beschikbaar zodat deze kunnen worden toegewezen aan Adobe Analytics-variabelen in het Adobe Analytics-framework.

De variabele Adobe Analytics s.products gebruikt de volgende syntaxis:

```
s.products="category;product;quantity;price;eventY={value}|eventZ={value};evarA={value}|evarB={value}"
```

De integratiemodule van Adobe Analytics maakt de `s.products` variabele met behulp van de `product` waarden die door AEM-componenten worden gegenereerd. De `product` waarde in het JavaScript dat door AEM-componenten wordt gegenereerd, is een array van waarden met de volgende structuur:

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

Wanneer een gegevensitem van de `product` waarde wordt weggelaten, wordt het als een lege tekenreeks in s.products verzonden.

>[!NOTE]
>
>Als er geen gebeurtenis aan een productwaarde is gekoppeld, gebruikt Adobe Analytics de `prodView` gebeurtenis standaard.

Het `analytics` knooppunt van de component moet de variabelenamen zichtbaar maken met behulp van de `cq:trackvars` eigenschap:

* product.category
* product.sku
* product.quantity
* product.price
* product.events.eventName1
* product.events.eventName_n
* product.evars.eVarName1
* product.evars.eVarName_n

De module eCommerce biedt verschillende componenten die variabele gegevens van s.products genereren. Met de component submitOrder ([http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp](http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp)) wordt bijvoorbeeld javascript gegenereerd dat vergelijkbaar is met het volgende voorbeeld:

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

Doorgaans beperken webbrowsers de grootte van GET-aanvragen. Omdat CQ-product- en SKU-waarden opslagpaden zijn, kunnen productarrays met meerdere waarden de limiet van de aanvraaggrootte overschrijden. Daarom zouden uw componenten het aantal punten in de `product` serie van elk moeten beperken `CQ_Analytics.record function`. Maak meerdere functies als het aantal items dat u wilt bijhouden de limiet kan overschrijden.

Bijvoorbeeld, beperkt de eCommerce voorleggingscomponent het aantal `product` punten in een vraag tot vier. Wanneer de kar meer dan vier producten bevat, produceert het veelvoudige `CQ_Analytics.record` functies.
