---
title: Videoassets beheren
description: Video-elementen uploaden, voorvertonen, notities aanbrengen en publiceren in [!DNL Adobe Experience Manager].
contentOwner: AG
role: User
feature: Asset Management
exl-id: 21d3e0bd-5955-470a-8ca2-4d995c17eb4c
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 8%

---

# Videoassets beheren {#manage-video-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-video-assets.html?lang=en) |
| AEM 6,5 | Dit artikel |
| AEM 6,4 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-64/assets/managing/managing-video-assets.html?lang=en) |

De video-indeling is een essentieel onderdeel van digitale middelen van een organisatie. [!DNL Adobe Experience Manager] biedt geavanceerde aanbiedingen en functies om de volledige levenscyclus van uw video-elementen te beheren nadat deze zijn gemaakt.

Leer hoe u de video-elementen beheert en bewerkt in [!DNL Adobe Experience Manager Assets]. Videocodering en -transcodering, bijvoorbeeld MPEG-transcodering, is mogelijk met [!DNL Dynamic Media] integratie.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] Hiermee genereert u voorvertoningen voor video-elementen met de extensie MP4. Als de indeling van het element niet MP4 is, installeert u het MPEG-pakket om een voorvertoning te genereren. MPEG maakt video-uitvoeringen van het type OGG en MP4. U kunt een voorvertoning van de vertoningen weergeven in het dialoogvenster [!DNL Assets] gebruikersinterface.

