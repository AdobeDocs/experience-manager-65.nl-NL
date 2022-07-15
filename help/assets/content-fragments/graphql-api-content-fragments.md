---
title: AEM GraphQL API voor gebruik met Content Fragments
description: Leer hoe u Content Fragments in Adobe Experience Manager (AEM) kunt gebruiken met de AEM GraphQL API voor het leveren van inhoud zonder kop.
feature: Content Fragments,GraphQL API
exl-id: beae1f1f-0a76-4186-9e58-9cab8de4236d
source-git-commit: 6f3f88ea0f07c97fa8d7ff3bdd1c89114d12a8a1
workflow-type: tm+mt
source-wordcount: '3986'
ht-degree: 0%

---

# AEM GraphQL API voor gebruik met Content Fragments {#graphql-api-for-use-with-content-fragments}

Leer hoe u Content Fragments in Adobe Experience Manager (AEM) kunt gebruiken met de AEM GraphQL API voor het leveren van inhoud zonder kop.

AEM GraphQL API die wordt gebruikt met Content Fragments is sterk gebaseerd op de standaard, open-source GraphQL API.

Door de GraphQL API in AEM te gebruiken, kunt u inhoudsfragmenten efficiënt aan JavaScript-clients leveren in CMS-implementaties zonder kop:

* Herhalende API-aanvragen voorkomen, zoals REST,
* ervoor zorgen dat de levering beperkt blijft tot de specifieke eisen;
* Het toestaan voor bulklevering van precies wat voor het teruggeven als antwoord op één enkele API vraag nodig is.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM):
>
>* [AEM Commerce gebruikt gegevens van een Commerce-platform via GraphQL](/help/commerce/cif/integrating/magento.md).
>* AEM Inhoudsfragmenten werken samen met de AEM GraphQL API (een aangepaste implementatie op basis van standaard GraphQL) voor gestructureerde inhoud voor gebruik in uw toepassingen.


## De GraphQL API {#graphql-api}

GraphQL is:

* &quot;*...een querytaal voor API&#39;s en een runtime voor het uitvoeren van deze query&#39;s met uw bestaande gegevens. GraphQL biedt een volledige en begrijpelijke beschrijving van de gegevens in uw API, geeft clients de mogelijkheid om precies te vragen wat ze nodig hebben en niets meer, maakt het gemakkelijker om API&#39;s in de loop der tijd te ontwikkelen en maakt krachtige ontwikkelaarsgereedschappen mogelijk.*&quot;.

   Zie [GraphQL.org](https://graphql.org)

* &quot;*...een open specificatie voor een flexibele API-laag. GrafiekQL op uw bestaande achtergronden plaatsen om producten sneller dan ooit te bouwen....*&quot;.

   Zie [GrafiekQL verkennen](https://www.graphql.com).

* *&quot;...een taal en specificatie voor gegevensquery die in 2012 intern door Facebook zijn ontwikkeld, voordat deze in 2015 openbaar is uitbesteed. Het biedt een alternatief voor op REST gebaseerde architecturen met als doel de productiviteit van ontwikkelaars te verhogen en de hoeveelheden overgedragen gegevens te minimaliseren. GraphQL wordt gebruikt in productie door honderden organisaties van elke grootte...&quot;*

   Zie [GraphQL Foundation](https://foundation.graphql.org/).

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all of the tools they need to understand and adopt GraphQL.*". 
-->

Zie de volgende secties (onder andere bronnen) voor meer informatie over de GraphQL API:

* At [graphql.org](https://graphql.org):

   * [Inleiding tot GraphQL](https://graphql.org/learn)

   * [De GraphQL-specificatie](https://spec.graphql.org/)

* At [graphql.com](https://graphql.com):

   * [Hulplijnen](https://www.graphql.com/guides/)

   * [Tutorials](https://www.graphql.com/tutorials/)

   * [Casestudy&#39;s](https://www.graphql.com/case-studies/)

GraphQL voor AEM implementatie is gebaseerd op de standaard Java Library GraphQL. Zie:

* [graphQL.org - Java](https://graphql.org/code/#java)

* [GraphQL Java bij GitHub](https://github.com/graphql-java)

### GraphQL-terminologie {#graphql-terminology}

GraphQL gebruikt het volgende:

* **[Zoekopdrachten](https://graphql.org/learn/queries/)**

* **[Schema&#39;s en typen](https://graphql.org/learn/schema/)**:

   * Schema&#39;s worden gegenereerd door AEM op basis van de modellen van inhoudsfragmenten.
   * Gebruikend uw schema&#39;s, stelt GraphQL de types en verrichtingen voor toegelaten GraphQL voor AEM implementatie voor.

* **[Velden](https://graphql.org/learn/queries/#fields)**

* **[GraphQL-eindpunt](#graphql-aem-endpoint)**
   * De weg in AEM die aan vragen GraphQL antwoordt, en toegang tot de schema&#39;s GraphQL verleent.

   * Zie [GrafiekQL-eindpunt inschakelen](#enabling-graphql-endpoint) voor nadere bijzonderheden.

Zie de [(GraphQL.org) Inleiding tot GraphQL](https://graphql.org/learn/) voor uitvoerige informatie, waaronder [Aanbevolen werkwijzen](https://graphql.org/learn/best-practices/).

### GraphQL-querytypen {#graphql-query-types}

Met GraphQL kunt u vragen uitvoeren om of terug te keren:

* A **enkel item**

* A **[lijst van vermeldingen](https://graphql.org/learn/schema/#lists-and-non-null)**

U kunt ook het volgende uitvoeren:

* [Blijvende query&#39;s die in cache zijn geplaatst](#persisted-queries-caching)

>[!NOTE]
>U kunt vragen van GraphQL testen en zuiveren gebruikend [GraphiQL IDE](#graphiql-interface).

## GraphQL voor AEM Endpoint {#graphql-aem-endpoint}

Het eindpunt is de weg die wordt gebruikt om tot GraphQL voor AEM toegang te hebben. Met dit pad kunt u (of uw app) het volgende doen:

* toegang tot het GraphQL-schema;
* verzend uw vragen GraphQL,
* ontvangt de reacties (op uw vragen GraphQL).

Er zijn twee soorten eindpunten in AEM:

* Algemeen
   * Beschikbaar voor gebruik door alle sites.
   * Dit eindpunt kan alle Modellen van het Fragment van de Inhoud van alle configuraties van Plaatsen gebruiken (die in [Configuratiebrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)).
   * Als er om het even welke Modellen van het Fragment van de Inhoud zijn die onder de configuraties van Plaatsen zouden moeten worden gedeeld, dan zouden deze onder de globale configuraties van Plaatsen moeten worden gecreeerd.
* Siteconfiguraties:
   * Komt overeen met een configuratie Sites, zoals gedefinieerd in het dialoogvenster [Configuratiebrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser).
   * Specifiek voor een opgegeven site/project.
   * Een configuratie-specifiek eindpunt van Plaatsen zal de Modellen van het Fragment van de Inhoud van die specifieke configuratie van Plaatsen samen met die van de globale configuratie van Plaatsen gebruiken.

>[!CAUTION]
>
>Met de Inhoudsfragmenteditor kan een inhoudsfragment van een siteconfiguratie verwijzen naar een inhoudsfragment van een andere siteconfiguratie (via beleid).
>
>In een dergelijk geval zal niet alle inhoud kunnen terugwinnen gebruikend een de configuratie van Plaatsen specifiek eindpunt.
>
>De inhoudauteur zou dit scenario moeten controleren; Het kan bijvoorbeeld handig zijn om gedeelde modellen van inhoudsfragmenten onder de configuratie Algemene sites te plaatsen.

De bewaarplaatspad van GraphQL voor AEM globale eindpunt is:

`/content/cq:graphql/global/endpoint`

Voor welke toepassing uw toepassing het volgende pad in de aanvraag-URL kan gebruiken:

`/content/_cq_graphql/global/endpoint.json`

Om een eindpunt voor GraphQL voor AEM toe te laten moet u:

* [GrafiekQL-eindpunt inschakelen](#enabling-graphql-endpoint)
* [Uw GraphQL-eindpunt publiceren](#publishing-graphql-endpoint)

### GrafiekQL-eindpunt inschakelen {#enabling-graphql-endpoint}

Om een Eindpunt te toelaten GraphQL moet u eerst een aangewezen configuratie hebben. Zie [Inhoudsfragmenten - Configuratiebrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md).

>[!CAUTION]
>
>Als de [gebruik van inhoudsfragmentmodellen is niet ingeschakeld](/help/assets/content-fragments/content-fragments-configuration-browser.md)de **Maken** is niet beschikbaar.

Om het overeenkomstige eindpunt toe te laten:

1. Navigeren naar **Gereedschappen**, **Activa** selecteert u vervolgens **GraphQL**.
1. Selecteer **Maken**.
1. De **Nieuw GraphQL-eindpunt maken** wordt geopend. Hier kunt u opgeven:
   * **Naam**: naam van het eindpunt; U kunt elke gewenste tekst invoeren.
   * **GrafiekQL-schema gebruiken dat is opgegeven door**: Gebruik de vervolgkeuzelijst om de gewenste site of het vereiste project te selecteren.

   >[!NOTE]
   >
   >De volgende waarschuwing wordt weergegeven in het dialoogvenster:
   >
   >* *De eindpunten van GraphQL kunnen gegevensveiligheid en prestatieskwesties introduceren als niet zorgvuldig beheerd. Gelieve te verzekeren om aangewezen toestemmingen te plaatsen na het creëren van een eindpunt.*


1. Bevestigen met **Maken**.
1. De **Volgende stappen** de dialoog zal een directe verbinding aan de console van de Veiligheid verstrekken zodat u kunt ervoor zorgen dat het onlangs gecreeerde eindpunt geschikte toestemmingen heeft.

   >[!CAUTION]
   >
   >Het eindpunt is toegankelijk voor iedereen. Dit kan - vooral bij publiceer instanties - een veiligheidszorg veroorzaken, aangezien de vragen GraphQL een zware lading op de server kunnen opleggen.
   >
   >U kunt opstelling ACLs, aangewezen aan uw gebruiksgeval, op het eindpunt.

### Het Eindpunt GraphQL publiceren {#publishing-graphql-endpoint}

Selecteer het nieuwe eindpunt en **Publiceren** om het volledig beschikbaar te maken in alle milieu&#39;s.

>[!CAUTION]
>
>Het eindpunt is toegankelijk voor iedereen.
>
>Bij het publiceren van instanties kan dit een veiligheidszorg veroorzaken, aangezien de vragen GraphQL een zware lading op de server kunnen opleggen.
>
>U moet opstelling ACLs aangewezen aan uw gebruiksgeval op het eindpunt.

## GraphiQL Interface {#graphiql-interface}

Tenuitvoerlegging van de norm [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) interface is beschikbaar voor gebruik met AEM GraphQL. Dit kan [geïnstalleerd met AEM](#installing-graphiql-interface).

>[!NOTE]
>
>GraphiQL is gebonden het globale eindpunt (en werkt niet met andere eindpunten voor specifieke configuraties van Plaatsen).

Met deze interface kunt u query&#39;s rechtstreeks invoeren en testen.

Bijvoorbeeld:

* `http://localhost:4502/content/graphiql.html`

Dit biedt functies zoals syntaxismarkering, automatisch aanvullen, automatisch voorstellen, samen met een geschiedenis en online documentatie:

![GraphiQL Interface](assets/cfm-graphiql-interface.png "GraphiQL Interface")

### De interface AEM GraphiQL installeren {#installing-graphiql-interface}

De GraphiQL-gebruikersinterface kan worden geïnstalleerd op AEM met een toegewezen pakket: de [GraphiQL-inhoudspakket v0.0.6 (2021.3)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-graphql/graphiql-0.0.6.zip) pakket.

>[!NOTE]
>
>Het beschikbare pakket is volledig compatibel met AEM 6.5.10.0 en AEM as a Cloud Service.

## Kwesties gebruiken voor auteur- en publicatie-omgevingen {#use-cases-author-publish-environments}

De gebruiksgevallen kunnen afhankelijk zijn van het type AEM omgeving:

* Publicatie-omgeving; gebruikt voor:
   * Query-gegevens voor JS-toepassing (standaardgebruikscenario)

* Auteursomgeving; gebruikt voor:
   * Query-gegevens voor &quot;inhoudsbeheerdoeleinden&quot;:
      * GraphQL in AEM is momenteel een alleen-lezen API.
      * De REST-API kan worden gebruikt voor CR(u)D-bewerkingen.

## Machtigingen {#permission}

De machtigingen zijn vereist voor toegang tot middelen.

## Schema genereren {#schema-generation}

GraphQL is een sterk getypte API, wat betekent dat de gegevens duidelijk gestructureerd en georganiseerd moeten zijn door type.

De specificatie GraphQL verstrekt een reeks richtlijnen op hoe te om tot een robuuste API voor het ondervragen van gegevens over een bepaalde instantie te leiden. Om dit te doen, moet een cliënt halen [Schema](#schema-generation), die alle typen bevat die nodig zijn voor een query.

Voor Inhoudsfragmenten zijn de GraphQL-schema&#39;s (structuur en typen) gebaseerd op **Ingeschakeld** [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md) en hun gegevenstypen.

>[!CAUTION]
>
>Alle schema&#39;s GraphQL (die uit de Modellen van het Fragment van de Inhoud worden afgeleid die zijn **Ingeschakeld**) zijn leesbaar door het eindpunt GraphQL.
>
>Dit betekent dat u ervoor moet zorgen dat er geen gevoelige gegevens beschikbaar zijn, aangezien deze op deze manier kunnen worden gelekt; Dit omvat bijvoorbeeld informatie die als veldnamen in de modeldefinitie aanwezig kan zijn.

Als een gebruiker bijvoorbeeld een Content Fragment Model heeft gemaakt, genaamd `Article`AEM het object genereren `article` van een type `ArticleModel`. De velden in dit type komen overeen met de velden en gegevenstypen die in het model zijn gedefinieerd.

1. A Content Fragment Model:

   ![Inhoudsfragmentmodel voor gebruik met GraphQL](assets/cfm-graphqlapi-01.png "Inhoudsfragmentmodel voor gebruik met GraphQL")

1. Het corresponderende GraphQL-schema (uitvoer van de automatische documentatie GraphiQL):
   ![GrafiekQL-schema gebaseerd op inhoudsfragmentmodel](assets/cfm-graphqlapi-02.png "GrafiekQL-schema gebaseerd op inhoudsfragmentmodel")

   Dit toont aan dat het geproduceerde type `ArticleModel` bevat diverse [velden](#fields).

   * Drie van hen zijn gecontroleerd door de gebruiker: `author`, `main` en `referencearticle`.

   * De andere velden zijn automatisch toegevoegd door AEM en zijn nuttige methoden voor het verschaffen van informatie over een bepaald inhoudsfragment. in dit voorbeeld: `_path`, `_metadata`, `_variations`. Deze [helpervelden](#helper-fields) zijn gemarkeerd met een voorgaande `_` om onderscheid te maken tussen wat door de gebruiker is gedefinieerd en wat automatisch is gegenereerd.

1. Nadat een gebruiker tot een Fragment van de Inhoud leidt dat op het model van het Artikel wordt gebaseerd, kan het dan door GraphQL worden ondervraagd. Zie voor voorbeelden de [Voorbeeldquery&#39;s](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries) (op basis van een [structuur van voorbeeldinhoudsfragment voor gebruik met GraphQL](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)).

In GraphQL voor AEM, is het schema flexibel. Dit betekent dat deze telkens automatisch wordt gegenereerd wanneer een inhoudsfragmentmodel wordt gemaakt, bijgewerkt of verwijderd. De caches voor het gegevensschema worden ook vernieuwd wanneer u een model van het inhoudsfragment bijwerkt.

De dienst van GrafiekQL van Plaatsen luistert (in de achtergrond) naar om het even welke die wijzigingen aan een Model van het Fragment van de Inhoud worden aangebracht. Wanneer updates worden ontdekt, slechts wordt dat deel van het schema opnieuw geproduceerd. Deze optimalisatie bespaart tijd en zorgt voor stabiliteit.

Als u bijvoorbeeld:

1. Een pakket installeren met `Content-Fragment-Model-1` en `Content-Fragment-Model-2`:

   1. GraphQL-typen voor `Model-1` en `Model-2` wordt gegenereerd.

1. Vervolgens wijzigen `Content-Fragment-Model-2`:

   1. Alleen de `Model-2` Het type GraphQL wordt bijgewerkt.

   1. Overwegende `Model-1` blijft hetzelfde.

>[!NOTE]
>
>Dit is belangrijk om op te merken voor het geval u bulkupdates op de Modellen van het Fragment van de Inhoud door REST api, of anders wilt doen.

Het schema wordt gediend door het zelfde eindpunt zoals de vragen GraphQL, met de cliënt die het feit behandelt dat het schema met de uitbreiding wordt geroepen `GQLschema`. U kunt bijvoorbeeld een eenvoudige `GET` verzoek op `/content/cq:graphql/global/endpoint.GQLschema` resulteert in de uitvoer van het schema met het inhoudstype: `text/x-graphql-schema;charset=iso-8859-1`.

### Schema genereren - Niet-gepubliceerde modellen {#schema-generation-unpublished-models}

Wanneer Inhoudsfragmenten zijn genest, kan een bovenliggend inhoudsfragmentmodel worden gepubliceerd, maar een model waarnaar wordt verwezen, niet.

>[!NOTE]
>
>De AEM UI verhindert dit gebeurt, maar als het publiceren programmatically, of met inhoudspakketten wordt gemaakt, kan het voorkomen.

Wanneer dit gebeurt, genereert AEM een *onvolledig* Schema voor het bovenliggende inhoudsfragmentmodel. Dit betekent dat de fragmentverwijzing, die afhankelijk is van het niet-gepubliceerde model, uit het schema wordt verwijderd.

## Fields {#fields}

Binnen het schema zijn er afzonderlijke velden, van twee basiscategorieën:

* Velden die u genereert.

   Een selectie van [Veldtypen](#field-types) worden gebruikt om velden te maken die zijn gebaseerd op de manier waarop u het inhoudsfragmentmodel configureert. De veldnamen zijn afkomstig uit het **Eigenschapnaam** van het **Gegevenstype**.

   * Er is ook **Renderen als** in aanmerking te nemen eigenschap, omdat gebruikers bepaalde gegevenstypen kunnen configureren; bijvoorbeeld als tekst met één regel of als een tekstveld met meerdere regels.

* GraphQL voor AEM genereert ook een aantal [helpervelden](#helper-fields).

   Deze worden gebruikt om een inhoudsfragment te identificeren of om meer informatie over een inhoudsfragment te krijgen.

### Veldtypen {#field-types}

GraphQL voor AEM ondersteunt een lijst met typen. Alle ondersteunde gegevenstypen van het Content Fragment Model en de corresponderende typen GraphQL worden weergegeven:

| Inhoudsfragmentmodel - Gegevenstype | Type GraphQL | Beschrijving |
|--- |--- |--- |
| Tekst met één regel | String, [String] |  Wordt gebruikt voor eenvoudige tekenreeksen, zoals namen van auteurs, locaties, enzovoort. |
| Tekst met meerdere regels | Tekenreeks |  Wordt gebruikt voor het uitvoeren van tekst, zoals de hoofdtekst van een artikel |
| Getal |  Float [Float] | Wordt gebruikt om het zwevende-kommagetal en de reguliere getallen weer te geven |
| Boolean |  Boolean |  Gebruikt om selectievakjes weer te geven → eenvoudige true/false-instructies |
| Datum en tijd | Kalender |  Wordt gebruikt om datum en tijd weer te geven in de ISO 8086-indeling. Afhankelijk van het geselecteerde type, zijn er drie aroma&#39;s beschikbaar voor gebruik in AEM GraphQL: `onlyDate`, `onlyTime`, `dateTime` |
| Opsomming |  Tekenreeks |  Wordt gebruikt om een optie weer te geven uit een lijst met opties die bij het maken van het model zijn gedefinieerd |
|  Tags |  [Tekenreeks] |  Wordt gebruikt om een lijst weer te geven met tekenreeksen die tags vertegenwoordigen die in AEM worden gebruikt |
| Content Reference |  Tekenreeks |  Wordt gebruikt om het pad naar een ander element in AEM weer te geven |
| Fragmentverwijzing |  *Een modeltype* |  Wordt gebruikt om te verwijzen naar een ander inhoudsfragment van een bepaald modeltype, dat is gedefinieerd toen het model werd gemaakt. |

### Helpervelden {#helper-fields}

Naast de gegevenstypen voor door de gebruiker gegenereerde velden, genereert GraphQL voor AEM ook een aantal *helper* velden voor het herkennen van een inhoudsfragment of voor het verschaffen van aanvullende informatie over een inhoudsfragment.

#### Pad {#path}

Het padveld wordt gebruikt als id in GraphQL. Het vertegenwoordigt het pad van het Content Fragment-element in de AEM opslagplaats. Dit is de id van een inhoudsfragment, omdat dit:

* uniek is binnen AEM,
* kan gemakkelijk worden opgehaald.

De volgende code geeft de paden weer van alle inhoudsfragmenten die zijn gemaakt op basis van het model van het inhoudsfragment `Person`.

```xml
{
  personList {
    items {
      _path
    }
  }
}
```

Als u één inhoudsfragment van een bepaald type wilt ophalen, moet u ook eerst het pad bepalen. bijvoorbeeld:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      firstName
      name
    }
  }
}
```

Zie [Voorbeeldquery - één specifiek stedenfragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment).

#### Metagegevens {#metadata}

Via GraphQL stelt AEM ook de metagegevens van een inhoudsfragment beschikbaar. Metagegevens zijn de informatie die een inhoudsfragment beschrijft, zoals de titel van een inhoudsfragment, het miniatuurpad, de beschrijving van een inhoudsfragment en de datum waarop het is gemaakt.

Omdat metagegevens worden gegenereerd via de Schema-editor en als zodanig geen specifieke structuur hebben, `TypedMetaData` Het type GraphQL is geïmplementeerd om de metagegevens van een inhoudsfragment beschikbaar te maken. `TypedMetaData` stelt de informatie bloot die door de volgende scalaire types wordt gegroepeerd:

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

Als u bijvoorbeeld de titel van een inhoudsfragment wilt ophalen, weten we dat deze eigenschap een String-eigenschap is, zodat we een query voor alle String-metagegevens uitvoeren:

Ga als volgt te werk om te zoeken naar metagegevens:

```xml
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

U kunt alle types van meta-gegevensGrafiekQL bekijken als u het Gegenereerde schema GraphQL bekijkt. Alle modeltypen hebben dezelfde `TypedMetaData`.

>[!NOTE]
>
>**Verschil tussen normale metagegevens en arraymetagegevens**
>Houd er rekening mee dat `StringMetadata` en `StringArrayMetadata` beide verwijzen naar wat in de bewaarplaats wordt opgeslagen, niet hoe u hen terugwint.
>
>Bijvoorbeeld door de `stringMetadata` veld, ontvangt u een array van alle metagegevens die in de repository zijn opgeslagen als een `String` en als u `stringArrayMetadata` u ontvangt dan een array met alle metagegevens die in de repository zijn opgeslagen als `String[]`.

Zie [Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb).

#### Variaties {#variations}

De `_variations` is geïmplementeerd om het opvragen van variaties in een inhoudsfragment te vereenvoudigen. Bijvoorbeeld:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _variations
    }
  }
}
```

Zie [Voorbeeldquery - Alle steden met een benoemde variatie](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation).

>[!NOTE]
>
>Als de opgegeven variatie niet bestaat voor een inhoudsfragment, wordt de master variatie geretourneerd als standaard (fallback).

<!--
## Security Considerations {#security-considerations}
-->

## GrafiekQL-variabelen {#graphql-variables}

GraphQL laat variabelen toe om in de vraag worden geplaatst. Voor meer informatie kunt u de [GraphQL-documentatie voor variabelen](https://graphql.org/learn/queries/#variables).

Als u bijvoorbeeld alle inhoudsfragmenten van het type wilt ophalen `Article` die een specifieke variatie hebben, kunt u de variabele opgeven `variation` in GraphiQL.

![GrafiekQL-variabelen](assets/cfm-graphqlapi-03.png "GrafiekQL-variabelen")

```xml
### query
query GetArticlesByVariation($variation: String!) {
    articleList(variation: $variation) {
        items {
            _path
            author
        }
    }
}
 
### in query variables
{
    "variation": "uk"
}
```

## GraphQL-richtlijnen {#graphql-directives}

In GraphQL is er een mogelijkheid om de vraag te veranderen die op variabelen wordt gebaseerd, genoemd Richtlijnen GraphQL.

U kunt bijvoorbeeld de opdracht `adventurePrice` veld in een query voor alle `AdventureModels`, gebaseerd op een variabele `includePrice`.

![GraphQL-richtlijnen](assets/cfm-graphqlapi-04.png "GraphQL-richtlijnen")

```xml
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

U kunt het filtreren in uw vragen gebruiken GraphQL om specifieke gegevens terug te keren.

Bij het filteren wordt een syntaxis gebruikt die is gebaseerd op logische operatoren en expressies.

Met de volgende (basis)query worden bijvoorbeeld alle personen gefilterd die een naam hebben van `Jobs` of `Smith`:

```xml
query {
  personList(filter: {
    name: {
      _logOp: OR
      _expressions: [
        {
          value: "Jobs"
        },
        {
          value: "Smith"
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

Zie voor meer voorbeelden:

* nadere gegevens over de [GraphQL voor AEM extensies](#graphql-extensions)

* [Voorbeeldquery&#39;s met deze voorbeeldinhoud en -structuur](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

   * En de [Voorbeeldinhoud en -structuur](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql) voorbereid voor gebruik in voorbeeldquery&#39;s

* [Voorbeeldquery&#39;s op basis van het WKND-project](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## GraphQL voor AEM - Overzicht van extensies {#graphql-extensions}

De basisverrichting van vragen met GraphQL voor AEM houdt zich aan de standaardspecificatie GraphQL. Voor vragen GraphQL met AEM zijn er een paar uitbreidingen:

* Als u één resultaat nodig hebt:
   * de modelnaam gebruiken; Bijvoorbeeld stad

* Als u een lijst met resultaten verwacht:
   * toevoegen `List` de modelnaam; bijvoorbeeld:  `cityList`
   * Zie [Voorbeeldquery - Alle informatie over alle steden](#sample-all-information-all-cities)

* Als u logische OR wilt gebruiken:
   * use ` _logOp: OR`
   * Zie [Voorbeeldquery - Alle personen met de naam &quot;Jobs&quot; of &quot;Smith&quot;](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-all-persons-jobs-smith)

* Logische AND bestaat ook, maar is (vaak) impliciet

* U kunt zoeken naar veldnamen die overeenkomen met de velden in het model van het inhoudsfragment
   * Zie [Voorbeeldquery - Volledige details van de CEO en medewerkers van een bedrijf](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-full-details-company-ceos-employees)

* Naast de velden van uw model zijn er velden die door het systeem worden gegenereerd (voorafgegaan door een onderstrepingsteken):

   * Voor inhoud:

      * `_locale` : de taal te onthullen; gebaseerd op Taalbeheer
         * Zie [Voorbeeldquery voor meerdere inhoudsfragmenten van een bepaalde landinstelling](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-wknd-multiple-fragments-given-locale)
      * `_metadata` : om metagegevens voor uw fragment weer te geven
         * Zie [Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb)
      * `_model` : toestaan dat wordt gezocht naar een inhoudsfragmentmodel (pad en titel)
         * Zie [Voorbeeldquery voor een inhoudsfragmentmodel op basis van een model](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-wknd-content-fragment-model-from-model)
      * `_path` : het pad naar het inhoudsfragment in de repository
         * Zie [Voorbeeldquery - één specifiek stedenfragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)
      * `_reference` : verwijzingen zichtbaar te maken; inline-verwijzingen opnemen in de Rich Text Editor
         * Zie [Voorbeeldquery voor meerdere inhoudfragmenten met vooraf ingestelde verwijzingen](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-wknd-multiple-fragments-prefetched-references)
      * `_variation` : om specifieke variaties in het inhoudsfragment weer te geven

         >[!NOTE]
         >
         >Als de opgegeven variatie niet bestaat voor een inhoudsfragment, wordt de master variatie geretourneerd als standaard (fallback).

         * Zie [Voorbeeldquery - Alle steden met een benoemde variatie](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation)
   * En bewerkingen:

      * `_operator` : specifieke exploitanten toepassen; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`, `STARTS_WITH`
         * Zie [Voorbeeldquery - Alle personen die geen naam hebben van &quot;Taken&quot;](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-all-persons-not-jobs)
         * Zie [Voorbeeldquery - Alle avonturen waar de `_path` begint met een bepaald voorvoegsel](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-wknd-all-adventures-cycling-path-filter)
      * `_apply` : specifieke voorwaarden toe te passen; bijvoorbeeld:  `AT_LEAST_ONCE`
         * Zie [Voorbeeldquery - Filter op een array met een item dat minstens één keer moet voorkomen](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-array-item-occur-at-least-once)
      * `_ignoreCase` : om de zaak te negeren bij het vragen
         * Zie [Voorbeeldquery - Alle steden met SAN in naam, ongeacht het geval](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-all-cities-san-ignore-case)









* GraphQL-vaktypen worden ondersteund:

   * gebruiken `... on`
      * Zie [Voorbeeldquery voor een inhoudsfragment van een specifiek model met een inhoudsverwijzing](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-wknd-fragment-specific-model-content-reference)

* Extra fallback bij het opvragen van geneste fragmenten:

   * Als de gevraagde variatie niet bestaat in een genest fragment, wordt de **Master** variatie wordt geretourneerd.

## Blijvende query&#39;s (cache) {#persisted-queries-caching}

Na het voorbereiden van een vraag met een verzoek van de POST, kan het met een verzoek van de GET worden uitgevoerd dat door de geheime voorgeheugens van HTTP of een CDN kan worden in het voorgeheugen ondergebracht.

Dit wordt vereist aangezien de vragen van de POST gewoonlijk niet in het voorgeheugen ondergebracht zijn, en als het gebruiken van GET met de vraag als parameter er een significant risico is dat de parameter voor de diensten en tussenpersonen van HTTP te groot wordt.

De aanhoudende vragen moeten altijd het eindpunt met betrekking tot [geschikte configuratie Sites](#graphql-aem-endpoint); zodat ze beide of beide kunnen gebruiken:

* De globale configuratie en het eindpunt de vraag heeft toegang tot alle Modellen van het Fragment van de Inhoud.
* De specifieke configuratie(s) van Plaatsen en eindpunt(s) Creërend een persisted vraag voor een specifieke configuratie van Plaatsen vereist een overeenkomstig plaats-configuratie-specifiek eindpunt (om toegang tot de verwante Modellen van het Fragment van de Inhoud te verlenen).
Bijvoorbeeld, om een voortgeduurde vraag specifiek voor de configuratie van Plaatsen te creëren WKND, moet een overeenkomstige WKND-Specifieke configuratie van Plaatsen, en een WKND-Specifiek eindpunt vooraf worden gecreeerd.

>[!NOTE]
>
>Zie [Functionaliteit van inhoudsfragment inschakelen in configuratievenster](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) voor meer informatie .
>
>De **GraphQL-vragen over persistentie** moet worden toegelaten, voor de aangewezen configuratie van Plaatsen.

Als er bijvoorbeeld een bepaalde query wordt uitgevoerd, `my-query`, die een model gebruikt `my-model` vanuit de configuratie Sites `my-conf`:

* U kunt een query maken met de opdracht `my-conf` specifiek eindpunt, en dan zal de vraag als volgt worden bewaard:
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* U kunt dezelfde query maken met `global` eindpunt, maar dan zal de vraag als volgt worden bewaard:
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Dit zijn twee verschillende query&#39;s die zijn opgeslagen onder verschillende paden.
>
>Ze gebruiken gewoon hetzelfde model, maar via verschillende eindpunten.


Hier zijn de stappen die worden vereist om een bepaalde vraag voort te zetten:

1. Bereid de vraag door PUTing het aan het nieuwe eindpunt URL voor `/graphql/persist.json/<config>/<persisted-label>`.

   Maak bijvoorbeeld een doorlopende query:

   ```xml
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

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. U kunt de voortgezette vraag dan opnieuw spelen door URL te KRIJGEN `/graphql/execute.json/<shortPath>`.

   Gebruik bijvoorbeeld de voortgezette query:

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Werk een voortgezette vraag door POSTing aan een reeds bestaand vraagweg bij.

   Gebruik bijvoorbeeld de voortgezette query:

   ```xml
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

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Creeer een verpakte onbewerkte vraag met geheim voorgeheugencontrole.

   Bijvoorbeeld:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Maak een doorlopende query met parameters:

   Bijvoorbeeld:

   ```xml
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

1. Een query uitvoeren met parameters.

   Bijvoorbeeld:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

1. Als u de query wilt uitvoeren bij publiceren, moet de verwante boomstructuur worden gerepliceerd

   * Een POST voor replicatie gebruiken:

      ```xml
      $curl -X POST   http://localhost:4502/bin/replicate.json \
        -H 'authorization: Basic YWRtaW46YWRtaW4=' \
        -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
        -F cmd=activate
      ```

   * Een pakket gebruiken:
      1. Maak een nieuwe pakketdefinitie.
      1. De configuratie opnemen (bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries`).
      1. Maak het pakket.
      1. Herhaal het pakket.
   * Het replicatie-/distributiehulpmiddel gebruiken.
      1. Ga naar het gereedschap Distributie.
      1. Selecteer boomactivering voor de configuratie (bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries`).
   * Een workflow gebruiken (via workflowstartconfiguratie):
      1. Definieer een workflowstartregel voor het uitvoeren van een workflowmodel dat de configuratie van verschillende gebeurtenissen zou repliceren (bijvoorbeeld, maken, wijzigen, enz.).



1. Zodra de vraagconfiguratie is op publiceren, zijn de zelfde principes van toepassing, enkel gebruikend het publiceereindpunt.

   >[!NOTE]
   >
   >Voor anonieme toegang veronderstelt het systeem dat ACL &quot;iedereen&quot;toestaat om toegang tot de vraagconfiguratie te hebben.
   >
   >Als dat niet het geval is, zal het niet kunnen uitvoeren.

   >[!NOTE]
   >
   >Eventuele puntkomma&#39;s (&quot;;&quot;) in de URL&#39;s moeten worden gecodeerd.
   >
   >Bijvoorbeeld, zoals in het verzoek om een voortgezette vraag uit te voeren:
   >
   >
   ```xml
   >curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   >```

## Het vragen van het eindpunt GraphQL van een Externe Website {#query-graphql-endpoint-from-external-website}

Om tot het eindpunt GraphQL van een externe website toegang te hebben moet u vormen:

* [CORS-filter](#cors-filter)
* [Refererfilter](#referrer-filter)

### CORS-filter {#cors-filter}

>[!NOTE]
>
>Voor een gedetailleerd overzicht van het beleid voor het delen van bronnen in AEM zie [Werken met het delen van bronnen tussen verschillende bronnen (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html#understand-cross-origin-resource-sharing-(cors)).

Om tot het eindpunt toegang te hebben GraphQL, moet een beleid CORS in de bewaarplaats van de Kit van de klant worden gevormd. Dit wordt gedaan door een aangewezen OSGi CORS configuratiedossier voor het gewenste eindpunt (s) toe te voegen.

Deze configuratie moet een vertrouwde website-oorsprong opgeven `alloworigin` of `alloworiginregexp` waarvoor toegang moet worden verleend.

Bijvoorbeeld, om toegang tot het eindpunt te verlenen GraphQL en voortgeduurde vragen eindpunt voor `https://my.domain` u kunt gebruiken:

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

Als u een ijdelingspad voor het eindpunt hebt gevormd, kunt u het binnen ook gebruiken `allowedpaths`.

### Refererfilter {#referrer-filter}

Naast de configuratie CORS, moet een filter van de Referateur worden gevormd om toegang van derdeshosts toe te staan.

Dit wordt gedaan door een aangewezen OSGi de configuratiedossier van de Filter toe te voegen dat:

* geeft een hostnaam voor een vertrouwde website aan; ofwel `allow.hosts` of `allow.hosts.regexp`,
* verleent toegang voor deze gastheernaam.

Bijvoorbeeld om toegang voor verzoeken met de Referiteur te verlenen `my.domain` u kunt:

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
>Het blijft de verantwoordelijkheid van de klant om:
>
>* alleen toegang verlenen tot vertrouwde domeinen
>* ervoor zorgen geen gevoelige informatie wordt blootgesteld
>* geen jokerteken gebruiken [*] syntaxis; dit zal allebei voor authentiek verklaarde toegang tot het eindpunt van GraphQL onbruikbaar maken en zal het aan de volledige wereld ook blootstellen.


>[!CAUTION]
>
>Alle GraphQL [schema&#39;s](#schema-generation) (afgeleid van Content Fragment Models die **Ingeschakeld**) zijn leesbaar door het eindpunt GraphQL.
>
>Dit betekent dat u ervoor moet zorgen dat er geen gevoelige gegevens beschikbaar zijn, aangezien deze op deze manier kunnen worden gelekt; Dit omvat bijvoorbeeld informatie die als veldnamen in de modeldefinitie aanwezig kan zijn.

## Verificatie {#authentication}

Zie [Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten](/help/assets/content-fragments/graphql-authentication-content-fragments.md).

<!-- to be addressed later -->

<!--
## Sorting {#sorting}
-->

<!-- to be addressed later -->

<!--
## Paging {#paging}
-->

## Veelgestelde vragen {#faqs}

De gerezen vragen:

1. **Q**: &quot;*Hoe is GraphQL API voor AEM verschillend van de Bouwer API van de Vraag?*&quot;

   * **A**: &quot;*De AEM GraphQL API biedt volledige controle op de JSON-uitvoer en is een industriestandaard voor het opvragen van inhoud.
Als u verder gaat, is AEM van plan te investeren in de AEM GraphQL API.*&quot;

## Zelfstudie - Aan de slag met AEM headless and GraphQL {#tutorial}

Op zoek naar een praktische zelfstudie? Uitchecken [Aan de slag met AEM headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) end-to-end zelfstudie waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt samenstellen en beschikbaar maken met behulp van AEM GraphQL-API&#39;s en die door een externe toepassing wordt verbruikt.
