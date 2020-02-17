---
title: Gegevens van paginaanalyse bekijken
seo-title: Gegevens van paginaanalyse bekijken
description: Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten
seo-description: Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten
uuid: 5398a5d5-0239-4194-a403-77f5e6fcd741
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5d192a48-c86f-4803-bb0d-0411ac7470f5
docset: aem65
legacypath: /content/help/en/experience-manager/6-4/help/sites-authoring/pa-using.html
translation-type: tm+mt
source-git-commit: e3683f6254295e606e9d85e88979feaaea76c42e

---


# Gegevens van paginaanalyse bekijken{#seeing-page-analytics-data}

Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten.

## Analyse zichtbaar vanuit de console {#analytics-visible-from-the-console}

![spad-01](assets/spad-01.png)

De analysegegevens van de pagina worden getoond in de Mening [van de](/help/sites-authoring/basic-handling.md#list-view) Lijst van de console van Plaatsen. Wanneer de pagina&#39;s in lijstformaat worden getoond, zijn de volgende kolommen beschikbaar door gebrek:

* Paginaweergaven
* Unieke bezoekers
* Tijd op pagina

In elke kolom wordt een waarde voor de lopende rapportageperiode weergegeven en wordt ook aangegeven of de waarde sinds de vorige rapportageperiode is gestegen of gedaald. De gegevens die u ziet, worden elke 12 uur bijgewerkt.

>[!NOTE]
>
>Om de updateperiode te veranderen, [vorm het de invoerinterval](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Open de **Sites** -console. bijvoorbeeld [https://localhost:4502/sites.html/content](https://localhost:4502/sites.html/content)
1. Rechtsboven op de werkbalk (in de rechterbovenhoek) klikt of tikt u op het pictogram om **Lijstweergave** te selecteren (het weergegeven pictogram is afhankelijk van de [huidige weergave](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. Klik of tik nogmaals in de rechterbovenhoek van de werkbalk op het pictogram en selecteer **Weergave-instellingen**. Het dialoogvenster Kolommen **** configureren wordt geopend. Breng de vereiste wijzigingen aan en bevestig deze met **Bijwerken**.

   ![spad-02](assets/spad-02.png)

### De rapportageperiode selecteren {#selecting-the-reporting-period}

Selecteer de rapportperiode waarvoor de gegevens van Analytics op de console van Plaatsen verschijnen:

* Gegevens laatste 30 dagen
* Gegevens van afgelopen 90 dagen
* Gegevens van dit jaar

De huidige rapportageperiode wordt weergegeven op de werkbalk van de Sites-console (rechts van de bovenste werkbalk). Gebruik de vervolgkeuzelijst om de vereiste rapportageperiode te selecteren.

![aa-05](assets/aa-05.png)

### Beschikbare gegevenskolommen configureren {#configuring-available-data-columns}

Leden van de analytische-beheerders gebruikersgroep kunnen de console van Plaatsen vormen om auteurs toe te laten om extra kolommen van Analytics te zien.

>[!NOTE]
>
>Wanneer een boomstructuur met pagina&#39;s onderliggende items bevat die zijn gekoppeld aan verschillende Adobe Analytics-cloud-configuraties, kunt u de beschikbare gegevenskolommen voor de pagina&#39;s niet configureren.

1. In de Lijstweergave gebruikt u de weergavekiezers (rechts van de werkbalk), selecteert u Instellingen **** weergeven en vervolgens Aangepaste analysegegevens **** toevoegen.

   ![spad-03](assets/spad-03.png)

1. Selecteer de metriek die u aan auteurs in de console van Plaatsen wilt blootstellen, en dan klikken **toevoegt**.

   De kolommen die worden weergegeven, worden opgehaald uit Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Inhoudsgegevens van sites openen {#opening-content-insights-from-sites}

Open Inzicht [van de](/help/sites-authoring/content-insights.md) Inhoud van de console van Plaatsen om paginadoeltreffendheid verder te onderzoeken.

1. Selecteer in de Sites-console de pagina waarvoor u Inhoudsgegevens wilt weergeven.
1. Klik op het pictogram Analytics and Recommendations (Analytics en Aanbevelingen) op de werkbalk.

   ![](do-not-localize/chlimage_1-14.png)

## Analyses zichtbaar uit de Pagina-editor (Activiteitenkaart) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de API voor Adobe Analytics is het niet langer mogelijk de versie van Activity Map te gebruiken die in AEM is opgenomen.
>
>De [ActivityMap-plug-in van Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) moet nu worden gebruikt.
