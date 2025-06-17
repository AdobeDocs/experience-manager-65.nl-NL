---
title: Samengestelde componenten in SPA's
description: Leer hoe te om uw eigen samengestelde componenten, componenten tot stand te brengen uit andere componenten, die met de Redacteur van de Toepassing van de enig-Pagina van AEM werken (SPA).
exl-id: 02b6c698-d169-467a-9168-9fa6181bed6c
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
index: false
source-git-commit: 1509ca884e2f9eb931fc7cd416801957459cc4a0
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Samengestelde componenten in SPA&#39;s {#composite-components-in-spas}

Samengestelde componenten gebruiken de modulaire aard van AEM-componenten door meerdere basiscomponenten in één component te combineren. Een veelvoorkomend geval voor gebruik van samengestelde componenten is de kaartcomponent, die bestaat uit een combinatie van de afbeelding en tekstcomponenten.

Wanneer samengestelde componenten correct binnen het kader van de Redacteur van de Redacteur van de Toepassing van de Enige Pagina van AEM (SPA) worden uitgevoerd, kunnen de inhoudsauteurs dergelijke componenten slepen en laten vallen zoals zij een andere component, maar hebben nog de capaciteit om elke component afzonderlijk uit te geven die omhoog de samengestelde component maken.

Dit artikel toont aan hoe u een samengestelde component aan uw enige paginatoepassing kunt toevoegen om foutloos met de Redacteur van AEM SPA te werken.

{{ue-over-spa}}

## Hoofdletters gebruiken {#use-case}

Dit artikel gebruikt de typische kaartcomponent als zijn geval van het voorbeeldgebruik. Kaarten vormen een algemeen interface-element voor veel digitale ervaringen en bestaan doorgaans uit een afbeelding en de bijbehorende tekst of bijschrift. Een auteur wil de hele kaart kunnen slepen en neerzetten, maar de afbeelding van de kaart afzonderlijk kunnen bewerken en de bijbehorende tekst aanpassen.

## Vereisten {#prerequisites}

De volgende modellen voor het steunen van de composietgebruiksgevallen vereisen de volgende eerste vereisten.

* Uw AEM-ontwikkelingsexemplaar wordt lokaal uitgevoerd op poort 4502 met een voorbeeldproject.
* U hebt werkende externe Reactie app [ die voor het uitgeven in AEM wordt toegelaten.](spa-edit-external.md)
* React app wordt geladen in de redacteur van AEM [ gebruikend de component RemotePage.](spa-remote-page.md)

## Samengestelde componenten toevoegen aan een SPA {#adding-composite-components}

Er zijn drie verschillende modellen om uw samengestelde component afhankelijk van uw implementatie van het KUUROORD binnen AEM uit te voeren.

