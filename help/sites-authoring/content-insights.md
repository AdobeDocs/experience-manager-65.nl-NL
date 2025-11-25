---
title: Content Insight
description: Content Insight biedt informatie over paginaprestaties met behulp van webanalyses en SEO-aanbevelingen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 187f3cde-a0db-4c02-9e8b-08272987a67d
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Content Insight{#content-insight}

Content Insight biedt informatie over paginaprestaties met behulp van webanalyses en SEO-aanbevelingen. Met Content Insight kunt u bepalen hoe pagina&#39;s moeten worden gewijzigd of hoe vorige wijzigingen de prestaties hebben gewijzigd. Voor elke pagina die u ontwerpt, kunt u Inhoud Insight openen om de pagina te analyseren.

![&#x200B; chlimage_1-311 &#x200B;](assets/chlimage_1-311.png)

De lay-out van de pagina Content Insight wordt aangepast aan de schermafmetingen en de stand van het apparaat dat u gebruikt.

## Rapportgegevens

De pagina Content Insight bevat rapporten waarin Adobe SiteCatalyst-, Adobe Target-, Adobe Social- en BrightStor-gegevens worden gebruikt:

* SiteCatalyst: rapporten voor de volgende meetgegevens zijn beschikbaar:

   * Paginaweergaven
   * Gemiddelde tijd besteed aan pagina
   * Bronnen

* Doel: rapporteert over campagneactiviteiten waarvoor uw pagina voorstellen bevat.
* BrightStor: meldt de paginafuncties die de zichtbaarheid van de pagina voor zoekprogramma&#39;s verbeteren en raadt functies aan die moeten worden geïmplementeerd.

Zie [&#x200B; Openend Analytics en Aanbevelingen voor een Pagina &#x200B;](/help/sites-authoring/ci-analyze.md#opening-analytics-and-recommendations-for-a-page).

## Rapportageperiode

De rapporten tonen gegevens voor een periode die u controleert. Wanneer u de rapportageperiode aanpast, worden de rapporten automatisch vernieuwd met gegevens voor die periode. Visuele aanwijzingen geven de tijd aan waarop paginaversies zijn gewijzigd, zodat u de prestaties van elke versie kunt vergelijken.

>[!NOTE]
>
>De tijdlijn voor het Insight-dashboard voor inhoud staat in `GMT` .

U kunt ook de granulariteit van de gerapporteerde gegevens opgeven. U kunt bijvoorbeeld dagelijkse, wekelijkse, maandelijkse of jaarlijkse gegevens zien.

Zie [&#x200B; Veranderend de Rapportageperiode &#x200B;](/help/sites-authoring/ci-analyze.md#changing-the-reporting-period).

>[!NOTE]
>
>De rapporten met inzichten van inhoud vereisen dat uw beheerder AEM heeft geïntegreerd met SiteCatalyst, Target en BrightStor. Zie [&#x200B; Integrerend met SightCatalyst &#x200B;](/help/sites-administering/adobeanalytics.md), [&#x200B; Integrerend met Adobe Target &#x200B;](/help/sites-administering/target.md), en [&#x200B; Integrerend met BrightEdge &#x200B;](/help/sites-administering/brightedge.md).

## Het weergavenrapport {#the-views-report}

Het rapport Weergaven bevat de volgende functies voor het evalueren van het paginaverkeer:

* Het totale aantal weergaven voor een pagina voor de verslagperiode.
* Een grafiek van het aantal weergaven in de verslagperiode:

   * Totaal aantal weergaven.
   * Unieke bezoekers.

![&#x200B; chlimage_1-312 &#x200B;](assets/chlimage_1-312.png)

## Rapport over paginagewicht {#the-page-average-engaged-report}

Het rapport Paginagemiddelde van deelnemers bevat de volgende functies voor het evalueren van de doeltreffendheid van pagina&#39;s:

* De gemiddelde tijd dat de pagina gedurende de gehele rapportageperiode open blijft.
* Een grafiek van de gemiddelde lengte van een paginaweergave over de verslagperiode.

![&#x200B; chlimage_1-313 &#x200B;](assets/chlimage_1-313.png)

## Bronnen {#the-sources-report}

Het rapport Bronnen geeft aan hoe gebruikers naar de pagina zijn genavigeerd, bijvoorbeeld op basis van resultaten van zoekprogramma&#39;s of via de bekende URL.

![&#x200B; chlimage_1-314 &#x200B;](assets/chlimage_1-314.png)

## Het Bounces-rapport {#the-bounces-report}

Het rapport Bounces bevat een grafiek die het aantal grenzen aangeeft dat zich tijdens de geselecteerde rapportageperiode op een pagina heeft voorgedaan.

![&#x200B; chlimage_1-315 &#x200B;](assets/chlimage_1-315.png)

## Het activiteitenverslag van de campagne {#the-campaign-activity-report}

Voor elke campagne waarvoor de pagina actief is, verschijnt een rapport genoemd *Activiteit van de Naam van de Campagne 0&rbrace;.* Het rapport toont paginamonpressies en omzettingen voor elk segment waarvoor een aanbieding wordt verstrekt.

![&#x200B; chlimage_1-316 &#x200B;](assets/chlimage_1-316.png)

## Rapport SEO-aanbevelingen {#the-seo-recommendations-report}

Het rapport SEO Recommendations bevat de resultaten van de BrightEdge-analyse voor de pagina. Het rapport is een controlelijst van paginafuncties die aangeeft welke functies de pagina heeft en niet bevat voor het maximaliseren van de zoekbaarheid met behulp van zoekmachines.

Met dit rapport kunt u taken maken die u wilt verbeteren en de zoekbaarheid van pagina&#39;s verbeteren. De aanbevelingen wijzen erop dat de taken voor de uitvoering van de aanbeveling zijn gecreeerd. Zie [&#x200B; Toewijzende Taken voor SEO Aanbevelingen &#x200B;](/help/sites-authoring/ci-analyze.md#assigning-tasks-for-seo-recommendations).

![&#x200B; chlimage_1-317 &#x200B;](assets/chlimage_1-317.png)
