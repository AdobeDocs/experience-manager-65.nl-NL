---
title: Dynamische klassieke mediafuncties toevoegen aan uw pagina
description: Leer hoe u Dynamic Media Classic-functies en componenten aan uw AEM pagina toevoegt.
uuid: aa5a4735-bfec-43b8-aec0-a0c32bff134f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: managing-assets
discoiquuid: e7b95732-a571-48e8-afad-612059cdbde7
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '2727'
ht-degree: 0%

---


# Dynamische klassieke mediafuncties toevoegen aan uw pagina {#adding-scene-features-to-your-page}

[Adobe Dynamic Media ](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) Classics is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke mediabestanden aan webpagina&#39;s, mobiele telefoons, e-mails en internetschermen en drukwerk.

U kunt AEM elementen die zijn gepubliceerd in Dynamic Media Classic, in verschillende viewers weergeven:

* In-/uitzoomen
* Flyout
* Video
* Afbeeldingssjabloon
* Afbeelding

U kunt digitale elementen rechtstreeks van AEM naar Dynamic Media Classic publiceren en u kunt digitale elementen van Dynamic Media Classic naar AEM publiceren.

In dit document wordt beschreven hoe u digitale elementen kunt publiceren van AEM naar Dynamic Media Classic en omgekeerd. Viewers worden ook in detail beschreven. Voor informatie bij het vormen van AEM voor Dynamische Klassiek van Media, zie [Integrating Dynamic Media Classic met AEM](/help/sites-administering/scene7.md).

Zie ook [Afbeeldingskaarten toevoegen](image-maps.md).

Zie [Video](video.md) voor meer informatie over het gebruik van videocomponenten met AEM.

