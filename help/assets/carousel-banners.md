---
title: Carousel-banners
description: Leer hoe u met carrouselbanners werkt in Dynamic Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: Carousel Banners
role: User, Admin
exl-id: 53d34d3a-ecb6-4fa0-9665-60d21f48021e
solution: Experience Manager, Experience Manager Assets
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '4596'
ht-degree: 2%

---

# Carousel-banners{#carousel-banners}

Met carrouselbanners kunnen marketers de conversie stimuleren door eenvoudig interactieve, draaiende promotionele inhoud te maken en deze op elk scherm te leveren.

Het maken en wijzigen van inhoud in promotiebanners kan tijdrovend zijn, waardoor u minder snel nieuwe inhoud kunt publiceren of deze doelgerichter kunt maken. Met carrouselbanners kunt u snel roterende banners maken of wijzigen. U kunt interactiviteit toevoegen zoals hotspots die aan productdetails of verwante middelen verbinden, en hen leveren aan om het even welk scherm - latend u nieuwe promotionele inhoud aan markt sneller brengt.

Carrouselbanners worden aangeduid door een banner met het woord **[!UICONTROL CAROUSELSET]**

![ chlimage_1-438 ](assets/chlimage_1-438.png)

Op uw website kan een carrouselbanner er als volgt uitzien:

![ chlimage_1-439 ](assets/chlimage_1-439.png)

Hier kunt u door de afbeeldingen navigeren (door op de nummers te klikken). Bovendien worden de dia&#39;s automatisch geroteerd op basis van een tijdsinterval dat u kunt aanpassen. Afbeeldingen die u in carrouselbanners toevoegt, ondersteunen zowel hotspots als afbeeldingen met hyperlinks, waarbij gebruikers een hyperlink kunnen selecteren of naar een hyperlink kunnen gaan of toegang kunnen krijgen tot een Quickview-venster.

In dit voorbeeld heeft een gebruiker op een afbeelding met hyperlinks getikt of erop geklikt en heeft hij het venster QuickView voor handschoenen geopend:

![ chlimage_1-440 ](assets/chlimage_1-440.png)

## Kijk hoe carrouselbanners zijn gemaakt {#watch-how-carousel-banners-are-created}

Speel een analyse op [ hoe de carrouselbanners ](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 minuten en 33 seconden) worden gecreeerd. U leert ook hoe u carrouselbanners kunt voorvertonen, bewerken en afleveren.

>[!NOTE]
>
>Gebruikers zonder beheerdersrechten moeten worden toegevoegd aan de **[!UICONTROL `dam-users`]** -groep om carrouselbanners te kunnen maken of bewerken. Als u problemen ondervindt bij het maken of bewerken, raadpleegt u de systeembeheerder die u aan de groep **[!UICONTROL `dam-users`]** kan toevoegen.

## Snel starten: Carousel-banners {#quick-start-carousel-banners}

Zo kunt u snel aan de slag met carrouselbanners:

