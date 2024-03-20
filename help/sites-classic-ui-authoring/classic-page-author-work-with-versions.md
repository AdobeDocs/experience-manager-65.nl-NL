---
title: Werken met paginaversies
description: Leer hoe u versies kunt maken en hoe u een momentopname van een pagina kunt maken op een bepaald tijdstip.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: 4eb0de5e-0306-4166-9cee-1297a5cd14ce
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 0%

---

# Werken met paginaversies{#working-with-page-versions}

Met Versioning maakt u een &quot;momentopname&quot; van een pagina op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:

* Maak een versie van een pagina.
* Herstel een pagina naar een vorige versie zodat u een wijziging die u hebt aangebracht in een pagina ongedaan kunt maken.
* Vergelijk de huidige versie van een pagina met een vorige versie met verschillen in de gemarkeerde tekst en afbeeldingen.

## Een versie maken {#creating-a-new-version}

Een versie van een pagina maken:

1. Open in uw browser de pagina waarvoor u een versie wilt maken.
1. Selecteer in de Sidekick de optie **Versioning** en vervolgens de **Versie maken** subtab.

   ![screen_shot_2012-02-14at40259pm](assets/screen_shot_2012-02-14at40259pm.png)

1. Voer een **Opmerking** (optioneel).
1. Als u een label wilt instellen op de versie (optioneel), klikt u op de knop **Meer >>** en stelt de **Label** om de versie een naam te geven. Als het label niet is ingesteld, wordt de versie automatisch verhoogd.
1. Klikken **Versie maken**. Er wordt een grijs bericht weergegeven op de pagina, bijvoorbeeld versie 1.2 die is gemaakt voor: Hemden.

>[!NOTE]
>
>Er wordt automatisch een versie gemaakt wanneer de pagina wordt geactiveerd.

## Paginaversie herstellen vanuit Sidekick {#restoring-a-page-version-from-sidekick}

De pagina herstellen naar een vorige versie:

1. Open de pagina waarvoor u een vorige versie wilt herstellen.
1. Selecteer in het zijpaneel de optie **Versioning** en vervolgens de **Versie herstellen** subtab.

   ![screen_shot_2012-02-14at42949pm](assets/screen_shot_2012-02-14at42949pm.png)

1. Selecteer de versie die u wilt herstellen en selecteer **Herstellen**.

## Paginaversie herstellen vanuit de console {#restoring-a-page-version-from-the-console}

Deze methode kan worden gebruikt om een paginaversie te herstellen. Deze kan ook worden gebruikt om eerder verwijderde pagina&#39;s te herstellen:

1. In de **Websites** navigeer naar de pagina die u wilt herstellen en selecteer deze.
1. Selecteer in het bovenste menu de optie **Gereedschappen** vervolgens **Herstellen**:

   ![screen_shot_2012-02-08at41326pm](assets/screen_shot_2012-02-08at41326pm.png)

1. Selecteren **Versie herstellen...** Hiermee worden versies van documenten in de huidige map weergegeven. Zelfs als een pagina is verwijderd, wordt de laatste versie weergegeven:

   ![screen_shot_2012-02-08at45743pm](assets/screen_shot_2012-02-08at45743pm.png)

1. Selecteer de versie die u wilt herstellen en klik op **Herstellen**. AEM herstelt de versies (of bomen) die u selecteert.

### Een structuur herstellen vanuit de console {#restoring-a-tree-from-the-console}

Deze methode kan worden gebruikt om een paginaversie te herstellen. Deze kan ook worden gebruikt om eerder verwijderde pagina&#39;s te herstellen:

1. In de **Websites** navigeer naar de map die u wilt herstellen en selecteer deze.
1. Selecteer in het bovenste menu de optie **Gereedschappen** vervolgens **Herstellen**.
1. Selecteren **Boom herstellen...** Hiermee opent u het dialoogvenster waarin u de structuur kunt selecteren die u wilt herstellen:

   ![screen_shot_2012-02-08at45743pm-1](assets/screen_shot_2012-02-08at45743pm-1.png)

