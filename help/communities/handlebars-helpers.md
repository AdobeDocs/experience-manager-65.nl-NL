---
title: SCF Handlebars Helpers
description: De methodes van de Helper van de bars om het werk met SCF te vergemakkelijken
topic-tags: developing
content-type: reference
exl-id: bfb95cae-4b0f-4521-a113-042dc4005a63
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1445'
ht-degree: 1%

---

# SCF Handlebars Helpers {#scf-handlebars-helpers}

| **[Essentiële ⇐ functies](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|   | **[Aanpassing aan client-side bezig](client-customize.md)** |

Handlebars Helpers (helpers) zijn methodes callable van de manuscripten van Handlebars om het werken met componenten te vergemakkelijken SCF.

De implementatie omvat een client-side en een server-side definitie. Ontwikkelaars kunnen ook aangepaste hulplijnen maken.

De aangepaste SCF-hulplijnen die bij AEM Communities worden geleverd, zijn gedefinieerd in het dialoogvenster [clientbibliotheek](../../help/sites-developing/clientlibs.md):

* `/etc/clientlibs/social/commons/scf/helpers.js`

>[!NOTE]
>
>Zorg ervoor dat u de [nieuwste edities pakket met functies](deploy-communities.md#latestfeaturepack).

## Afkorting {#abbreviate}

Een helper om een afgekorte tekenreeks te retourneren die voldoet aan de eigenschappen maxWords en maxLength.

De tekenreeks die moet worden afgekort, wordt opgegeven als de context. Als er geen context is opgegeven, wordt een lege tekenreeks geretourneerd.

Eerst wordt de context bijgesneden tot maxLength en vervolgens wordt de context in woorden gesegmenteerd en tot maxWords teruggebracht.

Als safeString is ingesteld op true, is de geretourneerde tekenreeks een SafeString.

### Parameters {#parameters}

* **context**: String

  (Optioneel) Standaard is de lege tekenreeks

* **maxLength**: Number

  (Optioneel) Standaard is de lengte van de context.

* **maxWords**: Number

  (Optioneel) De standaardwaarde is het aantal woorden in de bijgesneden tekenreeks.

* **safeString**: Boolean

  (Optioneel) Retourneert een handlerBar.SafeString() indien true. De standaardwaarde is false.

### Voorbeelden {#examples}

```
{{abbreviate subject maxWords=2}}

/*
If subject =
    "AEM Communities - Site Creation Wizard"

Then abbreviate would return
    "AEM Communities".
*/
```

```
{{{abbreviate message safeString=true maxLength=30}}}

/*
If message =
    "The goal of AEM Communities is to quickly create a community engagement site."

Then abbreviate would return
    "The goal of AEM Communities is"
*/
```

## Inhoud laden {#content-loadmore}

Een hulpmiddel om twee reeksen onder een div toe te voegen, één voor de volledige tekst en andere voor minder tekst, met de capaciteit om tussen de twee meningen van een knevel te voorzien.

### Parameters {#parameters-1}

* **context**: String

  (Optioneel) Standaard is de lege tekenreeks.

* **numChars**: Number

  (Optioneel) Het aantal tekens dat moet worden weergegeven wanneer geen volledige tekst wordt weergegeven. De standaardwaarde is 100.

* **moreText**: String

  (Optioneel) De tekst die moet worden weergegeven om aan te geven dat er meer tekst moet worden weergegeven. Standaard is &quot;meer&quot;.

* **ellipsesText**: String

  (Optioneel) De tekst die moet worden weergegeven om aan te geven dat er verborgen tekst is. Standaard is &quot;...&quot;.

* **safeString**: Boolean

  (Optioneel) Booleaanse waarde die aangeeft of Handlebars.SafeString() moet worden toegepast voordat het resultaat wordt geretourneerd. De standaardwaarde is false.

### Voorbeeld {#example}

```
{{content-loadmore  context numChars=32  moreText="go on"  ellipsesText="..." }}

/*
If context =
    "Here is the initial less content and this is more content."

Then content-loadmore would return
    "Here is the initial less content<span class="moreelipses">...</span> <span class="scf-morecontent"><span>and this is more content.</span>  <a href="" class="scf-morelink" evt="click=toggleContent">go on</a></span>"
*/
```

## DateUtil {#dateutil}

Een hulpmiddel om een geformatteerde datumreeks terug te keren.

### Parameters {#parameters-2}

* **context**: Number

  (Optioneel) Een millisecondenverschuiving vanaf 1 januari 1970 (tijdperk). De standaardwaarde is de huidige datum.

* **format**: String

  (Optioneel) De datumnotatie die moet worden toegepast. Standaard is &quot;`YYYY-MM-DDTHH:mm:ss.sssZ`&quot; en wordt het resultaat weergegeven als &quot;`2015-03-18T18:17:13-07:00`&quot;

### Voorbeelden {#examples-1}

```
{{dateUtil this.memberSince format="dd MMM yyyy, hh:mm"}}

// returns "18 Mar 2015, 18:17"
```

```
{{dateUtil this.birthday format="MM-DD-YYYY"}}

// returns "03-18-2015"
```

## Gelijk {#equals}

Een hulpmiddel om inhoud terug te keren afhankelijk van een voorwaardelijk gelijk aan.

### Parameters {#parameters-3}

* **lvalue**: String

  De waarde die links moet worden vergeleken.

* **tegenwaarde**: String

  De rechterwaarde die moet worden vergeleken.

### Voorbeeld {#example-1}

```
{{#equals  value "some-value"}}
  <div>They are EQUAL!</div>
`{{else}}`
  <div>They are NOT equal!</div>
{{/equals}}
```

## If-wcm-mode {#if-wcm-mode}

Een blokhelper die de huidige waarde van test [WCM-modus](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) op een door een tekenreeks gescheiden lijst met modi.

### Parameters {#parameters-4}

* **context**: String

  (Optioneel) De tekenreeks die moet worden vertaald. Vereist als er geen standaard is opgegeven.

* **mode**: String

  (Optioneel) Een door komma&#39;s gescheiden lijst met [WCM-modi](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) om te testen of deze is ingesteld.

### Voorbeeld {#example-2}

```xml
{{#if-wcm-mode mode="DESIGN, EDIT"}}
 ...
{else}}
 ...
`{{/if-wcm-mode}}`
```

## i18n {#i-n}

Deze hulp treedt helper &quot;i18n&quot;van Handlebars met voeten.

Zie ook [Tekenreeksen internationaliseren in JavaScript-code](../../help/sites-developing/i18n-dev.md#internationalizing-strings-in-javascript-code).

### Parameters {#parameters-5}

* **context**: String

  (Optioneel) De tekenreeks die moet worden vertaald. Vereist als er geen standaard is opgegeven.

* **default**: String

  (Optioneel) De standaardtekenreeks die moet worden getransleerd. Vereist als er geen context is opgegeven.

* **opmerking**: String

  (Optioneel) Een vertaalhint

### Voorbeeld {#example-3}

```
{{i18n "hello"}}
{{i18n "hello" comment="greeting" default="bonjour"}}
```

## Inclusief {#include}

Een hulpmiddel om een component als niet bestaand middel in een malplaatje te omvatten.

Deze methode laat het middel programmatically worden aangepast gemakkelijker dan voor een middel dat als knoop JCR wordt toegevoegd mogelijk is. Zie [Een onderdeel van een Gemeenschappen toevoegen of opnemen](scf.md#add-or-include-a-communities-component).

Er zijn slechts enkele onderdelen van de Gemeenschappen beschikbaar die u wilt opnemen. <!-- OBSOLETE/OLD  NEED TO UPDATE FOR 6.5  For AEM 6.1, those that are includable are [comments](essentials-comments.md), [rating](rating-basics.md), [reviews](reviews-basics.md), and [voting](essentials-voting.md). -->

Deze helper, die alleen geschikt is aan de serverzijde, biedt functionaliteit die lijkt op [cq:include](../../help/sites-developing/taglib.md) voor JSP-scripts.

### Parameters {#parameters-6}

* **context**: String of object

  (Optioneel, tenzij een relatief pad wordt opgegeven)

  Gebruiken `this` om de huidige context door te geven.

  Gebruiken `this.id` om de bron te verkrijgen op `id` voor het renderen van het aangevraagde resourceType.

* **resourceType**: String

  (Facultatief) middeltype gebreken aan middeltype van context.

* **template**: String

  Pad naar componentscript.

* **pad**: String

  (Vereist) Het pad naar de bron. Als het pad relatief is, moet een context worden opgegeven, anders wordt de lege tekenreeks geretourneerd.

* **authoringDisabled**: Boolean

  (Optioneel) Standaard is false. Alleen voor intern gebruik.

### Voorbeeld {#example-4}

```
{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}
```

Bevat een nieuwe component comments op `this.id` + /comments.

## IncludeClientLib {#includeclientlib}

Een helper die een AEM HTML- cliëntbibliotheek omvat, die een js, een css of een themabibliotheek kan zijn. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in het Handlebars-script.

Deze helper, die alleen geschikt is aan de serverzijde, biedt functionaliteit die lijkt op [ui:includeClientLib](../../help/sites-developing/taglib.md) voor JSP-scripts.

### Parameters {#parameters-7}

* **categorieën**: String

  (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Alle JavaScript- en CSS-bibliotheken opnemen voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

* **thema**: String

  (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Alle themabibliotheken (zowel CSS als JS) opnemen voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

* **js**: String

  (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Bevat alle JavaScript-bibliotheken voor de opgegeven categorieën.

* **css**: String

  (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Bevat alle CSS-bibliotheken voor de opgegeven categorieën.

### Voorbeelden {#examples-2}

```
// all: js + theme (theme-js + css)
{{includeClientLib categories="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// only js libs
{{includeClientLib js="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// theme only (theme-js + css)
{{includeClientLib theme="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// css only
{{includeClientLib css="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
```

## Nochtans {#pretty-time}

Een hulpmiddel om te tonen hoeveel tijd tot een afbreekpunt is overgegaan, waarna een regelmatige datumformaat wordt getoond.

Bijvoorbeeld:

* 12 uur geleden
* 7 dagen geleden

### Parameters {#parameters-8}

* **context**: Number

  Een tijd in het verleden om te vergelijken met &quot;nu&quot;. Tijd wordt uitgedrukt als een millisecondenverschuiving vanaf 1 januari 1970 (tijdperk).

* **daysCutoff**: Number

  Het aantal dagen geleden voordat wordt overgeschakeld op een werkelijke datum. De standaardwaarde is 60.

### Voorbeeld {#example-5}

```
{{pretty-time this.published daysCutoff=7}}

/*
Depending on how long in the past, may return

  "3 minutes ago"

  "3 hours ago"

  "3 days ago"
*/
```

## Xss-html {#xss-html}

Een hulpmiddel dat een bronkoord voor HTML elementinhoud codeert helpen tegen XSS beschermen.

OPMERKING: deze helper is geen validator en mag niet worden gebruikt voor het schrijven van kenmerkwaarden.

### Parameters {#parameters-9}

* **context**: object

  De te coderen HTML.

### Voorbeeld {#example-6}

```
<p>{{xss-html forum-ugc}}</p>
```

## Xss-htmlAttr {#xss-htmlattr}

Een helper die een bronkoord codeert voor het schrijven aan een waarde van het attribuut van HTML helpen tegen XSS beschermen.

OPMERKING: deze helper is geen validator en mag niet worden gebruikt voor het schrijven van actiefattributen (href, src, gebeurtenishandlers).

### Parameters {#parameters-10}

* **context**: Object

  De te coderen HTML.

### Voorbeeld {#example-7}

```
<div id={{xss-htmlAttr id}} />
```

## Xss-jsString {#xss-jsstring}

Een hulpmiddel dat een bronkoord codeert voor het schrijven aan JavaScript koordinhoud helpen tegen XSS beschermen.

OPMERKING: deze helper is geen validator en mag niet worden gebruikt voor het schrijven naar willekeurig JavaScript.

### Parameters {#parameters-11}

* **context**: Object

  De te coderen HTML.

### Voorbeeld {#example-8}

```
var input = {{xss-jsString topic-title}}
```

## Xss-validHref {#xss-validhref}

Een helper die een URL ontsmetten voor het schrijven als HTML href of srce attributenwaarde helpen tegen XSS.

OPMERKING: deze hulpfunctie kan een lege tekenreeks retourneren.

### Parameters {#parameters-12}

* **context**: Object

  De URL die moet worden ontsmet.

### Voorbeeld {#example-9}

```
<a href="{{xss-validHref url}}">my link</a>
```

## Handlebars.js Basic - Overzicht {#handlebars-js-basic-overview}

* Een hulpvraag van Handlebars is eenvoudig herkenningsteken ( *name* van de helper), gevolgd door nul of meer door spaties gescheiden parameters.
* Parameters kunnen een eenvoudig String-, Number-, Boolean- of JSON-object zijn, en een optionele reeks sleutelwaardeparen (hash-argumenten) als de laatste parameters.
* De sleutels in hakargumenten moeten eenvoudige herkenningstekens zijn.
* De waarden in hashargumenten zijn Handlebars-expressies: eenvoudige id&#39;s, paden of Tekenreeksen.
* De huidige context, `this`, is altijd beschikbaar voor de helpers van Handlebars.
* De context kan een String, Number, boolean of een JSON-gegevensobject zijn.
* Het is mogelijk een object door te geven dat in de huidige context als de context is genest, zoals `this.url` of `this.id` (zie de volgende voorbeelden van eenvoudige en blokhulplijnen).

* De helpers van het blok zijn functies die van overal in het malplaatje kunnen worden geroepen. Ze kunnen een blok van de sjabloon telkens nul of meer keer aanroepen met een andere context. Ze bevatten een context tussen `{{#*name*}}` en `{{/*name*}}`.

* Handlebars verstrekken een definitieve parameter aan helpers genoemd &quot;opties&quot;. Het speciale object &#39;options&#39; bevat

   * Optionele privégegevens (options.data)
   * Optionele sleutel-waarde eigenschappen van de aanroep (options.hash)
   * Mogelijkheid om zichzelf aan te roepen (options.fn())
   * Mogelijkheid om de inverse van zichzelf aan te roepen (options.inverse())

* Men adviseert dat de inhoud van het Koord van HTML die van een helper wordt teruggekeerd een SafeString is.

### Een voorbeeld van een eenvoudige helper van documentatie Handlebars.js: {#an-example-of-a-simple-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link_to', function(title, options) {
    return new Handlebars.SafeString('<a href="/posts' + this.url + '">' + title + "!</a>");
});

var context = {posts: [
    {url: "/hello-world",
      body: "Hello World!"}
  ] };

// when link_to is called, posts is the current context
var source = '<ul>`{{#posts}}`<li>{{{link_to "Post"}}}</li>`{{/posts}}`</ul>'

var template = Handlebars.compile(source);

template(context);
```

Zou renderen:

&lt;ul>
&lt;li>&lt;a href=&quot;/posts/hello-world&quot;>Publiceren!&lt;/a>&lt;/li>
&lt;/ul>

### Een voorbeeld van een blokhelper van documentatie Handlebars.js: {#an-example-of-a-block-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link', function(options) {
    return new Handlebars.SafeString('<a href="/people/' + this.id + '">' + options.fn(this) + '</a>');
});

var data = { "people": [
  { "name": "Alan", "id": 1 },
  { "name": "Yehuda", "id": 2 }
]};

// when link is called, people is the current context
var source = "<ul>`{{#people}}`<li>`{{#link}}``{{name}}``{{/link}}`</li>`{{/people}}`</ul>";

var template = Handlebars.compile(source);

template(data);
```

Zou renderen:
&lt;ul>
&lt;li>&lt;a href=&quot;/people/1&quot;>Alan&lt;/a>&lt;/li>
&lt;li>&lt;a href=&quot;/people/2&quot;>Yehuda&lt;/a>&lt;/li>
&lt;/ul>

## Aangepaste SCF-hulplijnen {#custom-scf-helpers}

Aangepaste helpers moeten aan de serverzijde en client-kant worden geïmplementeerd, vooral wanneer gegevens worden doorgegeven. Voor SCF, worden de meeste malplaatjes gecompileerd en op server-kant teruggegeven aangezien de server de HTML voor een bepaalde component produceert wanneer de pagina wordt gevraagd.

### Aangepaste hulp op de server {#server-side-custom-helpers}

Om een douaneSCF helper op de server uit te voeren en te registreren, voer eenvoudig de interface Java™ uit [TemplateHelper](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/handlebars/api/TemplateHelper.html), maak er een [OSGi-service](../../help/sites-developing/the-basics.md#osgi) en installeer het als deel van een bundel OSGi.

Bijvoorbeeld:

### FooTextHelper.java {#footexthelper-java}

```java
/** Custom Handlebars Helper */

package com.my.helpers;

import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

import com.adobe.cq.social.handlebars.api.TemplateHelper;
import com.github.jknack.handlebars.Options;

@Service
@Component
public class FooTextHelper implements TemplateHelper<String>{

    @Override
    public CharSequence apply(String context, Options options) throws IOException {
        return "foo-" + context;
    }

    @Override
    public String getHelperName() {
        return "foo-text";
    }

    @Override
    public Class<String> getContextType() {
        return String.class;
    }
}
```

>[!NOTE]
>
>Een helper die voor server-kant wordt gecreeerd moet ook voor cliënt-kant worden gecreeerd.
>
>De component wordt re-teruggegeven op de cliënt-kant voor de aangemelde gebruiker, en als de cliënt-zijhelper niet wordt gevonden, verdwijnt de component.

### Aangepaste hulp aan clientzijde {#client-side-custom-helpers}

De helpers aan de clientzijde zijn Handlebars-scripts die zijn geregistreerd door het aanroepen van `Handlebars.registerHelper()`.
Bijvoorbeeld:

### custom-helpers.js {#custom-helpers-js}

```
function(Handlebars, SCF, $CQ) {

    Handlebars.registerHelper('foo-text', function(context, options) {
        if (!context) {
            return "";
        }
        return "foo-" + context;
    });

})(Handlebars, SCF, $CQ);
```

De aangepaste client-side helpers moeten worden toegevoegd aan een aangepaste clientbibliotheek.
Clilib moet:

* Een afhankelijkheid opnemen van `cq.social.scf`.
* Laden nadat handgrepen zijn geladen.
* zijn [inbegrepen](clientlibs.md).

Opmerking: de SCF-helpers zijn gedefinieerd in `/etc/clientlibs/social/commons/scf/helpers.js`.

| **[Essentiële ⇐ functies](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|   | **[Aanpassing aan client-side bezig](client-customize.md)** |
