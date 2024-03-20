---
title: GraphiQL IDE gebruiken in AEM
description: Leer hoe u de GraphiQL IDE in Adobe Experience Manager gebruikt.
exl-id: d4b01485-658b-4245-b2e6-04be8abc8ecf
solution: Experience Manager, Experience Manager Sites
feature: Content Fragments,GraphQL API
role: Developer
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# GraphiQL IDE gebruiken {#graphiql-ide}

Tenuitvoerlegging van de norm [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE is beschikbaar voor gebruik met de GraphQL API van Adobe Experience Manager (AEM).

>[!NOTE]
>
>GraphiQL is inbegrepen in alle milieu&#39;s van AEM (maar zal slechts toegankelijk/zichtbaar zijn wanneer u uw eindpunten vormt).
>
>In vorige versies was een pakket nodig om de GraphiQL IDE te installeren. Als u deze installatie hebt, kunt u deze nu verwijderen.

>[!NOTE]
>U moet [Uw eindpunten geconfigureerd](/help/sites-developing/headless/graphql-api/graphql-endpoint.md) in de [configuratievenster](/help/assets/content-fragments/content-fragments-configuration-browser.md) voordat u GraphiQL IDE gebruikt.

De **GraphiQL** kunt u testen en fouten opsporen in uw GraphQL-query&#39;s door het volgende in te schakelen:

* Selecteer de **Endpoint** aangewezen aan de configuratie van Plaatsen die u voor uw vragen wilt gebruiken
* direct nieuwe query&#39;s invoeren
* creëren en openen, **[Blijvende query&#39;s](/help/sites-developing/headless/graphql-api/persisted-queries.md)**
* stel uw vragen in werking om de resultaten onmiddellijk te zien
* beheren **Query-variabelen**
* opslaan en beheren **Blijvende query&#39;s**
* publiceren of publiceren ongedaan maken, **Blijvende query&#39;s** (bijvoorbeeld van/naar `dev-publish`)
* zie **Historie** van uw vorige vragen
* gebruiken **Documentatieverkenner** om toegang te krijgen tot de documentatie, zodat u kunt leren welke methoden beschikbaar zijn en begrijpen.

U kunt tot de vraagredacteur van één van beiden toegang hebben:

* **Gereedschappen** > **Algemeen** > **GraphQL Query Editor**
* rechtstreeks; bijvoorbeeld `http://localhost:4502/aem/graphiql.html`

![GraphiQL Interface](assets/cfm-graphiql-interface.png "GraphiQL Interface")

U kunt GraphiQL op uw systeem gebruiken zodat de vragen door uw cliënttoepassing kunnen worden gevraagd gebruikend verzoeken, en voor het publiceren van vragen. Voor productiegebruik kunt u vervolgens [verplaats uw vragen naar uw productieomgeving](/help/sites-developing/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Aanvankelijk aan productieauteur voor het bevestigen van onlangs authored inhoud met de vragen, en productie publiceren voor levende consumptie.

## Het selecteren van uw eindpunt {#selecting-endpoint}

Als eerste stap moet u de **[Endpoint](/help/sites-developing/headless/graphql-api/graphql-endpoint.md)** die u voor de vragen wilt gebruiken. Het eindpunt is aangewezen aan de configuratie van Plaatsen die u voor uw vragen wilt gebruiken.

Dit is beschikbaar in de vervolgkeuzelijst rechtsboven.

## Een nieuwe query maken en doorgaan {#creating-new-query}

U kunt uw nieuwe vraag in de redacteur ingaan - die in het midden-linkerpaneel, direct onder het logo GraphiQL is.

>[!NOTE]
>
>Als u al een aanhoudende query hebt geselecteerd en in het deelvenster Editor wordt weergegeven, selecteert u `+` (naast **Blijvende query&#39;s**) om de editor leeg te maken voor de nieuwe query.

Begin gewoon te typen, de redacteur ook:

* gebruikt mouseOver om aanvullende informatie over elementen weer te geven
* biedt functies zoals syntaxismarkering, automatisch aanvullen en automatisch voorstellen

>[!NOTE]
>
>GraphQL-query&#39;s beginnen doorgaans met een `{` teken.
>
>Lijnen die beginnen met een `#` worden genegeerd.

Gebruiken **Opslaan als** om uw nieuwe vraag voort te zetten.

## Uw voortgezette query bijwerken {#updating-persisted-query}

Selecteer de query die u wilt bijwerken in de lijst in het dialoogvenster **[Blijvende query&#39;s](/help/sites-developing/headless/graphql-api/persisted-queries.md)** (helemaal links).

De vraag wordt getoond in het redacteurspaneel. Breng de gewenste wijzigingen aan en gebruik vervolgens **Opslaan** om uw updates aan de persisted query vast te leggen.

## Query&#39;s uitvoeren {#running-queries}

U kunt een nieuwe vraag in werking stellen onmiddellijk, of u kunt een voortgezette vraag laden en in werking stellen. Als u een voortgezette query wilt laden, selecteert u deze in de lijst. De query wordt weergegeven in het deelvenster Editor.

In beide gevallen is de query die wordt weergegeven in het editorpaneel de query die wordt uitgevoerd wanneer u een van de volgende twee doet:

* klik op de **Query uitvoeren** pictogram
* de toetsenbordcombinatie gebruiken `Control-Enter`

## Query-variabelen {#query-variables}

<!-- more details needed here? -->

Met GraphiQL IDE kunt u ook uw [Query-variabelen](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphql-variables).

Bijvoorbeeld:

![GraphQL-variabelen](assets/cfm-graphqlapi-03.png "GraphQL-variabelen")

<!--
## Managing cache for your persisted queries {#managing-cache}

[Persisted queries](/help/headless/graphql-api/persisted-queries.md) are recommended as they can be cached at the dispatcher and CDN layers, ultimately improving the performance of the requesting client application. By default AEM will invalidate the Content Delivery Network (CDN) cache based on a default Time To Live (TTL).

>[!NOTE]
>
>Custom rewrite rules on the Dispatcher might override defaults from AEM publish. 
>
>In the case that you are sending TTL-based cache-control headers from the dispatcher, based on a location match pattern then, if necessary, you might want to exclude `/graphql/execute.json/*` from the matches.

Using GraphQL you can configure the HTTP Cache Headers  to control these parameters for your individual persisted query.

1. The **Headers** option is accessible via the three vertical dots to the right of the persisted query name (far left panel):

   ![Persisted Query HTTP Cache Headers](assets/cfm-graphqlapi-headers-01.png "Persisted Query HTTP Cache Headers")

1. Selecting this opens the **Cache Configuration** dialog box:

   ![Persisted Query HTTP Cache Header Settings](assets/cfm-graphqlapi-headers-02.png "Persisted Query HTTP Cache Header Settings")

1. Select the appropriate parameter, then adjust the value as required:

   * **cache-control** - **max-age**
     Caches can store this content for specified number of seconds. Typically this is the browser TTL (Time To Live).
   * **surrogate-control** - **s-maxage**
     Same as max-age but applies specifically to proxy caches.
   * **surrogate-control** - **stale-while-revalidate**
     Caches may continue to serve a cached response after it becomes stale, for up to the specified number of seconds.
   * **surrogate-control** - **stale-if-error**
     Caches may continue to serve a cached response if there is an origin error, for up to the specified number of seconds.

1. Select **Save** to persist the changes.
-->

## Het publiceren van voortgeduurde vragen {#publishing-persisted-queries}

Als u eenmaal uw [voortgezette query](/help/sites-developing/headless/graphql-api/persisted-queries.md) in de lijst (linkerdeelvenster) kunt u de opdracht **Publiceren** en **Publiceren ongedaan maken** handelingen. Hiermee worden ze geactiveerd in uw publicatieomgeving (bijvoorbeeld `dev-publish`) voor eenvoudige toegang door uw toepassingen tijdens het testen.

>[!NOTE]
>
>De definitie van het voorgeheugen van de persisted query `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} heeft een standaardwaarde van 2 uur (7200 seconden).

## URL kopiëren om rechtstreeks toegang te krijgen tot de query {#copy-url}

De **URL kopiëren** Met deze optie kunt u een query simuleren door de URL te kopiëren die wordt gebruikt om rechtstreeks toegang te krijgen tot de voortgezette query en de resultaten te bekijken. Dit kan vervolgens voor testdoeleinden worden gebruikt, bijvoorbeeld door toegang te krijgen tot een browser:

<!--
  >[!NOTE]
  >
  >The URL will need [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
  >
  >The target environment might need adjusting, depending on your requirements.
-->

Bijvoorbeeld:

`http://localhost:4502/graphql/execute.json/global/article-list-01`

Door deze URL in browser te gebruiken, kunt u de resultaten bevestigen:

![GraphiQL - URL kopiëren](assets/cfm-graphiql-copy-url.png "GraphiQL - URL kopiëren")

De **URL kopiëren** Deze optie is toegankelijk via de drie verticale stippen rechts van de naam van de voortgezette query (het linkerdeelvenster):

![GraphiQL - URL kopiëren](assets/cfm-graphiql-persisted-query-options.png "GraphiQL - URL kopiëren")

## Doorlopende query&#39;s verwijderen {#deleting-persisted-queries}

De **Verwijderen** Deze optie is ook toegankelijk via de drie verticale stippen rechts van de naam van de blijvend query (het linkerdeelvenster).

<!-- what happens if you try to delete something that is still published? -->


## Uw blijvende query installeren op productie {#installing-persisted-query-production}

Na het ontwikkelen van en het testen van uw persistente vraag met GraphiQL, is het definitieve doel: [deze naar uw productieomgeving overbrengen](/help/sites-developing/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production) voor gebruik door uw toepassingen.

## Sneltoetsen {#keyboard-shortcuts}

Er zijn een selectie van toetsenbordkortere weg die directe toegang tot actiepictogrammen in winde verlenen:

* Query uitvoeren:  `Shift-Control-P`
* Query samenvoegen:  `Shift-Control-M`
* Query uitvoeren:  `Control-Enter`
* Automatisch aanvullen:  `Control-Space`

>[!NOTE]
>
>Op sommige toetsenborden `Control` key is gelabeld als `Ctrl`.
