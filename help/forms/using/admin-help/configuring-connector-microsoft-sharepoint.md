---
title: Connector configureren voor Microsoft SharePoint
description: Configureer Connector voor Microsoft SharePoint om communicatie tussen AEM formulieren en Microsoft SharePoint mogelijk te maken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: a8be58f1-1961-4bf5-aaad-feb4489fb389
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Connector configureren voor Microsoft SharePoint {#configuring-connector-for-microsoft-sharepoint}

Connector voor Microsoft SharePoint maakt communicatie mogelijk tussen AEM formulieren en Microsoft SharePoint. Zie &quot;Connectors for ECM&quot; in [Servicereferentie](https://www.adobe.com/go/learn_aemforms_services_63).

1. Klik in de beheerconsole op Services > Connector voor Microsoft SharePoint.
1. Geef de volgende instellingen op voor uw SharePoint-server:

   **Hostnaam SharePoint-server:** Het poortnummer van de hostnaam van de webtoepassing op de SharePoint-server, in de notatie `[hostname]:'port'`.

   **Gebruikersnaam:** De gebruikersaccount waarmee verbinding wordt gemaakt met de SharePoint-server.

   **Wachtwoord:** Wachtwoord voor de gebruikersaccount waarmee verbinding wordt gemaakt met de SharePoint-server

   **Domeinnaam:** Domein waar de SharePoint-server zich bevindt.

1. Klik op Opslaan.

## Microsoft SharePoint-configuratieservice {#microsoft-sharepoint-configuration-service}

De Microsoft SharePoint-configuratieservice `(MSSharePointConfigService)` Hiermee kunt u referenties opgeven voor de gebruiker van AEM formulier die imitatierechten heeft. Zie voor informatie over imitatierechten [Connector configureren voor Microsoft SharePoint](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). Voer de volgende stappen uit om instellingen op te geven voor `MSSharePointConfigService`:

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Navigeer in de lijst met services en klik op `MSSharePointConfigService`.
1. Specificeer de volgende montages op de pagina van de Configuratie:

   * Gebruikersnaam voor een gebruiker met imitatierechten
   * Wachtwoord voor bovenstaande gebruiker

1. Klik op Opslaan.
