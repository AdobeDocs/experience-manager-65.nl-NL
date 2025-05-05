---
title: Aanbevolen werkwijzen voor SEO- en URL-beheer
description: Leer over SEO beste praktijken en aanbevelingen over een AEM implementatie.
topic-tags: managing
content-type: reference
docset: aem65
exl-id: b138f6d1-0870-4071-b96e-4a759ad9a76e
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '3524'
ht-degree: 38%

---

# Aanbevolen werkwijzen voor SEO- en URL-beheer{#seo-and-url-management-best-practices}

SEO (Search Engine Optimization, optimalisering van zoekprogramma&#39;s) is een belangrijk punt van zorg geworden voor veel marketers. Daarom moeten de zorgen van de SEO over vele AEM projecten worden aangepakt.

Dit document beschrijft eerst sommige [ SEO beste praktijken ](#seo-best-practices) en aanbevelingen op een AEM implementatie. Vervolgens wordt in dit document dieper ingegaan op enkele van de meer [complexe implementatiestappen](#aem-configurations) die in de eerste sectie aan bod komen.

## SEO Best practices {#seo-best-practices}

In deze sectie worden enkele algemene best practices voor SEO beschreven.

### URL&#39;s {#urls}

Er zijn enkele geaccepteerde aanbevolen procedures voor URL&#39;s.

Stel uzelf de volgende vragen wanneer u uw URL&#39;s evalueert in uw AEM-project:

&quot;Als een gebruiker deze URL en geen van de inhoud op de pagina heeft gezien, kunnen ze deze pagina dan beschrijven?&quot;

Als het antwoord ja is, dan is het waarschijnlijk dat URL goed voor een onderzoeksmotor werkt.

Hier volgen enkele algemene tips voor het samenstellen van URL&#39;s voor SEO:

* Gebruik afbreekstreepjes om woorden van elkaar te scheiden.

   * Geef pagina&#39;s een naam met afbreekstreepjes (-) als scheidingstekens.
   * Vermijd het gebruik van CamelCase-woorden, onderstrepingstekens en spaties.

* Vermijd waar mogelijk het gebruik van queryparameters. Als deze toch nodig zijn, gebruik er dan maximaal twee.

   * Gebruik de mappenstructuur om de informatiearchitectuur aan te geven, indien beschikbaar.
   * Als een mappenstructuur geen optie is, gebruikt u Selectoren voor delen in de URL in plaats van queryreeksen. Naast de SEO-waarde die ze bieden, zorgen slingerkiezers ervoor dat pagina&#39;s ook in de cache kunnen worden geplaatst voor de Dispatcher.

* Hoe beter een URL voor mensen leesbaar is, hoe beter. Trefwoorden aanwezig hebben in de URL verhoogt waarde.

   * Wanneer u selectors op een pagina gebruikt, hebben selectors die semantische waarde bieden, de voorkeur.
   * Als mensen uw URL niet kunnen lezen, kan een zoekmachine dat ook niet.
   * Bijvoorbeeld:

     `mybrand.com/products/product-detail.product-category.product-name.html`
heeft de voorkeur boven `mybrand.com/products/product-detail.1234.html`

* Vermijd waar mogelijk subdomeinen, omdat zoekmachines deze als verschillende entiteiten behandelen, waardoor de SEO-waarde van de site wordt gefragmenteerd.

   * Gebruik in plaats daarvan subpaden op het eerste niveau. Gebruik bijvoorbeeld `www.mybrand.com/es/home.html` in plaats van `es.mybrand.com/home.html`.

   * Plan de inhoudshiërarchie zodanig dat deze overeenkomt met de manier waarop de inhoud wordt weergegeven, volgens deze richtlijn.

* De doeltreffendheid van trefwoorden in URL&#39;s neemt af naarmate de lengte van de URL en de positie van het trefwoord toenemen. Korter is dus beter.

   * Gebruik technieken en functies voor het verkorten van URL&#39;s die door AEM worden geboden om overbodige URL-onderdelen te verwijderen.
   * `mybrand.com/en/myPage.html` heeft bijvoorbeeld de voorkeur boven `mybrand.com/content/my-brand/en/myPage.html`.

* Gebruik canonieke URL&#39;s.

   * Wanneer u een URL vanuit verschillende paden of met verschillende parameters of selectors kunt bedienen, moet u ervoor zorgen dat u een tag `rel=canonical` op de pagina gebruikt.

   * Neem canonieke URL&#39;s op in de code voor de AEM sjabloon.

* Pas waar mogelijk URL&#39;s aan paginatitels aan.

   * Contentauteurs moeten worden aangemoedigd deze praktijk toe te passen.

* Ondersteun hoofdlettergevoeligheid in URL-aanvragen.

   * Configureer de Dispatcher om alle binnenkomende verzoeken als kleine letters te herschrijven.
   * Train contentauteurs om alle pagina&#39;s met kleine letters te maken.

* Zorg ervoor dat elke pagina slechts vanaf één protocol wordt aangeboden.

   * Soms worden sites aangeboden via `http` totdat een gebruiker een pagina bereikt met bijvoorbeeld een uitcheckformulier of een aanmeldingsformulier, waarna naar `https` wordt omgeschakeld. Als de gebruiker bij het koppelen van deze pagina terug kan keren naar `http` pagina&#39;s en deze kan openen via `https` , worden deze door het zoekprogramma bijgehouden als twee aparte pagina&#39;s.

   * Google geeft momenteel de voorkeur aan `https`-pagina&#39;s boven `http`-pagina&#39;s. Ze helpen het leven van iedereen makkelijker te maken om de hele site te bedienen `https` .

### Serverconfiguratie {#server-configuration}

Bij serverconfiguratie kunt u de volgende stappen uitvoeren om ervoor te zorgen dat alleen de juiste content wordt verkend:

* Gebruik een `robots.txt`-bestand om te voorkomen dat content die niet moet worden geïndexeerd, wordt verkend.

   * Blokkeer **alle** verkenningen in testomgevingen.

* Wanneer u een nieuwe site met bijgewerkte URL&#39;s start, implementeert u 301-omleidingen om ervoor te zorgen dat uw bestaande SEO-classificatie niet verloren gaat.
* Neem een favicon op voor uw site.
* Implementeer een XML-sitemap om het voor zoekprogramma&#39;s eenvoudiger te maken om door uw inhoud te kruipen. Neem een mobiele sitemap op voor mobiele en/of responsieve sites.

## Configuraties AEM {#aem-configurations}

Deze sectie beschrijft de implementatiestappen om AEM met de volgende aanbevelingen te vormen SEO.

### Selectors voor schuiven gebruiken {#using-sling-selectors}

Eerder, was het gebruiken van vraagparameters de erkende praktijk toen het bouwen van een toepassing van het ondernemingsWeb.

De afgelopen jaren is het steeds vaker zo dat parameters werden verwijderd om URL&#39;s leesbaarder te maken. Op vele platforms, impliceert dit verwijderingsproces het uitvoeren van omleidingen op de Webserver of het Netwerk van de Levering van de Inhoud (CDN), maar het Sling maakt proces ongecompliceerd. Sling-selectors:

* Verbeteren de leesbaarheid van URL&#39;s.
* Hiermee kunt u uw pagina&#39;s in cache plaatsen op de Dispatcher en de beveiliging verbeteren.
* Hiermee kunt u de inhoud rechtstreeks adresseren, in plaats van een algemeen servlet te hebben dat inhoud ophaalt. Het verleent u de voordelen van ACLs die u op uw bewaarplaats en filters toepast die u op Dispatcher toepast.

#### Selectors voor servlets gebruiken {#using-selectors-for-servlets}

AEM biedt ons twee opties bij het schrijven van servlets:

* **bin**-servlets
* **Sling**-servlets

In de volgende voorbeelden ziet u hoe u servlets kunt registreren die zowel deze patronen als het voordeel volgen dat wordt opgedaan door het gebruik van Sling servlets.

#### Bin servlets (één niveau omlaag) {#bin-servlets-one-level-down}

**Bin**-servlets volgen het patroon dat vele ontwikkelaars kennen via J2EE-programmering. De servlet wordt geregistreerd bij een specifiek weg die, in AEM, gewoonlijk onder `/bin` is, en u haalt de noodzakelijke verzoekparameters uit het vraagkoord.

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
* De aanwezigheid van queryparameters in de URL betekent dat de Dispatcher de reactie niet in de cache kan plaatsen.
* Als u deze servlet wilt beveiligen, implementeert u uw eigen aangepaste beveiligingslogica in de servlet.
* De Dispatcher moet (zorgvuldig) zijn geconfigureerd om `/bin/myApp/myServlet` beschikbaar te maken. Als `/bin` gewoon beschikbaar wordt gemaakt, is toegang mogelijk tot bepaalde servlets die niet toegankelijk mogen zijn voor bezoekers van de site.

#### Serlets verkopen (één niveau omlaag) {#sling-servlets-one-level-down}

Met **Sling**-servlets kunt u uw servlet op de omgekeerde manier registreren. In plaats van een servlet te richten en de inhoud te specificeren u servlet zou willen teruggeven gebaseerd op de vraagparameters, richt u de inhoud die u wilt. En u geeft de servlet op die de inhoud moet renderen op basis van selectors voor bloeden.

De SCR-annotatie voor dit type servlet ziet er ongeveer als volgt uit:

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json", methods="GET")
```

In dit geval is de bron die de URL-adressen - een instantie van de `myPageType` -bron - automatisch toegankelijk in het servlet. Om tot het toegang te hebben, roept u het volgende:

```
Resource myPage = req.getResource();
```

De resulterende URL die wordt gebruikt, ziet er ongeveer als volgt uit:

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

De voordelen van deze aanpak zijn de volgende:

* U kunt SEO-waarde &quot;inbakken&quot; die afkomstig is van de semantiek die aanwezig is in uw sitehiërarchie en paginanaam.
* Aangezien er geen queryparameters aanwezig zijn, kan de Dispatcher de reactie in cache plaatsen. Als de pagina wordt geactiveerd en de geadresseerde pagina wordt bijgewerkt, wordt deze cache ongeldig.
* Alle ACLs die op `/content/my-brand/my-page` wordt toegepast komt in werking wanneer een gebruiker probeert om tot dit servlet toegang te hebben.
* De Dispatcher is al geconfigureerd om deze inhoud te bedienen als functie van het bedienen van de website. Geen extra configuratie wordt vereist.

### URL herschrijven {#url-rewriting}

In AEM worden al uw webpagina&#39;s opgeslagen onder `/content/my-brand/my-content`. Hoewel deze locatie nuttig is vanuit het oogpunt van gegevensbeheer in de opslagplaats, is het niet noodzakelijk hoe u uw klanten uw site wilt laten zien. En, kan het met de SEO richtlijn strijdig zijn om URLs zo kort mogelijk te houden. Bovendien kunt u meerdere websites vanuit hetzelfde AEM en verschillende domeinnamen bedienen.

In deze sectie worden de opties besproken die in AEM beschikbaar zijn voor het beheer van deze URL&#39;s en het op een beter leesbare en meer SEO-vriendelijke manier presenteren van deze URL&#39;s aan gebruikers.

#### Vanity URL&#39;s {#vanity-urls}

Als een auteur wil dat een pagina voor promotiedoeleinden vanaf een tweede locatie toegankelijk is, kunnen de vanity-URL&#39;s van AEM, die per pagina worden gedefinieerd, nuttig zijn. Als u een vanity-URL voor een pagina wilt toevoegen, gaat u naar deze URL in de **Sites**-console en bewerkt u de pagina-eigenschappen. Onder aan het tabblad **Basic** ziet u een sectie waar vanity-URL&#39;s kunnen worden toegevoegd. Houd er rekening mee dat als de pagina toegankelijk is via meer dan één URL, de SEO-waarde van de pagina wordt gefragmenteerd. Daarom moet een canonieke URL-tag aan de pagina worden toegevoegd om dit probleem te voorkomen.

#### Gelokaliseerde paginanamen {#localized-page-names}

U kunt gelokaliseerde paginanamen aan gebruikers van vertaalde inhoud willen tonen. Bijvoorbeeld:

* In plaats van een Spaanstalige gebruiker te laten navigeren naar:
  `www.mydomain.com/es/home.html`

* Zou het beter zijn als de URL er als volgt uitziet:
  `www.mydomain.com/es/casa.html`.

De uitdaging bij het lokaliseren van de naam van de pagina is dat veel van de lokalisatieprogramma&#39;s die beschikbaar zijn op het AEM-platform, erop vertrouwen dat de paginanamen in verschillende landinstellingen overeenkomen, zodat de inhoud gesynchroniseerd blijft.

Met de eigenschap `sling:alias` kunt u ook Adobe taart gebruiken. U kunt `sling:alias` als een eigenschap toevoegen aan elke bron om een aliasnaam voor de bron toe te staan. In het vorige voorbeeld zou u het volgende hebben:

* Een pagina in het JCR op:
  `…/es/home`

* Voeg er vervolgens een eigenschap aan toe:
  `sling:alias` = `casa`

Dankzij deze workflow kunnen de AEM vertaalhulpmiddelen, zoals de beheerder van meerdere sites, een relatie onderhouden tussen:

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
( `org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* Is de eigenschap
  **Mapping Location** ( `resource.resolver.map.location`)

* standaard ingesteld op `/etc/map`.

Toewijzingsdefinities kunnen op deze locatie worden toegevoegd om binnenkomende aanvragen toe te wijzen, URL&#39;s op pagina&#39;s in AEM te herschrijven of beide.

Als u een toewijzing wilt maken, maakt u een knooppunt `sling:Mapping` op deze locatie onder `/http` of `/https` . Gebaseerd op de eigenschappen `sling:match` en `sling:internalRedirect` die op dit knooppunt zijn ingesteld, zal AEM al het verkeer voor de overeenkomstige URL omleiden naar de waarde die in de eigenschap `internalRedirect` is opgegeven.

Hoewel deze benadering wordt beschreven in de officiële documentatie AEM en Sling, is de reguliere-expressieondersteuning die door deze implementatie wordt geboden beperkt in bereik in vergelijking met de opties die beschikbaar zijn via `SlingResourceResolver` rechtstreeks. Bovendien kan het op deze manier implementeren van toewijzingen leiden tot problemen met Dispatcher-cachevalidatie.

Hier volgt een voorbeeld van hoe dit probleem optreedt:

1. Een gebruiker bezoekt uw website en vraagt `https://www.mydomain.com/my-page.html` aan.
1. De Dispatcher stuurt dit verzoek door naar de publicatieserver.
1. Met behulp van `/etc/map` zet de publicatieserver deze aanvraag om naar `/content/my-brand/my-page` en wordt de pagina gerenderd.

1. De Dispatcher plaatst de reactie in cache op `/my-page.html` en geeft de reactie aan de gebruiker.
1. Een auteur van inhoud wijzigt deze pagina en activeert deze.
1. De Dispatcher flush-agent verzendt een verzoek tot validatie voor `/content/my-brand/my-page`**.** Omdat de Dispatcher geen pagina heeft die in het cachegeheugen is opgeslagen op dit pad, blijft de oude inhoud in het cachegeheugen opgeslagen en is deze standaard niet beschikbaar.

Er zijn manieren om aangepaste verstuurings-spoelregels te configureren die de kortere URL toewijzen aan de langere URL ten behoeve van cachevalidatie.

Er is echter ook een eenvoudigere manier om deze kwestie te beheren:

1. **Regels voor SlingResourceResolver**

   Met behulp van de webconsole (bijvoorbeeld localhost:4502/system/console/configMgr) kunt u de Sling Resource Resolver configureren:

   * **Apache Sling Resource Resolver Factory**

     `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.

   De Adobe adviseert dat u de afbeeldingen bouwt die worden vereist om URLs als regelmatige uitdrukkingen te verkorten, dan deze configuraties onder een OsgiConfignode, `config.publish` te bepalen die in uw bouwstijl inbegrepen is.

   In plaats van uw toewijzingen te definiëren in `/etc/map`, kunt u deze rechtstreeks toewijzen aan de eigenschap **URL Mappings** (`resource.resolver.mapping`):

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   In dit eenvoudige voorbeeld verwijdert u `/content/my-brand/` van het begin van elke URL waar dit aanwezig is.

   Er wordt een URL geconverteerd:

   * Van `/content/my-brand/my-page.html`
   * Naar gewoon `/my-page.html`

   Deze conversie is in overeenstemming met de aanbevolen procedure om URL&#39;s zo kort mogelijk te houden.

1. **URL-uitvoer op pagina&#39;s toewijzen**

   Nadat u de toewijzingen in de Apache Sling Resource Resolver hebt gedefinieerd, gebruikt u deze toewijzingen in uw componenten om ervoor te zorgen dat de URL&#39;s die u uitvoert op uw pagina&#39;s kort en getijdenig zijn. U kunt dit onderhoud uitvoeren met de kaartfunctie van de `ResourceResolver` .

   Als u bijvoorbeeld een aangepaste navigatiecomponent implementeerde die de onderliggende elementen van de huidige pagina opsomt, kunt u de toewijzingsmethode als volgt gebruiken:

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Mod Apache HTTP Server_rewrite {#apache-http-server-mod-rewrite}

Tot nu toe hebt u toewijzingen geïmplementeerd samen met de logica in uw componenten om deze toewijzingen te gebruiken wanneer u URL&#39;s op pagina&#39;s uitvoert.

Het laatste stuk aan de puzzel is het afhandelen van deze verkorte URL&#39;s wanneer ze naar de Dispatcher komen, waar `mod_rewrite` in spel komt. Het grootste voordeel aan het gebruiken van `mod_rewrite` is dat URLs terug naar hun lange vorm *in kaart wordt gebracht alvorens* zij worden verzonden naar de module van Dispatcher. Deze stroom betekent dat de Dispatcher de lange URL opvraagt bij de publicatieserver en de URL overeenkomstig in de cache plaatst. Daarom kunnen alle Dispatcher-aanvragen die afkomstig zijn van de publicatieserver, deze inhoud ongeldig maken.

Om deze regels te implementeren, kunt u `RewriteRule`-elementen toevoegen onder uw virtuele host in de Apache HTTP Server-configuratie. Als u de verkorte URL&#39;s uit het vorige voorbeeld wilt uitbreiden, kunt u een regel implementeren die er als volgt uitziet:

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Canonical URL tags {#canonical-url-tags}

Canonieke URL-tags zijn koppelingstags die in de kop van een HTML-document worden geplaatst om te verduidelijken hoe zoekmachines een pagina moeten behandelen terwijl de content wordt geïndexeerd. Het voordeel dat ze bieden, is ervoor te zorgen dat (verschillende versies van) een pagina als hetzelfde worden geïndexeerd, zelfs als de URL naar de pagina verschillen kan bevatten.

Als een site bijvoorbeeld een printervriendelijke versie van een pagina zou aanbieden, zou een zoekmachine deze pagina mogelijk afzonderlijk van de gewone versie van de pagina indexeren. De canonieke tag vertelt de zoekmachine dat ze hetzelfde zijn.

Voorbeelden:

* `https://www.mydomain.com/my-brand/my-page.html`
* `https://www.mydomain.com/my-brand/my-page.print.html`

Beide zouden de volgende tag op de kop van de pagina toepassen:

```xml
<link rel="canonical" href="my-brand/my-page.html"/>
```

De `href` kan relatief of absoluut zijn. De code moet worden opgenomen in de paginamarkering om de canonieke URL voor de pagina te bepalen en deze tag uit te voeren.

### De Dispatcher configureren voor hoofdlettergevoeligheid {#configuring-the-dispatcher-for-case-insensitivity}

U kunt het beste alle pagina&#39;s met kleine letters aanbieden. U wilt echter niet dat een gebruiker een 404-foutmelding krijgt wanneer hij of zij uw website opent met hoofdletters in de URL. Daarom raadt Adobe u aan een herschrijvingsregel toe te voegen in de Apache HTTP Server-configuratie om alle binnenkomende URL&#39;s toe te wijzen aan kleine letters. Ook moeten auteurs van inhoud worden getraind om hun pagina&#39;s met kleine letters te maken.

Om Apache te configureren om al het binnenkomend verkeer te forceren om kleine letters te gebruiken, voegt u het volgende toe aan de `vhost`-configuratie:

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

Voeg ook het volgende toe boven aan het bestand `htaccess` :

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### Robots.txt implementeren om ontwikkelomgevingen te beschermen {#implementing-robots-txt-to-protect-development-environments}

Zoekmachines *zouden moeten* controleren of er een bestand `robots.txt` aanwezig is in de hoofdmap van de site voordat uw site wordt verkend. Hoewel dit bestand wordt gerespecteerd door grote zoekprogramma&#39;s zoals Google, Yahoo of Bing, hebben sommige buitenlandse zoekprogramma&#39;s dat niet.

De eenvoudigste manier om toegang tot uw gehele site te blokkeren, is een bestand met de naam `robots.txt` in de hoofdmap van de site te plaatsen met de volgende content:

```xml
User-agent: *
Disallow: /
```

In een liveomgeving kunt u ervoor kiezen om bepaalde paden die u niet wilt indexeren, niet toe te staan.

Het probleem met het plaatsen van het `robots.txt` -bestand in de hoofdmap van de site is dat Dispatcher-aanvragen dit bestand mogelijk wissen. URL-toewijzingen plaatsen de hoofdmap van de site waarschijnlijk ook ergens anders dan de `DOCROOT` , zoals gedefinieerd in de Apache HTTP Server-configuratie. Daarom is het gebruikelijk om dit bestand op de auteurinstantie in de hoofdmap van de site te plaatsen en het te repliceren naar de publicatie-instantie.

### Een XML-sitemap maken op AEM {#building-an-xml-sitemap-on-aem}

Verkenners gebruiken XML-sitemaps om de structuur van websites beter te begrijpen. Hoewel er geen enkele garantie is dat het aanbieden van een sitemap leidt tot betere beoordelingen van de SEO, is het een overeengekomen beste praktijk. U kunt handmatig een XML-bestand op de webserver onderhouden dat u als sitemap wilt gebruiken. De Adobe raadt u echter aan de sitemap programmatisch te genereren om ervoor te zorgen dat de sitemap de wijzigingen automatisch weerspiegelt wanneer auteurs inhoud maken.

AEM gebruikt de [ module van de Sitemap van Apache Sling ](https://github.com/apache/sling-org-apache-sling-sitemap) om de sitemaps van XML te produceren, die een brede waaier van opties voor ontwikkelaars en redacteurs verstrekt om een sitemap van plaatsenXML bijgewerkt te houden.

>[!NOTE]
>
>Beschikbaar als productfunctie sinds Adobe Experience Manager versie 6.5.11.0.
> 
>Voor oudere versies kunt u zelf een Sling Server registreren om te luisteren naar een `sitemap.xml` oproep. Gebruik de bron die via de servlet-API wordt geleverd om de huidige pagina en de onderliggende elementen op te zoeken en een `sitemap.xml` -bestand uit te voeren.

De module Apache Sling Sitemap maakt onderscheid tussen een sitemap op hoofdniveau en een geneste sitemap. Beide methoden worden gegenereerd voor elke bron waarvoor de eigenschap `sling:sitemapRoot` is ingesteld op `true` . Over het algemeen worden sitemaps weergegeven met behulp van kiezers op het pad van de sitemap op hoofdniveau van de structuur. Dit is de bron die geen andere voorouder van de sitemap-hoofdmap heeft. Deze sitemap-hoofdmap op hoofdniveau stelt ook de sitemap-index beschikbaar, wat normaal gesproken is wat een site-eigenaar zou configureren in het configuratieportaal van de zoekmachine of zou toevoegen aan de site `robots.txt` .

Neem bijvoorbeeld een site die een sitemaproot op hoofdniveau in `my-page` en een geneste sitemaproot in `my-page/news` definieert om een speciale sitemap voor pagina&#39;s in de nieuwsubstructuur te genereren. De resulterende relevante URL&#39;s zouden

* `https://www.mydomain.com/my-brand/my-page.sitemap-index.xml`
* `https://www.mydomain.com/my-brand/my-page.sitemap.xml`
* `https://www.mydomain.com/my-brand/my-page.sitemap.news-sitemap.html`

>[!NOTE]
>
>De kiezers `sitemap` en `sitemap-index` kunnen problemen opleveren met aangepaste implementaties. Als u de productfunctie niet wilt gebruiken, configureert u uw eigen servlet voor deze kiezers met een waarde `service.ranking` hoger dan 0.

In de standaardconfiguratie biedt het dialoogvenster Pagina-eigenschappen een optie om een pagina te markeren als een sitemaproot en genereert u dus, zoals hierboven beschreven, een sitemap van zichzelf en de onderliggende elementen. Dit gedrag wordt geïmplementeerd door implementaties van de interface `SitemapGenerator` en kan worden uitgebreid door alternatieve implementaties toe te voegen. Aangezien de frequentie waarop de XML-sitemaps opnieuw moeten worden gegenereerd afhankelijk is van de workflows en werklasten voor het schrijven van inhoud, verzendt het product echter geen `SitemapScheduler` -configuratie. Als zodanig maakt het de functie effectief opt-in.

Om de achtergrondtaak in te schakelen die de XML-sitemaps genereert, moet een `SitemapScheduler` zijn geconfigureerd. Hiertoe maakt u een OSGI-configuratie voor de PID `org.apache.sling.sitemap.impl.SitemapScheduler` . De plannerexpressie `0 0 0 * * ?` kan worden gebruikt als beginpunt om alle XML-sitemaps eenmaal per dag om middernacht opnieuw te genereren.

![ Apache Sling Sitemap - Planner ](assets/sling-sitemap-scheduler.png)

De sitemap-generatietaak kan zowel op auteur- als op publicatielagen worden uitgevoerd. Gewoonlijk wordt het aanbevolen de generatie uit te voeren op instanties van de publicatielaag, aangezien er alleen daar goede canonieke URL&#39;s kunnen worden gegenereerd (omdat de regels voor het toewijzen van resources aan slingerend doorgaans alleen aanwezig zijn op instanties van de publicatielaag). Nochtans, is het mogelijk om in een douaneimplementatie van het externaliseringsmechanisme te stoppen dat wordt gebruikt om canonical URLs te produceren door de [ SitemapLinkExternalAlizer ](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/sitemap/externalizer/SitemapLinkExternalizer.html) interface uit te voeren. Als een aangepaste implementatie de canonieke URL&#39;s van een sitemap kan genereren voor de instanties van de auteurslaag, kan `SitemapScheduler` worden geconfigureerd voor de modus voor uitvoeren van de auteur. En, kan de de generatiewerkbelasting van XML sitemap over de instanties van de cluster van de auteursdienst worden verdeeld. In dit scenario, moet de voorzichtigheid worden besteed aan de behandeling van inhoud die nog niet is gepubliceerd, is gewijzigd, of slechts zichtbaar aan een beperkte groep gebruikers is.

AEM Sites bevat een standaardimplementatie van een `SitemapGenerator` die een boomstructuur van pagina&#39;s doorloopt om een sitemap te genereren. Het is vooraf geconfigureerd om alleen de canonieke URL&#39;s van een site en eventuele taalalternatieven uit te voeren, indien beschikbaar. Het kan ook worden gevormd om de laatste gewijzigde datum van een pagina indien nodig te omvatten. Om dit te doen, laat _toe voeg Laatste Gewijzigde_ optie van de _Adobe AEM SEO toe - de Configuratie van de Sitemap van de Boom van de Pagina_ en selecteer a _Laatste Gewijzigde Source_. Wanneer de Sitemaps op de publicatielijst worden gegenereerd, wordt aangeraden de datum `cq:lastModified` te gebruiken.

![ Adobe AEM SEO - de Configuratie van de Generator van de Sitemap van de Paginaboom ](assets/sling-sitemap-pagetreegenerator.png)

Om de inhoud van een sitemap te beperken, kunnen de volgende de dienstinterfaces worden uitgevoerd wanneer nodig:

* [ SitemapPageFilter ](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/sitemap/SitemapPageFilter.html) kan worden uitgevoerd om pagina&#39;s van de plaatsen van XML te verbergen die door de specifieke de sitemapgenerator van AEM Sites worden geproduceerd
* a [ SitemapProductFilter ](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/sitemap/SitemapProductFilter.html) of [ SitemapCategoryFilter ](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/sitemap/SitemapCategoryFilter.html) kan worden uitgevoerd om producten of categorieën van de sitemaps van XML uit te filteren die door de [ Commerce integration frameworken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/home.html) specifieke sitemapgenerators worden geproduceerd

Als de standaardimplementaties niet werken aan een bepaald gebruiksgeval of als de extensiepunten niet flexibel genoeg zijn, implementeert u een aangepaste instructie `SitemapGenerator` om de volledige controle over de inhoud van een gegenereerde sitemap te verkrijgen. In het volgende voorbeeld wordt de logica van de standaardimplementatie voor AEM Sites gebruikt. Het gebruikt [ ResourceTreeSitemapGenerator ](https://javadoc.io/doc/org.apache.sling/org.apache.sling.sitemap/latest/org/apache/sling/sitemap/spi/generator/ResourceTreeSitemapGenerator.html) als uitgangspunt om een boom van pagina&#39;s te oversteken:

```
import java.util.Optional;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.sitemap.SitemapException;
import org.apache.sling.sitemap.builder.Sitemap;
import org.apache.sling.sitemap.builder.Url;
import org.apache.sling.sitemap.spi.common.SitemapLinkExternalizer;
import org.apache.sling.sitemap.spi.generator.ResourceTreeSitemapGenerator;
import org.apache.sling.sitemap.spi.generator.SitemapGenerator;
import org.jetbrains.annotations.NotNull;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.adobe.aem.wcm.seo.sitemap.PageTreeSitemapGenerator;
import com.day.cq.wcm.api.Page;

@Component(
    service = SitemapGenerator.class,
    property = { "service.ranking:Integer=20" }
)
public class SitemapGeneratorImpl extends ResourceTreeSitemapGenerator {

    private static final Logger LOG = LoggerFactory.getLogger(SitemapGeneratorImpl.class);

    @Reference
    private SitemapLinkExternalizer externalizer;
    @Reference
    private PageTreeSitemapGenerator defaultGenerator;

    @Override
    protected void addResource(@NotNull String name, @NotNull Sitemap sitemap, Resource resource) throws SitemapException {
        Page page = resource.adaptTo(Page.class);
        if (page == null) {
            LOG.debug("Skipping resource at {}: not a page", resource.getPath());
            return;
        }
        String location = externalizer.externalize(resource);
        Url url = sitemap.addUrl(location + ".html");
        // add any additional content to the Url like lastmod, change frequency, and so on
    }

    @Override
    protected final boolean shouldFollow(@NotNull Resource resource) {
        return super.shouldFollow(resource)
            && Optional.ofNullable(resource.adaptTo(Page.class)).map(this::shouldFollow).orElse(Boolean.TRUE);
    }

    private boolean shouldFollow(Page page) {
        // add additional conditions to stop traversing some pages
        return !defaultGenerator.isProtected(page);
    }

    @Override
    protected final boolean shouldInclude(@NotNull Resource resource) {
        return super.shouldInclude(resource)
            && Optional.ofNullable(resource.adaptTo(Page.class)).map(this::shouldInclude).orElse(Boolean.FALSE);
    }

    private boolean shouldInclude(Page page) {
        // add additional conditions to stop including some pages
        return defaultGenerator.isPublished(page)
            && !defaultGenerator.isNoIndex(page)
            && !defaultGenerator.isRedirect(page)
            && !defaultGenerator.isProtected(page);
    }
}
```

Bovendien kan de functionaliteit die voor de sitemaps van XML wordt uitgevoerd ook voor verschillende gebruiksgevallen worden gebruikt, bijvoorbeeld om de canonieke verbinding of de taalalternatieven aan het hoofd van een pagina toe te voegen. Zie [ SeoTags ](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/SeoTags.html) interface voor meer informatie.

### 301 omleidingen maken voor verouderde URL&#39;s {#creating-redirects-for-legacy-urls}

Wanneer u een site met een nieuwe structuur start, is het om twee redenen belangrijk om 301-omleidingen te implementeren en te testen in Apache HTTP Server:

* De verouderde URL&#39;s hebben in de loop der tijd een SEO-waarde opgebouwd. Door een omleiding te implementeren, kan de zoekmachine deze waarde toepassen op de nieuwe URL.
* Gebruikers van uw site hebben mogelijk bladwijzers voor deze pagina&#39;s gemaakt. Door omleidingen te implementeren, weet u zeker dat u de gebruiker naar de pagina op de nieuwe site stuurt die het meest overeenkomt met de locatie op de oude site.

Controleer of de sectie met extra bronnen die volgt op instructies voor het implementeren van 301 omleidingen en een gereedschap waarmee wordt getest of de omleidingen naar verwachting werken.

## Aanvullende bronnen {#additional-resources}

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
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)
