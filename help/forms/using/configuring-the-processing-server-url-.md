---
title: AEM DS-instellingen configureren
seo-title: Configuring AEM DS settings
description: U moet de URL van de verwerkingsserver opgeven voordat u een formulier verzendt.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 55a6d434-7352-48a8-8387-8a5c1a48fafc
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: a7387bd3-8b31-4bd0-a861-daa8f7cb2d05
docset: aem65
role: Admin
exl-id: c43cab7b-3421-4e1b-a834-b2dd6eb23c1d
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# AEM DS-instellingen configureren{#configuring-aem-ds-settings}

Dit artikel beschrijft hoe te vormen **AEM DS Settings Service**. Deze instelling kan in meerdere scenario&#39;s worden gebruikt, bijvoorbeeld:

* In het Correspondentenbeheer

   * Voor het configureren van de AEM Forms-workflow
   * Tijdens het gebruik van de portal Formulieren voor het op afstand opslaan van concepten/verzenden

* In adaptieve formulieren voor gevallen waarin een adaptief formulier wordt ingediend vanuit een publicatie-instantie

Hier volgen de stappen voor het configureren van de **[!UICONTROL AEM DS Settings]**:

1. Open de Manager van de Configuratie op publiceer instantie gebruikend URL:\
   *https://localhost:port/system/console/configMgr*.

   ![Webconsole-configuratie AEM](assets/web_configuration_console_new.png)

1. In de **[!UICONTROL Adobe Experience Manager Web Console Configuration]** venster, zoek en klik op **[!UICONTROL AEM DS Settings]** optie.

   ![DS-instellingen](assets/ds_settings_new.png)

1. De **[!UICONTROL AEM DS Settings Service]** toont de gemeenschappelijke configuratiemontages voor AEM DS Componenten.

   ![DS Settings Service](assets/ds_settings_service_new.png)

1. Voeg de volgende informatie in de respectieve gebieden toe:

   **[!UICONTROL Processing Server URL]**: De Verwerkingsserver is de server waarop de Forms- of AEM-workflow moet worden geactiveerd. Dit kan gelijk zijn aan de URL van de AEM auteur-instantie of de andere server-URL (https://localhost:port/).

   **[!UICONTROL Processing Server User Name]**: Gebruikersnaam werkstroomgebruiker [gebaseerd op de server-URL die wordt gebruikt]

   **[!UICONTROL Processing Server Password]**: Wachtwoord workflowgebruiker

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Voordat u Forms- of AEM-workflows gebruikt, moet u de service voor DS-instellingen configureren voordat u gegevens van de publicatieserver verzendt. Anders zal de indiening van het formulier mislukken.

