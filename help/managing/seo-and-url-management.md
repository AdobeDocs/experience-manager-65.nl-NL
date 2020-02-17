---
title: Aanbevolen werkwijzen voor SEO- en URL-beheer
seo-title: Aanbevolen werkwijzen voor SEO- en URL-beheer
description: Leer over SEO beste praktijken en aanbevelingen voor het bereiken van deze op een implementatie AEM.
seo-description: Leer over SEO beste praktijken en aanbevelingen voor het bereiken van deze op een implementatie AEM.
uuid: 943e76c4-bd88-4b52-bb43-db375eb89d23
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 7c8f2cec-870b-41a8-8d98-70e29b495587
docset: aem65
translation-type: tm+mt
source-git-commit: c623724df8d849f4cc01f5dc134c775dc24dafc7

---


# Aanbevolen werkwijzen voor SEO- en URL-beheer{#seo-and-url-management-best-practices}

SEO (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s) is voor veel marketeers een belangrijk probleem geworden. Daarom moeten de SEO-zorgen over veel AEM-projecten worden aangepakt.

In dit document worden eerst enkele best practices [voor](#seo-best-practices) SEO beschreven en aanbevelingen voor het bereiken van deze best practices voor een AEM-implementatie. Vervolgens wordt in dit document dieper ingegaan op enkele van de meer [complexe implementatiestappen](#aem-configurations) die in de eerste sectie aan de orde worden gesteld.

## SEO Best practices {#seo-best-practices}

In deze sectie worden enkele algemene SEO-best practices beschreven.

### URL&#39;s {#urls}

Er zijn enkele algemeen aanvaarde aanbevolen procedures voor URL&#39;s.

In uw AEM- project, wanneer het evalueren van uw URLs, vraag me het volgende:

&quot;Als een gebruiker deze URL en geen van de inhoud op de pagina zou zien, konden zij beschrijven wat deze pagina was?&quot;

Als het antwoord &quot;ja&quot; is, werkt de URL waarschijnlijk goed voor een zoekmachine.

Hier volgen enkele algemene tips voor het samenstellen van URL&#39;s voor SEO:

* Gebruik afbreekstreepjes om woorden van elkaar te scheiden.

   * Geef pagina&#39;s een naam met afbreekstreepjes (-) als scheidingstekens.
   * Vermijd het gebruik van kamelazen, onderstrepingstekens en spaties.

* Vermijd waar mogelijk het gebruik van queryparameters. Beperk deze indien nodig tot maximaal twee.

   * Gebruik de mappenstructuur om de informatiearchitectuur aan te geven, indien beschikbaar.
   * Als een mappenstructuur geen optie is, maakt u gebruik van de optie Selectoren splitsen in de URL in plaats van queryreeksen. Naast de SEO-waarde die ze bieden, zorgen kiezers voor de sling-optie ervoor dat de pagina&#39;s ook in de cache kunnen worden geplaatst voor de verzender.

* Hoe beter een URL voor mensen leesbaar is, hoe beter. als trefwoorden aanwezig zijn in de URL, wordt de waarde verhoogd.

   * Wanneer u kiezers op een pagina gebruikt, heeft de voorkeur aan kiezers die een semantische waarde bieden.
   * Als een mens uw URL niet kan lezen, kan een zoekmachine dat ook niet.
   * Bijvoorbeeld:
      `mybrand.com/products/product-detail.product-category.product-name.html`
heeft de voorkeur boven `mybrand.com/products/product-detail.1234.html`

* Vermijd waar mogelijk subdomeinen, aangezien de onderzoeksmotoren hen als verschillende entiteiten zullen behandelen, die de SEO waarde van de plaats verdelen.

   * Gebruik in plaats daarvan subpaden op het eerste niveau. Bijvoorbeeld, in plaats van `es.mybrand.com/home.html`, gebruik `www.mybrand.com/es/home.html`.

   * Plan de inhoudshiërarchie zodat deze overeenkomt met de manier waarop de inhoud wordt weergegeven, volgens deze richtlijn.

* De doeltreffendheid van trefwoorden in URL&#39;s neemt af naarmate de lengte van de URL en de positie van het trefwoord toenemen. Korter is dus beter.

   * Gebruik technieken en functies voor het verkorten van URL&#39;s die door AEM worden geboden om overbodige URL-onderdelen te verwijderen.
   * De voorkeur `mybrand.com/en/myPage.html` wordt bijvoorbeeld gegeven aan `mybrand.com/content/my-brand/en/myPage.html`.

* Gebruik canonieke URL&#39;s.

   * Wanneer u een URL vanuit verschillende paden of met verschillende parameters of kiezers kunt bedienen, moet u ervoor zorgen dat u een `rel=canonical` tag op de pagina gebruikt.

   * Dit kan worden opgenomen in de code voor de AEM-sjabloon.

* Pas URLs aan paginatitels waar mogelijk aan.

   * Inhoudsauteurs moeten worden aangemoedigd deze praktijk te volgen.

* Ondersteunt hoofdlettergevoeligheid in URL-aanvragen.

   * Vorm de verzender om alle binnenkomende verzoeken als kleine letters te herschrijven.
   * Schrijvers van trainingsinhoud om alle pagina&#39;s te maken met kleine letters.

* Zorg ervoor dat elke pagina slechts van één protocol wordt gediend.

   * Soms worden sites doorgegeven `http` totdat een gebruiker een pagina bereikt met bijvoorbeeld een uitcheckformulier of een aanmeldingsformulier, waarna de gebruiker naar `https`deze pagina gaat. Als de gebruiker bij het koppelen van deze pagina terug kan gaan naar `http` pagina&#39;s en deze kan openen `https`, worden deze door het zoekprogramma bijgehouden als twee afzonderlijke pagina&#39;s.

   * Google geeft momenteel de voorkeur aan `https` pagina&#39;s boven `http` pagina&#39;s. Daarom maakt het het voor iedereen vaak gemakkelijker om de hele site te bedienen `https`.

### Serverconfiguratie {#server-configuration}

Voor serverconfiguratie kunt u de volgende stappen uitvoeren om ervoor te zorgen dat alleen de juiste inhoud wordt gekropen:

* Gebruik een `robots.txt` bestand om te blokkeren dat inhoud die niet moet worden geïndexeerd, horizontaal schuift.

   * Blok **alle** kruipen in testomgevingen.

* Wanneer u een nieuwe site met bijgewerkte URL&#39;s start, implementeert u 301 omleidingen om ervoor te zorgen dat uw bestaande SEO-classificatie niet verloren gaat.
* Neem een favicon op voor uw site.
* Een XML-sitemap implementeren om het voor zoekprogramma&#39;s gemakkelijker te maken door uw inhoud te kruipen. Zorg ervoor dat u een mobiele sitemap opneemt voor mobiele en/of responsieve sites.

## AEM-configuraties {#aem-configurations}

In deze sectie worden de benodigde implementatiestappen beschreven waarmee AEM deze SEO-aanbevelingen kan uitvoeren.

### Selectors voor schuiven gebruiken {#using-sling-selectors}

Eerder, was het gebruiken van vraagparameters de algemeen erkende praktijk wanneer het bouwen van een toepassing van het ondernemingsWeb.

De afgelopen jaren is het steeds vaker zo dat deze worden geschrapt in een poging om URL&#39;s leesbaarder te maken. Op vele platforms, impliceert dit het uitvoeren van omleidingen op de Webserver of het Netwerk van de Levering van de Inhoud (CDN), maar het Sling maakt dit ongecompliceerd. Selectors voor schuiven:

* Verbeter de leesbaarheid van URL.
* Hiermee kunt u uw pagina&#39;s in cache plaatsen op de dispatcher en wordt de beveiliging vaak verbeterd.
* Sta u toe om de inhoud direct te richten, eerder dan het hebben van een generisch servlet die inhoud terugwint. Dit verleent u de voordelen van ACLs die u op uw bewaarplaats en filters toepast die u op de verzender toepast.

#### Selectors voor servlets gebruiken {#using-selectors-for-servlets}

AEM biedt ons twee opties bij het schrijven van servlets:

* **bin** servlets
* **Sling** servlets

De volgende voorbeelden laten zien hoe u servlets kunt registreren die zowel deze patronen als het voordeel volgen dat wordt verkregen door het gebruik van Sling servlets.

#### Bin servlets (één niveau omlaag) {#bin-servlets-one-level-down}

**Bin** servlets volgen het patroon dat vele ontwikkelaars aan van J2EE programmering worden gebruikt. servlet wordt geregistreerd bij een specifieke weg, die in het geval van AEM gewoonlijk onder is `/bin`, en u haalt de noodzakelijke verzoekparameters uit het vraagkoord.

De SCR annotatie voor dit type servlet zou iets als dit kijken:

```
@SlingServlet(paths = "/bin/myApp/myServlet", extensions = "json", methods = "GET")
```

Vervolgens extraheert u de parameters uit de querytekenreeks via het `SlingHttpServletRequest` object dat in de `doGet` methode is opgenomen. bijvoorbeeld:

```
String myParam = req.getParameter("myParam");
```

De resulterende gebruikte URL zou er ongeveer als volgt uitzien:

`https://www.mydomain.com/bin/myApp/myServlet.json?myParam=myValue`

Met deze aanpak moeten enkele punten in overweging worden genomen:

* De URL verliest zelf SEO-waarde. Gebruikers die de site openen, inclusief zoekmachines, ontvangen geen semantische waarde van de URL, omdat de URL een programmatisch pad vertegenwoordigt en niet de inhoudshiërarchie.
* De aanwezigheid van vraagparameters in URL betekent dat de verzender niet de reactie in het voorgeheugen onder kan brengen.
* Als u deze servlet wilt beveiligen, moet u uw eigen logica van de douaneveiligheid in servlet uitvoeren.
* De verzender moet (zorgvuldig) worden gevormd om bloot te stellen `/bin/myApp/myServlet`. Als u deze functie openbaar maakt, `/bin` kunt u toegang krijgen tot bepaalde servers die niet toegankelijk moeten zijn voor bezoekers van de site.

#### Serlets verkopen (één niveau omlaag) {#sling-servlets-one-level-down}

**Met slingerende** servlets kunt u uw servlet op de omgekeerde manier registreren. In plaats van een servlet te richten en de inhoud te specificeren u servlet zou willen teruggeven gebaseerd op de vraagparameters, richt u de inhoud die u wilt en specificeert servlet die de inhoud zou moeten teruggeven die op het Verkopen selecteurs wordt gebaseerd.

De SCR annotatie voor dit type servlet zou iets als dit kijken:

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json”, methods=”GET”)
```

In dit geval is de bron die de URL-adressen (een instantie van de `myPageType` bron) automatisch toegankelijk in de servlet. Om tot het toegang te hebben, roept u:

```
Resource myPage = req.getResource();
```

De resulterende gebruikte URL zou er ongeveer als volgt uitzien:

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

De voordelen van deze aanpak zijn:

* U kunt in de waarde van SEO, die door de semantiek wordt bereikt in uw plaatshiërarchie en paginanaam wordt bereikt.
* Aangezien er geen queryparameters aanwezig zijn, kan de verzender de reactie in cache plaatsen. Bovendien wordt deze cache ongeldig als de pagina wordt geactiveerd wanneer updates worden uitgevoerd op de geadresseerde pagina.
* Alle ACLs waarop wordt toegepast `/content/my-brand/my-page` zal van kracht worden wanneer een gebruiker probeert om tot dit servlet toegang te hebben.
* De verzender wordt al geconfigureerd om deze inhoud te leveren als functie van het bedienen van de website. Geen extra configuratie wordt vereist.

### URL herschrijven {#url-rewriting}

In AEM worden al uw webpagina&#39;s opgeslagen onder `/content/my-brand/my-content`. Hoewel dit vanuit het oogpunt van gegevensbeheer in de opslagplaats nuttig kan zijn, is het niet noodzakelijk hoe u uw klanten uw plaats wilt zien en met de SEO richtlijn kan strijdig zijn om URLs zo kort mogelijk te houden. Bovendien kunt u meerdere websites vanuit hetzelfde AEM-exemplaar en verschillende domeinnamen bedienen.

In deze sectie worden de opties besproken die in AEM beschikbaar zijn voor het beheer van deze URL&#39;s en het op een beter leesbare en SEO-vriendelijke manier presenteren aan gebruikers.

#### Vanity URL&#39;s {#vanity-urls}

Als een auteur wil dat een pagina voor promotiedoeleinden vanaf een tweede locatie toegankelijk is, kunnen de vanity-URL&#39;s van AEM, die per pagina worden gedefinieerd, nuttig zijn. Als u een vanity-URL voor een pagina wilt toevoegen, navigeert u naar deze URL in de **Sites** -console en bewerkt u de pagina-eigenschappen. Onder aan het tabblad **Standaard** ziet u een sectie waar vanity-URL&#39;s kunnen worden toegevoegd. Houd er rekening mee dat als de pagina toegankelijk is via meer dan één URL, de SEO-waarde van de pagina wordt gefragmenteerd. Daarom moet een canonieke URL-tag aan de pagina worden toegevoegd om dit probleem te voorkomen.

#### Gelokaliseerde paginanamen {#localized-page-names}

U kunt gelokaliseerde paginanamen aan gebruikers van vertaalde inhoud willen tonen. Bijvoorbeeld:

* In plaats van een Spaanstalige gebruiker naar:
   `www.mydomain.com/es/home.html`

* Het zou beter zijn als de URL:
   `www.mydomain.com/es/casa.html`.

De uitdaging bij het lokaliseren van de naam van de pagina is dat veel van de lokalisatieprogramma&#39;s die beschikbaar zijn op het AEM-platform, erop vertrouwen dat de paginanamen in verschillende landinstellingen overeenkomen, zodat de inhoud gesynchroniseerd blijft.

Dankzij de `sling:alias` eigenschap kunt u ook onze taart eten. `sling:alias` kan als bezit aan om het even welke middel worden toegevoegd om voor een alias naam voor het middel toe te staan. In het vorige voorbeeld hebt u het volgende:

* Een pagina in het JCR op:
   `…/es/home`

* Voeg er vervolgens een eigenschap aan toe:
   `sling:alias` = `casa`

Hierdoor zouden de vertaalhulpmiddelen van AEM, zoals de manager van meerdere sites, een relatie kunnen blijven onderhouden tussen:

* `/en/home`

* `/es/home`

Eindgebruikers kunnen ook in hun eigen taal met de paginanaam communiceren.

>[!NOTE]
>
>De `sling:alias` eigenschap kan worden ingesteld met de eigenschap [Alias bij het bewerken van Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md#advanced).

#### /etc/map {#etc-map}

In een standaard AEM-installatie:

* voor de OSGi-configuratie
   **Apache Sling Resource Resolver Factory**( `org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* the, eigenschap
   **Toewijzingslocatie** ( `resource.resolver.map.location`)

