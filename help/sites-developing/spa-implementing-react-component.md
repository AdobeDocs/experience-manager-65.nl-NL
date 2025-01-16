---
title: Een component React implementeren voor SPA
description: In dit artikel wordt een voorbeeld gegeven van hoe u een eenvoudige, bestaande React-component kunt aanpassen aan het werk met de Adobe Experience Manager (AEM) SPA Editor.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: f4959c12-54c5-403a-9973-7a4ab5f16bed
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 6d961456e0e1f7a26121da9be493308a62c53e04
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Een component React implementeren voor SPA{#implementing-a-react-component-for-spa}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen Adobe Experience Manager (AEM) voor een site die is gebouwd met behulp van SPA frameworks.

De SPA ontwerpfunctie biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel biedt een voorbeeld van hoe u een eenvoudige, bestaande React-component kunt aanpassen aan het werk met de AEM SPA Editor.

{{ue-over-spa}}

## Inleiding {#introduction}

Dankzij het eenvoudige en lichte contract dat door AEM wordt vereist en tussen de SPA en de SPA Editor tot stand is gebracht, is het eenvoudig om een bestaande JavaScript-toepassing te nemen en aan te passen voor gebruik met een SPA in AEM.

Dit artikel illustreert het voorbeeld van de weercomponent op de Wij.Retail steekproef van het Dagboek SPA.

U zou met de [ structuur van een SPA toepassing voor AEM ](/help/sites-developing/spa-getting-started-react.md) moeten vertrouwd zijn alvorens dit artikel te lezen.

>[!CAUTION]
>Dit document gebruikt [ Wij.Retail app van het Dagboek ](https://github.com/adobe/aem-sample-we-retail-journal) slechts voor demonstratiedoeleinden. Gebruik het niet voor enig projectwerk.
>
>Om het even welk AEM project zou [ AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat SPA projecten gebruikend React of Angular steunt en SPA SDK gebruikt.

## De component Weer {#the-weather-component}

De weercomponent staat linksboven in de app Web.Retail Journal. Het toont het huidige weer van een bepaalde plaats, trekkend dynamisch weergegevens.

### De widget Weer gebruiken {#using-the-weather-widget}

![ screen_shot_2018-06-08at143224 ](assets/screen_shot_2018-06-08at143224.png)

Wanneer u inhoud van de SPA ontwerpt in de SPA Editor, wordt de weercomponent net als elke andere AEM weergegeven, compleet met een werkbalk en is deze bewerkbaar.

![ screen_shot_2018-06-08at143304 ](assets/screen_shot_2018-06-08at143304.png)

De plaats kan in een dialoog enkel als om het even welke andere AEM component worden bijgewerkt.

![ screen_shot_2018-06-08at143446 ](assets/screen_shot_2018-06-08at143446.png)

De wijziging blijft bestaan en de component wordt automatisch bijgewerkt met nieuwe weergegevens.

![ screen_shot_2018-06-08at143524 ](assets/screen_shot_2018-06-08at143524.png)

### Implementatie van weercomponent {#weather-component-implementation}

De weercomponent is gebaseerd op een openbaar beschikbare component van het Reageren, genoemd [ Reageer Open Weer ](https://www.npmjs.com/package/react-open-weather). Het is aangepast om als component binnen de Wij.Retail SPA toepassing van de steekproef van het Dagboek te werken.

Hieronder vindt u fragmenten uit de NPM-documentatie van het gebruik van de component React Open Weather.

![ screen_shot_2018-06-08at144723 ](assets/screen_shot_2018-06-08at144723.png) ![ screen_shot_2018-06-08at144215 ](assets/screen_shot_2018-06-08at144215.png)

Het herzien van de code van de aangepaste weercomponent ( `Weather.js`) in de toepassing van het Dagboek Wij.Retail:

* **Lijn 16**: Reageer Open widget van het Weer wordt geladen zoals vereist.
* **Lijn 46**: De `MapTo` functie verwant deze React component aan een overeenkomstige AEM component zodat het in de SPARedacteur kan worden uitgegeven.

* **Lijnen 22-29**: `EditConfig` wordt bepaald, controlerend als de stad is bevolkt en bepalend de waarde als leeg.

* **Lijnen 31-44**: De component van het Weer breidt de `Component` klasse uit en verstrekt de vereiste gegevens zoals die in de NPM gebruiksdocumentatie voor de React Open component van het Weer worden bepaald en geeft de component terug.

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

Hoewel een achterste-eindcomponent reeds moet bestaan, kan de voorste-eindontwikkelaar de React Open component van het Weer in het SPA van het Dagboek gebruiken Wij.Retail met weinig codering.

## Volgende stap {#next-step}

Voor verdere informatie over het ontwikkelen van SPA voor AEM zie het artikel [ Ontwikkelend SPA voor AEM ](/help/sites-developing/spa-architecture.md).
