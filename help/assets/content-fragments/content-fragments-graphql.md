---
title: Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL
description: Leer hoe u AEM Content Fragments met GraphQL kunt gebruiken voor het leveren van inhoud zonder kop.
feature: Content Fragments
role: User
exl-id: 2debd678-2d73-41f2-b33c-c29d661f6a6b
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Met Adobe Experience Manager (AEM) kunt u Content Fragments gebruiken, samen met de AEM GraphQL API (een aangepaste implementatie, gebaseerd op standaard GraphQL), om zonder problemen gestructureerde inhoud te leveren voor gebruik in uw toepassingen. Met de mogelijkheid om één API-query aan te passen kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

<!--
>[!NOTE]
>
>See [Headless and AEM](/help/implementing/developing/headless/introduction.md) for an introduction to Headless Development for AEM Sites.
-->

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM):
>
>* [AEM Commerce gebruikt gegevens van een handelsplatform via GraphQL](/help/commerce/cif/integrating/magento.md).
>* [AEM Content Fragments werken samen met de AEM GraphQL API (een aangepaste implementatie, gebaseerd op standaard GraphQL) om gestructureerde inhoud te leveren voor gebruik in uw toepassingen](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md).

## CMS zonder hoofd {#headless-cms}

Een CMS (Headless Content Management System) is:

* &quot;*Een headless-contentbeheersysteem, of CMS zonder kop, is een back-end alleen contentbeheersysteem (CMS) dat vanaf de basis is ontwikkeld als een opslagplaats voor inhoud die inhoud toegankelijk maakt via een API voor weergave op elk apparaat.*

  Zie [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

Wat het ontwerpen van inhoudsfragmenten in AEM betekent dit:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - Een overzicht {#graphql-overview}

GraphQL is:

* &quot;*...een querytaal voor API&#39;s en een runtime voor het uitvoeren van deze query&#39;s met uw bestaande gegevens.*&quot;.

  Zie [GraphQL.org](https://graphql.org)

De [GRAPHQL API AEM](#aem-graphql-api) laat u (complexe) vragen op uw uitvoeren [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md); met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## GRAPHQL API AEM {#aem-graphql-api}

Voor Adobe Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [GraphQL API AEM voor gebruik met inhoudsfragmenten](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) voor meer informatie.

De AEM GraphQL API-implementatie is gebaseerd op de [GraphQL Java-bibliotheken](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[Inhoudsfragmenten](#content-fragments) kan als basis voor GraphQL voor AEM vragen worden gebruikt als:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [Modellen van inhoudsfragmenten](#content-fragments-models) voorzien in de vereiste structuur door middel van gedefinieerde gegevenstypen.
* De [Fragmentverwijzing](#fragment-references), die beschikbaar zijn bij het definiëren van een model, kunnen worden gebruikt om extra structuurlagen te definiëren.

![Inhoudsfragmenten voor gebruik met GraphQL](assets/cfm-nested-01.png "Inhoudsfragmenten voor gebruik met GraphQL")

### Inhoudsfragmenten {#content-fragments}

Content Fragments:

* Bevat gestructureerde inhoud.

* Zij zijn gebaseerd op een [Inhoudsfragmentmodel](#content-fragments-models), waarin de structuur voor het resulterende fragment vooraf wordt gedefinieerd.

### Modellen van inhoudsfragmenten {#content-fragments-models}

Deze [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md):

* worden gebruikt om de [Schemas](https://graphql.org/learn/schema/), eenmaal **Ingeschakeld**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Fragmentverwijzingen](#fragment-references)** U kunt in uw model worden gebruikt om naar een ander inhoudsfragment te verwijzen en zo extra structuurniveaus te introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Fragmentverwijzing](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Is in samenwerking met GraphQL van bijzonder belang.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer gedefinieerd als een **multifeed** Er kan door het primaire fragment naar meerdere subfragmenten worden verwezen (opgehaald).

### JSON-voorvertoning {#json-preview}

Om u te helpen bij het ontwerpen en ontwikkelen van uw modellen van inhoudsfragmenten, kunt u een voorvertoning weergeven [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md).

## GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md) voor een inleiding op het gebruik van de AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM Headless en GraphQL

Op zoek naar een praktische zelfstudie? Uitchecken [Aan de slag met AEM Headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) end-to-end zelfstudie waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt ontwikkelen en beschikbaar maken met de GraphQL-API&#39;s van AEM en die door een externe toepassing wordt verbruikt.
