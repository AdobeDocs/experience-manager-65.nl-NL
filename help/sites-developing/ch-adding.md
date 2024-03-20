---
title: ContextHub toevoegen aan Pagina's en Toegang tot Sporen
description: Voeg ContextHub aan uw pagina's toe om de eigenschappen ContextHub toe te laten en aan de bibliotheken van JavaScript te verbinden ContextHub
exl-id: ae745af9-b49f-46b9-ab48-2fd256e9a681
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# ContextHub toevoegen aan Pagina&#39;s en Toegang tot Sporen {#adding-contexthub-to-pages-and-accessing-stores}

Voeg ContextHub aan uw pagina&#39;s toe om de eigenschappen ContextHub toe te laten en aan de bibliotheken van JavaScript te verbinden ContextHub.

De JavaScript-API van ContextHub biedt toegang tot de contextgegevens die door ContextHub worden beheerd. Deze pagina beschrijft kort de belangrijkste eigenschappen van API voor de toegang tot van en het manipuleren van contextgegevens. Volg de koppelingen naar de API-naslagdocumentatie voor gedetailleerde informatie en codevoorbeelden.

## ContextHub toevoegen aan een paginacomponent {#adding-contexthub-to-a-page-component}

Om de eigenschappen ContextHub toe te laten en aan de bibliotheken van JavaScript te verbinden ContextHub, omvat `contexthub` in de `head` van uw pagina. De HTML-code voor uw paginacomponent moet op het volgende voorbeeld lijken:

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