* [De component bestaat niet in uw AEM-project.](#component-does-not-exist)
* [De component bestaat in uw AEM-project, maar de vereiste inhoud niet.](#content-does-not-exist)
* [De component en de vereiste inhoud zijn beide aanwezig in uw AEM-project.](#both-exist)

De volgende secties geven voorbeelden van het uitvoeren van elk geval gebruikend de kaartcomponent als voorbeeld.

### De component bestaat niet in uw AEM-project. {#component-does-not-exist}

Begin door de componenten te creëren die de samengestelde component, namelijk componenten voor het beeld en zijn tekst zullen vormen.

1. Maak de tekstcomponent in uw AEM-project.
1. Voeg de overeenkomende `resourceType` uit het project toe in het knooppunt `editConfig` van de component.

   ```text
    resourceType: 'wknd-spa/components/text' 
   ```

1. Gebruik de `withMappable` -hulplijn om bewerking voor de component in te schakelen.

   ```text
   export const AEMText = withMappable(Text, TextEditConfig); 
   ```

De tekstcomponent is vergelijkbaar met het volgende:

```javascript
import React from 'react';
import { withMappable } from '@adobe/aem-react-editable-components';

export const TextEditConfig = {
  emptyLabel: 'Text',
  isEmpty: function(props) {
    return !props || !props.text || props.text.trim().length < 1;
  },
  resourceType: 'wknd-spa/components/text'
};

export const Text = ({ cqPath, richText, text }) => {
  const richTextContent = () => (
    <div className="aem_text"
      id={cqPath.substr(cqPath.lastIndexOf('/') + 1)}
      data-rte-editelement
      dangerouslySetInnerHTML={{__html: text}} />
  );
  return richText ? richTextContent() : (
     <div className="aem_text">{text}</div>
  );
};

export const AEMText = withMappable(Text, TextEditConfig);
```

Als u een afbeeldingscomponent op dezelfde manier maakt, kunt u deze met de component `AEMText` combineren tot een nieuwe kaartcomponent en de afbeeldings- en tekstcomponenten als onderliggende elementen gebruiken.

```javascript
import React from 'react';
import { AEMText } from './AEMText';
import { AEMImage } from './AEMImage';

export const AEMCard = ({ pagePath, itemPath}) => (
  <div>
    <AEMText
       pagePath={pagePath}
       itemPath={`text`} />
    <AEMImage
       pagePath={pagePath}
       itemPath={`image`} />
   </div>
);
```

Deze resulterende samengestelde component kan nu overal in de app worden geplaatst en de component zal plaatsaanduidingen voor een tekst en een afbeeldingscomponent toevoegen in de SPA Editor. In het onderstaande voorbeeld wordt de kaartcomponent toegevoegd aan de thuiscomponent onder de titel.

```javascript
function Home() {
  return (
    <div className="Home">
      <h2>Current Adventures</h2>
      <AEMCard
        pagePath='/content/wknd-spa/home' />
    </div>
  );
}
```

Hiermee wordt een lege plaatsaanduiding voor een tekst en een afbeelding in de editor weergegeven. Wanneer u waarden voor deze waarden invoert via de editor, worden ze opgeslagen op het opgegeven paginapad, dat wil zeggen `/content/wknd-spa/home` op het hoofdniveau met de namen die zijn opgegeven in `itemPath` .

![ Samengestelde kaartcomponent in de redacteur ](assets/composite-card.png)

### De component bestaat in uw AEM-project, maar de vereiste inhoud niet. {#content-does-not-exist}

In dit geval is de kaartcomponent al gemaakt in uw AEM-project met titel- en afbeeldingsknooppunten. De kindknopen (tekst en beeld) hebben de overeenkomstige middeltypes.

![ structuur van de Knoop van de kaartcomponent ](assets/composite-node-structure.png)

U kunt het dan toevoegen aan uw SPA en zijn inhoud terugwinnen.

1. Creeer een overeenkomstige component in SPA voor dit. Zorg ervoor dat de kindcomponenten aan hun overeenkomstige het middeltypes van AEM binnen het project van het KUUROORD in kaart worden gebracht. In dit voorbeeld gebruiken wij het zelfde `AEMText` en `AEMImage` componenten zoals gedetailleerd [ in het vorige geval.](#component-does-not-exist)

   ```javascript
   import React from 'react';
   import { Container, withMappable, MapTo } from '@adobe/aem-react-editable-components';
   import { Text, TextEditConfig } from './AEMText';
   import Image, { ImageEditConfig } from './AEMImage';
   
   export const AEMCard = withMappable(Container, {
     resourceType: 'wknd-spa/components/imagecard'
   });
   
   MapTo('wknd-spa/components/text')(Text, TextEditConfig);
   MapTo('wknd-spa/components/image')(Image, ImageEditConfig);
   ```

1. Aangezien er geen inhoud is voor de component `imagecard` , voegt u de kaart toe aan de pagina. Neem de bestaande container van AEM op in de SPA.
   * Als er een container reeds in het project van AEM is, kunnen wij dit in SPA in plaats daarvan omvatten en de component aan de container van AEM in plaats daarvan toevoegen.
   * Verzeker de kaartcomponent aan het overeenkomstige middeltype in het KUUROORD in kaart wordt gebracht.

   ```javascript
   <ResponsiveGrid
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid' />
   ```

1. Voeg de gecreeerde `wknd-spa/components/imagecard` component aan de toegestane componenten voor de containercomponent [ in het paginamalplaatje toe.](/help/sites-authoring/templates.md)

De component `imagecard` kan nu rechtstreeks aan de container worden toegevoegd in de AEM-editor.

![ Samengestelde kaart in de redacteur ](assets/composite-card.gif)

### De component en de vereiste inhoud zijn beide aanwezig in uw AEM-project. {#both-exist}

Als de inhoud in AEM bestaat, kan het direct in het KUUROORD worden omvat door de weg aan de inhoud te verstrekken.

```javascript
<AEMCard
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid/imagecard' />
```

![ Samengestelde weg in knoopstructuur ](assets/composite-path.png)

De component `AEMCard` is het zelfde als bepaald [ in het vorige gebruiksgeval.](#content-does-not-exist) Hier is de inhoud die op de bovenstaande locatie in het AEM-project is gedefinieerd, opgenomen in de SPA.
