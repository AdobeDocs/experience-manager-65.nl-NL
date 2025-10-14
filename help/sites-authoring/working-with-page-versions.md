---
title: Werken met versies van inhoudspagina's
description: Maak, vergelijk en herstel versies van een pagina in Adobe Experience Manager.
exl-id: cb7a9da2-7112-4ef0-b1cf-211a7df93625
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: d2e2f330dadb7c327324e53a17e8398ef3a473a9
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 2%

---

# Werken met paginaversies{#working-with-page-versions}

Met Versioning maakt u een &quot;momentopname&quot; van een pagina op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:

* Maak een versie van een pagina.
* Een pagina herstellen naar een vorige versie, bijvoorbeeld:
   * om een wijziging die u hebt aangebracht in de pagina ongedaan te maken.
* Vergelijk de huidige versie van een pagina met een vorige versie:
   * om verschillen in de tekst en afbeeldingen te benadrukken.

>[!NOTE]
>
>Alleen inhoud wordt versioned in de AEM-opslagplaats. Dynamische bronnen zoals code, CSS en JavaScript hebben geen versiebeheer.
>
>* Wanneer u versies weergeeft, wordt de inhoud weergegeven met de huidige code, CSS en JavaScript van de opslagplaats.
>* Bij het herstellen van versies wordt alleen de inhoud hersteld en worden de huidige code, CSS en JavaScript van de opslagplaats erop toegepast.

## Een nieuwe versie maken {#creating-a-new-version}

U kunt een versie van uw bron maken op basis van:

