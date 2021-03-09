---
title: Inleiding tot [!DNL Adobe Experience Manager Assets]
description: Leer wat het beheer van digitale middelen, zijn gebruiksgevallen, en [!DNL Adobe Experience Manager Asset] aanbieding is.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b851bfb2758db60e960afd4720d04202934c18bc
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---


# Informatie over [!DNL Adobe Experience Manager Assets] als DAM-oplossing {#administering-assets}

[!DNL Assets] is een DAM-hulpmiddel (Digital Asset Management) dat een integraal onderdeel is van het  [!DNL Experience Manager] platform en waarmee uw onderneming digitale middelen kan beheren en distribueren. Gebruikers in een organisatie kunnen vele typen digitale elementen beheren, opslaan en openen, zoals afbeeldingen, video&#39;s, documenten, audioclips, 3D-bestanden en rijke media voor gebruik op het web, in gedrukte vorm en voor digitale distributie.

## Wat is Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] zorgt voor bedrijfsbreed delen en distributie van de belangrijkste digitale middelen van een organisatie. Gebruikers in een organisatie kunnen digitale elementen zoals afbeeldingen, afbeeldingen, audio, video en documenten via een webinterface (of een CIFS- of WebDAV-map) opslaan, beheren en benaderen.

[!DNL Assets] mogelijkheden van  [!DNL Experience Manager] laten u het volgende doen:

* U kunt afbeeldingen, documenten, audiobestanden en videobestanden in verschillende bestandsindelingen toevoegen en delen.
* Elementen beheren door deze te groeperen op tags, lichtbakken of sterren (uw favorieten). Annotaties toevoegen aan elementen.
* U kunt elementen zoeken door te zoeken in bestandsnamen, de volledige tekst van documenten en door datums, documenttype en codes te zoeken.
* Voeg metagegevens voor elementen toe of bewerk deze. Metagegevens worden automatisch bijgewerkt met het bijbehorende element. U kunt metagegevens van elementen importeren of exporteren.
* Voer functies voor het bewerken van afbeeldingen uit, zoals schalen en afbeeldingsfilters toevoegen. U kunt meerdere digitale elementen tegelijk importeren en exporteren met een WebDAV- of CIFS-map.
* Gebruik workflows en meldingen om gezamenlijke verwerking en downloads van een set elementen mogelijk te maken en toegangsrechten voor elementen te beheren.

### [!DNL Experience Manager Assets] is geïntegreerd met  [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] volledig geïntegreerd met  [!DNL Sites] en werkt naadloos voor alle gebruiksgevallen. Wanneer u bijvoorbeeld webpagina&#39;s ontwerpt, kunnen de [!DNL Sites] auteurs de digitale elementen zoeken en gebruiken via de Inhoudszoeker. De gebruikersinterface van [!DNL Assets] is het zelfde als dat van [!DNL Sites]. Zie [overzicht van sites](/help/sites-authoring/page-authoring.md) voor volledige details.

De basisgebruikersinterface is het zelfde als dat van [!DNL Sites]. Zie [Overzicht van de Sites](/help/sites-authoring/page-authoring.md) voor volledige details.

### Digital Asset Management versus imageonderdeel {#digital-asset-management-versus-image-component}

Houd rekening met de levenscyclus van de afbeelding wanneer u bepaalt of een afbeelding in de DAM-opslagplaats moet worden geplaatst of een afbeeldingscomponent moet worden gebruikt:

* Als de afbeelding dezelfde levenscyclus heeft als de pagina, gebruikt u de component Image.
* Als de afbeelding een aparte levenscyclus heeft, bijvoorbeeld als u de afbeelding tweemaal of buiten WCM gebruikt, gebruikt u [!DNL Assets].

## Wat zijn digitale middelen? {#what-are-digital-assets}

