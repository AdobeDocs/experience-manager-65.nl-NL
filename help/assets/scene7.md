---
title: Dynamic Media Klassieke functies toevoegen aan uw pagina
description: Leer hoe u klassieke Dynamic Media-functies en -componenten aan uw Adobe Experience Manager-pagina kunt toevoegen.
uuid: aa5a4735-bfec-43b8-aec0-a0c32bff134f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: managing-assets
discoiquuid: e7b95732-a571-48e8-afad-612059cdbde7
feature: Dynamic Media Classic
role: Business Practitioner, Administrator
exl-id: 815f577d-4774-4830-8baf-0294bd085b83
source-git-commit: 900a2ccbf33575644f934e5a75380d8dd3eab5d8
workflow-type: tm+mt
source-wordcount: '2711'
ht-degree: 0%

---

# Dynamic Media Klassieke functies toevoegen aan uw pagina {#adding-scene-features-to-your-page}

[Adobe Dynamic Media ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/home.html) Classics is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media middelen aan Web, mobiel, e-mail, en Internet-verbonden vertoningen en druk.

U kunt Experience Manager-elementen die zijn gepubliceerd in Dynamic Media Classic, in verschillende viewers weergeven:

* In-/uitzoomen
* Flyout
* Video
* Afbeeldingssjabloon
* Afbeelding

U kunt digitale elementen rechtstreeks van Experience Manager naar Dynamic Media Classic publiceren en u kunt digitale elementen van Dynamic Media Classic naar Experience Manager publiceren.

In dit document wordt beschreven hoe u digitale elementen kunt publiceren van Experience Manager naar Dynamic Media Classic en omgekeerd. Viewers worden ook in detail beschreven. Zie [Dynamic Media Classic integreren met Experience Manager](/help/sites-administering/scene7.md) voor informatie over het configureren van Experience Manager voor Dynamic Media Classic.

Zie ook [Afbeeldingskaarten toevoegen](image-maps.md).

Zie [Video](video.md) voor meer informatie over het gebruik van videocomponenten met Experience Manager.

