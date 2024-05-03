---
title: Eindpunten toevoegen, inschakelen, wijzigen of verwijderen
description: Leer hoe u eindpunten toevoegt, inschakelt, wijzigt en verwijdert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b7461d5c-95d1-4da2-9d2a-f54c410a87f9
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Eindpunten toevoegen, inschakelen, wijzigen of verwijderen {#adding-enabling-modifying-or-removing-endpoints}

## Voeg een eindpunt aan de dienst toe {#add-an-endpoint-to-a-service}

Eindpunten kunnen alleen aan services worden toegevoegd. Een eindpunt kan niet bestaan alleen; het moet met de dienst worden geassocieerd.

>[!NOTE]
>
>Het wordt aanbevolen unieke namen te gebruiken wanneer u eindpunten toevoegt.

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik de dienst om te vormen.
1. Selecteer in de lijst op het tabblad Eindpunten het type eindpunt dat u wilt toevoegen en klik op Toevoegen.
1. Afhankelijk van het eindpunttype, vorm extra eindpuntmontages.

[Instellingen voor het eindpunt van gecontroleerde mappen](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)

[Instellingen voor e-maileindpunt](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)

[Eindpunten van Taakbeheer configureren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)

[Instellingen voor eindpunten verwijderen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings)

1. Klik toevoegen.

## Een eindpunt in- of uitschakelen {#enable-or-disable-an-endpoint}

Nieuwe eindpunten worden standaard automatisch ingeschakeld. Maar als u een eindpunt onbruikbaar hebt gemaakt, moet u het voor het om operationeel te maken toelaten.

Als u problemen met de diensten ervaart, maak de bijbehorende eindpunten onbruikbaar om het probleem beter op te lossen. U kunt eindpunten tijdens regelmatig systeemonderhoud of wanneer het bevorderen van de dienst ook willen onbruikbaar maken.

1. Klik in de beheerconsole op Services > Toepassingen en services > Eindpuntbeheer.
1. Voor de pagina van het Beheer van het Eindpunt, selecteer de controledoos voor het eindpunt om toe te laten of onbruikbaar te maken en toe te laten of onbruikbaar te maken en te klikken of onbruikbaar te maken.

## Een eindpunt wijzigen {#modify-an-endpoint}

>[!NOTE]
>
>De veranderingen u aan een eindpuntconfiguratie gebruikend beleidsconsole aanbrengt worden niet weerspiegeld in de ontwerp-tijd exemplaren van uw toepassingen. Als u een toepassing opnieuw opstelt, zal om het even welke verandering die u aan zijn eindpunten gebruikend beleidsconsole aanbracht, worden verloren.

1. Klik in de beheerconsole op Services > Toepassingen en services > Eindpuntbeheer.
1. Voor de pagina van het Beheer van het Eindpunt, klik het eindpunt om te wijzigen.
1. Op de pagina van het Eindpunt van de Update, wijzig de eindpuntnaam, de beschrijving, en de montages.

   >[!NOTE]
   >
   >Plaats geen &lt;-teken in de naam of beschrijving omdat de naam of beschrijving die in Workspace wordt weergegeven hierdoor wordt afgekapt.

1. Klik op Bijwerken om de wijzigingen op te slaan.

U kunt deze taak van de pagina van het Beheer van de Dienst ook doen door de dienst te selecteren en dan de Eindpunten tabel te klikken.

## Een eindpunt verwijderen {#remove-an-endpoint}

1. Klik in de beheerconsole op Services > Toepassingen en services > Eindpuntbeheer.
1. Voor de pagina van het Beheer van het Eindpunt, selecteer de controledoos voor het eindpunt te verwijderen en te klikken verwijdert. Het eindpunt wordt niet meer weergegeven.
