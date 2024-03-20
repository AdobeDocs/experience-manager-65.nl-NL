---
title: "[!DNL Adobe Camera Raw] ondersteuning voor de verwerking van digitale middelen"
description: Leer hoe u kunt inschakelen [!DNL Adobe Camera Raw] ondersteuning in [!DNL Adobe Experience Manager Assets]
contentOwner: AG
role: Admin
feature: Developer Tools
exl-id: 7159a908-4c36-42b4-bbb4-d7fb1be4ee1b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Afbeeldingen verwerken met [!DNL Adobe Camera Raw] {#camera-raw-support}

U kunt de [!DNL Adobe Camera Raw] ondersteuning voor het verwerken van Raw-bestandsindelingen, zoals CR2, NEF en RAF, en het renderen van afbeeldingen in de indeling JPEG. De functionaliteit wordt ondersteund in [!DNL Adobe Experience Manager Assets] met de [Camera Raw pakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) beschikbaar bij Softwaredistributie.

>[!NOTE]
>
>De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.

Inschakelen [!DNL Camera Raw] ondersteuning in [!DNL Experience Manager Assets]Voer de volgende stappen uit:

1. Download de [[!DNL Camera Raw] package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-cameraraw-pkg-1.4.8.zip) van [!DNL Software Distribution].
1. Toegang `https://[aem_server]:[port]/workflow`. Open de **[!UICONTROL DAM Update Asset]** workflow.
1. Bewerk de **[!UICONTROL Process Thumbnails]** stap.
1. Geef de volgende configuratie op in de **[!UICONTROL Thumbnails]** tab:

   * **[!UICONTROL Thumbnails]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Skip Mime Types]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage_1-128](assets/chlimage_1-334.png)

1. In de **[!UICONTROL Web Enabled Image]** tabblad, in de **[!UICONTROL Skip List]** veld, specificeren `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![chlimage_1-129](assets/chlimage_1-335.png)

1. Voeg vanuit het zijpaneel de **[!UICONTROL Camera Raw/DNG Handler]** stap onder de **[!UICONTROL Process Thumbnails]** stap.
1. In de **[!UICONTROL Camera Raw/DNG Handler]** stap, voeg de volgende configuratie in toe **[!UICONTROL Arguments]** tab:

   * **[!UICONTROL Mime Types]**: `image/dng` en `image/x-raw-(.*)`
   * **[!UICONTROL Command]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-130](assets/chlimage_1-336.png)

1. Klik op **[!UICONTROL Save]**.

>[!NOTE]
>
>Zorg ervoor dat de bovenstaande configuratie gelijk is aan de **[!UICONTROL Sample DAM Update Asset With Camera RAW and DNG Handling Step]** configuratie.

U kunt nu Camera Raw-bestanden importeren in Elementen. Nadat u het Camera Raw pakket hebt geïnstalleerd en de vereiste workflow hebt geconfigureerd, **[!UICONTROL Image Adjust]** wordt weergegeven in de lijst met zijvensters.

![chlimage_1-131](assets/chlimage_1-337.png)

*Afbeelding: opties in het zijvenster.*

![chlimage_1-132](assets/chlimage_1-338.png)

*Afbeelding: gebruik de optie om foto&#39;s lichtgewichtbewerkingen uit te voeren.*

Nadat u de bewerkingen hebt opgeslagen in een [!DNL Camera Raw] afbeelding, een nieuwe vertoning `AdjustedPreview.jpg` wordt voor de afbeelding gegenereerd. Voor andere afbeeldingstypen, behalve [!DNL Camera Raw], worden de wijzigingen weerspiegeld in alle uitvoeringen.

## Tips en trucs, bekende problemen en beperkingen {#best-practices}

De functionaliteit heeft de volgende beperkingen:

* De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.
* Metagegevensterugname wordt niet ondersteund voor RAW- en DNG-indelingen.
* De [!DNL Camera Raw] De bibliotheek heeft beperkingen rond de totale pixel het in een tijd kan verwerken. Op dit moment kan het maximaal 65000 pixels aan de lange zijde van een bestand of 512 MP verwerken, ongeacht de criteria die het eerst worden aangetroffen.
