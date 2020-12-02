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

## ContextHub toevoegen aan een component van de Pagina {#adding-contexthub-to-a-page-component}

Om de eigenschappen ContextHub toe te laten en aan de bibliotheken te verbinden ContextHub Javascript, omvat de `contexthub` component in de `head` sectie van uw pagina. De HTML-code voor uw paginacomponent moet op het volgende voorbeeld lijken:

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

Merk op dat u ook moet vormen of de toolbar ContextHub op de wijze van de Voorproef verschijnt. Zie [Het tonen van en het Hiding van ContextHub UI](ch-configuring.md#showing-and-hiding-the-contexthub-ui).

## Informatie over ContextHub-winkels {#about-contexthub-stores}

De opslag van ContextHub van het gebruik om contextgegevens voort te zetten. ContextHub verstrekt de volgende types van opslag die de basis van alle opslagtypes vormen:

* [PersistedStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](contexthub-api.md#contexthub-store-persistedstore)

Alle opslagtypes zijn uitbreidingen van de [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) klasse. Zie [Aangepaste winkels maken](ch-extend.md#creating-custom-store-candidates) voor informatie over het maken van een nieuw winkeltype. Voor informatie over de types van steekproefopslag, zie [Sample ContextHub Store Candidates](ch-samplestores.md).

### Persistentiemodi {#persistence-modes}

De opslag van de Hub van de context gebruikt één van de volgende persistentiemodi:

* **Lokaal:** gebruikt HTML5 localStorage om gegevens te behouden. Lokale opslag blijft in de browser tijdens sessies behouden.
* **Sessie:** gebruikt HTML5 sessionStorage om gegevens te behouden. De opslag van de zitting wordt voortgeduurd voor de browser zitting en is beschikbaar aan alle browser vensters.
* **Cookie:** gebruikt de native ondersteuning van de browser voor cookies voor gegevensopslag. De gegevens van het koekje worden verzonden naar en van de server in HTTP- verzoeken.
* **Window.name:** Gebruikt het window.name bezit om gegevens voort te zetten.
* **Geheugen:** gebruikt een JavaScript-object om gegevens te behouden.

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

De boomstructuur bepaalt gegevenspunten in de opslag als sleutel/waardeparen. In het bovenstaande voorbeeld komt de sleutel `/number` overeen met de waarde `321` en de sleutel `/data/country` komt overeen met de waarde `Switzerland`.

### Objecten {#manipulating-objects} bewerken

ContextHub verstrekt de [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree) klasse voor het manipuleren van voorwerpen Javascript. Gebruik de functies van deze klasse voor het manipuleren van voorwerpen Javascript alvorens u hen aan een opslag toevoegt, of nadat u hen van een opslag verkrijgt.

Daarnaast biedt de klasse [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json) functies voor het serieel ordenen van objecten met tekenreeksen en het ongedaan maken van tekenreeksen met objecten. Gebruik deze klasse voor het verwerken van JSON-gegevens om browsers te ondersteunen die de functies `JSON.parse` en `JSON.stringify` niet native bevatten.

## Interactie met de Opslag {#interacting-with-contexthub-stores} van ContextHub

Gebruik het Javascript-object [`ContextHub`](contexthub-api.md#ui-event-constants) om een winkel als een JavaScript-object op te halen. Nadat u het opslagobject hebt verkregen, kunt u de gegevens in het object bewerken. Gebruik [`getAllStores`](contexthub-api.md#getallstores) of [`getStore`](contexthub-api.md#getstore-name) functie om de opslag te verkrijgen.

### Toegang tot opslaggegevens {#accessing-store-data}

De Javascript-klasse [`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) definieert verschillende functies voor interactie met opslaggegevens. Met de volgende functies worden meerdere gegevensitems in objecten opgeslagen en opgehaald:

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
>U kunt ContextHub bewust maken van het programma geopende gebruikers door de profielopslag te laden. Verwijs naar [steekproefcode op GitHub hier](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub-gebeurtenis {#contexthub-eventing}

ContextHub omvat een gebeurteniskader dat u toelaat om automatisch te reageren om gebeurtenissen op te slaan. Elk opslagvoorwerp bevat een [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing) voorwerp dat als [`eventing`](contexthub-api.md#eventing) bezit van de opslag beschikbaar is. Gebruik de functie [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) of [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents) om een functie JavaScript aan een archiefgebeurtenis te binden.

## Het gebruiken van de Hub van de Context om Koekjes {#using-context-hub-to-manipulate-cookies} te manipuleren

De JavaScript-API van de Context Hub biedt ondersteuning voor verschillende browsers voor de verwerking van browsercookies. De naamruimte [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie) definieert verschillende functies voor het maken, bewerken en verwijderen van cookies.

## Het bepalen van Opgeloste Segmenten ContextHub {#determining-resolved-contexthub-segments}

De ContextHub segmentmotor laat u toe om te bepalen welke van de geregistreerde segmenten in de huidige context worden opgelost. Gebruik de functie getResolvedSegments van de klasse [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager) om opgeloste segmenten terug te winnen. Vervolgens gebruikt u de functie `getName` of `getPath` van de klasse [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment) om te testen op een segment.

### ContextHub-segmenten {#contexthub-segments}

De segmenten van ContextHub worden geïnstalleerd onder de `/conf/<site>/settings/wcm/segments` knoop.

De volgende segmenten worden geïnstalleerd met de [WKND-zelfstudiesite.](getting-started.md)

* zomer
* winter

De regels die worden gebruikt om deze segmenten op te lossen zijn als volgt samengevat:

* Eerst wordt de [geolocation](ch-samplestores.md#contexthub-geolocation-sample-store-candidate) opslag gebruikt om breedte van de gebruiker te bepalen.
* Dan bepaalt het maandgegevenspunt van [surferinfo store](ch-samplestores.md#contexthub-surferinfo-sample-store-candidate) welk seizoen het in die breedtegraad is.

>[!WARNING]
>
>De geïnstalleerde segmenten worden verstrekt als verwijzingsconfiguraties om u te helpen uw eigen specifieke configuratie voor uw project bouwen en als zodanig niet direct zouden moeten worden gebruikt.

## Foutopsporing in ContextHub {#debugging-contexthub}

Er zijn een aantal opties voor het zuiveren ContextHub met inbegrip van het produceren van logboeken. Zie [Het vormen ContextHub voor meer informatie.](ch-configuring.md#logging-debug-messages-for-contexthub)

## Zie een Overzicht van het Kader ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub verstrekt een [diagnostische pagina](ch-diagnostics.md) waar u een overzicht van het kader ContextHub kunt zien.
