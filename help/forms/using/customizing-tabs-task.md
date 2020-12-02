---
title: Tabs aanpassen voor een taak
seo-title: Tabs aanpassen voor een taak
description: Hoe kan ik de namen van de tabbladen voor uw taken aanpassen in de werkruimte van LiveCycle AEM Forms.
seo-description: Hoe kan ik de namen van de tabbladen voor uw taken aanpassen in de werkruimte van LiveCycle AEM Forms.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Tabbladen aanpassen voor een taak {#customizing-tabs-for-a-task}

U kunt tabnamen voor de `Start Process` component aanpassen in de `Start Process` Uberweergave en de `Task Details` component in de `ToDo` Uberweergave.

1. Volg de [Algemene stappen voor de aanpassing van de AEM Forms-werkruimte](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Wijzig de waarde van `tabname`in het `translation.json`-bestand.

   Wijzig bijvoorbeeld `/apps/ws/locales/en-US/translation.json` voor Engels in het volgende.

   * Voor taken die in het beginproces in werking worden gesteld, gebruik het volgende fragment van het `"startprocess" : {}` blok.

   ```json
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Voor taken in te doen, gebruik het volgende fragment van het `"todo" : {}` blok.

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
