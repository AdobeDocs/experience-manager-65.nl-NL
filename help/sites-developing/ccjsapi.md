---
title: JavaScript-API voor clientcontext
seo-title: JavaScript-API voor clientcontext
description: De JavaScript-API voor clientcontext
seo-description: De JavaScript-API voor clientcontext
uuid: be58998c-f23e-4768-8394-1f1ad3994c4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: a6e5810b-dac5-4137-93cf-5d8d53cacc49
feature: Context Hub
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '3165'
ht-degree: 4%

---


# JavaScript-API{#client-context-javascript-api} voor clientcontext

## CQ_Analytics.ClientContextMgr {#cq-analytics-clientcontextmgr}

Het object CQ_Analytics.ClientContextMgr is een singleton dat een set zelfgeregistreerde sessiewinkels bevat en methoden biedt voor het registreren, voortzetten en beheren van de sessiewinkels.

Breidt CQ_Analytics.PersistedSessionStore uit.

### Methoden {#methods}

#### getRegisteredStore(name) {#getregisteredstore-name}

Retourneert een sessiearchief met een opgegeven naam. Zie ook [Toegang tot een Sessiewinkel](/help/sites-developing/client-context.md#accessing-session-stores).

**Parameters**

* naam: Tekenreeks. De naam van de sessiewinkel.

**Geeft als resultaat**

Een CQ_Analytics.SessionStore-object dat de zittingsopslag van de opgegeven naam vertegenwoordigt. Retourneert `null` wanneer er geen opslag met de opgegeven naam bestaat.

#### register(sessionstore) {#register-sessionstore}

Registreert een zittingsopslag met de Context van de Cliënt. Hiermee worden gebeurtenissen in het opslagregister en de opslagperiode na voltooiing geactiveerd.

**Parameters**

* sessionstore: CQ_Analytics.SessionStore. Het sessieopslagobject dat moet worden geregistreerd.

**Geeft als resultaat**

Geen geretourneerde waarde.

## CQ_Analytics.ClientContextUtils {#cq-analytics-clientcontextutils}

Verstrekt methodes om op de activering en registratie van de zittingsopslag te luisteren. Zie ook [Controleren of een Sessiewinkel is gedefinieerd en geïnitialiseerd](/help/sites-developing/client-context.md#checking-that-a-session-store-is-defined-and-initialized).

### Methoden {#methods-1}

#### onStoreInitialized(storeName, callback, delay) {#onstoreinitialized-storename-callback-delay}

Registreert een callback functie die wordt geroepen wanneer een zittingsopslag wordt geïnitialiseerd. Voor opslag die verscheidene tijden worden geïnitialiseerd, specificeer een callback vertraging zodat de callback functie slechts eenmaal wordt geroepen:

* Wanneer de opslag tijdens de vertragingsperiode van een vorige initialisering wordt geïnitialiseerd, wordt de vorige functievraag geannuleerd, en de functie wordt opnieuw geroepen voor de huidige initialisering.
* Als de vertragingsperiode vervalt voordat een volgende initialisatie plaatsvindt, wordt de callback-functie twee keer uitgevoerd.

Een sessiewinkel is bijvoorbeeld gebaseerd op een JSON-object en opgehaald via een JSON-aanvraag. De volgende initialisatiescenario&#39;s zijn mogelijk:

* De aanvraag is voltooid, gegevens worden opgehaald en in de winkel geladen. In dit geval vindt de initialisatie eenmaal plaats.
* De aanvraag is mislukt (timeout). In dit geval gebeurt initialisatie niet en zijn er geen gegevens in de opslag.
* De opslag wordt vooraf gevuld met standaardwaarden (init-eigenschappen), maar de aanvraag mislukt (timeout). Er is slechts één initialisatie met standaardwaarden.
* De winkel is vooraf gevuld.

Wanneer de vertraging aan `true` of een aantal milliseconden wordt geplaatst, wacht de methode alvorens de callback methode te roepen. Als een andere initialisatiegebeurtenis wordt geactiveerd voordat de vertraging wordt doorgegeven, wordt gewacht totdat de vertragingstijd is overschreden zonder initialisatiegebeurtenis. Dit laat het wachten op een tweede initialiseringsgebeurtenis toe om worden teweeggebracht en roept de callback functie in het meest optimale geval.

**Parameters**

* storeName: Tekenreeks. De naam van het sessiearchief om de listener toe te voegen.
* callback: Functie. De functie om op archiefinitialisatie te roepen.
* vertraging: Boolean of Number. De hoeveelheid tijd om de vraag aan de callback functie, in milliseconden te vertragen. Een booleaanse waarde van `true` gebruikt de standaardvertraging van `200 ms`. Een booleaanse waarde van `false` of een negatief getal zorgt ervoor dat geen vertraging wordt gebruikt.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### onStoreRegistered(storeName, callback) {#onstoreregistered-storename-callback}

Registreert een callback functie die wordt geroepen wanneer een zittingsopslag wordt geregistreerd. De registergebeurtenis vindt plaats wanneer een winkel is geregistreerd op [CQ_Analytics.ClientContextMgr](#cq-analytics-clientcontextmgr).

**Parameters**

* storeName: Tekenreeks. De naam van het sessiearchief om de listener toe te voegen.
* callback: Functie. De functie om op archiefinitialisatie te roepen.

**Geeft als resultaat**

Geen geretourneerde waarde.

## CQ_Analytics.JSONPStore {#cq-analytics-jsonpstore}

Een niet-voortgezette sessiewinkel die JSON-gegevens bevat. De gegevens worden teruggewonnen van de externe dienst JSONP. Gebruik de methode `getInstance` of `getRegisteredInstance` om een instantie van deze klasse te creëren.

Breidt CQ_Analytics.JSONStore uit.

### Eigenschappen {#properties}

Zie CQ_Analytics.JSONStore en CQ_Analytics.SessonStore voor geërfte eigenschappen.

### Methoden {#methods-2}

Zie ook CQ_Analytics.JSONStore en CQ_Analytics.SessonStore voor geërfte methodes.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback}

Maakt een CQ_Analytics.JSONPStore-object.

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: Tekenreeks. De URL van de JSONP-service
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* deferLoading: (Optioneel) Booleaans. De waarde true voorkomt dat de JSONP-service bij het maken van objecten wordt aangeroepen. Een waarde van vals veroorzaakt de dienst JSONP om worden geroepen.
* loadingCallback: (Optioneel) String. De naam van de functie om voor verwerking het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Geeft als resultaat**

Het nieuwe object CQ_Analytics.JSONPStore of null als storeName null is.

#### getServiceURL() {#getserviceurl}

Hiermee wordt de URL opgehaald van de JSONP-service die dit object gebruikt om JSON-gegevens op te halen.

**Parameters**

Geen.

**Geeft als resultaat**

Een tekenreeks die de service-URL vertegenwoordigt, of null als er geen service-URL is geconfigureerd.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback}

Roept de dienst JSONP aan. JSONP URL is de dienst URL die met een bepaalde callback functienaam wordt achtervoegd.

**Parameters**

* serviceURL: (Optioneel) String. De JSONP-service die moet worden aangeroepen. De waarde null zorgt ervoor dat de reeds geconfigureerde service-URL wordt gebruikt. Een waarde die niet gelijk is aan null, stelt de JSONP-service in die voor dit object moet worden gebruikt. (Zie setServiceURL.)
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback}

