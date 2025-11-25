---
title: Eigenschappen en knooppunten van inhoud
description: Volg deze pagina voor meer informatie over eigenschappen en knooppunten van inhoud.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 05c8c846-69cc-4075-9149-33890b3d1e08
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---

# Eigenschappen en knooppunten van inhoud {#content-properties-and-nodes}

{{ue-over-mobile}}

Artikelen, banners en verzamelingen worden in AEM als cq :Pages weergegeven.

Zij delen de zelfde gemeenschappelijke eigenschappen die in om het even welke cq :Page naast verscheidene hieronder getoonde anderen worden gevonden die de mobiele de dienstenmeta-gegevens van de On-Demand van Adobe Experience Manager (AEM) en integratie ondersteunende eigenschappen vertegenwoordigen.

In de volgende tabellen worden de eigenschappen en knooppunten van de inhoud beschreven.

## Algemene integratieeigenschappen {#common-integration-properties}

| **de Naam van het Bezit** | **Type** | **Gebreken of Verwachte Waarden** | **Beschrijving** |
|---|---|---|---|
| dps-id | String |  | toegewezen door AEM Mobile en opgeslagen door AEM na uploaden naar AEM Mobile of geïmporteerd uit AEM Mobile |
| dps-resourceType | String | dps:Article | `dps:Banner` \| `dps:Collection` \| `entity type property` |
| dps-versie | String |  | versie van AEM Mobile-entiteit (ook opgenomen in de volledige AMM-id) |
| dps-lastSynced | Datum |  | datum van laatste synchronisatie/import uit AEM Mobile naar AEM |
| dps-lastUploaded | Datum |  | datum van laatste upload van AEM naar AEM Mobile |
| dps-lastUploadedBy | String :userid |  | ID-gebruiker die het laatste uploadverzoek van AEM naar AEM Mobile heeft uitgevoerd |

## Eigenschappen van kernmetagegevens {#core-metadata-properties}

| Eigenschapnaam | Type | Standaardwaarden of Verwachte waarden |
|--- |--- |--- |
| dps-title | String |  |
| dps-shortTitle | String |  |
| dps-abstract | String |  |
| dps-shortAbstract | String |  |
| dps-afdeling | String |  |
| dps-categorie | String |  |
| dps-trefwoorden | String [] |  |
| dps-internalKeywords | String [] |  |
| dps-belang | String [] | Important from {&quot;low&quot;, &quot;normal&quot;, &quot;high&quot;} |

### Artikelen {#articles}

| **de Naam van het Bezit** | **Type** | **Gebreken of Verwachte Waarden** |
|---|---|---|
| dps-auteur | String |  |
| dps-auteurURL | String |  |
| dps-hideFromBrowsePage | Boolean |  |
| dps-toegang | String | ProtectedAccess from {&quot;protected&quot;, &quot;metered&quot;, &quot;free&quot;} |
| **Sociale** |  |  |
| dps-socialShareURL | String |  |
| dps-articleText | String |  |
| dps-url | String |  |

### Banners {#banners}

| **de Naam van het Bezit** | **Type** | **Gebreken of Verwachte Waarden** |
|---|---|---|
| dps-tapAction |  | TapAction from {webLink} |
| dps-tapActinUrl |  |  |

### Verzamelingen {#collections}

| Eigenschapnaam | Type | Standaardwaarden of Verwachte waarden |
|--- |--- |--- |
| dps-productId | String |  |
| dps-readingPosition | String | from {&quot;reset&quot;,&quot;keep&quot;} |
| dps-horizontalSwipe | Boolean |  |
| dps-allowDownload | Boolean |  |
| dps-openDefault | String | van &quot;browsePage&quot;,&quot;contentView&quot;&rbrace; |
| dps-lay-out | String |  |

## Inhoudsknooppunten {#content-nodes}

### Algemene knooppunten {#common-nodes}

| Node Name | Type | Standaardwaarden of Verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| image | jcr:primaryType=nt:unstructured <br> sling :resourceType=foundation/components/image |  |  |

### Entiteiten {#entities}

#### Artikelen {#articles-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| social-share-image |  | jcr:primaryType=nt:unstructured <br> sling :resourceType=foundation/components/image |  |

#### Banners {#banners-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|---|---|---|---|
| NA |  |  |  |

#### Verzamelingen {#collections-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| achtergrondafbeelding | jcr:primaryType=nt:unstructured <br> sling :resourceType=foundation/components/image |  |  |
