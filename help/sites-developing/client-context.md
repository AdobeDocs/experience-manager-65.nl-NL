---
title: Clientcontext in detail
seo-title: Clientcontext in detail
description: De context van de Cliënt vertegenwoordigt een dynamisch geassembleerde inzameling van gebruikersgegevens
seo-description: De context van de Cliënt vertegenwoordigt een dynamisch geassembleerde inzameling van gebruikersgegevens
uuid: 95b08fbd-4f50-44a1-80fb-46335fe04a40
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: c881ad66-bcc3-4f99-b77f-0944c23e2d29
docset: aem65
feature: Context Hub
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '3025'
ht-degree: 0%

---


# Clientcontext in detail{#client-context-in-detail}

>[!NOTE]
>
>De Context van de cliënt is vervangen door ContextHub. Zie de [verwante documentatie](/help/sites-developing/contexthub.md) voor meer informatie.

De context van de Cliënt vertegenwoordigt een dynamisch geassembleerde inzameling van gebruikersgegevens. Met de gegevens kunt u bepalen welke inhoud in een bepaalde situatie op een webpagina moet worden weergegeven (inhoud is gericht). De gegevens zijn ook beschikbaar voor analyses op websites en voor alle javascript-functies op de pagina.

Clientcontext bestaat hoofdzakelijk uit de volgende aspecten:

* De zittingsopslag, die de gebruikersgegevens bevat.
* De interface die de gebruikersgegevens weergeeft en tools biedt om de gebruikerservaring te simuleren.
* A [javascript API](/help/sites-developing/ccjsapi.md) voor interactie met zittingsopslag.

Om een standalone zittingsopslag tot stand te brengen en het toe te voegen aan de Context van de Cliënt, of een zittingsopslag te creëren die aan een component van de Opslag van de Context gebonden is. AEM installeert diverse Context Store-componenten die u direct kunt gebruiken. U kunt deze componenten als basis voor uw componenten gebruiken.

Voor informatie over het openen van de Context van de Cliënt, het vormen van de informatie die het toont, en het simuleren van de gebruikerservaring, zie [Context van de Cliënt](/help/sites-administering/client-context.md).

## Sessiewinkels {#session-stores}

De context van de Cliënt omvat diverse zittingsopslag die gebruikersgegevens bevatten. De gegevens van de opslag komen uit de volgende bronnen:

