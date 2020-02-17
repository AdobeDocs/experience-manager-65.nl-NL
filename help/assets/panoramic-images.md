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
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Panoramische afbeeldingen{#panoramic-images}

In deze sectie wordt beschreven hoe u met de Panorama-viewer werkt om bolvormige panoramische afbeeldingen te renderen voor een indrukwekkende kijkervaring van 360 graden van een kamer, eigenschap, locatie of landschap.

Zie ook Voorinstellingen [voor viewers](/help/assets/managing-viewer-presets.md)beheren.

![panoramic-image2](assets/panoramic-image2.png)

## Elementen uploaden voor gebruik met de Panorama-viewer {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Als u een geüpload element wilt kwalificeren als een bolvormige panorama-afbeelding die u wilt gebruiken met de Panorama-viewer, moet het element een van de volgende opties of beide hebben:

* Een hoogte-breedteverhouding van 2.
U kunt de standaardverhouding van 2 in CRXDE Lite bij het volgende met voeten treden:
   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Gelabeld met de trefwoorden `equirectangular`, of `spherical`en `panorama`, of `spherical` en `panoramic`. Zie [Tags](/help/sites-authoring/tags.md)gebruiken.

Zowel zijn de aspectverhouding als de sleutelwoordcriteria op panoramische activa voor de pagina van activa detailleert en de component `Panoramic Media` WCM van toepassing.

Zie [Elementen](/help/assets/managing-assets-touch-ui.md#uploading-assets)uploaden voor gebruik met de Panorama-viewer.

## Het vormen van Dynamische Klassieke Media (Scene7) {#configuring-dynamic-media-classic-scene}

De Panoramische beeldkijker werkt behoorlijk binnen AEM, moet u vooraf instelt van de Kijker van het Beeld Panoramische met Dynamische Media Klassieke (Scene7) en Dynamische Media Klassieke (Scene7) - specifieke meta-gegevens synchroniseren zodat wordt de kijker vooraf instelt bijgewerkt in JCR. Om dit te verwezenlijken, vorm Dynamische Klassieke Media (Scene7) op de volgende manier:

1. [Logboek in uw geval van Dynamische Media Klassiek (Scene7)](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) voor elke bedrijfrekening.

1. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**.
1. Voor de Publish pagina van de Server van het Beeld, van het **[!UICONTROL Publish drop-down menu dichtbij de bovenkant, uitgezochte]** Beeld Serving ****.

1. Voor de zelfde pagina van de Publicatie van de Server van het Beeld, bepaal de plaats van de rubriek **[!UICONTROL verzoekAttributen]**.
1. Zoek onder de kop Kenmerken aanvragen de optie Limiet voor afbeeldingsgrootte **[!UICONTROL beantwoorden]**. Vergroot vervolgens in de bijbehorende velden Breedte en Hoogte de maximaal toegestane afbeeldingsgrootte voor panoramische afbeeldingen.

   Dynamic Media Classic (Scene7) heeft een limiet van 25.000.000 pixels. De maximaal toegestane grootte voor afbeeldingen met een hoogte-breedteverhouding van 2:1 is 7000 x 3500. Voor standaarddesktopschermen is 4096 x 2048 pixels echter voldoende.

   >[!NOTE]
   >
   >Alleen afbeeldingen die binnen de maximaal toegestane afbeeldingsgrootte vallen, worden ondersteund. Verzoeken om afbeeldingen die groter zijn dan de maximale grootte, leveren een reactie van 403 op.

1. Ga als volgt te werk onder Aanvraagkenmerken:

   * Stel de modus Vervaging aanvragen in op **[!UICONTROL Uitgeschakeld]**.
   * Vergrendelingsmodus voor aanvragen instellen op **[!UICONTROL Uitgeschakeld]**.
   Deze instellingen zijn nodig voor het gebruik van de `Panoramic Media` WCM-component in AEM.

1. Klik links onder aan de pagina Publiceren afbeeldingsserver op **[!UICONTROL Opslaan]**.

1. Klik in de rechterbenedenhoek op **[!UICONTROL Sluiten]**.

### Problemen met de WCM-component Panoramische media oplossen {#troubleshooting-the-panoramic-media-wcm-component}

Als u een beeld in de component Panoramische Media in uw WCM en samengevouwen componentenplaceholder liet vallen, kunt u het volgende willen problemen oplossen:

* Als u een fout van 403 kent waarvoor een verbod geldt, kan deze zijn veroorzaakt door het te grote formaat van de gevraagde afbeelding. Herzie de montages van de Grens **[!UICONTROL van de Grootte van het Beeld van het Antwoord in het]** Vormen van Dynamische Klassieke Media (Scene7) [](/help/assets/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

* Voor een &quot;Ongeldige vergrendeling&quot; op het element of &quot;Parseerfout&quot; die op de pagina wordt weergegeven, schakelt u de modus Verduistering aanvragen en de modus Vergrendelen aanvragen in om ervoor te zorgen dat deze zijn uitgeschakeld.
* Voor een bekroonde canvasfout, opstelling een Pad van het Dossier van de Definitie van de Regel en maakt CTN voor de vorige verzoeken om het beeldmiddel ongeldig.
* Als de afbeeldingskwaliteit na een afbeeldingsaanvraag met een formaat groter dan de ondersteunde limiet erg laag wordt, controleert u of de instelling **[!UICONTROL JPEG-coderingskenmerken > Kwaliteit]** niet leeg is. Een standaardinstelling voor het veld **[!UICONTROL Kwaliteit]** is `95`. U kunt het plaatsen op de de Publish pagina van de Server van het Beeld vinden. Om tot de pagina toegang te hebben, zie het [Vormen Dynamische Klassieke Media (Scene7)](/help/assets/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

## Voorvertoning panorama-afbeeldingen weergeven {#previewing-panoramic-images}

Zie [Voorvertoning van elementen](/help/assets/previewing-assets.md)weergeven.

## Panorama-afbeeldingen publiceren {#publishing-panoramic-images}

Zie Elementen [](/help/assets/publishing-dynamicmedia-assets.md)publiceren.
