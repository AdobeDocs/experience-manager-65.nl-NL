---
title: Samengestelde onderdelen in SPA
description: Leer hoe u uw eigen samengestelde componenten maakt, componenten die uit andere componenten bestaan, die werken met de AEM Single-Page Application (SPA) Editor.
exl-id: 02b6c698-d169-467a-9168-9fa6181bed6c
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# Samengestelde onderdelen in SPA {#composite-components-in-spas}

Samengestelde componenten gebruiken de modulaire aard van AEM componenten door meerdere basiscomponenten in één component te combineren. Een veelvoorkomend geval voor gebruik van samengestelde componenten is de kaartcomponent, die bestaat uit een combinatie van de afbeelding en tekstcomponenten.

Wanneer samengestelde componenten correct worden geïmplementeerd in het kader van de Editor (SPA) van AEM toepassing voor één pagina, kunnen de auteurs van de inhoud deze componenten slepen en neerzetten, net als elke andere component, maar kunnen ze toch elke component die de samengestelde component vormt afzonderlijk bewerken.

Dit artikel laat zien hoe u een samengestelde component kunt toevoegen aan uw toepassing voor één pagina, zodat u naadloos kunt werken met de AEM SPA Editor.

## Hoofdletters gebruiken {#use-case}

Dit artikel gebruikt de typische kaartcomponent als zijn geval van het voorbeeldgebruik. Kaarten vormen een algemeen interface-element voor veel digitale ervaringen en bestaan doorgaans uit een afbeelding en de bijbehorende tekst of bijschrift. Een auteur wil de hele kaart kunnen slepen en neerzetten, maar de afbeelding van de kaart afzonderlijk kunnen bewerken en de bijbehorende tekst aanpassen.

## Vereisten {#prerequisites}

De volgende modellen voor het steunen van de composietgebruiksgevallen vereisen de volgende eerste vereisten.

* Uw AEM ontwikkelingsinstantie loopt plaatselijk op haven 4502 met een steekproefproject.
* U hebt een werkende externe Reactie-app [ingeschakeld voor bewerking in AEM.](spa-edit-external.md)
* De React-app is geladen in de AEM-editor [met de RemotePage-component.](spa-remote-page.md)

## Samengestelde onderdelen toevoegen aan een SPA {#adding-composite-components}

Er zijn drie verschillende modellen voor het uitvoeren van uw samengestelde component afhankelijk van uw SPA implementatie binnen AEM.

* [De component bestaat niet in uw AEM project.](#component-does-not-exist)
* [De component bestaat in uw AEM project maar de vereiste inhoud niet.](#content-does-not-exist)
* [De component en zijn vereiste inhoud allebei bestaan in uw AEM project.](#both-exist)

De volgende secties geven voorbeelden van het uitvoeren van elk geval gebruikend de kaartcomponent als voorbeeld.

### De component bestaat niet in uw AEM project. {#component-does-not-exist}

Begin door de componenten te creëren die de samengestelde component, namelijk componenten voor het beeld en zijn tekst zullen vormen.

1. Maak de tekstcomponent in uw AEM project.
1. Voeg de bijbehorende `resourceType` van het project in de componenten `editConfig` knooppunt.

   ```text
    resourceType: 'wknd-spa/components/text' 
   ```

1. Gebruik de `withMappable` de hulp om het uitgeven voor de component toe te laten.

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

Als u een afbeeldingscomponent op een vergelijkbare manier maakt, kunt u deze combineren met de opdracht `AEMText` in een nieuwe kaartcomponent, die de beeld en tekstcomponenten gebruiken als kinderen.

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

Dit resulterende samengestelde onderdeel kan nu overal in de app worden geplaatst en de toepassing voegt plaatsaanduidingen voor een tekst en een afbeeldingscomponent toe in de SPA Editor. In het onderstaande voorbeeld wordt de kaartcomponent toegevoegd aan de thuiscomponent onder de titel.

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

Hiermee wordt een lege plaatsaanduiding voor een tekst en een afbeelding in de editor weergegeven. Wanneer u waarden voor deze waarden invoert via de editor, worden ze opgeslagen op het opgegeven paginapad, dat wil zeggen `/content/wknd-spa/home`  op het hoofdniveau met de namen die zijn opgegeven in `itemPath`.

![Samengestelde kaartcomponent in de editor](assets/composite-card.png)

### De component bestaat in uw AEM project maar de vereiste inhoud niet. {#content-does-not-exist}

In dit geval wordt de kaartcomponent al gemaakt in uw AEM project met titel- en afbeeldingsknooppunten. De kindknopen (tekst en beeld) hebben de overeenkomstige middeltypes.

![Nodestructuur van de kaartcomponent](assets/composite-node-structure.png)

U kunt het dan toevoegen aan uw SPA en zijn inhoud terugwinnen.

1. Maak hiervoor een overeenkomende component in de SPA. Zorg ervoor dat de kindcomponenten aan hun overeenkomstige AEM middeltypes binnen het SPA project in kaart worden gebracht. In dit voorbeeld gebruiken we hetzelfde `AEMText` en `AEMImage` componenten als gedetailleerd [in het vorige geval.](#component-does-not-exist)

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

1. Aangezien er geen inhoud is voor de `imagecard` de kaart aan de pagina toevoegen. Neem de bestaande container van AEM op in de SPA.
   * Als er al een container in het AEM project is, kunnen wij dit in de SPA in plaats daarvan omvatten en de component aan de container van AEM in plaats daarvan toevoegen.
   * Zorg ervoor dat de kaartcomponent is toegewezen aan het corresponderende brontype in de SPA.

   ```javascript
   <ResponsiveGrid
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid' />
   ```

1. Het gemaakte object toevoegen `wknd-spa/components/imagecard` component aan de toegestane componenten voor de containercomponent [in de paginasjabloon.](/help/sites-authoring/templates.md)

Nu de `imagecard` kan direct aan de container in de AEM redacteur worden toegevoegd.

![Samengestelde kaart in de editor](assets/composite-card.gif)

### De component en zijn vereiste inhoud allebei bestaan in uw AEM project. {#both-exist}

Als de inhoud in AEM bestaat, kan deze rechtstreeks in de SPA worden opgenomen door het pad naar de inhoud op te geven.

```javascript
<AEMCard
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid/imagecard' />
```

![Samengesteld pad in knooppuntstructuur](assets/composite-path.png)

De `AEMCard` component is hetzelfde als gedefinieerd [in het geval van eerder gebruik.](#content-does-not-exist) Hier is de inhoud die op de bovenstaande locatie in het AEM project is gedefinieerd, opgenomen in de SPA.
