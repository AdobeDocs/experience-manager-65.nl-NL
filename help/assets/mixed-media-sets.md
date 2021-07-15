---
title: Mixed Media Sets
description: Leer hoe u met gemengde mediasets werkt in Dynamic Media
uuid: cecad772-ed05-46f6-ba44-107195866b0d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ed84157a-e6b4-4dde-af2e-a1e0b6259628
docset: aem65
feature: Gemengde mediasets, beheer van bedrijfsmiddelen
role: User, Admin
exl-id: 70a72fb9-a289-4eda-abcc-300edf9f1961
source-git-commit: f5eccfc1b81d8e24cafe917f3ad74b472c0676bd
workflow-type: tm+mt
source-wordcount: '1384'
ht-degree: 22%

---

# Gemengde mediasets{#mixed-media-sets}

Met gemengde mediasets kunt u in één presentatie een combinatie van afbeeldingen, afbeeldingssets, centrifuges en video&#39;s aanbieden.

Gemengde mediasets worden aangegeven door een banner met het woord **[!UICONTROL MixedMediaSet]**. Als de gemengde mediaset wordt gepubliceerd, wordt bovendien de publicatiedatum, die door het pictogram **[!UICONTROL World]** wordt aangegeven, samen met de laatste wijzigingsdatum op de banner weergegeven. Dit wordt aangegeven door het pictogram **[!UICONTROL Pencil]**.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Zie [Elementen beheren](/help/assets/manage-assets.md) voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Gemengde mediasets {#quick-start-mixed-media-sets}

Ga als volgt te werk om snel aan de slag te gaan met gemengde mediasets:

1. [Upload uw elementen](#uploading-assets).

   Begin door de afbeeldingen en video&#39;s voor uw gemengde mediasets te uploaden. Maak indien nodig uw eigen [afbeeldingsets](/help/assets/image-sets.md) en [spinsets](/help/assets/spin-sets.md). Omdat gebruikers kunnen inzoomen op afbeeldingen in de gemengde Media Set Viewer, moet u de afbeeldingen zorgvuldig kiezen. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn in de grootste dimensie.

1. [Gemengde mediasets](#creating-mixed-media-sets) maken.

   Als u een gemengde mediaset wilt maken, tikt u op de elementenpagina op **[!UICONTROL Create]** > **[!UICONTROL Mixed Media Set]** en geeft u de set een naam, kiest u de elementen en kiest u de volgorde waarin de afbeeldingen worden weergegeven.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md).

1. Stel [Voorinstellingen voor gemengde media-viewer](/help/assets/managing-viewer-presets.md) naar wens in.

   Beheerders kunnen viewervoorinstellingen voor gemengde mediasets maken of wijzigen. Als u de gemengde media met een viewervoorinstelling wilt weergeven, selecteert u de gemengde mediaset en selecteert u **[!UICONTROL Viewers]** in de vervolgkeuzelijst van het linkerspoor.

   Als u viewervoorinstellingen wilt maken of bewerken, raadpleegt u **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.

   Zie [Voorinstellingen voor viewers toevoegen en bewerken](/help/assets/managing-viewer-presets.md).

1. [Voorvertoning gemengde mediasets](#previewing-mixed-media-sets).

   Selecteer de gemengde Mediaset en u kunt er een voorvertoning van weergeven. Klik op de miniatuurpictogrammen om de gemengde mediaset in de geselecteerde viewer te bekijken. U kunt verschillende Viewers van **[!UICONTROL Viewers]** menu kiezen, beschikbaar van het linkerspoordrop-down menu.

1. [Gemengde mediasets](#publishing-mixed-media-sets) publiceren.

   Wanneer u een gemengde mediaset publiceert, worden de URL en de insluitreeks geactiveerd. Daarnaast moet u [de viewervoorinstelling](/help/assets/managing-viewer-presets.md#publishing-viewer-presets) publiceren.

1. [Koppel URL&#39;s aan uw webtoepassing ](/help/assets/linking-urls-to-yourwebapplication.md) of  [sluit de video- of afbeeldingsviewer](/help/assets/embed-code.md) in.

   Adobe Experience Manager Assets maakt URL-aanroepen voor gemengde mediasets en activeert deze nadat u de gemengde mediasets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de Gemengde Reeks van Media, dan in de linkerspoordrop-down menu, uitgezocht **[!UICONTROL Viewers]**.

   Zie [Een gemengde mediaset koppelen aan een webpagina](/help/assets/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/embed-code.md).

Indien nodig kunt u [Gemengde Mediasets](#editing-mixed-media-sets) bewerken. Daarnaast kunt u [Eigenschappen van gemengde mediaset](/help/assets/manage-assets.md#editing-properties) weergeven en wijzigen.

>[!NOTE]
>
>Zie [Problemen met Dynamic Media oplossen - Scene7-modus](/help/assets/troubleshoot-dms7.md) als u problemen ondervindt bij het maken van sets.

## Elementen uploaden {#uploading-assets}

Begin door de afbeeldingen en video&#39;s voor uw gemengde mediasets te uploaden. Omdat gebruikers kunnen inzoomen op afbeeldingen in de gemengde Media Set Viewer, moet u de afbeeldingen zorgvuldig kiezen. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn in de grootste dimensie.

Als u bovendien pinsets of afbeeldingssets wilt toevoegen aan de gemengde mediaset, maakt u ook deze sets.

## Gemengde mediasets maken {#creating-mixed-media-sets}

U kunt afbeeldingen, afbeeldingssets, centrifuges en video&#39;s toevoegen aan de gemengde mediaset. Zorg ervoor dat de bestanden, afbeeldingssets en centrifuges klaar zijn om te worden gepubliceerd voordat u ze aan de gemengde mediaset toevoegt.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

**Een gemengde mediaset maken:**

1. Ga in Assets naar de plaats waar u een gemengde mediaset wilt maken, klik op **[!UICONTROL Create]** en selecteer **[!UICONTROL Mixed Media Set]**. U kunt de set ook maken vanuit een map die uw assets bevat. De editor voor gemengde mediasets wordt weergegeven.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. In de Gemengde Redacteur van de Reeks van Media, in **[!UICONTROL Title]**, ga een naam voor de Gemengde Reeks van Media in. De naam wordt in de banner weergegeven in de gemengde mediaset. Voer eventueel een beschrijving in.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Wanneer u de gemengde mediaset maakt, kunt u de miniatuur van de gemengde mediaset wijzigen of Experience Manager toestaan de miniatuur automatisch te selecteren op basis van de elementen in de gemengde mediaset. Als u een miniatuur wilt selecteren, klikt u op **[!UICONTROL Change thumbnail]** en selecteert u een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Selecteer **[!UICONTROL Switch to Automatic thumbnail]** als u een miniatuur hebt geselecteerd en vervolgens wilt dat Experience Manager een miniatuur genereert van de gemengde mediaset.

1. Tik op de Asset Selector, zodat u elementen kunt selecteren die u wilt opnemen in de gemengde mediaset. Selecteer deze en klik op **[!UICONTROL Select]**.

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door het pictogram **[!UICONTROL View]** te selecteren en **[!UICONTROL List View]**, **[!UICONTROL Column View]** of **[!UICONTROL Card View]** te selecteren.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-383.png)

1. Wijzig de volgorde van de elementen door deze omhoog of omlaag te slepen in de lijst (moet het pictogram **[!UICONTROL Reorder]** selecteren).

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Als u miniaturen wilt toevoegen, klikt u op het pictogram **+** **[!UICONTROL thumbnail]** naast de afbeelding en gaat u naar de gewenste miniatuur. Klik wanneer u alle miniatuurafbeeldingen hebt geselecteerd op **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Tik op **[!UICONTROL Add Asset]** als u elementen wilt toevoegen.

1. Als u een element wilt verwijderen, schakelt u het desbetreffende selectievakje in en tikt u op **[!UICONTROL Delete Asset]**.
1. Tik op **[!UICONTROL Preset]** in de rechterbovenhoek om een voorinstelling toe te passen en selecteer een voorinstelling die u op de elementen wilt toepassen.
1. Klik op **[!UICONTROL Save]**. De nieuwe gemengde mediaset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Gemengde mediasets bewerken {#editing-mixed-media-sets}

U kunt verschillende bewerkingstaken rechtstreeks in de gebruikersinterface uitvoeren op elementen in gemengde mediasets [net als op elementen in Elementen](/help/assets/manage-assets.md). U kunt ook de volgende handelingen uitvoeren in Gemengde Mediasets:

* Voeg elementen toe aan de gemengde mediaset.
* Elementen opnieuw rangschikken in de gemengde mediaset.
* Elementen verwijderen uit de gemengde mediaset.
* Voorinstellingen voor viewers toepassen.
* Wijzig de standaardminiatuur.

**Een gemengde mediaset bewerken:**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een element uit een gemengde mediaset en tik op **[!UICONTROL Edit]** (potloodpictogram).
   * Tik met de muis over een element uit een gemengde mediaset op **[!UICONTROL Select]** (vinkpictogram) en tik **[!UICONTROL Edit]** op de werkbalk.

   * Tik op een element uit een gemengde mediaset en tik op **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer in de Editor gemengde mediaset een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Assets]** (afbeeldingspictogram) om elementen opnieuw te rangschikken. Sleep een element naar een nieuwe locatie.
   * Tik op **[!UICONTROL Add Asset]** om elementen toe te voegen. Navigeer naar de elementen. Tik op het pictogram van het vinkje voor elk element dat u wilt toevoegen. Houd de muisaanwijzer boven de afbeelding van het element (niet de naam van het element). Tik in de rechterbovenhoek op **[!UICONTROL Select]**.

   * Tik op **[!UICONTROL Assets]** (afbeeldingspictogram) in het linkerdeelvenster en selecteer vervolgens het element om een element te verwijderen. Tik op **[!UICONTROL Delete Asset]** op de werkbalk.

   * Tik in het linkerdeelvenster op **[!UICONTROL Assets]** (afbeeldingspictogram) om elementen op naam in oplopende of aflopende volgorde te sorteren. Tik rechts van de **[!UICONTROL Assets]**-kop op de pictogrammen voor de invoegpunt.

      >[!NOTE]
      >
      >* Als u een volledige gemengde mediaset wilt verwijderen, navigeert u vanuit elke weergavemodus (zoals **[!UICONTROL Card View]** of **[!UICONTROL Column View]**) naar de gemengde mediaset. Houd de muisaanwijzer boven het element en tik op het vinkje zodat u het kunt selecteren. Druk op **[!UICONTROL Backspace]** op het toetsenbord of klik **[!UICONTROL More]** (drie punten) op de werkbalk en tik vervolgens op **[!UICONTROL Delete]**.
         >
         >
      * U kunt elementen in een gemengde mediaset bewerken door naar de set te navigeren en op **[!UICONTROL Set Members]** in de linkertrack te klikken. Tik op het pictogram **[!UICONTROL Pencil]** op een afzonderlijk element zodat u dit in het bewerkingsvenster opent.


1. Tik **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

   >[!NOTE]
   >
   >* Als u de assets in een gemengde mediaset wilt bewerken, gaat u naar de gemengde mediaset. Tik (niet selecteren) op de set zodat deze wordt geopend op de pagina Voorvertoning Experience Manager instellen. Klik in de linkertrack op het inlasteken omlaag om de vervolgkeuzelijst te openen en tik vervolgens op **[!UICONTROL Set Members]**. Houd de muisaanwijzer op een element in de pagina Leden instellen en tik op **[!UICONTROL Edit]** (potloodpictogram) om de bewerkingspagina te openen.
      >
      >
   * Als u een volledige gemengde mediaset wilt verwijderen, gaat u vanuit een willekeurige weergavemodus (zoals kaart- of kolomweergave) naar de gemengde mediaset. Houd de muis boven de set en tik op **Select** (vinkpictogram). Druk op **[!UICONTROL Backspace]** op het toetsenbord of tik **[!UICONTROL More]** (rij met drie punten) en tik vervolgens op **[!UICONTROL Delete]**.


## Voorvertoning van gemengde mediasets {#previewing-mixed-media-sets}

Zie [Elementen voorvertonen](/help/assets/previewing-assets.md) voor meer informatie over het voorvertonen van gemengde mediasets.

## Gemengde mediasets publiceren {#publishing-mixed-media-sets}

Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van gemengde Mediasets.

>[!NOTE]
>
>Als de gemengde mediaset de eerste keer dat u deze publiceert niet volledig in de leveringsservice terechtkomt, publiceert u de gemengde mediaset een tweede keer.