1. [ identificeer hotspot en beeld kaartvariabelen ](#identifying-hotspot-and-image-map-variables) (slechts voor klanten die Experience Manager Assets + Dynamic Media gebruiken)

   Begin door dynamische variabelen te identificeren die door de bestaande implementatie van QuickView worden gebruikt zodat u hotspots en beeldkaartgegevens behoorlijk tijdens het proces van de de bannerverwezenlijking van de carrousel in Adobe Experience Manager Assets kunt ingaan.

   >[!NOTE]
   >
   >Als u een klant van Experience Manager Sites of van de Handel bent, kunt u de ingebouwde eigenschap gebruiken om aan productpagina&#39;s te navigeren en bestaande SKUs (de Houdende Eenheid van het Beeld) in de productcatalogus te zoeken. U hoeft niet handmatig hotspot- of afbeeldingskaartvariabelen in te voeren. Zie informatie over [ vestiging eCommerce ](/help/commerce/cif-classic/administering/generic.md).
   >
   >
   >Als u een Experience Manager Assets- en Dynamic Media-klant bent, voert u handmatig gegevens in voor hotspots en afbeeldingen met hyperlinks. Vervolgens integreert u de gepubliceerde URL of de Embed-code met uw externe contentbeheersysteem.

1. Optioneel: [Maak zo nodig een viewervoorinstelling voor een carrouselset](/help/assets/managing-viewer-presets.md).

   Als beheerder kunt u het gedrag en de weergave van de carrousel aanpassen door uw eigen voorinstelling voor de Carousel-viewer te maken. Het belangrijkste voordeel is dat u deze aangepaste viewer-voorinstelling kunt hergebruiken voor meerdere carrousels. Gebruikers kunnen het gedrag en de weergave van de carrousel echter desgewenst rechtstreeks aanpassen tijdens het ontwerpen van de carrousel. Deze methode heeft de voorkeur wanneer u een specifiek ontwerp voor een bepaalde carrousel wilt.

1. [ upload een Banner van het Beeld ](#uploading-image-banners).

   Upload afbeeldingsbanners die u interactief wilt maken.

1. [ creeer de Reeksen van Carousel ](#creating-carousel-sets).

   In de Reeksen van Carrousels, navigeren de gebruikers door bannerbeelden en selecteren hotspots of beeldkaarten om tot relevante inhoud toegang te hebben.

   Als u een Carousel-set wilt maken in Assets, selecteert u **[!UICONTROL Create]** en vervolgens **[!UICONTROL Carousel Sets]** . Voeg elementen toe aan elke dia en selecteer **[!UICONTROL Save]** . U kunt de weergave en het gedrag van de carrousel ook rechtstreeks in de editor bewerken.

1. [ voeg hotspots of beeldkaarten aan een Banner van het Beeld toe ](#adding-hotspots-or-image-maps-to-an-image-banner).

   Voeg een of meer hotspots of afbeeldingen met hyperlinks toe aan een afbeeldingsbanner en koppel deze aan een actie zoals een koppeling, een Snelle weergave of een Experience-fragment. Nadat u hotspots of afbeeldingen met hyperlinks hebt toegevoegd, kunt u deze taak voltooien door de carrouselset te publiceren. Met Publiceren maakt u de insluitcode die u kunt gebruiken om de bestemmingspagina van uw website te kopiëren en toe te passen.

   Zie [ (Optioneel) Voorvertoning van carrouselbanners weergeven ](#optional-previewing-carousel-banners) - Optioneel. U kunt desgewenst een voorstelling van de carrouselset weergeven en de interactiviteit ervan testen.

1. [ Publish carrouselbanners ](#publishing-carousel-banners).

   U publiceert een Carousel-set op dezelfde manier als elk ander element. Navigeer in Assets naar de Carousel-set, selecteer deze en selecteer **[!UICONTROL Publish]** . Als u een Carousel-set publiceert, worden de URL en de insluittekenreeks geactiveerd.

1. Voer een van de volgende handelingen uit:

   * [ voeg een carrouselbanner aan uw website toe ](#adding-a-carousel-banner-to-your-website-page) u kunt carrouselbanner URL toevoegen of code inbedden u op de website pagina hebt gekopieerd.

      * [ integreer de carrouselbanner met een bestaande QuickView ](#integrating-the-carousel-banner-with-an-existing-quickview). Als u een systeem voor webcontentbeheer van derden gebruikt, moet u de nieuwe carrouselbanner integreren met de bestaande Quickview-implementatie op uw website.

   * [ voeg een carrouselbanner aan uw website in Experience Manager ](/help/assets/adding-dynamic-media-assets-to-pages.md) toe als u een klant van Experience Manager Sites bent u de carrousel kunt toevoegen die direct aan de pagina in Experience Manager wordt geplaatst, gebruikend de Interactieve component van Media.

Om de Reeksen van Carousel uit te geven, zie [ het uitgeven Carousel Reeksen ](#editing-carousel-sets). Bovendien kunt u [ Carousel - vastgestelde eigenschappen ](manage-assets.md#editing-properties) bekijken en uitgeven.

## Variabelen hotspot en afbeelding met hyperlinks identificeren {#identifying-hotspot-and-image-map-variables}

Begin door dynamische variabelen te identificeren die door de bestaande implementatie van QuickView worden gebruikt zodat u hotspots of beeldkaartgegevens behoorlijk tijdens het proces van de carrouselreeks creatie in Experience Manager Assets kunt ingaan.

Wanneer u hotspots of afbeeldingen met hyperlinks toevoegt aan een bannerafbeelding in Experience Manager Assets, wijst u een SKU en optionele extra variabelen toe aan elke hotspot of afbeelding met hyperlinks. Dergelijke variabelen worden later gebruikt om hotspots of afbeeldingen met hyperlinks te laten overeenkomen met Quickview-inhoud.

>[!NOTE]
>
>Als u een klant van de Handel van Experience Manager Sites en/of van de Experience Manager bent, sla deze stap over. U hoeft niet handmatig hotspot- of afbeeldingskaartvariabelen te identificeren; u kunt de integratie met e-commerce gebruiken voor productintegratie. Zie informatie over [ vestiging eCommerce ](/help/commerce/cif-classic/administering/generic.md). Daarnaast kunt u de component Interactive gebruiken en toevoegen aan uw webpagina.
>
>Als u een Experience Manager Assets- of Media-klant bent, publiceert u de URL- of insluitcode en integreert u deze vervolgens met het contentbeheersysteem van derden en identificeert u handmatig hotspots en afbeeldingen met hyperlinks.

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot of beeldkaartgegevens te associëren. Op elke hotspot of afbeeldingskaart die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie staan om het product ondubbelzinnig te identificeren in het bestaande back-endsysteem. Tegelijkertijd mag elke hotspot of afbeelding met hyperlinks niet meer gegevens bevatten dan nodig is. De reden hiervoor is dat het gegevensinvoerproces hierdoor te complex en voortdurend hotspot- of imagekaartbeheer wordt.

Er zijn verschillende manieren om een set variabelen te identificeren die moet worden gebruikt voor hotspot- of afbeeldingskaartgegevens.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande implementatie van QuickView. Zij zullen waarschijnlijk weten wat de minimumreeks gegevens wordt vereist om Snelle mening in het systeem te identificeren. Meestal is het echter ook mogelijk om gewoon het bestaande gedrag van de front-end code te analyseren.

De meeste implementaties van de Snelle mening gebruiken het volgende paradigma:

* De gebruiker activeert een gebruikersinterface-element op de website. Tik bijvoorbeeld op een knop **[!UICONTROL Quickview]**.
* De website verzendt een Ajax-aanvraag naar de achterkant om de Quickview-gegevens of -inhoud te laden, indien nodig.
* De Quickview-gegevens worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie QuickView is geïmplementeerd. Trigger de Snelle mening, en vang Ajax URL die door Web-pagina wordt verzonden voor het laden van de gegevens of de inhoud van de Snelle mening wordt verzonden.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Als u alle uitgaande HTTP-aanvragen in Google Chrome wilt bekijken, drukt u op F12 (Windows) of Command-Option-I (Mac) om het deelvenster Gereedschappen voor ontwikkelaars te openen en selecteert u vervolgens het tabblad Netwerk.
* In Firefox kunt u de Firebug-plug-in activeren door op F12 (Windows) of Command-Option-I (Mac) te drukken en het tabblad Net te gebruiken. U kunt ook het ingebouwde paneel en het bijbehorende tabblad Netwerk gebruiken.

Wanneer netwerkcontrole in browser wordt aangezet, teweeg de Snelle mening op de pagina.

Zoek nu de URL van Quickview Ajax in het netwerklogboek en kopieer de geregistreerde URL voor toekomstige analyse. Gewoonlijk wanneer u de Quickview teweegbrengt zijn er talrijke verzoeken die naar de server worden verzonden. De URL van Quickview Ajax is doorgaans een van de eerste in de lijst. Het heeft een complex gedeelte of pad voor een querytekenreeks en het MIME-type voor reactie is `text/html` , `text/xml` of `text/javascript` .

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat URL&#39;s in de Snelle weergave onderdelen bevatten die algemeen gelden voor een bepaalde categorie websites, maar deze alleen wijzigen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval, is het enige veranderlijke deel in Quickview URL productSKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots of afbeeldingen met hyperlinks toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter verschillende elementen die naast de SKU verschillen, zoals categorie-id, kleurcode en code voor de grootte. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot- of afbeeldingskaart in de bannerfunctie carrousel.

Bekijk de volgende voorbeelden van URL&#39;s in QuickView en de resulterende hotspot- of afbeeldingskaartvariabelen:

<table>
 <tbody>
  <tr>
   <td>Enige SKU, die in het vraagkoord wordt gevonden.</td>
   <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Het enige variabele deel in de URL is de waarde van de parameter van de <code>productId=</code> querytekenreeks en het is duidelijk een SKU-waarde. Voor hotspots of afbeeldingen met hyperlinks zijn daarom alleen SKU-velden nodig die zijn gevuld met waarden zoals <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td>
  </tr>
  <tr>
   <td>Eén SKU, gevonden in het URL-pad.</td>
   <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/product/6422350843</code></p> </li>
     <li><p><code>https://server/product/1607745002</code></p> </li>
     <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van de hotspots/afbeeldingen met hyperlinks:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td>
  </tr>
  <tr>
   <td>SKU en categorie-id in de queryreeks.</td>
   <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. SKU wordt opgeslagen in de <code>prodId</code> parameter en categorie identiteitskaart wordt opgeslagen in de <code>category=</code> parameter.</p> <p>De definities van hotspot/afbeelding met hyperlinks zijn dus paren. Dit is een SKU-waarde en een extra variabele met de naam <code>categoryId</code> . De resulterende paren zijn als volgt:</p>
    <ul>
     <li><p>SKU is <strong><code>305466</code></strong> en <code>categoryId</code> is <code>1100004</code> .</p> </li>
     <li><p>SKU is <strong><code>310181</code></strong> en <code>categoryId</code> is <strong><code>1100004</code></strong> .</p> </li>
     <li><p>SKU is <strong><code>308706</code></strong> en <code>categoryId</code> is <strong><code>1740148</code></strong> .</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Afbeeldingsbanners uploaden {#uploading-image-banners}

Als u reeds de beelden hebt geupload die u wilt gebruiken, aan de volgende stap vooruitgaan, [ creeer de Reeksen van Carousel ](#creating-carousel-sets). De afbeeldingen die in de carrousel worden gebruikt, moeten worden geüpload nadat Dynamic Media is ingeschakeld.

Om beeldbanners te uploaden, zie [ activa ](/help/assets/manage-assets.md) uploaden.

## Carrouselsets maken {#creating-carousel-sets}

>[!NOTE]
>
>Gebruikers zonder beheerdersrechten moeten worden toegevoegd aan de **[!UICONTROL `dam-users`]** -groep om carrouselbanners te kunnen maken of bewerken. Als u problemen ondervindt bij het maken of bewerken, raadpleegt u de systeembeheerder die u aan de groep **[!UICONTROL `dam-users`]** kan toevoegen.

**om de Reeksen van Carousel tot stand te brengen:**

1. Navigeer in Assets naar de map waarin u de Carousel-set wilt maken en ga naar **[!UICONTROL Create]** > **[!UICONTROL Carousel Set]** .
1. Selecteer op de pagina met de editor van de carrouselbanner de optie **[!UICONTROL Tap to open Asset Selector]** om de afbeelding voor de eerste dia te selecteren.

   Voer een van de volgende handelingen uit op de pagina voor de editor van carrouselbanners:

   * Selecteer **[!UICONTROL Add Slide]** pictogram in de linkerbovenhoek van de pagina.

   * Selecteer **[!UICONTROL Tap to open Asset Selector]** in het midden van de pagina.

   Selecteer deze optie om de elementen te selecteren die u in de Carousel-set wilt opnemen. Geselecteerde assets hebben een vinkje. Wanneer u klaar bent, selecteert u **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken of klikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en selecteer vervolgens het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door te tikken op het pictogram Weergave en **[!UICONTROL Column View]**, **[!UICONTROL Card View]** of **[!UICONTROL List View]** te selecteren.

   Zie [ Werk met Kiezers ](/help/assets/working-with-selectors.md) voor meer informatie.

1. Ga door met het toevoegen van dia&#39;s totdat u alle afbeeldingen hebt toegevoegd die u wilt roteren in de Carousel-set.
1. (Optioneel) Voer een van de volgende handelingen uit:

   * Sleep indien nodig dia&#39;s om de volgorde van de afbeeldingen in de lijst te wijzigen.
   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en vervolgens **[!UICONTROL Delete Slide]** op de werkbalk.

   * Als u een voorinstelling wilt toepassen, selecteert u in de rechterbovenhoek van de pagina de vervolgkeuzelijst met voorinstellingen en selecteert u vervolgens een voorinstelling die u tegelijk op de set wilt toepassen.

   Als u een dia wilt verwijderen, selecteert u de dia en vervolgens op de werkbalk de optie **[!UICONTROL Delete Slide]** . Als u een dia wilt verplaatsen, selecteert u het pictogram voor opnieuw ordenen en houdt u de muisknop ingedrukt en gaat u naar de gewenste locatie.

1. Nadat u de afbeeldingen in dia&#39;s hebt toegevoegd, kunt u een hotspot, afbeelding met hyperlinks of beide toevoegen aan uw afbeelding. Zie [ hotspots of beeldkaarten aan een Banner van het Beeld ](#adding-hotspots-or-image-maps-to-an-image-banner) toevoegen.
1. U kunt het visuele ontwerp en het gedrag van carrouselsets wijzigen. Selecteer de tabbladen **[!UICONTROL Behavior]** en **[!UICONTROL Appearance]** en pas aan hoe de carrouselbanner wordt weergegeven of hoe specifieke componenten zich gedragen. Zie [ de kijker beheren stelt ](/help/assets/viewer-presets.md) voor meer informatie vooraf in over hoe te om de kijkersredacteur te gebruiken.

   >[!NOTE]
   >
   >Voor carrouselbanners kunt u de volgende zaken aanpassen:
   >
   >    * Duur waarin een afbeelding wordt weergegeven. Standaard wordt elke afbeelding 9 seconden weergegeven.
   >    * Animatie. Elke dia-overgang is standaard vervagen. U kunt dat wijzigen in een dia-overgang.
   >    * Stijl van de knoppen. Gebruikers kunnen door de banners roteren door op elke punt of elk getal te tikken. U kunt wijzigen waar de knoppen van de ingestelde indicator worden weergegeven (en of ze numeriek of gestippeld zijn) en hoe groot ze zijn.
   >    * Wijzig de markeerstijl van een afbeeldingskaart of het pictogram dat voor hotspots wordt gebruikt.
   >    * Voordat u een viewervoorinstelling bewerkt, kiest u de stijl waarop de voorinstelling moet zijn gebaseerd. Als u geen stijl kiest en de voorinstelling van de viewer gaat bewerken, gaan alle wijzigingen verloren als u besluit dat u een andere voorinstelling wilt gebruiken.
   >
   >Zie [ Speciale overwegingen voor carrouselbanners ](/help/assets/managing-viewer-presets.md#special-considerations-for-creating-a-carousel-banner-viewer-preset) voor gedetailleerde instructies en meer informatie over de kijkersredacteur.

   U kunt ook een voorvertoning weergeven van de wijze waarop de carrouselbanner wordt weergegeven. Zie [ (Optioneel) Voorvertoning van carrouselbanners weergeven ](#optional-previewing-carousel-banners) .

1. Selecteer **[!UICONTROL Save]** wanneer u klaar bent.

## Hotspots of afbeeldingen met hyperlinks toevoegen aan een afbeeldingsbanner {#adding-hotspots-or-image-maps-to-an-image-banner}

Met de Carousel-set-editor kunt u hotspots of afbeeldingen met hyperlinks toevoegen aan een banner.

Wanneer u hotspots of afbeeldingen met hyperlinks toevoegt, kunt u deze definiëren als een pop-upweergave in QuickView, als een hyperlink of als een Experience-fragment.

Zie [ Fragment van de Ervaring ](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>De gereedschappen voor het delen van sociale media in carrouselbanner worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment.
>
>Om dit probleem te verhelpen, kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Terwijl u hotspots of afbeeldingen met hyperlinks toevoegt aan een afbeelding, vergeet dan niet uw werk op te slaan. Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw carrouselbanner, kunt u Voorvertoning optioneel gebruiken om een voorstelling te zien van hoe uw carrouselbanner aan klanten wordt weergegeven.

Zie [ (Optioneel) Voorvertoning van carrouselbanners weergeven ](#optional-previewing-carousel-banners) .

>[!NOTE]
>
>Wanneer u hotspots aan een beeld in een [ Interactieve Beeld ](/help/assets/interactive-images.md) of een carrouselbanner toevoegt, wordt de hotspot informatie opgeslagen in de zelfde meta-gegevensplaats. Deze locatie is relatief ten opzichte van de locatie van de afbeelding, ongeacht of het een interactieve afbeelding of een carrouselbanner betreft. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.
>
>Houd er echter rekening mee dat carrouselbanners afbeeldingen met hyperlinks ondersteunen op afbeeldingen die ook hotspots kunnen bevatten; een interactieve afbeelding niet. Onthoud deze regel als u een interactieve afbeeldings- of carrouselbanner wilt maken die dezelfde afbeelding gebruikt. Overweeg interactieve afbeeldingen en carrouselbanners te maken met afzonderlijke kopieën van dezelfde afbeelding.

>[!NOTE]
>
>Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

Zie ook [ beeldkaarten ](/help/assets/image-maps.md) toevoegen.

**om hotspots of beeldkaarten aan een Banner van het Beeld toe te voegen:**

1. Navigeer vanuit Assets naar de carrouselset die u interactief wilt maken.
1. Selecteer de carrouselset en selecteer **[!UICONTROL Edit]** . De Carousel Viewer Editor wordt geopend.
1. Selecteer de dia die u interactief wilt maken.
1. Selecteer **[!UICONTROL Hotspot]** of **[!UICONTROL Image Map]** in de linkerbovenhoek van de pagina.
1. Voer een van de volgende handelingen uit:

   * Voor hotspots: selecteer in de afbeelding de locatie waar u de hotspot wilt weergeven.
   * Voor afbeeldingen met hyperlinks: selecteer de afbeelding in de afbeelding en sleep deze vervolgens van linksboven naar rechtsonder om het gebied voor de afbeelding met hyperlinks te maken. U kunt de grootte van de afbeelding met hyperlinks aanpassen door de hoeken te slepen.

   Sleep indien nodig de hotspot of de afbeelding met hyperlinks naar een nieuwe locatie. Voeg desgewenst meer hotspots of afbeeldingen met hyperlinks toe.

   Als u een hotspot of afbeelding met hyperlinks wilt verwijderen, selecteert u de tab **[!UICONTROL Actions]** . Selecteer onder de kop **[!UICONTROL Maps & Hotspots]** in het vervolgkeuzemenu **[!UICONTROL Selected Type]** de naam van de hotspot of de afbeelding met hyperlinks die u wilt verwijderen. Selecteer het pictogram **[!UICONTROL Trash]** naast het menu en selecteer vervolgens **[!UICONTROL Delete]** .

1. Typ in het tekstveld Naam de naam van de hotspot of de afbeelding met hyperlinks. Deze naam wordt ook weergegeven in de vervolgkeuzelijst **[!UICONTROL Maps & Hotspot]** . Als u een naam opgeeft, kunt u de hotspot of de afbeelding met hyperlinks gemakkelijk herkennen als u deze later wilt wijzigen.
1. Voer op het tabblad **[!UICONTROL Actions]** een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Quickview]** .

      * Als u een Experience Manager Sites- en e-commerceklanten bent, selecteert u het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen. Selecteer het product dat u wilt gebruiken en selecteer vervolgens het vinkje in de rechterbovenhoek van de pagina zodat u kunt terugkeren naar de editor voor carrouselbanners.
      * Als u geen klant van Experience Manager Sites of van de Handel bent

         * Zie [ hotspot variabelen identificeren ](#identifying-hotspot-and-image-map-variables) als u deze variabelen wilt bepalen.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU (Stock Keeping Unit) van het product. Dit is een unieke id voor elk afzonderlijk product of elke service die u aanbiedt. De ingegaan waarde van SKU bevolkt automatisch het veranderlijke gedeelte van het malplaatje van de Snelle mening zodat het systeem weet om geëtteerde hotspot met een bepaalde Snelle mening van SKU te associëren.
         * (Optioneel) Als de Snelle weergave andere variabelen bevat die u moet gebruiken om een product verder te identificeren, selecteert u **[!UICONTROL Add Generic Variable]** . Geef in het tekstveld een extra variabele op. category=Mens is bijvoorbeeld een toegevoegde variabele.

         * Zie [ Werk met Kiezers ](/help/assets/working-with-selectors.md) voor meer informatie.

   * Selecteer **[!UICONTROL Hyperlink]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het pictogram Sitekiezer (map) om naar een URL te navigeren.

        >[!NOTE]
        >
        >De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.

      * Als u een zelfstandige klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [ Werkend met Kiezers ](/help/assets/working-with-selectors.md) voor meer informatie.

   * Selecteer **[!UICONTROL Experience Fragment]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het zoekpictogram (vergrootglas) om de pagina Experience Fragment te openen. Selecteer het gewenste fragment van de Ervaring en selecteer vervolgens **[!UICONTROL Select]** in de rechterbovenhoek van de pagina zodat u kunt terugkeren naar de pagina voor hotspotbeheer.
Zie [ Fragmenten van de Ervaring ](/help/sites-authoring/experience-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals dit op de banner wordt weergegeven.

        >[!NOTE]
        >
        >De gereedschappen voor het delen van sociale media in carrouselbanner worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment.
        >
        >U kunt dit probleem omzeilen door viewervoorinstellingen te maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

   ![ experience_fragment-carouselbanner ](assets/experience_fragment-carouselbanner.png)

   U kunt ook een voorvertoning weergeven van de wijze waarop de carrouselbanner wordt weergegeven. Zie [ (Optioneel) Een voorvertoning weergeven van carrouselbanners ](#optional-previewing-carousel-banners) .

1. Selecteer **[!UICONTROL Save]** .
1. Publish de carrouselset. Bij het publiceren wordt de insluitcode of URL gemaakt die u op uw websitepagina kunt gebruiken. Als u een Experience Manager Sites-klant bent, kunt u de carrousel rechtstreeks aan uw webpagina toevoegen.

   Zie [ het Publiceren activa ](/help/assets/publishing-dynamicmedia-assets.md).

   Zie [ Toevoegend een carrousel die aan uw website landende pagina ](#adding-a-carousel-banner-to-your-website-page) wordt geplaatst

## Carrouselsets bewerken {#editing-carousel-sets}

>[!NOTE]
>
>Gebruikers zonder beheerdersrechten moeten worden toegevoegd aan de **[!UICONTROL `dam-users`]** -groep om carrouselbanners te kunnen maken of bewerken. Als u problemen ondervindt bij het maken of bewerken, raadpleegt u de systeembeheerder die u aan de groep **[!UICONTROL dam-users]** kan toevoegen.

U kunt verschillende bewerkingstaken uitvoeren op Carousel Sets, zoals:

* Voeg dia&#39;s toe aan een Carousel-set. Zie ook [ Werk met Kiezers ](/help/assets/working-with-selectors.md).
* Wijzig de volgorde van de dia&#39;s in de carrouselset.
* Elementen in de Carousel-set verwijderen.
* Een viewervoorinstelling toepassen.
* Verwijder de carrouselset.
* Voeg hotspots en afbeeldingen met hyperlinks toe of bewerk deze. Zie ook [ Werk met Kiezers ](/help/assets/working-with-selectors.md).

**om de Reeksen van Carousel uit te geven:**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een Carousel-set-element en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram).
   * Houd de cursor boven een Carousel-set-element, selecteer **[!UICONTROL Select]** (vinkpictogram) en selecteer vervolgens **[!UICONTROL Edit]** op de werkbalk.

   * Selecteer een Carousel-set-element en selecteer vervolgens in de linkerbovenhoek van de pagina **[!UICONTROL Edit]** (potloodpictogram).

1. Voer een van de volgende handelingen uit om de Carousel-set te bewerken:

   * Als u een dia wilt toevoegen, selecteert u het pictogram **[!UICONTROL Add Slide]** en navigeert u naar het element dat u aan die dia wilt toevoegen. Selecteer vervolgens het vinkje.
   * Als u de volgorde van dia&#39;s wilt wijzigen, sleept u een dia naar een nieuwe locatie (selecteer het pictogram voor opnieuw ordenen om items te verplaatsen).
   * Om hotspot of beeldkaart toe te voegen, selecteer hotspot of beeld kaartpictogrammen en zie [ toevoegend hotspots en beeldkaarten ](#adding-hotspots-or-image-maps-to-an-image-banner).
   * Als u de weergave of het gedrag van de carrouselset wilt bewerken, selecteert u de tab **[!UICONTROL Appearance]** of de tab **[!UICONTROL Behavior]** en stelt u de gewenste opties in.
   * Als u hotspots of afbeeldingen met hyperlinks wilt bewerken, selecteert u op de juiste dia een hotspot of afbeelding met hyperlinks en wijzigt u desgewenst onder het tabblad **[!UICONTROL Actions]** .
   * Als u een dia wilt verwijderen, selecteert u deze en selecteert u **[!UICONTROL Delete Slide]** op de werkbalk.
   * Als u een voorinstelling wilt toepassen, selecteert u in de rechterbovenhoek van de pagina de vervolgkeuzelijst **[!UICONTROL Preset]** en selecteert u vervolgens een voorinstelling voor de viewer.
   * Als u een volledige Carousel-set wilt verwijderen, navigeert u naar de Carousel-set, selecteert u deze en selecteert u vervolgens **[!UICONTROL Delete]** .

   >[!NOTE]
   >
   >Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.
   >
   >

## (Optioneel) Voorvertoning van carrouselbanners bekijken {#optional-previewing-carousel-banners}

Met Voorvertoning kunt u zien hoe uw carrouselbanner er uitziet voor klanten en kunt u de hotspots voor carrouselbanners en afbeeldingen met hyperlinks testen om te controleren of deze zich gedragen zoals u had verwacht.

Wanneer u tevreden bent met de carrouselbanner, kunt u deze publiceren.
Zie [ Inbeddend de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/embed-code.md).
Zie [ Koppelend URLs aan uw Webtoepassing ](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [ Toevoegend Dynamic Media Assets aan pagina&#39;s ](/help/assets/adding-dynamic-media-assets-to-pages.md).

U kunt een voorvertoning van carrouselbanners weergeven in de Carousel Editor (voorkeursmethode) of in de lijst **[!UICONTROL Viewers]** .

**aan voorproef carrouselbanners:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande carrouselbanner die u hebt gemaakt en selecteer deze om deze te openen.
1. Selecteer **[!UICONTROL Edit]** .
1. Selecteer in de lijst met voorinstellingen voor viewers in de rechterhoek van de werkbalk een viewer voor een voorvertoning van de carrouselbanner.

   ![ experience_fragment-carouselbanner-viewerdropdown ](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Selecteer **[!UICONTROL Preview]** .
1. Selecteer de hotspots of de afbeeldingen met hyperlinks in de afbeelding, zodat u de bijbehorende handelingen kunt testen.

**aan voorproef carrouselbanners van de lijst van Kijkers:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande carrouselbanner die u hebt gemaakt en selecteer deze om deze te openen.
1. Selecteer het pictogram Inhoud in de linkerbovenhoek van de voorvertoningspagina.
1. Selecteer in de lijst **[!UICONTROL Viewers]** in het deelvenster aan de linkerkant van de pagina de naam van de voorinstelling voor de carrouselbannerviewer die u wilt gebruiken.
1. Selecteer de hotspots of de afbeeldingen met hyperlinks in de afbeelding, zodat u de bijbehorende handelingen kunt testen.

## Publish carrouselbanners {#publishing-carousel-banners}

Publish de carrousel zodat je hem kunt gebruiken. Als u een Carousel-set publiceert, worden de URL en de insluitcode geactiveerd. Het publiceert ook de carrousel naar de Dynamic Media-cloud, die is geïntegreerd met een CDN voor schaalbare en krachtige levering.

>[!NOTE]
>
>Als u een bestaande interactieve afbeelding met hotspots voor uw carrouselbanner gebruikt, moet u de interactieve afbeelding afzonderlijk publiceren nadat u de carrouselbanner hebt gepubliceerd.
>
>Als u een reeds gepubliceerde interactieve afbeelding wijzigt die u in een carrouselbanner gebruikt, moet u de interactieve afbeelding publiceren voordat deze wijzigingen worden weerspiegeld in de carrouselbanner.

Zie [ Publish Dynamic Media Assets ](/help/assets/publishing-dynamicmedia-assets.md) voor informatie over hoe te om carrouselbanners te publiceren.

## Een carrouselbanner toevoegen aan uw websitepagina {#adding-a-carousel-banner-to-your-website-page}

Nadat u bannerafbeeldingen hebt geüpload om een carrousel te maken, hotspots en/of afbeeldingen met hyperlinks naar de banner hebt toegevoegd en de carrouselset hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande websitepagina.

>[!NOTE]
>
>Als u een Experience Manager Sites-klant bent, kunt u de carrouselbanner rechtstreeks aan de pagina toevoegen door de component Interactieve media naar de pagina te slepen. Zie [ de activa van Dynamic Media aan pagina&#39;s ](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.

Als u echter een zelfstandige Experience Manager bent, kunt u de carrouselbanner handmatig toevoegen aan de bestemmingspagina van uw website, zoals beschreven in deze sectie.

1. Kopieer de insluitcode van de gepubliceerde carrouselset.
Zie [ de video of Kijker van het Beeld op een Web-pagina ](/help/assets/embed-code.md) inbedden.

1. Voeg de insluitcode die u van Experience Manager Assets hebt gekopieerd, toe aan uw webpagina.
De gekopieerde insluitcode reageert, zodat deze automatisch in het insluitingsgebied van de pagina past.

## De carrouselbanner integreren met een bestaande QuickView {#integrating-the-carousel-banner-with-an-existing-quickview}

>[!NOTE]
>
>Deze stap is alleen van toepassing als u een zelfstandige Experience Manager Assets-klant bent.

De laatste stap in dit proces is het integreren van de carrouselbanner met een bestaande implementatie van QuickView op uw website. Elke implementatie van QuickView is uniek en een specifieke benadering is nodig die de hulp van een front-end IT persoon impliceert.

De bestaande implementatie van QuickView vertegenwoordigt normaal gesproken een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een Quickview URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een Ajax- verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achterste logica keert de overeenkomstige gegevens of inhoud van de Snelle mening terug naar de front-end code.
1. De front-end code laadt de gegevens of de inhoud van de Snelle mening.
1. Naar keuze, zet de front-end code de geladen gegevens van de Snelle mening in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm weer voor de eindgebruiker.

Deze aanroepen vertegenwoordigen geen onafhankelijke openbare API-aanroepen die door de webpaginalogica kunnen worden aangeroepen vanuit een willekeurige stap. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Tegelijkertijd met het feit dat de carrouselbanner stap 1 en gedeeltelijk stap 2 vervangt, wordt een dergelijke interactie door de viewer afgehandeld wanneer een gebruiker op een hotspot of afbeelding met hyperlinks in de carrouselbanner tikt. De viewer retourneert een gebeurtenis naar de webpagina die alle eerder toegevoegde hotspot- of afbeeldingskaartgegevens bevat.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die door de carrouselbanner wordt uitgegeven.
* Hiermee maakt u een Quickview-URL op basis van de gegevens van de hotspot of afbeelding met hyperlinks.
* Triggert het proces om de Snelle mening van het achtereind te laden en het terug te geven op het scherm voor vertoning.

De insluitcode die door Experience Manager Assets wordt geretourneerd, bevat al een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd.

Het is dus alleen nodig de commentaarmarkering van de code ongedaan te maken en de dummy-handlertekst te vervangen door de code die specifiek is voor de specifieke webpagina.

Het proces voor het samenstellen van de URL van de Snelle weergave is tegengesteld aan het proces voor het identificeren van hotspot- en afbeeldingskaartvariabelen die eerder zijn behandeld.

Zie [ hotspot en de variabelen van de Kaart van het Beeld identificeren ](#identifying-hotspot-and-image-map-variables).

De laatste stap om de Quickview URL teweeg te brengen en het paneel van de Snelle mening te activeren vereist hoogstwaarschijnlijk de hulp van een front-end persoon van IT van uw afdeling van IT. Zij hebben de kennis om het best te weten hoe te om de implementatie van de Snelle mening van de juiste stap nauwkeurig teweeg te brengen, die een klaar-aan-gebruiksKickview URL hebben.

## Aangepaste pop-ups maken met Snelle weergave {#using-quickviews-to-create-custom-pop-ups}

Zie [ douane pop-UPS creëren gebruikend QuickView ](/help/assets/custom-pop-ups.md).
