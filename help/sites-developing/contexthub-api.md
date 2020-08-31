---
title: ContextHub JavaScript API-naslaggids
seo-title: ContextHub JavaScript API-naslaggids
description: De JavaScript API van ContextHub is beschikbaar aan uw manuscripten wanneer de component ContextHub aan de pagina is toegevoegd
seo-description: De JavaScript API van ContextHub is beschikbaar aan uw manuscripten wanneer de component ContextHub aan de pagina is toegevoegd
uuid: 296d6c8e-517f-4837-9e86-ae571ea8aa17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 90605f41-1861-4891-a7c8-b8b5918cd5c6
translation-type: tm+mt
source-git-commit: 9a4ae73c08657195da2741cccdb196bd7f7142c9
workflow-type: tm+mt
source-wordcount: '5029'
ht-degree: 2%

---


# ContextHub JavaScript API-naslaggids{#contexthub-javascript-api-reference}

De JavaScript-API van ContextHub is beschikbaar voor uw scripts wanneer de [component ContextHub aan de pagina](/help/sites-developing/ch-adding.md#adding-contexthub-to-a-page-component)is toegevoegd.

## ContextHub-constanten {#contexthub-constants}

Constante waarden die door de JavaScript-API van ContextHub worden gedefinieerd.

### Gebeurtenisconstanten {#event-constants}

De volgende lijst maakt een lijst van de namengebeurtenissen die voor Winkels ContextHub voorkomen. Zie ook [ContextHub.Utils.Event](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing).

| Constante | Beschrijving | Waarde |
|---|---|---|
| ContextHub.Constants.EVENT_NAMESPACE | ContextHub-gebeurtenisnaamruimte | ch |
| ContextHub.Constants.EVENT_ALL_STORES_READY | Geeft aan dat alle vereiste winkels zijn geregistreerd, geïnitialiseerd en klaar zijn om te worden verbruikt | klaar voor alle winkels |
| ContextHub.Constants.EVENT_STORES_PARTIALLY_READY | Geeft aan dat niet alle winkels binnen een bepaalde tijd zijn geïnitialiseerd | gedeeltelijk gereed voor winkels |
| ContextHub.Constants.EVENT_STORE_REGISTERED | Wordt geactiveerd wanneer een winkel is geregistreerd | in de winkel geregistreerd |
| ContextHub.Constants.EVENT_STORE_READY | Geeft aan dat winkels klaar zijn om te werken. Het wordt teweeggebracht onmiddellijk na registratie, behalve JSONP slaat op, waar het in brand wordt gestoken wanneer het gegeven wordt opgehaald). | klaar voor gebruik |
| ContextHub.Constants.EVENT_STORE_UPDATED | Wordt geactiveerd wanneer een winkel de persistentie bijwerkt | store-updated |
| ContextHub.Constants.PERSISTENCE_CONTAINER_NAME | Naam container voor persistentie | ContextHubPersistence |
| ContextHub.Constants.SERVICE_RAW_RESPONSE_KEY | Hiermee wordt de specifieke naam van de persistentiesleutel opgeslagen waar het Raw JSON-resultaat wordt opgeslagen | /_/raw-response |
| ContextHub.Constants.SERVICE_RESPONSE_TIME_KEY | Hiermee wordt een specifieke tijdstempel opgeslagen die aangeeft wanneer JSON-gegevens zijn opgehaald | /_/responstijd |
| ContextHub.Constants.SERVICE_LAST_URL_KEY | Hiermee wordt de specifieke URL van de JSON-service opgeslagen die tijdens de laatste aanroep is gebruikt | /_/url |
| ContextHub.Constants.IS_CONTAINER_EXPANDED | Geeft aan of de UI van ContextHub is uitgebreid | /_/container-extended |

### UI-gebeurtenisconstanten {#ui-event-constants}

De volgende lijst maakt een lijst van de namen van gebeurtenissen die voor ContextHub UI voorkomen.

| **Constante** | **Beschrijving** | **Waarde** |
|---|---|---|
| ContextHub.Constants.EVENT_UI_MODE_REGISTERED | Wordt geactiveerd wanneer een modus is geregistreerd | geregistreerd in de modus ui |
| ContextHub.Constants.EVENT_UI_MODE_UNREGISTERED | Wordt geactiveerd wanneer een modus niet is geregistreerd | niet-geregistreerde ui-mode |
| ContextHub.Constants.EVENT_UI_MODE_RENDERER_REGISTERED | Wordt geactiveerd wanneer een modusrenderer is geregistreerd | met ui-modus-renderer geregistreerd |
| ContextHub.Constants.EVENT_UI_MODE_RENDERER_UNREGISTERED | Wordt geactiveerd wanneer een renderer voor een modus niet is geregistreerd | ui-mode-renderer-niet-geregistreerd |
| ContextHub.Constants.EVENT_UI_MODE_ADDED | Wordt geactiveerd wanneer een nieuwe modus wordt toegevoegd | toegevoegd in de modus ui |
| ContextHub.Constants.EVENT_UI_MODE_REMOVED | Wordt geactiveerd wanneer een modus wordt verwijderd | ui-mode verwijderd |
| ContextHub.Constants.EVENT_UI_MODE_SELECTED | Wordt geactiveerd wanneer een modus door de gebruiker is geselecteerd | geselecteerd in de modus ui |
| ContextHub.Constants.EVENT_UI_MODULE_REGISTERED | Wordt geactiveerd wanneer een nieuwe module is geregistreerd | met ui-module geregistreerd |
| ContextHub.Constants.EVENT_UI_MODULE_UNREGISTERED | Wordt geactiveerd wanneer een module niet is geregistreerd | niet-geregistreerde ui-module |
| ContextHub.Constants.EVENT_UI_MODULE_RENDERER_REGISTERED | Wordt geactiveerd wanneer een modulerenderer is geregistreerd | met ui-module-renderer geregistreerd |
| ContextHub.Constants.EVENT_UI_MODULE_RENDERER_UNREGISTERED | Wordt geactiveerd wanneer een modulerenderer niet is geregistreerd | ui-module-renderer-niet-geregistreerd |
| ContextHub.Constants.EVENT_UI_MODULE_ADDED | Wordt geactiveerd wanneer een nieuwe module wordt toegevoegd | toegevoegd aan de module |
| ContextHub.Constants.EVENT_UI_MODULE_REMOVED | Wordt geactiveerd wanneer een module wordt verwijderd | ui-module verwijderd |
| ContextHub.Constants.EVENT_UI_CONTAINER_ADDED | Wordt geactiveerd wanneer de UI-container aan de pagina wordt toegevoegd | toegevoegd aan ui-container |
| ContextHub.Constants.EVENT_UI_CONTAINER_OPENED | Wordt geactiveerd wanneer de ContextHub UI wordt geopend | met ui-container geopend |
| ContextHub.Constants.EVENT_UI_CONTAINER_CLOSED | Wordt geactiveerd wanneer de ContextHub-gebruikersinterface is samengevouwen | ui-container-gesloten |
| ContextHub.Constants.EVENT_UI_PROPERTY_MODIFIED | Wordt geactiveerd wanneer een eigenschap wordt gewijzigd | ui-eigenschap-modified |
| ContextHub.Constants.EVENT_UI_RENDERED | Wordt geactiveerd telkens wanneer de ContextHub UI wordt gerenderd (bijvoorbeeld na een bezitsverandering) | ui-rendering |
| ContextHub.Constants.EVENT_UI_INITIALIZED | Wordt geactiveerd wanneer de UI-container wordt geïnitialiseerd | ui-geïnitialiseerd |
| ContextHub.Constants.ACTIVE_UI_MODE | Geeft de actieve UI-modus aan | /_/active-ui-mode |

