---
title: Interactieve afbeeldingen
description: Leer hoe u met interactieve afbeeldingen werkt in Dynamic Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: Interactive Images
role: User, Admin
exl-id: 8a609024-e9e6-4805-8306-48d095110eb6
solution: Experience Manager, Experience Manager Assets
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '4098'
ht-degree: 0%

---

# Interactieve afbeeldingen{#interactive-images}

U kunt statische afbeeldingen eenvoudig verrijken en aantrekkelijke ervaringen voor klanten creëren door &#39;onoverzichtelijke&#39; hotspots naar een afbeelding te slepen. Slepbare hotspots combineren aanvullende informatie over een product of service met een directe, verkooppuntfunctie &#39;Toevoegen aan winkelwagentje&#39; of &#39;Kopen&#39;. Klanten kunnen deze hotspots selecteren en rechtstreeks aan het product of de service worden gekoppeld, deze aan een winkelwagentje toevoegen of aan een webpagina worden gekoppeld. Directe ervaringen zoals deze verhogen de betrokkenheid van klanten en conversies op uw website.

Hieronder ziet u een blaasbare banner met een pop-upvenster van QuickView. Een gebruiker activeert de Snelle weergave door de cirkel of de hotspot op het model te selecteren.

![ chlimage_1-152 ](assets/chlimage_1-368.png)

Bekijk de volgende interactieve afbeeldingen in actie op de bovenstaande webpagina:

