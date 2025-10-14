---
title: Adobe PDF-instellingen configureren
description: Leer hoe u de Adobe PDF-instellingen configureert die op de pagina Adobe PDF Settings worden weergegeven. U kunt de vooraf gedefinieerde PDF-instellingen gebruiken of uw eigen instellingen maken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: 1bcb8429-c06e-4bd3-b422-4c512084dd09
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '7415'
ht-degree: 0%

---

# Adobe PDF-instellingen configureren{#configuring-adobe-pdf-settings}

Op de pagina Adobe PDF Settings worden de conversie-instellingen weergegeven die u voor uw bronnen kunt opgeven. U kunt de vooraf gedefinieerde PDF-instellingen gebruiken of uw eigen instellingen maken. De PDF-instellingen bepalen exact hoe bestanden worden geconverteerd en wat de resulterende PDF-structuur en -functies zijn. Adobe PDF-instellingen werden voorheen Distiller®-parameters of taakopties genoemd.

Op de pagina Adobe PDF Settings kunt u de volgende taken uitvoeren:

* Bekijk de vooraf gedefinieerde PDF-instellingen. (Zie [&#x200B; Ongeveer de vooraf bepaalde montages van PDF &#x200B;](configuring-pdf-settings.md#about-the-predefined-pdf-settings).)
* Maak een PDF-instelling of bewerk een instelling die u eerder hebt gemaakt. (Zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.)
* Geef de standaardinstellingen voor PDF op. (Zie [&#x200B; Verandering de standaardmontages &#x200B;](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings))
* Upload een bestand met PDF-instellingen naar de server. (Zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#upload-pdf-settings) uploaden.)
* Aangepaste PDF-instellingen verwijderen. (Zie [&#x200B; PDF montages van de Schrapping &#x200B;](configuring-pdf-settings.md#delete-pdf-settings).)
* Proloog- en epiloogbestanden uploaden en downloaden. (Zie [&#x200B; Uploading en het downloaden van proloog en epiloogdossiers &#x200B;](configuring-pdf-settings.md#uploading-and-downloading-prologue-and-epilogue-files).)

Adobe PDF-instellingen zijn alleen van toepassing op conversies op basis van PDFMaker. Deze omvatten de volgende omzettingen:

* Microsoft Word-document (DOC, DOCX, RTF, TXT)
* Microsoft Excel-document (XLS, XLSX)
* Microsoft PowerPoint-document (PPT, PPTX)
* Microsoft Project-document (MPP)
* Microsoft Visio-document (VSD)

>[!NOTE]
>
>Als u OpenOffice gebruikt om bovenstaande indelingen om te zetten, worden Adobe PDF-instellingen niet toegepast.

## De vooraf gedefinieerde PDF-instellingen {#about-the-predefined-pdf-settings}

PDF Generator biedt verschillende vooraf gedefinieerde PDF-instellingen voor uw gebruik. U kunt deze vooraf gedefinieerde instellingen niet wijzigen. U kunt echter een instelling maken op basis van een bestaande instelling door de instelling te bewerken en onder een andere naam op te slaan.

**Hoge Druk van de Kwaliteit:** creeert PDF dossiers voor output van uitstekende kwaliteit. Deze instelling:

* Hiermee worden kleuren- en grijswaardenafbeeldingen gedownsampled met 300 dpi
* Hiermee worden monochrome afbeeldingen gedownsampled met 1200 dpi
* afdrukken naar een hogere afbeeldingsresolutie
* gebruikt andere instellingen om de maximale hoeveelheid informatie over het oorspronkelijke document te behouden.

Deze PDF-bestanden kunnen worden geopend in Adobe Acrobat 5 en Adobe Acrobat Reader® 5 of hoger.

**Overmaatse Pagina&#39;s:** creeert PDF documenten die voor het betrouwbare bekijken en druk van technische tekeningen geschikt zijn die groter zijn dan 200 x 200 duim. Gemaakte PDF-documenten kunnen worden geopend in Adobe Acrobat Professional en Acrobat Standard, versie 7 of hoger en Adobe Reader 7 of hoger.

**PDF/A-1B 2005 CMYK / PDF/A-1B 2005 RGB:** controleert inkomende banen op naleving van de norm van ISO voor langdurig behoud (archivering) van elektronische documenten en leidt tot PDF/A dossiers slechts als volgzaam. Deze bestanden worden vooral gebruikt voor archivering. Compatibele bestanden kunnen alleen tekst, rasterafbeeldingen en vectorobjecten bevatten; ze kunnen geen versleuteling en scripts bevatten. Bovendien moeten alle lettertypen zijn ingesloten, zodat de documenten kunnen worden geopend en weergegeven zoals ze zijn gemaakt. PDF/A-1b gebruikt PDF 1.4 en zet alle kleuren in of CMYK of RGB om, afhankelijk van welke norm u kiest. PDF-bestanden die met dit instellingenbestand zijn gemaakt, kunnen worden geopend in Acrobat 5 en Acrobat Reader 5 en hoger. Zie Adobe en industriestandaarden voor meer informatie over PDF/A.

**PDF/x-1a 2001:** controleert inkomende banen voor naleving PDF/x-1a, en leidt tot PDF- dossiers slechts als volgzaam. PDF/X-1a is een ISO-standaard voor het uitwisselen van grafische inhoud. PDF/X-1a vereist dat alle lettertypen worden ingesloten, dat de juiste PDF-vakken worden opgegeven en dat kleuren worden weergegeven als CMYK- of steunkleuren. PDF-bestanden die voldoen aan de PDF/X-1a-vereisten, zijn gericht op een specifieke uitvoervoorwaarde, zoals web-offsetdrukwerk volgens de specificaties voor Web-offsetpublicaties. Zie Adobe en industriestandaarden voor meer informatie over PDF/X.

**PDF/x-3 2002:** controleert inkomende banen voor naleving PDF/x-3 en leidt tot PDF- dossiers slechts als volgzaam. Net als PDF/X-1a is PDF/X-3 een ISO-standaard voor het uitwisselen van grafische inhoud. Het belangrijkste verschil is dat PDF/X-3 apparaatonafhankelijke kleuren ondersteunt.

**Kwaliteit van de Pers:** creeert PDF- dossiers voor de drukproductie van uitstekende kwaliteit (bijvoorbeeld, op een imagesetter of platesetter). In dit geval is bestandsgrootte geen overweging. Het doel is om alle informatie in een PDF-bestand te behouden die een drukker of prepress-bureau nodig heeft om het document correct af te drukken. Deze set opties:

* Hiermee worden kleuren- en grijswaardenafbeeldingen gedownsampled met 300 dpi
* Hiermee worden monochrome afbeeldingen gedownsampled met 1200 dpi
* Hiermee worden subsets ingesloten van alle lettertypen die in het document worden gebruikt
* afdrukken tot een hogere beeldresolutie,
* roteert pagina&#39;s niet automatisch op basis van de richting van de tekst of de opmerkingen in de DSC-indeling (Document Structure Conventions)
* gebruikt andere instellingen om de maximale hoeveelheid informatie over het oorspronkelijke document te behouden.

Afdruktaken mislukken als ze fonts hebben die niet kunnen worden ingesloten. Deze PDF-bestanden kunnen worden geopend in Acrobat 5 en Acrobat Reader 5 en hoger.

>[!NOTE]
>
>Voordat u een PDF-bestand maakt dat u naar een commerciële drukker of prepress-bureau wilt verzenden, bepaalt u de uitvoerresolutie en andere instellingen of vraagt u een .joboptions-bestand met de aanbevolen instellingen aan. Mogelijk moet u de Adobe PDF-instellingen aanpassen voor een bepaalde provider en een eigen .joboptions-bestand meeleveren.

**Kleinste Grootte van het Dossier:** creeert PDF dossiers voor het tonen op het Web of een Intranet, of voor distributie door een e-mailsysteem voor het bekijken op het scherm. Bij deze set opties worden compressie, downsampling en een relatief lage afbeeldingsresolutie gebruikt. Alle kleuren worden omgezet in sRGB en er worden geen lettertypen ingesloten, tenzij dat nodig is. Ook worden bestanden geoptimaliseerd voor byteserving. Deze PDF-bestanden kunnen worden geopend in Acrobat 5 en Acrobat Reader 5.0 en hoger.

**Norm:** creeert de dossiers van PDF aan druk aan Desktopprinters of digitale kopieerapparaten, publiceren op CD, of verzenden naar een cliënt als het publiceren bewijs. Bij deze set opties worden compressie en downsampling gebruikt om de bestandsgrootte te beperken. Subsets met alle lettertypen die in het bestand worden gebruikt, worden geconverteerd naar sRGB en afgedrukt naar een gemiddelde resolutie om een redelijk nauwkeurige weergave van het oorspronkelijke document te maken. Subsets van Microsoft Windows-lettertypen worden niet standaard ingesloten. Deze PDF-bestanden kunnen worden geopend in Acrobat 5 en Acrobat Reader 5.0 en hoger.

## PDF-instellingen toevoegen of bewerken {#add-or-edit-pdf-settings}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

PDF-instellingen bepalen exact hoe bestanden worden geconverteerd en de resulterende PDF-structuur en -functies. Definieer een nieuwe PDF-instelling of bewerk een instelling die u eerder hebt gemaakt. U kunt vooraf gedefinieerde instellingen niet wijzigen, maar u kunt een instelling maken op basis van een bestaande instelling door de instelling te bewerken en onder een andere naam op te slaan.

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF Settings.
1. Klik op Nieuw of klik op de naam van een bestaande instelling.
1. Voer op de pagina Nieuwe Adobe PDF-instelling/-instellingen bewerken de vereiste informatie in deze secties in:

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

U kunt PDF-instellingen beschikbaar hebben op de PDF Generator-server door deze te uploaden vanaf een lokale computer of een netwerklocatie.

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF-instellingen en klik op Uploaden.
1. Klik op de pagina Adobe PDF-instellingen uploaden op Bladeren, zoek het bestand met PDF-instellingen en klik op Openen.
1. Klik op OK en vervolgens nogmaals op OK.

## PDF-instellingen verwijderen {#delete-pdf-settings}

U kunt PDF-instellingen permanent verwijderen als deze niet meer vereist zijn.

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF Settings.
1. Schakel het selectievakje naast de instelling die u wilt verwijderen in. U kunt meerdere instellingen selecteren.
1. Klik op Verwijderen en klik nogmaals op Verwijderen op de pagina Bevestiging verwijderen.

## Algemene opties {#general-options}

Gebruik de algemene opties om de versie van Acrobat op te geven die u wilt gebruiken voor bestandscompatibiliteit en andere bestands- en apparaatopties. Voor instructies over de toegang tot van de Algemene opties, zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.

### Bestandsopties {#file-options}

**Verenigbaarheid:** het verenigbaarheidsniveau van het dossier van de PDF. Voor documenten die op grote schaal worden gedistribueerd, kunt u wellicht beter Acrobat 4 (PDF 1.3) of Acrobat 5 (PDF 1.4) selecteren om ervoor te zorgen dat alle gebruikers het document kunnen bekijken en afdrukken. Bestanden die u maakt met Acrobat 5-compatibiliteit of hoger, zijn mogelijk niet compatibel met eerdere versies van Acrobat. In de volgende subsecties ziet u enkele verschillen tussen PDF-bestanden die zijn gemaakt met verschillende niveaus van Acrobat-compatibiliteit.

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
   <td><p>Kan geen illustraties bevatten die actieve transparantie-effecten gebruiken. Transparantie moet worden afgevlakt voordat u de afbeelding omzet in PDF 1.3.</p> </td>
   <td><p>Ondersteunt het gebruik van actieve transparantie in illustraties. (Acrobat Distiller-functie voegt transparantie af.)</p> </td>
   <td><p>Ondersteunt het gebruik van actieve transparantie in illustraties. (Acrobat Distiller-functie voegt transparantie af.)</p> </td>
   <td><p>Ondersteunt het gebruik van actieve transparantie in illustraties. (Acrobat Distiller-functie voegt transparantie af.)</p> </td>
  </tr>
  <tr>
   <td><p>Lagen worden niet ondersteund.</p> </td>
   <td><p>Lagen worden niet ondersteund.</p> </td>
   <td><p>Lagen blijven behouden wanneer u PDF-bestanden maakt van toepassingen die het genereren van gelaagde PDF-documenten, zoals Adobe Illustrator® CS of Adobe InDesign® CS en hoger, ondersteunen.</p> </td>
   <td><p>Lagen blijven behouden wanneer u PDF-bestanden maakt van toepassingen die het genereren van gelaagde PDF-documenten, zoals Illustrator CS of InDesign CS en hoger, ondersteunen.</p> </td>
  </tr>
  <tr>
   <td><p>DeviceN-kleurruimte met 8 kleurstoffen wordt ondersteund.</p> </td>
   <td><p>DeviceN-kleurruimte met 8 kleurstoffen wordt ondersteund.</p> </td>
   <td><p>DeviceN-kleurruimte met maximaal 31 kleurstoffen wordt ondersteund.</p> </td>
   <td><p>DeviceN-kleurruimte met maximaal 31 kleurstoffen wordt ondersteund.</p> </td>
  </tr>
  <tr>
   <td><p>Multibyte-lettertypen kunnen worden ingesloten. (Distiller converteert de lettertypen bij het insluiten.)</p> </td>
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

**de Compressie van het Niveau van Objecten:** consolideert kleine voorwerpen (elk waarvan niet zelf) in stromen comprimeren die dan efficiënt kunnen worden samengeperst.

**weg:** comprimeert geen structurele informatie in het document van de PDF. Selecteer deze optie als u wilt dat gebruikers met Acrobat 5 en hoger door bladwijzers en andere structuurgegevens kunnen navigeren en deze kunnen gebruiken.

**slechts Markeringen:** comprimeert structurele informatie in het document van de PDF. Als u deze optie gebruikt, resulteert dit in een PDF-bestand dat met Acrobat 5 kan worden geopend en afgedrukt. Gebruikers kunnen in Acrobat 5 of Acrobat Reader 5.0 geen toegankelijkheids-, structuur- of gelabelde PDF-informatie weergeven, maar ze kunnen deze informatie wel bekijken in Acrobat 6 en Adobe Reader 6.0.

**auto-Roteer Pagina&#39;s:** plaatst de automatische omwenteling van pagina&#39;s die op de richtlijn van de tekst of de commentaren van DSC worden gebaseerd. Sommige pagina&#39;s (zoals pagina&#39;s die tabellen bevatten) vereisen bijvoorbeeld dat de gebruiker deze pagina&#39;s zijdelings leest. Selecteer Afzonderlijk om elke pagina te roteren op basis van de richting van de tekst op die pagina. Selecteer Collectief op bestand om alle pagina&#39;s in het document te roteren op basis van de richting van de meeste tekst.

>[!NOTE]
>
>Als DSC-opmerkingen verwerken is geselecteerd in de Geavanceerde instellingen en als opmerkingen over de afdrukstand zijn opgenomen in %%Viewing Orientation, hebben deze opmerkingen voorrang bij het bepalen van de afdrukstand van de pagina.

**Bindend:** specificeert of om een dossier van PDF met linker-zij of juist-zijband te tonen. Deze instelling is van invloed op de weergave van pagina&#39;s in de indeling Pagina naast elkaar - Doorlopende lay-out en de weergave van miniaturen naast elkaar.

**Resolutie:** plaatst de wedijver voor de resolutie van een printer voor inputdossiers die hun gedrag volgens de resolutie van de printer aanpassen zij aan drukken. Voor de meeste invoerbestanden leidt een hogere resolutie-instelling tot grotere, maar kwalitatief betere PDF-bestanden en een lagere instelling tot kleinere, maar minder goede PDF-bestanden. Meestal bepaalt de resolutie het aantal stappen in een verloop of overvloeiing. U kunt een waarde tussen 72 en 4000 invoeren. Deze instelling blijft de standaardinstelling, tenzij u het PDF-bestand wilt afdrukken op een specifieke printer en u de resolutie wilt emuleren die in het oorspronkelijke invoerbestand is gedefinieerd.

>[!NOTE]
>
>Als u de resolutie-instelling verhoogt, wordt het bestand groter en kan de verwerkingstijd van sommige bestanden iets langer worden.

**Alle Pagina&#39;s of Pagina&#39;s van:** specificeert welke pagina&#39;s om te zetten. Laat het vak Aan leeg om een bereik te maken van het paginanummer dat u hebt ingevoerd in het vak Van tot het einde van het bestand.

**optimaliseert voor Snelle Mening van het Web:** herstructureert het dossier voor pagina-bij-a-tijd het downloaden (byte het dienen) van Webservers. Met deze optie comprimeert u tekst en lijnen, ongeacht de compressie-instellingen op het tabblad Afbeeldingen die u hebt geselecteerd. Compressie leidt tot snellere toegang en weergave wanneer het bestand wordt gedownload van het web of een netwerk. Deze optie is standaard niet ingeschakeld.

### Standaardpaginaformaat {#default-page-size}

Met de opties bij Standaardpaginaformaat geeft u het paginaformaat op dat moet worden gebruikt als er geen formaat is opgegeven in het oorspronkelijke bestand. Adobe PostScript-bestanden bevatten deze informatie meestal, behalve voor Encapsulated PostScript (EPS)-bestanden, die een selectiekadergrootte maar geen paginagrootte geven. Het maximale paginaformaat is 31.800.000 inch (15.000.000 cm) in beide richtingen. Met deze opties configureert u het standaardpaginaformaat:

**Breedte:** Breedte van de pagina

**Hoogte:** Hoogte van de pagina

**Eenheden:** Eenheden om voor de breedte en de hoogtemontages te gebruiken

## Afbeeldingsopties {#images-options}

Met de opties bij Afbeeldingen geeft u compressie en resampling voor afbeeldingen op. U kunt met deze opties experimenteren om een juiste balans te vinden tussen bestandsgrootte en afbeeldingskwaliteit. Voor instructies over de toegang tot van de montages van Beelden, zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.

Met deze opties configureert u afbeeldingen in kleur, grijswaarden en monochroom:

**Downsample:** plaats een waarde voor elk type van beeld. Voor het downsamplen van kleuren-, grijswaarden- of monochrome afbeeldingen, combineert PDF Generator pixels in een monstergebied om één grotere pixel te maken. Geef de resolutie van het uitvoerapparaat op in dpi (dots per inch) en voer een resolutie in dpi in het tekstvak Voor afbeeldingen boven in. Voor afbeeldingen met een resolutie die hoger is dan deze drempelwaarde, combineert PDF Generator zo nodig pixels om de resolutie van de afbeelding (pixels per inch) tot de opgegeven dpi-instelling te beperken. Selecteer Uit om downsampling uit te schakelen. Hier volgen de opties:

**Gemiddelde Downsampling aan:** Gemiddelt de pixel in een steekproefgebied en vervangt het volledige gebied met de gemiddelde pixelkleur bij de gespecificeerde resolutie.

**Bicubische Downsampling aan:** gebruikt een gewogen gemiddelde om pixelkleur te bepalen en produceert gewoonlijk betere resultaten dan de eenvoudige het gemiddelde nemen methode van downsampling. Bicubisch is de langzaamste maar meest nauwkeurige methode en resulteert in de meest vloeiende kleurovergangen.

**Subsampling aan:** selecteert een pixel in het centrum van het steekproefgebied en vervangt het volledige gebied met die pixel bij de gespecificeerde resolutie. Subsampling vermindert significant de omzettingstijd in vergelijking met downsampling, maar het resulteert in beelden die minder vlot en ononderbroken zijn.

De resolutie-instelling voor kleur en grijswaarden moet 1,5 tot 2 keer de rasterliniatuur zijn waarmee het bestand wordt afgedrukt. (Als u deze aanbevolen resolutie-instelling niet overschrijdt, worden afbeeldingen zonder rechte lijnen of geometrische of herhalende patronen niet beïnvloed door een lagere resolutie.) De resolutie voor monochrome afbeeldingen moet gelijk zijn aan die van het uitvoerapparaat. Als u echter een monochrome afbeelding opslaat met een resolutie die hoger is dan 1500 dpi, neemt de bestandsgrootte toe zonder dat de beeldkwaliteit merkbaar toeneemt.

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

**Compressie:** plaats een waarde om op kleur, grayscale, en monochrome beelden van toepassing te zijn. Voor kleuren- en grijswaardenafbeeldingen stelt u ook de afbeeldingskwaliteit in:

* Voor kleuren- of grijswaardenafbeeldingen selecteert u ZIP om compressie toe te passen die geschikt is voor afbeeldingen met grote gebieden met één kleur of herhalende patronen. Voorbeelden zijn schermafbeeldingen, eenvoudige afbeeldingen die zijn gemaakt met tekenprogramma&#39;s en monochrome afbeeldingen die herhalende patronen bevatten. Selecteer JPEG, kwaliteit minimaal tot maximaal, om compressie toe te passen die geschikt is voor grijswaarden- of kleurenafbeeldingen, zoals continutoonfoto&#39;s die meer details bevatten dan op het scherm of in de afdruk kunnen worden gereproduceerd. Selecteer Automatisch (JPEG) om automatisch de beste kwaliteit voor kleuren- en grijswaardenafbeeldingen te bepalen.
* Voor monochrome beelden, uitgezochte Groep 4 CCITT, Groep 3 CCITT, ZIP, JPEG200, Automatische (JPEG 2000), of de compressie van de Lengte van de Looppas.

Zorg ervoor dat monochrome afbeeldingen worden gescand als monochroom en niet als grijswaarden. Gescande tekst wordt soms standaard opgeslagen als grijswaardenafbeeldingen. Grijswaardentekst die is gecomprimeerd met de compressiemethode JPEG, is niet duidelijk en kan onleesbaar zijn.

**Kwaliteit van het Beeld:** vormt de beeldkwaliteit voor kleur en grayscale beelden. De opties zijn minimaal, laag, gemiddeld, hoog en maximaal.

**anti-alias aan Grijs:** maakt gekartelde randen in monochrome beelden vloeiend. Selecteer 2 bits, 4 bits of 8 bits om 4, 16 of 256 grijsniveaus op te geven. (Anti-aliasing kan kleine tekst of dunne lijnen vervagen.)

>[!NOTE]
>
>De compressie van tekst en lijnen is altijd ingeschakeld.

**Beleid van het Beeld:** plaats een beleid voor kleur, grayscale, en monochrome beelden. Als de afbeeldingsresolutie lager is dan de opgegeven resolutie, kunt u doorgaan (Negeren), een waarschuwingsbericht opgeven of de taak annuleren.

## Fontopties {#fonts-options}

Met de lettertypeopties geeft u op welke lettertypen u in een PDF-bestand wilt insluiten en of u een subset met tekens wilt insluiten die in het PDF-bestand worden gebruikt. Voor instructies over de toegang tot van de opties van Doopvonten, zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.

>[!NOTE]
>
>Wanneer u PDF-bestanden combineert met dezelfde fontsubset, probeert PDF Generator de fontsubsets te combineren.

**bed Alle Doopvonten in:** sluit alle doopvonten in die in het dossier worden gebruikt. Lettertype-insluiting is vereist voor PDF/X-compatibiliteit.

**Subset ingebedde doopvonten wanneer percentage gebruikte karakters
Is minder dan:** als u deze optie selecteert, specificeer een drempelpercentage om slechts een ondergroep van de doopvonten in te bedden. Als de drempelwaarde bijvoorbeeld 35 is en minder dan 35% van de tekens wordt gebruikt, sluit PDF Generator alleen die tekens in. Alleen fonts met de juiste machtigingsbits worden ingesloten.

**wanneer het Inbedden ontbreekt:** specificeert hoe de PDF Generator antwoordt als het geen doopvont kan vinden om in te bedden wanneer het verwerken van een dossier. PDF Generatoren kunnen de aanvraag negeren en het font vervangen, u waarschuwen en het font vervangen of de verwerking van de huidige taak annuleren.

**Doopvont Source:** de plaats van de doopvonten die de PDF Generator gebruikt.

### Opgeven welke fonts moeten worden ingesloten {#specify-which-fonts-to-embed}

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF Settings.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Klik op Lettertypen en schakel de optie Alle lettertypen insluiten uit.
1. Selecteer een lettertypenbron in de lijst Lettertypenbron en klik op Ga om de lijst met lettertypen in het vak links te vernieuwen.
1. Klik op een lettertype in het vak aan de linkerkant. Klik vervolgens op Toevoegen naast het desbetreffende vak om het item te verplaatsen naar de lijst Altijd insluiten of Nooit insluiten. Herhaal dit voor elk lettertype. Houd Ctrl ingedrukt en klik om meerdere te verplaatsen lettertypen te selecteren.
1. Als u een lettertype wilt verwijderen uit de lijst Altijd insluiten of Nooit insluiten, selecteert u het en klikt u op Verwijderen naast het desbetreffende vak. Met deze actie verwijdert u het lettertype niet van uw systeem, maar verwijdert u alleen de verwijzing naar het lettertype in de lijst.
1. Als het lettertype dat u wilt opgeven niet wordt weergegeven, typt u de naam in het vak Lettertype toevoegen en klikt u op Altijd insluiten of Nooit insluiten. Fontnamen mogen geen alfanumerieke tekens bevatten.

>[!NOTE]
>
>Een TrueType-font kan een instelling bevatten die de fontontwerper heeft toegevoegd en die voorkomt dat het font wordt ingesloten in PDF-bestanden.

>[!NOTE]
>
>De lettertypen worden gekozen uit de cache van het Windows-systeemlettertype en het systeem moet opnieuw worden opgestart om de cache bij te werken. Nadat u de lettertypemap voor de klant hebt opgegeven, dient u het systeem waarop AEM formulieren zijn geïnstalleerd opnieuw te starten.

## Kleuropties {#color-options}

Met de kleuropties stelt u alle kleurbeheerinformatie voor de PDF Generator in. Voor instructies over de toegang tot van de opties van de Kleur, zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.

### Adobe Color-instellingen {#adobe-color-settings}

**Dossier van Montages:** Deze lijst bevat een lijst van kleurenmontages die ook in belangrijke grafiektoepassingen, zoals Adobe Photoshop en Adobe Illustrator worden gebruikt. De kleurinstelling die u selecteert, bepaalt de andere kleurinstellingen voor de Adobe op deze pagina. Als u bijvoorbeeld een andere instelling dan Geen selecteert, worden alle andere opties dan die voor apparaatafhankelijke gegevens vooraf gedefinieerd en gedimd. U kunt de instellingen Beleid voor kleurbeheer en Werkruimten alleen bewerken als u Geen selecteert bij Instellingenbestand.

### Beleid voor kleurbeheer {#color-management-policies}

Als u Geen hebt geselecteerd bij Instellingenbestand, wordt in het gebied Beleid voor kleurbeheer aangegeven hoe PDF Generator onbeheerde kleuren in een PostScript-bestand converteert.

**Kleur van het Verlof Onveranderd:** laat apparaat-afhankelijke kleuren ongewijzigd en bewaart apparaat-onafhankelijke kleuren als meest dichtbijgelegen mogelijke equivalent in PDF. Deze optie is handig voor drukkers die al hun apparaten hebben gekalibreerd, die deze informatie gebruiken om de kleur in het bestand op te geven en die alleen op die apparaten afdrukken.

**Etiketteer Alles voor het Beheer van de Kleur:** sluit een profiel van het Consortium van de Internationale Kleur in wanneer het distilleren van dossiers en het kalibreren van kleur in de beelden, die kleuren in de resulterende PDF dossiers apparaat-onafhankelijk maakt als u Acrobat 4 (PDF 1.3) of recentere verenigbaarheid selecteerde. Apparaatafhankelijke kleurruimten in bestanden (RGB, Grijswaarden en CMYK) worden echter omgezet in apparaatonafhankelijke kleurruimten (CalRGB, CalGray en LAB).

**slechts Beelden van de Markering voor het Beheer van de Kleur:** sluit ICC profielen slechts in beelden, niet tekst of grafiek in, wanneer het distilleren van dossiers als u (PDF 1.3) verenigbaarheid van Acrobat 4 selecteerde. Met deze optie voorkomt u dat zwarte tekst een kleurverschuiving ondergaat. Apparaatafhankelijke kleurruimten in afbeeldingen (RGB, Grijswaarden en CMYK) worden echter omgezet in apparaatonafhankelijke kleurruimten (CalRGB, CalGray en LAB). Tekst en afbeeldingen worden niet omgezet.

**zet Alle Kleuren in sRGB om of zet Alle Kleuren in om
CMYK:** Kalibreert kleur in het bestand, waardoor de kleur apparaatonafhankelijk wordt, vergelijkbaar met Alles coderen voor kleurbeheer. Als u compatibiliteit met Acrobat 4 (PDF 1.3) of hoger hebt geselecteerd en de CMYK- en RGB-afbeeldingen hebt omgezet in sRGB, worden deze omgezet in sRGB.

Grijswaardenafbeeldingen blijven ongewijzigd, ongeacht de compatibiliteitsoptie die u selecteert. Hierdoor wordt de grootte van PDF-bestanden meestal verkleind en de weergavesnelheid van deze bestanden verhoogd, omdat er minder informatie nodig is om RGB-afbeeldingen te beschrijven dan om CMYK-afbeeldingen te beschrijven. Omdat RGB de eigen kleurruimte is die wordt gebruikt op monitoren, is er geen kleurconversie nodig tijdens het weergeven, wat bijdraagt aan een snelle online weergave. Deze optie wordt aanbevolen als het PDF-bestand online of met printers met een lage resolutie moet worden gebruikt.

**het Teruggeven van het Document Intent:** de methode om kleuren tussen kleurenruimten in kaart te brengen. Het resultaat van een bepaalde methode hangt af van de profielen van de kleurruimten. Sommige profielen produceren bijvoorbeeld identieke resultaten met verschillende methoden. Deze opties zijn beschikbaar:

>[!NOTE]
>
>In alle gevallen kunnen intenties worden genegeerd of overschreven door kleurbeheerbewerkingen die plaatsvinden nadat het PDF-bestand is gemaakt.

**Behouden:** betekent dat de bedoeling in het uitvoerapparaat eerder dan in het dossier van PDF wordt gespecificeerd. In veel uitvoerapparaten is Relatief colorimetrisch de standaardintentie.

**Perceptueel:** handhaaft de relatieve kleurenwaarden onder de originele pixel aangezien zij aan de bestemmingskleuromvang in kaart worden gebracht. Met deze methode blijft de visuele relatie tussen kleuren behouden, maar de kleurwaarden zelf kunnen veranderen.

**Verzadiging:** handhaaft de relatieve verzadigingswaarden van de originele pixel. Deze methode is geschikt voor zakelijke afbeeldingen, waarbij de exacte relatie tussen kleuren niet zo belangrijk is als heldere verzadigde kleuren.

**Relatief colorimetrisch:** wijst het witte punt van de bronruimte aan het witte punt van de bestemmingsruimte opnieuw toe.

**Absolute Colorimetrisch:** maakt de aanpassing van witte en zwarte punten onbruikbaar wanneer het omzetten van kleuren. Deze methode wordt alleen aanbevolen als u de handtekeningkleuren, zoals de kleuren die worden gebruikt in handelsmerken of logo&#39;s, wilt behouden.

### Werkruimten {#working-spaces}

Voor alle waarden in de lijst onder Beleid voor kleurbeheer, behalve Kleur ongewijzigd laten, selecteert u een van de lijsten in het gebied Werkruimte om op te geven welke ICC-profielen worden gebruikt voor het definiëren en kalibreren van de grijswaarden-, RGB- en CMYK-kleurruimten in gedistilleerde PDF-bestanden. Deze opties zijn beschikbaar:

**Grijs:** bepaalt de kleurenruimte van alle grijswaardenbeelden in dossiers. Deze optie is alleen beschikbaar als u Alles labelen voor kleurbeheer of Alleen labels toewijzen voor afbeeldingen voor kleurbeheer hebt gekozen. Het standaard-ICC-profiel voor grijswaardenafbeeldingen is Grijsgamma 2.2. U kunt ook Geen selecteren om te voorkomen dat grijswaardenafbeeldingen worden omgezet.

**RGB:** bepaalt de kleurenruimte van alle beelden van RGB in dossiers. De standaardinstelling, sRGB IEC61966-2.1, is doorgaans een goede keuze omdat deze industriestandaard wordt en veel uitvoerapparaten deze herkennen. U kunt ook Geen selecteren om te voorkomen dat RGB-afbeeldingen worden omgezet.

**CMYK:** bepaalt de kleurenruimte van alle beelden CMYK in dossiers. De standaardwaarde is U.S. Web Coated (SWOP) v2. U kunt ook Geen selecteren om te voorkomen dat CMYK-afbeeldingen worden omgezet.

>[!NOTE]
>
>Als u Geen selecteert voor alle drie de werkruimten, heeft dit hetzelfde effect als wanneer u Kleur ongewijzigd laten selecteert.

**Behoud CMYK Waarden voor gekalibreerde CMYK Kleurruimten:** Wanneer geselecteerd, worden de apparaat-onafhankelijke waarden CMYK behandeld als apparaat-afhankelijke (DeviceCMYK) waarden, apparaat-onafhankelijke kleurenruimten worden verworpen, en PDF/X-1a- dossiers gebruiken de Bekeerling Alle Kleuren in waarde CMYK. Als deze optie niet is geselecteerd, worden apparaatonafhankelijke kleurruimten omgezet in CMYK als het kleurbeheerbeleid is ingesteld op Alle kleuren converteren naar CMYK.

### Apparaatafhankelijke gegevens {#device-dependent-data}

Deze opties zijn van toepassing als u werkt met documenten die zijn gemaakt met geavanceerde documentatie en grafische toepassingen, zoals Adobe Illustrator en Adobe InDesign. Raadpleeg de documentatie bij de toepassing voor meer informatie.

Overdrachtsfuncties worden gebruikt voor artistieke effecten en voor het aanpassen van de specificaties van een specifiek uitvoerapparaat. Een bestand dat bijvoorbeeld is bedoeld voor uitvoer op een bepaalde imagesetter, kan overdrachtsfuncties bevatten die de puntverbreding compenseren die inherent is aan die printer.

**Behoud onder de Verwijdering van de Kleur en Zwarte Generatie:** behoudt deze montages als zij in het dossier van PostScript bestaan. Zwarte plaat berekent de hoeveelheid zwart die moet worden gebruikt wanneer u een bepaalde kleur probeert te reproduceren. Met Menggrijsvervanging vermindert u de hoeveelheid cyaan, magenta en gele componenten om de hoeveelheid zwart te compenseren die door de zwarte plaat wordt toegevoegd. Omdat het minder inkt gebruikt, wordt UCR over het algemeen gebruikt voor krantenpapier en niet-gecoat papier.

**wanneer de Functies van de Overdracht worden gevonden:** bepaalt wat te doen wanneer de overdrachtsfuncties worden gevonden:

**Behouden:** behoudt de overdrachtsfuncties die traditioneel worden gebruikt om puntaanwinst of puntverlies te compenseren die kunnen voorkomen wanneer een beeld wordt overgebracht naar film. Er treedt puntverbreding op wanneer de inktstippen waaruit een afgedrukte afbeelding bestaat, groter zijn (bijvoorbeeld door spreiding op papier) dan in het halftoonraster. Puntverlies treedt op wanneer de punten kleiner worden afgedrukt. Met deze optie worden de overdrachtsfuncties als onderdeel van het bestand bewaard en op het bestand toegepast wanneer het bestand wordt uitgevoerd.

**is van toepassing:** houdt niet de overdrachtsfunctie maar past het op het dossier toe, dat de kleuren in het dossier verandert. Deze optie is handig voor het maken van kleureffecten in een bestand. Deze optie is standaard geselecteerd voor nieuwe instellingen.

**verwijder:** verwijdert om het even welke toegepaste overdrachtsfuncties. Verwijder toegepaste overdrachtsfuncties tenzij het PDF-bestand wordt uitgevoerd naar hetzelfde apparaat waarvoor het PostScript-bronbestand is gemaakt.

**Behoud Halftooninformatie:** behoudt om het even welke halftooninformatie in dossiers. Halftooninformatie bestaat uit stippen die bepalen hoeveel halftoonapparaten met inkt op een specifieke locatie op het papier worden neergezet. Door de puntgrootte en de dichtheid te variëren, lijkt het alsof de kleur grijs of doorlopend is. Voor een CMYK-afbeelding worden vier halftoonrasters gebruikt, één voor elke inkt die in het afdrukproces wordt gebruikt.

In de traditionele afdrukproductie wordt een halftoon gemaakt door een halftoonraster tussen een film en de afbeelding te plaatsen en vervolgens de film beschikbaar te maken. Met elektronische equivalenten, zoals in Adobe Photoshop, kunnen gebruikers de halftoonrasterkenmerken opgeven voordat ze de film- of papieruitvoer produceren. Halftooninformatie is bedoeld voor gebruik met een bepaald uitvoerapparaat.

## Geavanceerde opties {#advanced-options}

Met de opties Geavanceerd geeft u op welke DSC-opmerkingen (Documentstructuurconventies) u in het PDF-bestand wilt behouden en hoe u andere opties wilt instellen die van invloed zijn op de conversie vanuit PostScript. In een PostScript-bestand bevatten DSC-opmerkingen informatie over het bestand (zoals de brontoepassing, de aanmaakdatum en de afdrukstand). Ze bieden ook structuur voor paginabeschrijvingen in het bestand (zoals instructies voor het begin en einde van een prologsectie). DSC-opmerkingen kunnen handig zijn wanneer uw document wordt afgedrukt of ingedrukt. Voor instructies over de toegang tot van de Geavanceerde opties, zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.

Als u werkt met de geavanceerde opties, is het handig om te weten wat de PostScript-taal is en hoe deze wordt vertaald naar PDF. (Zie [&#x200B; Adobe PostScript 3 &#x200B;](https://www.adobe.com/products/postscript/main.html).)

**staat het Dossier van PostScript toe om de Montages van Adobe PDF met voeten te treden:** gebruikt montages die in een dossier van PostScript in plaats van het huidige de montagesdossier van Adobe PDF worden opgeslagen. Voordat u een PostScript-bestand verwerkt, kunt u parameters in het bestand plaatsen om de volgende aspecten te beheren:

* compressie van tekst en afbeeldingen
* downsamplen en coderen van gesamplede afbeeldingen
* Insluiten van Type 1-lettertypen en instanties van Type 1 Multiple Master-lettertypen

**staat PostScript XObjects toe:** PostScript XObjects slaan informatie op die op vele pagina&#39;s van het zelfde dossier, zoals een achtergrondbeeld of kopbal en footer informatie verschijnt. Het gebruik van PostScript XObjects kan resulteren in sneller afdrukken, maar vereist meer printergeheugen. Als u wilt voorkomen dat PostScript XObjects worden gemaakt, schakelt u deze optie uit als u PDF-bestanden maakt met Acrobat 5 (PDF 1.4) of latere compatibiliteit.

**zet Verlopen in Vloeiende Schaduwen om:** zet overvloeiingen in vlotte schaduwen voor Acrobat 4 en later om, makend PDF dossiers kleiner en potentieel verbeterend de kwaliteit van definitieve output. PDF Generator converteert verlopen vanuit Adobe Illustrator, Adobe InDesign, Adobe FreeHand MX, CorelDraw, Quark Xpress en Microsoft PowerPoint.

**zet Vloeiende Lijnen in Krommen om:** vermindert de hoeveelheid controlepunten die worden gebruikt om krommen in CAD tekeningen te bouwen, die in kleinere PDF en snellere het schermteruggeven resulteert.

**Niveau 2 Semantiek van de Punten van het Behoud:** gebruikt de copypage exploitant die in LanguageLevel 2 PostScript in plaats van in LanguageLevel 3 PostScript wordt bepaald. Als u een PostScript-bestand hebt en deze optie selecteert, kopieert een copypage-operator de pagina. Als deze optie niet is geselecteerd, wordt het equivalent van een showpage-bewerking uitgevoerd, maar wordt de grafische status niet opnieuw geïnitialiseerd.

**de Montages van de Overdruk van het Behoud:** behoudt om het even welke overdrukmontages in dossiers die in PDF worden omgezet. Overgedrukte kleuren zijn twee of meer inkten die op elkaar worden afgedrukt. Wanneer bijvoorbeeld een cyaan inkt over een gele inkt wordt afgedrukt, is de resulterende overdruk een groene kleur. Zonder overdrukken wordt het onderliggende geel niet afgedrukt, wat resulteert in een cyaan kleur.

**het Overdrukken Gebrek is Niet nul Overdruk:** verhindert overgedrukte voorwerpen met nul waarden CMYK uit voorwerpen uit te nemen CMYK die onder hen zijn. Dit effect wordt bereikt door de statusparameter OPM 1 voor afbeeldingen in te voegen in het PDF-bestand, waar de operator SetOverprint zich bevindt.

**sparen de Montages van Adobe PDF binnen het Dossier van de PDF:** sluit het montagesdossier in dat wordt gebruikt om het dossier van de PDF tot stand te brengen. U kunt het instellingenbestand (met de bestandsnaamextensie .joboptions) openen en weergeven in het dialoogvenster Bestandsbijlagen in Acrobat. Het Adobe PDF-instellingenbestand wordt een item in de structuur EmbeddedFiles in het PDF-bestand.

**sparen Oorspronkelijke beelden van JPEG in PDF indien mogelijk:** verwerkt om het even welke samengeperste beelden van JPEG (beelden die reeds gebruikend het coderen DCT) worden samengeperst zonder hen opnieuw te comprimeren. Als u deze optie selecteert, worden JPEG-afbeeldingen door de PDF Generator gedecomprimeerd om te voorkomen dat ze beschadigd raken. Geldige afbeeldingen worden echter niet opnieuw gecomprimeerd, waardoor de oorspronkelijke afbeelding ongewijzigd wordt verwerkt. Als deze optie is geselecteerd, verbeteren de prestaties omdat alleen decompressie (geen recompressie) optreedt en de afbeeldingsgegevens en metagegevens behouden blijven.

**sparen Portable Ticket van de Baan binnen het Dossier van PDF:** behoudt een de baankaartje van PostScript in een dossier van PDF. Het opdrachtticket bevat informatie over het PostScript-bestand, zoals het paginaformaat, de resolutie en overvullingsgegevens, in plaats van informatie over de inhoud. Deze informatie kan later in een werkstroom of voor druk worden gebruikt de PDF.

**Prologue.ps en Epilogue.ps van het Gebruik:** verzendt een proloog en epiloogdossier met elke baan. Deze bestanden hebben vele doeleinden. Profielbestanden kunnen bijvoorbeeld worden bewerkt en omslagpagina&#39;s opgeven. U kunt Epilog-bestanden bewerken om een reeks procedures in een PostScript-bestand op te lossen. U kunt de bestanden uploaden of downloaden. (Zie Prologue- en epiloogbestanden uploaden en downloaden.)

**de Commentaren van DSC van het Proces DSC:** handhaaft DSC- informatie van een dossier van PostScript. Deze subopties zijn beschikbaar:

**de Waarschuwingen van DSC van het Logboek:** toont waarschuwingsberichten over problematische commentaren van DSC tijdens verwerking en voegt hen aan een logboekdossier toe.

**Behoud de Informatie van EPS van DSC:** behoudt informatie, zoals de voortkomende toepassing en creatiedatum voor een dossier van EPS. Als deze optie is uitgeschakeld, wordt de grootte en het midden van de pagina gebaseerd op de linkerbovenhoek van het object linksboven en de rechterbenedenhoek van het object rechtsonder op de pagina.

**Behoud OPI Commentaren:** behoudt informatie die wordt vereist om a voor het beeld van de Plaatsing slechts (FPO) te vervangen of met het high-resolution beeld te becommentariëren dat op servers wordt gevestigd die Open Prepress Interface (OPI) versies 1.3 en 2.0 steunen.

**Behoud de Informatie van het Document van DSC:** behoudt informatie zoals de titel, de aanmaakdatum, en de tijd. Wanneer u een PDF-bestand opent in Acrobat, wordt deze informatie weergegeven in het deelvenster Beschrijving van documenteigenschappen.

**vergroot de Pagina en het Illustratie van het Centrum voor de Dossiers van EPS:** centreert een beeld van EPS en resizes de pagina om dicht rond het beeld te passen. Deze optie is alleen van toepassing op taken die uit één EPS-bestand bestaan.

## Standaardrapporterings- en compatibiliteitsopties {#standards-reporting-and-compliance-options}

PDF Generatoren kunnen de documentinhoud in een PostScript-bestand controleren om na te gaan of deze voldoen aan de standaard PDF/X-1a-, PDF/X-3- of PDF/A-criteria voordat ze het PDF-bestand maken. Voor bestanden die compatibel zijn met PDF/X, kunt u ook eisen dat het PostScript-bestand voldoet aan aanvullende criteria door andere opties te selecteren onder &#39;Standaardenrapportage en -compatibiliteit&#39;. De beschikbaarheid van opties is afhankelijk van de standaard die u selecteert.

PDF/X-compatibele bestanden worden voornamelijk gebruikt als een gestandaardiseerde indeling voor de uitwisseling van PDF-bestanden die zijn bedoeld voor de productie van afdrukken met hoge resolutie. Tenzij u een PDF-document maakt voor afdrukproductie, kunt u de compatibiliteitsnormen voor PDF/X negeren.

Bestanden die voldoen aan de PDF/A-standaard worden vooral gebruikt voor archivering. Omdat bewaring op lange termijn het doel is, mag het document alleen bevatten wat nodig is voor het openen en weergeven gedurende de gehele beoogde levensduur van het document. Bestanden die voldoen aan de PDF/A-standaard kunnen bijvoorbeeld alleen tekst, rasterafbeeldingen en vectorobjecten bevatten; ze kunnen geen versleuteling en scripts bevatten. Bovendien moeten alle lettertypen zijn ingesloten, zodat de documenten kunnen worden geopend en weergegeven zoals ze zijn gemaakt. Met andere woorden, PDF/a-Volgzame documenten zijn *dunner* dan hun PDF/X tegenhangers, die voor high-end productie voorgenomen zijn.

>[!NOTE]
>
>Als u een controlemap instelt voor het maken van bestanden die voldoen aan de PDF/A-standaard, moet u ervoor zorgen dat u geen beveiliging aan de map toevoegt. Codering wordt niet toegestaan door de PDF/A-standaard.

Voor instructies over de toegang tot van de Normen die en nalevingsopties rapporteren, zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.

**Norm van de Naleving:** selecteer een norm om een rapport te produceren dat erop wijst of het dossier aan de vereisten voldoet en, als niet, welke problemen werden ontmoet. Wanneer Compatibiliteit op de pagina Algemene instellingen is ingesteld op Acrobat 4.0, zijn de volgende opties ingeschakeld. Als Compatibiliteit is ingesteld op Acrobat 5.0, zijn alleen de Acrobat 5.0-opties beschikbaar om te selecteren. Wanneer Compatibiliteit is ingesteld op een andere optie, worden de volgende opties grijs weergegeven:

* PDF/X-1a (compatibel met Acrobat 4.0)
* PDF/X-3 (compatibel met Acrobat 4.0)
* PDF/X-1a (compatibel met Acrobat 5.0)
* PDF/X-3 (compatibel met Acrobat 5.0)
* PDF/A-1b (compatibel met Acrobat 5.0)

### Opties voor PDF/X-standaarden {#options-for-pdf-x-standards}

**wanneer niet Voldoet:** specificeert of om het dossier van de PDF tot stand te brengen als het dossier van PostScript niet aan PDF/X vereisten voldoet. Deze optie is beschikbaar wanneer de Norm van de Naleving op de pagina van de Rapportering en van de Naleving van Normen aan een andere optie dan niets wordt geplaatst.

**ga verder:** creeert een dossier van de PDF.

**annuleert Baan:** creeert een dossier van de PDF slechts als het dossier van PostScript aan de PDF/X vereisten van de geselecteerde rapportopties voldoet en anders geldig is. Als beide PDF/X-rapportopties zijn geselecteerd en het PostScript-bestand slechts aan één set PDF/X-criteria voldoet (bijvoorbeeld PDF/X-3), maakt PDF Generator het compatibele bestand.

**als Noch TrimBox noch ArtBox wordt gespecificeerd:** Beschikbaar wanneer de Norm van de Naleving op de pagina van de Rapportering en van de Normen aan een optie buiten niets wordt geplaatst.

**Rapport als Fout:** vlagt het dossier van PostScript als niet-volgzaam als één van de rapporteringsopties wordt geselecteerd en een trim doos of kunstdoos mist van om het even welke pagina.

**plaatste TrimBox aan MediaBox met Verschuivingen:** verwerkt waarden in punten voor de versiedoos die op de compensatie voor de media doos van respectieve pagina&#39;s wordt gebaseerd als noch de trimdoos noch kunstdoos wordt gespecificeerd. Het bijsnijdvak is altijd zo klein of kleiner dan het omsluitende mediavak.

**als BleedBox niet wordt gespecificeerd:** Beschikbaar wanneer de Norm van de Naleving op de pagina van de Normen die en van de Naleving aan een optie buiten niets meldt wordt geplaatst.

**Reeks BleedBox aan MediaBox:** gebruikt de media vakwaarden voor het afloopvak als het afloopvak niet wordt gespecificeerd.

**Reeks BleedBox aan TrimBox met Verschuivingen:** verwerkt waarden in punten voor het afloopvakje dat op de compensatie voor de bijsnijddoos van respectieve pagina&#39;s wordt gebaseerd als het afloopvakje niet wordt gespecificeerd. Het afloopvak is altijd even groot of groter dan het omsloten bijsnijdvak.

**Standaardwaarden als niet gespecificeerd in het Document:** Deze optie is beschikbaar wanneer de Norm van de Naleving op de pagina van de Normen die en van de Naleving aan een optie buiten niets wordt geplaatst.

**Naam van het Profiel van de Intentie van de Output:** wijst op de gekarakteriseerde drukvoorwaarde dat het document voor wordt voorbereid. Als een document geen naam van OutputIntent opgeeft, gebruikt de PDF Generator de geselecteerde waarde van dit menu. U kunt een van de opgegeven namen selecteren of een naam invoeren in de beschikbare ruimte. Selecteer Geen als de workflow vereist dat het document de uitvoerintentie opgeeft. Een document dat niet aan de vereisten voldoet, kan niet worden gecontroleerd op de naleving.

**Identifier van de Voorwaarde van de Output:** wijst op de verwijzingsnaam die door de registratie van de naam van het outputintentieprofiel wordt gespecificeerd.

**Voorwaarde van de Output:** beschrijft de voorgenomen drukvoorwaarde. Deze vermelding kan nuttig zijn voor de ontvanger van het PDF-document.

**Naam van de Registratie (URL):** wijst op het Webadres voor meer informatie over de registratie. De URL wordt automatisch ingevoerd voor ICC-registernamen.

**Overvuld:** wijst op de staat van het opsluiten in het document. Voor compatibiliteit met PDF/X is de waarde Waar of Onwaar vereist. Als het document de overvulstatus niet opgeeft, wordt de hier opgegeven waarde gebruikt. Selecteer Ongedefinieerd laten als uw werkstroom vereist dat het document de overvulstatus opgeeft. Een document dat niet aan de vereisten voldoet, kan niet worden gecontroleerd op de naleving.

### Opties voor PDF/A-standaard {#options-for-pdf-a-standard}

Deze opties worden ingeschakeld wanneer Compatibiliteit (in het gedeelte Algemeen) is ingesteld op Acrobat 4 (PDF 1.3) of Acrobat 5 (PDF 1.4).

**wanneer niet Voldoet:** specificeert of om het dossier van de PDF tot stand te brengen als het dossier van PostScript niet aan PDF/A vereisten voldoet.

**ga verder:** creeert een dossier van de PDF zelfs als het dossier van PostScript niet aan de vereisten van de norm voldoet.

**annuleert Baan:** creeert een dossier van PDF slechts als het dossier van PostScript aan PDF/A vereisten voldoet en anders geldig is.

**Naam van het Profiel van de Intentie van de Output:** wijst op de gekarakteriseerde drukvoorwaarde waarvoor het document is voorbereid en voor naleving PDF/A wordt vereist. Selecteer Geen als de workflow vereist dat in het document uitvoerintentiegegevens worden opgegeven. Als deze informatie niet is opgegeven, wordt niet gecontroleerd of het document aan de voorschriften voldoet.

**Voorwaarde van de Output:** beschrijft de voorgenomen drukvoorwaarde. Deze vermelding is niet vereist, maar kan worden gebruikt om nuttige informatie te verstrekken aan de voorgenomen ontvanger van het document van de PDF.

## Oorspronkelijke weergaveopties {#initial-view-options}

Deze opties zijn ingedeeld in drie gebieden: Documentopties, Vensteropties en Interfaceopties. Voor instructies over de toegang tot van de Eerste meningsopties, zie [&#x200B; PDF montages &#x200B;](configuring-pdf-settings.md#add-or-edit-pdf-settings) toevoegen of uitgeven.

Als u opties wilt gebruiken, selecteert u Instellingen voor beginweergave instellen.

### Documentopties {#document-options}

De documentopties bepalen de weergave van het document in het documentvenster, zoals de zoomfactor en de schuifwijze.

**toon:** bepaalt welke ruiten en lusjes in het toepassingsvenster door gebrek worden getoond. In het venster Bladwijzers en op de pagina wordt het documentvenster geopend en wordt het tabblad Bladwijzers weergegeven.

**Lay-out van de Pagina:** bepaalt of het document op enig-pagina, onder ogen ziet-pagina, ononderbroken pagina, of ononderbroken onder ogen ziet-pagina wijze wordt bekeken.

**Vergroting:** plaatst het gezoemniveau dat wordt gebruikt om het document te tonen wanneer geopend. De standaardwaarde gebruikt de door de gebruiker ingestelde vergrotingswaarde in de voorkeuren van Acrobat of Adobe Reader.

**open aan Aantal van de Pagina:** plaatst de pagina die het document opent bij, wat gewoonlijk pagina 1 is.

>[!NOTE]
>
>Als u Standaard instelt voor de opties voor vergroting en paginalay-out, worden de afzonderlijke gebruikersinstellingen in de voorkeuren voor paginaweergave in Acrobat of Adobe Reader gebruikt.

### Vensteropties {#window-options}

De vensteropties bepalen hoe het venster in het schermgebied wordt aangepast wanneer een gebruiker het document opent. De opties hebben echter geen effect wanneer een PDF-document in een webbrowser wordt weergegeven.

**vergroot venster aan Aanvankelijke Pagina:** past het documentvenster aan flits rond de het openen pagina, volgens de opties aan die u onder de Opties van het Document selecteerde.

**Venster van het Centrum op Scherm:** Plaatst het venster in het centrum van het het schermgebied.

**Open op Volledige Wijze van het Scherm:** maximaliseert het documentvenster en toont het document zonder de menubar, de toolbar, of venstercontroles.

**toon:** Filename toont filename in de titelbar van het venster. De documenttitel wordt weergegeven in de titelbalk van het venster.

### Gebruikersinterfaceopties {#user-interface-options}

De gebruikersinterface-opties bepalen welke besturingselementen worden weergegeven of verborgen wanneer de gebruiker het document opent.

**de Bar van het Menu van de Huid:** Indien geselecteerd, verbergt de menubar

**Verberg Toolbars:** Indien geselecteerd, verbergt toolbars

**de Controles van het Venster van de Huid:** Indien geselecteerd, verbergt de venstercontroles

>[!NOTE]
>
>Als u de menubalk en de werkbalk verbergt, kunnen gebruikers alleen met behulp van sneltoetsen opties toepassen en gereedschappen selecteren wanneer ze het bestand in Acrobat openen.

## Proloog- en epiloogbestanden uploaden en downloaden {#uploading-and-downloading-prologue-and-epilogue-files}

Prolologbestanden worden gebruikt om aangepaste PostScript-code toe te voegen die wordt uitgevoerd aan het begin van elke PostScript-taak die wordt gedistilleerd. Epilog-bestanden worden gebruikt om aangepaste PostScript-code toe te voegen die aan het einde van elke PostScript-taak wordt uitgevoerd. U kunt proloog- en epiloogbestanden downloaden van de server om ze lokaal op te slaan. U kunt de bestanden downloaden om ze onafhankelijk te configureren of te uploaden naar een andere locatie of een andere computer.

Deze bestanden hebben vele doeleinden. Profielbestanden kunnen bijvoorbeeld worden bewerkt om omslagpagina&#39;s op te geven; epiloogbestanden kunnen worden bewerkt om een reeks procedures in een PostScript-bestand op te lossen. U kunt ook de proloog- en epiloogbestanden selecteren en uploaden die u met elke taak wilt verzenden.

### Een proloog- of epiloogbestand downloaden {#download-a-prologue-or-epilogue-file}

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF Settings.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Klik op Geavanceerd en vervolgens naast de optie Prologue.ps en Epilogue.ps gebruiken op Downloaden.
1. Klik op Prologue.ps of Epilogue.ps en klik op Opslaan op de pagina Prologue en Epilogue-bestanden downloaden.

### Een proloog- of epiloogbestand uploaden {#upload-a-prologue-or-epilogue-file}

1. Klik in de beheerconsole op Services > PDF Generator > Adobe PDF Settings.
1. Klik op Nieuw of klik op de naam van een instelling.
1. Klik op Geavanceerd en vervolgens naast de optie Prologue.ps en Epilogue.ps gebruiken op Uploaden.
1. Klik op de pagina Prologue uploaden en Epiloogbestanden op Bladeren om een proloog of een epiloogbestand te selecteren.
1. Zoek het bestand en klik op Openen.
1. Als u het bestand wilt gebruiken, selecteert u Prologue.ps en Epilogue.ps gebruiken in het gedeelte Geavanceerd van de instellingspagina van Adobe PDF Nieuw/Bewerken.
1. Klik op Opslaan

>[!NOTE]
>
>PDF Generator ondersteunt alleen proloog- en epiloogbestanden voor conversie van PostScript- en Encapsulated PostScript-bestanden naar PDF.
