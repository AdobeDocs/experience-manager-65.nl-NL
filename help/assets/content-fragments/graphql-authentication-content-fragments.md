---
title: Verificatie voor externe AEM GraphQL-query's op inhoudsfragmenten
description: Begrijp de authentificatie die voor Verre AEM vragen GraphQL wordt vereist om uw inhoud zonder kop te beveiligen.
feature: Content Fragments,GraphQL API
source-git-commit: 2f647fc640d3809dc684bce397831ab37fb94b07
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Een primair gebruiksgeval voor [Adobe Experience Manager (AEM) GraphQL API voor de Levering van het Fragment van de Inhoud](/help/assets/content-fragments/graphql-api-content-fragments.md) moet verre vragen van derdetoepassingen of de diensten goedkeuren. Deze externe query&#39;s vereisen mogelijk geverifieerde API-toegang om de levering van inhoud zonder kop te beveiligen.

>[!NOTE]
>
>Voor het testen en de ontwikkeling kunt u tot de AEM API ook direct toegang hebben GraphQL gebruikend [GraphiQL interface](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) interface.

Voor authentificatie moet de derdedienst [een Token van de Toegang terugwinnen](#retrieving-access-token), die dan [in het Vraag GraphQL](#use-access-token-in-graphql-request) kan worden gebruikt.

## Een toegangstoken ophalen {#retrieving-access-token}

<!-- 6.5.10.0 - does this page need to be migrated? -->

<!--
See [Generating Access Tokens for Server Side APIs](/help/sites-developing/generating-access-tokens-for-server-side-apis.md) for full details.
-->

## Het gebruiken van het Token van de Toegang in een Vraag GraphQL {#use-access-token-in-graphql-request}

Voor een derdedienst om met een AEM instantie te verbinden moet het *Token van de Toegang* hebben. De dienst moet dit teken aan `Authorization` kopbal op het verzoek van de POST dan toevoegen.

Bijvoorbeeld een GraphQL-autorisatieheader:

```xml
Authorization: Bearer <access_token>
```

## Machtigingsvereisten {#permission-requirements}

Alle verzoeken die worden gedaan gebruikend het toegangstoken zullen *eigenlijk door de gebruikersrekening worden gemaakt die het token* produceerde.

Dit betekent dat u moet controleren dat de rekening de toestemmingen heeft die worden vereist om vragen in werking te stellen GraphQL.

U kunt dit controleren door GraphiQL op de lokale instantie te gebruiken.
