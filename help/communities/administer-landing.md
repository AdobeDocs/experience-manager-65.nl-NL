---
title: Communitysites
description: Leer over de grondbeginselen van de gemeenschappen van Adobe Experience Manager (AEM) voor het beheer die reeds met zijn basiseigenschappen vertrouwd zijn.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: e3ffc73e-2bc5-492d-b64b-750cc7d8ab9b
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Communitysites {#communities-sites}

Deze sectie is bedoeld voor degenen die AEM Communities beheren en vertrouwd zijn met de functies van AEM Communities.

## Overzicht {#overview}

Ga voor een overzicht en zelfstudies om aan de slag te gaan naar:

* [AEM Communities - Overzicht](overview.md)
* [Aan de slag met AEM Communities](getting-started.md)

## Beheer en configuratieonderwerpen {#administration-and-configuration-topics}

### Creatie en beheer van sites van gemeenschappen {#communities-site-creation-and-management}

* Gemeenschappen [consoles](consoles.md)

   * [Sites](sites-console.md)

      * [Groepen (subgemeenschappen)](groups.md)

   * [Moderatie](moderation.md)
   * [Leden en groepsbeheer](members.md)
   * [Rapporten](reports.md)

* Gemeenschappen [*gereedschappen*](tools.md):

   * [Sitesjablonen](sites.md)
   * [Groepssjablonen](tools-groups.md)
   * [Communautaire functies](functions.md)
   * [Opslagconfiguratie](srp-config.md)
   * [Component Guide](components-guide.md)
   * [Badges](badges.md)


### Door gebruiker gegenereerde inhoud {#user-generated-content}

Een belangrijk kenmerk van AEM Communities is het genereren van door gebruikers gegenereerde inhoud (UGC) door inloggers (leden). Ga voor meer informatie over het werken met UGC naar:

* [Algemene UGC-opslag](working-with-srp.md): keuze van SRP voor gedeelde opslag van UGC
* [Moderne UGC](moderate-ugc.md): Vertrouwde leden kunnen UGC in bulk of in context matigen
* [UGC-tags](tag-ugc.md): functies kunnen zo worden geconfigureerd dat leden inhoud kunnen labelen
* [UGC vertalen](translate-ugc.md): de functies kunnen worden geconfigureerd om alle UGC te vertalen of leden toe te staan geselecteerde posts te vertalen
* [Analyseconfiguratie](analytics.md): Adobe Analytics in staat stellen om te rapporteren over verschillende maatstaven met betrekking tot lidactiviteit

### Communautaire leden {#community-members}

* [Gebruikers en gebruikersgroepen beheren](users.md): bijzonderheden over leden van de gemeenschap en groepen leden, waaronder geprivilegieerde leden.
* [Bijdragelimieten](limits.md): de mogelijkheid om detachering door nieuwe leden te beperken.
* [Tunnelservice](deploy-communities.md#tunnel-service-on-author): Hiermee kunt u leden van de publicatielanden en lidgroepen benaderen vanuit de auteursomgeving.
* [Samenstellingen van leden en groepen](members.md): Hiermee kunnen leden en lidgroepen van de publicatiezijde worden gemaakt en beheerd vanuit de auteursomgeving.
* [Gebruikerssynchronisatie](sync.md): voor het synchroniseren van leden en lidgroepen in meerdere publicatie-instanties.
* [Sociale aanmelding met Facebook en Twitter](social-login.md): mogelijkheid voor bezoekers van de site om lid te worden van de gemeenschap op basis van hun Facebook- of Twitter-inloggegevens.
* [Scores en badges](implementing-scoring.md): de mogelijkheid om toegangspasjes toe te wijzen om de rollen van een lid te identificeren en om leden een toegangspasje te laten verdienen door hun deelname aan de gemeenschap .
* [Meldingen](notifications.md): de mogelijkheid voor de leden om in kennis te worden gesteld van hun activiteiten.
* [Abonnementen](subscriptions.md): mogelijkheid voor leden om via externe e-mail te communiceren met de gemeenschap.
* [Berichten](messaging.md): de mogelijkheid voor leden om met de gemeenschap te communiceren door middel van interne berichten.

### Implementatie {#deployment}

De sectie Implementatie bevat specifieke informatie voor AEM Communities.

De aard van het werken met inhoud van de gemeenschap beïnvloedt de structuur van de plaatsing:

* [Aanbevolen topologieën voor Gemeenschappen](topologies.md)

Het is belangrijk om de meest recente versie van Gemeenschappen op het AEM platform te installeren:

* [Feitenpakket van de nieuwste gemeenschappen](deploy-communities.md#latestfeaturepack)

Zie de inzetpagina voor andere communautaire specifieke informatie, zoals voor [Bijwerken](upgrade.md), [Dispatcher](dispatcher.md), en [Replicatie](deploy-communities.md#replication-agents-on-author).

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek [Gemeenschappen inzetten](deploy-communities.md) waar u over geadviseerde plaatsingen kunt leren.

* Bezoek [Ontwikkelingsgemeenschappen](communities.md) waar u over het sociale componentenkader (SCF) en het aanpassen van de componenten en de eigenschappen van de Gemeenschappen kunt leren.

* Bezoek [Componenten van Gemeenschappen ontwerpen](author-communities.md) waar u kunt leren om met te schrijven en de componenten van de Gemeenschappen te vormen.
