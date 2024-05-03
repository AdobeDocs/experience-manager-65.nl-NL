---
title: Overzicht van AEM Document Services
description: AEM Document Services is een set OSGi Services voor het maken, samenstellen en beveiligen van PDF-documenten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services
exl-id: 4c8a3877-1a3c-410d-ad1f-69c73ba4fcc1
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 0%

---

# Overzicht van AEM Document Services{#overview-of-aem-document-services}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html) |
| AEM 6,5 | Dit artikel |


AEM Document Services is een set OSGi Services voor het maken, samenstellen en beveiligen van PDF-documenten. Document Services bevatten de volgende services:

## Uitvoerservice {#output-service}

Met de uitvoerservice kunt u documenten in verschillende indelingen maken, zoals PDF, laserprinterindelingen en labelprinterindelingen. Indelingen voor laserprinters zijn PostScript en Printer Control Language (PCL). In de volgende lijst ziet u de indeling van labelprinters:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Een document kan naar een netwerkprinter, een lokale printer of een bestand op het bestandssysteem worden verzonden. De service Uitvoer voegt XML-formuliergegevens samen met een formulierontwerp om een document te genereren. De service Uitvoer kan een document genereren zonder XML-formuliergegevens samen te voegen in het document. De primaire workflow is echter het samenvoegen van gegevens in het document.

>[!NOTE]
>
>Een formulierontwerp wordt meestal gemaakt met Designer. Zie Help bij Designer voor informatie over het maken van formulierontwerpen voor de Output-service.

Als u de Output-service gebruikt om XML-gegevens samen te voegen met een formulierontwerp, is het resultaat een niet-interactief PDF-document. In een niet-interactief PDF-document kunnen gebruikers geen gegevens invoeren in de desbetreffende velden. U kunt daarentegen de Forms-service gebruiken om een interactief PDF-formulier te maken waarmee gebruikers gegevens in de betreffende velden kunnen invoeren.

De volgende vier de dienstverrichtingen van de Output zijn beschikbaar voor gebruik:

* **generatePDFOuput**: Voegt een formulierontwerp samen met gegevens om een PDF-document te genereren
* **generatePrintedOutput**: Voegt een formulierontwerp samen met formuliergegevens om een document te genereren dat naar een laser- of labelnetwerkprinter wordt verzonden

* **generatePDFOutputBatch**: Voegt meerdere sjablonen samen met meerdere records met gegevens in één aanroep om een batch PDF-bestanden te genereren. Er is ook een mogelijkheid om één PDF te genereren door alle PDF te combineren
* **generatePrintedOutputBatch**: Voegt meerdere sjablonen samen met meerdere records met gegevens in één aanroep om een batch gedrukte documenten te genereren (PS, PCL, ZPL, DPL, IPL, TPCL). U kunt ook één afdrukdocument genereren.

## Assembler-service {#assembler-service}

Met de service Assembler kunt u PDF- en XDP-documenten combineren, opnieuw rangschikken en vergroten en informatie over PDF-documenten opvragen. Elke baan die aan de dienst van de Assembler wordt voorgelegd omvat een document van XML van de Beschrijving van het Document (DDX), brondocumenten, en externe middelen (koorden en grafiek). Het DDX-document bevat instructies voor het gebruik van de brondocumenten om een set resulterende documenten te maken.

Naast bovengenoemde mogelijkheden, de dienst van de Assembler:

* Hiermee converteert u PDF-documenten naar PDF/A-standaard.
* Hiermee worden PDF forms, XML-formulieren (gemaakt in Designer) en PDF forms (gemaakt in Acrobat) getransformeerd naar PDF/A-1b, PDF/A-2b en PDFA/A-3b.
* Hiermee converteert u ondertekende of niet-ondertekende PDF-documenten (digitale handtekeningen vereist).
* Hiermee wordt de compatibiliteit van een PDF/A-bestand gevalideerd en zo nodig geconverteerd.

