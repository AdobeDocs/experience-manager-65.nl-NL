---
title: Dynamic Media-elementen toevoegen aan pagina's
description: Als u de Dynamic Media-functionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de Dynamic Media- of Interactive Media-component rechtstreeks op de pagina toevoegen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
exl-id: d2ebfca5-19f9-4fa5-b142-b978f46a912f
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 1%

---

# Dynamic Media-elementen toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Als u de Dynamic Media-functionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component **[!UICONTROL Dynamic Media]** of **[!UICONTROL Interactive Media]** rechtstreeks op de pagina toevoegen. Voer de modus **[!UICONTROL Design]** in en schakel de Dynamic Media-componenten in. Vervolgens kunt u deze componenten aan de pagina toevoegen en assets aan de component toevoegen. De Dynamic Media en interactieve mediacomponenten zijn slim: ze weten of u een afbeelding of een video toevoegt en de beschikbare opties veranderen dienovereenkomstig.

U voegt Dynamic Media-elementen rechtstreeks aan de pagina toe als u Adobe Experience Manager als uw WCM gebruikt.

>[!NOTE]
>
>Afbeeldingen met hyperlinks zijn beschikbaar in het vak voor carrouselbanners.

## Een Dynamic Media-component aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van de component [!UICONTROL Dynamic Media] of [!UICONTROL Interactive Media] aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. De componenten [!UICONTROL Dynamic Media] en [!UICONTROL Interactive Media] worden in de volgende secties uitgebreid beschreven.

Een Dynamic Media-component/viewer toevoegen aan een pagina:

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Als er geen Dynamic Media-component beschikbaar is, selecteert u de liniaal in de [!UICONTROL Sidekick] om de modus **[!UICONTROL Design]** te activeren.
1. Selecteer **[!UICONTROL Edit]** parsys.
1. Selecteer **[!UICONTROL Dynamic Media]** zodat u de Dynamic Media-componenten beschikbaar kunt maken.

   >[!NOTE]
   >
   >Zie [ Vormende Componenten op de Wijze van het Ontwerp ](/help/sites-authoring/default-components-designmode.md) voor meer informatie.

