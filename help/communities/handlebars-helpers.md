---
title: SCF Handlebars Helpers
seo-title: SCF Handlebars Helpers
description: De methodes van de Helper van de bars om het werk met SCF te vergemakkelijken
seo-description: De methodes van de Helper van de bars om het werk met SCF te vergemakkelijken
uuid: 9c514199-871e-4b68-8147-2052d2eeda15
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8b6c1697-d693-41f4-8337-f41658465107
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 2%

---


# SCF Handlebars Helpers {#scf-handlebars-helpers}

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|  | **[Aanpassing aan clientzijde☐](client-customize.md)** |

Handlebars Helpers (helpers) zijn methodes callable van de manuscripten van Handlebars om het werken met componenten te vergemakkelijken SCF.

De implementatie omvat een client-side en een server-side definitie. Ontwikkelaars kunnen ook aangepaste hulplijnen maken.

De aangepaste SCF-helpers die bij AEM Communities worden geleverd, worden gedefinieerd in de [clientbibliotheek](../../help/sites-developing/clientlibs.md):

* `/etc/clientlibs/social/commons/scf/helpers.js`

>[!NOTE]
>
>Zorg ervoor dat u het [nieuwste bronnenpakket](deploy-communities.md#latestfeaturepack)van de Gemeenschappen installeert.

## Afkorting {#abbreviate}

Een helper om een afgekorte tekenreeks te retourneren die voldoet aan de eigenschappen maxWords en maxLength.

De tekenreeks die moet worden afgekort, wordt opgegeven als de context. Als er geen context is opgegeven, wordt een lege tekenreeks geretourneerd.

Eerst wordt de context bijgesneden tot maxLength en vervolgens wordt de context in woorden gesegmenteerd en tot maxWords teruggebracht.

Als safeString is ingesteld op true, is de geretourneerde tekenreeks een SafeString.

### Parameters {#parameters}

* **context**: String

   (Optioneel) Standaard is de lege tekenreeks

* **maxLength**: Getal

   (Optioneel) Standaard is de lengte van de context.

* **maxWords**: Getal

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

* **numChars**: Getal

   (Optioneel) Het aantal tekens dat moet worden weergegeven wanneer geen volledige tekst wordt weergegeven. De standaardwaarde is 100.

* **moreText**: String

   (Optioneel) De tekst die moet worden weergegeven om aan te geven dat er meer tekst moet worden weergegeven. Standaard is &quot;meer&quot;.

* **ellipsesText**: String

   (Optioneel) De tekst die moet worden weergegeven om aan te geven dat er verborgen tekst is. Standaard is &quot;...&quot;.

* **safeString**: Boolean

   (Optioneel) Booleaanse waarde die aangeeft of Handlebars.SafeString() al dan niet moet worden toegepast voordat het resultaat wordt geretourneerd. De standaardwaarde is false.

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

* **context**: Getal

   (Optioneel) Een millisecondenverschuiving vanaf 1 januari 1970 (tijdperk). De standaardwaarde is de huidige datum.

* **indeling**: String

   (Optioneel) De datumnotatie die moet worden toegepast. De standaardwaarde is &quot;YYYY-MM-DDTHH:mm:ss.sssZ&quot; en het resultaat wordt weergegeven als &quot;2015-03-18T18:17:13-07:00&quot;

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

   De waarde aan de linkerkant die moet worden vergeleken.

* **waarde**: String

   De rechterwaarde die moet worden vergeleken.

### Voorbeeld {#example-1}

```
{{#equals  value "some-value"}}
  <div>They are EQUAL!</div>
{{else}}
  <div>They are NOT equal!</div>
{{/equals}}
```

## If-wcm-mode {#if-wcm-mode}

Een blokhelper die de huidige waarde van wijze [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) WCM tegen een koord gescheiden lijst van wijzen test.

### Parameters {#parameters-4}

* **context**: String

   (Optioneel) De tekenreeks die moet worden vertaald. Vereist als er geen standaard is opgegeven.

* **modus**: String

   (Optioneel) Een door komma&#39;s gescheiden lijst met [WCM-modi](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) die moeten worden getest, indien ingesteld.

### Voorbeeld {#example-2}

```xml
{{#if-wcm-mode mode="DESIGN, EDIT"}}
 ...
{{else}}
 ...
{{/if-wcm-mode}}
```

## i18n {#i-n}

Deze hulp treedt helper &quot;i18n&quot;van Handlebars met voeten.

Zie ook [Internationaliserende Tekenreeksen in JavaScript-code](../../help/sites-developing/i18n-dev.md#internationalizing-strings-in-javascript-code).

### Parameters {#parameters-5}

* **context**: String

   (Optioneel) De tekenreeks die moet worden vertaald. Vereist als er geen standaard is opgegeven.

* **standaard**: String

   (Optioneel) De standaardtekenreeks die moet worden getransleerd. Vereist als er geen context is opgegeven.

* **opmerking**: String

   (Optioneel) Een vertaaltip

### Voorbeeld {#example-3}

```
{{i18n "hello"}}
{{i18n "hello" comment="greeting" default="bonjour"}}
```

## Opnemen {#include}

Een hulpmiddel om een component als niet bestaand middel in een malplaatje te omvatten.

Hierdoor kan de bron beter programmatisch worden aangepast dan mogelijk is voor een bron die als JCR-knooppunt wordt toegevoegd. Zie Een onderdeel [](scf.md#add-or-include-a-communities-component)van een Gemeenschappen toevoegen of opnemen.

Slechts een paar communautaire componenten zijn inbegrepen. Voor AEM 6.1 zijn de meegeleverde opmerkingen [opmerkingen](essentials-comments.md), [beoordelingen](rating-basics.md), [beoordelingen](reviews-basics.md)en [stemmingen](essentials-voting.md).

Deze hulp, die slechts op de server-kant aangewezen is, verstrekt functionaliteit gelijkend op [cq:omvat](../../help/sites-developing/taglib.md) voor manuscripten JSP.

### Parameters {#parameters-6}

* **context**: Tekenreeks of object

   (Optioneel, tenzij een relatief pad wordt opgegeven)

   Gebruik deze optie `this` om de huidige context door te geven.

   Gebruik `this.id` om het middel bij te verkrijgen `id` voor het teruggeven van gevraagde resourceType.

* **resourceType**: String

   (Facultatief) middeltype zal aan middeltype van context in gebreke blijven.

* **sjabloon**: String

   Pad naar componentscript.

* **pad**: String

   (Vereist) Het pad naar de bron. Als het pad relatief is, moet een context worden opgegeven, anders wordt de lege tekenreeks geretourneerd.

* **authoringDisabled**: Boolean

   (Optioneel) Standaard is false. Uitsluitend voor intern gebruik.

### Voorbeeld {#example-4}

```
{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}
```

Dit omvat een nieuwe commentaarcomponent bij `this.id` + /comments.

## IncludeClientLib {#includeclientlib}

Een helper die een AEM HTML- cliëntbibliotheek omvat, die een js, een css of een themabibliotheek kan zijn. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in het Handlebars-script.

Deze hulp, aangewezen slechts op de server-kant, verstrekt functionaliteit gelijkend op [ui:includeClientLib](../../help/sites-developing/taglib.md) voor manuscripten JSP.

### Parameters {#parameters-7}

* **categorieën**: String

   (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle JavaScript- en CSS-bibliotheken voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

* **thema**: String

   (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle themabibliotheken (zowel CSS als JS) voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

* **js**: String

   (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle bibliotheken Javascript voor de bepaalde categorieën.

* **css**: String

   (Optioneel) Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle CSS-bibliotheken voor de opgegeven categorieën.

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

* **context**: Getal

   Een tijd in het verleden om te vergelijken met &quot;nu&quot;. Tijd wordt uitgedrukt als een millisecondenverschuiving vanaf 1 januari 1970 (tijdperk).

* **daysCutoff**: Getal

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

Een hulpmiddel dat een bronkoord voor de elementeninhoud van HTML codeert helpen tegen XSS.

OPMERKING: Dit is geen validator en moet niet worden gebruikt voor het schrijven van kenmerkwaarden.

### Parameters {#parameters-9}

* **context**: object

   De HTML die moet worden gecodeerd.

### Voorbeeld {#example-6}

```
<p>{{xss-html forum-ugc}}</p>
```

## Xss-htmlAttr {#xss-htmlattr}

Een hulpmiddel dat een bronkoord codeert voor het schrijven aan een de attributenwaarde van HTML helpen tegen XSS beschermen.

OPMERKING: dit is geen validator en moet niet worden gebruikt voor het schrijven van actionable attributen (href, src, gebeurtenismanagers).

### Parameters {#parameters-10}

* **context**: Object

   De HTML die moet worden gecodeerd.

### Voorbeeld {#example-7}

```
<div id={{xss-htmlAttr id}} />
```

## Xss-jsString {#xss-jsstring}

Een hulpmiddel dat een bronkoord codeert voor het schrijven aan JavaScript koordinhoud helpen tegen XSS beschermen.

OPMERKING: Dit is geen validator en mag niet worden gebruikt voor het schrijven naar willekeurig JavaScript.

### Parameters {#parameters-11}

* **context**: Object

   De HTML die moet worden gecodeerd.

### Voorbeeld {#example-8}

```
var input = {{xss-jsString topic-title}}
```

## Xss-validHref {#xss-validhref}

Een helper die een URL ontsmetten voor het schrijven als href van HTML of srce attributenwaarde helpen tegen XSS.

OPMERKING: dit kan een lege tekenreeks retourneren

### Parameters {#parameters-12}

* **context**: Object

   De URL die moet worden ontsmet.

### Voorbeeld {#example-9}

```
<a href="{{xss-validHref url}}">my link</a>
```

## Handlebars.js Basic - Overzicht {#handlebars-js-basic-overview}

Een kort overzicht van hulpfuncties in de documentatie [van](https://handlebarsjs.com/expressions.html)Handlebars.js:

* Een hulpvraag van Handlebars is een eenvoudig herkenningsteken (de *naam* van de helper), die door nul of meer ruimte-gescheiden parameters wordt gevolgd.
* Parameters kunnen een eenvoudig String-, Number-, Boolean- of JSON-object zijn, plus een optionele reeks sleutelwaardeparen (hash-argumenten) als de laatste parameter(s).
* De sleutels in knoeiboelargumenten moeten eenvoudige herkenningstekens zijn.
* De waarden in hash-argumenten zijn Handlebars-expressies: eenvoudige id&#39;s, paden of tekenreeksen.
* De huidige context, `this`, is altijd beschikbaar aan helpers Handlebars.
* De context kan een String, Number, boolean of een JSON-gegevensobject zijn.
* Het is mogelijk om een object door te geven dat is genest in de huidige context als de context, zoals `this.url` of `this.id` (zie de volgende voorbeelden van eenvoudige en blokhulplijnen).

* De helpers van het blok zijn functies die van overal in het malplaatje kunnen worden geroepen. Ze kunnen een blok van de sjabloon telkens nul of meer keer aanroepen met een andere context. Ze bevatten een context tussen {{#*name*}} en {{/*name*}}.

* Handlebars verstrekt een definitieve parameter aan helpers genoemd &quot;opties&quot;. Het speciale object &#39;options&#39; bevat

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
var source = '<ul>{{#posts}}<li>{{{link_to "Post"}}}</li>{{/posts}}</ul>'

var template = Handlebars.compile(source);

template(context);
```

Zou renderen:

&lt;ul>&lt;li>&lt;a href=&quot;/posts/hello-world&quot;>Post!&lt;/a>&lt;/li>&lt;/ul>

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
var source = "<ul>{{#people}}<li>{{#link}}{{name}}{{/link}}</li>{{/people}}</ul>";

var template = Handlebars.compile(source);

template(data);
```

Zou renderen:
&lt;ul>&lt;li>&lt;a href=&quot;/people/1&quot;>Alan&lt;/a>&lt;/li>&lt;li>&lt;a href=&quot;/people/2&quot;>Yehuda&lt;/a>&lt;/li>&lt;/ul>

## Aangepaste SCF-hulplijnen {#custom-scf-helpers}

Aangepaste helpers moeten zowel aan de serverzijde als aan de clientzijde worden geïmplementeerd, vooral wanneer gegevens worden doorgegeven. Voor SCF, worden de meeste malplaatjes gecompileerd en op server-kant teruggegeven aangezien de server HTML voor een bepaalde component produceert wanneer de pagina wordt gevraagd.

### Aangepaste hulp op de server {#server-side-custom-helpers}

Om een hulp van douaneSCF op server-kant uit te voeren en te registreren, voer eenvoudig de interface [TemplateHelper](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/handlebars/api/TemplateHelper.html)van Java uit, maak het een [Dienst](../../help/sites-developing/the-basics.md#osgi) OSGi en installeer het als deel van een bundel OSGi.

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

De client-side helpers zijn Handlebars-scripts die zijn geregistreerd door het aanroepen `Handlebars.registerHelper()`.
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

* Neem een afhankelijkheid op van `cq.social.scf`.
* Laden nadat handgrepen zijn geladen.
* Moet worden [opgenomen](clientlibs.md).

Opmerking: de SCF-helpers worden gedefinieerd in `/etc/clientlibs/social/commons/scf/helpers.js`.

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|  | **[Aanpassing aan clientzijde☐](client-customize.md)** |

