---
title: 360/VR-video
description: Leer hoe u met 360 en VR-video (Virtual Reality) werkt in Dynamic Media.
uuid: c21bf2c0-7acc-401f-857e-0186de86e7a1
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: aac3c850-ae84-4bff-80de-d370e150f675
docset: aem65
feature: 360 VR-video
role: Business Practitioner, Administrator
exl-id: 0c2077a7-bd16-484b-980f-4d4a1a681491
source-git-commit: 663d7b886ba31521789b41002333715ce447e5ca
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%

---

# 360/VR-video {#vr-video}

Bij video&#39;s van 360 graden wordt een weergave in elke richting tegelijkertijd vastgelegd. Ze worden opgenomen met een omnidirectionele camera of een verzameling camera&#39;s. Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; Voor afspeelapparatuur op mobiele apparaten worden doorgaans de ingebouwde gyroscopische besturingselementen gebruikt.

De Dynamic Media-Scene7-modus biedt native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

In deze sectie wordt beschreven hoe u met de 360/VR Video-viewer werkt om equirechthoekige video te renderen voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap, medische procedure, enzovoort.

Ruimtelijke audio wordt momenteel niet ondersteund. als audio in stereo wordt gemengd, verandert de balans (L/R) niet aangezien de klant de kijkhoek van de camera verandert.

