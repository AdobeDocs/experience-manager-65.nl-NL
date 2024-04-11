---
title: Paginaprestaties analyseren
description: Gebruik de pagina Inzicht van inhoud om de prestaties van de pagina te analyseren die u ontwerpt
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: 14484a90-4e44-4c85-9411-b78ed11dc70d
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Integration
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# Paginaprestaties analyseren{#analyzing-page-performance}

Open de [Inhoudsinzicht](/help/sites-authoring/content-insights.md) pagina om de prestaties te analyseren van de pagina die u ontwerpt. Configureer de rapportageperiode om uw analyse te concentreren.

## Analyses en Recommendations openen voor een pagina {#opening-analytics-and-recommendations-for-a-page}

Gebruik de volgende procedure om de Analytics en Recommendations voor een pagina te zien:

1. Navigeer naar de pagina die u wilt analyseren.
1. Klik op de werkbalk op **Analytics en Recommendations**.

   >[!NOTE]
   >
   >Analyses en Recommendations voor een pagina worden alleen weergegeven als u AEM hebt geconfigureerd voor [integreren met Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md).

   ![screen-shot_2019-03-05at115319](assets/screen-shot_2019-03-05at115319.png)

### Wijziging van de verslagperiode {#changing-the-reporting-period}

Wijzig de volgende tijdgerelateerde aspecten van de analyserapporten:

* De periode waarin verslag moet worden uitgebracht.
* De granulariteit van de gegevens.

De gereedschappen voor het wijzigen van de aan de tijd gerelateerde aspecten van de rapporten staan boven aan de pagina Inzicht in inhoud. ![chlimage_1-126](assets/chlimage_1-126.png)

#### Wijziging van de verslagperiode {#changing-the-reporting-period-1}

Wijzig de rapportageperiode van de pagina Inhoudscontrole om uw analyse van de pagina-activiteit toe te spitsen op een specifieke periode. Wanneer u de rapportageperiode wijzigt, worden de rapporten automatisch vernieuwd. Het schaduwgebied op het tijdframe vertegenwoordigt de rapportageperiode. De datums in de tijdlijn nemen toe van links naar rechts.

![chlimage_1-127](assets/chlimage_1-127.png)

Om de rapportageperiode van een pagina Inhoudscontrole te wijzigen:

1. Als de tijdlijn niet boven aan de pagina wordt weergegeven, klikt u op het pictogram Tijdlijn in-/uitschakelen.

   ![Tijdschema in-/uitschakelen](do-not-localize/chlimage_1-22.png)

1. Als u de begindatum van de rapportageperiode wilt wijzigen, sleept u de cirkel die links van het schaduwgebied wordt weergegeven naar de gewenste begindatum.

   Als u de linkerzijde van het gearceerde gebied niet ziet, gebruikt u de schuifbalk om dit zichtbaar te maken.

1. Als u de einddatum van de rapportageperiode wilt wijzigen, sleept u de cirkel die rechts van het schaduwgebied wordt weergegeven naar de gewenste einddatum.

#### Wijziging van de rangorde van de verslagperiode {#changing-the-granularity-of-the-reporting-period}

Verander de hoeveelheid tijd dat elk gegevenspunt in een rapport overspant. Wanneer u bijvoorbeeld de granulariteit voor week selecteert, geeft elk gegevenspunt in het weergavenrapport het aantal weergaven voor een week aan.

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

De granulariteit beïnvloedt de rapporten die gegevens tegen tijd, zoals de Meningen en de Pagina Gemiddelde Bewerkte Minerapporten plotten. Korreligheid is ook van invloed op de schaal van de tijdlijn.

1. Als het besturingselement voor granulariteit niet wordt weergegeven, klikt u op het pictogram Korreligheid in-/uitschakelen.

   ![chlimage_1-128](assets/chlimage_1-128.png)

1. Klik op de gewenste granulariteit. Zodra geselecteerd, werkt het rapport automatisch bij om op granulariteit te wijzen.

### Taken toewijzen voor SEO Recommendations {#assigning-tasks-for-seo-recommendations}

Gebruik het SEO Recommendations-rapport om taken te maken waarmee u de zichtbaarheid van pagina&#39;s voor zoekprogramma&#39;s kunt verbeteren. Voor elke aanbeveling in het rapport die geen controleteken heeft, kunt u een taak tot stand brengen die u aan een gebruiker toewijst om het vereiste werk uit te voeren.

![chlimage_1-129](assets/chlimage_1-129.png)

De status van de SEO-aanbeveling geeft aan wanneer de taak is gemaakt maar nog niet is voltooid.

![chlimage_1-130](assets/chlimage_1-130.png)

Wanneer deze taak is gemaakt, wordt deze weergegeven in de lijst Taken van de gebruiker. Voor informatie over taken raadpleegt u [Werken met taken](/help/sites-authoring/task-content.md).

Gebruik de volgende procedure om een taak voor een aanbeveling te creëren SEO.

1. Klik op het informatiepictogram voor de SEO-aanbeveling.

   ![Onformatiepictogram](do-not-localize/chlimage_1-23.png)

1. Klik op het omcirkelde driehoekje naast het informatiepictogram.

   ![chlimage_1-131](assets/chlimage_1-131.png)

1. Vul de formuliervelden die worden weergegeven en selecteer vervolgens Maken:

   * Project: selecteer het project waarin u de taak wilt maken.
   * Naam: De naam die de taak identificeert. De standaardnaam is de titel van de SEO aanbeveling.
   * Toewijzen aan: selecteer de gebruiker aan wie de taak wordt toegewezen. Typ de naam van de gebruiker om de lijst te filteren.
   * Beschrijving: Een beschrijving van de activiteit die vereist is om de taak te voltooien. De standaardbeschrijving is de informatie die bij de SEO-aanbeveling is gevoegd.
   * Taakprioriteit: de prioriteit van de taak.
   * Vervaldatum: de datum waarop de taak moet zijn voltooid.

   **Opmerking:** De taak die wordt gecreeerd omvat ook de weg aan de pagina waarop de aanbeveling SEO van toepassing is.

1. Klik op Gereed om het bericht Taak gemaakt te sluiten.
