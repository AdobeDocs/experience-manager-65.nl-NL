---
title: SPA
seo-title: SPA Page Component
description: In een SPA biedt de paginacomponent niet de HTML-elementen van de onderliggende componenten, maar delegeert deze aan het SPA. In dit document wordt uitgelegd hoe de paginacomponent van een SPA hierdoor uniek wordt.
seo-description: In an SPA the page component doesn't provide the HTML elements of its child components, but instead delegates this to the SPA framework. This document explains how this makes the page component of an SPA unique.
uuid: d444527a-e883-4873-a55b-c2bc140d8d7f
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 6329301c-1a26-4a46-99ae-1b7cc15b08be
docset: aem65
exl-id: 0e9e2350-67ef-45c3-991f-6c1cd98fe93d
source-git-commit: 17c198c744111753ffffcc0758f98859524c964e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# SPA{#spa-page-component}

In een SPA biedt de paginacomponent niet de HTML-elementen van de onderliggende componenten, maar delegeert deze aan het SPA. In dit document wordt uitgelegd hoe de paginacomponent van een SPA hierdoor uniek wordt.

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA kader gebaseerde cliënt-zijteruggeven (b.v. Reageren of Angular) vereisen.

## Inleiding {#introduction}

De paginacomponent voor een SPA verstrekt niet de elementen van HTML van zijn kindcomponenten via een JSP of HTML- dossier en middelvoorwerpen. Deze bewerking wordt gedelegeerd aan het SPA. De representatie van onderliggende componenten wordt opgehaald als een JSON-gegevensstructuur (dat wil zeggen het model). De SPA componenten worden vervolgens aan de pagina toegevoegd volgens het opgegeven JSON-model. De oorspronkelijke compositie van de hoofdtekst van de paginacomponent verschilt daarom van de vooraf weergegeven HTML-tegenhangers.

## Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een meegeleverde [ `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) module. De SPA moet communiceren met de module `PageModelManager` wanneer deze wordt geïnitialiseerd om het eerste paginamodel op te halen en zich te registreren voor modelupdates - meestal geproduceerd wanneer de auteur de pagina bewerkt via de Pagina-editor. `PageModelManager` is toegankelijk door SPA project als npm pakket. Als tolk tussen AEM en de SPA is `PageModelManager` bedoeld om de SPA te begeleiden.

Als u het schrijven van de pagina wilt toestaan, moet een clientbibliotheek met de naam `cq.authoring.pagemodel.messaging` worden toegevoegd voor een communicatiekanaal tussen de SPA en de pagina-editor. Als de SPA paginacomponent overerft van de pagina-component wcm/core, zijn er de volgende opties om de clientbibliotheekcategorie `cq.authoring.pagemodel.messaging` beschikbaar te maken:

* Als de sjabloon bewerkbaar is, voegt u de categorie van de clientbibliotheek toe aan het paginabeleid.
* Voeg de categorie van de cliëntbibliotheek toe gebruikend `customfooterlibs.html` van de paginacomponent.

Vergeet niet de opname van de categorie `cq.authoring.pagemodel.messaging` te beperken tot de context van de pagina-editor.

## Gegevenstype communicatie {#communication-data-type}

Het gegevenstype voor communicatie wordt ingesteld als een HTML-element binnen de component AEM pagina met het kenmerk `data-cq-datatype`. Wanneer het gegevenstype van communicatiegegevens is ingesteld op JSON, bereiken de aanvragen van de GET de eindpunten van het verzendmodel van een component. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. In de bibliotheek Paginamodel wordt vervolgens een waarschuwing voor de SPA van updates weergegeven.

**SPA pagina-component -`body.html`**

```
<div id="page"></div>
```

Naast goede praktijken om de generatie van DOM niet uit te stellen, vereist het SPA kader dat de manuscripten aan het eind van het lichaam worden toegevoegd.

**SPA pagina-component -`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

De eigenschappen van de meta-bron die de SPA inhoud beschrijven:

**SPA pagina-component -`customheaderlibs.html`**

```
<meta property="cq:datatype" data-sly-test="${wcmmode.edit || wcmmode.preview}" content="JSON"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.edit}" content="edit"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.preview}" content="preview"/>
<meta property="cq:pagemodel_root_url" data-sly-use.page="com.adobe.cq.sample.spa.journal.models.AppPage" content="${page.rootUrl}"/>
<sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
    <sly data-sly-call="${clientlib.css @ categories='we-retail-journal-react'}"/>
</sly>
```

>[!NOTE]
>
>De standaardmodelkiezer wordt statisch ingesteld bij het aanvragen van de representatie van een component in het verkoopmodel.

## Eigenschappen van meta {#meta-properties}

* `cq:wcmmode`: WCM-modus van de editors (bijvoorbeeld pagina, sjabloon)
* `cq:pagemodel_root_url`: URL van het basismodel van de app. Cruciaal bij directe toegang tot een onderliggende pagina, aangezien het onderliggende paginamodel een fragment is van het basismodel van de app. ` [PageModelManager](/help/sites-developing/spa-page-component.md)` stelt dan systematisch het aanvankelijke model van de toepassing opnieuw samen zoals ingaand de toepassing van zijn wortelingangspunt.

* `cq:pagemodel_router`: De  ` [ModelRouter](/help/sites-developing/spa-routing.md)`   `PageModelManager` bibliotheek in- of uitschakelen

* `cq:pagemodel_route_filters`: Door komma&#39;s gescheiden lijsten of reguliere expressies om routes te bieden die de gebruiker  ` [ModelRouter](/help/sites-developing/spa-routing.md)` moet negeren.

>[!CAUTION]
>
>Dit document gebruikt de app We.Retail Journal alleen voor demonstratiedoeleinden. Het mag niet worden gebruikt voor projectwerkzaamheden.
>
>Elk AEM project zou hefboomwerking [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html), dat SPA projecten gebruikend React of Angular steunt en hefboomwerkingen de SPA SDK.Alle SPA projecten op AEM zouden op het Maven Archetype voor SPA Starter Kit moeten worden gebaseerd.

## Overlaysynchronisatie van paginaeditor {#page-editor-overlay-synchronization}

De synchronisatie van de overlays wordt gegarandeerd door dezelfde Mutation Observer die door de categorie `cq.authoring.page` wordt geboden.

## Sling Model JSON Geëxporteerde structuurconfiguratie {#sling-model-json-exported-structure-configuration}

Wanneer de verpletterende mogelijkheden worden toegelaten, is de veronderstelling dat de uitvoer JSON van de SPA de verschillende routes van de toepassing dankzij de uitvoer JSON van de AEM navigatiecomponent bevat. De JSON-uitvoer van de AEM navigatiecomponent kan via de volgende twee eigenschappen worden geconfigureerd in het inhoudsbeleid voor SPA basispagina:

* `structureDepth`: Aantal dat overeenkomt met de diepte van de geëxporteerde structuur
* `structurePatterns`: Regex van array van regexes die overeenkomt met de pagina die geëxporteerd moet worden

Dit kan in de SPA steekproefinhoud in `/conf/we-retail-journal/react/settings/wcm/policies/we-retail-journal/react/components/structure/page/root` worden getoond.
