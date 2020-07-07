---
title: Responsief ontwerp voor webpagina's
seo-title: Responsief ontwerp voor webpagina's
description: Met responsief ontwerp kunnen dezelfde pagina's effectief op meerdere apparaten worden weergegeven in meerdere richtingen
seo-description: Met responsief ontwerp kunnen dezelfde pagina's effectief op meerdere apparaten worden weergegeven in meerdere richtingen
uuid: 3d324557-e7ff-4c82-920f-9b5a906925e8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: 532544b0-1932-419a-b6bd-ecf57a926fef
legacypath: /content/docs/en/aem/6-0/develop/mobile/responsive
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '5327'
ht-degree: 0%

---


# Responsief ontwerp voor webpagina&#39;s{#responsive-design-for-web-pages}

>[!NOTE]
>
>Adobe raadt het gebruiken van de Redacteur van het KUUROORD voor projecten aan die op kader-gebaseerde cliënt-kant van enige paginatoepassing teruggeven (zoals _Reageren_) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.


Ontwerp uw webpagina&#39;s zodanig dat ze zich aanpassen aan de clientviewport waarin ze worden weergegeven. Met responsief ontwerp kunnen dezelfde pagina&#39;s effectief op meerdere apparaten in beide richtingen worden weergegeven. In de volgende afbeelding ziet u enkele manieren waarop een pagina kan reageren op wijzigingen in de viewportgrootte:

* Layout: Gebruik lay-outs met één kolom voor kleinere viewports en lay-outs met meerdere kolommen voor grotere viewports.
* Tekengrootte: Gebruik grotere tekstgrootte (indien van toepassing, zoals koppen) in grotere viewports.
* Inhoud: Neem alleen de belangrijkste inhoud op wanneer u deze weergeeft op kleinere apparaten.
* Navigatie: Er zijn apparaatspecifieke gereedschappen voor toegang tot andere pagina&#39;s.
* Afbeeldingen: Uitvoerende afbeeldingsuitvoeringen die geschikt zijn voor de viewport van de client. afhankelijk van de afmetingen van het venster.

![chlimage_1-4](assets/chlimage_1-4a.png)

Ontwikkel Adobe Experience Manager (AEM) toepassingen die HTML5 pagina&#39;s produceren die zich aan veelvoudige venstergrootte en richtlijn aanpassen. De volgende bereiken van viewport-breedten komen bijvoorbeeld overeen met verschillende apparaattypen en -oriëntaties

* Maximale breedte van 480 pixels (telefoon, staand)
* Maximale breedte van 767 pixels (telefoon, liggend)
* Breedte tussen 768 pixels en 979 pixels (tablet, staand)
* Breedte tussen 980 pixels en 1199 pixels (tablet, liggend)
* Breedte van 1200 px of hoger (bureaublad)

Zie de volgende onderwerpen voor informatie over het uitvoeren van ontvankelijk ontwerpgedrag:

