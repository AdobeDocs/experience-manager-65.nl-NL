---
title: AEM en Adobe Commerce Integration met Commerce integration framework
description: AEM en Adobe Commerce zijn naadloos geïntegreerd met behulp van het Commerce integration framework (CIF). CIF biedt AEM toegang tot een Adobe Commerce-exemplaar en communiceert met Adobe Commerce via GraphQL. Ook kunnen AEM auteurs product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Adobe Commerce worden opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
exl-id: f843784c-5ff7-41d1-97c5-13facb8459b2
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Integratie van AEM en Adobe Commerce (Magento) met Commerce integration framework {#aem-commerce-framework}

De Experience Manager en Adobe Commerce zijn naadloos geïntegreerd met het Commerce integration framework (CIF). CIF laat AEM toe om tot direct toegang te hebben en met de handelsinstantie te communiceren gebruikend Adobe Commerce [GraphQL API&#39;s](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
>De minimaal ondersteunde GraphQL API-versie is 2.3.5. Bepaalde functies worden alleen ondersteund in nieuwere versies of alleen in de Adobe Commerce-editie.

## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![Overzicht CIF architectuur](../assets/AEM_Magento_Architecture.png)

Binnen CIF, is er steun voor server-kant en cliënt-zijcommunicatie patronen.
Server-kant APIs vraag wordt uitgevoerd gebruikend bouwstijl-binnen, generisch [GraphQL-client](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met een [reeks gegenereerde gegevensmodellen](https://github.com/adobe/commerce-cif-magento-graphql) voor de handel GraphQL schema. Daarnaast kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de client-side componenten, die bouwen met [Reageren](https://reactjs.org/)de [Apollo-client](https://www.apollographql.com/docs/react/) wordt gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[CIF kerncomponenten AEM](https://github.com/adobe/aem-core-cif-components) zeer gelijkaardige ontwerppatronen en beste praktijken volgen als [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components).

De bedrijfslogica en de achtergrondcommunicatie met Adobe Commerce voor de AEM CIF Core Components wordt geïmplementeerd in Sling Models. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>De [Aanpassen AEM kerncomponenten](../customizing/customize-cif-components.md) Deze pagina bevat een gedetailleerd voorbeeld en aanbevolen methoden voor het aanpassen van CIF Core Components.

Binnen projecten, AEM CIF de Componenten van de Kern en de componenten van het douaneproject gemakkelijk de gevormde cliënt voor een opslag van Adobe Commerce verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie terugwinnen.
