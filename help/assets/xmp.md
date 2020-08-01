---
title: Ondersteuning voor XMP metagegevens in [!DNL Adobe Experience Manager Assets].
description: Leer meer over de metagegevensstandaard (Extensible Metadata Platform) van de XMP die [!DNL Experience Manager Assets] wordt gebruikt voor metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal verschillende toepassingen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 19%

---


# XMP-metadata {#xmp-metadata}

XMP (Extensible Metadata Platform) is de metagegevensstandaard die wordt gebruikt [!DNL Adobe Experience Manager Assets] voor al het metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal verschillende toepassingen.

Naast het aanbieden van universele meta-gegevenscodering die in alle dossierformaten kan worden ingebed, verstrekt XMP een rijk [inhoudsmodel](xmp.md#xmp-core-concepts) en door Adobe [en andere bedrijven wordt](xmp.md#advantages-of-xmp) gesteund, zodat de gebruikers van XMP in combinatie met [!DNL Assets] een krachtig platform om op te bouwen.

De [XMP specificatie](https://www.adobe.com/devnet/xmp.html) is beschikbaar bij Adobe.

## Wat is XMP? {#what-is-xmp}

[!DNL Assets] native ondersteunt het XMP - het Extensible Metadata Platform dat wordt geleid door Adobe. XMP is een standaard voor het verwerken en opslaan van gestandaardiseerde en merkgebonden metagegevens in digitale elementen. XMP wordt ontworpen om de gemeenschappelijke norm te zijn die veelvoudige toepassingen toestaat om effectief met meta-gegevens te werken.

Productieprofessionals gebruiken bijvoorbeeld de ingebouwde XMP ondersteuning binnen toepassingen om informatie in meerdere indelingen door te geven. [!DNL Assets] opslagplaats extraheert de XMP metagegevens en gebruikt deze om de levenscyclus van de inhoud te beheren en biedt de mogelijkheid om automatiseringsworkflows te maken.

XMP standaardiseren hoe metagegevens worden gedefinieerd, gemaakt en verwerkt door een gegevensmodel, een opslagmodel en schema&#39;s op te geven. Al deze concepten worden behandeld in deze sectie.

Alle oudere meta-gegevens van EXIF, ID3, of Microsoft Office wordt automatisch vertaald aan XMP, die kan worden uitgebreid om klant-specifiek meta-gegevensschema, zoals productcatalogi te steunen.

Metagegevens in XMP bestaan uit een set eigenschappen. Deze eigenschappen worden altijd geassocieerd met een bepaalde entiteit die als middel wordt bedoeld; dat wil zeggen dat de eigenschappen &quot;over&quot; de bron zijn. In het geval van XMP is de bron altijd het middel.

### Adobe {#adobe}

Adobe introduceerde eerst de XMP standaard als onderdeel van het Adobe Acrobat-softwareproduct. Sindsdien is de XMP norm op grote schaal aangenomen.

### XMP ecosysteem {#xmp-ecosystem}

XMP definieert een [metadatamodel](https://nl.wikipedia.org/wiki/Metadata) dat kan worden gebruikt met elke gedefinieerde set metadataitems. XMP definieert ook bepaalde [schema&#39;s](https://nl.wikipedia.org/wiki/XML_schema) voor basiseigenschappen die nuttig zijn voor het opnemen van de geschiedenis van een resource tijdens het doorlopen van meerdere verwerkingsstappen, van het fotograferen, [scannen](https://en.wikipedia.org/wiki/Image_scanner) of ontwerpen als tekst, het doorlopen van fotobewerkingsstappen (zoals [bijsnijden](https://en.wikipedia.org/wiki/Cropping_%28image%29) of kleuraanpassing) tot het samenvoegen in een uiteindelijke afbeelding. Met XMP kan elk softwareprogramma of apparaat in de loop van de tijd zijn eigen informatie toevoegen aan een digitale resource, die vervolgens in het uiteindelijke digitale bestand kan worden bewaard.

XMP wordt doorgaans geserialiseerd en opgeslagen met behulp van een subset van het [W3C](https://nl.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://nl.wikipedia.org/wiki/Resource_Description_Framework) (RDF), dat op zijn beurt wordt uitgedrukt in [XML](https://nl.wikipedia.org/wiki/XML).

## Voordelen van XMP {#advantages-of-xmp}

XMP heeft de volgende voordelen ten opzichte van andere coderingsnormen en -schema&#39;s:

* Op XMP gebaseerde metagegevens zijn zeer krachtig en fijnkorrelig.
* Met XMP kunt u meerdere waarden voor één eigenschap hebben.
* XMP heeft gestandaardiseerde codering, waarmee u metagegevens eenvoudig kunt uitwisselen.
* XMP is uitbreidbaar. U kunt aanvullende informatie aan uw elementen toevoegen.

### Uitbreidbaar {#extensible}

De XMP standaard is zo ontworpen dat deze uitbreidbaar is, zodat u aangepaste typen metagegevens kunt toevoegen aan de XMP. EXIF heeft daarentegen geen vaste lijst met eigenschappen die niet kunnen worden uitgebreid.

>[!NOTE]
>
>XMP staat over het algemeen niet binaire gegevenstypes toe om worden ingebed. Als u binaire gegevens wilt meenemen in XMP, bijvoorbeeld miniatuurafbeeldingen, moeten deze worden gecodeerd in een XML-vriendelijke indeling, zoals `Base64`.

## XMP kernconcepten {#xmp-core-concepts}

De volgende secties beschrijven de kernconcepten van XMP, met inbegrip van namespaces en schema&#39;s, eigenschappen en waarden, en taalalternatieven.

### Naamruimten en Schemata {#namespaces-and-schemata}

Een XMP schema is een reeks eigenschapnamen in een gemeenschappelijke XML-naamruimte die het gegevenstype en beschrijvende informatie bevat. Een XMP schema wordt geïdentificeerd door zijn XML namespace URI. Het gebruik van naamruimten voorkomt conflicten tussen eigenschappen in verschillende schema&#39;s die dezelfde naam maar een andere betekenis hebben.

De `Creator` eigenschap in twee onafhankelijk ontworpen schema&#39;s kan bijvoorbeeld de persoon zijn die het element heeft gemaakt of de toepassing die het element heeft gemaakt (bijvoorbeeld Adobe Photoshop).

### Eigenschappen en waarden {#properties-and-values}

XMP kunnen eigenschappen van een of meer schema&#39;s omvatten. Een standaardsubset die door veel Adobe-toepassingen wordt gebruikt, kan bijvoorbeeld het volgende zijn:

* Dublin-kernschema: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`.
* Basisschema XMP: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`.
* Schema voor XMP rechtenbeheer: `xmpRights:WebStatement`, `xmpRights:Marked`.
* Schema voor mediabeheer XMP: `xmpMM:DocumentID`.

### Taalalternatieven {#language-alternatives}

XMP kunt u een `xml:lang` eigenschap aan teksteigenschappen toevoegen om de taal van de tekst op te geven.