* De clientwebbrowser.
* De server (zie [JSONP Store](/help/sites-administering/client-context.md#main-pars-variable-8) voor het opslaan van informatie van derdebronnen)

Het kader van de Context van de Cliënt verstrekt [javascript API](/help/sites-developing/ccjsapi.md) dat u kunt gebruiken om met zittingsopslag in wisselwerking te staan om gebruikersgegevens te lezen en te schrijven, en te luisteren en te reageren om gebeurtenissen op te slaan. U kunt ook sessiewinkels maken voor gebruikersgegevens die u gebruikt voor inhoud die zich richt op of voor andere doeleinden.

Sessieopslaggegevens blijven op de client staan. De context van de Cliënt schrijft geen gegevens terug naar de server. Als u gegevens naar de server wilt verzenden, gebruikt u een formulier of ontwikkelt u aangepaste javascript.

Elke zittingsopslag is een inzameling van bezit-waarde paren. De zittingsopslag vertegenwoordigt een inzameling van gegevens (van om het even welke soort), waarvan de conceptuele betekenis door de ontwerper en/of de ontwikkelaar kan worden beslist. In het volgende voorbeeld wordt een object gedefinieerd dat de profielgegevens vertegenwoordigt die in de sessieopslag kunnen worden opgeslagen:

```
{
  age: 20,
  authorizableId: "aparker@geometrixx.info",
  birthday: "27 Feb 1992",
  email: "aparker@geometrixx.info",
  formattedName: "Alison Parker",
  gender: "female",
  path: "/home/users/geometrixx/aparker@geometrixx.info/profile"
}
```

Een zittingsopslag kan over browser zittingen worden voortgeduurd, of kan slechts voor de browser zitting duren waarin het wordt gecreeerd.

>[!NOTE]
>
>Bij persistentie van de opslag worden browseropslag of cookies gebruikt (het cookie `SessionPersistence`). Browseropslag komt vaker voor.
>
>Wanneer de browser wordt gesloten en opnieuw geopend, kan een zittingsopslag met de waarden van een persisted store worden geladen. Het wissen van de browsercache is dan nodig om de oude waarden te verwijderen.

### Context Store-componenten {#context-store-components}

Een component van de contextopslag is een component CQ die aan de Context van de Cliënt kan worden toegevoegd. Typisch, tonen de componenten van de contextopslag gegevens van een zittingsopslag waaraan zij worden geassocieerd. Nochtans, is de informatie die de componentenvertoning van de contextopslag niet beperkt tot zittingsopslaggegevens.

Contextarchiefcomponenten kunnen de volgende items bevatten:

* JSP manuscripten die de verschijning in de Context van de Cliënt bepalen.
* Eigenschappen voor het weergeven van de component in Sidetrap.
* Dialoogvensters bewerken voor het configureren van componentinstanties.
* Javascript dat de zittingsopslag initialiseert.

Voor een beschrijving van de geïnstalleerde Componenten van de Opslag van de Context die u aan de Opslag van de Context kunt toevoegen, zie [Beschikbare Componenten van de Context van de Cliënt](/help/sites-administering/client-context.md#available-client-context-components).

>[!NOTE]
>
>Paginagegevens bevinden zich niet meer in de clientcontext als een standaardcomponent. Indien nodig, kunt u dit toevoegen door de cliëntcontext uit te geven, toevoegend **Algemene Eigenschappen van de Opslag** component, dan vormend dit om **Store** als `pagedata` te bepalen.

### Doelgerichte levering van inhoud {#targeted-content-delivery}

Profielinformatie wordt ook gebruikt voor het afleveren van [doelinhoud](/help/sites-authoring/content-targeting-touch.md).

![clientContext_](assets/clientcontext_targetedcontentdelivery.png) ![targetContentLoaderClientContext_targetContentDeliydetail](assets/clientcontext_targetedcontentdeliverydetail.png)

## Clientcontext toevoegen aan een pagina {#adding-client-context-to-a-page}

Neem de component Client Context op in de hoofdsectie van uw webpagina&#39;s om Client Context in te schakelen. Het pad van het knooppunt Client Context component is `/libs/cq/personalization/components/clientcontext`. Als u de component wilt opnemen, voegt u de volgende code toe aan het JSP-bestand van uw paginacomponent, dat zich net onder het element `body` van de pagina bevindt:

```java
<cq:include path="clientcontext" resourceType="cq/personalization/components/clientcontext"/>
```

De component ClientContext veroorzaakt de pagina om de cliëntbibliotheken te laden die de Context van de Cliënt uitvoeren.

* De JavaScript-API voor de clientcontext.
* Het clientcontextframework dat sessiewinkels, gebeurtenisbeheer, enzovoort ondersteunt.
* Segmenten die zijn gedefinieerd.
* De manuscripten init.js die voor elke component van de contextopslag worden geproduceerd die aan de Context van de Cliënt is toegevoegd.
* (Alleen instantie Auteur) De gebruikersinterface van de clientcontext.

De gebruikersinterface van de clientcontext is alleen beschikbaar voor de instantie van de auteur.

## Clientcontext uitbreiden {#extending-client-context}

Om de Context van de Cliënt uit te breiden, creeer een zittingsopslag en naar keuze toon de opslaggegevens:

* Maak een sessiewinkel voor de gebruikersgegevens die u nodig hebt voor het aangeven van inhoud en webanalyse.
* Creeer een component van de contextopslag om beheerders toe te laten om de bijbehorende zittingsopslag te vormen, en opslaggegevens in de Context van de Cliënt voor testende doeleinden te tonen.

>[!NOTE]
>
>Als u een `JSONP` dienst hebt (of creeert) die de gegevens kan verstrekken, kunt u eenvoudig de `JSONP` component van de contextopslag gebruiken en het in kaart brengen aan de dienst JSONP. Dit zal de zittingsopslag behandelen.

### Sessieopslag {#creating-a-session-store} maken

Creeer een zittingsopslag voor de gegevens die u aan moet toevoegen en van de Context van de Cliënt terugwinnen. Over het algemeen, gebruikt u de volgende procedure om een zittingsopslag tot stand te brengen:

1. Maak een clientbibliotheekmap met de eigenschapswaarde `categories` van `personalization.stores.kernel`. Clientcontext laadt automatisch de clientbibliotheken van deze categorie.

1. Configureer de clientbibliotheekmap zodat deze afhankelijk is van de clientbibliotheekmap `personalization.core.kernel`. De clientbibliotheek `personalization.core.kernel` biedt de JavaScript-API voor clientcontext.

1. Voeg de javascript toe die tot de zittingsopslag leidt en initialiseert.

Het opnemen van javascript in de de cliëntbibliotheek personalization.stores.kernel veroorzaakt de opslag dat wordt gecreeerd wanneer het kader van de Context van de Cliënt wordt geladen.

>[!NOTE]
>
>Als u een zittingsopslag als deel van een component van de contextopslag creeert, kunt u javascript in het init.js.jsp- dossier van de component alternatief plaatsen. In dit geval, wordt de zittingsopslag gecreeerd slechts als de component aan de Context van de Cliënt wordt toegevoegd.

#### Typen sessiewinkels {#types-of-session-stores}

Sessiewinkels worden gemaakt en beschikbaar tijdens een browsersessie, of blijven aanwezig in browseropslag of cookies. De JavaScript-API voor clientcontext definieert verschillende klassen die beide typen gegevensopslag vertegenwoordigen:

* ` [CQ_Analytics.SessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore)`: Deze objecten bevinden zich alleen in het pagina-DOM. De gegevens worden gemaakt en geduurd tijdens de levensduur van de pagina.
* ` [CQ_Analytics.PerstistedSessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-persistedsessionstore)`: Deze objecten bevinden zich in het pagina-DOM en worden bewaard in browseropslag of cookies. De gegevens zijn beschikbaar op pagina&#39;s en in gebruikerssessies.

API verstrekt ook uitbreidingen van deze klassen die voor het opslaan van JSON- gegevens of JSONP- gegevens worden gespecialiseerd:

* Alleen sessieobjecten: [CQ_Analytics.JSONStore](/help/sites-developing/ccjsapi.md#cq-analytics-jsonstore) en [CQ_Analytics.JSONPStore](/help/sites-developing/ccjsapi.md#cq-analytics-jsonpstore).

* Blijvende objecten: [CQ_Analytics.PersistedJSONStore](/help/sites-developing/ccjsapi.md#cq-analytics-persistedjsonstore) en [CQ_Analytics.PersistedJSONPStore](/help/sites-developing/ccjsapi.md#cq-analyics-persistedjsonpstore).

#### Het creëren van het Voorwerp van de Sessieopslag {#creating-the-session-store-object}

Het javascript van uw omslag van de cliëntbibliotheek leidt tot en initialiseert de zittingsopslag. De zittingsopslag moet dan worden geregistreerd gebruikend de Manager van de Opslag van de Context. In het volgende voorbeeld wordt een object [CQ_Analytics.SessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore) gemaakt en geregistreerd.

```
//Create the session store
if (!CQ_Analytics.MyStore) {
    CQ_Analytics.MyStore = new CQ_Analytics.SessionStore();
    CQ_Analytics.MyStore.STOREKEY = "MYSTORE";
    CQ_Analytics.MyStore.STORENAME = "mystore";
    CQ_Analytics.MyStore.data={};
}
//register the session store
if (CQ_Analytics.ClientContextMgr){
    CQ_Analytics.ClientContextMgr.register(CQ_Analytics.MyStore)
}
```

Voor het opslaan van JSON-gegevens wordt in het volgende voorbeeld een object [CQ_Analytics.JSONStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore) gemaakt en geregistreerd.

```
if (!CQ_Analytics.myJSONStore) {
    CQ_Analytics.myJSONStore = CQ_Analytics.JSONStore.registerNewInstance("myjsonstore",{});
}
```

### Een Context Store-component maken {#creating-a-context-store-component}

Creeer een component van de contextopslag om zittingsopslaggegevens in de Context van de Cliënt terug te geven. Zodra gecreeerd, kunt u uw component van de contextopslag op de Context van de Cliënt slepen om gegevens van een zittingsopslag terug te geven. Contextarchiefcomponenten bestaan uit de volgende items:

* JSP-script voor het renderen van de gegevens.
* Een bewerkingsdialoogvenster.
* Een JSP script voor het initialiseren van de sessieopslag.
* (Optioneel) Een clientbibliotheekmap waarmee de sessieopslag wordt gemaakt. U hoeft de map met de clientbibliotheek niet op te nemen als de component een bestaande sessieopslag gebruikt.

#### De geleverde componenten van de Context Store uitbreiden {#extending-the-provided-context-store-components}

AEM verstrekt de genericstore en de genericstoreproperties contextstore componenten die u kunt uitbreiden. De structuur van uw opslaggegevens bepaalt de component die u uitbreidt:

* Eigenschap-waardeparen: Breid de `GenericStoreProperties` component uit. Deze component geeft automatisch opslagruimten van eigenschap-waarde paren terug. Er zijn verschillende interactiepunten beschikbaar:

   * `prolog.jsp` en  `epilog.jsp`: componentinteractie waarmee u logica aan de serverzijde kunt toevoegen voor of na het renderen van de component.

* Complexe gegevens: Breid de `GenericStore` component uit. Uw zittingsopslag zal dan een &quot;renderer&quot;methode nodig hebben die zal worden geroepen telkens als de component moet worden teruggegeven. De renderfunctie wordt aangeroepen met twee parameters:

   * `@param {String} store`
De winkel die moet worden gerenderd

   * `@param {String} divId`
Id van de div waarin de opslag moet worden teruggegeven.

>[!NOTE]
>
>Alle componenten van de Context van de Cliënt zijn uitbreidingen van of de Algemene opslag of de Algemene componenten van de Eigenschappen van de Opslag. In de map `/libs/cq/personalization/components/contextstores` zijn verschillende voorbeelden geïnstalleerd.

#### De weergave in Sidetrap configureren {#configuring-the-appearance-in-sidekick}

Wanneer het uitgeven van de Context van de Cliënt, verschijnen de componenten van de contextopslag in Sidetrap. Zoals bij alle componenten bepalen de eigenschappen `componentGroup` en `jcr:title` van de component van de cliëntcontext de groep en de naam van de component.

Alle componenten met de eigenschapwaarde `componentGroup` van `Client Context` verschijnen standaard in Sidetrap. Als u voor de eigenschap `componentGroup` een andere waarde gebruikt, moet u de component handmatig aan Sidetrap toevoegen met de ontwerpmodus.

#### Instanties van Context Store-componenten {#context-store-component-instances}

Wanneer u een component van de contextopslag aan de Context van de Cliënt toevoegt, wordt een knoop die de componenteninstantie vertegenwoordigt gecreeerd onder `/etc/clientcontext/default/content/jcr:content/stores`. Dit knooppunt bevat de eigenschapwaarden die zijn geconfigureerd via het dialoogvenster voor bewerken van de component.

Wanneer de Context van de Cliënt wordt geïnitialiseerd, worden deze knopen verwerkt.

#### Bezig met initialiseren van de bijbehorende Sessiewinkel {#initializing-the-associated-session-store}

Voeg een init.js.jsp- dossier aan uw component toe om code te produceren javascript die de zittingsopslag initialiseert die uw component van de contextopslag gebruikt. Gebruik bijvoorbeeld het initialisatiescript om configuratie-eigenschappen voor de component op te halen en deze te gebruiken om de sessieopslag te vullen.

Het gegenereerde JavaScript wordt aan de pagina toegevoegd wanneer de clientcontext wordt geïnitialiseerd bij het laden van de pagina op zowel de auteur- als de publicatieinstantie. Dit JSP wordt uitgevoerd alvorens de instantie van de component van de contextstore wordt geladen en teruggegeven.

De code moet het mime-type van het bestand instellen op `text/javascript`, anders wordt het niet uitgevoerd.

>[!CAUTION]
>
>Het init.js.jsp-script wordt uitgevoerd op de auteur- en publicatie-instantie, maar alleen als de component context store is toegevoegd aan Client Context.

De volgende procedure leidt tot het init.js.jsp manuscriptdossier en voegt de code toe die het correcte mime type plaatst. De code die de opslaginitialisatie uitvoert zou volgen.

1. Klik met de rechtermuisknop op het knooppunt van de contextstore-component en klik op Maken > Bestand maken.
1. Typ `init.js.jsp` in het veld Naam en klik op OK.
1. Voeg boven aan de pagina de volgende code toe en klik op Alles opslaan.

   ```java
   <%@page contentType="text/javascript" %>
   ```

### Het teruggeven van de Gegevens van de Sessieopslag voor GenericusProperties Componenten {#rendering-session-store-data-for-genericstoreproperties-components}

Gegevens van sessieopslagbestanden weergeven in Client Context met een consistente indeling.

#### Eigenschapsgegevens {#displaying-property-data} weergeven

De verpersoonlijkingstabel verstrekt de `personalization:storePropertyTag` markering die de waarde van een bezit van een zittingsopslag toont. Als u de tag wilt gebruiken, neemt u de volgende coderegel op in uw JSP-bestand:

```xml
<%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
```

De tag heeft de volgende indeling:

```xml
<personalization:storePropertyTag propertyName="property_name" store="session_store_name"/>
```

Het `propertyName` attribuut is de naam van het archiefbezit aan vertoning. Het `store` attribuut is de naam van de geregistreerde opslag. De volgende voorbeeldmarkering toont de waarde van het `authorizableId` bezit van `profile` opslag:

```xml
<personalization:storePropertyTag propertyName="authorizableId" store="profile"/>
```

#### HTML-structuur {#html-structure}

De map personalization.ui met clientbibliotheken (/etc/clientlibs/foundation/personalization/ui/themes/default) biedt de CSS-stijlen die door Client Context worden gebruikt om de HTML-code op te maken. De volgende code illustreert de voorgestelde structuur die moet worden gebruikt voor de weergave van opslaggegevens:

```xml
<div class="cq-cc-store">
   <div class="cq-cc-thumbnail">
      <div class="cq-cc-store-property">
           <!-- personalization:storePropertyTag for the store thumbnail image goes here -->
      </div>
   </div>
   <div class="cq-cc-content">
       <div class="cq-cc-store-property cq-cc-store-property-level0">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level1">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level2">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level3">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
   </div>
   <div class="cq-cc-clear"></div>
</div>
```

De contextarchiefcomponent `/libs/cq/personalization/components/contextstores/profiledata` gebruikt deze structuur om gegevens van de opslag van de profielzitting te tonen. De klasse `cq-cc-thumbnail` plaatst de miniatuurafbeelding. De klassen `cq-cc-store-property-level*x*` formatteren de alfanumerieke gegevens:

* level0, level1, en level2 worden verticaal verdeeld, en gebruiken een witte doopvont.
* niveau3 en eventuele extra niveaus worden horizontaal verdeeld en gebruiken een wit lettertype met een donkerdere achtergrond.

![chlimage_1-4](assets/chlimage_1-4.png)

### Sessieopslaggegevens voor generieke opslagcomponenten renderen {#rendering-session-store-data-for-genericstore-components}

Om opslaggegevens terug te geven die een component van de algemeen opslag gebruiken, moet u:

* Voeg de personalization:storeRendererTag-tag toe aan het JSP-script van de component om de naam van de sessieopslag te identificeren.
* Voer een rendermethode op de klasse van de zittingsopslag uit.

#### Het identificeren van de opslag van de genericstore Sessie {#identifying-the-genericstore-session-store}

De verpersoonlijkingstabel verstrekt de `personalization:storePropertyTag` markering die de waarde van een bezit van een zittingsopslag toont. Als u de tag wilt gebruiken, neemt u de volgende coderegel op in uw JSP-bestand:

```xml
<%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
```

De tag heeft de volgende indeling:

```java
<personalization:storeRendererTag store="store_name"/>
```

#### Implementatie van de rendermethode {#implementing-the-session-store-renderer-method} voor de Sessiewinkel

Uw zittingsopslag zal dan een &quot;renderer&quot;methode nodig hebben die zal worden geroepen telkens als de component moet worden teruggegeven. De renderfunctie wordt aangeroepen met twee parameters:

* @param {String} store
De winkel die moet worden gerenderd
* @param {String} divId
Id van de div waarin de opslag moet worden teruggegeven.

## Interactie met Sessiewinkels {#interacting-with-session-stores}

Gebruik javascript om met zittingsopslag in wisselwerking te staan.

### Toegang tot sessiewinkels {#accessing-session-stores}

Vraag een voorwerp van de zittingsopslag om gegevens aan de opslag te lezen of te schrijven. [CQ_Analytics.](/help/sites-developing/ccjsapi.md#cq-analytics-clientcontextmgr) ClientContextMgrsupplies toegang tot opslag die op de archiefnaam wordt gebaseerd. Zodra verkregen, gebruik de methodes van [CQ_Analytics.SessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore) of [CQ_Analytics.PersistedSessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-persistedsessionstore) om met archiefgegevens in wisselwerking te staan.

Het volgende voorbeeld verkrijgt `profile` opslag en wint dan het `formattedName` bezit van de opslag terug.

```
function getName(){
   var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
   if(profilestore){
      return profilestore.getProperty("formattedName", false);
   } else {
      return null;
   }
}
```

### Een listener maken die reageert op een Session Store-update {#creating-a-listener-to-react-to-a-session-store-update}

Sessie slaat brandgebeurtenissen op, zodat het mogelijk is om listeners toe te voegen en gebeurtenissen te activeren die op deze gebeurtenissen zijn gebaseerd.

De sessiewinkels zijn gebaseerd op het `Observable`-patroon. Zij breiden [ `CQ_Analytics.Observable`](/help/sites-developing/ccjsapi.md#cq-analytics-observable) uit die ` [addListener](/help/sites-developing/ccjsapi.md#addlistener-event-fct-scope)` methode verstrekt.

In het volgende voorbeeld wordt een listener toegevoegd aan de gebeurtenis `update` van de sessieopslag `profile`.

```
var profileStore = ClientContextMgr.getRegisteredStore("profile");
if( profileStore ) {
  //callback execution context
  var executionContext = this;

  //add "update" event listener to store
  profileStore.addListener("update",function(store, property) {
    //do something on store update

  },executionContext);
}
```

### Controleren of een Sessiewinkel is gedefinieerd en geïnitialiseerd {#checking-that-a-session-store-is-defined-and-initialized}

Sessiewinkels zijn pas beschikbaar als ze zijn geladen en geïnitialiseerd met gegevens. De volgende factoren kunnen de timing van de beschikbaarheid van de zittingsopslag beïnvloeden:

* Pagina laden
* JavaScript laden
* Uitvoeringstijd van JavaScript
* Responstijden voor XHR-verzoeken
* Dynamische wijzigingen in de sessiewinkel

Gebruik de methoden [CQ_Analytics.ClientContextUtils](/help/sites-developing/ccjsapi.md#cq-analytics-clientcontextutils) van het object [onStoreRegistered](/help/sites-developing/ccjsapi.md#onstoreregistered-storename-callback) en [onStoreInitialized](/help/sites-developing/ccjsapi.md#onstoreinitialized-storename-callback-delay) om sessiewinkels alleen te openen als deze beschikbaar zijn. Met deze methoden kunt u gebeurtenislisteners registreren die reageren op sessieregistratie- en initialisatiegebeurtenissen.

>[!CAUTION]
>
>Als u van een andere opslag afhankelijk bent, moet u rekening houden met het geval wanneer de winkel nooit is geregistreerd.

In het volgende voorbeeld wordt de gebeurtenis `onStoreRegistered` van de sessieopslag `profile` gebruikt. Wanneer de opslag wordt geregistreerd, wordt een luisteraar toegevoegd aan de `update` gebeurtenis van de zittingsopslag. Wanneer de opslag wordt bijgewerkt, wordt de inhoud van het `<div class="welcome">` element op de pagina bijgewerkt met de naam van `profile` opslag.

```
//listen for the store registration
CQ_Analytics.ClientContextUtils.onStoreRegistered("profile", listen);

//listen for the store's update event
function listen(){
 var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
    profilestore.addListener("update",insertName);
}

//insert the welcome message
function insertName(){
 $("div.welcome").text("Welcome "+getName());
}

//obtain the name from the profile store
function getName(){
 var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
 if(profilestore){
  return profilestore.getProperty("formattedName", false);
    } else {
        return null;
    }
}
```

### Een eigenschap uitsluiten van de sessionpersistentie-cookie {#excluding-a-property-from-the-sessionpersistence-cookie}

Om een bezit van `PersistedSessionStore` te verhinderen worden voortgeduurd (d.w.z. sluit het van `sessionpersistence` koekje uit), voeg het bezit aan de niet-persisted bezitslijst van de persistente zittingszittingsopslag toe.

Zie ` [CQ_Analytics.PersistedSessionStore.setNonPersisted(propertyName)](/help/sites-developing/ccjsapi.md#setnonpersisted-name)`

```
CQ_Analytics.ClientContextUtils.onStoreRegistered("surferinfo", function(store) {
  //this will exclude the browser, OS and resolution properties of the surferinfo session store from the
  store.setNonPersisted("browser");
  store.setNonPersisted("OS");
  store.setNonPersisted("resolution");
});
```

## De apparaatschuifregelaar {#configuring-the-device-slider} configureren

### Voorwaarden {#conditions}

De huidige pagina moet een bijbehorende mobiele pagina hebben; dit wordt alleen bepaald als op de pagina een LiveCopy is geconfigureerd met een mobiele rollout-configuratie ( `rolloutconfig.path.toLowerCase` bevat `mobile`).

#### Configuratie {#configuration}

Bij het schakelen van de desktoppagina naar het bijbehorende mobiele equivalent:

* De DOM van de mobiele pagina wordt geladen.
* De hoofdmap `div` (vereist) die de inhoud bevat, wordt uitgepakt en in de huidige desktoppagina geïnjecteerd.

* De CSS- en body-klassen die moeten worden geladen, moeten handmatig worden geconfigureerd.

Bijvoorbeeld:

```
window.CQMobileSlider["geometrixx-outdoors"] = {
  //CSS used by desktop that need to be removed when mobile
  DESKTOP_CSS: [
    "/etc/designs/${app}/clientlibs_desktop_v1.css"
  ],

  //CSS used by mobile that need to be removed when desktop
  MOBILE_CSS: [
    "/etc/designs/${app}/clientlibs_mobile_v1.css"
  ],

  //id of the content that needs to be removed when mobile
  DESKTOP_MAIN_ID: "main",

  //id of the content that needs to be removed when desktop
  MOBILE_MAIN_ID: "main",

  //body classes used by desktop that need to be removed when mobile
  DESKTOP_BODY_CLASS: [
    "page"
  ],

  //body classes used by mobile that need to be removed when desktop
  MOBILE_BODY_CLASS: [
    "page-mobile"
  ]
};
```

## Voorbeeld: Aangepaste contextwinkelcomponent maken {#example-creating-a-custom-context-store-component}

In dit voorbeeld maakt u een contextopslagcomponent die gegevens van een externe service ophaalt en deze in de sessieopslag opslaat:

* Breidt de genericstoreproperties-component uit.
* Initialiseert een winkel met behulp van een Javascript-object CQ_Analytics.JSONPStore.
* Roept de dienst JSONP om gegevens terug te winnen en het toe te voegen aan de opslag.
* Geeft de gegevens in de Context van de Cliënt terug.

### De geoloc-component {#add-the-geoloc-component} toevoegen

Maak een CQ-toepassing en voeg de geoloc-component toe.

1. Open CRXDE Lite in uw Webbrowser ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Klik met de rechtermuisknop op de map `/apps` en klik op Maken > Map maken. Geef een naam op van `myapp` en klik op OK.
1. Maak onder `myapp` ook een map met de naam `contextstores`. &quot;
1. Klik met de rechtermuisknop op de map `/apps/myapp/contextstores` en klik op Maken > Component maken. Geef de volgende eigenschapswaarden op en klik op Volgende:

   * Label: geoloc
   * Titel: Locatiewinkel
   * Supertype: cq/personalization/components/contextstores/genericstoreproperties
   * Groep: Clientcontext

1. Klik in het dialoogvenster Component maken op Volgende op elke pagina totdat de knop OK is ingeschakeld. Klik vervolgens op OK.
1. Klik op Alles opslaan.

### Dialoogvenster voor geoloc bewerken maken {#create-the-geoloc-edit-dialog}

Voor de component Context Store is een dialoogvenster voor bewerken vereist. Het dialoogvenster voor geoloc-bewerking bevat een statisch bericht dat aangeeft dat er geen eigenschappen zijn die kunnen worden geconfigureerd.

1. Klik met de rechtermuisknop op het knooppunt `/libs/cq/personalization/components/contextstores/genericstoreproperties/dialog` en klik op Kopiëren.
1. Klik met de rechtermuisknop op het knooppunt `/apps/myapp/contextstores/geoloc` en klik op Plakken.
1. Verwijder alle onderliggende knooppunten onder het knooppunt /apps/myapp/contextstores/geoloc/dialog/items/items/tab1/items:

   * winkel
   * eigenschappen
   * miniatuur

1. Klik met de rechtermuisknop op het knooppunt `/apps/myapp/contextstores/geoloc/dialog/items/items/tab1/items` en klik op Maken > Knooppunt maken. Geef de volgende eigenschapswaarden op en klik op OK:

   * Naam: static
   * Type: cq:Widget

1. Voeg de volgende eigenschappen toe aan het knooppunt:

   | Naam | Type | Waarde |
   |---|---|---|
   | cls | Tekenreeks | x-form-field-set-description |
   | text | Tekenreeks | Voor de geoloc-component is geen configuratie vereist. |
   | xtype | Tekenreeks | statisch |

1. Klik op Alles opslaan.

   ![chlimage_1-5](assets/chlimage_1-5.png)

### Het initialisatiescript maken {#create-the-initialization-script}

Voeg een init.js.jsp-bestand toe aan de geoloc-component en gebruik dit bestand om de sessieopslag te maken, de locatiegegevens op te halen en toe te voegen aan de winkel.

Het bestand init.js.jsp wordt uitgevoerd wanneer de clientcontext door de pagina wordt geladen. Tegen deze tijd wordt de JavaScript-API voor clientcontext geladen en beschikbaar voor uw script.

1. Klik met de rechtermuisknop op het knooppunt /apps/myapp/contextstores/geoloc en klik op Maken > Bestand maken. Geef een naam op voor init.js.jsp en klik op OK.
1. Voeg de volgende code toe boven aan de pagina en klik op Alles opslaan.

   ```java
   <%@page contentType="text/javascript;charset=utf-8" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   log.info("***** initializing geolocstore ****");
   String store = "locstore";
   String jsonpurl = "https://api.wipmania.com/jsonp?callback=${callback}";
   
   %>
   var locstore = CQ_Analytics.StoreRegistry.getStore("<%= store %>");
   if(!locstore){
    locstore = CQ_Analytics.JSONPStore.registerNewInstance("<%= store %>", "<%= jsonpurl %>",{});
   }
   <% log.info(" ***** done initializing geoloc ************"); %>
   ```

### De geoloc Session Store-gegevens {#render-the-geoloc-session-store-data} renderen

Voeg de code aan het JSP dossier van de geologische component toe om de opslaggegevens in de Context van de Cliënt terug te geven.

![chlimage_1-6](assets/chlimage_1-6.png)

1. Open het bestand `/apps/myapp/contextstores/geoloc/geoloc.jsp` in CRXDE Lite.
1. Voeg de volgende HTML-code onder de sectie-code toe:

   ```xml
   <%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
   <div class="cq-cc-store">
      <div class="cq-cc-content">
          <div class="cq-cc-store-property cq-cc-store-property-level0">
              Continent: <personalization:storePropertyTag propertyName="address/continent" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level1">
              Country: <personalization:storePropertyTag propertyName="address/country" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level2">
              City: <personalization:storePropertyTag propertyName="address/city" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level3">
              Latitude: <personalization:storePropertyTag propertyName="latitude" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level4">
              Longitude: <personalization:storePropertyTag propertyName="longitude" store="locstore"/>
          </div>
      </div>
       <div class="cq-cc-clear"></div>
   </div>
   ```

1. Klik op Alles opslaan.

### Component toevoegen aan clientcontext {#add-the-component-to-client-context}

Voeg de component van de Opslag van de Plaats aan de Context van de Cliënt toe zodat het wordt geïnitialiseerd wanneer de pagina laadt.

1. Open de homepage van Geometrixx Outdoors op de auteursinstantie ([https://localhost:4502/content/geometrixx-outdoors/en.html](https://localhost:4502/content/geometrixx-outdoors/en.html)).
1. Klik op Ctrl-Alt-c (vensters) of Control-option-c (Mac) om Client Context te openen.
1. Klik op het bewerkingspictogram boven aan Client Context om Client Context Designer te openen.

   ![](do-not-localize/chlimage_1.png)

1. Sleep de component van de Opslag van de Plaats aan de Context van de Cliënt.

### Zie Locatie-informatie in clientcontext {#see-the-location-information-in-client-context}

Open de homepage van Geometrixx Outdoors in geef wijze uit en open dan de Context van de Cliënt om de gegevens van de component van de Opslag van de Plaats te zien.

1. Open de Engelse pagina van de site Geometrixx Outdoors. ([https://localhost:4502/content/geometrixx-outdoors/en.html](https://localhost:4502/content/geometrixx-outdoors/en.html))
1. Druk op Ctrl+Alt+c (vensters) of Control+Option+c (Mac) om de clientcontext te openen.

## Een aangepaste clientcontext maken {#creating-a-customized-client-context}

Als u een tweede clientcontext wilt maken, moet u de vertakking dupliceren:

`/etc/clientcontext/default`

* De submap:
   `/content`
bevat de inhoud van de aangepaste clientcontext.

* De map:
   `/contextstores`
staat u toe om verschillende configuraties voor de contextopslag te bepalen.

Als u de aangepaste clientcontext wilt gebruiken, bewerkt u de eigenschap
`path`
in de ontwerpstijl van de component van de cliëntcontext, zoals inbegrepen in het paginamalplaatje. Bijvoorbeeld als de standaardlocatie van:
`/libs/cq/personalization/components/clientcontext/design_dialog/items/path`