Merk op dat u ook moet vormen of de toolbar ContextHub op de wijze van de Voorproef verschijnt. Zie [Het tonen van en het Verbergen van ContextHub UI](ch-configuring.md#showing-and-hiding-the-contexthub-ui).

## Informatie over ContextHub-winkels {#about-contexthub-stores}

De opslag van ContextHub van het gebruik om contextgegevens voort te zetten. ContextHub verstrekt de volgende types van opslag die de basis van alle opslagtypes vormen:

* [PersistedStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](contexthub-api.md#contexthub-store-persistedstore)

Alle winkeltypen zijn extensies van de [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) klasse. Voor informatie over het maken van een winkeltype raadpleegt u [Aangepaste winkels maken](ch-extend.md#creating-custom-store-candidates). Voor informatie over de types van steekproefopslag, zie [Voorbeeld van ContextHub Store-kandidaten](ch-samplestores.md).

### Persistentiemodi {#persistence-modes}

De opslag van de Hub van de context gebruikt één van de volgende persistentiemodi:

* **Lokaal:** Gebruikt HTML5 localStorage om gegevens te behouden. Lokale opslag blijft in de browser tijdens sessies behouden.
* **Sessie:** Gebruikt HTML5 sessionStorage om gegevens te handhaven. De opslag van de zitting wordt voortgeduurd voor de browser zitting en is beschikbaar aan alle browser vensters.
* **Koekje:** Gebruikt de native ondersteuning van de browser voor cookies voor gegevensopslag. De gegevens van het koekje worden verzonden naar en van de server in HTTP- verzoeken.
* **Window.name:** Gebruikt de eigenschap window.name om gegevens te behouden.
* **Geheugen:** Gebruikt een JavaScript-object om gegevens te behouden.

Door gebrek, gebruikt de Hub van de Context de Lokale persistentiemodus. Als de browser geen ondersteuning biedt voor HTML5 localStorage of als dit niet is toegestaan, wordt de sessiepersistentie gebruikt. Als de browser HTML5 sessionStorage niet ondersteunt of toestaat, wordt Window.name persistence gebruikt.

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

De boomstructuur bepaalt gegevenspunten in de opslag als sleutel/waardeparen. In het bovenstaande voorbeeld wordt de toets `/number` komt overeen met de waarde `321`en de sleutel `/data/country` komt overeen met de waarde `Switzerland`.

### Objecten bewerken {#manipulating-objects}

ContextHub biedt de [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree) klasse voor het bewerken van JavaScript-objecten. Gebruik de functies van deze klasse voor het bewerken van JavaScript-objecten voordat u deze toevoegt aan een winkel of nadat u ze hebt opgehaald uit een winkel.

Daarnaast worden de [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json) klasse biedt functies voor het serieel ordenen van objecten op tekenreeksen en het ongedaan maken van tekenreeksen op objecten. Gebruik deze klasse voor het verwerken van JSON-gegevens ter ondersteuning van browsers die zelf geen `JSON.parse` en `JSON.stringify` functies.

## Interactief werken met ContextHub-winkels {#interacting-with-contexthub-stores}

Gebruik de [`ContextHub`](contexthub-api.md#ui-event-constants) JavaScript-object om een winkel te verkrijgen als een JavaScript-object. Nadat u het opslagobject hebt verkregen, kunt u de gegevens in het object bewerken. Gebruik de [`getAllStores`](contexthub-api.md#getallstores) of de [`getStore`](contexthub-api.md#getstore-name) om de winkel te verkrijgen.

### Winkelgegevens openen {#accessing-store-data}

De [`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) JavaScript-klasse definieert verschillende functies voor interactie met opslaggegevens. Met de volgende functies worden meerdere gegevensitems in objecten opgeslagen en opgehaald:

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
>U kunt ContextHub bewust maken van het programma geopende gebruikers door de profielopslag te laden. Zie [voorbeeldcode hier op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub Event {#contexthub-eventing}

ContextHub omvat een gebeurteniskader dat u toelaat om automatisch te reageren om gebeurtenissen op te slaan. Elk winkelobject bevat een [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing) object dat beschikbaar is als de opslagruimte [`eventing`](contexthub-api.md#eventing) eigenschap. Gebruik de [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) of [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents) functie om een JavaScript-functie te binden aan een store-gebeurtenis.

## Contexthub gebruiken om cookies te manipuleren {#using-context-hub-to-manipulate-cookies}

De JavaScript-API van de Context Hub biedt ondersteuning voor verschillende browsers voor de verwerking van browsercookies. De [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie) namespace bepaalt verscheidene functies voor het creëren van, het manipuleren van, en het schrappen van koekjes.

## Opgeloste ContextHub-segmenten bepalen {#determining-resolved-contexthub-segments}

De ContextHub segmentmotor laat u toe om te bepalen welke van de geregistreerde segmenten in de huidige context worden opgelost. Gebruik de functie getResolvedSegments van het [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager) om opgeloste segmenten op te halen. Gebruik vervolgens de `getName` of `getPath` de functie van de [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment) klasse om te testen op een segment.

### ContextHub-segmenten {#contexthub-segments}

ContextHub-segmenten worden onder de `/conf/<site>/settings/wcm/segments` knooppunt.

De volgende segmenten worden geïnstalleerd met de [WKND-zelfstudie.](getting-started.md)

* zomer
* winter

De regels die worden gebruikt om deze segmenten op te lossen zijn als volgt samengevat:

* Eerste [geolocatie](ch-samplestores.md#contexthub-geolocation-sample-store-candidate) store wordt gebruikt om de breedtegraad van de gebruiker te bepalen.
* Vervolgens het maandgegevensitem van het dialoogvenster [surferinfo store](ch-samplestores.md#contexthub-surferinfo-sample-store-candidate) bepaalt welk seizoen het in die breedtegraad is.

>[!WARNING]
>
>De geïnstalleerde segmenten worden verstrekt als verwijzingsconfiguraties om u te helpen uw eigen specifieke configuratie voor uw project bouwen. Niet direct gebruiken.

## Foutopsporing in ContextHub {#debugging-contexthub}

Er zijn verscheidene opties voor het zuiveren ContextHub met inbegrip van het produceren van logboeken. Zie [Het vormen ContextHub voor meer informatie.](ch-configuring.md#logging-debug-messages-for-contexthub)

## Zie een Overzicht van het Kader ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub biedt een [diagnosepagina](ch-diagnostics.md) waar u een overzicht van het kader kunt zien ContextHub.
