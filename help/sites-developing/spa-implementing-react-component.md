---
title: Het uitvoeren van een Component van de Reactie voor SPA
description: Dit artikel stelt een voorbeeld van voor hoe te om een eenvoudige, bestaande component van de Reactie aan het werk met de Redacteur van het KUUROORD van Adobe Experience Manager (AEM) aan te passen.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: f4959c12-54c5-403a-9973-7a4ab5f16bed
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
index: false
source-git-commit: 1509ca884e2f9eb931fc7cd416801957459cc4a0
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Het uitvoeren van een Component van de Reactie voor SPA{#implementing-a-react-component-for-spa}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen de inhoud binnen Adobe Experience Manager (AEM) voor een plaats foutloos uitgeven die gebruikend het kader van het KUUROORD wordt gebouwd.

De auteurseigenschap van het KUUROORD biedt een uitvoerige oplossing voor het steunen van SPAs binnen AEM aan. Dit artikel stelt een voorbeeld van voor hoe te om een eenvoudige, bestaande component van de Reactie aan het werk met de Redacteur van AEM SPA aan te passen.

{{ue-over-spa}}

## Inleiding {#introduction}

Dankzij het eenvoudige en lichte contract dat door AEM wordt vereist en tussen SPA en de Redacteur van het KUUROORD wordt gevestigd, is het nemen van een bestaande toepassing van JavaScript en het aanpassen van het voor gebruik met een KUUROORD in AEM een ongecompliceerde kwestie.

Dit artikel illustreert het voorbeeld van de weercomponent op het Web.Retail steekproefSPA van het Dagboek.

U zou met de [ structuur van een toepassing van het KUUROORD voor AEM ](/help/sites-developing/spa-getting-started-react.md) vóór het lezen van dit artikel vertrouwd moeten zijn.

>[!CAUTION]
>Dit document gebruikt [ Wij.Retail app van het Dagboek ](https://github.com/adobe/aem-sample-we-retail-journal) slechts voor demonstratiedoeleinden. Gebruik het niet voor enig projectwerk.
>
>Om het even welk project van AEM zou het [ Archetype van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat de projecten van het KUUROORD gebruikend React of Angular steunt en het KUUROORD SDK gebruikt.

## De component Weer {#the-weather-component}

De weercomponent staat linksboven in de app Web.Retail Journal. Het toont het huidige weer van een bepaalde plaats, trekkend dynamisch weergegevens.

### De widget Weer gebruiken {#using-the-weather-widget}

![ screen_shot_2018-06-08at143224 ](assets/screen_shot_2018-06-08at143224.png)

Wanneer het ontwerpen van inhoud van het KUUROORD in de Redacteur van het KUUROORD, verschijnt de weercomponent zoals een andere component van AEM, volledig met een toolbar, en is editable.

![ screen_shot_2018-06-08at143304 ](assets/screen_shot_2018-06-08at143304.png)

De stad kan in een dialoog worden bijgewerkt enkel als een andere component van AEM.

![ screen_shot_2018-06-08at143446 ](assets/screen_shot_2018-06-08at143446.png)

De wijziging blijft bestaan en de component wordt automatisch bijgewerkt met nieuwe weergegevens.

![ screen_shot_2018-06-08at143524 ](assets/screen_shot_2018-06-08at143524.png)

### Implementatie van weercomponent {#weather-component-implementation}

De weercomponent is gebaseerd op een openbaar beschikbare component van het Reageren, genoemd [ Reageer Open Weer ](https://www.npmjs.com/package/react-open-weather). Het is aangepast om als component binnen de Wij.Retail steekproeftoepassing van het Dagboek van het Dagboek te werken SPA.

Hieronder vindt u fragmenten uit de NPM-documentatie van het gebruik van de component React Open Weather.

![ screen_shot_2018-06-08at144723 ](assets/screen_shot_2018-06-08at144723.png) ![ screen_shot_2018-06-08at144215 ](assets/screen_shot_2018-06-08at144215.png)

Het herzien van de code van de aangepaste weercomponent ( `Weather.js`) in de toepassing van het Dagboek Wij.Retail:

* **Lijn 16**: Reageer Open widget van het Weer wordt geladen zoals vereist.
* **Lijn 46**: De `MapTo` functie past deze React component aan een overeenkomstige component van AEM toe zodat het in de Redacteur van het KUUROORD kan worden uitgegeven.

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

Hoewel een achterste deelcomponent reeds moet bestaan, kan de voorste-eindontwikkelaar de React Open component van het Weer in het Web.Retail Journal SPA met weinig codering gebruiken.

## Volgende stap {#next-step}

Voor verdere informatie over het ontwikkelen van SPAs voor AEM zie het artikel [ Ontwikkelend SPAs voor AEM ](/help/sites-developing/spa-architecture.md).
