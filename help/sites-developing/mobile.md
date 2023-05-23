---
title: Sites maken voor mobiele apparaten
seo-title: Creating Sites for Mobile Devices
description: Het maken van een mobiele site lijkt op het maken van een standaardsite, omdat er ook sjablonen en componenten moeten worden gemaakt
seo-description: Creating a mobile site is similar to creating a standard site as it also involves creating templates and components
uuid: 6b19042c-03f1-4e33-970e-475f9fb8c5fb
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: 0aabfb0a-ef9c-4b06-b698-61cad101c3c1
docset: aem65
legacypath: /content/docs/en/aem/6-0/develop/mobile/mobile
exl-id: 21b2037a-685a-441d-aecd-865884253e03
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3840'
ht-degree: 0%

---

# Sites maken voor mobiele apparaten{#creating-sites-for-mobile-devices}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

Het maken van een mobiele site lijkt op het maken van een standaardsite, omdat sjablonen en componenten moeten worden gemaakt. Raadpleeg de volgende pagina&#39;s voor meer informatie over het maken van sjablonen en componenten: [Sjablonen](/help/sites-developing/templates.md), [Componenten](/help/sites-developing/components.md) en [Aan de slag met het ontwikkelen van AEM Sites](/help/sites-developing/getting-started.md). Het belangrijkste verschil bestaat erin de AEM ingebouwde mobiele functies binnen de site mogelijk te maken. Dit wordt bereikt door een sjabloon te maken die afhankelijk is van het component voor mobiele pagina.

U moet ook overwegen om [responsief ontwerp](/help/sites-developing/responsive.md)en één site maken die geschikt is voor meerdere schermgrootten.

Als u aan de slag wilt gaan, kunt u de **We.Retail Mobile Demo Site** dat beschikbaar is in AEM.

Ga als volgt te werk om een mobiele site te maken:

1. Maak de pagina-component:

   * Stel de `sling:resourceSuperType` eigenschap aan `wcm/mobile/components/page`
Op deze manier is de component afhankelijk van de component voor mobiele pagina.

   * Maak de `body.jsp` met de projectspecifieke logica.

1. Maak de paginasjabloon:

   * Stel de `sling:resourceType` aan de nieuw gemaakte paginacomponent.
   * Stel de `allowedPaths` eigenschap.

1. Maak de ontwerppagina voor de site.
1. De hoofdpagina van de site maken onder de `/content` knooppunt:

   * Stel de `cq:allowedTemplates` eigenschap.
   * Stel de `cq:designPath` eigenschap.

1. Stel in de pagina-eigenschappen van de hoofdpagina van de site de apparaatgroepen in in de **Mobiel** tab.
1. Maak de sitepagina&#39;s met de nieuwe sjabloon.

De component mobiele pagina ( `/libs/wcm/mobile/components/page`):

* Hiermee voegt u de **Mobiel** aan het dialoogvenster Pagina-eigenschappen.
* Via haar `head.jsp`, wordt de huidige groep mobiele apparaten opgehaald uit de aanvraag en wordt de groep gebruikt als een apparaatgroep wordt gevonden `drawHead()` methode om de daaraan gekoppelde emulator van de apparaatgroep in de component op te nemen (alleen in de auteursmodus) en de CSS van de apparaatgroep.

>[!NOTE]
>
>De wortelpagina van de mobiele plaats moet op niveau 1 van de knoophiërarchie zijn, en wordt geadviseerd om onder de /content knoop te zijn.

## Een mobiele site maken met Beheer van meerdere sites {#creating-a-mobile-site-with-the-multi-site-manager}

Met MSM (Multi Site Manager) kunt u een live mobiele kopie van een standaardsite maken. De standaardsite wordt automatisch getransformeerd naar een mobiele site: de mobiele site beschikt over alle functies van de mobiele sites ( bijvoorbeeld editie in een emulator ) en kan worden beheerd in synchronisatie met de standaardsite . Zie de sectie [Een actieve kopie maken voor verschillende kanalen](/help/sites-administering/msm.md) op de pagina Multi-Site Manager.

## Server-Side Mobile-API {#server-side-mobile-api}

De Java-pakketten met de mobiele klassen zijn:

* [com.day.cq.wcm.mobile.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/api/device/capability/package-summary.html) - definieert MobileConstants.
* [com.day.cq.wcm.mobile.api.device](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/api/device/package-summary.html) - definieert Device, DeviceGroup en DeviceGroupList.
* [com.day.cq.wcm.mobile.api.device.capabilities](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/api/device/capability/package-summary.html) - definieert DeviceCapability.
* [com.day.cq.wcm.mobile.api.wurfl](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/workflow/api/package-summary.html) - definieert WurflQueryEngine.
* [com.day.cq.wcm.mobile.core](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/mobile/core/package-summary.html) - definieert MobileUtil, die verschillende hulpprogrammamethoden biedt die rondom WCM Mobile draaien.

