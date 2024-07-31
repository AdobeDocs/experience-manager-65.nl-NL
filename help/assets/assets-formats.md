---
title: Ondersteunde bestandsindelingen en MIME-typen
description: De formaten van het dossier en MIME types die door  [!DNL Assets]  en  [!DNL Dynamic Media]  worden gesteund en de eigenschappen die voor elk formaat worden gesteund.
contentOwner: AG
mini-toc-levels: 1
role: User, Admin
feature: Asset Management,Renditions
exl-id: a4bcf67b-54f4-4681-9e42-fd4753acde1a
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 0d491be4fb2605220b1558c8c877151ab4405978
workflow-type: tm+mt
source-wordcount: '1862'
ht-degree: 0%

---

# Ondersteunde indelingen in [!DNL Adobe Experience Manager Assets] {#assets-supported-formats}

[!DNL Experience Manager Assets] ondersteunt een groot aantal bestandsindelingen en elke functie biedt verschillende ondersteuning voor verschillende MIME-typen. Als u [!DNL Assets] wilt integreren met andere DAM-oplossingen (Digital Asset Management) en bureaubladsoftware, gebruikt u de XMP [!DNL Extensible Metadata Platform] (Adobe).

Gebruik de legenda om het steunniveau te begrijpen.

| Ondersteuningsniveau | Beschrijving |
| :-----------: | ------------------------------ |
| ✓ | Ondersteund |
| &#42; | Ondersteund met add-onfuncties |
| - | Niet van toepassing |

## Ondersteunde rasterafbeeldingsindelingen in [!DNL Experience Manager] {#supported-raster-image-formats}

De ondersteunde rasterafbeeldingsindelingen in [!DNL Assets] zijn:

