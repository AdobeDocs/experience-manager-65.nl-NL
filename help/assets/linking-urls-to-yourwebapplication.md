---
title: URL's koppelen aan uw webapplicatie
description: URL's koppelen aan uw webtoepassing in dynamische media
uuid: cf599e66-b1f9-40c0-b572-cea19f2e6793
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d12e6ea3-aaf4-4672-9679-3c16c76d7d5b
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 9%

---


# URL&#39;s koppelen aan uw webapplicatie {#linking-urls-to-your-web-application}

Via URL-aanroepen hebben uw websites en toepassingen toegang tot Dynamic Media-services. Nadat u een element hebt gepubliceerd, activeert Dynamic Media een URL-tekenreeks die verwijst naar het element. U kunt deze URL&#39;s voor testdoeleinden in een webbrowser plakken.

U koppelt alleen aan URL&#39;s als u *geen* AEM gebruikt als uw WCM. Linking-versus insluiten-wordt gebruikt wanneer u een videospeler als pop-up of modaal venster wilt leveren. Als u AEM gebruikt als uw WCM, voegt [u de elementen rechtstreeks op uw pagina toe.](adding-dynamic-media-assets-to-pages.md)

Als u deze URL-tekenreeksen wilt plaatsen in uw webpagina&#39;s en toepassingen, kopieert u ze van Dynamic Media.

>[!NOTE]
>
>URL-tekenreeksen zijn alleen beschikbaar voor dynamische uitvoeringen van elementen. Ze zijn momenteel niet beschikbaar voor statische elementen die zich in DAM bevinden en niet voor de dynamische mediaserver. De knop URL wordt niet weergegeven voor vertoningen die statisch zijn.

See also [Embedding the Video or Image Viewer on a Web Page.](embed-code.md)

Zie ook URL&#39;s [koppelen aan uw webtoepassing.](video.md)

See also [Delivering Optimized Images for a Responsive Site.](responsive-site.md)

