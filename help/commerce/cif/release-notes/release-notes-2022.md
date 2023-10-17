---
title: Opmerkingen bij de release AEM2022
description: Opmerkingen bij de release Adobe Experience Manager Content and Commerce 2022.
exl-id: d0a66e70-c4f1-4051-8161-11f07dad0612
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 4%

---

# GitHub-releaseoverzicht van het Commerce Integration Framework

## Overzicht van de systeemvereisten

Controleer de minimale systeemvereisten in de onderstaande tabel voor de CIF versie die u momenteel gebruikt of die u in de toekomst wilt gebruiken.

| Component | Systeemvereisten |
|:-------|:-----:|
| CIF | Minimaal: AEM 6.5.7, Adobe Commerce 2.3.5 GraphQL-schema&#39;s |
| CIF Core-componenten | [Systeemvereisten](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| Projectarchetype AEM | [Systeemvereisten](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: september 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2022.09.20.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.09.20.00.zip) |
| CIF Core-componenten | 2.11.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.11.0) |
| CIF Venia Reference Site | 2022.09.02 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.09.02) |

### Wat is er nieuw? {#what-is-new-september}

* Auteurs kunnen productlijsten dynamisch verrijken met ervaringsfragmenten (bijvoorbeeld: een banner tussen productlijsten plaatsen)
* De component List ondersteunt gekoppelde product-/categoriepagina&#39;s om gerelateerde pagina&#39;s dynamisch weer te geven
* Ondersteuning voor peregrine 12.5-onderdelen
* Steun voor het laden van de prijs aan de clientzijde in productgummetje en carrousel

## Releasedatum: juli 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2022.08.02.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.08.02.00.zip) |

### Wat is er nieuw? {#what-is-new-july}

* Koppeling van AEM pagina&#39;s naar producten en categorieën via AEM pagina-eigenschappen plus overzicht in de cockpit van het product
  ![productcockpit page association](/help/assets/CIF/product_cockpit_page_association.png)

## Releasedatum: juni 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2022.07.05.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.07.05.00.zip) |
| CIF Core-componenten | 2.10.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) |
| CIF Venia Reference Site | 2022.07.04 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.07.04) |

### Wat is er nieuw? {#what-is-new-june}

* De verrijking van de productcatalogus steunt nu AEM pagina&#39;s, toelatend auteurs om pagina - productvereniging te beheren.

* Verschillende CIF Core-componentverbeteringen

### Bugfixes {#bug-fixes-june}

* Aanmeldingstoken toevoegen aan prijsophaalbewerkingen op de client

* Onjuiste pagina-component in gegevenslaag.

## Releasedatum: mei 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2022.05.31.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.05.31.00.zip) |
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
| CIF | 2022.04.28.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.04.28.00.zip) |
| CIF Core-componenten | 2.8.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.8.0) |
| CIF Venia Reference Site | 2022.04.28 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.04.28) |

### Wat is er nieuw? {#what-is-new-april}

* Snelle toegang tot productcockpit: eenvoudig toegang tot volledige gedetailleerde productinformatie met één klik in de Sites Editor

  ![Enable wishlist](/help/assets/CIF/enable-wishlist.png)

* Steun voor extra marketing commerciële componenten: De componenten kunnen worden gevormd om toe:voegen-aan-kart en toe:voegen-aan-verlanglijstvraag-aan-actie te tonen

  ![Snelkoppeling naar productcockpit in Sites-editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)

## Releasedatum: februari 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2022.02.24.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.02.24.00.zip) |
| CIF Core-componenten | 2.6.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) |
| CIF Venia Reference Site | 2022.02.24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.02.24) |

### Wat is er nieuw? {#what-is-new-march}

* Bèta: AEM CIF Search Core Component support Commerce LiveSearch
* Verbeterde SEO voor meerdere opslagscenario&#39;s: URL-indelingen voor PDP / PLP kunnen nu op archiefniveau worden geconfigureerd via de CIF Cloud Config-eigenschappen
* Productkiezer ondersteunt gefaseerde producten via de nieuwe filteroptie in de gebruikersinterface. Laat inhoudsartsen toe om het beheer van productinhoud voor te bereiden voor de aanstaande productlanceringen
* Vereenvoudigd CIF configuratiebeheer en foutafhandeling met de naam CIF Cloud Config in plaats van proxyURL te configureren
* Handmatige categorieselectie voor productlijst en carrouselcomponenten. Hiermee kunnen gebruikers van inhoud deze componenten gebruiken op inhoudspagina&#39;s, buiten de cataloguservaring

## Releasedatum: januari 2022

| Component | Versie | Details |
|:-------|:-----:|---------------------:|
| CIF | 2022.01.20.00 | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.01.20.00.zip) |
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
