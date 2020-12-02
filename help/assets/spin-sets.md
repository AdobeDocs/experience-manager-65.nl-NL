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
source-git-commit: c3ae4447581d946554d792c68d31b47a6b67d5df
workflow-type: tm+mt
source-wordcount: '1761'
ht-degree: 7%

---


# Spin Sets{#spin-sets}

Een centrifugeerset simuleert de echte handeling waarbij een object wordt omgedraaid om het te onderzoeken. Met centrifuges kunt u items vanuit elke hoek bekijken en de belangrijkste visuele details vanuit elke hoek verkrijgen.

Een centrifugeerset simuleert een kijkervaring van 360 graden. Dynamische media biedt centrifugesets met één as waarin gebruikers een item kunnen roteren. Bovendien kunnen gebruikers met een paar eenvoudige muisklikken in- en uitzoomen op een vrije vorm en een willekeurige weergave pannen. Op deze manier kunnen gebruikers een item vanuit een bepaald gezichtspunt nader onderzoeken.

De Reeksen van de draaien worden aangewezen door een banner met het woord **[!UICONTROL SPINSET.]**. Bovendien als de Reeks van de Draai wordt gepubliceerd, dan is de publicatiedatum, die door het **[!UICONTROL World]** pictogram wordt vermeld op de banner samen met de laatste wijzigingsdatum, die door **[!UICONTROL Pencil]** pictogramvertoningen wordt vermeld.

![chlimage_1-](assets/chlimage_1-380.png)

