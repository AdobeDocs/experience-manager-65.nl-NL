---
title: Je Adobe Campaign als doelgroep instellen
seo-title: Je Adobe Campaign als doelgroep instellen
description: De opstellingssegmentatie omvat het creëren van segmenten, een merk, een campagne, en ervaringen.
seo-description: De opstellingssegmentatie omvat het creëren van segmenten, een merk, een campagne, en ervaringen.
uuid: 520cd006-0aa8-43f3-b754-efb7397bb92f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: bbc2aac9-ccf1-40c3-be4f-d59c2d0d8a6c
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---


# Uw Adobe Campaign{#targeting-your-adobe-campaign} aanwijzen

Als u uw Adobe Campaign-nieuwsbrief als doel wilt instellen, moet u eerst segmentatie instellen. Deze is alleen beschikbaar in de klassieke gebruikersinterface. Daarna kunt u gerichte ervaringen voor Adobe Campaign maken.

## Segmentatie instellen in AEM {#setting-up-segmentation-in-aem}

De opstellingssegmentatie omvat het creëren van segmenten, een merk, een campagne, en ervaringen. U kunt alleen een segment maken in de klassieke UI. U kunt merken, campagnes en ervaringen maken in de interface met aanraakbediening.

>[!NOTE]
>
>Segment-id moet worden toegewezen aan de segment aan de Adobe Campaign-zijde.

### Segmenten {#creating-segments} maken

Segmenten maken:

1. Open de [segmentatieconsole](http://localhost:4502/miscadmin#/etc/segmentation) op **&lt;host>:&lt;port>/miscadmin#/etc/segmentation**.
1. Maak een nieuwe pagina en voer een titel in - bijvoorbeeld **AC Segments** - en selecteer de sjabloon **Segment (Adobe Campaign)**.
1. Selecteer de gemaakte pagina in de structuurweergave aan de linkerkant.
1. Maak een segment, bijvoorbeeld voor mannelijke gebruikers, door een nieuwe pagina te maken onder het segment dat u met de naam Mannelijk hebt gemaakt en selecteer de sjabloon **Segment (Adobe Campaign)**.
1. Open de gemaakte segmentpagina en sleep een **Segment-id** van het hulpstuk naar de pagina.
1. Dubbelklik op het kenmerk, voer in dit geval de id in die staat, het mannelijke segment dat in Adobe Campaign is gedefinieerd - bijvoorbeeld **MALE** - en klik op **OK**. Het volgende bericht moet worden weergegeven: `targetData.segmentCode == "MALE"`
1. Herhaal de stappen voor een ander segment, bijvoorbeeld een segment dat zich richt op vrouwelijke gebruikers.

### Een merk maken {#creating-a-brand}

Een merk maken:

1. Navigeer in **Sites** naar de map **Campagnes** (bijvoorbeeld in We.Retail).
1. Klik **Create Pagina** en ga een titel voor de pagina in, bijvoorbeeld Wij.Retail Brand en selecteer **Merk** malplaatje.

### Een campagne maken {#creating-a-campaign}

Een campagne maken:

1. Open de pagina **Merk** die u net hebt gemaakt.
1. Klik **Create Pagina** en ga een titel voor uw pagina in, bijvoorbeeld, Wij.Retail Campaign, en selecteer **Campagne** malplaatje en klik **Create**.

### Ervaringen maken {#creating-experiences}

Zo creëert u ervaringen voor segmenten:

1. Open de pagina **Campagne** die u net hebt gemaakt.
1. Maak ervaringen voor uw segmenten door te klikken op **Pagina maken** en een titel voor uw pagina in te voeren, bijvoorbeeld Mannelijk terwijl u een ervaring voor het Mannelijke segment maakt, en selecteer de sjabloon **Experience**.
1. Open de pagina voor het maken van ervaring.
1. Klik **Edit**, dan onder Segmenten klik **Add Punt**.
1. Voer het pad naar het mannelijke segment in, bijvoorbeeld `/etc/segmentation/ac-segments/male` en klik op **OK**. Het volgende bericht moet worden weergegeven: *De ervaring is gericht op: Mannelijk*
1. Herhaal de vorige stappen om een ervaring voor alle segmenten, bijvoorbeeld het vrouwelijke doel tot stand te brengen.

## Een nieuwsbrief met doelinhoud maken {#creating-a-newsletter-with-targeted-content}

Nadat u segmenten, een merk, een campagne en een ervaring hebt gemaakt, kunt u een nieuwsbrief met gerichte inhoud maken. Nadat u de ervaring hebt gemaakt, koppelt u ervaringen aan uw segmenten.

U kunt de nieuwsbrief met gerichte inhoud in zowel aanraking-toegelaten als klassieke gebruikersinterface tot stand brengen. In dit document wordt de procedure beschreven voor de interface met aanraakbediening.

Een nieuwsbrief met doelinhoud maken:

1. Een nieuwsbrief met doelinhoud maken: Klik of tik onder E-mailcampagnes in Geometrixx Outdoors op **Maken** > **Pagina** en selecteer een van de Adobe Campaign Mail-sjablonen.

   >[!NOTE]
   >
   >[E-mailvoorbeelden zijn alleen beschikbaar in Geometrixx](/help/sites-developing/we-retail.md#weretail). Download voorbeeldinhoud van Geometrixx uit Pakket delen.

1. Voeg in de nieuwsbrief een component Tekst en Personalisatie toe.
1. Voeg tekst toe aan de component Tekst en Personalisatie, zoals &quot;Dit is de standaardinstelling&quot;.
1. Klik op de pijl naast **Edit** en selecteer **Targeting**.
1. Selecteer uw merk in het keuzemenu Merk en selecteer uw Campagne. (Dit is het merk en de campagne die u eerder hebt gemaakt).
1. Klik **Beginnen met richten**. U ziet de segmenten verschijnen in het gebied Soorten publiek. De standaardervaring wordt gebruikt als geen van de gedefinieerde segmenten overeenkomt.

   >[!NOTE]
   >
   >Standaard gebruiken de e-mailvoorbeelden die bij AEM worden geleverd Adobe Campaign als de doelengine. Voor aangepaste nieuwsbrieven moet u wellicht Adobe Campaign selecteren als de doelengine. Tik op of klik op + op de werkbalk als u een doelversie van de nieuwe activiteit wilt opgeven en selecteer **Adobe Campaign** als de doelengine.

1. Klik **Standaard** en dan de component van de Tekst en van de Personalisatie u toevoegde en u ziet de Bullseye met een pijl in het. Klik op het pictogram om deze component als doel in te stellen.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Navigeer naar een ander segment (Mannelijk) en klik op **Aanbieding toevoegen** en klik op het plusteken +. Bewerk vervolgens het voorstel.
1. Navigeer naar een ander segment (Vrouwelijk) en klik op **Aanbieding toevoegen** en het plusteken +. Bewerk dit voorstel vervolgens.
1. Klik **Volgende** om Afbeelding te zien, dan klik **Volgende** om Instellingen te zien, die niet van toepassing zijn op Adobe Campaign, en klik **Opslaan**.

   AEM genereert automatisch de juiste doelcode voor Adobe Campaign wanneer de inhoud wordt gebruikt in een levering binnen Adobe Campaign

1. Maak in Adobe Campaign uw levering. Selecteer **E-maillevering met AEM inhoud** en selecteer het lokale AEM-account, al naar gelang wat van toepassing is, en bevestig uw wijzigingen.

   In de HTML-weergave staan de verschillende ervaringen van doelcomponenten in Adobe Campaign-code voor doelcomponenten.

   ![chlimage_1-166](assets/chlimage_1-166.png)

   >[!NOTE]
   >
   >Als u de segmenten ook in Adobe Campaign plaatst, zal het klikken **Voorproef** u de ervaringen voor elk segment tonen.

