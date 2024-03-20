---
title: Opmerkingen bij de release Adobe Experience Manager Content and Commerce 2021
description: Opmerkingen bij de release Adobe Experience Manager Content and Commerce 2021.
exl-id: ec47c5f8-d4dd-469f-94df-5ee28f25d696
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 4%

---

# Commerce integration framework GitHub Release-overzicht

## Overzicht van de systeemvereisten

Controleer de minimale systeemvereisten in de onderstaande tabel voor de CIF versie die u momenteel gebruikt of die u in de toekomst wilt gebruiken.

| Component | Systeemvereisten |
|:-------|:-----:|
| CIF | Minimaal: Adobe Experience Manager (AEM) 6.5.7, Adobe Commerce 2.3.5 GraphQL-schema&#39;s |
| CIF kerncomponenten | [Systeemvereisten](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| Projectarchetype AEM | [Systeemvereisten](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: november 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021 11 18 00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.11.18.00.zip) |
| CIF kerncomponenten | 2.4.2. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.4.2) |
| CIF Venia-referentiegebied | 2021 12 01 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.12.01) |

### Wat is er nieuw? {#what-is-new-november}

* Uitgebreide myAccount-componenten die zijn gebaseerd op uitbreidbare Peregrine-componenten van de Handel

![Uitgebreide myAccount-componenten](/help/assets/CIF/extended-myAccount-components.png)

* Auteurs kunnen ad-hoc Product Recommendations van de Handel tot stand brengen gebruikend extra advisetypes

* Ondersteuning voor cadeaukaarten in AEM Storefront

## Releasedatum: oktober 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021.10.2002 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.10.20.02.zip) |
| CIF kerncomponenten | 2.4.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.4.0) |
| CIF Venia-referentiegebied | 2021 11 01 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.11.01) |

### Wat is er nieuw? {#what-is-new-october}

* De CIF add-on biedt ondersteuning voor de nieuwste Commerce v2.4.3 met nieuwe GraphQL API&#39;s en schema&#39;s

* Auteurs kunnen koppelingen naar product- en cataloguspagina&#39;s in tekstvelden toevoegen met de RTE (RTE). Er is een CIF pictogram toegevoegd aan de RTE-werkbalk waarmee de kiezers snel het product of de categorie kunnen zoeken en selecteren zonder de context te verlaten.

* Bestaande pop-up winkelwagentje en kassa zijn vervangen door speciale AEM winkelwagentje en afhandelingspagina&#39;s. De componenten op deze pagina&#39;s worden samengesteld met behulp van uitbreidbare Peregrine-onderdelen van Adobe Commerce

* Handelaars kunnen bepaalde categorieën van de productcatalogus in de navigatie verbergen gebruikend de achtergrond van de Handel. De CIF component van de Kern van de Navigatie eerbiedigt de handel achterste configuratie &quot;omvat in menu&quot;om categorieën in navigatie te tonen/te verbergen

* AEM Storefront Venia retourneert de HTTP 404-fout als de categorie of productpagina niet wordt gevonden

## Releasedatum: september 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021,09,27 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.09.27.zip) |
| CIF kerncomponenten | 2.2.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.2.0) |
| CIF Venia-referentiegebied | 2021,09,23 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.09.23) |

### Wat is er nieuw? {#what-is-new-september}

* Het nieuwe lusje &quot;bijbehorende commerciële inhoud&quot;in de redacteur van Plaatsen verhoogt auteur efficiency door snel toegang tot relevante AEM productinhoud voor de huidige context te krijgen

  ![Gekoppelde commerciële inhoud](/help/assets/CIF/associated-commerce-content.png)

* Verbeterde gebruikersinterface van de productkiezer voor een betere gebruikerservaring, verbeterde efficiëntie en ondersteuning voor complexe productcatalogus

  ![Nieuwe productkiezer](/help/assets/CIF/product-picker.png)

* Eigenschap &quot;include_in_menu&quot; in navigatiecomponent respecteren

### Bugfixes {#bug-fixes-september}

* Het leegmaken van de menucache werkt niet zoals verwacht

* JS-fouten tijdens AEM CS-implementatiestap en wanneer geen clientcomponenten worden gebruikt

* Kan CIF wolkenconfiguratie in omslagen tot stand brengen die een helling hebben:vormt knoop

## Releasedatum: augustus 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021 09 02 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.09.02.zip) |
| CIF kerncomponenten | 2.1.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.1.0) |
| CIF Venia-referentiegebied | 2021,08,27 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.08.27) |

### Wat is er nieuw? {#what-is-new-august}

* De nieuwe interface van de Plukker van de Categorie voor betere gebruikerservaring, verhoogde efficiency en betere steun voor complexe productcatalogus

  ![Nieuwe rubriekkiezer](/help/assets/CIF/category-picker.png)

* Betere A11Y-ondersteuning voor CIF Core Components

### Bugfixes {#bug-fixes-august}

* Kan categorie filteraccordeon niet sluiten wanneer deze is geopend

