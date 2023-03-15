---
title: De importmodule voor ontwerpen voor bestemmingspagina's uitbreiden en configureren
seo-title: Extending and Configuring the Design Importer for Landing Pages
description: Leer hoe u de ontwerpimportmodule configureert voor het openen van pagina's.
seo-description: Learn how to configure the Design Importer for landing pages.
uuid: a2dd0c30-03e4-4e52-ba01-6b0b306c90fc
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e02f5484-fbc2-40dc-8d06-ddb53fd9afc2
docset: aem65
exl-id: 1b8c6075-13c6-4277-b726-8dea7991efec
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '3503'
ht-degree: 0%

---

# De importmodule voor ontwerpen voor bestemmingspagina&#39;s uitbreiden en configureren{#extending-and-configuring-the-design-importer-for-landing-pages}

In deze sectie wordt beschreven hoe u de ontwerpimportmodule voor bestemmingspagina&#39;s configureert en zo nodig uitbreidt. Werken met aanlandingspagina&#39;s na import is opgenomen in [Aanlandingspagina&#39;s.](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)

**De ontwerpimporter extraheert uw aangepaste component**

Hier volgen de logische stappen waarmee ontwerpimporters uw aangepaste component herkennen

1. Een TagHandler maken

   * Een markeringsmanager is POJO die HTML markeringen van een specifieke soort behandelt. Het &quot;type&quot;van HTML markeringen uw TagHandler kan behandelen wordt bepaald via het bezit OSGi van TagHandlerFactory &quot;tagpattern.name&quot;. Deze eigenschap OSGi is in wezen een regex die de invoer-HTML-tag moet aanpassen die u wilt verwerken. Alle geneste tags worden naar de taghandler gegenereerd voor verwerking. Als u zich bijvoorbeeld registreert voor een div-element dat een geneste &lt;p> -tag, de &lt;p> -tag wordt ook naar uw TagHandler gegenereerd en het is aan u hoe u deze wilt beheren.
   * De interface van de markeringsmanager is gelijkaardig aan een interface van de inhoudsmanager van SAX. Het ontvangt SAX-gebeurtenissen voor elke HTML-tag. Als leverancier van labelafhandelingen moet u bepaalde levenscyclusmethoden implementeren die automatisch worden aangeroepen door het framework van ontwerporters.

1. Maak de bijbehorende TagHandlerFactory.

   * De taghandlerfabriek is een OSGi-component (singleton) die verantwoordelijk is voor het paaien van instanties van uw taghandler.
   * moet de taghandlerfactory een OSGi-eigenschap met de naam &quot;tagpattern.name&quot; beschikbaar maken waarvan de waarde wordt vergeleken met de invoer-HTML-tag.
   * Als er meerdere taghandlers zijn die overeenkomen met de invoer-HTML-tag, wordt de handler met een hogere positie gekozen. De rangschikking zelf wordt als een OSGi-eigenschap weergegeven **service.ranking**.
   * TagHandlerFactory is een component OSGi. Alle verwijzingen die u aan uw TagHandler wilt verstrekken moeten via deze fabriek zijn.

1. Zorg ervoor dat uw TagHandlerFactory een betere rangschikking heeft als u het gebrek wilt met voeten treden.

>[!CAUTION]
>
>De ontwerpimportmodule die wordt gebruikt voor het importeren van bestemmingspagina&#39;s, [is vervangen door AEM 6.5](/help/release-notes/deprecated-removed-features.md#deprecated-features).

## De HTML voorbereiden voor importeren {#preparing-the-html-for-import}

Nadat u een importerpagina hebt gemaakt, kunt u de volledige HTML-openingspagina importeren. Als u de HTML-openingspagina wilt importeren, moet u de inhoud eerst in een ontwerppakket plaatsen. Het ontwerppakket bevat de bestemmingspagina van de HTML en de bestanden waarnaar wordt verwezen (afbeeldingen, css, pictogrammen, scripts enzovoort).

In het volgende plakblad ziet u hoe u de HTML voorbereidt voor het importeren:

Openingspagina — Cheat Sheet

[Bestand ophalen](assets/cheatsheet.zip)

### Bestandsindeling en vereisten overslaan {#zip-file-layout-and-requirements}

