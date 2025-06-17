---
title: SPA-pagina-component
description: In een KUUROORD verstrekt de paginacomponent niet de elementen van HTML van zijn kindcomponenten, maar in plaats daarvan delegeert dit aan het kader van het KUUROORD. Dit document verklaart hoe dit tot de paginacomponent van een SPA uniek maakt.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: 0e9e2350-67ef-45c3-991f-6c1cd98fe93d
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
index: false
source-git-commit: 1509ca884e2f9eb931fc7cd416801957459cc4a0
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---


# SPA-pagina-component{#spa-page-component}

In een KUUROORD verstrekt de paginacomponent niet de elementen van HTML van zijn kindcomponenten, maar in plaats daarvan delegeert dit aan het kader van het KUUROORD. Dit document verklaart hoe dit tot de paginacomponent van een SPA uniek maakt.

{{ue-over-spa}}

## Inleiding {#introduction}

De paginacomponent voor een SPA verstrekt niet de elementen van HTML van zijn kindcomponenten via een JSP of HTML- dossier en middelvoorwerpen. Deze verrichting wordt gedelegeerd aan het kader van het KUUROORD. De representatie van onderliggende componenten wordt opgehaald als een JSON-gegevensstructuur (het model). De componenten van het KUUROORD worden dan toegevoegd aan de pagina volgens het verstrekte model JSON. Als zodanig verschilt de oorspronkelijke compositie van de hoofdtekst van de paginacomponent van de bovenliggende HTML-component.

## Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een opgegeven module [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) . Het SPA moet met de `PageModelManager` module in wisselwerking staan wanneer het initialiseert om het aanvankelijke paginamodel en register voor modelupdates te halen - meestal geproduceerd wanneer de auteur de pagina via de Redacteur van de Pagina uitgeeft. `PageModelManager` is toegankelijk door het project van het KUUUROORD als npm pakket. Als tolk tussen AEM en de SPA is de `PageModelManager` bedoeld om de SPA te begeleiden.

Om de pagina toe te staan om worden authored, moet een cliëntbibliotheek genoemd `cq.authoring.pagemodel.messaging` worden toegevoegd om een communicatiekanaal tussen SPA en de paginaredacteur te verstrekken. Als de de paginacomponent van het KUUROORD van de pagina wcm/kerncomponent erft, zijn er de volgende opties om de `cq.authoring.pagemodel.messaging` categorie van de cliëntbibliotheek beschikbaar te maken:

* Als de sjabloon bewerkbaar is, voegt u de categorie van de clientbibliotheek toe aan het paginabeleid.
* Voeg de categorie van de cliëntbibliotheek toe gebruikend `customfooterlibs.html` van de paginacomponent.

Vergeet niet de opname van de categorie `cq.authoring.pagemodel.messaging` te beperken tot de context van de pagina-editor.

## Gegevenstype communicatie {#communication-data-type}

Het gegevenstype voor communicatie wordt ingesteld als een HTML-element binnen de component AEM Page met het kenmerk `data-cq-datatype` . Wanneer het gegevenstype voor communicatie is ingesteld op JSON, bereiken de GET-aanvragen de eindpunten van het model voor het splitsen van een component. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. De bibliotheek van het Model van de Pagina waarschuwt dan het KUUROORD van updates.

**SPA Page Component -`body.html`**

```
<div id="page"></div>
```

Naast het zijn goede praktijken om de generatie van DOM niet uit te stellen, vereist het kader van het KUUROORD dat de manuscripten aan het eind van het lichaam worden toegevoegd.

**Component van de Pagina van het KUUROORD -`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

De eigenschappen van het meta-middel die de inhoud van het KUUROORD beschrijven:

**SPA Page Component -`customheaderlibs.html`**

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
* `cq:pagemodel_root_url`: URL van het basismodel van de app. Cruciaal bij directe toegang tot een onderliggende pagina, aangezien het onderliggende paginamodel een fragment is van het basismodel van de app. Vervolgens stelt ` [PageModelManager](/help/sites-developing/spa-page-component.md)` het oorspronkelijke toepassingsmodel systematisch opnieuw samen als het invoeren van de toepassing vanaf het hoofdinvoerpunt.

* `cq:pagemodel_router`: de ` [ModelRouter](/help/sites-developing/spa-routing.md)` van de `PageModelManager` bibliotheek in- of uitschakelen

* `cq:pagemodel_route_filters`: een door komma&#39;s gescheiden lijst of reguliere expressies om routes te bieden die de ` [ModelRouter](/help/sites-developing/spa-routing.md)` moet negeren.

>[!CAUTION]
>
>Dit document gebruikt de app We.Retail Journal alleen voor demonstratiedoeleinden. Niet gebruiken voor projectwerk.
>
>Om het even welk project van AEM zou het [ Archetype van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat de projecten van het KUUROORD gebruikend React of Angular steunt en het KUUROORD SDK.Alle projecten van het KUUROORD op AEM zouden moeten worden gebaseerd op het Maven Archetype voor Kit van de Aanzet van het KUUUROORD.

## Overlaysynchronisatie van paginaeditor {#page-editor-overlay-synchronization}

De synchronisatie van de overlays wordt gegarandeerd door dezelfde Mutation Observer die door de categorie `cq.authoring.page` wordt geboden.

## Sling Model JSON Geëxporteerde structuurconfiguratie {#sling-model-json-exported-structure-configuration}

Wanneer de verpletterende mogelijkheden worden toegelaten, is de veronderstelling dat de uitvoer JSON van het KUUROORD de verschillende routes van de toepassing dankzij de uitvoer JSON van de navigatiecomponent van AEM bevat. De output JSON van de navigatiecomponent van AEM kan in het de inhoudbeleid van de wortelpagina van het KUUROORD door de volgende twee eigenschappen worden gevormd:

* `structureDepth`: getal dat overeenkomt met de diepte van de geëxporteerde structuur
* `structurePatterns`: Regex van array van regexes die overeenkomt met de pagina die geëxporteerd moet worden

Dit kan in de het steekproefinhoud van het KUUROORD in `/conf/we-retail-journal/react/settings/wcm/policies/we-retail-journal/react/components/structure/page/root` worden getoond.