>[!NOTE]
>
>Zie [Elementen beheren](/help/assets/manage-assets.md) voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Draaisets {#quick-start-spin-sets}

Ga als volgt te werk om snel aan de slag te gaan met centrifuges:

1. [Upload uw afbeeldingen voor meerdere weergaven.](#uploading-assets-for-spin-sets)

   U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset en 16-24 voor een tweedimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30 graden (360/12) voor elke opname.

1. [Spin-sets maken.](#creating-spin-sets)

   Als u een centrifugeset wilt maken, selecteert u **[!UICONTROL Create > Spin Set]** en geeft u de set een naam, kiest u de elementen en kiest u de volgorde waarin de afbeeldingen worden weergegeven.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md).

   >[!NOTE]
   >
   >U kunt ook automatisch spinsets maken via [voorinstellingen voor batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). **Belangrijk:** Batchsets worden gemaakt door het IPS (Image Production System) als onderdeel van het opnemen van elementen en zijn alleen beschikbaar in de modus Dynamische media - Scene7.

1. Stel [Voorinstellingen van de viewer voor de centrifugeerset ](/help/assets/managing-viewer-presets.md) naar wens in.

   Beheerders kunnen viewervoorinstellingen voor spinsets maken of wijzigen. Als u uw spinset wilt weergeven met een viewervoorinstelling, selecteert u de spinset en selecteert u **Viewers** in het vervolgkeuzemenu voor het linkerspoor.

   Zie **[!UICONTROL Tools > Assets > Viewer Presets]** om voorinstellingen voor viewers te maken of te bewerken.

   Zie [Voorinstellingen voor viewers toevoegen en bewerken.](/help/assets/managing-viewer-presets.md)

1. [Spin-sets](#viewing-spin-sets) weergeven.

   U kunt sets die zijn gemaakt met voorinstellingen voor batchsets op drie verschillende manieren weergeven en openen. (Sets die zijn gemaakt met voorinstellingen voor batchsets, worden *niet* weergegeven in de gebruikersinterface.)

1. [Voorvertoning van centrifuges.](/help/assets/previewing-assets.md)

   Selecteer de centrifugeset en u kunt er een voorvertoning van weergeven. Roteer de centrifugeset. U kunt verschillende kijkers van **[!UICONTROL Viewers]** menu kiezen, beschikbaar van het linkerspoordrop-down menu.

1. [Spin-sets publiceren.](/help/assets/publishing-dynamicmedia-assets.md)

   Als u een centrifugeerset publiceert, worden de URL- en insluitreeks geactiveerd. Daarnaast moet u [de viewervoorinstelling](/help/assets/managing-viewer-presets.md) publiceren.

1. [Koppel URL&#39;s aan uw webtoepassing ](/help/assets/linking-urls-to-yourwebapplication.md) of  [sluit de video- of afbeeldingsviewer](/help/assets/embed-code.md) in.

   AEM Assets maakt URL-aanroepen voor centrifuges en activeert deze nadat u de centrifuges hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de centrifugeset en selecteer **[!UICONTROL Viewers.]** in het keuzemenu voor de linkertrack

   Zie [Een spinset koppelen aan een webpagina](/help/assets/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/embed-code.md).

Als dat nodig is, kunt u [centrifuges bewerken](#editing-spin-sets). Bovendien kunt u [Vastgestelde eigenschappen van de Spin](/help/assets/manage-assets.md#editing-properties) bekijken en wijzigen.

## Elementen uploaden voor centrifuges {#uploading-assets-for-spin-sets}

U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset en 16-24 voor een tweedimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30 graden (360/12) voor elke opname.

U kunt afbeeldingen voor de centrifuges uploaden zoals u [elk ander element in AEM Assets](/help/assets/manage-assets.md) uploadt.

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
>U kunt ook automatisch spinsets maken via [voorinstellingen voor batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). **Belangrijk:** Batchsets worden gemaakt door het IPS (Image Production System) als onderdeel van het opnemen van elementen en zijn alleen beschikbaar in de modus Dynamische media - Scene7.
>
>Zie &quot;Voorinstellingen voor batchsets maken om automatisch afbeeldingssets en centrifuges te genereren&quot; in [Dynamische media configureren - Scene7-modus](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).


>[!NOTE]
>
>De volgorde waarin afbeeldingen worden weergegeven in een draaiset. Zorg ervoor dat u ze zo bestelt dat de centrifuge een vloeiende weergave van 360 graden biedt.

**Draaisets maken**

1. Navigeer in Elementen naar de plaats waar u een centrifugeset wilt maken, klik op **[!UICONTROL Create]** en selecteer **[!UICONTROL Spin Set.]** U kunt de set ook maken vanuit een map die uw elementen bevat. De Editor van spinset wordt weergegeven.

   ![6_5_spinset-createpulldownmenu](assets/6_5_spinset-createpulldownmenu.png)

1. Voer in het veld **[!UICONTROL Title]** in de Editor voor de centrifugeset een naam in voor de centrifugeerset. De naam wordt weergegeven in de banner over de centrifugeset. Voer eventueel een beschrijving in.

   ![6_5_spinset-spinseteditortitle](assets/6_5_spinset-spinseteditortitle.png)

   >[!NOTE]
   >
   >Wanneer u de centrifugeset maakt, kunt u de miniatuur van de centrifugeset wijzigen of AEM de miniatuur automatisch selecteren op basis van de elementen in de centrifugeset. Als u een miniatuur wilt selecteren, klikt u op **[!UICONTROL Change thumbnail]** en selecteert u een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Selecteer **[!UICONTROL Switch to Automatic thumbnail.]** als u een miniatuur hebt geselecteerd en vervolgens wilt bepalen dat u een miniatuur AEM genereren op basis van de centrifugeset.

1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Add Asset.]** in de linkerbovenhoek van de pagina Spin Set Editor.

   * Tik op **[!UICONTROL Tap to open Asset Selector.]** in het midden van de pagina van de Editor voor centrifugeerset
   Tik om de elementen te selecteren die u in de centrifugeset wilt opnemen. Geselecteerde assets hebben een vinkje. Tik, als u klaar bent, in de rechterbovenhoek van de pagina op **[!UICONTROL Select.]**

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door te tikken op het pictogram Weergave en **[!UICONTROL Column View]**, **[!UICONTROL Card View]** of **[!UICONTROL List View.]** te selecteren

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw ordenen of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![De volgorde van frame 11 in de centrifugeerset wijzigen door deze naar een nieuwe locatie te slepen.](assets/6_5_spinset-reorderassets.png)

   De volgorde van frame 11 in de centrifugeerset wijzigen door deze naar een nieuwe locatie te slepen.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en tikt u op **[!UICONTROL Delete Asset.]**

   * Tik op **[!UICONTROL Preset]** en selecteer vervolgens een voorinstelling die u op alle elementen tegelijk wilt toepassen om een voorinstelling toe te passen in de rechterbovenhoek van de pagina.

1. Klik op **[!UICONTROL Save.]** De nieuwe centrifugeset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Spin-sets {#viewing-spin-sets} weergeven

U kunt centrifuges maken in de gebruikersinterface of automatisch met [voorinstellingen voor batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). Sets die zijn gemaakt met voorinstellingen voor batchsets, worden echter *niet* weergegeven in de gebruikersinterface. U hebt op drie verschillende manieren toegang tot sets die zijn gemaakt met voorinstellingen voor batchsets. (Deze methoden zijn ook beschikbaar als u de centrifuges in de gebruikersinterface hebt gemaakt.)

>[!NOTE]
>
>U kunt sets ook weergeven in de gebruikersinterface zoals wordt beschreven in [Spin Sets bewerken](#editing-spin-sets).

**Draaisets weergeven**

1. Bij het openen van de eigenschappen van een afzonderlijk element. Eigenschappen geven aan welke sets het geselecteerde element lid zijn van (onder **[!UICONTROL Member of Sets]**). Klik op de naam van de set om de volledige set weer te geven.

   ![chlimage_1-156](assets/chlimage_1-384.png)

1. Van een lidafbeelding van om het even welke set. Selecteer het menu **[!UICONTROL Sets]** om de sets weer te geven waarvan het element lid is.

   ![chlimage_1-157](assets/chlimage_1-385.png)

1. Vanuit zoekopdracht kunt u **[!UICONTROL Filters]** selecteren, vervolgens **[!UICONTROL Dynamic Media]** uitvouwen en **[!UICONTROL Sets.]** selecteren

   De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde reeksen, wordt de onderzoeksvraag geleid gebruikend `Starts with` onderzoekscriteria die van AEM onderzoek verschillend zijn dat op het gebruiken van `Contains` onderzoekscriteria gebaseerd is. Het instellen van het filter op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde sets te doorzoeken.

   ![chlimage_1-158](assets/chlimage_1-386.png)

## Spinsets bewerken {#editing-spin-sets}

U kunt diverse bewerkingstaken uitvoeren op bijvoorbeeld de volgende centrifuges:

* Voeg afbeeldingen toe aan de centrifugeset.
* Wijzig de volgorde van de afbeeldingen in de centrifugeset.
* Elementen in de centrifugeset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de centrifugeset.

**Een centerset bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een in een centrifugeerset geplaatst element en tik op **[!UICONTROL Edit]** (potloodpictogram).
   * Tik met de muis over een gecentreerd element op **[!UICONTROL Select]** (vinkpictogram) en tik **[!UICONTROL Edit]** op de werkbalk.

   * Tik op een gecentreerd element en tik op **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de centrifugeset te bewerken:

   * Als u de volgorde van afbeeldingen wilt wijzigen, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor herschikken om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, klikt u op de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, klikt u op **[!UICONTROL Add Asset.]** Navigeren naar een element, selecteert u het element en tikt u vervolgens op **[!UICONTROL Select]** in de rechterbovenhoek.
Als u de afbeelding verwijdert die AEM gebruikt voor de miniatuur door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en klikt of tikt u op **[!UICONTROL Delete Asset.]**
   * Tik op het pictogram Voorinstelling of klik op het pictogram Voorinstelling om een voorinstelling toe te passen.
   * Als u een volledige centrifugeset wilt verwijderen, navigeert u naar de centrifugeset, selecteert u deze en selecteert u **[!UICONTROL Delete]**

   >[!NOTE]
   >
   >U kunt de afbeeldingen in een centrifugeset bewerken door naar de set te navigeren, op **[!UICONTROL Set Members]** in de linkertrack te tikken en vervolgens op het potloodpictogram op een afzonderlijk element te tikken om het bewerkingsvenster te openen.

1. Klik **[!UICONTROL Save]** wanneer klaar het uitgeven.

## Voorvertoning van centrifuges {#previewing-spin-sets}

Zie [Elementen voorvertonen](/help/assets/previewing-assets.md).

## Spin-sets {#publishing-spin-sets} publiceren

Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md).
