---
title: Tabs aanpassen voor een taak
description: Hoe kan ik de namen van de tabbladen voor uw taken aanpassen in de werkruimte van LiveCycle AEM Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 8412cfec-bcab-40b7-9e5b-fcc211d43c0b
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Tabs aanpassen voor een taak {#customizing-tabs-for-a-task}

U kunt tabnamen aanpassen voor de `Start Process` in de `Start Process` De Uberweergave en de `Task Details` in de `ToDo` Uberweergave.

1. Volg de [Algemene stappen voor aanpassing van de AEM Forms-werkruimte](/help/forms/using/generic-steps-html-workspace-customization.md).
1. De waarde wijzigen van `tabname`in de `translation.json` bestand.

   Bijvoorbeeld, wijzigen `/apps/ws/locales/en-US/translation.json` voor Engels naar het volgende.

   * Voor taken die in het beginproces worden gestart, gebruikt u het volgende fragment uit het dialoogvenster `"startprocess" : {}` blokkeren.

   ```json
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Voor taken in Te-doen, gebruik het volgende fragment van `"todo" : {}` blokkeren.

   ```json
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
