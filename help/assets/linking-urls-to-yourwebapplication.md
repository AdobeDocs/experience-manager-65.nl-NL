---
title: URL's koppelen aan uw webtoepassing
description: URL's koppelen aan uw webtoepassing in Dynamic Media
uuid: cf599e66-b1f9-40c0-b572-cea19f2e6793
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d12e6ea3-aaf4-4672-9679-3c16c76d7d5b
role: User, Admin
exl-id: d62275f0-02a4-48c9-bfb1-e23d63b618c9
feature: Configuratie
source-git-commit: 77687a0674b939460bd34011ee1b94bd4db50ba4
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 4%

---

# URL&#39;s koppelen aan uw webtoepassing {#linking-urls-to-your-web-application}

Uw websites en toepassingen hebben via URL-oproepen toegang tot Dynamic Media-services. Nadat u een element hebt gepubliceerd, activeert Dynamic Media een URL-tekenreeks die verwijst naar het element. U kunt deze URL&#39;s voor testdoeleinden in een webbrowser plakken.

U verbindt met URLs slechts als u *niet* gebruikend Experience Manager als uw WCM bent. Koppelen - versus insluiten - wordt gebruikt wanneer u een videospeler wilt leveren als pop-up of modaal venster. Als u Experience Manager als uw WCM gebruikt, [voegt u de activa direct op uw pagina](adding-dynamic-media-assets-to-pages.md) toe.

Kopieer deze URL-tekenreeksen vanuit Dynamic Media om deze in uw webpagina&#39;s en toepassingen te plaatsen.

>[!NOTE]
>
>URL-tekenreeksen zijn alleen beschikbaar voor dynamische uitvoeringen van elementen. Ze zijn momenteel niet beschikbaar voor statische elementen die zich in DAM bevinden en niet voor de Dynamic Media-server. De knop URL wordt niet weergegeven voor vertoningen die statisch zijn.

Zie ook [De video- of afbeeldingsviewer insluiten op een webpagina](embed-code.md).

