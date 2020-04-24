---
title: Metagegevens voor digitale middelen beheren in [!DNL Adobe Experience Manager].
description: Meer informatie over de typen metagegevens en hoe u met [!DNL Adobe Experience Manager Assets] metagegevens voor elementen kunt beheren, zodat u elementen gemakkelijker kunt indelen en ordenen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: abc4821ec3720969bf1c2fb068744c07477aca46

---


# Metagegevens voor digitale elementen beheren {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] bewaart meta-gegevens voor elk middel. Dit maakt het gemakkelijker om middelen in te delen en te organiseren en helpt mensen die een bepaald goed zoeken. Dankzij de mogelijkheid metagegevens te extraheren uit bestanden waarnaar geüpload wordt, kan het beheer van metagegevens worden geïntegreerd in de creatieve workflow. [!DNL Experience Manager Assets] Dankzij de mogelijkheid om willekeurige metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van de metagegevens van de elementen. [!DNL Experience Manager Assets]

* [XMP-metagegevens](xmp.md)
* [Metagegevens bewerken of toevoegen](meta-edit.md)
* [Referentie metagegevensschema](meta-ref.md)

## Waarom we metagegevens nodig hebben {#why-we-need-metadata}

Metagegevens zijn gegevens over gegevens. In dit verband verwijzen de gegevens naar het element dat u behandelt, bijvoorbeeld een afbeelding. Metagegevens zijn belangrijk omdat gebruikers elementen efficiënter kunnen beheren.

Metagegevens zijn de verzameling van alle gegevens die beschikbaar zijn voor deze afbeelding, maar die niet noodzakelijkerwijs in die afbeelding staan, bijvoorbeeld:

* de naam van het element
* de datum en het tijdstip waarop deze voor het laatst is gewijzigd
* de grootte van de afbeelding zoals deze is opgeslagen in de opslagplaats
* de naam van de map waarin deze zich bevindt

Dit zijn de basiseigenschappen van metagegevens die voor elementen [!DNL Experience Manager] kunnen worden beheerd. Hiermee kunnen gebruikers bijvoorbeeld alle elementen zien die op de laatste wijzigingsdatum zijn geordend. Dit is handig wanneer ze proberen te achterhalen welke elementen onlangs aan de opslagplaats zijn toegevoegd.

U kunt meer gegevens op hoog niveau toevoegen aan digitale elementen, bijvoorbeeld:

* het type element (is het een afbeelding, video, audioclip of document?)
* de eigenaar van het actief
* de titel van het actief
* de beschrijving van het actief
* de labels die aan een element zijn toegewezen

Met meer metagegevens kunt u elementen verder indelen. Dit is handig wanneer de hoeveelheid digitale informatie toeneemt. Hoewel het voor één enkele persoon mogelijk is om een lijst van een paar honderd dossiers te beheren eenvoudig die op hun dossiernamen worden gebaseerd, is deze benadering ontoereikend wanneer het aantal betrokken personen en het aantal beheerde activa groeit.

Wanneer metagegevens aan elementen worden toegevoegd, neemt de waarde van het element toe omdat het element

* toegankelijker - mensen kunnen het veel gemakkelijker vinden
* eenvoudiger te beheren - u kunt gemakkelijker middelen vinden met dezelfde set eigenschappen en er wijzigingen op toepassen
* complexer - hoe meer metagegevens u aan een element hebt toegevoegd, des te belangrijker het beheer van metagegevens wordt

Daarom [!DNL Assets] beschikt u over de juiste middelen om metagegevens voor uw digitale elementen te maken, te beheren en uit te wisselen.

## Metagegevens: basiskennis {#metadata-basics}

Metagegevens worden uit elementen geëxtraheerd wanneer deze worden geïmporteerd (ingestort). Bovendien kunt u elementen nog verder categoriseren door metagegevens toe te voegen.

In deze sectie worden de typen metagegevens en coderingsnormen besproken.

### Typen metagegevens {#types-of-metadata}

Er zijn twee basistypen metagegevens:

* technische metagegevens
* beschrijvende metagegevens

#### Technische metagegevens {#technical-metadata}

Technische metagegevens zijn handig voor softwaretoepassingen die werken met digitale elementen en mogen niet handmatig worden onderhouden. Technische metagegevens kunnen automatisch worden bepaald door [!DNL Experience Manager Assets] en andere software en kunnen worden gewijzigd wanneer het element wordt gewijzigd. De beschikbare technische metagegevens van een element zijn grotendeels afhankelijk van het bestandstype van het element. Voorbeelden van technische metagegevens zijn:

* de grootte van een bestand
* de afmetingen (hoogte en breedte) van een afbeelding
* de bitsnelheid van een audio- of videobestand
* de resolutie (detailniveau) van een afbeelding

