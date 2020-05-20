---
title: Videoassets beheren
description: Leer hoe u video-elementen kunt uploaden, voorvertonen, annoteren en publiceren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 10%

---


# Videoassets beheren {#manage-video-assets}

Leer hoe u de video-elementen beheert en bewerkt in Adobe Experience Manager (AEM) Assets. Raadpleeg ook de documentatie bij [](/help/assets/video.md)dynamische media als u een licentie hebt voor het gebruik van Dynamic Media.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

Adobe Experience Manager Assets genereert voorvertoningen voor video-elementen met de extensie MP4. Als de indeling van het element niet MP4 is, installeert u het MPEG-pakket om een voorvertoning te genereren. MPEG maakt video-uitvoeringen van het type OGG en MP4. U kunt een voorvertoning van deze vertoningen weergeven in de gebruikersinterface van AEM Assets.

1. Navigeer in de map Digital Assets of in de submappen naar de locatie waar u digitale elementen wilt toevoegen.
1. Als u het element wilt uploaden, klikt u op **[!UICONTROL Create]** de werkbalk en kiest u **[!UICONTROL Files]**. U kunt het ook rechtstreeks in het gebied met elementen neerzetten. Zie Elementen [](managing-assets-touch-ui.md#uploading-assets) uploaden voor meer informatie over het uploaden.
1. Als u een video wilt voorvertonen in de kaartweergave, klikt u op de **[!UICONTROL Play]** knop in het video-element.

   ![chlimage_1-65](assets/chlimage_1-201.png)

   U kunt video alleen in de kaartweergave pauzeren of afspelen. De knoppen [!UICONTROL Play] en [!UICONTROL Pause] zijn niet beschikbaar in de lijstweergave.

1. Als u een voorvertoning van de video wilt weergeven op de pagina met elementdetails, klikt u op het **[!UICONTROL Edit]** pictogram op de kaart.

   De video wordt afgespeeld in de native videospeler van de browser. U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

   ![chlimage_1-66](assets/chlimage_1-202.png)

## Configuratie voor het uploaden van middelen die groter zijn dan 2 GB {#configuration-to-upload-assets-that-are-larger-than-gb}

Standaard kunt u met de middelen van Experience Manager geen elementen uploaden die groter zijn dan 2 GB vanwege een maximale bestandsgrootte. Nochtans, kunt u deze grens overschrijven door in CRXDE Lite te gaan en een knoop onder de `/apps` folder te creëren. Het knooppunt moet dezelfde knooppuntnaam, directorystructuur en vergelijkbare knooppunteigenschappen van volgorde hebben.

Wijzig naast de configuratie Experience Manager de volgende configuraties voor het uploaden van grote elementen:

* Verhoog de vervaltijd van het token. Zie [!UICONTROL Adobe Granite CSRF Servlet] in webconsole op `https://[aem_server]:[port]/system/console/configMgr`. Zie [CSRF-bescherming](/help/sites-developing/csrf-protection.md)voor meer informatie.
* Verhoog de `receiveTimeout` configuratie van Dispatcher. Voor meer informatie, zie de configuratie [van de Verzender van de Manager van de](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)Ervaring.

>[!NOTE]
>
>Voor de Klassieke AEM-gebruikersinterface geldt geen beperking voor de bestandsgrootte van 2 GB. Bovendien wordt de end-to-end workflow voor grote video niet volledig ondersteund.

Voer de volgende stappen in de `/apps` map uit om een hogere maximale bestandsgrootte te configureren.

1. Klik in AEM op **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in CRXDE Lite naar `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Tik op het `>>` pictogram om het directoryvenster weer te geven.
1. From the toolbar, click the **[!UICONTROL Overlay Node]**. U kunt ook **[!UICONTROL Overlay Node]** selecteren in het contextmenu.
1. In the **[!UICONTROL Overlay Node]** dialog, click **[!UICONTROL OK]**.

   ![chlimage_1-67](assets/chlimage_1-203.png)

1. Vernieuw de browser. Het bedekkingsknooppunt `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` is geselecteerd.
1. Voer op het **[!UICONTROL Properties]** tabblad de juiste waarde in bytes in om de maximale grootte tot de gewenste grootte te verhogen. Voer bijvoorbeeld een `{sizeLimit : "32212254720"}` waarde in als u de maximale grootte tot 30 GB wilt verhogen.

1. From the toolbar, touch **[!UICONTROL Save All]**.
1. Klik in AEM op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Zoek en klik op de pagina Bundles van de webconsole van Adobe Experience Manager onder de kolom Naam van de tabel **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Stel de seconden voor de velden **[!UICONTROL Default Timeout]** en **[!UICONTROL Max Timeout]** in op `18000` (vijf uur) op de pagina Handler van externe procestaken van Adobe Granite Workflow.
1. Klik op **[!UICONTROL Save]**.
1. Klik in AEM op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina Workflowmodellen de optie **[!UICONTROL Dynamic Media Encode Video]** en klik op **[!UICONTROL Edit]**.
1. Dubbelklik op de werkstroompagina op de **[!UICONTROL Dynamic Media Video Service Process]** component.
1. Vouw in het dialoogvenster [!UICONTROL Step Properties] onder het tabblad **[!UICONTROL Common]** **Geavanceerde instellingen** uit.
1. In the **[!UICONTROL Timeout]** field, specify a value of `18000`, then click **[!UICONTROL OK]** to return to the **[!UICONTROL Dynamic Media Encode Video]** workflow page.
1. Klik onder de titel van de pagina Video coderen van dynamische media boven aan de pagina **[!UICONTROL Save]**.

## Video-elementen publiceren {#publish-video-assets}

Nadat uw video-elementen zijn gepubliceerd, kunt u ze als URL of insluiting op een webpagina opnemen in een webpagina. Zie [publiceren, elementen](/help/assets/publishing-dynamicmedia-assets.md).

## Video-elementen notities aanbrengen {#annotate-video-assets}

1. Klik in de middelenconsole op het [!UICONTROL Edit] pictogram op de elementenkaart om de pagina met elementdetails weer te geven.
1. Klik op het [!UICONTROL Preview] pictogram om de video af te spelen.
1. Klik op de **[!UICONTROL Annotate]** knop om de video een annotatie te geven. Er wordt een aantekening toegevoegd op het specifieke tijdpunt (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen.

   ![chlimage_1-68](assets/chlimage_1-204.png)

   Klik op de knop **[!UICONTROL Close]** om de wizard Annotatie af te sluiten.

1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 10 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.

   ![chlimage_1-69](assets/chlimage_1-205.png)

1. Klik op een annotatie om deze in de tijdlijn weer te geven. Klik op de knop **[!UICONTROL Delete]**.

   ![chlimage_1-70](assets/chlimage_1-206.png)
