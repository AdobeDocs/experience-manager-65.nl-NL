---
title: JWT Credentials Deprection in Adobe Developer Console
description: Meer informatie over de gevolgen van de afschrijving van JWT-gebruikersgegevens in Adobe Developer Console voor AEM
exl-id: f19a92de-ba6a-4f6d-9e12-60ad1bad2e74
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: bb4367fa9916a8bafa6255562b2454ddae143351
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# JWT Credentials Deprection in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
> AEM als Cloud-service moet verwijzen naar [dit artikel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html) voor meer informatie .

Adobe die klanten gebruiken [Adobe Developer Console](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de geloofsbrieven van Server-aan-Server OAuth. De nieuwe geloofsbrieven van de Rekening van de Dienst (JWT) kunnen niet op of na 3 juni 2024 worden gecreeerd, en de bestaande geloofsbrieven van JWT zullen niet aan of na 27 jan. 2025 werken. U kunt [lezen over de afgekeurde tekst](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dit artikel biedt een extra context voor de manier waarop Adobe Experience Manager (AEM) 6.5-klanten de afschrijving moeten afhandelen.

Het belangrijkste wegnemen is dat AEM nu de nieuwe geloofsbrieven OAuth server-aan-Server voor AEM steunt. U hebt mogelijk een e-mail ontvangen met instructies voor het migreren van uw JWT-gegevens. Deze migratie kan nu worden uitgevoerd.

In de volgende secties worden de scenario&#39;s weergegeven waarin klanten hun JWT-referenties (Service Account) moeten vervangen door OAuth Server-to-Server-referenties, nu AEM hen ondersteunt. [Lees hoe](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) om de gegevens te migreren.

## AEM integreren met andere oplossingen voor Adobe {#integrating-aem-with-other-adobe-solutions}

**Handeling**: Migreer uw configuratie aangezien AEM nu geloofsbrieven OAuth steunt.

**Relevante AEM versies**: Adobe Managed Services (Service Pack 21 en hoger).

AEM klanten gebruiken de AEM om integratie met alle andere oplossingen van de Adobe te vormen. Bijvoorbeeld Adobe Target, Adobe Analytics en andere.

![AEM integreren met andere oplossingen](/help/sites-administering/assets/jwt-deprecation.png)

Zie [IMS-integratie instellen voor AEM](/help/sites-administering/setting-up-ims-integrations-for-aem.md) voor meer informatie over hoe:

* configuraties maken met OAuth-gebruikersgegevens
* migreer configuraties, die met geloofsbrieven JWT werden gecreeerd, om geloofsbrieven te gebruiken OAuth

## Cloud Manager-API&#39;s {#cloud-manager-apis}

**Handeling**: Bevestig wanneer deze gegevens kunnen worden gemigreerd van JWT naar OAuth-referenties.

**Relevante AEM versies**: Adobe Managed Services (Service Pack 21 en hoger).

Klanten maken Adobe Developer Console-projecten zodat ze deze kunnen aanroepen [Cloud Manager-API&#39;s](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). De geloofsbrieven in het project van Adobe Developer zouden aan het server-aan-Server referentie type OAuth moeten worden gemigreerd alvorens de afgekeurde geloofsbrieven JWT in Januari 2025 verlopen.
