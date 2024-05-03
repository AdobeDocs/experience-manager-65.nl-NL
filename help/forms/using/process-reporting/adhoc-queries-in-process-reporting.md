---
title: Ad hoc Vragen in Proces het Melden
description: Aangepaste query's maken om te zoeken naar AEM Forms in JEE-proces en taakdetails in Process Reporting
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: a096eea0-b2fb-4d86-b729-ca47611135b2
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 0%

---

# Ad hoc Vragen in Proces het Melden{#ad-hoc-queries-in-process-reporting}

## Ad-hocquery&#39;s in procesrapportage {#ad-hoc-queries-in-process-reporting-1}

Met ad-hocquery&#39;s in Process Reporting kunt u aangepaste query&#39;s maken die u kunt gebruiken om te zoeken naar proces- en taakdetails van de AEM Forms-procesinstanties die in uw AEM Forms-omgeving zijn gedefinieerd.

Ook, kunnen de ad hoc vragen worden bepaald gebruikend proces en de filters van het taakbezit. Deze filters kunnen vervolgens worden opgeslagen en gebruikt om de rapporten later uit te voeren.

[**Proceszoekopdracht**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-search-p): Zoek naar procesinstanties met een door de gebruiker gedefinieerd zoekfilter op basis van proceskenmerken.

[**Procesdetails**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-details-p): Bekijk details van een procesinstantie door de proces-id op te geven.

**Zoeken in taken**: Zoek naar taakinstanties met een door de gebruiker gedefinieerd zoekfilter op basis van taakkenmerken.

**Taakdetails**: Geef details van een taakinstantie weer door de taak-id op te geven.

### Processen en taken {#processes-and-tasks}

De stappen die u volgt om filters tot stand te brengen en vragen voor procesdetails in werking te stellen zijn het zelfde als dat voor taken.

Dit betekent dat de gebruikersinterface voor het Onderzoek van het Proces en het Onderzoek van de Taak slechts op de gebieden verschilt die u kunt zoeken door en de gebieden terugkomen in de onderzoeksresultaten. Dit komt omdat veel velden identiek zijn, maar bepaalde velden specifiek zijn voor processen en bepaalde velden specifiek zijn voor taken.

In dit artikel worden de beschrijvingen van de secties Zoeken/Taak en Proces/Taakdetails beschreven. Op aangewezen plaatsen, zullen om het even welke specifieke verschillen specifiek worden geroepen.

## Proces/taak zoeken {#process-task-search}

U gebruikt Proces/Taak Onderzoek om filters te bepalen voor het vragen van proces/taakinstanties.

### Een zoekquery voor proces/taak maken {#to-create-a-process-task-search-query}

1. Als u de opgeslagen zoekopdrachten voor proces/taak wilt weergeven of een query wilt maken, klikt u op **Ad-hocquery&#39;s** en klik vervolgens op **Proces/taak zoeken**.

   ![search_nodes](assets/search_nodes.png)

   De **Mijn filters** wordt rechts van de structuurweergave weergegeven.

   In de **Mijn filters** kunt u nieuwe ad-hocquery&#39;s maken en klikken om eerder opgeslagen query&#39;s uit te voeren.

   ![my_filters_panel](assets/my_filters_panel.png)

1. Als u een bestaande query wilt uitvoeren, klikt u gewoon op de query in het dialoogvenster **Mijn filters** deelvenster.
1. Klik op **Toevoegen** (+).

   De **Filter maken** wordt weergegeven.

   ![create_filter_panel](assets/create_filter_panel.png)

   Een query bestaat uit een of meer queryfilters. Als u een filter wilt maken, voegt u een filterrij toe aan de query. Standaard wordt één filterrij aan de query toegevoegd.

   **Een filter definiëren**

   1. Selecteer een veld.

      ![filter_field](assets/filter_field.png)

      >[!NOTE]
      >
      >De veldlijst bevat de velden die specifiek zijn voor AEM Forms-proces/-taak.

   1. Selecteer een voorwaarde.

      ![filter_condition](assets/filter_condition.png)

      >[!NOTE]
      >
      >De vermelde voorwaarden hangen van de attributen af die voor het filtreren wordt geselecteerd.

   1. Voer een waarde in.

      ![filter_value](assets/filter_value.png)

   1. Als u nog een filter aan de query wilt toevoegen, klikt u op **Toevoegen (+)** rechts van de filterrij.

      Als u een filter uit de query wilt verwijderen, klikt u op **Verwijderen (-)** rechts van de filterrij.

      ![filter_add_del](assets/filter_add_del.png)

Nadat u een query hebt gemaakt, gebruikt u de opties in de rechterbovenhoek van het dialoogvenster **Filter maken** paneel naar:

