---
title: JavaScript-API voor clientcontext
description: Meer informatie over de JavaScript API for Client Context in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
feature: Context Hub,Developing,Personalization
exl-id: 24bdf9fc-71e6-4b99-9dad-0f41a5e36b98
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '3106'
ht-degree: 0%

---

# JavaScript-API voor clientcontext{#client-context-javascript-api}

## CQ_Analytics.ClientContextMgr {#cq-analytics-clientcontextmgr}

Het object CQ_Analytics.ClientContextMgr is een singleton dat een set zelfgeregistreerde sessiewinkels bevat en methoden biedt voor het registreren, voortzetten en beheren van de sessiewinkels.

Breidt CQ_Analytics.PersistedSessionStore uit.

### Methoden {#methods}

#### getRegisteredStore(name) {#getregisteredstore-name}

Retourneert een sessiearchief met een opgegeven naam. Zie ook [ Toegang hebbend tot een Opslag van de Zitting ](/help/sites-developing/client-context.md#accessing-session-stores).

**Parameters**

* name: String. De naam van de sessiewinkel.

**Keert** terug

Een CQ_Analytics.SessionStore-object dat de zittingsopslag van de opgegeven naam vertegenwoordigt. Retourneert `null` wanneer er geen opslag met de opgegeven naam bestaat.

#### register(sessionstore) {#register-sessionstore}

Registreert een zittingsopslag met de Context van de Cliënt. Hiermee worden gebeurtenissen in het opslagregister en de opslagperiode na voltooiing geactiveerd.

**Parameters**

* sessionstore: CQ_Analytics.SessionStore. Het te registreren sessieopslagobject.

**Keert** terug

Geen geretourneerde waarde.

## CQ_Analytics.ClientContextUtils {#cq-analytics-clientcontextutils}

Verstrekt methodes om op de activering en registratie van de zittingsopslag te luisteren. Zie ook [ Controlerend dat een opslag van de Zitting wordt bepaald en ](/help/sites-developing/client-context.md#checking-that-a-session-store-is-defined-and-initialized) geïnitialiseerd.

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

Wanneer de vertraging op `true` of verscheidene milliseconden wordt geplaatst, wacht de methode alvorens de callback methode te roepen. Als een andere initialisatiegebeurtenis wordt geactiveerd voordat de vertraging wordt doorgegeven, wordt gewacht totdat de vertragingstijd is overschreden zonder initialisatiegebeurtenis. Dit laat het wachten op een tweede initialiseringsgebeurtenis toe om worden teweeggebracht en roept de callback functie in het meest optimale geval.

**Parameters**

* storeName: String. De naam van het sessiearchief om de listener toe te voegen.
* callback: Function. De functie om op archiefinitialisatie te roepen.
* delay: Boolean of Number. De hoeveelheid tijd om de vraag aan de callback functie, in milliseconden te vertragen. Een Booleaanse waarde `true` gebruikt de standaardvertraging van `200 ms` . Een booleaanse waarde `false` of een negatief getal zorgt ervoor dat er geen vertraging wordt gebruikt.

**Keert** terug

Geen geretourneerde waarde.

#### onStoreRegistered(storeName, callback) {#onstoreregistered-storename-callback}

Registreert een callback functie die wordt geroepen wanneer een zittingsopslag wordt geregistreerd. De registergebeurtenis komt voor wanneer een opslag aan [ CQ_Analytics.ClientContextMgr ](#cq-analytics-clientcontextmgr) wordt geregistreerd.

**Parameters**

* storeName: String. De naam van het sessiearchief om de listener toe te voegen.
* callback: Function. De functie om op archiefinitialisatie te roepen.

**Keert** terug

Geen geretourneerde waarde.

## CQ_Analytics.JSONPStore {#cq-analytics-jsonpstore}

Een niet-voortgezette sessiewinkel die JSON-gegevens bevat. De gegevens worden teruggewonnen van de externe dienst JSONP. Gebruik de methode `getInstance` of `getRegisteredInstance` om een instantie van deze klasse te maken.

Breidt CQ_Analytics.JSONStore uit.

### Eigenschappen {#properties}

Zie CQ_Analytics.JSONStore en CQ_Analytics.SessonStore voor geërfte eigenschappen.

### Methoden {#methods-2}

Zie ook CQ_Analytics.JSONStore en CQ_Analytics.SessonStore voor geërfte methodes.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback}

Maakt een CQ_Analytics.JSONPStore-object.

**Parameters**

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: String. De URL van de JSONP-service
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* delayLoading: (Optioneel) Boolean. De waarde true voorkomt dat de JSONP-service bij het maken van objecten wordt aangeroepen. Een waarde van vals veroorzaakt de dienst JSONP om worden geroepen.
* loadingCallback: (Optioneel) String. De naam van de functie om voor verwerking van het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Keert** terug

Het nieuwe object CQ_Analytics.JSONPStore of null als storeName null is.

#### getServiceURL() {#getserviceurl}

Hiermee wordt de URL opgehaald van de JSONP-service die dit object gebruikt om JSON-gegevens op te halen.

**Parameters**

Geen.

**Keert** terug

Een tekenreeks die de service-URL vertegenwoordigt, of null als er geen service-URL is geconfigureerd.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback}

Roept de dienst JSONP aan. JSONP URL is de dienst URL die met een bepaalde callback functienaam wordt achtervoegd.

**Parameters**

* serviceURL: (Optioneel) tekenreeks. De JSONP-service die moet worden aangeroepen. De waarde null zorgt ervoor dat de reeds geconfigureerde service-URL wordt gebruikt. Een waarde die niet gelijk is aan null, stelt de JSONP-service in die voor dit object moet worden gebruikt. (Zie setServiceURL.)
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking van het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Keert** terug

Geen geretourneerde waarde.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback}

