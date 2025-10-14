---
title: Opmerkingen bij de release AEM Content en Commerce 2019
description: Opmerkingen bij de release Adobe Experience Manager Content en Commerce 2019.
exl-id: 7e61a75d-6b35-46ee-b88a-444c10b2708f
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 4%

---

# Commerce integration framework GitHub Release-overzicht

## Releasedatum: november 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 0,7,1 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 0,6,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,6,2 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw? {#what-is-new-november}

* Auteurs kunnen productdetails en pagina&#39;s met productlijsten voorvertonen met producten/categorieën met de nieuwe optie &#39;Weergeven met product/categorie&#39; in de Sites-editor.

* Auteurs kunnen elementen labelen per product-SKU en naar productspecifieke elementen zoeken door SKU.

* Voeg couponondersteuning toe aan winkelwagentje of verwijder deze.

* Betaalsteun voor Braintree toegevoegd aan AEM kant van de winkel van Venia.

### Verbeterde functies {#what-is-improved-november}

* Categorie-/productkiezers die zijn verbeterd om de opgegeven Adobe Commerce-winkelweergave te respecteren in een installatie in meerdere winkels.

* React-gebaseerde componenten zijn beschikbaar als npm pakket. Dit staat ontwikkelaars toe om het pakket van Componenten van de Reactie als gebiedsdeel voor een nieuw project van de Reactie te gebruiken om aanpassing van bestaande componenten toe te staan of nieuwe React-based componenten te ontwikkelen.

* Aanpassing van GraphQL-query is vereenvoudigd. Op deze manier kunnen ontwikkelaars CIF basiscomponenten aanpassen met minder code.

## Releasedatum: oktober 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 0,6,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 0,5,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,5,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw? {#what-is-new-october}

* Volledig bruikbare sjablonen voor de pagina met productdetails en de pagina met productlijsten. Auteurs kunnen nu sjablonen maken en de productlijst en productdetailcomponenten naar deze sjablonen slepen en neerzetten. Naast het toevoegen van andere componenten, kunnen de auteurs de lay-out van deze malplaatjes nu veranderen, die hen onbeperkte vrijheid geven om verbazende ervaringen tot stand te brengen die marketing en handelsinhoud combineren.

