---
title: Werken met paginaversies
seo-title: Werken met paginaversies
description: Met Versioning maakt u een "momentopname" van een pagina op een bepaald tijdstip.
seo-description: Met Versioning maakt u een "momentopname" van een pagina op een bepaald tijdstip.
uuid: 06e112cd-e4ae-4ee0-882d-7009f53ac85b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 48936115-4be2-4b0c-81ce-d61e43e4535d
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50

---


# Werken met paginaversies{#working-with-page-versions}

Met Versioning maakt u een &quot;momentopname&quot; van een pagina op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:

* Maak een versie van een pagina.
* Herstel een pagina naar een vorige versie om bijvoorbeeld een wijziging in een pagina ongedaan te maken.
* Vergelijk de huidige versie van een pagina met een vorige versie met verschillen in de gemarkeerde tekst en afbeeldingen.

## Een nieuwe versie maken {#creating-a-new-version}

Een nieuwe versie van een pagina maken:

1. Open in uw browser de pagina waarvoor u een nieuwe versie wilt maken.
1. Selecteer in de Sidetrap het tabblad **Versioning** en vervolgens het subtabblad **Versie** maken.

   ![screen_shot_2012-02-14at40259pm](assets/screen_shot_2012-02-14at40259pm.png)

1. Voer een **opmerking** in (optioneel).
1. Als u een label wilt instellen op de versie (optioneel), klikt u op de knop **Meer >>** en stelt u het **label** in om de versie een naam te geven. Als het label niet is ingesteld, wordt de versie automatisch verhoogd.
1. Klik op **Versie**maken. Er wordt een grijs bericht weergegeven op de pagina. bijvoorbeeld:
Versie 1.2 gemaakt voor: Hemden.

>[!NOTE]
>
>Er wordt automatisch een versie gemaakt wanneer de pagina wordt geactiveerd.

## Paginaversie herstellen vanaf Sidetrap {#restoring-a-page-version-from-sidekick}

De pagina herstellen naar een vorige versie:

1. Open de pagina waarvoor u een vorige versie wilt herstellen.
1. Selecteer in de assistent het tabblad **Versioning** en vervolgens het subtabblad **Versie** herstellen.

   ![screen_shot_2012-02-14at42949pm](assets/screen_shot_2012-02-14at42949pm.png)

1. Selecteer de versie die u wilt herstellen en selecteer **Herstellen**.

## Paginaversie herstellen vanuit de console {#restoring-a-page-version-from-the-console}

Deze methode kan worden gebruikt om een paginaversie te herstellen. Deze kan ook worden gebruikt om eerder verwijderde pagina&#39;s te herstellen:

1. Navigeer in de **websiteconsole** naar de pagina die u wilt herstellen en selecteer deze.
1. Selecteer in het bovenste menu **Gereedschappen** en **herstel**:

   ![screen_shot_2012-02-08at41326pm](assets/screen_shot_2012-02-08at41326pm.png)

1. **Versie** herstellen selecteren... Hiermee worden versies van documenten in de huidige map weergegeven. Zelfs als een pagina is verwijderd, wordt de laatste versie weergegeven:

   ![screen_shot_2012-02-08at45743pm](assets/screen_shot_2012-02-08at45743pm.png)

1. Selecteer de versie die u wilt herstellen en klik op **Herstellen**. De door u geselecteerde versie(s) (of bomen) worden hersteld.

### Een structuur herstellen vanuit de console {#restoring-a-tree-from-the-console}

Deze methode kan worden gebruikt om een paginaversie te herstellen. Deze kan ook worden gebruikt om eerder verwijderde pagina&#39;s te herstellen:

1. Navigeer in de **** websiteconsole naar de map die u wilt herstellen en selecteer deze.
1. Selecteer in het bovenste menu **Gereedschappen** en **herstel**.
1. **Structuur** herstellen selecteren... Hiermee opent u het dialoogvenster waarin u de structuur kunt selecteren die u wilt herstellen:

   ![screen_shot_2012-02-08at45743pm-1](assets/screen_shot_2012-02-08at45743pm-1.png)

1. Klik op **Herstellen**. De geselecteerde boomstructuur wordt hersteld.

## Vergelijken met een vorige versie {#comparing-with-a-previous-version}

De huidige versie van de pagina vergelijken met een vorige versie:

1. Open in uw browser de pagina die u met een vorige versie wilt vergelijken.
1. Selecteer in de Sidetrap het tabblad **Versioning** en vervolgens het subtabblad **Versie herstellen**.

   ![screen_shot_2012-02-14at42949pm-1](assets/screen_shot_2012-02-14at42949pm-1.png)

1. Selecteer de versie die u wilt vergelijken en klik op de knop **Diff** .
1. De verschillen tussen de huidige versie en de geselecteerde versie worden als volgt weergegeven:

   * Tekst die is verwijderd, is rood en doorgehaald.
   * De toegevoegde tekst is groen en gemarkeerd.
   * Afbeeldingen die zijn toegevoegd of verwijderd, zijn groene afbeeldingen.
   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Selecteer in de Sidetrap het subtabblad Versie **** herstellen en klik op de knop **&lt;&lt;Terug** om de huidige versie weer te geven.

## Timewarp {#timewarp}

Timewarp is een eigenschap die wordt ontworpen om de ***gepubliceerde*** staat van een pagina op specifieke tijden in het verleden te simuleren.

Het doel is om u toe te staan om de gepubliceerde website op het geselecteerde punt in tijd te volgen. Hiermee wordt de status van de publicatieomgeving bepaald aan de hand van de paginabactivering.

Dit doet u als volgt:

* Het systeem zoekt naar de paginaversie die op het geselecteerde tijdstip actief was.
* Dit betekent de getoonde versie werd gecreeerd/geactiveerd *vóór* het punt in tijd die in Timewarp wordt geselecteerd.
* Wanneer u naar een pagina navigeert die is verwijderd, wordt dit ook weergegeven, zolang de oude versies van de pagina nog beschikbaar zijn in de opslagplaats.
* Als geen gepubliceerde versie wordt gevonden, dan zal Timewarp aan de huidige staat van de pagina op het auteursmilieu terugkeren (dit moet een fout/404 pagina verhinderen, wat zou betekenen dat u niet meer kunt doorbladeren).

>[!NOTE]
>
>Als versies uit de dataopslag worden verwijderd, kan Timewarp niet de correcte mening tonen. Als elementen (zoals code, css, afbeeldingen, enz.) voor het renderen van de website zijn gewijzigd, zal de weergave ook verschillen van wat deze oorspronkelijk was, aangezien deze items niet zijn geversileerd in de opslagplaats.

### De tijdverdraaiingskalender gebruiken {#using-the-timewarp-calendar}

Timewarp is beschikbaar bij sidekick.

De kalenderversie wordt gebruikt als u een specifieke dag hebt om te bekijken:

1. Open het tabblad **Versioning** en klik vervolgens op **Tijdverdraaiing** (onder aan het zijpaneel). Het volgende dialoogvenster wordt weergegeven:

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Met de datum- en tijdkiezers geeft u de gewenste datum/tijd op en klikt u op **Ga**.

   Met Timewarp wordt de pagina weergegeven zoals deze was gepubliceerd vóór/op de datum die u hebt gekozen.

   >[!NOTE]
   >
   >Tijdlijnverdraaiing werkt alleen volledig als u de pagina eerder hebt gepubliceerd. Als dat niet het geval is, wordt de huidige pagina in de auteursomgeving weergegeven.

   >[!NOTE]
   >
   >Als u navigeert naar een pagina die is verwijderd of verwijderd uit de opslagplaats, wordt deze correct weergegeven als de oude versies van de pagina nog steeds beschikbaar zijn in de opslagplaats.

   >[!NOTE]
   >
   >U kunt de oude versie van de pagina niet bewerken. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, moet u dat handmatig doen met [terugzetten](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoring-a-page-version-from-sidekick).

