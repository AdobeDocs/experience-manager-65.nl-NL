---
title: Elementeninzichten configureren om analyses op te halen.
description: Elementeninzichten configureren in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
role: Architect, Admin
feature: Asset Insights, Asset Reports
exl-id: 67be0ae6-5939-40fe-bf8a-b8a2c2f68f15
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Elementengegevens configureren {#configure-asset-insights}

[!DNL Adobe Experience Manager Assets] Hiermee haalt u gebruiksgegevens op van digitale elementen die door websites van derden worden gebruikt  [!DNL Adobe Analytics]. Om ActivaInzichten toe te laten om deze gegevens terug te winnen en inzichten te produceren, vorm eerst de eigenschap om met [!DNL Adobe Analytics] te integreren. Als u deze functie wilt gebruiken in een on-premise installatie, moet u [!DNL Adobe Analytics] licentie afzonderlijk aanschaffen. Klanten op [!DNL Managed Services] ontvangen [!DNL Analytics] licentie gebundeld met [!DNL Experience Manager]. Zie [Managed Services productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klik op de **[!UICONTROL Insights Configuration]**-kaart.
1. Selecteer een datacenter in de wizard en geef uw referenties op, inclusief de naam van uw organisatie, gebruikersnaam en gedeeld geheim.

   ![Adobe Analytics for Assets Insights in Experience Manager configureren](assets/insights_config2.png)

   *Afbeelding: Configureer  [!DNL Adobe Analytics] voor Middelen-inzichten in  [!DNL Experience Manager].*

1. Klik op **[!UICONTROL Authenticate]**.
1. Nadat [!DNL Experience Manager] uw geloofsbrieven voor authentiek verklaart, van de **[!UICONTROL Report Suite]** lijst, kies een [!DNL Adobe Analytics] rapportreeks van waar u de Inzichten van Activa om gegevens wilt halen. Klik op **[!UICONTROL Add]**.
1. Nadat [!DNL Experience Manager] uw rapportsuite heeft ingesteld, klikt u op **[!UICONTROL Done]**.

## Paginatracering {#page-tracker}

Nadat u uw [!DNL Adobe Analytics] rekening vormt, wordt de code van de Tracker van de Pagina geproduceerd voor u. Als u met behulp van Elementen inzicht wilt krijgen in het bijhouden van [!DNL Experience Manager]-elementen die worden gebruikt op websites van derden, neemt u de paginacontrackercode op in de websitecode. Gebruik het [!UICONTROL Page Tracker] nut in [!DNL Experience Manager Assets] om de code van de paginacontracker te produceren. Zie [Paginacontracker gebruiken en code insluiten in webpagina&#39;s van derden](/help/assets/use-page-tracker.md) voor meer informatie over het opnemen van de code in Paginanummering in webpagina&#39;s.

1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klik op de **[!UICONTROL Navigation]**-pagina op de **[!UICONTROL Insights Page Tracker]**-kaart.
1. Klik **[!UICONTROL Download]** om de code van de paginacontracker te downloaden.
