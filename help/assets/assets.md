---
title: Informatie over Adobe Experience Manager-elementen
description: Meer informatie over het beheer van digitale middelen, de gebruiksgevallen ervan en de Experience Manager Asset-aanbieding van Adobe
contentOwner: AG
translation-type: tm+mt
source-git-commit: a61e1e9ffb132b59c725b2078f09641a3c2a479a
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# Elementen beheren {#administering-assets}

Assets is een Digital Asset Management (DAM)-tool die volledig is geïntegreerd met het Experience Manager-platform en waarmee uw onderneming digitale middelen kan delen en distribueren. Gebruikers in een organisatie kunnen afbeeldingen, video&#39;s, documenten, audioclips en rich media, zoals Flash-bestanden, beheren, opslaan en openen voor gebruik op het web, in gedrukte vorm en voor digitale distributie.

## Wat is Digital Asset Management? {#what-is-digital-asset-management}

Middelen bieden bedrijfsbreed delen en distribueren van de belangrijkste digitale middelen van een organisatie. Gebruikers in een organisatie kunnen digitale elementen zoals afbeeldingen, afbeeldingen, audio, video en documenten via een webinterface (of een CIFS- of WebDAV-map) opslaan, beheren en benaderen.

Goed geïntegreerd in Experience Manager, laat het middelenvermogen u het volgende doen:

* U kunt afbeeldingen, documenten, audiobestanden en videobestanden in verschillende bestandsindelingen toevoegen en delen.
* Elementen beheren door deze te groeperen op tags, lichtbakken of sterren (uw favorieten). Annotaties toevoegen aan elementen.
* U kunt elementen zoeken door te zoeken in bestandsnamen, de volledige tekst van documenten en door datums, documenttype en codes te zoeken.
* Voeg metagegevens voor elementen toe of bewerk deze. Metagegevens worden automatisch bijgewerkt met het bijbehorende element. U kunt metagegevens van elementen importeren of exporteren.
* Voer functies voor het bewerken van afbeeldingen uit, zoals schalen en afbeeldingsfilters toevoegen. U kunt meerdere digitale elementen tegelijk importeren en exporteren met een WebDAV- of CIFS-map.
* Gebruik workflows en meldingen om gezamenlijke verwerking en downloads van een set elementen mogelijk te maken en toegangsrechten voor elementen te beheren.

### Experience Manager Assets is geïntegreerd met Experience Manager Sites {#aem-assets-fully-integrated-in-cq-wcm}

Elementen zijn volledig geïntegreerd met sites en alle functies zijn naadloos beschikbaar. De digitale elementen die worden beheerd in de gegevensopslagruimte van Middelen, zijn dan toegankelijk via de zoekfunctie voor inhoud wanneer u webpagina&#39;s ontwerpt.

De basisgebruikersinterface is het zelfde als dat van Plaatsen. Zie [Overzicht van de sites](/help/sites-authoring/page-authoring.md) voor meer informatie.

### Digitaal middelenbeheer versus imageonderdeel {#digital-asset-management-versus-image-component}

Houd rekening met de levenscyclus van de afbeelding wanneer u bepaalt of een afbeelding in de DAM-opslagplaats moet worden geplaatst of een afbeeldingscomponent moet worden gebruikt:

* Als de afbeelding dezelfde levenscyclus heeft als de pagina, gebruikt u de component Afbeelding.
* Als de afbeelding een aparte levenscyclus heeft, bijvoorbeeld als u de afbeelding tweemaal of buiten WCM gebruikt, gebruikt u Elementen.

## Wat zijn digitale middelen? {#what-are-digital-assets}

