---
title: Concepten van de gebruikersinterface voor Adobe Experience Manager Touch
description: Met Adobe Experience Manager 5.6 introduceerde Adobe een nieuwe, aanraakgeoptimaliseerde interface met responsief ontwerp voor de auteursomgeving
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: f13ac6c2-16ab-422d-9005-ab0b49172271
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2147'
ht-degree: 0%

---

# Concepten van de gebruikersinterface voor Adobe Experience Manager Touch{#concepts-of-the-aem-touch-enabled-ui}

Adobe Experience Manager (AEM) kenmerkt een aanraking-toegelaten UI met [&#x200B; ontvankelijk ontwerp &#x200B;](/help/sites-authoring/responsive-layout.md) voor het auteursmilieu dat wordt ontworpen om op zowel aanraak als Desktopapparaten te werken.

>[!NOTE]
>
>De interface met aanraakbediening is de standaardinterface voor AEM. De klassieke interface is vervangen door AEM 6.4.

De interface met aanraakbediening bevat:

* De reeksheader die:
   * Het logo tonen
   * Verstrekt een verbinding aan de Globale Navigatie
   * Verzekert verbinding met andere generische acties; zoals Onderzoek, Hulp, de Oplossingen van het Experience Cloud, Meldingen, en de Montages van de Gebruiker.
* De linkerspoorstaaf (indien nodig getoond en verborgen), die het volgende kan aantonen:
   * Tijdlijn
   * Verwijzingen
   * Filters
* De navigatiekop, die ook contextgevoelig is en kan tonen:
   * Geeft aan welke console u momenteel gebruikt, of uw locatie, of beide, binnen die console
   * Selectie voor de linkerspoorstaaf
   * Broodkruimels
   * Toegang tot aangewezen **creeer** acties
   * Selecties weergeven
* Het inhoudsgebied dat:
   * Hiermee geeft u de inhoudsitems weer (pagina&#39;s, middelen, forumposts, enzovoort)
   * Kan worden opgemaakt zoals gevraagd, bijvoorbeeld kolom, kaart of lijst
   * Gebruikt een responsief ontwerp (het scherm wordt automatisch aangepast aan uw apparaat en/of venstergrootte)
   * Gebruikt oneindig schuiven (geen paginering meer, alle punten zijn vermeld in één venster)

![&#x200B; chlimage_1-79 &#x200B;](assets/chlimage_1-79.png)

>[!NOTE]
>
>Bijna alle AEM functionaliteit is naar de interface met aanraakbediening verzonden. In sommige beperkte gevallen wordt de functionaliteit echter teruggezet naar de klassieke interface. Zie [&#x200B; de Status van de Eigenschap van de Aanraak UI &#x200B;](/help/release-notes/touch-ui-features-status.md) voor meer informatie.

De interface met aanraakbediening is ontworpen door Adobe voor consistentie in de gebruikerservaring van meerdere producten. Het is gebaseerd op:

* **Koraal UI** (CUI) een implementatie van de visuele stijl van de Adobe voor aanraking-toegelaten UI. Koral UI verstrekt alles uw product/project/Webtoepassing moet de visuele stijl van UI goedkeuren.
* {de componenten van 0} graniet UI **worden gebouwd met Koraal UI.**

De basisbeginselen van de interface met aanraakbediening zijn:

* Eerst mobiel (met het oog op desktop)
* Responsief ontwerp
* Voor de context relevante weergave
* Herbruikbaar
* Inclusief ingesloten naslagdocumentatie
* Ingesloten tests opnemen
* Onderste ontwerp om ervoor te zorgen dat deze beginselen op elk element en elke component worden toegepast

Voor een verder overzicht van de aanraking-Toegelaten structuur UI, zie [&#x200B; Structuur van de AEM aanraking-Toegelaten UI &#x200B;](/help/sites-developing/touch-ui-structure.md).

## AEM {#aem-technology-stack}

AEM gebruikt het Granite-platform als basis en het Granite-platform bevat onder andere de Java™ Content Repository.

![&#x200B; chlimage_1-80 &#x200B;](assets/chlimage_1-80.png)

## Graniet {#granite}

Granite is de Open Web-stapel van de Adobe, die diverse componenten verstrekt die omvatten:

* Een toepassing starten
* Een kader OSGi waarin alles wordt opgesteld
* Verschillende OSGi-directoryservices ter ondersteuning van bouwtoepassingen
* Een uitgebreid Logging Kader dat diverse registreren APIs verstrekt
* Implementatie van de JCR API-specificatie in CRX Repository
* Het Apache Sling Web Framework
* Extra onderdelen van het huidige CRX-product

>[!NOTE]
>
>Granite wordt binnen de Adobe uitgevoerd als een open ontwikkelingsproject: bijdragen aan de code, discussies en problemen worden door het hele bedrijf gemaakt.
>
>Nochtans, graniet is **niet** een open-bronproject. Het is sterk gebaseerd op verschillende open-sourceprojecten (met name Apache Sling, Felix, Jackrabbit en Lucene), maar de Adobe tekent een duidelijke lijn tussen wat openbaar en wat intern is.

## Graniet-interface {#granite-ui}

Het technische platform van Granite verstrekt ook een kader van stichting UI. De belangrijkste doelstellingen hiervan zijn:

* Widgets voor granulaire gebruikersinterface bieden
* Voer de concepten UI uit en illustreer beste praktijken (lange lijsten teruggeven, lijsten het filtreren, voorwerp CRUD, de tovenaars van de CUD...)
* Verstrek een verlengbare en op stop-binnen gebaseerde beleidsinterface

Deze voldoen aan de eisen:

* &#39;&#39;mobile first&#39; respecteren
* Uitbreidbaar
* Eenvoudig te overschrijven

![&#x200B; chlimage_1-81 &#x200B;](assets/chlimage_1-81.png)
GraniteUI.pdf

[&#x200B; krijgt Dossier &#x200B;](assets/graniteui.pdf)
De graniet-interface:

* Gebruikt de RESTful-architectuur van Sling
* Hiermee implementeert u componentbibliotheken die zijn bedoeld voor het bouwen van inhoudgerichte webtoepassingen
* Biedt granulaire UI-widgets
* Biedt een standaard, gestandaardiseerde gebruikersinterface
* Is uitbreidbaar
* Is ontworpen voor zowel mobiele apparaten als desktopapparaten (respecteert eerst mobiel)
* Kan worden gebruikt in elk platform/product/project op basis van graniet, bijvoorbeeld AEM

![&#x200B; chlimage_1-82 &#x200B;](assets/chlimage_1-82.png)

* [&#x200B; de Componenten van de Stichting UI van Granite &#x200B;](#granite-ui-foundation-components)
Deze bibliotheek met basiscomponenten kan door andere bibliotheken worden gebruikt of uitgebreid.
* [Algemene UI-componenten](#granite-ui-administration-components)

### Client-kant versus server-kant {#client-side-vs-server-side}

De cliënt-server mededeling in granite UI bestaat uit hypertext, niet voorwerpen, zodat is er geen behoefte aan de cliënt om de bedrijfslogica te begrijpen

* De server verrijkt de HTML met semantische gegevens
* De client verrijkt de hypertekst met hypermedia (interactie)

![&#x200B; chlimage_1-83 &#x200B;](assets/chlimage_1-83.png)

#### Client-kant {#client-side}

Hierbij wordt een uitbreiding van de woordenlijst HTML gebruikt, op voorwaarde dat de auteur zijn voornemen kenbaar kan maken om een interactieve webapp te maken. Dit is een gelijkaardige benadering van [&#x200B; WAI-ARIA &#x200B;](https://www.w3.org/TR/wai-aria/) en [&#x200B; microformats &#x200B;](https://microformats.org/).

Het bestaat voornamelijk uit een verzameling interactiepatronen (bijvoorbeeld het asynchroon verzenden van een formulier) die worden geïnterpreteerd door JS- en CSS-codes die op de client worden uitgevoerd. De rol van de client-kant bestaat uit het verbeteren van de opmaak (gegeven als de hypermediapliteit van de server) voor interactiviteit.

De client-kant is onafhankelijk van servertechnologie. Zolang de server de aangewezen prijsverhoging geeft, kan de cliënt-kant zijn rol vervullen.

Momenteel worden JS en CSS codes geleverd als Granite [&#x200B; clientlibs &#x200B;](/help/sites-developing/clientlibs.md) onder de categorie:

`granite.ui.foundation and granite.ui.foundation.admin`

Deze worden geleverd als onderdeel van het inhoudspakket:

`granite.ui.content`

#### Server-kant {#server-side}

Dit wordt gevormd door een inzameling van sling componenten die de auteur toelaten om *webapp snel samen te stellen.* De ontwikkelaar ontwikkelt componenten, de auteur assembleert de componenten aan webapp. De rol van de server-kant is de hypermedia betaalbaarheid (prijsverhoging) aan de cliënt te geven.

Momenteel bevinden de componenten zich in de granietopslagplaats op:

`/libs/granite/ui/components/foundation`

Deze wordt geleverd als onderdeel van het inhoudspakket:

`granite.ui.content`

### Verschillen met de klassieke gebruikersinterface {#differences-with-the-classic-ui}

De verschillen tussen de gebruikersinterface van Granite en ExtJS (die voor de klassieke gebruikersinterface worden gebruikt) zijn ook van belang:

<table>
 <tbody>
  <tr>
   <td><strong>ExtJS</strong></td>
   <td><strong>Graniet-interface</strong></td>
  </tr>
  <tr>
   <td>De verre Vraag van de Procedure <br /> </td>
   <td>Overgangen naar status</td>
  </tr>
  <tr>
   <td>Data Transfer-objecten</td>
   <td>Hypermedia</td>
  </tr>
  <tr>
   <td>Client kent interne serverfuncties</td>
   <td>Client kent geen interne gegevens</td>
  </tr>
  <tr>
   <td>"Fat client"</td>
   <td>"Dunne client"</td>
  </tr>
  <tr>
   <td>Gespecialiseerde clientbibliotheken</td>
   <td>Universal Client libraries</td>
  </tr>
 </tbody>
</table>

### Graniet UI Foundation-componenten {#granite-ui-foundation-components}

De [&#x200B; de stichtingscomponenten van UI van Granite &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) verstrekken de basisbouwstenen nodig voor de bouw van om het even welke UI. Deze omvatten onder meer:

* Knop
* Hyperlink
* Gebruiker Avatar

De basiscomponenten zijn te vinden onder:

`/libs/granite/ui/components/foundation`

Deze bibliotheek bevat een graniet UI-component voor elk koraalelement. Een component wordt gestuurd door inhoud, waarbij de configuratie zich in de repository bevindt. Hierdoor is het mogelijk een Granite UI-toepassing samen te stellen zonder handmatig markeringen voor HTML te schrijven.

Doel:

* Componentmodel voor HTML Elements
* Componentcompositie
* Automatische eenheid- en functietests

Implementatie:

* Op opslagplaats gebaseerde samenstelling en configuratie
* Gebruik van testfaciliteiten die door het Granite-platform worden geleverd
* JSP-sjablonen

Deze bibliotheek met basiscomponenten kan door andere bibliotheken worden gebruikt of uitgebreid.

### ExtJS en corresponderende UI-componenten voor graniet {#extjs-and-corresponding-granite-ui-components}

Wanneer het bevorderen van code ExtJS om granite UI te gebruiken, verstrekt de volgende lijst een geschikt overzicht van xtypes ExtJS en knooptypes van ExtJS met hun gelijkwaardige middeltypes van Granite UI.

| **ExtJS xtype** | **graniet UI middeltype** |
|---|---|
| `button` | `granite/ui/components/foundation/form/button` |
| `checkbox` | `granite/ui/components/foundation/form/checkbox` |
| `componentstyles` | `cq/gui/components/authoring/dialog/componentstyles` |
| `cqinclude` | `granite/ui/components/foundation/include` |
| `datetime` | `granite/ui/components/foundation/form/datepicker` |
| `dialogfieldset` | `granite/ui/components/foundation/form/fieldset` |
| `hidden` | `granite/ui/components/foundation/form/hidden` |
| `html5smartfile, html5smartimage` | `granite/ui/components/foundation/form/fileupload` |
| `multifield` | `granite/ui/components/foundation/form/multifield` |
| `numberfield` | `granite/ui/components/foundation/form/numberfield` |
| `pathfield, paragraphreference` | `granite/ui/components/foundation/form/pathbrowser` |
| `selection` | `granite/ui/components/foundation/form/select` |
| `sizefield` | `cq/gui/components/authoring/dialog/sizefield` |
| `tags` | `granite/ui/components/foundation/form/autocomplete` `cq/gui/components/common/datasources/tags` |
| `textarea` | `granite/ui/components/foundation/form/textarea` |
| `textfield` | `granite/ui/components/foundation/form/textfield` |

| **Type van Knoop** | **graniet UI middeltype** |
|---|---|
| `cq:WidgetCollection` | `granite/ui/components/foundation/container` |
| `cq:TabPanel` | `granite/ui/components/foundation/container` `granite/ui/components/foundation/layouts/tabs` |
| `cq:panel` | `granite/ui/components/foundation/container` |

### Algemene UI-componenten {#granite-ui-administration-components}

De [&#x200B; componenten van het beleid van Granite UI &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) bouwen op de stichtingscomponenten voort om generische bouwstenen te verstrekken die om het even welke beleidstoepassing kan uitvoeren. Deze omvatten onder meer:

* Algemene navigatiebalk
* Rail (skelet)
* Deelvenster Zoeken

Doel:

* Verenigde blik-en-voelen voor beleidstoepassingen
* RAD voor beheertoepassingen

Implementatie:

* Vooraf gedefinieerde componenten die de basiscomponenten gebruiken
* Componenten kunnen worden aangepast

## Koraalinterface {#coral-ui}

CoralUI.pdf

[&#x200B; krijgt Dossier &#x200B;](assets/coralui.pdf)
CUI (Coral UI) is een implementatie van de visuele stijl van de Adobe voor de interface met aanraakbediening die is ontworpen om consistentie in de gebruikerservaring op meerdere producten te bieden. Koraal UI verstrekt alles dat u de visuele stijl moet aannemen die op het auteursmilieu wordt gebruikt.

>[!CAUTION]
>
>Koral UI is een bibliotheek UI die aan AEM klanten voor de bouw van toepassingen en Webinterfaces binnen de grenzen van hun vergunning gegeven gebruik van het product ter beschikking wordt gesteld.
>
>Het gebruik van de koraalinterface is alleen toegestaan:
>
>
>* Wanneer het met AEM is verzonden en gebundeld.
>* Voor gebruik wanneer het uitbreiden van bestaande UI van het auteursmilieu.
>* Adobe zakelijke zekerheden, advertenties en presentaties.
>* De gebruikersinterface van toepassingen met het merk Adobe (het lettertype mag niet direct beschikbaar zijn voor andere toepassingen).
>* Met kleine aanpassingen.
>
>Het gebruik van de koraalinterface moet worden vermeden in:
>
>* Documenten en andere niet met Adobe verband houdende posten.
>* Omgevingen voor het maken van inhoud (waar de voorafgaande items door anderen kunnen worden gegenereerd).
>* Toepassingen/componenten/webpagina&#39;s die niet duidelijk zijn verbonden met Adobe.
>

De koraalinterface is een verzameling bouwstenen voor het ontwikkelen van webtoepassingen.

![&#x200B; chlimage_1-84 &#x200B;](assets/chlimage_1-84.png)

Ontworpen om modulair van het begin te zijn, vormt elke module een afzonderlijke laag die op zijn primaire rol wordt gebaseerd. Hoewel de lagen zijn ontworpen om elkaar te steunen, kunnen zij ook onafhankelijk worden gebruikt indien nodig. Hierdoor is het mogelijk om de gebruikerservaring van Coral te implementeren in elke omgeving die geschikt is voor HTML.

Met de koraalinterface is het niet verplicht een bepaald ontwikkelingsmodel en/of -platform te gebruiken. Het primaire doel van Coral is verenigde en schone HTML5 prijsverhoging te verstrekken, onafhankelijk van de daadwerkelijke methode die wordt gebruikt om deze prijsverhoging uit te zenden. Dit kan worden gebruikt voor client- of server-side rendering, sjablonen, JSP-, PHP- of zelfs Adobe Flash RIA-toepassingen - om er maar een paar te noemen.

### HTML-elementen - De opmaaklaag {#html-elements-the-markup-layer}

De HTML-elementen bieden een gemeenschappelijke look en feel voor alle UI-basiselementen (zoals navigatiebalk, knop, menu, spoorstaaf).

Op het eenvoudigste niveau is een HTML-element een HTML-tag met een toegewezen klassenaam. Complexere elementen kunnen bestaan uit meerdere tags, die binnen elkaar zijn genest (op een specifieke manier).

De CSS wordt gebruikt om het daadwerkelijke uiterlijk te geven. Om het mogelijk te maken om het blik-en-gevoel (bijvoorbeeld, voor het geval van branding) gemakkelijk aan te passen, worden de daadwerkelijke stijlwaarden verklaard als variabelen die door [&#x200B; LESS &#x200B;](https://lesscss.org/) pre-bewerker tijdens runtime worden uitgebreid.

Doel:

* Verstrek basiselementen UI met een gemeenschappelijke blik-en-voelt
* Standaardrastersysteem opgeven

Implementatie:

* HTML markeringen met stijlen die door [&#x200B; worden geïnspireerd Bootstrap &#x200B;](https://twitter.github.com/bootstrap/)
* Klassen worden gedefinieerd in LESS-bestanden
* Pictogrammen worden gedefinieerd als fontsprites

De markering:

```xml
<button class="btn btn-large btn-primary" type="button">Large button</button>
<button class="btn btn-large" type="button">Large button</button>
```

Wordt weergegeven als:

![&#x200B; chlimage_1-85 &#x200B;](assets/chlimage_1-85.png)

De look-and-feel wordt gedefinieerd in LESS, gekoppeld aan een element met een speciale klassenaam (het volgende extract is verkort omwille van de beknoptheid):

```xml
.btn {
    font-size: @baseFontSize;
    line-height: @baseLineHeight;
    .buttonBackground(@btnBackground,
                                @btnBackgroundHighlight,
                                @grayDark, 0 1px 1px rgba(255,255,255,.75));
```

Werkelijke waarden worden gedefinieerd in een LESS-variabelebestand (het volgende uittreksel is verkort vanwege de beknoptheid):

```xml
@btnBackgroundHighlight: darken(@white, 10%);
@btnPrimaryBackgroundHighlight: spin(@btnPrimaryBackground, 20%);
@baseFontSize: 17px;
@baseFontFamily: @sansFontFamily;
```

### Elementplug-ins {#element-plugins}

Veel van de HTML-elementen moeten een soort dynamisch gedrag vertonen, zoals het openen en sluiten van pop-upmenu&#39;s. Dit is de rol van de elementinsteekmodules, die dergelijke taken uitvoeren door de DOM te manipuleren met behulp van JavaScript.

Een insteekmodule is:

* Ontworpen voor gebruik op een specifiek DOM-element. Een insteekmodule voor het dialoogvenster verwacht bijvoorbeeld `DIV class=dialog` te vinden
* Algemeen in de natuur. Een lay-outbeheer biedt bijvoorbeeld een lay-out voor elke lijst met `DIV` - of `LI` -elementen

Het gedrag van de insteekmodule kan met parameters worden aangepast, door één van beiden:

* De parameters doorgeven met een JavaScript-aanroep
* Toegewezen `data-*` -kenmerken gebruiken die zijn gekoppeld aan de markering HTML

Hoewel de ontwikkelaar de beste aanpak voor elke plug-in kan kiezen, is de duimregel:

* `data-*` -kenmerken voor opties met betrekking tot de indeling van HTML. Als u bijvoorbeeld het aantal kolommen wilt opgeven
* API-opties/klassen voor functionaliteit met betrekking tot gegevens. Bijvoorbeeld door de lijst met weer te geven items samen te stellen

Hetzelfde concept wordt gebruikt om formuliervalidatie te implementeren. Voor een element dat u wilt valideren, moet u het vereiste invoerformulier opgeven als een aangepast `data-*` -kenmerk. Dit kenmerk wordt vervolgens gebruikt als een optie voor een validatie-insteekmodule.

>[!NOTE]
>
>waar mogelijk moet native HTML5-formuliervalidatie worden gebruikt en/of uitgebreid.

Doel:

* Dynamisch gedrag voor HTML Elements opgeven
* Aangepaste lay-outs bieden die niet mogelijk zijn met zuivere CSS
* Formuliervalidatie uitvoeren
* Geavanceerde DOM-bewerking uitvoeren

Implementatie:

* jQuery-insteekmodule, gekoppeld aan specifieke DOM-elementen
* `data-*` -kenmerken gebruiken om gedrag aan te passen

Een uittreksel van voorbeeldprijsverhoging (neem nota van de opties die als gegeven &#42; attributen worden gespecificeerd):

```xml
<ul data-column-width="220" data-layout="card" class="cards">
  <li class="item">
    <div class="thumbnail">
      <img href="/a.html" src="/a.thumb.319.319..png">
      <div class="caption">
        <h4>Toolbar</h4>
          <p><small>toolbar</small><br></p>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="thumbnail">
      <img href="/a.html" src="/a.thumb.319.319..png">
      <div class="caption">
        <h4>Toolbar</h4>
        <p><small>toolbar</small><br></p>
      </div>
    </div>
  </li>
```

De aanroep van de jQuery-insteekmodule:

```
$('.cards').cardlayout ();
```

Dit wordt weergegeven als:

![&#x200B; chlimage_1-86 &#x200B;](assets/chlimage_1-86.png)

Met de plug-in `cardLayout` worden de omsloten `UL` -elementen ingedeeld op basis van hun respectieve hoogten en waarbij ook rekening wordt gehouden met de breedte van het bovenliggende element.

### HTML Elements-widgets {#html-elements-widgets}

Een widget combineert een of meer basiselementen met een JavaScript-insteekmodule om interface-elementen op een hoger niveau te vormen. Deze kunnen complexer gedrag en ook een complexere blik en het gevoel uitvoeren dan één enkel element zou kunnen leveren. Goede voorbeelden zijn de tagkiezer of de spoorwidgets.

Een widget kan zowel aangepaste gebeurtenissen activeren als naar aangepaste gebeurtenissen luisteren om samen te werken met andere widgets op de pagina. Sommige widgets zijn native jQuery-widgets die de Coral HTML-elementen gebruiken.

Doel:

* UI-elementen op hoger niveau implementeren die complex gedrag vertonen
* Gebeurtenissen activeren en afhandelen

Implementatie:

* jQuery-insteekmodule + HTML-opmaakcode
* Kan client-/server-zijsjablonen gebruiken

Voorbeeldopmaak is:

```
<input type="text" name="tags" placeholder="Tags" class="tagManager"/>
```

De aanroep van de jQuery-insteekmodule (met opties):

```
$(".tagManager").tagsManager({
        prefilled: ["Pisa", "Rome"] })
```

De plug-in geeft HTML-markeringen uit (deze markering gebruikt basiselementen, die mogelijk intern andere plug-ins gebruiken):

```
<span>Pisa</code>
<a title="Removing tag" tagidtoremove="0"
   id="myRemover_0" class="myTagRemover" href="#">x</a></code>

<span id="myTag_1" class="myTag"><span>Rome</code>
<a title="Removing tag" tagidtoremove="1"
   id="myRemover_1" class="myTagRemover" href="#">x</a></code>

<input type="text" data-original-title="" class="input-medium tagManager"
       placeholder="Tags" name="tags" data-provide="typeahead" data-items="6"
       autocomplete="off">
```

Dit wordt weergegeven als:

![&#x200B; chlimage_1-87 &#x200B;](assets/chlimage_1-87.png)

### Hulpprogrammabibliotheek {#utility-library}

Deze bibliotheek is een verzameling JavaScript-hulplijnplug-ins en/of -functies:

* UI-onafhankelijk
* Toch cruciaal voor het ontwikkelen van volledige webtoepassingen

Dit zijn onder andere XSS-afhandeling en de gebeurtenisbus.

Hoewel de HTML-elemenu&#39;s en -widgets kunnen vertrouwen op functionaliteit die wordt geleverd door de nutsbibliotheek, kan de hulpprogrammabibliotheek niet afhankelijk zijn van de elementen of widgets zelf.

Doel:

* Algemene functionaliteit bieden
* Implementatie van gebeurtenisbus
* Clientsjablonen
* XSS

Implementatie:

* jQuery-plug-ins of JavaScript-modules die voldoen aan AMD
