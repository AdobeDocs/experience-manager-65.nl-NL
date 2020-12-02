---
title: Aan de slag met SPA in AEM - Reageren
seo-title: Aan de slag met SPA in AEM - Reageren
description: In dit artikel wordt een voorbeeld SPA toepassing gepresenteerd, wordt uitgelegd hoe deze wordt samengesteld en kunt u snel met uw eigen SPA aan de slag gaan met het React-framework.
seo-description: In dit artikel wordt een voorbeeld SPA toepassing gepresenteerd, wordt uitgelegd hoe deze wordt samengesteld en kunt u snel met uw eigen SPA aan de slag gaan met het React-framework.
uuid: 2beca277-a381-4482-99f6-85005d826d06
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: cc1e5c20-cc9c-4222-8a11-ec5a963d4466
docset: aem65
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 0%

---


# Aan de slag met SPA in AEM - Reageren{#getting-started-with-spas-in-aem-react}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van SPA frameworks.

De SPA ontwerpfunctie biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel biedt een vereenvoudigde SPA toepassing voor het React-framework, legt uit hoe het is samengesteld, zodat u snel aan de slag kunt met uw eigen SPA.

>[!NOTE]
>
>Dit artikel is gebaseerd op het React-kader. Zie [Aan de slag met SPA in AEM - Hoek](/help/sites-developing/spa-getting-started-angular.md) voor het corresponderende document voor het hoekframework.

>[!NOTE]
>
>De SPA Editor is de aanbevolen oplossing voor projecten die SPA op raamwerk gebaseerde renderen aan de clientzijde vereisen (bijvoorbeeld Reageren of Hoekig).

## Inleiding {#introduction}

Dit artikel vat het basisfunctioneren van een eenvoudige SPA en het minimum samen dat u moet weten om van u lopend te krijgen.

Raadpleeg de volgende documenten voor meer informatie over SPA werken in AEM:

* [SPA Inleiding en Analyse](/help/sites-developing/spa-walkthrough.md)
* [Introductie SPA](/help/sites-developing/spa-overview.md)
* [SPA](/help/sites-developing/spa-blueprint.md)

>[!NOTE]
>
>Om inhoud binnen een SPA te kunnen schrijven, moet de inhoud in AEM worden opgeslagen en door het inhoudsmodel worden vrijgegeven.
>
>Een SPA die buiten AEM is ontwikkeld, is niet ontvankelijk als het contract voor het inhoudsmodel niet wordt nageleefd.

Dit document doorloopt de structuur van een vereenvoudigde SPA die is gemaakt met het React-framework en illustreert hoe het werkt, zodat u deze interpretatie kunt toepassen op uw eigen SPA.

## Afhankelijkheden, configuratie en gebouw {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van React, kan de steekproef SPA extra bibliotheken gebruiken om de verwezenlijking van SPA efficiënter te maken.

### Afhankelijkheden {#dependencies}

Het `package.json` dossier bepaalt de vereisten van het algemene SPA pakket. De minimum AEM gebiedsdelen voor een werkende SPA zijn hier vermeld.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

Omdat dit voorbeeld op het React kader gebaseerd is, zijn er twee React-specifieke gebiedsdelen die in het `package.json` dossier verplicht zijn:

```
react
 react-dom
```

De `aem-clientlib-generator` wordt gebruikt om het maken van clientbibliotheken automatisch te maken als onderdeel van het ontwikkelproces.

`"aem-clientlib-generator": "^1.4.1",`

