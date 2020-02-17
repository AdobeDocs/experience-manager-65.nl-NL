---
title: AEM DS-instellingen configureren
seo-title: AEM DS-instellingen configureren
description: U moet de URL van de verwerkingsserver opgeven voordat u een formulier verzendt.
seo-description: U moet de URL van de verwerkingsserver opgeven voordat u een formulier verzendt.
uuid: 55a6d434-7352-48a8-8387-8a5c1a48fafc
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: a7387bd3-8b31-4bd0-a861-daa8f7cb2d05
docset: aem65
translation-type: tm+mt
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7

---


# AEM DS-instellingen configureren{#configuring-aem-ds-settings}

In dit artikel wordt beschreven hoe u **AEM DS Settings Service** configureert. Deze instelling kan in meerdere scenario&#39;s worden gebruikt, bijvoorbeeld:

* In het Correspondentenbeheer

   * Voor het configureren van AEM Forms Workflow
   * Tijdens het gebruik van de portal Formulieren voor het op afstand opslaan van concepten/verzenden

* In adaptieve formulieren voor gevallen waarin een adaptief formulier wordt ingediend vanuit een publicatie-instantie

Hier volgen de stappen voor het configureren van de **[!UICONTROL AEM DS-instellingen]**:

1. Open de Manager van de Configuratie op publiceer instantie gebruikend URL:\
   *https://localhost:port/system/console/configMgr*.

   ![Configuratie van AEM-webconsole](assets/web_configuration_console_new.png)

1. Zoek en klik in het venster Configuratie **[!UICONTROL webconsole van]** Adobe Experience Manager op de optie **[!UICONTROL AEM DS Settings]** .

   ![DS-instellingen](assets/ds_settings_new.png)

1. In het venster **[!UICONTROL AEM DS Settings Service]** worden de algemene configuratie-instellingen voor AEM DS Components weergegeven.

   ![DS Settings Service](assets/ds_settings_service_new.png)

1. Voeg de volgende informatie in de respectieve gebieden toe:

   **[!UICONTROL URL]** verwerkingsserver: De Verwerkingsserver is de server waarop de Forms of AEM-workflow moet worden geactiveerd. Dit kan gelijk zijn aan de URL van de AEM-auteurinstantie of de andere Server-URL (https://localhost:port/).

   **[!UICONTROL Gebruikersnaam]** server verwerken: Gebruikersnaam van workflowgebruiker [gebaseerd op de server-URL die wordt gebruikt]

   **[!UICONTROL Wachtwoord]** verwerkingsserver: Wachtwoord workflowgebruiker

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Wanneer u Forms of AEM-workflows gebruikt, voordat u een verzending vanaf de publicatieserver maakt, is het nodig de service DS-instellingen te configureren. Anders zal de indiening van het formulier mislukken.


