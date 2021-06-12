---
title: Interactieve afbeeldingen
description: Leer hoe u met interactieve afbeeldingen werkt in Dynamic Media
uuid: 0bdb73f7-6ce9-4cdf-b6b5-a4d3d4e19a23
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: a6f58f6a-015a-4ced-941c-ef1b6d3e1d6f
docset: aem65
feature: Interactieve afbeeldingen
role: Business Practitioner, Administrator
exl-id: 8a609024-e9e6-4805-8306-48d095110eb6
source-git-commit: 3110c1d4424179dbc9eda9e07cf3353c4b4bb4b0
workflow-type: tm+mt
source-wordcount: '4256'
ht-degree: 1%

---

# Interactieve afbeeldingen{#interactive-images}

U kunt statische afbeeldingen eenvoudig verrijken en aantrekkelijke ervaringen voor klanten creëren door &#39;onoverzichtelijke&#39; hotspots naar een afbeelding te slepen. Slepbare hotspots combineren aanvullende informatie over een product of service met een directe, verkooppuntfunctie &#39;Toevoegen aan winkelwagentje&#39; of &#39;Kopen&#39;. Klanten kunnen op deze hotspots tikken of erop klikken en deze rechtstreeks aan het product of de service koppelen, ze aan een winkelwagentje toevoegen of aan een webpagina koppelen. Directe ervaringen zoals deze verhogen de betrokkenheid van klanten en conversies op uw website.

Hieronder ziet u een blaasbare banner met een pop-upvenster van QuickView. Een gebruiker activeert de Snelle weergave door op de cirkel of de hotspot op het model te tikken.

![chlimage_1-152](assets/chlimage_1-368.png)

Bekijk de volgende interactieve afbeeldingen in actie op de bovenstaande webpagina:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## Bekijk hoe u interactieve afbeeldingsbanners {#watch-how-interactive-image-banners-are-created} maakt

Speel een analyse op [hoe de interactieve beeldbanners worden gecreeerd](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 minuten en 33 seconden). U leert ook hoe u interactieve afbeeldingsbanners kunt voorvertonen, bewerken en leveren.

## Snel starten: Interactieve afbeeldingen {#quick-start-interactive-images}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met interactieve afbeeldingen in Adobe Experience Manager Assets.

Zoek naar **Voorbeeld** rubriek binnen enkele taken van het Snelle Begin. Het bevat een korte zelfstudie die is gebaseerd op het volgende webpaginavoorbeeld waaraan nog geen interactieve afbeeldingen zijn toegevoegd:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

De zelfstudie helpt u de stappen te illustreren voor het integreren van interactieve afbeeldingen op uw eigen website.

Stappen voor interactieve afbeeldingen:

1. **(Optioneel) Hotspot-variabelen**  identificeren - Als u Experience Manager Assets en Dynamic Media standalone gebruikt, begint u met het identificeren van dynamische variabelen die worden gebruikt in uw bestaande Quickview-implementatie. Vervolgens kunt u hotspotgegevens invoeren wanneer u de interactieve afbeelding maakt. Zie [(Optioneel) Hotspot-variabelen identificeren](#optional-identifying-hotspot-variables).
Als u echter Adobe Experience Manager Sites of Adobe Experience Manager eCommerce gebruikt, of beide, is deze stap niet nodig.
Zie [eCommerce-concepten in Experience Manager Assets](/help/commerce/cif-classic/administering/concepts.md).

1. **(Optioneel) Een voorinstelling**  voor een interactieve afbeeldingsviewer maken - Pas de afbeelding aan die wordt gebruikt om hotspots te vertegenwoordigen. Het is niet nodig een eigen voorinstelling voor de interactieve afbeeldingsviewer te maken als u de voorinstelling `Shoppable_Banner` in plaats daarvan wilt gebruiken die buiten de box is ingesteld met de naam Interactive Image Viewer.
Zie [(Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken](/help/assets/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Uploading an image banner**  - Upload afbeeldingsbanners die u interactief wilt maken.
Zie [Een afbeeldingsbanner uploaden](#uploading-an-image-banner).

1. **Hotspots toevoegen aan een afbeeldingsbanner**  - Voeg een of meer hotspots toe aan een afbeeldingsbanner en koppel deze aan een handeling zoals een hyperlink, een Snelle weergave of een ervaringsfragment. Nadat u hotspots hebt toegevoegd, kunt u deze taak voltooien door de interactieve afbeelding te publiceren.

   * Zie [Hotspots toevoegen aan een afbeeldingsbanner](#adding-hotspots-to-an-image-banner).
   * Zie [Interactieve afbeeldingen voorvertonen](#optional-previewing-interactive-images) - Optioneel. U kunt desgewenst een representatie van de verscherpte banner bekijken en de interactiviteit ervan testen.
   * Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van interactieve afbeeldingselementen.

1. **Een interactieve afbeelding in Experience Manager**  toevoegen aan uw website of website - Als u Sites of eCommerce gebruikt of beide, kunt u de interactieve afbeelding toevoegen aan een webpagina in Experience Manager. Sleep de component Interactieve media naar de pagina. Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).

   Als u de Elementen van de Experience Manager en Dynamic Media standalone gebruikt, moet u de ingebedde code op uw website kopiëren en dan het integreren met uw bestaande Snelle mening. Zie [Een interactieve afbeelding integreren met uw website](#integrating-an-interactive-image-with-your-website).

   Als u een externe WCM (Web Content Manager) gebruikt, moet u de nieuwe interactieve video integreren met de bestaande implementatie van de Snelle weergave die op uw website wordt gebruikt. Zie [Een interactieve afbeelding integreren met een bestaande QuickView](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optioneel) Hotspotvariabelen {#optional-identifying-hotspot-variables} identificeren

>[!NOTE]
>
>Deze taak is alleen vereist als aan de volgende voorwaarden wordt voldaan:
>
>* U wilt interactiviteit aan uw beeld toevoegen door aan Snelle meningen te teweegbrengen.
>* Uw implementatie van Experience Manager maakt *niet* gebruik van een eCommerce-integratieframework om productgegevens vanuit elke eCommerce-oplossing, zoals IBM® WebSphere® Commerce, Elastic Path, hybris of Intershop, naar de Experience Manager te halen. Zie [eCommerce-concepten in Experience Manager Assets](/help/commerce/cif-classic/administering/concepts.md).

>
>
Als uw implementatie van Experience Manager eCommerce gebruikt, kunt u deze taak overslaan en aan de volgende taak te werk gaan.

Begin door dynamische variabelen te identificeren die door uw bestaande implementatie van QuickView worden gebruikt zodat u hotspot gegevens kunt ingaan om het interactieve beeld tot stand te brengen.

Wanneer u hotspots toevoegt aan een bannerafbeelding in Experience Manager Assets, moet u een SKU (Stock Keeping Unit en optionele extra variabelen aan elke hotspot toewijzen. Dergelijke hotspotvariabelen worden later gebruikt om hotspots aan te passen aan Quickview-inhoud.

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot gegevens te associëren. Elke hotspot die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie bevatten om het product ondubbelzinnig te identificeren in het bestaande back-endsysteem.

Er zijn verschillende manieren om een set variabelen te identificeren die voor hotspot-gegevens moet worden gebruikt.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande implementatie van QuickView. IT-specialisten zullen waarschijnlijk weten wat de minimale gegevensverzameling is die vereist is voor de identificatie van QuickView in het systeem. Het is echter ook mogelijk om eenvoudig het bestaande gedrag van de front-end code te analyseren.

De meeste implementaties van de Snelle mening gebruiken het volgende paradigma:

* De gebruiker activeert een gebruikersinterface-element op de website. Klik bijvoorbeeld op een knop Snelle weergave.
* De website verzendt een Ajax-aanvraag naar de achterkant om de Quickview-gegevens of -inhoud te laden, indien nodig.
* De Quickview-gegevens worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie QuickView is geïmplementeerd. Vervolgens activeert u de QuickView en legt u de Ajax-URL vast die per webpagina is verzonden voor het laden van de Quickview-gegevens of -inhoud.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Om alle uitgaande HTTP- verzoeken in Google Chrome te zien, druk F12 om het paneel van Hulpmiddelen van de Ontwikkelaar te openen, en dan het lusje van het Netwerk te klikken.
Druk op een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en klik vervolgens op het tabblad Netwerk.

* In Firefox kunt u de Firebug-plug-in activeren door op F12 te drukken en het tabblad Net te gebruiken. U kunt ook het ingebouwde controllergereedschap en het bijbehorende tabblad Netwerk gebruiken.
Druk op een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en klik vervolgens op het tabblad Inspecteur.

Wanneer netwerkcontrole in browser wordt aangezet, teweeg de Snelle mening op de pagina.

Zoek nu de URL van Quickview Ajax in het netwerklogboek en kopieer de geregistreerde URL voor toekomstige analyse. Gewoonlijk, wanneer u de Quickview teweegbrengt zijn er talrijke verzoeken die naar de server worden verzonden. De URL van Quickview Ajax is doorgaans een van de eerste in de lijst. Het heeft of een complex gedeelte van het vraagkoord of weg, en zijn reactieMIME type of `text/html`, `text/xml`, of `text/javascript` is.

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat URL&#39;s in de Snelle weergave onderdelen kunnen bevatten die algemeen gelden voor een bepaalde categorie websites, maar deze alleen kunnen wijzigen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval, is het enige veranderlijke deel in Quickview URL productSKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter naast de SKU verschillende elementen, zoals categorie-id, kleurcode en code voor de grootte. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot-gegevens in de functie voor onoverzichtbare interactieve afbeeldingen in Experience Manager Assets.

Bekijk de volgende voorbeelden van URL&#39;s van QuickView en de resulterende hotspot-variabelen:

<table>
  <tbody>
  <tr>
    <td><p>Enige SKU, die in het vraagkoord wordt gevonden.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Het enige veranderlijke deel in URL is de waarde van de productId= parameter van het vraagkoord, en het is duidelijk een waarde SKU. Daarom hebben uw hotspots alleen SKU-velden nodig die zijn gevuld met waarden als <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>Eén SKU, gevonden in het URL-pad.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van de hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU en categorie-id in de queryreeks.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. De SKU wordt opgeslagen in de <code>prodId</code> parameter en de categorie ID<code></code> wordt opgeslagen in de <code>category=</code> parameter.</p> <p>Daarom zijn de hotspot-definities paren. Dat wil zeggen, een SKU-waarde en een extra variabele met de naam <code>categoryId</code>. De resulterende paren zijn:</p>
    <ul>
      <li><p>SKU is <strong><code>305466</code></strong> en <code>categoryId</code> is <code>1100004</code>.</p> </li>
      <li><p>SKU is <strong><code>310181</code></strong> en <code>categoryId</code> is <strong><code>1100004</code></strong>.</p> </li>
      <li><p>SKU is <strong><code>308706</code></strong> en <code>categoryId</code> is <strong><code>1740148</code></strong>.</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Voorbeeld**

U kunt dezelfde aanpak toepassen als in de drie bovenstaande voorbeelden op de demo-webpagina:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

De demo-webpagina heeft verschillende productminiaturen, elk met een Quickview-knop met het label &quot;Meer weergeven&quot;. Terwijl het foutopsporingsprogramma van uw webbrowser nog is geactiveerd, klikt u op elke knop en noteert u de opgenomen URL&#39;s van de Snelle weergave. Nadat u alle vier de productenQuickviews beschikbaar op de pagina activeert, hebt u de volgende lijst verzoeken van de Snelle mening die aan het achterste eind worden gemaakt:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wanneer u de serveraanroepen bekijkt, ziet u dat productspecifieke informatie alleen aanwezig is in het aanvraagpad. U merkt ook op dat het vraagkoord helemaal niet wordt gebruikt en er zijn twee verschillende types van betrokken gegevensstukken:

* Het eerste type is Men of Vrouwen. Je kunt deze &#39;productcategorie&#39; noemen.
* Het tweede type is productnaam, zoals CamoPullover. U kunt veronderstellen dat deze informatie product SKU is.

Op basis van deze informatie heeft de volledige URL van de Snelle weergave het volgende patroon:

`/datafeed/$categoryId$-$SKU$.json`

Op basis van een dergelijke analyse gebruikt u `categoryId` en `SKU` voor hotspots.

U kunt nu een afbeeldingsbanner uploaden en er hotspots aan toevoegen met de functie voor onoverzichtelijke interactieve afbeeldingen in Experience Manager Assets.

## (Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken {#optional-creating-an-interactive-image-viewer-preset}

U kunt ervoor kiezen om de standaardvoorinstelling `Shoppable_Banner` voor de Interactieve afbeeldingsviewer buiten de box te gebruiken die wordt geleverd bij Experience Manager Assets. U kunt ook uw eigen aangepaste viewer-voorinstelling maken voor gebruik met interactieve afbeeldingen.

Wanneer u een aangepaste voorinstelling voor een interactieve afbeeldingsviewer maakt, kunt u de weergave van hotspots in de afbeeldingsbanner bepalen. Als onderdeel van het maken van de viewervoorinstelling kunt u een hotspot-afbeelding uit een galerie met vooraf gedefinieerde afbeeldingen gebruiken.

Nadat u de viewervoorinstelling hebt opgeslagen, wordt deze automatisch geactiveerd (ingeschakeld) op de pagina met de lijst met voorinstellingen voor viewer in Experience Manager Assets. Deze functionaliteit houdt in dat het zichtbaar is in de Interactieve component van Media en wanneer u activa bekijkt. Als u *echter een interactieve banner met deze viewervoorinstelling wilt leveren, moet u* ook *uw viewervoorinstelling publiceren.* Deze regel geldt voor aangepaste of uit-van-box viewer-voorinstellingen.

**Een voorinstelling voor een interactieve afbeeldingsviewer maken:**

1. Tik in de linkerspoorstaaf op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Create]**.
1. Typ in het dialoogvenster Nieuwe voorinstelling voor viewer een naam om de voorinstelling voor de interactieve bannerviewer te beschrijven.

   Nadat u de titel hebt opgeslagen, wordt deze weergegeven in de lijstpagina Voorinstelling viewer.

1. Selecteer in het vervolgkeuzemenu Uitgebreid mediatype de optie **[!UICONTROL Interactive Image]**.
1. Tik op **[!UICONTROL Create]**.
1. Tik op het tabblad **[!UICONTROL Appearance]** op de pagina Voorinstelling viewer bewerken.
1. Voer een van de volgende handelingen uit:

   * Tik op het pictogram Asset Picker om uw eigen hotspot-afbeelding te uploaden die u voor afbeeldingen wilt gebruiken. Navigeer op de pagina Inhoud selecteren naar de gewenste hotspot-afbeelding, selecteer deze en tik op het pictogram Markeren controleren in de rechterbovenhoek.
   * Tik op het pictogram Hotspot-galerie om een vooraf gedefinieerde hotspot-afbeelding te selecteren. Tik in het palet van de hotspot op de hotspot die u wilt gebruiken.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]**.

   Zorg ervoor dat u de nieuwe viewervoorinstelling publiceert.

   Zie [Voorinstellingen voor viewers publiceren die u hebt toegevoegd](/help/assets/managing-viewer-presets.md#publishing-viewer-presets).

   U kunt nu een afbeeldingsbanner uploaden.

## Een afbeeldingsbanner {#uploading-an-image-banner} uploaden

Als u de afbeeldingen die u wilt gebruiken al hebt geüpload, gaat u naar de volgende stap [Hotspots toevoegen aan een afbeeldingsbanner](#adding-hotspots-to-an-image-banner).

**Een afbeeldingsbanner uploaden:**

1. Upload afbeeldingsbanners die u interactief wilt maken.

   Zie [Elementen uploaden](/help/assets/manage-assets.md#uploading-assets).

   U kunt nu hotspots toevoegen aan de afbeeldingsbanner. zie de volgende taak hieronder.

## Hotspots toevoegen aan een afbeeldingsbanner {#adding-hotspots-to-an-image-banner}

U kunt hotspots toevoegen aan een afbeeldingsbanner met de editor op de pagina Hotspot-beheer.

Wanneer u hotspots toevoegt, kunt u deze definiëren als een pop-upweergave in QuickView, als een hyperlink of als een Experience-fragment.

Zie [Fragmenten ervaren](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Om dit probleem te verhelpen, kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw interactieve afbeelding, kunt u Voorvertoning gebruiken om een voorstelling te zien van hoe uw interactieve afbeelding eruit ziet voor klanten.

Zie [(Optioneel) Interactieve afbeeldingen voorvertonen](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wanneer u hotspots toevoegt aan een afbeelding in een interactieve afbeelding of een carrouselbanner, worden de hotspotgegevens opgeslagen op dezelfde metagegevenslocatie. Deze locatie is relatief ten opzichte van de locatie van de afbeelding, ongeacht of het een interactieve afbeelding of een carrouselbanner betreft. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.
Carrouselbanners ondersteunen afbeeldingen met hyperlinks op afbeeldingen die ook hotspots kunnen bevatten. en Interactieve afbeeldingen niet. Houd deze regel in gedachten als u een interactieve afbeelding of Carousel Banner wilt maken die dezelfde afbeelding gebruikt. U kunt interactieve afbeeldingen en carrouselbanners maken met afzonderlijke kopieën van dezelfde afbeelding.
Zie ook [Carrouselbanners](/help/assets/carousel-banners.md).

>[!NOTE]
Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

**Hotspots toevoegen aan een afbeeldingsbanner:**

1. Navigeer in de weergave Elementen naar de afbeeldingsbanner die u interactief wilt maken.
1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Select]** (vinkpictogram) op de afbeelding. Tik op **[!UICONTROL Edit]** op de werkbalk.

   * Tik op **[!UICONTROL More actions]** (drie punts pictogram) **[!UICONTROL Edit]**.

   * Tik op de afbeelding zodat u deze kunt openen op de pagina Gedetailleerde weergave. Tik op **[!UICONTROL Edit]** op de werkbalk.

1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL Add Hotspot]** (vingertikpictogram) om de pagina Hotspotbeheer te openen.
1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL Hotspot]**.

   1. Tik in de linkerbovenhoek van de pagina Hotspot Management op **[!UICONTROL Hotspot]**.
   1. Tik in de afbeelding op een locatie waar u de hotspot wilt weergeven. Sleep indien nodig de hotspot om de locatie ervan aan te passen.
   1. Voeg desgewenst extra hotspots toe door de stappen a en b te herhalen.
   1. (Optioneel) Als u een hotspot wilt verwijderen, selecteert u de hotspot in de afbeelding en tikt u op **[!UICONTROL Delete]** (trashcan-pictogram) onder de kop **[!UICONTROL Hotspots]**.

1. Typ in het tekstveld Naam de naam van de hotspot. Deze naam wordt ook weergegeven in de vervolgkeuzelijst Geselecteerde hotspot.
1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Quickview]**.

      * Tik of klik op het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen als u een Experience Manager- of eCommerce-klant bent. Tik of klik op het product dat u wilt gebruiken en tik op **[!UICONTROL Select]** in de rechterbovenhoek van de pagina zodat u terug kunt keren naar de pagina Hotspot-beheer.
      * Als u *not* een klant van de Experience Manager of van de eCommerce bent

         * Zie [Hotspot-variabelen identificeren](#optional-identifying-hotspot-variables); U moet deze variabelen definiëren.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU (Stock Keeping Unit) van het product. Dit is een unieke id voor elk afzonderlijk product of elke service die u aanbiedt. De ingegaan waarde van SKU bevolkt automatisch het veranderlijke gedeelte van het malplaatje van de Snelle mening zodat het systeem weet om geëtteerde hotspot met een bepaalde Snelle mening van SKU te associëren.
         * (Optioneel) Tik op **[!UICONTROL Add Generic Variable]** als er andere variabelen in de Snelle weergave zijn die u moet gebruiken om een product verder te identificeren. Geef in het tekstveld een extra variabele op. `category=Mens` is bijvoorbeeld een toegevoegde variabele.
   * Tik op **[!UICONTROL Hyperlink]**.

      * Als u een klant van de Plaatsen van de Experience Manager bent, tik of klik het pictogram van de Selecteur van de Plaats (omslag) om aan een URL te navigeren. De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.
      * Als u een zelfstandige klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md) voor meer informatie.

   * Tik op **[!UICONTROL Experience Fragment]**.

      * Als u een klant van de Plaatsen van de Experience Manager bent, tik of klik het pictogram van het Onderzoek (vergrootglas) om de pagina van het Fragment van de Ervaring te openen. Tik op het ervaringsfragment dat u wilt gebruiken en tik vervolgens op **[!UICONTROL Select]** in de rechterbovenhoek van de pagina zodat u terug kunt keren naar de pagina Hotspot-beheer.
Zie [Fragmenten ervaren](/help/sites-authoring/experience-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals u het wilt weergeven op de banner.

         >[!NOTE]
         De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Om dit probleem te verhelpen, kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.



1. Tik **[!UICONTROL Save]** om uw werk op te slaan en terug te keren naar de pagina Bladeren.
1. Publiceer de interactieve afbeelding. Met publicatie kan de banner via de cloud worden geleverd en wordt ook insluitcode gegenereerd als u wilt integreren met een website van derden.

   Zie [Elementen publiceren](/help/assets/manage-assets.md#publishing-assets).

   Nadat u hotspots hebt toegevoegd en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande website.

   Zie [Een interactieve afbeelding integreren met uw website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

### (Optioneel) Interactieve afbeeldingen voorvertonen {#optional-previewing-interactive-images}

Met Voorvertoning kunt u zien hoe uw interactieve afbeelding eruit ziet en kunt u de hotspots van de afbeelding testen om te controleren of deze zich naar behoren gedragen.

Als u tevreden bent met de interactieve afbeelding, kunt u deze publiceren.
Zie [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md).
Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.
Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).

**Een voorvertoning weergeven van interactieve afbeeldingen:**

1. Navigeer in de weergave Middelen naar een bestaande, door u gemaakte interactieve afbeelding en tik erop om deze te openen in Voorvertoning.
1. Tik in de vervolgkeuzelijst Inhoud in de linkerbovenhoek van de voorvertoningspagina op **[!UICONTROL Viewers]**.
1. Tik in de lijst Viewers op **[!UICONTROL Shoppable_Banner]** of de naam van de voorinstelling voor de interactieve afbeeldingsviewer die u hebt gemaakt.
1. Tik op hotspots in de afbeelding als u de bijbehorende handelingen wilt testen.

## Interactieve afbeeldingselementen publiceren {#publishing-interactive-image-assets}

Zie [Elementen publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van interactieve afbeeldingselementen.

## Een interactieve afbeelding integreren met uw website {#integrating-an-interactive-image-with-your-website}

Nadat u een bannerafbeelding hebt geüpload, hotspots hebt toegevoegd aan de afbeelding en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw websitepagina.

Als u een klant van de Plaatsen van de Experience Manager bent, kunt u het interactieve beeld toevoegen door de Interactieve component van Media op uw pagina te slepen. Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).

Als u een zelfstandige klant van de Middelen van de Experience Manager bent, kunt u het interactieve beeld aan uw website manueel toevoegen zoals die in deze sectie wordt beschreven.

1. Kopieer de insluitcode van de gepubliceerde interactieve afbeelding.
Zie [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md).

1. Voeg de gekopieerde insluitcode toe op de gewenste locatie op de webpagina.
De gekopieerde insluitcode wordt ingesteld voor een responsieve omgeving, zodat deze automatisch in het toegewezen gebied past.

**Voorbeeld**

De demo-website als voorbeeld gebruiken:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

Het beeld van de drie mannen is een statische `IMG`-tag:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Integratie is zo eenvoudig als het verwijderen van de tag `IMG` en het vervangen door de gekopieerde insluitcode uit Experience Manager Assets. Het resultaat wordt weergegeven in de volgende URL, die de mogelijk onjuiste interactieve afbeelding op de pagina met drie hotspots per cirkel weergeeft:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
De hotspots op de schopbare interactieve afbeelding van de demo-website zijn dan alleen bedoeld voor weergave. zij zijn nog niet geïntegreerd met de bestaande Snelle meningen.

Als u een &#39;uitsnijding&#39; wilt toepassen op een verwisselbare interactieve afbeelding voor een responsieve omgeving, kunt u het configuratiekenmerk Interactive Image `ZoomView.iscommand` toevoegen aan het pad. De component `ZoomView` wordt aangeroepen en `iscommand` is de opdracht voor het leveren van de &quot;uitsnijdafbeelding&quot; die u toepast.

Zie [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html) configuratiekenmerk.

Zie [opdracht Uitsnijden](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html) afbeelding weergeven.

U bent nu klaar om de interactieve afbeelding te integreren met een bestaande QuickView op uw website.

## Een interactieve afbeelding integreren met een bestaande QuickView {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
Deze taak is slechts van toepassing als u een stand-alone klant van de Activa van de Experience Manager bent.

De laatste stap in dit proces is het integreren van de interactieve afbeelding met een bestaande Quickview-implementatie op uw website. Er is geen oplossing voor de integratie die in alle gevallen werkt. Elke implementatie van Quickview is uniek en een specifieke benadering is nodig. Het gaat waarschijnlijk om de hulp van een front-end IT-persoon.

De bestaande implementatie van QuickView vertegenwoordigt normaal gesproken een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een Quickview URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een Ajax- verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achterste logica keert de overeenkomstige gegevens of inhoud van de Snelle mening terug naar de front-end code.
1. De front-end code laadt de gegevens of de inhoud van de Snelle mening.
1. Naar keuze, zet de front-end code de geladen gegevens van de Snelle mening in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm weer voor de eindgebruiker.

Deze aanroepen vertegenwoordigen geen onafhankelijke openbare API-aanroepen die door de webpaginalogica kunnen worden aangeroepen vanuit een willekeurige stap. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Wanneer een gebruiker op een hotspot in de aanpasbare afbeelding klikt, wordt deze gebruikersinteractie door de viewer afgehandeld, terwijl de aanpasbare interactieve afbeelding stap 1 en gedeeltelijk stap 2 vervangt. De viewer retourneert een gebeurtenis naar de webpagina die alle hotspotgegevens bevat die eerder aan Experience Manager Assets zijn toegevoegd.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die wordt uitgegeven door de mogelijk onjuiste interactieve afbeelding.
* Hiermee maakt u een Quickview-URL op basis van de hotspot-gegevens.
* Triggert het proces om de Snelle mening van het achtereind te laden en het terug te geven op het scherm voor vertoning.

De insluitcode die door Experience Manager Assets wordt geretourneerd, heeft al een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd, zoals in het volgende gemarkeerde codefragment wordt getoond:

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : {
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/",
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Het is dus alleen nodig de commentaarmarkering van de code ongedaan te maken en de dummy-handlertekst te vervangen door de code die specifiek is voor de specifieke webpagina.

Het proces voor het samenstellen van de URL van de Snelle weergave is tegengesteld aan het proces voor het identificeren van hotspot-variabelen die eerder zijn behandeld.

Zie [Hotspot-variabelen identificeren](#optional-identifying-hotspot-variables).

Met behulp van de vorige URL-voorbeelden van Quickview kunt u in de volgende voorbeelden zien hoe de URL van de QuickView in elk geval wordt samengesteld:

<table>
 <tbody>
  <tr>
   <td><p>Single SKU, gevonden in het vraagkoord</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>Enkele SKU, gevonden in het pad URL</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>SKU en categorie-id in de queryreeks</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td>
  </tr>
 </tbody>
</table>

De laatste stap om de Quickview URL teweeg te brengen en het paneel van de Snelle mening te activeren vereist hoogstwaarschijnlijk de hulp van een front-end persoon van IT van uw afdeling van IT. Zij hebben de kennis om het best te weten hoe te om de implementatie van de Snelle mening van de juiste stap nauwkeurig teweeg te brengen, die een klaar-aan-gebruiksKickview URL hebben.

U kunt zien hoe deze stappen worden toegepast op de demo-website om een onoverzichtelijke interactieve afbeelding volledig te integreren met de Quickview-code. Eerder werd de structuur van de URL van de Snelle weergave als volgt geïdentificeerd:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Als u deze URL wilt reconstrueren binnen de handler `quickViewActivate`, kunt u de velden `categoryId` en `SKU` gebruiken die beschikbaar zijn in het object `inData` dat door de code van de viewer aan de handler wordt doorgegeven:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

De demowebsite activeert het dialoogvenster Snelle weergave met een eenvoudige functieaanroep `loadQuickView()`. Deze functie heeft slechts één argument, namelijk de gegevens-URL van de Snelle weergave. Als dusdanig, is de laatste stap om het shoppable interactieve beeld te integreren de volgende lijn van code aan `quickViewActivate` manager toe te voegen:

```xml
loadQuickView(quickViewUrl);
```

Hier volgt de volledige broncode:

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : {
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    },
   });
 s7interactiveimageviewer.init();
```

De laatste demo-website met de volledig geïntegreerde interactieve afbeelding ziet er als volgt uit:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html)

## Quickviews gebruiken om aangepaste pop-ups te maken {#using-quickviews-to-create-custom-pop-ups}

Zie [Aangepaste pop-ups maken met Quickviews](/help/assets/custom-pop-ups.md).