Zie ook Elementen [uploaden.](managing-assets-touch-ui.md#uploading-assets)

## Een URL ophalen voor een element {#obtaining-a-url-for-an-asset}

U kunt een URL-tekenreeks verkrijgen die wordt gegenereerd door een voorinstelling voor afbeeldingen of een voorinstelling voor de viewer. Nadat u de URL hebt gekopieerd, wordt de URL op het Klembord geplaatst, zodat u deze desgewenst kunt plakken naar de pagina&#39;s van uw website of toepassing.

>[!NOTE]
>
>De URL is pas beschikbaar voor kopiëren nadat u het geselecteerde element hebt gepubliceerd. Daarnaast moet u ook de voorinstelling van de viewer of de voorinstelling van de afbeelding publiceren.
>
>Zie Elementen [](publishing-dynamicmedia-assets.md)publiceren.
>
>Zie Voorinstellingen [voor](managing-viewer-presets.md#publishing-viewer-presets)viewers publiceren.
>
>Zie [Voorinstellingen](managing-image-presets.md#publishing-image-presets)afbeelding publiceren.

Er zijn verschillende manieren waarop u een URL-tekenreeks kunt verkrijgen. In de onderstaande stappen ziet u echter slechts één methode die u kunt gebruiken.

**Een URL verkrijgen voor een element**

1. Navigeer naar het *gepubliceerde* element waarvan u de URL met voorinstellingen voor afbeeldingen of de URL met voorinstellingen voor viewers wilt kopiëren en tik op het element om het te openen.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie Elementen [publiceren.](publishing-dynamicmedia-assets.md)

   Zie Voorinstellingen [voor](managing-viewer-presets.md#publishing-viewer-presets)viewers publiceren.

   Zie [Voorinstellingen](managing-image-presets.md#publishing-image-presets)afbeelding publiceren.

1. Voer op basis van het element dat u hebt geselecteerd een van de volgende handelingen uit:

   * Als u een afbeelding hebt geselecteerd, tikt u in de vervolgkeuzelijst op **[!UICONTROL Renditions.]**

      Tik onder de **[!UICONTROL Dynamic]** kop op de naam van een voorinstelling om de vertoning ervan in het rechterframe weer te geven. Mogelijk moet u door de lijst met uitvoeringen bladeren om de dynamische kop te zien.

      Tik onder aan de linkerspoorstaaf op **[!UICONTROL URL.]**

      ![chlimage_1-270](assets/chlimage_1-270.png)

   * Als u in het keuzemenu een centrifugeset, een afbeeldingenset, een carrouselset of een video hebt geselecteerd, tikt u op **[!UICONTROL Viewers.]**

      Tik in de linkertrack op de naam van een viewervoorinstelling. Er wordt een voorvertoning van de set of video geopend op een aparte pagina.

      Tik in de linkerspoorstaaf onderaan **[!UICONTROL URL.]**

      ![chlimage_1-271](assets/chlimage_1-271.png)

1. Selecteer en kopieer de tekst naar uw webbrowser om een voorvertoning van het element weer te geven of om deze toe te voegen aan uw pagina met webinhoud.

   Tik op het URL-venster **[!UICONTROL X]** of tik op **[!UICONTROL Close.]**

## Een URL verkrijgen voor een statisch element {#obtaining-a-url-for-a-static-asset}

Dynamische media ondersteunt de levering van statische elementen. Dit zijn aanvullende elementen die verder gaan dan alleen afbeeldingen en video. Tot de ondersteunde indelingen voor statische elementen voor levering behoren:

* 3D-bestanden
* Geanimeerde GIF
* Audiobestanden
* CSS
* JavaScript (wanneer uw bedrijf met zijn eigen domein wordt gevormd)
* PDF
* SVG
* XML
* ZIP

**Een URL verkrijgen voor een statisch element**

1. Navigeer naar het *gepubliceerde* statische element waarvan u de URL wilt kopiëren en tik op het element om het te openen.

   Remember that URLs are only available to copy *after* you have first *published* the static asset.

   Zie Elementen [](publishing-dynamicmedia-assets.md)publiceren.

1. Gebruik een van de volgende methoden om de URL van het gepubliceerde statische element te verkrijgen:

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

         Bijvoorbeeld, `https://aem.com/is/content/adobe/image.gif`.
   * Tik **[!UICONTROL Asset > Dynamic Renditions]** vervolgens op een dynamische uitvoering van het statische element en kopieer de URL.

      Wijzig de gekopieerde URL in plaats van de URL die u `is/content` in het pad wilt gebruiken `is/image/`.


## Een video-URL ophalen voor een gepubliceerde video-uitvoering {#obtaining-a-video-url-for-a-published-video-rendition}

1. Navigeer in AEM naar **[!UICONTROL Tools > Deployment > Cloud > Cloud Services.]**
1. Schuif op de pagina **[!UICONTROL Cloud Services]** omlaag naar de kop **[!UICONTROL Dynamic Media Cloud Services]** en tik op **[!UICONTROL Show Configurations.]**
1. Tik onder **[!UICONTROL Available Configurations]** op de naam van de gewenste configuratie.

1. Kopieer op de **[!UICONTROL Dynamic Media Cloud Settings]** pagina onder **[!UICONTROL Video Service URL]** het volledige URL-pad naar beneden. U hebt het gekopieerde URL-pad later nodig in de stappen.

   Het URL-pad kan er bijvoorbeeld ongeveer als volgt uitzien:

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (Bovenstaand pad dient slechts ter illustratie; het is niet het daadwerkelijke pad dat u kopieert.)

1. Kopieer onder **[!UICONTROL Registration ID]** de naam van de klant die u in het laatste gedeelte van de id vindt.

   Als de registratie-id bijvoorbeeld `87654321|MyCompany`is, is de naam van de klant `MyCompany`.

1. Tik in de linkerbovenhoek van de pagina **[!UICONTROL Cloud Services]** op het logo van de Experience Manager en navigeer naar **[!UICONTROL General > CRXDE Lite.]**
1. Kopieer het volledige pad voor video-uitvoering vanuit de JCR (Java Content Repository).

   Het weergavepad van de video kan er bijvoorbeeld ongeveer als volgt uitzien:

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (Bovenstaand pad dient slechts ter illustratie; het is niet het daadwerkelijke pad dat u kopieert.)

1. Plaats de gekopieerde gegevens in de volgende volgorde om een volledig URL-pad te vormen:

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Met de voorbeeldpaden en de voorbeeldnaam van de klant uit de bovenstaande stappen ziet het volledige pad er als volgt uit:

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Dit is de volledige video-URL voor een gepubliceerde video-uitvoering.

## Een video-URL ophalen voor adaptieve streaming (HLS) {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. Navigeer in AEM naar **[!UICONTROL Tools > Deployment > Cloud > Cloud Services.]**
1. Schuif op de pagina **[!UICONTROL Cloud Services]** omlaag naar de kop **[!UICONTROL Dynamic Media Cloud Services]** en tik op **[!UICONTROL Show Configurations.]**
1. Tik onder **[!UICONTROL Available Configurations]** op de naam van de gewenste configuratie.
1. Ga als volgt te werk op de **[!UICONTROL Dynamic Media Cloud Services Settings]** pagina:

   * Kopieer onder **[!UICONTROL Video Service URL]** het volledige URL-pad. U hebt het gekopieerde URL-pad later in deze stappen nodig. Het URL-pad kan er bijvoorbeeld ongeveer als volgt uitzien:

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (Bovenstaand pad dient slechts ter illustratie; het is niet het daadwerkelijke pad dat u kopieert.)

   * Kopieer onder **[!UICONTROL Registration ID]** de naam van de klant die u in het laatste gedeelte van de id vindt. U zult de gekopieerde klantnaam later in deze stappen nodig hebben.

      Als de registratie-id bijvoorbeeld `87654321|demoCo`is, is de naam van de klant die u kopieert, `demoCo`.


1. Kopieer de respectievelijke protocolkiezer op basis van het video-leveringsprotocol dat u gebruikt. U hebt de gekopieerde protocolkiezer later in deze stappen nodig.

   | Video-leveringsprotocol dat u gebruikt | Te gebruiken protocolkiezer |
   |---|---|
   | HTTP <br> Als u HTTP gebruikt (niet-veilige video levering), zorg ervoor u https in de waarde van de VideoDienst URL verandert u vroeger kopieerde. | `public/` |
   | HTTPS | `public-ssl/` |

1. Kopieer het volledige pad naar het video-element in AEM, zoals dit wordt verwerkt door Dynamic Media. U hebt dit gekopieerde pad naar video-elementen later in deze stappen nodig.

   Bijvoorbeeld:

   `/content/dam/marketing/MyVideo.mp4`

1. Combineer alle onderdelen die u eerder hebt gekopieerd om een tekenreeks in de volgende volgorde te maken:

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Met de gekopieerde informatie uit de voorbeelden in deze stappen ziet de tekenreeks er bijvoorbeeld als volgt uit:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Voltooi de URL door deze aan het einde van `.m3u8` de tekenreeks toe te voegen. Als u bijvoorbeeld de tekenreeks toevoegt uit de vorige stap, ziet het volledige URL-pad er als volgt uit: `.m3u8`

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Het gebruiken van HTTP/2 om uw Dynamische activa van Media te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van dynamische media-elementen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van Inhoud](http2.md) voor volledige details over begonnen worden het gebruiken van HTTP/2 met uw Dynamische rekening van Media.
