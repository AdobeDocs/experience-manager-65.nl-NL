---
title: Werken met beginpunten
description: Stappen om te werken met een Adobe Experience Manager Forms-proces vanaf uw mobiele apparaat dat is gedefinieerd in Workbench.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: d5970f90-2899-43a5-a3a0-61a2c844d919
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: dd8748cee7a4b3ba91795a51928bd8590c47ef27
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Werken met beginpunten{#working-with-startpoints}

Een startpunt roept een proces aan dat in Workbench wordt gecreeerd. Het is gekoppeld aan een formulier dat het proces activeert wanneer het formulier wordt verzonden.

>[!NOTE]
>
>De termen startpunten, beginproces en vorm worden door elkaar gebruikt wanneer u naar dit concept verwijst.

Om een proces van Adobe Experience Manager (AEM) in werking te stellen Forms app, moet u een uitgangspunt van type **Workspace** in uw proces hebben. U moet ook de optie **[!UICONTROL Visible in Mobile Workspace]** selecteren voor het startpunt.

![&#x200B; mws_startpoint_select_option &#x200B;](assets/mws_startpoint_select_option.png)

**om een proces te beginnen dat in Workbench wordt bepaald**

1. Om de Startpunten te bekijken beschikbaar in AEM Forms app, ga naar [&#x200B; het scherm van het Huis &#x200B;](../../forms/using/home-screen.md).
1. Standaard wordt de lijst **[!UICONTROL All Forms]** weergegeven op het scherm **[!UICONTROL Home]** .

   Het startpunt is gekoppeld aan een formulier. Selecteer het startpunt voor het formulier in de lijst om het te openen.

   Het formulier dat aan het startpunt is gekoppeld, wordt geopend.

1. Voer de details in het **[!UICONTROL Startpoint]** -formulier in.

   U kunt annotaties aan deze taak toevoegen gebruikend de [&#x200B; gehechtheid &#x200B;](../../forms/using/add-attachments.md) knoop.

1. Nadat u het formulier hebt ingevuld, selecteert u de knop **[!UICONTROL Submit]** .

Als de app offline is, worden het formulier en de bijbehorende gegevens opgeslagen in de map Outbox.

Als de app online is, wordt de taak gesynchroniseerd met de AEM Forms-server en toegewezen aan de gebruiker die in het proces is opgegeven.

Om met de taak in uw taaklijst te werken, zie [&#x200B; Openend een taak &#x200B;](/help/forms/using/open-task.md).
