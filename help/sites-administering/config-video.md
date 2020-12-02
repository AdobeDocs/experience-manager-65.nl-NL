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
source-git-commit: 535a175486a2d0f31762d71954c4fead2ef246e1
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---


# De videocomponent {#configure-the-video-component} configureren

Met de [Video-component](/help/sites-authoring/default-components-foundation.md#video) kunt u een vooraf gedefinieerd, out-of-the-box (OTB)-video-element op uw pagina plaatsen.

Een beheerder installeert FMPEG afzonderlijk om ervoor te zorgen dat de juiste transcodering plaatsvindt. Zie [Mpeg installeren en AEM configureren](#install-ffmpeg). Beheerders kunnen ook [Videoprofielen configureren](#configure-video-profiles) voor gebruik met HTML5-elementen.

## Videoprofielen {#configure-video-profiles} configureren

Definieer videoprofielen voor gebruik van HTML5-elementen. De hier gekozen methoden worden op volgorde gebruikt. Als u toegang wilt krijgen, gebruikt u [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) (alleen klassieke gebruikersinterface) en selecteert u het tabblad **[!UICONTROL Profiles]**:

![chlimage_1-317](assets/chlimage_1-317.png)

Vanuit dit dialoogvenster kunt u ook het ontwerp configureren van de component Video en de parameters voor [!UICONTROL Playback], [!UICONTROL Flash] en [!UICONTROL Advanced].

## Mpeg installeren en AEM {#install-ffmpeg} configureren

De videocomponent is voor het transcoderen van video&#39;s afhankelijk van de open-source product-MPEG van derden. Gedownload van [https://ffmpeg.org/](https://ffmpeg.org/). Nadat u MPEG hebt geïnstalleerd, configureert u AEM om een specifieke audiocodec en specifieke runtime-opties te gebruiken.

Voer de volgende stappen uit om Mpeg te installeren op **Windows**:

1. Download het gecompileerde binaire bestand als `ffmpeg.zip`.
1. Archief met een map opheffen.
1. Stel de systeemomgevingsvariabele `PATH` in op &lt;*your-ffmpeg-location*`\bin`.
1. Start AEM opnieuw.

Voer de volgende stappen uit om Mpeg te installeren op **Mac OS X**:

1. Installeer Xcode beschikbaar op [developer.apple.com/xcode](https://developer.apple.com/xcode/).
1. Installeer beschikbaar bij [XQuartz](https://www.xquartz.org) om [X11](https://support.apple.com/en-us/HT201341) te krijgen.
1. Installeer MacPorts beschikbaar op [www.macports.org](https://www.macports.org/).
1. Voer in de console de opdracht `sudo port install ffmpeg` uit en volg de aanwijzingen op het scherm. Zorg ervoor dat het pad van het uitvoerbare bestand `FFmpeg` wordt toegevoegd aan de systeemvariabele `PATH`.

Voer de volgende stappen uit om Mpeg te installeren op **Mac OS X 10.6** met behulp van de vooraf gecompileerde versie:

1. Download de vooraf gecompileerde versie.
1. Verwijder het archief naar de map `/usr/local`.
1. In de console, voer `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg` uit. Wijzig de paden naar wens.

Ga als volgt te werk om AEM **te configureren:**

>[!NOTE]
>
>Deze stappen zijn alleen nodig als de codecs verder moeten worden aangepast.

1. Open [!UICONTROL CRXDE Lite] in uw webbrowser. Toegang [http://localhost:4502/crx/de](http://localhost:4502/crx/de).
2. Selecteer de `/libs/settings/dam/video/format_aac/jcr:content` knoop en zorg ervoor dat de knoopeigenschappen als volgt zijn:

   * `audioCodec` is  `aac`.
   * `customArgs` is  `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8`.

3. Als u de configuratie wilt aanpassen, maakt u een overlay in `/apps/settings/`-knooppunt en verplaatst u dezelfde structuur onder `/conf/global/settings/`-knooppunt. Het kan niet in `/libs` knoop worden uitgegeven. Als u bijvoorbeeld een pad `/libs/settings/dam/video/fullhd-bp` wilt bedekken, maakt u het op `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Bedek en bewerk het gehele profielknooppunt en niet alleen de eigenschap die moet worden gewijzigd. Dergelijke middelen worden niet opgelost via SlingResourceMerger.

4. Als u een van de eigenschappen hebt gewijzigd, klikt u op **[!UICONTROL Save All.]**

>[!NOTE]
>
>Wijzigingen in de standaard out-of-the-box (OOTB)-workflowmodellen blijven niet behouden wanneer u een upgrade uitvoert van de AEM. Adobe raadt u aan de gewijzigde workflowmodellen te kopiëren voordat u deze gaat bewerken. Kopieer bijvoorbeeld het OOTB [!UICONTROL DAM Update Asset]-model voordat u de stap MPEG Transcoding in het [!UICONTROL DAM Update Asset]-model bewerkt om namen voor videoprofielen te kiezen die vóór de upgrade bestonden. Vervolgens kunt u het knooppunt `/apps` bedekken om AEM de aangepaste wijzigingen in het OOTB-model op te halen.
