---
title: Dynamisch model aan Component Mapping voor SPAs
description: Leer hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor Adobe Experience Manager voorkomt.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
exl-id: 5b2ccac0-bf1d-4f06-8743-7fce6fb68378
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
index: false
source-git-commit: 1509ca884e2f9eb931fc7cd416801957459cc4a0
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Dynamisch model aan Component Mapping voor SPAs{#dynamic-model-to-component-mapping-for-spas}

Dit document beschrijft hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor Adobe Experience Manager (AEM) voorkomt.

{{ue-over-spa}}

## ComponentMapping-module {#componentmapping-module}

De module `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan de middeltypes van AEM in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elke item in het model bevat een veld `:type` dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Zie [ Vervaging van het KUUROORD ](/help/sites-developing/spa-blueprint.md) voor meer informatie over model het ontleden en de front-end componententoegang tot het model.

Zie ook het npm pakket: [ https://www.npmjs.com/package/@adobe/aem-spa-component-mapping ](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen op één pagina die gebruikmaken van de JavaScript SPA SDK voor AEM, zijn gebaseerd op modellen:

1. De front-end componenten registreren zich aan de [ Opslag van de Afbeelding van de Component ](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Dan de [ Container ](/help/sites-developing/spa-blueprint.md#container), eens voorzien van een model door de [ ModelLeverancier ](/help/sites-developing/spa-blueprint.md#the-model-provider), herhaalt over zijn modelinhoud ( `:items`).

1. Als er een pagina is, krijgen zijn kinderen ( `:children`) eerst een componentenklasse van de [ Afbeelding van de Component ](/help/sites-developing/spa-blueprint.md#componentmapping) en dan het concretiseren.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) moet worden geïnitialiseerd zoals vertegenwoordigd door de [ initialiseringsstroom ](/help/sites-developing/spa-blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [ component van de Container ](/help/sites-developing/spa-blueprint.md#container) van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![ app_model_initialization ](assets/app_model_initialization.png)
