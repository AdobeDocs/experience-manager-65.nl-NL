---
title: Aflevering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL
description: Leer hoe te om AEM Inhoudsfragmenten met GraphQL voor hoofdloze inhoudslevering te gebruiken.
feature: Content Fragments
role: User
source-git-commit: 819df6d6123575b378676dda200064725de47b84
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Aflevering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Met Adobe Experience Manager (AEM), kunt u de Fragments van de Inhoud, samen met de AEM GraphQL API (een aangepaste implementatie, die op standaard GraphQL wordt gebaseerd) gebruiken, zonder problemen gestructureerde inhoud voor gebruik in uw toepassingen leveren. Dankzij de mogelijkheid om één API-query aan te passen, kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

<!--
>[!NOTE]
>
>See [Headless and AEM](/help/implementing/developing/headless/introduction.md) for an introduction to Headless Development for AEM Sites.
-->

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM):
>
>* [AEM de Handel verbruikt gegevens van een handelsplatform via GraphQL](/help/commerce/cif/integrating/magento.md).
>* [AEM Inhoudsfragmenten werken samen met de AEM GraphQL API (een aangepaste implementatie op basis van standaard GraphQL) voor gestructureerde inhoud voor gebruik in uw toepassingen](/help/assets/content-fragments/graphql-api-content-fragments.md).


## CMS zonder hoofd {#headless-cms}

Een CMS (Headless Content Management System) is:

* &quot;*Een systeem voor inhoudsbeheer zonder kop, of CMS zonder kop, is een back-end alleen inhoudsbeheersysteem (CMS) dat vanaf de basis is opgebouwd als een inhoudsopslagplaats die inhoud toegankelijk maakt via een API voor weergave op elk apparaat.*

   Zie [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

Wat het ontwerpen van inhoudsfragmenten in AEM betekent dit:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - een overzicht {#graphql-overview}

GraphQL is:

* &quot;*..een vraagtaal voor APIs en runtime voor het vervullen van die vragen met uw bestaande gegevens.*&quot;.

   Zie [GraphQL.org](https://graphql.org)

Met de [AEM GraphQL API](#aem-graphql-api) kunt u (complexe) query&#39;s uitvoeren op uw [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md); met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## AEM GraphQL API {#aem-graphql-api}

Voor Adobe Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [AEM GraphQL API voor gebruik met Content Fragments](/help/assets/content-fragments/graphql-api-content-fragments.md) voor details.

De implementatie van AEM GraphQL API is gebaseerd op de [GraphQL Java-bibliotheken](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[Inhoud ](#content-fragments) Fragmenteren kan als basis voor GraphQL voor AEM vragen worden gebruikt als:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [Content Fragment Models](#content-fragments-models) bieden de vereiste structuur door middel van gedefinieerde gegevenstypen.
* De [Fragmentverwijzing](#fragment-references), die beschikbaar is wanneer u een model definieert, kan worden gebruikt om extra structuurlagen te definiëren.

![Inhoudsfragmenten voor gebruik met ](assets/cfm-nested-01.png "GraphQLContent-fragmenten voor gebruik met GraphQL")

### Contentfragmenten {#content-fragments}

Contentfragmenten:

* Bevat gestructureerde inhoud.

* Ze zijn gebaseerd op een [Inhoudsfragmentmodel](#content-fragments-models), dat de structuur voor het resulterende fragment vooraf definieert.

### Modellen van contentfragmenten {#content-fragments-models}

Deze [Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md):

* Wordt gebruikt om [Schemas](https://graphql.org/learn/schema/), eens **Enabled** te produceren.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Fragmentverwijzingen](#fragment-references)** kan in uw model worden gebruikt om naar een ander Inhoudsfragment te verwijzen, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Fragmentverwijzing](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Is van bijzonder belang in samenhang met GraphQL.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer gedefinieerd als een **multifeed**, kunnen meerdere subfragmenten door het prime-fragment naar verwezen (opgehaald) worden.

### JSON-voorvertoning {#json-preview}

Om u te helpen bij het ontwerpen en ontwikkelen van uw modellen van inhoudsfragmenten, kunt u een voorvertoning van [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md) weergeven.

## Leren gebruiken GraphQL met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [Leren om GraphQL met AEM te gebruiken - de Inhoud van de Steekproef en Vragen](/help/assets/content-fragments/content-fragments-graphql-samples.md) voor een inleiding aan het gebruiken van AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM headless and GraphQL

Op zoek naar een praktische zelfstudie? Ontdek [Aan de slag met AEM Headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) de zelfstudie van begin tot eind waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt ontwikkelen en beschikbaar maken met de GraphQL-API&#39;s van AEM en die door een externe toepassing wordt verbruikt.
