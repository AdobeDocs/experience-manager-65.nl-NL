---
title: Video in dynamische media
description: Leer hoe u met video werkt in dynamische media, zoals aanbevolen werkwijzen voor het coderen van video's, het toevoegen van meerdere audio- en bijschrifttracks aan video's en videominiaturen.
mini-toc-levels: 3
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: Asset Management
role: User, Admin
exl-id: 28cf9e39-cab4-4278-b6c9-e84cc31964db
solution: Experience Manager, Experience Manager Assets
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '10333'
ht-degree: 1%

---

# Video in dynamische media {#video}

In deze sectie wordt het werken met video in Dynamic Media beschreven.

## Snel starten: Video&#39;s {#quick-start-videos}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met Adaptive Video Sets in Dynamic Media. Na elke stap, zijn er verwijzingen naar onderwerprubrieken waar u meer informatie kunt vinden.

>[!IMPORTANT]
>
>Zorg ervoor dat uw Adobe Experience Manager-beheerder Dynamic Media Cloud Services heeft ingeschakeld en geconfigureerd in de modus Dynamische media - Scene7 of Hybride voordat u werkt met video in Dynamic Media.
>
>* Zie [&#x200B; Dynamische Diensten van de Wolk van Media vormen &#x200B;](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) in het Vormen van Dynamische Media - wijze Scene7 en [&#x200B; Los Dynamische Media problemen op - wijze Scene7 &#x200B;](/help/assets/troubleshoot-dms7.md).
>
>* Zie [&#x200B; Dynamische Diensten van de Wolk van Media vormen &#x200B;](/help/assets/config-dynamic.md#configuring-dynamic-media-cloud-services) in het Vormen van Dynamische Media - Hybride wijze.
>
>Huidige bekende videoplaybackkwestie in Dynamische Media *op Experience Manager 6.5.9.0 slechts*:
>
>* Als een gepubliceerde video wordt bijgewerkt, moet deze opnieuw worden gepubliceerd om wijzigingen in de levering te weerspiegelen.
>

1. **upload uw Dynamische video&#39;s van Media** door het volgende te doen:

   * Maak uw eigen videocoderingsprofiel. Of, kunt u het vooraf bepaalde _Aangepaste Video Coderen_ profiel eenvoudig gebruiken dat met Dynamische Media komt.

      * [&#x200B; creeer een video het coderen profiel &#x200B;](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * De maximale resolutie voor videocodering van de uitvoer is 8,192 × 4,320 of 4,320 × 8,192,md.
      * Leer meer over [&#x200B; Beste praktijken voor video het coderen &#x200B;](#best-practices-for-encoding-videos).

   * Koppel het videoverwerkingsprofiel aan een of meer mappen waar u de primaire bronvideo&#39;s gaat uploaden.

      * [&#x200B; pas een videoprofiel op omslagen &#x200B;](/help/assets/video-profiles.md#applying-a-video-profile-to-folders) toe.
      * Leer meer over [&#x200B; Beste praktijken voor het organiseren van uw digitale activa voor het gebruiken van verwerkingsprofielen &#x200B;](/help/assets/organize-assets.md).
      * Leer meer over [&#x200B; Organiseer digitale activa &#x200B;](/help/assets/organize-assets.md).

   * Upload uw primaire bronvideo&#39;s naar de mappen. Wanneer u video&#39;s aan de map toevoegt, worden deze gecodeerd volgens het videoverwerkingsprofiel dat u aan de map hebt toegewezen.

      * Dynamische media ondersteunt voornamelijk korte video&#39;s met een maximale lengte van 30 minuten en een minimale resolutie van meer dan 25 × 25.
      * De maximale ondersteunde invoervideoresolutie is 16,384 × 16,384.
      * U kunt videobestanden uploaden van maximaal 15 GB elk.
      * [&#x200B; upload uw video&#39;s &#x200B;](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).
      * Leer meer over [&#x200B; Ondersteunde formaten van het inputdossier &#x200B;](/help/assets/assets-formats.md#supported-multimedia-formats).

   * Monitor hoe [&#x200B; video het coderen &#x200B;](#monitoring-video-encoding-and-youtube-publishing-progress) of van de activa of werkschemamening vooruitgaat.

1. **beheer uw Dynamische video&#39;s van Media** door om het even welke volgend te doen:

   * Video-elementen organiseren, doorbladeren en zoeken

      * [&#x200B; Organiseer digitale activa &#x200B;](/help/assets/organize-assets.md)
Leer meer over [&#x200B; Beste praktijken voor het organiseren van uw digitale activa voor het gebruiken van verwerkingsprofielen &#x200B;](organize-assets.md)

      * [&#x200B; videoactiva van het Onderzoek &#x200B;](search-assets.md#custompredicates) of [&#x200B; activa van het Onderzoek &#x200B;](/help/assets/search-assets.md)

   * Video-elementen voorvertonen en publiceren

      * Bekijk de bronvideo en de gecodeerde vertoningen van de video samen met de bijbehorende miniaturen:
        [&#x200B; de video&#39;s van de Voorproef &#x200B;](managing-video-assets.md#upload-and-preview-video-assets) of [&#x200B; activa van de Voorproef &#x200B;](previewing-assets.md)
        [&#x200B; de videovertoningen van de Mening &#x200B;](video-renditions.md)
        [&#x200B; beheer videovertoningen &#x200B;](manage-assets.md#managing-renditions)

      * [Voorinstellingen voor viewers beheren](managing-viewer-presets.md)
      * [Elementen publiceren](publishing-dynamicmedia-assets.md)

   * Werken met videometagegevens

      * Bekijk de eigenschappen van een gecodeerde video-uitvoering, zoals framesnelheid, audio- en videobitsnelheid en codec:
        [&#x200B; de eigenschappen van de videovertoning van de Mening &#x200B;](video-renditions.md)

      * Bewerk de eigenschappen van video, zoals de titel, beschrijving en tags, aangepaste metagegevensvelden:
        [&#x200B; geef videoeigenschappen &#x200B;](manage-assets.md#editing-properties) uit

      * [Metagegevens voor digitale elementen beheren](metadata.md)
      * [Metagegevensschema&#39;s](metadata-schemas.md)

   * Video&#39;s bekijken, goedkeuren en annoteren en volledige versiebeheer behouden

      * [&#x200B; Annoteer video&#39;s &#x200B;](managing-video-assets.md#annotate-video-assets) of [&#x200B; activa &#x200B;](manage-assets.md#annotating) annoteren

      * [Een versie maken](manage-assets.md#asset-versioning)
      * [&#x200B; pas werkschema&#39;s op activa &#x200B;](assets-workflow.md) toe of zie [&#x200B; Begin een werkschema op een activa &#x200B;](manage-assets.md#starting-a-workflow-on-an-asset)

      * [Mapmiddelen controleren](bulk-approval.md)
      * [Projecten](../sites-authoring/projects.md)

1. **publiceer uw Dynamische video&#39;s van Media** door één van het volgende te doen:

   * Als u Adobe Experience Manager gebruikt als beheersysteem voor webinhoud, kunt u video&#39;s rechtstreeks aan uw webpagina&#39;s toevoegen.

      * [&#x200B; voegt video&#39;s aan uw Web-pagina&#39;s &#x200B;](adding-dynamic-media-assets-to-pages.md) toe.

   * Als u een systeem voor webcontentbeheer van derden gebruikt, kunt u video&#39;s koppelen aan of insluiten in uw webpagina&#39;s.

      * Video integreren met URL:
        [&#x200B; Verbinding URLs aan uw Webtoepassing &#x200B;](linking-urls-to-yourwebapplication.md).

      * Video integreren met behulp van ingesloten code op een webpagina:
        [&#x200B; bedt de videokijker op een Web-pagina &#x200B;](embed-code.md) in.

   * [&#x200B; produceer videorapporten &#x200B;](#viewing-video-reports).

   * [&#x200B; voegt titels aan de video &#x200B;](#adding-captions-to-video) toe.

## Werken met video in dynamische media {#working-with-video-in-dynamic-media}

Video in Dynamic Media is een end-to-end oplossing die het gemakkelijk maakt om adaptieve video van hoge kwaliteit te publiceren voor streaming op meerdere schermen, waaronder desktopcomputers, iOS, Android™, BlackBerry® en mobiele Windows-apparaten. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. De desktopcomputer of het mobiele apparaat detecteert de beschikbare bandbreedte.

Op een mobiel iOS-apparaat wordt bijvoorbeeld een bandbreedte gedetecteerd, zoals 3G, 4G of Wi-Fi. Vervolgens wordt automatisch de naar rechts gecodeerde video geselecteerd bij de verschillende bitsnelheden van de video in de adaptieve videoset. De video wordt gestreamd naar desktops, mobiele apparaten of tablets.

Bovendien wordt de videokwaliteit automatisch dynamisch geschakeld als de netwerkomstandigheden veranderen op het bureaublad of op het mobiele apparaat. Als een klant de modus Volledig scherm op een desktopcomputer inschakelt, reageert de Adaptive Video Set met een betere resolutie, waardoor de kijkervaring van de klant wordt verbeterd. Adaptieve videosets zorgen voor een optimale weergave voor klanten die Dynamic Media-video op meerdere schermen en apparaten bekijken.

De logica die een videospeler gebruikt om te bepalen welke gecodeerde video moet worden afgespeeld of tijdens het afspelen moet worden geselecteerd, is gebaseerd op het volgende algoritme:

1. De videospeler laadt het eerste videofragment op basis van de bitsnelheid die het dichtst bij de waarde ligt die voor de beginbitsnelheid is ingesteld in de speler zelf.
1. De videospelerschakelaars die op veranderingen in de bandbreedtesnelheid worden gebaseerd die de volgende criteria gebruiken:

   1. De speler kiest de hoogste bandbreedtestroom onder of gelijk aan de geschatte bandbreedte.
   1. De speler overweegt slechts 80% van de beschikbare bandbreedte. Als er echter een overstap wordt gemaakt, is het conservatiever bij slechts 70% om overschatting te voorkomen en onmiddellijk terug te keren.

Voor gedetailleerde technische informatie over het algoritme, zie [&#x200B; https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp &#x200B;](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Voor het beheren van afzonderlijke video- en adaptieve videosets wordt het volgende ondersteund:

* Upload video&#39;s in verschillende ondersteunde indelingen en codeer ze naar MP4 H.264, zodat ze op meerdere schermen kunnen worden afgespeeld. U kunt vooraf gedefinieerde adaptieve videovoorinstellingen gebruiken, voorinstellingen voor één videocodering gebruiken of uw eigen codering aanpassen om de kwaliteit en de grootte van de video te bepalen.

   * Wanneer een adaptieve videoset wordt gegenereerd, bevat deze MP4-video&#39;s.
   * **Nota**: De primaire/bronvideo&#39;s worden niet toegevoegd aan een Aangepaste VideoReeks.

* ondertiteling in alle HTML5-videoviewers.
* Video organiseren, doorbladeren en doorzoeken met volledige metagegevensondersteuning voor een efficiënt beheer van video-elementen.
* Lever Adaptieve videosets naar het web en naar desktops en mobiele apparaten, zoals de iPhone, iPad, Android™, BlackBerry® en Windows-telefoon.

Adaptieve videostreaming wordt ondersteund op verschillende iOS-platforms. Zie {de Gids van de Verwijzing van de Kijkers van 0} Dynamische Media [.](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference#video)

Dynamische media ondersteunt het afspelen van mobiele video voor MP4 H.264-video. <!-- LINK IS 404 WITH NO SUITABLE REPLACEMENT You can find BlackBerry&reg; devices that support this video format at the following: [Supported video formats on BlackBerry&reg;](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482). -->

U kunt de apparaten vinden van Vensters die dit videoformaat bij het volgende steunen: [&#x200B; Gesteunde media codecs voor Telefoon 8 van Vensters &#x200B;](https://learn.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs)

* Speel de video terug gebruikend Dynamische Media VideoKijker vooraf instelt, met inbegrip van het volgende:

   * Enkele videoviewers.
   * Gemengde Media-viewers die zowel video- als afbeeldingsinhoud combineren.

* Configureer videospelers om aan uw brandingbehoeften te voldoen.
* Video met een eenvoudige URL of insluitcode integreren in uw website, mobiele site of mobiele toepassing.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480) sample. -->

Zie ook [&#x200B; Kijkers voor Experience Manager Assets en Dynamic Media Classic &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers#viewers-aem-assets-dmc) en [&#x200B; Kijkers voor slechts de activa van Experience Manager &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers#viewers-for-aem-assets-only).

## Tips en trucs: De HTML5-videoviewer gebruiken {#best-practice-using-the-html-video-viewer}

Dynamische media HTML5-voorinstellingen voor videoviewers zijn robuuste videospelers. U kunt ze gebruiken om veel voorkomende problemen te voorkomen die samenhangen met het afspelen van HTML5-video. En problemen met mobiele apparaten, zoals een gebrek aan adaptieve streaminglevering met bitsnelheid en een beperkt bereik van de desktopbrowser.

Aan de ontwerpkant van de speler, kunt u de functionaliteit van de videospeler ontwerpen gebruikend standaardWeb ontwikkelingshulpmiddelen. U kunt bijvoorbeeld de knoppen, besturingselementen en de achtergrond van een aangepaste posterafbeelding ontwerpen met HTML5 en CSS om u te helpen uw klanten te bereiken met een aangepaste weergave.

Aan de afspeelzijde van de viewer wordt automatisch de videocapaciteit van de browser gedetecteerd. Vervolgens wordt de video weergegeven met HLS (Live HTTP-streaming) of DASH (Dynamic Adaptive Streaming via HTTP), ook wel adaptieve bitsnelheidstreaming genoemd. Of als deze leveringsmethoden niet aanwezig zijn, wordt in plaats daarvan HTML5 progressief gebruikt.

Door het volgende te combineren in één speler:

* De mogelijkheid om de afspeelcomponenten te ontwerpen met HTML5 en CSS
* Ingesloten afspelen hebben
* Adaptieve en progressieve streaming gebruiken, afhankelijk van de browsermogelijkheden

U vergroot het bereik van uw rijke media-inhoud tot zowel desktopgebruikers als mobiele gebruikers en zorgt voor een gestroomlijnde videobeleving.

Zie ook [&#x200B; Ongeveer Kijkers HTML5 &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers#viewers-for-aem-assets-only).

### Video afspelen op bureaubladcomputers en mobiele apparaten met de HTML5-videoviewer {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Voor adaptieve videostreaming op het bureaublad en mobiele apparaten zijn de video&#39;s die worden gebruikt voor het schakelen naar een andere bitsnelheid, gebaseerd op alle MP4-video&#39;s in de adaptieve videoset.

Het afspelen van video vindt plaats met behulp van DASH of HLS of via progressief downloaden van video. In eerdere versies van Experience Manager, zoals 6.0, 6.1 en 6.2, werden video&#39;s gestreamd via HTTP.

In Experience Manager 6.3 en hoger worden video&#39;s nu gestreamd via HTTPS (DASH of HLS) omdat de URL van de DM-gatewayservice altijd HTTPS gebruikt. Dit standaardgedrag heeft geen gevolgen voor de klant. Videostreaming vindt altijd plaats via HTTPS, behalve wanneer de browser dit niet ondersteunt. (Zie de volgende tabel). Daarom

* Als u een HTTPS-website met HTTPS-videostreaming hebt, is streaming prima.
* Als u een HTTP-website met HTTPS-videostreaming hebt, is streaming prima en zijn er geen problemen met gemengde inhoud in de webbrowser.

DASH is de internationale standaard en HLS is een Apple-standaard. Beide worden gebruikt voor adaptieve videostreaming. En, passen beide technologieën automatisch playback aan die op de capaciteit van de netwerkbandbreedte wordt gebaseerd. Het laat de klant ook &quot;zoeken&quot;aan om het even welk punt in de video zonder de behoefte om op de rest van de video te wachten te downloaden.

Progressieve video wordt geleverd door de video lokaal te downloaden en op het desktopsysteem of mobiele apparaat van de gebruiker op te slaan.

In de volgende tabel worden het apparaat, de browser en de afspeelmethode beschreven van video&#39;s op bureaubladcomputers en mobiele apparaten met de Dynamic Media-videoviewer.

<table>
 <tbody>
  <tr>
   <td><strong>Apparaat</strong></td>
   <td><strong>Browser</strong></td>
   <td><strong>Video-afspeelmodus</strong></td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Internet Explorer 9 en 10</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Internet Explorer 11+</td>
   <td>In Windows 8 en Windows 10 - Gebruik HTTPS wanneer DASH* of HLS wordt aangevraagd, forceren. Bekende beperking: HTTP op DASH* of HLS werkt niet in deze combinatie browser/besturingssysteem <br /> <br /> In Windows 7 - Progressief downloaden. Gebruikt de standaardlogica voor het selecteren van het protocol HTTP versus HTTPS.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 23-44</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 45 of hoger</td>
   <td>Adaptieve bitsnelheidstreaming van DASH* of HLS.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Chrome</td>
   <td>Adaptieve bitsnelheidstreaming van DASH* of HLS.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Safari (Mac)</td>
   <td>Adaptieve bitsnelheidstreaming van HLS.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 6 of eerder)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 7 of hoger)</td>
   <td>Adaptieve bitsnelheidstreaming van DASH* of HLS.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Android™ (standaardbrowser)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Safari (iOS)</td>
   <td>Adaptieve bitsnelheidstreaming van HLS.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (iOS)</td>
   <td>Adaptieve bitsnelheidstreaming van HLS.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>BlackBerry®</td>
   <td>Adaptieve bitsnelheidstreaming van DASH* of HLS./td&gt;
  </tr>
 </tbody>
</table>

## Architectuur van Dynamic Media-video-oplossing {#architecture-of-dynamic-media-video-solution}

In de volgende afbeelding ziet u de algemene ontwerpworkflow voor video&#39;s die via de DMGateway (in de modus Dynamische media hybride) zijn geüpload en gecodeerd en voor openbare consumptie beschikbaar zijn.

![&#x200B; Architectuur van Dynamische de videooplossing van Media.](assets/chlimage_1-427.png)

## Hybride publicatiearchitectuur voor video&#39;s {#hybrid-publishing-architecture-for-videos}

![&#x200B; Hybride het publiceren architectuur voor video&#39;s.](assets/chlimage_1-428.png)

## Aanbevolen werkwijzen voor het coderen van video&#39;s {#best-practices-for-encoding-videos}

De **Dynamische Media codeert Video** werkschema codeert video als u Dynamische Media en de diensten van de opstellingsvideowolk hebt toegelaten. In deze workflow worden de historie en informatie over fouten van het workflowproces vastgelegd. Als u Dynamic Media hebt ingeschakeld en cloudservices voor video hebt ingesteld, wordt de **[!UICONTROL Dynamic Media Encode Video]** -workflow automatisch van kracht wanneer u een video uploadt. (Als u geen gebruik maakt van Dynamische media, wordt de **[!UICONTROL DAM Update Asset]** -workflow van kracht.)

<!-- DEAD The following are best-practice tips for encoding source video files.

For advice about video encoding, see [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en).

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en). -->

### Source-videobestanden {#source-video-files}

Wanneer u een videobestand codeert, gebruikt u een videobronbestand van de hoogst mogelijke kwaliteit. Gebruik geen eerder gecodeerde videobestanden omdat deze bestanden al zijn gecomprimeerd en als u verder codeert, wordt een video van subparkwaliteit gemaakt.

* Dynamische media ondersteunt voornamelijk korte video&#39;s met een maximale lengte van 30 minuten en een minimale resolutie van meer dan 25 × 25.
* U kunt primaire bronvideobestanden uploaden die elk maximaal 15 GB bedragen.

In de volgende tabel worden de aanbevolen grootte, hoogte-breedteverhouding en minimale bitsnelheid beschreven die uw bronvideobestanden moeten hebben voordat u ze codeert:

| Grootte | Hoogte-breedteverhouding | Minimale bitsnelheid |
|--- |--- |--- |
| 1024 × 768 | 4:3 | 4500 kbps voor de meeste video&#39;s. |
| 1280 × 720 | 16 :9 | 3000 - 6000 kbps, afhankelijk van de hoeveelheid beweging in de video. |
| 1920 × 1080 | 16 :9 | 6000 - 8000 kbps, afhankelijk van de mate van beweging in de video. |

### De metagegevens van een bestand verkrijgen {#obtaining-a-file-s-metadata}

U kunt de metagegevens van een bestand verkrijgen door de metagegevens van het bestand te bekijken met een programma voor videobewerking of met een toepassing die is ontworpen voor het verkrijgen van metagegevens. Hieronder vindt u instructies voor het gebruik van MediaInfo, een toepassing van derden, voor het verkrijgen van de metagegevens van een videobestand:

1. Ga naar [&#x200B; Download MediaInfo &#x200B;](https://mediaarea.net/en/MediaInfo/Download).
1. Selecteer en download het installatieprogramma voor de GUI-versie en volg de installatie-instructies.
1. Klik na de installatie met de rechtermuisknop op het videobestand (alleen Windows) en selecteer MediaInfo, of open MediaInfo en sleep het videobestand naar de toepassing. U ziet alle metagegevens die aan het videobestand zijn gekoppeld, inclusief de breedte, hoogte en fps.

### Hoogte-breedteverhouding {#aspect-ratio}

Wanneer u een voorinstelling voor videocodering selecteert of maakt voor uw primaire videobestand, moet u ervoor zorgen dat de hoogte-breedteverhouding van de voorinstelling overeenkomt met die van het primaire videobestand. De hoogte-breedteverhouding is de verhouding tussen de breedte en de hoogte van de video.

Als u de hoogte-breedteverhouding van een videobestand wilt bepalen, vraagt u de metagegevens van het bestand op en noteert u de breedte en hoogte van het bestand. Zie De metagegevens van een bestand hierboven verkrijgen. Gebruik vervolgens deze formule om de hoogte-breedteverhouding te bepalen:

width/height = hoogte-breedteverhouding

In de volgende tabel wordt beschreven hoe de resultaten van de formule worden omgezet in algemene opties voor de hoogte-breedteverhouding:

| Formulerresultaat | Hoogte-breedteverhouding |
|--- |--- |
| 1,33 | 4:3 |
| 0,75 | 3 :4 |
| 1,78 | 16 :9 |
| 0,56 | 9 :16 |

Een video van 1440 bij 1080 heeft bijvoorbeeld een hoogte-breedteverhouding van 1440/1080 of 1,33. In dit geval kiest u een voorinstelling voor videocodering met een hoogte-breedteverhouding van 4 :3 om het videobestand te coderen.

### Bitsnelheid {#bitrate}

Een bitsnelheid is de hoeveelheid gegevens die is gecodeerd om één seconde te vertegenwoordigen bij het afspelen van video. De bitsnelheid wordt gemeten in kilobits per seconde (Kbps).

>[!NOTE]
>
>Omdat in alle codecs compressie met verlies wordt gebruikt, is bitsnelheid de belangrijkste factor voor de videokwaliteit. Bij compressie met verlies neemt de kwaliteit af naarmate u een videobestand comprimeert. Daarom zijn alle andere eigenschappen gelijk (de resolutie, framesnelheid en codec), hoe lager de bitsnelheid, hoe lager de kwaliteit van het gecomprimeerde bestand.

Wanneer u een codering voor bitsnelheden selecteert, kunt u kiezen uit twee typen:

* **[!UICONTROL Constant Bitrate Encoding]** (CBR) - Tijdens CBR-codering blijft de bitsnelheid of het aantal bits per seconde tijdens het coderingsproces ongewijzigd. Bij CBR-codering blijft de gegevenssnelheid van de set behouden voor de instelling van de gehele video. Bij CBR-codering worden mediabestanden niet geoptimaliseerd voor kwaliteit, maar wordt opslagruimte bespaard.
Gebruik CBR als uw video een vergelijkbaar bewegingsniveau in de gehele video bevat. CBR wordt meestal gebruikt voor het streamen van video-inhoud. Zie ook [&#x200B; douane-toegevoegde videocoderingsparameters van het Gebruik &#x200B;](/help/assets/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Variable Bitrate Encoding]** (VBR) - VBR-codering past de gegevenssnelheid naar beneden en naar de bovenste limiet die u instelt, aan op basis van de gegevens die de compressor nodig heeft. Deze functionaliteit houdt in dat de bitsnelheid van het mediabestand tijdens een VBR-coderingsproces dynamisch wordt verhoogd of verlaagd, afhankelijk van de bitsnelheidbehoeften van het mediabestand.
VBR duurt langer om te coderen, maar geeft de meest gunstige resultaten. De kwaliteit van het mediabestand is superieur. VBR wordt het meest meestal gebruikt voor http progressieve levering van video-inhoud.

Wanneer gebruikt u VBR versus CRB?
Als u VBR en CBR selecteert, wordt het bijna altijd aanbevolen VBR te gebruiken voor uw mediabestanden. VBR biedt bestanden van hogere kwaliteit tegen concurrerende bitsnelheden. Wanneer u VBR gebruikt, moet u ervoor zorgen dat u met codering met twee controles gebruikt en de maximale bitsnelheid instellen op 1,5x de bitsnelheid van de doelvideo.

Wanneer u een voorinstelling voor videocodering kiest, moet u rekening houden met de verbindingssnelheid van de eindgebruiker. Kies een voorinstelling met een gegevenssnelheid van 80 procent van die snelheid. Als de verbindingssnelheid van de eindgebruiker van het doel bijvoorbeeld 1000 Kbps is, is de beste voorinstelling een snelheid met een videogegevenssnelheid van 800 Kbps.

In deze tabel wordt de gegevenssnelheid beschreven van standaardverbindingssnelheden.

| Snelheid (Kbps) | Verbindingstype |
|--- |--- |
| 256 | Inbelverbinding. |
| 800 | Normale mobiele verbinding. Kies hiervoor een gegevenssnelheid tussen 400 en maximaal 800 voor 3G-ervaringen. |
| 2000 | Standaardbreedbandverbinding voor desktops. Voor deze verbinding, richt een gegevenstarief in de waaier 800-2000 Kbps, met de meeste doelstellingen gemiddeld 1200-1500 Kbps. |
| 5000 | Typische breedbandverbinding. Codering in dit bovenste bereik wordt niet aanbevolen, omdat de video bij deze snelheid niet beschikbaar is voor de meeste consumenten. |

### Resolutie {#resolution}

**Resolutie** beschrijft de hoogte en de breedte van een videodossier in pixel. De meeste bronvideo wordt opgeslagen met een hoge resolutie (bijvoorbeeld 1920 × 1080). Voor streamingdoeleinden wordt bronvideo gecomprimeerd tot een lagere resolutie (640 × 480 of lager).

Resolutie en gegevenssnelheid zijn twee geïntegreerde gekoppelde factoren die de videokwaliteit bepalen. Als u dezelfde videokwaliteit wilt behouden, geldt dat hoe hoger het aantal pixels in een videobestand (hoe hoger de resolutie), hoe hoger de gegevenssnelheid. Neem bijvoorbeeld het aantal pixels per frame in een videobestand met een resolutie van 320 × 240 en een resolutie van 640 × 480:

| Resolutie | Pixels per frame |
|--- |--- |
| 320 × 240 | 76.800 |
| 640 × 480 | 307.200 |

Het bestand van 640 × 480 heeft vier keer meer pixels per frame. Als u voor deze twee voorbeeldresoluties dezelfde gegevenssnelheid wilt bereiken, past u viermaal de compressie toe op het bestand van 640 × 480, waardoor de kwaliteit van de video afneemt. Een videogegevenssnelheid van 250 Kbps resulteert daarom in beelden van hoge kwaliteit bij een resolutie van 320 × 240, maar niet bij een resolutie van 640 × 480.

Over het algemeen geldt dat hoe hoger de gegevenssnelheid, hoe beter de video er uitziet en hoe hoger de resolutie die u gebruikt, hoe hoger de gegevenssnelheid waarmee u de weergavekwaliteit wilt behouden (in vergelijking met lagere resoluties).

Omdat de resolutie en de gegevenssnelheid zijn gekoppeld, hebt u twee opties bij het coderen van video:

* Kies een gegevenssnelheid en codeer vervolgens met de hoogste resolutie die er goed uitziet in de gekozen gegevenssnelheid.
* Kies een resolutie en codeer met de gegevenssnelheid die nodig is voor video van hoge kwaliteit met de gekozen resolutie.

Wanneer u een voorinstelling voor videocodering kiest (of maakt) voor uw primaire bronvideobestand, gebruikt u deze tabel om de juiste resolutie in te stellen:

| Resolutie | Hoogte (pixels) | Schermgrootte |
|--- |--- |--- |
| 240p | 240 | Glanzend scherm |
| 300p | 300 | Klein scherm, meestal voor mobiele apparaten |
| 360p | 360 | Klein scherm |
| 480p | 480 | Medium-scherm |
| 720p | 720 | Groot scherm |
| 1080p | 1080 | High-definition groot scherm |

De maximale ondersteunde invoervideoresolutie is 16,384 × 16,384. De maximale resolutie voor videocodering van de uitvoer is 8,192 × 4,320 of 4,320 × 8,192.

### FPS (frames per seconde) {#fps-frames-per-second}

In de Verenigde Staten en Japan worden de meeste video&#39;s opgenomen met een snelheid van 29,97 frames per seconde (fps). In Europa is de norm 25 fps. Film wordt echter doorgaans genomen bij 24 fps.

Kies een voorinstelling voor videocodering die overeenkomt met de fps-snelheid van het primaire bronvideobestand. Als uw primaire bronvideo bijvoorbeeld 25 fps is, kiest u een coderingsvoorinstelling met 25 fps. Standaard wordt bij alle aangepaste codering de fps van het primaire bronvideobestand gebruikt. Daarom hoeft u de fps-instelling niet expliciet op te geven wanneer u een voorinstelling voor videocodering maakt.

### Afmetingen videocodering {#video-encoding-dimensions}

Voor optimale resultaten selecteert u de coderingsafmetingen, zodat de bronvideo een volledig veelvoud van alle gecodeerde video&#39;s is.

Als u deze verhouding wilt berekenen, deelt u de bronbreedte door de gecodeerde breedte om de breedteverhouding op te halen. Vervolgens deelt u de bronhoogte door de gecodeerde hoogte om de hoogte-breedteverhouding te bepalen.

Als de resulterende verhouding een geheel geheel getal is, betekent dit dat de video optimaal wordt geschaald. Als de resulterende verhouding geen geheel geheel getal is, is dit van invloed op de videokwaliteit doordat pixelartefacten overblijven op het scherm. Dit effect is vooral opvallend wanneer de video tekst heeft.

Stel dat uw bronvideo bijvoorbeeld 1920 × 1080 is. In de volgende tabel bieden de drie gecodeerde video&#39;s de optimale coderingsinstellingen.

| Videotype | Breedte × Hoogte | Breedteverhouding | Hoogteverhouding |
|--- |--- |--- |--- |
| Source | 1920 × 1080 | 1 | 1 |
| Gecodeerd | 960 × 540 | 2 | 2 |
| Gecodeerd | 640 × 360 | 3 | 3 |
| Gecodeerd | 480 × 270 | 4 | 4 |

### Gecodeerde videobestandsindeling {#encoded-video-file-format}

Dynamische media raadt u aan voorinstellingen voor MP4 H.264-videocodering te gebruiken. Omdat MP4-bestanden de H.264-videocodec gebruiken, biedt deze video van hoge kwaliteit, maar met een gecomprimeerde bestandsgrootte.

## Videorapporten weergeven {#viewing-video-reports}

>[!NOTE]
>
>Videorapporten zijn alleen beschikbaar wanneer u Dynamische media - hybride modus uitvoert.

De videoRapporten tonen verscheidene gezamenlijke metriek over een gespecificeerde tijd om u te helpen controleren dat *gepubliceerde* individuele en gezamenlijke video&#39;s zoals verwacht presteren. De volgende statistische gegevens worden geaggregeerd voor alle gepubliceerde video&#39;s op uw gehele website:

* Video start
* Voltooiingssnelheid
* Gemiddelde tijd op video
* Totale tijd op video
* Video&#39;s per bezoek

Een lijst van alle *gepubliceerde* video&#39;s is ook vermeld zodat kunt u de hoogste bekeken video&#39;s op uw website volgen die op totale videobegin wordt gebaseerd.

Wanneer u een videonaam in de lijst selecteert, wordt het rapport voor het vasthouden van het publiek van de video (drop-off) weergegeven in de vorm van een lijndiagram. Het diagram toont het aantal weergaven voor een bepaald tijdstip tijdens het afspelen van video. Wanneer u de video afspeelt, wordt de verticale balk gesynchroniseerd met de tijdindicator in de speler. De vallen in de gegevens van het lijndiagram wijzen op waar uw publiek van oninteresse wegvalt.

Als de video buiten Adobe Experience Manager Dynamic Media is gecodeerd, zijn het diagram voor het vasthouden van het publiek (drop-off) en de gegevens voor het afspeelpercentage in de tabel niet beschikbaar.

Zie ook [&#x200B; de Dynamische Diensten van de Wolk van Media vormen &#x200B;](/help/assets/config-dynamic.md).

>[!NOTE]
>
>Het bijhouden en rapporteren van gegevens is uitsluitend gebaseerd op het gebruik van de eigen videospeler van Dynamic Media en de bijbehorende voorinstelling van de videospeler. Daarom kunt u geen video&#39;s bijhouden en rapporteren die via andere videospelers worden afgespeeld.

Door gebrek, de eerste keer u VideoRapporten ingaat, toont het rapport videogegevens die bij de eerste van de huidige maand beginnen en met de datum van de huidige maand beëindigen. U kunt het standaarddatumbereik echter overschrijven door uw eigen datumbereik op te geven. De volgende keer dat u Video-rapporten invoert, wordt het opgegeven datumbereik gebruikt.

Videorapporten werken alleen correct als er automatisch een rapportsuite-id wordt gemaakt wanneer Dynamic Media Cloud Services is geconfigureerd. Tegelijkertijd wordt de rapportsuite-id doorgegeven aan de publicatieserver, zodat deze beschikbaar is voor de functie URL kopiëren wanneer u een voorvertoning van elementen weergeeft. Voor deze functionaliteit is echter wel vereist dat de publicatieserver al is ingesteld. Als de publicatieserver niet is ingesteld, kunt u toch publiceren om het videoverslag te zien. U moet echter terugkeren naar de Dynamic Media Cloud Configuration en **[!UICONTROL OK]** selecteren.

**aan meningsvideorapporten:**

1. Selecteer in de linkerbovenhoek van Experience Manager het Experience Manager-logo en klik vervolgens in de linkertrack op **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Video Reports]** .
1. Voer een van de volgende handelingen uit op de pagina Videorapporten:

   * Vlak de hoger-juiste hoek, selecteer **verfrissen Videopictogram van het Rapport**.
Gebruik alleen Vernieuwen als de einddatum van het rapport de huidige dag is. Dit zorgt ervoor dat u de video het volgen ziet die sinds de laatste tijd is voorgekomen u het rapport in werking stelde.

   * Vlak de hoger-juiste hoek, selecteer het **pictogram van de Plukker van 0&rbrace; Datum &lbrace;.**
Geef het begin- en einddatumbereik op waarvoor u videogegevens wilt en selecteer vervolgens **[!UICONTROL Run Report]** .

   De Hoogste de groepsdoos van Metriek identificeert diverse gezamenlijke metingen voor alle *gepubliceerde* video&#39;s over uw plaats.

1. Selecteer in de tabel met de bovenste gepubliceerde video&#39;s een videonaam om de video af te spelen en zie ook het rapport voor het vasthouden van het publiek van de video (drop-off).

### Video-rapporten weergeven op basis van een videoviewer die u hebt gemaakt met de Dynamic Media HTML5 Viewer SDK {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Als u een uit-van-doos videoviewer gebruikt die door Dynamische Media wordt verstrekt, of als u een vooraf ingestelde douaneviewer creeerde die op een uit-van-doos videokijker wordt gebaseerd, dan worden geen extra stappen vereist om VideoRapporten te bekijken. Als u echter uw eigen videoviewer hebt gemaakt op basis van de HTML5 Viewer SDK API, voert u de volgende stappen uit om ervoor te zorgen dat uw videoviewer traceergebeurtenissen verzendt naar Dynamic Media Video-rapporten.

Gebruik de [&#x200B; Gids van de Verwijzing van de Kijkers van de Media van Adobe Dynamische &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources) en [&#x200B; SDK API van de Kijker HTML5 &#x200B;](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) om uw eigen videokijkers tot stand te brengen.

**aan meningsvideorapporten die op een videokijker worden gebaseerd die u gebruikend de Dynamische Kijker HTML5 van Media SDK creeerde:**

1. Navigeer naar een gepubliceerd video-element.
1. Selecteer in de vervolgkeuzelijst in de linkerbovenhoek van de assetpagina de optie **[!UICONTROL Viewers]**.
1. Selecteer een voorinstelling voor een videoviewer en kopieer de insluitcode.
1. Zoek in de insluitcode de regel met het volgende:

   `videoViewer.setParam("config2", "<value>");`

   De parameter `config2` schakelt tracering in HTML5 Viewers in. Het is ook een bedrijf-specifieke vooraf ingesteld die de configuratieinformatie voor Video die, en voor klant-specifieke configuraties van Adobe Analytics bevat meldt.

   De juiste waarde voor de config2-parameter wordt gevonden in zowel de functie **[!UICONTROL Embed Code]** als de functie copy **[!UICONTROL URL]** . In de URL van de opdracht copy **[!UICONTROL URL]** is de parameter die moet worden gezocht `&config2=<value>` . De waarde is bijna altijd `companypreset`, maar in sommige gevallen ook `companypreset-1`, `companypreset-2`, enz.

1. Voeg in uw aangepaste videoviewercode AppMeasurementBridge .jsp als volgt toe aan de viewerpagina:

   * Bepaal eerst of u de parameter `&preset` nodig hebt.

     Als de `config2` parameter `companypreset` is, hebt u ** niet nodig `&preset=parameter`.

     Als `config2` iets anders is, stelt u de parameter preset in op dezelfde waarde als de parameter `config2` . Voeg bijvoorbeeld `config2=companypreset-2` , indien `&param2=companypreset-2` , toe aan de URL AppMeasurmentBridge.jsp.

   * Voeg vervolgens het script AppMeasurementBridge.jsp toe:

     `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Maak als volgt de component TrackingManager:

   * Nadat u `s7sdk.Util.init();` hebt aangeroepen, maakt u een instantie TrackingManager om gebeurtenissen bij te houden door het volgende toe te voegen:

     `var trackingManager = new s7sdk.TrackingManager();`

   * Verbind componenten met TrackingManager door het volgende te doen:

     Koppel in de gebeurtenishandler `s7sdk.Event.SDK_READY` de component die u wilt bijhouden aan TrackingManager.

     Als de component bijvoorbeeld `videoPlayer` is, voegt u

     `trackingManager.attach(videoPlayer);`

     om de component aan trackingManager vast te maken. Als u meerdere viewers op een pagina wilt bijhouden, gebruikt u meerdere beheercomponenten voor bijhouden.

   * Maak het object AppMeasurementBridge door het volgende toe te voegen:

     ```
     var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
     ```

   * Voeg de functie voor bijhouden toe door het volgende toe te voegen:

     ```
     trackingManager.setCallback(appMeasurementBridge.track, 
      appMeasurementBridge);
     ```

   Het object appMeturementBridge heeft een ingebouwde trackfunctie. U kunt echter uw eigen systeem beschikbaar stellen voor de ondersteuning van meerdere trackingsystemen of andere functies.

<!--    For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->



## Ondersteuning voor meerdere bijschriften en audiotracks voor video&#39;s in dynamische media{#about-msma}

Met de mogelijkheden voor meerdere bijschriften en audiotracks in Dynamic Media kunt u eenvoudig meerdere ondertitels en audiotracks toevoegen aan een primaire video. Dit betekent dat uw video&#39;s toegankelijk zijn voor een wereldwijd publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de ondertitels en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

![&#x200B; Bijschriften en audiosporen lusje in Dynamische Media samen met een lijst die geuploade `.vtt` bijschriftdossiers en geupload .MP3 audiospoordossiers voor een video tonen.](assets-dm/msma-subtitle-audiotracks-tab2.png)

Een aantal van de gebruiksscenario&#39;s die u kunt gebruiken voor het toevoegen van meerdere bijschriften en audiotracks aan uw primaire video zijn onder meer:

| Type | Hoofdletters gebruiken |
|--- |--- |
| **Bijschriften** | Ondersteuning voor meerdere talen |
|  | Beschrijvende tekst voor toegankelijkheid |
| **Audiosporen** | Ondersteuning voor meerdere talen |
|  | Commentaartracks |
|  | Beschrijvende audio |

Alle [&#x200B; video formaten die in Dynamische Media &#x200B;](/help/assets/assets-formats.md) worden gesteund en alle Dynamische videokijkers van Media - behalve de Dynamische 2&rbrace; Video_360 *kijker van Media - worden gesteund voor gebruik met veelvoudige titel en audiosporen.*

### Meerdere bijschriften en audiotracks toevoegen aan uw video {#add-msma}

Voordat u meerdere bijschriften en audiotracks aan uw video toevoegt, moet u controleren of u al over het volgende beschikt:

* Dynamic Media wordt ingesteld in een AEM-omgeving.
* Het profiel van A [&#x200B; Dynamische Video van Media wordt toegepast op de omslag waar uw video&#39;s &#x200B;](/help/assets/video-profiles.md#applying-a-video-profile-to-folders) worden opgenomen.

Toegevoegde bijschriften en bijschriften worden ondersteund in de indelingen WebVTT en Adobe `.vtt` . Toegevoegde audiotrackbestanden worden ook ondersteund in de MP3-indeling.

>[!IMPORTANT]
>
>Om het even welke video&#39;s die u *alvorens* toelatend veelvoudige titel en audiospoorsteun op uw Dynamische rekening van Media uploadde, [&#x200B; moet worden opnieuw verwerkt &#x200B;](/help/assets/processing-profiles.md#reprocessing-assets). Deze videoopwerkingsstap is nodig om ervoor te zorgen dat meerdere bijschriften en audiotrackmogelijkheden beschikbaar zijn. De video-URL&#39;s blijven werken en worden na de opwerking op de gebruikelijke wijze afgespeeld.

**om veelvoudige titel en audiosporen aan uw video toe te voegen:**

1. [&#x200B; uploadt uw primaire video aan een omslag &#x200B;](/help/assets/managing-video-assets.md#upload-and-preview-video-assets) die reeds een videoprofiel heeft dat aan het wordt toegewezen.
1. Navigeer naar het geüploade video-element waaraan u meerdere bijschriften en audiotracks wilt toevoegen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
   ![&#x200B; Geselecteerde videoactiva met controleteken over videoduimnagelbeeld en Eigenschappen van de Mening die op de toolbar worden benadrukt.](assets-dm/msma-selectedasset-propertiesbutton.png)*Geselecteerde videoactiva in de Mening van de Kaart.*
1. Selecteer de tab **[!UICONTROL Captions & Audio Tracks]** op de pagina Eigenschappen van video.

   >[!TIP]
   >Als u het tabblad **[!UICONTROL Captions & Audio Tracks]** niet ziet, betekent dit een van de volgende twee dingen:
   >
   >* Aan de map waarin de geselecteerde video zich bevindt, is geen videoprofiel toegewezen. In welk geval, zie [&#x200B; een videoprofiel op de omslag &#x200B;](/help/assets/video-profiles.md#applying-video-profiles-to-specific-folders) toepassen.
   >* Of dynamische media moeten de video opnieuw verwerken. In welk geval, zie [&#x200B; activa in een omslag &#x200B;](/help/assets/processing-profiles.md#reprocessing-assets) opnieuw verwerken.
   >
   >Als u een van de bovenstaande taken hebt uitgevoerd, gaat u terug naar deze stappen.

   ![&#x200B; Bijschriften en Audiosporen lusje op de pagina van Eigenschappen.](assets-dm/msma-audiotracks2.png)*Bijschriften en audiosporen lusje op de pagina van de Eigenschappen van de video.*

1. (Optioneel) Ga als volgt te werk om een of meer bijschriftbestanden aan een video toe te voegen:
   * Selecteer **[!UICONTROL Upload Captions]** .
   * Navigeer naar en selecteer een of meer `.vtt` (Video Text Tracks)-bestanden en open deze.
   * Voor titels om op de media speler zichtbaar te zijn, moet u **&#x200B; vereiste details (meta-gegevens) over *toevoegen elk* titeldossier dat u uploadde. Selecteer het potloodpictogram rechts van de bestandsnaam van een bijschrift. In &#x200B;** geef de dialoogdoos van de Titel **&#x200B; uit, ga de volgende vereiste details over het dossier in, dan uitgezocht &#x200B;** [!UICONTROL Save]**. Herhaal dit proces voor elk bijschriftbestand dat u hebt geüpload:

     | Metagegevens bijschrift | Beschrijving |
     |--- |--- |
     | Bestandsnaam | De standaardbestandsnaam wordt afgeleid van de oorspronkelijke bestandsnaam. De bestandsnaam kan alleen tijdens het uploaden worden gewijzigd en kan later niet worden gewijzigd. De vereisten voor bestandsnaamtekens zijn gelijk aan die voor AEM Assets.<br> zelfde filename kan niet voor extra titeldossiers en audiospoordossiers worden gebruikt. |
     | Taal | Selecteer de taal van het bijschrift. |
     | Type | Selecteer het type bijschrift dat u gebruikt.<br>**Ondertitel** - de titeltekst die met de video wordt getoond die vertaalt of de dialoog transcripting.<br>**Titel** - de bijschrifttekst omvat achtergrondgeluiden, sprekersdifferentiatie, en andere relevante details. Het verstrekt ook de vertaling of transcriptie van de dialoog. Al deze aspecten maken de inhoud toegankelijker voor doven of slechthorenden. |
     | Label | De tekst die voor de naam van het bijschrift wordt weergegeven in de pop-uplijst **[!UICONTROL Select audio or subtitle]** in de mediaspeler. Het label is wat een klant ziet die met een ondertitel of bijschrifttrack correspondeert. Bijvoorbeeld `English (CC)` . |

     U kunt de metagegevens van bijschriften indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze details weerspiegeld op openbare URLs in gepubliceerde video&#39;s.

1. (Optioneel) Ga als volgt te werk om een of meer audiotracks aan een video toe te voegen:
   * Selecteer **[!UICONTROL Upload Audio Tracks]** .
   * Navigeer naar en selecteer een of meer MP3-bestanden en open deze.
   * Om audiosporen te maken verschijnen in de **[!UICONTROL Select audio or caption]** pop-up lijst op de media speler, moet u **&#x200B; de vereiste details verstrekken. Deze details zijn nodig voor *elk* audiospoordossier dat u toevoegde. Selecteer het potloodpictogram rechts van de bestandsnaam van een audiotrack. In &#x200B;** geef Audiospoor **&#x200B; dialoogdoos uit, ga de volgende vereiste details in, dan uitgezocht &#x200B;** [!UICONTROL Save]**. Herhaal dit proces voor elk audiospoordossier dat u uploadde.

     | Metagegevens audiotrack | Beschrijving |
     |--- |--- |
     | Bestandsnaam | De standaardbestandsnaam wordt afgeleid van de oorspronkelijke bestandsnaam. De bestandsnaam kan alleen tijdens het uploaden worden gewijzigd en kan later niet worden gewijzigd. De vereisten voor bestandsnaamtekens zijn gelijk aan die voor AEM Assets.<br> zelfde filename kan niet voor extra audiospoordossiers of titeldossiers worden gebruikt. |
     | Taal | Selecteer de taal van de audiotrack. |
     | Type | Selecteer het type audiotrack dat u gebruikt.<br>**Origineel** - het audiospoor oorspronkelijk in bijlage aan de video en vertegenwoordigd als `[Original]` in het etiket met `English` taal die door gebrek wordt geselecteerd. Hoewel **[!UICONTROL Label]** en **[!UICONTROL Language]** kunnen worden gewijzigd in het dialoogvenster **[!UICONTROL Edit Audio Track]** , worden de oorspronkelijke waarden gebruikt als de primaire video opnieuw wordt verwerkt.<br>**Norm** - een toe:voegen-op audiospoor voor een taal buiten origineel.<br>**audiobeschrijving** - een audiospoor dat ook een beschrijvend verhaal van non-verbale acties en gebaren in de video omvat, die inhoud toegankelijker maken voor individuen die visueel gehandicapt zijn. |
     | Label | De tekst die als naam van de audiotrack in de pop-uplijst **[!UICONTROL Select audio or subtitle]** in de mediaspeler wordt weergegeven. Het label is wat een klant ziet die met een audiotrack correspondeert. Bijvoorbeeld `English [Original]` . Het label van de audio die aan een video is gekoppeld, wordt standaard ingesteld op `[Original]` . |

     U kunt deze metagegevens van de audiotrack indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze details weerspiegeld op openbare URLs in gepubliceerde video&#39;s.

1. Selecteer **[!UICONTROL Save & Close]** in de rechterbovenhoek van de pagina in de vervolgkeuzelijst **[!UICONTROL Save]** . De dossiers worden geupload en de meta-gegevensverwerking begint, zoals gezien in de **kolom van de Status** van de interface.

   >[!NOTE]
   >
   >Op basis van de cacheinstellingen van uw instantie kan het verwerken van metagegevens enkele minuten duren voordat dit effect wordt weerspiegeld in de voorvertoning en in gepubliceerde URL&#39;s.

1. (Optioneel) Als u **[!UICONTROL Save & Close]** in de vorige stap hebt geselecteerd in plaats van **[!UICONTROL Save]** te selecteren, kunt u nog steeds de verwerkingsstatus van de geüploade bestanden bekijken. Zie [&#x200B; Mening de levenscyclusstatus van geupload titels en audiospoordossiers &#x200B;](#lifecycle-status-video).
1. (Optioneel) Geef een voorvertoning van de video weer voordat u de video publiceert, zodat de bijschriften en audio naar behoren werken. Zie [&#x200B; Voorproef een video die veelvoudige titel en audiosporen &#x200B;](#preview-video-audio-subtitle) heeft
1. Publiceer de video. Zie [&#x200B; activa &#x200B;](publishing-dynamicmedia-assets.md) publiceren.

#### Bijschrift- en audiotrackbestanden toevoegen aan een video die al is gepubliceerd

Als u aanvullende bijschriftbestanden of audiotrackbestanden uploadt naar een reeds gepubliceerde video, wordt de status `Processed` toegewezen aan die bestanden. Deze status wordt toegepast nadat de bestanden na het uploaden zijn voorbereid. Op dat punt kunt u de video voorvertonen in Dynamic Media om de nieuw geüploade bestanden te bekijken of te horen.

Na voorproef, echter, moet u *de video opnieuw voor de onlangs toegevoegde titel of audiospoordossiers publiceren die, ook moeten worden gepubliceerd.* Na publicatie worden de bijschriften of audio beschikbaar via de URL van de openbare dynamische media.

>[!NOTE]
>
>Op basis van de cacheinstellingen van uw instantie kunnen updates van metagegevens enkele minuten duren voordat deze worden weergegeven in de voorvertoning en in gepubliceerde URL&#39;s.

In het scenario waarin u Dynamic Media hebt geconfigureerd voor direct publiceren, wordt door het uploaden van extra bijschrift- of audiobestanden direct een publicatie van de video gestart na het uploaden van bijschrift- of audiobestanden.

>[!CAUTION]
>
>Wanneer u titeldossiers of audiodossiers aan een video uploadt die of gepubliceerd of unpublished is, worden de dossiers geschrapt als u [*&#128279;*](/help/assets/processing-profiles.md#reprocessing-assets) de video opnieuw verwerkt. Alleen de oorspronkelijke audio van de video blijft intact. In dergelijke gevallen moet u de bijschriftbestanden en audiotrackbestanden opnieuw uploaden naar de video.

#### Meerdere bijschriften toevoegen aan een video met een bestaande URL met bijschriftoptie

Dynamische media ondersteunt het toevoegen van één bijschrift met video via een URL-modifier. Zie [&#x200B; titels aan video &#x200B;](#adding-captions-to-video) toevoegen.

Meerdere bijschriftwijzigingen hebben voorrang op een bijschrift dat is toegevoegd via een URL-modifier voor gepubliceerde video&#39;s.

**om veelvoudige titels aan een video toe te voegen die bestaande URL met titelbepaling heeft:**

1. Upload het bijschriftbestand dat al als een modifier aan de video is toegevoegd, zodat u het bestand expliciet kunt beheren.
1. U kunt desgewenst aanvullende bijschriftbestanden uploaden.
1. Publiceer de video op de gebruikelijke wijze.
De bestaande URL met de optie caption kan nu meerdere bijschriften laden.

### De levenscyclusstatus van geüploade bijschriften en audiotrackbestanden weergeven{#lifecycle-status-video}

U kunt de levenscyclusstatus bekijken van elk bijschrift of audiotrackbestand dat naar uw primaire video is geüpload. U kunt dit van **Bijschriften &amp; Audiosporen** lusje van **Eigenschappen** doen.

**om de levenscyclusstatus van een video te bekijken:**

1. Navigeer naar het video-element waarvan u de levenscyclusstatus wilt weergeven.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** . Noteer in de kolom Status de status van elk bijschrift of audiobestand.

| Status bijschrift of audiotrack | Beschrijving |
| --- | --- |
| Verwerking | Wanneer een nieuw bijschrift of audiotrackbestand wordt toegevoegd en opgeslagen, verandert dit in de status &quot;Verwerking&quot;. Dynamic Media verwerkt het bestand door het streamingmanifest aan de primaire video te koppelen. |
| Verwerkt | Nadat de verwerking is voltooid, worden het bijschrift of audiotrackbestand, of de oorspronkelijke audiotrack die is gekoppeld aan de primaire video, weergegeven in de status &quot;Verwerkt&quot;. U kunt voorproef titel en audiospoordossiers die als &quot;Bewerkt&quot;*verschijnen alvorens* u de video live publiceert. |
| Gepubliceerd | De status &quot;Gepubliceerd&quot; vertegenwoordigt een vergelijkbare status als &quot;Gepubliceerd&quot; voor een primaire video. Assets wordt gepubliceerd wanneer de primaire video wordt gepubliceerd en is beschikbaar op de openbare URL voor dynamische media. |
| Mislukt | De status &quot;Mislukt&quot; betekent dat de verwerking van een bijschrift of audiotrackbestand niet is voltooid. Verwijder het bijschrift of het audiotrackbestand en upload het opnieuw. |
| Ongepubliceerd | Wanneer een gepubliceerde primaire video niet expliciet wordt gepubliceerd, worden alle bijschriften of audiotrackbestanden die u aan de video hebt toegevoegd, ook niet gepubliceerd. |

![&#x200B; de kolom van de Status die voor de gebieden van de Sporen van de Ondertitels en Audio wordt benadrukt.](assets-dm/msma-lifecycle-status2.png)*de status van de levenscyclus van elk geupload caption en audiospoordossier.*

### De standaardaudio instellen voor een video met meerdere audiotracks

Standaard wordt de oorspronkelijke audio van een video ingesteld als de standaardaudio die moet worden afgespeeld.

Geüploade audiotrackbestanden kunnen echter worden ingesteld als de standaardaudio die moet worden afgespeeld nadat een video in de viewer is geladen. In het gebruikersinterface van Eigenschappen, onder het **Bijschriften &amp; Audiosporen** lusje, wordt het `Default` etiket toegepast rechts van het audiospoordossier voor videoplayback.

>[!NOTE]
>
>Het afspelen van standaardaudio kan ook afhankelijk zijn van de instelling in de volgende browsers:
>
>* Chrome - De standaardaudio die in de video is ingesteld, wordt afgespeeld.
>* Safari - Als de standaardtaal in Safari is ingesteld, wordt audio afgespeeld met de ingestelde standaardtaal, mits deze beschikbaar is met het manifest van de video. Anders wordt de standaardaudio afgespeeld die is ingesteld als onderdeel van de eigenschappen van een video.

**om de standaardaudio voor een video te plaatsen die veelvoudige audiosporen heeft:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** .
1. Onder de **Audiosporen** rubriek, selecteer het audiospoordossier dat u als gebrek van de video wilt plaatsen.
1. Selecteer **[!UICONTROL Set as default]** .
In de **Reeks als standaard** dialoogdoos, uitgezochte **[!UICONTROL Replace]**.

   ![&#x200B; de rubriek van Audiosporen met een geselecteerde audiospoordossier - naam en benadrukte &quot;Reeks als gebrek&quot;knoop.](assets-dm/msma-defaultaudiotrack2.png)*plaatsend het standaard audiospoor voor een video.*

1. Selecteer **[!UICONTROL Save & Close]** in de rechterbovenhoek.
1. Publiceer de video. Zie [&#x200B; activa &#x200B;](publishing-dynamicmedia-assets.md) publiceren.

### Een voorvertoning weergeven van een video met meerdere bijschriften en audiotracks{#preview-video-audio-subtitle}

Nadat bijschriftbestanden en audiotrackbestanden naar een video zijn geüpload en zijn verwerkt, kunt u met de Dynamic Media-videoviewer (of andere viewertypen, indien gewenst) een voorvertoning van alle verschillende tracks weergeven. Door een voorvertoning weer te geven, kunt u zien hoe uw video er uitziet en hoe de video eruit ziet en klinkt. Zo weet u zeker dat de video zich naar behoren gedraagt.

Wanneer u met de video wordt tevreden, kunt u het [&#x200B; publiceren gebruikend om het even welke volgende methodes.](publishing-dynamicmedia-assets.md)

Zie [&#x200B; de Video of Kijker van het Beeld op een Web-pagina &#x200B;](/help/assets/embed-code.md) inbedden.
Zie [&#x200B; Verbinding URLs aan uw Webtoepassing &#x200B;](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [&#x200B; Dynamische Media Assets aan pagina&#39;s &#x200B;](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.

>[!NOTE]
>
>Het standaardtabblad Experience Manager Preview geeft geen bijschrift en audiotracks weer. De reden hiervoor is dat deze tracks zijn gekoppeld aan Dynamic Media en alleen kunnen worden weergegeven met de voorvertoning van de Dynamic Media Viewer.

**aan voorproef een video die veelvoudige titels en audiosporen heeft:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande video waaraan u meerdere bijschriften en audiotracks hebt toegevoegd.
1. Klik op het video-element zodat u dit kunt openen in de voorvertoningsmodus.
1. Selecteer op de voorvertoningspagina, linksboven op de pagina, de vervolgkeuzelijst en selecteer vervolgens **[!UICONTROL Viewers]** .

   ![&#x200B; drop-down lijst die de optie van Kijkers toont.](assets-dm/msma-selectviewers.png)

1. Selecteer in de lijst Viewers een viewer die u wilt gebruiken voor de videovoorvertoning. In de volgende schermafbeelding ziet u bijvoorbeeld hoe de **[!UICONTROL Video]** -viewer wordt geselecteerd.

   ![&#x200B; Selectie van de Videokijker van de drop-down lijst van Kijkers.](assets-dm/msma-dmviewerselected.png)

1. Selecteer bij de rechterbenedenhoek, links van het volumepictogram, het pictogram van de spraakballon en selecteer vervolgens de audio of het bijschrift die u wilt horen, of zien of beide. U kunt desgewenst onder Bijschriften **[!UICONTROL Off]** selecteren, zodat de bijschriften niet worden weergegeven.

   ![&#x200B; de Audio en de Pop-up lijst van Bijschriften in de Videokijker.](assets-dm/msma-selectaudiosubtitle.png)*Simulatie van een gebruiker die de audio en de titel voor videoplayback selecteren.*

1. Selecteer de knop **[!UICONTROL Play]** van de video om het afspelen te starten.
Noteer de knoppen **[!UICONTROL URL]** en **[!UICONTROL Embed]** in de linkerbenedenhoek. Gebruik deze knopen aan [&#x200B; verbinding URL van de video aan uw Webtoepassing &#x200B;](/help/assets/linking-urls-to-yourwebapplication.md) of [&#x200B; bed de video op een Web-pagina &#x200B;](/help/assets/embed-code.md) in, respectievelijk.
1. Selecteer **[!UICONTROL Close]** in de rechterbovenhoek van de voorvertoningspagina.

### Bijschrift- of audiotrackbestanden verwijderen uit een video

U kunt bijschrift- of audiotrackbestanden verwijderen uit een video. Het verwijderen van gepubliceerde bijschriften of audiotrackbestanden wordt automatisch weerspiegeld in de gepubliceerde URL van de video.

De oorspronkelijke audiotrack die uit een primaire video is geëxtraheerd, kan niet worden verwijderd.

**om titel of audiospoordossiers van een video te schrappen:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** .
1. Voer een van de volgende handelingen uit:

   * Bijschriften - onder de **rubriek van de Bijschriften**, selecteer één of meerdere titeldossiers die u van de video wilt schrappen, dan selecteren **[!UICONTROL Delete]**.
   * De AudioSporen - onder de **Audiosporen** rubriek, selecteer één of meerdere audiospoordossiers die u van de video wilt schrappen, dan selecteren **[!UICONTROL Delete]**.

1. Selecteer **[!UICONTROL OK]** in het dialoogvenster Verwijderen.
1. Publiceer de video.

### Bijschrift- of audiotrackbestanden downloaden die naar een video zijn geüpload

U kunt een of meer bijschrift- of audiotrackbestanden downloaden die u hebt geüpload voor gebruik met een video. U kunt alle geselecteerde bestanden downloaden als ZIP-bestand of een aparte downloadmap maken voor elk bestand.

De oorspronkelijke audiotrack die uit een primair bestand is gehaald, kan niet worden gedownload.

**om titel of audiospoordossiers van een video te downloaden:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** .
1. Voer een van de volgende handelingen uit:

   * Bijschriften - onder de **rubriek van de Bijschriften**, selecteer één of meerdere titeldossiers die u van de video wilt downloaden, dan selecteren **[!UICONTROL Download]**.
   * De AudioSporen - onder de **AudioKeuren** rubriek, selecteer één of meerdere audiospoordossiers die u van de video wilt downloaden, dan selecteren **[!UICONTROL Download]**.

1. Stel in het dialoogvenster Downloaden de volgende opties in:

   | Optie | Beschrijving |
   |--- |--- |
   | Opslaan als | Gebruik de standaardbestandsnaam die u in het tekstveld Opslaan als hebt opgegeven of geef uw eigen naam op. |
   | Een aparte map maken voor elk element | Maak een map voor elk bijschriftbestand of audiotrackbestand dat u hebt geselecteerd om te downloaden. |
   | E-mail | Gebruik uw standaard e-mailprogramma om het .zip-bestand naar een opgegeven e-mailadres te verzenden. |
   | Assets | Hiermee geeft u het aantal bestanden op dat u downloadt en de gecombineerde totale grootte van alle geselecteerde bestanden. Als u deze optie uitschakelt, wordt de knop **[!UICONTROL Download]** gedimd (uitgeschakeld), zodat u geen bestand kunt downloaden. |

1. Selecteer **[!UICONTROL Download]** .
1. Publiceer de video. Zie [&#x200B; activa &#x200B;](publishing-dynamicmedia-assets.md) publiceren.






## Gesloten bijschriften toevoegen aan een video {#adding-captions-to-video}

U kunt het bereik van uw video&#39;s uitbreiden naar wereldwijde markten door ondertiteling toe te voegen aan enkele video&#39;s of aan Adaptive Video Sets. Door ondertiteling toe te voegen, vermijdt u de behoefte om de audio te duwen, of de behoefte om inheemse sprekers te gebruiken om de audio voor elke verschillende taal opnieuw op te nemen. De video wordt afgespeeld in de taal waarin deze is opgenomen. Bijschriften in vreemde talen worden weergegeven zodat mensen in verschillende talen het audiogedeelte nog steeds kunnen begrijpen.

Ondertiteling met gesloten deuren maakt ook een betere toegankelijkheid mogelijk voor doven of slechthorenden.

>[!NOTE]
>
>De videospeler die u gebruikt moet de vertoning van titels steunen.

Zie ook [&#x200B; Toegankelijkheid in Dynamische Media &#x200B;](/help/assets/accessibility-dm.md).

Met Dynamische media worden bijschriftbestanden omgezet in de JSON-indeling (JavaScript Object Notation). Met deze conversie kunt u de JSON-tekst insluiten in een webpagina als een verborgen, maar volledige transcriptie van de video. Zoekprogramma&#39;s kunnen de inhoud vervolgens verkennen en indexeren, zodat de video&#39;s gemakkelijker te vinden zijn en klanten meer informatie krijgen over de video-inhoud.

Zie [&#x200B; statische (niet beeld) inhoud van de Server &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents#image-serving-api) voor meer informatie over het gebruiken van de functie JSON in een URL.

**om gesloten titels aan een video toe te voegen:**

1. U kunt een toepassing of service van derden gebruiken om uw videobijschriftbestand te maken.

   Zorg ervoor dat het bestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsnaamextensie voor ondertiteling is `.vtt` . U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

   Zie [&#x200B; WebVTT: Het formaat van de Tracks van de Tekst van het Web Video &#x200B;](https://w3c.github.io/webvtt/).

   Er zijn vele websites die zowel gratis als premiumhulpmiddelen en de diensten aanbieden die u aan auteurWebVTT caption/caption dossiers buiten Dynamische Media kunt gebruiken. <!-- THE FOLLOWING LINK IS NO LONGER LIVE. CHECKED DECEMBER 13, 2023 For example, to create a simple video caption file with no styling, you can use the following free online caption authoring and editing tool: -->

   <!--[WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   For best results, use the tool in Internet Explorer 9 or above, Google Chrome, or Safari.

   In the tool, in the **[!UICONTROL Enter URL of video file]** field, paste the copied URL of your video file and then click **[!UICONTROL Load]**. See [Obtain a URL for an Asset](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) to get the URL to the video file itself which you can then paste into the **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome, or Safari can then natively play back the video. -->

   Volg de aanwijzingen op het scherm van een site om het WebVTT-bestand te ontwerpen en op te slaan. Wanneer u klaar bent, kopieert u de inhoud van het bijschriftbestand en plakt u deze in een teksteditor zonder opmaak en slaat u het bestand op met de bestandsnaamextensie `.vtt` .

   >[!NOTE]
   >
   >Voor algemene ondersteuning van videobijschriften in meerdere talen vereist de WebVTT-standaard dat u afzonderlijke `.vtt` bestanden maakt en aanroepen voor elke taal die u wilt ondersteunen.

   Over het algemeen wilt u het bijschriftbestand `.vtt` dezelfde naam geven als het videobestand en dit bestand toevoegen met de landinstelling van de taal, zoals -EN, -FR of -DE. Op deze manier kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.

1. Upload in Experience Manager uw WebVTT-bijschriftbestand naar DAM.
1. Navigeer aan *gepubliceerde* videoactiva die u met het titeldossier wilt associëren dat u uploadde.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*.

   Zie [&#x200B; activa &#x200B;](/help/assets/publishing-dynamicmedia-assets.md) publiceren.

1. Voer een van de volgende handelingen uit:

   * Klik op **[!UICONTROL URL]** voor een pop-upviewerervaring voor video. Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord en passeer de URL naar een eenvoudige teksteditor. Voeg de gekopieerde URL van de video toe met de volgende syntaxis:

     `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

     Noteer de `,1` aan het einde van het bijschriftpad. Direct na de bestandsnaamextensie van `.vtt` in het pad kunt u optioneel de knop voor een gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door deze in te stellen op respectievelijk `,1` of `,0` .

   * Selecteer **[!UICONTROL Embed Code]** voor een ingesloten videoviewerervaring. Selecteer in het dialoogvenster Code insluiten de insluitcode en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor. Voeg de gekopieerde insluitcode toe met de volgende syntaxis:

     `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

     Noteer de `,1` aan het einde van het bijschriftpad. Direct na de bestandsnaamextensie van `.vtt` in het pad kunt u optioneel de knop voor een gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door deze in te stellen op respectievelijk `,1` of `,0` .

## Hoofdstukmarkeringen aan video toevoegen {#adding-chapter-markers-to-video}

U kunt lange-vormvideo&#39;s gemakkelijker bekijken en navigeren door hoofdstukmarkeringen toe te voegen aan enkele video&#39;s of aan Adaptieve videosets. Wanneer een gebruiker de video afspeelt, kunnen hij of zij op de hoofdstukmarkeringen op de videotijdlijn (ook wel de videoscrubber genoemd) klikken om gemakkelijk naar zijn of haar interessepunt te navigeren. Of ze kunnen meteen naar nieuwe inhoud, demonstraties en zelfstudies gaan.

>[!NOTE]
>
>De gebruikte videospeler moet het gebruik van hoofdstukmarkeringen steunen. Dynamische media-videospelers ondersteunen wel hoofdstukmarkeringen, maar het gebruik van videospelers van derden is mogelijk niet mogelijk.

Desgewenst kunt u uw eigen aangepaste videoviewer maken en markeren met hoofdstukken in plaats van een voorinstelling voor de videoviewer te gebruiken. Voor instructies over het maken van uw eigen HTML5-viewer met hoofdstuknavigatie verwijst u in de Adobe HTML5 Viewer SDK API naar de kop &quot;Gedrag aanpassen met wijzigingstoetsen&quot; onder de klassen `s7sdk.video.VideoPlayer` en `s7sdk.video.VideoScrubber` . Zie [&#x200B; HTML5 de 1&rbrace; documentatie van SDK API van de Kijker.](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

<!-- If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading "Customizing Behavior Using Modifiers" under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

U maakt een hoofdstuklijst voor uw video op ongeveer dezelfde manier als u bijschriften maakt. U maakt dus een WebVTT-bestand. Dit bestand moet echter gescheiden zijn van elk WebVTT-bijschriftbestand dat u ook gebruikt. U kunt bijschriften en hoofdstukken niet combineren tot één WebVTT-bestand.

U kunt het volgende voorbeeld als voorbeeld van het formaat gebruiken u gebruikt om een dossier WebVTT met hoofdstuknavigatie tot stand te brengen:

### WebVTT-bestand met navigatie in videohoofdstukken {#webvtt-file-with-video-chapter-navigation}

```xml
WEBVTT
Chapter 1
00:00.000 --> 01:04.364
The bicycle store behind it all.
Chapter 2
01:04.364 --> 02:00.944
Creative Cloud.
Chapter 3
02:00.944 --> 03:02.937
Ease of management for a working solution.
Chapter 4
03:02.937 --> 03:35.000
Cost-efficient access to rapidly evolving technology.
```

In het bovenstaande voorbeeld is `Chapter 1` de cue-id en optioneel. De actieduur van `00:00:000 --> 01:04:364` geeft de begin- en eindtijd van het hoofdstuk op in de `00:00:000` -indeling. Deze laatste drie cijfers zijn milliseconden en kunnen desgewenst als `000` worden verlaten. De hoofdstuktitel van `The bicycle store behind it all` is de feitelijke beschrijving van de inhoud van het hoofdstuk. De actidentificator, de begintijd en de hoofdstuktitel worden allemaal weergegeven in een pop-up van een videospeler wanneer een gebruiker de muisaanwijzer boven een visueel actiepunt in de tijdlijn van de video houdt.

Omdat u een HTML5-videoviewer gebruikt, moet u ervoor zorgen dat het hoofdstukbestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsextensie van het hoofdstuk is `.vtt` . U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

Zie [&#x200B; WebVTT: Het formaat van de Tracks van de Tekst van het Web Video &#x200B;](https://w3c.github.io/webvtt/)

**om de navigatie van het videohoofdstuk toe te voegen:**

1. Sla het `.vtt` -bestand op in UTF8-codering, zodat u problemen met tekenuitvoering in de hoofdstuktiteltekst voorkomt.

   Over het algemeen wilt u het hoofdstukbestand een naam geven `.vtt` die gelijk is aan het videobestand en dit bestand toevoegen met hoofdstukken. Op deze manier kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.
1. Upload in Experience Manager uw WebVTT-hoofdstukbestand.

   Zie [&#x200B; Uploading Assets &#x200B;](/help/assets/manage-assets.md#uploading-assets).

1. Voer een van de volgende handelingen uit:

   <table>
     <tbody>
      <tr>
       <td>Voor een viewerervaring voor pop-upvideo's</td>
       <td>
       <ol>
       <li>Navigeer aan <i> gepubliceerde </i> videoactiva die u met het hoofdstukdossier wilt associëren dat u uploadde. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/publishing-dynamicmedia-assets.md"> het Publiceren Assets.</a></li>
       <li>Van het drop-down menu, dan klik <strong> Kijkers </strong>.</li>
       <li>Klik in de linkertrack op de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>In het linkerspoor, bij de bodem, klik <strong> URL </strong>.</li>
       <li>Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord. Plak vervolgens de URL in een eenvoudige teksteditor.</li>
       <li>Voeg de gekopieerde URL van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand: <br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Voor een ingebedde videokijkervaring, <br /> </td>
       <td>
       <ol>
       <li>Navigeer aan <i> gepubliceerde </i> videoactiva die u met het hoofdstukdossier wilt associëren dat u uploadde. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/publishing-dynamicmedia-assets.md"> het Publiceren Assets.</a></li>
       <li>Van het drop-down menu, dan klik <strong> Kijkers </strong>.</li>
       <li>Klik in de linkertrack op de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>In het linkerspoor, bij de bodem, klik <strong> bed </strong> in.</li>
       <li>Selecteer in het dialoogvenster Code insluiten de gehele code en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor.</li>
       <li>Voeg de insluitcode van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>

## Ongeveer videoduimnagels in Dynamische Media - wijze Scene7 {#about-video-thumbnails-in-dynamic-media-scene-mode}

Een videominiatuur is een verkleinde versie van een videoframe of een afbeeldingselement dat de video voor de klant vertegenwoordigt. De miniatuur moedigt een klant aan om de video te selecteren.

Aan alle video&#39;s in Experience Manager moet een miniatuur zijn gekoppeld. Als u een miniatuur verwijdert, moet u deze vervangen. Wanneer u een video uploadt naar Experience Manager, wordt standaard het eerste frame gebruikt als miniatuur. U kunt de miniatuur echter aanpassen voor bijvoorbeeld branding of visuele zoekopdracht. Wanneer u een videominiatuur aanpast, kunt u de video afspelen en pauzeren op het frame dat u wilt gebruiken. Of, kunt u een beeldactiva selecteren die u reeds hebt geupload en *gepubliceerd* in uw digitale activamanager.

Een aangepaste videominiatuurafbeelding die u selecteert uit een video, wordt niet geëxtraheerd en in de DAM opgeslagen als een afzonderlijk en afzonderlijk element. Een aangepaste videominiatuur die u selecteert uit een bestaand afbeeldingselement, wordt echter opgeslagen in de tekenherkenning. Het pad van het geselecteerde element wordt opgeslagen onder het knooppunt van het video-element, zoals in het volgende voorbeeldpad:

`/content/dam/*<folder_name*>/<*video_name*>/jcr:content/manualThumbnail`

De mogelijkheid om een videominiatuur aan te passen is alleen beschikbaar nadat u een videoprofiel hebt toegepast op de map waarin de video zich bevindt.

Zie ook [&#x200B; Ongeveer videoduimnagels in Dynamische Media - Hybride wijze &#x200B;](#about-video-thumbnails-in-dynamic-media-hybrid-mode).

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail}

Deze stappen zijn alleen van toepassing op dynamische media die in de modus &quot;Dynamicmedia_Scene7&quot; worden uitgevoerd.

**om een duimnagel van de douanevideo toe te voegen:**

1. Zorg ervoor dat u al het volgende hebt gedaan:

   * Er is een map gemaakt voor uw video-elementen.
   * [&#x200B; pas een videoprofiel op de omslag &#x200B;](/help/assets/video-profiles.md#applying-a-video-profile-to-folders) toe.

   * [&#x200B; uploadde uw video&#39;s aan de omslag &#x200B;](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

1. Navigeer naar een geüpload video-element waarvan u de miniatuurafbeelding wilt wijzigen.
1. Selecteer het video-element in de modus voor middelenselectie van **[!UICONTROL List View]** of **[!UICONTROL Card View]** .
1. Selecteer op de werkbalk het pictogram **[!UICONTROL Properties]** (een cirkel met een &quot;i&quot; erin).
1. Selecteer **[!UICONTROL Change Thumbnail]** op de pagina Eigenschappen van video.
1. Voer een van de volgende handelingen uit op de pagina Miniatuur wijzigen:

   * Een frame uit de video gebruiken als de nieuwe miniatuur:

      * Selecteer **[!UICONTROL Select Frame from video]** op de werkbalk.
      * Selecteer de knop Afspelen en selecteer vervolgens de knop Pauzeren in het frame dat u wilt vastleggen als de nieuwe miniatuur van de video.

   * Een afbeeldingselement gebruiken als de nieuwe miniatuur:

      * Selecteer **[!UICONTROL Select Thumbnail from Assets]** op de werkbalk.
      * Selecteer **[!UICONTROL Select Thumbnail]** .
      * Navigeer naar een eerder geüpload en gepubliceerd afbeeldingselement dat u wilt gebruiken. De grootte van het element wordt automatisch gewijzigd om te dienen als miniatuurafbeelding voor de video.
      * Selecteer het afbeeldingselement en selecteer vervolgens **[!UICONTROL Select]** .

1. Selecteer **[!UICONTROL Save Change]** op de pagina Miniatuur wijzigen.
1. Selecteer **[!UICONTROL Save & Close]** in de rechterbovenhoek van de pagina Eigenschappen van video.

## Informatie over videominiaturen in de modus Dynamische media - Hybride {#about-video-thumbnails-in-dynamic-media-hybrid-mode}

U kunt kiezen uit een van de tien miniatuurafbeeldingen die automatisch door Dynamic Media worden gegenereerd om aan uw video toe te voegen. De videospeler geeft de geselecteerde miniatuur weer wanneer een video-element wordt gebruikt met de component Dynamic Media in de ontwerpomgeving van Experience Manager Sites, Experience Manager Mobile of Experience Manager Screens. De miniatuur fungeert als een statisch beeld dat de inhoud van de gehele video het beste vertegenwoordigt en dat gebruikers verder aanmoedigt om op de knop Afspelen te klikken.

Dynamische media legt tien (standaard)miniatuurafbeeldingen vast op basis van de totale tijd van de video. Het systeem legt beelden met de volgende videointervallen vast:

* 1%
* 11%
* 21%
* 31%
* 41%
* 51%
* 61%
* 71%
* 81%
* 91%

De tien miniaturen blijven bestaan. Dit betekent dat als u een andere miniatuur kiest, u de reeks niet opnieuw hoeft te genereren. U bekijkt een voorvertoning van de tien miniatuurafbeeldingen en selecteert vervolgens de miniatuurafbeelding die u voor de video wilt gebruiken. Als u de standaardinstelling wilt wijzigen, kunt u CRXDE Lite gebruiken om het tijdsinterval te configureren dat miniatuurafbeeldingen worden gegenereerd. Als u bijvoorbeeld alleen een reeks van vier miniatuurafbeeldingen met gelijkmatige tussenruimte uit uw video wilt genereren, kunt u de intervaltijd instellen op 24%, 49%, 74% en 99%.

In het ideale geval kunt u een videominiatuur toevoegen nadat u de video hebt geüpload, maar voordat u de video op uw website publiceert.

Desgewenst kunt u een aangepaste miniatuur uploaden om uw video te vertegenwoordigen in plaats van een miniatuur te gebruiken die is gegenereerd door Dynamic Media. U kunt bijvoorbeeld een aangepaste miniatuurafbeelding maken met de titel van uw video, een opvallende openingsafbeelding of een specifieke afbeelding die u van uw video hebt vastgelegd. De aangepaste videominiatuurafbeelding die u uploadt, moet een maximale resolutie van 1280 × 720 pixels (minimale breedte van 640 pixels) hebben en mag niet groter zijn dan 2 MB.

Zie ook [&#x200B; Ongeveer videoduimnagels in Dynamische Media - wijze Scene7 &#x200B;](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

### Een videominiatuur toevoegen {#adding-a-video-thumbnail}

Deze stappen zijn alleen van toepassing op dynamische media die in de hybride modus worden uitgevoerd.

**om een videoduimnagel toe te voegen:**

1. Navigeer naar een geüpload video-element waaraan u een videominiatuur wilt toevoegen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram **[!UICONTROL View Properties]** (een cirkel met een &quot;i&quot; erin).
1. Selecteer **[!UICONTROL Change Thumbnail]** op de pagina Eigenschappen van video.
1. Selecteer op de pagina Miniatuur wijzigen op de werkbalk de optie **[!UICONTROL Select Frame]** .

   Dynamische media genereert een reeks miniatuurafbeeldingen van uw video op basis van het standaardtijdinterval of tijdinterval dat u hebt aangepast.

1. Geef een voorvertoning van de gegenereerde miniatuurafbeeldingen weer en selecteer de miniatuurafbeelding die u aan de video wilt toevoegen.
1. Selecteer **[!UICONTROL Save Change]** .

   De miniatuurafbeelding van de video wordt bijgewerkt zodat deze de geselecteerde miniatuur gebruikt. Als u later besluit de miniatuurafbeelding te wijzigen, gaat u terug naar de pagina **[!UICONTROL Change Thumbnail]** en selecteert u een nieuwe pagina.

   Als u nieuwe standaardtijdintervallen instelt of een nieuwe video uploadt om bestaande te vervangen, zorg ervoor dat de Dynamische Media de duimnagels opnieuw produceert.

   Zie [&#x200B; het standaardtijdinterval vormen dat de videoduimnagels &#x200B;](#configuring-the-default-time-interval-that-video-thumbnails-are-generated) worden geproduceerd.

#### Configureer het standaardtijdinterval dat videominiaturen worden gegenereerd {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

Wanneer u het nieuwe standaardtijdinterval configureert en opslaat, is uw wijziging automatisch alleen van toepassing op video&#39;s die u in de toekomst uploadt. De nieuwe standaard wordt niet automatisch toegepast op video&#39;s die u eerder hebt geüpload. Voor bestaande video&#39;s moet u de miniaturen opnieuw genereren.

Zie [&#x200B; een videoduimnagel &#x200B;](#adding-a-video-thumbnail) toevoegen.

**om het standaardtijdinterval te vormen dat de videoduimnagels worden geproduceerd:**

1. Selecteer in Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]** .

1. Navigeer op de CRXDE Lite-pagina in het mappenvenster links naar `o etc/dam/imageserver/configuration/jcr:content/settings.`

   als het mappendeelvenster niet zichtbaar is, selecteert u het pictogram >> links van het tabblad Start.

1. Dubbelselecteer `thumbnailtime` op het tabblad Eigenschappen in het deelvenster rechtsonder.
1. Gebruik de tekstvelden in het dialoogvenster **[!UICONTROL Edit thumbnailtime]** om intervalwaarden in te voeren als percentages.

   * Selecteer het plusteken (+) pictogram als u één of meerdere gebieden van de intervalwaarde wilt toevoegen. Blader zo nodig naar de onderkant van het dialoogvenster om het pictogram weer te geven.
   * Selecteer het minteken (-) rechts van een veld voor de intervalwaarde als u het uit de lijst wilt verwijderen.
   * Selecteer het pictogram pijl-omhoog en pijl-omlaag als u de intervalwaarden opnieuw wilt rangschikken.

1. Selecteer **[!UICONTROL OK]** en ga terug naar het tabblad Eigenschappen.
1. Selecteer **[!UICONTROL Save All]** in de linkerbovenhoek van de CRXDE Lite-pagina en selecteer vervolgens het pictogram Home Terug in de linkerbovenhoek om terug te keren naar Experience Manager.

   Zie [&#x200B; een videoduimnagel &#x200B;](#adding-a-video-thumbnail) toevoegen.

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail-1}

Deze stappen zijn alleen van toepassing op dynamische media die in de hybride modus worden uitgevoerd.

**om een duimnagel van de douanevideo toe te voegen:**

1. Navigeer naar een geüpload video-element waaraan u een aangepaste miniatuur voor video wilt toevoegen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram **[!UICONTROL View Properties]** (een cirkel met een &quot;i&quot; erin).
1. Selecteer **[!UICONTROL Change Thumbnail]** op de pagina Eigenschappen van video.
1. Selecteer op de pagina Miniatuur wijzigen op de werkbalk de optie **[!UICONTROL Upload New Thumbnail]** .
1. Navigeer naar een miniatuurafbeelding die u wilt gebruiken, selecteer deze en selecteer vervolgens **[!UICONTROL Open]** om de afbeelding naar Experience Manager te uploaden. Na het uploaden moet u de afbeelding publiceren.
1. Selecteer **[!UICONTROL Save Changes]** nadat u de afbeelding hebt geüpload en gepubliceerd op de pagina Miniatuur wijzigen.

   De aangepaste miniatuur wordt toegevoegd aan uw video.

## De URL van dynamische media voor dynamische media-elementen wijzigen {#manifest-urls}

Video&#39;s die in dynamische media worden verwerkt, kunnen worden gebruikt met viewers die niet in de box staan. Of door de manifest-URL&#39;s te openen en deze af te spelen in aangepaste viewers. Hier volgt de API voor het ophalen van manifest-URL&#39;s voor een video.

### Over de getVideoManifestURI-API

`getVideoManifestURI` API wordt blootgesteld door c `q-scene7-api:com.day.cq.dam.scene7.api` en kan worden gebruikt om volgende manifest URLs te produceren:

```java
/**   
* Returns the manifest url for videos 
* @param resource video resource 
* @param manifestType type of video streaming manifest being requested 
* @param onlyIfPublished return a manifest only if the video is published 
* @return the manifest url for videos 
* 
* @throws Exception 
*/
@Nullable 
String getVideoManifestURI(Resource resource, ManifestType manifestType, boolean onlyIfPublished) throws Exception;
```

#### getVideoManifestURI API-parameters

Deze API heeft de volgende drie parameters:

| Parameter | Beschrijving |
| --- | --- |
| `resource` | De bron die correspondeert met de video die Dynamic Media heeft ingeslikt. |
| `manifestType` | Kan `ManifestType.DASH` of `ManifestType.HLS` zijn |
| `onlyIfPublished` | Ingesteld op true voor het geval dat de manifest-uri alleen wordt gegenereerd als deze wordt gepubliceerd en beschikbaar is op de leveringslaag. |

Om manifest URLs voor video&#39;s te halen die de methode hierboven gebruiken, voeg a [&#x200B; video het coderen profiel &#x200B;](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) aan een &quot;upload video&quot;omslag toe. Dynamische media verwerkt deze video&#39;s op basis van de coderingen in het videocoderingsbestand dat aan de map is toegewezen. Nu kunt u de bovenstaande API aanroepen voor het ophalen van manifest-URL&#39;s voor de geüploade video&#39;s.

### Foutscenario&#39;s

De API retourneert null als er fouten zijn. Uitzonderingen worden aangemeld bij Experience Manager-foutenlogboeken. Dergelijke geregistreerde fouten beginnen met `Could not generate Video Manifest URI`. Dergelijke fouten kunnen in de volgende scenario&#39;s optreden:

* Een `IllegalArgumentException` wordt geregistreerd voor om het even welke volgend:

   * De doorgegeven parameter `resource` is null.
   * De doorgegeven parameter `resource` is geen video.
   * De doorgegeven parameter `manifestType` is null.
   * De parameter `onlyIfPublished` wordt doorgegeven als true, maar de video wordt niet gepubliceerd.
   * De video is niet opgenomen met een adaptieve videoset van Dynamic Media.

* `IOException` wordt geregistreerd wanneer er een probleem is met de verbinding met dynamische media.
* `UnsupportedOperationException` wordt geregistreerd wanneer een doorgegeven `manifestType` parameter `ManifestType.DASH` is, terwijl de video niet is verwerkt met de DASH-indeling.

Het volgende is een voorbeeld van bovengenoemde API gebruikend servlets die in de ** specificatie HTTPWhiteBoard worden geschreven. Selecteer elk tabblad voor de codesyntaxis.

>[!BEGINTABS]

>[!TAB voegt gebiedsdeel in pom.xml  toe]

+++**voegt gebiedsdeel in pom.xml** toe 

```java
dependency> 
     <groupId>com.day.cq.dam</groupId> 
     <artifactId>cq-scene7-api</artifactId> 
     <version>5.12.64</version> 
     <scope>provided</scope> 
</dependency> 
```

+++

>[!TAB  servlet van de Steekproef ]

+++**servlet van de Steekproef** 

```java
@Component
        service = Servlet.class 
) 
@HttpWhiteboardServletPattern(value = ManifestServlet.SERVLET_PATTERN) 
@HttpWhiteboardContextSelect(value = Constants.SERVLET_CONTEXT_SELECTOR) 
public class ManifestServlet extends HttpServlet { 

   private static final Logger LOGGER = LoggerFactory.getLogger(ManifestServlet.class); 

   private final ObjectMapper objectMapper; 

    @Reference 
    private Scene7Service scene7Service; 

   public static final String SERVLET_PATTERN = Constants.VIDEO_API_PREFIX + "/manifestUrl"; 

   public ManifestServlet() {
         this.objectMapper = new ObjectMapper(); 
         objectMapper.setSerializationInclusion(JsonInclude.Include.NON_NULL); 
   }

   @Override 

   protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        final ResourceResolver resolver = getResourceResolver(request); 
        String assetPath = request.getParameter("assetPath"); 
        String manifest = request.getParameter("manifestType"); 
        String onlyIfPublished = request.getParameter("onlyIfPublished"); 
        Resource resource = resolver.getResource(assetPath); 
        response.setCharacterEncoding(StandardCharsets.UTF_8.toString()); 
        response.setContentType("application/json"); 
        if(resource == null) { 
            LOGGER.info("could not retrieve the resource from JCR"); 
            error("could not retrieve the resource from JCR", response); 
            return; 
        }

        String manifestUri = null; 

        try{ 
            ManifestType manifestType =  ManifestType.DASH; 
            if(manifest != null) { 
                manifestType = ManifestType.valueOf(manifest); 
            } 
            manifestUri = scene7Service.getVideoManifestURI(resource, manifestType, onlyIfPublished != null); 
            objectMapper.writeValue(response.getWriter(), new ManifestUrl(manifestUri)); 
            response.setContentType("application/json"); 
        } catch (Exception e) { 
            LOGGER.error(e.getMessage(), e); 
            error(String.format("Unable to get the manifest url for %s. %s", assetPath, e.getMessage()), response); 
        } 
    } 

    private ResourceResolver getResourceResolver(HttpServletRequest request) { 
        Object rr = request.getAttribute(AuthenticationSupport.REQUEST_ATTRIBUTE_RESOLVER); 
        if (!(rr instanceof ResourceResolver)) { 
            throw new IllegalStateException( 
                    "The request does not seem to have been created via Apache Sling's authentication mechanism."); 
        } else { 
            return (ResourceResolver) rr; 
        } 
    } 

    private void error(String errorMessage, HttpServletResponse response) throws IOException { 
        ManifestUrl errorManifest = new ManifestUrl(null); 
        errorManifest.setErrorMessage(errorMessage); 
        response.setStatus(HttpServletResponse.SC_INTERNAL_SERVER_ERROR); 
        objectMapper.writeValue(response.getWriter(), errorManifest); 
    } 
} 
```

+++

>[!TAB  Klasse van de Reactie voor servlet ]

+++**Klasse van de Reactie voor servlet** 

```java
public class ManifestUrl extends VideoResponse { 
     String manifestUrl; 
     public ManifestUrl(String manifestUrl) { 
         this.manifestUrl = manifestUrl; 
     } 
     public String getManifestUrl() { 
         return manifestUrl; 
     } 
} 

public abstract class VideoResponse { 
     String errorString; 

     public String getErrorString() { 
         return errorString; 
     } 

     public void setErrorMessage(String errorString) { 
         this.errorString = errorString; 
     } 
} 
```

+++

>[!TAB  het dossier van constanten die in servlet van verwijzingen worden voorzien ]

+++**het dossier van constanten die in servlet van verwijzingen worden voorzien** 

```java
public final class Constants { 

     private Constants() { 
     } 

     public static final String VIDEO_API_PREFIX = "/dynamicmedia/video"; 
     public static final String SERVLET_CONTEXT_SELECTOR = "(" + HttpWhiteboardConstants.HTTP_WHITEBOARD_CONTEXT_NAME + "=" + 
             DMSampleApiHttpContext.CONTEXT_NAME + ")"; 

 } 
```

+++

>[!TAB  ServletContext ]

+++**ServletContext** 

Koppel de bovenstaande servlet met een `servletContext` . Hieronder ziet u een voorbeeld van `servletContext` .

```java
public class DMSampleApiHttpContext extends ServletContextHelper { 

 public static final String CONTEXT_NAME = "com.adobe.dmSample"; 
 public static final String CONTEXT_PATH = "/dmSample"; 

 private final MimeTypeService mimeTypeService; 

 private final AuthenticationSupport authenticationSupport; 

 /** 
  * Constructs a new context that will use the given dependencies. 
  * 
  * @param mimeTypeService Used when providing mime type of requests. 
  * @param authenticationSupport Used to authenticate requests with sling. 
  */ 
 @Activate 
 public DMSampleApiHttpContext(@Reference final MimeTypeService mimeTypeService, 
                               @Reference final AuthenticationSupport authenticationSupport) { 
     this.mimeTypeService = mimeTypeService; 
     this.authenticationSupport = authenticationSupport; 
 } 

 // ---------- HttpContext interface ---------------------------------------- 
 /** 
  * Returns the MIME type as resolved by the <code>MimeTypeService</code> or 
  * <code>null</code> if the service is not available. 
  */ 
 @Override 
 public String getMimeType(String name) { 
     MimeTypeService mtservice = mimeTypeService; 
     if (mtservice != null) { 
         return mtservice.getMimeType(name); 
     } 
     return null; 
 } 

 /** 
  * Returns the real context path that is used to mount this context. 
  * @param req servlet request 
  * @return the context path 
  */ 
 public static String getRealContextPath(HttpServletRequest req) { 
     final String path = req.getContextPath(); 
     if (path.equals(CONTEXT_PATH)) { 
         return ""; 
     } 
     return path.substring(CONTEXT_PATH.length()); 
 } 

 /** 
  * Returns a request wrapper that transforms the context path back to the original one 
  * @param req request 
  * @return the request wrapper 
  */ 
 public static HttpServletRequest createContextPathAdapterRequest(HttpServletRequest req) { 
     return new HttpServletRequestWrapper(req) { 

         @Override 
         public String getContextPath() { 
             return getRealContextPath((HttpServletRequest) getRequest()); 
         } 

     }; 

 } 

 /** 
  * Always returns <code>null</code> because resources are all provided 
  * through individual endpoint implementations. 
  */ 
 @Override 
 public URL getResource(String name) { 
     return null; 
 } 

 /** 
  * Tries to authenticate the request using the 
  * <code>SlingAuthenticator</code>. If the authenticator or the Repository 
  * is missing this method returns <code>false</code> and sends a 503/SERVICE 
  * UNAVAILABLE status back to the client. 
  */ 
 @Override 
 public boolean handleSecurity(HttpServletRequest request, 
                               HttpServletResponse response) throws IOException { 

     final AuthenticationSupport authenticator = this.authenticationSupport; 
     if (authenticator != null) { 
         return authenticator.handleSecurity(createContextPathAdapterRequest(request), response); 
     } 

     // send 503/SERVICE UNAVAILABLE, flush to ensure delivery 
     response.sendError(HttpServletResponse.SC_SERVICE_UNAVAILABLE, 
             "AuthenticationSupport service missing. Cannot authenticate request."); 
     response.flushBuffer(); 

     // terminate this request now 
     return false; 
 } 
}
```

+++

>[!ENDTABS]

### De voorbeeldservlet gebruiken

U roept de servlet aan door een `GET` -bewerking bij `/dmSample/dynamicmedia/video/manifestUrl` uit te voeren. De volgende queryparameters worden doorgegeven:

| Query-parameter | Beschrijving |
| --- | --- |
| `assetPath` | Verplicht. Het pad naar de video waarvoor `manifestUrl` wordt gegenereerd. |
| `manifestType` | Optioneel. De parameter kan DASH of HLS zijn. Als het niet wordt overgegaan, blijft het aan DASH in gebreke. |
| `onlyIfPublished` | Optioneel. Als de waarde wordt doorgegeven, wordt de waarde `manifestUrl` alleen geretourneerd als de video is gepubliceerd. |

In dit voorbeeld, veronderstel de volgende opstelling:

* Het bedrijf is `samplecompany` .
* De ontwerpinstantie is `http://sample-aem-author.com` .
* Op de map `/content/dam/video-example` is een videocoderingsprofiel toegepast.
* De video `scenery.mp4` wordt geüpload naar de map `/content/dam/video-example` .

U kunt de servlet op de volgende manieren aanroepen:

| Type | Beschrijving |
| :--- | --- |
| HLS | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=HLS&assetPath=/content/dam/video-example/scenery.mp4`<br><br> als de levering van DASH wordt toegelaten:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8?packagedStreaming=true"}`<br><br> als de levering van DASH gehandicapt is:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8"}` |
| DASH | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scenery.mp4`<br><br> als de levering van DASH wordt toegelaten:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.mpd"}`<br><br> als de levering van DASH gehandicapt is:<br>`{}` |
| Fout: middelenpad is onjuist | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scennnnnnery.mp4`<br><br>`{"errorString":"could not retrieve the resource from JCR"}` |




<!-- OBSOLETE. REMOVED AS PER EMAIL FROM RIYA MIDHA ON WEDNESDAY, MARCH 5, 2025

### Enable DASH, multiple caption and audio track support on your Dynamic Media account {#enable-dash}

**About enabling DASH on your account**
DASH (Digital Adaptive Streaming over HTTP) is the international standard for video streaming and is widely adopted across different video viewers. When DASH is enabled on your account, you get the option to choose from either DASH or HLS for adaptive video streaming. Or, you can opt for both with automatic switching between players when **[!UICONTROL auto]** is selected as the playback type in the Viewer preset.

Some key benefits from enabling DASH on your account include the following:
     
* Package DASH stream video for adaptive bitrate streaming. This method leads to higher efficiency of delivery. Adaptive streaming ensures the best viewing experience for your customers.
* Browser optimized streaming with Dynamic Media players switches between HLS and DASH streaming to ensure the best quality of service. The video player auto-switches to HLS when a Safari browser is used.
* You can configure your preferred streaming method (HLS or DASH) by editing the video viewer preset.
* Optimized video encoding ensures that no additional storage is used while enabling DASH capability. A single set of video encodings are created for both HLS and DASH to optimize video storage costs.
* Helps make video delivery more accessible for your customers.
* Get the streaming URL by way of APIs, too.

Enabling DASH on your account requires two steps: 

* Configuring Dynamic Media to use DASH, which you can easily do yourself.
* Configuring Experience Manager 6.5 to use DASH which is done by way of an Adobe Customer Support case that you create and submit.

When you create an Adobe Support case to enable DASH on your account, multiple caption and audio track support is automatically enabled as well. Once activated, all newly uploaded videos are processed using an updated backend architecture that supports adding multiple caption and audio tracks.

>[!IMPORTANT]
>
>Any videos that you uploaded *before* enabling multiple caption and audio track support on your Dynamic Media account, [must be reprocessed](/help/assets/processing-profiles.md#reprocessing-assets). This video reprocessing step is necessary so that multiple caption and audio track capability is available to them. The video URLs continue to work and play as usual, after reprocessing.

**To enable DASH, multiple caption and multiple audio track support on your Dynamic Media account:**

<!-- 1. **Configure Dynamic Media for DASH** - In Dynamic Media on Experience Manager 6.5, navigate to [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).

1. Search for **AEM Assets Dynamic Media Video Advanced Streaming** feature flag.
1. To enable (turn on) DASH, select the checkbox.
1. Begin by **configuring Dynamic Media for DASH** - From Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

1. From the **[!UICONTROL Adobe Experience Manager Web Console Configuration]** page, scroll to the name *AEM Assets Dynamic Media Video Advanced Streaming Feature Flag*.

1. To the left of the name, select the checkbox to enable (turn on) DASH.

1. Select **[!UICONTROL Save]**.

1. Now, use the Admin Console to start the [creation of a new support case](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html).
1. To create a support case, follow the instructions while ensuring you provide the following information:

    * Primary contact name, email, phone.
    * Name of your Dynamic Media account.
    * Specify that you want DASH, multiple caption and multiple audio track support enabled on your Dynamic Media account, on Experience Manager 6.5.
   
1. Adobe Customer Support adds you to the Customer Wait List based on the order in which requests are submitted.
1. When Adobe is ready to handle your request, Customer Support contacts you to coordinate and set a target date for enablement.
1. Customer support notifies you after completion.
1. Now, you can do either one of the following:

    * Create your [video viewer preset](/help/assets/managing-viewer-presets.md#creating-a-new-viewer-preset) as usual.
    * [Add multiple caption and audio tracks](#add-msma) to your video. -->