Meer details over het kunnen [op GitHub hier](https://github.com/wcm-io-frontend/aem-clientlib-generator) worden gevonden.

>[!CAUTION]
>
>De minimaal vereiste versie van `aem-clientlib-generator` is 1.4.1.

`aem-clientlib-generator` wordt gevormd in `clientlib.config.js` dossier als volgt.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-react-app/clientlibs",

    libs: {
        name: "my-react-app",
        allowProxy: true,
        categories: ["my-react-app"],
        embed: ["my-react-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### {#building} samenstellen

Bij het ontwikkelen van de app wordt [Webpack](https://webpack.js.org/) benut voor omzetting in aanvulling op de aem-clientlib-generator voor het automatisch maken van de clientbibliotheek. Daarom zal het bouwstijlbevel op lijken:

`"build": "webpack && clientlib --verbose"`

Nadat het pakket is gemaakt, kan het naar een AEM-instantie worden geüpload.

### Projectarchetype {#aem-project-archetype} AEM

Om het even welk AEM project zou hefboomwerking [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html), dat SPA projecten gebruikend React of Hoekig steunt en hefboomwerkingen de SPA SDK.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app samenstelt zoals eerder beschreven, blijft er een werkende SPA over die u kunt uploaden naar uw AEM.

In het volgende gedeelte van dit document wordt uitgelegd hoe een SPA in AEM is gestructureerd, welke belangrijke bestanden de toepassing sturen en hoe deze samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### index.js {#index-js}

Het ingangspunt in de SPA is natuurlijk het `index.js` dossier hier vereenvoudigd om zich op de belangrijke inhoud te concentreren.

```
import ReactDOM from 'react-dom';
import App from './App';
import { ModelManager, Constants } from "@adobe/aem-spa-page-model-manager";

...

ModelManager.initialize().then((pageModel) => {
ReactDOM.render(
    <App cqChildren={pageModel[Constants.CHILDREN_PROP]} cqItems={pageModel[Constants.ITEMS_PROP]} cqItemsOrder={pageModel[Constants.ITEMS_ORDER_PROP]} cqPath={ModelManager.rootPath} locationPathname={ window.location.pathname }/>
, document.getElementById('page'));

});
```

De belangrijkste functie van `index.js` is het hefboomeffect van de `ReactDOM.render` functie om te bepalen waar in DOM om de toepassing te injecteren.

Dit is een standaardgebruik van deze functie, niet uniek voor deze voorbeeldapp.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje (b.v. JSX), moet de waarde van het model tot de eigenschappen van de component worden overgegaan.

### App.js {#app-js}

Door de app te renderen, `index.js` roept `App.js` aan, die hier in een vereenvoudigde versie wordt getoond om zich op de belangrijke inhoud te concentreren.

```
import {Page, withModel } from '@adobe/aem-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` Deze service omvat hoofdzakelijk het verpakken van de basiscomponenten waaruit de app is samengesteld. Het ingangspunt van elke toepassing is de pagina.

### Page.js {#page-js}

Door de pagina terug te geven, `App.js` roept `Page.js` hier in een vereenvoudigde versie vermeld.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

In dit voorbeeld breidt de `AppPage` klasse `Page` uit, die de binnen-inhoudsmethodes bevat die dan kunnen worden gebruikt.

De `Page` neemt de JSON-weergave van het paginamodel op en verwerkt de inhoud om elk element van de pagina om te buigen of te versieren. Meer informatie over `Page` vindt u in het document [SPA Blauwdruk](/help/sites-developing/spa-blueprint.md#main-pars-header-1694932501).

### Image.js {#image-js}

Als de pagina wordt gerenderd, kunnen de componenten zoals `Image.js` zoals hier getoond worden teruggegeven.

```
import React, {Component} from 'react';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Image.css');

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function() {
        return !this.props || !this.props.src || this.props.src.trim().length < 1;
    }
};

class Image extends Component {

    render() {
        return (<img src={this.props.src}>);
    }
}

MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);
```

Het centrale idee van SPA in AEM is het idee om SPA componenten aan AEM componenten in kaart te brengen en de component bij te werken wanneer de inhoud wordt gewijzigd (en vice versa). Zie het document [SPA het Overzicht van de Redacteur](/help/sites-developing/spa-overview.md) voor een samenvatting van dit communicatie model.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

De methode `MapTo` wijst de SPA component aan de AEM toe. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

`ImageEditConfig` is een configuratievoorwerp dat tot het toelaten van de auteursmogelijkheden van een component bijdraagt door de noodzakelijke meta-gegevens voor de redacteur te verstrekken om placeholders te produceren

Als er geen inhoud is, worden etiketten verstrekt als placeholders om de lege inhoud te vertegenwoordigen.

#### Dynamisch doorgegeven eigenschappen {#dynamically-passed-properties}

De gegevens uit het model worden dynamisch doorgegeven als eigenschappen van de component.

## Bewerkbare inhoud exporteren {#exporting-editable-content}

U kunt een component exporteren en bewerkbaar houden.

```
import React, { Component } from 'react';
import { MapTo } from '@adobe/aem-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

De functie `MapTo` keert `Component` terug die het resultaat van een samenstelling is die verstrekt `PageClass` met de klassennamen en de attributen uitbreidt die het auteursrecht toelaten. Deze component kan naar later worden uitgevoerd om in de prijsverhoging van uw toepassing worden geconcretiseerd.

Bij het exporteren met de functies `MapTo` of `withModel` wordt de component `Page` verpakt met een component `ModelProvider` die standaardcomponenten toegang biedt tot de nieuwste versie van het paginamodel of een exacte locatie in dat paginamodel.

Zie [SPA document Blueprint](/help/sites-developing/spa-blueprint.md#main-pars-header-329251743) voor meer informatie.

>[!NOTE]
>
>Door gebrek ontvangt u het volledige model van de component wanneer het gebruiken van de `withModel` functie.

## Informatie delen tussen SPA componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld door React Context te gebruiken.
* **Optie 2:** Deel componentstatussen met een framebibliotheek, zoals Redux.
* **Optie 3:** Gebruik de objecthiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

Voor een geleidelijke gids voor het creëren van uw eigen SPA, zie [Begonnen het worden met de AEM SPA Redacteur - WKND de Zelfstudie van Gebeurtenissen](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html).

Zie het artikel [SPA ontwikkelen voor AEM](/help/sites-developing/spa-architecture.md) voor meer informatie over hoe u uzelf kunt organiseren om SPA te ontwikkelen voor AEM.

Zie het artikel [Dynamisch model aan componenttoewijzing voor SPA](/help/sites-developing/spa-dynamic-model-to-component-mapping.md) voor meer informatie over het dynamische model aan componenttoewijzing en hoe het werkt binnen SPA in AEM.

Als u SPA in AEM voor een ander kader dan React of Hoekig wilt uitvoeren of eenvoudig een diepe duik in willen nemen hoe de SPA SDK voor AEM werkt, verwijs naar [SPA Blauwdruk](/help/sites-developing/spa-blueprint.md) artikel.
