---
title: Video in Dynamic Media
description: Leer hoe u in Dynamic Media met video werkt, zoals tips en trucs voor het coderen van video's, het publiceren van video's naar YouTube en het weergeven van videoverslagen. Leer ook hoe u ondertiteling, ondertitels of hoofdstukmarkeringen aan video's kunt toevoegen.
mini-toc-levels: 3
uuid: 97f311a3-a227-479a-91bf-fb54ecd1a55d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 1103b849-0042-4e11-b170-38ee81dd0157
docset: aem65
feature: Asset Management
role: User, Admin
exl-id: 28cf9e39-cab4-4278-b6c9-e84cc31964db
source-git-commit: 2c4be989decbac2a4109e7c02cd9d6231c1d0753
workflow-type: tm+mt
source-wordcount: '12065'
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
>* Zie [Dynamic Media-Cloud Services configureren](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) in De modus Dynamic Media configureren - Scene7 en [Problemen met Dynamic Media oplossen - Scene7-modus](/help/assets/troubleshoot-dms7.md).
>
>* Zie [Dynamic Media-Cloud Services configureren](/help/assets/config-dynamic.md#configuring-dynamic-media-cloud-services) in De modus Dynamic Media configureren - hybride.
>
>Bekend probleem met het afspelen van video in Dynamic Media *alleen in Experience Manager 6.5.9.0*:
>
>* Als een gepubliceerde video wordt bijgewerkt, moet deze opnieuw worden gepubliceerd om wijzigingen in de levering te weerspiegelen.
>


1. **Dynamic Media-video&#39;s uploaden** door het volgende te doen:

   * Maak uw eigen videocoderingsprofiel. U kunt ook gewoon de vooraf gedefinieerde _Adaptieve videocodering_ profiel dat bij Dynamic Media wordt geleverd.

      * [Een videocoderingsprofiel maken](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * Meer informatie over [Aanbevolen procedures voor videocodering](#best-practices-for-encoding-videos).
   * Koppel het videoverwerkingsprofiel aan een of meer mappen waar u de primaire bronvideo&#39;s gaat uploaden.

      * [Een videoprofiel toepassen op mappen](/help/assets/video-profiles.md#applying-a-video-profile-to-folders).
      * Meer informatie over [Aanbevolen procedures voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](/help/assets/organize-assets.md).
      * Meer informatie over [Digitale elementen ordenen](/help/assets/organize-assets.md).
   * Upload uw primaire bronvideo&#39;s naar de mappen. Wanneer u video&#39;s aan de map toevoegt, worden deze gecodeerd volgens het videoverwerkingsprofiel dat u aan de map hebt toegewezen.

      * Dynamic Media ondersteunt voornamelijk korte video&#39;s met een maximale lengte van 30 minuten en een minimale resolutie van meer dan 25 x 25.
      * U kunt videobestanden uploaden van maximaal 15 GB elk.
      * [Uw video&#39;s uploaden](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).
      * Meer informatie over [Ondersteunde bestandsindelingen voor invoer](/help/assets/assets-formats.md#supported-multimedia-formats).
   * Controleren hoe [videocodering wordt voortgezet](#monitoring-video-encoding-and-youtube-publishing-progress) vanuit het element of de werkstroomweergave.




1. **Uw Dynamic Media-video&#39;s beheren** door een van de volgende handelingen uit te voeren:

   * Video-elementen organiseren, doorbladeren en zoeken

      * [Digitale elementen ordenen](/help/assets/organize-assets.md)
Meer informatie over [Aanbevolen procedures voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](organize-assets.md)

      * [Video-elementen zoeken](search-assets.md#custompredicates) of [Zoeken in middelen](/help/assets/search-assets.md)
   * Video-elementen voorvertonen en publiceren

      * Bekijk de bronvideo en de gecodeerde vertoningen van de video samen met de bijbehorende miniaturen:
         [Video&#39;s voorvertonen](managing-video-assets.md#upload-and-preview-video-assets) of [Elementen voorvertonen](previewing-assets.md)
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

      * [Video&#39;s notities aanbrengen](managing-video-assets.md#annotate-video-assets) of [Elementen notities aanbrengen](manage-assets.md#annotating)

      * [Een versie maken](manage-assets.md#asset-versioning)
      * [Workflows toepassen op elementen](assets-workflow.md) of zie [Een workflow op een element starten](manage-assets.md#starting-a-workflow-on-an-asset)

      * [Mapmiddelen controleren](bulk-approval.md)
      * [Projecten](../sites-authoring/projects.md)




1. **Dynamic Media-video&#39;s publiceren** door een van de volgende handelingen uit te voeren:

   * Als u Adobe Experience Manager gebruikt als beheersysteem voor webinhoud, kunt u video&#39;s rechtstreeks aan uw webpagina&#39;s toevoegen.

      * [Video&#39;s toevoegen aan uw webpagina&#39;s](adding-dynamic-media-assets-to-pages.md).
   * Als u een systeem voor webcontentbeheer van derden gebruikt, kunt u video&#39;s koppelen aan of insluiten in uw webpagina&#39;s.

      * Video integreren met URL:
         [URL&#39;s koppelen aan uw webtoepassing](linking-urls-to-yourwebapplication.md).

      * Video integreren met gebruik van ingesloten code op webpagina:
         [De videoviewer insluiten op een webpagina](embed-code.md).
   * [Video&#39;s publiceren naar YouTube](#publishing-videos-to-youtube).
   * [Videorapporten genereren](#viewing-video-reports).

   * [Bijschriften toevoegen aan video](#adding-captions-to-video).



## Werken met video in Dynamic Media {#working-with-video-in-dynamic-media}

Video in Dynamic Media is een end-to-end oplossing waarmee u eenvoudig Adaptieve video van hoge kwaliteit kunt publiceren voor streaming op meerdere schermen, zoals desktopcomputers, iOS, Android™, BlackBerry® en mobiele Windows-apparaten. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. De desktopcomputer of het mobiele apparaat detecteert de beschikbare bandbreedte.

Op een mobiel iOS-apparaat wordt bijvoorbeeld een bandbreedte gedetecteerd, zoals 3G, 4G of Wi-Fi. Vervolgens wordt automatisch de naar rechts gecodeerde video geselecteerd bij de verschillende bitsnelheden van de video in de adaptieve videoset. De video wordt gestreamd naar desktops, mobiele apparaten of tablets.

Bovendien wordt de videokwaliteit automatisch dynamisch geschakeld als de netwerkomstandigheden veranderen op het bureaublad of op het mobiele apparaat. Als een klant de modus Volledig scherm op een desktopcomputer inschakelt, reageert de Adaptive Video Set met een betere resolutie, waardoor de kijkervaring van de klant wordt verbeterd. Met Adaptieve videosets kunt u Dynamic Media-video op meerdere schermen en apparaten het best afspelen.

De logica die een videospeler gebruikt om te bepalen welke gecodeerde video moet worden afgespeeld of tijdens het afspelen moet worden geselecteerd, is gebaseerd op het volgende algoritme:

1. Videospeler laadt het eerste videofragment op basis van de bitsnelheid die het dichtst bij de waarde ligt die is ingesteld voor de beginbitsnelheid in de speler zelf.
1. De videospelerschakelaars die op veranderingen in de bandbreedtesnelheid worden gebaseerd die de volgende criteria gebruiken:

   1. De speler kiest de hoogste bandbreedtestroom onder of gelijk aan de geschatte bandbreedte.
   1. De speler overweegt slechts 80% van de beschikbare bandbreedte. Als er echter een overstap wordt gemaakt, is het conservatiever bij slechts 70% om overschatting te voorkomen en onmiddellijk terug te keren.

Voor gedetailleerde technische informatie over het algoritme, zie [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Voor het beheren van afzonderlijke video- en adaptieve videosets wordt het volgende ondersteund:

* Video uploaden van video-indelingen en audio-indelingen die ondersteuning bieden voor een groot aantal apparaten en het coderen van video naar de MP4 H.264-indeling, zodat deze op meerdere schermen kan worden afgespeeld. U kunt vooraf gedefinieerde adaptieve videovoorinstellingen gebruiken, voorinstellingen voor één videocodering gebruiken of uw eigen codering aanpassen om de kwaliteit en de grootte van de video te bepalen.

   * Wanneer een adaptieve videoset wordt gegenereerd, bevat deze MP4-video&#39;s.
   * **Opmerking**: Master-/bronvideo&#39;s worden niet toegevoegd aan een adaptieve videoset.

* ondertiteling in alle HTML5-videoviewers.
* Video organiseren, doorbladeren en doorzoeken met volledige metagegevensondersteuning voor een efficiënt beheer van video-elementen.
* Lever Adaptieve videosets naar het web en naar desktops en mobiele apparaten, zoals de iPhone, iPad, Android™, BlackBerry® en Windows-telefoon.

Adaptieve videostreaming wordt ondersteund op verschillende iOS-platforms. Zie [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html#video).

Dynamic Media ondersteunt het afspelen van mobiele video voor MP4 H.264-video. U kunt de apparaten van BlackBerry® vinden die dit videoformaat bij het volgende steunen: [Ondersteunde video-indelingen op BlackBerry®](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

U kunt de apparaten van Vensters vinden die dit videoformaat bij het volgende steunen: [Ondersteunde mediacodecs voor Windows Phone 8](https://learn.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs)



* Speel de video terug gebruikend de Voorinstellingen van de VideoKijker van Dynamic Media, met inbegrip van het volgende:

   * Afzonderlijke videoviewers.
   * Gemengde Media-viewers die zowel video- als afbeeldingsinhoud combineren.

* Configureer videospelers om aan uw brandingbehoeften te voldoen.
* Video met een eenvoudige URL of insluitcode integreren in uw website, mobiele site of mobiele toepassing.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480) sample. -->

Zie ook [Viewers voor Experience Manager Assets en Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc) en [Viewers voor alleen Experience Manager-elementen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only).

## Beste praktijken: De HTML5-videoviewer gebruiken {#best-practice-using-the-html-video-viewer}

De Dynamic Media HTML5 Video viewer-voorinstellingen zijn robuuste videospelers. U kunt deze gebruiken om veel voorkomende problemen te voorkomen die samenhangen met het afspelen van HTML5-video. En problemen die samenhangen met mobiele apparaten, zoals een gebrek aan adaptieve streaminglevering en een beperkt bereik van de desktopbrowser.

Aan de ontwerpkant van de speler, kunt u de functionaliteit van de videospeler ontwerpen gebruikend standaardWeb ontwikkelingshulpmiddelen. U kunt bijvoorbeeld de knoppen, besturingselementen en de achtergrond van een aangepaste posterafbeelding ontwerpen met behulp van HTML5 en CSS om u te helpen uw klanten te bereiken met een aangepaste weergave.

Aan de afspeelzijde van de viewer wordt automatisch de videocapaciteit van de browser gedetecteerd. Vervolgens wordt de video afgespeeld met HLS of DASH, ook wel adaptieve videostreaming genoemd. Of als deze leveringsmethoden niet aanwezig zijn, wordt in plaats daarvan HTML5 progressief gebruikt.

Door het volgende te combineren in één speler:

* De mogelijkheid om de afspeelcomponenten te ontwerpen met behulp van HTML5 en CSS
* Ingesloten afspelen hebben
* Adaptieve en progressieve streaming gebruiken, afhankelijk van de browsermogelijkheden

U vergroot het bereik van uw rijke media-inhoud tot zowel gebruikers op het bureaublad als mobiele gebruikers en zorgt voor een gestroomlijnde videobeleving.

Zie ook [HTML5-viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only).

### Video afspelen op bureaubladcomputers en mobiele apparaten met de HTML5-videoviewer {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Voor adaptieve videostreaming op het bureaublad en mobiele apparaten zijn de video&#39;s die worden gebruikt voor het schakelen naar een andere bitsnelheid, gebaseerd op alle MP4-video&#39;s in de adaptieve videoset.

Het afspelen van video vindt plaats met HLS of DASH of met progressieve videodownload. In eerdere versies van Experience Manager, zoals 6.0, 6.1 en 6.2, werden video&#39;s gestreamd via HTTP.

In Experience Manager 6.3 en hoger worden video&#39;s nu gestreamd via HTTPS (dat wil zeggen, HLS of DASH) omdat de URL van de DM-gatewayservice altijd HTTPS gebruikt. Dit standaardgedrag heeft geen gevolgen voor de klant. Videostreaming vindt altijd plaats via HTTPS, tenzij dit niet door de browser wordt ondersteund. (zie de volgende tabel). Op grond daarvan wordt met

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
   <td>In Windows 8 en Windows 10 - Gebruik HTTPS wanneer DASH* of HLS wordt aangevraagd, forceren. Bekende beperking: HTTP op DASH* of HLS werkt niet in deze combinatie van browser en besturingssysteem<br /> <br /> In Windows 7: progressief downloaden. Gebruikt de standaardlogica voor het selecteren van het protocol HTTP versus HTTPS.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 23-44</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 45 of hoger</td>
   <td>DASH* of HLS</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Chroom</td>
   <td>DASH* of HLS</td>
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
   <td>DASH* of HLS</td>
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
   <td>DASH* of HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>BlackBerry®</td>
   <td>DASH* of HLS</td>
  </tr>
 </tbody>
</table>

>[!IMPORTANT]
>
>*Als u DASH wilt gebruiken voor uw video&#39;s, moet DASH eerst worden ingeschakeld door Adobe Technical Support op uw account. Zie [DASH inschakelen voor uw account](#enable-dash).)

## Architectuur van Dynamic Media-videooplossing {#architecture-of-dynamic-media-video-solution}

In de volgende afbeelding ziet u de algemene ontwerpworkflow voor video&#39;s die via DMGateway (in de Dynamic Media Hybrid-modus) worden geüpload en gecodeerd en die voor openbare consumptie beschikbaar worden gesteld.

![chlimage_1-427](assets/chlimage_1-427.png)

## Hybride publicatiearchitectuur voor video&#39;s {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Aanbevolen werkwijzen voor het coderen van video&#39;s {#best-practices-for-encoding-videos}

De **Dynamic Media-video coderen** de workflow codeert video als u Dynamic Media hebt ingeschakeld en videocloudservices hebt ingesteld. In deze workflow worden de historie en informatie over fouten van het workflowproces vastgelegd. Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress). Als u Dynamic Media hebt ingeschakeld en videocloudservices hebt ingesteld, **[!UICONTROL Dynamic Media Encode Video]** de workflow wordt automatisch van kracht wanneer u een video uploadt. (Als u Dynamic Media niet gebruikt, wordt **[!UICONTROL DAM Update Asset]** workflow wordt van kracht.)

<!-- DEAD The following are best-practice tips for encoding source video files.

For advice about video encoding, see [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en).

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en). -->

### Bronvideobestanden {#source-video-files}

Wanneer u een videobestand codeert, gebruikt u een videobronbestand van de hoogst mogelijke kwaliteit. Gebruik geen eerder gecodeerde videobestanden omdat deze bestanden al zijn gecomprimeerd en als u verder codeert, wordt een video van subparkwaliteit gemaakt.

* Dynamic Media ondersteunt voornamelijk korte video&#39;s met een maximale lengte van 30 minuten en een minimale resolutie van meer dan 25 x 25.
* U kunt primaire bronvideobestanden uploaden die elk maximaal 15 GB bedragen.

In de volgende tabel worden de aanbevolen grootte, hoogte-breedteverhouding en minimale bitsnelheid beschreven die uw bronvideobestanden moeten hebben voordat u ze codeert:

| Grootte | Hoogte-breedteverhouding | Minimale bitsnelheid |
|--- |--- |--- |
| 1024 x 768 | 4:3 | 4500 kbps voor de meeste video&#39;s. |
| 1280 x 720 | 16:9 | 3000 - 6000 kbps, afhankelijk van de hoeveelheid beweging in de video. |
| 1920 x 1080 | 16:9 | 6000 - 8000 kbps, afhankelijk van de mate van beweging in de video. |

### De metagegevens van een bestand verkrijgen {#obtaining-a-file-s-metadata}

U kunt de metagegevens van een bestand verkrijgen door de metagegevens van het bestand te bekijken met een programma voor videobewerking of met een toepassing die is ontworpen voor het verkrijgen van metagegevens. Hieronder vindt u instructies voor het gebruik van MediaInfo, een toepassing van derden, voor het verkrijgen van de metagegevens van een videobestand:

1. Ga naar [MediaInfo downloaden](https://mediaarea.net/en/MediaInfo/Download).
1. Selecteer en download het installatieprogramma voor de GUI-versie en volg de installatie-instructies.
1. Klik na de installatie met de rechtermuisknop op het videobestand (alleen Windows) en selecteer MediaInfo, of open MediaInfo en sleep het videobestand naar de toepassing. U ziet alle metagegevens die aan het videobestand zijn gekoppeld, inclusief de breedte, hoogte en fps.

### Hoogte-breedteverhouding {#aspect-ratio}

Wanneer u een voorinstelling voor videocodering kiest of maakt voor uw primaire bronvideobestand, moet u ervoor zorgen dat de voorinstelling dezelfde hoogte-breedteverhouding heeft als het primaire bronvideobestand. De hoogte-breedteverhouding is de verhouding tussen de breedte en de hoogte van de video.

Als u de hoogte-breedteverhouding van een videobestand wilt bepalen, vraagt u de metagegevens van het bestand op en noteert u de breedte en hoogte van het bestand (zie De metagegevens van een bestand hierboven verkrijgen). Gebruik vervolgens deze formule om de hoogte-breedteverhouding te bepalen:

width/height = hoogte-breedteverhouding

In de volgende tabel wordt beschreven hoe de resultaten van de formule worden omgezet in algemene opties voor de hoogte-breedteverhouding:

| Resultaat van formule | Hoogte-breedteverhouding |
|--- |--- |
| 1.33 | 4:3 |
| 0.75 | 3:4 |
| 1.78 | 16:9 |
| 0.56 | 9:16 |

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

**Resolutie** Hiermee worden de hoogte en breedte van een videobestand in pixels beschreven. De meeste bronvideo wordt opgeslagen met een hoge resolutie (bijvoorbeeld 1920 x 1080). Voor streamingdoeleinden wordt bronvideo gecomprimeerd tot een lagere resolutie (640 x 480 of lager).

Resolutie en gegevenssnelheid zijn twee geïntegreerde gekoppelde factoren die de videokwaliteit bepalen. Als u dezelfde videokwaliteit wilt behouden, geldt dat hoe hoger het aantal pixels in een videobestand (hoe hoger de resolutie), hoe hoger de gegevenssnelheid. Neem bijvoorbeeld het aantal pixels per frame in een videobestand met een resolutie van 320 x 240 en een resolutie van 640 x 480:

| Resolutie | Pixels per frame |
|--- |--- |
| 320 x 240 | 76,800 |
| 640 x 480 | 307,200 |

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
| Bron | 1920 x 1080 | 1 | 1 |
| Gecodeerd | 960 x 540 | 2 | 2 |
| Gecodeerd | 640 x 360 | 3 | 3 |
| Gecodeerd | 480 x 270 | 4 | 4 |

### Gecodeerde videobestandsindeling {#encoded-video-file-format}

Dynamic Media raadt u aan voorinstellingen voor MP4 H.264-videocodering te gebruiken. Omdat MP4-bestanden de H.264-videocodec gebruiken, biedt deze video van hoge kwaliteit, maar met een gecomprimeerde bestandsgrootte.

### DASH inschakelen voor uw account {#enable-dash}

DASH (Digital Adaptive Streaming via HTTP) is de internationale standaard voor videostreaming en wordt op grote schaal toegepast door verschillende videoviewers. Wanneer u DASH inschakelt, kunt u kiezen uit HLS of DASH voor adaptieve videostreaming. U kunt ook voor beide kiezen met automatische omschakeling tussen spelers.

Enkele belangrijke voordelen van het inschakelen van DASH voor uw account zijn:

* Pakket DASH-streamvideo voor adaptieve streaming. Deze methode leidt tot een efficiëntere levering. Adaptieve streaming zorgt voor de beste kijkervaring voor uw klanten.
* Bij voor browsers geoptimaliseerde streaming met Dynamic Media-spelers wordt geschakeld tussen HLS- en DASH-streaming voor de beste kwaliteit van de service. Wanneer een Safari-browser wordt gebruikt, schakelt de videospeler automatisch over naar HLS.
* U kunt uw voorkeursstreammethode (HLS of DASH) configureren door de voorinstelling voor de videoviewer te bewerken.
* Geoptimaliseerde videocodering zorgt ervoor dat er geen extra opslagruimte wordt gebruikt terwijl DASH-mogelijkheden worden ingeschakeld. Er wordt één set videocoderingscodes gemaakt voor zowel HLS als DASH om de opslagkosten voor video te optimaliseren.
* Helpt de levering van video toegankelijker te maken voor uw klanten.
* U kunt de URL voor streaming ook ophalen via API&#39;s.

   >[!IMPORTANT]
   >
   >Het inschakelen van DASH op uw account is momenteel alleen beschikbaar in Noord-Amerika.

**DASH inschakelen voor uw account:**

1. Navigeren naar [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Zoeken naar **AEM Assets Dynamic Media Video Advanced Streaming** markering functie.
1. Schakel het selectievakje in om DASH in te schakelen (inschakelen).
1. Selecteer **[!UICONTROL Save]**.

## Video&#39;s publiceren naar YouTube {#publishing-videos-to-youtube}

U kunt video-elementen op locatie voor Experience Managers rechtstreeks publiceren naar een YouTube-kanaal dat u eerder hebt gemaakt.

Als u video-elementen naar YouTube wilt publiceren, stelt u Experience Manager Assets in met tags. U koppelt deze tags aan een YouTube-kanaal. Als de tag van een video-element overeenkomt met de tag van een YouTube-kanaal, wordt de video gepubliceerd naar YouTube. Publiceren naar YouTube vindt plaats samen met een normale publicatie van de video zolang een bijbehorende tag wordt gebruikt.

YouTube voert zijn eigen codering uit. Als zodanig wordt het oorspronkelijke videobestand dat naar de Experience Manager is geüpload, gepubliceerd naar YouTube in plaats van een video-uitvoering die door Dynamic Media is gemaakt. Hoewel het niet nodig is om video&#39;s te verwerken met Dynamic Media, wordt verwacht dat dit gebeurt voor het geval dat een viewer-voorinstelling nodig is voor het afspelen.

Wanneer u het videoverwerkingsprofiel overslaat en rechtstreeks naar YouTube publiceert, betekent dit gewoon dat uw video-element in Experience Manager Asset geen zichtbare miniatuur krijgt. Het betekent ook dat als je binnenkomt `dynamicmedia` of `dynamicmedia_scene7` uitvoeringsmodi, video&#39;s die niet zijn gecodeerd, werken niet met Dynamic Media-elementtypen.

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

U kunt ook [Publiceren van video&#39;s ongedaan maken om deze uit YouTube te verwijderen](#unpublishing-videos-to-remove-them-from-youtube).

### Google Cloud-instellingen configureren {#configuring-google-cloud-settings}

Als u wilt publiceren naar YouTube, hebt u een Google-account nodig. Als u een GMAIL-account hebt, hebt u al een Google-account. als u geen Google-account hebt, kunt u er eenvoudig een maken. U hebt het account nodig omdat u aanmeldingsgegevens nodig hebt om video-elementen naar YouTube te publiceren. Als u al een account hebt gemaakt, slaat u deze taak over en gaat u rechtstreeks door naar [Een YouTube-kanaal maken](#creating-a-youtube-channel).

Het account dat wordt gebruikt met Google Cloud en het Google-account dat wordt gebruikt voor YouTube, hoeft niet hetzelfde te zijn.

Google wijzigt regelmatig de gebruikersinterface. De stappen voor het publiceren van video&#39;s naar YouTube kunnen dan ook enigszins afwijken van wat hieronder wordt beschreven. Dit voorbehoud geldt ook voor YouTube wanneer u probeert te controleren of er video&#39;s naar worden geüpload.

>[!NOTE]
>
>De volgende stappen waren correct op het moment van schrijven. Google werkt zijn websites echter regelmatig en zonder kennisgeving bij. Daarom kunnen deze stappen iets anders zijn.

Google Cloud-instellingen configureren:

1. Maak een Google-account.
   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   Als u al een Google-account hebt, gaat u verder met de volgende stap.

1. Ga naar [https://cloud.google.com/](https://cloud.google.com/).
1. Klik in de rechterbovenhoek op de Google Cloud-pagina op **[!UICONTROL Console]**.

   Indien nodig **[!UICONTROL Sign in]** met uw Google-accountgegevens de **[!UICONTROL Console]** optie.

1. Op de pagina Dashboard, rechts van **[!UICONTROL Google Cloud Platform]**, klikt u op de vervolgkeuzelijst Project om het dialoogvenster Een project selecteren te openen.
1. Tik in het dialoogvenster Een project selecteren op **[!UICONTROL New Project]**.

   ![6_5_gogleaccount-newproject](assets/6_5_googleaccount-newproject.png)

1. In het Nieuwe de dialoogvakje van het Project, op het gebied van de Naam van het Project, typ de naam van uw nieuw project.

   Uw project-id is gebaseerd op uw projectnaam. Kies daarom de projectnaam zorgvuldig; het kan na het creëren niet worden veranderd. U moet dezelfde project-id opnieuw invoeren wanneer u YouTube later instelt in Experience Manager. Ik zou het willen afschrijven.

1. Klik op **[!UICONTROL Create]**.

1. Voer een van de volgende handelingen uit:

   * Tik op het dashboard van uw project op de Aan de slag-kaart **[!UICONTROL Explore and enable APIs]**.
   * Tik op het dashboard van uw project op de API&#39;s-kaart **[!UICONTROL Go to APIs overview]**.

   ![6_5_googleaccount-apis-enable2](assets/6_5_googleaccount-apis-enable2.png)

1. Tik boven aan de pagina met API&#39;s en services op **[!UICONTROL Enable APIs and Services]**.
1. Op de pagina van de API-bibliotheek, links, onder **[!UICONTROL Category]**, tikken **[!UICONTROL YouTube]**. Tik rechts op de pagina op **[!UICONTROL YouTube Data API]**.
1. Tik op de v3-pagina YouTube Data API **[!UICONTROL Enable]**.

   ![6_5_googleaccount-apis-enable3](assets/6_5_googleaccount-apis-enable3.png)

1. U hebt referenties nodig om de API te gebruiken. Klik indien nodig op **[!UICONTROL Create Credentials]**.

   ![6_5_googleaccount-apis-createcredentials](assets/6_5_googleaccount-apis-createcredentials.png)

1. Op de **[!UICONTROL Add credentials to your project]** pagina, stap 1, doet het volgende:

   * Selecteer in de vervolgkeuzelijst **[!UICONTROL Which API are you using?]** de optie **[!UICONTROL YouTube Data API v3]**.

   * Selecteer in de vervolgkeuzelijst **[!UICONTROL Where are you calling the API from?]** de optie **[!UICONTROL Web Server (for example, node.js, Tomcat)]**

   * Van de **[!UICONTROL What data are you accessing?]** vervolgkeuzelijst, tikken **[!UICONTROL User data]**.

   ![6_5_googleaccount-apis-createcredentials2](assets/6_5_googleaccount-apis-createcredentials2.png)

1. Tik op **[!UICONTROL What credentials do I need?]**
1. Voer op de pagina **[!UICONTROL Add credentials to your project]** in stap 2 onder de kop **[!UICONTROL Create an OAuth 2.0 client ID]** in het veld Naam desgewenst een unieke naam in. U kunt ook de standaardnaam gebruiken die door Google is opgegeven.
1. Onder de **[!UICONTROL Authorized JavaScript origins]** Voer in het tekstveld het volgende pad in, waarbij u uw eigen domein- en poortnummer in het pad vervangt en druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>`

   Bijvoorbeeld, `https://1a2b3c.mycompany.com:4321`

   **Opmerking**: Het bovenstaande padvoorbeeld is alleen bedoeld voor demonstratiedoeleinden.

   ![6_5_googleaccount-apis-createcredentials-oauth](assets/6_5_googleaccount-apis-createcredentials-oauth.png)

1. Onder de **[!UICONTROL Authorized redirect URIs]** Voer in het tekstveld het volgende pad in, waarbij u uw eigen domein- en poortnummer in het pad vervangt en druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Bijvoorbeeld, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **Opmerking**: Het bovenstaande padvoorbeeld is alleen bedoeld voor demonstratiedoeleinden.

1. Klik op **[!UICONTROL Create OAuth client ID]**.
1. Selecteer op de pagina **[!UICONTROL Add credentials to your project]** in stap 3 onder de kop **[!UICONTROL Set up the OAuth 2.0 consent screen]** het e-mailadres van Gmail dat u momenteel gebruikt.

   ![6_5_googleaccount-apis-createcredentials-consentscreen](assets/6_5_googleaccount-apis-createcredentials-consentscreen.png)

1. Onder de **[!UICONTROL Product name shown to users]** Voer in het tekstveld in wat u wilt weergeven op het instemmingsscherm.

   Het toestemmingsscherm wordt getoond aan de beheerder van de Experience Manager wanneer zij aan YouTube voor authentiek verklaren; Experience Manager neemt contact op met YouTube voor toestemming.

1. Klik op **[!UICONTROL Continue]**.
1. Tik op de pagina Referenties aan uw project toevoegen in stap 4 onder de kop **[!UICONTROL Download credentials]** op **[!UICONTROL Download]**.

   ![6_5_googleaccount-apis-createcredentials-downloadcredentials](assets/6_5_googleaccount-apis-createcredentials-downloadcredentials.png)

1. Sla de `client_id.json` bestand.

   U hebt dit gedownloade json-bestand nodig wanneer u YouTube later instelt in Adobe Experience Manager.

1. Klik op **[!UICONTROL Done]**.

   Log uit op je Google account. Maak nu een YouTube-kanaal.

### Een YouTube-kanaal maken {#creating-a-youtube-channel}

Voor het publiceren van video&#39;s naar YouTube hebt u een of meer kanalen nodig. Als u al een YouTube-kanaal hebt gemaakt, kunt u deze taak overslaan en naar [Codes toevoegen voor publicatie](/help/assets/video.md#adding-tags-for-publishing).

>[!WARNING]
>
>Zorg ervoor dat u al een of meer kanalen hebt ingesteld in YouTube *voor* u voegt kanalen toe onder YouTube Settings in Experience Manager (zie [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem) hieronder). Als u een of meer kanalen niet instelt, wordt u niet gewaarschuwd voor niet-bestaande kanalen. Google-verificatie vindt echter nog steeds plaats wanneer u een kanaal toevoegt, maar er is geen optie om te kiezen welk kanaal de video wordt verzonden.

**Een YouTube-kanaal maken:**

1. Ga naar [https://www.youtube.com](https://www.youtube.com/) en meld u aan met uw aanmeldingsgegevens van uw Google-account.
1. Klik in de rechterbovenhoek van de YouTube-pagina op de profielafbeelding (kan ook als een letter in een cirkel met effen kleuren worden weergegeven) en klik vervolgens op **[!UICONTROL YouTube settings]** (rondtandwielpictogram).
1. Klik op de pagina Overzicht onder de kop Extra functies op **[!UICONTROL See all my channels or create a channel]**.
1. Klik op de pagina Kanalen op **[!UICONTROL Create a new channel]**.
1. Voer op de pagina Brand Account in het veld Brand Account Name een bedrijfsnaam of een andere kanaalnaam in die u kiest waar u de video-elementen wilt publiceren en klik vervolgens op **[!UICONTROL Create]**.

   Onthoud de naam die u hier invoert, omdat u deze opnieuw moet invoeren wanneer u YouTube instelt in Experience Manager.

1. (Optioneel) Voeg desgewenst meer kanalen toe.

   Voeg nu codes toe voor publicatie.

### Codes toevoegen voor publicatie {#adding-tags-for-publishing}

Als u video&#39;s naar YouTube wilt publiceren, koppelt de Experience Manager de tags aan een of meer YouTube-kanalen. Als u tags wilt toevoegen voor publicatie, raadpleegt u [Tags beheren](/help/sites-administering/tags.md).

Of als u de standaardlabels in de Experience Manager wilt gebruiken, kunt u deze taak overslaan en naar [De YouTube Publish Replication-agent inschakelen](#enabling-the-youtube-publish-replication-agent).

### De YouTube Publish Replication-agent inschakelen {#enabling-the-youtube-publish-replication-agent}

Als u de YouTube Publish Replication Agent hebt ingeschakeld en u de verbinding met de Google Cloud-account wilt testen, tikt u op **[!UICONTROL Test Connection]**. Op het tabblad Browser worden de verbindingsresultaten weergegeven. Als u YouTube-kanalen hebt toegevoegd, wordt een lijst met kanalen weergegeven als onderdeel van de test.

1. Klik in de linkerbovenhoek van de Experience Manager op het logo van de Experience Manager en klik vervolgens in de linkerspoorstaaf op **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. Klik op de pagina Agents van auteur op **[!UICONTROL YouTube Publish]**.
1. Klik op de werkbalk rechts van Instellingen op **[!UICONTROL Edit]**.
1. Selecteer **[!UICONTROL Enabled]** checkbox zodat kunt u de replicatieagent aanzetten.
1. Klik op **[!UICONTROL OK]**.

   Stel nu YouTube in Experience Manager in.

### YouTube instellen in Experience Manager {#setting-up-youtube-in-aem}

Vanaf Experience Manager 6.4 is een nieuwe aanraakgebruikersinterfacemethode geïntroduceerd om YouTube-publicaties in Experience Manager in te stellen. Op basis van de geïnstalleerde Experience Manager die u gebruikt, voert u een van de volgende handelingen uit:

* Om YouTube in Experience Manager vóór 6.4 te vormen, zie [YouTube instellen in Experience Manager vóór 6.4](/help/assets/video.md#setting-up-youtube-in-aem-before).
* Om YouTube in Experience Manager 6.4 of later te vormen, zie [YouTube instellen in Experience Manager 6.4 en hoger](#setting-up-youtube-in-aem-and-later).

#### YouTube instellen in Experience Manager 6.4 en hoger {#setting-up-youtube-in-aem-and-later}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.
1. Tik in de linkerbovenhoek op het logo van de Experience Manager en tik vervolgens in de linkerspoorstaaf op **[!UICONTROL Tools]**(hamerpictogram) > **[!UICONTROL Cloud Services]** > **[!UICONTROL YouTube Publishing Configuration]**.
1. Tikken **[!UICONTROL global]** (niet selecteren).

1. Tik in de rechterbovenhoek van de algemene pagina op **[!UICONTROL Create]**.
1. Voer op de pagina YouTube-configuratie maken onder Google Cloud-platforminstellingen in het veld **[!UICONTROL Application Name]** de Google-project-id in.

   U hebt de project-id opgegeven toen u de Google Cloud-instellingen voor het eerst eerder hebt geconfigureerd.
Laat de pagina YouTube-configuratie maken open. zo kom je er nog op terug .

   ![6_5_youtubepublish-createyoutubeconfiguration](assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder in de taak hebt gedownload en opgeslagen [Google Cloud-instellingen configureren](/help/assets/video.md#configuring-google-cloud-settings).
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]**.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Tik op **[!UICONTROL Add Channel]**.
1. Voer in het veld Kanaalnaam de naam in van het kanaal dat u in de taak hebt gemaakt **[!UICONTROL Adding one or more channels to YouTube]** eerder.

   U kunt desgewenst een beschrijving toevoegen.

1. Tik op **[!UICONTROL Add]**.
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet. het is geen kanaal .
   * Tik op de volgende pagina op **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Tik op **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Tik op de pagina Cloud Services > YouTube op het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Tik op het pictogram van de vervolgkeuzelijst (ondersteboven), zodat u de lijst met beschikbare labels in de Experience Manager kunt weergeven.
1. Tik op een of meer tags zodat u deze kunt toevoegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en tikt u op **[!UICONTROL X]**.

1. Tik op **[!UICONTROL Save]**.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

#### YouTube instellen in Experience Manager vóór 6.4 {#setting-up-youtube-in-aem-before}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.

1. Tik in de linkerbovenhoek op het logo van de Experience Manager en tik vervolgens in de linkerspoorstaaf op **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Onder de rubriek Services van derden tikt u onder YouTube op **[!UICONTROL Configure now]**.
1. Voer in het dialoogvenster Configuratie maken een titel (verplicht) en een naam (optioneel) in de desbetreffende velden in.
1. Tik op **[!UICONTROL Create]**.
1. Voer in het veld **[!UICONTROL Application Name]** in het dialoogvenster YouTube-accountinstellingen de Google-project-id in.

   U hebt de project-id opgegeven toen u het eerst [geconfigureerde Google Cloud-instellingen](/help/assets/video.md#configuring-google-cloud-settings) eerder.
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

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet. het is geen kanaal .
   * Tik op de volgende pagina op **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Tik op **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Tik op de pagina Cloud Services > YouTube op het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Tik op het pictogram van de vervolgkeuzelijst (ondersteboven), zodat u de lijst met beschikbare labels in de Experience Manager kunt weergeven.
1. Tik op een of meer tags zodat u deze kunt toevoegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en tikt u op **X**.

1. Tik op **[!UICONTROL OK]**.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

### (Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

U kunt desgewenst de instelling van YouTube-eigenschappen automatiseren bij het uploaden van uw video&#39;s door een verwerkingsprofiel voor metagegevens in Experience Manager te maken.

Als u het verwerkingsprofiel voor metadata wilt maken, kopieert u eerst waarden uit de velden **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]** en **[!UICONTROL Choices]** die te vinden zijn in de metadataschema&#39;s voor video. Vervolgens kunt u het verwerkingsprofiel voor YouTube-videometagegevens samenstellen door deze waarden eraan toe te voegen.

U kunt als volgt de standaardeigenschappen van YouTube voor uw geüploade video&#39;s automatiseren:

1. Tik in de linkerbovenhoek op het logo van de Experience Manager en klik vervolgens in de linkerspoorstaaf op **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. Klik op **[!UICONTROL default]**. (Voeg geen vinkje toe aan het selectievak links van &quot;standaard&quot;.)
1. Op de **[!UICONTROL default]** pagina, schakel het selectievakje links van **[!UICONTROL video]** tikt u vervolgens op **[!UICONTROL Edit]**.
1. Tik op de pagina Metadata Schema Editor op de knop **[!UICONTROL Advanced]** tab.
1. Klik onder de kop YouTube-publicatie op **[!UICONTROL YouTube Category]**.
1. Aan de rechterkant van de pagina, onder de **[!UICONTROL Settings]** doet u het volgende:

   * In de **[!UICONTROL Map to property]** tekstveld, selecteer en kopieer de waarde.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Onder **[!UICONTROL Choices]**selecteert en kopieert u de standaardwaarde die u wilt gebruiken (zoals Personen en blogs of Wetenschap en Technologie).
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Tik onder de kop YouTube Publishing op **[!UICONTROL YouTube Privacy]**.
1. Aan de rechterkant van de pagina, onder de **[!UICONTROL Settings]** doet u het volgende:

   * In de **[!UICONTROL Map to property]** tekstveld, selecteer en kopieer de waarde.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Onder **[!UICONTROL Choices]**selecteert en kopieert u de standaardwaarde die u wilt gebruiken. De keuzen zijn gegroepeerd in twee. Het onderste veld in het paar is de standaardwaarde die u wilt kopiëren, bijvoorbeeld public, unlist of private.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Klik in de rechterbovenhoek van de pagina Metadata Schema Editor op **[!UICONTROL Cancel]**.
1. Tik in de linkerbovenhoek van de Experience Manager op het logo van de Experience Manager en klik vervolgens in de linkerspoorstaaf op **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]**.

1. Klik in de rechterbovenhoek van de pagina Metagegevensprofielen op **[!UICONTROL Create]**.
1. Voer in het tekstveld **[!UICONTROL Profile title]** in het dialoogvenster Metadataprofiel toevoegen de naam `YouTube Video` in en klik vervolgens op **[!UICONTROL Create]**.
1. Klik op de pagina Metagegevensprofieleditor op de knop **[!UICONTROL Advance]** tab.
1. Voeg de gekopieerde YouTube Publishing-waarden als volgt toe aan het profiel:

   * Klik rechts van de pagina op de knop **[!UICONTROL Build Form]** tab.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en neer in het formuliergebied.
   * (Optioneel) Klik op **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label de tekst `YouTube Publishing`.
   * Klik op de knop **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en laat het onder de **[!UICONTROL YouTube Publishing]** koptekst die u hebt gemaakt.

   * Klikken **[!UICONTROL Field Label]** de component is dus geselecteerd.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Voeg de gekopieerde YouTube-privacywaarden als volgt toe aan het profiel:

   * Klik rechts van de pagina op de knop **[!UICONTROL Build Form]** tab.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en neer in het formuliergebied.
   * (Optioneel) Klik op **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label de tekst `YouTube Privacy`.
   * Klik op de knop **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en laat het onder de **[!UICONTROL YouTube Privacy]** door u gemaakte koptekst.

   * Klikken **[!UICONTROL Field Label]** de component is dus geselecteerd.
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
>Voor het publiceren van inhoud vanuit YouTube gebruikt Experience Manager de optie **[!UICONTROL Publish to YouTube]** werkstroom, waarmee u de voortgang kunt controleren en eventuele foutgegevens kunt bekijken.
>
>Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).
>
>Voor gedetailleerdere voortgangsgegevens kunt u het YouTube-logboek onder replicatie controleren. Houd er echter rekening mee dat voor dergelijke bewaking beheerderstoegang vereist is.

**Video&#39;s publiceren naar uw YouTube-kanaal:**

1. Navigeer in Experience Manager naar een video-element dat u naar het YouTube-kanaal wilt publiceren.
1. Selecteer het video-element (de adaptieve videoset).
1. Klik op de werkbalk op **[!UICONTROL Properties]**.
1. Klik op het tabblad Standaard onder de kop Metagegevens op **[!UICONTROL Open Selection Dialog]** rechts van het veld Tags.
1. Navigeer op de pagina Codes selecteren naar de gewenste codes en selecteer een of meer codes.

   Vergeet niet dat de tags moeten worden gekoppeld aan het YouTube-kanaal.

1. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Select]**.
1. Klik in de rechterbovenhoek van de eigenschappenpagina van de video op **[!UICONTROL Save and Close]**.
1. Klik op de werkbalk op **[!UICONTROL Quick Publish]**.

   Zie ook [Publicatiebeheer gebruiken met Experience Manager Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html).

   U kunt desgewenst de gepubliceerde video op uw YouTube-kanaal verifiëren.

### (Optioneel) Controleer de gepubliceerde video op YouTube {#optional-verifying-the-published-video-on-youtube}

U kunt optioneel de voortgang van het publiceren van YouTube (of het ongedaan maken van het publiceren) volgen.

Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

De het publiceren tijden kunnen zeer afhankelijk van talrijke factoren variëren die het formaat van uw primaire bronvideo, dossiergrootte, en uploadverkeer omvatten. Het publicatieproces kan een paar minuten tot enkele uren duren. Bovendien worden indelingen met een hogere resolutie veel langzamer gerenderd. Het duurt bijvoorbeeld langer om 720p en 1080p weer te geven dan 480p.

Na acht uur als je nog steeds een statusbericht ziet dat **[!UICONTROL Uploaded (processing, please wait)]**, verwijdert u de video van de Adobe en uploadt u deze opnieuw.

### YouTube-URL&#39;s koppelen aan uw webtoepassing {#linking-youtube-urls-to-your-web-application}

U kunt een YouTube URL-tekenreeks verkrijgen die door Dynamic Media wordt gegenereerd nadat u de video hebt gepubliceerd. Wanneer u de YouTube-URL kopieert, wordt deze op het Klembord gedownload, zodat u deze indien nodig kunt plakken naar pagina&#39;s in uw website of toepassing.

>[!NOTE]
>
>De YouTube-URL kan pas worden gekopieerd nadat u het video-element naar YouTube hebt gepubliceerd.

**YouTube-URL&#39;s koppelen aan uw webtoepassing:**

1. Ga naar de *YouTube gepubliceerd* video-element waarvan u de URL die u wilt kopiëren wilt selecteren.

   Houd er rekening mee dat YouTube-URL&#39;s alleen beschikbaar zijn om te kopiëren *na* u hebt de eerste *gepubliceerd* de video-elementen naar YouTube.

1. Klik op de werkbalk op **[!UICONTROL Properties]**.
1. Klik op de knop **[!UICONTROL Advanced]** tab.
1. Selecteer onder YouTube Publishing in de URL-lijst van YouTube de URL-tekst die u naar uw webbrowser wilt kopiëren om een voorvertoning van het element weer te geven of om deze toe te voegen aan uw pagina met webinhoud.

### Publiceren van video&#39;s ongedaan maken zodat u deze kunt verwijderen uit YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Wanneer u de publicatie van een video-element in Experience Manager ongedaan maakt, wordt de video verwijderd uit YouTube.

>[!CAUTION]
>
>Als u een video rechtstreeks uit YouTube verwijdert, is de Experience Manager zich hiervan niet bewust en gedragen deze zich alsof de video nog steeds naar YouTube wordt gepubliceerd. Publiceer de publicatie van een video-element vanuit YouTube altijd ongedaan als Experience Manager.

>[!NOTE]
>
>Om inhoud uit YouTube te verwijderen, gebruikt de Experience Manager **[!UICONTROL Unpublish from YouTube]** werkstroom, waarmee u de voortgang kunt controleren en eventuele foutgegevens kunt bekijken.
>
>Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

**Publiceren van video&#39;s ongedaan maken om deze uit YouTube te verwijderen:**

1. Navigeer naar de video-elementen waarvan u de publicatie via uw YouTube-kanaal wilt ongedaan maken.
1. Selecteer in de modus voor middelenselectie een of meer gepubliceerde video-elementen.
1. Klik op de werkbalk op **[!UICONTROL Manage Publication]**. Tik op het pictogram met drie puntjes (. . .) op de werkbalk **[!UICONTROL Manage Publication]** wordt geopend.
1. Tik op de pagina Publicatie beheren op **[!UICONTROL Unpublish]**.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Next]**.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Unpublish]**.

## Video-codering en YouTube-publicatievoortgang controleren {#monitoring-video-encoding-and-youtube-publishing-progress}

Wanneer u een nieuwe video uploadt naar een map waarop videocodering is toegepast, of wanneer u uw video publiceert naar YouTube, kunt u controleren hoe de videocodering/YouTube-publicatie vordert. Werkelijke vorderingen bij het publiceren in YouTube zijn alleen beschikbaar via de logboeken. De mislukking of het succes ervan wordt echter vermeld op aanvullende manieren die in de volgende procedure worden beschreven. Bovendien ontvangt u e-mailmeldingen wanneer een publicatieworkflow of videocodering van YouTube is voltooid of onderbroken.

### Voortgang van controle {#monitoring-progress}

1. Voortgang videocodering weergeven in map met elementen:

   * In de kaartweergave wordt de voortgang van de videocodering met een percentage weergegeven op het element. Als er een fout optreedt, wordt deze informatie ook weergegeven op het element.

   ![chlimage_1-429](assets/chlimage_1-429.png)

   * In de lijstweergave wordt de voortgang van de videocodering weergegeven in het dialoogvenster **[!UICONTROL Processing Status]** kolom. Als er een fout is, wordt dit bericht in dezelfde kolom weergegeven.

   ![chlimage_1-430](assets/chlimage_1-430.png)

   Deze kolom wordt niet standaard weergegeven. Als u de kolom wilt inschakelen, selecteert u **[!UICONTROL View Settings]** in het vervolgkeuzemenu Weergaven en voegt u de kolom **[!UICONTROL Processing Status]** toe en tikt of klikt u op **[!UICONTROL Update]**.

   ![chlimage_1-431](assets/chlimage_1-431.png)

1. De voortgang van de elementen weergeven. Als u op een element tikt of erop klikt, opent u het vervolgkeuzemenu en selecteert u **[!UICONTROL Timeline]**. Selecteer **[!UICONTROL Workflows]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Workflowinformatie, zoals codering, wordt weergegeven in de tijdlijn. Voor YouTube-publicatie bevat de tijdlijn van de workflow ook de naam van het YouTube-kanaal en de YouTube-video-URL. Bovendien ziet u eventuele foutmeldingen in de tijdlijn van de workflow nadat het publiceren is voltooid.

   >[!NOTE]
   >
   >Het kan lang duren voordat foutberichten of foutberichten definitief worden opgenomen omdat er meerdere workflowconfiguraties zijn **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >    * Configuratie Apache Sling-taakwachtrij
   >    * Adobe Granite-workflow - Externe verwerking van taken
   >    * Tijdelijke wachtrij voor Granite Workflow

   >
   >U kunt de **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** eigenschappen in deze configuraties.

1. Zie Workflowinstanties beschikbaar via **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instances]** voor actieve workflows.

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Selecteer de instantie en tik op **[!UICONTROL Open History]**.

   ![chlimage_1-434](assets/chlimage_1-434.png)

   Vanuit het gebied Workflowinstanties kunt u workflows ook opschorten, beëindigen of hernoemen. Zie [Workflows beheren](/help/sites-administering/workflows-administering.md) voor meer informatie .

1. Voor mislukte taken raadpleegt u de beschikbare workflowfouten in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Failures]**. De lijst **[!UICONTROL Workflow Failure]** bevat alle mislukte workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Het kan lang duren voordat het foutbericht eindelijk is opgenomen omdat er meerdere workflowconfiguraties zijn **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >
   >
   >    * Configuratie Apache Sling-taakwachtrij
   >    * Adobe Granite-workflow - Externe verwerking van taken
   >    * Tijdelijke wachtrij voor Granite Workflow

   >
   >
   >U kunt de **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** eigenschappen in deze configuraties.

1. Zie Workflowarchief in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archive]** voor voltooide workflows. In **[!UICONTROL Workflow Archive]** vindt u een lijst met alle voltooide workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. U ontvangt e-mailmeldingen over afgebroken of mislukte workflowtaken. Deze e-mailberichten kunnen door een beheerder worden geconfigureerd. Zie [E-mailmeldingen configureren](#configuring-e-mail-notifications).

#### E-mailmeldingen configureren {#configuring-e-mail-notifications}

>[!NOTE]
>
>U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

Hoe u een melding configureert, hangt af van het feit of u meldingen voor coderingstaken of YouTube-publicatietaken wilt:

* Voor coderingstaken hebt u toegang tot de configuratiepagina voor alle e-mailmeldingen over de workflow van de Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** en door te zoeken naar **[!UICONTROL Day CQ Workflow Email Notification Service]**. Zie [E-mailmelding configureren in Experience Manager](/help/sites-administering/notification.md). U kunt de selectievakjes voor **[!UICONTROL Notify on Abort]** of **[!UICONTROL Notify on Complete]** dienovereenkomstig.

* Ga als volgt te werk voor publicatietaken in YouTube:

1. Tik in Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina Workflowmodellen **[!UICONTROL Publish to YouTube]** tikt u vervolgens op **[!UICONTROL Edit]** op de werkbalk.
1. Tik in de rechterbovenhoek van de pagina Publiceren op YouTube-workflow op **[!UICONTROL Edit]**.
1. Houd de muisaanwijzer boven op de YouTube-component Upload en tik één keer om de inlinewerkbalk weer te geven.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. Tik op de inlinewerkbalk op het configuratiepictogram (moersleutel). Klik op de knop **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. Tik in het dialoogvenster YouTube Upload Process - Step Properties op de knop **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. U kunt de volgende selectievakjes in- of uitschakelen:

   * Start publiceren
   * Publicatiefout
   * Voltooien publiceren - bevat informatie over kanalen en URL&#39;s

   Als u een selectievakje wist, ontvangt u geen e-mailbericht van de publicatieworkflow van YouTube.

   >[!NOTE]
   >
   >Deze e-mailberichten zijn specifiek voor YouTube en vormen een aanvulling op de algemene e-mailmeldingen over de workflow. Dientengevolge kunt u twee reeksen e-mailbericht ontvangen - het generische bericht beschikbaar in **[!UICONTROL Day CQ Workflow Email Notification Service]** en één specifiek voor YouTube, afhankelijk van uw configuratie-instellingen.

1. Tik op de knop **[!UICONTROL Done]** pictogram (vinkje).
1. Tik op de pagina Publiceren naar YouTube-workflow rechtsboven in het scherm op **[!UICONTROL Sync]**.

## Videorapporten weergeven {#viewing-video-reports}

>[!NOTE]
>
>Videorapporten zijn alleen beschikbaar wanneer u de modus Dynamic Media - Hybride uitvoert.

Videorapporten geven verschillende statistische gegevens over een bepaalde tijd weer, zodat u kunt controleren of *gepubliceerde *individuele en geaggregeerde video&#39;s naar behoren functioneren. De volgende statistische gegevens worden geaggregeerd voor alle gepubliceerde video&#39;s op uw gehele website:

* Video start
* Voltooiingssnelheid
* Gemiddelde tijd op video
* Totale tijd op video
* Video&#39;s per bezoek

Een tabel met alle *gepubliceerd* de video&#39;s worden ook vermeld, zodat u de bovenste weergegeven video&#39;s op uw website kunt bijhouden op basis van het totale aantal video&#39;s dat wordt gestart.

Wanneer u op een videonaam in de lijst tikt, ziet u het rapport voor het behoud van het publiek van de video (drop-off) in de vorm van een lijndiagram. Het diagram toont het aantal weergaven voor een bepaald tijdstip tijdens het afspelen van video. Wanneer u de video afspeelt, wordt de verticale balk gesynchroniseerd met de tijdindicator in de speler. De vallen in de gegevens van het lijndiagram wijzen op waar uw publiek van oninteresse wegvalt.

Als de video buiten Adobe Experience Manager Dynamic Media is gecodeerd, zijn het diagram voor het vasthouden van het publiek (drop-off) en de gegevens voor het afspeelpercentage in de tabel niet beschikbaar.

Zie ook [Dynamic Media-Cloud Services configureren](/help/assets/config-dynamic.md).

>[!NOTE]
>
>Het bijhouden en rapporteren van gegevens is uitsluitend gebaseerd op het gebruik van de eigen videospeler van Dynamic Media en de bijbehorende voorinstelling van de videospeler. U kunt dus geen video&#39;s bijhouden en rapporteren die door andere videospelers worden afgespeeld.

Door gebrek, de eerste keer u VideoRapporten ingaat, toont het rapport videogegevens die bij de eerste van de huidige maand beginnen en met de datum van de huidige maand beëindigen. U kunt het standaarddatumbereik echter overschrijven door uw eigen datumbereik op te geven. De volgende keer dat u Video-rapporten invoert, wordt het opgegeven datumbereik gebruikt.

Voor het correct werken van videorapporten, wordt een identiteitskaart van de Reeks van het Rapport automatisch gecreeerd wanneer de Cloud Services van Dynamic Media wordt gevormd. Tegelijkertijd wordt de rapportsuite-id doorgegeven aan de publicatieserver, zodat deze beschikbaar is voor de functie URL kopiëren wanneer u een voorvertoning van elementen weergeeft. Deze functionaliteit vereist echter dat de publicatieserver al is ingesteld. Als de publicatieserver niet is ingesteld, kunt u toch publiceren om het videoverslag te zien. U moet echter terugkeren naar de Dynamic Media Cloud Configuration en tikken **[!UICONTROL OK]**.

**Videorapporten weergeven:**

1. Tik in de linkerbovenhoek van de Experience Manager op het logo van de Experience Manager en tik vervolgens in de linkerspoorstaaf op **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Video Reports]**.
1. Voer een van de volgende handelingen uit op de pagina Videorapporten:

   * Tik in de rechterbovenhoek op de knop **Videorapport vernieuwen** pictogram.
Gebruik alleen Vernieuwen als de einddatum van het rapport de huidige dag is. Dit zorgt ervoor dat u de video het volgen ziet die sinds de laatste tijd is voorgekomen u het rapport in werking stelde.

   * Tik in de rechterbovenhoek op de knop **Datumkiezer** pictogram.
Geef het begin- en einddatumbereik op waarvoor u videogegevens wilt en tik vervolgens op **[!UICONTROL Run Report]**.

   Het groepsvak Bovenste metagegevens identificeert verschillende samengestelde metingen voor alle *gepubliceerd* video&#39;s op uw site.

1. Tik in de tabel met de bovenste gepubliceerde video&#39;s op een videonaam om de video af te spelen en zie ook het rapport voor het vasthouden van het publiek van de video (drop-off).

### Videorapporten weergeven op basis van een videoviewer die u hebt gemaakt met de SDK van de Dynamic Media HTML5 Viewer {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Als u een uit-van-doos videoviewer gebruikt die door Dynamic Media wordt verstrekt, of als u een vooraf ingestelde douaneviewer creeerde die van een uit-van-doos videokijker wordt gebaseerd, dan worden geen extra stappen vereist om videorapporten te bekijken. Als u echter uw eigen videoviewer hebt gemaakt op basis van de HTML5 Viewer SDK API, voert u de volgende stappen uit om ervoor te zorgen dat uw videoviewer traceergebeurtenissen naar Dynamic Media Video Reports verzendt.

Gebruik de [Adobe Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html) en de [HTML5 Viewer SDK API](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) om uw eigen videoviewers te maken.

**U kunt als volgt videorapporten weergeven op basis van een videoviewer die u hebt gemaakt met de Dynamic Media HTML5 Viewer SDK:**

1. Navigeer naar een gepubliceerd video-element.
1. Selecteer in de vervolgkeuzelijst in de linkerbovenhoek van de assetpagina de optie **[!UICONTROL Viewers]**.
1. Selecteer een voorinstelling voor een videoviewer en kopieer de insluitcode.
1. Zoek in de insluitcode de regel met het volgende:

   `videoViewer.setParam("config2", "<value>");`

   De `config2` schakelt het bijhouden van gegevens in HTML5 Viewers in. Het is ook een bedrijf-specifieke vooraf ingesteld die de configuratieinformatie voor Video die, en voor klant-specifieke configuraties van Adobe Analytics bevat meldt.

   De correcte waarde voor de config2-parameter vindt u in zowel de functie **[!UICONTROL Embed Code]** als in de functie voor het kopiëren van de **[!UICONTROL URL]**. In de URL van de opdracht voor het kopiëren van de **[!UICONTROL URL]**, zoekt u naar de parameter `&config2=<value>`. De waarde is bijna altijd `companypreset`, maar in sommige gevallen ook `companypreset-1`, `companypreset-2`, enz.

1. Voeg in uw aangepaste videoviewercode AppMeasurementBridge .jsp als volgt toe aan de viewerpagina:

   * Bepaal eerst of u de `&preset` parameter.

      Als de `config2` parameter is `companypreset`, doet u dat *niet* behoefte `&preset=parameter`.

      Indien `config2` is om het even wat anders, plaats de vooraf ingestelde parameter het zelfde als `config2` parameter. Als `config2=companypreset-2`, toevoegen `&param2=companypreset-2` naar de URL AppMeasurmentBridge.jsp.

   * Voeg vervolgens het script AppMeasurementBridge.jsp toe:

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Maak als volgt de component TrackingManager:

   * Nadat u hebt gebeld `s7sdk.Util.init();`, creeer een instantie TrackingManager om gebeurtenissen te volgen door het volgende toe te voegen:

      `var trackingManager = new s7sdk.TrackingManager();`

   * Verbind componenten met TrackingManager door het volgende te doen:

      In de `s7sdk.Event.SDK_READY` gebeurtenismanager, maak de component vast u aan TrackingManager wilt volgen.

      Wanneer de component bijvoorbeeld `videoPlayer`, toevoegen

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

## Gesloten bijschriften of ondertitels toevoegen aan video {#adding-captions-to-video}

U kunt het bereik van uw video&#39;s uitbreiden naar wereldwijde markten door ondertiteling toe te voegen aan enkele video&#39;s of aan Adaptive Video Sets. Door ondertiteling toe te voegen, vermijdt u de behoefte om de audio te duwen, of de behoefte om inheemse sprekers te gebruiken om de audio voor elke verschillende taal opnieuw op te nemen. De video wordt afgespeeld in de taal waarin deze is opgenomen. Er verschijnen ondertitels in vreemde talen, zodat mensen in verschillende talen het audiogedeelte nog steeds kunnen begrijpen.

Ondertiteling met gesloten deuren maakt ook een betere toegankelijkheid mogelijk voor doven of slechthorenden.

>[!NOTE]
>
>De videospeler die u gebruikt moet de vertoning van titels steunen.

Zie ook [Toegankelijkheid in Dynamic Media](/help/assets/accessibility-dm.md).

Dynamic Media converteert bijschriftbestanden naar de indeling JSON (JavaScript Object Notation). Met deze conversie kunt u de JSON-tekst insluiten in een webpagina als een verborgen, maar volledige transcriptie van de video. Zoekprogramma&#39;s kunnen de inhoud vervolgens verkennen en indexeren, zodat de video&#39;s gemakkelijker te vinden zijn en klanten meer informatie krijgen over de video-inhoud.

Zie [Statische (niet-grafische) inhoud serveren](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) in de *Help bij Dynamic Media Image Serving and Rendering API* voor meer informatie over het gebruik van de functie JSON in een URL.

**Bijschriften of ondertitels toevoegen aan video:**

1. U kunt een toepassing of service van derden gebruiken om een ondertitelingsbestand of ondertitelingsbestand voor video te maken.

   Zorg ervoor dat het bestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsnaamextensie voor ondertiteling is .vtt. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

   Zie [WebVTT: De indeling Webvideoteksttracks](https://w3c.github.io/webvtt/).

   Er zijn zowel gratis als premiumtools en -services die u kunt gebruiken voor het schrijven van bijschriften en ondertitelingsbestanden buiten Dynamic Media. Als u bijvoorbeeld een eenvoudig videobijschriftbestand zonder opmaak wilt maken, kunt u de volgende gratis gereedschappen voor het maken en bewerken van bijschriften gebruiken:

   [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   U bereikt het beste resultaat met het gereedschap in Internet Explorer 9 of hoger, Google Chrome of Safari.

   In het hulpmiddel, in **[!UICONTROL Enter URL of video file]** veld, plak de gekopieerde URL van het videobestand en klik vervolgens op **[!UICONTROL Load]**. Zie [Een URL ophalen voor een element](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) om de URL naar het videobestand zelf op te halen, die u vervolgens in het deelvenster **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome of Safari kunnen de video vervolgens op een native manier afspelen.

   Volg nu de aanwijzingen op het scherm van de site om het WebVTT-bestand te ontwerpen en op te slaan. Wanneer u klaar bent, kopieert u de inhoud van het bijschriftbestand en plakt u het in een gewone teksteditor en slaat u het op met een `.vtt` bestandsnaamextensie.

   >[!NOTE]
   >
   >Voor algemene ondersteuning van videoondertitels in meerdere talen vereist de WebVTT-standaard dat u afzonderlijke .vtt-bestanden maakt en dat u voor elke taal die u wilt ondersteunen, een oproep doet.

   Over het algemeen wilt u het VTT-bestand van het bijschrift dezelfde naam geven als het videobestand en dit bestand toevoegen met de landinstelling van de taal, zoals -EN, -FR of -DE. Hierdoor kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.

1. Upload in Experience Manager uw WebVTT-bijschriftbestand naar DAM.
1. Ga naar de *gepubliceerd* video-element dat u wilt koppelen aan het bijschriftbestand dat u hebt geüpload.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*.

   Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md).

1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL URL]**. Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord en passeer de URL naar een eenvoudige teksteditor. Voeg de gekopieerde URL van de video toe met de volgende syntaxis:

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Noteer de `,1` aan het einde van het bijschriftpad. Onmiddellijk na de `.vtt` bestandsnaamextensie in het pad, kunt u optioneel de knop voor een gesloten bijschrift op de balk van de videospeler in- of uitschakelen (uitschakelen) door in te stellen op `,1` of `,0`, respectievelijk.

   * Tik op **[!UICONTROL Embed Code]**. Selecteer in het dialoogvenster Code insluiten de insluitcode en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor. Voeg de gekopieerde insluitcode toe met de volgende syntaxis:

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Noteer de `,1` aan het einde van het bijschriftpad. Onmiddellijk na de `.vtt` bestandsnaamextensie in het pad, kunt u optioneel de knop voor een gesloten bijschrift op de balk van de videospeler in- of uitschakelen (uitschakelen) door in te stellen op `,1` of `,0`, respectievelijk.

## Hoofdstukmarkeringen aan video toevoegen {#adding-chapter-markers-to-video}

U kunt uw lange formuliervideo&#39;s beter weergeven en navigeren door hoofdstukmarkeringen toe te voegen aan enkele video&#39;s of aan Adaptieve videosets. Wanneer een gebruiker de video afspeelt, kunnen hij of zij op de hoofdstukmarkeringen op de videotijdlijn (ook wel de videoscrubber genoemd) klikken om gemakkelijk naar zijn of haar interessepunt te navigeren. Of ze kunnen meteen naar nieuwe inhoud, demonstraties en zelfstudies gaan.

>[!NOTE]
>
>De videospeler die wordt gebruikt moet het gebruik van hoofdstukmarkeringen steunen. Dynamic Media-videospelers ondersteunen wel hoofdstukmarkeringen, maar het gebruik van videospelers van derden is mogelijk niet mogelijk.

Desgewenst kunt u uw eigen aangepaste videoviewer maken en markeren met hoofdstukken in plaats van een voorinstelling voor de videoviewer te gebruiken. Voor instructies voor het maken van uw eigen HTML5-viewer met hoofdstuknavigatie verwijst u in de SDK-API van de Adobe HTML5 Viewer naar de kop &quot;Gedrag aanpassen met behulp van wijzigingstoetsen&quot; onder de klassen `s7sdk.video.VideoPlayer` en `s7sdk.video.VideoScrubber`. Zie de [HTML5 Viewer SDK API](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) documentatie.

<!-- If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading "Customizing Behavior Using Modifiers" under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

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

In het bovenstaande voorbeeld: `Chapter 1` is de cue-id en is optioneel. De actieduur van `00:00:000 --> 01:04:364` geeft de begin- en eindtijd van het hoofdstuk aan, in `00:00:000` gebruiken. De laatste drie cijfers zijn milliseconden en kunnen als volgt worden verlaten `000`, indien gewenst. De titel van het hoofdstuk `The bicycle store behind it all` Dit is de feitelijke beschrijving van de inhoud van het hoofdstuk. De actidentificator, de begintijd en de hoofdstuktitel worden allemaal weergegeven in een pop-up van een videospeler wanneer een gebruiker de muisaanwijzer boven een visueel actiepunt in de tijdlijn van de video houdt.

Omdat u een HTML5-videoviewer gebruikt, moet u ervoor zorgen dat het hoofdstukbestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsextensie van het hoofdstuk is `.vtt`. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

Zie [WebVTT: De indeling Webvideoteksttracks](https://w3c.github.io/webvtt/)

**Navigatie voor videopunten toevoegen:**

1. Sla de `.vtt` bestand in UTF8-codering, zodat u problemen met tekenuitvoering in de hoofdstuktiteltekst voorkomt.

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
       <li>Ga naar de <i>gepubliceerd </i>video-element dat u wilt koppelen aan het hoofdstukbestand dat u hebt geüpload. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/publishing-dynamicmedia-assets.md">Middelen publiceren.</a></li>
       <li>Klik of tik in het keuzemenu op <strong>Viewers</strong>.</li>
       <li>Tik of klik in de linkertrack op de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>Klik in de linkerspoorstaaf onderaan op <strong>URL</strong>.</li>
       <li>Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord. Plak vervolgens de URL in een eenvoudige teksteditor.</li>
       <li>Voeg de gekopieerde URL van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Voor een ingesloten videoviewerervaring<br /> </td>
       <td>
       <ol>
       <li>Ga naar de <i>gepubliceerd </i>video-element dat u wilt koppelen aan het hoofdstukbestand dat u hebt geüpload. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/publishing-dynamicmedia-assets.md">Middelen publiceren.</a></li>
       <li>Klik of tik in het keuzemenu op <strong>Viewers</strong>.</li>
       <li>Tik of klik in de linkertrack op de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>Klik in de linkerspoorstaaf onderaan op <strong>Insluiten</strong>.</li>
       <li>Selecteer in het dialoogvenster Code insluiten de gehele code en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor.</li>
       <li>Voeg de insluitcode van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>

## Informatie over videominiaturen in de modus Dynamic Media - Scene7 {#about-video-thumbnails-in-dynamic-media-scene-mode}

Een videominiatuur is een verkleinde versie van een videoframe of een afbeeldingselement dat de video voor de klant vertegenwoordigt. De miniatuur moedigt een klant aan om op de video te klikken.

Aan alle video&#39;s in de Experience Manager moet een miniatuur zijn gekoppeld. u kunt een miniatuur niet verwijderen zonder deze te vervangen. Wanneer u een video uploadt naar Experience Manager, wordt standaard het eerste frame gebruikt als miniatuur. U kunt de miniatuur echter aanpassen voor bijvoorbeeld branding of visuele zoekopdracht. Wanneer u een videominiatuur aanpast, kunt u de video afspelen en pauzeren op het frame dat u wilt gebruiken. U kunt ook een afbeeldingselement selecteren dat u al hebt geüpload en *gepubliceerd* in uw Digital Asset Manager.

Een aangepaste videominiatuurafbeelding die u selecteert uit een video, wordt niet geëxtraheerd en in de DAM opgeslagen als een afzonderlijk en afzonderlijk element. Een aangepaste videominiatuur die u selecteert uit een bestaand afbeeldingselement, wordt echter opgeslagen in de tekenherkenning. Het pad van het geselecteerde element wordt opgeslagen onder het knooppunt van het video-element, zoals in het volgende voorbeeldpad:

`/content/dam/*<folder_name*>/<*video_name*>/jcr:content/manualThumbnail`

De mogelijkheid om een videominiatuur aan te passen is alleen beschikbaar nadat u een videoprofiel hebt toegepast op de map waarin de video zich bevindt.

Zie ook [Informatie over videominiaturen in Dynamic Media - hybride modus](#about-video-thumbnails-in-dynamic-media-hybrid-mode).

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail}

Deze stappen zijn alleen van toepassing op Dynamic Media die wordt uitgevoerd in de modus &quot;Dynamicmedia_Scene7&quot;.

**Een aangepaste videominiatuur toevoegen:**

1. Zorg ervoor dat u al het volgende hebt gedaan:

   * Er is een map gemaakt voor uw video-elementen.
   * [Een videoprofiel toepassen op de map](/help/assets/video-profiles.md#applying-a-video-profile-to-folders).

   * [Uw video&#39;s zijn geüpload naar de map](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

1. Navigeer naar een geüpload video-element waarvan u de miniatuurafbeelding wilt wijzigen.
1. In de modus voor selectie van middelen **[!UICONTROL List View]** of **[!UICONTROL Card View]** tikt u op het video-element.
1. Tik op de werkbalk op de knop **[!UICONTROL Properties]** pictogram (een cirkel met een &quot;i&quot; erin).
1. Tik op de eigenschappenpagina van de video op **[!UICONTROL Change Thumbnail]**.
1. Voer een van de volgende handelingen uit op de pagina Miniatuur wijzigen:

   * Een frame van de video gebruiken als de nieuwe miniatuur:

      * Tik op de werkbalk op **[!UICONTROL Select Frame from video]**.
      * Tik op de knop Afspelen en tik vervolgens op de knop Pauzeren op het frame dat u wilt vastleggen als de nieuwe miniatuur van de video.
   * Een afbeeldingselement gebruiken als de nieuwe miniatuur:

      * Tik op de werkbalk op **[!UICONTROL Select Thumbnail from Assets]**.
      * Tik op **[!UICONTROL Select Thumbnail]**.
      * Navigeer naar een eerder geüpload en gepubliceerd afbeeldingselement dat u wilt gebruiken. De grootte van het element wordt automatisch aangepast om te dienen als miniatuurafbeelding voor de video.
      * Selecteer het afbeeldingselement en tik vervolgens op **[!UICONTROL Select]**.


1. Tik op de pagina Miniatuur wijzigen op **[!UICONTROL Save Change]**.
1. Tik in de rechterbovenhoek op de pagina Eigenschappen van video op **[!UICONTROL Save & Close]**.

## Informatie over videominiaturen in Dynamic Media - hybride modus {#about-video-thumbnails-in-dynamic-media-hybrid-mode}

U kunt kiezen uit een van de tien miniatuurafbeeldingen die automatisch door Dynamic Media worden gegenereerd om aan uw video toe te voegen. De videospeler geeft de geselecteerde miniatuur weer wanneer een video-element wordt gebruikt met de Dynamic Media-component in de ontwerpomgeving van Experience Manager Sites, Experience Manager Mobile of Experience Managers Screens. De miniatuur fungeert als een statisch beeld dat de inhoud van de gehele video het beste vertegenwoordigt en dat gebruikers verder aanmoedigt om op de knop Afspelen te klikken.

Dynamic Media legt tien (standaard)miniatuurafbeeldingen vast op basis van de totale tijd van de video. De afbeeldingen worden vastgelegd op 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81% en 91% in de video. De tien miniaturen blijven bestaan. Dit betekent dat als u een andere miniatuur kiest, u de reeks niet opnieuw hoeft te genereren. U bekijkt een voorvertoning van de tien miniatuurafbeeldingen en selecteert vervolgens de miniatuurafbeelding die u voor de video wilt gebruiken. Als u wilt veranderen in het gebrek, kunt u CRXDE Lite gebruiken om het tijdinterval te vormen dat duimnagelbeelden worden geproduceerd. Als u bijvoorbeeld alleen een reeks van vier miniatuurafbeeldingen met gelijkmatige tussenruimte uit uw video wilt genereren, kunt u de intervaltijd instellen op 24%, 49%, 74% en 99%.

In het ideale geval kunt u een videominiatuur toevoegen nadat u de video hebt geüpload, maar voordat u de video op uw website publiceert.

Desgewenst kunt u een aangepaste miniatuur uploaden die uw video vertegenwoordigt in plaats van een miniatuur die door Dynamic Media is gegenereerd. U kunt bijvoorbeeld een aangepaste miniatuurafbeelding maken met de titel van uw video, een opvallende openingsafbeelding of een specifieke afbeelding die u van uw video hebt vastgelegd. De aangepaste videominiatuurafbeelding die u uploadt, moet een maximale resolutie van 1280 x 720 pixels (minimale breedte van 640 pixels) en niet groter zijn dan 2 MB.

Zie ook [Informatie over videominiaturen in de modus Dynamic Media - Scene7](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

### Een videominiatuur toevoegen {#adding-a-video-thumbnail}

Deze stappen zijn alleen van toepassing op Dynamic Media die wordt uitgevoerd in de hybride modus.

**Een videominiatuur toevoegen:**

1. Navigeer naar een geüpload video-element waaraan u een videominiatuur wilt toevoegen.
1. Tik in de modus voor middelenselectie in de lijstweergave of de kaartweergave op het video-element.
1. Tik op de werkbalk op de knop **[!UICONTROL View Properties]** pictogram (een cirkel met een &quot;i&quot; erin).
1. Tik op de eigenschappenpagina van de video op **[!UICONTROL Change Thumbnail]**.
1. Tik op de pagina Miniatuur wijzigen op de werkbalk op **[!UICONTROL Select Frame]**.

   Dynamic Media genereert een reeks miniatuurafbeeldingen van uw video op basis van het standaardtijdinterval of -interval dat u hebt aangepast.

1. Geef een voorvertoning van de gegenereerde miniatuurafbeeldingen weer en selecteer de miniatuurafbeelding die u aan de video wilt toevoegen.
1. Tik op **[!UICONTROL Save Change]**.

   De miniatuurafbeelding van de video wordt bijgewerkt en gebruikt nu de miniatuur die u hebt geselecteerd. Als u later besluit om de miniatuurafbeelding te wijzigen, kunt u terugkeren naar de **[!UICONTROL Change Thumbnail]** en selecteer een nieuwe pagina.

   Als u nieuwe standaardtijdintervallen hebt geconfigureerd of als u een nieuwe video hebt geüpload ter vervanging van de bestaande video, moet Dynamic Media de miniaturen opnieuw genereren.

   Zie [Configureer het standaardtijdinterval dat videominiaturen worden gegenereerd](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

#### Configureer het standaardtijdinterval dat videominiaturen worden gegenereerd {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

Wanneer u het nieuwe standaardtijdinterval configureert en opslaat, is uw wijziging automatisch alleen van toepassing op video&#39;s die u in de toekomst uploadt. De nieuwe standaardinstelling wordt niet automatisch toegepast op video&#39;s die u eerder hebt geüpload. Voor bestaande video&#39;s moet u de miniaturen opnieuw genereren.

Zie [Een videominiatuur toevoegen](#adding-a-video-thumbnail).

**U configureert als volgt het standaardtijdsinterval dat videominiaturen worden gegenereerd:**

1. Tik in Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. Navigeer op de pagina CRXDE Lite in het mappenvenster aan de linkerkant naar de pagina `o etc/dam/imageserver/configuration/jcr:content/settings.`

   Als het mappenvenster niet zichtbaar is, tikt u op het pictogram >> links van het tabblad Start.

1. Dubbeltik in het deelvenster rechtsonder op het tabblad Eigenschappen `thumbnailtime`.
1. In de **[!UICONTROL Edit thumbnailtime]** gebruikt u de tekstvelden om intervalwaarden in te voeren als percentages.

   * Tik op het plusteken (+) als u een of meer velden voor intervalwaarden wilt toevoegen. Blader zo nodig naar de onderkant van het dialoogvenster om het pictogram weer te geven.
   * Tik op het minteken (-) rechts van een veld voor de intervalwaarde als u dit wilt verwijderen uit de lijst.
   * Tik op het pictogram Pijl-omhoog en Pijl-omlaag als u de intervalwaarden opnieuw wilt rangschikken.

1. Tikken **[!UICONTROL OK]** en ga terug naar het tabblad Eigenschappen.
1. Tik in de linkerbovenhoek van de pagina CRXDE Lite op **[!UICONTROL Save All]** tikt u vervolgens op het pictogram Startpagina terug in de linkerbovenhoek om terug te keren naar de Experience Manager.

   Zie [Een videominiatuur toevoegen](#adding-a-video-thumbnail).

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail-1}

Deze stappen zijn alleen van toepassing op Dynamic Media die wordt uitgevoerd in de hybride modus.

**Een aangepaste videominiatuur toevoegen:**

1. Navigeer naar een geüpload video-element waaraan u een aangepaste miniatuur voor video wilt toevoegen.
1. Tik in de modus voor middelenselectie in de lijstweergave of de kaartweergave op het video-element.
1. Tik op de werkbalk op de knop **[!UICONTROL View Properties]** pictogram (een cirkel met een &quot;i&quot; erin).
1. Tik op de eigenschappenpagina van de video op **[!UICONTROL Change Thumbnail]**.
1. Tik op de pagina Miniatuur wijzigen op de werkbalk op **[!UICONTROL Upload New Thumbnail]**.
1. Navigeer naar een miniatuurafbeelding die u wilt gebruiken, selecteer deze en tik vervolgens op **[!UICONTROL Open]** om de afbeelding naar de Experience Manager te uploaden. Na het uploaden moet u de afbeelding publiceren.
1. Tik op **[!UICONTROL Save Changes]**.

   De aangepaste miniatuur wordt toegevoegd aan uw video.

## De Dynamic Media-URL voor Dynamic Media-elementen wijzigen {#manifest-urls}

Video&#39;s die in Dynamic Media worden verwerkt, kunnen worden gebruikt in de vorm van verouderde viewers en ook door rechtstreeks toegang te krijgen tot de manifest-URL&#39;s en deze af te spelen via uw eigen aangepaste viewers. Hier volgt de API voor het ophalen van manifest-URL&#39;s voor een video.

### Over de getVideoManifestURI-API

De `getVideoManifestURI`API is beschikbaar via c`q-scene7-api:com.day.cq.dam.scene7.api` en kan worden gebruikt om de volgende manifest-URL&#39;s te genereren:

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
| `resource` | De bron die correspondeert met de video die Dynamic Media heeft gegeten. |
| `manifestType` | Kan `ManifestType.DASH` of `ManifestType.HLS` |
| `onlyIfPublished` | Ingesteld op true voor het geval dat de manifest-uri alleen wordt gegenereerd als deze wordt gepubliceerd en beschikbaar is op de leveringslaag. |

Als u de manifest-URL&#39;s voor video&#39;s wilt ophalen met de bovenstaande methode, voegt u een [videocoderingsprofiel](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) naar een map voor het uploaden van video&#39;s. Dynamic Media verwerkt deze video&#39;s op basis van de coderingen in het videocoderingsbestand dat aan de map is toegewezen. Nu kunt u de bovenstaande API aanroepen om manifest-URL&#39;s voor de geüploade video&#39;s op te halen.

### Foutscenario&#39;s

De API retourneert null als er fouten zijn. Uitzonderingen worden geregistreerd in foutenlogboeken voor Experience Managers. Al dergelijke geregistreerde fouten beginnen met `Could not generate Video Manifest URI`. Dergelijke fouten kunnen in de volgende scenario&#39;s optreden:

* An `IllegalArgumentException` wordt geregistreerd voor om het even welk van het volgende:

   * De `resource` doorgegeven parameter is null.
   * De `resource` doorgegeven parameter is geen video.
   * De `manifestType` doorgegeven parameter is null.
   * De `onlyIfPublished` parameter wordt doorgegeven als true, maar de video wordt niet gepubliceerd.
   * De video is niet opgenomen met een adaptieve videoset van Dynamic Media.

* `IOException` wordt geregistreerd als er een probleem is dat verbinding maakt met Dynamic Media.
* `UnsupportedOperationException` wordt geregistreerd wanneer een `manifestType` doorgegeven parameter is `ManifestType.DASH`, terwijl de video niet is verwerkt met de indeling DASH.

Hieronder ziet u een voorbeeld van de bovenstaande API met behulp van servlets die in zijn geschreven *HTTPWhiteBoard* specificatie. Selecteer elk tabblad voor de codesyntaxis.

>[!BEGINTABS]

>[!TAB Afhankelijkheid toevoegen in pom.xml]

+++**Afhankelijkheid toevoegen in pom.xml**

```java
dependency> 
     <groupId>com.day.cq.dam</groupId> 
     <artifactId>cq-scene7-api</artifactId> 
     <version>5.12.64</version> 
     <scope>provided</scope> 
</dependency> 
```

+++

>[!TAB Sample-servlet]

+++**Sample-servlet**

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

>[!TAB Responsklasse voor servlet]

+++**Responsklasse voor servlet**

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

>[!TAB Constantenbestand waarnaar wordt verwezen in servlet]

+++**Constantenbestand waarnaar wordt verwezen in servlet**

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

>[!TAB ServletContext]

+++**ServletContext**

Bovenstaande servlet koppelen met een `servletContext`. Hier volgt een voorbeeld van `servletContext`.

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

U roept de servlet op door een `GET` bewerking bij `/dmSample/dynamicmedia/video/manifestUrl`. De volgende queryparameters worden doorgegeven:

| Query-parameter | Beschrijving |
| --- | --- |
| `assetPath` | Verplicht. Het pad naar de video waarvoor `manifestUrl` wordt gegenereerd. |
| `manifestType` | Optioneel. Parameter kan DASH of HLS zijn. Als het niet wordt overgegaan, blijft het aan DASH in gebreke. |
| `onlyIfPublished` | Optioneel. Indien geslaagd, `manifestUrl` wordt alleen geretourneerd als de video is gepubliceerd. |

In dit voorbeeld, laten wij de volgende opstelling veronderstellen:

* Het bedrijf is `samplecompany`.
* De ontwerpinstantie is `http://sample-aem-author.com`.
* De map `/content/dam/video-example` waarop een videocoderingsprofiel is toegepast.
* De video `scenery.mp4` wordt geüpload naar de map `/content/dam/video-example`.

U kunt de servlet op de volgende manieren aanroepen:

| Type | Beschrijving |
| :--- | --- |
| HLS | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=HLS&assetPath=/content/dam/video-example/scenery.mp4`<br><br>Als levering DASH is ingeschakeld:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8?packagedStreaming=true"}`<br><br>Als de levering DASH is uitgeschakeld:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8"}` |
| DASH | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scenery.mp4`<br><br>Als levering DASH is ingeschakeld:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.mpd"}`<br><br>Als de levering DASH is uitgeschakeld:<br>`{}` |
| Fout: middelenpad is onjuist | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scennnnnnery.mp4`<br><br>`{"errorString":"could not retrieve the resource from JCR"}` |