* **Annuleren**: Annuleer de wijzigingen en ga terug naar de **Mijn filters** deelvenster.
* **Uitvoeren**: Voer de huidige query uit om de resultaten te zien en/of te verifiëren. In dit geval hoeft u de query niet op te slaan voordat u de query uitvoert. U kunt de resultaten verifiëren, indien nodig wijzigingen aanbrengen en de query opslaan als u tevreden bent met de uitvoer.
* **Opslaan**: Sla het filter op. Het filter kan vervolgens worden weergegeven en uitgevoerd via het dialoogvenster **Mijn filters** deelvenster.

### Opties in het deelvenster Mijn filters {#options-in-my-filters-panel}

Gebruik de opties in het dialoogvenster **Mijn filters** van **Toevoegen** ![lc_pr_add_filter](assets/lc_pr_add_filter.png), **Bewerken** ![lc_pr_delete_filter](assets/lc_pr_delete_filter.png), of **Verwijderen** ![lc_pr_edit_filter](assets/lc_pr_edit_filter.png)een ad-hocquery.

![my_filters_options](assets/my_filters_options.png)

### Een zoekquery uitvoeren {#to-execute-a-search-query}

1. Als u een query wilt uitvoeren, klikt u op het filter in de **Mijn filters** of klik op **Uitvoeren** als u een filter maakt of bewerkt.
1. De resultaten van de vraagvertoning in **Rapport** van het **Procesrapportage** venster.

   ![process_search_result](assets/process_search_result.png)

   U kunt de onderzoeksresultaten met de hulp van het pagineringspaneel pagineren dat bij de bodem van het rapport wordt getoond.

   ![process_result_pgn](assets/process_result_pgn.png)

   In de **Weergave** kiest u het aantal resultaten dat per pagina moet worden weergegeven.

   In de **Pagina** typt, voert u een paginanummer in om rechtstreeks naar die pagina te gaan.

1. De volgende velden worden weergegeven in een zoekresultaat van het proces:

   * **Proces-id**: De id van het proces. Het veld is aan hyperlinks gekoppeld. Als u in dit veld op een proces-id klikt, wordt u doorgestuurd naar de **[!UICONTROL Process Details]** voor het proces.
   * **Initiator**: De AEM Forms-gebruiker die de procesinstantie heeft gestart
   * **Aanmaaktijd**: De datum en tijd waarop de procesinstantie is gestart
   * **Voltooide tijd**: De datum en tijd waarop de procesinstantie is voltooid
   * **Duur**: De duur van het begin tot aan de voltooiing van de procesinstantie
   * **Status**: De huidige status van de procesinstantie.

   Standaard wordt het resultaat gesorteerd op procesid. Als u het resultaat echter op een van de velden wilt sorteren, klikt u op de veldtitel.

   Aangezien het sorteren een knevelverrichting is, klik een kolomkopbal om het resultaat oplopend te sorteren en het opnieuw te klikken om aflopend te sorteren.

   Op dezelfde manier worden de volgende gebieden getoond in een Resultaat van het Onderzoek van de Taak:

   * **Taak-id**: De id van de taak. Het veld is aan hyperlinks gekoppeld. Als u in dit veld op een taak-id klikt, wordt u doorgestuurd naar de **[!UICONTROL Task Details]** voor de taak.
   * **Initiator**: De AEM Forms-gebruiker die de procesinstantie heeft gestart
   * **Aanmaaktijd**: De datum en tijd waarop de procesinstantie is gestart
   * **Voltooide tijd**: De datum en tijd waarop de procesinstantie is voltooid
   * **Duur**: De duur van het begin tot aan de voltooiing van de procesinstantie
   * **Status**: De huidige status van de procesinstantie.

   Standaard wordt het resultaat gesorteerd op Taak-id. Als u het resultaat echter op een van de velden wilt sorteren, klikt u op de veldtitel. Het resultaat wordt gesorteerd op de kolom die wordt aangegeven met een donkerdere pijl naast de kolomkop.

   Aangezien het sorteren een knevelverrichting is, klik een gebiedsheader om het resultaat oplopend te sorteren en het opnieuw te klikken om aflopend te sorteren. De huidige sorteervolgorde (oplopend/aflopend) wordt aangegeven door de richting van de donkere pijl naast de kolomkop.

   ![task_search_result](assets/task_search_result.png)

1. Klik op de knop Spoorstaaf ![lc_pr_rail_button](assets/lc_pr_rail_button.png) op de linkerbovenhoek om de **Mijn filters** en breidt de ruimte die beschikbaar is voor de **Rapport** deelvenster.
1. Gebruik de opties in de hogere juiste hoek van het **Rapport **paneel om verrichtingen op het vraagresultaat uit te voeren.

   * **Vernieuwen**: Hiermee vernieuwt u het rapport met de meest recente gegevens in de opslagruimte

   * **Exporteren naar CSV**: Exporteer de rapportgegevens naar een bestand met komma&#39;s als scheidingsteken.

   >[!NOTE]
   >
   >Wanneer u een rapport exporteert, wordt het volledige resultaat van de zoekopdracht geëxporteerd naar een CSV-bestand en niet alleen naar de huidige pagina

