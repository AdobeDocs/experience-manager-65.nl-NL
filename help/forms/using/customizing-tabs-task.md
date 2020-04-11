---
title: Tabs aanpassen voor een taak
seo-title: Tabs aanpassen voor een taak
description: In de werkruimte LiveCycle AEM Forms kunt u de namen van de tabbladen voor uw taken aanpassen.
seo-description: In de werkruimte LiveCycle AEM Forms kunt u de namen van de tabbladen voor uw taken aanpassen.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Tabs aanpassen voor een taak {#customizing-tabs-for-a-task}

U kunt tabnamen voor de `Start Process` component aanpassen in de `Start Process` Uberweergave en de `Task Details` component in de `ToDo` Uberweergave.

1. Voer de [algemene stappen uit voor het aanpassen](/help/forms/using/generic-steps-html-workspace-customization.md)van de werkruimte van AEM Forms.
1. Wijzig de waarde van `tabname`in het `translation.json` bestand.

   Wijzig bijvoorbeeld `/apps/ws/locales/en-US/translation.json` voor Engels in het volgende.

   * Gebruik het volgende fragment uit het `"startprocess" : {}` blok voor taken die in het beginproces worden gestart.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Voor taken in te doen, gebruik het volgende fragment van het `"todo" : {}` blok.

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Voeg het corresponderende sleutel-waardepaar voor alle ondersteunde talen toe.
