---
title: De Dynamic Media Video-, Image Viewer- of Dimensional-viewer insluiten op een webpagina
description: Leer hoe u Dynamic Media-video, -afbeeldingen of -3D-afbeeldingen op een webpagina insluit
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
feature: Viewers
role: User, Admin
exl-id: 203ea349-ef4c-421c-b4b6-76ee9d46ec34
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 20%

---

# De Dynamic Media Video-, Image Viewer- of Dimensional-viewer insluiten op een webpagina {#embedding-the-video-or-image-viewer-on-a-web-page}

Gebruik de functie **[!UICONTROL Embed Code]** wanneer u de video wilt afspelen of een asset wilt bekijken die op een webpagina is ingesloten. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed Code]**.

U sluit URLs slechts in als u *niet* gebruikend Adobe Experience Manager als WCM bent. Als u Experience Manager als uw WCM gebruikt, [voegt u de activa direct op uw pagina](adding-dynamic-media-assets-to-pages.md) toe.

Zie [URLs van de verbinding aan uw Toepassing van het Web](linking-urls-to-yourwebapplication.md).

Zie [Geoptimaliseerde afbeeldingen leveren voor een responsieve site](responsive-site.md).

>[!NOTE]
>
>De insluitcode kan pas worden gekopieerd nadat u het geselecteerde element hebt gepubliceerd. Daarnaast moet u ook de voorinstelling van de viewer of de voorinstelling van de afbeelding publiceren.
>
>Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).
>
>Zie [Voorinstellingen van viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).
>
>Zie [Voorinstellingen voor afbeeldingen publiceren](managing-image-presets.md#publishing-image-presets).

**U kunt als volgt de Dynamic Media Video, Image Viewer of DIMM-viewer insluiten op een webpagina:**

1. Navigeer naar de *gepubliceerde* video of afbeeldingselement waarvan u de insluitcode wilt kopi??ren.

   Onthoud dat de insluitcode alleen beschikbaar is om te kopi??ren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

   Zie [Voorinstellingen van viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).

   Zie [Voorinstellingen voor afbeeldingen publiceren](managing-image-presets.md#publishing-image-presets).

1. Selecteer in de linkertrack het vervolgkeuzemenu en selecteer **[!UICONTROL Viewers]**.
1. Selecteer in het linkerspoor een naam voor de viewervoorinstelling. De viewervoorinstelling wordt toegepast op het element.
1. Selecteer **[!UICONTROL Embed]**.
1. Kopieer in het dialoogvenster **[!UICONTROL Embed Code]** de gehele code naar het klembord en selecteer **[!UICONTROL Close]**.
1. Plak de insluitcode in uw webpagina&#39;s.

## HTTP/2 gebruiken om uw Dynamic Media-middelen te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-middelen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van Inhoud](http2.md) voor volledige informatie over het gaan gebruiken van HTTP/2 met uw Dynamic Media-account.
