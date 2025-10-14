---
title: Aanbevolen procedures voor het verwerken van de ondersteunde bestandsindelingen
description: Aanbevolen procedures om de diverse ondersteunde bestandstypen te verwerken met  [!DNL Experience Manager Assets] .
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

# Aanbevolen werkwijzen voor Assets-bestandsindelingen {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] biedt ondersteuning voor een groot aantal bibliotheken met bestandsindelingen van leveranciers en derden, zodat gebruikers aan verschillende vereisten voor bestandsondersteuning kunnen voldoen. Tot de ondersteunde bibliotheken voor Adoben behoren [!DNL Adobe Camera Raw] , Gibson, Adobe PDF Rasterizer en [!DNL Adobe InDesign Server] . Daarnaast biedt [!DNL Experience Manager Assets] ondersteuning voor bibliotheken van derden, zoals [!DNL ImageMagick] , [!DNL TwelveMonkeys] , enzovoort.

Voor de gesteunde dossierformaten, zie [&#x200B; Assets gesteunde formaten &#x200B;](/help/assets/assets-formats.md).

>[!TIP]
>
>Als u [!DNL Experience Manager] gebruikt op Adobe Managed Services (AMS), neemt u contact op met de klantenondersteuning van de Adobe als u van plan bent veel grote PSD of PSB-bestanden te verwerken. Werk samen met de medewerker van de klantenondersteuning van de Adobe om deze best practices voor uw AMS-implementatie te implementeren en de best mogelijke tools en modellen te kiezen voor de eigen indelingen van de Adobe. [!DNL Experience Manager] verwerkt mogelijk geen PSB-bestanden met zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels.

## [!DNL Adobe Camera Raw] library {#adobe-camera-raw-library}

Voor optimale prestaties raadt de Adobe aan [!DNL Adobe Camera Raw] -bibliotheek te gebruiken voor RAW- en DNG-bestanden.

[!DNL Adobe Camera Raw] -bibliotheek ondersteunt CMYK-kleurprofiel als invoer. De uitvoer wordt echter alleen in de kleurruimte RGB gegenereerd en uitvoer in de indeling JPEG wordt alleen ondersteund. De kleurruimte van het bronbestand (bijvoorbeeld CMYK) blijft niet behouden in de miniaturen.

Voor meer informatie, zie [&#x200B; Camera Raw steun &#x200B;](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-bibliotheek {#adobe-pdf-rasterizer-library}

Voor de beste resultaten raadt de Adobe aan de Adobe PDF Rasterizer-bibliotheek te gebruiken voor de volgende bestanden:

* Zware, inhoudintensieve PDF-bestanden
* AI-bestanden met miniaturen die niet uit het vak zijn gegenereerd
* Voor AI-bestanden met SPOT-kleuren (PMS)

Miniaturen en voorvertoningen die worden gegenereerd met de Rasterizer-PDF, zijn beter van kwaliteit dan rasteruitvoer die niet in de doos wordt weergegeven. De Adobe PDF Rasterizer-bibliotheek biedt geen ondersteuning voor conversie van kleurruimten. Ongeacht de kleurruimte van het PDF-bronbestand genereert Adobe PDF Rasterizer alleen RGB-uitvoer.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe raadt u aan [!DNL Adobe InDesign Server] te gebruiken om [!DNL Adobe InDesign] -specifieke uitvoeringen, zoals IDML en HTML, te extraheren. Voor meer informatie, zie [&#x200B; Toevoegend de activa van de Experience Manager als verwijzingen in Adobe InDesign &#x200B;](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] genereert en levert meerdere variaties van rijke inhoud in real-time via het algemene, schaalbare en voor prestaties geoptimaliseerde netwerk. Het dient voor interactieve kijkervaringen en stroomlijnt het beheerproces voor digitale campagnes. Voor details rond het toelaten van [!DNL Dynamic Media], zie [&#x200B; Vormend Dynamic Media &#x200B;](/help/assets/config-dynamic.md).

Op dit moment kan [!DNL Dynamic Media] video&#39;s met maximaal 15 GB aan inhoud per bestand ondersteunen.

## ImageMagick-bibliotheek {#imagemagick-library}

De Adobe raadt aan de ImageMagick-bibliotheek in de volgende scenario&#39;s te gebruiken:

* Miniatuurweergaven genereren voor EPS-bestanden.
* Hiermee behoudt u de afbeeldingsprofielgegevens.
* De transparantie behouden.
* PSD- en PSB-bestanden verwerken.

Om te weten hoe te opstelling de [!DNL ImageMagick] bibliotheek in [!DNL Experience Manager], zie [&#x200B; Gebruikend ImageMagick &#x200B;](/help/assets/media-handlers.md#an-example-using-imagemagick). Voor optimaal gebruik, zie [&#x200B; Beste praktijken voor het Vormen ImageMagick &#x200B;](/help/assets/best-practices-for-imagemagick.md).

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

Voor details, zie [&#x200B; Beeldend Transcoding Bibliotheek &#x200B;](/help/assets/imaging-transcoding-library.md).
