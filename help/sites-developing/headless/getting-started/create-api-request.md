---
title: Toegang tot en levering van contentfragmenten zonder kop Handleiding voor snel starten
description: Leer hoe u AEM Assets REST API kunt gebruiken voor het beheer van inhoudsfragmenten en de GraphQL API voor het zonder kop leveren van inhoud met fragmenten.
exl-id: 4664b3a4-4873-4f42-b59d-aadbfaa6072f
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# Toegang tot en levering van contentfragmenten zonder kop Handleiding voor snel starten {#accessing-delivering-content-fragments}

Leer hoe u AEM Assets REST API kunt gebruiken voor het beheer van inhoudsfragmenten en de GraphQL API voor de levering van inhoud zonder kop.

## Wat zijn GraphQL en Assets REST API&#39;s? {#what-are-the-apis}

[ nu dat u sommige inhoudsfragmenten hebt gecreeerd, ](create-content-fragment.md) kunt u AEM gebruiken APIs om hen zonder kop te leveren.

* [ GraphQL API ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) laat u verzoeken tot toegang tot en levering van de Fragmenten van de Inhoud tot stand brengen.
   * Om dit te gebruiken, [ eindpunten moeten worden bepaald en worden toegelaten in AEM ](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint), en indien nodig, geïnstalleerde [ interface GraphiQL ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#installing-graphiql-interface).
* [ Assets REST API ](/help/assets/assets-api-content-fragments.md) laat u tot stand brengen en wijzigen de Fragmenten van de Inhoud (en andere activa).

De rest van deze handleiding is gericht op GraphQL-toegang en levering van inhoudsfragmenten.

## Een inhoudsfragment afleveren met GraphQL {#how-to-deliver-a-content-fragment}

De architecten van de informatie moeten vragen voor hun kanaaleindpunten ontwerpen om inhoud te leveren. Denk slechts eens na deze vragen per eindpunt, per model. Voor deze gids Aan de slag kunt u slechts één gids maken.

1. Logboek in AEM en toegang tot de [ interface GraphiQL ](/help/sites-developing/headless/graphql-api/graphiql-ide.md):
   * Bijvoorbeeld: `http://<host>:<port>/aem/graphiql.html` .

1. GraphiQL is een in-browser vraagredacteur voor GraphQL. U kunt het gebruiken om vragen te bouwen om de Fragmenten van de Inhoud terug te winnen om hen onophoudelijk als JSON te leveren.
   * In het linkerdeelvenster kunt u een query maken.
   * De resultaten worden weergegeven in het rechterdeelvenster.
   * De vraagredacteur kenmerkt codevoltooiing en hotkeys om de vraag gemakkelijk uit te voeren.

     ![ GraphiQL redacteur ](assets/graphiql.png)

1. Ervan uitgaande dat het model dat u hebt gemaakt `person` is aangeroepen met velden `firstName` , `lastName` en `position` , kunt u een eenvoudige query maken om de inhoud van het inhoudsfragment op te halen.

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
<!--
   ![GraphiQL query](assets/graphiql-query.png)
-->

1. Klik het **Uitvoeren pictogram van de Vraag** (juiste pijl) of gebruik `Ctrl-Enter` hotkey en de resultaten worden getoond als JSON in het juiste paneel.
   ![ GraphiQL resultaten ](assets/graphiql-results.png)

1. Klik:
   * **Dokken** bij het hoogste recht van de pagina om in-context documentatie te tonen om u te helpen uw vragen bouwen die aan uw eigen modellen aanpassen.
   * **Geschiedenis** in de hoogste toolbar om vorige vragen te tonen.
   * **sparen als** en **sparen** om uw vragen te bewaren, waarna u hen van het **Persisted paneel van Vragen** en **Publish** kunt een lijst maken en terugwinnen.

     ![ documentatie GraphiQL ](assets/graphiql-documentation.png)

GraphQL laat gestructureerde vragen toe die niet alleen specifieke gegevensreeksen of individuele gegevensvoorwerpen kunnen richten, maar ook specifieke elementen van de voorwerpen, genestelde resultaten, biedt steun voor vraagvariabelen, en veel meer kunnen leveren.

GraphQL kan herhalende API-aanvragen en overlevering voorkomen. In plaats daarvan is het mogelijk om in grote hoeveelheden te leveren wat precies nodig is voor rendering als reactie op één API-query. De resulterende JSON kan worden gebruikt om gegevens te leveren aan andere sites of apps.

## Volgende stappen {#next-steps}

Dat is het! U hebt nu een basiskennis van beheer van inhoud zonder kop in AEM. Er zijn veel meer bronnen waar u dieper kunt duiken voor een volledig begrip van de beschikbare functies.

* **[Browser van de Configuratie](create-configuration.md)** - voor details over Browser van de Configuratie AEM
* **[Fragmenten van de Inhoud](/help/assets/content-fragments/content-fragments.md)** - voor details over het creëren van en het beheren van de Fragmenten van de Inhoud
* **[GrahiQL winde](/help/sites-developing/headless/graphql-api/graphiql-ide.md)** voor verdere details van het gebruiken van IDE GraphiQL
* **[Blijven Vragen](/help/sites-developing/headless/graphql-api/persisted-queries.md)** voor verdere details van Gepersisteerde Vragen
* **[de Steun van de Fragmenten van de Inhoud in HTTP API van AEM Assets](/help/assets/assets-api-content-fragments.md)** - voor details bij de toegang tot van AEM inhoud direct over HTTP API, via de verrichtingen van CRUD (creeer, las, Update, schrap)
* **[GraphQL API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)** - voor details op hoe te om de Fragmenten van de Inhoud zonder kop te leveren
