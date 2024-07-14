---
title: Paginaanalysegegevens bekijken om de doeltreffendheid van pagina-inhoud te meten
description: Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
legacypath: /content/help/en/experience-manager/6-4/help/sites-authoring/pa-using.html
exl-id: 2e406512-47fb-451d-b837-0a3898ae1f08
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Gegevens van paginaanalyse bekijken{#seeing-page-analytics-data}

Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten.

## Analyse zichtbaar vanuit de console {#analytics-visible-from-the-console}

![ pad-01 ](assets/spad-01.png)

De analysegegevens van de pagina worden getoond in [ Mening van de Lijst ](/help/sites-authoring/basic-handling.md#list-view) van de console van Plaatsen. Wanneer de pagina&#39;s in lijstformaat worden getoond, zijn de volgende kolommen beschikbaar door gebrek:

* Paginaweergaven
* Unieke bezoekers
* Tijd op pagina

In elke kolom wordt een waarde voor de lopende rapportageperiode weergegeven en wordt ook aangegeven of de waarde sinds de vorige rapportageperiode is gestegen of gedaald. De gegevens die u ziet, worden elke 12 uur bijgewerkt.

>[!NOTE]
>
>Om de updateperiode te veranderen, [ vorm het de invoerinterval ](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Open de **console van Plaatsen**; bijvoorbeeld, [ https://localhost:4502/sites.html/content ](https://localhost:4502/sites.html/content)
1. In het uiterste recht van de toolbar (hoger-juiste hoek), klik het pictogram om **Mening van de Lijst** te selecteren (het getoonde pictogram zal van de [ huidige mening ](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) afhangen).

1. Opnieuw, in het uiterste recht van de toolbar (hoger-juiste hoek), klik het pictogram dan selecteren **Montages van de Mening**. Het **vormt de dialoog van Kolommen** opent. Breng om het even welke vereiste veranderingen aan en bevestig met **Update**.

   ![ pad-02 ](assets/spad-02.png)

### De rapportageperiode selecteren {#selecting-the-reporting-period}

Selecteer de rapportperiode waarvoor de gegevens van Analytics op de console van Plaatsen verschijnen:

* Gegevens laatste 30 dagen
* Gegevens van afgelopen 90 dagen
* Gegevens van dit jaar

De huidige rapportageperiode wordt weergegeven op de werkbalk van de Sites-console (rechts van de bovenste werkbalk). Gebruik de vervolgkeuzelijst om de vereiste rapportageperiode te selecteren.

![ a-05 ](assets/aa-05.png)

### Beschikbare gegevenskolommen configureren {#configuring-available-data-columns}

Leden van de analytische-beheerders gebruikersgroep kunnen de console van Plaatsen vormen om auteurs toe te laten om extra kolommen van Analytics te zien.

>[!NOTE]
>
>Wanneer een boomstructuur met pagina&#39;s onderliggende elementen bevat die zijn gekoppeld aan verschillende Adobe Analytics-wolkenconfiguraties, kunt u de beschikbare gegevenskolommen voor de pagina&#39;s niet configureren.

1. In de Mening van de Lijst, gebruik de meningsselecteurs (recht van toolbar), de uitgezochte **Montages van de Mening** en dan **voegt de Gegevens van de Analyse van de Douane** toe.

   ![ pad-03 ](assets/spad-03.png)

1. Selecteer de metriek die u aan auteurs in de console van Plaatsen wilt blootstellen, en dan **toevoegen** klikken.

   De kolommen die worden weergegeven, worden opgehaald uit Adobe Analytics.

   ![ a-16 ](assets/aa-16.png)

### Inhoudsgegevens van sites openen {#opening-content-insights-from-sites}

Open [ Inzicht van de Inhoud ](/help/sites-authoring/content-insights.md) van de console van Plaatsen om paginadoeltreffendheid verder te onderzoeken.

1. Selecteer in de Sites-console de pagina waarvoor u Inhoudsgegevens wilt weergeven.
1. Klik op het pictogram Analytics en Recommendations op de werkbalk.

   ![ Analytics en het pictogram van Recommendations ](do-not-localize/chlimage_1-14.png)

## Analyses zichtbaar in de Pagina-editor (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen.
>
>De [ insteekmodule ActivityMap die door Adobe Analytics ](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) wordt verstrekt zou nu moeten worden gebruikt.