## ContextHub JavaScript API-naslaggids {#contexthub-javascript-api-reference-2}

Het voorwerp ContextHub verleent toegang tot alle opslag.

### Functies (ContextHub) {#functions-contexthub}

#### getAllStores() {#getallstores}

Retourneert alle geregistreerde ContextHub-winkels.

Deze functie heeft geen parameters.

**Geeft als resultaat**

Een voorwerp dat alle opslag ContextHub bevat. Elke opslag is een voorwerp dat de zelfde naam zoals de opslag gebruikt.

**Voorbeeld**

In het volgende voorbeeld worden alle opslagruimten opgehaald en wordt vervolgens de geolocatieopslag opgehaald:

```
var allStores = ContextHub.getAllStores();
var geoloc = allStores.geolocation
```

#### getStore(name) {#getstore-name}

Hiermee wordt een winkel opgehaald als een JavaScript-object.

**Parameters**

* **naam:** De naam waarmee de winkel is geregistreerd.

**Geeft als resultaat**

Een object dat de winkel vertegenwoordigt.

**Voorbeeld**

In het volgende voorbeeld wordt de opslag van de geolocatie opgehaald:

```
var geoloc = ContextHub.getStore("geolocation");
```

## ContextHub.SegmentEngine.Segment {#contexthub-segmentengine-segment}

Vertegenwoordigt een segment ContextHub. Gebruik ContextHub.SegmentEngine.SegmentManager om segmenten te verkrijgen.

### Functies (ContextHub.ContextEngine.Segment) {#functions-contexthub-contextengine-segment}

#### getName() {#getname}

Retourneert de naam van het segment als een tekenreekswaarde.

#### getPath() {#getpath}

Retourneert het pad van de opslagplaats van de segmentdefinitie als een tekenreekswaarde.

## ContextHub.SegmentEngine.SegmentManager {#contexthub-segmentengine-segmentmanager}

Verleent toegang tot segmenten ContextHub.

### Functies (ContextHub.SegmentEngine.SegmentManager) {#functions-contexthub-segmentengine-segmentmanager}

#### getResolvedSegments() {#getresolvedsegments}

Retourneert de segmenten die zijn omgezet in de huidige context. Deze functie heeft geen parameters.

**Geeft als resultaat**

Een array van objecten ContextHub.SegmentEngine.Segment.

## ContextHub.Store.Core {#contexthub-store-core}

De basisklasse voor opslag ContextHub.

### Eigenschappen (ContextHub.Store.Core) {#properties-contexthub-store-core}

#### voorkomen {#eventing}

