---
title: Video-uitvoeringen
description: Video-uitvoeringen
uuid: a02f9ec1-30d9-4cbb-8746-8391ac614f0a
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: 1601b473-7227-4a56-bb7c-289de2987e4b
translation-type: tm+mt
source-git-commit: 66f46a34832254af74c72da16ec8ebe3eb8cd46d

---


# Video-uitvoeringen {#video-renditions}

Met Adobe Experience Manager (AEM) kunt u video-uitvoeringen genereren voor video-elementen van verschillende indelingen, zoals OGG, FLV enzovoort.

AEM-elementen ondersteunen statische en dynamische uitvoeringen (met DM gecodeerde uitvoeringen) voor media-elementen.

Statische uitvoeringen worden native gegenereerd met behulp van FFMPEG (geïnstalleerd en beschikbaar op het systeempad) en opgeslagen in de inhoudsopslagplaats.

De met DM gecodeerde vertoningen worden opgeslagen in de volmachtsserver en bij runtime gediend.

AEM-elementen bieden afspeelondersteuning voor deze uitvoeringen aan de clientzijde.

Als u de vertoningen van een bepaald video-element wilt weergeven, opent u de elementenpagina en tikt u op het pictogram Algemene navigatie. Kies vervolgens **[!UICONTROL Uitvoeringen]** in de lijst.

![chlimage_1-478](assets/chlimage_1-478.png)

De lijst met video-uitvoeringen wordt weergegeven in het deelvenster **[!UICONTROL Uitvoeringen]** .

![chlimage_1-479](assets/chlimage_1-479.png)

Om de volmachtsserver voor DM-Gecodeerde vertoningen te vormen, [vorm de Dynamische Diensten van de Wolk van Media.](config-dynamic.md)

Als u video-uitvoeringen met de gewenste parameters wilt genereren, [maakt u een overeenkomstig videoprofiel](video-profiles.md).

Nadat u de proxyserver hebt geconfigureerd en videoprofielen hebt gemaakt, kunt u deze videovoorinstelling opnemen in een verwerkingsprofiel en het verwerkingsprofiel toepassen op een map.

>[!NOTE]
>
>Het afspelen van audio werkt niet voor OGG- en WAV-bestanden in Microsoft Internet Explorer 11. Er wordt een fout weergegeven op de pagina met elementdetails voor elementen met de extensie OGG of WAV. `Invalid Source`
>
>Op MS Edge en iPad worden OGG-bestanden niet afgespeeld en wordt een niet-ondersteunde indelingsfout gegenereerd.
