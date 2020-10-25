---
title: Introduction to [!DNL Adobe Experience Manager Assets].
description: Leer wat het beheer van digitale middelen is, zijn gebruiksgevallen, [!DNL Adobe Experience Manager Asset] en het aanbieden van diensten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: cec6c4f9a1a75eb049dd4b8461c36c8d58d46f79
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 0%

---


# Info [!DNL Adobe Experience Manager Assets] als DAM-oplossing {#administering-assets}

[!DNL Assets] is een DAM-hulpmiddel (Digital Asset Management) dat een integraal onderdeel is van het [!DNL Experience Manager] platform en waarmee uw onderneming digitale middelen kan beheren en distribueren. Gebruikers in een organisatie kunnen vele typen digitale elementen beheren, opslaan en openen, zoals afbeeldingen, video&#39;s, documenten, audioclips, 3D-bestanden en rijke media voor gebruik op het web, in gedrukte vorm en voor digitale distributie.

## Wat is Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] zorgt voor bedrijfsbreed delen en distributie van de belangrijkste digitale middelen van een organisatie. Gebruikers in een organisatie kunnen digitale elementen zoals afbeeldingen, afbeeldingen, audio, video en documenten via een webinterface (of een CIFS- of WebDAV-map) opslaan, beheren en benaderen.

[!DNL Assets] mogelijkheden van [!DNL Experience Manager] laat u het volgende doen:

* U kunt afbeeldingen, documenten, audiobestanden en videobestanden in verschillende bestandsindelingen toevoegen en delen.
* Elementen beheren door deze te groeperen op tags, lichtbakken of sterren (uw favorieten). Annotaties toevoegen aan elementen.
* U kunt elementen zoeken door te zoeken in bestandsnamen, de volledige tekst van documenten en door datums, documenttype en codes te zoeken.
* Voeg metagegevens voor elementen toe of bewerk deze. Metagegevens worden automatisch bijgewerkt met het bijbehorende element. U kunt metagegevens van elementen importeren of exporteren.
* Voer functies voor het bewerken van afbeeldingen uit, zoals schalen en afbeeldingsfilters toevoegen. U kunt meerdere digitale elementen tegelijk importeren en exporteren met een WebDAV- of CIFS-map.
* Gebruik workflows en meldingen om gezamenlijke verwerking en downloads van een set elementen mogelijk te maken en toegangsrechten voor elementen te beheren.

### [!DNL Experience Manager Assets] is geïntegreerd met [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] volledig geïntegreerd met [!DNL Sites] en werkt naadloos voor alle gebruiksgevallen. Wanneer [!DNL Sites] ontwerpers bijvoorbeeld webpagina&#39;s maken, kunnen ze de digitale elementen zoeken en gebruiken via de Inhoudszoeker. De gebruikersinterface van [!DNL Assets] is het zelfde als dat van [!DNL Sites]. Zie [Overzicht van Sites](/help/sites-authoring/page-authoring.md) voor meer informatie.

De basisgebruikersinterface is hetzelfde als die van [!DNL Sites]. Zie [Overzicht van de sites](/help/sites-authoring/page-authoring.md) voor meer informatie.

### Digitaal middelenbeheer versus imageonderdeel {#digital-asset-management-versus-image-component}

Houd rekening met de levenscyclus van de afbeelding wanneer u bepaalt of een afbeelding in de DAM-opslagplaats moet worden geplaatst of een afbeeldingscomponent moet worden gebruikt:

* Als de afbeelding dezelfde levenscyclus heeft als de pagina, gebruikt u de component Afbeelding.
* Als de afbeelding een aparte levenscyclus heeft, bijvoorbeeld als u de afbeelding tweemaal of buiten WCM gebruikt, gebruikt u [!DNL Assets].

## Wat zijn digitale middelen? {#what-are-digital-assets}

