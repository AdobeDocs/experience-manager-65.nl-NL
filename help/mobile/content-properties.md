---
title: Eigenschappen en knooppunten van inhoud
seo-title: Content Properties and Nodes
description: Volg deze pagina voor meer informatie over eigenschappen en knooppunten van inhoud.
seo-description: Follow this page to learn about content properties and nodes.
uuid: 2dad52c8-5b6c-4b90-8498-62217a9a27fc
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: f5721ddc-df5c-496c-be61-38d1cab63ad4
exl-id: 05c8c846-69cc-4075-9149-33890b3d1e08
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 12%

---

# Eigenschappen en knooppunten van inhoud {#content-properties-and-nodes}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

Artikelen, banners en verzamelingen worden weergegeven als cq:Pagina&#39;s in AEM.

Ze delen dezelfde gemeenschappelijke eigenschappen die in elke cq:pagina worden gevonden, naast diverse hieronder getoonde eigenschappen die de metagegevens van de mobiele on-demand services van Adobe Experience Manager (AEM) vertegenwoordigen en ondersteunende eigenschappen voor integratie.

In de volgende tabellen worden de eigenschappen en knooppunten van de inhoud beschreven.

## Algemene integratieeigenschappen {#common-integration-properties}

| **Eigenschapnaam** | **Type** | **Standaardwaarden of Verwachte waarden** | **Beschrijving** |
|---|---|---|---|
| dps-id | Tekenreeks |  | toegewezen door AEM Mobile en opgeslagen door AEM zodra geüpload naar AEM Mobile of geïmporteerd uit AEM Mobile |
| dps-resourceType | Tekenreeks | dps:Artikel | dps:banner | dps:Verzameling | eigenschap type entiteit |
| dps-versie | Tekenreeks |  | versie van AEM Mobile-entiteit (ook opgenomen in de volledige AMM-id) |
| dps-lastSynced | Date |  | datum van laatste synchronisatie/import uit AEM Mobile naar AEM |
| dps-lastUploaded | Date |  | datum van laatste upload van AEM naar AEM Mobile |
| dps-lastUploadedBy | String:userid |  | De gebruiker van identiteitskaart die het laatste uploadverzoek van AEM aan AEM Mobile uitvoerde |

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
| dps-openDefault | Tekenreeks | from {&quot;browsePage&quot;,&quot;contentView&quot;} |
| dps-lay-out | Tekenreeks |  |

## Inhoudsknooppunten {#content-nodes}

### Algemene knooppunten {#common-nodes}

| Node Name | Type | Standaardwaarden of Verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| afbeelding | jcr:primaryType=nt:unStructured <br> sling:resourceType=foundation/components/image |  |  |

### Entiteiten {#entities}

#### Artikelen {#articles-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| social-share-image |  | jcr:primaryType=nt:unStructured <br> sling:resourceType=foundation/components/image |  |

#### Banners {#banners-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|---|---|---|---|
| NA |  |  |  |

#### Verzamelingen {#collections-1}

| Node Name | Type | Standaardwaarden van verwachte waarden | Beschrijving |
|--- |--- |--- |--- |
| achtergrondafbeelding | jcr:primaryType=nt:unStructured <br> sling:resourceType=foundation/components/image |  |  |
