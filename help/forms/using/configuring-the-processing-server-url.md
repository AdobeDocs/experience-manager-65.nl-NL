---
title: AEM DS-instellingen configureren
description: Leer hoe u de URL van de verwerkingsserver opgeeft voordat u een formulier verzendt.
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
exl-id: c43cab7b-3421-4e1b-a834-b2dd6eb23c1d
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# AEM DS-instellingen configureren{#configuring-aem-ds-settings}

Dit artikel beschrijft hoe te om de **AEM DS Dienst van Montages te vormen**. Deze instelling kan in meerdere scenario&#39;s worden gebruikt, bijvoorbeeld:

* In het Correspondentenbeheer

   * Voor het configureren van de AEM Forms-workflow
   * Tijdens het gebruik van de Forms Portal voor het op afstand opslaan van concepten/verzendingen

* In adaptieve formulieren, voor gevallen waarin een adaptief formulier wordt ingediend vanuit een publicatie-instantie

Hier volgen de stappen voor het configureren van de **[!UICONTROL AEM DS Settings]** :

1. Open de Manager van de Configuratie op publiceer instantie gebruikend URL:\
   *https://localhost:port/system/console/configMgr*.

   ![ AEM de Configuratie van de Console van het Web ](assets/web_configuration_console_new.png)

1. Zoek in het **[!UICONTROL Adobe Experience Manager Web Console Configuration]** -venster de optie **[!UICONTROL AEM DS Settings]** en klik erop.

   ![ DS Montages ](assets/ds_settings_new.png)

1. In het **[!UICONTROL AEM DS Settings Service]** -venster worden de algemene configuratie-instellingen voor AEM DS-componenten weergegeven.

   ![ DS de Dienst van Montages ](assets/ds_settings_service_new.png)

1. Voeg de volgende informatie in de respectieve gebieden toe:

   **[!UICONTROL Processing Server URL]**: De Verwerkingsserver is de server waarop de Forms- of AEM-workflow moet worden geactiveerd. Dit kan het zelfde als URL van de AEM auteursinstantie of andere Server URL (namelijk https://localhost:port/) zijn.

   **[!UICONTROL Processing Server User Name]**: De Naam van de Gebruiker van het werkschema gebruiker [ gebaseerd op de server URL die wordt gebruikt ]

   **[!UICONTROL Processing Server Password]**: Wachtwoord workflowgebruiker

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Voordat u Forms- of AEM-workflows gebruikt, moet u de service voor DS-instellingen configureren voordat u gegevens van de publicatieserver verzendt. Anders zal de indiening van het formulier mislukken.
   >    
   >
