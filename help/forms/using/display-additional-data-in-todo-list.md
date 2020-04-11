---
title: Extra gegevens weergeven in de lijst ToDo
seo-title: Extra gegevens weergeven in de lijst ToDo
description: Hoe kan ik de weergave van de lijst Te doen van LiveCycle AEM Forms-werkruimte aanpassen om meer informatie naast de standaardwerkruimte weer te geven.
seo-description: Hoe kan ik de weergave van de lijst Te doen van LiveCycle AEM Forms-werkruimte aanpassen om meer informatie naast de standaardwerkruimte weer te geven.
uuid: 9467c655-dce2-43ce-8e8f-54542fe81279
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: fed3b562-bcc2-4fb7-8fd2-35b1ac621e16
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Extra gegevens weergeven in de lijst ToDo{#displaying-additional-data-in-todo-list}

Standaard worden in de lijst Te doen van de werkruimte AEM-formulieren de naam en beschrijving van de taakweergave weergegeven. U kunt echter andere gegevens toevoegen, zoals de aanmaakdatum en de einddatum. U kunt ook pictogrammen toevoegen en de stijl van de weergave wijzigen.

![Een blik bij de Te doen lusje van de Werkruimte van HTML die standaardconfiguratie toont](assets/html-todo-list.png)

In dit artikel worden de stappen beschreven die moeten worden uitgevoerd om informatie toe te voegen die voor elke taak in de lijst AanDoe moet worden weergegeven.

## Wat kan worden toegevoegd {#what-can-be-added}

U kunt de informatie toevoegen die beschikbaar is in `task.json` verzending door de server. De informatie kan als gewone tekst worden toegevoegd of u kunt stijlen gebruiken om de informatie te formatteren.

Zie [dit](/help/forms/using/html-workspace-json-object-description.md) artikel voor meer informatie over de beschrijving van het JSON-object.

## Informatie weergeven over een taak {#displaying-information-on-a-task}

1. Voer de [algemene stappen uit voor het aanpassen](../../forms/using/generic-steps-html-workspace-customization.md)van de werkruimte van AEM Forms.
1. Om extra informatie voor een taak te tonen, moeten de overeenkomstige zeer belangrijk-waardeparen binnen het taakblok van worden toegevoegd `translation.json`.

   Bijvoorbeeld wijzigen `/apps/ws/locales/en-US/translation.json` voor Engels:

   ```
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >Voeg overeenkomstige sleutel-waarde paren voor alle gesteunde talen toe.

1. Voeg bijvoorbeeld informatie toe in het taakblok:

   ```
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## CSS definiëren voor de nieuwe eigenschap {#defining-css-for-the-new-property}

1. U kunt stijl toepassen op de informatie (eigenschap) die aan een taak is toegevoegd. Hiervoor moet u stijlinformatie toevoegen voor de nieuwe eigenschap die wordt toegevoegd aan `/apps/ws/css/newStyle.css`.

   Voeg bijvoorbeeld toe:

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## Item toevoegen in de HTML-sjabloon {#adding-entry-in-the-html-template}

Tot slot moet u een ingang in het dev pakket voor elk bezit omvatten dat u aan de taak wilt toevoegen. Om tot stand te brengen verwijs naar de code van de de werkruimte van de Vormen van AEM.

1. Kopiëren `task.html`:

   * from: `/libs/ws/js/runtime/templates/`
   * to: `/apps/ws/js/runtime/templates/`

1. Voeg de nieuwe informatie toe aan `/apps/ws/js/runtime/templates/task.html`.

   Voeg bijvoorbeeld toe onder `div class="taskProperties"`:

   ```
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```
