---
title: Werken met paginaversies
seo-title: Working with Page Versions
description: Versies van een pagina maken, vergelijken en herstellen
seo-description: Create, compare, and restore versions of a page
uuid: 29e049f0-532c-4e3b-b64f-5be88ee6b08c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1368347a-9b65-4cfc-87e1-62993dc627fd
docset: aem65
exl-id: cb7a9da2-7112-4ef0-b1cf-211a7df93625
source-git-commit: b11a97b9b00e6f80fb0243e234ed1dc2c004ed3a
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 4%

---

# Werken met paginaversies{#working-with-page-versions}

Met Versioning maakt u een &quot;momentopname&quot; van een pagina op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:

* Maak een versie van een pagina.
* Herstel een pagina naar een vorige versie om bijvoorbeeld een wijziging in een pagina ongedaan te maken.
* Vergelijk de huidige versie van een pagina met een vorige versie met verschillen in de gemarkeerde tekst en afbeeldingen.

## Een nieuwe versie maken {#creating-a-new-version}

U kunt een versie van uw bron maken op basis van:

* de [Tijdlijnrail](#creating-a-new-version-timeline)
* de [Maken](#creating-a-new-version-create-with-a-selected-resource) (wanneer een bron is geselecteerd)

### Nieuwe versie maken - tijdlijn {#creating-a-new-version-timeline}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina in [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de **Tijdlijn** kolom.
1. Klik op de pijlpunt of tik op het veld Opmerking om de opties weer te geven:

   ![screen-shot_2019-03-05at112335](assets/screen-shot_2019-03-05at112335.png)

1. Selecteren **Opslaan als versie**.
1. Voer een **Label** en **Opmerking** indien nodig.

   ![chlimage_1-42](assets/chlimage_1-42.png)

1. De nieuwe versie bevestigen met **Maken**.

   De informatie in de tijdlijn wordt bijgewerkt om de nieuwe versie aan te geven.

### Een nieuwe versie maken - Maken met een geselecteerde bron {#creating-a-new-version-create-with-a-selected-resource}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina in [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Selecteer **Maken** van de werkbalk.
1. Het dialoogvenster wordt geopend. U kunt een **Label** en **Opmerking** indien vereist:

   ![screen_shot_2012-02-15at105050am](assets/screen_shot_2012-02-15at105050am.png)

1. De nieuwe versie bevestigen met **Maken**.

   De tijdlijn wordt geopend met de informatie die wordt bijgewerkt om de nieuwe versie aan te geven.

## Versies opnieuw installeren {#reinstating-versions}

Nadat u een versie van de pagina hebt gemaakt, kunt u een eerdere versie op verschillende manieren opnieuw installeren:

* de **Deze versie herstellen** van de [Tijdlijn](/help/sites-authoring/basic-handling.md#timeline) spoor

   Vorige versie van geselecteerde pagina opnieuw installeren.

* de **Herstellen** opties van boven [werkbalk Handelingen](/help/sites-authoring/basic-handling.md#actions-toolbar)

   * **Versie herstellen**

      Hiermee herstelt u versies van opgegeven pagina&#39;s in de geselecteerde map. dit kan ook het herstellen van pagina&#39;s omvatten die eerder zijn verwijderd.

   * **Boom herstellen**

      Zet een versie van een volledige boom op een gespecificeerde datum en tijd opnieuw op; hieronder kunnen pagina&#39;s vallen die eerder zijn verwijderd.

>[!NOTE]
>
>Wanneer u een pagina opnieuw invoegt, maakt de gemaakte versie deel uit van een nieuwe vertakking.
>
>Ter illustratie:
>
>1. Maak versies van een willekeurige pagina.
>1. De initiële labels en namen van versieknooppunten zijn 1.0, 1.1, 1.2 enzovoort.
>1. De eerste versie opnieuw installeren; d.w.z. 1.0.
>1. Maak opnieuw nieuwe versies.
>1. De gegenereerde labels en knooppuntnamen zijn nu 1.0.0, 1.0.1, 1.0.2 enzovoort.


### Versie herstellen {#revert-to-a-version}

Naar **Vorige versie** de geselecteerde pagina naar een vorige versie:

1. Navigeer om de pagina weer te geven die u naar een vorige versie wilt terugkeren.
1. Selecteer de pagina in [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**. De paginaversies voor de geselecteerde pagina worden weergegeven.
1. Selecteer de versie waarnaar u wilt terugkeren. De mogelijke opties worden weergegeven:

   ![Deze versie herstellen](assets/screen-shot_2019-03-05at112505.png)

1. Selecteren **Deze versie herstellen**. De geselecteerde versie wordt hersteld en de informatie in de tijdlijn wordt bijgewerkt.

### Versie herstellen {#restore-version}

Deze methode kan worden gebruikt om versies van opgegeven pagina&#39;s in de huidige map te herstellen. dit kan ook het herstellen van eerder verwijderde pagina&#39;s omvatten:

1. Navigeren naar en [selecteren](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources), de vereiste map.

1. Selecteren **Herstellen** vervolgens **Versie herstellen** vanaf boven [werkbalk Handelingen](/help/sites-authoring/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >Indien:
   >
   >* u één pagina hebt geselecteerd die nooit onderliggende pagina&#39;s heeft gehad,
   >* of geen van de pagina&#39;s in de map een versie heeft,

   >
   >Dan zal de vertoning leeg zijn aangezien er geen toepasselijke versies zijn.

1. De beschikbare versies worden weergegeven:

   ![Versie herstellen - Lijst met alle pagina&#39;s in map](/help/sites-authoring/assets/versions-restore-version-01.png)

1. Gebruik voor een specifieke pagina de keuzelijst onder **HERSTELLEN NAAR VERSIE** om de vereiste versie voor die pagina te selecteren.

   ![Versie herstellen - Versie selecteren](/help/sites-authoring/assets/versions-restore-version-02.png)

1. Selecteer in het hoofdscherm de pagina die u wilt herstellen:

   ![Versie herstellen - Pagina selecteren](/help/sites-authoring/assets/versions-restore-version-03.png)

1. Selecteren **Herstellen** voor de geselecteerde versie, van de geselecteerde pagina, terug te zetten als huidige versie.

>[!NOTE]
>
>De volgorde waarin u een vereiste pagina en de bijbehorende versie selecteert, is uitwisselbaar.

### Boom herstellen {#restore-tree}

Deze methode kan worden gebruikt om een versie van een boom op een gespecificeerde datum en tijd te herstellen; hieronder kunnen pagina&#39;s vallen die eerder zijn verwijderd:

1. Navigeren naar en [selecteren](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources), de vereiste map.

1. Selecteren **Herstellen** vervolgens **Boom herstellen** vanaf boven [werkbalk Handelingen](/help/sites-authoring/basic-handling.md#actions-toolbar). De meest recente versie van de boomstructuur wordt weergegeven:

   ![Boom herstellen](/help/sites-authoring/assets/versions-restore-tree-02.png)

1. De datum- en tijdkiezer gebruiken op **Laatste versies op datum** om een andere versie van de structuur te selecteren - de versie die moet worden hersteld.

1. Markering instellen **Bewaarde niet-versioned pagina&#39;s** indien vereist:

   * Als deze optie actief is (geselecteerd), blijven niet-versioned pagina&#39;s behouden en worden deze niet beïnvloed door het terugzetten.

   * Als de optie inactief (niet geselecteerd) is, worden alle pagina&#39;s zonder versiebeheer verwijderd, omdat deze niet in de versiestructuur bestonden.

1. Selecteren **Herstellen** voor de geselecteerde versie van de boomstructuur die moet worden hersteld als de *huidig* versie.

## Een voorbeeld van een versie bekijken {#previewing-a-version}

U kunt een voorvertoning van een specifieke versie weergeven:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina in [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt voorvertonen:

   ![screen-shot_2019-03-05at112505-1](assets/screen-shot_2019-03-05at112505-1.png)

1. Selecteren **Voorvertoning**. De pagina wordt weergegeven op een nieuw tabblad.

   >[!CAUTION]
   >
   >Als een pagina is verplaatst, kunt u geen voorvertoning meer weergeven van versies die vóór de verplaatsing zijn gemaakt.
   >
   >* Als u problemen ondervindt met een voorvertoning, controleert u de [Tijdlijn](/help/sites-authoring/basic-handling.md#timeline) om te zien of de pagina is verplaatst.


## Een versie vergelijken met de huidige pagina {#comparing-a-version-with-current-page}

Een vorige versie vergelijken met de huidige pagina:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina in [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt vergelijken:

   ![screen-shot_2019-03-05at112505-2](assets/screen-shot_2019-03-05at112505-2.png)

1. Selecteren **Vergelijken met huidige**. De [pagina diff](/help/sites-authoring/page-diff.md) opent en toont de verschillen.

## Timewarp {#timewarp}

Timewarp is een eigenschap die wordt ontworpen om het *gepubliceerd* staat van een pagina op specifieke tijden in het verleden.

>[!TIP]
>
>[Tijdverdraaiing kan ook worden gebruikt bij Startpagina&#39;s om een voorvertoning van de toekomst weer te geven](/help/sites-authoring/launches.md) wanneer AEM 6.5.10.0 of hoger wordt uitgevoerd.

Omdat content creation een doorlopend en gezamenlijk proces is, is het doel van Timewarp om auteurs in staat te stellen de gepubliceerde website in de loop van de tijd bij te houden om te begrijpen hoe de inhoud is gewijzigd. Deze functie gebruikt de paginaversies om de status van de publicatieomgeving te bepalen.

Dit doet u als volgt:

* Het systeem zoekt naar de paginaversie die op het geselecteerde tijdstip actief was.
* Dit betekent dat de weergegeven versie is gemaakt/geactiveerd *voor* het punt in tijd dat in Timewarp wordt geselecteerd.
* Wanneer u naar een verwijderde pagina navigeert, wordt deze ook weergegeven, zolang de oude versies van de pagina nog beschikbaar zijn in de opslagplaats.
* Als geen gepubliceerde versie wordt gevonden, dan zal Timewarp aan de huidige staat van de pagina op het auteursmilieu terugkeren (dit is om een fout/404 pagina te verhinderen, die het doorbladeren zou verhinderen).

### Tijdverdraaiing gebruiken {#using-timewarp}

Timewaring is een [mode](/help/sites-authoring/author-environment-tools.md#page-modes) van de pagina-editor. Om het te beginnen, eenvoudig schakelaar het zoals u een andere wijze.

1. Start de editor voor de pagina waarop u Tijdverdraaiing wilt starten en selecteer vervolgens **Timewarp** in de modusselectie.

   ![wwpv-01](assets/wwpv-01.png)

1. Stel in het dialoogvenster een doeldatum en -tijd in en klik of tik op **Datum instellen**. Als u geen tijd selecteert, wordt de huidige tijd standaard ingesteld.

   ![wwpv-02](assets/wwpv-02.png)

1. De pagina wordt weergegeven op basis van de datumset. De modus Tijdlijn verdraaien wordt aangegeven via de blauwe statusbalk boven in het venster. Gebruik de koppelingen op de statusbalk om een nieuwe doeldatum of einddatum voor de tijdverdraaiingsmodus te selecteren.

   ![wwpv-03](assets/wwpv-03.png)

### Beperkingen voor tijdverdraaiing {#timewarp-limitations}

Met Timewarp wordt het best geprobeerd een pagina op een geselecteerd punt in de tijd te reproduceren. Vanwege de complexiteit van het voortdurend ontwerpen van inhoud in AEM is dit echter niet altijd mogelijk. Deze beperkingen moeten in gedachten worden gehouden wanneer u Tijdverdraaiing gebruikt.

* **Tijdlijn verdraaien werkt op basis van gepubliceerde pagina&#39;s** - Tijdlijn-verdraaiing werkt alleen volledig als u de pagina eerder hebt gepubliceerd. Als dat niet het geval is, wordt de huidige pagina in de auteursomgeving weergegeven.
* **Timewaring gebruikt paginaversies** - Als u navigeert naar een pagina die is verwijderd of verwijderd uit de opslagplaats, wordt deze correct weergegeven als de oude versies van de pagina nog steeds beschikbaar zijn in de opslagplaats.
* **Verwijderde versies beïnvloeden Timewarp** - Als versies uit de opslagplaats worden verwijderd, kan Timewarp niet de juiste weergave tonen.

* **Timewarp is read-only** - U kunt de oude versie van de pagina niet bewerken. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, moet u dat handmatig doen met [terugzetten](#reverting-to-a-page-version).

* **Tijdlijn verdraaien is alleen gebaseerd op pagina-inhoud** - Als elementen (zoals code, css, assets/images, enz.) voor het renderen van de website zijn gewijzigd, zal de weergave afwijken van wat oorspronkelijk het geval was, aangezien deze items niet zijn geversieerd in de opslagplaats.

>[!CAUTION]
>
>Timewarp is ontworpen als een hulpmiddel om auteurs te helpen bij het begrijpen en creëren van hun inhoud. Het is niet bedoeld als controlelogboek of voor juridische doeleinden.
