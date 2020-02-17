---
title: Elementinzichten configureren
description: Elementinzichten in AEM-elementen configureren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6d4f79c126a3c44666e2a42b2246c964813d24ab

---


# Elementinzichten configureren {#configure-asset-insights}

Met Adobe Experience Manager (AEM) worden gebruiksgegevens opgehaald van AEM-elementen die door websites van derden worden gebruikt met Adobe Analytics. Als u Asset Insights wilt inschakelen om deze gegevens op te halen en inzichten te genereren, moet u eerst de functie configureren voor integratie met Adobe Analytics.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. Klik in AEM op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]**.

   ![chlimage_1-72](assets/chlimage_1-210.png)

1. Klik op de **[!UICONTROL inzichten Configuration]** -kaart.
1. Selecteer een datacenter in de wizard en geef uw referenties op, inclusief de naam van uw organisatie, gebruikersnaam en gedeeld geheim.

   ![Adobe Analytics voor Assets Insights configureren in AEM](assets/insights_config2.png)


   *Afbeelding: Adobe Analytics voor Assets Insights configureren in AEM*

1. Klik/tik **[!UICONTROL voor verifiëren]**.
1. Nadat AEM uw gegevens heeft geverifieerd, kiest u in de lijst **[!UICONTROL Report Suite]** een Adobe Analytics-rapportsuite waaruit u gegevens wilt ophalen met behulp van Asset Insights. Click **[!UICONTROL Add]**.
1. Nadat AEM uw rapportsuite heeft ingesteld, klikt of tikt u op **[!UICONTROL Gereed]**.

## Paginatracering {#page-tracker}

Nadat u uw Adobe Analytics-account hebt geconfigureerd, wordt de code van Paginanummer voor u gegenereerd. Als u Assets Insights wilt inschakelen om AEM-elementen die worden gebruikt op websites van derden bij te houden, neemt u de paginacontrackercode op in de websitecode. Gebruik het hulpprogramma Paginanummering in AEM Assets om de code van de paginacontracker te genereren. Zie Paginacontrole [gebruiken en code insluiten in webpagina&#39;s](/help/assets/touch-ui-using-page-tracker.md)voor meer informatie over het opnemen van uw code in Paginanummering in externe webpagina&#39;s.

1. Klik in AEM op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]**.

   ![chlimage_1-73](assets/chlimage_1-214.png)

1. Klik op de **[!UICONTROL navigatiepagina]** op de kaart voor **[!UICONTROL inzichten in paginanummering]** .
1. Klik op **[!UICONTROL Downloaden]** om de code van de paginacontracker te downloaden.
