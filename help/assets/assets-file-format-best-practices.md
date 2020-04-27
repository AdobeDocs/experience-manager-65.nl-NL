---
title: Aanbevolen procedures voor het verwerken van de verschillende ondersteunde bestandsindelingen met behulp van AEM Assets.
description: Aanbevolen procedures voor het verwerken van de verschillende ondersteunde bestandstypen met AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31234518537ca4a0b7ff36e8d52a3b7b1b8fe4f7

---


# Aanbevolen werkwijzen voor bestandsindelingen voor elementen {#assets-file-format-best-practices}

AEM Assets steunt vele merkgebonden en derdedossierformaatbibliotheken om aan diverse vereisten van de dossiersteun van gebruikers te voldoen. Tot de ondersteunde Adobe-bibliotheken behoren Adobe Camera Raw, Gibson, Adobe PDF Rasterizer en Adobe InDesign Server. AEM Assets biedt bovendien ondersteuning voor bibliotheken van derden, zoals ImageMagick, TwelveMonkeys, enzovoort.

Zie [Elementen met ondersteunde indelingen](/help/assets/assets-formats.md)voor de ondersteunde bestandsindelingen.

>[!TIP]
>
>Als u Experience Manager gebruikt op Adobe Managed Services (AMS), kunt u contact opnemen met de Technische Ondersteuning van Adobe als u een groot aantal grote PSD- of PSB-bestanden wilt verwerken. Werk samen met de vertegenwoordiger van de klantendienst van Adobe om deze beste praktijken voor uw plaatsing van AMS uit te voeren en de best mogelijke hulpmiddelen en de modellen voor merkgebonden formaten van Adobe te kiezen. Experience Manager kan PSB-bestanden met zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, niet verwerken.

## Adobe Camera Raw-bibliotheek {#adobe-camera-raw-library}

Voor optimale prestaties raadt Adobe aan de Adobe Camera Raw-bibliotheek voor RAW- en DNG-bestanden te gebruiken.

Adobe Camera Raw-bibliotheek ondersteunt CMYK-kleurprofiel als invoer. De uitvoer wordt echter gegenereerd in RGB-kleurruimte en alleen uitvoer in JPEG-indeling wordt ondersteund. De kleurruimte van het bronbestand (bijvoorbeeld CMYK) blijft niet behouden in de miniaturen.

Zie Ondersteuning [van](/help/assets/camera-raw.md)Camera Raw voor meer informatie.

## Adobe PDF Rasterizer-bibliotheek {#adobe-pdf-rasterizer-library}

Voor de beste resultaten raadt Adobe u aan de Adobe PDF Rasterizer-bibliotheek te gebruiken voor de volgende bestanden:

* Zware, inhoudintensieve PDF-bestanden
* AI-bestanden met miniaturen die niet uit het vak zijn gegenereerd
* Voor AI-bestanden met SPOT-kleuren (PMS)

Miniaturen en voorvertoningen die worden gegenereerd met PDF Rasterizer, zijn beter van kwaliteit dan rasteruitvoer die niet in de doos wordt weergegeven. De Adobe PDF Rasterizer-bibliotheek ondersteunt geen kleurruimteconversie. Ongeacht de kleurruimte van het PDF-bronbestand wordt in Adobe PDF Rasterizer alleen RGB-uitvoer gegenereerd.

## Adobe InDesign Server {#adobe-indesign-server}

Adobe raadt u aan Adobe InDesign Server te gebruiken om Adobe InDesign-specifieke uitvoeringen, zoals IDML en HTML, te extraheren. Zie AEM-elementen [toevoegen als verwijzingen in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai)voor meer informatie.

##  Dynamic Media {#dynamic-media}

De dynamische Media produceert en levert veelvoudige variaties van rijke inhoud in real time door zijn globaal, scalable, en prestaties-geoptimaliseerd netwerk. Het dient voor interactieve kijkervaringen en stroomlijnt het beheerproces voor digitale campagnes. Zie Dynamische media [configureren voor meer informatie over het inschakelen van dynamische media](/help/assets/config-dynamic.md).

Dynamische media kunnen momenteel video&#39;s ondersteunen van maximaal 20 GB aan inhoud per bestand.

## ImageMagick-bibliotheek {#imagemagick-library}

Adobe raadt u aan de ImageMagick-bibliotheek in de volgende gevallen te gebruiken:

* Miniatuurweergaven genereren voor EPS-bestanden
* Profielgegevens behouden
* Transparantie behouden
* PSD- en PSB-bestanden verwerken

Om te weten hoe te opstelling de bibliotheek ImageMagic in AEM, zie het [Gebruiken ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Voor optimaal gebruik, zie [Beste praktijken voor het Vormen ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Bibliotheek voor transformatie van afbeeldingen {#image-transcoding-library}

De Adobe Imaging Transcoding Library is een oplossing voor beeldverwerking die kernfuncties voor beeldverwerking uitvoert, zoals beeldcodering, transcodering, hersampling, formaatwijziging, enzovoort.

De bibliotheek Imaging Transcoding ondersteunt de volgende MIME-typen:

* JPG/JPEG
* PNG (8 bits en 16 bits)
* GIF
* BMP
* TIFF/gecomprimeerde TIFF (behalve 32 bits TIFF en PTiff).
* ICO
* ICN

Zie [Afbeeldingstransformatiebibliotheek](/help/assets/imaging-transcoding-library.md)voor meer informatie.
