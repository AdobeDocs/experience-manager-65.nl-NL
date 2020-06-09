---
title: De Dynamic Media Video- of Image-viewer insluiten op een webpagina
description: Leer hoe u video of afbeeldingen van dynamische media op een webpagina insluit
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
translation-type: tm+mt
source-git-commit: 572b856fbdd1ef916f8f897ba86ddefafee324fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 21%

---


# De dynamische media-video, afbeeldingsviewer of dimensionale viewer insluiten op een webpagina {#embedding-the-video-or-image-viewer-on-a-web-page}

Gebruik de functie **[!UICONTROL Embed Code]** wanneer u de video wilt afspelen of een asset wilt bekijken die op een webpagina is ingesloten. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed Code]**.

U sluit alleen URL&#39;s in als u _geen_ AEM als uw WCM gebruikt. Als u AEM als uw WCM gebruikt, voegt [u de elementen rechtstreeks op uw pagina toe.](adding-dynamic-media-assets-to-pages.md)

See [Linking URLs to your Web Application.](linking-urls-to-yourwebapplication.md)

See [Delivering Optimized Images for a Responsive Site.](responsive-site.md)

>[!NOTE]
>
>De insluitcode kan pas worden gekopieerd nadat u het geselecteerde element hebt gepubliceerd. Daarnaast moet u ook de voorinstelling van de viewer of de voorinstelling van de afbeelding publiceren.
>
>Zie Elementen [](publishing-dynamicmedia-assets.md)publiceren.
>
>Zie Voorinstellingen [voor](managing-viewer-presets.md#publishing-viewer-presets)viewers publiceren.
>
>Zie [Voorinstellingen](managing-image-presets.md#publishing-image-presets)afbeelding publiceren.

**Dynamische mediavideo of afbeeldingsviewer insluiten op een webpagina**

1. Navigeer naar de *gepubliceerde* video of het afbeeldingselement waarvan u de insluitcode wilt kopiëren.

   Onthoud dat de insluitcode alleen beschikbaar is om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie Elementen [publiceren.](publishing-dynamicmedia-assets.md)

   Zie Voorinstellingen [voor](managing-viewer-presets.md#publishing-viewer-presets)viewers publiceren.

   Zie [Voorinstellingen](managing-image-presets.md#publishing-image-presets)afbeelding publiceren.

1. Selecteer het vervolgkeuzemenu in het linkerspoor en tik op **[!UICONTROL Viewers]**.
1. Tik in de linkertrack op de naam van een viewervoorinstelling. De viewervoorinstelling wordt toegepast op het element.
1. Tik op **[!UICONTROL Embed]**.
1. Kopieer in het **[!UICONTROL Embed Code]** dialoogvenster de gehele code naar het klembord en tik op **[!UICONTROL Close]**.
1. Plak de insluitcode in uw webpagina&#39;s.

## Het gebruiken van HTTP/2 om uw Dynamische activa van Media te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van dynamische media-elementen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van Inhoud](http2.md) voor volledige details over begonnen worden het gebruiken van HTTP/2 met uw Dynamische rekening van Media.