## Proces-/taakdetails {#process-task-details}

U gebruikt de **Procesdetails** om de details van een bepaald proces weer te geven.

Op dezelfde manier gebruikt u de opdracht **Taakdetails** om de details van een specifieke taak weer te geven.

### Proces-/taakdetails weergeven {#to-view-process-task-details}

U kunt de details van een specifiek AEM Forms-proces/een specifieke-taak bekijken:

* **Van een Proces/Taak het Resultaat**
* **Door de proces-/taak-id in te voeren in het deelvenster Proces/Taakdetails**

#### Van een Proces/Taak het Resultaat {#from-a-process-task-search-result}

1. Een proces-/taakzoekopdracht uitvoeren. Zie voor meer informatie [Een zoekquery voor proces uitvoeren](#to-execute-a-search-query).

   De proces-id&#39;s die in het resultaat worden weergegeven, zijn aan hyperlinks gekoppeld.

   ![process_id_list](assets/process_id_list.png)

1. Klik op een proces-id in de lijst om de details van dit proces te bekijken in het dialoogvenster **Procesdetails** deelvenster.

   De **Proces-/taakdetails** Het vraagresultaat toont details van de taken/de vormen bevat in het proces/de taak.

   Standaard wordt het resultaat gesorteerd op Taak-/Formulier-id. Als u het resultaat echter op een van de velden wilt sorteren, klikt u op de veldtitel. De kolom waarmee het resultaat wordt gesorteerd, wordt aangegeven met een donkerdere pijl naast de kolomkop.

   Aangezien het sorteren een knevelverrichting is, klik een gebiedsheader om het resultaat oplopend te sorteren en het opnieuw te klikken om aflopend te sorteren. De huidige sorteervolgorde (oplopend/aflopend) wordt aangegeven door de richting van de donkere pijl naast de kolomkop.

   **Resultaat van procesdetails**

   ![process_details](assets/process_details.png)

   **Deelvenster Links:** Geeft de volgende details van het geselecteerde proces weer:

   * Naam van het proces
   * Datum aanmaakdatum proces
   * Einddatum proces
   * Procesduur
   * Processtatus
   * Procesinitiator

   **Deelvenster rechtsboven:** Geeft de volgende details weer van de taken waaruit het geselecteerde proces bestaat:

   * Taak-id
   * Taaknaam
   * Taakeigenaar
   * Tijd van aanmaakdatum van taak
   * Tijdstip van update van taak
   * Einddatum taak
   * Taakduur
   * Taakstatus

   **Deelvenster Rechtsonder:** Geeft de volgende details van de procesgeschiedenis van het geselecteerde proces weer:

   * Procesnaam
   * Procesinitiator
   * Tijdstip van procesupdate
   * Einddatum proces
   * Processtatus

   **Resultaat taakdetails**

   ![task_details](assets/task_details.png)

   **Deelvenster Links:** Geeft de volgende details van de geselecteerde taak weer:

   * Taaknaam
   * Id van proces waartoe deze taak behoort
   * Taakbeschrijving
   * Tijd van aanmaakdatum van taak
   * Einddatum taak
   * Taakduur
   * Taakstatus
   * Geselecteerde taakroute

   **Deelvenster rechtsboven:** Hier worden de volgende details weergegeven van de formulieren waaruit de geselecteerde taak bestaat:

   * Foprm-id
   * Aanmaakdatum van formulier
   * Tijdstip van bijwerken van formulier
   * URL van formuliersjabloon

   **Deelvenster Rechtsonder:** Geeft de volgende details van de procesgeschiedenis van de geselecteerde taak weer:

   * Type taaktoewijzing
   * Taakeigenaar
   * Aanmaakdatum taak
   * Tijdstip van update van taak

1. Klikken **Terug naar zoeken in proces/taak** om terug te gaan naar het zoekresultaat waaruit de proces-/taakdetails zijn weggeboord.

   ![back_to_search](assets/back_to_search.png)

   Als de proces-/taakdetails echter zijn gevonden door een specifieke proces-/taak-id in te voeren, kunt u door op Terug naar zoeken in proces/taak te klikken, teruggaan naar **Proces/taak zoeken** zonder zoekresultaten weer te geven.

#### Door de proces-/taak-id in te voeren in het deelvenster Proces/Taakdetails {#by-entering-the-process-task-id-in-the-process-task-details-panel-br}

1. Ga naar de **Proces-/taakdetails** deelvenster.

   ![details_nodes](assets/details_nodes.png)

1. Voer in het tekstvak Proces/Taak-id de proces-/taak-id in.

   ![process_details-1](assets/process_details-1.png)

   De velden in het dialoogvenster **Proces-/taakdetails** Zoekresultaat zijn velden die specifiek zijn voor een AEM Forms-proces/-taak.

   Voor een proces, toont het vraagresultaat de details van de taken in het proces.

   Voor een taak, toont het vraagresultaat de details de vormen in de taak.
