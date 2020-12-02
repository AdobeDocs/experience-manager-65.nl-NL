---
title: SPA
seo-title: SPA
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


# SPA Model Routering{#spa-model-routing}

Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.

>[!NOTE]
>
>De SPA Editor is de aanbevolen oplossing voor projecten die SPA op raamwerk gebaseerde renderen aan de clientzijde vereisen (bijvoorbeeld Reageren of Hoekig).

## Projectroutering {#project-routing}

App bezit het verpletteren en dan uitgevoerd door de ontwikkelaars van het projectfront. Dit document beschrijft specifiek het verpletteren voor het model dat door de AEM server is teruggekeerd. De gegevensstructuur van het paginamodel stelt URL van het onderliggende middel bloot. Het front-end project kan om het even welke douane of derdebibliotheek gebruiken die verpletterende functionaliteit verstrekt. Zodra een route een fragment van model verwacht, kan een vraag aan de `PageModelManager.getData()` functie worden gemaakt. Wanneer een modelroute is veranderd moet een gebeurtenis worden teweeggebracht om luisterbibliotheken zoals de Redacteur van de Pagina te waarschuwen.

## Architectuur {#architecture}

Voor een gedetailleerde beschrijving raadpleegt u de sectie [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) van het document SPA blauwdruk.

## ModelRouter {#modelrouter}

`ModelRouter` - indien ingeschakeld - kapselt de API-functies `pushState` en `replaceState` van de HTML5 History in om ervoor te zorgen dat een bepaald fragment van het model vooraf wordt opgehaald en toegankelijk is. Vervolgens wordt de geregistreerde front-end component meegedeeld dat het model is gewijzigd.

## Handmatig versus automatisch model dat {#manual-vs-automatic-model-routing}

Met `ModelRouter` worden fragmenten van het model automatisch opgehaald. Maar zoals elk geautomatiseerd gereedschap ook met beperkingen gepaard gaat. Indien nodig kan `ModelRouter` worden uitgeschakeld of geconfigureerd om paden te negeren met behulp van meta-eigenschappen (zie de sectie Meta-eigenschappen van het document [SPA Paginacomponent](/help/sites-developing/spa-page-component.md)). De ontwikkelaars van het vooreind kunnen hun eigen model dan uitvoeren die laag verpletteren door `PageModelManager` te verzoeken om om het even welk bepaald fragment van model te laden gebruikend de `getData()` functie.

>[!NOTE]
>
>Momenteel illustreert het steekproefReact project van het Dagboek Wij.Retail van het Dagboek de geautomatiseerde benadering terwijl het Hoekproject handboek illustreert. Een semi-geautomatiseerde benadering zou ook een geldige gebruikscase zijn.

>[!CAUTION]
>
>De huidige versie van `ModelRouter` steunt slechts het gebruik van URLs die aan de daadwerkelijke middelweg van de Invoerpunten van het Sling Model richt. Het steunt niet het gebruik van Vanity URLs of aliassen.

## Routeringscontract {#routing-contract}

De huidige implementatie is gebaseerd op de veronderstelling dat het SPA project de HTML5 History API voor het verpletteren aan de verschillende toepassingspagina&#39;s gebruikt.

### Configuratie {#configuration}

`ModelRouter` steunt het concept model verpletterend aangezien het `pushState` en `replaceState` vraag aan prefetch modelfragmenten luistert. Intern activeert het `PageModelManager` om het model te laden dat aan een bepaalde URL beantwoordt en een `cq-pagemodel-route-changed` gebeurtenis in brand steken die andere modules kunnen luisteren aan.

Dit gedrag wordt standaard automatisch ingeschakeld. Om het onbruikbaar te maken, zou de SPA het volgende meta-bezit moeten teruggeven:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Merk op dat elke route van de SPA aan een toegankelijke bron in AEM (b.v., &quot; `/content/mysite/mypage"`) zou moeten beantwoorden aangezien `PageModelManager` automatisch zal proberen om het overeenkomstige paginamodel te laden zodra de route wordt geselecteerd. Desondanks, indien nodig, kan de SPA een &quot;lijst van afgewezen personen&quot;van routes ook bepalen die door `PageModelManager` moeten worden genegeerd:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
