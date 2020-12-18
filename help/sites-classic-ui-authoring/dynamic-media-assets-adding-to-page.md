---
title: Dynamic Media-assets aan pagina's toevoegen
seo-title: Dynamic Media-assets aan pagina's toevoegen
description: Als u de functionaliteit voor dynamische media wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component Dynamic Media of Interactive Media rechtstreeks op de pagina toevoegen.
seo-description: Als u de functionaliteit voor dynamische media wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component Dynamic Media of Interactive Media rechtstreeks op de pagina toevoegen.
uuid: 650d0867-a079-4936-a466-55b7a30803a2
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 331f4980-5193-4546-a22e-f27e38bb8250
translation-type: tm+mt
source-git-commit: e95f26cc1a084358b6bcb78605e3acb98f257b66
workflow-type: tm+mt
source-wordcount: '1602'
ht-degree: 2%

---


# Dynamic Media-assets aan pagina&#39;s toevoegen{#adding-dynamic-media-assets-to-pages}

Als u de Dynamic Media-functionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component **[!UICONTROL Dynamic Media]** of **[!UICONTROL Interactive Media]** rechtstreeks op de pagina toevoegen. U doet dit door de modus [!UICONTROL Design] in te voeren en de dynamische mediacomponenten in te schakelen. Vervolgens kunt u deze componenten aan de pagina toevoegen en assets aan de component toevoegen. De dynamische media en interactieve mediacomponenten zijn slim: ze weten of u een afbeelding of video toevoegt en de beschikbare opties veranderen dienovereenkomstig.

U voegt dynamische media-elementen rechtstreeks aan de pagina toe als u AEM gebruikt als uw WCM.

>[!NOTE]
>
>Afbeeldingen met hyperlinks zijn beschikbaar in het vak voor carrouselbanners.

## Een Dynamic Media-component toevoegen aan een pagina {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van de component [!UICONTROL Dynamic Media] of [!UICONTROL Interactive Media] aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. De componenten [!UICONTROL Dynamic Media] en [!UICONTROL Interactive Media] worden in de volgende secties gedetailleerd beschreven.

Een Dynamic Media-component/viewer toevoegen aan een pagina:

1. Open in AEM de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Als er geen Dynamic Media-component beschikbaar is, klikt u op de liniaal in [!UICONTROL Sidekick] om de modus **[!UICONTROL Design]** te activeren, klikt u op **[!UICONTROL Edit]** parsys en selecteert u **[!UICONTROL Dynamic Media]** om de Dynamic Media-componenten beschikbaar te maken.

   >[!NOTE]
   >
   >Zie [Componenten configureren in ontwerpmodus](/help/sites-authoring/default-components-designmode.md) voor meer informatie.

