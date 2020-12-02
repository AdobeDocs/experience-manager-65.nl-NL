---
title: '[!DNL Adobe Camera Raw] ondersteuning.'
description: Leer hoe te om [!DNL Adobe Camera Raw] steun in [!DNL Adobe Experience Manager Assets] toe te laten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: bccc937c1e1a349ab292a748c3c7b9d0c68b6199
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Afbeeldingen verwerken met Camera Raw {#camera-raw-support}

U kunt de ondersteuning van [!DNL Adobe Camera Raw] inschakelen voor het verwerken van Raw-bestandsindelingen, zoals CR2, NEF en RAF, en voor het renderen van afbeeldingen in JPEG-indeling. De functionaliteit wordt ondersteund in [!DNL Adobe Experience Manager Assets] met behulp van het [Camera Raw pakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) dat beschikbaar is bij Softwaredistributie.

>[!NOTE]
>
>De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.

Ga als volgt te werk om [!DNL Camera Raw]-ondersteuning in [!DNL Experience Manager Assets] in te schakelen:

1. Download het [Camera Raw pakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) van de Distributie van de Software.
1. Ga naar `https://[aem_server]:[port]/workflow`. Open de **[!UICONTROL DAM Update Asset]** workflow.
1. Open de stap **[!UICONTROL Process Thumbnails]**.
1. Geef de volgende configuratie op het tabblad **[!UICONTROL Thumbnails]** op:

   * **[!UICONTROL Thumbnails]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Skip Mime Types]**:  `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage_1-128](assets/chlimage_1-334.png)

1. Geef op het tabblad **[!UICONTROL Web Enabled Image]** in het veld **[!UICONTROL Skip List]** `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)` op.

   ![chlimage_1-129](assets/chlimage_1-335.png)

1. Voeg vanuit het zijpaneel de stap **[!UICONTROL Camera Raw/DNG Handler]** onder de stap **[!UICONTROL Thumbnail creation]** toe.
1. Voeg in de stap **[!UICONTROL Camera Raw/DNG Handler]** de volgende configuratie toe op het tabblad **[!UICONTROL Arguments]**:

   * **[!UICONTROL Mime Types]**:  `image/dng` en  `image/x-raw-(.*)`
   * **[!UICONTROL Command]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-130](assets/chlimage_1-336.png)

1. Klik op **[!UICONTROL Save]**.

>[!NOTE]
>
>Zorg ervoor dat de bovenstaande configuratie het zelfde als **[!UICONTROL Sample DAM Update Asset With Camera RAW and DNG Handling Step]** configuratie is.

U kunt nu Camera Raw-bestanden importeren in Elementen. Nadat u het Camera Raw pakket hebt geïnstalleerd en de vereiste workflow hebt geconfigureerd, wordt de optie **[!UICONTROL Image Adjust]** weergegeven in de lijst met zijvensters.

![chlimage_1-131](assets/chlimage_1-337.png)

*Afbeelding: Opties in het zijpaneel.*

![chlimage_1-132](assets/chlimage_1-338.png)

*Afbeelding: Gebruik deze optie om lichte bewerkingen uit te voeren op uw afbeeldingen.*

Nadat u de bewerkingen hebt opgeslagen in een [!DNL Camera Raw]-afbeelding, wordt een nieuwe uitvoering `AdjustedPreview.jpg` gegenereerd voor de afbeelding. Voor andere afbeeldingstypen, behalve [!DNL Camera Raw], worden de wijzigingen in alle uitvoeringen doorgevoerd.

## Beste werkwijzen, bekende problemen en beperkingen {#best-practices}

De functionaliteit heeft de volgende beperkingen:

* De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.
* Metagegevensterugname wordt niet ondersteund voor RAW- en DNG-indelingen.
* De bibliotheek [!DNL Camera Raw] heeft beperkingen rond de totale pixel het in een tijd kan verwerken. Op dit moment kan het maximaal 65000 pixels aan de lange zijde van een bestand of 512 MP verwerken, ongeacht de criteria die het eerst worden aangetroffen.
