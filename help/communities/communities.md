---
title: Ontwikkelingsgemeenschappen
description: Creëer en pas communautaire eigenschappen zoals forums, gebruikersgroepen, en meer aan.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 3ed3768a-1b3c-45a1-a34c-61694cd407d9
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Ontwikkelingsgemeenschappen  {#developing-communities}

## Overzicht {#overview}

Adobe Experience Manager (AEM) Community&#39;s vereenvoudigen het maken en aanpassen van community-functies, zoals forums, gebruikersgroepen, blogs, Vragen en antwoorden, kalenders, opmerkingen, revisies, stemmen, beoordelingen en toewijzingen. Deze functies leiden ertoe dat door de gebruiker gegenereerde inhoud (UGC) wordt ingevoerd in de publicatieomgeving.

De stichting van een [community-site](overview.md#communitiessites) is de [sociale component](scf.md) (SCF). Het maken van een gemeenschapssite begint met het selecteren van een [sjabloon voor community-site](sites-console.md) die bestaat uit [communautaire functies](functions.md).

Ga voor een overzicht en zelfstudies om aan de slag te gaan naar:

* [AEM Communities - Overzicht](overview.md)
* [Aan de slag met AEM Communities](getting-started.md)

>[!NOTE]
> 
>Het wordt ten zeerste aanbevolen de [nieuwste releases](deploy-communities.md#latest-releases).

## Aanbevolen implementaties {#recommended-deployments}

* [Opslag van communautaire inhoud](working-with-srp.md): bespreekt de beschikbare opties van de Sociale Leverancier van het Middel (SRP) voor een gemeenschappelijke opslag UGC
* [Aanbevolen topologieën voor Gemeenschappen](topologies.md): bespreekt topologieën die op gebruiksgeval en keus SRP worden gebaseerd

## Framework sociale component {#social-component-framework}

* [Framework sociale component](scf.md): overzicht van framework en API&#39;s.
* [SCF Handlebars Helpers](handlebars-helpers.md): standaard helpers en hoe aangepaste helpers te schrijven.
* [Aanpassing aan clientzijde](client-customize.md): code aanpassen die in de browser wordt uitgevoerd.
* [Aanpassing op de server](server-customize.md): code aanpassen die op de server wordt uitgevoerd.
* [Storage Resource Provider (SRP)](srp.md): overzicht van de opslag van community-inhoud.
* [Codeerrichtlijnen](code-guide.md): richtlijnen, tips en trucs.
* [Community Components Guide](components-guide.md): interactief ontwikkelingsinstrument.

## Component, Function en Feature Essentials {#component-function-and-feature-essentials}

AEM Communities-componenten, -functies en -functies bieden de bouwstenen voor [communitysites](sites-console.md).

* [Componenten, functies en essentiële functies](essentials.md)
* [Clientlibs voor Community-componenten](clientlibs.md)
* [Communautaire functies](functions.md)
* [Gemeenschapsgroepsjablonen](tools-groups.md)
* [Sjablonen voor community-sites](sites.md)

## Communautaire leden {#community-members}

* [Gebruikers en gebruikersgroepen beheren](users.md)
* [Sociale aanmelding met Facebook en Twitter](social-login.md)

## Communautaire groepen {#community-groups}

[Communautaire groepen](overview.md#communitygroups) het is de bedoeling de leden van de gemeenschap toe te staan subgemeenschappen op te richten binnen de communautaire site . Het maken van een community-groep kan plaatsvinden in de publicatie- of auteursomgeving.

* [Essentiële elementen van gebruikersgroepen](essentials-groups.md)
* [Functie Groepen](functions.md#groups-function)
* [Gemeenschapsgroepsjablonen](tools-groups.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)
* [Communautaire groepen auteurs](creating-groups.md)

## Gegevens beheren {#managing-data}

* [SRP en UGC Essentials](srp-and-ugc.md) - Hulpprogrammamethoden en -voorbeelden van SRP API
* [Grondbeginselen van tags](tag.md) - de mogelijkheid voor leden van de gemeenschap om UGC en/of gecatalogiseerde actiemiddelen van tags te voorzien

## Tutorials {#tutorials}

* [Zelfstudies op de client](tutorials.md#client-side-customization)
* [Zelfstudies op de server](tutorials.md#server-side-customization)
* [Hoe kan ik-instructies](tutorials.md#how-to-instructions)

## Problemen oplossen {#troubleshooting}

* [Problemen oplossen](troubleshooting.md)
* [Bekende problemen](/help/release-notes/release-notes.md)

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek [Gemeenschappen inzetten](deploy-communities.md) om over geadviseerde plaatsingen en de configuratie van de Verzender te leren.

* Bezoek [Communitysites beheren](administer-landing.md) om over het creëren van een Communautaire Plaats te leren, vormend Communautaire Malplaatjes van de Plaats, het modereren van communautaire inhoud, het beheren van leden, en het vormen overseinen.

* Bezoek [Componenten van Gemeenschappen ontwerpen](author-communities.md) om te leren om met te schrijven en de componenten van de Gemeenschappen te vormen.
