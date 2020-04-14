---
title: Video
seo-title: Video
description: Middelen voorzien voor gecentraliseerd videobeheer van activa waar u video's aan Middelen voor auto-codering aan Scene7 en tot video Scene7 rechtstreeks van Middelen voor paginaontwerp kunt uploaden.
seo-description: Middelen voorzien voor gecentraliseerd videobeheer van activa waar u video's aan Middelen voor auto-codering aan Scene7 en tot video Scene7 rechtstreeks van Middelen voor paginaontwerp kunt uploaden.
uuid: 46da7a0d-d17b-4716-a304-ce5496421b5a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dfaa4b3f-f65a-4fe3-87a7-f3bc71015e56
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Video{#video}

Middelen bieden gecentraliseerd beheer van video-elementen waarmee u video&#39;s rechtstreeks kunt uploaden naar Middelen voor automatische codering naar Dynamic Media Classic en rechtstreeks vanuit Middelen toegang kunt krijgen tot Dynamic Media Classic-video&#39;s voor het ontwerpen van pagina&#39;s.

De dynamische integratie van Media Klassieke video breidt het bereik van geoptimaliseerde video tot alle schermen (autoapparaat en bandbreedteopsporing) uit.

* De dynamische Media Klassieke (Scene7) videocomponent voert automatisch apparaat en bandbreedteopsporing uit om het juiste formaat en de juiste kwaliteit video over Desktop, tablets en mobiel te spelen.
* Elementen - U kunt adaptieve videosets opnemen in plaats van alleen afzonderlijke video-elementen. Een adaptieve videoset is een container voor alle video-uitvoeringen die nodig zijn om video naadloos af te spelen op meerdere schermen. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. U gebruikt een adaptieve videoset, samen met de S7-videocomponent, voor adaptieve videostreaming op meerdere schermen, zoals desktops, iOS, Android, Blackberry en mobiele Windows-apparaten. Zie [documentatie Scene7 over adaptieve videoreeksen voor meer informatie](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html).

## Info over FFMPEG en Dynamic Media Classic {#about-ffmpeg-and-scene}

Het standaardvideocoderingsproces is gebaseerd op het gebruik van de op FFMPEG gebaseerde integratie met videoprofielen. Daarom bevat de out-of-the-box [!UICONTROL DAM Update Asset] -workflow de volgende twee workflowstappen op basis van ffmpeg:

* FMPEG-miniaturen
* FFMPEG-codering

Houd er rekening mee dat het inschakelen en configureren van de Dynamic Media Classic-integratie deze twee workflowstappen niet automatisch verwijdert of deactiveert uit de uit-van-de-box [!UICONTROL DAM Update-workflow voor het opnemen van bedrijfsmiddelen] . Als u al gebruik maakt van de op FFMPEG gebaseerde videocodering in AEM, is het waarschijnlijk dat FFMPEG is geïnstalleerd in uw ontwerpomgeving. In dit geval wordt een nieuwe video die met Elementen wordt ingevoerd, twee keer gecodeerd: eenmaal van de FFMPEG-encoder en eenmaal van Dynamic Media Classic-integratie.

Als u de op FFMPEG gebaseerde videocodering in AEM hebt geconfigureerd en FFMPEG hebt geïnstalleerd, raadt Adobe u aan de twee FFMPEG-workflows te verwijderen uit uw [!UICONTROL DAM Update Asset] -workflows.

### Ondersteunde indelingen {#supported-formats}

De volgende indelingen worden ondersteund voor de Klassieke videocomponent van Dynamic Media:

* F4V H.264
* MP4 H.264

### Bepalen waar uw video moet worden geüpload {#deciding-where-to-upload-your-video}

Bepaal waar u uw video-elementen wilt uploaden afhankelijk van het volgende:

* Hebt u een workflow voor het video-element nodig?
* Hebt u versiebeheer nodig voor het video-element?

Als het antwoord op een van deze vragen &quot;ja&quot; is, uploadt u uw video rechtstreeks naar Adobe DAM. Als het antwoord op beide vragen &#39;nee&#39; is, uploadt u uw video rechtstreeks naar Dynamic Media Classic. Het werkschema voor elk scenario wordt beschreven in de volgende sectie.

#### Als u de video rechtstreeks uploadt naar Adobe Assets {#if-you-are-uploading-your-video-directly-to-adobe-assets}

Als u een workflow of versie voor uw elementen nodig hebt, moet u deze eerst uploaden naar Adobe Assets. Hieronder vindt u de aanbevolen workflow:

1. Upload het video-element naar Adobe Assets en codeer en publiceer het automatisch naar Dynamic Media Classic.
1. Open in AEM video-elementen in WCM op het tabblad **[!UICONTROL Films]** van de Inhoudszoeker.
1. Auteur met Dynamic Media Classic-video of basisvideocomponent.

#### Als u de video uploadt naar Dynamic Media Classic {#if-you-are-uploading-your-video-to-scene}

Als u geen workflow of versie voor uw elementen nodig hebt, moet u uw elementen uploaden naar Dynamic Media Classic. Hieronder vindt u de aanbevolen workflow:

1. In Dynamic Media Classic [stelt u een geplande FTP-upload en -codering in naar Dynamic Media Classic (systeem geautomatiseerd)](https://help.adobe.com/en_US/scene7/using/WS70B173EC-4CAD-4b4c-BF9C-43A11F3A5950.html).
1. Open in AEM video-elementen in WCM op het tabblad **[!UICONTROL Dynamische media Klassiek]** van de Inhoudszoeker.
1. Auteur met de Dynamic Media Classic-videocomponent.

### Integratie met Dynamic Media Classic Video configureren {#configuring-integration-with-scene-video}

**Universele voorinstellingen** configureren:

1. Navigeer in **[!UICONTROL Cloud Services]** naar uw **[!UICONTROL Dynamic Media Classic]** -configuratie en klik op **[!UICONTROL Bewerken]**.
1. Selecteer het tabblad **[!UICONTROL Video]** .

   >[!NOTE]
   >
   >Het tabblad **[!UICONTROL Video]** wordt niet weergegeven als de pagina geen cloudconfiguratie heeft. Zie Dynamische media [Klassiek inschakelen voor WCM](#enablingscene7forwcm).

1. Selecteer het adaptieve videocoderingsprofiel, een uit-van-de-doos enig videocoderingsprofiel, of een profiel van de douanevideocodering.

   >[!NOTE]
   >
   >Raadpleeg de documentatie bij [](https://help.adobe.com/en_US/scene7/using/WSE86ACF2B-BD50-4c48-A1D7-9CD4405B62D0.html)Dynamic Media Classic voor meer informatie over wat de videovoorinstellingen betekenen.
   >
   >Adobe raadt u aan beide adaptieve videosets te selecteren wanneer u de universele voorinstellingen configureert of de optie **[!UICONTROL Adaptieve videocodering]** te selecteren.

1. De geselecteerde coderingsprofielen worden automatisch toegepast op alle video&#39;s die zijn geüpload naar de CQ DAM-doelmap die u hebt ingesteld voor deze Dynamic Media Classic Cloud config. U kunt meerdere Dynamic Media Classic-cloudconfiguraties met verschillende doelmappen instellen om zo nodig verschillende coderingsprofielen toe te passen.

### Voorinstellingen voor viewers en codering bijwerken {#updating-viewer-and-encoding-presets}

Als u de voorinstellingen voor de viewer en codering voor video in AEM moet bijwerken omdat de voorinstellingen zijn bijgewerkt in Dynamic Media Classic, navigeert u naar de configuratie Dynamic Media Classic in de cloudconfiguratie en klikt u op **Viewer- en coderingsvoorinstellingen** bijwerken.

![chlimage_1-131](assets/chlimage_1-131.png)

### De stramienvideo uploaden {#uploading-your-master-video}

U kunt als volgt uw stramienvideo vanaf Adobe DAM uploaden naar Dynamic Media Classic:

1. Navigeer naar de CQ DAM-doelmap waar u de cloudconfiguratie hebt ingesteld met dynamische Media Classic-coderingsprofielen.
1. Klik op **[!UICONTROL Uploaden]** om stramienvideo te uploaden. Het uploaden en coderen van video is voltooid nadat de workflow voor [!UICONTROL DAM Update Asset] is voltooid en **[!UICONTROL Publiceren naar Dynamic Media Classic]** een vinkje heeft.

   >[!NOTE]
   >
   >Het kan enige tijd duren voordat de videominiaturen zijn gegenereerd.

   Wanneer u de DAM-hoofdvideo naar de videocomponent sleept, krijgt u toegang tot *alle* door Dynamic Media Classic gecodeerde proxy-uitvoeringen voor levering.

### Flash Video-component versus Dynamic Media Classic Video-component {#foundation-video-component-versus-scene-video-component}

Wanneer het gebruiken van AEM, hebt u toegang tot zowel de Video component beschikbaar in Plaatsen als de Dynamische Klassieke (Scene7) videocomponent van Media. Deze componenten zijn niet onderling verwisselbaar.

De dynamische Media Klassieke videocomponent werkt slechts voor Dynamische Media Klassieke video&#39;s. De stichtingscomponent werkt met video&#39;s die zijn opgeslagen vanuit AEM (met behulp van mpeg) en Dynamic Media Classic-video&#39;s.

De volgende matrix legt uit wanneer u welke component moet gebruiken:

![chlimage_1-132](assets/chlimage_1-132.png)

>[!NOTE]
>
>De dynamische Media Klassieke videocomponent gebruikt het universele videoprofiel uit het vak. U kunt de op HTML5 gebaseerde videospeler echter verkrijgen voor gebruik door AEM. Kopieer in Dynamic Media Classic de insluitcode van de HTML5-videospeler uit de doos en plaats deze in uw AEM-pagina.


## AEM-videocomponent {#aem-video-component}

Zelfs als het gebruiken van de Dynamische Klassieke videocomponent van Media voor het bekijken van Dynamische Klassieke video&#39;s van Media wordt geadviseerd, beschrijft deze sectie het gebruiken van Dynamische Klassieke video&#39;s van Media met de Component [!UICONTROL van de Video van de] Stichting in AEM, voor volledigheid.

### AEM Video en Dynamische Klassieke Video vergelijking van Media {#aem-video-and-scene-video-comparison}

De volgende lijst verstrekt een high level vergelijking van gesteunde mogelijkheden tussen de component van de Stichting AEM en de Videocomponent Scene7:

|  | Video over AEM Foundation | Dynamische media Klassieke video |
|---|---|---|
| Benadering | De eerste HTML5-aanpak. Flash wordt alleen gebruikt voor andere fallback dan HTML5. | Flash op de meeste desktops. HTML5 wordt gebruikt voor mobiele apparaten en tablets. |
| Aflevering | Progressief | Adaptieve streaming |
| Tekstspatiëring | Ja | Ja |
| Uitbreidbaarheid | Ja | Ja (met Dynamic Media Classic viewer SDK) |
| Mobiele video | Ja | Ja |

### Instellen {#setting-up}

#### Videoprofielen maken {#creating-video-profiles}

De verschillende videocoderingen worden gemaakt op basis van de dynamische Media Classic-coderingsvoorinstellingen die zijn geselecteerd in de dynamische Media Classic-cloudconfiguratie. Als u wilt dat de stichtingsvideo-component er gebruik van maakt, moet u een videoprofiel maken voor elke geselecteerde dynamische Media Classic-coderingsvoorinstelling. Hierdoor kan de video-component de DAM-uitvoeringen dienovereenkomstig selecteren.

>[!NOTE]
>
>Nieuwe videoprofielen en wijzigingen ervan moeten worden geactiveerd om te publiceren.

1. Ga in AEM naar **[!UICONTROL Tools]** en selecteer **[!UICONTROL Configuration Console]**. Navigeer in de configuratieconsole naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]** > **[!UICONTROL Videoprofielen]** in de navigatiestructuur.
1. Maak een nieuw, dynamisch mediaprofiel voor klassieke video. In het dialoogvenster **[!UICONTROL Nieuw...]** selecteert u Pagina **** maken en selecteert u vervolgens de sjabloon Dynamisch mediaprofiel voor klassieke video. Geef de nieuwe pagina met videoprofielen een naam en klik op **[!UICONTROL Maken]**.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Bewerk het nieuwe videoprofiel. Selecteer eerst de cloud config. Selecteer vervolgens dezelfde coderingsvoorinstelling die u in de cloudconfiguratie hebt geselecteerd.

   ![chlimage_1-134](assets/chlimage_1-134.png)

   | Eigenschap | Beschrijving |
   |---|---|
   | Dynamic Media Classic (Scene7) Cloud Config | De cloud config die voor de coderingsvoorinstellingen moet worden gebruikt. |
   | Dynamische voorinstelling voor codering van media Classic (Scene7) | De coderingsvoorinstelling waarmee dit videoprofiel wordt toegewezen. |
   | HTML5-videotype | Met deze eigenschap kunt u de waarde instellen van de eigenschap type van het bronelement van de HTML5-video. Deze informatie wordt niet verstrekt door de Dynamische Media Klassieke het coderen voorinstellingen, maar vereist voor behoorlijk het teruggeven van de video&#39;s gebruikend het videoelement van HTML5. Er is een lijst met algemene indelingen beschikbaar, maar deze lijst kan worden overschreven voor andere indelingen. |

   Herhaal deze stap voor alle coderingsvoorinstellingen die zijn geselecteerd in de cloudconfiguratie die u wilt gebruiken in de videocomponent.

#### Ontwerp configureren {#configuring-design}

De basis videocomponent moet weten welke videoprofielen moeten worden gebruikt om de lijst met videobronnen te maken. U moet het dialoogvenster Ontwerp van videocomponenten openen en het componentontwerp configureren voor het gebruik van de nieuwe videoprofielen.

>[!NOTE]
>
>Als u de basis-videocomponent op een mobiele pagina gebruikt, moet u deze stappen mogelijk herhalen bij het ontwerp van de mobiele pagina.

>[!NOTE]
>
>Wijzigingen in het ontwerp vereisen activering van het ontwerp om van kracht te worden bij de publicatie.

1. Open het ontwerpdialoogvenster van de stichtingsvideo-component en wijzig deze in het tabblad **[!UICONTROL Profielen]** . Verwijder vervolgens de out-of-the-box-profielen en voeg de nieuwe Dynamic Media Classic-videoprofielen toe. De volgorde van de profiellijst in het ontwerpdialoogvenster definieert ook de volgorde van het element videobronnen bij het renderen.
1. Voor browsers die geen HTML5 ondersteunen, kunt u met de videocomponent een flitsfallback configureren. Open het ontwerpdialoogvenster voor videocomponenten en wijzig dit op het tabblad **[!UICONTROL Flash]** . Configureer de Flash Player-instellingen en wijs een fallback-profiel toe aan de Flash Player.

#### Checklist {#checklist}

1. Creeer een Dynamische Klassieke (Scene7) wolkenconfig van Media. Zorg ervoor dat de voorinstellingen voor videocodering zijn ingesteld en dat de importmodule wordt uitgevoerd.
1. Maak een dynamisch mediaprofiel voor klassieke video voor elke videocoderingsvoorinstelling die is geselecteerd in de cloudconfiguratie.
1. De videoprofielen moeten worden geactiveerd.
1. Configureer het ontwerp van de basis-videocomponent op de pagina.
1. Activeer het ontwerp nadat u klaar bent met uw ontwerpwijzigingen.

