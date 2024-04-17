---
title: Aan de slag met SPA in AEM - Angular
description: Dit artikel presenteert een voorbeeld SPA toepassing, legt uit hoe het wordt samengesteld, en laat u met uw eigen SPA snel het kader van de Angular in werking stellen.
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: 9528d92b-0989-4e2d-83be-ba6c07c845e2
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 0%

---

# Aan de slag met SPA in AEM - Angular{#getting-started-with-spas-in-aem-angular}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van SPA frameworks.

De SPA ontwerpfunctie biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel presenteert een vereenvoudigde SPA toepassing over het kader van de Angular, verklaart hoe het wordt samengesteld, die u toestaat om met uw eigen SPA snel in werking te stellen.

>[!NOTE]
>
>Dit artikel is gebaseerd op het kader van de Angular. Zie voor het bijbehorende document voor het React-framework [Aan de slag met SPA in AEM - Reageren](/help/sites-developing/spa-getting-started-react.md).

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

Dit document loopt door de structuur van een vereenvoudigde SPA en illustreert hoe het werkt zodat u deze interpretatie op uw eigen SPA kunt toepassen.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van de Angular, kan de steekproef SPA extra bibliotheken gebruiken om de verwezenlijking van SPA efficiënter te maken.

### Afhankelijkheden {#dependencies}

