---
title: Dynamic Media Assets toevoegen aan pagina's
description: Dynamic Media-componenten toevoegen aan een pagina in Adobe Experience Manager.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: 62d4a38c-2873-4560-8d58-ad172288764d
feature: Components,Publishing
solution: Experience Manager, Experience Manager Assets
source-git-commit: ed7183efa57db6d97941e3acc99d126c2fc0f6c5
workflow-type: tm+mt
source-wordcount: '3063'
ht-degree: 5%

---

# Dynamic Media-elementen toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Om de functionaliteit van Dynamic Media aan activa toe te voegen die u op uw websites gebruikt, kunt u **Dynamic Media**, **Interactieve Media**, **Panoramische Media**, of **Video 360 Media** component direct op de pagina toevoegen. U voegt componenten toe door de modus Lay-out in te voeren en de Dynamic Media-componenten in te schakelen. Vervolgens kunt u deze componenten aan de pagina toevoegen en assets aan de component toevoegen. De componenten voor dynamische media zijn slim: ze weten of u een afbeelding of een video toevoegt en de beschikbare configuratieopties veranderen dienovereenkomstig.

U kunt Dynamic Media-elementen rechtstreeks aan de pagina toevoegen als u Adobe Experience Manager als uw WCM gebruikt. Als u een oplossing van derden gebruikt voor uw WCM, moet u uw assets [koppelen](/help/assets/linking-urls-to-yourwebapplication.md) of [insluiten](/help/assets/embed-code.md). Voor een responsieve website van derden raadpleegt u het [leveren van geoptimaliseerde afbeeldingen op een responsieve site](/help/assets/responsive-site.md).

>[!NOTE]
>
>Zorg ervoor dat u elementen publiceert voordat u deze in Experience Manager aan pagina&#39;s toevoegt. Zie {de activa van Dynamic Media van 0} Publish [&#128279;](/help/assets/publishing-dynamicmedia-assets.md).

## Een Dynamic Media-component aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van een 3D-mediacomponent, Dynamic Media, Interactieve media, Panoramische media, SmartCrop-video of Video 360-mediacomponent aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. De Dynamic Media-componenten worden in de volgende secties beschreven.

**om een component van Dynamic Media aan een pagina toe te voegen:**

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Selecteer het pictogram **[!UICONTROL Components]** in het deelvenster aan de linkerkant van de pagina (indien nodig de weergave van het zijpaneel in-/uitschakelen).
1. Selecteer onder de kop **[!UICONTROL Components]** in de vervolgkeuzelijst de optie **[!UICONTROL Dynamic Media]** .

   Als er geen lijst met Dynamic Media-componenten beschikbaar is, moet u de Dynamic Media-componenten inschakelen die u wilt gebruiken. Zie [ de componenten van Dynamic Media ](#enabling-dynamic-media-components) toelaten.

   ![ 6_5_360video_wcmcomponent ](/help/assets/assets/6_5_360video_wcmcomponent.png)

1. Sleep een **[!UICONTROL Dynamic Media]** -component die u wilt gebruiken en zet deze op de gewenste locatie op de pagina neer.

1. Houd de muisaanwijzer rechtstreeks boven de component. Wanneer de component door een blauw vakje wordt omringd, selecteer eens om de toolbar van de component te tonen. Selecteer het pictogram **[!UICONTROL Configuration (wrench)]** .

   ![ 6_5_360video_wcmcomponentconfigure ](/help/assets/assets/6_5_360video_wcmcomponentconfigure.png)

1. Afhankelijk van de Dynamic Media-component die u op de pagina hebt neergezet, wordt een configuratiedialoogvenster geopend. [ plaats de opties van de component ](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) zonodig.

   In het onderstaande voorbeeld ziet u het dialoogvenster Dynamic Media **[!UICONTROL Video 360 Media]** -component en de opties die beschikbaar zijn in de vervolgkeuzelijst Voorinstelling viewer.

   ![ Video 360 de component van Media ](assets/6_5_360video_wcmcomponentviewerpreset.png)

   De Dynamic Media Video 360 Media-component.

1. Als u klaar bent, selecteert u in de rechterbovenhoek van het dialoogvenster het vinkje waarop u de wijzigingen wilt opslaan.

### Dynamic Media-componenten inschakelen {#enabling-dynamic-media-components}

Als er geen Dynamic Media-componenten beschikbaar zijn om aan een pagina toe te voegen, betekent dit waarschijnlijk dat u eerst de componenten moet inschakelen die u wilt gebruiken.

**om de componenten van Dynamic Media toe te laten:**

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Selecteer links op de werkbalk naast de pagina het pictogram Pagina-informatie en selecteer vervolgens **[!UICONTROL Edit Template]** in de vervolgkeuzelijst.

   ![ geef-malplaatje uit ](/help/assets/assets-dm/edit-template.png)

1. Selecteer in de vervolgkeuzelijst rechts van de werkbalk boven aan de pagina de optie **[!UICONTROL Structure]** .

   ![ Beleid ](/help/assets/assets-dm/structure-mode.png)

1. Selecteer onder aan de pagina de optie **[!UICONTROL Layout Container]** om de werkbalk van de pagina te openen en selecteer vervolgens het pictogram Beleid.
1. Controleer of op de pagina **[!UICONTROL Layout Container]** onder de kop **[!UICONTROL Properties]** het tabblad **[!UICONTROL Allowed Components]** is geselecteerd.

   ![ Toegestane componenten ](/help/assets/assets-dm/allowed-components.png)

1. Schuif totdat u **[!UICONTROL Dynamic Media]** ziet.
1. Selecteer het pictogram > links van **[!UICONTROL Dynamic Media]** , zodat u de lijst kunt uitvouwen en vervolgens de Dynamic Media-componenten die u wilt inschakelen.

   ![ de componentenlijst van Dynamic Media ](/help/assets/assets-dm/dm-components-select.png)

1. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Layout Container]** het pictogram Gereed (vinkje).