1. Navigeer in de map met digitale elementen of in de submappen naar de locatie waar u digitale elementen wilt toevoegen.
1. Als u het element wilt uploaden, klikt u op **[!UICONTROL Create]** op de werkbalk en kiest u **[!UICONTROL Files]**. U kunt ook een bestand naar de gebruikersinterface slepen. Zie [elementen uploaden](manage-assets.md#uploading-assets) voor meer informatie.
1. Als u een voorvertoning van een video wilt weergeven in de kaartweergave, klikt u op de knop **[!UICONTROL Play]** ![afspeeloptie](assets/do-not-localize/play.png) op het video-element. U kunt video alleen in de kaartweergave pauzeren of afspelen. De [!UICONTROL Play] en [!UICONTROL Pause] zijn niet beschikbaar in de lijstweergave.

1. Klik op **[!UICONTROL Edit]** op de kaart. De video wordt afgespeeld in de native videospeler van de browser. U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

   ![Besturingselementen voor het afspelen van video](assets/video-playback-controls.png)

## Configuratie voor het uploaden van middelen die groter zijn dan 2 GB {#configuration-to-upload-assets-that-are-larger-than-gb}

Standaard, [!DNL Assets] Hiermee kunt u geen elementen uploaden die groter zijn dan 2 GB vanwege een maximale bestandsgrootte. Nochtans, kunt u deze grens overschrijven door in CRXDE Lite te gaan en een knoop onder te creëren `/apps` directory. Het knooppunt moet dezelfde knooppuntnaam, directorystructuur en vergelijkbare knooppunteigenschappen van volgorde hebben.

Naast [!DNL Assets] configuratie, verander de volgende configuraties om grote activa te uploaden:

* Verhoog de vervaltijd van het token. Zie [!UICONTROL Adobe Granite CSRF Servlet] in webconsole op `https://[aem_server]:[port]/system/console/configMgr`. Zie voor meer informatie [CSRF-bescherming](/help/sites-developing/csrf-protection.md).
* De `receiveTimeout` in Dispatcher-configuratie. Zie voor meer informatie [Configuratie van Experience Manager Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>De [!DNL Experience Manager] Voor de klassieke gebruikersinterface geldt geen beperking voor de bestandsgrootte van 2 GB. Bovendien wordt de end-to-end workflow voor grote video niet volledig ondersteund.

Voer de volgende stappen uit in het dialoogvenster `/apps` directory.

1. In [!DNL Experience Manager], klikt u op **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in CRXDE Lite naar `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Klik op de knop `>>`.
1. Klik in de werkbalk op de knop **[!UICONTROL Overlay Node]**. U kunt ook **[!UICONTROL Overlay Node]** selecteren in het contextmenu.
1. In de **[!UICONTROL Overlay Node]** dialoogvenster, klikt u op **[!UICONTROL OK]**.

   ![Overlay-knooppunt](assets/overlay-node-path.png)

1. Vernieuw de browser. Het overlayknooppunt `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` is geselecteerd.
1. In de **[!UICONTROL Properties]** voert u de gewenste waarde in bytes in om de maximale grootte tot de gewenste grootte te verhogen. Als u bijvoorbeeld de maximale grootte wilt verhogen tot 30 GB, voert u `32212254720` waarde.

1. Klik **[!UICONTROL Save All]** op de werkbalk.
1. In [!DNL Experience Manager], klikt u op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Op de [!DNL Adobe Experience Manager] [!UICONTROL Web Console Bundles] pagina, onder de kolom Naam van de lijst, bepaal de plaats, en klik **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Op de [!UICONTROL Adobe Granite Workflow External Process Job Handler] pagina, stel de seconden voor beide in **[!UICONTROL Default Timeout]** en **[!UICONTROL Max Timeout]** velden naar `18000` (vijf uur). Klik op **[!UICONTROL Save]**.
1. In [!DNL Experience Manager], klikt u op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina Workflowmodellen **[!UICONTROL Dynamic Media Encode Video]** en klik vervolgens op **[!UICONTROL Edit]**.
1. Dubbelklik op de pagina met workflows op de knop **[!UICONTROL Dynamic Media Video Service Process]** component.
1. Vouw in het dialoogvenster [!UICONTROL Step Properties] onder het tabblad **[!UICONTROL Common]** **Geavanceerde instellingen** uit.
1. In de **[!UICONTROL Timeout]** veld, geef een waarde op van `18000`en klik vervolgens op **[!UICONTROL OK]** om terug te keren naar de **[!UICONTROL Dynamic Media Encode Video]** workflowpagina.
1. Boven aan de pagina, onder de [!UICONTROL Dynamic Media Encode Video] paginatitel, klik **[!UICONTROL Save]**.

## Video-elementen publiceren {#publish-video-assets}

Na publicatie kunt u de video-elementen in een webpagina opnemen als een URL of de elementen rechtstreeks insluiten. Zie voor meer informatie [Dynamic Media-middelen publiceren](/help/assets/publishing-dynamicmedia-assets.md).

## Video-elementen notities aanbrengen {#annotate-video-assets}

1. Van de [!DNL Assets] console, selecteren **[!UICONTROL Edit]** op de elementenkaart om de pagina met elementdetails weer te geven.
1. Als u de video wilt afspelen, klikt u op **[!UICONTROL Preview]**.
1. Klik op **[!UICONTROL Annotate]**. Er wordt een aantekening toegevoegd op het specifieke tijdstip (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen. Als u de wizard Annotatie wilt afsluiten, klikt u op **[!UICONTROL Close]**.

   ![Tekenen en notities aanbrengen in een videoframe](assets/annotate-video.png)

1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 20 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.

   ![Hiermee wordt naar een tijd in een video gezocht om met opgegeven seconden over te slaan](assets/seek-in-video.png)

1. Klik op een annotatie om deze in de tijdlijn weer te geven. Als u de annotatie uit de tijdlijn wilt verwijderen, klikt u op **[!UICONTROL Delete]**.

   ![Annotaties en de details in de tijdlijn weergeven](assets/timeline-view-annotation.png)

>[!MORELIKETHIS]
>
>* [Digitale middelen beheren in Experience Manager Assets](/help/assets/manage-assets.md)
>* [Verzamelingen beheren in Experience Manager Assets](/help/assets/manage-collections.md)
>* [Dynamic Media-videodocumentatie](/help/assets/video.md).

