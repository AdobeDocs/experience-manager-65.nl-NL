---
title: Dynamic Media-assets aan pagina's toevoegen
seo-title: Dynamic Media-assets aan pagina's toevoegen
description: Als u de functionaliteit voor dynamische media wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de Dynamic Media of de component Interactieve media rechtstreeks op de pagina toevoegen.
seo-description: Als u de functionaliteit voor dynamische media wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de Dynamic Media of de component Interactieve media rechtstreeks op de pagina toevoegen.
uuid: 650d0867-a079-4936-a466-55b7a30803a2
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 331f4980-5193-4546-a22e-f27e38bb8250
translation-type: tm+mt
source-git-commit: 23dfcc944a83dd683078cfe00f85c4cc734e7752
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 2%

---


# Dynamic Media-assets aan pagina&#39;s toevoegen{#adding-dynamic-media-assets-to-pages}

To add the Dynamic Media functionality to assets you use on your websites, you can add the **[!UICONTROL Dynamic Media]** or **[!UICONTROL Interactive Media]** component directly on the page. You do this by entering [!UICONTROL Design] mode and enabling the dynamic media components. Vervolgens kunt u deze componenten aan de pagina toevoegen en assets aan de component toevoegen. De dynamische media en interactieve mediacomponenten zijn slim: ze weten of u een afbeelding of video toevoegt en de beschikbare opties veranderen dienovereenkomstig.

U voegt dynamische media-elementen rechtstreeks aan de pagina toe als u AEM als uw WCM gebruikt.

>[!NOTE]
>
>Afbeeldingen met hyperlinks zijn beschikbaar in het vak voor carrouselbanners.

## Een component Dynamic Media toevoegen aan een pagina {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van de component [!UICONTROL Dynamic Media] of [!UICONTROL Interactive Media] component aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. De componenten [!UICONTROL Dynamic Media] en [!UICONTROL Interactive Media] worden in de volgende secties uitgebreid beschreven.

Een component Dynamic Media/viewer toevoegen aan een pagina:

1. Open in AEM de pagina waaraan u de component Dynamic Media wilt toevoegen.
1. Als er geen component Dynamic Media beschikbaar is, klikt u op de liniaal [!UICONTROL Sidekick] om de **[!UICONTROL Design]** modus in te schakelen, klikt u op **[!UICONTROL Edit]** parsys en selecteert u **[!UICONTROL Dynamic Media]** om de componenten Dynamic Media beschikbaar te maken.

   >[!NOTE]
   >
   >Zie Componenten [configureren in Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) voor meer informatie.