### Mobiele componenten {#mobile-components}

De **We.Retail Mobile Demo Site** gebruikt de volgende mobiele componenten die zich hieronder bevinden `/libs/foundation/components`:

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
   <td>mobiele afbeelding</td>
   <td>Mobiel</td>
   <td>- gebaseerd op de component waarop de afbeelding is gebaseerd<br /> - rendert een afbeelding als het apparaat<br /> </td>
  </tr>
  <tr>
   <td>mobiele</td>
   <td>Mobiel</td>
   <td>- gebaseerd op de component List<br /> - listitem_teaser.jsp rendert een afbeelding als het apparaat<br /> </td>
  </tr>
  <tr>
   <td>mobilelogo</td>
   <td>verborgen</td>
   <td>- gebaseerd op de basiscomponent van het logo<br /> - rendert een afbeelding als het apparaat<br /> </td>
  </tr>
  <tr>
   <td>mobilereferentie</td>
   <td>Mobiel</td>
   <td><p>- vergelijkbaar met de stichtingscomponent van de referentie</p> <p>- wijst een component van de textielafbeelding aan mobiletextimage toe één en een beeldcomponent aan mobiel beeld één</p> </td>
  </tr>
  <tr>
   <td>mobiletextimage</td>
   <td>Mobiel</td>
   <td>- op basis van de textielcomponent<br /> - rendert een afbeelding als het apparaat</td>
  </tr>
  <tr>
   <td>mobiletopnav</td>
   <td>verborgen</td>
   <td><p>- op basis van de bovenste grondcomponent</p> <p>- alleen tekst wordt weergegeven</p> </td>
  </tr>
 </tbody>
</table>

#### Een mobiele component maken {#creating-a-mobile-component}

Met het AEM mobiele framework kunt u componenten ontwikkelen die gevoelig zijn voor het apparaat dat het verzoek doet. De volgende codevoorbeelden laten zien hoe u de AEM mobiele API in een componentspaak kunt gebruiken en vooral hoe u dit kunt doen:

* Haal het apparaat op uit de aanvraag:
   `Device device = slingRequest.adaptTo(Device.class);`

* De apparaatgroep ophalen:
   `DeviceGroup deviceGroup = device.getDeviceGroup();`

* Krijg de mogelijkheden van de apparatengroep:
   `Collection<DeviceCapability> capabilities = deviceGroup.getCapabilities();`

* Haal de apparaatkenmerken op (onbewerkte capaciteitstoets/waarden uit de WURFL-database):
   `Map<String,String> deviceAttributes = device.getAttributes();`

* Haal de user-agent van het apparaat op:
   `String userAgent = device.getUserAgent();`

* Haal de lijst met apparaatgroepen (apparaatgroepen die door de auteur aan de site zijn toegewezen) op van de huidige pagina:
   `DeviceGroupList deviceGroupList = currentPage.adaptTo(DeviceGroupList.class);`

* Controleren of de apparaatgroep afbeeldingen ondersteunt
   `if (deviceGroup.hasCapability(DeviceCapability.CAPABILITY_IMAGES)) {`
... OF ...   `if MobileUtil.hasCapability(request, DeviceCapability.CAPABILITY_IMAGES) {`
...

>[!NOTE]
>
>In een jsp, `slingRequest` is beschikbaar via `<sling:defineObjects>` tag en `currentPage` via de `<cq:defineObjects>` tag.

### Emulators {#emulators}

Emulatorgebaseerde authoring biedt auteurs de mogelijkheid om inhoudspagina&#39;s te maken die bedoeld zijn voor mobiele clients. Mobiele inhoud schrijven volgens hetzelfde principe als WYSIWYG bewerken. Auteurs kunnen de weergave van de pagina op een mobiel apparaat alleen zien als ze een pagina met mobiele inhoud bewerken met een apparaatemulator.

Mobiele apparaten emulators zijn gebaseerd op het generieke emulatorframework. Zie voor meer informatie de [Emulators](/help/sites-developing/emulators.md) pagina.

De apparatenmededinger toont het mobiele apparaat op de pagina terwijl het gebruikelijke uitgeven (parsys, componenten) binnen het scherm van het apparaat voorkomt. De apparaatemulator is afhankelijk van de apparaatgroepen die voor de site zijn geconfigureerd. Verschillende emulators kunnen worden toegewezen aan een apparaatgroep. Alle emulators zijn vervolgens beschikbaar op de inhoudspagina. Standaard wordt de eerste emulator weergegeven die is toegewezen aan de eerste apparaatgroep die aan de site is toegewezen. Emulators kunnen worden geschakeld via de emulatorcarrousel boven aan de pagina of via de bewerkingsknop van de Sidetrap.

