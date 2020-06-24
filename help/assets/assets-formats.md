---
title: Ondersteunde bestandsindelingen voor verwerking in [!DNL Adobe Experience Manager Assets].
description: Bestandsindelingen en MIME-typen die worden ondersteund door [!DNL Assets] en [!DNL Dynamic Media] en de functies die worden ondersteund voor elke indeling.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7e9dcebc654e63e171e2baacfe53081f58676f8d
workflow-type: tm+mt
source-wordcount: '1608'
ht-degree: 2%

---


# Ondersteunde indelingen in [!DNL Adobe Experience Manager Assets] {#assets-supported-formats}

[!DNL Experience Manager Assets] ondersteunt een groot aantal bestandsindelingen en elke functie biedt verschillende ondersteuning voor verschillende MIME-typen. Voor integratie [!DNL Assets] met andere DAM-oplossingen (Digital Asset Management) en desktopsoftware, gebruikt u Adobe [!DNL Extensible Metadata Platform] (XMP).

Gebruik de legenda om het steunniveau te begrijpen.

| Ondersteuningsniveau | Beschrijving |
| :-----------: | ------------------------------ |
| ✓ | Ondersteund |
| * | Ondersteund met add-onfuncties |
| − | Niet van toepassing |

## Ondersteunde rasterafbeeldingsindelingen in [!DNL Experience Manager] {#supported-raster-image-formats}

De ondersteunde rasterafbeeldingsindelingen in [!DNL Assets] zijn:

| Format | Opslag | Metagegevensbeheer | Metagegevensextractie | Miniaturen genereren | Bewerken | Metagegevens terugschrijven | Inzichten |
| ------------ | :------: | :-----------------: | :-----------------: | :------------------: | :------: | :----------------: | :------: |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PNM | ✓ | ✓ |  |  |  |  | ✓ |
| PGM | ✓ | ✓ |  |  |  |  | ✓ |
| PBM | ✓ | ✓ |  |  |  |  | ✓ |
| PPM | ✓ | ✓ |  |  |  |  | ✓ |
| PSD ‡ | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| PICT |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

‡ De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die door Adobe Photoshop wordt gegenereerd en die in het PSD-bestand wordt opgenomen. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

De ondersteunde rasterafbeeldingsindelingen in [!DNL Dynamic Media] zijn:

| Format | Uploaden<br> (invoerindeling) | Afbeeldingsvoorinstelling<br> maken<br><br> (uitvoerindeling) | Voorvertoning<br> van dynamische<br> uitvoering | Dynamische<br> uitvoering<br> leveren | Dynamische<br><br> uitvoering downloaden |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PSD ‡ | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |

‡ De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die door Adobe Photoshop wordt gegenereerd en die in het PSD-bestand wordt opgenomen. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

Naast bovenstaande informatie, moet u rekening houden met het volgende:

