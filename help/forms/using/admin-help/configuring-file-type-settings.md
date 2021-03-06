---
title: Instellingen voor bestandstypen configureren
seo-title: Instellingen voor bestandstypen configureren
description: Leer hoe u instellingen voor bestandstypen configureert.
seo-description: Leer hoe u instellingen voor bestandstypen configureert.
uuid: ab037659-c6ff-4de9-9417-f5a6fc8122cb
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
discoiquuid: ab19b248-8931-4cf6-b6a5-fb7b067c4a49
feature: PDF Generator
translation-type: tm+mt
source-git-commit: 3bb12f6323398971ec315f49611a39977bd548a2
workflow-type: tm+mt
source-wordcount: '5874'
ht-degree: 1%

---


# Instellingen voor bestandstypen configureren {#configuring-file-type-settings}

In PDF Generator, kunt u de toepassingsmontages voor gesteunde dossiertypes plaatsen. In Windows kunt u de toepassingsinstellingen voor elk ondersteund bestandstype instellen. In UNIX en Linux kunt u de toepassingsinstellingen voor HTML-naar-PDF en OpenOffice instellen.

Op de pagina Instellingen bestandstype kunt u de volgende taken uitvoeren:

* [Een instelling voor bestandstypen maken of bewerken](#create-or-edit-file-type-settings)
* Geef op welke bestandstypen standaard moeten worden gebruikt (zie [Configuratiebestanden van PDF Generator importeren en exporteren](/help/forms/using/admin-help/importing-exporting-pdf-generator-configuration.md))
* [De standaardinstellingen wijzigen](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings)
* [PDF/A-ondersteuning inschakelen](/help/forms/using/admin-help/enable-pdf-a-support.md)
* [Een instelling voor Bestandstypen verwijderen](/help/forms/using/admin-help/enable-pdf-a-support.md)

>[!NOTE]
>
>De instellingen voor bestandstypen zijn niet beschikbaar voor de fallback-convertors, zoals Acrobat voor HTML-conversie naar PDF, Microsoft PowerPoint, Microsoft Word en Microsoft Excel.

## Instellingen voor bestandstypen maken of bewerken {#create-or-edit-file-type-settings}

Maak of bewerk een bestandstype-instelling om op te geven hoe de toepassing omgaat met de conversie van ondersteunde bestandstypen. In Windows kunt u de toepassingsinstellingen voor elk ondersteund bestandstype instellen. In UNIX en Linux kunt u de toepassingsinstellingen voor HTML-naar-PDF en OpenOffice instellen.

1. Klik in de beheerconsole op **[!UICONTROL Services]** > **[!UICONTROL PDF Generator]** > **[!UICONTROL File Type Settings]**.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Typ in het vak Bestandsnaamextensies de bestandsextensies, gescheiden door komma&#39;s, voor de bestandstypen die voor deze toepassing zijn geaccepteerd. Neem de punt voor of geen ruimte op tussen de extensies. De standaardwaarde is `bmp,gif,jpeg,jpg,tif,tiff,png`.
1. (Optioneel) Als u OCR (optische codeherkenning) wilt gebruiken voor tekst in afbeeldingen of afbeeldingen, selecteert u OCR gebruiken en stelt u de volgende opties in:

**Primaire OCR-taal:** de taal die de OCR-engine moet gebruiken om de tekens te identificeren. De standaardwaarde is Engels (VS).

**PDF-uitvoerstijl:** Selecteer Doorzoekbare afbeelding als u een bitmapafbeelding wilt maken van de pagina&#39;s op de voorgrond en de gescande tekst op een onzichtbare laag eronder. De weergave van de pagina verandert niet, maar de tekst wordt selecteerbaar en leesbaar. Selecteer Opgemaakte tekst en afbeeldingen om de originele pagina samen te stellen met herkende tekst, lettertypen, afbeeldingen en andere grafische elementen. De standaardinstelling is Doorzoekbare afbeelding (exact).

**Afbeeldingen downsamplen:** Hiermee verkleint u het aantal pixels in kleuren-, grijswaarden- en monochrome afbeeldingen. De downsampling van gescande afbeeldingen wordt uitgevoerd nadat de OCR is voltooid. De standaardwaarde is Laagste (600 dpi). Deze optie is niet beschikbaar als u de PDF-uitvoerstijl instelt op Doorzoekbare afbeelding (exact).

1. Voer de vereiste informatie in deze secties in:

   [PDF Generator-configuratiebestanden importeren en exporteren](/help/forms/using/admin-help/importing-exporting-pdf-generator-configuration.md)

   [Adobe PDF-exportinstellingen (alleen Windows)](#adobe-pdf-export-settings-windows-only)

   [HTML-naar-PDF-instellingen](#html-to-pdf-settings)

   [Video&#39;s Flash naar PDF-instellingen](#flash-videos-to-pdf-settings)

   [XPS naar PDF-instellingen](#xps-to-pdf-settings)

   [Instellingen voor PDF optimaliseren](/help/forms/using/admin-help/configuring-file-type-settings.md)

   [Microsoft Excel-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-excel-settings-windows-only)

   [Microsoft PowerPoint-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-powerpoint-settings-windows-only)

   [Microsoft Project-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-project-settings-windows-only)

   [Microsoft Word-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-word-settings-windows-only)

   [Microsoft Visio-instellingen (alleen Windows)](#visio)

   [Microsoft Publisher-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-publisher-settings-windows-only)

   [AutoCAD-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#autocad-settings-windows-only)

   [OpenOffice-instellingen](/help/forms/using/admin-help/configuring-file-type-settings.md#openoffice-settings)

   [Instellingen van andere toepassingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#other-applications-settings-windows-only)

   Als u naar een andere sectie wilt gaan, klikt u op de koppeling op de webpagina of gebruikt u de knoppen **[!UICONTROL Next]** of **[!UICONTROL Previous]**.

1. Nadat u alle secties voltooit, klik **[!UICONTROL Save]** of **[!UICONTROL Save As]** en ga een naam voor het plaatsen in.

Ondersteuning voor verschillende bestandstypen kan worden aangepast. (Zie &quot; [Ondersteuning toevoegen voor extra eigen bestandsindelingen](https://help.adobe.com/en_US/AEMForms/6.1/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-7756.2.html)&quot; in [Programmeren met AEM formulieren](https://www.adobe.com/go/learn_lc_programming_11).)

## De standaardinstellingen wijzigen {#change-the-default-settings}

U kunt de standaardwaarde wijzigen voor de Adobe PDF-instellingen, beveiligingsinstellingen en bestandstypen die van toepassing zijn op nieuwe bronnen. Het wijzigen van de standaardinstellingen heeft geen invloed op de instellingen van bestaande bronnen.

1. Klik in Beheerconsole op **[!UICONTROL Services > PDF Generator]**.
1. Op **[!UICONTROL Adobe PDF Settings]**, **[!UICONTROL File Type Settings]**, of **[!UICONTROL Security Settings]** pagina, klik **[!UICONTROL Set Default Settings]**.
1. Selecteer de gewenste standaardinstellingen. Een of meer van de volgende instellingen zijn beschikbaar op de pagina Standaardinstellingen instellen:

   **[!UICONTROL Adobe PDF Setting]**: De oorspronkelijke standaardinstelling is Standaard (Acrobat 6).

   **[!UICONTROL Security Settings]**: De oorspronkelijke standaardinstelling is Geen beveiliging (Acrobat 5).

   **[!UICONTROL File Type Settings]**: De oorspronkelijke standaardinstelling is Standaard.

1. Klik op **[!UICONTROL Save]**.

## Een instelling voor het bestandstype verwijderen {#delete-a-file-type-setting}

U kunt een bestandstype-instelling verwijderen die niet meer wordt gebruikt.

1. Klik in de beheerconsole op **[!UICONTROL Services > PDF Generator> File Type Settings]**.
1. Schakel het selectievakje naast de instelling die u wilt verwijderen in. U kunt meerdere bronnen selecteren. Instellingen zonder selectievakje worden altijd opgenomen in de PDF-Generator en kunnen niet worden verwijderd.
1. Klik **[!UICONTROL Delete]** en, op de Schrappingspagina van de Bevestiging van de Schrapping, klik **[!UICONTROL Delete]**.

## Afbeelding naar PDF-instellingen {#image-to-pdf-settings}

De volgende opties bepalen hoe afbeeldingsbestanden naar PDF worden geconverteerd. Zie [Bestandstype-instellingen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het openen van deze instellingen.

**Bestandsnaamextensies:lijst met bestandsextensies die door** komma&#39;s kunnen worden geconverteerd.

**Probeer Converter fallback:** PDF Generator kan Java??? of Acrobat gebruiken om afbeeldingsbestanden te converteren naar PDF. Als deze optie is geselecteerd en een conversie mislukt of de opgegeven time-outlimiet bereikt, probeert de PDF Generator de conversie met de alternatieve methode uit te voeren. Als de alternatieve methode mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

>[!NOTE]
>
>JPEG 2000-bestanden kunnen alleen worden geconverteerd met Acrobat.

**OCR gebruiken:** geeft aan of OCR (optische tekenherkenning) op de PDF moet worden toegepast. Met de OCR-software kunt u de tekst in de PDF zoeken, corrigeren en kopi??ren.

***opmerking **: De functie OCR PDF (doorzoekbare PDF) wordt alleen ondersteund in Microsoft Windows.*

**Primaire OCR-taal:** geeft de taal op die de OCR-engine moet gebruiken om de tekens te identificeren.

**PDF-uitvoerstijl:** bepaalt het type PDF dat wordt geproduceerd. Bij alle indelingen worden OCR en font- en paginaherkenning toegepast op tekstafbeeldingen en worden deze naar normale tekst omgezet.

**Doorzoekbare afbeelding:** zorgt dat de tekst doorzoekbaar en selecteerbaar is. Met deze optie behoudt u de oorspronkelijke afbeelding, heft u de afbeelding desgewenst schuin en plaatst u er een onzichtbare tekstlaag overheen. Met de optie Afbeeldingen downsamplen bepaalt u of en in welke mate de afbeelding wordt gedownsampled.

**Doorzoekbare afbeelding (exact):** zorgt dat de tekst doorzoekbaar en selecteerbaar is. Met deze optie behoudt u de oorspronkelijke afbeelding en plaatst u er een onzichtbare tekstlaag overheen. Aanbevolen voor gevallen waarin maximale getrouwheid aan de oorspronkelijke afbeelding vereist is.

**ClearScan:** synchroniseert een nieuw Type 3-font dat het origineel vrijwel benadert en behoudt de pagina-achtergrond door een kopie met lage resolutie te gebruiken.

**Afbeeldingen downsamplen:** Hiermee verkleint u het aantal pixels in kleuren-, grijswaarden- en monochrome afbeeldingen nadat de OCR is voltooid. Kies de mate van downsampling die u wilt toepassen. Hogere opties zorgen voor minder downsampling, waardoor PDF&#39;s met een hogere resolutie ontstaan.

## Adobe PDF-exportinstellingen (alleen Windows) {#adobe-pdf-export-settings-windows-only}

De instelling Bestandstype exporteren in het gedeelte Adobe PDF-exportinstellingen wordt gebruikt voor de conversie van een PDF-bestand naar een andere indeling. De standaardinstelling is HTML 4.01 met CSS (Cascading Style Sheets) 1.0 (*.htm, *.html).

Zie [Bestandstype-instellingen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het benaderen van deze instelling.

## HTML-naar-PDF-instellingen {#html-to-pdf-settings}

De volgende opties bepalen hoe HTML-bestanden naar PDF worden geconverteerd. Zie [Bestandstype-instellingen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

**Probeer Convertor voor alternatieven:** PDF Generator kan Java??? of Acrobat gebruiken om HTML-bestanden naar PDF te converteren. Als deze optie is geselecteerd en een conversie mislukt of de opgegeven time-outlimiet bereikt, probeert de PDF Generator de conversie met de alternatieve methode uit te voeren. Als de alternatieve methode mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Standaardcodering:** stelt de invoercodering van de bestandstekst in via een menu met besturingssystemen en alfabeten. Hiermee wordt de selectie bij Standaardcodering alleen gebruikt als het HTML-bronbestand geen type codering opgeeft.

**Geselecteerde codering forceren:** negeert alle codering die in het HTML-bronbestand is opgegeven en gebruikt de selectie die wordt weergegeven in de optie Standaardcodering.

### Bezig met weergeven van instellingen {#spidering-settings}

*Met* Spinnen kunt u webpagina&#39;s scannen op koppelingen naar andere webpagina&#39;s. Wanneer een koppeling naar een andere webpagina wordt aangetroffen, wordt de doelpagina opgehaald en opgenomen in het PDF-document dat wordt gegenereerd. Schakel deze opties in om het aantal niveaus in te stellen dat moet worden opgehaald en geconverteerd naar PDF:

**Alleen X-niveaus ophalen:** Spinnen en pagina&#39;s met een diepte van het opgegeven niveau omzetten in de URL van de basispagina. Met de waarde 1 wordt alleen de opgegeven URL geconverteerd.

**Volledige site ophalen:** hiermee wordt de gehele site geconverteerd, te beginnen met de opgegeven URL.

**Op hetzelfde pad blijven:** koppelingen die verwijzen naar pagina&#39;s die zich niet op hetzelfde relatieve pad bevinden als de basis-URL, worden niet geconverteerd tijdens het spinnen.

**Op dezelfde server blijven:** Koppelingen die verwijzen naar pagina&#39;s op verschillende servers worden niet geconverteerd tijdens het spinnen. Alleen koppelingen die naar dezelfde server als de opgegeven URL verwijzen, worden geconverteerd.

### Instellingen voor paginaconversie {#page-conversion-settings}

Schakel deze opties in om op te geven hoe de HTML-pagina&#39;s worden geconverteerd. Op basis van het paginaformaat worden de waarden voor breedte, hoogte en marge dienovereenkomstig aangepast.

**Paginaformaat:** Kies een aangepaste waarde en geef de breedte en hoogte op of selecteer vooraf gedefinieerde afmetingen.

**Afdrukstand:** selecteer Staand of Liggend voor het geconverteerde PDF-document.

**Marges:** geeft de marges (Boven, Onder, Links en Rechts) op in het gegenereerde PDF-document.

**Bladwijzers toevoegen aan PDF:bladwijzers** toevoegen aan het PDF-document.

**Schakel Gecodeerde PDF:** sluit codes in het PDF-document in.

**Instellingen voor beginweergave instellen:** Hiermee kunt u documentopties, vensteropties en gebruikersinterfaceopties configureren. Deze instellingen bepalen hoe de inhoud in eerste instantie wordt weergegeven.

### Documentopties {#document-options}

Schakel deze opties in om op te geven hoe de inhoud moet worden weergegeven, hoe pagina&#39;s in het PDF-document moeten worden weergegeven en hoe u het vergrotingsniveau wilt instellen:

**Tonen:** selecteer de deelvensters die u wilt openen in Acrobat wanneer het PDF-document wordt geopend.

**Pagina-indeling:** selecteer het type pagina-indeling voor het PDF-document.

**Vergroting:** kies vooraf ingestelde vergroting voor de aanvankelijke mening van het PDF document of selecteer een douanewaarde. Als u een standaardinstelling kiest, wordt de standaardvergroting voor Acrobat gebruikt.

**Openen naar paginanummer:** Geef het paginanummer op waarop de PDF wordt geopend.

### Vensteropties {#window-options}

Schakel deze opties in om op te geven hoe de grootte en weergave van het venster worden aangepast.

**Vensterformaat als van eerste pagina:** wijzigt de grootte van het Acrobat-venster tot de grootte van de eerste pagina.

**Venster centreren op scherm:** Hiermee opent u het venster in het midden van het scherm.

**Openen in Volledig scherm:** opent het venster in de modus Volledig scherm.

**Tonen:** geeft de documenttitel of bestandsnaam weer in het venster.

### Opties gebruikersinterface {#user-interface-options}

Schakel deze opties in om de weergave van het venster op te geven:

**Menubalk verbergen:** verbergt de menubalk in het PDF-document.

**Werkbalken verbergen:** verbergt de werkbalken in het PDF-document.

**Vensterbalk verbergen:** verbergt de vensterbesturingselementen in het PDF-document.

## Video&#39;s Flash naar PDF-instellingen {#flash-videos-to-pdf-settings}

PDF Generator ondersteunt de mogelijkheid om een video te verzenden voor Adobe Flash (SWF- of FLV-bestand) en een PDF-bestand te maken waarin een video is ingesloten voor Adobe Flash. Voor deze conversie hoeft Adobe Flash Player niet te worden ge??nstalleerd op de formulierserver. Zie [Bestandstype-instellingen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het openen van deze optie.

**Bestandsnaamextensies:lijst met bestandsextensies die door** komma&#39;s kunnen worden geconverteerd.

## XPS naar PDF-instellingen {#xps-to-pdf-settings}

De Specificatie van het Papier van XML (XPS) wordt gebruikt in de Drukkerij van Vensters. Dit is een formaat van Microsoft en kan van om het even welke toepassing van Microsoft Office worden gecreeerd. Met AEM formulieren kunt u XPS-bestanden converteren naar PDF.

**Bestandsnaamextensies:** een door komma&#39;s gescheiden lijst met alle XPS-bestandsnaamextensies die kunnen worden geconverteerd. Er is momenteel ????n indeling: .xps.

## Instellingen voor PDF optimaliseren {#pdf-optimizer-settings}

PDF Generator ondersteunt de mogelijkheid om PDF-bestanden te verkleinen. Of u al deze instellingen gebruikt of slechts een paar instellingen zijn afhankelijk van de manier waarop u de bestanden wilt gebruiken en van de essenti??le eigenschappen die een bestand moet hebben. In de meeste gevallen zijn de standaardinstellingen geschikt voor maximale effici??ntie. U bespaart ruimte door ingesloten lettertypen te verwijderen, afbeeldingen te comprimeren en overbodige items uit de bestanden te verwijderen.

>[!NOTE]
>
>Als u een digitaal ondertekend document optimaliseert, worden de digitale handtekeningen verwijderd en ongeldig gemaakt.

Zie [Bestandstype-instellingen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het benaderen van deze instelling.

**Doel-PDF-versie:** geeft de versie van Acrobat op waarmee de PDF compatibel is.

### Lettertypen {#fonts}

1. Selecteer **Lettertypen.**
1. Kies een van de volgende opties:

   **Insluiten van alle fonts ongedaan maken:** insluiten van alle ingesloten fonts opheffen.

   **Geen lettertypen vrijmaken:** sluit insluiting van lettertypen niet ongedaan.

   **Enkele lettertypen insluiten ongedaan maken:alleen de opgegeven lettertypen** insluiten opheffen. Ga als volgt te werk om de fonts op te geven die u wilt verwijderen uit de insluiting:

   * Selecteer zo nodig een andere map met lettertypen in het vervolgkeuzemenu **Fontbron**. Dit vervolgkeuzemenu bevat de lettertypemappen die zijn opgegeven in **Home > Instellingen > Core System > Core Configurations**.
   * Selecteer een of meer lettertypen in de lijst **Beschikbare lettertypen** en klik op **Toevoegen**. Deze lettertypen worden toegevoegd aan de lijst **Lettertypen voor insluiten ongedaan maken**.
   * Als u de insluiting van bepaalde fonts ongedaan wilt maken die niet op de formulierserver aanwezig zijn, voert u de namen van deze fonts in het tekstvak **Fonts toevoegen aan de insluiting**. Klik **Add**.

   >[!NOTE]
   >
   >*Als u de insluiting van bepaalde lettertypen waarvan de subsets in het document zijn ingesloten, ongedaan wilt maken, plaatst u het plusteken (+) v????r de naam van het lettertype. Bijvoorbeeld &quot;+Helvetica&quot;.*

1. Als u alleen de gebruikte subsets van de ingesloten fonts wilt insluiten, selecteert u **Subset maken van alle ingesloten fonts**.

   >[!NOTE]
   >
   >*Als u deze optie gebruikt in combinatie met het insluiten van bepaalde lettertypen **ongedaan**maken, wordt het insluiten van lettertypen in de lijst **Lettertypen toevoegen aan**niet-ingesloten lijst nog steeds volledig ongedaan gemaakt.*

   >[!NOTE]
   >
   >*Subsets van lettertypen is de techniek waarbij slechts een gedeelte van een lettertype wordt ingesloten. Een fontsubset bevat alleen de tekens die in het document worden gebruikt.*

### Transparantie {#transparency}

Als uw PDF-document illustraties met transparantie bevat, kunt u met de instellingen van PDF optimaliseren de transparantie afvlakken en de bestandsgrootte verkleinen.

>[!NOTE]
>
>Als Acrobat 4.0 en hoger is geselecteerd als de doel-PDF-versie, worden alle transparante objecten afgevlakt. Voor andere Doel-PDF-versies wordt transparantie ondersteund en u kunt de transparantie-instellingen configureren.

Selecteer **Transparantie** om de transparantie-instellingen te configureren tijdens het optimaliseren van PDF-documenten.

**TransparantieniveauHiermee bepaalt u** hoeveel vectorinformatie behouden blijft. Bij een hogere instelling blijven meer vectorobjecten behouden, terwijl bij een lagere instelling meer vectorobjecten worden gerasterd. Met tussenliggende instellingen blijven eenvoudige gebieden in vectorvorm behouden en worden complexe gebieden gerasterd. Selecteer de laagste instelling als u alle illustraties wilt rasteren.

>[!NOTE]
>
>De mate van rastering is afhankelijk van de complexiteit van de pagina en de typen overlappende objecten.

**Lijntekeningen en** tekstresolutie waarop alle objecten, inclusief afbeeldingen, vectorillustraties, tekst en verlopen, worden gerasterd. De ondersteunde waarden zijn 1 pixels per inch (ppi) tot en met 9600 ppi.

>[!NOTE]
>
>De resolutie voor lijnwerk en tekst moet doorgaans worden ingesteld op 600-1200 ppi voor rastering van hoge kwaliteit, vooral bij tekst met schreef of kleine puntgrootten.

**Verloop en** resolutie waarop verloop en netten worden gerasterd. De ondersteunde waarden zijn 1 ppi tot en met 1200 ppi.

>[!NOTE]
>
>Verloop- en netresolutie moet doorgaans worden ingesteld op 150-300 ppi, omdat de kwaliteit van de verlopen, slagschaduwen en doezelaars niet verbetert bij hogere resoluties, maar doordat de afdruktijd en de bestandsgrootte toenemen.

**Alle tekst omzetten in** contourenHiermee worden alle tekstobjecten (punttekst, vlaktekst en padtekst) omgezet in contouren en wordt alle informatie over tekstglyphs op pagina&#39;s met transparantie genegeerd. Met deze optie blijft de breedte van tekst tijdens het afvlakken consistent. Houd er rekening mee dat kleine lettertypen hierdoor iets dikker worden weergegeven in Acrobat of worden afgedrukt op desktopprinters met een lage resolutie. Dit heeft geen invloed op de kwaliteit van de tekst die wordt afgedrukt op printers of imagesetters met hoge resolutie.

**Alle lijnen converteren naar** contourenHiermee worden alle lijnen omgezet in eenvoudige gevulde paden op pagina&#39;s met transparantie. Met deze optie blijft de breedte van lijnen tijdens het afvlakken consistent. Houd er rekening mee dat dunne lijnen hierdoor iets dikker worden weergegeven en dat de prestaties van de afvlakking kunnen afnemen.

**Complexe** gebieden knippenHiermee zorgt u ervoor dat de grenzen tussen vectorillustraties en gerasterde illustraties langs objectpaden vallen. Met deze optie worden stitching-artefacten verminderd die ontstaan wanneer ze deel uitmaken van een logboek

<!--
NOTE to WRITER: Unfinished sentence above.
-->

>[!NOTE]
>
>Sommige printerstuurprogramma&#39;s verwerken raster- en vectorillustraties op een andere manier, wat soms tot kleurstitching leidt. U kunt het stitching problemen kunnen minimaliseren door sommige druk-bestuurder specifieke montages van het kleurenbeheer onbruikbaar te maken. Deze instellingen vari??ren per printer. Raadpleeg de documentatie bij de printer voor meer informatie.

Overdruk behouden: Hiermee voegt u de kleur van transparante illustraties samen met de achtergrondkleur om een overdrukeffect te cre??ren.

In de volgende tabel ziet u de meestgebruikte printertypen en de resolutie van deze printers in dpi, de standaard rasterliniatuur in regels per inch (lpi) en een resamplingresolutie voor afbeeldingen in pixels per inch (ppi). Als u bijvoorbeeld afdrukt op een 600-dpi laserprinter, voert u 170 in voor de resolutie waarmee u het aantal pixels in afbeeldingen wilt wijzigen.

**** AfbeeldingenSelecteer Afbeeldingen om opties voor compressie en resampling op te geven voor kleuren-, grijswaarden- en monochrome afbeeldingen. U kunt met deze opties experimenteren om een juiste balans te vinden tussen bestandsgrootte en afbeeldingskwaliteit. De resolutie-instelling voor kleuren- en grijswaardenafbeeldingen moet 1,5 tot 2 keer zo hoog zijn als de rasterliniatuur waarop het bestand wordt afgedrukt. De resolutie voor monochrome afbeeldingen moet gelijk zijn aan die van het uitvoerapparaat, maar houd er rekening mee dat als u een monochrome afbeelding opslaat met een resolutie hoger dan 1500 dpi, het bestand groter wordt zonder dat de beeldkwaliteit merkbaar toeneemt. Voor afbeeldingen die worden vergroot, zoals kaarten, is mogelijk een hogere resolutie vereist.

>[!NOTE]
>
>Het berekenen van nieuwe beeldpixels in monochrome afbeeldingen kan onverwachte weergaveresultaten hebben, zoals geen beeldweergave. Als dit gebeurt, schakelt u resampling uit en converteert u het bestand opnieuw. Dit probleem doet zich het meest voor bij subsampling en het minst bij bicubische downsampling.

<table>
 <tbody>
  <tr>
   <th><p><strong>Printerresolutie</strong></p> </th>
   <th><p><strong>Standaardlijnscherm</strong></p> </th>
   <th><p><strong>Afbeeldingsresolutie</strong></p> </th>
  </tr>
  <tr>
   <td><p>300 dpi (laserprinter)</p> </td>
   <td><p>60 lpi</p> </td>
   <td><p>120 ppi</p> </td>
  </tr>
  <tr>
   <td><p>600 dpi (laserprinter)</p> </td>
   <td><p>85 lpi</p> </td>
   <td><p>170 ppi</p> </td>
  </tr>
  <tr>
   <td><p>1200 dpi (imagesetter)</p> </td>
   <td><p>120 lpi</p> </td>
   <td><p>240 ppi</p> </td>
  </tr>
  <tr>
   <td><p>2400 dpi (imagesetter)</p> </td>
   <td><p>150 lpi</p> </td>
   <td><p>300 ppi</p> </td>
  </tr>
 </tbody>
</table>

#### Objecten {#discard-objects} negeren

* Selecteer **Objecten negeren** om objecten op te geven die u uit de PDF wilt verwijderen en om gekromde lijnen in CAD-tekeningen te optimaliseren.
* **Alle acties** voor het verzenden, importeren en opnieuw instellen van formulieren negeren: Hiermee worden alle handelingen uitgeschakeld die betrekking hebben op het verzenden of importeren van formuliergegevens, en worden formuliervelden opnieuw ingesteld. Met deze optie blijven formulierobjecten behouden waaraan handelingen zijn gekoppeld.
* **Alle JavaScript-handelingen** negeren: Hiermee verwijdert u handelingen die JavaScript gebruiken uit de PDF.
* **Ingesloten paginaminiaturen** negeren: Hiermee verwijdert u ingesloten paginaminiaturen. Deze optie is handig voor grote documenten waarbij het lang kan duren voordat de paginaminiaturen zijn gegenereerd nadat u op de knop Pagina&#39;s hebt geklikt.
* **Vloeiende lijnen converteren naar curven**: Hiermee verkleint u het aantal controlepunten dat wordt gebruikt om curven op te bouwen in CAD-tekeningen. Dit resulteert in kleinere PDF-bestanden en snellere rendering op het scherm.
* **Ingesloten afdrukinstellingen** negeren: Hiermee verwijdert u ingesloten afdrukinstellingen uit het document, zoals pagina&#39;s schalen en duplexmodus.
* **Bladwijzers** negeren: Hiermee verwijdert u alle bladwijzers uit het document.
* **Formuliervelden** afvlakken: Hiermee maakt u formuliervelden onbruikbaar zonder dat de weergave verandert. Formuliergegevens worden met de pagina samengevoegd om pagina-inhoud te worden.
* **Alle alternatieve afbeeldingen** negeren: Hiermee verwijdert u alle versies van een afbeelding, behalve de versie die is bestemd voor schermweergave. Sommige PDF&#39;s bevatten meerdere versies van dezelfde afbeelding voor verschillende doeleinden, zoals weergave op het scherm met lage resolutie en afdrukken met hoge resolutie.
* **Documentcodes** negeren: Hiermee verwijdert u codes uit het document, waardoor ook de toegankelijkheid en de mogelijkheid om de tekst opnieuw te plaatsen worden verwijderd.
* **Afbeeldingsfragmenten** zoeken en samenvoegen: Zoekt naar afbeeldingen of maskers die zijn gefragmenteerd in dunne segmenten en probeert de segmenten samen te voegen tot ????n afbeelding of masker.
* **Ingesloten zoekindex** negeren: Hiermee verwijdert u ingesloten zoekindexen, waardoor het bestand kleiner wordt.

#### Gebruikersgegevens {#discard-user-data} negeren

Selecteer **Gebruikersgegevens negeren** om persoonlijke gegevens te verwijderen die u niet wilt verspreiden of delen met andere gebruikers.

* **Alle opmerkingen, Forms en multimedia** negeren: Hiermee verwijdert u alle opmerkingen, formulieren, formuliervelden en multimedia uit de PDF.
* **Alle objectgegevens** negeren: Hiermee verwijdert u alle objecten uit de PDF.
* **Externe kruisverwijzingen negeren**: Hiermee verwijdert u koppelingen naar andere documenten. Koppelingen die naar andere locaties in de PDF gaan, worden niet verwijderd.
* **Inhoud van verborgen lagen negeren en zichtbare lagen** afvlakken: Hiermee verkleint u de bestandsgrootte. Het geoptimaliseerde document ziet er net zo uit als de originele PDF, maar bevat geen laaggegevens.
* **Documentgegevens en metagegevens** negeren: Hiermee wordt informatie verwijderd uit het documentinformatiewoordenboek en alle metagegevensstromen. (Gebruik de opdracht Opslaan als om metagegevensstromen te herstellen naar een kopie van de PDF.)
* **Bestandsbijlagen** negeren: Hiermee verwijdert u alle bestandsbijlagen, inclusief bijlagen die als opmerkingen aan de PDF zijn toegevoegd. (PDF optimaliseren optimaliseert bijgevoegde bestanden niet.)
* **Priv??gegevens van andere toepassingen** negeren: Hiermee verwijdert u gegevens uit een PDF-document die alleen nuttig zijn voor de toepassing waarmee het document is gemaakt. Deze instelling heeft geen invloed op de functionaliteit van de PDF, maar verkleint de bestandsgrootte.

### {#clean-up} opruimen

Selecteer **Overbodig verwijderen** om overbodige items uit het document te verwijderen.
Deze items bevatten elementen die verouderd of niet nodig zijn voor het beoogde gebruik van het document. Het verwijderen van bepaalde elementen kan ernstige gevolgen hebben voor de functionaliteit van de PDF. Standaard worden alleen elementen geselecteerd die geen invloed hebben op de functionaliteit. Als u niet zeker weet wat de gevolgen zijn van het verwijderen van andere opties, gebruikt u de standaardselecties.

**Compressie**

Selecteer een van de volgende compressieopties voor Flate in het keuzemenu:

* Volledig bestand comprimeren
* Documentstructuur comprimeren
* Compressie verwijderen
* Compressie ongewijzigd laten

**Gebruik Flate om niet-gecodeerde** stromen te coderen: Hiermee past u Flate-compressie toe op alle stromen die niet zijn gecodeerd.

**Ongeldige bladwijzers** negeren: Hiermee verwijdert u bladwijzers die verwijzen naar pagina&#39;s in het document die worden verwijderd.

**Benoemde doelen zonder referenties** negeren: Hiermee verwijdert u benoemde doelen waarnaar niet intern in het PDF-document wordt verwezen. Met deze optie wordt niet gecontroleerd op koppelingen van andere PDF-bestanden of websites.

**De PDF optimaliseren voor snelle webweergave**: Hiermee deelt u een PDF-document opnieuw in, zodat het document per pagina kan worden gedownload van webservers (byte-serving).

**Gebruik Flate in plaats** van LZW-codering in stromen die LZW-codering gebruiken: Hiermee past u Flate-compressie toe op alle inhoudsstromen en afbeeldingen die LZW-codering gebruiken.

**Ongeldige koppelingen** negeren: Hiermee verwijdert u koppelingen die naar ongeldige doelen springen.

**Pagina-inhoud** optimaliseren: Hiermee worden alle regeleindetekens geconverteerd naar spatietekens, wat de Flate-compressie verbetert.

## Microsoft Excel-instellingen (alleen Windows) {#microsoft-excel-settings-windows-only}

Deze opties bepalen hoe de dossiers van Microsoft Excel worden omgezet. Zie [Bestandstype-instellingen maken of bewerken](#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

**Probeer OpenOffice als terugvalconverter**: Als deze optie is geselecteerd en een conversie met Microsoft Excel mislukt of de opgegeven time-outlimiet bereikt, probeert de PDF-Generator de conversie uit te voeren met OpenOffice. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Bestandsnaamextensies**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `xls,xlsx`. Neem geen punt voor of spatie op tussen de extensies.

**PDF/A-1a-compatibel bestand** maken: Hiermee wordt het gebruik van de instelling PDF/A-1b:2005 RGB Adobe PDF geforceerd.

**Bladwijzers toevoegen aan Adobe PDF**: Hiermee converteert u Excel-werkbladnamen naar bladwijzers. Deze optie is standaard geselecteerd.

**Werkblad aanpassen aan enkele pagina**: Hiermee wordt de tekst verkleind zodat deze op ????n pagina in het werkblad past.

**Hele werkboek** converteren: Hiermee converteert u alle werkbladen in het Excel-bestand. Als u deze optie niet selecteert, wordt alleen de huidige pagina geconverteerd.

**Macro&#39;s automatisch** uitvoeren: Hiermee worden alle macro&#39;s in het Excel-document uitgevoerd (bijvoorbeeld een macro dat de huidige tijd invoegt) voordat het document wordt geconverteerd.

**Documentgegevens** converteren: Hiermee voegt u PDF-documenteigenschappen toe op basis van de documentgegevens in het bronbestand. Dit omvat informatie zoals documenttitel, auteur, onderwerp, en sleutelwoorden.

**Koppelingen toevoegen aan Adobe PDF**: Hiermee converteert u hyperlinks in het bronbestand naar hyperlinks in het PDF-document.

**Bronbestand bijvoegen bij Adobe PDF**: Als deze optie is geselecteerd, wordt het originele Excel-werkblad ingevoegd als een bijlage in het gegenereerde PDF-document.

**Toegankelijkheid en Reflow inschakelen met gelabelde Adobe PDF**: Hiermee sluit u codes in het PDF-document in om toegankelijkheid en opnieuw plaatsen in te schakelen.

**Lijst met Excel-toevoegingen die moeten worden geladen**: Standaard worden (om beveiligingsredenen) geen Excel-invoegtoepassingen uitgevoerd wanneer een Excel-bestand naar PDF wordt geconverteerd. Om bepaalde toe:voegen-ins van Excel toe te staan om tijdens omzetting te lopen, verstrek een komma-gescheiden lijst van de namen van toe:voegen-ins.

**Lijst met te converteren** werkbladen: Als dit vak leeg is, worden alle werkbladen in het Excel-werkblad opgenomen in het gegenereerde PDF-bestand. Als u een subset van de werkbladen selectief wilt converteren, voert u een door komma&#39;s gescheiden lijst met werkbladnamen in.

## Microsoft PowerPoint-instellingen (alleen Windows) {#microsoft-powerpoint-settings-windows-only}

Deze opties bepalen hoe Microsoft PowerPoint-bestanden worden geconverteerd. Zie [Bestandstype-instellingen maken of bewerken](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

**[!UICONTROL Try OpenOffice As Fallback Converter]**: Als deze optie is geselecteerd en een conversie met Microsoft PowerPoint mislukt of de opgegeven time-outlimiet bereikt, probeert de PDF-Generator de conversie met OpenOffice uit te voeren. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is ppt, pptx. Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: Hiermee voegt u documentinformatie toe uit het dialoogvenster Eigenschappen van het bronbestand, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard geselecteerd.

**[!UICONTROL Add Bookmarks To Adobe PDF]**: Hiermee converteert u PowerPoint-titels naar bladwijzers. Deze optie is standaard geselecteerd.

**[!UICONTROL Attach Source File To Adobe PDF]**: Hiermee voegt u het bronbestand als bijlage toe aan het PDF-bestand. Deze optie is standaard niet geselecteerd.

**[!UICONTROL Enable Accessibility And Reflow With Tagged Adobe PDF]**: Hiermee sluit u codes in het PDF-bestand in. Deze optie is standaard niet geselecteerd.

**[!UICONTROL Convert Multimedia To PDF Multimedia]**: Hiermee converteert u waar mogelijk multimedia naar PDF. Deze optie is standaard geselecteerd.

**[!UICONTROL Convert Speaker Notes]**: Hiermee converteert u sprekersnotities naar PDF.

**[!UICONTROL Run Macros Automatically]**: Hiermee worden eventuele macro&#39;s in het PowerPoint-document uitgevoerd (bijvoorbeeld een macro dat de huidige tijd invoegt) voordat het document wordt geconverteerd.

**[!UICONTROL PDF Layout Based On PowerPoint Printer Settings]**: Gebruikt PowerPoint-printerinstellingen om het PDF-document op te maken.

**[!UICONTROL Add Links To Adobe PDF]**: Bestaande koppelingen blijven behouden wanneer het bestand wordt geconverteerd. De weergave van koppelingen is over het algemeen ongewijzigd. Koppelingen kunnen alleen worden gemaakt als de optie Toegankelijkheid inschakelen ook is geselecteerd. Deze optie is standaard niet geselecteerd.

**[!UICONTROL Save Slide Transitions In Adobe PDF]**: Hiermee converteert u diaovergangen. Deze optie is standaard geselecteerd.

**[!UICONTROL Save Animations In Adobe PDF]**: Geconverteerde animaties worden opgeslagen in het PDF-bestand.

**[!UICONTROL Convert Hidden Slides To PDF Pages]**: Verborgen dia&#39;s converteren.

**[!UICONTROL Create PDF/A-1a Compliant File]**: Hiermee wordt het gebruik van de instelling PDF/A-1b:2005 RGB Adobe PDF geforceerd. Enkele PowerPoint-functies worden niet geconverteerd wanneer u een PDF-bestand maakt. Als een PowerPoint-overgang in Acrobat geen gelijkwaardige overgang heeft, wordt een vergelijkbare overgang vervangen. Als meerdere animatie-effecten zich in dezelfde dia bevinden, wordt ????n effect gebruikt. Paginaovergangen en vlieg-ins voor opsommingstekens worden geconverteerd.

## Microsoft Project-instellingen (alleen Windows) {#microsoft-project-settings-windows-only}

Deze opties bepalen hoe de dossiers van het Project van Microsoft worden omgezet. Zie [Bestandstype-instellingen maken of bewerken](#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

1. **[!UICONTROL Filename Extensions:]** Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `mpp`. Neem geen punt voor of spatie op tussen de extensies.

1. **[!UICONTROL Convert Document Information]**: Hiermee voegt u documentinformatie toe uit het dialoogvenster Eigenschappen van het bronbestand, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard geselecteerd.
1. **[!UICONTROL Attach Source File To Adobe PDF]**: Hiermee voegt u het bronbestand als bijlage toe aan het PDF-bestand.
1. **[!UICONTROL Create PDF/A-1a Compliant File]**: Hiermee wordt het gebruik van de instelling PDF/A-1b:2005 RGB Adobe PDF geforceerd.
1. **[!UICONTROL Run Macros Automatically]**: Hiermee worden eventuele macro&#39;s in het Microsoft Project-document uitgevoerd (bijvoorbeeld een macro dat de huidige tijd invoegt) voordat het document wordt geconverteerd.

## Microsoft Word-instellingen (alleen Windows) {#microsoft-word-settings-windows-only}

Deze opties bepalen hoe Microsoft Word-bestanden worden geconverteerd. Zie [Bestandstype-instellingen maken of bewerken](#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

**[!UICONTROL Try OpenOffice As Fallback Converter]**: Als deze optie is geselecteerd en een conversie met Microsoft Word mislukt of de opgegeven time-outlimiet bereikt, probeert de PDF-Generator de conversie met OpenOffice uit te voeren. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `doc,docx,rtf,txt`. Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: Hiermee voegt u documentinformatie toe uit het dialoogvenster Eigenschappen van het bronbestand, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard geselecteerd.

**[!UICONTROL Add Bookmarks To Adobe PDF]**: Hiermee converteert u koppen naar bladwijzers. Deze optie is standaard geselecteerd.

**[!UICONTROL Attach Source File To Adobe PDF]**: Hiermee voegt u het bronbestand als bijlage toe aan het PDF-bestand.

**[!UICONTROL Convert Cross-References And Table Of Contents To Links]**: Hiermee converteert u alle kruisverwijzingen en items in de inhoudsopgave naar koppelingen. Deze optie is standaard geselecteerd.

**[!UICONTROL Enable Accessibility And Reflow With Tagged Adobe PDF]**: Hiermee sluit u codes in het PDF-bestand in. Deze optie is standaard geselecteerd.

**[!UICONTROL Create PDF/A-1a Compliant File]**: Als deze optie is geselecteerd, wordt de RGB-Adobe PDF-instelling PDF/A-1b:2005 gebruikt.

**[!UICONTROL Run Macros Automatically]**: Hiermee worden alle macro&#39;s in het Word-document uitgevoerd (bijvoorbeeld een macro dat de huidige tijd invoegt) voordat het document wordt geconverteerd.

**[!UICONTROL Preserve Document Markup In Adobe PDF]**: Hiermee converteert u opmaak in het Word-document naar annotaties in het PDF-bestand.

**[!UICONTROL Add Links To Adobe PDF]**: Hiermee converteert u hyperlinks in het bronbestand naar hyperlinks in het PDF-document.

**[!UICONTROL Convert Footnote And Endnote Links]**: Hiermee maakt u koppelingen van de voetnoot- en eindnootverwijzingen naar notities in het PDF-document.

**[!UICONTROL Convert Displayed Comments To Notes in Adobe PDF]**: Hiermee converteert u opmerkingen in het Word-document naar tekstnotities in het PDF-document.

**[!UICONTROL Enable Advanced Tagging]**: Hiermee voegt u geavanceerde codes toe voor verbeterde toegankelijkheid.

**[!UICONTROL Convert All Styles To Bookmarks]**: Hiermee converteert u alle stijlen in het Word-document naar bladwijzers in het PDF-document.

**[!UICONTROL Convert specified styles to bookmarks]**: Hiermee converteert u de stijlen die u in het  **[!UICONTROL Styles with levels]** veld definieert naar bladwijzers in het PDF-document.

**[!UICONTROL Styles With Levels]**: Hiermee geeft u op welke stijlen in het Word-document worden geconverteerd naar bladwijzers in het PDF-document. Hiermee geeft u ook het niveau van de bladwijzers op. Als u deze functie wilt gebruiken, schakelt u de optie **[!UICONTROL Convert All Styles To Bookmarks]** uit en geeft u de stijlnamen op in de volgende indeling:

**styleName1=level1[,styleName2=level2...]**

Als de naam van een Microsoft Word-stijl een komma (,) of een gelijkteken (=) bevat, plaatst u voor de speciale tekens het escape-teken (&quot;\_). Geef bijvoorbeeld een stijl met de naam &quot;Kop, 1&quot; op als Kop\, 1.

**Acrobat PDFMaker-codering:** geeft het coderingstype op voor de invoer van normale tekst in Acrobat PDFMaker. Als u bijvoorbeeld een bestand met UTF-8-codering gebruikt, bereikt u de beste resultaten met UTF-8.

## Microsoft Visio-instellingen (alleen Windows) {#visio}

**Documentgegevens** converteren: Hiermee voegt u documentinformatie toe uit het dialoogvenster Eigenschappen van het bronbestand, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard geselecteerd. Deze optie is standaard ingeschakeld.

**Koppelingen toevoegen aan Adobe PDF**: Hiermee blijven alle koppelingen behouden. Deze optie is standaard geselecteerd.

**Bladwijzers toevoegen aan Adobe PDF**: Hiermee converteert u koppen naar bladwijzers. Deze optie is standaard geselecteerd.

**Bronbestand bijvoegen bij Adobe PDF**: Hiermee voegt u het bronbestand als bijlage toe aan het PDF-bestand.

**Lagen altijd afvlakken in Adobe PDF**: Hiermee worden alle Visio-lagen samengevoegd.

**Alle pagina&#39;s** converteren: Hiermee converteert u alle pagina&#39;s van het Visio-bestand.

**Deelvenster Lagen openen bij weergave in Adobe Acrobat**: Als Visio-lagen niet worden samengevoegd, wordt een venster geopend waarin u kunt opgeven welke lagen in het PDF-bestand behouden blijven wanneer u het opent met Acrobat. Deze optie is standaard geselecteerd.

**PDF/A-1b-compatibel bestand** maken: Hiermee wordt het gebruik van de Adobe PDF-instelling PDF/A-1b:2005 (RGB) geforceerd.

**Opmerkingen converteren naar Adobe PDF-opmerkingen**: Hiermee converteert u Visio-notities naar PDF-opmerkingen.

## Microsoft Publisher-instellingen (alleen Windows) {#microsoft-publisher-settings-windows-only}

Deze opties bepalen hoe Microsoft Publisher-bestanden worden geconverteerd. Zie [Bestandstype-instellingen maken of bewerken](#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `pub`. Neem geen punt voor of spatie op tussen de extensies.

## AutoCAD-instellingen (alleen Windows) {#autocad-settings-windows-only}

Deze opties bepalen hoe AutoCAD-bestanden worden geconverteerd. Zie [Bestandstype-instellingen maken of bewerken](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `dwg`. Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: Hiermee voegt u documentinformatie toe uit het dialoogvenster Eigenschappen van het bronbestand, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard geselecteerd.

**[!UICONTROL Add Bookmarks To Adobe PDF]**: Hiermee converteert u koppen naar bladwijzers.

**[!UICONTROL Always Flatten Layers In Adobe PDF]**: Hiermee worden alle AutoCAD-lagen samengevoegd.

**[!UICONTROL Open Layers Pane When Viewed In Adobe Acrobat]**: Hiermee geeft u de lagenstructuur weer wanneer de PDF in Acrobat wordt geopend.

**[!UICONTROL Convert All Layouts]**: Hiermee worden alle indelingen in de PDF opgenomen.

**[!UICONTROL Convert Model Space to 3D]**: Als deze optie is geselecteerd, wordt de indeling van de modelruimte geconverteerd naar een 3D-annotatie in de PDF.

**[!UICONTROL Add Links To Adobe PDF]**: Als deze optie is geselecteerd, blijven alle koppelingen behouden.

**[!UICONTROL Attach Source File To Adobe PDF]**: Hiermee voegt u het bronbestand als bijlage toe aan het PDF-bestand.

**[!UICONTROL Create PDF/A-1b Compliant File]**: Hiermee wordt het gebruik van de instelling PDF/A-1b Adobe PDF geforceerd.

**[!UICONTROL Convert All Layers]**: Standaard converteert PDF Generator alleen de standaardlaag AutoCAD-bestanden naar PDF in plaats van alle lagen in het bestand. Selecteer deze optie als u alle lagen van het bestand wilt converteren.

**[!UICONTROL Embed Scale Information]**: Behoudt informatie over de tekenschaal.

**[!UICONTROL Convert Current Layout]**: Hiermee neemt u alleen de huidige indeling in de PDF op.

**[!UICONTROL List Of AutoCAD Layouts To Convert]**: Een AutoCAD-tekening kan meerdere lay-outs hebben. Als dit vak leeg is, worden alle lay-outs in de AutoCAD-tekening opgenomen in het gegenereerde PDF-document. Als u een subset van de lay-outs selectief wilt omzetten, voert u een door komma&#39;s gescheiden lijst met indelingsnamen in.

## OpenOffice-instellingen {#openoffice-settings}

Deze opties bepalen hoe de dossiers OpenOffice worden omgezet. Zie [Bestandstype-instellingen maken of bewerken](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings) voor instructies over het openen van deze opties.

**PDFMaker uitproberen als fallback-converter**: Als deze optie is geselecteerd en een conversie met OpenOffice de opgegeven time-outlimiet niet bereikt of niet doorloopt, probeert PDF Generator de conversie met PDFMaker. Als de conversie met PDFMaker mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Bestandsnaamextensies**: Geef de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die voor deze toepassing worden geaccepteerd. De standaardwaarde is `odt,odp,ods,odg,odf,sxw,sxi,sxd`. Neem geen punt voor of spatie op tussen de extensies.

**Bereik**: Zet alle pagina&#39;s om of geef bepaalde pagina&#39;s of een paginabereik op. Als er geen paginabereik is gedefinieerd, worden alle pagina&#39;s geconverteerd. Als u een paginabereik wilt exporteren, gebruikt u de indeling 3-6. Als u enkele pagina&#39;s wilt exporteren, gebruikt u de indeling 7;9;11. U kunt een combinatie van paginabereiken en enkele pagina&#39;s exporteren met een indeling als 3-6;8;10;12.

**Afdrukstand**: Alleen voor normale tekstbestanden selecteert u Staand of Liggend voor het geconverteerde PDF-document.

**Afbeeldingen**: Configureer hoe afbeeldingen worden geconverteerd. EPS-afbeeldingen met ingesloten voorvertoningen worden alleen als voorvertoningen ge??xporteerd. EPS-afbeeldingen zonder ingesloten voorvertoningen worden ge??xporteerd als lege plaatsaanduidingen. Bij compressie zonder verlies van afbeeldingen blijven alle pixels behouden. Met JPEG-compressie van afbeeldingen en een hoge kwaliteit blijven bijna alle pixels behouden. Bij een laag kwaliteitsniveau gaan sommige pixels verloren en worden artefacten ge??ntroduceerd, maar de bestanden worden kleiner.

**Algemeen**: Schakel de opties in om een gecodeerde PDF te converteren of om opmerkingen in Schrijver- en FormCalc-documenten te exporteren, dia-overgangseffecten te drukken of lege pagina&#39;s naar de PDF te exporteren. Wanneer tags worden ge??xporteerd, kan de bestandsgrootte aanzienlijk toenemen. Sommige tags die worden ge??xporteerd, zijn inhoudsopgaven, hyperlinks en besturingselementen.

U kunt ook opgeven hoe formulieren worden verzonden. De opties zijn XML, FDF, PDF of HTML. Dit het plaatsen treedt het bezit van URL van de controle met voeten dat u in het document plaatst. U kunt slechts ????n veelgebruikte instelling selecteren voor het PDF-document:

* PDF (verzendt het gehele document)
* FDF (verzendt de besturingsinhoud)
* HTML
* XML

**Gelabelde PDF**: Hiermee wordt het maken van gecodeerde PDF vanuit OpenOffice-documenten ingeschakeld. Gecodeerde PDF bevat informatie over de structuur van de documentinhoud. Dit kan helpen bij het weergeven van het document op apparaten met verschillende schermen en bij het gebruik van schermlezersoftware. Het helpt toegankelijkheidssoftware ook diverse nuttige bewerkingen uit te voeren met het PDF-document, zoals de inhoud van het PDF-document hardop lezen.

**Notities** exporteren: Hiermee converteert u de notities in OpenOffice-documenten naar notities in het gegenereerde PDF-document.

**Overgangseffecten** gebruiken: Hiermee converteert u de overgangseffecten van dia&#39;s in OpenOffice-presentaties naar de corresponderende PDF-overgangseffecten.

**Forms verzenden in formaat**: Hiermee maakt u een PDF-formulier dat kan worden ingevuld en afgedrukt door de gebruiker van het PDF-document.

**Automatisch ingevoegde lege pagina&#39;s** exporteren: Als deze optie is geselecteerd, worden automatisch ingevoegde lege pagina&#39;s opgenomen in het gegenereerde PDF-document. Dit is handig als u een PDF-document dubbelzijdig afdrukt. Een boek kan bijvoorbeeld zo worden geconfigureerd dat de eerste pagina van het hoofdstuk altijd begint op een pagina met een oneven nummer. Als het vorige hoofdstuk eindigt op een oneven pagina, voegt OpenOffice een lege even pagina in. Met deze optie bepaalt u of de even pagina in de gegenereerde PDF moet worden opgenomen.

## Overige toepassingsinstellingen (alleen Windows) {#other-applications-settings-windows-only}

U kunt de instellingen voor andere toepassingen niet wijzigen via de beheerconsole; de bestandsnaamextensies voor de ondersteunde bestandstypen worden weergegeven. Zie [Bestandstype-instellingen maken of bewerken](https://help.adobe.com/en_US/AEMForms/6.1/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7e42.2.html) voor instructies over het openen van deze instellingen.

* Corel WordPerfect: `wpd`
* Adobe PageMaker: `pmd, pm6, p65, pm`
* Adobe FrameMaker: `fm`
* Adobe Photoshop: `psd`

Ondersteuning voor deze bestandstypen moet mogelijk worden aangepast. Zie &quot;Support for Additional Native File Formats&quot; toevoegen in [Programmeren met AEM formulieren](https://www.adobe.com/go/learn_aemforms_programming_62) voor meer informatie.

Zie [Een PDFG-netwerkprinter instellen (alleen Windows)](/help/forms/using/admin-help/setting-pdfg-network-printer-windows.md) voor hulp bij het configureren van een PDFG-netwerkprinter.