Maakt een CQ_Analytics.JSONPStore-object en registreert de winkel met Client-context.

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: (Optioneel) String. De URL van de JSONP-service.
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Geeft als resultaat**

Het geregistreerde object CQ_Analytics.JSONPStore.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl}

Plaatst URL van de dienst JSONP voor het terugwinnen van JSON- gegevens te gebruiken.

**Parameters**

* serviceURL: Tekenreeks. De URL van de JSONP-service die JSON-gegevens levert

**Geeft als resultaat**

Geen geretourneerde waarde.

## CQ_Analytics.JSONStore {#cq-analytics-jsonstore}

Een container voor een JSON-object. Maak een instantie van deze klasse om een niet-voortgezette sessiewinkel te maken die JSON-gegevens bevat:

`myjsonstore = new CQ_Analytics.JSONStore`

U kunt een reeks gegevens bepalen die de opslag bij initialisatie bevolkt.

Breidt CQ_Analytics.SessionStore uit.

### Eigenschappen {#properties-1}

#### STOREKEY {#storekey}

De sleutel die de opslag identificeert. Gebruik de methode `getInstance` om deze waarde op te halen.

#### STORENAME {#storename}

De naam van de winkel. Gebruik de methode `getInstance` om deze waarde op te halen.

### Methoden {#methods-3}

Zie ook CQ_Analytics.SessionStore voor overerfde methoden.

#### clear() {#clear}

Verwijdert de gegevens van de zittingsopslag en verwijdert alle initialiseringseigenschappen.

