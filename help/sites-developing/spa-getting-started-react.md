---
title: Aan de slag met SPA in AEM - Reageren
description: In dit artikel wordt een voorbeeld SPA toepassing gepresenteerd, wordt uitgelegd hoe deze wordt samengesteld en kunt u snel met uw eigen SPA aan de slag met het React-framework.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: 552649e7-6054-4ae8-b570-5ba7230e6f19
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---

# Aan de slag met SPA in AEM - Reageren{#getting-started-with-spas-in-aem-react}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van SPA frameworks.

De SPA ontwerpfunctie biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel biedt een vereenvoudigde SPA toepassing voor het React-framework, legt uit hoe het is samengesteld, zodat u snel aan de slag kunt met uw eigen SPA.

>[!NOTE]
>
>Dit artikel is gebaseerd op het React-kader. Voor het overeenkomstige document voor het kader van de Angular zie [Aan de slag met SPA in AEM - Angular](/help/sites-developing/spa-getting-started-angular.md).

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA op kader-gebaseerde cliënt-zijteruggeven (bijvoorbeeld, Reageren of Angular) vereisen.

## Inleiding {#introduction}

Dit artikel vat het basisfunctioneren van een eenvoudige SPA en het minimum samen dat u moet weten om van u lopend te krijgen.

Raadpleeg de volgende documenten voor meer informatie over SPA werken in AEM:

* [SPA Inleiding en Analyse](/help/sites-developing/spa-walkthrough.md)
* [Introductie SPA](/help/sites-developing/spa-overview.md)
* [SPA](/help/sites-developing/spa-blueprint.md)

>[!NOTE]
>
>Om inhoud binnen een SPA te kunnen ontwerpen, moet de inhoud in AEM worden opgeslagen en door het inhoudsmodel worden blootgesteld.
>
>Een SPA die buiten AEM is ontwikkeld, is niet ontvankelijk als het contract voor het inhoudsmodel niet wordt nageleefd.

Dit document doorloopt de structuur van een vereenvoudigde SPA die is gemaakt met het React-framework en illustreert hoe het werkt, zodat u deze interpretatie kunt toepassen op uw eigen SPA.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van React, kan de steekproef SPA extra bibliotheken gebruiken om de verwezenlijking van SPA efficiënter te maken.

### Afhankelijkheden {#dependencies}

De `package.json` bevat de vereisten van het algemene SPA. De minimum AEM gebiedsdelen voor een werkende SPA zijn hier vermeld.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

Omdat dit voorbeeld is gebaseerd op het React-kader, zijn er twee React-specifieke afhankelijkheden die verplicht zijn in het `package.json` bestand:

```
react
 react-dom
```

De `aem-clientlib-generator` wordt gebruikt om het maken van clientbibliotheken automatisch te maken als onderdeel van het ontwikkelproces.

`"aem-clientlib-generator": "^1.4.1",`

