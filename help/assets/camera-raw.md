---
title: "[!DNL Adobe Camera Raw] ondersteuning voor het verwerken van digitale elementen"
description: Leer hoe te om  [!DNL Adobe Camera Raw]  steun in  [!DNL Adobe Experience Manager Assets] toe te laten
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

U kunt de [!DNL Adobe Camera Raw] -ondersteuning inschakelen voor het verwerken van Raw-bestandsindelingen, zoals CR2, NEF en RAF, en voor het renderen van afbeeldingen in de JPEG-indeling. De functionaliteit wordt gesteund in [!DNL Adobe Experience Manager Assets] gebruikend het [ Camera Raw pakket ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) beschikbaar bij de Distributie van de Software.

>[!NOTE]
>
>De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.

Voer de volgende stappen uit om [!DNL Camera Raw] support in [!DNL Experience Manager Assets] in te schakelen:

1. Download het [[!DNL Camera Raw]  pakket ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-cameraraw-pkg-1.4.8.zip) van [!DNL Software Distribution].
1. Toegang `https://[aem_server]:[port]/workflow`. Open de **[!UICONTROL DAM Update Asset]** -workflow.
1. Bewerk de stap **[!UICONTROL Process Thumbnails]** .
1. Geef de volgende configuratie op het tabblad **[!UICONTROL Thumbnails]** op:

   * **[!UICONTROL Thumbnails]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Skip Mime Types]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![ chlimage_1-128 ](assets/chlimage_1-334.png)

1. Geef op het tabblad **[!UICONTROL Web Enabled Image]** in het veld **[!UICONTROL Skip List]** `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)` op.

   ![ chlimage_1-129 ](assets/chlimage_1-335.png)

1. Voeg vanuit het zijpaneel de stap **[!UICONTROL Camera Raw/DNG Handler]** onder de stap **[!UICONTROL Process Thumbnails]** toe.
1. Voeg in de stap **[!UICONTROL Camera Raw/DNG Handler]** de volgende configuratie toe op het tabblad **[!UICONTROL Arguments]** :

   * **[!UICONTROL Mime Types]**: `image/dng` and `image/x-raw-(.*)`
   * **[!UICONTROL Command]** :

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![ chlimage_1-130 ](assets/chlimage_1-336.png)

1. Klik op **[!UICONTROL Save]**.

>[!NOTE]
>
>Controleer of de bovenstaande configuratie gelijk is aan de configuratie van **[!UICONTROL Sample DAM Update Asset With Camera RAW and DNG Handling Step]** .

U kunt nu Camera Raw-bestanden importeren in Assets. Nadat u het Camera Raw pakket hebt geïnstalleerd en de vereiste workflow hebt geconfigureerd, wordt de optie **[!UICONTROL Image Adjust]** weergegeven in de lijst met zijvensters.

![ chlimage_1-131 ](assets/chlimage_1-337.png)

*Cijfer: Opties in de zijruit.*

![ chlimage_1-132 ](assets/chlimage_1-338.png)

*Cijfer: De optie van het gebruik om lichtgewichtuitgeeft aan uw beelden te maken.*

Nadat u de bewerkingen hebt opgeslagen in een [!DNL Camera Raw] -afbeelding, wordt een nieuwe uitvoering `AdjustedPreview.jpg` gegenereerd voor de afbeelding. Voor andere afbeeldingstypen, behalve [!DNL Camera Raw] , worden de wijzigingen in alle uitvoeringen doorgevoerd.

## Tips en trucs, bekende problemen en beperkingen {#best-practices}

De functionaliteit heeft de volgende beperkingen:

* De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.
* Metagegevensterugname wordt niet ondersteund voor RAW- en DNG-indelingen.
* De bibliotheek van [!DNL Camera Raw] heeft beperkingen rond de totale pixel het in een tijd kan verwerken. Op dit moment kan het maximaal 65000 pixels aan de lange zijde van een bestand of 512 MP verwerken, ongeacht de criteria die het eerst worden aangetroffen.
