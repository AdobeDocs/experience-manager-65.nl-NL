---
title: Ontwikkelen voor gerichte inhoud
description: Onderwerpen over het ontwikkelen van componenten voor gebruik met inhoud die richten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 92b62532-4f79-410d-903e-d2bca6d0fd1c
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 0%

---

# Ontwikkelen voor gerichte inhoud{#developing-for-targeted-content}

Deze sectie beschrijft onderwerpen over het ontwikkelen van componenten voor gebruik met inhoud het richten.

* Voor informatie over het verbinden met Adobe Target, zie [&#x200B; Integrerend met Adobe Target &#x200B;](/help/sites-administering/target.md).
* Voor informatie over het ontwerpen van gerichte inhoud, zie [&#x200B; Authoring Gerichte Inhoud gebruikend het richten Wijze &#x200B;](/help/sites-authoring/content-targeting-touch.md).

>[!NOTE]
>
>Wanneer u een component in AEM auteur richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (indien gevormd). Er worden geen serveraanroepen vanuit AEM naar Adobe Target gepubliceerd.

## Gericht op Adobe Target op uw pagina&#39;s inschakelen {#enabling-targeting-with-adobe-target-on-your-pages}

Als u doelcomponenten wilt gebruiken op uw pagina&#39;s die met Adobe Target werken, neemt u specifieke code aan de clientzijde op in het element &lt;head>.

### De kopsectie {#the-head-section}

Voeg beide volgende codeblokken toe aan de sectie &lt;head> van de pagina:

```xml
<!--/* Include Context Hub */-->
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

```xml
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
```

Met deze code voegt u de vereiste analytische JavaScript-objecten toe en worden de cloudservicebibliotheken geladen die aan de website zijn gekoppeld. Voor de service Target worden de bibliotheken geladen via `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

De set bibliotheken die wordt geladen, is afhankelijk van het type doelclientbibliotheek (mbox.js of at.js) dat wordt gebruikt in de doelconfiguratie:

**voor standaard mbox.js**

```
<script type="text/javascript" src="/libs/cq/foundation/testandtarget/parameters.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/mbox.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/personalization/integrations/commons.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/util.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/init.js"></script>
```

**voor douane mbox.js**

```
<script type="text/javascript" src="/etc/cloudservices/testandtarget/<CLIENT-CODE>/_jcr_content/public/mbox.js"></script>
        <script type="text/javascript" src="/libs/cq/foundation/testandtarget/parameters.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/personalization/integrations/commons.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/util.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/init.js"></script>
```

**voor at.js**

```
<script type="text/javascript" src="/libs/cq/foundation/testandtarget/parameters.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/atjs-integration.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/atjs.js"></script>
```

>[!NOTE]
>
>Alleen de versie van `at.js` die bij het product wordt geleverd, wordt ondersteund. De versie van `at.js` die bij het product wordt geleverd, kunt u verkrijgen door het bestand van `at.js` op de locatie te raadplegen:
>
>**/libs/cq/testandtarget/clientlibs/testandtarget/atjs/source/at.js**.

**voor douane at.js**

```
<script type="text/javascript" src="/etc/cloudservices/testandtarget/<CLIENT-CODE>/_jcr_content/public/at.js"></script>
    <script type="text/javascript" src="/libs/cq/foundation/testandtarget/parameters.js"></script>
 <script type="text/javascript" src="/libs/cq/foundation/testandtarget/atjs-integration.js"></script>
```

De doelfunctionaliteit aan de clientzijde wordt beheerd door het `CQ_Analytics.TestTarget` -object. Daarom zal de pagina wat init code zoals in het volgende voorbeeld bevatten:

```
<script type="text/javascript">
            if ( !window.CQ_Analytics ) {
                window.CQ_Analytics = {};
            }
            if ( !CQ_Analytics.TestTarget ) {
                CQ_Analytics.TestTarget = {};
            }
            CQ_Analytics.TestTarget.clientCode = 'my_client_code';
        </script>
      ...

    <div class="cloudservice testandtarget">
  <script type="text/javascript">
  CQ_Analytics.TestTarget.maxProfileParams = 11;

  if (CQ_Analytics.CCM) {
   if (CQ_Analytics.CCM.areStoresInitialized) {
    CQ_Analytics.TestTarget.registerMboxUpdateCalls();
   } else {
    CQ_Analytics.CCM.addListener("storesinitialize", function (e) {
     CQ_Analytics.TestTarget.registerMboxUpdateCalls();
    });
   }
  } else {
   // client context not there, still register calls
   CQ_Analytics.TestTarget.registerMboxUpdateCalls();
  }
  </script>
 </div>
```

JSP voegt de vereiste analytische voorwerpen javascript en verwijzingen naar cliënt-kant JavaScript bibliotheken toe. Het bestand testandtarget.js bevat de functies mbox.js. De HTML die het script genereert, is vergelijkbaar met het volgende voorbeeld:

```xml
<script type="text/javascript">
        if ( !window.CQ_Analytics ) {
            window.CQ_Analytics = {};
        }
        if ( !CQ_Analytics.TestTarget ) {
            CQ_Analytics.TestTarget = {};
        }
        CQ_Analytics.TestTarget.clientCode = 'MyClientCode';
</script>
<link rel="stylesheet" href="/etc/clientlibs/foundation/testandtarget/testandtarget.css" type="text/css">
<script type="text/javascript" src="/etc/clientlibs/foundation/testandtarget/testandtarget.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/testandtarget/init.js"></script>
```

#### De hoofdsectie (start) {#the-body-section-start}

Voeg onmiddellijk na de tag &lt;body> de volgende code toe om de kenmerken van de clientcontext aan de pagina toe te voegen:

```xml
<cq:include path="clientcontext" resourceType="cq/personalization/components/clientcontext"/>
```

#### De hoofdsectie (einde) {#the-body-section-end}

Voeg de volgende code toe vlak voor de eindtag &lt;/body>:

```xml
<cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
```

Het JSP manuscript van deze component produceert vraag aan het Doel javascript API en voert andere vereiste configuraties uit. De HTML die het script genereert, is vergelijkbaar met het volgende voorbeeld:

```xml
<div class="servicecomponents cloudservices">
  <div class="cloudservice testandtarget">
    <script type="text/javascript">
      CQ_Analytics.TestTarget.maxProfileParams = 11;
      CQ_Analytics.CCM.addListener("storesinitialize", function(e) {
        CQ_Analytics.TestTarget.registerMboxUpdateCalls();
      });
    </script>
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
</div>
```

### Een aangepast doelbibliotheekbestand gebruiken {#using-a-custom-target-library-file}

>[!NOTE]
>
>Als u geen DTM of een ander doelmarketingsysteem gebruikt, kunt u aangepaste doelbibliotheekbestanden gebruiken.

>[!NOTE]
>
>De vakken zijn standaard verborgen. De klasse mboxDefault bepaalt dit gedrag. Verborgen vakken zorgen ervoor dat bezoekers de standaardinhoud niet zien voordat deze wordt omgewisseld. Het verbergen van vakken heeft echter invloed op de waargenomen prestaties.

Het standaard mbox.js- dossier dat wordt gebruikt om dozen tot stand te brengen wordt gevestigd in /etc/clientlibs/foundation/testandtarget/mbox/source/mbox.js. Als u een bestand mbox.js van de klant wilt gebruiken, voegt u het bestand toe aan de configuratie van de doelcloud. Als u het bestand wilt toevoegen, moet het bestand mbox.js beschikbaar zijn op het bestandssysteem.

Bijvoorbeeld, als u de [&#x200B; dienst van identiteitskaart van de Marketing Cloud wilt gebruiken &#x200B;](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=nl-NL) moet u mbox.js downloaden zodat het de correcte waarde voor de `imsOrgID` variabele bevat, die op uw huurder gebaseerd is. Deze variabele wordt vereist voor het integreren met de dienst van identiteitskaart van de Marketing Cloud. Voor informatie, zie [&#x200B; Adobe Analytics als Rapporterende Source voor Adobe Target &#x200B;](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t.html?lang=nl-NL) en [&#x200B; alvorens u &#x200B;](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/before-implement.html?lang=nl-NL) uitvoert.

>[!NOTE]
>
>Als een douanembox in een configuratie van het Doel wordt bepaald, moet iedereen gelezen toegang tot **hebben/etc/cloudservices** op publicatieservers. Zonder deze toegang leidt het laden van mbox.js-bestanden op de publicatiewebsite tot een fout van 404.

1. Ga naar CQ **Hulpmiddelen** pagina en selecteer **Cloud Servicen**. ([&#x200B; https://localhost:4502/libs/cq/core/content/tools/cloudservices.html](https://localhost:4502/libs/cq/core/content/tools/cloudservices.html))
1. Selecteer Adobe Target in de boomstructuur en dubbelklik in de lijst met configuraties op de doelconfiguratie.
1. Klik op Bewerken op de configuratiepagina.
1. Voor het bezit van Custom mbox.js, doorbladert de klik en selecteert het dossier.
1. Als u de wijzigingen wilt toepassen, voert u het wachtwoord voor uw Adobe Target-account in, klikt u op Opnieuw verbinden met doel en klikt u op OK als de verbinding tot stand is gebracht. Klik vervolgens op OK in het dialoogvenster Component bewerken.

Uw configuratie van het Doel omvat een douane mbox.js- dossier, [&#x200B; de vereiste code in de hoofdsectie &#x200B;](/help/sites-developing/target.md#p-the-head-section-p) van uw pagina voegt het dossier aan het kader van de cliëntbibliotheek in plaats van een verwijzing naar de bibliotheek testandtarget.js toe.

## Het onbruikbaar maken van het Bevel van het Doel voor Componenten {#disabling-the-target-command-for-components}

De meeste componenten kunnen in gerichte componenten worden omgezet gebruikend het bevel van het Doel op het contextmenu.

![&#x200B; chlimage_1-21 &#x200B;](assets/chlimage_1-21.png)

Als u de opdracht Doel uit het contextmenu wilt verwijderen, voegt u de volgende eigenschap toe aan het knooppunt cq:editConfig van de component:

* Naam: cq:disableTargeting
* Type: Boolean
* Waarde: waar

Als u bijvoorbeeld het aanwijzen van doelen voor de titelcomponenten van de Geometrixx Demo-sitepagina&#39;s wilt uitschakelen, voegt u de eigenschap toe aan het knooppunt /apps/geometrixx/components/title/cq:editConfig.

![&#x200B; chlimage_1-22 &#x200B;](assets/chlimage_1-22.png)

## Bevestigingsgegevens voor bestelling naar Adobe Target verzenden {#sending-order-confirmation-information-to-adobe-target}

>[!NOTE]
>
>Als u DTM niet gebruikt, stuurt u een bevestiging van de bestelling naar Adobe Target.

Als u de prestaties van uw website wilt volgen, stuurt u aankoopgegevens van de bevestigingspagina van uw bestelling naar Adobe Target. (Zie [&#x200B; een orderConfirmPage Mbox &#x200B;](https://developer.adobe.com/target/implement/client-side/atjs/how-to-deployatjs/implement-target-without-a-tag-manager/?lang=en) en [&#x200B; Bevestigingsmebox van de Orde - voeg douaneparameters toe.](https://experienceleaguecommunities.adobe.com/t5/adobe-target-questions/order-confirmation-mbox-add-custom-parameters/m-p/275779?profile.language=nl)) Adobe Target herkent mbox-gegevens als orderbevestigingsgegevens wanneer uw MBox-naam `orderConfirmPage` is en gebruikt de volgende specifieke parameternamen:

* productPurchasedId: een lijst met id&#39;s die de aangekochte producten identificeren.
* orderId: De id van de bestelling.
* ordertotaal: het totale bedrag van de aankoop.

De code op de gerenderde pagina van de HTML die tot mbox leidt is gelijkaardig aan het volgende voorbeeld:

```xml
<script type="text/javascript">
     mboxCreate('orderConfirmPage',
     'productPurchasedId=product1 product2 product3',
     'orderId=order1234',
     'orderTotal=24.54');
</script>
```

De waarden van elke parameter zijn verschillend voor elke orde. Daarom hebt u een component nodig die de code genereert op basis van de eigenschappen van de aankoop. Het CQ [&#x200B; Kader van de Integratie van de Handel &#x200B;](/help/commerce/cif-classic/administering/ecommerce.md) laat u toe om met uw productcatalogus te integreren en een het winkelen karretje en checkout pagina uit te voeren.

In het voorbeeld Geometrixx Outdoors wordt de volgende bevestigingspagina weergegeven wanneer een bezoeker producten koopt:

![&#x200B; chlimage_1-23 &#x200B;](assets/chlimage_1-23.png)

De volgende code voor het JSP manuscript van een component heeft toegang tot de eigenschappen van het het winkelwagentje en drukt dan de code voor het creëren van mbox.

```java
<%--

  confirmationmbox component.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false"
          import="com.adobe.cq.commerce.api.CommerceService,
                  com.adobe.cq.commerce.api.CommerceSession,
                  com.adobe.cq.commerce.common.PriceFilter,
                  com.adobe.cq.commerce.api.Product,
                  java.util.List, java.util.Iterator"%><%

/* obtain the CommerceSession object */
CommerceService commerceservice = resource.adaptTo(CommerceService.class);
CommerceSession session = commerceservice.login(slingRequest, slingResponse);

/* obtain the cart items */
List<CommerceSession.CartEntry> entries = session.getCartEntries();
Iterator<CommerceSession.CartEntry> cartiterator = entries.iterator();

/* iterate the items and get the product IDs */
String productIDs = new String();
while(cartiterator.hasNext()){
 CommerceSession.CartEntry entry = cartiterator.next();
 productIDs = productIDs + entry.getProduct().getSKU();
    if (cartiterator.hasNext()) productIDs = productIDs + ", ";
}

/* get the cart price and orderID */
String total = session.getCartPrice(new PriceFilter("CART", "PRE_TAX"));
String orderID = session.getOrderId();

%><div class="mboxDefault"></div>
<script type="text/javascript">
     mboxCreate('orderConfirmPage',
     'productPurchasedId=<%= productIDs %>',
     'orderId=<%= orderID %>',
     'orderTotal=<%= total %>');
</script>
```

Wanneer de component is opgenomen in de uitcheckpagina in het vorige voorbeeld, bevat de paginabron het volgende script waarmee het selectievakje wordt gemaakt:

```
<div class="mboxDefault"></div>
<script type="text/javascript">

     mboxCreate('orderConfirmPage',
     'productPurchasedId=47638-S, 46587',
     'orderId=d03cb015-c30f-4bae-ab12-1d62b4d105ca',
     'orderTotal=US$677.00');

</script>
```

## De doelcomponent begrijpen {#understanding-the-target-component}

Met de component Target kunnen auteurs dynamische vakken maken op basis van CQ-inhoudscomponenten. (Zie [&#x200B; Inhoud richtend &#x200B;](/help/sites-authoring/content-targeting-touch.md).) De doelcomponent bevindt zich op /libs/cq/personalization/components/target.

Het target.jsp manuscript toegang tot de paginaeigenschappen om de het richten motor te bepalen voor de component te gebruiken, en voert dan het aangewezen manuscript uit:

* Adobe Target: /libs/cq/personalization/components/target/engine_tnt.jsp
* [&#x200B; Adobe Target met AT.JS &#x200B;](/help/sites-administering/target.md): /libs/cq/personalization/components/target/engine_atjs.jsp
* [&#x200B; Adobe Campaign &#x200B;](/help/sites-authoring/target-adobe-campaign.md): /libs/cq/personalization/components/target/engine_cq_campaign.jsp
* Client-kant Rules/ContextHub: /libs/cq/personalization/components/target/engine_cq.jsp

### Maken van dozen {#the-creation-of-mboxes}

>[!NOTE]
>
>De vakken zijn standaard verborgen. De klasse mboxDefault bepaalt dit gedrag. Verborgen vakken zorgen ervoor dat bezoekers de standaardinhoud niet zien voordat deze wordt omgewisseld. Het verbergen van vakken heeft echter invloed op de waargenomen prestaties.

Als Adobe Target de doelinhoud aanstuurt, maakt het script engine_tnt.jsp vakken die de inhoud van de beoogde ervaring bevatten:

* Voegt een `div` -element toe met de klasse `mboxDefault` , zoals vereist door de Adobe Target API.

* Hiermee voegt u de inhoud van het selectievakje (de inhoud van de beoogde ervaring) toe aan het element `div` .

Na het element `mboxDefault` div wordt de javascript waarmee de mbox wordt gemaakt, ingevoegd:

* De naam, de id en de locatie van de box zijn gebaseerd op het opslagpad van de component.
* Het script verkrijgt namen en waarden van parameters voor de clientcontext.
* De aanroepen worden gemaakt aan de functies die mbox.js en andere cliëntbibliotheken bepalen om dozen tot stand te brengen.

#### Clientbibliotheken voor doelinhoud {#client-libraries-for-content-targeting}

Hier volgen de beschikbare clientlib-categorieën:

* testandtarget.mbox
* testandtarget.init
* testandtarget.util
* testandtarget.atjs
* testandtarget.atjs-integration
