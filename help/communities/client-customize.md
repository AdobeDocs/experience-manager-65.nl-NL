---
title: Aanpassing aan clientzijde
description: Gedrag of weergave van de client in AEM Communities aanpassen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: bf34f564-ac93-4c8c-95f7-8690d99d85cb
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 0%

---

# Aanpassing aan clientzijde  {#client-side-customization}

| **[Essentiële ⇐ functies](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

Er zijn verschillende manieren om de weergave en/of het gedrag van een AEM Communities-component op de client aan te passen.

Twee belangrijke benaderingen zijn het bedekken of uitbreiden van een component.

[Bedekken](#overlays) een component verandert de standaardcomponent en beïnvloedt elke verwijzing naar de component.

[Uitbreiden](#extensions) een component, die uniek wordt genoemd, beperkt het werkingsgebied van veranderingen. De term &#39;extend&#39; wordt door elkaar gebruikt met &#39;override&#39;.

## Bedekkingen {#overlays}

Het bedekken van een component is een methode om wijzigingen aan een standaardcomponent aan te brengen en alle instanties te beïnvloeden die het gebrek gebruiken.

De bedekking wordt verwezenlijkt door een exemplaar van de standaardcomponent in te wijzigen /**apps** in plaats van de oorspronkelijke component in de map / te wijzigen **libben** directory. De component is geconstrueerd met een identiek relatief pad, behalve dat &#39;libs&#39; wordt vervangen door &#39;apps&#39;.

De map /apps is de eerste plaats die wordt gezocht om aanvragen op te lossen. Als deze niet wordt gevonden, wordt de standaardversie in de map /libs gebruikt.

De standaardcomponent in de /libs folder moet nooit worden gewijzigd aangezien de toekomstige flarden en de verbeteringen vrij zijn om de /libs folder op om het even welke manier noodzakelijk te veranderen terwijl het handhaven van openbare interfaces.

Dit verschilt van [verlenging](#extensions) een standaardcomponent waar het verlangen wijzigingen voor een specifiek gebruik moet maken, die tot een uniek weg aan de component leidt en zich baseert op het van verwijzingen voorzien van de originele standaardcomponent in de /libs folder als super middeltype.

Voor een snel voorbeeld van het bedekken van de commentaarcomponent, probeer [Zelfstudie van de component Overlay Comments](overlay-comments.md).

## Extensies {#extensions}

Het uitbreiden (met voeten treden) van een component is een methode om wijzigingen voor een specifiek gebruik aan te brengen zonder alle instanties te beïnvloeden die het gebrek gebruiken. De uitgebreide component krijgt een unieke naam in de map /apps en verwijst naar de standaardcomponent in de map /libs, zodat het standaardontwerp en de standaardwerking van een component niet worden gewijzigd.

Dit verschilt van [bedekken](#overlays) De standaardcomponent waarin de aard van Sling relatieve verwijzingen naar apps/omslag alvorens in de libs/ omslag te zoeken oplost, zodat wordt het ontwerp of het gedrag van een component globaal gewijzigd.

Voor een kort voorbeeld van het uitbreiden van de commentaarcomponent, probeer [Zelfstudie opmerkingencomponent uitbreiden](extend-comments.md).

## JavaScript-binding {#javascript-binding}

Het HBS-script voor de component moet zijn gebonden aan de JavaScript-objecten, -modellen en -weergaven, die deze functie implementeren.

De waarde van `data-scf-component` kenmerk kan de standaardwaarde zijn, zoals **`social/tally/components/hbs/rating`** of een uitgebreide (aangepaste) component voor aangepaste functionaliteit, zoals **weretail/componenten/hbs/rating**.

Om een component te binden, moet het volledige componentenmanuscript binnen een worden ingesloten &lt;div> element met de volgende kenmerken:

* `data-component-id`=&quot;`{{id}}`&quot;

  wordt vanuit de context omgezet in de eigenschap id

* `data-scf-component`=&quot;*&lt;resourcetype>*

Bijvoorbeeld van `/apps/weretail/components/hbs/rating/rating.hbs`:

```xml
<div class="we-Rating" data-component-id="`{{id}}`" data-scf-component="weretail/components/hbs/rating">

     <!-- HTML with HBS accessing the rating component -->

</div>
```

## Aangepaste eigenschappen {#custom-properties}

Wanneer u een component uitbreidt of bedekt, is het mogelijk eigenschappen toe te voegen aan een gewijzigd dialoogvenster.

Alle eigenschappen die op een component/een middel worden geplaatst kunnen worden betreden door de bezitssleutels in het zakbalkmalplaatje van verwijzingen te voorzien:

`{{properties.<property_name>}}`

## CSS schuintrekken {#skinning-css}

Componenten aanpassen aan het algemene thema van de website kan worden bereikt door &#39;skins&#39; toe te wijzen. Kleuren, lettertypen, afbeeldingen, knoppen, koppelingen, afstand en zelfs een bepaalde positie worden gewijzigd.

Skin maken kan worden bereikt door de framestijlen selectief te overschrijven of door geheel nieuwe stijlpagina&#39;s te schrijven. De componenten SCF bepalen namespaced, modulaire, en semantische CSS klassen die de diverse elementen beïnvloeden die omhoog een component maken.

Een component skin geven:

1. Identificeer de elementen die u wilt veranderen (voorbeeld - composer gebied, toolbarknopen, berichtdoopvont, etc.).
1. Identificeer de CSS klasse/de regels die deze elementen beïnvloeden.
1. Maak een stijlbladbestand (.css).
1. Stijlblad opnemen in clientbibliotheekmap ([clientlibs](#clientlibs-for-scf)) voor uw site en zorg ervoor dat deze wordt opgenomen in uw sjablonen en pagina&#39;s met [ui:includeClientLib](../../help/sites-developing/clientlibs.md).

1. Definieer de CSS-klassen en -regels die u hebt geïdentificeerd (#2) in uw stijlpagina opnieuw en voeg stijlen toe.

De aangepaste stijlen overschrijven nu de standaardframestijlen en de component wordt met de nieuwe skin gerenderd.

>[!CAUTION]
>
>Elke CSS-klassennaam die vooraf is voorzien van `scf-js` heeft een specifiek gebruik in JavaScript-code. Deze klassen beïnvloeden de status van een component (bijvoorbeeld van verborgen naar zichtbaar schakelen) en mogen niet worden overschreven of verwijderd.
>
>Terwijl de `scf-js` klassen zijn niet van invloed op stijlen. De klassennamen kunnen in stijlbladen worden gebruikt met het voorwendsel dat er bijwerkingen kunnen optreden wanneer deze de status van elementen bepalen.

## JavaScript uitbreiden {#extending-javascript}

Als u een JavaScript-implementatie voor componenten wilt uitbreiden, moet u:

1. Maak een component voor uw app met een jcr:resourceSuperType dat is ingesteld op de waarde van jcr:resourceType van de uitgebreide component, bijvoorbeeld social/forum/components/hbs/forum.
1. Onderzoek JavaScript van de standaardSCF component om te bepalen welke methodes moeten worden geregistreerd gebruikend SCF.registerComponent ().
1. Kopieer het JavaScript van de uitgebreide component of begin helemaal opnieuw.
1. Breid de methode uit.
1. Gebruik SCF.registerComponent() om alle methoden te registreren met de standaardinstellingen of de aangepaste objecten en weergaven.

### forum.js: Sample Extension of Forum - HBS  {#forum-js-sample-extension-of-forum-hbs}

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

Het gebruik van [clientbibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs), biedt een manier om de JavaScript en CSS die worden gebruikt om inhoud op de client te renderen, te organiseren en te optimaliseren.

De clientlibs voor SCF volgen een zeer specifiek noemingspatroon voor twee varianten, die slechts door de aanwezigheid van &quot;auteur&quot;in de categorienaam variëren:

| Clientlib-variabele | Patroon voor eigenschap Categorieën |
|--- |--- |
| complete clientlib | cq.social.hbs.&lt;component name> |
| auteur-clientlib | cq.social.author.hbs.&lt;component name> |

### Volledige Clientlibs {#complete-clientlibs}

De volledige (niet-auteur) clientlibs bevatten afhankelijkheden en zijn handig voor het opnemen met ui:includeClientLib.

Deze versies zijn te vinden in:

* `/etc/clientlibs/social/hbs/&lt;component name&gt;`

Bijvoorbeeld:

* Clientmapknooppunt: `/etc/clientlibs/social/hbs/forum`
* Categorie-eigenschap: `cq.social.hbs.forum`

De [Community Components Guide](components-guide.md) maakt een lijst van de volledige clientlibs die voor elke component SCF wordt vereist.

[Clientlibs voor Community-componenten](clientlibs.md) beschrijft hoe u clientlibs aan een pagina kunt toevoegen.

### Auteur Clientlibs {#author-clientlibs}

De clientlibs van de auteurversie worden gestript neer aan minimale JavaScript noodzakelijk om de component uit te voeren.

Deze clientlibs moeten nooit rechtstreeks worden opgenomen, maar zijn in plaats daarvan beschikbaar om in andere clientlibs in te sluiten, die voor een site worden gemaakt.

Deze versies staan in de map SCF libs:

* `/libs/social/&lt;feature&gt;/components/hbs/&lt;component name&gt;/clientlibs`

Bijvoorbeeld:

* Clientmapknooppunt: `/libs/social/forum/hbs/forum/clientlibs`
* Categorie-eigenschap: `cq.social.author.hbs.forum`

Opmerking: hoewel auteur clientlibs geen andere bibliotheken heeft ingesloten, worden hun afhankelijkheden wel vermeld. Wanneer de afhankelijkheden zijn ingesloten in andere bibliotheken, worden deze niet automatisch ingesloten en moeten ze ook worden ingesloten.

De vereiste auteur clientlibs kunnen worden geïdentificeerd door &quot;auteur&quot;in de clientlibs op te nemen die voor elke component SCF in SCF worden vermeld [Community Components Guide](components-guide.md).

### Overwegingen bij gebruik {#usage-considerations}

Elke site is anders in de manier waarop ze clientbibliotheken beheren. Enkele factoren zijn:

* Algemene snelheid: misschien is het de bedoeling dat de site reageert, maar het is acceptabel dat de eerste pagina iets traag wordt geladen. Als veel pagina&#39;s dezelfde JavaScript gebruiken, kunnen de verschillende JavaScript-code in één client worden ingesloten en kan er vanaf de eerste pagina die moet worden geladen naar worden verwezen. Het JavaScript in deze enkele download blijft in het cachegeheugen opgeslagen, waardoor de hoeveelheid gegevens die voor volgende pagina&#39;s moet worden gedownload, tot een minimum wordt beperkt.
* Kort naar eerste pagina: misschien is het de bedoeling dat de eerste pagina snel wordt geladen. In dit geval bestaat de JavaScript-code uit meerdere kleine bestanden waarnaar alleen kan worden verwezen als dat nodig is.
* Een balans tussen het laden van de eerste pagina en volgende downloads.

| **[Essentiële ⇐ functies](essentials.md)** | **[Aanpassing aan server-side bezig jj.](server-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |
