---
title: SPA-paginacomponent
seo-title: SPA-paginacomponent
description: In een KUUROORD verstrekt de paginacomponent niet de elementen van HTML van zijn kindcomponenten, maar in plaats daarvan delegeert dit aan het kader van het KUUROORD. Dit document verklaart hoe dit tot de paginacomponent van een SPA uniek maakt.
seo-description: In een KUUROORD verstrekt de paginacomponent niet de elementen van HTML van zijn kindcomponenten, maar in plaats daarvan delegeert dit aan het kader van het KUUROORD. Dit document verklaart hoe dit tot de paginacomponent van een SPA uniek maakt.
uuid: d444527a-e883-4873-a55b-c2bc140d8d7f
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 6329301c-1a26-4a46-99ae-1b7cc15b08be
docset: aem65
translation-type: tm+mt
source-git-commit: 14cc66dfef7bc7781907bdd6093732912c064579

---


# SPA-paginacomponent{#spa-page-component}

In een KUUROORD verstrekt de paginacomponent niet de elementen van HTML van zijn kindcomponenten, maar in plaats daarvan delegeert dit aan het kader van het KUUROORD. Dit document verklaart hoe dit tot de paginacomponent van een SPA uniek maakt.

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

## Inleiding {#introduction}

De paginacomponent voor een SPA verstrekt niet de elementen van HTML van zijn kindcomponenten via een JSP of HTML- dossier en middelvoorwerpen. Deze verrichting wordt gedelegeerd aan het kader van het KUUROORD. De representatie van onderliggende componenten wordt opgehaald als een JSON-gegevensstructuur (dat wil zeggen het model). De componenten van het KUUROORD worden dan toegevoegd aan de pagina volgens het verstrekte model JSON. De oorspronkelijke compositie van de hoofdtekst van de paginacomponent verschilt daarom van de vooraf weergegeven HTML-tegenhangers.

## Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een opgegeven [ `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) module. Het KUUROORD moet met de `PageModelManager` module in wisselwerking staan wanneer het initialiseert om het aanvankelijke paginamodel en register voor modelupdates te halen - meestal geproduceerd wanneer de auteur de pagina via de Redacteur van de Pagina uitgeeft. Het `PageModelManager` is toegankelijk door het project van het KUUUROORD als npm pakket. Als tolk tussen AEM en de SPA `PageModelManager` is het de bedoeling de SPA te begeleiden.

Om toe te staan dat de pagina wordt geschreven, `cq.authoring.pagemodel.messaging` moet een genoemde cliëntbibliotheek worden toegevoegd om een communicatie kanaal tussen het KUUROORD en de paginaredacteur te verstrekken. Als de de paginacomponent van het KUUROORD van de pagina wcm/kerncomponent erft dan zijn er de volgende opties om de categorie van de `cq.authoring.pagemodel.messaging` cliëntbibliotheek beschikbaar te maken:

* Als de sjabloon bewerkbaar is, voegt u de categorie van de clientbibliotheek toe aan het paginabeleid.
* Voeg de categorie van de cliëntbibliotheek toe gebruikend de `customfooterlibs.html` component van de pagina.

Vergeet niet de opname van de `cq.authoring.pagemodel.messaging` categorie te beperken tot de context van de pagina-editor.

## Gegevenstype communicatie {#communication-data-type}

Het gegevenstype voor communicatie wordt ingesteld als een HTML-element binnen de component AEM Page met behulp van het `data-cq-datatype` kenmerk. Wanneer het gegevenstype van communicatiegegevens aan JSON wordt geplaatst, krijgen de GET verzoeken de Sling Model eindpunten van een component. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. De bibliotheek van het Model van de Pagina waarschuwt dan het KUUROORD van updates.

**SPA-paginacomponent -`body.html`**

```
<div id="page"></div>
```

Naast het zijn goede praktijken om de generatie van DOM niet uit te stellen, vereist het kader van het KUUROORD dat de manuscripten aan het eind van het lichaam worden toegevoegd.

**SPA-paginacomponent -`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

De eigenschappen van het meta-middel die de inhoud van het KUUROORD beschrijven:

**SPA-paginacomponent -`customheaderlibs.html`**

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
* `cq:pagemodel_root_url`: URL van het basismodel van de app. Cruciaal bij directe toegang tot een onderliggende pagina, aangezien het onderliggende paginamodel een fragment is van het basismodel van de app. Vervolgens stelt de toepassing het oorspronkelijke model systematisch opnieuw samen, zodat de toepassing vanaf het hoofdinvoerpunt wordt ingevoerd. ` [PageModelManager](/help/sites-developing/spa-page-component.md)`

* `cq:pagemodel_router`: Het inschakelen of uitschakelen ` [ModelRouter](/help/sites-developing/spa-routing.md)` van de `PageModelManager` bibliotheek

* `cq:pagemodel_route_filters`: Door komma&#39;s gescheiden lijsten of reguliere expressies om routes te bieden die de gebruiker ` [ModelRouter](/help/sites-developing/spa-routing.md)` moet negeren.

>[!CAUTION]
>
>Dit document gebruikt de app We.Retail Journal alleen voor demonstratiedoeleinden. Het mag niet worden gebruikt voor projectwerkzaamheden.
>
>Om het even welk AEM project zou hefboomwerking het Archetype [van het Project van](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM moeten, dat de projecten van het KUUROORD gebruikend React of Angular steunt en hefboomwerkingen het KUUROORD SDK.Alle projecten van het KUUROORD op AEM zouden op het Geweven Archetype voor Kit van de Aanzet van het KUUROORD moeten worden gebaseerd.

## Overlaysynchronisatie van paginaeditor {#page-editor-overlay-synchronization}

De synchronisatie van de overlays wordt gegarandeerd door dezelfde Mutation Observer die de `cq.authoring.page` categorie biedt.

## Sling Model JSON Geëxporteerde structuurconfiguratie {#sling-model-json-exported-structure-configuration}

Wanneer de verpletterende mogelijkheden worden toegelaten, is de veronderstelling dat de uitvoer JSON van SPA de verschillende routes van de toepassing dankzij de uitvoer JSON van de AEM navigatiecomponent bevat. De output JSON van de navigatiecomponent AEM kan in het de inhoudbeleid van de wortelpagina van het KUUROORD door de volgende twee eigenschappen worden gevormd:

* `structureDepth`: Aantal dat overeenkomt met de diepte van de geëxporteerde structuur
* `structurePatterns`: Regex van array van regexes die overeenkomt met de pagina die geëxporteerd moet worden

Dit kan in de de steekproefinhoud van het KUUROORD in worden getoond `/conf/we-retail-journal/react/settings/wcm/policies/we-retail-journal/react/components/structure/page/root`.
