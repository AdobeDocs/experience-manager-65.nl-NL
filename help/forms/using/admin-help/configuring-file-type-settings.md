---
title: Instellingen voor bestandstypen configureren
description: Leer hoe u instellingen voor bestandstypen configureert. In PDF Generator kunt u de toepassingsinstelling voor ondersteunde bestandstypen instellen om instellingen voor bestandstypen te configureren.
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
feature: PDF Generator
exl-id: 1a6640cc-22ef-41d5-a0c6-7a2c2dabcef1
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '5891'
ht-degree: 0%

---

# Instellingen voor bestandstypen configureren {#configuring-file-type-settings}

In PDF Generator kunt u de toepassingsinstellingen voor ondersteunde bestandstypen instellen. In Windows kunt u de toepassingsinstellingen voor elk ondersteund bestandstype instellen. In UNIX en Linux kunt u de toepassingsinstellingen voor HTML-naar-PDF en OpenOffice instellen.

Op de pagina Instellingen bestandstype kunt u de volgende taken uitvoeren:

* [Een instelling voor bestandstypen maken of bewerken](#create-or-edit-file-type-settings)
* Specificeer welke dossiertype montages aan gebruik door gebrek (zie [ het Invoeren en het uitvoeren van de configuratiedossiers van de PDF Generator ](/help/forms/using/admin-help/importing-exporting-pdf-generator-configuration.md))
* [De standaardinstellingen wijzigen](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings)
* [Ondersteuning voor PDF/A inschakelen](/help/forms/using/admin-help/enable-pdf-a-support.md)
* [Een instelling voor Bestandstypen verwijderen](/help/forms/using/admin-help/enable-pdf-a-support.md)

>[!NOTE]
>
>De instellingen voor bestandstypen zijn niet beschikbaar voor de fallback-convertors, zoals Acrobat voor conversie van HTML naar PDF, Microsoft PowerPoint, Microsoft Word en Microsoft Excel.

## Instellingen voor bestandstypen maken of bewerken {#create-or-edit-file-type-settings}

Maak of bewerk een bestandstype-instelling om op te geven hoe de toepassing omgaat met de conversie van ondersteunde bestandstypen. In Windows kunt u de toepassingsinstellingen voor elk ondersteund bestandstype instellen. In UNIX en Linux kunt u de toepassingsinstellingen voor HTML-naar-PDF en OpenOffice instellen.

1. Klik in de beheerconsole op **[!UICONTROL Services]** > **[!UICONTROL PDF Generator]** > **[!UICONTROL File Type Settings]** .
1. Klik op Nieuw of klik op de naam van een instelling.
1. Typ in het vak Bestandsnaamextensies de bestandsextensies, gescheiden door komma&#39;s, voor de bestandstypen die voor deze toepassing zijn geaccepteerd. Neem de punt voor of geen ruimte op tussen de extensies. De standaardwaarde is `bmp,gif,jpeg,jpg,tif,tiff,png` .
1. (Optioneel) Als u OCR (optische codeherkenning) wilt gebruiken voor tekst in afbeeldingen of afbeeldingen, selecteert u OCR gebruiken en stelt u de volgende opties in:

**Primaire Taal OCR:** De taal voor de motor OCR om de karakters te gebruiken te identificeren. De standaardwaarde is Engels (VS).

**de Stijl van de Output van de PDF:** Selecteer Doorzoekbaar Beeld om een bitmap beeld van de pagina&#39;s in de voorgrond en de gescande tekst op een onzichtbare laag onder te hebben. De weergave van de pagina verandert niet, maar de tekst wordt selecteerbaar en leesbaar. Selecteer Opgemaakte tekst en afbeeldingen om de originele pagina samen te stellen met herkende tekst, lettertypen, afbeeldingen en andere grafische elementen. De standaardwaarde is Doorzoekbare afbeelding (exact).

**de Beelden van de Downsampling:** vermindert het aantal pixel in kleur, grayscale, en monochrome beelden. De downsampling van gescande afbeeldingen wordt uitgevoerd nadat de OCR is voltooid. De standaardwaarde is Laagste (600 dpi). Deze optie is niet beschikbaar als u de uitvoerstijl PDF instelt op Doorzoekbare afbeelding (exact).

1. Voer de vereiste informatie in deze secties in:

[Configuratiebestanden van PDF Generatoren importeren en exporteren](/help/forms/using/admin-help/importing-exporting-pdf-generator-configuration.md)

[Adobe PDF-exportinstellingen (alleen Windows)](#adobe-pdf-export-settings-windows-only)

[HTML-naar-PDF-instellingen](#html-to-pdf-settings)

[Video&#39;s Flash naar PDF-instellingen](#flash-videos-to-pdf-settings)

[XPS naar PDF-instellingen](#xps-to-pdf-settings)

[Instellingen voor PDF optimaliseren](/help/forms/using/admin-help/configuring-file-type-settings.md)

[Microsoft Excel-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-excel-settings-windows-only)

[Microsoft PowerPoint-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-powerpoint-settings-windows-only)

[Microsoft-projectinstellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-project-settings-windows-only)

[Microsoft Word-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-word-settings-windows-only)

[Microsoft Visio-instellingen (alleen Windows)](#visio)

[Microsoft Publisher-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-publisher-settings-windows-only)

[AutoCAD-instellingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#autocad-settings-windows-only)

[OpenOffice-instellingen](/help/forms/using/admin-help/configuring-file-type-settings.md#openoffice-settings)

[Instellingen van andere toepassingen (alleen Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#other-applications-settings-windows-only)

   Klik op de koppeling op de webpagina of gebruik de knoppen **[!UICONTROL Next]** of **[!UICONTROL Previous]** om naar een andere sectie te gaan.

1. Nadat u alle secties hebt voltooid, klikt u op **[!UICONTROL Save]** of **[!UICONTROL Save As]** en geeft u een naam voor de instelling op.

Ondersteuning voor verschillende bestandstypen kan worden aangepast. (Zie &quot; [ Toevoegend Steun voor de Extra Inheemse Formaten van het Dossier ](https://help.adobe.com/en_US/AEMForms/6.1/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-7756.2.html)&quot;in [ Programmerend met AEM vormen ](https://www.adobe.com/go/learn_lc_programming_11).)

## De standaardinstellingen wijzigen {#change-the-default-settings}

U kunt de standaardwaarde wijzigen voor de Adobe PDF-instellingen, beveiligingsinstellingen en bestandstypen die van toepassing zijn op nieuwe bronnen. Het wijzigen van de standaardinstellingen heeft geen invloed op de instellingen van bestaande bronnen.

1. Klik in Beheerconsole op **[!UICONTROL Services > PDF Generator]** .
1. Klik op de pagina **[!UICONTROL Adobe PDF Settings]** , **[!UICONTROL File Type Settings]** of **[!UICONTROL Security Settings]** op **[!UICONTROL Set Default Settings]** .
1. Selecteer de gewenste standaardinstellingen. Een of meer van de volgende instellingen zijn beschikbaar op de pagina Standaardinstellingen instellen:

   **[!UICONTROL Adobe PDF Setting]**: De oorspronkelijke standaardwaarde is Standaard (Acrobat 6).

   **[!UICONTROL Security Settings]**: De oorspronkelijke standaardwaarde is Geen beveiliging (Acrobat 5).

   **[!UICONTROL File Type Settings]**: De oorspronkelijke standaardinstelling is Standaard.

1. Klik op **[!UICONTROL Save]**.

## Een instelling voor Bestandstypen verwijderen {#delete-a-file-type-setting}

U kunt een bestandstype-instelling verwijderen die niet meer wordt gebruikt.

1. Klik in de beheerconsole op **[!UICONTROL Services > PDF Generator> File Type Settings]** .
1. Schakel het selectievakje naast de instelling die u wilt verwijderen in. U kunt meerdere bronnen selecteren. Instellingen die geen selectievakje hebben, worden altijd opgenomen in de PDF Generator en kunnen niet worden verwijderd.
1. Klik op **[!UICONTROL Delete]** en klik op **[!UICONTROL Delete]** op de pagina Bevestiging verwijderen.

## Instellingen voor Afbeelding naar PDF {#image-to-pdf-settings}

De volgende opties bepalen hoe afbeeldingsbestanden worden omgezet in PDF. Voor instructies over de toegang tot van deze montages, zie [ creeer of geef dossiertype montages ](configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

**Bestandsnaamuitbreidingen:** komma-gescheiden lijst van filename uitbreidingen die kunnen worden omgezet.

**probeert de Convertor van de Fallback:** de PDF Generator kan of Java™ of Acrobat gebruiken om beelddossiers in PDF om te zetten. Wanneer deze optie is geselecteerd en een conversie mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie met de alternatieve methode uit te voeren. Als de alternatieve methode mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

>[!NOTE]
>
>JPEG 2000-bestanden kunnen alleen worden geconverteerd met Acrobat.

**OCR van het Gebruik:** specificeert of om OCR (optische karaktererkenning) op de PDF toe te passen. Met de OCR-software kunt u de tekst in de PDF zoeken, corrigeren en kopiëren.

***nota **: De OCR PDF (doorzoekbare PDF) eigenschap wordt gesteund slechts op Microsoft Vensters.*

**Primaire Taal OCR:** specificeert de taal voor de motor OCR om de karakters te gebruiken te identificeren.

**de Stijl van de Output van de PDF:** bepaalt het type van te produceren PDF. Bij alle indelingen worden OCR en font- en paginaherkenning toegepast op tekstafbeeldingen en worden deze naar normale tekst omgezet.

**Doorzoekbaar Beeld:** verzekert dat de tekst doorzoekbaar en selecteerbaar is. Met deze optie behoudt u de oorspronkelijke afbeelding, heft u de afbeelding desgewenst schuin en plaatst u er een onzichtbare tekstlaag overheen. Met de optie Afbeeldingen downsamplen bepaalt u of en in welke mate de afbeelding wordt gedownsampled.

**Doorzoekbaar Beeld (Exact):** zorgt ervoor dat de tekst doorzoekbaar en selecteerbaar is. Met deze optie behoudt u de oorspronkelijke afbeelding en plaatst u er een onzichtbare tekstlaag overheen. Aanbevolen voor gevallen waarin maximale getrouwheid aan de oorspronkelijke afbeelding vereist is.

**ClearScan:** synchroniseert een nieuw Type 3 doopvont die dicht origineel benadert, en bewaart de paginaachtergrond door een laag-resolutieexemplaar te gebruiken.

**de Beelden van de Downsampling:** vermindert het aantal pixel in kleur, grayscale, en monochrome beelden nadat OCR volledig is. Kies de mate van downsampling die u wilt toepassen. Bij een hogere waarde is er minder downsampling, waardoor PDF met een hogere resolutie ontstaan.

## Adobe PDF-exportinstellingen (alleen Windows) {#adobe-pdf-export-settings-windows-only}

De instelling Bestandstype exporteren in het gedeelte Adobe PDF-exportinstellingen wordt gebruikt voor het converteren van een PDF-bestand naar een andere indeling. De standaardwaarde is HTML 4.01 met CSS (Cascading Style Sheets) 1.0 (*.htm, *.html).

Voor instructies over de toegang tot van dit plaatsen, zie [ creeer of geef dossiertype montages ](configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

## HTML-naar-PDF-instellingen {#html-to-pdf-settings}

De volgende opties bepalen hoe de dossiers van HTML in PDF worden omgezet. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

**probeert de Convertor van de Fallback:** de PDF Generator kan of Java™ of Acrobat gebruiken om HTML dossiers in PDF om te zetten. Wanneer deze optie is geselecteerd en een conversie mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie met de alternatieve methode uit te voeren. Als de alternatieve methode mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Standaard het Coderen:** plaatst de inputcodering van de dossiertekst van een menu van werkende systemen en alfabeten. Hiermee wordt de selectie bij Standaardcodering alleen gebruikt als het bronbestand van de HTML geen type codering opgeeft.

**Kracht Geselecteerde Codering:** negeert om het even welke codering die in het HTML brondossier wordt gespecificeerd en de selectie gebruikt die in de Standaard Coderende optie wordt getoond.

### Instellingen voor Spiegelen {#spidering-settings}

*Spijend* scant Web-pagina&#39;s voor verbindingen aan andere Web-pagina&#39;s. Wanneer een koppeling naar een andere webpagina wordt aangetroffen, wordt de doelpagina opgehaald en opgenomen in het gegenereerde PDF-document. Schakel deze opties in om het aantal niveaus in te stellen dat moet worden opgehaald en omgezet in PDF:

**krijgt slechts de Niveaus van X:** Spinnen en zet pagina&#39;s tot een diepte van het gespecificeerde niveau van de basis pagina URL om. De waarde 1 zet alleen de opgegeven URL om.

**krijgt Volledige Plaats:** zet de volledige plaats om, die van verstrekte URL begint.

**Verblijf op Zelfde Weg:** Om het even welke verbindingen die aan pagina&#39;s richten die niet op de zelfde relatieve weg zoals basis URL zijn worden niet omgezet tijdens het spinnen.

**Verblijf op de Zelfde Server:** Om het even welke verbindingen die aan pagina&#39;s op verschillende servers richten worden niet omgezet tijdens het spinnen. Alleen koppelingen die naar dezelfde server als de opgegeven URL verwijzen, worden omgezet.

### Instellingen voor paginaconversie {#page-conversion-settings}

Schakel deze opties in om op te geven hoe de HTML-pagina&#39;s worden geconverteerd. Op basis van het paginaformaat worden de waarden voor breedte, hoogte en marge dienovereenkomstig aangepast.

**Grootte van de Pagina:** kies douane en specificeer de breedte en de hoogte, of selecteer vooraf bepaalde afmetingen.

**Richtlijn:** selecteer of portret of landschap voor het omgezette document van de PDF.

**Marges:** specificeert de marges (Boven, Onder, Links, en Rechts) in het geproduceerde document van de PDF.

**voegt Bladwijzers aan PDF toe:** voegt referenties aan het document van de PDF toe.

**laat Gecodeerde PDF toe:** sluit markeringen in het document van de PDF in.

**plaats Aanvankelijke Montages van de Mening:** laat u de Opties van het Document, de Opties van het Venster, en de Opties van het Gebruikersinterface vormen. Deze instellingen bepalen hoe de inhoud in eerste instantie wordt weergegeven.

### Documentopties {#document-options}

Schakel deze opties in om op te geven hoe de inhoud moet worden weergegeven, hoe pagina&#39;s in het PDF-document moeten worden weergegeven en hoe u het vergrotingsniveau wilt instellen:

**toon:** selecteer de ruiten om in Acrobat worden geopend wanneer het document van de PDF wordt geopend.

**Lay-out van de Pagina:** selecteer het type van paginalay-out voor het document van de PDF.

**Vergroting:** kies vooraf ingestelde vergroting voor de aanvankelijke mening van het document van de PDF of selecteer een douanewaarde. Als u een standaardinstelling kiest, wordt de standaardvergroting van Acrobat gebruikt.

**open aan Aantal van de Pagina:** specificeer het paginaaantal dat de PDF waaropent.

### Vensteropties {#window-options}

Schakel deze opties in om op te geven hoe de grootte en weergave van het venster worden aangepast.

**vergroot venster aan Aanvankelijke Pagina:** vergroot het venster van Acrobat tot de grootte van de aanvankelijke pagina.

**Venster van het Centrum op het Scherm:** opent het venster in het centrum van het scherm.

**Open op Volledige Wijze van het Scherm:** opent het venster op volledige het schermwijze.

**toon:** toont de documenttitel of filename in het venster.

### Gebruikersinterfaceopties {#user-interface-options}

Schakel deze opties in om de weergave van het venster op te geven:

**de Bar van het Menu van de Huid:** verbergt de menubar in het document van de PDF.

**Verberg Toolbars:** verbergt toolbars in het document van de PDF.

**de Controles van het Venster van de Huid:** verbergt de venstercontroles in het document van PDF.

## Video&#39;s Flash naar PDF-instellingen {#flash-videos-to-pdf-settings}

PDF Generator ondersteunt de mogelijkheid om een video te verzenden voor Adobe Flash (SWF of FLV-bestand) en een PDF-bestand te maken met een video waarin de Adobe Flash is ingesloten. Voor deze conversie hoeft de Adobe Flash Player niet op de Forms-server te worden geïnstalleerd. Voor instructies over de toegang tot van deze optie, zie [ creeer of geef dossiertype montages ](configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

**Bestandsnaamuitbreidingen:** komma-gescheiden lijst van filename uitbreidingen die kunnen worden omgezet.

## XPS naar PDF-instellingen {#xps-to-pdf-settings}

De Specificatie van het Papier van XML (XPS) wordt gebruikt in de Drukkerij van Vensters. Dit is een Microsoft-indeling die kan worden gemaakt met elke Microsoft Office-toepassing. AEM formulieren bieden de mogelijkheid om XPS-bestanden om te zetten in PDF.

**Bestandsnaamuitbreidingen:** a komma-gescheiden lijst van alle filename van XPS uitbreidingen die kunnen worden omgezet. Er is momenteel één indeling: .xps.

## Instellingen voor PDF optimaliseren {#pdf-optimizer-settings}

PDF Generator ondersteunt de mogelijkheid om de grootte van PDF-bestanden te verkleinen. Of u al deze instellingen gebruikt of slechts een paar instellingen zijn afhankelijk van de manier waarop u de bestanden wilt gebruiken en van de essentiële eigenschappen die een bestand moet hebben. In de meeste gevallen zijn de standaardinstellingen geschikt voor maximale efficiëntie. U bespaart ruimte door ingesloten lettertypen te verwijderen, afbeeldingen te comprimeren en overbodige items uit de bestanden te verwijderen.

>[!NOTE]
>
>Als u een digitaal ondertekend document optimaliseert, worden de digitale handtekeningen verwijderd en ongeldig gemaakt.

Voor instructies over de toegang tot van dit plaatsen, zie [ creeer of geef dossiertype montages ](configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

**Versie van het Doel PDF:** specificeert de versie van Acrobat dat de PDF met compatibel is.

### Lettertypen {#fonts}

1. Selecteer **Doopvonten.**
1. Selecteer een van de volgende opties:

   **unnembed alle doopvonten:** stelt alle ingebedde doopvonten samen.

   **maak om het even welk doopvont niet ongedaan:** maakt geen doopvonten unembed.

   **unnembed sommige doopvonten:** Unembedds slechts de gespecificeerde doopvonten. Ga als volgt te werk om de fonts op te geven die u wilt verwijderen uit de insluiting:

   * Indien nodig, selecteer een verschillende doopvontenfolder van het **bron van de Doopvont** drop-down menu. Dit drop-down menu maakt een lijst van doopvontfolders die in **worden gespecificeerd Huis > Montages > het Systeem van de Kern > de Configuraties van de Kern**.
   * Selecteer één of meerdere doopvonten van de **Beschikbare lijst van Doopvonten** en klik **toevoegen**. Deze doopvonten worden toegevoegd aan de **Doopvonten aan Unembed** lijst.
   * Als u sommige doopvonten wilt unembed die niet op de Server van Forms bestaan, ga de namen van die doopvonten in **voegt doopvonten aan unembed** doos toe. Klik **toevoegen**.

   >[!NOTE]
   >
   >*als u sommige doopvonten wilt unembed waarvan subsets in het document worden ingebed, prefix de doopvontnaam met + teken. Bijvoorbeeld, &quot;+Helvetica&quot;.*

1. Als u slechts de in-use subsets van de ingebedde doopvonten wilt inbedden, uitgezochte **Subset alle ingebedde doopvonten**.

   >[!NOTE]
   >
   >*Als u deze optie in combinatie met **gebruikt bedde sommige doopvonten**, zijn de doopvonten in **toevoegen doopvonten aan unembed**lijst nog volledig unembedded.*

   >[!NOTE]
   >
   >*subsetting van de Doopvont is de techniek om slechts een gedeelte van een doopvont in te bedden. Een fontsubset bevat alleen de tekens die in het document worden gebruikt.*

### Transparantie {#transparency}

Als uw PDF-document illustraties bevat die transparantie bevatten, kunt u de instellingen voor PDF optimaliseren gebruiken om de transparantie af te vlakken en de bestandsgrootte te verkleinen.

>[!NOTE]
>
>Als Acrobat 4.0 en hoger is geselecteerd als de doelversie, worden alle transparante objecten afgevlakt. Voor andere doelversies van PDF wordt transparantie ondersteund en kunt u de transparantie-instellingen configureren.

Selecteer **Transparantie** om de transparantiemontages te vormen terwijl het optimaliseren van de documenten van PDF.

**het niveau van de Transparantie** specificeert de hoeveelheid vectorinformatie die zal worden bewaard. Bij hogere instellingen blijven meer vectorobjecten behouden, terwijl bij lagere instellingen meer vectorobjecten worden gerasterd. Bij tussenliggende instellingen blijven eenvoudige gebieden in vectorvorm behouden en worden complexe gebieden gerasterd. Selecteer de laagste instelling als u alle illustraties wilt rasteren.

>[!NOTE]
>
>De mate van rastering is afhankelijk van de complexiteit van de pagina en de typen overlappende objecten.

**de Kunst van de Lijn en de Resolutie van de Tekst** waaraan alle voorwerpen, met inbegrip van beelden, vectorkunstwerk, tekst, en gradiënten, worden gerasterd. De ondersteunde waarden zijn 1 pixels per inch (ppi) tot 9600 ppi.

>[!NOTE]
>
>De resolutie voor lijnwerk en tekst moet doorgaans worden ingesteld op 600-1200 ppi voor rastering van hoge kwaliteit, vooral bij tekst met schreef of kleine puntgrootten.

**Verloop en Netten** Resolutie waaraan de gradiënt en de netten worden gerasterd. De ondersteunde waarden zijn 1 ppi tot 1200 ppi.

>[!NOTE]
>
>Verloop- en netresolutie moet doorgaans worden ingesteld op 150-300 ppi, omdat de kwaliteit van de verlopen, slagschaduwen en doezelaars niet verbetert bij hogere resoluties, maar doordat de afdruktijd en de bestandsgrootte toenemen.

**zet Alle Tekst in Omtrek** om alle typevoorwerpen (punttype, gebiedstype, en wegtype) in overzichten om en verwerpt alle informatie van typeglyph op pagina&#39;s die transparantie bevatten. Met deze optie blijft de breedte van tekst tijdens het afvlakken consistent. Houd er rekening mee dat kleine lettertypen hierdoor iets dikker worden weergegeven in Acrobat of worden afgedrukt op desktopprinters met een lage resolutie. Dit heeft geen invloed op de kwaliteit van de tekst die wordt afgedrukt op printers of imagesetters met hoge resolutie.

**zet Alle Lijnen in Omtrek** om alle slagen in eenvoudige gevulde wegen op pagina&#39;s die transparantie bevatten. Met deze optie blijft de breedte van lijnen tijdens het afvlakken consistent. Houd er rekening mee dat dunne lijnen hierdoor iets dikker worden weergegeven en dat de prestaties van de afvlakking kunnen afnemen.

**Zorgt de Complexe Gebieden van de Klem 1} ervoor dat de grenzen tussen vectorkunstwerk en gerasterde kunstwerk langs objecten wegen vallen.** Met deze optie worden stitching-artefacten verminderd die ontstaan wanneer ze deel uitmaken van een logboek

<!--
NOTE to WRITER: Unfinished sentence above.
-->

>[!NOTE]
>
>Sommige printerstuurprogramma&#39;s verwerken raster- en vectorillustraties op een andere manier, wat soms tot kleurstitching leidt. U kunt het stitching problemen kunnen minimaliseren door sommige druk-bestuurder specifieke montages van het kleurenbeheer onbruikbaar te maken. Deze instellingen variëren per printer. Raadpleeg de documentatie bij de printer voor meer informatie.

Overdruk behouden: hiermee laat u de kleur van transparante illustraties overvloeien in de achtergrondkleur om een overdrukeffect te creëren.

In de volgende tabel ziet u de meestgebruikte printertypen en de resolutie van deze printers in dpi, de standaard rasterliniatuur in regels per inch (lpi) en een resamplingresolutie voor afbeeldingen in pixels per inch (ppi). Als u bijvoorbeeld afdrukt op een 600-dpi laserprinter, voert u 170 in voor de resolutie waarmee u het aantal pixels in afbeeldingen wilt wijzigen.

**Beelden** selecteren Beelden om compressie en resampling opties voor kleur, grijswaarden, en monochrome beelden te specificeren. U kunt met deze opties experimenteren om een juiste balans te vinden tussen bestandsgrootte en afbeeldingskwaliteit. De resolutie-instelling voor kleuren- en grijswaardenafbeeldingen moet 1,5 tot 2 keer zo hoog zijn als de rasterliniatuur waarop het bestand wordt afgedrukt. De resolutie voor monochrome afbeeldingen moet gelijk zijn aan die van het uitvoerapparaat, maar als u een monochrome afbeelding opslaat met een resolutie hoger dan 1500 dpi, neemt de bestandsgrootte toe zonder dat de beeldkwaliteit merkbaar toeneemt. Voor afbeeldingen die worden vergroot, zoals kaarten, is mogelijk een hogere resolutie vereist.

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

* Selecteer **Weigeren Objecten** om voorwerpen te specificeren uit de PDF te verwijderen en gebogen lijnen in CAD tekeningen te optimaliseren.
* **verwerpt Alle Verzending van de Vorm, de Invoer en de Acties van het Terugstellen**: Maakt alle acties onbruikbaar die met het voorleggen of het invoeren van vormgegevens verwant zijn, en stelt vormgebieden opnieuw in. Met deze optie blijven formulierobjecten behouden waaraan handelingen zijn gekoppeld.
* **verwerpt Alle Acties van JavaScript**: Verwijdert uit de PDF om het even welke acties die JavaScript gebruiken.
* **verwerping Ingesloten de miniaturen van de Pagina**: verwijdert ingebedde paginaminiaturen. Deze optie is handig voor grote documenten waarbij het lang kan duren voordat de paginaminiaturen zijn gegenereerd nadat u op de knop Pagina&#39;s hebt geklikt.
* **zet Vloeiende Lijnen in Krommen** om: Vermindert het aantal controlepunten die worden gebruikt om krommen in CAD tekeningen te bouwen, die in kleinere PDF dossiers en snellere het schermteruggeven resulteren.
* **verwerping Ingesloten Montages van de Druk**: Verwijdert ingebedde drukmontages, zoals pagina het schrapen en duplexwijze, uit het document.
* **verwerping Bladwijzers**: verwijdert alle referenties uit het document.
* **Velden van de Vorm afvlakken**: maakt vormgebieden onbruikbaar zonder verandering in hun verschijning. Formuliergegevens worden met de pagina samengevoegd om pagina-inhoud te worden.
* **verwerpt Alle Afbeeldingen Alternatieve**: verwijdert alle versies van een beeld behalve de versie die voor het bekijken op het scherm bestemd is. Sommige PDF bevatten meerdere versies van dezelfde afbeelding voor verschillende doeleinden, zoals weergave op het scherm met lage resolutie en afdrukken met hoge resolutie.
* **de Markeringen van het Document van de Weigering**: verwijdert markeringen uit het document, dat ook de toegankelijkheid en het opnieuw plaatsen mogelijkheden voor de tekst verwijdert.
* **ontdekt en voegt de Fragmenten van het Beeld** samen: Zoekt beelden of maskers die in dunne plakken worden gefragmenteerd en probeert om de plakken in één enkel beeld of masker samen te voegen.
* **verwerping Ingesloten Index van het Onderzoek**: Verwijdert ingebedde onderzoeksindexen, die dossiergrootte verminderen.

#### Gebruikersgegevens negeren {#discard-user-data}

Selecteer **Gegevens van de Gebruiker negeren** om het even welke persoonlijke informatie te verwijderen die u niet met andere gebruikers wilt verspreiden of delen.

* **verwerp Alle Commentaren, Forms en Multimedia**: verwijdert alle commentaren, vormen, vormgebieden, en multimedia van de PDF.
* **verwerpt Alle Gegevens van Objecten**: verwijdert alle voorwerpen uit PDF.
* **verwerping Externe Verwijzingen**: Verwijdert verbindingen aan andere documenten. Koppelingen die naar andere locaties in de PDF gaan, worden niet verwijderd.
* **verwerpt de Verborgen inhoud van de Laag en vlakt Zichtbare Lagen** af: Vermindert dossiergrootte. Het geoptimaliseerde document ziet er net zo uit als de oorspronkelijke PDF, maar bevat geen laaggegevens.
* **verwerpt de Informatie van het Document en Meta-gegevens**: verwijdert informatie in het woordenboek van de documentinformatie en alle meta-gegevensstromen. (Gebruik de opdracht Opslaan als om metagegevensstromen te herstellen naar een kopie van de PDF.)
* **verwerpt de Gehechtheid van het Dossier**: verwijdert alle dossiergehechtheid, met inbegrip van gehechtheid die aan de PDF als commentaren wordt toegevoegd. (Met PDF optimaliseren worden bijgevoegde bestanden niet geoptimaliseerd.)
* **verwerpt Privé Gegevens van Andere Toepassingen**: scheurt informatie van een document van PDF dat slechts aan de toepassing nuttig is die tot het document leidde. Deze instelling heeft geen invloed op de functionaliteit van de PDF, maar de bestandsgrootte neemt wel af.

### Opruimen {#clean-up}

Selecteer **Opruimen** om onnodige punten uit het document te verwijderen.
Deze items bevatten elementen die verouderd of niet nodig zijn voor het beoogde gebruik van het document. Het verwijderen van bepaalde elementen kan ernstige gevolgen hebben voor de functionaliteit van de PDF. Standaard worden alleen elementen geselecteerd die geen invloed hebben op de functionaliteit. Gebruik de standaardselecties als u niet zeker weet wat de gevolgen zijn van het verwijderen van andere opties.

**Compressie**

Selecteer een van de volgende compressieopties voor Flate in het keuzemenu:

* Volledig bestand comprimeren
* Documentstructuur comprimeren
* Compressie verwijderen
* Compressie ongewijzigd laten

**Vloeiend van het Gebruik om stromen te coderen die niet** worden gecodeerd: Past Flate compressie op alle stromen toe die niet worden gecodeerd.

**verwerping Ongeldige Bladwijzers**: verwijdert referenties die aan pagina&#39;s in het document richten die worden geschrapt.

**verwerpt Benoemde Benoemde Doelen**: verwijdert genoemde bestemmingen die niet intern van binnen het document van de PDF worden van verwijzingen voorzien. Met deze optie wordt niet gecontroleerd op koppelingen van andere PDF-bestanden of websites.

**optimaliseer PDF voor Snelle Mening van het Web**: Herstructureert een document van PDF voor pagina-bij-a-tijd het downloaden (byte-dienen) van Webservers.

**in Streams die Codering LZW, Gebruik Flate in plaats daarvan** gebruiken: Past Flate compressie op alle inhoudsstromen en beelden toe die LZW het coderen gebruiken.

**Verwerp Ongeldige Verbindingen**: Verwijdert verbindingen die aan ongeldige bestemmingen springen.

**optimaliseer de Inhoud van de Pagina**: Zet alle eind-van-lijn karakters in ruimtekarakters om, die Flate compressie verbetert.

## Microsoft Excel-instellingen (alleen Windows) {#microsoft-excel-settings-windows-only}

Deze opties bepalen hoe Microsoft Excel-bestanden worden omgezet. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](#create-or-edit-file-type-settings) uit.

**probeert OpenOffice als Convertor van de Fallback**: Wanneer deze optie wordt geselecteerd en een omzetting die Microsoft Excel gebruikt ontbreekt of de gespecificeerde onderbreking bereikt, probeert de PDF Generator de omzetting door OpenOffice te gebruiken. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Bestandsnaamuitbreidingen**: Specificeert filename uitbreidingen voor dossiertypes, die door komma&#39;s worden gescheiden, die voor deze toepassing worden goedgekeurd. De standaardwaarde is `xls,xlsx` . Neem geen punt voor of spatie op tussen de extensies.

**creeer PDF/a-1a Volgzaam Dossier**: Dwingt het gebruik van het PDF/A-1b:2005 RGB Adobe PDF plaatsen.

**voegt Bladwijzers aan Adobe PDF** toe: Zet de werkbladnamen van Excel in referenties om. Deze optie is standaard ingeschakeld.

**Passend Werkblad aan Één enkele Pagina**: Vermindert de grootte van de tekst om het aantekenvel op één enkele pagina te passen.

**zet Volledig Werkboek** om: Zet alle aantekenvellen in het dossier van Excel om. Als u deze optie niet selecteert, wordt alleen de huidige pagina geconverteerd.

**de Macro&#39;s van de Looppas automatisch**: stelt om het even welke macro&#39;s in het document van Excel (zoals een macro in werking die de huidige tijd) alvorens het document opneemt om te zetten.

**zet de Informatie van het Document** om: Voegt PDF documenteigenschappen toe die op de documentinformatie in het brondossier worden gebaseerd. Dit omvat informatie zoals documenttitel, auteur, onderwerp, en sleutelwoorden.

**voegt Verbindingen aan Adobe PDF** toe: Zet hyperlinks in het brondossier in hyperlinks in het document van de PDF om.

**het Dossier van Source van de Band aan Adobe PDF**: Wanneer deze optie wordt geselecteerd, wordt het originele spreadsheet van Excel opgenomen als gehechtheid binnen het geproduceerde document van PDF.

**laat Toegankelijkheid en Reflow met Gelabelde Adobe PDF** toe: sluit markeringen binnen het document van PDF in om toegankelijkheid en opnieuw plaatsen toe te laten.

**lijst van de Toevoegingen van Excel** te laden: Door gebrek (voor veiligheidsredenen), worden geen toe:voegen-ins van Excel in werking gesteld wanneer een dossier van Excel in PDF wordt omgezet. Om bepaalde toe:voegen-ins van Excel toe te staan om tijdens omzetting te lopen, verstrek een komma-gescheiden lijst van de namen van toe:voegen-ins.

**Lijst van te zetten Werkbladen**: Wanneer dit vakje leeg is, zijn alle aantekenvellen in het spreadsheet van Excel inbegrepen in de geproduceerde PDF. Als u een subset van de werkbladen selectief wilt converteren, voert u een door komma&#39;s gescheiden lijst met werkbladnamen in.

## Microsoft PowerPoint-instellingen (alleen Windows) {#microsoft-powerpoint-settings-windows-only}

Deze opties bepalen hoe Microsoft PowerPoint-bestanden worden omgezet. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

**[!UICONTROL Try OpenOffice As Fallback Converter]**: wanneer deze optie is geselecteerd en een conversie met Microsoft PowerPoint mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie met OpenOffice. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**[!UICONTROL Filename Extensions]** - Geeft de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is ppt, pptx. Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Add Bookmarks To Adobe PDF]** - Hiermee converteert u PowerPoint-titels naar bladwijzers. Deze optie is standaard ingeschakeld.

**[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand. Deze optie is standaard uitgeschakeld.

**[!UICONTROL Enable Accessibility And Reflow With Tagged Adobe PDF]**: Hiermee sluit u tags in het PDF-bestand in. Deze optie is standaard uitgeschakeld.

**[!UICONTROL Convert Multimedia To PDF Multimedia]**: zet multimedia waar mogelijk om in PDF-multimedia. Deze optie is standaard ingeschakeld.

**[!UICONTROL Convert Speaker Notes]**: zet sprekersnotities om in PDF.

**[!UICONTROL Run Macros Automatically]**: voert eventuele macro&#39;s in het PowerPoint-document uit (zoals een macro die de huidige tijd invoegt) voordat het document wordt geconverteerd.

**[!UICONTROL PDF Layout Based On PowerPoint Printer Settings]**: gebruikt PowerPoint-printerinstellingen om het PDF-document op te maken.

**[!UICONTROL Add Links To Adobe PDF]** : de bestaande koppelingen blijven behouden wanneer het bestand wordt geconverteerd. De weergave van koppelingen is over het algemeen ongewijzigd. Koppelingen kunnen alleen worden gemaakt als de optie Toegankelijkheid inschakelen ook is geselecteerd. Deze optie is standaard uitgeschakeld.

**[!UICONTROL Save Slide Transitions In Adobe PDF]**: hiermee converteert u diaovergangen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Save Animations In Adobe PDF]**: hiermee slaat u geconverteerde animaties op in het PDF-bestand.

**[!UICONTROL Convert Hidden Slides To PDF Pages]** - Verborgen dia&#39;s worden omgezet.

**[!UICONTROL Create PDF/A-1a Compliant File]**: Dwingt het gebruik van de PDF/A-1b:2005 RGB Adobe PDF-instelling. Enkele PowerPoint-functies worden niet geconverteerd wanneer u een PDF-bestand maakt. Als een PowerPoint-overgang in Acrobat geen gelijkwaardige overgang heeft, wordt een vergelijkbare overgang vervangen. Als meerdere animatie-effecten zich in dezelfde dia bevinden, wordt één effect gebruikt. Paginaovergangen en vlieg-ins voor opsommingstekens worden omgezet.

## Microsoft-projectinstellingen (alleen Windows) {#microsoft-project-settings-windows-only}

Deze opties bepalen hoe Microsoft-projectbestanden worden geconverteerd. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](#create-or-edit-file-type-settings) uit.

1. **[!UICONTROL Filename Extensions:]** Hiermee geeft u de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `mpp` . Neem geen punt voor of spatie op tussen de extensies.

1. **[!UICONTROL Convert Document Information]**: voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.
1. **[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand.
1. **[!UICONTROL Create PDF/A-1a Compliant File]**: Dwingt het gebruik van de PDF/A-1b:2005 RGB Adobe PDF-instelling.
1. **[!UICONTROL Run Macros Automatically]**: voert eventuele macro&#39;s in het Microsoft Project-document uit (zoals een macro die de huidige tijd invoegt) voordat het document wordt geconverteerd.

## Microsoft Word-instellingen (alleen Windows) {#microsoft-word-settings-windows-only}

Deze opties bepalen hoe Microsoft Word-bestanden worden geconverteerd. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](#create-or-edit-file-type-settings) uit.

**[!UICONTROL Try OpenOffice As Fallback Converter]**: Wanneer deze optie is geselecteerd en een conversie met Microsoft Word mislukt of de opgegeven time-outlimiet bereikt, probeert PDF Generator de conversie uit te voeren met OpenOffice. Als de conversie met OpenOffice mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**[!UICONTROL Filename Extensions]** - Geeft de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `doc,docx,rtf,txt` . Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Add Bookmarks To Adobe PDF]** - koppen worden omgezet in bladwijzers. Deze optie is standaard ingeschakeld.

**[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand.

**[!UICONTROL Convert Cross-References And Table Of Contents To Links]**: hiermee worden alle kruisverwijzingen en items in de inhoudsopgave geconverteerd naar koppelingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Enable Accessibility And Reflow With Tagged Adobe PDF]**: Hiermee sluit u tags in het PDF-bestand in. Deze optie is standaard ingeschakeld.

**[!UICONTROL Create PDF/A-1a Compliant File]**: Als deze optie is geselecteerd, wordt de Adobe PDF-instelling PDF/A-1b:2005 RGB gebruikt.

**[!UICONTROL Run Macros Automatically]**: voert eventuele macro&#39;s in het Word-document uit (zoals een macro die de huidige tijd invoegt) voordat het document wordt geconverteerd.

**[!UICONTROL Preserve Document Markup In Adobe PDF]** - Hiermee converteert u opmaak in het Word-document naar annotaties in het PDF-bestand.

**[!UICONTROL Add Links To Adobe PDF]**: hiermee zet u hyperlinks in het bronbestand om in hyperlinks in het PDF-document.

**[!UICONTROL Convert Footnote And Endnote Links]**: hiermee maakt u koppelingen van de voetnoot- en eindnootverwijzingen naar notities in het PDF-document.

**[!UICONTROL Convert Displayed Comments To Notes in Adobe PDF]** - Opmerkingen in het Word-document worden geconverteerd naar tekstnotities in het PDF-document.

**[!UICONTROL Enable Advanced Tagging]**: voegt geavanceerde codes toe voor verbeterde toegankelijkheid.

**[!UICONTROL Convert All Styles To Bookmarks]** - Alle stijlen in het Word-document worden omgezet in bladwijzers in het PDF-document.

**[!UICONTROL Convert specified styles to bookmarks]**: hiermee worden de stijlen die u in het veld **[!UICONTROL Styles with levels]** definieert, geconverteerd naar bladwijzers in het document PDF.

**[!UICONTROL Styles With Levels]** - Geeft aan welke stijlen in het Word-document worden omgezet in bladwijzers in het PDF-document. Hiermee geeft u ook het niveau van de bladwijzers op. Als u deze functie wilt gebruiken, schakelt u de optie **[!UICONTROL Convert All Styles To Bookmarks]** uit en geeft u de stijlnamen op in de volgende indeling:

**styleName1=level1 [, styleName2=level2..]**

Als de naam van een Microsoft Word-stijl een komma (,) of een gelijkteken (=) bevat, plaatst u voor de speciale tekens het escape-teken (&quot;\_). Geef bijvoorbeeld een stijl met de naam &quot;Kop, 1&quot; op als Kop\, 1.

**Codering PDFMaker van Acrobat:** specificeert het coderingstype van de invoer zonder tekst dossiers aan Acrobat PDFMaker. Als u bijvoorbeeld een bestand met UTF-8-codering gebruikt, bereikt u de beste resultaten met UTF-8.

## Microsoft Visio-instellingen (alleen Windows) {#visio}

**zet de Informatie van het Document** om: Voegt documentinformatie van het de dialoogvakje van Eigenschappen van het brondossier, met inbegrip van titel, onderwerp, auteur, sleutelwoorden, manager, bedrijf, categorie, en commentaren toe. Deze optie is standaard ingeschakeld. Deze optie is standaard ingeschakeld.

**voegt Verbindingen aan Adobe PDF** toe: Behoudt alle verbindingen. Deze optie is standaard ingeschakeld.

**voegt Bladwijzers aan Adobe PDF** toe: Zet rubrieken in referenties om. Deze optie is standaard ingeschakeld.

**maak het Dossier van Source aan Adobe PDF** vast: Voegt het brondossier aan het dossier van PDF als gehechtheid toe.

**sluit altijd Lagen in Adobe PDF** af: Vlakt alle lagen van Visio af.

**zet Alle Pagina&#39;s** om: Zet alle pagina&#39;s van het dossier van Visio om.

**Open het Comité van Lagen wanneer Bekeken in Adobe Acrobat**: Als de lagen van Visio niet worden afgevlakt, opent een venster waar u de lagen kunt specificeren die in het dossier van de PDF wanneer geopend gebruikend Acrobat worden bewaard. Deze optie is standaard ingeschakeld.

**creeer PDF/a-1b Volgzaam Dossier**: Dwingt het gebruik van Adobe PDF die PDF/A-1b plaatsen:2005 (RGB).

**zet Commentaren in de Commentaren van Adobe PDF** om: Zet de nota&#39;s van Visio in PDF commentaren.

## Microsoft Publisher-instellingen (alleen Windows) {#microsoft-publisher-settings-windows-only}

Deze opties bepalen hoe Microsoft Publisher-bestanden worden geconverteerd. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](#create-or-edit-file-type-settings) uit.

**[!UICONTROL Filename Extensions]** - Geeft de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `pub` . Neem geen punt voor of spatie op tussen de extensies.

## AutoCAD-instellingen (alleen Windows) {#autocad-settings-windows-only}

Deze opties bepalen hoe AutoCAD-bestanden worden omgezet. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

**[!UICONTROL Filename Extensions]** - Geeft de bestandsextensies op voor bestandstypen, gescheiden door komma&#39;s, die worden geaccepteerd voor deze toepassing. De standaardwaarde is `dwg` . Neem geen punt voor of spatie op tussen de extensies.

**[!UICONTROL Convert Document Information]**: voegt documentinformatie uit het dialoogvenster Eigenschappen van het bronbestand toe, zoals titel, onderwerp, auteur, trefwoorden, manager, bedrijf, categorie en opmerkingen. Deze optie is standaard ingeschakeld.

**[!UICONTROL Add Bookmarks To Adobe PDF]** - koppen worden omgezet in bladwijzers.

**[!UICONTROL Always Flatten Layers In Adobe PDF]**: hiermee worden alle AutoCAD-lagen samengevoegd.

**[!UICONTROL Open Layers Pane When Viewed In Adobe Acrobat]** - Geeft de lagenstructuur weer wanneer de PDF in Acrobat wordt geopend.

**[!UICONTROL Convert All Layouts]** - Alle lay-outs worden opgenomen in de PDF.

**[!UICONTROL Convert Model Space to 3D]**: als deze optie is geselecteerd, wordt de indeling van de modelruimte omgezet in een 3D-annotatie in de PDF.

**[!UICONTROL Add Links To Adobe PDF]**: als deze optie is geselecteerd, blijven alle koppelingen behouden.

**[!UICONTROL Attach Source File To Adobe PDF]**: voegt het bronbestand als bijlage toe aan het PDF-bestand.

**[!UICONTROL Create PDF/A-1b Compliant File]**: Dwingt het gebruik van de PDF/A-1b Adobe PDF-instelling.

**[!UICONTROL Convert All Layers]**: Standaard zet PDF Generator alleen de standaardlaag AutoCAD-bestanden om in PDF in plaats van alle lagen in het bestand. Selecteer deze optie als u alle lagen van het bestand wilt converteren.

**[!UICONTROL Embed Scale Information]**: behoudt tekenschaalgegevens.

**[!UICONTROL Convert Current Layout]**: neemt alleen de huidige lay-out in de PDF op.

**[!UICONTROL List Of AutoCAD Layouts To Convert]**: Een AutoCAD-tekening kan meerdere lay-outs hebben. Als dit vak leeg is, worden alle lay-outs in de AutoCAD-tekening opgenomen in het gegenereerde PDF-document. Als u een subset van de lay-outs selectief wilt omzetten, voert u een door komma&#39;s gescheiden lijst met indelingsnamen in.

## OpenOffice-instellingen {#openoffice-settings}

Deze opties bepalen hoe de dossiers OpenOffice worden omgezet. Voor instructies over de toegang tot van deze opties, zie [ creeer of geef dossiertype montages ](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings) uit.

**probeert PDFMaker als Convertor van de Fallback**: Wanneer deze optie wordt geselecteerd en een omzetting die OpenOffice gebruikt ontbreekt of de gespecificeerde onderbrekingsgrens bereikt, probeert de PDF Generator de omzetting door PDFMaker te gebruiken. Als de conversie met PDFMaker mislukt of de opgegeven time-outlimiet bereikt, wordt een uitzondering naar het logbestand geschreven.

**Bestandsnaamuitbreidingen**: specificeer filename uitbreidingen voor dossiertypes, die door komma&#39;s worden gescheiden, die voor deze toepassing worden goedgekeurd. De standaardwaarde is `odt,odp,ods,odg,odf,sxw,sxi,sxd` . Neem geen punt voor of spatie op tussen de extensies.

**Waaier**: Zet alle pagina&#39;s om of specificeer bepaalde pagina&#39;s of een paginabereik. Als er geen paginabereik is gedefinieerd, worden alle pagina&#39;s geconverteerd. Als u een paginabereik wilt exporteren, gebruikt u de indeling 3-6. Als u één pagina wilt exporteren, gebruikt u de indeling 7;9;11. U kunt een combinatie van paginabereiken en enkele pagina&#39;s exporteren met een indeling als 3-6;8;10;12.

**de Richtlijn van de Pagina**: Voor gewone tekstdossiers, selecteer of portret of landschap voor het omgezette document van PDF.

**Beelden**: Vorm hoe de beelden worden omgezet. EPS-afbeeldingen met ingesloten voorvertoningen worden alleen als voorvertoningen geëxporteerd. EPS-afbeeldingen zonder ingesloten voorvertoningen worden geëxporteerd als lege plaatsaanduidingen. Bij compressie zonder verlies van afbeeldingen blijven alle pixels behouden. Met JPEG-compressie van afbeeldingen en een hoge kwaliteit blijven bijna alle pixels behouden. Bij een laag kwaliteitsniveau gaan sommige pixels verloren en worden artefacten geïntroduceerd, maar de bestandsgrootte neemt af.

**Algemeen**: Laat de opties toe om geëtiketteerde PDF om te zetten of schrijver uit te voeren en FormCalc documentnota&#39;s, de gevolgen van de diavergang van de Druk, of lege pagina&#39;s in de PDF. Wanneer tags worden geëxporteerd, kan de bestandsgrootte aanzienlijk toenemen. Sommige tags die worden geëxporteerd, zijn inhoudsopgaven, hyperlinks en besturingselementen.

U kunt ook opgeven hoe formulieren worden verzonden. De opties zijn XML, FDF, PDF of HTML. Dit het plaatsen treedt het bezit van URL van de controle met voeten dat u in het document plaatst. U kunt slechts één veelgebruikte instelling selecteren voor het PDF-document:

* PDF (het hele document wordt verzonden)
* FDF (verzendt de besturingsinhoud)
* HTML
* XML

**geëtiketteerde PDF**: Laat verwezenlijking van geëtiketteerde PDF van documenten OpenOffice toe. Gelabelde PDF bevat informatie over de structuur van de documentinhoud. Dit kan helpen bij het weergeven van het document op apparaten met verschillende schermen en bij het gebruik van schermlezersoftware. Het helpt toegankelijkheidssoftware ook diverse nuttige bewerkingen uit te voeren met het PDF-document, zoals de inhoud van het PDF-document hardop lezen.

**de Nota&#39;s van de Uitvoer**: Zet de nota&#39;s in documenten OpenOffice in nota&#39;s in het geproduceerde document van de PDF om.

**Gevolgen van de Overgang van het Gebruik**: Zet de gevolgen van de diavergang in presentaties OpenOffice in overeenkomstige PDF overgangsgevolgen om.

**legt Forms in Formaat** voor: Creeert een vorm van de PDF die kan worden ingevuld en door de gebruiker van het document van de PDF gedrukt.

**de Uitvoer automatisch Ingevoegde Lege Pagina&#39;s**: Wanneer deze optie wordt geselecteerd, automatisch opgenomen blanco pagina&#39;s zijn inbegrepen in het geproduceerde document van de PDF. Dit is handig als u een PDF-document dubbelzijdig afdrukt. Een boek kan bijvoorbeeld zo worden geconfigureerd dat de eerste pagina van het hoofdstuk altijd begint op een pagina met een oneven nummer. Als het vorige hoofdstuk eindigt op een oneven pagina, voegt OpenOffice een lege even pagina in. Met deze optie bepaalt u of de even pagina in de gegenereerde PDF wordt opgenomen.

## Overige toepassingsinstellingen (alleen Windows) {#other-applications-settings-windows-only}

U kunt de instellingen voor andere toepassingen niet wijzigen via de beheerconsole, maar wel via de bestandsextensies voor de ondersteunde bestandstypen. Voor instructies over de toegang tot van deze montages, zie [ creeer of geef dossiertype montages ](https://help.adobe.com/en_US/AEMForms/6.1/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7e42.2.html) uit.

* Corel WordPerfect: `wpd`
* PageMaker Adobe: `pmd, pm6, p65, pm`
* Adobe FrameMaker: `fm`
* Adobe Photoshop: `psd`

Ondersteuning voor deze bestandstypen moet mogelijk worden aangepast. Voor meer informatie, zie &quot;Toevoegend Steun voor de Extra Inheemse Formaten van het Dossier&quot;in [ Programmering met AEM vormen ](https://www.adobe.com/go/learn_aemforms_programming_62).

Voor hulp bij het vormen van een PDFG netwerkprinter, zie [ Opstelling een PDFG netwerkprinter (Vensters slechts) ](/help/forms/using/admin-help/setting-pdfg-network-printer-windows.md).
