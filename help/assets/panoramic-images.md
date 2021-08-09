---
title: Panoramische afbeeldingen
description: Leer hoe u in Dynamic Media met panoramische afbeeldingen werkt.
uuid: ced3e5bd-93c8-4d5f-a397-1380d4d0a5e7
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 632a9074-b747-49a1-a57d-1f42bba1f4e9
docset: aem65
feature: Panoramische afbeeldingen, beheer van bedrijfsmiddelen
role: User, Admin
exl-id: 4d6fbeb1-94db-4154-9e41-b76033fb4398
source-git-commit: 363e5159d290ecfbf4338f6b9793e11b613389a5
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 4%

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

Zie [Elementen uploaden](/help/assets/manage-assets.md#uploading-assets) als u elementen wilt uploaden voor gebruik met de Panoramische Image-viewer.

## Dynamic Media Classic configureren {#configuring-dynamic-media-classic-scene}

De Panorama-viewer werkt alleen correct in Adobe Experience Manager als u de voorinstellingen voor de Panoramische Image Viewer synchroniseert met klassieke metagegevens van Dynamic Media Classic en Dynamic Media Classic, zodat de voorinstellingen van de viewer worden bijgewerkt in de JCR. Om deze synch te verwezenlijken, vorm als volgt Dynamic Media Classic:

1. Open [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meld u vervolgens aan bij uw account.

1. Selecteer **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]** in de rechterbovenhoek van de pagina.
1. Selecteer **[!UICONTROL Image Serving]** in het vervolgkeuzemenu **[!UICONTROL Publish Context]** boven op de pagina Publiceren op de afbeeldingsserver.

1. Zoek op dezelfde pagina voor het publiceren van afbeeldingsservers de kop **[!UICONTROL Request Attributes]**.
1. Zoek onder de kop Aanvraagkenmerken **[!UICONTROL Reply Image Size Limit]**. Vergroot vervolgens in de bijbehorende velden Breedte en Hoogte de maximaal toegestane afbeeldingsgrootte voor panoramische afbeeldingen.

   Dynamic Media Classic heeft een limiet van 25.000.000 pixels. De maximaal toegestane grootte voor afbeeldingen met een hoogte-breedteverhouding van 2:1 is 7000 x 3500. Voor standaarddesktopschermen is 4096 x 2048 pixels echter voldoende.

   >[!NOTE]
   >
   >Alleen afbeeldingen die binnen de maximaal toegestane afbeeldingsgrootte vallen, worden ondersteund. Verzoeken om afbeeldingen die groter zijn dan de maximale grootte, leveren een reactie van 403 op.

1. Ga als volgt te werk onder Aanvraagkenmerken:

   * Stel de modus Vervaging verzoek in op **[!UICONTROL Disabled]**.
   * Stel de modus Verzoek vergrendelen in op **[!UICONTROL Disabled]**.

   Deze instellingen zijn nodig voor het gebruik van de WCM-component `Panoramic Media` in Experience Manager.

1. Selecteer **[!UICONTROL Save]** links onder aan de pagina Publiceren afbeeldingsserver.

1. Selecteer **[!UICONTROL Close]** in de rechterbenedenhoek.

### Problemen met de WCM-component Panoramische media oplossen {#troubleshooting-the-panoramic-media-wcm-component}

Als u een beeld in de component Panoramische Media in uw WCM en samengevouwen componentenplaceholder liet vallen, los het volgende problemen op:

* Als u een fout van 403 kent waarvoor een verbod geldt, kan deze worden veroorzaakt door het te grote formaat van de gevraagde afbeelding. Controleer de **[!UICONTROL Reply Image Size Limit]**-instellingen in [Dynamic Media Classic configureren](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene).

* Voor een &quot;Ongeldige vergrendeling&quot; op het element of &quot;Parseerfout&quot; die op de pagina wordt weergegeven, schakelt u de modus Verduistering aanvragen en de modus Vergrendelen aanvragen in om ervoor te zorgen dat deze zijn uitgeschakeld.
* Voor een bekroonde canvasfout, opstelling een Pad van het Dossier van de Definitie van de Regel plaatst en maakt CTN voor de vorige verzoeken om het beeldmiddel ongeldig.
* Als de afbeeldingskwaliteit laag wordt na een verzoek om een afbeelding waarvan de grootte groter is dan de ondersteunde limiet, controleert u of de instelling **[!UICONTROL JPEG Encoding Attributes > Quality]** niet leeg is. Een typische instelling voor het veld **[!UICONTROL Quality]** is `95`. U kunt het plaatsen op de de Publish pagina van de Server van het Beeld vinden. Zie [Dynamic Media Classic configureren](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene) voor toegang tot de pagina.

## Voorvertoning panorama-afbeeldingen {#previewing-panoramic-images}

Zie [Elementen voorvertonen](/help/assets/previewing-assets.md).

## Panorama-afbeeldingen publiceren {#publishing-panoramic-images}

Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md).
