---
title: Inleiding tot  [!DNL Adobe Experience Manager Assets]
description: Maak, beheer, verwerk en distribueer digitale assets in Experience Manager. In deze handleidingen worden aanbevolen methoden, toegankelijkheidsfuncties en het gebruik van AEM 6.5-elementen beschreven.
hide: true
feature: Asset Management
role: Leader, Architect, User
exl-id: 68239634-a2e8-414e-a866-cd8082641ee8
solution: Experience Manager, Experience Manager Assets
source-git-commit: 347828d5bf3da01685f19fb43609505b24126c63
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager Assets] als DAM-oplossing {#administering-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/overview) |
| AEM 6.5 | Dit artikel |

AEM [!DNL Assets] is een Digital Asset Management (DAM)-hulpprogramma dat deel uitmaakt van het [!DNL Experience Manager] -platform en waarmee uw onderneming digitale middelen kan beheren en distribueren. Gebruikers in een organisatie kunnen vele typen digitale elementen beheren, opslaan en openen, zoals afbeeldingen, video&#39;s, documenten, audioclips, 3D-bestanden en rijke media voor gebruik op het web, in gedrukte vorm en voor digitale distributie.

## Wat is Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] biedt delen en distribueren op bedrijfsniveau van de belangrijkste digitale middelen van een organisatie. Gebruikers in een organisatie kunnen digitale elementen zoals afbeeldingen, afbeeldingen, audio, video en documenten via een webinterface (of een CIFS- of WebDAV-map) opslaan, beheren en benaderen.

Met de functie [!DNL Assets] van [!DNL Experience Manager] kunt u het volgende doen:

* Voeg en deel beelden, documenten, audiodossiers, en videodossiers in diverse dossierformaten toe.
* Elementen beheren door deze te groeperen op tags, lichtbakken of sterren (uw favorieten). Annotaties toevoegen aan elementen.
* U kunt elementen zoeken door te zoeken in bestandsnamen, de volledige tekst van documenten en door datums, documenttype en codes te zoeken.
* Voeg metagegevens voor elementen toe of bewerk deze. Metagegevens worden automatisch bijgewerkt met het bijbehorende element. U kunt metagegevens van elementen importeren of exporteren.
* Voer beeldbewerkingsfuncties uit, zoals schalen en afbeeldingsfilters toevoegen. U kunt meerdere digitale elementen tegelijk importeren en exporteren met een WebDAV- of CIFS-map.
* Gebruik workflows en meldingen om gezamenlijke verwerking en downloads van een set elementen mogelijk te maken en toegangsrechten voor elementen te beheren.

### [!DNL Experience Manager Assets] is geïntegreerd met [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] is volledig geïntegreerd met [!DNL Sites] en werkt naadloos voor alle gevallen waarin het wordt gebruikt. Wanneer u bijvoorbeeld webpagina&#39;s ontwerpt, kunnen de auteurs van [!DNL Sites] de digitale elementen zoeken en gebruiken via de Inhoudszoeker. De gebruikersinterface van [!DNL Assets] is hetzelfde als die van [!DNL Sites] . Zie een [ overzicht van Plaatsen ](/help/sites-authoring/page-authoring.md) voor volledige details.

De basisgebruikersinterface is dezelfde als die van [!DNL Sites] . Zie [ Overzicht van de Plaatsen ](/help/sites-authoring/page-authoring.md) voor volledige details.

### Digitaal middelenbeheer versus imageonderdeel {#digital-asset-management-versus-image-component}

Houd rekening met de levenscyclus van de afbeelding wanneer u bepaalt of een afbeelding in de DAM-opslagplaats moet worden geplaatst of een afbeeldingscomponent moet worden gebruikt:

* Als de afbeelding dezelfde levenscyclus heeft als de pagina, gebruikt u de component Image.
* Als de afbeelding een aparte levenscyclus heeft, bijvoorbeeld als u de afbeelding tweemaal of buiten WCM gebruikt, gebruikt u [!DNL Assets] .

## Wat zijn digitale middelen? {#what-are-digital-assets}

Middelen zijn digitale documenten, afbeeldingen, video of audio (of een deel daarvan) die meerdere uitvoeringen kunnen hebben. Het kan ook subelementen hebben, bijvoorbeeld lagen in een Photoshop-bestand, dia&#39;s in een PowerPoint-bestand, pagina&#39;s in een PDF, bestanden in een ZIP.

Een element is in wezen een binair plus metagegevens plus uitvoeringen plus subelementen. Zie de [ Gids van Prestaties DAM ](/help/sites-deploying/assets-performance-sizing.md) voor gedetailleerde informatie.

>[!CAUTION]
>
>Het uploaden en/of bewerken van een groot volume aan elementen (in het bijzonder afbeeldingen) kan van invloed zijn op de prestaties van de implementatie van [!DNL Experience Manager] .

### [!DNL Experience Manager Assets] terminologie {#aem-assets-terminology}

Wanneer u met digitale elementen werkt in [!DNL Experience Manager] , is het handig als u de volgende terminologie begrijpt:

* **Inzameling**: Een inzameling van activa, of gebaseerd op fysieke plaats (omslag), gemeenschappelijke eigenschappen (bewaarde onderzoeksomslag), of gebruikersselectie (lichtbakomslagen).

* **Meta-gegevens** [!DNL Assets] hebben meta-gegevens; bijvoorbeeld, auteur, vervaldatum, en Informatie DRM (Digital Rights Management). Metagegevens zijn toegankelijk. [!DNL Assets] biedt ondersteuning voor de volgende algemene metagegevensschema&#39;s in het vak:

   * Dublin Core: inclusief auteur, beschrijving, datum, onderwerp, enzovoort.
   * IPTC: inclusief gebeurtenis, model, locatie, enzovoort.
   * WCM: inclusief pagina-eigenschappen [!UICONTROL On Time] en [!UICONTROL Off Time] , enzovoort.

* **het Tags**: [!DNL Assets] kan worden geëtiketteerd en worden geclassificeerd. Zie [ het organiseren van activa ](/help/assets/organize-assets.md).

* **Vertoningen**: Een vertoning is de binaire vertegenwoordiging van een activa. [!DNL Assets] heeft altijd een primaire representatie, die van het geüploade bestand. Ze kunnen een aantal aanvullende voorstellingen hebben die bijvoorbeeld worden gemaakt door aangepaste workflowstappen of wanneer een element wordt geüpload. Uitvoeringen kunnen een andere grootte hebben, met een andere resolutie, met een toegevoegd watermerk of een ander gewijzigd kenmerk.

* **Versies**: Het versioning leidt tot een momentopname van digitale activa op een specifiek punt in tijd. U kunt middelen aan vorige versies herstellen. Zie [ versioning in  [!DNL Assets]](manage-assets.md#asset-versioning).

* **Subactiva**: De sub-activa zijn activa die omhoog activa, bijvoorbeeld, lagen in een [!DNL Adobe Photoshop] dossier of pagina&#39;s in een dossier van PDF maken. In [!DNL Assets] kunt u subelementen op dezelfde manier beheren als elementen.

### Werken met digitale middelen {#how-to-work-with-assets}

U voert een actie op een middel of een inzameling uit. Met handelingen kunt u elementen, verzamelingen en uitvoeringen maken of wijzigen. Veel van de basishandelingen die u uitvoert op elementen - uploaden, verwijderen, bijwerken, opslaan van subelementen - activeren vooraf geconfigureerde workflows. Deze worden automatisch ingeschakeld in [!DNL Assets] en worden in detail beschreven in [!DNL Assets] -mediamandlers.

De taken u met deze pre-gevormde werkschema&#39;s kunt uitvoeren:

* Sla het middel op in de opslagplaats of verwijder het middel uit de opslagplaats.
* Metagegevens voor het element extraheren en opslaan; de afzonderlijke metagegevensitems worden opgeslagen als XMP.
* Rendities en miniaturen genereren voor het element, inclusief indien nodig automatisch vergroten/verkleinen en bijsnijden.
* Transcodeer het element waar nodig. Zo wordt video voor mobiel gebruik en webgebruik getranscodeerd met 24 frames per seconde. Download video met 30 frames per seconde. Audio voor mobiel en webgebruik wordt getranscodeerd met 128 Kbps, audio voor downloaden met 192 Kbps.

U kunt workflows ook handmatig toepassen. Zie [ de Handlers van de Media van Assets ](media-handlers.md) voor een lijst van standaardwerkschema&#39;s.

## [!DNL Experience Manager Assets] en [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Zie [ Assets en de Bibliotheek van Media ](medialibrary.md) voor informatie over de verschillen.

>[!MORELIKETHIS]
>
>* [ Inleiding van de Video - Experience Manager Assets als moderne DAM ](https://www.youtube.com/watch?v=PBwQqZgC-yo)
>* [ begrijp meta-gegevensconcepten ](/help/assets/metadata-concepts.md)
