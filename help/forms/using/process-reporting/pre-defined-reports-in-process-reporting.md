---
title: Vooraf gedefinieerde rapporten in procesrapportage
seo-title: Vooraf gedefinieerde rapporten in procesrapportage
description: Vraag naar AEM Forms over JEE-procesgegevens om rapporten te maken over langdurige processen, procesduur en workflowvolume
seo-description: Vraag naar AEM Forms over JEE-procesgegevens om rapporten te maken over langdurige processen, procesduur en workflowvolume
uuid: 704a8886-90ea-4793-a3fc-f998f878c928
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d93375e-ec37-4445-96ea-d315676787b4
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# Vooraf gedefinieerde rapporten in Process Reporting {#pre-defined-reports-in-process-reporting}

## Vooraf gedefinieerde rapporten in procesrapportage {#pre-defined-reports-in-process-reporting-1}

AEM Forms Process Reporting biedt de volgende *out-of-the-box*-rapporten:

* **[Lange processen](#long-running-processes)**: Een rapport van alle AEM Forms-processen die meer dan een opgegeven tijd hebben geduurd om te worden voltooid
* **[Tijdschema](#process-duration-report)** proces: Een rapport van een opgegeven AEM Forms-proces per tijdsduur
* **[Volume](#workflow-volume-report)** werkstroom: Een rapport van de lopende en voltooide instanties van gespecificeerd proces door datum

## Lange actieve processen {#long-running-processes}

Het rapport Lange actieve processen geeft de AEM Forms-processen weer die meer dan een opgegeven tijd in beslag hebben genomen.

### Een lang lopend procesrapport uitvoeren {#to-execute-a-long-running-process-report}

1. Als u de lijst met vooraf gedefinieerde rapporten in Process Reporting wilt weergeven, klikt u in de boomstructuurweergave **Process Reporting** op het knooppunt **Reports**.
1. Klik op het rapportknooppunt **Lange actieve processen**.

   ![long_running_node](assets/long_running_node.png)

   Wanneer u een rapport selecteert, wordt het **paneel van Parameters van het Rapport** getoond rechts van de boommening.

   ![het paneel van parameters van het lang lopende procesrapport](assets/report_parameters_panel.png)

   Parameters:

   * **Duur**  (*verplicht*): Geef een duur en tijdseenheid op. Alle AEM Forms-processen weergeven die langer dan de opgegeven duur zijn uitgevoerd.
   * **Gestart na**  (*optioneel*): Selecteer een datum. Filter het rapport om procesinstanties weer te geven die na de opgegeven datum zijn gestart.
   * **Gestart voor**  (*optioneel*): Selecteer een datum. Filter het rapport om procesinstanties weer te geven die vóór de opgegeven datum zijn gestart.

1. Klik **Go** om het rapport uit te voeren.

   Het rapport wordt weergegeven in het **Report**-deelvenster rechts van het venster **Process Reporting**.

   ![long_running_processes](assets/long_running_processes.png)

   Gebruik de opties in de hogere juiste hoek van **Report** paneel om de volgende verrichtingen op het rapport uit te voeren.

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur** wijzigen: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken

## Rapport over procesduur {#process-duration-report}

In het rapport Procesduur wordt het aantal instanties van een Forms-proces weergegeven op basis van het aantal dagen dat elke instantie is uitgevoerd.

### Een rapport {#to-execute-a-process-duration-report} over de procesduur uitvoeren

1. Als u de vooraf gedefinieerde rapporten in Process Reporting wilt weergeven, klikt u in de boomstructuurweergave **Process Reporting** op het knooppunt **Reports**.
1. Klik op het rapportknooppunt **Processes Duration**.

   ![process_duration_node](assets/process_duration_node.png)

   Wanneer u een rapport selecteert, wordt het **paneel van Parameters van het Rapport** getoond rechts van de boommening.

   ![het paneel van parameters van het lang lopende procesrapport](assets/process_duration_params.png)

   Parameters:

   * **Proces**  selecteren (*verplicht*): Selecteer een AEM Forms-proces.

1. Klik **Go** om het rapport uit te voeren.

   Het rapport toont in **Report** paneel op het recht van het venster van de Rapportering van het Proces.

   ![process_duration_report](assets/process_duration_report.png)

   Gebruik de opties in de hogere juiste hoek van **Report** paneel om de volgende verrichtingen op het rapport uit te voeren.

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur** wijzigen: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken

## Workflow Volume rapport {#workflow-volume-report}

Het workflowvolutrapport geeft het aantal exemplaren van een AEM Forms-proces dat momenteel wordt uitgevoerd en voltooid, per kalenderdag weer.

### Om een rapport van het Volume van het Werkschema {#to-execute-a-workflow-volume-report} uit te voeren

1. Als u de vooraf gedefinieerde rapporten in Process Reporting wilt weergeven, klikt u in de boomstructuurweergave **Process Reporting** op het knooppunt **Reports**.
1. Klik **Workflow Volume** rapportknooppunt.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Wanneer u een rapport selecteert, wordt het **paneel van Parameters van het Rapport** getoond rechts van de boommening.

   ![het paneel van parameters van het lang lopende procesrapport](assets/workflow_volume_params.png)

   Parameters:

   * **Proces**  selecteren (*verplicht*): Selecteer een AEM Forms-proces.

   * **Gestart na**  (*optioneel*): Selecteer een datum. Filtert het rapport om procesinstanties te tonen die na de gespecificeerde datum begonnen zijn.

   * **Gestart voor**  (*optioneel*): Selecteer een datum. Filtert het rapport om procesinstanties te tonen die vóór de gespecificeerde datum begonnen.

1. Klik **Go** om het rapport uit te voeren.

   Het rapport wordt weergegeven in het **Report**-deelvenster rechts van het venster **Process Reporting**.

   ![workflow_volume_rapport](assets/workflow_volume_report.png)

   Gebruik de opties in de hogere juiste hoek van **Report** paneel om de volgende verrichtingen op het rapport uit te voeren.

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur** wijzigen: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken
