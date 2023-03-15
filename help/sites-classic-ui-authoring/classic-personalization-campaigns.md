---
title: Campaign Management
seo-title: Campaign Management
description: Campagnerbeheer biedt digitale marketers de mogelijkheid om persoonlijke inhoud te leveren en zo speciale ervaringen voor bezoekers te creëren. Zo kunt u uw marketingcampagnes ordenen op het web, via e-mail en mobiele services en zo uw bezoekers erbij betrekken.
seo-description: Campaign management provides digital marketers the opportunity to deliver personalized content and so create dedicated experiences for visitors. It allows you to orchestrate your marketing campaigns across the web, email and mobile services and so engage your visitors.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
exl-id: d1741525-a475-4a76-bd16-55318023495e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# Campaign Management{#campaign-management}

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

* **Merken**
In AEM zijn merken de eenheid op het hoogste niveau en vormen ze een verzameling van 
**Campagnes**.

* **Campagnes**
Een campagne is een collectie individuele 
**Ervaringen**.

* **Ervaringen**
De inhoud met focus vormt de verschillende ervaringen die aan de bezoeker worden getoond op 
**Aanraakpunten**. Er zijn verschillende soorten ervaring beschikbaar:

   * **Teasers**
      [Taserpagina&#39;s/alinea&#39;s](#teasers) worden gebruikt om specifieke bezoekers te sturen **Segmenten** inhoud die op hun belangen is gericht.

      Taserpagina&#39;s kunnen:

      * een reeks opties presenteren waaruit de bezoeker kan kiezen
      * slechts één laseralinea tonen die op het specifieke bezoekerssegment is gebaseerd; zo kan de getoonde laseralinea afhankelijk zijn van de leeftijd van de bezoeker .

      Een laserpagina is doorgaans een tijdelijke actie die een bepaalde periode duurt, totdat deze wordt vervangen door de volgende laserpagina.

   * **Nieuwsbrieven**

      [E-mailcommunicatie](#emailmarketing) worden gebruikt om gebruikers aan te spreken en hen aan te moedigen uw website te bezoeken. Deze worden meestal verzonden in de vorm van een nieuwsbrief naar uw **Leads** (die gewoonlijk worden gegroepeerd in **Lijsten**). **Opmerking:** Adobe is niet van plan deze capaciteit verder te verbeteren. Aanbeveling is [Adobe Campaign en de integratie van AEM](/help/sites-administering/campaign.md).

   * **Adobe Target**

      Dit maakt integratie met Adobe Target (voorheen Test&amp;Target) mogelijk, waardoor marketers een tool voor optimalisatie van hun conversiewebsite krijgen met de benodigde mogelijkheden om hun online-inhoud voortdurend te maken en aanbiedingen die voor hun klanten relevanter zijn, waardoor hun conversie wordt vergroot. Adobe Target biedt een intuïtieve interface voor het ontwerpen en uitvoeren van tests, het maken van publiekssegmenten en het kiezen van inhoud, allemaal vanuit één toepassing.


* **Aanraakpunten**

   Dit zijn de contactpunten tussen de bezoeker en uw campagne. De aanraakpunten zijn verbonden met de ervaringen die u hebt gemaakt.

   Bijvoorbeeld, voor telers is het de inhoudspagina waar de teaser paragraaf wordt gevestigd, voor een nieuwsbrief is het de postingslijst.

* **Leads**

   De informatie die u over uw bezoekers hebt verzameld en hoe te om hen te contacteren vormt de basis voor uw lood. **Opmerking:** Adobe is niet van plan deze capaciteit verder te verbeteren.

   Aanbeveling is [Adobe Campaign en de integratie van AEM](/help/sites-administering/campaign.md).

* **Lijsten**

   Regelafstand wordt meestal gegroepeerd in lijsten, zodat u er gezamenlijk op kunt reageren. Opmerking: **Opmerking:** Adobe is niet van plan deze capaciteit verder te verbeteren.

   Aanbeveling is [Adobe Campaign en de integratie naar AEM.](/help/sites-administering/campaign.md)

* **Segmenten**

   De bezoekers van de plaats hebben verschillende belangen en doelstellingen wanneer zij aan een plaats komen. Door dit te analyseren op basis van factoren zoals activiteit op de website, geregistreerde profielinformatie en activiteit op andere websites, kunt u segmenten definiëren. De inhoud kan vervolgens specifiek worden afgestemd op de behoeften en belangen van de bezoeker, afhankelijk van het segment of de segmenten waaraan de inhoud voldoet.

* **MCM**

   De manager van de Campagne van de Marketing (MCM) is een console die u toestaat om tot alle functionaliteit toegang te hebben u uw campagnes, merken, ervaringen, touchpoints, lood, lijsten, segmenten en rapporten moet tot stand brengen en controleren.

   Het kan van diverse plaatsen worden betreden (geëtiketteerd als **Campagnes**), of met bijvoorbeeld de URL:

   `http://localhost:4502/libs/mcm/content/admin.html`
