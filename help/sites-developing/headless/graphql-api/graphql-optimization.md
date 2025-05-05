---
title: GraphQL-query's optimaliseren
description: Leer hoe u uw GraphQL-query's kunt optimaliseren tijdens het filteren, pagineren en sorteren van uw Content Fragments in Adobe Experience Manager as a Cloud Service voor levering van inhoud zonder kop.
exl-id: 47d0570b-224e-4109-b94e-ccc369d7ac5f
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1949'
ht-degree: 0%

---

# GraphQL-query&#39;s optimaliseren {#optimizing-graphql-queries}

>[!NOTE]
>
>Alvorens u deze optimaliseringsaanbevelingen toepast, overweeg [ Bijwerkend uw Fragmenten van de Inhoud voor het pagineren en het Sorteren in het Filtreren van GraphQL ](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md) voor beste prestaties.

Deze richtlijnen zijn bedoeld om prestatieproblemen met uw GraphQL-query&#39;s te voorkomen.

## GraphQL Checklist {#graphql-checklist}

De volgende controlelijst is bedoeld om u te helpen bij het optimaliseren van de configuratie en het gebruik van GraphQL in Adobe Experience Manager (AEM) as a Cloud Service.

### Eerste beginselen {#first-principles}

#### Gebruik doorlopende GraphQL-query&#39;s {#use-persisted-graphql-queries}

**Aanbeveling**

Het gebruik van doorlopende GraphQL-query&#39;s wordt sterk aanbevolen.

Blijvende GraphQL-query&#39;s helpen de prestaties van de query te verminderen door gebruik te maken van CDN (Content Delivery Network). Clienttoepassingen hebben doorlopende query&#39;s aangevraagd met GET-aanvragen voor snelle uitvoering met randfunctionaliteit.

**Verdere Verwijzing**

Zie:

* [ Blijven de vragen van GraphQL ](/help/sites-developing/headless/graphql-api/persisted-queries.md).
* [GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md)

#### Het GraphQL-indexpakket installeren {#install-graphql-index-package}

**Aanbeveling**

De klanten die GraphQL gebruiken *moeten* het Fragment van de Inhoud van de Experience Manager met het Pakket van de Index van GraphQL installeren. Zo kunt u de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken. Als u dit pakket niet installeert, kan dit leiden tot trage of mislukte GraphQL-query&#39;s.

Zie de Nota&#39;s van de Versie voor de versie aangewezen aan uw Service Pack. Bijvoorbeeld, voor het recentste Pak van de Dienst, zie [ het Pakket van de Index van GraphQL voor de Fragmenten van de Inhoud van de Experience Manager installeren ](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package).

>[!NOTE]
>
>Installeer dit pakket slechts eenmaal per instantie; het hoeft niet opnieuw te worden geïnstalleerd met elk Service Pack.

**Verdere Verwijzing**
Zie:

* [GraphQL-indexpakket voor Experience Manager-inhoudsfragmenten installeren](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package)

### Cachestrategie {#cache-strategy}

Verschillende methoden voor het in cache plaatsen kunnen ook worden gebruikt voor optimalisatie.

#### In cache AEM Dispatcher plaatsen {#enable-aem-dispatcher-caching}

**Aanbeveling**

[ AEM Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL) is het eerste niveaugeheime voorgeheugen binnen de AEM dienst, vóór CDN geheime voorgeheugen.

**Verdere Verwijzing**

Zie:

* [GraphQL Persisted Queries - caching inschakelen in Dispatcher](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphql-persisted-queries-enabling-caching-dispatcher)

#### Een CDN (Content Delivery Network) gebruiken {#use-cdn}

**Aanbeveling**

GraphQL-query&#39;s en hun JSON-antwoorden kunnen in de cache worden geplaatst als ze worden aangewezen als `GET` -aanvragen bij het gebruik van een CDN. Aanvragen zonder cache kunnen daarentegen zeer (bron)duur zijn en traag verlopen, met mogelijk verdere nadelige gevolgen voor de middelen van de oorsprong.

**Verdere Verwijzing**

Zie:

* [ Gebruikend CDN in AEM ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL#using-dispatcher-with-a-cdn)

#### HTTP-cachebeheerkoppen instellen {#set-http-cache-control-headers}

**Aanbeveling**

Wanneer het gebruiken van voortgeduurde vragen van GraphQL met een CDN, wordt het geadviseerd om aangewezen HTTP- geheim voorgeheugencontrolekopballen te plaatsen.

Elke voortgezette vraag kan zijn eigen specifieke reeks kopballen van de geheim voorgeheugencontrole hebben. De kopballen kunnen over [ GraphQL API ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) worden geplaatst.

Zij kunnen ook worden geplaatst gebruikend het **cURL** hulpmiddel van de bevellijn. Bijvoorbeeld, gebruikend een `PUT` verzoek om een verpakte vraag met geheim voorgeheugencontrole tot stand te brengen.

```shell
$ curl -X PUT \
    -H 'authorization: Basic YWRtaW46YWRtaW4=' \
    -H "Content-Type: application/json" \
    "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
    -d \
'{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
```

<!-- or the [AEM GraphiQL IDE](/help/sites-developing/headless/graphql-api/graphiql-ide.md#managing-cache). 
-->

**Verdere Verwijzing**

Zie:

* [Door uw doorlopende query&#39;s in cache te plaatsen](/help/sites-developing/headless/graphql-api/persisted-queries.md#caching-persisted-queries)
* [Een GraphQL-query laten doorgaan](/help/sites-developing/headless/graphql-api/persisted-queries.md#how-to-persist-query)
<!--
* [Managing cache for your persisted queries](/help/sites-developing/headless/graphql-api/graphiql-ide.md#managing-cache)
-->

<!--
#### Use AEM GraphQL pre-caching {#use-aem-graphql-pre-caching}

**Recommendation**

This capability allows AEM to further cache content within the scope of GraphQL queries that can then be assembled as blocks in JSON output rather than line by line. 

**Further Reference**

Contact Adobe to enable this capability for your AEM Cloud Service program and environments. 
-->

### GraphQL Query-optimalisatie {#graphql-query-optimization}

Op een AEM instantie met een hoog aantal Inhoudsfragmenten die hetzelfde model delen, kunnen vragen in de GraphQL-lijst kostbaar worden (in termen van bronnen).

Dit is omdat *alle* fragmenten die een model delen dat binnen de vraag van GraphQL wordt gebruikt in geheugen moet worden geladen. Dit verbruikt zowel tijd als geheugen. Het filtreren, dat het aantal punten in de (definitieve) resultaatreeks kan verminderen, kan slechts worden toegepast **nadat** ladend het volledige die resultaat in geheugen wordt geplaatst.

Dit kan de indruk wekken dat zelfs kleine resultaatsets (kunnen) tot slechte prestaties leiden. In werkelijkheid wordt de vertraging echter veroorzaakt door de grootte van de oorspronkelijke resultaatset, aangezien deze intern moet worden afgehandeld voordat filters kunnen worden toegepast.

Om de prestaties en het geheugen te verminderen, moet deze aanvankelijke resultaatreeks zo klein mogelijk worden gehouden.

AEM biedt twee manieren om GraphQL-query&#39;s te optimaliseren:

* [Hybride filtering](#use-aem-graphql-hybrid-filtering)
* [ het pagineren ](#use-aem-graphql-pagination) (of paginering)

   * [ het Sorteren ](#use-graphql-sorting) is niet direct verwant met optimalisering, maar is verwant aan het pagineren

Elke benadering heeft zijn eigen gebruiksgevallen en beperkingen. Deze sectie verstrekt informatie over het Hybride Filtreren en het Paging, samen met enkele [ beste praktijken ](#best-practices) voor gebruik in het optimaliseren van de vragen van GraphQL.

#### Hybride filters AEM GraphQL gebruiken {#use-aem-graphql-hybrid-filtering}

**Aanbeveling**

Bij hybride filters wordt JCR-filtering gecombineerd met AEM filtering.

Het past een filter JCR (in de vorm van een vraagbeperking) toe alvorens het resultaat te laden dat in geheugen voor AEM het filtreren wordt geplaatst. Hierdoor wordt de in het geheugen geladen resultatenset verminderd, aangezien het JCR-filter overbodige resultaten verwijdert.

>[!NOTE]
>
>Om technische redenen (bijvoorbeeld flexibiliteit, nesten van fragmenten), kan AEM niet het volledige filtreren aan JCR delegeren.

Met deze techniek blijft de flexibiliteit behouden die GraphQL-filters bieden, terwijl tegelijkertijd zoveel mogelijk filters worden gedelegeerd aan JCR.

>[!NOTE]
>
>AEM voor hybride filters moeten bestaande inhoudsfragmenten worden bijgewerkt

**Verdere Verwijzing**

Zie:

* [Inhoudsfragmenten bijwerken voor pagineren en sorteren in GraphQL-filters](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md)
* [Voorbeeldquery met filtering op _tags-id en exclusief variaties](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-filtering-tag-not-variations)

#### GraphQL-paginering gebruiken {#use-aem-graphql-pagination}

**Aanbeveling**

De reactietijd van complexe vragen, met grote resultaatreeksen, kan worden verbeterd door reacties in brokken te segmenteren gebruikend paginering, een norm van GraphQL.

GraphQL in AEM ondersteunt twee typen paginering:

* [ grens/op verschuiving-gebaseerde paginering ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#list-offset-limit)
Dit wordt gebruikt voor lijstquery&#39;s; deze eindigen met `List`, bijvoorbeeld `articleList` .
Als u dit wilt gebruiken, moet u de positie opgeven van het eerste item dat moet worden geretourneerd (de `offset` ) en het aantal items dat moet worden geretourneerd (de `limit` - of paginaformaat).

* [ curseur-gebaseerde paginering ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#paginated-first-after) (vertegenwoordigd door `first` en `after`)
Dit verstrekt een unieke identiteitskaart voor elk punt; ook gekend als curseur.
In de vraag, specificeert u de curseur van het laatste punt van de vorige pagina, plus de paginagrootte (het maximumaantal punten dat moet worden teruggekeerd).

  Aangezien de op curseur-gebaseerde paginering niet binnen de gegevensstructuren van op lijst-gebaseerde vragen past, AEM heeft `Paginated` vraagtype geïntroduceerd; bijvoorbeeld, `articlePaginated`. De gegevensstructuren en de parameters die worden gebruikt volgen [ GraphQL Cursor ConnectionSpecification ](https://relay.dev/graphql/connections.htm).

  >[!NOTE]
  >
  >AEM ondersteunt momenteel paginering via de volgende pagina (met behulp van `after` / `first` -parameters).
  >
  >Achterwaartse paginering (met behulp van `before`/`last` -parameters) wordt niet ondersteund.

**Verdere Verwijzing**

Zie:

* [Voorbeeld van pagineringsquery met eerste en volgende](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-pagination-first-after)

#### GraphQL-sortering gebruiken {#use-graphql-sorting}

**Aanbeveling**

Bij het sorteren is ook een GraphQL-standaard waarmee clients JSON-inhoud in gesorteerde volgorde kunnen ontvangen. Dit kan de behoefte aan verdere verwerking op de cliënt verminderen.

Sorteren kan alleen efficiënt zijn als alle sorteercriteria betrekking hebben op fragmenten op het hoogste niveau.

Als de sorteervolgorde een of meer velden bevat die zich op een genest fragment bevinden, moeten alle fragmenten die het model op hoofdniveau delen, in het geheugen worden geladen. Dit heeft een negatieve invloed op de prestaties.

>[!NOTE]
>
>Sorteren op velden op het hoogste niveau heeft ook een (zij het kleine) invloed op de prestaties.

**Verdere Verwijzing**

Zie:

* [Voorbeeldquery met filtering op _tags-id en exclusief variaties, en sorteren op naam](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-filtering-tag-not-variations)

## Aanbevolen procedures {#best-practices}

Het belangrijkste doel van alle optimaliseringsaanbevelingen is het verminderen van de aanvankelijke resultaatreeks. De hier vermelde beste praktijken verstrekken manieren om dit te doen. Zij kunnen (en moeten) worden gecombineerd.

### Alleen op eigenschappen op hoofdniveau filteren {#filter-top-level-properties-only}

Filteren op JCR-niveau werkt momenteel alleen voor fragmenten op hoofdniveau.

Als een filter de velden van een genest fragment aanpakt, moet AEM terugvallen naar het laden (in geheugen) van alle fragmenten die het onderliggende model delen.

U kunt dergelijke vragen van GraphQL nog optimaliseren door filteruitdrukkingen op gebieden van top-level fragmenten en die op gebieden van genestelde fragmenten met [ EN exploitant ](#logical-operations-in-filter-expressions) te combineren.

### De inhoudsstructuur gebruiken {#use-content-structure}

In AEM wordt het over het algemeen als een goede praktijk beschouwd om de gegevensopslagstructuur te gebruiken om het bereik van de te verwerken inhoud te beperken.

Deze aanpak moet ook worden toegepast op GraphQL-query&#39;s.

Dit kan door een filter op het `_path` gebied van het top-level fragment toe te passen:

```graphql
{
  someList(filter: {
    _path: {
      _expressions: [ 
        {
          value: "/content/dam/some/sub/path/",
          _operator: STARTS_WITH
        }
      ]
    }
  }) {
    items {
      # ...
    }
  }
}
```

>[!NOTE]
>
>U moet `/` on `value` volgen voor de beste prestaties.

### Paginering gebruiken {#use-paging}

U kunt ook paginering gebruiken om de oorspronkelijke resultaatset te reduceren, vooral als uw aanvragen geen filters en sortering gebruiken.

Als u filtert of sorteert op geneste fragmenten, kunnen gepagineerde query&#39;s nog steeds traag zijn, omdat AEM mogelijk grotere hoeveelheden fragmenten in het geheugen moet laden. Daarom als u het filtreren en het pagineren combineert, overweeg de regels voor het filtreren (zoals hierboven vermeld).

Voor pagineren is sorteren even belangrijk, omdat gepagineerde resultaten altijd worden gesorteerd - expliciet of impliciet.

Als u vooral alleen geïnteresseerd bent in het ophalen van de eerste paar pagina&#39;s, is er geen significant verschil tussen het gebruik van de query&#39;s `...List` of `...Paginated` . Als uw toepassing echter meer dan één of twee pagina&#39;s wil lezen, moet u rekening houden met de query `...Paginated` omdat deze vooral beter werkt met de latere pagina&#39;s.

### Logische bewerkingen in filterexpressies {#logical-operations-in-filter-expressions}

Als u filtert op geneste fragmenten, kunt u nog steeds JCR-filters toepassen door een bijbehorend filter op te geven voor een veld op hoofdniveau dat wordt gecombineerd met de operator `AND` .

Een typisch gebruik-geval zou het werkingsgebied van de vraag moeten beperken gebruikend een filter op het `_path` gebied van het top-level fragment, en dan filter op extra gebieden die op top-level, of op een genesteld fragment zouden kunnen zijn.

In dit geval worden de verschillende filterexpressies gecombineerd met `AND` . Daarom kan het filter op `_path` de aanvankelijke resultaatreeks effectief beperken. Alle andere filters in velden op het hoogste niveau kunnen helpen om de oorspronkelijke resultaatset ook te reduceren, mits ze worden gecombineerd met `AND` .

Filterexpressies in combinatie met `OR` kunnen niet worden geoptimaliseerd als er geneste fragmenten bij betrokken zijn. `OR` de uitdrukkingen kunnen slechts worden geoptimaliseerd als *geen* genestelde fragmenten betrokken zijn.

### Filteren op tekstvelden met meerdere regels wordt vermeden {#avoid-filtering-multiline-textfields}

De velden van een tekstveld met meerdere regels (html, markdown, plaintext, json) kunnen niet worden gefilterd via een JCR-query, omdat de inhoud van deze velden direct moet worden berekend.

Als u nog steeds op een tekstveld met meerdere regels moet filteren, kunt u de grootte van de oorspronkelijke resultaatset beperken door extra filterexpressies toe te voegen en deze te combineren met `AND` . Ook het beperken van het bereik door filtering op het veld `_path` is een goede aanpak.

### Filteren op virtuele velden vermijden {#avoid-filtering-virtual-fields}

Virtuele velden (de meeste velden die beginnen met `_` ) worden berekend terwijl een GraphQL-query wordt uitgevoerd en vallen daarom buiten het bereik van op JCR gebaseerde filtering.

Één belangrijke uitzondering is het `_path` gebied, dat effectief kan worden gebruikt om de grootte van de aanvankelijke resultaatreeks te verminderen - als de inhoud dienovereenkomstig gestructureerd is (zie [ Gebruik de inhoudsstructuur ](#use-content-structure)).

### Filteren: uitsluitingen {#filtering-exclusions}

Er zijn verschillende andere situaties waarin een filterexpressie niet op het JCR-niveau kan worden geëvalueerd (en daarom moet worden vermeden dat de beste prestaties worden bereikt):

* Filterexpressies op een `Float` -waarde die de `_sensitiveness` filteroptie gebruiken en waarbij `_sensitiveness` op een andere waarde dan `0.0` is ingesteld.

* Filterexpressies op een `String` -waarde met de filteroptie `_ignoreCase` .

* Filteren op `null` -waarden.

* Filters op arrays met `_apply: ALL_OR_EMPTY` .

* Filters op arrays met `_apply: INSTANCES` , `_instances: 0` .

* Filterexpressies met de operator `CONTAINS_NOT` .

* Filterexpressies op een `Calendar` -, `Date` - of `Time` -waarde die de `NOT_AT` -operator gebruiken.

### Nesten van inhoudsfragmenten minimaliseren {#minimize-content-fragment-nesting}

Het nesten van Inhoudsfragmenten is een uitstekende manier om aangepaste inhoudsstructuren te modelleren. U kunt zelfs een fragment hebben met een genest fragment dat een genest fragment bevat, dat... heeft enzovoort.

Als u echter een structuur met te veel niveaus maakt, kunnen de verwerkingstijden voor een GraphQL-query toenemen, aangezien GraphQL de volledige hiërarchie van alle geneste Content Fragments moet doorlopen.

Diepe nesting kan ook negatieve gevolgen hebben voor het beheer van inhoud. Over het algemeen wordt aanbevolen het nesten van inhoudsfragmenten te beperken tot minder dan vijf of zes niveaus.

### Niet alle indelingen uitvoeren (tekstelementen met meerdere regels) {#do-not-output-all-formats}

AEM GraphQL kan tekst terugkeren, authored in het **[Meerdere lijntekst](/help/assets/content-fragments/content-fragments-models.md#data-types)** gegevenstype, in veelvoudige formaten: Rijke Tekst, Eenvoudige Tekst, en Markdown.

Wanneer u alle drie de indelingen uitvoert, wordt de tekstuitvoer in JSON met een factor drie vergroot. Dat, in combinatie met over het algemeen grote resultaatreeksen van zeer brede vragen, zeer grote JSON reacties kan veroorzaken die daarom lang duurt om te berekenen. Het is beter om de uitvoer te beperken tot alleen de tekstindelingen die nodig zijn voor het renderen van de inhoud.

### Inhoudsfragmenten wijzigen {#modifying-content-fragments}

Wijzig slechts de Fragments van de Inhoud, en hun middelen, gebruikend AEM UI of APIs. Breng geen wijzigingen rechtstreeks aan in de tekenherkenning.

### Uw query&#39;s testen {#test-your-queries}

Het verwerken van GraphQL-query&#39;s is vergelijkbaar met het verwerken van zoekquery&#39;s en is aanzienlijk complexer dan eenvoudige API-aanvragen voor alle GET-inhoud.

Het zorgvuldig plannen, testen, en optimaliseren van uw vragen in een gecontroleerde niet productieomgeving is essentieel voor later succes wanneer gebruikt in productie.
