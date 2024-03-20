---
title: Inleiding tot [!DNL Adobe Experience Manager Assets]
description: Maak, beheer, verwerk en distribueer digitale assets in Exerience Manager. In deze handleidingen worden aanbevolen methoden, toegankelijkheidsfuncties en het gebruik van AEM 6.5-elementen beschreven.
contentOwner: AG
feature: Asset Management
role: Leader, Architect, User
exl-id: 68239634-a2e8-414e-a866-cd8082641ee8
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 2%

---

# Info [!DNL Adobe Experience Manager Assets] als DAM-oplossing {#administering-assets}

AEM [!DNL Assets] is een DAM-hulpmiddel (Digital Asset Management) dat deel uitmaakt van het [!DNL Experience Manager] en stelt uw onderneming in staat om digitale middelen te beheren en te distribueren. Gebruikers in een organisatie kunnen vele typen digitale elementen beheren, opslaan en openen, zoals afbeeldingen, video&#39;s, documenten, audioclips, 3D-bestanden en rijke media voor gebruik op het web, in gedrukte vorm en voor digitale distributie.

## Wat is Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] biedt bedrijfsbrede uitwisseling en distributie van de belangrijkste digitale middelen van een organisatie. Gebruikers in een organisatie kunnen digitale elementen zoals afbeeldingen, afbeeldingen, audio, video en documenten via een webinterface (of een CIF- of WebDAV-map) opslaan, beheren en benaderen.

[!DNL Assets] vermogen van [!DNL Experience Manager] Hiermee kunt u het volgende doen:

* Voeg en deel beelden, documenten, audiodossiers, en videodossiers in diverse dossierformaten toe.
* Elementen beheren door deze te groeperen op tags, lichtbakken of sterren (uw favorieten). Annotaties toevoegen aan elementen.
* U kunt elementen zoeken door te zoeken in bestandsnamen, de volledige tekst van documenten en door datums, documenttype en codes te zoeken.
* Voeg metagegevens voor elementen toe of bewerk deze. Metagegevens worden automatisch bijgewerkt met het bijbehorende element. U kunt metagegevens van elementen importeren of exporteren.
* Voer beeldbewerkingsfuncties uit, zoals schalen en afbeeldingsfilters toevoegen. U kunt meerdere digitale elementen tegelijk importeren en exporteren met een WebDAV- of CIF-map.
* Gebruik workflows en meldingen om gezamenlijke verwerking en downloads van een set elementen mogelijk te maken en toegangsrechten voor elementen te beheren.

### [!DNL Experience Manager Assets] is geïntegreerd met [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] volledig geïntegreerd met [!DNL Sites] en werkt naadloos voor alle gebruiksgevallen. Wanneer u bijvoorbeeld webpagina&#39;s ontwerpt, worden de [!DNL Sites] auteurs kunnen de digitale middelen vinden en gebruiken via de Inhoudszoeker. De gebruikersinterface van [!DNL Assets] is gelijk aan die van [!DNL Sites]. Zie een [overzicht van sites](/help/sites-authoring/page-authoring.md) voor volledige informatie.

De basisgebruikersinterface is gelijk aan die van [!DNL Sites]. Zie [Overzicht van de sites](/help/sites-authoring/page-authoring.md) voor volledige informatie.

### Digitaal middelenbeheer versus imageonderdeel {#digital-asset-management-versus-image-component}

Houd rekening met de levenscyclus van de afbeelding wanneer u bepaalt of een afbeelding in de DAM-opslagplaats moet worden geplaatst of een afbeeldingscomponent moet worden gebruikt:

* Als de afbeelding dezelfde levenscyclus heeft als de pagina, gebruikt u de component Image.
* Als de afbeelding een aparte levenscyclus heeft, bijvoorbeeld als u de afbeelding tweemaal of buiten WCM gebruikt, gebruikt u [!DNL Assets].

## Wat zijn digitale middelen? {#what-are-digital-assets}

Middelen zijn digitale documenten, afbeeldingen, video of audio (of een deel daarvan) die meerdere uitvoeringen kunnen hebben. Het kan ook subelementen hebben, bijvoorbeeld lagen in een Photoshop-bestand, dia&#39;s in een PowerPoint-bestand, pagina&#39;s in een PDF, bestanden in een ZIP.