### Informatie over DDX {#about-ddx}

Wanneer het gebruiken van de dienst van de Assembler, gebruik een op XML-Gebaseerde taal genoemd XML van de Beschrijving van het Document (DDX) om de output te beschrijven u wilt. DDX is een verklarende prijsverhogingstaal de waarvan elementen bouwstenen van documenten vertegenwoordigen. Deze bouwstenen omvatten PDF-documenten, XDP-documenten, XDP-formulierfragmenten en andere elementen, zoals opmerkingen, bladwijzers en gestileerde tekst.

In het DDX-document kunnen resultaatdocumenten met de volgende kenmerken worden opgegeven:

* PDF-document dat is samengesteld uit meerdere PDF-documenten
* Meerdere PDF-documenten die zijn gesplitst van één PDF-document
* PDF Portfolio dat een op zichzelf staand gebruikersinterface en veelvoudige PDF en niet-PDF documenten omvat
* XDP-document dat is samengesteld uit meerdere XDP-documenten
* XDP-document dat XML-fragmenten bevat die dynamisch in een XDP-document worden ingevoegd
* PDF-document dat een XDP-document verpakt
* XML-bestanden die de kenmerken van een PDF-document rapporteren. Tot de gerapporteerde kenmerken behoren tekst, opmerkingen, formuliergegevens, bestandsbijlagen, bestanden die worden gebruikt in PDF-Portfolio&#39;s, bladwijzers en PDF-eigenschappen. PDF-eigenschappen zijn onder andere formuliereigenschappen, pagina-rotatie en documentauteur.

U kunt DDX gebruiken om de documenten van PDF als deel van documentassemblage of demontage te verhogen. U kunt een willekeurige combinatie van de volgende effecten opgeven:

* Watermerken of achtergronden toevoegen aan of verwijderen uit geselecteerde pagina&#39;s.
* Kop- en voetteksten toevoegen aan of verwijderen uit geselecteerde pagina&#39;s.
* Hiermee verwijdert u de structuur en navigatiemogelijkheden van een PDF-pakket of PDF-Portfolio. Het resultaat is één PDF-bestand.
* Paginalabels opnieuw nummeren. Paginalabels worden doorgaans gebruikt voor paginanummering.
* Metagegevens uit een ander brondocument importeren.
* Bestandsbijlagen, bladwijzers, koppelingen, opmerkingen en JavaScript toevoegen of verwijderen.
* Stel de oorspronkelijke weergavekenmerken in en optimaliseer deze voor weergave op het web.
* Machtigingen instellen voor gecodeerde PDF.
* Pagina&#39;s roteren of inhoud roteren en verschuiven op pagina&#39;s.
* Wijzig de grootte van geselecteerde pagina&#39;s.
* Gegevens samenvoegen met een op XFA gebaseerde PDF.

U kunt een eenvoudige invoerkaart gebruiken om de locaties van de bron en de resulterende documenten op te geven. U kunt ook de volgende externe gegevens-URL-typen gebruiken:

* Bestand
* FTP
* HTTP/HTTPS

## Doc Assurance Service {#doc-assurance-service}

Met de Doc Assurance Service kunt u documenten versleutelen en ontsleutelen, de functionaliteit van Adobe Reader uitbreiden met extra gebruiksrechten en digitale handtekeningen toevoegen aan uw documenten. Uw gebruikers kunnen gemakkelijk met PDF forms en documenten in wisselwerking staan, terwijl uw organisatie veiligheid, archivering, en naleving verbetert.

De Doc Assurance-service bevat drie services: handtekening, versleuteling en reader-extensie.

### Handtekeningenservice {#signature-service}

Met de service Handtekening kunt u werken met digitale handtekeningen en documenten op de AEM server. De service Handtekening wordt bijvoorbeeld doorgaans in de volgende situaties gebruikt:

