---
title: Zoeken
seo-title: Zoeken
description: De auteursomgeving van AEM verstrekt diverse mechanismen om naar inhoud te zoeken, afhankelijk van het middeltype.
seo-description: De auteursomgeving van AEM verstrekt diverse mechanismen om naar inhoud te zoeken, afhankelijk van het middeltype.
uuid: 6dd3df4d-6040-4230-8373-fc028687b675
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8d32960c-47c3-4e92-b02e-ad4d8fea7b2d
docset: aem65
translation-type: tm+mt
source-git-commit: 4dc4a518c212555b7833ac27de02087a403d3517

---


# Zoeken{#searching}

De auteursomgeving van AEM verstrekt diverse mechanismen om naar inhoud te zoeken, afhankelijk van het middeltype.

>[!NOTE]
>
>Buiten de auteursomgeving zijn andere mechanismen ook beschikbaar voor het zoeken, zoals de Bouwer [van de](/help/sites-developing/querybuilder-api.md) Vraag en [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Grondbeginselen van zoekopdrachten {#search-basics}

U opent het deelvenster Zoeken door op het tabblad **Zoeken** boven in het linkerdeelvenster van de desbetreffende console te klikken.

![chlimage_1-101](assets/chlimage_1-101.png)

Met het deelvenster Zoeken kunt u al uw websitepagina&#39;s doorzoeken. Het bevat velden en widgets voor het volgende:

* **Fulltext**: Zoeken naar de opgegeven tekst
* **Gewijzigd na/voor**: Alleen de pagina&#39;s zoeken die zijn gewijzigd tussen de specifieke datums
* **Sjabloon**: Alleen die pagina&#39;s zoeken op basis van de opgegeven sjabloon
* **Tags**: Alleen de pagina&#39;s met de opgegeven tags doorzoeken

>[!NOTE]
>
>Wanneer uw instantie voor het onderzoek [van](/help/sites-deploying/queries-and-indexing.md) Lucene wordt gevormd kunt u het volgende in **Fulltext** gebruiken:
>
>* [Jokertekens](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Wildcard_Searches)
>* [Booleaanse operatoren](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boolean_operators)
   >
   >
* [Reguliere expressies](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Regexp_Searches)
>* [Veldgroepering](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Field_Grouping)
>* [Verhogen](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boosting_a_Term)
>



Voer de zoekopdracht uit door onder in het deelvenster op **Zoeken** te klikken. Klik op **Herstellen** om de zoekcriteria te wissen.

## Filter {#filter}

Op verschillende locaties kan een filter worden ingesteld (en gewist) om de weergave omlaag te doorlopen en te verfijnen:

![chlimage_1-102](assets/chlimage_1-102.png)

## Zoeken en vervangen {#find-and-replace}

In de **Websites** console staat een het menuoptie van de **Vondst &amp; van de Vervangen** u toe om naar, veelvoudige instanties van een koord, binnen een sectie van de website te zoeken en te vervangen.

1. Selecteer de hoofdpagina, of map, waar de zoek- en vervangactie moet plaatsvinden.
1. Selecteer **Gereedschappen** en **zoek en vervang**:

   ![screen_shot_2012-02-15at120346pm](assets/screen_shot_2012-02-15at120346pm.png)

1. Het dialoogvenster **Zoeken en vervangen** doet het volgende:

   * bevestigt het hoofdpad waar de zoekactie moet beginnen
   * definieert de term die moet worden gevonden
   * bepaalt de termijn die het moet vervangen
   * Hiermee wordt aangegeven of de zoekopdracht hoofdlettergevoelig moet zijn
   * Hiermee wordt aangegeven of alleen hele woorden moeten worden gevonden (anders worden ook subtekenreeksen gevonden)
   Als u op **Voorvertoning** klikt, wordt de term weergegeven. U kunt specifieke te vervangen exemplaren selecteren/wissen:

   ![screen_shot_2012-02-15at120719pm](assets/screen_shot_2012-02-15at120719pm.png)

1. Klik op **Vervangen** om alle exemplaren te vervangen. U wordt gevraagd de actie te bevestigen.

Het standaardwerkingsgebied voor het vondst en vervangt servlet behandelt de volgende eigenschappen:

* `jcr:title`
* `jcr:description`
* `jcr:text`
* `text`

Het bereik kan worden gewijzigd met de Apache Felix Web Management Console (bijvoorbeeld bij `https://localhost:4502/system/console/configMgr`). Selecteer `CQ WCM Find Replace Servlet (com.day.cq.wcm.core.impl.servlets.FindReplaceServlet)` en vorm het werkingsgebied zoals vereist.

>[!NOTE]
>
>In een standaardAEM installatie zoeken en vervangen gebruikt Lucene voor de onderzoeksfunctionaliteit.
>
>Lucene indexeert tekenreekseigenschappen met een lengte van maximaal 16 k. Tekenreeksen die dit overschrijden, worden niet doorzocht.
