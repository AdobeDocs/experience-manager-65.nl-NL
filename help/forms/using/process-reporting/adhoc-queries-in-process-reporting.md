---
title: Ad hoc Vragen in Proces het Melden
seo-title: Ad hoc Vragen in Proces het Melden
description: Aangepaste query's maken om te zoeken naar AEM Forms in JEE-proces en taakdetails in Process Reporting
seo-description: Aangepaste query's maken om te zoeken naar AEM Forms in JEE-proces en taakdetails in Process Reporting
uuid: db0c5c28-b213-4582-a6ed-df127e570a4e
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b0a544e2-2ce4-48e2-a721-82f481d36004
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 0%

---


# Ad-hoc Vragen in Proces het Melden{#ad-hoc-queries-in-process-reporting}

## Ad-hocquery&#39;s in Process Reporting {#ad-hoc-queries-in-process-reporting-1}

Ad-hoc vragen in het Rapport van het Proces staan u toe om douanevragen tot stand te brengen die u kunt gebruiken om naar proces en taakdetails van de het procesinstanties van AEM Forms te zoeken die in uw milieu van AEM Forms worden bepaald.

Ook, kunnen de ad hoc vragen worden bepaald gebruikend proces en de filters van het taakbezit. Deze filters kunnen vervolgens worden opgeslagen en gebruikt om de rapporten later uit te voeren.

[**Proceszoekopdracht**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-search-p): Zoek naar procesinstanties met een user-defined onderzoeksfilter die op procesattributen wordt gebaseerd.

[**Procesdetails**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-details-p): Geef details van een procesinstantie weer door de proces-id op te geven.

**Taakzoekopdracht**: Zoek naar taakinstanties met een user-defined onderzoeksfilter die op taakattributen wordt gebaseerd.

**Taakdetails**: Geef details van een taakinstantie weer door de taak-id op te geven.

### Processen en taken {#processes-and-tasks}

De stappen die u volgt om filters tot stand te brengen en vragen voor procesdetails in werking te stellen zijn het zelfde als dat voor taken.

Dit betekent dat de gebruikersinterface voor het Onderzoek van het Proces en het Onderzoek van de Taak slechts op de gebieden verschilt die u kunt zoeken door en de gebieden terugkomen in de onderzoeksresultaten. Dit komt omdat veel velden identiek zijn, maar bepaalde velden specifiek zijn voor processen en bepaalde velden specifiek zijn voor taken.

In dit artikel worden de beschrijvingen van de secties Zoeken/Taak en Proces/Taakdetails beschreven. Op aangewezen plaatsen, zullen om het even welke specifieke verschillen specifiek worden geroepen.

## Zoeken in proces/taak {#process-task-search}

U gebruikt Proces/Taak Onderzoek om filters te bepalen voor het vragen van proces/taakinstanties.

### Om een vraag van het Proces/van het Onderzoek van de Taak te creëren {#to-create-a-process-task-search-query}

1. Om de opgeslagen vragen van het Proces/van het Onderzoek van de Taak te bekijken of een vraag tot stand te brengen, klik **Adhoc Vragen** en klik dan **Proces/Taak Onderzoek**.

   ![search_nodes](assets/search_nodes.png)

   Het deelvenster **Mijn filters** wordt rechts van de structuurweergave weergegeven.

   In **Mijn Filters** paneel, kunt u nieuwe ad hoc vragen tot stand brengen en klikken om eerder bewaarde vragen uit te voeren.

   ![my_filters_panel](assets/my_filters_panel.png)

1. Om een bestaande vraag uit te voeren, klikt u eenvoudig de vraag in **Mijn Filters** paneel.
1. Als u een query wilt maken, klikt u op **Toevoegen** (+).

   Het **Create Filter** paneel toont.

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

Nadat u een vraag creeert, gebruik de opties in de hogere juiste hoek van **Create Filter** paneel om:

* **Annuleren**: Annuleer de wijzigingen en ga terug naar het deelvenster  **Mijn** filter.
* **Uitvoeren**: Voer de huidige vraag uit om de resultaten te zien en/of te verifiëren. In dit geval hoeft u de query niet op te slaan voordat u de query uitvoert. U kunt de resultaten verifiëren, indien nodig wijzigingen aanbrengen en de query opslaan als u tevreden bent met de uitvoer.
* **Opslaan**: Sla het filter op. Het filter kan vervolgens worden weergegeven en uitgevoerd vanuit het deelvenster **Mijn filters**.

### Opties in het deelvenster Mijn filters {#options-in-my-filters-panel}

