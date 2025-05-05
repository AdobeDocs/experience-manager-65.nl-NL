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
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/assets-insights.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Met de functie Assets Insights kunt u gebruikersbeoordelingen en gebruiksstatistieken bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van de Adobe. Het helpt inzichten betreffende hun prestaties en populariteit af te leiden.

[!DNL Assets] Met deze inzichten worden gegevens over gebruikersactiviteit vastgelegd, zoals het aantal keer dat een afbeelding wordt beoordeeld, geklikt en afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd.

Als u met [!DNL Assets] inzichten gebruiksstatistieken wilt vastleggen voor afbeeldingen van een website, moet u de insluitcode voor de afbeelding opnemen in de websitecode.

Om Assets Insights gebruiksstatistieken voor activa te laten weergeven, configureert u eerst de functie voor het ophalen van rapportgegevens uit Adobe Analytics. Voor details, zie [ de Inzichten van Assets ](/help/assets/configure-asset-insights.md) vormen. Als u deze functie in een on-premise installatie wilt gebruiken, moet u de [!DNL Adobe Analytics] -licentie afzonderlijk aanschaffen. Klanten op [!DNL Managed Services] ontvangen een [!DNL Analytics] -licentie die is gebundeld met [!DNL Experience Manager] . Zie [ Managed Services productbeschrijving ](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

## Statistieken voor een afbeelding weergeven {#viewing-statistics-for-an-image}

U kunt de Assets Insights-scores bekijken op de metagegevenspagina.

1. Selecteer de afbeelding in de gebruikersinterface van [!DNL Assets] (UI) en klik vervolgens op **[!UICONTROL Properties]** op de werkbalk.
1. Klik op de pagina Eigenschappen op de tab **[!UICONTROL Insights]** .
1. Controleer de gebruiksdetails voor het element op het tabblad **[!UICONTROL Insights]** . In de sectie **[!UICONTROL Score]** worden het totale gebruik en de prestatiesbronnen van een element beschreven.

   De score van het gebruik beschrijft het aantal tijden activa wordt gebruikt in diverse oplossingen.

   De **[!UICONTROL Impressions]** score is het aantal keren dat het element op de website wordt geladen. Het getal dat onder **[!UICONTROL Clicks]** wordt weergegeven, is het aantal keren dat op het element wordt geklikt.

1. Controleer de sectie **[!UICONTROL Usage Statistics]** om te weten van welke entiteiten het element deel uitmaakte en welke creatieve oplossingen het onlangs hebben gebruikt. Hoe hoger het gebruik, hoe groter de kans dat het middel populair is bij gebruikers. Gebruiksgegevens worden onder de volgende koppen weergegeven:

   * **Activa**: Het aantal tijden het middel deel van een inzameling of een samengesteld middel maakte
   * **Web &amp; Mobiel**: Het aantal tijden het middel deel van websites en apps maakte
   * **Sociaal**: Het aantal tijden de activa in oplossingen, zoals Adobe Social en Adobe Campaign werden gebruikt
   * **E-mail**: Het aantal tijden de activa in e-mailcampagnes werden gebruikt

   ![ usage_statistics ](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Omdat de functie Assets Insights de gegevens van Oplossingen doorgaans periodiek van Adobe Analytics ophaalt, wordt in de sectie Oplossingen mogelijk niet de meest recente gegevens weergegeven. De tijdsperiode waarvoor de gegevens worden weergegeven, is afhankelijk van het schema van de ophaalbewerking die Assets Insights uitvoert om analysegegevens op te halen.

1. Als u de prestatiestatistieken voor het element gedurende een bepaalde periode grafisch wilt weergeven, selecteert u een punt in de sectie **[!UICONTROL Performance Statistics]** . De details, inclusief klikken en impressies, worden getoond als trendlijnen van een grafiek.

   ![ chlimage_1-3 ](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >In tegenstelling tot de gegevens in de sectie van Oplossingen, toont de sectie van de Statistieken van Prestaties de meest recente gegevens.

1. Klik op **[!UICONTROL Get Embed Code]** onder de elementminiatuur om de insluitcode te verkrijgen voor het element dat u in websites opneemt om prestatiegegevens op te halen. Voor meer informatie over hoe te om uw Embed code in derdeWeb-pagina&#39;s te omvatten, zie [ Gebruikend de Traceur van de Pagina en bed code in Web-pagina&#39;s ](/help/assets/use-page-tracker.md) in.

   ![ chlimage_1-98 ](assets/chlimage_1-303.png)

## Samengevoegde statistieken voor afbeeldingen weergeven {#viewing-aggregate-statistics-for-images}

U kunt scores van alle elementen in een map tegelijk weergeven met **[!UICONTROL Insights View]** .

1. Navigeer in de gebruikersinterface van [!DNL Assets] naar de map met de elementen waarvoor u inzichten wilt weergeven.
1. Klik op Indeling op de werkbalk en kies vervolgens **[!UICONTROL Insights View]** .
1. Op de pagina worden gebruiksscores voor de elementen weergegeven. Vergelijk de ratings van de verschillende activa en teken inzichten.

## Achtergrondtaak plannen {#scheduling-background-job}

Assets Insights haalt op periodieke wijze gebruiksgegevens voor middelen van Adobe Analytics-rapportreeksen op. Standaard voert Assets Insights elke 24 uur om 2 uur een achtergrondtaak uit naar de opgehaalde gegevens. U kunt echter zowel de frequentie als de tijd aanpassen door de **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** -service vanuit de webconsole te configureren.

1. Klik op het logo [!DNL Experience Manager] en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** .
1. Open de serviceconfiguratie van **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** .

   ![ chlimage_1-99 ](assets/chlimage_1-304.png)

1. Specificeer de gewenste plannerfrequentie en de begintijd voor de baan in de uitdrukking van de bezitsplanner. Sla de wijzigingen op.
