---
title: Metagegevens van uw digitale middelen beheren in [!DNL Adobe Experience Manager].
description: Meer informatie over de typen metagegevens en hoe u met [!DNL Adobe Experience Manager Assets] metagegevens voor elementen kunt beheren, zodat u elementen gemakkelijker kunt indelen en ordenen. [!DNL Experience Manager] maakt het mogelijk elementen automatisch te ordenen en te verwerken op basis van hun metagegevens.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Metagegevens van uw digitale middelen beheren {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] bewaart meta-gegevens voor elk middel. Hierdoor kunnen elementen gemakkelijker worden gecategoriseerd en geordend en kunnen mensen die op zoek zijn naar een bepaald bedrijfsmiddel worden geholpen. Dankzij de mogelijkheid metagegevens te extraheren uit bestanden waarnaar geüpload wordt, kan het beheer van metagegevens worden geïntegreerd in de creatieve workflow. [!DNL Experience Manager Assets] Dankzij de mogelijkheid om metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van de metagegevens van de elementen. [!DNL Experience Manager Assets]

* [XMP-metadata](xmp.md).
* [Metagegevens](meta-edit.md)bewerken of toevoegen.
* [Referentie voor](meta-ref.md)metagegevensschema&#39;s.

## Waarom we metagegevens nodig hebben {#why-we-need-metadata}

Metagegevens zijn gegevens over gegevens. In dit verband verwijzen gegevens naar uw digitale middel, bijvoorbeeld een afbeelding. Metagegevens zijn essentieel voor efficiënt middelenbeheer.

Metagegevens zijn de verzameling van alle gegevens die beschikbaar zijn voor een element, maar die niet noodzakelijkerwijs in die afbeelding voorkomen. Voorbeelden van metagegevens zijn:

* Naam van het element.
* Tijdstip en datum van laatste wijziging.
* Grootte van het middel zoals het in de bewaarplaats werd opgeslagen.
* Naam van de map waarin deze zich bevindt.
* Gerelateerde elementen of toegepaste tags.

Dit zijn de basiseigenschappen van metagegevens die voor elementen [!DNL Experience Manager] kunnen worden beheerd. Hiermee kunnen gebruikers bijvoorbeeld alle elementen zien die op de laatste wijzigingsdatum zijn geordend. Dit is handig wanneer ze proberen te achterhalen welke elementen onlangs aan de opslagplaats zijn toegevoegd.

U kunt meer gegevens op hoog niveau toevoegen aan digitale elementen, bijvoorbeeld:

* Type element (is het een afbeelding, video, audioclip of document?).
* Eigenaar van het actief.
* Titel van het element.
* Beschrijving van het actief.
* Tags die aan een element zijn toegewezen.

Met meer metagegevens kunt u elementen verder indelen. Dit is handig wanneer de hoeveelheid digitale informatie toeneemt. Het is mogelijk om een paar honderd bestanden te beheren op basis van alleen de bestandsnamen. Nochtans, is deze benadering niet scalable en valt snel onder wanneer het aantal betrokken personen en het aantal beheerde activa stijgt.

Als er metagegevens worden toegevoegd, neemt de waarde van een digitaal element toe, omdat het element

* Toegankelijker - systemen en gebruikers kunnen het gemakkelijk vinden.
* Gemakkelijker te beheren - u kunt gemakkelijker middelen met de zelfde reeks eigenschappen vinden en veranderingen op hen toepassen.
* Vollediger - Hoe meer metagegevens u aan een element hebt toegevoegd, des te meer informatie en context het element bevat.

Daarom [!DNL Assets] beschikt u over de juiste middelen om metagegevens voor uw digitale elementen te maken, te beheren en uit te wisselen.

## Typen metagegevens {#types-of-metadata}

De twee basistypen metagegevens zijn technische metagegevens en beschrijvende metagegevens.

Technische metagegevens zijn handig voor softwaretoepassingen die werken met digitale elementen en mogen niet handmatig worden onderhouden. [!DNL Experience Manager Assets] en andere software bepaalt automatisch de technische metagegevens en de metagegevens kunnen veranderen wanneer het element wordt gewijzigd. De beschikbare technische metagegevens van een element zijn grotendeels afhankelijk van het bestandstype van het element. Voorbeelden van technische metagegevens zijn:

* Grootte van een bestand.
* Afmetingen (hoogte en breedte) van een afbeelding.
* Bitsnelheid van een audio- of videobestand.
* Resolutie (detailniveau) van een afbeelding.