>[!NOTE]
>
>Als de Klassieke activa van Dynamic Media niet behoorlijk tonen, zorg ervoor dat Dynamic Media [gehandicapt ](config-dynamic.md#disabling-dynamic-media) is en vernieuw dan de pagina.

## Handmatig publiceren naar Dynamic Media Classic vanuit middelen {#manually-publishing-to-scene-from-assets}

U kunt digitale elementen als volgt naar Dynamic Media Classic publiceren:

* [In de klassieke gebruikersinterface van de middelenconsole](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-the-assets-console)
* [In de klassieke gebruikersinterface van een element](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-an-asset)
* [In de klassieke gebruikersinterface van buiten de CQ-doelmap](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-assets-from-outside-the-cq-target-folder)

>[!NOTE]
>
>Experience Manager publiceert asynchroon naar Dynamic Media Classic. Nadat u op **[!UICONTROL Publish]** hebt geklikt, duurt het enkele seconden voordat uw element naar Dynamic Media Classic wordt gepubliceerd.


## Dynamic Media Klassieke componenten {#scene-components}

De volgende Klassieke Dynamic Media-componenten zijn beschikbaar in de Experience Manager:

* In-/uitzoomen
* Flyout (zoomen)
* Afbeeldingssjabloon
* Afbeelding
* Video

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de modus **[!UICONTROL Design]** worden geselecteerd voordat ze kunnen worden gebruikt.

Nadat de componenten in de modus **[!UICONTROL Design]** beschikbaar zijn gemaakt, kunt u de componenten net als alle andere Experience Managers aan de pagina toevoegen. Elementen die nog niet naar Dynamic Media Classic zijn gepubliceerd, worden naar Dynamic Media Classic gepubliceerd als ze zich in een gesynchroniseerde map of op een pagina bevinden of als ze zich in een Classic-cloudconfiguratie van Dynamic Media bevinden.

>[!NOTE]
>
>Als u aangepaste viewers maakt en ontwikkelt en de Inhoudszoeker gebruikt, moet u expliciet de parameter `allowfullscreen` toevoegen.

### Kennisgeving over de gebruiksduur van Flash-viewers {#flash-viewers-end-of-life-notice}

Vanaf 31 januari 2017 is ondersteuning voor het Flash-viewerplatform beëindigd voor Adobe Dynamic Media Classic.

<!-- For more information about this important change, see [Flash Viewer End-of-Life FAQs](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html). -->

### Een Dynamic Media Classic (Scene7)-component toevoegen aan een pagina {#adding-a-scene-component-to-a-page}

Het toevoegen van een Dynamic Media Klassieke (Scene7) component aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. Klassieke Dynamic Media-componenten worden in de volgende secties uitgebreid beschreven.

**Een Dynamic Media Classic (Scene7)-component toevoegen aan een pagina:**

1. Open in Experience Manager de pagina waar u de **[!UICONTROL Dynamic Media Classic (Scene7)]**-component wilt toevoegen.

1. Als er geen Klassieke Dynamic Media-componenten beschikbaar zijn, klikt u op **[!UICONTROL Design]**-modus, tikt u op een component met een blauwe rand, tikt u op het pictogram **[!UICONTROL Parent]** en vervolgens op het pictogram **[!UICONTROL Configuration]**. Selecteer in **[!UICONTROL Parsys (Design)]** alle Klassieke Dynamic Media-componenten om deze beschikbaar te maken en klik op **[!UICONTROL OK]**.

   ![chlimage_1-224](assets/chlimage_1-224.png)

1. Klik **[!UICONTROL Edit]** zodat kunt u op **[!UICONTROL Edit]** wijze terugkeren.

1. Sleep een component van de Klassieke groep van Dynamic Media in de sidekick op de pagina in de gewenste plaats.

1. Klik op het pictogram **[!UICONTROL Configuration]** zodat u de component kunt openen.

1. Bewerk de component naar wens en klik op **[!UICONTROL OK]** om de wijzigingen op te slaan.
1. Sleep de afbeelding of video van de inhoudbrowser naar de klassieke Dynamic Media-component die u aan de pagina hebt toegevoegd.

   >[!NOTE]
   >
   >Alleen in de gebruikersinterface moet u de afbeelding of video slepen en neerzetten op het klassieke Dynamic Media-onderdeel dat u op de pagina hebt geplaatst. Het selecteren en bewerken van de Klassieke Dynamic Media-component en vervolgens het kiezen van het element wordt niet ondersteund.

### Interactieve kijkervaringen toevoegen aan een responsieve site {#adding-interactive-viewing-experiences-to-a-responsive-website}

Het responsieve ontwerp voor uw elementen betekent dat uw element wordt aangepast, afhankelijk van waar het wordt weergegeven. Bij een responsief ontwerp kunnen dezelfde elementen effectief op meerdere apparaten worden weergegeven.

Zie ook [Responsief ontwerp voor webpagina&#39;s](/help/sites-developing/responsive.md).

**Een interactieve kijkervaring toevoegen aan een responsieve site:**

1. Meld u aan bij de Experience Manager en controleer of u [geconfigureerde Adobe Dynamic Media Classic Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) hebt en of Dynamic Media Classic-componenten beschikbaar zijn.

   >[!NOTE]
   >
   >Als de Klassieke componenten van Dynamic Media niet beschikbaar zijn, zeker [om hen als wijze van het Ontwerp toe te laten](/help/sites-authoring/default-components-designmode.md).

1. In een website waarvoor **[!UICONTROL Dynamic Media Classic]**-componenten zijn ingeschakeld, sleept u een **[!UICONTROL Image]**-component naar de pagina.
1. Selecteer de component en tik op het configuratiepictogram.
1. Pas op het tabblad **[!UICONTROL Dynamic Media Classic Settings]** de onderbrekingspunten aan.

   ![chlimage_1-225](assets/chlimage_1-225.png)

1. Controleer of de viewers het formaat responsief wijzigen en of alle interacties zijn geoptimaliseerd voor computers, tablets en mobiele apparaten.

### Gemeenschappelijke instellingen voor alle Dynamic Media Classic-componenten {#settings-common-to-all-scene-components}

Hoewel de configuratieopties variëren, zijn het volgende gemeenschappelijk voor alle [!UICONTROL Dynamic Media Classic] componenten:

* **[!UICONTROL File Reference]** - Blader naar een bestand waarnaar u wilt verwijzen. De verwijzing van het dossier toont de activa URL en niet noodzakelijk de volledige Klassieke URL van Dynamic Media met inbegrip van de bevelen URL en de parameters. U kunt in dit veld geen klassieke URL-opdrachten en -parameters van Dynamic Media toevoegen. In plaats daarvan voegt u ze toe via de bijbehorende functionaliteit in de component.
* **[!UICONTROL Width]** - Hiermee kunt u de breedte instellen.
* **[!UICONTROL Height]** - Hiermee kunt u de hoogte instellen.

U stelt deze configuratieopties in door een klassieke Dynamic Media-component te openen (dubbelklikken), bijvoorbeeld wanneer u een **[!UICONTROL Zoom]**-component opent:

![chlimage_1-226](assets/chlimage_1-226.png)

### In-/uitzoomen {#zoom}

De component HTML5 Zoom geeft een grotere afbeelding weer wanneer u op de knop **[!UICONTROL +]** drukt.

Het element heeft onderaan zoomgereedschappen. Tik **[!UICONTROL +]** als u wilt vergroten; Tik **[!UICONTROL -]** als u wilt verminderen. Als u op **[!UICONTROL x]** of de zoompijl opnieuw instellen tikt, wordt de oorspronkelijke grootte van de afbeelding hersteld wanneer deze als geïmporteerd werd. Tik op de diagonale pijlen zodat u deze volledig scherm kunt weergeven. Tik **[!UICONTROL Edit]** zodat u de component kunt configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle [!UICONTROL Dynamic Media Classic] componenten](#settings-common-to-all-scene-components).

![chlimage_1-227](/help/assets/assets/do-not-localize/chlimage_1-227.png)

### Flyout {#flyout}

In de HTML5 **[!UICONTROL Flyout]**-component wordt het element weergegeven als gesplitst scherm. het element in de opgegeven grootte laten staan; rechts wordt het zoomgedeelte weergegeven. Tik **[!UICONTROL Edit]** zodat u de component kunt configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle Klassieke componenten van Dynamic Media](#settings-common-to-all-scene-components).

>[!NOTE]
>
>Als uw **[!UICONTROL Flyout]** component een douanegrootte gebruikt, dan wordt die douanegrootte gebruikt en ontvankelijke opstelling van de component wordt onbruikbaar gemaakt.
>
>Als uw **[!UICONTROL Flyout]** component de standaardgrootte gebruikt, zoals die in **[!UICONTROL Design View]** wordt geplaatst, dan wordt de standaardgrootte gebruikt en de componentenrek om de grootte van de paginalay-out met ontvankelijke opstelling van de toegelaten component aan te passen. Er geldt een beperking voor de responsieve instelling van de component. Wanneer u de **[!UICONTROL Flyout]** component met ontvankelijke opstelling gebruikt, gebruik het niet met volledige paginalrek. Anders loopt de **[!UICONTROL Flyout]** verder dan de rechterrand van de pagina.

![chlimage_1-228](assets/chlimage_1-228.png)

### Afbeelding {#image}

Met de Klassieke Dynamic Media-component **[!UICONTROL Image]** kunt u Klassieke Dynamic Media-functionaliteit aan uw afbeeldingen toevoegen, zoals Klassieke Dynamic Media-wijzigingstoetsen, voorinstellingen voor afbeeldingen of viewers en verscherpen. De Dynamic Media Classic **[!UICONTROL Image]**-component is vergelijkbaar met andere afbeeldingscomponenten in Experience Manager met speciale Dynamic Media Classic-functionaliteit. In dit voorbeeld is de optie `&op_invert=1` van Dynamic Media Classic URL op de afbeelding toegepast.

![chlimage_1-229](assets/chlimage_1-229.png)

**[!UICONTROL Title, Alt Text]** - Voeg op het  **[!UICONTROL Advanced]** tabblad een titel toe aan de afbeelding en alternatieve tekst voor gebruikers met afbeeldingen uitgeschakeld.

**[!UICONTROL URL, Open in]** - U kunt een element instellen van om een koppeling te openen. Stel **[!UICONTROL URL]** in en **[!UICONTROL Open in]** geef aan of u het venster wilt openen in hetzelfde venster of in een nieuw venster.

![chlimage_1-230](assets/chlimage_1-230.png)

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**[!UICONTROL Dynamic Media Classic Configuration]** - Selecteer de Klassieke Dynamic Media-configuratie die u wilt gebruiken om actieve voorinstellingen voor afbeeldingen op te halen uit SPS.

**[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Voorinstellingen voor afbeeldingen beheren](/help/assets/managing-image-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**[!UICONTROL Output Format]** - Selecteer de uitvoerindeling van de afbeelding, bijvoorbeeld JPEG. Afhankelijk van de uitvoerindeling die u selecteert, zijn er aanvullende configuratieopties. Zie [Vooraf ingestelde beste werkwijzen voor afbeeldingen](/help/assets/managing-image-presets.md#image-preset-options).

**[!UICONTROL Sharpening]** - Selecteer hoe u de afbeelding wilt verscherpen. Verscherpen wordt gedetailleerd uitgelegd in [Voorinstellingen voor afbeeldingen met de aanbevolen werkwijzen](/help/assets/managing-image-presets.md#image-preset-options) en [Beste werkwijzen verscherpen](/help/assets/assets/sharpening_images.pdf).

**[!UICONTROL URL Modifiers]** - U kunt afbeeldingseffecten wijzigen door aanvullende opdrachten voor klassieke Dynamic Media-afbeeldingen op te geven. Deze opdrachten worden beschreven in [Voorinstellingen afbeelding](/help/assets/managing-image-presets.md) en de [Command-referentie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Breakpoints]** - Als uw website reageert, wilt u de onderbrekingspunten aanpassen. Onderbrekingspunten moeten worden gescheiden door komma&#39;s ( , ).

### Afbeeldingssjabloon {#image-template}

[Dynamic Media Classic Image ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html) Templatesare gelaagde Photoshop-inhoud die is geïmporteerd naar Dynamic Media Classic, waar inhoud en eigenschappen zijn geparametriseerd voor variabiliteit. Met de component **[!UICONTROL Image template]** kunt u afbeeldingen importeren en de tekst dynamisch in Experience Manager wijzigen. Bovendien kunt u de **[!UICONTROL Image template]** component vormen om waarden van cliëntcontext te gebruiken, zodat elke gebruiker het beeld op een gepersonaliseerde manier ervaart.

Tik **[!UICONTROL Edit]** als u de component wilt configureren. U kunt [instellingen configureren die hetzelfde zijn voor alle klassieke Dynamic Media-componenten](#settings-common-to-all-scene-components) en andere instellingen die in deze sectie worden beschreven.

![chlimage_1-231](assets/chlimage_1-231.png)

**[!UICONTROL File Reference, Width, Height]** - Zie montages gemeenschappelijk voor alle componenten ScDynamic Media Classicene7.

>[!NOTE]
>
>Klassieke URL-opdrachten en -parameters van Dynamic Media kunnen niet rechtstreeks aan de URL van de bestandsverwijzing worden toegevoegd. Ze kunnen alleen worden gedefinieerd in de interface van de component in het **[!UICONTROL Parameter]**-deelvenster.

**[!UICONTROL Title, Alt Text]** - Voeg op het tabblad Klassieke afbeeldingssjabloon van Dynamic Media een titel toe aan de afbeelding en alternatieve tekst voor gebruikers die afbeeldingen hebben uitgeschakeld.

**[!UICONTROL URL, Open in]** - U kunt een element instellen van om een koppeling te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![chlimage_1-232](assets/chlimage_1-232.png)

**[!UICONTROL Parameter Panel]** - Wanneer u een afbeelding importeert, worden de parameters vooraf gevuld met informatie uit de afbeelding. Als er geen inhoud is die dynamisch kan worden gewijzigd, is dit venster leeg.

![chlimage_1-233](assets/chlimage_1-233.png)

#### Tekst dynamisch wijzigen {#changing-text-dynamically}

Als u de tekst dynamisch wilt wijzigen, voert u nieuwe tekst in de velden in en klikt u op **[!UICONTROL OK]**. In dit voorbeeld is **[!UICONTROL Price]** nu $50 en is de verzending 99 cent.

![chlimage_1-234](assets/chlimage_1-234.png)

De tekst in de afbeelding verandert. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te tikken.

![chlimage_1-235](assets/chlimage_1-235.png)

#### Tekst wijzigen om de waarde van de context van een client weer te geven {#changing-text-to-reflect-the-value-of-a-client-context-value}

Als u een veld aan een clientcontextwaarde wilt koppelen, tikt u op **[!UICONTROL Select]** om het contextmenu van de client te openen, selecteert u de clientcontext en tikt u op **[!UICONTROL OK]**. In dit voorbeeld verandert de naam op basis van de koppeling van de naam met de opgemaakte naam in het profiel.

![chlimage_1-236](assets/chlimage_1-236.png)

De tekst geeft de naam weer van de gebruiker die momenteel is aangemeld. U kunt de tekst terugzetten naar de oorspronkelijke waarde door op **[!UICONTROL Reset]** naast het veld te klikken.

![chlimage_1-237](assets/chlimage_1-237.png)

#### Van de klassieke Dynamic Media-afbeeldingssjabloon een koppeling {#making-the-scene-image-template-a-link} maken

1. Tik op **[!UICONTROL Edit]** op de pagina met de klassieke Dynamic Media-component **[!UICONTROL Image Template]**.
1. Voer in het veld **[!UICONTROL URL]** de URL in waarnaar gebruikers gaan wanneer op de afbeelding wordt getikt. Selecteer in het veld **[!UICONTROL Open in]** of u het doel wilt openen (een nieuw venster of hetzelfde venster).

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. Tik op **[!UICONTROL OK]**.

### Videocomponent {#video-component}

De Klassieke Dynamic Media **[!UICONTROL Video]**-component (beschikbaar in het Klassieke Dynamic Media-gedeelte van het hulpapparaat) gebruikt apparaat- en bandbreedtedetectie om de juiste video voor elk scherm te leveren. Deze component is een HTML5-videospeler; het is één viewer die via meerdere kanalen kan worden gebruikt.

Deze kan worden gebruikt voor adaptieve videosets, één MP4-video of één F4V-video.

Zie [Video](s7-video.md) voor meer informatie over hoe video&#39;s werken met de Klassieke integratie van Dynamic Media. Bovendien [de Klassieke Video component van Dynamic Media tegenover de Video component van de Stichting](s7-video.md).

![chlimage_1-239](assets/chlimage_1-239.png)

### Bekende beperkingen voor de videocomponent {#known-limitations-for-the-video-component}

Adobe DAM en WCM laten zien of een primaire bronvideo is geüpload. Deze proxy-elementen worden niet weergegeven:

* Dynamic Media Classic gecodeerde uitvoeringen
* Dynamic Media Classic adaptieve videosets

Wanneer u een adaptieve videoset gebruikt met de klassieke Dynamic Media-videocomponent, moet u de grootte van de component aanpassen aan de afmetingen van de video.

## Dynamic Media Klassieke inhoudbrowser {#scene-content-browser}

Met de Dynamic Media Classic-inhoudbrowser kunt u inhoud van Dynamic Media Classic rechtstreeks in de Experience Manager weergeven. Als u de inhoudbrowser wilt openen, selecteert u **[!UICONTROL Content Finder]** in de gebruikersinterface met geoptimaliseerde aanrakingen of het pictogram **[!UICONTROL S7]** in de klassieke gebruikersinterface. **[!UICONTROL Dynamic Media Classic]** De functionaliteit is identiek tussen beide gebruikersinterfaces.

Als u veelvoudige configuraties hebt, toont de Experience Manager door gebrek [standaardconfiguratie](/help/sites-administering/scene7.md#configuring-a-default-configuration). U kunt verschillende configuraties rechtstreeks selecteren in de Dynamic Media Klassieke inhoudbrowser in het vervolgkeuzemenu.

>[!NOTE]
>
>* Middelen in de map op aanvraag worden niet weergegeven in de browser voor klassieke inhoud van Dynamic Media.
>* Wanneer [Beveiligde voorvertoning is ingeschakeld](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), worden zowel gepubliceerde als niet-gepubliceerde elementen op Dynamic Media Classic wel weergegeven in de Dynamic Media Classic-inhoudbrowser.
>* Als u **[!UICONTROL Dynamic Media Classic]** of het **[!UICONTROL S7]** pictogram niet als optie in inhoudbrowser ziet, moet u [Dynamic Media Klassiek vormen om met Experience Manager](/help/sites-administering/scene7.md) te werken.
>* De Dynamic Media Classic-inhoudbrowser ondersteunt voor video:

   >
   >   
   * Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
   >   * Eén MP4-video
   >   * Single F4V-video


### Door inhoud bladeren in de interface met geoptimaliseerde aanrakingen {#browsing-content-in-the-touch-optimized-ui}

U kunt de inhoudbrowser openen via de geoptimaliseerde interface of via de klassieke gebruikersinterface. Op dit moment heeft het geoptimaliseerde aanraakgebied de volgende beperking:

* FXG- en Flash-elementen van Dynamic Media Classic worden niet ondersteund.

Blader door Klassieke Dynamic Media-elementen door **[!UICONTROL Dynamic Media Classic]** te selecteren in het derde keuzemenu. Dynamic Media Classic wordt niet weergegeven in de lijst als u de integratie van Dynamic Media Classic/Experience Manager niet hebt geconfigureerd.

>[!NOTE]
>
>* In de Dynamic Media Classic-inhoudbrowser worden ongeveer 100 elementen geladen en op naam gesorteerd.
>* Als u een beveiligde voorvertoningsserver hebt ingesteld, gebruikt de browser die voorvertoningsserver om miniaturen en elementen te renderen.

>



![chlimage_1-240](assets/chlimage_1-240.png)

Bovendien kunt u informatie over de resolutie, de grootte, de dagen sinds de wijziging en de bestandsnaam doorbladeren door de muisaanwijzer op het element in de browser te plaatsen.

![chlimage_1-241](assets/chlimage_1-241.png)

* Voor adaptieve videosets en sjablonen wordt geen informatie over de grootte gegenereerd voor miniaturen.
* Voor adaptieve videosets wordt geen resolutie gegenereerd voor miniaturen.

### Dynamic Media Classic-elementen zoeken met de inhoudbrowser {#searching-for-scene-assets-with-the-content-browser}

Het zoeken naar elementen in Dynamic Media Classic lijkt op het zoeken naar elementen in Experience Manager Assets. Wanneer u echter zoekt, ziet u in feite een externe weergave van de elementen in het klassieke Dynamic Media-systeem in plaats van deze rechtstreeks in de Experience Manager te importeren.

U kunt zowel de klassieke interface als de interface met geoptimaliseerde aanrakingen gebruiken om elementen weer te geven en te zoeken. Afhankelijk van de interface, is hoe u zoekt lichtjes verschillend.

Wanneer u in een van beide UI zoekt, kunt u filteren op de volgende criteria (die hier in de voor aanraking geoptimaliseerde UI worden getoond):

**[!UICONTROL Enter keywords]** - U kunt elementen zoeken op naam. Bij het zoeken zijn de ingevoerde trefwoorden de beginwaarden van de bestandsnaam. Als u bijvoorbeeld het woord &quot;zwemmen&quot; typt, wordt gezocht naar namen van elementbestanden die met die letters in die volgorde beginnen. Tik op Enter nadat u de term hebt getypt om het element te zoeken.

![chlimage_1-242](assets/chlimage_1-242.png)

**[!UICONTROL Folder/path]** - De naam van de map die wordt weergegeven, is gebaseerd op de configuratie die u hebt geselecteerd. U kunt tot lagere niveaus boren door het omslagpictogram te tikken en een subfolder te selecteren, dan het controleteken te tikken om het te selecteren.

Als u een sleutelwoord ingaat en een omslag selecteert, zoekt de Experience Manager die omslag en om het even welke subfolders. Als u bij het zoeken echter geen trefwoorden invoert, worden bij het selecteren van de map alleen de elementen in die map weergegeven en worden er geen submappen opgenomen.

Standaard zoekt de Experience Manager naar de geselecteerde map en naar alle submappen.

![chlimage_1-243](assets/chlimage_1-243.png)

**[!UICONTROL Type of Asset]** - Selecteer deze optie  **[!UICONTROL Dynamic Media Classic]** om door klassieke Dynamic Media-inhoud te bladeren. Deze optie is alleen beschikbaar als Dynamic Media Classic is geconfigureerd.

![chlimage_1-244](assets/chlimage_1-244.png)

**[!UICONTROL Configuration]** - Als u meer dan één Classic Dynamic Media-configuratie hebt gedefinieerd in  [!UICONTROL Cloud Services], kunt u deze hier selecteren. Hierdoor wordt de map gewijzigd op basis van de gekozen configuratie.

![chlimage_1-245](assets/chlimage_1-245.png)

**[!UICONTROL Asset type]** - In de Klassieke browser van Dynamic Media kunt u de resultaten filteren en de volgende items opnemen: afbeeldingen, sjablonen, video&#39;s en adaptieve videosets. Als u geen elementtype selecteert, zoekt de Experience Manager standaard naar alle elementtypen.

![chlimage_1-246](assets/chlimage_1-246.png)

>[!NOTE]
>
>* In klassieke UI, kunt u ook naar **Flash** en **FXG** zoeken. Filteren voor deze typen in de interface met geoptimaliseerde aanrakingen wordt niet ondersteund.
   >
   >
* Bij het zoeken naar video zoekt u op één vertoning. Resultaten retourneren de oorspronkelijke uitvoering (alleen &amp;ast; .mp4) en de gecodeerde uitvoering.
>* Bij het zoeken naar een adaptieve videoset zoekt u naar de map en naar alle submappen, maar alleen als u een trefwoord aan de zoekopdracht hebt toegevoegd. Als u geen trefwoord hebt toegevoegd, doorzoekt Experience Manager de submappen niet.

>



**[!UICONTROL Publish Status]** - U kunt filteren op elementen die zijn gebaseerd op de publicatiestatus:  **[!UICONTROL Unpublished]** of  **[!UICONTROL Published]**. Als u geen **[!UICONTROL Publish Status]** selecteert, zoekt de Experience Manager standaard alle publicatiestatus.

![chlimage_1-247](assets/chlimage_1-247.png)
