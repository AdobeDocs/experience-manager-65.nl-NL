---
title: Zoeken
description: De auteursomgeving van AEM verstrekt diverse mechanismen om naar inhoud te zoeken, afhankelijk van het middeltype.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 1f46a57f-4966-4dd1-8c99-c0740718ae76
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Zoeken{#searching}

De auteursomgeving van AEM verstrekt diverse mechanismen om naar inhoud te zoeken, afhankelijk van het middeltype.

>[!NOTE]
>
>Buiten de auteursomgeving zijn andere mechanismen ook beschikbaar voor het zoeken, zoals [Query Builder](/help/sites-developing/querybuilder-api.md) en [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Basisinformatie zoeken {#search-basics}

Als u het deelvenster Zoeken wilt openen, klikt u op de knop **Zoeken** aan de bovenkant van de linkerruit van de aangewezen console.

![chlimage_1-101](assets/chlimage_1-101.png)

Met het deelvenster Zoeken kunt u al uw websitepagina&#39;s doorzoeken. Het bevat velden en widgets voor het volgende:

* **Fulltext**: Zoeken naar de opgegeven tekst
* **Gewijzigd na/vóór**: Alleen de pagina&#39;s zoeken die zijn gewijzigd tussen de specifieke datums
* **Sjabloon**: Alleen die pagina&#39;s zoeken op basis van de opgegeven sjabloon
* **Tags**: Alleen de pagina&#39;s met de opgegeven tags zoeken

>[!NOTE]
>
>Wanneer uw instantie wordt gevormd voor [Lucene-zoekopdracht](/help/sites-deploying/queries-and-indexing.md) u kunt de volgende opties gebruiken in **Fulltext**:
>
>* [Jokertekens](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Wildcard_Searches)
>* [Booleaanse operatoren](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boolean_operators)
>
>* [Reguliere expressies](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Regexp_Searches)
>* [Veldgroepering](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Field_Grouping)
>* [Verhogen](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boosting_a_Term)
>

De zoekopdracht uitvoeren door op **Zoeken** onder aan het deelvenster. Klikken **Herstellen** de zoekcriteria te wissen.

## Filter {#filter}

Op verschillende locaties kan een filter worden ingesteld (en gewist) om de weergave omlaag te doorlopen en te verfijnen:

![chlimage_1-102](assets/chlimage_1-102.png)

## Zoeken en vervangen {#find-and-replace}

In de **Websites** console a **Zoeken en vervangen** met de menuoptie kunt u zoeken naar meerdere instanties van een tekenreeks in een sectie van de website en deze vervangen.

1. Selecteer de hoofdpagina, of map, waar de zoek- en vervangactie moet plaatsvinden.
1. Selecteren **Gereedschappen** dan **Zoeken en vervangen**:

   ![screen_shot_2012-02-15at120346pm](assets/screen_shot_2012-02-15at120346pm.png)

1. De **Zoeken en vervangen** wordt het volgende uitgevoerd:

   * bevestigt het hoofdpad waar de zoekactie moet beginnen
   * definieert de term die moet worden gevonden
   * bepaalt de termijn die het moet vervangen
   * Hiermee wordt aangegeven of de zoekopdracht hoofdlettergevoelig moet zijn
   * Hiermee wordt aangegeven of alleen hele woorden moeten worden gevonden (anders worden ook subtekenreeksen gevonden)

   Klikken **Voorvertoning** lijsten waarin de term is gevonden. U kunt specifieke te vervangen exemplaren selecteren/wissen:

   ![screen_shot_2012-02-15at120719pm](assets/screen_shot_2012-02-15at120719pm.png)

1. Klikken **Vervangen** om alle instanties daadwerkelijk te vervangen. U wordt gevraagd de actie te bevestigen.

Het standaardwerkingsgebied voor het vondst en vervangt servlet behandelt de volgende eigenschappen:

* `jcr:title`
* `jcr:description`
* `jcr:text`
* `text`

Het bereik kan worden gewijzigd met de Apache Felix Web Management Console (bijvoorbeeld bij `https://localhost:4502/system/console/configMgr`). Selecteren `CQ WCM Find Replace Servlet (com.day.cq.wcm.core.impl.servlets.FindReplaceServlet)` en configureer het bereik naar wens.

>[!NOTE]
>
>In een standaardinstallatie AEM vindt en vervangt het gebruik van Lucene voor de zoekfunctionaliteit.
>
>Lucene indexeert tekenreekseigenschappen met een lengte van maximaal 16 k. Tekenreeksen die dit overschrijden, worden niet doorzocht.
