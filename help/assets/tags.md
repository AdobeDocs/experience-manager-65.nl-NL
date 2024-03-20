---
title: Dynamic Media-viewers integreren met Adobe Analytics- en Experience Platform-tags
description: Meer informatie over de extensie Dynamic Media Viewers voor Experience Platform Tags en Dynamic Media Viewers 5.13. Het laat klanten van Adobe Analytics en de Markeringen van het Experience Platform gebeurtenissen en gegevens gebruiken specifiek voor de Kijkers van Dynamic Media in hun configuratie van de Markeringen van het Experience Platform.
mini-toc-levels: 3
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
docset: aem65
feature: Viewers
role: User, Admin,Developer,Data Engineer,Data Architect
exl-id: 161dfe22-bc1c-4b60-8ab6-a19407a39e2e
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '6264'
ht-degree: 6%

---

# Dynamic Media-viewers integreren met Adobe Analytics- en Experience Platform-tags {#integrating-dynamic-media-viewers-with-adobe-analytics-and-adobe-launch}

## Wat is de integratie van Dynamic Media Viewers met Adobe Analytics en Experience Platform Tags? {#what-is-dynamic-media-viewers-integration-with-adobe-analytics-and-adobe-launch}

<!-- Leave this hidden path here; it points to the topic source from Sasha https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=~oufimtse&title=Dynamic+Media+Viewers+integration+with+Adobe+Launch -->

*Dynamic Media Viewers* Met de extensie Experience Platform Tags en Dynamic Media Viewers 5.13 kunnen klanten met Adobe Analytics- en Experience Platform Tags gebeurtenissen en gegevens gebruiken die specifiek zijn voor Dynamic Media Viewers in hun configuratie met Experience Platform Tags.

Dankzij deze integratie kunt u het gebruik van Dynamic Media Viewers op uw website bijhouden met Adobe Analytics. Tegelijkertijd kunt u de gebeurtenissen en gegevens gebruiken die door de viewers worden weergegeven, met een andere extensie Experience Platform Tags die afkomstig is van een Adobe of een derde.

Zie voor meer informatie over Adobe-extensies of extensies van derden [Extensies Adoben](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/overview.html) in de gebruikershandleiding voor tags Experience Platform.

**Dit onderwerp is bedoeld voor het volgende:** De beheerders van de plaats, Ontwikkelaars op het Experience Platform, en mensen in Verrichtingen.

### Beperkingen van de integratie {#limitations-of-the-integration}

* Integratie van Experience Platform-tags voor Dynamic Media-viewers werkt niet in het knooppunt van de auteur van de Experience Manager. U kunt geen het volgen van een pagina zien WCM tot het wordt gepubliceerd.
* Integratie van Experience Platform-tags voor Dynamic Media-viewers wordt niet ondersteund in de pop-upbewerkingsmodus, waarin de URL van de viewer wordt verkregen via de knop &quot;URL&quot; op de pagina Asset Details.
* Integratie van Experience Platform Tags kan niet gelijktijdig worden gebruikt met de integratie van verouderde viewers Analytics (via `config2=` parameter).
* Ondersteuning voor het bijhouden van video&#39;s is beperkt tot het bijhouden van de &#39;kern playback&#39;, zoals wordt beschreven in [Overzicht van bijhouden](https://experienceleague.adobe.com/docs/media-analytics/using/tracking/track-core-overview.html?lang=en). Met name QoS, Advertenties, Hoofdstuk/Segmenten, of het volgen van Fouten wordt niet gesteund.
* De configuratie van de Duur van de opslag voor Elementen van Gegevens wordt niet gesteund voor Elementen van Gegevens die gebruiken *Dynamic Media Viewers* extensie. Opslagduur moet worden ingesteld op **[!UICONTROL None]**.

### Gebruik de integratiegevallen {#use-cases-for-the-integration}

Het belangrijkste gebruiksgeval voor de integratie met Experience Platform Tags is klanten die zowel Adobe Experience Manager Assets als Adobe Experience Manager Sites gebruiken. In dergelijke scenario&#39;s, kunt u opstelling een standaardintegratie tussen uw de auteurknoop van de Experience Manager en de Markeringen van het Experience Platform, dan uw instantie van Plaatsen met het bezit van de Markeringen van het Experience Platform associëren. Daarna volgt elke Dynamic Media WCM-component die aan een sitepagina wordt toegevoegd, de gegevens en gebeurtenissen van viewers.

Zie [Dynamic Media-viewers bijhouden in Experience Manager Sites](#tracking-dynamic-media-viewers-in-aem-sites).

Een tweede gebruiksgeval dat de integratie steunt zijn die klanten die slechts Experience Manager Assets, of Dynamic Media Classic gebruiken. In dergelijke gevallen ontvangt u de insluitcode voor uw viewer en voegt u deze toe aan de websitepagina. Vervolgens haalt u de productie-URL voor de bibliotheek met Experience Platform-tags op uit Experience Platform-tags en voegt u deze handmatig toe aan de webpaginacode.

Zie [Dynamic Media-viewers bijhouden met behulp van insluitcode](#tracking-dynamic-media-viewers-using-embed-code).

<!-- Path on internal wiki [About tracking Dynamic Media viewers using embed code](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersusingEmbedcode). -->

## Hoe gegevens en gebeurtenis volgen werkt in de integratie {#how-data-and-event-tracking-works-in-the-integration}

De integratie maakt gebruik van twee aparte en onafhankelijke typen tracering voor Dynamic Media Viewers: *Adobe Analytics* en *Adobe Analytics for Audio and Video*.

### Over reeksspatiëring in Adobe Analytics  {#about-tracking-using-adobe-analytics}

Met Adobe Analytics kunt u handelingen bijhouden die door de eindgebruiker worden uitgevoerd wanneer deze communiceert met Dynamic Media Viewers op uw website. Met Adobe Analytics kunt u ook viewerspecifieke gegevens bijhouden. U kunt bijvoorbeeld de laadgebeurtenissen van de weergave bijhouden en opnemen, samen met de naam van het element, eventuele zoomacties die hebben plaatsgevonden en handelingen voor het afspelen van video.

In de Markeringen van het Experience Platform, de concepten van *Gegevenselementen* en *Regels* samenwerken om het volgen van Adobe Analytics toe te laten.

#### Gegevenselementen in Experience Platform-tags {#about-data-elements-in-adobe-launch}

Een gegevenselement in Experience Platform-tags is een benoemde eigenschap waarvan de waarde statisch wordt gedefinieerd of dynamisch wordt berekend op basis van de status van een webpagina of Dynamic Media Viewers-gegevens.

De opties die beschikbaar zijn voor een definitie van een gegevenselement, zijn afhankelijk van de lijst met extensies die zijn geïnstalleerd in de eigenschap Codes van het Experience Platform. De &quot;Core&quot;uitbreiding is vooraf geïnstalleerd en beschikbaar uit de doos in om het even welke configuratie. Met de extensie &quot;Core&quot; kunt u een gegevenselement definiëren dat afkomstig is van cookie, JavaScript-code, queryreeks en vele andere bronnen.

Als u wilt dat Adobe Analytics meerdere extensies kan bijhouden, moet u de extensies installeren die worden beschreven in [Installatie en installatie van extensies](#installing-and-setup-of-extensions). Met de extensie Dynamic Media Viewers kunt u een gegevenselement definiëren dat een argument is van de gebeurtenis Dynamic Viewer. Het is bijvoorbeeld mogelijk te verwijzen naar het viewertype, of de naam van het element die tijdens het laden door de viewer wordt gemeld, het zoomniveau dat wordt gemeld wanneer de eindgebruiker zoomt en nog veel meer.

Met de extensie Dynamic Media Viewer worden de waarden van de Data Elements automatisch bijgewerkt.

Nadat u het hebt bepaald, kan een Element van Gegevens in andere plaatsen van de Tags UI van het Experience Platform worden gebruikt, gebruikend de plukker van het Element van Gegevens widget. Met name wordt in de regel naar gegevenselementen die zijn gedefinieerd voor het bijhouden van Dynamic Media Viewers verwezen door de extensie Handeling voor variabelen instellen van Adobe Analytics (zie hieronder).

Zie [Gegevenselementen](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/data-elements.html).

#### Informatie over Regels in Experience Platform-tags {#about-rules-in-adobe-launch}

Een regel in de Markeringen van het Experience Platform is een agnostische configuratie die drie gebieden bepaalt die omhoog een regel maken: *Gebeurtenissen*, *Voorwaarden*, en *Handelingen*:

* *Gebeurtenissen* (if) vertel de Markeringen van het Experience Platform wanneer om een Regel te teweegbrengen.
* *Voorwaarden* (if) vertel de Markeringen van het Experience Platform welke andere beperkingen om toe te staan of te verbieden wanneer het teweegbrengen van een Regel.
* *Handelingen* (dan) vertel de Markeringen van het Experience Platform wat te doen wanneer een Regel wordt teweeggebracht.

Welke opties beschikbaar zijn in de sectie Gebeurtenissen, Voorwaarden en Handelingen, is afhankelijk van de extensies die zijn geïnstalleerd in de eigenschap Experience Platform-tags. De *Kern* wordt vooraf geïnstalleerd en is beschikbaar uit-van-de-doos in om het even welke configuratie. De extensie biedt verschillende opties voor gebeurtenissen, zoals basishandelingen op browserniveau. Deze acties zijn onder andere focuswijziging, toetsdrukken en het verzenden van formulieren. Het bevat ook opties voor Voorwaarden, zoals cookiewaarde, browsertype en meer. Voor Acties is alleen de optie Aangepaste code beschikbaar.

Voor het bijhouden van Adobe Analytics moeten verschillende andere extensies worden geïnstalleerd, zoals beschreven in [Installatie en installatie van extensies](#installing-and-setup-of-extensions). Specifiek:

* De extensie Dynamic Media Viewers breidt de lijst met ondersteunde gebeurtenissen uit tot gebeurtenissen die specifiek zijn voor Dynamic Media-viewers, zoals het laden van viewers, het wisselen van middelen, inzoomen en het afspelen van video.
* De extensie Adobe Analytics breidt de lijst met ondersteunde handelingen uit met twee handelingen die vereist zijn voor het verzenden van gegevens naar trackingservers: *Variabelen instellen* en *Bandbaken verzenden*.

Als u Dynamic Media-viewers wilt bijhouden, kunt u elk type van de volgende opties gebruiken:

* Gebeurtenissen van de extensie Dynamic Media Viewers, Core-extensie of een andere extensie.
* Voorwaarden in de definitie van de regel. Of u kunt het gebied met voorwaarden leeg laten.

In de sectie Acties is het vereist dat u een *Variabelen instellen* handeling. Deze actie vertelt Adobe Analytics hoe te om het volgen variabelen met gegevens te bevolken. Tegelijkertijd worden *Variabelen instellen* actie verzendt niets naar de volgende server.

De *Variabelen instellen* de actie moet worden gevolgd door een *Bandbaken verzenden* handeling. De *Bandbaken verzenden* de actie verzendt eigenlijk gegevens naar de analytische volgende server. Beide handelingen, *Variabelen instellen* en *Bandbaken verzenden*, afkomstig uit de extensie Adobe Analytics.

Zie [Regels](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html).

#### Voorbeeldconfiguratie {#sample-configuration}

In de volgende voorbeeldconfiguratie binnen Experience Platform Tags ziet u hoe u een elementnaam kunt bijhouden tijdens het laden van de viewer.

1. Van de **[!UICONTROL Data Elements]** tab, een gegevenselement definiëren `AssetName` verwijzingen `asset` parameter van de `LOAD` uit de extensie Dynamic Media Viewers.

   ![image2019-11](assets/image2019-11.png)

1. Van de **[!UICONTROL Rules]** tab, een regel definiëren *TrackAssetOnLoad*.

   In deze regel geldt het **[!UICONTROL Event]** in het veld wordt het **[!UICONTROL LOAD]** uit de extensie Dynamic Media Viewers.

   ![image2019-22](assets/image2019-22.png)

1. De configuratie van de Actie heeft twee types van Actie van de uitbreiding van Adobe Analytics:

   *Variabelen instellen*, die een door u gekozen analytische variabele toewijst aan de waarde van `AssetName` Gegevenselement.

   *Bandbaken verzenden*, die trackinggegevens naar Adobe Analytics verzendt.

   ![image2019-3](assets/image2019-3.png)

1. De resulterende regelconfiguratie ziet er als volgt uit:

   ![image2019-4](assets/image2019-4.png)

### Informatie over Adobe Analytics for Audio en Video {#about-adobe-analytics-for-audio-and-video}

Als een Experience Cloud-account is geabonneerd op Adobe Analytics for Audio en Video, is het voldoende om het bijhouden van video&#39;s in te schakelen in de *Dynamic Media Viewers* extensie-instellingen. Videomeetgegevens zijn beschikbaar in Adobe Analytics. Het bijhouden van video&#39;s is afhankelijk van de aanwezigheid van Adobe Media Analytics for Audio and Video extension.

Zie [Installatie en installatie van extensies](#installing-and-setup-of-extensions).

De ondersteuning voor het bijhouden van video&#39;s is momenteel beperkt tot het bijhouden van de &#39;core playback&#39;, zoals beschreven in [Overzicht van bijhouden](https://experienceleague.adobe.com/docs/media-analytics/using/tracking/track-core-overview.html?lang=en). Met name QoS, Advertenties, Hoofdstuk/Segmenten, of het volgen van Fouten wordt niet gesteund.

## De extensie Dynamic Media Viewers gebruiken {#using-the-dynamic-media-viewers-extension}

Zoals vermeld in [Gebruik de integratiegevallen](#use-cases-for-the-integration), is het mogelijk om Dynamic Media-viewers bij te houden met de nieuwe integratie van Experience Platform Tags in Experience Manager Sites en door insluitcode te gebruiken.

### Dynamic Media-viewers bijhouden in Experience Manager Sites {#tracking-dynamic-media-viewers-in-aem-sites}

Als u Dynamic Media-viewers in Experience Manager Sites wilt bijhouden, voert u alle stappen onder de [Alle integratieonderdelen configureren](#configuring-all-the-integration-pieces) moet worden uitgevoerd. Specifiek, moet u de configuratie IMS en de Configuratie van de Wolk van de Markeringen van het Experience Platform tot stand brengen.

Na de juiste configuratie worden gegevens automatisch bijgehouden in Dynamic Media-viewers die u aan een sitepagina toevoegt met behulp van een WCM-component die door Dynamic Media wordt ondersteund, naar Adobe Analytics, Adobe Analytics for Video of beide.

<!-- To be reviewed and updated although this is found live in the Experience ManageraaCS version:
See [Adding Dynamic Media Assets to Pages using Adobe Sites](https://helpx.adobe.com/experience-manager/6-5/help/assets/adding-dynamic-media-assets-to-pages.html).
-->

### Dynamic Media-viewers bijhouden met behulp van insluitcode {#tracking-dynamic-media-viewers-using-embed-code}

Klanten die geen gebruik maken van Experience Manager Sites of Dynamic Media-viewers insluiten in webpagina&#39;s buiten Experience Manager Sites of beide, kunnen de integratie met Experience Platform Tags nog steeds gebruiken.

Voltooi de configuratiestappen van de [Adobe Analytics configureren](#configuring-adobe-analytics-for-the-integration) en [Experience Platform-tags configureren](#configuring-adobe-launch-for-the-integration) secties. Nochtans, zijn de op Experience Manager betrekking hebbende configuratiestappen niet nodig.

Na de juiste configuratie kunt u ondersteuning voor Experience Platform-tags toevoegen aan een webpagina met een Dynamic Media-viewer.

Zie [De insluitcode voor Experience Platform-tags toevoegen](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/add-embed-code.html) voor meer informatie over hoe u de insluitcode van de bibliotheek Experience Platform Tags kunt gebruiken.

<!-- To be reviewed and updated although this is found live in the Experience ManageraaCS version:
See [Embedding the Video or Image Viewer on a Web Page](https://helpx.adobe.com/experience-manager/6-5/help/assets/embed-code.html) to learn more about how to use the embed code feature of Experience Manager Dynamic Media.
-->

**Dynamic Media-viewers bijhouden met gebruik van insluitcode:**

1. Een webpagina klaar hebben voor het insluiten van een Dynamic Media-viewer.
1. Verkrijg de insluitcode voor de bibliotheek van de Markeringen van het Experience Platform door zich eerst aan te melden bij de Markeringen van het Experience Platform (zie [Experience Platform-tags configureren](#configuring-adobe-launch-for-the-integration)).
1. Selecteren **[!UICONTROL Property]** en selecteert u vervolgens de **[!UICONTROL Environments]** tab.
1. Ophalen van het milieuniveau dat relevant is voor de omgeving van de webpagina. Dan, in **[!UICONTROL Install]** selecteert u het pictogram van het vak.
1. **[!UICONTROL In the Web Install Instructions]** in, kopieert u de volledige insluitcode van de bibliotheek met Experience Platforms-tags en de omringende `<script/>` -tags.

## Referentiegids voor de extensie Dynamic Media Viewers {#reference-guide-for-the-dynamic-media-viewers-extension}

### De configuratie van Dynamic Media Viewers {#about-the-dynamic-media-viewers-configuration}

De extensie Dynamic Media Viewer wordt automatisch geïntegreerd met de bibliotheek met Experience Platform-tags als aan de volgende voorwaarden wordt voldaan:

* Globaal object Experience Platform Tags, bibliotheek ( `_satellite`) is aanwezig op de pagina.
* De extensiefunctie Dynamic Media Viewers `_dmviewers_v001()` is gedefinieerd op `_satellite`.

* `config2=` Er is geen viewerparameter opgegeven, wat betekent dat de viewer geen gebruik maakt van verouderde analytische integratie.

Er is ook een optie om de integratie van Experience Platform-tags in de viewer expliciet uit te schakelen door `launch=0` in de configuratie van de viewer. De standaardwaarde van deze parameter is `1`.

### De extensie Dynamic Media Viewers configureren {#configuring-the-dynamic-media-viewers-extension}

De enige configuratieoptie voor de extensie Dynamic Media Viewers is **[!UICONTROL Enable Adobe Media Analytics for Audio and Video]**.

Wanneer u deze optie inschakelt en de extensie Adobe Media Analytics for Audio en Video is geïnstalleerd en geconfigureerd, worden meetgegevens voor het afspelen van video naar de Adobe Analytics for Audio and Video-oplossing verzonden. Als u deze optie uitschakelt, wordt het bijhouden van video uitgeschakeld.

Als u deze optie inschakelt *zonder* Als Adobe Media Analytics voor Audio en Video wordt geïnstalleerd, heeft de optie geen effect.

![image2019-7-22_12-4-23](assets/image2019-7-22_12-4-23.png)

### Over Data Elements in de extensie Dynamic Media Viewers {#about-data-elements-in-the-dynamic-media-viewers-extension}

Het enige data-elementtype dat de uitbreiding Dynamische mediaviewers biedt, is **[!UICONTROL Viewer Event]** in de vervolgkeuzelijst **[!UICONTROL Data Element Type]**.

Als deze optie is geselecteerd, maakt de Data Element-editor een formulier met twee velden:

* **[!UICONTROL DM viewers event data type]** - een vervolgkeuzelijst met alle viewergebeurtenissen die door de uitbreiding Dynamische mediaviewers worden ondersteund en die argumenten bevatten, plus een speciaal **[!UICONTROL COMMON]**-item. Een **[!UICONTROL COMMON]**-item vertegenwoordigt een lijst met gebeurtenisparameters die gemeenschappelijk zijn voor alle typen gebeurtenissen die door de viewers worden verzonden.
* **[!UICONTROL Tracking parameter]** - een argument van de geselecteerde Dynamic Media-viewergebeurtenis.

![image2019-7-22_12-5-46](assets/image2019-7-22_12-5-46.png)

Zie de [Referentiehandleiding voor Dynamic Media Viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc) voor de lijst met ondersteunde gebeurtenissen per viewertype; ga naar de specifieke viewersectie en selecteer vervolgens Ondersteuning voor de subsectie Adobe Analytics tracking. Op dit moment worden in de naslaggids voor Dynamic Media Viewers geen gebeurtenisargumenten vastgelegd.

Bekijk nu de levenscyclus van de Dynamic Media Viewers *Gegevenselement*. De waarde van een dergelijk gegevenselement wordt gevuld nadat de bijbehorende Dynamic Media-viewergebeurtenis op de pagina plaatsvindt. Stel dat het gegevenselement verwijst naar de **[!UICONTROL LOAD]** en het argument &quot;asset&quot; ervan. In dat geval ontvangt de waarde van een dergelijk gegevenselement geldige gegevens nadat de viewer het **[!UICONTROL LOAD]** voor de eerste keer. Als het gegevenselement naar de **[!UICONTROL ZOOM]** -gebeurtenis en het bijbehorende &quot;scale&quot;-argument, blijft de waarde van een dergelijk gegevenselement leeg totdat de gebruiker een **[!UICONTROL ZOOM]** voor de eerste keer.

Op dezelfde manier worden de waarden van data-elementen automatisch bijgewerkt wanneer de viewer een overeenkomstige gebeurtenis op de pagina verzendt. De waarde-update gebeurt zelfs als de specifieke gebeurtenis niet in de regelconfiguratie is opgegeven. Stel bijvoorbeeld dat het gegevenselement **[!UICONTROL ZoomScale]** wordt gedefinieerd voor de parameter &quot;scale&quot; van de ZOOM-gebeurtenis. Nochtans, wordt de enige regel huidig in de configuratie van de Regel teweeggebracht door **[!UICONTROL LOAD]** gebeurtenis. De waarde van **[!UICONTROL ZoomScale]** wordt nog steeds bijgewerkt wanneer een gebruiker inzoomt in de viewer.

Elke viewer voor dynamische media heeft een unieke id op de webpagina. Het gegevenselement houdt de waarde zelf bij en de viewer die de waarde heeft gevuld. Stel dat er meerdere viewers op dezelfde pagina staan en dat er een **[!UICONTROL AssetName]** Gegevenselement dat naar het **[!UICONTROL LOAD]** en het argument &quot;asset&quot; ervan. De **[!UICONTROL AssetName]** Het gegevenselement handhaaft een inzameling van activa namen die met elke kijker worden geassocieerd die op de pagina wordt geladen.

De exacte waarde die door het gegevenselement wordt geretourneerd, is afhankelijk van de context. Als het gegevenselement wordt gevraagd in een Regel die door een de kijkergebeurtenis van Dynamic Media werd teweeggebracht, dan is de waarde van het Element van Gegevens teruggekeerd voor de kijker die de Regel in werking stelde. En, wordt het Element van Gegevens gevraagd in een Regel die door een Gebeurtenis van één of andere uitbreiding van de Markeringen van het Experience Platform werd teweeggebracht. Op dat punt, komt de waarde van het Element van Gegevens uit de kijker die het laatst dit Element van Gegevens bijwerkte.

**Overweeg de volgende voorbeeldopstelling:**

* Een webpagina met twee Dynamic Media-zoomviewers: *viewer1* en *viewer2*.

* **[!UICONTROL ZoomScale]** Het gegevenselement wijst naar de **[!UICONTROL ZOOM]** en het argument &quot;scale&quot;.
* **[!UICONTROL TrackPan]** Regel met het volgende:

   * Gebruikt de Dynamic Media Viewer **[!UICONTROL PAN]** gebeurtenis als trigger.
   * Verzendt de waarde van **[!UICONTROL ZoomScale]** Gegevenselement naar Adobe Analytics.

* **[!UICONTROL TrackKey]** Regel met het volgende:

   * Gebruikt de belangrijkste persgebeurtenis van de uitbreiding van de Markeringen van het Experience Platform van de Kern als trekker.
   * Verzendt de waarde van **[!UICONTROL ZoomScale]** Gegevenselement naar Adobe Analytics.

Nu, veronderstel de eindgebruiker de Web-pagina met de twee kijkers laadt. In *viewer1*, worden ze ingezoomd op een schaal van 50% en vervolgens op *viewer2* en zoomen ze in op een schaal van 25%. In *viewer1*, pannen ze de afbeelding rond en selecteren ze ten slotte een toets op het toetsenbord.

De activiteit van de eindgebruiker resulteert in de volgende twee volgende volgende vraag die aan Adobe Analytics wordt gemaakt:

* De eerste oproep doet zich voor omdat **[!UICONTROL TrackPan]** De regel wordt geactiveerd wanneer de gebruiker het programma in *viewer1*. Die vraag verzendt 50% als waarde van **[!UICONTROL ZoomScale]** Het Element van gegevens omdat het Element van Gegevens weet dat de Regel door wordt teweeggebracht *viewer1* en haalt de overeenkomstige schaalwaarde op;
* De tweede aanroep doet zich voor omdat **[!UICONTROL TrackKey]** De regel wordt geactiveerd wanneer de gebruiker op een toets op het toetsenbord drukt. Die vraag verzendt 25% als waarde van **[!UICONTROL ZoomScale]** Gegevenselement omdat de regel niet door de viewer is geactiveerd. Als dusdanig, keert het Element van Gegevens de meest bijgewerkte waarde terug.

Het voorbeeld hierboven heeft ook invloed op de levensduur van de waarde voor het gegevenselement. De waarde van het gegevenselement dat door de Dynamic Media Viewer wordt beheerd, wordt opgeslagen in de bibliotheekcode van Experience Platforms Tags, zelfs nadat de viewer zelf op de webpagina is verwijderd. Deze functionaliteit houdt in dat als er een regel is die door een niet-Dynamic Media Viewer-extensie wordt geactiveerd en naar een dergelijk gegevenselement verwijst, het gegevenselement de laatst bekende waarde retourneert. Zelfs als de viewer niet meer aanwezig is op de webpagina.

In elk geval worden de waarden van gegevenselementen die door Dynamic Media Viewers worden aangestuurd, niet opgeslagen op de lokale opslag of op de server. In plaats daarvan worden ze alleen bewaard in de tagbibliotheek van het client-side Experience Platform. Waarden van een dergelijk gegevenselement verdwijnen als de webpagina opnieuw wordt geladen.

Over het algemeen wordt de Data Element-editor ondersteund [selectie van opslagduur](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/data-elements.html#create-a-data-element). Gegevenselementen die de extensie Dynamic Media Viewers gebruiken, ondersteunen echter alleen de opslagduuroptie van **[!UICONTROL None]**. Het instellen van een andere waarde is mogelijk in de gebruikersinterface, maar het gedrag Gegevenselement is in dit geval niet gedefinieerd. De extensie beheert de waarde van het gegevenselement op zichzelf: het gegevenselement dat de waarde van het gebeurtenisargument van de viewer behoudt tijdens de volledige levenscyclus van de viewer.

### Over Regels in de extensie Dynamic Media Viewers {#about-rules-in-the-dynamic-media-viewers-extension}

In de redacteur van de Regel, voegt de uitbreiding nieuwe configuratieopties voor de redacteur van Gebeurtenissen toe. De editor biedt ook een optie om handmatig te verwijzen naar gebeurtenisparameters in de Action Editor als een kortzichtige optie in plaats van vooraf geconfigureerde gegevenselementen te gebruiken.

#### Informatie over de Events-editor {#about-the-events-editor}

In de gebeurteniseditor voegt de extensie Dynamic Media Viewers een **[!UICONTROL Event Type]** gebeld **[!UICONTROL Viewer Event]**.

Als deze optie is geselecteerd, wordt de vervolgkeuzelijst weergegeven in de gebeurteniseditor **[!UICONTROL Dynamic Media Viewer events]**, waarin alle beschikbare gebeurtenissen worden vermeld die door Dynamic Media-viewers worden ondersteund.

![image2019-8-2_15-13-1](assets/image2019-8-2_15-13-1.png)

#### De Editor voor handelingen {#about-the-actions-editor}

Met de extensie Dynamic Media Viewers kunt u gebeurtenisparameters van Dynamic Media-viewers gebruiken om de variabelen voor de analyse in te delen in de editor Variabelen instellen van de Adobe Analytics-extensie.

De eenvoudigste methode om dat te doen is het volgende twee-stap proces te voltooien:

* Definieer eerst een of meer gegevenselementen, waarbij elk gegevenselement een parameter van een Dynamic Media Viewer-gebeurtenis vertegenwoordigt.
* Tot slot selecteert u in de editor Variabelen instellen van de extensie Adobe Analytics de optie **[!UICONTROL Data Element]** Pictogram van de plukker (drie gestapelde schijven) om het Uitgezochte de dialoogvakje van het Element van Gegevens te openen, dan selecteer een Element van Gegevens van het.

![image2019-7-10_20-41-52](assets/image2019-7-10_20-41-52.png)

Het is echter mogelijk om een alternatieve manier te gebruiken en het maken van data-elementen te omzeilen. U kunt rechtstreeks verwijzen naar een argument van een Dynamic Media Viewer-gebeurtenis. Voer de volledig gekwalificeerde naam van het gebeurtenisargument in het dialoogvenster **[!UICONTROL value]** invoerveld van de variabele Analytics-toewijzing. Zorg ervoor dat u het omringt met procenttekens (%). Bijvoorbeeld:

`%event.detail.dm.LOAD.asset%`

![image2019-7-12_19-2-35](assets/image2019-7-12_19-2-35.png)

Er is een belangrijk verschil tussen het gebruik van Data Elements en de verwijzing naar directe-gebeurtenisargumenten. Voor het Element van Gegevens, maakt het niet uit welke gebeurtenis de Vastgestelde actie van Variabelen teweegbrengt. De gebeurtenis die de regel activeert, kan geen verband houden met Dynamic Viewer. Selecteer bijvoorbeeld de webpagina in de extensie Core. Maar wanneer het gebruiken van een directe argumentverwijzing is het belangrijk om ervoor te zorgen dat de gebeurtenis die de regel teweegbrengt aan het gebeurtenisargument beantwoordt dat het verwijst.

Als bijvoorbeeld wordt verwezen naar `%event.detail.dm.LOAD.asset%`, wordt de juiste assetnaam geretourneerd als de regel wordt getriggerd door de gebeurtenis **[!UICONTROL LOAD]** van de uitbreiding Dynamische mediaviewer. Er wordt echter een lege waarde voor elke andere gebeurtenis geretourneerd.

De volgende tabel bevat een lijst met Dynamic Media Viewer-gebeurtenissen en de argumenten die hiervoor worden ondersteund:

<table>
 <tbody>
  <tr>
   <td>Naam van viewergebeurtenis</td>
   <td>Argument reference</td>
  </tr>
  <tr>
   <td><code>COMMON</code></td>
   <td><code>%event.detail.dm.objID%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.compClass%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.instName%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.timeStamp%</code></td>
  </tr>
  <tr>
   <td><code>BANNER</code><br /> </td>
   <td><code>%event.detail.dm.BANNER.asset%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.BANNER.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.BANNER.label%</code></td>
  </tr>
  <tr>
   <td><code>HREF</code></td>
   <td><code>%event.detail.dm.HREF.rollover%</code></td>
  </tr>
  <tr>
   <td><code>ITEM</code></td>
   <td><code>%event.detail.dm.ITEM.rollover%</code></td>
  </tr>
  <tr>
   <td><code>LOAD</code></td>
   <td><code>%event.detail.dm.LOAD.applicationname%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.asset%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.company%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.sdkversion%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.viewertype%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.viewerversion%</code></td>
  </tr>
  <tr>
   <td><code>METADATA</code></td>
   <td><code>%event.detail.dm.METADATA.length%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.METADATA.type%</code></td>
  </tr>
  <tr>
   <td><code>MILESTONE</code></td>
   <td><code>%event.detail.dm.MILESTONE.milestone%</code></td>
  </tr>
  <tr>
   <td><code>PAGE</code></td>
   <td><code>%event.detail.dm.PAGE.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.PAGE.label%</code></td>
  </tr>
  <tr>
   <td><code>PAUSE</code></td>
   <td><code>%event.detail.dm.PAUSE.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>PLAY</code></td>
   <td><code>%event.detail.dm.PLAY.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>SPIN</code></td>
   <td><code>%event.detail.dm.SPIN.framenumber%</code></td>
  </tr>
  <tr>
   <td><code>STOP</code></td>
   <td><code>%event.detail.dm.STOP.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>SWAP</code></td>
   <td><code>%event.detail.dm.SWAP.asset%</code></td>
  </tr>
  <tr>
   <td><code>SWATCH</code></td>
   <td><code>%event.detail.dm.SWATCH.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.SWATCH.label%</code></td>
  </tr>
  <tr>
   <td><code>TARG</code></td>
   <td><code>%event.detail.dm.TARG.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.TARG.label%</code></td>
  </tr>
  <tr>
   <td><code>ZOOM</code></td>
   <td><code>%event.detail.dm.ZOOM.scale%</code></td>
  </tr>
 </tbody>
</table>

## Alle integratieonderdelen configureren {#configuring-all-the-integration-pieces}

**VOORDAT U BEGINT**

Adobe raadt u aan alle documentatie vóór deze sectie grondig te bekijken, zodat u de volledige integratie begrijpt.

In deze sectie worden de configuratiestappen beschreven die nodig zijn om Dynamic Media-viewers te integreren met Adobe Analytics en Adobe Analytics for Audio en Video. Hoewel het gebruik van de extensie Dynamic Media Viewers voor andere doeleinden in Experience Platforms tags mogelijk is, worden dergelijke scenario&#39;s niet behandeld in deze documentatie.

U gaat de volgende producten van de Adobe gebruiken om uw integratie te vormen:

* Adobe Analytics - gebruikt om het volgen variabelen en rapporten te vormen.
* Tags voor Experience Platforms - worden gebruikt om een eigenschap, een of meer regels en een of meer gegevenselementen te definiëren om het bijhouden van de viewer in te schakelen.

Als deze integratieoplossing wordt gebruikt met Experience Manager Sites, moet ook de volgende configuratie worden uitgevoerd:

* [!DNL Adobe Developer Console] - er wordt integratie voor Experience Platform-tags gecreëerd.
* Knooppunt van de auteur van de Experience Manager - de configuratie IMS en de wolkenconfiguratie van de Markeringen van het Experience Platform.

Als deel van de configuratie, zeker bent u toegang tot een bedrijf in Adobe Experience Cloud hebt dat Adobe Analytics en de Markeringen van het Experience Platform reeds heeft toegelaten.

## Adobe Analytics configureren voor integratie {#configuring-adobe-analytics-for-the-integration}

Nadat u Adobe Analytics hebt geconfigureerd, wordt het volgende voor integratie ingesteld:

* Er is een rapportsuite geïnstalleerd en geselecteerd.
* De Variabelen van de Analyse zijn beschikbaar om het volgen gegevens te ontvangen.
* Rapporten zijn beschikbaar voor het weergeven van verzamelde gegevens in Adobe Analytics.

Zie ook [Handleiding voor analytische implementatie](https://experienceleague.adobe.com/docs/analytics/implementation/home.html).

**Adobe Analytics configureren voor integratie:**

1. Start via Adobe Analytics vanuit het Experience Cloud [homepage](https://experience.adobe.com/#/home). Selecteer in de menubalk de optie **[!UICONTROL Solutions]** pictogram (drie bij drie punten) in de rechterbovenhoek van de pagina en selecteert u vervolgens **[!UICONTROL Analytics]**.

   ![2019-07-22_18-08-47](assets/2019-07-22_18-08-47.png)

   Selecteer nu een rapportsuite.

### Selecteer een rapportsuite {#selecting-a-report-suite}

1. Selecteer in de rechterbovenhoek van de Adobe Analytics-pagina rechts van het veld **[!UICONTROL Search Reports]** de juiste rapportsuite in de vervolgkeuzelijst. Als er meerdere rapportsuites beschikbaar zijn en u niet zeker weet welke suite u moet gebruiken, neemt u contact op met uw Adobe Analytics-beheerder. Deze beheerder kan u helpen bij het selecteren van de rapportsuite die moet worden gebruikt.

   In de onderstaande schermafbeelding heeft een gebruiker een rapportsuite gemaakt met de naam *DynamicMediaViewersExtensionDoc* en selecteert u deze in de vervolgkeuzelijst. De naam van de rapportsuite is alleen een voorbeeldnaam. De naam van de rapportsuite die u uiteindelijk selecteert, is aan u.

   Als er geen rapportsuite beschikbaar is, moet u of uw Adobe Analytics-beheerder er een maken voordat u verder kunt gaan met de configuratie.

   Zie [Rapporten en rapportsuite](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/report-suites-admin.html) en [Een rapportsuite maken](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite.html).

   In Adobe Analytics worden rapportsuites beheerd onder **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]**.

   ![2019-07-22_18-09-49](assets/2019-07-22_18-09-49.png)

   Stel nu Adobe Analytics-variabelen in.

### Adobe Analytics-variabelen instellen {#setting-up-adobe-analytics-variables}

1. Wijs een of meer Adobe Analytics-variabelen aan die u wilt gebruiken om het gedrag van Dynamic Media Viewers op de webpagina bij te houden.

   U kunt elk type variabele gebruiken dat door Adobe Analytics wordt ondersteund. Het besluit over het veranderlijke type (zoals het Verkeer van de Douane [props], Omzetting [eVar]) wordt aangestuurd door de specifieke behoeften van uw analytische implementatie.

   Zie [Overzicht van props en eVars](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html#vars).

   In het kader van deze documentatie wordt alleen een variabele Custom Traffic (props) gebruikt, omdat deze binnen een paar minuten nadat een handeling op een webpagina heeft plaatsgevonden, beschikbaar komt in een Analytics-rapport.

   Als u een nieuwe aangepaste verkeersvariabele wilt inschakelen, gaat u in Adobe Analytics op de werkbalk naar **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]**.

1. Op de **[!UICONTROL Report Suite Manager]** pagina, selecteert u het juiste rapport en navigeert u vervolgens op de werkbalk naar **[!UICONTROL Edit Settings]** > **[!UICONTROL Traffic]** > **[!UICONTROL Traffic Variables]**.
1. Selecteer een variabele die niet wordt gebruikt, geef deze een beschrijvende naam (**[!UICONTROL Viewer asset (prop 30)]**) en wijzig keuzelijst met invoervak in &quot;Ingeschakeld&quot; in de kolom Ingeschakeld.

   De volgende schermafbeelding is een voorbeeld van een variabele van het Verkeer van de Douane ( **[!UICONTROL prop30]**) voor het bijhouden van een elementnaam die door de viewer wordt gebruikt:

   ![image2019-6-26_23-6-59](assets/image2019-6-26_23-6-59.png)

1. Selecteer onder aan de lijst met variabelen de optie **[!UICONTROL Save]**.

### Een rapport instellen {#setting-up-a-report}

1. Over het algemeen wordt het opstellen van een rapport in Adobe Analytics gestuurd door specifieke projectbehoeften. Als dusdanig, is de gedetailleerde rapportopstelling voorbij het werkingsgebied voor deze integratie.

   Het is echter voldoende om te weten dat de rapporten Aangepast verkeer automatisch beschikbaar worden in Adobe Analytics nadat u aangepaste verkeersvariabelen hebt ingesteld in [Adobe Analytics-variabelen instellen](#setting-up-adobe-analytics-variables).

   Het rapport voor **[!UICONTROL Viewer asset (prop 30)]** variabele is beschikbaar in het menu Rapporten onder **[!UICONTROL Custom Traffic]** > **[!UICONTROL Custom Traffic 21-30]** > **[!UICONTROL Viewer asset (prop 30)]**.

   Als u dit rapport meteen na het maken van **[!UICONTROL Viewer asset (prop 30)]** bezoekt, worden er geen data weergegeven. Dat wordt op dit moment in de integratie verwacht.

   ![image2019-6-26_23-12-49](assets/image2019-6-26_23-12-49.png)

## Experience Platform-tags configureren voor integratie {#configuring-adobe-launch-for-the-integration}

Nadat u de Markeringen van het Experience Platform vormt, wordt het volgende opstelling voor de integratie:

* Het creëren van een nieuw Bezit om al uw configuraties samen te houden.
* De installatie en installatie van extensies. De client-side code van alle extensies die in de eigenschap zijn geïnstalleerd, wordt samen gecompileerd in een bibliotheek. Deze bibliotheek wordt later door de webpagina gebruikt.
* Configuratie van gegevenselementen en regels. Deze configuratie bepaalt welke gegevens van de kijkers van Dynamic Media moeten vangen, wanneer om de volgende logica teweeg te brengen, en waar om de gegevens van de kijker in Adobe Analytics te verzenden.
* Publiceren van de bibliotheek.

**Om de Markeringen van het Experience Platform voor de integratie te vormen:**

1. Begin door de Markeringen van het Experience Platform van het Experience Cloud toegang te hebben [homepage](https://experience.adobe.com/#/home). Selecteer in de menubalk de optie **[!UICONTROL Solutions]** pictogram (drie bij drie punten) rechts boven aan de pagina en selecteert u **[!UICONTROL Tags]**.

   U kunt [Experience Platform-tags rechtstreeks openen](https://launch.adobe.com/).

   ![image2019-7-8_15-38-44](assets/image2019-7-8_15-38-44.png)

### Een eigenschap maken in Experience Platform-tags {#creating-a-property-in-adobe-launch}

Een bezit in de Markeringen van het Experience Platform is een genoemde configuratie die al uw montages bij elkaar houdt. Er wordt een bibliotheek met de configuratie-instellingen gegenereerd en gepubliceerd op verschillende milieuniveaus (ontwikkeling, staging en productie).

Zie ook [Een eigenschap Tags maken](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/initial-configuration/configure-tags.html).

1. Selecteer in Experience Platform-tags de optie **[!UICONTROL New Property]**.
1. Typ in het dialoogvenster **[!UICONTROL Create Property]** in het veld **[!UICONTROL Name]** een beschrijvende naam, zoals de titel van uw website. Bijvoorbeeld: `DynamicMediaViewersProp.`
1. In de **[!UICONTROL Domains]** , voert u het domein van uw website in.
1. In de **[!UICONTROL Advanced Options]** vervolgkeuzelijst, inschakelen **[!UICONTROL Configure for extension development (cannot be modified later)]** in het geval dat de extensie die u wilt gebruiken, in dit geval: *Dynamic Media Viewers*—wordt nog niet vrijgegeven.

   ![image2019-7-8_16-3-47](assets/image2019-7-8_16-3-47.png)

1. Selecteren **[!UICONTROL Save]**.

   Selecteer de nieuwe eigenschap en ga verder met *Installatie en installatie van extensies*.

### Extensies installeren en instellen {#installing-and-setup-of-extensions}

Alle beschikbare extensies in Experience Platform-tags worden onder **[!UICONTROL Extensions]** > **[!UICONTROL Catalog]**.

Als u een extensie wilt installeren, selecteert u **[!UICONTROL Install]**. Voer zo nodig een eenmalige extensieconfiguratie uit en selecteer **[!UICONTROL Save]**.

Waar nodig moeten de volgende extensies worden geïnstalleerd en geconfigureerd:

* (Vereist) *Experience Cloud-id-service* extensie.

Geen extra configuratie is nodig, keur voor om het even welke voorgestelde waarden goed. Zorg ervoor dat u **[!UICONTROL Save]**.

Zie [Adobe Experience Cloud Identity Service-extensie](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/id-service/overview.html).

* (Vereist) *Adobe Analytics* extension

Als u deze extensie wilt configureren, hebt u de rapportsuite-id in Adobe Analytics nodig, onder **[!UICONTROL Admin]** > **[!UICONTROL Report Suite]**, onder de **[!UICONTROL Report Suite ID]** kolomkop.

(Alleen voor demonstratiedoeleinden, de rapportsuite-id van de **[!UICONTROL DynamicMediaViewersExtensionDoc]** Report Suite wordt gebruikt in de volgende schermafbeeldingen. Deze id is gemaakt en gebruikt in [Selecteer een rapportsuite](#selecting-a-report-suite) eerder.)

![image2019-7-8_16-45-34](assets/image2019-7-8_16-45-34.png)

Voer op de pagina Uitbreiding installeren de rapportsuite-id in het veld **[!UICONTROL Development Report Suites]**, het veld **[!UICONTROL Staging Report Suites]** en het veld **[!UICONTROL Production Report Suites]** in.

![image2019-7-8_16-47-40](assets/image2019-7-8_16-47-40.png)

*Configureer het volgende item alleen als u videotracering wilt gebruiken:*

Op de **[!UICONTROL Install Extension]** pagina, uitbreiden **[!UICONTROL General]** en geeft u vervolgens de trackingserver op. De volgende server volgt de sjabloon `<trackingNamespace>.sc.omtrdc.net`, waarbij `<trackingNamespace>` Dit is de informatie die wordt verkregen in de e-mail met provisioning.

Selecteren **[!UICONTROL Save]**.

Zie [Adobe Analytics-extensie](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/analytics/overview.html).

* (Optioneel; alleen vereist als videotracering nodig is) *Adobe Media Analytics voor audio en video* extension

Vul het veld Trackingserver in. De trackingserver voor *Adobe Media Analytics voor audio en video* De extensie verschilt van de trackingserver die voor Adobe Analytics wordt gebruikt. Hiervoor volgt de sjabloon `<trackingNamespace>.hb.omtrdc.net`, waarbij `<trackingNamespace>` Dit is de informatie uit de e-mail met provisioning.

Alle andere velden zijn optioneel.

Zie [Adobe Media Analytics voor audio- en video-extensie](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/media-analytics/overview.html).

* (Vereist) *Dynamic Media Viewers* extension

Schakel **[!UICONTROL enable Adobe Analytics for Video]** in om het bijhouden van videorecorders in te schakelen.

Bij het schrijven van de *Dynamic Media Viewers* De extensie is alleen beschikbaar als de eigenschap Experience Platform-tags is gemaakt voor ontwikkeling.

Zie [Een eigenschap maken in Experience Platform-tags](#creating-a-property-in-adobe-launch).

Nadat de extensies zijn geïnstalleerd en ingesteld, worden ten minste de volgende vijf extensies (vier extensies als u geen video bijhoudt) weergegeven in het gedeelte Extensies > Geïnstalleerd.

![image2019-7-22_12-7-36](assets/image2019-7-22_12-7-36.png)

### Gegevenselementen en regels instellen {#setting-up-data-elements-and-rules}

Maak gegevenselementen en -regels in Experience Platform-tags die nodig zijn voor het bijhouden van Dynamic Media-viewers.

Zie [Hoe gegevens en gebeurtenis volgen werkt in de integratie](#how-data-and-event-tracking-works-in-the-integration) voor een overzicht van het bijhouden van Experience Platforms Tags.

Zie [Voorbeeldconfiguratie](#sample-configuration) voor een voorbeeldconfiguratie in Experience Platform Tags die aantoont hoe een elementnaam bij het laden van de viewer wordt bijgehouden.

Zie [De extensie Dynamic Media Viewers configureren](#configuring-the-dynamic-media-viewers-extension) voor uitgebreide informatie over de mogelijkheden van de extensie.

### Bibliotheek publiceren {#publishing-a-library}

Als u de configuratie van Experience Platform Tags wilt wijzigen (inclusief de instelling Eigenschap, Extensies, Regels en Gegevenselementen), moet u *publish* dergelijke wijzigingen. Het publiceren in de Markeringen van het Experience Platform wordt uitgevoerd van het Publiceren lusje onder de configuratie van het Bezit.

De Markeringen van het Experience Platform kunnen veelvoudige milieu&#39;s van de Ontwikkeling, één het Opvoeren milieu, en één milieu van de Productie potentieel hebben. Door gebrek wijst de Configuratie van de Wolk van de Markeringen van het Experience Platform in Experience Manager de Experience Manager auteurknoop aan het milieu van het Stadium van de Markeringen van het Experience Platform. Het knooppunt Experience Manager publiceren verwijst naar de productieomgeving van Experience Platform-tags. Dit betekent dat met de standaardinstellingen voor Experience Managers, de bibliotheek met Experience Platform-tags moet worden gepubliceerd naar de testomgeving. Zo kunt u het gebruiken in de auteur van de Experience Manager. U kunt het dan publiceren in het milieu van de Productie zodat het in Experience Manager kan worden gebruikt publiceren.

Zie [Omgevingen](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/environments/environments.html) voor meer informatie over Experience Platform Tags-omgevingen.

Bij het publiceren van een bibliotheek worden de volgende twee stappen uitgevoerd:

* Het toevoegen van en het bouwen van een nieuwe bibliotheek door alle noodzakelijke veranderingen (nieuwe degenen en updates) in de bibliotheek te omvatten.
* De bibliotheek door de verschillende milieuniveaus verplaatsen (van Ontwikkeling tot Staging en Productie).

#### Een nieuwe bibliotheek toevoegen en maken {#adding-and-building-a-new-library}

1. De eerste keer dat u het tabblad Publiceren opent in Experience Platform-tags, is de bibliotheeklijst leeg.

   Selecteer in de linkerkolom **[!UICONTROL Add New Library]**.

   ![image2019-7-15_14-43-17](assets/image2019-7-15_14-43-17.png)

1. Op de pagina Nieuwe bibliotheek maken klikt u in het dialoogvenster **[!UICONTROL Name]** Voer een beschrijvende naam in voor de nieuwe bibliotheek. Bijvoorbeeld:

   *DynamicMediaViewersLib*

   Kies in de vervolgkeuzelijst Milieu het niveau Milieu. In eerste instantie is alleen het ontwikkelingsniveau beschikbaar voor selectie. Selecteer in de linkerbenedenhoek van de pagina de optie **[!UICONTROL Add All Changed Resources]**.

   ![image2019-7-15_14-49-41](assets/image2019-7-15_14-49-41.png)

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save & Build for Development]**.

   Over een paar minuten wordt de bibliotheek gemaakt en klaar voor gebruik.

   ![image2019-7-15_15-3-34](assets/image2019-7-15_15-3-34.png)

   >[!NOTE]
   >
   >De volgende keer dat u de configuratie van de tags van het Experience Platform wijzigt, gaat u naar **[!UICONTROL Publishing]** onder de **[!UICONTROL Property]** en selecteert u de eerder gemaakte bibliotheek.
   >
   >
   >Selecteer in het publicatiescherm van de bibliotheek de optie **[!UICONTROL Add All Changed Resources]** selecteert u vervolgens **[!UICONTROL Save & Build for Development]**.

#### Een bibliotheek omhoog verplaatsen via omgevingsniveaus {#moving-a-library-up-through-environment-levels}

1. Nadat er een nieuwe bibliotheek is toegevoegd, bevindt deze zich in de ontwikkelomgeving. Als u het wilt verplaatsen naar het niveau van de testomgeving (dat overeenkomt met de kolom Verzenden), selecteert u in het vervolgkeuzemenu van de bibliotheek de optie **[!UICONTROL Submit for Approval]**.

   ![image2019-7-15_15-52-37](assets/image2019-7-15_15-52-37.png)

1. Selecteer in het bevestigingsdialoogvenster de optie **[!UICONTROL Submit]**.

   Als de bibliotheek naar de kolom Verstuurd is gegaan, selecteert u in het vervolgkeuzemenu van de bibliotheek de optie **[!UICONTROL Build for Staging]**.

   ![image2019-7-15_15-54-37](assets/image2019-7-15_15-54-37.png)

1. Als u de bibliotheek wilt verplaatsen van de testomgeving naar de productieomgeving (de kolom Published), voert u een vergelijkbaar proces uit.

   Selecteer eerst in het keuzemenu de optie **[!UICONTROL Approve for Publishing]**.

   ![image2019-7-15_16-7-39](assets/image2019-7-15_16-7-39.png)

1. Selecteer in het keuzemenu de optie **[!UICONTROL Build & Publish to Production]**.

   ![image2019-7-15_16-8-9](assets/image2019-7-15_16-8-9.png)

   Zie [Publiceren](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) voor meer informatie over het publicatieproces in Experience Platforms Tags.

## Adobe Experience Manager configureren voor integratie {#configuring-adobe-experience-manager-for-the-integration}

Vereisten:

* Experience Manager voert zowel auteur- als publicatieinstanties uit.
* Het schrijverknooppunt van de Experience Manager is ingesteld in de uitvoeringsmodus Dynamic Media - Scene7 (dynamicmedia_s7)
* Dynamic Media WCM-componenten zijn ingeschakeld in Experience Manager Sites.

De configuratie van de Experience Manager bestaat uit de volgende twee belangrijke stappen:

* Configuratie van Experience Manager IMS.
* Configuratie van Experience Platform Tags Cloud.

### Experience Manager-IMS configureren {#configuring-aem-ims}

1. Selecteer in de auteur van de Experience Manager de **[!UICONTROL Tools]** pictogram (hamer), ga dan naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

   ![2019-07-25_11-52-58](assets/2019-07-25_11-52-58.png)

1. Selecteer in de Adobe-IMC-configuratiepagina in de linkerbovenhoek de optie **[!UICONTROL Create]**.
1. Op de **[!UICONTROL Adobe IMS Technical Account Configuration]** pagina, in de **[!UICONTROL Cloud Solution]** vervolgkeuzelijst, selecteert u **[!UICONTROL Experience Platform Tags]**.
1. Inschakelen **[!UICONTROL Create new certificate]** Voer vervolgens in het tekstveld een betekenisvolle waarde voor het certificaat in. Bijvoorbeeld: *AdobeLaunchIMSCert*. Selecteren **[!UICONTROL Create certificate]**.

   Het volgende Info-bericht wordt weergegeven:

   *Als u een geldig toegangstoken wilt ophalen, wordt de openbare sleutel van het nieuwe certificaat toegevoegd aan de technische account op Adobe Developer Console!*

   Selecteer **[!UICONTROL OK]**.

   ![2019-07-25_12-09-24](assets/2019-07-25_12-09-24.png)

1. Een bestand met een openbare sleutel downloaden (&#42;.crt) naar uw lokale systeem, selecteert u **[!UICONTROL Download Public Key]**.

   >[!NOTE]
   >
   >Op dit punt ***open laten*** de **[!UICONTROL Adobe IMS Technical Account Configuration]** pagina; ***niet*** sluit de pagina en ***niet*** Selecteer Volgende. U gaat later in de stappen terug naar deze pagina.

   ![2019-07-25_12-52-24](assets/2019-07-25_12-52-24.png)

1. Navigeer in een nieuw browsertabblad naar [[!DNL Adobe Developer Console]](https://developer.adobe.com/console/integrations).

1. Van de **[!UICONTROL Adobe Developer Console Integrations]** pagina, bij de rechterbovenhoek, selecteert u **[!UICONTROL New integration]**.
1. In de **[!UICONTROL Create a new integration]** , zorgt u ervoor dat **[!UICONTROL Access an API]** keuzerondje is geselecteerd en selecteer vervolgens **[!UICONTROL Continue]**.

   ![2019-07-25_13-04-20](assets/2019-07-25_13-04-20.png)

1. Schakel op de tweede pagina **[!UICONTROL Create a new integration]** het keuzerondje **[!UICONTROL Experience Platform Tags API]** in. Selecteer in de rechterbenedenhoek van de pagina de optie **[!UICONTROL Continue]**.

   ![2019-07-25_13-14](assets/2019-07-25_13-13-54.png)

1. Op de derde **[!UICONTROL Create a new integration]** pagina, ga als volgt te werk:

   * In de **[!UICONTROL Name]** veld, voert u een beschrijvende naam in. Bijvoorbeeld: *DynamicMediaViewersIO*.

   * In de **[!UICONTROL Description]** , voert u een beschrijving in voor de integratie.

   * In de **[!UICONTROL Public key certificates]** gebied, uploadt u het bestand met de openbare sleutel (&#42;.crt) die u eerder in deze stappen hebt gedownload.

   * Onder de **[!UICONTROL Select a role for Experience Platform Tags API]** kop, selecteren **[!UICONTROL Admin]**.

   * Onder de **[!UICONTROL Select one or more product profiles for Experience Platform Tags API]** Selecteer het productprofiel met de naam **[!UICONTROL Tags - <your_company_name>]**.

   ![2019-07-25_13-49-18](assets/2019-07-25_13-49-18.png)

1. Selecteren **[!UICONTROL Create integration]**.
1. Op de **[!UICONTROL Integration created]** pagina, selecteert u **[!UICONTROL Continue to integration details]**.

   ![2019-07-25_14-16-33](assets/2019-07-25_14-16-33.png)

1. Er verschijnt een pagina met integratiegegevens. **** vergelijkbaar met het volgende:

   >[!NOTE]
   >
   >***Laat deze pagina met integratiedata open***. U zult verschillende stukken van informatie van nodig hebben **[!UICONTROL Overview]** en **[!UICONTROL JWT]** tabs even.

   ![2019-07-25_14-35-30](assets/2019-07-25_14-35-30.png)

   Pagina met integratiegegevens.

1. Ga terug naar de pagina **[!UICONTROL Adobe IMS Technical Account Configuration]** die u eerder geopend hebt gelaten. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Next]** om de **[!UICONTROL Account]** pagina in de **[!UICONTROL Adobe IMS Technical Account Configuration]** venster.

   (Als u de pagina eerder hebt gesloten, gaat u terug naar de auteur van de Experience Manager en navigeert u naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Selecteer **[!UICONTROL Create]**. Selecteer in de vervolgkeuzelijst **[!UICONTROL Cloud Solution]** de optie **[!UICONTROL Experience Platform Tags]**. In de **[!UICONTROL Certificate]** de naam van het eerder gemaakte certificaat.)

   ![2019-07-25_20-57-50](assets/2019-07-25_20-57-50.png)

   Configuratie technische account van Adobe IMS - Certificaatpagina.

1. De **[!UICONTROL Account]** De pagina heeft vijf gebieden die u moet invullen gebruikend informatie van de de detailpagina van de Integratie van de vorige stap.

   ![2019-07-25_20-42-45](assets/2019-07-25_20-42-45.png)

   Configuratie technische account van Adobe IMS - Accountpagina.

1. Op de **[!UICONTROL Account]** pagina, vult de volgende velden in:

   * **[!UICONTROL Title]** - Voer een beschrijvende accounttitel in.
   * **[!UICONTROL Authorization Server]** - Ga terug naar de pagina met integratiegegevens die u eerder hebt geopend. Selecteer de **[!UICONTROL JWT]** tab. Kopieer de servernaam, zonder het pad, zoals hieronder gemarkeerd.

   Terugkeren naar de **[!UICONTROL Account]** en plakt u de naam in het desbetreffende veld.
Bijvoorbeeld: `https://ims-na1.adobelogin.com/`
(De servernaam is alleen een voorbeeld)

   ![2019-07-25_15-01-53](assets/2019-07-25_15-01-53.png)

   Detailpagina voor integratie - tabblad JWT

1. **[!UICONTROL API Key]** - Ga terug naar de pagina met integratiedetails. Selecteer de **[!UICONTROL Overview]** en vervolgens rechts van de knop **[!UICONTROL API Key (Client ID)]** veld, selecteren **[!UICONTROL Copy]**.

   Ga terug naar de pagina **[!UICONTROL Account]** en plak de toets in het desbetreffende veld.

   ![2019-07-25_14-35-33](assets/2019-07-25_14-35-333.png)

   Pagina met integratiegegevens.

1. **[!UICONTROL Client Secret]** - Ga terug naar de pagina met integratiedetails. Van de **[!UICONTROL Overview]** tab, selecteert u **[!UICONTROL Retrieve Client Secret]**. Rechts van het **[!UICONTROL Client secret]** veld, selecteren **[!UICONTROL Copy]**.

   Ga terug naar de pagina **[!UICONTROL Account]** en plak de toets in het desbetreffende veld.

1. **[!UICONTROL Payload]** - Ga terug naar de pagina met integratiedetails. Van de **[!UICONTROL JWT]** , kopieert u in het veld JWT Payload de gehele JSON-objectcode.

   Ga terug naar de pagina **[!UICONTROL Account]** en plak de code in het desbetreffende veld.

   ![2019-07-25_21-59-12](assets/2019-07-25_21-59-12.png)

   Pagina met integratiegegevens - tabblad JWT

   De pagina Account, met alle velden ingevuld, ziet er ongeveer als volgt uit:

   ![2019-07-25_22-08-30](assets/2019-07-25_22-08-30.png)

1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Account]** pagina, selecteert u **[!UICONTROL Create]**.

   Met gevormde Experience Manager IMS, hebt u nu een nieuwe die rekening IMSA onder wordt vermeld **[!UICONTROL Adobe IMS Configurations]**.

   ![image2019-7-15_14-17-54](assets/image2019-7-15_14-17-54.png)

## Cloud met Experience Platform Tags configureren voor integratie {#configuring-adobe-launch-cloud-for-the-integration}

1. Selecteer in de Experience Manager de optie **[!UICONTROL Tools]** pictogram (hamer), ga dan naar **[!UICONTROL Cloud Services]** > **[!UICONTROL Experience Platform Tags Configurations]**.

   ![2019-07-26_12-10-38](assets/2019-07-26_12-10-38.png)

1. Op de **[!UICONTROL Experience Platform Tags Configurations]** pagina, in het linkerpaneel, selecteer een Plaats van de Experience Manager waarvoor u uw Configuratie van de Markeringen van het Experience Platform wilt toepassen.

   Uitsluitend voor steekproefdoeleinden **`We.Retail`** is geselecteerd in de onderstaande schermafbeelding.

   ![2019-07-26_12-20-06](assets/2019-07-26_12-20-06.png)

1. Selecteer in de linkerbovenhoek van de pagina de optie **[!UICONTROL Create]**.
1. Vul op de pagina **[!UICONTROL General]** (1/3 pagina&#39;s) van het venster **[!UICONTROL Create Experience Platform Tags Configuration]** de volgende velden in:

   * **[!UICONTROL Title]** - Voer een beschrijvende configuratitel in. Bijvoorbeeld: `We.Retail Tags cloud configuration`.

   * **[!UICONTROL Associated Adobe IMS Configuration]** - Selecteer de IMS-configuratie die u eerder hebt gemaakt in [Experience Manager-IMS configureren](#configuring-aem-ims).

   * **[!UICONTROL Company]** - van de **[!UICONTROL Company]** Selecteer uw bedrijf van de Experience Cloud. De lijst wordt automatisch gevuld.

   * **[!UICONTROL Property]** - Selecteer in de vervolgkeuzelijst Eigenschap de eigenschap Experience Platform-tags die u eerder hebt gemaakt. De lijst wordt automatisch gevuld.

   Nadat u alle velden hebt ingevuld, kunt u **[!UICONTROL General]** De pagina ziet er ongeveer als volgt uit:

   ![image2019-7-15_14-34-23](assets/image2019-7-15_14-34-23.png)

1. Selecteer in de linkerbovenhoek de optie **[!UICONTROL Next]**.
1. Vul op de pagina **[!UICONTROL Staging]** (2/3 pagina&#39;s) van het venster **[!UICONTROL Create Experience Platform Tags Configuration]** het volgende veld in:

   In de **[!UICONTROL Library URI]** (Uniform Resource Identifier). Controleer de locatie van de testversie van de Experience Platform Tags-bibliotheek. Experience Manager vult dit veld automatisch in.

   Voor steekproefdoeleinden slechts, gebruikt deze stap de bibliotheken van de Markeringen van het Experience Platform die aan Adobe CDN worden opgesteld.

   >[!NOTE]
   >
   >Controleer of de automatisch gevulde bibliotheek-URI (Uniform Resource Identifier) niet onjuist is samengesteld. Herstel indien nodig de URL zodanig dat deze een protocol-relatieve URI vertegenwoordigt. Dat wil zeggen dat het begint met een dubbele slash.
   >
   >
   >Bijvoorbeeld: `//assets.adobetm.com/launch-xxxx`.

   Uw **[!UICONTROL Staging]** Deze pagina wordt waarschijnlijk op de volgende pagina weergegeven. De **[!UICONTROL Archive]** en **[!UICONTROL Load Library Asynchronously]** opties zijn ***niet*** set:

   ![image2019-7-15_15-21-8](assets/image2019-7-15_15-21-8.png)

1. Selecteer in de rechterbovenhoek de optie **[!UICONTROL Next]**.
1. Herstel, indien nodig, de automatisch gevulde productie-URI op de pagina **[!UICONTROL Production]** (3/3 pagina&#39;s) van het venster **[!UICONTROL Create Experience Platform Tags Configuration]** op ongeveer dezelfde manier als op de vorige pagina **[!UICONTROL Staging]**.
1. Selecteer in de rechterbovenhoek de optie **[!UICONTROL Create]**.

   Uw nieuwe Configuratie van de Codes Cloud van het Experience Platform wordt nu gecreeerd en naast uw website vermeld gelijkend op het volgende voorbeeld:

1. Selecteer uw nieuwe Configuratie van de Codes van de Wolk van het Experience Platform (een vinkje verschijnt links van de configuratietaak wanneer het wordt geselecteerd). Selecteer op de werkbalk de optie **[!UICONTROL Publish]**.

   ![image2019-7-15_15-47-6](assets/image2019-7-15_15-47-6.png)

Momenteel biedt de auteur van de Experience Manager geen ondersteuning voor de integratie van Dynamic Media Viewers met Experience Platform-tags.

Deze wordt echter wel ondersteund in het publicatieknooppunt Experience Manager. Gebruikend de standaardinstellingen van de Configuratie van de Wolk van de Markeringen van het Experience Platform, gebruikt de Experience Manager publicatieknooppunt de productiemilieu van de Markeringen van het Experience Platform. Daarom is het noodzakelijk om de bibliotheekupdates van de Markeringen van het Experience Platform van Ontwikkeling tot aan het milieu van de Productie elke keer tijdens de test te duwen.

Het is mogelijk om deze beperking te omzeilen. Geef de ontwikkelings- of staging-URL van de bibliotheek Platform Tags op in de Cloud-configuratie voor Experience Platforms voor het publicatieknooppunt van de Experience Manager hierboven. Dit maakt de Experience Manager publicatieknooppunt gebruiken de versie van de Markeringen van het Experience Platform van de Ontwikkeling of van het Staging.

Zie [Experience Manager met Experience Platform-tags integreren via [!DNL Adobe Developer Console]](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html) voor meer informatie over het instellen van Experience Platform Tags Cloud Configuration.