Gebruik de opties in het **Mijn filters** paneel aan **Add** ![lc_pr_add_filter](assets/lc_pr_add_filter.png), **Edit** ![lc_pr_delete_filter](assets/lc_pr_delete_filter.png) of **Delete** ![lc_pr_edit_filter](assets/lc_pr_edit_filter.png)een ad-hocquery.

![my_filters_options](assets/my_filters_options.png)

### Een zoekquery uitvoeren {#to-execute-a-search-query}

1. Als u een query wilt uitvoeren, klikt u op het filter in het deelvenster **Mijn filters** of klikt u op de knop **Uitvoeren** als u een filter maakt of bewerkt.
1. De resultaten van de vraagvertoning in **Report** paneel van **Process Reporting** venster.

   ![process_search_result](assets/process_search_result.png)

   U kunt de onderzoeksresultaten met de hulp van het pagineringspaneel pagineren dat bij de bodem van het rapport wordt getoond.

   ![process_result_pgn](assets/process_result_pgn.png)

   Kies in de vervolgkeuzelijst **Weergave** het aantal resultaten dat per pagina moet worden weergegeven.

   Voer in het tekstvak **Pagina** een paginanummer in om rechtstreeks naar die pagina te gaan.

1. De volgende velden worden weergegeven in een zoekresultaat van het proces:

   * **Proces-id**: De id van het proces. Het veld is aan hyperlinks gekoppeld. Als u in dit veld op een proces-id klikt, wordt u voor het proces omgeleid naar het deelvenster **[!UICONTROL Process Details]**.
   * **Initiator**: De AEM Forms-gebruiker die de procesinstantie heeft gestart
   * **Aanmaaktijd**: De datum en tijd waarop de procesinstantie is gestart
   * **Voltooide tijd**: De datum en tijd waarop de procesinstantie is voltooid
   * **Duur**: De duur van begin tot voltooiing van de procesinstantie
   * **Status**: De huidige status van de procesinstantie.

   Standaard wordt het resultaat gesorteerd op procesid. Als u het resultaat echter op een van de velden wilt sorteren, klikt u op de veldtitel.

   Aangezien het sorteren een knevelverrichting is, klik een kolomkopbal om het resultaat oplopend te sorteren en het opnieuw te klikken om aflopend te sorteren.

   Op dezelfde manier worden de volgende gebieden getoond in een Resultaat van het Onderzoek van de Taak:

   * **Taak-id**: De id van de taak. Het veld is aan hyperlinks gekoppeld. Als u in dit veld op een taak-id klikt, wordt u voor de taak omgeleid naar het deelvenster **[!UICONTROL Task Details]**.
   * **Initiator**: De AEM Forms-gebruiker die de procesinstantie heeft gestart
   * **Aanmaaktijd**: De datum en tijd waarop de procesinstantie is gestart
   * **Voltooide tijd**: De datum en tijd waarop de procesinstantie is voltooid
   * **Duur**: De duur van begin tot voltooiing van de procesinstantie
   * **Status**: De huidige status van de procesinstantie.

   Door gebrek, wordt het resultaat gesorteerd door identiteitskaart van de Taak. Als u het resultaat echter op een van de velden wilt sorteren, klikt u op de veldtitel. Het resultaat wordt gesorteerd op de kolom die wordt aangegeven met een donkerdere pijl naast de kolomkop.

   Aangezien het sorteren een knevelverrichting is, klik een gebiedsheader om het resultaat oplopend te sorteren en het opnieuw te klikken om aflopend te sorteren. De huidige sorteervolgorde (oplopend/aflopend) wordt aangegeven door de richting van de donkere pijl naast de kolomkop.

   ![task_search_result](assets/task_search_result.png)

1. Klik op de railknop ![lc_pr_rail_button](assets/lc_pr_rail_button.png) linksboven om het venster **Mijn filters** samen te vouwen en vergroot de ruimte die beschikbaar is voor het venster **Report**.
1. Gebruik de opties in de hogere juiste hoek van het **Rapport **paneel om verrichtingen op het vraagresultaat uit te voeren.

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen

   * **Exporteren naar CSV**: Exporteer de rapportgegevens naar een bestand met komma&#39;s als scheidingsteken.
   >[!NOTE]
   >
   >Wanneer u een rapport exporteert, wordt het volledige resultaat van de zoekopdracht geëxporteerd naar een CSV-bestand en niet alleen naar de huidige pagina

## Proces/taakdetails {#process-task-details}

U gebruikt **Procesdetails** paneel om de details van een specifiek proces te bekijken.

