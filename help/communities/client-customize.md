---
title: Aanpassing aan clientzijde
seo-title: Aanpassing aan clientzijde
description: Gedrag of weergave van de client in AEM Communities aanpassen
seo-description: Gedrag of weergave van de client in AEM Communities aanpassen
uuid: 57978c39-9a8a-4098-9001-c8bbe7ee786f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 24b6d1d2-c118-4a25-959f-2783961c4ae3
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 0%

---


# Aanpassing aan clientzijde {#client-side-customization}

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|  | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

Er zijn verschillende manieren om de weergave en/of het gedrag van een AEM Communities-component op de client aan te passen.

Twee belangrijke benaderingen zijn het bedekken of uitbreiden van een component.

[Als u een component ](#overlays) overschrijft, wordt de standaardcomponent gewijzigd en wordt elke verwijzing naar de component gewijzigd.

[Als u een component ](#extensions) uitbreidt met een unieke naam, beperkt u het bereik van wijzigingen. De term &#39;extend&#39; wordt door elkaar gebruikt met &#39;override&#39;.

## Bedekkingen {#overlays}

Het bedekken van een component is een methode om wijzigingen aan een standaardcomponent aan te brengen en alle instanties te beïnvloeden die het gebrek gebruiken.

De bedekking wordt verwezenlijkt door een exemplaar van de standaardcomponent in de folder te wijzigen /**apps**, eerder dan het wijzigen van de originele component in /**libs** folder. De component is geconstrueerd met een identiek relatief pad, behalve dat &#39;libs&#39; wordt vervangen door &#39;apps&#39;.

De map /apps is de eerste plaats die wordt gezocht om aanvragen op te lossen. Als deze niet wordt gevonden, wordt de standaardversie in de map /libs gebruikt.

De standaardcomponent in de /libs folder moet nooit worden gewijzigd aangezien de toekomstige flarden en de verbeteringen vrij zijn om de /libs folder op om het even welke manier noodzakelijk te veranderen terwijl het handhaven van openbare interfaces.

Dit is verschillend van [het uitbreiden van](#extensions) een standaardcomponent waar het verlangen wijzigingen voor een specifiek gebruik moet maken, die tot een uniek weg aan de component leiden en zich baserend op het van verwijzingen voorzien van de originele standaardcomponent in de /libs folder als supermiddeltype baseren.

Voor een snel voorbeeld van het bedekken van de commentaarcomponent, probeer [de Onderzelfstudie van de Component van Commentaren van de Bedekking](overlay-comments.md).

## Extensies {#extensions}

Het uitbreiden (met voeten treden) van een component is een methode om wijzigingen voor een specifiek gebruik aan te brengen zonder alle instanties te beïnvloeden die het gebrek gebruiken. De uitgebreide component krijgt een unieke naam in de map /apps en verwijst naar de standaardcomponent in de map /libs, zodat het standaardontwerp en de standaardwerking van een component niet worden gewijzigd.

Dit verschilt van [het bedekken](#overlays) de standaardcomponent waar de aard van het Sling relatieve verwijzingen naar apps/omslag alvorens in de libs/ omslag te zoeken oplost, zodat wordt het ontwerp of het gedrag van een component globaal gewijzigd.

Voor een snel voorbeeld van het uitbreiden van de commentaarcomponent, probeer [breid de Component van Commentaren uit leerprogramma](extend-comments.md).

## JavaScript-binding {#javascript-binding}

Het HBS-script voor de component moet zijn gebonden aan de JavaScript-objecten, -modellen en -weergaven, die deze functie implementeren.

De waarde van het kenmerk `data-scf-component` kan de standaardwaarde zijn, zoals **`social/tally/components/hbs/rating`**, of een uitgebreide (aangepaste) component voor aangepaste functionaliteit, zoals **weretail/components/hbs/rating**.

Om een component te binden, moet het volledige componentenmanuscript binnen een &lt;div> element met de volgende attributen worden ingesloten:

* `data-component-id`=&quot;{{id}}&quot;

   wordt vanuit de context omgezet in de eigenschap id

* `data-scf-component`=&quot;*&lt;resourcetype>*

Bijvoorbeeld uit `/apps/weretail/components/hbs/rating/rating.hbs`:

```xml
<div class="we-Rating" data-component-id="{{id}}" data-scf-component="weretail/components/hbs/rating">

     <!-- HTML with HBS accessing the rating component -->

</div>
```

## Eigen eigenschappen {#custom-properties}

Wanneer u een component uitbreidt of bedekt, is het mogelijk eigenschappen toe te voegen aan een gewijzigd dialoogvenster.

Alle eigenschappen die op een component/een middel worden geplaatst kunnen worden betreden door de bezitssleutels in het zakbalkmalplaatje van verwijzingen te voorzien:

`{{properties.<property_name>}}`

## CSS {#skinning-css} schuintrekken

Componenten aanpassen aan het algemene thema van de website kan worden bereikt door &#39;skins&#39; toe te wijzen. Kleuren, lettertypen, afbeeldingen, knoppen, koppelingen, afstand en zelfs positionering worden in zekere mate gewijzigd.

Skin maken kan worden bereikt door de framestijlen selectief te overschrijven of door geheel nieuwe stijlpagina&#39;s te schrijven. De componenten SCF bepalen namespaced, modulaire en semantische CSS klassen die de diverse elementen beïnvloeden die omhoog een component maken.

Een skin toewijzen aan een component:

1. Identificeer de elementen die u wilt wijzigen (bijvoorbeeld: compositiegebied, werkbalkknoppen, berichtlettertype, enz.).
1. Identificeer de CSS klasse/de regels die deze elementen beïnvloeden.
1. Maak een stijlbladbestand (.css).
1. Neem het opmaakmodel op in een clientbibliotheekmap ([clientlibs](#clientlibs-for-scf)) voor uw site en zorg ervoor dat dit opneemt vanuit uw sjablonen en pagina&#39;s met [ui:includeClientLib](../../help/sites-developing/clientlibs.md).

1. Definieer de CSS-klassen en -regels die u hebt geïdentificeerd (#2) in uw stijlpagina opnieuw en voeg stijlen toe.

De aangepaste stijlen overschrijven nu de standaardframestijlen en de component wordt weergegeven met de nieuwe skin.

>[!CAUTION]
>
>Elke CSS-klassenaam die wordt voorafgegaan door `scf-js`, heeft een specifiek gebruik in javascript-code. Deze klassen beïnvloeden de status van een component (bijvoorbeeld van verborgen naar zichtbaar schakelen) en mogen niet worden overschreven of verwijderd.
>
>Hoewel de `scf-js`-klassen geen invloed hebben op stijlen, kunnen de klassennamen in stijlpagina&#39;s worden gebruikt met het voorbehoud dat er, aangezien ze de status van elementen bepalen, bijwerkingen kunnen optreden.

## JavaScript {#extending-javascript} uitbreiden

Als u een JavaScript-implementatie voor componenten wilt uitbreiden, moet u:

1. Maak een component voor u-app met een jcr:resourceSuperType dat is ingesteld op de waarde van jcr:resourceType van de uitgebreide component, bijvoorbeeld social/forum/components/hbs/forum.
1. Onderzoek Javascript van de standaardSCF component om te bepalen welke methodes moeten worden geregistreerd gebruikend SCF.registerComponent ().
1. Kopieer het JavaScript van de uitgebreide component of begin helemaal opnieuw.
1. Breid de methode uit.
1. Gebruik SCF.registerComponent() om alle methoden te registreren met de standaardinstellingen of de aangepaste objecten en weergaven.

### forum.js: Voorbeeld van uitbreiding van forum - GB {#forum-js-sample-extension-of-forum-hbs}

```xml
(function($CQ, _, Backbone, SCF) {
    "use strict";
    var GMForumView = SCF.ForumView.extend({
        viewName: "GMForum",
        showComposer: function(e) {
            SCF.ForumView.prototype.toggleComposer.apply(this);
            var cancel = this.$el.find('.cancel-new-topic');
            cancel.toggle();
        },
        hideComposer: function(e) {
            SCF.ForumView.prototype.toggleComposer.apply(this);
            var cancel = this.$el.find('.cancel-new-topic');
            cancel.toggle();
        }
    });

    SCF.registerComponent('social/forum/components/hbs/post', SCF.Post, SCF.PostView);
    SCF.registerComponent('social/forum/components/hbs/topic', SCF.Topic, SCF.TopicView);
    SCF.registerComponent('social/forum/components/hbs/forum', SCF.Forum, GMForumView );
})($CQ, _, Backbone, SCF);
```

## Scriptlabels {#script-tags}

Scripttags vormen een inherent onderdeel van het clientframework. Zij zijn de lijm die de prijsverhoging bindt die op de serverkant met de modellen en de meningen op de cliëntkant wordt geproduceerd.

Scripttags in SCF-scripts mogen niet worden verwijderd wanneer componenten worden overschreven of overschreven. SCF-scripttags die automatisch zijn gemaakt voor het injecteren van JSON in de HTML, worden aangeduid met het kenmerk `data-scf-json=true`.

## Clientlibs voor SCF {#clientlibs-for-scf}

Het gebruik van [client-side bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) biedt een manier om de JavaScript en CSS die worden gebruikt om inhoud op de client te renderen, te organiseren en te optimaliseren.

De clientlibs voor SCF volgen een zeer specifiek noemingspatroon voor twee varianten, die slechts door de aanwezigheid van &quot;auteur&quot;in de categorienaam variëren:

| Clientlib-variabele | Patroon voor eigenschap Categorieën |
|--- |--- |
| complete clientlib | cq.social.hbs.&lt;component name=&quot;&quot;> |
| auteur-clientlib | cq.social.author.hbs.&lt;component name=&quot;&quot;> |

### Volledige Clientlibs {#complete-clientlibs}

De volledige (niet-auteur) clientlibs bevatten afhankelijkheden en zijn handig voor het opnemen met ui:includeClientLib.

Deze versies zijn te vinden in:

* `/etc/clientlibs/social/hbs/&lt;component name&gt;`

Bijvoorbeeld:

* Clientmapknooppunt: `/etc/clientlibs/social/hbs/forum`
* Eigenschap Categorieën: `cq.social.hbs.forum`

De [Community Components guide](components-guide.md) maakt een lijst van de volledige clientlibs die voor elke SCF component worden vereist.

[Clientlibs voor Community ](clientlibs.md) Componenten beschrijft hoe u clientlibs aan een pagina kunt toevoegen.

### Clientlibs {#author-clientlibs}

De clientlibs van de auteurversie worden gestript neer aan minimale JavaScript noodzakelijk om de component uit te voeren.

Deze clientlibs moeten nooit rechtstreeks worden opgenomen, maar zijn in plaats daarvan beschikbaar om in andere clientlibs in te sluiten, die voor een site worden gemaakt.

Deze versies staan in de map SCF libs:

* `/libs/social/&lt;feature&gt;/components/hbs/&lt;component name&gt;/clientlibs`

Bijvoorbeeld:

* Clientmapknooppunt: `/libs/social/forum/hbs/forum/clientlibs`
* Eigenschap Categorieën: `cq.social.author.hbs.forum`

Opmerking: hoewel auteur clientlibs geen andere bibliotheken inbedden , maken ze een lijst van hun afhankelijkheden . Wanneer de afhankelijkheden zijn ingesloten in andere bibliotheken, worden deze niet automatisch ingesloten en moeten ze ook worden ingesloten.

De vereiste auteur clientlibs kunnen worden geïdentificeerd door &quot;auteur&quot;in de clientlibs op te nemen die voor elke component SCF in [Community Components guide](components-guide.md) worden vermeld.

### Overwegingen bij gebruik {#usage-considerations}

Elke site is anders in de manier waarop ze clientbibliotheken beheren. Enkele factoren zijn:

* Totale snelheid: Misschien is het de wens dat de site reageert, maar het is acceptabel dat de eerste pagina een beetje traag wordt geladen. Als veel van de pagina&#39;s dezelfde Javascript gebruiken, kunnen de verschillende Javascripts in één client worden ingesloten en kan er vanaf de eerste pagina naar worden verwezen om te laden. Het JavaScript in deze enkele download blijft in het cachegeheugen opgeslagen, waardoor de hoeveelheid gegevens die voor volgende pagina&#39;s moet worden gedownload, tot een minimum wordt beperkt.
* Korte tijd tot eerste pagina: Misschien is het de bedoeling dat de eerste pagina snel wordt geladen. In dit geval bevat het JavaScript-bestand meerdere kleine bestanden waarnaar alleen kan worden verwezen als dat nodig is.
* Een balans tussen het laden van de eerste pagina en volgende downloads.

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|  | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

