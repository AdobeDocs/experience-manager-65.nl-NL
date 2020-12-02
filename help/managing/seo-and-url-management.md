---
title: Aanbevolen werkwijzen voor SEO- en URL-beheer
seo-title: Aanbevolen werkwijzen voor SEO- en URL-beheer
description: Leer over SEO beste praktijken en aanbevelingen om deze op een AEM implementatie te bereiken.
seo-description: Leer over SEO beste praktijken en aanbevelingen om deze op een AEM implementatie te bereiken.
uuid: 943e76c4-bd88-4b52-bb43-db375eb89d23
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 7c8f2cec-870b-41a8-8d98-70e29b495587
docset: aem65
translation-type: tm+mt
source-git-commit: c623724df8d849f4cc01f5dc134c775dc24dafc7
workflow-type: tm+mt
source-wordcount: '3119'
ht-degree: 97%

---


# Aanbevolen werkwijzen voor SEO- en URL-beheer{#seo-and-url-management-best-practices}

SEO (Search Engine Optimization, zoekmachineoptimalisatie) is voor veel marketeers een belangrijke zorg geworden. Daarom moet bij veel AEM projecten rekening worden gehouden met de bezorgdheid van de ZOO.

In dit document worden eerst enkele [SEO best practices](#seo-best-practices) beschreven en aanbevelingen voor het bereiken van deze procedures voor een AEM-implementatie. Vervolgens wordt in dit document dieper ingegaan op enkele van de meer [complexe implementatiestappen](#aem-configurations) die in de eerste sectie aan bod komen.

## Best practices voor SEO {#seo-best-practices}

In deze sectie worden enkele algemene best practices voor SEO beschreven.

### URL&#39;s {#urls}

Er zijn enkele algemeen aanvaarde best practices voor URL&#39;s.

Stel uzelf de volgende vragen wanneer u uw URL&#39;s evalueert in uw AEM-project:

&quot;Als een gebruiker deze URL zou zien, maar niet de content op de pagina, zou de gebruiker dan kunnen beschrijven waarover deze pagina gaat?&quot;

Als het antwoord &quot;ja&quot; is, zal de URL waarschijnlijk goed werken voor een zoekmachine.

Hier volgen enkele algemene tips voor het samenstellen van URL&#39;s voor SEO:

* Gebruik afbreekstreepjes om woorden van elkaar te scheiden.

   * Geef pagina&#39;s een naam met afbreekstreepjes (-) als scheidingstekens.
   * Vermijd het gebruik van CamelCase-woorden, onderstrepingstekens en spaties.

* Vermijd waar mogelijk het gebruik van queryparameters. Als deze toch nodig zijn, gebruik er dan maximaal twee.

   * Gebruik de mappenstructuur om de informatiearchitectuur aan te geven, indien beschikbaar.
   * Als een mappenstructuur geen optie is, gebruikt u Sling-selectors in de URL in plaats van queryreeksen. Naast de SEO-waarde die ze bieden, zorgen Sling-selectors er ook voor dat de pagina&#39;s in de cache kunnen worden geplaatst voor de dispatcher.

* Hoe beter een URL voor mensen leesbaar is, hoe beter de waarde zal zijn als trefwoorden aanwezig zijn in de URL.

   * Wanneer u selectors op een pagina gebruikt, hebben selectors die semantische waarde bieden, de voorkeur.
   * Als mensen uw URL niet kunnen lezen, kan een zoekmachine dat ook niet.
   * Bijvoorbeeld:
      `mybrand.com/products/product-detail.product-category.product-name.html`
heeft de voorkeur boven 
`mybrand.com/products/product-detail.1234.html`

* Vermijd waar mogelijk subdomeinen, aangezien zoekmachines deze als verschillende entiteiten behandelen, waardoor de SEO-waarde van de site wordt gefragmenteerd.

   * Gebruik in plaats daarvan subpaden op het eerste niveau. Gebruik bijvoorbeeld `www.mybrand.com/es/home.html` in plaats van `es.mybrand.com/home.html`.

   * Plan de contenthiërarchie zodat deze overeenkomt met de manier waarop de content wordt weergegeven, volgens deze richtlijn.

* De doeltreffendheid van trefwoorden in URL&#39;s neemt af naarmate de lengte van de URL en de positie van het trefwoord toenemen. Korter is dus beter.

   * Gebruik technieken en functies voor het verkorten van URL&#39;s die door AEM worden geboden om overbodige URL-onderdelen te verwijderen.
   * `mybrand.com/en/myPage.html` heeft bijvoorbeeld de voorkeur boven `mybrand.com/content/my-brand/en/myPage.html`.

* Gebruik canonieke URL&#39;s.

   * Wanneer u een URL vanuit verschillende paden of met verschillende parameters of selectors kunt bedienen, moet u ervoor zorgen dat u een tag `rel=canonical` op de pagina gebruikt.

   * Deze kan worden opgenomen in de code voor de AEM-sjabloon.

* Pas waar mogelijk URL&#39;s aan paginatitels aan.

   * Contentauteurs moeten worden aangemoedigd deze praktijk toe te passen.

* Ondersteun hoofdlettergevoeligheid in URL-aanvragen.

   * Configureer de dispatcher om alle binnenkomende aanvragen als kleine letters te herschrijven.
   * Train contentauteurs om alle pagina&#39;s met kleine letters te maken.

* Zorg ervoor dat elke pagina slechts vanaf één protocol wordt aangeboden.

   * Soms worden sites aangeboden via `http` totdat een gebruiker een pagina bereikt met bijvoorbeeld een uitcheckformulier of een aanmeldingsformulier, waarna naar `https` wordt omgeschakeld. Als de gebruiker bij het koppelen van deze pagina terug kan gaan naar `http`-pagina&#39;s en deze kan openen via `https`, worden deze door de zoekmachine bijgehouden als twee afzonderlijke pagina&#39;s.

   * Google geeft momenteel de voorkeur aan `https`-pagina&#39;s boven `http`-pagina&#39;s. Daarom is het voor iedereen vaak gemakkelijker om de hele site aan te bieden via `https`.

### Serverconfiguratie {#server-configuration}

Bij serverconfiguratie kunt u de volgende stappen uitvoeren om ervoor te zorgen dat alleen de juiste content wordt verkend:

* Gebruik een `robots.txt`-bestand om te voorkomen dat content die niet moet worden geïndexeerd, wordt verkend.

   * Blokkeer **alle** verkenningen in testomgevingen.

* Wanneer u een nieuwe site met bijgewerkte URL&#39;s start, implementeert u 301-omleidingen om ervoor te zorgen dat uw bestaande SEO-classificatie niet verloren gaat.
* Neem een favicon op voor uw site.
* Implementeer een XML-sitemap zodat zoekmachines gemakkelijker uw content kunnen verkennen. Neem een mobiele sitemap op voor mobiele en/of responsieve sites.

## AEM-configuraties {#aem-configurations}

In deze sectie worden de benodigde implementatiestappen beschreven waarmee AEM deze SEO-aanbevelingen kan uitvoeren.

### Sling-selectors gebruiken {#using-sling-selectors}

Eerder was het gebruik van queryparameters de algemeen aanvaarde praktijk voor het bouwen van een zakelijke webapplicatie.

De afgelopen jaren worden queryparameters echter steeds meer verwijderd in een poging om URL&#39;s leesbaarder te maken. Op vele platforms impliceert dit het uitvoeren van omleidingen op de webserver of het CDN (Content Delivery Network of netwerk voor contentlevering), maar dankzij Sling wordt dit eenvoudiger. Sling-selectors:

* Verbeteren de leesbaarheid van URL&#39;s.
* Laten u uw pagina&#39;s in een cache plaatsen op de dispatcher en verbeteren vaak de beveiliging.
* Staan u toe om de content direct te richten, eerder dan dat een generische servlet content ophaalt. Dit biedt u de voordelen van ACL&#39;s die u op uw opslagplaats toepast en filters die u op de dispatcher toepast.

#### Selectors voor servlets gebruiken {#using-selectors-for-servlets}

AEM biedt ons twee opties bij het schrijven van servlets:

* **bin**-servlets
* **Sling**-servlets

De volgende voorbeelden tonen hoe u servlets kunt registreren die beide patronen volgen en u ontdekt ook welke voordelen verbonden zijn aan het gebruik van Sling-servlets.

#### Bin-servlets (één niveau omlaag) {#bin-servlets-one-level-down}

**Bin**-servlets volgen het patroon dat vele ontwikkelaars kennen via J2EE-programmering. De servlet wordt geregistreerd op een specifiek pad, dat zich in het geval van AEM gewoonlijk onder `/bin` bevindt, en u extraheert de benodigde aanvraagparameters uit de queryreeks.

De SCR-annotatie voor dit type servlet ziet er ongeveer als volgt uit:

```
@SlingServlet(paths = "/bin/myApp/myServlet", extensions = "json", methods = "GET")
```

Vervolgens extraheert u de parameters uit de queryreeks via het `SlingHttpServletRequest`-object dat in de `doGet`-methode is opgenomen, bijvoorbeeld:

```
String myParam = req.getParameter("myParam");
```

De resulterende URL die wordt gebruikt, ziet er ongeveer als volgt uit:

`https://www.mydomain.com/bin/myApp/myServlet.json?myParam=myValue`

Met deze aanpak moeten enkele punten in overweging worden genomen:

* De URL zelf verliest SEO-waarde. Gebruikers die toegang krijgen tot de site, inclusief zoekmachines, ontvangen geen semantische waarde van de URL, omdat de URL een programmatisch pad vertegenwoordigt en niet de contenthiërarchie.
* De aanwezigheid van queryparameters in de URL betekent dat de dispatcher het antwoord niet in een cache kan plaatsen.
* Als u deze servlet wilt beveiligen, moet u uw eigen aangepaste beveiligingslogica in de servlet implementeren.
* De dispatcher moet (zorgvuldig) worden geconfigureerd om `/bin/myApp/myServlet` beschikbaar te maken. Als `/bin` gewoon beschikbaar wordt gemaakt, is toegang mogelijk tot bepaalde servlets die niet toegankelijk mogen zijn voor bezoekers van de site.

#### Sling-servlets (één niveau omlaag) {#sling-servlets-one-level-down}

Met **Sling**-servlets kunt u uw servlet op de omgekeerde manier registreren. In plaats van dat u zich richt op een servlet en de content opgeeft die door uw servlet moet worden gerenderd op basis van de queryparameters, richt u zich op de content die u wilt en geeft u de servlet op die de content moet renderen op basis van Sling-selectors.

De SCR-annotatie voor dit type servlet ziet er ongeveer als volgt uit:

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json”, methods=”GET”)
```

In dit geval is de bron die door de URL wordt aangesproken (een instantie van de bron `myPageType`), automatisch toegankelijk in de servlet. Om toegang te krijgen roept u het volgende aan:

```
Resource myPage = req.getResource();
```

De resulterende URL die wordt gebruikt, ziet er ongeveer als volgt uit:

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

De voordelen van deze aanpak zijn de volgende:

* U kunt SEO-waarde &quot;inbakken&quot; die afkomstig is van de semantiek die aanwezig is in uw sitehiërarchie en paginanaam.
* Aangezien er geen queryparameters aanwezig zijn, kan de dispatcher het antwoord in de cache plaatsen. Bovendien wordt deze cache ongeldig als de pagina wordt geactiveerd wanneer updates worden uitgevoerd op de geadresseerde pagina.
* Alle ACL&#39;s die zijn toegepast op `/content/my-brand/my-page`, worden van kracht wanneer een gebruiker toegang tot deze servlet probeert te krijgen.
* De dispatcher wordt al geconfigureerd om deze content te leveren als een functie voor het aanbieden van de website. Geen extra configuratie wordt vereist.

### URL herschrijven {#url-rewriting}

In AEM worden al uw webpagina&#39;s opgeslagen onder `/content/my-brand/my-content`. Hoewel dit vanuit het oogpunt van gegevensbeheer in de opslagplaats nuttig kan zijn, is dit niet noodzakelijk de manier waarop u uw klanten uw site wilt tonen en dit conflicteert mogelijk met de SEO-richtlijn om URL&#39;s zo kort mogelijk te houden. Bovendien biedt u mogelijk meerdere websites aan vanaf dezelfde AEM-instantie en vanaf verschillende domeinnamen.

In deze sectie worden de opties besproken die in AEM beschikbaar zijn voor het beheer van deze URL&#39;s en het op een beter leesbare en meer SEO-vriendelijke manier presenteren van deze URL&#39;s aan gebruikers.

#### Vanity-URL&#39;s {#vanity-urls}

Als een auteur wil dat een pagina voor promotiedoeleinden vanaf een tweede locatie toegankelijk is, kunnen de vanity-URL&#39;s van AEM, die per pagina worden gedefinieerd, nuttig zijn. Als u een vanity-URL voor een pagina wilt toevoegen, gaat u naar deze URL in de **Sites**-console en bewerkt u de pagina-eigenschappen. Onder aan het tabblad **Basic** ziet u een sectie waar vanity-URL&#39;s kunnen worden toegevoegd. Houd er rekening mee dat als de pagina toegankelijk is via meer dan één URL, de SEO-waarde van de pagina wordt gefragmenteerd. Daarom moet een canonieke URL-tag aan de pagina worden toegevoegd om dit probleem te voorkomen.

#### Gelokaliseerde paginanamen {#localized-page-names}

U wilt mogelijk gelokaliseerde paginanamen tonen aan gebruikers van vertaalde content. Bijvoorbeeld:

* In plaats van een Spaanstalige gebruiker te laten navigeren naar:
   `www.mydomain.com/es/home.html`

* Zou het beter zijn als de URL er als volgt uitziet:
   `www.mydomain.com/es/casa.html`.

De uitdaging bij het lokaliseren van de naam van de pagina is dat veel van de lokalisatieprogramma&#39;s die beschikbaar zijn op het AEM-platform, erop vertrouwen dat de paginanamen in verschillende landinstellingen overeenkomen, zodat de content gesynchroniseerd blijft.

Dankzij de `sling:alias` eigenschap kunt u echt het onderste uit de kan halen. `sling:alias` kan als eigenschap aan om het even welke bron worden toegevoegd om een aliasnaam voor de bron mogelijk te maken. In het vorige voorbeeld hebt u het volgende:

* Een pagina in het JCR op:
   `…/es/home`

* Voeg er vervolgens een eigenschap aan toe:
   `sling:alias` = `casa`

Hierdoor kunnen de vertaalhulpmiddelen van AEM, zoals Multi-Site Manager, een relatie blijven onderhouden tussen:

* `/en/home`

* `/es/home`

Tegelijk kunnen eindgebruikers ook in hun eigen taal met de paginanaam communiceren.

>[!NOTE]
>
>De eigenschap `sling:alias` kan worden ingesteld met de eigenschap [Alias bij het bewerken van Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md#advanced).

#### /etc/map {#etc-map}

In een standaard AEM-installatie:

* Voor de OSGi-configuratie
   **Apache Sling Resource Resolver Factory**
( 
`org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* Is de eigenschap
   **Mapping Location** ( `resource.resolver.map.location`)

* standaard ingesteld op `/etc/map`.

Toewijzingsdefinities kunnen op deze locatie worden toegevoegd om binnenkomende aanvragen toe te wijzen, URL&#39;s op pagina&#39;s in AEM te herschrijven of beide.

Als u een nieuwe toewijzing wilt maken, maakt u een nieuw `sling:Mapping`-knooppunt op deze locatie onder `/http` of `/https`. Gebaseerd op de eigenschappen `sling:match` en `sling:internalRedirect` die op dit knooppunt zijn ingesteld, zal AEM al het verkeer voor de overeenkomstige URL omleiden naar de waarde die in de eigenschap `internalRedirect` is opgegeven.

Hoewel dit de benadering is die in de officiële documentatie van AEM en Sling wordt beschreven, is ondersteuning voor reguliere expressies die door deze implementatie wordt verstrekt, beperkt in bereik in vergelijking met de opties die beschikbaar zijn door de `SlingResourceResolver` direct te gebruiken. Bovendien kunnen door deze implementatiemethode problemen ontstaan met de invalidatie van de cache van de dispatcher.

Hier volgt een voorbeeld van hoe dit probleem optreedt:

1. Een gebruiker bezoekt uw website en vraagt `https://www.mydomain.com/my-page.html` aan.
1. De dispatcher stuurt deze aanvraag door naar de publicatieserver.
1. Met behulp van `/etc/map` zet de publicatieserver deze aanvraag om naar `/content/my-brand/my-page` en wordt de pagina gerenderd.

