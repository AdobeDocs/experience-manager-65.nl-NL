---
title: Dynamisch model aan Component Mapping voor SPAs
seo-title: Dynamisch model aan Component Mapping voor SPAs
description: Dit artikel beschrijft hoe het dynamische model aan componentenafbeelding in Javascript SPA SDK voor AEM voorkomt.
seo-description: Dit artikel beschrijft hoe het dynamische model aan componentenafbeelding in Javascript SPA SDK voor AEM voorkomt.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Dynamisch model aan Component Mapping voor SPAs{#dynamic-model-to-component-mapping-for-spas}

Dit document beschrijft hoe het dynamische model aan componentenafbeelding in Javascript SPA SDK voor AEM voorkomt.

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

## ComponentMapping-module {#componentmapping-module}

De `ComponentMapping` module wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan AEM middeltypes in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elke punten in het model bevatten een `:type` gebied dat een AEM middeltype blootstelt. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Gelieve te verwijzen naar het document van de Blauwdruk [van het](/help/sites-developing/spa-blueprint.md) KUUROORD voor meer informatie over modelontleding en de front-end componententoegang tot het model.

Zie ook het npm-pakket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen van één pagina die gebruikmaken van de Javascript SPA SDK voor AEM zijn modelgestuurd:

1. De front-end componenten registreren zich aan de Opslag van de Toewijzing van de [Component](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Dan herhaalt de [Container](/help/sites-developing/spa-blueprint.md#container), zodra voorzien van een model door de [ModelLeverancier](/help/sites-developing/spa-blueprint.md#the-model-provider), over zijn modelinhoud ( `:items`).

1. In het geval van een pagina, krijgen zijn kinderen ( `:children`) eerst een componentenklasse van de Toewijzing [van de](/help/sites-developing/spa-blueprint.md#componentmapping) Component en dan concretiseren het.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. De [ initialisatie `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) moet worden uitgevoerd zoals deze wordt vertegenwoordigd door de [initialisatiestroom](/help/sites-developing/spa-blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end [wortelContainer](/help/sites-developing/spa-blueprint.md#container) component van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![app_model_initialisatie](assets/app_model_initialization.png)

