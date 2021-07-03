---
title: Assets Insights
description: Leer hoe u met behulp van Assets Insights gebruikersbeoordelingen en gebruiksstatistieken kunt bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen voor Adobe.
contentOwner: AG
role: User, Admin
feature: Asset Insights, Asset Reports
exl-id: 0130ac40-a72b-4caf-a10f-3c7d76eaa1e6
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 2%

---

# Assets Insights {#asset-insights}

Met de Assets Insights kunt u gebruikersbeoordelingen en gebruiksstatistieken bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen voor Adobe. Het helpt inzichten betreffende hun prestaties en populariteit af te leiden.

[!DNL Assets] Met deze inzichten worden gegevens over gebruikersactiviteit vastgelegd, zoals het aantal keren dat een afbeelding wordt beoordeeld, geklikt en de afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd.

Als u [!DNL Assets] inzichten wilt gebruiken om gebruiksstatistieken voor afbeeldingen van een website vast te leggen, moet u de insluitcode voor de afbeelding opnemen in de websitecode.

Om de statistieken van het de vertoningsgebruik van Activa van Inzichten voor activa te laten, vorm eerst de eigenschap om rapportgegevens van Adobe Analytics te halen. Voor details, zie [Elementen inzichten](/help/assets/configure-asset-insights.md) vormen. Als u deze functie wilt gebruiken in een on-premise installatie, moet u [!DNL Adobe Analytics] licentie afzonderlijk aanschaffen. Klanten op [!DNL Managed Services] ontvangen [!DNL Analytics] licentie gebundeld met [!DNL Experience Manager]. Zie [Managed Services productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

## Statistieken voor een afbeelding weergeven {#viewing-statistics-for-an-image}

U kunt de elementinzichten van de metagegevenspagina weergeven.

1. Selecteer de afbeelding in de gebruikersinterface [!DNL Assets] (UI) en klik op **[!UICONTROL Properties]** op de werkbalk.
1. Klik op het tabblad **[!UICONTROL Insights]** op de pagina Eigenschappen.
1. Controleer de gebruiksdetails voor het element op het tabblad **[!UICONTROL Insights]**. In de sectie **[!UICONTROL Score]** worden het totale gebruik en de prestatiesbronnen van een element beschreven.

   De score van het gebruik beschrijft het aantal tijden activa wordt gebruikt in diverse oplossingen.

   De **[!UICONTROL Impressions]** score is het aantal keren dat het element op de website wordt geladen. Het getal dat onder **[!UICONTROL Clicks]** wordt weergegeven, is het aantal keren dat op het element wordt geklikt.

1. Controleer de sectie **[!UICONTROL Usage Statistics]** om te weten van welke entiteiten het middel deel uitmaakte en welke creatieve oplossingen het onlangs gebruikten. Hoe hoger het gebruik, hoe groter de kans dat het middel populair is bij gebruikers. Gebruiksgegevens worden onder de volgende koppen weergegeven:

   * **Element**: Het aantal keren dat het actief deel uitmaakte van een collectie of samengesteld actief
   * **Web en mobiel**: Het aantal keren dat het middel deel uitmaakte van websites en apps
   * **Sociaal**: Het aantal keren dat het middel is gebruikt in oplossingen, zoals Adobe Social en Adobe Campaign
   * **E-mail**: Het aantal keren dat het middel in e-mailcampagnes is gebruikt

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Omdat de functie van de Inzichten van Activa typisch de gegevens van Oplossingen van Adobe Analytics op een periodieke manier haalt, kan de sectie van Oplossingen niet de meest recente gegevens tonen. De tijdspanne waarvoor de gegevens worden getoond hangt het programma van de haalverrichting af die de Inzichten van Activa in werking stellen om de gegevens van de Analyse terug te winnen.

1. Als u de prestatiestatistieken voor het element gedurende een bepaalde periode grafisch wilt weergeven, selecteert u een punt in de sectie **[!UICONTROL Performance Statistics]**. De details, inclusief klikken en impressies, worden getoond als trendlijnen van een grafiek.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >In tegenstelling tot de gegevens in de sectie van Oplossingen, toont de sectie van de Statistieken van Prestaties de meest recente gegevens.

1. Klik **[!UICONTROL Get Embed Code]** onder de elementminiatuur om de insluitcode te verkrijgen voor het element dat u in websites opneemt om prestatiegegevens op te halen. Voor meer informatie over hoe te om uw Embed code in derdeWeb-pagina&#39;s op te nemen, zie [het Gebruiken van de Traceur van de Pagina en bed code in Web-pagina&#39;s in](/help/assets/use-page-tracker.md).

   ![chlimage_1-98](assets/chlimage_1-303.png)

## Samengevoegde statistieken voor afbeeldingen weergeven {#viewing-aggregate-statistics-for-images}

U kunt de scores van alle elementen in een map tegelijkertijd weergeven met **[!UICONTROL Insights View]**.

1. Navigeer in de gebruikersinterface [!DNL Assets] naar de map met de elementen waarvoor u inzichten wilt weergeven.
1. Klik op Indeling op de werkbalk en kies **[!UICONTROL Insights View]**.
1. Op de pagina worden gebruiksscores voor de elementen weergegeven. Vergelijk de ratings van de verschillende activa en teken inzichten.

## Achtergrondtaak plannen {#scheduling-background-job}

Assets Insights haalt gebruiksgegevens voor middelen van Adobe Analytics op periodieke wijze. Door gebrek, stelt de Inzichten van Activa een achtergrondbaan om de 24 uur bij 2 AM in werking aan de ophaalgegevens. Nochtans, kunt u zowel de frequentie als de tijd wijzigen door de **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** dienst van de Webconsole te vormen.

1. Klik op het [!DNL Experience Manager]-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de serviceconfiguratie **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-99](assets/chlimage_1-304.png)

1. Specificeer de gewenste plannerfrequentie en de begintijd voor de baan in de uitdrukking van de bezitsplanner. Sla de wijzigingen op.