1. Klik wanneer u de pagina hebt bekeken:

   * **Tijdlijn-verdraaiing** afsluiten om af te sluiten en terug te keren naar de huidige auteurspagina.
   * [Tijdlijn](#using-the-timewarp-timeline) tonen om de tijdlijn weer te geven.
   ![chlimage_1-77](assets/chlimage_1-77.png)

### De tijdlijn Tijdlijn Tijdlijn gebruiken {#using-the-timewarp-timeline}

De tijdlijnversie wordt gebruikt als u een overzicht wilt zien van de publicatieactiviteiten op de pagina.

Als u de tijdlijn van het document wilt weergeven:

1. U kunt de tijdlijn als volgt weergeven:

   1. Open het tabblad **Versioning** en klik vervolgens op **Tijdverdraaiing** (onder aan het zijpaneel).

   1. Gebruik het dialoogvenster sidekick dat wordt weergegeven na [gebruik van de tijdlijnkalender](#using-the-timewarp-calendar).

1. Klik op Tijdlijn **** tonen. De tijdlijn van het document wordt weergegeven. bijvoorbeeld:

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Selecteer en verplaats (houd ingedrukt en sleep) de tijdlijn om door de tijdlijn van het document te gaan.

   * Alle regels geven gepubliceerde versies aan.
Wanneer een pagina wordt geactiveerd, wordt een nieuwe regel gestart. Telkens wanneer het document wordt bewerkt, wordt er een nieuwe kleur weergegeven.
In het onderstaande voorbeeld geeft de rode lijn aan dat de pagina is bewerkt tijdens het tijdsbestek van de eerste groene versie en de gele lijn geeft aan dat de pagina ergens in de rode versie is bewerkt, enzovoort.
   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Klik:

   1. **Ga** naar om de inhoud van de gepubliceerde pagina op het geselecteerde tijdpunt weer te geven.
   1. Wanneer het tonen van die inhoud dan gebruik Tijdverdraaiing van de **Uitgang** om aan de huidige auteurspagina weg te gaan en terug te keren.

### Beperkingen voor tijdverdraaiing {#timewarp-limitations}

Met Timewarp wordt het best geprobeerd een pagina op een geselecteerd punt in de tijd te reproduceren. Vanwege de complexiteit van het voortdurend ontwerpen van inhoud in AEM is dit echter niet altijd mogelijk. Deze beperkingen moeten in gedachten worden gehouden wanneer u Tijdverdraaiing gebruikt.

* **Tijdlijnverdraaiing werkt op basis van gepubliceerde pagina** &#39;s. Tijdverdraaiing werkt alleen volledig als u de pagina eerder hebt gepubliceerd. Als dat niet het geval is, wordt de huidige pagina in de auteursomgeving weergegeven.
* **Time-warp gebruikt paginaversies** - Als u naar een pagina navigeert die is verwijderd of verwijderd uit de opslagplaats, wordt deze correct weergegeven als de oude versies van de pagina nog steeds beschikbaar zijn in de opslagplaats.
* **Verwijderde versies hebben invloed op Timewarp** - Als versies uit de opslagplaats worden verwijderd, kan Timewarp de juiste weergave niet weergeven.

* **Tijdlijnverdraaiing is alleen** -lezen - U kunt de oude versie van de pagina niet bewerken. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, moet u dat handmatig doen met [terugzetten](#main-pars-title-1).

* **De tijdverdraaiing is alleen gebaseerd op pagina-inhoud** . Als elementen (zoals code, css, assets/images, enz.) voor het renderen van de website zijn gewijzigd, verschilt de weergave van wat deze oorspronkelijk was, aangezien deze items niet zijn geversieerd in de opslagplaats.

>[!CAUTION]
>
>Timewarp is ontworpen als een hulpmiddel om auteurs te helpen bij het begrijpen en creëren van hun inhoud. Het is niet bedoeld als controlelogboek of voor juridische doeleinden.
