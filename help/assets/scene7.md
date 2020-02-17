---
title: Dynamische klassieke mediafuncties toevoegen aan uw pagina
description: Leer hoe u Dynamic Media Classic-functies en componenten aan uw AEM-pagina toevoegt.
uuid: aa5a4735-bfec-43b8-aec0-a0c32bff134f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: managing-assets
discoiquuid: e7b95732-a571-48e8-afad-612059cdbde7
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Dynamische klassieke mediafuncties toevoegen aan uw pagina {#adding-scene-features-to-your-page}

[Adobe Dynamic Media Classic](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media-elementen aan web, mobiele apparaten, e-mail en displays en drukwerk via internet.

U kunt AEM-elementen die zijn gepubliceerd in Dynamic Media Classic, in verschillende viewers weergeven:

* In-/uitzoomen
* Flyout
* Video
* Afbeeldingssjabloon
* Afbeelding

U kunt digitale elementen rechtstreeks van AEM naar Dynamic Media Classic publiceren en u kunt digitale elementen van Dynamic Media Classic naar AEM publiceren.

In dit document wordt beschreven hoe u digitale elementen van AEM naar Dynamic Media Classic kunt publiceren en andersom. Viewers worden ook in detail beschreven. Voor informatie bij het vormen van AEM voor Dynamische Klassiek van Media, zie het [Integreren van Dynamische Klassieke Media met AEM](/help/sites-administering/scene7.md).

Zie ook Afbeeldingskaarten [toevoegen](image-maps.md).

Zie [Video](video.md)voor meer informatie over het gebruik van videocomponenten met AEM.

>[!NOTE]
>
>Als de dynamische Klassieke activa van Media niet behoorlijk tonen, zorg ervoor dat de Dynamische media wordt [onbruikbaar gemaakt](config-dynamic.md#disabling-dynamic-media) en vernieuw dan de pagina.

## Handmatig publiceren naar Dynamic Media Classic vanaf elementen {#manually-publishing-to-scene-from-assets}

U kunt digitale elementen als volgt publiceren naar Dynamic Media Classic:

* [In de klassieke gebruikersinterface van de middelenconsole](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-the-assets-console)
* [In de klassieke gebruikersinterface van een element](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-an-asset)
* [In de klassieke gebruikersinterface van buiten de CQ-doelmap](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-assets-from-outside-the-cq-target-folder)

>[!NOTE]
>
>AEM publiceert asynchroon naar Dynamic Media Classic. Nadat u op **[!UICONTROL Publiceren]** hebt geklikt, kan het enkele seconden duren voordat uw element naar Dynamic Media Classic wordt gepubliceerd.


## Dynamische media Klassieke componenten {#scene-components}

De volgende Dynamic Media Classic-componenten zijn beschikbaar in AEM:

* In-/uitzoomen
* Flyout (zoomen)
* Afbeeldingssjabloon
* Afbeelding
* Video

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de **[!UICONTROL ontwerpmodus]** worden geselecteerd voordat ze kunnen worden gebruikt.

Nadat ze in de **[!UICONTROL ontwerpmodus]** beschikbaar zijn gemaakt, kunt u de componenten net als alle andere AEM-componenten aan de pagina toevoegen. Elementen die nog niet zijn gepubliceerd naar Dynamic Media Classic, worden gepubliceerd naar Dynamic Media Classic als ze zich in een gesynchroniseerde map of op een pagina bevinden of met een dynamische Media Classic-cloudconfiguratie.

>[!NOTE]
>
>Als u aangepaste viewers maakt en ontwikkelt en de Inhoudszoeker gebruikt, moet u de parameter **[!UICONTROL allowfullscreen]** expliciet toevoegen.

### Eindbericht voor Flash-viewers {#flash-viewers-end-of-life-notice}

Vanaf 31 januari 2017 wordt ondersteuning voor het Flash-viewerplatform door Adobe Dynamic Media Classic beëindigd.

Zie [Flash Viewer End-of-Life-veelgestelde vragen voor meer informatie over deze belangrijke wijziging](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Het toevoegen van een Dynamische Klassieke component van Media (Scene7) aan een pagina {#adding-a-scene-component-to-a-page}

Het toevoegen van een Dynamische Klassieke (Scene7) component van Media aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. De dynamische Klassieke componenten van Media worden beschreven in detail in de volgende secties.

**Om een Dynamische Klassieke component van Media (Scene7) aan een pagina toe te voegen**

1. Open in AEM de pagina waaraan u de component Dynamic Media Classic (Scene7) wilt toevoegen.

1. Als er geen dynamische Media Classic-componenten beschikbaar zijn, klikt u op de **[!UICONTROL ontwerpmodus]** , tikt u op een component met een blauwe rand, tikt u op het **[!UICONTROL bovenliggende]** pictogram en vervolgens op het **[!UICONTROL configuratiepictogram]** . In **[!UICONTROL Parsys (Ontwerp)]**, selecteer alle Dynamische componenten van Media Klassieke om hen ter beschikking te stellen en **[!UICONTROL O.K]** te klikken.

   ![chlimage_1-224](assets/chlimage_1-224.png)

1. Klik op **[!UICONTROL Bewerken]** om terug te keren naar de modus **[!UICONTROL Bewerken]** .

1. Sleep een component van de Dynamische Klassieke groep van Media in sidekick op de pagina in de gewenste plaats.

1. Klik op het pictogram **[!UICONTROL Configuratie]** om de component te openen.

1. Bewerk de component naar wens en klik op **[!UICONTROL OK]** om de wijzigingen op te slaan.
1. Sleep de afbeelding of video van de inhoudbrowser naar de Dynamic Media Classic-component die u aan de pagina hebt toegevoegd.

   >[!NOTE]
   >
   >Alleen in de interface van aanrakingen moet u de afbeelding of video naar het dynamische Media Classic-onderdeel slepen dat u op de pagina hebt geplaatst. Het selecteren en bewerken van de Klassieke component Dynamische media en het vervolgens kiezen van het element worden niet ondersteund.

### Interactieve weergaven toevoegen aan een responsieve site {#adding-interactive-viewing-experiences-to-a-responsive-website}

Het responsieve ontwerp voor uw middelen betekent dat uw middelen worden aangepast afhankelijk van waar ze worden weergegeven. Bij een responsief ontwerp kunnen dezelfde middelen effectief op meerdere apparaten worden weergegeven.

Zie ook [Responsief ontwerp voor webpagina&#39;s](/help/sites-developing/responsive.md).

**Een interactieve kijkervaring toevoegen aan een responsieve site**

1. Meld u aan bij AEM en controleer of u Adobe Dynamic Media Classic Cloud Services [hebt](/help/sites-administering/scene7.md#configuring-scene-integration) geconfigureerd en of er dynamische Media Classic-componenten beschikbaar zijn.

   >[!NOTE]
   >
   >Als de Dynamische Klassieke componenten van Media niet beschikbaar zijn, ben zeker [om hen als wijze](/help/sites-authoring/default-components-designmode.md)van het Ontwerp toe te laten.

1. In een website met de **[!UICONTROL Dynamische Klassieke]** componenten van Media toegelaten, sleep een component van het **[!UICONTROL Beeld]** aan de pagina.
1. Selecteer de component en tik op het configuratiepictogram.
1. Pas de onderbrekingspunten aan op het tabblad Klassieke instellingen **[!UICONTROL voor]** dynamische media.

   ![chlimage_1-225](assets/chlimage_1-225.png)

1. Controleer of de viewers het formaat responsief wijzigen en of alle interacties zijn geoptimaliseerd voor computers, tablets en mobiele apparaten.

### Gemeenschappelijke instellingen voor alle dynamische media Klassieke componenten {#settings-common-to-all-scene-components}

Hoewel de configuratieopties variëren, zijn het volgende gemeenschappelijk voor alle [!UICONTROL Dynamische Klassieke] componenten van Media:

* **[!UICONTROL Bestandsverwijzing]** - Blader naar een bestand waarnaar u wilt verwijzen. De verwijzing van het dossier toont activa URL en niet noodzakelijk de volledige Dynamische Klassieke URL van Media met inbegrip van de bevelen URL en de parameters. U kunt in dit veld geen klassieke URL-opdrachten en -parameters voor dynamische media toevoegen. Ze moeten worden toegevoegd via de bijbehorende functionaliteit in de component.
* **[!UICONTROL Breedte]** - Hiermee kunt u de breedte instellen.
* **[!UICONTROL Hoogte]** - Hiermee kunt u de hoogte instellen.

U stelt deze configuratieopties in door bijvoorbeeld een Klassieke component van Dynamische media te openen (dubbelklikken) wanneer u een **[!UICONTROL component van het Gezoem]** opent:

![chlimage_1-226](assets/chlimage_1-226.png)

### In-/uitzoomen {#zoom}

De component HTML5 Zoom geeft een grotere afbeelding weer wanneer u op de knop **[!UICONTROL +]** drukt.

Het element heeft onderaan zoomgereedschappen. Tik **[!UICONTROL +]** om te vergroten. Tik **[!UICONTROL -]** om te reduceren. Als u op de **[!UICONTROL x]** - of zoompijl opnieuw instellen tikt, wordt de oorspronkelijke grootte van de afbeelding hersteld. Tik op de diagonale pijlen om deze volledig scherm te maken. Tik op **[!UICONTROL Bewerken]** om de component te configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle [!UICONTROL Dynamische Klassieke] componenten](#settings-common-to-all-scene-components)van Media.

![chlimage_1-227](/help/assets/assets/do-not-localize/chlimage_1-227.png)

### Flyout {#flyout}

In de HTML5 **[!UICONTROL Flyout]** -component wordt het element weergegeven als gesplitst scherm. het element in de opgegeven grootte laten staan; rechts wordt het zoomgedeelte weergegeven. Tik op **[!UICONTROL Bewerken]** om de component te configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle Dynamische Klassieke componenten](#settings-common-to-all-scene-components)van Media.

>[!NOTE]
>
>Als uw **[!UICONTROL Flyout]** -component een aangepaste grootte gebruikt, wordt die aangepaste grootte gebruikt en wordt de responsieve instelling van de component uitgeschakeld.
>
>Als uw **[!UICONTROL component Flyout]** de standaardgrootte, zoals die in de Mening **[!UICONTROL van het]** Ontwerp wordt geplaatst, dan wordt de standaardgrootte gebruikt en de componentenreeksen om de grootte van de paginalay-out met ontvankelijke opstelling van de toegelaten component aan te passen. Houd er echter rekening mee dat er een beperking geldt voor de responsieve installatie van de component. Wanneer u de component **[!UICONTROL Flyout]** met ontvankelijke opstelling gebruikt, zou u het niet met volledige paginalrek moeten gebruiken. Anders kan de **[!UICONTROL Flyout]** buiten de rechterrand van de pagina komen.

![chlimage_1-228](assets/chlimage_1-228.png)

### Image {#image}

Met de component Dynamische media Klassieke **[!UICONTROL afbeelding]** kunt u dynamische media Klassieke functionaliteit toevoegen aan uw afbeeldingen, zoals Dynamische media Klassieke modifiers, afbeelding of viewer-voorinstellingen en verscherpen. De component Dynamic Media Classic **[!UICONTROL Image]** is vergelijkbaar met andere afbeeldingscomponenten in AEM met speciale functionaliteit voor dynamische media Classic. In dit voorbeeld is de optie Dynamische media Klassieke URL op de afbeelding `&op_invert=1` toegepast.

![chlimage_1-229](assets/chlimage_1-229.png)

**[!UICONTROL Titel, Alt-tekst]** - Voeg op het tabblad **[!UICONTROL Geavanceerd]** een titel toe aan de afbeelding en alternatieve tekst voor gebruikers die afbeeldingen hebben uitgeschakeld.

**[!UICONTROL URL, Openen in]** - U kunt een middel van plaatsen om een verbinding te openen. Stel de **[!UICONTROL URL]** in en **** Open in om aan te geven of u deze wilt openen in hetzelfde venster of in een nieuw venster.

![chlimage_1-230](assets/chlimage_1-230.png)

**[!UICONTROL Viewer-voorinstelling]** - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen [van viewers](/help/assets/managing-viewer-presets.md)beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

**[!UICONTROL Dynamische Klassieke Configuratie]** van Media - selecteer de Dynamische Klassieke configuratie van Media u wilt gebruiken om actieve beeldvoorinstellingen van SPS te halen.

**[!UICONTROL Voorinstelling]** afbeelding - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie [Voorinstellingen](/help/assets/managing-image-presets.md)voor afbeeldingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

**[!UICONTROL Uitvoerindeling]** - Selecteer de uitvoerindeling van de afbeelding, bijvoorbeeld jpeg. Afhankelijk van de uitvoerindeling die u selecteert, hebt u mogelijk aanvullende configuratieopties. Zie Aanbevolen werkwijzen [voor voorinstellingen](/help/assets/managing-image-presets.md#image-preset-options)afbeelding.

**[!UICONTROL Verscherpen]** - Selecteer hoe u de afbeelding wilt verscherpen. Verscherpen wordt gedetailleerd uitgelegd in de aanbevolen werkwijzen [voor](/help/assets/managing-image-presets.md#image-preset-options) voorinstellingen van afbeeldingen en in de aanbevolen werkwijzen [voor](/help/assets/assets/s7_sharpening_images.pdf)Verscherpen.

**[!UICONTROL URL-wijzigingstoetsen]** - U kunt afbeeldingseffecten wijzigen door aanvullende opdrachten voor dynamische media in de klassieke afbeelding op te geven. Deze worden beschreven in Voorinstellingen [](/help/assets/managing-image-presets.md) afbeelding en de [opdrachtverwijzing](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/c_command_reference.html).

**[!UICONTROL Onderbrekingspunten]** - Als uw website reageert, wilt u de onderbrekingspunten aanpassen. Onderbrekingspunten moeten worden gescheiden door komma&#39;s ( , ).

### Afbeeldingssjabloon {#image-template}

[Dynamische media Klassieke afbeeldingssjablonen](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) zijn gelaagde Photoshop-inhoud die naar Dynamic Media Classic is geïmporteerd, waarbij voor de inhoud en eigenschappen parameters zijn ingesteld voor variabiliteit. Met de sjablooncomponent **[!UICONTROL Afbeelding]** kunt u afbeeldingen importeren en de tekst dynamisch wijzigen in AEM. Daarnaast kunt u de sjablooncomponent **[!UICONTROL Afbeelding]** zodanig configureren dat waarden van de clientcontext worden gebruikt, zodat elke gebruiker de afbeelding op een gepersonaliseerde manier ervaart.

Tik op **[!UICONTROL Bewerken]** om de component te configureren. U kunt [montages vormen gemeenschappelijk voor alle Dynamische Klassieke componenten](#settings-common-to-all-scene-components) van Media evenals andere montages die in deze sectie worden beschreven.

![chlimage_1-231](assets/chlimage_1-231.png)

**[!UICONTROL De Verwijzing van het dossier, Breedte, Hoogte]** - zie montages gemeenschappelijk voor alle componenten ScDynamic Media Classicene7.

>[!NOTE]
>
>Dynamische media Klassieke URL-opdrachten en -parameters kunnen niet rechtstreeks aan de URL van de bestandsverwijzing worden toegevoegd. Ze kunnen alleen worden gedefinieerd in de gebruikersinterface van de component in het deelvenster **[!UICONTROL Parameter]** .

**[!UICONTROL Titel, Alt-tekst]** - Voeg op het tabblad Dynamische media Classic afbeeldingssjabloon een titel toe aan de afbeelding en alternatieve tekst voor gebruikers die afbeeldingen hebben uitgeschakeld.

**[!UICONTROL URL, Openen in]** - U kunt een middel van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![chlimage_1-232](assets/chlimage_1-232.png)

**[!UICONTROL Deelvenster]** Parameter - Bij het importeren van een afbeelding worden de parameters vooraf gevuld met informatie uit de afbeelding. Als er geen inhoud is die dynamisch kan worden gewijzigd, is dit venster leeg.

![chlimage_1-233](assets/chlimage_1-233.png)

#### Tekst dynamisch wijzigen {#changing-text-dynamically}

Als u de tekst dynamisch wilt wijzigen, voert u nieuwe tekst in de velden in en klikt u op **[!UICONTROL OK]**. In dit voorbeeld is de **[!UICONTROL Prijs]** nu $50 en de verzendkosten 99 cent.

![chlimage_1-234](assets/chlimage_1-234.png)

De tekst in de afbeelding verandert. U kunt de oorspronkelijke waarde van de tekst herstellen door op **[!UICONTROL Herstellen]** naast het veld te tikken.

![chlimage_1-235](assets/chlimage_1-235.png)

#### Tekst wijzigen om de waarde van de context van een client weer te geven {#changing-text-to-reflect-the-value-of-a-client-context-value}

Als u een veld aan een clientcontextwaarde wilt koppelen, tikt u op **[!UICONTROL Selecteren]** om het contextmenu van de client te openen, selecteert u de clientcontext en tikt u op **[!UICONTROL OK]**. In dit voorbeeld verandert de naam op basis van de koppeling van de naam met de opgemaakte naam in het profiel.

![chlimage_1-236](assets/chlimage_1-236.png)

De tekst geeft de naam weer van de gebruiker die momenteel is aangemeld. U kunt de oorspronkelijke waarde van de tekst herstellen door op **[!UICONTROL Herstellen]** naast het veld te klikken.

![chlimage_1-237](assets/chlimage_1-237.png)

#### Een koppeling maken van de Klassieke afbeeldingssjabloon voor dynamische media {#making-the-scene-image-template-a-link}

1. Tik op de pagina met de component Dynamic Media Classic **[!UICONTROL afbeeldingssjabloon]** op **[!UICONTROL Bewerken]**.
1. Voer in het veld **[!UICONTROL URL]** de URL in waarnaar gebruikers gaan wanneer op de afbeelding wordt getikt. Selecteer in het veld **[!UICONTROL Openen in]** of u het doel wilt openen (een nieuw venster of hetzelfde venster).

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. Tik op **[!UICONTROL OK]**.

### Video-component {#video-component}

De dynamische Media Klassieke **[!UICONTROL Video]** component (beschikbaar bij de Dynamische Klassieke sectie van Media van sidekick) gebruikt apparaat en bandbreedteopsporing om de juiste video aan elk scherm te dienen. Deze component is een HTML5-videospeler; het is één viewer die via meerdere kanalen kan worden gebruikt.

Deze kan worden gebruikt voor adaptieve videosets, één MP4-video of één F4V-video.

Zie [Video](s7-video.md) voor meer informatie over hoe video&#39;s werken met Dynamic Media Classic-integratie. Bovendien zie [de Dynamische Klassieke Video component van Media tegenover de Video van de Stichting component](s7-video.md).

![chlimage_1-239](assets/chlimage_1-239.png)

### Bekende beperkingen voor de video-component {#known-limitations-for-the-video-component}

Adobe DAM en WCM tonen of een hoofdvideo wordt geüpload. Deze proxy-elementen worden niet weergegeven:

* Dynamische gecodeerde weergaven van Media Classic
* Dynamische Media Classic adaptieve videosets

Wanneer u een adaptieve videoset gebruikt met de Dynamic Media Classic-videocomponent, moet u de grootte van de component aanpassen aan de afmetingen van de video.

## Browser voor dynamische media klassieke inhoud {#scene-content-browser}

Met de browser Dynamische media Klassieke inhoud kunt u inhoud van Dynamic Media Classic rechtstreeks in AEM weergeven. Als u toegang wilt tot de inhoudbrowser, selecteert u in de **[!UICONTROL Content Finder]** de optie **[!UICONTROL Dynamic Media Classic]** in de gebruikersinterface met geoptimaliseerde aanrakingen of het pictogram **[!UICONTROL S7]** in de klassieke gebruikersinterface. De functionaliteit is identiek tussen beide gebruikersinterfaces.

Als u veelvoudige configuraties hebt, toont AEM door gebrek de [standaardconfiguratie](/help/sites-administering/scene7.md#configuring-a-default-configuration). U kunt verschillende configuraties direct selecteren in de Dynamische browser van de Inhoud van Media Klassieke in het drop-down menu.

>[!NOTE]
>
>* Middelen in de ad-hocmap worden niet weergegeven in de browser met dynamische media klassieke inhoud.
>* Wanneer [Beveiligde voorvertoning is ingeschakeld](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), worden zowel gepubliceerde als niet-gepubliceerde elementen op Dynamic Media Classic wel weergegeven in de browser met dynamische media Klassieke inhoud.
>* Als u geen **[!UICONTROL Dynamische Klassieke]** Media of het pictogram **[!UICONTROL S7]** als optie in inhoudbrowser ziet, moet u Dynamische Klassiek van Media [vormen om met AEM](/help/sites-administering/scene7.md)te werken.
>* Voor video ondersteunt de Dynamic Media Classic-inhoudbrowser:
   >
   >  
* Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
>  * Eén MP4-video
>  * Single F4V-video


### Door inhoud bladeren in de gebruikersinterface die geoptimaliseerd is voor aanrakingen {#browsing-content-in-the-touch-optimized-ui}

U kunt de inhoudbrowser openen via de geoptimaliseerde interface of via de klassieke gebruikersinterface. Op dit moment heeft het geoptimaliseerde aanraakgebied de volgende beperking:

* FXG- en Flash-elementen van Dynamic Media Classic worden niet ondersteund.

Blader door Dynamische media Klassieke elementen door **[!UICONTROL Dynamische Media Klassiek]** van het derde drop-down menu te selecteren. De dynamische Klassieke Media verschijnt niet in de lijst als u geen Dynamische integratie van Media Classic/AEM hebt gevormd.

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

### Dynamische media Klassieke elementen zoeken met de inhoudbrowser {#searching-for-scene-assets-with-the-content-browser}

Het zoeken naar dynamische media Klassieke activa is gelijkaardig aan het zoeken van activa AEM behalve dat wanneer u zoekt u eigenlijk een verre mening van de activa in het Dynamische Klassieke systeem van Media ziet, eerder dan hen direct in AEM in te voeren.

U kunt zowel de klassieke interface als de interface met geoptimaliseerde aanrakingen gebruiken om elementen weer te geven en te zoeken. Afhankelijk van de interface, is hoe u zoekt lichtjes verschillend.

Wanneer u in een van beide UI zoekt, kunt u filteren op de volgende criteria (die hier in de voor aanraking geoptimaliseerde UI worden getoond):

**[!UICONTROL Trefwoorden]** invoeren - U kunt elementen zoeken op naam. Wanneer u de trefwoorden zoekt die u invoert, begint de bestandsnaam met. Als u bijvoorbeeld het woord &quot;zwemmen&quot; typt, wordt gezocht naar namen van elementbestanden die met die letters in die volgorde beginnen. Tik op Enter nadat u de term hebt getypt om het element te zoeken.

![chlimage_1-242](assets/chlimage_1-242.png)

**[!UICONTROL Map/pad]** - De naam van de map die wordt weergegeven, is gebaseerd op de configuratie die u hebt geselecteerd. U kunt tot lagere niveaus boren door het omslagpictogram te tikken en een subomslag te selecteren, dan het controleteken te tikken om het te selecteren.

Als u een trefwoord invoert en een map selecteert, doorzoekt AEM die map en eventuele submappen. Als u echter bij het zoeken geen trefwoorden invoert, worden bij het selecteren van de map alleen de elementen in die map weergegeven en worden er geen submappen opgenomen.

Standaard zoekt AEM naar de geselecteerde map en naar alle submappen.

![chlimage_1-243](assets/chlimage_1-243.png)

**[!UICONTROL Type element]** - selecteer **[!UICONTROL Dynamic Media Classic]** om door dynamische media Classic-inhoud te bladeren. Deze optie is alleen beschikbaar als Dynamic Media Classic is geconfigureerd.

![chlimage_1-244](assets/chlimage_1-244.png)

**[!UICONTROL Configuratie]** - Als u meer dan één Dynamische Klassieke configuratie van Media hebt die in de Diensten [!UICONTROL van de]Wolk wordt bepaald, kunt u het hier selecteren. Hierdoor wordt de map gewijzigd op basis van de gekozen configuratie.

![chlimage_1-245](assets/chlimage_1-245.png)

**[!UICONTROL Elementtype]** - In de dynamische Mediaclassieke browser kunt u de resultaten filteren en een van de volgende items opnemen: afbeeldingen, sjablonen, video&#39;s en adaptieve videosets. Als u geen elementtype selecteert, worden standaard alle elementtypen doorzocht.

![chlimage_1-246](assets/chlimage_1-246.png)

>[!NOTE]
>
>* In de klassieke interface kunt u ook zoeken naar **Flash** en **FXG**. Filteren hiervoor in de interface met geoptimaliseerde aanrakingen wordt momenteel niet ondersteund.
   >
   >
* Bij het zoeken naar video zoekt u op één vertoning. Resultaten retourneren de oorspronkelijke uitvoering (alleen &amp;ast; .mp4) en de gecodeerde uitvoering.
>* Bij het zoeken naar een adaptieve videoset zoekt u naar de map en naar alle submappen, maar alleen als u een trefwoord aan de zoekopdracht hebt toegevoegd. Als u geen trefwoord hebt toegevoegd, doorzoekt AEM de submappen niet.
>



**[!UICONTROL Publicatiestatus]** - U kunt filteren op elementen die zijn gebaseerd op de publicatiestatus: **[!UICONTROL Niet gepubliceerd]** of **[!UICONTROL gepubliceerd]**. Als u geen **[!UICONTROL publicatiestatus]** selecteert, zoekt AEM standaard alle publicatiestatus.

![chlimage_1-247](assets/chlimage_1-247.png)

