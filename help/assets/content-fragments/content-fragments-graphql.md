---
title: Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL
description: Leer hoe u AEM GraphQL inhoudsfragmenten met kunt gebruiken voor het leveren van inhoud zonder kop.
feature: Content Fragments,Headless,GraphQL
role: User,Developer
exl-id: 2debd678-2d73-41f2-b33c-c29d661f6a6b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
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
>* [&#x200B; AEM Commerce verbruikt gegevens van een handelsplatform via GraphQL &#x200B;](/help/commerce/cif/integrating/magento.md).
>* [&#x200B; AEM de Fragmenten van de Inhoud werken samen met AEM GraphQL API (een aangepaste implementatie, die op standaardGraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen &#x200B;](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) te leveren.

## CMS zonder hoofd {#headless-cms}

Een CMS (Headless Content Management System) is:

* &quot;*A headless inhoudsbeheersysteem, of hoofd CMS, is een achterste enkel inhoudsbeheersysteem (CMS) dat van de grond omhoog als inhoudsbewaarplaats wordt gebouwd die inhoud toegankelijk door middel van API voor vertoning op om het even welk apparaat maakt.*

  Zie [&#x200B; Wikipedia &#x200B;](https://en.wikipedia.org/wiki/Headless_content_management_system).

Wat het ontwerpen van inhoudsfragmenten in AEM betekent dit:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - Een overzicht {#graphql-overview}

GraphQL is:

* &quot;*...een vraagtaal voor APIs en runtime voor het vervullen van die vragen met uw bestaande gegevens.*&quot;.

  Zie [&#x200B; GraphQL.org &#x200B;](https://graphql.org)

[&#x200B; AEM GraphQL API &#x200B;](#aem-graphql-api) laat u (complexe) vragen op uw [&#x200B; Fragmenten van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments.md) uitvoeren; met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## GRAPHQL API AEM {#aem-graphql-api}

Voor Adobe Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [&#x200B; AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud &#x200B;](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) voor details.

De AEM implementatie van GraphQL API is gebaseerd op de [&#x200B; bibliotheken van GraphQL Java &#x200B;](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[&#x200B; de Fragmenten van de Inhoud &#x200B;](#content-fragments) kunnen als basis voor GraphQL voor AEM vragen als worden gebruikt:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [&#x200B; Modellen van het Fragment van de Inhoud &#x200B;](#content-fragments-models) verstrekken de vereiste structuur door middel van bepaalde gegevenstypes.
* De [&#x200B; Verwijzing van het Fragment &#x200B;](#fragment-references), beschikbaar wanneer het bepalen van een model, kan worden gebruikt om extra lagen van structuur te bepalen.

![&#x200B; de Fragmenten van de Inhoud voor gebruik met de Fragmenten van de Inhoud van GraphQL &#x200B;](assets/cfm-nested-01.png " voor gebruik met GraphQL ")

### Inhoudsfragmenten {#content-fragments}

Content Fragments:

* Bevat gestructureerde inhoud.

* Zij zijn gebaseerd op het Model van het Fragment van de a [&#x200B; Inhoud &#x200B;](#content-fragments-models), dat de structuur voor het resulterende fragment vooraf bepaalt.

### Modellen van inhoudsfragmenten {#content-fragments-models}

Deze [&#x200B; Modellen van het Fragment van Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-models.md):

* Wordt gebruikt om de [&#x200B; Schema&#39;s &#x200B;](https://graphql.org/learn/schema/) te produceren, eens **Toegelaten**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Verwijzingen van het Fragment](#fragment-references)** kan in uw model worden gebruikt om een ander Fragment van de Inhoud van verwijzingen te voorzien, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Verwijzing van het Fragment](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Is in samenwerking met GraphQL van bijzonder belang.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer bepaald als a **multifeed**, kunnen de veelvoudige sub-fragmenten (teruggewonnen) door het eerste fragment van verwijzingen worden voorzien.

### JSON-voorvertoning {#json-preview}

Om met het ontwerpen van en het ontwikkelen van uw Modellen van het Fragment van de Inhoud te helpen, kunt u voorproef [&#x200B; output JSON &#x200B;](/help/assets/content-fragments/content-fragments-json-preview.md).

## GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [&#x200B; Lerend om GraphQL met AEM te gebruiken - de Inhoud en Vragen van de Steekproef &#x200B;](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md) voor een inleiding aan het gebruiken van AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM Headless en GraphQL

Op zoek naar een praktische zelfstudie? Controle uit [&#x200B; Begonnen het Worden met AEM Zwaartepunt en GraphQL &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=nl-NL) leerprogramma van begin tot eind illustrerend hoe te om inhoud op te bouwen en bloot te stellen gebruikend GraphQL APIs van AEM en verbruikt door een externe app, in een hoofdCMS scenario.
