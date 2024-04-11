---
title: Hoofdletters en headless in AEM
description: AEM projecten kunnen worden geïmplementeerd in een krachtig en zonder kop, maar de keuze is niet binair. AEM biedt de flexibiliteit om de voordelen van beide modellen in één project te benutten.
exl-id: c9597c78-be05-42ff-84fe-f7451119e83d
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Hoofdletters en headless in AEM {#headful-headless}

Adobe Experience Manager-projecten kunnen worden geïmplementeerd in zowel headful als headless modellen, maar de keuze is niet binair. AEM biedt de flexibiliteit om de voordelen van beide modellen in één project te benutten. Dit document biedt een overzicht van de verschillende modellen en beschrijft de niveaus van SPA integratie.

## Overzicht {#overview}

AEM biedt krachtige tools om zowel de creatie van inhoud als de levering ervan in één platform te beheren. Dit is een traditioneel &#39;krachtig&#39; model van contentbeheer, waarbij de auteurs en ontwikkelaars van inhoud op hetzelfde platform werken om de ervaringen aan de gebruikers van de inhoud te leveren.

AEM kan ook worden gebruikt om inhoud eenvoudig te beheren, zodat de presentatie en levering van de inhoud door een ander platform kunnen worden beheerd. Dit is het &#39;headless&#39;-model van contentbeheer, waarbij de auteurs en ontwikkelaars van inhoud op verschillende platforms werken om de gebruikers van inhoud ervaring te bieden.

Maar dit hoeft geen binaire keuze te zijn. AEM biedt ongekende flexibiliteit, die u toestaat om de voordelen van beide modellen voor uw project te exploiteren.

![Implementatiemodellen AEM](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

In een krachtig of volledig-stapelmodel, wordt de inhoud beheerd in de AEM bewaarplaats en AEM componenten die op Java, HTML worden gebaseerd, etc., worden gebruikt om de inhoud voor de gebruikerservaring terug te geven. In dit model gebeurt het maken van de inhoud, het vormgeven, het presenteren en het leveren ervan allemaal in AEM.

In een headless model, wordt de inhoud beheerd in de AEM bewaarplaats, maar geleverd via APIs zoals REST en GraphQL aan een ander systeem om de inhoud voor de gebruikerservaring terug te geven. In dit model wordt inhoud gemaakt in AEM, maar wordt de inhoud vormgegeven, gepresenteerd en geleverd op een ander platform.

Toepassingen op één pagina (SPA) zijn vaak de bestemming voor inhoud die zonder kop door AEM wordt geleverd. Deze SPA hoeven echter niet geheel buiten de AEM te liggen. AEM kunt u bepalen in welke mate uw SPA in AEM wordt geïntegreerd. Laten we een voorbeeld nemen.

## Voorbeeld van webwinkel {#web-shop-example}

Laten we zeggen dat u een bestaande webshop hebt voor uw bedrijf als SPA. Hierin staan al uw productdetails en afbeeldingen. Vervolgens introduceert u AEM om uw marketingactiviteiten, zoals promotiesites, blogs en inhoud van campagnes, kracht bij te zetten. Hoe integreer je deze twee? AEM maakt een spectrum van opties mogelijk:

* **De systemen onafhankelijk laten werken.**
* **Bied de webshop met beperkte inhoud van AEM via GraphQL.** Inhoud kan door auteurs in AEM worden gemaakt, maar kan alleen via de SPA van de webshop worden bekeken.
* **Sluit de SPA van de webshop in AEM in.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de webshop worden weergegeven, maar niet worden gemanipuleerd.
* **Sluit de SPA van de webshop in AEM in en schakel bewerkbare punten in.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de context van de webshop worden weergegeven. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA binnen AEM te manipuleren.
* **Sluit de webwinkel in AEM in en schakel volledige zones in voor bewerking.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de context van de webshop worden weergegeven. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA binnen AEM te manipuleren.

In de volgende sectie worden deze integratieniveaus nader beschreven.

>[!NOTE]
>
>Natuurlijk kunt u de SPA van de webshop ook opnieuw implementeren als een volledig functionerende AEM SPA [het AEM SPA Editor-framework gebruiken.](/help/sites-developing/spa-walkthrough.md) Als u al een webshop of andere SPA hebt AEM en wilt maken, is dit de aanbevolen methode, maar is deze buiten het bereik van dit document.

## SPA integratieniveaus {#integration-levels}

SPA integratie ligt op een spectrum van vier niveaus in AEM.

* **Niveau 0: geen integratie**
   * De SPA en AEM bestaan afzonderlijk en wisselen geen informatie uit.
   * Inhoud wordt in twee aparte systemen gemaakt, beheerd en afzonderlijk geleverd.
* **Niveau 1: integratie van inhoudsfragmenten**
   * [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om beperkte inhoud voor de SPA te maken en te beheren.
   * De SPA haalt deze inhoud op via AEM [GraphQL API.](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)
   * Sommige inhoud wordt beheerd in AEM en sommige in een extern systeem.
   * Inhoud kan alleen in de SPA worden weergegeven.
* **Niveau 2: sluit de SPA in AEM in**
   * [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om inhoud voor de SPA te maken en te beheren.
   * De SPA haalt deze inhoud op via AEM [GraphQL API.](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)
   * Sommige inhoud wordt beheerd in AEM en sommige in een extern systeem.
   * Inhoud kan binnen AEM in context worden weergegeven.
   * Beperkte inhoud kan binnen AEM worden bewerkt.
* **Niveau 3: SPA insluiten en volledig inschakelen in AEM**
   * [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om inhoud voor de SPA te maken en te beheren.
   * De SPA haalt deze inhoud op via AEM [GraphQL API.](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)
   * Inhoud kan binnen AEM in context worden weergegeven.
   * De meeste inhoud kan worden bewerkt in AEM.

Niveau 1 is een voorbeeld van een typische implementatie zonder kop. Inhoudsauteurs kunnen hun inhoud echter alleen in-context binnen de SPA bekijken. AEM is slechts een ontwerpgereedschap.

Het voordeel en de flexibiliteit van AEM worden duidelijk met niveaus 2 en 3, terwijl de voordelen van SPA behouden blijven. Inhoudsauteurs kunnen hun inhoud in AEM maken, maar zien deze ook in context binnen AEM. De SPA krijgt het vermogen om in AEM te worden ontworpen, maar nog als SPA worden geleverd.

## Implementatie van de integratieniveaus {#implementing}

Er zijn verschillende gereedschappen in AEM beschikbaar, afhankelijk van het integratieniveau dat u kiest. Elk niveau bouwt op de hulpmiddelen voort die in het vorige worden gebruikt. De volgende lijst verwijst naar de relevante bronnen.

* **Niveau 1:** Inhoudsfragmenten en de [AEM kader zonder kop](/help/sites-developing/headless/introduction.md) kan worden gebruikt om AEM inhoud aan de SPA te leveren.
* **Niveau 2:** Naast niveau 1:
   * [De component RemotePage](/help/sites-developing/spa-remote-page.md) kan worden gebruikt om de externe SPA in te sluiten in AEM waar AEM inhoud in context kan worden bekeken.
   * Bepaalde punten op de SPA kunnen ook worden ingeschakeld op [beperkte bewerking in AEM toestaan.](/help/sites-developing/spa-edit-external.md)
* **Niveau 3:** Naast niveau 2:
   * Volledige zones van de SPA kunnen worden ingeschakeld om uitgebreide bewerkingen in AEM toe te staan.
