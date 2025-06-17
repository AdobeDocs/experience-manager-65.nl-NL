---
title: SPA Model Routing
description: Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
exl-id: eaef65ec-2e4d-490f-8158-d48d738e3409
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
index: false
source-git-commit: 1509ca884e2f9eb931fc7cd416801957459cc4a0
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# SPA Model Routing{#spa-model-routing}

Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.

{{ue-over-spa}}

## Project routeren {#project-routing}

App bezit het verpletteren en dan uitgevoerd door de ontwikkelaars van het projectfront. Dit document beschrijft specifiek het verpletteren voor het model dat door de server van AEM is teruggekeerd. De gegevensstructuur van het paginamodel stelt URL van het onderliggende middel bloot. Het front-end project kan om het even welke douane of derdebibliotheek gebruiken die verpletterende functionaliteit verstrekt. Zodra een route een fragment van model verwacht, kan een vraag aan de `PageModelManager.getData()` functie worden gemaakt. Wanneer een modelroute is veranderd moet een gebeurtenis worden teweeggebracht om luisterbibliotheken zoals de Redacteur van de Pagina te waarschuwen.

## Architectuur {#architecture}

Voor een gedetailleerde beschrijving, zie de [&#128279;](/help/sites-developing/spa-blueprint.md#pagemodelmanager) sectie PageModelManager van het document van de Vervaging van het KUUROORD.

## ModelRouter {#modelrouter}

`ModelRouter` - indien ingeschakeld - kapselt de HTML5 History API-functies `pushState` en `replaceState` in om te garanderen dat een bepaald fragment van het model vooraf wordt opgehaald en toegankelijk is. Vervolgens wordt de geregistreerde front-end component meegedeeld dat het model is gewijzigd.

## Handmatig versus automatisch model routeren {#manual-vs-automatic-model-routing}

Met `ModelRouter` worden fragmenten van het model automatisch opgehaald. Maar zoals elk geautomatiseerd gereedschap ook met beperkingen gepaard gaat. Wanneer nodig `ModelRouter` kan worden onbruikbaar gemaakt of worden gevormd om wegen te negeren gebruikend meta-eigenschappen (zie de sectie van Eigenschappen van Meta van het [ document van de Component van de Pagina van het KUUROORD ](/help/sites-developing/spa-page-component.md)). Ontwikkelaars aan de voorzijde kunnen vervolgens hun eigen model voor het routeren van lagen implementeren door `PageModelManager` te vragen een bepaald fragment van een model te laden met de functie `getData()` .

>[!NOTE]
>
>Het {[&#128279;](https://github.com/adobe/aem-sample-we-retail-journal) steekproefReageer project van het Dagboek van 0} Wij.Retail illustreert de geautomatiseerde benadering terwijl het project van Angular het handboek illustreert.  Een semi-geautomatiseerde benadering zou ook een geldige gebruikscase zijn.

>[!CAUTION]
>
>De huidige versie van de `ModelRouter` ondersteunt alleen het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van de entry-punten Sling Model. Het ondersteunt het gebruik van URL&#39;s of aliassen van het type Vanity niet.

## Routeringscontract {#routing-contract}

De huidige implementatie is gebaseerd op de veronderstelling dat het project van het KUUROORD HTML5 Geschiedenis API voor het verpletteren aan de verschillende toepassingspagina&#39;s gebruikt.

### Configuratie {#configuration}

`ModelRouter` steunt het concept model die verplettert aangezien het op `pushState` en `replaceState` vraag aan vooraf ingestelde modelfragmenten luistert. Intern activeert het `PageModelManager` om het model te laden dat overeenkomt met een opgegeven URL en wordt een `cq-pagemodel-route-changed` -gebeurtenis geactiveerd waarnaar andere modules kunnen luisteren.

Dit gedrag wordt standaard automatisch ingeschakeld. Om het onbruikbaar te maken, zou SPA het volgende meta-bezit moeten teruggeven:

```
<meta property="cq:pagemodel_router" content="disabled"\>
```

Merk op dat elke route van het KUUROORD met een toegankelijke middel in AEM (bijvoorbeeld, &quot; `/content/mysite/mypage"`) zou moeten beantwoorden aangezien `PageModelManager` automatisch zal proberen om het overeenkomstige paginamodel te laden zodra de route wordt geselecteerd. Alhoewel, indien nodig, kan het KUUROORD een &quot;lijst van gewezen personen&quot;van routes ook bepalen die door `PageModelManager` zouden moeten worden genegeerd:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
