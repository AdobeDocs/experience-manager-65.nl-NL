---
title: Gemengde mediasets
description: Leer hoe u met gemengde mediasets werkt in Dynamic Media
uuid: cecad772-ed05-46f6-ba44-107195866b0d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ed84157a-e6b4-4dde-af2e-a1e0b6259628
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Gemengde mediasets{#mixed-media-sets}

Met gemengde mediasets kunt u in één presentatie een combinatie van afbeeldingen, afbeeldingssets, centrifuges en video&#39;s aanbieden.

De gemengde Reeksen van Media worden aangewezen door een banner met het woord **[!UICONTROL GemengdMediaSet]**. Als de gemengde mediaset wordt gepubliceerd, staat bovendien de publicatiedatum, die wordt aangegeven door het pictogram **[!UICONTROL Wereld]** , op de banner samen met de laatste wijzigingsdatum, die wordt aangegeven door het **[!UICONTROL potloodpictogram]** .

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Zie Elementen [beheren met de aanraakinterface](/help/assets/managing-assets-touch-ui.md)voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Gemengde mediasets {#quick-start-mixed-media-sets}

Ga als volgt te werk om snel aan de slag te gaan met gemengde mediasets:

1. [Upload uw elementen](#uploading-assets).

   Begin door de beelden en video&#39;s voor uw Gemengde Reeksen van Media te uploaden. Maak indien nodig uw [afbeeldingssets](/help/assets/image-sets.md) en [centrifuges](/help/assets/spin-sets.md). Omdat gebruikers kunnen inzoomen op afbeeldingen in de gemengde Media Set Viewer, moet u rekening houden met zoomen wanneer u afbeeldingen kiest. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn.

1. [Gemengde mediasets maken.](#creating-mixed-media-sets)

   Als u een gemengde mediaset wilt maken, tikt u op de elementenpagina op **[!UICONTROL Maken > Gemengde mediaset]** en geeft u een naam op voor de set, kiest u de elementen en kiest u de volgorde waarin de afbeeldingen worden weergegeven.

   Zie [Werken met kiezers.](/help/assets/working-with-selectors.md)

1. Stel indien nodig [gemengde voorinstellingen](/help/assets/managing-viewer-presets.md)voor de Media Viewer in.

   Beheerders kunnen voorinstellingen voor gemengde mediaset maken of wijzigen. Als u de gemengde media met een viewervoorinstelling wilt weergeven, selecteert u de gemengde mediaset en selecteert u **[!UICONTROL Viewers]** in het keuzemenu voor de linkertrack.

   Zie **[!UICONTROL Gereedschappen > Middelen > Voorinstellingen]** viewer om voorinstellingen voor viewers te maken of te bewerken.

   Zie Voorinstellingen voor viewers [toevoegen en bewerken.](/help/assets/managing-viewer-presets.md)

1. [Voorvertoning gemengde mediasets.](#previewing-mixed-media-sets)

   Selecteer de gemengde Mediaset en u kunt er een voorvertoning van weergeven. Klik op de miniatuurpictogrammen om de gemengde mediaset in de geselecteerde viewer te bekijken. U kunt verschillende Viewers kiezen in het menu **[!UICONTROL Viewers]** , dat beschikbaar is in het linkervervolgkeuzemenu.

1. [Gemengde mediasets publiceren.](#publishing-mixed-media-sets)

   Wanneer u een gemengde mediaset publiceert, worden de URL en de insluitreeks geactiveerd. Bovendien moet u de voorinstelling [van de viewer](/help/assets/managing-viewer-presets.md#publishing-viewer-presets)publiceren.

1. [Koppel URL&#39;s aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md) of [sluit de video- of afbeeldingsviewer](/help/assets/embed-code.md)in.

   Met AEM-elementen worden URL-aanroepen voor gemengde mediasets gemaakt en geactiveerd nadat u de gemengde mediasets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de Gemengde Reeks van Media, dan in het linkerspoordrop-down menu, uitgezochte **[!UICONTROL Kijkers]**.

   Zie Een gemengde mediaset [koppelen aan een webpagina](/help/assets/linking-urls-to-yourwebapplication.md) en de video- of afbeeldingsviewer [](/help/assets/embed-code.md)insluiten.

Indien nodig kunt u [gemengde mediasets](#editing-mixed-media-sets)bewerken. Daarnaast kunt u de eigenschappen [van](/help/assets/managing-assets-touch-ui.md#editing-properties)gemengde mediaset weergeven en wijzigen.

>[!NOTE]
>
>Als u kwesties creeert reeksen hebt, zie het [Oplossen van problemen Dynamische Media - wijze](/help/assets/troubleshoot-dms7.md)Scene7.

## Elementen uploaden {#uploading-assets}

Begin door de beelden en video&#39;s voor uw Gemengde Reeksen van Media te uploaden. Omdat gebruikers kunnen inzoomen op afbeeldingen in de gemengde Media Set Viewer, dient u rekening te houden met zoomen wanneer u afbeeldingen kiest. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn.

Als u bovendien centrifuges of afbeeldingssets wilt toevoegen aan de gemengde mediaset, maakt u deze ook.

## Gemengde mediasets maken {#creating-mixed-media-sets}

U kunt afbeeldingen, afbeeldingssets, centrifuges en video&#39;s toevoegen aan de gemengde mediaset. Zorg ervoor dat de bestanden, afbeeldingssets en centrifuges klaar zijn om te worden gepubliceerd voordat u ze aan de gemengde mediaset toevoegt.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

**Een gemengde mediaset maken**

1. Navigeer in Elementen naar de plaats waar u een gemengde mediaset wilt maken, klik op **[!UICONTROL Maken]** en selecteer **[!UICONTROL Gemengde mediaset]**. U kunt de set ook maken vanuit een map die uw elementen bevat. De Gemengde Redacteur van de Reeks van Media toont.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. In de Gemengde Redacteur van de Reeks van Media, in **[!UICONTROL Titel]**, ga een naam voor de Gemengde Reeks van Media in. De naam wordt in de banner weergegeven in de gemengde mediaset. Voer eventueel een beschrijving in.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Wanneer u de gemengde mediaset maakt, kunt u de miniatuur van de gemengde mediaset wijzigen of AEM toestaan de miniatuur automatisch te selecteren op basis van de elementen in de gemengde mediaset. Als u een miniatuur wilt selecteren, klikt u op de miniatuur **** Wijzigen en selecteert u een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Als u een miniatuur hebt geselecteerd en vervolgens besluit dat u een miniatuur van de gemengde mediaset wilt genereren, selecteert u **[!UICONTROL Schakelen naar automatische miniatuur]**.

1. Tik op de Asset Selector om de elementen te selecteren die u in de gemengde mediaset wilt opnemen. Selecteer ze en klik op **[!UICONTROL Selecteren]**.

   Met de Kiezer van Activa, kunt u naar activa zoeken door in een sleutelwoord te typen en **[!UICONTROL Terugkeer]** te tikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door het pictogram **[!UICONTROL Weergave]** te selecteren en **[!UICONTROL Lijstweergave]**, **[!UICONTROL Kolomweergave]** of **[!UICONTROL Kaartweergave]** te selecteren.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-383.png)

1. Wijzig de volgorde van de elementen door deze omhoog of omlaag in de lijst te slepen (selecteer indien nodig het pictogram **[!UICONTROL Opnieuw ordenen]** ).

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Als u miniaturen wilt toevoegen, klikt u op het pictogram **+** **[!UICONTROL miniatuur]** naast de afbeelding en navigeert u naar de gewenste miniatuur. Als u alle miniatuurafbeeldingen hebt geselecteerd, klikt u op **[!UICONTROL Opslaan]**.

   >[!NOTE]
   >
   >Tik op Element **[!UICONTROL toevoegen als u elementen]** wilt toevoegen.

1. Als u een element wilt verwijderen, schakelt u het desbetreffende selectievakje in en tikt u op Element **** verwijderen.
1. Als u een voorinstelling wilt toepassen, tikt u op **[!UICONTROL Voorinstelling]** in de rechterbovenhoek en selecteert u een voorinstelling die u op de elementen wilt toepassen.
1. Click **[!UICONTROL Save]**. De nieuwe gemengde mediaset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Gemengde mediasets bewerken {#editing-mixed-media-sets}

U kunt diverse bewerkingstaken rechtstreeks in de gebruikersinterface uitvoeren op elementen in gemengde mediasets, [net als op elementen](/help/assets/managing-assets-touch-ui.md). U kunt ook de volgende handelingen uitvoeren in Gemengde Mediasets:

* Voeg elementen toe aan de gemengde mediaset.
* Wijzig de volgorde van elementen in de gemengde mediaset.
* Elementen verwijderen uit de gemengde mediaset.
* Voorinstellingen voor viewers toepassen.
* Wijzig de standaardminiatuur.

**Een gemengde mediaset bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een element uit een gemengde mediaset en tik op **[!UICONTROL Bewerken]** (potloodpictogram).
   * Tik met de muis over een gemengde mediaset op **[!UICONTROL Selecteren]** (vinkpictogram) en tik vervolgens op **[!UICONTROL Bewerken]** op de werkbalk.

   * Tik op een element uit een gemengde mediaset en tik vervolgens op **[!UICONTROL Bewerken]** (potloodpictogram) op de werkbalk.

1. Voer in de Editor gemengde mediaset een van de volgende handelingen uit:

   * Tik in het linkerdeelvenster op **[!UICONTROL Elementen]** (afbeeldingspictogram) en sleep een element naar een nieuwe locatie om de volgorde van de elementen te wijzigen.
   * Tik op Element **** toevoegen om elementen toe te voegen. Navigeer naar de elementen. Tik op het pictogram van het vinkje voor elk element dat u wilt toevoegen. Houd de muisaanwijzer boven de afbeelding van het element (niet de naam van het element). Tik in de rechterbovenhoek op **[!UICONTROL Selecteren]**.

   * Tik op **[!UICONTROL Elementen]** (afbeeldingspictogram) in het linkerdeelvenster en selecteer vervolgens het element om een element te verwijderen. Tik op de werkbalk op Element **[!UICONTROL verwijderen]**.

   * Tik in het linkerdeelvenster op **[!UICONTROL Elementen]** (afbeeldingspictogram) om elementen op naam in oplopende of aflopende volgorde te sorteren. Tik rechts van de kop **[!UICONTROL Middelen]** op de pictogrammen voor de invoegpunt omhoog of omlaag.

      >[!NOTE]
      >
      >    * Als u een volledige gemengde mediaset wilt verwijderen, navigeert u vanuit elke weergavemodus (zoals **[!UICONTROL Kaartweergave]** of **[!UICONTROL Kolomweergave]**) naar de gemengde mediaset. Houd de cursor boven het element en tik op het vinkje om het te selecteren. Druk op **[!UICONTROL Backspace]** op het toetsenbord of klik op **[!UICONTROL Meer]** (drie punten) op de werkbalk en tik vervolgens op **[!UICONTROL Delete]**.
         >
         >    
      * U kunt de elementen in een gemengde mediaset bewerken door naar de set te navigeren, op Leden **instellen te klikken]** in de linkerrails en vervolgens op het pictogram **[!UICONTROL Potlood]** op een afzonderlijk element te tikken om het bewerkingsvenster te openen.


1. Tik op **[!UICONTROL Opslaan]** als u klaar bent met bewerken.

   >[!NOTE]
   >
   >* Als u de elementen in een gemengde mediaset wilt bewerken, navigeert u naar de gemengde mediaset. Tik (niet selecteren) op de set om deze te openen op de pagina Voorvertoning van AEM-set. Klik in het linkerspoor op het inlasteken omlaag om de vervolgkeuzelijst te openen en tik vervolgens op Leden **** instellen. Houd de muisaanwijzer boven een element op de pagina Leden instellen en tik op **[!UICONTROL Bewerken]** (potloodpictogram) om de bewerkingspagina te openen.
      >
      >
   * Als u een volledige gemengde mediaset wilt verwijderen, navigeert u vanuit elke weergavemodus (zoals de Kaart- of kolomweergave) naar de gemengde mediaset. Houd de muisaanwijzer boven de set en tik op **Selecteren]** (vinkpictogram). Druk op **[!UICONTROL Backspace]** op uw toetsenbord of tik op **[!UICONTROL Meer]** (rij met drie punten) en tik vervolgens op **[!UICONTROL Delete]**.


## Voorvertoning van gemengde mediasets {#previewing-mixed-media-sets}

Zie Elementen [](/help/assets/previewing-assets.md) voorvertonen voor meer informatie over het voorvertonen van gemengde mediasets.

## Gemengde mediasets publiceren {#publishing-mixed-media-sets}

Zie Elementen [](/help/assets/publishing-dynamicmedia-assets.md) publiceren voor meer informatie over het publiceren van gemengde mediasets.

>[!NOTE]
>
>Als de gemengde mediaset de eerste keer dat u deze publiceert niet volledig in de leveringsservice terechtkomt, moet u de gemengde mediaset mogelijk nog een keer publiceren.

