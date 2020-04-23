---
title: Dynamic Media-viewers integreren met Adobe Analytics en Adobe Launch
description: Met de extensie Dynamic Media Viewers voor Adobe Launch en de release van Dynamic Media Viewers 5.13 kunnen klanten van Dynamic Media, Adobe Analytics en Adobe Launch gebeurtenissen en gegevens gebruiken die specifiek zijn voor de Dynamic Media Viewers in hun Adobe Launch-configuratie.
uuid: d218ee1c-cd2c-40c3-a3d4-b95719ae8e98
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: f4051767-182e-4cfd-9dfc-8f516378e0b6
docset: aem65
translation-type: tm+mt
source-git-commit: e8f97f6164a5021609917b99feb0608bcea59553

---


# Dynamic Media-viewers integreren met Adobe Analytics en Adobe Launch {#integrating-dynamic-media-viewers-with-adobe-analytics-and-adobe-launch}

## Wat is de integratie van Dynamic Media Viewers met Adobe Analytics en Adobe Launch? {#what-is-dynamic-media-viewers-integration-with-adobe-analytics-and-adobe-launch}

Met de nieuwe extensie *Dynamic Media Viewers* voor Adobe Launch en de recente release van Dynamic Media Viewers 5.13 kunnen klanten van Dynamic Media, Adobe Analytics en Adobe Launch gebeurtenissen en gegevens gebruiken die specifiek zijn voor de Dynamic Media Viewers in hun Adobe Launch-configuratie.

Dankzij deze integratie kunt u het gebruik van Dynamic Media Viewers op uw website bijhouden met Adobe Analytics. Tegelijkertijd kunt u de gebeurtenissen en gegevens gebruiken die door de viewers beschikbaar worden gesteld, met elke andere extensie voor Starten die afkomstig is van Adobe of een derde.

Zie [Adobe Extension](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/overview.html) in de gebruikershandleiding bij Starten van ervaringsplatform voor meer informatie over extensies.

**Doelgroep van deze documentatie:** Sitebeheerders, ontwikkelaars op het AEM-platform en beheerders in bewerkingen.

### Beperkingen van de integratie {#limitations-of-the-integration}

* De integratie van Adobe Launch voor Dynamic Media-viewers werkt niet in het auteurknooppunt van AEM. U kunt geen het volgen van een pagina zien WCM tot het wordt gepubliceerd.
* De integratie van Adobe Launch voor Dynamic Media-viewers wordt niet ondersteund in de pop-upbewerkingsmodus, waarin de URL van de viewer wordt verkregen met de knop &quot;URL&quot; op de pagina Asset Details.
* Adobe Launch-integratie kan niet gelijktijdig worden gebruikt met de integratie van verouderde viewers Analytics (via de `config2=` parameter).
* Ondersteuning voor het bijhouden van video&#39;s is beperkt tot alleen het bijhouden van de kern, zoals wordt beschreven in [Overzicht](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html)van bijhouden. Met name QoS, Advertenties, Hoofdstuk/Segmenten, of het volgen van Fouten wordt niet gesteund.
* De configuratie van de Duur van de opslag voor Elementen van Gegevens wordt niet gesteund voor Elementen van Gegevens gebruikend de *Dynamische uitbreiding van Kijkers* van Media. Opslagduur moet zijn ingesteld op **[!UICONTROL Geen]**.

### Gebruik de integratiegevallen {#use-cases-for-the-integration}

Het belangrijkste gebruiksscenario voor de integratie met Adobe Launch zijn klanten die zowel AEM Assets als AEM Sites gebruiken. In dergelijke scenario&#39;s kunt u een standaardintegratie instellen tussen uw AEM-auteurknooppunt en Adobe Launch en vervolgens uw Sites-instantie koppelen aan de Adobe Launch-eigenschap. Daarna, zal om het even welke Dynamische component van Media WCM die aan een pagina van Plaatsen wordt toegevoegd gegevens en gebeurtenissen van kijkers volgen.

Zie [Informatie over het bijhouden van dynamische mediasviewers in AEM-sites](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersinAEMSites).

Een tweede gebruiksgeval dat de integratie steunt zijn die klanten die slechts de Middelen van AEM, of Dynamische Klassiek van Media gebruiken. In dergelijke gevallen ontvangt u de insluitcode voor uw viewer en voegt u deze toe aan de websitepagina. Vervolgens haalt u de URL voor de productie van de bibliotheek bij Adobe Launch op en voegt u deze handmatig toe aan de code van de webpagina.

Zie [Informatie over het bijhouden van Dynamic Media-viewers met gebruik van ingesloten code](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersusingEmbedcode).

## Hoe gegevens en gebeurtenis volgen werkt in de integratie {#how-data-and-event-tracking-works-in-the-integration}

De integratie maakt gebruik van twee afzonderlijke en onafhankelijke typen van Dynamic Media Viewers die worden bijgehouden: *Adobe Analytics* en *Adobe Analytics for Audio and Video*.

### Informatie over reeksspatiëring met Adobe Analytics {#about-tracking-using-adobe-analytics}

Met Adobe Analytics kunt u handelingen bijhouden die door de eindgebruiker worden uitgevoerd wanneer deze met Dynamic Media Viewers op uw website werkt. Met Adobe Analytics kunt u ook viewerspecifieke gegevens bijhouden. U kunt bijvoorbeeld de laadgebeurtenissen van de weergave bijhouden en opnemen, samen met de naam van het element, eventuele zoomacties die zijn uitgevoerd, handelingen voor het afspelen van video enzovoort.

In Adobe Launch werken de concepten *Data Elements* en *Rules* samen om het bijhouden van Adobe-analysemogelijkheden in te schakelen.

#### Over gegevenselementen in Adobe Launch {#about-data-elements-in-adobe-launch}

Een gegevenselement in Adobe Launch is een benoemde eigenschap waarvan de waarde statisch is gedefinieerd of dynamisch is berekend op basis van de status van een webpagina of gegevens van Dynamic Media Viewers.

Welke opties beschikbaar zijn voor een definitie van een gegevenselement, is afhankelijk van de lijst met extensies die zijn geïnstalleerd in de Adobe-starteigenschap. De &quot;Core&quot;uitbreiding is vooraf geïnstalleerd en beschikbaar uit de doos in om het even welke configuratie. Met deze extensie &quot;Core&quot; kunt u een gegevenselement definiëren dat afkomstig is van cookie, JavaScript-code, queryreeks en vele andere bronnen.

