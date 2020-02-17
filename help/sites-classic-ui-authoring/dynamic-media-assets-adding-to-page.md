---
title: Dynamische media-elementen toevoegen aan pagina's
seo-title: Dynamische media-elementen toevoegen aan pagina's
description: Als u de dynamische mediafunctionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component Dynamische media of Interactieve media rechtstreeks op de pagina toevoegen.
seo-description: Als u de dynamische mediafunctionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component Dynamische media of Interactieve media rechtstreeks op de pagina toevoegen.
uuid: 650d0867-a079-4936-a466-55b7a30803a2
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 331f4980-5193-4546-a22e-f27e38bb8250
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Dynamische media-elementen toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Als u de functionaliteit Dynamische media wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component **[!UICONTROL Dynamische media]** of **[!UICONTROL Interactieve media]** rechtstreeks op de pagina toevoegen. U doet dit door de [!UICONTROL ontwerpmodus] in te voeren en de dynamische mediacomponenten in te schakelen. Vervolgens kunt u deze componenten aan de pagina toevoegen en elementen aan de component toevoegen. De dynamische media en interactieve mediacomponenten zijn slim: ze weten of u een afbeelding of video toevoegt en de beschikbare opties veranderen dienovereenkomstig.

U voegt dynamische media-elementen rechtstreeks aan de pagina toe als u AEM als uw WCM gebruikt.

>[!NOTE]
>
>Afbeeldingen met hyperlinks zijn beschikbaar in het vak voor carrouselbanners.

## Een component Dynamische media aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van de component [!UICONTROL Dynamische media] of [!UICONTROL Interactieve media] aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. De [!UICONTROL componenten Dynamische media] en [!UICONTROL Interactieve Media] worden in de volgende secties gedetailleerd beschreven.

Een component/viewer voor dynamische media toevoegen aan een pagina:

1. Open in AEM de pagina waaraan u de component Dynamische media wilt toevoegen.
1. Als geen Dynamische component van Media beschikbaar is, klik de heerser op de [!UICONTROL Sidetrap] om de wijze van het **[!UICONTROL Ontwerp]** in te gaan, **[!UICONTROL geef]** parsys uit, en selecteer **[!UICONTROL Dynamische Media]** om de Dynamische componenten van Media beschikbaar te maken.

   >[!NOTE]
   >
   >Zie Componenten [configureren in Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) voor meer informatie.

1. Ga terug naar de modus **[!UICONTROL Bewerken]** door op het potloodpictogram in de [!UICONTROL Sidetrap]te klikken.
1. Sleep de component **[!UICONTROL Dynamische media]** of **[!UICONTROL Interactieve media]** van de **[!UICONTROL Andere]** groep in het hulpstuk naar de pagina in de gewenste plaats.
1. Klik op **[!UICONTROL Bewerken]** om de component te openen.
1. [Bewerk de component](#dynamic-media-component) naar wens en klik op **[!UICONTROL OK]** om de wijzigingen op te slaan.

## Dynamische mediacomponenten {#dynamic-media-components}

[!UICONTROL Dynamische media] en [!UICONTROL Interactieve media] zijn beschikbaar in de [!UICONTROL Sidetrap] onder **[!UICONTROL Dynamische Media]**. U gebruikt de component **[!UICONTROL Interactieve media]** voor alle interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets. Gebruik de component **[!UICONTROL Dynamische media]** voor alle andere dynamische mediacomponenten.

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt. [Nadat de componenten in de ontwerpmodus](/help/sites-authoring/default-components-designmode.md)beschikbaar zijn gemaakt, kunt u de componenten aan de pagina toevoegen, net als alle andere AEM-componenten.

### Dynamische media-component {#dynamic-media-component}

De component Dynamische media is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

>[!NOTE]
>
>Wanneer u de component [!UICONTROL Dynamische media] toevoegt en **[!UICONTROL Dynamische media-instellingen]** leeg is of wanneer u een element niet correct kunt toevoegen, controleert u het volgende:
>
>* Dynamische media is [ingeschakeld](/help/assets/config-dynamic.md). Dynamische media is standaard uitgeschakeld.
>* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die zijn geïmporteerd voordat dynamische media is ingeschakeld, hebben geen TIFF-bestand met piramide.
>



#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de [!UICONTROL component Dynamische media] kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

![chlimage_1-72](assets/chlimage_1-72a.png)

U kunt de volgende instellingen voor dynamische media bewerken door in de component op **[!UICONTROL Bewerken]** te klikken en vervolgens op het tabblad **[!UICONTROL Dynamische media-instellingen]** te klikken.

![chlimage_1-73](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent Dynamische media adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component op het **[!UICONTROL Geavanceerde]** lusje met de eigenschappen van de **[!UICONTROL Breedte]** en van de **[!UICONTROL Hoogte]** .

**[!UICONTROL Viewer-voorinstelling]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen [van viewers](/help/assets/managing-viewer-presets.md)beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

Dit is de enige beschikbare optie als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt. De weergegeven viewervoorinstellingen zijn ook slim. Alleen relevante viewervoorinstellingen worden weergegeven.

**[!UICONTROL Voorinstelling]** afbeelding - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Voorinstellingen](/help/assets/managing-image-presets.md)voor afbeeldingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Afbeeldingswijzigingstoetsen]** - U kunt afbeeldingseffecten wijzigen door extra opdrachten voor afbeeldingen te leveren. Deze worden beschreven in Voorinstellingen [van het Beeld](/help/assets/managing-viewer-presets.md) beheren en de verwijzing [van het](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/c_command_reference.html)Bevel.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Onderbrekingspunten]** - Als u dit element gebruikt op een responsieve site, moet u de pagina-onderbrekingspunten toevoegen. Afbeeldingsonderbrekingspunten moeten door komma&#39;s (,) worden gescheiden. Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

