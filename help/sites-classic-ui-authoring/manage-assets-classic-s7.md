---
title: Het toevoegen van Eigenschappen Scene7 aan uw Pagina
seo-title: Het toevoegen van Eigenschappen Scene7 aan uw Pagina
description: Adobe Scene7 is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media activa aan Web, mobiel, e-mail, en Internet-Verbonden vertoningen en druk.
seo-description: Adobe Scene7 is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media activa aan Web, mobiel, e-mail, en Internet-Verbonden vertoningen en druk.
uuid: dc463e2d-a452-490e-88af-f79bdaa3b089
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dc0191d0-f181-4e1e-b3f4-73427aa22073
docset: aem65
translation-type: tm+mt
source-git-commit: 9bd71115dac8109c9a47155ab60ac7573d88014c
workflow-type: tm+mt
source-wordcount: '3221'
ht-degree: 0%

---


# Het toevoegen van Eigenschappen Scene7 aan uw Pagina{#adding-scene-features-to-your-page}

[Adobe Scene7](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media activa aan Web, mobiel, e-mail, en Internet-verbonden vertoningen en druk.

U kunt AEM activa bekijken die in Scene7 in diverse kijkers worden gepubliceerd:

* In-/uitzoomen
* Flyout
* Video
* Afbeeldingssjabloon
* Afbeelding

U kunt digitale activa van AEM aan Scene7 direct publiceren en u kunt digitale activa van Scene7 aan AEM publiceren.

In dit document wordt beschreven hoe u digitale elementen van AEM naar Scene7 kunt publiceren en andersom. Viewers worden ook in detail beschreven. Voor informatie bij het vormen van AEM voor Scene7, zie het [Integreren Scene7 met AEM](/help/sites-administering/scene7.md).

Zie ook Afbeeldingskaarten [toevoegen](/help/assets/image-maps.md).

Raadpleeg de volgende secties voor meer informatie over het gebruik van videocomponenten met AEM:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Als de activa Scene7 niet behoorlijk tonen, gelieve ervoor te zorgen dat de Dynamische media [gehandicapt](/help/assets/config-dynamic.md#disabling-dynamic-media) is en dan de pagina te verfrissen.

## Handmatig publiceren naar Scene7 vanaf middelen {#manually-publishing-to-scene-from-assets}

U kunt digitale activa aan Scene7 of van de console van Activa in klassieke UI of direct van de activa publiceren.

>[!NOTE]
>
>AEM publiceert asynchroon aan Scene7. Nadat u **Publish** klikt, kan het verscheidene seconden voor uw activa vergen om aan Scene7 te publiceren.


### Publiceren vanaf de middelenconsole {#publishing-from-the-assets-console}

Om aan Scene7 van de console van Activa te publiceren als de activa in een Scene7 doelomslag zijn:

1. Klik in de klassieke UI van AEM op **Digital Assets** om toegang te krijgen tot het beheer van digitale elementen.

1. Selecteer de activa (of activa) of de omslag van binnen de doelomslag u aan Scene7 wilt publiceren en met de rechtermuisknop aanklikken en uitgezocht **publiceren aan Scene7**. Alternatief, kunt u **publiceren aan Scene7** van het menu **van** Hulpmiddelen selecteren.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Ga naar Scene7 en bevestig dat de activa beschikbaar zijn.

   >[!NOTE]
   >
   >Als de activa niet in een Scene7 gesynchroniseerde omslag zijn, **publiceer aan Scene7** in beide menu&#39;s is zichtbaar maar gehandicapt.

### Publiceren vanuit een element {#publishing-from-an-asset}

U kunt activa manueel publiceren zolang dat middel binnen de gesynchroniseerde omslag Scene7 wordt gevestigd.

>[!NOTE]
>
>Als de activa niet in de Scene7 gesynchroniseerde omslag wordt gevestigd, zal de verbinding aan **Publish aan Scene7** niet verschijnen.

Om aan Scene7 direct van een digitaal middel te publiceren:

1. Klik in AEM op **Digitale elementen** om toegang te krijgen tot het beheer van digitale elementen.

1. Dubbelklik om een element te openen.

1. In de ruit van elementdetails, uitgezochte **Publish aan Scene7**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. De koppeling verandert in **Publiceren...** en vervolgens **Gepubliceerd**. Ga naar Scene7 en bevestig dat de activa beschikbaar is.

   >[!NOTE]
   >
   >Als het element niet correct naar Scene7 publiceert, verandert de verbinding in het **Publiceren Mislukt**. Als de activa reeds aan Scene7 is gepubliceerd, leest de verbinding **opnieuw publiceren aan Scene7**. Met opnieuw publiceren kunt u wijzigingen aanbrengen in een element in AEM en deze opnieuw publiceren.

### Elementen publiceren van buiten de map CQ Target {#publishing-assets-from-outside-the-cq-target-folder}

Adobe adviseert dat u activa aan Scene7 slechts van activa binnen de scene7 doelomslag publiceert. Nochtans, als u activa van een omslag buiten de doelomslag moet uploaden, kunt u dat nog doen door hen aan een **ad hoc** omslag op Scene7 te uploaden.

U doet dit door eerst de configuratie van de Wolk voor de pagina te vormen waar de activa zullen verschijnen. Vervolgens voegt u een component Scene7 toe aan de pagina en sleept u een element naar de component. Nadat de pagina-eigenschappen voor die pagina zijn ingesteld, wordt een koppeling **Publiceren naar Scene7** weergegeven die bij selectie het uploaden naar Scene7 activeert.

>[!NOTE]
>
>Middelen die in de ad hoc omslag zijn verschijnen niet in Scene7 Inhoudsbrowser.

Elementen publiceren die zich buiten de CQ-doelmap bevinden:

1. In AEM in klassieke UI, klik **Websites** en navigeer aan de Web-pagina die u een digitaal middel aan wilt toevoegen dat nog niet aan Scene7 wordt gepubliceerd. (Normale regels voor paginaovererving zijn van toepassing.)

1. Klik in het hulpgedeelte op het pictogram **Pagina** en klik op **Pagina-eigenschappen**.

1. Klik **Cloud Servicen** en klik de **Add diensten** en selecteer **Scene7**.
1. Selecteer de gewenste configuratie in de vervolgkeuzelijst **Adobe Scene7** en klik op **OK**.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Voor de Web-pagina, voeg een component Scene7 aan de gewenste plaats op de pagina toe.
1. Sleep een digitaal element vanuit de zoeker naar de component. U ziet een verbinding aan de Status **van de Publicatie van** Controle Scene7.

   >[!NOTE]
   >
   >Als het digitale element in de CQ doelomslag is, dan verschijnt geen verbinding aan de Status **van de Publicatie van de** Controle Scene7. De elementen worden eenvoudig in de component geplaatst.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Klik **de Status** van de Publicatie Scene7 controleren. Als de activa niet worden gepubliceerd, publiceert AEM de activa aan Scene7. Nadat het element is geüpload, bevindt het zich in de ad-hocmap. De map ad hoc bevindt zich standaard in de map **name_of_the_company/CQ5_adhoc**. U kunt dit, indien nodig [](#configuringtheadhocfolder)vormen.

   >[!NOTE]
   >
   >Als de activa niet in een Scene7 gesynchroniseerde omslag is en er geen Scene7 wolkenconfiguratie verbonden aan de huidige pagina is, zal uploaden ontbreken.

## Scene7-componenten {#scene-components}

De volgende componenten Scene7 zijn beschikbaar in AEM:

* In-/uitzoomen
* Flyout (zoomen)
* Afbeeldingssjabloon
* Afbeelding
* Video

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt.

Nadat ze in de ontwerpmodus beschikbaar zijn gemaakt, kunt u de componenten net als alle andere AEM-componenten aan de pagina toevoegen. De activa die nog niet aan Scene7 zijn gepubliceerd worden gepubliceerd aan Scene7 als in een gesynchroniseerde omslag of op een pagina of met een Scene7 wolkenconfiguratie.

>[!NOTE]
>
>Als u de kijkers van douane S7 en het gebruiken van de Vinder van de Inhoud creeert en ontwikkelt, moet u de parameter **allowfullscreen** uitdrukkelijk toevoegen.

### Kennisgeving over de gebruiksduur van Flash-viewers {#flash-viewers-end-of-life-notice}

Met ingang van 31 januari 2017 zal Adobe Scene7 officieel ondersteuning voor het einde van de levensduur van het Flash-viewerplatform bieden.

Zie [Flash Viewer End-of-Life-veelgestelde vragen voor meer informatie over deze belangrijke wijziging](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Een component Scene7 aan een Pagina toevoegen {#adding-a-scene-component-to-a-page}

Het toevoegen van een component Scene7 aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. De componenten Scene7 worden beschreven in de volgende secties in detail.

Om een component Scene7/een kijker aan een pagina in klassieke UI toe te voegen:

1. In AEM, open de pagina waar u de component Scene7 wilt toevoegen.

1. Als geen componenten Scene7 beschikbaar zijn, klik de heerser in sidekick om de wijze van het **Ontwerp** in te gaan, klik **uitgeven** parsys, en selecteren alle componenten **Scene7** om hen beschikbaar te maken.

1. Keer terug naar de modus **Bewerken** door op het potlood in het zijpaneel te klikken.

1. Sleep een component van de groep **Scene7** in sidekick op de pagina in de gewenste plaats.

1. Klik op **Bewerken** om de component te openen.

1. Bewerk de component naar wens en klik op **OK** om de wijzigingen op te slaan.

### Interactieve weergaven toevoegen aan een responsieve website {#adding-interactive-viewing-experiences-to-a-responsive-website}

Het responsieve ontwerp voor uw middelen betekent dat uw middelen worden aangepast afhankelijk van waar ze worden weergegeven. Bij een responsief ontwerp kunnen dezelfde elementen effectief op meerdere apparaten worden weergegeven.

Een interactieve kijkervaring toevoegen aan een responsieve site in de klassieke gebruikersinterface:

1. Login aan AEM, en zorg ervoor dat u de Cloud Servicen [van Adobe Scene7 hebt](/help/sites-administering/scene7.md#configuring-scene-integration) gevormd en dat de componenten Scene7 beschikbaar zijn.

   >[!NOTE]
   >
   >Als de componenten Scene7 WCM niet beschikbaar zijn, zeker om hen via de wijze van het Ontwerp toe te laten.

1. In een website met toegelaten componenten Scene7, sleep een kijker van het **Beeld** aan de pagina.
1. Bewerk de component en pas de onderbrekingspunten aan op het tabblad **Scene7-instellingen** .

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Controleer of de viewers het formaat responsief wijzigen en of alle interacties zijn geoptimaliseerd voor computers, tablets en mobiele apparaten.

### Gemeenschappelijke montages voor alle componenten Scene7 {#settings-common-to-all-scene-components}

Hoewel de configuratieopties variëren, zijn het volgende gemeenschappelijk voor alle componenten Scene7:

* **Bestandsverwijzing**- Blader naar een bestand waarnaar u wilt verwijzen. De verwijzing van het dossier toont de activa URL en niet noodzakelijk volledige Scene7 URL met inbegrip van de bevelen URL en de parameters. U kunt geen bevelen Scene7 URL en parameters op dit gebied toevoegen. Ze moeten worden toegevoegd via de bijbehorende functionaliteit in de component.
* **Breedte** - Hiermee kunt u de breedte instellen.
* **Hoogte** - Hiermee kunt u de hoogte instellen.

U plaatst deze configuratieopties door (tweemaal klikkend) een component Scene7, bijvoorbeeld te openen wanneer u een component van het **Gezoem** opent:

![chlimage_1-52](assets/chlimage_1-52.png)

### In-/uitzoomen {#zoom}

De component HTML5 Zoom geeft een grotere afbeelding weer wanneer u op de knop + drukt.

Het element heeft onderaan zoomgereedschappen. Klik **+** om te vergroten. Klik **-** om te verminderen. Als u op de **x** - of zoompijl opnieuw instellen klikt, wordt de oorspronkelijke grootte van de afbeelding hersteld. Klik op de diagonale pijlen om deze op volledig scherm weer te geven. Klik op **Bewerken** om de component te configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle componenten](#settings-common-to-all-scene-components)Scene7.

![](do-not-localize/chlimage_1-3.png)

### Flyout {#flyout}

In de HTML5 Flyout-component wordt het element weergegeven als gesplitst scherm. het element in de opgegeven grootte laten staan; rechts wordt het zoomgedeelte weergegeven. Klik op **Bewerken** om de component te configureren. Met deze component, kunt u [montages vormen gemeenschappelijk voor alle componenten](/help/sites-administering/scene7.md#settingscommontoallscene7components)Scene7.

>[!NOTE]
>
>Als uw Flyout-component een aangepaste grootte gebruikt, wordt die aangepaste grootte gebruikt en wordt de responsieve instelling van de component uitgeschakeld.
>
>Als de component Flyout de standaardgrootte gebruikt, zoals die in de ontwerpweergave is ingesteld, wordt de standaardgrootte gebruikt en wordt de component uitgerekt om de grootte van de paginalay-out aan te passen met de responsieve instelling van de component ingeschakeld. Houd er echter rekening mee dat er een beperking geldt voor de responsieve instelling van de component. Wanneer u de component Flyout met ontvankelijke opstelling gebruikt, zou u het niet met volledige paginalrek moeten gebruiken. Anders kan de Flyout de rechterrand van de pagina overschrijden.

![chlimage_1-53](assets/chlimage_1-53.png)

### Image {#image}

De component van het Beeld Scene7 laat u functionaliteit Scene7 aan uw beelden, zoals bepalingen Scene7, beeld of kijker vooraf instelt, en het scherpen toevoegen. De scene7 beeldcomponent is gelijkaardig aan andere beeldcomponenten in AEM met speciale functionaliteit Scene7. In dit voorbeeld, heeft het beeld de bepaling Scene7 URL, **&amp;op_invert=1** toegepast.

![](do-not-localize/chlimage_1-4.png)

**Titel, Alt-tekst** op het tabblad Geavanceerd: voeg een titel toe aan de afbeelding en alternatieve tekst voor gebruikers die afbeeldingen hebben uitgeschakeld.

**URL, Openen in** U kunt een middel van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![chlimage_1-54](assets/chlimage_1-54.png)

**Viewer-voorinstelling** Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

**De Configuratie** Scene7 selecteert de configuratie Scene7 u wilt gebruiken om actieve beeldvoorinstellingen van SPS te halen.

**Afbeeldingsvoorinstelling** Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

**Uitvoerindeling** Selecteer de uitvoerindeling van de afbeelding, bijvoorbeeld jpeg. Afhankelijk van de uitvoerindeling die u selecteert, hebt u mogelijk aanvullende configuratieopties. Zie Aanbevolen werkwijzen voor voorinstellingen afbeelding.

**Met Verscherpen** selecteert u hoe u de afbeelding wilt verscherpen. Verscherpen wordt gedetailleerd uitgelegd in de aanbevolen werkwijzen voor voorinstellingen van afbeeldingen en in de aanbevolen werkwijzen voor Verscherpen.

**URL Modifiers** U kunt beeldgevolgen veranderen door extra S7 beeldbevelen te verstrekken. Deze worden beschreven in Voorinstellingen afbeelding en de opdrachtverwijzing.

**Onderbrekingspunten** Als uw website reageert, wilt u de onderbrekingspunten aanpassen. Onderbrekingspunten moeten worden gescheiden door komma&#39;s (,).

### Afbeeldingssjabloon {#image-template}

[Scene7 de Malplaatjes](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) van het Beeld zijn gelaagde inhoud Photoshop die in Scene7 werd ingevoerd, waar de inhoud en de eigenschappen voor variabiliteit werden bepaald. Met de sjablooncomponent **Afbeelding** kunt u afbeeldingen importeren en de tekst dynamisch wijzigen in AEM. Daarnaast kunt u de sjablooncomponent **Afbeelding** zodanig configureren dat waarden van de clientcontext worden gebruikt, zodat elke gebruiker de afbeelding op een gepersonaliseerde manier ervaart.

Klik op **Bewerken** om de component te configureren. U kunt [montages vormen gemeenschappelijk voor alle componenten](/help/sites-administering/scene7.md#settingscommontoallscene7components) Scene7 evenals andere montages die in deze sectie worden beschreven.

![chlimage_1-55](assets/chlimage_1-55.png)

**De Verwijzing van het dossier, Breedte, Hoogte** zie montages gemeenschappelijk voor alle componenten Scene7.

>[!NOTE]
>
>De bevelen en de parameters van Scene7 URL kunnen niet direct aan de Verwijzing URL van het Dossier worden toegevoegd. Ze kunnen alleen worden gedefinieerd in de gebruikersinterface van de component in het deelvenster **Parameter** .

**Titel, de Tekst** van Alt in het lusje van het Malplaatje van het Beeld Scene7, voeg een titel aan het beeld en alt tekst voor die gebruikers toe die grafiek hebben uitgezet.

**URL, Openen in** U kunt een middel van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![chlimage_1-56](assets/chlimage_1-56.png)

**Het deelvenster** Parameter wanneer u een afbeelding importeert, worden de parameters vooraf gevuld met informatie uit de afbeelding. Als er geen inhoud is die dynamisch kan worden gewijzigd, is dit venster leeg.

![chlimage_1-57](assets/chlimage_1-57.png)

#### Tekst dynamisch wijzigen {#changing-text-dynamically}

Als u de tekst dynamisch wilt wijzigen, voert u nieuwe tekst in de velden in en klikt u op **OK**. In dit voorbeeld is de **Prijs** nu $50 en de verzendkosten 99 cent.

![chlimage_1-58](assets/chlimage_1-58.png)

De tekst in de afbeelding verandert. U kunt de oorspronkelijke waarde van de tekst herstellen door op **Herstellen** naast het veld te klikken.

![chlimage_1-59](assets/chlimage_1-59.png)

#### Tekst wijzigen om de waarde van de context van een client weer te geven {#changing-text-to-reflect-the-value-of-a-client-context-value}

Als u een veld wilt koppelen aan de waarde van de clientcontext, klikt u op **Selecteren** om het contextmenu van de client te openen, selecteert u de context van de client en klikt u op **OK**. In dit voorbeeld verandert de naam op basis van de koppeling van de naam met de opgemaakte naam in het profiel.

![chlimage_1-60](assets/chlimage_1-60.png)

De tekst geeft de naam weer van de gebruiker die momenteel is aangemeld. U kunt de oorspronkelijke waarde van de tekst herstellen door op **Herstellen** naast het veld te klikken.

![chlimage_1-61](assets/chlimage_1-61.png)

#### Het maken van het beeld Scene7 malplaatje een verbinding {#making-the-scene-image-template-a-link}

Om van de Scene7 beeldmalplaatjecomponent een klikbare verbinding te maken:

1. Voor de pagina met de component van het beeldmalplaatje Scene7, geeft de klik **uit**.
1. Voer in het veld **URL** de URL in waarnaar gebruikers gaan wanneer op de afbeelding wordt geklikt. Selecteer in het veld **Openen in** of u het doel wilt openen (een nieuw venster of hetzelfde venster).

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Click **OK**.

### Video-component {#video-component}

De **Video** component Scene7 (beschikbaar bij de sectie Scene7 van sidekick) gebruikt apparaat en bandbreedteopsporing om de juiste video aan elk scherm te dienen. Deze component is een HTML5-videospeler; het is één viewer die via meerdere kanalen kan worden gebruikt.

Deze kan worden gebruikt voor adaptieve videosets, één MP4-video of één F4V-video.

Zie [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) voor meer informatie over hoe de video&#39;s met integratie Scene7 werken. Bovendien zie hoe [de video **component** Scene7 met de **stichtingsvideocomponent** vergelijkt](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-63](assets/chlimage_1-63.png)

### Bekende beperkingen voor de video-component {#known-limitations-for-the-video-component}

Adobe DAM en WCM laten zien of een primaire bronvideo is geüpload. Deze proxy-elementen worden niet weergegeven:

* Scene7 gecodeerde uitvoeringen
* Scene7 adaptieve videoreeksen

Wanneer het gebruiken van een adaptieve videoreeks met de videocomponent Scene7, zal de component resized om de afmetingen van de video te passen.

## Scene7-inhoudbrowser {#scene-content-browser}

De Scene7 inhoudsbrowser laat u inhoud van Scene7 direct in AEM bekijken. Om tot inhoudbrowser, in de Vinder van de Inhoud toegang te hebben, selecteer **Scene7** in het aanraking-geoptimaliseerde gebruikersinterface of het pictogram **S7** in het klassieke gebruikersinterface. De functionaliteit is identiek tussen beide gebruikersinterfaces.

Als u veelvoudige configuraties hebt, toont AEM door gebrek de [standaardconfiguratie](/help/sites-administering/scene7.md#configuring-a-default-configuration). U kunt verschillende configuraties direct in Scene7 inhoudsbrowser in het drop-down menu selecteren.

>[!NOTE]
>
>* De activa die in de ad hoc omslag worden gevestigd zullen niet in Scene7 inhoudsbrowser verschijnen.
>* Wanneer de [Veilige Voorproef wordt toegelaten](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), zowel verschijnen de gepubliceerde als unpublished activa op Scene7 in browser van de inhoud Scene7.
>* Als u **Scene7** of het pictogram **S7** niet als optie in inhoudbrowser ziet, moet u Scene7 [vormen om met AEM](/help/sites-administering/scene7.md)te werken.

   >
   >
* Voor video, steunt Scene7 inhoudsbrowser:
   >   * Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
   >   * Eén MP4-video
   >   * Single F4V-video


### Bladeren door inhoud {#browsing-content-in-the-classic-ui}

Blader inhoud in Scene7 door de **S7** tabel te klikken.

U kunt de configuratie veranderen u toegang hebt door de configuratie te selecteren.De omslagen veranderen afhankelijk van welke configuratie u selecteert.

![chlimage_1-64](assets/chlimage_1-64.png)

Net als bij de zoekfunctie voor inhoud naar Middelen kunt u zoeken naar elementen en resultaten filteren. In tegenstelling tot de zoeker bij Elementen, bij het invoeren van een trefwoord op het tabblad **S7** , **begint de bestandsnaam echter met** de tekenreeks die u hebt ingevoerd, in plaats van **het trefwoord in de bestandsnaam te bevatten** .

Elementen worden standaard weergegeven op bestandsnaam. U kunt resultaten ook filteren op type element.

>[!NOTE]
>
>Voor video, steunt Scene7 inhoudsbrowser van WCM:
>
>* Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
>* Eén MP4-video
>* Single F4V-video

>



### Het zoeken naar activa Scene7 met inhoudsbrowser {#searching-for-scene-assets-with-the-content-browser}

Het zoeken naar activa Scene7 is gelijkaardig aan het zoeken van activa AEM behalve dat wanneer u zoekt u eigenlijk een verre mening van de activa in het systeem Scene7 ziet, eerder dan het invoeren hen direct in AEM.

U kunt zowel de klassieke interface als de interface met geoptimaliseerde aanrakingen gebruiken om elementen weer te geven en te zoeken. Afhankelijk van de interface, is hoe u zoekt lichtjes verschillend.

Wanneer u in een van beide UI zoekt, kunt u filteren op de volgende criteria (die hier in de voor aanraking geoptimaliseerde UI worden getoond):

**Voer trefwoorden** in U kunt elementen zoeken op naam. Wanneer u de trefwoorden zoekt die u invoert, begint de bestandsnaam met. Als u bijvoorbeeld het woord &quot;zwemmen&quot; typt, wordt gezocht naar namen van elementbestanden die met die letters in die volgorde beginnen. Vergeet niet op Enter te klikken nadat u de term hebt getypt om het element te zoeken.

![chlimage_1-65](assets/chlimage_1-65.png)

**Map/pad** De naam van de map die wordt weergegeven, is gebaseerd op de configuratie die u hebt geselecteerd. U kunt tot lagere niveaus boor door het omslagpictogram te klikken en een subomslag te selecteren, dan het controleteken te klikken om het te selecteren.

Als u een trefwoord invoert en een map selecteert, doorzoekt AEM die map en eventuele submappen. Als u echter bij het zoeken geen trefwoorden invoert, worden bij het selecteren van de map alleen de elementen in die map weergegeven en worden er geen submappen opgenomen.

Standaard zoekt AEM naar de geselecteerde map en naar alle submappen.

![chlimage_1-66](assets/chlimage_1-66.png)

**Het type van Activum** selecteert Scene7 om inhoud te doorbladeren Scene7. Deze optie is slechts beschikbaar als Scene7 is gevormd.

![chlimage_1-67](assets/chlimage_1-67.png)

**De configuratie** als u meer dan één configuratie Scene7 die in Cloud Servicen wordt bepaald hebt, kunt u het hier selecteren. Hierdoor wordt de map gewijzigd op basis van de gekozen configuratie.

![chlimage_1-68](assets/chlimage_1-68.png)

**Het type** van activa binnen browser Scene7, kunt u resultaten filtreren om het even welke volgend op te nemen: afbeeldingen, sjablonen, video&#39;s en adaptieve videosets. Als u geen elementtype selecteert, worden standaard alle elementtypen doorzocht.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>* In de klassieke interface kunt u ook zoeken naar **Flash** en **FXG**. Filteren hiervoor in de interface met geoptimaliseerde aanrakingen wordt momenteel niet ondersteund.
   >
   >
* Bij het zoeken naar video zoekt u op één vertoning. Resultaten retourneren de oorspronkelijke uitvoering (alleen *.mp4) en de gecodeerde uitvoering.
* Wanneer u in een adaptieve videoset zoekt, zoekt u in de map en in alle submappen, maar alleen als u een trefwoord aan de zoekopdracht hebt toegevoegd. Als u geen trefwoord hebt toegevoegd, doorzoekt AEM de submappen niet.



**Publicatiestatus** U kunt filteren op elementen die zijn gebaseerd op de publicatiestatus: Niet gepubliceerd of gepubliceerd. Als u geen publicatiestatus selecteert, worden standaard alle publicatiestatussen doorzocht.

![chlimage_1-70](assets/chlimage_1-70.png)
