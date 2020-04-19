---
title: Adobe PDF-instellingen configureren
seo-title: Adobe PDF-instellingen configureren
description: Leer hoe u Adobe PDF-instellingen configureert.
seo-description: Leer hoe u Adobe PDF-instellingen configureert.
uuid: 980c9d6a-f75e-4e7d-b050-d2d07a10ef33
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ab018b6d-0233-4439-bb75-58c5421d769a
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Adobe PDF-instellingen configureren{#configuring-adobe-pdf-settings}

Op de pagina Instellingen Adobe PDF worden de conversie-instellingen weergegeven die u voor uw bronnen kunt opgeven. U kunt alle vooraf gedefinieerde PDF-instellingen gebruiken of zelf PDF-instellingen maken. De PDF-instellingen bepalen nauwkeurig hoe bestanden worden geconverteerd en de resulterende PDF-structuur en -functies. Adobe PDF-instellingen werden voorheen Distiller®-parameters of taakopties genoemd.

Op de pagina Adobe PDF-instellingen kunt u de volgende taken uitvoeren:

* Geef de vooraf gedefinieerde PDF-instellingen weer. (Zie [Vooraf gedefinieerde PDF-instellingen](configuring-pdf-settings.md#about-the-predefined-pdf-settings).)
* Maak een PDF-instelling of bewerk een instelling die u eerder hebt gemaakt. (Zie PDF-instellingen [](configuring-pdf-settings.md#add-or-edit-pdf-settings)toevoegen of bewerken.)
* Geef de standaard PDF-instellingen op. (Zie De [standaardinstellingen](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings)wijzigen)
* Upload een PDF-instellingenbestand naar de server. (Zie PDF-instellingen [](configuring-pdf-settings.md#upload-pdf-settings)uploaden.)
* Aangepaste PDF-instellingen verwijderen. (Zie PDF-instellingen [](configuring-pdf-settings.md#delete-pdf-settings)verwijderen.)
* Proloog- en epiloogbestanden uploaden en downloaden. (Zie [Prologue- en epiloogbestanden](configuring-pdf-settings.md#uploading-and-downloading-prologue-and-epilogue-files)uploaden en downloaden.)

Adobe PDF-instellingen zijn alleen van toepassing op conversies op basis van PDFMaker. Deze omvatten de volgende omzettingen:

* Microsoft Word-document (DOC, DOCX, RTF, TXT)
* Microsoft Excel-document (XLS, XLSX)
* Microsoft PowerPoint-document (PPT, PPTX)
* Microsoft Project-document (MPP)
* Microsoft Visio-document (VSD)

>[!NOTE]
>
>Als u OpenOffice gebruikt om bovenstaande indelingen te converteren, worden de Adobe PDF-instellingen niet toegepast.

## Vooraf gedefinieerde PDF-instellingen {#about-the-predefined-pdf-settings}

De PDF Generator biedt verschillende vooraf gedefinieerde PDF-instellingen voor uw gebruik. U kunt deze vooraf gedefinieerde instellingen niet wijzigen. u kunt echter een instelling maken op basis van een bestaande instelling door de instelling te bewerken en onder een andere naam op te slaan.

**Afdrukken met hoge kwaliteit:** Hiermee maakt u PDF-bestanden voor uitvoer van hoge kwaliteit. Deze instelling:

* Hiermee worden kleuren- en grijswaardenafbeeldingen gedownsampled met 300 dpi
* Hiermee worden monochrome afbeeldingen gedownsampled met 1200 dpi
* afdrukken naar een hogere afbeeldingsresolutie
* gebruikt andere instellingen om de maximale hoeveelheid informatie over het oorspronkelijke document te behouden.

Deze PDF-bestanden kunnen worden geopend in Adobe Acrobat 5 en Adobe Acrobat Reader® 5 of hoger.

**Grote pagina&#39;s:** Hiermee maakt u PDF-documenten die geschikt zijn voor het betrouwbaar weergeven en afdrukken van technische tekeningen die groter zijn dan 200 x 200 inch. Gemaakte PDF-documenten kunnen worden geopend in Adobe Acrobat Professional en Acrobat Standard, versie 7 of hoger en Adobe Reader 7 of hoger.

**PDF/A-1B 2005 CMYK / PDF/A-1B 2005 RGB:** Hiermee wordt gecontroleerd of binnenkomende taken voldoen aan de ISO-standaard voor langetermijnbewaring (archivering) van elektronische documenten en worden alleen PDF/A-bestanden gemaakt als deze voldoen. Deze bestanden worden vooral gebruikt voor archivering. Compatibele bestanden kunnen alleen tekst, rasterafbeeldingen en vectorobjecten bevatten. ze kunnen geen versleuteling en scripts bevatten. Bovendien moeten alle lettertypen zijn ingesloten, zodat de documenten kunnen worden geopend en weergegeven zoals ze zijn gemaakt. PDF/A-1b gebruikt PDF 1.4 en converteert alle kleuren naar CMYK of RGB, afhankelijk van de standaard die u kiest. PDF-bestanden die met dit instellingenbestand zijn gemaakt, kunnen worden geopend in Acrobat 5 en Acrobat Reader 5 en hoger. Zie Adobe en industriestandaarden voor meer informatie over PDF/A.

**PDF/X-1a 2001:** Hiermee worden inkomende taken gecontroleerd op compatibiliteit met PDF/X-1a en worden alleen PDF-bestanden gemaakt als deze voldoen. PDF/X-1a is een ISO-standaard voor het uitwisselen van grafische inhoud. PDF/X-1a vereist dat alle fonts worden ingesloten, dat de juiste PDF-vakken worden opgegeven en dat kleuren worden weergegeven als CMYK- of steunkleuren. PDF-bestanden die voldoen aan de PDF/X-1a-vereisten, zijn gericht op een specifieke uitvoervoorwaarde, zoals web-offsetdrukwerk volgens de specificaties voor Web-offsetpublicaties. Zie Adobe en industriestandaarden voor meer informatie over PDF/X.

**PDF/X-3 2002:** Hiermee worden inkomende taken gecontroleerd op PDF/X-3-compatibiliteit en worden alleen PDF-bestanden gemaakt als deze voldoen. Net als PDF/X-1a is PDF/X-3 een ISO-standaard voor het uitwisselen van grafische inhoud. Het belangrijkste verschil is dat PDF/X-3 apparaatonafhankelijke kleuren ondersteunt.

**Drukwerkkwaliteit:** Hiermee maakt u PDF-bestanden voor afdrukproductie van hoge kwaliteit (bijvoorbeeld op een zetmachine of plaatmachine). In dit geval is bestandsgrootte geen overweging. Het doel is om in een PDF-bestand alle gegevens te behouden die een drukker of prepress-bureau nodig heeft om het document correct af te drukken. Deze set opties:

* Hiermee worden kleuren- en grijswaardenafbeeldingen gedownsampled met 300 dpi
* Hiermee worden monochrome afbeeldingen gedownsampled met 1200 dpi
* Hiermee worden subsets ingesloten van alle lettertypen die in het document worden gebruikt
* afdrukken tot een hogere beeldresolutie,
* roteert pagina&#39;s niet automatisch op basis van de richting van de tekst of de opmerkingen in de DSC-indeling (Document Structure Conventions)
* gebruikt andere instellingen om de maximale hoeveelheid informatie over het oorspronkelijke document te behouden.

Afdruktaken mislukken als ze fonts hebben die niet kunnen worden ingesloten. Deze PDF-bestanden kunnen worden geopend in Acrobat 5 en Acrobat Reader 5 en hoger.

>[!NOTE]
>
>Voordat u een PDF-bestand maakt dat naar een commerciële drukker of prepress-bureau wordt verzonden, bepaalt u de uitvoerresolutie en andere instellingen of vraagt u een .joboptions-bestand met de aanbevolen instellingen aan. Mogelijk moet u de Adobe PDF-instellingen aanpassen voor een bepaald bureau en een eigen .joboptions-bestand meeleveren.

**Kleinste bestandsgrootte:** Hiermee maakt u PDF-bestanden voor weergave op het web of een intranet of voor distributie via een e-mailsysteem voor weergave op het scherm. Bij deze set opties worden compressie, downsampling en een relatief lage afbeeldingsresolutie gebruikt. Alle kleuren worden omgezet in sRGB en er worden geen lettertypen ingesloten, tenzij dat nodig is. Ook worden bestanden geoptimaliseerd voor byteserving. Deze PDF-bestanden kunnen worden geopend in Acrobat 5 en Acrobat Reader 5.0 en hoger.

**Standaard:** Hiermee maakt u PDF-bestanden die worden afgedrukt op desktopprinters of digitale kopieerapparaten, die worden gepubliceerd op een cd of die als een proefdruk naar een klant worden gestuurd. Bij deze set opties worden compressie en downsampling gebruikt om de bestandsgrootte te beperken. Subsets met alle lettertypen die in het bestand worden gebruikt, worden geconverteerd naar sRGB en afgedrukt naar een gemiddelde resolutie om een redelijk nauwkeurige weergave van het oorspronkelijke document te maken. Subsets van Microsoft Windows-lettertypen worden niet standaard ingesloten. Deze PDF-bestanden kunnen worden geopend in Acrobat 5 en Acrobat Reader 5.0 en hoger.

## PDF-instellingen toevoegen of bewerken {#add-or-edit-pdf-settings}

PDF-instellingen bepalen nauwkeurig hoe bestanden worden geconverteerd en de resulterende PDF-structuur en -functies. Definieer een nieuwe PDF-instelling of bewerk een instelling die u eerder hebt gemaakt. U kunt vooraf gedefinieerde instellingen niet wijzigen, maar u kunt een instelling maken op basis van een bestaande instelling door de instelling te bewerken en onder een andere naam op te slaan.

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF-instellingen.
1. Klik op Nieuw of klik op de naam van een bestaande instelling.
1. Voer op de pagina Nieuwe Adobe PDF-instellingen/Adobe PDF-instellingen bewerken de vereiste informatie in deze secties in:

   [Algemene opties](configuring-pdf-settings.md#general-options)

   [Afbeeldingsopties](configuring-pdf-settings.md#images-options)

   [Fontopties](configuring-pdf-settings.md#fonts-options)

   [Kleuropties](configuring-pdf-settings.md#color-options)

   [Geavanceerde opties](configuring-pdf-settings.md#advanced-options)

   [Standaardrapporterings- en compatibiliteitsopties](configuring-pdf-settings.md#standards-reporting-and-compliance-options)

   [Oorspronkelijke weergaveopties](configuring-pdf-settings.md#initial-view-options)

   Als u naar een andere sectie wilt gaan, klikt u op de koppeling op de webpagina of gebruikt u de knoppen Volgende en Vorige.

1. Nadat u de informatie in alle secties hebt voltooid, klikt u op Opslaan of Opslaan als en geeft u een naam voor de instelling op.

## PDF-instellingen uploaden {#upload-pdf-settings}

U kunt PDF-instellingen beschikbaar hebben op de server van de PDF Generator door deze te uploaden vanaf een lokale computer of een netwerklocatie.

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF-instellingen en klik op Uploaden.
1. Klik op de pagina Adobe PDF-instellingen uploaden op Bladeren, zoek het bestand met PDF-instellingen en klik op Openen.
1. Klik op OK en vervolgens nogmaals op OK.

## PDF-instellingen verwijderen {#delete-pdf-settings}

U kunt PDF-instellingen permanent verwijderen als deze niet meer vereist zijn.

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF-instellingen.
1. Schakel het selectievakje naast de instelling die u wilt verwijderen in. U kunt meerdere instellingen selecteren.
1. Klik op Verwijderen en klik nogmaals op Verwijderen op de pagina Bevestiging verwijderen.

## Algemene opties {#general-options}

Gebruik de algemene opties om de versie van Acrobat op te geven die u wilt gebruiken voor bestandscompatibiliteit en andere bestands- en apparaatopties. Zie PDF-instellingen [toevoegen of bewerken voor informatie over het openen van de algemene opties](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Bestandsopties {#file-options}

**Compatibiliteit:** Het compatibiliteitsniveau van het PDF-bestand. Voor documenten die op grote schaal worden gedistribueerd, kunt u wellicht beter Acrobat 4 (PDF 1.3) of Acrobat 5 (PDF 1.4) selecteren om ervoor te zorgen dat alle gebruikers het document kunnen weergeven en afdrukken. Bestanden die u maakt met Acrobat 5-compatibiliteit of hoger, zijn mogelijk niet compatibel met eerdere versies van Acrobat. In de volgende subsecties ziet u enkele verschillen tussen PDF-bestanden die zijn gemaakt met verschillende compatibiliteitsniveaus van Acrobat.

<table>
 <tbody>
  <tr>
   <th><p>Acrobat 4 (PDF 1.3)</p> </th>
   <th><p>Acrobat 5 (PDF 1.4)</p> </th>
   <th><p>Acrobat 6 (PDF 1.5)</p> </th>
   <th><p>Acrobat 7 (PDF 1.6) en Acrobat 8 (PDF 1.7)</p> </th>
  </tr>
  <tr>
   <td><p>Kan worden geopend met Acrobat 3.0 en Acrobat Reader 3.0 en hoger.</p> </td>
   <td><p>Kan worden geopend met Acrobat 3.0 en Acrobat Reader 3.0 en hoger. Functies die specifiek zijn voor latere versies kunnen verloren gaan of niet zichtbaar zijn.</p> </td>
   <td><p>De meeste kunnen worden geopend met Acrobat 4 en Acrobat Reader 4.0 en hoger. Functies die specifiek zijn voor latere versies kunnen verloren gaan of niet zichtbaar zijn.</p> </td>
   <td><p>De meeste kunnen worden geopend met Acrobat 4 en Acrobat Reader 4.0 en hoger. Functies die specifiek zijn voor latere versies kunnen verloren gaan of niet zichtbaar zijn.</p> </td>
  </tr>
  <tr>
   <td><p>Kan geen illustraties bevatten die actieve transparantie-effecten gebruiken. Transparantie moet worden afgevlakt voordat u naar PDF 1.3 gaat.</p> </td>
   <td><p>Ondersteunt het gebruik van actieve transparantie in illustraties. (Met de Acrobat Distiller-functie wordt transparantie afgevlakt.)</p> </td>
   <td><p>Ondersteunt het gebruik van actieve transparantie in illustraties. (Met de Acrobat Distiller-functie wordt transparantie afgevlakt.)</p> </td>
   <td><p>Ondersteunt het gebruik van actieve transparantie in illustraties. (Met de Acrobat Distiller-functie wordt transparantie afgevlakt.)</p> </td>
  </tr>
  <tr>
   <td><p>Lagen worden niet ondersteund.</p> </td>
   <td><p>Lagen worden niet ondersteund.</p> </td>
   <td><p>Lagen blijven behouden wanneer u PDF-bestanden maakt van toepassingen die het genereren van gelaagde PDF-documenten ondersteunen, zoals Adobe Illustrator® CS of Adobe InDesign® CS en hoger.</p> </td>
   <td><p>Lagen blijven behouden wanneer u PDF-bestanden maakt vanuit toepassingen die het genereren van gelaagde PDF-documenten, zoals Illustrator CS of InDesign CS en hoger, ondersteunen.</p> </td>
  </tr>
  <tr>
   <td><p>DeviceN-kleurruimte met 8 kleurstoffen wordt ondersteund.</p> </td>
   <td><p>DeviceN-kleurruimte met 8 kleurstoffen wordt ondersteund.</p> </td>
   <td><p>DeviceN-kleurruimte met maximaal 31 kleuren wordt ondersteund.</p> </td>
   <td><p>DeviceN-kleurruimte met maximaal 31 kleuren wordt ondersteund.</p> </td>
  </tr>
  <tr>
   <td><p>Multibyte-lettertypen kunnen worden ingesloten. (In Distiller worden de lettertypen tijdens het insluiten omgezet.)</p> </td>
   <td><p>Multibyte-lettertypen kunnen worden ingesloten.</p> </td>
   <td><p>Multibyte-lettertypen kunnen worden ingesloten.</p> </td>
   <td><p>Multibyte-lettertypen kunnen worden ingesloten.</p> </td>
  </tr>
  <tr>
   <td><p>40-bits RC4-beveiliging wordt ondersteund.</p> </td>
   <td><p>128-bits RC4-beveiliging wordt ondersteund.</p> </td>
   <td><p>128-bits RC4-beveiliging wordt ondersteund.</p> </td>
   <td><p>128-bits RC4- en 128-bits AES-beveiliging (Advanced Encryption Standard) worden ondersteund.</p> </td>
  </tr>
 </tbody>
</table>

**Compressie op objectniveau:** Hiermee consolideert u kleine objecten (elk zijn zelf niet gecomprimeerd) tot streams die vervolgens efficiënt kunnen worden gecomprimeerd.

**Uit:** Hiermee comprimeert u geen structuurgegevens in het PDF-document. Selecteer deze optie als u wilt dat gebruikers met Acrobat 5 en hoger door bladwijzers en andere structuurgegevens kunnen navigeren en ermee kunnen werken.

**Alleen tags:** Hiermee comprimeert u structuurgegevens in het PDF-document. Als u deze optie gebruikt, resulteert dit in een PDF-bestand dat kan worden geopend en afgedrukt met Acrobat 5. Gebruikers kunnen geen toegankelijkheid, structuur of gecodeerde PDF-gegevens weergeven in Acrobat 5 of Acrobat Reader 5.0, maar ze kunnen deze gegevens wel weergeven in Acrobat 6 en Adobe Reader 6.0.

**Pagina&#39;s automatisch roteren:** Hiermee stelt u de automatische rotatie van pagina&#39;s in op basis van de richting van de tekst- of DSC-opmerkingen. Sommige pagina&#39;s (zoals pagina&#39;s die tabellen bevatten) vereisen bijvoorbeeld dat de gebruiker deze pagina&#39;s zijdelings leest. Selecteer Afzonderlijk om elke pagina te roteren op basis van de richting van de tekst op die pagina. Selecteer Collectief op bestand om alle pagina&#39;s in het document te roteren op basis van de richting van de meeste tekst.

>[!NOTE]
>
>Als DSC-opmerkingen verwerken is geselecteerd in de Geavanceerde instellingen en als opmerkingen over de afdrukstand zijn opgenomen in %%Viewing Orientation, hebben deze opmerkingen voorrang bij het bepalen van de afdrukstand van de pagina.

**Binding:** Hiermee geeft u aan of een PDF-bestand met linker- of rechterbinding moet worden weergegeven. Deze instelling is van invloed op de weergave van pagina&#39;s in de indeling Pagina naast elkaar - Doorlopende lay-out en de weergave van miniaturen naast elkaar.

**Resolutie:** Hiermee stelt u de emulatie in voor de resolutie van een printer voor invoerbestanden die hun gedrag aanpassen op basis van de resolutie van de printer waarop ze afdrukken. Voor de meeste invoerbestanden leidt een hogere resolutie-instelling tot grotere PDF-bestanden van hogere kwaliteit, en een lagere instelling resulteert in kleinere PDF-bestanden van lagere kwaliteit. Meestal bepaalt de resolutie het aantal stappen in een verloop of overvloeiing. U kunt een waarde tussen 72 en 4000 invoeren. Deze instelling blijft de standaardinstelling, tenzij u het PDF-bestand wilt afdrukken op een specifieke printer en u de resolutie wilt emuleren die in het oorspronkelijke invoerbestand is gedefinieerd.

>[!NOTE]
>
>Als u de resolutie-instelling verhoogt, wordt het bestand groter en kan de verwerkingstijd van sommige bestanden iets langer worden.

**Alle pagina&#39;s of pagina&#39;s van:** Hiermee geeft u op welke pagina&#39;s u wilt converteren. Laat het vak Aan leeg om een bereik te maken van het paginanummer dat u hebt ingevoerd in het vak Van tot het einde van het bestand.

**Optimaliseren voor snelle weergave op het web:** Hiermee deelt u het bestand opnieuw in, zodat het per pagina kan worden gedownload van webservers (byte serving). Met deze optie comprimeert u tekst en lijnen, ongeacht de compressie-instellingen op het tabblad Afbeeldingen die u hebt geselecteerd. Compressie leidt tot snellere toegang en weergave wanneer het bestand wordt gedownload van het web of een netwerk. Deze optie is standaard niet ingeschakeld.

### Standaardpaginaformaat {#default-page-size}

Met de opties bij Standaardpaginaformaat geeft u het paginaformaat op dat moet worden gebruikt wanneer het oorspronkelijke bestand geen formaat bevat. Adobe PostScript-bestanden bevatten deze informatie meestal, behalve EPS-bestanden (Encapsulated PostScript) die een selectiekadergrootte hebben, maar geen paginaformaat. Het maximale paginaformaat is 31.800.000 inch (15.000.000 cm) in beide richtingen. Met deze opties configureert u het standaardpaginaformaat:

**Breedte:** Breedte van de pagina

**Hoogte:** Hoogte van de pagina

**Eenheden:** Eenheden die moeten worden gebruikt voor de instellingen voor breedte en hoogte

## Afbeeldingsopties {#images-options}

Met de opties bij Afbeeldingen geeft u compressie en resampling voor afbeeldingen op. U kunt met deze opties experimenteren om een juiste balans te vinden tussen bestandsgrootte en afbeeldingskwaliteit. Zie PDF-instellingen [toevoegen of bewerken voor informatie over het openen van de afbeeldingsinstellingen](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Met deze opties configureert u afbeeldingen in kleur, grijswaarden en monochroom:

**Downsample:** Stel een waarde in voor elk type afbeelding. In PDF Generator worden pixels in een voorbeeldgebied gecombineerd om afbeeldingen in kleur, grijswaarden of monochroom te downsamplen. Op deze manier wordt één grotere pixel gemaakt. Geef de resolutie van het uitvoerapparaat op in dpi (dots per inch) en voer een resolutie in dpi in het tekstvak Voor afbeeldingen boven in. Voor afbeeldingen met een resolutie die hoger is dan deze drempelwaarde, combineert PDF Generator indien nodig pixels om de resolutie van de afbeelding (pixels per inch) tot de opgegeven dpi-instelling te beperken. Selecteer Uit om downsampling uit te schakelen. Hier volgen de opties:

**Gemiddelde downsampling op:** Hiermee wordt het gemiddelde genomen van de pixels in een monstergebied en wordt het gehele gebied vervangen door de gemiddelde pixelkleur bij de opgegeven resolutie.

**Bicubische downsampling naar:** Gebruikt een gewogen gemiddelde om pixelkleur te bepalen en geeft gewoonlijk betere resultaten dan de eenvoudige het gemiddelde nemen methode van downsampling. Bicubisch is de langzaamste maar meest nauwkeurige methode en resulteert in de meest vloeiende kleurovergangen.

**Subsampling naar:** Hiermee selecteert u een pixel in het midden van het monstergebied en vervangt u het gehele gebied door die pixel bij de opgegeven resolutie. Subsampling vermindert significant de omzettingstijd in vergelijking met downsampling, maar het resulteert in beelden die minder vlot en ononderbroken zijn.

De resolutie-instelling voor kleur en grijswaarden moet 1,5 tot 2 keer de rasterliniatuur zijn waarmee het bestand wordt afgedrukt. (Als u deze aanbevolen resolutie-instelling niet overschrijdt, worden afbeeldingen zonder rechte lijnen of geometrische of herhalende patronen niet beïnvloed door een lagere resolutie.) De resolutie voor monochrome afbeeldingen moet gelijk zijn aan die van het uitvoerapparaat. Houd er echter rekening mee dat als u een monochrome afbeelding opslaat met een resolutie die hoger is dan 1500 dpi, de bestandsgrootte toeneemt zonder dat de beeldkwaliteit merkbaar toeneemt.

Overweeg ook of gebruikers een pagina moeten vergroten. Als u bijvoorbeeld een PDF-document van een kaart maakt, kunt u een hogere afbeeldingsresolutie gebruiken, zodat gebruikers kunnen inzoomen op de kaart.

>[!NOTE]
>
>Het berekenen van nieuwe beeldpixels in monochrome afbeeldingen kan onverwachte weergaveresultaten hebben, zoals geen beeldweergave. Als dit probleem optreedt, schakelt u resampling uit en converteert u het bestand opnieuw. Dit probleem doet zich het meest voor bij subsampling en het minst bij bicubische downsampling.

In deze tabel ziet u de typen printers en de resolutie van deze printers, gemeten in dpi, de standaardrasterliniatuur in regels per inch (lpi) en een resamplingresolutie voor afbeeldingen die worden gemeten in pixels per inch (ppi). Als u bijvoorbeeld wilt afdrukken op een 600-dpi laserprinter, voert u 170 in voor de resolutie waarmee u het aantal pixels van afbeeldingen wilt wijzigen.

<table>
 <tbody>
  <tr>
   <th><p>Printerresolutie</p> </th>
   <th><p>Standaardlijnscherm</p> </th>
   <th><p>Afbeeldingsresolutie</p> </th>
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

**Compressie:** Stel een waarde in die u wilt toepassen op afbeeldingen in kleur, grijswaarden en monochroom. Voor kleuren- en grijswaardenafbeeldingen stelt u ook de afbeeldingskwaliteit in:

* Voor kleuren- of grijswaardenafbeeldingen selecteert u ZIP om compressie toe te passen die geschikt is voor afbeeldingen met grote gebieden met één kleur of herhalende patronen. Voorbeelden zijn schermafbeeldingen, eenvoudige afbeeldingen die zijn gemaakt met tekenprogramma&#39;s en monochrome afbeeldingen die herhalende patronen bevatten. Selecteer JPEG, kwaliteit minimaal tot maximaal, om compressie toe te passen die geschikt is voor grijswaarden- of kleurenafbeeldingen, zoals continutoonfoto&#39;s die meer details bevatten dan op het scherm of in de afdruk kunnen worden gereproduceerd. Selecteer Automatisch (JPEG) om automatisch de beste kwaliteit voor kleuren- en grijswaardenafbeeldingen te bepalen.
* Voor monochrome afbeeldingen selecteert u CCITT Groep 4, CCITT Groep 3, ZIP, JPEG200, Automatisch (JPEG2000) of Run Length-compressie.

Zorg ervoor dat monochrome afbeeldingen worden gescand als monochroom en niet als grijswaarden. Gescande tekst wordt soms standaard opgeslagen als grijswaardenafbeeldingen. Grijswaardentekst die is gecomprimeerd met de JPEG-compressiemethode is niet duidelijk en kan onleesbaar zijn.

**Afbeeldingskwaliteit:** Hiermee configureert u de afbeeldingskwaliteit voor kleuren- en grijswaardenafbeeldingen. De opties zijn minimaal, laag, gemiddeld, hoog en maximaal.

**Anti-alias naar grijs:** Hiermee maakt u oneffen randen in monochrome afbeeldingen vloeiender. Selecteer 2-bits, 4-bits of 8-bits om 4, 16 of 256 grijsniveaus op te geven. (Anti-aliasing kan kleine tekst of dunne lijnen vervagen.)

>[!NOTE]
>
>De compressie van tekst en lijnen is altijd ingeschakeld.

**Beleid voor afbeeldingen:** Stel een beleid in voor kleuren-, grijswaarden- en monochrome afbeeldingen. Als de afbeeldingsresolutie lager is dan de opgegeven resolutie, kunt u doorgaan (Negeren), een waarschuwingsbericht opgeven of de taak annuleren.

## Fontopties {#fonts-options}

Met de opties bij Fonts geeft u op welke fonts u wilt insluiten in een PDF-bestand en of u een subset met tekens wilt insluiten die in het PDF-bestand worden gebruikt. Zie PDF-instellingen [toevoegen of bewerken voor informatie over het openen van lettertypeopties](configuring-pdf-settings.md#add-or-edit-pdf-settings).

>[!NOTE]
>
>Wanneer u PDF-bestanden combineert met dezelfde fontsubset, probeert PDF Generator de fontsubsets te combineren.

**Alle fonts insluiten:** Hiermee worden alle lettertypen ingesloten die in het bestand worden gebruikt. Lettertypen moeten worden ingesloten voor compatibiliteit met PDF/X.

**Subset maken van lettertypen wanneer percentage gebruikte tekens kleiner is dan:** Als u deze optie selecteert, geeft u een drempelpercentage op om alleen een subset van de lettertypen in te sluiten. Als de drempelwaarde bijvoorbeeld 35 is en minder dan 35% van de tekens wordt gebruikt, worden in PDF Generator alleen die tekens ingesloten. Alleen fonts met de juiste machtigingsbits worden ingesloten.

**Wanneer insluiten mislukt:** Hiermee geeft u op hoe de PDF Generator reageert als er bij de verwerking van een bestand geen font voor insluiting wordt gevonden. U kunt de PDF Generator de aanvraag laten negeren en het font vervangen, u waarschuwen en het font vervangen of de verwerking van de huidige taak annuleren.

**Fontbron:** De locatie van de lettertypen die door de PDF Generator worden gebruikt.

### Opgeven welke fonts moeten worden ingesloten {#specify-which-fonts-to-embed}

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF-instellingen.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Klik op Lettertypen en schakel de optie Alle lettertypen insluiten uit.
1. Selecteer een lettertypenbron in de lijst Lettertypenbron en klik op Ga om de lijst met lettertypen in het vak links te vernieuwen.
1. Klik op een lettertype in het vak aan de linkerkant. Klik vervolgens op Toevoegen naast het desbetreffende vak om het item te verplaatsen naar de lijst Altijd insluiten of Nooit insluiten. Herhaal dit voor elk lettertype. Houd Ctrl ingedrukt en klik om meerdere lettertypen te selecteren die u wilt verplaatsen.
1. Als u een lettertype wilt verwijderen uit de lijst Altijd insluiten of Nooit insluiten, selecteert u het en klikt u op Verwijderen naast het desbetreffende vak. Hierdoor wordt het lettertype niet van uw systeem verwijderd. alleen de verwijzing ernaar in de lijst wordt verwijderd .
1. Als het lettertype dat u wilt opgeven niet wordt weergegeven, typt u de naam in het vak Lettertype toevoegen en klikt u op Altijd insluiten of Nooit insluiten. Fontnamen mogen geen alfanumerieke tekens bevatten.

>[!NOTE]
>
>Een TrueType-font kan een instelling bevatten die de fontontwerper heeft toegevoegd en die voorkomt dat het font wordt ingesloten in PDF-bestanden.

>[!NOTE]
>
>De lettertypen worden gekozen uit de cache van het Windows-systeemlettertype en het systeem moet opnieuw worden opgestart om de cache bij te werken. Nadat u de lettertypemap voor de klant hebt opgegeven, dient u het systeem waarop AEM-formulieren zijn geïnstalleerd opnieuw te starten.

## Kleuropties {#color-options}

Met de kleuropties stelt u alle kleurbeheerinformatie in voor de PDF-generator. Zie PDF-instellingen [toevoegen of bewerken voor informatie over het openen van de kleuropties](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Adobe-kleurinstellingen {#adobe-color-settings}

**Instellingenbestand:** Deze lijst bevat een lijst met kleurinstellingen die ook worden gebruikt in grote grafische toepassingen, zoals Adobe Photoshop en Adobe Illustrator. De kleurinstelling die u selecteert, bepaalt de andere Adobe-kleurinstellingen op deze pagina. Als u bijvoorbeeld een andere instelling dan Geen selecteert, worden alle andere opties dan die voor apparaatafhankelijke gegevens vooraf gedefinieerd en gedimd. U kunt de instellingen Beleid voor kleurbeheer en Werkruimten alleen bewerken als u Geen selecteert bij Instellingenbestand.

### Beleid voor kleurbeheer {#color-management-policies}

Als u Geen hebt geselecteerd bij Instellingenbestand, wordt in het gebied Beleid voor kleurbeheer aangegeven hoe de niet-beheerde kleur van de PDF-generator wordt omgezet in een PostScript-bestand.

**Kleur ongewijzigd laten:** Hiermee blijven apparaatafhankelijke kleuren ongewijzigd en blijven apparaatonafhankelijke kleuren behouden als het dichtstbijzijnde equivalent in PDF. Deze optie is handig voor drukkers die al hun apparaten hebben gekalibreerd, die deze informatie gebruiken om de kleur in het bestand op te geven en die alleen op die apparaten afdrukken.

**Alles coderen voor kleurbeheer:** Hiermee wordt een profiel van een International Color Consortium ingesloten bij het distilleren van bestanden en het kalibreren van kleur in afbeeldingen. Kleuren in de resulterende PDF-bestanden worden apparaatonafhankelijk als u compatibiliteit met Acrobat 4 (PDF 1.3) of hoger hebt geselecteerd. Apparaatafhankelijke kleurruimten in bestanden (RGB, Grijswaarden en CMYK) worden echter omgezet in apparaatonafhankelijke kleurruimten (CalRGB, CalGray en LAB).

**Alleen afbeeldingen coderen voor kleurbeheer:** ICC-profielen worden alleen ingesloten in afbeeldingen, niet in tekst of afbeeldingen, wanneer bestanden worden gedistilleerd als u compatibiliteit met Acrobat 4 (PDF 1.3) hebt geselecteerd. Met deze optie voorkomt u dat zwarte tekst een kleurverschuiving ondergaat. Apparaatafhankelijke kleurruimten in afbeeldingen (RGB, Grijswaarden en CMYK) worden echter omgezet in apparaatonafhankelijke kleurruimten (CalRGB, CalGray en LAB). Tekst en afbeeldingen worden niet geconverteerd.

**Alle kleuren converteren naar sRGB of Alle kleuren converteren naar CMYK:** Kalibreert de kleur in het bestand en maakt de kleur apparaatonafhankelijk, vergelijkbaar met Alles coderen voor kleurbeheer. Als u compatibiliteit met Acrobat 4 (PDF 1.3) of hoger hebt geselecteerd en de afbeeldingen naar sRGB hebt geconverteerd, worden de CMYK- en RGB-afbeeldingen naar sRGB geconverteerd.

Grijswaardenafbeeldingen blijven ongewijzigd, ongeacht de compatibiliteitsoptie die u selecteert. Hierdoor wordt de grootte van PDF-bestanden meestal verkleind en de weergavesnelheid van PDF-bestanden verhoogd, omdat er minder informatie nodig is om RGB-afbeeldingen te beschrijven dan om CMYK-afbeeldingen te beschrijven. Omdat RGB de eigen kleurruimte is die wordt gebruikt op monitoren, is er geen kleurconversie nodig tijdens het weergeven, wat bijdraagt aan een snelle onlineweergave. Deze optie wordt aanbevolen als het PDF-bestand online of met printers met een lage resolutie moet worden gebruikt.

**Render-intentie document:** De methode voor het toewijzen van kleuren tussen kleurruimten. Het resultaat van een bepaalde methode hangt af van de profielen van de kleurruimten. Sommige profielen produceren bijvoorbeeld identieke resultaten met verschillende methoden. De volgende opties zijn beschikbaar:

>[!NOTE]
>
>In alle gevallen kunnen intenties worden genegeerd of overschreven door kleurbeheerbewerkingen die plaatsvinden nadat het PDF-bestand is gemaakt.

**Behouden:** Dit betekent dat de intentie wordt opgegeven in het uitvoerapparaat en niet in het PDF-bestand. In veel uitvoerapparaten is Relatief colorimetrisch de standaardintentie.

**Perceptueel:** Behoudt de relatieve kleurwaarden tussen de oorspronkelijke pixels wanneer deze worden toegewezen aan de doelkleuromvang. Met deze methode blijft de visuele relatie tussen kleuren behouden, maar de kleurwaarden zelf kunnen veranderen.

**Verzadiging:** Behoudt de relatieve verzadigingswaarden van de oorspronkelijke pixels. Deze methode is geschikt voor zakelijke afbeeldingen, waarbij de exacte relatie tussen kleuren niet zo belangrijk is als heldere verzadigde kleuren.

**Relatief colorimetrisch:** Hiermee wordt het witpunt van de bronruimte opnieuw toegewezen aan het witpunt van de doelruimte.

**Absoluut colorimetrisch:** Schakelt de regeling van witte en zwarte punten bij het omzetten van kleuren uit. Deze methode wordt alleen aangeraden als u de handtekeningkleuren, zoals de kleuren die worden gebruikt in handelsmerken of logo&#39;s, wilt behouden.

### Werkruimten {#working-spaces}

Voor alle waarden in de lijst onder Beleid voor kleurbeheer, behalve Kleur ongewijzigd laten, selecteert u een van de lijsten in het gebied Werkruimte om op te geven welke ICC-profielen worden gebruikt voor het definiëren en kalibreren van de grijswaarden-, RGB- en CMYK-kleurruimten in gedistilleerde PDF-bestanden. De volgende opties zijn beschikbaar:

**Grijs:** Hiermee definieert u de kleurruimte van alle grijswaardenafbeeldingen in bestanden. Deze optie is alleen beschikbaar als u Alles labelen voor kleurbeheer of Alleen labels toewijzen voor afbeeldingen voor kleurbeheer hebt gekozen. Het standaard-ICC-profiel voor grijswaardenafbeeldingen is Grijsgamma 2.2. U kunt ook Geen selecteren om te voorkomen dat grijswaardenafbeeldingen worden geconverteerd.

**RGB:** Hiermee definieert u de kleurruimte van alle RGB-afbeeldingen in bestanden. De standaardinstelling, sRGB IEC61966-2.1, is doorgaans een goede keuze omdat deze industriestandaard wordt en veel uitvoerapparaten deze herkennen. U kunt ook Geen selecteren om te voorkomen dat RGB-afbeeldingen worden geconverteerd.

**CMYK:** Hiermee definieert u de kleurruimte van alle CMYK-afbeeldingen in bestanden. De standaardwaarde is U.S. Web Coated (SWOP) v2. U kunt ook Geen selecteren om te voorkomen dat CMYK-afbeeldingen worden geconverteerd.

>[!NOTE]
>
>Als u Geen selecteert voor alle drie de werkruimten, heeft dit hetzelfde effect als wanneer u Kleur ongewijzigd laten selecteert.

**CMYK-waarden behouden voor gekalibreerde CMYK-kleurruimten:** Als deze optie is geselecteerd, worden apparaatonafhankelijke CMYK-waarden beschouwd als apparaatafhankelijke waarden (DeviceCMYK), worden apparaatonafhankelijke kleurruimten genegeerd en gebruiken PDF/X-1a-bestanden de waarde Alle kleuren converteren naar CMYK. Als deze optie niet is geselecteerd, worden apparaatonafhankelijke kleurruimten geconverteerd naar CMYK als het kleurbeheerbeleid is ingesteld op Alle kleuren converteren naar CMYK.

### Apparaatafhankelijke gegevens {#device-dependent-data}

Deze opties zijn van toepassing als u werkt met documenten die zijn gemaakt met geavanceerde documentatie en grafische toepassingen, zoals Adobe Illustrator en Adobe InDesign. Raadpleeg de documentatie bij de toepassing voor meer informatie.

Overdrachtsfuncties worden gebruikt voor artistieke effecten en voor het aanpassen van de specificaties van een specifiek uitvoerapparaat. Een bestand dat bijvoorbeeld is bedoeld voor uitvoer op een bepaalde imagesetter, kan overdrachtsfuncties bevatten die de puntverbreding compenseren die inherent is aan die printer.

**Under color removal en black generation behouden:** Hiermee blijven deze instellingen behouden als deze voorkomen in het PostScript-bestand. Zwarte plaat berekent de hoeveelheid zwart die moet worden gebruikt wanneer u een bepaalde kleur probeert te reproduceren. Met Menggrijsvervanging vermindert u de hoeveelheid cyaan, magenta en gele componenten om de hoeveelheid zwart te compenseren die door de zwarte plaat wordt toegevoegd. Omdat het minder inkt gebruikt, wordt UCR over het algemeen gebruikt voor krantenpapier en niet-gecoat papier.

**Wanneer overdrachtsfuncties worden gevonden:** Bepaalt wat te doen wanneer de overdrachtsfuncties worden gevonden:

**Behouden:** Hiermee behoudt u de overdrachtsfuncties die gewoonlijk worden gebruikt om de puntverbreding of puntversmalling te compenseren die kunnen optreden wanneer een afbeelding naar film wordt overgezet. Er treedt puntverbreding op wanneer de inktstippen waaruit een afgedrukte afbeelding bestaat, groter zijn (bijvoorbeeld door spreiding op papier) dan in het halftoonraster. puntverlies treedt op wanneer de punten kleiner worden afgedrukt. Met deze optie worden de overdrachtsfuncties als onderdeel van het bestand bewaard en op het bestand toegepast wanneer het bestand wordt uitgevoerd.

**Toepassen:** De overdrachtsfunctie blijft niet behouden, maar wordt toegepast op het bestand, waardoor de kleuren in het bestand worden gewijzigd. Deze optie is handig voor het maken van kleureffecten in een bestand. Deze optie is standaard geselecteerd voor nieuwe instellingen.

**Verwijderen:** Hiermee verwijdert u toegepaste overdrachtsfuncties. Verwijder toegepaste overdrachtsfuncties tenzij het PDF-bestand wordt uitgevoerd naar hetzelfde apparaat waarvoor het bron-PostScript-bestand is gemaakt.

**Halftoongegevens behouden:** Hiermee behoudt u alle halftoongegevens in bestanden. Halftooninformatie bestaat uit stippen die bepalen hoeveel halftoonapparaten met inkt op een specifieke locatie op het papier worden neergezet. Door de puntgrootte en de dichtheid te variëren, lijkt het alsof de kleur grijs of doorlopend is. Voor een CMYK-afbeelding worden vier halftoonrasters gebruikt, één voor elke inkt die in het afdrukproces wordt gebruikt.

In de traditionele afdrukproductie wordt een halftoon gemaakt door een halftoonraster tussen een film en de afbeelding te plaatsen en vervolgens de film beschikbaar te maken. Met elektronische equivalenten, zoals in Adobe Photoshop, kunnen gebruikers de halftoonrasterkenmerken opgeven voordat ze de film- of papieruitvoer produceren. Halftooninformatie is bedoeld voor gebruik met een bepaald uitvoerapparaat.

## Geavanceerde opties {#advanced-options}

Met de opties Geavanceerd geeft u op welke DSC-opmerkingen (Documentstructuurconventies) u in het PDF-bestand wilt behouden en hoe u andere opties instelt die van invloed zijn op de conversie vanuit PostScript. In een PostScript-bestand bevatten DSC-opmerkingen informatie over het bestand (zoals de brontoepassing, de aanmaakdatum en de afdrukstand van de pagina). Ze bieden ook structuur voor paginabeschrijvingen in het bestand (zoals instructies voor het begin en einde van een prologsectie). DSC-opmerkingen kunnen handig zijn wanneer uw document wordt afgedrukt of ingedrukt. Zie PDF-instellingen [toevoegen of bewerken voor informatie over het openen van de geavanceerde opties](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Als u werkt met de opties Geavanceerd, is het handig om te weten wat de PostScript-taal is en hoe deze naar PDF wordt vertaald. (Zie [Adobe PostScript 3](https://www.adobe.com/products/postscript/main.html).)

**PostScript-bestand toestaan om Adobe PDF-instellingen te overschrijven:** Hiermee gebruikt u instellingen die in een PostScript-bestand zijn opgeslagen in plaats van het huidige Adobe PDF-instellingenbestand. Voordat u een PostScript-bestand verwerkt, kunt u parameters in het bestand plaatsen om de volgende aspecten te beheren:

* compressie van tekst en afbeeldingen
* downsamplen en coderen van gesamplede afbeeldingen
* Insluiten van Type 1-lettertypen en instanties van Type 1 Multiple Master-lettertypen

**PostScript-XObjecten toestaan:** PostScript XObjecten slaan informatie op die op veel pagina&#39;s van hetzelfde bestand wordt weergegeven, zoals een achtergrondafbeelding of kop- en voettekstinformatie. Het gebruik van PostScript XObjects kan resulteren in sneller afdrukken, maar vereist meer printergeheugen. Als u wilt voorkomen dat PostScript-XObjects worden gemaakt, schakelt u deze optie uit als u PDF-bestanden maakt met compatibiliteit met Acrobat 5 (PDF 1.4) of hoger.

**Verlopen omzetten in vloeiende schaduwen:** Hiermee converteert u overvloeiingen naar vloeiende schaduwen voor Acrobat 4 en hoger, waardoor PDF-bestanden kleiner worden en de kwaliteit van de uiteindelijke uitvoer kan verbeteren. De Generator PDF zet gradiënten van de Illustrator van Adobe, Adobe InDesign, Adobe FreeHand MX, CorelDraw, Quark Xpress, en Microsoft PowerPoint om.

**Vloeiende lijnen converteren naar curven:** Hiermee vermindert u het aantal controlepunten dat wordt gebruikt om curven op te bouwen in CAD-tekeningen. Dit resulteert in kleinere PDF&#39;s en snellere rendering op het scherm.

**Level 2 copypage-semantiek behouden:** Gebruikt de copypage-operator die is gedefinieerd in LanguageLevel 2 PostScript in plaats van in LanguageLevel 3 PostScript. Als u een PostScript-bestand hebt en deze optie selecteert, kopieert een copypage-operator de pagina. Als deze optie niet is geselecteerd, wordt het equivalent van een showpage-bewerking uitgevoerd, maar wordt de grafische status niet opnieuw geïnitialiseerd.

**Overdrukinstellingen behouden:** Hiermee blijven eventuele overdrukinstellingen behouden in bestanden die naar PDF worden geconverteerd. Overgedrukte kleuren zijn twee of meer inkten die op elkaar worden afgedrukt. Wanneer bijvoorbeeld een cyaan inkt over een gele inkt wordt afgedrukt, is de resulterende overdruk een groene kleur. Zonder overdrukken wordt het onderliggende geel niet afgedrukt, wat resulteert in een cyaan kleur.

**Standaard voor overdrukken is niet-nul overdrukken:** Voorkomt dat overgedrukte objecten met CMYK-waarden van nul CMYK-objecten die eronder staan, uitnemen. Dit effect wordt bereikt door de statusparameter OPM 1 voor afbeeldingen in te voegen in het PDF-bestand, waar de Afdrukoperator SetOverprint zich bevindt.

**Adobe PDF-instellingen opslaan in PDF-bestand:** Hiermee sluit u het instellingenbestand in dat wordt gebruikt om het PDF-bestand te maken. U kunt het instellingenbestand (met de bestandsnaamextensie .joboptions) openen en weergeven in het dialoogvenster Bestandsbijlagen in Acrobat. Het Adobe PDF-instellingenbestand wordt een item in de structuur Ingesloten bestanden in het PDF-bestand.

**Oorspronkelijke JPEG-afbeeldingen indien mogelijk opslaan in PDF:** Verwerkt gecomprimeerde JPEG-afbeeldingen (afbeeldingen die al zijn gecomprimeerd met DCT-codering) zonder ze opnieuw te comprimeren. Als deze optie is geselecteerd, worden JPEG-afbeeldingen in de PDF-generator gedecomprimeerd om te voorkomen dat ze beschadigd raken. Geldige afbeeldingen worden echter niet opnieuw gecomprimeerd, waardoor de oorspronkelijke afbeelding ongewijzigd wordt verwerkt. Als deze optie is geselecteerd, verbeteren de prestaties omdat alleen decompressie (geen recompressie) optreedt en de afbeeldingsgegevens en metagegevens behouden blijven.

**Draagbaar opdrachtetiket opslaan in PDF-bestand:** Hiermee blijft een PostScript-opdrachtticket behouden in een PDF-bestand. Het opdrachtticket bevat informatie over het PostScript-bestand, zoals het paginaformaat, de resolutie en overvullingsgegevens, in plaats van informatie over de inhoud. Deze informatie kan later in een werkstroom of voor druk worden gebruikt PDF.

**Prologue.ps en Epilogue.ps gebruiken:** Hiermee wordt bij elke taak een proloog- en een epiloogbestand verzonden. Deze bestanden hebben vele doeleinden. Profielbestanden kunnen bijvoorbeeld worden bewerkt om omslagpagina&#39;s op te geven. Epiloogbestanden kunnen worden bewerkt om een reeks procedures in een PostScript-bestand op te lossen. U kunt de bestanden uploaden of downloaden. (Zie Prologue- en epiloogbestanden uploaden en downloaden.)

**DSC-opmerkingen verwerken:** Hiermee wordt DSC-informatie uit een PostScript-bestand bewaard. Deze subopties zijn beschikbaar:

**DSC-waarschuwingen logboek:** Toont waarschuwingsberichten over problematische commentaren van DSC tijdens verwerking en voegt hen aan een logboekdossier toe.

**EPS-informatie uit DSC behouden:** Hiermee behoudt u informatie, zoals de brontoepassing en de aanmaakdatum voor een EPS-bestand. Als deze optie is uitgeschakeld, wordt de grootte en het midden van de pagina gebaseerd op de linkerbovenhoek van het object linksboven en de rechterbenedenhoek van het object rechtsonder op de pagina.

**OPI-opmerkingen behouden:** Hiermee behoudt u de informatie die nodig is om een FPO-afbeelding (For Placement Only) of een opmerking te vervangen door de afbeelding met hoge resolutie op servers die OPI-versies 1.3 en 2.0 (Open Prepress Interface) ondersteunen.

**Documentgegevens uit DSC behouden:** Behoudt informatie zoals de titel, aanmaakdatum en -tijd. Wanneer u een PDF-bestand opent in Acrobat, wordt deze informatie weergegeven in het venster Beschrijving van documenteigenschappen.

**Paginaformaat wijzigen en illustraties centreren voor EPS-bestanden:** Hiermee centreert u een EPS-afbeelding en past u de grootte van de pagina aan de afbeelding aan. Deze optie is alleen van toepassing op taken die uit één EPS-bestand bestaan.

## Standaardrapporterings- en compatibiliteitsopties {#standards-reporting-and-compliance-options}

PDF Generator kan de documentinhoud in een PostScript-bestand controleren om te controleren of deze voldoet aan de standaard PDF/X-1a-, PDF/X-3- of PDF/A-criteria voordat het PDF-bestand wordt gemaakt. Voor PDF/X-compatibele bestanden kunt u ook opgeven dat het PostScript-bestand aan extra criteria voldoet door andere opties te selecteren onder &#39;Standaardenrapportage en -compatibiliteit&#39;. De beschikbaarheid van opties is afhankelijk van de standaard die u selecteert.

PDF/X-compatibele bestanden worden voornamelijk gebruikt als een gestandaardiseerde indeling voor de uitwisseling van PDF-bestanden die zijn bestemd voor afdrukproductie met hoge resolutie. Tenzij u een PDF-document maakt voor afdrukproductie, kunt u de compatibiliteitsnormen voor PDF/X negeren.

PDF/A-compatibele bestanden worden vooral gebruikt voor archivering. Omdat bewaring op lange termijn het doel is, mag het document alleen bevatten wat nodig is voor het openen en weergeven gedurende de gehele beoogde levensduur van het document. PDF/A-compatibele bestanden kunnen bijvoorbeeld alleen tekst, rasterafbeeldingen en vectorobjecten bevatten. ze kunnen geen versleuteling en scripts bevatten. Bovendien moeten alle lettertypen zijn ingesloten, zodat de documenten kunnen worden geopend en weergegeven zoals ze zijn gemaakt. Met andere woorden, PDF/A-compatibele documenten zijn *dunner* dan hun PDF/X-tegenhangers, die bedoeld zijn voor productie op hoog niveau.

>[!NOTE]
>
>Als u een gecontroleerde map instelt voor het maken van PDF/A-compatibele bestanden, moet u ervoor zorgen dat u geen beveiliging aan de map toevoegt. De PDF/A-standaard staat geen versleuteling toe.

Zie PDF-instellingen [toevoegen of bewerken voor instructies over het openen van de rapportage over standaarden en compatibiliteitsopties](configuring-pdf-settings.md#add-or-edit-pdf-settings).

**Compatibiliteitsnorm:** Selecteer een standaard om een rapport te maken waarin wordt aangegeven of het bestand voldoet aan de vereisten en, als dat niet het geval is, welke problemen zijn aangetroffen. Wanneer Compatibiliteit op de pagina Algemene instellingen is ingesteld op Acrobat 4.0, zijn de volgende opties ingeschakeld. Wanneer Compatibiliteit is ingesteld op Acrobat 5.0, zijn alleen de opties van Acrobat 5.0 beschikbaar om te selecteren. Wanneer Compatibiliteit is ingesteld op een andere optie, worden de volgende opties grijs weergegeven:

* PDF/X-1a (compatibel met Acrobat 4.0)
* PDF/X-3 (compatibel met Acrobat 4.0)
* PDF/X-1a (compatibel met Acrobat 5.0)
* PDF/X-3 (compatibel met Acrobat 5.0)
* PDF/A-1b (compatibel met Acrobat 5.0)

### Opties voor PDF/X-standaarden {#options-for-pdf-x-standards}

**Indien niet conform:** Hiermee geeft u aan of het PDF-bestand moet worden gemaakt als het PostScript-bestand niet voldoet aan PDF/X-vereisten. Deze optie is beschikbaar wanneer de Norm van de Naleving op de pagina van de Rapportering en van de Naleving van Normen aan een andere optie dan niets wordt geplaatst.

**Doorgaan:** Hiermee maakt u een PDF-bestand.

**Taak annuleren:** Hiermee maakt u alleen een PDF-bestand als het PostScript-bestand voldoet aan de PDF/X-vereisten van de geselecteerde rapportopties en anderszins geldig is. Als beide PDF/X-rapportopties zijn geselecteerd en het PostScript-bestand slechts aan één set PDF/X-criteria voldoet (bijvoorbeeld PDF/X-3), maakt de PDF Generator het compatibele bestand.

**Als er geen TrimBox en geen ArtBox zijn opgegeven:** Beschikbaar wanneer de Norm van de Naleving op de Pagina van de Rapportering en van de Naleving van Normen aan een andere optie dan niets wordt geplaatst.

**Als fout rapporteren:** Hiermee markeert u het PostScript-bestand als niet-compatibel als een van de rapportopties is geselecteerd en een bijsnijdvak of illustratievak ontbreekt op een pagina.

**TrimBox instellen op MediaBox met afstand:** Berekent waarden in punten voor het bijsnijdvak op basis van de verschuivingen voor het mediavak van de respectieve pagina&#39;s als noch het bijsnijdvak, noch het illustratievak is opgegeven. Het bijsnijdvak is altijd zo klein of kleiner dan het omsluitende mediavak.

**Als er geen BleedBox is opgegeven:** Beschikbaar wanneer de Norm van de Naleving op de Pagina van de Rapportering en van de Naleving van Normen aan een andere optie dan niets wordt geplaatst.

**BleedBox instellen op MediaBox:** Hiermee gebruikt u de waarden voor het mediavak voor het afloopvak als het afloopvak niet is opgegeven.

**BleedBox instellen op TrimBox met verschuivingen:** Berekent waarden in punten voor het afloopvak op basis van de verschuivingen voor het bijsnijdvak van de respectieve pagina&#39;s als het afloopvak niet is opgegeven. Het afloopvak is altijd even groot of groter dan het omsloten bijsnijdvak.

**Standaardwaarden, indien niet opgegeven in het document:** Deze optie is beschikbaar wanneer de Norm van de Naleving op de pagina van de Rapportering en van de Naleving van Normen aan een andere optie dan niets wordt geplaatst.

**Naam uitvoerintentieprofiel:** Hiermee wordt de gekarakteriseerde afdrukvoorwaarde aangegeven waarop het document wordt voorbereid. Als in een document geen naam voor een uitvoerintentie is opgegeven, gebruikt de PDF Generator de geselecteerde waarde in dit menu. U kunt een van de opgegeven namen selecteren of een naam invoeren in de beschikbare ruimte. Selecteer Geen als de workflow vereist dat het document de uitvoerintentie opgeeft. Een document dat niet aan de vereisten voldoet, kan niet worden gecontroleerd op de naleving.

**Uitvoervoorwaarde-id:** Hiermee wordt de referentienaam aangegeven die is opgegeven in het register van de naam van het uitvoerintentieprofiel.

**Uitvoervoorwaarde:** Beschrijft de voorgenomen drukvoorwaarde. Dit item kan handig zijn voor de ontvanger van het PDF-document.

**Registernaam (URL):** Geeft het webadres aan voor meer informatie over het register. De URL wordt automatisch ingevoerd voor ICC-registernamen.

**Overvuld:** Geeft de status van overvulling in het document aan. Voor compatibiliteit met PDF/X is de waarde Waar of Onwaar vereist. Als het document de overvulstatus niet opgeeft, wordt de hier opgegeven waarde gebruikt. Selecteer Ongedefinieerd laten als uw werkstroom vereist dat het document de overvulstatus opgeeft. Een document dat niet aan de vereisten voldoet, kan niet worden gecontroleerd op de naleving.

### Opties voor PDF/A-standaard {#options-for-pdf-a-standard}

Deze opties worden ingeschakeld als Compatibiliteit (in het gedeelte Algemeen) is ingesteld op Acrobat 4 (PDF 1.3) of Acrobat 5 (PDF 1.4).

**Indien niet conform:** Hiermee geeft u aan of het PDF-bestand moet worden gemaakt als het PostScript-bestand niet voldoet aan PDF/A-vereisten.

**Doorgaan:** Hiermee maakt u een PDF-bestand, zelfs als het PostScript-bestand niet voldoet aan de vereisten van de norm.

**Taak annuleren:** Hiermee maakt u alleen een PDF-bestand als het PostScript-bestand voldoet aan PDF/A-vereisten en anderszins geldig is.

**Naam uitvoerintentieprofiel:** Hiermee wordt de gekarakteriseerde afdrukvoorwaarde aangegeven waarvoor het document is voorbereid en die vereist is voor compatibiliteit met PDF/A. Selecteer Geen als de workflow vereist dat in het document uitvoerintentiegegevens worden opgegeven. Als deze informatie niet is opgegeven, wordt niet gecontroleerd of het document aan de voorschriften voldoet.

**Uitvoervoorwaarde:** Beschrijft de voorgenomen drukvoorwaarde. Dit item is niet vereist, maar kan worden gebruikt om nuttige informatie te verstrekken aan de beoogde ontvanger van het PDF-document.

## Oorspronkelijke weergaveopties {#initial-view-options}

Deze opties zijn onderverdeeld in drie gebieden: Documentopties, Vensteropties en Interfaceopties. Zie PDF-instellingen [toevoegen of bewerken voor instructies over het openen van de opties voor de weergave bij openen](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Als u opties wilt gebruiken, selecteert u Instellingen voor beginweergave instellen.

### Documentopties {#document-options}

De documentopties bepalen de weergave van het document in het documentvenster, zoals de zoomfactor en de schuifwijze.

**Tonen:** Hiermee bepaalt u welke deelvensters en tabbladen standaard in het toepassingsvenster worden weergegeven. In het venster Bladwijzers en op de pagina wordt het documentvenster geopend en wordt het tabblad Bladwijzers weergegeven.

**Pagina-indeling:** Hiermee bepaalt u of het document wordt weergegeven in de modus Eén pagina, Eén pagina naast elkaar, Ononderbroken pagina of Ononderbroken pagina naast elkaar.

**Vergroting:** Hiermee stelt u het zoomniveau in dat wordt gebruikt om het document weer te geven wanneer het wordt geopend. De standaardwaarde gebruikt de door de gebruiker ingestelde vergrotingswaarde in de voorkeuren van Acrobat of Adobe Reader.

**Openen naar paginanummer:** Hiermee stelt u de pagina in waarop het document wordt geopend. Dit is doorgaans pagina 1.

>[!NOTE]
>
>Als u Standaard instelt voor de opties voor vergroting en paginalay-out, worden de afzonderlijke gebruikersinstellingen in de voorkeuren voor paginaweergave in Acrobat of Adobe Reader gebruikt.

### Vensteropties {#window-options}

De vensteropties bepalen hoe het venster in het schermgebied wordt aangepast wanneer een gebruiker het document opent. De opties hebben echter geen effect wanneer een PDF-document in een webbrowser wordt weergegeven.

**Vensterformaat als van eerste pagina:** Hiermee past u het documentvenster aan zodat het precies rond de openingspagina past, afhankelijk van de opties die u onder Documentopties hebt geselecteerd.

**Venster centreren op scherm:** Plaatst het venster in het midden van het schermgebied.

**Openen in Volledig scherm:** Hiermee maximaliseert u het documentvenster en geeft u het document weer zonder de menubalk-, werkbalk- of vensteropties.

**Tonen:** Bestandsnaam geeft de bestandsnaam weer in de titelbalk van het venster. De documenttitel wordt weergegeven in de titelbalk van het venster.

### Gebruikersinterfaceopties {#user-interface-options}

De gebruikersinterface-opties bepalen welke besturingselementen worden weergegeven of verborgen wanneer de gebruiker het document opent.

**Menubalk verbergen:** Indien geselecteerd, wordt de menubalk verborgen

**Werkbalken verbergen:** Indien geselecteerd, verbergt u de werkbalken

**Vensterbalk verbergen:** Indien geselecteerd, verbergt de venstercontroles

>[!NOTE]
>
>Als u de menubalk en de werkbalk verbergt, kunnen gebruikers alleen met behulp van sneltoetsen opties toepassen en gereedschappen selecteren wanneer ze het bestand in Acrobat openen.

## Proloog- en epiloogbestanden uploaden en downloaden {#uploading-and-downloading-prologue-and-epilogue-files}

Prolologbestanden worden gebruikt om aangepaste PostScript-code toe te voegen die wordt uitgevoerd aan het begin van elke PostScript-taak die wordt gedistilleerd. Epiloogbestanden worden gebruikt om aangepaste PostScript-code toe te voegen die aan het einde van elke PostScript-taak wordt uitgevoerd. U kunt proloog- en epiloogbestanden downloaden van de server om ze lokaal op te slaan. U kunt de bestanden downloaden om ze onafhankelijk te configureren of naar een andere locatie of computer te uploaden.

Deze bestanden hebben vele doeleinden. Profielbestanden kunnen bijvoorbeeld worden bewerkt om omslagpagina&#39;s op te geven; U kunt epiloogbestanden bewerken om een reeks procedures in een PostScript-bestand op te lossen. U kunt ook de proloog- en epiloogbestanden selecteren en uploaden die u met elke taak wilt verzenden.

### Een proloog- of epiloogbestand downloaden {#download-a-prologue-or-epilogue-file}

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF-instellingen.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Klik op Geavanceerd en vervolgens naast de optie Prologue.ps en Epilogue.ps gebruiken op Downloaden.
1. Klik op Prologue.ps of Epilogue.ps en klik op Opslaan op de pagina Prologue en Epilogue-bestanden downloaden.

### Een proloog- of epiloogbestand uploaden {#upload-a-prologue-or-epilogue-file}

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF-instellingen.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Klik op Geavanceerd en vervolgens naast de optie Prologue.ps en Epilogue.ps gebruiken op Uploaden.
1. Klik op de pagina Prologue uploaden en Epiloogbestanden op Bladeren om een proloog of een epiloogbestand te selecteren.
1. Zoek het bestand en klik op Openen.
1. Als u het bestand wilt gebruiken, selecteert u Prologue.ps en Epilogue.ps gebruiken in het gedeelte Geavanceerd van de instellingspagina van Adobe PDF Nieuw/Bewerken.
1. Klik op Opslaan

>[!NOTE]
>
>PDF Generator ondersteunt alleen proloog- en epiloogbestanden voor conversie van PostScript- en Encapsulated PostScript-bestanden naar PDF.