De `package.json` bevat de vereisten van het algemene SPA. De minimum vereiste AEM gebiedsdelen zijn hier vermeld.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
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
    clientLibRoot: "./../content/jcr_root/apps/my-angular-app/clientlibs",

    libs: {
        name: "my-angular-app",
        allowProxy: true,
        categories: ["my-angular-app"],
        embed: ["my-angular-app.responsivegrid"],
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

`"build": "ng build --build-optimizer=false && clientlib",`

Nadat het pakket is gemaakt, kan het naar een AEM-instantie worden geüpload.

### Projectarchetype AEM {#aem-project-archetype}

Voor elk AEM project moet het [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html), die SPA projecten steunt die React of Angular gebruiken en SPA SDK gebruikt.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app samenstelt zoals eerder beschreven, blijft er een werkende SPA over die u kunt uploaden naar uw AEM-exemplaar.

In het volgende gedeelte van dit document wordt uitgelegd hoe een SPA in AEM is gestructureerd, welke belangrijke bestanden de toepassing sturen en hoe deze samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### app.module.ts {#app-module-ts}

Het ingangspunt in de SPA is de `app.module.ts` bestand dat hier wordt weergegeven, is vereenvoudigd zodat u zich kunt concentreren op de belangrijke inhoud.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/aem-angular-editable-components';
import { AppRoutingModule } from './app-routing.module';

@NgModule({
  imports: [ BrowserModule.withServerTransition({ appId: 'my-angular-app' }),
    SpaAngularEditableComponentsModule,
    AppRoutingModule,
    BrowserTransferStateModule ],
  providers: ...,
  declarations: [ ... ],
  entryComponents: [ ... ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```

De `app.module.ts` het dossier is het uitgangspunt van app en bevat de aanvankelijke projectconfiguratie en het gebruik `AppComponent` om de app op te starten.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje, moet de waarde van het model tot de eigenschappen van de component worden overgegaan. De waarden van het model worden doorgegeven als kenmerken die later beschikbaar moeten zijn als componenteigenschappen.

### app.component.ts {#app-component-ts}

Eenmaal `app.module.ts` bootstraps `AppComponent`kan de toepassing vervolgens worden geïnitialiseerd. Deze versie wordt hier in een vereenvoudigde versie weergegeven en richt zich op de belangrijke inhoud.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/aem-spa-page-model-manager';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-root',
  template: `
    <router-outlet></router-outlet>
  `
})

export class AppComponent {
  items;
  itemsOrder;
  path;

  constructor() {
    ModelManager.initialize().then(this.updateData.bind(this));
  }

  private updateData(model) {
    this.path = model[Constants.PATH_PROP];
    this.items = model[Constants.ITEMS_PROP];
    this.itemsOrder = model[Constants.ITEMS_ORDER_PROP];
  }
}
```

### main-content.component.ts {#main-content-component-ts}

Door de pagina te verwerken, `app.component.ts` oproepen `main-content.component.ts` hier vermeld in een vereenvoudigde versie.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-main',
  template: `
    <aem-page class="structure-page" [attr.data-cq-page-path]="path" [cqPath]="path" [cqItems]="items" [cqItemsOrder]="itemsOrder" ></aem-page>
  `
})

export class MainContentComponent {
  items;
  itemsOrder;
  path;

  constructor( private route: ActivatedRoute,
    private modelManagerService: ModelManagerService) {
    this.modelManagerService.getData({ path: this.route.snapshot.data.path }).then((data) => {
      this.path = data[Constants.PATH_PROP];
      this.items = data[Constants.ITEMS_PROP];
      this.itemsOrder = data[Constants.ITEMS_ORDER_PROP];
    });
  }
}
```

De `MainComponent` Voert de JSON-representatie van het paginamodel in en verwerkt de inhoud om elk element van de pagina om te buigen of te versieren. Nadere bijzonderheden over de `Page` kan in het document worden gevonden [SPA](/help/sites-developing/spa-blueprint.md#main-pars-header-1694932501).

### image.component.ts {#image-component-ts}

De `Page` bestaat uit componenten. Als de JSON wordt ingeslikt, kan de `Page` kan componenten zoals `image.component.ts` zoals u hier ziet.

```
/// image.component.ts
import { Component, Input } from '@angular/core';

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function(cqModel) {
        return !cqModel || !cqModel.src || cqModel.src.trim().length < 1;
    }
};

@Component({
  selector: 'app-image',
  templateUrl: './image.component.html',
})

export class ImageComponent {
  @Input() src: string;
  @Input() alt: string;
  @Input() title: string;
}

MapTo('my-angular-app/components/image')(ImageComponent, ImageEditConfig);
```

Het centrale idee van SPA in AEM is het idee om SPA componenten aan AEM componenten in kaart te brengen en de component bij te werken wanneer de inhoud (en omgekeerd) wordt gewijzigd. Zie het document [Overzicht SPA Editor](/help/sites-developing/spa-overview.md) voor een samenvatting van dit communicatiemodel.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

De `MapTo` methode wijst de SPA component aan de AEM component toe. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

`ImageEditConfig` is een configuratievoorwerp dat tot het toelaten van de auteursmogelijkheden van een component bijdraagt door de noodzakelijke meta-gegevens voor de redacteur te verstrekken om placeholders te produceren

Als er geen inhoud is, worden etiketten verstrekt als placeholders om de lege inhoud te vertegenwoordigen.

#### Dynamisch doorgegeven eigenschappen {#dynamically-passed-properties}

De gegevens uit het model worden dynamisch doorgegeven als eigenschappen van de component.

### image.component.html {#image-component-html}

Ten slotte kan de afbeelding worden gerenderd in `image.component.html`.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Informatie delen tussen SPA componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** Centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld, door een util klasse als zuivere object-oriented oplossing te gebruiken.
* **Optie 2:** De componentenstaten van het aandeel door een staatsbibliotheek zoals NgRx te gebruiken.
* **Optie 3:** Gebruik de objecthiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

Voor een geleidelijke gids voor het creëren van uw eigen SPA, zie [Aan de slag met de AEM SPA Editor - Zelfstudie voor WKND-gebeurtenissen](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html).

Zie het artikel voor meer informatie over hoe u uzelf kunt organiseren om SPA voor AEM te ontwikkelen [SPA ontwikkelen voor AEM](/help/sites-developing/spa-architecture.md).

Raadpleeg het artikel voor meer informatie over het dynamische model naar componenttoewijzing en over de manier waarop het binnen SPA in AEM werkt [Dynamisch model naar componenttoewijzing voor SPA](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Als u SPA in AEM voor een ander kader dan React of Angular wilt uitvoeren of eenvoudig een diepe duik in willen nemen hoe SPA SDK voor AEM werkt, zie [SPA](/help/sites-developing/spa-blueprint.md) artikel.