**Parameters**

Geen.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### getInstance(storeName, jsonData) {#getinstance-storename-jsondata}

Maakt een CQ_Analytics.JSONStore-object met een opgegeven naam en geïnitialiseerd met de opgegeven JSON-gegevens (roept de methode initJSON aan).

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Geeft als resultaat**

Het object CQ_Analytics.JSONStore.

#### getJSON() {#getjson}

Haalt de gegevens van de sessieopslag op in JSON-indeling.

**Parameters**

Geen.

**Geeft als resultaat**

Een object dat de opslaggegevens in JSON-indeling vertegenwoordigt.

#### init() {#init}

Wist de zittingsopslag en initialiseert het met het initialiseringsbezit. Stelt de initialisatiemarkering in op `true` en activeert vervolgens de gebeurtenissen `initialize` en `update`.

**Parameters**

Geen.

**Geeft als resultaat**

Geen geretourneerde gegevens.

#### initJSON(jsonData, doNotClear) {#initjson-jsondata-donotclear}

Maakt initialisatie-eigenschappen van de gegevens in een JSON-object. U kunt desgewenst alle bestaande initialisatie-eigenschappen verwijderen.

De namen van de eigenschappen worden afgeleid van de hiërarchie van de gegevens in het JSON-object. De volgende voorbeeldcode vertegenwoordigt een JSON-object:

```xml
{
A: "valueA",
B: {
     B1: "valueBB1"
    }
}
```

In dit voorbeeld worden de volgende eigenschappen gemaakt in de winkel:

```xml
A: "valueA"
B/B1: "valueBB1"
```

**Parameters**

* jsonData: Een JSON-object dat de gegevens bevat die moeten worden opgeslagen.
* doNotClear: Bij de waarde true blijven de bestaande initialisatie-eigenschappen behouden en worden de eigenschappen toegevoegd die zijn afgeleid van het JSON-object. Bij de waarde false worden de bestaande initialisatie-eigenschappen verwijderd voordat de eigenschappen uit het JSON-object worden toegevoegd.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata}

Maakt een CQ_Analytics.JSONStore-object met een opgegeven naam en geïnitialiseerd met de opgegeven JSON-gegevens (roept de methode initJSON aan). Het nieuwe object wordt automatisch geregistreerd bij Clickstream Cloud Manager.

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Geeft als resultaat**

Het object CQ_Analytics.JSONStore.

## CQ_Analytics.Observable {#cq-analytics-observable}

Hiermee worden gebeurtenissen geactiveerd en kunnen andere objecten naar deze gebeurtenissen luisteren en reageren. Klassen die deze klasse uitbreiden, kunnen gebeurtenissen doorlopen waardoor listeners worden aangeroepen.

### Methoden {#methods-4}

#### addListener(event, font, scope) {#addlistener-event-fct-scope}

Registreert een listener voor een gebeurtenis. Zie ook [Een listener maken om te reageren op een Session Store Update](/help/sites-developing/client-context.md#creating-a-listener-to-react-to-a-session-store-update).

**Parameters**

* gebeurtenis: Tekenreeks. De naam van de gebeurtenis waarnaar moet worden geluisterd.
* fct: Functie. De functie die wordt aangeroepen wanneer de gebeurtenis plaatsvindt.
* bereik: (Optioneel) Object. Het bereik waarin de handlerfunctie moet worden uitgevoerd. De context van de handlerfunctie &#39;this&#39;.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### removeListener(event, fct) {#removelistener-event-fct}

Verwijdert de opgegeven gebeurtenishandler voor een gebeurtenis.

**Parameters**

* gebeurtenis: Tekenreeks. De naam van de gebeurtenis.
* fct: Functie. De gebeurtenishandler.

**Geeft als resultaat**

Geen geretourneerde waarde.

## CQ_Analyics.PersistedJSONPStore {#cq-analyics-persistedjsonpstore}

Een persistente container van een JSON-object dat is opgehaald van een externe JSONP-service.

Breidt CQ_Analytics.PersistedJSONStore uit.

### Methoden {#methods-5}

Zie ook CQ_Analytics.PersistedJSONStore voor geërfte methodes.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback-1}

Maakt een CQ_Analytics.PersistedJSONPStore-object.

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: Tekenreeks. De URL van de JSONP-service
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* deferLoading: (Optioneel) Booleaans. De waarde true voorkomt dat de JSONP-service bij het maken van objecten wordt aangeroepen. Een waarde van vals veroorzaakt de dienst JSONP om worden geroepen.
* loadingCallback: (Optioneel) String. De naam van de functie om voor verwerking het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Geeft als resultaat**

Het nieuwe object CQ_Analytics.PersistedJSONPStore of null als storeName null is.

#### getServiceURL() {#getserviceurl-1}

Hiermee wordt de URL opgehaald van de JSONP-service die dit object gebruikt om JSON-gegevens op te halen.

**Parameters**

Geen.

**Geeft als resultaat**

Een tekenreeks die de service-URL vertegenwoordigt, of null als er geen service-URL is geconfigureerd.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback-1}

Roept de dienst JSONP aan. JSONP URL is de dienst URL die met een bepaalde callback functienaam wordt achtervoegd.

**Parameters**

* serviceURL: (Optioneel) String. De JSONP-service die moet worden aangeroepen. De waarde null zorgt ervoor dat de reeds geconfigureerde service-URL wordt gebruikt. Een waarde die niet gelijk is aan null, stelt de JSONP-service in die voor dit object moet worden gebruikt. (Zie setServiceURL.)
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback-1}

Maakt een CQ_Analytics.PersistedJSONPStore-object en registreert de winkel met Client-context.

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: (Optioneel) String. De URL van de JSONP-service.
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Geeft als resultaat**

Het geregistreerde object CQ_Analytics.PersistedJSONPStore.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl-1}

Plaatst URL van de dienst JSONP voor het terugwinnen van JSON- gegevens te gebruiken.

**Parameters**

* serviceURL: Tekenreeks. De URL van de JSONP-service die JSON-gegevens levert

**Geeft als resultaat**

Geen geretourneerde waarde.

## CQ_Analytics.PersistedJSONStore {#cq-analytics-persistedjsonstore}

Een persistente container van een JSON-object.

Breidt `CQ_Analytics.PersistedSessionStore` uit.

### Eigenschappen {#properties-2}

#### STOREKEY {#storekey-1}

De sleutel die de opslag identificeert. Gebruik de methode `getInstance` om deze waarde op te halen.

#### STORENAME {#storename-1}

De naam van de winkel. Gebruik de methode `getInstance` om deze waarde op te halen.

### Methoden {#methods-6}

Zie ook CQ_Analytics.PersistedSessionStore voor overerfde methoden.

#### getInstance(storeName, jsonData) {#getinstance-storename-jsondata-1}

Maakt een CQ_Analytics.PersistedJSONStore-object met een opgegeven naam en geïnitialiseerd met de opgegeven JSON-gegevens (roept de methode initJSON aan).

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Geeft als resultaat**

Het object CQ_Analytics.PersistedJSONStore.

#### getJSON() {#getjson-1}

Haalt de gegevens van de sessieopslag op in JSON-indeling.

**Parameters**

Geen.

**Geeft als resultaat**

Een object dat de opslaggegevens in JSON-indeling vertegenwoordigt.

#### initJSON(jsonData, doNotClear) {#initjson-jsondata-donotclear-1}

Maakt initialisatie-eigenschappen van de gegevens in een JSON-object. U kunt desgewenst alle bestaande initialisatie-eigenschappen verwijderen.

De namen van de eigenschappen worden afgeleid van de hiërarchie van de gegevens in het JSON-object. De volgende voorbeeldcode vertegenwoordigt een JSON-object:

```xml
{
A: "valueA",
B: {
     B1: "valueBB1"
    }
}
```

In dit voorbeeld worden de volgende eigenschappen gemaakt in de winkel:

```xml
A: "valueA"
B/B1: "valueBB1"
```

**Parameters**

* jsonData: Een JSON-object dat de gegevens bevat die moeten worden opgeslagen.
* doNotClear: Bij de waarde true blijven de bestaande initialisatie-eigenschappen behouden en worden de eigenschappen toegevoegd die zijn afgeleid van het JSON-object. Bij de waarde false worden de bestaande initialisatie-eigenschappen verwijderd voordat de eigenschappen uit het JSON-object worden toegevoegd.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata-1}

Maakt een CQ_Analytics.PersistedJSONStore-object met een opgegeven naam en geïnitialiseerd met de opgegeven JSON-gegevens (roept de methode initJSON aan). Het nieuwe object wordt automatisch geregistreerd bij Client Context Manager.

**Parameters**

* storeName: Tekenreeks. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Geeft als resultaat**

Het object CQ_Analytics.PersistedJSONStore.

## CQ_Analytics.PersistedSessionStore {#cq-analytics-persistedsessionstore}

Een container met eigenschappen en waarden. De gegevens blijven bestaan met CQ_Analytics.SessionPersistence. Maak een instantie van deze klasse om een persisted session store te maken:

`mypersistedstore = new CQ_Analytics.PersistedSessionStore`

Breidt CQ_Analytics.SessionStore uit.

### Eigenschappen {#properties-3}

#### STOREKEY {#storekey-2}

De standaardwaarde is `key`.

### Methoden {#methods-7}

Zie CQ_Analytics.SessionStore voor overerfde methoden.

Wanneer de overgeërfde methodes `clear`, `setProperty`, `setProperties`, `removeProperty` worden gebruikt om de opslaggegevens te veranderen, worden de veranderingen automatisch voortgeduurd, tenzij de veranderde eigenschappen als notPersisted worden gemarkeerd.

#### getStoreKey() {#getstorekey}

Hiermee wordt de eigenschap `STOREKEY` opgehaald.

**Parameters**

Geen

**Geeft als resultaat**

De waarde van de eigenschap `STOREKEY`.

#### isPersisted(name) {#ispersisted-name}

Hiermee wordt bepaald of een gegevenseigenschap wordt gepresteerd.

**Parameters**

* naam: Tekenreeks. De naam van de eigenschap.

**Geeft als resultaat**

Een Booleaanse waarde: `true` als de eigenschap wordt voortgezet, en een waarde van `false` als de waarde geen persisted eigenschap is.

#### persist() {#persist}

Houdt de zittingsopslag voort. In de standaardpersistentiemodus wordt browser `localStorage` gebruikt met `ClientSidePersistence` als naam ( `window.localStorage.set("ClientSidePersistance", store);`)

Als localStorage niet beschikbaar of schrijfbaar is, dan wordt de opslag voortgeduurd als bezit van het venster.

Hiermee wordt de gebeurtenis `persist` na voltooiing geactiveerd.

**Parameters**

Geen

**Geeft als resultaat**

Geen geretourneerde waarde.

#### reset(deferEvent) {#reset-deferevent}

Hiermee verwijdert u alle gegevenseigenschappen uit de winkel en gaat u door met de winkel. De gebeurtenis `udpate` wordt optioneel niet geactiveerd als de bewerking is voltooid.

**Parameters**

* delayEvent: De waarde true voorkomt dat de gebeurtenis `update` wordt geactiveerd. Bij een waarde van `false` wordt de updategebeurtenis geactiveerd.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### setNonPersisted(name) {#setnonpersisted-name}

Hiermee wordt een gegevenseigenschap gemarkeerd als niet voortgezet.

**Parameters**

* naam: Tekenreeks. The name of the property that is not to be persisted.

**Geeft als resultaat**

Geen retourwaarde.

## CQ_Analytics.SessionStore {#cq-analytics-sessionstore}

CQ_Analytics.SessionStore vertegenwoordigt een zittingsopslag. Maak een instantie van deze klasse om een sessiewinkel te maken:

`mystore = new CQ_Analytics.SessionStore`

Breidt CQ_Analytics.Observable uit.

### Eigenschappen {#properties-4}

#### STORENAME {#storename-2}

De naam van de sessiewinkel. Gebruik getName om de waarde van deze eigenschap op te halen.

### Methoden {#methods-8}

#### addInitProperty(name, value) {#addinitproperty-name-value}

Voegt een bezit en een waarde aan de de initialisatiegegevens van de zittingsopslag toe.

Gebruik loadInitProperties om de gegevens van de zittingsopslag met de initialisatiewaarden te bevolken.

**Parameters**

* naam: Tekenreeks. De naam van de eigenschap die moet worden toegevoegd.
* waarde: Tekenreeks. De waarde van de eigenschap die moet worden toegevoegd.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### clear() {#clear-1}

Hiermee verwijdert u alle gegevenseigenschappen uit de opslagruimte.

**Parameters**

Geen.

**Geeft als resultaat**

Geen retourwaarde.

#### getData(exclude) {#getdata-excluded}

Retourneert de opslaggegevens. Hiermee worden naameigenschappen eventueel uitgesloten van de gegevens. Roept de `init` methode als het gegevensbezit van de opslag niet bestaat.

**Parameters**

uitgesloten: (Optioneel) Een array met namen van eigenschappen die worden uitgesloten van de geretourneerde gegevens.

**Geeft als resultaat**

