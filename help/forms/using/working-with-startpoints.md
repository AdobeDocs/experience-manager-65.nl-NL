---
title: Werken met beginpunten
seo-title: Werken met beginpunten
description: Stappen om met een AEM Forms-proces te werken vanaf uw mobiele apparaat dat is gedefinieerd in Workbench.
seo-description: Stappen om met een AEM Forms-proces te werken vanaf uw mobiele apparaat dat is gedefinieerd in Workbench.
uuid: 1c4b4c86-cbdb-4e72-b0eb-7f8a2f5dcdde
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 1ea60fb2-cf9f-4a87-bd8e-98150e668456
docset: aem65
translation-type: tm+mt
source-git-commit: af326f2d2b278fe36df05afc8c172f74c99a064c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# Werken met beginpunten{#working-with-startpoints}

Een startpunt roept een proces aan dat in Workbench wordt gecreeerd. Het is gekoppeld aan een formulier dat het proces activeert wanneer het formulier wordt verzonden.

>[!NOTE]
>
>De termen startpunten, beginproces en vorm worden door elkaar gebruikt wanneer wordt verwezen naar dit concept.

Als u een proces wilt starten vanuit de AEM Forms-app, moet u een beginpunt van het type **Workspace** in uw proces hebben. U moet ook de **[!UICONTROL Visibile in Mobile Workspace]** optie voor het startpunt selecteren.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Een proces starten dat is gedefinieerd in Workbench**

1. Ga naar het scherm [](../../forms/using/home-screen.md)Home om de Startpunten te bekijken die beschikbaar zijn in de AEM Forms-app.
1. Standaard wordt de lijst op het **[!UICONTROL Home]** **[!UICONTROL All Forms]** scherm weergegeven.

   Het startpunt is gekoppeld aan een formulier. Tik op het aan het formulier gekoppelde startpunt in de lijst om het te openen.

   Het formulier dat aan het startpunt is gekoppeld, wordt geopend.

1. Voer de gegevens in het **[!UICONTROL Startpoint]** formulier in.

   U kunt annotaties toevoegen aan deze taak met de [knop Bijlage](../../forms/using/add-attachments.md) .

1. Tik op de **[!UICONTROL Submit]** knop nadat u het formulier hebt ingevuld.

Als de app offline is, worden het formulier en de bijbehorende gegevens opgeslagen in de map Outbox.

Als de app online is, wordt de taak gesynchroniseerd met de AEM Forms-server en toegewezen aan de gebruiker die in het proces is opgegeven.

Zie Een taak [openen](/help/forms/using/open-task.md)voor informatie over het werken met de taak in de takenlijst.