>[!NOTE]
>
>Als de Dynamische Klassieke activa van Media niet behoorlijk tonen, zorg ervoor dat de Dynamische media [gehandicapt ](config-dynamic.md#disabling-dynamic-media) is en vernieuw dan de pagina.

## Handmatig publiceren naar Dynamic Media Classic vanaf elementen {#manually-publishing-to-scene-from-assets}

U kunt digitale elementen als volgt publiceren naar Dynamic Media Classic:

* [In de klassieke gebruikersinterface van de middelenconsole](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-the-assets-console)
* [In de klassieke gebruikersinterface van een element](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-an-asset)
* [In de klassieke gebruikersinterface van buiten de CQ-doelmap](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-assets-from-outside-the-cq-target-folder)

>[!NOTE]
>
>AEM publiceert asynchroon naar Dynamic Media Classic. Nadat u op **[!UICONTROL Publish]** hebt geklikt, kan het enkele seconden duren voordat uw element naar Dynamic Media Classic wordt gepubliceerd.


## Dynamische media Klassieke componenten {#scene-components}

De volgende Dynamic Media Classic-componenten zijn beschikbaar in AEM:

* In-/uitzoomen
* Flyout (zoomen)
* Afbeeldingssjabloon
* Afbeelding
* Video

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de modus **[!UICONTROL Design]** worden geselecteerd voordat ze kunnen worden gebruikt.

Nadat de componenten in de modus **[!UICONTROL Design]** beschikbaar zijn gemaakt, kunt u de componenten net als alle andere AEM aan de pagina toevoegen. Elementen die nog niet zijn gepubliceerd naar Dynamic Media Classic, worden gepubliceerd naar Dynamic Media Classic als ze zich in een gesynchroniseerde map of op een pagina bevinden of met een dynamische Media Classic-cloudconfiguratie.

>[!NOTE]
>
>Als u aangepaste viewers maakt en ontwikkelt en de Inhoudszoeker gebruikt, moet u de parameter **[!UICONTROL allowfullscreen]** expliciet toevoegen.

### Kennisgeving over de gebruiksduur van Flash-viewers {#flash-viewers-end-of-life-notice}

Vanaf 31 januari 2017 wordt ondersteuning voor Adobe Dynamic Media Classic beëindigd voor het Flash-viewerplatform.

Zie [Flash Viewer End-of-Life FAQs](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html) voor meer informatie over deze belangrijke wijziging.

### Een dynamische Media Classic-component (Scene7) toevoegen aan een pagina {#adding-a-scene-component-to-a-page}

Het toevoegen van een dynamische Media Klassieke (Scene7) component aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. De dynamische Klassieke componenten van Media worden beschreven in detail in de volgende secties.

**Een Dynamic Media Classic (Scene7)-component aan een pagina toevoegen**

1. Open in AEM de pagina waaraan u de component Dynamic Media Classic (Scene7) wilt toevoegen.

1. Als er geen dynamische Media Classic-componenten beschikbaar zijn, klikt u op **[!UICONTROL Design]**-modus, tikt u op een component met een blauwe rand, tikt u op het pictogram **[!UICONTROL Parent]** en vervolgens op het pictogram **[!UICONTROL Configuration]**. Selecteer in **[!UICONTROL Parsys (Design)]** alle dynamische media klassieke componenten om deze beschikbaar te maken en klik op **[!UICONTROL OK.]**

   ![chlimage_1-224](assets/chlimage_1-224.png)

1. Klik **[!UICONTROL Edit]** om op **[!UICONTROL Edit]** wijze terug te komen.

1. Sleep een component van de Dynamische Klassieke groep van Media in sidekick op de pagina in de gewenste plaats.

1. Klik op het pictogram **[!UICONTROL Configuration]** om de component te openen.

1. Bewerk de component naar wens en klik op **[!UICONTROL OK]** om de wijzigingen op te slaan.
1. Sleep de afbeelding of video van de inhoudbrowser naar de Dynamic Media Classic-component die u aan de pagina hebt toegevoegd.

   >[!NOTE]
   >
   >Alleen in de interface van aanrakingen moet u de afbeelding of video naar het dynamische Media Classic-onderdeel slepen dat u op de pagina hebt geplaatst. Het selecteren en bewerken van de Klassieke component Dynamische media en het vervolgens kiezen van het element worden niet ondersteund.

### Interactieve kijkervaringen toevoegen aan een responsieve site {#adding-interactive-viewing-experiences-to-a-responsive-website}

Het responsieve ontwerp voor uw middelen betekent dat uw middelen worden aangepast afhankelijk van waar ze worden weergegeven. Bij een responsief ontwerp kunnen dezelfde elementen effectief op meerdere apparaten worden weergegeven.

Zie ook [Responsief ontwerp voor webpagina&#39;s](/help/sites-developing/responsive.md).

**Een interactieve kijkervaring toevoegen aan een responsieve site**

1. Meld u aan bij AEM en zorg ervoor dat u [geconfigureerde Adobe Dynamic Media Classic Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) hebt en dat er dynamische media Classic-componenten beschikbaar zijn.

   >[!NOTE]
   >
   >Als de Dynamische Klassieke componenten van Media niet beschikbaar zijn, zeker [om hen als wijze van het Ontwerp toe te laten](/help/sites-authoring/default-components-designmode.md).

1. In een website waarvoor **[!UICONTROL Dynamic Media Classic]**-componenten zijn ingeschakeld, sleept u een **[!UICONTROL Image]**-component naar de pagina.
1. Selecteer de component en tik op het configuratiepictogram.
1. Pas op het tabblad **[!UICONTROL Dynamic Media Classic Settings]** de onderbrekingspunten aan.

   ![chlimage_1-225](assets/chlimage_1-225.png)

1. Controleer of de viewers het formaat responsief wijzigen en of alle interacties zijn geoptimaliseerd voor computers, tablets en mobiele apparaten.

### Gemeenschappelijke instellingen voor alle dynamische media Klassieke componenten {#settings-common-to-all-scene-components}

Hoewel de configuratieopties variëren, zijn het volgende gemeenschappelijk voor alle [!UICONTROL Dynamic Media Classic] componenten:

* **[!UICONTROL File Reference]** - Blader naar een bestand waarnaar u wilt verwijzen. De verwijzing van het dossier toont activa URL en niet noodzakelijk de volledige Dynamische Klassieke URL van Media met inbegrip van de bevelen URL en de parameters. U kunt in dit veld geen klassieke URL-opdrachten en -parameters voor dynamische media toevoegen. Ze moeten worden toegevoegd via de bijbehorende functionaliteit in de component.
* **[!UICONTROL Width]** - Hiermee kunt u de breedte instellen.
* **[!UICONTROL Height]** - Hiermee kunt u de hoogte instellen.

U stelt deze configuratieopties in door bijvoorbeeld een Klassieke component Dynamische media te openen (dubbelklikken) wanneer u een component **[!UICONTROL Zoom]** opent:

![chlimage_1-226](assets/chlimage_1-226.png)

### In-/uitzoomen {#zoom}

De component HTML5 Zoom geeft een grotere afbeelding weer wanneer u op de knop **[!UICONTROL +]** drukt.

Het element heeft onderaan zoomgereedschappen. Tik **[!UICONTROL +]** om te vergroten. Tik **[!UICONTROL -]** om te reduceren. Als u op **[!UICONTROL x]** of de zoompijl opnieuw instellen tikt, wordt de oorspronkelijke grootte van de afbeelding hersteld wanneer deze als geïmporteerd werd. Tik op de diagonale pijlen om deze volledig scherm te maken. Tik **[!UICONTROL Edit]** om de component te configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle [!UICONTROL Dynamic Media Classic] componenten](#settings-common-to-all-scene-components).

![chlimage_1-227](/help/assets/assets/do-not-localize/chlimage_1-227.png)

### Flyout {#flyout}

In de HTML5 **[!UICONTROL Flyout]**-component wordt het element weergegeven als gesplitst scherm. het element in de opgegeven grootte laten staan; rechts wordt het zoomgedeelte weergegeven. Tik **[!UICONTROL Edit]** om de component te configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle Dynamische Klassieke componenten van Media](#settings-common-to-all-scene-components).

>[!NOTE]
>
>Als uw **[!UICONTROL Flyout]** component een douanegrootte gebruikt, dan wordt die douanegrootte gebruikt en ontvankelijke opstelling van de component wordt onbruikbaar gemaakt.
>
>Als uw **[!UICONTROL Flyout]** component de standaardgrootte gebruikt, zoals die in **[!UICONTROL Design View]** wordt geplaatst, dan wordt de standaardgrootte gebruikt en de componentenrek om de grootte van de paginalay-out met ontvankelijke opstelling van de toegelaten component aan te passen. Houd er echter rekening mee dat er een beperking geldt voor de responsieve installatie van de component. Wanneer u de **[!UICONTROL Flyout]** component met ontvankelijke opstelling gebruikt, zou u het niet met volledige paginalrek moeten gebruiken. Anders kan de **[!UICONTROL Flyout]** buiten de rechterrand van de pagina uitsteken.

![chlimage_1-228](assets/chlimage_1-228.png)

### Afbeelding {#image}

Met de component Dynamic Media Classic **[!UICONTROL Image]** kunt u dynamische Media Classic-functionaliteit toevoegen aan uw afbeeldingen, zoals Dynamische media Classic-modifiers, voorinstellingen voor afbeeldingen of viewers en verscherpen. De component Dynamic Media Classic **[!UICONTROL Image]** is vergelijkbaar met andere afbeeldingscomponenten in AEM met speciale functionaliteit voor dynamische media Classic. In dit voorbeeld is de optie Dynamische media Klassieke URL op de afbeelding toegepast, `&op_invert=1`.

![chlimage_1-229](assets/chlimage_1-229.png)

**[!UICONTROL Title, Alt Text]** - Voeg op het  **[!UICONTROL Advanced]** tabblad een titel toe aan de afbeelding en alternatieve tekst voor gebruikers met afbeeldingen uitgeschakeld.

**[!UICONTROL URL, Open in]** - U kunt een element instellen van om een koppeling te openen. Stel **[!UICONTROL URL]** in en **[!UICONTROL Open in]** geef aan of u het venster wilt openen in hetzelfde venster of in een nieuw venster.

![chlimage_1-230](assets/chlimage_1-230.png)

**[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Viewer-voorinstellingen beheren](/help/assets/managing-viewer-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

**[!UICONTROL Dynamic Media Classic Configuration]** - Selecteer de dynamische Klassieke configuratie van Media u wilt gebruiken om actieve beeldvoorinstellingen van SPS te halen.

**[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Voorinstellingen voor afbeeldingen beheren](/help/assets/managing-image-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

**[!UICONTROL Output Format]** - Selecteer de uitvoerindeling van de afbeelding, bijvoorbeeld JPEG. Afhankelijk van de uitvoerindeling die u selecteert, hebt u mogelijk aanvullende configuratieopties. Zie [Vooraf ingestelde beste werkwijzen voor afbeeldingen](/help/assets/managing-image-presets.md#image-preset-options).

**[!UICONTROL Sharpening]** - Selecteer hoe u de afbeelding wilt verscherpen. Verscherpen wordt gedetailleerd uitgelegd in [Voorinstellingen voor afbeeldingen met de aanbevolen werkwijzen](/help/assets/managing-image-presets.md#image-preset-options) en [Beste werkwijzen verscherpen](/help/assets/assets/s7_sharpening_images.pdf).

**[!UICONTROL URL Modifiers]** - U kunt afbeeldingseffecten wijzigen door aanvullende opdrachten voor dynamische media in de klassieke afbeelding op te geven. Deze worden beschreven in [Voorinstellingen voor afbeeldingen](/help/assets/managing-image-presets.md) en de [Command-referentie](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Breakpoints]** - Als uw website reageert, wilt u de onderbrekingspunten aanpassen. Onderbrekingspunten moeten worden gescheiden door komma&#39;s ( , ).

### Afbeeldingssjabloon {#image-template}

[Dynamic Media Classic Image ](https://docs.adobe.com/help/en/dynamic-media-classic/using/template-basics/quick-start-template-basics.html) Templatesare gelaagde Photoshop-inhoud die is geïmporteerd naar Dynamic Media Classic, waar inhoud en eigenschappen zijn geparametriseerd voor variabiliteit. Met de component **[!UICONTROL Image template]** kunt u afbeeldingen importeren en de tekst dynamisch in AEM wijzigen. Bovendien kunt u de **[!UICONTROL Image template]** component vormen om waarden van cliëntcontext te gebruiken, zodat elke gebruiker het beeld op een gepersonaliseerde manier ervaart.

Tik **[!UICONTROL Edit]** om de component te configureren. U kunt [montages vormen gemeenschappelijk voor alle Dynamische Klassieke componenten van Media](#settings-common-to-all-scene-components) evenals andere montages die in deze sectie worden beschreven.

![chlimage_1-231](assets/chlimage_1-231.png)

**[!UICONTROL File Reference, Width, Height]** - Zie montages gemeenschappelijk voor alle componenten ScDynamic Media Classicene7.

>[!NOTE]
>
>Dynamische media Klassieke URL-opdrachten en -parameters kunnen niet rechtstreeks aan de URL van de bestandsverwijzing worden toegevoegd. Ze kunnen alleen worden gedefinieerd in de interface van de component in het **[!UICONTROL Parameter]**-deelvenster.

**[!UICONTROL Title, Alt Text]** - Voeg op het tabblad Dynamische media Classic afbeeldingssjabloon een titel toe aan de afbeelding en alternatieve tekst voor gebruikers die afbeeldingen hebben uitgeschakeld.

**[!UICONTROL URL, Open in]** - U kunt een element instellen van om een koppeling te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![chlimage_1-232](assets/chlimage_1-232.png)

**[!UICONTROL Parameter Panel]** - Wanneer u een afbeelding importeert, worden de parameters vooraf gevuld met informatie uit de afbeelding. Als er geen inhoud is die dynamisch kan worden gewijzigd, is dit venster leeg.

![chlimage_1-233](assets/chlimage_1-233.png)

#### Tekst dynamisch wijzigen {#changing-text-dynamically}

Als u de tekst dynamisch wilt wijzigen, voert u nieuwe tekst in de velden in en klikt u op **[!UICONTROL OK.]** In dit voorbeeld is **[!UICONTROL Price]** nu $50 en is de verzending 99 cent.

![chlimage_1-234](assets/chlimage_1-234.png)

De tekst in de afbeelding verandert. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te tikken.

![chlimage_1-235](assets/chlimage_1-235.png)

#### Tekst wijzigen om de waarde van de context van een client weer te geven {#changing-text-to-reflect-the-value-of-a-client-context-value}

Als u een veld aan een clientcontextwaarde wilt koppelen, tikt u op **[!UICONTROL Select]** om het contextmenu van de client te openen, selecteert u de clientcontext en tikt u op **[!UICONTROL OK.]** In dit voorbeeld verandert de naam op basis van de koppeling van de naam aan de opgemaakte naam in het profiel.

![chlimage_1-236](assets/chlimage_1-236.png)

De tekst geeft de naam weer van de gebruiker die momenteel is aangemeld. U kunt de tekst terugzetten naar de oorspronkelijke waarde door op **[!UICONTROL Reset]** naast het veld te klikken.

![chlimage_1-237](assets/chlimage_1-237.png)

#### Van de dynamische Media Klassieke beeldmalplaatje een verbinding {#making-the-scene-image-template-a-link} maken

1. Tik op de pagina met de Dynamic Media Classic **[!UICONTROL Image Template]**-component op **[!UICONTROL Edit.]**
1. Voer in het veld **[!UICONTROL URL]** de URL in waarnaar gebruikers gaan wanneer op de afbeelding wordt getikt. Selecteer in het veld **[!UICONTROL Open in]** of u het doel wilt openen (een nieuw venster of hetzelfde venster).

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. Tik op **[!UICONTROL OK.]**

### Videocomponent {#video-component}

De dynamische Media Klassieke **[!UICONTROL Video]** component (beschikbaar bij de Dynamische Klassieke sectie van Media van sidekick) gebruikt apparaat en bandbreedteopsporing om de juiste video aan elk scherm te dienen. Deze component is een HTML5-videospeler; het is één viewer die via meerdere kanalen kan worden gebruikt.

Deze kan worden gebruikt voor adaptieve videosets, één MP4-video of één F4V-video.

Zie [Video](s7-video.md) voor meer informatie over hoe video&#39;s werken met Dynamic Media Classic integratie. Bovendien zie [de Dynamische Klassieke Video component van Media tegenover de Videocomponent van de Stichting](s7-video.md).

![chlimage_1-239](assets/chlimage_1-239.png)

### Bekende beperkingen voor de videocomponent {#known-limitations-for-the-video-component}

Adobe DAM en WCM laten zien of een primaire bronvideo is geüpload. Deze proxy-elementen worden niet weergegeven:

* Dynamische gecodeerde weergaven van Media Classic
* Dynamische Media Classic adaptieve videosets

Wanneer u een adaptieve videoset gebruikt met de Dynamic Media Classic-videocomponent, moet u de grootte van de component aanpassen aan de afmetingen van de video.

## Browser voor dynamische media klassieke inhoud {#scene-content-browser}

Met de browser Dynamische media Klassieke inhoud kunt u inhoud van Dynamic Media Classic rechtstreeks in AEM bekijken. Als u de inhoudbrowser wilt openen, selecteert u **[!UICONTROL Content Finder]** in de gebruikersinterface met geoptimaliseerde aanrakingen of het pictogram **[!UICONTROL S7]** in de klassieke gebruikersinterface. **[!UICONTROL Dynamic Media Classic]** De functionaliteit is identiek tussen beide gebruikersinterfaces.

Als u veelvoudige configuraties hebt, AEM door gebrek toont [standaardconfiguratie](/help/sites-administering/scene7.md#configuring-a-default-configuration). U kunt verschillende configuraties direct selecteren in de Dynamische browser van de Inhoud van Media Klassieke in het drop-down menu.

>[!NOTE]
>
>* Middelen in de ad-hocmap worden niet weergegeven in de browser met dynamische media klassieke inhoud.
>* Wanneer [Beveiligde voorvertoning is ingeschakeld](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), worden zowel gepubliceerde als niet-gepubliceerde elementen op Dynamic Media Classic wel weergegeven in de browser met dynamische media Classic-inhoud.
>* Als u **[!UICONTROL Dynamic Media Classic]** of het **[!UICONTROL S7]** pictogram niet als optie in inhoudbrowser ziet, moet u [Dynamic Media Classic vormen om met AEM](/help/sites-administering/scene7.md) te werken.
>* Voor video ondersteunt de Dynamic Media Classic-inhoudbrowser:

   >
   >   
   * Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
   >   * Eén MP4-video
   >   * Single F4V-video


### Door inhoud bladeren in de interface met geoptimaliseerde aanrakingen {#browsing-content-in-the-touch-optimized-ui}

U kunt de inhoudbrowser openen via de geoptimaliseerde interface of via de klassieke gebruikersinterface. Op dit moment heeft het geoptimaliseerde aanraakgebied de volgende beperking:

* FXG- en Flash-elementen van Dynamic Media Classic worden niet ondersteund.

Blader door Dynamische media Klassieke elementen door **[!UICONTROL Dynamic Media Classic]** in het derde drop-down menu te selecteren. De dynamische Klassieke Media verschijnt niet in de lijst als u geen Dynamische Klassieke/AEM integratie van Media hebt gevormd.

>[!NOTE]
>
>* De dynamische browser van de Media Klassieke inhoud laadt ongeveer 100 activa en sorteert hen door naam.
>* Als u een beveiligde voorvertoningsserver hebt ingesteld, gebruikt de browser die voorvertoningsserver om miniaturen en elementen te renderen.

>



![chlimage_1-240](assets/chlimage_1-240.png)

Bovendien kunt u informatie over de resolutie, de grootte, de dagen sinds de wijziging en de bestandsnaam doorbladeren door de muisaanwijzer op het element in de browser te plaatsen.

![chlimage_1-241](assets/chlimage_1-241.png)

* Voor adaptieve videosets en sjablonen wordt geen informatie over de grootte gegenereerd voor miniaturen.
* Voor adaptieve videosets wordt geen resolutie gegenereerd voor miniaturen.

### Zoeken naar dynamische media klassieke elementen met de inhoudbrowser {#searching-for-scene-assets-with-the-content-browser}

Het zoeken naar dynamische media Klassieke activa is gelijkaardig aan het zoeken AEM activa behalve dat wanneer u zoekt u eigenlijk een verre mening van de activa in het Dynamische Klassieke systeem van Media ziet, eerder dan hen direct in AEM in te voeren.

U kunt zowel de klassieke interface als de interface met geoptimaliseerde aanrakingen gebruiken om elementen weer te geven en te zoeken. Afhankelijk van de interface, is hoe u zoekt lichtjes verschillend.

Wanneer u in een van beide UI zoekt, kunt u filteren op de volgende criteria (die hier in de voor aanraking geoptimaliseerde UI worden getoond):

**[!UICONTROL Enter keywords]** - U kunt elementen zoeken op naam. Wanneer u de trefwoorden zoekt die u invoert, begint de bestandsnaam met. Als u bijvoorbeeld het woord &quot;zwemmen&quot; typt, wordt gezocht naar namen van elementbestanden die met die letters in die volgorde beginnen. Tik op Enter nadat u de term hebt getypt om het element te zoeken.

![chlimage_1-242](assets/chlimage_1-242.png)

**[!UICONTROL Folder/path]** - De naam van de map die wordt weergegeven, is gebaseerd op de configuratie die u hebt geselecteerd. U kunt tot lagere niveaus boren door het omslagpictogram te tikken en een subomslag te selecteren, dan het controleteken te tikken om het te selecteren.

Als u een sleutelwoord ingaat en een omslag selecteert, AEM onderzoeken die omslag en om het even welke subfolders. Als u echter bij het zoeken geen trefwoorden invoert, worden bij het selecteren van de map alleen de elementen in die map weergegeven en worden er geen submappen opgenomen.

AEM zoekt standaard naar de geselecteerde map en naar alle submappen.

![chlimage_1-243](assets/chlimage_1-243.png)

**[!UICONTROL Type of Asset]** - Selecteer deze optie  **[!UICONTROL Dynamic Media Classic]** om door dynamische media Klassieke inhoud te bladeren. Deze optie is alleen beschikbaar als Dynamic Media Classic is geconfigureerd.

![chlimage_1-244](assets/chlimage_1-244.png)

**[!UICONTROL Configuration]** - Als u meer dan één Dynamische Klassieke die configuratie van Media in wordt bepaald  [!UICONTROL Cloud Services], kunt u het hier selecteren. Hierdoor wordt de map gewijzigd op basis van de gekozen configuratie.

![chlimage_1-245](assets/chlimage_1-245.png)

**[!UICONTROL Asset type]** - Binnen Dynamische Media Klassieke browser, kunt u resultaten filtreren om het even welke volgend op te nemen: afbeeldingen, sjablonen, video&#39;s en adaptieve videosets. Als u geen elementtype selecteert, zoekt AEM standaard naar alle elementtypen.

![chlimage_1-246](assets/chlimage_1-246.png)

>[!NOTE]
>
>* In klassieke UI, kunt u ook naar **Flash** en **FXG** zoeken. Filteren hiervoor in de interface met geoptimaliseerde aanrakingen wordt momenteel niet ondersteund.
   >
   >
* Bij het zoeken naar video zoekt u op één vertoning. Resultaten retourneren de oorspronkelijke uitvoering (alleen &amp;ast; .mp4) en de gecodeerde uitvoering.
>* Bij het zoeken naar een adaptieve videoset zoekt u naar de map en naar alle submappen, maar alleen als u een trefwoord aan de zoekopdracht hebt toegevoegd. Als u geen trefwoord hebt toegevoegd, zoekt AEM niet in de submappen.

>



**[!UICONTROL Publish Status]** - U kunt filteren op elementen die zijn gebaseerd op de publicatiestatus:  **[!UICONTROL Unpublished]** of  **[!UICONTROL Published.]** Als u niets selecteert  **[!UICONTROL Publish Status]**, zoekt AEM standaard alle publicatiestatussen.

![chlimage_1-247](assets/chlimage_1-247.png)

