---
title: De synchronisatieplanner configureren
seo-title: De synchronisatieplanner configureren
description: Leer hoe u elementen kunt migreren en synchroniseren, synchronisatieplanner kunt configureren en mappen kunt gebruiken om elementen te rangschikken.
seo-description: Leer hoe u elementen kunt migreren en synchroniseren, synchronisatieplanner kunt configureren en mappen kunt gebruiken om elementen te rangschikken.
uuid: b2c89feb-2947-418a-b343-4c01e453602b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 8c8b1998-eab4-4230-b24f-5e96883ba599
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# De synchronisatieplanner configureren {#configuring-the-synchronization-scheduler}

Standaard wordt de synchronisatieplanner na elke 3 minuten uitgevoerd om alle elementen te synchroniseren die via LiveCycle Workbench 11 zijn gewijzigd en bijgewerkt in de opslagplaats. Toepassingen die formulieren en bronnen bevatten, zijn zichtbaar in de gebruikersinterface van AEM Forms zodra het synchronisatieproces is voltooid.

## Het interval van de synchronisatieplanner van de verandering {#change-interval-of-the-synchronization-scheduler}

Voer de volgende stappen uit om het interval van de synchronisatieplanner te veranderen:

1. Meld u aan bij AEM Configuration Manager. De URL van Configuration Manager is `https://'[server]:[port]'/lc/system/console/configMgr`

1. Zoek en open de bundel **FormsManagerConfiguration** .

1. Geef een nieuwe waarde op voor de optie **Synchronisatie-plannerfrequentie** .

   De eenheid van de frequentie is minuten. Bijvoorbeeld, om de planner te vormen om na elke 60 minuten te lopen, specificeer 60.

## Elementen synchroniseren {#synchronizing-assets}

Met de optie Elementen **synchroniseren vanuit opslagplaats** kunt u de elementen handmatig synchroniseren. Voer de volgende stappen uit om de elementen handmatig te synchroniseren:

1. Meld u aan bij AEM-formulieren. De standaard-URL is `https://'[server]:[port]'/lc/aem/forms/`.

   ![Gebruikersinterface AEM-formulieren](assets/aem_forms_ui.png)

   **Afbeelding:** Gebruikersinterface *voor AEM-formulieren*

1. Klik op het ![pictogram aem6forms_sync](assets/aem6forms_sync.png) op de werkbalk. Als u geen elementen hebt bij het laatste geconfigureerde pad, wordt het dialoogvenster weergegeven zoals hieronder. Klik op **Start** om de synchronisatie te starten.

   ![Synchronisatie, dialoogvenster](assets/migrate-and-syncronize.png)

   **Afbeelding:** Dialoogvenster *Synchronisatie*

## Synchronisatiefout voor probleemoplossing {#troubleshooting-synchronization-error}

U kunt nieuwe toepassingen maken in de workflowontwerper (LiveCycle Workbench).

Als de nieuwe toepassing en een map op het niveau /content/dam/formsanddocuments dezelfde naam hebben, wordt een fout &quot;*An asset with the same name as this application already exists at root level.*&quot; is geregistreerd.

U lost het conflict op door de naam van de toepassing te wijzigen en de elementen handmatig te synchroniseren.

![Conflicten in dialoogvenster voor synchronisatie van elementen](assets/sync-conflict.png)

**Afbeelding:** *Conflicten in dialoogvenster voor middelensynchronisatie*
