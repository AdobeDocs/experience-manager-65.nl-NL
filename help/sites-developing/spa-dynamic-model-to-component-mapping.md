---
title: Dynamisch model naar componenttoewijzing voor SPA
description: Leer hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor Adobe Experience Manager voorkomt.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
exl-id: 5b2ccac0-bf1d-4f06-8743-7fce6fb68378
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Dynamisch model naar componenttoewijzing voor SPA{#dynamic-model-to-component-mapping-for-spas}

In dit document wordt beschreven hoe het dynamische model wordt toegewezen aan componenttoewijzing in de JavaScript SPA SDK voor Adobe Experience Manager (AEM).

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA op kader-gebaseerde cliënt-zijteruggeven (bijvoorbeeld, Reageren of Angular) vereisen.

## ComponentMapping-module {#componentmapping-module}

De `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan AEM middeltypes in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elk onderdeel in het model bevat een `:type` veld dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Zie [SPA](/help/sites-developing/spa-blueprint.md) voor meer informatie over modelontleding en de front-end componententoegang tot het model.

Zie ook het npm-pakket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen met één pagina die de JavaScript SPA SDK voor AEM gebruiken, zijn op modellen gebaseerd:

1. Voorste-end componenten registreren zich aan [Opslag voor componenttoewijzing](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Vervolgens worden de [Container](/help/sites-developing/spa-blueprint.md#container), zodra het door de [Modelleverancier](/help/sites-developing/spa-blueprint.md#the-model-provider), herhaalt de modelinhoud ( `:items`).

1. Als er een pagina is, zijn onderliggende elementen ( `:children`) krijgt eerst een componentklasse van de [Componenttoewijzing](/help/sites-developing/spa-blueprint.md#componentmapping) en instantiëren.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. De [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) moet worden geïnitialiseerd als vertegenwoordigd door de [initialisatiestroom](/help/sites-developing/spa-blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [Container](/help/sites-developing/spa-blueprint.md#container) van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![app_model_initialisatie](assets/app_model_initialization.png)
