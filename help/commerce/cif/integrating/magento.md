---
title: AEM- en Adobe Commerce-integratie met behulp van Commerce Integration Framework
description: AEM en Adobe Commerce zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF biedt AEM toegang tot een Adobe Commerce-exemplaar en kan via GraphQL communiceren met Adobe Commerce. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om producten- en categoriegegevens op aanvraag van Adobe Commerce te doorzoeken. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
exl-id: f843784c-5ff7-41d1-97c5-13facb8459b2
source-git-commit: a5f3e33a6abe7ac1bbd610a8528fd599d1ffd2aa
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Integratie van AEM en Adobe Commerce (Magento) met gebruik van het Commerce Integration Framework {#aem-commerce-framework}

De Experience Manager en Adobe Commerce zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot de handelinstantie direct toegang te hebben en met Adobe Commerce te communiceren [GraphQL API&#39;s](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
>De minimaal ondersteunde GraphQL API-versie is 2.3.5. Bepaalde functies worden alleen ondersteund in nieuwere versies of alleen in de Adobe Commerce-editie.

## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![Overzicht van CIF-architectuur](../assets/AEM_Magento_Architecture.png)

Binnen CIF, is er steun voor server-kant en cliënt-zijcommunicatie patronen.
Server-kant APIs vraag wordt uitgevoerd gebruikend bouwstijl-binnen, generisch [GraphQL-client](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met een [reeks gegenereerde gegevensmodellen](https://github.com/adobe/commerce-cif-magento-graphql) voor de handel GraphQL schema. Daarnaast kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de client-side componenten, die bouwen met [Reageren](https://reactjs.org/)de [Apollo-client](https://www.apollographql.com/docs/react/) wordt gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) zeer gelijkaardige ontwerppatronen en beste praktijken volgen als [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components).

De bedrijfslogica en de achtergrondcommunicatie met Adobe Commerce voor de AEM CIF de Componenten van de Kern worden uitgevoerd in het Verdelen Modellen. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>De [Aanpassen AEM CIF Core-componenten](../customizing/customize-cif-components.md) Deze pagina bevat een gedetailleerd voorbeeld en aanbevolen methoden voor het aanpassen van CIF Core Components.

Binnen projecten, AEM de Componenten van de Kern van CIF en de componenten van het douaneproject kunnen de gevormde cliënt voor een opslag van Adobe Commerce gemakkelijk terugwinnen verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie.
