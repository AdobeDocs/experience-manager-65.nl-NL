---
title: JWT Credentials Deprection in Adobe Developer Console
description: Meer informatie over de gevolgen van de afschrijving van JWT-gebruikersgegevens in Adobe Developer Console voor AEM
exl-id: f19a92de-ba6a-4f6d-9e12-60ad1bad2e74
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# JWT Credentials Deprection in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
> AEM als Cloud-service moet verwijzen naar [dit artikel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html) voor meer informatie .

Adobe die klanten gebruiken [Adobe Developer Console](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de geloofsbrieven van Server-aan-Server OAuth. De nieuwe geloofsbrieven van de Rekening van de Dienst (JWT) kunnen niet op of na 1 Mei, 2024 worden gecreeerd, en de bestaande geloofsbrieven van JWT zullen niet aan of na 1 Jan, 2025 werken. U kunt [lezen over de afgekeurde tekst](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dit artikel verstrekt wat extra context over hoe AEM 6.5 klanten de veroudering zouden moeten behandelen.

Het belangrijkste op dit ogenblik weghalen is dat AEM eigenschappen nog niet de nieuwe geloofsbrieven van Server-aan-Server steunen OAuth. De steun zal binnenkort — half april 2024 door een speciaal verenigbaarheidspakket voor AEM 6.5 worden geïnstalleerd, als u het recentste Service Pack 20 of lager in werking stelt (Service Pack 21 en hoger zal automatisch het omvatten). U kunt een e-mail met instructies hebben ontvangen om uw geloofsbrieven van JWT te migreren, maar rust verzekerd dat u op de geloofsbrieven migratie kunt en zou moeten blokkeren tot AEM het nieuwe server-aan-server credentiële type van OAuth steunt.

In de volgende secties worden de scenario&#39;s weergegeven waarin klanten hun JWT-gegevens (Service Account) moeten vervangen door OAuth Server-to-Server-referenties, zodra AEM deze gegevens medio april ondersteunt. [Lees hoe](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) om de geloofsbrieven in de toekomst te vervangen.

## AEM integreren met andere oplossingen voor Adobe {#integrating-aem-with-other-adobe-solutions}

**Handeling**: Wacht op migratie tot medio april 2024, wanneer AEM het ondersteunt.

**Relevante AEM versies**: Adobe Managed Services (Service Pack 20 en lager).


AEM klanten gebruiken AEM Auteur UI om integratie met alle andere oplossingen van de Adobe te vormen. Bijvoorbeeld Adobe Target, Adobe Analytics, Adobe Launch, AFCS en nog veel meer.

![AEM integreren met andere oplossingen](/help/sites-administering/assets/jwt-deprecation.png)

Hier ziet u bijvoorbeeld [de instructies](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=en) voor het configureren van de integratie met Adobe Target. De API-sleutel in het dialoogvenster [De IMS-configuratie voltooien in AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html#completing-the-ims-configuration-in-aem) de sectie zou aan het server-aan-server referentie type van OAuth moeten worden gemigreerd, zodra AEM die geloofsbrieven halverwege april steunt. Die instructies zullen half april worden herzien om u te helpen de nieuwe geloofsbrieven van Server-aan-Server toepassen OAuth.

## Cloud Manager-API&#39;s {#cloud-manager-apis}

**Handeling**: Wacht op migratie tot medio april 2024, wanneer AEM het ondersteunt.

**Relevante AEM versies**: Adobe Managed Services (Service Pack 20 en lager).

Klanten maken Adobe Developer Console-projecten zodat ze deze kunnen aanroepen [Cloud Manager-API&#39;s](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). De geloofsbrieven in het project van Adobe Developer zouden aan het OAuth server-aan-Server credentietype moeten worden gemigreerd, zodra AEM en de Manager van de Wolk het steunen.
