---
title: Campagnebeheer
seo-title: Campagnebeheer
description: Campagnerbeheer biedt digitale marketers de mogelijkheid om persoonlijke inhoud te leveren en zo speciale ervaringen voor bezoekers te creëren. Zo kunt u uw marketingcampagnes ordenen op het web, via e-mail en mobiele services en zo uw bezoekers erbij betrekken.
seo-description: Campagnerbeheer biedt digitale marketers de mogelijkheid om persoonlijke inhoud te leveren en zo speciale ervaringen voor bezoekers te creëren. Zo kunt u uw marketingcampagnes ordenen op het web, via e-mail en mobiele services en zo uw bezoekers erbij betrekken.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---


# Campagnebeheer{#campaign-management}

Campagnerbeheer biedt digitale marketers de mogelijkheid om persoonlijke inhoud te leveren en zo speciale ervaringen voor bezoekers te creëren.

Zo kunt u uw marketingcampagnes ordenen op het web, via e-mail en mobiele services en zo uw bezoekers erbij betrekken. U kunt inhoud maken, bezoekers segmenteren, doelgerichte inhoud voor specifieke gebruikersprofielen duwen en promoten en campagnes op meerdere kanalen beheren.

In dit document worden de verschillende elementen beschreven waaruit campagnes bestaan. Meer gedetailleerde informatie is beschikbaar in de volgende documenten:

* [Teasers en strategieën](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [E-mailmarketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Openingspagina&#39;s](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Doelaanbiedingen](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Werken met de manager van de Campagne van de Marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Inzicht in segmentering](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Uw campagne instellen](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

Het beheer van campagnes bestaat uit verschillende elementen:

* **aem**
merken zijn de eenheid op hoofdniveau en vormen een verzameling 
**Campagnes**.

* **De**
campagne CampaignsA is een inzameling van individuele 
**Ervaringen**.

* ****
ErvaringenDe gerichte inhoud vormt de verschillende ervaringen die aan de bezoeker worden getoond op 
**Aanraakpunten**. Er zijn verschillende soorten ervaring beschikbaar:

   * **Teasers**
      [Taserpagina&#39;s/](#teasers) alinea&#39;s worden gebruikt om specifieke  **** bezoekerssegmenten te sturen naar inhoud die op hun belangen is toegespitst.

      Taserpagina&#39;s kunnen:

      * een reeks opties presenteren waaruit de bezoeker kan kiezen
      * slechts één laseralinea tonen die op het specifieke bezoekerssegment is gebaseerd; zo kan de getoonde laseralinea afhankelijk zijn van de leeftijd van de bezoeker .

      Een laserpagina is doorgaans een tijdelijke actie die een bepaalde periode duurt, totdat deze wordt vervangen door de volgende laserpagina.

   * **Nieuwsbrieven**

      [E-](#emailmarketing) mailcommunicatie wordt gebruikt om gebruikers aan te spreken en hen aan te moedigen uw website te bezoeken. Deze hebben gewoonlijk de vorm van een nieuwsbrief, die naar uw **Leads** wordt verzonden (die gewoonlijk in **Lijsten** worden gegroepeerd). **Opmerking:** Adobe is niet van plan deze mogelijkheid verder te verbeteren. De aanbeveling is om Adobe Campaign en de integratie in AEM[ te benutten.](/help/sites-administering/campaign.md)

   * **Adobe Target**

      Dit maakt integratie met Adobe Target (voorheen Test&amp;Target) mogelijk, waardoor marketers een tool voor optimalisatie van hun conversiewebsite krijgen met de benodigde mogelijkheden om hun online-inhoud voortdurend te maken en aanbiedingen die voor hun klanten relevanter zijn, waardoor hun conversie wordt vergroot. Adobe Target biedt een intuïtieve interface voor het ontwerpen en uitvoeren van tests, het maken van publiekssegmenten en het kiezen van inhoud, allemaal vanuit één toepassing.


* **Aanraakpunten**

   Dit zijn de contactpunten tussen de bezoeker en uw campagne. De aanraakpunten zijn verbonden met de ervaringen die u hebt gemaakt.

   Bijvoorbeeld, voor telers is het de inhoudspagina waar de teaser paragraaf wordt gevestigd, voor een nieuwsbrief is het de postingslijst.

* **Leads**

   De informatie die u over uw bezoekers hebt verzameld en hoe te om hen te contacteren vormt de basis voor uw lood. **Opmerking:** Adobe is niet van plan deze mogelijkheid verder te verbeteren.

   De aanbeveling is om Adobe Campaign en de integratie in AEM[ te benutten.](/help/sites-administering/campaign.md)

* **Lijsten**

   Regelafstand wordt meestal gegroepeerd in lijsten, zodat u er gezamenlijk op kunt reageren. Opmerking: **Opmerking:** Adobe is niet van plan deze mogelijkheid verder te verbeteren.

   Aanbeveling is om Adobe Campaign en de integratie naar AEM te gebruiken.[](/help/sites-administering/campaign.md)

* **Segmenten**

   De bezoekers van de plaats hebben verschillende belangen en doelstellingen wanneer zij aan een plaats komen. Door dit te analyseren op basis van factoren zoals activiteit op de website, geregistreerde profielinformatie en activiteit op andere websites, kunt u segmenten definiëren. De inhoud kan vervolgens specifiek worden afgestemd op de behoeften en belangen van de bezoeker, afhankelijk van het segment of de segmenten waaraan de inhoud voldoet.

* **MCM**

   De manager van de Campagne van de Marketing (MCM) is een console die u toestaat om tot alle functionaliteit toegang te hebben u uw campagnes, merken, ervaringen, touchpoints, lood, lijsten, segmenten en rapporten moet tot stand brengen en controleren.

   Het kan van diverse plaatsen (geëtiketteerd als **Campagnes**), of met, bijvoorbeeld URL worden betreden:

   `http://localhost:4502/libs/mcm/content/admin.html`