Maakt een CQ_Analytics.JSONPStore-object en registreert de winkel met Client-context.

**Parameters**

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: (Optioneel) tekenreeks. De URL van de JSONP-service.
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking van het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Keert** terug

Het geregistreerde object CQ_Analytics.JSONPStore.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl}

Plaatst URL van de dienst JSONP voor het terugwinnen van JSON- gegevens te gebruiken.

**Parameters**

* serviceURL: String. URL van de dienst JSONP die JSON gegevens verstrekt

**Keert** terug

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

**Keert** terug

Geen geretourneerde waarde.

#### getInstance(storeName, jsonData) {#getinstance-storename-jsondata}

Maakt een CQ_Analytics.JSONStore-object met een opgegeven naam en geïnitialiseerd met de opgegeven JSON-gegevens (roept de methode initJSON aan).

**Parameters**

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Keert** terug

Het object CQ_Analytics.JSONStore.

#### getJSON() {#getjson}

Haalt de gegevens van de sessieopslag op in JSON-indeling.

**Parameters**

Geen.

**Keert** terug

Een object dat de opslaggegevens in JSON-indeling vertegenwoordigt.

#### init() {#init}

Wist de zittingsopslag en initialiseert het met het initialiseringsbezit. Stelt de initialisatiemarkering in op `true` en activeert vervolgens de gebeurtenissen `initialize` en `update` .

**Parameters**

Geen.

**Keert** terug

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
* doNotClear: de waarde true behoudt de bestaande initialisatie-eigenschappen en voegt de waarden toe die zijn afgeleid van het JSON-object. Bij de waarde false worden de bestaande initialisatie-eigenschappen verwijderd voordat de eigenschappen uit het JSON-object worden toegevoegd.

**Keert** terug

Geen geretourneerde waarde.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata}

Maakt een CQ_Analytics.JSONStore-object met een opgegeven naam en geïnitialiseerd met de opgegeven JSON-gegevens (roept de methode initJSON aan). Het nieuwe object wordt automatisch geregistreerd bij de Clickstream Cloud Manager.

**Parameters**

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Keert** terug

Het object CQ_Analytics.JSONStore.

## CQ_Analytics.Observable {#cq-analytics-observable}

Hiermee worden gebeurtenissen geactiveerd en kunnen andere objecten naar deze gebeurtenissen luisteren en reageren. Klassen die deze klasse uitbreiden, kunnen gebeurtenissen doorlopen waardoor listeners worden aangeroepen.

### Methoden {#methods-4}

#### addListener (gebeurtenis, effect, bereik) {#addlistener-event-fct-scope}