>[!NOTE]
>
>Op dit moment kunnen ZIP-bestanden slechts één HTML-pagina of één deel van een pagina bevatten.

Een voorbeeldlay-out van de ZIP is als volgt:

* /index.html -> HTML-bestand van bestemmingspagina
* /css -> om toe te voegen aan de CSS-clientlib
* /img -> alle afbeeldingen en middelen
* /js -> om toe te voegen aan de JS clientlib

De indeling is gebaseerd op de schermindeling met aanbevolen werkwijzen van HTML5 Boilerplate. Lees meer op [https://html5boilerplate.com/](https://html5boilerplate.com/)

>[!NOTE]
>
>Het ontwerppakket **moet** bevatten een **index.html** bestand op hoofdniveau. Als de te importeren landingspagina ook een mobiele versie heeft, moet de ritssluiting een **mobile.index.html** samen met **index.html** op het hoofdniveau.

### De HTML van de bestemmingspagina voorbereiden {#preparing-the-landing-page-html}

Als u de HTML wilt importeren, moet u een canvasdiv toevoegen aan de HTML van de bestemmingspagina.

De canvasdiv is een HTML **div** with `id="cqcanvas"` die in de HTML moeten worden ingevoegd `<body>` -tags en moet de inhoud die is bedoeld voor conversie bevatten.

Een voorbeeldfragment van de landingspagina HTML na toevoeging van de canvasdiv ziet er als volgt uit:

```xml
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
  <meta name="description" content="">
</head>
<body>
 <div id="cqcanvas">
  <!-- HTML content intended for conversion -->
 </div>
</body>
</html>
```

### De HTML voorbereiden om bewerkbare AEM componenten op te nemen {#preparing-the-html-to-include-editable-aem-components}

Wanneer u een openingspagina importeert, kunt u de pagina ongewijzigd importeren. Dit betekent dat u, nadat de openingspagina is geïmporteerd, geen van de geïmporteerde items in AEM kunt bewerken (u kunt nog steeds extra AEM op de pagina toevoegen).

Voordat u de openingspagina importeert, wilt u wellicht bepaalde delen van de openingspagina converteren, zodat deze bewerkbare AEM onderdelen zijn. Hierdoor kunt u delen van de bestemmingspagina snel bewerken, zelfs nadat het ontwerp van de bestemmingspagina is geïmporteerd.

U doet dit door het toevoegen van `data-cq-component` naar de juiste component in het HTML-bestand dat u importeert.

In de volgende sectie wordt beschreven hoe u het HTML-bestand kunt bewerken, zodat u bepaalde delen van de bestemmingspagina&#39;s omzet in verschillende bewerkbare AEM. Componenten worden uitgebreid beschreven op [Onderdelen van bestemmingspagina&#39;s](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md).

>[!NOTE]
>
>HTML-opmaakcodes waarmee delen van de landingspagina worden omgezet in AEM onderdelen hebben zowel een lange vorm als een korte opmaakcode. Beide worden beschreven voor elke component.

### Beperkingen {#limitations}

Houd rekening met de volgende beperkingen voordat u gaat importeren:

### Kenmerken zoals klasse of id die op de tag &amp;lt;body> zijn toegepast, blijven niet behouden {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

Als bijvoorbeeld een kenmerk zoals id of klasse op de tag body wordt toegepast `<body id="container">` dan wordt het niet bewaard na de invoer. Het geïmporteerde ontwerp mag dus niet afhankelijk zijn van de kenmerken die op de `<body>` tag.

### ZIP slepen en neerzetten {#drag-and-drop-zip}

Uploaden via slepen en neerzetten wordt niet ondersteund voor Internet Explorer en Firefox versie 3.6 en lager. Als u een ontwerp wilt uploaden terwijl u deze browsers gebruikt, klikt u op de zone waar u het bestand neerzet om een dialoogvenster voor het uploaden van bestanden te openen en het ontwerp te uploaden met behulp van dat dialoogvenster.

De browsers die &#39;slepen en neerzetten&#39; van het zip-ontwerp ondersteunen, zijn Chrome, Safari5.x, Firefox 4 en hoger.

### Modernizr wordt niet ondersteund {#modernizr-is-not-supported}

`Modernizr.js` is een op javascript gebaseerd hulpmiddel dat inheemse mogelijkheden van browsers ontdekt en ontdekt of zij voor html5 elementen of niet geschikt zijn. Ontwerpen die Modernisering gebruiken voor het verbeteren van ondersteuning in oudere versies van verschillende browsers kunnen problemen met importeren veroorzaken in de oplossing van de bestemmingspagina. `Modernizr.js` scripts worden niet ondersteund door de Design importer.

### Pagina-eigenschappen blijven niet behouden op het moment dat het ontwerppakket wordt geïmporteerd {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

Elke pagina-eigenschap (bijvoorbeeld aangepast domein, HTTPS afdwingen, enz.) Deze instelling voor een pagina (die de sjabloon Lege landingspagina gebruikt) gebruikt voordat het ontwerppakket is geïmporteerd, gaat verloren nadat het ontwerp is geïmporteerd. Daarom wordt het aanbevolen om de pagina-eigenschappen in te stellen nadat het ontwerppakket is geïmporteerd.

### Markeringen alleen HTML gebruikt {#html-only-markup-assumed}

Tijdens het importeren wordt de markering om veiligheidsredenen ontsmet en om het importeren en publiceren van ongeldige opmaak te voorkomen. Dit veronderstelt HTML-slechts prijsverhoging en alle andere vorm van elementen zoals gealigneerde SVG of de Componenten van het Web zullen uit worden gefiltreerd.

### Tekst {#text}

Markeringen HTML om een tekstcomponent in te voegen ( `foundation/components/text`) in de HTML in het ontwerppakket:

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

Als u de bovenstaande markering opneemt in de HTML, gaat u als volgt te werk:

* Hiermee wordt een bewerkbare AEM tekstcomponent gemaakt ( `sling:resourceType=foundation/components/text`) op de landingspagina die na het importeren van het ontwerppakket is gemaakt.
* Hiermee stelt u de `text` eigenschap van de gemaakte tekstcomponent naar de HTML die binnen de `div`.

**Declaratie van tag voor korte component**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**Tekst met een lijst**

Een tekst met een lijst toevoegen:

* 1st
* 2nd

die in de redacteur RTE kunnen uitgeven:

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**Tekst met kleur**

Een tekst met (roze) kleur toevoegen die in de redacteur RTE kan worden uitgegeven:

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### Titel {#title}

Markeringen HTML om een titelcomponent in te voegen ( `wcm/landingpage/components/title`) in de HTML in het ontwerppakket:

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

Als u de bovenstaande markering opneemt in de HTML, gaat u als volgt te werk:

* Hiermee wordt een bewerkbare AEM titelcomponent gemaakt ( `sling:resourceType=wcm/landingpage/components/title`) op de landingspagina die na het importeren van het ontwerppakket is gemaakt.
* Hiermee stelt u de `jcr:title` eigenschap van de gemaakte component title naar de tekst binnen tag heading die is opgenomen in div.
* Hiermee stelt u de `type` eigenschap aan de tag heading, in dit geval `h1`.

De titelcomponent ondersteunt 7 typen - `h1, h2, h3, h4, h5, h6` en `default`.

**Declaratie van tag voor korte component**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### Afbeelding {#image}

HTML-markering om een afbeeldingscomponent (basis/componenten/afbeelding) in de HTML in te voegen binnen het ontwerppakket:

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

Als u de bovenstaande markering opneemt in de HTML, gaat u als volgt te werk:

* Hiermee maakt u een bewerkbare AEM afbeeldingscomponent ( `sling:resourceType=foundation/components/image`) op de landingspagina die na het importeren van het ontwerppakket is gemaakt.
* Hiermee stelt u de `fileReference` eigenschap van de gemaakte afbeeldingscomponent naar het pad waarnaar de afbeelding in het kenmerk src wordt geïmporteerd.
* Hiermee stelt u de `alt` aan de waarde van het alt-kenmerk in de tag img.
* Hiermee stelt u de `title` aan de waarde van titelkenmerk in de tag img.
* Hiermee stelt u de `width` aan de waarde van het breedtekenmerk in de tag img.
* Hiermee stelt u de `height` aan de waarde van het hoogtekenmerk in de tag img.

**Declaratie van stenorcomponent:**

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### Absolute URL-img src wordt niet ondersteund in Div van afbeeldingscomponent {#absolute-url-img-src-not-supported-within-image-component-div}

Als een `<img>` tag met een absolute URL-src wordt geconverteerd naar een component, een geschikte **UnsupportedTagContentException** wordt verhoogd. Het volgende wordt bijvoorbeeld niet ondersteund:

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

Maar anders worden absolute URL-afbeeldingen ondersteund voor img-tags die geen deel uitmaken van Image Component div.

### Vraag-aan-actie componenten {#call-to-action-components}

U kunt een deel van het landen pagina voor het invoeren als &quot;editable Vraag aan actiecomponent&quot;merken - dergelijke ingevoerde vraag-aan-actie componenten kunnen na het invoeren van de het landen pagina worden uitgegeven. AEM omvat de volgende componenten CTA:

* Klik via koppeling - Hiermee kunt u een tekstkoppeling toevoegen waarmee de bezoeker naar een doel-URL gaat wanneer erop wordt geklikt.
* Grafische koppeling - Hiermee kunt u een afbeelding toevoegen die de bezoeker naar een doel-URL stuurt wanneer erop wordt geklikt.

#### Klikken door koppeling {#click-through-link}

Deze component CTA kan worden gebruikt om een tekstverbinding op de het landen pagina toe te voegen.

Ondersteunde eigenschappen

* Label, met opties voor vet, cursief en onderstrepen
* Doel-URL, ondersteunt derden en AEM URL
* Renderopties voor pagina&#39;s (zelfde venster, nieuw venster, enz.)

HTML-tag om de component op te nemen, klikt u door de component in de geïmporteerde postcode. Hier ziet u hoe u URL&#39;s als doel instelt, &#39;Productdetails weergeven&#39; verwijst naar label enzovoort.

```xml
<div id="cqcanvas">
.
.
                <div data-cq-component="clickThroughLink">
        <a href="/content/we-retail/us/en/products/equipment/snow-sports/flying-snowboard.html">View Product Details  ></a>
  </div>
.
.
</div>
```

Deze component kan in elke standalone toepassing worden gebruikt of uit zip worden ingevoerd.

**Declaratie van tag voor korte component**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### Grafische koppeling {#graphical-link}

Deze component CTA kan worden gebruikt om het even welk grafisch beeld met verbinding op de het landen pagina toe te voegen. De afbeelding kan een eenvoudige knop zijn of een grafische afbeelding als achtergrond. Wanneer op de afbeelding wordt geklikt, wordt de gebruiker naar de doel-URL gegaan die in de componenteigenschappen is opgegeven. Het maakt deel uit van de &quot;Vraag aan Actie&quot;groep.

Ondersteunde eigenschappen

* Uitsnijden, roteren van afbeelding
* Tekst, beschrijving, grootte in px aanwijzen
* Doel-URL, ondersteunt derden en AEM URL
* Renderopties voor pagina&#39;s (zelfde venster, nieuw venster, enz.)

HTML-tag om de grafische koppelingscomponent op te nemen in de geïmporteerde zip. Hier wordt href toegewezen aan doel-URL, img src de renderingafbeelding, &#39;title&#39; wordt gebruikt als aanwijstekst enzovoort.

```xml
<div id="cqcanvas">
  <div data-cq-component="clickThroughGraphicalLink"><a href="https://www.adobe.com/go/wem"><img src="img/call-to-action-button.png" title="Click Here to Learn More" /></a></div>
</div>
```

**Declaratie van tag voor korte component**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughGraphicalLink"><img src="linkimage.png" alt="Click Through Graphical Link shorthand"/></a>
```

>[!NOTE]
>
>Als u een klikdoorgehaalde grafische verbinding wilt tot stand brengen, moet u een ankermarkering en de beeldmarkering in div met verpakken `data-cq-component="clickthroughgraphicallink"` kenmerk.
>
>bijv. `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>Andere manieren om een afbeelding aan een ankertag te koppelen met gebruik van CSS worden niet ondersteund. De volgende markering werkt bijvoorbeeld niet:
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>met een geassocieerd `css .hasbackground { background-image: pathtoimage }`

### Voorloopformulier {#lead-form}

Een formulier voor leads is een formulier dat wordt gebruikt om de profielgegevens van een bezoeker/lead te verzamelen. Deze informatie kan later worden opgeslagen en gebruikt om een efficiënte marketing te doen die op de informatie wordt gebaseerd. Deze informatie omvat gewoonlijk titel, naam, e-mail, geboortedatum, adres, rente, enzovoort. Het maakt deel uit van de CTA Lead-groep.

**Ondersteunde functies**

* Vooraf gedefinieerde loodvelden: voornaam, achternaam, adres, dob, geslacht, about, userId, emailId, submit button zijn beschikbaar in het secundaire bestand. U hoeft alleen het vereiste onderdeel in het formulier voor lead te slepen.
* Met behulp van deze componenten kan de auteur een zelfstandig hoofdformulier ontwerpen. Deze velden komen overeen met voorbeeldformuliervelden. In een zelfstandige of geïmporteerde ZIP-toepassing kan de gebruiker extra velden toevoegen met behulp van CQ:form- of CTA-leadformuliervelden. Geef deze velden een naam en ontwerp ze volgens de vereisten.
* Velden voor lead toewijzen met behulp van specifieke vooraf gedefinieerde namen van CTA-lead-formulieren, bijvoorbeeld - firstName voor voornaam in lead-formulier, enzovoort.
* Velden die niet zijn toegewezen aan een formulier voor leads, worden toegewezen aan cq:formuliercomponenten - tekst, radio, selectievakje, vervolgkeuzelijst, verborgen, wachtwoord.
* De gebruiker kan de titel opgeven met de tag &quot;label&quot; en kan de stijl toepassen met het kenmerk &quot;class&quot; van de stijl (alleen beschikbaar voor CTA-voorbeeldformuliercomponenten).
* De pagina Bedankt en de abonnementenlijst kunnen worden opgegeven als een verborgen parameter van het formulier (aanwezig in index.htm) of kunnen worden toegevoegd/bewerkt in de bewerkbalk van het &quot;Formulier voor begin van lead&quot;.

   &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

   &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* Beperkingen als - vereist kunnen worden opgegeven in de bewerkingsconfiguratie van elk onderdeel.

HTML-tag om de grafische koppelingscomponent op te nemen in de geïmporteerde zip. Hier wordt &#39;firstName&#39; toegewezen aan &#39;lead form firstName&#39; enzovoort, behalve voor selectievakjes. Deze twee selectievakjes worden toegewezen aan de component cq:form dropdown.

```xml
<div id="cqcanvas">
   <div id="form_wrapper">
    <h2>NEWSLETTER SIGN UP</h2>
       <div data-cq-component="leadFormGeneration">
       <form method="post" action="#" onsubmit="return popupBox()">
       <label for="firstName" class="checkText">
        FIRST NAME
       </label><br />
       <input name="firstName" class="text pink" type="text" /><br />
       <label for="lastName" class="checkText">
        LAST NAME
       </label><br />
       <input name="lastName" class="text pink" type="text" /><br />
       <label for="emailId" class="checkText">
        EMAIL ADDRESS
       </label><br />
       <input name="emailId" class="text pink" type="text" /><br />

       <div class="checkboxes">
       <input type="checkbox" class="check" name="send_news" /> <label for="send_news" class="checkText">Send me the latest We.Retail news and announcements.</label><br />
       <input type="checkbox" class="check" name="send_offers" /> <label for="send_offers" class="checkText">Send me We.Retail deals and special offers.</label><br />
       </div>
       <input type="submit" name="submit" class="submit pink" value="Sign Up >" />
       </form>
     </div>
   </div>
```

### Parsys {#parsys}

De AEM parsys component is een containercomponent die andere AEM componenten kan bevatten. Het is mogelijk om een parsys component in ingevoerde HTML toe te voegen. Hierdoor kan de gebruiker bewerkbare AEM aan de bestemmingspagina toevoegen of verwijderen, zelfs nadat deze is geïmporteerd.

Het alineasysteem biedt gebruikers de mogelijkheid om componenten toe te voegen met behulp van het hulpwerktuig.

De prijsverhoging van HTML om een component in te voegen parsys ( `foundation/components/parsys`) in de HTML in het ontwerppakket:

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

Als u de bovenstaande markering opneemt in de HTML, gebeurt het volgende:

* Voegt een AEM parsys component (stichting/componenten/parsys) in de landende pagina in die na het invoeren van het ontwerppakket wordt gecreeerd.
* Initialiseert het hulpdekick met standaardcomponenten. De nieuwe componenten kunnen aan de landende pagina worden toegevoegd door componenten van sidekick op de parsys component te slepen.
* Twee titelcomponenten maken ook deel uit van parsys.

### Doel {#target}

De doelcomponent toont de inhoud van een ervaring op de pagina. U kunt veel ervaring hebben die in een campagne is gemaakt en de doelcomponent kan inhoud van verschillende ervaringen dynamisch weergeven aan verschillende gebruikers die de pagina bezoeken.

De html prijsverhoging om een doelcomponent op te nemen en ook verschillende ervaringen in een campagne te creëren:

```xml
<div data-cq-component="target">
 <section data-cq-component="experience" data-cq-experience="default">
  <p data-cq-component="text">Default content. Select this campaign in client context to view other experiences</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="over-30">
  <p data-cq-component="text">Content for Over 30</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="under-30">
  <p data-cq-component="text">Content for Under 30</p>
 </section>
</div>
```

## Aanvullende importopties {#additional-importing-options}

Naast het specificeren of de ingevoerde componenten editable AEM componenten zijn, kunt u het volgende ook vormen alvorens het ontwerppakket in te voeren:

* Pagina-eigenschappen instellen door de metagegevens uit te nemen die zijn gedefinieerd in de geïmporteerde HTML.
* De charsetcodering in de HTML opgeven.
* Bedekken van de sjabloon voor de pagina Importeur.

### Pagina-eigenschappen instellen door metagegevens uit te nemen die zijn gedefinieerd in geïmporteerde HTML {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

De volgende metagegevens die in het hoofd van de ingevoerde HTML zijn aangegeven, worden door de ontwerpimporteur geëxtraheerd en bewaard als eigenschap &quot;jcr:description&quot;:

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

Het in de HTML-tag ingestelde kenmerk Lang wordt door de ontwerpimporteur geëxtraheerd en behouden als eigenschap &quot;jcr:language&quot;

* &lt;html lang=&quot;en&quot;>

### De codering van de tekenset opgeven in de html {#specifying-the-charset-encoding-in-the-html}

De ontwerpimportmodule leest de codering die in de geïmporteerde HTML is opgegeven. De codering kan als volgt worden gespecificeerd:

`<meta charset="UTF-8">`

*OF*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

Als er geen codering is opgegeven in de geïmporteerde HTML, is UTF-8 de standaardcodering die door de importer van het ontwerp is ingesteld.

### Bezig met overschrijven van sjabloon {#overlaying-template}

De sjabloon Lege landingspagina kan worden overschreven door een nieuwe sjabloon te maken op: `/apps/<appName>/designimporter/templates/<templateName>`

De stappen voor het maken van een nieuwe sjabloon in AEM worden uitgelegd [hier](/help/sites-developing/templates.md).

### Een component vanuit de bestemmingspagina verwijzen {#referring-a-component-from-landing-page}

Stel dat u een component hebt waarnaar u in uw HTML wilt verwijzen met het kenmerk data-cq-component, zodat de importer een component die op deze plaats is opgenomen, rendert. U wilt bijvoorbeeld naar de tabelcomponent verwijzen ( `resourceType = /libs/foundation/components/table`). In de HTML moet het volgende worden toegevoegd:

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

Het pad in de data-cq-component moet het resourceType van de component zijn.

### Best practices voor {#best-practices}

Het gebruik van CSS-kiezers die lijken op de volgende, wordt niet aanbevolen voor gebruik met elementen die zijn gemarkeerd voor componentconversie tijdens het importeren.

| E > F | een onderliggend element van het F-element van een E-element | [Onderliggende combinator](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | een F-element, onmiddellijk voorafgegaan door een E-element | [Aangrenzende combinator](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | een F-element voorafgegaan door een E-element | [Algemene verwant combinator](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | een E-element, basis van het document | [Structurele pseudo-klassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nde-onderliggend(n) | een E-element, het n-de onderliggende element van het bovenliggende element | [Structurele pseudo-klassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | een E-element, het n-de onderliggende element van het bovenliggende element, tellen vanaf het laatste | [Structurele pseudo-klassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nde-van-type(n) | een E-element, het n-de broedsel van het type | [Structurele pseudo-klassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nde-laatste-van-type(n) | een E-element, het n-de-bros van het type, tellend van het laatste | [Structurele pseudo-klassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

Dit is te wijten aan het feit dat extra html-elementen, zoals &lt;div> -tag wordt na het importeren toegevoegd aan de gegenereerde HTML.

* Scripts die op de hierboven beschreven structuur vertrouwen, worden ook niet aanbevolen voor gebruik met elementen die zijn gemarkeerd voor conversie naar AEM componenten.
* Stijlen op de opmaakcodes gebruiken voor componentconversie, zoals &lt;div data-cq-component=&quot;&amp;ast;&quot;> wordt niet aanbevolen.
* De ontwerplay-out moet de beste praktijken van HTML5 Boilerplate volgen. Meer informatie vindt u op: [https://html5boilerplate.com/](https://html5boilerplate.com/).

## OSGI-modules configureren {#configuring-osgi-modules}

De componenten die eigenschappen blootstellen die via console OSGI configureerbaar zijn zijn als volgt:

* Landingspagina, ontwerpimportmodule
* Openingspagina Builder
* Mobile Landing Page Builder
* Vooraf-processor bij het openen van pagina

In de onderstaande tabel worden de eigenschappen kort beschreven:

<table>
 <tbody>
  <tr>
   <td><strong>Component</strong></td>
   <td><strong>Eigenschapnaam</strong></td>
   <td><strong>Beschrijving van eigenschap </strong></td>
  </tr>
  <tr>
   <td>Landingspagina, ontwerpimportmodule</td>
   <td>Filter extraheren</td>
   <td>De lijst met reguliere expressies die moet worden gebruikt voor het filteren van bestanden uit extractie. <br /> Zip-items die overeenkomen met een van de opgegeven patronen worden niet uit de extractie verwijderd</td>
  </tr>
  <tr>
   <td>Openingspagina Builder</td>
   <td>Bestandspatroon</td>
   <td>De bouwer van de Openende Pagina kan worden gevormd om HTML dossiers te behandelen die een regelmatige uitdrukking zoals die door dossierpatroon wordt bepaald aanpassen.</td>
  </tr>
  <tr>
   <td>Mobile Landing Page Builder</td>
   <td>Bestandspatroon</td>
   <td>De bouwer van de Openende Pagina kan worden gevormd om HTML dossiers te behandelen die een regelmatige uitdrukking zoals die door dossierpatroon wordt bepaald aanpassen.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Apparaatgroepen</td>
   <td>De lijst met apparaatgroepen die moeten worden ondersteund.</td>
  </tr>
  <tr>
   <td>Vooraf-processor bij het openen van pagina</td>
   <td>Zoekpatroon </td>
   <td>Het patroon waarnaar moet worden gezocht, in de inhoud van het archiefitem. Deze reguliere expressie komt overeen met de inhoud van het item regel voor regel. Bij overeenkomst wordt de overeenkomende tekst vervangen door het opgegeven vervangingspatroon.<br /> <br /> Zie de onderstaande opmerking over de huidige beperkingen van het vooraf invoeren van de bestemmingspagina.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Patroon vervangen</td>
   <td>Het patroon dat de gevonden overeenkomsten vervangt. U kunt regex groepsverwijzingen zoals $1, $2 gebruiken. Bovendien ondersteunt dit patroon trefwoorden zoals {designPath} die met de werkelijke waarde worden opgelost tijdens het importeren.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>**Huidige beperking van het vooraf instellen van een invoerpagina:**
>Als u wijzigingen in het zoekpatroon wilt aanbrengen en u de eigenschappeneditor voor het voorvoegsel opent, moet u handmatig backslash-tekens toevoegen om de metatekens voor het voorloopgebied te omzeilen. Als u niet handmatig backslash-tekens toevoegt, wordt de regex als ongeldig beschouwd en wordt de oudere niet vervangen.
>
>Als de standaardconfiguratie bijvoorbeeld
>`/\* *CQ_DESIGN_PATH *\*/ *(['"])`
>
>En u moet vervangen >`CQ_DESIGN_PATH` with `VIPURL` in het zoekpatroon ziet uw zoekpatroon er als volgt uit:
`/\* *VIPURL *\*/ *(['"])`

## Problemen oplossen {#troubleshooting}

Bij het importeren van het ontwerppakket kunnen er verschillende fouten optreden, die in deze sectie worden beschreven.

### Initialisatie van hulpwerkick met relevante onderdelen voor de bestemmingspagina {#initialization-of-sidekick-with-landing-page-relevant-components}

Als het ontwerppakket een parsys componentenprijsverhoging bevat, dan na het invoeren, begint het hulpdekick landend-page relevante componenten te tonen. U kunt nieuwe componenten slepen en neerzetten op de component parsys binnen uw landende pagina. U kunt ook naar de ontwerpmodus gaan en nieuwe componenten aan het hulpstuk toevoegen.

### Foutberichten die tijdens het importeren worden weergegeven {#error-messages-displayed-during-import}

In het geval van fouten (het geïmporteerde pakket is bijvoorbeeld geen geldige postcode), wordt het pakket niet geïmporteerd tijdens het importeren van het ontwerp. In plaats daarvan wordt boven op de pagina net boven het vak Slepen en neerzetten een foutbericht weergegeven. Hier worden voorbeelden van foutscenario&#39;s gegeven. Nadat u de fout hebt gecorrigeerd, kunt u de bijgewerkte zip opnieuw importeren op dezelfde lege landingspagina. Er zijn verschillende scenario&#39;s waarin fouten worden gegenereerd:

* Geïmporteerd ontwerppakket is geen geldig zip-archief.
* Het geïmporteerde ontwerppakket bevat geen index.html op het hoofdniveau.

### Waarschuwingen weergegeven na importeren {#warnings-displayed-after-import}

In het geval van waarschuwingen (bijv. HTML verwijst naar afbeeldingen die niet in het pakket aanwezig zijn), importeert de ontwerpimporteur het zip, maar geeft hij tegelijkertijd een lijst weer met problemen/waarschuwingen in het resultatenvenster. Klik op de koppeling voor problemen om een lijst met waarschuwingen weer te geven waarin alle problemen in het ontwerppakket worden vermeld. Er zijn verschillende scenario&#39;s waarin waarschuwingen worden afgevangen en weergegeven door ontwerpimporteurs:

* HTML verwijst naar afbeeldingen die niet in het pakket voorkomen.
* HTML verwijst naar scripts die niet in het pakket voorkomen.
* HTML verwijst naar stijlen die niet in het pakket bestaan.

### Waar worden de bestanden van het ZIP-bestand opgeslagen in AEM? {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

Nadat de bestemmingspagina is geïmporteerd, worden de bestanden (afbeeldingen, css, js, enz.) in het ontwerppakket worden opgeslagen op de volgende locatie in AEM:

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

Stel dat de landingspagina is gemaakt onder de campagne We.Retail en de naam van de landingspagina is **myBlankLandingPage** Vervolgens ziet u de volgende locatie voor ZIP-bestanden:

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### Opmaak niet behouden {#formatting-not-preserved}

Houd rekening met de volgende beperkingen wanneer u uw CSS maakt:

Als een tekst en (bewerkbare) afbeelding er als volgt uitzien:

```xml
<div class="box">
<p><div data-cq-component="image"><img src="assets/image.jpg" width="115"
height="116" /></div>Some Text </p>
</div>
```

met een CSS toegepast op de klasse `box` als volgt:

```xml
.box

{ width: 450px; padding:10px; border: 1px #C5DBE7 solid; margin: 0px auto 0 auto; background-image:url(assets/box.gif); background-repeat:repeat-x,y; font-family:Verdana, Arial, Helvetica, sans-serif; font-size:12px; color:#6D6D6D; }
```

Vervolgens `box img` wordt gebruikt in de ontwerpimportmodule, lijkt de resulterende landingspagina de opmaak niet te hebben behouden. Als u dit wilt omzeilen, moet u er rekening mee houden dat AEM div-tags aan het CSS toevoegt en de code dienovereenkomstig herschrijft. Anders zijn sommige CSS-regels ongeldig.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
Ontwerpers dienen zich er ook van bewust te zijn dat alleen code binnen de **id=cqcanvas** wordt door de importeur erkend, anders blijft het ontwerp niet behouden.
