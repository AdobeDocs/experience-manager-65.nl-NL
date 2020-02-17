---
title: Ondersteuning voor XMP-metagegevens in AEM-elementen
description: Meer informatie over de XMP-metagegevensstandaard (Extensible Metadata Platform) die door AEM Assets wordt gebruikt voor metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal toepassingen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# XMP-metagegevens {#xmp-metadata}

XMP (Extensible Metadata Platform) is de metagegevensstandaard die wordt gebruikt door AEM Assets voor al het metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal toepassingen.

XMP biedt niet alleen universele metagegevenscodering die in alle bestandsindelingen kan worden ingesloten, maar biedt ook een rijk [inhoudsmodel](xmp.md#xmp-core-concepts) en wordt [ondersteund door Adobe](xmp.md#advantages-of-xmp) en andere bedrijven, zodat gebruikers van XMP in combinatie met AEM Assets een krachtig platform hebben waarop kan worden gebouwd.

De [XMP-specificatie](https://www.adobe.com/devnet/xmp.html) is verkrijgbaar bij Adobe.

## Wat is XMP? {#what-is-xmp}

AEM Assets biedt native ondersteuning voor het XMP - het Extensible Metadata Platform onder leiding van Adobe. XMP is een standaard voor het verwerken en opslaan van gestandaardiseerde en merkgebonden metagegevens in digitale elementen. XMP is ontworpen als de algemene standaard die meerdere toepassingen in staat stelt effectief met metagegevens te werken.

Productieprofessionals gebruiken bijvoorbeeld de ingebouwde XMP-ondersteuning in Adobe-toepassingen om informatie door te geven in meerdere bestandsindelingen. De AEM Assets-opslagplaats extraheert de XMP-metagegevens en gebruikt deze om de levenscyclus van de inhoud te beheren en biedt de mogelijkheid om automatiseringsworkflows te maken.

XMP is gestandaardiseerd hoe metagegevens worden gedefinieerd, gemaakt en verwerkt door een gegevensmodel, een opslagmodel en schema&#39;s op te geven. Al deze concepten worden behandeld in deze sectie.

Alle oudere metagegevens van EXIF, ID3 of Microsoft Office worden automatisch vertaald naar XMP, dat kan worden uitgebreid voor ondersteuning van klantspecifiek metagegevensschema, zoals productcatalogi.

Metagegevens in XMP bestaan uit een set eigenschappen. Deze eigenschappen worden altijd geassocieerd met een bepaalde entiteit die als middel wordt bedoeld; dat wil zeggen dat de eigenschappen &quot;over&quot; de bron zijn. In het geval van XMP is de bron altijd het element.

### Adobe {#adobe}

Adobe heeft de XMP-standaard voor het eerst geïntroduceerd als onderdeel van het Adobe Acrobat-softwareproduct. Sindsdien is de XMP-standaard op grote schaal toegepast.

### XMP-ecosysteem {#xmp-ecosystem}

XMP definieert een [metagegevensmodel](https://en.wikipedia.org/wiki/Metadata) dat kan worden gebruikt met elke gedefinieerde set metagegevensitems. XMP definieert ook bepaalde [schema&#39;s](https://en.wikipedia.org/wiki/XML_schema) voor basiseigenschappen die nuttig zijn voor het opnemen van de geschiedenis van een bron tijdens het doorlopen van meerdere verwerkingsstappen, van het fotograferen, [scannen](https://en.wikipedia.org/wiki/Image_scanner)of ontwerpen als tekst, via fotomewerkingsstappen (zoals [uitsnijden](https://en.wikipedia.org/wiki/Cropping_%28image%29) of kleuraanpassing) tot het samenvoegen in een uiteindelijke afbeelding. Met XMP kan elk softwareprogramma of apparaat onderweg zijn eigen informatie toevoegen aan een digitale bron, die vervolgens in het uiteindelijke digitale bestand kan worden bewaard.

XMP wordt het meest algemeen geserialiseerd en opgeslagen gebruikend een ondergroep van het Kader [van de Beschrijving van het](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) Middel [W3C](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF), dat beurtelings in [XML](https://en.wikipedia.org/wiki/XML)wordt uitgedrukt.

## Voordelen van XMP {#advantages-of-xmp}

XMP heeft de volgende voordelen ten opzichte van andere coderingsstandaarden en -schema&#39;s:

* Op XMP gebaseerde metagegevens zijn zeer krachtig en fijnkorrelig.
* Met XMP kunt u meerdere waarden voor één eigenschap hebben.
* XMP heeft gestandaardiseerde codering, waarmee u metagegevens eenvoudig kunt uitwisselen.
* XMP kan worden uitgebreid. U kunt aanvullende informatie aan uw elementen toevoegen.

### Uitbreidbaar {#extensible}

De XMP-standaard is zo ontworpen dat deze uitbreidbaar is, zodat u aangepaste typen metagegevens kunt toevoegen aan de XMP-gegevens. EXIF heeft daarentegen geen vaste lijst met eigenschappen die niet kunnen worden uitgebreid.

>[!NOTE]
>
>XMP staat meestal niet toe dat binaire gegevenstypen worden ingesloten. Als u binaire gegevens bijvoorbeeld wilt meenemen in XMP-miniatuurafbeeldingen, moeten deze worden gecodeerd in een XML-vriendelijke indeling, zoals `Base64`.

## XMP Core-concepten {#xmp-core-concepts}

De volgende secties beschrijven de kernconcepten van XMP, met inbegrip van namespaces en schema&#39;s, eigenschappen en waarden, en taalalternatieven.

### Naamruimten en Schemata {#namespaces-and-schemata}

Een XMP-schema is een set eigenschapnamen in een algemene XML-naamruimte die het gegevenstype en beschrijvende informatie bevat. Een XMP-schema wordt aangeduid met de XML-naamruimte-URI. Het gebruik van naamruimten voorkomt conflicten tussen eigenschappen in verschillende schema&#39;s die dezelfde naam maar een andere betekenis hebben.

De `Creator` eigenschap in twee onafhankelijk ontworpen schema&#39;s kan bijvoorbeeld de persoon zijn die het element heeft gemaakt of de toepassing die het element heeft gemaakt (bijvoorbeeld Adobe Photoshop).

### Eigenschappen en waarden {#properties-and-values}

XMP kan eigenschappen van één of meerdere schema&#39;s omvatten.

Een standaardsubset die door veel Adobe-toepassingen wordt gebruikt, kan bijvoorbeeld het volgende zijn:

* Dublin-kernschema: dc:title, dc:creator, dc:subject, dc:format, dc:rights
* XMP-basisschema: xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* XMP-schema voor rechtenbeheer: xmpRights:WebStatement, xmpRights:Marked
* XMP-schema voor mediabeheer: xmpMM:DocumentID

### Taalalternatieven {#language-alternatives}

Met XMP kunt u een `xml:lang` eigenschap aan teksteigenschappen toevoegen om de taal van de tekst op te geven.
