---
title: Video
description: Leer over het gecentraliseerde video middelenbeheer Adobe Experience Manager Assets waar u video's voor automatische codering kunt uploaden naar Dynamic Media Classic en rechtstreeks vanuit Experience Manager Assets toegang hebt tot Dynamic Media Classic video's. Dynamic Media Classic video integration breidt het bereik van geoptimaliseerde video uit naar alle schermen.
uuid: 8b3423f1-d96b-44d9-bdb7-e3b77875b25d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
discoiquuid: 2685f9f3-0973-40a9-89b8-e7db0a6a75f2
role: User, Admin
mini-toc-levels: 3
exl-id: 56009925-1a36-48b5-b96c-ec2e468da106
feature: Video
source-git-commit: 77687a0674b939460bd34011ee1b94bd4db50ba4
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---

# Video {#video}

Adobe Experience Manager Assets biedt gecentraliseerd beheer van video-elementen waarmee u video&#39;s rechtstreeks kunt uploaden naar Middelen voor automatische codering naar Dynamic Media Classic en rechtstreeks vanuit Middelen toegang kunt krijgen tot Dynamic Media Classic-video&#39;s voor het ontwerpen van pagina&#39;s.

Dynamic Media Classic video integration breidt het bereik van geoptimaliseerde video uit tot alle schermen (automatische apparaat- en bandbreedtedetectie).

* De component **[!UICONTROL Scene7 Video]** voert automatisch apparaat- en bandbreedtedetectie uit om de juiste indeling en video van de juiste kwaliteit af te spelen op desktopcomputers, tablets en mobiele apparaten.
* Elementen - U kunt adaptieve videosets opnemen in plaats van alleen afzonderlijke video-elementen. Een adaptieve videoset bevat alle video-uitvoeringen die nodig zijn om video naadloos af te spelen op meerdere schermen. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. U gebruikt een adaptieve videoset, samen met de S7-videocomponent, voor adaptieve videostreaming op meerdere schermen, waaronder desktopapparaten, iOS, Android™, BlackBerry® en mobiele Windows-apparaten.
<!-- See [Scene7 documentation about adaptive video sets for more information](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html). -->

## Info over FFMPEG en Dynamic Media Classic {#about-ffmpeg-and-scene}

Het standaardvideocoderingsproces is gebaseerd op het gebruik van de op FFMPEG gebaseerde integratie met videoprofielen. Daarom bevat de uit-van-de-doos workflow voor DAM-opname de volgende twee op ffmpeg gebaseerde workflowstappen:

* FMPEG-miniaturen
* FFMPEG-codering

Als u de Dynamic Media Classic-integratie inschakelt en configureert, worden deze twee workflowstappen niet automatisch verwijderd of gedeactiveerd uit de workflow voor het innemen van DAM buiten de box. Als u de op FFMPEG gebaseerde videocodering al in Adobe Experience Manager gebruikt, is het waarschijnlijk dat FFMPEG is geïnstalleerd in uw ontwerpomgeving. In dit geval wordt een nieuwe video die met DAM wordt ingevoerd, twee keer gecodeerd: eenmaal van de FFMPEG-encoder en eenmaal van de Dynamic Media Classic-integratie.

Als u op FFMPEG-Gebaseerde videocodering in Experience Manager hebt gevormd en FFMPEG geïnstalleerd, adviseert Adobe dat u de twee werkschema&#39;s FFMPEG uit uw DAM inname werkschema&#39;s verwijdert.

## Ondersteunde indelingen {#supported-formats}

De volgende indelingen worden ondersteund voor de Scene7 Video-component:

* F4V H.264
* MP4 H.264

## Bepaal waar u de video wilt uploaden {#deciding-where-to-upload-your-video}

Bepaal waar u uw video-elementen wilt uploaden afhankelijk van het volgende:

* Hebt u een workflow voor het video-element nodig?
* Hebt u versiebeheer nodig voor het video-element?

Als het antwoord op een van deze vragen &quot;ja&quot; is, uploadt u uw video rechtstreeks naar Adobe DAM. Als het antwoord op beide vragen &quot;nee&quot; is, uploadt u uw video rechtstreeks naar Dynamic Media Classic. Het werkschema voor elk scenario wordt beschreven in de volgende sectie.

### Als u de video rechtstreeks uploadt naar Adobe DAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Als u een workflow of versie voor uw middelen nodig hebt, uploadt u deze eerst naar Adobe DAM. Hieronder vindt u de aanbevolen workflow:

1. Upload het video-element naar Adobe DAM en codeer en publiceer het automatisch naar Dynamic Media Classic.
1. In Experience Manager, heb toegang tot videoactiva in WCM op **[!UICONTROL Movies]** lusje van de Vinder van de Inhoud.
1. Auteur met **[!UICONTROL Scene7 Video]** of **[!UICONTROL Foundation Video]** component.

