---
title: Image Sets
description: Leer hoe u met afbeeldingssets werkt in Dynamic Media
uuid: ca2fd5b0-656e-4960-b10c-f0ec3d418760
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ccc4eb23-934c-4e67-860b-a6faa2bcaafc
docset: aem65
translation-type: tm+mt
source-git-commit: 45de0f9d9570d64cacf7009d64072858012869a0

---


# Image Sets {#image-sets}

Afbeeldingssets bieden gebruikers een geïntegreerde weergave, waarbij gebruikers verschillende weergaven van een item kunnen zien door op een miniatuurafbeelding te klikken. Met Afbeeldingssets kunt u alternatieve weergaven van een item presenteren en de viewer beschikt over zoomgereedschappen waarmee u afbeeldingen op de juiste wijze kunt bekijken.

Afbeeldingsets worden aangegeven door een banner met het woord `IMAGESET`. In addition, if the Image Set is published, then the publish date, indicated by the **[!UICONTROL World]** icon is on the banner along with the last modification date, indicated by the **[!UICONTROL Pencil]** icon displays.

![chlimage_1-133](assets/chlimage_1-339.png)

In de afbeeldingsset kunt u ook stalen maken door een afbeeldingsset te maken en miniaturen toe te voegen.

Deze toepassing is vooral handig wanneer u een item in een andere kleur, in een ander patroon of in een ander patroon wilt weergeven. Als u een afbeeldingsset met kleurstalen wilt maken, hebt u één afbeelding nodig voor elke andere kleur, elk patroon of elke afwerking die u aan de gebruikers wilt presenteren. Voor elke kleur, elk patroon of elke afwerking hebt u ook één kleur-, patroon- of eindstaal nodig.

Stel dat u afbeeldingen van uiteinden met verschillende kleurrekeningen wilt weergeven. de rekeningen zijn rood , groen en blauw . In dit geval hebt u drie opnamen van hetzelfde kapje nodig. Je hebt een opname nodig met een rood, een met een groen en een met een blauwe rekening. U hebt ook een rood, groen en blauw kleurenstaal nodig. De kleurstalen fungeren als de miniaturen die gebruikers in de Staalset-viewer klikken om het rode, groene of blauwe kader met vulling weer te geven.

