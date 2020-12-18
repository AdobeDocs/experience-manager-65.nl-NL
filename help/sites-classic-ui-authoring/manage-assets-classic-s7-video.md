---
title: Video
seo-title: Video
description: Middelen bieden gecentraliseerd beheer van video-elementen waarmee u video's rechtstreeks kunt uploaden naar Middelen voor automatische codering naar Scene7 en rechtstreeks vanuit Middelen toegang kunt krijgen tot Scene7-video's voor het ontwerpen van pagina's.
seo-description: Middelen bieden gecentraliseerd beheer van video-elementen waarmee u video's rechtstreeks kunt uploaden naar Middelen voor automatische codering naar Scene7 en rechtstreeks vanuit Middelen toegang kunt krijgen tot Scene7-video's voor het ontwerpen van pagina's.
uuid: 46da7a0d-d17b-4716-a304-ce5496421b5a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dfaa4b3f-f65a-4fe3-87a7-f3bc71015e56
translation-type: tm+mt
source-git-commit: e95f26cc1a084358b6bcb78605e3acb98f257b66
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%

---


# Video{#video}

Middelen bieden gecentraliseerd beheer van video-elementen waarmee u video&#39;s rechtstreeks kunt uploaden naar Middelen voor automatische codering naar Dynamic Media Classic en rechtstreeks vanuit Middelen toegang kunt krijgen tot Classic Dynamic Media-video&#39;s voor het ontwerpen van pagina&#39;s.

Dynamic Media Classic video integration breidt het bereik van geoptimaliseerde video uit naar alle schermen (automatische apparaat- en bandbreedtedetectie).

* De Dynamic Media Classic (Scene7)-videocomponent voert automatisch apparaat- en bandbreedtedetectie uit voor het afspelen van de juiste indeling en videokwaliteit op desktopcomputers, tablets en mobiele apparaten.
* Elementen - U kunt adaptieve videosets opnemen in plaats van alleen afzonderlijke video-elementen. Een adaptieve videoset is een container voor alle video-uitvoeringen die nodig zijn om video naadloos af te spelen op meerdere schermen. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. U gebruikt een adaptieve videoset, samen met de S7-videocomponent, voor adaptieve videostreaming op meerdere schermen, zoals desktops, iOS, Android, Blackberry en mobiele Windows-apparaten. Zie [Scene7 documentatie over adaptieve videoreeksen voor meer informatie](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html).

## Info over FFMPEG en Dynamic Media Classic {#about-ffmpeg-and-scene}

Het standaardvideocoderingsproces is gebaseerd op het gebruik van de op FFMPEG gebaseerde integratie met videoprofielen. Daarom bevat de uit-van-de-doos [!UICONTROL DAM Update Asset] werkschema de volgende twee op ffmpeg-Gebaseerde werkschemastappen:

* FMPEG-miniaturen
* FFMPEG-codering

Houd er rekening mee dat het inschakelen en configureren van de Dynamic Media Classic-integratie deze twee workflowstappen niet automatisch verwijdert of deactiveert uit de [!UICONTROL DAM Update Asset]-innameworkflow. Als u al in AEM gebruik maakt van de op FFMPEG gebaseerde videocodering, is het waarschijnlijk dat FFMPEG is geïnstalleerd in uw ontwerpomgeving. In dit geval wordt een nieuwe video die met Elementen wordt ingevoerd, twee keer gecodeerd: eenmaal van de FFMPEG-encoder en eenmaal van de Dynamic Media Classic-integratie.

Als u op FFMPEG-Gebaseerde videocodering in AEM gevormd hebt en FFMPEG geïnstalleerd, adviseert Adobe dat u de twee werkschema&#39;s FFMPEG uit uw [!UICONTROL DAM Update Asset] werkschema&#39;s verwijdert.

### Ondersteunde indelingen {#supported-formats}

De volgende indelingen worden ondersteund voor de Klassieke Video-component van Dynamic Media:

* F4V H.264
* MP4 H.264

### Bepalen waar uw video moet worden geüpload {#deciding-where-to-upload-your-video}