Middelen zijn digitale documenten, afbeeldingen, video of audio (of een deel daarvan) die meerdere uitvoeringen kunnen hebben en subelementen kunnen bevatten (bijvoorbeeld lagen in een Photoshop-bestand, dia&#39;s in een PowerPoint-bestand, pagina&#39;s in een PDF, bestanden in een ZIP).

Een element is in wezen een binair plus metagegevens plus uitvoeringen plus subelementen. Raadpleeg de [DAM Performance Guide](/help/sites-deploying/assets-performance-sizing.md) voor meer informatie.

>[!CAUTION]
>
>Het uploaden en/of bewerken van een groot volume aan elementen (in het bijzonder afbeeldingen) kan de prestaties van uw Experience Manager-instantie beïnvloeden.

### Experience Manager Assets terminologie {#aem-assets-terminology}

Wanneer u werkt met digitale middelen in Experience Manager, hebt u de volgende terminologie nodig:

* **Verzameling** Een verzameling elementen op basis van de fysieke locatie (map), de algemene eigenschappen (opgeslagen zoekmap) of de gebruikersselectie (lichtbakmappen).

* **Metagegevenselementen** hebben metagegevens; bijvoorbeeld auteur, vervaldatum, DRM-gegevens (Digital Rights Management) enzovoort. Metagegevens zijn toegankelijk. Elementen ondersteunen de volgende algemene metagegevensschema&#39;s uit het vak:

   * Dublin Core: inclusief auteur, beschrijving, datum, onderwerp, enzovoort.
   * IPTC: inclusief gebeurtenis, model, locatie, enzovoort.
   * WCM: inclusief pagina-eigenschappen, [!UICONTROL On Time] [!UICONTROL Off Time]enzovoort.

* **Tagingelementen** kunnen worden gelabeld en geclassificeerd. Zie Tags gebruiken en Tags beheren.

* **Uitvoeringen** Een uitvoering is de binaire representatie van een element. Elementen hebben altijd een primaire representatie, namelijk die van het geüploade bestand. Ze kunnen een willekeurig aantal aanvullende voorstellingen hebben die worden gemaakt, bijvoorbeeld door aangepaste workflowstappen of wanneer een element wordt geüpload. Uitvoeringen kunnen een andere grootte hebben, met een andere resolutie, met een toegevoegd watermerk of een ander gewijzigd kenmerk.

* **Met Versieversie** maakt u een momentopname van digitale elementen op een bepaald tijdstip. U kunt middelen aan vorige versies herstellen. Zie [versioning in Elementen](managing-assets-touch-ui.md#asset-versioning).

* **Submiddelen** zijn elementen die een element vormen, zoals lagen in een Adobe Photoshop-bestand of pagina&#39;s in een PDF-bestand. In Elementen kunt u subelementen op dezelfde manier beheren als elementen.

### Werken met middelen {#how-to-work-with-assets}

U voert een actie op een middel of een inzameling uit. Met handelingen kunt u elementen, verzamelingen en uitvoeringen maken of wijzigen. Veel van de basishandelingen die u uitvoert op elementen - uploaden, verwijderen, bijwerken, opslaan van subelementen - activeren vooraf geconfigureerde workflows. Deze worden automatisch ingeschakeld in Elementen en worden in detail beschreven in Media Handlers van Elementen.

De taken u met deze vooraf gevormde werkschema&#39;s kunt uitvoeren:

* Sla het middel op in de opslagplaats of verwijder het middel uit de opslagplaats.
* metagegevens voor het element uitpakken en opslaan; de afzonderlijke metagegevensitems worden opgeslagen als XMP.
* rendities en miniaturen voor het element genereren; inclusief, waar nodig, automatisch vergroten/verkleinen en uitsnijden.
* het element zo nodig transcoderen. Zo wordt video voor mobiel gebruik en webgebruik getranscodeerd met 24 frames per seconde. Download video met 30 frames per seconde. Audio voor mobiel en webgebruik wordt getranscodeerd met 128 kbps, audio voor downloaden met 192 kbps.

Natuurlijk kunt u werkstromen ook handmatig toepassen. Zie [Assets Media](/help/assets/media-handlers.md)Handlersvoor een lijst met standaardworkflows.

## Experience Manager Assets en MediaLibrary {#cq-dam-vs-cq-medialibrary}

Zie [Middelen en MediaLibrary](/help/assets/medialibrary.md) voor informatie over de verschillen.