### Als u uw video uploadt naar Dynamic Media Classic {#if-you-are-uploading-your-video-to-scene}

Als u geen workflow of versie voor uw middelen nodig hebt, uploadt u uw middelen naar Scene7. Hieronder vindt u de aanbevolen workflow:

1. In Dynamic Media Classic stelt [een geplande FTP-upload en -codering in naar Scene7 (systeem geautomatiseerd)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#upload-files-using-via-ftp).
1. In Experience Manager, heb toegang tot videoactiva in WCM op **[!UICONTROL Scene7]** lusje van de Vinder van de Inhoud.
1. Auteur met de **[!UICONTROL Scene7 Video]** component.

## Integratie met Scene7 Video configureren {#configuring-integration-with-scene-video}

1. Navigeer in **[!UICONTROL Cloud Services]** naar de **[!UICONTROL Scene7]**-configuratie en selecteer **[!UICONTROL Edit]**.
1. Selecteer het tabblad **[!UICONTROL Video]**.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >Het tabblad **[!UICONTROL Video]** wordt niet weergegeven als de pagina geen cloudconfiguratie heeft.

1. Selecteer het adaptieve videocoderingsprofiel, een uit-van-de-doos enig videocoderingsprofiel, of een profiel van de douanevideocodering.

   >[!NOTE]
   >
   >Raadpleeg de [Klassieke documentatie van Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files) voor meer informatie over wat de videovoorinstellingen betekenen.
   >
   >Adobe raadt u aan beide adaptieve videosets te selecteren wanneer u de universele voorinstellingen configureert of de optie **[!UICONTROL Adaptive Video Encoding]** te selecteren.

1. De geselecteerde coderingsprofielen worden automatisch toegepast op alle video&#39;s die zijn geüpload naar de CQ DAM-doelmap die u hebt ingesteld voor deze Scene7-cloudconfiguratie. U kunt meerdere Scene7-cloudconfiguraties met verschillende doelmappen instellen om zo nodig verschillende coderingsprofielen toe te passen.

## Viewer- en coderingsvoorinstellingen bijwerken {#updating-viewer-and-encoding-presets}

Als u de voorinstellingen voor de viewer en codering voor video wilt bijwerken omdat de voorinstellingen in Scene7 zijn bijgewerkt, navigeert u naar de Scene7-configuratie in de Cloud Configuration en selecteert u **[!UICONTROL Update the viewer and encoding presets]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Upload uw primaire bronvideo naar Scene7 vanaf Adobe DAM {#uploading-your-master-video}

1. Navigeer naar de doelmap CQ DAM waar u de cloudconfiguratie hebt ingesteld met Scene7-coderingsprofielen.
1. Selecteer **[!UICONTROL Upload]** om primaire bronvideo te uploaden. Het uploaden en coderen van video is voltooid nadat de [!UICONTROL DAM Update Asset]-workflow is voltooid en **[!UICONTROL Publish to Scene7]** een vinkje heeft.

   >[!NOTE]
   >
   >Het genereren van videominiaturen duurt langer.

   Door de primaire DAM-bronvideo naar het videoonderdeel te slepen, wordt toegang verkregen tot *all* door Scene7 gecodeerde proxyuitvoeringen voor levering.

## Foundation Video Component versus Scene7 Video Component {#foundation-video-component-versus-scene-video-component}

Wanneer u Experience Manager gebruikt, hebt u toegang tot zowel de videocomponent Video beschikbaar in Sites als de videocomponent van Scene7. Deze componenten zijn niet onderling verwisselbaar.

De Scene7-videocomponent werkt alleen voor Scene7-video&#39;s. De stivingscomponent werkt met video&#39;s die zijn opgeslagen vanuit Experience Manager (met behulp van mpeg) en Scene7-video&#39;s.

De volgende matrix legt uit wanneer de component moet worden gebruikt:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>De videocomponent S7 gebruikt het universele videoprofiel uit het vak. U kunt de op HTML5 gebaseerde videospeler echter verkrijgen voor gebruik door Experience Manager. Kopieer in Scene7 de insluitcode van de HTML5-videospeler uit de doos en plaats deze in de pagina Experience Manager.

## Experience Manager Video-component {#aem-video-component}

Zelfs als het gebruiken van de videocomponent van Scene7 voor het bekijken van de video&#39;s van Scene7 wordt geadviseerd, beschrijft deze sectie het gebruiken van de video&#39;s van Scene7 met de Component van de Video van de Stichting in Experience Manager, voor volledigheid.

### Experience Manager Video en Scene7 Video vergelijking {#aem-video-and-scene-video-comparison}

De volgende lijst verstrekt een high-level vergelijking van gesteunde mogelijkheden tussen de Videomponent van de Stichting van de Experience Manager en de Videocomponent van Scene7:

|  | Video over Experience Manager Foundation | Scene7 Video |
|---|---|---|
| Benadering | De eerste HTML5-aanpak. Flash wordt alleen gebruikt voor niet-HTML5-fallback. | Flash op de meeste desktops. HTML5 wordt gebruikt voor mobiele apparaten en tablets. |
| Aflevering | Progressief | Adaptieve streaming |
| Tekstspatiëring | Ja | Ja |
| Uitbreidbaarheid | Ja | Nee |
| Mobiele video | Ja | Ja |

### Instellen {#setting-up}

#### Videoprofielen maken {#creating-video-profiles}

De verschillende videocoderingen worden gecreeerd volgens de S7 coderende voorinstellingen die in S7 wolkenconfig worden geselecteerd. Als u wilt dat de basis-videocomponent deze gebruikt, moet u een videoprofiel maken voor elke geselecteerde S7-coderingsvoorinstelling. Met deze methode kan het videoonderdeel de DAM-uitvoeringen op basis hiervan selecteren.

>[!NOTE]
>
>Nieuwe videoprofielen en wijzigingen ervan moeten worden geactiveerd om te publiceren.

1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Configuration Console]** in Experience Manager.
1. Navigeer in **[!UICONTROL Configuration Console]** naar **[!UICONTROL Tools]** > **[!UICONTROL DAM]** > **[!UICONTROL Video Profiles]** in de navigatiestructuur.
1. Maak een S7-videoprofiel. In **[!UICONTROL New]**. selecteert u **[!UICONTROL Create Page]** en selecteert u vervolgens de sjabloon Scene7 Video Profile. Geef de nieuwe pagina met videoprofielen een naam en selecteer **[!UICONTROL Create]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Bewerk het nieuwe videoprofiel. Selecteer eerst de cloud config. Selecteer vervolgens dezelfde coderingsvoorinstelling die u in de cloudconfiguratie hebt geselecteerd.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Eigenschap | Beschrijving |
   |---|---|
   | Scene7 Cloud Config | De cloud config die voor de coderingsvoorinstellingen moet worden gebruikt. |
   | Scene7-coderingsvoorinstelling | De coderingsvoorinstelling waarmee dit videoprofiel wordt toegewezen. |
   | HTML5-videotype | Met deze eigenschap kunt u de waarde instellen van de eigenschap type van het bronelement van de HTML5-video. Deze informatie wordt niet verschaft door de S7-coderingsvoorinstellingen, maar is vereist voor het correct renderen van video&#39;s met HTML5-video-element. Er is een lijst met algemene indelingen beschikbaar, maar deze lijst kan worden overschreven voor andere indelingen. |

   Herhaal deze stap voor alle coderingsvoorinstellingen die zijn geselecteerd in de cloudconfiguratie die u wilt gebruiken in de videocomponent.

#### Ontwerp configureren {#configuring-design}

De component **[!UICONTROL Foundation Video]** moet weten welke videoprofielen moeten worden gebruikt om de lijst met videobronnen te maken. Open het dialoogvenster Ontwerp van videocomponenten en configureer het componentontwerp voor het gebruik van de nieuwe videoprofielen.

>[!NOTE]
>
>Als u de **[!UICONTROL Foundation Video]** component op een mobiele pagina gebruikt, herhaalt u deze stappen bij het ontwerp van de mobiele pagina.

>[!NOTE]
>
>Wijzigingen in het ontwerp vereisen activering van het ontwerp om van kracht te worden bij de publicatie.

1. Open het ontwerpdialoogvenster van de **[!UICONTROL Foundation Video]** component en wijzig deze in het tabblad **[!UICONTROL Profiles]**. Verwijder vervolgens de out-of-the-box profielen en voeg de nieuwe S7-videoprofielen toe. De volgorde van de profiellijst in het dialoogvenster Ontwerp bepaalt de volgorde van het element Videobronnen bij het renderen.
1. Voor browsers die geen HTML5 ondersteunen, kunt u met de videocomponent een Flash-fallback configureren. Open het dialoogvenster Ontwerp van videocomponenten en wijzig deze in het tabblad **[!UICONTROL Flash]**. Configureer de instellingen voor de Flash-speler en wijs een fallback-profiel toe aan de Flash-speler.

#### Checklist {#checklist}

1. Creeer een S7 wolkenconfiguratie. Zorg ervoor dat de voorinstellingen voor videocodering zijn ingesteld en dat de importmodule wordt uitgevoerd.
1. Maak een S7-videoprofiel voor elke videocoderingsvoorinstelling die is geselecteerd in de cloudconfiguratie.
1. De videoprofielen moeten worden geactiveerd.
1. Configureer het ontwerp van de component **[!UICONTROL Foundation Video]** op de pagina.
1. Activeer het ontwerp nadat u klaar bent met uw ontwerpwijzigingen.
