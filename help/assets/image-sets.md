---
title: Afbeeldingssets
description: Leer hoe u met Afbeeldingssets werkt in Dynamic Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: Image Sets,Asset Management
role: User, Admin
exl-id: 2a536745-fa13-4158-8761-2ac5b6e1893e
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2207'
ht-degree: 4%

---

# Afbeeldingssets {#image-sets}

Afbeeldingssets bieden gebruikers een geïntegreerde weergave, waarbij gebruikers verschillende weergaven van een item kunnen zien door een miniatuurafbeelding te selecteren. Met Afbeeldingssets kunt u alternatieve weergaven van een item presenteren en de viewer beschikt over zoomgereedschappen waarmee u afbeeldingen op de juiste wijze kunt bekijken.

Afbeeldingssets worden aangeduid door een banner met het woord `IMAGESET`. Als de afbeeldingset wordt gepubliceerd, wordt bovendien de publicatiedatum, die door het pictogram **[!UICONTROL World]** wordt aangegeven, samen met de laatste wijzigingsdatum op de banner weergegeven. Dit wordt aangegeven door het pictogram **[!UICONTROL Pencil]**.

![Afbeeldingsset](assets/chlimage_1-339.png)

In de Afbeeldingsset kunt u ook stalen maken door een Afbeeldingsset te maken en miniaturen toe te voegen.

Deze toepassing is handig wanneer u een item in een andere kleur, in een ander patroon of in een ander patroon wilt weergeven. Als u een afbeeldingsset met kleurstalen wilt maken, hebt u één afbeelding nodig voor elke andere kleur, elk patroon of elke afwerking die u aan de gebruikers wilt presenteren. Voor elke kleur, elk patroon of elke afwerking hebt u ook één kleur-, patroon- of eindstaal nodig.

Stel dat u afbeeldingen van uiteinden met verschillende kleurrekeningen wilt weergeven. De rekeningen zijn rood, groen en blauw. In dit geval hebt u drie opnamen van hetzelfde kapje nodig. Je hebt een opname nodig met een rood, een met een groen en een met een blauwe rekening. U hebt ook een rood, groen en blauw kleurenstaal nodig. De kleurstalen fungeren als de miniaturen die gebruikers in de Staalset-viewer selecteren om de rode, groene of blauwe rechthoek te zien.

>[!NOTE]
>
>Voor informatie over de gebruikersinterface van Middelen raadpleegt u [Elementen beheren](/help/assets/manage-assets.md).

Wanneer u een Reeks van het Beeld creeert, beveelt de Adobe de volgende beste praktijken aan en handhaaft de volgende grenzen:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Aantal dubbele elementen per set | Geen duplicaten | 20‡ |
| Maximumaantal afbeeldingen per set | 5-10 afbeeldingen per set | 1000 |

‡ De beste manier is om geen dubbele elementen in een set te hebben. De limiet is 20 duplicaten voor één element. Als u nog een duplicaat voor dat element toevoegt (binnen die set), geeft de aanvraag een fout of wordt het duplicaat genegeerd.

Zie ook [Dynamic Media-beperkingen](/help/assets/limitations.md).

## Snel starten: Afbeeldingssets {#quick-start-image-sets}

**Zo kunt u snel aan de slag:**