Bepaal waar u uw video-elementen wilt uploaden afhankelijk van het volgende:

* Hebt u een workflow voor het video-element nodig?
* Hebt u versiebeheer nodig voor het video-element?

Als het antwoord op een van deze vragen &quot;ja&quot; is, uploadt u uw video rechtstreeks naar Adobe DAM. Als het antwoord op beide vragen &quot;nee&quot; is, uploadt u uw video rechtstreeks naar Dynamic Media Classic. Het werkschema voor elk scenario wordt beschreven in de volgende sectie.

#### Als u de video rechtstreeks uploadt naar Adobe Assets {#if-you-are-uploading-your-video-directly-to-adobe-assets}

Als u een workflow of versie voor uw elementen nodig hebt, moet u eerst uploaden naar Adobe Assets. Hieronder vindt u de aanbevolen workflow:

1. Upload het video-element naar Adobe Assets en codeer en publiceer het automatisch naar Dynamic Media Classic.
1. In AEM hebt u toegang tot video-elementen in WCM op het tabblad **[!UICONTROL Movies]** van de Inhoudszoeker.
1. Auteur met Dynamic Media Classic video- of stichtingsvideocomponent.

#### Als u uw video uploadt naar Dynamic Media Classic {#if-you-are-uploading-your-video-to-scene}

Als u geen workflow of versie voor uw middelen nodig hebt, moet u uw middelen uploaden naar Dynamic Media Classic. Hieronder vindt u de aanbevolen workflow:

1. In Dynamic Media Classic stelt [een geplande FTP-upload en -codering in naar Dynamic Media Classic (systeemgeautomatiseerd)](https://help.adobe.com/en_US/scene7/using/WS70B173EC-4CAD-4b4c-BF9C-43A11F3A5950.html).
1. In AEM hebt u toegang tot video-elementen in WCM op het tabblad **[!UICONTROL Dynamic Media Classic]** van de Inhoudszoeker.
1. Auteur met de klassieke Dynamic Media-videocomponent.

### Integratie met Dynamic Media Classic Video {#configuring-integration-with-scene-video} configureren

**Universele voorinstellingen** configureren:

1. Navigeer in **[!UICONTROL Cloud Services]** naar uw **[!UICONTROL Dynamic Media Classic]**-configuratie en klik op **[!UICONTROL Edit.]**
1. Selecteer het tabblad **[!UICONTROL Video]**.

   >[!NOTE]
   >
   >Het tabblad **[!UICONTROL Video]** wordt niet weergegeven als de pagina geen cloudconfiguratie heeft. Zie [Dynamic Media Classic inschakelen voor WCM](#enablingscene7forwcm).

1. Selecteer het adaptieve videocoderingsprofiel, een uit-van-de-doos enig videocoderingsprofiel, of een profiel van de douanevideocodering.

   >[!NOTE]
   >
   >Raadpleeg de [Klassieke documentatie van Dynamic Media](https://help.adobe.com/en_US/scene7/using/WSE86ACF2B-BD50-4c48-A1D7-9CD4405B62D0.html) voor meer informatie over wat de videovoorinstellingen betekenen.
   >
   >Adobe raadt u aan beide adaptieve videosets te selecteren wanneer u de universele voorinstellingen configureert of de optie **[!UICONTROL Adaptive Video Encoding]** te selecteren.

1. De geselecteerde coderingsprofielen worden automatisch toegepast op alle video&#39;s die zijn geüpload naar de CQ DAM-doelmap die u hebt ingesteld voor deze Dynamic Media Classic cloud config. U kunt meerdere Dynamic Media Classic-cloudconfiguraties instellen met verschillende doelmappen om zo nodig verschillende coderingsprofielen toe te passen.

### Voorinstellingen {#updating-viewer-and-encoding-presets} voor viewer en codering bijwerken

Als u de voorinstellingen voor de viewer en codering voor video in AEM moet bijwerken omdat de voorinstellingen zijn bijgewerkt in Dynamic Media Classic, navigeert u naar de Klassieke Dynamic Media-configuratie in de cloudconfiguratie en klikt u op **De voorinstellingen voor de viewer en codering bijwerken**.

![chlimage_1-131](assets/chlimage_1-131.png)

### Uw primaire bronvideo uploaden {#uploading-your-master-video}

U kunt als volgt uw primaire bronvideo vanaf Adobe DAM uploaden naar Dynamic Media Classic:

1. Navigeer naar de CQ DAM-doelmap waar u de cloudconfiguratie hebt ingesteld met de Classic-coderingsprofielen van Dynamic Media.
1. Klik **[!UICONTROL Upload]** om primaire bronvideo te uploaden. Het uploaden en coderen van video is voltooid nadat de [!UICONTROL DAM Update Asset]-workflow is voltooid en **[!UICONTROL Publish to Dynamic Media Classic]** een vinkje heeft.

   >[!NOTE]
   >
   >Het kan enige tijd duren voordat de videominiaturen zijn gegenereerd.

   Door de primaire DAM-bronvideo naar de videocomponent te slepen, wordt *all* van de door Dynamic Media Classic gecodeerde proxyuitvoeringen voor levering geopend.

### Foundation Video Component versus Dynamic Media Classic Video Component {#foundation-video-component-versus-scene-video-component}

Wanneer u AEM gebruikt, hebt u toegang tot zowel de videocomponent beschikbaar in Sites als de Dynamic Media (Scene7) videocomponent van. Deze componenten zijn niet onderling verwisselbaar.

De Dynamic Media Classic-videocomponent werkt alleen voor Dynamic Media Classic-video&#39;s. De stivingscomponent werkt met video&#39;s die zijn opgeslagen vanuit AEM (met behulp van mpeg) en Dynamic Media Classic video&#39;s.

De volgende matrix legt uit wanneer u welke component moet gebruiken:

![chlimage_1-132](assets/chlimage_1-132.png)

>[!NOTE]
>
>De klassieke Dynamic Media-videocomponent gebruikt het universele videoprofiel uit het vak. U kunt de op HTML5 gebaseerde videospeler echter verkrijgen voor gebruik door AEM. Kopieer in Dynamic Media Classic de insluitcode van de HTML5-videospeler uit de doos en plaats deze in de AEM pagina.


## AEM videocomponent {#aem-video-component}

Zelfs als het gebruik van de Klassieke Dynamic Media-videocomponent wordt aanbevolen voor het weergeven van Klassieke Dynamic Media-video&#39;s, wordt in deze sectie beschreven hoe u voor de volledigheid de Klassieke Dynamic Media-video&#39;s gebruikt met de [!UICONTROL Foundation Video Component] in AEM.

### AEM Klassieke videovergelijking met Video en Dynamic Media {#aem-video-and-scene-video-comparison}

De volgende lijst verstrekt een high level vergelijking van gesteunde mogelijkheden tussen de AEM component van de Video van de Stichting en de videocomponent van Scene7:

|  | AEM | Dynamic Media Klassieke video |
|---|---|---|
| Benadering | De eerste HTML5-aanpak. Flash wordt alleen gebruikt voor niet-HTML5-fallback. | Flash op de meeste desktops. HTML5 wordt gebruikt voor mobiele apparaten en tablets. |
| Aflevering | Progressief | Adaptieve streaming |
| Tekstspatiëring | Ja | Ja |
| Uitbreidbaarheid | Ja | Nee |
| Mobiele video | Ja | Ja |

### {#setting-up} instellen

#### Videoprofielen {#creating-video-profiles} maken

De verschillende videocoderingen worden gemaakt volgens de Dynamic Media Classic-coderingsvoorinstellingen die zijn geselecteerd in de Classic-cloudconfiguratie van Dynamic Media. Als u deze wilt gebruiken door de stichtingsvideocomponent, moet u een videoprofiel maken voor elke geselecteerde Dynamic Media Classic-coderingsvoorinstelling. Hierdoor kan de video-component de DAM-uitvoeringen dienovereenkomstig selecteren.

>[!NOTE]
>
>Nieuwe videoprofielen en wijzigingen ervan moeten worden geactiveerd om te publiceren.

1. Ga AEM naar **[!UICONTROL Tools]** en selecteer **[!UICONTROL Configuration Console.]** in de configuratieconsole om naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** in de navigatiestructuur te navigeren.
1. Maak een nieuw Klassiek Dynamic Media-videoprofiel. Selecteer **[!UICONTROL New...]** in het menu &lt;a0/> en selecteer vervolgens de sjabloon Klassiek videoprofiel van Dynamic Media. **[!UICONTROL Create Page]** Geef de nieuwe pagina met videoprofielen een naam en klik op **[!UICONTROL Create.]**

   ![chlimage_1-135](assets/chlimage_1-133.png)

1. Bewerk het nieuwe videoprofiel. Selecteer eerst de cloud config. Selecteer vervolgens dezelfde coderingsvoorinstelling die u in de cloudconfiguratie hebt geselecteerd.

   ![chlimage_1-134](assets/chlimage_1-134.png)

   | Eigenschap | Beschrijving |
   |---|---|
   | Dynamic Media Classic (Scene7) Cloud Config | De cloud config die voor de coderingsvoorinstellingen moet worden gebruikt. |
   | Dynamic Media Classic (Scene7)-coderingsvoorinstelling | De coderingsvoorinstelling waarmee dit videoprofiel wordt toegewezen. |
   | HTML5-videotype | Met deze eigenschap kunt u de waarde instellen van de eigenschap type van het bronelement van de HTML5-video. Deze informatie wordt niet verschaft door de Dynamic Media Classic-coderingsvoorinstellingen, maar is vereist voor het correct renderen van video&#39;s met HTML5-video-element. Er is een lijst met algemene indelingen beschikbaar, maar deze lijst kan worden overschreven voor andere indelingen. |

   Herhaal deze stap voor alle coderingsvoorinstellingen die zijn geselecteerd in de cloudconfiguratie die u wilt gebruiken in de videocomponent.

#### Ontwerp {#configuring-design} configureren

De basis videocomponent moet weten welke videoprofielen moeten worden gebruikt om de lijst met videobronnen te maken. U moet het dialoogvenster Ontwerp van videocomponenten openen en het componentontwerp configureren voor het gebruik van de nieuwe videoprofielen.

>[!NOTE]
>
>Als u de basis-videocomponent op een mobiele pagina gebruikt, moet u deze stappen mogelijk herhalen bij het ontwerp van de mobiele pagina.

>[!NOTE]
>
>Wijzigingen in het ontwerp vereisen activering van het ontwerp om van kracht te worden bij de publicatie.

1. Open het ontwerpdialoogvenster van de stichtingsvideo-component en wijzig dit in het tabblad **[!UICONTROL Profiles]**. Verwijder vervolgens de out-of-the-box profielen en voeg de nieuwe Dynamic Media Classic-videoprofielen toe. De volgorde van de profiellijst in het ontwerpdialoogvenster definieert ook de volgorde van het element videobronnen bij het renderen.
1. Voor browsers die geen HTML5 ondersteunen, kunt u met de videocomponent een flitsfallback configureren. Open het ontwerpdialoogvenster voor videocomponenten en wijzig dit in het tabblad **[!UICONTROL Flash]**. Configureer de Flash Player-instellingen en wijs een fallback-profiel toe aan de Flash Player.

#### Checklist {#checklist}

1. Maak een Dynamic Media Classic (Scene7) cloud config. Zorg ervoor dat de voorinstellingen voor videocodering zijn ingesteld en dat de importmodule wordt uitgevoerd.
1. Maak een klassiek Dynamic Media-videoprofiel voor elke videocoderingsvoorinstelling die in de cloudconfiguratie is geselecteerd.
1. De videoprofielen moeten worden geactiveerd.
1. Configureer het ontwerp van de basis-videocomponent op de pagina.
1. Activeer het ontwerp nadat u klaar bent met uw ontwerpwijzigingen.

