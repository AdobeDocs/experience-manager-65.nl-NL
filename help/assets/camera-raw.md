---
title: Camera Raw-ondersteuning
description: Leer hoe u ondersteuning voor Camera Raw inschakelt in Adobe Experience Manager-middelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 44daaa61f7328e79fd4e11a503b0eef3ff9ffb56

---


# Ondersteuning voor het verwerken van afbeeldingen met Camera Raw {#camera-raw-support}

U kunt Camera Raw-ondersteuning inschakelen voor het verwerken van Raw-bestandsindelingen, zoals CR2, NEF en RAF, en voor het renderen van afbeeldingen in de JPEG-indeling. De functionaliteit wordt ondersteund in Adobe Experience Manager Assets met behulp van het [Camera Raw-pakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) dat beschikbaar is via Package Share.

>[!NOTE]
>
>De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.

Voer de volgende stappen uit om Camera Raw-ondersteuning in Adobe Experience Manager-middelen in te schakelen:

1. Download het [Camera Raw-pakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) van het Delen van pakketten.
1. Toegang `https://[aem_server]:[port]/workflow`. Open de workflow **[!UICONTROL DAM Update Asset]** .
1. Open de stap Miniaturen **** verwerken.
1. Geef de volgende configuratie op het tabblad **[!UICONTROL Miniaturen]** op:

   * **[!UICONTROL Miniaturen]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL MIME-typen]** overslaan: `skip:image/dng, skip:image/x-raw-(.*)`
   ![chlimage_1-128](assets/chlimage_1-334.png)

1. Geef op het tabblad **[!UICONTROL Web Enabled Image]** (Afbeelding **[!UICONTROL voor web ingeschakeld) in het veld]** Skip List `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`(Lijstoverslaan).

   ![chlimage_1-129](assets/chlimage_1-335.png)

1. Voeg vanuit het zijpaneel de stap **[!UICONTROL Camera Raw/DNG Handler]** toe onder de stap **[!UICONTROL Miniatuurverwezenlijking]** .
1. Voeg in de stap **[!UICONTROL Camera Raw/DNG Handler]** de volgende configuratie toe op het tabblad **[!UICONTROL Argumenten]** :

   * **[!UICONTROL MIME-typen]**: `image/dng` en `image/x-raw-(.*)`
   * **[!UICONTROL Opdracht]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`
   ![chlimage_1-130](assets/chlimage_1-336.png)

1. Click **[!UICONTROL Save]**.

>[!NOTE]
>
>Zorg ervoor dat de bovenstaande configuratie hetzelfde is als het **[!UICONTROL voorbeeld-DAM-updateelement met de configuratie van de stappen]** voor Camera RAW en DNG-afhandeling.

U kunt nu Camera Raw-bestanden importeren in AEM-elementen. Nadat u het Camera RAW-pakket hebt geïnstalleerd en de vereiste workflow hebt geconfigureerd, wordt de optie **[!UICONTROL Afbeelding aanpassen]** weergegeven in de lijst met zijvensters.

![chlimage_1-135](assets/chlimage_1-337.png)

*Afbeelding: Opties in het zijpaneel.*

![chlimage_1-132](assets/chlimage_1-338.png)

*Afbeelding: Gebruik deze optie om lichte bewerkingen uit te voeren op uw afbeeldingen.*

Nadat u de bewerkingen in een Camera Raw-afbeelding hebt opgeslagen, `AdjustedPreview.jpg` wordt een nieuwe uitvoering voor de afbeelding gegenereerd. Voor andere afbeeldingstypen, behalve Camera Raw, worden de wijzigingen in alle uitvoeringen doorgevoerd.

## Beste werkwijzen, bekende problemen en beperkingen {#best-practices}

De functionaliteit heeft de volgende beperkingen:

* De functionaliteit ondersteunt alleen JPEG-uitvoeringen. Deze functie wordt ondersteund in Windows 64-bits, Mac OS en RHEL 7.x.
* Metagegevensterugname wordt niet ondersteund voor RAW- en DNG-indelingen.
* De Camera Raw-bibliotheek heeft beperkingen ten opzichte van het totale aantal pixels dat per keer kan worden verwerkt. Op dit moment kan het maximaal 65000 pixels aan de lange zijde van een bestand of 512 MP verwerken, ongeacht de criteria die het eerst worden aangetroffen.
