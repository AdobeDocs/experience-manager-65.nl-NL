---
title: Ondersteunde indelingen voor middelen
description: Lijst met bestandsindelingen die worden ondersteund door AEM Assets en door Dynamic Media, en functies die worden ondersteund voor elke indeling.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 593c1e1954a1c8e0355ede9889caed05ff72f3f9

---


# Ondersteunde middelenindelingen {#assets-supported-formats}

AEM Assets ondersteunt een groot aantal bestandsindelingen en elke functionaliteit biedt verschillende ondersteuning voor verschillende MIME-typen.

Gebruik het Extensible Metadata Platform (XMP) van Adobe om AEM-middelen te integreren met andere DAM-oplossingen (Digital Asset Management) en bureaubladsoftware die voldoen aan de standaarden.

Gebruik de legenda om het steunniveau te begrijpen.

| Ondersteuningsniveau | Beschrijving |
|:---:|---|
| ✓ | Ondersteund |
| * | Ondersteund met add-onfuncties |
| − | Niet van toepassing |

## Ondersteunde rasterafbeeldingsindelingen in AEM-elementen {#supported-raster-image-formats}

| Format | Opslag | Metagegevensbeheer | Metagegevensextractie | Miniaturen genereren | Interactief bewerken | Metagegevens terugschrijven | Inzichten |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
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

## Ondersteunde rasterafbeeldingsindelingen in Dynamic Media (#supported-raster-image-formats-dynamic-media)

| Format | Uploaden<br> (invoerindeling) | Afbeeldingsvoorinstelling<br> maken<br><br> (uitvoerindeling) | Voorvertoning<br> van dynamische<br> uitvoering | Dynamische<br> uitvoering<br> leveren | Dynamische<br><br> uitvoering downloaden |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PSD **‡** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |

**‡** De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die door Adobe Photoshop wordt gegenereerd en die in het PSD-bestand wordt opgenomen. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

Naast bovenstaande informatie, moet u rekening houden met het volgende:

