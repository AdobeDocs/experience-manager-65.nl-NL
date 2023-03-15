---
title: Dynamisch model naar componenttoewijzing voor SPA
seo-title: Dynamic Model to Component Mapping for SPAs
description: In dit artikel wordt beschreven hoe het dynamische model naar componenttoewijzing wordt uitgevoerd in de Javascript SPA SDK voor AEM.
seo-description: This article describes how the dynamic model to component mapping occurs in the Javascript SPA SDK for AEM.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
exl-id: 5b2ccac0-bf1d-4f06-8743-7fce6fb68378
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Dynamisch model naar componenttoewijzing voor SPA{#dynamic-model-to-component-mapping-for-spas}

In dit document wordt beschreven hoe het dynamische model naar componenttoewijzing wordt uitgevoerd in de Javascript SPA SDK voor AEM.

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA kader gebaseerde cliënt-zijteruggeven (b.v. Reageren of Angular) vereisen.

## ComponentMapping-module {#componentmapping-module}

De `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan AEM middeltypes in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elk onderdeel in het model bevat een `:type` veld dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Raadpleeg de [SPA](/help/sites-developing/spa-blueprint.md) document voor meer informatie over modelontleding en de front-end componententoegang tot het model.

Zie ook het npm-pakket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen met één pagina die gebruikmaken van de Javascript SPA SDK voor AEM, worden modelgestuurd:

1. Voorste-end componenten registreren zich aan [Opslag voor componenttoewijzing](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Vervolgens worden de [Container](/help/sites-developing/spa-blueprint.md#container), zodra het door de [Modelleverancier](/help/sites-developing/spa-blueprint.md#the-model-provider), herhaalt de modelinhoud ( `:items`).

1. In het geval van een pagina, de onderliggende `:children`) krijgt eerst een componentklasse van de [Componenttoewijzing](/help/sites-developing/spa-blueprint.md#componentmapping) en instantiëren.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [ `ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. De [ `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) moet worden geïnitialiseerd als vertegenwoordigd door de [initialisatiestroom](/help/sites-developing/spa-blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [Container](/help/sites-developing/spa-blueprint.md#container) van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![app_model_initialisatie](assets/app_model_initialization.png)
