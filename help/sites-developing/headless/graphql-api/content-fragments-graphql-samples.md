---
title: GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query's
description: Leer hoe u GraphQL met AEM kunt gebruiken om inhoud zonder problemen te bedienen door voorbeeldinhoud en query's te verkennen.
feature: Content Fragments,GraphQL API
exl-id: 91c5f61c-9c15-4d72-9b9b-0c23f31e7cdc
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 0%

---

# GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Leer hoe u GraphQL met AEM kunt gebruiken om inhoud zonder problemen te bedienen door voorbeeldinhoud en query&#39;s te verkennen.

>[!NOTE]
>
>Deze pagina moet samen met:
>
>* [Contentfragmenten](/help/assets/content-fragments/content-fragments.md)
>* [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
>* [GraphQL API AEM voor gebruik met inhoudsfragmenten](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)

Om aan de slag te gaan met GraphQL query&#39;s en hoe ze werken met AEM Content Fragments, is het nuttig om enkele praktische voorbeelden te zien.

Zie voor hulp bij dit:

* A [voorbeeldstructuur van inhoudsfragment](#content-fragment-structure-graphql)

* En sommige [voorbeeld GraphQL-vragen](#graphql-sample-queries), op basis van de fragmentstructuur van de voorbeeldinhoud (Content Fragment Models and related Content Fragments).


## GraphQL - Voorbeeldquery&#39;s met de structuur van het voorbeeldinhoudsfragment {#graphql-sample-queries-sample-content-fragment-structure}

Zie deze steekproefvragen voor illustraties van creeer vragen, samen met steekproefresultaten.

>[!NOTE]
>
>Afhankelijk van uw instantie kunt u rechtstreeks toegang krijgen tot [GraphiQL-interface inbegrepen bij AEM GraphQL API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphiql-interface) voor het indienen van en het testen van vragen.
>
>Bijvoorbeeld: `http://localhost:4502/content/graphiql.html`

>[!NOTE]
>
>De steekproefvragen zijn gebaseerd op [Voorbeeldstructuur van inhoudsfragment voor gebruik met GraphQL](#content-fragment-structure-graphql)

### Voorbeeldquery - Alle beschikbare schema&#39;s en datatypen {#sample-all-schemes-datatypes}

Deze voorbeeldquery retourneert alles `types` voor alle beschikbare schema&#39;s.

**Voorbeeldquery**

```graphql
{
  __schema {
    types {
      name
      description
    }
  }
}
```

**Voorbeeldresultaat**

```json
{
  "data": {
    "__schema": {
      "types": [
        {
          "name": "AdventureModel",
          "description": null
        },
        {
          "name": "AdventureModelArrayFilter",
          "description": null
        },
        {
          "name": "AdventureModelFilter",
          "description": null
        },
        {
          "name": "AdventureModelResult",
          "description": null
        },
        {
          "name": "AdventureModelResults",
          "description": null
        },
        {
          "name": "AllFragmentModels",
          "description": null
        },
        {
          "name": "ArchiveRef",
          "description": null
        },
        {
          "name": "ArrayMode",
          "description": null
        },
        {
          "name": "ArticleModel",
          "description": null
        },

...more results...

        {
          "name": "__EnumValue",
          "description": null
        },
        {
          "name": "__Field",
          "description": null
        },
        {
          "name": "__InputValue",
          "description": null
        },
        {
          "name": "__Schema",
          "description": "A GraphQL Introspection defines the capabilities of a GraphQL server. It exposes all available types and directives on the server, the entry points for query, mutation, and subscription operations."
        },
        {
          "name": "__Type",
          "description": null
        },
        {
          "name": "__TypeKind",
          "description": "An enum describing what kind of type a given __Type is"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle informatie over alle steden {#sample-all-information-all-cities}

Om alle informatie over alle steden terug te winnen, kunt u de basisvraag gebruiken:
**Voorbeeldquery**

```graphql
{
  cityList {
    items
  }
}
```

Bij uitvoering wordt de query automatisch uitgebreid met alle velden:

```graphql
{
  cityList {
    items {
      _path
      name
      country
      population
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/basel",
          "name": "Basel",
          "country": "Switzerland",
          "population": 172258
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/bucharest",
          "name": "Bucharest",
          "country": "Romania",
          "population": 1821000
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-francisco",
          "name": "San Francisco",
          "country": "USA",
          "population": 883306
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-jose",
          "name": "San Jose",
          "country": "USA",
          "population": 1026350
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/stuttgart",
          "name": "Stuttgart",
          "country": "Germany",
          "population": 634830
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/zurich",
          "name": "Zurich",
          "country": "Switzerland",
          "population": 415367
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Namen van alle steden {#sample-names-all-cities}

Deze voorbeeldquery is een eenvoudige query om de query te retourneren `name`van alle vermeldingen in de `city`schema.

**Voorbeeldquery**

```xmgraphqll
query {
  cityList {
    items {
      name
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Basel"
        },
        {
          "name": "Berlin"
        },
        {
          "name": "Bucharest"
        },
        {
          "name": "San Francisco"
        },
        {
          "name": "San Jose"
        },
        {
          "name": "Stuttgart"
        },
        {
          "name": "Zurich"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - één specifiek stedenfragment {#sample-single-specific-city-fragment}

Deze voorbeeldquery is een query om de details van één fragmentitem te retourneren op een specifieke locatie in de opslagplaats.

**Voorbeeldquery**

```graphql
{
  cityByPath (_path: "/content/dam/sample-content-fragments/cities/berlin") {
    item {
      _path
      name
      country
      population
     categories
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityByPath": {
      "item": {
        "_path": "/content/dam/sample-content-fragments/cities/berlin",
        "name": "Berlin",
        "country": "Germany",
        "population": 3669491,
        "categories": [
          "city:capital",
          "city:emea"
        ]
      }
    }
  }
}
```

### Voorbeeldquery - Alle steden met een benoemde variatie {#sample-cities-named-variation}

Als u een variatie maakt met de naam &quot;Berlin Center&quot; (`berlin_centre`) voor de `city` Berlijn, kunt u een vraag gebruiken om details van de variatie terug te keren.

**Voorbeeldquery**

```graphql
{
  cityList (variation: "berlin_center") {
    items {
      _path
      name
      country
      population
      categories
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491,
          "categories": [
            "city:capital",
            "city:emea"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Namen van alle steden die zijn getagd als stadseinden {#sample-names-all-cities-tagged-city-breaks}

Als u:

* verschillende tags maken, met de naam `Tourism` : `Business`, `City Break`, `Holiday`
* en wijs deze markeringen aan de Hoofdvariatie van diverse toe `City` instances

Dan kunt u een vraag gebruiken om details van terug te keren `name` en `tags`van alle items die zijn getagd als Stadseinden in het dialoogvenster `city`schema.

**Voorbeeldquery**

```graphql
query {
  cityList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "tourism:city-break", _operator: CONTAINS}]}}
  ){
    items {
      name,
      _tags
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Berlin",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        },
        {
          "name": "Zurich",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Volledige details van de CEO en medewerkers van een bedrijf {#sample-full-details-company-ceos-employees}

Gebruikend de structuur van de genestelde fragmenten, keert deze vraag de volledige details van CEO van een bedrijf en al zijn werknemers terug.

**Voorbeeldquery**

```graphql
query {
  companyList {
    items {
      name
      ceo {
        _path
        name
        firstName
        awards {
        id
          title
        }
      }
      employees {
       name
        firstName
       awards {
         id
          title
        }
      }
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Apple Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Marsh",
              "firstName": "Duke",
              "awards": []
            },
            {
              "name": "Caulfield",
              "firstName": "Max",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                }
              ]
            }
          ]
        },
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/adam-smith",
            "name": "Smith",
            "firstName": "Adam",
            "awards": []
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        },
        {
          "name": "NextStep Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe",
              "awards": []
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham",
              "awards": []
            }
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle personen met de naam &quot;Jobs&quot; of &quot;Smith&quot; {#sample-all-persons-jobs-smith}

Deze voorbeeldquery filtert alle `persons` voor alle bestanden met de naam `Jobs`of `Smith`.

**Voorbeeldquery**

```graphql
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

**Voorbeeldresultaten**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Jobs",
          "firstName": "Steve"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle personen die geen naam hebben van &quot;Taken&quot; {#sample-all-persons-not-jobs}

Deze voorbeeldquery filtert alle `persons` voor alle bestanden met de naam `Jobs`of `Smith`.

**Voorbeeldquery**

```graphql
query {
  personList(filter: {
    name: {
      _expressions: [
        {
          value: "Jobs"
          _operator: EQUALS_NOT
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

**Voorbeeldresultaten**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Lincoln",
          "firstName": "Abraham"
        },
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Slade",
          "firstName": "Cutter"
        },
        {
          "name": "Marsh",
          "firstName": "Duke"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Croft",
          "firstName": "Lara"
        },
        {
          "name": "Caulfield",
          "firstName": "Max"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle avonturen waarvan `_path` begint met een bepaald voorvoegsel {#sample-wknd-all-adventures-cycling-path-filter}

Alles `adventures` waar `_path` begint met een bepaald voorvoegsel (`/content/dam/wknd/en/adventures/cycling`).

**Voorbeeldquery**

```graphql
query {
  adventureList(
    filter: {
      _path: {
        _expressions: [
        {
          value: "/content/dam/wknd/en/adventures/cycling"
         _operator: STARTS_WITH
        }]
       }
    })
    {
    items {
      _path
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-southern-utah/cycling-southern-utah"
        },
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-tuscany/cycling-tuscany"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle steden in Duitsland of Zwitserland met een bevolking van 400000 tot en met 999999 {#sample-all-cities-d-ch-population}

Hier wordt een combinatie van velden gefilterd. An `AND` (impliciet) wordt gebruikt om `population`bereik, terwijl een `OR` (expliciet) wordt gebruikt om de vereiste steden te selecteren.

**Voorbeeldquery**

```graphql
query {
  cityList(filter: {
    population: {
      _expressions: [
        {
          value: 400000
          _operator: GREATER_EQUAL
        }, {
          value: 1000000
          _operator: LOWER
        }
      ]
    },
    country: {
      _logOp: OR
      _expressions: [
        {
          value: "Germany"
        }, {
          value: "Switzerland"
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Stuttgart",
          "population": 634830,
          "country": "Germany"
        },
        {
          "name": "Zurich",
          "population": 415367,
          "country": "Switzerland"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle steden met SAN in naam, ongeacht het geval {#sample-all-cities-san-ignore-case}

Deze vraag ondervraagt voor alle steden die `SAN` in de naam, ongeacht het geval.

**Voorbeeldquery**

```graphql
query {
  cityList(filter: {
    name: {
      _expressions: [
        {
          value: "SAN"
          _operator: CONTAINS
          _ignoreCase: true
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA"
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Filter op een array met een item dat minstens één keer moet voorkomen {#sample-array-item-occur-at-least-once}

Deze query filtert op een array met een item (`city:na`) die ten minste één keer moet plaatsvinden.

**Voorbeeldquery**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          value: "city:na"
          _apply: AT_LEAST_ONCE
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA",
          "categories": [
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Filter op een exacte arraywaarde {#sample-array-exact-value}

Deze query filtert op een exacte arraywaarde.

**Voorbeeldquery**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          values: [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery voor geneste inhoudsfragmenten - Alle bedrijven met ten minste één werknemer met de naam &quot;Smith&quot; {#sample-companies-employee-smith}

Deze query illustreert het filteren van alle `person` van `name` &quot;Smith&quot;, die informatie van over twee geneste fragmenten terugkeert - `company` en `employee`.

**Voorbeeldquery**

```graphql
query {
  companyList(filter: {
    employees: {
      _match: {
        name: {
          _expressions: [
            {
              value: "Smith"
            }
          ]
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
      }
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "NextStep Inc.",
          "ceo": {
            "name": "Jobs",
            "firstName": "Steve"
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe"
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham"
            }
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery voor geneste inhoudsfragmenten - Alle bedrijven waar alle werknemers de &quot;Gamestar&quot;-prijs hebben gewonnen {#sample-all-companies-employee-gamestar-award}

Deze query illustreert het filteren van drie geneste fragmenten - `company`, `employee`, en `award`.

**Voorbeeldquery**

```graphql
query {
  companyList(filter: {
    employees: {
      _apply: ALL
      _match: {
        awards: {
          _match: {
            id: {
              _expressions: [
                {
                  value: "GS"
                  _operator:EQUALS
                }
              ]
            }
          }
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
        awards {
          id
          title
        }
      }
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "name": "Smith",
            "firstName": "Adam"
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB {#sample-metadata-awards-gb}

Deze query illustreert het filteren van drie geneste fragmenten - `company`, `employee`, en `award`.

**Voorbeeldquery**

```graphql
query {
  awardList(filter: {
      id: {
        _expressions: [
          {
            value:"GB"
          }
        ]
    }
  }) {
    items {
      _metadata {
        stringMetadata {
          name,
          value
        }
      }
      id
      title
    }
  }
}
```

**Voorbeeldresultaten**

```json
{
  "data": {
    "awardList": {
      "items": [
        {
          "_metadata": {
            "stringMetadata": [
              {
                "name": "title",
                "value": "Gameblitz Award"
              },
              {
                "name": "description",
                "value": ""
              }
            ]
          },
          "id": "GB",
          "title": "Gameblitz"
        }
      ]
    }
  }
}
```

## Voorbeeldquery&#39;s met het WKND-project {#sample-queries-using-wknd-project}

Deze steekproefvragen zijn gebaseerd op het project WKND. Het heeft het volgende:

* Modellen voor inhoudsfragmenten zijn beschikbaar onder:
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhoudsfragmenten (en andere inhoud) beschikbaar onder:
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`

>[!NOTE]
>
>Aangezien de resultaten extensief kunnen zijn, worden ze hier niet weergegeven.

### Voorbeeldquery voor alle inhoudsfragmenten van een bepaald model met de opgegeven eigenschappen {#sample-wknd-all-model-properties}

Met deze voorbeeldquery wordt het volgende gevraagd:

* voor alle inhoudfragmenten van het type `article`
* met de `path`en `author` eigenschappen.

**Voorbeeldquery**

```graphql
{
  articleList {
    items {
      _path
      author
    }
  }
}
```

### Voorbeeldquery voor metagegevens {#sample-wknd-metadata}

Deze query vraagt om:

* voor alle inhoudfragmenten van het type `adventure`
* metagegevens

**Voorbeeldquery**

```graphql
{
  adventureList {
    items {
      _path,
      _metadata {
        stringMetadata {
          name,
          value
        }
        stringArrayMetadata {
          name,
          value
        }
        intMetadata {
          name,
          value
        }
        intArrayMetadata {
          name,
          value
        }
        floatMetadata {
          name,
          value
        }
        floatArrayMetadata {
          name,
          value
        }
        booleanMetadata {
          name,
          value
        }
        booleanArrayMetadata {
          name,
          value
        }
        calendarMetadata {
          name,
          value
        }
        calendarArrayMetadata {
          name,
          value
        }
      }
    }
  }
}
```

### Voorbeeldquery voor één inhoudsfragment van een bepaald model {#sample-wknd-single-content-fragment-of-given-model}

Met deze voorbeeldquery wordt het volgende gevraagd:

* voor één inhoudsfragment van type `article` op een bepaald pad
   * in dat pad, alle indelingen van inhoud:
      * HTML
      * Markering
      * Onbewerkte tekst
      * JSON

**Voorbeeldquery**

```graphql
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures") {
    item {
        _path
        author
        main {
          html
          markdown
          plaintext
          json
        }
    }
  }
}
```

### Voorbeeldquery voor een inhoudsfragmentmodel op basis van een model {#sample-wknd-content-fragment-model-from-model}

Met deze voorbeeldquery wordt het volgende gevraagd:

* voor één inhoudsfragment
   * details van het onderliggende inhoudsfragmentmodel

**Voorbeeldquery**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd/en/adventures/riverside-camping-australia/riverside-camping-australia") {
    item {
      _path
      adventureTitle
      _model {
        _path
        title
      }
    }
  }
}
```

### Voorbeeldquery voor een geneste inhoudsfragment - Type model{#sample-wknd-nested-fragment-single-model}

Deze query vraagt om:

* voor één inhoudsfragment van type `article` op een bepaald pad
   * binnen dat pad, het pad en de auteur van het fragment waarnaar wordt verwezen (genest)

>[!NOTE]
>
>Het veld `referencearticle` heeft het gegevenstype Data `fragment-reference`.

**Voorbeeldquery**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### Voorbeeldquery voor een geneste inhoudsfragment - Meerdere modeltypen{#sample-wknd-nested-fragment-multiple-model}

#### Type model waarnaar wordt verwezen

Deze query vraagt om:

* voor meerdere inhoudsfragmenten van het type `bookmark`
   * met fragmentverwijzingen naar andere fragmenten van het specifieke modeltype `Article`

>[!NOTE]
>
>Het veld `fragments` heeft het gegevenstype Data `fragment-reference`, met het model `Article` geselecteerd. Query levert `fragments` als een array van `[Article]`.

```graphql
{
  bookmarkList {
    items {
        fragments {
          _path
          author
        }
     }
  }
}
```

#### Meerdere modeltypen waarnaar wordt verwezen

Deze query vraagt om:

* voor meerdere inhoudsfragmenten van het type `bookmark`
   * met fragmentverwijzingen naar andere fragmenten van de specifieke modeltypen `Article` en `Adventure`

>[!NOTE]
>
>Het veld `fragments` heeft het gegevenstype Data `fragment-reference`met de modellen `Article`, `Adventure` geselecteerd. Query levert `fragments` als een array van `[AllFragmentModels]`, die wordt afgeweken van het type union.

```graphql
{
  bookmarkList {
    items {
        fragments {
          ... on ArticleModel {
            _path
            author
          }
          ... on AdventureModel {
            _path
            adventureTitle
          }
        }
     }
  }
}
```

### Voorbeeldquery voor een inhoudsfragment van een specifiek model met inhoudsverwijzingen{#sample-wknd-fragment-specific-model-content-reference}

Deze query heeft twee voordelen:

1. Alle inhoudsverwijzingen retourneren.
1. De specifieke inhoudsverwijzingen van het type retourneren `attachments`.

Deze vragen worden ondervraagd:

* voor meerdere inhoudsfragmenten van het type `bookmark`
   * met Content Reference to other fragments

#### Voorbeeldquery voor meerdere inhoudfragmenten met vooraf ingestelde verwijzingen {#sample-wknd-multiple-fragments-prefetched-references}

De volgende vraag keert alle inhoudsverwijzingen terug door te gebruiken `_references`:

```graphql
{
  bookmarkList {
     _references {
         ... on ImageRef {
          _path
          type
          height
        }
        ... on MultimediaRef {
          _path
          type
          size
        }
        ... on DocumentRef {
          _path
          type
          author
        }
        ... on ArchiveRef {
          _path
          type
          format
        }
    }
    items {
        _path
    }
  }
}
```

#### Voorbeeldquery voor meerdere inhoudsfragmenten met bijlagen {#sample-wknd-multiple-fragments-attachments}

De volgende query retourneert alle `attachments` - een specifiek veld (subgroep) van het type `content-reference`:

>[!NOTE]
>
>Het veld `attachments` heeft het gegevenstype Data `content-reference`, waarbij verschillende formulieren zijn geselecteerd.

```graphql
{
  bookmarkList {
    items {
      attachments {
        ... on PageRef {
          _path
          type
        }
        ... on ImageRef {
          _path
          width
        }
        ... on MultimediaRef {
          _path
          size
        }
        ... on DocumentRef {
          _path
          author
        }
        ... on ArchiveRef {
          _path
          format
        }
      }
    }
  }
}
```

### Voorbeeldquery voor één inhoudsfragment met RTE Inline-verwijzing {#sample-wknd-single-fragment-rte-inline-reference}

Deze query vraagt om:

* voor één inhoudsfragment van type `bookmark` op een bepaald pad
   * binnen dat, de gealigneerde verwijzingen van RTE

>[!NOTE]
>
>De RTE gealigneerde verwijzingen worden gehydrateerd binnen `_references`.

**Voorbeeldquery**

```graphql
{
  bookmarkByPath(_path: "/content/dam/wknd/en/bookmarks/skitouring") {
    item {
      _path
      description {
        json
      }
    }
    _references {
      ... on ArticleModel {
        _path
      }
      ... on AdventureModel {
        _path
      }
      ... on ImageRef {
        _path
      }
      ... on MultimediaRef {
        _path
      }
      ... on DocumentRef {
        _path
      }
      ... on ArchiveRef {
        _path
      }
    }
  }
}
```

### Voorbeeldquery voor één variatie van inhoudsfragment van een bepaald model {#sample-wknd-single-fragment-given-model}

Deze query vraagt om:

* voor één inhoudsfragment van type `article` op een bepaald pad
   * binnen dat pad de gegevens met betrekking tot de variatie: `variation1`

**Voorbeeldquery**

```graphql
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures", variation: "variation1") {
    item {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Voorbeeldquery voor een benoemde variatie van meerdere inhoudsfragmenten van een bepaald model {#sample-wknd-variation-multiple-fragment-given-model}

Deze query vraagt om:

* voor inhoudfragmenten van het type `article` met een specifieke variatie: `variation1`

**Voorbeeldquery**

```graphql
{
  articleList (variation: "variation1") {
    items {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Voorbeeldquery voor meerdere inhoudsfragmenten en de bijbehorende variaties van een bepaald model {#sample-wknd-multiple-fragment-variations-given-model}

Deze query vraagt om:

* voor inhoudfragmenten van het type `article` en alle variaties

**Voorbeeldquery**

```graphql
query {
  articleList(
    includeVariations: true  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Voorbeeldquery voor variaties van inhoudsfragmenten van een bepaald model waaraan een specifieke tag is gekoppeld{#sample-wknd-fragment-variations-given-model-specific-tag}

Deze query vraagt om:

* voor inhoudfragmenten van het type `article` met een of meer variaties met de tag `WKND : Activity / Hiking`

**Voorbeeldquery**

```graphql
{
  articleList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "wknd:activity/hiking", _operator: CONTAINS}]}}
  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Voorbeeldquery voor meerdere inhoudsfragmenten van een bepaalde landinstelling {#sample-wknd-multiple-fragments-given-locale}

Deze query vraagt om:

* voor inhoudfragmenten van het type `article` binnen de `fr` landinstelling

**Voorbeeldquery**

```graphql
{ 
  articleList (_locale: "fr") {
    items {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

## De structuur voor het voorbeeldinhoudfragment (wordt gebruikt met GraphQL) {#content-fragment-structure-graphql}

De steekproefvragen zijn gebaseerd op de volgende structuur, die gebruikt:

* één of meer, [Voorbeeld van fragmentmodellen van inhoud](#sample-content-fragment-models-schemas) - de basis vormen voor de GraphQL-regeling

* [Voorbeeldinhoudsfragmenten](#sample-content-fragments) op basis van bovenstaande modellen

### Voorbeeld van modellen van inhoudsfragmenten (schema&#39;s) {#sample-content-fragment-models-schemas}

Voor de steekproefvragen, gebruik de volgende Modellen van Inhoud en hun onderlinge verhoudingen (verwijzingen ->):

* [Bedrijf](#model-company)
-> [Persoon](#model-person)
    -> [Uitreiking](#model-award)

* [Plaats](#model-city)

#### Bedrijf {#model-company}

De basisvelden voor het bedrijf zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Bedrijfsnaam | Tekst met één regel | |
| CEO | Fragmentverwijzing (enkele) | [Persoon](#model-person) |
| Werknemers | Fragmentverwijzing (meerdere velden) | [Persoon](#model-person) |

#### Persoon {#model-person}

De velden waarin een persoon wordt gedefinieerd, die ook een werknemer kan zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Naam | Tekst met één regel | |
| Voornaam | Tekst met één regel | |
| Uitreiking | Fragmentverwijzing (meerdere velden) | [Uitreiking](#model-award) |

#### Uitreiking {#model-award}

De velden waarin een onderscheiding wordt gedefinieerd, zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Sneltoets/id | Tekst met één regel | |
| Titel | Tekst met één regel | |

#### Plaats {#model-city}

De velden voor het definiëren van een stad zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Naam | Tekst met één regel | |
| Land | Tekst met één regel | |
| Bevolking | Getal | |
| Categorieën | Tags | |

### Voorbeeldinhoudsfragmenten {#sample-content-fragments}

De volgende fragmenten worden gebruikt voor het juiste model.

#### Bedrijf {#fragment-company}

| Bedrijfsnaam | CEO | Werknemers |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh<br>Max Caulfield |
|  Little Pony Inc. | Adam Smith | Lara Croft<br>Trekslade |
| NextStep Inc. | Steve Jobs | Joe Smith<br>Abe Lincoln |

#### Persoon {#fragment-person}

| Naam | Voornaam | Uitreiking |
|--- |--- |--- |
| Lincoln |  Abe | |
| Smith | Adam |   |
| Slade |  Tussenruimte |  Gameblitz<br>Gamestar |
| Marsh |  Duke |   |   |
|  Smith |  Joe |   |
| Uitsnijden |  Lara | Gamestar |
| Caulfield |  Max |  Gameblitz |
|  Taken |  Steve |   |

#### Uitreiking {#fragment-award}

| Sneltoets/id | Titel |
|--- |--- |
| GB | Gameblitz |
|  GS | Gamestar |
|  OSC | Oscar |

#### Plaats {#fragment-city}

| Naam | Land | Bevolking | Categorieën |
|--- |--- |--- |--- |
| Bazel | Zwitserland | 172258 | stad:emea |
| Berlin | Duitsland | 3669491 | stad:hoofdstad<br>stad:emea |
| Boekarest | Roemenië | 1821000 |  stad:hoofdstad<br>stad:emea |
| San Francisco |  VS |  883306 |  stad:strand<br>plaats:na |
| San Jose |  VS |  102635 |  plaats:na |
| Stuttgart |  Duitsland |  634830 |  stad:emea |
|  Zurich |  Zwitserland |  415367 |  stad:hoofdstad<br>stad:emea |
