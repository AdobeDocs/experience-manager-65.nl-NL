---
title: Dynamic Media-elementen toevoegen aan pagina's
description: Dynamic Media-componenten toevoegen aan een pagina in Adobe Experience Manager
uuid: b5e982f5-fa1c-478a-bcb3-a1ef980df201
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 97a5f018-8255-4b87-9d21-4a0fdf740e4d
docset: aem65
role: User, Admin
exl-id: 62d4a38c-2873-4560-8d58-ad172288764d
feature: componenten,publiceren
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '3085'
ht-degree: 6%

---

# Dynamic Media-elementen toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Als u de functionaliteit voor dynamische media wilt toevoegen aan assets die u op uw websites gebruikt, kunt u de component **Dynamische media**, **Interactieve media**, **Panoramische media** of **Video 360-media** rechtstreeks op de pagina toevoegen. U voegt componenten toe door de modus Lay-out in te voeren en de Dynamic Media-componenten in te schakelen. Vervolgens kunt u deze componenten aan de pagina toevoegen en assets aan de component toevoegen. De componenten voor dynamische media zijn slim: ze weten of u een afbeelding of een video toevoegt en de beschikbare configuratieopties veranderen dienovereenkomstig.

U voegt Dynamic Media-elementen rechtstreeks aan de pagina toe als u Adobe Experience Manager als uw WCM gebruikt. Als u een derde voor uw WCM gebruikt, of [link](/help/assets/linking-urls-to-yourwebapplication.md) of [embed](/help/assets/embed-code.md) uw activa. Voor een responsieve website van derden raadpleegt u het [leveren van geoptimaliseerde afbeeldingen op een responsieve site](/help/assets/responsive-site.md).

>[!NOTE]
>
>Zorg ervoor dat u elementen publiceert voordat u deze in Experience Manager aan pagina&#39;s toevoegt. Zie [Dynamic Media-middelen publiceren](/help/assets/publishing-dynamicmedia-assets.md).

## Een Dynamic Media-component aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van een 3D-mediacomponent, Dynamic Media, Interactieve media, Panoramische media, SmartCrop-video of Video 360-mediacomponent aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. De Dynamic Media-componenten worden in de volgende secties beschreven.

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Klik in het deelvenster aan de linkerkant van de pagina (indien nodig op het pictogram **[!UICONTROL Components]** om de weergave van het zijpaneel in of uit te schakelen).
1. Selecteer **[!UICONTROL Dynamic Media]** onder de kop **[!UICONTROL Components]** in de vervolgkeuzelijst.

   Als er geen lijst met Dynamic Media-componenten beschikbaar is, moet u de Dynamic Media-componenten inschakelen die u wilt gebruiken. Zie [Dynamic Media-componenten inschakelen](#enabling-dynamic-media-components).

   ![6_5_360video_wcmcomponent](/help/assets/assets/6_5_360video_wcmcomponent.png)

1. Sleep een **[!UICONTROL Dynamic Media]** component die u wilt gebruiken en zet het op de gewenste plaats op de pagina neer.

1. Houd de muisaanwijzer rechtstreeks boven de component. Tik eenmaal om de werkbalk van de component weer te geven wanneer de component is omringd door een blauw vak. Tik op het pictogram **[!UICONTROL Configuration (wrench)]**.

   ![6_5_360video_wcmcomponentconfigure](/help/assets/assets/6_5_360video_wcmcomponentconfigure.png)

1. Afhankelijk van de Dynamic Media-component die u op de pagina hebt neergezet, wordt een configuratiedialoogvenster geopend. [Stel de ](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) opties van de component naar wens in.

   In het onderstaande voorbeeld ziet u het dialoogvenster Dynamic Media **[!UICONTROL Video 360 Media]** en de opties die beschikbaar zijn in de vervolgkeuzelijst Voorinstelling viewer.

   ![Video 360-mediacomponent](assets/6_5_360video_wcmcomponentviewerpreset.png)

   De Dynamic Media Video 360 Media-component.

1. Als u klaar bent, tikt u in de rechterbovenhoek van het dialoogvenster op het vinkje om de wijzigingen op te slaan.

### Dynamic Media-componenten inschakelen {#enabling-dynamic-media-components}

Als er geen Dynamic Media-componenten beschikbaar zijn om aan een pagina toe te voegen, betekent dit waarschijnlijk dat u eerst de componenten moet inschakelen die u wilt gebruiken.

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Tik links op de werkbalk naast de pagina op het pictogram Pagina-informatie en tik vervolgens op **[!UICONTROL Edit Template]** in de vervolgkeuzelijst.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Tik in de vervolgkeuzelijst rechts van de werkbalk naast de pagina op **[!UICONTROL Structure]**.

   ![Beleid](/help/assets/assets-dm/structure-mode.png)

1. Tik onder aan de pagina op **[!UICONTROL Layout Container]** om de werkbalk te openen en tik vervolgens op het pictogram Beleid.
1. Controleer of op de pagina **[!UICONTROL Layout Container]** onder de kop **[!UICONTROL Properties]** het tabblad **[!UICONTROL Allowed Components]** is geselecteerd.

   ![Toegestane componenten](/help/assets/assets-dm/allowed-components.png)

1. Schuif totdat u **[!UICONTROL Dynamic Media]** ziet.
1. Tik op het pictogram > links van **[!UICONTROL Dynamic Media]** zodat u de lijst kunt uitvouwen en vervolgens de Dynamic Media-componenten die u wilt inschakelen selecteren.

   ![Lijst met Dynamic Media-componenten](/help/assets/assets-dm/dm-components-select.png)

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Layout Container]** op het pictogram Gereed (vinkje).

