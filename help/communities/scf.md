---
title: Framework sociale component
description: Het kader van de sociale component (SCF) vereenvoudigt het proces om, componenten van de Gemeenschappen te vormen aan te passen en uit te breiden
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 5ca58bc3-8505-4d91-9cd1-6b2e2671f1be
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1478'
ht-degree: 0%

---

# Framework sociale component {#social-component-framework}

Het sociale componentenkader (SCF) vereenvoudigt het proces om, componenten van Gemeenschappen op zowel server-kant als cliënt-kant te vormen aan te passen en uit te breiden.

De voordelen van het kader:

* **Functioneel**: Het gemak uit-van-de-doos van integratie met weinig of geen aanpassing voor 80% van gebruiksgevallen.
* **Skinnable**: Consistent gebruik van de attributen van HTML voor CSS het stileren.
* **Verlengbaar**: De implementatie van de component is voorwerp-georiënteerd en licht op bedrijfslogica - gemakkelijk om stijgende bedrijfslogin op server toe te voegen.
* **Flexibel**: Eenvoudige logica-less JavaScript malplaatjes die gemakkelijk worden bedekt en aangepast.
* **Toegankelijk**: De HTTP API steunt het posten van om het even welke cliënt, met inbegrip van mobiele apps.
* **Draagbaar**: Integreer/bedt in om het even welke webpagina die op om het even welke technologie wordt gebouwd.

