---
title: Configureer Asset Insights om analyses van het gebruik van digitale middelen te verkrijgen.
description: Elementinzichten configureren in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: b59f7471ab9f3c5e6eb3365122262b592c8e6244
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Elementinzichten configureren {#configure-asset-insights}

[!DNL Adobe Experience Manager Assets] Hiermee haalt u gebruiksgegevens op van digitale elementen die door websites van derden worden gebruikt [!DNL Adobe Analytics]. Als u Asset Insights wilt inschakelen om deze gegevens op te halen en inzichten te genereren, moet u eerst de functie configureren voor integratie met Adobe Analytics.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. Klik [!DNL Experience Manager]in **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klik op de **[!UICONTROL Insights Configuration]** kaart.
1. Selecteer een datacenter in de wizard en geef uw referenties op, inclusief de naam van uw organisatie, gebruikersnaam en gedeeld geheim.

   ![Adobe Analytics for Assets Insights configureren in Experience Manager](assets/insights_config2.png)

   *Afbeelding: Configureer[!DNL Adobe Analytics]voor Middelen-inzichten in[!DNL Experience Manager].*

1. Klik op **[!UICONTROL Authenticate]**.
1. Nadat u uw referenties hebt [!DNL Experience Manager] geverifieerd, kiest u in de **[!UICONTROL Report Suite]** lijst een [!DNL Adobe Analytics] rapportsuite waaruit u gegevens wilt ophalen met behulp van Asset Insights. Klik op **[!UICONTROL Add]**.
1. Klik op de rapportsuite nadat u deze hebt [!DNL Experience Manager] **[!UICONTROL Done]** ingesteld.

## Paginatracering {#page-tracker}

Nadat u uw [!DNL Adobe Analytics] account hebt geconfigureerd, wordt de code van Paginanummer voor u gegenereerd. Neem de paginacontrackercode in de websitecode op om Elementen inzicht te geven in [!DNL Experience Manager] elementen die worden gebruikt op websites van derden. Gebruik het [!UICONTROL Page Tracker] nut in [!DNL Experience Manager Assets] om de code van de paginacontracker te produceren. Zie Paginacontrole [gebruiken en code insluiten in webpagina&#39;s](/help/assets/touch-ui-using-page-tracker.md)voor meer informatie over het opnemen van uw code in Paginanummering in externe webpagina&#39;s.

1. Klik [!DNL Experience Manager]in **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klik op de **[!UICONTROL Navigation]** **[!UICONTROL Insights Page Tracker]** kaart op de pagina.
1. Klik **[!UICONTROL Download]** om de code van de paginacontracker te downloaden.