Registreert een listener voor een gebeurtenis. Zie ook [ Creërend een Listener om aan een Update van de Sessieopslag ](/help/sites-developing/client-context.md#creating-a-listener-to-react-to-a-session-store-update) te antwoorden.

**Parameters**

* event: String. De naam van de gebeurtenis waarnaar moet worden geluisterd.
* fct: Functie. De functie die wordt aangeroepen wanneer de gebeurtenis plaatsvindt.
* bereik: (optioneel) Object. Het bereik waarin de handlerfunctie moet worden uitgevoerd. De context van de handlerfunctie &#39;this&#39;.

**Keert** terug

Geen geretourneerde waarde.

#### removeListener (gebeurtenis, fct) {#removelistener-event-fct}

Verwijdert de opgegeven gebeurtenishandler voor een gebeurtenis.

**Parameters**

* event: String. De naam van de gebeurtenis.
* fct: Functie. De gebeurtenishandler.

**Keert** terug

Geen geretourneerde waarde.

## CQ_Analyics.PersistedJSONPStore {#cq-analyics-persistedjsonpstore}

Een persistente container van een JSON-object dat is opgehaald van een externe JSONP-service.

Breidt CQ_Analytics.PersistedJSONStore uit.

### Methoden {#methods-5}

Zie ook CQ_Analytics.PersistedJSONStore voor geërfte methodes.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback-1}

Maakt een CQ_Analytics.PersistedJSONPStore-object.

**Parameters**

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: String. De URL van de JSONP-service
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* delayLoading: (Optioneel) Boolean. De waarde true voorkomt dat de JSONP-service bij het maken van objecten wordt aangeroepen. Een waarde van vals veroorzaakt de dienst JSONP om worden geroepen.
* loadingCallback: (Optioneel) String. De naam van de functie om voor verwerking van het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Keert** terug

Het nieuwe object CQ_Analytics.PersistedJSONPStore of null als storeName null is.

#### getServiceURL() {#getserviceurl-1}

Hiermee wordt de URL opgehaald van de JSONP-service die dit object gebruikt om JSON-gegevens op te halen.

**Parameters**

Geen.

**Keert** terug

Een tekenreeks die de service-URL vertegenwoordigt, of null als er geen service-URL is geconfigureerd.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback-1}

Roept de dienst JSONP aan. JSONP URL is de dienst URL die met een bepaalde callback functienaam wordt achtervoegd.

**Parameters**

* serviceURL: (Optioneel) tekenreeks. De JSONP-service die moet worden aangeroepen. De waarde null zorgt ervoor dat de reeds geconfigureerde service-URL wordt gebruikt. Een waarde die niet gelijk is aan null, stelt de JSONP-service in die voor dit object moet worden gebruikt. (Zie setServiceURL.)
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking van het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Keert** terug

Geen geretourneerde waarde.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback-1}

Maakt een CQ_Analytics.PersistedJSONPStore-object en registreert de winkel met Client-context.

**Parameters**

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters. Als er geen storeName is opgegeven, retourneert de methode null.
* serviceURL: (Optioneel) tekenreeks. De URL van de JSONP-service.
* dynamicData: (Optioneel) Object. JSON-gegevens die aan de initialisatiegegevens van de winkel moeten worden toegevoegd voordat de callback-functie wordt aangeroepen.
* callback: (Optioneel) String. De naam van de functie om voor verwerking van het voorwerp te roepen JSONP dat de dienst JSONP terugkeert. De callback functie moet één enkele parameter bepalen die een voorwerp CQ_Analytics.JSONPStore is.

**Keert** terug

Het geregistreerde object CQ_Analytics.PersistedJSONPStore.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl-1}

Plaatst URL van de dienst JSONP voor het terugwinnen van JSON- gegevens te gebruiken.

**Parameters**

* serviceURL: String. URL van de dienst JSONP die JSON gegevens verstrekt

**Keert** terug

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

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Keert** terug

Het object CQ_Analytics.PersistedJSONStore.

#### getJSON() {#getjson-1}

Haalt de gegevens van de sessieopslag op in JSON-indeling.

**Parameters**

Geen.

**Keert** terug

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
* doNotClear: de waarde true behoudt de bestaande initialisatie-eigenschappen en voegt de waarden toe die zijn afgeleid van het JSON-object. Bij de waarde false worden de bestaande initialisatie-eigenschappen verwijderd voordat de eigenschappen uit het JSON-object worden toegevoegd.

**Keert** terug

Geen geretourneerde waarde.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata-1}

