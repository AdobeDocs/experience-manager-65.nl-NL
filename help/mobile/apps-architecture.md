---
title: Paginasjablonen voor mobiele apps
seo-title: Paginasjablonen voor mobiele apps
description: Volg deze pagina voor meer informatie over paginasjablonen. De paginacomponenten die u voor uw app maakt, zijn gebaseerd op de component /libs/mobileapps/components/angular/ng-page.
seo-description: Volg deze pagina voor meer informatie over paginasjablonen. De paginacomponenten die u voor uw app maakt, zijn gebaseerd op de component /libs/mobileapps/components/angular/ng-page.
uuid: c53901c9-5974-4c6b-ac61-1c094a93c9d6
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: cfc7ad16-965e-4075-bc4d-5630abeaba55
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Paginasjablonen voor mobiele apps {#page-templates-for-mobile-apps}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

## Paginasjablonen voor mobiele apps {#page-templates-for-mobile-apps-1}

De paginacomponenten die u voor uw app maakt, zijn gebaseerd op de component /libs/mobileapps/components/angular/ng-page ([geopend in CRXDE Lite op een lokale server](http://localhost:4502/crx/de/index.jsp#/libs/mobileapps/components/angular/ng-page)). Deze component bevat de volgende JSP manuscripten die uw component of erft of met voeten treedt:

* ng-page.jsp
* head.jsp
* body.jsp
* angular-app-module.js.jsp
* angular-route-fragment.js.jsp
* angular-app-controllers.js.jsp
* controller.js.jsp
* template.jsp
* angular-module-list.js.jsp
* header.jsp
* footer.jsp
* js_clientlibs.jsp
* css_clientlibs.jsp

### ng-page.jsp {#ng-page-jsp}

Bepaalt de naam van de toepassing die het `applicationName` bezit gebruikt, en stelt het via pageContext bloot.

Omvat head.jsp en body.jsp.

### head.jsp {#head-jsp}

Schrijft het `<head>` element van de app-pagina.

Als u de meta-eigenschap viewport van de app wilt overschrijven, is dit het bestand dat u overschrijft.

De app bevat het css-gedeelte van de clientbibliotheken in de kop, terwijl de JS is opgenomen in het afsluitende &lt;- `body>` element. Dit wordt onder de best practices verstaan.

### body.jsp {#body-jsp}

De hoofdtekst van een hoekpagina wordt anders weergegeven, afhankelijk van het feit of wcmMode wordt gedetecteerd (!= WCMMode.DISABLED) om te bepalen of de pagina voor creatie of als gepubliceerde pagina wordt geopend.

**Auteursmodus**

In de auteurmodus wordt elke afzonderlijke pagina afzonderlijk weergegeven. Hoekig handelt het verpletteren tussen pagina&#39;s niet, noch een ng-mening die wordt gebruikt om een gedeeltelijk malplaatje te laden dat de componenten van de pagina bevat. In plaats daarvan wordt de inhoud van de paginasjabloon (template.jsp) via de `cq:include` tag aan de serverzijde toegevoegd.

Deze strategie maakt de auteur-functies mogelijk (zoals het toevoegen en bewerken van componenten in het alineasysteem, Sidetrap, ontwerpmodus, enz.) om zonder wijzigingen te werken. Pagina&#39;s die afhankelijk zijn van rendering op de client, zoals de pagina&#39;s voor apps, functioneren niet goed in de AEM-auteurmodus.

Merk op dat template.jsp omvat in een `div` element verpakt is dat de `ng-controller` richtlijn bevat. Met deze structuur kunt u de DOM-inhoud koppelen aan de controller. Daarom, hoewel de pagina&#39;s die zich op de cliëntkant teruggeven ontbreken, individuele componenten die dit doen goed werken (zie sectie over Componenten hieronder).

```xml
<div ng-controller="<c:out value="${controllerNameStripped}"/>">
      <cq:include script="template.jsp"/>
</div>
```

**Publicatiemodus**

In de publicatiemodus (bijvoorbeeld wanneer de app wordt geëxporteerd met Content Sync) worden alle pagina&#39;s een app van één pagina (SPA). (Om over SPAs te leren, gebruik de Hoektutorial, specifiek [https://docs.angularjs.org/tutorial/step_07](https://docs.angularjs.org/tutorial/step_07).)

Er is slechts één HTML-pagina in een SPA (een pagina die het `<html>` element bevat). Deze pagina wordt de &#39;lay-outsjabloon&#39; genoemd. In hoekige termen is het &quot;...een sjabloon die veel wordt gebruikt voor alle weergaven in onze toepassing.&quot; Beschouw deze pagina als de &#39;toepassingspagina op het hoogste niveau&#39;. Volgens conventie is de toepassingspagina op het hoogste niveau het `cq:Page` knooppunt van uw toepassing dat zich het dichtst bij de hoofdmap bevindt (en geen omleiding is).

Aangezien de werkelijke URI van uw app niet verandert in de publicatiemodus, moeten verwijzingen naar externe elementen van deze pagina gebruikmaken van relatieve paden. Daarom is er een speciale afbeeldingscomponent die rekening houdt met deze pagina op het hoogste niveau wanneer u afbeeldingen rendert voor exporteren.

Als SPA, produceert deze pagina van het lay-outmalplaatje eenvoudig een div element met een ng-meningsrichtlijn.

```xml
 <div ng-view ng-class="transition"></div>
```

De Hoekroutedienst gebruikt dit element om de inhoud van elke pagina in app, met inbegrip van de authorable inhoud van de huidige pagina (in template.jsp) te tonen.

Het bestand body.jsp bevat header.jsp en footer.jsp, die leeg zijn. Als u statische inhoud op elke pagina wilt verstrekken, kunt u deze manuscripten in uw app met voeten treden.

Tot slot worden javascript-clientlibs onder aan het element &lt;body> opgenomen, inclusief twee speciale JS-bestanden die op de server worden gegenereerd: *&lt;page name>*.angular-app-module.js and *&lt;page name>*.angular-app-controllers.js.

### angular-app-module.js.jsp {#angular-app-module-js-jsp}

Met dit script wordt de hoekmodule van de toepassing gedefinieerd. De output van dit manuscript is verbonden met de prijsverhoging die de rest van de component van het malplaatje via het `html` element in ng-page.jsp produceert, die het volgende attribuut bevat:

```xml
ng-app="<c:out value='${applicationName}'/>"
```

Dit kenmerk geeft aan hoekig te zijn dat de inhoud van dit DOM-element moet worden gekoppeld aan de volgende module. In deze module worden de weergaven (in AEM zijn dit cq:Page-bronnen) gekoppeld aan de overeenkomstige besturingselementen.

Deze module bepaalt ook een top-level controlemechanisme genoemd `AppController` die de `wcmMode` variabele aan het werkingsgebied blootstelt, en vormt URI waarvan om de updatelading van de Synchronisatie van de Inhoud te halen.

Ten slotte, herhaalt deze module door elke afstammende pagina (met inbegrip van zelf) en geeft de inhoud van het routefragment van elke pagina (via de hoek-route-fragment.js selecteur &amp; uitbreiding) terug, met inbegrip van het als config ingang aan Angular \$routeProvider. Met andere woorden, de \$routeProvider vertelt de toepassing welke inhoud moet worden teruggegeven wanneer een bepaald pad wordt gevraagd.

### angular-route-fragment.js.jsp {#angular-route-fragment-js-jsp}

Met dit script wordt een JavaScript-fragment gegenereerd dat de volgende vorm moet hebben:

```
.when('/<path>', {
    templateUrl: '<path to template>',
    controller: '<controller name>'
})
```

Deze code wijst aan $routeProvider (die in angular-app-module.js.jsp wordt bepaald) erop dat &quot;/&lt;path>&quot;door het middel bij moet worden behandeld, `templateUrl`en getelegrafeerd door `controller` (die wij aan volgende zullen krijgen).

Indien nodig, kunt u dit manuscript met voeten treden om complexere wegen, met inbegrip van die met variabelen te behandelen. Een voorbeeld van dit kan in het /apps/geometrixx-outdoors-app/components/angular/ng-template-page/angular-route-fragment.js.jsp manuscript worden gezien dat met AEM wordt geïnstalleerd:

```xml
// note the :id suffix on the path
.when('<c:out value="${resource.path}"/>/:id', {
    templateUrl: '<c:out value="${relativeResourcePath}"/>.template.html',
    controller: '<c:out value="${controllerNameStripped}"/>'
})
```

### angular-app-controllers.js.jsp {#angular-app-controllers-js-jsp}

In Hoekig, telegraferen de Controllers variabelen in \$scope, die hen aan de mening blootstellen. Het angular-app-controllers.js.jsp-script volgt het patroon dat wordt geïllustreerd door angular-app-module.js.jsp in die zin dat het elke afstammende pagina (inclusief zichzelf) doorloopt en het controllerfragment uitvoert dat elke pagina definieert (via controller.js.jsp). De module die wordt gedefinieerd, wordt aangeroepen `cqAppControllers` en moet worden vermeld als een afhankelijkheid van de app-module op het hoogste niveau, zodat de paginacontroles beschikbaar worden gemaakt.

### controller.js.jsp {#controller-js-jsp}

Met het controller.js.jsp-script wordt het controllerfragment voor elke pagina gegenereerd. Dit controllerfragment heeft de volgende vorm:

```
.controller('<c:out value="${controllerNameStripped}"/>', ['$scope', '$http',
    function($scope, $http) {
        var data = $http.get('<c:out value="${relativeResourcePath}"/>.angular.json' + cacheKiller);

        // component fragments which consume the contents of `data` go here
    }
])
```

Merk op dat de `data` variabele de belofte wordt toegewezen die door de Hoekmethode wordt teruggekeerd `$http.get` . Elke component die in deze pagina is opgenomen, kan desgewenst .json-inhoud (via het script angular.json.jsp) beschikbaar maken en op de inhoud van dit verzoek reageren wanneer dit wordt opgelost. Het verzoek is zeer snel op mobiele apparaten omdat het eenvoudig tot het dossiersysteem toegang heeft.

Als een component op deze manier deel moet uitmaken van de controller, moet de component /libs/mobileapps/components/angular/ng-component worden uitgebreid en de `frameworkType: angular` eigenschap worden opgenomen.

### template.jsp {#template-jsp}

Eerst geïntroduceerd in de body.jsp sectie, template.jsp bevat eenvoudig parsys van de pagina. In publicatiemodus, wordt deze inhoud van verwijzingen voorzien direct (bij &lt;page-path>.template.html) en geladen in het KUUROORD via templateUrl die op \$routeProvider wordt gevormd.

Parsys in dit manuscript kan worden gevormd om het even welk type van component goed te keuren. Nochtans, moet de zorg worden gegeven wanneer het behandelen van componenten die voor een traditionele website (in tegenstelling tot een KUUROORD) worden gebouwd. De component voor de basisafbeelding werkt bijvoorbeeld alleen correct op de toepassingspagina op het hoogste niveau, omdat deze niet is ontworpen om te verwijzen naar elementen die zich in een app bevinden.

### angular-module-list.js.jsp {#angular-module-list-js-jsp}

Met dit script worden gewoon de hoekafhankelijkheden van de app-module op het hoogste niveau uitgevoerd. Er wordt naar verwezen door angular-app-module.js.jsp.

### header.jsp {#header-jsp}

Een script waarmee statische inhoud boven aan de app wordt geplaatst. Deze inhoud wordt opgenomen door de pagina op het hoogste niveau, buiten het bereik van de niet-weergave.

### footer.jsp {#footer-jsp}

Een script waarmee statische inhoud onder aan de app wordt geplaatst. Deze inhoud wordt opgenomen door de pagina op het hoogste niveau, buiten het bereik van de niet-weergave.

### js_clientlibs.jsp {#js-clientlibs-jsp}

Hef dit script op om uw JavaScript-clientlibs op te nemen.

### css_clientlibs.jsp {#css-clientlibs-jsp}

Hef dit script op om uw CSS-clientlibs op te nemen.

## App-componenten {#app-components}

Toepassingscomponenten moeten niet alleen werken op een AEM-instantie (publiceren of auteur), maar ook wanneer de toepassingsinhoud via Content Sync naar het bestandssysteem wordt geëxporteerd. Het onderdeel moet daarom de volgende kenmerken bevatten:

* Er moet relatief worden verwezen naar alle elementen, sjablonen en scripts in een PhoneGap-toepassing.
* De afhandeling van koppelingen verschilt als de AEM-instantie werkt in de auteur- of publicatiemodus.

### Relatieve elementen {#relative-assets}

De URI van een willekeurig element in een PhoneGap-toepassing verschilt niet alleen per platform, maar is uniek bij elke installatie van de app. Let bijvoorbeeld op de volgende URI van een toepassing die wordt uitgevoerd in de iOS-simulator:

`file:///Users/userId/Library/Application%20Support/iPhone%20Simulator/7.0.3/Applications/24BA22ED-7D06-4330-B7EB-F6FC73251CA3/Library/files/www/content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en/home.html`

Noteer GUID &#39;24BA22ED-7D06-4330-B7EB-F6FC73251CA3&#39; in het pad.

Als ontwikkelaar van PhoneGap, wordt de inhoud die u betrokken bent gevestigd onder de folder www. Gebruik relatieve paden om toegang te krijgen tot de elementen van de app.

Uw PhoneGap-toepassing gebruikt het SPA-patroon (Single Page App), zodat de basis-URI (exclusief de hash) nooit verandert. Daarom **moet elk element, elke sjabloon of elk script waarnaar u verwijst relatief zijn ten opzichte van uw pagina op hoofdniveau.** De pagina op het hoogste niveau initialiseert de Hoekroutering en de controlemechanismen door middel van `*<name>*.angular-app-module.js` en `*<name>*.angular-app-controllers.js`. Deze pagina zou de dichtstbijzijnde pagina moeten zijn van de basis van de repository die *geen *extend een sling:redirect.

Er zijn verschillende helpermethoden beschikbaar voor het omgaan met relatieve paden:

* FrameworkContentExporterUtils.getTopLevelAppResource
* FrameworkContentExporterUtils.getRelativePathToRootLevel
* FrameworkContentExporterUtils.getPathToAsset

Als u voorbeelden van hun gebruik wilt bekijken, opent u de bron voor mobiele apps op de locatie /libs/mobileapps/components/angular.

### Koppelingen {#links}

Koppelingen moeten de functie gebruiken om alle WCM-modi te ondersteunen. `ng-click="go('/path')"` Deze functie hangt van de waarde van een werkingsgebiedvariabele af om de verbindingsactie correct te bepalen:

```xml
<c:choose><c:when test="${wcmMode}">
    <%-- WCMMode is enabled - page is being rendered in AEM --%>
    $scope.wcmMode = true;
</c:when><c:otherwise>
    <%-- WCMMode is disabled --%>
    $scope.wcmMode = false;
</c:otherwise></c:choose>
```

Wanneer `$scope.wcmMode == true` we elke navigatie-gebeurtenis op de gebruikelijke manier afhandelen, zodat het resultaat een wijziging is in het pad en/of paginagedeelte van de URL.

Alternatief, als `$scope.wcmMode == false`, elke navigatiegebeurtenis in een verandering in het knoeiboelgedeelte van URL resulteert die intern door de module ngRoute van Angular wordt opgelost.

### Details van componentscript {#component-script-details}

![chlimage_1-36](assets/chlimage_1-36.png)

#### ng-component.jsp {#ng-component-jsp}

Dit script geeft de inhoud van de component of een geschikte plaatsaanduiding weer wanneer de bewerkingsmodus wordt gedetecteerd.

#### template.jsp {#template-jsp-1}

Het script template.jsp rendert de opmaak van de component. Indien de component in kwestie wordt aangedreven door JSON-gegevens die uit AEM zijn geëxtraheerd (zoals &#39;ng-text&#39;: /libs/mobileapps/components/angular/ng-text/template.jsp), dan zal dit manuscript voor de bedrading van de prijsverhoging met gegevens verantwoordelijk zijn die door het de controlemechanismewerkingsgebied van de pagina worden blootgesteld.

Nochtans, vereisen de prestatiesvereisten soms dat geen cliënt zijtrilling (ook wel gegevensband genoemd) wordt uitgevoerd. In dit geval rendert u gewoon de markering van de component aan de serverzijde en is deze opgenomen in de inhoud van de paginasjabloon.

#### overhead.jsp {#overhead-jsp}

In componenten die door JSON-gegevens worden aangedreven (zoals &#39;ng-text&#39;: /libs/mobileapps/components/angular/ng-text), overhead.jsp kan worden gebruikt om alle Java-code uit template.jsp te verwijderen. Het wordt dan van template.jsp van verwijzingen voorzien en om het even welke variabelen die het op het verzoek blootstelt zijn beschikbaar voor gebruik. Deze strategie stimuleert de scheiding van logica van presentatie, en beperkt de hoeveelheid code die moet worden gekopieerd en worden gekleefd wanneer een nieuwe component uit bestaande wordt afgeleid.

#### controller.js.jsp {#controller-js-jsp-1}

Zoals beschreven in AEM-paginasjablonen, kan elke component een JavaScript-fragment uitvoeren om de JSON-inhoud te gebruiken die door de `data` belofte wordt vrijgegeven. Volgens de Hoekconventies mag een controller alleen worden gebruikt voor het toewijzen van variabelen aan het bereik.

#### angular.json.jsp {#angular-json-jsp}

Dit script is opgenomen als een fragment in het bestand &#39;&lt;page-name>.angular.json&#39; dat wordt geëxporteerd voor elke pagina die een niet-pagina uitbreidt. In dit bestand kan de componentontwikkelaar elke JSON-structuur onthullen die de component nodig heeft. In het voorbeeld &#39;ng-text&#39; bevat deze structuur eenvoudig de tekstinhoud van de component en een markering die aangeeft of de component RTF-tekst bevat.

De productcomponent van de Geometrixx-app voor buitenshuis is is een complexer voorbeeld (/apps/geometrixx-outdoor-app/components/angular/ng-product):

```xml
{
    "content-par/ng-product": {
        "items": [{
            "name": "Cajamara",
            "description": "Bike",
            "summaryHTML": "",
            "price": "$610.00",
            "SKU": "eqsmcj",
            "numberOfLikes": "0",
            "numberOfComments": "0"
        }]
    },
    "content-par/ng-product/ng-image": {
        "items": [{
            "hasContent": true,
            "imgSrc": "home/products/eq/eqsm/eqsmcj/jcr_content/content-par/ng-product/ng-image.img.jpg/1377771306985.jpg",
            "description": "",
            "alt": "Cajamara",
            "title": "Cajamara",
            "hasLink": false,
            "linkPath": "",
            "attributes": [{
                "attributeName": "class",
                "attributeValue": "cq-dd-image"
            }]
        }]
    }
}
```

## Inhoud van de CLI-middelen downloaden {#contents-of-the-cli-assets-download}

Download CLI-middelen van de toepassingsconsole om deze te optimaliseren voor een specifiek platform en maak de app vervolgens met de PhoneGap-API (Command Line Integration, CLI). De inhoud van het ZIP-bestand dat u opslaat naar het lokale bestandssysteem heeft de volgende structuur:

```xml
.cordova/
  |- hooks/
     |- after_prepare/
     |- before_platform_add/
     |- Other Hooks
plugins/
www/
  |- config.xml
  |- index.html
  |- res/
  |- etc/
  |- apps/
  |- content/
  |- package.json
  |- package-update.json
```

### .cordova {#cordova}

Dit is een verborgen map die u mogelijk niet ziet, afhankelijk van de huidige besturingssysteeminstellingen. U moet uw besturingssysteem zo configureren dat deze map zichtbaar is als u de daarin opgenomen appapuks wilt wijzigen.

#### .cordova/haken/ {#cordova-hooks}

Deze folder bevat de [haken](https://devgirl.org/2013/11/12/three-hooks-your-cordovaphonegap-project-needs/)CLI. De omslagen in de hooks folder bevatten knoop.js manuscripten die op nauwkeurige punten tijdens de bouwstijl worden uitgevoerd.

#### .cordova/haken/after-platform_add/ {#cordova-hooks-after-platform-add}

De folder after-platform_add bevat het `copy_AMS_Conifg.js` dossier. Met dit script wordt een configuratiebestand gekopieerd ter ondersteuning van de verzameling analyses van Adobe Mobile Services.

#### .cordova/haken/after-prepare/ {#cordova-hooks-after-prepare}

De map after-prepare bevat het `copy_resource_files.js` bestand. Met dit script wordt een aantal pictogrammen en welkomstschermen gekopieerd naar platformspecifieke locaties.

#### .cordova/hooks/before_platform_add/ {#cordova-hooks-before-platform-add}

De map before_platform_add bevat het `install_plugins.js` bestand. Dit script doorloopt een lijst met Cordova-insteekmodules voor insteekmodules, waarbij de id-id&#39;s die het detecteert, worden geïnstalleerd, is nog niet beschikbaar.

Deze strategie vereist niet dat u de stop- ins aan AEM bundelt en installeert telkens als het Maven `content-package:install` bevel wordt uitgevoerd. De alternatieve strategie om de bestanden in uw SCM-systeem te controleren, vereist herhaalde bundeling en installatie-activiteiten.

#### .cordova/haken/andere haken {#cordova-hooks-other-hooks}

Neem indien nodig andere haken op. De volgende haken zijn beschikbaar (zoals verstrekt door de Phonegap steekproef hello wereldapp):

* after_build
* before_build
* after_compile
* voor_compileren
* after_docs
* before_docs
* after_emulate
* before_emulate
* after_platform_add
* before_platform_add
* after_platform_ls
* before_platform_ls
* after_platform_rm
* before_platform_rm
* after_plugin_add
* before_plugin_add
* after_plugin_ls
* before_plugin_ls
* after_plugin_rm
* before_plugin_rm
* after_prepare
* before_prepare
* after_run
* before_run

#### platforms/ {#platforms}

Deze folder is leeg tot u het `phonegap run <platform>` bevel op het project uitvoert. Op dit moment kan dit `<platform>` ofwel `ios` ofwel `android`.

Nadat u de app voor een specifiek platform hebt gemaakt, wordt de bijbehorende map gemaakt en bevat deze de platformspecifieke toepassingscode.

#### plugins/ {#plugins}

De map plugins wordt gevuld met elke plug-in in het `.cordova/hooks/before_platform_add/install_plugins.js` bestand nadat u de `phonegap run <platform>` opdracht hebt uitgevoerd. De map is aanvankelijk leeg.

#### www/ {#www}

De map www bevat alle webinhoud (HTML-, JS- en CSS-bestanden) die de weergave en het gedrag van de app implementeert. Met uitzondering van de hieronder beschreven uitzonderingen, komt deze inhoud van AEM voort en wordt deze via Content Sync geëxporteerd naar de statische vorm ervan.

#### www/config.xml {#www-config-xml}

In de [PhoneGap-documentatie](https://docs.phonegap.com) wordt dit bestand een &#39;globaal configuratiebestand&#39; genoemd. Het bestand config.xml bevat veel app-eigenschappen, zoals de naam van de app, de &#39;voorkeuren&#39; van de app (bijvoorbeeld of een iOS-webweergave het schuiven toestaat) en insteekmodules die *alleen* door PhoneGap Build worden gebruikt.

Het bestand config.xml is een statisch bestand in AEM en wordt als zodanig geëxporteerd via Content Sync.

#### www/index.html {#www-index-html}

Het bestand index.html wordt omgeleid naar de startpagina van de app.

Het bestand config.xml bevat het `content` element:

`<content src="content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en.html" />`

In [de PhoneGap-documentatie](https://docs.phonegap.com)wordt dit element beschreven als &quot;Het optionele element &lt;content> definieert de startpagina van de app in de map met webelementen op het hoogste niveau. De standaardwaarde is index.html, die gewoonlijk in de top-level folder van een project www.&quot;verschijnt

De PhoneGap-build mislukt als er geen bestand index.html aanwezig is. Daarom is dit bestand opgenomen.

#### www/res {#www-res}

De map res bevat afbeeldingen en pictogrammen voor het welkomstscherm. Het `copy_resource_files.js` manuscript kopieert de dossiers aan hun platform-specifieke plaatsen tijdens de `after_prepare` bouwstijlfase.

#### www/etc {#www-etc}

Door overeenkomst, in AEM bevat de /etc knoop statische clientlib inhoud. De map etc bevat de topuntheek-, AngularJS- en Geometrixx ng-clientlibsall-bibliotheken.

#### www/apps {#www-apps}

De map apps bevat code die verwant is aan de splash-pagina. Het unieke kenmerk van de welkomstpagina van een AEM-app is dat de app wordt geïnitialiseerd zonder tussenkomst van de gebruiker. De clientlib-inhoud (zowel CSS als JS) van de app is daarom minimaal om de prestaties te maximaliseren.

#### www/content {#www-content}

De inhoudsmap bevat de rest van de webinhoud van de app. De inhoud kan de volgende bestanden bevatten, maar is niet beperkt tot:

* HTML-pagina-inhoud, die rechtstreeks in AEM is gemaakt
* Afbeeldingselementen die zijn gekoppeld aan AEM-componenten
* JavaScript-inhoud die door serverscripts wordt gegenereerd
* JSON-bestanden die pagina- of componentinhoud beschrijven

#### www/package.json {#www-package-json}

Het bestand package.json is een manifestbestand met de bestanden die een **volledige** download van Content Sync bevat. Dit bestand bevat ook het tijdstempel waarmee de payload van Content Sync is gegenereerd (`lastModified`). Deze eigenschap wordt gebruikt wanneer AEM gedeeltelijke updates van de app aanvraagt.

#### www/package-update.json {#www-package-update-json}

Als deze payload een download van de gehele app is, bevat dit manifest de exacte bestandenlijst als `package.json`.

Als deze laadbewerking echter een gedeeltelijke update is, `package-update.json` bevat deze alleen de bestanden die in deze specifieke laadbewerking zijn opgenomen.