1. Op de rechterkant van de toolbar dichtbij de bovenkant van de pagina, van de drop-down lijst, selecteer **[!UICONTROL Initial Content]**, dan [ voeg een component van Dynamic Media aan een pagina ](#adding-a-dynamic-media-component-to-a-page) toe zoals gebruikelijk.

## Dynamic Media-componenten lokaliseren {#localizing-dynamic-media-components}

U kunt Dynamic Media-componenten op twee manieren lokaliseren:

* Open **[!UICONTROL Properties]** en selecteer het tabblad **[!UICONTROL Advanced]** op een webpagina in Sites. Selecteer de gewenste taal voor lokalisatie.

  ![ chlimage_1-172 ](assets/chlimage_1-538.png)

* Selecteer de gewenste pagina of paginagroep in de sitekiezer. Selecteer **[!UICONTROL Properties]** en selecteer de tab **[!UICONTROL Advanced]** . Selecteer de gewenste taal voor lokalisatie.

  >[!NOTE]
  >
  >Niet alle talen die beschikbaar zijn in het menu **[!UICONTROL Language]** , hebben tokens toegewezen.

## Dynamic Media-componenten {#dynamic-media-components}

Dynamic Media-componenten zijn beschikbaar wanneer u het pictogram **[!UICONTROL Components]** selecteert en vervolgens op **[!UICONTROL Dynamic Media]** filtert.

De volgende Dynamic Media-componenten zijn beschikbaar:

* **[!UICONTROL Dynamic Media]** - Wordt gebruikt voor assets zoals afbeeldingen, video, e-catalogi en spinsets.
* **[!UICONTROL Interactive Media]** - Wordt gebruikt voor interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets.
* **[!UICONTROL Panoramic Media]** - Wordt gebruikt voor panoramische afbeeldingen of voor VR-afbeeldingselementen voor panoramische afbeeldingen.
* **[!UICONTROL Video 360 Media]** - Gebruik voor 360 video- en 360 VR-video-elementen.

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar; ze moeten beschikbaar worden gesteld in de sjablooneditor voordat u ze gebruikt. [ nadat zij beschikbaar worden gemaakt i ](/help/sites-authoring/templates.md#editing-templates-template-authors) in de malplaatjedacteur, kunt u de componenten aan uw pagina toevoegen aangezien u een andere component van de Experience Manager zou.

![ 6_5_dynamicmediawcmcomponents ](assets/6_5_dynamicmediawcmcomponents.png)

### Dynamic Media-component {#dynamic-media-component}

De Dynamic Media-component is slim. U hebt verschillende opties, of u nu een afbeelding of video toevoegt. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de Dynamic Media-component die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Het toewijzen van een andere viewervoorinstelling aan elke Dynamic Media-component op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Dynamic Media-componenten die op de pagina elementen van hetzelfde type gebruiken.

Wanneer u de Dynamic Media-component toevoegt en **[!UICONTROL Dynamic Media Settings]** leeg is of wanneer u een element niet correct kunt toevoegen, controleert u het volgende:

* U hebt [ toegelaten Dynamic Media ](/help/assets/config-dynamic.md). Dynamic Media is standaard uitgeschakeld.
* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die u importeert voordat u Dynamic Media inschakelt, beschikken niet over een TIFF-bestand met piramide.

#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de Dynamic Media-component kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

Bewerk de volgende Dynamic Media-instellingen door het pictogram **[!UICONTROL Edit]** in de component te selecteren en vervolgens **[!UICONTROL Dynamic Media Settings]** .

![ dm-montages-beeld-vooraf ingesteld ](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [ vooraf instelt van de kijker beheren ](/help/assets/managing-viewer-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

  Dit is de enige optie die beschikbaar is als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt. De weergegeven viewervoorinstellingen zijn slim. Alleen relevante viewervoorinstellingen worden weergegeven.

* **[!UICONTROL Viewer modifiers]** - Viewer-modifiers hebben de vorm van name=value pair met een &amp;-scheidingsteken en laten u viewers wijzigen zoals wordt beschreven in de Viewer Reference Guide. Een voorbeeld van een viewermodifier is `posterimage=img.jpg&caption=text.vtt,1` die een andere afbeelding instelt voor de videominiatuur en een ondertitelingsbestand aan de video koppelt.

* **[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor afbeeldingen in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te geven. Deze effecten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Breakpoints]** - Als u dit middel op een ontvankelijke plaats gebruikt, moet u de beeldbreekpunten toevoegen. Afbeeldingsonderbrekingspunten worden gescheiden door komma&#39;s (,). Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

  U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Optimize for higher resolution devices]** - Selecteer (standaard) het selectievakje om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

  De optie **[!UICONTROL Optimize for higher resolution devices]** wordt alleen weergegeven als het volgende true is:

   * Onder Type voorinstelling wordt **[!UICONTROL Image Preset]** geselecteerd en wordt **[!UICONTROL RESS_IP]** geselecteerd in de vervolgkeuzelijst **[!UICONTROL Image Preset]** .

  ![ het plaatsen van de de pixelverhouding van het apparaat voor vooraf ingesteld beeld ](/help/assets/assets-dm/dpr-ress-ip.png)

  Zie ook [ Ongeveer de optimalisering van de apparatenpixelverhouding ](/help/assets/imaging-faq.md#dpr). Alle Adobe Experience Manager Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel toe aan de afbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Plaats URL en in **Open in** wijzen erop of u het in het zelfde venster of een nieuw venster wilt openen.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met video {#when-working-with-video}

Met de Dynamic Media-component kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![ chlimage_1-173 ](assets/chlimage_1-540.png)

Bewerk de volgende Dynamic Media-instellingen door **[!UICONTROL Edit]** in de component te selecteren.

>[!NOTE]
>
>De Dynamic Media-videocomponent is standaard adaptief. Als u een vaste grootte wilt maken, stelt u deze in de component in met de tabbladen **[!UICONTROL Width]** en **[!UICONTROL Height]** **[!UICONTROL Advanced]** .

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [ vooraf instelt van de kijker beheren ](/help/assets/managing-viewer-presets.md).

* **[!UICONTROL Viewer modifiers]** - Viewer-modifiers hebben de vorm van name=value pair met een &amp;-scheidingsteken en laten u viewers wijzigen zoals wordt beschreven in de Adobe Viewers Reference Guide. Een voorbeeld van een viewer-modifier is `posterimage=img.jpg&caption=text.vtt,1`

  Met viewermodifiers kunt u bijvoorbeeld het volgende doen:

   * Koppel een bijschriftdossier met een video: [ titel ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Koppel een navigatiedossier met een video: [ navigatie ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

     U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met Slim uitsnijden {#when-working-with-smart-crop}

Met de Dynamic Media-component kunt u SmartCrop-afbeeldingselementen toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

Zie ook [ Profielen van het Beeld ](/help/assets/image-profiles.md).

![ dm-settings-smart-gewas ](assets/dm-settings-smart-crop.png)

Bewerk de volgende Dynamic Media-instelling door **[!UICONTROL Edit]** in de component te selecteren.

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te geven. Deze effecten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

  U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Enable Aspect Ratio match]** - Als u wilt dat Dynamic Media een slimme-uitsnijdvertoning kiest met een hoogte-breedteverhouding die het beste overeenkomt met de hoogte-breedteverhouding van de oorspronkelijke afbeelding, selecteert u deze optie.

* **[!UICONTROL Optimize for higher resolution devices]** - Selecteer (standaard) het selectievakje om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

  De optie **[!UICONTROL Optimize for higher resolution devices]** wordt alleen weergegeven als het volgende true is:

   * Onder Type voorinstelling is de optie **[!UICONTROL Smart Crop]** geselecteerd.

  ![ het plaatsen van de de pixelverhouding van het apparaat voor slimme gewas ](/help/assets/assets-dm/dpr-smartcrop.png)

  Zie ook [ Ongeveer de optimalisering van de apparatenpixelverhouding ](/help/assets/imaging-faq.md#dpr). Alle Adobe Experience Manager Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de slimme-uitsnijdafbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel toe aan de slimme-uitsnijdafbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

### Interactieve media-component {#interactive-media-component}

De component Interactieve media is bedoeld voor elementen die interactiviteit op deze elementen hebben, zoals hotspots of afbeeldingen met hyperlinks. Gebruik de component **[!UICONTROL Interactive Media]** als u een interactieve afbeelding, interactieve video of carrouselbanner hebt.

De component Interactieve media is slim. U hebt verschillende opties, of u nu een afbeelding of video toevoegt. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component Interactive Media die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Het toewijzen van een andere viewervoorinstelling aan elke interactieve mediacomponent op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle interactieve mediacomponenten die op de pagina elementen van hetzelfde type gebruiken.

![ chlimage_1-174 ](assets/chlimage_1-541.png)

U kunt de volgende **[!UICONTROL General]** -instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer de waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

  U kunt de volgende **[!UICONTROL Add To Cart]** -instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. In het productelement ziet u een afbeelding van het product, zoals gedefinieerd in de Commerce-module. Schakel het vinkje uit, zodat het element product niet wordt weergegeven.

* **[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Commerce. Schakel het vinkje uit zodat de productprijs niet wordt weergegeven.

* **[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit zodat de productvarianten niet worden weergegeven.

### Panoramische mediacomponent {#panoramic-media-component}

Panoramische media-component is bedoeld voor die elementen die bolvormige panoramische afbeeldingen zijn. Dergelijke afbeeldingen bieden een kijkervaring van 360 graden voor een ruimte, eigenschap, locatie of landschap. Een afbeelding kan alleen als bolvormig panorama worden beschouwd als de afbeelding een van de volgende opties of beide heeft:

* Een hoogte-breedteverhouding van 2:1.
* Gelabeld met de trefwoorden `equirectangular` of (`spherical` + `panorama`) of (`spherical` + `panoramic`). Zie [ Gebruikend Markeringen ](/help/sites-authoring/tags.md).

Zowel de criteria voor hoogte-breedteverhouding als voor trefwoorden zijn van toepassing op panoramische assets voor de pagina met assetdetails en de **[!UICONTROL Panoramic Media]** WCM-component.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component **[!UICONTROL Panoramic Media]** die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Het toewijzen van een andere viewervoorinstelling aan elke **[!UICONTROL Panoramic Media]** -component op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Panoramische Media-componenten die elementen van hetzelfde type gebruiken, op de pagina.

![ panoramisch-media-kijker-vooraf ingesteld ](assets/panoramic-media-viewer-preset.png)

U kunt de volgende instelling bewerken door **[!UICONTROL Configure]** in de component te selecteren.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Publish-viewervoorinstellingen voordat u deze gebruikt. Zie [ het Leiden Kijker stelt ](/help/assets/managing-viewer-presets.md) vooraf in.

### Video 360 Media-component {#video-media-component}

Gebruik de component **[!UICONTROL Video 360 Media]** om rechthoekige video op uw webpagina te renderen voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap of medische procedure.

Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; bij het afspelen op mobiele apparaten worden doorgaans de ingebouwde gyroscopische besturingselementen gebruikt.

De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

![ 6_5_360video_wcmcomponent-1 ](assets/6_5_360video_wcmcomponent-1.png)

U kunt de volgende instelling bewerken door **[!UICONTROL Configure]** in de component te selecteren.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer. Gebruik `Video360VR` voor eindgebruikers die een virtuele realiteitsbril gebruiken. Het omvat basisbesturingselementen voor het afspelen van video en functies voor sociale media. Gebruik `Video360_social` dat elementaire besturingselementen voor het afspelen van video bevat. Video renderen wordt uitgevoerd in de stereomodus. Handmatige zichtpuntcontrole is uitgeschakeld, maar gyroscopische controle is ingeschakeld. Er zijn geen functies voor sociale media.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Zorg ervoor dat u viewervoorinstellingen publiceert voordat u deze gebruikt. Zie [ het Leiden Kijker stelt ](/help/assets/managing-viewer-presets.md) vooraf in.

### HTTP/2 gebruiken om Dynamic Media-elementen te leveren {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-elementen kan nu plaatsvinden via HTTP/2, waardoor de responstijd en laadtijd beter zijn.

Zie [ HTTP2 Levering van Inhoud ](/help/assets/http2.md) voor volledige details bij het worden begonnen HTTP/2 met uw rekening van Dynamic Media te gebruiken.

>[!MORELIKETHIS]
>
>* [ Gebruik de videospeler in Experience Manager Dynamic Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-player-feature-video-use.html)
>* [ Interactieve Video van het Gebruik met Experience Manager Dynamic Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-interactive-video-feature-video-use.html)
>* [ Begrijp de Kijker van Activa met Experience Manager Dynamic Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/viewers/dynamic-media-viewer-feature-video-understand.html)
>* [ Gebruik een duimnagel van de douanevideo met Experience Manager Dynamic Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-thumbnails-feature-video-use.html)
>* [ Begrijp kleurenbeheer met Experience Manager Dynamic Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-color-management-technical-video-setup.html)
>* [ Gebruikend beeld verscherpen met Experience Manager Dynamic Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use.html)
