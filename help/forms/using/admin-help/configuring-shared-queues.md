---
title: Gedeelde wachtrijen configureren
description: Met gedeelde wachtrijen kunt u gebruikerswachtrijen effectief configureren en beheren. Leer hoe te om gedeelde rijen te vormen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 5f4467c1-0f3f-4dc6-9bd5-98259f327295
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Gedeelde wachtrijen configureren{#configuring-shared-queues}

Met gedeelde wachtrijen kunt u gebruikerswachtrijen effectief configureren en beheren. Een gebruikersrij is eenvoudig alle taken die aan een gebruiker worden toegewezen, zie [ om Lijsten ](https://help.adobe.com/en_US/livecycle/11.0/WorkspaceHelp/WS92d06802c76abadb-2b6ab502126beb6ba2f-7ffc.2.html) voor meer informatie te doen. U kunt gebruikersrijen toewijzen, ongedaan maken en opnieuw toewijzen, afhankelijk van uw organisatorische behoeften. U kunt Gedeelde wachtrijen op twee manieren beheren:

**beheert toegang tot een gebruiker**

Met deze optie kunt u de toegang tot een geselecteerde gebruikerswachtrij beheren.

**beheert toegang door een gebruiker**

Met deze optie kunt u gedeelde wachtrijen beheren die aan een geselecteerde gebruiker zijn toegewezen.

## Toegang tot een geselecteerde gebruikerswachtrij beheren {#managing-access-to-a-selected-user-queue}

Met Toegang tot een gebruikersfunctie beheren kunt u de toegang tot een geselecteerde gebruikerswachtrij beheren. U kunt toegang tot een geselecteerde gebruikersrij aan andere gebruikers in uw organisatie verlenen of intrekken. Kara Bowman is bijvoorbeeld niet meer aan het werk. Met behulp van de functie Toegang tot een gebruiker beheren kan de wachtrij van Kara worden gedeeld met Akira Tanaka en John Jacobs voor voltooiing. Op een later moment, wanneer Kara terugkeert naar het kantoor, kunt u de toegang tot haar rij intrekken van Akira Tanaka en John Jacobs.

Zodra deze taken zijn gedeeld, kunnen deze door de gebruiker worden voltooid, met toegang tot de wachtrij via Workspace.

>[!NOTE]
>
>De Flex Workspace is afgekeurd voor de release AEM formulieren.

### Toegang tot een geselecteerde gebruikerswachtrij configureren {#configuring-access-to-a-selected-user-queue}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

1. Meld u met een beheerdersaccount aan bij de beheerconsole.
1. Selecteer **de Diensten van 0} >** Forms Workflow **>** Gedeelde Rij **.**

1. Zoek op het tabblad Toegang tot een gebruiker beheren naar de gebruiker wiens wachtrij u wilt delen en selecteer deze. Op elk gewenst moment wordt in het rechterondervenster de lijst weergegeven met gebruikers die toegang hebben tot de geselecteerde gebruikerswachtrij.
1. Zoek en selecteer de gebruiker in het deelvenster linksonder. Klik op Delen.
1. Klik op Opslaan om te voltooien.

### Toegang tot een geselecteerde gebruikerswachtrij intrekken {#revoking-access-to-a-selected-user-queue}

1. Meld u met een beheerdersaccount aan bij de beheerconsole.
1. Selecteer **de Diensten van 0} >** Forms Workflow **>** Gedeelde Rij **.**

1. Zoek op het tabblad Toegang tot een gebruiker beheren naar de gebruiker wiens wachtrij u wilt beheren en selecteer deze.
1. In het rechterbenedendeelvenster wordt de lijst weergegeven met gebruikers die toegang hebben tot de geselecteerde gebruikerswachtrij. Selecteer de gebruiker en klik op Intrekken.
1. Klik op Opslaan om te voltooien.

## Wachtrijen beheren die aan een gebruiker zijn toegewezen {#managing-queues-assigned-to-a-user}

Met de functie Toegang door een gebruiker beheren kunt u wachtrijen beheren die aan een geselecteerde gebruiker zijn toegewezen. U kunt toegang tot gebruikersrijen verlenen of intrekken aan een geselecteerde gebruiker individueel. U wilt bijvoorbeeld de gebruikersrijen voor Akira Tanaka en John Jacobs toewijzen aan Kara Bowman. Met behulp van de functie Toegang beheren door een gebruiker kunt u zoeken naar Kara Bowman en toegang verlenen tot taken die zijn toegewezen aan Akira Tanaka en John Jacobs. Later kunt u de toegang van Kara Bowman tot deze gebruikerswachtrijen intrekken.

Zodra deze taken zijn toegewezen, kunnen deze door de gebruiker met Workspace worden voltooid.

>[!NOTE]
>
>De Flex Workspace is afgekeurd voor de release AEM formulieren.

### Toegang verlenen tot een geselecteerde gebruikerswachtrij {#granting-access-to-a-selected-user-queue}

1. Meld u met een beheerdersaccount aan bij de beheerconsole.
1. Selecteer **de Diensten van 0} >** Forms Workflow **>** Gedeelde Rij **.**

1. Zoek op het tabblad Toegang tot gebruiker beheren naar de gebruiker waarvan u de wachtrij wilt delen en selecteer deze. Op elk gewenst moment wordt in het rechterondervenster de lijst weergegeven met gebruikers die toegang hebben tot de geselecteerde gebruikerswachtrij.
1. Zoek en selecteer in het linkerbenedendeelvenster gebruikerswachtrijen die u met de geselecteerde gebruiker wilt delen. Klik op Delen.
1. Klik op Opslaan om te voltooien.

### Toegang tot een geselecteerde gebruikerswachtrij intrekken {#revoking_access_to_a_selected_user_queue-1}

1. Meld u met een beheerdersaccount aan bij de beheerconsole.
1. Selecteer **de Diensten van 0} >** Forms Workflow **>** Gedeelde Rij **.**

1. Zoek op het tabblad Toegang beheren door een gebruiker naar de gebruiker wiens wachtrij u wilt beheren en selecteer deze.
1. In het rechterbenedendeelvenster wordt de lijst weergegeven met gebruikerswachtrijen die aan de geselecteerde gebruiker zijn toegewezen. Selecteer de gebruikerswachtrij en klik op Intrekken.
1. Klik op Opslaan om te voltooien.