#### Beschrijvende metagegevens {#descriptive-metadata}

De beschrijvende meta-gegevens zijn meta-gegevens betrokken bij het toepassingsdomein, bijvoorbeeld, de zaken die een activa uit komt. Metagegevens met een beschrijving kunnen niet automatisch worden bepaald. Deze moet handmatig of halfautomatisch worden gemaakt. Een camera met GPS-functionaliteit kan bijvoorbeeld automatisch de breedte- en lengtegraad bijhouden van een afbeelding die is gemaakt en deze informatie toevoegen aan de metagegevens van de afbeelding.

Vanwege de hoge kosten van de handmatige inspanningen die nodig zijn om beschrijvende metagegevens te maken, zijn er normen opgesteld om de uitwisseling van metagegevens tussen softwaresystemen en organisaties te vergemakkelijken.

[!DNL Experience Manager Assets] ondersteunt alle relevante normen voor metagegevensbeheer.

Vanwege het belang van metagegevens en de grote handmatige betrokkenheid die nodig is om metagegevens te maken, zijn er normen opgesteld die het uitwisselen van gegevens vergemakkelijken.

### Coderingsstandaarden {#encoding-standards}

Er zijn verschillende manieren waarop metagegevens in bestanden kunnen worden ingesloten. Een selectie coderingsstandaarden wordt ondersteund:

* XMP: worden gebruikt door [!DNL Assets] de geëxtraheerde metagegevens op te slaan in de opslagplaats.
* ID3: voor audio- en videobestanden.
* EXIF: voor afbeeldingsbestanden.
* Overige/Verouderd: vanuit Microsoft Word, PowerPoint, Excel enzovoort.

#### XMP {#xmp}

XMP betekent Extensible Metadata Platform en is de standaard voor metagegevens die wordt gebruikt [!DNL Experience Manager Assets] voor al het metagegevensbeheer. XMP biedt niet alleen universele metagegevenscodering die in alle bestandsindelingen kan worden ingesloten, maar biedt ook een rijk inhoudsmodel en wordt ondersteund door Adobe en andere bedrijven, zodat gebruikers van XMP in combinatie met een krachtig platform [!DNL Experience Manager Assets] kunnen bouwen.

#### ID3 {#id}

Gegevens die in deze ID3-tags zijn opgeslagen, worden weergegeven wanneer u een digitaal audiobestand afspeelt op uw computer of op een draagbare MP3-speler.

ID3-tags zijn ontworpen voor de MP3-bestandsindeling. Aanvullende informatie over indelingen:

* ID3-tags werken in MP3- en MP3pro-bestanden.
* WAV heeft geen tags.
* WMA heeft merkgebonden markeringen die open bronimplementatie niet toestaan.
* Ogg Vorbis gebruikt Xiph-opmerkingen die zijn ingesloten in de Ogg-container.
* AAC gebruikt een merkgebonden etiketteringsformaat.

#### EXIF {#exif}

EXIF betekent Exchangeable image file format en is de populairste metagegevensindeling die wordt gebruikt voor digitale fotografie. Hiermee kunt u een vaste woordenlijst met metagegevenseigenschappen insluiten in een aantal bestandsindelingen, zoals JPEG, TIFF, RIFF en WAV.

Een belangrijke beperking van EXIF is dat deze niet wordt ondersteund door populaire indelingen voor afbeeldingsbestanden, zoals BMP, GIF of PNG.

EXIF slaat metagegevens op als paren van een metagegevensnaam en een metagegevenswaarde. Deze naam-waarde-paren voor metagegevens worden ook wel tags genoemd, maar mogen niet worden verward met de tags in [!DNL Experience Manager].

Aangezien EXIF automatisch door moderne digitale camera&#39;s wordt gecreeerd en door moderne grafieksoftware wordt gesteund, kan het als laagste gemeenschappelijke noemer voor meta-gegevensbeheer worden gezien.

De meeste metagegevensvelden die door EXIF worden gedefinieerd, zijn van zeer technische aard en van beperkte toepassing voor het beheer van beschrijvende metagegevens. Daarom [!DNL Assets] biedt u de toewijzing van EXIF-eigenschappen in [algemene metagegevensschema](metadata-schemas.md) en in [XMP](xmp-writeback.md), de krachtige metagegevensindeling die [!DNL Assets] gebruikt wordt voor metagegevensbeheer.

#### Andere metagegevens {#other-metadata}

Andere meta-gegevens die van dossiers kunnen worden ingebed omvatten Microsoft Word, PowerPoint, Excel, etc.

## Metagegevensschema {#metadata-schemata}

Metagegevensschema&#39;s zijn vooraf gedefinieerde sets definities van metagegevenseigenschappen die in een groot aantal toepassingen kunnen worden gebruikt. Eigenschappen worden altijd aan een element gekoppeld, wat betekent dat de eigenschappen over de bron gaan.

