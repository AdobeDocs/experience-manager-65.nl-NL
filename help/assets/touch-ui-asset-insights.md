---
title: Asset Insights
description: Leer hoe u met de functie Asset Insights gebruikersbeoordelingen en gebruiksstatistieken kunt bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van Adobe.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Asset Insights {#asset-insights}

Met de functie Asset Insights kunt u gebruikersbeoordelingen en gebruiksstatistieken bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van Adobe. Het helpt inzichten betreffende hun prestaties en populariteit af te leiden.

Met Elementinzichten worden gegevens over gebruikersactiviteit vastgelegd, zoals het aantal keer dat een afbeelding wordt beoordeeld, geklikt en afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd.

Als u met behulp van Assets gebruiksstatistieken wilt vastleggen voor afbeeldingen van een website, moet u de insluitcode voor de afbeelding opnemen in de websitecode.

Als u het gebruik van bedrijfsgegevens voor elementen wilt laten weergeven, configureert u eerst de functie voor het ophalen van rapportgegevens van Adobe Analytics. Zie [Elementinzichten](/help/assets/touch-ui-configuring-asset-insights.md)configureren voor meer informatie.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

## Statistieken voor een afbeelding weergeven {#viewing-statistics-for-an-image}

U kunt de Asset Insights-scores van de metagegevenspagina weergeven.

1. Selecteer de afbeelding in de gebruikersinterface Elementen en tik/klik vervolgens op **[!UICONTROL Eigenschappen]** op de werkbalk.
1. Tik op of klik op het tabblad **[!UICONTROL Inzichten]** op de pagina Eigenschappen.
1. Controleer de gebruiksdetails voor het element op het tabblad **[!UICONTROL Inzichten]** . In de sectie **[!UICONTROL Score]** worden het totale gebruik en de prestatiesbronnen van een element beschreven.

   De score van het gebruik beschrijft het aantal tijden activa wordt gebruikt in diverse oplossingen.

   De **[!UICONTROL score Impressions]** is het aantal keren dat het element op de website wordt geladen. Het getal dat onder **[!UICONTROL Klikken]** wordt weergegeven, is het aantal keren dat op het element wordt geklikt.

1. Controleer de sectie **[!UICONTROL Gebruiksstatistieken]** om te weten bij welke entiteiten het element hoort en welke creatieve oplossingen het onlangs hebben gebruikt. Hoe hoger het gebruik, hoe groter de kans dat het middel populair is bij gebruikers. Gebruiksgegevens worden onder de volgende koppen weergegeven:

   * **Element**: Het aantal keren dat het actief deel uitmaakte van een collectie of samengesteld actief
   * **Web en mobiel**: Het aantal keren dat het middel deel uitmaakte van websites en apps
   * **Sociaal**: Het aantal keren dat het middel is gebruikt in oplossingen, zoals Adobe Social en Adobe Campaign
   * **E-mail**: Het aantal keren dat het middel in e-mailcampagnes is gebruikt
   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Omdat de functie Asset Insights de gegevens van Oplossingen gewoonlijk periodiek ophaalt van Adobe Analytics, wordt in de sectie Oplossingen mogelijk niet de meest recente gegevens weergegeven. De tijdspanne waarvoor de gegevens worden getoond hangt het programma van de haalverrichting af die de Inzichten van Activa loopt om de gegevens van de Analyse terug te winnen.

1. Om prestatiesstatistieken voor het actief grafisch over een periode te bekijken, selecteer periode in de sectie van de Statistieken **[!UICONTROL van]** Prestaties. De details, met inbegrip van kliks en impressies worden getoond als trendlijnen van een grafiek.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >In tegenstelling tot de gegevens in de sectie van Oplossingen, toont de sectie van de Statistieken van Prestaties de meest recente gegevens.

1. Tik op de **[!UICONTROL knop Insluitcode]** ophalen onder de elementminiatuur om de insluitcode te verkrijgen voor het element dat u in websites opneemt om prestatiegegevens op te halen. Zie [Werken met paginanummering en code insluiten in webpagina&#39;s van derden voor meer informatie over het opnemen van uw insluitcode in webpagina&#39;s](/help/assets/touch-ui-using-page-tracker.md).

   ![chlimage_1-98](assets/chlimage_1-303.png)

## Samengevoegde statistieken voor afbeeldingen weergeven {#viewing-aggregate-statistics-for-images}

U kunt scores van alle elementen in een map tegelijk weergeven met de **[!UICONTROL weergave]** Inzichten.

1. Navigeer in de gebruikersinterface Elementen naar de map met de elementen waarvoor u inzichten wilt weergeven.
1. Tik/klik op het pictogram Lay-out op de werkbalk en kies vervolgens **[!UICONTROL Inzichtsweergave]**.
1. Op de pagina worden gebruiksscores voor de elementen weergegeven. Vergelijk de ratings van de verschillende activa en teken inzichten.

## Achtergrondtaak plannen {#scheduling-background-job}

Asset Insights haalt op periodieke wijze gebruiksgegevens voor middelen op uit Adobe Analytics-rapportreeksen. Door gebrek, stelt de Inzichten van Activa een achtergrondbaan om de 24 uur bij 2 AM aan de ophaalgegevens in werking. U kunt echter zowel de frequentie als de tijd aanpassen door de **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** Service via de webconsole te configureren.

1. Tik op het AEM-logo en ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**.
1. Open de configuratie van de **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** Service.

   ![chlimage_1-99](assets/chlimage_1-304.png)

1. Specificeer de gewenste plannerfrequentie en de begintijd voor de baan in de uitdrukking van de bezitsplanner. Sla de wijzigingen op.
