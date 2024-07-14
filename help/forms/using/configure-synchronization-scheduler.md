---
title: De synchronisatieplanner configureren
description: Leer hoe u elementen kunt migreren en synchroniseren, synchronisatieplanner kunt configureren en mappen kunt gebruiken om elementen te rangschikken.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
exl-id: 34db1f76-ee40-4612-85da-22041e7560fb
solution: Experience Manager, Experience Manager Forms
feature: Workbench,Adaptive Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# De synchronisatieplanner configureren {#configuring-the-synchronization-scheduler}

Standaard wordt de synchronisatieplanner na elke 3 minuten uitgevoerd om alle elementen te synchroniseren die via LiveCycle Workbench 11 zijn gewijzigd en bijgewerkt in de opslagplaats. Toepassingen die formulieren en bronnen bevatten, zijn zichtbaar in de AEM Forms-gebruikersinterface nadat het synchronisatieproces is voltooid.

## Het interval van de synchronisatieplanner van de verandering {#change-interval-of-the-synchronization-scheduler}

Voer de volgende stappen uit om het interval van de synchronisatieplanner te veranderen:

1. Meld u aan bij AEM Configuratiebeheer. De URL van Configuration Manager is `https://'[server]:[port]'/lc/system/console/configMgr`

1. Bepaal en open de plaats **FormsManagerConfiguration** bundel.

1. Specificeer een nieuwe waarde voor de **optie van de Frequentie van de Planner van de Synchronisatie**.

   De eenheid van de frequentie is minuten. Bijvoorbeeld, om de planner te vormen om na elke 60 minuten te lopen, specificeer 60.

## Elementen synchroniseren {#synchronizing-assets}

U kunt **gebruiken synchroniseer Assets van de optie van de Bewaarplaats** om de activa manueel te synchroniseren. Voer de volgende stappen uit om de elementen handmatig te synchroniseren:

1. Meld u aan bij AEM Forms. De standaard-URL is `https://'[server]:[port]'/lc/aem/forms/` .

   ![ AEM Forms gebruikersinterface ](assets/aem_forms_ui.png)

   **Cijfer:** *gebruikersinterface van AEM Forms*

1. Klik het {](assets/aem6forms_sync.png) pictogram 0} aem6forms_sync in de toolbar. ![ Als u geen elementen hebt bij het laatste geconfigureerde pad, wordt het dialoogvenster weergegeven zoals hieronder. Klik **Begin** om de synchronisatie in werking te stellen.

   ![ de dialoogdoos van de Synchronisatie ](assets/migrate-and-syncronize.png)

   **Cijfer:** *de dialoogdoos van de Synchronisatie*

## Synchronisatiefout voor probleemoplossing {#troubleshooting-synchronization-error}

U kunt nieuwe toepassingen in de werkschemaontwerper (LiveCycle Workbench) tot stand brengen.

Als de onlangs gecreeerde toepassing en een omslag bij /content/dam/formsanddocuments identieke naam hebben, een fout &quot;*activa met de zelfde naam zoals deze toepassing bestaat reeds op wortelniveau.*&quot; is geregistreerd.

U lost het conflict op door de naam van de toepassing te wijzigen en de elementen handmatig te synchroniseren.

![ Conflicten in de dialoogdoos van de activasynchronisatie ](assets/sync-conflict.png)

**Cijfer:** *Conflicten in de dialoogdoos van de activasynchronisatie*