* is standaard ingesteld op `/etc/map`.

Toewijzingsdefinities kunnen op deze locatie worden toegevoegd om binnenkomende aanvragen toe te wijzen, URL&#39;s op pagina&#39;s in AEM te herschrijven, of beide.

Als u een nieuwe toewijzing wilt maken, maakt u een nieuw `sling:Mapping` knooppunt op deze locatie onder `/http` of `/https`. Gebaseerd op de `sling:match` en de `sling:internalRedirect` eigenschappen die op deze knoop worden geplaatst, zal AEM al verkeer voor overeenkomende URL aan de waarde richten die in het `internalRedirect` bezit wordt gespecificeerd.

Hoewel dit de benadering is die in de officiële documentatie van AEM en Sling wordt gedocumenteerd, is de regelmatige uitdrukkingssteun die door deze implementatie wordt verstrekt in werkingsgebied beperkt in vergelijking met de opties die aan ons door het `SlingResourceResolver` direct te gebruiken beschikbaar zijn. Bovendien kan het op deze manier implementeren van toewijzingen leiden tot problemen met de invalidatie van het cachegeheugen van de verzender.

Hier volgt een voorbeeld van hoe dit probleem zich voordoet:

1. Een gebruiker bezoekt uw website en vraagt `https://www.mydomain.com/my-page.html`
1. De verzender stuurt dit verzoek door naar de publicatieserver.
1. De publicatieserver lost dit verzoek op `/etc/map``/content/my-brand/my-page` en geeft de pagina weer.

