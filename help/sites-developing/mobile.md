---
title: Sites maken voor mobiele apparaten
description: Het maken van een mobiele site lijkt op het maken van een standaardsite, omdat er ook sjablonen en componenten moeten worden gemaakt
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
docset: aem65
legacypath: /content/docs/en/aem/6-0/develop/mobile/mobile
exl-id: 21b2037a-685a-441d-aecd-865884253e03
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '3701'
ht-degree: 0%

---

# Sites maken voor mobiele apparaten{#creating-sites-for-mobile-devices}

{{ue-over-mobile}}

Het maken van een mobiele site lijkt op het maken van een standaardsite, omdat sjablonen en componenten moeten worden gemaakt. Voor meer details bij het creëren van malplaatjes en componenten, zie de volgende pagina&#39;s: [&#x200B; Malplaatjes &#x200B;](/help/sites-developing/templates.md), [&#x200B; Componenten &#x200B;](/help/sites-developing/components.md), en [&#x200B; Begonnen het Ontwikkelen van AEM Sites &#x200B;](/help/sites-developing/getting-started.md). Het belangrijkste verschil bestaat erin de ingebouwde mobiele functies van Adobe Experience Manager (AEM) binnen de site mogelijk te maken. Dit wordt bereikt door een sjabloon te maken die afhankelijk is van het component voor mobiele pagina.