Middelen zijn digitale documenten, afbeeldingen, video of audio (of een deel daarvan) die meerdere uitvoeringen kunnen hebben en subelementen kunnen bevatten (bijvoorbeeld lagen in een Photoshop-bestand, dia&#39;s in een PowerPoint-bestand, pagina&#39;s in een PDF, bestanden in een ZIP).

Een element is in wezen een binair plus metagegevens plus uitvoeringen plus subelementen. Zie de [DAM Performance Guide](/help/sites-deploying/assets-performance-sizing.md) voor gedetailleerde informatie.

>[!CAUTION]
>
>Het uploaden en/of bewerken van een groot volume aan middelen (in het bijzonder afbeeldingen) kan de prestaties van uw [!DNL Experience Manager]-implementatie beïnvloeden.

### [!DNL Experience Manager Assets] terminologie  {#aem-assets-terminology}

Wanneer u werkt met digitale elementen in [!DNL Experience Manager], hebt u de volgende terminologie nodig:

* **Verzameling**: Een verzameling elementen op basis van de fysieke locatie (map), algemene eigenschappen (opgeslagen zoekmap) of gebruikersselectie (lichtbakmappen).

* **metagegevens** [!DNL Assets] hebben; bijvoorbeeld auteur, vervaldatum, DRM-informatie (Digital Rights Management) enzovoort. Metagegevens zijn toegankelijk. [!DNL Assets] ondersteunt de volgende verschillende algemene metagegevensschema&#39;s uit het vak:

   * Dublin Core: inclusief auteur, beschrijving, datum, onderwerp, enzovoort.
   * IPTC: inclusief gebeurtenis, model, locatie, enzovoort.
   * WCM: inclusief pagina-eigenschappen, [!UICONTROL On Time] en [!UICONTROL Off Time] enzovoort.

* **Tags**:  [!DNL Assets] kunnen worden gelabeld en geclassificeerd. Zie [elementen ordenen](/help/assets/organize-assets.md).

* **Uitvoeringen**: Een vertoning is de binaire representatie van een element. [!DNL Assets] altijd een primaire representatie hebben, namelijk die van het geüploade bestand. Ze kunnen een willekeurig aantal aanvullende voorstellingen hebben die worden gemaakt, bijvoorbeeld door aangepaste workflowstappen of wanneer een element wordt geüpload. Uitvoeringen kunnen een andere grootte hebben, met een andere resolutie, met een toegevoegd watermerk of een ander gewijzigd kenmerk.

* **Versies**: Met Versioning maakt u een momentopname van digitale elementen op een bepaald tijdstip. U kunt middelen aan vorige versies herstellen. Zie [versioning in [!DNL Assets]](manage-assets.md#asset-versioning).

* **Subactiva**: Subelementen zijn elementen die een element vormen, bijvoorbeeld lagen in een  [!DNL Adobe Photoshop] bestand of pagina&#39;s in een PDF-bestand. In [!DNL Assets] kunt u subelementen op dezelfde manier beheren als elementen.

### Werken met digitale elementen {#how-to-work-with-assets}

U voert een actie op een middel of een inzameling uit. Met handelingen kunt u elementen, verzamelingen en uitvoeringen maken of wijzigen. Veel van de basishandelingen die u uitvoert op elementen - uploaden, verwijderen, bijwerken, opslaan van subelementen - activeren vooraf geconfigureerde workflows. Deze worden automatisch ingeschakeld in [!DNL Assets] en worden gedetailleerd beschreven in [!DNL Assets] media managers.

De taken u met deze vooraf gevormde werkschema&#39;s kunt uitvoeren:

* Sla het middel op in de opslagplaats of verwijder het middel uit de opslagplaats.
* Metagegevens voor het element extraheren en opslaan; de afzonderlijke metagegevensitems worden opgeslagen als XMP.
* Uitvoeringen en miniaturen genereren voor het element; inclusief, waar nodig, automatisch vergroten/verkleinen en uitsnijden.
* Transcodeer het element waar nodig. Zo wordt video voor mobiel gebruik en webgebruik getranscodeerd met 24 frames per seconde. Download video met 30 frames per seconde. Audio voor mobiel en webgebruik wordt getranscodeerd met 128 Kbps, audio voor downloaden met 192 Kbps.

Natuurlijk kunt u werkstromen ook handmatig toepassen. Zie [Elementen Media Handlers](media-handlers.md)voor een lijst met standaardworkflows.

## [!DNL Experience Manager Assets] en  [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Zie [Middelen en Mediabibliotheek](medialibrary.md) voor informatie over de verschillen.

>[!MORELIKETHIS]
>
>* [Video-introductie - Experience Manager-elementen als een moderne DAM](https://www.youtube.com/watch?v=PBwQqZgC-yo)
>* [Metagegevensconcepten begrijpen](/help/assets/metadata-concepts.md)

