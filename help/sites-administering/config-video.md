---
title: De component Video configureren
seo-title: De component Video configureren
description: Leer hoe u de videocomponent configureert.
seo-description: Leer hoe u de videocomponent configureert.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# De component Video configureren {#configure-the-video-component}

Met de [videocomponent](/help/sites-authoring/default-components-foundation.md#video) kunt u een vooraf gedefinieerd, OOTB-video-element (out-of-the-box) op de pagina plaatsen.

Voor juiste transcodering moet uw beheerder Mpeg [installeren en AEM](#install-ffmpeg) afzonderlijk configureren. Ze kunnen ook uw videoprofielen [](#configure-video-profiles) configureren voor gebruik met HTML5-elementen.

## Videoprofielen configureren {#configure-video-profiles}

U kunt videoprofielen definiëren die voor HTML5-elementen moeten worden gebruikt. De hier gekozen methoden worden op volgorde gebruikt. U opent de [ontwerpmodus](/help/sites-authoring/default-components-designmode.md) (alleen de klassieke gebruikersinterface) en selecteert het tabblad **[!UICONTROL Profielen]** :

![chlimage_1-317](assets/chlimage_1-317.png)

U kunt ook het ontwerp configureren van de videocomponenten en -parameters voor [!UICONTROL afspelen], [!UICONTROL Flash]en [!UICONTROL Geavanceerd].

## Mpeg installeren en AEM configureren {#install-ffmpeg}

De videocomponent is afhankelijk van open-source product Forms van derden voor een correcte transcodering van video&#39;s die kunnen worden gedownload van [https://ffmpeg.org/](https://ffmpeg.org/). Nadat u MPEG hebt geïnstalleerd, moet u AEM configureren voor het gebruik van een specifieke audiocodec en specifieke runtime-opties.

**U installeert als volgt Fmpeg voor uw platform**:

* **In Windows:**

   1. Download het gecompileerde binaire bestand als `ffmpeg.zip`
   1. Pak een map uit.
   1. De systeemomgevingsvariabele instellen `PATH` op `<*your-ffmpeg-locatio*n>\bin`
   1. Start AEM opnieuw.

* **In Mac OS X:**

   1. Xcode installeren ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. XQuartz/X11 installeren.
   1. MacPorts installeren ([https://www.macports.org/](https://www.macports.org/))
   1. Voer in de console de volgende opdracht uit en volg de instructies:

      `sudo port install ffmpeg`

      `FFmpeg` moet aanwezig zijn `PATH` zodat AEM het via de opdrachtregel kan ophalen.

* **De vooraf gecompileerde versie voor OS X 10.6 gebruiken:**

   1. Download de vooraf gecompileerde versie.
   1. Extraheer het naar de `/usr/local` map.
   1. Van terminal, voer uit:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**AEM** configureren:

1. Open [!UICONTROL CRXDE Lite] in uw Webbrowser. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Selecteer het `/libs/settings/dam/video/format_aac/jcr:content` knooppunt en controleer of de eigenschappen van het knooppunt als volgt zijn:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Als u de configuratie wilt aanpassen, maakt u een overlay in het `/apps/settings/` knooppunt en verplaatst u dezelfde structuur onder het `/conf/global/settings/` knooppunt. Kan niet worden bewerkt in `/libs` knooppunt. Als u bijvoorbeeld een pad wilt bedekken, maakt u het `/libs/settings/dam/video/fullhd-bp`op `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Bedek en bewerk het gehele profielknooppunt en niet alleen de eigenschap die moet worden gewijzigd. Dergelijke middelen worden niet opgelost via SlingResourceMerger.

1. Als u een van de eigenschappen hebt gewijzigd, klikt u op **[!UICONTROL Alles]** opslaan.

>[!NOTE]
>
>OOTB-workflowmodellen blijven niet behouden wanneer u uw AEM-instantie upgradet. Adobe raadt u aan OTB-workflowmodellen te kopiëren voordat u ze bewerkt. Kopieer bijvoorbeeld het model OOTB [!UICONTROL DAM Update Asset] voordat u de stap FFmpeg Transcoding in het model [!UICONTROL DAM Update Asset] toepast om namen van videoprofielen te kiezen die vóór de upgrade bestonden. Vervolgens kunt u het `/apps` knooppunt bedekken zodat AEM de aangepaste wijzigingen in het OTB-model kan ophalen.

