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
role: Beheerder
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# De synchronisatieplanner {#configuring-the-synchronization-scheduler} configureren

Standaard wordt de synchronisatieplanner na elke 3 minuten uitgevoerd om alle elementen te synchroniseren die via LiveCycle Workbench 11 zijn gewijzigd en bijgewerkt in de opslagplaats. Toepassingen die formulieren en bronnen bevatten, zijn zichtbaar in de AEM Forms-gebruikersinterface nadat het synchronisatieproces is voltooid.

## Het interval van de synchronisatieplanner {#change-interval-of-the-synchronization-scheduler} wijzigen

Voer de volgende stappen uit om het interval van de synchronisatieplanner te veranderen:

1. Meld u aan bij AEM Configuratiebeheer. De URL van Configuration Manager is `https://'[server]:[port]'/lc/system/console/configMgr`

1. Zoek en open de bundel **FormsManagerConfiguration**.

1. Geef een nieuwe waarde op voor de optie **Frequentie synchronisatieplanning**.

   De eenheid van de frequentie is minuten. Bijvoorbeeld, om de planner te vormen om na elke 60 minuten te lopen, specificeer 60.

## Elementen {#synchronizing-assets} synchroniseren

Met de optie **Elementen synchroniseren vanuit gegevensopslagruimte** kunt u de elementen handmatig synchroniseren. Voer de volgende stappen uit om de elementen handmatig te synchroniseren:

1. Meld u aan bij AEM Forms. De standaard-URL is `https://'[server]:[port]'/lc/aem/forms/`.

   ![AEM Forms-gebruikersinterface](assets/aem_forms_ui.png)

   **Afbeelding:** *AEM Forms-gebruikersinterface*

1. Klik op het pictogram ![aem6forms_sync](assets/aem6forms_sync.png) op de werkbalk. Als u geen elementen hebt bij het laatste geconfigureerde pad, wordt het dialoogvenster weergegeven zoals hieronder. Klik **Begin** om de synchronisatie in werking te stellen.

   ![Synchronisatie, dialoogvenster](assets/migrate-and-syncronize.png)

   **Afbeelding:** *Synchronisatie, dialoogvenster*

## Synchronisatiefout {#troubleshooting-synchronization-error} oplossen

U kunt nieuwe toepassingen maken in de werkstroomontwerper (LiveCycle Workbench).

Als de nieuwe toepassing en een map op /content/dam/formsanddocuments dezelfde naam hebben, treedt er een fout op &quot;*Er bestaat al een element met dezelfde naam als deze toepassing op het hoofdniveau.*&quot; is geregistreerd.

U lost het conflict op door de naam van de toepassing te wijzigen en de elementen handmatig te synchroniseren.

![Conflicten in dialoogvenster voor synchronisatie van elementen](assets/sync-conflict.png)

**Afbeelding:** *Conflicten in dialoogvenster voor middelensynchronisatie*