Meer informatie hierover is te vinden [op GitHub hier](https://github.com/wcm-io-frontend/aem-clientlib-generator).

>[!CAUTION]
>
>De minimumversie van de `aem-clientlib-generator` vereist is 1.4.1.

De `aem-clientlib-generator` is geconfigureerd in de `clientlib.config.js` bestand als volgt.

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

### Gebouw {#building}

Toepassingen ontwikkelen [Webpack](https://webpack.js.org/) voor de omzetting in aanvulling op de aem-clientlib-generator voor het automatisch maken van clientbibliotheken. Daarom zal het bouwstijlbevel op lijken:

`"build": "webpack && clientlib --verbose"`

Nadat het pakket is gemaakt, kan het naar een AEM-instantie worden geüpload.

### Projectarchetype AEM {#aem-project-archetype}

Voor elk AEM project moet het [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html), die SPA projecten steunt die React of Angular gebruiken en SPA SDK gebruikt.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app samenstelt zoals eerder beschreven, blijft er een werkende SPA over die u kunt uploaden naar uw AEM-exemplaar.

In het volgende gedeelte van dit document wordt uitgelegd hoe een SPA in AEM is gestructureerd, welke belangrijke bestanden de toepassing sturen en hoe deze samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### index.js {#index-js}

Het ingangspunt in de SPA is de `index.js` bestand dat hier wordt weergegeven, is vereenvoudigd zodat u zich kunt concentreren op de belangrijke inhoud.

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

De hoofdfunctie van `index.js` is om de `ReactDOM.render` om te bepalen waar in de DOM de toepassing wordt geïnjecteerd.

Dit is een standaardgebruik van deze functie, niet uniek voor deze voorbeeldapp.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje (bijvoorbeeld, JSX), moet de waarde van het model tot de eigenschappen van de component worden overgegaan.

### App.js {#app-js}

Door de app te renderen, `index.js` oproepen `App.js`, die hier in een vereenvoudigde versie wordt getoond om zich op de belangrijke inhoud te concentreren.

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

Door de pagina weer te geven, `App.js` oproepen `Page.js` hier in een vereenvoudigde versie vermeld.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

In dit voorbeeld wordt `AppPage` class extends `Page`, die de methoden voor binneninhoud bevat die vervolgens kunnen worden gebruikt.

De `Page` Voert de JSON-representatie van het paginamodel in en verwerkt de inhoud om elk element van de pagina om te buigen of te versieren. Nadere bijzonderheden over de `Page` kan in het document worden gevonden [SPA](/help/sites-developing/spa-blueprint.md#main-pars-header-1694932501).

### Image.js {#image-js}

Wanneer de pagina is gerenderd, worden de componenten zoals `Image.js` zoals u hier ziet, kan worden gerenderd.

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

Het centrale idee van SPA in AEM is het idee om SPA componenten aan AEM componenten in kaart te brengen en de component bij te werken wanneer de inhoud (en omgekeerd) wordt gewijzigd. Zie het document [Overzicht SPA Editor](/help/sites-developing/spa-overview.md) voor een samenvatting van dit communicatiemodel.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

De `MapTo` methode wijst de SPA component aan de AEM component toe. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

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

De `MapTo` functie retourneert een `Component` die het resultaat is van een samenstelling die de verstrekte `PageClass` met de klassennamen en -kenmerken die het ontwerpen mogelijk maken. Deze component kan naar later worden uitgevoerd om in de prijsverhoging van uw toepassing worden geconcretiseerd.

Als u het dialoogvenster `MapTo` of `withModel` functies, `Page` component, is verpakt met een `ModelProvider` die standaardcomponenten toegang biedt tot de nieuwste versie van het paginamodel of een exacte locatie in dat paginamodel.

Zie voor meer informatie de [Blauwdrukdocument SPA](/help/sites-developing/spa-blueprint.md#main-pars-header-329251743).

>[!NOTE]
>
>Standaard ontvangt u het volledige model van de component wanneer u de opdracht `withModel` functie.

## Informatie delen tussen SPA componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** Centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld, door React Context te gebruiken.
* **Optie 2:** Deelstatussen delen met een framebibliotheek, zoals Redux.
* **Optie 3:** Gebruik de objecthiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

Voor een geleidelijke gids voor het creëren van uw eigen SPA, zie [Aan de slag met de AEM SPA Editor - Zelfstudie voor WKND-gebeurtenissen](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html).

Zie het artikel voor meer informatie over hoe u uzelf kunt organiseren om SPA voor AEM te ontwikkelen [SPA ontwikkelen voor AEM](/help/sites-developing/spa-architecture.md).

Raadpleeg het artikel voor meer informatie over het dynamische model naar componenttoewijzing en over de manier waarop het binnen SPA in AEM werkt [Dynamisch model naar componenttoewijzing voor SPA](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Als u SPA in AEM voor een ander kader dan React of Angular wilt uitvoeren of eenvoudig een diepe duik in willen nemen hoe SPA SDK voor AEM werkt, zie [SPA](/help/sites-developing/spa-blueprint.md) artikel.