* [Mediaquery&#39;s](/help/sites-developing/responsive.md#using-media-queries)
* [Vloeiende rasters](/help/sites-developing/responsive.md#developing-a-fluid-grid)
* [Adaptieve afbeeldingen](/help/sites-developing/responsive.md#using-adaptive-images)

Tijdens het ontwerpen kunt u uw pagina&#39;s voor verschillende schermgrootten voorvertonen. **[!UICONTROL Sidekick]**

## Voordat u ontwikkelt {#before-you-develop}

Voordat u de AEM-toepassing ontwikkelt die uw webpagina&#39;s ondersteunt, moet u een aantal ontwerpbeslissingen nemen. U moet bijvoorbeeld over de volgende informatie beschikken:

* De apparaten waarop u zich richt.
* De grootte van de doelviewport.
* De paginalay-outs voor elk van de beoogde viewportgrootte.

### Toepassingsstructuur {#application-structure}

De typische AEM-toepassingsstructuur ondersteunt alle responsieve ontwerpimplementaties:

* Paginacomponenten bevinden zich onder /apps/*application_name*/components
* Sjablonen bevinden zich onder /apps/*application_name*/templates
* Ontwerpen bevinden zich onder /etc/designs

## Mediaquery&#39;s gebruiken {#using-media-queries}

Met mediaquery&#39;s kunt u CSS-stijlen selectief gebruiken voor het weergeven van pagina&#39;s. Met de ontwikkelingshulpmiddelen en functies van AEM kunt u mediaquery&#39;s effectief en efficiënt implementeren in uw toepassingen.

De W3C-groep bevat de aanbeveling [Mediaquery](https://www.w3.org/TR/css3-mediaqueries/) &#39;s waarin deze CSS3-functie en de syntaxis worden beschreven.

### Het CSS-bestand maken {#creating-the-css-file}

Definieer in uw CSS-bestand mediaquery&#39;s op basis van de eigenschappen van de apparaten waarvoor u een mediaquery maakt. De volgende implementatiestrategie is effectief voor het beheren van stijlen voor elke mediaquery:

* Gebruik een ClientLibraryFolder om CSS te bepalen die wordt samengesteld wanneer de pagina wordt teruggegeven.
* Definieer elke mediaquery en de bijbehorende stijlen in afzonderlijke CSS-bestanden. Het is handig bestandsnamen te gebruiken die de apparaatfuncties van de mediaquery vertegenwoordigen.
* Definieer stijlen die op alle apparaten in een afzonderlijk CSS-bestand van toepassing zijn.
* In het css.txt- dossier van ClientLibraryFolder, orde de lijst CSS dossiers zoals vereist in het geassembleerde CSS dossier.

In het voorbeeldformulier We.Retail Media wordt deze strategie gebruikt om stijlen in het siteontwerp te definiëren. Het CSS-bestand dat door We.Retail wordt gebruikt, bevindt zich op `*/apps/weretail/clientlibs/clientlib-site/less/grid.less`.

In de volgende tabel worden de bestanden in de onderliggende css-map weergegeven.

<table>
 <tbody>
  <tr>
   <th>Bestandsnaam</th>
   <th>Beschrijving</th>
   <th>Mediaquery</th>
  </tr>
  <tr>
   <td>style.css</td>
   <td>Algemene stijlen.</td>
   <td>N.v.t.</td>
  </tr>
  <tr>
   <td>bootstrap.css</td>
   <td>Algemene stijlen, gedefinieerd door Twitter Bootstrap.</td>
   <td>N.v.t.</td>
  </tr>
  <tr>
   <td>responsive-1200px.css</td>
   <td>Stijlen voor alle media die 1200 pixels breed of breder zijn.</td>
   <td><p>@media (min-breedte): 1200 px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-980px-1199px.css</td>
   <td>Stijlen voor media die tussen 980 pixels en 1199 pixels breed zijn.</td>
   <td><p>@media (min-breedte): 980 px) en (max. breedte: 1199 px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-768px-979px.css</td>
   <td>Stijlen voor media die tussen 768 pixels en 979 pixels breed zijn. </td>
   <td><p>@media (min-breedte): 768 px) en (max. breedte: 979 px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-767px-max.css</td>
   <td>Stijlen voor alle media die minder dan 768 pixels breed zijn.</td>
   <td><p>@media (maximale breedte: 767 px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-480px.css</td>
   <td>Stijlen voor alle media die minder dan 481 pixels breed zijn.</td>
   <td>@media (maximale breedte: 480) {<br /> ...<br /> }</td>
  </tr>
 </tbody>
</table>

Het bestand css.txt in de `/etc/designs/weretail/clientlibs` map bevat de CSS-bestanden die in de map met clientbibliotheken zijn opgenomen. De volgorde van de bestanden implementeert stijlprioriteit. Stijlen zijn specifieker naarmate de apparaatgrootte afneemt.

`#base=css`

```
style.css
 bootstrap.css
```

```
responsive-1200px.css
 responsive-980px-1199px.css
 responsive-768px-979px.css
 responsive-767px-max.css
 responsive-480px.css
```

**Tip**: Met beschrijvende bestandsnamen kunt u de doelgrootte van de viewport gemakkelijk identificeren.

### Mediaquery&#39;s gebruiken met AEM-pagina&#39;s {#using-media-queries-with-aem-pages}

Neem de clientbibliotheekmap op in het JSP-script van uw paginacomponent om het CSS-bestand te genereren dat de mediaquery&#39;s bevat en naar het bestand te verwijzen.

```xml
<ui:includeClientLib categories="apps.weretail.all"/>
```

>[!NOTE]
>
>In de map `apps.weretail.all` met clientbibliotheken wordt de clientlibs-bibliotheek ingesloten.

Het JSP manuscript produceert de volgende code van HTML die verwijzingen de stijlbladen:

```xml
<link rel="stylesheet" href="/etc/designs/weretail/clientlibs-all.css" type="text/css">
<link href="/etc/designs/weretail.css" rel="stylesheet" type="text/css">
```

## Voorvertonen voor specifieke apparaten {#previewing-for-specific-devices}

Bekijk voorvertoningen van uw pagina&#39;s in verschillende viewport grootten om het gedrag van uw responsieve ontwerp te testen. In de **[!UICONTROL Preview]** modus **[!UICONTROL Sidekick]** bevat de menuoptie een **[!UICONTROL Devices]** vervolgkeuzelijst waarmee u een apparaat kunt selecteren. Wanneer u een apparaat selecteert, wordt de pagina aangepast aan het formaat van de viewport.

![chlimage_1-5](assets/chlimage_1-5a.png)

Als u de voorvertoning van het apparaat wilt inschakelen, moet u de pagina en de **[!UICONTROL Sidekick]****[!UICONTROL MobileEmulatorProvider]** service configureren. Een andere paginaconfiguratie controleert de lijst van apparaten die in de **[!UICONTROL Devices]** lijst verschijnt.

### De lijst met apparaten toevoegen {#adding-the-devices-list}

De **[!UICONTROL Devices]** lijst wordt weergegeven in **[!UICONTROL Sidekick]** wanneer uw pagina het JSP-script bevat waarmee de **[!UICONTROL Devices]** lijst wordt weergegeven. Als u de **[!UICONTROL Devices]** lijst wilt toevoegen aan **[!UICONTROL Sidekick]**, neemt u het `/libs/wcm/mobile/components/simulator/simulator.jsp` script op in de `head` sectie van de pagina.

Neem de volgende code op in het JSP dat de `head` sectie definieert:

`<cq:include script="/libs/wcm/mobile/components/simulator/simulator.jsp"/>`

Open het `/apps/weretail/components/page/head.jsp` bestand in CRXDE Lite om een voorbeeld te zien.

### Paginacomponenten registreren voor simulatie {#registering-page-components-for-simulation}

Als u wilt dat de apparaatsimulator ondersteuning biedt voor uw pagina&#39;s, registreert u uw paginacomponenten bij de factory-service MobileEmulatorProvider en definieert u de `mobile.resourceTypes` eigenschap.

Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie het [Vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor volledige details.

Als u bijvoorbeeld een ` [sling:OsgiConfig](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)` knooppunt in uw toepassing wilt maken:

* Bovenliggende map: `/apps/application_name/config`
* Naam: `com.day.cq.wcm.mobile.core.impl.MobileEmulatorProvider-*alias*`

   Het achtervoegsel - `*alias*` wordt vereist omdat de dienst MobileEmulatorProvider een fabrieksdienst is. Gebruik een alias die uniek is voor deze fabriek.

* jcr:primaryType: `sling:OsgiConfig`

Voeg de volgende knooppunteigenschap toe:

* Naam: `mobile.resourceTypes`
* Type: `String[]`
* Waarde: De paden naar de paginacomponenten die uw webpagina&#39;s weergeven. De geometrixx-media-app gebruikt bijvoorbeeld de volgende waarden:

   ```
   geometrixx-media/components/page
    geometrixx-unlimited/components/pages/page
    geometrixx-unlimited/components/pages/coverpage
    geometrixx-unlimited/components/pages/issue
   ```

### De apparaatgroepen opgeven {#specifying-the-device-groups}

Als u de apparaatgroepen wilt opgeven die in de lijst Apparaten worden weergegeven, voegt u een `cq:deviceGroups` eigenschap toe aan het `jcr:content` knooppunt van de hoofdpagina van uw site. De waarde van de eigenschap is een array van paden naar de knooppunten van de apparaatgroep.

De knooppunten van de apparaatgroep bevinden zich in de `/etc/mobile/groups` map.

De hoofdpagina van de Geometrixx-mediasite is bijvoorbeeld `/content/geometrixx-media`. Het `/content/geometrixx-media/jcr:content` knooppunt bevat de volgende eigenschap:

* Naam: `cq:deviceGroups`
* Type: `String[]`
* Waarde: `/etc/mobile/groups/responsive`

Gebruik de console van Hulpmiddelen om apparatengroepen [te](/help/sites-developing/groupfilters.md)creëren en uit te geven.

>[!NOTE]
>
>Voor apparaatgroepen die u gebruikt voor responsief ontwerp, bewerkt u de apparaatgroep en selecteert u Emulator uitschakelen op het tabblad Algemeen. Met deze optie voorkomt u dat de carrousel van de emulator wordt weergegeven. Dit is niet relevant voor responsief ontwerp.


## Aangepaste afbeeldingen gebruiken {#using-adaptive-images}

U kunt mediaquery&#39;s gebruiken om een afbeeldingsbron te selecteren die u op de pagina wilt weergeven. Nochtans, wordt elk middel dat een media vraag gebruikt om zijn gebruik te conditionaliseren gedownload aan de cliënt. De mediaquery bepaalt alleen of de gedownloade bron wordt weergegeven.

Voor grote bronnen, zoals afbeeldingen, is het downloaden van alle bronnen geen efficiënt gebruik van de gegevenspijpleiding van de client. Om middelen selectief te downloaden, gebruik javascript om het middelverzoek in werking te stellen nadat de media vragen de selectie uitvoeren.

De volgende strategie laadt één enkel middel dat gebruikend media vragen wordt gekozen:

1. Voeg een element DIV voor elke versie van het middel toe. Neem de URI van de bron op als de waarde van een kenmerkwaarde. De browser interpreteert het kenmerk niet als een bron.
1. Voeg een mediaquery toe aan elk DIV-element dat geschikt is voor de bron.
1. Wanneer het document wordt geladen of het formaat van het venster wordt gewijzigd, test de code javascript de mediaquery van elk DIV-element.
1. Gebaseerd op de resultaten van de vragen, bepaal welke middel om te omvatten.
1. Voeg een HTML-element in het DOM in dat naar de bron verwijst.

### Mediaquery&#39;s evalueren met JavaScript {#evaluating-media-queries-using-javascript}

Implementaties van de [MediaQueryList-interface](https://dev.w3.org/csswg/cssom-view/#the-mediaquerylist-interface) die door W3C wordt gedefinieerd, stellen u in staat mediaquery&#39;s te evalueren met behulp van javascript. U kunt logica toepassen op de resultaten van mediaquery&#39;s en scripts uitvoeren die zijn bedoeld voor het huidige venster:

* Browsers die de interface MediaQueryList implementeren, ondersteunen de `window.matchMedia()` functie. Deze functie test mediaquery&#39;s op basis van een bepaalde tekenreeks. De functie retourneert een `MediaQueryList` object dat toegang biedt tot de queryresultaten.

* Voor browsers die de interface niet implementeren, kunt u een `matchMedia()` polyfill gebruiken, zoals [matchMedia.js](https://github.com/paulirish/matchMedia.js), een vrij beschikbare javascript-bibliotheek.

#### Media-specifieke bronnen selecteren {#selecting-media-specific-resources}

Het door W3C voorgestelde [afbeeldingselement](https://picture.responsiveimages.org/) gebruikt mediaquery&#39;s om te bepalen welke bron moet worden gebruikt voor afbeeldingselementen. Het afbeeldingselement gebruikt elementkenmerken om mediaquery&#39;s te koppelen aan afbeeldingspaden.

De vrij-beschikbare bibliotheek [picturefill.js verstrekt gelijkaardige functionaliteit zoals het voorgestelde](https://github.com/scottjehl/picturefill) `picture` element, en gebruikt een gelijkaardige strategie. De bibliotheek picturefill.js roept `window.matchMedia` om de media vragen te evalueren die voor een reeks `div` elementen worden bepaald. Elk `div` element geeft ook een afbeeldingsbron op. De bron wordt gebruikt wanneer de mediaquery van het `div` element terugkeert `true`.

De `picturefill.js` bibliotheek vereist HTML-code die vergelijkbaar is met het volgende voorbeeld:

```xml
<div data-picture>
    <div data-src='path to default image'></div>
    <div data-src='path to small image'    data-media="(media query for phone)"></div>
    <div data-src='path to medium image'   data-media="(media query for tablet)"></div>
    <div data-src='path to large image'     data-media="(media query for monitor)"></div>
</div>
```

Wanneer de pagina wordt gerenderd, voegt picturefull.js een `img` element als laatste kind van het `<div data-picture>` element in:

```xml
<div data-picture>
    <div data-src='path to default image'></div>
    <div data-src='path to small image'    data-media="(media query for phone)"></div>
    <div data-src='path to medium image'   data-media="(media query for tablet)"></div>
    <div data-src='path to large image'     data-media="(media query for monitor)"></div>
    <img src="path to medium image">
</div>
```

In een AEM-pagina is de waarde van het `data-src` kenmerk het pad naar een bron in de opslagplaats.

### Adaptieve afbeeldingen implementeren in AEM {#implementing-adaptive-images-in-aem}

Als u adaptieve afbeeldingen wilt implementeren in uw AEM-toepassing, moet u de vereiste JavaScript-bibliotheken toevoegen en de vereiste HTML-markering opnemen in uw pagina&#39;s.

**Bibliotheken**

Haal de volgende JavaScript-bibliotheken op en neem deze op in een clientbibliotheekmap:

* [matchMedia.js](https://github.com/paulirish/matchMedia.js) (voor browsers die de interface MediaQueryList niet implementeren)
* [picturefill.js](https://github.com/scottjehl/picturefill)
* jquery.js (beschikbaar via de `/etc/clientlibs/granite/jquery` clientbibliotheekmap (categorie = jquery)
* [jquery.debouncedresize.js](https://github.com/louisremi/jquery-smartresize) (een jQuery-gebeurtenis die één keer optreedt nadat de grootte van het venster is gewijzigd)

**Tip:** U kunt automatisch meerdere clientbibliotheekmappen samenvoegen door deze in te [sluiten](/help/sites-developing/clientlibs.md#embedding-code-from-other-libraries).

**HTML**

Maak een component die de vereiste div-elementen genereert die de code picturefill.js verwacht. In een AEM-pagina is de waarde van het kenmerk data-src het pad naar een bron in de opslagplaats. Een paginacomponent kan bijvoorbeeld de mediaquery&#39;s en de bijbehorende paden voor afbeeldingsuitvoeringen in DAM hard coderen. U kunt ook een aangepaste component Image maken waarmee auteurs afbeeldingsuitvoeringen kunnen selecteren of renderopties bij uitvoering kunnen opgeven.

In het volgende voorbeeld-HTML worden 2 DAM-uitvoeringen van dezelfde afbeelding geselecteerd.

```xml
<div data-picture>
    <div data-src='/content/dam/geometrixx-media/articles/meridien.png'></div>
    <div data-src='/content/dam/geometrixx-media/articles/meridien.png/jcr:content/renditions/cq5dam.thumbnail.319.319.png'    data-media="(min-width: 769px)"></div>
    <div data-src='/content/dam/geometrixx-media/articles/meridien.png/jcr:content/renditions/cq5dam.thumbnail.140.100.png'   data-media="(min-width: 481px)"></div>
</div>
```

>[!NOTE]
>
>De stichtingscomponent Adaptive Image implementeert adaptieve afbeeldingen:
>
>* Map clientbibliotheek: `/libs/foundation/components/adaptiveimage/clientlibs`
>* Script dat de HTML genereert: `/libs/foundation/components/adaptiveimage/adaptiveimage.jsp`
>
>
In het volgende gedeelte vindt u meer informatie over deze component.


### Renderen van afbeeldingen in AEM {#understanding-image-rendering-in-aem}

Als u de rendering van afbeeldingen wilt aanpassen, dient u te weten wat de standaard statische implementatie van AEM voor het renderen van afbeeldingen is. AEM biedt de component Image en een server voor het renderen van afbeeldingen die samenwerken om afbeeldingen voor webpagina&#39;s te renderen. De volgende reeks gebeurtenissen vindt plaats wanneer de component Image is opgenomen in het alineasysteem van de pagina:

1. Authoring: Auteurs bewerken de component Image om het afbeeldingsbestand op te geven dat in een HTML-pagina moet worden opgenomen. Het bestandspad wordt opgeslagen als een eigenschapwaarde van het knooppunt Image component.
1. Aanvraag pagina: De JSP van de paginacomponent produceert de code van HTML. JSP van de component van het Beeld produceert en voegt een img element aan de pagina toe.
1. Afbeeldingsverzoek: De webbrowser laadt de pagina en vraagt de afbeelding aan volgens het kenmerk src van het img-element.
1. Rendering afbeelding: De afbeelding wordt door het servlet voor het renderen van afbeeldingen geretourneerd naar de webbrowser.

![chlimage_1-6](assets/chlimage_1-6a.png)

De JSP van de component Image genereert bijvoorbeeld het volgende HTML-element:

`<img title="My Image" alt="My Image" class="cq-dd-image" src="/content/mywebsite/en/_jcr_content/par/image_0.img.jpg/1358372073597.jpg">`

Wanneer de browser de pagina laadt, wordt de afbeelding opgevraagd met de waarde van het kenmerk src als URL. Bij Sling wordt de URL ontleed:

* Bron: `/content/mywebsite/en/_jcr_content/par/image_0`
* Bestandsnaamextensie: `.jpg`
* Kiezer: `img`
* Achtervoegsel: `1358372073597.jpg`

Het `image_0` knooppunt heeft een `jcr:resourceType` waarde van `foundation/components/image`, die een `sling:resourceSuperType` waarde van `foundation/components/parbase`heeft. De parbase component bevat het script img.GET.java dat overeenkomt met de kiezer en de bestandsextensie van de aanvraag-URL. CQ gebruikt dit script (servlet) om de afbeelding te renderen.

Als u de broncode van het script wilt zien, gebruikt u CRXDE Lite om het `/libs/foundation/components/parbase/img.GET.java`bestand te openen.

## Afbeeldingen schalen voor de huidige viewport-grootte {#scaling-images-for-the-current-viewport-size}

Afbeeldingen tijdens runtime schalen op basis van de kenmerken van de viewport van de client om afbeeldingen te maken die voldoen aan de principes van responsief ontwerp. Gebruik hetzelfde ontwerppatroon als het renderen van statische afbeeldingen met behulp van een servlet en een ontwerpcomponent.

De component moet de volgende taken uitvoeren:

* Sla het pad en de gewenste afmetingen van de afbeeldingsbron op als eigenschapswaarden.
* Genereer `div` elementen die mediaselectors en serviceoproepen voor het renderen van de afbeelding bevatten.

>[!NOTE]
>
>De webclient gebruikt de Javascript-bibliotheken (of vergelijkbare bibliotheken) matchMedia en Picturefill om de mediaselectors te evalueren.


servlet die het beeldverzoek verwerkt moet de volgende taken uitvoeren:

* Haal het pad en de afmetingen van de afbeelding op uit de eigenschappen van de component.
* Schaal de afbeelding op basis van de eigenschappen en retourneer de afbeelding.

**Beschikbare oplossingen**

AEM installeert de volgende implementaties die u kunt gebruiken of uitbreiden.

* De Aanpassings de stichtingscomponent van het Beeld die media vragen produceert, en HTTP- verzoeken aan de AanpassingsServlet van de Component van het Beeld die de beelden schrapt.
* Het Geometrixx-pakket Commons installeert de voorbeeldservlets van de Server van de Wijziging van de Verwijzing van het Beeld die beeldresolutie veranderen.

### De component Adaptieve afbeelding {#understanding-the-adaptive-image-component}

De adaptieve component van het Beeld produceert vraag aan de Adaptive Servlet van de Component van het Beeld om een beeld terug te geven dat volgens het apparatenscherm wordt gerangschikt. De component bevat de volgende bronnen:

* JSP: Voegt div-elementen toe die mediaquery&#39;s koppelen aan aanroepen van Adaptive Image Component Servlet.
* Clientbibliotheken: De clientlibs-map is een map `cq:ClientLibraryFolder` die de javascript-bibliotheek matchMedia polyfill en een aangepaste Javascript-bibliotheek Picturefill samenstelt.
* Dialoogvenster Bewerken: Het `cq:editConfig` knooppunt negeert de component van de CQ-basisafbeelding, zodat het neerzetdoel een adaptieve-afbeeldingscomponent maakt in plaats van een component van een basisafbeelding.

#### De DIV-elementen toevoegen {#adding-the-div-elements}

Het script adaptive-image.jsp bevat de volgende code waarmee div-elementen en mediaquery&#39;s worden gegenereerd:

```
<div data-picture data-alt='<%= alt %>'>
    <div data-src='<%= path + ".img.320.low." + extension + suffix %>'       data-media="(min-width: 1px)"></div>                                        <%-- Small mobile --%>
    <div data-src='<%= path + ".img.320.medium." + extension + suffix %>'    data-media="(min-width: 320px)"></div>  <%-- Portrait mobile --%>
    <div data-src='<%= path + ".img.480.medium." + extension + suffix %>'    data-media="(min-width: 321px)"></div>  <%-- Landscape mobile --%>
    <div data-src='<%= path + ".img.476.high." + extension + suffix %>'      data-media="(min-width: 481px)"></div>   <%-- Portrait iPad --%>
    <div data-src='<%= path + ".img.620.high." + extension + suffix %>'      data-media="(min-width: 769px)"></div>  <%-- Landscape iPad --%>
    <div data-src='<%= path + ".img.full.high." + extension + suffix %>'     data-media="(min-width: 1025px)"></div> <%-- Desktop --%>

    <%-- Fallback content for non-JS browsers. Same img src as the initial, unqualified source element. --%>
    <noscript>
        <img src='<%= path + ".img.320.low." + extension + suffix %>' alt='<%= alt %>'>
    </noscript>
</div>
```

De `path` variabele bevat het pad van de huidige bron (het componentknooppunt adaptive-image). De code genereert een reeks `div` elementen met de volgende structuur:

`<div data-scr = "*path-to-parent-node*.adaptive-image.adapt.*width*.*quality*.jpg" data-media="*media query*"></div>`

De waarde van het `data-scr` kenmerk is een URL die met Sling wordt omgezet in de Adaptive Image Component Servlet die de afbeelding rendert. Het data-media attribuut bevat de media vraag die tegen de cliënteigenschappen wordt geëvalueerd.

De volgende HTML-code is een voorbeeld van de `div` elementen die de JSP genereert:

```xml
<div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.320.low.jpg'></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.320.medium.jpg'    data-media="(min-width: 320px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.480.medium.jpg'    data-media="(min-width: 321px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.476.high.jpg'     data-media="(min-width: 481px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.620.high.jpg'     data-media="(min-width: 769px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.full.high.jpg'     data-media="(min-width: 1025px)"></div>
```

#### Selectors voor afbeeldingsgrootte wijzigen {#changing-the-image-size-selectors}

Als u de component Adaptive Image aanpast en de breedteselectors wijzigt, moet u ook de Adaptive Image Component Servlet configureren om de breedten te ondersteunen.

### Werken met de Adaptive Image Component Servlet {#understanding-the-adaptive-image-component-servlet}

Met de adaptieve afbeeldingscomponentserver wordt de grootte van een JPEG-afbeelding aangepast aan de opgegeven breedte en wordt de JPEG-kwaliteit ingesteld.

#### De interface van de Adaptive Image Component Servlet {#the-interface-of-the-adaptive-image-component-servlet}

De server voor adaptieve afbeeldingscomponenten is gebonden aan het standaard-Sling-servlet en ondersteunt de bestandsextensies .jpg, .jpeg, .gif en .png. De servletkiezer is img.

>[!CAUTION]
>
>Geanimeerde .gif-bestanden worden niet ondersteund in AEM voor adaptieve uitvoeringen.

Daarom lost het Sling URLs van het HTTP- verzoek van het volgende formaat aan dit servlet op:

`*path-to-node*.img.*extension*`

Zo kunt u bijvoorbeeld HTTP-aanvragen doorsturen met de URL `http://localhost:4502/content/geometrixx/adaptiveImage.img.jpg` naar Adaptive Image Component Servlet.

Twee extra kiezers geven de gewenste afbeeldingsbreedte en JPEG-kwaliteit op. In het volgende voorbeeld wordt een afbeelding met een breedte van 480 pixels en een gemiddelde kwaliteit opgevraagd:

`http://localhost:4502/content/geometrixx/adaptiveImage.adapt.480.MEDIUM.jpg`

**Ondersteunde afbeeldingseigenschappen**

De servlet accepteert een eindig aantal afbeeldingsbreedten en -kwaliteiten. De volgende breedten worden standaard ondersteund (in pixels):

* volledig
* 320
* 480
* 476
* 620

De volledige waarde geeft aan dat er geen schaling is.

De volgende waarden voor JPEG-kwaliteit worden ondersteund:

* LAAG
* MEDIUM
* HOOG

De numerieke waarden zijn respectievelijk 0,4, 0,82 en 1,0.

**De standaard ondersteunde breedten wijzigen**

Gebruik de webconsole ([http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)) of een sling:OsgiConfig-knooppunt om de ondersteunde breedten van de Adobe CQ Adaptive Image Component Servlet te configureren.

Voor informatie over hoe te om de diensten van AEM te vormen, zie het [Vormen OSGi](/help/sites-deploying/configuring-osgi.md).

<table>
 <tbody>
  <tr>
   <th> </th>
   <th>Webconsole</th>
   <th>sling:OsgiConfig</th>
  </tr>
  <tr>
   <th>Service- of knooppuntnaam</th>
   <td>De servicenaam op het tabblad Configuratie is de Adaptive Image Component Servlet van Adobe CQ</td>
   <td>com.day.cq.wcm.foundation.impl. AdaptiveImageComponentServlet</td>
  </tr>
  <tr>
   <th>Eigenschap</th>
   <td><p>Ondersteunde breedten</p>
    <ul>
     <li>Als u een ondersteunde breedte wilt toevoegen, klikt u op een +-knop en voert u een positief geheel getal in.</li>
     <li>Als u een ondersteunde breedte wilt verwijderen, klikt u op de knop Bijbehorend -.</li>
     <li>Als u een ondersteunde breedte wilt wijzigen, bewerkt u de waarde van het veld.</li>
    </ul> </td>
   <td><p>adapt.supported.widths</p>
    <ul>
     <li>De eigenschap is een multivalueerde tekenreekswaarde.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

#### Implementatiedetails {#implementation-details}

De `com.day.cq.wcm.foundation.impl.AdaptiveImageComponentServlet` klasse breidt de [klasse AbstractImageServlet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html) uit. De broncode AdaptiveImageComponentServlet bevindt zich in de `/libs/foundation/src/impl/src/com/day/cq/wcm/foundation/impl` map.

De klasse gebruikt de SCR annotaties van Felix om het middeltype en de dossieruitbreiding te vormen die servlet met, en de naam van de eerste selecteur wordt geassocieerd.

```java
@Component(metatype = true, label = "Adobe CQ Adaptive Image Component Servlet",
        description = "Render adaptive images in a variety of qualities")
@Service
@Properties(value = {
    @Property(name = "sling.servlet.resourceTypes", value = "foundation/components/adaptiveimage", propertyPrivate = true),
    @Property(name = "sling.servlet.selectors", value = "img", propertyPrivate = true),
    @Property(name = "sling.servlet.extensions", value ={
            "jpg",
            "jpeg",
            "png",
            "gif"
    }, propertyPrivate = true)
})
```

servlet gebruikt de SCR annotatie van het Bezit om de standaard gesteunde beeldkwaliteit en afmetingen te plaatsen.

```java
@Property(value = {
            "320", // iPhone portrait
            "480", // iPhone landscape
            "476", // iPad portrait
            "620" // iPad landscape
    },
            label = "Supported Widths",
            description = "List of widths this component is permitted to generate.")
```

De `AbstractImageServlet` klasse biedt de `doGet` methode die de HTTP-aanvraag verwerkt. Deze methode bepaalt het middel dat met het verzoek wordt geassocieerd, wint middeleigenschappen van de bewaarplaats terug, en keert hen in een voorwerp [ImageContext](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.ImageContext.html) terug.

>[!NOTE]
>
>De [klasse com.day.cq.commons.DownloadResource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/DownloadResource.html) verstrekt `getFileReference method`, die de waarde van het `fileReference` bezit van het middel terugwint.

De `AdaptiveImageComponentServlet` klasse negeert de `createLayer` methode. De methode verkrijgt de weg van het beeldmiddel en de gevraagde beeldbreedte van het `ImageContext` voorwerp. Vervolgens worden de methoden van de `info.geometrixx.commons.impl.AdaptiveImageHelper` klasse aangeroepen, die de werkelijke schaling van de afbeelding uitvoert.

De klasse AdaptiveImageComponentServlet overschrijft ook de methode writeLayer. Deze methode past de JPEG-kwaliteit toe op de afbeelding.

### Referentiewijzigingsservlet voor afbeelding (vaak geometrixx) {#image-reference-modification-servlet-geometrixx-common}

Met de voorbeeldserver voor het wijzigen van afbeeldingsreferenties worden groottekenmerken voor het img-element gegenereerd om een afbeelding op de webpagina te schalen.

#### De servlet aanroepen {#calling-the-servlet}

De servlet is gebonden aan `cq:page` bronnen en ondersteunt de bestandsextensie .jpg. De servletkiezer is `image`. Daarom lost het Sling URLs van het HTTP- verzoek van het volgende formaat aan dit servlet op:

`path-to-page-node.image.jpg`

Bijvoorbeeld, door:sturen HTTP- verzoeken met URL `http://localhost:4502/content/geometrixx/en.image.jpg` aan de Servlet van de Wijziging van de Verwijzing van het Beeld.

Drie extra kiezers geven de gewenste afbeeldingsbreedte, -hoogte en (optioneel) -kwaliteit op. In het volgende voorbeeld wordt een afbeelding met een breedte van 770 pixels, een hoogte van 360 pixels en een gemiddelde kwaliteit opgevraagd.

`http://localhost:4502/content/geometrixx/en.image.770.360.MEDIUM.jpg`

**Ondersteunde afbeeldingseigenschappen**

De servlet accepteert een eindig aantal afbeeldingsafmetingen en kwaliteitswaarden.

De volgende waarden worden standaard ondersteund (breedte):

* 256x192
* 370x150
* 480x200
* 127x127
* 770x360
* 620x290
* 480x225
* 320x150
* 375x175
* 303x142
* 1170x400
* 940x340
* 770x300
* 480x190

De volgende waarden voor de afbeeldingskwaliteit worden ondersteund:

* laag
* medium
* hoog

Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie het [Vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor volledige details.

#### De afbeeldingsbron opgeven {#specifying-the-image-resource}

Het afbeeldingspad, de afmetingen en de kwaliteitswaarden moeten worden opgeslagen als eigenschappen van een knooppunt in de opslagplaats:

* De knooppuntnaam is `image`.
* Het bovenliggende knooppunt is het `jcr:content` knooppunt van een `cq:page` bron.

* Het afbeeldingspad wordt opgeslagen als de waarde van een eigenschap met de naam `fileReference`.

Wanneer u een pagina ontwerpt, gebruikt u **Sidetrap** om de afbeelding op te geven en het `image` knooppunt aan de pagina-eigenschappen toe te voegen:

1. Klik in **Sidetrap** op het tabblad **Pagina** en klik vervolgens op **Pagina-eigenschappen**.
1. Klik op het tabblad **Afbeelding** en geef de afbeelding op.
1. Click **OK**.

#### Implementatiedetails {#implementation-details-1}

De klasse info.geometrixx.commons.impl.servlets.ImageReferenceModificationServlet breidt de [klasse AbstractImageServlet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html) uit. Als u het pakket cq-geometrixx-commons-pkg hebt geïnstalleerd, bevindt de broncode ImageReferenceModificationServlet zich in de `/apps/geometrixx-commons/src/core/src/main/java/info/geometrixx/commons/impl/servlets` map.

De klasse gebruikt de SCR annotaties van Felix om het middeltype en de dossieruitbreiding te vormen die servlet met, en de naam van de eerste selecteur wordt geassocieerd.

```java
@Component(metatype = true, label = "Adobe CQ Image Reference Modification Servlet",
        description = "Render the image associated with a page in a variety of dimensions and qualities")
@Service
@Properties(value = {
    @Property(name = "sling.servlet.resourceTypes", value = NameConstants.NT_PAGE, propertyPrivate = true),
    @Property(name = "sling.servlet.selectors", value = "image", propertyPrivate = true),
    @Property(name = "sling.servlet.extensions", value = "jpg", propertyPrivate = true)
})
```

servlet gebruikt de SCR annotatie van het Bezit om de standaard gesteunde beeldkwaliteit en afmetingen te plaatsen.

```java
@Property(label = "Image Quality",
            description = "Quality must be a double between 0.0 and 1.0", value = "0.82")
@Property(value = {
                "256x192", // Category page article list images
                "370x150", // "Most popular" desktop & iPad & carousel min-width: 1px
                "480x200", // "Most popular" phone
                "127x127", // article summary phone square images
                "770x360", // article summary, desktop
                "620x290", // article summary, tablet
                "480x225", // article summary, phone (landscape)
                "320x150", // article summary, phone (portrait) and fallback
                "375x175", // 2-column article summary, desktop
                "303x142", // 2-column article summary, tablet
                "1170x400", // carousel, full
                "940x340",  // carousel min-width: 980px
                "770x300",  // carousel min-width: 768px
                "480x190"   // carousel min-width: 480px
            },
            label = "Supported Resolutions",
            description = "List of resolutions this component is permitted to generate.")
```

De `AbstractImageServlet` klasse biedt de `doGet` methode die de HTTP-aanvraag verwerkt. Deze methode bepaalt het middel dat met de vraag wordt geassocieerd, wint middeleigenschappen van de bewaarplaats terug, en bewaart hen in een voorwerp [ImageContext](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.ImageContext.html) .

De `ImageReferenceModificationServlet` klasse negeert de `createLayer` methode en implementeert de logica die de afbeeldingsbron bepaalt die moet worden gerenderd. De methode haalt een onderliggend knooppunt van het `jcr:content` knooppunt van de pagina met de naam `image`. Er wordt een [afbeeldingsobject](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/foundation/Image.html) gemaakt van dit `image` knooppunt en de `getFileReference` methode retourneert het pad naar het afbeeldingsbestand vanuit de `fileReference` eigenschap van het afbeeldingsknooppunt.

>[!NOTE]
>De [klasse com.day.cq.commons.DownloadResource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/DownloadResource.html) biedt de methode getFileReference.


## Een dynamisch raster ontwikkelen {#developing-a-fluid-grid}

Met AEM kunt u op efficiënte en effectieve wijze dynamische rasters implementeren. Op deze pagina wordt uitgelegd hoe u uw dynamische raster of een bestaande rasterimplementatie (zoals [Bootstrap](https://twitter.github.com/bootstrap/)) kunt integreren in uw AEM-toepassing.

Als u niet bekend bent met dynamische rasters, raadpleegt u de sectie [Inleiding tot dynamische rasters](/help/sites-developing/responsive.md#developing-a-fluid-grid) onder aan deze pagina. Deze inleiding geeft een overzicht van dynamische rasters en richtlijnen voor het ontwerpen ervan.

### Het raster definiëren met een component Pagina {#defining-the-grid-using-a-page-component}

Gebruik paginacomponenten om de elementen van HTML te produceren die de inhoudsblokken van de pagina bepalen. De ClientLibraryFolder waarnaar de pagina verwijst, bevat de CSS die de lay-out van de inhoudsblokken bepaalt:

* Pagina-component: Voegt div-elementen toe die rijen inhoudsblokken vertegenwoordigen. De div elementen die inhoudsblokken vertegenwoordigen omvatten een component parsys waar de auteurs inhoud toevoegen.
* Map clientbibliotheek: Geeft het CSS-bestand op dat mediaquery&#39;s en stijlen voor de div-elementen bevat.

De voorbeeldgeometrixx-media-toepassing bevat bijvoorbeeld de media-home-component. Deze paginacomponent voegt twee manuscripten in, die twee `div` elementen van klasse produceren `row-fluid`:

* De eerste rij bevat een `div` klassenelement `span12` (de inhoud omvat 12 kolommen). Het `div` element bevat de component parsys.

* De tweede rij bevat twee `div` elementen, een van de klassen `span8` en een van de andere `span4`. Elk `div` element omvat de component parsys.

```xml
<div class="page-content">
    <div class="row-fluid">
        <div class="span12">
            <cq:include path="grid-12-par" resourceType="foundation/components/parsys" />
        </div>
    </div>
    <div class="row-fluid">
        <div class="span8">
            <cq:include path="grid-8-par" resourceType="foundation/components/parsys" />
        </div>
        <div class="span4">
            <cq:include path="grid-4-par" resourceType="foundation/components/parsys" />
        </div>
    </div>
</div>
```

>[!NOTE]
>
>Wanneer een component veelvoudige `cq:include` elementen omvat die de parsys component van verwijzingen voorzien, moet elk `path` attribuut een verschillende waarde hebben.


#### Het raster van de component Pagina schalen {#scaling-the-page-component-grid}

Het ontwerp dat aan de geometrixx-media paginacomponent (`/etc/designs/geometrixx-media`) wordt gekoppeld bevat de `clientlibs` ClientLibraryFolder. Deze ClientLibraryFolder bepaalt CSS stijlen voor `row-fluid` klassen, `span*` klassen, en `span*` klassen die kinderen van `row-fluid` klassen zijn. Met mediaquery&#39;s kunnen stijlen opnieuw worden gedefinieerd voor verschillende viewportgrootten.

In het volgende voorbeeld is CSS een subset van deze stijlen. Deze ondergroep concentreert zich op `span12`, `span8`, en `span4` klassen, en media vragen voor twee viewport grootte. Let op de volgende kenmerken van de CSS:

* Met de `.span` stijlen definieert u elementbreedten aan de hand van absolute getallen.
* Met de `.row-fluid .span*` stijlen definieert u elementbreedten als percentages van het bovenliggende element. Percentages worden berekend op basis van de absolute breedten.
* De vragen van media voor grotere viewports wijzen grotere absolute breedten toe.

>[!NOTE]
>
>Met het voorbeeld Geometrixx Media wordt het JavaScript-framework van [Bootstrap](https://twitter.github.com/bootstrap/javascript.html) geïntegreerd in de dynamische rasterimplementatie. Het Bootstrap-framework biedt het bestand bootstrap.css.

```xml
/* default styles (no media queries) */
 .span12 { width: 940px }
 .span8 { width: 620px }
 .span4 { width: 300px }
 .row-fluid .span12 { width: 100% }
 .row-fluid .span8 { width: 65.95744680851064% }
 .row-fluid .span4 { width: 31.914893617021278% }

@media (min-width: 768px) and (max-width: 979px) {
 .span12 { width: 724px; }
 .span8 {     width: 476px; }
 .span4 {     width: 228px; }
 .row-fluid .span12 {     width: 100%;}
 .row-fluid .span8 {     width: 65.74585635359117%; }
 .row-fluid .span4 {     width: 31.491712707182323%; }
}

@media (min-width: 1200px) {
 .span12 { width: 1170px }
 .span8 { width: 770px }
 .span4 { width: 370px }
 .row-fluid .span12 { width: 100% }
 .row-fluid .span8 { width: 65.81196581196582% }
 .row-fluid .span4 { width: 31.623931623931625% }
}
```

#### Inhoud in het raster van de component Pagina verplaatsen {#repositioning-content-in-the-page-component-grid}

Op de pagina&#39;s van de voorbeeldtoepassing Geometrixx Media worden rijen inhoudsblokken horizontaal verdeeld in brede viewports. In kleinere viewports, worden de zelfde blokken verticaal verdeeld. In het volgende voorbeeld-CSS worden de stijlen getoond die dit gedrag implementeren voor de HTML-code die door de pagina-component Media-home wordt gegenereerd:

* De standaard-CSS voor de media-welkomstpagina wijst de `float:left` stijl voor `span*` klassen toe die binnen `row-fluid` klassen zijn.

* Mediaquery&#39;s voor kleinere viewports wijzen de `float:none` stijl voor dezelfde klassen toe.

```xml
/* default styles (no media queries) */
    .row-fluid [class*="span"] {
        width: 100%;
        float: left;
}

@media (max-width: 767px) {
    [class*="span"], .row-fluid [class*="span"] {
        float: none;
        width: 100%;
    }
}
```

#### De paginacomponenten moduleren {#tip-modularize-your-page-components}

Modulariseer uw componenten om efficiënt gebruik van de code te maken. Uw site gebruikt waarschijnlijk verschillende typen pagina&#39;s, zoals een welkomstpagina, een artikelpagina of een productpagina. Elk type pagina bevat verschillende typen inhoud en gebruikt waarschijnlijk verschillende lay-outs. Wanneer bepaalde elementen van elke lay-out echter op meerdere pagina&#39;s voorkomen, kunt u de code die dat deel van de lay-out implementeert, opnieuw gebruiken.

**Bedekkingen van pagina-componenten gebruiken**

Maak een hoofdpaginacomponent die scripts biedt voor het genereren van de verschillende delen van een pagina, zoals `head` en `body` secties, `header`, `content`en `footer` secties binnen de hoofdtekst.

Andere paginacomponenten maken die de hoofdpaginacomponent als `cq:resourceSuperType`de pagina gebruiken. Deze componenten omvatten manuscripten die de manuscripten van de belangrijkste pagina zonodig met voeten treden.

De toepassing goemetrixx-media bevat bijvoorbeeld de paginacomponent (de component `sling:resourceSuperType` is de basis van de pagina). Diverse onderliggende componenten (zoals artikel, categorie en media-home) gebruiken deze paginacomponent als de `sling:resourceSuperType`component. Elke onderliggende component bevat een content.jsp-bestand dat het content.jsp-bestand van de paginacomponent overschrijft.

**Scripts opnieuw gebruiken**

Creeer veelvoudige manuscripten JSP die rij en kolomcombinaties produceren die voor veelvoudige paginacomponenten gemeenschappelijk zijn. Het `content.jsp` script van het artikel en de media-home-componenten verwijzen bijvoorbeeld allebei naar het `8x4col.jsp` script.

**CSS-stijlen ordenen op doelgrootte van viewport**

CSS-stijlen en mediaquery&#39;s voor verschillende viewportgrootten opnemen in afzonderlijke bestanden. Gebruik clientbibliotheekmappen om deze samen te voegen.

### Componenten invoegen in het paginaraster {#inserting-components-into-the-page-grid}

Wanneer componenten één blok van inhoud produceren, over het algemeen controleert het net dat de paginacomponent vestigt de plaatsing van de inhoud.

Auteurs moeten zich ervan bewust zijn dat het inhoudsblok in verschillende formaten en relatieve posities kan worden weergegeven. De inhoudstekst zou geen relatieve richtingen moeten gebruiken om naar andere inhoudsblokken te verwijzen.

Indien nodig moet de component alle CSS- of javascript-bibliotheken leveren die vereist zijn voor de HTML-code die wordt gegenereerd. Gebruik een clientbibliotheekmap in de component om de CSS- en JS-bestanden te genereren. Als u de bestanden toegankelijk wilt maken, [maakt u een afhankelijkheid of sluit u de bibliotheek](/help/sites-developing/clientlibs.md#creating-client-library-folders) in een andere clientbibliotheekmap onder de map /etc in.

**Subrasters**

Als de component meerdere blokken inhoud bevat, voegt u de inhoudsblokken in een rij toe om een subraster op de pagina te maken:

* Gebruik dezelfde klassenamen als de omvattende paginacomponent om div-elementen uit te drukken als rijen en inhoudsblokken.
* Als u het gedrag wilt negeren dat de CSS van het paginaontwerp implementeert, gebruikt u een tweede klassenaam voor het element row div en geeft u de bijbehorende CSS op in een clientbibliotheekmap.

De `/apps/geometrixx-media/components/2-col-article-summary` component genereert bijvoorbeeld twee kolommen met inhoud. De HTML die wordt gegenereerd, heeft de volgende structuur:

```xml
<div class="row-fluid mutli-col-article-summary">
    <div class="span6">
        <article>
            <div class="article-summary-image">...</div>
            <div class="social-header">...</div>
            <div class="article-summary-description">...</div>
            <div class="social">...</div>
        </article>
    </div>
</div>
```

De `.row-fluid .span6` kiezers van de CSS van de pagina zijn van toepassing op de `div` elementen van dezelfde klasse en structuur in deze HTML. De component bevat echter ook de clientbibliotheekmap /apps/geometrixx-media/components/2-col-article-summary/clientlibs:

* In het CSS-bestand worden dezelfde mediaquery&#39;s gebruikt als de paginacomponent om wijzigingen in de lay-out op dezelfde afzonderlijke paginabreedten vast te stellen.
* Kiezers gebruiken de `multi-col-article-summary` klasse van het rijelement `div` om het gedrag van de `row-fluid` klasse van de pagina met voeten te treden.

De volgende stijlen zijn bijvoorbeeld opgenomen in het `/apps/geometrixx-media/components/2-col-article-summary/clientlibs/css/responsive-480px.css` bestand:

```xml
@media (max-width: 480px) {
    .mutli-col-article-summary .article-summary-image {
        float: left;
        width: 127px;
    }
    .mutli-col-article-summary .article-summary-description {
        width: auto;
        margin-left: 127px;
    }
    .mutli-col-article-summary .article-summary-description h4 {
        padding-left: 10px;
    }
    .mutli-col-article-summary .article-summary-text {
        margin-left: 127px;
        min-height: 122px;
        top: 0;
    }
}
```

## Inleiding tot vloeistofrasters {#introduction-to-fluid-grids}

Met dynamische rasters kunt u paginalay-outs aanpassen aan de afmetingen van de viewport van de client. Rasters bestaan uit logische kolommen en rijen die de blokken inhoud op de pagina plaatsen.

* Kolommen bepalen de horizontale posities en breedten van inhoudsblokken.
* Rijen bepalen de relatieve verticale posities van inhoudsblokken.

Met behulp van HTML5-technologie kunt u het raster implementeren en bewerken om de paginalay-outs aan te passen aan verschillende viewportgrootten:

* HTML- `div` elementen bevatten blokken inhoud die een bepaald aantal kolommen omspannen.
* Een of meer van deze div-elementen bestaan uit een rij wanneer ze een gemeenschappelijke bovenliggende divelement delen.

### discrete breedten gebruiken {#using-discrete-widths}

Gebruik voor elk bereik van viewportbreedten waarop u zich richt een statische paginabreedte en inhoudsblokken met constante breedte. Als u de grootte van een browservenster handmatig wijzigt, worden wijzigingen in de inhoudsgrootte aangebracht op verschillende vensterbreedten (ook wel onderbrekingspunten genoemd). Hierdoor worden paginaontwerpen nauwkeuriger toegepast, zodat de gebruiker er optimaal mee kan werken.

#### Het raster schalen {#scaling-the-grid}

Gebruik rasters om inhoudsblokken te schalen en deze aan te passen aan verschillende viewportgrootten. Inhoudsblokken beslaan een specifiek aantal kolommen. Naarmate de kolombreedten groter of kleiner worden om in verschillende viewportgrootten te passen, neemt de breedte van de inhoudsblokken dienovereenkomstig toe of af. Schalen kan zowel grote als middelgrote viewports steunen die genoeg breed zijn om de zij-aan-zijplaatsing van inhoudsblokken aan te passen.

![](do-not-localize/chlimage_1-1a.png)

#### Inhoud in het raster verplaatsen {#repositioning-content-in-the-grid}

De grootte van inhoudsblokken kan worden beperkt door een minimumbreedte, waarvoorbij schalen niet meer effectief is. Voor kleinere viewports, kan het net worden gebruikt om blokken van inhoud verticaal te verdelen eerder dan horizontaal.

![](do-not-localize/chlimage_1-2a.png)

### Het raster ontwerpen {#designing-the-grid}

Bepaal de kolommen en rijen die u nodig hebt om de blokken inhoud op uw pagina&#39;s te plaatsen. De paginalay-outs bepalen het aantal kolommen en rijen dat het raster omspannen.

**Aantal kolommen**

Neem voldoende kolommen op om de inhoudsblokken horizontaal voor alle viewportgrootten in al uw lay-outs te plaatsen. U zou meer kolommen dan momenteel nodig moeten gebruiken om toekomstige paginaontwerpen aan te passen.

**Rijinhoud**

Gebruik rijen om de verticale plaatsing van inhoudsblokken te bepalen. Bepaal de inhoudsblokken die dezelfde rij delen:

* Inhoudsblokken die zich horizontaal naast elkaar in een van de lay-outs bevinden, bevinden zich in dezelfde rij.
* De blokken van de inhoud die naast elkaar horizontaal (bredere viewports) en verticaal (kleinere viewports) worden gevestigd zijn in de zelfde rij.

### Rasterimplementaties {#grid-implementations}

Maak CSS-klassen en -stijlen om de lay-out van de inhoudsblokken op een pagina te bepalen. Paginaontwerpen zijn vaak gebaseerd op de relatieve grootte en positie van inhoudsblokken in de viewport. De viewport bepaalt de daadwerkelijke grootte van de inhoudsblokken. In uw CSS moet rekening worden gehouden met de relatieve en absolute grootten. U kunt een dynamisch raster implementeren met drie typen CSS-klassen:

* Een klasse voor een `div` element dat een container voor alle rijen is. Deze klasse stelt de absolute breedte van het raster in.
* Een klasse voor `div` elementen die een rij vertegenwoordigen. Deze klasse bepaalt de horizontale of verticale plaatsing van de inhoudsblokken die de klasse bevat.
* Klassen voor `div` elementen die blokken inhoud van verschillende breedten vertegenwoordigen. Breedten worden uitgedrukt als een percentage van het bovenliggende element (de rij).

De gerichte viewport breedten (en hun bijbehorende media vragen) wijzen discrete breedten af die voor een paginalay-out worden gebruikt.

#### Breedten van inhoudsblokken {#widths-of-content-blocks}

Over het algemeen is de `width` stijl van inhoudblokklassen gebaseerd op de volgende kenmerken van uw pagina en raster:

* De absolute paginabreedte die u voor elke beoogde viewportgrootte gebruikt. Dit zijn bekende waarden.
* De absolute breedte van de rasterkolommen voor elke paginabreedte. U bepaalt deze waarden.
* De relatieve breedte van elke kolom als een percentage van de totale paginabreedte. U berekent deze waarden.

CSS omvat een reeks media vragen die de volgende structuur gebruiken:

```xml
@media(query_for_targeted_viewport){

  .class_for_container{ width:absolute_page_width }
  .class_for_row { width:100%}

  /* several selectors for content blocks   */
  .class_for_content_block1 { width:absolute_block_width1 }
  .class_for_content_block2 { width:absolute_block_width2 }
  ...

  /* several selectors for content blocks inside rows */
  .class_for_row .class_for_content_block1 { width:relative_block_width1 }
  .class_for_row .class_for_content_block2 { width:relative_block_width2 }
  ...
}
```

Gebruik het volgende algoritme als uitgangspunt voor het ontwikkelen van de elementklassen en CSS stijlen voor uw pagina&#39;s.

1. Definieer een klassenaam voor het div-element dat alle rijen bevat, bijvoorbeeld `content.`
1. Definieer een CSS-klasse voor div-elementen die rijen vertegenwoordigen, zoals `row-fluid`.
1. Definieer klassenamen voor elementen van inhoudsblokken. Een klasse is vereist voor alle mogelijke breedten, in termen van kolombereiken. Gebruik bijvoorbeeld de `span3` klasse voor `div` elementen die zich uitstrekken over drie kolommen, gebruik `span4` klassen voor reeksen van vier kolommen. Definieer zoveel klassen als er kolommen in het raster staan.

1. Voor elke viewport grootte die u richt, voeg de overeenkomstige media vraag aan uw CSS dossier toe. Voeg de volgende items toe aan elke mediaquery:

   * Een kiezer voor de `content` klasse, bijvoorbeeld `.content{}`.
   * Selectors voor elke span-klasse, bijvoorbeeld `.span3{ }`.
   * Een kiezer voor de `row-fluid` klasse, bijvoorbeeld `.row-fluid{ }`
   * Kiezers voor bereikklassen die zich binnen de rij-vloeistofklassen bevinden, bijvoorbeeld `.row-fluid span3 { }`.

1. Breedtestijlen toevoegen voor elke kiezer:

   1. Stel de breedte van `content` kiezers bijvoorbeeld in op de absolute grootte van de pagina `width:480px`.
   1. Stel de breedte van alle kiezers in de rijvloeistof in op 100%.
   1. Stel de breedte van alle bereikkiezers in op de absolute breedte van het inhoudsblok. Een triviaal raster gebruikt gelijkmatig verdeelde kolommen van dezelfde breedte: `(absolute width of page)/(number of columns)`.
   1. Stel de breedte van de `.row-fluid .span` kiezers in als een percentage van de totale breedte. Bereken deze breedte met de `(absolute span width)/(absolute page width)*100` formule.

#### Inhoudsblokken in rijen plaatsen {#positioning-content-blocks-in-rows}

Gebruik de floatstijl van de `.row-fluid` klasse om te bepalen of de inhoudsblokken in een rij horizontaal of verticaal zijn gerangschikt.

* De `float:left` of de `float:right` stijl veroorzaakt de horizontale distributie van kindelementen (inhoudsblokken).

* De `float:none` stijl veroorzaakt verticale distributie van kindelementen.

Voeg de stijl toe aan de `.row-fluid` kiezer in elke mediaquery. Stel de waarde in op basis van de pagina-indeling die u gebruikt voor de mediaquery. Het volgende diagram illustreert bijvoorbeeld een rij die inhoud horizontaal verdeelt voor brede viewports, en verticaal voor smalle viewports.

![](do-not-localize/chlimage_1-3a.png)

In de volgende CSS kan dit gedrag worden geïmplementeerd:

```xml
@media (min-width: 768px) and (max-width: 979px) {
   .row-fluid {
       width:100%;
       float:left
   }
}

@media (max-width:480px){
    .row-fluid {
       width:100%;
       float:none
   }
}
```

#### Klassen toewijzen aan inhoudsblokken {#assigning-classes-to-content-blocks}

Voor de paginalay-out van elke viewport grootte u richt, bepaal het aantal kolommen dat elk inhoudsblok overspant. Bepaal vervolgens welke klasse moet worden gebruikt voor de div-elementen van die inhoudsblokken.

Wanneer u de div-klassen hebt gemaakt, kunt u het raster implementeren met uw AEM-toepassing.
