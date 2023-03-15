---
title: Toepassingen voor één pagina
seo-title: Single Page Applications
description: Volg deze pagina om meer te weten te komen over toepassingen die uit één pagina bestaan, dat wil zeggen dat u een toepassing kunt maken die dezelfde prestaties levert als een toepassing voor desktops of mobiele apparaten.
seo-description: Follow this page to learn about single page applications, that is, you can create an application that performs identically to a desktop or mobile application.
uuid: d1865e79-6e7c-4149-95c0-556e61478b01
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: a5b5e40e-2457-45fe-9632-baf5008fe8bf
exl-id: daf7bf39-a105-46eb-ab7b-1c59484949e2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Toepassingen voor één pagina{#single-page-applications}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

[Toepassingen met één pagina](https://en.wikipedia.org/wiki/Single-page_application) (SPA) een kritische massa hebben bereikt, die algemeen wordt beschouwd als het meest effectieve patroon voor het opbouwen van naadloze ervaringen met webtechnologie. Door een SPA te volgen kunt u een toepassing maken die dezelfde prestaties levert als een bureaubladtoepassing of mobiele toepassing, maar die een groot aantal apparaatplatforms en formulierfactoren bereikt vanwege de basis in open webstandaarden.

In het algemeen, SPA lijken krachtiger dan traditionele op pagina&#39;s gebaseerde websites omdat zij typisch een volledige pagina van de HTML laden **slechts één keer** (met inbegrip van CSS, JS, en het steunen doopvontinhoud), en laad dan slechts precies wat noodzakelijk is telkens als een verandering van staat in app voorkomt. Wat nodig is voor deze verandering van staat kan variëren gebaseerd op de gekozen reeks technologieën, maar omvat typisch één enkel fragment van HTML om de bestaande &quot;mening&quot;te vervangen, en de uitvoering van een blok van code JS om de nieuwe mening omhoog te telegraferen en om het even welke cliënt zijmalplaatje uit te voeren die noodzakelijk kan zijn. De snelheid van deze statuswijziging kan zelfs nog verder worden verbeterd door mechanismen voor het in cache plaatsen van sjablonen te ondersteunen, of zelfs offline toegang tot sjablooninhoud als Adobe PhoneGap wordt gebruikt.

AEM 6.1 ondersteunt de bouw en het beheer van SPA via AEM Apps. Dit artikel zal een inleiding geven op de concepten achter de SPA en hoe zij gebruik maken van [AngularJS](https://angularjs.org/) om uw merk naar de App Store en Google Play te brengen.

## SPA in AEM apps {#spa-in-aem-apps}

Met het toepassingsframework voor één pagina in AEM Apps kunt u de hoge prestaties van een AngularJS-app verhogen en tegelijkertijd auteurs (of ander niet-technisch personeel) de mogelijkheid bieden om de inhoud van de app te maken en te beheren via de voor aanrakingen geoptimaliseerde omgeving voor slepen en neerzetten die traditioneel is gereserveerd voor het beheer van websites. Hebt u al een site gebouwd met AEM? U zult merken dat het opnieuw gebruiken van uw inhoud, componenten, werkschema&#39;s, activa, en toestemmingen met AEM Apps gemakkelijk is.

## AngularJS Application Module {#angularjs-application-module}

AEM Apps behandelt veel van de configuratie AngularJS voor u, met inbegrip van het samenstellen van de top-level module van uw app. Deze module heeft standaard de naam &#39;AEMAngularApp&#39; en het script dat verantwoordelijk is voor de generatie ervan is te vinden (en te bedekken) op /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp.

Een deel van de initialisatie van uw app bestaat uit het opgeven van welke AngularJS-modules de toepassing afhankelijk is. De lijst met modules die door uw app worden gebruikt, is opgegeven door een script op /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp en kan worden bedekt door de paginacomponent van uw eigen apps om extra AngularJS-modules in te schakelen die uw app nodig heeft. Als voorbeeld, vergelijk het bovengenoemde manuscript met de implementatie van de Geometrixx (die in /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp wordt gevestigd).

Om navigatie tussen de verschillende staten in uw app te steunen, herhaalt het angular-app-module manuscript door alle afstammende pagina&#39;s van uw hoogste niveau app pagina om een reeks &quot;routes&quot;te produceren en elke weg op de dienst te vormen $routeProvider van de Angular. Neem voor een voorbeeld van hoe dit er in de praktijk uitziet, een blik op het angular-app-module script dat is gegenereerd door het voorbeeld van de Geometrixx Outdoors-app: (voor een koppeling is een lokale instantie vereist) [http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

Door in te schrijven naar de gegenereerde AEMAngularApp, ziet u een reeks routes die als volgt worden opgegeven:

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

Het bovenstaande voorbeeld illustreert met name een voorbeeld van het doorgeven van een parameter als onderdeel van het pad. In dit voorbeeld geven we aan dat wanneer een pad wordt aangevraagd dat voldoet aan het opgegeven patroon (/content/phonegap/geometrixx-outdoor/en/home/products/:id), het moet worden afgehandeld door de sjabloon home/products.template.html en de controller &#39;contentphonegapgeometrixxoutdoorsenhomeproducts&#39; moet gebruiken.

Het malplaatje te laden wanneer deze route wordt gevraagd wordt gespecificeerd door het templateUrl bezit. Dit malplaatje zal de HTML van AEM componenten bevatten die op de pagina zijn inbegrepen, evenals om het even welke richtlijnen AngularJS noodzakelijk voor de bedrading omhoog de cliëntkant van de toepassing. Neem bijvoorbeeld een voorbeeld van een AngularJS-instructie in een Geometrixx-component, kijk naar regel 45 van template.jsp (/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp) van de veegbeweging-carrousel.

## Paginacontrollers {#page-controllers}

In de eigen woorden van Angular, &quot;is een Controlemechanisme een JavaScript aannemersfunctie die wordt gebruikt om het Toepassingsgebied van de Angular te verhogen.&quot; ([bron](https://docs.angularjs.org/guide/controller)) Elke pagina in een AEM wordt automatisch getelegrafeerd tot een controlemechanisme dat door om het even welke controlemechanisme kan worden uitgebreid die een specificeert `frameworkType` van `angular`. Bekijk de ng-text component als voorbeeld (/libs/mobileapps/components/angular/ng-text), met inbegrip van de cq:template knoop die ervoor zorgt telkens als deze component aan een pagina wordt toegevoegd het dit belangrijke bezit omvat.

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

In het bovenstaande voorbeeld merkt u op dat we een parameter uit de `$routeParams` en deze vervolgens in de mappenstructuur te masseren waarin onze JSON-gegevens zijn opgeslagen. Door met de sku om te gaan `id` op deze manier, kunnen wij één enkel malplaatje van het Product leveren dat de productgegevens voor potentieel duizenden verschillende producten kan teruggeven. Dit is een veel scalable model dat een individuele route voor elk punt in (potentieel) massaal productgegevensbestand vereist.

Er zijn ook twee onderdelen aan het werk: ng-product vergroot het toepassingsgebied met de gegevens die het uit het bovenstaande haalt `$http` vraag. Deze pagina bevat ook een ng-afbeelding die het bereik vergroot met de waarde die het ophaalt uit het antwoord. Op grond van de Angular `$http` de dienst, zal elke component geduld wachten tot het verzoek wordt gebeëindigd en de belofte het wordt gecreeerd vervuld.

## De volgende stappen {#the-next-steps}

Als u meer hebt geleerd over de toepassingen voor één pagina, raadpleegt u [Apps ontwikkelen met PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md).
