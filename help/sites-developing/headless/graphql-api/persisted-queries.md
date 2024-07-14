---
title: Blijvende GraphQL-query's
description: Leer hoe u GraphQL-query's in Adobe Experience Manager kunt voortzetten voor optimale prestaties. De aanhoudende vragen kunnen door cliënttoepassingen worden gevraagd gebruikend de methode van de GET van HTTP en de reactie kan bij de lagen worden in het voorgeheugen ondergebracht Dispatcher en CDN, uiteindelijk verbeterend de prestaties van de cliënttoepassingen.
exl-id: d7a1955d-b754-4700-b863-e9f66396cbe1
solution: Experience Manager, Experience Manager Sites
feature: Content Fragments,GraphQL API
role: Developer
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1401'
ht-degree: 0%

---

# Blijvende GraphQL-query&#39;s {#persisted-queries-caching}

Blijvende query&#39;s zijn GraphQL-query&#39;s die zijn gemaakt en opgeslagen op de Adobe Experience Manager (AEM)-server. Ze kunnen worden aangevraagd met een GET-aanvraag door clienttoepassingen. De reactie van een verzoek van de GET kan bij de lagen van het Netwerk van de Levering van de Dispatcher en van de Inhoud (CDN) worden in het voorgeheugen ondergebracht, uiteindelijk verbeterend de prestaties van de het verzoeken cliënttoepassing. Dit verschilt van standaard GraphQL query&#39;s, die worden uitgevoerd met behulp van POST-aanvragen waarbij de reactie niet gemakkelijk in cache kan worden geplaatst.

