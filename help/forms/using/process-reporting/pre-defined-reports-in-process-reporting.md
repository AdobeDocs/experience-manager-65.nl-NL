---
title: Vooraf gedefinieerde rapporten in procesrapportage
seo-title: Pre-defined reports in Process Reporting
description: Vraag naar AEM Forms over JEE-procesgegevens om rapporten te maken over langdurige processen, procesduur en workflowvolume
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: 704a8886-90ea-4793-a3fc-f998f878c928
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d93375e-ec37-4445-96ea-d315676787b4
docset: aem65
exl-id: 34e55676-6332-4616-aecc-bcc8cc1e8a29
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# Vooraf gedefinieerde rapporten in procesrapportage {#pre-defined-reports-in-process-reporting}

## Vooraf gedefinieerde rapporten in procesrapportage {#pre-defined-reports-in-process-reporting-1}

AEM Forms Process Reporting biedt de volgende mogelijkheden: *uit-van-de-doos* rapporten:

* **[Lange processen](#long-running-processes)**: Een rapport van alle AEM Forms-processen die meer dan een opgegeven tijd hebben geduurd om te worden voltooid
* **[Procesduur](#process-duration-report)**: Een rapport van een opgegeven AEM Forms-proces per tijdsduur
* **[Volume werkstroom](#workflow-volume-report)**: Een rapport van de lopende en voltooide instanties van gespecificeerd proces door datum

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

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur wijzigen**: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken

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

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur wijzigen**: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken

## Workflow Volume-rapport {#workflow-volume-report}

Het workflowvolutrapport geeft het aantal exemplaren van een AEM Forms-proces dat momenteel wordt uitgevoerd en voltooid, per kalenderdag weer.

### Om een rapport van het Volume van het Werkschema uit te voeren {#to-execute-a-workflow-volume-report}

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

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur wijzigen**: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken
