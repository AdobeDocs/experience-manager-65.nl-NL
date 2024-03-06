---
title: De component Video configureren
description: Leer hoe u de component Video in Adobe Experience Manager kunt gebruiken om een vooraf gedefinieerd, out-of-box video-element op uw pagina te plaatsen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 9c97f99e-d6ef-4817-8b2a-201ab22f2b38
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# De component Video configureren {#configure-the-video-component}

De [Video-component](/help/sites-authoring/default-components-foundation.md#video) Hiermee kunt u een vooraf gedefinieerd, out-of-the-box video-element op uw pagina plaatsen.

Een beheerder installeert FMPEG afzonderlijk om ervoor te zorgen dat de juiste transcodering plaatsvindt. Zie [Mpeg installeren en AEM configureren](#install-ffmpeg). Beheerders [Videoprofielen configureren](#configure-video-profiles) voor gebruik met HTML5-elementen.

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Core Components Embed Component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/embed.html) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

## Videoprofielen configureren {#configure-video-profiles}

Definieer videoprofielen voor gebruik van HTML5-elementen. De hier gekozen methoden worden op volgorde gebruikt. Om toegang te krijgen, gebruik [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) (Alleen klassieke gebruikersinterface) en selecteer de **[!UICONTROL Profiles]** tab:

![chlimage_1-317](assets/chlimage_1-317.png)

Vanuit dit dialoogvenster kunt u ook het ontwerp configureren van de component Video en parameters voor [!UICONTROL Playback], [!UICONTROL Flash], en [!UICONTROL Advanced].

## Mpeg installeren en AEM configureren {#install-ffmpeg}

De videocomponent is voor het transcoderen van video&#39;s afhankelijk van de open-source product-MPEG van derden. Gedownload van [https://ffmpeg.org/](https://ffmpeg.org/). Nadat u MPEG hebt geïnstalleerd, configureert u AEM voor het gebruik van een specifieke audiocodec en specifieke runtime-opties.

Mpeg installeren op **Windows** Voer de volgende stappen uit:

1. Download het gecompileerde binaire bestand als `ffmpeg.zip`.
1. Het archiveren in een map ongedaan maken.
1. De systeemomgevingsvariabele instellen `PATH` tot &lt;*your-ffmpeg-locatie*>`\bin`.
1. Start AEM opnieuw.

Mpeg installeren op **MACOS X** Voer de volgende stappen uit:

1. Xcode installeren die beschikbaar is op [developer.apple.com/xcode](https://developer.apple.com/xcode/).
1. Beschikbaar op [XQuartz](https://www.xquartz.org) om te worden [X11](https://support.apple.com/en-us/100724).
1. MacPorts installeren op [www.macports.org](https://www.macports.org/).
1. Voer in de console uit `sudo port install ffmpeg` en volgt u de aanwijzingen op het scherm. Zorg ervoor dat het pad van de `FFmpeg` uitvoerbaar bestand wordt toegevoegd aan de `PATH` systeemvariabele.

Mpeg installeren op **macOS X 10.6** Voer de volgende stappen uit met behulp van de vooraf gecompileerde versie:

1. Download de vooraf gecompileerde versie.
1. Het bestand ongedaan maken voor de `/usr/local` directory.
1. Voer in de console uit `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`. Wijzig het pad naar wens.

Naar **AEM configureren** Voer de volgende stappen uit:

>[!NOTE]
>
>Deze stappen zijn alleen nodig als de codecs verder moeten worden aangepast.

1. Openen [!UICONTROL CRXDE Lite] in uw webbrowser. Toegang [http://localhost:4502/crx/de](http://localhost:4502/crx/de).
2. Selecteer de `/libs/settings/dam/video/format_aac/jcr:content` en zorg ervoor dat de knoopeigenschappen als volgt zijn:

   * `audioCodec` is `aac`.
   * `customArgs` is `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8`.

3. Als u de configuratie wilt aanpassen, maakt u een bedekking in `/apps/settings/` knooppunt en dezelfde structuur onder `/conf/global/settings/` knooppunt. Kan het bestand niet bewerken in `/libs` knooppunt. Als u bijvoorbeeld een pad wilt bedekken `/libs/settings/dam/video/fullhd-bp`, maakt u deze op `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Bedek en bewerk het gehele profielknooppunt en niet alleen de eigenschap die moet worden gewijzigd. Dergelijke middelen worden niet opgelost via SlingResourceMerger.

4. Als u een van de eigenschappen hebt gewijzigd, klikt u op **[!UICONTROL Save All]**.

>[!NOTE]
>
>Wijzigingen in de standaard out-of-the-box workflowmodellen blijven niet behouden wanneer u een upgrade uitvoert van de AEM. Adobe raadt u aan de gewijzigde workflowmodellen te kopiëren voordat u deze gaat bewerken. Bijvoorbeeld, kopieer uit-van-de-doos [!UICONTROL DAM Update Asset] model voordat u de coderingsstap MPEG in het dialoogvenster [!UICONTROL DAM Update Asset] model voor het selecteren van namen voor videoprofielen die vóór de upgrade bestonden. Vervolgens kunt u de `/apps` knoop om de douaneveranderingen in het uit-van-de-doosmodel AEM terug te winnen.
