---
title: Opmerkingen bij de release Adobe Experience Manager Content en Commerce 2021
description: Opmerkingen bij de release Adobe Experience Manager Content en Commerce 2021.
exl-id: ec47c5f8-d4dd-469f-94df-5ee28f25d696
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 7c1aeec18f35b019a63d0385ada248b26a0df9de
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 4%

---

# Commerce integration framework GitHub Release-overzicht

## Overzicht van de systeemvereisten

Controleer de minimale systeemvereisten in de onderstaande tabel voor de CIF-versie die u momenteel gebruikt of die u in de toekomst wilt gebruiken.

| Component | Systeemvereisten |
|:-------|:-----:|
| CIF-invoegtoepassing | Minimaal: Adobe Experience Manager (AEM) 6.5.7, Adobe Commerce 2.3.5 GraphQL-schema&#39;s |
| CIF Core-componenten | [ Vereisten van het Systeem ](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM Project Archetype | [ Vereisten van het Systeem ](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: november 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021 11 18 00 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.11.18.00.zip) |
| CIF Core-componenten | 2.4.2. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.4.2) |
| CIF Venia Reference Site | 2021 12 01 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.12.01) |

### Wat is er nieuw? {#what-is-new-november}

* Uitgebreide myAccount-componenten die zijn gebaseerd op uitbreidbare Peregrine-componenten van Commerce

![ Uitgebreide myAccount componenten ](/help/assets/CIF/extended-myAccount-components.png)

* Auteurs kunnen ad-hoc Commerce-productaanbevelingen maken met behulp van aanvullende aanbevolen typen

* Ondersteuning voor cadeaukaarten in AEM Store

## Releasedatum: oktober 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021.10.2002 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.10.20.02.zip) |
| CIF Core-componenten | 2.4.0. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.4.0) |
| CIF Venia Reference Site | 2021 11 01 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.11.01) |

### Wat is er nieuw? {#what-is-new-october}

* De invoegtoepassing CIF ondersteunt de nieuwste Commerce v2.4.3 met nieuwe GraphQL API&#39;s en schema&#39;s

* Auteurs kunnen koppelingen naar product- en cataloguspagina&#39;s in tekstvelden toevoegen met de RTE (RTE). Er is een CIF-pictogram toegevoegd aan de RTE-werkbalk waarmee de kiezers snel het product of de categorie kunnen zoeken en selecteren zonder de context te verlaten.

* Bestaande pop-up winkelwagentje en afhandeling zijn vervangen door speciale AEM-winkelwagentje en afhandelingspagina&#39;s. De componenten op deze pagina&#39;s worden samengesteld met behulp van uitbreidbare Peregrine-onderdelen van Adobe Commerce

* Met de Commerce-backend kunnen verkopers bepaalde productcataloguscategorieën in de navigatie verbergen. De CIF Navigation Core Component respecteert de Commentaar configuratie &quot;omvat in menu&quot;om categorieën in navigatie te tonen/te verbergen

* AEM Storefront Venia retourneert de HTTP 404-fout als de categorie of productpagina niet wordt gevonden

## Releasedatum: september 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,09,27 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.09.27.zip) |
| CIF Core-componenten | 2.2.0. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.2.0) |
| CIF Venia Reference Site | 2021,09,23 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.09.23) |

### Wat is er nieuw? {#what-is-new-september}

* Het nieuwe tabblad &quot;Gerelateerde commerciële inhoud&quot; in Sites Editor verhoogt de efficiëntie van de auteur door snel toegang te krijgen tot relevante AEM-productinhoud voor de huidige context

  ![ Verwante handelsinhoud ](/help/assets/CIF/associated-commerce-content.png)

* Verbeterde gebruikersinterface van de productkiezer voor een betere gebruikerservaring, verbeterde efficiëntie en ondersteuning voor complexe productcatalogus

  ![ Nieuwe Plukker van het Product ](/help/assets/CIF/product-picker.png)

* Eigenschap &quot;include_in_menu&quot; in navigatiecomponent respecteren

### Bugfixes {#bug-fixes-september}

* Het leegmaken van de menucache werkt niet zoals verwacht

* JS-fouten tijdens de AEM CS-implementatiestap en wanneer geen clientcomponenten worden gebruikt

* Kan CIF cloud config niet maken in mappen met een sling :configs -knooppunt

## Releasedatum: augustus 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021 09 02 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.09.02.zip) |
| CIF Core-componenten | 2.1.0. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.1.0) |
| CIF Venia Reference Site | 2021,08,27 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.08.27) |

### Wat is er nieuw? {#what-is-new-august}

* De nieuwe interface van de Plukker van de Categorie voor betere gebruikerservaring, verhoogde efficiency en betere steun voor complexe productcatalogus

  ![ Nieuwe Plukker van de Categorie ](/help/assets/CIF/category-picker.png)

* Betere A11Y-ondersteuning voor CIF Core-componenten

### Bugfixes {#bug-fixes-august}

* Kan categorie filteraccordeon niet sluiten wanneer deze is geopend

