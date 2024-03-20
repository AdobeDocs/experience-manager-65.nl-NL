---
title: URL's koppelen aan uw webtoepassing
description: URL's koppelen aan uw webtoepassing in Dynamic Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
exl-id: d62275f0-02a4-48c9-bfb1-e23d63b618c9
feature: Configuration
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 3%

---

# URL&#39;s koppelen aan uw webtoepassing {#linking-urls-to-your-web-application}

Uw websites en toepassingen hebben via URL-oproepen toegang tot Dynamic Media-services. Nadat u een element hebt gepubliceerd, activeert Dynamic Media een URL-tekenreeks die verwijst naar het element. U kunt deze URL&#39;s voor testdoeleinden in een webbrowser plakken.

U koppelt alleen aan URL&#39;s als u *niet* Experience Manager gebruiken als uw WCM. Koppelen - in plaats van insluiten - wordt gebruikt wanneer u een videospeler wilt leveren als pop-up of modaal venster. Als u Experience Manager als uw WCM gebruikt, [u voegt de elementen rechtstreeks op de pagina toe](adding-dynamic-media-assets-to-pages.md).

Kopieer deze URL-tekenreeksen vanuit Dynamic Media om deze in uw webpagina&#39;s en toepassingen te plaatsen.

>[!NOTE]
>
>URL-tekenreeksen zijn alleen beschikbaar voor dynamische uitvoeringen van elementen. Ze zijn momenteel niet beschikbaar voor statische elementen die zich in DAM bevinden en niet voor de Dynamic Media-server. De knop URL wordt niet weergegeven voor vertoningen die statisch zijn.

Zie ook [De video- of afbeeldingsviewer insluiten op een webpagina](embed-code.md).

