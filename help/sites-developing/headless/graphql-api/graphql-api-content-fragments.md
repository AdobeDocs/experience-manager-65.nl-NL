---
title: GraphQL API AEM voor gebruik met inhoudsfragmenten
description: Leer hoe u inhoudsfragmenten in Adobe Experience Manager (AEM) kunt gebruiken met de AEM GraphQL API voor het leveren van inhoud zonder kop.
feature: Content Fragments,GraphQL API
exl-id: beae1f1f-0a76-4186-9e58-9cab8de4236d
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 47aac4b19bfbd29395fb09f3c27c981e7aa908f6
workflow-type: tm+mt
source-wordcount: '4984'
ht-degree: 0%

---

# GraphQL API AEM voor gebruik met inhoudsfragmenten {#graphql-api-for-use-with-content-fragments}

Leer hoe u inhoudsfragmenten in Adobe Experience Manager (AEM) kunt gebruiken met de AEM GraphQL API voor het leveren van inhoud zonder kop.

AEM GraphQL API die wordt gebruikt met Content Fragments is sterk gebaseerd op de standaard, open-source GraphQL API.

Door de GraphQL API in AEM te gebruiken, kunt u inhoudsfragmenten efficiënt aan JavaScript-clients leveren in CMS-implementaties zonder kop:

* Herhalende API-aanvragen voorkomen, zoals REST,
* ervoor zorgen dat de levering beperkt blijft tot de specifieke eisen;
* Het toestaan voor bulklevering van precies wat voor het teruggeven als antwoord op één enkele API vraag nodig is.

>[!NOTE]
>
>GraphQL wordt gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM):
>
>* [ AEM Commerce verbruikt gegevens van een platform van Commerce via GraphQL ](/help/commerce/cif/integrating/magento.md).
>* AEM Content Fragments werken samen met de AEM GraphQL API (een aangepaste implementatie op basis van standaard GraphQL) voor gestructureerde inhoud voor gebruik in uw toepassingen.

## Vereisten {#prerequisites}

