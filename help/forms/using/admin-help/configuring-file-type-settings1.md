---
title: Instellingen voor bestandstypen configureren
description: Leer hoe u instellingen voor bestandstypen configureert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '5868'
ht-degree: 0%

---


# Instellingen voor bestandstypen configureren {#configuring-file-type-settings}

In PDF Generator kunt u de toepassingsinstellingen voor ondersteunde bestandstypen instellen. In Windows kunt u de toepassingsinstellingen voor elk ondersteund bestandstype instellen. In UNIX en Linux kunt u de toepassingsinstellingen voor HTML-naar-PDF en OpenOffice instellen.

Op de pagina Instellingen bestandstype kunt u de volgende taken uitvoeren:

* [Een instelling voor bestandstypen maken of bewerken](#create-or-edit-file-type-settings)
* Geef op welke instellingen voor bestandstypen standaard moeten worden gebruikt (zie [Configuratiebestanden van PDF Generatoren importeren en exporteren](https://helpx.adobe.com/aem-forms/6-2/admin-help/importing-exporting-pdf-generator-configuration.html))
* [De standaardinstellingen wijzigen](/help/forms/using/admin-help/configuring-file-type-settings1.md#change-the-default-settings)
* [Ondersteuning voor PDF/A inschakelen](https://helpx.adobe.com/aem-forms/6-2/admin-help/enable-pdf-a-support.html)
* [Een instelling voor Bestandstypen verwijderen](https://helpx.adobe.com/aem-forms/6-2/admin-help/enable-pdf-a-support.html)

>[!NOTE]
>
>De instellingen voor bestandstypen zijn niet beschikbaar voor de fallback-convertors, zoals Acrobat voor conversie van HTML naar PDF, Microsoft PowerPoint, Microsoft Word en Microsoft Excel.

## Instellingen voor bestandstypen maken of bewerken {#create-or-edit-file-type-settings}

Maak of bewerk een bestandstype-instelling om op te geven hoe de toepassing omgaat met de conversie van ondersteunde bestandstypen. In Windows kunt u de toepassingsinstellingen voor elk ondersteund bestandstype instellen. In UNIX en Linux kunt u de toepassingsinstellingen voor HTML-naar-PDF en OpenOffice instellen.

1. Klik in de beheerconsole op **[!UICONTROL Services]** > **[!UICONTROL PDF Generator]** > **[!UICONTROL File Type Settings]**.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Typ in het vak Bestandsnaamextensies de bestandsextensies, gescheiden door komma&#39;s, voor de bestandstypen die voor deze toepassing zijn geaccepteerd. Neem de punt voor of geen ruimte op tussen de extensies. De standaardwaarde is `bmp,gif,jpeg,jpg,tif,tiff,png`.
1. (Optioneel) Als u OCR (optische codeherkenning) wilt gebruiken voor tekst in afbeeldingen of afbeeldingen, selecteert u OCR gebruiken en stelt u de volgende opties in:

**Primaire OCRL-taal:** De taal die de OCR-engine moet gebruiken om de tekens te identificeren. De standaardwaarde is Engels (VS).

**PDF-uitvoerstijl:** Selecteer Doorzoekbare afbeelding om een bitmapafbeelding te hebben van de pagina&#39;s op de voorgrond en de gescande tekst op een onzichtbare laag eronder. De weergave van de pagina verandert niet, maar de tekst wordt selecteerbaar en leesbaar. Selecteer Opgemaakte tekst en afbeeldingen om de originele pagina samen te stellen met herkende tekst, lettertypen, afbeeldingen en andere grafische elementen. De standaardwaarde is Doorzoekbare afbeelding (exact).

**Afbeeldingen downsamplen:** Hiermee verkleint u het aantal pixels in kleuren-, grijswaarden- en monochrome afbeeldingen. De downsampling van gescande afbeeldingen wordt uitgevoerd nadat de OCR is voltooid. De standaardwaarde is Laagste (600 dpi). Deze optie is niet beschikbaar als u de uitvoerstijl PDF instelt op Doorzoekbare afbeelding (exact).

1. Voer de vereiste informatie in deze secties in:

   [Configuratiebestanden van PDF Generatoren importeren en exporteren](https://helpx.adobe.com/aem-forms/6-2/admin-help/importing-exporting-pdf-generator-configuration.html)

[Adobe PDF-exportinstellingen (alleen Windows)](#adobe-pdf-export-settings-windows-only)

[HTML-naar-PDF-instellingen](#html-to-pdf-settings)

[Video&#39;s Flash naar PDF-instellingen](#flash-videos-to-pdf-settings)

[XPS naar PDF-instellingen](#xps-to-pdf-settings)

[Instellingen voor PDF optimaliseren](#pdf-optimizer-settings)

[Microsoft Excel-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings1.md#microsoft-excel-settings-windows-only)

[Microsoft PowerPoint-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings1.md#microsoft-powerpoint-settings-windows-only)

[Microsoft-projectinstellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings1.md#microsoft-project-settings-windows-only)

[Microsoft Word-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings1.md#microsoft-word-settings-windows-only)

[Microsoft Visio-instellingen (alleen Windows)](#visio)

[Microsoft Publisher-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings1.md#microsoft-publisher-settings-windows-only)

[AutoCAD-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings1.md#autocad-settings-windows-only)

[OpenOffice-instellingen](/help/forms/using/admin-help/configuring-file-type-settings1.md#openoffice-settings)

[Instellingen van andere toepassingen (alleen Windows)](#other-applications-settings-windows-only)

   Als u naar een andere sectie wilt gaan, klikt u op de koppeling op de webpagina of gebruikt u de **[!UICONTROL Next]**of **[!UICONTROL Previous]** knoppen.

1. Klik op **[!UICONTROL Save]** of **[!UICONTROL Save As]** en geef een naam voor de instelling op.

Ondersteuning voor verschillende bestandstypen kan worden aangepast. (Zie &quot; [Ondersteuning toevoegen voor extra eigen bestandsindelingen](https://help.adobe.com/en_US/AEMForms/6.1/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-7756.2.html)&quot; in [Programmeren met AEM formulieren](https://www.adobe.com/go/learn_lc_programming_11).)

## De standaardinstellingen wijzigen {#change-the-default-settings}

U kunt de standaardwaarde wijzigen voor de Adobe PDF-instellingen, beveiligingsinstellingen en bestandstypen die van toepassing zijn op nieuwe bronnen. Het wijzigen van de standaardinstellingen heeft geen invloed op de instellingen van bestaande bronnen.

1. Klik in Beheerconsole op **[!UICONTROL Services > PDF Generator]**.
1. Op de **[!UICONTROL Adobe PDF Settings]**, **[!UICONTROL File Type Settings]**, of **[!UICONTROL Security Settings]** pagina, klikt u **[!UICONTROL Set Default Settings]**.
1. Selecteer de gewenste standaardinstellingen. Een of meer van de volgende instellingen zijn beschikbaar op de pagina Standaardinstellingen instellen:

   **[!UICONTROL Adobe PDF Setting]**: De oorspronkelijke standaardwaarde is Standaard (Acrobat 6).

   **[!UICONTROL Security Settings]**: De oorspronkelijke standaardwaarde is Geen beveiliging (Acrobat 5).

   **[!UICONTROL File Type Settings]**: De oorspronkelijke standaardinstelling is Standaard.

1. Klik op **[!UICONTROL Save]**.

## Een instelling voor Bestandstypen verwijderen {#delete-a-file-type-setting}

U kunt een bestandstype-instelling verwijderen die niet meer wordt gebruikt.

1. Klik in de beheerconsole op **[!UICONTROL Services > PDF Generator> File Type Settings]**.
1. Schakel het selectievakje naast de instelling die u wilt verwijderen in. U kunt meerdere bronnen selecteren. Instellingen die geen selectievakje hebben, worden altijd opgenomen in de PDF Generator en kunnen niet worden verwijderd.
1. Klikken **[!UICONTROL Delete]** en klikt u op de pagina Verwijderbevestiging op **[!UICONTROL Delete]**.

## Instellingen voor Afbeelding naar PDF {#image-to-pdf-settings}

De volgende opties bepalen hoe afbeeldingsbestanden worden omgezet in PDF. Voor instructies over de toegang tot van deze montages, zie [Instellingen voor bestandstypen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Bestandsnaamextensies:** Lijst met door komma&#39;s gescheiden bestandsextensies die kunnen worden omgezet.

**Converter voor alternatieven uitproberen:** PDF Generatoren kunnen Java™ of Acrobat gebruiken om afbeeldingsbestanden om te zetten in PDF. Wanneer deze optie is geselecteerd en een conversie mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie met de alternatieve methode uit te voeren. Als de alternatieve methode mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

>[!NOTE]
>
>JPEG 2000-bestanden kunnen alleen worden geconverteerd met Acrobat.

**OCR gebruiken:** Bepaalt of OCR (optische tekenherkenning) op de PDF moet worden toegepast. Met de OCR-software kunt u de tekst in de PDF zoeken, corrigeren en kopiëren.

***notitie **: De functie OCR PDF (doorzoekbare PDF) wordt alleen ondersteund in Microsoft Windows.*

**Primaire OCR-taal** Hiermee geeft u de taal op die de OCR-engine moet gebruiken om de tekens te identificeren.

**PDF-uitvoerstijl:** Hiermee bepaalt u het type PDF dat wordt geproduceerd. Bij alle indelingen worden OCR en font- en paginaherkenning toegepast op tekstafbeeldingen en worden deze naar normale tekst omgezet.

**Doorzoekbare afbeelding:** Hiermee zorgt u ervoor dat de tekst doorzoekbaar en selecteerbaar is. Met deze optie behoudt u de oorspronkelijke afbeelding, heft u de afbeelding desgewenst schuin en plaatst u er een onzichtbare tekstlaag overheen. Met de optie Afbeeldingen downsamplen bepaalt u of en in welke mate de afbeelding wordt gedownsampled.

**Doorzoekbare afbeelding (exact):** Hiermee zorgt u ervoor dat de tekst doorzoekbaar en selecteerbaar is. Met deze optie behoudt u de oorspronkelijke afbeelding en plaatst u er een onzichtbare tekstlaag overheen. Aanbevolen voor gevallen waarin maximale getrouwheid aan de oorspronkelijke afbeelding vereist is.

**ClearScan:** Hiermee wordt een nieuw Type 3-lettertype gesynchroniseerd dat het oorspronkelijke lettertype benadert en wordt de pagina-achtergrond behouden door een kopie met lage resolutie te gebruiken.

**Afbeeldingen downsamplen:** Hiermee verkleint u het aantal pixels in kleuren-, grijswaarden- en monochrome afbeeldingen nadat de OCR is voltooid. Kies de mate van downsampling die u wilt toepassen. Bij een hogere waarde is er minder downsampling, waardoor PDF met een hogere resolutie ontstaan.

## Adobe PDF-exportinstellingen (alleen Windows) {#adobe-pdf-export-settings-windows-only}

De instelling Bestandstype exporteren in het gedeelte Adobe PDF-exportinstellingen wordt gebruikt voor het converteren van een PDF-bestand naar een andere indeling. De standaardwaarde is HTML 4.01 met CSS (Cascading Style Sheets) 1.0 (&amp;ast;.htm, &amp;ast;.html).

Voor instructies over het verkrijgen van toegang tot deze instelling raadpleegt u [Instellingen voor bestandstypen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings).

## HTML-naar-PDF-instellingen {#html-to-pdf-settings}

De volgende opties bepalen hoe de dossiers van HTML in PDF worden omgezet. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Converter voor alternatieven uitproberen:** PDF Generatoren kunnen Java™ of Acrobat gebruiken om HTML-bestanden om te zetten in PDF. Wanneer deze optie is geselecteerd en een conversie mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie met de alternatieve methode uit te voeren. Als de alternatieve methode mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Standaardcodering:** Hiermee stelt u de invoercodering van de bestandstekst in via een menu met besturingssystemen en alfabeten. Hiermee wordt de selectie bij Standaardcodering alleen gebruikt als het bronbestand van de HTML geen type codering opgeeft.

**Geselecteerde codering forceren:** Hiermee wordt alle codering die in het bronbestand van de HTML is opgegeven, genegeerd en wordt de selectie gebruikt die wordt weergegeven bij Standaardcodering.

### Instellingen voor Spiegelen {#spidering-settings}

*Spiegelen* scant webpagina&#39;s naar koppelingen naar andere webpagina&#39;s. Wanneer een koppeling naar een andere webpagina wordt aangetroffen, wordt de doelpagina opgehaald en opgenomen in het gegenereerde PDF-document. Schakel deze opties in om het aantal niveaus in te stellen dat moet worden opgehaald en omgezet in PDF:

**Alleen x-niveaus ophalen:** Met deze optie worden pagina&#39;s tot een diepte van het opgegeven niveau geconverteerd van de URL van de basispagina. De waarde 1 zet alleen de opgegeven URL om.

**Volledige site ophalen:** Hiermee converteert u de gehele site, te beginnen met de opgegeven URL.

**Op hetzelfde pad blijven:** Koppelingen die verwijzen naar pagina&#39;s die zich niet op hetzelfde relatieve pad bevinden als de basis-URL, worden niet geconverteerd tijdens het spinnen.

**Op dezelfde server blijven:** Koppelingen die verwijzen naar pagina&#39;s op verschillende servers worden niet geconverteerd tijdens het spinnen. Alleen koppelingen die naar dezelfde server als de opgegeven URL verwijzen, worden omgezet.

### Instellingen voor paginaconversie {#page-conversion-settings}

Schakel deze opties in om op te geven hoe de HTML-pagina&#39;s worden geconverteerd. Op basis van het paginaformaat worden de waarden voor breedte, hoogte en marge dienovereenkomstig aangepast.

**Paginaformaat:** Kies Aangepast en geef de breedte en hoogte op of selecteer vooraf gedefinieerde afmetingen.

**Richting:** Selecteer Staand of Liggend voor het omgezette document van de PDF.

**Marges:** Hiermee geeft u de marges (Boven, Onder, Links en Rechts) in het gegenereerde PDF-document op.

**Bladwijzers toevoegen aan PDF:** Voegt bladwijzers toe aan het PDF-document.

**Gelabelde PDF inschakelen:** Hiermee sluit u codes in het PDF-document in.

**Instellingen voor beginweergave instellen:** Hiermee kunt u Documentopties, Vensteropties en gebruikersinterfaceopties configureren. Deze instellingen bepalen hoe de inhoud in eerste instantie wordt weergegeven.

### Documentopties {#document-options}

Schakel deze opties in om op te geven hoe de inhoud moet worden weergegeven, hoe pagina&#39;s in het PDF-document moeten worden weergegeven en hoe u het vergrotingsniveau wilt instellen:

**Tonen:** Selecteer de deelvensters die in Acrobat moeten worden geopend wanneer het PDF-document wordt geopend.

**Pagina-indeling:** Selecteer het type pagina-indeling voor het PDF-document.

**Vergroting:** Kies een vooraf ingestelde vergroting voor de openingsweergave van het PDF-document of selecteer een aangepaste waarde. Als u een standaardinstelling kiest, wordt de standaardvergroting van Acrobat gebruikt.

**Openen naar paginanummer:** Geef het paginanummer op waarop de PDF wordt geopend.

### Vensteropties {#window-options}

Schakel deze opties in om op te geven hoe de grootte en weergave van het venster worden aangepast.

**Vensterformaat als van eerste pagina:** Hiermee past u de grootte van het Acrobat-venster aan aan de grootte van de eerste pagina.

**Venster centreren op scherm:** Hiermee opent u het venster in het midden van het scherm.

**Openen in Volledig scherm:** Hiermee opent u het venster in de modus Volledig scherm.

**Tonen:** Hiermee geeft u de documenttitel of bestandsnaam weer in het venster.

### Gebruikersinterfaceopties {#user-interface-options}

Schakel deze opties in om de weergave van het venster op te geven:

**Menubalk verbergen:** Hiermee verbergt u de menubalk in het PDF-document.

**Werkbalken verbergen:** Hiermee verbergt u de werkbalken in het PDF-document.

**Vensterbalk verbergen:** Hiermee verbergt u de vensterbesturingselementen in het PDF-document.

## Video&#39;s Flash naar PDF-instellingen {#flash-videos-to-pdf-settings}

PDF Generator ondersteunt de mogelijkheid om een video te verzenden voor Adobe Flash (SWF of FLV-bestand) en een PDF-bestand te maken met een video waarin de Adobe Flash is ingesloten. Voor deze conversie hoeft de Adobe Flash Player niet op de Forms-server te worden geïnstalleerd. Zie voor instructies over het openen van deze optie [Instellingen voor bestandstypen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Bestandsnaamextensies:** Lijst met door komma&#39;s gescheiden bestandsextensies die kunnen worden omgezet.

## XPS naar PDF-instellingen {#xps-to-pdf-settings}

De Specificatie van het Papier van XML (XPS) wordt gebruikt in de Drukkerij van Vensters. Dit is een Microsoft-indeling die kan worden gemaakt met elke Microsoft Office-toepassing. AEM formulieren bieden de mogelijkheid om XPS-bestanden om te zetten in PDF.

**Bestandsnaamextensies:** Een door komma&#39;s gescheiden lijst van alle filename van XPS uitbreidingen die kunnen worden omgezet. Er is momenteel één indeling: .xps.

## Instellingen voor PDF optimaliseren {#pdf-optimizer-settings}

PDF Generator ondersteunt de mogelijkheid om de grootte van PDF-bestanden te verkleinen. Of u al deze instellingen gebruikt of slechts een paar instellingen zijn afhankelijk van de manier waarop u de bestanden wilt gebruiken en van de essentiële eigenschappen die een bestand moet hebben. In de meeste gevallen zijn de standaardinstellingen geschikt voor maximale efficiëntie. U bespaart ruimte door ingesloten lettertypen te verwijderen, afbeeldingen te comprimeren en overbodige items uit de bestanden te verwijderen.

>[!NOTE]
>
>Als u een digitaal ondertekend document optimaliseert, worden de digitale handtekeningen verwijderd en ongeldig gemaakt.

Voor instructies over het verkrijgen van toegang tot deze instelling raadpleegt u [Instellingen voor bestandstypen maken of bewerken](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Doelversie PDF:** Geeft de versie van Acrobat aan waarmee de PDF compatibel is.

### Lettertypen {#fonts}

1. Selecteren **Lettertypen.**
1. Selecteer een van de volgende opties:

   **Insluiting van alle fonts ongedaan maken:** Hiermee worden alle ingesloten lettertypen verwijderd.

   **Geen font verwijderen:** Insluiting van fonts wordt niet ongedaan gemaakt.

   **Enkele fonts insluiten ongedaan maken:** Hiermee worden alleen de opgegeven lettertypen verwijderd. Ga als volgt te werk om de fonts op te geven die u wilt verwijderen uit de insluiting:

   * Selecteer zo nodig een andere map met lettertypen in het menu **Fontbron** vervolgkeuzelijst. In dit vervolgkeuzemenu worden de mappen met fonts weergegeven die zijn opgegeven in **Home > Settings > Core System > Core Configurations**.
   * Selecteer een of meer lettertypen in het menu **Beschikbare lettertypen** lijst en klik op **Toevoegen**. Deze lettertypen worden toegevoegd aan de **Te verwijderen ingesloten fonts** lijst.
   * Als u de insluiting van sommige lettertypen die niet op de Forms-server bestaan, ongedaan wilt maken, voert u de namen van deze lettertypen in het dialoogvenster **Fonts toevoegen aan niet-insluiting** doos. Klikken **Toevoegen**.

   >[!NOTE]
   >
   >*Als u de insluiting van bepaalde lettertypen waarvan de subsets in het document zijn ingesloten, ongedaan wilt maken, plaatst u het plusteken voor de naam van het lettertype. Bijvoorbeeld &quot;+Helvetica&quot;.*

1. Als u alleen de gebruikte subsets van de ingesloten fonts wilt insluiten, selecteert u **Subset maken van alle ingesloten fonts**.

   >[!NOTE]
   >
   >*Als u deze optie in combinatie met **Enkele fonts insluiten ongedaan maken**, fonts in de **A**Het insluiten van fonts in de niet-ingesloten lijst wordt nog steeds ongedaan gemaakt.*

   >[!NOTE]
   >
   >*Subsets van lettertypen is de techniek waarbij slechts een gedeelte van een lettertype wordt ingesloten. Een fontsubset bevat alleen de tekens die in het document worden gebruikt.*

### Transparantie {#transparency}

Als uw PDF-document illustraties bevat die transparantie bevatten, kunt u de instellingen voor PDF optimaliseren gebruiken om de transparantie af te vlakken en de bestandsgrootte te verkleinen.

>[!NOTE]
>
>Als Acrobat 4.0 en hoger is geselecteerd als de doelversie, worden alle transparante objecten afgevlakt. Voor andere doelversies van PDF wordt transparantie ondersteund en kunt u de transparantie-instellingen configureren.

Selecteren **Transparantie** om de transparantie-instellingen te configureren tijdens het optimaliseren van PDF-documenten.

**Transparantieniveau** Hiermee bepaalt u de hoeveelheid vectorinformatie die behouden blijft. Bij hogere instellingen blijven meer vectorobjecten behouden, terwijl bij lagere instellingen meer vectorobjecten worden gerasterd. Bij tussenliggende instellingen blijven eenvoudige gebieden in vectorvorm behouden en worden complexe gebieden gerasterd. Selecteer de laagste instelling als u alle illustraties wilt rasteren.

>[!NOTE]
>
>De mate van rastering is afhankelijk van de complexiteit van de pagina en de typen overlappende objecten.

**Lijntekeningen en tekst** Resolutie waarop alle objecten, inclusief afbeeldingen, vectorillustraties, tekst en verlopen, worden gerasterd. De ondersteunde waarden zijn 1 pixels per inch (ppi) tot 9600 ppi.

>[!NOTE]
>
>De resolutie voor lijnwerk en tekst moet doorgaans worden ingesteld op 600-1200 ppi voor rastering van hoge kwaliteit, vooral bij tekst met schreef of kleine puntgrootten.

**Verloop en netten** Resolutie waarop het verloop en de netten worden gerasterd. De ondersteunde waarden zijn 1 ppi tot 1200 ppi.

>[!NOTE]
>
>Verloop- en netresolutie moet doorgaans worden ingesteld op 150-300 ppi, omdat de kwaliteit van de verlopen, slagschaduwen en doezelaars niet verbetert bij hogere resoluties, maar doordat de afdruktijd en de bestandsgrootte toenemen.

**Alle tekst omzetten in contouren** Hiermee worden alle tekstobjecten (punttekst, vlaktekst en padtekst) omgezet in contouren en wordt alle informatie over tekstglyphs op pagina&#39;s met transparantie genegeerd. Met deze optie blijft de breedte van tekst tijdens het afvlakken consistent. Houd er rekening mee dat kleine lettertypen hierdoor iets dikker worden weergegeven in Acrobat of worden afgedrukt op desktopprinters met een lage resolutie. Dit heeft geen invloed op de kwaliteit van de tekst die wordt afgedrukt op printers of imagesetters met hoge resolutie.

**Alle lijnen converteren naar contouren** Hiermee zet u alle lijnen om in eenvoudige gevulde paden op pagina&#39;s met transparantie. Met deze optie blijft de breedte van lijnen tijdens het afvlakken consistent. Houd er rekening mee dat dunne lijnen hierdoor iets dikker worden weergegeven en dat de prestaties van de afvlakking kunnen afnemen.

**Complexe gebieden knippen** Hiermee zorgt u ervoor dat de grenzen tussen vectorillustraties en gerasterde illustraties langs objectpaden vallen. Met deze optie worden stitching-artefacten verminderd die ontstaan wanneer ze deel uitmaken van een logboek

<!--
NOTE to WRITER: Unfinished sentence above.
-->

>[!NOTE]
>
>Sommige printerstuurprogramma&#39;s verwerken raster- en vectorillustraties op een andere manier, wat soms tot kleurstitching leidt. U kunt het stitching problemen kunnen minimaliseren door sommige druk-bestuurder specifieke montages van het kleurenbeheer onbruikbaar te maken. Deze instellingen variëren per printer. Raadpleeg de documentatie bij de printer voor meer informatie.

Overdruk behouden: hiermee laat u de kleur van transparante illustraties overvloeien in de achtergrondkleur om een overdrukeffect te creëren.

In de volgende tabel ziet u de meestgebruikte printertypen en de resolutie van deze printers in dpi, de standaard rasterliniatuur in regels per inch (lpi) en een resamplingresolutie voor afbeeldingen in pixels per inch (ppi). Als u bijvoorbeeld afdrukt op een 600-dpi laserprinter, voert u 170 in voor de resolutie waarmee u het aantal pixels in afbeeldingen wilt wijzigen.

**Afbeeldingen** Selecteer Afbeeldingen om opties voor compressie en resampling op te geven voor afbeeldingen in kleur, grijswaarden en monochroom. U kunt met deze opties experimenteren om een juiste balans te vinden tussen bestandsgrootte en afbeeldingskwaliteit. De resolutie-instelling voor kleuren- en grijswaardenafbeeldingen moet 1,5 tot 2 keer zo hoog zijn als de rasterliniatuur waarop het bestand wordt afgedrukt. De resolutie voor monochrome afbeeldingen moet gelijk zijn aan die van het uitvoerapparaat, maar als u een monochrome afbeelding opslaat met een resolutie hoger dan 1500 dpi, neemt de bestandsgrootte toe zonder dat de beeldkwaliteit merkbaar toeneemt. Voor afbeeldingen die worden vergroot, zoals kaarten, is mogelijk een hogere resolutie vereist.

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
   <td><p>120 lp</p> </td>
   <td><p>240 ppi</p> </td>
  </tr>
  <tr>
   <td><p>2400 dpi (imagesetter)</p> </td>
   <td><p>150 lpi</p> </td>
   <td><p>300 ppi</p> </td>
  </tr>
 </tbody>
</table>

#### Objecten negeren {#discard-objects}

* Selecteren **Objecten negeren** om objecten op te geven die u uit de PDF wilt verwijderen en om gekromde lijnen in CAD-tekeningen te optimaliseren.
* **Alle acties voor het verzenden, importeren en opnieuw instellen van formulieren negeren**: Hiermee schakelt u alle handelingen uit die betrekking hebben op het verzenden of importeren van formuliergegevens, en stelt u formuliervelden opnieuw in. Met deze optie blijven formulierobjecten behouden waaraan handelingen zijn gekoppeld.
* **Alle JavaScript-handelingen negeren**: Hiermee verwijdert u alle handelingen die JavaScript gebruiken uit de PDF.
* **Ingesloten paginaminiaturen negeren**: Hiermee verwijdert u ingesloten paginaminiaturen. Deze optie is handig voor grote documenten waarbij het lang kan duren voordat de paginaminiaturen zijn gegenereerd nadat u op de knop Pagina&#39;s hebt geklikt.
* **Vloeiende lijnen converteren naar curven**: Hiermee verkleint u het aantal controlepunten dat wordt gebruikt om curven op te bouwen in CAD-tekeningen. Dit resulteert in kleinere PDF-bestanden en snellere rendering op het scherm.
* **Ingesloten afdrukinstellingen negeren**: Hiermee verwijdert u ingesloten afdrukinstellingen uit het document, zoals pagina&#39;s schalen en duplexmodus.
* **Bladwijzers negeren**: verwijdert alle bladwijzers uit het document.
* **Formuliervelden afvlakken**: Hiermee maakt u formuliervelden onbruikbaar zonder dat de weergave verandert. Formuliergegevens worden met de pagina samengevoegd om pagina-inhoud te worden.
* **Alle alternatieve afbeeldingen negeren**: Hiermee verwijdert u alle versies van een afbeelding, behalve de versie die bestemd is voor schermweergave. Sommige PDF bevatten meerdere versies van dezelfde afbeelding voor verschillende doeleinden, zoals weergave op het scherm met lage resolutie en afdrukken met hoge resolutie.
* **Documentcodes negeren**: Hiermee verwijdert u codes uit het document. Hierdoor worden ook de toegankelijkheid en de mogelijkheden voor opnieuw plaatsen voor de tekst verwijderd.
* **Afbeeldingsfragmenten zoeken en samenvoegen**: zoekt naar afbeeldingen of maskers die zijn gefragmenteerd in dunne segmenten en probeert de segmenten samen te voegen tot één afbeelding of masker.
* **Ingesloten zoekindex negeren**: Hiermee verwijdert u ingesloten zoekindexen, waardoor het bestand kleiner wordt.

#### Gebruikersgegevens negeren {#discard-user-data}

Selecteren **Gebruikersgegevens negeren** om persoonlijke gegevens te verwijderen die u niet wilt verspreiden of delen met andere gebruikers.

* **Alle opmerkingen, Forms en multimedia negeren**: Hiermee verwijdert u alle opmerkingen, formulieren, formuliervelden en multimedia uit de PDF.
* **Alle objectgegevens negeren**: Hiermee verwijdert u alle objecten uit de PDF.
* **Externe kruisverwijzingen negeren**: verwijdert koppelingen naar andere documenten. Koppelingen die naar andere locaties in de PDF gaan, worden niet verwijderd.
* **Inhoud van verborgen lagen negeren en zichtbare lagen afvlakken**: Hiermee verkleint u de bestandsgrootte. Het geoptimaliseerde document ziet er net zo uit als de oorspronkelijke PDF, maar bevat geen laaggegevens.
* **Documentgegevens en metagegevens negeren**: Hiermee verwijdert u informatie uit het documentinformatiewoordenboek en alle metagegevensstromen. (Gebruik de opdracht Opslaan als om metagegevensstromen te herstellen naar een kopie van de PDF.)
* **Bestandsbijlagen negeren**: Hiermee verwijdert u alle bestandsbijlagen, inclusief bijlagen die als opmerkingen aan de PDF zijn toegevoegd. (Met PDF optimaliseren worden bijgevoegde bestanden niet geoptimaliseerd.)
* **Privégegevens van andere toepassingen negeren**: Hiermee verwijdert u gegevens uit een PDF-document dat alleen nuttig is voor de toepassing waarmee het document is gemaakt. Deze instelling heeft geen invloed op de functionaliteit van de PDF, maar de bestandsgrootte neemt wel af.

### Opruimen {#clean-up}

Selecteren **Opruimen** om overbodige items uit het document te verwijderen.
Deze items bevatten elementen die verouderd of niet nodig zijn voor het beoogde gebruik van het document. Het verwijderen van bepaalde elementen kan ernstige gevolgen hebben voor de functionaliteit van de PDF. Standaard worden alleen elementen geselecteerd die geen invloed hebben op de functionaliteit. Gebruik de standaardselecties als u niet zeker weet wat de gevolgen zijn van het verwijderen van andere opties.

**Compressie**

Selecteer een van de volgende compressieopties voor Flate in het keuzemenu:

* Volledig bestand comprimeren
* Documentstructuur comprimeren
* Compressie verwijderen
* Compressie ongewijzigd laten

**Niet-gecodeerde stromen coderen met Flate**: past Flate-compressie toe op alle stromen die niet zijn gecodeerd.

**Ongeldige bladwijzers negeren**: verwijdert bladwijzers die verwijzen naar pagina&#39;s in het document die worden verwijderd.

**Benoemde doelen zonder referenties negeren**: Verwijdert benoemde doelen waarnaar intern niet wordt verwezen vanuit het PDF-document. Met deze optie wordt niet gecontroleerd op koppelingen van andere PDF-bestanden of websites.

**De PDF optimaliseren voor snelle webweergave**: Hiermee deelt u een PDF-document opnieuw in, zodat het document per pagina kan worden gedownload van webservers (byte-serving).

**Gebruik Flate in plaats daarvan in stromen die LZW-codering gebruiken**: Hiermee past u Flate-compressie toe op alle inhoudsstromen en afbeeldingen die LZW-codering gebruiken.

**Ongeldige koppelingen negeren**: Verwijdert koppelingen die naar ongeldige doelen springen.

**Pagina-inhoud optimaliseren**: zet alle regeleindetekens om in spatietekens, wat de Flate-compressie verbetert.

## Microsoft Excel-instellingen (alleen Windows) {#microsoft-excel-settings-windows-only}

Deze opties bepalen hoe Microsoft Excel-bestanden worden omgezet. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](#create-or-edit-file-type-settings).

**OpenOffice uitproberen als fallback-converter**: Wanneer deze optie is geselecteerd en een conversie met Microsoft Excel mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie uit te voeren met OpenOffice. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Bestandsnaamextensies**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `xls,xlsx`. Neem geen punt voor of spatie op tussen de extensies.

**PDF/A-1a-compatibel bestand maken**: Forces the use of the PDF/A-1b:2005 RGB Adobe PDF setting.

**Bladwijzers toevoegen aan Adobe PDF**: Hiermee converteert u Excel-werkbladnamen naar bladwijzers. Deze optie is standaard ingeschakeld.

**Werkblad aanpassen aan enkele pagina**: Hiermee wordt de tekst verkleind zodat deze op één pagina in het werkblad past.

**Hele werkboek converteren**: converteert alle werkbladen in het Excel-bestand. Als u deze optie niet selecteert, wordt alleen de huidige pagina geconverteerd.

**Macro&#39;s automatisch uitvoeren**: Hiermee worden alle macro&#39;s in het Excel-document uitgevoerd (bijvoorbeeld een macro dat de huidige tijd invoegt) voordat het document wordt geconverteerd.

**Documentgegevens converteren**: Voegt PDF-documenteigenschappen toe op basis van de documentgegevens in het bronbestand. Dit omvat informatie zoals documenttitel, auteur, onderwerp, en sleutelwoorden.

**Koppelingen toevoegen aan Adobe PDF**: zet hyperlinks in het bronbestand om in hyperlinks in het PDF-document.

**Bronbestand bijvoegen bij Adobe PDF**: Als u deze optie selecteert, wordt het originele Excel-werkblad ingevoegd als een bijlage in het gegenereerde PDF-document.

**Toegankelijkheid en Reflow inschakelen met gelabelde Adobe PDF**: Hiermee sluit u codes in het PDF-document in om toegankelijkheid en opnieuw plaatsen in te schakelen.

**Lijst met te laden Excel-toevoegingen**: Door gebrek (voor veiligheidsoverwegingen), worden geen toe:voegen-ins van Excel in werking gesteld wanneer een dossier van Excel in PDF wordt omgezet. Om bepaalde toe:voegen-ins van Excel toe te staan om tijdens omzetting te lopen, verstrek een komma-gescheiden lijst van de namen van toe:voegen-ins.

**Lijst met te converteren werkbladen**: Als dit vak leeg is, worden alle werkbladen in het Excel-werkblad opgenomen in de gegenereerde PDF. Als u een subset van de werkbladen selectief wilt converteren, voert u een door komma&#39;s gescheiden lijst met werkbladnamen in.

## Microsoft PowerPoint-instellingen (alleen Windows) {#microsoft-powerpoint-settings-windows-only}

Deze opties bepalen hoe Microsoft PowerPoint-bestanden worden omgezet. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](/help/forms/using/admin-help/configuring-file-type-settings1.md#create-or-edit-file-type-settings).

**[!UICONTROL Try OpenOffice As Fallback Converter]**: Wanneer deze optie is geselecteerd en een conversie met Microsoft PowerPoint mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie uit te voeren met OpenOffice. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is ppt, pptx. Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: Voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Add Bookmarks To Adobe PDF]**: zet PowerPoint-titels om in bladwijzers. Deze optie is standaard ingeschakeld.

**[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand. Deze optie is standaard uitgeschakeld.

**[!UICONTROL Enable Accessibility And Reflow With Tagged Adobe PDF]**: Hiermee sluit u tags in het PDF-bestand in. Deze optie is standaard uitgeschakeld.

**[!UICONTROL Convert Multimedia To PDF Multimedia]**: zet multimedia waar mogelijk om in PDF-multimedia. Deze optie is standaard ingeschakeld.

**[!UICONTROL Convert Speaker Notes]**: Hiermee converteert u sprekersnotities naar PDF.

**[!UICONTROL Run Macros Automatically]**: Voert eventuele macro&#39;s in het PowerPoint-document uit (zoals een macro dat de huidige tijd invoegt) voordat het document wordt geconverteerd.

**[!UICONTROL PDF Layout Based On PowerPoint Printer Settings]**: Hiermee gebruikt u PowerPoint-printerinstellingen om het PDF-document op te maken.

**[!UICONTROL Add Links To Adobe PDF]**: Bestaande koppelingen blijven behouden wanneer het bestand wordt omgezet. De weergave van koppelingen is over het algemeen ongewijzigd. Koppelingen kunnen alleen worden gemaakt als de optie Toegankelijkheid inschakelen ook is geselecteerd. Deze optie is standaard uitgeschakeld.

**[!UICONTROL Save Slide Transitions In Adobe PDF]**: Hiermee converteert u diaovergangen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Save Animations In Adobe PDF]**: geconverteerde animaties worden opgeslagen in het PDF-bestand.

**[!UICONTROL Convert Hidden Slides To PDF Pages]**: Hiermee converteert u verborgen dia&#39;s.

**[!UICONTROL Create PDF/A-1a Compliant File]**: Forces the use of the PDF/A-1b:2005 RGB Adobe PDF setting. Enkele PowerPoint-functies worden niet geconverteerd wanneer u een PDF-bestand maakt. Als een PowerPoint-overgang in Acrobat geen gelijkwaardige overgang heeft, wordt een vergelijkbare overgang vervangen. Als meerdere animatie-effecten zich in dezelfde dia bevinden, wordt één effect gebruikt. Paginaovergangen en vlieg-ins voor opsommingstekens worden omgezet.

## Microsoft-projectinstellingen (alleen Windows) {#microsoft-project-settings-windows-only}

Deze opties bepalen hoe Microsoft-projectbestanden worden geconverteerd. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](#create-or-edit-file-type-settings).

1. **[!UICONTROL Filename Extensions:]** Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `mpp`. Neem geen punt voor of spatie op tussen de extensies.

1. **[!UICONTROL Convert Document Information]**: Voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.
1. **[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand.
1. **[!UICONTROL Create PDF/A-1a Compliant File]**: Forces the use of the PDF/A-1b:2005 RGB Adobe PDF setting.
1. **[!UICONTROL Run Macros Automatically]**: Voert eventuele macro&#39;s in het Microsoft-projectdocument uit (zoals een macro die de huidige tijd invoegt) voordat het document wordt geconverteerd.

## Microsoft Word-instellingen (alleen Windows) {#microsoft-word-settings-windows-only}

Deze opties bepalen hoe Microsoft Word-bestanden worden geconverteerd. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](#create-or-edit-file-type-settings).

**[!UICONTROL Try OpenOffice As Fallback Converter]**: Wanneer deze optie is geselecteerd en een conversie met Microsoft Word mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie uit te voeren met OpenOffice. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `doc,docx,rtf,txt`. Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: Voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Add Bookmarks To Adobe PDF]**: hiermee zet u koppen om in bladwijzers. Deze optie is standaard ingeschakeld.

**[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand.

**[!UICONTROL Convert Cross-References And Table Of Contents To Links]**: hiermee worden alle kruisverwijzingen en items in de inhoudsopgave omgezet in koppelingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Enable Accessibility And Reflow With Tagged Adobe PDF]**: Hiermee sluit u tags in het PDF-bestand in. Deze optie is standaard ingeschakeld.

**[!UICONTROL Create PDF/A-1a Compliant File]**: Als deze optie is geselecteerd, wordt de Adobe PDF-instelling PDF/A-1b:2005 RGB gebruikt.

**[!UICONTROL Run Macros Automatically]**: Hiermee worden alle macro&#39;s in het Word-document uitgevoerd (bijvoorbeeld een macro dat de huidige tijd invoegt) voordat het document wordt geconverteerd.

**[!UICONTROL Preserve Document Markup In Adobe PDF]**: Hiermee converteert u opmaak in het Word-document naar annotaties in het PDF-bestand.

**[!UICONTROL Add Links To Adobe PDF]**: zet hyperlinks in het bronbestand om in hyperlinks in het PDF-document.

**[!UICONTROL Convert Footnote And Endnote Links]**: Hiermee maakt u koppelingen van de voetnoot- en eindnootcitaten naar notities in het document PDF.

**[!UICONTROL Convert Displayed Comments To Notes in Adobe PDF]**: Hiermee converteert u opmerkingen in het Word-document naar tekstnotities in het PDF-document.

**[!UICONTROL Enable Advanced Tagging]**: Voegt geavanceerde codes toe voor verbeterde toegankelijkheid.

**[!UICONTROL Convert All Styles To Bookmarks]**: hiermee worden alle stijlen in het Word-document omgezet in bladwijzers in het PDF-document.

**[!UICONTROL Styles With Levels]**: Hiermee geeft u op welke stijlen in het Word-document worden omgezet in bladwijzers in het PDF-document. Hiermee geeft u ook het niveau van de bladwijzers op. Schakel de optie **[!UICONTROL Convert All Styles To Bookmarks]** en geef de stijlnamen op in de volgende indeling:

styleName1=level1[,styleName2=level2...]

Als de naam van een Microsoft Word-stijl een komma (,) of een gelijkteken (=) bevat, plaatst u voor de speciale tekens het escape-teken (&quot;\_). Geef bijvoorbeeld een stijl met de naam &quot;Kop, 1&quot; op als Kop\, 1.

## Microsoft Visio-instellingen (alleen Windows) {#visio}

**Documentgegevens converteren**: Voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld. Deze optie is standaard ingeschakeld.

**Koppelingen toevoegen aan Adobe PDF**: Alle koppelingen blijven behouden. Deze optie is standaard ingeschakeld.

**Bladwijzers toevoegen aan Adobe PDF**: hiermee zet u koppen om in bladwijzers. Deze optie is standaard ingeschakeld.

**Bronbestand bijvoegen bij Adobe PDF**: voegt het bronbestand als bijlage toe aan het PDF-bestand.

**Lagen altijd afvlakken in Adobe PDF**: Hiermee worden alle Visio-lagen samengevoegd.

**Alle pagina&#39;s converteren**: hiermee worden alle pagina&#39;s van het Visio-bestand geconverteerd.

**Deelvenster Lagen openen bij weergave in Adobe Acrobat**: Als Visio-lagen niet worden samengevoegd, wordt een venster geopend waarin u kunt opgeven welke lagen in het PDF-bestand behouden blijven wanneer u het opent met Acrobat. Deze optie is standaard ingeschakeld.

**PDF/A-1b-compatibel bestand maken**: Forces the use of the Adobe PDF Setting PDF/A-1b:2005 (RGB).

**Opmerkingen converteren naar Adobe PDF-opmerkingen**: Hiermee converteert u Visio-notities naar PDF-opmerkingen.

## Microsoft Publisher-instellingen (alleen Windows) {#microsoft-publisher-settings-windows-only}

Deze opties bepalen hoe Microsoft Publisher-bestanden worden geconverteerd. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](#create-or-edit-file-type-settings).

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `pub`. Neem geen punt voor of spatie op tussen de extensies.

## AutoCAD-instellingen (alleen Windows) {#autocad-settings-windows-only}

Deze opties bepalen hoe AutoCAD-bestanden worden omgezet. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](/help/forms/using/admin-help/configuring-file-type-settings1.md#create-or-edit-file-type-settings).

**[!UICONTROL Filename Extensions]**: Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `dwg`. Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: Voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Add Bookmarks To Adobe PDF]**: hiermee zet u koppen om in bladwijzers.

**[!UICONTROL Always Flatten Layers In Adobe PDF]**: Hiermee worden alle AutoCAD-lagen samengevoegd.

**[!UICONTROL Open Layers Pane When Viewed In Adobe Acrobat]**: geeft de lagenstructuur weer wanneer de PDF in Acrobat wordt geopend.

**[!UICONTROL Create PDF/E-1 Compliant File]**: Hiermee maakt u een bestand dat compatibel is met PDF/E-1. PDF/E is een ISO-norm voor de uitwisseling van technische en technische documentatie. Voor meer informatie over PDF/E-1, zie [Adobe en industriestandaarden](https://www.adobe.com/enterprise/standards/index.html).

**[!UICONTROL Convert All Layouts]**: Neemt alle lay-outs op in de PDF.

**[!UICONTROL Convert Model Space to 3D]**: Als deze optie is geselecteerd, wordt de indeling van de modelruimte omgezet in een 3D-annotatie in de PDF.

**[!UICONTROL Add Links To Adobe PDF]**: Als deze optie is geselecteerd, blijven alle koppelingen behouden.

**[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand.

**[!UICONTROL Create PDF/A-1b Compliant File]**: Forces the use of the PDF/A-1b Adobe PDF setting.

**[!UICONTROL Convert All Layers]**: Standaard wordt met PDF Generator alleen de standaardlaag AutoCAD-bestanden omgezet in PDF in plaats van alle lagen in het bestand. Selecteer deze optie als u alle lagen van het bestand wilt converteren.

**[!UICONTROL Embed Scale Information]**: Hiermee blijven de gegevens van de tekenschaal behouden.

**[!UICONTROL Convert Current Layout]**: Alleen de huidige lay-out wordt opgenomen in de PDF.

**[!UICONTROL List Of AutoCAD Layouts To Convert]**: Een AutoCAD-tekening kan meerdere lay-outs hebben. Als dit vak leeg is, worden alle lay-outs in de AutoCAD-tekening opgenomen in het gegenereerde PDF-document. Als u een subset van de lay-outs selectief wilt omzetten, voert u een door komma&#39;s gescheiden lijst met indelingsnamen in.

## OpenOffice-instellingen {#openoffice-settings}

Deze opties bepalen hoe de dossiers OpenOffice worden omgezet. Voor instructies over de toegang tot van deze opties raadpleegt u [Instellingen voor bestandstypen maken of bewerken](/help/forms/using/admin-help/configuring-file-type-settings1.md#create-or-edit-file-type-settings).

**PDFMaker uitproberen als fallback-converter**: Wanneer deze optie is geselecteerd en een conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie uit te voeren met PDFMaker. Als de conversie met PDFMaker mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Bestandsnaamextensies**: Geef de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die voor deze toepassing worden geaccepteerd. De standaardwaarde is `odt,odp,ods,odg,odf,sxw,sxi,sxd`. Neem geen punt voor of spatie op tussen de extensies.

**Bereik**: Converteer alle pagina&#39;s of geef bepaalde pagina&#39;s of een paginabereik op. Als er geen paginabereik is gedefinieerd, worden alle pagina&#39;s geconverteerd. Als u een paginabereik wilt exporteren, gebruikt u de indeling 3-6. Als u één pagina wilt exporteren, gebruikt u de indeling 7;9;11. U kunt een combinatie van paginabereiken en enkele pagina&#39;s exporteren met een indeling als 3-6;8;10;12.

**Afdrukstand pagina**: Alleen voor normale tekstbestanden selecteert u Staand of Liggend voor het omgezette PDF-document.

**Afbeeldingen**: Configureer hoe afbeeldingen worden omgezet. EPS-afbeeldingen met ingesloten voorvertoningen worden alleen als voorvertoningen geëxporteerd. EPS-afbeeldingen zonder ingesloten voorvertoningen worden geëxporteerd als lege plaatsaanduidingen. Bij compressie zonder verlies van afbeeldingen blijven alle pixels behouden. Met JPEG-compressie van afbeeldingen en een hoge kwaliteit blijven bijna alle pixels behouden. Bij een laag kwaliteitsniveau gaan sommige pixels verloren en worden artefacten geïntroduceerd, maar de bestandsgrootte neemt af.

**Algemeen**: Schakel de opties in om een gecodeerde PDF te converteren of om opmerkingen in Schrijver- en FormCalc-documenten te exporteren, om diaovergangseffecten te drukken of om lege pagina&#39;s naar de PDF te exporteren. Wanneer tags worden geëxporteerd, kan de bestandsgrootte aanzienlijk toenemen. Sommige tags die worden geëxporteerd, zijn inhoudsopgaven, hyperlinks en besturingselementen.

U kunt ook opgeven hoe formulieren worden verzonden. De opties zijn XML, FDF, PDF of HTML. Dit het plaatsen treedt het bezit van URL van de controle met voeten dat u in het document plaatst. U kunt slechts één veelgebruikte instelling selecteren voor het PDF-document:

* PDF (het hele document wordt verzonden)
* FDF (verzendt de besturingsinhoud)
* HTML
* XML

**Tagged PDF**: Schakelt het maken van gelabelde PDF uit OpenOffice-documenten in. Gelabelde PDF bevat informatie over de structuur van de documentinhoud. Dit kan helpen bij het weergeven van het document op apparaten met verschillende schermen en bij het gebruik van schermlezersoftware. Het helpt toegankelijkheidssoftware ook diverse nuttige bewerkingen uit te voeren met het PDF-document, zoals de inhoud van het PDF-document hardop lezen.

**Notities exporteren**: Hiermee worden de notities in OpenOffice-documenten omgezet in notities in het gegenereerde PDF-document.

**Overgangseffecten gebruiken**: Hiermee converteert u de overgangseffecten van de dia in OpenOffice-presentaties naar de overeenkomende overgangseffecten van de PDF.

**Forms verzenden in formaat**: maakt een PDF-formulier dat kan worden ingevuld en afgedrukt door de gebruiker van het PDF-document.

**Automatisch ingevoegde lege pagina&#39;s exporteren**: Als u deze optie selecteert, worden automatisch ingevoegde lege pagina&#39;s opgenomen in het gegenereerde PDF-document. Dit is handig als u een PDF-document dubbelzijdig afdrukt. Een boek kan bijvoorbeeld zo worden geconfigureerd dat de eerste pagina van het hoofdstuk altijd begint op een pagina met een oneven nummer. Als het vorige hoofdstuk eindigt op een oneven pagina, voegt OpenOffice een lege even pagina in. Met deze optie bepaalt u of de even pagina in de gegenereerde PDF wordt opgenomen.

## Overige toepassingsinstellingen (alleen Windows) {#other-applications-settings-windows-only}

U kunt de instellingen voor andere toepassingen niet wijzigen via de beheerconsole, maar wel via de bestandsextensies voor de ondersteunde bestandstypen. Voor instructies over de toegang tot van deze montages, zie [Instellingen voor bestandstypen maken of bewerken](https://help.adobe.com/en_US/AEMForms/6.1/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7e42.2.html).

* Corel WordPerfect: `wpd`
* PageMaker Adobe: `pmd, pm6, p65, pm`
* Adobe FrameMaker: `fm`
* Adobe Photoshop: `psd`

Ondersteuning voor deze bestandstypen moet mogelijk worden aangepast. Zie &quot;Ondersteuning voor extra eigen bestandsindelingen toevoegen&quot; in [Programmeren met AEM formulieren](https://www.adobe.com/go/learn_aemforms_programming_62).

Voor hulp bij het configureren van een PDFG-netwerkprinter raadpleegt u [Een PDFG-netwerkprinter instellen (alleen Windows)](/help/forms/using/admin-help/setting-pdfg-network-printer-windows.md).
