---
title: Vooraf gedefinieerde rapporten in procesrapportage
seo-title: Vooraf gedefinieerde rapporten in procesrapportage
description: Vraag naar AEM Forms voor JEE-procesgegevens om rapporten te maken over langdurige processen, procesduur en workflowvolume
seo-description: Vraag naar AEM Forms voor JEE-procesgegevens om rapporten te maken over langdurige processen, procesduur en workflowvolume
uuid: 704a8886-90ea-4793-a3fc-f998f878c928
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d93375e-ec37-4445-96ea-d315676787b4
docset: aem65
translation-type: tm+mt
source-git-commit: d9975c0dcc02ae71ac64aadb6b4f82f7c993f32c

---


# Vooraf gedefinieerde rapporten in procesrapportage {#pre-defined-reports-in-process-reporting}

## Vooraf gedefinieerde rapporten in procesrapportage {#pre-defined-reports-in-process-reporting-1}

AEM Forms Process Reporting biedt de volgende *out-of-the-box* -rapporten:

* **[Lange processen](#long-running-processes)**: Een rapport van alle processen van Vormen AEM die meer dan een gespecificeerde tijd kostten om te voltooien
* **[Tijdschema](#process-duration-report)**proces: Een rapport van een opgegeven AEM Forms-proces op duur
* **[Volume](#workflow-volume-report)**werkstroom: Een rapport van de lopende en voltooide instanties van gespecificeerd proces door datum

## Lange processen {#long-running-processes}

Het rapport Lange actieve processen geeft de AEM Forms-processen weer die meer dan een opgegeven tijd in beslag hebben genomen.

### Een lang lopend procesrapport uitvoeren {#to-execute-a-long-running-process-report}

1. Klik op het knooppunt **Rapporten ** **om de lijst met vooraf gedefinieerde rapporten in Process Reporting** weer te geven.
1. Klik op het rapportknooppunt **Lange actieve processen** .

   ![long_running_node](assets/long_running_node.png)

   Wanneer u een rapport selecteert, wordt het deelvenster **Rapportparameters** rechts van de structuurweergave weergegeven.

   ![het paneel van parameters van het lang lopende procesrapport](assets/report_parameters_panel.png)

   Parameters:

   * **Duur**(*verplicht*): Geef een duur en tijdseenheid op. Geef alle processen van AEM-formulieren weer die langer dan de opgegeven duur zijn uitgevoerd.
   * **Gestart na** (*optioneel*): Selecteer een datum. Filter het rapport om procesinstanties weer te geven die na de opgegeven datum zijn gestart.
   * **Gestart voor** (*optioneel*): Selecteer een datum. Filter het rapport om procesinstanties weer te geven die vóór de opgegeven datum zijn gestart.

1. Klik op **Ga** om het rapport uit te voeren.

   Het rapport toont in **Rapport **paneel op het recht van het venster van de Rapportering van het **Proces** .

   ![long_running_processes](assets/long_running_processes.png)

   Gebruik de opties in de hogere juiste hoek van het **Rapport **paneel om de volgende verrichtingen op het rapport uit te voeren.

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur** wijzigen: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken

## Rapport Procesduur {#process-duration-report}

In het rapport Procesduur wordt het aantal exemplaren van een Forms-proces weergegeven met het aantal dagen dat elke instantie is uitgevoerd.

### Een rapport over de procesduur uitvoeren {#to-execute-a-process-duration-report}

1. Om de vooraf bepaalde rapporten in het Melden van het Proces, over de de boommening van de **Rapportering** van het Proces te bekijken, klik de **Rapporten **knoop.
1. Klik de het rapportknoop van de Duur van **Processen** .

   ![process_duration_node](assets/process_duration_node.png)

   Wanneer u een rapport selecteert, wordt het deelvenster **Rapportparameters** rechts van de structuurweergave weergegeven.

   ![het paneel van parameters van het lang lopende procesrapport](assets/process_duration_params.png)

   Parameters:

   * **Proces selecteren **(*verplicht*): Selecteer een AEM-formulierproces.

1. Klik **Go **om het rapport uit te voeren.

   Het rapport toont in **Rapport **paneel op het recht van het venster van de Rapportering van het Proces.

   ![process_duration_report](assets/process_duration_report.png)

   Gebruik de opties in de hogere juiste hoek van het **Rapport **paneel om de volgende verrichtingen op het rapport uit te voeren.

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur** wijzigen: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken

## Workflow Volume-rapport {#workflow-volume-report}

Het rapport Workflow Volume geeft het aantal exemplaren van een AEM Forms-proces dat momenteel wordt uitgevoerd en voltooid, per kalenderdag weer.

### Om een rapport van het Volume van het Werkschema uit te voeren {#to-execute-a-workflow-volume-report}

1. Om de vooraf bepaalde rapporten in het Melden van het Proces, op de **Proces Meldend **boommening te bekijken, klik **Rapporten **knoop.
1. Klik op het rapportknooppunt **Workflowvolume** .

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Wanneer u een rapport selecteert, wordt het deelvenster **Rapportparameters** rechts van de structuurweergave weergegeven.

   ![het paneel van parameters van het lang lopende procesrapport](assets/workflow_volume_params.png)

   Parameters:

   * **Proces selecteren **(*verplicht*): Selecteer een AEM-formulierproces.

   * **Gestart na** (*optioneel*): Selecteer een datum. Filtert het rapport om procesinstanties te tonen die na de gespecificeerde datum begonnen zijn.

   * **Gestart voor** (*optioneel*): Selecteer een datum. Filtert het rapport om procesinstanties te tonen die vóór de gespecificeerde datum begonnen.

1. Klik **Go **om het rapport uit te voeren.

   Het rapport toont in **Rapport **paneel op het recht van het venster van de Rapportering van het **Proces** .

   ![workflow_volume_rapport](assets/workflow_volume_report.png)

   Gebruik de opties in de hogere juiste hoek van het **Rapport **paneel om de volgende verrichtingen op het rapport uit te voeren.

   * **Vernieuwen**: Verfrist het rapport met de recentste gegevens die in de opslag liggen
   * **De legendarische kleur** wijzigen: De kleur van de legenda van het rapport selecteren en wijzigen
   * **Exporteren naar CSV**: De gegevens van het rapport exporteren en downloaden naar een bestand met komma&#39;s als scheidingsteken

[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)