Een object met eigenschappen en hun waarden.

#### getInitProperty(name) {#getinitproperty-name}

Hiermee wordt de waarde van een eigenschap data opgehaald.

**Parameters**

* naam: Tekenreeks. The name of the data property to retrieve.

**Geeft als resultaat**

De waarde van de eigenschap data. Retourneert `null` als de sessieopslag geen eigenschap van de opgegeven naam bevat.

#### getName() {#getname}

Retourneert de naam van de sessiewinkel.

**Parameters**

Geen.

**Geeft als resultaat**

Een tekenreekswaarde die staat voor de winkelnaam.

#### getProperty(name, raw) {#getproperty-name-raw}

Retourneert de waarde van een eigenschap. De waarde wordt geretourneerd als de onbewerkte eigenschap of de XSS-gefilterde waarde. Roept de `init` methode als het gegevensbezit van de opslag niet bestaat.

**Parameters**

* naam: Tekenreeks. The name of the data property to retrieve.
* raw: Booleaans. De waarde true zorgt ervoor dat de waarde van de onbewerkte eigenschap wordt geretourneerd. Bij de waarde false wordt de geretourneerde waarde XSS-gefilterd.

**Geeft als resultaat**

De waarde van de eigenschap data.

#### getPropertyNames(uitgesloten) {#getpropertynames-excluded}

Retourneert de namen van de eigenschappen die de sessieopslag bevat. Roept de `init` methode als het gegevensbezit van de opslag niet bestaat.

**Parameters**

uitgesloten: (Optioneel) Een array met namen van eigenschappen die uit de resultaten moeten worden weggelaten.

**Geeft als resultaat**

Een array met tekenreekswaarden die staan voor de namen van de sessieeigenschappen.

#### getSessionStore() {#getsessionstore}

Retourneert de sessiewinkel die aan het huidige object is gekoppeld.

**Parameters**

Geen.

**Geeft als resultaat**

this

#### init() {#init-1}

Hiermee markeert u de winkel als geïnitialiseerd en wordt de gebeurtenis `initialize` geactiveerd.

**Parameters**

Geen.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### isInitialized() {#isinitialized}

Geeft aan of de opslag van sessies is geïnitialiseerd.

**Parameters**

Geen.

**Geeft als resultaat**

Een waarde van `true` als de opslag wordt geïnitialiseerd, en een waarde van `false` als de opslag niet wordt geïnitialiseerd.

#### loadInitProperties(obj, setValues) {#loadinitproperties-obj-setvalues}

Voegt de eigenschappen van een bepaald voorwerp aan de initialisatiegegevens van de zittingsopslag toe. Optioneel worden de objectgegevens ook toegevoegd aan de opslaggegevens.

**Parameters**

* obj: Een object dat opsombare eigenschappen bevat.
* setValues: Indien waar (true), worden de eigenschappen obj toegevoegd aan de opslaggegevens van de sessie als de opslaggegevens nog geen eigenschap met dezelfde naam bevatten. Wanneer de waarde false is, worden geen gegevens toegevoegd aan de opslaggegevens van de sessie.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### removeProperty(name) {#removeproperty-name}

Hiermee wordt een eigenschap uit de sessieopslag verwijderd. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd. Roept de `init` methode als het gegevensbezit van de opslag niet bestaat.

**Parameters**

* naam: Tekenreeks. De naam van de eigenschap die moet worden verwijderd.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### reset() {#reset}

Hiermee herstelt u de oorspronkelijke waarden van de gegevensopslag. De standaardimplementatie verwijdert eenvoudig alle gegevens. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd.

**Parameters**

Geen.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### setProperties(eigenschappen) {#setproperties-properties}

Stelt de waarden van meerdere eigenschappen in. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd. Roept de `init` methode als het gegevensbezit van de opslag niet bestaat.

**Parameters**

* Eigenschappen: Object. Een object dat opsombare eigenschappen bevat. Elke eigenschapnaam en -waarde worden toegevoegd aan de winkel.

**Geeft als resultaat**

Geen geretourneerde waarde.

#### setProperty(name, value) {#setproperty-name-value}

Hiermee wordt de waarde van een eigenschap ingesteld. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd. Roept de `init` methode als het gegevensbezit van de opslag niet bestaat.

**Parameters**

* naam: Tekenreeks. De naam van de eigenschap.
* waarde: Tekenreeks. Waarde eigenschap.

**Geeft als resultaat**

Geen geretourneerde waarde.
