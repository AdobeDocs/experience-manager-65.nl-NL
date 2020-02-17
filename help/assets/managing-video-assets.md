---
title: Video-elementen beheren
description: Leer hoe u video-elementen kunt uploaden, voorvertonen, annoteren en publiceren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Video-elementen beheren {#manage-video-assets}

Leer hoe u de video-elementen beheert en bewerkt in Adobe Experience Manager (AEM) Assets. Raadpleeg ook de documentatie bij [](/help/assets/video.md)dynamische media als u een licentie hebt voor het gebruik van Dynamic Media.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

Adobe Experience Manager Assets genereert voorvertoningen voor video-elementen met de extensie MP4. Als de indeling van het element niet MP4 is, installeert u het MPEG-pakket om een voorvertoning te genereren. MPEG maakt video-uitvoeringen van het type OGG en MP4. U kunt een voorvertoning van deze vertoningen weergeven in de gebruikersinterface van AEM Assets.

1. Navigeer in de map Digital Assets of in de submappen naar de locatie waar u digitale elementen wilt toevoegen.
1. Klik of tik op **[!UICONTROL Maken]** op de werkbalk om het element te uploaden en kies **[!UICONTROL Bestanden]**. U kunt het ook rechtstreeks in het gebied met elementen neerzetten. Zie Elementen [](managing-assets-touch-ui.md#uploading-assets) uploaden voor meer informatie over het uploaden.
1. Tik op de knop **[!UICONTROL Afspelen]** op het video-element om een voorvertoning van een video weer te geven in de kaartweergave.

   ![chlimage_1-65](assets/chlimage_1-201.png)

   U kunt video alleen in de kaartweergave pauzeren of afspelen. De knoppen [!UICONTROL Afspelen] en [!UICONTROL Pauzeren] zijn niet beschikbaar in de lijstweergave.

1. Als u een voorvertoning van de video wilt weergeven op de pagina met elementdetails, klikt of tikt u op het pictogram **[!UICONTROL Bewerken]** op de kaart.

   De video wordt afgespeeld in de native videospeler van de browser. U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

   ![chlimage_1-66](assets/chlimage_1-202.png)

## Configuratie voor het uploaden van middelen die groter zijn dan 2 GB {#configuration-to-upload-assets-that-are-larger-than-gb}

Standaard kunt u met de middelen van Experience Manager geen elementen uploaden die groter zijn dan 2 GB vanwege een maximale bestandsgrootte. Nochtans, kunt u deze grens overschrijven door in CRXDE Lite te gaan en een knoop onder de `/apps` folder te creëren. Het knooppunt moet dezelfde knooppuntnaam, directorystructuur en vergelijkbare knooppunteigenschappen van volgorde hebben.

Wijzig naast de configuratie Experience Manager de volgende configuraties voor het uploaden van grote elementen:

* Verhoog de vervaltijd van het token. Zie [!UICONTROL Adobe Granite CSRF Servlet] in de Console van het Web bij `https://[aem_server]:[port]/system/console/configMgr`. Zie [CSRF-bescherming](/help/sites-developing/csrf-protection.md)voor meer informatie.
* Verhoog de `receiveTimeout` configuratie van Dispatcher. Voor meer informatie, zie de configuratie [van de Verzender van de Manager van de](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)Ervaring.

>[!NOTE]
>
>Voor de Klassieke AEM-gebruikersinterface geldt geen beperking voor de bestandsgrootte van 2 GB. Bovendien wordt de end-to-end workflow voor grote video niet volledig ondersteund.

Voer de volgende stappen in de `/apps` map uit om een hogere maximale bestandsgrootte te configureren.

1. Tik in AEM op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Algemeen]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in CRXDE Lite naar `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Tik op het `>>` pictogram om het directoryvenster weer te geven.
1. Tik op de werkbalk op het **[!UICONTROL Overlayknooppunt]**. U kunt ook **[!UICONTROL Overlayknooppunt]** selecteren in het contextmenu.
1. Tik in het dialoogvenster **[!UICONTROL Overlayknooppunt]** op **[!UICONTROL OK]**.

   ![chlimage_1-67](assets/chlimage_1-203.png)

1. Vernieuw de browser. Het bedekkingsknooppunt `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` is geselecteerd.
1. Voer op het tabblad **[!UICONTROL Eigenschappen]** de juiste waarde in bytes in om de maximale grootte tot de gewenste grootte te verhogen. Voer bijvoorbeeld een `{sizeLimit : "32212254720"}` waarde in als u de maximale grootte tot 30 GB wilt verhogen.

1. Tik op de werkbalk op Alles **** opslaan.
1. Tik in AEM op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**.
1. Zoek en tik op de pagina Bundles van de webconsole van Adobe Experience Manager onder de kolom Naam van de tabel **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Stel de seconden voor de velden **[!UICONTROL Standaardtime-out]** en **[!UICONTROL Maximale time-out]** in op `18000` (vijf uur) op de pagina External Process Job Handler van de Adobe Granite-workflow.
1. Tik op **[!UICONTROL Opslaan]**.
1. Tik in AEM op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modellen]**.
1. Selecteer op de pagina Workflowmodellen de optie **[!UICONTROL Dynamic Media Encode Video]** en tik vervolgens op **[!UICONTROL Bewerken]**.
1. Tik op de workflowpagina op de **[!UICONTROL Dynamic Media Video Service-component]** .
1. Vouw [!UICONTROL Geavanceerde instellingen] uit onder het tabblad **[!UICONTROL Algemeen]** in het dialoogvenster Eigenschappen **voor stap**.
1. Geef in het veld **[!UICONTROL Time-out]** een waarde op van `18000`, tik vervolgens op **[!UICONTROL OK]** om terug te keren naar de **[!UICONTROL workflowpagina Video]** coderen van dynamische media.
1. Tik boven aan de pagina onder de titel van de pagina Dynamic Media Encode Video op **[!UICONTROL Opslaan]**.

## Video-elementen publiceren {#publish-video-assets}

Nadat uw video-elementen zijn gepubliceerd, kunt u ze als URL of insluiting op een webpagina opnemen in een webpagina. Zie [publiceren, elementen](/help/assets/publishing-dynamicmedia-assets.md).

## Video-elementen notities aanbrengen {#annotate-video-assets}

1. Klik of tik vanuit de middelenconsole op het pictogram [!UICONTROL Bewerken] op de elementenkaart om de pagina met elementdetails weer te geven.
1. Als u de video wilt afspelen, klikt of tikt u op het pictogram [!UICONTROL Voorvertoning] .
1. Klik op de knop **[!UICONTROL Annoteren]** om de video van een annotatie te voorzien. Er wordt een aantekening toegevoegd op het specifieke tijdpunt (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen.

   ![chlimage_1-68](assets/chlimage_1-204.png)

   Klik op **[!UICONTROL Sluiten om de wizard Annotatie af te sluiten]**.

1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het **tekstveld** en klik op **Springen**. Als u bijvoorbeeld de eerste 10 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.

   ![chlimage_1-69](assets/chlimage_1-205.png)

1. Klik op een annotatie om deze in de tijdlijn weer te geven. Als u de annotatie uit de tijdlijn wilt verwijderen, klikt u op **[!UICONTROL Verwijderen]**.

   ![chlimage_1-70](assets/chlimage_1-206.png)