1. Klikken **Herstellen**. AEM herstelt de structuur die u hebt geselecteerd.

## Vergelijken met een vorige versie {#comparing-with-a-previous-version}

De huidige versie van de pagina vergelijken met een vorige versie:

1. Open in uw browser de pagina die u met een vorige versie wilt vergelijken.
1. Selecteer in de Sidekick de optie **Versioning** en vervolgens de **Versie herstellen** n subtab.

   ![screen_shot_2012-02-14at42949pm-1](assets/screen_shot_2012-02-14at42949pm-1.png)

1. Selecteer de versie die u wilt vergelijken en klik op **Diff** knop.
1. De verschillen tussen de huidige versie en de geselecteerde versie worden als volgt weergegeven:

   * Tekst die is verwijderd, is rood en doorgehaald.
   * De toegevoegde tekst is groen en gemarkeerd.
   * Afbeeldingen die zijn toegevoegd of verwijderd, zijn groene afbeeldingen.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Selecteer in de Sidekick de optie **Versie herstellen** subtab en klik op de knop **&lt;&lt;back span=&quot;&quot; id=&quot;3&quot; translate=&quot;no&quot; /> om de huidige versie weer te geven.**

## Timewarp {#timewarp}

Timewarp is een eigenschap die wordt ontworpen om het ***gepubliceerd*** staat van een pagina op specifieke tijden in het verleden.

Het doel is om de gepubliceerde website op het geselecteerde tijdstip bij te houden. Hiermee wordt de status van de publicatieomgeving bepaald aan de hand van de paginabactivering.

Dit doet u als volgt:

* Het systeem zoekt naar de paginaversie die op het geselecteerde tijdstip actief was.
* Dit betekent dat de weergegeven versie is gemaakt/geactiveerd *voor* het punt in tijd dat in Timewarp wordt geselecteerd.
* Wanneer u naar een pagina navigeert die is verwijderd, wordt dit ook weergegeven, zolang de oude versies van de pagina nog beschikbaar zijn in de opslagplaats.
* Als geen gepubliceerde versie wordt gevonden, dan keert Timewarp aan de huidige staat van de pagina op het auteursmilieu terug (dit moet een fout/404 pagina verhinderen, wat zou betekenen dat u niet meer kunt doorbladeren).

>[!NOTE]
>
>Als versies uit de dataopslag worden verwijderd, kan Timewarp niet de correcte mening tonen. Als de elementen (zoals code, css en afbeeldingen) voor het renderen van de website zijn gewijzigd, verschilt de weergave ook van wat oorspronkelijk was, omdat deze items niet in de repository zijn geversileerd.

### De tijdverdraaiingskalender gebruiken {#using-the-timewarp-calendar}

Timewarp is beschikbaar bij sidekick.

De kalenderversie wordt gebruikt als u een specifieke dag hebt om te bekijken:

1. Open de **Versioning** en klik vervolgens op **Timewarp** (vlakbij de onderkant van het hulpje). Het volgende dialoogvenster wordt weergegeven:

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Met de datum- en tijdkiezers geeft u de gewenste datum/tijd op en klikt u op **Ga**.

   Met Tijdlijn verdraaien wordt de pagina weergegeven zoals deze was gepubliceerd vóór/op de datum die u hebt gekozen.

   >[!NOTE]
   >
   >Tijdlijn verdraaien werkt alleen volledig als u de pagina eerder hebt gepubliceerd. Als dat niet het geval is, wordt bij Timewarp de huidige pagina in de auteursomgeving weergegeven.

   >[!NOTE]
   >
   >Als u navigeert naar een pagina die is verwijderd of verwijderd uit de opslagplaats, wordt deze correct weergegeven als de oude versies van de pagina nog steeds beschikbaar zijn in de opslagplaats.

   >[!NOTE]
   >
   >U kunt de oude versie van de pagina niet bewerken. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, kunt u dat handmatig doen met [terugzetten](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoring-a-page-version-from-sidekick).