U kunt ook uw eigen schema&#39;s voor metagegevens ontwerpen als er geen bestaan die aan uw behoeften voldoen (zorg er echter voor dat u iets dat al bestaat, niet dupliceert). Binnen een organisatie, maakt het scheiden van schema&#39;s het gemakkelijker om meta-gegevens onder organisaties te delen.

[!DNL Experience Manager] biedt u een lijst van de meest populaire metagegevensschema&#39;s, waarmee u uw strategie voor metagegevens kunt starten en de gewenste eigenschappen voor metagegevens kunt kiezen in een reeds gedefinieerd schema.

De ondersteunde metagegevensschema&#39;s worden in de volgende sectie weergegeven.

### Standaardmetagegevens {#standard-metadata}

* dc - Dublin Core - de belangrijkste en meest gebruikte reeks metagegevens
* DICOM - Digital Imaging and Communications in Medicine
* IPTC4xmpCore &amp; iptc4xmpExt - International Press Communications Standard - veel onderwerpspecifieke metagegevens
* rdf - Resource Description Framework - voor algemene semantische webmetagegevens
* xmp - Extensible Metadata Platform
* xmpBJ - Basic Job Ticketing

### Toepassingsspecifieke metagegevens {#application-specific-metadata}

>[!NOTE]
>
>Toepassingsspecifieke metagegevens omvatten technische en beschrijvende metagegevens. Als u deze gebruikt, kunnen andere toepassingen mogelijk de meta-gegevens niet gebruiken. Als u bijvoorbeeld een element hebt met Adobe Photoshop-metagegevens en een andere toepassing voor het renderen van afbeeldingen probeert toegang te krijgen tot de metagegevens, is dat mogelijk niet het geval.
>
>Als u ontdekt dat u veel toepassing-specifieke meta-gegevens in uw activa hebt, kunt u een werkschemastap tot stand brengen die de toepassing-specifieke bezit in een norm verandert.

* acdsee - metagegevens beheerd door het ACDSee-programma [www.acdsee.com/](https://www.acdsee.com/)
* album - Adobe Photoshop Album
* cq - gebruikt door [!DNL Experience Manager Assets]
* dam - gebruikt door [!DNL Experience Manager Assets]
* dex - Optima SC Description Explorer
* crs - Adobe Photoshop Camera Raw
* lr - Adobe Lightroom
* mediapro - IView MediaPro
* Microsoft Photo and MP - Microsoft Photo
* pdf amd pdfx
* Photoshop &amp; psAux - Adobe Photoshop

### Metagegevens van Digital Rights Management {#digital-rights-management-metadata}

* cc - creative commons
* xmpRights
* plus - Picture Licensing Universal System - https://www.useplus.com/
* prism - https://www.idealliance.org/prism-metadata Publishing Requirements for Industry Standard Metadata
* prl - Prism Rights Language
* pur - Rechten van riskgebruik
* xmpPlus - integratie van PLUS met XMP

### Fotografiespecifieke metagegevens {#photography-specific-metadata}

* exif - veel technische informatie van de camera, waaronder de GPS-positie
* crs - photoshop camera raw
* Iptc4xmpCore en iptc4xmpExt
* TIFF - metagegevens van afbeeldingen (niet alleen voor TIFF-afbeeldingen)

### Afdrukspecifieke metagegevens {#print-specific-metadata}

* pdf en pdfx - Adobe PDF en toepassingen van derden
* prism - [www.prismstandard.org](https://www.prismstandard.org) Publicatie-vereisten voor industriestandaard metagegevens
* xmp
* xmpPG - xmp voor gepagineerde tekst

### Multimediaspecifieke metagegevens {#multimedia-specific-metadata}

* xmpDM - Dynamische media
* xmpMM - Mediabeheer

## Workflows met metagegevens {#metadata-driven-workflows}

Door workflows te maken die op metagegevens zijn gebaseerd, kunt u sommige processen automatiseren, wat de efficiëntie ten goede komt. In een workflow met metagegevens leest het workflowbeheersysteem de workflow en wordt er dus een vooraf gedefinieerde actie uitgevoerd.

U kunt bijvoorbeeld op een aantal manieren werkstromen gebruiken die zijn gebaseerd op metagegevens:

* Met de workflow kunt u controleren of een afbeelding een titel heeft. Als dit niet het geval is, wordt een bepaalde gebruiker door het systeem op de hoogte gesteld van het toevoegen van een titel.
* De workflow kan controleren of een copyrightkennisgeving op een middel distributie mogelijk maakt. Als dit het geval is, verzendt het systeem het middel naar één server. Als dit niet het geval is, verzendt het systeem het element naar een andere server.
