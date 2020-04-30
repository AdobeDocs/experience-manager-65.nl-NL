---
title: Configureer Asset Insights om analyses van het gebruik van digitale middelen te verkrijgen.
description: Elementinzichten configureren in [!DNL Adobe Experience Manager-middelen].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Elementinzichten configureren {#configure-asset-insights}

[!DNL Adobe Experience Manager Assets] Hiermee haalt u gebruiksgegevens op van digitale elementen die door websites van derden worden gebruikt [!DNL Adobe Analytics]. Als u Asset Insights wilt inschakelen om deze gegevens op te halen en inzichten te genereren, moet u eerst de functie configureren voor integratie met Adobe Analytics.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. In [!DNL Experience Manager], click **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klik op de **[!UICONTROL Insights-configuratiekaart]**.
1. Selecteer een datacenter in de wizard en geef uw referenties op, inclusief de naam van uw organisatie, gebruikersnaam en gedeeld geheim.

   ![Adobe Analytics for Assets Insights configureren in Experience Manager](assets/insights_config2.png)

   *Afbeelding: Configureer[!DNL Adobe Analytics]voor Middelen-inzichten in[!DNL Experience Manager].*

1. Klik op **[!UICONTROL Verifiëren]**.
1. Nadat u uw gegevens hebt [!DNL Experience Manager] geverifieerd, kiest u in de lijst **[!UICONTROL Rapportsuite]** een [!DNL Adobe Analytics] rapportsuite waaruit u gegevens wilt ophalen met behulp van Asset Insights. Click **[!UICONTROL Add]**.
1. Nadat u de rapportsuite hebt [!DNL Experience Manager] ingesteld, klikt u op **[!UICONTROL Gereed]**.

## Paginatracering {#page-tracker}

Nadat u uw [!DNL Adobe Analytics] account hebt geconfigureerd, wordt de code van Paginanummer voor u gegenereerd. Neem de paginacontrackercode in de websitecode op om Elementen inzicht te geven in [!DNL Experience Manager] elementen die worden gebruikt op websites van derden. Gebruik het hulpprogramma [!UICONTROL Paginanummering] in [!DNL Experience Manager Assets] om de code van de paginacontracker te genereren. Zie Paginacontrole [gebruiken en code insluiten in webpagina&#39;s](/help/assets/touch-ui-using-page-tracker.md)voor meer informatie over het opnemen van uw code in Paginanummering in externe webpagina&#39;s.

1. In [!DNL Experience Manager], click **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klik op de pagina **[!UICONTROL Navigatie]** op de kaart voor **[!UICONTROL Insights-paginatracering]**.
1. Klik op **[!UICONTROL Downloaden]** om de code van de paginacontracker te downloaden.
