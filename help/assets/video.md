---
title: Video in Dynamic Media
description: Leer hoe u met video werkt in Dynamic Media
mini-toc-levels: 3
uuid: 97f311a3-a227-479a-91bf-fb54ecd1a55d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 1103b849-0042-4e11-b170-38ee81dd0157
docset: aem65
feature: Beheer van bedrijfsmiddelen
role: User, Admin
exl-id: 28cf9e39-cab4-4278-b6c9-e84cc31964db
source-git-commit: b42a14729a88bda563b0773dac735ad569ad3097
workflow-type: tm+mt
source-wordcount: '11189'
ht-degree: 4%

---

# Video in Dynamic Media {#video}

In deze sectie wordt het werken met video in Dynamic Media beschreven.

## Snel starten: Video&#39;s {#quick-start-videos}

De volgende stapsgewijze workflowbeschrijving is ontworpen om u te helpen snel aan de slag te gaan met adaptieve videosets in Dynamic Media. Na elke stap, zijn er verwijzingen naar onderwerprubrieken waar u meer informatie kunt vinden.

>[!IMPORTANT]
>
>Voordat u in Dynamic Media met video gaat werken, moet u controleren of uw Adobe Experience Manager-beheerder Dynamic Media-Cloud Services al heeft ingeschakeld en geconfigureerd in de Dynamic Media-Scene7-modus of in de Dynamic Media-hybride modus.
>
>* Zie [Dynamic Media-Cloud Services configureren](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) in de modus Dynamic Media configureren - Scene7 en [Dynamic Media oplossen - Scene7-modus](/help/assets/troubleshoot-dms7.md).
   >
   >
* Zie [Dynamic Media-Cloud Services configureren](/help/assets/config-dynamic.md#configuring-dynamic-media-cloud-services) in Dynamic Media configureren - hybride modus.
>
>
Bekende problemen met het afspelen van video in Dynamic Media *alleen op Experience Manager 6.5.9.0*:
>
>* 

   <!-- CQDOC-18116 -->You cannot play video renditions from the asset's Details page on Experience Manager - Dynamic Media running in hybrid mode.
>* 

   <!-- CQDOC-18116 -->You cannot stream videos on Experience Manager - Dynamic Media running in hybrid mode.
>



1. **Upload uw Dynamic Media-** video&#39;s als volgt:

   * Maak uw eigen videocoderingsprofiel. U kunt ook gewoon het vooraf gedefinieerde _Adaptieve videocodering_-profiel gebruiken dat bij Dynamic Media wordt geleverd.

      * [Maak een videocoderingsprofiel](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * Meer informatie over [Aanbevolen werkwijzen voor videocodering](#best-practices-for-encoding-videos).
   * Koppel het videoverwerkingsprofiel aan een of meer mappen waar u de primaire bronvideo&#39;s gaat uploaden.

      * [Pas een videoprofiel toe op mappen](/help/assets/video-profiles.md#applying-a-video-profile-to-folders).
      * Meer informatie over [Aanbevolen werkwijzen voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](/help/assets/organize-assets.md).
      * Meer informatie over [Digitale elementen ordenen](/help/assets/organize-assets.md).
   * Upload uw primaire bronvideo&#39;s naar de mappen. U kunt videobestanden uploaden van maximaal 15 GB elk. Wanneer u video&#39;s aan de map toevoegt, worden deze gecodeerd volgens het videoverwerkingsprofiel dat u aan de map hebt toegewezen.

      * [Upload uw video](/help/assets/managing-video-assets.md#upload-and-preview-video-assets)&#39;s.
      * Meer informatie over [Ondersteunde invoerbestandsindelingen](/help/assets/assets-formats.md#supported-multimedia-formats).
   * Controleer hoe [video het coderen](#monitoring-video-encoding-and-youtube-publishing-progress) of van de activa of werkschemamening vordert.




1. **Voer een van de volgende handelingen uit om uw Dynamic Media-** video&#39;s te beheren:

   * Video-elementen organiseren, doorbladeren en zoeken

      * [Digitale ](/help/assets/organize-assets.md)
middelen organiserenMeer informatie over  [Aanbevolen werkwijzen voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](organize-assets.md)

      * [Video-](search-assets.md#custompredicates) apparatuur zoeken  [Zoeken in middelen](/help/assets/search-assets.md)
   * Video-elementen voorvertonen en publiceren

      * Bekijk de bronvideo en de gecodeerde vertoningen van de video samen met de bijbehorende miniaturen:
         [Voorvertoning van ](managing-video-assets.md#upload-and-preview-video-assets) videosor  [Voorvertoning van elementen weergeven](previewing-assets.md)
         [Video-uitvoeringen weergeven](video-renditions.md)
         [Video-uitvoeringen beheren](manage-assets.md#managing-renditions)

      * [Viewervoorinstellingen beheren](managing-viewer-presets.md)
      * [Elementen publiceren](publishing-dynamicmedia-assets.md)
   * Werken met videometagegevens

      * Bekijk de eigenschappen van een gecodeerde video-uitvoering, zoals framesnelheid, audio- en videobitsnelheid en codec:
         [Eigenschappen van video-uitvoering weergeven](video-renditions.md)

      * Bewerk de eigenschappen van video, zoals de titel, beschrijving en tags, aangepaste metagegevensvelden:
         [Video-eigenschappen bewerken](manage-assets.md#editing-properties)

      * [Metagegevens voor digitale elementen beheren](metadata.md)
      * [Metagegevensschema&#39;s](metadata-schemas.md)
   * Video&#39;s bekijken, goedkeuren en annoteren en volledige versiebeheer behouden

      * [Annoteer ](managing-video-assets.md#annotate-video-assets) videobestanden of  [Annoteer elementen](manage-assets.md#annotating)

      * [Een versie maken](manage-assets.md#asset-versioning)
      * [Workflows toepassen op ](assets-workflow.md) elementen of een workflow voor een element  [starten](manage-assets.md#starting-a-workflow-on-an-asset)

      * [Mapmiddelen controleren](bulk-approval.md)
      * [Projecten](../sites-authoring/projects.md)




1. **Publiceer uw Dynamic Media-** video&#39;s op een van de volgende manieren:

   * Als u Adobe Experience Manager gebruikt als beheersysteem voor webinhoud, kunt u video&#39;s rechtstreeks aan uw webpagina&#39;s toevoegen.

      * [Voeg video&#39;s toe aan uw webpagina](adding-dynamic-media-assets-to-pages.md)&#39;s.
   * Als u een systeem voor webcontentbeheer van derden gebruikt, kunt u video&#39;s koppelen aan of insluiten in uw webpagina&#39;s.

      * Video integreren met URL:
         [Koppel URL&#39;s aan uw webtoepassing](linking-urls-to-yourwebapplication.md).

      * Video integreren met gebruik van ingesloten code op webpagina:
         [Sluit de videoviewer in op een webpagina](embed-code.md).
   * [Publiceer video&#39;s naar YouTube](#publishing-videos-to-youtube).
   * [Genereer videoverslagen](#viewing-video-reports).

   * [Bijschriften toevoegen aan video](#adding-captions-to-video).



## Werken met video in Dynamic Media {#working-with-video-in-dynamic-media}

Video in Dynamic Media is een end-to-end oplossing waarmee u eenvoudig Adaptieve video van hoge kwaliteit kunt publiceren voor streaming op meerdere schermen, zoals desktopcomputers, iOS, Android™, BlackBerry® en mobiele Windows-apparaten. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. De desktopcomputer of het mobiele apparaat detecteert de beschikbare bandbreedte.

Op een mobiel iOS-apparaat detecteert het bijvoorbeeld een bandbreedte zoals 3G, 4G of Wi-Fi. Vervolgens wordt automatisch de naar rechts gecodeerde video geselecteerd bij de verschillende bitsnelheden van de video in de adaptieve videoset. De video wordt gestreamd naar desktops, mobiele apparaten of tablets.

Bovendien wordt de videokwaliteit automatisch dynamisch geschakeld als de netwerkomstandigheden veranderen op het bureaublad of op het mobiele apparaat. Ook, als een klant volledig-schermwijze op een Desktop ingaat, antwoordt de Adaptieve VideoReeks door een betere resolutie te gebruiken, verbeterend de het bekijken van de klant ervaring. Met Adaptieve videosets kunt u Dynamic Media-video op meerdere schermen en apparaten het best afspelen.

De logica die een videospeler gebruikt om te bepalen welke gecodeerde video moet worden afgespeeld of tijdens het afspelen moet worden geselecteerd, is gebaseerd op het volgende algoritme:

1. Videospeler laadt het eerste videofragment op basis van de bitsnelheid die het dichtst bij de waarde ligt die is ingesteld voor de &#39;initiële bitsnelheid&#39; in de speler zelf.
1. De videospelerschakelaars die op veranderingen in de bandbreedtesnelheid worden gebaseerd die de volgende criteria gebruiken:

   1. De speler kiest de hoogste bandbreedtestroom onder of gelijk aan de geschatte bandbreedte.
   1. De speler overweegt slechts 80% van de beschikbare bandbreedte. Als er echter een overstap wordt gemaakt, is het conservatiever bij slechts 70% om overschatting te voorkomen en onmiddellijk terug te keren.

Voor gedetailleerde technische informatie over het algoritme, zie [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Voor het beheren van afzonderlijke video- en adaptieve videosets wordt het volgende ondersteund:

* Video uploaden van diverse ondersteunde video-indelingen en audio-indelingen en video coderen naar MP4 H.264-indeling, zodat deze op meerdere schermen kan worden afgespeeld. U kunt vooraf gedefinieerde adaptieve videovoorinstellingen gebruiken, voorinstellingen voor één videocodering gebruiken of uw eigen codering aanpassen om de kwaliteit en de grootte van de video te bepalen.

   * Wanneer een adaptieve videoset wordt gegenereerd, bevat deze MP4-video&#39;s.
   * **Opmerking**: Master-/bronvideo&#39;s worden niet toegevoegd aan een adaptieve videoset.

* ondertiteling in alle HTML5-videoviewers.
* Video organiseren, doorbladeren en doorzoeken met volledige metagegevensondersteuning voor een efficiënt beheer van video-elementen.
* Lever Adaptieve videosets naar het web en naar desktops en mobiele apparaten, waaronder de iPhone, iPad, Android™, BlackBerry® en Windows-telefoon.

Adaptieve videostreaming wordt ondersteund op verschillende iOS-platforms. Zie [Referentiehandleiding voor Dynamic Media-viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html#video).

Dynamic Media ondersteunt het afspelen van mobiele video voor MP4 H.264-video. U kunt de apparaten van BlackBerry® vinden die dit videoformaat bij het volgende steunen: [Ondersteunde video-indelingen op BlackBerry®](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

U kunt de apparaten van Vensters vinden die dit videoformaat bij het volgende steunen: [Ondersteunde mediacodecs voor Windows Phone 8](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs)

* Speel de video terug gebruikend de Voorinstellingen van de VideoKijker van Dynamic Media, met inbegrip van het volgende:

   * Afzonderlijke videoviewers.
   * Gemengde Media-viewers die zowel video- als afbeeldingsinhoud combineren.

* Configureer videospelers om aan uw brandingbehoeften te voldoen.
* Video met een eenvoudige URL of insluitcode integreren in uw website, mobiele site of mobiele toepassing.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480) sample. -->

Zie ook [Viewers for Experience Manager Assets and Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc) and [Viewers for Experience Manager assets only](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only).

## Beste praktijken: De HTML5-videoviewer gebruiken {#best-practice-using-the-html-video-viewer}

De voorinstellingen van de Dynamic Media HTML5 Video-viewer zijn robuuste videospelers. U kunt ze gebruiken om veel voorkomende problemen te voorkomen die samenhangen met het afspelen van HTML5-video. En problemen die samenhangen met mobiele apparaten, zoals een gebrek aan adaptieve streaminglevering en een beperkt bereik van de desktopbrowser.

Aan de ontwerpkant van de speler, kunt u de functionaliteit van de videospeler ontwerpen gebruikend standaardhulpmiddelen van de Webontwikkeling. U kunt bijvoorbeeld de knoppen, besturingselementen en de achtergrond van een aangepaste posterafbeelding ontwerpen met HTML5 en CSS, zodat u uw klanten kunt bereiken met een aangepaste weergave.

Aan de afspeelzijde van de viewer wordt automatisch de videocapaciteit van de browser gedetecteerd. Vervolgens wordt de video afgespeeld met behulp van HLS (HTTP Live Streaming), ook wel adaptieve videostreaming genoemd. Als deze leveringsmethoden niet aanwezig zijn, wordt in plaats daarvan HTML5 progressief gebruikt.

Door het volgende te combineren in één speler:

* De mogelijkheid om de afspeelcomponenten te ontwerpen met HTML5 en CSS
* Ingesloten afspelen hebben
* Adaptieve en progressieve streaming gebruiken, afhankelijk van de browsermogelijkheden

U vergroot het bereik van uw rijke media-inhoud tot zowel gebruikers op het bureaublad als mobiele gebruikers en zorgt voor een gestroomlijnde videobeleving.

Zie ook [Informatie over HTML5 Viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only).

### Video afspelen op bureaubladcomputers en mobiele apparaten met de HTML5-videoviewer {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Voor adaptieve videostreaming op het bureaublad en mobiele apparaten zijn de video&#39;s die worden gebruikt voor het schakelen naar een andere bitsnelheid, gebaseerd op alle MP4-video&#39;s in de adaptieve videoset.

Het afspelen van video vindt plaats met behulp van HLS of progressieve videodownload. In eerdere versies van Experience Manager, zoals 6.0, 6.1 en 6.2, werden video&#39;s gestreamd via HTTP.

In Experience Manager 6.3 en hoger worden video&#39;s nu gestreamd via HTTPS (dat wil zeggen, HLS), omdat de URL van de DM-gatewayservice altijd HTTPS gebruikt. Dit standaardgedrag heeft geen gevolgen voor de klant. Videostreaming vindt altijd plaats via HTTPS, tenzij dit niet door de browser wordt ondersteund. (zie de volgende tabel). Op grond daarvan wordt met

* Als u een HTTPS-website met HTTPS-videostreaming hebt, is streaming prima.
* Als u een HTTP-website met HTTPS-videostreaming hebt, is streaming prima en zijn er geen problemen met gemengde inhoud in de webbrowser.

HLS is een Apple-standaard voor adaptieve videostreaming die het afspelen automatisch aanpast op basis van de capaciteit van de netwerkbandbreedte. Het laat de klant ook &quot;zoeken&quot;aan om het even welk punt in de video zonder de behoefte om op de rest van de video te wachten te downloaden.

Progressieve video wordt geleverd door de video lokaal te downloaden en op het desktopsysteem of mobiele apparaat van de gebruiker op te slaan.

In de volgende tabel worden het apparaat, de browser en de afspeelmethode beschreven van video&#39;s op bureaubladcomputers en mobiele apparaten met de Dynamic Media Video Viewer.

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
   <td>In Windows 8 en Windows 10 - Gebruik van HTTPS forceren wanneer om HLS wordt gevraagd. Bekende beperking: HTTP op HLS werkt niet in deze browser/werkend systeemcombinatie<br /> <br /> op Vensters 7 - Progressieve download. Gebruikt de standaardlogica voor het selecteren van het protocol HTTP versus HTTPS.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 23-44</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 45 of hoger</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Chroom</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Safari (Mac)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 6 of eerder)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 7 of hoger)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Android™ (standaardbrowser)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Safari (iOS)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (iOS)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>BlackBerry®</td>
   <td>HLS</td>
  </tr>
 </tbody>
</table>

## Architectuur van Dynamic Media-videooplossing {#architecture-of-dynamic-media-video-solution}

In de volgende afbeelding ziet u de algemene ontwerpworkflow voor video&#39;s die via DMGateway (in de Dynamic Media Hybrid-modus) worden geüpload en gecodeerd en die voor openbare consumptie beschikbaar worden gesteld.

![chlimage_1-427](assets/chlimage_1-427.png)

## Hybride publicatiearchitectuur voor video&#39;s {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Aanbevolen werkwijzen voor het coderen van video&#39;s {#best-practices-for-encoding-videos}

De **Dynamic Media Encode Video**-workflow codeert video als u Dynamic Media hebt ingeschakeld en videocloudservices hebt ingesteld. In deze workflow worden de historie en informatie over fouten van het workflowproces vastgelegd. Zie [Videocodering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress). Als u Dynamic Media hebt ingeschakeld en videocloudservices hebt ingesteld, wordt de **[!UICONTROL Dynamic Media Encode Video]**-workflow automatisch van kracht wanneer u een video uploadt. (Als u Dynamic Media niet gebruikt, wordt de **[!UICONTROL DAM Update Asset]**-workflow van kracht.)

<!-- DEAD The following are best-practice tips for encoding source video files.

For advice about video encoding, see [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en).

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en). -->

### Bronvideobestanden {#source-video-files}

Wanneer u een videobestand codeert, gebruikt u een videobronbestand van de hoogst mogelijke kwaliteit. Gebruik geen eerder gecodeerde videobestanden omdat deze bestanden al zijn gecomprimeerd en als u verder codeert, wordt een video van subparkwaliteit gemaakt.

In de volgende tabel worden de aanbevolen grootte, hoogte-breedteverhouding en minimale bitsnelheid beschreven die uw bronvideobestanden moeten hebben voordat u ze codeert:

| Grootte | Hoogte-breedteverhouding | Minimale bitsnelheid |
|--- |--- |--- |
| 1024 x 768 | 4:3 | 4500 kbps voor de meeste video&#39;s. |
| 1280 x 720 | 16:9 | 3000 - 6000 kbps, afhankelijk van de hoeveelheid beweging in de video. |
| 1920 x 1080 | 16:9 | 6000 - 8000 kbps, afhankelijk van de mate van beweging in de video. |

### De metagegevens van een bestand verkrijgen {#obtaining-a-file-s-metadata}

U kunt de metagegevens van een bestand verkrijgen door de metagegevens van het bestand te bekijken met een programma voor videobewerking of met een toepassing die is ontworpen voor het verkrijgen van metagegevens. Hieronder vindt u instructies voor het gebruik van MediaInfo, een toepassing van derden, voor het verkrijgen van de metagegevens van een videobestand:

1. Ga naar [MediaInfo Download](https://mediaarea.net/en/MediaInfo/Download).
1. Selecteer en download het installatieprogramma voor de GUI-versie en volg de installatie-instructies.
1. Klik na de installatie met de rechtermuisknop op het videobestand (alleen Windows) en selecteer MediaInfo, of open MediaInfo en sleep het videobestand naar de toepassing. U ziet alle metagegevens die aan het videobestand zijn gekoppeld, inclusief de breedte, hoogte en fps.

### Hoogte-breedteverhouding {#aspect-ratio}

Wanneer u een voorinstelling voor videocodering kiest of maakt voor uw primaire bronvideobestand, moet u ervoor zorgen dat de voorinstelling dezelfde hoogte-breedteverhouding heeft als het primaire bronvideobestand. De hoogte-breedteverhouding is de verhouding tussen de breedte en de hoogte van de video.

Als u de hoogte-breedteverhouding van een videobestand wilt bepalen, vraagt u de metagegevens van het bestand op en noteert u de breedte en hoogte van het bestand (zie De metagegevens van het bestand hierboven verkrijgen). Gebruik vervolgens deze formule om de hoogte-breedteverhouding te bepalen:

width/height = hoogte-breedteverhouding

In de volgende tabel wordt beschreven hoe de resultaten van de formule worden omgezet in algemene opties voor de hoogte-breedteverhouding:

| Resultaat van formule | Hoogte-breedteverhouding |
|--- |--- |
| 1,33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:9 |
| 0,56 | 9:16 |

Een video van 1440 x 1080 hoogte heeft bijvoorbeeld een hoogte-breedteverhouding van 1440/1080 of 1,33. In dit geval kiest u een voorinstelling voor videocodering met een hoogte-breedteverhouding van 4:3 om het videobestand te coderen.

### Bitsnelheid {#bitrate}

Bitsnelheid is de hoeveelheid gegevens die wordt gecodeerd om één seconde video af te spelen. De bitsnelheid wordt gemeten in kilobits per seconde (Kbps).

>[!NOTE]
>
>Omdat in alle codecs compressie met verlies wordt gebruikt, is bitsnelheid de belangrijkste factor voor de videokwaliteit. Bij compressie met verlies neemt de kwaliteit af naarmate u een videobestand comprimeert. Daarom zijn alle andere eigenschappen gelijk (de resolutie, framesnelheid en codec), hoe lager de bitsnelheid, hoe lager de kwaliteit van het gecomprimeerde bestand.

Wanneer u een codering voor bitsnelheden selecteert, kunt u kiezen uit twee typen:

* **[!UICONTROL Constant Bitrate Encoding]** (CBR) - Tijdens CBR-codering blijft de bitsnelheid of het aantal bits per seconde tijdens het coderingsproces ongewijzigd. Bij CBR-codering blijft de gegevenssnelheid van de set behouden voor de instelling van de gehele video. Bij CBR-codering worden mediabestanden niet geoptimaliseerd voor kwaliteit, maar wordt opslagruimte bespaard.
Gebruik CBR als uw video een vergelijkbaar bewegingsniveau in de gehele video bevat. CBR wordt meestal gebruikt voor het streamen van video-inhoud. Zie ook [Parameters voor aangepaste videocodering gebruiken](/help/assets/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Variable Bitrate Encoding]** (VBR) - VBR-codering past de gegevenssnelheid naar beneden en naar de bovenste limiet die u instelt, aan op basis van de gegevens die de compressor nodig heeft. Deze functionaliteit houdt in dat de bitsnelheid van het mediabestand tijdens een VBR-coderingsproces dynamisch wordt verhoogd of verlaagd, afhankelijk van de behoeften aan bitsnelheid van mediabestanden.
VBR duurt langer om te coderen maar produceert de gunstigste resultaten; de kwaliteit van het mediabestand is superieur. VBR wordt het meest meestal gebruikt voor http progressieve levering van video-inhoud.

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

**Met** resolutie worden de hoogte en breedte van een videobestand in pixels beschreven. De meeste bronvideo wordt opgeslagen met een hoge resolutie (bijvoorbeeld 1920 x 1080). Voor streamingdoeleinden wordt bronvideo gecomprimeerd tot een lagere resolutie (640 x 480 of lager).

Resolutie en gegevenssnelheid zijn twee geïntegreerde gekoppelde factoren die de videokwaliteit bepalen. Als u dezelfde videokwaliteit wilt behouden, geldt dat hoe hoger het aantal pixels in een videobestand (hoe hoger de resolutie), hoe hoger de gegevenssnelheid. Neem bijvoorbeeld het aantal pixels per frame in een videobestand met een resolutie van 320 x 240 en een resolutie van 640 x 480:

| Resolutie | Pixels per frame |
|--- |--- |
| 320 x 240 | 76 800 |
| 640 x 480 | 307 200 |

Het bestand van 640 x 480 heeft vier keer zoveel pixels per frame. Als u voor deze twee voorbeeldresoluties dezelfde gegevenssnelheid wilt bereiken, past u viermaal de compressie toe op het bestand van 640 x 480, waardoor de kwaliteit van de video kan afnemen. Daarom levert een videogegevenssnelheid van 250 Kbps beelden van hoge kwaliteit bij een resolutie van 320 x 240, maar niet bij een resolutie van 640 x 480.

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
| 480p | 480 | Standaardscherm |
| 720p | 720 | Groot scherm |
| 1080p | 1080 | High-definition groot scherm |

### FPS (frames per seconde) {#fps-frames-per-second}

In de Verenigde Staten en Japan wordt de meeste video opgenomen met een snelheid van 29,97 frames per seconde (fps); in Europa wordt de meeste video opgenomen met 25 fps. Film wordt opgenomen bij 24 fps.

Kies een voorinstelling voor videocodering die overeenkomt met de fps-snelheid van het primaire bronvideobestand. Als uw primaire bronvideo bijvoorbeeld 25 fps is, kiest u een coderingsvoorinstelling met 25 fps. Standaard wordt bij alle aangepaste codering de fps van het primaire bronvideobestand gebruikt. Daarom hoeft u de fps-instelling niet expliciet op te geven wanneer u een voorinstelling voor videocodering maakt.

### Afmetingen videocodering {#video-encoding-dimensions}

Voor optimale resultaten selecteert u de coderingsafmetingen, zodat de bronvideo een volledig veelvoud van alle gecodeerde video&#39;s is.

Als u deze verhouding wilt berekenen, deelt u de bronbreedte door de gecodeerde breedte om de breedteverhouding op te halen. Vervolgens deelt u de bronhoogte door de gecodeerde hoogte om de hoogte-breedteverhouding te bepalen.

Als de resulterende verhouding een geheel geheel getal is, betekent dit dat de video optimaal wordt geschaald. Als de resulterende verhouding geen geheel geheel getal is, is dit van invloed op de videokwaliteit doordat pixelartefacten overblijven op het scherm. Dit effect is vooral opvallend wanneer de video tekst heeft.

Stel dat uw bronvideo bijvoorbeeld 1920 x 1080 is. In de volgende tabel bieden de drie gecodeerde video&#39;s de optimale coderingsinstellingen.

| Videotype | Breedte x hoogte | Breedteverhouding | Hoogteverhouding |
|--- |--- |--- |--- |
| Bron | 1920 x 1080 | 1 | 3 |
| Gecodeerd | 960 x 540 | 2 | 2 |
| Gecodeerd | 640 x 360 | 3 | 3 |
| Gecodeerd | 480 x 270 | 4 | 4 |

### Gecodeerde videobestandsindeling {#encoded-video-file-format}

Dynamic Media raadt u aan voorinstellingen voor MP4 H.264-videocodering te gebruiken. Omdat MP4-bestanden de H.264-videocodec gebruiken, biedt deze video van hoge kwaliteit, maar met een gecomprimeerde bestandsgrootte.

## Video&#39;s publiceren naar YouTube {#publishing-videos-to-youtube}

U kunt video-elementen op locatie voor Experience Managers rechtstreeks publiceren naar een YouTube-kanaal dat u eerder hebt gemaakt.

Als u video-elementen naar YouTube wilt publiceren, stelt u Experience Manager Assets in met tags. U koppelt deze tags aan een YouTube-kanaal. Als de tag van een video-element overeenkomt met de tag van een YouTube-kanaal, wordt de video gepubliceerd naar YouTube. Publiceren naar YouTube vindt plaats samen met een normale publicatie van de video zolang een bijbehorende tag wordt gebruikt.

YouTube voert zijn eigen codering uit. Als zodanig wordt het oorspronkelijke videobestand dat naar de Experience Manager is geüpload, gepubliceerd naar YouTube in plaats van een video-uitvoering die door de codering van Dynamic Media is gemaakt. Hoewel het niet nodig is om video&#39;s te verwerken met Dynamic Media, wordt verwacht dat dit gebeurt voor het geval dat een viewer-voorinstelling nodig is voor het afspelen.

Wanneer u het videoverwerkingsprofiel overslaat en rechtstreeks naar YouTube publiceert, betekent dit gewoon dat uw video-element in Experience Manager Asset geen zichtbare miniatuur krijgt. Dit betekent ook dat als u in de uitvoermodi `dynamicmedia` of `dynamicmedia_scene7` uitvoert, video&#39;s die niet zijn gecodeerd, niet met een van de Dynamic Media-elementtypen werken.

Bij het publiceren van video-elementen naar YouTube-servers moeten de volgende taken worden uitgevoerd om een veilige en beveiligde server-naar-server verificatie met YouTube te garanderen:

1. [Google Cloud-instellingen configureren](#configuring-google-cloud-settings)
1. [Een YouTube-kanaal maken](#creating-a-youtube-channel)
1. [Codes toevoegen voor publicatie](#adding-tags-for-publishing)
1. [De YouTube-agent voor publicatiereplicatie inschakelen](#enabling-the-youtube-publish-replication-agent)
1. [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem)
1. [(Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Video&#39;s publiceren naar uw YouTube-kanaal](#publishing-videos-to-your-youtube-channel)
1. [(Optioneel) Controleer de gepubliceerde video op YouTube](/help/assets/video.md#optional-verifying-the-published-video-on-youtube)
1. [YouTube-URL&#39;s koppelen aan uw webtoepassing](#linking-youtube-urls-to-your-web-application)

U kunt de publicatie van video&#39;s ook [ongedaan maken om deze uit YouTube te verwijderen](#unpublishing-videos-to-remove-them-from-youtube).

### Google Cloud-instellingen configureren {#configuring-google-cloud-settings}

Als u naar YouTube wilt publiceren, hebt u een Google-account nodig. Als u een GMAIL-account hebt, hebt u al een Google-account; als u geen Google-account hebt, kunt u er eenvoudig een maken. U hebt het account nodig omdat u aanmeldingsgegevens nodig hebt om video-elementen naar YouTube te publiceren. Als u al een account hebt gemaakt, slaat u deze taak over en gaat u direct door naar [Een YouTube-kanaal maken](#creating-a-youtube-channel).

Het account dat wordt gebruikt met Google Cloud en het Google-account dat wordt gebruikt voor YouTube, hoeft niet hetzelfde te zijn.

Google wijzigt regelmatig zijn gebruikersinterface. De stappen voor het publiceren van video&#39;s naar YouTube kunnen dan ook enigszins afwijken van wat hieronder wordt beschreven. Dit voorbehoud geldt ook voor YouTube wanneer u probeert te controleren of er video&#39;s naar worden geüpload.

>[!NOTE]
>
>De volgende stappen waren correct op het moment van schrijven. Google werkt zijn websites echter regelmatig en zonder kennisgeving bij. Daarom kunnen deze stappen iets anders zijn.

Google Cloud-instellingen configureren:

1. Maak een Google-account.
   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   Als u al een Google-account hebt, gaat u verder met de volgende stap.

1. Ga naar [https://cloud.google.com/](https://cloud.google.com/).
1. Klik in de rechterbovenhoek op de Google Cloud-pagina op **[!UICONTROL Console]**.

   Indien nodig **[!UICONTROL Sign in]** met de referenties van uw Google-account om de optie **[!UICONTROL Console]** weer te geven.

1. Klik op de dashboardpagina rechts van **[!UICONTROL Google Cloud Platform]** op de vervolgkeuzelijst Project om het dialoogvenster Een project selecteren te openen.
1. Tik in het dialoogvenster Een project selecteren op **[!UICONTROL New Project]**.

   ![6_5_gogleaccount-newproject](assets/6_5_googleaccount-newproject.png)

1. In het Nieuwe de dialoogvakje van het Project, op het gebied van de Naam van het Project, typ de naam van uw nieuw project.

   Uw project-id is gebaseerd op uw projectnaam. Kies daarom de projectnaam zorgvuldig; het kan na het creëren niet worden veranderd. U moet dezelfde project-id opnieuw invoeren wanneer u YouTube later instelt in Experience Manager. Ik zou het willen afschrijven.

1. Klik op **[!UICONTROL Create]**.

1. Voer een van de volgende handelingen uit:

   * Tik op het dashboard van uw project op de Aan de slag-kaart op **[!UICONTROL Explore and enable APIs]**.
   * Tik op het dashboard van uw project op de API&#39;s-kaart op **[!UICONTROL Go to APIs overview]**.

   ![6_5_googleaccount-apis-enable2](assets/6_5_googleaccount-apis-enable2.png)

1. Tik boven aan de pagina met API&#39;s en services op **[!UICONTROL Enable APIs and Services]**.
1. Tik op de pagina API-bibliotheek links onder **[!UICONTROL Category]** op **[!UICONTROL YouTube]**. Tik rechts van de pagina op **[!UICONTROL YouTube Data API]**.
1. Tik op de v3-pagina YouTube Data API op **[!UICONTROL Enable]**.

   ![6_5_googleaccount-apis-enable3](assets/6_5_googleaccount-apis-enable3.png)

1. U hebt referenties nodig om de API te gebruiken. Klik zo nodig op **[!UICONTROL Create Credentials]**.

   ![6_5_googleaccount-apis-createcredentials](assets/6_5_googleaccount-apis-createcredentials.png)

1. Ga als volgt te werk op de pagina **[!UICONTROL Add credentials to your project]**:

   * Selecteer in de vervolgkeuzelijst **[!UICONTROL Which API are you using?]** de optie **[!UICONTROL YouTube Data API v3]**.

   * Selecteer in de vervolgkeuzelijst **[!UICONTROL Where are you calling the API from?]** de optie **[!UICONTROL Web Server (for example, node.js, Tomcat)]**

   * Tik in de vervolgkeuzelijst **[!UICONTROL What data are you accessing?]** op **[!UICONTROL User data]**.

   ![6_5_googleaccount-apis-createcredentials2](assets/6_5_googleaccount-apis-createcredentials2.png)

1. Tik op **[!UICONTROL What credentials do I need?]**
1. Voer op de pagina **[!UICONTROL Add credentials to your project]** in stap 2 onder de kop **[!UICONTROL Create an OAuth 2.0 client ID]** in het veld Naam desgewenst een unieke naam in. U kunt ook de standaardnaam gebruiken die door Google is opgegeven.
1. Voer onder de kop **[!UICONTROL Authorized JavaScript origins]** in het tekstveld het volgende pad in, waarbij u uw eigen domein- en poortnummer in het pad vervangt, en druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>`

   Bijvoorbeeld, `https://1a2b3c.mycompany.com:4321`

   **Opmerking**: Het bovenstaande padvoorbeeld is alleen bedoeld voor demonstratiedoeleinden.

   ![6_5_googleaccount-apis-createcredentials-oauth](assets/6_5_googleaccount-apis-createcredentials-oauth.png)

1. Voer onder de kop **[!UICONTROL Authorized redirect URIs]** in het tekstveld het volgende pad in, waarbij u uw eigen domein- en poortnummer in het pad vervangt, en druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Bijvoorbeeld, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **Opmerking**: Het bovenstaande padvoorbeeld is alleen bedoeld voor demonstratiedoeleinden.

1. Klik op **[!UICONTROL Create OAuth client ID]**.
1. Selecteer op de pagina **[!UICONTROL Add credentials to your project]** in stap 3 onder de kop **[!UICONTROL Set up the OAuth 2.0 consent screen]** het e-mailadres van Gmail dat u momenteel gebruikt.

   ![6_5_googleaccount-apis-createcredentials-consentscreen](assets/6_5_googleaccount-apis-createcredentials-consentscreen.png)

1. Voer onder de kop **[!UICONTROL Product name shown to users]** in het tekstveld in wat u wilt weergeven op het instemmingsscherm.

   Het toestemmingsscherm wordt getoond aan de beheerder van de Experience Manager wanneer zij aan YouTube voor authentiek verklaren; Experience Manager neemt contact op met YouTube voor toestemming.

1. Klik op **[!UICONTROL Continue]**.
1. Tik op de pagina Referenties aan uw project toevoegen in stap 4 onder de kop **[!UICONTROL Download credentials]** op **[!UICONTROL Download]**.

   ![6_5_googleaccount-apis-createcredentials-downloadcredentials](assets/6_5_googleaccount-apis-createcredentials-downloadcredentials.png)

1. Sla het `client_id.json`-bestand op.

   U hebt dit gedownloade json-bestand nodig wanneer u YouTube later instelt in Adobe Experience Manager.

1. Klik op **[!UICONTROL Done]**.

   Log uit op je Google account. Maak nu een YouTube-kanaal.

### Een YouTube-kanaal maken {#creating-a-youtube-channel}

Voor het publiceren van video&#39;s naar YouTube hebt u een of meer kanalen nodig. Als u al een YouTube-kanaal hebt gemaakt, kunt u deze taak overslaan en naar [Codes toevoegen voor publicatie](/help/assets/video.md#adding-tags-for-publishing) gaan.

>[!WARNING]
>
>Zorg ervoor dat u al een of meer kanalen hebt ingesteld in YouTube *before* u kanalen toevoegt onder YouTube Settings in Experience Manager (zie [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem) hieronder). Als u een of meer kanalen niet instelt, wordt u niet gewaarschuwd voor niet-bestaande kanalen. Google-verificatie vindt echter nog steeds plaats wanneer u een kanaal toevoegt, maar er is geen optie om te kiezen welk kanaal de video wordt verzonden.

**Een YouTube-kanaal maken:**

1. Ga naar [https://www.youtube.com](https://www.youtube.com/) en meld u aan met de referenties van uw Google-account.
1. Klik in de rechterbovenhoek van de YouTube-pagina op de profielafbeelding (kan ook als een letter binnen een cirkel met effen kleuren worden weergegeven) en klik vervolgens op **[!UICONTROL YouTube settings]** (pictogram met ronde versnelling).
1. Voor de pagina van het Overzicht, onder de Extra rubriek van Eigenschappen, klik **[!UICONTROL See all my channels or create a new channel]**.
1. Voor de pagina van Kanalen, klik **[!UICONTROL Create a new channel]**.
1. Voer op de pagina Brand Account in het veld Brand Account Name een bedrijfsnaam of een andere kanaalnaam in die u kiest waar u de video-elementen wilt publiceren en klik vervolgens op **[!UICONTROL Create]**.

   Onthoud de naam die u hier invoert, omdat u deze opnieuw moet invoeren wanneer u YouTube instelt in Experience Manager.

1. (Optioneel) Voeg desgewenst meer kanalen toe.

   Voeg nu codes toe voor publicatie.

### Codes toevoegen voor publicatie {#adding-tags-for-publishing}

Als u video&#39;s naar YouTube wilt publiceren, koppelt de Experience Manager de tags aan een of meer YouTube-kanalen. Zie [Codes beheren](/help/sites-administering/tags.md) als u codes wilt toevoegen voor publicatie.

Of, als u van plan bent om de standaardmarkeringen in Experience Manager te gebruiken, kunt u deze taak overslaan en naar [Enable YouTube Publish replicator](#enabling-the-youtube-publish-replication-agent) gaan.

### De YouTube Publish Replication-agent inschakelen {#enabling-the-youtube-publish-replication-agent}

Tik op **[!UICONTROL Test Connection]** als u de YouTube Publish Replication Agent hebt ingeschakeld en u de verbinding met het Google Cloud-account wilt testen. Op het tabblad Browser worden de verbindingsresultaten weergegeven. Als u YouTube-kanalen hebt toegevoegd, wordt een lijst met kanalen weergegeven als onderdeel van de test.

1. Klik in de linkerbovenhoek van de Experience Manager op het logo van de Experience Manager en klik vervolgens in de linkertrack op **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. Voor de Agenten van de pagina van de Auteur, klik **[!UICONTROL YouTube Publish]**.
1. Klik rechts van Instellingen op de werkbalk op **[!UICONTROL Edit]**.
1. Schakel het selectievakje **[!UICONTROL Enabled]** in zodat u de replicatieagent kunt inschakelen.
1. Klik op **[!UICONTROL OK]**.

   Stel nu YouTube in Experience Manager in.

### YouTube instellen in Experience Manager {#setting-up-youtube-in-aem}

Vanaf Experience Manager 6.4 is een nieuwe aanraakgebruikersinterfacemethode geïntroduceerd om YouTube-publicaties in Experience Manager in te stellen. Op basis van de geïnstalleerde Experience Manager die u gebruikt, voert u een van de volgende handelingen uit:

* Om YouTube in Experience Manager vóór 6.4 te vormen, zie [Opstelling YouTube in Experience Manager vóór 6.4](/help/assets/video.md#setting-up-youtube-in-aem-before).
* Om YouTube in Experience Manager 6.4 of later te vormen, zie [Opstelling YouTube in Experience Manager 6.4 en later](#setting-up-youtube-in-aem-and-later).

#### YouTube instellen in Experience Manager 6.4 en hoger {#setting-up-youtube-in-aem-and-later}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.
1. Tik in de linkerbovenhoek op het logo van de Experience Manager en tik **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Cloud Services]** > **[!UICONTROL YouTube Publishing Configuration]** in de linkerrails.
1. Tik **[!UICONTROL global]** (niet selecteren).

1. Tik in de rechterbovenhoek van de globale pagina op **[!UICONTROL Create]**.
1. Voer op de pagina YouTube-configuratie maken onder Google Cloud-platforminstellingen in het veld **[!UICONTROL Application Name]** de Google-project-id in.

   U hebt de project-id opgegeven toen u aanvankelijk eerder Google Cloud-instellingen had geconfigureerd.
Laat de pagina YouTube-configuratie maken open. zo kom je er nog op terug .

   ![6_5_youtubepublish-createyoutubeconfiguration](assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder hebt gedownload en opgeslagen in de taak [Google Cloud-instellingen configureren](/help/assets/video.md#configuring-google-cloud-settings).
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]**.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Tik op **[!UICONTROL Add Channel]**.
1. Voer in het veld Kanaalnaam de naam in van het kanaal dat u eerder in de taak **[!UICONTROL Adding one or more channels to YouTube]** hebt gemaakt.

   U kunt desgewenst een beschrijving toevoegen.

1. Tik op **[!UICONTROL Add]**.
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project-id en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet. het is geen kanaal .
   * Tik op de volgende pagina op **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Tik op **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Tik op de pagina Cloud Services > YouTube op het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Tik op het pictogram van de vervolgkeuzelijst (ondersteboven), zodat u de lijst met beschikbare labels in de Experience Manager kunt weergeven.
1. Tik op een of meer tags zodat u deze kunt toevoegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en tikt u op **[!UICONTROL X]**.

1. Tik **[!UICONTROL Save]** wanneer u alle gewenste tags hebt toegevoegd.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

#### YouTube instellen in Experience Manager vóór 6.4 {#setting-up-youtube-in-aem-before}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.

1. Tik in de linkerbovenhoek op het logo van de Experience Manager en tik **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Tik onder de kop Services van derden onder YouTube op **[!UICONTROL Configure now]**.
1. Voer in het dialoogvenster Configuratie maken een titel (verplicht) en een naam (optioneel) in de desbetreffende velden in.
1. Tik op **[!UICONTROL Create]**.
1. Voer in het veld **[!UICONTROL Application Name]** in het dialoogvenster YouTube-accountinstellingen de Google-project-id in.

   U hebt de project-id opgegeven wanneer u eerder [Google Cloud-instellingen hebt geconfigureerd](/help/assets/video.md#configuring-google-cloud-settings).
Laat het dialoogvenster YouTube-accountinstellingen open. daar kom je zo op terug .

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder hebt gedownload en opgeslagen in de taak Google Cloud-instellingen configureren.
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Tik op **[!UICONTROL OK]**.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Tik rechts van **[!UICONTROL Available Channels]** op **+** (plusteken).
1. Voer in het veld Titel in het dialoogvenster YouTube-kanaalinstellingen de naam in van het kanaal dat u eerder in de taak **[!UICONTROL Adding one or more channels to YouTube]** hebt gemaakt.

   U kunt desgewenst een beschrijving toevoegen.

1. Tik op **[!UICONTROL OK]**.
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project-id en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet. het is geen kanaal .
   * Tik op de volgende pagina op **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Tik op **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Tik op de pagina Cloud Services > YouTube op het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Tik op het pictogram van de vervolgkeuzelijst (ondersteboven), zodat u de lijst met beschikbare labels in de Experience Manager kunt weergeven.
1. Tik op een of meer tags zodat u deze kunt toevoegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en tikt u op **X**.

1. Tik **[!UICONTROL OK]** wanneer u alle gewenste tags hebt toegevoegd.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

### (Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

U kunt desgewenst de instelling van YouTube-eigenschappen automatiseren bij het uploaden van uw video&#39;s door een verwerkingsprofiel voor metagegevens in Experience Manager te maken.

Als u het verwerkingsprofiel voor metadata wilt maken, kopieert u eerst waarden uit de velden **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]** en **[!UICONTROL Choices]** die te vinden zijn in de metadataschema&#39;s voor video. Vervolgens kunt u het verwerkingsprofiel voor YouTube-videometagegevens samenstellen door deze waarden eraan toe te voegen.

U kunt als volgt de standaardeigenschappen van YouTube voor uw geüploade video&#39;s automatiseren:

1. Tik in de linkerbovenhoek op het logo van de Experience Manager en klik vervolgens in de linkertrack op **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. Klik op **[!UICONTROL default]**. (Voeg geen vinkje toe aan het selectievak links van &quot;standaard&quot;.)
1. Schakel op de pagina **[!UICONTROL default]** het vakje links van **[!UICONTROL video]** in en tik **[!UICONTROL Edit]**.
1. Tik op het tabblad **[!UICONTROL Advanced]** op de pagina Metagegevensschema-editor.
1. Klik onder de kop YouTube-publicatie op **[!UICONTROL YouTube Category]**.
1. Voer rechts van de pagina onder het tabblad **[!UICONTROL Settings]** de volgende handelingen uit:

   * Selecteer en kopieer de waarde in het tekstveld **[!UICONTROL Map to property]**.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Selecteer en kopieer onder **[!UICONTROL Choices]** de standaardwaarde die u wilt gebruiken (zoals Personen en blogs of Wetenschap en Technologie).
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Tik onder de kop YouTube Publishing op **[!UICONTROL YouTube Privacy]**.
1. Voer rechts van de pagina onder het tabblad **[!UICONTROL Settings]** de volgende handelingen uit:

   * Selecteer en kopieer de waarde in het tekstveld **[!UICONTROL Map to property]**.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Selecteer en kopieer onder **[!UICONTROL Choices]** de standaardwaarde die u wilt gebruiken. De keuzen zijn gegroepeerd in twee. Het onderste veld in het paar is de standaardwaarde die u wilt kopiëren, bijvoorbeeld public, unlist of private.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Klik in de rechterbovenhoek van de pagina van de Editor van het metagegevensschema op **[!UICONTROL Cancel]**.
1. Tik in de linkerbovenhoek van de Experience Manager op het logo van de Experience Manager en klik vervolgens in de linkerspoorstaaf op **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]**.

1. Klik in de rechterbovenhoek van de pagina Metagegevensprofielen op **[!UICONTROL Create]**.
1. Voer in het tekstveld **[!UICONTROL Profile title]** in het dialoogvenster Metadataprofiel toevoegen de naam `YouTube Video` in en klik vervolgens op **[!UICONTROL Create]**.
1. Klik op het tabblad **[!UICONTROL Advance]** op de pagina Metagegevensprofieleditor.
1. Voeg de gekopieerde YouTube Publishing-waarden als volgt toe aan het profiel:

   * Klik rechts van de pagina op het tabblad **[!UICONTROL Build Form]**.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en zet deze neer in het formuliergebied.
   * (Optioneel) Klik op **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ `YouTube Publishing` rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label.
   * Klik op de tab **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en zet deze onder de kop **[!UICONTROL YouTube Publishing]** die u hebt gemaakt.

   * Klik **[!UICONTROL Field Label]** zodat wordt de component geselecteerd.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Voeg de gekopieerde YouTube-privacywaarden als volgt toe aan het profiel:

   * Klik rechts van de pagina op het tabblad **[!UICONTROL Build Form]**.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en zet deze neer in het formuliergebied.
   * (Optioneel) Klik op **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ `YouTube Privacy` rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label.
   * Klik op het tabblad **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en zet deze onder de **[!UICONTROL YouTube Privacy]** kop die u hebt gemaakt.

   * Klik **[!UICONTROL Field Label]** zodat wordt de component geselecteerd.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]**.
1. Pas het metagegevensprofiel voor YouTube Publishing toe op de mappen waarin u video&#39;s gaat uploaden. U moet zowel het profiel Metagegevens als het videoprofiel hebben ingesteld.

   Zie [Metadataprofielen](/help/assets/metadata-config.md#metadata-profiles) en [Videoprofielen](/help/assets/video-profiles.md).

### Video&#39;s publiceren naar uw YouTube-kanaal {#publishing-videos-to-your-youtube-channel}

Nu associeert u de markeringen die u eerder aan videoactiva toevoegde. Dit proces stelt de Experience Manager in kennis van de elementen die naar uw YouTube-kanaal moeten worden gepubliceerd.

>[!NOTE]
>
>Als u de functie Dynamic Media - Scene7 gebruikt, wordt deze functie niet automatisch naar YouTube gepubliceerd. Als de Dynamic Media-Scene7-modus is ingesteld, zijn er twee publicatieopties waaruit u kunt kiezen: **[!UICONTROL Immediately]** of **[!UICONTROL Upon Activation]**.
>
>**[!UICONTROL Publish Immediately]** betekent dat het geüploade element-nadat het met IPS wordt gesynchroniseerd-automatisch aan het leveringssysteem wordt gepubliceerd. Dat geldt voor Dynamic Media, maar dat geldt niet voor YouTube. Als u wilt publiceren naar YouTube, moet u publiceren als Experience Manager Auteur.

>[!NOTE]
>
>Om inhoud van YouTube te publiceren, gebruikt de Experience Manager **[!UICONTROL Publish to YouTube]** werkschema, dat u vooruitgang laat controleren en om het even welke mislukkingsinformatie bekijken.
>
>Zie [Videocodering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).
>
>Voor gedetailleerdere voortgangsgegevens kunt u het YouTube-logboek onder replicatie controleren. Houd er echter rekening mee dat voor dergelijke bewaking beheerderstoegang vereist is.

**Video&#39;s publiceren naar uw YouTube-kanaal:**

1. Navigeer in Experience Manager naar een video-element dat u naar het YouTube-kanaal wilt publiceren.
1. Selecteer het video-element (de adaptieve videoset).
1. Klik op **[!UICONTROL Properties]** op de werkbalk.
1. Klik op het tabblad Standaard onder de kop Metagegevens op **[!UICONTROL Open Selection Dialog]** rechts van het veld Codes.
1. Navigeer op de pagina Codes selecteren naar de gewenste codes en selecteer een of meer codes.

   Vergeet niet dat de tags moeten worden gekoppeld aan het YouTube-kanaal.

1. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Select]**.
1. Klik in de rechterbovenhoek van de eigenschappenpagina van de video op **[!UICONTROL Save and Close]**.
1. Klik op **[!UICONTROL Quick Publish]** op de werkbalk.

   Zie ook [Publicatiebeheer gebruiken met Experience Manager Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html).

   U kunt desgewenst de gepubliceerde video op uw YouTube-kanaal verifiëren.

### (Optioneel) Controleer de gepubliceerde video op YouTube {#optional-verifying-the-published-video-on-youtube}

U kunt optioneel de voortgang van het publiceren van YouTube (of het ongedaan maken van het publiceren) volgen.

Zie [Videocodering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

De het publiceren tijden kunnen zeer afhankelijk van talrijke factoren variëren die het formaat van uw primaire bronvideo, dossiergrootte, en uploadverkeer omvatten. Het publicatieproces kan een paar minuten tot enkele uren duren. Bovendien worden indelingen met een hogere resolutie veel langzamer gerenderd. Het duurt bijvoorbeeld langer om 720p en 1080p weer te geven dan 480p.

Na acht uur als er nog een statusbericht wordt weergegeven met de tekst **[!UICONTROL Uploaded (processing, please wait)]**. Verwijder de video van de site en upload deze opnieuw.

### YouTube-URL&#39;s koppelen aan uw webtoepassing {#linking-youtube-urls-to-your-web-application}

U kunt een YouTube URL-tekenreeks verkrijgen die door Dynamic Media wordt gegenereerd nadat u de video hebt gepubliceerd. Wanneer u de YouTube-URL kopieert, wordt deze op het Klembord gedownload, zodat u deze indien nodig kunt plakken naar pagina&#39;s in uw website of toepassing.

>[!NOTE]
>
>De YouTube-URL kan pas worden gekopieerd nadat u het video-element naar YouTube hebt gepubliceerd.

**YouTube-URL&#39;s koppelen aan uw webtoepassing:**

1. Navigeer naar het *YouTube gepubliceerde* videoelement waarvan u de URL wilt kopiëren en selecteer het.

   Onthoud dat YouTube-URL&#39;s alleen beschikbaar zijn om *after* te kopiëren. De video-elementen zijn eerst *gepubliceerd* naar YouTube.

1. Klik op **[!UICONTROL Properties]** op de werkbalk.
1. Klik op het tabblad **[!UICONTROL Advanced]**.
1. Selecteer onder YouTube Publishing in de URL-lijst van YouTube de URL-tekst die u naar uw webbrowser wilt kopiëren om een voorvertoning van het element weer te geven of om deze toe te voegen aan uw pagina met webinhoud.

### Publiceren van video&#39;s ongedaan maken zodat u deze kunt verwijderen uit YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Wanneer u de publicatie van een video-element in Experience Manager ongedaan maakt, wordt de video verwijderd uit YouTube.

>[!CAUTION]
>
>Als u een video rechtstreeks uit YouTube verwijdert, is de Experience Manager zich hiervan niet bewust en gedragen deze zich alsof de video nog steeds naar YouTube wordt gepubliceerd. Publiceer de publicatie van een video-element vanuit YouTube altijd ongedaan als Experience Manager.

>[!NOTE]
>
>Om inhoud uit YouTube te verwijderen, gebruikt Experience Manager **[!UICONTROL Unpublish from YouTube]** werkschema, dat u vooruitgang laat controleren en om het even welke mislukkingsinformatie bekijken.
>
>Zie [Videocodering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

**Publiceren van video&#39;s ongedaan maken om deze uit YouTube te verwijderen:**

1. Navigeer naar de video-elementen waarvan u de publicatie via uw YouTube-kanaal wilt ongedaan maken.
1. Selecteer in de modus voor middelenselectie een of meer gepubliceerde video-elementen.
1. Klik op **[!UICONTROL Manage Publication]** op de werkbalk. Tik op het pictogram met drie puntjes (. . .) op de werkbalk wordt **[!UICONTROL Manage Publication]** geopend.
1. Tik op **[!UICONTROL Unpublish]** op de pagina Publicatie beheren.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Next]**.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Unpublish]**.

## Video-codering en YouTube-publicatievoortgang controleren {#monitoring-video-encoding-and-youtube-publishing-progress}

Wanneer u een nieuwe video uploadt naar een map waarop videocodering is toegepast, of wanneer u uw video publiceert naar YouTube, kunt u controleren hoe de videocodering/YouTube-publicatie vordert. Werkelijke vorderingen bij het publiceren in YouTube zijn alleen beschikbaar via de logboeken. De mislukking of het succes ervan wordt echter vermeld op aanvullende manieren die in de volgende procedure worden beschreven. Bovendien ontvangt u e-mailmeldingen wanneer een publicatieworkflow of videocodering van YouTube is voltooid of onderbroken.

### Voortgang van controle {#monitoring-progress}

1. Voortgang videocodering weergeven in map met elementen:

   * In de kaartweergave wordt de voortgang van de videocodering met een percentage weergegeven op het element. Als er een fout optreedt, wordt deze informatie ook weergegeven op het element.

   ![chlimage_1-429](assets/chlimage_1-429.png)

   * In de lijstweergave wordt de voortgang van de videocodering weergegeven in de kolom **[!UICONTROL Processing Status]**. Als er een fout is, wordt dit bericht in dezelfde kolom weergegeven.

   ![chlimage_1-430](assets/chlimage_1-430.png)

   Deze kolom wordt niet standaard weergegeven. Als u de kolom wilt inschakelen, selecteert u **[!UICONTROL View Settings]** in het vervolgkeuzemenu Weergaven en voegt u de kolom **[!UICONTROL Processing Status]** toe en tikt of klikt u op **[!UICONTROL Update]**.

   ![chlimage_1-431](assets/chlimage_1-431.png)

1. De voortgang van de elementen weergeven. Wanneer u op een element tikt of erop klikt, opent u het keuzemenu en selecteert u **[!UICONTROL Timeline]**. Selecteer **[!UICONTROL Workflows]** om deze te beperken tot workflowactiviteiten zoals coderen of YouTube-publicatie.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Workflowinformatie, zoals codering, wordt weergegeven in de tijdlijn. Voor YouTube-publicatie bevat de tijdlijn van de workflow ook de naam van het YouTube-kanaal en de YouTube-video-URL. Bovendien ziet u eventuele foutmeldingen in de tijdlijn van de workflow nadat het publiceren is voltooid.

   >[!NOTE]
   >
   >Het kan lang duren voordat foutberichten/foutberichten definitief worden opgenomen vanwege meerdere workflowconfiguraties op **[!UICONTROL retries]**, **[!UICONTROL retry delay]** en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >    * Configuratie Apache Sling-taakwachtrij
   >    * Adobe Granite-workflow - Externe verwerking van taken
   >    * Tijdelijke wachtrij voor Granite Workflow

   >
   >U kunt de eigenschappen **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** in deze configuraties aanpassen.

1. Zie Workflowinstanties beschikbaar via **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instances]** voor actieve workflows.

   >[!NOTE]
   >
   >U hebt beheerrechten nodig om toegang te krijgen tot het menu **[!UICONTROL Tools]**.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Selecteer de instantie en tik **[!UICONTROL Open History]**.

   ![chlimage_1-434](assets/chlimage_1-434.png)

   Vanuit het gebied Workflowinstanties kunt u workflows ook opschorten, beëindigen of hernoemen. Zie [Workflows beheren](/help/sites-administering/workflows-administering.md) voor meer informatie.

1. Voor mislukte taken raadpleegt u de beschikbare workflowfouten in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Failures]**. De lijst **[!UICONTROL Workflow Failure]** bevat alle mislukte workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerrechten nodig om toegang te krijgen tot het menu **[!UICONTROL Tools]**.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Het kan lang duren voordat het foutbericht eindelijk wordt opgenomen vanwege meerdere workflowconfiguraties op **[!UICONTROL retries]**, **[!UICONTROL retry delay]** en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >
   >
   >    * Configuratie Apache Sling-taakwachtrij
   >    * Adobe Granite-workflow - Externe verwerking van taken
   >    * Tijdelijke wachtrij voor Granite Workflow

   >
   >
   >U kunt de eigenschappen **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** in deze configuraties aanpassen.

1. Zie Workflowarchief in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archive]** voor voltooide workflows. In **[!UICONTROL Workflow Archive]** vindt u een lijst met alle voltooide workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerrechten nodig om toegang te krijgen tot het menu **[!UICONTROL Tools]**.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. U ontvangt e-mailmeldingen over afgebroken of mislukte workflowtaken. Deze e-mailberichten kunnen door een beheerder worden geconfigureerd. Zie [E-mailmeldingen configureren](#configuring-e-mail-notifications).

#### E-mailmeldingen configureren {#configuring-e-mail-notifications}

>[!NOTE]
>
>U hebt beheerrechten nodig om toegang te krijgen tot het menu **[!UICONTROL Tools]**.

Hoe u een melding configureert, hangt af van het feit of u meldingen voor coderingstaken of YouTube-publicatietaken wilt:

* Voor coderingsbanen, kunt u tot de configuratiepagina voor alle Experience Manager werkschema e-mailberichten op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** en door te zoeken naar **[!UICONTROL Day CQ Workflow Email Notification Service]** toegang hebben. Zie [E-mailmelding configureren in Experience Manager](/help/sites-administering/notification.md). U kunt de selectievakjes voor **[!UICONTROL Notify on Abort]** of **[!UICONTROL Notify on Complete]** dienovereenkomstig selecteren of wissen.

* Ga als volgt te werk voor publicatietaken in YouTube:

1. Tik in Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer **[!UICONTROL Publish to YouTube]** op de pagina Workflowmodellen en tik **[!UICONTROL Edit]** op de werkbalk.
1. Tik in de rechterbovenhoek van de workflowpagina Publiceren naar YouTube op **[!UICONTROL Edit]**.
1. Houd de muisaanwijzer boven op de YouTube-component Upload en tik één keer om de inlinewerkbalk weer te geven.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. Tik op de inlinewerkbalk op het configuratiepictogram (moersleutel). Klik op het tabblad **[!UICONTROL Arguments]**.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. Tik in het dialoogvenster YouTube Upload Process - Step Properties op het tabblad **[!UICONTROL Arguments]**.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. U kunt de volgende selectievakjes in- of uitschakelen:

   * Start publiceren
   * Publicatiefout
   * Voltooien publiceren - bevat informatie over kanalen en URL&#39;s

   Als u een selectievakje wist, ontvangt u geen e-mailbericht van de publicatieworkflow van YouTube.

   >[!NOTE]
   >
   >Deze e-mailberichten zijn specifiek voor YouTube en vormen een aanvulling op de algemene e-mailmeldingen over de workflow. Dientengevolge, kunt u twee reeksen e-mailbericht ontvangen - het generische bericht beschikbaar in **[!UICONTROL Day CQ Workflow Email Notification Service]** en één specifiek voor YouTube afhankelijk van uw configuratiemontages.

1. Tik op het pictogram **[!UICONTROL Done]** (vinkje) wanneer u klaar bent, in de rechterbovenhoek van het dialoogvenster.
1. Tik op de workflowpagina Publiceren naar YouTube in de rechterbovenhoek op **[!UICONTROL Sync]**.

## Videorapporten weergeven {#viewing-video-reports}

>[!NOTE]
>
>Videorapporten zijn alleen beschikbaar wanneer u de modus Dynamic Media - Hybride uitvoert.

De videorapporten tonen verscheidene gezamenlijke metriek over een gespecificeerde tijd om u te helpen controleren dat *published *individual en gezamenlijke video&#39;s zoals verwacht presteren. De volgende statistische gegevens worden geaggregeerd voor alle gepubliceerde video&#39;s op uw gehele website:

* Video start
* Voltooiingssnelheid
* Gemiddelde tijd op video
* Totale tijd op video
* Video&#39;s per bezoek

Er wordt ook een tabel met alle *gepubliceerde* video&#39;s weergegeven, zodat u de bovenste weergegeven video&#39;s op uw website kunt bijhouden op basis van het totale aantal videobeelden dat wordt gestart.

Wanneer u een videonaam in de lijst tikt, wordt het rapport met betrekking tot het vasthouden van het publiek van de video (drop-off) weergegeven in de vorm van een lijndiagram. Het diagram toont het aantal weergaven voor een bepaald tijdstip tijdens het afspelen van video. Wanneer u de video afspeelt, wordt de verticale balk gesynchroniseerd met de tijdindicator in de speler. De vallen in de gegevens van het lijndiagram wijzen op waar uw publiek van oninteresse wegvalt.

Als de video buiten Adobe Experience Manager Dynamic Media is gecodeerd, zijn het diagram voor het vasthouden van het publiek (drop-off) en de gegevens voor het afspeelpercentage in de tabel niet beschikbaar.

Zie ook [Dynamic Media-Cloud Services configureren](/help/assets/config-dynamic.md).

>[!NOTE]
>
>Het bijhouden en rapporteren van gegevens is uitsluitend gebaseerd op het gebruik van de eigen videospeler van Dynamic Media en de bijbehorende voorinstelling van de videospeler. U kunt dus geen video&#39;s bijhouden en rapporteren die door andere videospelers worden afgespeeld.

Door gebrek, de eerste keer u VideoRapporten ingaat, toont het rapport videogegevens die bij de eerste van de huidige maand beginnen en met de datum van de huidige maand beëindigen. U kunt het standaarddatumbereik echter overschrijven door uw eigen datumbereik op te geven. De volgende keer dat u Video-rapporten invoert, wordt het opgegeven datumbereik gebruikt.

Voor het correct werken van videorapporten, wordt een identiteitskaart van de Reeks van het Rapport automatisch gecreeerd wanneer de Cloud Services van Dynamic Media wordt gevormd. Tegelijkertijd wordt de rapportsuite-id doorgegeven aan de publicatieserver, zodat deze beschikbaar is voor de functie URL kopiëren wanneer u een voorvertoning van elementen weergeeft. Deze functionaliteit vereist echter dat de publicatieserver al is ingesteld. Als de publicatieserver niet is ingesteld, kunt u toch publiceren om het videoverslag te zien. U moet echter terugkeren naar de Dynamic Media Cloud Configuration en **[!UICONTROL OK]** tikken.

**Videorapporten weergeven:**

1. Tik in de linkerbovenhoek van de Experience Manager op het logo van de Experience Manager en tik **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Video Reports]**.
1. Voer een van de volgende handelingen uit op de pagina Videorapporten:

   * Tik in de rechterbovenhoek op het pictogram **Video-rapport vernieuwen**.
Gebruik alleen Vernieuwen als de einddatum van het rapport de huidige dag is. Dit zorgt ervoor dat u de video het volgen ziet die sinds de laatste tijd is voorgekomen u het rapport in werking stelde.

   * Tik in de rechterbovenhoek op het pictogram **Datumkiezer**.
Geef het begin- en einddatumbereik op waarvoor u videogegevens wilt en tik op **[!UICONTROL Run Report]**.

   In het groepsvak Metriek bovenaan ziet u diverse geaggregeerde metingen voor alle *gepubliceerde* video&#39;s op uw site.

1. Tik in de tabel met de bovenste gepubliceerde video&#39;s op een videonaam om de video af te spelen en zie ook het rapport voor het vasthouden van het publiek van de video (drop-off).

### Videorapporten weergeven op basis van een videoviewer die u hebt gemaakt met de SDK van de Dynamic Media HTML5 Viewer {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Als u een uit-van-doos videoviewer gebruikt die door Dynamic Media wordt verstrekt, of als u een vooraf ingestelde douaneviewer creeerde die van een uit-van-doos videokijker wordt gebaseerd, dan worden geen extra stappen vereist om videorapporten te bekijken. Als u echter uw eigen videoviewer hebt gemaakt op basis van de HTML5 Viewer SDK API, voert u de volgende stappen uit om ervoor te zorgen dat uw videoviewer traceergebeurtenissen naar Dynamic Media Video Reports verzendt.

Gebruik de [Adobe Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html) en de [HTML5 Viewer SDK API](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) om uw eigen videoviewers te maken.

**U kunt als volgt videorapporten weergeven op basis van een videoviewer die u hebt gemaakt met de SDK van de Dynamic Media HTML5 Viewer:**

1. Navigeer naar een gepubliceerd video-element.
1. Selecteer in de vervolgkeuzelijst in de linkerbovenhoek van de assetpagina de optie **[!UICONTROL Viewers]**.
1. Selecteer een voorinstelling voor een videoviewer en kopieer de insluitcode.
1. Zoek in de insluitcode de regel met het volgende:

   `videoViewer.setParam("config2", "<value>");`

   Met de parameter `config2` kunnen HTML5 Viewers worden bijgehouden. Het is ook een bedrijf-specifieke vooraf ingesteld die de configuratieinformatie voor Video die, en voor klant-specifieke configuraties van Adobe Analytics bevat meldt.

   De correcte waarde voor de config2-parameter vindt u in zowel de functie **[!UICONTROL Embed Code]** als in de functie voor het kopiëren van de **[!UICONTROL URL]**. In de URL van de opdracht voor het kopiëren van de **[!UICONTROL URL]**, zoekt u naar de parameter `&config2=<value>`. De waarde is bijna altijd `companypreset`, maar in sommige gevallen ook `companypreset-1`, `companypreset-2`, enz.

1. Voeg in uw aangepaste videoviewercode AppMeasurementBridge .jsp als volgt toe aan de viewerpagina:

   * Bepaal eerst of u de parameter `&preset` nodig hebt.

      Als de `config2` parameter `companypreset` is, doet u *not* behoefte `&preset=parameter`.

      Wanneer `config2` iets anders is, stelt u de parameter preset op dezelfde manier in als de parameter `config2`. Als `config2=companypreset-2` bijvoorbeeld, `&param2=companypreset-2` aan AppMeturmentBridge.jsp URL toevoegt.

   * Voeg vervolgens het script AppMeasurementBridge.jsp toe:

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Maak als volgt de component TrackingManager:

   * Nadat u `s7sdk.Util.init();` roept, creeer een instantie TrackingManager om gebeurtenissen te volgen door het volgende toe te voegen:

      `var trackingManager = new s7sdk.TrackingManager();`

   * Verbind componenten met TrackingManager door het volgende te doen:

      Verbind in de `s7sdk.Event.SDK_READY` gebeurtenismanager, de component u aan TrackingManager wilt volgen.

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

## Bijschriften of ondertitels toevoegen aan video {#adding-captions-to-video}

U kunt het bereik van uw video&#39;s uitbreiden naar wereldwijde markten door ondertiteling toe te voegen aan enkele video&#39;s of aan Adaptive Video Sets. Door ondertiteling toe te voegen vermijdt u de noodzaak om de audio te dupliceren, of de behoefte om inheemse sprekers te gebruiken om de audio voor elke verschillende taal opnieuw op te nemen. De video wordt afgespeeld in de taal waarin deze is opgenomen. Er verschijnen ondertitels in vreemde talen, zodat mensen in verschillende talen het audiogedeelte nog steeds kunnen begrijpen.

Ondertiteling maakt ook een betere toegankelijkheid mogelijk door ondertiteling te gebruiken voor doven of slechthorenden.

>[!NOTE]
>
>De videospeler die u gebruikt moet de vertoning van titels steunen.

Dynamic Media converteert bijschriftbestanden naar de indeling JSON (JavaScript Object Notation). Met deze conversie kunt u de JSON-tekst insluiten in een webpagina als een verborgen, maar volledige transcriptie van de video. Zoekprogramma&#39;s kunnen de inhoud vervolgens verkennen en indexeren, zodat de video&#39;s gemakkelijker te vinden zijn en klanten meer informatie krijgen over de video-inhoud.

Zie [Statische inhoud (niet van het beeld) dienen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) in *Dynamic Media Image Serving and Rendering API Help* voor meer informatie over het gebruik van de functie JSON in een URL.

**Bijschriften of ondertitels toevoegen aan video:**

1. U kunt een toepassing of service van derden gebruiken om een ondertitelingsbestand of ondertitelingsbestand voor video te maken.

   Zorg ervoor dat het bestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsnaamextensie voor ondertiteling is .vtt. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

   Zie [WebVTT: De indeling Web Video Text Tracks](https://w3c.github.io/webvtt/).

   Er zijn zowel gratis als premiumtools en -services die u kunt gebruiken voor het schrijven van bijschriften en ondertitelingsbestanden buiten Dynamic Media. Als u bijvoorbeeld een eenvoudig videobijschriftbestand zonder opmaak wilt maken, kunt u de volgende gratis gereedschappen voor het maken en bewerken van bijschriften gebruiken:

   [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   U bereikt de beste resultaten met het programma in Internet Explorer 9 of hoger, Google Chrome of Safari.

   Plak in het veld **[!UICONTROL Enter URL of video file]** van het gereedschap de gekopieerde URL van het videobestand en klik vervolgens op **[!UICONTROL Load]**. Zie [Een URL verkrijgen voor een element](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) om de URL naar het videobestand zelf op te halen, dat u vervolgens in **[!UICONTROL Enter URL of video file field]** kunt plakken. Internet Explorer, Chrome of Safari kunnen de video vervolgens op een native manier afspelen.

   Volg nu de aanwijzingen op het scherm van de site om het WebVTT-bestand te ontwerpen en op te slaan. Wanneer u klaar bent, kopieert u de inhoud van het bijschriftbestand en plakt u deze in een teksteditor zonder opmaak en slaat u het bestand op met de bestandsnaamextensie `.vtt`.

   >[!NOTE]
   >
   >Voor algemene ondersteuning van videoondertitels in meerdere talen vereist de WebVTT-standaard dat u afzonderlijke .vtt-bestanden maakt en dat u voor elke taal die u wilt ondersteunen, een oproep doet.

   Over het algemeen wilt u het VTT-bestand van het bijschrift dezelfde naam geven als het videobestand en dit bestand toevoegen met de landinstelling van de taal, zoals -EN, -FR of -DE. Hierdoor kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.

1. Upload in Experience Manager uw WebVTT-bijschriftbestand naar DAM.
1. Navigeer naar het *gepubliceerde*-videoelement dat u wilt koppelen aan het bijschriftbestand dat u hebt geüpload.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*.

   Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md).

1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL URL]** voor een pop-upviewerbeleving. Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord en passeer de URL naar een eenvoudige teksteditor. Voeg de gekopieerde URL van de video toe met de volgende syntaxis:

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Noteer `,1` aan het einde van het bijschriftpad. Direct na de bestandsnaamextensie `.vtt` in het pad kunt u optioneel de knop voor het gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door respectievelijk `,1` of `,0` in te stellen.

   * Tik op **[!UICONTROL Embed Code]** voor een ingesloten video-viewerbeleving. Selecteer in het dialoogvenster Code insluiten de insluitcode en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor. Voeg de gekopieerde insluitcode toe met de volgende syntaxis:

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Noteer `,1` aan het einde van het bijschriftpad. Direct na de bestandsnaamextensie `.vtt` in het pad kunt u optioneel de knop voor het gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door respectievelijk `,1` of `,0` in te stellen.

## Hoofdstukmarkeringen aan video toevoegen {#adding-chapter-markers-to-video}

U kunt uw lange formuliervideo&#39;s beter weergeven en navigeren door hoofdstukmarkeringen toe te voegen aan enkele video&#39;s of aan Adaptieve videosets. Wanneer een gebruiker de video afspeelt, kunnen hij of zij op de hoofdstukmarkeringen op de videotijdlijn (ook wel de videoscrubber genoemd) klikken om gemakkelijk naar zijn of haar interessepunt te navigeren. Of ze kunnen meteen naar nieuwe inhoud, demonstraties en zelfstudies gaan.

>[!NOTE]
>
>De videospeler die wordt gebruikt moet het gebruik van hoofdstukmarkeringen steunen. Dynamic Media-videospelers ondersteunen wel hoofdstukmarkeringen, maar het gebruik van videospelers van derden is mogelijk niet mogelijk.

Desgewenst kunt u uw eigen aangepaste videoviewer maken en markeren met hoofdstukken in plaats van een voorinstelling voor de videoviewer te gebruiken. Raadpleeg voor instructies over het maken van uw eigen HTML5-viewer met hoofdstuknavigatie in de Adobe HTML5 Viewer SDK API de kop &quot;Gedrag aanpassen met wijzigingstoetsen&quot; onder de klassen `s7sdk.video.VideoPlayer` en `s7sdk.video.VideoScrubber`. Zie de [HTML5 Viewer SDK API](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) documentatie.

<!-- If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading “Customizing Behavior Using Modifiers” under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

U maakt een hoofdstuklijst voor uw video op ongeveer dezelfde manier als u bijschriften maakt. U maakt dus een WebVTT-bestand. Merk op, echter, dat dit dossier van om het even welk WebVTT titeldossier moet gescheiden zijn dat u ook gebruikt; u kunt geen titels en hoofdstukken in één dossier combineren WebVTT.

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

In het bovenstaande voorbeeld is `Chapter 1` de cue-id en is deze optioneel. De cuetijd van `00:00:000 --> 01:04:364` specificeert de begintijd en eindtijd van het hoofdstuk, in formaat `00:00:000`. Die laatste drie cijfers zijn milliseconden en kunnen als `000`, indien gewenst worden verlaten. De hoofdstuktitel van `The bicycle store behind it all` is de daadwerkelijke beschrijving van de inhoud van het hoofdstuk. De actidentificator, de begintijd en de hoofdstuktitel worden allemaal weergegeven in een pop-up van een videospeler wanneer een gebruiker de muisaanwijzer boven een visueel actiepunt in de tijdlijn van de video houdt.

Omdat u een HTML5-videoviewer gebruikt, moet u ervoor zorgen dat het hoofdstukbestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsextensie van het hoofdstuk is `.vtt`. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

Zie [WebVTT: De indeling Web Video Text Tracks](https://w3c.github.io/webvtt/)

**Hoofdstukmarkeringen aan video toevoegen:**

1. Sla het `.vtt`-bestand op in UTF8-codering, zodat u problemen met tekenuitvoering in de hoofdstuktiteltekst voorkomt.

   Over het algemeen wilt u het hoofdstuk VTT-bestand dezelfde naam geven als het videobestand en het toevoegen met hoofdstukken. Hierdoor kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.
1. Upload in Experience Manager uw WebVTT-hoofdstukbestand.

   Zie [Elementen uploaden](/help/assets/manage-assets.md#uploading-assets).

1. Voer een van de volgende handelingen uit:

   <table>
     <tbody>
      <tr>
       <td>Voor een ervaring met een pop-upvideoviewer</td>
       <td>
       <ol>
       <li>Navigeer naar het <i>gepubliceerde </i>video-element dat u wilt koppelen aan het hoofdstukbestand dat u hebt geüpload. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/publishing-dynamicmedia-assets.md">Elementen publiceren.</a></li>
       <li>Klik of tik in het keuzemenu op <strong>Viewers</strong>.</li>
       <li>Tik of klik in de linkertrack op de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>Klik op <strong>URL</strong> in het linkerspoor onderaan.</li>
       <li>Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord. Plak vervolgens de URL in een eenvoudige teksteditor.</li>
       <li>Voeg de gekopieerde URL van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Voor een ingesloten videoviewerervaring<br /> </td>
       <td>
       <ol>
       <li>Navigeer naar het <i>gepubliceerde </i>video-element dat u wilt koppelen aan het hoofdstukbestand dat u hebt geüpload. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/publishing-dynamicmedia-assets.md">Elementen publiceren.</a></li>
       <li>Klik of tik in het keuzemenu op <strong>Viewers</strong>.</li>
       <li>Tik of klik in de linkertrack op de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>Klik op <strong>Insluiten</strong> in de linkertrack onder.</li>
       <li>Selecteer in het dialoogvenster Code insluiten de gehele code en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor.</li>
       <li>Voeg de insluitcode van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>

## Informatie over videominiaturen in de modus Dynamic Media - Scene7 {#about-video-thumbnails-in-dynamic-media-scene-mode}

Een videominiatuur is een verkleinde versie van een videoframe of een afbeeldingselement dat de video voor de klant vertegenwoordigt. De miniatuur moedigt een klant aan om op de video te klikken.

Aan alle video&#39;s in de Experience Manager moet een miniatuur zijn gekoppeld. u kunt een miniatuur niet verwijderen zonder deze te vervangen. Wanneer u een video uploadt naar Experience Manager, wordt standaard het eerste frame gebruikt als miniatuur. U kunt de miniatuur echter aanpassen voor bijvoorbeeld branding of visuele zoekopdracht. Wanneer u een videominiatuur aanpast, kunt u de video afspelen en pauzeren op het frame dat u wilt gebruiken. U kunt ook een afbeeldingselement selecteren dat u al hebt geüpload en *gepubliceerd* in het beheer van digitale elementen.

Een aangepaste videominiatuurafbeelding die u selecteert uit een video, wordt niet geëxtraheerd en in de DAM opgeslagen als een afzonderlijk en afzonderlijk element. Een aangepaste videominiatuur die u selecteert uit een bestaand afbeeldingselement, wordt echter opgeslagen in de tekenherkenning. Het pad van het geselecteerde element wordt opgeslagen onder het knooppunt van het video-element, zoals in het volgende voorbeeldpad:

`/content/dam/*<folder_name*>/<*video_name*>/jcr:content/manualThumbnail`

De mogelijkheid om een videominiatuur aan te passen is alleen beschikbaar nadat u een videoprofiel hebt toegepast op de map waarin de video zich bevindt.

Zie ook [Informatie over videominiaturen in Dynamic Media - hybride modus](#about-video-thumbnails-in-dynamic-media-hybrid-mode).

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail}

Deze stappen zijn alleen van toepassing op Dynamic Media die wordt uitgevoerd in de modus &quot;Dynamicmedia_Scene7&quot;.

**Een aangepaste videominiatuur toevoegen:**

1. Zorg ervoor dat u al het volgende hebt gedaan:

   * Er is een map gemaakt voor uw video-elementen.
   * [Er is een videoprofiel op de map](/help/assets/video-profiles.md#applying-a-video-profile-to-folders) toegepast.

   * [Uw video&#39;s zijn geüpload naar de map](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

1. Navigeer naar een geüpload video-element waarvan u de miniatuurafbeelding wilt wijzigen.
1. Tik in de modus voor middelenselectie op **[!UICONTROL List View]** of **[!UICONTROL Card View]** van het video-element.
1. Tik op de werkbalk op het pictogram **[!UICONTROL Properties]** (een cirkel met een &quot;i&quot; erin).
1. Tik op **[!UICONTROL Change Thumbnail]** op de pagina Eigenschappen van video.
1. Voer een van de volgende handelingen uit op de pagina Miniatuur wijzigen:

   * Een frame uit de video gebruiken als de nieuwe miniatuur:

      * Tik op **[!UICONTROL Select Frame from video]** op de werkbalk.
      * Tik op de knop Afspelen en tik vervolgens op de knop Pauzeren op het frame dat u wilt vastleggen als de nieuwe miniatuur van de video.
   * Een afbeeldingselement gebruiken als de nieuwe miniatuur:

      * Tik op **[!UICONTROL Select Thumbnail from Assets]** op de werkbalk.
      * Tik op **[!UICONTROL Select Thumbnail]**.
      * Navigeer naar een eerder geüpload en gepubliceerd afbeeldingselement dat u wilt gebruiken. De grootte van het element wordt automatisch aangepast om te dienen als miniatuurafbeelding voor de video.
      * Selecteer het afbeeldingselement en tik op **[!UICONTROL Select]**.


1. Tik op **[!UICONTROL Save Change]** op de pagina Miniatuur wijzigen.
1. Tik in de rechterbovenhoek op de pagina Eigenschappen van video op **[!UICONTROL Save & Close]**.

## Informatie over videominiaturen in Dynamic Media - hybride modus {#about-video-thumbnails-in-dynamic-media-hybrid-mode}

U kunt kiezen uit een van de tien miniatuurafbeeldingen die automatisch door Dynamic Media worden gegenereerd om aan uw video toe te voegen. De videospeler toont uw geselecteerde duimnagel wanneer een videoactiva met de component van Dynamic Media in het auteursmilieu van de Plaatsen van de Experience Manager, Experience Manager Mobiele, of Experience Managers Screens wordt gebruikt. De miniatuur fungeert als een statisch beeld dat de inhoud van de gehele video het beste vertegenwoordigt en dat gebruikers verder aanmoedigt om op de knop Afspelen te klikken.

Dynamic Media legt tien (standaard)miniatuurafbeeldingen vast op basis van de totale tijd van de video. De afbeeldingen worden vastgelegd op 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81% en 91% in de video. De tien miniaturen blijven bestaan. Dit betekent dat als u een andere miniatuur kiest, u de reeks niet opnieuw hoeft te genereren. U bekijkt een voorvertoning van de tien miniatuurafbeeldingen en selecteert vervolgens de miniatuurafbeelding die u voor de video wilt gebruiken. Als u wilt veranderen in het gebrek, kunt u CRXDE Lite gebruiken om het tijdinterval te vormen dat duimnagelbeelden worden geproduceerd. Als u bijvoorbeeld alleen een reeks van vier miniatuurafbeeldingen met gelijkmatige tussenruimte uit uw video wilt genereren, kunt u de intervaltijd instellen op 24%, 49%, 74% en 99%.

In het ideale geval kunt u een videominiatuur toevoegen nadat u de video hebt geüpload, maar voordat u de video op uw website publiceert.

Desgewenst kunt u een aangepaste miniatuur uploaden die uw video vertegenwoordigt in plaats van een miniatuur die door Dynamic Media is gegenereerd. U kunt bijvoorbeeld een aangepaste miniatuurafbeelding maken met de titel van uw video, een opvallende openingsafbeelding of een specifieke afbeelding die u van uw video hebt vastgelegd. De aangepaste videominiatuurafbeelding die u uploadt, moet een maximale resolutie van 1280 x 720 pixels (minimale breedte van 640 pixels) en niet groter zijn dan 2 MB.

Zie ook [Informatie over videominiaturen in Dynamic Media - Scene7-modus](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

### Een videominiatuur toevoegen {#adding-a-video-thumbnail}

Deze stappen zijn alleen van toepassing op Dynamic Media die wordt uitgevoerd in de hybride modus.

**Een videominiatuur toevoegen:**

1. Navigeer naar een geüpload video-element waaraan u een videominiatuur wilt toevoegen.
1. Tik in de modus voor middelenselectie in de lijstweergave of de kaartweergave op het video-element.
1. Tik op de werkbalk op het pictogram **[!UICONTROL View Properties]** (een cirkel met een &quot;i&quot; erin).
1. Tik op **[!UICONTROL Change Thumbnail]** op de pagina Eigenschappen van video.
1. Tik op **[!UICONTROL Select Frame]** op de pagina Miniatuur wijzigen op de werkbalk.

   Dynamic Media genereert een reeks miniatuurafbeeldingen van uw video op basis van het standaardtijdinterval of -interval dat u hebt aangepast.

1. Geef een voorvertoning van de gegenereerde miniatuurafbeeldingen weer en selecteer de miniatuurafbeelding die u aan de video wilt toevoegen.
1. Tik op **[!UICONTROL Save Change]**.

   De miniatuurafbeelding van de video wordt bijgewerkt en gebruikt nu de miniatuur die u hebt geselecteerd. Als u later besluit om de miniatuurafbeelding te wijzigen, kunt u terugkeren naar de pagina **[!UICONTROL Change Thumbnail]** en een nieuwe pagina selecteren.

   Als u nieuwe standaardtijdintervallen hebt geconfigureerd of als u een nieuwe video hebt geüpload ter vervanging van de bestaande video, moet Dynamic Media de miniaturen opnieuw genereren.

   Zie [Het standaardtijdinterval configureren dat videominiaturen worden gegenereerd](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

#### Configureer het standaardtijdinterval dat videominiaturen worden gegenereerd {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

Wanneer u het nieuwe standaardtijdinterval configureert en opslaat, is uw wijziging automatisch alleen van toepassing op video&#39;s die u in de toekomst uploadt. De nieuwe standaardinstelling wordt niet automatisch toegepast op video&#39;s die u eerder hebt geüpload. Voor bestaande video&#39;s moet u de miniaturen opnieuw genereren.

Zie [Een videominiatuur toevoegen](#adding-a-video-thumbnail).

**U configureert als volgt het standaardtijdsinterval dat videominiaturen worden gegenereerd:**

1. Tik in Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. Navigeer op de pagina CRXDE Lite in het mappenvenster aan de linkerkant naar `o etc/dam/imageserver/configuration/jcr:content/settings.`

   Als het mappenvenster niet zichtbaar is, tikt u op het pictogram >> links van het tabblad Start.

1. Dubbeltik op het tabblad Eigenschappen in het deelvenster rechtsonder op `thumbnailtime`.
1. Gebruik in het dialoogvenster **[!UICONTROL Edit thumbnailtime]** de tekstvelden om intervalwaarden in te voeren als percentages.

   * Tik op het plusteken (+) als u een of meer velden voor intervalwaarden wilt toevoegen. Blader zo nodig naar de onderkant van het dialoogvenster om het pictogram weer te geven.
   * Tik op het minteken (-) rechts van een veld voor de intervalwaarde als u dit wilt verwijderen uit de lijst.
   * Tik op het pictogram Pijl-omhoog en Pijl-omlaag als u de intervalwaarden opnieuw wilt rangschikken.

1. Tik op **[!UICONTROL OK]** en ga terug naar het tabblad Eigenschappen.
1. Tik in de linkerbovenhoek van de pagina CRXDE Lite op **[!UICONTROL Save All]** en tik vervolgens op het pictogram Startpagina terug in de linkerbovenhoek om terug te keren naar de Experience Manager.

   Zie [Een videominiatuur toevoegen](#adding-a-video-thumbnail).

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail-1}

Deze stappen zijn alleen van toepassing op Dynamic Media die wordt uitgevoerd in de hybride modus.

**Een aangepaste videominiatuur toevoegen:**

1. Navigeer naar een geüpload video-element waaraan u een aangepaste miniatuur voor video wilt toevoegen.
1. Tik in de modus voor middelenselectie in de lijstweergave of de kaartweergave op het video-element.
1. Tik op de werkbalk op het pictogram **[!UICONTROL View Properties]** (een cirkel met een &quot;i&quot; erin).
1. Tik op **[!UICONTROL Change Thumbnail]** op de pagina Eigenschappen van video.
1. Tik op **[!UICONTROL Upload New Thumbnail]** op de pagina Miniatuur wijzigen op de werkbalk.
1. Navigeer naar een miniatuurafbeelding die u wilt gebruiken, selecteer deze en tik op **[!UICONTROL Open]** om de afbeelding naar de Experience Manager te uploaden. Na het uploaden moet u de afbeelding publiceren.
1. Tik op **[!UICONTROL Save Changes]** nadat u de afbeelding hebt geüpload en gepubliceerd op de pagina Miniatuur wijzigen.

   De aangepaste miniatuur wordt toegevoegd aan uw video.
