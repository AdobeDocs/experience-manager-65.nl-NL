---
title: SPA
description: In een SPA verschaft de paginacomponent niet de HTML-elementen van de onderliggende componenten, maar delegeert deze aan het SPA. In dit document wordt uitgelegd hoe de paginacomponent van een SPA hierdoor uniek wordt.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: 0e9e2350-67ef-45c3-991f-6c1cd98fe93d
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# SPA{#spa-page-component}

In een SPA verschaft de paginacomponent niet de HTML-elementen van de onderliggende componenten, maar delegeert deze aan het SPA. In dit document wordt uitgelegd hoe de paginacomponent van een SPA hierdoor uniek wordt.

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA op kader-gebaseerde cliënt-zijteruggeven (bijvoorbeeld, Reageren of Angular) vereisen.

## Inleiding {#introduction}

De paginacomponent voor een SPA verstrekt niet de HTML elementen van zijn kindcomponenten via een JSP of HTML- dossier en middelvoorwerpen. Deze bewerking wordt gedelegeerd aan het SPA. De representatie van onderliggende componenten wordt opgehaald als een JSON-gegevensstructuur (het model). De SPA componenten worden vervolgens aan de pagina toegevoegd volgens het opgegeven JSON-model. Als zodanig verschilt de oorspronkelijke compositie van de hoofdtekst van de paginacomponent van de bovenliggende HTML.

## Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een opgegeven [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) -module. De SPA moet met de `PageModelManager` wanneer deze wordt geïnitialiseerd om het eerste paginamodel op te halen en zich te registreren voor modelupdates, die meestal worden gemaakt wanneer de auteur de pagina bewerkt via de Pagina-editor. De `PageModelManager` is toegankelijk via SPA project als een npm-pakket. Als tolk tussen AEM en de SPA `PageModelManager` is bedoeld om de SPA te vergezellen.

Als u het schrijven van de pagina wilt toestaan, wordt een clientbibliotheek met de naam `cq.authoring.pagemodel.messaging` moet worden toegevoegd om een communicatiekanaal tussen de SPA en de pagina-editor te bieden. Als de SPA paginacomponent overerft van de pagina-component wcm/core, zijn er de volgende opties om de `cq.authoring.pagemodel.messaging` beschikbare categorie voor clientbibliotheek:

* Als de sjabloon bewerkbaar is, voegt u de categorie van de clientbibliotheek toe aan het paginabeleid.
* Voeg de categorie van de cliëntbibliotheek toe gebruikend `customfooterlibs.html` van de pagina-component.

Vergeet niet de opname van de `cq.authoring.pagemodel.messaging` in de context van de pagina-editor.

## Gegevenstype communicatie {#communication-data-type}

Het gegevenstype van de communicatie wordt ingesteld als een HTML-element binnen de component AEM pagina met behulp van `data-cq-datatype` kenmerk. Wanneer het gegevenstype van communicatiegegevens is ingesteld op JSON, bereiken de aanvragen van de GET de eindpunten van het verzendmodel van een component. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. In de bibliotheek Paginamodel wordt vervolgens een waarschuwing voor de SPA van updates weergegeven.

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
* `cq:pagemodel_root_url`: URL van het hoofdmodel van de app. Cruciaal bij directe toegang tot een onderliggende pagina, aangezien het onderliggende paginamodel een fragment is van het basismodel van de app. De ` [PageModelManager](/help/sites-developing/spa-page-component.md)` vervolgens wordt het oorspronkelijke toepassingsmodel systematisch opnieuw samengesteld zodat de toepassing wordt ingevoerd vanaf het beginpunt van de toepassing.

* `cq:pagemodel_router`: Schakel het dialoogvenster ` [ModelRouter](/help/sites-developing/spa-routing.md)` van de `PageModelManager` bibliotheek

* `cq:pagemodel_route_filters`: Door komma&#39;s gescheiden lijst of reguliere expressies om routes te bieden voor de ` [ModelRouter](/help/sites-developing/spa-routing.md)` moet worden genegeerd.

>[!CAUTION]
>
>Dit document gebruikt de app We.Retail Journal alleen voor demonstratiedoeleinden. Niet gebruiken voor projectwerk.
>
>Voor elk AEM project moet het [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html), die ondersteuning biedt voor SPA projecten die gebruikmaken van React of Angular en de SPA SDK gebruiken. Alle SPA projecten op AEM moeten gebaseerd zijn op het Maven Archetype voor SPA Starter Kit.

## Overlaysynchronisatie van paginaeditor {#page-editor-overlay-synchronization}

De synchronisatie van de overlays wordt gegarandeerd door dezelfde Mutation Observer die door de `cq.authoring.page` categorie.

## Sling Model JSON Geëxporteerde structuurconfiguratie {#sling-model-json-exported-structure-configuration}

Wanneer de verpletterende mogelijkheden worden toegelaten, is de veronderstelling dat de uitvoer JSON van de SPA de verschillende routes van de toepassing dankzij de uitvoer JSON van de AEM navigatiecomponent bevat. De JSON-uitvoer van de AEM navigatiecomponent kan via de volgende twee eigenschappen worden geconfigureerd in het inhoudsbeleid voor SPA basispagina:

* `structureDepth`: Nummer dat overeenkomt met de diepte van de geëxporteerde structuur
* `structurePatterns`: Regex van array van regexes die overeenkomt met de pagina die geëxporteerd moet worden

Dit kan worden weergegeven in de inhoud van het SPA monster in `/conf/we-retail-journal/react/settings/wcm/policies/we-retail-journal/react/components/structure/page/root`.
