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
source-git-commit: b5cf18d8e83786a23005aadf8aafe43d006a2e67
workflow-type: tm+mt
source-wordcount: '6236'
ht-degree: 7%

---

# Dynamic Media-viewers integreren met Adobe Analytics- en Experience Platform-tags {#integrating-dynamic-media-viewers-with-adobe-analytics-and-adobe-launch}

## Wat is de integratie van Dynamic Media Viewers met Adobe Analytics en Experience Platform Tags? {#what-is-dynamic-media-viewers-integration-with-adobe-analytics-and-adobe-launch}

<!-- Leave this hidden path here; it points to the topic source from Sasha https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=~oufimtse&title=Dynamic+Media+Viewers+integration+with+Adobe+Launch -->

*Met Dynamic Media* Viewersextension voor Experience Platform Tags en Dynamic Media Viewers 5.13 kunnen klanten met Adobe Analytics- en Experience Platform Tags gebeurtenissen en gegevens gebruiken die specifiek zijn voor Dynamic Media Viewers in hun configuratie met Experience Platform Tags.

Dankzij deze integratie kunt u het gebruik van Dynamic Media Viewers op uw website bijhouden met Adobe Analytics. Tegelijkertijd kunt u de gebeurtenissen en gegevens gebruiken die door de viewers beschikbaar worden gesteld, met een andere extensie Experience Platform Tags die afkomstig is van Adobe of een derde.

Zie [Adobe extensies](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/overview.html) in de gebruikershandleiding voor Adobe-tags voor meer informatie over Experience Platform-extensies of extensies van derden.

**Dit onderwerp is voorgenomen voor het volgende:De beheerders van de** Plaats, Ontwikkelaars op het Experience Platform, en mensen in Verrichtingen.

### Beperkingen van de integratie {#limitations-of-the-integration}

* Integratie van Experience Platform-tags voor Dynamic Media-viewers werkt niet in het knooppunt van de auteur van de Experience Manager. U kunt geen het volgen van een pagina zien WCM tot het wordt gepubliceerd.
* Integratie van Experience Platform-tags voor Dynamic Media-viewers wordt niet ondersteund in de pop-upbewerkingsmodus, waarin de URL van de viewer wordt verkregen via de knop &quot;URL&quot; op de pagina Asset Details.
* Integratie van Experience Platform Tags kan niet gelijktijdig worden gebruikt met de integratie van verouderde viewers Analytics (via de parameter `config2=`).
* Ondersteuning voor het bijhouden van video&#39;s is beperkt tot het alleen bijhouden van de &quot;core playback&quot;, zoals wordt beschreven in [Overzicht van bijhouden](https://experienceleague.adobe.com/docs/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html#player-events). Met name QoS, Advertenties, Hoofdstuk/Segmenten, of het volgen van Fouten wordt niet gesteund.
* Configuratie opslagduur voor gegevenselementen wordt niet ondersteund voor gegevenselementen met de extensie *Dynamic Media Viewers*. Opslagduur moet worden ingesteld op **[!UICONTROL None]**.

### Gebruik de integratiegevallen {#use-cases-for-the-integration}

Het belangrijkste gebruiksgeval voor de integratie met Experience Platform Tags is klanten die zowel Adobe Experience Manager Assets als Adobe Experience Manager Sites gebruiken. In dergelijke scenario&#39;s, kunt u opstelling een standaardintegratie tussen uw de auteurknoop van de Experience Manager en de Markeringen van het Experience Platform, dan uw instantie van Plaatsen met het bezit van de Markeringen van het Experience Platform associ??ren. Daarna volgt elke Dynamic Media WCM-component die aan een sitepagina wordt toegevoegd, de gegevens en gebeurtenissen van viewers.