1. Tik in de vervolgkeuzelijst rechts op de werkbalk boven aan de pagina op **[!UICONTROL Initial Content]** en voeg vervolgens [zoals gewoonlijk een Dynamic Media-component toe aan een pagina](#adding-a-dynamic-media-component-to-a-page).

## Dynamic Media-componenten lokaliseren {#localizing-dynamic-media-components}

U kunt Dynamic Media-componenten op twee manieren lokaliseren:

* Open **[!UICONTROL Properties]** en selecteer het tabblad **[!UICONTROL Advanced]** op een webpagina in Sites. Selecteer de gewenste taal voor lokalisatie.

   ![chlimage_1-172](assets/chlimage_1-538.png)

* Selecteer de gewenste pagina of paginagroep in de sitekiezer. Tik **[!UICONTROL Properties]** en selecteer het tabblad **[!UICONTROL Advanced]**. Selecteer de gewenste taal voor lokalisatie.

   >[!NOTE]
   >
   >Niet alle talen in het menu **[!UICONTROL Language]** hebben tokens toegewezen.

## Dynamic Media-componenten {#dynamic-media-components}

Dynamic Media-componenten zijn beschikbaar wanneer u op het **[!UICONTROL Components]**-pictogram tikt en vervolgens op **[!UICONTROL Dynamic Media]** filtert.

De volgende Dynamic Media-componenten zijn beschikbaar:

* **[!UICONTROL Dynamic Media]** - Wordt gebruikt voor assets zoals afbeeldingen, video, e-catalogi en spinsets.
* **[!UICONTROL Interactive Media]** - Wordt gebruikt voor interactieve elementen zoals interactieve video, interactieve afbeeldingen of carrouselsets.
* **[!UICONTROL Panoramic Media]** - Gebruik voor panoramische afbeeldingen of panoramische VR-afbeeldingselementen.
* **[!UICONTROL Video 360 Media]** - Wordt gebruikt voor 360 video- en 360 VR-video-elementen.

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar; ze moeten beschikbaar worden gesteld in de sjablooneditor voordat u ze kunt gebruiken. [Nadat zij ](/help/sites-authoring/templates.md#editing-templates-template-authors)in de malplaatjeredacteur ter beschikking worden gesteld, kunt u de componenten aan uw pagina toevoegen zoals u een andere component van de Experience Manager.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### Dynamic Media-component {#dynamic-media-component}

De Dynamic Media-component is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de Dynamic Media-component die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.

>
>
Het toewijzen van een andere viewervoorinstelling aan elke Dynamic Media-component op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Dynamic Media-componenten die op de pagina elementen van hetzelfde type gebruiken.

Wanneer u de Dynamic Media-component toevoegt en **[!UICONTROL Dynamic Media Settings]** leeg is of wanneer u een element niet correct kunt toevoegen, controleert u het volgende:

* U hebt [ingeschakelde Dynamic Media](/help/assets/config-dynamic.md). Dynamic Media is standaard uitgeschakeld.
* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die u importeert voordat u Dynamic Media inschakelt, beschikken niet over een TIFF-bestand met piramide.

#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de Dynamic Media-component kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

Bewerk de volgende Dynamic Media-instellingen door te tikken op het pictogram **[!UICONTROL Edit]** in de component en vervolgens **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

   Dit is de enige optie die beschikbaar is als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt. De weergegeven viewervoorinstellingen zijn slim. Alleen relevante viewervoorinstellingen worden weergegeven.

* **[!UICONTROL Viewer modifiers]** - Viewer-modifiers hebben de vorm van name=value pair met een &amp;-scheidingsteken en laten u viewers wijzigen zoals beschreven in de Viewer Reference Guide. Een voorbeeld van een viewermodifier is `posterimage=img.jpg&caption=text.vtt,1`, die een andere afbeelding instelt voor de videominiatuur en een ondertitelingsbestand aan de video koppelt.

* **[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te geven. Deze effecten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Breakpoints]** - Als u dit middel op een ontvankelijke plaats gebruikt, moet u de beeldbreekpunten toevoegen. Afbeeldingsonderbrekingspunten worden gescheiden door komma&#39;s (,). Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

   U kunt de volgende Geavanceerde Montages uitgeven door **[!UICONTROL Edit]** in de component te tikken.

* **[!UICONTROL Optimize for higher resolution devices]** - Schakel het selectievakje (standaard) in om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

   De optie **[!UICONTROL Optimize for higher resolution devices]** wordt alleen weergegeven wanneer het volgende true is:

   * Onder Type voorinstelling wordt **[!UICONTROL Image Preset]** geselecteerd en wordt **[!UICONTROL RESS_IP]** geselecteerd in de vervolgkeuzelijst **[!UICONTROL Image Preset]**.

   ![instelling voor pixelverhouding van apparaat voor voorinstelling afbeelding](/help/assets/assets-dm/dpr-ress-ip.png)

   Zie ook [Optimalisatie pixelverhouding apparaat](/help/assets/imaging-faq.md#dpr). Alle Adobe Experience Manager Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel aan de afbeelding toe voor gebruikers die afbeeldingen hebben uitgeschakeld.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.


#### Wanneer u werkt met video {#when-working-with-video}

Met de Dynamic Media-component kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![chlimage_1-173](assets/chlimage_1-540.png)

Bewerk de volgende Dynamic Media-instellingen door in de component op **[!UICONTROL Edit]** te klikken.

>[!NOTE]
>
>De Dynamic Media-videocomponent is standaard adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component met **[!UICONTROL Width]** en **[!UICONTROL Height]** in **[!UICONTROL Advanced]** tabel.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

* **[!UICONTROL Viewer modifiers]** - Viewer-modifiers hebben de vorm van name=value pair met een &amp;-scheidingsteken en laten u viewers wijzigen zoals beschreven in de Adobe Viewers Reference Guide. Een voorbeeld van een viewermodifier is `posterimage=img.jpg&caption=text.vtt,1`

   Met viewermodifiers kunt u bijvoorbeeld het volgende doen:

   * Een bijschriftbestand koppelen aan een video: [caption][https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Een navigatiebestand koppelen aan een video: [navigatie][https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

      U kunt de volgende Geavanceerde Montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met Slim uitsnijden {#when-working-with-smart-crop}

Met de Dynamic Media-component kunt u SmartCrop-afbeeldingselementen toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

Zie ook [Afbeeldingsprofielen](/help/assets/image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

Bewerk de volgende Dynamic Media-instelling door in de component op **[!UICONTROL Edit]** te klikken.

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te geven. Deze effecten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

   U kunt de volgende Geavanceerde Montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

* **[!UICONTROL Enable Aspect Ration match]** - Selecteer deze optie als u wilt dat Dynamic Media een slimme uitsnijdvertoning kiest met een hoogte-breedteverhouding die het beste overeenkomt met de hoogte-breedteverhouding van de oorspronkelijke afbeelding.

* **[!UICONTROL Optimize for higher resolution devices]** - Schakel het selectievakje (standaard) in om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

   De optie **[!UICONTROL Optimize for higher resolution devices]** wordt alleen weergegeven wanneer het volgende true is:

   * Onder Type voorinstelling is de optie **[!UICONTROL Smart Crop]** geselecteerd.

   ![instelling voor pixelverhouding van apparaat voor slim uitsnijden](/help/assets/assets-dm/dpr-smartcrop.png)

   Zie ook [Optimalisatie pixelverhouding apparaat](/help/assets/imaging-faq.md#dpr). Alle Adobe Experience Manager Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de slimme-uitsnijdafbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel toe aan de slimme-uitsnijdafbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

### Interactieve mediacomponent {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Als u een interactieve afbeelding, interactieve video of carrouselbanner hebt, gebruikt u de component **[!UICONTROL Interactive Media]**.

De component Interactieve media is slim. U hebt verschillende opties, of u nu een afbeelding of video toevoegt. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component Interactive Media die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.

>
>
Het toewijzen van een andere viewervoorinstelling aan elke interactieve mediacomponent op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle interactieve mediacomponenten die op de pagina elementen van hetzelfde type gebruiken.

![chlimage_1-174](assets/chlimage_1-541.png)

U kunt de volgende **[!UICONTROL General]** montages uitgeven door **[!UICONTROL Edit]** in de component te tikken.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

   U kunt de volgende **[!UICONTROL Add To Cart]** montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

* **[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. Het productelement toont een afbeelding van het product zoals gedefinieerd in de module Handel. Schakel het vinkje uit om het productelement niet weer te geven.

* **[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

* **[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.

### Panoramische mediacomponent {#panoramic-media-component}

Panoramische media-component is bedoeld voor die elementen die bolvormige panoramische afbeeldingen zijn. Dergelijke afbeeldingen bieden een kijkervaring van 360° voor een ruimte, eigenschap, locatie of landschap. Een afbeelding kan alleen als bolvormig panorama worden beschouwd als de afbeelding een van de volgende opties of beide heeft:

* Een hoogte-breedteverhouding van 2:1.
* Gelabeld met de trefwoorden `equirectangular` of (`spherical` + `panorama`) of (`spherical` + `panoramic`). Zie [Tags gebruiken](/help/sites-authoring/tags.md).

Zowel de criteria voor hoogte-breedteverhouding als voor trefwoorden zijn van toepassing op panoramische assets voor de pagina met assetdetails en de **[!UICONTROL Panoramic Media]** WCM-component.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component **[!UICONTROL Panoramic Media]** die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.

>
>
Het toewijzen van een andere viewervoorinstelling aan elke **[!UICONTROL Panoramic Media]**-component op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Panoramische Media-componenten die elementen van hetzelfde type gebruiken, op de pagina.

![panoramisch-media-viewer-voorinstelling](assets/panoramic-media-viewer-preset.png)

U kunt de volgende instelling bewerken door te tikken op **[!UICONTROL Configure]** in de component.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Publiceer viewervoorinstellingen voordat u deze gebruikt. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

### Video 360-mediacomponent {#video-media-component}

Met de component **[!UICONTROL Video 360 Media]** kunt u rechthoekige video op uw webpagina renderen voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap of medische procedure.

Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; Bij het afspelen op mobiele apparaten worden doorgaans de ingebouwde gyroscopische besturingselementen gebruikt.

De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

U kunt de volgende instelling bewerken door te tikken op **[!UICONTROL Configure]** in de component.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer. Gebruik Video360VR voor eindgebruikers die een virtuele realiteitsbril gebruiken. Bevat basisbesturingselementen voor het afspelen van video en functies voor sociale media. Gebruik Video360_social, die basisbesturingselementen voor het afspelen van video bevat. Video renderen wordt uitgevoerd in de stereomodus. Handmatige zichtpuntcontrole is uitgeschakeld, maar gyroscopische controle is ingeschakeld. Er zijn geen functies voor sociale media.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Zorg ervoor dat u viewervoorinstellingen publiceert voordat u deze gebruikt. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

### HTTP/2 gebruiken om Dynamic Media-elementen te leveren {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-middelen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van Inhoud](/help/assets/http2.md) voor volledige informatie over het gaan gebruiken van HTTP/2 met uw Dynamic Media-account.

>[!MORELIKETHIS]
>
>* [De videospeler gebruiken in Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-video-player-feature-video-use.html)
>* [Interactieve video gebruiken met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html)
>* [De Asset Viewer begrijpen met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-viewer-feature-video-understand.html)
>* [Aangepaste videominiatuur gebruiken met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Werken met kleurbeheer met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-color-management-technical-video-setup.html)
>* [Afbeelding verscherpen gebruiken met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html)