**Emulator maken**

Als u een emulator wilt maken, raadpleegt u de [Aangepaste mobiele emulator maken](/help/sites-developing/emulators.md) in de generieke pagina Emulators.

**Belangrijkste kenmerken van mobiele emulators**

* Een apparaatgroep bestaat uit een of meer emulators: de configuratiepagina van de apparaatgroep, bijvoorbeeld /etc/mobile/groups/touch, bevat de `emulators` eigenschap onder de `jcr:content` knooppunt.
Opmerking: hoewel het mogelijk is dat dezelfde emulator tot verschillende apparaatgroepen behoort, heeft het weinig zin.

* Via het de configuratiedialoog van de apparatengroep, `emulators` wordt ingesteld met het pad van de gewenste emulator(s). Bijvoorbeeld: `/libs/wcm/mobile/components/emulators/iPhone4`.

* De emulatorcomponenten (bv. `/libs/wcm/mobile/components/emulators/iPhone4`) de mobiele basisemulatorcomponent uitbreiden ( `/libs/wcm/mobile/components/emulators/base`).

* Elke component die de basis mobiele emulator uitbreidt, is beschikbaar voor selectie wanneer u een apparaatgroep configureert. Aangepaste emulators kunnen dus gemakkelijk worden gemaakt of uitgebreid.
* Op verzoek wordt de emulatorimplementatie gebruikt om de pagina weer te geven in de bewerkingsmodus.
* Wanneer de sjabloon van de pagina afhankelijk is van de component voor mobiele pagina, worden de emulatorfuncties automatisch in de pagina geïntegreerd (via de `head.jsp` van het mobiele paginacomponent).

### Apparaatgroepen {#device-groups}

