---
title: Carousel-banners
description: Leer hoe u met carrouselbanners werkt in Dynamic Media
uuid: 73684a08-d84d-4665-ab89-3a1bf88ac5dd
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e26c7f7f-bdd7-421a-8614-ba48abf381d2
docset: aem65
translation-type: tm+mt
source-git-commit: cec6c4f9a1a75eb049dd4b8461c36c8d58d46f79
workflow-type: tm+mt
source-wordcount: '4730'
ht-degree: 2%

---


# Carousel-banners{#carousel-banners}

Met carrouselbanners kunnen marketers de conversie stimuleren door eenvoudig interactieve, draaiende promotionele inhoud te maken en deze op elk scherm te leveren.

Het maken en wijzigen van inhoud in promotiebanners kan tijdrovend zijn, waardoor u minder snel nieuwe inhoud kunt publiceren of deze doelgerichter kunt maken. Met carrouselbanners kunt u snel roterende banners maken of wijzigen, interactiviteit toevoegen, zoals hotspots die aan productdetails of verwante bronnen zijn gekoppeld, en deze op elk scherm afleveren, zodat u nieuwe promotionele inhoud sneller op de markt kunt brengen.

Carousel Banners are designated by a banner with the word **[!UICONTROL CAROUSELSET]**:

![chlimage_1-438](assets/chlimage_1-438.png)

Op uw website kan een carrouselbanner er als volgt uitzien:

![chlimage_1-439](assets/chlimage_1-439.png)

Hier kunt u door de afbeeldingen navigeren (door op de getallen te klikken). Bovendien worden de dia&#39;s automatisch geroteerd op basis van een tijdsinterval dat u kunt aanpassen. Afbeeldingen die u in de carrouselbanner toevoegt, ondersteunen zowel hotspots als afbeeldingen met hyperlinks, waar gebruikers op een hyperlink kunnen tikken of naar een hyperlink kunnen gaan of een venster kunnen openen met een snelle weergave.

In dit voorbeeld heeft een gebruiker op een afbeelding met hyperlinks getikt of geklikt en heeft hij het venster Snel weergeven voor handschoenen geopend:

![chlimage_1-440](assets/chlimage_1-440.png)

## Kijk hoe carrouselbanners zijn gemaakt {#watch-how-carousel-banners-are-created}

Bekijk een 10 minuten en 33 seconden analyse over [hoe carrouselbanners worden gemaakt](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). U leert ook hoe u carrouselbanners kunt voorvertonen, bewerken en afleveren.

>[!NOTE]
>
>Niet-administratieve gebruikers moeten aan de **[!UICONTROL dam-users]** groep worden toegevoegd om carrouselbanners te kunnen tot stand brengen of uitgeven. Als u problemen ondervindt bij het maken of bewerken van bestanden, raadpleegt u de systeembeheerder die u aan de **d[!UICONTROL am-users]** -groep kan toevoegen.

## Snel starten: Carousel Banners {#quick-start-carousel-banners}

Zo kunt u snel aan de slag:

1. [Identificeer hotspot en beeldkaartvariabelen](#identifying-hotspot-and-image-map-variables) (slechts voor klanten die AEM Assets + Dynamische Media gebruiken)

   Begin door dynamische variabelen te identificeren die door de bestaande snelle meningsimplementatie worden gebruikt zodat u hotspots en beeldkaartgegevens behoorlijk tijdens het proces van de de bannerverwezenlijking van de carrousel in AEM Assets kunt ingaan.

   >[!NOTE]
   >
   >Als u een AEM Sites- of e-commerceklanten bent, kunt u de ingebouwde functie gebruiken om naar productpagina&#39;s te navigeren en de bestaande skus in de productcatalogus op te zoeken. U hoeft niet handmatig hotspot- of afbeeldingskaartvariabelen in te voeren. Zie informatie over het [instellen van eCommerce](/help/sites-administering/generic.md).
   >
   >
   >Als u een AEM Assets- en Dynamic Media-klant bent, voert u handmatig gegevens in voor hotspots en afbeeldingen met hyperlinks. Vervolgens integreert u de gepubliceerde URL of de Embed-code met uw externe contentbeheersysteem.

1. Optioneel: [Maak zo nodig een viewervoorinstelling voor een carrouselset](/help/assets/managing-viewer-presets.md).

   Als beheerder kunt u het gedrag en de weergave van de carrousel aanpassen door uw eigen voorinstelling voor de Carousel-viewer te maken. Het belangrijkste voordeel is dat u deze aangepaste viewer-voorinstelling kunt hergebruiken voor meerdere carrousels. Gebruikers kunnen echter ook het gedrag en de weergave van de carrousel rechtstreeks aanpassen tijdens het ontwerpen van de carrousel. Dit is de voorkeursaanpak wanneer u een specifiek ontwerp voor een bepaalde carrousel wilt.

1. [Upload een afbeeldingsbanner](#uploading-image-banners).

   Upload afbeeldingsbanners die u interactief wilt maken.

1. [Maak een Carousel-set](#creating-carousel-sets).

   In Carousels Sets navigeert de gebruiker door bannerafbeeldingen en tikt hij op hotspots of afbeeldingen met hyperlinks om toegang te krijgen tot relevante inhoud.

   Als u een Carousel-set in Elementen wilt maken, tikt u op **[!UICONTROL Create]** en selecteert u Elementen aan dia&#39;s toevoegen. Tik op **[!UICONTROL Carousel Sets.]** **[!UICONTROL Save.]** U kunt de vormgeving en het gedrag van de carrousel ook rechtstreeks in de editor bewerken.

1. [Voeg hotspots of afbeeldingen met hyperlinks toe aan een afbeeldingsbanner.](#adding-hotspots-or-image-maps-to-an-image-banner)

   Voeg een of meer hotspots of afbeeldingen met hyperlinks toe aan een afbeeldingsbanner en koppel deze aan een actie zoals een koppeling, een Snelle weergave of een Experience-fragment. Nadat u hotspots of afbeeldingen met hyperlinks hebt toegevoegd, kunt u deze taak voltooien door de carrouselset te publiceren. Met Publiceren maakt u de insluitcode die u kunt gebruiken om de bestemmingspagina van uw website te kopiëren en toe te passen.

   Zie [(Optioneel) Een voorvertoning weergeven van carrouselbanners](#optional-previewing-carousel-banners) - Optioneel. U kunt desgewenst een voorstelling van de carrouselset weergeven en de interactiviteit ervan testen.

1. [Carrouselbanners publiceren.](#publishing-carousel-banners)

   U publiceert een Carousel-set op dezelfde manier als elk ander element. In Elementen navigeert u naar de Carousel-set, selecteert u deze en tikt u op **[!UICONTROL Publish.]** Een carrousel-set publiceren om de URL en de insluitreeks te activeren.

1. Voer een van de volgende handelingen uit:

   * [Voeg een carrouselbanner toe aan uw websitepagina](#adding-a-carousel-banner-to-your-website-page) . U kunt de URL van de carrouselbanner of de ingesloten code die u naar de websitepagina hebt gekopieerd, toevoegen.

      * [Integreer de carrouselbanner met een bestaande QuickView](#integrating-the-carousel-banner-with-an-existing-quickview). Als u een systeem voor webcontentbeheer van derden gebruikt, moet u de nieuwe carrouselbanner integreren met de bestaande Quickview-implementatie op uw website.
   * [Voeg een carrouselbanner toe aan uw website in AEM](/help/assets/adding-dynamic-media-assets-to-pages.md) Als u een AEM Sites-klant bent, kunt u de carrousel die rechtstreeks op de pagina in AEM is ingesteld, toevoegen met de component Interactieve media.


Zie Carousel Sets [bewerken als u carrouselsets moet bewerken.](#editing-carousel-sets) Bovendien kunt u de eigenschappen [van de](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/managing-assets-touch-ui.html#editing-properties)Carousel-set weergeven en bewerken.

## Variabelen hotspot en afbeelding met hyperlinks identificeren {#identifying-hotspot-and-image-map-variables}

Begin door dynamische variabelen te identificeren die door de bestaande snelle meningsimplementatie worden gebruikt zodat u hotspots of beeldkaartgegevens behoorlijk tijdens het het vastgestelde proces van de carrouselverwezenlijking in AEM Assets kunt ingaan.

Wanneer u hotspots of afbeeldingen met hyperlinks toevoegt aan een bannerafbeelding in AEM Assets, moet u een SKU en optionele aanvullende variabelen toewijzen aan elke hotspot of afbeelding met hyperlinks. Dergelijke variabelen worden later gebruikt om hotspots of afbeeldingen met hyperlinks te laten overeenkomen met inhoud voor snelle weergave.

>[!NOTE]
>
>Als u een AEM Sites en/of AEM ecommerce klant bent, sla deze stap over. U hoeft de hotspot- of afbeeldingskaartvariabelen niet handmatig te identificeren; u kunt de integratie met Ecommerce voor productintegratie gebruiken. Zie informatie over het [instellen van eCommerce](/help/sites-administering/generic.md). Daarnaast kunt u de component Interactive gebruiken en toevoegen aan uw webpagina.
>
>Als u een AEM Assets- of Media-klant bent, publiceert u de URL- of insluitcode en integreert u deze vervolgens met het contentbeheersysteem van derden en identificeert u handmatig hotspots en afbeeldingen met hyperlinks.

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot of beeldkaartgegevens te associëren. Op elke hotspot of afbeeldingskaart die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie staan om het product ondubbelzinnig te identificeren in het bestaande back-endsysteem. Tegelijkertijd mag elke hotspot of afbeelding met hyperlinks niet meer gegevens bevatten dan nodig is. De reden hiervoor is dat het gegevensinvoerproces hierdoor te complex en voortdurend hotspot- of imagekaartbeheer wordt.

Er zijn verschillende manieren om een set variabelen te identificeren die moet worden gebruikt voor hotspot- of afbeeldingskaartgegevens.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande snelle weergave-implementatie, omdat zij waarschijnlijk weten wat de minimale gegevensset is die nodig is om snel zicht in het systeem te vinden. In de meeste gevallen is het echter ook mogelijk om eenvoudig het bestaande gedrag van de front-end code te analyseren.

De meeste snelle weergaveimplementaties gebruiken het volgende paradigma:

* De gebruiker activeert een gebruikersinterface-element op de website. Tik bijvoorbeeld op een knop **[!UICONTROL Quick View]**.
* De website stuurt een Ajax-aanvraag naar de achterkant om de gegevens of inhoud van de snelle weergave te laden, indien nodig.
* De gegevens van de Snelle weergave worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie Snelle weergave is geïmplementeerd, de snelle weergave activeren en de URL van Ajax die via de webpagina is verzonden, vastleggen om de gegevens of inhoud van de Snelle weergave te laden.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Om alle uitgaande HTTP- verzoeken in Google Chrome te zien, druk F12 (Vensters) of Command-Option-I (MAC) om het paneel van de Hulpmiddelen van de Ontwikkelaar te openen, en dan het lusje van het Netwerk te tikken.
* In Firefox kunt u de Firebug-plug-in activeren door op F12 (Windows) of Command-Option-I (Mac) te drukken en het tabblad Net te gebruiken. U kunt ook het ingebouwde paneel en het bijbehorende tabblad Netwerk gebruiken.

Wanneer netwerkcontrole in browser wordt aangezet, teweeg de snelle mening op de pagina.

Zoek nu de snelle weergave van Ajax URL in het netwerklogboek en kopieer de opgenomen URL voor toekomstige analyse. In de meeste gevallen waarin u de snelle weergave activeert, zijn er veel verzoeken die naar de server worden verzonden. Doorgaans is de URL voor een snelle weergave van Ajax een van de eerste in de lijst. Het heeft of een complex gedeelte of een weg van het vraagkoord, en zijn reactieMIME type of, `text/html`, of `text/xml``text/javascript`.

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat snelle weergave-URL&#39;s onderdelen kunnen bevatten die algemeen gelden voor een bepaalde categorie websites, maar deze URL alleen wijzigen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval, is het enige veranderlijke deel in Snelle mening URL productSKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots of afbeeldingen met hyperlinks toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter naast de SKU ook verschillende elementen, zoals categorie-id, kleurcode, code voor grootte enzovoort. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot- of afbeeldingskaart in de bannerfunctie carrousel.

Bekijk de volgende voorbeelden van snelle weergave-URL&#39;s en de resulterende hotspot- of afbeeldingskaartvariabelen:

<table>
 <tbody>
  <tr>
   <td>Enige SKU, die in het vraagkoord wordt gevonden.</td>
   <td><p>De opgenomen snelle weergave-URL's bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Het enige variabele deel in URL is de waarde van de parameter van het <code>productId=</code> vraagkoord, en het is duidelijk een waarde SKU. Daarom hebben onze hotspots of afbeeldingen met hyperlinks alleen SKU-velden nodig die zijn gevuld met waarden zoals <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td>
  </tr>
  <tr>
   <td>Eén SKU, gevonden in het URL-pad.</td>
   <td><p>De opgenomen snelle weergave-URL's bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/product/6422350843</code></p> </li>
     <li><p><code>https://server/product/1607745002</code></p> </li>
     <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van de hotspots/afbeeldingen met hyperlinks:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td>
  </tr>
  <tr>
   <td>SKU en categorie-id in de queryreeks.</td>
   <td><p>De opgenomen snelle weergave-URL's bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. SKU wordt opgeslagen in de <code>prodId</code> parameter en categorie ID wordt opgeslagen in de <code>category=</code>parameter.</p> <p>De definities van hotspot/afbeelding met hyperlinks zijn dus paren. Dat wil zeggen, een SKU-waarde en een aanvullende variabele <code>categoryId</code>. De resulterende paren zijn:</p>
    <ul>
     <li><p>SKU is <strong><code>305466</code></strong> en <code>categoryId</code> is <code>1100004</code>.</p> </li>
     <li><p>SKU is <strong><code>310181</code></strong> en <code>categoryId</code> is <strong><code>1100004</code></strong>.</p> </li>
     <li><p>SKU is <strong><code>308706</code></strong> en <code>categoryId</code> is <strong><code>1740148</code></strong>.</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Beeldbanners uploaden {#uploading-image-banners}

Als u de afbeeldingen die u wilt gebruiken al hebt geüpload, gaat u naar de volgende stap [Carousel-sets](#creating-carousel-sets)maken. Houd er rekening mee dat de afbeeldingen die in de carrousel worden gebruikt, moeten worden geüpload nadat Dynamic Media is ingeschakeld.

Zie [Elementen](/help/assets/manage-assets.md)uploaden om afbeeldingsbanners te uploaden.

## Carrouselsets maken {#creating-carousel-sets}

>[!NOTE]
>
>Niet-administratieve gebruikers moeten aan de **[!UICONTROL dam-users]** groep worden toegevoegd om carrouselbanners te kunnen tot stand brengen of uitgeven. Als u problemen ondervindt bij het maken of bewerken, raadpleegt u de systeembeheerder die u aan de **[!UICONTROL dam-users]** groep kan toevoegen.

**Een Carousel-set maken**

1. Navigeer in Elementen naar de map waar u de Carousel-set wilt maken en tik op **[!UICONTROL Create > Carousel Set.]**
1. Tik op de pagina Carousel Banner Editor op **[!UICONTROL Tap to open Asset Selector]** om de afbeelding voor de eerste dia te selecteren.

   Voer een van de volgende handelingen uit op de pagina Carousel Banner Editor:

   * Near the upper-left corner of the page, tap **[!UICONTROL Add Slide]** icon.

   * Tik in het midden van de pagina op **[!UICONTROL Tap to open Asset Selector.]**
   Tik om assets te selecteren die u in de carrouselset wilt opnemen. Geselecteerde assets hebben een vinkje. When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Select]**.

   Met de Asset Selector kunt u zoeken naar elementen door een trefwoord in te voeren en te tikken of door te klikken op **[!UICONTROL Return.]** U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Change the view by tapping the View icon and selecting **[!UICONTROL Column View]**, **[!UICONTROL Card View]**, or **[!UICONTROL List View.]**

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md) voor meer informatie.

1. Ga door met het toevoegen van dia&#39;s totdat u alle afbeeldingen hebt toegevoegd die u wilt roteren in de Carousel-set.
1. (Optioneel) Voer een van de volgende handelingen uit:

   * Sleep indien nodig dia&#39;s om de volgorde van de afbeeldingen in de lijst te wijzigen.
   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en tikt u op **[!UICONTROL Delete Slide]** de werkbalk.

   * Als u een voorinstelling wilt toepassen, klikt u in de rechterbovenhoek van de pagina op de vervolgkeuzelijst met voorinstellingen en selecteert u vervolgens een voorinstelling die u tegelijk op de set wilt toepassen.
   Als u een dia wilt verwijderen, tikt u op de dia of klikt u op de dia en tikt u of klikt u op **[!UICONTROL Delete Slide]** de werkbalk. Als u een dia wilt verplaatsen, tikt u op het invoegpictogram en houdt u de muisknop ingedrukt en verplaatst u de gewenste locatie.

1. Nadat u de afbeeldingen in dia&#39;s hebt toegevoegd, kunt u een hotspot, afbeelding met hyperlinks of beide toevoegen aan uw afbeelding. Zie hotspots of afbeeldingen met hyperlinks [toevoegen](#adding-hotspots-or-image-maps-to-an-image-banner).
1. U kunt het visuele ontwerp en het gedrag van carrouselsets wijzigen door op de tabbladen Gedrag en Weergave te tikken of door aanpassingen aan te brengen in de vormgeving van de carrouselbanner of in de manier waarop bepaalde componenten zich gedragen. Zie Voorinstellingen [voor viewers](/help/assets/viewer-presets.md) beheren voor meer informatie over het gebruik van de viewer-editor.

   >[!NOTE]
   >
   >Voor carrouselbanners kunt u het volgende aanpassen:
   >    * Duur waarin een afbeelding wordt weergegeven. Standaard wordt elke afbeelding 9 seconden weergegeven.
   >    * Animatie. Elke dia-overgang is standaard vervagen. U kunt dat wijzigen in een dia-overgang.
   >    * Stijl van de knoppen. Gebruikers kunnen door de banners roteren door op elke punt of elk getal te tikken. U kunt wijzigen waar de knoppen van de ingestelde indicator worden weergegeven (en of ze numeriek of gestippeld zijn) en hoe groot ze zijn.
   >    * Wijzig de markeerstijl van een afbeeldingskaart of het pictogram dat voor hotspots wordt gebruikt.
   >    * Voordat u een viewervoorinstelling bewerkt, kiest u de stijl waarvan u de voorinstelling wilt baseren. Als u dit niet doet en u de voorinstelling van de viewer gaat bewerken, gaan alle wijzigingen verloren als u een andere voorinstelling kiest.

   >
   >Zie [Speciale overwegingen voor Carousel Banners](/help/assets/managing-viewer-presets.md#special-considerations-for-creating-a-carousel-banner-viewer-preset) voor gedetailleerde instructies en meer informatie over de viewer editor.

   U kunt ook een voorvertoning weergeven van hoe de carrouselbanner eruitziet. Zie [(Optioneel) Een voorvertoning weergeven van carrouselbanners](#optional-previewing-carousel-banners).

1. Tik **[!UICONTROL Save]** als u klaar bent.

## Hotspots of afbeeldingen met hyperlinks toevoegen aan een afbeeldingsbanner {#adding-hotspots-or-image-maps-to-an-image-banner}

Met de Carousel-set-editor kunt u hotspots of afbeeldingen met hyperlinks toevoegen aan een banner.

Wanneer u hotspots of afbeeldingen met hyperlinks toevoegt, kunt u deze definiëren als een pop-upweergave in QuickView, als een hyperlink of als een Experience-fragment.

Zie Fragment [](/help/sites-authoring/experience-fragments.md)ervaren.

>[!NOTE]
>
>Houd er rekening mee dat de gereedschappen voor het delen van sociale media in Carousel Banner niet worden ondersteund wanneer u de viewer insluit in een Experience Fragment.
>
>U kunt dit omzeilen door voorinstellingen voor viewers te gebruiken of te maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Terwijl u hotspots of afbeeldingen met hyperlinks toevoegt aan een afbeelding, vergeet dan niet uw werk op te slaan. Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw carrouselbanner, kunt u Voorvertoning optioneel gebruiken om een voorstelling te zien van hoe uw carrouselbanner aan klanten wordt weergegeven.

Zie [(Optioneel) Een voorvertoning weergeven van carrouselbanners.](#optional-previewing-carousel-banners)

>[!NOTE]
>
>Wanneer u hotspots toevoegt aan een afbeelding in een [interactieve afbeelding](/help/assets/interactive-images.md) of een carrouselbanner, worden de hotspot-gegevens opgeslagen in dezelfde metagegevenslocatie, relatief ten opzichte van de locatie van de afbeelding, ongeacht of het een interactieve afbeelding of een carrouselbanner betreft. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.

>Houd er echter rekening mee dat Carousel Banners afbeeldingen met hyperlinks ondersteunen op afbeeldingen die ook hotspots kunnen bevatten. een interactieve afbeelding niet. Houd hier rekening mee als u een interactieve afbeelding of Carousel Banner wilt maken die dezelfde afbeelding gebruikt. U kunt interactieve afbeeldingen en carrouselbanners maken met afzonderlijke kopieën van dezelfde afbeelding.

>[!NOTE]
Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

Zie ook Afbeeldingskaarten [toevoegen](/help/assets/image-maps.md).

**Hotspots of afbeeldingen met hyperlinks toevoegen aan een afbeeldingsbanner**

1. Navigeer vanuit Middelen naar de carrouselset die u interactief wilt maken.
1. Selecteer de carrouselset en tik op **[!UICONTROL Edit.]** de carrousel Viewer Editor.
1. Selecteer de dia die u interactief wilt maken.
1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL Hotspot]** of **[!UICONTROL Image Map.]**
1. Voer een van de volgende handelingen uit:

   * Voor hotspots: Tik in de afbeelding op een locatie waar u de hotspot wilt weergeven.
   * Voor afbeeldingen met hyperlinks: Klik in de afbeelding en sleep van linksboven naar rechtsonder om het gebied met de afbeeldingskaart te maken. U kunt de grootte van de afbeelding met hyperlinks aanpassen door de hoeken te slepen.

   Sleep indien nodig de hotspot of de afbeelding met hyperlinks naar een nieuwe locatie. Voeg desgewenst extra hotspots of afbeeldingen met hyperlinks toe.

   Tik op het tabblad **[!UICONTROL Actions]** om een hotspot of afbeelding met hyperlinks te verwijderen. Selecteer onder de kop **[!UICONTROL Maps & Hotspots]** in het vervolgkeuzemenu **[!UICONTROL Selected Type]** de naam van de hotspot of de afbeelding met hyperlinks die u wilt verwijderen. Tik op het pictogram **[!UICONTROL Trash]** naast het menu en tik vervolgens op **[!UICONTROL Delete.]**

1. Typ in het tekstveld Naam de naam van de hotspot of de afbeelding met hyperlinks. Deze naam wordt ook weergegeven in de **[!UICONTROL Maps & Hotspot]** vervolgkeuzelijst. Als u een naam opgeeft, kunt u de hotspot of de afbeelding met hyperlinks gemakkelijk herkennen als u er later wijzigingen in wilt aanbrengen.
1. Voer op het **[!UICONTROL Actions]** tabblad een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Quickview.]**

      * Als u een AEM Sites- en e-commerceklanten bent, tikt u op het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen. Tik op het product dat u wilt gebruiken en tik vervolgens op het vinkje in de rechterbovenhoek van de pagina om terug te keren naar de Carousel Banner Editor.
      * Als u geen klant van AEM Sites of van de Handel bent

         * Zie [Hotspotvariabelen](#identifying-hotspot-and-image-map-variables) identificeren aangezien u deze variabelen kunt willen bepalen.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU (Stock Keeping Unit) van het product. Dit is een unieke id voor elk afzonderlijk product of elke service die u aanbiedt. De ingevoerde waarde van SKU bevolkt automatisch het veranderlijke gedeelte van het snelle meningsmalplaatje zodat het systeem weet om aangewezen hotspot met een bepaalde snelle mening van SKU te associëren.
         * (Optioneel) Als er andere variabelen in de snelle weergave zijn die u nodig hebt om een product nader te identificeren, tikt u op **[!UICONTROL Add Generic Variable.]** In het tekstveld en geeft u een extra variabele op. category=Mens is bijvoorbeeld een toegevoegde variabele.

         * Zie [Werken met kiezers](/help/assets/working-with-selectors.md) voor meer informatie.
   * Tik op **[!UICONTROL Hyperlink.]**

      * Als u een AEM Sites-klant bent, tikt u op het pictogram Sitekiezer (map) om naar een URL te navigeren.
         >[!NOTE]
         De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met AEM Sites pagina&#39;s heeft.

      * Als u een zelfstandige klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [Werken met kiezers](/help/assets/working-with-selectors.md) voor meer informatie.

   * Tik op **[!UICONTROL Experience Fragment.]**

      * Als u een AEM Sites-klant bent, tikt u op het zoekpictogram (vergrootglas) om de pagina Experience Fragment te openen. Tik op het gewenste fragment voor beleving of klik op het gewenste fragment. Tik vervolgens op Selecteren in de rechterbovenhoek van de pagina om terug te keren naar de pagina Hotspot-beheer.
Zie Fragmenten [ervaren](/help/sites-authoring/experience-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals dit wordt weergegeven op de banner.

         >[!NOTE]
         Houd er rekening mee dat de gereedschappen voor het delen van sociale media in Carousel Banner niet worden ondersteund wanneer u de viewer insluit in een Experience Fragment.
         U kunt dit omzeilen door voorinstellingen voor viewers te gebruiken of te maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.
   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   U kunt ook een voorvertoning weergeven van hoe de carrouselbanner eruitziet. Zie [(Optioneel) Een voorvertoning weergeven van carrouselbanners](#optional-previewing-carousel-banners).

1. Tik op **[!UICONTROL Save.]**
1. Publiceer de carrouselset. Bij het publiceren wordt de insluitcode of URL gemaakt die u op uw websitepagina kunt gebruiken. Als u een AEM Sites-klant bent, kunt u de carrousel rechtstreeks aan uw webpagina toevoegen.

   Zie [Elementen](/help/assets/publishing-dynamicmedia-assets.md)publiceren.

   Zie Een carrousel [toevoegen die is ingesteld op de bestemmingspagina van uw website](#adding-a-carousel-banner-to-your-website-page)

## Carrouselsets bewerken {#editing-carousel-sets}

>[!NOTE]
Niet-administratieve gebruikers moeten aan de **[!UICONTROL dam-users]** groep worden toegevoegd om carrouselbanners te kunnen tot stand brengen of uitgeven. Als u problemen ondervindt bij het maken of bewerken, raadpleegt u de systeembeheerder die u aan de **[!UICONTROL dam-users]** groep kan toevoegen.

U kunt diverse bewerkingstaken uitvoeren op Carousel Sets, zoals:

* Voeg dia&#39;s toe aan een Carousel-set. Zie ook [Werken met kiezers](/help/assets/working-with-selectors.md).
* Wijzig de volgorde van de dia&#39;s in de carrousel-set.
* Elementen in de Carousel-set verwijderen.
* Een viewervoorinstelling toepassen.
* Verwijder de carrouselset.
* Voeg hotspots en afbeeldingen met hyperlinks toe of bewerk deze. Zie ook [Werken met kiezers](/help/assets/working-with-selectors.md).

**Een Carousel-set bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een Carousel-set element en tik vervolgens op **[!UICONTROL Edit]** (potloodpictogram).
   * Houd de muisaanwijzer boven een Carousel-set-element, tik op **[!UICONTROL Select]** (vinkje) en tik vervolgens op **[!UICONTROL Edit]** de werkbalk.

   * Tap on a Carousel Set asset, then in the upper-left corner of the page tap **[!UICONTROL Edit]** (pencil icon).

1. Voer een van de volgende handelingen uit om de Carousel-set te bewerken:

   * To add a slide, tap the **[!UICONTROL Add Slide]** icon then navigate to the asset you want to add to that slide and tap or click the checkmark.
   * Als u de volgorde van de dia&#39;s wilt wijzigen, sleept u een dia naar een nieuwe locatie (selecteer het pictogram voor herschikken om items te verplaatsen).
   * Als u een hotspot of afbeelding met hyperlinks wilt toevoegen, klikt u op de pictogrammen voor hotspots of afbeeldingen met hyperlinks en ziet u hotspots en afbeeldingen met [hyperlinks](#adding-hotspots-or-image-maps-to-an-image-banner)toevoegen.
   * To edit the appearance or behavior of the carousel set, tap the **[!UICONTROL Appearance]** tab or **[!UICONTROL Behavior]** tab, then set the options you want.
   * Als u hotspots of afbeeldingen met hyperlinks wilt bewerken, selecteert u op de juiste dia een hotspot of afbeelding met hyperlinks en brengt u de gewenste wijzigingen aan onder het **[!UICONTROL Actions]** tabblad.
   * Als u een dia wilt verwijderen, selecteert u de dia en tikt u op **[!UICONTROL Delete Slide]** de werkbalk.
   * To apply a preset, near the upper-right corner of the page, tap the **[!UICONTROL Preset]** drop-down list, then select a viewer preset.
   * Als u een volledige Carousel-set wilt verwijderen, navigeert u naar de Carousel-set, selecteert u deze en tikt u op **[!UICONTROL Delete.]**

   >[!NOTE]
   Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

## (Optioneel) Voorvertoning van carrouselbanners bekijken {#optional-previewing-carousel-banners}

Met Voorvertoning kunt u zien hoe uw carrouselbanner eruit ziet voor klanten en kunt u de hotspots voor carrouselbanners en afbeeldingen met hyperlinks testen om te controleren of deze zich gedragen zoals u had verwacht.

Wanneer u tevreden bent met de carrouselbanner, kunt u deze publiceren.
See [Embedding the Video or Image Viewer on a Web Page](/help/assets/embed-code.md).
See [Linking URLs to your web application](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van koppelen is niet mogelijk als uw interactieve inhoud koppelingen naar relatieve URL&#39;s bevat, met name koppelingen naar AEM Sites-pagina&#39;s.
See [Adding Dynamic Media Assets to pages.](/help/assets/adding-dynamic-media-assets-to-pages.md)

U kunt een voorvertoning van carrouselbanners weergeven in de Carousel Editor (voorkeursmethode) of in de **[!UICONTROL Viewers]** lijst.

**Een voorvertoning weergeven van carrouselbanners**

1. Navigeer in **[!UICONTROL Assets]** de toepassing naar een bestaande carrouselbanner die u hebt gemaakt en tik op deze banner om deze te openen.
1. Tik op **[!UICONTROL Edit.]**
1. Selecteer in de lijst met voorinstellingen voor viewers in de rechterhoek van de werkbalk een viewer voor een voorvertoning van de carrouselbanner.

   ![experience_fragment-carouselbanner-viewerdropdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Tik op **[Voorvertoning.]**
1. Tik op de hotspots of afbeeldingen met hyperlinks op de afbeelding om de bijbehorende handelingen te testen.

**Een voorvertoning van carrouselbanners weergeven in de lijst Viewers**

1. Navigeer in **[!UICONTROL Assets]** de toepassing naar een bestaande carrouselbanner die u hebt gemaakt en tik op deze banner om deze te openen.
1. Klik in de linkerbovenhoek van de voorvertoningspagina op het pictogram Inhoud.
1. Tik in de **[!UICONTROL Viewers]** lijst in het deelvenster aan de linkerkant van de pagina op de naam van de voorinstelling voor de carrouselbannerviewer die u wilt gebruiken.
1. Tik op de hotspots of afbeeldingen met hyperlinks op de afbeelding om de bijbehorende handelingen te testen.

## Carrouselbanners publiceren {#publishing-carousel-banners}

U moet de carrousel publiceren om deze te kunnen gebruiken. Als u een Carousel-set publiceert, worden de URL en de insluitcode geactiveerd. De carrousel wordt ook gepubliceerd naar de Dynamic Media-cloud, die is geïntegreerd met een CDN voor schaalbare en krachtige levering.

>[!NOTE]
Als u een bestaande interactieve afbeelding met hotspots voor uw carrouselbanner gebruikt, moet u de interactieve afbeelding afzonderlijk publiceren nadat u de carrouselbanner hebt gepubliceerd.
Als u een reeds gepubliceerde interactieve afbeelding wijzigt die u in een carrouselbanner gebruikt, moet u de interactieve afbeelding publiceren voordat deze wijzigingen worden weerspiegeld in de carrouselbanner.

Zie Dynamische media-elementen [publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor informatie over het publiceren van carrouselbanners.

## Een carrouselbanner toevoegen aan uw websitepagina {#adding-a-carousel-banner-to-your-website-page}

Nadat u bannerafbeeldingen hebt geüpload om een carrousel te maken, hotspots en/of afbeeldingen met hyperlinks naar de banner hebt toegevoegd en de carrouselset hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande websitepagina.

>[!NOTE]
Als u een AEM Sites-klant bent, kunt u de carrouselbanner rechtstreeks aan de pagina toevoegen door de component Interactieve media naar de pagina te slepen. See [Adding Dynamic Media Assets to Pages.](/help/assets/adding-dynamic-media-assets-to-pages.md)

Als u echter een zelfstandige AEM bent, kunt u de carrouselbanner handmatig toevoegen aan de bestemmingspagina van uw website, zoals beschreven in deze sectie.

1. Kopieer de insluitcode van de gepubliceerde carrouselset.
See [Embedding the Video or Image Viewer on a Web Page](/help/assets/embed-code.md).

1. Voeg de insluitcode die u van AEM Assets hebt gekopieerd, toe aan uw webpagina.
De gekopieerde insluitcode reageert hierop, zodat deze automatisch in het insluitingsgebied van de pagina past.

## De Carousel Banner integreren met een bestaande QuickView {#integrating-the-carousel-banner-with-an-existing-quickview}

Opmerking: deze stap is alleen van toepassing als u een zelfstandige AEM Assets-klant bent.

De laatste stap in dit proces is het integreren van de carrouselbanner met een bestaande snelle weergave-implementatie op uw website. Elke snelle implementatie van de mening is uniek en een specifieke benadering is nodig die de hulp van een front-end persoon van IT het meest waarschijnlijk impliceert.

De bestaande implementatie van Snelle weergave vertegenwoordigt doorgaans een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een snelle mening URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een Ajax- verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achtergrondlogica retourneert de corresponderende gegevens of inhoud van de Snelle weergave terug naar de front-end code.
1. De front-end code laadt de snelle meningsgegevens of inhoud.
1. Naar keuze, zet de voorste-eindcode de geladen snelle meningsgegevens in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm weer voor de eindgebruiker.

Deze vraag kan onafhankelijke openbare API vraag niet vertegenwoordigen die door de Webpaginalogica van een willekeurige stap kan worden geroepen. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Wanneer een gebruiker op een hotspot of afbeelding met hyperlinks in de carrouselbanner klikt en tegelijkertijd de carrouselbanner stap 1 en gedeeltelijk stap 2 vervangt, wordt deze gebruikersinteractie door de viewer afgehandeld. De viewer retourneert een gebeurtenis naar de webpagina die alle eerder toegevoegde hotspot- of afbeeldingskaartgegevens bevat.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die door de carrouselbanner wordt uitgegeven.
* Hiermee maakt u een URL voor een snelle weergave op basis van de gegevens van de hotspot of afbeelding met hyperlinks.
* Triggert het proces waarbij de snelle weergave vanaf de achtergrond wordt geladen en op het scherm wordt weergegeven voor weergave.

De insluitcode die door AEM Assets wordt geretourneerd, bevat al een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd.

Het is dus alleen nodig de commentaarmarkering van de code ongedaan te maken en de dummy-handlertekst te vervangen door de code die specifiek is voor de specifieke webpagina.

Het proces voor het samenstellen van de URL van de Snelle weergave is in feite tegengesteld aan het proces voor het identificeren van hotspot- en afbeeldingskaartvariabelen die eerder zijn behandeld.

Zie [Variabelen](#identifying-hotspot-and-image-map-variables)voor hotspots en afbeeldingen met hyperlinks identificeren.

De laatste stap om de snelle mening URL teweeg te brengen en het snelle meningspaneel te activeren vereist hoogstwaarschijnlijk de hulp van een front-end IT persoon van uw afdeling van IT. Ze beschikken over de kennis om te weten hoe u de implementatie van de snelle weergave nauwkeurig kunt activeren vanuit de juiste stap en beschikken over een kant-en-klare URL voor snelle weergave.

## Quickviews gebruiken om aangepaste pop-ups te maken {#using-quickviews-to-create-custom-pop-ups}

See [Using Quickviews to create custom pop-ups](/help/assets/custom-pop-ups.md).