Voor het bijhouden van Adobe Analytics moeten verschillende extra extensies worden geïnstalleerd, zoals wordt beschreven in [Installatie en installatie van extensies](#installing-and-setup-of-extensions). Met de extensie Dynamic Media Viewers kunt u een gegevenselement definiëren dat een argument is van de gebeurtenis Dynamic Viewer. Het is bijvoorbeeld mogelijk te verwijzen naar het viewertype, of de naam van het element die tijdens het laden door de viewer wordt gemeld, het zoomniveau dat wordt gemeld wanneer de eindgebruiker zoomt en nog veel meer.

Met de extensie Dynamic Media Viewer worden de waarden van de Data Elements automatisch bijgewerkt.

Nadat u het hebt bepaald, kan een Element van Gegevens in andere plaatsen van de UI van de Lancering van Adobe worden gebruikt, gebruikend de plukker van het Element van Gegevens widget. In het bijzonder wordt in de regel naar gegevenselementen die zijn gedefinieerd voor het bijhouden van Dynamic Media Viewers verwezen door Handeling voor variabelen instellen van de extensie Adobe Analytics (zie hieronder).

Zie [Gegevenselementen](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/data-elements.html) in de Gids van de Gebruiker van de Lancering van het Platform van de Ervaring om meer te leren.

#### Informatie over regels in Adobe Launch {#about-rules-in-adobe-launch}

Een regel in de Lancering van Adobe is een agnostische configuratie die drie gebieden bepaalt die omhoog een regel maken: *Gebeurtenissen*, *Voorwaarden* en *Acties*:

* *Gebeurtenissen* (als) geven aan wanneer Adobe Launch een regel moet activeren.
* *Voorwaarden* (als) geven aan welke aanvullende beperkingen Adobe Launch moet toestaan of weigeren wanneer een regel wordt geactiveerd.
* *Handelingen* (vervolgens) geven aan wat Adobe Launch moet doen wanneer een regel wordt geactiveerd.

Welke opties beschikbaar zijn in de sectie Gebeurtenissen, Voorwaarden en Handelingen, is afhankelijk van de extensies die zijn geïnstalleerd in de Adobe-starteigenschap. De *Core* -extensie is vooraf geïnstalleerd en is in elke configuratie offline beschikbaar. De extensie biedt verschillende opties voor gebeurtenissen, zoals standaardacties op browserniveau, zoals focuswijziging, toetsdrukken, formulierverzendingen enzovoort. Het bevat ook opties voor Voorwaarden, zoals cookiewaarde, browsertype en meer. Voor Acties is alleen de optie Aangepaste code beschikbaar.

Voor het bijhouden van Adobe-analyses moeten verschillende extra extensies worden geïnstalleerd, zoals wordt beschreven in [Installatie en installatie van extensies](#installing-and-setup-of-extensions). Specifiek:

* De extensie Dynamic Media Viewers breidt de lijst met ondersteunde gebeurtenissen uit tot gebeurtenissen die specifiek zijn voor dynamische mediasviewers, zoals het laden van de viewer, het wisselen van elementen, inzoomen en het afspelen van video.
* De extensie Adobe Analytics breidt de lijst met ondersteunde handelingen uit met twee handelingen die vereist zijn voor het verzenden van gegevens naar trackingservers: *Stel variabelen* in en *verzend baken*.

Als u dynamische mediasviewers wilt bijhouden, kunt u een van de volgende typen gebruiken:

* Gebeurtenissen van de extensie Dynamic Media Viewers, Core-extensie of een andere extensie.
* Voorwaarden in de definitie van de regel. Of u kunt het gebied met voorwaarden leeg laten.

In de sectie van Acties, wordt het vereist dat u een *Vastgestelde actie van Variabelen* hebt. Deze actie vertelt Adobe Analytics hoe te om het volgen variabelen met gegevens te bevolken. Tegelijkertijd verzendt de actie Variabelen ** instellen niets naar de volgende server.

De *Vastgestelde actie van Variabelen* moet door een *Send actie* van het Baken worden gevolgd. De *Send actie van het Band* verzendt eigenlijk gegevens naar de analytische volgende server. Beide acties, *Vastgestelde Variabelen* en *Send Beacon*, komen van de uitbreiding van de Analyse van Adobe.

Zie [Regels](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/rules.html) in de Gids van de Gebruiker van de Lancering van het Platform van de Ervaring om meer te leren.

#### Voorbeeldconfiguratie {#sample-configuration}

In de volgende voorbeeldconfiguratie in Adobe Launch ziet u hoe u een elementnaam kunt bijhouden tijdens het laden van de viewer.

1. Definieer op het tabblad **[!UICONTROL Gegevenselementen]** een gegevenselement `AssetName` dat verwijst naar `asset` de parameter van de `LOAD` gebeurtenis vanuit de extensie Dynamische mediaquamenten.

   ![image2019-11](assets/image2019-11.png)

1. Definieer op het tabblad **[!UICONTROL Regels]** een regel *TrackAssetOnLoad*.

   In deze regel gebruikt het veld **[!UICONTROL Event]** de gebeurtenis **[!UICONTROL LOAD]** van de extensie Dynamic Media Viewers.

   ![image2019-22](assets/image2019-22.png)

1. De configuratie Handeling heeft twee actietypen van de extensie Adobe Analytics:

   *Stel Variabelen* in, die een door u gekozen analytische variabele toewijzen aan de waarde van `AssetName` Gegevenselement.

   *Stuur Beacon*, die trackinggegevens naar Adobe Analytics verzendt.

   ![image2019-3](assets/image2019-3.png)

1. De resulterende regelconfiguratie ziet er als volgt uit:

   ![image2019-4](assets/image2019-4.png)

### Informatie over Adobe Analytics voor audio en video {#about-adobe-analytics-for-audio-and-video}

Als een Experience Cloud-account is geabonneerd op Adobe Analytics voor Audio en Video, is het voldoende om het bijhouden van video in te schakelen in de extensie-instellingen voor *Dynamic Media Viewers* . Videomeetgegevens zijn beschikbaar in Adobe Analytics. Het bijhouden van video&#39;s is afhankelijk van de aanwezigheid van Adobe Media Analytics voor de extensie Audio en Video.

Zie [Installatie en installatie van extensies](#installing-and-setup-of-extensions).

De ondersteuning voor het bijhouden van video&#39;s is momenteel beperkt tot het bijhouden van de &#39;kern-afspeelfunctie&#39;, zoals wordt beschreven in [Overzicht](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html)van bijhouden. Met name QoS, Advertenties, Hoofdstuk/Segmenten, of het volgen van Fouten wordt niet gesteund.

## De extensie Dynamische mediaverviewers gebruiken {#using-the-dynamic-media-viewers-extension}

Zoals vermeld in de [Gebruiksscenario&#39;s voor de integratie](#use%20cases%20for%20the%20integration), is het mogelijk om Dynamic Media-viewers bij te houden met de nieuwe Adobe Launch-integratie in AEM-sites en door insluitcode te gebruiken.

### Dynamische mediasviewers bijhouden in AEM-sites {#tracking-dynamic-media-viewers-in-aem-sites}

Om de Dynamische kijkers van Media in Plaatsen te volgen AEM, moeten alle stappen die onder het [Vormen van alle integratiestukken](#configuring-all-the-integration-pieces) worden vermeld worden uitgevoerd. U moet met name de IMS-configuratie en de Adobe Launch Cloud Configuration maken.

Na de correcte configuratie, om het even welke Dynamische kijker van Media die u aan een pagina van Plaatsen toevoegt, gebruikend een component WCM die door Dynamische Media wordt gesteund, volgt automatisch gegevens aan de Analytics van Adobe, of Analytics van Adobe voor Video, of allebei.

Zie Dynamische media-elementen [toevoegen aan pagina&#39;s met Adobe-sites](https://helpx.adobe.com/experience-manager/6-5/help/assets/adding-dynamic-media-assets-to-pages.html).

### Dynamische mediasviewers bijhouden met gebruik van ingesloten code {#tracking-dynamic-media-viewers-using-embed-code}

Klanten die geen gebruik maken van AEM-sites of die geen gebruik maken van Dynamic Media-viewers voor webpagina&#39;s buiten AEM-sites, of beide, kunnen nog steeds de Adobe Launch-integratie gebruiken.

U moet de configuratiestappen van de secties [Adobe Analytics configureren](#configuringadobeanalytics) en [Adobe Launch configureren](#configuringadobelaunch) voltooien. Aan AEM gerelateerde configuratiestappen zijn echter niet nodig.

Na de juiste configuratie kunt u ondersteuning voor het starten van Adobe toevoegen aan een webpagina met een Dynamic Media-viewer.

Zie [De insluitcode](https://docs.adobe.com/content/help/en/launch/using/implement/configure/implement-the-launch-install-code.html) starten toevoegen voor meer informatie over het gebruik van de insluitcode van de Adobe-bibliotheek.

Zie De video- of afbeeldingsviewer [insluiten op een webpagina](https://helpx.adobe.com/experience-manager/6-5/help/assets/embed-code.html) voor meer informatie over het gebruik van de insluitcodefunctie van AEM Dynamic Media.

**Dynamische mediaviewers volgen met gebruik van ingesloten code**:

1. Zorg dat een webpagina gereed is voor het insluiten van een Dynamic Media-viewer.
1. Vraag de insluitcode voor de Adobe-opstartenbibliotheek aan door u eerst aan te melden bij Adobe Launch (zie Adobe [Launch](#configuringadobelaunch)configureren).
1. Klik op **[!UICONTROL Eigenschap]** en vervolgens op het tabblad **[!UICONTROL Omgevingen]** .
1. Ophalen van het milieuniveau dat relevant is voor de omgeving van de webpagina. Klik vervolgens in de kolom **[!UICONTROL Installeren]** op het vakpictogram.
1. **[!UICONTROL Kopieer in het dialoogvenster Installatie-instructies]** voor web de volledige insluitcode van de Adobe Launch-bibliotheek en de omringende `<script/>` tags.

## Referentiegids voor de extensie Dynamic Media Viewers {#reference-guide-for-the-dynamic-media-viewers-extension}

### Over de configuratie van Dynamic Media Viewers {#about-the-dynamic-media-viewers-configuration}

De extensie Dynamic Media Viewer wordt automatisch geïntegreerd met de Adobe Launch-bibliotheek als aan alle onderstaande voorwaarden wordt voldaan:

* Adobe Launch library global object ( `_satellite`) is aanwezig op de pagina.
* De extensiefunctie Dynamische media Viewers `_dmviewers_v001()` is ingeschakeld `_satellite`.

* `config2=` Er is geen viewerparameter opgegeven, wat betekent dat de viewer geen gebruik maakt van verouderde analytische integratie.

Bovendien is er een optie om Adobe Launch-integratie expliciet uit te schakelen in de viewer door `launch=0` parameter op te geven in de configuratie van de viewer. De standaardwaarde van deze parameter is `1`.

### De extensie Dynamic Media Viewers configureren {#configuring-the-dynamic-media-viewers-extension}

De enige configuratieoptie voor de extensie Dynamic Media Viewers is Adobe Media Analytics **[!UICONTROL inschakelen voor audio en video]**.

Wanneer u deze optie inschakelt (inschakelen of inschakelen) en als Adobe Media Analytics for Audio and Video is geïnstalleerd en correct is geconfigureerd, worden meetgegevens voor het afspelen van video verzonden naar de Adobe Analytics for Audio and Video-oplossing. Als u deze optie uitschakelt, wordt het bijhouden van video uitgeschakeld.

Als u deze optie inschakelt *zonder* dat Adobe Media Analytics for Audio and Video-extensie is geïnstalleerd, heeft deze optie geen effect.

![image2019-7-22_12-4-23](assets/image2019-7-22_12-4-23.png)

### Informatie over gegevenselementen in de extensie Dynamische media-viewers {#about-data-elements-in-the-dynamic-media-viewers-extension}

The only Data Element type that the Dynamic Media Viewers extension provides is **[!UICONTROL Viewer Event]** from the **[!UICONTROL Data Element Type]** drop-down list.

Als deze optie is geselecteerd, maakt de Data Element-editor een formulier met twee velden:

* **[!UICONTROL Het gegevenstype]** van een DM-viewer-gebeurtenis - een vervolgkeuzelijst die alle viewergebeurtenissen identificeert die door de extensie Dynamic Media Viewers worden ondersteund en die argumenten bevatten, plus een speciaal **[!UICONTROL COMMON]** -item. A **[!UICONTROL COMMON]** item represents a list of event parameters that are common to all type of events sent by the viewers.
* **[!UICONTROL Parameter]** bijhouden: een argument van de geselecteerde gebeurtenis van de Dynamic Media-viewer.

![image2019-7-22_12-5-46](assets/image2019-7-22_12-5-46.png)

Zie de naslaggids [voor](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_s7_aem_asset_viewers.html) Dynamic Media Viewers voor de lijst met ondersteunde gebeurtenissen per viewertype. Ga naar de specifieke viewersectie en klik vervolgens op Ondersteuning voor de sectie Adobe Analytics bijhouden. Op dit moment worden in de naslaggids voor dynamische media-viewers geen gebeurtenisargumenten vastgelegd.

Laten we nu eens kijken naar de levenscyclus van het *gegevenselement* van Dynamic Media Viewers. De waarde van een dergelijk gegevenselement wordt gevuld nadat de bijbehorende dynamische mediaviewer-gebeurtenis op de pagina plaatsvindt. Als het gegevenselement bijvoorbeeld naar de gebeurtenis **[!UICONTROL LOAD]** en het argument &#39;asset&#39; verwijst, ontvangt de waarde van dat gegevenselement geldige gegevens nadat de viewer de gebeurtenis LOAD voor de eerste keer uitvoert. Als het gegevenselement naar de **[!UICONTROL ZOOM]** -gebeurtenis en het bijbehorende &quot;scale&quot;-argument verwijst, blijft de waarde van dat gegevenselement leeg totdat de gebruiker een **[!UICONTROL ZOOM]** -gebeurtenis voor het eerst verzendt.

Op dezelfde manier worden de waarden van data-elementen automatisch bijgewerkt wanneer de viewer een overeenkomstige gebeurtenis op de pagina verzendt. De waarde-update gebeurt zelfs als de specifieke gebeurtenis niet in de regelconfiguratie is opgegeven. For example, if Data Element **[!UICONTROL ZoomScale]** is defined for &quot;scale&quot; parameter of the ZOOM event, but the only rule present in the Rule configuration is triggered by the **[!UICONTROL LOAD]** event, the value of **[!UICONTROL ZoomScale]** is still updated every time a user runs zoom inside the viewer.

Elke viewer voor dynamische media heeft een unieke id op de webpagina. Het data-element houdt de waarde zelf bij en de viewer die de waarde heeft ingevuld. This means that if there are several viewers on the same page, and there is an **[!UICONTROL AssetName]** Data Element that points to the **[!UICONTROL LOAD]** event and its &quot;asset&quot; argument, the **[!UICONTROL AssetName]** Data Element maintains a collection of asset names that are associated with each viewer loaded on the page.

De exacte waarde die door het gegevenselement wordt geretourneerd, is afhankelijk van de context. Als het gegevenselement in een Regel wordt gevraagd die door een Dynamische de kijkergebeurtenis van Media werd teweeggebracht, dan is de waarde van het Element van Gegevens teruggekeerd voor de kijker die de Regel in werking stelde. En als het gegevenselement wordt aangevraagd in een regel die is geactiveerd door een gebeurtenis van een andere Adobe-extensie voor starten, is de waarde van het gegevenselement de waarde van de viewer die als laatste het gegevenselement heeft bijgewerkt.

**Bekijk de volgende voorbeeldset-up**:

* Een webpagina met twee Dynamic Media Zoom-viewers; wij zullen naar hen als *kijker1* en *kijker2* verwijzen.

* **[!UICONTROL Het gegevenselement ZoomScale]** wijst naar de **[!UICONTROL ZOOM]** -gebeurtenis en het bijbehorende &quot;scale&quot;-argument.
* **[!UICONTROL Regel trackPan]** met het volgende:

   * Gebruikt de Dynamic Media Viewer **[!UICONTROL PAN]** -gebeurtenis als trigger.
   * Verzendt de waarde van het gegevenselement **[!UICONTROL ZoomScale]** naar Adobe Analytics.

* 
   * **[!UICONTROL Regel trackKey]** met het volgende:

   * Gebruikt de toetsdrukgebeurtenis van de Core Adobe Launch-extensie als een trigger.
   * Verzendt de waarde van het gegevenselement **[!UICONTROL ZoomScale]** naar Adobe Analytics.

Nu, veronderstel de eindgebruiker de Web-pagina met de twee kijkers laadt. In *viewer1* zoomen ze in op een schaal van 50%; vervolgens zoomen ze in *viewer2* in op een schaal van 25%. In *viewer1* pannen ze de afbeelding rond en drukken ze ten slotte op een toets op het toetsenbord.

De activiteit van de eindgebruiker resulteert in de volgende twee het volgen vraag wordt gemaakt aan de Analytics van Adobe:

* De eerste vraag komt voor omdat de Regel **[!UICONTROL TrackPan]** wordt teweeggebracht wanneer de gebruiker in *viewer1* pant. Die vraag verzendt 50% als waarde van het Element van Gegevens **[!UICONTROL ZoomScale]** omdat het Element van Gegevens zal weten dat de Regel door *viewer1* wordt teweeggebracht en de overeenkomstige schaalwaarde haalt;
* De tweede vraag komt voor omdat de Regel **[!UICONTROL TrackKey]** wordt teweeggebracht wanneer de gebruiker op een sleutel op het toetsenbord duwde. Die vraag verzendt 25% als waarde van het Element van Gegevens **[!UICONTROL ZoomScale]** omdat de Regel niet door de kijker werd teweeggebracht. Als dusdanig, keert het Element van Gegevens de meest bijgewerkte waarde terug.

Het voorbeeld hierboven heeft ook invloed op de levensduur van de waarde voor het gegevenselement. De waarde van het gegevenselement dat door de Dynamic Media Viewer wordt beheerd, wordt opgeslagen in de Adobe Launch-bibliotheekcode, zelfs nadat de viewer zelf op de webpagina is verwijderd. Dit betekent dat als er een Regel is die door een niet-Dynamische uitbreiding van de Kijker van Media wordt teweeggebracht en verwijzingen zoals het Element van Gegevens, het Element van Gegevens de laatste bekende waarde terugkeert, zelfs als de kijker niet meer op de Web-pagina aanwezig is.

In elk geval worden de waarden van gegevenselementen die door Dynamic Media Viewers worden aangestuurd, niet opgeslagen op de lokale opslag of op de server. in plaats daarvan worden ze alleen in de Adobe Launch-bibliotheek op de client bewaard. Waarden van een dergelijk gegevenselement verdwijnen als de webpagina opnieuw wordt geladen.

Over het algemeen biedt de editor voor gegevenselementen ondersteuning voor de [opslagduur](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/data-elements.html#create-a-data-element). Gegevenselementen die de extensie Dynamische mediumviewers gebruiken, ondersteunen echter alleen de opslagduuroptie **[!UICONTROL Geen]**. Het instellen van een andere waarde is mogelijk in de gebruikersinterface, maar het gedrag Gegevenselement is in dit geval niet gedefinieerd. De extensie beheert de waarde van het gegevenselement op zichzelf: het gegevenselement dat de waarde van het gebeurtenisargument van de viewer tijdens de volledige de levenscyclus van de kijker handhaaft.

### Over Regels in de extensie Dynamische mediasviewers {#about-rules-in-the-dynamic-media-viewers-extension}

In de redacteur van de Regel, voegt de uitbreiding nieuwe configuratieopties voor de redacteur van Gebeurtenissen toe. Ook biedt de toepassing een optie om handmatig te verwijzen naar gebeurtenisparameters in de Action Editor als een kortzichtige optie in plaats van vooraf geconfigureerde gegevenselementen te gebruiken.

#### Informatie over de Events-editor {#about-the-events-editor}

In the Event editor, the Dynamic Media Viewers extension adds a new **[!UICONTROL Event Type]** called **[!UICONTROL Viewer Event]**.

Als deze optie is geselecteerd, rendert de gebeurteniseditor de vervolgkeuzelijst **[!UICONTROL Dynamic Media Viewer-gebeurtenissen]** en worden hierin alle beschikbare gebeurtenissen weergegeven die door Dynamic Media-viewers worden ondersteund.

![image2019-8-2_15-13-1](assets/image2019-8-2_15-13-1.png)

#### De Editor voor handelingen {#about-the-actions-editor}

Met de extensie Dynamische media-viewers kunt u gebeurtenisparameters van Dynamic Media-viewers gebruiken voor het toewijzen van variabelen aan analytische variabelen in de editor Variabelen instellen van de extensie Adobe Analytics.

De eenvoudigste methode om dat te doen is het volgende twee-stap proces te voltooien:

* Definieer eerst een of meer gegevenselementen, waarbij elk gegevenselement een parameter van een dynamische Media Viewer-gebeurtenis vertegenwoordigt.
* Tot slot klikt u in de editor Variabelen instellen van de extensie Adobe Analytics op het pictogram voor de kiezer voor gegevenselement (drie gestapelde schijven) om het dialoogvenster Gegevenselement selecteren te openen en selecteert u vervolgens een gegevenselement in het dialoogvenster.

![image2019-7-10_20-41-52](assets/image2019-7-10_20-41-52.png)

Het is echter mogelijk om een alternatieve manier te gebruiken en het maken van data-elementen te omzeilen. You can directly reference an argument from a Dynamic Media Viewer event by entering the fully qualified name of the event argument in the **[!UICONTROL value]** input field of the Analytics variable assignment, surrounded by percent (%) signs. Bijvoorbeeld,

`%event.detail.dm.LOAD.asset%`

![image2019-7-12_19-2-35](assets/image2019-7-12_19-2-35.png)

Er is een belangrijk verschil tussen het gebruik van Data Elements en de verwijzing naar directe-gebeurtenisargumenten. Voor het Element van Gegevens, maakt het niet uit welke gebeurtenis de Vastgestelde actie van Variabelen teweegbrengt, de gebeurtenis die de Regel teweegbrengt kan niet met Dynamische Kijker (als een muisklik op de Web-pagina van de uitbreiding van de Kern) niet van belang zijn. Maar wanneer het gebruiken van een directe argumentverwijzing is het belangrijk om ervoor te zorgen dat de gebeurtenis die de regel teweegbrengt aan het gebeurtenisargument beantwoordt dat het verwijst.

For example, referencing `%event.detail.dm.LOAD.asset%` returns the correct asset name if the Rule is triggered by the **[!UICONTROL LOAD]** event of the Dynamic Media Viewer extension. Er wordt echter een lege waarde voor elke andere gebeurtenis geretourneerd.

In de volgende tabel worden de gebeurtenissen van de Dynamic Media Viewer en de ondersteunde argumenten weergegeven:

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
   <td><code>BANNER</code> </td>
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

Als u dit nog niet hebt gedaan, raadt Adobe u aan alle documentatie voorafgaand aan deze sectie grondig te controleren, zodat u de volledige integratie begrijpt.

In deze sectie worden de configuratiestappen beschreven die nodig zijn om Dynamic Media-viewers te integreren met Adobe Analytics en Adobe Analytics voor Audio en Video. Hoewel het gebruik van de extensie Dynamic Media Viewers voor andere doeleinden in Adobe Launch mogelijk is, worden dergelijke scenario&#39;s niet in deze documentatie besproken.

U configureert de integratie in de volgende Adobe-producten:

* Adobe Analytics - u zult het volgen variabelen en rapporten vormen.
* Adobe Launch - u definieert een eigenschap, een of meer regels en een of meer gegevenselementen om het bijhouden van de viewer in te schakelen.

Bovendien, als deze integratieoplossing met Plaatsen AEM wordt gebruikt, moet de volgende configuratie ook worden gedaan:

* Adobe I/O-console - integratie is gemaakt voor het starten van Adobe.
* AEM-auteurknooppunt - IMS-configuratie en Adobe Launch-wolkenconfiguratie.

Als onderdeel van de configuratie moet u toegang hebben tot een bedrijf in Adobe Experience Cloud dat Adobe Analytics en Adobe Launch al heeft ingeschakeld.

## Adobe Analytics configureren voor integratie {#configuring-adobe-analytics-for-the-integration}

Nadat u Adobe Analytics hebt geconfigureerd, wordt het volgende voor de integratie ingesteld:

* Er is een rapportsuite geïnstalleerd en geselecteerd.
* De Variabelen van de Analyse zijn beschikbaar om het volgen gegevens te ontvangen.
* Rapporten zijn beschikbaar voor het weergeven van verzamelde gegevens in Adobe Analytics.

Zie ook [Analytics Implementation Guide](https://docs.adobe.com/content/help/en/analytics/implementation/home.html).

**U configureert als volgt Adobe Analytics voor de integratie**:

1. Start Adobe Analytics via de [startpagina](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/)van Experience Cloud. Klik in de menubalk op het pictogram Oplossingen (drie bij drie punten) in de rechterbovenhoek van de pagina en klik vervolgens op **[!UICONTROL Analytics]**.

   ![2019-07-22_18-08-47](assets/2019-07-22_18-08-47.png)

   U selecteert nu een rapportsuite.

### Een rapportsuite selecteren {#selecting-a-report-suite}

1. Near the upper-right corner of the Adobe Analytics page, to the right of the **[!UICONTROL Search Reports]** field, select the correct report suite from the drop-down list. Als er meerdere rapportsuites beschikbaar zijn en u niet zeker weet welke suite u moet gebruiken, neemt u contact op met uw Adobe Analytics-beheerder. Deze beheerder kan u helpen bij het selecteren van de rapportsuite die moet worden gebruikt.

   In de onderstaande afbeelding heeft een gebruiker een rapportsuite met de naam *DynamicMediaViewersExtensionDoc* gemaakt en deze geselecteerd in de vervolgkeuzelijst. De naam van de rapportsuite is alleen ter illustratie; de naam van de rapportsuite die u uiteindelijk selecteert, verschilt.

   Als er geen rapportsuite beschikbaar is, moet u of de beheerder van Adobe Analytics er een maken voordat u verder kunt gaan met de configuratie.

   Zie [Rapporten en de Reeksen](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-reports-report-suites.html) van het Rapport en [creeer een rapportreeks](https://docs.adobe.com/content/help/en/analytics/admin/admin-console/create-report-suite.html).

   In Adobe Analytics worden rapportsuites beheerd onder **[!UICONTROL Beheer > Rapportagesuites]**.

   ![2019-07-22_18-09-49](assets/2019-07-22_18-09-49.png)

   U stelt nu Adobe Analytics-variabelen in.

### Adobe Analytics-variabelen instellen {#setting-up-adobe-analytics-variables}

1. U geeft nu een of meer Adobe Analytics-variabelen aan die u wilt gebruiken om het gedrag van Dynamic Media Viewers op de webpagina bij te houden.

   U kunt elk type variabele gebruiken dat door Adobe Analytics wordt ondersteund. Het besluit over het veranderlijke type (zoals [steunen]van het Verkeer van de Douane, Omzetting [eVar]) zou door specifieke behoeften van u implementatie Analytics moeten worden gedreven.

   Zie [Overzicht van props en eVars](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/traffic-props-evars/props-evars.html).

   In het kader van deze documentatie wordt alleen een variabele Custom Traffic (props) gebruikt, omdat deze binnen een paar minuten nadat een handeling op een webpagina heeft plaatsgevonden, beschikbaar komt in een Analytics-rapport.

   Als u een nieuwe variabele Aangepast verkeer wilt inschakelen, klikt u in Adobe Analytics op de werkbalk op **[!UICONTROL Beheer > Suites]** rapporteren.

1. Selecteer op de pagina **[!UICONTROL Report Suite Manager]** het juiste rapport en klik vervolgens op de werkbalk op Instellingen **[!UICONTROL bewerken > Verkeer > Verkeersvariabelen]**.
1. Daar, neem ongebruikte variabele op, geef het een beschrijvende naam (activa van de **[!UICONTROL Kijker (pro 30)]**) en verander combodoos in &quot;Toegelaten&quot;in de Toegelaten kolom.

   De volgende schermafbeelding is een voorbeeld van een variabele van het Verkeer van de Douane ( **[!UICONTROL prop30]**) voor het volgen van een activanaam die door de kijker wordt gebruikt:

   ![image2019-6-26_23-6-59](assets/image2019-6-26_23-6-59.png)

1. Klik onder aan de lijst met variabelen op **[!UICONTROL Opslaan]**.

### Een rapport instellen {#setting-up-a-report}

1. Over het algemeen wordt het instellen van een rapport in Adobe Analytics gestuurd door specifieke projectbehoeften. Als dusdanig, is de gedetailleerde rapportopstelling voorbij het werkingsgebied voor deze integratie.

   Het is echter voldoende om te weten dat de rapporten Aangepast verkeer automatisch beschikbaar worden in Adobe Analytics nadat u de variabelen Aangepast verkeer hebt ingesteld in **[Adobe Analytics-variabelen](#setting-up-adobe-analytics-variables)**instellen.

   Het rapport voor de elementvariabele **[!UICONTROL Viewer (prop 30)]** is bijvoorbeeld beschikbaar in het menu Rapporten onder **[!UICONTROL Aangepast verkeer > Aangepast verkeer 21-30 > Viewer-element (prop 30)]**.

   Visiting this report right after **[!UICONTROL Viewer asset (prop 30)]** creation shows no data; that is expected at this point in the integration.

   ![image2019-6-26_23-12-49](assets/image2019-6-26_23-12-49.png)

## Adobe Launch configureren voor integratie {#configuring-adobe-launch-for-the-integration}

Nadat u Adobe Launch hebt geconfigureerd, wordt het volgende ingesteld voor de integratie:

* Het creëren van een nieuw Bezit om al uw configuraties samen te houden.
* De installatie en installatie van extensies. De client-side code van alle extensies die in de eigenschap zijn geïnstalleerd, wordt samen gecompileerd in een bibliotheek. Deze bibliotheek wordt later door de webpagina gebruikt.
* Configuratie van gegevenselementen en regels. Deze configuratie bepaalt welke gegevens van de Dynamische kijkers van Media, wanneer om de volgende logica teweeg te brengen, en waar te om de gegevens van de kijker in de Analytics van Adobe te verzenden.
* Publiceren van de bibliotheek.

**Adobe Launch configureren voor integratie**:

1. Start Adobe Launch via de [startpagina](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/)van Experience Cloud. Klik in de menubalk op het pictogram Oplossingen (drie bij drie punten) rechtsboven op de pagina en klik vervolgens op **[!UICONTROL Starten]**.

   U kunt Adobe Launch ook rechtstreeks [](https://launch.adobe.com/)openen.

   ![image2019-7-8_15-38-44](assets/image2019-7-8_15-38-44.png)

### Een eigenschap maken in Adobe Launch {#creating-a-property-in-adobe-launch}

Een eigenschap in Adobe Launch is een benoemde configuratie die al uw instellingen bij elkaar houdt. Er wordt een bibliotheek met de configuratie-instellingen gegenereerd en gepubliceerd op verschillende milieuniveaus (ontwikkeling, staging en productie).

Zie ook [Een eigenschap](https://docs.adobe.com/content/help/en/launch/using/implement/configure/create-a-property.html)maken.

1. Klik in Adobe Launch op **[!UICONTROL New Property]**.
1. In the **[!UICONTROL Create Property]** dialog box, in the **[!UICONTROL Name]** field, type a descriptive name, such as the title of your website. Bijvoorbeeld, `DynamicMediaViewersProp.`
1. Voer in het veld **[!UICONTROL Domeinen]** het domein van uw website in.
1. Schakel in de vervolgkeuzelijst **[!UICONTROL Geavanceerde opties]** de optie **[!UICONTROL Configureren in voor de ontwikkeling van extensies (kan later niet worden gewijzigd)]** voor het geval dat de extensie die u wilt gebruiken, in dit geval nog niet wordt vrijgegeven voor *Dynamic Media Viewers*.

   ![image2019-7-8_16-3-47](assets/image2019-7-8_16-3-47.png)

1. Click **[!UICONTROL Save]**.

   Klik op de nieuwe eigenschap en ga vervolgens verder met *Installatie en installatie van extensies*.

### Extensies installeren en instellen {#installing-and-setup-of-extensions}

Alle beschikbare extensies in Adobe Launch worden weergegeven onder **[!UICONTROL Extensies > Catalogus]**.

Klik op **[!UICONTROL Installeren]** om een extensie te installeren. Voer zo nodig een eenmalige extensieconfiguratie uit en klik op **[!UICONTROL Opslaan]**.

Waar nodig moeten de volgende extensies worden geïnstalleerd en geconfigureerd:

* (Vereist) *Experience Cloud ID Service *extension

Geen extra configuratie is nodig, keur voor om het even welke voorgestelde waarden goed. Als u klaar bent, klikt u op **[!UICONTROL Opslaan]**.

Zie [Experience Cloud ID Service Extension](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/id-service-extension/overview.html).

* (Vereist) *Adobe Analytics* -extensie

To configure this extension, you will first need the Report Suite ID found in Adobe Analytics, under **[!UICONTROL Admin > Report Suite]**, under the **[!UICONTROL Report Suite ID]** column header.

(For demonstration purposes only, the Report Suite ID of the **[!UICONTROL DynamicMediaViewersExtensionDoc]** Report Suite will be used in the following screenshots. Deze id is eerder gemaakt en gebruikt in [Een rapportsuite selecteren](#selecting-a-report-suite).)

![image2019-7-8_16-45-34](assets/image2019-7-8_16-45-34.png)

Op de Install pagina van de Uitbreiding, ga identiteitskaart van de Reeks van het Rapport op het gebied van de Suites **[!UICONTROL van het]** Ontwikkelingsrapport, het gebied van de Suites **[!UICONTROL van het Rapport van het]** Staging, en het gebied van de Suites **[!UICONTROL van het]** Productierapport in.

![image2019-7-8_16-47-40](assets/image2019-7-8_16-47-40.png)

*Configureer het volgende item alleen als u videotracering wilt gebruiken:*

Vouw op de pagina Extensie **** installeren de optie **[!UICONTROL Algemeen]** uit en geef vervolgens de trackingserver op. De volgende server volgt de sjabloon `<trackingNamespace>.sc.omtrdc.net`, waarbij `<trackingNamespace>` de informatie wordt verkregen in de e-mail met provisies.

Click **[!UICONTROL Save]**.

Zie [Adobe Analytics Extension](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/analytics-extension/overview.html).

* (facultatief; is alleen vereist als videotracering vereist is) *Adobe Media Analytics voor audio en video* -extensie

Vul het veld Trackingserver in. De trackingserver voor de extensie *Adobe Media Analytics voor Audio en Video* verschilt van de trackingserver die wordt gebruikt voor Adobe Analytics. De sjabloon volgt `<trackingNamespace>.hb.omtrdc.net`de sjabloon, waar `<trackingNamespace>` is de informatie uit de e-mail met provisioning.

Alle andere velden zijn optioneel.

Zie [Adobe Media Analytics for Audio and Video Extension](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/media-analytics-extension/overview.html).

* (Vereist) *Dynamic Media Viewers* -extensie

Schakel Adobe Analytics **[!UICONTROL voor Video]** in om het bijhouden van videoclips in te schakelen (inschakelen).

Op het moment van schrijven is de extensie *Dynamic Media Viewers* alleen beschikbaar als de Adobe Launch-eigenschap is gemaakt voor ontwikkeling.

Zie Een eigenschap [maken in Adobe Launch](#creating-a-property-in-adobe-launch).

Nadat de extensies zijn geïnstalleerd en ingesteld, worden ten minste de volgende vijf extensies (vier extensies als u geen video bijhoudt) weergegeven in het gedeelte Extensies > Geïnstalleerd.

![image2019-7-22_12-7-36](assets/image2019-7-22_12-7-36.png)

### Gegevenselementen en regels instellen {#setting-up-data-elements-and-rules}

In de Lancering van Adobe, creeer de Elementen en de Regels van Gegevens die noodzakelijk zijn voor het volgen van de Dynamische kijkers van Media.

Zie [Hoe gegevens- en gebeurtenistracering werkt in de integratie](#how-data-and-event-tracking-works-in-the-integration) voor een overzicht van het bijhouden van de wijzigingen bij Adobe Launch.

Zie [Voorbeeldconfiguratie](#sample-configuration) voor een voorbeeldconfiguratie in Adobe Launch die laat zien hoe u een elementnaam bij het laden van een viewer kunt bijhouden.

Zie De extensie [Dynamische media-viewers](#configuring-the-dynamic-media-viewers-extension) configureren voor uitgebreide informatie over de mogelijkheden van de extensie.

### Een bibliotheek publiceren {#publishing-a-library}

Als u wijzigingen wilt aanbrengen in de configuratie van Adobe Launch (inclusief de instelling Eigenschappen, Extensies, Regels en Gegevenselementen), moet u dergelijke wijzigingen *publiceren* *.* Publiceren in Adobe Launch wordt uitgevoerd vanaf het tabblad Publiceren onder Eigenschapconfiguratie.

Adobe Launch kan meerdere ontwikkelomgevingen, één testomgeving en één productieomgeving hebben. Standaard wijst Adobe Launch Cloud Configuration in AEM het auteurknooppunt van AEM naar de Stage-omgeving van Adobe Launch en het publicatieknooppunt van AEM naar de Production-omgeving van Adobe Launch. Dit argument houdt in dat met de standaard AEM-instellingen de Adobe Launch-bibliotheek naar de Staging-omgeving moet worden gepubliceerd, zodat deze kan worden gebruikt in de AEM-auteur en vervolgens in de Productieomgeving, zodat deze kan worden gebruikt in AEM-publicatie.

Zie [Omgevingen](https://docs.adobe.com/content/help/en/launch/using/reference/publish/environments.html) voor meer informatie over de milieu&#39;s van de Lancering van Adobe.

Bij het publiceren van een bibliotheek worden de volgende twee stappen uitgevoerd:

* Het toevoegen van en het bouwen van een nieuwe bibliotheek door alle noodzakelijke veranderingen (nieuwe degenen en updates) in de bibliotheek te omvatten.
* De bibliotheek naar boven verplaatsen via de verschillende milieuniveaus (van ontwikkeling tot Staging en Productie)

#### Een nieuwe bibliotheek toevoegen en maken {#adding-and-building-a-new-library}

1. De eerste keer dat u het tabblad Publiceren opent in Adobe Launch, is de bibliotheeklijst leeg.

   Klik in de linkerkolom op **[!UICONTROL Nieuwe bibliotheek]** toevoegen.

   ![image2019-7-15_14-43-17](assets/image2019-7-15_14-43-17.png)

1. Voer op de pagina Nieuwe bibliotheek maken in het veld **[!UICONTROL Naam]** een beschrijvende naam in voor de nieuwe bibliotheek. Bijvoorbeeld,

   *DynamicMediaViewersLib*

   Kies in de vervolgkeuzelijst Milieu het niveau Milieu. In eerste instantie is alleen het ontwikkelingsniveau beschikbaar voor selectie. Klik links onder aan de pagina op Alle gewijzigde bronnen **[!UICONTROL toevoegen]**.

   ![image2019-7-15_14-49-41](assets/image2019-7-15_14-49-41.png)

1. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Opslaan en samenstellen voor ontwikkeling]**.

   Over enkele minuten wordt de bibliotheek gemaakt en klaar voor gebruik.

   ![image2019-7-15_15-3-34](assets/image2019-7-15_15-3-34.png)

   >[!NOTE]
   >
   >The next time you make changes to your Adobe Launch configuration, go to the **[!UICONTROL Publishing]** tab under the **[!UICONTROL Property]** configuration, then click your previously created library.
   >
   >
   >Klik in het publicatiescherm van de bibliotheek op Alle gewijzigde bronnen **** toevoegen en klik vervolgens op **[!UICONTROL Opslaan en bouwen voor ontwikkeling]**.

#### Een bibliotheek omhoog verplaatsen via het omgevingsniveau {#moving-a-library-up-through-environment-levels}

1. Nadat een nieuwe bibliotheek wordt toegevoegd, wordt het aanvankelijk gevestigd in het milieu van de Ontwikkeling. Klik in het vervolgkeuzemenu van de bibliotheek op **[!UICONTROL Verzenden voor goedkeuring]** om de titel naar het niveau van de testomgeving (dat overeenkomt met de kolom Verzenden) te verplaatsen.

   ![image2019-7-15_15-52-37](assets/image2019-7-15_15-52-37.png)

1. Klik in het bevestigingsdialoogvenster op **[!UICONTROL Verzenden]**.

   Klik in het keuzemenu van de bibliotheek op **[!UICONTROL Opbouwen voor Staging]** nadat de bibliotheek naar de kolom Verzenden is gegaan.

   ![image2019-7-15_15-54-37](assets/image2019-7-15_15-54-37.png)

1. Volg een vergelijkbaar proces om de bibliotheek van de Staging-omgeving naar de productieomgeving te verplaatsen (de kolom Published).

   Klik eerst in het keuzemenu op **[!UICONTROL Goedkeuren voor publiceren]**.

   ![image2019-7-15_16-7-39](assets/image2019-7-15_16-7-39.png)

1. Klik in het keuzemenu op **[!UICONTROL Samenstellen en publiceren naar productie]**.

   ![image2019-7-15_16-8-9](assets/image2019-7-15_16-8-9.png)

   Zie [Publiceren](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html) voor meer informatie over het publicatieproces in Adobe Launch.

## Adobe Experience Manager configureren voor integratie {#configuring-adobe-experience-manager-for-the-integration}

Vereisten:

* AEM voert zowel instanties Auteur als Publiceren uit.
* De auteursknoop van AEM wordt opstelling in Dynamische Media - Scene7 looppas wijze (dynamicmedia_s7)
* Dynamische media WCM-componenten worden ingeschakeld in AEM-sites.

De configuratie AEM bestaat uit de volgende twee belangrijke stappen:

* Configuratie van AEM IMS.
* Configuratie van Adobe Launch Cloud.

### AEM IMS configureren {#configuring-aem-ims}

1. Klik in de auteur van AEM op het pictogram Extra (hamer) en klik vervolgens op **[!UICONTROL Beveiliging > Adobe IMS Configurations]**.

   ![2019-07-25_11-52-58](assets/2019-07-25_11-52-58.png)

1. Klik in de linkerbovenhoek van de Adobe IMC-configuratiepagina op **[!UICONTROL Maken]**.
1. Klik op de pagina Configuratie **[!UICONTROL technische account van]** Adobe IMS in de vervolgkeuzelijst **[!UICONTROL Cloudoplossing]** op **[!UICONTROL Adobe Launch]**.
1. Schakel **[!UICONTROL Nieuw certificaat]** maken in en voer in het tekstveld een betekenisvolle waarde voor het certificaat in. Bijvoorbeeld *AdobeLaunchIMSCert*. Klik op **[!UICONTROL Certificaat]** maken.

   Het volgende Info-bericht wordt weergegeven:

   *Als u een geldig toegangstoken wilt ophalen, moet de openbare sleutel van het nieuwe certificaat worden toegevoegd aan de technische account op Adobe I/O!*.

   Klik op **[!UICONTROL OK]** om het dialoogvenster Info te sluiten.

   ![2019-07-25_12-09-24](assets/2019-07-25_12-09-24.png)

1. Klik op Openbare sleutel **** downloaden om een bestand met een openbare sleutel (*.crt) naar uw lokale systeem te downloaden.

   >[!NOTE]
   >
   >At this point, ***leave open*** the **[!UICONTROL Adobe IMS Technical Account Configuration]** page; ***do not*** close the page and ***do not*** click Next. U keert later in de stappen terug naar deze pagina.

   ![2019-07-25_12-52-24](assets/2019-07-25_12-52-24.png)

1. Navigeer op een nieuw browsertabblad naar de [Adobe I/O-console](https://console.adobe.io/integrations).

1. Klik in de rechterbovenhoek van de pagina Integraties **[!UICONTROL van de]** Adobe I/O-console op **[!UICONTROL Nieuwe integratie]**.
1. Controleer in het dialoogvenster **[!UICONTROL Een nieuwe integratie]** maken of het keuzerondje **[!UICONTROL Toegang tot een API]** is geselecteerd en klik op **[!UICONTROL Doorgaan]**.

   ![2019-07-25_13-04-20](assets/2019-07-25_13-04-20.png)

1. Schakel op de tweede **[!UICONTROL pagina Een nieuwe integratiepagina]** maken het keuzerondje **[!UICONTROL Experience Platform Launch API]** in (inschakelen). In the lower-right corner of the page, click **[!UICONTROL Continue]**.

   ![2019-07-25_13-13-54](assets/2019-07-25_13-13-54.png)

1. Ga als volgt te werk op de derde **[!UICONTROL pagina Een nieuwe integratie]** maken:

   * Voer in het veld **[!UICONTROL Naam]** een beschrijvende naam in. Bijvoorbeeld *DynamicMediaViewersIO*.

   * Voer in het veld **[!UICONTROL Beschrijving]** een beschrijving in voor de integratie.

   * Upload in het gebied **[!UICONTROL Certificaten]** met openbare sleutel het bestand met de openbare sleutel (*.crt) dat u eerder in deze stappen hebt gedownload.

   * Under the **[!UICONTROL Select a role for Experience Platform Launch API]** heading, select **[!UICONTROL Admin]**.

   * Selecteer onder de kop **[!UICONTROL Selecteer een of meer productprofielen voor Experience Platform Launch API]** het productprofiel met de naam **[!UICONTROL Launch - &lt;uw_bedrijf_naam>]**.
   ![2019-07-25_13-49-18](assets/2019-07-25_13-49-18.png)

1. Klik op Integratie **[!UICONTROL maken]**.
1. Klik op de pagina **[!UICONTROL Integratie gemaakt]** op **[!UICONTROL Doorgaan naar integratiegegevens]**.

   ![2019-07-25_14-16-33](assets/2019-07-25_14-16-33.png)

1. Er wordt een pagina met integratiedetails weergegeven, die lijkt op het volgende: ****

   >[!NOTE]
   >
   >***Laat deze pagina met integratiedata open***. You will need various pieces of information from the **[!UICONTROL Overview]** and **[!UICONTROL JWT]** tabs in just a moment.

   ![2019-07-25_14-35-30](assets/2019-07-25_14-35-30.png)

   Pagina met integratiegegevens.

1. Ga terug naar de pagina Configuratie **[!UICONTROL van de technische account van]** Adobe IMS die u eerder hebt geopend. Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Volgende]** om de pagina **[!UICONTROL Account]** te openen in het venster Configuratie **[!UICONTROL technische account van]** Adobe IMS.

   (Als u de pagina per ongeluk eerder hebt gesloten, gaat u terug naar de auteur van AEM en klikt u op **[!UICONTROL Gereedschappen > Beveiliging > Adobe IMS Configurations]**. Klik op **[!UICONTROL Maken]**. Selecteer **[!UICONTROL Adobe Launch in de vervolgkeuzelijst]** Cloud Solution ****. In the **[!UICONTROL Certificate]** drop-down list, select the name of the previously created certificate.)

   ![2019-07-25_20-57-50](assets/2019-07-25_20-57-50.png)

   Configuratie technische account van Adobe IMS - Certificaatpagina.

1. De pagina **[!UICONTROL Account]** heeft vijf velden waarvoor u gegevens van de pagina Integratiegegevens van de vorige stap moet invullen.

   ![2019-07-25_20-42-45](assets/2019-07-25_20-42-45.png)

   Configuratie van de technische account van Adobe IMS - Accountpagina.

1. Vul op de pagina **[!UICONTROL Account]** de volgende velden in:

   * **[!UICONTROL Titel]** - Voer een beschrijvende accounttitel in.
   * **[!UICONTROL De Server]** van de vergunning - terugkeer naar de de detailpagina van de Integratie die u vroeger opende. Klik op het tabblad **[!UICONTROL JWT]** . Kopieer de servernaam, zonder het pad, zoals hieronder gemarkeerd.
   Return to the **[!UICONTROL Account]** page, then paste the name into the respective field.
Bijvoorbeeld, `https://ims-na1.adobelogin.com/`(de naam van de voorbeeldserver is alleen ter illustratie)

   ![2019-07-25_15-01-53](assets/2019-07-25_15-01-53.png)

   Detailpagina voor integratie - tabblad JWT

1. **[!UICONTROL API-sleutel]** - Ga terug naar de pagina met integratiegegevens. Klik op het tabblad **[!UICONTROL Overzicht]** en klik vervolgens rechts van het veld **[!UICONTROL API-sleutel (client-id)]** op **[!UICONTROL Kopiëren]**.

   Return to the **[!UICONTROL Account]** page, then paste the key into the respective ****field.

   ![2019-07-25_14-35-333](assets/2019-07-25_14-35-333.png)

   Pagina met integratiegegevens.

1. **[!UICONTROL Clientgeheim]**- Ga terug naar de pagina met integratiegegevens. Klik op het tabblad **[!UICONTROL Overzicht]** op Client **[!UICONTROL Secret]** ophalen. Rechts van het geheime **[!UICONTROL gebied van de]** Cliënt, klik **[!UICONTROL Exemplaar]**.

   Return to the **[!UICONTROL Account]** page, then paste the key into the respective field.

1. **[!UICONTROL Payload]** - Ga terug naar de pagina met integratiegegevens. Kopieer op het tabblad **[!UICONTROL JWT]** in het veld JWT Payload de gehele JSON-objectcode.

   Return to the **[!UICONTROL Account]** page, then paste the code into the respective field.

   ![2019-07-25_21-59-12](assets/2019-07-25_21-59-12.png)

   Pagina met integratiegegevens - tabblad JWT

   De pagina Account, met alle velden ingevuld, ziet er ongeveer als volgt uit:

   ![2019-07-25_22-08-30](assets/2019-07-25_22-08-30.png)

1. Near the upper-right corner of the **[!UICONTROL Account]** page, click **[!UICONTROL Create]**.

   Als AEM IMS is geconfigureerd, wordt er een nieuwe IMSAcount weergegeven onder **[!UICONTROL Adobe IMS Configurations]**.

   ![image2019-7-15_14-17-54](assets/image2019-7-15_14-17-54.png)

## Adobe Launch Cloud configureren voor integratie {#configuring-adobe-launch-cloud-for-the-integration}

1. Klik in de linkerbovenhoek van de auteur van AEM op het pictogram Extra (hamer) en klik vervolgens op **[!UICONTROL Cloud Services > Adobe Launch Configurations]**.

   ![2019-07-26_12-10-38](assets/2019-07-26_12-10-38.png)

1. Selecteer op de pagina **[!UICONTROL Adobe-opstartconfiguraties]** in het linkerdeelvenster een AEM-site waarop u de Adobe-startconfiguratie wilt toepassen.

   Alleen ter illustratie wordt de site **[!UICONTROL We.Retail]** geselecteerd in de onderstaande schermafbeelding.

   ![2019-07-26_12-20-06](assets/2019-07-26_12-20-06.png)

1. Near the upper-left corner of the page, click **[!UICONTROL Create]**.
1. Vul de volgende velden in op de pagina **[!UICONTROL Algemeen]** (1/3 pagina&#39;s) van het venster **[!UICONTROL Adobe-startconfiguratie]** maken:

   * **[!UICONTROL Titel]** - Voer een beschrijvende configuratitel in. Bijvoorbeeld, `We.Retail Launch cloud configuration`.

   * **[!UICONTROL Gekoppelde Adobe IMS-configuratie]** : selecteer de IMS-configuratie die u eerder hebt gemaakt in AEM IMS [configureren](#configuring-aem-ims).

   * **[!UICONTROL Bedrijf]** - Selecteer uw Cloud-bedrijf voor ervaring in de vervolgkeuzelijst **[!UICONTROL Bedrijf]** . De lijst wordt automatisch gevuld.

   * **[!UICONTROL Eigenschap]** - Selecteer in de vervolgkeuzelijst Eigenschappen de Adobe-eigenschap Starten die u eerder hebt gemaakt. De lijst wordt automatisch gevuld.
   Nadat u alle velden hebt ingevuld, ziet de pagina **[!UICONTROL Algemeen]** er ongeveer als volgt uit:

   ![image2019-7-15_14-34-23](assets/image2019-7-15_14-34-23.png)

1. Klik in de linkerbovenhoek op **[!UICONTROL Volgende]**.
1. Vul het volgende veld in op de pagina **[!UICONTROL Staging]** (2/3 pagina&#39;s) van het venster **[!UICONTROL Adobe Launch Configuration]** (Adobe Launch Configuration):

   In the **[!UICONTROL Library URI]** field, check the location of the staging version of your Adobe Launch library. Dit veld wordt automatisch ingevuld door AEM.

   Alleen ter illustratie worden in deze stap Adobe Launch-bibliotheken gebruikt die zijn geïmplementeerd op Adobe CDN.

   >[!NOTE]
   >
   >Controleer of de automatisch gevulde bibliotheek-URI (Uniform Resource Identifier) niet onjuist is samengesteld. Herstel indien nodig de URL zodanig dat deze een protocol-relatieve URI vertegenwoordigt. Dat wil zeggen dat het begint met een dubbele slash.
   >
   >
   >Bijvoorbeeld: `//assets.adobetm.com/launch-xxxx`.

   Your **[!UICONTROL Staging]** page should look similar to the following. De opties **[!UICONTROL Archiveren]** en Bibliotheek asynchroon **** laden zijn ***niet*** ingesteld:

   ![image2019-7-15_15-21-8](assets/image2019-7-15_15-21-8.png)

1. Klik in de rechterbovenhoek op **[!UICONTROL Volgende]**.
1. On the **[!UICONTROL Production]** page (3/3 pages) of the **[!UICONTROL Create Adobe Launch Configuration]** window, if needed, fix the auto-populated production URI similar to how it was done on the previous **[!UICONTROL Staging]** page.
1. Klik in de rechterbovenhoek op **[!UICONTROL Maken]**.

   Uw nieuwe Adobe Launch Cloud Configuration wordt nu gemaakt en wordt naast uw website weergegeven, net als in het volgende voorbeeld:

1. Selecteer uw nieuwe Adobe Launch Cloud Configuration (een vinkje links van de configuratietotel wanneer deze is geselecteerd). Klik op **[!UICONTROL Publiceren]** op de werkbalk.

   ![image2019-7-15_15-47-6](assets/image2019-7-15_15-47-6.png)

De auteur van AEM ondersteunt momenteel niet de integratie van Dynamic Media Viewers met Adobe Launch.

Deze wordt echter ondersteund in het publicatieknooppunt AEM. Met de standaardinstellingen van Adobe Launch Cloud Configuration gebruikt AEM-publicatie de productieomgeving van Adobe Launch. Daarom is het nodig om Adobe Launch-bibliotheekupdates tijdens de test steeds naar de productieomgeving te sturen.

Deze beperking kan worden omzeild door de ontwikkelings- of staging-URL van de Adobe Launch-bibliotheek op te geven in de Adobe Launch Cloud-configuratie voor AEM-publicatie hierboven. Hierdoor gebruikt het publicatieknooppunt AEM de ontwikkelings- of staging-versie van de Adobe Launch-bibliotheek.

Zie AEM [integreren met Adobe Launch via Adobe I/O](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html) voor meer informatie over het instellen van Adobe Launch Cloud Configuration.
