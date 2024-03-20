---
title: Video-uitvoeringen
description: Leer hoe u Adobe Experience Manager Assets kunt gebruiken om video-uitvoeringen te genereren voor video-elementen van verschillende indelingen, zoals OGG, FLV enzovoort.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
exl-id: a644558e-5be9-4ba2-b560-fc300497fbdf
solution: Experience Manager, Experience Manager Assets
feature: Video
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Video-uitvoeringen {#video-renditions}

Adobe Experience Manager Assets genereert video-uitvoeringen voor video-elementen van verschillende indelingen, zoals OGG, FLV enzovoort.

Experience Manager Assets ondersteunt statische en dynamische uitvoeringen (met DM gecodeerde uitvoeringen) voor media-elementen.

Statische uitvoeringen worden native gegenereerd met behulp van FFMPEG (geïnstalleerd en beschikbaar op het systeempad) en opgeslagen in de inhoudsopslagplaats.

De met DM gecodeerde vertoningen worden opgeslagen in de volmachtsserver en bij runtime gediend.

Experience Manager Assets biedt afspeelondersteuning voor deze uitvoeringen op de client.

Als u de vertoningen van een bepaald video-element wilt weergeven, opent u de elementenpagina en selecteert u het pictogram Algemene navigatie. Kies vervolgens **[!UICONTROL Renditions]** in de lijst.

![chlimage_1-478](assets/chlimage_1-478.png)

De lijst met video-uitvoeringen wordt weergegeven in het dialoogvenster **[!UICONTROL Renditions]** deelvenster.

![chlimage_1-479](assets/chlimage_1-479.png)

De proxyserver configureren voor met DM gecodeerde uitvoeringen, [Dynamic Media Cloud-services configureren](config-dynamic.md).

Video-uitvoeringen genereren met de gewenste parameters, [een overeenkomstig videoprofiel maken](video-profiles.md).

Nadat u de proxyserver hebt geconfigureerd en videoprofielen hebt gemaakt, kunt u deze videovoorinstelling opnemen in een verwerkingsprofiel en het verwerkingsprofiel toepassen op een map.

>[!NOTE]
>
>Audio afspelen werkt niet voor OGG- en WAV-bestanden in Microsoft® Internet Explorer 11. Een fout `Invalid Source` wordt weergegeven op de pagina met elementdetails voor elementen met de extensie OGG of WAV.
>
>In MS® Edge en iPad worden OGG-bestanden niet afgespeeld en wordt een niet-ondersteunde indelingsfout weergegeven.
