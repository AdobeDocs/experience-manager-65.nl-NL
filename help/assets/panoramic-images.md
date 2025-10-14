---
title: Panoramische afbeeldingen
description: Leer hoe u in Dynamic Media met panoramische afbeeldingen werkt.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
docset: aem65
feature: Panoramic Images,Asset Management
role: User, Admin
exl-id: 4d6fbeb1-94db-4154-9e41-b76033fb4398
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 3%

---

# Panoramische afbeeldingen{#panoramic-images}

In deze sectie wordt beschreven hoe u met de Panorama-viewer werkt om bolvormige panoramische afbeeldingen te renderen voor een indrukwekkende kijkervaring van 360 graden van een kamer, eigenschap, locatie of landschap.

Zie ook [&#x200B; de Kijker beheren stelt &#x200B;](/help/assets/managing-viewer-presets.md) vooraf in.

![&#x200B; panoramisch-image2 &#x200B;](assets/panoramic-image2.png)

## Elementen uploaden voor gebruik met de Panorama-viewer {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Als u een geüpload element wilt kwalificeren als een bolvormige panorama-afbeelding die u wilt gebruiken met de Panorama-viewer, moet het element een van de volgende opties of beide hebben:

* Een hoogte-breedteverhouding van 2.
U kunt de standaardverhouding van 2 in CRXDE Lite bij het volgende met voeten treden:
  `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Gelabeld met de trefwoorden `equirectangular` of `spherical` en `panorama` of `spherical` en `panoramic` . Zie [&#x200B; Gebruikend Markeringen &#x200B;](/help/sites-authoring/tags.md).

Zowel de criteria voor hoogte-breedteverhouding als voor trefwoorden zijn van toepassing op panoramische assets voor de pagina met assetdetails en de `Panoramic Media` WCM-component.

Om activa voor gebruik met de kijker van het Beeld te uploaden Panorama, zie [&#x200B; Assets &#x200B;](/help/assets/manage-assets.md#uploading-assets) uploaden.

## Dynamic Media Classic configureren {#configuring-dynamic-media-classic-scene}

De Panorama-viewer werkt alleen correct in Adobe Experience Manager als u de voorinstellingen voor de Panoramische afbeeldingsviewer synchroniseert met de specifieke metagegevens voor Dynamic Media Classic en Dynamic Media Classic, zodat de viewervoorinstellingen worden bijgewerkt in het JCR. Voor deze synch configureert u Dynamic Media Classic als volgt:

1. Open de [&#x200B; Desktoptoepassing van Dynamic Media Classic &#x200B;](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=nl-NL#getting-started), dan login aan uw rekening.

1. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]** .
1. Selecteer **[!UICONTROL Image Serving]** in het vervolgkeuzemenu boven in de Publish-pagina voor afbeeldingsserver.**[!UICONTROL Publish Context]**

1. Zoek op dezelfde Publish-pagina voor Afbeeldingsserver de kop **[!UICONTROL Request Attributes]** .
1. Zoek onder de kop Aanvraagkenmerken naar **[!UICONTROL Reply Image Size Limit]** . Vergroot vervolgens in de bijbehorende velden Breedte en Hoogte de maximaal toegestane afbeeldingsgrootte voor panoramische afbeeldingen.

   Dynamic Media Classic heeft een limiet van 25.000.000 pixels. De maximaal toegestane grootte voor afbeeldingen met een hoogte-breedteverhouding van 2:1 is 7000 x 3500. Voor standaarddesktopschermen is 4096 x 2048 pixels echter voldoende.

   >[!NOTE]
   >
   >Alleen afbeeldingen die binnen de maximaal toegestane afbeeldingsgrootte vallen, worden ondersteund. Verzoeken om afbeeldingen die groter zijn dan de maximale grootte, leveren een reactie van 403 op.

1. Ga als volgt te werk onder Aanvraagkenmerken:

   * Stel de modus Verduistering aanvragen in op **[!UICONTROL Disabled]** .
   * Vergrendelingsmodus voor aanvragen instellen op **[!UICONTROL Disabled]** .

   Deze instellingen zijn nodig voor het gebruik van de WCM-component `Panoramic Media` in Experience Manager.

1. Selecteer onder aan de Publish-pagina Afbeeldingsserver aan de linkerkant de optie **[!UICONTROL Save]** .

1. Selecteer **[!UICONTROL Close]** in de rechterbenedenhoek.

### Problemen met de WCM-component Panoramische media oplossen {#troubleshooting-the-panoramic-media-wcm-component}

Als u een beeld in de component Panoramische Media in uw WCM en samengevouwen componentenplaceholder liet vallen, los het volgende problemen op:

* Als u een fout van 403 kent waarvoor een verbod geldt, kan deze worden veroorzaakt door het te grote formaat van de gevraagde afbeelding. Herzie de **[!UICONTROL Reply Image Size Limit]** montages in [&#x200B; vormen Dynamic Media Classic &#x200B;](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene).

* Voor een &quot;Ongeldige vergrendeling&quot; op het element of &quot;Parseerfout&quot; die op de pagina wordt weergegeven, schakelt u de modus Verduistering aanvragen en de modus Vergrendelen aanvragen in om ervoor te zorgen dat deze zijn uitgeschakeld.
* Voor een bekroonde canvasfout, opstelling een Pad van het Dossier van de Definitie van de Regel plaatst en maakt CTN voor de vorige verzoeken om het beeldmiddel ongeldig.
* Als de afbeeldingskwaliteit laag wordt na een afbeeldingsaanvraag waarvan de grootte groter is dan de ondersteunde limiet, controleert u of de instelling **[!UICONTROL JPEG Encoding Attributes > Quality]** niet leeg is. Een gebruikelijke instelling voor het veld **[!UICONTROL Quality]** is `95` . U kunt het plaatsen op de pagina van Publish van de Server van het Beeld vinden. Om tot de pagina toegang te hebben, zie [&#x200B; Dynamic Media Classic &#x200B;](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene) vormen.

## Voorvertoning panorama-afbeeldingen {#previewing-panoramic-images}

Zie [&#x200B; Voorproef Assets &#x200B;](/help/assets/previewing-assets.md).

## Publish Panorama-afbeeldingen {#publishing-panoramic-images}

Zie [&#x200B; Publish Assets &#x200B;](/help/assets/publishing-dynamicmedia-assets.md).