Klanten die GraphQL gebruiken, moeten het AEM Content Fragment installeren met GraphQL Index Package 1.0.5. Zie de [ Nota&#39;s van de Versie ](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package) voor verdere details.

## De GraphQL API {#graphql-api}

GraphQL is:

* &quot;*...een vraagtaal voor APIs en runtime voor het vervullen van die vragen met uw bestaande gegevens. GraphQL geeft een volledige en begrijpelijke beschrijving van de gegevens in uw API. Het geeft cliënten de macht om precies te vragen wat zij en niets meer nodig hebben, maakt het gemakkelijker om APIs in tijd te evolueren, en laat krachtige ontwikkelaarshulpmiddelen toe.*&quot;.

  Zie [ GraphQL.org ](https://graphql.org)

* &quot;*...een open specificatie voor een flexibele API laag. Plaats GraphQL over uw bestaande achtergronden zodat u producten sneller kunt bouwen dan ooit...*&quot;.

  Zie [ GraphQL ](https://graphql.com/) ontdekken.

* *&quot;...een taal en specificatie voor gegevensquery die in 2012 intern door Facebook zijn ontwikkeld, voordat deze in 2015 openbaar wordt uitbesteed. Het biedt een alternatief voor op REST gebaseerde architecturen met als doel de productiviteit van ontwikkelaars te verhogen en de hoeveelheden overgedragen gegevens te minimaliseren. GraphQL wordt gebruikt in productie door honderden organisaties van alle grootte...&quot;*

  Zie [ Stichting van GraphQL ](https://graphql.org/foundation).

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all the tools they need to understand and adopt GraphQL.*". 
-->

Raadpleeg de volgende secties (onder andere over veel andere bronnen) voor meer informatie over de GraphQL API:

* Bij [ graphql.org ](https://graphql.org):

   * [ Inleiding aan GraphQL ](https://graphql.org/learn)

   * [ de Specificatie van GraphQL ](https://spec.graphql.org/)

* Bij [ graphql.com ](https://graphql.com):

   * [ Tutorials ](https://graphql.com/tutorials/)


De GraphQL for AEM-implementatie is gebaseerd op de standaard GraphQL Java™-bibliotheek. Zie:

* [ graphQL.org - Java ](https://graphql.org/code/#java)

* [ GraphQL Java™ bij GitHub ](https://github.com/graphql-java)

### GraphQL Terminologie {#graphql-terminology}

GraphQL gebruikt het volgende:

* **[Vragen ](https://graphql.org/learn/queries/)**

* **[Schema&#39;s en Types ](https://graphql.org/learn/schema/)**:

   * Schema&#39;s worden gegenereerd door AEM op basis van de modellen van inhoudsfragmenten.
   * Met behulp van uw schema&#39;s geeft GraphQL de typen en bewerkingen weer die zijn toegestaan voor de GraphQL voor AEM implementatie.

* **[Gebieden ](https://graphql.org/learn/queries/#fields)**

* **[Eindpunt van GraphQL](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#graphql-aem-endpoint)**
   * Het pad in AEM dat reageert op GraphQL-query&#39;s en toegang biedt tot de GraphQL-schema&#39;s.

   * Zie [ toelatend uw Eindpunt van GraphQL ](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint) voor verdere details.

Zie [ (GraphQL.org) Inleiding aan GraphQL ](https://graphql.org/learn/) voor uitvoerige details, met inbegrip van [ Beste praktijken ](https://graphql.org/learn/best-practices/).

### GraphQL-querytypen {#graphql-query-types}

Met GraphQL kunt u query&#39;s uitvoeren die worden geretourneerd:

* A **enige ingang**

* A **[lijst van ingangen ](https://graphql.org/learn/schema/#lists-and-non-null)**

AEM verstrekt mogelijkheden om vragen (beide types) in [ Verlengde Vragen ](/help/sites-developing/headless/graphql-api/persisted-queries.md) om te zetten die door Dispatcher en CDN in het voorgeheugen worden opgeslagen.

### Aanbevolen werkwijzen voor GraphQL-query (Dispatcher en CDN) {#graphql-query-best-practices}

[ Geadviseerde vragen ](/help/sites-developing/headless/graphql-api/persisted-queries.md) zijn de geadviseerde methode om bij te gebruiken publiceert instanties als:

* ze zijn in cache geplaatst
* zij worden centraal beheerd door AEM

<!-- is this fully accurate? -->
>[!NOTE]
>
>Gewoonlijk is er geen verzender/CDN op auteur, zodat is er geen prestatieswinst in het gebruiken van persisted vragen daar; behalve het testen van hen.

GraphQL-query&#39;s die gebruikmaken van POST-aanvragen worden niet aanbevolen omdat ze niet in de cache zijn opgeslagen, zodat Dispatcher standaard is geconfigureerd om dergelijke query&#39;s te blokkeren.

Hoewel GraphQL ook GET-aanvragen ondersteunt, kunnen deze aanvragen limieten bereiken (bijvoorbeeld de lengte van de URL) die kunnen worden vermeden door middel van doorlopende query&#39;s.

Zie [ toelaten caching van persisted query ](#enable-caching-persisted-queries) voor verdere details.

>[!NOTE]
>
>De capaciteit om directe vragen uit te voeren kan op een bepaald punt in de toekomst worden verouderd.

## GraphiQL Interface {#graphiql-interface}

Een implementatie van de standaard [ GraphiQL ](https://graphql.org/learn/serving-over-http/#graphiql) interface is beschikbaar voor gebruik met AEM GraphQL.

>[!NOTE]
>
>GraphiQL is inbegrepen in alle milieu&#39;s van AEM (maar is slechts toegankelijk/zichtbaar wanneer u uw eindpunten vormt).
>
>In vorige versies had u een pakket nodig om GraphiQL IDE te installeren. Als u dit pakket hebt geïnstalleerd, kan het nu worden verwijderd.

Met deze interface kunt u query&#39;s rechtstreeks invoeren en testen.

Bijvoorbeeld:

* `http://localhost:4502/content/graphiql.html`

De klasse biedt functies zoals syntaxismarkering, automatisch aanvullen en automatisch voorstellen, samen met een geschiedenis en online documentatie:

![ GraphiQL Interface ](assets/cfm-graphiql-interface.png " GraphiQL Interface ")

>[!NOTE]
>
>Zie [ Gebruikend GrahiQL winde ](/help/sites-developing/headless/graphql-api/graphiql-ide.md).

## Kwesties gebruiken voor auteur- en Publish-omgevingen {#use-cases-author-publish-environments}

De gebruiksgevallen kunnen afhankelijk zijn van het type AEM omgeving:

* Publish-omgeving; wordt gebruikt voor:
   * Query-gegevens voor JS-toepassing (standaardgebruikscenario)

* Auteursomgeving; gebruikt voor:
   * Query-gegevens voor &quot;inhoudsbeheerdoeleinden&quot;:
      * GraphQL in AEM is een alleen-lezen API.
      * De REST-API kan worden gebruikt voor CR(u)D-bewerkingen.

## Machtigingen {#permission}

De machtigingen zijn vereist voor toegang tot Assets.

GraphQL query&#39;s worden uitgevoerd met toestemming van de AEM gebruiker van het onderliggende verzoek. Als de gebruiker geen leestoegang heeft tot bepaalde fragmenten (opgeslagen als Assets), worden deze geen deel van de resultaatset.

Ook, moet de gebruiker toegang tot een eindpunt van GraphQL hebben om de vragen van GraphQL in werking te kunnen stellen.

## Schema genereren {#schema-generation}

GraphQL is een getypeerde API, wat betekent dat de gegevens duidelijk gestructureerd en ingedeeld moeten zijn op basis van het type.

De GraphQL-specificatie biedt een aantal richtlijnen voor het maken van een robuuste API voor het ondervragen van gegevens over een bepaalde instantie. Om deze richtlijnen te voltooien, moet een cliënt het [ Schema ](#schema-generation) halen, dat alle types noodzakelijk voor een vraag bevat.

Voor Inhoudsfragmenten, zijn de schema&#39;s van GraphQL (structuur en types) gebaseerd op **Toegelaten** [ Modellen van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-models.md) en hun gegevenstypes.

>[!CAUTION]
>
>Alle schema&#39;s van GraphQL (die uit de Modellen van het Fragment van de Inhoud worden afgeleid die **&#x200B;**) zijn toegelaten zijn leesbaar door het eindpunt van GraphQL.
>
>Dit betekent dat u ervoor moet zorgen dat er geen gevoelige gegevens beschikbaar zijn, omdat deze op deze manier kunnen worden gelekt. Het bevat bijvoorbeeld informatie die als veldnamen aanwezig kan zijn in de modeldefinitie.

Als een gebruiker bijvoorbeeld een Content Fragment Model met de naam `Article` heeft gemaakt, genereert AEM een GraphQL-type `ArticleModel` . De velden in dit type komen overeen met de velden en gegevenstypen die in het model zijn gedefinieerd. Bovendien worden er enkele ingangspunten gemaakt voor de query&#39;s die op dit type werken, zoals `articleByPath` of `articleList` .

1. A Content Fragment Model:

   ![ Model van het Fragment van de Inhoud voor gebruik met GraphQL ](assets/cfm-graphqlapi-01.png " Model van het Fragment van de Inhoud voor gebruik met GraphQL ")

1. Het corresponderende GraphQL-schema (uitvoer van de automatische documentatie GraphiQL):
   ![ het Schema van GraphQL dat op het Model van het Fragment van de Inhoud ](assets/cfm-graphqlapi-02.png " wordt gebaseerd GraphQL Schema op het Model van het Fragment van de Inhoud ") wordt gebaseerd

   Dit beeld toont aan dat het geproduceerde type `ArticleModel` verscheidene [ gebieden ](#fields) bevat.

   * Drie ervan zijn door de gebruiker beheerd: `author`, `main` en `referencearticle` .

   * De andere velden zijn automatisch AEM toegevoegd en zijn nuttige methoden voor het verschaffen van informatie over een bepaald inhoudsfragment. In dit voorbeeld:
(de [ helpergebieden ](#helper-fields)) `_path`, `_metadata`, `_variations`.

1. Nadat een gebruiker een inhoudsfragment heeft gemaakt op basis van het artikelmodel, kan het vervolgens worden ondervraagd via GraphQL. Voor voorbeelden, zie de [ Vragen van de Steekproef ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#graphql-sample-queries) (die op de structuur van het Fragment van de a [ steekproefInhoud voor gebruik met GraphQL ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#content-fragment-structure-graphql) worden gebaseerd).

In GraphQL for AEM is het schema flexibel. Deze flexibiliteit betekent dat deze automatisch wordt gegenereerd wanneer een inhoudsfragmentmodel wordt gemaakt, bijgewerkt of verwijderd. De caches voor het gegevensschema worden ook vernieuwd wanneer u een model van het inhoudsfragment bijwerkt.

De service Sites GraphQL luistert (op de achtergrond) naar eventuele wijzigingen die zijn aangebracht in een inhoudsfragmentmodel. Wanneer updates worden ontdekt, slechts wordt dat deel van het schema opnieuw geproduceerd. Deze optimalisatie bespaart tijd en zorgt voor stabiliteit.

Als u bijvoorbeeld:

1. Installeer een pakket met `Content-Fragment-Model-1` en `Content-Fragment-Model-2` :

   1. Er worden GraphQL-typen voor `Model-1` en `Model-2` gegenereerd.

1. Wijzig vervolgens `Content-Fragment-Model-2` :

   1. Alleen het GraphQL-type `Model-2` wordt bijgewerkt.

   1. Hoewel `Model-1` hetzelfde blijft.

>[!NOTE]
>
>Dit detail is belangrijk om nota te nemen enkel voor het geval u bulkupdates op de Modellen van het Fragment van de Inhoud door REST api, of anders wilt doen.

Het schema wordt gediend door het zelfde eindpunt zoals de vragen van GraphQL, met de cliënt die het feit behandelt dat het schema met de uitbreiding `GQLschema` wordt geroepen. Als u bijvoorbeeld een eenvoudige `GET` aanvraag uitvoert op `/content/cq:graphql/global/endpoint.GQLschema` , levert dit de uitvoer op van het schema met het inhoudstype: `text/x-graphql-schema;charset=iso-8859-1` .

### Schema genereren - Niet-gepubliceerde modellen {#schema-generation-unpublished-models}

Wanneer Inhoudsfragmenten zijn genest, kan een bovenliggend inhoudsfragmentmodel worden gepubliceerd, maar een model waarnaar wordt verwezen, niet.

>[!NOTE]
>
>De AEM gebruikersinterface verhindert dit te gebeuren, maar als het publiceren programmatically, of met inhoudspakketten wordt gemaakt, kan het voorkomen.

Wanneer zulk gebeurt, AEM produceert een *onvolledig* Schema voor het Model van het Fragment van de ouderInhoud. Dit betekent dat de fragmentverwijzing, die afhankelijk is van het niet-gepubliceerde model, uit het schema wordt verwijderd.

## Velden {#fields}

Binnen het schema zijn er afzonderlijke velden, van twee basiscategorieën:

* Velden die u genereert.

  Een selectie van [ Types van Gegevens ](#data-types) wordt gebruikt om gebieden tot stand te brengen die op worden gebaseerd hoe u uw Model van het Fragment van de Inhoud vormt. De gebiedsnamen worden genomen van het **gebied van de Naam van het Bezit** van het **Type van Gegevens**.

   * Er is ook **teruggeeft als** het plaatsen om te overwegen, aangezien de gebruikers bepaalde gegevenstypes kunnen vormen. Een tekstveld met één regel kan bijvoorbeeld worden geconfigureerd voor meerdere tekst met één regel door `multifield` te kiezen in het vervolgkeuzemenu.

* GraphQL voor AEM produceert ook verscheidene [ helpergebieden ](#helper-fields).

  Deze velden worden gebruikt om een inhoudsfragment te identificeren of om meer informatie over een inhoudsfragment op te halen.

### Gegevenstypen {#data-types}

GraphQL for AEM ondersteunt een lijst met typen. Alle ondersteunde gegevenstypen van het inhoudsfragmentmodel en de bijbehorende GraphQL-typen worden weergegeven:

| Inhoudsfragmentmodel - Gegevenstype | GraphQL-type | Beschrijving |
|--- |--- |--- |
| Tekst met één regel | `String`, `[String]` |  Wordt gebruikt voor eenvoudige tekenreeksen, zoals namen van auteurs en locaties. |
| Meerdere regels tekst | `String` |  Wordt gebruikt voor het uitvoeren van tekst, zoals de hoofdtekst van een artikel |
| Getal |  `Float`, `[Float]` | Wordt gebruikt om het zwevende-kommanummer en de reguliere getallen weer te geven |
| Boolean |  `Boolean` |  Gebruikt om selectievakjes weer te geven → eenvoudige true/false-instructies |
| Datum en tijd | `Calendar` |  Wordt gebruikt om datum en tijd weer te geven in de ISO 8086-indeling. Afhankelijk van het geselecteerde type zijn er drie kleuren beschikbaar voor gebruik in AEM GraphQL: `onlyDate`, `onlyTime`, `dateTime` |
| Opsomming |  `String` |  Wordt gebruikt om een optie weer te geven uit een lijst met opties die bij het maken van het model zijn gedefinieerd |
|  Tags |  `[String]` |  Wordt gebruikt om een lijst weer te geven met tekenreeksen die tags vertegenwoordigen die in AEM worden gebruikt |
| Content Reference |  `String` |  Wordt gebruikt om het pad naar een ander element in AEM weer te geven |
| Fragmentverwijzing |  *ModelType van A* <br><br> Enig gebied: `Model` - Model type, direct van verwijzingen voorzien <br><br> Multifield, met één referenced type: `[Model]` - Serie van type `Model`, die direct van serie <br><br> Multifield, met veelvoudige referenced types wordt voorzien: `[AllFragmentModels]` - Serie van alle modeltypes, van serie met verenigingstype van verwijzingen voorzien type |  Gebruikt om één, of meer, de Fragmenten van de Inhoud van bepaalde ModelTypes van Verwijzing te voorzien, die toen het model werd gecreeerd |

{style="table-layout:auto"}

### Helpervelden {#helper-fields}

Naast de gegevenstypes voor gebruiker-geproduceerde gebieden, produceert GraphQL voor AEM ook verscheidene *helper* gebieden helpen een Fragment van de Inhoud identificeren, of om extra informatie over een Fragment van de Inhoud te verstrekken.

Deze [ helpergebieden ](#helper-fields) zijn duidelijk met een voorafgaande `_` om tussen te onderscheiden wat door de gebruiker is bepaald en wat auto-geproduceerd is.

#### Pad {#path}

Het padveld wordt gebruikt als een identifier in AEM GraphQL. Het vertegenwoordigt het pad van het Content Fragment-element in de AEM opslagplaats. Dit pad wordt gekozen als de id van een inhoudsfragment, omdat het:

* uniek is binnen AEM,
* kan gemakkelijk worden opgehaald.

Met de volgende code worden de paden weergegeven van alle inhoudsfragmenten die zijn gemaakt op basis van het inhoudsfragmentmodel `Person` .

```graphql
{
  personList {
    items {
      _path
    }
  }
}
```

Als u één inhoudsfragment van een bepaald type wilt ophalen, moet u ook eerst het pad ervan bepalen. Bijvoorbeeld:

```graphql
{
  authorByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      firstName
      name
    }
  }
}
```

Zie [ Vraag van de Steekproef - Één enkel Specifiek Fragment van de Stad ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-single-specific-city-fragment).

#### Metagegevens {#metadata}

Via GraphQL worden AEM ook de metagegevens van een inhoudsfragment beschikbaar gemaakt. Metagegevens zijn de informatie die een inhoudsfragment beschrijft, zoals het volgende:

* de titel van een inhoudsfragment
* het pad naar de miniatuur
* de beschrijving van een inhoudsfragment
* en de datum waarop het is gemaakt, onder andere.

Omdat metagegevens worden gegenereerd via de Schema-editor en als zodanig geen specifieke structuur hebben, is het GraphQL-type van `TypedMetaData` geïmplementeerd om de metagegevens van een inhoudsfragment beschikbaar te maken. De `TypedMetaData` stelt de informatie bloot die door de volgende scalaire types wordt gegroepeerd:

| Veld |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!`  |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

Elk scalair type vertegenwoordigt of één enkel naam-waarde paar of een serie van naam-waarde paren, waar de waarde van dat paar van het type is het werd gegroepeerd.

Als u bijvoorbeeld de titel van een inhoudsfragment wilt ophalen, is deze eigenschap een eigenschap String, zodat u een query voor alle metagegevens van tekenreeks kunt uitvoeren:

Ga als volgt te werk om te zoeken naar metagegevens:

```graphql
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      _metadata {
        stringMetadata {
          name
          value
        }
      }
    }
  }
}
```

U kunt alle GraphQL-typen voor metagegevens weergeven als u het schema Gegenereerde GraphQL weergeeft. Alle modeltypen hebben dezelfde `TypedMetaData` .

>[!NOTE]
>
>**Verschil tussen normale en seriemeta-gegevens**
>Houd er rekening mee dat `StringMetadata` en `StringArrayMetadata` beide verwijzen naar wat in de opslagplaats is opgeslagen, en niet naar de manier waarop u ze ophaalt.
>
>Als u bijvoorbeeld het veld `stringMetadata` aanroept, ontvangt u een array van alle metagegevens die in de gegevensopslagruimte zijn opgeslagen als een `String` . Als u `stringArrayMetadata` aanroept, ontvangt u een array met alle metagegevens die in de opslagplaats zijn opgeslagen als `String[]` .

Zie [ Vraag van de Steekproef voor Meta-gegevens - maak een lijst van de Meta-gegevens voor Uitreiking genoemd GB ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-metadata-awards-gb).

#### Variaties {#variations}

Het veld `_variations` is geïmplementeerd om het opvragen van variaties in een inhoudsfragment te vereenvoudigen. Bijvoorbeeld:

```graphql
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _variations
    }
  }
}
```

>[!NOTE]
>
>Het `_variations` gebied bevat geen a `master` variatie, aangezien technisch de originele gegevens (die als *Hoofd* in UI worden van verwijzingen voorzien) niet als expliciete variatie wordt beschouwd.

Zie [ Vraag van de Steekproef - Alle Plaatsen met een Benoemde Variatie ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-cities-named-variation).

>[!NOTE]
>
>Als de opgegeven variatie niet bestaat voor een inhoudsfragment, worden de oorspronkelijke gegevens (ook wel de hoofdvariatie genoemd) geretourneerd als een standaardinstelling (fallback).

<!--
## Security Considerations {#security-considerations}
-->

## GraphQL-variabelen {#graphql-variables}

GraphQL staat toe dat variabelen in de query worden geplaatst. Voor meer informatie, zie [ documentatie van GraphQL voor Variabelen ](https://graphql.org/learn/queries/#variables).

Als u bijvoorbeeld alle inhoudsfragmenten van het type `Article` wilt ophalen die een specifieke variatie hebben, kunt u de variabele `variation` in GraphiQL opgeven.

![ de Variabelen van GraphQL ](assets/cfm-graphqlapi-03.png " de Variabelen van GraphQL ")

```graphql
### query
query GetArticlesByVariation($variation: String!) {
    articleList(variation: $variation) {
        items {
            _path
            author
            _variations
        }
    }
}
 
### in query variables
{
    "variation": "uk"
}
```

## GraphQL-richtlijnen {#graphql-directives}

In GraphQL is er een mogelijkheid om de query te wijzigen op basis van variabelen, de zogenaamde GraphQL-richtlijnen.

Hier kunt u bijvoorbeeld het veld `adventurePrice` opnemen in een query voor alle `AdventureModels` , op basis van een variabele `includePrice` .

![ de Richtlijnen van GraphQL ](assets/cfm-graphqlapi-04.png " de Richtlijnen van GraphQL ")

```graphql
### query
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      adventureTitle
      adventurePrice @include(if: $includePrice)
    }
  }
}
 
### in query variables
{
    "includePrice": true
}
```

## Filteren {#filtering}

U kunt filteren ook gebruiken in uw GraphQL-query&#39;s om specifieke gegevens te retourneren.

Bij het filteren wordt een syntaxis gebruikt die is gebaseerd op logische operatoren en expressies.

Het meest atomische deel bestaat uit één expressie die kan worden toegepast op de inhoud van een bepaald veld. De inhoud van het veld wordt vergeleken met een bepaalde constante waarde.

De volgende expressie zou bijvoorbeeld de inhoud van het veld vergelijken met de waarde `some text` en geslaagd zijn als de inhoud gelijk is aan de waarde. Anders mislukt de expressie:

```graphql
{
  value: "some text"
  _op: EQUALS
}
```

De volgende operatoren kunnen worden gebruikt om velden met een bepaalde waarde te vergelijken:

| Operator | Typen | De expressie slaagt als ... |
|--- |--- |--- |
| `EQUALS` | `String`, `ID`, `Boolean` | ... de waarde is gelijk aan de inhoud van het veld |
| `EQUALS_NOT` | `String`, `ID` | ... de waarde is *niet* het zelfde als de inhoud van het gebied |
| `CONTAINS` | `String` | ... de inhoud van het veld bevat de waarde (`{ value: "mas", _op: CONTAINS }` komt overeen met `Christmas` , `Xmas` , `master` , ...) |
| `CONTAINS_NOT` | `String` | ... bevat de inhoud van het gebied *niet* de waarde |
| `STARTS_WITH` | `ID` | ... de id begint met een bepaalde waarde (`{ value: "/content/dam/", _op: STARTS_WITH` komt overeen met `/content/dam/path/to/fragment` , maar niet met `/namespace/content/dam/something` ) |
| `EQUAL` | `Int`, `Float` | ... de waarde is gelijk aan de inhoud van het veld |
| `UNEQUAL` | `Int`, `Float` | ... de waarde is *niet* het zelfde als de inhoud van het gebied |
| `GREATER` | `Int`, `Float` | ... de inhoud van het veld is groter dan de waarde |
| `GREATER_EQUAL` | `Int`, `Float` | ... de inhoud van het veld is groter dan of gelijk aan de waarde |
| `LOWER` | `Int`, `Float` | ... de inhoud van het veld is lager dan de waarde |
| `LOWER_EQUAL` | `Int`, `Float` | ... de inhoud van het veld is lager dan of gelijk aan de waarde |
| `AT` | `Calendar`, `Date`, `Time` | ... de inhoud van het veld is gelijk aan de waarde (inclusief tijdzone-instelling) |
| `NOT_AT` | `Calendar`, `Date`, `Time` | ... de inhoud van het gebied is *niet* het zelfde als de waarde |
| `BEFORE` | `Calendar`, `Date`, `Time` | ... het tijdpunt dat door de waarde wordt aangegeven, ligt vóór het tijdpunt dat door de inhoud van het veld wordt aangegeven |
| `AT_OR_BEFORE` | `Calendar`, `Date`, `Time` | ... het tijdpunt dat door de waarde wordt aangegeven, zich vóór of op hetzelfde tijdpunt bevindt dat door de inhoud van het veld wordt aangegeven |
| `AFTER` | `Calendar`, `Date`, `Time` | ... het punt in de tijd dat door de waarde wordt aangegeven, is na het punt in de tijd dat door de inhoud van het veld wordt aangegeven |
| `AT_OR_AFTER` | `Calendar`, `Date`, `Time` | ... het tijdpunt dat door de waarde wordt aangegeven, is na of op hetzelfde tijdpunt dat door de inhoud van het veld wordt aangegeven |

Bij sommige typen kunt u ook aanvullende opties opgeven die wijzigen hoe een expressie wordt geëvalueerd:

| Optie | Typen | Beschrijving |
|--- |--- |--- |
| `_ignoreCase` | `String` | Negeert het hoofdlettergebruik van een tekenreeks, bijvoorbeeld een waarde `time` overeenkomsten `TIME` , `time` , `tImE` , ... |
| `_sensitiveness` | `Float` | Hiermee kan een bepaalde marge voor `float` -waarden als hetzelfde worden beschouwd (om technische beperkingen te omzeilen vanwege de interne representatie van `float` -waarden; dit moet worden vermeden, omdat deze optie een negatief effect kan hebben op de prestaties |

De uitdrukkingen kunnen aan een reeks met behulp van een logische exploitant (`_logOp`) worden gecombineerd:

* `OR` - de reeks expressies slaagt als ten minste één expressie slaagt
* `AND` - de reeks expressies slagen als alle expressies slagen (standaard)

Elk veld kan met een eigen set expressies worden gefilterd. De expressiesets van alle velden die in het filterargument worden vermeld, worden uiteindelijk gecombineerd door de eigen logische operator.

Een filterdefinitie (doorgegeven als het argument `filter` aan een query) bevat:

* Een subdefinitie voor elk veld (het veld kan worden geopend via de naam ervan). Het filter bevat bijvoorbeeld een veld `lastName` voor het veld `lastName` in het gegevenstype Data (veld)
* Elke subdefinitie bevat de array `_expressions` , met daarin de set expressies en het veld `_logOp` waarin de logische operator wordt gedefinieerd waarmee de expressies moeten worden gecombineerd
* Elke expressie wordt gedefinieerd door de waarde (`value` veld) en de operator (`_operator` veld) waarmee de inhoud van een veld moet worden vergeleken

U kunt `_logOp` weglaten als u items met `AND` en `_operator` wilt combineren als u op gelijkheid wilt controleren, omdat deze waarden standaardinstellingen zijn.

In het volgende voorbeeld wordt een volledige query getoond die alle personen filtert die een `lastName` van `Provo` hebben of `sjö` bevatten, onafhankelijk van het hoofdlettergebruik:

```graphql
{
  authorList(filter: {
    lastname: {
      _logOp: OR
      _expressions: [
        {
          value: "sjö",
          _operator: CONTAINS,
          _ignoreCase: true
        },
        {
          value: "Provo"
        }
      ]
    }
  }) {
    items {
      lastName
      firstName
    }
  }
}
```

Wanneer het uitvoeren van een vraag van GraphQL gebruikend facultatieve variabelen, als een specifieke waarde **niet** voor de facultatieve variabele is verstrekt, dan zal de variabele in de filterevaluatie worden genegeerd. Dit betekent dat queryresultaten alle waarden bevatten, zowel `null` als niet `null` , voor de eigenschap die betrekking heeft op de filtervariabele.

>[!NOTE]
>
>Als a `null` waarde *uitdrukkelijk* voor zulk een variabele wordt gespecificeerd, dan zal de filter slechts `null` waarden voor het overeenkomstige bezit aanpassen.

In de query hieronder ziet u bijvoorbeeld waar geen waarde is opgegeven voor de eigenschap `lastName` :

```graphql
query getAuthorsFilteredByLastName($authorLastName: String) {
  authorList(filter:
    {
      lastName: {_expressions: {value: $authorLastName}
      }}) {
    items {
      lastName
    }
  }
}
```

Alle auteurs worden geretourneerd:

```graphql
{
  "data": {
    "authorList": {
      "items": [
        {
          "lastName": "Hammer"
        },
        {
          "lastName": "Provo"
        },
        {
          "lastName": "Wester"
        },
        {
          "lastName": null
        },
         ...
      ]
    }
  }
}
```

U kunt ook filteren op geneste velden, maar dit wordt afgeraden omdat dit tot prestatieproblemen kan leiden.

Zie voor meer voorbeelden:

* details van [ GraphQL voor AEM uitbreidingen ](#graphql-extensions)

* [Voorbeeldquery&#39;s met deze voorbeeldinhoud en -structuur](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

   * En de [ Inhoud en de Structuur van de Steekproef ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#content-fragment-structure-graphql) voorbereid voor gebruik in steekproefvragen

* [Voorbeeldquery&#39;s op basis van het WKND-project](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## Sorteren {#sorting}

>[!NOTE]
>
>Voor beste prestaties, overweeg [ Bijwerkend uw Fragmenten van de Inhoud voor het pagineren en het Sorteren in het Filtreren van GraphQL ](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md).

Met deze functie kunt u de zoekresultaten sorteren op basis van een opgegeven veld.

De sorteercriteria:

* is een door komma&#39;s gescheiden lijst met waarden die het veldpad aangeven
   * het eerste veld in de lijst definieert de primaire sorteervolgorde
      * het tweede veld wordt gebruikt als twee waarden van het primaire sorteercriterium gelijk zijn
      * het derde veld wordt gebruikt als de eerste twee criteria gelijk zijn , enzovoort .
   * puntnotatie, dat wil zeggen `field1.subfield.subfield` , enzovoort.
* met een optionele bestelrichting
   * ASC (oplopend) of DESC (aflopend); als standaard ASC wordt toegepast
   * de richting kan per gebied worden gespecificeerd; dit vermogen betekent dat u één gebied in stijgende orde kunt sorteren, een andere in dalende orde (naam, firstName DESC)

Bijvoorbeeld:

```graphql
query {
  authorList(sort: "lastName, firstName") {
    items {
      firstName
      lastName
    }
  }
}
```

En ook:

```graphql
{
  authorList(sort: "lastName DESC, firstName DESC") {
    items {
        lastName
        firstName
    }
  }
}
```

U kunt ook sorteren op een veld in een genest fragment met de indeling `nestedFragmentname.fieldname` .

>[!NOTE]
>
>Deze indeling kan negatieve gevolgen hebben voor de prestaties.

Bijvoorbeeld:

```graphql
query {
  articleList(sort: "authorFragment.lastName")  {
    items {
      title
      authorFragment {
        firstName
        lastName
        birthDay
      }
      slug
    }
  }
}
```

## Paginering {#paging}

>[!NOTE]
>
>Voor beste prestaties, overweeg [ Bijwerkend uw Fragmenten van de Inhoud voor het pagineren en het Sorteren in het Filtreren van GraphQL ](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md).

Met deze functie kunt u pagineren uitvoeren op querytypen die een lijst retourneren. Er zijn twee methoden:

* `offset` en `limit` in een query `List`
* `first` en `after` in een query `Paginated`

### Lijstquery - Verschuiven en beperken {#list-offset-limit}

In a `...List` vraag kunt u `offset` en `limit` gebruiken om een specifieke ondergroep van resultaten terug te keren:

* `offset`: geeft de eerste gegevensset op die moet worden geretourneerd
* `limit`: geeft het maximumaantal gegevenssets op dat moet worden geretourneerd

Bijvoorbeeld, om de pagina van resultaten uit te voeren die tot vijf artikelen bevatten, die van het vijfde artikel van de *volledige* resultatenlijst beginnen:

```graphql
query {
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        lastName
        firstName
      }
    }
  }
}
```

<!-- When available link to BP and replace "JCR query level" with a more neutral term. -->

<!-- When available link to BP and replace "JCR query result set" with a more neutral term. -->

>[!NOTE]
>
>* De paginering vereist een stabiele soortorde om correct over veelvoudige vragen te werken die verschillende pagina&#39;s van de zelfde resultaatreeks vragen. Standaard wordt het pad naar de opslagplaats van elk item van de resultaatset gebruikt om ervoor te zorgen dat de volgorde altijd gelijk is. Als een verschillende sorteervolgorde wordt gebruikt en als die sortering niet kan worden uitgevoerd op JCR-queryniveau, heeft dat een negatief effect op de prestaties. De reden hiervoor is dat de volledige resultaatset in het geheugen moet worden geladen voordat de pagina&#39;s worden bepaald.
>
>* Hoe hoger de verschuiving, des te meer tijd neemt het om de items van de volledige set JCR-queryresultaten over te slaan. Een alternatieve oplossing voor grote resultaatsets is de gepagineerde query met `first` en `after` te gebruiken.

### Gepagineerde query - eerste en volgende {#paginated-first-after}

Het `...Paginated` vraagtype gebruikt de meeste `...List` vraagtype eigenschappen (het filtreren, het sorteren) opnieuw, maar in plaats van het gebruiken van `offset`/ `limit` argumenten, gebruikt het `first`/ `after` argumenten zoals die door [ worden bepaald de Specificatie van de Verbindingen van de Curseur van GraphQL ](https://relay.dev/graphql/connections.htm). U kunt een minder formele inleiding in de [ inleiding van GraphQL ](https://graphql.org/learn/pagination/#pagination-and-edges) vinden.

* `first`: De `n` eerste items die moeten worden geretourneerd.
De standaardwaarde is `50` .
Het maximum is `100` .
* `after`: De cursor die het begin van de opgevraagde pagina bepaalt. Het punt dat door de curseur wordt vertegenwoordigd is niet inbegrepen in de resultaatreeks. De cursor van een item wordt bepaald door het veld `cursor` van de `edges` -structuur.

Bijvoorbeeld, output de pagina van resultaten die tot vijf avonturen bevatten, die van het bepaalde curseurpunt in de *volledige* resultatenlijst beginnen:

```graphql
query {
    adventurePaginated(first: 5, after: "ODg1MmMyMmEtZTAzMy00MTNjLThiMzMtZGQyMzY5ZTNjN2M1") {
        edges {
          cursor
          node {
            title
          }
        }
        pageInfo {
          endCursor
          hasNextPage
        }
    }
}
```

<!-- When available link to BP -->
<!-- Due to internal technical constraints, performance will degrade if sorting and filtering is applied on nested fields. Therefore it is recommended to use filter/sort fields stored at root level. For more information, see the [Best Practices document](link). -->

>[!NOTE]
>
>* Standaard wordt bij paginering de UUID gebruikt van het opslagplaats-knooppunt dat het fragment vertegenwoordigt voor de volgorde van de resultaten, om ervoor te zorgen dat de volgorde van de resultaten altijd gelijk is. Wanneer `sort` wordt gebruikt, wordt UUID impliciet gebruikt om een unieke soort te verzekeren; zelfs voor twee punten met identieke soortsleutels.
>
>* Als gevolg van interne technische beperkingen neemt de prestatie af als sortering en filtering worden toegepast op geneste velden. Gebruik daarom filter-/sorteervelden die op hoofdniveau zijn opgeslagen. Deze techniek is ook de geadviseerde manier als u grote gepagineerde resultaatreeksen wilt vragen.

## GraphQL Persisted Queries - caching inschakelen in Dispatcher {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Als het in het voorgeheugen onderbrengen in Dispatcher dan wordt toegelaten is de [ filter CORS ](#cors-filter) niet nodig, en zodat kan die sectie worden genegeerd.

Het in cache plaatsen van doorlopende query&#39;s is niet standaard ingeschakeld in de Dispatcher. Standaardactivering is niet mogelijk omdat klanten die gebruikmaken van CORS (Cross-Origin Resource Sharing) met meerdere origines hun Dispatcher-configuratie moeten controleren en mogelijk bijwerken.

>[!NOTE]
>
>De Dispatcher slaat de header `Vary` niet in cache op.
>
>Caching van andere CORS-verwante kopballen kan in de Dispatcher worden toegelaten, maar zou ontoereikend kunnen zijn wanneer er veelvoudige oorsprong CORS zijn.

### Het in cache plaatsen van doorlopende query&#39;s inschakelen {#enable-caching-persisted-queries}

Om het in cache plaatsen van persisted query&#39;s mogelijk te maken, zijn de volgende updates van de Dispatcher-configuratiebestanden vereist:

* `<conf.d/rewrites/base_rewrite.rules>`

  ```xml
  # Allow the dispatcher to be able to cache persisted queries - they need an extension for the cache file
  RewriteCond %{REQUEST_URI} ^/graphql/execute.json
  RewriteRule ^/(.*)$ /$1;.json [PT] 
  ```

  >[!NOTE]
  >
  >De Dispatcher voegt het achtervoegsel `.json` toe aan alle blijvende query-URL&#39;s, zodat het resultaat in de cache kan worden opgeslagen.
  >
  >Hiermee zorgt u ervoor dat de query voldoet aan de Dispatcher-vereisten voor documenten die in cache kunnen worden geplaatst. Voor verdere details zie [ Hoe keert Dispatcher documenten terug?](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html?lang=nl-NL#how-does-the-dispatcher-return-documents%3F)

* `<conf.dispatcher.d/filters/ams_publish_filters.any>`

  ```xml
  # Allow GraphQL Persisted Queries & preflight requests
  /0110 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
  ```

### CORS-configuratie in de Dispatcher {#cors-configuration-in-dispatcher}

Klanten die CORS-aanvragen gebruiken, moeten mogelijk hun CORS-configuratie in de Dispatcher controleren en bijwerken.

* De header `Origin` mag niet worden doorgegeven aan AEM die publiceert via de Dispatcher:
   * Controleer het `clientheaders.any` -bestand.
* In plaats daarvan moeten CORS-aanvragen worden beoordeeld op toegestane oorsprong op Dispatcher-niveau. Deze benadering zorgt er ook voor dat aan CORS gerelateerde koppen in alle gevallen correct worden ingesteld op één plaats.
   * Een dergelijke configuratie moet worden toegevoegd aan het `vhost` -bestand. Hieronder wordt een voorbeeldconfiguratie gegeven; voor de eenvoud is alleen het gedeelte met betrekking tot CORS opgenomen. U kunt deze aanpassen voor uw specifieke gebruiksgevallen.

  ```xml
  <VirtualHost *:80>
     ServerName "publish"
  
     # ...
  
     <IfModule mod_headers.c>
         Header add X-Vhost "publish"
  
          ################## Start of the CORS specific configuration ##################
  
          SetEnvIfExpr "req_novary('Origin') == ''"  CORSType=none CORSProcessing=false
          SetEnvIfExpr "req_novary('Origin') != ''"  CORSType=cors CORSProcessing=true CORSTrusted=false
  
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') == '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=invalidpreflight CORSProcessing=false
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') != '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=preflight CORSProcessing=true CORSTrusted=false
          SetEnvIfExpr "req_novary('Origin') -strcmatch 'https://%{HTTP_HOST}*'"  CORSType=samedomain CORSProcessing=false
  
          # For requests that require CORS processing, check if the Origin can be trusted
          SetEnvIfExpr "%{HTTP_HOST} =~ /(.*)/ " ParsedHost=$1
  
          ################## Adapt the regex to match CORS origin for your environment
          SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*.your-domain.tld(:\d+)?$)#" CORSTrusted=true
  
          # Extract the Origin header 
          SetEnvIfNoCase ^Origin$ ^https://(.*)$ CORSTrustedOrigin=https://$1
  
          # Flush If already set
          Header unset Access-Control-Allow-Origin
          Header unset Access-Control-Allow-Credentials
  
          # Trusted
          Header always set Access-Control-Allow-Credentials "true" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Origin "%{CORSTrustedOrigin}e" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Methods "GET" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Max-Age 1800 "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Headers "Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers" "expr=reqenv('CORSTrusted') == 'true'"
  
          # Non-CORS or Not Trusted
          Header unset Access-Control-Allow-Credentials "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Origin "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Methods "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Max-Age "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
  
          # Always vary on origin, even if its not there.
          Header merge Vary Origin
  
          # CORS - send 204 for CORS requests which are not trusted
          RewriteCond expr "reqenv('CORSProcessing') == 'true' && reqenv('CORSTrusted') == 'false'"
          RewriteRule "^(.*)" - [R=204,L]
  
          ################## End of the CORS specific configuration ##################
  
     </IfModule>
  
     <Directory />
  
         # ...
  
     </Directory>
  
     # ...
  
  </VirtualHost>
  ```

## GraphQL for AEM - Overzicht van extensies {#graphql-extensions}

De basisverrichting van vragen met GraphQL voor AEM voldoet aan de standaardspecificatie van GraphQL. Voor GraphQL-query&#39;s met AEM zijn er een aantal extensies:

* Als u één resultaat nodig hebt:
   * gebruik de modelnaam; bijvoorbeeld stad

* Als u een lijst met resultaten verwacht:
   * `List` toevoegen aan de modelnaam, bijvoorbeeld `cityList`
   * Zie [ Vraag van de Steekproef - Al Informatie over Alle Plaatsen ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-information-all-cities)

  U kunt dan:

   * [De resultaten sorteren](#sorting)

      * `ASC` : oplopend
      * `DESC` : aflopend

   * Retourneer een pagina met resultaten met:

      * [Een lijstvraag met compensatie en grens](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#list-offset-limit)
      * [Een gepagineerde query met eerste en volgende](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#paginated-first-after)
   * Zie [ Vraag van de Steekproef - Al Informatie over Alle Plaatsen ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-information-all-cities)

* Het filter `includeVariations` wordt opgenomen in het type query van `List` . Als u Variaties in inhoudsfragmenten in de queryresultaten wilt ophalen, moet het filter `includeVariations` zijn ingesteld op `true` .

  >[!CAUTION]
  >Het filter `includeVariations` kan niet worden gebruikt in combinatie met het door het systeem gegenereerde veld `_variation` .

* Als u logische OR wilt gebruiken:
   * use ` _logOp: OR`
   * Zie [ Vraag van de Steekproef - Alle Personen die een naam van &quot;Banen&quot;of &quot;Smith&quot;hebben ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-persons-jobs-smith)

* Logische AND bestaat ook, maar is (vaak) impliciet

* U kunt zoeken naar veldnamen die overeenkomen met de velden in het model van het inhoudsfragment
   * Zie [ Vraag van de Steekproef - Volledige Details van CEO en Werknemers van een Bedrijf ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-full-details-company-ceos-employees)

* Naast de velden van uw model zijn er velden die door het systeem worden gegenereerd (voorafgegaan door een onderstrepingsteken):

   * Voor inhoud:

      * `_locale` : om de taal te onthullen; gebaseerd op Taalbeheer
         * Zie [ Vraag van de Steekproef voor veelvoudige Fragmenten van de Inhoud van een bepaalde scène ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-multiple-fragments-given-locale)

      * `_metadata` : om metagegevens voor het fragment weer te geven
         * Zie [ Vraag van de Steekproef voor Meta-gegevens - maak een lijst van de Meta-gegevens voor Uitreiking genoemd GB ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-metadata-awards-gb)

      * `_model` : zoeken naar een inhoudsfragmentmodel toestaan (pad en titel)
         * Zie [ Vraag van de Steekproef voor een Model van het Fragment van de Inhoud van een Model ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-content-fragment-model-from-model)

      * `_path` : het pad naar het inhoudsfragment in de opslagplaats
         * Zie [ Vraag van de Steekproef - Één enkel Specifiek Fragment van de Stad ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)

      * `_reference` : om verwijzingen weer te geven; inclusief inline-verwijzingen in de Rich Text Editor
         * Zie [ Vraag van de Steekproef voor de veelvoudige Fragmenten van de Inhoud met Vooraf ingestelde Verwijzingen ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-multiple-fragments-prefetched-references)

      * `_variation` : specifieke variaties in het inhoudsfragment weergeven

        >[!NOTE]
        >
        >Als de opgegeven variatie niet bestaat voor een inhoudsfragment, wordt de hoofdvariatie geretourneerd als een standaardinstelling (fallback).

        >[!CAUTION]
        >Het door het systeem gegenereerde veld `_variation` kan niet samen met het filter `includeVariations` worden gebruikt.

         * Zie [ Vraag van de Steekproef - Alle Steden met een Benoemde Variatie ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-cities-named-variation)

      * `_tags` : om de id&#39;s weer te geven van inhoudsfragmenten of variaties die tags bevatten. Deze lijst is een array van `cq:tags` -id&#39;s.

         * Zie [ Vraag van de Steekproef - Namen van Alle Plaatsen die als de Breuken van de Stad ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-names-all-cities-tagged-city-breaks) worden geëtiketteerd
         * Zie [ Vraag van de Steekproef voor de Variaties van het Fragment van Inhoud van een bepaald Model dat een specifieke markering in bijlage ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-fragment-variations-given-model-specific-tag) heeft

        >[!NOTE]
        >
        >Tags kunnen ook worden opgevraagd door de metagegevens van een inhoudsfragment weer te geven.

   * En bewerkingen:

      * `_operator` : specifieke operatoren toepassen; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`, `STARTS_WITH`
         * Zie [ Vraag van de Steekproef - Alle Personen die geen naam van &quot;Banen&quot;hebben ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-persons-not-jobs)
         * Zie [ Vraag van de Steekproef - Alle avonturen waar `_path` met een specifieke prefix ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-all-adventures-cycling-path-filter) begint

      * `_apply` : specifieke voorwaarden toepassen, bijvoorbeeld `AT_LEAST_ONCE`
         * Zie [ Vraag van de Steekproef - filter op een serie met een punt dat minstens eens ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-array-item-occur-at-least-once) moet voorkomen

      * `_ignoreCase` : de kwestie negeren bij het opvragen
         * Zie [ Steekproefvraag - Alle steden met San in de naam, ongeacht geval ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-cities-san-ignore-case)

* GraphQL-union-typen worden ondersteund:

   * use `... on`
      * Zie [ Vraag van de Steekproef voor een Fragment van de Inhoud van een specifiek Model met een Verwijzing van de Inhoud ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-fragment-specific-model-content-reference)

* Extra fallback bij het opvragen van geneste fragmenten:

   * Als de gevraagde variatie niet in een genest fragment bestaat, dan is de **Hoofd** variatie teruggekeerd.

### CORS-filter {#cors-filter}

>[!CAUTION]
>
>Als [ caching in Dispatcher ](#graphql-persisted-queries-enabling-caching-dispatcher) dan is toegelaten is het filter CORS niet nodig, en zo kan deze sectie worden genegeerd.

>[!NOTE]
>
>Voor een gedetailleerd overzicht van het CORS middel delend beleid in AEM, zie [ het Delen van het Middel van de Cross-Origin begrijpen (CORS) ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=nl-NL#understand-cross-origin-resource-sharing-(cors)).

Om tot het eindpunt van GraphQL toegang te hebben, vorm een beleid CORS in de bewaarplaats van de Kit van de klant. Deze configuratie wordt gedaan door een aangewezen OSGi CORS configuratiedossier voor één of meerdere gewenste eindpunten toe te voegen.

Deze configuratie moet een vertrouwde website-oorsprong `alloworigin` of `alloworiginregexp` opgeven waarvoor toegang moet worden verleend.

Als u bijvoorbeeld toegang wilt verlenen tot het GraphQL-eindpunt en het voortgeduurde zoekeindpunt voor `https://my.domain` , kunt u het volgende gebruiken:

```xml
{
  "supportscredentials":true,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/_cq_graphql/global/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

Als u een ijkpad voor het eindpunt hebt geconfigureerd, kunt u dit ook gebruiken in `allowedpaths` .

### Refererfilter {#referrer-filter}

Naast de configuratie CORS, moet een filter van de Referateur worden gevormd om toegang van derdegastheren toe te staan.

Dit filter wordt gedaan door een aangewezen OSGi de configuratiedossier van de Filter toe te voegen dat:

* geeft de hostnaam van een vertrouwde website op; ofwel `allow.hosts` ofwel `allow.hosts.regexp` ,
* verleent toegang voor deze gastheernaam.

Als u bijvoorbeeld toegang wilt verlenen voor aanvragen bij de Referenter `my.domain` , kunt u:

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
      ""
    ]
}
```

>[!CAUTION]
>
>De klant blijft verantwoordelijk voor:
>
>* alleen toegang verlenen tot vertrouwde domeinen
>* ervoor zorgen dat geen gevoelige informatie wordt blootgesteld
>* Gebruik geen vervangingswaarde [ * ] syntaxis; deze functionaliteit maakt voor authentiek verklaarde toegang tot het eindpunt van GraphQL onbruikbaar en stelt het aan de volledige wereld ook bloot.

>[!CAUTION]
>
>Alle schema&#39;s van GraphQL [&#128279;](#schema-generation) (die uit de Modellen van het Fragment van de Inhoud worden afgeleid die **&#x200B;**&#x200B;zijn toegelaten) zijn leesbaar door het eindpunt van GraphQL.
>
>Deze functionaliteit houdt in dat u ervoor moet zorgen dat er geen gevoelige gegevens beschikbaar zijn, omdat deze op deze manier kunnen worden gelekt. Het bevat bijvoorbeeld informatie die als veldnamen aanwezig kan zijn in de modeldefinitie.

## Beperkingen {#limitations}

Om tegen potentiële problemen te beschermen worden er standaardbeperkingen opgelegd aan uw vragen:

* De query mag niet meer dan 1M (1024 * 1024) tekens bevatten
* De query mag niet meer dan 15000 tokens bevatten
* De query mag niet meer dan 200000 whitespace-tokens bevatten

U moet zich ook bewust zijn van:

* Er wordt een fout in een veldconflict geretourneerd wanneer uw GraphQL-query velden met dezelfde naam bevat in twee (of meer) modellen en aan de volgende voorwaarden wordt voldaan:

   * Dus waar:

      * Twee (of meer modellen) worden gebruikt als mogelijke verwijzingen; wanneer zij als toegestaan **ModelType** in de verwijzing van het Fragment van de Inhoud worden bepaald.

     en:

      * Deze twee modellen hebben gebieden met een gemeenschappelijke naam; dat betekent de zelfde naam voorkomt in beide modellen.

     en

      * Deze velden zijn van verschillende gegevenstypen.

   * Bijvoorbeeld:

      * Wanneer twee (of meer) fragmenten met verschillende modellen (bijvoorbeeld `M1` , `M2` ) worden gebruikt als mogelijke verwijzingen (Content Reference of Fragment Reference) uit een ander fragment, bijvoorbeeld `Fragment1` `MultiField/List`
      * Deze twee fragmenten met verschillende modellen (`M1`, `M2`) hebben velden met dezelfde naam, maar verschillende typen.
Ter illustratie:
         * `M1.Title` as `Text`
         * `M2.Title` as `Text/MultiField`
      * Er treedt dan een fout in het veldconflict op als de GraphQL-query het veld `Title` bevat.

## Verificatie {#authentication}

Zie [ Authentificatie voor Verre AEM GraphQL Vragen over de Fragmenten van de Inhoud ](/help/sites-developing/headless/graphql-api/graphql-authentication-content-fragments.md).

## Veelgestelde vragen {#faqs}

De gerezen vragen:

1. **Q**: &quot;*hoe is GraphQL API voor AEM verschillend van de Bouwer van de Vraag API?*&quot;

   * **A**:
&quot;*de AEM GraphQL API biedt totale controle op de output JSON aan, en is een industriestandaard voor het vragen van inhoud.
In de toekomst, is AEM van plan om in AEM GraphQL API te investeren.*&quot;

## Zelfstudie - Aan de slag met AEM Headless en GraphQL {#tutorial}

Op zoek naar een praktische zelfstudie? Controle uit [ Begonnen het Worden met AEM Zwaartepunt en GraphQL ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=nl-NL) leerprogramma van begin tot eind illustrerend hoe te om inhoud op te bouwen en bloot te stellen gebruikend AEM GraphQL APIs en verbruikt door een externe app, in een hoofdCMS scenario.
