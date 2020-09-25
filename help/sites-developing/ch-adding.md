---
title: ContextHub toevoegen aan Pagina's en Toegang tot Sporen
description: Voeg ContextHub aan uw pagina's toe om de eigenschappen ContextHub toe te laten en aan de bibliotheken te verbinden JavaScript van ContextHub
translation-type: tm+mt
source-git-commit: a8ba56849f6bb9f0cf6571fc51f4b5cae71620e0
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---


# ContextHub toevoegen aan Pagina&#39;s en Toegang tot Sporen {#adding-contexthub-to-pages-and-accessing-stores}

Voeg ContextHub aan uw pagina&#39;s toe om de eigenschappen ContextHub toe te laten en aan de bibliotheken te verbinden ContextHub Javascript.

De JavaScript-API van ContextHub biedt toegang tot de contextgegevens die door ContextHub worden beheerd. Deze pagina beschrijft kort de belangrijkste eigenschappen van API voor de toegang tot van en het manipuleren van contextgegevens. Volg de koppelingen naar de API-naslagdocumentatie voor gedetailleerde informatie en codevoorbeelden.

## ContextHub toevoegen aan een component Page {#adding-contexthub-to-a-page-component}

Om de eigenschappen ContextHub toe te laten en aan de bibliotheken te verbinden ContextHub Javascript, omvat de `contexthub` component in de `head` sectie van uw pagina. De HTML-code voor uw paginacomponent moet op het volgende voorbeeld lijken:

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

