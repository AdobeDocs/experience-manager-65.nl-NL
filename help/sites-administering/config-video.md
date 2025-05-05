---
title: De component Video configureren
description: Leer hoe u de component Video in Adobe Experience Manager kunt gebruiken om een vooraf gedefinieerd, out-of-box video-element op uw pagina te plaatsen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 9c97f99e-d6ef-4817-8b2a-201ab22f2b38
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# De component Video configureren {#configure-the-video-component}

De [ component van de Video ](/help/sites-authoring/default-components-foundation.md#video) laat u vooraf bepaalde, uit-van-de-doos videoactiva op uw pagina plaatsen.

Een beheerder installeert FMPEG afzonderlijk om ervoor te zorgen dat de juiste transcodering plaatsvindt. Zie [ Mpeg installeren en AEM ](#install-ffmpeg) vormen. De beheerders vormen ook [ Videoprofielen ](#configure-video-profiles) voor gebruik met HTML5 elementen.

>[!CAUTION]
>
>Deze Foundation-component is vervangen. De Adobe adviseert het gebruiken van de [ Componenten van de Kern Embed Component ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/embed.html?lang=nl-NL) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

## Videoprofielen configureren {#configure-video-profiles}

Definieer videoprofielen voor gebruik van HTML5-elementen. De hier gekozen methoden worden op volgorde gebruikt. Om toegang te hebben, gebruik [&#128279;](/help/sites-authoring/default-components-designmode.md) de Wijze van het Ontwerp van 0&rbrace; (Klassieke UI slechts) en selecteer het **[!UICONTROL Profiles]** lusje:

![ chlimage_1-317 ](assets/chlimage_1-317.png)

Vanuit dit dialoogvenster kunt u ook het ontwerp configureren van de component Video en de parameters voor [!UICONTROL Playback] , [!UICONTROL Flash] en [!UICONTROL Advanced] .

## Mpeg installeren en AEM configureren {#install-ffmpeg}

De videocomponent is voor het transcoderen van video&#39;s afhankelijk van de open-source product-MPEG van derden. Gedownload van [ https://ffmpeg.org/ ](https://ffmpeg.org/). Nadat u MPEG hebt geïnstalleerd, configureert u AEM voor het gebruik van een specifieke audiocodec en specifieke runtime-opties.

Om MPEG op **Vensters** te installeren, volg deze stappen:

1. Download het gecompileerde binaire bestand als `ffmpeg.zip` .
1. Het archiveren in een map ongedaan maken.
1. Plaats de variabele van het systeemmilieu `PATH` aan &lt;*uw-mpeg-plaats*> `\bin`.
1. Start AEM opnieuw.

Om MPEG op **macOS X** te installeren, volg deze stappen:

1. Installeer Xcode beschikbaar in [ developer.apple.com/xcode ](https://developer.apple.com/xcode/).
1. Installeer beschikbaar bij [ XQuartz ](https://www.xquartz.org) om [ X11 ](https://support.apple.com/en-us/100724) te krijgen.
1. Installeer MACPorts beschikbaar in [ www.macports.org ](https://www.macports.org/).
1. Voer in de console de opdracht `sudo port install ffmpeg` uit en volg de aanwijzingen op het scherm. Zorg ervoor dat het pad van het uitvoerbare bestand van `FFmpeg` wordt toegevoegd aan de systeemvariabele van `PATH` .

Om MPEG op **macOS X 10.6** te installeren, die de pre-gecompileerde versie gebruikt, volg deze stappen:

1. Download de vooraf gecompileerde versie.
1. Verwijder het archief naar de map `/usr/local` .
1. Voer `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg` uit in de console. Wijzig het pad naar wens.

Om **te vormen AEM**, volg deze stappen:

>[!NOTE]
>
>Deze stappen zijn alleen nodig als de codecs verder moeten worden aangepast.

1. Open [!UICONTROL CRXDE Lite] in uw webbrowser. Toegang [ http://localhost:4502/crx/de ](http://localhost:4502/crx/de).
2. Selecteer het knooppunt `/libs/settings/dam/video/format_aac/jcr:content` en controleer of de eigenschappen van het knooppunt als volgt zijn:

   * `audioCodec` is `aac` .
   * `customArgs` is `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8` .

3. Als u de configuratie wilt aanpassen, maakt u een overlay in het knooppunt `/apps/settings/` en verplaatst u dezelfde structuur onder het knooppunt `/conf/global/settings/` . Kan niet worden bewerkt in knooppunt `/libs` . Als u bijvoorbeeld een pad wilt bedekken `/libs/settings/dam/video/fullhd-bp` , maakt u het pad op `/conf/global/settings/dam/video/fullhd-bp` .

   >[!NOTE]
   >
   >Bedek en bewerk het gehele profielknooppunt en niet alleen de eigenschap die moet worden gewijzigd. Dergelijke middelen worden niet opgelost via SlingResourceMerger.

4. Als u een van de eigenschappen hebt gewijzigd, klikt u op **[!UICONTROL Save All]** .

>[!NOTE]
>
>Wijzigingen in de standaard out-of-the-box workflowmodellen blijven niet behouden wanneer u een upgrade uitvoert van de AEM. Adobe raadt u aan de gewijzigde workflowmodellen te kopiëren voordat u deze gaat bewerken. Kopieer bijvoorbeeld het out-of-box [!UICONTROL DAM Update Asset] model voordat u de stap MPEG Transcoding in het [!UICONTROL DAM Update Asset] -model bewerkt om namen voor videoprofielen te kiezen die vóór de upgrade bestonden. Vervolgens kunt u het knooppunt `/apps` bedekken zodat AEM de aangepaste wijzigingen in het out-of-the-box-model kunt ophalen.