1. [Upload uw primaire bronafbeeldingen voor meerdere weergaven](#uploading-assets-in-image-sets).

   Begin door de beelden voor uw Reeksen van het Beeld te uploaden. Wanneer u afbeeldingen kiest, moet u niet vergeten dat uw klanten op afbeeldingen kunnen zoomen in de viewer voor de afbeeldingsset. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn voor optimale zoomdetails. Dynamic Media kan afbeeldingen renderen tot 25 MP (megapixels). U kunt bijvoorbeeld een afbeelding van 5000 x 5000 MP of een andere formaatcombinatie van maximaal 25 MP gebruiken.

   Zie [Dynamic Media - Ondersteunde rasterafbeeldingsindelingen](/help/assets/assets-formats.md#supported-raster-image-formats-dynamic-media) voor een lijst met indelingen die worden ondersteund door Afbeeldingssets.

<!--    Adobe Experience Manager Assets supports many image file formats, but lossless TIFF, PNG, and EPS images are recommended. -->

1. [Een afbeeldingsset maken](#creating-image-sets).

   In de Reeksen van het Beeld, selecteren de gebruikers duimnagelbeelden in de Vastgestelde Kijker van het Beeld.

   Als u een Afbeeldingsset in elementen wilt maken, gaat u naar **[!UICONTROL Create]** > **[!UICONTROL Image Sets]**. Voeg vervolgens afbeeldingen toe en selecteer **[!UICONTROL Save]**.

   U kunt ook automatisch afbeeldingssets maken via [voorinstellingen voor batchsets](/help/assets/config-dms7.md).
   >[!IMPORTANT]
   >
   >Batchsets worden gemaakt door het IPS (Image Production System) als onderdeel van het opnemen van elementen en zijn alleen beschikbaar in de Dynamic Media-Scene7-modus.

   Zie [Afbeeldingssets voorbereiden voor het uploaden en uploaden van uw bestanden](#uploading-assets-in-image-sets).

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md).

1. Toevoegen [Voorinstellingen voor Afbeeldingsset viewer](/help/assets/managing-viewer-presets.md), indien nodig.

   Beheerders kunnen voorinstellingen voor de afbeeldingsset Viewer maken of wijzigen. Als u de Afbeeldingsset wilt weergeven met een viewervoorinstelling, selecteert u de Afbeeldingsset en selecteert u in de vervolgkeuzelijst voor de linkertrack de optie **[!UICONTROL Viewers]**.

   Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** als u voorinstellingen voor viewers wilt maken of bewerken.

1. (Optioneel) [Een afbeeldingsset weergeven](/help/assets/image-sets.md#viewing-image-sets) die zijn gemaakt met behulp van voorinstellingen voor batchsets.
1. [Voorvertoning van afbeeldingssets](/help/assets/previewing-assets.md).

   Selecteer de Afbeeldingsset en u kunt er een voorvertoning van weergeven. Selecteer de miniatuurpictogrammen zodat u de Afbeeldingsset kunt bekijken in de geselecteerde viewer. U kunt verschillende viewers kiezen in het menu **[!UICONTROL Viewers]** beschikbaar via het keuzemenu voor de linkertrack.

1. [Een afbeeldingsset publiceren](/help/assets/publishing-dynamicmedia-assets.md).

   Als u een Afbeeldingsset publiceert, wordt de URL geactiveerd en wordt de code ingesloten. Bovendien moet u [een aangepaste viewervoorinstelling publiceren](/help/assets/managing-viewer-presets.md) die u hebt gemaakt. Voorinstellingen voor viewers buiten de box zijn al gepubliceerd.

1. [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md) of [De video- of afbeeldingsviewer insluiten](/help/assets/embed-code.md).

   Experience Manager Assets maakt URL-aanroepen voor afbeeldingssets en activeert deze nadat u de afbeeldingssets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de Afbeeldingset en selecteer vervolgens in de vervolgkeuzelijst voor het linkerspoor **[!UICONTROL Viewers]**.

   Zie [Een Afbeeldingsset koppelen aan een webpagina](/help/assets/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/embed-code.md).

Zie voor informatie over het bewerken van afbeeldingssets [Afbeeldingssets bewerken](#editing-image-sets). Bovendien kunt u [Eigenschappen van Afbeeldingsset](/help/assets/manage-assets.md#editing-properties).

Als u problemen ondervindt bij het maken van sets, raadpleegt u Afbeeldingen en sets in [Problemen oplossen in de modus Dynamic Media - Scene7](/help/assets/troubleshoot-dms7.md#images-and-sets).

## Elementen uploaden in afbeeldingssets {#uploading-assets-in-image-sets}

Begin door de beelden voor uw Reeksen van het Beeld te uploaden. Wanneer u afbeeldingen kiest, moet u niet vergeten dat uw klanten op afbeeldingen kunnen zoomen in de viewer voor de afbeeldingsset. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn. Afbeeldingssets ondersteunen veel indelingen voor afbeeldingsbestanden, maar afbeeldingen zonder verlies van de indelingen TIFF, PNG en EPS worden aanbevolen.

U kunt afbeeldingen voor afbeeldingssets uploaden zoals u dat zou doen [andere elementen in Elementen uploaden](/help/assets/manage-assets.md#uploading-assets).

Zie [Dynamic Media - Ondersteunde rasterafbeeldingsindelingen](/help/assets/assets-formats.md#supported-raster-image-formats-dynamic-media) voor een lijst met indelingen die worden ondersteund door Afbeeldingssets.

### Afbeeldingsset-elementen voorbereiden voor uploaden {#preparing-image-set-assets-for-upload}

Voordat u Afbeeldingssets maakt, moet u ervoor zorgen dat de afbeeldingen de juiste grootte en indeling hebben.

Als u een Afbeeldingsset met meerdere weergaven wilt maken, hebt u afbeeldingen nodig die een item vanuit verschillende gezichtspunten weergeven of verschillende aspecten van hetzelfde item weergeven. Het doel is om de belangrijke kenmerken van een item te benadrukken, zodat gebruikers een volledig beeld hebben van hoe het eruit ziet of werkt.

Omdat gebruikers kunnen inzoomen op afbeeldingen in Afbeeldingssets, moet u ervoor zorgen dat de afbeeldingen ten minste 2000 pixels groot zijn. <!-- Assets support many image file formats, but lossless TIFF, PNG, and EPS images are recommended. -->

>[!NOTE]
>
>Als u miniaturen gebruikt om productstalen aan te geven, moet u het volgende doen:
>
>U hebt vignetten of verschillende opnamen van dezelfde afbeelding nodig die deze in verschillende kleuren, patronen of afwerkingen weergeven. U hebt ook miniatuurbestanden nodig die overeenkomen met de verschillende kleuren, patronen of afwerkingen. Als u bijvoorbeeld miniaturen wilt weergeven met een Afbeeldingsset die hetzelfde jasje in zwart, bruin en groen toont, hebt u het volgende nodig:
>
>* Een zwarte, bruine en groene opname van hetzelfde jasje.
>* Een zwarte, bruine en groene kleurminiatuur.

## Een afbeeldingsset maken {#creating-image-sets}

U kunt Afbeeldingssets maken via de gebruikersinterface of via de API. In deze sectie wordt beschreven hoe u Afbeeldingssets maakt in de gebruikersinterface.

>[!NOTE]
>
>U kunt ook automatisch afbeeldingssets maken via [voorinstellingen voor batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
>**Belangrijk:** Batchsets worden gemaakt door het IPS (Image Production System) als onderdeel van het opnemen van elementen en zijn alleen beschikbaar in de Dynamic Media-Scene7-modus.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

>[!NOTE]
>
>Afbeeldingssets worden niet ondersteund voor elementen met &quot;,&quot; (komma) in de bestandsnaam.

Wanneer u een Reeks van het Beeld creeert, beveelt de Adobe de volgende beste praktijken aan en handhaaft de volgende grenzen:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Aantal dubbele elementen per set | Geen duplicaten | 20‡ |
| Maximumaantal afbeeldingen per set | 5-10 afbeeldingen per set | 1000 |

‡ De beste manier is om geen dubbele elementen in een set te hebben. De limiet is 20 duplicaten voor één element. Als u nog een duplicaat voor dat element toevoegt (binnen die set), geeft de aanvraag een fout of wordt het duplicaat genegeerd.

Zie ook [Dynamic Media-beperkingen](/help/assets/limitations.md).

**Een afbeeldingsset maken:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben, dan ga **[!UICONTROL Navigation]** > **[!UICONTROL Assets]**. Navigeer naar de plaats waar u een Reeks van het Beeld wilt tot stand brengen, dan ga naar **[!UICONTROL Create]** > **[!UICONTROL Image Set]** om de pagina van de Editor van de set Afbeeldingen te openen.

   U kunt de set ook maken vanuit een map die uw elementen bevat.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Op de pagina van de Editor voor de set afbeeldingen, in het dialoogvenster **[!UICONTROL Title]** voert u een naam in voor de Afbeeldingsset. De naam wordt weergegeven in de banner in de Afbeeldingsset. Voer eventueel een beschrijving in.

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. Voer een van de volgende handelingen uit:

   * Selecteer in de linkerbovenhoek van de pagina Editor afbeeldingsset de optie **[!UICONTROL Add Asset]**.

   * Selecteer in het midden van de pagina Editor afbeeldingsset de optie **[!UICONTROL Tap to open Asset Selector]**.

   Selecteer de elementen die u in de afbeeldingsset wilt opnemen. Geselecteerde assets hebben een vinkje. Als u klaar bent, selecteert u in de rechterbovenhoek van de pagina de optie **[!UICONTROL Select]**.

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken of klikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en selecteer vervolgens het filter **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door te tikken op het pictogram Weergave en **[!UICONTROL Column View]**, **[!UICONTROL Card View]** of **[!UICONTROL List View]** te selecteren.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md).

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw rangschikken of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Als u een miniatuur of staal wilt wijzigen, selecteert u de optie **+** **miniatuur** naast de afbeelding en navigeer naar de gewenste miniatuur of staal. Selecteer alle afbeeldingen als u klaar bent **[!UICONTROL Save]**.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en **[!UICONTROL Delete Asset]**.

   * Selecteer **[!UICONTROL Preset]** Selecteer vervolgens een voorinstelling die u op alle elementen tegelijk wilt toepassen.

   >[!NOTE]
   >
   >Wanneer u de Afbeeldingsset maakt, kunt u de miniatuur van de afbeeldingsset wijzigen of Experience Manager toestaan de miniatuur automatisch te selecteren op basis van de elementen in de Afbeeldingsset. Selecteer een miniatuur door **[!UICONTROL Change thumbnail]** boven het veld Titel op de pagina Editor afbeeldingsset selecteert u een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Als u een miniatuur hebt geselecteerd en vervolgens besluit dat Experience Manager een miniatuur moet genereren in de Afbeeldingsset, selecteert u **[!UICONTROL Switch to]** > **[!UICONTROL Automatic thumbnail]**.

1. Selecteer **[!UICONTROL Save]**. De nieuwe afbeeldingsset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Een afbeeldingsset weergeven {#viewing-image-sets}

U kunt afbeeldingssets maken in de gebruikersinterface of automatisch met [voorinstellingen voor batchsets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

>[!IMPORTANT]
>
>De reeksen van de partij worden gecreeerd door IPS [Afbeeldingsproductiesysteem] als onderdeel van het opnemen van activa en zijn alleen beschikbaar in de Dynamic Media-Scene7-modus.)

sets die zijn gemaakt met voorinstellingen voor batchsets, doen *niet* in de gebruikersinterface. U kunt deze sets op drie verschillende manieren weergeven. (Deze methoden zijn beschikbaar, zelfs als u de afbeeldingssets in de gebruikersinterface hebt gemaakt.)

* Open de eigenschappen van een afzonderlijk element. Eigenschappen geven aan naar welke sets van het geselecteerde element wordt verwezen of een lid van. Selecteer de naam van de set als u de volledige set wilt zien.

  ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties2.png)

* Van een lidafbeelding van om het even welke set. Selecteer de **[!UICONTROL Sets]** om de sets weer te geven waarvan het element lid is.

  ![6_5_imageset-set-pushDownmenu](assets/6_5_imageset-setspulldownmenu.png)

* Van onderzoek, kunt u selecteren **[!UICONTROL Filter]** vervolgens uitvouwen **[!UICONTROL Dynamic Media]** en selecteert u **[!UICONTROL Sets]**.

  De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde reeksen, wordt de onderzoeksvraag geleid gebruikend &quot;Begint met&quot;onderzoekscriteria die van het onderzoek van de Experience Manager verschillend zijn die op het gebruiken van &quot;bevat&quot;onderzoekscriteria gebaseerd is. Het filter instellen op **[!UICONTROL Sets]** Dit is de enige manier om geautomatiseerde sets te zoeken.

  ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>U kunt sets weergeven in de gebruikersinterface zoals beschreven in [Afbeeldingssets bewerken](#editing-image-sets).

## Een afbeeldingsset bewerken {#editing-image-sets}

U kunt verschillende bewerkingstaken uitvoeren op Afbeeldingssets, zoals:

* Voeg afbeeldingen toe aan de Afbeeldingsset.
* Wijzig de volgorde van de afbeeldingen in de afbeeldingsset.
* Elementen in de afbeeldingsset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de afbeeldingsset.

**Een afbeeldingsset bewerken:**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een afbeeldingsset-element en selecteer **[!UICONTROL Edit]** (potloodpictogram).
   * Als u de cursor op een afbeeldingsset plaatst, selecteert u **[!UICONTROL Select]** (vinkje pictogram), selecteer dan **[!UICONTROL Edit]** op de werkbalk.
   * Selecteer een afbeeldingsset en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de afbeeldingen in de Afbeeldingsset te bewerken:

   * Als u elementen opnieuw wilt rangschikken, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor opnieuw ordenen om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, selecteert u de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, selecteert u de optie **[!UICONTROL Add Asset]**. Navigeer naar een element, selecteer het en selecteer het **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.
     >[!NOTE]
     >
     >Als u de afbeelding verwijdert die de Experience Manager voor de miniatuur gebruikt door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en selecteert u het **[!UICONTROL Delete Asset]**.
   * Selecteer **[!UICONTROL Preset]** selecteert u vervolgens een viewervoorinstelling.
   * Als u een miniatuur wilt toevoegen of wijzigen, selecteert u het miniatuurpictogram rechts van het element. Navigeer naar de nieuwe miniatuur of het nieuwe stalenelement, selecteer het en selecteer het **[!UICONTROL Select]**.
   * Als u een hele afbeeldingsset wilt verwijderen, navigeert u naar de afbeeldingsset, selecteert u deze en selecteert u **[!UICONTROL Delete]**.

   >[!NOTE]
   >
   >U kunt de afbeeldingen in een set afbeeldingen bewerken door naar de set te navigeren. Selecteer **[!UICONTROL Set Members]** in het linkerspoor, en selecteer dan het pictogram van het Potlood op een individueel middel om het het uitgeven venster te openen.

1. Selecteren **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

## Een voorvertoning van een afbeeldingsset weergeven {#previewing-image-sets}

Zie [Elementen voorvertonen](/help/assets/previewing-assets.md).

## Een afbeeldingsset publiceren {#publishing-image-sets}

Zie [Middelen publiceren](/help/assets/publishing-dynamicmedia-assets.md).