| Indeling | Opslag | Metagegevensbeheer | Metagegevensextractie | Miniaturen genereren | Bewerken | Metagegevens terugschrijven | Inzichten |
| ------------ | :------: | :-----------------: | :-----------------: | :------------------: | :------: | :----------------: | :------: |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| PNM | ✓ | ✓ | - | - | - | - | ✓ |
| PGM | ✓ | ✓ | - | - | - | - | ✓ |
| PBM | ✓ | ✓ | - | - | - | - | ✓ |
| PPM | ✓ | ✓ | - | - | - | - | ✓ |
| PSD ‡ | ✓ | ✓ | ✓ | ✓ | - | - | ✓ |
| [ EPS ](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | - | ✓ | - |
| PICT | - | - | - | - | - | - | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ | - | - | - |

‡ De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die door Adobe Photoshop wordt gegenereerd en die in het PSD-bestand wordt opgenomen. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

Naast bovenstaande informatie, moet u rekening houden met het volgende:

* De ondersteuning voor EPS-bestanden is alleen van toepassing op rasterafbeeldingen. Miniatuurgeneratie voor vectorafbeeldingen van EPS wordt bijvoorbeeld niet standaard ondersteund. Om steun toe te voegen, [ vorm ImageMagick ](best-practices-for-imagemagick.md). Om derdehulpmiddelen te integreren om extra mogelijkheden toe te laten, zie [ lijn Gebaseerde van Media Handler ](media-handlers.md#command-line-based-media-handler).

* Metagegevensterugkoppeling werkt voor de PSB-bestandsindeling wanneer deze wordt toegevoegd aan de `NComm` -handler.

* Voor EPS-bestanden wordt terugschrijven van metagegevens ondersteund in PostScript Document Structuring Convention (PS-Adobe) versie 3.0 of hoger.

## Ondersteunde 3D-indelingen {#support-3d-formats}

De volgende lijst met 3D-indelingen wordt ondersteund.

Zie ook [ Werkend met 3D activa in Dynamic Media.](/help/assets/assets-3d.md)

| Indeling | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Voorvertoning miniatuur | 3D-voorvertoning | Dynamic Media-levering |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | - | - | ✓ |

## Ondersteunde PDF Rasterizer-bibliotheek {#supported-pdf-rasterizer-library}

De Adobe PDF Rasterizer-bibliotheek genereert miniaturen en voorvertoningen van hoge kwaliteit voor grote en inhoudintensieve [!DNL Adobe Illustrator] - en PDF-bestanden. Adobe raadt u aan de PDF Rasterizer-bibliotheek te gebruiken voor het volgende:

* Inhoudsintensieve AI/PDF-bestanden die bronintensief zijn voor verwerking.
* AI/PDF-bestanden waarvoor standaard geen miniaturen worden gegenereerd.
* AI-bestanden met PMS-kleuren (Pantone Matching System).

Zie [ Gebruikend PDF Rasterizer ](aem-pdf-rasterizer.md).

## Ondersteunde bibliotheek voor afbeeldingstranscodering {#supported-image-transcoding-library}

De Adobe Imaging Transcoding-bibliotheek is een oplossing voor beeldverwerking die kernfuncties voor het verwerken van afbeeldingen uitvoert, zoals coderen, transcoderen, resampling en vergroten/verkleinen.

De bibliotheek voor grafische transformatie ondersteunt JPG/JPEG, PNG (8-bits en 16-bits), GIF, BMP, TIFF/Gecomprimeerde TIFF (behalve 32-bits TIFF- en PTIFF-bestanden), ICO- en ICN MIME-typen.

Zie [ Beeldend Transcoding Bibliotheek ](imaging-transcoding-library.md).

## Ondersteunde Camera Raw {#supported-camera-raw}

Met de [!DNL Adobe Camera Raw] -bibliotheek kan [!DNL Assets] Raw-afbeeldingen opnemen. Zie [ Camera Raw steun ](camera-raw.md).

## Ondersteunde [!DNL Assets] documentindelingen {#supported-document-formats}

Documentindelingen die worden ondersteund voor functies voor middelenbeheer zijn als volgt:

| Indeling | Opslag | [ het beheer van meta-gegevens ](metadata.md) | Volledige tekst <br> extractie | [ de extractie van meta-gegevens ](metadata.md) | Miniatuur <br> genereren | [ subasset extractie ](managing-linked-subassets.md) | [ Meta-gegevensschrijver ](xmp-writeback.md) | [Gekoppelde assets](use-assets-across-connected-assets-instances.md) |
|---|---|---|---|---|---|---|---|---|
| [ AI ](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ | - |
| DOC | ✓ | ✓ | ✓ | ✓ | - | - | - | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | - | - | - | ✓ |
| ODT | ✓ | ✓ | ✓ | - | - | - | - | ✓ |
| [ PDF ](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ | - | - | - | - | ✓ |
| RTF | ✓ | ✓ | ✓ | - | - | - | - | ✓ |
| TXT | ✓ | ✓ | ✓ | - | - | - | - | ✓ |
| XLS | ✓ | ✓ | ✓ | - | - | - | - | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | - | - | - | ✓ |
| ODS | ✓ | ✓ | ✓ | - | - | - | - | - |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| ODP | ✓ | ✓ | ✓ | - | - | - | - | - |
| [ INDD ](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ | - |
| PS | ✓ | ✓ | - | - | - | - | - | - |
| QXP | ✓ | ✓ | - | - | - | - | - | - |
| EPUB | ✓ | ✓ | - | ✓ | ✓ | - | - | - |

## Ondersteunde multimedia-indelingen {#supported-multimedia-formats}

| | Opslag | Metagegevensbeheer | Metagegevensextractie | Miniaturen genereren | MPEG-transcodering |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ | - | - | &#42; |
| MIDI | ✓ | ✓ | - | - | &#42; |
| 3GP | ✓ | ✓ | - | - | &#42; |
| MP3 | ✓ | ✓ | ✓ | - | &#42; |
| MPG | ✓ | ✓ | - | - | &#42; |
| OGA | ✓ | ✓ | - | - | &#42; |
| OGG | ✓ | ✓ | - | - | &#42; |
| RA | ✓ | ✓ | - | - | &#42; |
| WAV | ✓ | ✓ | - | - | &#42; |
| WMA | ✓ | ✓ | - | - | &#42; |
| DVI | ✓ | ✓ | - | &#42; | &#42; |
| FLV | ✓ | ✓ | - | &#42; | &#42; |
| M4V | ✓ | ✓ | - | &#42; | &#42; |
| MPEG | ✓ | ✓ | - | &#42; | &#42; |
| OGV | ✓ | ✓ | - | &#42; | &#42; |
| MOV | ✓ | ✓ | - | &#42; | &#42; |
| WMV | ✓ | ✓ | - | &#42; | &#42; |
| SWF | ✓ | ✓ | - | - | - |

## Ondersteunde archiefindelingen {#supported-archive-formats}

De ondersteunde archiefindelingen en de toepasbaarheid van de algemene DAM-workflows worden behandeld in de volgende tabel.

| Indelingen | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Dynamic Media-levering |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| ZIP | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

## Overige ondersteunde indelingen {#other-supported-formats}

De toepasbaarheid van de gebruikelijke DAM-functies voor een paar specifieke bestandsindelingen wordt hieronder beschreven.

| Indelingen | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Dynamic Media-levering |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript (indien geconfigureerd met eigen leveringsdomein) | - | - | - | - | - | ✓ |

>[!NOTE]
>
>Het uploaden en distribueren van JavaScript-bestanden is mogelijk niet veilig. Indien nodig kunt u overlays gebruiken om te voorkomen dat gebruikers JS-bestanden uploaden.

## Ondersteunde MIME-typen {#supported-mime-types}

Standaard detecteert [!DNL Experience Manager] het bestandstype met de bestandsextensie. [!DNL Experience Manager] kan de inhoud van de bestanden detecteren. Selecteer voor de laatste optie de optie [!UICONTROL Detect MIME from content] in [!UICONTROL Day CQ DAM Mime Type Service] in de [!DNL Experience Manager] webconsole.

Een lijst met ondersteunde MIME-typen is beschikbaar in CRXDE Lite op `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes` .

| Bestandsextensie | MIME-type/internet-mediatype | Standaardwaarde voor jobParam | Waarde van jobParam toegestaan |
|---|---|---|---|
| Afbeelding | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | Het standaard jobParam is van toepassing op alle MIME-elementen van het afbeeldingstype.<ul><li>[ knockoutBackgroundOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[ manualCropOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[ autoColorCropOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[ autoTransparentCropOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[ colorManagementOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[ autoSetCreationOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[ emailSetting ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[ xmpKeywords ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[ unsharpMaskOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| 3GP | video/3gpp | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| AAC | audio/x-aac | | |
| AFM | application/x-font-type1 | | |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[ postScriptOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [ illustratorOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff | | |
| AVI | video/x-msvideo | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| BMP | image/bmp | | |
| CSS | text/css | | |
| DOC | application/msword | | |
| EPS | <ul><li>application/postscript</li><li>applicatie/eps</li><li>application/x-eps</li><li>afbeelding/eps</li><li>image/x-eps</li></ul> | | |
| F4V | video/x-f4v | | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash | | |
| FLV | video/x-flv | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| FPX | image/vnd.fpx | | |
| GIF | image/gif | | |
| ICC | application/vnd.iccprofile | | |
| ICM | application/vnd.iccprofile | | |
| INDD | application/x-indesign | | |
| JPEG | image/jpeg | | |
| JPG | image/jpeg | | |
| M2V | video/mpeg | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| M4V | video/x-m4v | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| MOV | video/quicktime | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| MP3 | audio/mpeg | | |
| MP4 | video/mp4 | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| MPEG | video/mpeg | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| MPG | video/mpeg | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| MTS | model/vnd.mts | | |
| OGV | video/ogg | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| OTF | application/x-font-otf | | |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [ pdfOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-pdf-options.html) |
| PFB | application/x-font-type1 | | |
| PFM | application/x-font-type1 | | |
| PICT | image/x-pict | | |
| PNG | image/png | | |
| PPT | application/vnd.ms | | |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[ postScriptOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[ illustratorOptions ] (https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[ photoshopOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[ photoshopLayerOptions ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf | | |
| SVG | image/svg+xml | | |
| SWF | application/x-shockwave-flash | | |
| TAR | application/x-tar | | |
| TIF/TIFF | image/tiff | | |
| TTC | application/x-font-ttf | | |
| TTF | application/x-font-ttf | | |
| VOB | video/dvd | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| VTT | text/vtt | | |
| WAV | audio/x-wav | | |
| WEBM | video/web | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| WMA | audio/x-ms-wma | | |
| WMV | video/x-ms-wmv | | [ ExcludeMasterVideoFromAVS ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-deprecated-calls.html) |
| XLS | application/vnd.ms-Excel | | |
| ZIP | application/zip | | |

## Dynamic Media - Ondersteunde invoervideo-indelingen voor transcodering {#supported-input-video-formats-for-dynamic-media-transcoding}

| Videobestandsextensie | Container | Aanbevolen videocodecs | Niet-ondersteunde video-codecs |
|---|---|---|---|
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft® Video 1 (MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (vectoranimatiebestanden) |
| M4V | Apple iTunes | H264/AVC | - |
| MKV | Matroska | H264/AVC | - |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| MP4 | MPEG-4 | H264/AVC (alle profielen) | - |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| MXF ‡ | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | - |
| OGV, OGG | Ogg | Theora, VP3, Dirac | - |
| WebM | WebM | Google VP8 | - |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft® Screen (MSS2), Microsoft® Photo Story (WVP2) |

‡ Deze video-indeling wordt nog niet ondersteund voor gebruik met interactieve video&#39;s in Dynamic Media of voor gebruik met annotatie in Experience Manager Assets.

## Dynamic Media - Ondersteunde documentindelingen {#supported-document-formats-dynamic-media}

| Indeling | Upload <br> (Invoerindeling) | Creeer <br> beeld <br> vooraf ingesteld <br> (het formaat van de Output) | Voorvertoning <br> dynamische <br> uitvoering | Levert <br> dynamische <br> vertoning | <br> dynamische <br> uitvoering downloaden |
|---|:---:|:---:|:---:|:---:|:---:|
| [ AI ](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | - | - | - | - |
| [ INDD ](managing-image-presets.md#indesign-indd-file-format) | ✓ | - | - | - | - |
| [ PDF ](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) (Zie Nota hieronder) | ✓ | ✓ | ✓ | ✓ | ✓ |

>[!NOTE]
>
>Voor beveiligde PDF wordt alleen Uploaden ondersteund.

Overweeg het volgende naast de bovenstaande functionaliteit:

* Om Dynamic Media te gebruiken om dynamische vertoningen voor de dossiers van PDF te produceren, zie [ Adobe Illustrator (AI), Postscript (EPS), en de dossierformaten van PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Om Dynamic Media te gebruiken om dynamische vertoningen voor AI dossiers voor te vertonen en te produceren, zie [ Adobe Illustrator (AI), Postscript (EPS), en het dossierformaten van PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Om Dynamic Media te gebruiken om dynamische vertoningen voor dossiers te produceren INDD, zie [ InDesign (INDD) dossierformaat ](../assets/managing-image-presets.md#indesign-indd-file-format).

## Dynamic Media - Ondersteunde rasterafbeeldingsindelingen {#supported-raster-image-formats-dynamic-media}

| Indeling | Uploaden (invoerindeling) | Afbeeldingsvoorinstelling maken (uitvoerindeling) | Dynamische vertoning voorvertonen | Dynamische uitvoering leveren | Dynamische uitvoering downloaden | Typen instellen die deze indeling ondersteunen |
|---|:---:|:---:|:---:|:---:|:---:| --- |
| AVIF | - | - | - | ✓ | - | - |
| BMP | ✓ | - | - | - | - | [ Beeld ](/help/assets/image-sets.md), [ Gemengde Media ](/help/assets/mixed-media-sets.md), en [ Spin ](/help/assets/spin-sets.md) |
| [ EPS ](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| HEIC | - | - | - | ✓ | - | - |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | [ Beeld ](/help/assets/image-sets.md), [ Gemengde Media ](/help/assets/mixed-media-sets.md), en [ Spin ](/help/assets/spin-sets.md) |
| PICT | ✓ | - | - | - | - | - |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | [ Beeld ](/help/assets/image-sets.md), [ Gemengde Media ](/help/assets/mixed-media-sets.md), en [ Spin ](/help/assets/spin-sets.md) |
| PSD ‡ | ✓ | - | - | - | - | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ | [ Beeld ](/help/assets/image-sets.md), [ Gemengde Media ](/help/assets/mixed-media-sets.md), en [ Spin ](/help/assets/spin-sets.md) |
| WEBP | - | - | - | ✓ | - | - |

<!-- AVIF, HEIC, and WebP added to table above on March 4, 2024 based on CQDOC-21294 -->

‡ De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die door Adobe Photoshop wordt gegenereerd en die in het PSD-bestand wordt opgenomen. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

* De ondersteuning voor EPS-bestanden is alleen van toepassing op rasterafbeeldingen. Miniatuurgeneratie voor vectorafbeeldingen van EPS wordt bijvoorbeeld niet standaard ondersteund. Om steun toe te voegen, [ vorm ImageMagick ](best-practices-for-imagemagick.md). Om derdehulpmiddelen te integreren om extra mogelijkheden toe te laten, zie [ lijn Gebaseerde van Media Handler ](media-handlers.md#command-line-based-media-handler).

* Om [!DNL Dynamic Media] aan voorproef te gebruiken en dynamische vertoningen voor de dossiers van EPS te produceren, zie [ Adobe Illustrator (AI), Postscript (EPS), en het dossierformaten van PDF.](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Voor EPS-bestanden wordt terugschrijven van metagegevens ondersteund in PostScript Document Structuring Convention (PS-Adobe) versie 3.0 of hoger.

## Dynamic Media - Niet-ondersteunde rasterafbeeldingsindelingen {#unsupported-image-formats-dynamic-media}

De volgende lijst beschrijft de subtypes van het dossierformaten van het roosterbeeld die *niet* in Dynamic Media worden gesteund.

Zie ook [ ontdekt niet gestaafde dossierformaten voor het artikel van de Kennisbank van Dynamic Media ](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* PNG-bestanden met een IDAT-segmentgrootte groter dan 100 MB.
* PSB-bestanden
* PSD-bestanden met een andere kleurruimte dan CMYK, RGB, Grijswaarden of Bitmap worden niet ondersteund. DuoTone-, Lab- en Geïndexeerde kleurruimten worden niet ondersteund.
* PSD-bestanden met een bitdiepte groter dan 16.
* TIFF-bestanden met zwevende-kommagegevens.
* TIFF-bestanden met Lab-kleurruimte.

<!-- Topic commented out for now as of March 31, 2020. The topic may still need adjustment so it can be published live, or it may be moved into a KB article instead. Just waiting on feedback in CQDOC-15657. - Rick
## Unsupported raster image formats in Dynamic Media (#unsupported-image-formats-dynamic-media)

The following table describes the sub-types of raster image formats that are *not* supported in Dynamic Media. The table also describes suggested methods you can use to detect such files.

| Format | What is unsupported? | Suggested detection method |
|---|---|---|
| JPEG  | Files where the initial three bytes is incorrect. | To identify a JPEG file, its initial three bytes must be `ff d8 ff`. If they are anything else, then it is not classified as a JPEG.<br>&bull; There is no software tool that can help with this issue.<br>&bull; A small C++/java program which reads the initial three bytes of a file should be able to detect these types of files.<br>&bull; It may be better to track the source of such files and look at the tool generating the file. |
| PNG |  Files that have an IDAT chunk size greater than 100 MB. | You can detect this issue using [libpng](https://www.libpng.org/pub/png/libpng.html) in C++. |
| PSB |  | Use exiftool if the file type is PSB.<br>Example in an ExifTool log:<br>1. File type: `PSB` |
| PSD | Files with a color space other than CMYK, RGB, Grayscale, or Bitmap are not supported.<br>DuoTone, Lab, and Indexed color spaces are not supported. | Use ExifTool if Color mode is Duotone.<br>Example in an ExifTool log:<br>1. Color mode: `Duotone` |
|  | Files with abrupt endings. | Adobe is unable to detect this condition. Also, such files cannot be opened with Adobe PhotoShop. Adobe suggests you examine the tool that was used to create such a file and troubleshoot at the source. |
|  | Files that have a bit depth greater than 16. | Use ExifTool if the bit depth is greater than 16.<br>Example in an ExifTool log:<br>1. Bit depth: `32` |
|  | File that have Lab color space. | Use exiftool if the color mode is Lab.<br>Example in an ExifTool log:<br>1. Color mode: `Lab` |
| TIFF | Files that have floating point data. That is, a TIFF file with 32-bit depth is not supported. | Use ExifTool if the MIME type is `image/tiff` and the SampleFormat has `Float` in its value. Example in an ExifTool log:<br>1. MIME type: `image/tiff`<br>Sample format: `Float #`<br>2. MIME type: `image/tiff`<br>Sample format: `Float; Float; Float; Float` |
|  | Files that have Lab color space. | Use ExifTool if the color mode is Lab.<br>Example in an ExifTool log:<br>1. Color mode: `Lab` |
-->

## Dynamic Media - Ondersteunde 3D-indelingen {#supported-three-d-file-formats-in-dm}

Dynamic Media ondersteunt de volgende 3D-indelingen.

Zie ook [ Werkend met 3D activa in Dynamic Media ](/help/assets/assets-3d.md).

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Steun voor slechts opname; geen het bekijken of interactie is beschikbaar.* USDZ is een eigen 3D-indeling die door Safari- en iOS-apparaten kan worden weergegeven. |

>[!MORELIKETHIS]
>
>* [ laat MIME op type-gebaseerde Assets en Dynamic Media Classic toe uploadt baanparametersteun ](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).
>* [ vorm MIME type-gebaseerd voor uploadbaanparameters steun ](config-dynamic.md).