* De ondersteuning voor EPS-bestanden is alleen van toepassing op rasterafbeeldingen. Miniatuurgeneratie voor EPS-vectorafbeeldingen wordt bijvoorbeeld niet standaard ondersteund. Om steun toe te voegen, [vorm ImageMagick](best-practices-for-imagemagick.md). Om derdehulpmiddelen te integreren om extra mogelijkheden toe te laten, zie de lijn Gebaseerde Behandelaar [van Media van het](media-handlers.md#command-line-based-media-handler)Bevel.

* Metagegevensterugkoppeling werkt voor PSB-bestandsindeling wanneer deze wordt toegevoegd aan de `NComm` handler.

* Zie de bestandsindelingen [!DNL Dynamic Media] [Adobe Illustrator (AI), Postscript (EPS) en PDF voor informatie over het weergeven en genereren van dynamische uitvoeringen voor EPS-bestanden.](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Voor EPS-bestanden wordt terugschrijven van metagegevens ondersteund in PostScript Document Structuring Convention (PS-Adobe) versie 3.0 of hoger.

## Niet-ondersteunde rasterafbeeldingsindelingen in Dynamic Media {#unsupported-image-formats-dynamic-media}

In de volgende lijst worden de subtypen beschreven van bestandsindelingen voor rasterafbeeldingen die *niet* worden ondersteund in Dynamic Media.

Zie ook Niet-ondersteunde bestandsindelingen [detecteren voor Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* PNG-bestanden met een IDAT-segmentgrootte groter dan 100 MB.
* PSB-bestanden.
* PSD-bestanden met een andere kleurruimte dan CMYK, RGB, Grijswaarden of Bitmap worden niet ondersteund. DuoTone-, Lab- en Geïndexeerde kleurruimten worden niet ondersteund.
* PSD-bestanden met een bitdiepte groter dan 16.
* TIFF-bestanden met zwevende-kommagegevens.
* TIFF-bestanden met LAB-kleurruimte.

<!-- Topic commented out for now as of March 31, 2020. The topic may still need adjustment so it can be published live, or it may be moved into a KB article instead. Just waiting on feedback in CQDOC-15657. - Rick
## Unsupported raster image formats in Dynamic Media (#unsupported-image-formats-dynamic-media)

The following table describes the sub-types of raster image formats that are *not* supported in Dynamic Media. The table also describes suggested methods you can use to detect such files.

| Format | What is unsupported? | Suggested detection method |
|---|---|---|
| JPEG  | Files where the initial three bytes is incorrect. | To identify a JPEF file, its initial three bytes must be `ff d8 ff`. If they are anything else, then it is not classified as a JPEG.<br>&bull; There is no software tool that can help with this issue.<br>&bull; A small C++/java program which reads the initial three bytes of a file should be able to detect these types of files.<br>&bull; It may be better to track the source of such files and look at the tool generating the file. |
| PNG |  Files that have an IDAT chunk size greater than 100 MB. | You can detect this issue using [libpng](http://www.libpng.org/pub/png/libpng.html) in C++. |
| PSB |  | Use exiftool if the file type is PSB.<br>Example in an ExifTool log:<br>1. File type: `PSB` |
| PSD | Files with a color space other than CMYK, RGB, Grayscale, or Bitmap are not supported.<br>DuoTone, Lab, and Indexed color spaces are not supported. | Use ExifTool if Color mode is Duotone.<br>Example in an ExifTool log:<br>1. Color mode: `Duotone` |
|  | Files with abrupt endings. | Adobe is unable to detect this condition. Also, such files cannot be opened with Adobe PhotoShop. Adobe suggests you examine the tool that was used to create such a file and troubleshoot at the source. |
|  | Files that have a bit depth greater than 16. | Use ExifTool if the bit depth is greater than 16.<br>Example in an ExifTool log:<br>1. Bit depth: `32` |
|  | File that have Lab color space. | Use exiftool if the color mode is Lab.<br>Example in an ExifTool log:<br>1. Color mode: `Lab` |
| TIFF | Files that have floating point data. That is, a TIFF file with 32-bit depth is not supported. | Use ExifTool if the MIME type is `image/tiff` and the SampleFormat has `Float` in its value. Example in an ExifTool log:<br>1. MIME type: `image/tiff`<br>Sample format: `Float #`<br>2. MIME type: `image/tiff`<br>Sample format: `Float; Float; Float; Float` |
|  | Files that have Lab color space. | Use ExifTool if the color mode is Lab.<br>Example in an ExifTool log:<br>1. Color mode: `Lab` |
-->

## Ondersteunde PDF Rasterizer-bibliotheek {#supported-pdf-rasterizer-library}

De Adobe PDF Rasterizer-bibliotheek genereert miniaturen en voorvertoningen van hoge kwaliteit voor grote bestanden met veel inhoud [!DNL Adobe Illustrator] en PDF-bestanden. Adobe raadt u aan de PDF Rasterizer-bibliotheek te gebruiken voor het volgende:

* Inhoudsintensieve AI/PDF-bestanden die bronintensief zijn voor verwerking.
* AI/PDF-bestanden waarvoor standaard geen miniaturen worden gegenereerd.
* AI-bestanden met Pantone Matching System (PMS)-kleuren.

Zie [Werken met PDF Rasterizer](aem-pdf-rasterizer.md).

## Ondersteunde bibliotheek voor afbeeldingstranscodering {#supported-image-transcoding-library}

De Adobe Imaging Transcoding-bibliotheek is een oplossing voor beeldverwerking die kernfuncties voor het verwerken van afbeeldingen uitvoert, zoals coderen, transcoderen, resampling en vergroten/verkleinen.

De bibliotheek voor grafische transformatie ondersteunt de volgende MIME-typen: JPG/JPEG, PNG (8-bits en 16-bits), GIF, BMP, TIFF/Gecomprimeerde TIFF (behalve 32-bits TIFF-bestanden en PTIFF-bestanden), ICO en ICN.

Zie [Afbeeldingstransformatiebibliotheek](imaging-transcoding-library.md).

## Ondersteunde Camera Raw {#supported-camera-raw}

Met de Adobe Camera Raw-bibliotheek kunnen elementen Raw-afbeeldingen innemen. Zie [Camera Raw-ondersteuning](camera-raw.md).

## Ondersteunde indelingen voor middelendocumenten {#supported-document-formats}

Documentindelingen die worden ondersteund voor functies voor middelenbeheer zijn als volgt:

| Format | Opslag | [Metagegevensbeheer](metadata.md) | Volledige tekst<br> extraheren | [Metagegevensextractie](metadata.md) | Miniaturen<br> genereren | [Extractie van subactiva](managing-linked-subassets.md) | [Metagegevens terugschrijven](xmp-writeback.md) | [Gekoppelde assets](use-assets-across-connected-assets-instances.md) |
|---|---|---|---|---|---|---|---|---|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |  |
| DOC | ✓ | ✓ | ✓ | ✓ |  |  |  | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ |  |  |  | ✓ |
| ODT | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| RTF | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| TXT | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| XLS | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ |  |  |  | ✓ |
| ODS | ✓ | ✓ | ✓ |  |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| ODP | ✓ | ✓ | ✓ |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |  |
| PS | ✓ | ✓ |  |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |  |
| EPUB | ✓ | ✓ |  | ✓ | ✓ |  |  |  |

## Ondersteunde documentindelingen in Dynamic Media {#supported-document-formats-dynamic-media}

| Format | Uploaden<br> (invoerindeling) | Afbeeldingsvoorinstelling<br> maken<br><br> (uitvoerindeling) | Voorvertoning<br> van dynamische<br> uitvoering | Dynamische<br> uitvoering<br> leveren | Dynamische<br><br> uitvoering downloaden |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |

Overweeg het volgende naast de bovenstaande functionaliteit:

* Zie [Adobe Illustrator (AI), Postscript (EPS) en PDF-bestandsindelingen voor informatie over het genereren van dynamische uitvoeringen voor PDF-bestanden.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Zie [Adobe Illustrator (AI), Postscript (EPS) en PDF-bestandsindelingen voor informatie over het gebruik van Dynamic Media voor het weergeven en genereren van dynamische uitvoeringen voor AI-bestanden.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Zie de bestandsindeling [InDesign (INDD) als u Dynamic Media wilt gebruiken om dynamische uitvoeringen voor INDD-bestanden te genereren](../assets/managing-image-presets.md#indesign-indd-file-format).

## Ondersteunde multimedia-indelingen {#supported-multimedia-formats}

|  | Opslag | Metagegevensbeheer | Metagegevensextractie | Miniaturen genereren | MPEG-transcodering |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | − | * |
| MIDI | ✓ | ✓ |  | − | * |
| 3GP | ✓ | ✓ |  | − | * |
| MP3 | ✓ | ✓ | ✓ | − | * |
| MPG | ✓ | ✓ |  | − | * |
| OGA | ✓ | ✓ |  | − | * |
| OGG | ✓ | ✓ |  | − | * |
| RA | ✓ | ✓ |  | − | * |
| WAV | ✓ | ✓ |  | − | * |
| WMA | ✓ | ✓ |  | − | * |
| DVI | ✓ | ✓ |  | * | * |
| FLV | ✓ | ✓ |  | * | * |
| M4V | ✓ | ✓ |  | * | * |
| MPEG | ✓ | ✓ |  | * | * |
| OGV | ✓ | ✓ |  | * | * |
| MOV | ✓ | ✓ |  | * | * |
| WMV | ✓ | ✓ |  | * | * |
| SWF | ✓ | ✓ |  |  |  |

## Ondersteunde indelingen voor invoervideo in Dynamic Media voor transcodering {#supported-input-video-formats-for-dynamic-media-transcoding}

| Videobestandsextensie | Container | Aanbevolen videocodecs | Niet-ondersteunde video-codecs |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (alle profielen) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (vectoranimatiebestanden) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Raw-video, rood | MJPEG 2000 |  |
| RAM, RM | RealVideo | Niet ondersteund | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | Vrije, verliesvrije audiocodec |  |
| MJ2 | Beweging JPEG 2000 | Motion JPEG 2000-codec |  |

## Ondersteunde archiefindelingen {#supported-archive-formats}

De ondersteunde archiefindelingen en de toepasbaarheid van de algemene DAM-workflows worden behandeld in de volgende tabel.

| Indelingen | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Levering Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

## Overige ondersteunde indelingen {#other-supported-formats}

De toepasbaarheid van algemene DAM-workflows voor een aantal andere bestandsindelingen wordt in de onderstaande tabel beschreven. De gebruikelijke DAM-functionaliteit zoals opslag, versioning, ACL, workflow, publiceren en metagegevensbeheer, met uitzondering van levering van Dynamic Media, wordt voor alle bestanden ondersteund.

| Indelingen | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Levering Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript (indien geconfigureerd met eigen leveringsdomein) |  |  |  |  |  | ✓ |

## Ondersteunde MIME-typen {#supported-mime-types}

Experience Manager detecteert het bestandstype standaard met de bestandsextensie. Experience Manager kan dit detecteren op basis van de inhoud van de bestanden. Selecteer voor de laatste optie [!UICONTROL Detect MIME from content] in [!UICONTROL Day CQ DAM Mime Type Service] de Experience Manager-webconsole.

Een lijst van gesteunde types MIME is beschikbaar in CRXDE Lite bij `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Bestandsextensie | MIME-type/internet-mediatype | Standaardwaarde voor jobParam | Toegestane jobParam-waarde |
|---|---|---|---|
| Afbeelding | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | De standaard jobParam is van toepassing op alle MIME-elementen van het afbeeldingstype.<ul><li>[knockoutBackgroundOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>applicatie/eps</li><li>application/x-eps</li><li>afbeelding/eps</li><li>image/x-eps</li></ul> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-pdf-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[PhotoshopOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/web |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Schakel op MIME-type gebaseerde elementen/Scene7 in om taakparameterondersteuning](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support)te uploaden.
>* [Configureer MIME op type gebaseerd voor ondersteuning](config-dynamic.md)voor uploadtaakparameters.

