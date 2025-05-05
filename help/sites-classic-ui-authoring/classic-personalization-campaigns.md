---
title: Campaign Management
description: Campagnerbeheer biedt digitale marketers de mogelijkheid om persoonlijke inhoud te leveren en zo speciale ervaringen voor bezoekers te creëren. Hiermee kunt u uw marketingcampagnes ordenen op het web, via e-mail en via mobiele services en zo uw bezoekers erbij betrekken.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: d1741525-a475-4a76-bd16-55318023495e
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---


# Campaign Management{#campaign-management}

Campagnerbeheer biedt digitale marketers de mogelijkheid om persoonlijke inhoud te leveren en zo speciale ervaringen voor bezoekers te creëren.

Hiermee kunt u uw marketingcampagnes ordenen op het web, via e-mail en via mobiele services en zo uw bezoekers erbij betrekken. U kunt inhoud maken, bezoekers segmenteren, doelgerichte inhoud voor specifieke gebruikersprofielen duwen en promoten en campagnes op meerdere kanalen beheren.

In dit document worden de verschillende elementen beschreven waaruit campagnes bestaan. Meer gedetailleerde informatie is beschikbaar in de volgende documenten:

* [Teasers en strategieën](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [E-mailmarketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Openingspagina&#39;s](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Doelaanbiedingen](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Werken met de manager van de Campagne van de Marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Segmentering begrijpen](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Uw campagne instellen](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

Het beheer van campagnes bestaat uit verschillende elementen:

* **Banden**
In Adobe Experience Manager (AEM), zijn de merken de top-level eenheid en vormen een inzameling van **Campagnes**.

* **Campagnes**
Een campagne is een inzameling van individuele **Ervaringen**.

* **Ervaringen**
De geconcentreerde inhoud vormt de diverse ervaringen, die aan de bezoeker bij **Touchpoints** worden voorgesteld. Er zijn verschillende soorten ervaring beschikbaar:

   * **Teasers**

     [ de Pagina&#39;s/de Alinea&#39;s van het Taser ](#teasers) worden gebruikt om specifieke bezoekers **Segmenten** aan inhoud te sturen die op hun belangen wordt geconcentreerd.

     Taserpagina&#39;s kunnen:

      * een reeks opties presenteren waaruit de bezoeker kan kiezen
      * toon slechts één teaser paragraaf die op het specifieke bezoekerssegment gebaseerd is. De weergegeven teasalinea kan bijvoorbeeld afhankelijk zijn van de leeftijd van de bezoeker.

     Een laserpagina is doorgaans een tijdelijke actie die een bepaalde periode duurt, totdat deze wordt vervangen door de volgende laserpagina.

   * **Nieuwsbrieven**

     [ E-mailMededelingen ](#emailmarketing) worden gebruikt om gebruikers in dienst te nemen en hen aan te moedigen om uw website te bezoeken. Deze nemen gewoonlijk de vorm van een nieuwsbrief, die naar uw **wordt verzonden leidt** (die in **Lijsten** worden gegroepeerd). **Nota:** de Adobe is niet van plan om dit vermogen verder te verbeteren. De aanbeveling moet [ Adobe Campaign en de integratie aan AEM ](/help/sites-administering/campaign.md) gebruiken.

   * **Adobe Target**

     Dit maakt integratie met Adobe Target (voorheen Test&amp;Target) mogelijk, waardoor marketers een tool voor optimalisatie van hun conversiewebsite krijgen met de benodigde mogelijkheden om hun online-inhoud voortdurend te maken en biedt hun klanten meer relevantie voor een grotere conversie. Adobe Target biedt een intuïtieve interface voor het ontwerpen en uitvoeren van tests, het maken van publiekssegmenten en het kiezen van inhoud die allemaal in één toepassing beschikbaar is.

* **Aanraakpunten**

  Dit zijn de contactpunten tussen de bezoeker en uw campagne. De aanraakpunten zijn verbonden met de ervaringen die u hebt gemaakt.

  Bijvoorbeeld, voor telers is het de inhoudspagina waar de teaser paragraaf wordt gevestigd, voor een nieuwsbrief is het de postingslijst.

* **Leads**

  De informatie die u over uw bezoekers hebt verzameld en hoe te om hen te contacteren vormt de basis voor uw lood. **Nota:** de Adobe is niet van plan om dit vermogen verder te verbeteren.

  De aanbeveling moet [ Adobe Campaign en de integratie aan AEM ](/help/sites-administering/campaign.md) gebruiken.

* **Lijsten**

  Leads worden gegroepeerd in lijsten, zodat u er gezamenlijk actie op kunt ondernemen. Nota: **Nota:** de Adobe is niet van plan om dit vermogen verder te verbeteren.

  De aanbeveling moet [ Adobe Campaign en de integratie aan AEM gebruiken.](/help/sites-administering/campaign.md)

* **Segmenten**

  De bezoekers van de plaats hebben verschillende belangen en doelstellingen wanneer zij aan een plaats komen. Door dit te analyseren op basis van factoren zoals activiteit op de website, geregistreerde profielinformatie en activiteit op andere websites, kunt u segmenten definiëren. De inhoud kan vervolgens worden afgestemd op de behoeften en belangen van de bezoeker, afhankelijk van de segmenten die deze nodig hebben.

* **MCM**

  De manager van de Campagne van de Marketing (MCM) is een console die u tot alle functionaliteit toegang heeft u uw campagnes, merken, ervaringen, touchpoints, lood, lijsten, segmenten, en rapporten moet tot stand brengen en controleren.

  Het kan van diverse plaatsen worden betreden (geëtiketteerd als **Campagnes**), of met, bijvoorbeeld, URL:

  `http://localhost:4502/libs/mcm/content/admin.html`
