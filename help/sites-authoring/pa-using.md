---
title: Gegevens van paginaanalyse bekijken
seo-title: Gegevens van paginaanalyse bekijken
description: Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten
seo-description: Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
translation-type: tm+mt
source-git-commit: e3683f6254295e606e9d85e88979feaaea76c42e
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---


# Gegevens voor paginanalyse bekijken{#seeing-page-analytics-data}

Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten.

## Analyse zichtbaar vanuit de console {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

De gegevens van de paginaanalyse worden getoond in [Lijstweergave](/help/sites-authoring/basic-handling.md#list-view) van de console van Plaatsen. Wanneer de pagina&#39;s in lijstformaat worden getoond, zijn de volgende kolommen beschikbaar door gebrek:

* Paginaweergaven
* Unieke bezoekers
* Tijd op pagina

In elke kolom wordt een waarde voor de lopende rapportageperiode weergegeven en wordt ook aangegeven of de waarde sinds de vorige rapportageperiode is gestegen of gedaald. De gegevens die u ziet, worden elke 12 uur bijgewerkt.

>[!NOTE]
>
>Als u de updateperiode wilt wijzigen, [configureert u het importinterval](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Open de **Sites** console; bijvoorbeeld [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)
1. Rechtsboven op de werkbalk (in de rechterbovenhoek) klikt of tikt u op het pictogram om **Lijstweergave** te selecteren (het weergegeven pictogram is afhankelijk van de [huidige weergave](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. Nogmaals, uiterst rechts op de werkbalk (rechterbovenhoek), klikt of tikt u op het pictogram en selecteert u **Instellingen weergeven**. Het dialoogvenster **Kolommen configureren** wordt geopend. Breng de vereiste wijzigingen aan en bevestig deze met **Update**.

   ![aa-04](assets/aa-04.png)

### De rapportageperiode {#selecting-the-reporting-period} selecteren

Selecteer de rapportperiode waarvoor de gegevens van Analytics op de console van Plaatsen verschijnen:

* Gegevens laatste 30 dagen
* Gegevens van afgelopen 90 dagen
* Gegevens van dit jaar

De huidige rapportageperiode wordt weergegeven op de werkbalk van de Sites-console (rechts van de bovenste werkbalk). Gebruik de vervolgkeuzelijst om de vereiste rapportageperiode te selecteren.
![aa-05](assets/aa-05.png)

### Beschikbare gegevenskolommen {#configuring-available-data-columns} configureren

Leden van de analytische-beheerders gebruikersgroep kunnen de console van Plaatsen vormen om auteurs toe te laten om extra kolommen van Analytics te zien.

>[!NOTE]
>
>Wanneer een boomstructuur met pagina&#39;s onderliggende elementen bevat die zijn gekoppeld aan verschillende Adobe Analytics-wolkenconfiguraties, kunt u de beschikbare gegevenskolommen voor de pagina&#39;s niet configureren.

1. In de Mening van de Lijst, gebruik de meningsselecteurs (recht van toolbar), uitgezocht **de Montages van de Mening** en dan **voeg de Gegevens van de Analysatie van de Douane** toe.

   ![aa-15](assets/aa-15.png)

1. Selecteer de metriek die u aan auteurs in de console van Plaatsen wilt blootstellen, en dan **toevoegen** klikken.

   De kolommen die worden weergegeven, worden opgehaald uit Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Inhoudsgegevens van sites openen {#opening-content-insights-from-sites}

Open [Inzicht van inhoud](/help/sites-authoring/content-insights.md) van de console van Plaatsen om paginadoeltreffendheid verder te onderzoeken.

1. Selecteer in de Sites-console de pagina waarvoor u Inhoudsgegevens wilt weergeven.
1. Klik op het pictogram Analytics en Recommendations op de werkbalk.

   ![](do-not-localize/chlimage_1-16a.png)

## Analyses zichtbaar in de Pagina-editor (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!NOTE]
>
>Dit wordt weergegeven als de [Activity Map is geconfigureerd](/help/sites-administering/adobeanalytics-connect.md#configuring-for-the-activity-map) voor uw website.

>[!NOTE]
>
>Gegevens voor de Activity Map zijn afkomstig uit Adobe Analytics.

Wanneer uw website is [geconfigureerd voor Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md), kunt u de [modus Activity Map](/help/sites-authoring/author-environment-tools.md#page-modes) gebruiken om relevante gegevens weer te geven. Bijvoorbeeld:

![aa-07](assets/aa-07.png)

### Toegang tot de Activity Map {#accessing-the-activity-map}

Nadat u de modus [Activity Map](/help/sites-authoring/author-environment-tools.md#page-modes) hebt geselecteerd, wordt u gevraagd uw Adobe Analytics-referenties in te voeren.

![aa-03](assets/aa-03.png)

De zwevende werkbalk **Analytics** wordt weergegeven. hier kunt u :

* de werkbalkopmaak wijzigen met de dubbele pijlen (**>>**)
* Paginadetails in-/uitschakelen (oogpictogram)
* De Activity Map-instellingen configureren (cogopictogram)
* Selecteer de analysefunctie die u wilt weergeven (verschillende keuzelijsten)
* Sluit de Activity Map en sluit de werkbalk (x)

![aa-09](assets/aa-09.png)

### De te tonen Analytics selecteren {#selecting-the-analytics-to-show}

U kunt aan de hand van de verschillende criteria bepalen welke analysegegevens moeten worden weergegeven en hoe deze moeten worden weergegeven:

* **Standaard**/**Actief**

* gebeurtenistype
* gebruikersgroep
* **Luchtbellen**/**Verloop**/**Tussenruimers &amp; Gebruikers**/**Uit**

* periode

![aa-13](assets/aa-13.png)

### De Activity Map {#configuring-the-activity-map} configureren

Met het pictogram **Instellingen tonen** opent u het dialoogvenster **Activity Map-instellingen**.

![aa-04-1](assets/aa-04-1.png)

Het dialoogvenster **Activity Map-instellingen** biedt een reeks opties op drie tabbladen:

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

