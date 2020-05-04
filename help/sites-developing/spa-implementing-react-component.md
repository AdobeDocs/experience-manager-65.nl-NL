---
title: Het uitvoeren van een Component van de Reactie voor SPA
seo-title: Het uitvoeren van een Component van de Reactie voor SPA
description: Dit artikel stelt een voorbeeld van voor hoe te om een eenvoudige, bestaande component van de Reactie aan het werk met de Redacteur aan te passen AEM SPA.
seo-description: Dit artikel stelt een voorbeeld van voor hoe te om een eenvoudige, bestaande component van de Reactie aan het werk met de Redacteur aan te passen AEM SPA.
uuid: ae6a0a6f-0c3c-4820-9b58-c2a85a9f5291
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 6ed15763-02cc-45d1-adf6-cf9e5e8ebdb0
docset: aem65
translation-type: tm+mt
source-git-commit: 14cc66dfef7bc7781907bdd6093732912c064579

---


# Het uitvoeren van een Component van de Reactie voor SPA{#implementing-a-react-component-for-spa}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend het kader van het KUUROORD wordt gebouwd.

De auteurseigenschap van het KUUROORD biedt een uitvoerige oplossing voor het steunen van SPAs binnen AEM aan. Dit artikel stelt een voorbeeld van voor hoe te om een eenvoudige, bestaande component van de Reactie aan het werk met de Redacteur aan te passen AEM SPA.

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

## Inleiding {#introduction}

Dankzij het eenvoudige en lichte contract dat door AEM wordt vereist en tussen SPA en de Redacteur van het KUUROORD gevestigd, is het nemen van een bestaande toepassing Javascript en het aanpassen van het voor gebruik met een KUUROORD in AEM een ongecompliceerde kwestie.

Dit artikel illustreert het voorbeeld van de weercomponent op het Web.Retail steekproefSPA van het Dagboek.

U zou met de [structuur van een toepassing van het KUUROORD voor AEM](/help/sites-developing/spa-getting-started-react.md) vóór het lezen van dit artikel vertrouwd moeten zijn.

>[!CAUTION]
>Dit document gebruikt de app [](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) We.Retail Journal alleen voor demonstratiedoeleinden. Het mag niet worden gebruikt voor projectwerkzaamheden.
>
>Om het even welk project AEM zou hefboomwerking het Archetype [van het Project van](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, dat de projecten van het KUUROORD gebruikend React of Hoekig steunt en hefboomwerkingen SDK van het KUUROORD.

## De component Weer {#the-weather-component}

De weercomponent staat linksboven in de app Web.Retail Journal. Het toont het huidige weer van een bepaalde plaats, trekkend dynamisch weergegevens.

### De widget Weer gebruiken {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Wanneer het ontwerpen van inhoud van het KUUROORD in de Redacteur van het KUUROORD, verschijnt de weercomponent zoals een andere component AEM, volledig met een toolbar, en is editable.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

De stad kan in een dialoog enkel als om het even welke andere component van AEM worden bijgewerkt.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

De wijziging blijft bestaan en de component wordt automatisch bijgewerkt met nieuwe weergegevens.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implementatie van weercomponent {#weather-component-implementation}

De weercomponent is eigenlijk gebaseerd op een openbaar-beschikbare component van het Reageren, genoemd [React Open Weer](https://www.npmjs.com/package/react-open-weather), die is aangepast om als component binnen de Wij.Retail steekproeftoepassing van het DagboekSPA te werken.

Hieronder vindt u fragmenten uit de NPM-documentatie van het gebruik van de component React Open Weather.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Het herzien van de code van de aangepaste weercomponent ( `Weather.js`) in de toepassing van het Dagboek Wij.Retail:

* **Regel 16**: De widget Open Weer reageren wordt naar wens geladen.
* **Regel 46**: De `MapTo` functie verwant deze React component aan een overeenkomstige component AEM zodat het in de Redacteur van het KUUROORD kan worden uitgegeven.

* **Lijnen 22-29**: De waarde `EditConfig` wordt gedefinieerd, waarbij wordt gecontroleerd of de stad is gevuld en de waarde wordt gedefinieerd als deze leeg is.

* **Lijnen 31-44**: De component Weather breidt de `Component` klasse uit en verstrekt de vereiste gegevens zoals die in de NPM gebruiksdocumentatie voor de React Open component van het Weer worden bepaald en geeft de component terug.

```
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
import {MapTo} from '@adobe/cq-react-editable-components';

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

Hoewel een achterste deelcomponent reeds moet bestaan, kan de front-end ontwikkelaar hefboomwerking de React Open component van het Weer in het Web.Retail Journal SPA met zeer weinig codering.

## Volgende stap {#next-step}

Voor verdere informatie over het ontwikkelen van SPAs voor AEM zie het artikel [het Ontwikkelen van SPAs voor AEM](/help/sites-developing/spa-architecture.md).
