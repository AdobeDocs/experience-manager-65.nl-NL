---
title: Toegang tot en levering van contentfragmenten zonder kop Handleiding voor snel starten
description: Leer hoe u AEM Assets REST API kunt gebruiken voor het beheer van inhoudsfragmenten en de GraphQL API voor de levering van inhoud zonder kop.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
source-git-commit: 8ab774b8d21dd16e4873cd39ef0175ead3f2da23
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Toegang tot en levering van contentfragmenten zonder kop Handleiding voor snel starten {#accessing-delivering-content-fragments}

Leer hoe u AEM Assets REST API kunt gebruiken voor het beheer van inhoudsfragmenten en de GraphQL API voor de levering van inhoud zonder kop.

## Wat zijn GraphQL- en Assets REST-API&#39;s? {#what-are-the-apis}

[Nu u enkele inhoudsfragmenten hebt gemaakt,](create-content-fragment.md) u kunt AEM API&#39;s gebruiken om ze zonder kop te leveren.

* [De GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md) staat u toe om verzoeken tot toegang te creëren en inhoudsfragmenten te leveren.
   * Om dit te gebruiken, moeten de eindpunten in AEM worden bepaald en worden toegelaten, en indien vereist, geïnstalleerde interface GraphiQL.
* [De REST-API voor middelen](/help/assets/assets-api-content-fragments.md) Hiermee kunt u inhoudsfragmenten (en andere elementen) maken en wijzigen.

De rest van deze gids zal zich op toegang GraphQL en de levering van het Fragment van de Inhoud concentreren.

## Hoe te om een tevreden Fragment te leveren dat GraphQL gebruikt {#how-to-deliver-a-content-fragment}

De architecten van de informatie zullen vragen voor hun kanaaleindpunten moeten ontwerpen om inhoud te leveren. Deze vragen zullen over het algemeen slechts eens per eindpunt per model moeten worden overwogen. Met het oog op deze gids om aan de slag te gaan, zullen wij slechts één gids moeten creëren.

1. Logboek in AEM en toegang tot de interface GraphiQL:
   * Bijvoorbeeld: `https://<host>:<port>/content/graphiql.html`.

1. GraphiQL is een in-browser vraagredacteur voor GraphQL. U kunt het gebruiken om vragen te bouwen om de Fragmenten van de Inhoud terug te winnen om hen hoofdelijk als JSON te leveren.
   * In het linkerdeelvenster kunt u een query maken.
   * De resultaten worden weergegeven in het rechterdeelvenster.
   * De vraagredacteur kenmerkt codevoltooiing en hotkeys om de vraag gemakkelijk uit te voeren.
      ![GraphiQL-editor](../assets/graphiql.png)

1. Ervan uitgaande dat het model dat we hebben gemaakt, werd aangeroepen `person` met velden `firstName`, `lastName`, en `position`, kunnen wij een eenvoudige vraag bouwen om de inhoud van ons Inhoudsfragment terug te winnen.

   ```text
   query 
   {
     personList {
       items {
         _path
         firstName
         lastName
         position
       }
     }
   }
   ```

1. Voer de query in het linkerdeelvenster in.
   ![GraphiQL-query](../assets/graphiql-query.png)

1. Klik op de knop **Query uitvoeren** of de knop `Ctrl-Enter` en de resultaten worden als JSON weergegeven in het rechterdeelvenster.
   ![GraphiQL-resultaten](../assets/graphiql-results.png)

1. Klik op:
   * **Docs** rechtsboven op de pagina om in-context documentatie te tonen waarmee u query&#39;s kunt maken die u kunt aanpassen aan uw eigen modellen.
   * **Historie** in de bovenste werkbalk om vorige query&#39;s weer te geven.
      ![GraphiQL-documentatie](../assets/graphiql-documentation.png)

GraphQL laat gestructureerde vragen toe die niet alleen specifieke gegevensreeksen of individuele gegevensvoorwerpen kunnen richten, maar ook specifieke elementen van de voorwerpen, genestelde resultaten kunnen leveren, biedt steun voor vraagvariabelen, en veel meer.

GraphQL kan iteratieve API-verzoeken en overlevering vermijden en maakt in plaats daarvan bulklevering mogelijk van exact wat nodig is voor rendering als reactie op één API-query. De resulterende JSON kan worden gebruikt om gegevens te leveren aan andere sites of apps.

## Volgende stappen {#next-steps}

Dat is het! U hebt nu een basiskennis van beheer van inhoud zonder kop in AEM. Natuurlijk zijn er veel meer middelen waar u zich verdiept voor een uitgebreid inzicht in de beschikbare functies.

* **[Configuratiebrowser](create-configuration.md)** - Voor meer informatie over de AEM Configuration Browser
* **[Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)** - Meer informatie over het maken en beheren van inhoudsfragmenten
* **[Ondersteuning voor inhoudsfragmenten in AEM Assets HTTP API](/help/assets/assets-api-content-fragments.md)** - Voor meer informatie over het rechtstreeks benaderen van AEM inhoud via de HTTP-API, via CRUD-bewerkingen (Maken, Lezen, Bijwerken, Verwijderen)
* **[GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)** - Voor meer informatie over hoe u inhoudsfragmenten zonder problemen kunt leveren
