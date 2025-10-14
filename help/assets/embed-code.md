---
title: De Dynamic Media Video-, Image Viewer- of Dimensional-viewer insluiten op een webpagina
description: Leer hoe u Dynamic Media-video, -afbeeldingen of -3D-afbeeldingen op een webpagina insluit
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: Viewers
role: User, Admin
exl-id: 203ea349-ef4c-421c-b4b6-76ee9d46ec34
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 20%

---

# De Dynamic Media Video-, Image Viewer- of Dimensional-viewer insluiten op een webpagina {#embedding-the-video-or-image-viewer-on-a-web-page}

Gebruik de functie **[!UICONTROL Embed Code]** wanneer u de video wilt afspelen of een asset wilt bekijken die op een webpagina is ingesloten. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed Code]**.

U bedt URLs slechts als u *niet* gebruikend Adobe Experience Manager als uw WCM bent. Als u Experience Manager als uw WCM gebruikt, [&#x200B; voegt u de activa direct op uw pagina &#x200B;](adding-dynamic-media-assets-to-pages.md) toe.

Zie [&#x200B; Verbinding URLs aan uw Toepassing van het Web &#x200B;](linking-urls-to-yourwebapplication.md).

Zie [&#x200B; geoptimaliseerde beelden voor een ontvankelijke plaats leveren &#x200B;](responsive-site.md).

>[!NOTE]
>
>De insluitcode kan pas worden gekopieerd nadat u het geselecteerde element hebt gepubliceerd. Daarnaast moet u ook de voorinstelling van de viewer of de voorinstelling van de afbeelding publiceren.
>
>Zie [&#x200B; de activa van Publish &#x200B;](publishing-dynamicmedia-assets.md).
>
>Zie [&#x200B; de Kijker van Publish stelt &#x200B;](managing-viewer-presets.md#publishing-viewer-presets) vooraf in.
>
>Zie [&#x200B; het Beeld van Publish vooraf instelt &#x200B;](managing-image-presets.md#publishing-image-presets).

**om de Video van Dynamic Media, de kijker van het Beeld, of de Dimensionele kijker op een Web-pagina in te bedden:**

1. Navigeer aan de *gepubliceerde* video of beeldactiva de waarvan inbedcode u wilt kopiëren.

   Onthoud dat de insluitcode alleen beschikbaar is om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie [&#x200B; de activa van Publish &#x200B;](publishing-dynamicmedia-assets.md).

   Zie [&#x200B; de Kijker van Publish stelt &#x200B;](managing-viewer-presets.md#publishing-viewer-presets) vooraf in.

   Zie [&#x200B; het Beeld van Publish vooraf instelt &#x200B;](managing-image-presets.md#publishing-image-presets).

1. Selecteer in de linkertrack het vervolgkeuzemenu en selecteer **[!UICONTROL Viewers]** .
1. Selecteer in het linkerspoor een naam voor de viewervoorinstelling. De viewervoorinstelling wordt toegepast op het element.
1. Selecteer **[!UICONTROL Embed]** .
1. Kopieer in het dialoogvenster **[!UICONTROL Embed Code]** de gehele code naar het klembord en selecteer vervolgens **[!UICONTROL Close]** .
1. Plak de insluitcode in uw webpagina&#39;s.

## HTTP/2 gebruiken om uw Dynamic Media-middelen te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-middelen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [&#x200B; HTTP2 Levering van Inhoud &#x200B;](http2.md) voor volledige details bij het worden begonnen HTTP/2 met uw rekening van Dynamic Media te gebruiken.