[ https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## Controleren hoe interactieve afbeeldingsbanners worden gemaakt {#watch-how-interactive-image-banners-are-created}

Speel een analyse op [ hoe de interactieve beeldbanners ](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 minuten en 33 seconden) worden gecreeerd. U leert ook hoe u interactieve afbeeldingsbanners kunt voorvertonen, bewerken en leveren.

## Snel starten: Interactieve afbeeldingen {#quick-start-interactive-images}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met interactieve afbeeldingen in Adobe Experience Manager Assets.

Zoek de **rubriek van het Voorbeeld** binnen sommige van de Snelle taken van het Begin. Het bevat een korte zelfstudie die is gebaseerd op het volgende webpaginavoorbeeld waaraan nog geen interactieve afbeeldingen zijn toegevoegd:

[ https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

De zelfstudie helpt u de stappen te illustreren voor het integreren van interactieve afbeeldingen op uw eigen website.

Stappen voor interactieve afbeeldingen:

1. **(Optioneel) Identificeer hotspot-variabelen** - Als u Experience Manager Assets en Dynamic Media zelfstandig gebruikt, begint u met het identificeren van dynamische variabelen die worden gebruikt in uw bestaande Quickview-implementatie. Vervolgens kunt u hotspotgegevens invoeren wanneer u de interactieve afbeelding maakt. Zie [ (Optioneel) Hotspot-variabelen identificeren ](#optional-identifying-hotspot-variables) .
Als u echter Adobe Experience Manager Sites of Adobe Experience Manager eCommerce gebruikt, of beide, is deze stap niet nodig.
Zie [ eCommerce concepten in Experience Manager Assets ](/help/commerce/cif-classic/administering/concepts.md).

1. **(Optioneel) Maak een voorinstelling voor een interactieve afbeeldingsviewer** - Pas de afbeelding aan die wordt gebruikt om hotspots te vertegenwoordigen. U hoeft geen eigen voorinstelling voor de interactieve afbeeldingsviewer te maken als u in plaats daarvan de voorinstelling voor de externe interactieve afbeeldingsviewer met de naam `Shoppable_Banner` wilt gebruiken.
Zie [ (Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken ](/help/assets/managing-viewer-presets.md#creating-a-new-viewer-preset) .

1. **upload een beeldbanner** - upload beeldbanners die u interactief wilt maken.
Zie [ een beeldbanner ](#uploading-an-image-banner) uploaden.

1. **voeg hotspots aan een beeldbanner** toe - voeg één of meerdere hotspots aan een beeldbanner toe en associeer elk met een actie zoals een hyperlink, een Snelle mening, of een Fragment van de Ervaring. Nadat u hotspots hebt toegevoegd, kunt u deze taak voltooien door de interactieve afbeelding te publiceren.

   * Zie [ hotspots aan een beeldbanner ](#adding-hotspots-to-an-image-banner) toevoegen.
   * Zie [ Voorproef interactieve beelden ](#optional-previewing-interactive-images) - Facultatief. U kunt desgewenst een representatie van de verscherpte banner bekijken en de interactiviteit ervan testen.
   * Zie [ Publish Assets ](/help/assets/publishing-dynamicmedia-assets.md) voor details op hoe te om interactieve beeldactiva te publiceren.

1. **voeg een interactief beeld aan uw website** toe - als u Experience Manager Sites of eCommerce, of allebei gebruikt, kunt u het interactieve beeld aan een Web-pagina in Experience Manager toevoegen. Sleep de component Interactieve media naar de pagina. Zie [ Dynamic Media Assets aan Pagina&#39;s ](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.

   Als u Experience Manager Assets en Dynamic Media zelfstandig gebruikt, moet u de insluitcode naar uw website kopiëren en deze vervolgens integreren met uw bestaande Snelle weergave. Zie [ een interactief beeld met uw website ](#integrating-an-interactive-image-with-your-website) integreren.

   Als u een externe WCM (Web Content Manager) gebruikt, moet u de nieuwe interactieve video integreren met de bestaande implementatie van de Snelle weergave die op uw website wordt gebruikt. Zie [ een interactief beeld met een bestaande QuickView ](#integrating-an-interactive-image-with-an-existing-quickview) integreren.

## (Optioneel) Hotspotvariabelen identificeren {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Deze taak is alleen vereist als aan de volgende voorwaarden wordt voldaan:
>
>* U wilt interactiviteit aan uw beeld toevoegen door aan Snelle mening te teweegbrengen.
>* Uw implementatie van Experience Manager gebruikt ** geen eCommerce integratiekader voor het trekken van productgegevens in Experience Manager van om het even welke oplossing van de eHandel zoals IBM® WebSphere® Commerce, Elastic Path, hybris, of Intershop. Zie [ eCommerce concepten in Experience Manager Assets ](/help/commerce/cif-classic/administering/concepts.md).
>
>Als uw implementatie van Experience Manager eCommerce gebruikt, kunt u deze taak overslaan en aan de volgende taak te werk gaan.

Begin door dynamische variabelen te identificeren die door uw bestaande implementatie van QuickView worden gebruikt zodat u hotspot gegevens kunt ingaan om het interactieve beeld tot stand te brengen.

Wanneer u hotspots toevoegt aan een bannerafbeelding in Experience Manager Assets, moet u een SKU (Stock Keeping Unit en optionele extra variabelen aan elke hotspot toewijzen. Dergelijke hotspotvariabelen worden later gebruikt om hotspots te laten overeenkomen met Quickview-inhoud.

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot gegevens te associëren. Elke hotspot die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie bevatten om het product ondubbelzinnig te identificeren in het bestaande back-endsysteem.

Er zijn verschillende manieren om een set variabelen te identificeren die voor hotspot-gegevens moet worden gebruikt.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande implementatie van QuickView. IT-specialisten zullen waarschijnlijk weten wat de minimale gegevensverzameling is die vereist is voor de identificatie van QuickView in het systeem. Het is echter ook mogelijk om eenvoudig het bestaande gedrag van de front-end code te analyseren.

De meeste implementaties van de Snelle mening gebruiken het volgende paradigma:

* De gebruiker activeert een gebruikersinterface-element op de website. Selecteer bijvoorbeeld een knop Snelle weergave.
* De website verzendt een Ajax-aanvraag naar de achterkant om de Quickview-gegevens of -inhoud te laden, indien nodig.
* De Quickview-gegevens worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie QuickView is geïmplementeerd. Vervolgens activeert u de QuickView en legt u de Ajax-URL vast die per webpagina is verzonden voor het laden van de Quickview-gegevens of -inhoud.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Om alle uitgaande HTTP- verzoeken in Google Chrome te zien, druk F12 om het paneel van Hulpmiddelen van de Ontwikkelaar te openen, en dan het lusje van het Netwerk te selecteren.
Druk in een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en selecteer vervolgens het tabblad Netwerk.

* In Firefox kunt u de Firebug-plug-in activeren door op F12 te drukken en het tabblad Net te gebruiken. U kunt ook het ingebouwde controllergereedschap en het bijbehorende tabblad Netwerk gebruiken.
Druk in een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en selecteer vervolgens het tabblad Inspecteur.

Wanneer netwerkcontrole in browser wordt aangezet, teweeg de Snelle mening op de pagina.

Zoek nu de URL van Quickview Ajax in het netwerklogboek en kopieer de geregistreerde URL voor toekomstige analyse. Gewoonlijk, wanneer u de Quickview teweegbrengt zijn er talrijke verzoeken die naar de server worden verzonden. De URL van Quickview Ajax is doorgaans een van de eerste in de lijst. Het heeft een complex gedeelte of pad voor een querytekenreeks en het MIME-type voor reactie is `text/html` , `text/xml` of `text/javascript` .

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat URL&#39;s in de Snelle weergave onderdelen kunnen bevatten die algemeen gelden voor een bepaalde categorie websites, maar deze alleen kunnen wijzigen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval, is het enige veranderlijke deel in Quickview URL productSKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter verschillende elementen die naast de SKU verschillen, zoals categorie-id, kleurcode en code voor de grootte. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot-gegevens in de functie voor onoverzichtelijke interactieve afbeeldingen in Experience Manager Assets.

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
    </ul> <p>Het enige veranderlijke deel in URL is de waarde van de productId= parameter van het vraagkoord, en het is duidelijk een waarde SKU. Daarom hebben uw hotspots alleen SKU-velden nodig die zijn gevuld met waarden als <strong><code>866558</code></strong> , <strong><code>1196184</code></strong> , <strong><code>1081492</code></strong> en <strong><code>1898294</code></strong> .</p> </td>
  </tr>
  <tr>
    <td><p>Eén SKU, gevonden in het URL-pad.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van de hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong> .</p> </td>
  </tr>
  <tr>
    <td><p>SKU en categorie-id in de queryreeks.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. SKU wordt opgeslagen in de <code>prodId</code> parameter en categorieidentiteitskaart <code></code> wordt opgeslagen in de <code>category=</code> parameter.</p> <p>Daarom zijn de hotspot-definities paren. Dit is een SKU-waarde en een extra variabele met de naam <code>categoryId</code> . De resulterende paren zijn als volgt:</p>
    <ul>
      <li><p>SKU is <strong><code>305466</code></strong> en <code>categoryId</code> is <code>1100004</code> .</p> </li>
      <li><p>SKU is <strong><code>310181</code></strong> en <code>categoryId</code> is <strong><code>1100004</code></strong> .</p> </li>
      <li><p>SKU is <strong><code>308706</code></strong> en <code>categoryId</code> is <strong><code>1740148</code></strong> .</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Voorbeeld**

U kunt dezelfde aanpak toepassen als in de drie bovenstaande voorbeelden op de demo-webpagina:

[ https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

De demo-webpagina heeft verschillende productminiaturen, elk met een Quickview-knop met het label &quot;Meer weergeven&quot;. Selecteer elke knop terwijl het foutopsporingsprogramma van uw webbrowser nog is geactiveerd en noteer de opgenomen URL&#39;s van de Snelle weergave. Nadat u alle vier productenQuickview activeert die op de pagina beschikbaar zijn, hebt u de volgende lijst van verzoeken van de Snelle mening die aan het achterste eind worden gemaakt:

* `/datafeed/Male-Windbreaker.json`
* `/datafeed/Male-SimpleHenley.json`
* `/datafeed/Male-CamoPullover.json`
* `/datafeed/Female-QuiltedDownJacket.json`

Wanneer u de serveraanroepen bekijkt, ziet u dat productspecifieke informatie alleen aanwezig is in het aanvraagpad. U merkt ook op dat het vraagkoord helemaal niet wordt gebruikt en er zijn twee verschillende types van betrokken gegevensstukken:

* Het eerste type is Mannelijk of Vrouwelijk. Je kunt deze &#39;productcategorie&#39; noemen.
* Het tweede type is productnaam, zoals CamoPullover. U kunt veronderstellen dat deze informatie product SKU is.

Op basis van deze informatie heeft de volledige URL van de Snelle weergave het volgende patroon:

`/datafeed/$categoryId$-$SKU$.json`

Op basis van een dergelijke analyse gebruikt u `categoryId` en `SKU` voor hotspots.

U kunt nu een afbeeldingsbanner uploaden en er hotspots aan toevoegen met de functie voor onoverzichtelijke interactieve afbeeldingen in Experience Manager Assets.

## (Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken {#optional-creating-an-interactive-image-viewer-preset}

U kunt de standaardvoorinstelling voor een interactieve afbeeldingsviewer buiten de box met de naam `Shoppable_Banner` gebruiken die bij Experience Manager Assets wordt geleverd. U kunt ook uw eigen aangepaste viewer-voorinstelling maken voor gebruik met interactieve afbeeldingen.

Wanneer u een aangepaste voorinstelling voor een interactieve afbeeldingsviewer maakt, kunt u de weergave van hotspots in de afbeeldingsbanner bepalen. Als onderdeel van het maken van de viewervoorinstelling kunt u een hotspot-afbeelding uit een galerie met vooraf gedefinieerde afbeeldingen gebruiken.

Nadat u de viewervoorinstelling hebt opgeslagen, wordt deze automatisch geactiveerd (ingeschakeld) op de pagina met de lijst met voorinstellingen voor viewers in Experience Manager Assets. Deze functionaliteit houdt in dat het zichtbaar is in de Interactieve component van Media en wanneer u activa bekijkt. Nochtans, om ** een interactieve banner met deze vooraf ingestelde kijker te leveren, moet u ** uw kijker publiceren ook vooraf ingesteld. Deze regel geldt voor aangepaste of uit-van-box viewer-voorinstellingen.

**om een Interactieve de kijker van het Beeld tot stand te brengen vooraf ingesteld:**

1. Navigeer in de linkertrack naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** .
1. Selecteer **[!UICONTROL Create]** in de rechterbovenhoek van de pagina.
1. Typ in het dialoogvenster Nieuwe voorinstelling voor viewer een naam om de voorinstelling voor de interactieve bannerviewer te beschrijven.

   Nadat u de titel hebt opgeslagen, wordt deze weergegeven in de lijstpagina Voorinstelling viewer.

1. Selecteer in het vervolgkeuzemenu Uitgebreid mediatype de optie **[!UICONTROL Interactive Image]**.
1. Selecteer **[!UICONTROL Create]** .
1. Selecteer de tab **[!UICONTROL Appearance]** op de pagina Voorinstelling viewer bewerken.
1. Voer een van de volgende handelingen uit:

   * Als u uw eigen hotspot-afbeelding wilt uploaden die u voor afbeeldingen wilt gebruiken, selecteert u het pictogram Asset Picker. Navigeer op de pagina Inhoud selecteren naar de gewenste hotspot-afbeelding, selecteer deze en selecteer vervolgens het pictogram Markeren controleren in de rechterbovenhoek.
   * Als u een vooraf gedefinieerde hotspot-afbeelding wilt selecteren, selecteert u het pictogram Hotspot-galerie. Selecteer in het palet van de hotspot de hotspot die u wilt gebruiken.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.

   Zorg ervoor dat u de nieuwe viewervoorinstelling publiceert.

   Zie [ het Publiceren Kijker vooraf instelt die u ](/help/assets/managing-viewer-presets.md#publishing-viewer-presets) hebt toegevoegd.

   U kunt nu een afbeeldingsbanner uploaden.

## Een afbeeldingsbanner uploaden {#uploading-an-image-banner}

Als u reeds de beelden hebt geüpload die u wilt gebruiken, aan de volgende stap vooruitgaan, [ toevoegend hotspots aan een beeldbanner ](#adding-hotspots-to-an-image-banner).

**om een beeldbanner te uploaden:**

1. Upload afbeeldingsbanners die u interactief wilt maken.

   Zie [ Uploading activa ](/help/assets/manage-assets.md#uploading-assets).

   U kunt nu hotspots toevoegen aan de afbeeldingsbanner. Zie de volgende taak hieronder.

## Hotspots toevoegen aan een afbeeldingsbanner {#adding-hotspots-to-an-image-banner}

U kunt hotspots toevoegen aan een afbeeldingsbanner met de editor op de pagina Hotspot-beheer.

Wanneer u hotspots toevoegt, kunt u deze definiëren als een pop-upweergave in QuickView, als een hyperlink of als een Experience-fragment.

Zie [ Fragmenten van de Ervaring ](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Om dit probleem te verhelpen, kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw interactieve afbeelding, kunt u Voorvertoning gebruiken om een voorstelling te zien van hoe uw interactieve afbeelding eruit ziet voor klanten.

Zie [ (Optioneel) Een voorvertoning weergeven van interactieve afbeeldingen ](#optional-previewing-interactive-images) .

>[!NOTE]
>
>Wanneer u hotspots toevoegt aan een afbeelding in een interactieve afbeelding of een carrouselbanner, worden de hotspotgegevens opgeslagen op dezelfde metagegevenslocatie. Deze locatie is relatief ten opzichte van de locatie van de afbeelding, ongeacht of het een interactieve afbeelding of een carrouselbanner betreft. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.
>
>Carrouselbanners ondersteunen afbeeldingen met hyperlinks op afbeeldingen die ook hotspots kunnen bevatten. Interactieve afbeeldingen niet. Houd deze regel in gedachten als u een interactieve afbeelding of Carousel Banner wilt maken die dezelfde afbeelding gebruikt. U kunt interactieve afbeeldingen en carrouselbanners maken met afzonderlijke kopieën van dezelfde afbeelding.
>
>Zie ook [ Banners van de Carrousel ](/help/assets/carousel-banners.md).

>[!NOTE]
>
>Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

**om hotspots aan een beeldbanner toe te voegen:**

1. Navigeer in de Assets-weergave naar de afbeeldingsbanner die u interactief wilt maken.
1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven de afbeelding en selecteer vervolgens **[!UICONTROL Select]** (vinkje). Selecteer **[!UICONTROL Edit]** op de werkbalk.

   * Houd de muisaanwijzer boven de afbeelding en selecteer vervolgens **[!UICONTROL More actions]** (pictogram met drie punten) **[!UICONTROL Edit]** .

   * Selecteer de afbeelding zodat u deze kunt openen op de pagina Gedetailleerde weergave. Selecteer **[!UICONTROL Edit]** op de werkbalk.

1. Selecteer in de linkerbovenhoek van de pagina de optie **[!UICONTROL Add Hotspot]** (vingergeselecteerd pictogram) om de pagina Hotspot-beheer te openen.
1. Selecteer **[!UICONTROL Hotspot]** in de linkerbovenhoek van de pagina.

   1. Selecteer **[!UICONTROL Hotspot]** in de linkerbovenhoek van de pagina Hotspot Management.
   1. Selecteer in de afbeelding een locatie waar u de hotspot wilt weergeven. Sleep indien nodig de hotspot om de locatie ervan aan te passen.
   1. Voeg desgewenst extra hotspots toe door de stappen a en b te herhalen.
   1. (Optioneel) Als u een hotspot wilt verwijderen, selecteert u de hotspot in de afbeelding en selecteert u vervolgens **[!UICONTROL Delete]** (trashcan-pictogram) onder de kop **[!UICONTROL Hotspots]** .

1. Typ in het tekstveld Naam de naam van de hotspot. Deze naam wordt ook weergegeven in de vervolgkeuzelijst Geselecteerde hotspot.
1. Voer een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Quickview]** .

      * Als u een Experience Manager Sites- of eCommerce-klant bent, selecteert u het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen. Selecteer het product dat u wilt gebruiken en selecteer vervolgens **[!UICONTROL Select]** in de rechterbovenhoek van de pagina zodat u terug kunt keren naar de pagina Hotspot-beheer.
      * Als u *niet* een klant van Experience Manager Sites of eCommerce bent

         * Zie [ hotspot variabelen identificeren ](#optional-identifying-hotspot-variables); u moet deze variabelen bepalen.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU (Stock Keeping Unit) van het product. Dit is een unieke id voor elk afzonderlijk product of elke service die u aanbiedt. De ingevoerde waarde van SKU bevolkt automatisch het veranderlijke gedeelte van het malplaatje van de Snelle mening zodat het systeem weet om geselecteerde hotspot met een bepaalde mening van SKU te associëren Quickview.
         * (Optioneel) Als de Snelle weergave andere variabelen bevat die u moet gebruiken om een product verder te identificeren, selecteert u **[!UICONTROL Add Generic Variable]** . Geef in het tekstveld een extra variabele op. `category=Males` is bijvoorbeeld een toegevoegde variabele.

   * Selecteer **[!UICONTROL Hyperlink]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het pictogram Sitekiezer (map) om naar een URL te navigeren. De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
      * Als u een zelfstandige klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [ Werk met Kiezers ](/help/assets/working-with-selectors.md) voor meer informatie.

   * Selecteer **[!UICONTROL Experience Fragment]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het zoekpictogram (vergrootglas) om de pagina Experience Fragment te openen. Selecteer het ervaringsfragment dat u wilt gebruiken en selecteer vervolgens **[!UICONTROL Select]** in de rechterbovenhoek van de pagina zodat u kunt terugkeren naar de pagina Hotspot-beheer.
Zie [ Fragmenten van de Ervaring ](/help/sites-authoring/experience-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals u het wilt weergeven op de banner.

        >[!NOTE]
        >
        >De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Om dit probleem te verhelpen, kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

1. Selecteer **[!UICONTROL Save]** om uw werk op te slaan en terug te keren naar de pagina Bladeren.
1. Publish the interactive image. Met publicatie kan de banner via de cloud worden geleverd en wordt ook insluitcode gegenereerd als u wilt integreren met een website van derden.

   Zie [ de activa van Publish ](/help/assets/manage-assets.md#publishing-assets).

   Nadat u hotspots hebt toegevoegd en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande website.

   Zie [ een interactief beeld met uw website ](#integrating-an-interactive-image-with-your-website) integreren.

   >[!NOTE]
   >
   >Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

### (Optioneel) Interactieve afbeeldingen voorvertonen {#optional-previewing-interactive-images}

Met Voorvertoning kunt u zien hoe uw interactieve afbeelding eruit ziet en kunt u de hotspots van de afbeelding testen om te controleren of deze zich naar behoren gedragen.

Als u tevreden bent met de interactieve afbeelding, kunt u deze publiceren.
Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/embed-code.md) inbedden.
Zie [ Verbinding URLs aan uw Webtoepassing ](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [ Dynamic Media Assets aan Pagina&#39;s ](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.

**aan voorproef interactieve beelden:**

1. Navigeer in de Assets-weergave naar een bestaande interactieve afbeelding die u hebt gemaakt en selecteer deze om deze te openen in Voorvertoning.
1. Selecteer **[!UICONTROL Viewers]** in de vervolgkeuzelijst Inhoud in de linkerbovenhoek van de pagina Voorvertoning.
1. Selecteer **[!UICONTROL Shoppable_Banner]** in de lijst Viewers of de naam van de voorinstelling voor de interactieve afbeeldingsviewer die u hebt gemaakt.
1. Selecteer hotspots in de afbeelding als u de bijbehorende handelingen wilt testen.

## Interactieve Publish-afbeeldingselementen {#publishing-interactive-image-assets}

Zie {de activa van 0} Publish ](/help/assets/publishing-dynamicmedia-assets.md) voor details op hoe te om interactieve beeldactiva te publiceren.[

## Een interactieve afbeelding met uw website integreren {#integrating-an-interactive-image-with-your-website}

Nadat u een bannerafbeelding hebt geüpload, hotspots hebt toegevoegd aan de afbeelding en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw websitepagina.

Als u een Experience Manager Sites-klant bent, kunt u de interactieve afbeelding toevoegen door de component Interactieve media naar de pagina te slepen. Zie [ Dynamic Media Assets aan Pagina&#39;s ](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.

Als u een zelfstandige Experience Manager Assets-klant bent, kunt u de interactieve afbeelding handmatig aan uw website toevoegen, zoals in deze sectie wordt beschreven.

1. Kopieer de insluitcode van de gepubliceerde interactieve afbeelding.
Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/embed-code.md) inbedden.

1. Voeg de gekopieerde insluitcode toe op de gewenste locatie op de webpagina.
De gekopieerde insluitcode wordt ingesteld voor een responsieve omgeving, zodat deze automatisch in het toegewezen gebied past.

**Voorbeeld**

De demo-website als voorbeeld gebruiken:

[ https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

Het beeld van de drie mannetjes is een statische `IMG` -tag:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Integratie is net zo eenvoudig als het verwijderen van de tag `IMG` en het vervangen door de gekopieerde insluitcode uit Experience Manager Assets. Het resultaat wordt weergegeven in de volgende URL, die de mogelijk onjuiste interactieve afbeelding op de pagina met drie hotspots per cirkel weergeeft:

[ https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>Als dit punt, zijn de hotspots op het shoppable interactieve beeld van de demo website slechts voor vertoningsdoeleinden; zij zijn nog niet geïntegreerd met het bestaande Kickview.

Als u een &#39;uitsnijding&#39; wilt toepassen op een verwisselbare interactieve afbeelding voor een responsieve omgeving, kunt u het configuratiekenmerk Interactive Image `ZoomView.iscommand` op het pad opnemen. De component `ZoomView` wordt aangeroepen en `iscommand` is de opdracht voor het bedienen van een &quot;uitsnijdafbeelding&quot; die u toepast.

Zie [ ZoomView.iscommand ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand) configuratieattributen.

Zie [ gewas ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop) beeld het dienen bevel.

U bent nu klaar om de interactieve afbeelding te integreren met een bestaande QuickView op uw website.

## Een interactieve afbeelding integreren met een bestaande QuickView {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Deze taak is alleen van toepassing als u een zelfstandige Experience Manager Assets-klant bent.

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

Wanneer een gebruiker een hotspot binnen de verschuifbare afbeelding selecteert, wordt deze gebruikersinteractie door de viewer afgehandeld, terwijl de verschuifbare interactieve afbeelding stap 1 en gedeeltelijk stap 2 vervangt. De viewer retourneert een gebeurtenis naar de webpagina die alle hotspotgegevens bevat die eerder aan Experience Manager Assets zijn toegevoegd.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die wordt uitgegeven door de mogelijk onjuiste interactieve afbeelding.
* Hiermee maakt u een Quickview-URL op basis van de hotspot-gegevens.
* Triggert het proces om de Snelle mening van het achtereind te laden en het terug te geven op het scherm voor vertoning.

De insluitcode die door Experience Manager Assets wordt geretourneerd, bevat al een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd, zoals in het volgende gemarkeerde codefragment wordt getoond:

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
                    //To pass other parameter from the hotspot, you must add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //See your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Het is dus alleen nodig de commentaarmarkering van de code ongedaan te maken en de dummy-handlertekst te vervangen door de code die specifiek is voor de specifieke webpagina.

Het proces voor het samenstellen van de URL van de Snelle weergave is tegengesteld aan het proces voor het identificeren van hotspot-variabelen die eerder zijn behandeld.

Zie [ hotspot variabelen ](#optional-identifying-hotspot-variables) identificeren.

Met behulp van de vorige URL-voorbeelden van Quickview kunt u in de volgende voorbeelden zien hoe de URL van de QuickView in elk geval wordt samengesteld:

<table>
 <tbody>
  <tr>
   <td><p>Enige SKU, die in het vraagkoord wordt gevonden</p> </td>
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

Als u deze URL wilt reconstrueren binnen de `quickViewActivate` -handler, kunt u de velden `categoryId` en `SKU` gebruiken die beschikbaar zijn in het `inData` -object dat aan de handler wordt doorgegeven door de code van de viewer:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

De demowebsite activeert het dialoogvenster Snelle weergave met een eenvoudige functieaanroep `loadQuickView()` . Deze functie heeft slechts één argument, namelijk de gegevens-URL van de Snelle weergave. De laatste stap voor het integreren van de verschuifbare interactieve afbeelding is dan ook het toevoegen van de volgende coderegel aan de `quickViewActivate` -handler:

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

[ https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html)

## QuickView gebruiken om aangepaste pop-ups te maken {#using-quickviews-to-create-custom-pop-ups}

Zie [ douane pop-UPS creëren gebruikend QuickView ](/help/assets/custom-pop-ups.md).
