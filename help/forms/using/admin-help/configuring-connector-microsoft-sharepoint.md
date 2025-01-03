---
title: Connector configureren voor Microsoft SharePoint
description: Configureer Connector voor Microsoft SharePoint om communicatie tussen AEM formulieren en Microsoft SharePoint mogelijk te maken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: a8be58f1-1961-4bf5-aaad-feb4489fb389
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
source-git-commit: 98cbaaf64c0268be1afe7196a7bbbf5c93f02148
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Connector configureren voor Microsoft SharePoint

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Connector voor Microsoft SharePoint maakt communicatie mogelijk tussen AEM formulieren en Microsoft SharePoint. Voor extra achtergrondinformatie, zie &quot;Connectors voor ECM&quot;in [ Verwijzing van de Diensten ](https://www.adobe.com/go/learn_aemforms_services_63).

1. Klik in de beheerconsole op Services > Connector voor Microsoft SharePoint.
2. Geef de volgende instellingen op voor uw SharePoint-server:

   **de Naam van de Gastheer van de Server van SharePoint:** het de havenaantal van de gastheernaam van de Webtoepassing op de server van SharePoint, in het formaat `[hostname]:'port'`.

   **Naam van de Gebruiker:** De gebruikersrekening die wordt gebruikt om met de server van SharePoint te verbinden.

   **Wachtwoord:** Wachtwoord voor de gebruikersrekening die wordt gebruikt om met de server van SharePoint te verbinden

   **Naam van het Domein:** Domein waar de server van SharePoint wordt gevestigd.

3. Klik op Opslaan.

## Microsoft SharePoint-configuratieservice {#microsoft-sharepoint-configuration-service}

Met de Microsoft SharePoint-configuratieservice `(MSSharePointConfigService)` kunt u referenties opgeven voor de gebruiker van AEM formulier die imitatierechten heeft. Voor informatie over imitatierechten, zie [ het Vormen Schakelaar voor Microsoft SharePoint ](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). Voer de volgende stappen uit om instellingen op te geven voor `MSSharePointConfigService` :

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Navigeer in de lijst met services en klik op `MSSharePointConfigService` .
1. Specificeer de volgende montages op de pagina van de Configuratie:

   * Gebruikersnaam voor een gebruiker met imitatierechten
   * Wachtwoord voor bovenstaande gebruiker

1. Klik op Opslaan.