* De AEM server certificeert een formulier voordat het naar een gebruiker wordt verzonden om te worden geopend met Acrobat of Adobe Reader.
* De AEM server valideert een handtekening die aan een formulier is toegevoegd met Acrobat of Adobe Reader.
* De AEM server ondertekent een formulier namens een openbare notaris.

De handtekeningservice krijgt toegang tot certificaten en referenties die zijn opgeslagen in de vertrouwde opslag.

### Coderingsservice {#encryption-service}

Met de coderingsservice kunt u documenten versleutelen en ontsleutelen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. U kunt het volledige document van de PDF (met inbegrip van zijn inhoud, meta-gegevens, en gehechtheid), alles behalve zijn meta-gegevens, of slechts de gehechtheid coderen. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document met een wachtwoord is versleuteld, moet de gebruiker het wachtwoord voor openen opgeven voordat het document in Adobe Reader of Acrobat kan worden weergegeven. Als een PDF-document met een certificaat is versleuteld, moet de gebruiker het PDF-document decoderen met een persoonlijke sleutel (certificaat). De persoonlijke sleutel die wordt gebruikt voor het decoderen van het PDF-document, moet overeenkomen met de openbare sleutel waarmee het document is versleuteld.

### Reader Extension Service {#reader-extension-service}

De dienst van de Uitbreidingen van de Reader laat uw organisatie toe om interactieve documenten van de PDF gemakkelijk te delen door de functionaliteit van Adobe Reader met extra gebruiksrechten uit te breiden. De service Reader Extensions werkt met Adobe Reader 7.0 of hoger. De service voegt gebruiksrechten toe aan een PDF-document. Met deze actie activeert u functies die gewoonlijk niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document. Gebruikers van derden hebben geen extra software of plug-ins nodig om met documenten waarvoor rechten zijn ingeschakeld te kunnen werken.

Wanneer voor PDF-documenten de juiste gebruiksrechten zijn toegevoegd, kunnen ontvangers de volgende activiteiten uitvoeren vanuit Adobe Reader:

* PDF-documenten en -formulieren online of offline invullen, zodat ontvangers kopieën lokaal kunnen opslaan voor hun records en de toegevoegde gegevens intact kunnen houden
* PDF-documenten opslaan op een lokale vaste schijf om het originele document en eventuele aanvullende opmerkingen, gegevens of bijlagen te behouden
* Bestanden en mediaclips aan PDF-documenten koppelen
* Onderteken, certificeer en authenticeer PDF-documenten door digitale handtekeningen toe te passen met PKI-technologieën (Public Key Infrastructure) die industriestandaard zijn
* Ingevulde of geannoteerde PDF documenten elektronisch verzenden
* Gebruik PDF-documenten en -formulieren als intuïtieve ontwikkelfront-end voor interne databases en webservices
* Deel PDF-documenten met anderen, zodat revisoren opmerkingen kunnen toevoegen met intuïtieve opmaakgereedschappen. Deze gereedschappen zijn onder andere elektronische notities, stempels, hooglichten en doorhalen van tekst. Dezelfde functies zijn beschikbaar in Acrobat.
* Decodering van streepjescodes voor formulieren ondersteunen.

Deze speciale gebruikersmogelijkheden worden automatisch geactiveerd wanneer een PDF-document met toegangsrechten wordt geopend in Adobe Reader. Wanneer de gebruiker klaar is met het werken met een document waarvoor rechten zijn ingeschakeld, worden deze functies weer uitgeschakeld in Adobe Reader. Ze blijven uitgeschakeld totdat de gebruiker een ander PDF-document met ingeschakelde rechten ontvangt.

Uit de doos, is de dienst DocAssurance niet beschikbaar voor gebruik. Om de dienst DocAssurance te vormen, zie [Installeren en configureren van Document Services](../../forms/using/install-configure-document-services.md).

## Naar printerservice verzenden {#send-to-printer-service}

Send To Printer Service biedt API waarmee u documenten naar een opgegeven printer kunt verzenden voor afdrukken.
