---
title: Dynamic Media-elementen toevoegen aan pagina's
description: Als u de Dynamic Media-functionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de Dynamic Media- of Interactive Media-component rechtstreeks op de pagina toevoegen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
exl-id: d2ebfca5-19f9-4fa5-b142-b978f46a912f
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 1%

---

# Dynamic Media-elementen toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Als u de Dynamic Media-functionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component **[!UICONTROL Dynamic Media]** of **[!UICONTROL Interactive Media]** rechtstreeks op de pagina toevoegen. Ga **[!UICONTROL Design]** wijze in en toelatend de componenten van Dynamic Media. Vervolgens kunt u deze componenten aan de pagina toevoegen en assets aan de component toevoegen. De Dynamic Media en interactieve mediacomponenten zijn slim: ze weten of u een afbeelding of een video toevoegt en de beschikbare opties veranderen dienovereenkomstig.

U voegt Dynamic Media-elementen rechtstreeks aan de pagina toe als u Adobe Experience Manager als uw WCM gebruikt.

>[!NOTE]
>
>Afbeeldingen met hyperlinks zijn beschikbaar in het vak voor carrouselbanners.

## Een Dynamic Media-component aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van de component [!UICONTROL Dynamic Media] of [!UICONTROL Interactive Media] aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. De componenten [!UICONTROL Dynamic Media] en [!UICONTROL Interactive Media] worden in de volgende secties gedetailleerd beschreven.

Een Dynamic Media-component/viewer toevoegen aan een pagina:

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Als er geen Dynamic Media-component beschikbaar is, selecteert u de liniaal in [!UICONTROL Sidekick] om naar de modus **[!UICONTROL Design]** te gaan.
1. Selecteer **[!UICONTROL Edit]** parsys.
1. Selecteer **[!UICONTROL Dynamic Media]** zodat u de Dynamic Media-componenten beschikbaar kunt maken.

   >[!NOTE]
   >
   >Zie [Componenten configureren in ontwerpmodus](/help/sites-authoring/default-components-designmode.md) voor meer informatie.