Merk op dat u ook moet vormen of de toolbar ContextHub op de wijze van de Voorproef verschijnt. Zie [het Tonen van en het Verbergen van ContextHub UI](ch-configuring.md#showing-and-hiding-the-contexthub-ui).

## Informatie over ContextHub-winkels {#about-contexthub-stores}

De opslag van ContextHub van het gebruik om contextgegevens voort te zetten. ContextHub verstrekt de volgende types van opslag die de basis van alle opslagtypes vormen:

* [PersistedStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](contexthub-api.md#contexthub-store-persistedstore)

Alle opslagtypen zijn extensies van de [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) klasse. Zie Aangepaste winkels [maken voor informatie over het maken van een nieuw winkeltype](ch-extend.md#creating-custom-store-candidates). Voor informatie over de types van steekproefopslag, zie de Kandidaten [van de Winkel van de](ch-samplestores.md)Steekproef ContextHub.

### Persistentiemodi {#persistence-modes}

De opslag van de Hub van de context gebruikt één van de volgende persistentiemodi:

* **Lokaal:** Gebruikt lokale HTML5-opslag om gegevens te behouden. Lokale opslag blijft in de browser tijdens sessies behouden.
* **Sessie:** Gebruikt HTML5 sessionStorage om gegevens te behouden. De opslag van de zitting wordt voortgeduurd voor de browser zitting en is beschikbaar aan alle browser vensters.
* **Koekje:** Gebruikt de native ondersteuning van de browser voor cookies voor gegevensopslag. De gegevens van het koekje worden verzonden naar en van de server in HTTP- verzoeken.
* **Window.name:** Gebruikt de eigenschap window.name om gegevens te behouden.
* **Geheugen:** Gebruikt een Javascript-object om gegevens te behouden.

Door gebrek, gebruikt de Hub van de Context de Lokale persistentiemodus. Als de browser geen ondersteuning biedt voor lokale HTML5-opslag of deze toestaat, wordt de sessiepersistentie gebruikt. Als de browser HTML5 sessionStorage niet ondersteunt of toestaat, wordt de persistentie Window.name gebruikt.

### Gegevens opslaan {#store-data}

Intern vormen opslaggegevens een boomstructuur, waardoor waarden kunnen worden toegevoegd als primaire typen of complexe objecten. Wanneer u complexe objecten toevoegt aan opslagruimten, vormen de objecteigenschappen vertakkingen in de gegevensstructuur. Het volgende complexe object wordt bijvoorbeeld toegevoegd aan een lege opslaglocatie met de naam location:

```javascript
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

De boomstructuur van de opslaggegevens kan als volgt worden geconceptualiseerd:

```text
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

De boomstructuur bepaalt gegevenspunten in de opslag als sleutel/waardeparen. In het bovenstaande voorbeeld komt de sleutel `/number` overeen met de waarde `321`, en de sleutel `/data/country` komt overeen met de waarde `Switzerland`.

### Objecten bewerken {#manipulating-objects}

ContextHub biedt de [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree) klasse voor het manipuleren van Javascript-objecten. Gebruik de functies van deze klasse voor het manipuleren van voorwerpen Javascript alvorens u hen aan een opslag toevoegt, of nadat u hen van een opslag verkrijgt.

Bovendien biedt de [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json) klasse functies voor het serieel ordenen van objecten met tekenreeksen en het ongedaan maken van tekenreeksen met objecten. Gebruik deze klasse voor het verwerken van JSON-gegevens om browsers te ondersteunen die de functies `JSON.parse` `JSON.stringify` en functies niet native bevatten.

## Interactief werken met ContextHub-winkels {#interacting-with-contexthub-stores}

Gebruik het [`ContextHub`](contexthub-api.md#ui-event-constants) Javascript-object om een winkel als een JavaScript-object op te halen. Nadat u het opslagobject hebt verkregen, kunt u de gegevens in het object bewerken. Gebruik de [`getAllStores`](contexthub-api.md#getallstores) of de [`getStore`](contexthub-api.md#getstore-name) functie om de winkel te verkrijgen.

### Winkelgegevens openen {#accessing-store-data}

De [`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) Javascript-klasse definieert verschillende functies voor interactie met opslaggegevens. Met de volgende functies worden meerdere gegevensitems in objecten opgeslagen en opgehaald:

* [addAllItems](contexthub-api.md#addallitems-tree-options)
* [getTree](contexthub-api.md#gettree-includeinternals)

Afzonderlijke gegevensitems worden opgeslagen als een set sleutel-/waardeparen. Als u waarden wilt opslaan en ophalen, geeft u de bijbehorende sleutel op:

* [getItem](contexthub-api.md#getitem-key)
* [setItem](contexthub-api.md#setitem-key-value-options)

Merk op dat de kandidaten van de douaneopslag extra functies kunnen bepalen die toegang verlenen om gegevens op te slaan.

>[!NOTE]
>
>ContextHub is niet door gebrek zich bewust van momenteel het programma geopend op publiceer servers en dergelijke gebruikers worden beschouwd door ContextHub als &quot;Anoniem.&quot;
>
>U kunt ContextHub bewust maken van het programma geopende gebruikers door de profielopslag te laden. Verwijs hier naar [steekproefcode op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub Event {#contexthub-eventing}

ContextHub omvat een gebeurteniskader dat u toelaat om automatisch te reageren om gebeurtenissen op te slaan. Elk opslagobject bevat een [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing) object dat beschikbaar is als de [`eventing`](contexthub-api.md#eventing) eigenschap van de winkel. Gebruik de [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) functie of [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents) functie om een functie JavaScript aan een archiefgebeurtenis te binden.

## Contexthub gebruiken om cookies te manipuleren {#using-context-hub-to-manipulate-cookies}

De JavaScript-API van de Context Hub biedt ondersteuning voor verschillende browsers voor de verwerking van browsercookies. De [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie) naamruimte definieert verschillende functies voor het maken, bewerken en verwijderen van cookies.

## Opgeloste ContextHub-segmenten bepalen {#determining-resolved-contexthub-segments}

De ContextHub segmentmotor laat u toe om te bepalen welke van de geregistreerde segmenten in de huidige context worden opgelost. Gebruik de functie getResolvedSegments van de [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager) klasse om opgeloste segmenten terug te winnen. Gebruik vervolgens de `getName` of `getPath` functie van de [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment) klasse om op een segment te testen.

### ContextHub-segmenten {#contexthub-segments}

De segmenten van ContextHub worden geïnstalleerd onder de `/conf/<site>/settings/wcm/segments` knoop.

De volgende segmenten worden geïnstalleerd met de [WKND-zelfstudiesite.](getting-started.md)

* zomer
* winter

De regels die worden gebruikt om deze segmenten op te lossen zijn als volgt samengevat:

* Eerst wordt de [geolocatieopslag](ch-samplestores.md#contexthub-geolocation-sample-store-candidate) gebruikt om de breedtegraad van de gebruiker te bepalen.
* Vervolgens bepaalt het maandgegevensitem van de [surferinfo store](ch-samplestores.md#contexthub-surferinfo-sample-store-candidate) welk seizoen het op die breedtegraad is.

>[!WARNING]
>
>De geïnstalleerde segmenten worden verstrekt als verwijzingsconfiguraties om u te helpen uw eigen specifieke configuratie voor uw project bouwen en als zodanig niet direct zouden moeten worden gebruikt.

## Foutopsporing in ContextHub {#debugging-contexthub}

Er zijn een aantal opties voor het zuiveren ContextHub met inbegrip van het produceren van logboeken. Zie [het Vormen ContextHub voor meer informatie.](ch-configuring.md#logging-debug-messages-for-contexthub)

## Zie een Overzicht van het Kader ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub verstrekt een [diagnostische pagina](ch-diagnostics.md) waar u een overzicht van het kader kunt zien ContextHub.
