---
title: Paginaanalysegegevens bekijken om de doeltreffendheid van pagina-inhoud te meten
description: Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 554b10c2-6157-4821-a6a7-f2fb6666cdff
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Integration
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Gegevens van paginaanalyse bekijken{#seeing-page-analytics-data}

Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten.

## Analyse zichtbaar vanuit de console {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

Paginaanalysegegevens worden weergegeven in [Lijstweergave](/help/sites-authoring/basic-handling.md#list-view) van de Sites-console. Wanneer de pagina&#39;s in lijstformaat worden getoond, zijn de volgende kolommen beschikbaar door gebrek:

* Paginaweergaven
* Unieke bezoekers
* Tijd op pagina

In elke kolom wordt een waarde voor de lopende rapportageperiode weergegeven en wordt ook aangegeven of de waarde sinds de vorige rapportageperiode is gestegen of gedaald. De gegevens die u ziet, worden elke 12 uur bijgewerkt.

>[!NOTE]
>
>U wijzigt de updateperiode als volgt: [het importinterval configureren](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Open de **Sites** console; bijvoorbeeld [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)
1. Rechtsboven op de werkbalk (in de rechterbovenhoek) klikt u op het pictogram om het te selecteren **Lijstweergave** (het weergegeven pictogram is afhankelijk van het [huidige weergave](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. Nogmaals, uiterst rechts op de werkbalk (rechterbovenhoek), klikt u op het pictogram en selecteert u **Instellingen weergeven**. De **Kolommen configureren** wordt geopend. Breng vereiste wijzigingen aan en bevestig deze met **Bijwerken**.

   ![aa-04](assets/aa-04.png)

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
>Wanneer een boomstructuur met pagina&#39;s onderliggende elementen bevat die zijn gekoppeld aan verschillende Adobe Analytics-wolkenconfiguraties, kunt u de beschikbare gegevenskolommen voor de pagina&#39;s niet configureren.

1. Gebruik in de lijstweergave de weergavekiezers (rechts van de werkbalk) en selecteer **Instellingen weergeven** en vervolgens **Aangepaste analysegegevens toevoegen**.

   ![aa-15](assets/aa-15.png)

1. Selecteer de metriek die u aan auteurs in de console van Plaatsen wilt blootstellen, en dan klikken **Toevoegen**.

   De kolommen die worden weergegeven, worden opgehaald uit Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Inhoudsgegevens van sites openen {#opening-content-insights-from-sites}

Openen [Inhoudsinzicht](/help/sites-authoring/content-insights.md) van de console van Plaatsen om paginadoeltreffendheid verder te onderzoeken.

1. Selecteer in de Sites-console de pagina waarvoor u Inhoudsgegevens wilt weergeven.
1. Klik op het pictogram Analytics en Recommendations op de werkbalk.

   ![Pictogram Analytics en Recommendations](do-not-localize/chlimage_1-16a.png)

## Analyses zichtbaar in de Pagina-editor (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!NOTE]
>
>Dit wordt getoond als [Activity Map is geconfigureerd](/help/sites-administering/adobeanalytics-connect.md#configuring-for-the-activity-map) voor uw website.

>[!NOTE]
>
>Gegevens voor de Activity Map zijn afkomstig uit Adobe Analytics.

Wanneer uw website [geconfigureerd voor Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md), kunt u de [modus Activity Map](/help/sites-authoring/author-environment-tools.md#page-modes) om relevante gegevens te bekijken. Bijvoorbeeld:

![aa-07](assets/aa-07.png)

### Toegang tot de Activity Map {#accessing-the-activity-map}

Na het selecteren van [Activity Map](/help/sites-authoring/author-environment-tools.md#page-modes) wordt u gevraagd uw Adobe Analytics-gegevens in te voeren.

![aa-03](assets/aa-03.png)

De **Analyse** zwevende werkbalk wordt weergegeven; hier kunt u het volgende doen:

* de werkbalkopmaak wijzigen met dubbele pijlen (**>>**)
* Paginadetails in-/uitschakelen (oogpictogram)
* De Activity Map-instellingen configureren (cogopictogram)
* Selecteer de analysefunctie die u wilt weergeven (verschillende keuzelijsten)
* Sluit de Activity Map en sluit de werkbalk (x)

![aa-09](assets/aa-09.png)

### De weer te geven analyse selecteren {#selecting-the-analytics-to-show}

U kunt aan de hand van de verschillende criteria bepalen welke analysegegevens moeten worden weergegeven en hoe deze moeten worden weergegeven:

* **Standaard**/**Live**

* gebeurtenistype
* gebruikersgroep
* **Luchtbellen**/**Verloop**/**Gainers en Losers**/**Uit**

* te tonen periode

![aa-13](assets/aa-13.png)

### De Activity Map configureren {#configuring-the-activity-map}

Gebruik de **Instellingen tonen** pictogram om het **Activity Map-instellingen** in.

![aa-04-1](assets/aa-04-1.png)

De **Activity Map-instellingen** biedt een reeks opties op drie tabbladen:

![aa-06](assets/aa-06.png)

* Algemeen

   * Rapportsuite
   * Paginanaam
   * Taal
   * Labelbedekkingen met
   * Tekengrootte label
   * Verloopkleur
   * Bubbelkleur
   * Kleurverloop op basis van
   * Transparantie verloop

* Standaard

   * Weergeven (type en aantal koppelingen)
   * Bedekkingen verbergen voor koppelingen die geen treffers hebben ontvangen

* Live

   * Bovenkant weergeven (Gainers of Losers)
   * Onderkant % uitsluiten
   * Automatisch bijwerken (gegevens en periode)