1. Ga terug naar de modus **[!UICONTROL Edit]** door op het potloodpictogram in [!UICONTROL Sidekick] te klikken.
1. Sleep de component **[!UICONTROL Dynamic Media]** of **[!UICONTROL Interactive Media]** van de groep **[!UICONTROL Other]** in het hulpstuk op de pagina in de gewenste plaats.
1. Klik **[!UICONTROL Edit]** om de component te openen.
1. [Bewerk indien nodig de ](#dynamic-media-component) component en klik  **[!UICONTROL OK]** om de wijzigingen op te slaan.

## Dynamic Media-componenten {#dynamic-media-components}

[!UICONTROL Dynamic Media] en  [!UICONTROL Interactive Media] zijn beschikbaar in het  [!UICONTROL Sidekick] gedeelte  **[!UICONTROL Dynamic Media.]** U gebruikt de  **[!UICONTROL Interactive Media]** component voor interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets. Gebruik voor alle andere dynamische mediacomponenten de component **[!UICONTROL Dynamic Media]**.

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt. [Nadat de componenten in de ontwerpmodus](/help/sites-authoring/default-components-designmode.md) beschikbaar zijn gemaakt, kunt u de componenten aan de pagina toevoegen, net als elke andere AEM.

### Dynamic Media-component {#dynamic-media-component}

De Dynamic Media-component is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

>[!NOTE]
>
>Wanneer u de component [!UICONTROL Dynamic Media] toevoegt en **[!UICONTROL Dynamic Media Settings]** leeg is of u kunt activa niet behoorlijk toevoegen, controleer het volgende:
>
>* U hebt [ingeschakelde Dynamic Media](/help/assets/config-dynamic.md). Dynamic Media is standaard uitgeschakeld.
>* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die zijn geïmporteerd voordat dynamische media is ingeschakeld, hebben geen TIFF-bestand met piramide.

>



#### Wanneer u werkt met afbeeldingen {#when-working-with-images}

Met de component [!UICONTROL Dynamic Media] kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

![chlimage_1-72](assets/chlimage_1-72a.png)

U kunt de volgende Dynamic Media-instellingen bewerken door in de component op **[!UICONTROL Edit]** te klikken en vervolgens op het tabblad **[!UICONTROL Dynamic Media Settings]** te klikken.

![chlimage_1-73](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component op het **[!UICONTROL Advanced]** lusje met **[!UICONTROL Width]** en **[!UICONTROL Height]** eigenschappen.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

Dit is de enige beschikbare optie als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt. De weergegeven viewervoorinstellingen zijn ook slim. Alleen relevante viewervoorinstellingen worden weergegeven.

**[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Voorinstellingen voor afbeeldingen beheren](/help/assets/managing-image-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten wijzigen door extra opdrachten voor afbeeldingen in te voeren. Deze worden beschreven in [Voorinstellingen voor afbeeldingen beheren](/help/assets/managing-viewer-presets.md) en [Command reference](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Breakpoints]** - Als u dit element gebruikt op een responsieve site, moet u de pagina-onderbrekingspunten toevoegen. Afbeeldingsonderbrekingspunten moeten door komma&#39;s (,) worden gescheiden. Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

U kunt de volgende [!UICONTROL Advanced Settings] uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

**[!UICONTROL Alt Text]** - Voeg een titel aan de afbeelding toe voor gebruikers die afbeeldingen hebben uitgeschakeld.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL URL, Open in]** - U kunt een element instellen van om een koppeling te openen. Stel de **[!UICONTROL URL]** en **[!UICONTROL Open in]** in om aan te geven of het venster in hetzelfde venster of in een nieuw venster moet worden geopend.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarden niet invult, wordt het element adaptief.

#### Bij het werken met video {#when-working-with-video}

Met de component [!UICONTROL Dynamic Media] kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![chlimage_1-74](assets/chlimage_1-74a.png)

U kunt de volgende [!UICONTROL Dynamic Media Settings] uitgeven door **[!UICONTROL Edit]** in de component te klikken.

>[!NOTE]
>
>De Dynamic Media-videocomponent is standaard adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component met **[!UICONTROL Width]** en **[!UICONTROL Height]** in **[!UICONTROL Advanced]** tabel.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

U kunt de volgende [!UICONTROL Advanced] montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

#### Beveiligde video {#how-to-delivery-secure-video} leveren

Wanneer u in AEM 6.2 [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480) installeert, kunt u bepalen of een video wordt geleverd via een HTTPS-verbinding (Secure SSL) of een onveilige verbinding (HTTP). Standaard wordt het video-leveringsprotocol automatisch overgenomen van het protocol van de ingesloten webpagina. Als de webpagina via HTTPS wordt geladen, wordt de video ook via HTTPS geleverd. En omgekeerd, als de webpagina zich op HTTP bevindt, wordt de video geleverd via HTTP. In de meeste gevallen, is dit standaardgedrag fijn en er is geen behoefte om het even welke configuratieveranderingen aan te brengen. Nochtans, kunt u dit standaardgedrag met voeten treden door `VideoPlayer.ssl=on` aan het eind van een weg URL of aan de lijst van andere parameters van de kijkersconfiguratie in een ingebed codefragment toe te voegen, om veilige videolevering te dwingen.

Zie [Beveiligde videoverstrekking](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html) in de naslaggids voor viewers voor meer informatie over veilige videoverzending en het gebruik van het configuratiekenmerk `VideoPlayer.ssl` in het URL-pad. Naast de videoviewer is beveiligde video-levering beschikbaar voor de viewer voor gemengde media en de interactieve videoviewer.

### Interactieve mediacomponent {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Als u een interactieve afbeelding, interactieve video of carrouselbanner hebt, gebruikt u de component **[!UICONTROL Interactive Media]**.

De [!UICONTROL Interactive Media] component is slim - afhankelijk van of u een beeld of een video toevoegt, hebt u diverse opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

![chlimage_1-75](assets/chlimage_1-75a.png)

U kunt de volgende **[!UICONTROL General]** montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

**[!UICONTROL Title]** - Wijzig de titel van de video.

**[!UICONTROL Width and Height]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

U kunt de volgende **[!UICONTROL Add To Cart]** montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

**[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. Het productelement toont een afbeelding van het product zoals gedefinieerd in de module Handel. Schakel het vinkje uit om het productelement niet weer te geven.

**[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

**[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.