* De eigenschap &#39;Call to action text&#39; is afgebroken in de productteaser

* CIF JS-fouten tijdens de implementatiestap van AEM CS

* Toegang tot onbewerkte producten herstellen voor in kaart gebrachte producten

## Releasedatum: juli 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,07,21 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.07.21.zip) |
| CIF Core-componenten | 2.0.0. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.0.0) |
| CIF Venia Reference Site | 2021,07,22 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.07.22) |

### Wat is er nieuw? {#what-is-new-july}

* CIF Core Components v2
   * Vereenvoudigde en verbeterde configuraties voor PDP/PLP URL en SEO
   * Visuele indicator voor gefaseerde productgegevens op auteurswijze voor betere zichtbaarheid van aanstaande veranderingen
   * Nieuwe sitemapcomponent voor inhoud- en handelspagina&#39;s

* Steun voor [ het Product van Adobe Commerce AI Aanbeveling, aangedreven door Adobe AI ](https://business.adobe.com/ai/adobe-genai.html) in AEM Storefront gebruikend vooraf bepaalde of op-de-vlieg gecreeerde aanbevelingen

## Releasedatum: juni 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,06,18 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.06.18.zip) |
| CIF Core-componenten | 1.12.0. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.12.0) |
| CIF Venia Reference Site | 2021 06 12 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.06.17) |

### Wat is er nieuw? {#what-is-new-june}

* Nieuwe CIF-product- en categoriereferentiegegevenstypen voor Content Fragments (incl. product/categoriekiezer (ondersteuning voor gebruikersinterface)
* Nieuwe Commerce Content Fragment Core-component
* Full-text handelzoekopdracht ondersteund in AEM-achtergrond
* Commerce Core Components biedt ondersteuning voor Adobe Commerce AI Recs-gegevensverzameling
* Verbeterde SEO-vriendelijke URL&#39;s voor categoriepagina&#39;s
* Ondersteuning voor aangepaste HTTP-headers per site/config

## Releasedatum: mei 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,05,26 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.05.26.zip) |
| CIF Core-componenten | 1.11.0. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.11.0) |
| CIF Venia Reference Site | 2021,05,24 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.05.24) |

### Wat is er nieuw? {#what-is-new-may}

* Pagineringsondersteuning voor gekoppelde inhoud in eigenschappen van productconsole

### Bugfixes {#bug-fixes-may}

* Miniaturen van middelen worden niet weergegeven op het tabblad Middelen van de producteigenschappen

* Breadcrumb herstelt voorvertoningsgegevens in productconsole

## Releasedatum: april 2021

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2021,04,22 | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.04.22.zip) |
| CIF Core-componenten | 1.10.0. | [ GitHub ](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,04,22 | [ GitHub ](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-april}

* Steun voor categorie UID - dit ontgrendelt derde handelsintegraties voor systemen die Koorden voor categorie ids gebruiken

* AEM extension for PWA Studio incl. voorbeeld-integratie

* Nieuwe CIF-kerncomponent voor navigatie die de WCM-kerncomponent uitbreidt

### Bugfixes {#bug-fixes-april}

* Het veld Hoofdcategorie is niet weergegeven op het tabblad Handel in de pagina-eigenschappen van categoriepagina&#39;s

## Releasedatum: maart 2021 {#what-is-new-march}

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF Connector | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.9.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,03,25 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Nieuwe functies

* Ondersteuning voor Adobe Commerce 2.4.2

### Verbeterde functies

* Verbeterde herbruikbaarheid van productdetailcomponent voor inhoudsgestuurde pagina&#39;s

* Betere caching en minder backend vraag voor PDPs

* Meerdere opgeloste problemen.

## Releasedatum: februari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF Connector | 1.8.0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.8.0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021,02,24 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-february}

* Product Experience Management: verrijk de productcataloguspagina&#39;s afzonderlijk met Experience Fragments.

* Uitgebreide eigenschappen van de productconsole om verbonden Assets en de Fragmenten van de Ervaring te tonen, met inbegrip van actie om snel aan de bijbehorende inhoud te navigeren.

### Verbeterde functies  {#what-is-improved-february}

* Verbeterde gegevenslaag aan de clientzijde met URL- en categoriegegevens voor productafbeeldingen.

* Meerdere opgeloste problemen.

## Releasedatum: januari 2021

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF Connector | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 1.7.0. | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia Reference Site | 2021 02 02 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Wat is er nieuw? {#what-is-new-january}

* Product Experience Management: Nieuw tabblad &quot;Commerce&quot; voor Assets en Experience Fragments. Op dit tabblad kunt u Assets en Experience Fragments koppelen aan producten en categorieën. Het lusje toont ook gegevens in real time voor verbonden handelsobjecten en een verbinding om details in de productconsole te tonen.

### Verbeterde functies  {#what-is-improved-january}

* Stuur gebruikersgegevens na verificatie naar de Adobe Client Data Layer.

* Meerdere opgeloste problemen.
