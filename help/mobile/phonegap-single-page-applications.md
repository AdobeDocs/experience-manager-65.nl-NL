---
title: Toepassingen voor één pagina
description: Volg deze pagina om meer te weten te komen over toepassingen die uit één pagina bestaan, dat wil zeggen dat u een toepassing kunt maken die dezelfde prestaties levert als een toepassing voor desktops of mobiele apparaten.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: daf7bf39-a105-46eb-ab7b-1c59484949e2
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# Toepassingen voor één pagina{#single-page-applications}

{{ue-over-mobile}}

[&#x200B; Toepassingen van één pagina &#x200B;](https://en.wikipedia.org/wiki/Single-page_application) (SPA) hebben kritieke massa bereikt, wijd beschouwd als het meest efficiënte patroon voor de bouw van naadloze ervaringen met Webtechnologie. Door een SPA te volgen kunt u een toepassing maken die dezelfde prestaties levert als een bureaubladtoepassing of mobiele toepassing, maar die een groot aantal apparaatplatforms en formulierfactoren bereikt vanwege de basis in open webstandaarden.

Over het algemeen, SPA lijken krachtiger dan traditionele op pagina-gebaseerde websites omdat zij typisch een volledige pagina van de HTML **slechts eenmaal** (met inbegrip van CSS, JS, en het steunen doopvontinhoud) laden, en dan slechts precies laden wat noodzakelijk is telkens als een verandering van staat in app voorkomt. Wat nodig is voor deze verandering van staat kan variëren gebaseerd op de gekozen reeks technologieën, maar omvat typisch één enkel fragment van HTML om de bestaande &quot;mening&quot;te vervangen, en de uitvoering van een blok van code JS om de nieuwe mening omhoog te telegraferen en om het even welke cliënt-zijmalplaatje uit te voeren die noodzakelijk kan zijn. De snelheid van deze statuswijziging kan zelfs nog verder worden verbeterd door mechanismen voor het in cache plaatsen van sjablonen te ondersteunen, of zelfs offline toegang tot sjablooninhoud als Adobe PhoneGap wordt gebruikt.

AEM 6.1 ondersteunt de bouw en het beheer van SPA via AEM Apps. Dit artikel verstrekt een inleiding aan de concepten achter de SPA en hoe zij [&#x200B; AngularJS &#x200B;](https://angularjs.org/) gebruiken om uw merk aan App Store en Google Play te brengen.

## SPA in AEM apps {#spa-in-aem-apps}

Met het toepassingsframework voor één pagina in AEM Apps kunt u de hoge prestaties van een AngularJS-app verhogen en tegelijkertijd auteurs (of ander niet-technisch personeel) de mogelijkheid bieden om de inhoud van de app te maken en te beheren via de voor aanrakingen geoptimaliseerde omgeving voor slepen en neerzetten die traditioneel is gereserveerd voor het beheer van websites. Hebt u al een site gebouwd met AEM? U merkt dat het opnieuw gebruiken van uw inhoud, componenten, werkschema&#39;s, activa, en toestemmingen met AEM Apps gemakkelijk is.

## AngularJS Application Module {#angularjs-application-module}

AEM Apps behandelt veel van de configuratie AngularJS voor u, met inbegrip van het samenstellen van de top-level module van uw app. Deze module heeft standaard de naam &#39;AEMAngularApp&#39; en het script dat verantwoordelijk is voor het genereren van de module is te vinden (en te bedekken) op /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp.

Een deel van de initialisatie van uw app bestaat uit het opgeven van welke AngularJS-modules de toepassing afhankelijk is. De lijst met modules die door uw app worden gebruikt, is opgegeven door een script op /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp en kan worden bedekt door de paginacomponent van uw eigen apps om extra AngularJS-modules in te schakelen die uw app nodig heeft. Als voorbeeld, vergelijk het bovengenoemde manuscript met de implementatie van de Geometrixx (die in /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp wordt gevestigd).

Om navigatie tussen de verschillende staten in uw app te steunen, herhaalt het angular-app-module manuscript door alle afstammende pagina&#39;s van uw top-level app pagina om een reeks &quot;routes&quot;te produceren en elke weg op de dienst van $routeProvider van Angular te vormen. Voor een voorbeeld van hoe dit in praktijk kijkt, bekijk het angular-app-module manuscript door de Geometrixx Outdoors wordt geproduceerd app steekproef: (de verbinding vereist een lokale instantie) [&#x200B; http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js &#x200B;](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

Door in te schrijven naar de gegenereerde AEMAngularApp, ziet u een reeks routes die als volgt worden opgegeven:

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

Het bovenstaande voorbeeld illustreert met name een voorbeeld van het doorgeven van een parameter als onderdeel van het pad. In dit voorbeeld wordt aangegeven dat wanneer een pad wordt aangevraagd dat voldoet aan het opgegeven patroon (/content/phonegap/geometrixx-outdoor/en/home/products/:id), dit moet worden afgehandeld door de sjabloon home/products.template.html en de controller &#39;contentphonegapgeometrixxoutdoorsenhomeproducts&#39; moet gebruiken.

Het malplaatje te laden wanneer deze route wordt gevraagd wordt gespecificeerd door het templateUrl bezit. Deze sjabloon bevat de HTML van AEM componenten die op de pagina zijn opgenomen, en alle AngularJS-instructies die nodig zijn voor het opbedraden van de clientzijde van de toepassing. Kijk bijvoorbeeld naar regel 45 van template Sjabloon.jsp (/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp) van de swipe-carrousel voor een voorbeeld van een AngularJS-richtlijn in een Geometrixx-component.

## Paginacontrollers {#page-controllers}

In de eigen woorden van Angulars, &quot;is een Controlemechanisme een de aannemersfunctie van JavaScript die wordt gebruikt om het Toepassingsgebied van de Angular te verhogen.&quot; ([&#x200B; bron &#x200B;](https://docs.angularjs.org/guide/controller)) Elke pagina in een AEM App wordt automatisch getelegrafeerd tot een controlemechanisme dat door om het even welk controlemechanisme kan worden uitgebreid dat a `frameworkType` van `angular` specificeert. Bekijk de ng-text component als voorbeeld (/libs/mobileapps/components/angular/ng-text), met inbegrip van de cq:template knoop die ervoor zorgt telkens als deze component aan een pagina wordt toegevoegd het dit belangrijke bezit omvat.

Voor een complexer controllervoorbeeld opent u het script ng-template-page controller.jsp (op /apps/geometrixx-outdoor-app/components/angular/ng-template-page). Van bijzonder belang is de JavaScript-code die wordt gegenereerd wanneer deze wordt uitgevoerd, die als volgt wordt weergegeven:

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

In het bovenstaande voorbeeld wordt de parameter van de `$routeParams` -service genomen en vervolgens in de mappenstructuur gemasseerd waarin de JSON-gegevens zijn opgeslagen. Door SKU `id` op deze manier te behandelen, kunt u één enkel malplaatje van het Product leveren dat de productgegevens voor potentieel duizenden verschillende producten kan teruggeven. Dit is een veel scalable model dat een individuele route voor elk punt in (potentieel) massaal productgegevensbestand vereist.

Er zijn hier ook twee componenten aan het werk: ng-product vergroot het werkingsgebied met de gegevens het uit bovengenoemde `$http` vraag haalt. Deze pagina bevat ook een ng-afbeelding die het bereik vergroot met de waarde die het ophaalt uit het antwoord. Dankzij de `$http` -service van de Angular wacht elke component geduldig tot het verzoek is afgehandeld en de gemaakte belofte is nagekomen.

## De volgende stappen {#the-next-steps}

Zodra u over de Enige Toepassingen van de Pagina hebt geleerd, zie [&#x200B; Ontwikkelend Toepassingen met CLI PhoneGap &#x200B;](/help/mobile/phonegap-apps-pg-cli.md).