1. Ga terug naar de **[!UICONTROL Edit]** modus door op het potloodpictogram in de [!UICONTROL Sidekick]modus te klikken.
1. Sleep de **[!UICONTROL Dynamic Media]** of de **[!UICONTROL Interactive Media]** component van de **[!UICONTROL Other]** groep in het hulpstuk naar de pagina op de gewenste locatie.
1. Klik **[!UICONTROL Edit]** om de component te openen.
1. [Bewerk de component](#dynamic-media-component) naar wens en klik **[!UICONTROL OK]** om de wijzigingen op te slaan.

## Componenten Dynamic Media {#dynamic-media-components}

[!UICONTROL Dynamic Media] en [!UICONTROL Interactive Media] zijn beschikbaar in het [!UICONTROL Sidekick] gedeelte **[!UICONTROL Dynamic Media.]** U gebruikt de **[!UICONTROL Interactive Media]** component voor interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets. Gebruik de **[!UICONTROL Dynamic Media]** component voor alle andere dynamische mediacomponenten.

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt. [Nadat de componenten in de ontwerpmodus](/help/sites-authoring/default-components-designmode.md)beschikbaar zijn gemaakt, kunt u de componenten aan de pagina toevoegen, net als alle andere AEM-componenten.

### component Dynamic Media {#dynamic-media-component}

De component Dynamic Media is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

>[!NOTE]
>
>Wanneer u de [!UICONTROL Dynamic Media] component toevoegt en leeg **[!UICONTROL Dynamic Media Settings]** is of een element niet correct kunt toevoegen, controleert u het volgende:
>
>* U hebt Dynamic Media [](/help/assets/config-dynamic.md)ingeschakeld. Dynamic Media zijn standaard uitgeschakeld.
>* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die zijn geïmporteerd voordat dynamische media is ingeschakeld, hebben geen TIFF-bestand met piramide.

>



#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de [!UICONTROL Dynamic Media] component kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

![chlimage_1-72](assets/chlimage_1-72a.png)

U kunt de volgende Dynamic Media-instellingen bewerken door **[!UICONTROL Edit]** in de component te klikken en vervolgens op het **[!UICONTROL Dynamic Media Settings]** tabblad te klikken.

![chlimage_1-73](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. If you want to make it a fixed size, set it in the component in the **[!UICONTROL Advanced]** tab with the **[!UICONTROL Width]** and **[!UICONTROL Height]** properties.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen [van viewers](/help/assets/managing-viewer-presets.md)beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

Dit is de enige beschikbare optie als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt. De weergegeven viewervoorinstellingen zijn ook slim. Alleen relevante viewervoorinstellingen worden weergegeven.

**[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Voorinstellingen](/help/assets/managing-image-presets.md)voor afbeeldingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten wijzigen door extra opdrachten voor afbeeldingen in te voeren. Deze worden beschreven in Voorinstellingen [van het Beeld](/help/assets/managing-viewer-presets.md) beheren en de verwijzing [van het](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html)Bevel.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Breakpoints]** - Als u dit element gebruikt op een responsieve site, moet u de pagina-onderbrekingspunten toevoegen. Afbeeldingsonderbrekingspunten moeten door komma&#39;s (,) worden gescheiden. Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

U kunt het volgende bewerken [!UICONTROL Advanced Settings] door in de component te klikken **[!UICONTROL Edit]** .

**[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

**[!UICONTROL Alt Text]** - Voeg een titel aan de afbeelding toe voor gebruikers die afbeeldingen hebben uitgeschakeld.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL URL, Open in]** - U kunt een element instellen van om een koppeling te openen. Stel de opties in **[!UICONTROL URL]** en geef **[!UICONTROL Open in]** aan of u deze wilt openen in hetzelfde venster of in een nieuw venster.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarden niet invult, wordt het element adaptief.

#### Wanneer u werkt met video {#when-working-with-video}

Gebruik de [!UICONTROL Dynamic Media] component om dynamische video toe te voegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![chlimage_1-74](assets/chlimage_1-74a.png)

U kunt het volgende bewerken [!UICONTROL Dynamic Media Settings] door in de component te klikken **[!UICONTROL Edit]** .

>[!NOTE]
>
>De videocomponent Dynamic Media is standaard adaptief. If you want to make it a fixed size, set it in the component with the **[!UICONTROL Width]** and **[!UICONTROL Height]** in the **[!UICONTROL Advanced]** tab.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen [van viewers](/help/assets/managing-viewer-presets.md)beheren.

You can edit the following [!UICONTROL Advanced] settings by clicking **[!UICONTROL Edit]** in the component.

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

#### Beveiligde video leveren {#how-to-delivery-secure-video}

Wanneer u in AEM 6.2 [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480)installeert, kunt u bepalen of een video wordt geleverd via een HTTPS-verbinding (Secure SSL) of een onveilige verbinding (HTTP). Standaard wordt het video-leveringsprotocol automatisch overgenomen van het protocol van de ingesloten webpagina. Als de webpagina via HTTPS wordt geladen, wordt de video ook via HTTPS geleverd. En omgekeerd, als de webpagina zich op HTTP bevindt, wordt de video geleverd via HTTP. In de meeste gevallen, is dit standaardgedrag fijn en er is geen behoefte om het even welke configuratieveranderingen aan te brengen. U kunt dit standaardgedrag echter negeren door `VideoPlayer.ssl=on` aan het einde van een URL-pad of aan de lijst met andere parameters voor de viewerconfiguratie in een ingesloten codefragment toe te voegen, zodat de beveiligde video-levering geforceerd wordt.

Zie `VideoPlayer.ssl` Beveiligde videoverlevering [in de naslaggids voor viewers voor meer informatie over veilige videoverzending en het gebruik van het](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html) configuratiekenmerk in uw URL-pad. Naast de videoviewer is beveiligde video-levering beschikbaar voor de viewer voor gemengde media en de interactieve videoviewer.

### Interactieve mediacomponent {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Gebruik de **[!UICONTROL Interactive Media]** component als u een interactieve afbeelding, interactieve video of carrouselbanner hebt.

De [!UICONTROL Interactive Media] component is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

![chlimage_1-75](assets/chlimage_1-75a.png)

You can edit the following **[!UICONTROL General]** settings by clicking **[!UICONTROL Edit]** in the component.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

You can edit the following **[!UICONTROL Add To Cart** settings by clicking **[!UICONTROL Edit]** in the component.

**[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. Het productelement toont een afbeelding van het product zoals gedefinieerd in de module Handel. Schakel het vinkje uit om het productelement niet weer te geven.

**[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

**[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.
