---
title: Werken met beginpunten
seo-title: Working with Startpoints
description: Stappen om met een AEM Forms-proces te werken vanaf uw mobiele apparaat dat is gedefinieerd in Workbench.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 1c4b4c86-cbdb-4e72-b0eb-7f8a2f5dcdde
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 1ea60fb2-cf9f-4a87-bd8e-98150e668456
docset: aem65
exl-id: d5970f90-2899-43a5-a3a0-61a2c844d919
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Werken met beginpunten{#working-with-startpoints}

Een startpunt roept een proces aan dat in Workbench wordt gecreeerd. Het is gekoppeld aan een formulier dat het proces activeert wanneer het formulier wordt verzonden.

>[!NOTE]
>
>De termen startpunten, beginproces en vorm worden door elkaar gebruikt wanneer wordt verwezen naar dit concept.

Als u een proces wilt starten vanuit de AEM Forms-app, hebt u een beginpunt van het type nodig **Werkruimte** in uw proces. Ook moet u de optie **[!UICONTROL Visibile in Mobile Workspace]** voor het startpunt.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Een proces starten dat is gedefinieerd in Workbench**

1. Ga naar [Startscherm](../../forms/using/home-screen.md).
1. Op de **[!UICONTROL Home]** het scherm, door gebrek **[!UICONTROL All Forms]** wordt weergegeven.

   Het startpunt is gekoppeld aan een formulier. Tik op het aan het formulier gekoppelde startpunt in de lijst om het te openen.

   Het formulier dat aan het startpunt is gekoppeld, wordt geopend.

1. Voer de gegevens in het dialoogvenster **[!UICONTROL Startpoint]** formulier.

   U kunt annotaties toevoegen aan deze taak met de opdracht [bijlage](../../forms/using/add-attachments.md) knop.

1. Tik op de knop **[!UICONTROL Submit]** knop.

Als de app offline is, worden het formulier en de bijbehorende gegevens opgeslagen in de map Outbox.

Als de app online is, wordt de taak gesynchroniseerd met de AEM Forms-server en toegewezen aan de gebruiker die in het proces is opgegeven.

Als u met de taak in uw takenlijst wilt werken, raadpleegt u [Een taak openen](/help/forms/using/open-task.md).
