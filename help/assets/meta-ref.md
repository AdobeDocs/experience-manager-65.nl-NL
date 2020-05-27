---
title: Referentie metagegevensschema
description: 'Leer meer over standaardconventies voor het beschrijven van metagegevens van elementen, zoals Dublin Core, IPTC en ander metagegevensschema. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 2%

---


# Referentie metagegevensschema {#metadata-schemata-reference}

De volgende naslaggids bevat informatie over een bepaald metagegevensschema (in alfabetische volgorde) en een lijst met eigenschappen en de bijbehorende definities.

## Dublin Core {#dublin-core}

De meta-gegevens van de Kern van Dublin verstrekt een gestandaardiseerde reeks overeenkomsten voor het beschrijven van activa om hen gemakkelijker te maken te vinden. In Middelen, beschrijft de Kern van Dublin digitale activa met inbegrip van video, geluid, beelden, en documenten.

De eenvoudige Dublin Core Metadata Element Set (DCMES) bevat 15 metagegevenselementen die in de volgende tabel worden vermeld. Elk Dublin Core-element is optioneel en kan worden herhaald. U kunt Dublin Core-metagegevens toevoegen of verwijderen op dezelfde manier als voor mediatype-specifieke metagegevens.

Naast het DCMES zijn er andere metagegevenselementen die door het Dublin Core-initiatief zijn gecreëerd. Zie het [Dublin Core-initiatief](https://dublincore.org/) voor meer informatie.

| Eigenschap | Beschrijving |
| ----------- | ------------------------------------------------------------------------------------------------------------------------ |
| contribuant | De persoon die of het bedrijf dat verantwoordelijk is voor het leveren van bijdragen aan de inhoud. |
| dekking | De geografische locatie of tijdsperiode waarop het actief betrekking heeft. |
| schepper | De persoon of het bedrijf die verantwoordelijk is voor het maken van de inhoud. |
| date | Datum of periode die aan het element is gekoppeld. |
| beschrijving | Meer informatie over het element. |
| format | De bestandsindeling, het fysieke medium of de afmetingen van het element. Experience Manager gebruikt `dc:format` om het MIME-type van het element aan te geven. |
| id | Een unieke verwijzing naar het element. |
| language | De taal van het element (bijvoorbeeld en voor Engels). |
| uitgever | De persoon of het bedrijf die verantwoordelijk is voor het ter beschikking stellen van het actief. |
| relation | Een gerelateerd actief. |
| rechten | Informatie over wie de rechten op dit actief heeft. |
| source | Een gerelateerd actief waarvan het actief is afgeleid. |
| onderwerp | Het onderwerp van de activa. |
| title | Een naam voor het element. |
| type | De aard of het genre van het actief. |

## IPTC {#iptc}

De International Press Telecommunications Council (IPTC) is een consortium van nieuwsagentschappen over de hele wereld - een van de doelstellingen is het ontwikkelen en handhaven van technische normen. In de IPTC is een reeks standaarden voor fotometagegevens gedefinieerd voor afbeeldingen die vrijwel overal door fotografen worden geaccepteerd. Deze metagegevensstandaarden maakten deel uit van de bredere standaard die bekend staat als het IPTC Information Interchange Model (IIM) dat in de jaren negentig is gemaakt.

Hoewel de IPTC-headerinformatie meestal is vervangen door XMP, zijn een IPTC-kernschema en een extensieschema beschikbaar voor XMP. In afbeeldingsprogramma&#39;s worden zowel de XMP- als de IPTC-eigenschappen gesynchroniseerd.
