---
title: Video in de Klassieke Authoring van Plaatsen
description: Assets biedt gecentraliseerd beheer van video-elementen waarmee u video's rechtstreeks naar Assets kunt uploaden voor automatische codering naar Dynamic Media Classic en rechtstreeks vanuit Assets toegang kunt krijgen tot Dy-video's voor het ontwerpen van pagina's.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
exl-id: c540aa49-9981-4e8c-97df-972085b26490
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---

# Video{#video}

Assets biedt gecentraliseerd beheer van video-elementen waarmee u video&#39;s rechtstreeks naar Assets kunt uploaden voor automatische codering naar Dynamic Media Classic en Dynamic Media Classic-video&#39;s rechtstreeks vanuit Assets kunt openen voor het ontwerpen van pagina&#39;s.

Dynamic Media Classic-videointegratie breidt het bereik van geoptimaliseerde video uit naar alle schermen (automatische detectie van apparaat en bandbreedte).

* De Dynamic Media Classic-videocomponent voert automatisch apparaat- en bandbreedtedetectie uit om de juiste indeling en videokwaliteit van de juiste kwaliteit af te spelen op desktopcomputers, tablets en mobiele apparaten.
* Assets - U kunt adaptieve videosets opnemen in plaats van alleen afzonderlijke video-elementen. Een adaptieve videoset is een container voor alle video-uitvoeringen die nodig zijn om video naadloos af te spelen op meerdere schermen. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. U gebruikt een adaptieve videoset, samen met de S7-videocomponent, voor adaptieve videostreaming op meerdere schermen, zoals desktopcomputers, iOS, Android™, BlackBerry® en mobiele Windows-apparaten. Zie {de documentatie van 0} Dynamic Media Classic over adaptieve videoreeksen voor meer informatie [&#128279;](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/video/quick-start-video.html#video).

## Info over FFMPEG en Dynamic Media Classic {#about-ffmpeg-and-scene}

Het standaardproces voor videocodering is gebaseerd op het gebruik van de op FFMPEG gebaseerde integratie met videoprofielen. Daarom bevat de workflow buiten de box [!UICONTROL DAM Update Asset] de volgende twee workflowstappen op basis van ffmpeg:

* FMPEG-miniaturen
* FFMPEG-codering

Als u de Dynamic Media Classic-integratie inschakelt en configureert, worden deze twee workflowstappen niet automatisch verwijderd of gedeactiveerd uit de uit-de-box [!UICONTROL DAM Update Asset] insluitingsworkflow. Als u in Adobe Experience Manager al op FFMPEG gebaseerde videocodering gebruikt, is het waarschijnlijk dat FFMPEG is geïnstalleerd in uw ontwerpomgeving. In dit geval wordt een nieuwe video die met Experience Manager Assets wordt ingevoerd, twee keer gecodeerd: één keer vanuit de FFMPEG-codeermodule en één keer vanuit de Dynamic Media Classic-integratie.

Als u de op FFMPEG gebaseerde videocodering in Experience Manager hebt geconfigureerd en FFMPEG hebt geïnstalleerd, raadt de Adobe u aan de twee FFMPEG-workflows uit uw [!UICONTROL DAM Update Asset] -workflows te verwijderen.

### Ondersteunde indelingen {#supported-formats}

De volgende indelingen worden ondersteund voor de Dynamic Media Classic Video-component:

* F4V H.264
* MP4 H.264

### Bepaal waar u de video wilt uploaden {#deciding-where-to-upload-your-video}

Bepaal waar u uw video-elementen wilt uploaden afhankelijk van het volgende:

* Hebt u een workflow voor het video-element nodig?
* Hebt u versiebeheer nodig voor het video-element?

Als het antwoord &quot;ja&quot;op één van beide of beide vragen is, dan upload uw video direct aan Adobe DAM. Als het antwoord op beide vragen &quot;nee&quot; is, uploadt u uw video rechtstreeks naar Dynamic Media Classic. Het werkschema voor elk scenario wordt beschreven in de volgende sectie.

#### Als u de video rechtstreeks uploadt naar Adobe Assets {#if-you-are-uploading-your-video-directly-to-adobe-assets}

Als u een workflow of versie voor uw elementen nodig hebt, moet u eerst uploaden naar Adobe Assets. Hieronder vindt u de aanbevolen workflow:

1. Upload het video-element naar Adobe Assets en codeer en publiceer het automatisch naar Dynamic Media Classic.
1. In Experience Manager hebt u toegang tot video-elementen in WCM op het tabblad **[!UICONTROL Movies]** van de Inhoudszoeker.
1. Auteur met Dynamic Media Classic video- of stichtingsvideocomponent.

#### Als u uw video uploadt naar Dynamic Media Classic {#if-you-are-uploading-your-video-to-scene}

Als u geen workflow of versie voor uw middelen nodig hebt, moet u uw middelen uploaden naar Dynamic Media Classic. Hieronder vindt u de aanbevolen workflow:

1. In de Desktop app van Dynamic Media Classic, [ opstelling een geplande FTP uploadend en het coderen aan Dynamic Media Classic (systeem geautomatiseerd) ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#upload-options).
1. In Experience Manager hebt u toegang tot video-elementen in WCM op het tabblad **[!UICONTROL Dynamic Media Classic]** van de Inhoudszoeker.
1. Auteur met het Dynamic Media Classic-videoonderdeel.

### Integratie met Dynamic Media Classic Video configureren {#configuring-integration-with-scene-video}

1. Navigeer in **[!UICONTROL Cloud Services]** naar de **[!UICONTROL Dynamic Media Classic]** -configuratie en selecteer **[!UICONTROL Edit]** .
1. Selecteer de tab **[!UICONTROL Video]** .

   >[!NOTE]
   >
   >Het tabblad **[!UICONTROL Video]** wordt niet weergegeven als de pagina geen cloudconfiguratie heeft. Zie [ Dynamic Media Classic voor WCM ](#enablingscene7forwcm) toelaten.

1. Selecteer het adaptieve videocoderingsprofiel, een uit-van-de-doos enig videocoderingsprofiel, of een profiel van de douanevideocodering.

   >[!NOTE]
   >
   >Voor meer informatie over wat video vooraf instelt betekent, zie [ Video vooraf instelt voor het coderen van videodossiers ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe raadt u aan beide adaptieve videosets te selecteren wanneer u de universele voorinstellingen configureert of de optie **[!UICONTROL Adaptive Video Encoding]** te selecteren.

1. De geselecteerde coderingsprofielen worden automatisch toegepast op alle video&#39;s die zijn geüpload naar de CQ DAM-doelmap die u hebt ingesteld voor deze Dynamic Media Classic-cloudconfiguratie. U kunt meerdere Dynamic Media Classic-cloudconfiguraties met verschillende doelmappen instellen om zo nodig verschillende coderingsprofielen toe te passen.

### Voorinstellingen voor viewers en codering bijwerken {#updating-viewer-and-encoding-presets}

Werk de viewer- en coderingsvoorinstellingen voor video in Experience Manager bij als de voorinstellingen in Dynamic Media Classic zijn bijgewerkt. In zulk geval, navigeer aan de configuratie van Dynamic Media Classic in de wolkenconfiguratie en selecteer **Update de kijker en het coderen vooraf instelt**.

![ chlimage_1-131 ](assets/chlimage_1-131.png)

### Uw primaire bronvideo uploaden {#uploading-your-master-video}

U kunt als volgt uw primaire bronvideo vanaf Adobe DAM uploaden naar Dynamic Media Classic:

1. Navigeer naar de doelmap CQ DAM waar u de cloudconfiguratie hebt ingesteld met Dynamic Media Classic-coderingsprofielen.
1. Selecteer **[!UICONTROL Upload]** om primaire bronvideo te uploaden. Het uploaden en coderen van video is voltooid nadat de [!UICONTROL DAM Update Asset] -workflow is voltooid en **[!UICONTROL Publish to Dynamic Media Classic]** een vinkje heeft.

   >[!NOTE]
   >
   >Het kan enige tijd duren voordat de videominiaturen zijn gegenereerd.

   Wanneer u de DAM primaire bronvideo op de videocomponent sleept, heeft het toegang *alle* Dynamic Media Classic gecodeerde volmachtsvertoningen voor levering.

### Elementaire videocomponent versus Dynamic Media Classic Video-component {#foundation-video-component-versus-scene-video-component}

Wanneer u Experience Manager gebruikt, hebt u toegang tot zowel de videocomponent Video beschikbaar in Sites als de videocomponent van Dynamic Media Classic. Deze componenten zijn niet onderling verwisselbaar.

De Dynamic Media Classic-videocomponent werkt alleen voor Dynamic Media Classic-video&#39;s. De stichtingscomponent werkt met video&#39;s die zijn opgeslagen vanuit Experience Manager (met behulp van mpeg) en Dynamic Media Classic-video&#39;s.

De volgende matrix legt uit wanneer u welke component moet gebruiken:

![ chlimage_1-132 ](assets/chlimage_1-132.png)

>[!NOTE]
>
>Het Dynamic Media Classic-videoonderdeel gebruikt het universele videoprofiel buiten het vak. U kunt de op HTML5 gebaseerde videospeler echter verkrijgen voor gebruik door Experience Manager. Kopieer in Dynamic Media Classic de insluitcode van de uit-van-box HTML5-videospeler en plaats deze in de pagina Experience Manager.
>

## Experience Manager Video-component {#aem-video-component}

Zelfs als het gebruik van de Dynamic Media Classic Video-component wordt aanbevolen voor het weergeven van Dynamic Media Classic-video&#39;s, wordt in deze sectie beschreven hoe u de volledige versie van Dynamic Media Classic-video&#39;s gebruikt met de [!UICONTROL Foundation Video Component] -Experience Manager.

### Experience Manager Video en Dynamic Media Classic Video vergelijking {#aem-video-and-scene-video-comparison}

De volgende lijst verstrekt een high-level vergelijking van gesteunde mogelijkheden tussen de Videomponent van de Stichting van de Experience Manager en de Videocomponent van Dynamic Media Classic:

|   | Video over Experience Manager Foundation | Dynamic Media Classic Video |
|---|---|---|
| Benadering | HTML5 eerste aanpak. Flash wordt alleen gebruikt voor niet-HTML-fallback. | Flash op de meeste desktops. HTML5 wordt gebruikt voor mobiele apparaten en tabletten. |
| Aflevering | Progressief | Adaptieve streaming |
| Tekstspatiëring | Ja | Ja |
| Uitbreidbaarheid | Ja | Nee |
| Mobiele video | Ja | Ja |

### Instellen {#setting-up}

#### Videoprofielen maken {#creating-video-profiles}

De verschillende videocoderingen worden gemaakt volgens de Dynamic Media Classic-coderingsvoorinstellingen die zijn geselecteerd in de Dynamic Media Classic Cloud Configuration. Als u deze wilt gebruiken in de basis-videocomponent, moet u een videoprofiel maken voor elke geselecteerde Dynamic Media Classic-coderingsvoorinstelling. Hiermee kan de video-component de DAM-uitvoeringen op basis daarvan selecteren.

>[!NOTE]
>
>Nieuwe videoprofielen en wijzigingen ervan moeten worden geactiveerd om te publiceren.

1. Ga in Experience Manager naar **[!UICONTROL Tools]** en selecteer vervolgens **[!UICONTROL Configuration Console]** .
1. Navigeer in de configuratieconsole naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** in de navigatiestructuur.
1. Maak een Dynamic Media Classic-videoprofiel. Selecteer **[!UICONTROL Create Page]** in het menu **[!UICONTROL New]** .
1. Selecteer de Dynamic Media Classic Video profile sjabloon. Geef de nieuwe pagina met videoprofielen een naam en selecteer **[!UICONTROL Create]** .

   ![ chlimage_1-133 ](assets/chlimage_1-133.png)

1. Bewerk het nieuwe videoprofiel. Selecteer eerst de cloudconfiguratie. Selecteer vervolgens dezelfde coderingsvoorinstelling die u in de cloudconfiguratie hebt geselecteerd.

   ![ chlimage_1-134 ](assets/chlimage_1-134.png)

   | Eigenschap | Beschrijving |
   |---|---|
   | Dynamic Media Classic Cloud Config | De cloud config die voor de coderingsvoorinstellingen moet worden gebruikt. |
   | Dynamic Media Classic-coderingsvoorinstelling | De coderingsvoorinstelling waarmee dit videoprofiel wordt toegewezen. |
   | HTML5-videotype | Met deze eigenschap kunt u de waarde instellen van de eigenschap type van het HTML5-videobronelement. Deze informatie wordt niet verschaft door de Dynamic Media Classic-coderingsvoorinstellingen, maar is vereist voor een correcte weergave van de video&#39;s met behulp van HTML5-video-element. Er is een lijst met algemene indelingen beschikbaar, maar deze lijst kan worden overschreven voor andere indelingen. |

   Herhaal deze stap voor alle coderingsvoorinstellingen die zijn geselecteerd in de cloudconfiguratie die u wilt gebruiken in de videocomponent.

#### Ontwerp configureren {#configuring-design}

De stichtingsvideocomponent moet weten welke videoprofielen moeten worden gebruikt om de lijst met videobronnen te bouwen. Open het dialoogvenster voor het ontwerpen van videocomponenten en configureer het componentontwerp voor het gebruik van de nieuwe videoprofielen.

>[!NOTE]
>
>Als u de basis-videocomponent op een mobiele pagina gebruikt, herhaalt u deze stappen bij het ontwerp van de mobiele pagina.

>[!NOTE]
>
>Wijzigingen in het ontwerp vereisen dat het ontwerp wordt geactiveerd om na publicatie van kracht te worden.

1. Open het ontwerpdialoogvenster van de stichtingsvideo-component en wijzig deze in het tabblad **[!UICONTROL Profiles]** . Verwijder vervolgens de profielen uit de doos en voeg de nieuwe Dynamic Media Classic-videoprofielen toe. De volgorde van de profiellijst in het ontwerpdialoogvenster definieert ook de volgorde van het element videobronnen bij het renderen.
1. Voor browsers die geen HTML5 ondersteunen, kunt u met de component Video een fallback configureren. Open het dialoogvenster voor het ontwerpen van videocomponenten en wijzig de tab **[!UICONTROL Flash]** . Configureer de Flash Player-instellingen en wijs een fallback-profiel toe aan de Flash Player.

#### Checklist {#checklist}

1. Een Dynamic Media Classic-cloud configureren. Zorg ervoor dat de voorinstellingen voor videocodering zijn ingesteld en dat de importmodule wordt uitgevoerd.
1. Maak een Dynamic Media Classic-videoprofiel voor elke videocoderingsvoorinstelling die is geselecteerd in de cloudconfiguratie.
1. De videoprofielen moeten worden geactiveerd.
1. Configureer het ontwerp van de basis-videocomponent op de pagina.
1. Activeer het ontwerp nadat u klaar bent met uw ontwerpwijzigingen.
