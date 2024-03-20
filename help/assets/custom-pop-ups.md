---
title: Aangepaste pop-ups maken met Snelle weergave
description: De standaard Snelle mening wordt gebruikt in e-commerceervaringen waardoor pop-up met productinformatie wordt getoond om een aankoop te drijven. U kunt aangepaste inhoud activeren om weer te geven in de pop-ups.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: Viewers
role: User, Admin
exl-id: 4e7f17ea-6985-4644-b91c-2c1299d01321
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# Aangepaste pop-ups maken met Snelle weergave {#using-quickviews-to-create-custom-pop-ups}

De standaard Snelle mening wordt gebruikt in e-commerceervaringen waardoor pop-up met productinformatie wordt getoond om een aankoop te drijven. U kunt echter aangepaste inhoud activeren om weer te geven in de pop-ups. Afhankelijk van de viewer kunnen gebruikers met deze functionaliteit een hotspot, miniatuurafbeelding of een afbeelding met hyperlinks selecteren om informatie of verwante inhoud te zien.

QuickView wordt ondersteund door de volgende viewers in Dynamic Media:

* Interactieve afbeelding (klikbare hotspots)
* Interactieve video (aanklikbare miniatuurafbeeldingen tijdens het afspelen van video)
* Carrouselbanner (aanklikbare hotspots of afbeeldingen met hyperlinks)

Hoewel de functionaliteit van elke viewer verschilt, is het proces voor het maken van een QuickView hetzelfde voor alle drie ondersteunde viewers.

**Aangepaste pop-ups maken met Snelle weergave:**

1. Maak een Snelle weergave voor een geüpload element.

   Normaal gesproken maakt u een QuickView op hetzelfde moment dat u een element bewerkt voor gebruik met de viewer die u gebruikt.

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
    <td>Carousel Banners</td>
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
    <td><a href="/help/assets/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Een interactieve afbeelding met uw website integreren</a>.<br /> </td>
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

1. De viewer die u gebruikt, moet weten hoe u de Snelle weergave kunt gebruiken.

   De kijker gebruikt een manager genoemd `QuickViewActive`.

   **Voorbeeld**
Stel dat u de volgende voorbeeldcode voor insluiten op uw webpagina gebruikt voor een interactieve afbeelding:

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

   Meer informatie over `setHandlers()` methode op de volgende wijze:

   * Interactieve afbeeldingsviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * Interactieve videoviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. Vorm `quickViewActivate` handler.

   De `quickViewActivate` De manager controleert de Snelle mening in de kijker. De manager bevat de veranderlijke lijst en functievraag voor gebruik met de Snelle mening. De ingebedde code verstrekt afbeelding voor de variabele SKU die in de Snelle mening en een steekproef wordt geplaatst `loadQuickView` functieaanroep.

   **Variabele toewijzen**
Wijs variabelen voor gebruik in uw Web-pagina aan de waarde SKU en generische variabelen in de Snelle mening toe:

   `var *variable1*= inData.*quickviewVariable*`

   De verstrekte insluitcode heeft een steekproefafbeelding voor de variabele SKU:

   `var sku=inData.sku`

   Wijs ook extra variabelen van de Snelle mening, zoals in het volgende toe:

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Functieaanroep**
De manager vereist ook een functievraag voor de Snelle mening om te werken. De functie wordt verondersteld om door uw gastheerpagina toegankelijk te zijn. De insluitcode bevat een voorbeeld van een functieaanroep:

   `loadQuickView(sku)`

   De aanroep van de voorbeeldfunctie gaat uit van de functie `loadQuickView()` bestaat en toegankelijk is.

   Meer informatie over `quickViewActivate` methode op de volgende wijze:

   * Interactieve afbeeldingsviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * Interactieve videoviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * Interactieve gegevensondersteuning in de interactieve videoviewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. Ga als volgt te werk:

   * Verwijder de commentaarmarkering van de sectie setHandlers van de insluitcode.
   * Wijs om het even welke extra variabelen in de Snelle mening toe.

      * Werk de `loadQuickView(sku,*var1*,*var2*)` Vraag als u extra variabelen toevoegt.

   * Eenvoudig maken `loadQuickView` () op pagina, buiten de viewer.

     Bijvoorbeeld, schrijft het volgende de waarde van SKU aan de browser console:

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Upload een HTML-pagina voor de test naar een webserver en open deze.

     Met de variabelen van in kaart gebrachte Snelle mening en de functievraag op zijn plaats, schrijft de browser console de veranderlijke waarde aan de browser console gebruikend de verstrekte steekproeffunctie.

1. U kunt nu een functie gebruiken om een eenvoudige pop-up in de Snelle mening aan te halen. In het volgende voorbeeld wordt een `DIV` voor een popup.
1. De pop-up opmaken `DIV` op de volgende wijze. Voeg desgewenst uw eigen extra stijlen toe.

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Het pop-upvenster plaatsen `DIV` in de hoofdtekst van de pagina HTML.

   Één van de elementen wordt geplaatst met een identiteitskaart die met waarde SKU wordt bijgewerkt wanneer de gebruiker een Snelle mening aanhaalt. Het voorbeeld bevat ook een eenvoudige knop waarmee u de pop-up weer kunt verbergen nadat deze zichtbaar is geworden.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Voeg een functie toe zodat u de SKU-waarde in de pop-up kunt bijwerken. Maak de pop-up zichtbaar door de eenvoudige functie te vervangen die in stap 5 wordt gemaakt. met het volgende:

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Upload een HTML-pagina voor de test naar uw webserver en open deze. De pop-up wordt weergegeven door de viewer `DIV` wanneer een gebruiker een Snelle mening aanhaalt.
1. **Het weergeven van de aangepaste pop-up in de modus Volledig scherm**

   Sommige viewers, zoals de Interactieve Video-viewer, ondersteunen weergave in de modus Volledig scherm. Als u de pop-up echter gebruikt zoals in de vorige stappen wordt beschreven, wordt deze achter de viewer weergegeven in de modus Volledig scherm.

   Als u de pop-upweergave zowel in de standaardmodus als in de modus Volledig scherm wilt weergeven, koppelt u de pop-up aan de viewercontainer. Een tweede handlermethode gebruiken `initComplete`.

   De `initComplete` handler wordt aangeroepen nadat de viewer is geïnitialiseerd.

   ```xml
   "initComplete":function() { code block }
   ```

   Meer informatie over `init()` methode op de volgende wijze:

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

   **Voorbeeld**
In dit voorbeeld wordt de interactieve afbeeldingsviewer gebruikt.

   `s7interactiveimageviewer.init()`

   Nadat u de viewer hebt ingesloten in uw hostpagina, moet u ervoor zorgen dat de viewerinstantie is gemaakt en dat de handlers worden geladen voordat de viewer wordt aangeroepen met `init()`.
