---
title: De synchronisatieplanner configureren
description: Leer hoe u elementen kunt migreren en synchroniseren, synchronisatieplanner kunt configureren en mappen kunt gebruiken om elementen te rangschikken.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin
exl-id: 34db1f76-ee40-4612-85da-22041e7560fb
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# De synchronisatieplanner configureren {#configuring-the-synchronization-scheduler}

Standaard wordt de synchronisatieplanner na elke 3 minuten uitgevoerd om alle elementen te synchroniseren die via LiveCycle Workbench 11 zijn gewijzigd en bijgewerkt in de opslagplaats. Toepassingen die formulieren en bronnen bevatten, zijn zichtbaar in de AEM Forms-gebruikersinterface nadat het synchronisatieproces is voltooid.

## Het interval van de synchronisatieplanner van de verandering {#change-interval-of-the-synchronization-scheduler}

Voer de volgende stappen uit om het interval van de synchronisatieplanner te veranderen:

1. Meld u aan bij AEM Configuratiebeheer. De URL van Configuration Manager is `https://'[server]:[port]'/lc/system/console/configMgr`

1. Zoek en open de **FormsManagerConfiguration** bundel.

1. Geef een nieuwe waarde op voor de **Frequentie synchronisatieplanning** -optie.

   De eenheid van de frequentie is minuten. Bijvoorbeeld, om de planner te vormen om na elke 60 minuten te lopen, specificeer 60.

## Elementen synchroniseren {#synchronizing-assets}

U kunt de **Elementen synchroniseren vanuit gegevensopslagruimte** om de elementen handmatig te synchroniseren. Voer de volgende stappen uit om de elementen handmatig te synchroniseren:

1. Meld u aan bij AEM Forms. De standaard-URL is `https://'[server]:[port]'/lc/aem/forms/`.

   ![AEM Forms-gebruikersinterface](assets/aem_forms_ui.png)

   **Afbeelding:** *AEM Forms-gebruikersinterface*

1. Klik op de knop ![aem6forms_sync](assets/aem6forms_sync.png) in de werkbalk. Als u geen elementen hebt bij het laatste geconfigureerde pad, wordt het dialoogvenster weergegeven zoals hieronder. Klikken **Start** om de synchronisatie te starten.

   ![Synchronisatie, dialoogvenster](assets/migrate-and-syncronize.png)

   **Afbeelding:** *Synchronisatie, dialoogvenster*

## Synchronisatiefout voor probleemoplossing {#troubleshooting-synchronization-error}

U kunt nieuwe toepassingen in de werkschemaontwerper (LiveCycle Workbench) tot stand brengen.

Als de nieuwe toepassing en een map in /content/dam/formsanddocuments dezelfde naam hebben, wordt een fout &quot;*Middelen met dezelfde naam als deze toepassing bestaan al op hoofdniveau.*&quot; is geregistreerd.

U lost het conflict op door de naam van de toepassing te wijzigen en de elementen handmatig te synchroniseren.

![Conflicten in dialoogvenster voor synchronisatie van elementen](assets/sync-conflict.png)

**Afbeelding:** *Conflicten in dialoogvenster voor synchronisatie van elementen*