Een element is in wezen een binair plus metagegevens plus uitvoeringen plus subelementen. Zie de [DAM Performance Guide](/help/sites-deploying/assets-performance-sizing.md) voor nadere informatie.

>[!CAUTION]
>
>Het uploaden en/of bewerken van een groot volume aan elementen (in het bijzonder afbeeldingen) kan van invloed zijn op de prestaties van uw [!DNL Experience Manager] implementatie.

### [!DNL Experience Manager Assets] terminologie {#aem-assets-terminology}

Wanneer u werkt met digitale middelen in [!DNL Experience Manager]Het is handig als u de volgende terminologie begrijpt:

* **Verzameling**: Een verzameling elementen op basis van de fysieke locatie (map), algemene eigenschappen (opgeslagen zoekmap) of de selectie van de gebruiker (lichtbakmappen).

* **Metagegevens** [!DNL Assets] beschikken over metagegevens, zoals auteur, vervaldatum en DRM-gegevens (Digital Rights Management). Metagegevens zijn toegankelijk. [!DNL Assets] ondersteunt de volgende verschillende algemene metagegevensschema&#39;s uit het vak:

   * Dublin Core: inclusief auteur, beschrijving, datum, onderwerp, enzovoort.
   * IPTC: inclusief gebeurtenis, model, locatie, enzovoort.
   * WCM: pagina-eigenschappen opnemen, [!UICONTROL On Time] en [!UICONTROL Off Time], enzovoort.

* **Tags**: [!DNL Assets] kunnen worden gelabeld en geclassificeerd. Zie [elementen ordenen](/help/assets/organize-assets.md).

* **Uitvoeringen**: Een vertoning is de binaire representatie van een element. [!DNL Assets] altijd een primaire representatie hebben, namelijk die van het geüploade bestand. Ze kunnen een aantal aanvullende voorstellingen hebben die bijvoorbeeld worden gemaakt door aangepaste workflowstappen of wanneer een element wordt geüpload. Uitvoeringen kunnen een andere grootte hebben, met een andere resolutie, met een toegevoegd watermerk of een ander gewijzigd kenmerk.

* **Versies**: Met Versioning maakt u een momentopname van digitale elementen op een bepaald tijdstip. U kunt middelen aan vorige versies herstellen. Zie [versioning in [!DNL Assets]](manage-assets.md#asset-versioning).

* **Subactiva**: Subelementen zijn elementen die een element vormen, bijvoorbeeld lagen in een [!DNL Adobe Photoshop] bestand of pagina&#39;s in een PDF-bestand. In [!DNL Assets]U kunt subelementen beheren op dezelfde manier als elementen.

### Werken met digitale middelen {#how-to-work-with-assets}

U voert een actie op een middel of een inzameling uit. Met handelingen kunt u elementen, verzamelingen en uitvoeringen maken of wijzigen. Veel van de basishandelingen die u uitvoert op elementen - uploaden, verwijderen, bijwerken, opslaan van subelementen - activeren vooraf geconfigureerde workflows. Deze worden automatisch ingeschakeld [!DNL Assets] en worden in detail beschreven [!DNL Assets] mediahandlers.

De taken u met deze pre-gevormde werkschema&#39;s kunt uitvoeren:

* Sla het middel op in de opslagplaats of verwijder het middel uit de opslagplaats.
* Metagegevens voor het element extraheren en opslaan; de afzonderlijke metagegevensitems worden opgeslagen als XMP.
* Rendities en miniaturen genereren voor het element, inclusief indien nodig automatisch vergroten/verkleinen en bijsnijden.
* Transcodeer het element waar nodig. Zo wordt video voor mobiel gebruik en webgebruik getranscodeerd met 24 frames per seconde. Download video met 30 frames per seconde. Audio voor mobiel en webgebruik wordt getranscodeerd met 128 Kbps, audio voor downloaden met 192 Kbps.

U kunt workflows ook handmatig toepassen. Zie [Media Handlers voor middelen](media-handlers.md)voor een lijst met standaardworkflows.

## [!DNL Experience Manager Assets] en [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Zie [Middelen en Media Library](medialibrary.md) voor informatie over de verschillen.

>[!MORELIKETHIS]
>
>* [Introductie van video - Experience Manager Assets als moderne DAM](https://www.youtube.com/watch?v=PBwQqZgC-yo)
>* [Metagegevensconcepten begrijpen](/help/assets/metadata-concepts.md)