Mobiele apparaatgroepen bieden segmentatie van mobiele apparaten op basis van de mogelijkheden van het apparaat. Een apparatengroep verstrekt de informatie die voor op emulator-gebaseerde creatie op de auteursinstantie en voor correcte inhouderenteruggave op het publish geval wordt vereist: zodra auteurs inhoud hebben toegevoegd aan de mobiele pagina en deze hebben gepubliceerd , kan de pagina worden opgevraagd in het publicatieexemplaar . In plaats van de emulator-bewerkingsweergave wordt de inhoudspagina weergegeven met een van de geconfigureerde apparaatgroepen. De selectie van de apparaatgroep vindt plaats op basis van [detectie van mobiele apparaten](#devicedetection). De passende apparatengroep verstrekt dan de noodzakelijke het stileren informatie.

Apparaatgroepen worden hieronder gedefinieerd als inhoudspagina&#39;s `/etc/mobile/devices` en gebruiken de **Mobiele apparaatgroep** sjabloon. Het malplaatje van de apparatengroep dient als configuratiemalplaatje voor de definities van de apparatengroep in de vorm van inhoudspagina&#39;s. De belangrijkste kenmerken zijn:

* Locatie: `/libs/wcm/mobile/templates/devicegroup`
* Toegestaan pad: `/etc/mobile/groups/*`
* Paginacomponent: `wcm/mobile/components/devicegroup`

#### Apparaatgroepen toewijzen aan uw site {#assigning-device-groups-to-your-site}

Wanneer u een mobiele site maakt, moet u apparaatgroepen aan uw site toewijzen. AEM biedt drie apparaatgroepen, afhankelijk van de HTML- en JavaScript-rendermogelijkheden van het apparaat:

* **Functie** telefoons, voor eigenschapapparaten zoals Sony Ericsson W800 met steun voor basis HTML maar geen steun voor beelden en JavaScript.
* **Slim** telefoons, voor apparaten zoals Blackberry met ondersteuning voor standaard HTML en afbeeldingen, maar geen ondersteuning voor JavaScript.

* **Aanraken** telefoons, voor apparaten zoals iPad met volledige steun voor HTML, beelden, JavaScript en apparatenomwenteling.

Als emulators kunnen worden gekoppeld aan een apparaatgroep (zie de sectie [Een apparaatgroep maken](#creating-a-device-group)), kan de auteur door het toewijzen van een apparaatgroep aan een site een keuze maken tussen de emulators die aan de apparaatgroep zijn gekoppeld om de pagina te bewerken.

U kunt als volgt een apparaatgroep aan uw site toewijzen:

1. Ga in uw browser naar **Siteadmin** console.
1. De hoofdpagina van uw mobiele site hieronder openen **Websites**.
1. Open de pagina-eigenschappen.
1. Selecteer **Mobiel** tab:

   * Definieer de apparaatgroepen.
   * Klikken **OK**.

>[!NOTE]
>
>Wanneer de apparaatgroepen voor een site zijn gedefinieerd, worden ze door alle pagina&#39;s van de site overgenomen.

#### Apparaatgroepfilters {#device-group-filters}

Filters voor apparaatgroepen definiëren criteria die zijn gebaseerd op de mogelijkheid om te bepalen of een apparaat tot de groep behoort. Wanneer u een apparaatgroep maakt, kunt u de filters selecteren die u wilt gebruiken voor het evalueren van apparaten.

Wanneer AEM een HTTP-aanvraag van een apparaat ontvangt, vergelijkt elk filter dat aan een groep is gekoppeld de mogelijkheden van het apparaat met specifieke criteria. Het apparaat wordt geacht tot de groep te behoren wanneer het alle mogelijkheden heeft die de filters vereisen. Capabilities worden opgehaald uit de WURFL™-database.

Apparaatgroepen kunnen nul of meer filters gebruiken voor capaciteitsdetectie. Een filter kan ook worden gebruikt met meerdere apparaatgroepen. AEM verstrekt een standaardfilter dat bepaalt of het apparaat de mogelijkheden heeft die voor een groep worden geselecteerd:

* CSS
* JPG- en PNG-afbeeldingen
* JavaScript
* Apparaatrotatie

Als de apparatengroep geen filter gebruikt, zijn de geselecteerde mogelijkheden die voor de groep worden gevormd de enige mogelijkheden die een apparaat vereist.

Zie voor meer informatie [Apparaatgroepfilters maken](/help/sites-developing/groupfilters.md).

#### Een apparaatgroep maken {#creating-a-device-group}

Maak een apparaatgroep als de groepen die AEM installeren niet aan uw vereisten voldoen.

1. Ga in uw browser naar **Gereedschappen** console.
1. Een nieuwe pagina maken hieronder **Gereedschappen** > **Mobiel** > **Apparaatgroepen**. In de **Pagina maken** dialoogvenster:

   * Als **Titel** enter `Special Phones`.

   * Als **Naam** enter `special`.

   * Selecteer **Sjabloon mobiele apparaatgroep**.
   * Klikken **Maken**.

1. Voeg in CRXDE een **static.css** bestand met de stijlen voor de apparaatgroep onder de `/etc/mobile/groups/special` knooppunt.

1. Open de **Speciale telefoons** pagina.
1. Als u de apparaatgroep wilt configureren, klikt u op de knop **Bewerken** knop naast **Instellingen**.
Op de **Algemeen** tab:

   * **Titel**: de naam van de mobiele apparaatgroep.
   * **Beschrijving**: beschrijving van de groep.
   * **Gebruikersagent**: user-agent-tekenreeks waar de apparaten aan worden aangepast. Het is optioneel en kan een regex zijn. Voorbeeld: `BlackBerryZ10`
   * **Mogelijkheden**: Hiermee bepaalt u of de groep afbeeldingen, CSS, JavaScript of het roteren van apparaten kan verwerken.
   * **Minimale schermbreedte** en **Hoogte**
   * **Emulator uitschakelen**: om de emulator tijdens het bewerken van inhoud in of uit te schakelen.

   Op de **Emulators** tab:

   * **Emulators**: Selecteer de emulators die aan deze apparaatgroep zijn toegewezen.

   Op de **Filters** tab:

   * Als u een filter wilt toevoegen, klikt u op Item toevoegen en selecteert u een filter in de vervolgkeuzelijst.
   * Filters worden geëvalueerd in de volgorde waarin ze worden weergegeven. Wanneer een apparaat niet aan de criteria van een filter voldoet, worden de opeenvolgende filters in de lijst niet geëvalueerd.



1. Klik op OK.

Het dialoogvenster voor de configuratie van groepen mobiele apparaten ziet er als volgt uit:

![screen_shot_2012-02-01at2043pm](assets/screen_shot_2012-02-01at22043pm.png)

#### Aangepaste CSS per apparaatgroep {#custom-css-per-device-group}

Zoals eerder is beschreven, is het mogelijk om een aangepaste CSS te koppelen aan een apparaatgroeppagina, ongeveer zoals de CSS van een ontwerppagina. Deze CSS wordt gebruikt om de apparaatgroepspecifieke weergave van de pagina-inhoud bij auteur en publicatie te beïnvloeden.Deze CSS wordt vervolgens automatisch opgenomen:

* In de pagina op de auteurinstantie voor elke mededinger die door deze apparatengroep wordt gebruikt.
* In de pagina op de publicatieinstantie als de gebruikersagent van de aanvraag overeenkomt met een mobiel apparaat in deze specifieke apparaatgroep.

## Apparaatdetectie op de server {#server-side-device-detection}

Gebruik filters en een bibliotheek met apparaatspecificaties om de mogelijkheden te bepalen van het apparaat dat de HTTP-aanvraag uitvoert.

### Apparaatgroepfilters ontwikkelen {#develop-device-group-filters}

Maak een apparaatgroepfilter om een set vereisten voor apparaatmogelijkheden te definiëren. Maak zoveel filters als u nodig hebt om de benodigde groepen apparaatmogelijkheden als doel in te stellen.

Ontwerp uw filters zodat u combinaties ervan kunt gebruiken om de groepen mogelijkheden te bepalen. Gewoonlijk zijn de mogelijkheden van verschillende apparaatgroepen elkaar overlappen. Daarom zou u sommige filters met veelvoudige definities van de apparatengroep kunnen gebruiken.

Nadat u een filter creeert, kunt u het in de groepsconfiguratie gebruiken.

Ga voor meer informatie naar [Apparaatgroepfilters maken](/help/sites-developing/groupfilters.md).

### De WURFL™-database gebruiken {#using-the-wurfl-database}

AEM gebruikt een afgekapte versie van de [WURFL](https://wurfl.sourceforge.net/)™-database voor het opvragen van apparaatmogelijkheden, zoals schermresolutie of javascript-ondersteuning, op basis van de gebruikersagent van het apparaat.

De XML-code van de WURFL™-database wordt hieronder weergegeven als knooppunten `/var/mobile/devicespecs` door de `wurfl.xml`bestand bij `/libs/wcm/mobile/devicespecs/wurfl.xml.` De uitbreiding aan knopen komt de eerste keer voor dat `cq-mobile-core` bundel is gestart.

Apparaatmogelijkheden worden opgeslagen als knoopeigenschappen en knooppunten vertegenwoordigen apparaatmodellen. U kunt query&#39;s gebruiken om de mogelijkheden van een apparaat of gebruikersagent op te halen.

Aangezien het WURFL™ gegevensbestand evolueert, kunt u het moeten aanpassen of vervangen. Voor het bijwerken van de database voor mobiele apparaten hebt u de volgende opties:

* Vervang het bestand door de nieuwste versie als u een licentie hebt die dit gebruik toestaat. Zie Een andere WURFL-database installeren.
* Gebruik de versie die in AEM beschikbaar is en vorm een regexp die uw gebruiker-Agent koorden en punten aan een bestaand apparaat WURFL™ aanpast. Zie [Een op regexp gebaseerde overeenstemmende gebruikersagent toevoegen](#adding-a-regexp-based-user-agent-matching).

#### Het testen van de Afbeelding van een Gebruiker-Agent aan Mogelijkheden WURFL™ {#testing-the-mapping-of-a-user-agent-to-wurfl-capabilities}

Wanneer een apparaat toegang krijgt tot uw mobiele site, detecteert AEM het apparaat, wijst het apparaat toe aan een apparaatgroep op basis van zijn mogelijkheden en verzendt het een weergave van de pagina die overeenkomt met de apparaatgroep. De overeenkomende apparaatgroep bevat de vereiste opmaakgegevens. De toewijzingen kunnen op de Mobiele Gebruiker-Agent Pagina van de Test worden getest:

`https://localhost:4502/etc/mobile/useragent-test.html`

#### Een andere WURFL™-database installeren {#installing-a-different-wurfl-database}

De afgekapte WURFL™-database die met AEM is geïnstalleerd, is een release die dateert van vóór 30 augustus 2011. Als uw versie van WURFL na 30 augustus 2011 is uitgebracht, moet u ervoor zorgen dat uw gebruik voldoet aan uw licentie.

Een WURFL™-database installeren:

1. Maak de volgende map in CRXDE Lite: `/apps/wcm/mobile/devicespecs`
1. Kopieer het WURFL™-bestand naar de map.
1. De naam van het bestand wijzigen als `wurfl.xml`.

AEM automatisch de `wurfl.xml` bestand en werkt de onderstaande knooppunten bij `/var/mobile/devicespecs`.

>[!NOTE]
>
>Wanneer de volledige WURFL™-database is ingeschakeld, kan het parseren en activeren enkele minuten duren. U kunt de logboeken bekijken voor voortgangsinformatie.

#### Een op regexp gebaseerde overeenstemmende gebruikersagent toevoegen {#adding-a-regexp-based-user-agent-matching}

Voeg een user-agent als regelmatige uitdrukking onder /apps/wcm/mobile/devicespecs/wurfl/regexp toe om aan een bestaand WURFL™ apparatentype te richten.

1. In **CRXDE Lite**, maakt u een knooppunt onder /apps/wcm/mobile/devicespecs/regexp, bijvoorbeeld apple_ipad_ver1.
1. Voeg de volgende eigenschappen toe aan het knooppunt:

   * **regexp**: reguliere expressie die user-agents definieert, bijvoorbeeld: .&#42;Mozilla.&#42;iPad.&#42;AppleWebKit.&#42;Safari.&#42;
   * **deviceId**: de apparaat-id zoals gedefinieerd in het bestand wurfl.xml, bijvoorbeeld: apple_ipad_ver1

De bovenstaande configuratie veroorzaakt apparaten waarvoor de gebruiker-Agent de geleverde regelmatige uitdrukking aanpast om aan apple_ipad_ver1 WURFL™ apparatenidentiteitskaart worden in kaart gebracht, als het bestaat.

## Apparaatdetectie op de client {#client-side-device-detection}

In deze sectie wordt beschreven hoe u de clientdetectie van AEM van het apparaat kunt gebruiken om de weergave van pagina&#39;s te optimaliseren of om de client alternatieve websiteversies te bieden.

AEM ondersteunt apparaatclientdetectie op basis van `BrowserMap`. `BrowserMap` wordt in AEM verzonden als een clientbibliotheek onder `/etc/clientlibs/browsermap`.

`BrowserMap` biedt u drie strategieën waarmee u een alternatieve website aan een client kunt aanbieden. Deze worden in de volgende volgorde gebruikt:

1. [Alternatieve koppelingen](#providing-alternate-links)
1. [Specifieke URL voor apparaatgroep](#definingdevicegroupspecificurl)
1. [Op kiezer gebaseerde URL](#defining-selector-based-urls)

>[!NOTE]
>
>Voor meer informatie over de integratie van de clientbibliotheek leest u de [Client-Side HTML-bibliotheken gebruiken](/help/sites-developing/clientlibs.md) sectie.

### Alternatieve koppelingen opgeven {#providing-alternate-links}

De `PageVariantsProvider` De dienst OSGi kan afwisselende verbindingen voor plaatsen produceren die tot de zelfde familie behoren. Om sites te configureren waarmee de service rekening moet houden, kan een `cq:siteVariant` knooppunt moet worden toegevoegd aan de `jcr:content` knooppunt van de hoofdmap van de site.

De `cq:siteVariant` node moet de volgende eigenschappen hebben:

* `cq:childNodesMapTo` - bepaalt aan welk kenmerk van het koppelingselement de onderliggende knooppunten worden toegewezen; het wordt aanbevolen de inhoud van uw website zodanig te ordenen dat de onderliggende items van het hoofdknooppunt de basis vormen voor een taalvariant van uw globale website (bijvoorbeeld `/content/mysite/en`, `/content/mysite/de`), in welk geval de waarde van de `cq:childNodesMapTo` moeten `hreflang`;
* `cq:variantDomain` - geeft aan wat `Externalizer` het domein wordt gebruikt om de absolute URL&#39;s van de paginariabelen te genereren; als deze waarde niet is ingesteld, worden de paginariabelen gegenereerd met relatieve koppelingen;
* `cq:variantFamily` - geeft aan tot welke familie van websites deze site behoort; meerdere apparaatspecifieke vertegenwoordigingen van dezelfde website moeten tot dezelfde familie behoren;
* `media` - slaat de waarden van het mediakenmerk van het koppelingselement op; wordt aangeraden de naam van de `BrowserMap` geregistreerd `DeviceGroups`, zodat de `BrowserMap` De bibliotheek kan de cliënten aan de correcte variant van de website automatisch door:sturen.

#### PageVariantsProvider en Externalalizer {#pagevariantsprovider-and-externalizer}

Wanneer de waarde van de `cq:variantDomain` eigenschap van een `cq:siteVariant` node is not empty, the `PageVariantsProvider` de dienst zal absolute verbindingen produceren gebruikend deze waarde als gevormd domein voor `Externalizer` service. Zorg ervoor dat u de `Externalizer` om uw opstelling te weerspiegelen.

>[!NOTE]
>
>Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

### Een apparaatgroepspecifieke URL definiëren {#defining-a-device-group-specific-url}

Als u geen alternatieve verbindingen wilt gebruiken, kunt u een globale URL voor elk vormen `DeviceGroup`. We raden u aan uw eigen clientbibliotheek te maken die de `browsermap.standard` clientbibliotheek, maar definieert de apparaatgroepen opnieuw.

BrowserMap is zodanig ontworpen dat de definities van apparaatgroepen kunnen worden overschreven door een nieuwe apparaatgroep met dezelfde naam te maken en aan de `BrowserMap` -object uit uw aangepaste clientbibliotheek.

>[!NOTE]
>
>Lees voor meer informatie de [Aangepaste BrowserMap](#creatingacustomisedbrowsermap) sectie.

### Op kiezers gebaseerde URL&#39;s definiëren {#defining-selector-based-urls}

Indien geen van de voorgaande mechanismen is gebruikt om een alternatieve locatie aan te geven voor `BrowserMap`en selecteert u vervolgens de kiezers die de namen van de `DeviceGroups` wordt toegevoegd aan de `URL`s, in welk geval u uw eigen servlets zou moeten verstrekken die de verzoeken zullen behandelen.

Bijvoorbeeld door een apparaat bladeren `www.example.com/index.html` geïdentificeerd als `smartphone` door BrowserMap wordt doorgestuurd naar `www.example.com/index.smartphone.html.`

### BrowserMap gebruiken op uw pagina&#39;s {#using-browsermap-on-your-pages}

Als u de standaard BrowserMap-clientbibliotheek op een pagina wilt gebruiken, moet u de `/libs/wcm/core/browsermap/browsermap.jsp` bestand met een `cq:include`-tag in de pagina `head` sectie.

```xml
<cq:include script="/libs/wcm/core/browsermap/browsermap.jsp" />
```

Naast het toevoegen van `BrowserMap` clientbibliotheek in uw `JSP` bestanden, moet u ook een `cq:deviceIdentificationMode` Eigenschap String ingesteld op `client-side` aan de `jcr:content` onder de hoofdmap van uw website.

### Standaardgedrag van BrowserMap overschrijven {#overriding-browsermap-s-default-behaviour}

Als u wilt aanpassen `BrowserMap` - door de `DeviceGroups` of het toevoegen van meer sondes - dan zou u uw eigen cliënt-zijbibliotheek moeten creëren waarin u inbedt `browsermap.standard`bibliotheek aan de clientzijde.

Bovendien moet u manueel roepen `BrowserMap.forwardRequest()` in uw `JavaScript` code.

>[!NOTE]
>
>Voor meer informatie over de integratie van de clientbibliotheek leest u de [Client-Side HTML-bibliotheken gebruiken](/help/sites-developing/clientlibs.md) sectie.

Nadat u de aangepaste `BrowserMap` clientbibliotheek, stellen wij de volgende aanpak voor:

1. Een `browsermap.jsp` bestand in uw toepassing

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

1. Inclusief de `broswermap.jsp` in uw kopsectie.

   ```xml
   <cq:include script="browsermap.jsp" />
   ```

### BrowserMap uitsluiten van bepaalde pagina&#39;s {#excluding-browsermap-from-certain-pages}

Als u de bibliotheek BrowserMap van sommige van uw pagina&#39;s zou willen uitsluiten waar u geen cliënt-opsporing nodig hebt, kunt u een verzoekattribuut toevoegen:

```xml
<%
request.setAttribute("browsermap.enabled", false);
%>
```

Hierdoor wordt `/libs/wcm/core/browsermap/browsermap.jsp` script om een meta-tag toe te voegen aan de pagina die wordt gemaakt `BrowserMap` geen detectie uitvoeren:

```xml
<meta name="browsermap.enabled" content="false">
```

### Een specifieke versie van een website testen {#testing-a-specific-version-of-a-web-site}

Doorgaans leidt het BrowserMap-script bezoekers altijd naar de meest geschikte versie van de website, waarbij bezoekers doorgaans naar het bureaublad of de mobiele site worden omgeleid wanneer dat nodig is.

U kunt het apparaat van om het even welk verzoek dwingen om een specifieke versie van een website te testen door toe te voegen `device` aan uw URL. Met de volgende URL wordt de mobiele versie van de website Geometrixx Outdoors weergegeven.

`https://localhost:4502/content/geometrixx-outdoors/en.html?wcmmode=disabled&device=smartphone`

>[!NOTE]
>
>De `wcmmode` paratemer is ingesteld op `disabled` om het gedrag van een publicatie-instantie te simuleren.

De overschreven apparaatwaarde wordt opgeslagen in een cookie, zodat u door uw website kunt bladeren zonder de `device` parameter voor elke `URL`.

Dientengevolge moet u het zelfde roepen `URL` met de `device` instellen op `browser` om terug te keren naar de bureaubladversie van de website.

>[!NOTE]
>
>BrowserMap slaat de overschreven apparaatwaarde op in een cookie met de naam `BMAP_device`. Als u deze cookie verwijdert, zorgt u ervoor dat CQ de juiste versie van de website aanbiedt op basis van uw huidige apparaat (bijvoorbeeld bureaublad of mobiel).

## Mobiele aanvraagverwerking {#mobile-request-processing}

AEM verwerkt als volgt een aanvraag die is uitgegeven door een mobiel apparaat dat tot de aanraakapparaatgroep behoort:

1. Een iPad verzendt een verzoek naar de AEM-publicatie-instantie, bijvoorbeeld `https://localhost:4503/content/geometrixx_mobile/en/products.html`
1. AEM bepaalt of de site van de aangevraagde pagina een mobiele site is (door te controleren of de pagina op het eerste niveau `/content/geometrixx_mobile` breidt het mobiele paginacomponent uit). Zo ja:
1. AEM kijkt omhoog de apparatenmogelijkheden die op gebruiker-Agent in de verzoekkopbal worden gebaseerd.
1. AEM wijst de apparatenmogelijkheden aan de apparatengroep toe en plaatst `touch` als de selector van de apparaatgroep.
1. AEM de aanvraag om `https://localhost:4503/content/geometrixx_mobile/en/products.touch.html.`
1. AEM stuurt het antwoord naar de iPad:

   * `products.touch.html` wordt op de gebruikelijke manier weergegeven en is in cache geplaatst.
   * De renderingcomponenten gebruiken kiezers om de presentatie aan te passen.
   * AEM voegt automatisch de mobiele kiezer toe aan alle interne koppelingen op de pagina.

### Statistieken {#statistics}

U kunt statistieken opvragen over het aantal aanvragen dat door mobiele apparaten bij de AEM server is ingediend. Het aantal aanvragen kan worden uitgesplitst:

* per apparaatgroep en apparaat
* per jaar, maand en dag

De statistieken weergeven:

1. Ga naar de **Gereedschappen** console.
1. Open de **Apparaatstatistieken** pagina hieronder **Gereedschappen** > **Mobiel**.
1. Klik op de koppeling om de statistieken voor een bepaald jaar, een bepaalde maand of een bepaalde dag weer te geven.

De **Statistieken** De pagina ziet er als volgt uit:

![screen_shot_2012-02-01at24353pm](assets/screen_shot_2012-02-01at24353pm.png)

>[!NOTE]
>
>De **Statistieken** Deze pagina wordt gemaakt wanneer een mobiel apparaat voor het eerst toegang krijgt tot AEM en wordt gedetecteerd. Daarvoor is het niet beschikbaar.

Als u een ingang in de statistieken moet produceren, kunt u als volgt te werk gaan:

1. Gebruik een mobiel apparaat of een emulator (bijvoorbeeld https://chrispederick.com/work/user-agent-switcher/ op Firefox).
1. Vraag een mobiele pagina aan op de auteurinstantie door de auteurswijze onbruikbaar te maken, b.v.:
   `https://localhost:4502/content/geometrixx_mobile/en/products.html?wcmmode=disabled`

De **Statistieken** is nu beschikbaar.

### Ondersteunende pagina-caching voor koppelingen naar vrienden verzenden {#supporting-page-caching-for-send-link-to-a-friend-links}

Mobiele pagina&#39;s kunnen doorgaans in de cache van Dispatcher worden geplaatst, omdat pagina&#39;s die voor een apparaatgroep worden weergegeven, in de pagina-URL worden onderscheiden door de kiezer van de apparaatgroep, bijvoorbeeld `/content/mobilepage.touch.html`. Een aanvraag naar een mobiele pagina zonder kiezer wordt nooit in de cache geplaatst, aangezien in dit geval de apparaatdetectie werkt en ten slotte wordt omgeleid naar de overeenkomende apparaatgroep (of &quot;nomatch&quot; voor dat geval). Een mobiele pagina die wordt weergegeven met een apparaatgroepkiezer, wordt verwerkt door de koppelingenrewriter, die alle koppelingen binnen de pagina herschrijft om ook de apparaatgroepkiezer te bevatten, zodat apparaatdetectie niet opnieuw kan worden uitgevoerd voor elke klik op een reeds gekwalificeerde pagina.

Daarom zou u het volgende scenario kunnen ontmoeten:

Alice van gebruiker wordt opnieuw gericht aan `coolpage.feature.html`en verzendt die URL naar een vriend Bob die het benadert met een andere client die zich in de `touch` apparaatgroep.

Indien `coolpage.feature.html` wordt gediend van een voorste voorste geheime voorgeheugen, krijgt AEM geen kans om het verzoek te analyseren om te weten te komen dat de mobiele selecteur niet de nieuwe gebruiker-Agent aanpast, en het Loodje krijgt de verkeerde vertegenwoordiging.

Als u dit wilt oplossen, kunt u een eenvoudige selectie-UI op de pagina&#39;s opnemen, waar eindgebruikers de apparaatgroep die is geselecteerd door AEM kunnen overschrijven. In het bovenstaande voorbeeld kan de eindgebruiker met een koppeling (of een pictogram) op de pagina schakelen naar `coolpage.touch.html` als hij denkt dat zijn apparaat daarvoor goed genoeg is .
