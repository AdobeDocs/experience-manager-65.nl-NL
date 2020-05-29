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
source-git-commit: 071f4a292343f0ad52ca3700c95bf60f03c307cc
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# De component Video configureren {#configure-the-video-component}

Met de [videocomponent](/help/sites-authoring/default-components-foundation.md#video) kunt u een vooraf gedefinieerd, out-of-the-box (OOTB) video-element op uw pagina plaatsen.

Een beheerder installeert FMPEG afzonderlijk om ervoor te zorgen dat de juiste transcodering plaatsvindt. Zie [Mpeg installeren en AEM](#install-ffmpeg)configureren. Beheerders [configureren ook videoprofielen](#configure-video-profiles) voor gebruik met HTML5-elementen.

## Videoprofielen configureren {#configure-video-profiles}

Definieer videoprofielen voor gebruik van HTML5-elementen. De hier gekozen methoden worden op volgorde gebruikt. U opent de [ontwerpmodus](/help/sites-authoring/default-components-designmode.md) (alleen de klassieke gebruikersinterface) en selecteert het **[!UICONTROL Profiles]** tabblad:

![chlimage_1-317](assets/chlimage_1-317.png)

Vanuit dit dialoogvenster kunt u ook het ontwerp configureren van de component Video en parameters voor [!UICONTROL Playback], [!UICONTROL Flash]en [!UICONTROL Advanced].

## Mpeg installeren en AEM configureren {#install-ffmpeg}

De videocomponent is voor het transcoderen van video&#39;s afhankelijk van de open-source product-MPEG van derden. Gedownload van [https://ffmpeg.org/](https://ffmpeg.org/). Nadat u MPEG hebt geïnstalleerd, configureert u AEM voor het gebruik van een specifieke audiocodec en specifieke runtime-opties.

Voer de volgende stappen uit om Fmpeg in **Windows** te installeren:

1. Download het gecompileerde binaire bestand als `ffmpeg.zip`.
1. Archief met een map opheffen.
1. Stel de omgevingsvariabele van het systeem in `PATH` op &lt;*your-ffmpeg-location*>`\bin`.
1. Start AEM opnieuw.

Voer de volgende stappen uit om Fmpeg te installeren in **Mac OS X**:

1. Installeer Xcode beschikbaar op [developer.apple.com/xcode](hhttps://developer.apple.com/xcode/).
1. Installeer beschikbaar op [XQuartz](https://www.xquartz.org) om [X11](https://support.apple.com/en-us/HT201341)te krijgen.
1. Installeer MacPorts op [www.macports.org](https://www.macports.org/).
1. Voer in de console de `sudo port install ffmpeg` opdracht uit en volg de aanwijzingen op het scherm. Zorg ervoor dat het pad van het `FFmpeg` uitvoerbare bestand wordt toegevoegd aan de `PATH` systeemvariabele.

Voer de volgende stappen uit om Fmpeg te installeren in **Mac OS X 10.6** met behulp van de vooraf gecompileerde versie:

1. Download de vooraf gecompileerde versie.
1. Verwijder het archief naar de `/usr/local` directory.
1. Voer in de console uit `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`. Wijzig de paden naar wens.

Ga als volgt te werk om AEM **te** configureren:

>[!NOTE]
>
>Deze stappen zijn alleen nodig als de codecs verder moeten worden aangepast.

1. Openen [!UICONTROL CRXDE Lite] in uw webbrowser. Ga naar [http://localhost:4502/crx/de](http://localhost:4502/crx/de).
2. Selecteer het `/libs/settings/dam/video/format_aac/jcr:content` knooppunt en controleer of de eigenschappen van het knooppunt als volgt zijn:

   * `audioCodec` is `aac`.
   * `customArgs` is `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8`.

3. Als u de configuratie wilt aanpassen, maakt u een overlay in het `/apps/settings/` knooppunt en verplaatst u dezelfde structuur onder het `/conf/global/settings/` knooppunt. Kan niet worden bewerkt in `/libs` knooppunt. Als u bijvoorbeeld een pad wilt bedekken, maakt u het `/libs/settings/dam/video/fullhd-bp`op `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Bedek en bewerk het gehele profielknooppunt en niet alleen de eigenschap die moet worden gewijzigd. Dergelijke middelen worden niet opgelost via SlingResourceMerger.

4. Als u een van de eigenschappen hebt gewijzigd, klikt u op **[!UICONTROL Save All]**.

>[!NOTE]
>
>Wijzigingen in de standaard out-of-the-box (OTB)-workflowmodellen blijven niet behouden wanneer u een upgrade uitvoert van uw AEM-instantie. Adobe raadt u aan de gewijzigde workflowmodellen te kopiëren voordat u deze bewerkt. Kopieer bijvoorbeeld het OTB- [!UICONTROL DAM Update Asset] model voordat u de stap MPEG Transcoding in het [!UICONTROL DAM Update Asset] model bewerkt, om namen voor videoprofielen te kiezen die vóór de upgrade bestonden. Vervolgens kunt u het `/apps` knooppunt bedekken zodat AEM de aangepaste wijzigingen in het OTB-model kan ophalen.
