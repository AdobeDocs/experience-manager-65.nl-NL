---
title: ContextHub JavaScript API-naslaggids
description: De JavaScript API van ContextHub is beschikbaar aan uw manuscripten wanneer de component ContextHub aan de pagina is toegevoegd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
feature: Context Hub,Developing,Personalization
exl-id: b472d96f-b1a5-40b7-be2a-52f3396f6884
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '4913'
ht-degree: 0%

---

# ContextHub JavaScript API-naslaggids{#contexthub-javascript-api-reference}

De JavaScript API van ContextHub is beschikbaar aan uw manuscripten wanneer de [&#x200B; component ContextHub aan de pagina &#x200B;](/help/sites-developing/ch-adding.md#adding-contexthub-to-a-page-component) is toegevoegd.

## ContextHub-constanten {#contexthub-constants}

Constante waarden die door de ContextHub JavaScript API worden gedefinieerd.

### Gebeurtenisconstanten {#event-constants}

De volgende lijst maakt een lijst van de namengebeurtenissen die voor Winkels ContextHub voorkomen. Zie ook [&#x200B; ContextHub.Utils.Event &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing).

| Constante | Beschrijving | Waarde |
|---|---|---|
| ContextHub.Constants.EVENT_NAMESPACE | ContextHub-gebeurtenisnaamruimte | ch |
| ContextHub.Constants.EVENT_ALL_STORES_READY | Geeft aan dat alle vereiste winkels zijn geregistreerd, geïnitialiseerd en klaar zijn om te worden verbruikt | klaar voor alle winkels |
| ContextHub.Constants.EVENT_STORES_PARTIALLY_READY | Geeft aan dat niet alle winkels binnen een bepaalde tijd zijn geïnitialiseerd | gedeeltelijk gereed voor opslag |
| ContextHub.Constants.EVENT_STORE_REGISTERED | Wordt geactiveerd wanneer een winkel is geregistreerd | in de winkel geregistreerd |
| ContextHub.Constants.EVENT_STORE_READY | Geeft aan dat winkels klaar zijn om te werken. Het wordt teweeggebracht onmiddellijk na registratie, behalve JSONP slaat op, waar het in brand wordt gestoken wanneer het gegeven wordt opgehaald). | geschikt voor de winkel |
| ContextHub.Constants.EVENT_STORE_UPDATED | Wordt geactiveerd wanneer een winkel de persistentie bijwerkt | store-updated |
| ContextHub.Constants.PERSISTENCE_CONTAINER_NAME | Naam van container voor persistentie | ContextHubPersistence |
| ContextHub.Constants.SERVICE_RAW_RESPONSE_KEY | Hiermee wordt de specifieke naam van de persistentiesleutel opgeslagen waar het Raw JSON-resultaat wordt opgeslagen | /_/raw-response |
| ContextHub.Constants.SERVICE_RESPONSE_TIME_KEY | Hiermee wordt een specifieke tijdstempel opgeslagen die aangeeft wanneer JSON-gegevens zijn opgehaald | /_/response-time |
| ContextHub.Constants.SERVICE_LAST_URL_KEY | Hiermee wordt de specifieke URL van de JSON-service opgeslagen die tijdens de laatste aanroep is gebruikt | /_/url |
| ContextHub.Constants.IS_CONTAINER_EXPANDED | Geeft aan of de UI van ContextHub is uitgebreid | /_/container-extended |

### UI-gebeurtenisconstanten {#ui-event-constants}

De volgende lijst maakt een lijst van de namen van gebeurtenissen die voor ContextHub UI voorkomen.

| **Constant** | **Beschrijving** | **Waarde** |
|---|---|---|
| ContextHub.Constants.EVENT_UI_MODE_REGISTERED | Wordt geactiveerd wanneer een modus is geregistreerd | geregistreerd in de modus ui |
| ContextHub.Constants.EVENT_UI_MODE_UNREGISTERED | Wordt geactiveerd wanneer een modus niet is geregistreerd | niet-geregistreerde ui-mode |
| ContextHub.Constants.EVENT_UI_MODE_RENDERER_REGISTERED | Wordt geactiveerd wanneer een modusrenderer is geregistreerd | met ui-modus-renderer geregistreerd |
| ContextHub.Constants.EVENT_UI_MODE_RENDERER_UNREGISTERED | Wordt geactiveerd wanneer een renderer voor een modus niet is geregistreerd | ui-mode-renderer-niet-geregistreerd |
| ContextHub.Constants.EVENT_UI_MODE_ADDED | Wordt geactiveerd wanneer een nieuwe modus wordt toegevoegd | toegevoegd in de modus |
| ContextHub.Constants.EVENT_UI_MODE_REMOVED | Wordt geactiveerd wanneer een modus wordt verwijderd | ui-mode verwijderd |
| ContextHub.Constants.EVENT_UI_MODE_SELECTED | Wordt geactiveerd wanneer een modus door de gebruiker is geselecteerd | geselecteerd in de ui-modus |
| ContextHub.Constants.EVENT_UI_MODULE_REGISTERED | Wordt geactiveerd wanneer een nieuwe module is geregistreerd | met ui-module geregistreerd |
| ContextHub.Constants.EVENT_UI_MODULE_UNREGISTERED | Wordt geactiveerd wanneer een module niet is geregistreerd | niet-geregistreerde ui-module |
| ContextHub.Constants.EVENT_UI_MODULE_RENDERER_REGISTERED | Wordt geactiveerd wanneer een modulerenderer is geregistreerd | met ui-module-renderer geregistreerd |
| ContextHub.Constants.EVENT_UI_MODULE_RENDERER_UNREGISTERED | Wordt geactiveerd wanneer een modulerenderer niet is geregistreerd | ui-module-renderer-niet-geregistreerd |
| ContextHub.Constants.EVENT_UI_MODULE_ADDED | Wordt geactiveerd wanneer een nieuwe module wordt toegevoegd | toegevoegd aan ui-module |
| ContextHub.Constants.EVENT_UI_MODULE_REMOVED | Wordt geactiveerd wanneer een module wordt verwijderd | ui-module-removed |
| ContextHub.Constants.EVENT_UI_CONTAINER_ADDED | Wordt geactiveerd wanneer de UI-container aan de pagina wordt toegevoegd | toegevoegd aan ui-container |
| ContextHub.Constants.EVENT_UI_CONTAINER_OPENED | Wordt geactiveerd wanneer de ContextHub UI wordt geopend | met ui-container geopend |
| ContextHub.Constants.EVENT_UI_CONTAINER_CLOSED | Wordt geactiveerd wanneer de ContextHub-gebruikersinterface is samengevouwen | ui-container-gesloten |
| ContextHub.Constants.EVENT_UI_PROPERTY_MODIFIED | Wordt geactiveerd wanneer een eigenschap wordt gewijzigd | ui-eigenschap-modified |
| ContextHub.Constants.EVENT_UI_RENDERED | Wordt geactiveerd telkens wanneer de ContextHub UI wordt gerenderd (bijvoorbeeld, na een bezitsverandering) | door ui gerenderd |
| ContextHub.Constants.EVENT_UI_INITIALIZED | Wordt geactiveerd wanneer de UI-container wordt geïnitialiseerd | ui-geïnitialiseerd |
| ContextHub.Constants.ACTIVE_UI_MODE | Geeft de actieve UI-modus aan | /_/active-ui-mode |

## ContextHub JavaScript API-naslaggids {#contexthub-javascript-api-reference-2}

Het voorwerp ContextHub verleent toegang tot alle opslag.

### Functies (ContextHub) {#functions-contexthub}

#### getAllStores() {#getallstores}

Retourneert alle geregistreerde ContextHub-winkels.

Deze functie heeft geen parameters.

**Keert** terug

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

* **naam:** de naam waarmee de opslag werd geregistreerd.

**Keert** terug

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

**Keert** terug

Een array van objecten ContextHub.SegmentEngine.Segment.

## ContextHub.Store.Core {#contexthub-store-core}

De basisklasse voor opslag ContextHub.

### Eigenschappen (ContextHub.Store.Core) {#properties-contexthub-store-core}

#### voorkomen {#eventing}

A [&#x200B; ContextHub.Utils.Event &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) voorwerp. Gebruik dit object voor het binden van functies om gebeurtenissen op te slaan. Voor informatie over de standaardwaarde en initialisering, zie [&#x200B; init (naam, config) &#x200B;](/help/sites-developing/contexthub-api.md#init-name-config).

#### name {#name}

De naam van de winkel.

#### volharding {#persistence}

Een ContextHub.Utils.Persistence-object. Zie `[init(name,config)](/help/sites-developing/contexthub-api.md#init-name-config).` voor meer informatie over de standaardwaarde en initialisatie.

### Functies (ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

Voegt een gegevensobject of een array samen met de opslaggegevens. Elk sleutelwaardepaar in het object of de array wordt toegevoegd aan de store (via de functie `setItem` ):

* **Voorwerp:** Sleutels zijn de bezitsnamen.
* **Serie:** Sleutels zijn de serieindexen.

Waarden kunnen objecten zijn.

**Parameters**

* **boom:** (Voorwerp of serie) de gegevens aan de opslag toe te voegen.
* **opties:** (Voorwerp) een facultatief voorwerp van opties dat tot de functie setItem wordt overgegaan. Voor informatie, zie de `options` parameter van [&#x200B; setItem (sleutel, waarde, opties) &#x200B;](/help/sites-developing/contexthub-api.md#setitem-key-value-options).

**Keert** terug

Een `boolean` -waarde:

* De waarde `true` geeft aan dat het gegevensobject is opgeslagen.
* De waarde `false` geeft aan dat de gegevensopslag ongewijzigd blijft.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

Maakt een verwijzing van de ene toets naar de andere. Een sleutel kan niet naar zichzelf verwijzen.

**Parameters**

* **sleutel:** De sleutel die verwijzingen `anotherKey`.

* **een andere sleutel:** zij sleutel die door `key` van verwijzingen wordt voorzien.

**Keert** terug

Een `boolean` -waarde:

* De waarde `true` geeft aan dat de verwijzing is toegevoegd.
* De waarde `false` geeft aan dat er geen verwijzing is toegevoegd.

#### noticeReadiness() {#announcereadiness}

De gebeurtenis `ready` voor deze winkel wordt geactiveerd. Deze functie heeft geen parameters en retourneert geen waarde.

#### clean() {#clean}

Hiermee verwijdert u alle gegevens uit de winkel. De functie heeft geen parameters en geen geretourneerde waarde.

#### getItem(key) {#getitem-key}

Retourneert de waarde die aan een toets is gekoppeld.

**Parameters**

* **sleutel:** (Koord) de sleutel waarvoor om de waarde terug te keren.

**Keert** terug

Een object dat de waarde voor de toets vertegenwoordigt.

#### getKeys(includeInternal) {#getkeys-includeinternals}

Haalt de sleutels uit de opslag op. Naar keuze kunt u de sleutels terugwinnen die intern door het kader ContextHub worden gebruikt.

**Parameters**

* **includeInternal:** Een waarde van `true` omvat intern gebruikte sleutels in de resultaten. Deze toetsen beginnen met het onderstrepingsteken (&quot;_&quot;). De standaardwaarde is `false` .

**Keert** terug

Een array met sleutelnamen ( `string` waarden).

#### getReferences() {#getreferences}

Haalt de verwijzingen uit de opslag op.

**Keert** terug

Een array die naar toetsen verwijst als indexen voor de toetsen waarnaar wordt verwezen:

* Verwijzen naar sleutels komt overeen met de parameter `key` van de functie `addReference` .

* Sleutels waarnaar wordt verwezen, komen overeen met de parameter `anotherKey` van de functie `addReference` .

#### getTree(includeInternal) {#gettree-includeinternals}

Hiermee wordt de gegevensstructuur uit de opslagruimte opgehaald. Naar keuze kunt u de sleutel/waardeparen omvatten die intern door het kader ContextHub worden gebruikt.

**Parameters**

* `includeInternals:` Een waarde van `true` bevat intern gebruikte sleutel-/waardeparen in de resultaten. De sleutels van deze gegevens beginnen met het onderstrepingsteken (&quot;_&quot;) karakter. De standaardwaarde is `false` .

**Keert** terug

Een object dat de gegevensstructuur vertegenwoordigt. De sleutels zijn de bezitsnamen van het voorwerp.

#### init(name, config) {#init-name-config}

Initialiseert de winkel.

* Stelt de opslaggegevens in op een leeg object.
* Hiermee stelt u de opslagverwijzingen in naar een leeg object.
* EventChannel is gegevens:*naam*, waar *naam* de opslagnaam is.

* storeDataKey is /store/*naam*, waar *naam* de opslagnaam is.

**Parameters**

* **naam:** De naam van de opslag.
* **config:** een voorwerp dat configuratieeigenschappen bevat:

   * eventDeferring: de standaardwaarde is 32.
   * gebeurtenis: Het {[&#128279;](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) voorwerp 0} ContextHub.Utils.Event voor deze opslag.  De standaardwaarde is het voorwerp ContextHub.eventing gebruikt.
   * persistence: Het object ContextHub.Utils.Persistence voor deze store. De standaardwaarde is het voorwerp ContextHub.persistence.

#### isEventPaused() {#iseventingpaused}

Bepaalt of de gebeurtenis voor deze opslag wordt gepauzeerd.

**Keert** terug

Een Booleaanse waarde:

* `true`: De gebeurtenis wordt gepauzeerd zodat er geen gebeurtenissen voor deze opslag worden geactiveerd.
* `false`: De gebeurtenis wordt niet gepauzeerd zodat de gebeurtenissen voor deze opslag worden teweeggebracht.

#### pauseEvent() {#pauseeventing}

Pauzeert het voorkomen voor de opslag zodat geen gebeurtenissen worden teweeggebracht. Deze functie vereist geen parameters en retourneert geen waarde.

#### removeItem(sleutel, opties) {#removeitem-key-options}

Hiermee verwijdert u een sleutel-/waardepaar uit de winkel.

Wanneer een toets wordt verwijderd, activeert de functie de gebeurtenis `data` . De gebeurtenisgegevens omvatten de opslagnaam, de naam van de sleutel die is verwijderd, de waarde die is verwijderd, de nieuwe waarde voor de sleutel (null) en het actietype &quot;remove&quot;.

U kunt desgewenst het activeren van de gebeurtenis `data` voorkomen.

**Parameters**

* **sleutel:** (Koord) de naam van de te verwijderen sleutel.
* **opties:** (Voorwerp) een voorwerp van opties. De volgende objecteigenschappen zijn geldig:

   * silent: de waarde `true` voorkomt dat de gebeurtenis `data` wordt geactiveerd. De standaardwaarde is `false` .

**Keert** terug

Een `boolean` -waarde:

* De waarde `true` geeft aan dat het sleutelwaardepaar is verwijderd.
* De waarde `false` geeft aan dat de gegevensopslag ongewijzigd blijft omdat de sleutel niet in de opslagruimte is gevonden.

#### removeReference(key) {#removereference-key}

Hiermee verwijdert u een verwijzing uit de winkel.

**Parameters**

* **sleutel:** de belangrijkste verwijzing om te verwijderen. Deze parameter komt overeen met de parameter `key` van de functie `addReference` .

**Keert** terug

Een `boolean` -waarde:

* De waarde `true` geeft aan dat de verwijzing is verwijderd.
* De waarde `false` geeft aan dat de toets niet geldig was en dat de winkel ongewijzigd is.

#### reset(keepRestatingData) {#reset-keepremainingdata}

Herstelt de aanvankelijke waarden van de blijvende gegevens van de opslag. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de opslag wordt teruggesteld. Deze functie retourneert geen waarde.

De aanvankelijke waarden worden verstrekt in het initialValues bezit van het config voorwerp dat wordt gebruikt om het archiefvoorwerp te concretiseren.

**Parameters**

* **keepRestatingData:** (Boolean) een waarde van waar veroorzaakt dat de niet-aanvankelijke gegevens worden voortgeduurd. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

Herstelt de aanvankelijke waarden van de blijvende gegevens van de opslag. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de opslag wordt teruggesteld. Deze functie retourneert geen waarde.

De aanvankelijke waarden worden verstrekt in het initialValues bezit van het config voorwerp dat wordt gebruikt om het archiefvoorwerp te concretiseren.

**Parameters**

* keepRestatingData: (Boolean) Bij een waarde van true blijven niet-initiële gegevens behouden. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

#### resolveReference(key, retry) {#resolvereference-key-retry}

Hiermee wordt een toets waarnaar wordt verwezen, opgehaald. U kunt desgewenst het aantal herhalingen opgeven dat moet worden gebruikt om de beste overeenkomst op te lossen.

**Parameters**

* **sleutel:** (Koord) de sleutel waarvoor om de verwijzing op te lossen. Deze parameter `key` komt overeen met de parameter `key` van de functie `addReference` .

* **probeer opnieuw:** (Aantal) het aantal herhalingen aan gebruik.

**Keert** terug

Een `string` -waarde die de toets waarnaar wordt verwezen vertegenwoordigt. Wanneer geen verwijzing wordt opgelost, wordt de waarde van de parameter `key` geretourneerd.

#### resumeEvent() {#resumeeventing}

Hervat de gebeurtenis voor deze opslag zodat de gebeurtenissen worden teweeggebracht. Deze functie definieert geen parameters en retourneert geen waarde.

#### setItem(key, value, options) {#setitem-key-value-options}

Voegt een sleutel/waardepaar aan de opslag toe.

De gebeurtenis `data` wordt alleen geactiveerd als de waarde voor de toets afwijkt van de waarde die momenteel voor de toets is opgeslagen. U kunt desgewenst voorkomen dat de gebeurtenis `data` wordt geactiveerd.

Tot de gebeurtenisgegevens behoren de opslagnaam, de sleutel, de vorige waarde, de nieuwe waarde en het actietype `set` .

**Parameters**

* **sleutel:** (Koord) de naam van de sleutel.
* **opties:** (Voorwerp) een voorwerp van opties. De volgende objecteigenschappen zijn geldig:

   * silent: de waarde `true` voorkomt dat de gebeurtenis `data` wordt geactiveerd. De standaardwaarde is `false` .

* **waarde:** (Voorwerp) de waarde aan vennoot met de sleutel.

**Keert** terug

Een `boolean` -waarde:

* De waarde `true` geeft aan dat het gegevensobject is opgeslagen.
* De waarde `false` geeft aan dat de gegevensopslag ongewijzigd blijft.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

Een opslag die JSON-gegevens bevat. De gegevens worden teruggewonnen van de externe dienst JSONP, of naar keuze van de dienst die JSON- gegevens terugkeert. Geef de servicedetails op met de functie [`init`](/help/sites-developing/contexthub-api.md#init-name-config) wanneer u een instantie van deze klasse maakt.

De opslag gebruikt in-geheugenpersistentie (variabele JavaScript). De gegevens van de opslag zijn beschikbaar slechts tijdens het leven van de pagina.

ContextHub.Store.JSONPStore breidt [&#x200B; ContextHub.Store.Core &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-store-core) uit en erft de functies van die klasse.

### Functies (ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

Vormt de details voor het verbinden met de dienst JSONP die dit voorwerp gebruikt. U kunt de bestaande configuratie bijwerken of vervangen. De functie retourneert geen waarde.

**Parameters**

* **serviceConfig:** een voorwerp dat de volgende eigenschappen bevat:

   * host: (String) De servernaam of het IP-adres.
   * jsonp: (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Wanneer waar, &lbrace;callback: &quot;ContextHub.Callbacks.*Object.name* wordt voorwerp toegevoegd aan het service.params voorwerp.
   * params: (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen zijn eigenschapnamen en parameterwaarden zijn eigenschapswaarden.
   * path: (String) The path to the service.
   * poort: (Number) Het poortnummer van de service.
   * secure: (String of Boolean) Determines the protocol to use for the service URL:

      * auto: //
      * true: https://
      * false: https://

* **opheffing:** (Van Boole). Bij de waarde `true` wordt de bestaande serviceconfiguratie vervangen door de eigenschappen van `serviceConfig` . Bij de waarde `false` worden de bestaande serviceconfiguratie-eigenschappen samengevoegd met de eigenschappen van `serviceConfig` .

#### getRawResponse() {#getrawresponse}

Keert de ruwe reactie terug die sinds de laatste vraag aan de dienst JSONP in het voorgeheugen ondergebracht is. De functie vereist geen parameters.

**Keert** terug

Een object dat de onbewerkte reactie vertegenwoordigt.

#### getServiceDetails() {#getservicedetails}

Hiermee wordt het serviceobject voor dit ContextHub.Store.JSONPStore-object opgehaald. Het serviceobject bevat alle informatie die nodig is om de service-URL te maken.

**Keert** terug

Een object met de volgende eigenschappen:

* **gastheer:** (Koord) de servernaam of IP adres.
* **jsonp:** (Van Boole) een waarde van waar wijst erop dat de dienst de dienst JSONP dienst is, anders vals. Wanneer waar, &lbrace;callback: &quot;ContextHub.Callbacks.*Object.name* wordt voorwerp toegevoegd aan het service.params voorwerp.

* **params:** (Voorwerp) parameters URL die als objecten eigenschappen worden vertegenwoordigd. Parameternamen zijn eigenschapnamen en parameterwaarden zijn eigenschapswaarden.
* **weg:** (Koord) de weg aan de dienst.
* **haven:** (Aantal) het havenaantal van de dienst.
* **veilig:** (Koord of Van Boole) bepaalt het protocol voor de dienst URL te gebruiken:

   * auto: //
   * true: https://
   * false: https://

#### getServiceURL(resolve) {#getserviceurl-resolve}

Haalt URL van de dienst JSONP op.

**Parameters**

* **los op:** (Van Boole) bepaalt of om omgezette parameters in URL te omvatten. De waarde `true` lost parameters op en `false` niet.

**Keert** terug

Een `string` -waarde die de service-URL vertegenwoordigt.

#### init(name, config) {#init-name-config-1}

initialiseert het object ContextHub.Store.JSONPStore.

**Parameters**

* **naam:** (Koord) de naam van de opslag.
* **config:** (Voorwerp) een voorwerp dat het de dienstbezit bevat. Het JSONPStore-object gebruikt de eigenschappen van het `service` -object om de URL van de JSONP-service te maken:

   * eventDeferring: 32.
   * gebeurtenis: Het object ContextHub.Utils.Event voor deze winkel. De standaardwaarde is het `ContextHub.eventing` -object.
   * persistence: Het object ContextHub.Utils.Persistence voor deze store. Standaard wordt geheugenpersistentie gebruikt (JavaScript-object).
   * service: (Object)

      * host: (String) De servernaam of het IP-adres.
      * jsonp: (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Wanneer waar, wordt het `{callback: "ContextHub.Callbacks.*Object.name*}` voorwerp toegevoegd aan `service.params`.
      * params: (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen en -waarden zijn respectievelijk namen en waarden van objecteigenschappen.
      * path: (String) The path to the service.
      * poort: (Number) Het poortnummer van de service.
      * secure: (String of Boolean) Determines the protocol to use for the service URL:

         * auto: //
         * true: https://
         * false: https://

      * timeout: (Number) The amount of time to wait for the JSONP service to response before timing out, in milliseconden.
      * ttl: De minimumhoeveelheid tijd in milliseconden die tussen vraag aan de dienst JSONP overgaat. (Zie de [&#x200B; queryService &#x200B;](/help/sites-developing/contexthub-api.md#queryservice-reload) functie).

#### queryService(reload) {#queryservice-reload}

Zoekt de verre dienst JSONP en caches de reactie. Als de tijd sinds de vorige aanroep van deze functie kleiner is dan de waarde van `config.service.ttl` , wordt de service niet aangeroepen en wordt de reactie in de cache niet gewijzigd. Naar keuze, kunt u de dienst dwingen om worden geroepen. Het `config.service.ttl` bezit wordt geplaatst wanneer het roepen van de [&#x200B; init &#x200B;](/help/sites-developing/contexthub-api.md#init-name-config) functie om de opslag te initialiseren.

De gebeurtenis ready wordt geactiveerd wanneer de query is voltooid. Wanneer de URL van de JSONP-service niet is ingesteld, doet de functie niets.

**Parameters**

* **herladen:** (Van Boole) Een waarde van waar verwijdert de caching reactie en dwingt de dienst JSONP om worden geroepen.

#### reset {#reset}

Herstelt de aanvankelijke waarden van de opslag persisted gegevens en roept dan de dienst JSONP. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de aanvankelijke waarden worden teruggesteld. Deze functie retourneert geen waarde.

De aanvankelijke waarden worden verstrekt in het initialValues bezit van het config voorwerp dat wordt gebruikt om het archiefvoorwerp te concretiseren.

**Parameters**

* **keepRestatingData:** (Boolean) een waarde van waar veroorzaakt dat de niet-aanvankelijke gegevens worden voortgeduurd. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

#### resolveParameter(f) {#resolveparameter-f}

Hiermee wordt de opgegeven parameter omgezet.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

ContextHub.Store.PersistedJSONPStore breidt [&#x200B; ContextHub.Store.JSONPStore &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore) uit zodat erft het alle functies van die klasse. Nochtans, worden de gegevens die van de dienst JSONP worden teruggewonnen voortgeduurd volgens de configuratie van persistentie ContextHub. (Zie [&#x200B; persistentiemodi &#x200B;](/help/sites-developing/ch-adding.md#persistence-modes).)

## ContextHub.Store.PersistedStore {#contexthub-store-persistedstore}

ContextHub.Store.PersistedStore breidt [&#x200B; ContextHub.Store.Core &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-store-core) uit zodat erft het alle functies van die klasse. De gegevens in deze opslag worden voortgeduurd volgens de configuratie van persistentie ContextHub.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

ContextHub.Store.SessionStore breidt [&#x200B; ContextHub.Store.Core &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-store-core) uit zodat erft het alle functies van die klasse. De gegevens in deze opslag blijven behouden met in-memory persistance (JavaScript-object).

## ContextHub.UI {#contexthub-ui}

Beheert UI-modules en UI-moduleurs.

### Functies (ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

Registreert een UI modulerenderer met ContextHub. Nadat renderer wordt geregistreerd, kan het worden gebruikt om [&#x200B; modules tot stand te brengen UI &#x200B;](ch-configuring.md#adding-a-ui-module). Gebruik deze functie wanneer u [&#x200B; uitbreidt ContextHub.UI.BaseModuleRenderer &#x200B;](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types) om een renderer van de Module van douaneUI te creëren.

**Parameters**

* **moduleType:** (Koord) het herkenningsteken voor UI module renderer. Als een renderer al is geregistreerd met de opgegeven waarde, is de bestaande renderer niet geregistreerd voordat deze renderer is geregistreerd.
* **renderer:** (Koord) de naam van de klasse die de module UI teruggeeft.
* **dontRender:** (Van Boole) plaatste aan `true` om te verhinderen ContextHub UI wordt teruggegeven nadat renderer wordt geregistreerd. De standaardwaarde is `false` .

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

* **sleutel:** A `String` die de sleutel van het koekje bevat waarvoor u test.

**Keert** terug

De `boolean` -waarde true geeft aan dat het cookie bestaat.

**Voorbeeld**

```
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(filter) {#getallitems-filter}

Retourneert alle cookies met sleutels die overeenkomen met een filter.

**Parameters**

* (Facultatief) **filter:** Criteria voor de aanpassing van koekjessleutels. Als u alle cookies wilt retourneren, geeft u geen waarde op. De volgende typen worden ondersteund:

   * Tekenreeks: de tekenreeks wordt vergeleken met de cookie-toets.
   * Array: elk item in de array is een filter.
   * Een object RegExp: de testfunctie van het object wordt gebruikt om cookies aan te passen.
   * A function: A function that test a cookie key for a match. De functie moet de koekjessleutel als parameter nemen en waar terugkeren als de test een gelijke bevestigt.

**Keert** terug

Een object van cookies. Objecteigenschappen zijn cookie sleutels en sleutelwaarden zijn cookie waarden.

**Voorbeeld**

```
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key) {#getitem-key-1}

Retourneert een cookiewaarde.

**Parameters**

* **sleutel:** De sleutel van het koekje waarvoor u de waarde wilt.

**Keert** terug

De waarde van het cookie of `null` als er geen cookie is gevonden voor de toets.

**Voorbeeld**

```
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys (filter) {#getkeys-filter}

Retourneert een array met de sleutels van bestaande cookies die overeenkomen met een filter.

**Parameters**

* **filter:** Criteria voor de aanpassing van koekjessleutels. De volgende typen worden ondersteund:

   * Tekenreeks: de tekenreeks wordt vergeleken met de cookie-toets.
   * Array: elk item in de array is een filter.
   * Een object RegExp: de testfunctie van het object wordt gebruikt om cookies aan te passen.
   * A function: A function that test a cookie key for a match. De functie moet de cookiesleutel als parameter nemen en `true` terugkeren als de test een gelijke bevestigt.

**Keert** terug

Een array van tekenreeksen waarbij elke tekenreeks de sleutel is van een cookie die overeenkomt met het filter.

**Voorbeeld**

```
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(sleutel, opties) {#removeitem-key-options-1}

Hiermee verwijdert u een cookie. Als u het cookie wilt verwijderen, wordt de waarde ingesteld op een tekenreeks en wordt de vervaldatum ingesteld op de dag vóór de huidige datum.

**Parameters**

* **sleutel:** A `String` waarde die de sleutel van het te verwijderen koekje vertegenwoordigt.

* **opties:** een voorwerp dat bezitswaarden voor het vormen van de koekjesattributen bevat. Zie de functie ` [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)` voor meer informatie. De eigenschap `expires` heeft geen effect.

**Keert** terug

Deze functie retourneert geen waarde.

**Voorbeeld**

```
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(key, value, options) {#setitem-key-value-options-1}

Hiermee maakt u een cookie van de opgegeven sleutel en waarde en voegt u het cookie toe aan het huidige document. U kunt desgewenst opties opgeven waarmee de kenmerken van het cookie worden geconfigureerd.

**Parameters**

* **sleutel:** een Koord dat de sleutel van het koekje bevat.
* **waarde:** Een Koord dat de koekjeswaarde bevat.
* **opties:** (Facultatief) een voorwerp dat om het even welke volgende eigenschappen bevat die de koekjesattributen vormen:

   * verloopt: Een `date` - of `number` -waarde die opgeeft wanneer de cookie vervalt. Een datumwaarde geeft de absolute vervaltijd aan. Een getal (in dagen) stelt de vervaltijd in op de huidige tijd plus het getal. De standaardwaarde is `undefined` .
   * secure: A `boolean` value that specifies the `Secure` attribute of the cookie. De standaardwaarde is `false` .
   * pad: een `String` -waarde die als het `Path` -kenmerk van de cookie moet worden gebruikt. De standaardwaarde is `undefined` .

**Keert** terug

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

Hiermee verwijdert u alle cookies die overeenkomen met een opgegeven filter. Cookies worden afgedekt met de functie getKeys en verwijderd met de functie removeItem.

**Parameters**

* **filter:** het `filter` argument in de vraag aan de `[getKeys](/help/sites-developing/contexthub-api.md#getkeys-filter)` functie te gebruiken.

* **opties:** het `options` argument in de vraag aan de `[removeItem](/help/sites-developing/contexthub-api.md#removeitem-key-options)` functie te gebruiken.

**Keert** terug

Deze functie retourneert geen waarde.

## ContextHub.Utils.Eventing {#contexthub-utils-eventing}

Laat u toe om functies aan ContextHub archiefgebeurtenissen te binden en los te maken. Toegang ContextHub.Utils.Event heeft bezwaar voor een opslag gebruikend het [&#x200B; gebeurtenis &#x200B;](/help/sites-developing/contexthub-api.md#eventing) bezit van de opslag.

### Functies (ContextHub.Utils.Event) {#functions-contexthub-utils-eventing}

#### off (naam, kiezer) {#off-name-selector}

Hiermee wordt de binding van een functie met een gebeurtenis opgeheven.

**Parameters**

* **naam:** De [&#x200B; naam van de gebeurtenis &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) waarvoor u de functie unbinding.

* **selecteur:** de selecteur die bindt. (Zie de `selector` parameter voor [&#x200B; op &#x200B;](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) en [&#x200B; eens &#x200B;](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) functies).

**Keert** terug

Deze functie retourneert geen waarde.

#### on(naam, handler, kiezer, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

Bindt een functie aan een gebeurtenis. De functie wordt aangeroepen telkens wanneer de gebeurtenis plaatsvindt. De functie kan optioneel worden aangeroepen voor gebeurtenissen die zich in het verleden hebben voorgedaan, voordat de binding wordt ingesteld.

**Parameters**

* **naam:** (Koord) de [&#x200B; naam van de gebeurtenis &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) waaraan u de functie bindt.

* **manager:** (Functie) de functie om aan de gebeurtenis te binden.
* **selecteur:** (Koord) een uniek herkenningsteken voor bindt. U hebt de kiezer nodig om de binding te identificeren als u de functie `off` wilt gebruiken om de binding te verwijderen.

* **triggerForPastEvents:** (Boolean) wijst erop of de manager voor gebeurtenissen zou moeten worden uitgevoerd die in het verleden voorkwamen. De waarde `true` roept de handler voor gebeurtenissen uit het verleden aan. De waarde `false` roept de handler voor toekomstige gebeurtenissen aan. De standaardwaarde is `true` .

**Keert** terug

Wanneer het argument `triggerForPastEvents` `true` is, retourneert deze functie een `boolean` -waarde die aangeeft of de gebeurtenis in het verleden heeft plaatsgevonden:

* `true`: De gebeurtenis is in het verleden opgetreden en de handler wordt aangeroepen.
* `false`: De gebeurtenis is niet in het verleden opgetreden.

Als `triggerForPastEvents` `false` is, retourneert deze functie geen waarde.

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

* **naam:** (Koord) de [&#x200B; naam van de gebeurtenis &#x200B;](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) waaraan u de functie bindt.

* **manager:** (Functie) de functie om aan de gebeurtenis te binden.
* **selecteur:** (Koord) een uniek herkenningsteken voor bindt. U hebt de kiezer nodig om de binding te identificeren als u de functie `off` wilt gebruiken om de binding te verwijderen.

* **triggerForPastEvents:** (Boolean) wijst erop of de manager voor gebeurtenissen zou moeten worden uitgevoerd die in het verleden voorkwamen. De waarde `true` roept de handler voor gebeurtenissen uit het verleden aan. De waarde `false` roept de handler voor toekomstige gebeurtenissen aan. De standaardwaarde is `true` .

**Keert** terug

Wanneer het argument `triggerForPastEvents` `true` is, retourneert deze functie een `boolean` -waarde die aangeeft of de gebeurtenis in het verleden heeft plaatsgevonden:

* `true`: De gebeurtenis is in het verleden opgetreden en de handler wordt aangeroepen.
* `false`: De gebeurtenis is niet in het verleden opgetreden.

Als `triggerForPastEvents` `false` is, retourneert deze functie geen waarde.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

Een hulpprogrammaklasse waarmee een object de eigenschappen en methoden van een ander object kan overnemen.

### Functies (ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit (child, parent) {#inherit-child-parent}

Causes an object to inherit the properties and methods of another object.

**Parameters**

* **kind:** (Voorwerp) het voorwerp dat erft.
* **ouder:** (Voorwerp) het voorwerp dat de eigenschappen en de methodes bepaalt die worden geërft.

## ContextHub.Utils.JSON {#contexthub-utils-json}

Biedt functies voor het serialiseren van objecten in JSON-indeling en het deserialiseren van JSON-tekenreeksen in objecten.

### Functies (ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

Parseert een tekenreekswaarde als JSON en zet deze om in een javascript-object.

**Parameters**

* **gegevens:** een koordwaarde in formaat JSON.

**Keert** terug

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

Hiermee serialiseert u JavaScript-waarden en -objecten in tekenreekswaarden in JSON-indeling.

**Parameters**

* **gegevens:** de waarde of het voorwerp om in series te vervaardigen. Deze functie ondersteunt booleaanse waarden, arrays, getallen, tekenreeksen en datumwaarden.

**Keert** terug

De geserialiseerde tekenreekswaarde Wanneer `data` een R `egExp` -waarde is, retourneert deze functie een leeg object. Wanneer `data` een functie is, wordt `undefined` geretourneerd.

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

* **boom:** het voorwerp dat wordt gekopieerd.
* **secondTree:** het voorwerp dat met het exemplaar van het `tree` voorwerp wordt samengevoegd.

**Keert** terug

Een object dat de samengevoegde gegevens bevat.

#### Cleup() {#cleanup}

Maakt een kopie van een object, zoekt en verwijdert items in de gegevensstructuur die geen waarden, null-waarden of ongedefinieerde waarden bevatten en retourneert de kopie.

**Parameters**

* **boom:** het voorwerp aan schoon te maken.

**Keert** terug

Een kopie van de boom die is schoongemaakt.

#### getItem() {#getitem}

Hiermee wordt de waarde opgehaald van een object voor de toets.

**Parameters**

* **boom:** het gegevensvoorwerp.
* **sleutel:** de sleutel voor de waarde die u wilt terugwinnen.

**Keert** terug

De waarde die overeenkomt met de toets. Wanneer de toets onderliggende toetsen heeft, retourneert deze functie een complex object. Wanneer het type van de waarde voor de toets `undefined` is, wordt `null` geretourneerd.

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

De volgende voorbeeldcode retourneert de waarde `260` :

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

* **boom:** het voorwerp waarvan om de sleutels van de gegevensboom terug te winnen.
* **ouder:** (Facultatief) de sleutel van een punt in de gegevensboom waarvoor u de sleutels van de kindpunten wilt terugwinnen.
* **orde:** (Facultatief) een functie die de soortorde van de teruggekeerde sleutels bepaalt. (Zie [&#x200B; Array.prototype.sort &#x200B;](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) op het Netwerk van de Ontwikkelaar Mozilla.)

**Keert** terug

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

Het `ContextHub.Utils.JSON.tree.getKeys(myObject);` -script retourneert de volgende array:

```
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

Maakt een kopie van een bepaald object, verwijdert de opgegeven vertakking uit de gegevensstructuur en retourneert de gewijzigde kopie.

**Parameters**

* structuur: een gegevensobject.
* key: De toets die moet worden verwijderd.

**Keert** terug

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

* Hiermee worden meerdere opeenvolgende slashes tot één slash verkleind.
* Verwijdert witruimte aan het begin en einde van de tekenreeks.
* Splitst het resultaat in een array van tekenreeksen die worden afgebakend door slashes.

Gebruik de resulterende array om een bruikbare sleutel te maken.  **Parameters**

* **sleutel:** `string` om te ontsmetten.

**Keert** terug

Een array van `string` waarden waarbij elke tekenreeks het deel is van de `key` die door slashes is afgebakend. vertegenwoordigt de geanimeerde sleutel. Wanneer de geanimeerde array een lengte van nul heeft, retourneert deze functie `null` .

**Voorbeeld**

Met de volgende code wordt een tekenreeks geanimeerd om de array `["this", "is", "a", "path"]` te maken en wordt vervolgens de sleutel `"/this/is/a/path"` uit de array gegenereerd:

```
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

Voegt een sleutel/waardepaar aan de gegevensboom van een exemplaar van een voorwerp toe. Voor informatie over gegevensbomen, zie [&#x200B; Persistence &#x200B;](/help/sites-developing/contexthub.md#persistence).

**Parameters**

* structuur: een gegevensobject.
* key: De sleutel die aan de waarde moet worden gekoppeld die u toevoegt. De sleutel is het pad naar het item in de gegevensstructuur. Deze functie roept `ContextHub.Utils.JSON.tree.sanitize` aan om de sleutel te ontsmetten alvorens het toe te voegen.
* waarde: de waarde die aan de gegevensstructuur moet worden toegevoegd.

**Keert** terug

Een kopie van het object `tree` dat het paar `key`/ `value` bevat.

**Voorbeeld**

Bekijk de volgende JavaScript-code:

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

* **storeType:** (Koord) de naam van het opslagtype. Zie de parameter `storeType` van de functie [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#contexthub-utils-storecandidates) .

**Keert** terug

Een object van winkeltypen. De objecteigenschappen zijn de namen van opslagtypen en de eigenschapswaarden zijn een array van geregistreerde opslagkandidaten.

#### getStoreFromCandidates(storeType) {#getstorefromcandidates-storetype}

Retourneert een winkeltype van de geregistreerde kandidaten. Als meer dan één opslagtype van de zelfde naam wordt geregistreerd, keert de functie het opslagtype met de hoogste prioriteit terug.

**Parameters**

* storeType: (String) De naam van de opslagkandidaat. Zie de parameter `storeType` van de functie [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) .

**Keert** terug

Een object dat de geregistreerde opslagkandidaat vertegenwoordigt. Als het gewenste opslagtype niet is geregistreerd, wordt een fout gegenereerd.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

Retourneert de namen van de winkeltypen die als opslagkandidaten zijn geregistreerd. Deze functie vereist geen parameters.

**Keert** terug

Een array van tekenreekswaarden, waarbij elke tekenreeks het opslagtype is waarmee een opslagkandidaat is geregistreerd. Zie de parameter `storeType` van de functie [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](/help/sites-developing/contexthub-api.md#contexthub-utils-storecandidates) .

#### registerStoreCandidate(store, storeType, priority, apply) {#registerstorecandidate-store-storetype-priority-applies}

Registreert een opslagvoorwerp als opslagkandidaat gebruikend een naam en een prioriteit.

De prioriteit is een aantal dat op het belang van de zelfde-genoemde opslag wijst. Wanneer een opslagkandidaat met dezelfde naam als een reeds geregistreerde opslagkandidaat wordt geregistreerd, wordt de kandidaat met de hogere prioriteit gebruikt. Wanneer het registreren van een opslagkandidaat, wordt de opslag geregistreerd slechts als de prioriteit hoger is dan de zelfde-genoemde geregistreerde opslagkandidaten.

**Parameters**

* **opslag:** (Voorwerp) het opslagvoorwerp om als opslagkandidaat te registreren.
* **storeType:** (Koord) de naam van de opslagkandidaat. Deze waarde wordt vereist wanneer het creëren van een geval van de opslagkandidaat.
* **prioriteit:** (Aantal) de prioriteit van de opslagkandidaat.
* **is van toepassing:** (Functie) de functie om aan te halen die de toepasselijkheid van de opslag in het huidige milieu evalueert. De functie moet `true` retourneren als de winkel van toepassing is, anders `false` . De standaardwaarde is een functie die waar retourneert: `function() {return true;}`

**Voorbeeld**

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```