1. Ga terug naar de modus **[!UICONTROL Edit]** door op het potloodpictogram in [!UICONTROL Sidekick] te klikken.
1. Sleep de component **[!UICONTROL Dynamic Media]** of **[!UICONTROL Interactive Media]** van de groep **[!UICONTROL Other]** in het hulpstuk op de pagina in de gewenste plaats.
1. Selecteer **[!UICONTROL Edit]** zodat de component wordt geopend.
1. [Bewerk indien nodig de ](#dynamic-media-component) component.
1. Selecteer **[!UICONTROL OK]** zodat worden uw veranderingen bewaard.

## Dynamic Media-componenten {#dynamic-media-components}

[!UICONTROL Dynamic Media] en  [!UICONTROL Interactive Media] zijn beschikbaar in het  [!UICONTROL Sidekick] volgende  **[!UICONTROL Dynamic Media]**. U gebruikt de component **[!UICONTROL Interactive Media]** voor alle interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets. Voor alle andere Dynamic Media-componenten gebruikt u de **[!UICONTROL Dynamic Media]**-component.

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt. [Nadat de componenten in de ontwerpmodus](/help/sites-authoring/default-components-designmode.md) beschikbaar zijn gemaakt, kunt u de componenten aan de pagina toevoegen, net als alle andere Experience Managers.

### Dynamic Media-component {#dynamic-media-component}

De Dynamic Media-component is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

>[!NOTE]
>
>Wanneer u de component [!UICONTROL Dynamic Media] toevoegt en **[!UICONTROL Dynamic Media Settings]** leeg is of u kunt activa niet behoorlijk toevoegen, controleer het volgende:
>
>* U hebt [ingeschakelde Dynamic Media](/help/assets/config-dynamic.md). Dynamic Media is standaard uitgeschakeld.
>* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die zijn geïmporteerd voordat Dynamic Media is ingeschakeld, hebben geen TIFF-bestand met piramide.

>



#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de component [!UICONTROL Dynamic Media] kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

![chlimage_1-72](assets/chlimage_1-72a.png)

U kunt de volgende Dynamic Media-instellingen bewerken door in de component op **[!UICONTROL Edit]** te klikken en vervolgens op het tabblad **[!UICONTROL Dynamic Media Settings]** te klikken.

![chlimage_1-73](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component op het **[!UICONTROL Advanced]** lusje met **[!UICONTROL Width]** en **[!UICONTROL Height]** eigenschappen.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

Deze optie is alleen beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt. De weergegeven viewervoorinstellingen zijn slim. Er worden dus alleen relevante voorinstellingen voor viewers weergegeven.

**[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Voorinstellingen voor afbeeldingen beheren](/help/assets/managing-image-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten wijzigen door extra opdrachten voor afbeeldingen in te voeren. Deze opdrachten worden beschreven in [Voorinstellingen voor afbeeldingen beheren](/help/assets/managing-viewer-presets.md) en de [Command-referentie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Breakpoints]** - Als u dit element gebruikt op een responsieve site, moet u de pagina-onderbrekingspunten toevoegen. Afbeeldingsonderbrekingspunten worden gescheiden door komma&#39;s (,). Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

U kunt de volgende [!UICONTROL Advanced Settings] uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

**[!UICONTROL Alt Text]** - Voeg een titel aan de afbeelding toe voor gebruikers die afbeeldingen hebben uitgeschakeld.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL URL, Open in]** - U kunt een element instellen van om een koppeling te openen. Stel de **[!UICONTROL URL]** en **[!UICONTROL Open in]** in om aan te geven of het venster in hetzelfde venster of in een nieuw venster moet worden geopend.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarden niet invult, wordt het element adaptief.

#### Wanneer u werkt met video {#when-working-with-video}

Met de component **[!UICONTROL Dynamic Media]** kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![chlimage_1-74](assets/chlimage_1-74a.png)

U kunt de volgende [!UICONTROL Dynamic Media Settings] uitgeven door **[!UICONTROL Edit]** in de component te klikken.

>[!NOTE]
>
>De Dynamic Media-videocomponent is standaard adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component met **[!UICONTROL Width]** en **[!UICONTROL Height]** in **[!UICONTROL Advanced]** tabel.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

U kunt de volgende [!UICONTROL Advanced] montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

#### Beveiligde video leveren {#how-to-delivery-secure-video}

In Experience Manager 6.2, wanneer u [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480) installeert, kunt u controleren of een video over een veilige SSL verbinding (HTTPS) of een onveilige verbinding (HTTP) wordt geleverd. Standaard wordt het video-leveringsprotocol automatisch overgenomen van het protocol van de ingesloten webpagina. Als de webpagina via HTTPS wordt geladen, wordt de video ook via HTTPS geleverd. Omgekeerd geldt dat als de webpagina zich op HTTP bevindt, de video via HTTP wordt geleverd. Gewoonlijk is dit standaardgedrag prima en hoeft de configuratie niet te worden gewijzigd. U kunt dit standaardgedrag echter overschrijven. Voeg `VideoPlayer.ssl=on` aan of het eind van een weg URL of aan de lijst van andere parameters van de kijkersconfiguratie in een ingebed codefragment toe. Beide acties dwingen de veilige videoverzending.

Zie [Beveiligde videoverstrekking](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html) in de naslaggids voor viewers voor meer informatie over veilige videoverzending en het gebruik van het configuratiekenmerk `VideoPlayer.ssl` in het URL-pad. Naast de videoviewer is beveiligde video-levering beschikbaar voor de viewer voor gemengde media en de interactieve videoviewer.

### Interactieve mediacomponent {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Als u een interactieve afbeelding, interactieve video of carrouselbanner hebt, gebruikt u de component **[!UICONTROL Interactive Media]**.

De [!UICONTROL Interactive Media] component is slim - afhankelijk van of u een beeld of een video toevoegt, hebt u diverse opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

![chlimage_1-75](assets/chlimage_1-75a.png)

U kunt de volgende **[!UICONTROL General]** montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie [Viewervoorinstellingen beheren](/help/assets/managing-viewer-presets.md).

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

U kunt de volgende **[!UICONTROL Add To Cart]** montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. Het productelement toont een afbeelding van het product zoals gedefinieerd in de module Handel. Schakel het vinkje uit om het productelement niet weer te geven.

**[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

**[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.