Onderzoek op een auteur of publiceer instantie gebruikend de interactieve [&#x200B; gids van de Componenten van de Gemeenschap &#x200B;](components-guide.md).

## Overzicht {#overview}

In SCF, wordt een component samengesteld uit een POJO SocialComponent, een Malplaatje van Handlebars JS (om de component terug te geven), en CSS (om de component te stileren).

Een JS-sjabloon Handlebars kan de JS-componenten model/weergave uitbreiden om gebruikersinteractie met de component op de client af te handelen.

Als een component wijziging van gegevens moet ondersteunen, kan de implementatie van de API voor sociale componenten worden geschreven ter ondersteuning van het bewerken/opslaan van gegevens die vergelijkbaar zijn met model- en gegevensobjecten in traditionele webtoepassingen. Daarnaast kunnen bewerkingen (controllers) en een bewerkingsservice worden toegevoegd om bewerkingsverzoeken te verwerken, bedrijfslogica uit te voeren en de API&#39;s op het model/de gegevensobjecten aan te roepen.

De API van de sociale component kan worden uitgebreid om gegevens te verstrekken die door een cliënt voor een meningslaag of een cliënt van HTTP worden vereist.

### Hoe pagina&#39;s voor de client worden gerenderd {#how-pages-are-rendered-for-client}

![&#x200B; scf-pagina-teruggevend &#x200B;](assets/scf-overview.png)

### Component Customization and Extension {#component-customization-and-extension}

Als u de componenten wilt aanpassen of uitbreiden, schrijft u alleen de overlays en extensies naar de map /apps waarmee u het upgradeproces naar toekomstige releases kunt vereenvoudigen.

* Voor skin:
   * Slechts vereist [&#x200B; CSS het uitgeven &#x200B;](client-customize.md#skinning-css).
* Voor uiterlijk:
   * Wijzig de JS-sjabloon en de CSS.
* Voor look, Voel en UX:
   * Verander het Malplaatje JS, CSS, en [&#x200B; breid/treedt JavaScript &#x200B;](client-customize.md#extending-javascript) uit.
* Om de informatie beschikbaar aan het Malplaatje JS of aan het eindpunt van GET te wijzigen:
   * Breid [&#x200B; SocialComponent &#x200B;](server-customize.md#socialcomponent-interface) uit.
* Aangepaste verwerking toevoegen tijdens bewerkingen:
   * Schrijf een [&#x200B; OperationExtension &#x200B;](server-customize.md#operationextension-class).
* Een aangepaste bewerking toevoegen:
   * Creeer de Verrichting van Post van de a [&#x200B; Verschuiving &#x200B;](server-customize.md#postoperation-class).
   * Gebruik bestaande [&#x200B; OperationServices &#x200B;](server-customize.md#operationservice-class) zoals nodig.
   * Voeg JavaScript-code toe om uw bewerking zo nodig vanaf de client aan te roepen.

## Server-Side Framework {#server-side-framework}

Het framework biedt API&#39;s voor toegang tot functionaliteit op de server en voor ondersteuning van interactie tussen de client en de server.

### Java™ API&#39;s {#java-apis}

De Java™ API&#39;s bieden abstracte klassen en interfaces die gemakkelijk kunnen worden overgeërfd of gesubclassificeerd.

De belangrijkste klassen worden beschreven op de [&#x200B; server-kant pagina van de Aanpassing &#x200B;](server-customize.md).

Bezoek [&#x200B; Overzicht van de Leverancier van het Middel van de Opslag &#x200B;](srp.md) om over het werken met UGC te leren.

### HTTP-API {#http-api}

De HTTP-API ondersteunt eenvoudige aanpassingen en keuzemogelijkheden van clientplatforms voor PhoneGap-apps, native apps en andere integraties en mashups. Bovendien staat HTTP API een communautaire plaats toe om als dienst zonder een cliënt te lopen, zodat de kadercomponenten in om het even welke webpage kunnen worden geïntegreerd die op om het even welke technologie wordt voortgebouwd.

### HTTP API - GET {#http-api-get-requests}

Voor elke SocialComponent, verstrekt het kader een op HTTP-Gebaseerd API eindpunt. Het eindpunt wordt betreden door een verzoek van de GET naar het middel met &quot;.social.json&quot;selecteur + uitbreiding te verzenden. Met Sling wordt de aanvraag aan de `DefaultSocialGetServlet` overhandigd.

**`DefaultSocialGetServlet`**

1. Geeft de resource (resourceType) door aan `SocialComponentFactoryManager` en ontvangt een SocialComponentFactory die een `SocialComponent` kan selecteren die de resource vertegenwoordigt.

1. Roept de fabriek aan en ontvangt een `SocialComponent` die de bron en aanvraag kan verwerken.
1. Roept `SocialComponent` aan, die het verzoek verwerkt en een JSON-representatie van de resultaten retourneert.
1. Retourneert de JSON-reactie op de client.

**`GET Request`**

Een standaard GET servlet luistert naar .social.json verzoeken waaraan de SocialComponent met klantgerichte JSON antwoordt.

![&#x200B; scf-framework &#x200B;](assets/scf-framework.png)

### HTTP API - POST-aanvragen {#http-api-post-requests}

Naast de (Gelezen) verrichtingen van de GET, bepaalt het kader een eindpuntpatroon om andere verrichtingen op een component toe te laten, met inbegrip van Create, Update, en Schrapping. Deze eindpunten zijn HTTP-API&#39;s die invoer accepteren en reageren met een HTTP-statuscode of met een JSON-reactieobject.

Dit patroon van het kadereindpunt maakt de verrichtingen van de CUD verlengbaar, herbruikbaar, en testbaar.

**`POST Request`**

Er is een Sling POST:verrichting voor elke verrichting SocialComponent. De bedrijfslogica en onderhoudscode voor elke verrichting zijn verpakt in een OperationService die door HTTP API of van elders als dienst OSGi toegankelijk is. Hooks wordt geleverd ter ondersteuning van instelbare bewerkingsextensies voor acties voor en na acties.

![&#x200B; scf-post-verzoek &#x200B;](assets/scf-post-request.png)

### Storage Resource Provider (SRP) {#storage-resource-provider-srp}

Om over behandeling UGC te leren die in de [&#x200B; wordt opgeslagen opslag van de communautaire inhoud &#x200B;](working-with-srp.md), zie:

* [&#x200B; Overzicht van de Leverancier van het Middel van de Opslag &#x200B;](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [&#x200B; SRP en Hoofdzaak UGC &#x200B;](srp-and-ugc.md) - SRP API hulpprogrammamethodes en voorbeelden.
* [&#x200B; die tot UGC met SRP &#x200B;](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.

### Aanpassingen op de server {#server-side-customizations}

Bezoek [&#x200B; server-Kant Aanpassingen &#x200B;](server-customize.md) voor informatie bij het aanpassen van de bedrijfslogica en het gedrag van een component van Gemeenschappen op server-kant.

## Handlebars JS Templating Language {#handlebars-js-templating-language}

Een van de merkbaardere wijzigingen in het nieuwe framework is het gebruik van de sjabloontaal `Handlebars JS` (HBS), een populaire open-source technologie voor rendering van servers en clients.

HBS-scripts zijn eenvoudig, zonder logica, kunnen op zowel de server als de client worden gecompileerd, zijn eenvoudig te bedekken en aan te passen en zijn op natuurlijke wijze gebonden aan de client-UX, omdat HBS renderen op de client ondersteunt.

Het kader verstrekt verscheidene [&#x200B; helpers Handlebars &#x200B;](handlebars-helpers.md) die wanneer het ontwikkelen van SocialComponents nuttig zijn.

Op de server, wanneer het Sling een verzoek van de GET verhelpt, identificeert het het manuscript dat wordt gebruikt om op het verzoek te antwoorden. Als het manuscript een malplaatje HBS (.hbs) is, zal het Sling het verzoek aan de Motor van Handlebars delegeren. De Motor Handlebars zal dan de SocialComponent van aangewezen SocialComponentFactory krijgen, een context bouwen, en de HTML teruggeven.

### Geen toegangsbeperking {#no-access-restriction}

Handlebars (HBS) malplaatjedossiers (.hbs) zijn analoog aan .jsp en .html malplaatjedossiers, behalve zij kunnen voor het teruggeven zowel in cliëntbrowser als op de server worden gebruikt. Daarom ontvangt een cliëntbrowser die om een cliënt-zijmalplaatje verzoekt een .hbs dossier van de server.

Dit vereist dat alle malplaatjes van HBS in de sling onderzoekspad (om het even welke .hbs dossiers onder /libs/ of /apps) door om het even welke gebruiker van auteur kunnen worden gehaald of publiceren.

De toegang van HTTP tot .hbs dossiers kan niet worden verboden.

### Een onderdeel van een Gemeenschappen toevoegen of opnemen {#add-or-include-a-communities-component}

De meeste componenten van Gemeenschappen moeten *worden toegevoegd* als het Verzenden adresseerbare middel. Een uitgezochte paar componenten van Gemeenschappen kan ** in een malplaatje als niet bestaand middel &lbrace;worden omvat om voor dynamische opneming en aanpassing van de plaats toe te staan waarbij om gebruiker-geproduceerde inhoud (UGC) te schrijven.

In één van beide geval, moeten de van de component [&#x200B; vereiste cliëntbibliotheken &#x200B;](clientlibs.md) ook aanwezig zijn.

**voeg een Component** toe

Het toevoegen van een component verwijst naar het proces om een geval van een middel (component) toe te voegen, zoals wanneer gesleept van componentenbrowser (sidekick) op een pagina in auteur uitgeeft wijze.

Het resultaat is een JCR-onderliggend knooppunt onder een pari-knooppunt, dat adresseerbaar is.

**omvat een Component**

Het omvatten van een component verwijst naar het proces om een verwijzing naar een [&#x200B; &quot;niet bestaand&quot;middel &#x200B;](srp.md#for-non-existing-resources-ners) (geen knoop JCR) binnen het malplaatje toe te voegen, zoals het gebruiken van een scripting taal.

Vanaf Adobe Experience Manager (AEM) 6.1, wanneer een component dynamisch inbegrepen in plaats van toegevoegd is, is het mogelijk om de eigenschappen van de component op auteur *ontwerp* wijze uit te geven.

Slechts een paar AEM Communities-componenten kunnen dynamisch worden opgenomen. Het zijn:

* [Opmerkingen](essentials-comments.md)
* [Classificatie](rating-basics.md)
* [Revisies](reviews-basics.md)
* [Stemming](essentials-voting.md)

De [&#x200B; Communautaire Gids van Componenten &#x200B;](components-guide.md) staat includible componenten toe om van het worden van een knevel te worden voorzien van worden toegevoegd aan inbegrepen.

**wanneer het gebruiken van de Templating taal van Handels**, wordt het niet bestaande middel inbegrepen gebruikend [&#x200B; omvat helper &#x200B;](handlebars-helpers.md#include) door zijn resourceType te specificeren:

`{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}`

**wanneer het gebruiken van JSP**, is een middel inbegrepen gebruikend de markering [&#x200B; cq:omvat &#x200B;](../../help/sites-developing/taglib.md#lt-cq-include):

```
<cq:include path="votes"
 resourceType="social/tally/components/voting" />
```

>[!NOTE]
>
>Om een component aan een pagina dynamisch toe te voegen, in plaats van het toe te voegen of het op te nemen in een malplaatje, zie [&#128279;](sideloading.md) het Schuiven van de Component 0&rbrace;.

### Handlebars Helpers {#handlebars-helpers}

Zie [&#x200B; SCF de Helpers van Handlebars &#x200B;](handlebars-helpers.md) voor een lijst en een beschrijving van douanhelpers beschikbaar in SCF.

## Client-Side Framework {#client-side-framework}

### Model-View JavaScript Framework {#model-view-javascript-framework}

Het kader omvat een uitbreiding van [&#x200B; Backbone.js &#x200B;](https://backbonejs.org/), een model-mening kader van JavaScript, om ontwikkeling van rijke, interactieve componenten te vergemakkelijken. De objectgeoriënteerde aard ondersteunt een uitbreidbaar/herbruikbaar framework. De communicatie tussen client en server wordt vereenvoudigd met de HTTP API.

Het framework gebruikt server-side Handlebars-sjablonen om de componenten voor de client te renderen. De modellen zijn gebaseerd op de JSON-reacties die door de HTTP-API zijn gegenereerd. De meningen binden zich aan HTML die door de malplaatjes Handlebars wordt geproduceerd en verstrekken interactiviteit.

### CSS-conventies {#css-conventions}

Hieronder vindt u aanbevolen conventies voor het definiëren en gebruiken van CSS-klassen:

* Gebruik duidelijk benoemde CSS-klassenselectienamen en vermijd generieke namen zoals &#39;heading&#39; en &#39;image&#39;.
* Definieer specifieke klassenselectorstijlen, zodat de CSS-stijlpagina&#39;s goed werken met andere elementen en stijlen op de pagina. Bijvoorbeeld: `.social-forum .topic-list .li { color: blue; }`
* CSS-klassen voor opmaak gescheiden houden van CSS-klassen voor UX aangestuurd door JavaScript.

### Aanpassingen op de client {#client-side-customizations}

Voor het aanpassen van de verschijning en het gedrag van een component van Gemeenschappen op de cliënt-kant, verwijzing [&#x200B; Cliënt-Kant Aanpassingen &#x200B;](client-customize.md), die informatie over omvatten:

* [Bedekkingen](client-customize.md#overlays)
* [Extensies](client-customize.md#extensions)
* [HTML Markup](client-customize.md#htmlmarkup)
* [CSS schuintrekken](client-customize.md#skinning-css)
* [JavaScript uitbreiden](client-customize.md#extending-javascript)
* [Clientlibs voor SCF](client-customize.md#clientlibs-for-scf)

## Essentiële functies en componenten {#feature-and-component-essentials}

De essentiële informatie voor ontwikkelaars wordt beschreven in de [&#x200B; sectie van de Hoofdzaak van de Eigenschap en van de Component &#x200B;](essentials.md).

De extra ontwikkelaarinformatie kan in de [&#x200B; sectie van de Richtlijnen van de Codering &#x200B;](code-guide.md) worden gevonden.

## Problemen oplossen {#troubleshooting}

De gemeenschappelijke zorgen en bekende kwesties worden beschreven in de [&#x200B; 1&rbrace; sectie van het Oplossen van problemen.](troubleshooting.md)
