---
title: 360/VR-video
description: Leer werken met en gebruik 360 en VR-video (Virtual Reality) in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: 360 VR Video
role: User, Admin
exl-id: 0c2077a7-bd16-484b-980f-4d4a1a681491
solution: Experience Manager, Experience Manager Assets
source-git-commit: beef1f49b7563d824357043f4ed78fdaf70015cd
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# 360/VR-video {#vr-video}

Bij video&#39;s van 360 graden wordt een weergave in elke richting tegelijkertijd vastgelegd. Ze worden opgenomen met een omnidirectionele camera of een verzameling camera&#39;s. Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; afspeelapparatuur op mobiele apparaten gebruikt doorgaans de ingebouwde gyroscopische besturingselementen.

De Dynamic Media-Scene7-modus biedt native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

In deze sectie wordt beschreven hoe u met de 360/VR Video-viewer werkt om equirechthoekige video te renderen voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap, medische procedure, enzovoort.

Ruimtelijke audio wordt momenteel niet ondersteund. Als audio in stereo wordt gemengd, verandert de balans (L/R) niet omdat de klant de kijkhoek van de camera wijzigt.

Zie ook [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md).

## 360 Video in actie {#video-in-action}

Selecteren [Ruimtestation 360](https://s7d1.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS) om een browservenster te openen en een video van 360 graden te bekijken. Tijdens het afspelen van video sleept u de muisaanwijzer naar een nieuwe locatie om de weergavehoek te wijzigen.

![360-videomonster met het internationale ruimtestation drijft in de ruimte en de aarde en de zon erachter.](assets/6_5_360videoiss_simplified.png)
*Videoframe vanaf Space Station 360*

## 360/VR-video en Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Met Adobe Premier Pro kunt u 360/VR-beeldmateriaal weergeven en bewerken. U kunt bijvoorbeeld logo&#39;s en tekst op de juiste wijze in een scène plaatsen en effecten en overgangen toepassen die specifiek zijn ontworpen voor rechthoekige media.

Zie [360/VR-video bewerken](https://helpx.adobe.com/premiere-pro/how-to/edit-360-vr-video.html).

## Elementen uploaden voor gebruik met de 360-videoviewer {#uploading-assets-for-use-with-the-video-viewer}

360 video-elementen die naar Adobe Experience Manager worden geüpload, worden aangeduid als **Multimedia** op een elementpagina, vergelijkbaar met normaal video-element.

![6_5_360video-selecttopreview](assets/6_5_360video-selecttopreview.png)
*Een geüpload 360-video element dat in de Kaartweergave wordt weergegeven. Het element wordt aangeduid als Multimedia.*

**Elementen uploaden voor gebruik met de 360 Video-viewer:**

1. Er is een map gemaakt voor uw 360-video-element.
1. [Pas een adaptief videoprofiel toe op de map](/help/assets/video-profiles.md#applying-a-video-profile-to-folders).

   Bij het renderen van 360-video-inhoud worden hogere eisen gesteld aan de resolutie van de bronvideo en aan de resolutie van gecodeerde vertoningen dan aan de standaard niet-360-video-inhoud.

   U kunt het adaptieve videoprofiel gebruiken dat al bij Dynamic Media wordt geleverd. De kwaliteit van 360-video is echter merkbaar lager dan bij niet-360-video die is gecodeerd met dezelfde instellingen die zijn gerenderd met een niet-360-videoviewer. Ga daarom als volgt te werk als u hoogwaardige 360 video nodig hebt:

   * In het ideale geval kunt u het beste een van de volgende resoluties toepassen op de oorspronkelijke 360-video-inhoud:

      * 1080p - 1920 x 1080, bekend als Full HD- of FHD-resolutie of,
      * 2160p - 3840 x 2160, bekend als 4k, UHD of Ultra HD-resolutie. Deze grote weergaveresolutie wordt meestal aangetroffen op hoogwaardige televisies en computermonitoren. De resolutie van 2160p wordt vaak &#39;4k&#39; genoemd omdat de breedte dichtbij 4000 pixels ligt. Met andere woorden, het biedt vier keer de pixels van 1080p.

   * [Een aangepast adaptief videoprofiel maken](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) met uitvoeringen van hogere kwaliteit. Maak bijvoorbeeld een adaptief videoprofiel met de volgende drie instellingen:

      * width=auto; height=720; bitrate=2500 kbps
      * width=auto; height=1080; bitrate=5000 kbps
      * width=auto; height=1440; bitrate=6600 kbps

   * Verwerk 360-video-inhoud in een map die exclusief is bestemd voor 360 video-elementen.

   Deze benadering plaatst grotere eisen op het netwerk en cpu van het eind - gebruiker.

1. [Uw video uploaden naar de map](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

## De standaardverhouding van 360 video&#39;s overschrijven  {#overriding-the-default-aspect-ratio-of-videos}

Als u een geüpload element wilt kwalificeren als een 360-video die u wilt gebruiken met de 360-videoviewer, moet het element een hoogte-breedteverhouding van 2 hebben.

Standaard detecteert Experience Manager video als &quot;360&quot; als de hoogte-breedteverhouding (breedte/hoogte) 2,0 is. Als u een beheerder bent, kunt u de standaardverhouding van 2 overschrijven door de optionele `s7video360AR` eigenschap in CRXDE Lite op het volgende:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

   * **Type eigenschap** - dubbel
   * **Waarde** - drijvende-kommaverhouding, standaard 2,0.

Nadat u deze eigenschap hebt ingesteld, wordt deze direct van kracht op zowel bestaande als nieuw geüploade video&#39;s.

De hoogte-breedteverhouding is van toepassing op 360 video-elementen voor de pagina met elementdetails en de pagina [Video 360 Media WCM-component](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

Begin met het uploaden van 360 video&#39;s.

## Voorvertoning 360-video {#previewing-video}

Met Voorvertoning kunt u zien hoe uw 360-video er uitziet voor klanten en kunt u controleren of deze goed functioneert.

Zie ook [Voorinstellingen voor viewers bewerken](/help/assets/managing-viewer-presets.md#editing-viewer-presets).

Als u tevreden bent met de 360-video, kunt u deze publiceren.

Zie [De video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md).
Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).

**Een voorvertoning van 360 video weergeven:**

1. In **[!UICONTROL Assets]** navigeer naar een bestaande 360-video die u hebt gemaakt. Selecteer het 360 Video-element zodat u het kunt openen in de voorvertoningsmodus.

   ![6_5_360video-selecttopreview-1](assets/6_5_360video-selecttopreview-1.png)

   Selecteer het 360-video-element zodat u een voorvertoning van de video kunt bekijken.

1. Selecteer op de voorvertoningspagina, linksboven op de pagina, de vervolgkeuzelijst en selecteer **[!UICONTROL Viewers]**.

   ![6_5_360video-voorvertoning-viewers](assets/6_5_360video-preview-viewers.png)

   Selecteer in de lijst Viewers de optie **[!UICONTROL Video360_social]** Voer vervolgens een van de volgende handelingen uit:

   * Sleep de muisaanwijzer over de video als u de kijkhoek van de statische scène wilt wijzigen.
   * Selecteer de video&#39;s **[!UICONTROL Play]** als u wilt beginnen met afspelen. Terwijl de video wordt afgespeeld, sleept u de muisaanwijzer over de video om de kijkhoek te wijzigen.

   ![Een screenshot van het internationale ruimtestation dat in de ruimte zweeft met de aarde en de zon op de achtergrond ](assets/6_5_360video-preview-video360-social.png)*Een schermafbeelding van 360 video.*

   * Selecteer in de lijst Viewers de optie **[!UICONTROL Video360VR]**.

     VR-video (Virtual Reality) is overweldigende video-inhoud die wordt benaderd met headsets van virtuele realiteit. Net als bij gewone video&#39;s maakt u aan het begin VR-video&#39;s wanneer een video wordt opgenomen of vastgelegd met videocamera&#39;s van 360 graden.

   ![Een schermafbeelding van een close-up van het internationale ruimtestation dat in de ruimte zweeft, waarbij de aarde en de zon gedeeltelijk op de achtergrond zichtbaar zijn](assets/6_5_360video-preview-video360vr.png)
   *Een videoschermafbeelding van 360 VR.*

1. Rechtsboven op de voorvertoningspagina selecteert u **[!UICONTROL Close]**.

## 360-video publiceren {#publishing-video}

Publiceer de 360-video zodat u deze kunt gebruiken. Wanneer u een 360-video publiceert, wordt de URL en de insluitcode geactiveerd. Het publiceert ook de 360 Video aan de wolk van Dynamic Media die met een CDN voor scalable en prestatieslevering geïntegreerd is.

Zie [Dynamic Media-elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van 360-video.
Zie ook [De video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md).
Zie ook [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie ook [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).
