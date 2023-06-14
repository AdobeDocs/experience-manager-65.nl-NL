---
title: Opmerkingen bij de release AEM 2022
description: Opmerkingen bij de release AEM 2022
exl-id: d0a66e70-c4f1-4051-8161-11f07dad0612
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 4%

---

# GitHub-releaseoverzicht van het Commerce Integration Framework

## Overzicht van systeemvereisten

Controleer de minimale systeemvereisten in de onderstaande tabel voor de CIF-versie die u momenteel gebruikt of die u in de toekomst wilt gebruiken.

| Component | Systeemvereisten |
|:-------|:-----:|
| CIF-invoegtoepassing | Minimaal: AEM 6.5.7, Adobe Commerce 2.3.5 GraphQL-schema&#39;s |
| CIF Core-componenten | [Systeemvereisten](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| Projectarchetype AEM | [Systeemvereisten](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: september 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2022.09.20.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.09.20.00.zip) |
| CIF Core-componenten | 2.11.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.11.0) |
| CIF Venia Reference Site | 2022.09.02 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.09.02) |

### Wat is er nieuw? {#what-is-new-september}

* Auteurs kunnen productlijsten dynamisch verrijken met Experience Fragments (voorbeeld: Banner tussen productaanbiedingen plaatsen)
* De component List ondersteunt gekoppelde product-/categoriepagina&#39;s om gerelateerde pagina&#39;s dynamisch weer te geven
* Ondersteuning voor peregrine 12.5-onderdelen
* Steun voor het laden van de prijs aan de clientzijde in productschouder en carrousel

## Releasedatum: juli 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2022.08.02.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.08.02.00.zip) |

### Wat is er nieuw? {#what-is-new-july}

* Koppeling van AEM pagina&#39;s naar producten en categorieën via AEM pagina-eigenschappen plus overzicht in de cockpit van het product
  ![productcockpit page association](/help/assets/CIF/product_cockpit_page_association.png)

## Releasedatum: juni 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2022.07.05.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.07.05.00.zip) |
| CIF Core-componenten | 2.10.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) |
| CIF Venia Reference Site | 2022.07.04 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.07.04) |

### Wat is er nieuw? {#what-is-new-june}

* De verrijking van de productcatalogus steunt nu AEM pagina&#39;s, toelatend auteurs om pagina - productvereniging te beheren.

* Verschillende verbeteringen voor CIF Core-componenten

### Bugfixes {#bug-fixes-june}

* Aanmeldingstoken toevoegen aan prijsophaalbewerkingen op de client

* Onjuiste paginacomponent in gegevenslaag.

## Releasedatum: mei 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2022.05.31.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.05.31.00.zip) |
| CIF Core-componenten | 2.9.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.9.0) |
| CIF Venia Reference Site | 2022.05.30 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.05.30) |

### Wat is er nieuw? {#what-is-new-may}

* Pagina met eigenschappen van cockpit-eigenschappen voor nieuwe producten voor een beter en vereenvoudigd overzicht

![overzicht van de eigenschappen van productcockpit](/help/assets/CIF/product_cockpit_properties_overview.png)

* Verbeterde compatibiliteit en robuustheid voor connectors van derden op I/O Runtime

* Verbeterde ondersteuning voor overschreven GQL Client-configuratie (bijvoorbeeld aangepaste caching-functionaliteit instellen)

### Bugfixes {#bug-fixes-may}

* In het veld voor de productkiezer voor meerdere waarden worden de tweede en aanvullende producten als ongeldig weergegeven

* De productkiezer wordt soms verborgen achter componenten

## Releasedatum: april 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2022.04.28.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.04.28.00.zip) |
| CIF Core-componenten | 2.8.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.8.0) |
| CIF Venia Reference Site | 2022.04.28 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.04.28) |

### Wat is er nieuw? {#what-is-new-april}

* Snelle toegang tot productcockpit: Eenvoudig toegang tot volledige gedetailleerde productinformatie met één klik in de Editor voor sites

  ![Enable wishlist](/help/assets/CIF/enable-wishlist.png)

* Steun voor extra marketingcomponenten: De componenten kunnen worden gevormd om toe:voegen-aan-kar en toe:voegen-aan-wenslijst vraag-aan-actie te tonen

  ![Snelkoppeling naar productcockpit in Sites-editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)

## Releasedatum: februari 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2022.02.24.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.02.24.00.zip) |
| CIF Core-componenten | 2.6.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) |
| CIF Venia Reference Site | 2022.02.24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.02.24) |

### Wat is er nieuw? {#what-is-new-march}

* Bèta: AEM ondersteuning voor Kerncomponent CIF Search Commerce LiveSearch
* Verbeterde SEO voor meerdere winkelscenario&#39;s: URL-indelingen voor PDP/PLP kunnen nu op archiefniveau worden geconfigureerd via de CIF Cloud Config-eigenschappen
* Productkiezer ondersteunt gefaseerde producten via de nieuwe filteroptie in de gebruikersinterface. Laat inhoudsartsen toe om het beheer van productinhoud voor te bereiden voor de aanstaande productlanceringen
* Vereenvoudigd CIF-configuratiebeheer en foutafhandeling door CIF Cloud Config-naam te gebruiken in plaats van proxyURL te configureren
* Handmatige categorieselectie voor productlijst en carrouselcomponenten. Hiermee kunnen gebruikers van inhoud deze componenten gebruiken op inhoudspagina&#39;s, buiten de cataloguservaring

## Releasedatum: Januari 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF-invoegtoepassing | 2022.01.20.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.01.20.00.zip) |
| CIF Core-componenten | 2.5.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.5.0) |
| CIF Venia Reference Site | 2022.01.27 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.01.27) |

### Wat is er nieuw? {#what-is-new-january}

* Verbeterde myAccount-componenten
* De component van de Aanbeveling van het product steunt extra paginatypes (homepage, winkelwagentje, ordesbevestiging)
* **Wishlist**
   * Aangemeld door bezoekers kunnen producten toevoegen aan een verlanglijst
   * Beheer van de verlanglijst en de bijbehorende producten is mogelijk via mijn account
   * De knop &quot;Toevoegen aan wenslijst&quot; kan worden ingeschakeld/uitgeschakeld op componentniveau via beleid (bijvoorbeeld productgummetje, productdetails)
   * Beschikbaar als een kerncomponent en in de AEM Venia Storefront

![Wishlist](/help/assets/CIF/wishlist.png)
