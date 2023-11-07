---
title: Adobe Experience Manager Headless Content Architect Reis
description: Een inleiding tot de krachtige, flexibele, eindeloze eigenschappen van Adobe Experience Manager, en hoe te om inhoud voor uw project te modelleren.
exl-id: 49ba0d6d-dde4-42e2-92fd-c7655c0eebc0
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---

# Content Modeling for Headless with AEM - Een introductie {#architect-headless-introduction}

In dit deel van het [Reis van architect zonder hoofdinhoud AEM](overview.md), kunt u de (basis) concepten en de terminologie leren noodzakelijk om inhoud modellering voor hoofdloze inhoudslevering met Adobe Experience Manager (AEM) te begrijpen.

Met dit document krijgt u een beter inzicht in de levering van inhoud zonder kop, hoe AEM koploze inhoud ondersteunt en hoe inhoud wordt gemodelleerd voor koploze inhoud. Na het lezen moet u:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Wees vertrouwd met de manier waarop AEM modellering van inhoud en hoofdletters ondersteunt.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de concepten en de terminologie relevant voor Headless Content Modeling.

## Volledige levering van inhoud {#full-stack}

Sinds de opkomst van gebruiksvriendelijke, grootschalige contentbeheersystemen (CMS&#39;s) hebben organisaties deze als centrale locatie gebruikt voor het beheer van berichten, branding en communicatie. Het gebruik van het CMS als centraal punt voor het beheer van ervaringen heeft de efficiëntie verbeterd doordat taken in verschillende systemen niet hoeven te worden gedupliceerd.

![De klassieke full-stack CMS](/help/journey-headless/developer/assets/full-stack.png)

In een volledig-stapel CMS, is alle functionaliteit voor het manipuleren van inhoud in CMS. De functies van het systeem bestaan uit verschillende onderdelen van de CMS-stapel. De full-stack oplossing heeft veel voordelen.

* Er is één systeem om te onderhouden.
* Inhoud wordt centraal beheerd.
* Alle diensten van het systeem zijn geïntegreerd.
* Inhoud schrijven is naadloos.

Als dus een nieuw kanaal moet worden toegevoegd of ondersteuning voor nieuwe soorten ervaringen is vereist, kunnen een (of meer) nieuwe componenten in de stapel worden ingevoegd en is er slechts één plaats om wijzigingen aan te brengen.

![Een nieuw kanaal toevoegen aan de stapel](/help/journey-headless/developer/assets/adding-channel.png)

Nochtans wordt de ingewikkeldheid van de gebiedsdelen binnen de stapel snel duidelijk aangezien andere punten in de stapel moeten worden aangepast om de veranderingen aan te passen.

## De kop in de kop {#the-head}

Het hoofd van een systeem is doorgaans de uitvoerrenderer van dat systeem, meestal in de vorm van een grafische interface of andere grafische uitvoer.

Als we het hebben over een CMS zonder kop, beheert het CMS de inhoud en blijft het leveren aan consumenten. Maar alleen door de **content** op gestandaardiseerde wijze weglaat een CMS zonder kop de uiteindelijke rendering van de uitvoer, waardoor de **presentatie** van de inhoud aan de verbruikende dienst.

![CMS zonder hoofd](/help/journey-headless/developer/assets/headless-cms.png)

De verbruikende services, of het nu gaat om AIR, een webshop, mobiele ervaring, progressieve webapps (PWA), enzovoort, nemen inhoud van het CMS zonder kop in en bieden hun eigen rendering. Ze zorgen ervoor dat ze hun eigen hoofd geven aan je inhoud.

Het weglaten van het hoofd vereenvoudigt CMS door ingewikkeldheid te verwijderen. Hierdoor wordt ook de verantwoordelijkheid voor het renderen van de inhoud verplaatst naar de diensten die de inhoud nodig hebben en die vaak beter geschikt zijn voor dergelijke rendering.

## Inhoud modelleren {#content-modeling}

Content Modeling (ook wel gegevensmodellering genoemd) is uw specialiteit, dus wat moet u in overweging nemen bij het modelleren voor headless?

Voor toepassingen zonder kop hebt u een vooraf gedefinieerde structuur nodig om toegang te krijgen tot uw inhoud en er iets mee te kunnen doen. Het zou mogelijk zijn om uw inhoud als vrije vorm te hebben, maar het zou leven maken *zeer* ingewikkeld voor de toepassingen.

AEM u als Content Architect de inhoud modelleert om een reeks van **Modellen van inhoudsfragmenten**. Deze definiëren de structuur die wordt gebruikt wanneer de auteurs van de inhoud de **Inhoudsfragmenten** die de inhoud bevatten.

### De inhoud openen {#access-content}

Dit is meer een ontwikkelingsdetail - maar het zou u kunnen interesseren, enkel om het verhaal te voltooien.

Nadat u de modellen voor inhoudsfragmenten hebt gemaakt en de auteurs deze hebben gebruikt om de inhoud te genereren, moeten de toepassingen zonder kop toegang krijgen tot deze inhoud.

Adobe Experience Manager (AEM) heeft via de GraphQL API selectief toegang tot uw inhoudsfragmenten. Alleen de benodigde inhoud wordt geretourneerd. Met de API kan een ontwikkelaar query&#39;s formuleren die specifieke inhoud selecteren. Dit selectieproces is gebaseerd op *uw* Modellen van inhoudsfragmenten.

Dit betekent dat uw project zonder kop gestructureerde inhoud voor gebruik in uw toepassingen kan realiseren.

## Volgende functies {#whats-next}

Nu u de concepten en de terminologie hebt geleerd, is de volgende stap: [Leer de grondbeginselen van modellering met Content Fragment Models](basics.md).

## Aanvullende bronnen {#additional-resources}

* AEM Headless Developer Journey
   * [Meer informatie over CMS Headless Development](/help/journey-headless/developer/learn-about.md)
   * [Leer hoe u uw inhoud kunt modelleren](/help/journey-headless/developer/model-your-content.md)
* [Inleiding tot AEM als een headless CMS](/help/sites-developing/headless/introduction.md)
* [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [Tutorials voor headless in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