1. Klik op de volgende pagina als u de pagina hebt bekeken:

   * **Tijdlijnverdraaiing afsluiten** om af te sluiten en terug te keren naar de huidige auteurspagina.
   * [Tijdlijn tonen](#using-the-timewarp-timeline) zodat u de tijdlijn kunt bekijken.

   ![chlimage_1-77](assets/chlimage_1-77.png)

### De tijdlijn Tijdlijn Tijdlijn gebruiken {#using-the-timewarp-timeline}

De tijdlijnversie wordt gebruikt als u een overzicht wilt zien van de publicatieactiviteiten op de pagina.

Als u de tijdlijn van het document wilt weergeven:

1. Voer een van de volgende handelingen uit om de tijdlijn weer te geven:

   1. Open de **Versioning** en klikt u op **Timewarp** (vlakbij de onderkant van het hulpje).

   1. Het dialoogvenster sidekick gebruiken dat wordt weergegeven na [gebruiken van de Kalender Timewarp](#using-the-timewarp-calendar).

1. Klikken **Tijdlijn tonen** - de tijdlijn van het document wordt weergegeven, bijvoorbeeld:

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Selecteer en verplaats (houd ingedrukt en sleep) de tijdlijn om door de tijdlijn van het document te gaan.

   * Alle regels geven gepubliceerde versies aan.
Wanneer een pagina wordt geactiveerd, wordt een nieuwe regel gestart. Telkens wanneer het document wordt bewerkt, wordt er een nieuwe kleur weergegeven.
In het onderstaande voorbeeld geeft de rode lijn aan dat de pagina is bewerkt tijdens het tijdsbestek van de eerste groene versie. De gele lijn geeft aan dat de pagina ergens in de rode versie is bewerkt, enzovoort.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Klik:

   1. **Ga** om de inhoud van de gepubliceerde pagina op het geselecteerde tijdstip weer te geven.
   1. Gebruik bij het weergeven van die inhoud **Tijdlijnverdraaiing afsluiten** om af te sluiten en terug te keren naar de huidige auteurspagina.

### Beperkingen voor tijdwijziging {#timewarp-limitations}

Met Timewarp wordt het best geprobeerd een pagina op een geselecteerd punt in de tijd te reproduceren. Vanwege de complexiteit van het voortdurend ontwerpen van inhoud in AEM is dit echter niet altijd mogelijk. Deze beperkingen moeten in gedachten worden gehouden wanneer u Tijdverdraaiing gebruikt.

* **Tijdlijn verdraaien werkt op basis van gepubliceerde pagina&#39;s** - Tijdlijn verdraaien werkt alleen volledig als u de pagina eerder hebt gepubliceerd. Als dat niet het geval is, wordt bij Timewarp de huidige pagina in de auteursomgeving weergegeven.
* **Timewaring gebruikt paginaversies** - Als u navigeert naar een pagina die is verwijderd of verwijderd uit de opslagplaats, wordt deze correct weergegeven als de oude versies van de pagina nog steeds beschikbaar zijn in de opslagplaats.
* **Verwijderde versies beïnvloeden Timewarp** - Als versies uit de opslagplaats worden verwijderd, kan Timewarp niet de juiste weergave tonen.

* **Timewarp is read-only** - U kunt de oude versie van de pagina niet bewerken. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, kunt u dat handmatig doen met [terugzetten](#main-pars-title-1).

* **Tijdlijn verdraaien is alleen gebaseerd op pagina-inhoud** - Als elementen zoals code, css en afbeeldingselementen voor het renderen van de website zijn gewijzigd, verschilt de weergave van wat oorspronkelijk was. De reden hiervoor is dat deze items niet zijn geautoriseerd in de gegevensopslagruimte.

>[!CAUTION]
>
>Timewarp is ontworpen om auteurs te helpen bij het begrijpen en creëren van hun inhoud. Het is niet bedoeld als controlelogboek of voor juridische doeleinden.