>[!NOTE]
>
>Zie Elementen [beheren met de aanraakinterface](/help/assets/managing-assets-touch-ui.md)voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Afbeeldingssets {#quick-start-image-sets}

Zo kunt u snel aan de slag:

1. [Upload uw hoofdafbeeldingen voor meerdere weergaven.](#uploading-assets-in-image-sets)

   Begin door de beelden voor uw Reeksen van het Beeld te uploaden. Omdat gebruikers kunnen inzoomen op afbeeldingen in de Vastgestelde Kijker van het Beeld, houd rekening met het zoemen wanneer u beelden kiest. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn voor optimale zoomdetails. Met dynamische media kunnen afbeeldingen tot 25 megapixels worden gerenderd. U kunt bijvoorbeeld een afbeelding van 5000 x 5000 megapixel of een andere formaatcombinatie van maximaal 25 megapixels gebruiken.

   AEM-elementen ondersteunen een groot aantal bestandsindelingen voor afbeeldingen, maar het wordt aanbevolen afbeeldingen zonder verlies in de indeling TIFF, PNG en EPS te gebruiken.

1. [Afbeeldingssets maken.](#creating-image-sets)

   In de Reeksen van het Beeld, klikken de gebruikers duimnagelbeelden in de Vastgestelde Kijker van het Beeld.

   Tik of klik op **[!UICONTROL Maken > Afbeeldingssets]** om een Afbeeldingsset in elementen te maken. Voeg vervolgens afbeeldingen toe en klik op **[!UICONTROL Opslaan]**.

   You can also create image sets automatically through [batch set presets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   >[!IMPORTANT]
   >
   >De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen en zijn beschikbaar slechts op Dynamische Media - wijze Scene7.

   Zie [Afbeeldingsset-elementen voorbereiden voor het uploaden en uploaden van uw bestanden](#uploading-assets-in-image-sets).

   See [Working with Selectors.](/help/assets/working-with-selectors.md)

1. Voeg desgewenst voorinstellingen voor de [afbeeldingsset Viewer](/help/assets/managing-viewer-presets.md)toe.

   Beheerders kunnen voorinstellingen voor de afbeeldingsset Viewer maken of wijzigen. To see your image set with a viewer preset, select the image set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   Zie **[!UICONTROL Gereedschappen > Middelen > Voorinstellingen]** viewer om voorinstellingen voor viewers te maken of te bewerken.

1. (Optioneel) [Afbeeldingssets](/help/assets/image-sets.md#viewing-image-sets) weergeven die zijn gemaakt met voorinstellingen voor batchsets.
1. [Voorvertoning van afbeeldingssets.](/help/assets/previewing-assets.md)

   Selecteer de Afbeeldingsset en u kunt er een voorvertoning van weergeven. Klik op de miniatuurpictogrammen om de Afbeeldingsset in de geselecteerde viewer te bekijken. U kunt verschillende viewers kiezen in het menu **[!UICONTROL Viewers]** , beschikbaar in het keuzemenu voor de linkertrack.

1. [Afbeeldingssets publiceren.](/help/assets/publishing-dynamicmedia-assets.md)

   Als u een Afbeeldingsset publiceert, wordt de URL- en insluitreeks geactiveerd. Bovendien moet u een aangepaste viewer-voorinstelling [die u hebt gemaakt,](/help/assets/managing-viewer-presets.md) publiceren. Voorinstellingen voor viewers buiten de box zijn al gepubliceerd.

1. [Koppel URL&#39;s aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md) of [sluit de video- of afbeeldingsviewer](/help/assets/embed-code.md)in.

   AEM Assets leidt tot URL vraag naar de Reeksen van het Beeld en activeert hen nadat u de beeldreeksen publiceert. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Select the Image Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   Zie [Een afbeeldingset koppelen aan een webpagina](/help/assets/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/embed-code.md).

Zie Afbeeldingssets [bewerken als u Afbeeldingssets wilt bewerken.](#editing-image-sets) Bovendien kunt u de eigenschappen [van de](/help/assets/managing-assets-touch-ui.md#editing-properties)Afbeeldingsset weergeven en bewerken.

Als u kwesties creeert reeksen hebt, zie Beelden en Reeksen op het Oplossen van [Problemen Dynamische Media - wijze](/help/assets/troubleshoot-dms7.md#images-and-sets)Scene7.

## Elementen uploaden in afbeeldingssets {#uploading-assets-in-image-sets}

Begin door de beelden voor uw Reeksen van het Beeld te uploaden. Omdat gebruikers kunnen inzoomen op afbeeldingen in de Vastgestelde Kijker van het Beeld, houd rekening met het zoemen wanneer u beelden kiest. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn in de grootste dimensie. Afbeeldingssets ondersteunen veel bestandsindelingen voor afbeeldingen, maar afbeeldingen zonder verlies van de indeling TIFF, PNG en EPS worden aanbevolen.

U kunt afbeeldingen voor Afbeeldingssets uploaden zoals u elk ander element in Elementen [zou](/help/assets/managing-assets-touch-ui.md#uploading-assets)uploaden.

### Afbeeldingsset-elementen voorbereiden voor uploaden {#preparing-image-set-assets-for-upload}

Voordat u Afbeeldingssets maakt, moet u ervoor zorgen dat de afbeeldingen de juiste grootte en indeling hebben.

Als u een Afbeeldingsset met meerdere weergaven wilt maken, hebt u afbeeldingen nodig die een item vanuit verschillende gezichtspunten weergeven of verschillende aspecten van hetzelfde item weergeven. Het doel is om de belangrijke kenmerken van een item te benadrukken, zodat gebruikers een volledig beeld hebben van hoe het eruit ziet of werkt.

Omdat gebruikers kunnen inzoomen op afbeeldingen in Afbeeldingssets, moet u ervoor zorgen dat de afbeeldingen ten minste 2000 pixels groot zijn. Elementen ondersteunen veel bestandsindelingen voor afbeeldingen, maar TIFF-, PNG- en EPS-afbeeldingen zonder gegevensverlies worden aanbevolen.

>[!NOTE]
>
>Als u miniaturen gebruikt om productstalen aan te geven, moet u het volgende doen:
>
>U hebt vignetten of verschillende opnamen van dezelfde afbeelding nodig die deze in verschillende kleuren, patronen of afwerkingen weergeven. U hebt ook miniatuurbestanden nodig die overeenkomen met de verschillende kleuren, patronen of afwerkingen. Als u bijvoorbeeld miniaturen wilt weergeven met een Afbeeldingsset die hetzelfde jasje in zwart, bruin en groen toont, hebt u het volgende nodig:
>
>* Een zwarte, bruine en groene opname van hetzelfde jasje.
>* Een zwarte, bruine en groene kleurminiatuur.


## Afbeeldingssets maken {#creating-image-sets}

U kunt Afbeeldingssets maken via de gebruikersinterface of via de API. In deze sectie wordt beschreven hoe u afbeeldingssets maakt in de gebruikersinterface.

>[!NOTE]
>
>You can also create image sets automatically through [batch set presets](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets).
>**Belangrijk:**De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen en zijn beschikbaar slechts op Dynamische Media - wijze Scene7.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

>[!NOTE]
>
>Afbeeldingssets worden niet ondersteund voor elementen met &quot;,&quot; (komma) in de bestandsnaam.

**Een afbeeldingsset maken**

1. In AEM, tap the AEM logo to access the global navigation console, then tap **[!UICONTROL Navigation > Assets]**. Navigate to where you want to create an image set, then tap **[!UICONTROL Create > Image Set]** to open the Image Set Editor page.

   U kunt de set ook maken vanuit een map die uw assets bevat.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Voer op de pagina Editor afbeeldingsset in het veld **[!UICONTROL Titel]** een naam in voor de afbeeldingsset. De naam wordt weergegeven in de banner in de Afbeeldingsset. Voer eventueel een beschrijving in.

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. Voer een van de volgende handelingen uit:

   * Tik in de linkerbovenhoek van de pagina Editor afbeeldingsset op Element **[!UICONTROL toevoegen]**.

   * Tik in het midden van de pagina Editor afbeeldingsset op **[!UICONTROL Tikken om de Asset Selector]** te openen.
   Tik om elementen te selecteren die u in de afbeeldingsset wilt opnemen. Geselecteerde assets hebben een vinkje. When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Select]**.

   With the Asset Selector, you can search for assets by typing in a keyword and tapping or clicking **[!UICONTROL Return]**. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Select the filter and then tap the **[!UICONTROL Filter]** icon on the toolbar. Wijzig de weergave door op het pictogram Weergave te tikken en **[!UICONTROL Kolomweergave]**, **[!UICONTROL Kaartweergave]** of **[!UICONTROL Lijstweergave]** te selecteren.

   See [Working with Selectors.](/help/assets/working-with-selectors.md)

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw ordenen of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Als u een miniatuur of staal wilt wijzigen, klikt u op het pictogram **+** **miniatuur** naast de afbeelding en gaat u naar de gewenste miniatuur of staal. When done selecting all the images click **[!UICONTROL Save]**.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en tikt u op Element **** verwijderen.

   * To apply a preset, near the upper-right corner of the page, tap **[!UICONTROL Preset]**, then select a preset to apply to all the assets at once.
   >[!NOTE]
   >
   >Wanneer u de afbeeldingset maakt, kunt u de miniatuur van de afbeeldingset wijzigen of AEM toestaan de miniatuur automatisch te selecteren op basis van de assets in de afbeeldingset. To select a thumbnail, tap **[!UICONTROL Change thumbnail]** above the Title field on the Image Set Editor page, then select any image (you can navigate to other folders to find images as well). If you have selected a thumbnail and then decide that you want AEM to generate one from the image set, select **[!UICONTROL Switch to]** **[!UICONTROL Automatic thumbnail]**.

1. Click **[!UICONTROL Save]**. De nieuwe afbeeldingsset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Afbeeldingssets weergeven {#viewing-image-sets}

U kunt afbeeldingssets maken in de gebruikersinterface of u kunt automatisch [batchvoorinstellingen](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets)gebruiken.

>[!IMPORTANT]
>
>De reeksen van de partij worden gecreeerd door het IPS Systeem [van de Productie van het] Beeld als deel van activa opnemen en zijn beschikbaar slechts op Dynamische Media - wijze Scene7.)

Set die is gemaakt met voorinstellingen voor batchsets, wordt echter *niet* weergegeven in de gebruikersinterface. U kunt deze sets op drie verschillende manieren weergeven. (Deze methoden zijn ook beschikbaar als u de afbeeldingssets in de gebruikersinterface hebt gemaakt.)

* Open de eigenschappen van een afzonderlijk element. Eigenschappen geven aan naar welke sets van het geselecteerde element wordt verwezen of een lid van. Klik op de naam van de set om de volledige set weer te geven.

   ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties2.png)

* Van een lidafbeelding van om het even welke set. Selecteer het menu **[!UICONTROL Sets]** om de sets weer te geven waarvan de asset lid is.

   ![6_5_imageset-set-pushDownmenu](assets/6_5_imageset-setspulldownmenu.png)

* From search, you can select **[!UICONTROL Filter**, then expand **[!UICONTROL Dynamic Media** and select **[!UICONTROL Sets]**.

   De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde reeksen, wordt de onderzoeksvraag geleid gebruikend &quot;Begint met&quot;onderzoekscriteria die van het onderzoek AEM verschillend zijn die op het gebruiken van &quot;bevat&quot;onderzoekscriteria gebaseerd is. Het instellen van het filter op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde sets te doorzoeken.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>U kunt sets weergeven in de gebruikersinterface, zoals wordt beschreven in Afbeeldingssets [](#editing-image-sets)bewerken.

## Afbeeldingssets bewerken {#editing-image-sets}

U kunt diverse bewerkingstaken uitvoeren op Afbeeldingssets, zoals:

* Voeg afbeeldingen toe aan de Afbeeldingsset.
* Wijzig de volgorde van de afbeeldingen in de set Afbeeldingen.
* Elementen in de afbeeldingsset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de afbeeldingsset.

**Afbeeldingssets bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een afbeeldingsset en tik op **[!UICONTROL Bewerken]** (potloodpictogram).
   * Houd de muisaanwijzer boven een afbeeldingsset, tik op **[!UICONTROL Selecteren]** (vinkpictogram) en tik vervolgens op **[!UICONTROL Bewerken]** op de werkbalk.
   * Tik op een afbeeldingsset en tik vervolgens op **[!UICONTROL Bewerken]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de afbeeldingen in de Afbeeldingsset te bewerken:

   * Als u elementen opnieuw wilt rangschikken, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor opnieuw ordenen om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, klikt u op de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, klikt u op Element **[!UICONTROL toevoegen]**. Navigeer naar een element, selecteer het en tik op **[!UICONTROL Selecteren]** in de rechterbovenhoek van de pagina.
      >[!NOTE]
      >
      >Als u de afbeelding verwijdert die AEM voor de miniatuur gebruikt door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en tikt u erop of klikt u op Element **** verwijderen.
   * To apply a preset, near the upper-right corner of the page, tap **[!UICONTROL Preset]**, then select a viewer preset.
   * Als u een miniatuur wilt toevoegen of wijzigen, selecteert u het miniatuurpictogram rechts van het element. Navigeer naar de nieuwe miniatuur of het nieuwe stalenelement, selecteer het en tik op **[!UICONTROL Selecteren]**.
   * Als u een hele afbeeldingsset wilt verwijderen, navigeert u naar de afbeeldingsset, selecteert u deze en tikt u op **[!UICONTROL Verwijderen]**.
   >[!NOTE]
   >
   >You can edit the images in an Image Set by navigating to the set, tap **[!UICONTROL Set Members]** in the left rail, and then tap the Pencil icon on an individual asset to open the editing window.

1. Tik op **[!UICONTROL Opslaan]** als u klaar bent met bewerken.

## Voorvertoning van afbeeldingssets {#previewing-image-sets}

Zie [Voorvertoning van elementen](/help/assets/previewing-assets.md)weergeven.

## Afbeeldingssets publiceren {#publishing-image-sets}

Zie Elementen [](/help/assets/publishing-dynamicmedia-assets.md)publiceren.
