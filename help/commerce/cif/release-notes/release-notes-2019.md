---
title: Opmerkingen bij de release AEM2021
description: Opmerkingen bij de release AEM2021
translation-type: tm+mt
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 7%

---

# GitHub-releaseoverzicht van het Commerce Integration Framework

## Releasedatum: november 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 0,7,1 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 0,6,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,6,2 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw?{#what-is-new-november}

* Auteurs kunnen productdetails en pagina&#39;s met productlijsten voorvertonen met producten/categorieën met de nieuwe optie &#39;Weergeven met product/categorie&#39; in de Sites-editor.

* Auteurs kunnen elementen labelen per product-SKU en naar productspecifieke elementen zoeken door SKU.

* Voeg couponondersteuning toe aan winkelwagentje of verwijder deze.

* Braintree betalingsondersteuning toegevoegd aan AEM winkel van Venia.

### Verbeterde {#what-is-improved-november}

* De categorie/de plukkers van het Product verbeterd om gespecificeerde de archiefmening van de Magento in een multi-store opstelling te respecteren.

* React-gebaseerde componenten beschikbaar als npm pakket. Dit staat ontwikkelaars toe om het pakket van Componenten van de Reactie als gebiedsdeel voor een nieuw project van de Reactie te gebruiken om aanpassing van bestaande componenten toe te staan of nieuwe React-based componenten te ontwikkelen.

* GraphQL-query-aanpassing vereenvoudigd. Dit staat ontwikkelaars toe om de kerncomponenten van CIF met minder code aan te passen.

## Releasedatum: Oktober 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 0,6,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 0,5,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,5,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw?{#what-is-new-october}

* Volledig bruikbare sjablonen voor de pagina met productdetails en de pagina met productlijsten. Auteurs kunnen nu nieuwe sjablonen maken en de productlijst en productdetailcomponenten naar deze sjablonen slepen en neerzetten. Naast het toevoegen van andere componenten, kunnen de auteurs de lay-out van deze malplaatjes nu veranderen, die hen onbeperkte vrijheid geven om verbazende ervaringen tot stand te brengen die marketing en handelsinhoud combineren.

* Alle auteurvriendelijke kern-componenten van CIF zijn verbeterd om [AEM Systeem van de Stijl](https://helpx.adobe.com/experience-manager/6-5/sites/authoring/using/style-system.html) te steunen. Er zijn voorbeeldstijlen beschikbaar voor de component met de productlijst.

* React-based cliënt-zijcomponenten voor rekeningsbeheer. Deze release ondersteunt de volgende functies: Aanmelden, Wachtwoord vergeten en Account maken.

### Verbeterde {#what-is-improved-october}

* De productdetails en de componenten van de productlijst zijn verbeterd om dummygegevens te tonen om auteurs van een voorproef van de lay-out te voorzien wanneer deze componenten op een malplaatje/een pagina worden geplaatst.

* De onderdelen Minicart en Afhandeling gebruiken nu React-haken voor een betere uitbreidbaarheid.

## Releasedatum: september 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 0,5,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 0,4,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,4,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw?{#what-is-new-september}

* Meerdere sjabloonfuncties waarmee auteurs specifieke productdetailpagina of productlijstpagina kunnen verrijken. Auteurs kunnen eenvoudig een aangepaste productdetailpagina of productlijstpagina maken en de product- of categoriekiezer gebruiken om de aangepaste pagina aan een of meer specifieke producten of categorieën toe te wijzen.

* Binding van meerdere catalogi zodat auteurs meerdere catalogi in de AEM productconsole kunnen binden. Auteurs kunnen de eigenschappen voor de catalogusbinding ook bewerken en weergeven nadat ze de binding hebben gemaakt.

* React-based cliënt-zijAfhandeling en MiniKart die GraphQL gebruiken om een volledige basis het winkelen reis te steunen.

* Afhandelingscomponent bevat adresformulieren, selectie van betalingen en selectie van verzendmethoden.

### Verbeterde {#what-is-improved-september}

* De componenten van de Teaser en van het Product Carousel steunen productvarianten.

## Releasedatum: augustus 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 0,4,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 0,3,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,3,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw?{#what-is-new-august}

* Het insluiten van de Schakelaar van CIF in Archetype CIF maakte facultatief om ontwikkelaars meer flexibiliteit te verstrekken.

* CIF-componenten losgekoppeld van &quot;Venia&quot;-specifieke CSS-stijlen, zodat ontwikkelaars naar keuze CSS-stijlen kunnen toepassen.

* Multistore/site eigenschap om gebruik van de Componenten van de Kern van CIF op veelvoudige AEM plaatsstructuren toe te staan en het toelaten van de onderliggende cliënt GraphQL implementatie om met verschillende Magento opslag/opslagmeningen te verbinden.

* GraphQL caching die voor bepaalde vragen GraphQL via HTTP GET wordt toegelaten om reactietijd te verminderen.

* Weergave van de productbeschrijving ingeschakeld in AEM Producten-console.

* De Teaser van de handel breidt de component van het Teaser WCM uit om auteurs toe te staan om CTA- gebieden aan een productdetailpagina of een pagina van de productlijst ook toe te voegen.

* Knop om auteurs toe te staan op een AEM pagina te plaatsen en een koppeling te maken naar een AEM pagina, productdetailpagina, productlijstpagina of een externe koppeling.

### Verbeterde {#what-is-improved-august}

* De de opslagconfiguratie van Magento werd bewogen van OSGi aan AEM console van het Product om de integratieopstelling auteur-vriendelijker te maken.

## Releasedatum: juli 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 0,3,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 0,2,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,2,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw?{#what-is-new-july}

* Eerste CIF Archetype om ontwikkelaars van verscheidene plaatsingsopties te voorzien: 1.Distributie AEM Venia storefront 2. Stel steigers voor een nieuw project 3 op. CIF-elementen gebruiken in een bestaand project

* Catalogusnavigatie op meerdere niveaus ter ondersteuning van navigatie door categorieën en subcategorieën.

* Paginering op categoriepagina&#39;s voor betere UX.

* Client-side rendering van prijskenmerken in de componenten Productdetails en Productlijst ter ondersteuning van rendering van dynamische kenmerken.

* Server-side productcarrousel om een lijst met aanbevolen producten in carrouselstijl weer te geven.

* Lijst met aanbevolen categorieën aan de serverzijde om een lijst met categorieën op een AEM pagina weer te geven.

### Verbeterde {#what-is-improved-july}

* Ondersteuning voor Magento 2.3.2 en foutoplossingen met betrekking tot de weergave van producteigenschappen in de productconsole.

## Releasedatum: juni 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF-aansluiting | 0,2,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF Core-componenten | 0,1,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |

### Wat is er nieuw?{#what-is-new-june}

* AEM B2C-winkel met de eerste mobiele Venia CSS-stijl, openingspagina, dynamische catalogusnavigatie via product- en categoriepagina&#39;s, productzoekpagina en de mogelijkheid om winkelwagentjes te gebruiken om handelsprojecten snel te starten en te versnellen.

* CIF-aansluiting en -ontwerpgereedschappen (Productconsole, Productkiezer en Categoriekiezer) waarmee auteurs ervaringen kunnen creëren in AEM met commerciële inhoud.

* Eerste versie van CIF Core Components compatible met Magento 2.3.1:
   * Productgegevens
   * Productlijst
   * Productteam
   * Navigatie
   * Zoeken in producten
   * Winkelwagentje (REST)