1. Ga terug naar de modus **[!UICONTROL Edit]** door op het potloodpictogram in de [!UICONTROL Sidekick] te klikken.
1. Sleep de component **[!UICONTROL Dynamic Media]** of **[!UICONTROL Interactive Media]** van de groep **[!UICONTROL Other]** in het hulpstuk naar de pagina op de gewenste locatie.
1. Selecteer **[!UICONTROL Edit]** zodat de component wordt geopend.
1. [ geef de component ](#dynamic-media-component) zonodig uit.
1. Selecteer **[!UICONTROL OK]** zodat de wijzigingen worden opgeslagen.

## Dynamic Media-componenten {#dynamic-media-components}

[!UICONTROL Dynamic Media] en [!UICONTROL Interactive Media] zijn beschikbaar in [!UICONTROL Sidekick] onder **[!UICONTROL Dynamic Media]** . U gebruikt de component **[!UICONTROL Interactive Media]** voor alle interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets. Gebruik de component **[!UICONTROL Dynamic Media]** voor alle andere Dynamic Media-componenten.

![ chlimage_1-71 ](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt. [ nadat zij op de wijze van het Ontwerp ](/help/sites-authoring/default-components-designmode.md) ter beschikking worden gesteld, kunt u de componenten aan uw pagina toevoegen zoals u een andere component van de Experience Manager.

### Dynamic Media-component {#dynamic-media-component}

De Dynamic Media-component is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

>[!NOTE]
>
>Wanneer u de component [!UICONTROL Dynamic Media] toevoegt en **[!UICONTROL Dynamic Media Settings]** leeg is of wanneer u een element niet correct kunt toevoegen, controleert u het volgende:
>
>* U hebt [ toegelaten Dynamic Media ](/help/assets/config-dynamic.md). Dynamic Media is standaard uitgeschakeld.
>* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die zijn geïmporteerd voordat Dynamic Media is ingeschakeld, hebben geen TIFF-bestand met piramide.
>

#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de component [!UICONTROL Dynamic Media] kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

![ chlimage_1-72 ](assets/chlimage_1-72a.png)

U kunt de volgende Dynamic Media-instellingen bewerken door in de component op **[!UICONTROL Edit]** te klikken en vervolgens op de tab **[!UICONTROL Dynamic Media Settings]** te klikken.

![ chlimage_1-73 ](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt maken, stelt u deze in in de component op het tabblad **[!UICONTROL Advanced]** met de eigenschappen **[!UICONTROL Width]** en **[!UICONTROL Height]** .

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [ het Leiden Kijker stelt ](/help/assets/managing-viewer-presets.md) vooraf in. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

Deze optie is alleen beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt. De weergegeven viewervoorinstellingen zijn slim. Er worden dus alleen relevante voorinstellingen voor viewers weergegeven.

**[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor afbeeldingen in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [ het Leiden Beeld vooraf instelt ](/help/assets/managing-image-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten wijzigen door extra opdrachten voor afbeeldingen in te voeren. Deze bevelen worden beschreven in [ het Leiden Beeld vooraf instelt ](/help/assets/managing-viewer-presets.md) en de [ verwijzing van het Bevel ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Breakpoints]** - Als u dit element gebruikt op een responsieve site, moet u de pagina-onderbrekingspunten toevoegen. Afbeeldingsonderbrekingspunten worden gescheiden door komma&#39;s (,). Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

U kunt de volgende [!UICONTROL Advanced Settings] bewerken door op **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

**[!UICONTROL Alt Text]** - Voeg een titel toe aan de afbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL URL, Open in]** - U kunt een middel van plaatsen om een verbinding te openen. Stel de knoppen **[!UICONTROL URL]** en **[!UICONTROL Open in]** in om aan te geven of deze in hetzelfde venster of in een nieuw venster moeten worden geopend.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarden niet invult, wordt het element adaptief.

#### Wanneer u werkt met video {#when-working-with-video}

Gebruik de component **[!UICONTROL Dynamic Media]** om dynamische video toe te voegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![ chlimage_1-74 ](assets/chlimage_1-74a.png)

U kunt de volgende [!UICONTROL Dynamic Media Settings] bewerken door op **[!UICONTROL Edit]** in de component te klikken.

>[!NOTE]
>
>De Dynamic Media-videocomponent is standaard adaptief. Als u een vaste grootte wilt maken, stelt u deze in de component in met de tabbladen **[!UICONTROL Width]** en **[!UICONTROL Height]** **[!UICONTROL Advanced]** .

**[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [ het Leiden Kijker stelt ](/help/assets/managing-viewer-presets.md) vooraf in.

U kunt de volgende [!UICONTROL Advanced] -instellingen bewerken door op **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

#### Beveiligde video leveren {#how-to-delivery-secure-video}

In Experience Manager 6.2, wanneer u [ FP-13480 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480) installeert, kunt u controleren of een video over een veilige SSL verbinding (HTTPS) of een onveilige verbinding (HTTP) wordt geleverd. Standaard wordt het video-leveringsprotocol automatisch overgenomen van het protocol van de ingesloten webpagina. Als de webpagina via HTTPS wordt geladen, wordt de video ook via HTTPS geleverd. Omgekeerd geldt dat als de webpagina zich op HTTP bevindt, de video via HTTP wordt geleverd. Gewoonlijk is dit standaardgedrag prima en hoeft de configuratie niet te worden gewijzigd. U kunt dit standaardgedrag echter overschrijven. Voeg `VideoPlayer.ssl=on` toe aan het einde van een URL-pad of aan de lijst met andere parameters voor viewerconfiguratie in een ingesloten codefragment. Beide acties dwingen de veilige videoverzending.

Voor meer informatie over veilige videolevering en het gebruiken van het `VideoPlayer.ssl` configuratieattribuut in uw weg URL, zie [ Veilige VideoLevering ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html) in de Gids van de Verwijzing van Kijkers. Naast de videoviewer is beveiligde video-levering beschikbaar voor de viewer voor gemengde media en de interactieve videoviewer.

### Interactieve media-component {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Gebruik de component **[!UICONTROL Interactive Media]** als u een interactieve afbeelding, interactieve video of carrouselbanner hebt.

De component [!UICONTROL Interactive Media] is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

![ chlimage_1-75 ](assets/chlimage_1-75a.png)

U kunt de volgende **[!UICONTROL General]** -instellingen bewerken door op **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie [ vooraf instelt van de Kijker beheren ](/help/assets/managing-viewer-presets.md).

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

U kunt de volgende **[!UICONTROL Add To Cart]** -instellingen bewerken door op **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. In het productelement ziet u een afbeelding van het product, zoals gedefinieerd in de Commerce-module. Schakel het vinkje uit om het productelement niet weer te geven.

**[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Commerce. Schakel het vinkje uit om de productprijs niet weer te geven.

**[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.
