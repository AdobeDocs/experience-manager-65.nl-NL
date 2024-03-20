---
title: Assets Insights
description: Leer hoe u met de functie Assets Insights gebruikersbeoordelingen en gebruiksstatistieken kunt bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van de Adobe.
contentOwner: AG
role: User, Admin
feature: Asset Insights,Asset Reports
exl-id: 0130ac40-a72b-4caf-a10f-3c7d76eaa1e6
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 2%

---

# Assets Insights {#asset-insights}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/assets-insights.html?lang=en) |
| AEM 6,5 | Dit artikel |

Met de functie Assets Insights kunt u gebruikersbeoordelingen en gebruiksstatistieken bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van de Adobe. Het helpt inzichten betreffende hun prestaties en populariteit af te leiden.

[!DNL Assets] Met deze inzichten worden gegevens over gebruikersactiviteit vastgelegd, zoals het aantal keren dat een afbeelding wordt beoordeeld, geklikt en de afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd.

Voor [!DNL Assets] Met de inzichten waarmee u gebruiksstatistieken voor afbeeldingen van een website kunt vastleggen, moet u de insluitcode voor de afbeelding opnemen in de websitecode.

Om de statistieken van het de vertoningsgebruik van Activa van Inzichten voor activa te laten, vorm eerst de eigenschap om rapportgegevens van Adobe Analytics te halen. Zie voor meer informatie [Elementengegevens configureren](/help/assets/configure-asset-insights.md). Als u deze functie wilt gebruiken in een installatie op locatie, kunt u [!DNL Adobe Analytics] licentie afzonderlijk. Klanten op [!DNL Managed Services] ontvangen [!DNL Analytics] licentie gebundeld met [!DNL Experience Manager]. Zie [Managed Services-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

## Statistieken voor een afbeelding weergeven {#viewing-statistics-for-an-image}

U kunt de elementinzichten van de metagegevenspagina weergeven.

1. Van de [!DNL Assets] gebruikersinterface (UI), selecteert het beeld en klikt dan **[!UICONTROL Properties]** op de werkbalk.
1. Klik op de pagina Eigenschappen op de knop **[!UICONTROL Insights]** tab.
1. Bekijk de gebruiksdetails voor het element in de **[!UICONTROL Insights]** tab. De **[!UICONTROL Score]** in dit gedeelte wordt het totale gebruik en de prestatiesbronnen van een actief beschreven.

   De score van het gebruik beschrijft het aantal tijden activa wordt gebruikt in diverse oplossingen.

   De **[!UICONTROL Impressions]** De score is het aantal keren dat het element op de website wordt geladen. Het nummer dat onder wordt weergegeven **[!UICONTROL Clicks]** is het aantal keren dat op het element wordt geklikt.

1. Controleer de **[!UICONTROL Usage Statistics]** sectie om te weten van welke entiteiten het actief deel uitmaakte en welke creatieve oplossingen het onlangs gebruikten. Hoe hoger het gebruik, hoe groter de kans dat het middel populair is bij gebruikers. Gebruiksgegevens worden onder de volgende koppen weergegeven:

   * **Element**: Het aantal keren dat het actief deel uitmaakte van een collectie of samengesteld actief
   * **Web en mobiel**: Het aantal keren dat het middel deel uitmaakte van websites en apps
   * **Sociaal**: Het aantal keren dat het middel is gebruikt in oplossingen, zoals Adobe Social en Adobe Campaign
   * **E-mail**: Het aantal keren dat het middel in e-mailcampagnes is gebruikt

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Omdat de functie van de Inzichten van Activa typisch de gegevens van Oplossingen van Adobe Analytics op een periodieke manier haalt, kan de sectie van Oplossingen niet de meest recente gegevens tonen. De tijdspanne waarvoor de gegevens worden getoond hangt het programma van de haalverrichting af die de Inzichten van Activa in werking stellen om de gegevens van de Analyse terug te winnen.

1. Als u de prestatiestatistieken voor het actief grafisch wilt weergeven over een bepaalde periode, selecteert u de periode in het dialoogvenster **[!UICONTROL Performance Statistics]** sectie. De details, inclusief klikken en impressies, worden getoond als trendlijnen van een grafiek.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >In tegenstelling tot de gegevens in de sectie van Oplossingen, toont de sectie van de Statistieken van Prestaties de meest recente gegevens.

1. Als u de insluitcode wilt verkrijgen voor het element dat u in websites opneemt om prestatiegegevens op te halen, klikt u op **[!UICONTROL Get Embed Code]** onder de elementminiatuur. Voor meer informatie over het opnemen van uw insluitcode in externe webpagina&#39;s raadpleegt u [Paginanummering gebruiken en code insluiten in webpagina&#39;s](/help/assets/use-page-tracker.md).

   ![chlimage_1-98](assets/chlimage_1-303.png)

## Samengevoegde statistieken voor afbeeldingen weergeven {#viewing-aggregate-statistics-for-images}

U kunt de scores van alle elementen in een map tegelijk weergeven met **[!UICONTROL Insights View]**.

1. In de [!DNL Assets] in de gebruikersinterface, navigeert u naar de map met de elementen waarvoor u inzichten wilt weergeven.
1. Klik op Indeling op de werkbalk en kies **[!UICONTROL Insights View]**.
1. Op de pagina worden gebruiksscores voor de elementen weergegeven. Vergelijk de ratings van de verschillende activa en teken inzichten.

## Achtergrondtaak plannen {#scheduling-background-job}

Assets Insights haalt gebruiksgegevens voor middelen van Adobe Analytics op periodieke wijze. Door gebrek, stelt de Inzichten van Activa een achtergrondbaan om de 24 uur bij 2 AM in werking aan de ophaalgegevens. Nochtans, kunt u zowel de frequentie als de tijd wijzigen door te vormen **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** van de webconsole.

1. Klik op de knop [!DNL Experience Manager] logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** serviceconfiguratie.

   ![chlimage_1-99](assets/chlimage_1-304.png)

1. Specificeer de gewenste plannerfrequentie en de begintijd voor de baan in de uitdrukking van de bezitsplanner. Sla de wijzigingen op.
