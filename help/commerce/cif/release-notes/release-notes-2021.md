---
title: Opmerkingen bij de release AEM2021
description: Opmerkingen bij de release AEM2021
exl-id: ec47c5f8-d4dd-469f-94df-5ee28f25d696
source-git-commit: b6703f519295eef728d5504360d99de69438064c
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 7%

---

# GitHub-releaseoverzicht van het Commerce Integration Framework

## Overzicht van systeemvereisten

Controleer de minimale systeemvereisten in de onderstaande tabel voor de CIF-versie die u momenteel gebruikt of die u in de toekomst wilt gebruiken.

**Met de versie van April hebben wij de Schakelaar CIF van GitHub met CIF toe:voegen-** op vervangen die op de Distributie [ van de Software van ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)Adobe beschikbaar is. De omschakeling aan toe:voegen-op komt met grote voordelen voor projecten:

* De meeste nieuwe functies zijn direct beschikbaar op AEM 6.5 (niet meer wachtend op zijpoort met functies)
* Eenvoudig upgradebaar naar nieuwe invoegversies
* Gereed voor Cloud Service

De oude AEM CIF-connector gaat naar de onderhoudsmodus en mag niet meer worden gebruikt. Vervang de CIF-connector door de nieuwe CIF-invoegtoepassing. Voor de meeste projecten moet eenvoudig een pakketvervanging mogelijk zijn.

| Component | Systeemvereisten |
|:-------|:-----:|
| CIF-invoegtoepassing | Minimaal: AEM 6.5.7, Magento 2.3.5 GraphQL schema&#39;s |
| CIF Core-componenten | [Systeemvereisten](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| Projectarchetype AEM | [Systeemvereisten](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: augustus 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,08,20 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.08.20.zip) |
| CIF Core-componenten | 2.1.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.1.0) |
| CIF Venia Reference Site | 2021,08,27 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.08.27) |

### Wat is er nieuw? {#what-is-new-august}

* De nieuwe interface van de Categoriekiezer voor betere gebruikerservaring, verhoogde efficiency en betere steun voor complexe productcatalogus

   ![Nieuwe rubriekkiezer](/help/assets/CIF/category-picker.png)

* Betere A11Y-ondersteuning voor CIF Core-componenten

### Bugfixes {#bug-fixes-august}

* Kan categorie filteraccordeon niet sluiten wanneer deze is geopend

* De eigenschap &#39;Call to action text&#39; is verbroken in de productteaser

* CIF JS-fouten tijdens AEM implementatiestap van CS

* Toegang tot onbewerkte producten herstellen voor in kaart gebrachte producten

## Releasedatum: juli 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,07,21 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.07.21.zip) |
| CIF Core-componenten | 2.0.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.0.0) |
| CIF Venia Reference Site | 2021,07,22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.07.22) |

### Wat is er nieuw? {#what-is-new-july}

* CIF Core Components v2
   * Vereenvoudigde en verbeterde configuraties voor PDP/PLP URL en SEO
   * Visuele indicator voor gefaseerde productgegevens op auteurswijze voor betere zichtbaarheid van aanstaande veranderingen
   * Nieuwe sitemapcomponent voor inhoud- en handelspagina&#39;s

* Ondersteuning voor [Adobe Commerce Sensei Product Recommendation, aangedreven door Adobe Sensei](https://business.adobe.com/products/magento/product-recommendations.html) in AEM Storefront met behulp van vooraf gedefinieerde of ter plekke gemaakte aanbevelingen

## Releasedatum: juni 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,06,18 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.06.18.zip) |
| CIF Core-componenten | 1.12.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.12.0) |
| CIF Venia Reference Site | 2021 06 12 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.06.17) |

### Wat is er nieuw? {#what-is-new-june}

* Nieuwe CIF-product- en categoriereferentiedetypen voor inhoudsfragmenten (incl. product/categoriekiezer (ondersteuning voor gebruikersinterface)
* New Commerce Content Fragment Core Component
* Full-text zoekopdracht ondersteund in AEM achterkant
* Commerce Core Components support Adobe Commerce Sensei Recs data collection
* Verbeterde SEO-vriendelijke URL&#39;s voor categoriepagina&#39;s
* Ondersteuning voor aangepaste HTTP-headers per site/config

## Releasedatum: Mei 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,05,26 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.05.26.zip) |
| CIF Core-componenten | 1.11.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.11.0) |
| CIF Venia Reference Site | 2021,05,24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.05.24) |

### Wat is er nieuw? {#what-is-new-may}

* Pagineringsondersteuning voor gekoppelde inhoud in eigenschappen van productconsole

### Bugfixes {#bug-fixes-may}

* Miniaturen van middelen worden niet weergegeven op het tabblad Middelen van de producteigenschappen

* Breadcrumb herstelt voorvertoningsgegevens in productconsole

## Releasedatum: april 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,04,22 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.04.22.zip) |
| CIF Core-componenten | 1.10.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,04,22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-april}

* Steun voor categorie UID - dit ontgrendelt derde handelsintegraties voor systemen die Koorden voor categorie ids gebruiken

* AEM extensie voor PWA Studio incl. voorbeeldintegratie

* Nieuwe CIF-kerncomponent voor navigatie die de WCM-kerncomponent voor navigatie uitbreidt

### Bugfixes {#bug-fixes-april}

* Het veld Hoofdcategorie is niet weergegeven op het tabblad Handel in de pagina-eigenschappen van categoriepagina&#39;s

## Releasedatum: maart 2021 {#what-is-new-march}

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,03,25 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw

* Ondersteuning voor Magento 2.4.2

### Verbeterde functies

* Verbeterde herbruikbaarheid van productdetailcomponent voor inhoudsgestuurde pagina&#39;s

* Betere caching en minder backend vraag voor PDPs

* Meerdere opgeloste problemen.

## Releasedatum: februari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 1.8.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.8.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,02,24 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-february}

* Product Experience Management: Verrijk de pagina&#39;s van de productcatalogus individueel met de Fragmenten van de Ervaring.

* De uitgebreide eigenschappen van de productconsole om verbonden Middelen en de Fragmenten van de Ervaring te tonen, met inbegrip van actie om snel aan de bijbehorende inhoud te navigeren.

### Verbeterde functies  {#what-is-improved-february}

* Verbeterde gegevenslaag aan de clientzijde met URL- en categoriegegevens voor productafbeeldingen.

* Meerdere opgeloste problemen.

## Releasedatum: januari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021 02 02 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-january}

* Product Experience Management: Het nieuwe de bezitslusje van de &quot;Handel&quot;voor Activa en de Fragmenten van de Ervaring. Op dit tabblad kunt u elementen en fragmenten uit de ervaring koppelen aan producten en categorieën. Het lusje toont ook gegevens in real time voor verbonden handelsobjecten en een verbinding om details in de productconsole te tonen.

### Verbeterde functies  {#what-is-improved-january}

* Verzend gebruikersgegevens na authentificatie naar de Laag van de Gegevens van de Adobe Cliënt.

* Meerdere opgeloste problemen.
