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

Als u een proces wilt starten vanuit de Adobe Experience Manager (AEM) Forms-app, moet u een beginpunt van het type hebben **Werkruimte** in uw proces. U moet ook de optie **[!UICONTROL Visible in Mobile Workspace]** voor het startpunt.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Een proces starten dat is gedefinieerd in Workbench**

1. Ga naar [Startscherm](../../forms/using/home-screen.md).
1. Op de **[!UICONTROL Home]** het scherm, door gebrek **[!UICONTROL All Forms]** wordt weergegeven.

   Het startpunt is gekoppeld aan een formulier. Selecteer het startpunt voor het formulier in de lijst om het te openen.

   Het formulier dat aan het startpunt is gekoppeld, wordt geopend.

1. Voer de gegevens in het dialoogvenster **[!UICONTROL Startpoint]** formulier.

   U kunt annotaties toevoegen aan deze taak met de opdracht [bijlage](../../forms/using/add-attachments.md) knop.

1. Nadat u het formulier hebt ingevuld, selecteert u het **[!UICONTROL Submit]** knop.

Als de app offline is, worden het formulier en de bijbehorende gegevens opgeslagen in de map Outbox.

Als de app online is, wordt de taak gesynchroniseerd met de AEM Forms-server en toegewezen aan de gebruiker die in het proces is opgegeven.

Als u met de taak in uw takenlijst wilt werken, raadpleegt u [Een taak openen](/help/forms/using/open-task.md).
