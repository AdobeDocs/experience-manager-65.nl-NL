---
title: Connector configureren voor Microsoft SharePoint
seo-title: Connector configureren voor Microsoft SharePoint
description: Configureer Connector voor Microsoft SharePoint om communicatie tussen AEM formulieren en Microsoft SharePoint mogelijk te maken.
seo-description: Configureer Connector voor Microsoft SharePoint om communicatie tussen AEM formulieren en Microsoft SharePoint mogelijk te maken.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 1%

---


# Connector configureren voor Microsoft SharePoint {#configuring-connector-for-microsoft-sharepoint}

De schakelaar voor Microsoft SharePoint laat communicatie tussen AEM vormen en Microsoft SharePoint toe. Zie &quot;Connectors for ECM&quot; in [Services Reference](https://www.adobe.com/go/learn_aemforms_services_63) voor aanvullende achtergrondinformatie.

1. Klik in de beheerconsole op Services > Connector voor Microsoft SharePoint.
1. Geef de volgende instellingen op voor uw SharePoint-server:

   **Hostnaam van SharePoint-server:** het poortnummer van de hostnaam van de webtoepassing op de SharePoint-server, in de indeling  `[hostname]:'port'`.

   **Gebruikersnaam:** De gebruikersaccount die wordt gebruikt om verbinding te maken met de SharePoint-server.

   **Wachtwoord:** Wachtwoord voor de gebruikersaccount die wordt gebruikt om verbinding te maken met de SharePoint-server

   **Domeinnaam:** domein waar de SharePoint-server zich bevindt.

1. Klik op Opslaan.

## Microsoft SharePoint-configuratieservice {#microsoft-sharepoint-configuration-service}

Met de Microsoft SharePoint-configuratieservice `(MSSharePointConfigService)` kunt u referenties opgeven voor de gebruiker van AEM formulieren die imitatierechten heeft. Voor informatie over imitatierechten, zie [Het vormen Schakelaar voor Microsoft SharePoint](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). Ga als volgt te werk om instellingen op te geven voor `MSSharePointConfigService`:

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Navigeer in de lijst met services en klik op `MSSharePointConfigService`.
1. Specificeer de volgende montages op de pagina van de Configuratie:

   * Gebruikersnaam voor een gebruiker met imitatierechten
   * Wachtwoord voor bovenstaande gebruiker

1. Klik op Opslaan.