Een [object ContextHub.Utils.Event](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) . Gebruik dit object voor het binden van functies om gebeurtenissen op te slaan. Voor informatie over de standaardwaarde en initialisatie, zie [init (naam,config)](/help/sites-developing/contexthub-api.md#init-name-config).

#### name {#name}

De naam van de winkel.

#### volharding {#persistence}

Een ContextHub.Utils.Persistence-object. Voor informatie over de standaardwaarde en initialisatie raadpleegt u `[init(name,config)](/help/sites-developing/contexthub-api.md#init-name-config).`

### Functies (ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

Voegt een gegevensobject of een array samen met de opslaggegevens. Elk sleutelwaardepaar in het object of de array wordt toegevoegd aan de store (via de `setItem` functie):

* **Object:** Toetsen zijn de eigenschapnamen.
* **Array:** Toetsen zijn de array-indexen.

Waarden kunnen objecten zijn.

**Parameters**

* **boom:** (Object of array) De gegevens die aan de winkel moeten worden toegevoegd.
* **opties:** (Object) Een optioneel object met opties dat wordt doorgegeven aan de functie setItem. Zie de `options` parameter van [setItem(key,value,options)](/help/sites-developing/contexthub-api.md#setitem-key-value-options)voor meer informatie.

**Geeft als resultaat**

Een `boolean` waarde:

* Een waarde van `true` geeft aan dat het gegevensobject is opgeslagen.
* Een waarde van `false` geeft aan dat de gegevensopslag ongewijzigd blijft.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

Maakt een verwijzing van de ene toets naar de andere. Een sleutel kan niet naar zichzelf verwijzen.

**Parameters**

* **toets:** De sleutel waarnaar wordt verwezen `anotherKey`.

* **andere sleutel:** De toets waarnaar wordt verwezen door `key`.

**Geeft als resultaat**

Een `boolean` waarde:

* De waarde van `true` geeft aan dat de verwijzing is toegevoegd.
* De waarde van `false` geeft aan dat er geen verwijzing is toegevoegd.

#### noticeReadiness() {#announcereadiness}

De `ready` gebeurtenis voor deze winkel wordt geactiveerd. Deze functie heeft geen parameters en retourneert geen waarde.

#### clean() {#clean}

Hiermee verwijdert u alle gegevens uit de winkel. De functie heeft geen parameters en geen geretourneerde waarde.

#### getItem(key) {#getitem-key}

Retourneert de waarde die aan een toets is gekoppeld.

**Parameters**

* **toets:** (String) De sleutel waarvoor de waarde moet worden geretourneerd.

**Geeft als resultaat**

Een object dat de waarde voor de toets vertegenwoordigt.

#### getKeys(includeInternal) {#getkeys-includeinternals}

Haalt de sleutels uit de opslag op. Naar keuze kunt u de sleutels terugwinnen die intern door het kader ContextHub worden gebruikt.

**Parameters**

* **includeInternal:** Een waarde van `true` neemt intern gebruikte sleutels in de resultaten op. Deze toetsen beginnen met het onderstrepingsteken (&quot;_&quot;). De standaardwaarde is `false`.

**Geeft als resultaat**

Een array met sleutelnamen (- `string` waarden).

#### getReferences() {#getreferences}

Haalt de verwijzingen uit de opslag op.

**Geeft als resultaat**

Een array die naar toetsen verwijst als indexen voor de toetsen waarnaar wordt verwezen:

* Verwijzen naar sleutels komt overeen met de `key` parameter van de `addReference` functie.

* Sleutels waarnaar wordt verwezen, komen overeen met de `anotherKey` parameter van de `addReference` functie.

#### getTree(includeInternal) {#gettree-includeinternals}

Hiermee wordt de gegevensstructuur uit de opslagruimte opgehaald. Naar keuze kunt u de sleutel/waardeparen omvatten die intern door het kader ContextHub worden gebruikt.

**Parameters**

* `includeInternals:` Een waarde van `true` omvat intern-gebruikte sleutel/waardeparen in de resultaten. De sleutels van deze gegevens beginnen met het onderstrepingsteken (&quot;_&quot;) karakter. De standaardwaarde is `false`.

**Geeft als resultaat**

Een object dat de gegevensstructuur vertegenwoordigt. De sleutels zijn de bezitsnamen van het voorwerp.

#### init(name, config) {#init-name-config}

Initialiseert de winkel.

* Stelt de opslaggegevens in op een leeg object.
* Hiermee stelt u de opslagverwijzingen in naar een leeg object.
* Het eventChannel is data:*name*, waarbij de *naam* de winkelnaam is.

* De storeDataKey is /store/*name*, waar de *naam* de opslagnaam is.

**Parameters**

* **naam:** De naam van de winkel.
* **config:** Een object dat configuratie-eigenschappen bevat:

   * eventDeferring: De standaardwaarde is 32.
   * gebeurtenis: Het [object ContextHub.Utils.Event](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) voor deze opslag. De standaardwaarde is het voorwerp ContextHub.eventing gebruikt.
   * persistentie: Het object ContextHub.Utils.Persistence voor deze winkel. De standaardwaarde is het voorwerp ContextHub.persistence.

#### isEventPaused() {#iseventingpaused}

Bepaalt of de gebeurtenis voor deze opslag wordt gepauzeerd.

**Geeft als resultaat**

Een Booleaanse waarde:

* `true`: De gebeurtenis wordt gepauzeerd zodat geen gebeurtenissen voor deze opslag worden teweeggebracht.
* `false`: De gebeurtenis wordt niet gepauzeerd zodat de gebeurtenissen voor deze opslag worden teweeggebracht.

#### pauseEvent() {#pauseeventing}

Pauzeert het voorkomen voor de opslag zodat geen gebeurtenissen worden teweeggebracht. Deze functie vereist geen parameters en retourneert geen waarde.

#### removeItem(sleutel, opties) {#removeitem-key-options}

Hiermee verwijdert u een sleutel-/waardepaar uit de winkel.

Wanneer een toets wordt verwijderd, activeert de functie de `data` gebeurtenis. De gebeurtenisgegevens omvatten de opslagnaam, de naam van de sleutel die is verwijderd, de waarde die is verwijderd, de nieuwe waarde voor de sleutel (null) en het actietype &quot;remove&quot;.

U kunt desgewenst het activeren van de `data` gebeurtenis voorkomen.

**Parameters**

* **toets:** (String) De naam van de toets die moet worden verwijderd.
* **opties:** (Object) Een object met opties. De volgende objecteigenschappen zijn geldig:

   * stil: Een waarde van `true` voorkomt dat de `data` gebeurtenis wordt geactiveerd. De standaardwaarde is `false`.

**Geeft als resultaat**

Een `boolean` waarde:

* Een waarde van `true` geeft aan dat het sleutelwaardepaar is verwijderd.
* Een waarde van `false` geeft aan dat de gegevensopslag ongewijzigd is omdat de sleutel niet in de opslag is gevonden.

#### removeReference(key) {#removereference-key}

Hiermee verwijdert u een verwijzing uit de winkel.

**Parameters**

* **toets:** De belangrijkste verwijzing om te verwijderen. Deze parameter komt overeen met de `key` parameter van de `addReference` functie.

**Geeft als resultaat**

Een `boolean` waarde:

* Een waarde van `true` geeft aan dat de verwijzing is verwijderd.
* De waarde van `false` geeft aan dat de toets niet geldig was en dat de winkel ongewijzigd is.

#### reset(keepRestatingData) {#reset-keepremainingdata}

Herstelt de aanvankelijke waarden van de blijvende gegevens van de opslag. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de opslag wordt teruggesteld. Deze functie retourneert geen waarde.

De aanvankelijke waarden worden verstrekt in het initialValues bezit van het config voorwerp dat wordt gebruikt om het archiefvoorwerp te concretiseren.

**Parameters**

* **keepRestatingData:** (Boolean) Bij de waarde true blijven niet-initiële gegevens behouden. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

Herstelt de aanvankelijke waarden van de blijvende gegevens van de opslag. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de opslag wordt teruggesteld. Deze functie retourneert geen waarde.

De aanvankelijke waarden worden verstrekt in het initialValues bezit van het config voorwerp dat wordt gebruikt om het archiefvoorwerp te concretiseren.

**Parameters**

* keepRestatingData: (Boolean) Bij de waarde true blijven niet-initiële gegevens behouden. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

#### resolveReference(key, retry) {#resolvereference-key-retry}

Hiermee wordt een toets waarnaar wordt verwezen, opgehaald. U kunt desgewenst het aantal herhalingen opgeven dat moet worden gebruikt om de beste overeenkomst op te lossen.

**Parameters**

* **toets:** (String) De sleutel waarvoor de verwijzing moet worden opgelost. Deze `key` parameter komt overeen met de `key` parameter van de `addReference` functie.

* **opnieuw proberen:** (Number) Het aantal herhalingen dat moet worden gebruikt.

**Geeft als resultaat**

Een `string` waarde die de referenced sleutel vertegenwoordigt. Wanneer geen verwijzing wordt opgelost, wordt de waarde van de `key` parameter geretourneerd.

#### resumeEvent() {#resumeeventing}

Hervat de gebeurtenis voor deze opslag zodat de gebeurtenissen worden teweeggebracht. Deze functie definieert geen parameters en retourneert geen waarde.

#### setItem(key, value, options) {#setitem-key-value-options}

Voegt een sleutel/waardepaar aan de opslag toe.

De `data` gebeurtenis wordt alleen geactiveerd als de waarde voor de toets anders is dan de waarde die momenteel voor de toets is opgeslagen. U kunt desgewenst het activeren van de `data` gebeurtenis voorkomen.

De gebeurtenisgegevens omvatten de opslagnaam, de sleutel, de vorige waarde, de nieuwe waarde en het actietype van `set`.

**Parameters**

* **toets:** (String) De naam van de toets.
* **opties:** (Object) Een object met opties. De volgende objecteigenschappen zijn geldig:

   * stil: Een waarde van `true` voorkomt dat de `data` gebeurtenis wordt geactiveerd. De standaardwaarde is `false`.

* **waarde:** (Object) De waarde die aan de sleutel moet worden gekoppeld.

**Geeft als resultaat**

Een `boolean` waarde:

* Een waarde van `true` geeft aan dat het gegevensobject is opgeslagen.
* Een waarde van `false` geeft aan dat de gegevensopslag ongewijzigd blijft.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

Een opslag die JSON-gegevens bevat. De gegevens worden teruggewonnen van de externe dienst JSONP, of naar keuze van de dienst die JSON- gegevens terugkeert. Geef de servicedetails op met behulp van de [ `init`](/help/sites-developing/contexthub-api.md#init-name-config) functie wanneer u een instantie van deze klasse maakt.

De opslag gebruikt in-geheugenpersistentie (variabele Javascript). De gegevens van de opslag zijn beschikbaar slechts tijdens het leven van de pagina.

ContextHub.Store.JSONPStore breidt [ContextHub.Store.Core](/help/sites-developing/contexthub-api.md#contexthub-store-core) uit en erft de functies van die klasse.

### Functies (ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

Vormt de details voor het verbinden met de dienst JSONP die dit voorwerp gebruikt. U kunt de bestaande configuratie bijwerken of vervangen. De functie retourneert geen waarde.

**Parameters**

* **serviceConfig:** Een object dat de volgende eigenschappen bevat:

   * host: (Tekenreeks) De servernaam of het IP-adres.
   * jsonp: (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Indien waar (true), wordt de callback: &quot;ContextHub.Callbacks.*Object.name*} wordt toegevoegd aan het object service.params.
   * param: (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen zijn eigenschapnamen en parameterwaarden zijn eigenschapswaarden.
   * pad: (Tekenreeks) Het pad naar de service.
   * poort: (Aantal) het havenaantal van de dienst.
   * veilig: (String of Boolean) Bepaalt het protocol dat voor de service-URL moet worden gebruikt:

      * auto: //
      * true: https://
      * false: https://

* **overschrijven:** (Booleaans). Een waarde van `true` veroorzaakt dat de bestaande de dienstconfiguratie wordt vervangen door de eigenschappen van `serviceConfig`. Een waarde van `false` veroorzaakt dat de bestaande eigenschappen van de de dienstconfiguratie met de eigenschappen van worden samengevoegd `serviceConfig`.

#### getRawResponse() {#getrawresponse}

Keert de ruwe reactie terug die sinds de laatste vraag aan de dienst JSONP in het voorgeheugen ondergebracht is. De functie vereist geen parameters.

**Geeft als resultaat**

Een object dat de onbewerkte reactie vertegenwoordigt.

#### getServiceDetails() {#getservicedetails}

Hiermee wordt het serviceobject voor dit ContextHub.Store.JSONPStore-object opgehaald. Het serviceobject bevat alle informatie die nodig is om de service-URL te maken.

**Geeft als resultaat**

Een object met de volgende eigenschappen:

* **host:** (Tekenreeks) De servernaam of het IP-adres.
* **jsonp:** (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Indien waar (true), wordt de callback: &quot;ContextHub.Callbacks.*Object.name*} wordt toegevoegd aan het object service.params.

* **param:** (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen zijn eigenschapnamen en parameterwaarden zijn eigenschapswaarden.
* **pad:** (Tekenreeks) Het pad naar de service.
* **poort:** (Aantal) het havenaantal van de dienst.
* **veilig:** (String of Boolean) Bepaalt het protocol dat voor de service-URL moet worden gebruikt:

   * auto: //
   * true: https://
   * false: https://

#### getServiceURL(resolve) {#getserviceurl-resolve}

Haalt URL van de dienst JSONP op.

**Parameters**

* **oplossen:** (Boolean) Hiermee wordt bepaald of omgezette parameters in de URL moeten worden opgenomen. Een waarde van `true` lost parameters op, en `false` niet.

**Geeft als resultaat**

Een `string` waarde die de service-URL vertegenwoordigt.

#### init(name, config) {#init-name-config-1}

initialiseert het object ContextHub.Store.JSONPStore.

**Parameters**

* **naam:** (Tekenreeks) De naam van de winkel.
* **config:** (Object) Een object dat de eigenschap service bevat. Het JSONPStore-object gebruikt de eigenschappen van het `service` object om de URL van de JSONP-service te maken:

   * eventDeferring: 32.
   * gebeurtenis: Het object ContextHub.Utils.Event voor deze winkel. De standaardwaarde is het `ContextHub.eventing` object.
   * persistentie: Het object ContextHub.Utils.Persistence voor deze winkel. Standaard wordt geheugenpersistentie gebruikt (Javascript-object).
   * service: (Object)

      * host: (Tekenreeks) De servernaam of het IP-adres.
      * jsonp: (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Indien waar (true), wordt het `{callback: "ContextHub.Callbacks.*Object.name*}`object toegevoegd aan `service.params`.
      * param: (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen en -waarden zijn respectievelijk namen en waarden van objecteigenschappen.
      * pad: (Tekenreeks) Het pad naar de service.
      * poort: (Aantal) het havenaantal van de dienst.
      * veilig: (String of Boolean) Bepaalt het protocol dat voor de service-URL moet worden gebruikt:

         * auto: //
         * true: https://
         * false: https://
      * timeout: (Aantal) de hoeveelheid tijd op de dienst JSONP te wachten om vóór timing uit, in milliseconden te antwoorden.
      * ttl: De minimumhoeveelheid tijd in milliseconden die tussen vraag tot de dienst JSONP overgaat. (Zie de functie [queryService](/help/sites-developing/contexthub-api.md#queryservice-reload) ).


#### queryService(reload) {#queryservice-reload}

Zoekt de verre dienst JSONP en caches de reactie. Als de hoeveelheid tijd sinds de vorige vraag aan deze functie minder dan de waarde van is, wordt de dienst niet geroepen en de caching reactie wordt niet veranderd. `config.service.ttl` Naar keuze, kunt u de dienst dwingen om worden geroepen. De `config.service.ttl`eigenschap wordt ingesteld wanneer de functie [init](/help/sites-developing/contexthub-api.md#init-name-config) wordt aangeroepen om de store te initialiseren.

De gebeurtenis ready wordt geactiveerd wanneer de query is voltooid. Wanneer de URL van de JSONP-service niet is ingesteld, doet de functie niets.

**Parameters**

* **opnieuw laden:** (Boolean) De waarde true verwijdert de reactie in de cache en dwingt de JSONP-service aan te roepen.

#### reset {#reset}

Herstelt de aanvankelijke waarden van de opslag persisted gegevens en roept dan de dienst JSONP. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de aanvankelijke waarden worden teruggesteld. Deze functie retourneert geen waarde.

De aanvankelijke waarden worden verstrekt in het initialValues bezit van het config voorwerp dat wordt gebruikt om het archiefvoorwerp te concretiseren.

**Parameters**

* **keepRestatingData:** (Boolean) Bij de waarde true blijven niet-initiële gegevens behouden. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

#### resolveParameter(f) {#resolveparameter-f}

Hiermee wordt de opgegeven parameter omgezet.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

ContextHub.Store.PersistedJSONPStore breidt [ContextHub.Store.JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore) uit zodat erft het alle functies van die klasse. Nochtans, worden de gegevens die van de dienst JSONP worden teruggewonnen voortgeduurd volgens de configuratie van persistentie ContextHub. (Zie [Persistentiemodi](/help/sites-developing/ch-adding.md#persistence-modes).)

## ContextHub.Store.PersistedStore {#contexthub-store-persistedstore}

ContextHub.Store.PersistedStore breidt [ContextHub.Store.Core](/help/sites-developing/contexthub-api.md#contexthub-store-core) uit zodat erft het alle functies van die klasse. De gegevens in deze opslag worden voortgeduurd volgens de configuratie van persistentie ContextHub.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

ContextHub.Store.SessionStore breidt [ContextHub.Store.Core](/help/sites-developing/contexthub-api.md#contexthub-store-core) uit zodat erft het alle functies van die klasse. De gegevens in deze opslag blijven behouden met in-memory persistance (Javascript-object).

## ContextHub.UI {#contexthub-ui}

Beheert UI-modules en UI-moduleurs.

### Functies (ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

Registreert een UI modulerenderer met ContextHub. Nadat renderer wordt geregistreerd, kan het worden gebruikt om modules [](/help/sites-administering/contexthub-config.md#adding-a-ui-module)tot stand te brengen UI. Gebruik deze functie wanneer u ContextHub.UI.BaseModuleRenderer [](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types) uitbreidt om een renderer van de Module van de douaneUI tot stand te brengen.

**Parameters**

* **moduleType:** (Tekenreeks) De id voor de renderer van de module UI. Als een renderer al is geregistreerd met de opgegeven waarde, is de bestaande renderer niet geregistreerd voordat deze renderer is geregistreerd.
* **renderer:** (String) De naam van de klasse die de module UI rendert.
* **dontRender:** (Boolean) Ingesteld om te voorkomen `true` dat de ContextHub UI wordt gerenderd nadat de renderer is geregistreerd. De standaardwaarde is `false`.

**Voorbeeld**

In het volgende voorbeeld wordt een renderer geregistreerd als het type van de module contexthub.browserinfo.

```
ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());
```

## ContextHub.Utils.Cookie {#contexthub-utils-cookie}

Een hulpprogrammaklasse voor interactie met cookies.

### Functies (ContextHub.Utils.Cookie) {#functions-contexthub-utils-cookie}

#### exists(key) {#exists-key}

Hiermee wordt bepaald of een cookie bestaat.

**Parameters**

* **toets:** Een `String` code die de sleutel bevat van het cookie waarvoor u test.

**Geeft als resultaat**

De `boolean` waarde true geeft aan dat het cookie bestaat.

**Voorbeeld**

```
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(filter) {#getallitems-filter}

Retourneert alle cookies met sleutels die overeenkomen met een filter.

**Parameters**

* (Optioneel) **filter:** Criteria voor het afstemmen van cookies. Geef geen waarde op om alle cookies te retourneren. De volgende typen worden ondersteund:

   * Tekenreeks: De tekenreeks wordt vergeleken met de cookie-toets.
   * Array: Elk item in de array is een filter.
   * Een RegExp-object: De testfunctie van het object wordt gebruikt om cookies aan te passen.
   * Een functie: Een functie die een koekjessleutel voor een gelijke test. De functie moet de koekjessleutel als parameter nemen en waar terugkeren als de test een gelijke bevestigt.

**Geeft als resultaat**

Een object van cookies. Objecteigenschappen zijn cookie sleutels en sleutelwaarden zijn cookie waarden.

**Voorbeeld**

```
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key) {#getitem-key-1}

Retourneert een cookiewaarde.

**Parameters**

* **toets:** De sleutel van het koekje waarvoor u de waarde wilt.

**Geeft als resultaat**

De waarde van het cookie of `null` als er geen cookie is gevonden voor de toets.

**Voorbeeld**

```
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys (filter) {#getkeys-filter}

Retourneert een array met de sleutels van bestaande cookies die overeenkomen met een filter.

**Parameters**

* **filter:** Criteria voor het afstemmen van cookies. De volgende typen worden ondersteund:

   * Tekenreeks: De tekenreeks wordt vergeleken met de cookie-toets.
   * Array: Elk item in de array is een filter.
   * Een RegExp-object: De testfunctie van het object wordt gebruikt om cookies aan te passen.
   * Een functie: Een functie die een koekjessleutel voor een gelijke test. De functie moet de koekjessleutel als parameter nemen en terugkeren `true` als de test een gelijke bevestigt.

**Geeft als resultaat**

Een array van tekenreeksen waarbij elke tekenreeks de sleutel is van een cookie die overeenkomt met het filter.

**Voorbeeld**

```
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(sleutel, opties) {#removeitem-key-options-1}

Hiermee verwijdert u een cookie. Als u het cookie wilt verwijderen, wordt de waarde ingesteld op een tekenreeks en wordt de vervaldatum ingesteld op de dag vóór de huidige datum.

**Parameters**

* **toets:** Een `String` waarde die staat voor de sleutel van het cookie dat moet worden verwijderd.

* **opties:** Een object dat eigenschapwaarden bevat voor het configureren van de cookie-kenmerken. Zie de ` [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)` functie voor meer informatie. De `expires` eigenschap heeft geen effect.

**Geeft als resultaat**

Deze functie retourneert geen waarde.

**Voorbeeld**

```
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(key, value, options) {#setitem-key-value-options-1}

Hiermee maakt u een cookie van de opgegeven sleutel en waarde en voegt u het cookie toe aan het huidige document. U kunt desgewenst opties opgeven waarmee de kenmerken van het cookie worden geconfigureerd.

**Parameters**

* **toets:** Een tekenreeks die de sleutel van het cookie bevat.
* **waarde:** Een tekenreeks die de cookiewaarde bevat.
* **opties:** (Optioneel) Een object dat een van de volgende eigenschappen bevat waarmee de cookie-kenmerken worden geconfigureerd:

   * verloopt: Een `date` of `number` waarde die aangeeft wanneer het cookie vervalt. Een datumwaarde geeft de absolute vervaltijd aan. Een getal (in dagen) stelt de vervaltijd in op de huidige tijd plus het getal. De standaardwaarde is `undefined`.
   * veilig: Een `boolean` waarde die het `Secure` kenmerk van de cookie aangeeft. De standaardwaarde is `false`.
   * pad: Een `String` waarde die als het `Path` kenmerk van het cookie moet worden gebruikt. De standaardwaarde is `undefined`.

**Geeft als resultaat**

Het cookie met de ingestelde waarde.

**Voorbeeld**

```
ContextHub.Utils.Cookie.setItem("name", "mycookie", {
    expires: 3,
    domain: 'localhost',
    path: '/some/directory',
    secure: true
});
```

#### verdwijnt(filter, opties) {#vanish-filter-options}

Hiermee verwijdert u alle cookies die overeenkomen met een opgegeven filter. Cookies worden gevonden met behulp van de functie getKeys en verwijderd met behulp van de functie removeItem.

**Parameters**

* **filter:** Het `filter` argument dat moet worden gebruikt in de aanroep van de `[getKeys](/help/sites-developing/contexthub-api.md#getkeys-filter)` functie.

* **opties:** Het `options` argument dat moet worden gebruikt in de aanroep van de `[removeItem](/help/sites-developing/contexthub-api.md#removeitem-key-options)` functie.

**Geeft als resultaat**

Deze functie retourneert geen waarde.

## ContextHub.Utils.Event {#contexthub-utils-eventing}

Laat u toe om functies aan ContextHub archiefgebeurtenissen te binden en los te maken. Heb toegang tot voorwerpen ContextHub.Utils.Event voor een opslag gebruikend het [eventing](/help/sites-developing/contexthub-api.md#eventing) bezit van de opslag.

### Functies (ContextHub.Utils.Event) {#functions-contexthub-utils-eventing}

#### off (naam, kiezer) {#off-name-selector}

Hiermee wordt de binding van een functie met een gebeurtenis opgeheven.

**Parameters**

* **naam:** De [naam van de gebeurtenis](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) waarvoor u de binding van de functie opheft.

* **kiezer:** De kiezer die de binding aangeeft. (Zie de `selector` parameter voor de functies [on](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) en [once](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) .)

**Geeft als resultaat**

Deze functie retourneert geen waarde.

#### on(naam, handler, kiezer, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

Bindt een functie aan een gebeurtenis. De functie wordt aangeroepen telkens wanneer de gebeurtenis plaatsvindt. De functie kan optioneel worden aangeroepen voor gebeurtenissen die zich in het verleden hebben voorgedaan, voordat de binding wordt ingesteld.

**Parameters**

* **naam:** (String) De [naam van de gebeurtenis](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) waaraan u de functie bindt.

* **handler:** (Functie) De functie die aan de gebeurtenis wordt gebonden.
* **kiezer:** (Tekenreeks) Een unieke id voor de binding. U hebt de kiezer nodig om de binding te identificeren als u de `off` functie wilt gebruiken om de binding te verwijderen.

* **triggerForPastEvents:** (Boolean) Geeft aan of de handler moet worden uitgevoerd voor gebeurtenissen die zich in het verleden hebben voorgedaan. Een waarde van `true` roept de handler voor gebeurtenissen uit het verleden aan. Een waarde van `false` roept de handler voor toekomstige gebeurtenissen aan. De standaardwaarde is `true`.

**Geeft als resultaat**

Wanneer het `triggerForPastEvents` argument is `true`, retourneert deze functie een `boolean` waarde die aangeeft of de gebeurtenis in het verleden heeft plaatsgevonden:

* `true`: De gebeurtenis vond in het verleden plaats en de handler wordt aangeroepen.
* `false`: De gebeurtenis heeft zich in het verleden niet voorgedaan.

Als `triggerForPastEvents` `false`dit zo is, retourneert deze functie geen waarde.

**Voorbeeld**

In het volgende voorbeeld wordt een functie gebonden aan de gebeurtenis data van de geolocation store. De functie vult een element op de pagina met de waarde voor het latitude-gegevensitem uit de winkel.

```
<div class="location">
    <p>latitude: <span id="lat"></span></p>
</div>

<script>
    var geostore = ContextHub.getStore("geolocation");
    geostore.eventing.on(ContextHub.Constants.EVENT_DATA_UPDATE,getlat,"getlat");

    function getlat(){
       latitude = geostore.getItem("latitude");
       $("#lat").html(latitude);
    }
</script>
```

#### once(naam, handler, kiezer, triggerForPastEvents) {#once-name-handler-selector-triggerforpastevents}

Bindt een functie aan een gebeurtenis. De functie wordt slechts eenmaal aangeroepen voor het eerste exemplaar van de gebeurtenis. De functie kan optioneel worden aangeroepen voor de gebeurtenis die in het verleden heeft plaatsgevonden, voordat de binding wordt ingesteld.

**Parameters**

* **naam:** (String) De [naam van de gebeurtenis](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) waaraan u de functie bindt.

* **handler:** (Functie) De functie die aan de gebeurtenis wordt gebonden.
* **kiezer:** (Tekenreeks) Een unieke id voor de binding. U hebt de kiezer nodig om de binding te identificeren als u de `off` functie wilt gebruiken om de binding te verwijderen.

* **triggerForPastEvents:** (Boolean) Geeft aan of de handler moet worden uitgevoerd voor gebeurtenissen die zich in het verleden hebben voorgedaan. Een waarde van `true` roept de handler voor gebeurtenissen uit het verleden aan. Een waarde van `false` roept de handler voor toekomstige gebeurtenissen aan. De standaardwaarde is `true`.

**Geeft als resultaat**

Wanneer het `triggerForPastEvents` argument is `true`, retourneert deze functie een `boolean` waarde die aangeeft of de gebeurtenis in het verleden heeft plaatsgevonden:

* `true`: De gebeurtenis vond in het verleden plaats en de handler wordt aangeroepen.
* `false`: De gebeurtenis heeft zich in het verleden niet voorgedaan.

Als `triggerForPastEvents` `false`dit zo is, retourneert deze functie geen waarde.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

Een hulpprogrammaklasse waarmee een object de eigenschappen en methoden van een ander object kan overnemen.

### Functies (ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit (child, parent) {#inherit-child-parent}

Causes an object to inherit the properties and methods of another object.

**Parameters**

* **kind:** (Object) Het object dat overerft.
* **bovenliggend element:** (Object) Het object dat de eigenschappen en methoden definieert die worden overgeërfd.

## ContextHub.Utils.JSON {#contexthub-utils-json}

Biedt functies voor het serialiseren van objecten in JSON-indeling en het deserialiseren van JSON-tekenreeksen in objecten.

### Functies (ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

Parseert een tekenreekswaarde als JSON en zet deze om in een javascript-object.

**Parameters**

* **gegevens:** Een tekenreekswaarde in JSON-indeling.

**Geeft als resultaat**

Een JavaScript-object.

**Voorbeeld**

De code `ContextHub.Utils.JSON.parse("{'city':'Basel','country':'Switzerland','population':'173330'}");` retourneert het volgende object:

```
Object {
   city: "Basel",
   country: "Switzerland",
   population: 173330
}
```

#### stringify(data) {#stringify-data}

Serializes Javascript-waarden en -objecten in tekenreekswaarden in JSON-indeling.

**Parameters**

* **gegevens:** De waarde of het object waarop serienummering moet worden toegepast. Deze functie ondersteunt booleaanse waarden, arrays, getallen, tekenreeksen en datumwaarden.

**Geeft als resultaat**

De geserialiseerde tekenreekswaarde. Wanneer `data` een R- `egExp` waarde is, retourneert deze functie een leeg object. Wanneer `data` een functie is, retourneert deze `undefined`.

**Voorbeeld**

De volgende code retourneert `"{'city':'Basel','country':'Switzerland','population':'173330'}":`

```
ContextHub.Utils.JSON.stringify({
   city: "Basel",
   country: "Switzerland",
   population: 173330
});
```

## ContextHub.Utils.JSON.tree {#contexthub-utils-json-tree}

Deze klasse vergemakkelijkt de manipulatie van gegevensvoorwerpen die moeten worden opgeslagen of van opslag ContextHub worden teruggewonnen.

### Functies (ContextHub.Utils.JSON.tree) {#functions-contexthub-utils-json-tree}

#### addAllItems() {#addallitems}

Maakt een kopie van een gegevensobject en voegt er vanuit een tweede object de gegevensstructuur aan toe. De functie retourneert de kopie en wijzigt geen van de oorspronkelijke objecten. Wanneer de gegevensstructuren van de twee objecten identieke sleutels bevatten, overschrijft de waarde van het tweede object de waarde van het eerste object.

**Parameters**

* **boom:** Het object dat wordt gekopieerd.
* **secondTree:** Het object dat met de kopie van het `tree` object is samengevoegd.

**Geeft als resultaat**

Een object dat de samengevoegde gegevens bevat.

#### Cleup() {#cleanup}

Maakt een kopie van een object, zoekt en verwijdert items in de gegevensstructuur die geen waarden, null-waarden of ongedefinieerde waarden bevatten en retourneert de kopie.

**Parameters**

* **boom:** Het object dat moet worden gewist.

**Geeft als resultaat**

Een kopie van de boom die is schoongemaakt.

#### getItem() {#getitem}

Hiermee wordt de waarde opgehaald van een object voor de toets A.

**Parameters**

* **boom:** Het gegevensobject.
* **toets:** De sleutel voor de waarde die u wilt terugwinnen.

**Geeft als resultaat**

De waarde die overeenkomt met de toets. Wanneer de toets onderliggende toetsen heeft, retourneert deze functie een complex object. Wanneer het type van de waarde voor de sleutel is `undefined`, `null` is teruggekeerd.

**Voorbeeld**

Bekijk het volgende JavaScript-object:

```
myObject {
  user: {
    location: {
      city: "Basel",
        details: {
          population: 173330,
          elevation: 260
        }
      }
    }
  }
```

De volgende voorbeeldcode retourneert de waarde `260`:

```
ContextHub.Utils.JSON.tree.getItem(myObject, "/user/location/details/elevation");
```

De volgende voorbeeldcode wint de waarde voor een sleutel terug die kindsleutels heeft:

```
ContextHub.Utils.JSON.tree.getItem(myObject, "/user");
```

De functie retourneert het volgende object:

```
Object {
  location: {
    city: "Basel",
    details: {
      population: 173330,
      elevation: 260
    }
  }
}
```

#### getKeys() {#getkeys}

Hiermee worden alle sleutels opgehaald uit de gegevensstructuur van een object. U kunt desgewenst alleen de toetsen van de onderliggende toetsen van een specifieke toets ophalen. U kunt desgewenst ook een sorteervolgorde van de opgehaalde toetsen opgeven.

**Parameters**

* **boom:** Het object waarvan de sleutels van de gegevensstructuur moeten worden opgehaald.
* **bovenliggend element:** (Optioneel) De sleutel van een item in de gegevensstructuur waarvoor u de sleutels van de onderliggende items wilt ophalen.
* **bestelling:** (Optioneel) Een functie die de sorteervolgorde van de geretourneerde toetsen bepaalt. (Zie [Array.prototype.sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) op het Mozilla Developer Network.)

**Geeft als resultaat**

Een array met sleutels.

**Voorbeeld**

Bekijk het volgende object:

```
myObject {
  location: {
    weather: {
      temperature: "28C",
      humidity: "77%",
      precipitation: "10%",
      wind: "8km/h"
    },
    city: "Basel",
    country: "Switzerland",
    longitude: 7.5925727,
    latitude: 47.557421
  }
}
```

Het `ContextHub.Utils.JSON.tree.getKeys(myObject);` script retourneert de volgende array:

```
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

Maakt een kopie van een bepaald object, verwijdert de opgegeven vertakking uit de gegevensstructuur en retourneert de gewijzigde kopie.

**Parameters**

* boom: Een gegevensobject.
* toets: De toets die moet worden verwijderd.

**Geeft als resultaat**

Een kopie van het oorspronkelijke gegevensobject waarbij de toets is verwijderd.

**Voorbeeld**

Bekijk het volgende object:

```
myObject {
  one: {
    foo: "bar",
    two: {
      three: {
        four: {
          five: 5,
          six: 6
        }
      }
    }
  }
}
```

Het volgende voorbeeldmanuscript verwijdert /one/two/three/four tak uit de gegevensboom:

```
myObject = ContextHub.Utils.JSON.tree.removeItem(myObject, "/one/two/three/four");
```

De functie retourneert het volgende object:

```
myObject {
  one: {
    foo: "bar"
  }
}
```

#### sanitizeKey(key) {#sanitizekey-key}

Hiermee worden tekenreekswaarden gesimuleerd zodat deze als toetsen kunnen worden gebruikt. Om een tekenreeks te ontsmetten, voert deze functie de volgende handelingen uit:

* Hiermee worden meerdere opeenvolgende slashes tot één schuine streep verkleind.
* Verwijdert witruimte aan het begin en einde van de tekenreeks.
* Splitst het resultaat in een array van tekenreeksen die worden afgebakend door slashes.

Gebruik de resulterende array om een bruikbare sleutel te maken.  **Parameters**

* **toets:** De kleur `string` die moet worden ontsmet.

**Geeft als resultaat**

Een array van `string` waarden waarbij elke tekenreeks het deel is van de tekenreeks `key` dat door slashes is afgebakend. vertegenwoordigt de geanimeerde sleutel. Als de geanimeerde array een lengte van nul heeft, retourneert deze functie `null`.

**Voorbeeld**

Met de volgende code wordt een tekenreeks geanimeerd om de array te produceren `["this", "is", "a", "path"]`en wordt de sleutel `"/this/is/a/path"` uit de array gegenereerd:

```
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

Hiermee voegt u een sleutel-/waardepaar toe aan de gegevensstructuur van een kopie van een object. Zie [Persistentie](/help/sites-developing/contexthub.md#persistence)voor informatie over gegevensbomen.

**Parameters**

* boom: Een gegevensobject.
* toets: De sleutel die moet worden gekoppeld aan de waarde die u toevoegt. De sleutel is het pad naar het item in de gegevensstructuur. Deze functie roept `ContextHub.Utils.JSON.tree.sanitize` aan om de sleutel te ontsmetten alvorens het toe te voegen.
* waarde: De waarde die aan de gegevensstructuur moet worden toegevoegd.

**Geeft als resultaat**

Een kopie van het `tree` object dat het `key`/- `value` paar bevat.

**Voorbeeld**

Overweeg de volgende Javascript-code:

```
var myObject = {
     user: {
        location: {
           city: "Basel"
           }
        }
     };

var myKey = "/user/location/details";

var myValue = {
      population: 173330,
      elevation: 260
     };

myObject = ContextHub.Utils.JSON.tree.setItem(myObject, myKey, myValue);
```

Het object myObject heeft de volgende waarde:

## ContextHub.Utils.storeCandidates {#contexthub-utils-storecandidates}

Hiermee kunt u winkelkandidaten registreren en geregistreerde winkelkandidaten aanvragen.

### Functies (ContextHub.Utils.storeCandidates) {#functions-contexthub-utils-storecandidates}

#### getRegisteredCandidates(storeType) {#getregisteredcandidates-storetype}

Retourneert de winkeltypen die zijn geregistreerd als opslagkandidaten. Of wint de geregistreerde candicates van een specifiek archieftype of van alle archieftypes terug.

**Parameters**

* **storeType:** (String) De naam van het winkeltype. Zie de `storeType` parameter van de [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#contexthub-utils-storecandidates) functie.

**Geeft als resultaat**

Een object van winkeltypen. De objecteigenschappen zijn de namen van opslagtypen en de eigenschapswaarden zijn een array van geregistreerde opslagkandidaten.

#### getStoreFromCandidates(storeType) {#getstorefromcandidates-storetype}

Retourneert een winkeltype van de geregistreerde kandidaten. Als meer dan één opslagtype van de zelfde naam wordt geregistreerd, keert de functie het opslagtype met de hoogste prioriteit terug.

**Parameters**

* storeType: (String) De naam van de opslagkandidaat. Zie de `storeType` parameter van de [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) functie.

**Geeft als resultaat**

Een object dat de geregistreerde opslagkandidaat vertegenwoordigt. Als het gewenste opslagtype niet is geregistreerd, wordt een fout gegenereerd.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

Retourneert de namen van de winkeltypen die als opslagkandidaten zijn geregistreerd. Deze functie vereist geen parameters.

**Geeft als resultaat**

Een array van tekenreekswaarden, waarbij elke tekenreeks het opslagtype is waarmee een opslagkandidaat is geregistreerd. Zie de `storeType` parameter van de [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#contexthub-utils-storecandidates) functie.

#### registerStoreCandidate(store, storeType, priority, apply) {#registerstorecandidate-store-storetype-priority-applies}

Registreert een opslagvoorwerp als opslagkandidaat gebruikend een naam en een prioriteit.

De prioriteit is een aantal dat op het belang van de zelfde-genoemde opslag wijst. Wanneer een opslagkandidaat met dezelfde naam als een reeds geregistreerde opslagkandidaat wordt geregistreerd, wordt de kandidaat met de hogere prioriteit gebruikt. Wanneer het registreren van een opslagkandidaat, wordt de opslag geregistreerd slechts als de prioriteit hoger is dan de zelfde-genoemde geregistreerde opslagkandidaten.

**Parameters**

* **opslag:** (Object) Het opslagobject dat moet worden geregistreerd als opslagkandidaat.
* **storeType:** (String) De naam van de opslagkandidaat. Deze waarde wordt vereist wanneer het creëren van een geval van de opslagkandidaat.
* **prioriteit:** (Aantal) De prioriteit van de opslagkandidaat.
* **van toepassing:** (Functie) De functie die moet worden aangeroepen die de toepasselijkheid van de opslag in de huidige omgeving evalueert. De functie moet worden geretourneerd `true` als de winkel van toepassing is, en `false` anders. De standaardwaarde is een functie die waar retourneert: `function() {return true;}`

**Voorbeeld**

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```