* het [&#x200B; spoor van de Chronologie &#x200B;](#creating-a-new-version-timeline)
* [&#x200B; creeer &#x200B;](#creating-a-new-version-create-with-a-selected-resource) optie (wanneer een middel wordt geselecteerd)

### Nieuwe versie maken - tijdlijn {#creating-a-new-version-timeline}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina op [&#x200B; selectiemodus &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de **kolom van de Chronologie**.
1. Klik op de pijlpunt bij het veld Opmerking om de opties weer te geven:

   ![&#x200B; Chronologie - sparen als Versie &#x200B;](assets/screen-shot_2019-03-05at112335.png)

1. Selecteer **sparen als Versie**.
1. Ga a **Etiket** en **Commentaar** indien nodig in.

   ![&#x200B; creeer Versie - voeg etiket en commentaar &#x200B;](assets/chlimage_1-42.png) toe

1. Bevestig de nieuwe versie met **creeer**.

   De informatie in de tijdlijn wordt bijgewerkt om de nieuwe versie aan te geven.

### Een nieuwe versie maken - Maken met een geselecteerde bron {#creating-a-new-version-create-with-a-selected-resource}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina op [&#x200B; selectiemodus &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Selecteer **creeer** optie van de toolbar om de dialoog te openen.
1. In de dialoogdoos, kunt u a **Etiket** en a **Commentaar** ingaan, indien nodig:

   ![&#x200B; ga een etiket en een commentaar &#x200B;](assets/screen_shot_2012-02-15at105050am.png) in

1. Bevestig de nieuwe versie met **creeer**.

   De tijdlijn wordt geopend met de informatie die wordt bijgewerkt om de nieuwe versie aan te geven.

## Versies opnieuw installeren {#reinstating-versions}

Nadat u een versie van de pagina hebt gemaakt, kunt u een eerdere versie op verschillende manieren opnieuw installeren:

* **keert aan deze optie van Versie** van de [&#x200B; Chronologie &#x200B;](/help/sites-authoring/basic-handling.md#timeline) spoor terug

  Vorige versie van geselecteerde pagina opnieuw installeren.

* **herstel** opties van de hoogste [&#x200B; actiestoolbar &#x200B;](/help/sites-authoring/basic-handling.md#actions-toolbar)

   * **herstelt Versie**

     Herstel versies van opgegeven pagina&#39;s in de momenteel geselecteerde map. Dit kan ook het herstellen van eerder verwijderde pagina&#39;s omvatten.

   * **herstelt Boom**

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

Om **terug te keren** de geselecteerde pagina aan een vorige versie:

1. Navigeer om de pagina weer te geven die u naar een vorige versie wilt terugkeren.
1. Selecteer de pagina op [&#x200B; selectiemodus &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**. De paginaversies voor de geselecteerde pagina worden weergegeven.
1. Selecteer de versie waarnaar u wilt terugkeren. De mogelijke opties worden weergegeven:

   ![&#x200B; keert aan deze Versie &#x200B;](assets/screen-shot_2019-03-05at112505.png) terug

1. Selecteer **terugkeren aan deze Versie**. De geselecteerde versie wordt hersteld en de informatie in de tijdlijn wordt bijgewerkt.

### Versie herstellen {#restore-version}

Deze methode kan worden gebruikt om versies van opgegeven pagina&#39;s in de huidige map te herstellen. Dit kan ook het herstellen van eerder verwijderde pagina&#39;s omvatten:

1. Navigeer aan, en [&#x200B; selecteer &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources), de vereiste omslag.

1. Selecteer **herstellen**, dan **herstelt Versie** van de hoogste [&#x200B; actiestoolbar &#x200B;](/help/sites-authoring/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >Indien:
   >
   >* u één pagina hebt geselecteerd die nooit onderliggende pagina&#39;s heeft gehad,
   >* of geen van de pagina&#39;s in de map een versie heeft,
   >
   >Dan is de vertoning leeg aangezien er geen toepasselijke versies zijn.

1. De beschikbare versies worden weergegeven:

   ![&#x200B; herstelt Versie - Lijst van alle pagina&#39;s in omslag &#x200B;](/help/sites-authoring/assets/versions-restore-version-01.png)

1. Voor een specifieke pagina, gebruik de drop-down selecteur onder **HERSTEL AAN VERSIE** om de vereiste versie voor die pagina te selecteren.

   ![&#x200B; herstelt Versie - Uitgezochte Versie &#x200B;](/help/sites-authoring/assets/versions-restore-version-02.png)

1. Selecteer in het hoofdscherm de pagina die u wilt herstellen:

   ![&#x200B; herstelt Versie - selecteer Pagina &#x200B;](/help/sites-authoring/assets/versions-restore-version-03.png)

1. Selecteer **Herstel** voor de geselecteerde versie, van de geselecteerde pagina, die als huidige versie moet worden hersteld.

>[!NOTE]
>
>De volgorde waarin u een vereiste pagina en de bijbehorende versie selecteert, is uitwisselbaar.

### Boom herstellen {#restore-tree}

Deze methode kan worden gebruikt om een versie van een boom op een gespecificeerde datum en tijd te herstellen; dit kan pagina&#39;s omvatten die eerder zijn geschrapt:

1. Navigeer aan, en [&#x200B; selecteer &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources), de vereiste omslag.

1. Selecteer **herstellen**, dan **herstellen Boom** van de hoogste [&#x200B; actiestoolbar &#x200B;](/help/sites-authoring/basic-handling.md#actions-toolbar). De meest recente versie van de boomstructuur wordt weergegeven:

   ![&#x200B; herstelt Boom &#x200B;](/help/sites-authoring/assets/versions-restore-tree-02.png)

1. Gebruik de datum en tijdselecteur bij **Latest Versies bij Datum** om een andere versie van de boom te selecteren - te herstellen.

1. Plaats de vlag **Bewaarde Niet Versioned Pagina&#39;s** zoals vereist:

   * Als deze optie actief is (geselecteerd), blijven niet-versioned pagina&#39;s behouden en worden deze niet beïnvloed door het terugzetten.

   * Als de optie inactief (niet geselecteerd) is, worden alle pagina&#39;s zonder versiebeheer verwijderd, omdat deze niet in de versiestructuur bestonden.

1. Selecteer **herstellen** voor de geselecteerde versie van de boom die als *huidige* versie moet worden hersteld.

## Een voorbeeld van een versie bekijken {#previewing-a-version}

U kunt een voorvertoning van een specifieke versie weergeven:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina op [&#x200B; selectiemodus &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt voorvertonen:

   ![&#x200B; selecteer de versie aan voorproef &#x200B;](assets/screen-shot_2019-03-05at112505-1.png)

1. Selecteer **Voorproef**. De pagina wordt weergegeven op een nieuw tabblad.

   >[!CAUTION]
   >
   >Als een pagina is verplaatst, kunt u geen voorvertoning meer weergeven van versies die vóór de verplaatsing zijn gemaakt.
   >
   >* Als u problemen met een voorproef ervaart, controleer de [&#x200B; Chronologie &#x200B;](/help/sites-authoring/basic-handling.md#timeline) voor de pagina om te zien of de pagina is bewogen.

## Een versie vergelijken met de huidige pagina {#comparing-a-version-with-current-page}

Een vorige versie vergelijken met de huidige pagina:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina op [&#x200B; selectiemodus &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt vergelijken:

   ![&#x200B; Versies van de Pagina vermeld - uitgezochte versie &#x200B;](assets/screen-shot_2019-03-05at112505-2.png)

1. Selecteer **vergelijken met Huidige**. Het [&#x200B; pagina diff &#x200B;](/help/sites-authoring/page-diff.md) opent om de verschillen te tonen.

## Timewarp {#timewarp}

De tijdverdraaiing is een eigenschap die wordt ontworpen om de *gepubliceerde* staat van een pagina op specifieke tijden in het verleden te simuleren.

>[!TIP]
>
>[&#x200B; Tijdverdraaiing kan ook met Lanceringen worden gebruikt om toekomstige &#x200B;](/help/sites-authoring/launches.md) te voorproef wanneer het runnen van AEM 6.5.10.0 of later.

Het maken van inhoud is een doorlopend en gezamenlijk proces. Het doel van Timewarp is auteurs toe te staan om de gepubliceerde website in tijd te volgen, om hen te helpen begrijpen hoe de inhoud is veranderd. Deze functie gebruikt de paginaversies om de status van de publicatieomgeving te bepalen:

* Het systeem zoekt naar de paginaversie die op het geselecteerde tijdstip actief was.
   * Deze paginaversie werd gecreeerd/geactiveerd *vóór* het punt in tijd die in Tijdverdraaiing wordt geselecteerd.
* Wanneer u naar een pagina navigeert die is verwijderd, wordt deze ook weergegeven, zolang de oude versies van de pagina nog beschikbaar zijn in de opslagplaats.
* Als geen gepubliceerde versie wordt gevonden, dan keert Timewarp aan de huidige staat van de pagina op het auteursmilieu terug (om een fout/404 pagina te verhinderen, die het doorbladeren zou verhinderen).

### Tijdverdraaiing gebruiken {#using-timewarp}

De tijdverdraaiing is a [&#x200B; wijze &#x200B;](/help/sites-authoring/author-environment-tools.md#page-modes) van de paginaredacteur. Om het te beginnen, eenvoudig schakelaar het zoals u een andere wijze.

1. Begin de redacteur voor de pagina waar u wenst om Timewarp te beginnen en dan **Timewarp** op de wijzeselectie te selecteren.

   ![&#x200B; Uitgezochte Tijdverdraaiing op de wijzeselectie &#x200B;](assets/wwpv-01.png)

1. In de dialoog, plaats een doeldatum en tijd en klik **Vastgestelde Datum**. Als u geen tijd selecteert, wordt de huidige tijd als standaardwaarde genomen.

   ![&#x200B; plaats Datum &#x200B;](assets/wwpv-02.png)

1. De pagina wordt weergegeven op basis van de datumset. De modus Tijdlijn verdraaien wordt aangegeven via de blauwe statusbalk boven in het venster. Gebruik de koppelingen op de statusbalk om een nieuwe doeldatum of einddatum voor de tijdverdraaiingsmodus te selecteren.

   ![&#x200B; de indicator van de Onderbreking &#x200B;](assets/wwpv-03.png)

### Beperkingen voor tijdwijziging {#timewarp-limitations}

Met Timewarp wordt het best geprobeerd een pagina op een geselecteerd punt in de tijd te reproduceren. Vanwege de complexiteit van het voortdurend ontwerpen van inhoud in AEM is dit echter niet altijd mogelijk. Deze beperkingen moeten in gedachten worden gehouden wanneer u Tijdverdraaiing gebruikt.

* **de werken van de Onderbreking van de Onderbreking die op gepubliceerde pagina&#39;s** worden gebaseerd - de Onderbreking werkt slechts volledig als u eerder de pagina hebt gepubliceerd. Als dat niet het geval is, wordt de huidige pagina in de auteursomgeving weergegeven.
* **Tijdverdraaiing gebruikt paginaversies** - als u aan een pagina navigeert die is verwijderd/geschrapt uit de bewaarplaats het behoorlijk teruggegeven als de oude versies van de pagina nog in de bewaarplaats beschikbaar zijn.
* **Verwijderde versies beïnvloeden Timewarp** - als de versies uit de bewaarplaats dan worden verwijderd kan de Timewarp niet de correcte mening tonen.

* **Tijdverdraaiing is read-only** - u kunt niet de oude versie van de pagina uitgeven. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, moet u dat manueel doen gebruikend [&#x200B; herstellen &#x200B;](#reverting-to-a-page-version).

* **Tijdverdraaiing is slechts gebaseerd op paginacontent** - als de elementen voor het teruggeven van de website zijn veranderd, verschilt de mening van wat het oorspronkelijk was, aangezien die punten niet in de bewaarplaats versioned zijn. Dergelijke elementen zijn onder andere code, css, assets/images.

>[!CAUTION]
>
>Timewarp is ontworpen als een hulpmiddel om auteurs te helpen bij het begrijpen en creëren van hun inhoud. Het is niet bedoeld als controlelogboek of voor juridische doeleinden.
