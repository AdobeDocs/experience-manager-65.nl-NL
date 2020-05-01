---
title: Aanbevolen procedures voor het verwerken van de verschillende ondersteunde bestandsindelingen met behulp van [!DNL Adobe Experience Manager Assets].
description: Aanbevolen procedures voor het verwerken van de verschillende ondersteunde bestandstypen met [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5f67b4e5ccd5d7e982732e449050123e917c9914

---


# Aanbevolen werkwijzen voor bestandsindelingen voor elementen {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] Biedt ondersteuning voor een groot aantal bibliotheken met bedrijfseigen bestandsindelingen en bestandsindelingen van derden, zodat gebruikers aan verschillende vereisten voor bestandsondersteuning kunnen voldoen. Tot de ondersteunde Adobe-bibliotheken behoren onder andere [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer en [!DNL Adobe InDesign Server]. Daarnaast [!DNL Experience Manager Assets] worden bibliotheken van derden ondersteund, waaronder [!DNL ImageMagick], [!DNL TwelveMonkeys]enzovoort.

Zie [Elementen met ondersteunde indelingen](/help/assets/assets-formats.md)voor de ondersteunde bestandsindelingen.

>[!TIP]
>
>Als u Adobe Managed Services (AMS) gebruikt, vraagt u de klantenservice van Adobe als u een groot aantal grote PSD- of PSB-bestanden wilt verwerken. [!DNL Experience Manager] Werk samen met de vertegenwoordiger van de klantendienst van Adobe om deze beste praktijken voor uw plaatsing van AMS uit te voeren en de best mogelijke hulpmiddelen en de modellen voor merkgebonden formaten van Adobe te kiezen. [!DNL Experience Manager] PSB-bestanden met een zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, worden mogelijk niet verwerkt.

## [!DNL Adobe Camera Raw] bibliotheek {#adobe-camera-raw-library}

Voor optimale prestaties raadt Adobe aan een [!DNL Adobe Camera Raw] bibliotheek voor RAW- en DNG-bestanden te gebruiken.

[!DNL Adobe Camera Raw] De bibliotheek ondersteunt CMYK-kleurprofiel als invoer. De uitvoer wordt echter gegenereerd in RGB-kleurruimte en alleen uitvoer in JPEG-indeling wordt ondersteund. De kleurruimte van het bronbestand (bijvoorbeeld CMYK) blijft niet behouden in de miniaturen.

Zie Ondersteuning [van](/help/assets/camera-raw.md)Camera Raw voor meer informatie.

## Adobe PDF Rasterizer-bibliotheek {#adobe-pdf-rasterizer-library}

Voor de beste resultaten raadt Adobe u aan de Adobe PDF Rasterizer-bibliotheek te gebruiken voor de volgende bestanden:

* Zware, inhoudintensieve PDF-bestanden
* AI-bestanden met miniaturen die niet uit het vak zijn gegenereerd
* Voor AI-bestanden met SPOT-kleuren (PMS)

Miniaturen en voorvertoningen die worden gegenereerd met PDF Rasterizer, zijn beter van kwaliteit dan rasteruitvoer die niet in de doos wordt weergegeven. De Adobe PDF Rasterizer-bibliotheek ondersteunt geen kleurruimteconversie. Ongeacht de kleurruimte van het PDF-bronbestand wordt in Adobe PDF Rasterizer alleen RGB-uitvoer gegenereerd.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe raadt u aan [!DNL Adobe InDesign Server] [!DNL Adobe InDesign]om specifieke uitvoeringen, zoals IDML en HTML, te extraheren. Zie [Elementen van Experience Manager toevoegen als verwijzingen in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai)voor meer informatie.

## [!DNL Dynamic Media]  {#dynamic-media}

[!DNL Dynamic Media] produceert en levert veelvoudige variaties van rijke inhoud in echt - tijd door zijn globaal, scalable, en prestaties-geoptimaliseerd netwerk. Het dient voor interactieve kijkervaringen en stroomlijnt het beheerproces voor digitale campagnes. Voor details rond het toelaten [!DNL Dynamic Media], zie het [Vormen Dynamische Media](/help/assets/config-dynamic.md).

Op dit moment [!DNL Dynamic Media] kunt u video&#39;s met maximaal 15 GB inhoud per bestand ondersteunen.

## ImageMagick-bibliotheek {#imagemagick-library}

Adobe raadt u aan de ImageMagick-bibliotheek in de volgende gevallen te gebruiken:

* Miniatuurweergaven genereren voor EPS-bestanden.
* Hiermee behoudt u de afbeeldingsprofielgegevens.
* De transparantie behouden.
* PSD- en PSB-bestanden verwerken.

Om te weten hoe te opstelling de [!DNL ImageMagick] bibliotheek in [!DNL Experience Manager], zie [Gebruikend ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Voor optimaal gebruik, zie [Beste praktijken voor het Vormen ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Bibliotheek voor transformatie van afbeeldingen {#image-transcoding-library}

De Adobe Imaging Transcoding Library is een oplossing voor beeldverwerking die kernfuncties voor beeldverwerking uitvoert, zoals beeldcodering, transcodering, hersampling, formaatwijziging, enzovoort.

De Beeldtransformatiebibliotheek ondersteunt de volgende MIME-typen:

* JPG/JPEG
* PNG (8 bits en 16 bits)
* GIF
* BMP
* TIFF/gecomprimeerde TIFF (behalve 32 bits TIFF en PTiff).
* ICO
* ICN

Zie [Afbeeldingstransformatiebibliotheek](/help/assets/imaging-transcoding-library.md)voor meer informatie.