* Alle auteursvriendelijk CIF kern-componenten zijn verbeterd om [&#x200B; AEM het Systeem van de Stijl &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/siteandpage/style-system.html?lang=nl-NL) te steunen. Er zijn voorbeeldstijlen beschikbaar voor de component met de productlijst.

* React-based cliënt-zijcomponenten voor rekeningsbeheer. Deze release ondersteunt de volgende functies: Aanmelden, Wachtwoord vergeten en Account maken.

### Verbeterde functies {#what-is-improved-october}

* De productdetails en de componenten van de productlijst zijn verbeterd om dummygegevens te tonen om auteurs van een voorproef van de lay-out te voorzien wanneer deze componenten op een malplaatje/een pagina worden geplaatst.

* De onderdelen Minicart en Afhandeling gebruiken nu React-haken voor een betere uitbreidbaarheid.

## Releasedatum: september 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 0,5,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 0,4,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,4,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw? {#what-is-new-september}

* Met de functie voor meerdere sjablonen kunnen auteurs een specifieke productdetailpagina of productlijstpagina verrijken. Auteurs kunnen eenvoudig een aangepaste productdetailpagina of productlijstpagina maken en de product- of categoriekiezer gebruiken om de aangepaste pagina aan een bepaald product of een bepaalde categorie toe te wijzen.

* Binding van meerdere catalogi zodat auteurs meerdere catalogi in de AEM productconsole kunnen binden. Auteurs kunnen de eigenschappen voor de catalogusbinding ook bewerken en weergeven nadat ze de binding hebben gemaakt.

* React-based cliënt-zijAfhandeling en Mini Cart die GraphQL gebruiken om een volledige basis het winkelen reis te steunen.

* De component Uitchecken bevat adresformulieren, selectie van betalingen en selectie van verzendmethoden.

### Verbeterde functies {#what-is-improved-september}

* De componenten van de Teaser en van het Product Carousel steunen productvarianten.

## Releasedatum: augustus 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 0,4,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 0,3,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,3,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw? {#what-is-new-august}

* Het insluiten CIF Connector in CIF Archetype wordt facultatief gemaakt om ontwikkelaars meer flexibiliteit te verstrekken.

* CIF Componenten losgekoppeld van specifieke CSS-stijlen voor &quot;Venia&quot;, zodat ontwikkelaars naar keuze CSS-stijlen kunnen toepassen.

* Multistore/site functie om het gebruik van CIF Core Components op meerdere AEM sitestructuren toe te staan en de onderliggende GraphQL client-implementatie in staat te stellen verbinding te maken met verschillende Adobe Commerce store/store-weergaven.

* GraphQL caching is ingeschakeld voor bepaalde GraphQL query&#39;s via HTTP GET om de reactietijd te verminderen.

* De mening van de productbeschrijving wordt toegelaten in de console van de Producten van de AEM.

* Commerce Teaser breidt de WCM Teaser-component uit, zodat auteurs ook CTA-velden kunnen toevoegen aan een productdetailpagina of een productlijstpagina.

* Knop om auteurs toe te staan op een AEM pagina te plaatsen en een koppeling te maken naar een AEM pagina, productdetailpagina, productlijstpagina of een externe koppeling.

### Verbeterde functies {#what-is-improved-august}

* Adobe Commerce store configuration bewogen van OSGi aan de console van het Product van het AEM om de integratieopstelling te maken auteur-vriendelijker.

## Releasedatum: juli 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 0,3,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 0,2,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Archetype | 0,2,0 | [Releaseopmerkingen](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Wat is er nieuw? {#what-is-new-july}

* Eerste CIF Archetype om ontwikkelaars verschillende implementatieopties te bieden: 1.Implementeer AEM Venia storefront 2. Stel steigers voor een nieuw project 3 op. CIF gebruiken in een bestaand project

* Catalogusnavigatie op meerdere niveaus ter ondersteuning van navigatie door categorieën en subcategorieën.

* Paginering op categoriepagina&#39;s voor betere UX.

* Client-side rendering van prijskenmerken in de componenten Productdetails en Productlijst ter ondersteuning van rendering van dynamische kenmerken.

* Server-side productcarrousel om een lijst met aanbevolen producten in carrouselstijl weer te geven.

* Lijst met aanbevolen categorieën aan de serverzijde om een lijst met categorieën op een AEM pagina weer te geven.

### Verbeterde functies {#what-is-improved-july}

* Ondersteuning voor Adobe Commerce 2.3.2 en foutoplossingen voor de weergave van producteigenschappen in de productconsole.

## Releasedatum: juni 2019

| GitHub | Versie | Gedetailleerde opmerkingen bij de release |
|:-------|:-----:|---------------------:|
| CIF | 0,2,0 | [Releaseopmerkingen](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF kerncomponenten | 0,1,0 | [Releaseopmerkingen](https://github.com/adobe/aem-core-cif-components/releases) |

### Wat is er nieuw? {#what-is-new-june}

* AEM B2C-winkel met de eerste mobiele Venia CSS-stijl, openingspagina, dynamische catalogusnavigatie via product- en categoriepagina&#39;s, productzoekpagina en de mogelijkheid om winkelwagentjes te gebruiken om handelsprojecten snel te starten en te versnellen.

* CIF Connector- en ontwerpgereedschappen (Productconsole, Productkiezer en Categoriekiezer) om auteurs in staat te stellen ervaringen in AEM met commerciële inhoud te maken.

* Eerste versie van CIF Core Components compatible met Adobe Commerce 2.3.1:
   * Productgegevens
   * Productlijst
   * Productteam
   * Navigatie
   * Zoeken in producten
   * Winkelwagentje (REST)
