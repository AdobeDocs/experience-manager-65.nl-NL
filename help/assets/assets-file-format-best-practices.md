---
title: Aanbevolen procedures voor het verwerken van de ondersteunde bestandsindelingen
description: Aanbevolen procedures voor het verwerken van de verschillende ondersteunde bestandstypen met [!DNL Experience Manager Assets].
contentOwner: AG
role: Admin
feature: Asset Management,Developer Tools
exl-id: da080f12-4cf7-4c26-901b-cd40d9c00bcb
source-git-commit: b2faf81983216bef9151548d90ae86f1c26a9f91
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor bestandsindelingen voor elementen {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] Biedt ondersteuning voor een groot aantal bibliotheken met bedrijfseigen bestandsindelingen en bestandsindelingen van derden, zodat gebruikers aan verschillende vereisten voor bestandsondersteuning kunnen voldoen. Tot de ondersteunde Adobe-bibliotheken behoren [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer en [!DNL Adobe InDesign Server]. Daarnaast biedt [!DNL Experience Manager Assets] ondersteuning voor bibliotheken van derden, zoals [!DNL ImageMagick], [!DNL TwelveMonkeys] enzovoort.

Zie [Ondersteunde indelingen voor elementen](/help/assets/assets-formats.md) voor de ondersteunde bestandsindelingen.

>[!TIP]
>
>Als u [!DNL Experience Manager] gebruikt op Adobe Managed Services (AMS), kunt u contact opnemen met de Adobe Klantenondersteuning als u van plan bent een groot aantal grote PSD- of PSB-bestanden te verwerken. Werk samen met de medewerker van de klantenondersteuning van Adobe om deze beste praktijken voor uw plaatsing van AMS uit te voeren en de best mogelijke hulpmiddelen en modellen voor merkgebonden formaten van de Adobe te kiezen. [!DNL Experience Manager] PSB-bestanden met een zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, worden mogelijk niet verwerkt.

## [!DNL Adobe Camera Raw] bibliotheek {#adobe-camera-raw-library}

Voor optimale prestaties raadt Adobe u aan [!DNL Adobe Camera Raw]-bibliotheek te gebruiken voor RAW- en DNG-bestanden.

[!DNL Adobe Camera Raw] De bibliotheek ondersteunt CMYK-kleurprofiel als invoer. De uitvoer wordt echter alleen in de kleurruimte RGB gegenereerd en uitvoer in de indeling JPEG wordt alleen ondersteund. De kleurruimte van het bronbestand (bijvoorbeeld CMYK) blijft niet behouden in de miniaturen.

Zie [Camera Raw ondersteuning](/help/assets/camera-raw.md) voor meer informatie.

## Adobe PDF Rasterizer-bibliotheek {#adobe-pdf-rasterizer-library}

Voor de beste resultaten raadt Adobe u aan de Adobe PDF Rasterizer-bibliotheek te gebruiken voor de volgende bestanden:

* Zware, inhoudintensieve PDF-bestanden
* AI-bestanden met miniaturen die niet uit het vak zijn gegenereerd
* Voor AI-bestanden met SPOT-kleuren (PMS)

Miniaturen en voorvertoningen die worden gegenereerd met de Rasterizer-PDF, zijn beter van kwaliteit dan rasteruitvoer die niet in de doos wordt weergegeven. De Adobe PDF Rasterizer-bibliotheek biedt geen ondersteuning voor conversie van kleurruimten. Ongeacht de kleurruimte van het PDF-bronbestand genereert Adobe PDF Rasterizer alleen RGB-uitvoer.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe raadt u aan [!DNL Adobe InDesign Server] te gebruiken om [!DNL Adobe InDesign]-specifieke vertoningen, zoals IDML en HTML te extraheren. Zie [Elementen van Experience Managers toevoegen als verwijzingen in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai) voor meer informatie.

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] produceert en levert veelvoudige variaties van rijke inhoud in echt - tijd door zijn globaal, scalable, en prestaties-geoptimaliseerd netwerk. Het dient voor interactieve kijkervaringen en stroomlijnt het beheerproces voor digitale campagnes. Zie [Dynamic Media configureren](/help/assets/config-dynamic.md) voor meer informatie over het inschakelen van [!DNL Dynamic Media].

[!DNL Dynamic Media] biedt momenteel ondersteuning voor video&#39;s met maximaal 15 GB aan inhoud per bestand.

## ImageMagick-bibliotheek {#imagemagick-library}

Adobe raadt u aan de ImageMagick-bibliotheek in de volgende scenario&#39;s te gebruiken:

* Miniatuurweergaven genereren voor EPS-bestanden.
* Hiermee behoudt u de afbeeldingsprofielgegevens.
* De transparantie behouden.
* PSD- en PSB-bestanden verwerken.

Zie [ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick) gebruiken om te weten hoe u de [!DNL ImageMagick]-bibliotheek instelt in [!DNL Experience Manager]. Voor optimaal gebruik, zie [Beste praktijken voor het Vormen ImageMagick](/help/assets/best-practices-for-imagemagick.md).

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

Zie [Bibliotheek van transformatie van afbeeldingen](/help/assets/imaging-transcoding-library.md) voor meer informatie.
