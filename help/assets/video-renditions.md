---
title: Video-uitvoeringen
description: Video-uitvoeringen
uuid: a02f9ec1-30d9-4cbb-8746-8391ac614f0a
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: 1601b473-7227-4a56-bb7c-289de2987e4b
exl-id: a644558e-5be9-4ba2-b560-fc300497fbdf
source-git-commit: 77687a0674b939460bd34011ee1b94bd4db50ba4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Video-uitvoeringen {#video-renditions}

Adobe Experience Manager Assets genereert video-uitvoeringen voor video-elementen van verschillende indelingen, zoals OGG, FLV enzovoort.

Experience Manager-elementen ondersteunen statische en dynamische uitvoeringen (met DM gecodeerde uitvoeringen) voor media-elementen.

Statische uitvoeringen worden native gegenereerd met behulp van FFMPEG (geïnstalleerd en beschikbaar op het systeempad) en opgeslagen in de inhoudsopslagplaats.

De met DM gecodeerde vertoningen worden opgeslagen in de volmachtsserver en bij runtime gediend.

Experience Manager Assets biedt ondersteuning voor het afspelen van deze uitvoeringen aan de clientzijde.

Als u de vertoningen van een bepaald video-element wilt weergeven, opent u de elementenpagina en selecteert u het pictogram Algemene navigatie. Kies vervolgens **[!UICONTROL Renditions]** in de lijst.

![chlimage_1-478](assets/chlimage_1-478.png)

De lijst met video-uitvoeringen wordt weergegeven in het deelvenster **[!UICONTROL Renditions]**.

![chlimage_1-479](assets/chlimage_1-479.png)

[configureer Dynamic Media Cloud-services](config-dynamic.md) om de proxyserver voor met DM gecodeerde uitvoeringen te configureren.

[Maak een overeenkomstig videoprofiel](video-profiles.md) om video-uitvoeringen met de gewenste parameters te genereren.

Nadat u de proxyserver hebt geconfigureerd en videoprofielen hebt gemaakt, kunt u deze videovoorinstelling opnemen in een verwerkingsprofiel en het verwerkingsprofiel toepassen op een map.

>[!NOTE]
>
>Het afspelen van audio werkt niet voor OGG- en WAV-bestanden in Microsoft® Internet Explorer 11. Er wordt een fout `Invalid Source` weergegeven op de pagina met elementdetails voor elementen met de extensie OGG of WAV.
>
>In MS® Edge en iPad worden OGG-bestanden niet afgespeeld en wordt een niet-ondersteunde indelingsfout gegenereerd.
