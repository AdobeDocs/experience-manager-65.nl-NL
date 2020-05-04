---
title: Aan de slag met SPA's in AEM - Reageren
seo-title: Aan de slag met SPA's in AEM - Reageren
description: Dit artikel stelt een steekproeftoepassing van het KUUROORD voor, verklaart hoe het wordt samengebracht, en staat u toe om met uw eigen KUUROORD snel in werking te stellen gebruikend het kader van het Reageren.
seo-description: Dit artikel stelt een steekproeftoepassing van het KUUROORD voor, verklaart hoe het wordt samengebracht, en staat u toe om met uw eigen KUUROORD snel in werking te stellen gebruikend het kader van het Reageren.
uuid: 2beca277-a381-4482-99f6-85005d826d06
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: cc1e5c20-cc9c-4222-8a11-ec5a963d4466
docset: aem65
translation-type: tm+mt
source-git-commit: 590dc4464182d4baf8293e7bb0774ce92971c0af

---


# Aan de slag met SPA&#39;s in AEM - Reageren{#getting-started-with-spas-in-aem-react}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend het kader van het KUUROORD wordt gebouwd.

De auteurseigenschap van het KUUROORD biedt een uitvoerige oplossing voor het steunen van SPAs binnen AEM aan. Dit artikel stelt een vereenvoudigde toepassing van het KUUROORD op het kader van het Reageren voor, verklaart hoe het wordt samengesteld, toestaand u om snel met uw eigen KUUROORD in werking te stellen.

>[!NOTE]
>
>Dit artikel is gebaseerd op het React-kader. Voor het overeenkomstige document voor het Hoekkader zie [Begonnen worden met SPAs in AEM - Hoek](/help/sites-developing/spa-getting-started-angular.md).

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

## Inleiding {#introduction}

Dit artikel vat het basisfunctioneren van een eenvoudige KUUROORD en het minimum samen dat u moet weten om van u lopende te krijgen.

Voor meer detail op hoe SPAs in AEM werkt, zie de volgende documenten:

* [Introductie van het KUUROORD en Analyse](/help/sites-developing/spa-walkthrough.md)
* [Introductie SPA Authoring](/help/sites-developing/spa-overview.md)
* [SPA-blauwdruk](/help/sites-developing/spa-blueprint.md)

>[!NOTE]
>
>Om inhoud binnen een SPA te kunnen schrijven, moet de inhoud in AEM worden opgeslagen en door het inhoudsmodel worden blootgesteld.
>
>Een SPA die buiten AEM wordt ontwikkeld zal niet authorable zijn als het niet het contract van het inhoudsmodel eerbiedigt.

Dit document zal door de structuur van een vereenvoudigde SPA lopen die gebruikend het React kader wordt gecreeerd en zal illustreren hoe het werkt zodat kunt u dit begrip op uw eigen SPA toepassen.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van het Reageren, kan de steekproefSPA extra bibliotheken hefboomwerking maken om de verwezenlijking van het KUUROORD efficiënter te maken.

### Afhankelijkheden {#dependencies}

Het `package.json` dossier bepaalt de vereisten van het algemene pakket van SPA. De minimum AEM gebiedsdelen voor een werkende SPA zijn hier vermeld.

```
  "dependencies": {
    "@adobe/cq-react-editable-components": "~1.0.3",
    "@adobe/cq-spa-component-mapping": "~1.0.3",
    "@adobe/cq-spa-page-model-manager": "~1.0.4"
  }
```

Omdat dit voorbeeld is gebaseerd op het React-framework, zijn er twee React-specifieke afhankelijkheden die verplicht zijn in het `package.json` bestand:

```
react
 react-dom
```

Het `aem-clientlib-generator` is gebruikt om het maken van clientbibliotheken automatisch te maken als onderdeel van het ontwikkelproces.

`"aem-clientlib-generator": "^1.4.1",`

