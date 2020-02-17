---
title: Toepassingen voor één pagina
seo-title: Toepassingen voor één pagina
description: Volg deze pagina om meer te weten te komen over toepassingen die uit één pagina bestaan, dat wil zeggen dat u een toepassing kunt maken die dezelfde prestaties levert als een toepassing voor desktops of mobiele apparaten.
seo-description: Volg deze pagina om meer te weten te komen over toepassingen die uit één pagina bestaan, dat wil zeggen dat u een toepassing kunt maken die dezelfde prestaties levert als een toepassing voor desktops of mobiele apparaten.
uuid: d1865e79-6e7c-4149-95c0-556e61478b01
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: a5b5e40e-2457-45fe-9632-baf5008fe8bf
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Toepassingen voor één pagina{#single-page-applications}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

[Toepassingen](https://en.wikipedia.org/wiki/Single-page_application) van één pagina (SPA) hebben kritieke massa bereikt, die algemeen als het meest efficiënte patroon wordt beschouwd om naadloze ervaringen met Webtechnologie te bouwen. Door een patroon van het KUUROORD te volgen, kunt u een toepassing tot stand brengen die identiek aan een Desktop of een mobiele toepassing presteert, maar een veelheid van apparatenplatforms en vormfactoren wegens zijn stichting in open Webnormen bereikt.

In het algemeen, lijken SPAs krachtiger dan traditionele op pagina-gebaseerde websites omdat zij typisch een volledige HTML- pagina **slechts eenmaal** (met inbegrip van CSS, JS, en het steunen doopvontinhoud) laden, en dan slechts precies laden wat noodzakelijk is telkens als een verandering van staat in app voorkomt. Wat nodig is voor deze verandering van staat kan variëren gebaseerd op de gekozen reeks technologieën, maar omvat typisch één enkel fragment van HTML om de bestaande &quot;mening&quot;te vervangen, en de uitvoering van een blok van code JS om de nieuwe mening omhoog te telegraferen en om het even welke cliënt zijmalplaatje uit te voeren die noodzakelijk kan zijn. De snelheid van deze statuswijziging kan nog verder worden verbeterd door mechanismen voor het in cache plaatsen van sjablonen te ondersteunen, of zelfs offline toegang tot sjablooninhoud als Adobe PhoneGap wordt gebruikt.

AEM 6.1 steunt de bouw en het beheer van SPAs via AEM Apps. In dit artikel wordt een inleiding gegeven op de concepten achter de SPA en op de manier waarop [AngularJS](https://angularjs.org/) uw merk kan gebruiken om de App Store en Google Play onder de aandacht te brengen.

## SPA in AEM-apps {#spa-in-aem-apps}

Met het toepassingsframework voor één pagina in AEM-apps kunnen auteurs (of ander niet-technisch personeel) de inhoud van de app maken en beheren via de voor aanrakingen geoptimaliseerde omgeving voor slepen en neerzetten die traditioneel is gereserveerd voor het beheer van websites. Hebt u al een site gebouwd met AEM? U zult merken dat het opnieuw gebruiken van uw inhoud, componenten, werkschema&#39;s, activa, en toestemmingen met AEM Apps gemakkelijk is.

## AngularJS Application Module {#angularjs-application-module}

AEM Apps behandelt veel van de configuratie AngularJS voor u, met inbegrip van het samenstellen van de top-level module van uw app. Deze module heeft standaard de naam &#39;AEMAngularApp&#39; en het script dat verantwoordelijk is voor de generatie ervan is te vinden (en te bedekken) op /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp.

Een deel van de initialisatie van uw app bestaat uit het opgeven van welke AngularJS-modules de toepassing afhankelijk is. De lijst met modules die door uw app worden gebruikt, is opgegeven door een script op /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp en kan worden bedekt door de paginacomponent van uw eigen apps om extra AngularJS-modules in te schakelen die uw app nodig heeft. Als voorbeeld, vergelijk het bovengenoemde manuscript met de implementatie Geometrixx (die in /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp wordt gevestigd).

Om navigatie tussen de verschillende staten in uw app te steunen, herhaalt het hoekige-app-module manuscript door alle dalende pagina&#39;s van uw hoogste niveau app pagina om een reeks &quot;routes&quot;te produceren en elk weg op de dienst te vormen $routeProvider van Angular. Bekijk voor een voorbeeld van hoe dit er in de praktijk uitziet, het hoekige-app-module-script dat is gegenereerd door het voorbeeld van de Geometrixx-app Buiten: (voor de koppeling is een lokale instantie vereist) [http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

Door in te schrijven naar de gegenereerde AEMAngularApp, ziet u een reeks routes die als volgt worden opgegeven:

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

Het bovenstaande voorbeeld illustreert met name een voorbeeld van het doorgeven van een parameter als onderdeel van het pad. In dit voorbeeld geven we aan dat wanneer een pad wordt aangevraagd dat voldoet aan het opgegeven patroon (/content/phonegap/geometrixx-outdoor/en/home/products/:id), het moet worden afgehandeld door de sjabloon home/products.template.html en de controller &#39;contentphonegapgeometrixxoutdoorsenhomeproducts&#39; moet gebruiken.

Het malplaatje te laden wanneer deze route wordt gevraagd wordt gespecificeerd door het templateUrl bezit. Deze sjabloon bevat de HTML van AEM-componenten die op de pagina zijn opgenomen, en alle AngularJS-instructies die nodig zijn voor de bedrading van de clientzijde van de toepassing. Neem bijvoorbeeld een voorbeeld van een AngularJS-instructie in een Geometrixx-component en bekijk lijn 45 van template.jsp (/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp) van de veegbeweging-carrousel.

## Paginacontrollers {#page-controllers}

In de eigen woorden van Angular is &quot;een controller een JavaScript-constructorfunctie die wordt gebruikt om het hoekbereik te vergroten.&quot; ([bron](https://docs.angularjs.org/guide/controller)) Elke pagina in een AEM App wordt automatisch getelegrafeerd tot een controlemechanisme dat door om het even welk controlemechanisme kan worden uitgebreid dat een `frameworkType` van `angular`specificeert. Bekijk de ng-text component als voorbeeld (/libs/mobileapps/components/angular/ng-text), met inbegrip van de cq:template knoop die ervoor zorgt telkens als deze component aan een pagina wordt toegevoegd het dit belangrijke bezit omvat.

Voor een complexer controllervoorbeeld opent u het script ng-template-page controller.jsp (dat zich bevindt op /apps/geometrixx-outdoor-app/components/angular/ng-template-page). Van bijzonder belang is de javascript-code die wordt gegenereerd wanneer deze wordt uitgevoerd, die als volgt wordt weergegeven:

```xml
// Controller for page 'products'
.controller('contentphonegapgeometrixxoutdoorsenhomeproducts', ['$scope', '$http', '$routeParams',
    function($scope, $http, $routeParams) {
        var sku = $routeParams.id;
        var productPath = '/' + sku.substring(0, 2) + '/' + sku.substring(0, 4) + '/' + sku;
        var data = $http.get('home/products' + productPath + '.angular.json' + cacheKiller);

        /* ng-product component controller (path: content-par/ng-product) */
        data.then(function(response) {
            $scope.contentparngproduct = response.data["content-par/ng-product"].items;
        });

        /* ng-image component controller (path: content-par/ng-product/ng-image) */
        data.then(function(response) {
            $scope.contentparngproductngimage = response.data["content-par/ng-product/ng-image"].items;
        });
    }
])
```

In het bovenstaande voorbeeld, zult u merken dat wij een parameter van de `$routeParams` dienst nemen en dan het massaging in de folderstructuur dat onze gegevens JSON in wordt opgeslagen. Door de sku op deze manier te behandelen, kunnen wij één enkel malplaatje van het Product leveren dat de productgegevens voor potentieel duizenden verschillende producten kan teruggeven. `id` Dit is een veel scalable model dat een individuele route voor elk punt in (potentieel) massaal productgegevensbestand vereist.

Er zijn ook twee onderdelen aan het werk: ng-product vergroot het toepassingsgebied met de gegevens die het uit bovengenoemde `$http` oproep haalt. Deze pagina bevat ook een ng-afbeelding die het bereik vergroot met de waarde die het ophaalt uit het antwoord. Op grond van de `$http` dienst van Angular zal elke component geduldig wachten tot het verzoek wordt gebeëindigd en de belofte het wordt gecreeerd wordt vervuld.

## De volgende stappen {#the-next-steps}

Zie Apps [ontwikkelen met PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md)als u eenmaal ervaring hebt met de toepassingen voor één pagina.
