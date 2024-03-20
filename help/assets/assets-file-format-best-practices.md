---
title: Aanbevolen procedures voor het verwerken van de ondersteunde bestandsindelingen
description: Aanbevolen procedures voor het verwerken van de verschillende ondersteunde bestandstypen met [!DNL Experience Manager Assets].
contentOwner: AG
role: Admin
feature: Asset Management,Developer Tools
exl-id: da080f12-4cf7-4c26-901b-cd40d9c00bcb
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor bestandsindelingen voor elementen {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] Biedt ondersteuning voor een groot aantal bibliotheken met bedrijfseigen bestandsindelingen en bestandsindelingen van derden, zodat gebruikers aan verschillende vereisten voor bestandsondersteuning kunnen voldoen. Tot de ondersteunde bibliotheken met Adoben behoren: [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer, en [!DNL Adobe InDesign Server]. Daarnaast [!DNL Experience Manager Assets] biedt ondersteuning voor bibliotheken van derden, waaronder [!DNL ImageMagick], [!DNL TwelveMonkeys], enzovoort.

Zie voor de ondersteunde bestandsindelingen [Ondersteunde indelingen voor middelen](/help/assets/assets-formats.md).

>[!TIP]
>
>Als u [!DNL Experience Manager] op Adobe Managed Services (AMS), vraag aan de Steun van de Klant van de Adobe als u van plan bent om veel grote PSD of PSB dossiers te verwerken. Werk samen met de medewerker van de klantenondersteuning van de Adobe om deze best practices voor uw AMS-implementatie te implementeren en de best mogelijke tools en modellen te kiezen voor de eigen indelingen van de Adobe. [!DNL Experience Manager] PSB-bestanden met een zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, worden mogelijk niet verwerkt.

## [!DNL Adobe Camera Raw] bibliotheek {#adobe-camera-raw-library}

Voor optimale prestaties raadt de Adobe het gebruik van [!DNL Adobe Camera Raw] bibliotheek voor RAW- en DNG-bestanden.

[!DNL Adobe Camera Raw] De bibliotheek ondersteunt CMYK-kleurprofiel als invoer. De uitvoer wordt echter alleen in de kleurruimte RGB gegenereerd en uitvoer in de indeling JPEG wordt alleen ondersteund. De kleurruimte van het bronbestand (bijvoorbeeld CMYK) blijft niet behouden in de miniaturen.

Zie voor meer informatie [Camera Raw ondersteuning](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-bibliotheek {#adobe-pdf-rasterizer-library}

Voor de beste resultaten raadt de Adobe aan de Adobe PDF Rasterizer-bibliotheek te gebruiken voor de volgende bestanden:

* Zware, inhoudintensieve PDF-bestanden
* AI-bestanden met miniaturen die niet uit het vak zijn gegenereerd
* Voor AI-bestanden met SPOT-kleuren (PMS)

Miniaturen en voorvertoningen die worden gegenereerd met de Rasterizer-PDF, zijn beter van kwaliteit dan rasteruitvoer die niet in de doos wordt weergegeven. De Adobe PDF Rasterizer-bibliotheek biedt geen ondersteuning voor conversie van kleurruimten. Ongeacht de kleurruimte van het PDF-bronbestand genereert Adobe PDF Rasterizer alleen RGB-uitvoer.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe raadt u aan [!DNL Adobe InDesign Server] om te extraheren [!DNL Adobe InDesign]-specifieke uitvoeringen, zoals IDML en HTML. Zie voor meer informatie [Elementen van Experience Managers toevoegen als verwijzingen in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] produceert en levert veelvoudige variaties van rijke inhoud in echt - tijd door zijn globaal, scalable, en prestaties-geoptimaliseerd netwerk. Het dient voor interactieve kijkervaringen en stroomlijnt het beheerproces voor digitale campagnes. Voor meer informatie over inschakelen [!DNL Dynamic Media], zie [Dynamic Media configureren](/help/assets/config-dynamic.md).

Momenteel [!DNL Dynamic Media] ondersteunt video&#39;s met maximaal 15 GB inhoud per bestand.

## ImageMagick-bibliotheek {#imagemagick-library}

De Adobe raadt aan de ImageMagick-bibliotheek in de volgende scenario&#39;s te gebruiken:

* Miniatuurweergaven genereren voor EPS-bestanden.
* Hiermee behoudt u de afbeeldingsprofielgegevens.
* De transparantie behouden.
* PSD- en PSB-bestanden verwerken.

Om te weten hoe te opstelling [!DNL ImageMagick] bibliotheek in [!DNL Experience Manager], zie [ImageMagick gebruiken](/help/assets/media-handlers.md#an-example-using-imagemagick). Voor optimaal gebruik raadpleegt u [Beste praktijken voor het Vormen ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Bibliotheek voor transformatie van afbeeldingen {#image-transcoding-library}

De Adobe Imaging Transcoding Library is een oplossing voor beeldverwerking die kernfuncties voor beeldverwerking uitvoert, zoals beeldcodering, transcodering, hersampling, formaatwijziging, enzovoort.

De Beeldtransformatiebibliotheek ondersteunt de volgende MIME-typen:

* JPG/JPEG
* PNG (8 bits en 16 bits)
* GIF
* BMP
* TIFF/Gecomprimeerde TIFF (behalve 32 bits TIFF en PTiff).
* ICO
* ICN

Zie voor meer informatie [Afbeeldingstransformatiebibliotheek](/help/assets/imaging-transcoding-library.md).
