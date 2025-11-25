---
title: Meer informatie over inhoud zonder kop en hoe u deze vertaalt in AEM
description: Ontdek headless-concepten, hoe ze in kaart brengen naar AEM, en de theorie van de AEM-vertaling.
exl-id: cb2e2d89-e2d2-462f-8fff-b201847d0641
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Developer, User, Leader
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Meer informatie over inhoud zonder kop en hoe u deze vertaalt in AEM {#learn-about}

Ontdek headless-concepten, hoe ze in kaart brengen naar AEM, en de theorie van de AEM-vertaling.

## Doelstelling {#objective}

Met dit document krijgt u inzicht in de inhoud zonder kop, hoe AEM koploze inhoud ondersteunt en hoe dergelijke inhoud kan worden vertaald. Na het lezen moet u:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Wees vertrouwd met de manier waarop AEM ondersteuning biedt voor headless en translatie.

## Volledige levering van inhoud {#full-stack}

Sinds de opkomst van gebruiksvriendelijke, grootschalige contentbeheersystemen (CMS&#39;s) hebben organisaties deze als centrale locatie gebruikt voor het beheer van berichten, branding en communicatie. Het gebruik van de CMS als centraal punt voor het beheer van ervaringen heeft geleid tot een verbeterde efficiëntie doordat het niet nodig is taken in verschillende systemen te dupliceren.

![ de klassieke volledig-stapel CMS ](/help/journey-headless/developer/assets/full-stack.png)

In een CMS met volledige stapel bevindt alle functionaliteit voor het manipuleren van inhoud zich in de CMS. De functies van het systeem bestaan uit verschillende onderdelen van de CMS-stapel. De full-stack oplossing heeft veel voordelen.

* Er is één systeem om te onderhouden.
* Inhoud wordt centraal beheerd.
* Alle diensten van het systeem zijn geïntegreerd.
* Inhoud schrijven is naadloos.

Als dus een nieuw kanaal moet worden toegevoegd of ondersteuning voor nieuwe soorten ervaringen is vereist, kunnen een (of meer) nieuwe componenten in de stapel worden ingevoegd en is er slechts één plaats om wijzigingen aan te brengen.

![ Toevoegend een nieuw kanaal aan de stapel ](/help/journey-headless/developer/assets/adding-channel.png)

Nochtans wordt de ingewikkeldheid van de gebiedsdelen binnen de stapel snel duidelijk aangezien andere punten in de stapel moeten worden aangepast om de veranderingen aan te passen.

## De kop in de kop {#the-head}

Het hoofd van een systeem is doorgaans de uitvoerrenderer van dat systeem, meestal in de vorm van een grafische interface of andere grafische uitvoer.

Als we het hebben over een CMS zonder kop, beheert de CMS de inhoud en blijft ze leveren aan de consument. Nochtans, door slechts de **inhoud** op een gestandaardiseerde manier te leveren, weglaat een headless CMS de definitieve output die teruggeeft, verlatend de **presentatie** van de inhoud aan de verbruikende dienst.

![ Headless CMS ](/help/journey-headless/developer/assets/headless-cms.png)

De verbruikende services, of het nu gaat om AIR, een webshop, mobiele ervaringen, progressieve webapps (PWA&#39;s), enzovoort, nemen inhoud van de CMS zonder kop in en bieden hun eigen rendering. Ze zorgen ervoor dat ze hun eigen hoofd geven aan je inhoud.

Als u de kop weglaat, wordt de CMS vereenvoudigd doordat de complexiteit wordt weggenomen. Hierdoor wordt ook de verantwoordelijkheid voor het renderen van de inhoud verplaatst naar de diensten die de inhoud nodig hebben en die vaak beter geschikt zijn voor dergelijke rendering.

## Koploze inhoud omzetten in AEM {#translating-in-aem}

Naast robuuste tools voor het maken, beheren en leveren van traditionele webpagina&#39;s op een volledig stapelbare manier, biedt AEM ook de mogelijkheid om op zichzelf staande selecties van inhoud te maken en deze zonder problemen te bedienen.

Dankzij de kracht van AEM kan de server inhoud zonder kop, volledig of in beide modellen tegelijk leveren. Voor de vertaalspecialist, kan de zelfde reeks vertaalhulpmiddelen op beide types van inhoud worden toegepast, die u een verenigde benadering geven voor het vertalen van uw inhoud.

Op reis leert u hoe AEM inhoud vertaalt, maar op een hoog niveau is het concept eenvoudig:

1. Definieer een verbinding met een vertaalservice door het framework voor vertaalintegratie te configureren.
1. Bepaal welke inhoud met behulp van vertaalregels moet worden vertaald.
1. Maak een vertaalproject om de inhoud te oogsten, stuur het naar de vertaalservice en ontvang de resultaten.
1. U kunt de vertaalde inhoud controleren en publiceren.

## Volgende functies {#what-is-next}

Hartelijk dank voor de start van uw AEM-reis zonder hoofd! Nu u dit document leest, moet u:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Wees vertrouwd met de manier waarop AEM ondersteuning biedt voor headless en translatie.

Bouw op deze kennis voort en ga uw onophoudelijke vertaalreis van AEM door het document [ te herzien begonnen worden met de hoofdloze vertaling van AEM ](getting-started.md) waar u een overzicht van zult hebben hoe AEM hoofdloze inhoud beheert en zijn vertaalhulpmiddelen te kennen krijgt.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de hoofdloze vertaalreis door het document [ te herzien begonnen wordt met de hoofdloze vertaling van AEM, ](getting-started.md) het volgende zijn sommige extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document doen worden vermeld, maar zij worden niet vereist om op de hoofdloze reis verder te gaan.

* [ MSM en Vertaling ](/help/sites-administering/msm-and-translation.md) - de details van de Manager van de Multisite van AEM en hoe het met zijn vertaalhulpmiddelen werkt
* Een [ Inleiding aan AEM als Headless CMS ](/help/sites-developing/headless/introduction.md)
* Het [ Portaal van de Ontwikkelaar van AEM ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ Leerprogramma&#39;s voor Zwaartepunt in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
