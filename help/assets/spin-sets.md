---
title: Spin Sets
description: Leer hoe u met centrifuges werkt in Dynamic Media
uuid: 379a20a3-6a17-499a-b0f1-3a835b97aa7b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 8e9b3815-2893-4e6b-ac41-77720b42d56b
docset: aem65
translation-type: tm+mt
source-git-commit: 74f259d579bcf8d7a9198f93ef667288787a4493
workflow-type: tm+mt
source-wordcount: '1765'
ht-degree: 7%

---


# Spin Sets{#spin-sets}

Een centrifugeerset simuleert de echte handeling waarbij een object wordt omgedraaid om het te onderzoeken. Met centrifuges kunt u items vanuit elke hoek bekijken en de belangrijkste visuele details vanuit elke hoek verkrijgen.

Een centrifugeerset simuleert een kijkervaring van 360 graden. Dynamische media biedt centrifugesets met één as waarin gebruikers een item kunnen roteren. Bovendien kunnen gebruikers met een paar eenvoudige muisklikken in- en uitzoomen op een vrije vorm en een willekeurige weergave pannen. Op deze manier kunnen gebruikers een item vanuit een bepaald gezichtspunt nader onderzoeken.

De Reeksen van de Draai worden aangewezen door een banner met het woord **[!UICONTROL SPINSET.]** Bovendien als de Reeks van de Draai wordt gepubliceerd, dan is de publicatiedatum, die door het pictogram wordt vermeld op de banner samen met de laatste wijzigingsdatum wordt vermeld, die door het **[!UICONTROL World]** **[!UICONTROL Pencil]** pictogramvertoningen wordt vermeld.

![chlimage_1-](assets/chlimage_1-380.png)

