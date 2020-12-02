---
title: Panoramische afbeeldingen
description: Leer hoe u met panoramische afbeeldingen werkt in Dynamic Media.
uuid: ced3e5bd-93c8-4d5f-a397-1380d4d0a5e7
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 632a9074-b747-49a1-a57d-1f42bba1f4e9
docset: aem65
translation-type: tm+mt
source-git-commit: cec6c4f9a1a75eb049dd4b8461c36c8d58d46f79
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 5%

---


# Panoramische afbeeldingen{#panoramic-images}

In deze sectie wordt beschreven hoe u met de Panorama-viewer werkt om bolvormige panoramische afbeeldingen te renderen voor een indrukwekkende kijkervaring van 360 graden van een kamer, eigenschap, locatie of landschap.

Zie ook [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

![panoramisch beeld2](assets/panoramic-image2.png)

## Elementen uploaden voor gebruik met de Panorama-viewer {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Als u een geüpload element wilt kwalificeren als een bolvormige panorama-afbeelding die u wilt gebruiken met de Panorama-viewer, moet het element een van de volgende opties of beide hebben:

* Een hoogte-breedteverhouding van 2.
U kunt de standaardverhouding van 2 in CRXDE Lite bij het volgende met voeten treden:
   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Gelabeld met de trefwoorden `equirectangular` of `spherical`en `panorama`, of `spherical` en `panoramic`. Zie [Tags gebruiken](/help/sites-authoring/tags.md).

Zowel de criteria voor hoogte-breedteverhouding als voor trefwoorden zijn van toepassing op panoramische assets voor de pagina met assetdetails en de `Panoramic Media` WCM-component.

Zie [Elementen uploaden](/help/assets/manage-assets.md#uploading-assets) om elementen te uploaden voor gebruik met de Panoramische Image Viewer.

## Dynamic Media Classic (Scene7) {#configuring-dynamic-media-classic-scene} configureren

De Panoramische beeldviewer werkt alleen correct binnen AEM als u de voorinstellingen van de Panoramische afbeeldingsviewer synchroniseert met de specifieke metagegevens voor Dynamic Media Classic (Scene7) en Dynamic Media Classic (Scene7), zodat de voorinstellingen van de viewer worden bijgewerkt in de JCR. Hiertoe configureert u Dynamic Media Classic (Scene7) op de volgende manier:

1. [Meld u ](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) voor elk bedrijfsaccount aan bij Dynamic Media Classic (Scene7).

1. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server.]**
1. Selecteer **[!UICONTROL Image Serving.]** in het vervolgkeuzemenu **[!UICONTROL Publish Context]** op de pagina Publiceren op de afbeeldingsserver

1. Zoek op dezelfde pagina voor het publiceren van afbeeldingsservers de kop **[!UICONTROL Request Attributes.]**
1. Zoek onder de kop Request-kenmerken **[!UICONTROL Reply Image Size Limit.]** Vervolgens in de bijbehorende velden Breedte en Hoogte de maximaal toegestane afbeeldingsgrootte voor panoramische afbeeldingen.

   Dynamic Media Classic (Scene7) heeft een limiet van 25.000.000 pixels. De maximaal toegestane grootte voor afbeeldingen met een hoogte-breedteverhouding van 2:1 is 7000 x 3500. Voor standaarddesktopschermen is 4096 x 2048 pixels echter voldoende.

   >[!NOTE]
   >
   >Alleen afbeeldingen die binnen de maximaal toegestane afbeeldingsgrootte vallen, worden ondersteund. Verzoeken om afbeeldingen die groter zijn dan de maximale grootte, leveren een reactie van 403 op.

1. Ga als volgt te werk onder Aanvraagkenmerken:

   * Modus Verduistering verzoek instellen op **[!UICONTROL Disabled.]**
   * Vergrendelingsmodus voor aanvragen instellen op **[!UICONTROL Disabled.]**

   Deze instellingen zijn nodig voor het gebruik van de WCM-component `Panoramic Media` in AEM.

1. Klik links onder aan de pagina Publiceren afbeeldingsserver op **[!UICONTROL Save.]**

1. Klik in de rechterbenedenhoek op **[!UICONTROL Close.]**

### Problemen met de WCM-component Panoramische media {#troubleshooting-the-panoramic-media-wcm-component} oplossen

Als u een beeld in de component Panoramische Media in uw WCM en samengevouwen componentenplaceholder liet vallen, kunt u het volgende willen problemen oplossen:

* Als u een fout van 403 kent waarvoor een verbod geldt, kan deze zijn veroorzaakt door het te grote formaat van de gevraagde afbeelding. Controleer de **[!UICONTROL Reply Image Size Limit]**-instellingen in [Dynamic Media Classic configureren (Scene7)](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene).

* Voor een &quot;Ongeldige vergrendeling&quot; op het element of &quot;Parseerfout&quot; die op de pagina wordt weergegeven, schakelt u de modus Verduistering aanvragen en de modus Vergrendelen aanvragen in om ervoor te zorgen dat deze zijn uitgeschakeld.
* Voor een bekroonde canvasfout, opstelling een Pad van het Dossier van de Definitie van de Regel en maakt CTN voor de vorige verzoeken om het beeldmiddel ongeldig.
* Als de afbeeldingskwaliteit na een afbeeldingsaanvraag met een formaat groter dan de ondersteunde limiet erg laag wordt, controleert u of de instelling **[!UICONTROL JPEG Encoding Attributes > Quality]** niet leeg is. Een typische instelling voor het veld **[!UICONTROL Quality]** is `95`. U kunt het plaatsen op de de Publish pagina van de Server van het Beeld vinden. Om tot de pagina toegang te hebben, zie [Het vormen van Dynamische Klassieke Media (Scene7)](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene).

## Voorvertoning van panorama-afbeeldingen {#previewing-panoramic-images}

Zie [Elementen voorvertonen](/help/assets/previewing-assets.md).

## Panorama-afbeeldingen {#publishing-panoramic-images} publiceren

Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md).