Zie [Dynamic Media-viewers bijhouden in Experience Manager Sites](#tracking-dynamic-media-viewers-in-aem-sites).

Een tweede gebruiksgeval dat de integratie steunt zijn die klanten die slechts de Activa van de Experience Manager, of Klassiek van Dynamic Media gebruiken. In dergelijke gevallen ontvangt u de insluitcode voor uw viewer en voegt u deze toe aan de websitepagina. Vervolgens haalt u de productie-URL voor de bibliotheek met Experience Platform-tags op uit Experience Platform-tags en voegt u deze handmatig toe aan de webpaginacode.

Zie [Dynamic Media-viewers bijhouden met de ingesloten code](#tracking-dynamic-media-viewers-using-embed-code).

<!-- Path on internal wiki [About tracking Dynamic Media viewers using embed code](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersusingEmbedcode). -->

## Hoe gegevens en gebeurtenis volgen werkt in de integratie {#how-data-and-event-tracking-works-in-the-integration}

De integratie maakt gebruik van twee aparte en onafhankelijke typen tracering voor Dynamic Media Viewers: *Adobe Analytics* en *Adobe Analytics for Audio and Video*.

### Over reeksspati??ring in Adobe Analytics  {#about-tracking-using-adobe-analytics}

Met Adobe Analytics kunt u handelingen bijhouden die door de eindgebruiker worden uitgevoerd wanneer deze communiceert met Dynamic Media Viewers op uw website. Met Adobe Analytics kunt u ook viewerspecifieke gegevens bijhouden. U kunt bijvoorbeeld de laadgebeurtenissen van de weergave bijhouden en opnemen, samen met de naam van het element, eventuele zoomacties die hebben plaatsgevonden en handelingen voor het afspelen van video.

In de Markeringen van het Experience Platform, werken de concepten *Gegevens Elementen* en *Regels* samen om Adobe Analytics het volgen toe te laten.

#### Gegevenselementen in Experience Platform-tags {#about-data-elements-in-adobe-launch}

Een gegevenselement in Experience Platform-tags is een benoemde eigenschap waarvan de waarde statisch wordt gedefinieerd of dynamisch wordt berekend op basis van de status van een webpagina of Dynamic Media Viewers-gegevens.

De opties die beschikbaar zijn voor een definitie van een gegevenselement, zijn afhankelijk van de lijst met extensies die zijn ge??nstalleerd in de eigenschap Codes van het Experience Platform. De &quot;Core&quot;uitbreiding is vooraf ge??nstalleerd en beschikbaar uit de doos in om het even welke configuratie. Met deze extensie &quot;Core&quot; kunt u een gegevenselement defini??ren dat afkomstig is van cookie, JavaScript-code, queryreeks en vele andere bronnen.

Voor het bijhouden van Adobe Analytics moeten meerdere extensies worden ge??nstalleerd, zoals beschreven in [Installatie en installatie van extensies](#installing-and-setup-of-extensions). Met de extensie Dynamic Media Viewers kunt u een gegevenselement defini??ren dat een argument is van de gebeurtenis Dynamic Viewer. Het is bijvoorbeeld mogelijk te verwijzen naar het viewertype, of de naam van het element die tijdens het laden door de viewer wordt gemeld, het zoomniveau dat wordt gemeld wanneer de eindgebruiker zoomt en nog veel meer.

Met de extensie Dynamic Media Viewer worden de waarden van de Data Elements automatisch bijgewerkt.

Nadat u het hebt bepaald, kan een Element van Gegevens in andere plaatsen van de Tags UI van het Experience Platform worden gebruikt, gebruikend de plukker van het Element van Gegevens widget. Met name wordt in de regel naar gegevenselementen die zijn gedefinieerd voor het bijhouden van Dynamic Media Viewers verwezen door de extensie Handeling voor variabelen instellen van Adobe Analytics (zie hieronder).

Zie [Gegevenselementen](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/data-elements.html).

#### Informatie over Regels in Experience Platform-tags {#about-rules-in-adobe-launch}

Een regel in de Markeringen van het Experience Platform is een agnostische configuratie die drie gebieden bepaalt die omhoog een regel maken: *Gebeurtenissen*, *Voorwaarden* en *Acties*:

* *Gebeurtenissen*  (als) vertellen Experience Platform Tags wanneer een regel moet worden geactiveerd.
* *De voorwaarden*  (als) vertellen de Markeringen van het Experience Platform welke andere beperkingen toestaan of verwerpen wanneer het teweegbrengen van een Regel.
* *Handelingen*  (dan) vertellen Experience Platform Tags wat er moet gebeuren wanneer een regel wordt geactiveerd.

Welke opties beschikbaar zijn in de sectie Gebeurtenissen, Voorwaarden en Handelingen, is afhankelijk van de extensies die zijn ge??nstalleerd in de eigenschap Experience Platform-tags. De *Core* uitbreiding is vooraf ge??nstalleerd en is beschikbaar uit-van-de-doos in om het even welke configuratie. De extensie biedt verschillende opties voor gebeurtenissen, zoals basishandelingen op browserniveau. Deze acties zijn onder andere focuswijziging, toetsdrukken en het verzenden van formulieren. Het bevat ook opties voor Voorwaarden, zoals cookiewaarde, browsertype en meer. Voor Acties is alleen de optie Aangepaste code beschikbaar.

Voor het bijhouden van Adobe Analytics moeten verschillende andere extensies worden ge??nstalleerd, zoals beschreven in [Installatie en installatie van extensies](#installing-and-setup-of-extensions). Specifiek:

* De extensie Dynamic Media Viewers breidt de lijst met ondersteunde gebeurtenissen uit tot gebeurtenissen die specifiek zijn voor Dynamic Media-viewers, zoals het laden van viewers, het wisselen van middelen, inzoomen en het afspelen van video.
* De extensie Adobe Analytics breidt de lijst met ondersteunde handelingen uit met twee handelingen die vereist zijn voor het verzenden van gegevens naar trackingservers: *Stel variabelen in* en *Verstuur baken*.

Als u Dynamic Media-viewers wilt bijhouden, kunt u elk type van de volgende opties gebruiken:

* Gebeurtenissen van de extensie Dynamic Media Viewers, Core-extensie of een andere extensie.
* Voorwaarden in de definitie van de regel. Of u kunt het gebied met voorwaarden leeg laten.

In de sectie van Acties, is het vereist dat u een *actie van Variabelen* plaatst. Deze actie vertelt Adobe Analytics hoe te om het volgen variabelen met gegevens te bevolken. Tegelijkertijd verzendt de handeling *Variabelen instellen* niets naar de trackingserver.

De *actie van de Vastgestelde Variabelen* moet door een *actie worden gevolgd verzenden Beacon*. Met de handeling *Send Beacon* worden gegevens daadwerkelijk verzonden naar de analytics tracking-server. Beide acties, *Reeks Variabelen* en *Send Beacon*, komen uit de uitbreiding van Adobe Analytics.

Zie [Regels](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html).

#### Voorbeeldconfiguratie {#sample-configuration}

In de volgende voorbeeldconfiguratie binnen Experience Platform Tags ziet u hoe u een elementnaam kunt bijhouden tijdens het laden van de viewer.

1. Definieer op het tabblad **[!UICONTROL Data Elements]** een gegevenselement `AssetName` dat verwijst naar de parameter `asset` van de gebeurtenis `LOAD` van de extensie Dynamic Media Viewers.

   ![image2019-11](assets/image2019-11.png)

1. Definieer op het tabblad **[!UICONTROL Rules]** een regel *TrackAssetOnLoad*.

   In deze regel gebruikt het veld **[!UICONTROL Event]** de gebeurtenis **[!UICONTROL LOAD]** van de extensie Dynamic Media Viewers.

   ![image2019-22](assets/image2019-22.png)

1. De configuratie van de Actie heeft twee types van Actie van de uitbreiding van Adobe Analytics:

   *Stel Variabelen* in, die een door u gekozen analytische variabele toewijzen aan de waarde van  `AssetName` Gegevenselement.

   *Stuur Beacon*, die trackinggegevens naar Adobe Analytics verzendt.

   ![image2019-3](assets/image2019-3.png)

1. De resulterende regelconfiguratie ziet er als volgt uit:

   ![image2019-4](assets/image2019-4.png)

### Informatie over Adobe Analytics for Audio en Video {#about-adobe-analytics-for-audio-and-video}

Wanneer een Experience Cloud-account is geabonneerd om Adobe Analytics for Audio en Video te gebruiken, is het voldoende om het bijhouden van video&#39;s in te schakelen in de extensie-instellingen *Dynamic Media Viewers*. Videomeetgegevens zijn beschikbaar in Adobe Analytics. De videotracering is afhankelijk van de aanwezigheid van Adobe Media Analytics voor de extensie Audio en Video.

Zie [Installatie en installatie van extensies](#installing-and-setup-of-extensions).

Momenteel is de ondersteuning voor videotracering beperkt tot het bijhouden van de &quot;core playback&quot;, zoals beschreven in [Tracking overview](https://experienceleague.adobe.com/docs/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html#player-events). Met name QoS, Advertenties, Hoofdstuk/Segmenten, of het volgen van Fouten wordt niet gesteund.

## De extensie Dynamic Media Viewers gebruiken {#using-the-dynamic-media-viewers-extension}

Zoals vermeld in [Gebruik gevallen voor de integratie](#use-cases-for-the-integration), is het mogelijk om de kijkers van Dynamic Media met de nieuwe integratie van de Markeringen van het Experience Platform in de Plaatsen van de Experience Manager te volgen en door ingebedcode te gebruiken.

### Dynamic Media-viewers bijhouden in Experience Manager Sites {#tracking-dynamic-media-viewers-in-aem-sites}

Om de kijkers van Dynamic Media in de Plaatsen van de Experience Manager te volgen, moeten alle stappen die onder [worden vermeld alle integratiestukken](#configuring-all-the-integration-pieces) sectie vormen worden uitgevoerd. Specifiek, moet u de configuratie IMS en de Configuratie van de Wolk van de Markeringen van het Experience Platform tot stand brengen.

Na de juiste configuratie worden gegevens automatisch bijgehouden naar Adobe Analytics, Adobe Analytics for Video, of naar beide, wanneer u een Dynamic Media-viewer toevoegt aan een sitepagina met een WCM-component die door Dynamic Media wordt ondersteund.

<!-- To be reviewed and updated although this is found live in the Experience ManageraaCS version:
See [Adding Dynamic Media Assets to Pages using Adobe Sites](https://helpx.adobe.com/experience-manager/6-5/help/assets/adding-dynamic-media-assets-to-pages.html).
-->

### Dynamic Media-viewers bijhouden met behulp van insluitcode {#tracking-dynamic-media-viewers-using-embed-code}

Klanten die geen gebruik maken van Experience Manager Sites of Dynamic Media-viewers insluiten in webpagina&#39;s buiten Experience Manager Sites, of beide, kunnen nog steeds gebruikmaken van de integratie met Experience Platform Tags.

Voltooi de configuratiestappen van [vorm Adobe Analytics](#configuring-adobe-analytics-for-the-integration) en [vorm de secties van de Markeringen van het Experience Platform](#configuring-adobe-launch-for-the-integration). Nochtans, zijn de op Experience Manager betrekking hebbende configuratiestappen niet nodig.

Na de juiste configuratie kunt u ondersteuning voor Experience Platform-tags toevoegen aan een webpagina met een Dynamic Media-viewer.

Zie [Voeg de tags van het Experience Platform toe bed Code](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/configure-launch/launch-add-embed.html#configure-launch) in om meer over te leren hoe te om de de bibliotheekinsluitcode van de Markeringen van het Experience Platform te gebruiken.

<!-- To be reviewed and updated although this is found live in the Experience ManageraaCS version:
See [Embedding the Video or Image Viewer on a Web Page](https://helpx.adobe.com/experience-manager/6-5/help/assets/embed-code.html) to learn more about how to use the embed code feature of Experience Manager Dynamic Media.
-->

**Dynamic Media-viewers bijhouden met gebruik van insluitcode:**

1. Zorg dat een webpagina gereed is voor het insluiten van een Dynamic Media-viewer.
1. Haal de insluitcode voor de bibliotheek van de Markeringen van het Experience Platform door zich eerst aan de Markeringen van het Experience Platform aan te melden (zie [Het Vormen van de Markeringen van het Experience Platform](#configuring-adobe-launch-for-the-integration)).
1. Selecteer **[!UICONTROL Property]** en selecteer vervolgens het tabblad **[!UICONTROL Environments]**.
1. Ophalen van het milieuniveau dat relevant is voor de omgeving van de webpagina. Selecteer vervolgens in de kolom **[!UICONTROL Install]** het vakpictogram.
1. **[!UICONTROL In the Web Install Instructions]** , kopieert u de volledige insluitcode van de Experience Platform Tags in de bibliotheek, samen met de omringende  `<script/>` tags.

## Referentiegids voor de extensie Dynamic Media Viewers {#reference-guide-for-the-dynamic-media-viewers-extension}

### De configuratie van Dynamic Media Viewers {#about-the-dynamic-media-viewers-configuration}

De extensie Dynamic Media Viewer wordt automatisch ge??ntegreerd met de bibliotheek met Experience Platform-tags als aan de volgende voorwaarden wordt voldaan:

* Globaal object ( `_satellite`) voor bibliotheektags van Experience Platform is aanwezig op de pagina.
* De Dynamic Media Viewers extension functie `_dmviewers_v001()` wordt gedefinieerd op `_satellite`.

* `config2=` Er is geen viewerparameter opgegeven, wat betekent dat de viewer geen gebruik maakt van verouderde analytische integratie.

Er is ook een optie om de integratie van Experience Platform-tags in de viewer expliciet uit te schakelen door de parameter `launch=0` in de configuratie van de viewer op te geven. De standaardwaarde van deze parameter is `1`.

### De extensie Dynamic Media Viewers configureren {#configuring-the-dynamic-media-viewers-extension}

De enige configuratieoptie voor de extensie Dynamic Media Viewers is **[!UICONTROL Enable Adobe Media Analytics for Audio and Video]**.

Wanneer u deze optie inschakelt en de extensie Adobe Media Analytics for Audio en Video is ge??nstalleerd en geconfigureerd, worden meetgegevens voor het afspelen van video naar de Adobe Analytics for Audio and Video-oplossing verzonden. Als u deze optie uitschakelt, wordt het bijhouden van video uitgeschakeld.

Als u deze optie *inschakelt zonder dat er Adobe Media Analytics for Audio en Video is ge??nstalleerd, heeft deze optie geen effect.*

![image2019-7-22_12-4-23](assets/image2019-7-22_12-4-23.png)

### Over Data Elements in de extensie Dynamic Media Viewers {#about-data-elements-in-the-dynamic-media-viewers-extension}

Het enige data-elementtype dat de uitbreiding Dynamische mediaviewers biedt, is **[!UICONTROL Viewer Event]** in de vervolgkeuzelijst **[!UICONTROL Data Element Type]**.

Als deze optie is geselecteerd, maakt de Data Element-editor een formulier met twee velden:

* **[!UICONTROL DM viewers event data type]** - een vervolgkeuzelijst met alle viewergebeurtenissen die door de uitbreiding Dynamische mediaviewers worden ondersteund en die argumenten bevatten, plus een speciaal **[!UICONTROL COMMON]**-item. Een **[!UICONTROL COMMON]**-item vertegenwoordigt een lijst met gebeurtenisparameters die gemeenschappelijk zijn voor alle typen gebeurtenissen die door de viewers worden verzonden.
* **[!UICONTROL Tracking parameter]** - een argument van de geselecteerde Dynamic Media-viewergebeurtenis.

![image2019-7-22_12-5-46](assets/image2019-7-22_12-5-46.png)

Zie de [Dynamic Media Viewers reference guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc) voor de lijst met ondersteunde gebeurtenissen per viewertype; Ga naar de specifieke sectie van de kijker, dan uitgezochte Steun voor de sectie van het volgen van Adobe Analytics. Op dit moment worden in de naslaggids voor Dynamic Media Viewers geen gebeurtenisargumenten vastgelegd.

Bekijk nu de levenscyclus van de Dynamic Media Viewers *Data Element*. De waarde van een dergelijk gegevenselement wordt gevuld nadat de bijbehorende Dynamic Media-viewergebeurtenis op de pagina plaatsvindt. Stel dat het gegevenselement verwijst naar de gebeurtenis **[!UICONTROL LOAD]** en het argument &quot;asset&quot; ervan. In dat geval ontvangt de waarde van een dergelijk gegevenselement geldige gegevens nadat de viewer de gebeurtenis **[!UICONTROL LOAD]** voor de eerste keer uitvoert. Als het gegevenselement naar de gebeurtenis **[!UICONTROL ZOOM]** en het bijbehorende &quot;schaal&quot;argument wijst, blijft de waarde van zulk een Element van Gegevens leeg tot de kijker een **[!UICONTROL ZOOM]** gebeurtenis voor het eerst verzendt.

Op dezelfde manier worden de waarden van data-elementen automatisch bijgewerkt wanneer de viewer een overeenkomstige gebeurtenis op de pagina verzendt. De waarde-update gebeurt zelfs als de specifieke gebeurtenis niet in de regelconfiguratie is opgegeven. Stel dat het gegevenselement **[!UICONTROL ZoomScale]** is gedefinieerd voor de parameter &quot;scale&quot; van de ZOOM-gebeurtenis. Nochtans, wordt de enige regel huidig in de configuratie van de Regel teweeggebracht door de **[!UICONTROL LOAD]** gebeurtenis. De waarde van **[!UICONTROL ZoomScale]** wordt nog steeds bijgewerkt wanneer een gebruiker inzoomt in de viewer uitvoert.

Elke viewer voor dynamische media heeft een unieke id op de webpagina. Het gegevenselement houdt de waarde zelf bij en de viewer die de waarde heeft gevuld. Stel dat er bijvoorbeeld verschillende viewers op dezelfde pagina staan en een **[!UICONTROL AssetName]** gegevenselement dat naar de gebeurtenis **[!UICONTROL LOAD]** en het argument &quot;asset&quot; verwijst. Het gegevenselement **[!UICONTROL AssetName]** onderhoudt een verzameling elementnamen die zijn gekoppeld aan elke viewer die op de pagina is geladen.

De exacte waarde die door het gegevenselement wordt geretourneerd, is afhankelijk van de context. Als het gegevenselement wordt gevraagd in een Regel die door een de kijkergebeurtenis van Dynamic Media werd teweeggebracht, dan is de waarde van het Element van Gegevens teruggekeerd voor de kijker die de Regel in werking stelde. En, wordt het Element van Gegevens gevraagd in een Regel die door een Gebeurtenis van ????n of andere uitbreiding van de Markeringen van het Experience Platform werd teweeggebracht. Op dat punt, komt de waarde van het Element van Gegevens uit de kijker die het laatst dit Element van Gegevens bijwerkte.

**Overweeg de volgende voorbeeldopstelling:**

* Een webpagina met twee Dynamic Media-zoomviewers: *viewer1* en *viewer2*.

* **[!UICONTROL ZoomScale]** Data Element verwijst naar de  **[!UICONTROL ZOOM]** gebeurtenis en het argument &#39;scale&#39; ervan.
* **[!UICONTROL TrackPan]** Regel met het volgende:

   * Gebruikt de Dynamic Media Viewer **[!UICONTROL PAN]**-gebeurtenis als trigger.
   * Verzendt de waarde van **[!UICONTROL ZoomScale]** het Element van Gegevens naar Adobe Analytics.

* **[!UICONTROL TrackKey]** Regel met het volgende:

   * Gebruikt de belangrijkste persgebeurtenis van de uitbreiding van de Markeringen van het Experience Platform van de Kern als trekker.
   * Verzendt de waarde van **[!UICONTROL ZoomScale]** het Element van Gegevens naar Adobe Analytics.

Nu, veronderstel de eindgebruiker de Web-pagina met de twee kijkers laadt. In *viewer1*, zoom zij aan schaal 50% in; Vervolgens zoomen ze in *viewer2* in op een schaal van 25%. In *viewer1*, pannen zij beeld rond, en selecteren tenslotte een sleutel op het toetsenbord.

De activiteit van de eindgebruiker resulteert in de volgende twee volgende volgende vraag die aan Adobe Analytics wordt gemaakt:

* De eerste vraag komt voor omdat **[!UICONTROL TrackPan]** de Regel wordt teweeggebracht wanneer de gebruiker in *viewer1* pant. Die vraag verzendt 50% als waarde van **[!UICONTROL ZoomScale]** het Element van Gegevens omdat het Element van Gegevens weet dat de Regel door *viewer1* wordt teweeggebracht en de overeenkomstige schaalwaarde haalt;
* De tweede vraag komt voor omdat **[!UICONTROL TrackKey]** de Regel wordt teweeggebracht wanneer de gebruiker op een sleutel op het toetsenbord duwde. Die vraag verzendt 25% als waarde van **[!UICONTROL ZoomScale]** het Element van Gegevens omdat de Regel niet door de kijker werd teweeggebracht. Als dusdanig, keert het Element van Gegevens de meest bijgewerkte waarde terug.

Het voorbeeld hierboven heeft ook invloed op de levensduur van de waarde voor het gegevenselement. De waarde van het gegevenselement dat door de Dynamic Media Viewer wordt beheerd, wordt opgeslagen in de bibliotheekcode van Experience Platforms Tags, zelfs nadat de viewer zelf op de webpagina is verwijderd. Deze functionaliteit houdt in dat als er een regel is die door een niet-Dynamic Media Viewer-extensie wordt geactiveerd en naar een dergelijk gegevenselement verwijst, het gegevenselement de laatst bekende waarde retourneert. Zelfs als de viewer niet meer aanwezig is op de webpagina.

De waarden van gegevenselementen die door Dynamic Media Viewers worden aangestuurd, worden in geen geval opgeslagen op de lokale opslag of op de server. in plaats daarvan, worden zij slechts op de cli??nt-zijbibliotheek van de Markeringen van het Experience Platform gehouden. Waarden van een dergelijk gegevenselement verdwijnen als de webpagina opnieuw wordt geladen.

Over het algemeen biedt de Data Element-editor ondersteuning voor de optie [opslagduur](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/data-elements.html#create-a-data-element). Gegevenselementen die de extensie Dynamic Media Viewers gebruiken, ondersteunen echter alleen de opslagduuroptie van **[!UICONTROL None]**. Het instellen van een andere waarde is mogelijk in de gebruikersinterface, maar het gedrag Gegevenselement is in dit geval niet gedefinieerd. De extensie beheert de waarde van het gegevenselement op zichzelf: het gegevenselement dat de waarde van het gebeurtenisargument van de viewer tijdens de volledige de levenscyclus van de kijker handhaaft.

### Over Regels in de extensie Dynamic Media Viewers {#about-rules-in-the-dynamic-media-viewers-extension}

In de redacteur van de Regel, voegt de uitbreiding nieuwe configuratieopties voor de redacteur van Gebeurtenissen toe. Ook biedt de editor een optie om handmatig te verwijzen naar gebeurtenisparameters in de Action Editor als een kortzichtige optie in plaats van vooraf geconfigureerde gegevenselementen te gebruiken.

#### Informatie over de Events-editor {#about-the-events-editor}

In de redacteur van de Gebeurtenis, voegt de uitbreiding van de Kijkers van Dynamic Media **[!UICONTROL Event Type]** genoemd **[!UICONTROL Viewer Event]** toe.

Als deze optie is geselecteerd, wordt de vervolgkeuzelijst **[!UICONTROL Dynamic Media Viewer events]** weergegeven met alle beschikbare gebeurtenissen die door Dynamic Media-viewers worden ondersteund.

![image2019-8-2_15-13-1](assets/image2019-8-2_15-13-1.png)

#### De Editor voor handelingen {#about-the-actions-editor}

Met de extensie Dynamic Media Viewers kunt u gebeurtenisparameters van Dynamic Media-viewers gebruiken om de variabelen voor de analyse in te delen in de editor Variabelen instellen van de Adobe Analytics-extensie.

De eenvoudigste methode om dat te doen is het volgende twee-stap proces te voltooien:

* Definieer eerst een of meer gegevenselementen, waarbij elk gegevenselement een parameter van een Dynamic Media Viewer-gebeurtenis vertegenwoordigt.
* Tot slot in de Vastgestelde redacteur van Variabelen van de uitbreiding van Adobe Analytics selecteer **[!UICONTROL Data Element]** plukkerpictogram (drie gestapelde schijven) om het Uitgezochte de dialoogvakje van het Element van Gegevens te openen, dan selecteer een Element van Gegevens van het.

![image2019-7-10_20-41-52](assets/image2019-7-10_20-41-52.png)

Het is echter mogelijk om een alternatieve manier te gebruiken en het maken van data-elementen te omzeilen. U kunt rechtstreeks verwijzen naar een argument van een Dynamic Media Viewer-gebeurtenis. Voer de volledig gekwalificeerde naam van het gebeurtenisargument in het invoerveld **[!UICONTROL value]** van de variabele Analytics-toewijzing in. Zorg ervoor dat u het omringt met procenttekens (%). Bijvoorbeeld,

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

Adobe raadt u aan alle documentatie v????r deze sectie grondig te controleren, zodat u de volledige integratie begrijpt.

In deze sectie worden de configuratiestappen beschreven die nodig zijn om Dynamic Media-viewers te integreren met Adobe Analytics en Adobe Analytics for Audio en Video. Hoewel het gebruik van de extensie Dynamic Media Viewers voor andere doeleinden in Experience Platforms tags mogelijk is, worden dergelijke scenario&#39;s niet behandeld in deze documentatie.

U gaat de volgende producten van Adobe gebruiken om uw integratie te vormen:

* Adobe Analytics - gebruikt om het volgen variabelen en rapporten te vormen.
* Tags voor Experience Platforms - worden gebruikt om een eigenschap, een of meer regels en een of meer gegevenselementen te defini??ren om het bijhouden van de viewer in te schakelen.

Ook, als deze integratieoplossing met de Plaatsen van de Experience Manager wordt gebruikt, moet de volgende configuratie ook worden gedaan:

* [!DNL Adobe I/O] Console - integratie wordt gecreeerd voor de Markeringen van het Experience Platform.
* Knooppunt van de auteur van de Experience Manager - de configuratie IMS en de wolkenconfiguratie van de Markeringen van het Experience Platform.

Als deel van de configuratie, zeker bent u toegang tot een bedrijf in Adobe Experience Cloud hebt dat Adobe Analytics en de Markeringen van het Experience Platform reeds heeft toegelaten.

## Adobe Analytics configureren voor integratie {#configuring-adobe-analytics-for-the-integration}

Nadat u Adobe Analytics hebt geconfigureerd, wordt het volgende voor integratie ingesteld:

* Er is een rapportsuite ge??nstalleerd en geselecteerd.
* De Variabelen van de Analyse zijn beschikbaar om het volgen gegevens te ontvangen.
* Rapporten zijn beschikbaar voor het weergeven van verzamelde gegevens in Adobe Analytics.

Zie ook [Analytics Implementation Guide](https://experienceleague.adobe.com/docs/analytics/implementation/home.html).

**Adobe Analytics configureren voor integratie:**

1. Begin door Adobe Analytics van de Experience Cloud [homepage](https://experience.adobe.com/#/home) toegang te hebben. Selecteer in de menubalk het pictogram **[!UICONTROL Solutions]** (een drie bij drie punten) rechtsboven op de pagina en selecteer vervolgens **[!UICONTROL Analytics]**.

   ![2019-07-22_18-08-47](assets/2019-07-22_18-08-47.png)

   Selecteer nu een rapportsuite.

### Selecteer een rapportsuite {#selecting-a-report-suite}

1. Selecteer in de rechterbovenhoek van de Adobe Analytics-pagina rechts van het veld **[!UICONTROL Search Reports]** de juiste rapportsuite in de vervolgkeuzelijst. Als er meerdere rapportsuites beschikbaar zijn en u niet zeker weet welke suite u moet gebruiken, neemt u contact op met uw Adobe Analytics-beheerder. Deze beheerder kan u helpen bij het selecteren van de rapportsuite die moet worden gebruikt.

   In de onderstaande schermafbeelding heeft een gebruiker een rapportsuite gemaakt met de naam *DynamicMediaViewersExtensionDoc* en deze geselecteerd in de vervolgkeuzelijst. De naam van de rapportsuite is alleen een voorbeeldnaam. De naam van de rapportsuite die u uiteindelijk selecteert, is aan u.

   Als er geen rapportsuite beschikbaar is, moet u of uw Adobe Analytics-beheerder er een maken voordat u verder kunt gaan met de configuratie.

   Zie [Rapporten en Rapporten ](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/report-suites-admin.html#manage-report-suites) en [Een rapportsuite](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html) maken.

   In Adobe Analytics worden rapportsuites beheerd onder **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]**.

   ![2019-07-22_18-09-49](assets/2019-07-22_18-09-49.png)

   Stel nu Adobe Analytics-variabelen in.

### Adobe Analytics-variabelen instellen {#setting-up-adobe-analytics-variables}

1. Wijs een of meer Adobe Analytics-variabelen aan die u wilt gebruiken om het gedrag van Dynamic Media Viewers op de webpagina bij te houden.

   U kunt elk type variabele gebruiken dat door Adobe Analytics wordt ondersteund. De beslissing over het variabeletype (zoals het Verkeer van de Douane [props], de Omzetting [eVar]) wordt gedreven door de specifieke behoeften van uw implementatie Analytics.

   Zie [Overzicht van props en eVars](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html#vars).

   In het kader van deze documentatie wordt alleen een variabele Custom Traffic (props) gebruikt, omdat deze binnen een paar minuten nadat een handeling op een webpagina heeft plaatsgevonden, beschikbaar komt in een Analytics-rapport.

   Als u een nieuwe variabele Aangepast verkeer wilt inschakelen, gaat u in Adobe Analytics op de werkbalk naar **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]**.

1. Selecteer op de pagina **[!UICONTROL Report Suite Manager]** het juiste rapport en navigeer op de werkbalk naar **[!UICONTROL Edit Settings]** > **[!UICONTROL Traffic]** > **[!UICONTROL Traffic Variables]**.
1. Selecteer een variabele die niet wordt gebruikt, geef het een beschrijvende naam (**[!UICONTROL Viewer asset (prop 30)]**) en verander combodoos in &quot;Toegelaten&quot;in de Toegelaten kolom.

   De volgende schermafbeelding is een voorbeeld van een variabele van het Verkeer van de Douane ( **[!UICONTROL prop30]**) voor het volgen van een activanaam die door de kijker wordt gebruikt:

   ![image2019-6-26_23-6-59](assets/image2019-6-26_23-6-59.png)

1. Selecteer **[!UICONTROL Save]** onder aan de lijst met variabelen.

### Een rapport instellen {#setting-up-a-report}

1. Over het algemeen wordt het opstellen van een rapport in Adobe Analytics gestuurd door specifieke projectbehoeften. Als dusdanig, is de gedetailleerde rapportopstelling voorbij het werkingsgebied voor deze integratie.

   Het is, echter, genoeg om te weten dat de rapporten van het Verkeer van de Douane automatisch beschikbaar worden in Adobe Analytics nadat u de variabelen van het Verkeer van de Opstelling van het Verkeer in [de variabelen van Adobe Analytics van de Opstelling ](#setting-up-adobe-analytics-variables) plaatst.

   Het rapport voor de variabele **[!UICONTROL Viewer asset (prop 30)]** is bijvoorbeeld beschikbaar in het menu Rapporten onder **[!UICONTROL Custom Traffic]** > **[!UICONTROL Custom Traffic 21-30]** > **[!UICONTROL Viewer asset (prop 30)]**.

   Als u dit rapport meteen na het maken van **[!UICONTROL Viewer asset (prop 30)]** bezoekt, worden er geen data weergegeven. Dat wordt op dit moment in de integratie verwacht.

   ![image2019-6-26_23-12-49](assets/image2019-6-26_23-12-49.png)

## Experience Platform-tags configureren voor integratie {#configuring-adobe-launch-for-the-integration}

Nadat u de Markeringen van het Experience Platform vormt, zal het volgende opstelling voor de integratie zijn:

* Het cre??ren van een nieuw Bezit om al uw configuraties samen te houden.
* De installatie en installatie van extensies. De client-side code van alle extensies die in de eigenschap zijn ge??nstalleerd, wordt samen gecompileerd in een bibliotheek. Deze bibliotheek wordt later door de webpagina gebruikt.
* Configuratie van gegevenselementen en regels. Deze configuratie bepaalt welke gegevens van de kijkers van Dynamic Media moeten vangen, wanneer om de volgende logica teweeg te brengen, en waar om de gegevens van de kijker in Adobe Analytics te verzenden.
* Publiceren van de bibliotheek.

**Om de Markeringen van het Experience Platform voor de integratie te vormen:**

1. Begin door tot de Markeringen van het Experience Platform van de Experience Cloud [homepage](https://experience.adobe.com/#/home) toegang te hebben. Selecteer in de menubalk het pictogram **[!UICONTROL Solutions]** (drie bij drie puntenlijsten) rechtsboven op de pagina en selecteer **[!UICONTROL Tags]**.

   U kunt ook [Experience Platform Tags direct openen](https://launch.adobe.com/).

   ![image2019-7-8_15-38-44](assets/image2019-7-8_15-38-44.png)

### Een eigenschap maken in Experience Platform-tags {#creating-a-property-in-adobe-launch}

Een bezit in de Markeringen van het Experience Platform is een genoemde configuratie die al uw montages bij elkaar houdt. Er wordt een bibliotheek met de configuratie-instellingen gegenereerd en gepubliceerd op verschillende milieuniveaus (ontwikkeling, staging en productie).

Zie ook [Een eigenschap van Codes maken](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-mobile-android-apps-with-launch/configure-launch/launch-create-a-property.html#configure-launch).

1. Selecteer **[!UICONTROL New Property]** in Experience Platform-tags.
1. Typ in het dialoogvenster **[!UICONTROL Create Property]** in het veld **[!UICONTROL Name]** een beschrijvende naam, zoals de titel van uw website. Bijvoorbeeld, `DynamicMediaViewersProp.`
1. Voer in het veld **[!UICONTROL Domains]** het domein van uw website in.
1. Schakel in de vervolgkeuzelijst **[!UICONTROL Advanced Options]** **[!UICONTROL Configure for extension development (cannot be modified later)]** in voor het geval dat de extensie die u wilt gebruiken, in dit geval *Dynamic Media Viewers*???nog niet wordt vrijgegeven.

   ![image2019-7-8_16-3-47](assets/image2019-7-8_16-3-47.png)

1. Selecteer **[!UICONTROL Save]**.

   Selecteer het nieuwe bezit dan aan *Installatie en opstelling van uitbreidingen* te werk gaan.

### Extensies installeren en instellen {#installing-and-setup-of-extensions}

Alle beschikbare extensies in Experience Platform-tags worden weergegeven onder **[!UICONTROL Extensions]** > **[!UICONTROL Catalog]**.

Selecteer **[!UICONTROL Install]** om een extensie te installeren. Voer zo nodig een eenmalige extensieconfiguratie uit en selecteer **[!UICONTROL Save]**.

Waar nodig moeten de volgende extensies worden ge??nstalleerd en geconfigureerd:

* (Vereist) *Experience Cloud ID Service* uitbreiding.

Geen extra configuratie is nodig, keur voor om het even welke voorgestelde waarden goed. Als u klaar bent, moet u **[!UICONTROL Save]** selecteren.

Zie [Adobe Experience Cloud Identity Service extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/id-service/overview.html).

* (Vereist) *Adobe Analytics*-extensie

Als u deze extensie wilt configureren, hebt u de rapportsuite-id in Adobe Analytics nodig onder **[!UICONTROL Admin]** > **[!UICONTROL Report Suite]** onder de kolomkop **[!UICONTROL Report Suite ID]**.

(Alleen voor demonstratiedoeleinden wordt de rapportsuite-id van de rapportsuite **[!UICONTROL DynamicMediaViewersExtensionDoc]** gebruikt in de volgende schermafbeeldingen. Deze id is gemaakt en gebruikt in [Selecteer eerder een rapportsuite](#selecting-a-report-suite).)

![image2019-7-8_16-45-34](assets/image2019-7-8_16-45-34.png)

Voer op de pagina Uitbreiding installeren de rapportsuite-id in het veld **[!UICONTROL Development Report Suites]**, het veld **[!UICONTROL Staging Report Suites]** en het veld **[!UICONTROL Production Report Suites]** in.

![image2019-7-8_16-47-40](assets/image2019-7-8_16-47-40.png)

*Configureer het volgende item alleen als u videotracering wilt gebruiken:*

Vouw op de pagina **[!UICONTROL Install Extension]** **[!UICONTROL General]** uit en geef vervolgens de trackingserver op. De volgende server volgt de sjabloon `<trackingNamespace>.sc.omtrdc.net`, waarbij `<trackingNamespace>` de informatie is die in de inrichtingse-mail wordt verkregen.

Selecteer **[!UICONTROL Save]**.

Zie [Adobe Analytics extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/analytics/overview.html).

* (facultatief; is alleen vereist als videotracering nodig is) *Adobe Media Analytics voor audio en Video*-extensie

Vul het veld Trackingserver in. De volgende server voor *Adobe Media Analytics voor Audio en Video* uitbreiding is verschillend van de volgende server die voor Adobe Analytics wordt gebruikt. Hierna volgt de sjabloon `<trackingNamespace>.hb.omtrdc.net`, waarbij `<trackingNamespace>` de informatie uit de inrichtingse-mail is.

Alle andere velden zijn optioneel.

Zie [Adobe Media Analytics for Audio and Video extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics/overview.html).

* (Vereist) *Dynamic Media Viewers*-extensie

Schakel **[!UICONTROL enable Adobe Analytics for Video]** in om het bijhouden van videorecorders in te schakelen.

Bij het ter perse gaan is de extensie *Dynamic Media Viewers* alleen beschikbaar als de eigenschap Experience Platform Tags is gemaakt voor ontwikkeling.

Zie [Een eigenschap maken in Experience Platform-tags](#creating-a-property-in-adobe-launch).

Nadat de extensies zijn ge??nstalleerd en ingesteld, worden ten minste de volgende vijf extensies (vier extensies als u geen video bijhoudt) weergegeven in het gedeelte Extensies > Ge??nstalleerd.

![image2019-7-22_12-7-36](assets/image2019-7-22_12-7-36.png)

### Gegevenselementen en regels instellen {#setting-up-data-elements-and-rules}

Maak gegevenselementen en -regels in Experience Platform-tags die nodig zijn voor het bijhouden van Dynamic Media-viewers.

Zie [Hoe gegevens en gebeurtenis het volgen in de integratie ](#how-data-and-event-tracking-works-in-the-integration) voor een overzicht van het volgen met de Markeringen van het Experience Platform werkt.

Zie [Voorbeeldconfiguratie](#sample-configuration) voor een voorbeeldconfiguratie in Experience Platform Tags die aantonen hoe u een elementnaam bij het laden van de viewer kunt bijhouden.

Zie [De extensie Dynamic Media Viewers configureren](#configuring-the-dynamic-media-viewers-extension) voor uitgebreide informatie over de mogelijkheden van de extensie.

### Bibliotheek publiceren {#publishing-a-library}

Om de configuratie van de Markeringen van het Experience Platform (met inbegrip van Bezit, Uitbreidingen, Regels, en de opstelling van Elementen van Gegevens) te veranderen, moet u *publiceren* dergelijke veranderingen. Het publiceren in de Markeringen van het Experience Platform wordt uitgevoerd van het Publiceren lusje onder de configuratie van het Bezit.

De Markeringen van het Experience Platform kunnen veelvoudige milieu&#39;s van de Ontwikkeling, ????n het Opvoeren milieu, en ????n milieu van de Productie potentieel hebben. Door gebrek wijst de Configuratie van de Wolk van de Markeringen van het Experience Platform in Experience Manager de Experience Manager auteurknoop aan het milieu van het Stadium van de Markeringen van het Experience Platform. De Experience Manager publiceert knoop wijst aan het milieu van de Productie van de Markeringen van het Experience Platform. Dit betekent dat met de standaardinstellingen voor Experience Managers, de bibliotheek met Experience Platform-tags moet worden gepubliceerd naar de testomgeving. Zo kunt u het gebruiken in de auteur van de Experience Manager. U kunt het dan publiceren in het milieu van de Productie zodat het in Experience Manager kan worden gebruikt publiceren.

Zie [Omgevingen](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/environments/environments.html) voor meer informatie over de milieu&#39;s van de Markeringen van het Experience Platform.

Bij het publiceren van een bibliotheek worden de volgende twee stappen uitgevoerd:

* Het toevoegen van en het bouwen van een nieuwe bibliotheek door alle noodzakelijke veranderingen (nieuwe degenen en updates) in de bibliotheek te omvatten.
* De bibliotheek door de verschillende milieuniveaus verplaatsen (van Ontwikkeling tot Staging en Productie).

#### Een nieuwe bibliotheek toevoegen en maken {#adding-and-building-a-new-library}

1. De eerste keer dat u het tabblad Publiceren opent in Experience Platform-tags, is de bibliotheeklijst leeg.

   Selecteer **[!UICONTROL Add New Library]** in de linkerkolom.

   ![image2019-7-15_14-43-17](assets/image2019-7-15_14-43-17.png)

1. Voer op de pagina Nieuwe bibliotheek maken in het veld **[!UICONTROL Name]** een beschrijvende naam in voor de nieuwe bibliotheek. Bijvoorbeeld,

   *DynamicMediaViewersLib*

   Kies in de vervolgkeuzelijst Milieu het niveau Milieu. In eerste instantie is alleen het ontwikkelingsniveau beschikbaar voor selectie. Selecteer **[!UICONTROL Add All Changed Resources]** naast de linkerbenedenzijde van de pagina.

   ![image2019-7-15_14-49-41](assets/image2019-7-15_14-49-41.png)

1. Selecteer **[!UICONTROL Save & Build for Development]** in de rechterbovenhoek van de pagina.

   Over een paar minuten wordt de bibliotheek gemaakt en klaar voor gebruik.

   ![image2019-7-15_15-3-34](assets/image2019-7-15_15-3-34.png)

   >[!NOTE]
   >
   >De volgende keer dat u de configuratie van de tags van het Experience Platform wijzigt, gaat u naar het tabblad **[!UICONTROL Publishing]** onder de configuratie **[!UICONTROL Property]** en selecteert u de eerder gemaakte bibliotheek.
   >
   >
   >Selecteer **[!UICONTROL Add All Changed Resources]** in het publicatiescherm van de bibliotheek en selecteer **[!UICONTROL Save & Build for Development]**.

#### Een bibliotheek omhoog verplaatsen via omgevingsniveaus {#moving-a-library-up-through-environment-levels}

1. Nadat er een nieuwe bibliotheek is toegevoegd, bevindt deze zich in de ontwikkelomgeving. Selecteer **[!UICONTROL Submit for Approval]** in het vervolgkeuzemenu van de bibliotheek om deze naar het niveau van de testomgeving (dat overeenkomt met de kolom Verzenden) te verplaatsen.

   ![image2019-7-15_15-52-37](assets/image2019-7-15_15-52-37.png)

1. Selecteer **[!UICONTROL Submit]** in het bevestigingsdialoogvenster.

   Selecteer **[!UICONTROL Build for Staging]** nadat de bibliotheek naar de kolom Verzonden is gegaan in het vervolgkeuzemenu van de bibliotheek.

   ![image2019-7-15_15-54-37](assets/image2019-7-15_15-54-37.png)

1. Als u de bibliotheek wilt verplaatsen van de testomgeving naar de productieomgeving (de kolom Published), voert u een vergelijkbaar proces uit.

   Selecteer eerst **[!UICONTROL Approve for Publishing]** in het keuzemenu.

   ![image2019-7-15_16-7-39](assets/image2019-7-15_16-7-39.png)

1. Selecteer **[!UICONTROL Build & Publish to Production]** in het keuzemenu.

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

1. In de auteur van de Experience Manager, selecteer **[!UICONTROL Tools]** pictogram (hamer), dan ga naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

   ![2019-07-25_11-52-58](assets/2019-07-25_11-52-58.png)

1. Selecteer **[!UICONTROL Create]** op de pagina Configuratie Adobe IMC in de linkerbovenhoek.
1. Selecteer **[!UICONTROL Experience Platform Tags]** op de pagina **[!UICONTROL Adobe IMS Technical Account Configuration]** in de vervolgkeuzelijst **[!UICONTROL Cloud Solution]**.
1. Schakel **[!UICONTROL Create new certificate]** in en voer in het tekstveld een betekenisvolle waarde voor het certificaat in. Bijvoorbeeld *AdobeLaunchIMSCert*. Selecteer **[!UICONTROL Create certificate]**.

   Het volgende Info-bericht wordt weergegeven:

   *Om een geldig toegangstoken terug te winnen, wordt de openbare sleutel van het nieuwe certificaat toegevoegd aan de technische rekening op Adobe I/O!*

   Selecteer **[!UICONTROL OK]** om het dialoogvenster Info te sluiten.

   ![2019-07-25_12-09-24](assets/2019-07-25_12-09-24.png)

1. Als u een bestand met een openbare sleutel (*.crt) naar uw lokale systeem wilt downloaden, selecteert u **[!UICONTROL Download Public Key]**.

   >[!NOTE]
   >
   >Op dit punt, ***verlaat open*** de **[!UICONTROL Adobe IMS Technical Account Configuration]** pagina; ***sluit de pagina niet*** en ***selecteer Volgende niet***. U gaat later in de stappen terug naar deze pagina.

   ![2019-07-25_12-52-24](assets/2019-07-25_12-52-24.png)

1. In een nieuw browser lusje, navigeer aan [[!DNL Adobe I/O] Console](https://console.adobe.io/integrations).

1. Selecteer **[!UICONTROL New integration]** op de pagina **[!UICONTROL Adobe I/O Console Integrations]** in de rechterbovenhoek.
1. Controleer in het dialoogvenster **[!UICONTROL Create a new integration]** of het keuzerondje **[!UICONTROL Access an API]** is geselecteerd en selecteer **[!UICONTROL Continue]**.

   ![2019-07-25_13-04-20](assets/2019-07-25_13-04-20.png)

1. Schakel op de tweede pagina **[!UICONTROL Create a new integration]** het keuzerondje **[!UICONTROL Experience Platform Tags API]** in. Selecteer **[!UICONTROL Continue]** in de rechterbenedenhoek van de pagina.

   ![2019-07-25_13-14](assets/2019-07-25_13-13-54.png)

1. Ga als volgt te werk op de derde pagina **[!UICONTROL Create a new integration]**:

   * Voer in het veld **[!UICONTROL Name]** een beschrijvende naam in. Bijvoorbeeld *DynamicMediaViewersIO*.

   * Voer in het veld **[!UICONTROL Description]** een beschrijving in voor de integratie.

   * Upload in het gebied **[!UICONTROL Public key certificates]** het bestand met de openbare sleutel (*.crt) dat u eerder in deze stappen hebt gedownload.

   * Selecteer **[!UICONTROL Admin]** onder de kop **[!UICONTROL Select a role for Experience Platform Tags API]**.

   * Selecteer onder de kop **[!UICONTROL Select one or more product profiles for Experience Platform Tags API]** het productprofiel **[!UICONTROL Tags - <your_company_name>]**.

   ![2019-07-25_13-49-18](assets/2019-07-25_13-49-18.png)

1. Selecteer **[!UICONTROL Create integration]**.
1. Selecteer **[!UICONTROL Continue to integration details]** op de pagina **[!UICONTROL Integration created]**.

   ![2019-07-25_14-16-33](assets/2019-07-25_14-16-33.png)

1. Er wordt een pagina met integratiedetails weergegeven ****, vergelijkbaar met het volgende:

   >[!NOTE]
   >
   >***Laat deze pagina met integratiedata open***. U zult verschillende stukken van informatie van **[!UICONTROL Overview]** en **[!UICONTROL JWT]** lusjes in enkel een ogenblik nodig hebben.

   ![2019-07-25_14-35-30](assets/2019-07-25_14-35-30.png)

   Pagina met integratiegegevens.

1. Ga terug naar de pagina **[!UICONTROL Adobe IMS Technical Account Configuration]** die u eerder geopend hebt gelaten. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Next]** om de pagina **[!UICONTROL Account]** in het venster **[!UICONTROL Adobe IMS Technical Account Configuration]** te openen.

   (Als u de pagina eerder hebt gesloten, gaat u terug naar de auteur van de Experience Manager en navigeert u naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Selecteer **[!UICONTROL Create]**. Selecteer in de vervolgkeuzelijst **[!UICONTROL Cloud Solution]** de optie **[!UICONTROL Experience Platform Tags]**. Selecteer in de vervolgkeuzelijst **[!UICONTROL Certificate]** de naam van het eerder gemaakte certificaat.)

   ![2019-07-25_20-57-50](assets/2019-07-25_20-57-50.png)

   Adobe IMS Technical Account Configuration - Certificate page.

1. De **[!UICONTROL Account]** pagina heeft vijf gebieden die u moet invullen gebruikend informatie van de de detailpagina van de Integratie van de vorige stap.

   ![2019-07-25_20-42-45](assets/2019-07-25_20-42-45.png)

   Adobe IMS Technical Account Configuration - Account page.

1. Vul op de pagina **[!UICONTROL Account]** de volgende velden in:

   * **[!UICONTROL Title]** - Voer een beschrijvende accounttitel in.
   * **[!UICONTROL Authorization Server]** - Ga terug naar de pagina met integratiegegevens die u eerder hebt geopend. Selecteer het tabblad **[!UICONTROL JWT]**. Kopieer de servernaam, zonder het pad, zoals hieronder gemarkeerd.

(De servernaam is alleen een voorbeeld)   Ga terug naar de pagina **[!UICONTROL Account]** en plak de naam in het desbetreffende veld.
Bijvoorbeeld `https://ims-na1.adobelogin.com/`
(De servernaam is alleen een voorbeeld)

   ![2019-07-25_15-01-53](assets/2019-07-25_15-01-53.png)

   Detailpagina voor integratie - tabblad JWT

1. **[!UICONTROL API Key]** - Ga terug naar de pagina met integratiedetails. Selecteer de tab **[!UICONTROL Overview]** en selecteer **[!UICONTROL Copy]** rechts van het veld **[!UICONTROL API Key (Client ID)]**.

   Ga terug naar de pagina **[!UICONTROL Account]** en plak de toets in het desbetreffende veld.

   ![2019-07-25_14-35-33](assets/2019-07-25_14-35-333.png)

   Pagina met integratiegegevens.

1. **[!UICONTROL Client Secret]** - Ga terug naar de pagina met integratiedetails. Selecteer **[!UICONTROL Retrieve Client Secret]** op het tabblad **[!UICONTROL Overview]**. Selecteer **[!UICONTROL Copy]** rechts van het veld **[!UICONTROL Client secret]**.

   Ga terug naar de pagina **[!UICONTROL Account]** en plak de toets in het desbetreffende veld.

1. **[!UICONTROL Payload]** - Ga terug naar de pagina met integratiedetails. Kopieer op het tabblad **[!UICONTROL JWT]** in het veld JWT Payload de gehele JSON-objectcode.

   Ga terug naar de pagina **[!UICONTROL Account]** en plak de code in het desbetreffende veld.

   ![2019-07-25_21-59-12](assets/2019-07-25_21-59-12.png)

   Pagina met integratiegegevens - tabblad JWT

   De pagina Account, met alle velden ingevuld, ziet er ongeveer als volgt uit:

   ![2019-07-25_22-08-30](assets/2019-07-25_22-08-30.png)

1. Selecteer **[!UICONTROL Create]** in de rechterbovenhoek van de pagina **[!UICONTROL Account]**.

   Met gevormde Experience Manager IMS, hebt u nu een nieuwe die IMSArekening onder **[!UICONTROL Adobe IMS Configurations]** wordt vermeld.

   ![image2019-7-15_14-17-54](assets/image2019-7-15_14-17-54.png)

## Cloud met Experience Platform Tags configureren voor integratie {#configuring-adobe-launch-cloud-for-the-integration}

1. In de auteur van de Experience Manager, dichtbij de upper-left hoek, selecteer **[!UICONTROL Tools]** pictogram (hamer), dan ga naar **[!UICONTROL Cloud Services]** > **[!UICONTROL Experience Platform Tags Configurations]**.

   ![2019-07-26_12-10-38](assets/2019-07-26_12-10-38.png)

1. Selecteer op de pagina **[!UICONTROL Experience Platform Tags Configurations]** in het linkerdeelvenster een site van een Experience Manager waarop u de configuratie van de Experience Platform Tags wilt toepassen.

   Alleen voor voorbeelddoeleinden wordt de **`We.Retail`**-site geselecteerd in de onderstaande schermafbeelding.

   ![2019-07-26_12-20-06](assets/2019-07-26_12-20-06.png)

1. Selecteer **[!UICONTROL Create]** in de linkerbovenhoek van de pagina.
1. Vul op de pagina **[!UICONTROL General]** (1/3 pagina&#39;s) van het venster **[!UICONTROL Create Experience Platform Tags Configuration]** de volgende velden in:

   * **[!UICONTROL Title]** - Voer een beschrijvende configuratitel in. Bijvoorbeeld, `We.Retail Tags cloud configuration`.

   * **[!UICONTROL Associated Adobe IMS Configuration]** - Selecteer de configuratie IMS die u eerder in  [Configure Experience Manager IMS](#configuring-aem-ims) creeerde.

   * **[!UICONTROL Company]** - Selecteer uw Experience Cloud bedrijf in de  **[!UICONTROL Company]** vervolgkeuzelijst. De lijst wordt automatisch gevuld.

   * **[!UICONTROL Property]** - Selecteer in de vervolgkeuzelijst Eigenschap de eigenschap Experience Platform-tags die u eerder hebt gemaakt. De lijst wordt automatisch gevuld.
   Nadat u alle velden hebt ingevuld, ziet uw **[!UICONTROL General]**-pagina er ongeveer als volgt uit:

   ![image2019-7-15_14-34-23](assets/image2019-7-15_14-34-23.png)

1. Selecteer **[!UICONTROL Next]** in de linkerbovenhoek.
1. Vul op de pagina **[!UICONTROL Staging]** (2/3 pagina&#39;s) van het venster **[!UICONTROL Create Experience Platform Tags Configuration]** het volgende veld in:

   Controleer in het veld **[!UICONTROL Library URI]** (Uniform Resource Identifier) de locatie van de testversie van de Experience Platform Tags-bibliotheek. Experience Manager vult dit veld automatisch in.

   Alleen voor de doeleinden van deze stap worden bibliotheken met tags voor Experience Platforms gebruikt die worden ge??mplementeerd op Adobe CDN.

   >[!NOTE]
   >
   >Controleer of de automatisch gevulde bibliotheek-URI (Uniform Resource Identifier) niet onjuist is samengesteld. Herstel indien nodig de URL zodanig dat deze een protocol-relatieve URI vertegenwoordigt. Dat wil zeggen dat het begint met een dubbele slash.
   >
   >
   >Bijvoorbeeld: `//assets.adobetm.com/launch-xxxx`.

   De **[!UICONTROL Staging]** pagina lijkt waarschijnlijk op het volgende: De opties **[!UICONTROL Archive]** en **[!UICONTROL Load Library Asynchronously]** zijn ***not*** ingesteld:

   ![image2019-7-15_15-21-8](assets/image2019-7-15_15-21-8.png)

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek.
1. Herstel, indien nodig, de automatisch gevulde productie-URI op de pagina **[!UICONTROL Production]** (3/3 pagina&#39;s) van het venster **[!UICONTROL Create Experience Platform Tags Configuration]** op ongeveer dezelfde manier als op de vorige pagina **[!UICONTROL Staging]**.
1. Selecteer **[!UICONTROL Create]** in de rechterbovenhoek.

   Uw nieuwe Configuratie van de Codes Cloud van het Experience Platform wordt nu gecreeerd en naast uw website vermeld gelijkend op het volgende voorbeeld:

1. Selecteer uw nieuwe Configuratie van de Codes van de Wolk van het Experience Platform (een vinkje verschijnt links van de configuratietaak wanneer het wordt geselecteerd). Selecteer **[!UICONTROL Publish]** op de werkbalk.

   ![image2019-7-15_15-47-6](assets/image2019-7-15_15-47-6.png)

Momenteel biedt de auteur van de Experience Manager geen ondersteuning voor de integratie van Dynamic Media Viewers met Experience Platform-tags.

Deze wordt echter wel ondersteund in het publicatieknooppunt Experience Manager. Gebruikend de standaardinstellingen van de Configuratie van de Wolk van de Markeringen van het Experience Platform, gebruikt de Experience Manager publicatieknooppunt de productiemilieu van de Markeringen van het Experience Platform. Daarom is het noodzakelijk om de bibliotheekupdates van de Markeringen van het Experience Platform van Ontwikkeling tot aan het milieu van de Productie elke keer tijdens de test te duwen.

Het is mogelijk om deze beperking te omzeilen. Geef de ontwikkelings- of staging-URL van de bibliotheek met Platform-tags op in de Cloud-configuratie voor Experience Platform-tags voor het publicatieknooppunt hierboven voor de Experience Manager. Dit maakt de Experience Manager publicatieknooppunt gebruiken de versie van de Markeringen van het Experience Platform van de Ontwikkeling of van het Staging van.

Zie [Experience Manager met de Markeringen van het Experience Platform door middel van  [!DNL Adobe I/O]](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html) voor meer informatie over de Configuratie van de Wolk van de Markeringen van het Experience Platform.