1. De dispatcher plaatst het antwoord in de cache op `/my-page.html` en retourneert het antwoord naar de gebruiker.
1. Een contentauteur voert een wijziging uit op deze pagina en activeert deze.
1. De flushagent van de dispatcher verzendt een aanvraag tot invalidatie voor `/content/my-brand/my-page`**.** Aangezien de dispatcher geen pagina heeft die in de cache is opgeslagen op dit pad, blijft de oude content in de cache opgeslagen en is deze inactief.

Er zijn manieren om aangepaste flushregels voor dispatching te configureren die de kortere URL aan de langere URL toewijzen voor de cache-invalidatie.

Er is echter ook een eenvoudigere manier om dit te beheren:

1. **Regels voor SlingResourceResolver**

   Met behulp van de webconsole (bijvoorbeeld localhost:4502/system/console/configMgr) kunt u de Sling Resource Resolver configureren:

   * **Apache Sling Resource Resolver Factory**

      `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.
   We raden u aan de toewijzingen die nodig zijn voor het verkorten van URL&#39;s als reguliere expressies, samen te stellen en vervolgens deze configuraties onder een OsgiConfignode, `config.publish`, die in uw build is inbegrepen, te definiëren.

   In plaats van uw toewijzingen te definiëren in `/etc/map`, kunt u deze rechtstreeks toewijzen aan de eigenschap **URL Mappings** (`resource.resolver.mapping`):

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   In dit eenvoudige voorbeeld verwijdert u `/content/my-brand/` van het begin van elke URL waar dit aanwezig is.

   Hiermee converteert u een URL:

   * Van `/content/my-brand/my-page.html`
   * Naar gewoon `/my-page.html`

   Dit is in overeenstemming met de aanbevolen praktijk om URL&#39;s zo kort mogelijk te houden.

1. **URL-uitvoer op pagina&#39;s toewijzen**

   Nadat u uw toewijzingen in de Apache Sling Resource Resolver hebt gedefinieerd, moet u deze toewijzingen in uw componenten gebruiken om ervoor te zorgen dat de URL&#39;s die u op uw pagina&#39;s uitvoert, kort en netjes zijn. U kunt dit doen door de toewijzingsfunctie van de `ResourceResolver` te gebruiken.

   Als u bijvoorbeeld een aangepaste navigatiecomponent implementeerde die de onderliggende elementen van de huidige pagina opsomt, kunt u de toewijzingsmethode als volgt gebruiken:

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Apache HTTP Server mod_rewrite {#apache-http-server-mod-rewrite}

Tot dusver hebt u toewijzingen samen met de logica in uw componenten geïmplementeerd om deze toewijzingen te gebruiken bij het uitvoeren van URL&#39;s op onze pagina&#39;s.

Het laatste puzzelstukje is het verwerken van deze verkorte URL&#39;s in de dispatcher waar `mod_rewrite` wordt gebruikt. Het grootste voordeel aan het gebruik van `mod_rewrite`, is dat URL&#39;s opnieuw aan hun lange vorm worden toegewezen *voordat* ze naar de dispatchermodule worden verzonden. Dit betekent dat de dispatcher de lange URL aanvraagt bij de publicatieserver en deze dienovereenkomstig in de cache plaatst. Daardoor kunnen flushaanvragen voor de dispatcher die afkomstig zijn van de publicatieserver deze content ongeldig maken.

Om deze regels te implementeren, kunt u `RewriteRule`-elementen toevoegen onder uw virtuele host in de Apache HTTP Server-configuratie. Als u de verkorte URL&#39;s uit het vorige voorbeeld wilt uitbreiden, kunt u een regel implementeren die er als volgt uitziet:

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Canonieke URL-tags {#canonical-url-tags}

Canonieke URL-tags zijn koppelingstags die in de kop van een HTML-document worden geplaatst om te verduidelijken hoe zoekmachines een pagina moeten behandelen terwijl de content wordt geïndexeerd. Het voordeel van deze tags is dat ze ervoor zorgen dat (verschillende versies van) een pagina op dezelfde manier worden geïndexeerd, zelfs als de URL naar de pagina verschillen kan bevatten.

Als een site bijvoorbeeld een printervriendelijke versie van een pagina zou aanbieden, zou een zoekmachine deze pagina mogelijk afzonderlijk van de gewone versie van de pagina indexeren. De canonieke tag geeft aan de zoekmachine door dat ze hetzelfde zijn.

Voorbeelden:

* https://www.mydomain.com/my-brand/my-page.html
* https://www.mydomain.com/my-brand/my-page.print.html

Beide zouden de volgende tag op de kop van de pagina toepassen:

```xml
<link rel=”canonical” href=”my-brand/my-page.html”/>
```

De `href` kan relatief of absoluut zijn. De code moet worden opgenomen in de paginamarkering om de canonieke URL voor de pagina te bepalen en deze tag uit te voeren.

### De dispatcher configureren voor hoofdlettergevoeligheid {#configuring-the-dispatcher-for-case-insensitivity}

U kunt het beste alle pagina&#39;s met kleine letters aanbieden. U wilt echter niet dat een gebruiker een 404-foutmelding krijgt wanneer hij of zij uw website opent met hoofdletters in de URL. Daarom raadt Adobe u aan een herschrijvingsregel toe te voegen in de Apache HTTP Server-configuratie om alle binnenkomende URL&#39;s toe te wijzen aan kleine letters. Bovendien moeten contentauteurs worden getraind om hun pagina&#39;s met kleine letters te maken.

Om Apache te configureren om al het binnenkomend verkeer te forceren om kleine letters te gebruiken, voegt u het volgende toe aan de `vhost`-configuratie:

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

Voeg bovendien het volgende toe helemaal bovenaan het bestand `htaccess`:

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### robots.txt implementeren om ontwikkelomgevingen te beschermen {#implementing-robots-txt-to-protect-development-environments}

Zoekmachines *zouden moeten* controleren of er een bestand `robots.txt` aanwezig is in de hoofdmap van de site voordat uw site wordt verkend. &quot;zouden moeten&quot; wordt hier benadrukt, omdat belangrijke zoekmachines zoals Google, Yahoo of Bing dit allemaal respecteren, terwijl andere internationale zoekmachines dat niet doen.

De eenvoudigste manier om toegang tot uw gehele site te blokkeren, is een bestand met de naam `robots.txt` in de hoofdmap van de site te plaatsen met de volgende content:

```xml
User-agent: *
Disallow: /
```

In een liveomgeving kunt u ervoor kiezen om bepaalde paden die u niet wilt indexeren, niet toe te staan.

Het probleem met het plaatsen van het bestand `robots.txt` in de hoofdmap van de site, is dat flushaanvragen voor de dispatcher dit bestand kunnen wissen en dat URL-toewijzingen de hoofdmap van de site waarschijnlijk ergens anders plaatsen dan de `DOCROOT`, zoals gedefinieerd in de Apache HTTP Server-configuratie. Daarom is het gebruikelijk om dit bestand op de auteurinstantie in de hoofdmap van de site te plaatsen en het te repliceren naar de publicatie-instantie.

### Een XML-sitemap maken op AEM {#building-an-xml-sitemap-on-aem}

Verkenners gebruiken XML-sitemaps om de structuur van websites beter te begrijpen. Hoewel er geen enkele garantie is dat het aanbieden van een sitemap automatisch leidt tot betere SEO-rankings, is het een algemeen erkende best practice. U kunt handmatig een XML-bestand op de webserver onderhouden om als sitemap te gebruiken, maar het wordt aanbevolen de sitemap programmatisch te genereren, zodat de wijzigingen automatisch worden doorgevoerd in de sitemap wanneer auteurs nieuwe content maken.

Om een sitemap programmatisch te genereren, registreert u een Sling-servlet die luistert naar een aanroep van `sitemap.xml`. De servlet kan vervolgens de bron gebruiken die via de servlet-API wordt geleverd om naar de huidige pagina en de onderliggende elementen ervan te kijken, zodat XML wordt uitgevoerd. De XML wordt vervolgens in de cache van de dispatcher geplaatst. Naar deze locatie moet worden verwezen in de sitemapeigenschap van het bestand `robots.txt`. Bovendien moet een aangepaste flushregel worden geïmplementeerd om ervoor te zorgen dat dit bestand wordt leeggemaakt wanneer een nieuwe pagina wordt geactiveerd.

>[!NOTE]
>
>U kunt een Sling-servlet registreren om te luisteren naar de selector `sitemap` met de extensie `xml`. Hierdoor verwerkt de servlet de aanvraag telkens wanneer een URL wordt aangevraagd die eindigt op:
>    `/<path-to>/page.sitemap.xml`
Vervolgens kunt u de aangevraagde bron ophalen uit de aanvraag en een sitemap genereren vanaf dat punt in de contentstructuur met behulp van de JCR API&#39;s.
Het voordeel van een dergelijke aanpak is wanneer meerdere sites vanuit dezelfde instantie worden aangeboden. Een aanvraag voor `/content/siteA.sitemap.xml` zou een sitemap voor `siteA` genereren terwijl een aanvraag voor `/content/siteB.sitemap.xml` een sitemap voor `siteB` zou genereren zonder dat extra code moet worden geschreven.

### 301-omleidingen maken voor verouderde URL&#39;s {#creating-redirects-for-legacy-urls}

Wanneer u een site met een nieuwe structuur start, is het om twee redenen belangrijk om 301-omleidingen te implementeren en te testen in Apache HTTP Server:

* De verouderde URL&#39;s hebben in de loop der tijd een SEO-waarde opgebouwd. Door een omleiding te implementeren, kan de zoekmachine deze waarde toepassen op de nieuwe URL.
* Gebruikers van uw site hebben mogelijk bladwijzers voor deze pagina&#39;s gemaakt. Door omleidingen te implementeren, weet u zeker dat u de gebruiker naar de pagina op de nieuwe site stuurt die het meest overeenkomt met de locatie op de oude site.

Raadpleeg de volgende sectie met extra bronnen voor instructies voor het implementeren van 301-omleidingen en een hulpprogramma om te testen of uw omleidingen naar behoren werken.

## Aanvullende bronnen {#additional-resources}

Raadpleeg de volgende aanvullende bronnen voor meer informatie:

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