Zie ook [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

## 360 Video in actie {#video-in-action}

Tik [Ruimtestation 360](https://mobiletest.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS) om een browservenster te openen en een video van 360 graden te bekijken. Tijdens het afspelen van video sleept u de muisaanwijzer naar een nieuwe locatie om de weergavehoek te wijzigen.

![360 Video ](assets/6_5_360videoiss_simplified.png)
*sampleVideo frame van Space Station 360*

## 360/VR-video en Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Met Adobe Premier Pro kunt u 360/VR-beeldmateriaal weergeven en bewerken. U kunt bijvoorbeeld logo&#39;s en tekst op de juiste wijze in een scène plaatsen en effecten en overgangen toepassen die specifiek zijn ontworpen voor rechthoekige media.

Zie [360/VR-video bewerken](https://helpx.adobe.com/premiere-pro/how-to/edit-360-vr-video.html).

## Elementen uploaden voor gebruik met de 360-videoviewer {#uploading-assets-for-use-with-the-video-viewer}

360 video-elementen die naar Adobe Experience Manager worden geüpload, krijgen het label **Multimedia** op een elementpagina, vergelijkbaar met het normale video-element.

![6_5_360video-](assets/6_5_360video-selecttopreview.png)
*selectto previewEen geüploade 360 video-element in de kaartweergave. Het element is gelabeld als Multimedia.*

**Elementen uploaden voor gebruik met de 360 Video-viewer:**

1. Er is een map gemaakt voor uw 360-video-element.
1. [Pas een adaptief videoprofiel toe op de map](/help/assets/video-profiles.md#applying-a-video-profile-to-folders).

   Bij het renderen van 360 video-inhoud worden hogere eisen gesteld aan de resolutie van de bronvideo en aan de resolutie van gecodeerde vertoningen dan aan de standaard niet-360 video-inhoud.

   U kunt het adaptieve videoprofiel gebruiken dat al bij Dynamic Media wordt geleverd. Het resultaat is echter een merkbaar lagere videokwaliteit dan bij niet-360 video-gecodeerd met dezelfde instellingen die met een niet-360-videoviewer worden gerenderd. Ga daarom als volgt te werk als u hoogwaardige 360 video nodig hebt:

   * In het ideale geval heeft uw oorspronkelijke 360 video-inhoud het beste een van de volgende resoluties:

      * 1080p - 1920 x 1080, bekend als Full HD- of FHD-resolutie of,
      * 2160p - 3840 x 2160, bekend als 4k, UHD of Ultra HD-resolutie. Deze grote weergaveresolutie wordt meestal aangetroffen op hoogwaardige televisies en computermonitoren. De resolutie van 2160p wordt vaak &#39;4k&#39; genoemd omdat de breedte dichtbij 4000 pixels ligt. Met andere woorden, het biedt vier keer de pixels van 1080p.
   * [Maak een aangepast adaptief videoprofiel ](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) met uitvoeringen van hogere kwaliteit. Maak bijvoorbeeld een adaptief videoprofiel met de volgende drie instellingen:

      * width=auto; height=720; bitsnelheid=2500 kbps
      * width=auto; height=1080; bitsnelheid=5000 kbps
      * width=auto; height=1440; bitsnelheid=6600 kbps
   * Verwerk 360 video-inhoud in een map die exclusief is bestemd voor 360 video-elementen.

   Deze benadering plaatst grotere eisen op het netwerk en cpu van het eind - gebruiker.

1. [Upload uw video naar de map](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

## De standaardverhouding van 360 video&#39;s overschrijven  {#overriding-the-default-aspect-ratio-of-videos}

Als u een geüpload element wilt kwalificeren als een 360-video die u wilt gebruiken met de 360-videoviewer, moet het element een hoogte-breedteverhouding van 2 hebben.

Standaard detecteert Experience Manager video als &quot;360&quot; als de hoogte-breedteverhouding (breedte/hoogte) 2,0 is. Als u een Beheerder bent, kunt u het gebrek aspectverhouding plaatsen van 2 met voeten treden door het facultatieve `s7video360AR` bezit in CRXDE Lite bij het volgende te plaatsen:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

   * **Type**  eigenschap - dubbel
   * **Waarde**  - floating-point aspectverhouding, gebrek 2.0.

Nadat u deze eigenschap hebt ingesteld, wordt deze direct van kracht op zowel bestaande als nieuw geüploade video&#39;s.

De hoogte-breedteverhouding is van toepassing op 360 video-elementen voor de pagina met elementdetails en de [Video 360 Media WCM-component](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

Begin met het uploaden van 360 video&#39;s.

## Voorvertoning van 360 video {#previewing-video}

Met Voorvertoning kunt u zien hoe uw 360-video er uitziet voor klanten en kunt u controleren of deze zich gedraagt zoals u had verwacht.

Zie ook [Viewer-voorinstellingen bewerken](/help/assets/managing-viewer-presets.md#editing-viewer-presets).

Als u tevreden bent met de 360-video, kunt u deze publiceren.

Zie [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md).
Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.
Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).

**Een voorvertoning van 360 video&#39;s weergeven:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande 360-video die u hebt gemaakt. Tik op het 360 Video-element zodat u dit kunt openen in de voorvertoningsmodus.

   ![6_5_360video-selecttopreview-1](assets/6_5_360video-selecttopreview-1.png)

   Tik op het video-element 360 zodat u een voorvertoning van de video kunt bekijken.

1. Tik op de voorvertoningspagina linksboven op de pagina op de vervolgkeuzelijst en selecteer **[!UICONTROL Viewers]**.

   ![6_5_360video-voorvertoning-viewers](assets/6_5_360video-preview-viewers.png)

   Tik in de lijst Viewers op **[!UICONTROL Video360_social]** en voer een van de volgende handelingen uit:

   * Sleep de muisaanwijzer over de video als u de kijkhoek van de statische scène wilt wijzigen.
   * Tik op de knop **[!UICONTROL Play]** als u wilt beginnen met afspelen. Terwijl de video wordt afgespeeld, sleept u de muisaanwijzer over de video om de kijkhoek te wijzigen.

   ![6_5_360video-voorvertoning-video360-](assets/6_5_360video-preview-video360-social.png)*socialA 360 videoscreenshot.*

   * Tik in de lijst Viewers op **[!UICONTROL Video360VR]**.

      VR-video (Virtual Reality) is overweldigende video-inhoud die wordt benaderd met headsets van virtuele realiteit. Net als bij gewone video&#39;s maakt u aan het begin VR-video&#39;s wanneer een video wordt opgenomen of vastgelegd met videocamera&#39;s van 360 graden.
   ![6_5_360video-voorvertoning-video360vr](assets/6_5_360video-preview-video360vr.png)
   *Een videoschermafbeelding van 360 VR.*

1. Tik rechtsboven op de voorvertoningspagina op **[!UICONTROL Close]**.

## 360-video publiceren {#publishing-video}

Publiceer de 360-video zodat u deze kunt gebruiken. Wanneer u een 360-video publiceert, wordt de URL en de insluitcode geactiveerd. Het publiceert ook de 360 Video aan de wolk van Dynamic Media die met een CDN voor scalable en prestatieslevering geïntegreerd is.

Zie [Dynamic Media Assets publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van 360 Video.
Zie ook [Video of Afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md).
Zie ook [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.
Zie ook [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).
