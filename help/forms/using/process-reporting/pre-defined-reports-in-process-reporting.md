---
title: Vooraf gedefinieerde rapporten in procesrapportage
description: Vraag naar AEM Forms over JEE-procesgegevens om rapporten te maken over langdurige processen, procesduur en workflowvolume
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: 34e55676-6332-4616-aecc-bcc8cc1e8a29
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# Vooraf gedefinieerde rapporten in procesrapportage {#pre-defined-reports-in-process-reporting}

## Vooraf gedefinieerde rapporten in procesrapportage {#pre-defined-reports-in-process-reporting-1}

AEM Forms Process Reporting biedt de volgende mogelijkheden: *uit-van-de-doos* rapporten:

* **[Lange processen](#long-running-processes)**: Een rapport van alle AEM Forms-processen die meer dan een opgegeven tijd hebben geduurd om te worden voltooid
* **[Procesduur](#process-duration-report)**: Een rapport van een opgegeven AEM Forms-proces per tijdsduur
* **[Volume werkstroom](#workflow-volume-report)**: Een rapport van de actieve en voltooide exemplaren van het opgegeven proces per datum

## Lange processen {#long-running-processes}

Het rapport Lange actieve processen geeft de AEM Forms-processen weer die meer dan een opgegeven tijd in beslag hebben genomen.

### Een lang lopend procesrapport uitvoeren {#to-execute-a-long-running-process-report}

1. Als u de lijst met vooraf gedefinieerde rapporten wilt weergeven in Process Reporting, gaat u naar het tabblad **Procesrapportage** boomstructuurweergave, klik op de knop **Rapporten** knooppunt.
1. Klik op de knop **Lange processen** rapportknooppunt.

   ![long_running_node](assets/long_running_node.png)

   Wanneer u een rapport selecteert, wordt **Rapportparameters** wordt rechts van de structuurweergave weergegeven.

   ![het paneel van parameters van het lang lopende procesrapport](assets/report_parameters_panel.png)

   Parameters:

   * **Duur** (*verplicht*): Geef een duur en tijdseenheid op. Alle AEM Forms-processen weergeven die langer dan de opgegeven duur zijn uitgevoerd.
   * **Gestart na** (*optioneel*): Selecteer een datum. Filter het rapport om procesinstanties weer te geven die na de opgegeven datum zijn gestart.
   * **Beginnen voor** (*optioneel*): Selecteer een datum. Filter het rapport om procesinstanties weer te geven die vóór de opgegeven datum zijn gestart.

1. Klikken **Ga** om het rapport uit te voeren.

   Het rapport wordt weergegeven in het dialoogvenster **Rapport** aan de rechterkant van het **Procesrapportage** venster.

   ![long_running_processes](assets/long_running_processes.png)

   Gebruik de opties in de rechterbovenhoek van het dialoogvenster **Rapport** om de volgende bewerkingen op het rapport uit te voeren.

   * **Vernieuwen**: Hiermee vernieuwt u het rapport met de meest recente gegevens in de opslagruimte
   * **De legenda wijzigen**: Selecteer en wijzig de kleur van de legenda van het rapport
   * **Exporteren naar CSV**: Exporteer en download de gegevens uit het rapport naar een bestand met komma&#39;s als scheidingsteken

## Rapport Procesduur  {#process-duration-report}

In het rapport Procesduur wordt het aantal instanties van een Forms-proces weergegeven op basis van het aantal dagen dat elke instantie is uitgevoerd.

### Een rapport over de procesduur uitvoeren {#to-execute-a-process-duration-report}

1. Als u de vooraf gedefinieerde rapporten wilt weergeven in Process Reporting, gaat u naar de **Procesrapportage** boomstructuurweergave, klik op de knop **Rapporten** knooppunt.
1. Klik op de knop **Procesduur** rapportknooppunt.

   ![process_duration_node](assets/process_duration_node.png)

   Wanneer u een rapport selecteert, wordt **Rapportparameters** wordt rechts van de structuurweergave weergegeven.

   ![het paneel van parameters van het lang lopende procesrapport](assets/process_duration_params.png)

   Parameters:

   * **Proces selecteren** (*verplicht*): Selecteer een AEM Forms-proces.

1. Klikken **Ga** om het rapport uit te voeren.

   Het rapport wordt weergegeven in het dialoogvenster **Rapport** rechts van het venster Procesrapportage.

   ![process_duration_report](assets/process_duration_report.png)

   Gebruik de opties in de rechterbovenhoek van het dialoogvenster **Rapport** om de volgende bewerkingen op het rapport uit te voeren.

   * **Vernieuwen**: Hiermee vernieuwt u het rapport met de meest recente gegevens in de opslagruimte
   * **De legenda wijzigen**: Selecteer en wijzig de kleur van de legenda van het rapport
   * **Exporteren naar CSV**: Exporteer en download de gegevens uit het rapport naar een bestand met komma&#39;s als scheidingsteken

## Workflow Volume-rapport {#workflow-volume-report}

Het workflowvolutrapport geeft het aantal exemplaren van een AEM Forms-proces dat momenteel wordt uitgevoerd en voltooid, per kalenderdag weer.

### Een workflowvolutrapport uitvoeren {#to-execute-a-workflow-volume-report}

1. Als u de vooraf gedefinieerde rapporten wilt weergeven in Process Reporting, gaat u naar de **Procesrapportage** boomstructuurweergave, klik op de knop **Rapporten** knooppunt.
1. Klik op de knop **Volume werkstroom** rapportknooppunt.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Wanneer u een rapport selecteert, wordt **Rapportparameters** wordt rechts van de structuurweergave weergegeven.

   ![het paneel van parameters van het lang lopende procesrapport](assets/workflow_volume_params.png)

   Parameters:

   * **Proces selecteren** (*verplicht*): Selecteer een AEM Forms-proces.

   * **Gestart na** (*optioneel*): Selecteer een datum. Filtert het rapport om procesinstanties te tonen die na de gespecificeerde datum begonnen zijn.

   * **Beginnen voor** (*optioneel*): Selecteer een datum. Filtert het rapport om procesinstanties te tonen die vóór de gespecificeerde datum begonnen.

1. Klikken **Ga** om het rapport uit te voeren.

   Het rapport wordt weergegeven in het dialoogvenster **Rapport** aan de rechterkant van het **Procesrapportage** venster.

   ![workflow_volume_rapport](assets/workflow_volume_report.png)

   Gebruik de opties in de rechterbovenhoek van het dialoogvenster **Rapport** om de volgende bewerkingen op het rapport uit te voeren.

   * **Vernieuwen**: Hiermee vernieuwt u het rapport met de meest recente gegevens in de opslagruimte
   * **De legenda wijzigen**: Selecteer en wijzig de kleur van de legenda van het rapport
   * **Exporteren naar CSV**: Exporteer en download de gegevens uit het rapport naar een bestand met komma&#39;s als scheidingsteken