Middelen zijn digitale documenten, afbeeldingen, video of audio (of een deel daarvan) die meerdere uitvoeringen kunnen hebben en subelementen kunnen bevatten (bijvoorbeeld lagen in een Photoshop-bestand, dia&#39;s in een PowerPoint-bestand, pagina&#39;s in een PDF, bestanden in een ZIP).

Een element is in wezen een binair plus metagegevens plus uitvoeringen plus subelementen. Raadpleeg de [DAM Performance Guide](/help/sites-deploying/assets-performance-sizing.md) voor meer informatie.

>[!CAUTION]
>
>Het uploaden en/of bewerken van een groot volume aan middelen (in het bijzonder afbeeldingen) kan de prestaties van uw [!DNL Experience Manager] implementatie beïnvloeden.

### [!DNL Experience Manager Assets] terminologie {#aem-assets-terminology}

Wanneer u met digitale middelen werkt in, moet u de volgende terminologie begrijpen: [!DNL Experience Manager]

* **Verzameling**: Een verzameling elementen op basis van de fysieke locatie (map), algemene eigenschappen (opgeslagen zoekmap) of gebruikersselectie (lichtbakmappen).

* **Metagegevens** bevatten metagegevens [!DNL Assets] ; bijvoorbeeld auteur, vervaldatum, DRM-informatie (Digital Rights Management) enzovoort. Metagegevens zijn toegankelijk. [!DNL Assets] ondersteunt de volgende verschillende algemene metagegevensschema&#39;s uit het vak:

   * Dublin Core: inclusief auteur, beschrijving, datum, onderwerp, enzovoort.
   * IPTC: inclusief gebeurtenis, model, locatie, enzovoort.
   * WCM: inclusief pagina-eigenschappen, [!UICONTROL On Time] [!UICONTROL Off Time]enzovoort.

* **Tags**: [!DNL Assets] kunnen worden gelabeld en geclassificeerd. Zie elementen [ordenen](/help/assets/organize-assets.md).

* **Uitvoeringen**: Een vertoning is de binaire representatie van een element. [!DNL Assets] altijd een primaire representatie hebben, namelijk die van het geüploade bestand. Ze kunnen een willekeurig aantal aanvullende voorstellingen hebben die worden gemaakt, bijvoorbeeld door aangepaste workflowstappen of wanneer een element wordt geüpload. Uitvoeringen kunnen een andere grootte hebben, met een andere resolutie, met een toegevoegd watermerk of een ander gewijzigd kenmerk.

* **Versies**: Met Versioning maakt u een momentopname van digitale elementen op een bepaald tijdstip. U kunt middelen aan vorige versies herstellen. Zie [versioning in Elementen](manage-assets.md#asset-versioning).

* **Subactiva**: Subelementen zijn elementen die een element vormen, bijvoorbeeld lagen in een [!DNL Adobe Photoshop] bestand of pagina&#39;s in een PDF-bestand. In [!DNL Assets], kunt u subactiva beheren zoals u activa.

### Werken met middelen {#how-to-work-with-assets}

U voert een actie op een middel of een inzameling uit. Met handelingen kunt u elementen, verzamelingen en uitvoeringen maken of wijzigen. Veel van de basishandelingen die u uitvoert op elementen - uploaden, verwijderen, bijwerken, opslaan van subelementen - activeren vooraf geconfigureerde workflows. Deze worden automatisch ingeschakeld in [!DNL Assets] en worden in detail beschreven in [!DNL Assets] mediahandlers.

De taken u met deze vooraf gevormde werkschema&#39;s kunt uitvoeren:

* Sla het middel op in de opslagplaats of verwijder het middel uit de opslagplaats.
* Metagegevens voor het element extraheren en opslaan; de afzonderlijke metagegevensitems worden opgeslagen als XMP.
* Uitvoeringen en miniaturen genereren voor het element; inclusief, waar nodig, automatisch vergroten/verkleinen en uitsnijden.
* Transcodeer het element waar nodig. Zo wordt video voor mobiel gebruik en webgebruik getranscodeerd met 24 frames per seconde. Download video met 30 frames per seconde. Audio voor mobiel en webgebruik wordt getranscodeerd met 128 Kbps, audio voor downloaden met 192 Kbps.

Natuurlijk kunt u werkstromen ook handmatig toepassen. Zie [Assets Media](/help/assets/media-handlers.md)Handlersvoor een lijst met standaardworkflows.

## [!DNL Experience Manager Assets] en [!DNL MediaLibrary] {#cq-dam-vs-cq-medialibrary}

Zie [Middelen en MediaLibrary](/help/assets/medialibrary.md) voor informatie over de verschillen.
