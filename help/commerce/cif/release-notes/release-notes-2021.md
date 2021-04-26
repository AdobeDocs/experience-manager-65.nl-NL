---
title: Opmerkingen bij de release AEM2021
description: Opmerkingen bij de release AEM2021
translation-type: tm+mt
source-git-commit: 1a6d713e74056333b18ed68f58876c2a75d535b8
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 10%

---

# GitHub-releaseoverzicht van het Commerce Integration Framework

## Overzicht van systeemvereisten

Controleer de minimale systeemvereisten in de onderstaande tabel voor de CIF-versie die u momenteel gebruikt of die u in de toekomst wilt gebruiken.

**CIF-invoegtoepassing is nu beschikbaar via  [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). De oude AEM CIF-connector gaat naar de onderhoudsmodus en mag niet meer worden gebruikt. Migreer naar de nieuwe CIF-invoegtoepassing.**

| Component | Systeemvereisten |
|:-------|:-----:|
| CIF-invoegtoepassing | Minimaal: AEM 6.5.7, Magento 2.3.5 GraphQL schema&#39;s |
| CIF Core-componenten | [Systeemvereisten](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| Projectarchetype AEM | [Systeemvereisten](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: april 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | v021.04.22 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.04.22.zip) |
| CIF Core-componenten | 1.10.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,04,22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw {#what-is-new-april}

* Ondersteuning voor categorie UID - Hierdoor wordt integratie van andere leveranciers mogelijk voor systemen die strings gebruiken voor categorie-id&#39;s

* AEM extensie voor PWA Studio incl. voorbeeldintegratie

* Nieuwe CIF-kerncomponent voor navigatie die de WCM-kerncomponent voor navigatie uitbreidt

* Visuele indicator voor gefaseerde catalogusgegevens in AEM storefront

### Bugfixes {#bug-fixes-april}

* Het veld Hoofdcategorie is niet weergegeven op het tabblad Handel in de pagina-eigenschappen van categoriepagina&#39;s

## Releasedatum: {#what-is-new-march}

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,03,25 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw

* Ondersteuning voor Magento 2.4.2

### Wat is er verbeterd?

* Verbeterde herbruikbaarheid van productdetailcomponent voor pagina&#39;s met inhoud

* Betere caching en minder backend vraag voor PDPs

* Meerdere opgeloste problemen.

## Releasedatum: februari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 1.8.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.8.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,02,24 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw {#what-is-new-february}

* Product Experience Management: Verrijk de pagina&#39;s van de productcatalogus individueel met de Fragmenten van de Ervaring.

* Uitgebreide eigenschappen van de productconsole om verbonden Middelen en de Fragmenten van de Ervaring te tonen, met inbegrip van actie om snel aan de bijbehorende inhoud te navigeren.

### Wat is er verbeterd?{#what-is-improved-february}

* Verbeterde gegevenslaag aan de clientzijde met URL- en catalogusinformatie voor productafbeeldingen

* Meerdere opgeloste problemen.

## Releasedatum: januari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021 02 02 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw {#what-is-new-january}

* Product Experience Management: Het nieuwe de bezitslusje van de &quot;Handel&quot;voor Activa en de Fragmenten van de Ervaring. Op dit tabblad kunt u elementen en fragmenten uit de ervaring koppelen aan producten en categorieën. Het lusje toont ook gegevens in real time voor verbonden handelsobjecten en een verbinding om details in de productconsole te tonen.

### Wat is er verbeterd?{#what-is-improved-january}

* Verzend gebruikersgegevens na authentificatie naar de Laag van de Gegevens van de Adobe Cliënt.

* Meerdere opgeloste problemen.