De beschrijvende meta-gegevens zijn meta-gegevens betrokken bij het toepassingsdomein, bijvoorbeeld, de zaken die een activa uit komt. Metagegevens met een beschrijving kunnen niet automatisch worden bepaald. Deze wordt handmatig of halfautomatisch gemaakt. Een camera met GPS-functionaliteit kan bijvoorbeeld automatisch de breedte en lengte bijhouden en geotaggen aan de afbeelding toevoegen.

Vanwege de hoge kosten van de handmatige inspanningen die nodig zijn om beschrijvende metagegevens te maken, zijn er normen opgesteld om de uitwisseling van metagegevens tussen softwaresystemen en organisaties te vergemakkelijken.

[!DNL Experience Manager Assets] ondersteunt alle relevante normen voor metagegevensbeheer.

Vanwege het belang van metagegevens en de grote handmatige betrokkenheid die nodig is om metagegevens te maken, zijn er normen opgesteld die het uitwisselen van gegevens vergemakkelijken.

## Coderingsnormen {#encoding-standards}

Er zijn verschillende manieren om metagegevens in bestanden in te sluiten. Een selectie coderingsstandaarden wordt ondersteund:

* XMP: worden gebruikt door [!DNL Assets] de geëxtraheerde metagegevens op te slaan in de opslagplaats.
* ID3: voor audio- en videobestanden.
* EXIF: voor afbeeldingsbestanden.
* Overige/Verouderd: van [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel]enzovoort.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) is een open standaard die door [!DNL Experience Manager Assets] voor al meta-gegevensbeheer wordt gebruikt. De standaard biedt universele metagegevenscodering die in alle bestandsindelingen kan worden ingesloten. Adobe en andere bedrijven ondersteunen de XMP-standaard omdat deze een Rich Content Model biedt. Gebruikers van de XMP-standaard en van [!DNL Experience Manager Assets] een krachtig platform waarop u kunt bouwen. For more information, see [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

Gegevens die in deze ID3-tags zijn opgeslagen, worden weergegeven wanneer u een digitaal audiobestand afspeelt op uw computer of op een draagbare MP3-speler.

ID3-tags zijn ontworpen voor de MP3-bestandsindeling. Aanvullende informatie over indelingen:

* ID3-tags werken in MP3- en MP3PRO-bestanden.
* WAV heeft geen tags.
* WMA heeft merkgebonden markeringen die open-bronimplementatie niet toestaan.
* Ogg Vorbis gebruikt Xiph-opmerkingen die zijn ingesloten in de Ogg-container.
* AAC gebruikt een merkgebonden etiketteringsformaat.

### Exif {#exif}

Exchangeable image file format (Exif) is de meest gebruikte metagegevensindeling voor digitale fotografie. Hiermee kunt u een vaste woordenlijst met metagegevenseigenschappen insluiten in vele bestandsindelingen, zoals JPEG, TIFF, RIFF en WAV. In Exif worden metagegevens opgeslagen als paren van een metagegevensnaam en een metagegevenswaarde. Deze naam-waarde-paren voor metagegevens worden ook wel tags genoemd, maar mogen niet worden verward met de tags in [!DNL Experience Manager]. Aangezien Exif automatisch door moderne digitale camera&#39;s wordt gecreeerd en door moderne grafieksoftware wordt gesteund, kan het als laagste gemeenschappelijke noemer voor meta-gegevensbeheer worden gezien.

Een belangrijke beperking van Exif is dat een aantal populaire indelingen voor afbeeldingsbestanden, zoals BMP, GIF of PNG, dit niet ondersteunen.

Metagegevensvelden die gewoonlijk door EXIF worden gedefinieerd, zijn van technische aard en zijn van beperkte toepassing voor beschrijvend metagegevensbeheer. Daarom [!DNL Experience Manager Assets] biedt u de toewijzing van EXIF-eigenschappen in [algemene metagegevensschema](metadata-schemas.md) en in [XMP](xmp-writeback.md).

### Overige metagegevens {#other-metadata}

Andere meta-gegevens die van dossiers kunnen worden ingebed omvatten Microsoft Word, PowerPoint, Excel, etc.

## Metagegevensschema {#metadata-schemata}

Metagegevensschema&#39;s zijn vooraf gedefinieerde sets definities van metagegevenseigenschappen die in verschillende toepassingen kunnen worden gebruikt. Eigenschappen worden altijd gekoppeld aan een element. Dit houdt in dat de eigenschappen &#39;over&#39; de bron zijn.

U kunt ook uw eigen metagegevensschema&#39;s ontwerpen als er geen schema&#39;s zijn die aan uw behoeften voldoen. Dupliceer bestaande informatie niet. Binnen een organisatie, maakt het scheiden van schema&#39;s het gemakkelijker om meta-gegevens te delen. [!DNL Experience Manager] biedt u een standaardlijst met de populairste metagegevensschema&#39;s. De lijst helpt u om uw meta-gegevensstrategie te springen en snel de meta-gegevenseigenschappen te kiezen die u nodig hebt.

De ondersteunde metagegevensschema&#39;s worden hieronder weergegeven.

### Standaardmetagegevens {#standard-metadata}

* dc - [!DNL Dublin Core] is de belangrijkste en meest gebruikte reeks metagegevens .
* DICOM - Digital Imaging and Communications in Medicine.
* Iptc4xmpCore &amp; iptc4xmpExt - International Press Communications Standard bevat veel onderwerpspecifieke metagegevens.
* rdf - Resource Description Framework - voor algemene semantische webmetagegevens.
* xmp - [!DNL Extensible Metadata Platform].
* xmpBJ - Basic Job Ticketing.

### Toepassingsspecifieke metagegevens {#application-specific-metadata}

De toepassingsspecifieke metagegevens bevatten technische en beschrijvende metagegevens. Als u deze gebruikt, kunnen andere toepassingen mogelijk de meta-gegevens niet gebruiken. Als u bijvoorbeeld een element met [!DNL Adobe Photoshop] metagegevens hebt en een andere toepassing voor het renderen van afbeeldingen probeert toegang te krijgen tot de metagegevens, heeft deze mogelijk geen toegang tot de metagegevens. Als u ontdekt dat u veel toepassing-specifieke meta-gegevens in uw activa hebt, kunt u een werkschemagestap tot stand brengen die een toepassing-specifieke bezit in een standaardbezit verandert.

* ACDSee - Metagegevens die door het [!DNL ACDSee] programma worden beheerd. Zie [www.acdsee.com/](https://www.acdsee.com/).
* album - [!DNL Adobe Photoshop Album].
* cq - Gebruikt door [!DNL Experience Manager Assets].
* dam - Gebruikt door [!DNL Experience Manager Assets].
* Index - Optima SC Description Explorer.
* crs - Adobe Photoshop Camera Raw.
* lr - [!DNL Adobe Lightroom].
* mediapro - IView MediaPro.
* MicrosoftPhoto &amp; MP - Microsoft Photo.
* pdf en pdfx.
* photoshop &amp; psAux - [!DNL Adobe Photoshop].

### Metagegevens van Digital Rights Management {#digital-rights-management-metadata}

* CC - [!DNL Creative Commons].
* [!DNL XMPRights].
* plus - [Picture Licensing Universal System](https://www.useplus.com).
* prism - https://www.idealliance.org/prism-metadata Publishing Requirements for Industry Standard Metadata.
* PRL - PRISM Rights Language.
* PUR - PRISM-gebruiksrechten.
* xmpPlus - Integratie van PLUS met XMP.

### Specifieke metagegevens voor fotografie {#photography-specific-metadata}

* EXIF - Technische informatie van camera, inclusief GPS-positie.
* CRS - [!DNL Camera Raw] schema.
* Iptc4xmpCore en iptc4xmpExt.
* TIFF - metagegevens van afbeeldingen (niet alleen voor TIFF-afbeeldingen).

### Afdrukspecifieke metagegevens {#print-specific-metadata}

* pdf en pdfx - Adobe PDF en toepassingen van derden.
* prism - [www.prismstandard.org](https://www.prismstandard.org) Publishing Requirements for Industry Standard Metadata.
* xmp.
* xmpPG - XMP-metagegevens voor gepagineerde tekst.

### Multimediaspecifieke metagegevens {#multimedia-specific-metadata}

* xmpDM - [!DNL Dynamic Media].
* xmpMM - Mediabeheer.

## Workflows met metagegevens {#metadata-driven-workflows}

Door workflows te maken die op metagegevens zijn gebaseerd, kunt u bepaalde processen automatiseren, wat de efficiëntie ten goede komt. In een workflow met metagegevens leest het workflowbeheersysteem de workflow en wordt er dus een vooraf gedefinieerde actie uitgevoerd. U kunt bijvoorbeeld op een aantal manieren werkstromen gebruiken die zijn gebaseerd op metagegevens:

* De workflow kan controleren of een afbeelding een titel heeft of niet. Als dit niet het geval is, wordt een melding weergegeven om een titel toe te voegen.
* De workflow kan controleren of een copyrightkennisgeving op een middel distributie toestaat of niet. Het systeem verzendt het element dan ook naar de ene of de andere server.
* Een workflow kan controleren op elementen zonder vooraf gedefinieerde, verplichte metagegevens of elementen met *ongeldige* metagegevens.
