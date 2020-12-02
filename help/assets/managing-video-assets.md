---
title: Videoassets beheren
description: Upload, voorproef, annoteer, en publiceer videoactiva in  [!DNL Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 8%

---


# Videoassets beheren {#manage-video-assets}

De video-indeling is een essentieel onderdeel van digitale middelen van een organisatie. [!DNL Adobe Experience Manager] biedt geavanceerde aanbiedingen en functies om de volledige levenscyclus van uw video-elementen te beheren nadat deze zijn gemaakt.

Leer hoe u de video-elementen beheert en bewerkt in [!DNL Adobe Experience Manager Assets]. Videocodering en -transcodering, bijvoorbeeld MPEG-transcodering, is mogelijk met [!DNL Dynamic Media]-integratie.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] Hiermee genereert u voorvertoningen voor video-elementen met de extensie MP4. Als de indeling van het element niet MP4 is, installeert u het MPEG-pakket om een voorvertoning te genereren. MPEG maakt video-uitvoeringen van het type OGG en MP4. U kunt een voorvertoning van de uitvoeringen weergeven in de gebruikersinterface [!DNL Assets].

1. Navigeer in de map met digitale elementen of in de submappen naar de locatie waar u digitale elementen wilt toevoegen.
1. Als u het element wilt uploaden, klikt u op **[!UICONTROL Create]** op de werkbalk en kiest u **[!UICONTROL Files]**. U kunt ook een bestand naar de gebruikersinterface slepen. Zie [Elementen uploaden](manage-assets.md#uploading-assets) voor meer informatie.
1. Als u een voorvertoning van een video wilt bekijken in de Kaart-weergave, klikt u op de optie **[!UICONTROL Play]** ![afspeeloptie](assets/do-not-localize/play.png) op het video-element. U kunt video alleen in de kaartweergave pauzeren of afspelen. De opties [!UICONTROL Play] en [!UICONTROL Pause] zijn niet beschikbaar in de lijstweergave.

1. Klik op **[!UICONTROL Edit]** op de kaart om een voorvertoning van de video weer te geven op de pagina met elementdetails. De video wordt afgespeeld in de native videospeler van de browser. U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

   ![Besturingselementen voor het afspelen van video](assets/video-playback-controls.png)

## Configuratie voor het uploaden van middelen die groter zijn dan 2 GB {#configuration-to-upload-assets-that-are-larger-than-gb}

Standaard kunt u met [!DNL Assets] geen elementen uploaden die groter zijn dan 2 GB vanwege een maximale bestandsgrootte. Nochtans, kunt u deze grens overschrijven door in CRXDE Lite te gaan en een knoop onder de `/apps` folder te creëren. Het knooppunt moet dezelfde knooppuntnaam, directorystructuur en vergelijkbare knooppunteigenschappen van volgorde hebben.

Naast [!DNL Assets] configuratie, verander de volgende configuraties om grote activa te uploaden:

* Verhoog de vervaltijd van het token. Zie [!UICONTROL Adobe Granite CSRF Servlet] in Webconsole op `https://[aem_server]:[port]/system/console/configMgr`. Zie [CSRF-beveiliging](/help/sites-developing/csrf-protection.md) voor meer informatie.
* Verhoog de `receiveTimeout` in de configuratie van de Verzender. Voor meer informatie, zie [de configuratie van de Verzender van de Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>De klassieke gebruikersinterface [!DNL Experience Manager] heeft geen beperking voor de bestandsgrootte van 2 GB. Bovendien wordt de end-to-end workflow voor grote video niet volledig ondersteund.

Als u een hogere maximale bestandsgrootte wilt configureren, voert u de volgende stappen uit in de map `/apps`.

1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in CRXDE Lite naar `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Klik op `>>` om het directoryvenster weer te geven.
1. Klik in de werkbalk op **[!UICONTROL Overlay Node]**. U kunt ook **[!UICONTROL Overlay Node]** selecteren in het contextmenu.
1. Klik in het dialoogvenster **[!UICONTROL Overlay Node]** op **[!UICONTROL OK]**.

   ![Overlay-knooppunt](assets/overlay-node-path.png)

1. Vernieuw de browser. Het bedekkingsknooppunt `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` is geselecteerd.
1. Voer op het tabblad **[!UICONTROL Properties]** de juiste waarde in bytes in om de maximale grootte tot de gewenste grootte te verhogen. Als u bijvoorbeeld de formaatlimiet wilt verhogen tot 30 GB, voert u `32212254720` in.

1. Klik **[!UICONTROL Save All]** op de werkbalk.
1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Zoek op de pagina [!DNL Adobe Experience Manager] [!UICONTROL Web Console Bundles] onder de kolom Naam van de tabel **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** en klik op &lt;a2/>.
1. Stel op de pagina [!UICONTROL Adobe Granite Workflow External Process Job Handler] de seconden voor zowel **[!UICONTROL Default Timeout]** als **[!UICONTROL Max Timeout]** velden in op `18000` (vijf uur). Klik op **[!UICONTROL Save]**.
1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer **[!UICONTROL Dynamic Media Encode Video]** op de pagina Workflowmodellen en klik vervolgens op **[!UICONTROL Edit]**.
1. Dubbelklik op de component **[!UICONTROL Dynamic Media Video Service Process]** op de werkstroompagina.
1. Vouw in het dialoogvenster [!UICONTROL Step Properties] onder het tabblad **[!UICONTROL Common]** **Geavanceerde instellingen** uit.
1. Geef in het veld **[!UICONTROL Timeout]** een waarde `18000` op en klik vervolgens op **[!UICONTROL OK]** om terug te keren naar de **[!UICONTROL Dynamic Media Encode Video]**-werkstroompagina.
1. Klik onder de paginatitel [!UICONTROL Dynamic Media Encode Video] boven aan de pagina op **[!UICONTROL Save]**.

## Video-elementen publiceren {#publish-video-assets}

Na publicatie kunt u de video-elementen in een webpagina opnemen als een URL of de elementen rechtstreeks insluiten. Zie [Dynamische media-elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor meer informatie.

## Video-elementen {#annotate-video-assets} notities aanbrengen

1. Selecteer **[!UICONTROL Edit]** op de elementenkaart in de [!DNL Assets]-console om de pagina met elementdetails weer te geven.
1. Klik op **[!UICONTROL Preview]** om de video af te spelen.
1. Klik op **[!UICONTROL Annotate]** om de video een annotatie te geven. Er wordt een aantekening toegevoegd op het specifieke tijdstip (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen. Klik op **[!UICONTROL Close]** om de wizard Annotatie af te sluiten.

   ![Tekenen en notities aanbrengen in een videoframe](assets/annotate-video.png)

1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 20 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.

   ![Hiermee wordt naar een tijd in een video gezocht om met opgegeven seconden over te slaan](assets/seek-in-video.png)

1. Klik op een annotatie om deze in de tijdlijn weer te geven. Als u de annotatie uit de tijdlijn wilt verwijderen, klikt u op **[!UICONTROL Delete]**.

   ![Annotaties en de details in de tijdlijn weergeven](assets/timeline-view-annotation.png)

>[!MORELIKETHIS]
>
>* [Digitale middelen beheren in Experience Manager Assets](/help/assets/manage-assets.md)
>* [Verzamelingen beheren in Experience Managers](/help/assets/manage-collections.md)
>* [Dynamische mediavideodocumentatie](/help/assets/video.md).