Meer details over het kunnen [op GitHub hier](https://github.com/wcm-io-frontend/aem-clientlib-generator)worden gevonden.

>[!CAUTION]
>
>De minimumversie van de `aem-clientlib-generator` vereiste versie is 1.4.1.

Het `aem-clientlib-generator` bestand is als volgt geconfigureerd in het `clientlib.config.js` bestand.

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

Bij het ontwikkelen van de app wordt [Webpack](https://webpack.js.org/) gebruikt voor transplantatie naast de aem-clientlib-generator voor het automatisch maken van clientbibliotheken. Daarom zal het bouwstijlbevel op lijken:

`"build": "webpack && clientlib --verbose"`

Nadat het pakket is gemaakt, kan het worden geüpload naar een AEM-instantie.

### AEM-projectarchetype {#aem-project-archetype}

Om het even welk project AEM zou hefboomwerking het Archetype [van het Project van](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, dat de projecten van het KUUROORD gebruikend React of Hoekig steunt en hefboomwerkingen SDK van het KUUROORD.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app maakt zoals eerder beschreven, blijft er een werkende SPA-pakket over dat u kunt uploaden naar uw AEM-instantie.

De volgende sectie van dit document zal u door hoe een KUUROORD in AEM gestructureerd is, de belangrijke dossiers die de toepassing drijven, en hoe zij samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### index.js {#index-js}

Het ingangspunt in SPA is natuurlijk het hier getoonde `index.js` dossier vereenvoudigd om zich op de belangrijke inhoud te concentreren.

```
import ReactDOM from 'react-dom';
import App from './App';
import { ModelManager, Constants } from "@adobe/cq-spa-page-model-manager";

...

ModelManager.initialize().then((pageModel) => {
ReactDOM.render(
    <App cqChildren={pageModel[Constants.CHILDREN_PROP]} cqItems={pageModel[Constants.ITEMS_PROP]} cqItemsOrder={pageModel[Constants.ITEMS_ORDER_PROP]} cqPath={ModelManager.rootPath} locationPathname={ window.location.pathname }/>
, document.getElementById('page'));

});
```

De belangrijkste functie van `index.js` is het benutten van de `ReactDOM.render` functie om te bepalen waar in het DOM de toepassing wordt geïnjecteerd.

Dit is een standaardgebruik van deze functie, niet uniek voor deze voorbeeldapp.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje (b.v. JSX), moet de waarde van het model tot de eigenschappen van de component worden overgegaan.

### App.js {#app-js}

Door de app te renderen, `index.js` worden aanroepen `App.js`weergegeven in een vereenvoudigde versie om de aandacht op de belangrijke inhoud te vestigen.

```
import {Page, withModel } from '@adobe/cq-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` Deze service omvat hoofdzakelijk het verpakken van de basiscomponenten waaruit de app is samengesteld. Het ingangspunt van elke toepassing is de pagina.

### Page.js {#page-js}

Door de pagina terug te geven, `App.js` `Page.js` vraag hier vermeld in een vereenvoudigde versie.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/cq-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

In dit voorbeeld breidt de `AppPage` klasse zich uit `Page`, die de binneninhoudsmethoden bevat die vervolgens kunnen worden gebruikt.

De code `Page` voegt de JSON-representatie van het paginamodel in en verwerkt de inhoud om elk element van de pagina in te pakken of te versieren. Nadere details over het `Page` kunnen in het document [SPA Blueprint](/help/sites-developing/spa-blueprint.md#main-pars-header-1694932501)worden gevonden.

### Image.js {#image-js}

Als de pagina wordt gerenderd, kunnen de componenten zoals `Image.js` zoals hier getoond worden teruggegeven.

```
import React, {Component} from 'react';
import {MapTo} from '@adobe/cq-react-editable-components';

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

Het centrale idee van SPAs in AEM is het idee om de componenten van SPA aan componenten AEM in kaart te brengen en de component bij te werken wanneer de inhoud (en vice versa) wordt gewijzigd. Zie het Overzicht [van de Redacteur van het document](/help/sites-developing/spa-overview.md) SPA van dit communicatie model.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

De `MapTo` methode brengt de component van het KUUROORD aan de component AEM in kaart. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

`ImageEditConfig` is een configuratievoorwerp dat tot het toelaten van de auteursmogelijkheden van een component bijdraagt door de noodzakelijke meta-gegevens voor de redacteur te verstrekken om placeholders te produceren

Als er geen inhoud is, worden etiketten verstrekt als placeholders om de lege inhoud te vertegenwoordigen.

#### Dynamisch doorgegeven eigenschappen {#dynamically-passed-properties}

De gegevens uit het model worden dynamisch doorgegeven als eigenschappen van de component.

## Bewerkbare inhoud exporteren {#exporting-editable-content}

U kunt een component exporteren en bewerkbaar houden.

```
import React, { Component } from 'react';
import { MapTo } from '@cq/cq-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

De `MapTo` functie retourneert een instructie `Component` die het resultaat is van een compositie die de opgegeven klasse uitbreidt `PageClass` met de klassennamen en kenmerken die het schrijven mogelijk maken. Deze component kan naar later worden uitgevoerd om in de prijsverhoging van uw toepassing worden geconcretiseerd.

Bij het exporteren met behulp van de `MapTo` of `withModel` functies, wordt de `Page` component voorzien van een `ModelProvider` component die standaardcomponenten toegang biedt tot de nieuwste versie van het paginamodel of een exacte locatie in dat paginamodel.

Voor meer informatie zie het document [van de Blauwdruk van het](/help/sites-developing/spa-blueprint.md#main-pars-header-329251743)KUUROORD.

>[!NOTE]
>
>Standaard ontvangt u het volledige model van de component wanneer u de `withModel` functie gebruikt.

## Informatie delen tussen SPA-componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** Centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld door React Context te gebruiken.
* **Optie 2:** Deelstatussen delen met een framebibliotheek, zoals Redux.
* **Optie 3:** Gebruik de objecthiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

Voor een geleidelijke gids aan het creëren van uw eigen SPA, zie [Begonnen het Worden met de Redacteur AEM SPA - het Leerprogramma](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html)van Gebeurtenissen WKND.

Voor verdere informatie over hoe te om zich te organiseren om SPAs voor AEM te ontwikkelen zie het artikel [het Ontwikkelen van SPAs voor AEM](/help/sites-developing/spa-architecture.md).

Voor verdere details over het dynamische model aan componentenafbeelding en hoe het binnen SPAs in AEM werkt, zie het artikel [Dynamisch Model aan de Afbeelding van de Component voor SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Als u wenst om SPAs in AEM voor een kader buiten React of Hoekig uit te voeren of eenvoudig een diepe duik in te nemen hoe het KUUROORD SDK voor AEM werkt, verwijs naar het artikel van het Blauwdruk [van het](/help/sites-developing/spa-blueprint.md) KUUROORD.