>[!NOTE]
>
>Zie Elementen [beheren met de aanraakinterface](/help/assets/managing-assets-touch-ui.md)voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Sets draaien {#quick-start-spin-sets}

Ga als volgt te werk om snel aan de slag te gaan met centrifuges:

1. [Upload uw afbeeldingen voor meerdere weergaven.](#uploading-assets-for-spin-sets)

   U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset en 16-24 voor een tweedimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30 graden (360/12) voor elke opname.

1. [Spin-sets maken.](#creating-spin-sets)

   Als u een centrifugeset wilt maken, selecteert u de set **[!UICONTROL Create > Spin Set]** en geeft u een naam op. Kies vervolgens de elementen en kies de volgorde waarin de afbeeldingen worden weergegeven.

   See [Working with Selectors](/help/assets/working-with-selectors.md).

   >[!NOTE]
   >
   >U kunt ook automatisch spinsets maken via [voorinstellingen voor batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). **Belangrijk:** Batchsets worden door het IPS (Image Production System) gemaakt als onderdeel van het opnemen van elementen en zijn alleen beschikbaar in de modus Dynamische media - Scene7.

1. Stel, indien nodig, [voorinstellingen](/help/assets/managing-viewer-presets.md)voor de draaiende viewer in.

   Beheerders kunnen viewervoorinstellingen voor spinsets maken of wijzigen. Als u uw spinset wilt weergeven met een viewervoorinstelling, selecteert u de spinset en selecteert u **Viewers** in het vervolgkeuzemenu voor het linkerspoor.

   Zie **[!UICONTROL Tools > Assets > Viewer Presets]** viewervoorinstellingen maken of bewerken.

   Zie Voorinstellingen voor viewers [toevoegen en bewerken.](/help/assets/managing-viewer-presets.md)

1. [Spin-sets](#viewing-spin-sets)weergeven.

   U kunt sets die zijn gemaakt met voorinstellingen voor batchsets op drie verschillende manieren weergeven en openen. (Sets die zijn gemaakt met behulp van voorinstellingen voor batchsets, worden *niet* weergegeven in de gebruikersinterface.)

1. [Voorvertoning van centrifuges.](/help/assets/previewing-assets.md)

   Selecteer de centrifugeset en u kunt er een voorvertoning van weergeven. Roteer de centrifugeset. U kunt verschillende kijkers van het **[!UICONTROL Viewers]** menu kiezen, beschikbaar van het linkerspoordrop-down menu.

1. [Spin-sets publiceren.](/help/assets/publishing-dynamicmedia-assets.md)

   Als u een centrifugeerset publiceert, worden de URL- en insluitreeks geactiveerd. Bovendien moet u de voorinstelling [van de viewer](/help/assets/managing-viewer-presets.md)publiceren.

1. [Koppel URL&#39;s aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md) of [sluit de video- of afbeeldingsviewer](/help/assets/embed-code.md)in.

   AEM Assets maakt URL-aanroepen voor centrifuges en activeert deze nadat u de centrifuges hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Select the Spin Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers.]**

   Zie [Een spinset koppelen aan een webpagina](/help/assets/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/embed-code.md).

Indien nodig kunt u [centrifuges](#editing-spin-sets)bewerken. Bovendien kunt u de eigenschappen [van de](/help/assets/managing-assets-touch-ui.md#editing-properties)Spin-set weergeven en wijzigen.

## Elementen uploaden voor centrifuges {#uploading-assets-for-spin-sets}

U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset en 16-24 voor een tweedimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30 graden (360/12) voor elke opname.

U kunt afbeeldingen voor de centrifuges uploaden zoals u elk ander element in AEM Assets [](/help/assets/managing-assets-touch-ui.md)uploadt.

### Richtlijnen voor het vastleggen van afbeeldingen voor uw centrifugeset {#guidelines-for-shooting-spin-set-images}

Hieronder vindt u een aantal aanbevolen procedures voor het uitvoeren van gecentreerde afbeeldingen. Over het algemeen geldt dat hoe meer afbeeldingen u in een centrifugeset hebt, hoe beter het effect van het draaien van de afbeelding is. Als u echter veel afbeeldingen in de set opneemt, neemt de laadtijd van de afbeeldingen toe. AEM raadt deze richtlijnen aan voor het maken van foto&#39;s voor gebruik in centrifuges:

* Gebruik minimaal 8-12 afbeeldingen in een eendimensionale centrifuge en 16-24 afbeeldingen in een tweedimensionale centrifugeset. U hebt minimaal 8 afbeeldingen nodig om 360 graden te kunnen draaien. Eendimensionale centrifuges komen vaker voor omdat het maken van tweedimensionale centrifuges arbeidsintensief is.
* Gebruik een indeling zonder verlies. TIFF en PNG worden aanbevolen.
* Masker alle afbeeldingen zodat het item op een zuiver witte of andere achtergrond met veel contrast wordt weergegeven. Voeg desgewenst schaduwen toe.
* Zorg ervoor dat de productdetails goed verlicht en in nadruk zijn.
* Neem spin beelden voor modekleding met een mannequin of een model. Vaak wordt de mannequin volledig gemaskeerd (met behulp van een glazen mannequin) of wordt in de afbeelding een gestileerde mannequin/dressform weergegeven. U kunt een op-model spin-reeks tot stand brengen door het aantal hoeken te bepalen. Markeer elke hoek met band op de vloer om het model te begeleiden en in de richting van elke opname te kijken.

## Spin-sets maken {#creating-spin-sets}

In deze sectie wordt beschreven hoe u centrifuges kunt maken in AEM.

>[!NOTE]
>
>U kunt ook automatisch spinsets maken via [voorinstellingen voor batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). **Belangrijk:** Batchsets worden door het IPS (Image Production System) gemaakt als onderdeel van het opnemen van elementen en zijn alleen beschikbaar in de modus Dynamische media - Scene7.
>
>Zie &quot;Voorinstellingen voor batchsets maken om automatisch afbeeldingssets en centrifuges te genereren&quot; in de modus [Dynamische media](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)configureren - Scene7.


>[!NOTE]
>
>De volgorde waarin afbeeldingen worden weergegeven in een draaiset. Zorg ervoor dat u ze zo bestelt dat de centrifuge een vloeiende weergave van 360 graden biedt.

**Draaisets maken**

1. Navigeer in Elementen naar de plaats waar u een centrifugeset wilt maken, klik **[!UICONTROL Create]** en selecteer **[!UICONTROL Spin Set.]** U kunt de set ook maken vanuit een map die uw elementen bevat. De Editor van spinset wordt weergegeven.

   ![6_5_spinset-createpulldownmenu](assets/6_5_spinset-createpulldownmenu.png)

1. Voer in het **[!UICONTROL Title]** veld in de Editor van de centrifugeset een naam in voor de centrifugeset. De naam wordt weergegeven in de banner over de centrifugeset. Voer eventueel een beschrijving in.

   ![6_5_spinset-spinseteditortitle](assets/6_5_spinset-spinseteditortitle.png)

   >[!NOTE]
   >
   >Wanneer u de centrifugeset maakt, kunt u de miniatuur van de centrifugeset wijzigen of AEM de miniatuur automatisch selecteren op basis van de elementen in de centrifugeset. Als u een miniatuur wilt selecteren, klikt u op een willekeurige afbeelding **[!UICONTROL Change thumbnail]** en selecteert u deze (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). If you have selected a thumbnail and then decide that you want AEM to generate one from the spin set, select **[!UICONTROL Switch to Automatic thumbnail.]**

1. Voer een van de volgende handelingen uit:

   * Tik in de linkerbovenhoek van de pagina van de Editor voor de centrifugeset op **[!UICONTROL Add Asset.]**

   * Tik in het midden van de pagina van de Editor voor de centrifugeset op **[!UICONTROL Tap to open Asset Selector.]**
   Tik om de elementen te selecteren die u in de centrifugeset wilt opnemen. Geselecteerde assets hebben een vinkje. When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Select.]**

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Change the view by tapping the View icon and selecting **[!UICONTROL Column View]**, **[!UICONTROL Card View]**, or **[!UICONTROL List View.]**

   See [Working with Selectors](/help/assets/working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw ordenen of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![De volgorde van frame 11 in de centrifugeerset wijzigen door deze naar een nieuwe locatie te slepen.](assets/6_5_spinset-reorderassets.png)

   De volgorde van frame 11 in de centrifugeerset wijzigen door deze naar een nieuwe locatie te slepen.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en tikt u op **[!UICONTROL Delete Asset.]**

   * To apply a preset, near the upper-right corner of the page, tap **[!UICONTROL Preset]**, then select a preset to apply to all the assets at once.

1. Klik op **[!UICONTROL Save.]** de nieuwe centrifugeset in de map waarin u deze hebt gemaakt.

## Spin-sets weergeven {#viewing-spin-sets}

U kunt spin-sets maken in de gebruikersinterface of automatisch met behulp van voorinstellingen voor [batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). Set die is gemaakt met voorinstellingen voor batchsets, wordt echter *niet* weergegeven in de gebruikersinterface. U hebt op drie verschillende manieren toegang tot sets die zijn gemaakt met voorinstellingen voor batchsets. (Deze methoden zijn ook beschikbaar als u de centrifuges in de gebruikersinterface hebt gemaakt.)

>[!NOTE]
>
>U kunt sets ook weergeven in de gebruikersinterface, zoals wordt beschreven in [Spin-sets](#editing-spin-sets)bewerken.

**Draaisets weergeven**

1. Bij het openen van de eigenschappen van een afzonderlijk element. Eigenschappen geven aan welke sets het geselecteerde element lid zijn van (onder **[!UICONTROL Member of Sets]**). Klik op de naam van de set om de volledige set weer te geven.

   ![chlimage_1-156](assets/chlimage_1-384.png)

1. Van een lidafbeelding van om het even welke set. Select the **[!UICONTROL Sets]** menu to display the sets that the asset is a member of.

   ![chlimage_1-157](assets/chlimage_1-385.png)

1. From search, you can Select **[!UICONTROL Filters]**, then expand **[!UICONTROL Dynamic Media]** and select **[!UICONTROL Sets.]**

   De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde sets wordt de zoekopdracht uitgevoerd aan de hand van `Starts with` zoekcriteria die afwijken van AEM zoekopdracht op basis van `Contains` zoekcriteria. Het instellen van het filter op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde sets te doorzoeken.

   ![chlimage_1-158](assets/chlimage_1-386.png)

## Bewerken van centrifuges {#editing-spin-sets}

U kunt diverse bewerkingstaken uitvoeren op bijvoorbeeld de volgende centrifuges:

* Voeg afbeeldingen toe aan de centrifugeset.
* Wijzig de volgorde van de afbeeldingen in de centrifugeset.
* Elementen in de centrifugeset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de centrifugeset.

**Een centerset bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een set met centrifuges en tik op **[!UICONTROL Edit]** (potloodpictogram).
   * Houd de muisaanwijzer boven een in een centrifugeerset geplaatst element, tik op **[!UICONTROL Select]** (vinkpictogram) en tik vervolgens op **[!UICONTROL Edit]** de werkbalk.

   * Tik op een gecentreerd element en tik vervolgens op **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de centrifugeset te bewerken:

   * Als u de volgorde van afbeeldingen wilt wijzigen, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor herschikken om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, klikt u op de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, klikt u op **[!UICONTROL Add Asset.]** Navigeren naar een element, selecteert u het element en tikt u vervolgens **[!UICONTROL Select]** in de rechterbovenhoek.
Als u de afbeelding verwijdert die AEM gebruikt voor de miniatuur door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en klikt of tikt u erop **[!UICONTROL Delete Asset.]**
   * Tik op het pictogram Voorinstelling of klik op het pictogram Voorinstelling om een voorinstelling toe te passen.
   * Als u een volledige centrifugeset wilt verwijderen, navigeert u naar de centrifugeset, selecteert u deze en selecteert u **[!UICONTROL Delete]**

   >[!NOTE]
   >
   >You can edit the images in a Spin Set by navigating to the set, tap **[!UICONTROL Set Members]** in the left rail, and then tap the Pencil icon on an individual asset to open the editing window.

1. Klik **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

## Voorvertoning van centrifuges weergeven {#previewing-spin-sets}

Zie [Voorvertoning van elementen](/help/assets/previewing-assets.md)weergeven.

## Spin-sets publiceren {#publishing-spin-sets}

Zie Elementen [](/help/assets/publishing-dynamicmedia-assets.md)publiceren.