Zie ook [YouTube URLs van de Verbinding met uw Toepassing van het Web](video.md).

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
>Zie [Voorinstellingen van viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).
>
>Zie [Voorinstellingen voor afbeeldingen publiceren](managing-image-presets.md#publishing-image-presets).

Er zijn verschillende manieren waarop u een URL-tekenreeks kunt verkrijgen. In de onderstaande stappen ziet u echter slechts één methode die u kunt gebruiken.

**Een URL verkrijgen voor een element:**

1. Navigeer naar het *gepubliceerde*-element waarvan u de URL van de voorinstelling voor de afbeelding of de URL van de viewer met voorinstelling wilt kopiëren en selecteer het element om het te openen.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

   Zie [Voorinstellingen van viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).

   Zie [Voorinstellingen voor afbeeldingen publiceren](managing-image-presets.md#publishing-image-presets).

1. Voer op basis van het element dat u hebt geselecteerd een van de volgende handelingen uit:

   * Als u een afbeelding hebt geselecteerd, selecteert u **[!UICONTROL Renditions]** in het keuzemenu.

      Selecteer onder de kop **[!UICONTROL Dynamic]** een naam voor de voorinstelling om de vertoning ervan in het rechterframe weer te geven. Schuif zo nodig in de lijst Uitvoeringen om de dynamische kop weer te geven.

      Selecteer **[!UICONTROL URL]** onder aan het linkerspoor.

      ![chlimage_1-270](assets/chlimage_1-270.png)

   * Selecteer **[!UICONTROL Viewers]** als u een centrifugeset, een afbeeldingsset, een carrouselset of een video hebt geselecteerd in de vervolgkeuzelijst.

      Selecteer in het linkerspoor een naam voor de viewervoorinstelling. Er wordt een voorvertoning van de set of video geopend op een aparte pagina.

      Selecteer **[!UICONTROL URL]** in het linkerspoor onderaan.

      ![chlimage_1-271](assets/chlimage_1-271.png)

1. Selecteer en kopieer de tekst naar uw webbrowser, zodat u een voorvertoning van het element kunt bekijken of het aan uw webinhoudpagina kunt toevoegen.

   Als u het URL-venster wilt sluiten, selecteert u **[!UICONTROL X]** of **[!UICONTROL Close]**.

## Een URL verkrijgen voor een statisch element {#obtaining-a-url-for-a-static-asset}

Dynamic Media ondersteunt de levering van statische elementen. Dit zijn aanvullende elementen die verder gaan dan alleen afbeeldingen en video. Tot de ondersteunde indelingen voor statische elementen voor levering behoren:

* 3D-bestanden
* Geanimeerde GIF
* Audiobestanden
* CSS
* JavaScript (wanneer uw bedrijf met zijn eigen domein wordt gevormd)
* PDF
* SVG
* XML
* ZIP

**Een URL verkrijgen voor een statisch element:**

1. Navigeer naar het statische element *published* waarvan u de URL wilt kopiëren en selecteer het element om het te openen.

   Onthoud dat URL&#39;s alleen beschikbaar zijn om *after* te kopiëren. U hebt eerst *published* het statische element.

   Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

1. Gebruik een van de volgende methoden om de URL van het gepubliceerde statische element te verkrijgen:

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

         Bijvoorbeeld, `https://aem.com/is/content/adobe/image.gif`.
   * Selecteer **[!UICONTROL Asset]** > **[!UICONTROL Dynamic Renditions]**, dan selecteer een dynamische vertoning van het statische element en kopieer URL.

      Wijzig de gekopieerde URL om `is/content` in het pad te gebruiken in plaats van `is/image/`.


## Een video-URL verkrijgen voor een gepubliceerde video-uitvoering {#obtaining-a-video-url-for-a-published-video-rendition}

1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud]** > **[!UICONTROL Cloud Services]**.
1. Schuif op de pagina **[!UICONTROL Cloud Services]** omlaag naar de kop **[!UICONTROL Dynamic Media Cloud Services]** en selecteer **[!UICONTROL Show Configurations]**.
1. Selecteer onder **[!UICONTROL Available Configurations]** de naam van de gewenste configuratie.

1. Kopieer op de pagina **[!UICONTROL Dynamic Media Cloud Settings]** onder **[!UICONTROL Video Service URL]** het volledige URL-pad omlaag. U dient het gekopieerde URL-pad later in de stappen te gebruiken.

   Het URL-pad kan er bijvoorbeeld ongeveer als volgt uitzien:

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (Het bovenstaande pad is slechts een voorbeeld; het is niet het daadwerkelijke pad dat u kopieert.)

1. Kopieer onder **[!UICONTROL Registration ID]** de naam van de klant die u in het laatste gedeelte van de id vindt.

   Als de registratie-id bijvoorbeeld `87654321|MyCompany` was, zou de naam van de klant `MyCompany` zijn.

1. Selecteer **[!UICONTROL Cloud Services]** in de linkerbovenhoek van de pagina, selecteer vervolgens het logo van de Experience Manager en navigeer naar **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Kopieer het volledige pad voor video-uitvoering van de JCR (Java™ Content Repository) naar beneden.

   Het weergavepad van de video kan er bijvoorbeeld ongeveer als volgt uitzien:

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (Het bovenstaande pad is slechts een voorbeeld; het is niet het daadwerkelijke pad dat u kopieert.)

1. Plaats de gekopieerde gegevens in de volgende volgorde, zodat ze een volledig URL-pad vormen:

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Met de voorbeeldpaden en de voorbeeldnaam van de klant uit de bovenstaande stappen ziet het volledige pad er als volgt uit:

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Dit voorbeeld is de volledige video-URL voor een gepubliceerde video-uitvoering.

## Een video-URL ophalen voor adaptieve streaming (HLS) {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud]** > **[!UICONTROL Cloud Services]**.
1. Schuif op de pagina **[!UICONTROL Cloud Services]** omlaag naar de kop **[!UICONTROL Dynamic Media Cloud Services]** en selecteer **[!UICONTROL Show Configurations]**.
1. Selecteer onder **[!UICONTROL Available Configurations]** de naam van de gewenste configuratie.
1. Ga als volgt te werk op de pagina **[!UICONTROL Dynamic Media Cloud Services Settings]**:

   * Kopieer onder **[!UICONTROL Video Service URL]** het volledige URL-pad. U hebt het gekopieerde pad naar de URL later nodig in deze stappen. Het URL-pad kan er bijvoorbeeld ongeveer als volgt uitzien:

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (Het bovenstaande pad is slechts een voorbeeld; het is niet het daadwerkelijke pad dat u kopieert.)

   * Kopieer onder **[!UICONTROL Registration ID]** de naam van de klant die u in het laatste gedeelte van de id vindt. U hebt de gekopieerde klantennaam later in deze stappen nodig.

      Als de registratie-id bijvoorbeeld `87654321|demoCo` was, zou de naam die u kopieert `demoCo` zijn.


1. Kopieer de respectievelijke protocolkiezer op basis van het video-leveringsprotocol dat u gebruikt. U hebt de gekopieerde protocolkiezer later in deze stappen nodig.

   | Video-leveringsprotocol dat u gebruikt | Te gebruiken protocolkiezer |
   |---|---|
   | HTTP <br> Als u HTTP gebruikt (niet-veilige videolevering), zorg ervoor u https in http in de waarde verandert van de Videodienst URL u vroeger kopieerde. | `public/` |
   | HTTPS | `public-ssl/` |

1. Kopieer het volledige pad naar video-elementen in Experience Manager, zoals verwerkt door Dynamic Media. U hebt dit gekopieerde pad voor video-elementen later in deze stappen nodig.

   Bijvoorbeeld:

   `/content/dam/marketing/MyVideo.mp4`

1. Combineer alle onderdelen die u eerder hebt gekopieerd om een tekenreeks in de volgende volgorde te maken:

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Met de gekopieerde informatie uit de voorbeelden in deze stappen ziet de tekenreeks er bijvoorbeeld als volgt uit:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Voltooi de URL door `.m3u8` aan het einde van de tekenreeks toe te voegen. Als u bijvoorbeeld `.m3u8` toevoegt aan de tekenreeks uit de vorige stap, wordt het volledige URL-pad als volgt weergegeven:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Gebruik HTTP/2 om uw Dynamic Media-middelen te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-middelen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van Inhoud](http2.md) voor volledige informatie over het gaan gebruiken van HTTP/2 met uw Dynamic Media-account.