Maakt een CQ_Analytics.PersistedJSONStore-object met een opgegeven naam en geïnitialiseerd met de opgegeven JSON-gegevens (roept de methode initJSON aan). Het nieuwe object wordt automatisch geregistreerd bij Client Context Manager.

**Parameters**

* storeName: String. De naam die als eigenschap STORENAME moet worden gebruikt. De waarde van het bezit STOREKEY wordt geplaatst aan storeName met alle karakters in hoofdletters.
* jsonData: Object. Een object dat JSON-gegevens bevat.

**Keert** terug

Het object CQ_Analytics.PersistedJSONStore.

## CQ_Analytics.PersistedSessionStore {#cq-analytics-persistedsessionstore}

Een container met eigenschappen en waarden. De gegevens blijven bestaan met CQ_Analytics.SessionPersistence. Maak een instantie van deze klasse om een persisted session store te maken:

`mypersistedstore = new CQ_Analytics.PersistedSessionStore`

Breidt CQ_Analytics.SessionStore uit.

### Eigenschappen {#properties-3}

#### STOREKEY {#storekey-2}

De standaardwaarde is `key` .

### Methoden {#methods-7}

Zie CQ_Analytics.SessionStore voor overerfde methoden.

Wanneer de overerfde methoden `clear` , `setProperty` , `setProperties` , `removeProperty` worden gebruikt om de opslaggegevens te wijzigen, worden de wijzigingen automatisch voortgezet, tenzij de gewijzigde eigenschappen worden gemarkeerd als notPersisted.

#### getStoreKey() {#getstorekey}

Hiermee wordt de eigenschap `STOREKEY` opgehaald.

**Parameters**

Geen

**Keert** terug

De waarde van de eigenschap `STOREKEY` .

#### isPersisted(name) {#ispersisted-name}

Hiermee wordt bepaald of een gegevenseigenschap wordt gepresteerd.

**Parameters**

* name: String. De naam van de eigenschap.

**Keert** terug

Een Booleaanse waarde: `true` als de eigenschap wordt voortgezet, en de waarde `false` als de waarde geen blijvend eigenschap is.

#### persist() {#persist}

Houdt de zittingsopslag voort. In de standaardpersistentiemodus wordt browser `localStorage` gebruikt met `ClientSidePersistence` als naam ( `window.localStorage.set("ClientSidePersistance", store);` )

Als localStorage niet beschikbaar of schrijfbaar is, dan wordt de opslag voortgeduurd als bezit van het venster.

Hiermee wordt de gebeurtenis `persist` na voltooiing geactiveerd.

**Parameters**

Geen

**Keert** terug

Geen geretourneerde waarde.

#### reset(delayEvent) {#reset-deferevent}

Hiermee verwijdert u alle gegevenseigenschappen uit de winkel en gaat u door met de winkel. De gebeurtenis `udpate` wordt optioneel niet gestart als de bewerking is voltooid.

**Parameters**

* delayEvent: de waarde true voorkomt dat de gebeurtenis `update` wordt gestart. Bij de waarde `false` wordt de updategebeurtenis geactiveerd.

**Keert** terug

Geen geretourneerde waarde.

#### setNonPersisted(name) {#setnonpersisted-name}

Hiermee wordt een gegevenseigenschap gemarkeerd als niet blijvend.

**Parameters**

* name: String. The name of the property that is not to be persisted.

**Keert** terug

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

* name: String. De naam van de eigenschap die moet worden toegevoegd.
* value: String. De waarde van de eigenschap die moet worden toegevoegd.

**Keert** terug

Geen geretourneerde waarde.

#### clear() {#clear-1}

Hiermee verwijdert u alle gegevenseigenschappen uit de opslagruimte.

**Parameters**

Geen.

**Keert** terug

Geen retourwaarde.

#### getData(uitgesloten) {#getdata-excluded}

Retourneert de opslaggegevens. Hiermee worden naameigenschappen eventueel uitgesloten van de gegevens. Roept de methode `init` aan als de eigenschap data van de store niet bestaat.

**Parameters**

exclude: (Optioneel) Een array met namen van eigenschappen die worden uitgesloten van de geretourneerde gegevens.

**Keert** terug

Een object met eigenschappen en hun waarden.

#### getInitProperty(name) {#getinitproperty-name}

Hiermee wordt de waarde van een eigenschap data opgehaald.

**Parameters**

