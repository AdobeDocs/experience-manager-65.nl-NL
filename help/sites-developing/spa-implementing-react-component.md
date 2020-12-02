---
title: Een component React implementeren voor SPA
seo-title: Een component React implementeren voor SPA
description: Dit artikel biedt een voorbeeld van hoe u een eenvoudige, bestaande React-component kunt aanpassen aan het werk met de AEM SPA Editor.
seo-description: Dit artikel biedt een voorbeeld van hoe u een eenvoudige, bestaande React-component kunt aanpassen aan het werk met de AEM SPA Editor.
uuid: ae6a0a6f-0c3c-4820-9b58-c2a85a9f5291
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 6ed15763-02cc-45d1-adf6-cf9e5e8ebdb0
docset: aem65
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---


# Een React-component implementeren voor SPA{#implementing-a-react-component-for-spa}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van SPA frameworks.

De SPA ontwerpfunctie biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel biedt een voorbeeld van hoe u een eenvoudige, bestaande React-component kunt aanpassen aan het werk met de AEM SPA Editor.

>[!NOTE]
>
>De SPA Editor is de aanbevolen oplossing voor projecten die SPA op raamwerk gebaseerde renderen aan de clientzijde vereisen (bijvoorbeeld Reageren of Hoekig).

## Inleiding {#introduction}

Dankzij het eenvoudige en lichte contract dat door AEM wordt vereist en tussen de SPA en de SPA Editor tot stand is gebracht, is het eenvoudig om een bestaande Javascript-toepassing te nemen en deze aan te passen voor gebruik met een SPA in AEM.

Dit artikel illustreert het voorbeeld van de weercomponent op de Wij.Retail steekproef van het Dagboek SPA.

Voordat u dit artikel leest, moet u bekend zijn met de [structuur van een SPA toepassing voor AEM](/help/sites-developing/spa-getting-started-react.md).

>[!CAUTION]
>Dit document gebruikt [We.Retail Journal app](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) alleen voor demonstratiedoeleinden. Het mag niet worden gebruikt voor projectwerkzaamheden.
>
>Om het even welk AEM project zou hefboomwerking [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html), dat SPA projecten gebruikend React of Hoekig steunt en hefboomwerkingen de SPA SDK.

## De weercomponent {#the-weather-component}

De weercomponent staat linksboven in de app Web.Retail Journal. Het toont het huidige weer van een bepaalde plaats, trekkend dynamisch weergegevens.

### De widget Weer gebruiken {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Wanneer u inhoud van de SPA ontwerpt in de SPA Editor, wordt de weercomponent net als elke andere AEM weergegeven, compleet met een werkbalk en is deze bewerkbaar.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

De plaats kan in een dialoog enkel als om het even welke andere AEM component worden bijgewerkt.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

De wijziging blijft bestaan en de component wordt automatisch bijgewerkt met nieuwe weergegevens.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implementatie van doezelcomponent {#weather-component-implementation}

De weercomponent is eigenlijk gebaseerd op een openbaar-beschikbare component van de Reactie, genoemd [Reageer Open Weer](https://www.npmjs.com/package/react-open-weather), die is aangepast om als component binnen de Wij.Retail steekproeftoepassing van het Dagboek SPA te werken.

Hieronder vindt u fragmenten uit de NPM-documentatie van het gebruik van de component React Open Weather.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Het herzien van de code van de aangepaste weercomponent ( `Weather.js`) in de toepassing van het Dagboek Wij.Retail:

* **Regel 16**: De widget Open Weer reageren wordt naar wens geladen.
* **Regel 46**: De  `MapTo` functie koppelt deze React component aan een overeenkomstige AEM component zodat het in de SPARedacteur kan worden uitgegeven.

* **Lijnen 22-29**: De waarde  `EditConfig` wordt gedefinieerd, waarbij wordt gecontroleerd of de stad is gevuld en de waarde wordt gedefinieerd als deze leeg is.

* **Lijnen 31-44**: De component Weather breidt de  `Component` klasse uit en verstrekt de vereiste gegevens zoals die in de NPM gebruiksdocumentatie voor de React Open component van het Weer worden bepaald en geeft de component terug.

```javascript
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ~ Copyright 2018 Adobe Systems Incorporated
 ~
 ~ Licensed under the Apache License, Version 2.0 (the "License");
 ~ you may not use this file except in compliance with the License.
 ~ You may obtain a copy of the License at
 ~
 ~     https://www.apache.org/licenses/LICENSE-2.0
 ~
 ~ Unless required by applicable law or agreed to in writing, software
 ~ distributed under the License is distributed on an "AS IS" BASIS,
 ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 ~ See the License for the specific language governing permissions and
 ~ limitations under the License.
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
import React, {Component} from 'react';
import ReactWeather from 'react-open-weather';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Weather.css');

const WeatherEditConfig = {

    emptyLabel: 'Weather',

    isEmpty: function() {
        return !this.props || !this.props.cq_model || !this.props.cq_model.city || this.props.cq_model.city.trim().length < 1;
    }
};

class Weather extends Component {

    render() {
        let apiKey = "12345678901234567890";
        let city;

        if (this.props.cq_model) {
            city = this.props.cq_model.city;
            return <ReactWeather key={'react-weather' + Date.now()} forecast="today" apikey={apiKey} type="city" city={city} />
        }

        return null;
    }
}

MapTo('we-retail-journal/global/components/weather')(Weather, WeatherEditConfig);
```

Hoewel een back-end component reeds moet bestaan, kan de front-end ontwikkelaar hefboomwerking de React Open component van het Weer in de SPA van het Dagboek van de Handel met zeer weinig codering.

## Volgende stap {#next-step}

Zie het artikel [SPA ontwikkelen voor AEM](/help/sites-developing/spa-architecture.md) voor meer informatie over het ontwikkelen van SPA voor AEM.
