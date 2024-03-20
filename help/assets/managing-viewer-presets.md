---
title: Viewer-voorinstellingen beheren
description: Viewer-voorinstellingen in Dynamic Media maken, bewerken en beheren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
feature: Viewer Presets
role: User, Admin
exl-id: 0899e497-88e9-4fc3-a6be-b3a149fb5b32
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '4305'
ht-degree: 6%

---

# Viewer-voorinstellingen beheren{#managing-viewer-presets}

Een voorinstelling voor de viewer is een verzameling instellingen die bepalen hoe gebruikers multimedia-elementen op hun computerschermen en mobiele apparaten weergeven. Beheerders kunnen voorinstellingen voor viewers maken. Er zijn instellingen beschikbaar voor een array met viewerconfiguratieopties. U kunt bijvoorbeeld de weergavegrootte of het zoomgedrag van de viewer wijzigen.

Raadpleeg de Adobe van Dynamic Media voor instructies voor het maken en aanpassen van uw eigen HTML5-viewervoorinstellingen *HTML5 Viewer SDK API-documentatie*. De SDK is beschikbaar op de IS-publicatieserver die is ingesloten in de SDK zelf. Elke bibliotheekversie heeft zijn eigen documentatie van SDK inbegrepen.

Pad: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
Bijvoorbeeld 3.10 SDK: [https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

Zie ook de [Referentiehandleiding voor Adobe Dynamic Media Viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

In deze sectie wordt beschreven hoe u voorinstellingen voor viewers kunt maken, bewerken en beheren. U kunt een viewervoorinstelling op elk gewenst moment op een element toepassen. Zie [Viewer-voorinstellingen toepassen](#applying-a-viewer-preset-to-an-asset).

>[!NOTE]
>
>Alle *Voorinstellingen voor vooraf gedefinieerde viewers buiten de box* is geen ondersteund scenario. Als u probeert een voorinstelling voor een viewer buiten het vak te bewerken, wordt u gevraagd de voorinstelling van de viewer op te slaan onder een andere naam.

## Toetsenbordtoegankelijkheid voor viewers {#keyboard-accessibility-for-viewers}

Alle viewers die niet in de verpakking zijn opgenomen, ondersteunen toegankelijkheid van het toetsenbord.

Zie ook [Toetsenbordtoegankelijkheid en -navigatie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## Viewer-voorinstellingen beheren {#managing-viewer-presets-1}

U kunt in Adobe Experience Manager voorinstellingen voor viewers toevoegen, bewerken, verwijderen, publiceren, ongedaan maken en een voorvertoning weergeven door te tikken **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.

![6_5_tools-assets-viewerpresets](assets/6_5_tools-assets-viewerpresets.png)

>[!NOTE]
>
>Standaard geeft het systeem 15 voorinstellingen voor viewers weer wanneer u Viewers selecteert in de gedetailleerde weergave van elementen. U kunt deze limiet verhogen. Zie [Het aantal weergegeven viewervoorinstellingen verhogen](#increasing-the-number-of-viewer-presets-that-display).

### Viewer-ondersteuning voor responsieve webpagina&#39;s {#viewer-support-for-responsive-designed-web-pages}

Verschillende webpagina&#39;s hebben verschillende behoeften. Soms wilt u bijvoorbeeld een webpagina die een koppeling bevat waarmee de HTML5 Viewer in een apart browservenster wordt geopend. In andere gevallen kan het nodig zijn de HTML5 Viewer rechtstreeks in te sluiten op de hostpagina. In het laatste geval kan de webpagina een statische indeling hebben. Of de interface reageert mogelijk op een ander scherm op verschillende apparaten of voor verschillende venstergrootten in de browser. Om aan deze behoeften tegemoet te komen, ondersteunen alle vooraf gedefinieerde, kant-en-klare HTML5 Viewers die bij Dynamic Media worden geleverd zowel statische webpagina&#39;s als responsieve webpagina&#39;s.

Zie [Responsieve afbeeldingsbibliotheek](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) voor meer informatie over het insluiten van responsieve viewers op uw webpagina&#39;s.

>[!NOTE]
>
>Publiceer alle viewers die niet in de box staan voordat u ze voor het eerst gebruikt.
>Zie [Voorinstellingen van viewer publiceren].(#publishing-viewer-presets)

### Compatibiliteit van het systeem met voorinstellingen voor viewers {#viewer-preset-system-compatibility}

Alle voorinstellingen voor viewers buiten de box die bij Dynamic Media worden geleverd, zijn volledig compatibel met de volgende systemen:

* Desktops
* Apple iPhone
* Apple iPad
* Android™-smartphone
* Android™-tablet
* Voor video is aanvullende ondersteuning voor het afspelen van MP4 beschikbaar [BlackBerry®](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) en [Windows-telefoon](https://learn.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs).

### Rijke mediatypen voor viewervoorinstellingen {#rich-media-types-for-viewer-presets}

Beheerders kunnen de volgende rich media-typen toevoegen en aanpassen bij het maken van voorinstellingen voor viewers.

<table>
 <tbody>
  <tr>
   <td><strong>Carousel-set</strong><br /> </td>
   <td><p>Hotspots of afbeeldingen met hyperlinks of beide worden toegevoegd aan een reeks van twee of meer afbeeldingen. Een klant kan de afbeeldingen naar links of rechts pannen en vervolgens een hotspot op een afbeelding selecteren voor meer informatie of voor directe aankoop van de categorie, de startpagina of de landingspagina's van een website.</p> </td>
  </tr>
  <tr>
   <td><strong>Dimensionaal</strong><br /> </td>
   <td><p>Hiermee geeft u 3D-scènes weer waarmee u de camera kunt draaien, pannen, zoomen of opnieuw centreren.</p> </td>
  </tr>
  <tr>
   <td><strong>Zoomen met flyout</strong></td>
   <td><p>Hiermee geeft u een tweede afbeelding van het ingezoomde gebied weer naast de oorspronkelijke afbeelding. Er zijn geen besturingselementen om te gebruiken. Gebruikers verplaatsen de selectie over het gebied dat ze willen weergeven.</p> <p>Houd er bij het bepalen van het totale bandbreedtegebruik voor deze viewer rekening mee dat zowel de hoofdafbeelding als de vervolgafbeelding in de viewer worden weergegeven. De grootte van de vervolgafbeelding wordt bepaald door de grootte van de hoofdafbeelding (breedte en hoogte van werkgebied) en de zoomfactor. Als u wilt voorkomen dat het flyout-bestand te groot wordt, brengt u de volgende twee waarden met elkaar in evenwicht: als u een grote hoofdafbeeldingsgrootte hebt, verlaagt u de waarde voor Zoomfactor. (De breedte en hoogte van de Flyout bepalen de grootte van het wegvliegvenster, maar niet de grootte van het vliegend beeld dat aan de kijker wordt gediend.)</p> <p>Als de hoofdafbeelding bijvoorbeeld 350 x 350 pixels groot is, met een zoomfactor van 3, is de resulterende uitvliegafbeelding 1050 x 1050 pixels. Als de hoofdafbeeldingsgrootte 300 x 300 pixels is, met een zoomfactor van 4, is de vervolgafbeelding 1200 x 1200 pixels. Afhankelijk van de kwaliteitsinstelling JPEG (aanbevolen instellingen liggen tussen 80 en 90), kunt u de bestandsgrootte aanzienlijk verkleinen. De aanbevolen zoomfactoren zijn 2,5 tot 4, afhankelijk van de grootte van de hoofdafbeelding.</p> </td>
  </tr>
  <tr>
   <td><strong>Inline zoomen</strong></td>
   <td>Hiermee geeft u een afbeelding weer van het ingezoomde gebied in de oorspronkelijke viewer. Er zijn geen besturingselementen om te gebruiken. Gebruikers verplaatsen de selectie dus over het gebied dat ze willen weergeven.</td>
  </tr>
  <tr>
   <td><strong>Afbeeldingsset</strong></td>
   <td>In de Vastgestelde kijker van het Beeld, kunnen de gebruikers verschillende meningen of kleurenvariaties van een punt zien door een duimnagelbeeld te selecteren. Deze viewer beschikt ook over zoomgereedschappen waarmee u afbeeldingen nauwkeurig kunt bekijken.</td>
  </tr>
  <tr>
   <td><strong>Interactieve afbeelding</strong></td>
   <td>Hotspots worden toegevoegd aan delen van een afbeelding die een klant vervolgens kan selecteren voor meer informatie of voor directe aankoop van de categorie, de startpagina of de landingspagina's van een website.</td>
  </tr>
  <tr>
   <td><strong>Interactieve video</strong></td>
   <td>Miniaturen worden toegevoegd aan tijdlijnsegmenten in een video die een klant vervolgens kan selecteren voor meer details of voor directe aankoop van de categorie, de startpagina of de bestemmingspagina's van een website.</td>
  </tr>
  <tr>
   <td><strong>Gemengde media</strong></td>
   <td>Hiermee geeft u verschillende typen media weer in één viewer. U kunt centrifuges, afbeeldingssets, afbeeldingen en video's opnemen.</td>
  </tr>
  <tr>
   <td><strong>Panoramische afbeelding</strong></td>
   <td><p>Met de Panoramische afbeelding en de Panoramische VR-viewers worden bolvormige panoramische afbeeldingen weergegeven zodat gebruikers deze kunnen bekijken in een 360-gradenervaring in een ruimte, eigenschap, locatie of landschap.</p> <p>Een geüploade afbeelding kan alleen als een bolvormig panorama worden beschouwd als de afbeelding een van de volgende opties of beide heeft:</p>
    <ul>
     <li>Een hoogte-breedteverhouding van 2:1.</li>
     <li>Gecodeerd met de trefwoorden <code>equirectangular</code>, of <code>spherical</code> en <code>panorama</code>, of <code>spherical </code>en <code>panoramic</code>. Zie <a href="/help/sites-authoring/tags.md">Tags gebruiken</a>.</li>
    </ul> <p>Zowel zijn de aspectverhouding als de sleutelwoordcriteria van toepassing op panoramische activa voor de de detailpagina van activa en de component van "Panoramische Media" WCM.</p> <p><strong>Belangrijk</strong>: Deze viewer is alleen beschikbaar in de modus Dynamic Media - Scene7.</p> </td>
  </tr>
  <tr>
   <td><strong>Video over slim uitsnijden</strong><br /> </td>
   <td><p>Met deze viewer kunt u automatisch het brandpunt in een video detecteren en uitsnijden.</p> </td>
  </tr>
  <tr>
   <td><strong>Set draaien</strong></td>
   <td>Biedt meerdere weergaven van een afbeelding, zodat gebruikers het object kunnen draaien om de verschillende zijden en hoeken te bekijken.</td>
  </tr>
  <tr>
   <td><strong>360-video</strong></td>
   <td><p>Met de 360/VR-videoviewer kunt u rechthoekige video renderen voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap of medische procedure.</p> <p>Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; bij het afspelen op mobiele apparaten worden doorgaans de ingebouwde gyroscopische besturingselementen toegepast.</p> <p>De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.</p> <p><strong>Belangrijk</strong>: Deze viewer is alleen beschikbaar in de modus Dynamic Media - Scene7.</p> </td>
  </tr>
  <tr>
   <td><strong>Video</strong></td>
   <td><p>Speelt video af met progressieve of adaptieve bitsnelheidstreaming. Bij adaptieve bitsnelheidstreaming worden automatisch apparaat- en bandbreedtedetectie uitgevoerd voor de juiste videokwaliteit in de juiste indeling.</p> </td>
  </tr>
  <tr>
   <td><strong>Verticaal zoomen</strong></td>
   <td><p>Met de verticale zoomviewer kunt u een productafbeeldingsweergave maximaliseren, zodat uw gebruikers de beste weergave van een product krijgen. De verticale locatie van stalen doet het volgende:</p>
    <ul>
     <li>Hiermee zorgt u ervoor dat stalen zich boven de vouw bevinden.<br/> Bij horizontale stalen zijn deze, afhankelijk van de grootte van het bureaublad van de gebruiker, pas zichtbaar wanneer de gebruiker de pagina omlaag schuift. Door de stalen verticaal in de viewer te plaatsen, weet u zeker dat ze zichtbaar zijn, ongeacht de schermgrootte van de gebruiker.</li>
     <li>Maximaliseert de hoofdafbeeldingsgrootte.<br /> Met horizontale stalen is het nodig ruimte op de pagina te reserveren om ervoor te zorgen dat deze zichtbaar zijn. Hierdoor nam de grootte van de hoofdafbeelding af. Met een verticale staallay-out hoeft u deze ruimte echter niet toe te wijzen. Op die manier kunt u de grootte van de hoofdafbeelding maximaliseren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Zoomen</strong></td>
   <td>Hiermee kunnen gebruikers inzoomen op het gebied door het te selecteren. Gebruikers kunnen besturingselementen selecteren om in te zoomen, uit te zoomen en de standaardgrootte van de afbeelding te herstellen.</td>
  </tr>
 </tbody>
</table>

### Lijst met voorinstellingen voor viewers buiten de box {#list-of-out-of-the-box-viewer-presets}

In de volgende tabel worden alle vooraf gedefinieerde, kant-en-klare Viewer-voorinstellingen weergegeven die bij Dynamic Media worden geleverd.

Zie ook [Live demo&#39;s](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Voor informatie over ondersteunde webbrowsers en besturingssysteemversies voor Viewers kunt u de Opmerkingen bij de release Viewers bekijken.

Zie Opmerkingen bij de release van viewers in de inhoudsopgave van het dialoogvenster [Referentiehandleiding voor viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

>[!NOTE]
>
>Alle voorinstellingen voor viewers die buiten de box vallen, zijn al geactiveerd (ingeschakeld), maar u moet ze publiceren.
>Zie [Voorinstellingen van viewer publiceren](#publishing-viewer-presets).
>
>Alle nieuwe viewervoorinstellingen die u maakt en toevoegt, moeten zowel worden geactiveerd *als *gepubliceerd.
>Zie [Viewer-voorinstellingen activeren of deactiveren](#activating-or-deactivating-viewer-presets) en [Voorinstellingen van viewer publiceren](#publishing-viewer-presets).

<table>
 <tbody>
  <tr>
   <td><strong>Titel van voorinstelling van viewer</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>CSS-bestandsnaam</strong><br /> </td>
  </tr>
  <tr>
   <td>Carrousel_Gestippeld_donker</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_dark.css</code></td>
  </tr>
  <tr>
   <td>Carrousel_Gestippeld_licht</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_light.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_light.css</code></td>
  </tr>
  <tr>
   <td>Dimensionaal</td>
   <td>Dimensionaal</td>
   <td><code>html5_dimensionalviewer.css</code></td>
  </tr>
  <tr>
   <td>Flyout</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_flyoutviewer.css</code></td>
  </tr>
  <tr>
   <td>Afbeeldingsset_donker</td>
   <td>Afbeeldingsset</td>
   <td><code>html5_zoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_light</td>
   <td>Afbeeldingsset</td>
   <td><code>html5_zoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_donker</td>
   <td>Gemengd_Media</td>
   <td><code>html5_inlinemixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_light</td>
   <td>Gemengd_Media</td>
   <td><code>html5_inlinemixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineZoom</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_inlinezoomviewer.css</code></td>
  </tr>
  <tr>
   <td>GemengdMedia_donker</td>
   <td>Gemengd_Media</td>
   <td><code>html5_mixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>GemengdMedia_licht</td>
   <td>Gemengd_Media</td>
   <td><code>html5_mixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>PanoramaImage</td>
   <td>Panorama_Afbeelding</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>PanoramaImageVR</td>
   <td>Panorama_Afbeelding</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>Shopable_Banner</td>
   <td>Interactive_Image</td>
   <td><code>html5_interactiveimage.css</code></td>
  </tr>
  <tr>
   <td>Shopable_Video_donker</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideoviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Shopable_Video_light</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideovewer_light.css</code></td>
  </tr>
  <tr>
   <td>SmartCropVideo</td>
   <td>Smart_Crop_Video</td>
   <td><code>html5_smartcropvideoviewer.css</code></td>
  </tr>
  <tr>
   <td>SmartCropVideo_social</td>
   <td>Smart_Crop_Video</td>
   <td><code>html5_smartcropvideoviewersocial.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_donker</td>
   <td>Spin_set</td>
   <td><code>html5_spinviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_light</td>
   <td>Spin_set</td>
   <td><code>html5_spinviewer_light.css</code></td>
  </tr>
  <tr>
   <td><p>Video</p> <p>(Inclusief ondersteuning voor ondertiteling)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video360_social</p> <p>(Inclusief standaardbesturingselementen voor het afspelen van video, videorendering wordt uitgevoerd in de stereomodus, handmatige besturing van het gezichtspunt is uitgeschakeld, maar gyroscopische besturing is ingeschakeld en er zijn geen functies voor sociale media)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewersocial.css</code></td>
  </tr>
  <tr>
   <td><p>Video360VR</p> <p>(Ontworpen voor eindgebruikers die een virtuele realiteitsbril gebruiken. Inclusief standaardbesturingselementen voor het afspelen van video en functies voor sociale media)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video_social</p> <p>(Inclusief ondersteuning voor ondertiteling en sociale media)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewersocial.css</code></td>
  </tr>
  <tr>
   <td>Zoomen_donker<br /> </td>
   <td>Zoomen<br /> </td>
   <td><code>html5_basiczoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Zoomen_licht<br /> </td>
   <td>Zoomen</td>
   <td><code>html5_basiczoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>ZoomenVerticaal_donker<br /> </td>
   <td>Verticaal_Zoomen</td>
   <td><code>html5_zoomverticalviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_light</td>
   <td>Verticaal_Zoomen</td>
   <td><code>html5_zoomverticalviewer_light.css</code></td>
  </tr>
 </tbody>
</table>

### Matrix voor ondersteunde mobiele viewers {#supported-mobile-viewers-gestures-matrix}

In de volgende tabel worden de bewegingen van de mobiele viewer weergegeven die worden ondersteund op iOS-, Android™ 2.x- en Android™ 3.x-apparaten.

<table>
 <tbody>
  <tr>
   <td><strong>Gesture</strong></td>
   <td><strong>Zoomen met flyout</strong></td>
   <td><strong>Zoomen</strong></td>
   <td><strong>Draaien</strong></td>
  </tr>
  <tr>
   <td><p><strong>Slepen</strong></p> </td>
   <td><p>Pannen</p> </td>
   <td><p>Pannen</p> </td>
   <td><p>Pannen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Selecteren</strong></p> </td>
   <td><p>Flyout-venster tonen</p> </td>
   <td><p>De gebruikersinterface weergeven of verbergen</p> </td>
   <td><p>De gebruikersinterface weergeven of verbergen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Dubbelselecteren</strong></p> </td>
   <td><p>Niet van toepassing</p> </td>
   <td><p>Inzoomen of voorinstellingen</p> </td>
   <td><p>Inzoomen of voorinstellingen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Kneep open</strong></p> </td>
   <td><p>Niet van toepassing</p> </td>
   <td><p>Inzoomen (alleen iOS en Android™, 3x)</p> </td>
   <td><p>Inzoomen (alleen iOS en Android™, 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Kneep dicht</strong></p> </td>
   <td><p>Niet van toepassing</p> </td>
   <td><p>Uitzoomen (alleen iOS en Android™, 3x)</p> </td>
   <td><p>Uitzoomen (alleen iOS en Android™, 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Veeggebaar</strong></p> </td>
   <td><p>Schuift de staalbalk</p> </td>
   <td><p>Afbeeldingen schuiven</p> </td>
   <td><p>Spinnen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Vlikken</strong></p> </td>
   <td><p>Schuift de staalbalk</p> </td>
   <td><p>Afbeeldingen schuiven</p> </td>
   <td><p>Spinnen</p> </td>
  </tr>
 </tbody>
</table>

## Het aantal weergegeven Viewer-voorinstellingen vergroten {#increasing-the-number-of-viewer-presets-that-display}

Experience Manager toont een groot aantal verschillende viewervoorinstellingen wanneer een element wordt weergegeven vanuit **[!UICONTROL Detail View]** > **[!UICONTROL Viewers]**. U kunt het aantal weergegeven viewers verhogen of verlagen.

**Het aantal weergegeven Viewer-voorinstellingen verhogen:**

1. Navigeren naar CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigeer naar het knooppunt met voorinstellingen voor viewer op de volgende locatie:

   `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. Wijzig in de eigenschap **[!UICONTROL limit]** de **[!UICONTROL Value]**, die standaard op 15 is ingesteld, in het gewenste getal.
1. Navigeer naar de vooraf ingestelde gegevensbron voor de viewer op `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. Wijzig in de eigenschap limit het getal in het gewenste getal, bijvoorbeeld `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Selecteren **[!UICONTROL Save All]**.

## Een voorinstelling voor viewers maken {#creating-a-new-viewer-preset}

Door viewervoorinstellingen te maken, kunt u verschillende instellingen toepassen op weergave en interactie met elementen. U hoeft echter geen voorinstellingen voor viewers te maken. Desgewenst kunt u de standaardvoorinstellingen voor viewers gebruiken die al bij AEM Assets worden geleverd.

Als u een viewervoorinstelling maakt nadat u deze hebt opgeslagen, wordt de status van de viewer automatisch geactiveerd (ingesteld op **[!UICONTROL On]**) op de pagina Voorinstellingen viewer. Deze status betekent dat deze zichtbaar is in de Dynamic Media-component en de Interactieve Media-component en wanneer u een voorvertoning van een afbeelding of video weergeeft.

Sommige voorinstellingen voor viewers hebben exclusieve instellingen die het gebruik en het algemene gedrag van de viewer kunnen beïnvloeden. Afhankelijk van de viewervoorinstelling die u maakt, is het verstandig rekening te houden met deze speciale overwegingen.

Zie [Speciale overwegingen voor het maken van een interactieve viewervoorinstelling](#special-considerations-for-creating-an-interactive-viewer-preset).

Zie [Speciale overwegingen voor het maken van een voorinstelling voor de Carousel Banner Viewer](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**Een voorinstelling voor de viewer maken:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]>[!UICONTROL Viewer Presets]**.

   ![6_5_viewervoorinstellingen](assets/6_5_viewerpresets.png)

1. Selecteer op de pagina Voorinstellingen viewer op de werkbalk de optie **[!UICONTROL Create]**.
1. In de **[!UICONTROL New Viewer Preset]** in het dialoogvenster **[!UICONTROL Preset Name]** voert u de naam van de nieuwe voorinstelling in. Een naam zorgvuldig kiezen: deze kan niet worden bewerkt nadat u een **[!UICONTROL Create]**.

   Wanneer u de voorinstelling later in deze stappen opslaat, wordt de naam weergegeven op de pagina Voorinstellingen viewer onder de kolomkop Titel voorinstelling.

1. Selecteer in het vervolgkeuzemenu Type rijke media het type voorinstelling voor de viewer dat u wilt maken en selecteer vervolgens in de rechterbovenhoek van de pagina de optie **[!UICONTROL Create]**.

   Zie [Rijke mediatypen voor viewervoorinstellingen](#rich-media-types-for-viewer-presets).

1. Selecteer op de pagina Viewer Preset Editor de optie **[!UICONTROL Appearance]** tab.
1. Voer een van de volgende handelingen uit:

   * In de **[!UICONTROL Selected Type]** keuzemenu, selecteer een component waarvan visueel ontwerp u wilt aanpassen. U kunt ook elk visueel element in de viewer selecteren om het te selecteren voor configuratie.

     Met de visuele editor kunt u zien welk effect een bepaalde eigenschap heeft op een stijl. Stel een eigenschap in of pas deze aan om direct te zien welk effect het heeft op de viewer met behulp van het voorbeeld links van de editor.

     De CSS-opmaakeigenschappen voor elk type viewer-voorinstelling worden beschreven in het gedeelte &quot;Aanpassen *`<viewer name>`* Help-onderwerp van de viewer [Referentiehandleiding voor viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html). Als u bijvoorbeeld een viewervoorinstelling van het type maakt `Mixed_Media`, zie [Gemengde Media Viewer aanpassen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) voor een lijst en beschrijving van elke eigenschap.

   * Als u stijlinstellingen hebt gedefinieerd in een afzonderlijk CSS-bestand, kunt u het CSS-bestand uploaden naar AEM Assets. Selecteren **[!UICONTROL Import CSS]** onder de **[!UICONTROL Selected Type]** pull-down menu (indien nodig, scrol de visuele redacteur omhoog om het te zien) zodat kunt u het geüploade CSS dossier vinden en het associëren met de kijker vooraf ingestelde.

     Wanneer u een CSS-bestand importeert, controleert de visuele editor of de CSS de juiste viewermarkeringen gebruikt. Als u bijvoorbeeld een zoomviewer maakt, moeten alle CSS-regels die u importeert, worden gedefinieerd met de naam van de viewerklasse `.s7mixedmediaviewer` gedefinieerd voor een bovenliggend viewerelement.

     U kunt willekeurige, handgemaakte CSS importeren zolang deze de CSS-markeringen voor een bepaalde viewer correct definieert. (CSS-markeertekens worden in elke &quot;Aanpassen&quot; beschreven *&lt;viewer name=&quot;&quot;>* Help-onderwerp van de viewer [Referentiehandleiding voor viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html). Als u bijvoorbeeld wilt lezen over CSS-markeringen voor de Zoomviewer, raadpleegt u [Zoomviewer aanpassen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html).) Het is echter mogelijk dat de visuele editor bepaalde CSS-waarden niet begrijpt. In dergelijke gevallen probeert de visuele editor de fouten te negeren zodat de CSS nog steeds werkt.

   >[!NOTE]
   >
   >Als u de CSS liever rechtstreeks in de onbewerkte vorm bewerkt, selecteert u **[!UICONTROL Show/Hide CSS]** onder het keuzemenu Geselecteerde tekst (schuif indien nodig de visuele editor omhoog om deze te zien).
   >Als de visuele redacteur, wanneer u een bezit direct in CSS verandert, ziet u onmiddellijk welk effect het op de kijkerssteekproef heeft. En, wordt dat zelfde bezit automatisch bijgewerkt tezelfdertijd in de visuele redacteur. Als zodanig kunt u de onbewerkte CSS-editor of de visuele editor gebruiken, of beide door elkaar gebruiken.

   >[!NOTE]
   >
   >Voor knopillustraties kiest u de 2x-afbeelding en uploadt u kunstwerk met hoge resolutie. Wanneer u werkt met interactieve afbeeldingen en schopbare banners, kunt u ook verschillende hotspotknoppen uit de doos selecteren.

1. (Optioneel) Selecteer Boven aan de pagina Voorinstelling viewer bewerken de optie **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]**, of **[!UICONTROL Phone]** Hiermee definieert u unieke visuele stijlen voor verschillende apparaat- en schermtypen.
1. Selecteer op de pagina Viewer Preset Editor de optie **[!UICONTROL Behavior]** tab. U kunt ook elk visueel element in de viewer selecteren om het te selecteren voor configuratie.
Bijvoorbeeld voor *VideoPlayer* tekst, onder **[!UICONTROL Modifiers]** > **[!UICONTROL Playback]** kunt u kiezen uit een van de drie adaptieve opties voor bitsnelheidstreaming:

   * **[!UICONTROL dash]** - Video&#39;s worden alleen als streepje gestreamd. Op Safari/iOS-apparaten moet u echter **[!UICONTROL hls]** als het type.
   * **[!UICONTROL hls]** - Video&#39;s worden alleen als hls gestreamd.
   * **[!UICONTROL auto]** - Beste praktijken. Het maken van DASH- en HLS-streams is geoptimaliseerd voor opslag. Daarom adviseert de Adobe dat u altijd selecteert **[!UICONTROL auto]** als het afspeeltype. Video&#39;s worden gestreamd als strepen, hls of progressief, zoals in de volgende afspeelvolgorde:
      * Als de browser DASH ondersteunt, wordt eerst DASH-streaming gebruikt.
      * Als de browser geen ondersteuning biedt voor DASH, wordt vervolgens HLS-streaming gebruikt.
      * Als de browser DASH of HLS niet ondersteunt, wordt progressief afspelen gebruikt, tot slot.

   >[!NOTE]
   >
   >Om de **[!UICONTROL dash]** moet deze optie eerst worden ingeschakeld door de Technische Ondersteuning van de Adobe op uw account. Zie [DASH inschakelen voor uw account](/help/assets/video.md#enable-dash).

1. Selecteer in het vervolgkeuzemenu **[!UICONTROL Selected Type]** een component waarvan u het gedrag wilt wijzigen.

   Veel componenten in de visuele editor hebben een gedetailleerde beschrijving. Deze beschrijvingen worden weergegeven in blauwe vakken wanneer u een component uitbreidt om de bijbehorende parameters weer te geven.

   Sommige viewertypen bevatten componenten waarmee u opdrachten voor het leveren van afbeeldingen in een tekstveld **[!UICONTROL IS Command]** kunt opgeven. Zie de [Referentie van de API voor het leveren van afbeeldingen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html) voor een lijst met opdrachten die u kunt gebruiken.

   >[!NOTE]
   >
   >**Als u een aanraakapparaat gebruikt, zoals een telefoon of tablet...**
   >
   >
   >Nadat u een waarde in het tekstgebied typt, selecteer elders in het gebruikersinterface om de verandering voor te leggen en het virtuele toetsenbord te sluiten. Als u Enter selecteert, vindt geen actie plaats.

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save]**.
1. Publiceer uw nieuwe viewervoorinstelling zodat u deze op uw website kunt gebruiken.

   Zie [Voorinstellingen van viewer publiceren](#publishing-viewer-presets).

   >[!IMPORTANT]
   >
   >Voor oude video&#39;s die een adaptief streamingprofiel voor bitsnelheid gebruiken, wordt de URL verder op de gebruikelijke wijze afgespeeld — met HLS-streaming — totdat u [de video-elementen opnieuw verwerken](/help/assets/processing-profiles.md#reprocessing-assets). Na de opwerking blijft dezelfde URL werken, maar nu met *beide* DASH en HLS streaming ingeschakeld.

### Speciale overwegingen voor het maken van een interactieve viewervoorinstelling {#special-considerations-for-creating-an-interactive-viewer-preset}

**Informatie over weergavemodi voor afbeeldingsminiaturen in het deelvenster**

Wanneer u een voorinstelling voor een interactieve videoviewer maakt of bewerkt, kunt u kiezen welke instelling voor de weergavemodus moet worden gebruikt wanneer u `InteractiveSwatches` van de **[!UICONTROL Selected Component]** menu onder de **[!UICONTROL Behavior]** tab. De weergavemodus die u kiest, bepaalt hoe en wanneer miniaturen worden weergegeven terwijl de video wordt afgespeeld. U kunt een van de `segment`weergavemodus (standaard) of een `continuous` weergavemodus.

<table>
 <tbody>
  <tr>
   <td><strong>Weergavemodus</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Segment</td>
   <td><p><code>Segment </code>is de standaardweergavemodus voor de voorinstellingen van de uit-van-box Interactive Video Viewer <code>Shoppable_Video_light</code> en <code>Shoppable_Video_dark</code> en alle interactieve voorinstellingen voor de video-viewer die u zelf maakt.</p> <p>Wanneer in deze modus minder miniaturen zijn toegewezen aan een videosegment dan het aantal zichtbare vlekken in het deelvenster. Miniaturen uit de volgende of vorige subsegmenten zijn ook <i>niet </i>worden ingedrukt om lege vlekken in het deelvenster te vullen. Met andere woorden, het behoudt de weergave van stalen die aan het specifieke videosegment zijn toegewezen.</p> </td>
  </tr>
  <tr>
   <td>Doorlopend</td>
   <td><p>In <code>continuous </code>in de weergavemodus: als het aantal miniaturen in een segment kleiner is dan het aantal dat in het deelvenster zichtbaar is, neemt de viewer automatisch de weergave van miniaturen van het volgende segment op. Of de viewer bevat automatisch de weergave van de miniaturen van het vorige segment, in gevallen waarin de laatste miniatuur wordt weergegeven.</p> <p>De <a href="/help/assets/interactive-videos.md">video in dit onderwerp</a> is een voorbeeld van het <code>continuous </code>weergavemodus.</p> </td>
  </tr>
 </tbody>
</table>

**Over het gedrag voor automatisch schuiven in de Interactieve videoviewer**

Het gedrag voor automatisch schuiven van miniaturen in de Interactieve videoviewer werkt onafhankelijk van de gekozen weergavemodus.

Wanneer u een voorinstelling voor een interactieve videoviewer maakt of bewerkt, hebt u via het tabblad Gedrag toegang tot Automatisch schuiven. Ga op het tabblad Gedrag naar het tabblad **[!UICONTROL Selected Components]** vervolgkeuzelijst, selecteert u **[!UICONTROL InteractiveSwatches]**. Het selectievakje Automatisch schuiven wordt weergegeven onder het tekstveld IS-opdracht.

Als u **[!UICONTROL Auto Scroll]** uitschakelt (het selectievakje wist) in de viewervoorinstelling, wordt tijdens het afspelen van video door de gebruiker in het deelvenster alleen de eerste miniatuurafbeelding voor de volledige lengte van de video weergegeven. Een gebruiker kan echter desgewenst handmatig door de miniaturen bladeren met de pictogrammen pijl-omhoog en pijl-omlaag.

Wanneer u **[!UICONTROL Auto Scroll]** inschakelt (selecteert) in de viewervoorinstelling, schuiven miniatuurafbeeldingen die aan een videosegment zijn toegewezen tijdens het afspelen van de video naar het begin van een segment. Er zijn echter gevallen waarin bepaalde miniaturen in een segment tweemaal zo lang worden weergegeven als andere miniaturen ervoor of erna. Dit gedrag treedt op omdat het aantal miniaturen in een segment groter is dan het aantal dat zichtbaar is in het deelvenster en dat aantal niet gelijkmatig kan worden verdeeld.

Stel dat u een videosegment van 30 seconden hebt om dit te illustreren. En er zijn in totaal negen miniaturen die gedurende de 30 seconden moeten worden weergegeven. De grootte van de browser is zodanig dat er vier zichtbare miniatuurposities in het weergavevenster aanwezig zijn. Het videotijdsegment van 30 seconden wordt verdeeld in drie subsegmenten. In de volgende tabel wordt de verdeling weergegeven van de miniaturen voor een bepaald tijdsubsegment:

| **Video-subsegment** | **Tijd van subsegment in seconden** | **Miniaturen die zichtbaar zijn in het deelvenster** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

Het videosubsegment 3 reikt niet verder dan de miniaturen die eraan zijn toegewezen. De miniaturen 4, 6 en 7 zijn twee keer zo lang in het deelvenster zichtbaar als de andere miniaturen.

De logica die de viewer gebruikt voor het aantal miniaturen dat in het deelvenster wordt weergegeven op basis van het aantal beschikbare posities is als volgt:

* Aantal subsegmenten = rond tot volgende subsegment (aantal duimnagels/aantal zichtbare groeven in het duimnagelpaneel, gebaseerd op browser venstergrootte).
Aan de hand van het voorbeeld in de bovenstaande tabel worden 9 miniaturen / 4 sleuven = 2,25; de viewerlogica rondt deze rond in maximaal drie subsegmenten.

* Aantal miniaturen = afgerond tot op de volgende miniatuur (aantal miniaturen / aantal videosubsegmenten).
In het bovenstaande voorbeeld worden 9 miniaturen / 3 videosubsegmenten = 3 miniaturen gebruikt.

* Duur van het subsegment = totale videoduur / aantal videosubsegmenten.
Gebruikend het voorbeeld in de bovenstaande lijst, 30 seconden/3 videosubsegments = 10 secondevertoning van elk videosubsegment.

#### Speciale overwegingen voor het maken van voorinstellingen voor een Carousel Banner Viewer {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Als u voorinstellingen voor de Carousel Banner-viewer maakt, kunt u de stijl van hotspots als volgt wijzigen:

| | **Beschrijving** | **Handelingen** |
|---|---|---|
| **[!UICONTROL Hotspot Icon]** | Pictogram wijzigen dat wordt gebruikt voor hotspot | Als u de afbeelding van het hotspot-pictogram wilt wijzigen, gaat u naar **[!UICONTROL Appearance]** tab, in **[!UICONTROL Selected Component]**, selecteert u **[!UICONTROL ImageMapEffect]**. Onder **[!UICONTROL Icon]**, selecteert u **[!UICONTROL Background]** en in de **[!UICONTROL Image]** navigeer naar de gewenste achtergrondafbeelding. |

## Viewer-voorinstellingen activeren of deactiveren {#activating-or-deactivating-viewer-presets}

De Viewer-voorinstellingen die beschikbaar zijn in de gebruikersinterface, zijn afhankelijk van de vraag welke voorinstellingen actief zijn in de modus Auteur. Een viewervoorinstelling is standaard ingeschakeld nadat u deze hebt gemaakt. Als u de voorinstelling uitschakelt, wordt deze niet weergegeven in de modus Auteur. Als de voorinstelling wordt gepubliceerd, wordt deze altijd gepubliceerd, ongeacht of deze wordt in- of uitgeschakeld. U kunt voorinstellingen voor viewers desactiveren als de lijst te log wordt of als u niet wilt dat een voorinstelling voor viewers kan worden gebruikt.

**Viewer-voorinstellingen activeren of deactiveren:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.
1. Op de voorinstellingspagina van de viewer, onder de **[!UICONTROL State]** kolomkop, selecteert u de schakeloptie om een viewervoorinstelling te activeren of deactiveren.

   De voorinstellingen van de viewer die worden geactiveerd, worden rechts, in een blauw vak weergegeven. De schakeloptie wordt links in een lichtgrijs vak weergegeven wanneer de viewer wordt gedeactiveerd.

## Voorinstellingen viewer publiceren {#publishing-viewer-presets}

Als u de status van een viewervoorinstelling activeert (of inschakelt), is deze zichtbaar in de Dynamic Media-component, de interactieve mediacomponent en wanneer u een element weergeeft.

Aan *leveren* Als u middelen gebruikt met een viewer-voorinstelling, moet de viewer-voorinstelling ook worden gepubliceerd. Alle voorinstellingen van de viewer moeten worden geactiveerd *en* gepubliceerd om URL te verkrijgen of code voor een element in te sluiten. Zorg ervoor dat u alle bij Dynamic Media meegeleverde viewervoorinstellingen activeert en publiceert. Aangepaste viewervoorinstellingen die u maakt en toevoegt, worden automatisch geactiveerd, maar moeten ook worden gepubliceerd.

Zie [Viewer-voorinstellingen activeren of deactiveren](#activating-or-deactivating-viewer-presets).

Zie ook [Elementen voorvertonen](/help/assets/previewing-assets.md).

**Voorinstellingen voor viewer publiceren:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.
1. Selecteer een of meer voorinstellingen voor viewers die u wilt publiceren.
1. Selecteer op de werkbalk de optie **[!UICONTROL Publish]** pictogram.

## Viewer-voorinstellingen sorteren {#sorting-viewer-presets}

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.
1. Selecteren **[!UICONTROL Preset Title]**, **[!UICONTROL Type]**, **[!UICONTROL Published]**, of **[!UICONTROL State]** op die kolomkop te sorteren. Selecteer bijvoorbeeld **[!UICONTROL Type]**  om de typen viewervoorinstellingen in alfabetische of omgekeerde alfabetische volgorde te sorteren.

## Viewer-voorinstellingen bewerken {#editing-viewer-presets}

Alle *Voorinstellingen voor vooraf gedefinieerde viewers buiten de box* is geen ondersteund scenario. Als u een voorinstelling voor een viewer buiten de box bewerkt, wordt u gevraagd deze op te slaan onder een andere naam.

**Viewer-voorinstellingen bewerken:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Asset]** > **[!UICONTROL Viewer Presets]**.
1. Selecteer een voorinstelling door het vakje links van de titel van de voorinstelling voor de viewer in te schakelen.
1. Selecteer op de werkbalk de optie **[!UICONTROL Edit]**.
1. Op de **[!UICONTROL Viewer Preset Editor]** pagina, breng de wijzigingen aan die u in de viewer-voorinstelling wilt aanbrengen met de opties in het dialoogvenster **[!UICONTROL Appearance]** en **[!UICONTROL Behavior]** tabs.

   Van de **[!UICONTROL Appearance]** , in de linkerbovenhoek van de pagina Voorinstellingeneditor van de viewer, selecteert u **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]**, of **[!UICONTROL Phone]** om de presentatiemodus van het element te wijzigen.

1. Voer in de rechterbovenhoek van de pagina een van de volgende handelingen uit:

   * Selecteren **[!UICONTROL Save]** om uw wijzigingen op te slaan en terug te keren naar de pagina Voorinstelling viewer.
   * Selecteren **[!UICONTROL Cancel]** om wijzigingen die u hebt aangebracht te voorkomen en terug te keren naar de pagina Voorinstelling viewer.

## Aangepaste voorinstellingen viewer verwijderen {#deleting-custom-viewer-presets}

U kunt Viewer-voorinstellingen verwijderen die u hebt gemaakt en aan Dynamic Media hebt toegevoegd.

**Aangepaste voorinstellingen van viewer verwijderen:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.
1. Controleer op de pagina Voorinstellingen viewer een titel voor voorinstellingen en selecteer vervolgens de knop **[!UICONTROL Trash]** pictogram.
1. Selecteren **[!UICONTROL Delete]**.

## Een Viewer-voorinstelling toepassen op een element {#applying-a-viewer-preset-to-an-asset}

Als u zowel de asset als de geselecteerde viewer al hebt gepubliceerd, worden de knoppen **[!UICONTROL URL]** en **[!UICONTROL Embed]** weergegeven nadat u een viewervoorinstelling hebt geselecteerd.

**Een Viewer-voorinstelling toepassen op een element:**

1. Open het element in de linkerbovenhoek van de pagina en selecteer het vervolgkeuzemenu en selecteer vervolgens **[!UICONTROL Viewers]**.

   >[!NOTE]
   >
   >Als u zowel de asset als de geselecteerde viewer al hebt gepubliceerd, worden de knoppen **[!UICONTROL URL]** en **[!UICONTROL Embed]** weergegeven nadat u een viewervoorinstelling hebt geselecteerd.

1. Selecteer een viewervoorinstelling in het linkerdeelvenster, zodat u deze op het element kunt toepassen.

   U kunt [de URL kopiëren die u wilt delen](/help/assets/linking-urls-to-yourwebapplication.md) met andere gebruikers.

## Elementen leveren met voorinstellingen voor viewers {#delivering-assets-with-viewer-presets}

Als u de URL&#39;s voor Viewer-voorinstellingen wilt ophalen, raadpleegt u [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md). Zie ook [De video-viewer insluiten op een webpagina](/help/assets/embed-code.md).

Als u Experience Manager als uw WCM gebruikt, kunt u elementen toevoegen met behulp van de voorinstellingen van de viewer rechtstreeks op de pagina. Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).
