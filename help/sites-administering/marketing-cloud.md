---
title: Integratie met de Adobe Experience Cloud
description: Leer hoe u Adobe Experience Manager kunt integreren met Adobe Experience Cloud.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: ba518290-dd82-44dc-ae7c-c8152df89179
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Integratie met de Adobe Experience Cloud{#integrating-with-the-adobe-marketing-cloud}

De [Adobe Experience Cloud](https://business.adobe.com/products/marketing-cloud/main.html), bevat krachtige webanalytische functies en producten voor het optimaliseren van websites die gebruiksvriendelijke, realtime gegevens en inzichten leveren om succesvolle online initiatieven te stimuleren. Het biedt een geïntegreerd en open platform voor online bedrijfsoptimalisatie. De cloud bestaat uit geïntegreerde toepassingen voor het verzamelen en onthullen van de kracht van inzicht van de klant om de aankoop, conversie en retentie van de klant en het maken en distribueren van inhoud te optimaliseren.

Met Adobe Experience Manager (AEM) kunt u naadloos integreren met de volgende producten van de Adobe Experience Cloud:

* Adobe Analytics biedt marketers praktische, realtime informatie over online strategieën en marketinginitiatieven.
* Adobe Target biedt marketers de mogelijkheid om hun online inhoud voortdurend voor hun klanten relevanter te maken, waardoor ze een grotere conversie krijgen.
* Adobe Dynamic Media Classic automatiseert mediabeheer, stroomlijnt webpublicaties en verbetert de webervaringen, allemaal in een gehoste omgeving.
* Adobe Dynamic Tag Management biedt marketers intuïtieve tools om snel en eenvoudig een onbeperkt aantal Adoben en tags van derden te beheren.
<!-- Search&Promote is end of life as of September 1, 2022 * Adobe Search&Promote gives marketers the ability to control and optimize the search results on their sites. -->
* Met Adobe Campaign kunt u inhoud voor e-maillevering rechtstreeks in Adobe Experience Manager beheren.

Bovendien kunt u [AEM integreren met Creative Cloud](/help/assets/aem-cc-integration-best-practices.md) en met [services van derden](/help/sites-administering/third-party-services.md).

## Integreren met Adobe Analytics {#integrating-with-adobe-analytics}

[Adobe Analytics](https://business.adobe.com/products/analytics/adobe-analytics.html) Dit is de toonaangevende oplossing voor de digitale markt, die de mogelijkheid biedt om geïntegreerde gegevens van alle online initiatieven via meerdere marketingkanalen te meten, te analyseren en te optimaliseren. Het verstrekt marketers actionable, real-time Web analytics intelligentie over digitale strategieën en marketing initiatieven. Adobe Analytics helpt marketers snel de meest winstgevende paden te identificeren via een website, gesegmenteerd verkeer om hoogwaardige webbezoekers te vinden, te bepalen waar bezoekers vandaan van de site navigeren en belangrijke succesgegevens voor online marketingcampagnes te identificeren.

U kunt Adobe Analytics gebruiken om gegevens van uw sites te analyseren.

Door te integreren met Adobe Analytics kunt u het volgende doen:

* Gebruikersregistratie voor Analytics inschakelen.
* Wijs uw looppaswijzen (bijvoorbeeld, auteur, publiceer) aan verschillende rapportreeksen toe.
* Clientcontextvariabelen verzenden als conversievariabelen of verkeerseigenschappen.
* Gebruik vooraf gedefinieerde variabeletoewijzingen.
* Configureer volledige sitesecties tegelijk.
* Aangepaste gebeurtenissen bijhouden.

Voor informatie over het integreren van AEM met Analytics, zie [Integreren met Adobe Analytics](/help/sites-administering/adobeanalytics.md).

U kunt ook de opdracht [Wizard Inschakelen](/help/sites-administering/opt-in.md) om de integratie gemakkelijk uit te voeren.

## Integreren met Adobe Target {#integrating-with-adobe-target}

[Adobe Target](https://business.adobe.com/products/target/adobe-target.html) wordt door marketers gebruikt om online tests te ontwerpen en uit te voeren, om on-the-fly publiekssegmenten te maken (op basis van gedrag) en om het richten van inhoud en online ervaringen te automatiseren.

De online consumenten hebben vandaag de dag constant veranderende behoeften en verwachten relevante, zelfs gepersonaliseerde inhoud van de grote verscheidenheid van plaatsen en inhoudsbronnen zij van kunnen kiezen. Om een online publiek te bereiken, is het van essentieel belang dat online marketeers snel identificeren welke aanbiedingen en inhoud relevant en dwingend zijn voor hun publiek. Op basis van deze kennis hebben marketers de mogelijkheid nodig om hun sites voortdurend te ontwikkelen en de juiste inhoud te richten op verschillende doelgroepen.

[Integreren met Adobe Target](/help/sites-administering/target.md) legt uit hoe u uw site kunt integreren met Target.

U kunt ook de opdracht [Wizard Inschakelen](/help/sites-administering/opt-in.md) om de integratie gemakkelijk uit te voeren.

## Aanmelden bij Analyse en Doel {#opting-in-to-analytics-and-target}

AEM biedt een eenvoudige opt-in-procedure voor integratie met Adobe Analytics en Adobe Target. Wanneer u login als beheerder en de console van Projecten bezoekt, wordt u voorgesteld met een opt-in tovenaar.

![chlimage_1-107](assets/chlimage_1-107a.png)

Kies voor integratie met Analytics en/of Target om het gebruik van de mogelijkheden voor het bijhouden en analyseren van pagina&#39;s en de personalisatiefuncties mogelijk te maken. Wanneer u zich aanmeldt, geeft u de gegevens van uw gebruikersaccount op en geeft u de pagina&#39;s op die worden bijgehouden.

Zie voor meer informatie [Opteren in Adobe Analytics en Adobe Target.](/help/sites-administering/opt-in.md)

## Integreren met Adobe Dynamic Media Classic {#integrating-with-scene}

Adobe Dynamic Media Classic is een gehoste oplossing voor het publiceren, beheren, verbeteren en leveren van dynamische marketingmiddelen en rijke visuele producten voor het web, mobiele apparaten, e-mail, sociale media, internetdisplays en drukwerk.

In Adobe Experience Manager kunt u digitale middelen rechtstreeks van Adobe Experience Manager naar Dynamic Media Classic publiceren en kunt u digitale middelen van Dynamic Media Classic naar Adobe Experience Manager publiceren.

Bovendien kunt u Adobe Experience Manager-elementen die in Dynamic Media Classic zijn gepubliceerd, weergeven in verschillende viewers, zoals Standaardzoom en Video.

Raadpleeg voor meer informatie over hoe Adobe Experience Manager kan integreren met Dynamic Media Classic de [Integreren met Dynamic Media Classic](/help/sites-administering/scene7.md) documentatie.

## Integreren met Adobe Dynamic Tag Management {#integrating-with-adobe-dynamic-tag-management}

[Adobe Dynamic Tag Management](https://business.adobe.com/products/experience-platform/adobe-experience-platform.html) biedt marketers intuïtieve tools om snel en eenvoudig een onbeperkt aantal Adoben en tags van derden te beheren. U hebt meer controle en flexibiliteit om vrijwel alles online te optimaliseren, en tegelijkertijd de afhankelijkheid van IT-bronnen te verminderen.

[Adobe Dynamic Tag Management integreren](/help/sites-administering/dtm.md) met AEM, zodat u uw Dynamic Tag Management-wegeigenschappen kunt gebruiken om AEM sites bij te houden.

## Integreren met Adobe Audience Manager {#integrating-with-adobe-audience-manager}

De integratie van de Audience Manager is verwijderd in AEM 6.3.

<!-- Search&Promote is end of life as of September 1, 2022 ## Integrating with Search&Promote {#integrating-with-search-promote} -->

<!-- Search&Promote is end of life as of September 1, 2022 Adobe Search&Promote enables marketers to optimizehow visitors browse, find, compare, and select relevant products and content on web and mobile sites. Businesses can easily promote priority items based on business objectives and visitor intent, and automate merchandising and promotions activity via KPI-based triggers or metrics. -->

<!-- Search&Promote is end of life as of September 1, 2022 Adobe Search&Promote is a reliable and scalable hosted site search application, capable of scaling to millions of pages or products, for heavily visited online businesses ranging from retail to news sites. It offers unprecedented levels of marketer control and metrics-based relevance. -->

<!-- Search&Promote is end of life as of September 1, 2022 For information about integrating AEM and Search&Promote, see [Integrating with Adobe Search&Promote](/help/sites-administering/search-and-promote.md). -->

## Integreren met Adobe Campaign {#integrating-with-adobe-campaign}

[Adobe Campaign](https://business.adobe.com/products/campaign/adobe-campaign.html) Hiermee kunt u inhoud voor e-maillevering rechtstreeks in Adobe Experience Manager beheren.

Voor informatie over hoe AEM zich integreert met Adobe Campaign raadpleegt u [Integreren met Adobe Campaign](/help/sites-administering/campaignstandard.md).