Op dezelfde manier gebruikt u **Taakdetails** paneel om de details van een specifieke taak te bekijken.

### Proces-/taakdetails weergeven {#to-view-process-task-details}

U kunt de details van een specifiek AEM Forms-proces/een specifieke-taak bekijken:

* **Van een Proces/Taak het Resultaat van het Onderzoek**
* **Door de proces-/taak-id in te voeren in het deelvenster Proces/Taakdetails**

#### Van een Proces/Taak het resultaat van het Onderzoek {#from-a-process-task-search-result}

1. Een proces-/taakzoekopdracht uitvoeren. Zie [Een zoekquery verwerken](#to-execute-a-search-query) uitvoeren voor meer informatie.

   De proces-id&#39;s die in het resultaat worden weergegeven, zijn aan hyperlinks gekoppeld.

   ![process_id_list](assets/process_id_list.png)

1. Klik op een proces-id in de lijst om de details van dit proces weer te geven in het **Procesdetails** deelvenster.

   Het **Proces/Taakdetails** vraagresultaat toont details van de taken/vormen in het proces/de taak.

   Standaard wordt het resultaat gesorteerd op Taak-/Formulier-id. Als u het resultaat echter op een van de velden wilt sorteren, klikt u op de veldtitel. De kolom waarmee het resultaat wordt gesorteerd, wordt aangegeven met een donkere pijl naast de kolomkop.

   Aangezien het sorteren een knevelverrichting is, klik een gebiedsheader om het resultaat oplopend te sorteren en het opnieuw te klikken om aflopend te sorteren. De huidige sorteervolgorde (oplopend/aflopend) wordt aangegeven door de richting van de donkere pijl naast de kolomkop.

   **Resultaat van procesdetails**

   ![process_details](assets/process_details.png)

   **Linkerpaneel:** geeft de volgende details van het geselecteerde proces weer:

   * Naam van het proces
   * Datum aanmaakdatum proces
   * Einddatum proces
   * Procesduur
   * Processtatus
   * Procesinitiator

   **Rechtsboven:** geeft de volgende details weer van de taken waaruit het geselecteerde proces bestaat:

   * Taak-id
   * Taaknaam
   * Taakeigenaar
   * Tijd van aanmaakdatum van taak
   * Tijdstip van update van taak
   * Einddatum taak
   * Taakduur
   * Taakstatus

   **Rechtsonder:** geeft de volgende details van de procesgeschiedenis van het geselecteerde proces weer:

   * Procesnaam
   * Procesinitiator
   * Tijdstip van procesupdate
   * Einddatum proces
   * Processtatus

   **Resultaat taakdetails**

   ![task_details](assets/task_details.png)

   **Linkerpaneel:** geeft de volgende details van de geselecteerde taak weer:

   * Taaknaam
   * Id van proces waartoe deze taak behoort
   * Taakbeschrijving
   * Tijd van aanmaakdatum van taak
   * Einddatum taak
   * Taakduur
   * Taakstatus
   * Geselecteerde taakroute

   **Rechtsboven:** geeft de volgende details weer van de formulieren waaruit de geselecteerde taak bestaat:

   * Foprm-id
   * Aanmaakdatum van formulier
   * Tijdstip van updatedatum van formulier
   * URL van formuliersjabloon

   **Rechtsonder:** geeft de volgende details van de procesgeschiedenis van de geselecteerde taak weer:

   * Type taaktoewijzing
   * Taakeigenaar
   * Aanmaakdatum taak
   * Tijdstip van update van taak






1. Klik **Terug naar Zoeken in proces/taak** om terug te keren naar het zoekresultaat waaruit de proces-/taakdetails zijn neergezet.

   ![back_to_search](assets/back_to_search.png)

   Als de proces-/taakdetails echter zijn gevonden door een specifieke proces-/taak-id in te voeren, kunt u terugkeren naar **Zoeken in proces/taak** zonder zoekresultaten weer te geven.

#### Door proces/Taak-id in te voeren in het deelvenster Proces/Taakdetails {#by-entering-the-process-task-id-in-the-process-task-details-panel-br}

1. Ga naar **Proces/Taakdetails** paneel.

   ![details_nodes](assets/details_nodes.png)

1. Voer in het tekstvak Proces/Taak-id de proces-/taak-id in.

   ![process_details-1](assets/process_details-1.png)

   De gebieden in **Proces/Taak Details** vraagresultaat zijn gebieden specifiek voor een proces/een taak van AEM Forms.

   Voor een proces, toont het vraagresultaat de details van de taken in het proces.

   Voor een taak, toont het vraagresultaat de details de vormen in de taak.
