---
title: Adobe-campagne als doel instellen
seo-title: Adobe-campagne als doel instellen
description: U kunt doelgerichte ervaringen voor Adobe Campagne maken nadat u segmentatie hebt ingesteld
seo-description: U kunt doelgerichte ervaringen voor Adobe Campagne maken nadat u segmentatie hebt ingesteld
uuid: 8fcc9210-d8c5-44e3-8aa8-6c6db810c98e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f1cb5e98-ccd1-4b2c-acca-2b3cc1b7ac5f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Adobe-campagne als doel instellen{#targeting-your-adobe-campaign}

Als u de Adobe Campagne-nieuwsbrief als doel wilt instellen, moet u eerst segmentatie instellen. Deze segmentatie is alleen beschikbaar in de klassieke gebruikersinterface (voor clientcontext). Daarna kunt u gerichte ervaringen voor de Campagne van Adobe creëren. Beide worden beschreven in deze sectie.

## Segmentatie instellen in AEM {#setting-up-segmentation-in-aem}

Als u segmentatie wilt instellen, moet u de klassieke UI gebruiken om de segmenten in te stellen. De overige stappen kunnen worden uitgevoerd in de standaardinterface.

De opstellingssegmentatie omvat het creëren van segmenten, een merk, een campagne, en ervaringen.

>[!NOTE]
>
>Segment-id moet worden toegewezen aan de id aan de zijde Adobe Campagne.

### Segmenten maken {#creating-segments}

Segmenten maken:

1. Open de [segmentatieconsole](http://localhost:4502/miscadmin#/etc/segmentation) op **&lt;host>:&lt;port>/miscadmin#/etc/segmentation**.
1. Maak een nieuwe pagina en voer een titel in, bijvoorbeeld **AC Segments**, en selecteer de sjabloon **Segment (Adobe Campaign)** .
1. Selecteer de gemaakte pagina in de structuurweergave aan de linkerkant.
1. Maak een segment, bijvoorbeeld voor mannelijke gebruikers, door een nieuwe pagina te maken onder het segment dat u met de naam Mannelijk hebt gemaakt en selecteer de sjabloon **Segment (Adobe Campaign)** .
1. Open de gemaakte segmentpagina en sleep een **segment-id** van de assistent naar de pagina.
1. Dubbelklik op de eigenschap, voer de id in die in dit geval wordt weergegeven, het mannelijke segment dat is gedefinieerd in Adobe Campaign (bijvoorbeeld **MALE** ) en klik op **OK**. Het volgende bericht moet worden weergegeven: *`targetData.segmentCode == "MALE"`*
1. Herhaal de stappen voor een ander segment, bijvoorbeeld een segment dat zich richt op vrouwelijke gebruikers.

### Een merk maken {#creating-a-brand}

Een merk maken:

1. Navigeer in **Sites** naar de map **Campagnes** (bijvoorbeeld in We.Retail).
1. Klik op Pagina **** maken en voer een titel voor de pagina in, bijvoorbeeld Wij.Handelsmerk en selecteer de sjabloon **Merk** .

### Een campagne maken {#creating-a-campaign}

Een campagne maken:

1. Open de pagina **Merk** die u net hebt gemaakt.
1. Klik op Pagina **** maken en voer een titel voor uw pagina in, bijvoorbeeld We.Retail-campagne, en selecteer de sjabloon **Campagne** en klik op **Maken**.

### Ervaringen maken {#creating-experiences}

Zo creëert u ervaringen voor segmenten:

1. Open de pagina **Campagne** die u net hebt gemaakt.
1. Maak ervaringen voor uw segmenten door te klikken op Pagina **** maken en een titel voor uw pagina in te voeren, bijvoorbeeld Mannelijk als u een ervaring voor het Mannelijke segment maakt, en de sjabloon **Ervaring** te selecteren.
1. Open de pagina voor het maken van ervaring.
1. Klik op **Bewerken** en klik vervolgens onder Segmenten op Item **** toevoegen.
1. Voer het pad naar het mannelijke segment in, bijvoorbeeld **/etc/segmentation/ac-segments/man** en klik op **OK**. Het volgende bericht moet worden weergegeven: De *ervaring is gericht op: Mannelijk*
1. Herhaal de vorige stappen om een ervaring voor alle segmenten, bijvoorbeeld het vrouwelijke doel tot stand te brengen.

## Een nieuwsbrief met doelinhoud maken {#creating-a-newsletter-with-targeted-content}

Nadat u segmenten, een merk, een campagne en een ervaring hebt gemaakt, kunt u een nieuwsbrief met gerichte inhoud maken. Nadat u de ervaring hebt gemaakt, koppelt u ervaringen aan uw segmenten.

>[!NOTE]
>
>[E-mailvoorbeelden zijn alleen beschikbaar in Geometrixx](/help/sites-developing/we-retail.md). Download voorbeeldinhoud van Geometrixx uit Pakket delen.

Een nieuwsbrief met doelinhoud maken:

1. Een nieuwsbrief met doelinhoud maken: Klik onder E-mailcampagnes in Geometrixx buiten, klik of tik op **Maken** > **Pagina** en selecteer een van de sjablonen voor Adobe Campagne Mail.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Voeg in de nieuwsbrief een component Tekst en Personalisatie toe.
1. Voeg tekst toe aan de component Tekst en Personalisatie, zoals &quot;Dit is de standaardinstelling&quot;.
1. Klik op de pijl naast **Bewerken** en selecteer **Doel**.
1. Selecteer uw merk in het keuzemenu Merk en selecteer uw Campagne. (Dit is het merk en de campagne die u eerder hebt gemaakt).
1. Klik op **Doelstelling** starten. U ziet de segmenten verschijnen in het gebied Soorten publiek. De standaardervaring wordt gebruikt als geen van de gedefinieerde segmenten overeenkomt.

   >[!NOTE]
   >
   >Standaard gebruiken de e-mailvoorbeelden die bij AEM worden geleverd Adobe Campaign als de doelengine. Voor aangepaste nieuwsbrieven moet u mogelijk Adobe Campaign selecteren als de doelengine. Tik of klik op + wanneer u een doelwit voor de nieuwe activiteit opgeeft, typ of klik op de werkbalk en selecteer **Adobe Campagne** als de doelengine.

1. Klik op **Standaard** en vervolgens op de component Tekst en personalisatie die u hebt toegevoegd en u ziet de opsomming met een pijl erin. Klik op het pictogram om deze component als doel in te stellen.

   ![chlimage_1-189](assets/chlimage_1-189.png)

1. Navigeer naar een ander segment (Mannelijk) en klik op Aanbieding **** toevoegen en klik op het plusteken +. Bewerk vervolgens het voorstel.
1. Navigeer naar een ander segment (Vrouwen) en klik op Aanbieding **** toevoegen en het plusteken +. Bewerk dit voorstel vervolgens.
1. Klik op **Volgende** om Toewijzing te bekijken en klik vervolgens op **Volgende** om de instellingen weer te geven die niet van toepassing zijn op Adobe Campagne. Klik vervolgens op **Opslaan**.

   AEM genereert automatisch de juiste doelcode voor Adobe Campaign wanneer de inhoud wordt gebruikt in een levering in Adobe Campaign

1. Maak in Adobe Campaign uw levering - selecteer **E-maillevering met AEM-inhoud** en selecteer de lokale AEM-account, al naar gelang wat van toepassing is, en bevestig uw wijzigingen.

   In de HTML-weergave staan de verschillende ervaringen van doelcomponenten in de Adobe-campagne voor code.

   ![chlimage_1-190](assets/chlimage_1-190.png)

   >[!NOTE]
   >
   >Als u de segmenten ook instelt in Adobe Campaign, kunt u door op **Voorvertoning** te klikken de ervaringen voor elk segment zien.