* De eigenschap &#39;Call to action text&#39; is verbroken in de productteaser

* JS-fouten CIF tijdens AEM implementatiestap voor CS

* Toegang tot onbewerkte producten herstellen voor in kaart gebrachte producten

## Releasedatum: juli 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021,07,21 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.07.21.zip) |
| CIF kerncomponenten | 2.0.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.0.0) |
| CIF Venia-referentiegebied | 2021,07,22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.07.22) |

### Wat is er nieuw? {#what-is-new-july}

* CIF Core Components v2
   * Vereenvoudigde en verbeterde configuraties voor PDP/PLP URL en SEO
   * Visuele indicator voor gefaseerde productgegevens op auteurswijze voor betere zichtbaarheid van aanstaande veranderingen
   * Nieuwe sitemapcomponent voor inhoud- en handelspagina&#39;s

* Ondersteuning voor [Adobe Commerce Sensei Product Recommendation, aangedreven door Adobe Sensei](https://business.adobe.com/products/magento/product-recommendations.html) in AEM Storefront met behulp van vooraf gedefinieerde of tijdens de vlucht gemaakte aanbevelingen

## Releasedatum: juni 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021,06,18 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.06.18.zip) |
| CIF kerncomponenten | 1.12.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.12.0) |
| CIF Venia-referentiegebied | 2021 06 12 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.06.17) |

### Wat is er nieuw? {#what-is-new-june}

* Nieuwe CIF product- en categoriereferentietypen voor inhoudsfragmenten (incl. product/categoriekiezer (ondersteuning voor gebruikersinterface)
* New Commerce Content Fragment Core Component
* Full-text zoekopdracht ondersteund in AEM achterkant
* Commerce Core Components ondersteunt Adobe Commerce Sensei Recs gegevensverzameling
* Verbeterde SEO-vriendelijke URL&#39;s voor categoriepagina&#39;s
* Ondersteuning voor aangepaste HTTP-headers per site/config

## Releasedatum: mei 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021,05,26 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.05.26.zip) |
| CIF kerncomponenten | 1.11.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.11.0) |
| CIF Venia-referentiegebied | 2021,05,24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.05.24) |

### Wat is er nieuw? {#what-is-new-may}

* Pagineringsondersteuning voor gekoppelde inhoud in eigenschappen van productconsole

### Bugfixes {#bug-fixes-may}

* Miniaturen van middelen worden niet weergegeven op het tabblad Middelen van de producteigenschappen

* Breadcrumb herstelt voorvertoningsgegevens in productconsole

## Releasedatum: april 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2021,04,22 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.04.22.zip) |
| CIF kerncomponenten | 1.10.0. | [GitHub](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-referentiegebied | 2021,04,22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-april}

* Steun voor categorie UID - dit ontgrendelt derde handelsintegraties voor systemen die Koorden voor categorie ids gebruiken

* AEM extensie voor PWA Studio incl. voorbeeld-integratie

* Nieuwe CIF kerncomponent voor navigatie die de WCM-kerncomponent voor navigatie uitbreidt

### Bugfixes {#bug-fixes-april}

* Het veld Hoofdcategorie is niet weergegeven op het tabblad Handel in de pagina-eigenschappen van categoriepagina&#39;s

## Releasedatum: maart 2021 {#what-is-new-march}

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-referentiegebied | 2021,03,25 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Nieuwe functies

* Ondersteuning voor Adobe Commerce 2.4.2

### Verbeterde functies

* Verbeterde herbruikbaarheid van productdetailcomponent voor inhoudsgestuurde pagina&#39;s

* Betere caching en minder backend vraag voor PDPs

* Meerdere opgeloste problemen.

## Releasedatum: februari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 1.8.0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 1.8.0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-referentiegebied | 2021,02,24 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-february}

* Product Experience Management: verrijk de productcataloguspagina&#39;s afzonderlijk met Experience Fragments.

* De uitgebreide eigenschappen van de productconsole om verbonden Middelen en de Fragmenten van de Ervaring te tonen, met inbegrip van actie om snel aan de bijbehorende inhoud te navigeren.

### Verbeterde functies  {#what-is-improved-february}

* Verbeterde gegevenslaag aan de clientzijde met URL- en categoriegegevens voor productafbeeldingen.

* Meerdere opgeloste problemen.

## Releasedatum: januari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-referentiegebied | 2021 02 02 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-january}

* Product Experience Management: Nieuw tabblad Eigenschappen &#39;Commerce&#39; voor Elementen en Ervingfragmenten. Op dit tabblad kunt u elementen en fragmenten uit de ervaring koppelen aan producten en categorieën. Het lusje toont ook gegevens in real time voor verbonden handelsobjecten en een verbinding om details in de productconsole te tonen.

### Verbeterde functies  {#what-is-improved-january}

* Verzend gebruikersgegevens na authentificatie aan de Laag van de Gegevens van de Cliënt van de Adobe.

* Meerdere opgeloste problemen.