U kunt de volgende [!UICONTROL Geavanceerde instellingen] bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

**[!UICONTROL Titel]** - Wijzig de titel van de afbeelding.

**[!UICONTROL Alt-tekst]** - Voeg een titel toe aan de afbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL URL, Openen in]** - U kunt een middel van plaatsen om een verbinding te openen. Stel de **[!UICONTROL URL]** en **[!UICONTROL Openen in]** in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

**[!UICONTROL Breedte en Hoogte]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarden niet invult, wordt het element adaptief.

#### Wanneer u werkt met video {#when-working-with-video}

Met de component [!UICONTROL Dynamische media] kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![chlimage_1-74](assets/chlimage_1-74a.png)

U kunt de volgende [!UICONTROL dynamische Media-instellingen] bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

>[!NOTE]
>
>Standaard is de videocomponent Dynamic Media adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component met de **[!UICONTROL Breedte]** en de **[!UICONTROL Hoogte]** op het **[!UICONTROL Geavanceerde]** lusje.

**[!UICONTROL Viewer-voorinstelling]** - Selecteer een bestaande voorinstelling voor een videoviewer in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen [van viewers](/help/assets/managing-viewer-presets.md)beheren.

U kunt de volgende [!UICONTROL geavanceerde] instellingen bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

**[!UICONTROL Titel]** - Wijzig de titel van de video.

**[!UICONTROL Breedte en Hoogte]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

#### Beveiligde video leveren {#how-to-delivery-secure-video}

Wanneer u in AEM 6.2 [FP-13480](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480)installeert, kunt u bepalen of een video wordt geleverd via een HTTPS-verbinding (Secure SSL) of een onveilige verbinding (HTTP). Standaard wordt het video-leveringsprotocol automatisch overgenomen van het protocol van de ingesloten webpagina. Als de webpagina via HTTPS wordt geladen, wordt de video ook via HTTPS geleverd. En omgekeerd, als de webpagina zich op HTTP bevindt, wordt de video geleverd via HTTP. In de meeste gevallen, is dit standaardgedrag fijn en er is geen behoefte om het even welke configuratieveranderingen aan te brengen. U kunt dit standaardgedrag echter negeren door `VideoPlayer.ssl=on` aan het einde van een URL-pad of aan de lijst met andere parameters voor de viewerconfiguratie in een ingesloten codefragment toe te voegen, zodat de beveiligde video-levering geforceerd wordt.

Zie `VideoPlayer.ssl` Beveiligde videoverlevering [in de naslaggids voor viewers voor meer informatie over veilige videoverzending en het gebruik van het](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_video_viewer_20_securevideodelivery.html) configuratiekenmerk in uw URL-pad. Naast de videoviewer is beveiligde video-levering beschikbaar voor de viewer voor gemengde media en de interactieve videoviewer.

### Interactieve mediacomponent {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Als u een interactieve afbeelding, interactieve video of carrouselbanner hebt, gebruikt u de component **[!UICONTROL Interactieve media]** .

De component [!UICONTROL Interactieve media] is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert dus automatisch op basis van de schermgrootte. Alle viewers zijn op HTML5 gebaseerde viewers.

![chlimage_1-75](assets/chlimage_1-75a.png)

U kunt de volgende **[!UICONTROL algemene]** instellingen bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

**[!UICONTROL Viewer-voorinstelling]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

**[!UICONTROL Titel]** - Wijzig de titel van de video.

**[!UICONTROL Breedte en Hoogte]** - Voer een waarde in pixels in als u wilt dat de video een vaste grootte heeft. Als u deze waarden niet invult, wordt het adaptief.

U kunt het volgende bewerken **[!UICONTROL voegt toe aan winkelwagentinstellingen** door in de component op **[!UICONTROL Bewerken]** te klikken.

**[!UICONTROL Productelement]** tonen - Deze waarde is standaard geselecteerd. Het productelement toont een afbeelding van het product zoals gedefinieerd in de module Handel. Schakel het vinkje uit om het productelement niet weer te geven.

**[!UICONTROL Productprijs]** tonen - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

**[!UICONTROL Productformulier]** tonen - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.
