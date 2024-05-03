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
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# AEM DS-instellingen configureren{#configuring-aem-ds-settings}

In dit artikel wordt beschreven hoe u de **AEM DS Settings Service**. Deze instelling kan in meerdere scenario&#39;s worden gebruikt, bijvoorbeeld:

* In het Correspondentenbeheer

   * Voor het configureren van de AEM Forms-workflow
   * Tijdens het gebruik van de Forms Portal voor het op afstand opslaan van concepten/verzendingen

* In adaptieve formulieren, voor gevallen waarin een adaptief formulier wordt ingediend vanuit een publicatie-instantie

Hier volgen de stappen voor het configureren van de **[!UICONTROL AEM DS Settings]**:

1. Open de Manager van de Configuratie op publiceer instantie gebruikend URL:\
   *https://localhost:port/system/console/configMgr*.

   ![Webconsole-configuratie AEM](assets/web_configuration_console_new.png)

1. In de **[!UICONTROL Adobe Experience Manager Web Console Configuration]** venster, zoek en klik op de knop **[!UICONTROL AEM DS Settings]** -optie.

   ![DS-instellingen](assets/ds_settings_new.png)

1. De **[!UICONTROL AEM DS Settings Service]** toont de gemeenschappelijke configuratiemontages voor AEM DS Componenten.

   ![DS Settings Service](assets/ds_settings_service_new.png)

1. Voeg de volgende informatie in de respectieve gebieden toe:

   **[!UICONTROL Processing Server URL]**: De Verwerkingsserver is de server waarop de Forms- of AEM-workflow moet worden geactiveerd. Dit kan het zelfde als URL van de AEM auteursinstantie of andere Server URL (namelijk https://localhost:port/) zijn.

   **[!UICONTROL Processing Server User Name]**: Gebruikersnaam werkstroomgebruiker [gebaseerd op de server-URL die wordt gebruikt]

   **[!UICONTROL Processing Server Password]**: Wachtwoord workflowgebruiker

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Voordat u Forms- of AEM-workflows gebruikt, moet u de service voor DS-instellingen configureren voordat u gegevens van de publicatieserver verzendt. Anders zal de indiening van het formulier mislukken.
   >    
   >
