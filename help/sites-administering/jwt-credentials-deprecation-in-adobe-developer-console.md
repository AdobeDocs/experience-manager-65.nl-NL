---
title: JWT Credentials Deprection in Adobe Developer Console
description: Meer informatie over de impact van de afschrijving van JWT-referenties in Adobe Developer Console op AEM
exl-id: f19a92de-ba6a-4f6d-9e12-60ad1bad2e74
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: f96b178ae84b4b930b59e36d4994970682c53dbd
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# JWT Credentials Deprection in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
> AEM als de dienst van de Wolk zou [ het vergelijkbare artikel voor versie AEMaaCS ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html?lang=nl-NL) voor meer informatie moeten van verwijzingen voorzien.

De klanten van Adobe gebruiken [ Adobe Developer Console ](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de geloofsbrieven van Server-aan-Server OAuth. De nieuwe geloofsbrieven van de Rekening van de Dienst (JWT) kunnen niet op of na 3 juni 2024 worden gecreeerd, en de bestaande geloofsbrieven van JWT zullen niet aan of na 27 jan. 2025 werken. U kunt [ lezen over de veroudering ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration).

Dit artikel biedt een extra context voor de manier waarop Adobe Experience Manager (AEM) 6.5-klanten de afschrijving moeten afhandelen.

Het belangrijkste voordeel is dat AEM nu de nieuwe OAuth Server-to-Server referenties voor AEM ondersteunt. U hebt mogelijk een e-mail ontvangen met instructies voor het migreren van uw JWT-gegevens. Deze migratie kan nu worden uitgevoerd.

In de volgende secties worden de scenario&#39;s weergegeven waarin klanten hun JWT-referenties (Service Account) moeten vervangen door OAuth Server-to-Server-referenties, nu AEM deze ondersteunt. [ las hoe ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration#migration-overview) om de geloofsbrieven te migreren.

## AEM integreren met andere Adobe-oplossingen {#integrating-aem-with-other-adobe-solutions}

**Actie**: Migreer uw configuratie aangezien AEM nu geloofsbrieven OAuth steunt.

**Relevante versies van AEM**: Adobe Managed Services (Service Pack 21 en hierboven).

AEM-klanten gebruiken de AEM om integratie met alle andere Adobe-oplossingen te configureren. Bijvoorbeeld Adobe Target, Adobe Analytics en andere.

![ Integrerend AEM met andere oplossingen ](/help/sites-administering/assets/jwt-deprecation.png)

Zie &lbrace;de Integraties IMS van de Opstelling voor AEM [&#128279;](/help/sites-administering/setting-up-ims-integrations-for-aem.md) voor details van hoe te:

* configuraties maken met OAuth-gebruikersgegevens
* migreer configuraties, die met geloofsbrieven JWT werden gecreeerd, om geloofsbrieven te gebruiken OAuth

## Cloud Manager API&#39;s {#cloud-manager-apis}

**Actie**: Bevestig wanneer deze van geloofsbrieven kunnen worden gemigreerd JWT aan OAuth.

**Relevante versies van AEM**: Adobe Managed Services (Service Pack 21 en hierboven).

De klanten creëren de projecten van Adobe Developer Console zodat kunnen zij [ Cloud Manager APIs ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aanhalen. De geloofsbrieven in het project van Adobe Developer zouden aan het server-aan-Server referentie type OAuth moeten worden gemigreerd alvorens de afgekeurde geloofsbrieven JWT in Januari 2025 verlopen.
