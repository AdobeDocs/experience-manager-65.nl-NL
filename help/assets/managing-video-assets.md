---
title: Video-elementen beheren in [!DNL Adobe Experience Manager].
description: U kunt video-elementen uploaden, voorvertonen, notities aanbrengen en publiceren in [!DNL-Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: a61e1e9ffb132b59c725b2078f09641a3c2a479a
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 7%

---


# Videoassets beheren {#manage-video-assets}

De video-indeling is een essentieel onderdeel van digitale middelen van een organisatie. [!DNL Adobe Experience Manager] biedt geavanceerde aanbiedingen en functies om de volledige levenscyclus van uw video-elementen te beheren nadat deze zijn gemaakt.

Leer hoe u de video-elementen in beheert en bewerkt [!DNL Adobe Experience Manager Assets]. Raadpleeg ook de documentatie bij [!DNL Dynamic Media]video over [](/help/assets/video.md)Dynamic Media als u een gebruikslicentie hebt.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] Hiermee genereert u voorvertoningen voor video-elementen met de extensie MP4. Als de indeling van het element niet MP4 is, installeert u het MPEG-pakket om een voorvertoning te genereren. MPEG maakt video-uitvoeringen van het type OGG en MP4. U kunt een voorvertoning van de uitvoeringen weergeven in de gebruikersinterface Elementen.