1. De verzender plaatst de reactie in het cachegeheugen `/my-page.html` en retourneert de reactie aan de gebruiker.
1. Een auteur van inhoud wijzigt deze pagina en activeert deze.
1. De verzender flush agent verzendt een verzoek tot ongeldigverklaring voor `/content/my-brand/my-page`**.**Aangezien de verzender geen pagina heeft die in het cachegeheugen is opgeslagen op dit pad, blijft de oude inhoud in het cachegeheugen opgeslagen en is deze niet beschikbaar.

Er zijn manieren om aangepaste verstuurings-spoelregels te configureren die de kortere URL aan de langere URL toewijzen voor het ongeldig maken van de cache.

Er is echter ook een eenvoudigere manier om dit te beheren:

1. **Regels voor SlingResourceResolver**

   Met behulp van de webconsole (bijvoorbeeld localhost:4502/system/console/configMgr) kunt u de Sling Resource Resolver configureren:

   * **Apache Sling Resource Resolver Factory**
      `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.
   Het wordt geadviseerd dat u de afbeeldingen bouwt die worden vereist om URLs als regelmatige uitdrukkingen te verkorten, dan deze configuraties onder een OsgiConfignode te bepalen, `config.publish`die in uw bouwstijl inbegrepen is.

   In plaats van uw toewijzingen in te definiëren, kunt u ze rechtstreeks toewijzen aan de eigenschap `/etc/map`URL Mappings **(** `resource.resolver.mapping`):

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   In dit eenvoudige voorbeeld verwijdert u van het begin `/content/my-brand/` van elke URL waar deze aanwezig is.

   Hiermee converteert u een URL:

   * from `/content/my-brand/my-page.html`
   * alleen `/my-page.html`
   Dit is in overeenstemming met de aanbevolen praktijk om URL&#39;s zo kort mogelijk te houden.

1. **URL-uitvoer toewijzen op pagina&#39;s**

   Nadat u uw toewijzingen in de Apache Sling Resource Resolver hebt bepaald, moet u deze toewijzingen in uw componenten gebruiken om ervoor te zorgen dat URLs u op uw pagina&#39;s uitvoert kort en tij zijn. U kunt dit doen door de kaartfunctie van `ResourceResolver`te gebruiken.

   Als u bijvoorbeeld een aangepaste navigatiecomponent implementeerde die de onderliggende elementen van de huidige pagina opsomt, kunt u de toewijzingsmethode als volgt gebruiken:

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Mod Apache HTTP Server_rewrite {#apache-http-server-mod-rewrite}

Tot dusver, hebt u afbeeldingen samen met de logica in uw componenten uitgevoerd om deze afbeeldingen te gebruiken wanneer het uitvoeren van URLs op onze pagina&#39;s.

Het laatste stuk aan de puzzel is het behandelen van deze verkorte URLs wanneer zij binnen aan de verzender komen, die is waar in spel `mod_rewrite` komt. Het grootste voordeel aan het gebruiken `mod_rewrite` is dat URLs terug naar hun lange vorm *alvorens* zij naar de verzender module worden verzonden wordt in kaart gebracht. Dit betekent dat de verzender de lange URL opvraagt bij de publicatieserver en deze dienovereenkomstig in de cache plaatst. Daarom kunnen aanvragen voor het verwijderen van verzendingen die afkomstig zijn van de publicatieserver deze inhoud ongeldig maken.

Om deze regels uit te voeren, kunt u `RewriteRule` elementen onder uw virtuele gastheer in de configuratie van de Server van Apache toevoegen HTTP. Als u de verkorte URL&#39;s uit het vorige voorbeeld wilt uitbreiden, kunt u een regel implementeren die er als volgt uitziet:

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Canonical URL tags {#canonical-url-tags}

Canonieke URL-tags zijn koppelingscodes die in de kop van een HTML-document worden geplaatst om te verduidelijken hoe zoekprogramma&#39;s een pagina moeten behandelen terwijl de inhoud wordt geïndexeerd. Het voordeel dat ze bieden, is ervoor te zorgen dat (verschillende versies van) een pagina als hetzelfde wordt geïndexeerd, zelfs als de URL naar de pagina verschillen kan bevatten.

Als een site bijvoorbeeld een printervriendelijke versie van een pagina zou aanbieden, zou een zoekprogramma deze pagina mogelijk apart van de standaardversie van de pagina indexeren. De canonieke tag geeft aan de zoekfunctie door dat ze hetzelfde zijn.

Voorbeelden:

* https://www.mydomain.com/my-brand/my-page.html
* https://www.mydomain.com/my-brand/my-page.print.html

Beide zouden de volgende markering op het hoofd van de pagina toepassen:

```xml
<link rel=”canonical” href=”my-brand/my-page.html”/>
```

Het `href` kan relatief of absoluut zijn. De code moet worden opgenomen in de paginamarkering om de canonieke URL voor de pagina te bepalen en deze tag uit te voeren.

### De verzender configureren voor hoofdlettergevoeligheid {#configuring-the-dispatcher-for-case-insensitivity}

U kunt het beste alle pagina&#39;s met kleine letters bedienen. U wilt echter niet dat een gebruiker 404 krijgt wanneer hij of zij uw website opent met hoofdletters in de URL. Daarom raadt Adobe u aan een herschrijfregel toe te voegen in de configuratie van Apache HTTP Server om alle inkomende URL&#39;s toe te wijzen aan kleine letters. Bovendien moeten auteurs van inhoud worden getraind om hun pagina&#39;s met kleine letters te maken.

Om Apache te vormen om al binnenkomend verkeer aan kleine letters te dwingen, voeg het volgende aan `vhost` config toe:

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

Voeg bovendien het volgende toe helemaal boven aan het `htaccess` bestand:

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### Robots.txt implementeren om ontwikkelomgevingen te beschermen {#implementing-robots-txt-to-protect-development-environments}

Zoekprogramma&#39;s *moeten* controleren of er een `robots.txt` bestand aanwezig is in de hoofdmap van de site voordat u door de site kruipt. Hier moet de nadruk op worden gelegd, omdat belangrijke zoekmachines zoals Google, Yahoo of Bing dit allemaal respecteren, sommige buitenlandse zoekmachines dat niet doen.

De eenvoudigste manier om toegang tot uw gehele site te blokkeren, is een bestand met de naam `robots.txt` in de hoofdmap van de site te plaatsen met de volgende inhoud:

```xml
User-agent: *
Disallow: /
```

In een live omgeving kunt u ook bepaalde paden die u niet wilt indexeren, uitschakelen.

Het probleem met het plaatsen van het `robots.txt` bestand in de hoofdmap van de site is dat aanvragen voor het leegmaken van de dispatcher dit bestand kunnen wissen en dat URL-toewijzingen de hoofdmap van de site waarschijnlijk ergens anders plaatsen dan `DOCROOT` zoals gedefinieerd in de configuratie van Apache HTTP Server. Daarom is het gebruikelijk om dit bestand op de auteurinstantie in de hoofdmap van de site te plaatsen en het te repliceren naar de publicatie-instantie.

### Een XML-sitemap maken op AEM {#building-an-xml-sitemap-on-aem}

Crawlers gebruiken XML-sitemaps om de structuur van websites beter te begrijpen. Hoewel er geen enkele garantie is dat het aanbieden van een sitemap zal leiden tot betere beoordelingen van de SEO, is het een overeengekomen beste praktijk. U kunt handmatig een XML-bestand op de webserver onderhouden om als sitemap te gebruiken, maar het wordt aanbevolen de sitemap programmatisch te genereren, zodat de wijzigingen automatisch worden doorgevoerd wanneer auteurs nieuwe inhoud maken.

Om programmatically een sitemap te produceren, registreer een Servlet van het Sling luisterend naar een `sitemap.xml` vraag. De servlet kan dan de bron die via de servlet API wordt geleverd gebruiken om naar de huidige pagina en zijn kinderen te kijken, uitvoerend XML. De XML wordt vervolgens in de cache van de verzender geplaatst. Naar deze locatie moet worden verwezen in de eigenschap sitemap van het `robots.txt` bestand. Bovendien moet een aangepaste uitlijningsregel worden geïmplementeerd om ervoor te zorgen dat dit bestand wordt leeggemaakt wanneer een nieuwe pagina wordt geactiveerd.

>[!NOTE]
>
>U kunt een Sling Servlet registreren om naar de selecteur `sitemap` met de uitbreiding te luisteren `xml`. Hierdoor verwerkt de servlet de aanvraag op elk moment dat een URL wordt aangevraagd die eindigt in:
>    `/<path-to>/page.sitemap.xml`
Vervolgens kunt u de gevraagde bron ophalen uit de aanvraag en een sitemap genereren vanaf dat punt in de inhoudsstructuur met behulp van de JCR API&#39;s.
Het voordeel van een dergelijke aanpak is wanneer u meerdere sites hebt die vanuit hetzelfde exemplaar worden bediend. Een verzoek om `/content/siteA.sitemap.xml` zou een sitemap voor `siteA` terwijl een verzoek om `/content/siteB.sitemap.xml` zou produceren een sitemap voor `siteB` zonder de behoefte om extra code te schrijven.

### 301 omleidingen maken voor verouderde URL&#39;s {#creating-redirects-for-legacy-urls}

Wanneer u een site met een nieuwe structuur start, is het om twee redenen belangrijk om 301 omleidingen te implementeren en te testen in Apache HTTP Server:

* De oudere URL&#39;s hebben in de loop der tijd een SEO-waarde opgebouwd. Door een omleiding te implementeren, kan het zoekprogramma deze waarde toepassen op de nieuwe URL.
* Gebruikers van uw site hebben mogelijk bladwijzers voor deze pagina&#39;s gemaakt. Door omleidingen te implementeren, kunt u zeker weten dat u de gebruiker naar de pagina op de nieuwe site stuurt die het meest overeenkomt met de locatie op de oude site.

Controleer of de sectie met extra bronnen die volgt op instructies voor het implementeren van 301 omleidingen en een gereedschap om te testen of uw omleidingen naar behoren werken.

## Additional Resources {#additional-resources}

Zie de volgende aanvullende bronnen voor meer informatie:

* [Brontoewijzing](/help/sites-deploying/resource-mapping.md)
* [https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url](https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url)
* [https://moz.com/blog/15-seo-best-practices-for-structuring-urls](https://moz.com/blog/15-seo-best-practices-for-structuring-urls)
* [https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/](https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/)
* [https://sling.apache.org/documentation/the-sling-engine/servlets.html](https://sling.apache.org/documentation/the-sling-engine/servlets.html)
* [https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
* [https://httpd.apache.org/docs/current/mod/mod_rewrite.html](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)
* [https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps](https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps)
* [https://www.robotstxt.org/robotstxt.html](https://www.robotstxt.org/robotstxt.html)
* [https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/](https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/)
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)

