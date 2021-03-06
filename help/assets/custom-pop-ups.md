---
title: Aangepaste pop-ups maken met Snelle weergave
seo-title: QuickView gebruiken om aangepaste pop-ups te maken
description: De standaard Snelle mening wordt gebruikt in e-commerceervaringen waarbij pop-up met productinformatie wordt getoond om een aankoop te drijven. U kunt aangepaste inhoud activeren om weer te geven in de pop-ups.
seo-description: De standaard Snelle mening wordt gebruikt in e-commerceervaringen waarbij pop-up met productinformatie wordt getoond om een aankoop te drijven. U kunt aangepaste inhoud activeren om weer te geven in de pop-ups.
uuid: b906cfff-ac44-4989-b6da-8a9bbf02af03
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4bcab3f4-500f-432e-b16b-cdc26b9bab4d
feature: Viewers
role: User, Admin
exl-id: 4e7f17ea-6985-4644-b91c-2c1299d01321
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---

# Aangepaste pop-ups maken met Snelle weergave {#using-quickviews-to-create-custom-pop-ups}

De standaard Snelle mening wordt gebruikt in e-commerceervaringen waarbij pop-up met productinformatie wordt getoond om een aankoop te drijven. U kunt echter aangepaste inhoud activeren om weer te geven in de pop-ups. Afhankelijk van de viewer kunnen gebruikers met deze functionaliteit een hotspot, miniatuurafbeelding of een afbeelding met hyperlinks selecteren om informatie of verwante inhoud te zien.

QuickView wordt ondersteund door de volgende viewers in Dynamic Media:

* Interactieve afbeelding (klikbare hotspots)
* Interactieve video (aanklikbare miniatuurafbeeldingen tijdens het afspelen van video)
* Carrouselbanner (aanklikbare hotspots of afbeeldingen met hyperlinks)

Hoewel de functionaliteit van elke viewer verschilt, is het proces voor het maken van een QuickView hetzelfde voor alle drie ondersteunde viewers.

**Aangepaste pop-ups maken met Snelle weergave:**

1. Maak een Snelle weergave voor een geüpload element.

   Normaal gesproken maakt u een Snelle weergave op hetzelfde moment dat u middelen bewerkt voor gebruik met de viewer die u gebruikt.

   <table>
    <tbody>
    <tr>
    <td><strong>Viewer die u gebruikt</strong></td>
    <td><strong>Voer de volgende stappen uit als u de Snelle weergave wilt maken</strong></td>
    </tr>
    <tr>
    <td>Interactieve afbeeldingen</td>
    <td><a href="/help/assets/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">Hotspots toevoegen aan een afbeeldingsbanner</a>.</td>
    </tr>
    <tr>
    <td>Interactieve video's</td>
    <td><a href="/help/assets/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">Interactiviteit toevoegen aan uw video</a>.</td>
    </tr>
    <tr>
    <td>Carousel-banners</td>
    <td><a href="/help/assets/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">Hotspots of afbeeldingen met hyperlinks toevoegen aan een banner</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Vraag de insluitcode van de viewer aan om de viewer in uw website te integreren.

   <table>
    <tbody>
    <tr>
    <td><strong>Viewer die u gebruikt</strong><br /> </td>
    <td><strong>Voer de volgende stappen uit als u de viewer wilt integreren met uw website</strong></td>
    </tr>
    <tr>
    <td>Interactieve afbeelding</td>
    <td><a href="/help/assets/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Een interactieve afbeelding met uw website</a> integreren.<br /> </td>
    </tr>
    <tr>
    <td>Interactieve video<br /> </td>
    <td><a href="/help/assets/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Een interactieve video integreren met uw website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Carousel banner</td>
    <td><a href="/help/assets/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Een carrouselbanner toevoegen aan uw websitepagina</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. De viewer die u nu gebruikt, moet weten hoe u de Snelle weergave kunt gebruiken.

   De viewer gebruikt een handler met de naam `QuickViewActive`.

   ****
