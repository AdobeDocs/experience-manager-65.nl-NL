---
title: Werken met versies van inhoudspagina's
description: Maak, vergelijk en herstel versies van een pagina in Adobe Experience Manager.
exl-id: cb7a9da2-7112-4ef0-b1cf-211a7df93625
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 2%

---

# Werken met paginaversies{#working-with-page-versions}

Met Versioning maakt u een &quot;momentopname&quot; van een pagina op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:

* Maak een versie van een pagina.
* Een pagina herstellen naar een vorige versie, bijvoorbeeld:
   * om een wijziging die u hebt aangebracht in de pagina ongedaan te maken.
* Vergelijk de huidige versie van een pagina met een vorige versie:
   * om verschillen in de tekst en afbeeldingen te benadrukken.

## Een nieuwe versie maken {#creating-a-new-version}

U kunt een versie van uw bron maken op basis van:

* de [Tijdlijnrail](#creating-a-new-version-timeline)
* de [Maken](#creating-a-new-version-create-with-a-selected-resource) (wanneer een bron is geselecteerd)

### Nieuwe versie maken - tijdlijn {#creating-a-new-version-timeline}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina in [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de **Tijdlijn** kolom.
1. Klik op de pijlpunt bij het veld Opmerking om de opties weer te geven:

   ![Tijdlijn - Opslaan als versie](assets/screen-shot_2019-03-05at112335.png)

1. Selecteren **Opslaan als versie**.
1. Voer een **Label** en **Opmerking** indien nodig.

   ![Versie maken - label en opmerking toevoegen](assets/chlimage_1-42.png)

1. De nieuwe versie bevestigen met **Maken**.

   De informatie in de tijdlijn wordt bijgewerkt om de nieuwe versie aan te geven.

### Een nieuwe versie maken - Maken met een geselecteerde bron {#creating-a-new-version-create-with-a-selected-resource}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina in [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Selecteer de **Maken** van de werkbalk om het dialoogvenster te openen.
1. In het dialoogvenster kunt u een **Label** en **Opmerking**, indien nodig:

   ![Een label en opmerking invoeren](assets/screen_shot_2012-02-15at105050am.png)

1. De nieuwe versie bevestigen met **Maken**.

   De tijdlijn wordt geopend met de informatie die wordt bijgewerkt om de nieuwe versie aan te geven.

## Versies opnieuw installeren {#reinstating-versions}

Nadat u een versie van de pagina hebt gemaakt, kunt u een eerdere versie op verschillende manieren opnieuw installeren:

* de **Deze versie herstellen** van de [Tijdlijn](/help/sites-authoring/basic-handling.md#timeline) spoor

  Vorige versie van geselecteerde pagina opnieuw installeren.

* de **Herstellen** opties van boven [werkbalk Handelingen](/help/sites-authoring/basic-handling.md#actions-toolbar)

   * **Versie herstellen**

     Herstel versies van opgegeven pagina&#39;s in de momenteel geselecteerde map. Dit kan ook het herstellen van eerder verwijderde pagina&#39;s omvatten.

   * **Boom herstellen**

     Zet een versie van een volledige boom op een gespecificeerde datum en tijd opnieuw op; dit kan pagina&#39;s omvatten die eerder zijn geschrapt.

>[!NOTE]
>
>Wanneer u een pagina opnieuw invoegt, maakt de gemaakte versie deel uit van een nieuwe vertakking.
>
>Ter illustratie:
>
>1. Maak versies van een willekeurige pagina.
>1. De initiële labels en namen van versieknooppunten zijn 1.0, 1.1, 1.2 enzovoort.
>1. Zet de eerste versie opnieuw in, in dit geval 1.0.
>1. Maak opnieuw versies.
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

Deze methode kan worden gebruikt om versies van opgegeven pagina&#39;s in de huidige map te herstellen. Dit kan ook het herstellen van eerder verwijderde pagina&#39;s omvatten:

1. Navigeren naar en [selecteren](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources), de vereiste map.

1. Selecteren **Herstellen** vervolgens **Versie herstellen** vanaf boven [werkbalk Handelingen](/help/sites-authoring/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >Indien:
   >
   >* u één pagina hebt geselecteerd die nooit onderliggende pagina&#39;s heeft gehad,
   >* of geen van de pagina&#39;s in de map een versie heeft,
   >
   >Dan is de vertoning leeg aangezien er geen toepasselijke versies zijn.

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

Deze methode kan worden gebruikt om een versie van een boom op een gespecificeerde datum en tijd te herstellen; dit kan pagina&#39;s omvatten die eerder zijn geschrapt:

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

   ![Selecteer de versie die u wilt voorvertonen](assets/screen-shot_2019-03-05at112505-1.png)

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

   ![Paginaversies weergegeven - versie selecteren](assets/screen-shot_2019-03-05at112505-2.png)

1. Selecteren **Vergelijken met huidige**. De [pagina diff](/help/sites-authoring/page-diff.md) wordt geopend om de verschillen weer te geven.

## Timewarp {#timewarp}

Timewarp is een eigenschap die wordt ontworpen om het *gepubliceerd* staat van een pagina op specifieke tijden in het verleden.

>[!TIP]
>
>[Tijdverdraaiing kan ook worden gebruikt bij Startpagina&#39;s om een voorvertoning van de toekomst weer te geven](/help/sites-authoring/launches.md) wanneer AEM 6.5.10.0 of hoger wordt uitgevoerd.

Het maken van inhoud is een doorlopend en gezamenlijk proces. Het doel van Timewarp is auteurs toe te staan om de gepubliceerde website in tijd te volgen, om hen te helpen begrijpen hoe de inhoud is veranderd. Deze functie gebruikt de paginaversies om de status van de publicatieomgeving te bepalen:

* Het systeem zoekt naar de paginaversie die op het geselecteerde tijdstip actief was.
   * Deze paginaversie is gemaakt/geactiveerd *voor* het punt in tijd dat in Timewarp wordt geselecteerd.
* Wanneer u naar een pagina navigeert die is verwijderd, wordt deze ook weergegeven, zolang de oude versies van de pagina nog beschikbaar zijn in de opslagplaats.
* Als geen gepubliceerde versie wordt gevonden, dan keert Timewarp aan de huidige staat van de pagina op het auteursmilieu terug (om een fout/404 pagina te verhinderen, die het doorbladeren zou verhinderen).

### Tijdverdraaiing gebruiken {#using-timewarp}

Timewaring is een [mode](/help/sites-authoring/author-environment-tools.md#page-modes) van de pagina-editor. Om het te beginnen, eenvoudig schakelaar het zoals u een andere wijze.

1. Start de editor voor de pagina waarop u Tijdverdraaiing wilt starten en selecteer vervolgens **Timewarp** in de modusselectie.

   ![Selecteer Timewaring in de wijzeselectie](assets/wwpv-01.png)

1. Stel in het dialoogvenster een datum en tijd in en klik op **Datum instellen**. Als u geen tijd selecteert, wordt de huidige tijd als standaardwaarde genomen.

   ![Datum instellen](assets/wwpv-02.png)

1. De pagina wordt weergegeven op basis van de datumset. De modus Tijdlijn verdraaien wordt aangegeven via de blauwe statusbalk boven in het venster. Gebruik de koppelingen op de statusbalk om een nieuwe doeldatum of einddatum voor de tijdverdraaiingsmodus te selecteren.

   ![Indicator voor tijdwijziging](assets/wwpv-03.png)

### Beperkingen voor tijdwijziging {#timewarp-limitations}

Met Timewarp wordt het best geprobeerd een pagina op een geselecteerd punt in de tijd te reproduceren. Vanwege de complexiteit van het voortdurend ontwerpen van inhoud in AEM is dit echter niet altijd mogelijk. Deze beperkingen moeten in gedachten worden gehouden wanneer u Tijdverdraaiing gebruikt.

* **Tijdlijn verdraaien werkt op basis van gepubliceerde pagina&#39;s** - Tijdlijn verdraaien werkt alleen volledig als u de pagina eerder hebt gepubliceerd. Als dat niet het geval is, wordt de huidige pagina in de auteursomgeving weergegeven.
* **Timewaring gebruikt paginaversies** - Als u navigeert naar een pagina die is verwijderd of verwijderd uit de opslagplaats, wordt deze correct weergegeven als de oude versies van de pagina nog steeds beschikbaar zijn in de opslagplaats.
* **Verwijderde versies beïnvloeden Timewarp** - Als versies uit de opslagplaats worden verwijderd, kan Timewarp niet de juiste weergave tonen.

* **Timewarp is read-only** - U kunt de oude versie van de pagina niet bewerken. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, moet u dat handmatig doen met [terugzetten](#reverting-to-a-page-version).

* **Tijdlijn verdraaien is alleen gebaseerd op pagina-inhoud** - Als de elementen voor het renderen van de website zijn gewijzigd, verschilt de weergave van wat oorspronkelijk was, aangezien deze items niet zijn geversieerd in de repository. Dergelijke elementen zijn onder andere code, css, assets/images.

>[!CAUTION]
>
>Timewarp is ontworpen als een hulpmiddel om auteurs te helpen bij het begrijpen en creëren van hun inhoud. Het is niet bedoeld als controlelogboek of voor juridische doeleinden.