* name: String. The name of the data property to retrieve.

**Keert** terug

De waarde van de eigenschap data. Retourneert `null` als de sessiewinkel geen eigenschap met de opgegeven naam bevat.

#### getName() {#getname}

Retourneert de naam van de sessiewinkel.

**Parameters**

Geen.

**Keert** terug

Een tekenreekswaarde die staat voor de winkelnaam.

#### getProperty(name, raw) {#getproperty-name-raw}

Retourneert de waarde van een eigenschap. De waarde wordt geretourneerd als de onbewerkte eigenschap of de XSS-gefilterde waarde. Roept de methode `init` aan als de eigenschap data van de store niet bestaat.

**Parameters**

* name: String. The name of the data property to retrieve.
* raw: Boolean. De waarde true zorgt ervoor dat de waarde van de onbewerkte eigenschap wordt geretourneerd. Bij de waarde false wordt de geretourneerde waarde XSS-gefilterd.

**Keert** terug

De waarde van de eigenschap data.

#### getPropertyNames(uitgesloten) {#getpropertynames-excluded}

Retourneert de namen van de eigenschappen die de sessieopslag bevat. Roept de methode `init` aan als de eigenschap data van de store niet bestaat.

**Parameters**

uitgesloten: (Optioneel) Een array met namen van eigenschappen die niet in de resultaten worden opgenomen.

**Keert** terug

Een array met tekenreekswaarden die staan voor de namen van de sessieeigenschappen.

#### getSessionStore() {#getsessionstore}

Retourneert de sessiewinkel die aan het huidige object is gekoppeld.

**Parameters**

Geen.

**Keert** terug

dit

#### init() {#init-1}

Hiermee wordt de winkel gemarkeerd als geïnitialiseerd en wordt de gebeurtenis `initialize` geactiveerd.

**Parameters**

Geen.

**Keert** terug

Geen geretourneerde waarde.

#### isInitialized() {#isinitialized}

Geeft aan of de opslag van sessies is geïnitialiseerd.

**Parameters**

Geen.

**Keert** terug

De waarde `true` als de winkel is geïnitialiseerd en de waarde `false` als de winkel niet is geïnitialiseerd.

#### loadInitProperties(obj, setValues) {#loadinitproperties-obj-setvalues}

Voegt de eigenschappen van een bepaald voorwerp aan de initialisatiegegevens van de zittingsopslag toe. Optioneel worden de objectgegevens ook toegevoegd aan de opslaggegevens.

**Parameters**

* obj: Een object dat opsombare eigenschappen bevat.
* setValues: Indien true, worden de eigenschappen obj toegevoegd aan de gegevens van de sessieopslagruimte als de opslaggegevens nog geen eigenschap met dezelfde naam bevatten. Wanneer de waarde false is, worden geen gegevens toegevoegd aan de opslaggegevens van de sessie.

**Keert** terug

Geen geretourneerde waarde.

#### removeProperty(name) {#removeproperty-name}

Hiermee wordt een eigenschap uit de sessieopslag verwijderd. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd. Roept de methode `init` aan als de eigenschap data van de store niet bestaat.

**Parameters**

* name: String. The name of the property to remove.

**Keert** terug

Geen geretourneerde waarde.

#### reset() {#reset}

Hiermee herstelt u de oorspronkelijke waarden van de gegevensopslag. De standaardimplementatie verwijdert eenvoudig alle gegevens. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd.

**Parameters**

Geen.

**Keert** terug

Geen geretourneerde waarde.

#### setProperties(eigenschappen) {#setproperties-properties}

Stelt de waarden van meerdere eigenschappen in. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd. Roept de methode `init` aan als de eigenschap data van de store niet bestaat.

**Parameters**

* Eigenschappen: Object. Een object dat opsombare eigenschappen bevat. Elke eigenschapnaam en -waarde worden toegevoegd aan de winkel.

**Keert** terug

Geen geretourneerde waarde.

#### setProperty(name, value) {#setproperty-name-value}

Hiermee wordt de waarde van een eigenschap ingesteld. Hiermee wordt de gebeurtenis `update` na voltooiing geactiveerd. Roept de methode `init` aan als de eigenschap data van de store niet bestaat.

**Parameters**

* name: String. De naam van de eigenschap.
* value: String. Waarde eigenschap.

**Keert** terug

Geen geretourneerde waarde.