Overweeg gebruikend [&#x200B; ontvankelijk ontwerp &#x200B;](/help/sites-developing/responsive.md), creërend één enkele plaats die veelvoudige het schermgrootte aanpast.

Om begonnen te worden, kunt u een blik bij **hebben wij.Retail Mobiele Plaats van de Demo** die in AEM beschikbaar is.

Ga als volgt te werk om een mobiele site te maken:

1. Maak de pagina-component:

   * Stel de eigenschap `sling:resourceSuperType` in op `wcm/mobile/components/page`
Op deze manier is de component afhankelijk van de component voor mobiele pagina.

   * Maak de `body.jsp` met de projectspecifieke logica.

1. Maak de paginasjabloon:

   * Stel de eigenschap `sling:resourceType` in op de nieuwe paginacomponent.
   * Stel de eigenschap `allowedPaths` in.

1. Maak de ontwerppagina voor de site.
1. Maak de hoofdpagina van de site onder het knooppunt `/content` :

   * Stel de eigenschap `cq:allowedTemplates` in.
   * Stel de eigenschap `cq:designPath` in.

1. In de paginaeigenschappen van de pagina van de plaatswortel, plaats de apparatengroepen in **Mobiele** tabel.
1. Maak de sitepagina&#39;s met de nieuwe sjabloon.

De component voor mobiele pagina ( `/libs/wcm/mobile/components/page`):

* Voegt het **Mobiele** lusje aan de dialoog van de paginaeigenschappen toe.
* Via zijn `head.jsp` haalt het de huidige mobiele apparatengroep van het verzoek terug en als een apparatengroep wordt gevonden, gebruikt de methode van de groep `drawHead()` om de bijbehorende mededinger van de apparatengroep in de component (slechts in auteurswijze) en de het teruggeven CSS van de apparatengroep te omvatten.

>[!NOTE]
>
>De wortelpagina van de mobiele plaats moet op niveau 1 van de knoophiërarchie zijn, en wordt geadviseerd om onder de /content knoop te zijn.

## Een mobiele site maken met beheer van meerdere sites {#creating-a-mobile-site-with-the-multi-site-manager}

Met MSM (Multi Site Manager) kunt u een live mobiele kopie van een standaardsite maken. De standaardsite wordt automatisch getransformeerd naar een mobiele site: de mobiele site heeft alle functies van de mobiele sites (bijvoorbeeld een editie in een emulator) en kan worden beheerd in synchronisatie met de standaardsite. Verwijs naar de sectie [&#x200B; Creërend Levend Exemplaar voor verschillende Kanalen &#x200B;](/help/sites-administering/msm.md) in de Multi pagina van de Manager van de Plaats.

## Server-Side Mobile-API {#server-side-mobile-api}

De Java™-pakketten met de mobiele klassen zijn:

* [&#x200B; com.day.cq.wcm.mobile.api &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/mobile/api/device/capability/package-summary.html) - bepaalt MobileConstants.
* [&#x200B; com.day.cq.wcm.mobile.api.device &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/mobile/api/device/package-summary.html) - bepaalt Apparaat, DeviceGroup, en DeviceGroupList.
* [&#x200B; com.day.cq.wcm.mobile.api.device.capabilities &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/mobile/api/device/capability/package-summary.html) - bepaalt DeviceCapability.
* [&#x200B; com.day.cq.wcm.mobile.api.wurfl &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/workflow/api/package-summary.html) - bepaalt WurflQueryEngine.
* [&#x200B; com.day.cq.wcm.mobile.core &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/mobile/core/package-summary.html) - bepaalt MobileUtil, die diverse nutsmethodes verstrekt die rond Mobiel WCM draaien.

### Mobiele componenten {#mobile-components}

**Wij.Retail Mobiele Plaats van de Demo** gebruikt de volgende mobiele componenten die onder `/libs/foundation/components` worden gevestigd:

<table>
 <tbody>
  <tr>
   <td>Naam</td>
   <td>Groep</td>
   <td>Kenmerken</td>
  </tr>
  <tr>
   <td>mobiele voettekst</td>
   <td>verborgen</td>
   <td>- voettekst</td>
  </tr>
  <tr>
   <td>mobileimage</td>
   <td>Mobiel</td>
   <td>- gebaseerd op de component van de beeldstichting <br /> - geeft een beeld terug als het apparaat <br /> geschikt is </td>
  </tr>
  <tr>
   <td>mobiele</td>
   <td>Mobiel</td>
   <td>- gebaseerd op de component van de lijststichting <br /> - listitem_teaser.jsp geeft een beeld terug als het apparaat geschikt is <br /> </td>
  </tr>
  <tr>
   <td>mobiele</td>
   <td>verborgen</td>
   <td>- gebaseerd op de component van de logostichting <br /> - geeft een beeld terug als het apparaat <br /> geschikt is </td>
  </tr>
  <tr>
   <td>mobilereferentie</td>
   <td>Mobiel</td>
   <td><p>- vergelijkbaar met de stichtingscomponent van de referentie</p> <p>- wijst een component van de textielafbeelding aan mobiletextimage toe één en een beeldcomponent aan mobiel beeld één</p> </td>
  </tr>
  <tr>
   <td>mobiletextimage</td>
   <td>Mobiel</td>
   <td>- gebaseerd op de component van de textielbeeldstichting <br /> - geeft een beeld terug als het apparaat geschikt is</td>
  </tr>
  <tr>
   <td>mobiletopnav</td>
   <td>verborgen</td>
   <td><p>- op basis van de bovenste grondcomponent</p> <p>- alleen tekst wordt weergegeven</p> </td>
  </tr>
 </tbody>
</table>

#### Een mobiele component maken {#creating-a-mobile-component}

Met het AEM mobiele framework kunt u componenten ontwikkelen die gevoelig zijn voor het apparaat dat de aanvraag doet. De volgende codevoorbeelden laten zien hoe u de AEM mobiele API in een componentspaak kunt gebruiken en vooral hoe u dit kunt doen:

* Haal het apparaat op uit de aanvraag:
  `Device device = slingRequest.adaptTo(Device.class);`

* De apparaatgroep ophalen:
  `DeviceGroup deviceGroup = device.getDeviceGroup();`

* Krijg de mogelijkheden van de apparatengroep:
  `Collection<DeviceCapability> capabilities = deviceGroup.getCapabilities();`

* Haal de apparaatkenmerken op (onbewerkte capaciteitstoets/waarden uit de WURFL-database):
  `Map<String,String> deviceAttributes = device.getAttributes();`

* Krijg de apparaat user-agent:
  `String userAgent = device.getUserAgent();`

* Haal de lijst met apparaatgroepen (apparaatgroepen die door de auteur aan de site zijn toegewezen) op van de huidige pagina:
  `DeviceGroupList deviceGroupList = currentPage.adaptTo(DeviceGroupList.class);`

* Controleren of de apparaatgroep afbeeldingen ondersteunt
  `if (deviceGroup.hasCapability(DeviceCapability.CAPABILITY_IMAGES)) {`
...
OF
  `if MobileUtil.hasCapability(request, DeviceCapability.CAPABILITY_IMAGES) {`
...

>[!NOTE]
>
>In een jsp is `slingRequest` beschikbaar via de tag `<sling:defineObjects>` en `currentPage` via de tag `<cq:defineObjects>` .

### Emulators {#emulators}

Emulatorgebaseerde authoring biedt auteurs de mogelijkheid om inhoudspagina&#39;s te maken die bedoeld zijn voor mobiele clients. Bij het ontwerpen van mobiele inhoud wordt hetzelfde principe gehanteerd als bij het op locatie bewerken van WYSIWYG. Auteurs kunnen de weergave van de pagina op een mobiel apparaat alleen zien als ze een pagina met mobiele inhoud bewerken met een apparaatemulator.

Mobiele apparaten emulators zijn gebaseerd op het generieke emulatorframework. Voor meer details, zie [&#x200B; Medewerkers &#x200B;](/help/sites-developing/emulators.md).

De apparatenmededinger toont het mobiele apparaat op de pagina terwijl het gebruikelijke uitgeven (parsys, componenten) binnen het scherm van het apparaat voorkomt. De apparaatemulator is afhankelijk van de apparaatgroepen die voor de site zijn geconfigureerd. Verschillende emulators kunnen worden toegewezen aan een apparaatgroep. Alle emulators zijn vervolgens beschikbaar op de inhoudspagina. Standaard wordt de eerste emulator weergegeven die is toegewezen aan de eerste apparaatgroep die aan de site is toegewezen. Emulators kunnen worden geschakeld via de emulatorcarrousel boven aan de pagina of via de bewerkingsknop van de Sidekick.

**Creërend een mededinger**

Om een mededinger tot stand te brengen, zie [&#x200B; Creërend een Emulator van de Douane Mobiele &#x200B;](/help/sites-developing/emulators.md) in de generische pagina van Emulators.

**Belangrijkste kenmerken van mobiele mededingers**

* Een apparaatgroep bestaat uit een van meerdere emulators: de configuratiepagina van de apparaatgroep, bijvoorbeeld /etc/mobile/groups/touch, bevat de eigenschap `emulators` onder het knooppunt `jcr:content` .
Opmerking: hoewel het mogelijk is dat dezelfde emulator tot verschillende apparaatgroepen behoort, heeft dit weinig zin.

* Via het configuratiedialoogvenster van de apparaatgroep wordt de eigenschap `emulators` ingesteld met het pad van de gewenste emulators. Bijvoorbeeld: `/libs/wcm/mobile/components/emulators/iPhone4` .

* De emulatorcomponenten (bijvoorbeeld `/libs/wcm/mobile/components/emulators/iPhone4` ) breiden de basis mobiele emulatorcomponent ( `/libs/wcm/mobile/components/emulators/base` ) uit.

* Elke component die de basis mobiele emulator uitbreidt, is beschikbaar voor selectie wanneer u een apparaatgroep configureert. Aangepaste emulators kunnen dus gemakkelijk worden gemaakt of uitgebreid.
* Op verzoek wordt de emulatorimplementatie gebruikt om de pagina weer te geven in de bewerkingsmodus.
* Wanneer de sjabloon van de pagina afhankelijk is van de component voor mobiele pagina, worden de emulatorfuncties automatisch in de pagina geïntegreerd (via de `head.jsp` van de component voor mobiele pagina).

### Apparaatgroepen {#device-groups}

Mobiele apparaatgroepen bieden segmentatie van mobiele apparaten op basis van de mogelijkheden van het apparaat. Een apparaatgroep biedt de informatie die vereist is voor op emulator gebaseerde authoring op de auteurinstantie en voor correcte rendering van inhoud op de publicatie-instantie: zodra auteurs inhoud aan de mobiele pagina hebben toegevoegd en deze hebben gepubliceerd, kan de pagina worden opgevraagd in de publicatie-instantie. In plaats van de emulator-bewerkingsweergave wordt de inhoudspagina weergegeven met een van de geconfigureerde apparaatgroepen. De selectie van de apparatengroep komt voor gebaseerd op [&#x200B; mobiele apparatenopsporing &#x200B;](#devicedetection). De passende apparatengroep verstrekt dan de noodzakelijke het stileren informatie.

De groepen van het apparaat worden bepaald als inhoudspagina&#39;s onder `/etc/mobile/devices` en gebruiken het **Mobiele malplaatje van de Groep van het Apparaat**. Het malplaatje van de apparatengroep dient als configuratiemalplaatje voor de definities van de apparatengroep in de vorm van inhoudspagina&#39;s. De belangrijkste kenmerken zijn:

* Locatie: `/libs/wcm/mobile/templates/devicegroup`
* Toegestaan pad: `/etc/mobile/groups/*`
* Paginacomponent: `wcm/mobile/components/devicegroup`

#### Apparaatgroepen toewijzen aan uw site {#assigning-device-groups-to-your-site}

Wanneer u een mobiele site maakt, moet u apparaatgroepen aan uw site toewijzen. AEM biedt drie apparaatgroepen, afhankelijk van de HTML- en JavaScript-rendermogelijkheden van het apparaat:

* **telefoons van de Eigenschap 0&rbrace;, voor eigenschapapparaten zoals Sony Ericsson W800 met steun voor basis HTML maar geen steun voor beelden en JavaScript.**
* **Slimme** telefoons, voor apparaten zoals BlackBerry® met steun voor fundamentele HTML en beelden, maar geen steun voor JavaScript.

* **aanraak** telefoons, voor apparaten zoals iPad met volledige steun voor HTML, beelden, JavaScript, en apparatenomwenteling.

Aangezien de mededingers met een apparatengroep kunnen worden geassocieerd (zie de sectie [&#x200B; Creërend een Groep van het Apparaat &#x200B;](#creating-a-device-group)), laat het toewijzen van een apparatengroep aan een plaats auteurs toe om tussen de mededingers te selecteren die met de apparatengroep worden geassocieerd om de pagina uit te geven.

U kunt als volgt een apparaatgroep aan uw site toewijzen:

1. In uw browser, ga naar de **Siteadmin** console.
1. Open de wortelpagina van uw mobiele plaats onder **Websites**.
1. Open de pagina-eigenschappen.
1. Selecteer het **Mobiele** lusje:

   * Definieer de apparaatgroepen.
   * Klik **OK**.

>[!NOTE]
>
>Wanneer de apparaatgroepen voor een site zijn gedefinieerd, worden ze door alle pagina&#39;s van de site overgenomen.

#### Apparaatgroepfilters {#device-group-filters}

Filters voor apparaatgroepen definiëren criteria die zijn gebaseerd op de mogelijkheid om te bepalen of een apparaat tot de groep behoort. Wanneer u een apparaatgroep maakt, kunt u de filters selecteren die u wilt gebruiken voor het evalueren van apparaten.

Wanneer AEM een HTTP-aanvraag van een apparaat ontvangt, vergelijkt elk filter dat aan een groep is gekoppeld de mogelijkheden van het apparaat met specifieke criteria. Het apparaat wordt geacht tot de groep te behoren wanneer het alle mogelijkheden heeft die de filters vereisen. Capabilities worden opgehaald uit de WURFL™-database.

Apparaatgroepen kunnen nul of meer filters gebruiken voor capaciteitsdetectie. Een filter kan ook worden gebruikt met meerdere apparaatgroepen. AEM verstrekt een standaardfilter dat bepaalt of het apparaat de mogelijkheden heeft die voor een groep worden geselecteerd:

* CSS
* &#x200B;- en PNG-afbeeldingen JPG
* JavaScript
* Apparaatrotatie

Als de apparatengroep geen filter gebruikt, zijn de geselecteerde mogelijkheden die voor de groep worden gevormd de enige mogelijkheden die een apparaat vereist.

Voor meer informatie, zie [&#x200B; Creërend de Filters van de Groep van het Apparaat &#x200B;](/help/sites-developing/groupfilters.md).

#### Een apparaatgroep maken {#creating-a-device-group}

Maak een apparaatgroep als de groepen die AEM installeren niet aan uw vereisten voldoen.

1. In uw browser, ga naar de **console van Hulpmiddelen**.
1. Creeer een pagina onder **Hulpmiddelen** > **Mobiele** > **Groepen van het Apparaat**. In **creeer de dialoog van de Pagina**:

   * Als **Titel**, ga `Special Phones` in.

   * Als **Naam**, ga `special` in.

   * Selecteer het **Mobiele Malplaatje van de Groep van het Apparaat**.
   * Klik **creëren**.

1. In CRXDE, voeg a **static.css** dossier toe dat de stijlen voor de apparatengroep onder de `/etc/mobile/groups/special` knoop bevat.

1. Open de **Speciale Phones** pagina.
1. Om de apparatengroep te vormen, klik **uitgeven** knoop naast **Montages**.
Op het **Algemene** lusje:

   * **Titel**: de naam van de mobiele apparatengroep.
   * **Beschrijving**: beschrijving van de groep.
   * **gebruiker-agent**: gebruiker-agent koord dat de apparaten tegen worden aangepast. Het is optioneel en kan een regex zijn. Voorbeeld: `BlackBerryZ10`
   * **Mogelijkheden**: bepaalt als de groep beelden, CSS, JavaScript, of apparatenomwenteling kan behandelen.
   * **Minimale Breedte van het Scherm** en **Hoogte**
   * **maak Emulator** onbruikbaar: om de mededinger tijdens inhoud het uitgeven toe te laten/onbruikbaar te maken.

   Op het **Emulators** lusje:

   * **Emulators**: selecteer de mededingers die aan deze apparatengroep worden toegewezen.

   Op het **lusje van Filters**:

   * Als u een filter wilt toevoegen, klikt u op Item toevoegen en selecteert u een filter in de vervolgkeuzelijst.
   * Filters worden geëvalueerd in de volgorde waarin ze worden weergegeven. Wanneer een apparaat niet aan de criteria van een filter voldoet, worden de opeenvolgende filters in de lijst niet geëvalueerd.

1. Klik op OK.

Het dialoogvenster voor de configuratie van groepen mobiele apparaten ziet er als volgt uit:

![&#x200B; screen_shot_2012-02-01at22043pm &#x200B;](assets/screen_shot_2012-02-01at22043pm.png)

#### Aangepaste CSS per apparaatgroep {#custom-css-per-device-group}

Zoals eerder is beschreven, is het mogelijk om een aangepaste CSS te koppelen aan een apparaatgroeppagina, ongeveer zoals de CSS van een ontwerppagina. Deze CSS wordt gebruikt om de apparaatgroepspecifieke rendering van de pagina-inhoud bij auteur en publicatie te beïnvloeden. Deze CSS wordt vervolgens automatisch opgenomen:

* In de pagina op de auteurinstantie, voor elke mededinger die door deze apparatengroep wordt gebruikt.
* Op de pagina op de publicatie-instantie als de gebruikersagent van de aanvraag overeenkomt met een mobiel apparaat in deze specifieke apparaatgroep.

## Apparaatdetectie op de server {#server-side-device-detection}

Gebruik filters en een bibliotheek met apparaatspecificaties om de mogelijkheden te bepalen van het apparaat dat de HTTP-aanvraag uitvoert.

### Apparaatgroepfilters ontwikkelen {#develop-device-group-filters}

Maak een apparaatgroepfilter om een set vereisten voor apparaatmogelijkheden te definiëren. Maak zoveel filters als u nodig hebt om de benodigde groepen apparaatmogelijkheden als doel in te stellen.

Ontwerp uw filters zodat u combinaties ervan kunt gebruiken om de groepen mogelijkheden te bepalen. Gewoonlijk zijn de mogelijkheden van verschillende apparaatgroepen elkaar overlappen. Daarom zou u sommige filters met veelvoudige definities van de apparatengroep kunnen gebruiken.

Nadat u een filter creeert, kunt u het in de groepsconfiguratie gebruiken.

Voor informatie, ga [&#x200B; Creërend de Filters van de Groep van het Apparaat &#x200B;](/help/sites-developing/groupfilters.md).

### De WURFL™-database gebruiken {#using-the-wurfl-database}

AEM gebruikt een beknot versie van het [&#x200B; WURFL &#x200B;](https://wurfl.sourceforge.net/) ™ gegevensbestand aan de mogelijkheden van het vraagapparaat, zoals het schermresolutie of de steun van JavaScript, die op gebruiker-Agent van het apparaat wordt gebaseerd.

De code van XML van het WURFL™- gegevensbestand wordt vertegenwoordigd als knopen onder `/var/mobile/devicespecs` door het `wurfl.xml` dossier bij `/libs/wcm/mobile/devicespecs/wurfl.xml.` te ontleden de uitbreiding aan knopen voorkomt de eerste keer dat de `cq-mobile-core` bundel wordt begonnen.

Apparaatmogelijkheden worden opgeslagen als knoopeigenschappen en knooppunten vertegenwoordigen apparaatmodellen. U kunt query&#39;s gebruiken om de mogelijkheden van een apparaat of gebruikersagent op te halen.

Aangezien het WURFL™ gegevensbestand evolueert, kunt u het moeten aanpassen of vervangen. Als u de database voor mobiele apparaten wilt bijwerken, hebt u de volgende opties:

* Vervang het bestand door de nieuwste versie als u een licentie hebt die dit gebruik toestaat. Zie Een andere WURFL-database installeren.
* Gebruik de versie die in AEM beschikbaar is en vorm een regexp die uw gebruiker-Agent koorden en punten aan een bestaand apparaat WURFL™ aanpast. Zie [&#x200B; Toevoegend op regexp-Gebaseerde gebruiker-Agent het Verstemmen &#x200B;](#adding-a-regexp-based-user-agent-matching).

#### Het testen van de Afbeelding van een Gebruiker-Agent aan Mogelijkheden WURFL™ {#testing-the-mapping-of-a-user-agent-to-wurfl-capabilities}

Wanneer een apparaat toegang krijgt tot uw mobiele site, detecteert AEM het apparaat, wijst het apparaat toe aan een apparaatgroep op basis van zijn mogelijkheden en verstuurt het een weergave van de pagina die overeenkomt met de apparaatgroep. De overeenkomende apparaatgroep bevat de vereiste opmaakgegevens. De toewijzingen kunnen op de Mobiele Gebruiker-Agent Pagina van de Test worden getest:

`https://localhost:4502/etc/mobile/useragent-test.html`

#### Een andere WURFL™-database installeren {#installing-a-different-wurfl-database}

De afgekapte WURFL™-database die met AEM is geïnstalleerd, is een release die dateert van vóór
30 augustus 2011. Als uw versie van WURFL na 30 augustus 2011 is uitgebracht, moet u ervoor zorgen dat uw gebruik voldoet aan uw licentie.

Een WURFL™-database installeren:

1. Maak in CRXDE Lite de volgende map: `/apps/wcm/mobile/devicespecs`
1. Kopieer het WURFL™-bestand naar de map.
1. Wijzig de naam van het bestand in `wurfl.xml` .

AEM het bestand `wurfl.xml` automatisch parseert en de onderliggende knooppunten `/var/mobile/devicespecs` bijwerkt.

>[!NOTE]
>
>Wanneer de volledige WURFL™-database is ingeschakeld, kan het parseren en activeren enkele minuten duren. U kunt de logboeken bekijken voor voortgangsinformatie.

#### Een op regexp gebaseerde overeenstemmende gebruikersagent toevoegen {#adding-a-regexp-based-user-agent-matching}

Voeg een user-agent als regelmatige uitdrukking onder /apps/wcm/mobile/devicespecs/wurfl/regexp toe om aan een bestaand WURFL™ apparatentype te richten.

1. In **CRXDE Lite**, creeer een knoop onder /apps/wcm/mobile/devicespecs/regexp, bijvoorbeeld, `apple_ipad_ver1`.
1. Voeg de volgende eigenschappen toe aan het knooppunt:

   * **regexp**: regelmatige uitdrukking die gebruiker-agenten, bijvoorbeeld, bepaalt.&#42; Mozilla.&#42; iPad.&#42; AppleWebKit.&#42; Safari.&#42;
   * **deviceId**: Apparaatidentiteitskaart zoals bepaald in wurfl.xml, bijvoorbeeld, `apple_ipad_ver1`

De bovenstaande configuratie veroorzaakt apparaten waarvoor de gebruiker-Agent de geleverde regelmatige uitdrukking aanpast om aan apple_ipad_ver1 WURFL™ apparatenidentiteitskaart worden in kaart gebracht, als het bestaat.

## Apparaatdetectie op de client {#client-side-device-detection}

In deze sectie wordt beschreven hoe u de detectie van AEM op de client van het apparaat kunt gebruiken om de weergave van pagina&#39;s te optimaliseren of om de client alternatieve websiteversies te bieden.

AEM ondersteunt apparaatclientdetectie op basis van `BrowserMap` . `BrowserMap` wordt verzonden in AEM als een clientbibliotheek onder `/etc/clientlibs/browsermap` .

`BrowserMap` biedt u drie strategieën waarmee u een alternatieve website aan een client kunt aanbieden. Deze strategie wordt in de volgende volgorde gebruikt:

1. [Alternatieve koppelingen](#providing-alternate-links)
1. [Specifieke URL voor apparaatgroep](#definingdevicegroupspecificurl)
1. [Op kiezer gebaseerde URL](#defining-selector-based-urls)

>[!NOTE]
>
>Voor meer informatie over de integratie van de Bibliotheek van de Cliënt, zie [&#x200B; Gebruikend de Bibliotheken van de HTML van de Cliënt-Kant &#x200B;](/help/sites-developing/clientlibs.md).

### Alternatieve koppelingen opgeven {#providing-alternate-links}

De dienst `PageVariantsProvider` OSGi kan afwisselende verbindingen voor plaatsen produceren die tot de zelfde familie behoren. Als u sites wilt configureren die door de service worden beschouwd, moet een knooppunt `cq:siteVariant` aan het knooppunt `jcr:content` worden toegevoegd vanaf de hoofdmap van de site.

Het knooppunt `cq:siteVariant` moet de volgende eigenschappen hebben:

* `cq:childNodesMapTo` - bepaalt aan welk kenmerk van het koppelingselement de onderliggende knooppunten worden toegewezen; het wordt aanbevolen de inhoud van uw website zodanig te ordenen dat de onderliggende knooppunten van het hoofdknooppunt de basis vormen voor een taalvariant van uw algemene website (bijvoorbeeld `/content/mysite/en` , `/content/mysite/de` ), in welk geval de waarde van de `cq:childNodesMapTo` moet `hreflang` zijn;
* `cq:variantDomain` - geeft aan welk `Externalizer` -domein wordt gebruikt om de absolute URL&#39;s van de paginariabelen te genereren. Als deze waarde niet is ingesteld, worden de paginariabelen gegenereerd met relatieve koppelingen.
* `cq:variantFamily` - geeft aan tot welke familie van websites deze site behoort; meerdere apparaatspecifieke vertegenwoordigingen van dezelfde website moeten tot dezelfde familie behoren;
* `media` - slaat de waarden van het mediakenmerk van het koppelingselement op. Het wordt aanbevolen de naam van de `BrowserMap` registered `DeviceGroups` te gebruiken, zodat de `BrowserMap` -bibliotheek de clients automatisch naar de juiste variant van de website kan doorsturen.

#### PageVariantsProvider en Externalalizer {#pagevariantsprovider-and-externalizer}

Wanneer de waarde van de eigenschap `cq:variantDomain` van een knooppunt `cq:siteVariant` niet leeg is, genereert de service `PageVariantsProvider` absolute koppelingen met deze waarde als een geconfigureerd domein voor de service `Externalizer` . Zorg ervoor dat u de service `Externalizer` configureert op basis van uw instellingen.

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

### Een apparaatgroepspecifieke URL definiëren {#defining-a-device-group-specific-url}

Als u geen alternatieve koppelingen wilt gebruiken, kunt u voor elke `DeviceGroup` een algemene URL configureren. Adobe raadt u aan uw eigen clientbibliotheek te maken die de `browsermap.standard` -clientbibliotheek insluit, maar de apparaatgroepen opnieuw definieert.

BrowserMap is zodanig ontworpen dat de definities van apparaatgroepen kunnen worden overschreven door een apparaatgroep met dezelfde naam te maken en toe te voegen aan het `BrowserMap` -object uit de aangepaste clientbibliotheek.

>[!NOTE]
>
>Voor meer details, zie [&#x200B; Aangepaste BrowserMap &#x200B;](#creatingacustomisedbrowsermap).

### Op kiezers gebaseerde URL&#39;s definiëren {#defining-selector-based-urls}

Als geen van de vorige mechanismen is gebruikt om een alternatieve site voor `BrowserMap` aan te geven, worden kiezers die de namen van de `DeviceGroups` gebruiken, toegevoegd aan de `URL` s. In dat geval moet u uw eigen servlets opgeven die de aanvragen zullen verwerken.

Bijvoorbeeld een apparaat dat `www.example.com/index.html` door `smartphone` BrowserMap wordt geïdentificeerd wordt doorgestuurd naar `www.example.com/index.smartphone.html.`

### BrowserMap gebruiken op uw pagina&#39;s {#using-browsermap-on-your-pages}

Als u de standaardclientbibliotheek BrowserMap in een pagina wilt gebruiken, moet u het `/libs/wcm/core/browsermap/browsermap.jsp` -bestand opnemen met de tag a `cq:include` in de sectie `head` van de pagina.

```xml
<cq:include script="/libs/wcm/core/browsermap/browsermap.jsp" />
```

Naast het toevoegen van de `BrowserMap` clientbibliotheek in uw `JSP` -bestanden, moet u ook een `cq:deviceIdentificationMode` String-eigenschap ingesteld op `client-side` aan het `jcr:content` -knooppunt onder de hoofdmap van uw website toevoegen.

### Standaardgedrag van BrowserMap overschrijven {#overriding-browsermap-s-default-behaviour}

Als u `BrowserMap` zou willen aanpassen - door `DeviceGroups` met voeten te treden of meer sondes toe te voegen - dan zou u uw eigen cliënt-zijbibliotheek moeten tot stand brengen waarin u de `browsermap.standard` cliënt-zijbibliotheek inbedt.

Bovendien moet u de methode `BrowserMap.forwardRequest()` handmatig in uw `JavaScript` -code aanroepen.

>[!NOTE]
>
>Voor meer informatie over de integratie van de Bibliotheek van de Cliënt, zie [&#x200B; Gebruikend de Bibliotheken van de HTML van de Cliënt-Kant &#x200B;](/help/sites-developing/clientlibs.md).

Zodra u uw aangepaste `BrowserMap` cliëntbibliotheek hebt gecreeerd, stelt de Adobe de volgende benadering voor:

1. Een `browsermap.jsp` -bestand maken in uw toepassing

   ```xml
   <%@include file="/libs/foundation/global.jsp" %>
   <%@ taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
   <%@ page import="
       com.day.cq.wcm.api.variants.PageVariant,
       com.day.cq.wcm.api.variants.PageVariantsProvider,
       com.day.cq.wcm.api.devicedetection.DeviceIdentificationMode,
       com.day.cq.wcm.api.WCMMode"
   %>
   <%
       final PageVariantsProvider p = sling.getService(PageVariantsProvider.class);
       if(p == null) {
           throw new IllegalStateException("Missing PageVariantsProvider service");
       }
       for(PageVariant v : p.getVariants(currentPage, slingRequest)) {
           final String curVar = v.getAttributes().get("data-current-variant");
           String media = v.getAttributes().get("media");
           if (media != null) {
               media = media.replaceAll(" ", "");
           }
   %>
       <link
           rel="alternate"
           data-cq-role="site.variant"
           title="<%= xssAPI.encodeForHTMLAttr(v.getTitle()) %>"
           hreflang="<%= xssAPI.encodeForHTMLAttr(v.getAttributes().get("hreflang")) %>"
           media="<%= xssAPI.encodeForHTMLAttr(media) %>"
           href="<%= xssAPI.getValidHref(v.getURL()) %>"
           <% if(curVar != null) { %> data-current-variant="<%= curVar %>"<% } %>
       />
   <%
       }
       Boolean browserMapEnabled = true;
       final DeviceIdentificationMode dim = sling.getService(DeviceIdentificationMode.class);
       String[] selectors  = slingRequest.getRequestPathInfo().getSelectors();
       boolean isPortletRequest = false;
       for (int i = 0; i < selectors.length; i++) {
           if ("portlet".equals(selectors[i])) {
               isPortletRequest = true;
               break;
           }
       }
       if (isPortletRequest) {
           log.debug("Request was made by a portlet container - BrowserMap will not be embedded");
       } else {
           final WCMMode wcmMode = WCMMode.fromRequest(slingRequest);
           boolean shouldIncludeClientLib = false;
           if (WCMMode.EDIT != wcmMode && WCMMode.PREVIEW != wcmMode && WCMMode.DESIGN != wcmMode) {
               if (dim != null) {
                   final String mode = dim.getDeviceIdentificationModeForPage(currentPage);
                   shouldIncludeClientLib = DeviceIdentificationMode.CLIENT_SIDE.equals(mode);
                   if (shouldIncludeClientLib) {
                       browserMapEnabled = (Boolean) request.getAttribute("browsermap.enabled");
                       if (browserMapEnabled == null) {
                           browserMapEnabled = true;
                       }
                   }
               }
           }
   %>
           <c:if test="<%= !browserMapEnabled %>">
               <meta name="browsermap.enabled" content="false">
           </c:if>
           <c:if test="<%= shouldIncludeClientLib %>">
               <meta name="viewport" content="width=device-width, initial-scale=1.0">
               <cq:includeClientLib categories="browsermap.custom"/>
           </c:if>
   <%
       }
   %>
   ```

1. Neem het `broswermap.jsp` -bestand op in de kopsectie.

   ```xml
   <cq:include script="browsermap.jsp" />
   ```

### BrowserMap uitsluiten van bepaalde pagina&#39;s {#excluding-browsermap-from-certain-pages}

Als u de BrowserMap-bibliotheek wilt uitsluiten van sommige van uw pagina&#39;s waarvoor geen clientdetectie nodig is, kunt u een aanvraagkenmerk toevoegen:

```xml
<%
request.setAttribute("browsermap.enabled", false);
%>
```

Hierdoor voegt het script van `/libs/wcm/core/browsermap/browsermap.jsp` een metatag toe aan de pagina, zodat `BrowserMap` geen detectie uitvoert:

```xml
<meta name="browsermap.enabled" content="false">
```

### Een specifieke versie van een website testen {#testing-a-specific-version-of-a-web-site}

Doorgaans leidt het BrowserMap-script bezoekers altijd naar de meest geschikte versie van de website, waarbij bezoekers doorgaans naar het bureaublad of de mobiele site worden omgeleid wanneer dat nodig is.

U kunt het apparaat van elke aanvraag dwingen een specifieke versie van een website te testen door de parameter `device` aan uw URL toe te voegen. Met de volgende URL wordt de mobiele versie van de website Geometrixx Outdoors weergegeven.

`https://localhost:4502/content/geometrixx-outdoors/en.html?wcmmode=disabled&device=smartphone`

>[!NOTE]
>
>De parameter `wcmmode` wordt ingesteld op `disabled` om het gedrag van een publicatie-instantie te simuleren.

De overschrijvende apparaatwaarde wordt opgeslagen in een cookie, zodat u door uw website kunt bladeren zonder de parameter `device` aan elke `URL` toe te voegen.

Als gevolg hiervan moet u dezelfde `URL` aanroepen met de eigenschap `device` set to `browser` om terug te keren naar de bureaubladversie van de website.

>[!NOTE]
>
>BrowserMap slaat de het met voeten treden apparatenwaarde in een koekje genoemd `BMAP_device` op. Als u deze cookie verwijdert, zorgt u ervoor dat CQ de juiste versie van de website aanbiedt op basis van uw huidige apparaat (bijvoorbeeld bureaublad of mobiel).

## Mobiele aanvraagverwerking {#mobile-request-processing}

AEM verwerkt als volgt een aanvraag die is uitgegeven door een mobiel apparaat dat tot de aanraakapparaatgroep behoort:

1. Een iPad verzendt een aanvraag naar de AEM-publicatie-instantie, bijvoorbeeld `https://localhost:4503/content/geometrixx_mobile/en/products.html`
1. AEM bepaalt of de site van de aangevraagde pagina een mobiele site is (door te controleren of de pagina op het eerste niveau `/content/geometrixx_mobile` de component voor de mobiele pagina uitbreidt). Zo ja:
1. AEM kijkt omhoog de apparatenmogelijkheden die op gebruiker-Agent in de verzoekkopbal worden gebaseerd.
1. AEM wijst de apparaatmogelijkheden toe aan de apparaatgroep en stelt `touch` in als de apparaatgroepkiezer.
1. AEM stuurt de aanvraag om naar `https://localhost:4503/content/geometrixx_mobile/en/products.touch.html.`
1. AEM stuurt het antwoord naar de iPad:

   * `products.touch.html` wordt op de gebruikelijke manier gerenderd en kan in cache worden geplaatst.
   * De renderingcomponenten gebruiken kiezers om de presentatie aan te passen.
   * AEM voegt automatisch de mobiele kiezer toe aan alle interne koppelingen op de pagina.

### Statistieken {#statistics}

U kunt statistieken opvragen over het aantal aanvragen dat door mobiele apparaten bij de AEM server is ingediend. Het aantal aanvragen kan worden uitgesplitst:

* per apparaatgroep en -apparaat
* per jaar, maand en dag

De statistieken weergeven:

1. Ga naar de **console van Hulpmiddelen**.
1. Open de **pagina van de Statistieken van het Apparaat** onder **Hulpmiddelen** > **Mobiel**.
1. Klik op de koppeling om de statistieken voor een bepaald jaar, een bepaalde maand of een bepaalde dag weer te geven.

De **Statistieken** pagina kijkt als volgt:

![&#x200B; screen_shot_2012-02-01at24353pm &#x200B;](assets/screen_shot_2012-02-01at24353pm.png)

>[!NOTE]
>
>De **pagina van de Statistieken** wordt gecreeerd de eerste keer een mobiel apparaat tot AEM toegang heeft en ontdekt. Daarvoor is het niet beschikbaar.

Als u een ingang in de statistieken moet produceren, kunt u als volgt te werk gaan:

1. Gebruik een mobiel apparaat of een emulator (bijvoorbeeld https://chrispederick.com/work/user-agent-switcher/ op Firefox).
1. Vraag een mobiele pagina op de auteurinstantie door de auteurswijze onbruikbaar te maken, bijvoorbeeld:
   `https://localhost:4502/content/geometrixx_mobile/en/products.html?wcmmode=disabled`

De **pagina van de Statistieken** is nu beschikbaar.

### Ondersteunende pagina-caching voor koppelingen naar vrienden verzenden {#supporting-page-caching-for-send-link-to-a-friend-links}

Mobiele pagina&#39;s kunnen in Dispatcher in cache worden geplaatst, omdat pagina&#39;s die voor een apparaatgroep worden weergegeven in de pagina-URL worden onderscheiden door de kiezer van de apparaatgroep, bijvoorbeeld `/content/mobilepage.touch.html` . Een aanvraag naar een mobiele pagina zonder kiezer wordt nooit in de cache geplaatst, aangezien in dit geval de apparaatdetectie werkt en ten slotte wordt omgeleid naar de overeenkomende apparaatgroep (of &quot;nomatch&quot; voor dat geval). Een mobiele pagina die wordt weergegeven met een apparaatgroepkiezer, wordt verwerkt door de koppelingenrewriter, die alle koppelingen binnen de pagina herschrijft om ook de apparaatgroepkiezer te bevatten, zodat apparaatdetectie niet opnieuw kan worden uitgevoerd voor elke klik van een reeds gekwalificeerde pagina.

Daarom zou u het volgende scenario kunnen ontmoeten:

Alice van de gebruiker wordt opnieuw gericht aan `coolpage.feature.html`, en verzendt die URL naar vriendBob die tot het met een verschillende cliënt toegang heeft die in de `touch` apparatengroep valt.

Als `coolpage.feature.html` van een front-end geheime voorgeheugen wordt gediend, krijgt AEM geen kans om het verzoek te analyseren om te weten te komen dat de mobiele selecteur niet de nieuwe gebruiker-Agent aanpast, en Bob krijgt de verkeerde vertegenwoordiging.

Als u dit wilt oplossen, kunt u een eenvoudige selectie-UI op de pagina&#39;s opnemen, waar eindgebruikers de apparaatgroep die is geselecteerd door AEM kunnen overschrijven. In het bovenstaande voorbeeld kan de eindgebruiker met een koppeling (of een pictogram) op de pagina naar `coolpage.touch.html` schakelen als hij of zij van mening is dat het apparaat hiervoor geschikt is.
