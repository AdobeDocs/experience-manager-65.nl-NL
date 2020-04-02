---
title: Eigenschappen en knooppunten van inhoud
seo-title: Eigenschappen en knooppunten van inhoud
description: Volg deze pagina voor meer informatie over eigenschappen en knooppunten van inhoud.
seo-description: Volg deze pagina voor meer informatie over eigenschappen en knooppunten van inhoud.
uuid: 2dad52c8-5b6c-4b90-8498-62217a9a27fc
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: f5721ddc-df5c-496c-be61-38d1cab63ad4
translation-type: tm+mt
source-git-commit: 50c0bdfc3203410d392e53536bc7cd00245406e5

---


# Eigenschappen en knooppunten van inhoud {#content-properties-and-nodes}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Artikelen, banners en verzamelingen worden weergegeven als cq:pagina&#39;s in AEM.

Ze delen dezelfde algemene eigenschappen die u kunt vinden in elke cq:Page, in aanvulling op verschillende hieronder getoonde eigenschappen die de metagegevens van de Mobile On-Demand Services van Adobe Experience Manager (AEM) vertegenwoordigen en ondersteunende eigenschappen voor integratie.

In de volgende tabellen worden de eigenschappen en knooppunten van de inhoud beschreven.

## Algemene integratieeigenschappen {#common-integration-properties}

| **Eigenschapnaam** | **Type** | **Standaardwaarden of Verwachte waarden** | **Beschrijving** |
|---|---|---|---|
| dps-id | Tekenreeks |  | toegewezen door AEM Mobile en opgeslagen door AEM zodra geüpload naar AEM Mobile of geïmporteerd uit AEM Mobile |
| dps-resourceType | Tekenreeks | dps:Artikel | dps:banner | dps:Verzameling | eigenschap type entiteit |
| dps-versie | Tekenreeks |  | versie van AEM Mobile-entiteit (ook opgenomen in de volledige AMM-id) |
| dps-lastSynced | Date |  | datum van laatste synchronisatie/import van AEM Mobile naar AEM |
| dps-lastUploaded | Date |  | datum van laatste upload van AEM naar AEM Mobile |
| dps-lastUploadedBy | String:userid |  | De gebruiker die het laatste uploadverzoek van AEM aan AEM Mobile uitvoerde |

## Eigenschappen van kernmetagegevens {#core-metadata-properties}

| Eigenschapnaam | Type | Standaardwaarden of Verwachte waarden |
|--- |--- |--- |
| dps-title | Tekenreeks |  |
| dps-shortTitle | Tekenreeks |  |
| dps-abstract | Tekenreeks |  |
| dps-shortAbstract | Tekenreeks |  |
| dps-afdeling | Tekenreeks |  |
| dps-categorie | Tekenreeks |  |
| dps-trefwoorden | Tekenreeks[] |  |
| dps-internalKeywords | Tekenreeks[] |  |
| dps-belang | Tekenreeks[] | Important from {&quot;low&quot;, &quot;normal&quot;, &quot;high&quot;} |

### Artikelen {#articles}

| **Eigenschapnaam** | **Type** | **Standaardwaarden of Verwachte waarden** |
|---|---|---|
| dps-auteur | Tekenreeks |  |
| dps-auteurURL | Tekenreeks |  |
| dps-hideFromBrowsePage | Boolean |  |
| dps-toegang | Tekenreeks | ProtectedAccess from {&quot;protected&quot;, &quot;metered&quot;, &quot;free&quot;} |
| **Sociaal** |  |  |
| dps-socialShareURL | Tekenreeks |  |
| dps-articleText | Tekenreeks |  |
| dps-url | Tekenreeks |  |

### Banners {#banners}

| **Eigenschapnaam** | **Type** | **Standaardwaarden of Verwachte waarden** |
|---|---|---|
| dps-tapAction |  | TapAction van {webLink} |
| dps-tapActinUrl |  |  |

### Verzamelingen {#collections}

| Eigenschapnaam | Type | Standaardwaarden of Verwachte waarden |
|--- |--- |--- |
| dps-productId | Tekenreeks |  |
| dps-readingPosition | Tekenreeks | from {&quot;reset&quot;,&quot;keep&quot;} |
| dps-horizontalSwipe | Boolean |  |
| dps-allowDownload | Boolean |  |
| dps-openDefault | Tekenreeks | van {1}&quot;browsePage&quot;,&quot;contentView&quot;} |
| dps-lay-out | Tekenreeks |  |

## Inhoudsknooppunten {#content-nodes}

### Algemene knooppunten {#common-nodes}

| Node Name | Type | Standaardwaarden of Verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| image | jcr:primaryType=nt:ongestructureerde <br> sling:resourceType=foundation/components/image |  |  |

### Entities {#entities}

#### Artikelen {#articles-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| social-share-image |  | jcr:primaryType=nt:ongestructureerde <br> sling:resourceType=foundation/components/image |  |

#### Banners {#banners-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|---|---|---|---|
| NA |  |  |  |

#### Verzamelingen {#collections-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| achtergrondafbeelding | jcr:primaryType=nt:ongestructureerde <br> sling:resourceType=foundation/components/image |  |  |
