---
title: Hoofdletters en headless in AEM
description: AEM-projecten kunnen worden geïmplementeerd in een krachtig model zonder kop, maar de keuze is niet binair. AEM biedt de flexibiliteit om de voordelen van beide modellen in één project te benutten.
exl-id: c9597c78-be05-42ff-84fe-f7451119e83d
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Hoofdletters en headless in AEM {#headful-headless}

Adobe Experience Manager-projecten kunnen worden geïmplementeerd in zowel headful als headless modellen, maar de keuze is niet binair. AEM biedt de flexibiliteit om de voordelen van beide modellen in één project te benutten. Dit document verstrekt een overzicht van de verschillende modellen en beschrijft de niveaus van de integratie van het KUUROORD.

## Overzicht {#overview}

AEM biedt krachtige tools voor het beheer van zowel het maken van content als de levering ervan in één platform. Dit is een traditioneel &#39;krachtig&#39; model van contentbeheer, waarbij de auteurs en ontwikkelaars van inhoud op hetzelfde platform werken om de ervaringen aan de gebruikers van de inhoud te leveren.

AEM kan ook worden gebruikt om inhoud eenvoudig te beheren, zodat presentatie en levering van de inhoud door een ander platform kunnen worden beheerd. Dit is het &#39;headless&#39;-model van contentbeheer, waarbij de auteurs en ontwikkelaars van inhoud op verschillende platforms werken om de gebruikers van inhoud ervaring te bieden.

Maar dit hoeft geen binaire keuze te zijn. AEM biedt een ongekende flexibiliteit, zodat u de voordelen van beide modellen voor uw project kunt benutten.

![ Modellen van de Implementatie van AEM ](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

In een krachtig of volledig-stapelmodel, wordt de inhoud beheerd in de bewaarplaats van AEM en de componenten van AEM die op Java, HTML worden gebaseerd, etc., worden gebruikt om de inhoud voor de gebruikerservaring terug te geven. In dit model gebeurt het maken van de inhoud, het vormgeven, het presenteren en leveren ervan allemaal in AEM.

In een headless-model wordt de inhoud beheerd in de AEM-opslagplaats, maar via API&#39;s zoals REST en GraphQL geleverd aan een ander systeem om de inhoud voor de gebruikerservaring te renderen. In dit model wordt inhoud gemaakt in AEM, maar de opmaak, presentatie en levering gebeuren allemaal op een ander platform.

Toepassingen van één pagina (SPAs) zijn vaak de bestemming voor inhoud die zonder kop door AEM wordt geleverd. Nochtans, te hoeven deze SPAs niet volledig extern aan AEM te zijn. Met AEM kunt u bepalen in welke mate uw SPA&#39;s in AEM zijn geïntegreerd. Laten we een voorbeeld nemen.

## Voorbeeld van webwinkel {#web-shop-example}

Laten wij zeggen dat u een bestaande Webshop voor uw bedrijf als KUUROORD hebt. Hierin staan al uw productdetails en afbeeldingen. Vervolgens introduceert u AEM om uw marketingactiviteiten, zoals promotiesites, blogs en inhoud van campagnes, kracht bij te zetten. Hoe integreer je deze twee? AEM biedt verschillende opties:

* **sta de systemen toe om onafhankelijk te werken.**
* **leverde de Webshop met beperkte inhoud van AEM via GraphQL.** Inhoud kan door auteurs in AEM worden gemaakt, maar kan alleen via de webshop SPA worden bekeken.
* **bedt WebshopSPA in AEM in.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM worden weergegeven in de context van de webshop, maar kan niet worden gemanipuleerd.
* **bedt WebshopSPA in AEM in, en laat editable punten toe.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM worden weergegeven in de context van de webshop. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA in AEM te manipuleren.
* **bed Webs shopSPA in AEM in, en laat volledige streken voor het uitgeven toe.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM worden weergegeven in de context van de webshop. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA in AEM te manipuleren.

In de volgende sectie worden deze integratieniveaus nader beschreven.

>[!NOTE]
>
>Natuurlijk kon u WebshopSPA als volledig-functionerende AEM SPA [ ook re-uitvoeren gebruikend het kader van de Redacteur van AEM SPA.](/help/sites-developing/spa-walkthrough.md) Als u AEM al hebt en een webshop of andere SPA wilt maken, is dit de aanbevolen methode, maar is deze buiten het bereik van dit document.

## SPA-integratieniveaus {#integration-levels}

De integratie van SPA&#39;s valt op een spectrum van vier niveaus in AEM.

* **Niveau 0: Geen integratie**
   * De SBZ en AEM bestaan afzonderlijk en wisselen geen informatie uit.
   * Inhoud wordt in twee aparte systemen gemaakt, beheerd en afzonderlijk geleverd.
* **Niveau 1: De integratie van het fragmentintegratie van de inhoud**
   * [ de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om beperkte inhoud voor het KUUUROORD tot stand te brengen en te beheren.
   * SPA wint deze inhoud via AEM [ GraphQL API terug.](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)
   * Sommige inhoud wordt beheerd in AEM en andere in een extern systeem.
   * De inhoud kan slechts in SPA worden bekeken.
* **Niveau 2: Sluit het KUUROORD in AEM** in
   * [ de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om inhoud voor het KUUROORD tot stand te brengen en te beheren.
   * SPA wint deze inhoud via AEM [ GraphQL API terug.](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)
   * Sommige inhoud wordt beheerd in AEM en andere in een extern systeem.
   * Inhoud kan in AEM in context worden weergegeven.
   * Beperkte inhoud kan in AEM worden bewerkt.
* **Niveau 3: Sluit en laat volledig SPA in AEM** in
   * [ de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om inhoud voor het KUUROORD tot stand te brengen en te beheren.
   * SPA wint deze inhoud via AEM [ GraphQL API terug.](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)
   * Inhoud kan in AEM in context worden weergegeven.
   * De meeste inhoud kan in AEM worden bewerkt.

Niveau 1 is een voorbeeld van een typische implementatie zonder kop. Nochtans kunnen de inhoudsauteurs hun inhoud binnen context binnen het KUUROORD slechts bekijken. AEM is slechts een ontwerpgereedschap.

Het voordeel en de flexibiliteit van AEM worden duidelijk met niveaus 2 en 3 terwijl het behouden van de voordelen van SPAs. Inhoudsauteurs kunnen hun inhoud maken in AEM, maar zien deze ook in context in AEM. Het KUUROORD krijgt de capaciteit om in AEM worden authored, maar nog als KUUROORD worden geleverd.

## Implementatie van de integratieniveaus {#implementing}

Er zijn verschillende gereedschappen beschikbaar in AEM, afhankelijk van het integratieniveau dat u kiest. Elk niveau bouwt op de hulpmiddelen voort die in het vorige worden gebruikt. De volgende lijst verwijst naar de relevante bronnen.

* **Niveau 1:** de Fragmenten van de Inhoud en [ het hoofd van AEM kader ](/help/sites-developing/headless/introduction.md) kunnen worden gebruikt om de inhoud van AEM aan het KUUROORD te leveren.
* **Niveau 2:** naast niveau één:
   * [ de component RemotePage ](/help/sites-developing/spa-remote-page.md) kan worden gebruikt om het externe KUUROORD in AEM in te bedden waar de inhoud van AEM in-context kan worden bekeken.
   * Bepaalde punten op het KUUROORD kunnen ook worden toegelaten om [ beperkt het uitgeven in AEM toe te staan.](/help/sites-developing/spa-edit-external.md)
* **Niveau 3:** naast niveau twee:
   * De volledige streken van het KUUROORD kunnen worden toegelaten om het uitvoerige uitgeven in AEM toe te staan.