<!--
>[!NOTE]
>
>Persisted Queries are recommended. See [GraphQL Query Best Practices (Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) for details, and the related Dispatcher configuration.
-->

[ IDE GraphiQL ](/help/sites-developing/headless/graphql-api/graphiql-ide.md) is beschikbaar in AEM voor u om, uw vragen van GraphQL te ontwikkelen te testen en voort te zetten, alvorens [ over te brengen naar uw productiemilieu ](#transfer-persisted-query-production). Voor gevallen die aanpassing (bijvoorbeeld, wanneer [ het geheime voorgeheugen ](/help/sites-developing/headless/graphql-api/graphiql-ide.md#caching-persisted-queries) aanpassen) nodig hebben kunt u API gebruiken; zie het cURL voorbeeld dat in [ wordt verstrekt hoe te om een vraag van GraphQL ](#how-to-persist-query) voort te zetten.

## Blijvende query&#39;s en eindpunten {#persisted-queries-and-endpoints}

De aangehouden vragen moeten altijd het eindpunt met betrekking tot de [ aangewezen configuratie van Plaatsen ](/help/sites-developing/headless/graphql-api/graphql-endpoint.md) gebruiken; zodat kunnen zij of, of allebei gebruiken:

* De globale configuratie en het eindpunt
De query heeft toegang tot alle modellen van inhoudsfragmenten.
* Specifieke configuratie(s) en eindpunt(en) van sites
Creërend een persisted vraag voor een specifieke configuratie van Plaatsen vereist een overeenkomstig plaats-configuratie-specifiek eindpunt (om toegang tot de verwante Modellen van het Fragment van de Inhoud te verlenen).
Bijvoorbeeld, om een voortgeduurde vraag specifiek voor de configuratie van Plaatsen te creëren WKND, moet een overeenkomstige WKND-Specifieke configuratie van Plaatsen, en een WKND-Specifiek eindpunt vooraf worden gecreeerd.

>[!NOTE]
>
>Zie [ Functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie ](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) voor meer details toelaten.
>
>De **GraphQL Persisted Vragen** moeten worden toegelaten, voor de aangewezen configuratie van Plaatsen.

Als er bijvoorbeeld een bepaalde query met de naam `my-query` is, die een model `my-model` uit de configuratie Sites `my-conf` gebruikt:

* U kunt een vraag tot stand brengen gebruikend het `my-conf` specifieke eindpunt, en dan zal de vraag als volgt worden bewaard:
  `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* U kunt dezelfde query maken met het eindpunt `global` , maar de query wordt als volgt opgeslagen:
  `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Dit zijn twee verschillende query&#39;s die zijn opgeslagen onder verschillende paden.
>
>Ze gebruiken gewoon hetzelfde model, maar via verschillende eindpunten.

## Een GraphQL-query laten doorgaan {#how-to-persist-query}

Het wordt geadviseerd om vragen over een AEM auteursmilieu aanvankelijk en dan [ over te zetten de vraag ](#transfer-persisted-query-production) aan uw productie AEM milieu, voor gebruik door toepassingen publiceren.

Er zijn verschillende methoden om query&#39;s te blijven uitvoeren, waaronder:

* IDE GraphiQL - zie [ het Opslaan van Persisted Vragen ](/help/sites-developing/headless/graphql-api/graphiql-ide.md#saving-persisted-queries) (aangewezen methode)
* cURL - zie het volgende voorbeeld
* Andere hulpmiddelen, met inbegrip van [ Postman ](https://www.postman.com/)

IDE GraphiQL is de **geprefereerde** methode voor het voortduren van vragen. Om een bepaalde vraag voort te zetten gebruikend het **cURL** hulpmiddel van de bevellijn:

1. Bereid de vraag voor door het aan het nieuwe eindpunt URL `/graphql/persist.json/<config>/<persisted-label>` te PLAATSEN.

   Maak bijvoorbeeld een doorlopende query:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. Controleer nu het antwoord.

   Controleer bijvoorbeeld of het programma is gelukt:

   ```json
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Vervolgens kunt u de voortgezette query aanvragen door de URL op te halen `/graphql/execute.json/<shortPath>` .

   Gebruik bijvoorbeeld de voortgezette query:

   ```shell
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Werk een voortgezette vraag door POSTing aan een reeds bestaand vraagweg bij.

   Gebruik bijvoorbeeld de voortgezette query:

   ```shell
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. Een onbewerkte query maken.

   Bijvoorbeeld:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Creeer een verpakte onbewerkte vraag met geheim voorgeheugencontrole.

   Bijvoorbeeld:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Maak een doorlopende query met parameters:

   Bijvoorbeeld:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```


## Hoe te om een Verlengde vraag uit te voeren {#execute-persisted-query}

Een clienttoepassing vraagt een aanvraag tot GET met de volgende syntaxis uit om een query met behoud van waarden uit te voeren:

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

Waar `PERSISTENT_PATH` een verkort pad is naar waar de Persisted-query wordt opgeslagen.

1. `wknd` is bijvoorbeeld de configuratienaam en `plain-article-query` is de naam van de Persisted-query. De query uitvoeren:

   ```shell
   $ curl -X GET \
       https://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Een query uitvoeren met parameters.

   >[!NOTE]
   >
   > De variabelen en de waarden van de vraag moeten behoorlijk [ worden gecodeerd ](#encoding-query-url) wanneer het uitvoeren van een Verlengde vraag.

   Bijvoorbeeld:

   ```bash
   $ curl -X GET \
       "https://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   Zie het gebruiken van [ vraagvariabelen ](#query-variables) voor meer details.

## Query-variabelen gebruiken {#query-variables}

De variabelen van de vraag kunnen met Verblijfsde Vragen worden gebruikt. De vraagvariabelen worden toegevoegd aan het verzoek vooraf bepaald met een puntkomma (`;`) gebruikend de veranderlijke naam en de waarde. Meerdere variabelen worden gescheiden door puntkomma&#39;s.

Het patroon ziet er als volgt uit:

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

De volgende query bevat bijvoorbeeld een variabele `activity` om een lijst te filteren op basis van een activiteitwaarde:

```graphql
query getAdventuresByActivity($activity: String!) {
      adventureList (filter: {
        adventureActivity: {
          _expressions: [
            {
              value: $activity
            }
          ]
        }
      }){
        items {
          _path
        adventureTitle
        adventurePrice
        adventureTripLength
      }
    }
  }
```

Deze query kan worden uitgevoerd onder een pad `wknd/adventures-by-activity` . Om de Persisted vraag te roepen waar `activity=Camping` het verzoek als dit zou kijken:

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

`%3B` is de UTF-8-codering voor `;` en `%3D` is de codering voor `=` . De vraagvariabelen en om het even welke speciale karakters moeten [ behoorlijk ](#encoding-query-url) voor de Persisted vraag worden gecodeerd om uit te voeren.

## Door uw doorlopende query&#39;s in cache te plaatsen {#caching-persisted-queries}

De geadviseerde vragen worden geadviseerd aangezien zij bij de [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) en de lagen van het Netwerk van de Levering van de Inhoud (CDN) in het voorgeheugen kunnen worden ondergebracht, uiteindelijk verbeterend de prestaties van de het vragen cliënttoepassing.

AEM maakt de cache standaard ongeldig op basis van de definitie Tijd tot live (TTL). Deze TTLs kan door de volgende parameters worden bepaald. Deze parameters zijn op verschillende manieren toegankelijk, waarbij de namen variëren volgens het gebruikte mechanisme:

| Cachetype | [ HTTP- kopbal ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control)  | cURL  | OSGi-configuratie  |
|--- |--- |--- |--- |
| Browser | `max-age` | `cache-control : max-age` | `cacheControlMaxAge` |
| CDN | `s-maxage` | `surrogate-control : max-age` | `surrogateControlMaxAge` |
| CDN | `stale-while-revalidate` | `surrogate-control : stale-while-revalidate ` | `surrogateControlStaleWhileRevalidate` |
| CDN | `stale-if-error` | `surrogate-control : stale-if-error` | `surrogateControlStaleIfError` |

{style="table-layout:auto"}

### Auteursinstanties {#author-instances}

Voor auteur-instanties zijn de standaardwaarden:

* `max-age` : 60
* `s-maxage` : 60
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Hiervoor gold het volgende:

* kan niet met een configuratie OSGi worden beschreven
* kan door een verzoek worden beschreven dat de kopbalmontages van HTTP gebruikend cURL bepaalt; het zou geschikte montages voor `cache-control` en/of `surrogate-control` moeten omvatten; voor voorbeelden, zie [ het Leiden Geheime voorgeheugen bij het Persisted Niveau van de Vraag ](#cache-persisted-query-level)

<!-- CQDOC-20186 -->
<!-- following entry is only when the GraphiQL IDE is ready; add cross-reference too -->
<!--
* can be overwritten if you specify values in the **Headers** dialog of the [GraphiQL IDE](#http-cache-headers-graphiql-ide)
-->

### Publish-instanties {#publish-instances}

Voor publicatie-instanties zijn de standaardwaarden:

* `max-age` : 60
* `s-maxage` : 7200
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Deze kunnen worden overschreven:

<!-- CQDOC-20186 -->
<!-- following entry is only when the GraphiQL IDE is ready -->
<!--
* [from the GraphQL IDE](#http-cache-headers-graphiql-ide)
-->

* [ bij het Verblijfsde Niveau van de Vraag ](#cache-persisted-query-level); dit impliceert het posten van de vraag aan AEM gebruikend cURL in uw interface van de bevellijn, en het publiceren van de Verlengde Vraag.

* [met een OSGi-configuratie](#cache-osgi-configration)

<!-- CQDOC-20186 -->
<!-- keep for future use; check link -->
<!--
### Managing HTTP Cache Headers in the GraphiQL IDE {#http-cache-headers-graphiql-ide}

The GraphiQL IDE - see [Saving Persisted Queries](/help/sites-developing/headless/graphql-api/graphiql-ide.md#managing-cache)
-->

### Het beheren van Geheime voorgeheugen op het Aanhoudende Niveau van de Vraag {#cache-persisted-query-level}

Dit omvat het posten van de vraag aan AEM gebruikend cURL in uw interface van de bevellijn.

Een voorbeeld van de methode PUT (create):

```bash
curl -u admin:admin -X PUT \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

Een voorbeeld van de methode POST (update):

```bash
curl -u admin:admin -X POST \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

`cache-control` kan op de aanmaaktijd (PUT) of later worden ingesteld (bijvoorbeeld via een verzoek om POST). Het cache-control is optioneel wanneer u de aanhoudend query maakt, omdat AEM de standaardwaarde kan opgeven. Zie [ hoe te om een vraag van GraphQL ](#how-to-persist-query), voor een voorbeeld voort te zetten om een vraag te gebruiken cURL.

### Het beheren van Geheime voorgeheugen met een configuratie OSGi {#cache-osgi-configration}

Om het geheime voorgeheugen globaal te beheren, kunt u [ de montages OSGi ](/help/sites-deploying/configuring-osgi.md) voor de **Verlengde Configuratie van de Dienst van de Vraag** vormen. Anders gebruikt deze configuratie OSGi de [ standaardwaarden voor publiceer instanties ](#publish-instances).

>[!NOTE]
>
>De configuratie OSGi is slechts aangewezen voor publiceer instanties. De configuratie bestaat bij de instanties van de auteur, maar wordt genegeerd.

## De URL van de query coderen voor gebruik door een app {#encoding-query-url}

Voor gebruik door een toepassing, moeten om het even welke speciale karakters die worden gebruikt wanneer het construeren van vraagvariabelen (d.w.z. puntkomma&#39;s (`;`), gelijkteken (`=`), schuine strepen `/`) worden omgezet om het overeenkomstige coderen te gebruiken UTF-8.

Bijvoorbeeld:

```bash
curl -X GET \ "https://localhost:4502/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

De URL kan worden opgesplitst in de volgende onderdelen:

| URL-onderdeel | Beschrijving |
|----------| -------------|
| `/graphql/execute.json` | Blijvend vraageindpunt |
| `/wknd/adventure-by-path` | Pad voor permanente query |
| `%3B` | Codering van `;` |
| `adventurePath` | Query-variabele |
| `%3D` | Codering van `=` |
| `%2F` | Codering van `/` |
| `%2Fcontent%2Fdam...` | Gecodeerd pad naar het inhoudsfragment |

In onbewerkte tekst ziet de aanvraag-URI er als volgt uit:

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

Om een voortgezette vraag in een cliënttoepassing te gebruiken, zou de AEM headless cliënt SDK voor [ JavaScript ](https://github.com/adobe/aem-headless-client-js), [ Java ](https://github.com/adobe/aem-headless-client-java), of [ NodeJS ](https://github.com/adobe/aem-headless-client-nodejs) moeten worden gebruikt. De Headless Client SDK codeert alle queryvariabelen automatisch naar behoren in de aanvraag.

## Het overbrengen van een blijvende vraag aan uw milieu van de Productie  {#transfer-persisted-query-production}

De gepersisteerde vragen zouden altijd op de dienst van de Auteur van de AEM moeten worden gecreeerd en dan (herhaald) aan de dienst van AEM Publish gepubliceerd. Vaak, worden de Persisted vragen gecreeerd en op lagere milieu&#39;s zoals lokale of milieu&#39;s van de Ontwikkeling getest. Het is dan noodzakelijk om Persisted query&#39;s naar omgevingen op een hoger niveau te promoten, zodat ze uiteindelijk beschikbaar worden gesteld op een productie AEM Publish-omgeving voor gebruik door clienttoepassingen.

### Voorbehouden query&#39;s verpakken

De aanhoudende vragen kunnen in [ AEM Pakketten ](/help/sites-administering/package-manager.md) worden gebouwd. AEM pakketten kunnen vervolgens worden gedownload en geïnstalleerd in verschillende omgevingen. AEM Pakketten kunnen ook worden gerepliceerd vanuit een AEM Auteur-omgeving naar AEM Publish-omgevingen.

Een pakket maken:

1. Navigeer aan **Hulpmiddelen** > **Plaatsing** > **Pakketten**.
1. Creeer een pakket door **te tikken creeer Pakket**. Hiermee wordt een dialoogvenster geopend waarin u het pakket kunt definiëren.
1. In de Dialoog van de Definitie van het Pakket, onder **Algemene** ga a **Naam** als &quot;wknd-persistente-query&#39;s&quot; in.
1. Voer een versienummer in, bijvoorbeeld &quot;1.0&quot;.
1. Onder **Filters** voeg een nieuwe **Filter** toe. Gebruik de Finder van het Weg om de `persistentQueries` omslag onder de configuratie te selecteren. Voor de `wknd` -configuratie is het volledige pad bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries` .
1. Selecteer **sparen** om de nieuwe definitie van het Pakket te bewaren en de dialoog te sluiten.
1. Selecteer **bouwt** knoop in de pas gecreëerde definitie van het Pakket.

Nadat het pakket is gemaakt, kunt u:

* **Download** het pakket en herupload op een verschillend milieu.
* **Repliceer** het pakket door **meer** te tikken > **Repliceer**. Hierdoor wordt het pakket gerepliceerd naar de aangesloten AEM Publish-omgeving.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, among others).
-->
