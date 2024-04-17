---
title: Je Adobe Campaign als doelgroep instellen
description: De opstellingssegmentatie omvat het creëren van segmenten, een merk, een campagne, en ervaringen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: e56986b2-397e-4802-992b-05a9ea7b2e36
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# Je Adobe Campaign als doelgroep instellen{#targeting-your-adobe-campaign}

Als u uw Adobe Campaign-nieuwsbrief als doel wilt instellen, moet u eerst segmentatie instellen. Deze is alleen beschikbaar in de klassieke gebruikersinterface. Daarna kunt u gerichte ervaringen voor Adobe Campaign maken.

## Segmentatie instellen in AEM {#setting-up-segmentation-in-aem}

De opstellingssegmentatie omvat het creëren van segmenten, een merk, een campagne, en ervaringen. U kunt slechts een segment in klassieke UI tot stand brengen. U kunt merken, campagnes en ervaringen maken in de interface met aanraakbediening.

>[!NOTE]
>
>Segment-id moet worden toegewezen aan de segment aan de Adobe Campaign-zijde.

### Segmenten maken {#creating-segments}

Segmenten maken:

1. Open de [segmentatieconsole](http://localhost:4502/miscadmin#/etc/segmentation) om **&lt;host>:&lt;port>/miscadmin#/etc/segmentatie**.
1. Maak een pagina en voer een titel in, bijvoorbeeld **AC-segmenten** - en selecteer de **Segment (Adobe Campaign)** sjabloon.
1. Selecteer de gemaakte pagina in de structuurweergave aan de linkerkant.
1. Maak bijvoorbeeld een segment voor mannelijke gebruikers door een pagina te maken onder het segment dat u met de naam Mannelijk hebt gemaakt en selecteer de optie **Segment (Adobe Campaign)** sjabloon.
1. Open de gemaakte segmentpagina en sleep een **Segment-id** van het hulpje naar de pagina.
1. Dubbelklik op het kenmerk, voer in dit geval de id in die het mannelijke segment vertegenwoordigt dat in Adobe Campaign is gedefinieerd, bijvoorbeeld: **MALE** - en klik op **OK**. Het volgende bericht moet worden weergegeven: `targetData.segmentCode == "MALE"`
1. Herhaal de stappen voor een ander segment, bijvoorbeeld een segment dat zich richt op vrouwelijke gebruikers.

### Een merk maken {#creating-a-brand}

Een merk maken:

1. In **Sites**, navigeert u naar de **Campagnes** map (bijvoorbeeld in We.Retail).
1. Klikken **Pagina maken** en voer een titel voor de pagina in, bijvoorbeeld We.Retail Brand en selecteer de **Merk** sjabloon.

### Een campagne maken {#creating-a-campaign}

Een campagne maken:

1. Open de **Merk** pagina die u hebt gemaakt.
1. Klikken **Pagina maken** en voer een titel in voor uw pagina, bijvoorbeeld Wij.Handelscampagne, en selecteer de **Campagne** sjabloon en klik op **Maken**.

### Ervaringen maken {#creating-experiences}

Zo creëert u ervaringen voor segmenten:

1. Open de **Campagne** pagina die u hebt gemaakt.
1. Maak ervaringen voor uw segmenten door op **Pagina maken** en voert u een titel in voor uw pagina, bijvoorbeeld Mannelijk terwijl u een ervaring maakt voor het Mannelijke segment, en selecteert u de optie **Ervaring** sjabloon.
1. Open de pagina voor het maken van ervaring.
1. Klikken **Bewerken** en klik vervolgens onder Segmenten op **Item toevoegen**.
1. Voer bijvoorbeeld het pad naar het mannelijke segment in. `/etc/segmentation/ac-segments/male` en klik op **OK**. Het volgende bericht moet worden weergegeven: *De ervaring is gericht op: Mannelijk*
1. Herhaal de vorige stappen om een ervaring voor alle segmenten, bijvoorbeeld, het vrouwelijke doel tot stand te brengen.

## Een nieuwsbrief met doelinhoud maken {#creating-a-newsletter-with-targeted-content}

Nadat u segmenten, een merk, een campagne en een ervaring hebt gemaakt, kunt u een nieuwsbrief met gerichte inhoud maken. Nadat u de ervaring hebt gemaakt, koppelt u ervaringen aan uw segmenten.

U kunt de nieuwsbrief met gerichte inhoud in zowel aanraking-toegelaten als klassieke gebruikersinterface tot stand brengen. In dit document wordt de procedure beschreven voor de interface met aanraakbediening.

Een nieuwsbrief met doelinhoud maken:

1. Een nieuwsbrief met de gewenste inhoud maken: klik onder E-mailcampagnes in Geometrixx Outdoors op **Maken** > **Pagina** en selecteer een van de Adobe Campaign Mail-sjablonen.

   >[!NOTE]
   >
   >[E-mailvoorbeelden zijn alleen beschikbaar in Geometrixx](/help/sites-developing/we-retail.md#weretail). Download voorbeeldinhoud van het Geometrixx van het Pakket Delen.

1. Voeg in de nieuwsbrief een component Tekst en Personalisatie toe.
1. Voeg tekst toe aan de component Tekst en Personalisatie, zoals &quot;Dit is de standaardinstelling&quot;.
1. Klik op de pijl naast **Bewerken** en selecteert u **Targeting**.
1. Selecteer uw merk in het keuzemenu Merk en selecteer uw Campagne. (Dit is het merk en de campagne die u eerder hebt gemaakt).
1. Klikken **Doelstelling starten**. U ziet de segmenten verschijnen in het gebied Soorten publiek. De standaardervaring wordt gebruikt als geen van de gedefinieerde segmenten overeenkomt.

   >[!NOTE]
   >
   >Standaard gebruiken de e-mailvoorbeelden die bij AEM worden geleverd Adobe Campaign als de doelengine. Voor aangepaste nieuwsbrieven moet u wellicht Adobe Campaign selecteren als de doelengine. Klik + op de werkbalk als u een doel instelt, voer een titel in voor de nieuwe activiteit en selecteer **Adobe Campaign** als de doelmotor.

1. Klikken **Standaard** en dan de component van de Tekst en van de Personalisatie u toevoegde en u ziet de Bullseye met een pijl in het. Klik op het pictogram om deze component als doel in te stellen.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Navigeer naar een ander segment (Mannelijk) en klik **Voorstel toevoegen** en klik op het plusteken +. Bewerk vervolgens het voorstel.
1. Navigeer naar een ander segment (Vrouwelijk) en klik op **Voorstel toevoegen** en het plusteken +. Bewerk dit voorstel vervolgens.
1. Klikken **Volgende** om Toewijzing te zien, klikt u vervolgens op **Volgende** om Settings weer te geven, die niet van toepassing is op Adobe Campaign, en klik op **Opslaan**.

   AEM genereert automatisch de juiste doelcode voor Adobe Campaign wanneer de inhoud wordt gebruikt in een levering binnen Adobe Campaign

1. Maak in Adobe Campaign je levering - selecteer **E-maillevering met AEM inhoud** en selecteer het lokale AEM account, al naar het geval, en bevestig uw wijzigingen.

   In de weergave HTML staan de verschillende ervaringen van doelcomponenten in Adobe Campaign-code voor doelcomponenten.

   ![chlimage_1-166](assets/chlimage_1-166.png)

   >[!NOTE]
   >
   >Als u de segmenten ook instelt in Adobe Campaign, klikt u op **Voorvertoning** zal u de ervaringen voor elk segment tonen.
