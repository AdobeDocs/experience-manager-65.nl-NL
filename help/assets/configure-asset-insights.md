---
title: Configureer Assets Insights voor analyses.
description: Configureer Assets Insights in  [!DNL Adobe Experience Manager Assets] .
contentOwner: AG
role: Architect, Admin
feature: Asset Insights,Asset Reports
exl-id: 67be0ae6-5939-40fe-bf8a-b8a2c2f68f15
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Assets Insights configureren {#configure-asset-insights}

[!DNL Adobe Experience Manager Assets] haalt gebruiksgegevens op over digitale elementen die door websites van derden worden gebruikt vanuit [!DNL Adobe Analytics] . Als u Assets Insights in staat wilt stellen deze gegevens op te halen en inzichten te genereren, moet u eerst de functie configureren voor integratie met [!DNL Adobe Analytics] . Als u deze functie in een on-premise installatie wilt gebruiken, moet u de [!DNL Adobe Analytics] -licentie afzonderlijk aanschaffen. Klanten op [!DNL Managed Services] ontvangen een [!DNL Analytics] -licentie die is gebundeld met [!DNL Experience Manager] . Zie [ Managed Services productbeschrijving ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** .

   ![ chlimage_1-72 ](assets/chlimage_1-210.png)

1. Klik op de **[!UICONTROL Insights Configuration]** -kaart.
1. Selecteer een datacenter in de wizard en geef uw referenties op, inclusief de naam van uw organisatie, gebruikersnaam en gedeeld geheim.

   ![ vorm Adobe Analytics voor de Inzichten van Assets in Experience Manager ](assets/insights_config2.png)

   *Cijfer: Vorm [!DNL Adobe Analytics] voor de Inzichten van Assets in [!DNL Experience Manager].*

1. Klik op **[!UICONTROL Authenticate]**.
1. Nadat [!DNL Experience Manager] uw referenties heeft geverifieerd, kiest u in de lijst **[!UICONTROL Report Suite]** een [!DNL Adobe Analytics] -rapportsuite vanuit de locatie waar u gegevens wilt ophalen met Assets Insights. Klik op **[!UICONTROL Add]**.
1. Klik op **[!UICONTROL Done]** nadat [!DNL Experience Manager] de rapportsuite heeft ingesteld.

## Paginatracering {#page-tracker}

Nadat u uw [!DNL Adobe Analytics] -account hebt geconfigureerd, wordt de code van Paginanummer voor u gegenereerd. Als u wilt dat Assets Insights [!DNL Experience Manager] -elementen kan bijhouden die worden gebruikt op websites van derden, neemt u de paginacontrackercode op in de websitecode. Gebruik het hulpprogramma [!UICONTROL Page Tracker] in [!DNL Experience Manager Assets] om de code van de paginacontracker te genereren. Voor meer informatie over hoe te om uw code van het Beheer van de Pagina in derdeWeb-pagina&#39;s te omvatten, zie [ de paginacontracker van het Gebruik en bed code in Web-pagina&#39;s ](/help/assets/use-page-tracker.md) in.

1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** .

   ![ chlimage_1-73 ](assets/chlimage_1-214.png)

1. Klik op de **[!UICONTROL Navigation]** -pagina op de **[!UICONTROL Insights Page Tracker]** -kaart.
1. Klik op **[!UICONTROL Download]** om de code van de paginacontracker te downloaden.