* De ondersteuning voor EPS-bestanden is alleen van toepassing op rasterafbeeldingen. Miniatuurgeneratie voor EPS-vectorafbeeldingen wordt bijvoorbeeld niet standaard ondersteund. Om steun toe te voegen, [vorm ImageMagick](best-practices-for-imagemagick.md). Om derdehulpmiddelen te integreren om extra mogelijkheden toe te laten, zie de lijn Gebaseerde Behandelaar [van Media van het](media-handlers.md#command-line-based-media-handler)Bevel.

* Metagegevensterugkoppeling werkt voor PSB-bestandsindeling wanneer deze wordt toegevoegd aan de `NComm` handler.

* Zie [Adobe Illustrator (AI), Postscript (EPS) en PDF-bestandsindelingen voor informatie over het gebruik van dynamische media voor het weergeven en genereren van dynamische uitvoeringen voor EPS-bestanden.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Voor EPS-bestanden wordt terugschrijven van metagegevens ondersteund in PostScript Document Structuring Convention (PS-Adobe) versie 3.0 of hoger.

## Niet-ondersteunde indelingen voor rasterafbeeldingen in Dynamic Media (#unsupported-image-formats-dynamic-media)

In de volgende tabel worden de subtypen van rasterafbeeldingsindelingen beschreven die *niet* worden ondersteund in Dynamic Media. In de tabel staan ook suggesties voor methoden die u kunt gebruiken om dergelijke bestanden te detecteren.

| Format | Wat wordt niet ondersteund? | Voorgestelde detectiemethode |
|---|---|---|
| JPEG | Bestanden waarin de eerste drie bytes onjuist zijn. | Als u een JPEF-bestand wilt identificeren, moeten de initiële drie bytes van dat bestand zijn `ff d8 ff`. Als het iets anders is, wordt het niet geclassificeerd als JPEG.<br>・ Er is geen software die u kan helpen met dit probleem.<br>・ Een klein programma C++/java dat de aanvankelijke drie bytes van een dossier leest zou deze types van dossiers moeten kunnen ontdekken.<br>・ Het kan beter zijn om de bron van dergelijke dossiers te volgen en het hulpmiddel te bekijken dat het dossier produceert. |
| PNG | Bestanden met een IDAT-segmentgrootte groter dan 100 MB. | U kunt dit probleem detecteren met [libpng](http://www.libpng.org/pub/png/libpng.html) in C++. |
| PSB |  | Gebruik exiftool als het bestandstype PSB is.<br>Voorbeeld in een ExifTool-logboek:<br>1. Bestandstype: `PSB` |
| PSD | Bestanden met een andere kleurruimte dan CMYK, RGB, Grijswaarden of Bitmap worden niet ondersteund.<br>DuoTone-, Lab- en Geïndexeerde kleurruimten worden niet ondersteund. | Gebruik ExifTool als de kleurmodus Duotoon is.<br>Voorbeeld in een ExifTool-logboek:<br>1. Kleurmodus: `Duotone` |
|  | Bestanden met abrupte eindes. | Adobe kan deze voorwaarde niet detecteren. Dergelijke bestanden kunnen ook niet worden geopend met Adobe PhotoShop. Adobe raadt u aan het programma te onderzoeken dat is gebruikt om een dergelijk bestand te maken en problemen bij de bron op te lossen. |
|  | Bestanden met een bitdiepte groter dan 16. | Gebruik ExifTool als de bitdiepte groter is dan 16.<br>Voorbeeld in een ExifTool-logboek:<br>1. Bitdiepte: `32` |
|  | Bestand met Lab-kleurruimte. | Gebruik exiftool als de kleurmodus Lab is.<br>Voorbeeld in een ExifTool-logboek:<br>1. Kleurmodus: `Lab` |
| TIFF | Bestanden met zwevende-kommagegevens. Een TIFF-bestand met 32-bits diepte wordt dus niet ondersteund. | Gebruik ExifTool als het MIME-type is `image/tiff` en de waarde van SampleFormat `Float` is. Voorbeeld in een ExifTool-logboek:<br>1. MIME-type: `image/tiff`<br>Voorbeeldindeling: `Float #`<br>2. MIME-type: `image/tiff`<br>Voorbeeldindeling: `Float; Float; Float; Float` |
|  | Bestanden met Lab-kleurruimte. | Gebruik ExifTool als de kleurmodus Lab is.<br>Voorbeeld in een ExifTool-logboek:<br>1. Kleurmodus: `Lab` |

## Ondersteunde PDF Rasterizer-bibliotheek {#supported-pdf-rasterizer-library}

De Adobe PDF Rasterizer-bibliotheek genereert miniaturen en voorvertoningen van hoge kwaliteit voor grote en inhoudintensieve Adobe Illustrator- en PDF-bestanden. Adobe raadt u aan de PDF Rasterizer-bibliotheek te gebruiken voor het volgende:

* Inhoudsintensieve AI/PDF-bestanden die bronintensief zijn voor verwerking.
* AI/PDF-bestanden waarvoor standaard geen miniaturen worden gegenereerd.
* AI-bestanden met Pantone Matching System (PMS)-kleuren.

Zie [Werken met PDF Rasterizer](aem-pdf-rasterizer.md).

## Ondersteunde bibliotheek voor afbeeldingstranscodering {#supported-image-transcoding-library}

De Adobe Imaging Transcoding-bibliotheek is een oplossing voor beeldverwerking die kernfuncties voor het verwerken van afbeeldingen uitvoert, zoals coderen, transcoderen, resampling en vergroten/verkleinen.

De bibliotheek voor grafische transformatie ondersteunt de volgende MIME-typen: JPG/JPEG, PNG (8-bits en 16-bits), GIF, BMP, TIFF/Gecomprimeerde TIFF (behalve 32-bits TIFF-bestanden en PTIFF-bestanden), ICO en ICN.

Zie [Afbeeldingstransformatiebibliotheek](imaging-transcoding-library.md).

## Ondersteunde Camera Raw {#supported-camera-raw}

Met de Adobe Camera Raw-bibliotheek kunnen AEM Assets Raw-afbeeldingen innemen. Zie [Camera Raw-ondersteuning](camera-raw.md).

## Ondersteunde indelingen voor middelendocumenten {#supported-document-formats}

Documentindelingen die worden ondersteund voor functies voor middelenbeheer zijn als volgt:

| Format | Opslag | Metagegevensbeheer<br> | Metagegevens<br> extraheren | Miniaturen<br> genereren | Interactieve<br> bewerking | Metagegevens<br> terugschrijven | [Inzichten](touch-ui-asset-insights.md) | [Gekoppelde assets](use-assets-across-connected-assets-instances.md) |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
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

## Ondersteunde documentindelingen in dynamische media (#supported-document-formats-dynamic-media)

| Format | Uploaden<br> (invoerindeling) | Afbeeldingsvoorinstelling<br> maken<br><br> (uitvoerindeling) | Voorvertoning<br> van dynamische<br> uitvoering | Dynamische<br> uitvoering<br> leveren | Dynamische<br><br> uitvoering downloaden |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |

Overweeg het volgende naast de bovenstaande functionaliteit:

* Zie [Adobe Illustrator (AI), Postscript (EPS) en PDF-bestandsindelingen als u dynamische media wilt gebruiken om dynamische uitvoeringen voor PDF-bestanden te genereren.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Zie [Adobe Illustrator (AI), Postscript (EPS) en PDF-bestandsindelingen voor informatie over het gebruik van dynamische media voor het weergeven en genereren van dynamische uitvoeringen voor AI-bestanden.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Zie de bestandsindeling [InDesign (INDD) als u dynamische media wilt gebruiken om dynamische uitvoeringen voor INDD-bestanden te genereren](../assets/managing-image-presets.md#indesign-indd-file-format).

## Ondersteunde multimedia-indelingen {#supported-multimedia-formats}

|  | Opslag | Metagegevensbeheer | Metagegevensextractie | Miniaturen genereren | FFMPEG-transcodering |
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

## Ondersteunde invoervideo-indelingen in Dynamic Media voor transcodering {#supported-input-video-formats-for-dynamic-media-transcoding}

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

| Indelingen | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Dynamische levering van media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

## Overige ondersteunde indelingen {#other-supported-formats}

De toepasbaarheid van algemene DAM-workflows voor een aantal andere bestandsindelingen wordt in de onderstaande tabel beschreven. De gebruikelijke DAM-functionaliteit zoals opslag, versioning, ACL, workflow, publiceren en metagegevensbeheer, behalve Dynamic Media Delivery, wordt voor alle bestanden ondersteund.

| Indelingen | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Dynamische levering van media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript (indien geconfigureerd met eigen leveringsdomein) |  |  |  |  |  | ✓ |

## Ondersteunde MIME-typen {#supported-mime-types}

Standaard detecteert AEM het bestandstype met de bestandsextensie. AEM kan het van de inhoud van de dossiers ontdekken. Selecteer voor de laatste optie de optie MIME [!UICONTROL detecteren uit inhoud] in [!UICONTROL Day CQ DAM Mime Type Service] in de AEM-webconsole.

Een lijst van gesteunde types MIME is beschikbaar in CRXDE Lite bij `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

Zie MIME op type-Gebaseerd [configureren voor ondersteuning](config-dynamic.md)voor uploadtaakparameters.

Zie ook [het toelaten van MIME op type-gebaseerde Activa/Scene7 uploadt baanparametersteun](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

| Bestandsextensie | MIME-type/internet-mediatype | Standaardwaarde voor jobParam | Toegestane jobParam-waarde |
|---|---|---|---|
| Afbeelding | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | De standaardjobParam is van toepassing op alle mime-afbeeldingselementen.<ul><li>[knockoutBackgroundOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_knockout_background_options.html)</li><li>manualCropOptions</li><li>[autoColorCropOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_auto_color_crop_options)</li><li>[autoTransparentCropOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_auto_transparent_crop_options)</li><li>[colorManagementOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_color_management_options.html)</li><li>[autoSetCreationOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_auto_set_creation_options.html)</li><li>[emailSetting](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/string_constants/index.html?f=r_email_settings)</li><li>[xmpKeywords](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_xmp_keywords)</li><li>[unsharpMaskOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_unsharp_mask_options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_exclude_master_video_from_avs) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_post_script_options.html)</li><li> [illustratorOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_illustrator_options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>applicatie/eps</li><li>application/x-eps</li><li>afbeelding/eps</li><li>image/x-eps</li></ul> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_pdf_options) |
| PFB | application/x-font-type1 |  |  |
| PGM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_post_script_options)</li><li>[illustratorOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_illustrator_options)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[PhotoshopOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_photoshop_options)</li><li>[photoshopLayerOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_photoshop_layer_options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/web |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Schakel op MIME-type gebaseerde elementen/Scene7 in om taakparameterondersteuning](../sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support)te uploaden.