VoorbeeldStel dat u de volgende voorbeeldcode voor insluiten op uw webpagina gebruikt voor een interactieve afbeelding:

   ![chlimage_1-291](assets/chlimage_1-291.png)

   De handler wordt in de viewer geladen met `setHandlers`:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Met behulp van het voorbeeld van de voorbeeldinsluitcode hierboven, is er de volgende code:**

   ```xml
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   Meer informatie over de methode `setHandlers()` vindt u in het volgende voorbeeld:

   * Interactieve afbeeldingsviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * Interactieve videoviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. U moet nu de `quickViewActivate` manager vormen.

   De `quickViewActivate` manager controleert de Snelle mening in de kijker. De manager bevat de veranderlijke lijst en functievraag voor gebruik met de Snelle mening. De ingebedde code verstrekt afbeelding voor de variabele SKU die in de Snelle mening en een steekproef `loadQuickView` functievraag wordt geplaatst.

   **Variabele**
mappingMap variabelen voor gebruik in uw Web-pagina aan de waarde SKU en generische variabelen in de Snelle mening:

   `var *variable1*= inData.*quickviewVariable*`

   De verstrekte insluitcode heeft een steekproefafbeelding voor de variabele SKU:

   `var sku=inData.sku`

   Wijs ook extra variabelen van de Snelle mening, zoals in het volgende toe:

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **De functie**
callThe manager vereist ook een functievraag voor QuickView om te werken. De functie wordt verondersteld om door uw gastheerpagina toegankelijk te zijn. De insluitcode bevat een voorbeeld van een functieaanroep:

   `loadQuickView(sku)`

   De aanroep van de voorbeeldfunctie gaat ervan uit dat de functie `loadQuickView()` bestaat en toegankelijk is.

   Meer informatie over de methode `quickViewActivate` vindt u in het volgende voorbeeld:

   * Interactieve afbeeldingsviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * Interactieve videoviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * Interactieve gegevensondersteuning in de interactieve videoviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. Ga als volgt te werk:

   * Verwijder de commentaarmarkering van de sectie setHandlers van de insluitcode.
   * Wijs om het even welke extra variabelen in de Snelle mening toe.

      * Werk `loadQuickView(sku,*var1*,*var2*)` vraag bij als u extra variabelen toevoegt.
   * Maak een eenvoudige functie `loadQuickView` () op pagina, buiten de viewer.

      Bijvoorbeeld, schrijft het volgende de waarde van SKU aan de browser console:

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Upload een HTML-testpagina naar een webserver en open deze.

      Met de variabelen van in kaart gebrachte Snelle mening en de functievraag op zijn plaats, schrijft de browser console de veranderlijke waarde aan de browser console gebruikend de verstrekte steekproeffunctie.



1. U kunt nu een functie gebruiken om een eenvoudige pop-up in de Snelle mening aan te halen. In het volgende voorbeeld wordt een `DIV` voor een pop-up gebruikt.
1. Maak het pop-upvenster op de volgende manier `DIV` op. Voeg desgewenst uw eigen aanvullende opmaak toe.

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Plaats de pop-up `DIV` in het lichaam van uw HTML- pagina.

   Één van de elementen wordt geplaatst met een identiteitskaart die met waarde SKU wordt bijgewerkt wanneer de gebruiker een Snelle mening aanhaalt. Het voorbeeld bevat ook een eenvoudige knop waarmee u de pop-up weer kunt verbergen nadat deze zichtbaar is geworden.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Voeg een functie toe zodat u de waarde SKU in pop-up kunt bijwerken; de pop-up zichtbaar maken door de eenvoudige functie te vervangen die in stap 5 wordt gecreeerd. met het volgende:

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Upload een HTML-testpagina naar uw webserver en open deze. De viewer geeft de pop-up `DIV` weer wanneer een gebruiker een Snelle weergave aanroept.
1. **Het weergeven van de aangepaste pop-up in de modus Volledig scherm**

   Sommige viewers, zoals de Interactieve Video-viewer, ondersteunen weergave op volledig scherm. Als u de pop-up echter gebruikt zoals in de vorige stappen wordt beschreven, wordt deze achter de viewer weergegeven in de modus Volledig scherm.

   Als u de pop-upweergave zowel in de standaardmodus als in de modus Volledig scherm wilt weergeven, koppelt u de pop-up aan de viewercontainer. Gebruik een tweede handlermethode, `initComplete`.

   De handler `initComplete` wordt aangeroepen nadat de viewer is geïnitialiseerd.

   ```xml
   "initComplete":function() { code block }
   ```

   Meer informatie over de methode `init()` vindt u in het volgende voorbeeld:

   * Interactieve afbeeldingsviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html)
   * Interactieve videoviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html)

1. Gebruik de volgende code om het pop-upvenster dat in de vorige stappen is beschreven, aan de viewer te koppelen:

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   In de bovenstaande code is het volgende gedaan:

   * De aangepaste pop-up geïdentificeerd.
   * Verwijderd uit DOM.
   * De viewercontainer geïdentificeerd.
   * De pop-up is gekoppeld aan de viewercontainer.

1. De gehele setHandlers-code ziet er ongeveer als volgt uit (Interactive Video Viewer is gebruikt):

   ```xml
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. Nadat de handlers worden geladen, initialiseert u de kijker:

   `*viewerInstance.*init()`

   ****
VoorbeeldIn dit voorbeeld wordt de interactieve afbeeldingsviewer gebruikt.

   `s7interactiveimageviewer.init()`

   Nadat u de viewer hebt ingesloten in uw hostpagina, moet u ervoor zorgen dat de viewerinstantie wordt gemaakt en dat de handlers worden geladen voordat de viewer wordt aangeroepen met `init()`.
