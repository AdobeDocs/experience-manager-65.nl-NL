---
title: SPA Model Routing
seo-title: SPA Model Routing
description: Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.
seo-description: Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.
uuid: 93b4f85a-a240-42d4-95e2-e8b790df7723
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: d9f1e24e-51a9-4f28-b2cd-2e97aed63a24
translation-type: tm+mt
source-git-commit: 4ea1bad1fb76142be7f6d564ecf30ed85a6da694
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# SPA Model Routing{#spa-model-routing}

Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

## Project routeren {#project-routing}

App bezit het verpletteren en dan uitgevoerd door de ontwikkelaars van het projectfront. Dit document beschrijft het verpletteren specifiek voor het model dat door de server AEM is teruggekeerd. De gegevensstructuur van het paginamodel stelt URL van het onderliggende middel bloot. Het front-end project kan om het even welke douane of derdebibliotheek gebruiken die verpletterende functionaliteit verstrekt. Zodra een route een fragment van model verwacht, kan een vraag aan de `PageModelManager.getData()` functie worden gemaakt. Wanneer een modelroute is veranderd moet een gebeurtenis worden teweeggebracht om luisterbibliotheken zoals de Redacteur van de Pagina te waarschuwen.

## Architectuur {#architecture}

Voor een gedetailleerde beschrijving, gelieve te verwijzen naar de sectie [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) van het document van de Blauwdruk van het KUUROORD.

## ModelRouter {#modelrouter}

De API-functies van HTML5 History worden ingekapseld `ModelRouter` - indien ingeschakeld `pushState` en `replaceState` om te garanderen dat een bepaald fragment van het model vooraf wordt opgehaald en toegankelijk is. Vervolgens wordt de geregistreerde front-end component meegedeeld dat het model is gewijzigd.

## Handmatig versus automatisch model routeren {#manual-vs-automatic-model-routing}

Met de opdracht `ModelRouter` automatiseert u het ophalen van fragmenten van het model. Maar zoals elk geautomatiseerd gereedschap ook met beperkingen gepaard gaat. Indien nodig `ModelRouter` kan het worden onbruikbaar gemaakt of worden gevormd om wegen te negeren gebruikend meta-eigenschappen (zie de sectie van Eigenschappen van Meta van het document van de Component [van de Pagina van het](/help/sites-developing/spa-page-component.md) KUUROORD). De ontwikkelaars van het vooreind kunnen hun eigen model dan uitvoeren die laag verpletteren door te verzoeken om om het even welk bepaald fragment van model te laden gebruikend de `PageModelManager` `getData()` functie.

>[!NOTE]
>
>Momenteel illustreert het steekproefReact project van het Dagboek Wij.Retail van het Dagboek de geautomatiseerde benadering terwijl het Hoekproject handboek illustreert. Een semi-geautomatiseerde benadering zou ook een geldige gebruikscase zijn.

>[!CAUTION]
>
>De huidige versie van het model ondersteunt `ModelRouter` alleen het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van de entry-punten Sling Model. Het steunt niet het gebruik van Vanity URLs of aliassen.

## Routeringscontract {#routing-contract}

De huidige implementatie is gebaseerd op de veronderstelling dat het project van het KUUROORD de HTML5 Geschiedenis API voor het verpletteren aan de verschillende toepassingspagina&#39;s gebruikt.

### Configuratie {#configuration}

Het `ModelRouter` steunt het concept model dat verplettert aangezien het luistert naar `pushState` en `replaceState` vraag om modelfragmenten vooraf in te stellen. Intern activeert het het model `PageModelManager` om het model te laden dat aan een bepaalde URL beantwoordt en brengt een `cq-pagemodel-route-changed` gebeurtenis in brand die andere modules kunnen luisteren aan.

Dit gedrag wordt standaard automatisch ingeschakeld. Om het onbruikbaar te maken, zou SPA het volgende meta-bezit moeten teruggeven:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Merk op dat elke route van het KUUROORD aan een toegankelijk middel in AEM (b.v., &quot; `/content/mysite/mypage"`) zou moeten beantwoorden aangezien de `PageModelManager` automatisch zal proberen om het overeenkomstige paginamodel te laden zodra de route wordt geselecteerd. Alhoewel, indien nodig, kan het KUUROORD een &quot;bloklijst&quot;van routes ook bepalen die door `PageModelManager`: zouden moeten worden genegeerd:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
