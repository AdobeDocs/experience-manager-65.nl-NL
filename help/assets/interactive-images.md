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
translation-type: tm+mt
source-git-commit: 90c99e527a40bb663d4f32d8746b46cf34a2319f
workflow-type: tm+mt
source-wordcount: '4301'
ht-degree: 1%

---


# Interactive images{#interactive-images}

U kunt statische afbeeldingen eenvoudig verrijken en aantrekkelijke ervaringen voor klanten creëren door &#39;onoverzichtelijke&#39; hotspots naar een afbeelding te slepen. Slepbare hotspots combineren aanvullende informatie over een product of service met een directe, verkooppuntfunctie &#39;Toevoegen aan winkelwagentje&#39; of &#39;Kopen&#39;. Klanten kunnen op deze hotspots tikken of erop klikken en deze rechtstreeks aan het product of de service koppelen, ze aan een winkelwagentje toevoegen of aan een webpagina koppelen. Directe ervaringen zoals deze vergroten het contact en de conversie van klanten op uw website.

Hieronder ziet u een blaasbare banner met een pop-upvenster van QuickView. Een gebruiker activeert de Snelle weergave door op de cirkel of de hotspot op het model te tikken.

![chlimage_1-152](assets/chlimage_1-368.png)

Bekijk de volgende interactieve afbeeldingen in actie op de bovenstaande webpagina:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## Controleren hoe interactieve afbeeldingsbanners worden gemaakt {#watch-how-interactive-image-banners-are-created}

Watch a 10 minute and 33 second walkthrough on [how interactive image banners are created](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). U leert ook hoe u interactieve afbeeldingsbanners kunt voorvertonen, bewerken en leveren.

## Snel starten: Interactieve afbeeldingen {#quick-start-interactive-images}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met interactieve afbeeldingen in AEM Assets.

Zoek de kop **Voorbeeld** in sommige van de taken van Snel starten. Het bevat een korte zelfstudie die is gebaseerd op het volgende webpaginavoorbeeld waaraan nog geen interactieve afbeeldingen zijn toegevoegd:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

De zelfstudie helpt u de stappen te illustreren voor het integreren van interactieve afbeeldingen op uw eigen website.

Stappen voor interactieve afbeeldingen:

1. **(Optioneel) Hotspot-variabelen** identificeren - Als u AEM Assets en Dynamic Media zelfstandig gebruikt, begint u met het identificeren van dynamische variabelen die worden gebruikt in uw bestaande Quickview-implementatie, zodat u hotspot-gegevens kunt invoeren wanneer u de interactieve afbeelding maakt. Zie [(Optioneel) Hotspot-variabelen](#optional-identifying-hotspot-variables)identificeren.
Nochtans, als u AEM Sites, of AEM eCommerce, of allebei gebruikt, dan is deze stap niet noodzakelijk.
Zie [eCommerce-concepten in AEM Assets](/help/sites-administering/concepts.md).

1. **(Optioneel) Een voorinstelling** voor een interactieve afbeeldingsviewer maken - Pas de afbeelding aan die wordt gebruikt om hotspots te vertegenwoordigen. U hoeft geen eigen voorinstelling voor de interactieve afbeeldingsviewer te maken als u de voorinstelling Interactieve afbeeldingsviewer buiten de box wilt gebruiken. Deze voorinstelling heet `Shoppable_Banner` in plaats daarvan.
Zie [(Optioneel) Een voorinstelling](/help/assets/managing-viewer-presets.md#creating-a-new-viewer-preset)voor een interactieve afbeeldingsviewer maken.

1. **Een afbeeldingsbanner** uploaden - Afbeeldingsbanners uploaden die u interactief wilt maken.
Zie Een afbeeldingsbanner [uploaden](#uploading-an-image-banner).

1. **Hotspots toevoegen aan een afbeeldingsbanner** - Voeg een of meer hotspots toe aan een afbeeldingsbanner en koppel deze aan een handeling zoals een hyperlink, een Snelle weergave of een ervaringsfragment. Nadat u hotspots hebt toegevoegd, kunt u deze taak voltooien door de interactieve afbeelding te publiceren.

   * Zie [Hotspots toevoegen aan een afbeeldingsbanner](#adding-hotspots-to-an-image-banner).
   * Zie [Een voorvertoning weergeven van interactieve afbeeldingen](#optional-previewing-interactive-images) - Optioneel. U kunt desgewenst een representatie van de verscherpte banner bekijken en de interactiviteit ervan testen.
   * Zie Elementen [](/help/assets/publishing-dynamicmedia-assets.md) publiceren voor meer informatie over het publiceren van interactieve afbeeldingselementen.

1. **Een interactieve afbeelding toevoegen aan uw website of uw website in AEM** Als u AEM Sites of AEM eCommerce gebruikt, of beide, kunt u de interactieve afbeelding rechtstreeks toevoegen aan een webpagina in AEM door de component Interactieve media naar de pagina te slepen. See [Adding Dynamic Media Assets to Pages.](/help/assets/adding-dynamic-media-assets-to-pages.md)
Als u AEM Assets en Dynamic Media zelfstandig gebruikt, moet u de insluitcode naar uw website kopiëren en deze vervolgens integreren met uw bestaande QuickView. Zie Een interactieve afbeelding [integreren met uw website](#integrating-an-interactive-image-with-your-website).
Als u WCM (Web Content Manager) van derden gebruikt, moet u de nieuwe interactieve video integreren met de bestaande implementatie van de Snelle weergave die op uw website wordt gebruikt. Zie Een interactieve afbeelding [integreren met een bestaande Snelle weergave](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optioneel) Hotspotvariabelen identificeren {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Deze taak is alleen vereist als aan de volgende voorwaarden wordt voldaan:
>
>* U wilt interactiviteit aan uw beeld toevoegen door aan Snelle meningen te teweegbrengen.
>* Uw implementatie van AEM maakt *geen* gebruik van een eCommerce-integratiekader om productgegevens in AEM te halen van een eCommerce-oplossing zoals IBM Websphere Commerce, Elastic Path, hybris of Intershop. Zie [eCommerce-concepten in AEM Assets](/help/sites-administering/concepts.md).

>
>
Als uw implementatie van AEM eCommerce gebruikt, kunt u deze taak overslaan en aan de volgende taak te werk gaan.

Begin door dynamische variabelen te identificeren die door uw bestaande implementatie van QuickView worden gebruikt zodat u hotspot gegevens kunt ingaan om het interactieve beeld tot stand te brengen.

Wanneer u hotspots toevoegt aan een bannerafbeelding in AEM Assets, moet u een SKU (Stock Keeping Unit) toewijzen; een unieke id voor elk afzonderlijk product of elke service die u aanbiedt) en optionele aanvullende variabelen voor elke hotspot. Dergelijke hotspotvariabelen worden later gebruikt om hotspots aan te passen aan Quickview-inhoud.

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot gegevens te associëren. Elke hotspot die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie bevatten om het product ondubbelzinnig te identificeren in het bestaande back-endsysteem.

Er zijn verschillende manieren om een set variabelen te identificeren die voor hotspot-gegevens moet worden gebruikt.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande QuickView-implementatie, omdat ze waarschijnlijk zullen weten wat de minimale gegevensset is die nodig is om QuickView in het systeem te identificeren. In de meeste gevallen is het echter ook mogelijk om eenvoudig het bestaande gedrag van de front-end code te analyseren.

De meeste implementaties van de Snelle mening gebruiken het volgende paradigma:

* De gebruiker activeert een gebruikersinterface-element op de website. Klik bijvoorbeeld op een knop Snelle weergave.
* De website verzendt een Ajax-aanvraag naar de achterkant om de Quickview-gegevens of -inhoud te laden, indien nodig.
* De Quickview-gegevens worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie QuickView is geïmplementeerd, de QuickView activeren en de Ajax-URL vastleggen die via een webpagina is verzonden om de gegevens of inhoud van de QuickView-weergave te laden.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Om alle uitgaande HTTP- verzoeken in Google Chrome te zien, druk F12 om het paneel van Hulpmiddelen van de Ontwikkelaar te openen, en dan het lusje van het Netwerk te klikken.
Druk op een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en klik vervolgens op het tabblad Netwerk.

* In Firefox kunt u de Firebug-plug-in activeren door op F12 te drukken en het tabblad Net te gebruiken. U kunt ook het ingebouwde controllergereedschap en het bijbehorende tabblad Netwerk gebruiken.
Druk op een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en klik vervolgens op het tabblad Inspecteur.

Wanneer netwerkcontrole in browser wordt aangezet, teweeg de Snelle mening op de pagina.

Zoek nu de URL van Quickview Ajax in het netwerklogboek en kopieer de geregistreerde URL voor toekomstige analyse. In de meeste gevallen wanneer u de Quickview teweegbrengt zijn er talrijke verzoeken die naar de server worden verzonden. De URL van Quickview Ajax is doorgaans een van de eerste in de lijst. Het heeft of een complex gedeelte of een weg van het vraagkoord, en zijn reactieMIME type of, `text/html`, of `text/xml``text/javascript`.

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat URL&#39;s in de Snelle weergave onderdelen kunnen bevatten die algemeen gelden voor een bepaalde categorie websites, maar deze alleen wijzigen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval, is het enige veranderlijke deel in Quickview URL productSKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter naast de SKU ook verschillende elementen, zoals categorie-id, kleurcode, code voor grootte enzovoort. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot-gegevens in de functie voor onoverzichtelijke interactieve afbeeldingen in AEM Assets.

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
    </ul> <p>Het enige veranderlijke deel in URL is de waarde van de productId= parameter van het vraagkoord, en het is duidelijk een waarde SKU. Daarom hebben onze hotspots alleen SKU-velden nodig die zijn gevuld met waarden als <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td>
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
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. SKU wordt opgeslagen in de <code>prodId</code> parameter en categorieidentiteitskaart<code></code> wordt opgeslagen in de <code>category=</code> parameter.</p> <p>Daarom zijn de hotspot-definities paren. Dat wil zeggen, een SKU-waarde en een aanvullende variabele <code>categoryId</code>. De resulterende paren zijn:</p>
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

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

De demo-webpagina heeft verschillende productminiaturen, elk met een Quickview-knop met het label &quot;Meer weergeven&quot;. Terwijl het foutopsporingsprogramma van uw webbrowser nog is geactiveerd, klikt u op elke knop en noteert u de opgenomen URL&#39;s van de Snelle weergave. Nadat u alle vier de productenQuickviews beschikbaar op de pagina activeert, hebt u de volgende lijst verzoeken van de Snelle mening die aan het achterste eind worden gemaakt:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wanneer u deze serveraanroepen bekijkt, ziet u dat productspecifieke informatie alleen aanwezig is in het aanvraagpad. U merkt ook op dat het vraagkoord helemaal niet wordt gebruikt en er zijn twee verschillende types van betrokken gegevensstukken:

* Het eerste type is Men of Vrouwen. Je kunt deze &#39;productcategorie&#39; noemen.
* Het tweede type is productnaam, zoals CamoPullover. U kunt veronderstellen dit het product SKU is.

Op basis van deze informatie heeft de volledige URL van de Snelle weergave het volgende patroon:

`/datafeed/$categoryId$-$SKU$.json`

Op basis van deze analyse gebruikt u hotspots `categoryId` en `SKU` voor hotspots.

U kunt nu een afbeeldingsbanner uploaden en er hotspots aan toevoegen met de functie voor onoverzichtelijke interactieve afbeeldingen in AEM Assets.

## (Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken {#optional-creating-an-interactive-image-viewer-preset}

U kunt ervoor kiezen om de standaardvoorinstelling voor een interactieve afbeeldingsviewer buiten de box te gebruiken, die bij AEM Assets wordt geleverd. `Shoppable_Banner` U kunt ook uw eigen aangepaste viewer-voorinstelling maken voor gebruik met interactieve afbeeldingen.

Wanneer u een aangepaste voorinstelling voor een interactieve afbeeldingsviewer maakt, kunt u de weergave van hotspots in de afbeeldingsbanner bepalen. Als onderdeel van het maken van de viewervoorinstelling kunt u een hotspot-afbeelding uit een galerie met vooraf gedefinieerde afbeeldingen gebruiken.

Nadat u de viewervoorinstelling hebt opgeslagen, wordt deze automatisch geactiveerd (ingeschakeld) op de pagina met de lijst met voorinstellingen voor viewers in AEM Assets. Deze functionaliteit houdt in dat het zichtbaar is in de Interactieve component van Media en wanneer u activa bekijkt. Als *echter *een interactieve banner met deze viewer-voorinstelling wilt leveren, moet *uw viewer-voorinstelling ook *publiceren (dit geldt voor aangepaste of offline viewervoorinstellingen).

**Een voorinstelling voor een interactieve afbeeldingsviewer maken**

1. Tik in de linkerspoorstaaf **[!UICONTROL Tools > Assets > Viewer Presets.]**
1. Near the upper-right corner of the page, tap **[!UICONTROL Create.]**
1. Typ in het dialoogvenster Nieuwe voorinstelling voor viewer een naam om de voorinstelling voor de interactieve bannerviewer te beschrijven.

   Dit is de titel die wordt weergegeven op de pagina met de lijst Voorinstellingen voor viewer nadat u de voorinstelling hebt opgeslagen.

1. Selecteer in het vervolgkeuzemenu Uitgebreid mediatype de optie **[!UICONTROL Interactive Image.]**
1. Tik op **[!UICONTROL Create.]**
1. On the Edit Viewer Preset page, tap the **[!UICONTROL Appearance]** tab.
1. Voer een van de volgende handelingen uit:

   * Tik op het pictogram Asset Picker om uw eigen hotspot-afbeelding te uploaden die u voor afbeeldingen wilt gebruiken. Navigeer op de pagina Inhoud selecteren naar de gewenste hotspot-afbeelding, selecteer deze en tik op het pictogram Markeren controleren in de rechterbovenhoek.
   * Tik op het pictogram Hotspot-galerie om een vooraf gedefinieerde hotspot-afbeelding te selecteren. Tik op het palet van de hotspot op de hotspot die u wilt gebruiken.

1. Near the upper-right corner of the page, tap **[!UICONTROL Save.]**

   Zorg ervoor dat u de nieuwe viewervoorinstelling publiceert.

   Zie Voorinstellingen [voor viewers publiceren die u hebt toegevoegd](/help/assets/managing-viewer-presets.md#publishing-viewer-presets).

   U kunt nu een afbeeldingsbanner uploaden.

## Een afbeeldingsbanner uploaden {#uploading-an-image-banner}

Als u de afbeeldingen die u wilt gebruiken al hebt geüpload, gaat u naar de volgende stap Hotspots [toevoegen aan een afbeeldingsbanner](#adding-hotspots-to-an-image-banner).

**Een afbeeldingsbanner uploaden**

1. Upload afbeeldingsbanners die u interactief wilt maken.

   Zie Elementen [uploaden](/help/assets/manage-assets.md#uploading-assets).

   U kunt nu hotspots toevoegen aan de afbeeldingsbanner. zie de volgende taak hieronder.

## Hotspots toevoegen aan een afbeeldingsbanner {#adding-hotspots-to-an-image-banner}

U kunt hotspots toevoegen aan een afbeeldingsbanner met de editor op de pagina Hotspot-beheer.

Wanneer u hotspots toevoegt, kunt u deze definiëren als een pop-upweergave in QuickView, als een hyperlink of als een Experience-fragment.

Zie Fragmenten [ervaren](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Houd er rekening mee dat de gereedschappen voor het delen van sociale media in interactieve afbeeldingen niet worden ondersteund wanneer u de viewer insluit in een Experience-fragment. U kunt dit omzeilen door voorinstellingen voor viewers te gebruiken of te maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw interactieve afbeelding, kunt u Voorvertoning gebruiken om een voorstelling te zien van hoe uw interactieve afbeelding eruit zal zien voor klanten.

Zie [(Optioneel) Een voorvertoning weergeven van interactieve afbeeldingen](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wanneer u hotspots toevoegt aan een afbeelding in een interactieve afbeelding of een carrouselbanner, worden de hotspotgegevens opgeslagen op dezelfde metagegevenslocatie, relatief ten opzichte van de locatie van de afbeelding, ongeacht of het een interactieve afbeelding of een carrouselbanner betreft. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.
>
>Houd er echter rekening mee dat Carousel Banners afbeeldingen met hyperlinks ondersteunen op afbeeldingen die ook hotspots kunnen bevatten. een interactieve afbeelding niet. Houd hier rekening mee als u een interactieve afbeelding of Carousel Banner wilt maken die dezelfde afbeelding gebruikt. U kunt interactieve afbeeldingen en carrouselbanners maken met afzonderlijke kopieën van dezelfde afbeelding.
>
>Zie ook [Carousel Banners](/help/assets/carousel-banners.md).

>[!NOTE]
>
>Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

**Hotspots toevoegen aan een afbeeldingsbanner**

1. Navigeer in de weergave Elementen naar de afbeeldingsbanner die u interactief wilt maken.
1. Voer een van de volgende handelingen uit:

   * Hover on the image, then tap **[!UICONTROL Select]** (checkmark icon). Tik op de werkbalk op **[!UICONTROL Edit.]**

   * Houd de cursor boven op de afbeelding en tik vervolgens op **[!UICONTROL More actions]** (driepuntpictogram) **[!UICONTROL > Edit.]**

   * Tik op de afbeelding om deze te openen in de detailweergave. Tik op de werkbalk op **[!UICONTROL Edit.]**

1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL Add Hotspot]** (vingertikpictogram) om de pagina Hotspotbeheer te openen.
1. Near the upper-left corner of the page, tap **[!UICONTROL Hotspot.]**

1. Tik in de linkerbovenhoek van de pagina Hotspot Management (Hotspot-beheer) op **[!UICONTROL Hotspot.]**
1. Tik in de afbeelding op een locatie waar u de hotspot wilt weergeven. Sleep indien nodig de hotspot om de locatie ervan aan te passen.
1. Voeg desgewenst extra hotspots toe door de stappen a en b te herhalen.
1. (Optioneel) Als u een hotspot wilt verwijderen, selecteert u de hotspot in de afbeelding en tikt u vervolgens op **[!UICONTROL Delete]** (vuilnisbakpictogram) onder de **[!UICONTROL Hotspots]** kop.

1. Typ in het tekstveld Naam de naam van de hotspot. Deze naam wordt ook weergegeven in de vervolgkeuzelijst Geselecteerde hotspot.
1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Quickview.]**

      * Als u een AEM Sites- of eCommerce-klant bent, tikt of klikt u op het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen. Tik of klik op het product dat u wilt gebruiken en tik op **Selecteer **in de rechterbovenhoek van de pagina om terug te keren naar de pagina Hotspot-beheer.
      * Als je *geen* AEM Sites- of eCommerce-klant bent

         * Zie [Hotspot-variabelen](#optional-identifying-hotspot-variables)identificeren; U moet deze variabelen definiëren.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU (Stock Keeping Unit) van het product. Dit is een unieke id voor elk afzonderlijk product of elke service die u aanbiedt. De ingegaan waarde van SKU bevolkt automatisch het veranderlijke gedeelte van het malplaatje van de Snelle mening zodat het systeem weet om geëtteerde hotspot met een bepaalde Snelle mening van SKU te associëren.
         * (Optioneel) Als de Snelle weergave andere variabelen bevat die u nodig hebt om een product nader te identificeren, tikt u op **[!UICONTROL Add Generic Variable.]** In het tekstveld en geeft u een extra variabele op. Dit `category=Mens` is bijvoorbeeld een toegevoegde variabele.
   * Tik op **[!UICONTROL Hyperlink.]**

      * Als u een AEM Sites-klant bent, tikt of klikt u op het pictogram Site-kiezer (map) om naar een URL te navigeren. De op URL gebaseerde methode van koppelen is niet mogelijk als uw interactieve inhoud koppelingen naar relatieve URL&#39;s bevat, met name koppelingen naar AEM Sites-pagina&#39;s.
      * Als u een zelfstandige klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md) voor meer informatie.

   * Tik op **[!UICONTROL Experience Fragment.]**

      * Als u een AEM Sites-klant bent, tikt of klikt u op het zoekpictogram (vergrootglas) om de pagina Experience Fragment te openen. Tik op het gewenste fragment voor beleving of klik op het gewenste fragment. Tik vervolgens op Selecteren in de rechterbovenhoek van de pagina om terug te keren naar de pagina Hotspot-beheer.
Zie Fragmenten [ervaren](/help/sites-authoring/experience-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals dit wordt weergegeven op de banner.

         >[!NOTE]
         >
         >Houd er rekening mee dat de gereedschappen voor het delen van sociale media in interactieve afbeeldingen niet worden ondersteund wanneer u de viewer insluit in een Experience-fragment. U kunt dit omzeilen door voorinstellingen voor viewers te gebruiken of te maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.



1. Tik **[!UICONTROL Save]** om uw werk op te slaan en terug te keren naar de pagina Bladeren.
1. Publiceer de interactieve afbeelding. Met publicatie kan de banner via de cloud worden geleverd en wordt ook insluitcode gegenereerd als u wilt integreren met een website van derden.

   Zie [Elementen](/help/assets/manage-assets.md#publishing-assets)publiceren.

   Nadat u hotspots hebt toegevoegd en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande website.

   Zie Een interactieve afbeelding [integreren met uw website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

### (Optioneel) Interactieve afbeeldingen voorvertonen {#optional-previewing-interactive-images}

U kunt Voorvertoning gebruiken om een voorstelling te zien van hoe uw interactieve afbeelding eruit zal zien voor klanten en om de hotspots van de afbeelding te testen om te controleren of deze zich gedragen zoals u had verwacht.

Als u tevreden bent met de interactieve afbeelding, kunt u deze publiceren.
See [Embedding the Video or Image Viewer on a Web Page](/help/assets/embed-code.md).
See [Linking URLs to your web application](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van koppelen is niet mogelijk als uw interactieve inhoud koppelingen naar relatieve URL&#39;s bevat, met name koppelingen naar AEM Sites-pagina&#39;s.
See [Adding Dynamic Media Assets to Pages.](/help/assets/adding-dynamic-media-assets-to-pages.md)

**Interactieve afbeeldingen voorvertonen**

1. Navigeer in de weergave Middelen naar een bestaande, door u gemaakte interactieve afbeelding en tik erop om deze te openen in Voorvertoning.
1. Tik in de vervolgkeuzelijst Inhoud linksboven op de pagina Voorvertoning in **[!UICONTROL Viewers.]**
1. Tik in de lijst Viewers op de naam **[!UICONTROL Shoppable_Banner]** of de naam van de voorinstelling voor de interactieve afbeeldingsviewer die u hebt gemaakt.
1. Tik op hotspots in de afbeelding om de bijbehorende acties te testen.

## Interactieve afbeeldingselementen publiceren {#publishing-interactive-image-assets}

Zie Elementen [](/help/assets/publishing-dynamicmedia-assets.md) publiceren voor meer informatie over het publiceren van interactieve afbeeldingselementen.

## Een interactieve afbeelding met uw website integreren {#integrating-an-interactive-image-with-your-website}

Nadat u een bannerafbeelding hebt geüpload, hotspots hebt toegevoegd aan de afbeelding en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw websitepagina.

Als u een AEM Sites-klant bent, kunt u de interactieve afbeelding toevoegen door de component Interactieve media naar de pagina te slepen. See [Adding Dynamic Media Assets to Pages.](/help/assets/adding-dynamic-media-assets-to-pages.md)

Als u een zelfstandige AEM Assets-klant bent, kunt u de interactieve afbeelding handmatig aan uw website toevoegen, zoals in deze sectie wordt beschreven.

1. Kopieer de insluitcode van de gepubliceerde interactieve afbeelding.
See [Embedding the Video or Image Viewer on a Web Page](/help/assets/embed-code.md).

1. Voeg de gekopieerde insluitcode toe op de gewenste locatie op de webpagina.
De gekopieerde insluitcode wordt ingesteld voor een responsieve omgeving, zodat deze automatisch in het toegewezen gebied past.

**Voorbeeld**

De demo-website als voorbeeld gebruiken:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

De foto van de drie mannen is een statische `IMG` tag:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Integratie is zo eenvoudig als het verwijderen van de `IMG` tag en het vervangen door de gekopieerde insluitcode uit AEM Assets. Het resultaat wordt weergegeven in de volgende URL, die de mogelijk onjuiste interactieve afbeelding op de pagina met drie hotspots per cirkel weergeeft:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>De hotspots op de schopbare interactieve afbeelding van de demo-website zijn dan alleen bedoeld voor weergave. zij zijn nog niet geïntegreerd met de bestaande Snelle meningen.

Als u een &#39;uitsnijding&#39; wilt toepassen op een verwisselbare interactieve afbeelding voor een responsieve omgeving, kunt u het configuratiekenmerk Interactive Image opnemen `ZoomView.iscommand` op het pad. Waar `ZoomView` moet de component worden aangeroepen en `iscommand` is de opdracht Uitsnijdafbeelding die u gebruikt.

Zie [ZoomView.iscommand](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html) configuratiekenmerk.

Zie de opdracht [Afbeeldingsserving uitsnijden](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html) .

U bent nu klaar om de interactieve afbeelding te integreren met een bestaande QuickView op uw website.

## Een interactieve afbeelding integreren met een bestaande QuickView {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Deze taak is alleen van toepassing als u een zelfstandige AEM Assets-klant bent.

De laatste stap in dit proces is het integreren van de interactieve afbeelding met een bestaande Quickview-implementatie op uw website. Er is geen oplossing voor de integratie die in alle gevallen werkt. Elke implementatie van Quickview is uniek en een specifieke benadering is nodig die de hulp van een front-end IT persoon het meest waarschijnlijk impliceert.

De bestaande implementatie van QuickView vertegenwoordigt normaal gesproken een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een Quickview URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een Ajax- verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achterste logica keert de overeenkomstige gegevens of inhoud van de Snelle mening terug naar de front-end code.
1. De front-end code laadt de gegevens of de inhoud van de Snelle mening.
1. Naar keuze, zet de front-end code de geladen gegevens van de Snelle mening in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm weer voor de eindgebruiker.

Deze vraag kan onafhankelijke openbare API vraag niet vertegenwoordigen die door de Webpaginalogica van een willekeurige stap kan worden geroepen. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Wanneer een gebruiker op een hotspot in de aanpasbare afbeelding klikt, wordt deze gebruikersinteractie door de viewer afgehandeld, terwijl de aanpasbare interactieve afbeelding stap 1 en gedeeltelijk stap 2 vervangt. De viewer retourneert een gebeurtenis naar de webpagina die alle hotspotgegevens bevat die eerder aan AEM Assets zijn toegevoegd.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die wordt uitgegeven door de mogelijk onjuiste interactieve afbeelding.
* Hiermee maakt u een Quickview-URL op basis van de hotspot-gegevens.
* Triggert het proces om de Snelle mening van het achtereind te laden en het terug te geven op het scherm voor vertoning.

De insluitcode die door AEM Assets wordt geretourneerd, bevat al een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd, zoals in het volgende gemarkeerde codefragment wordt getoond:

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

Het proces voor het samenstellen van de URL van de Snelle weergave is in feite tegengesteld aan het proces voor het identificeren van hotspot-variabelen die eerder zijn behandeld.

Zie [Hotspot-variabelen](#optional-identifying-hotspot-variables)identificeren.

Aan de hand van onze vorige URL-voorbeelden van Quickview kunt u in de volgende voorbeelden zien hoe de URL van de QuickView in elk geval wordt samengesteld:

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

Als u deze URL binnen de `quickViewActivate` handler wilt reconstrueren, kunt u de `categoryId` en `SKU` velden gebruiken die beschikbaar zijn in het `inData` object dat door de code van de viewer aan de handler wordt doorgegeven:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

De demowebsite activeert het dialoogvenster Snelle weergave met een eenvoudige `loadQuickView()` functieaanroep. Deze functie heeft slechts één argument, namelijk de gegevens-URL van de Snelle weergave. Als dusdanig, is de laatste stap nodig om het shoppable interactieve beeld te integreren de volgende lijn van code aan de `quickViewActivate` manager toe te voegen:

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

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html)

## Quickviews gebruiken om aangepaste pop-ups te maken {#using-quickviews-to-create-custom-pop-ups}

See [Using Quickviews to create custom pop-ups](/help/assets/custom-pop-ups.md).