1. Navigeer in de map Digital Assets of in de submappen naar de locatie waar u digitale elementen wilt toevoegen.
1. Als u het element wilt uploaden, klikt u op **[!UICONTROL Create]** de werkbalk en kiest u **[!UICONTROL Files]**. U kunt het ook rechtstreeks in het gebied met elementen neerzetten. Zie Elementen [](managing-assets-touch-ui.md#uploading-assets) uploaden voor meer informatie over het uploaden.
1. Als u een video wilt voorvertonen in de kaartweergave, klikt u op de **[!UICONTROL Play]** knop in het video-element.

   ![chlimage_1-65](assets/chlimage_1-201.png)

   U kunt video alleen in de kaartweergave pauzeren of afspelen. De knoppen [!UICONTROL Play] en [!UICONTROL Pause] zijn niet beschikbaar in de lijstweergave.

1. Klik op de kaart om een voorvertoning van de video weer te geven op de pagina met elementdetails. **[!UICONTROL Edit]**

   De video wordt afgespeeld in de native videospeler van de browser. U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

   ![chlimage_1-66](assets/chlimage_1-202.png)

## Configuratie voor het uploaden van middelen die groter zijn dan 2 GB {#configuration-to-upload-assets-that-are-larger-than-gb}

Standaard kunt u [!DNL Assets] geen elementen uploaden die groter zijn dan 2 GB vanwege een maximale bestandsgrootte. Nochtans, kunt u deze grens overschrijven door in CRXDE Lite te gaan en een knoop onder de `/apps` folder te creëren. Het knooppunt moet dezelfde knooppuntnaam, directorystructuur en vergelijkbare knooppunteigenschappen van volgorde hebben.

Wijzig naast de [!DNL Assets] configuratie de volgende configuraties om grote elementen te uploaden:

* Verhoog de vervaltijd van het token. Zie [!UICONTROL Adobe Granite CSRF Servlet] in webconsole op `https://[aem_server]:[port]/system/console/configMgr`. Zie [CSRF-bescherming](/help/sites-developing/csrf-protection.md)voor meer informatie.
* Verhoog de `receiveTimeout` Dispatcher-configuratie. Zie de configuratie [van](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)Experience Manager Dispatcher voor meer informatie.

>[!NOTE]
>
>De [!DNL Experience Manager] klassieke gebruikersinterface heeft geen beperking voor de bestandsgrootte van 2 GB. Bovendien wordt de end-to-end workflow voor grote video niet volledig ondersteund.

Voer de volgende stappen in de `/apps` map uit om een hogere maximale bestandsgrootte te configureren.

1. Klik [!DNL Experience Manager]in **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in CRXDE Lite naar `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Klik op het venster `>>`om het directoryvenster weer te geven.
1. From the toolbar, click the **[!UICONTROL Overlay Node]**. U kunt ook **[!UICONTROL Overlay Node]** selecteren in het contextmenu.
1. In the **[!UICONTROL Overlay Node]** dialog, click **[!UICONTROL OK]**.

   ![Overlay-knooppunt](assets/overlay-node-path.png)

1. Vernieuw de browser. Het bedekkingsknooppunt `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` is geselecteerd.
1. Voer op het **[!UICONTROL Properties]** tabblad de juiste waarde in bytes in om de maximale grootte tot de gewenste grootte te verhogen. Voer bijvoorbeeld een `{sizeLimit : "32212254720"}` waarde in als u de maximale grootte tot 30 GB wilt verhogen.

1. Klik **[!UICONTROL Save All]** op de werkbalk.
1. Klik [!DNL Experience Manager]in **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Zoek op de [!DNL Adobe Experience Manager] pagina, onder de kolom Naam van de tabel, de gewenste locatie en klik op [!UICONTROL Web Console Bundles] **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Stel op de [!UICONTROL Adobe Granite Workflow External Process Job Handler] pagina de seconden voor zowel **[!UICONTROL Default Timeout]** als **[!UICONTROL Max Timeout]** velden in op `18000` (vijf uur). Klik op **[!UICONTROL Save]**.
1. Klik [!DNL Experience Manager]in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina Workflowmodellen de optie **[!UICONTROL Dynamic Media Encode Video]** en klik op **[!UICONTROL Edit]**.
1. Dubbelklik op de werkstroompagina op de **[!UICONTROL Dynamic Media Video Service Process]** component.
1. Vouw in het dialoogvenster [!UICONTROL Step Properties] onder het tabblad **[!UICONTROL Common]** **Geavanceerde instellingen** uit.
1. In the **[!UICONTROL Timeout]** field, specify a value of `18000`, then click **[!UICONTROL OK]** to return to the **[!UICONTROL Dynamic Media Encode Video]** workflow page.
1. Klik onder de titel van de [!UICONTROL Dynamic Media Encode Video] pagina boven aan de pagina **[!UICONTROL Save]**.

## Video-elementen publiceren {#publish-video-assets}

Na publicatie kunt u de video-elementen in een webpagina opnemen als een URL of de elementen rechtstreeks insluiten. Zie Dynamische media-elementen [](/help/assets/publishing-dynamicmedia-assets.md)publiceren voor meer informatie.

## Video-elementen notities aanbrengen {#annotate-video-assets}

1. Klik in de middelenconsole op [!UICONTROL Edit] de elementenkaart om de pagina met elementdetails weer te geven.
1. Klik op [!UICONTROL Preview]om de video af te spelen.
1. Klik op de **[!UICONTROL Annotate]** knop om de video een annotatie te geven. Er wordt een aantekening toegevoegd op het specifieke tijdstip (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen.

   ![Tekenen en notities aanbrengen in een videoframe](assets/annotate-video.png)

   Klik op de knop **[!UICONTROL Close]** om de wizard Annotatie af te sluiten.

1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 10 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.

   ![Hiermee wordt naar een tijd in een video gezocht om met opgegeven seconden over te slaan](assets/seek-in-video.png)

1. Klik op een annotatie om deze in de tijdlijn weer te geven. Klik op de knop **[!UICONTROL Delete]**.

   ![Annotaties en de details in de tijdlijn weergeven](assets/timeline-view-annotation.png)

>[!MORELIKETHIS]
>
>* [Digitale middelen beheren in Experience Manager Assets](/help/assets/managing-assets-touch-ui.md)
>* [Verzamelingen beheren in Experience Manager-middelen](/help/assets/managing-collections-touch-ui.md)

