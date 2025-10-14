---
title: AEM en Adobe Commerce Integration met Commerce integration framework
description: AEM en Adobe Commerce zijn naadloos geïntegreerd met behulp van het Commerce integration framework (CIF). CIF biedt AEM toegang tot een Adobe Commerce-exemplaar en communiceert met Adobe Commerce via GraphQL. Ook kunnen AEM auteurs product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Adobe Commerce worden opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
exl-id: f843784c-5ff7-41d1-97c5-13facb8459b2
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Integratie van AEM en Adobe Commerce (Magento) met Commerce integration framework {#aem-commerce-framework}

De Experience Manager en Adobe Commerce zijn naadloos geïntegreerd met het Commerce integration framework (CIF). CIF laat AEM toe om tot direct toegang te hebben en met de handelsinstantie te communiceren gebruikend Adobe Commerce [&#x200B; GraphQL APIs &#x200B;](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
>De minimaal ondersteunde GraphQL API-versie is 2.3.5. Bepaalde functies worden alleen ondersteund in nieuwere versies of alleen in de Adobe Commerce-editie.

## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![&#x200B; CIF het Overzicht van de Architectuur &#x200B;](../assets/AEM_Magento_Architecture.png)

Binnen CIF, is er steun voor server-kant en cliënt-zijcommunicatie patronen.
De server-kant APIs vraag wordt uitgevoerd gebruikend de bouwstijl-binnen, generische [&#x200B; cliënt van GraphQL &#x200B;](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met a [&#x200B; reeks geproduceerde gegevensmodellen &#x200B;](https://github.com/adobe/commerce-cif-magento-graphql) voor het schema van handelsGraphQL. Daarnaast kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de cliënt-zijcomponenten, die gebruikend [&#x200B; React &#x200B;](https://reactjs.org/) bouwen, wordt de [&#x200B; Cliënt van Apollo &#x200B;](https://www.apollographql.com/docs/react/) gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![&#x200B; AEM CIF de Architectuur van de Component van de Kern &#x200B;](../assets/cif-component-architecture.jpg)

[&#x200B; AEM CIF de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-core-cif-components) volgen zeer gelijkaardige ontwerppatronen en beste praktijken zoals [&#x200B; AEM de Componenten van de Kern WCM &#x200B;](https://github.com/adobe/aem-core-wcm-components).

De bedrijfslogica en de achtergrondcommunicatie met Adobe Commerce voor de AEM CIF Core Components wordt geïmplementeerd in Sling Models. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>[&#x200B; het Aanpassen AEM CIF de pagina van de Componenten van de Kern &#x200B;](../customizing/customize-cif-components.md) heeft een gedetailleerd voorbeeld en beste praktijken op hoe te om CIF Componenten van de Kern aan te passen.

Binnen projecten, AEM CIF de Componenten van de Kern en de componenten van het douaneproject gemakkelijk de gevormde cliënt voor een opslag van Adobe Commerce verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie terugwinnen.