Zie ook [YouTube-URL&#39;s koppelen aan uw webtoepassing](video.md).

Zie ook [Geoptimaliseerde afbeeldingen leveren voor een responsieve site](responsive-site.md).

Zie ook [Elementen uploaden](manage-assets.md#uploading-assets).

## Een URL verkrijgen voor een element {#obtaining-a-url-for-an-asset}

U kunt een URL-tekenreeks verkrijgen die wordt gegenereerd door een voorinstelling voor afbeeldingen of een voorinstelling voor de viewer. Nadat u de URL hebt gekopieerd, wordt de URL op het Klembord geland, zodat u deze desgewenst kunt plakken naar pagina&#39;s in uw website of toepassing.

>[!NOTE]
>
>De URL is pas beschikbaar voor kopiëren nadat u het geselecteerde element hebt gepubliceerd. Daarnaast moet u ook de voorinstelling van de viewer of de voorinstelling van de afbeelding publiceren.
>
>Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).
>
>Zie [Voorinstellingen viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).
>
>Zie [Voorinstellingen afbeelding publiceren](managing-image-presets.md#publishing-image-presets).

Er zijn verschillende manieren waarop u een URL-tekenreeks kunt verkrijgen. In de onderstaande stappen ziet u echter slechts één methode die u kunt gebruiken.

**Een URL verkrijgen voor een element:**

1. Ga naar de *gepubliceerd* -element waarvan u de URL van de voorinstelling voor de afbeelding of de URL van de viewer wilt kopiëren en het element wilt selecteren om het te openen.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

   Zie [Voorinstellingen viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).

   Zie [Voorinstellingen afbeelding publiceren](managing-image-presets.md#publishing-image-presets).

1. Voer op basis van het element dat u hebt geselecteerd een van de volgende handelingen uit:

   * Als u een afbeelding hebt geselecteerd, selecteert u in de vervolgkeuzelijst de optie **[!UICONTROL Renditions]**.

     Onder de **[!UICONTROL Dynamic]** Selecteer een naam voor de voorinstelling om de vertoning ervan in het rechterframe weer te geven. Schuif zo nodig in de lijst Uitvoeringen om de dynamische kop weer te geven.

     Selecteer onder aan het linkerspoor de optie **[!UICONTROL URL]**.

     ![chlimage_1-270](assets/chlimage_1-270.png)

   * Als u in het keuzemenu een centrifugeset, een afbeeldingsset, een carrouselset of een video hebt geselecteerd, selecteert u **[!UICONTROL Viewers]**.

     Selecteer in het linkerspoor een naam voor de viewervoorinstelling. Er wordt een voorvertoning van de set of video geopend op een aparte pagina.

     Selecteer in het linkerspoor, onderaan **[!UICONTROL URL]**.

     ![chlimage_1-271](assets/chlimage_1-271.png)

1. Selecteer en kopieer de tekst naar uw webbrowser, zodat u een voorvertoning van het element kunt bekijken of het aan uw webinhoudpagina kunt toevoegen.

   Als u het URL-venster wilt sluiten, selecteert u de optie **[!UICONTROL X]** of selecteer **[!UICONTROL Close]**.

## Een URL verkrijgen voor een statisch element {#obtaining-a-url-for-a-static-asset}

Dynamic Media ondersteunt de levering van statische elementen. Dit zijn aanvullende elementen die verder gaan dan alleen afbeeldingen en video. Tot de ondersteunde indelingen voor statische elementen voor levering behoren:

* 3D-bestanden
* Geanimeerd GIF
* Audiobestanden
* CSS
* JavaScript (wanneer uw bedrijf met zijn eigen domein wordt gevormd)
* PDF
* SVG
* XML
* ZIP

**Een URL verkrijgen voor een statisch element:**

1. Ga naar de *gepubliceerd* statisch element waarvan u de URL wilt kopiëren en selecteer het element om het te openen.

   Onthoud dat URL&#39;s alleen beschikbaar zijn om te kopiëren *na* u hebt de eerste *gepubliceerd* het statische element.

   Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

1. Gebruik een van de volgende methoden om de URL van het gepubliceerde statische element te verkrijgen:

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

        Bijvoorbeeld: `https://aem.com/is/content/adobe/image.gif`.

   * Selecteren **[!UICONTROL Asset]** > **[!UICONTROL Dynamic Renditions]** selecteert u vervolgens een dynamische vertoning van het statische element en kopieert u de URL.

     De gekopieerde URL wijzigen in gebruik `is/content` in plaats van `is/image/`.

## Een video-URL opvragen voor een gepubliceerde video-uitvoering {#obtaining-a-video-url-for-a-published-video-rendition}

1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud]** > **[!UICONTROL Cloud Services]**.
1. Op de **[!UICONTROL Cloud Services]** pagina, omlaag naar de **[!UICONTROL Dynamic Media Cloud Services]** kop selecteert u vervolgens **[!UICONTROL Show Configurations]**.
1. Onder **[!UICONTROL Available Configurations]** selecteert u de naam van de gewenste configuratie.

1. Op de **[!UICONTROL Dynamic Media Cloud Settings]** pagina, onder **[!UICONTROL Video Service URL]**, kopieert u het volledige URL-pad omlaag. U dient het gekopieerde URL-pad later in de stappen te gebruiken.

   Het URL-pad kan er bijvoorbeeld ongeveer als volgt uitzien:

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (Het bovenstaande pad is alleen een voorbeeld; het is niet het pad dat u daadwerkelijk kopieert.)

1. Kopieer onder **[!UICONTROL Registration ID]** de naam van de klant die u in het laatste gedeelte van de id vindt.

   Als de registratie-id bijvoorbeeld `87654321|MyCompany`, de naam van de klant `MyCompany`.

1. Selecteer in de linkerbovenhoek van de pagina de optie **[!UICONTROL Cloud Services]** selecteert u vervolgens het logo van de Experience Manager en navigeert u naar **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Kopieer het volledige pad voor video-uitvoering van de JCR (Java™ Content Repository) naar beneden.

   Het weergavepad van de video kan er bijvoorbeeld ongeveer als volgt uitzien:

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (Het bovenstaande pad is alleen een voorbeeld; het is niet het pad dat u daadwerkelijk kopieert.)

1. Plaats de gekopieerde gegevens in de volgende volgorde, zodat ze een volledig URL-pad vormen:

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Met de voorbeeldpaden en de voorbeeldnaam van de klant uit de bovenstaande stappen ziet het volledige pad er als volgt uit:

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Dit voorbeeld is de volledige video-URL voor een gepubliceerde video-uitvoering.

## Een video-URL verkrijgen voor adaptieve bitsnelheidstreaming (DASH of HLS) {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud]** > **[!UICONTROL Cloud Services]**.
1. Op de **[!UICONTROL Cloud Services]** pagina, omlaag naar de **[!UICONTROL Dynamic Media Cloud Services]** kop selecteert u vervolgens **[!UICONTROL Show Configurations]**.
1. Onder **[!UICONTROL Available Configurations]** selecteert u de naam van de gewenste configuratie.
1. Op de **[!UICONTROL Dynamic Media Cloud Services Settings]** pagina, ga als volgt te werk:

   * Onder **[!UICONTROL Video Service URL]**, kopieert u het volledige URL-pad. U hebt het gekopieerde URL-pad later in deze stappen nodig. Het URL-pad kan er bijvoorbeeld ongeveer als volgt uitzien:

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (Het bovenstaande pad is alleen een voorbeeld; het is niet het pad dat u daadwerkelijk kopieert.)

   * Onder **[!UICONTROL Registration ID]**, kopieert u de naam van de klant in het laatste gedeelte van de id. U hebt de gekopieerde klantennaam later in deze stappen nodig.

     Als de registratie-id bijvoorbeeld `87654321|demoCo`, de naam die u kopieert `demoCo`.

1. Kopieer de respectievelijke protocolkiezer op basis van het video-leveringsprotocol dat u gebruikt. U hebt de gekopieerde protocolkiezer later in deze stappen nodig.

   | Video-leveringsprotocol dat u gebruikt | Te gebruiken protocolkiezer |
   |---|---|
   | HTTP <br> Als u HTTP gebruikt (niet-veilige video levering), zeker ben u https in HTTP in de waarde van de VideoDienst URL verandert u vroeger kopieerde. | `public/` |
   | HTTPS | `public-ssl/` |

1. Kopieer het volledige pad naar video-elementen in Experience Manager, zoals verwerkt door Dynamic Media. U hebt dit gekopieerde pad voor video-elementen later in deze stappen nodig.

   Bijvoorbeeld:

   `/content/dam/marketing/MyVideo.mp4`

1. Combineer alle onderdelen die u eerder hebt gekopieerd om een tekenreeks in de volgende volgorde te maken:

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Met de gekopieerde informatie uit de voorbeelden in deze stappen ziet de tekenreeks er bijvoorbeeld als volgt uit:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Voltooi de URL door deze toe te voegen `.m3u8` tot het einde van de tekenreeks. Bijvoorbeeld, toevoegen `.m3u8` naar de tekenreeks van de vorige stap wordt het volledige URL-pad als volgt weergegeven:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Gebruik HTTP/2 om uw Dynamic Media-middelen te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-middelen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van inhoud](http2.md) voor volledige informatie over hoe u aan de slag gaat met HTTP/2 met uw Dynamic Media-account.
