---
title: Concepten
description: Leer de algemene concepten van e-handel met Adobe Experience Manager.
contentOwner: Guillaume Carlino
exl-id: 290b2af6-257f-42f2-b809-1248227a4795
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '4439'
ht-degree: 0%

---

# Concepten{#concepts}

Het integratiekader biedt de mechanismen en componenten voor:

* verbinding met een eCommerce-motor
* gegevens naar Adobe Experience Manager halen (AEM)
* die gegevens weergeven en de reacties van de winkels verzamelen
* transactiegegevens retourneren
* zoeken naar de gegevens van beide systemen

Dit betekent dat:

* Winkelaars kunnen zich registreren en winkelen zonder te wachten.
* Koersveranderingen worden onmiddellijk door de kopers gezien.
* De producten kunnen worden toegevoegd zoals vereist.

>[!NOTE]
>
>Het eCommerce-kader kan worden gebruikt met:
>
>* [&#x200B; Adobe Commerce &#x200B;](/help/commerce/cif/integrating/magento.md)
>* [&#x200B; Commerce Cloud VAN SAP &#x200B;](/help/commerce/cif-classic/administering/sap-commerce-cloud.md)
>* [&#x200B; Salesforce Commerce Cloud &#x200B;](https://github.com/adobe/commerce-salesforce)
>

>[!CAUTION]
>
>Het [&#x200B; eCommerce integratiekader &#x200B;](https://business.adobe.com/products/experience-manager/sites/ecommerce-integrations.html) is een AEM toe:voegen-aan.
>
>Uw vertegenwoordiger kan alle gegevens verstrekken, afhankelijk van de betreffende motor.

>[!CAUTION]
>
>Het framework biedt de basisvereisten voor uw eigen project.
>
>Er is altijd een zekere hoeveelheid ontwikkelingswerk nodig om het kader aan uw specificaties aan te passen.

>[!CAUTION]
>
>De standaard AEM installatie omvat de generieke implementatie van de eCommerce van de AEM (JCR).
>
>Dit is bedoeld voor demonstratiedoeleinden of als de basis voor een aangepaste implementatie volgens uw vereisten.

Om de werking te optimaliseren, richten zowel AEM als de eCommerce-motor zich op hun eigen expertisegebied. De informatie wordt tussen beide in real time overgebracht; bijvoorbeeld:

* AEM kan:

   * Verzoek:

      * Productinformatie van de eCommerce-engine.

   * Geef:

      * Weergaven van gebruikers voor productinformatie, winkelwagentje en kassa.
      * Winkelwagentje en afrekeninformatie naar de eCommerce-engine.
      * SEO (Search Engine Optimization, optimalisatie van zoekmachines).
      * communautaire functionaliteit.
      * Niet-gestructureerde marketinginteracties.

* eCommerce-engine kan:

   * Geef:

      * Productinformatie uit de database.
      * Beheer van productvarianten.
      * Order Management.
      * ERP (Enterprise Resource Planning).
      * Zoek in de productinformatie.

   * Proces:

      * Het winkelwagentje.
      * De kassa.
      * Volgorde.

>[!NOTE]
>
>De precieze details hangen af van de eCommerce-motor en de projectuitvoering.

Verscheidene uit-van-de-doos AEM componenten worden verstrekt om de integratielaag te gebruiken. Deze zijn momenteel:

* Productinformatie
* Winkelwagentje
* Uitchecken
* Mijn account

Er zijn ook verschillende zoekopties beschikbaar.

## Architectuur {#architecture}

Het integratieframework biedt de API, een reeks componenten om functionaliteit te illustreren en verschillende extensies om voorbeelden van verbindingsmethoden te geven:

![&#x200B; chlimage_1-4 &#x200B;](/help/sites-administering/assets/chlimage_1-4.png)

Het framework biedt u toegang tot functies zoals:

![&#x200B; chlimage_1-5 &#x200B;](/help/sites-administering/assets/chlimage_1-5.png)

### Implementaties {#implementations}

AEM eCommerce wordt geïmplementeerd met een eCommerce-motor:

* Het integratiekader voor eCommerce is ontworpen om u gemakkelijk een eCommerce-motor met AEM te laten integreren. De speciaal gebouwde eCommerce-engine bestuurt productgegevens, winkelwagentjes, kassa&#39;s en bestelling, terwijl AEM de campagnes voor het weergeven en op de markt brengen van gegevens beheert.


>[!NOTE]
>
>De standaard AEM installatie omvat de generieke implementatie van de eCommerce van de AEM (JCR).
>
>Dit is bedoeld voor demonstratiedoeleinden of als de basis voor een aangepaste implementatie volgens uw vereisten.
>
>AEM eCommerce die wordt uitgevoerd binnen AEM met behulp van generieke ontwikkeling op basis van JCR is:
>
>* Een zelfstandig, AEM-native voorbeeld van eCommerce om het gebruik van de API te illustreren. Dit kan worden gebruikt om productgegevens te controleren, winkelwagentjes te kopen en uit te checken met de bestaande programma&#39;s voor het weergeven en op de markt brengen van gegevens. In dit geval, wordt het productgegevensbestand opgeslagen in de bewaarplaats inheems aan AEM (de implementatie van de Adobe van [&#x200B; JCR &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)).
>
>  De standaard AEM installatie bevat de grondbeginselen van de [&#x200B; generische implementatie eCommerce &#x200B;](/help/commerce/cif-classic/administering/generic.md).

### Commerce-providers {#commerce-providers}

Wanneer het invoeren van gegevens van een handelingsmotor in uw AEM eCommerce plaats, wordt een handelsleverancier gebruikt om de importeurs van gegevens te voorzien. Eén handelsprovider kan meerdere importeurs ondersteunen.

Een handelsleverancier is AEM code die aan of wordt aangepast:

* interface aan een achterste verkoopmotor
* een handelssysteem implementeren bovenop de gegevensopslagruimte van het GCO

Er zijn momenteel twee voorbeeld-aanbieders van handel beschikbaar voor AEM:

* één voor geometrixx-hybris
* een andere voor geometrixx-generic (JCR)

Hoewel gewoonlijk moet een project hun eigen, aangepaste, handelsleverancier ontwikkelen specifiek voor hun PIM en schema van productgegevens.

>[!NOTE]
>
>De Geometrixx-importeurs gebruiken CSV-bestanden. De opmerkingen boven hun implementatie bevatten een beschrijving van het geaccepteerde schema (met aangepaste eigenschappen toegestaan).

[&#x200B; ProductServicesManager &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/ProductServicesManager.html) handhaaft (door [&#x200B; OSGi &#x200B;](/help/sites-deploying/configuring.md#osgi-configuration-settings)) een lijst van implementaties van [&#x200B; ProductImporter &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/ProductImporter.html) en [&#x200B; CatalogBluprintImporter &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/CatalogBlueprintImporter.html) interfaces. Deze worden vermeld in het **dropdown gebied van de Importer** Importer/van de Leverancier van Commerce &lbrace;van de tovenaar van de Importeur (gebruikend het `commerceProvider` bezit als naam).

Wanneer een specifieke importeur/handelsleverancier beschikbaar is in de vervolgkeuzelijst, moeten eventuele aanvullende gegevens die hij nodig heeft, worden gedefinieerd (afhankelijk van het type importeur) in:

* `/apps/commerce/gui/content/catalogs/importblueprintswizard/importers`
* `/apps/commerce/gui/content/products/importproductswizard/importers`

De map onder de juiste `importers` -map moet overeenkomen met de naam van de importer, bijvoorbeeld:

* `.../importproductswizard/importers/geometrixx/.content.xml`

De indeling van het bronimportbestand wordt gedefinieerd door de importer. Of de importer kan een verbinding tot stand brengen (bijvoorbeeld WebDAV of http) met de commerce engine.

## Rollen {#roles}

Het geïntegreerde systeem voorziet voor de volgende rollen om de gegevens te handhaven:

* PIM-gebruiker (Product Information Management) die het volgende onderhoudt:

   * Productinformatie.
   * Taxonomie, categorisering, goedkeuring.
   * Werkt met beheer van digitale middelen.
   * Prijsstelling - vaak komt dit uit een ERP-systeem en wordt dit niet expliciet in het handelssysteem gehandhaafd.

* Auteur/marketingmanager die het volgende onderhoudt:

   * Marketing van inhoud voor alle kanalen.
   * Promoties.
   * Vouchers.
   * Campagnes.

* Surfer/shopper die:

   * Bekijk uw productinformatie.
   * Hiermee plaatst u artikelen in het winkelwagentje.
   * Controleert hun bestellingen.
   * Voldoen van bestelling verwacht.

Hoewel de daadwerkelijke plaats van uw implementatie kan afhangen; bijvoorbeeld, algemeen of met een eCommerce motor:

![&#x200B; chlimage_1-6 &#x200B;](/help/sites-administering/assets/chlimage_1-6.png)

## Producten {#products}

### Productgegevens versus marketinggegevens {#product-data-versus-marketing-data}

#### Structuur- en marketingcategorieën {#structural-versus-marketing-categories}

Als de volgende twee categorieën kunnen worden gedifferentieerd, kunt u zo duidelijke URL&#39;s met een zinvolle structuur (bomen van `cq:Page` knooppunten) maken en dus heel dicht bij het beheer van klassieke AEM inhoud):

* *Structurele *categorieën

  De categorieboom die *bepaalt wat een product* is; bijvoorbeeld:

  `/products/mens/shoes/sneakers`

* *marketing* categorieën

  Alle andere categorieën die a *product tot* kunnen behoren; bijvoorbeeld:

  `/special-offers/christmas/shoes`)

### Productgegevens {#product-data}

Als u uw product wilt portretteren en beheren, wilt u een scala aan gegevens over deze producten bewaren.

Productgegevens kunnen zijn:

* rechtstreeks in AEM (algemeen) worden onderhouden.
* in de eCommerce-engine worden onderhouden en in AEM beschikbaar worden gesteld.

  Afhankelijk van het gegevenstype wordt het [&#x200B; gesynchroniseerd &#x200B;](#catalog-maintenance-data-synchronization) zonodig, of direct betreden; bijvoorbeeld, worden de hoogst volatiele en kritieke gegevens zoals productprijzen teruggewonnen van de e-commerce motor op elk paginaverzoek om ervoor te zorgen zij altijd bijgewerkt zijn.

In één van beide geval, wanneer de productgegevens zijn ingegaan/in AEM ingevoerd kan het van de **Produkten** console worden gezien. Hier wordt op de kaart en in de lijst informatie over een product weergegeven, zoals:

* de afbeelding
* de SKU-code
* wanneer laatst gewijzigd

![&#x200B; chlimage_1-7 &#x200B;](/help/sites-administering/assets/chlimage_1-7.png)

### Productvarianten {#product-variants}

Voor geschikte producten kan ook informatie over varianten worden bewaard. Voor kledingstukken worden de verschillende beschikbare kleuren bijvoorbeeld als varianten bewaard:

![&#x200B; elektronische productvarianten &#x200B;](/help/sites-administering/assets/ecommerceproductvariants.png)

### Productkenmerken {#product-attributes}

De afzonderlijke kenmerken van elk product kunnen afhankelijk zijn van de eCommerce-engine die wordt gebruikt en van uw AEM implementatie. Deze zijn (waar van toepassing) beschikbaar bij het bekijken van productpagina&#39;s en/of het uitgeven van productinformatie en kunnen omvatten:

* **Beeld**

  Een afbeelding van het product.

* **Titel**

  De productnaam.

* **Beschrijving**

  Een tekstbeschrijving van het product.

* **Markeringen**

  Tags die worden gebruikt om verwante producten te groeperen.

* **Standaard de Categorie van Activa**

  Een standaardcategorie voor elementen.

* **Gegevens ERP**

  ERP-informatie (Enterprise Resource Planning).

   * **SKU**

     Informatie over de bewaareenheid (SKU).

   * **Kleur**
   * **Grootte**
   * **Prijs**

     De eenheidsprijs van het product.

* **Samenvatting**

  Een samenvatting van de productkenmerken.

* **Eigenschappen**

  Meer informatie over de productfuncties.

### Product Assets {#product-assets}

Voor afzonderlijke producten kan een selectie van activa worden aangehouden. Dit zijn meestal afbeeldingen en video&#39;s.

## Catalogi {#catalogs}

In een catalogus worden productgegevens gegroepeerd voor zowel beheer als representatie voor de klant. Een catalogus is vaak gestructureerd op basis van onder andere taal, geografisch gebied, merk, seizoen, hobby, sport.

### Catalogusstructuur {#catalog-structure}

#### Catalogi in meerdere talen {#catalogs-in-multiple-languages}

AEM ondersteunt productinhoud in meerdere talen. Wanneer gegevens worden aangevraagd, haalt het integratieframework de taal op uit de huidige structuur (bijvoorbeeld `en_US` voor pagina&#39;s onder `/content/geometrixx-outdoors/en_US` ).

Voor een meertalige opslag, kunt u uw catalogus voor elke taalboom individueel invoeren (of het kopiëren met [&#x200B; MSM &#x200B;](/help/sites-administering/msm.md)).

#### Catalogi voor meerdere merken {#catalogs-for-multiple-brands}

Net als bij talen moeten grote multinationale ondernemingen rekening houden met meerdere merken.

#### Catalogi op tags {#catalogs-by-tags}

Met labels kunt u ook producten groeperen in een catalogus. Deze kunnen worden gebruikt voor meer dynamische catalogi, zoals seizoensaanbiedingen.

### Catalogusinstelling (eerste import) {#catalog-setup-initial-import}

Afhankelijk van uw implementatie kunt u de vereiste productgegevens voor uw basiscatalogus importeren in AEM van:

* een CSV-bestand (voor de algemene implementatie)
* de eCommerce-motor

### Catalogusonderhoud (gegevenssynchronisatie) {#catalog-maintenance-data-synchronization}

Verdere wijzigingen van de productgegevens zijn onvermijdelijk:

* voor de generische implementatie, kunnen deze met de [&#x200B; productredacteur &#x200B;](/help/commerce/cif-classic/administering/generic.md#editing-product-information) worden beheerd
* wanneer het gebruiken van een [&#x200B; eCommerce motor moeten de veranderingen worden gesynchroniseerd &#x200B;](#data-synchronization-with-an-ecommerce-engine-ongoing)

#### Gegevenssynchronisatie met een eCommerce-engine (aan de gang) {#data-synchronization-with-an-ecommerce-engine-ongoing}

Na de eerste import zijn wijzigingen in de productgegevens onvermijdelijk.

Bij gebruik van een eCommerce-motor worden de productgegevens daar bewaard en moeten ze in AEM beschikbaar zijn. Deze productgegevens moeten worden gesynchroniseerd wanneer updates worden uitgevoerd.

Dit kan afhankelijk zijn van het type gegevens:

* A [&#x200B; periodieke synchronisatie wordt gebruikt samen met een gegevensvoer van veranderingen &#x200B;](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#product-synchronization-and-publishing).

  Daarnaast kunt u specifieke updates selecteren voor een express-update.

* De hoogst volatiele gegevens, zoals prijsinformatie, worden teruggewonnen van de handelingsmotor voor elk paginaverzoek, om ervoor te zorgen dat het altijd bijgewerkt is.

### Catalogi - Prestaties en schalen {#catalogs-performance-and-scaling}

Het importeren van een grote catalogus met een groot aantal producten (meer dan 100.000) uit een eCommerce-engine (PIM) kan het systeem beïnvloeden vanwege het grote aantal knooppunten. Het kan ook de ontwerpinstantie vertragen als de producten bijbehorende elementen hebben (bijvoorbeeld productafbeeldingen). Dit komt omdat de naverwerking van deze middelen CPU- en geheugenintensief is.

U kunt kiezen uit verschillende strategieën om deze problemen op te lossen:

* [&#x200B; Emmering &#x200B;](#bucketing) - om voor het grote aantal knopen te behandelen
* [Middelen na verwerking naar een specifieke instantie verplaatsen](#offload-asset-post-processing-to-a-dedicated-instance)
* [Alleen productgegevens importeren](#only-import-product-data)
* [Throttling importeren en opslaan in batch](#import-throttling-and-batch-saves)
* [Prestatietesten](#performance-testing)
* [Prestaties - Diversen](#performance-miscellaneous)

#### Emmertje {#bucketing}

Als een knoop JCR vele directe kindknopen (bijvoorbeeld, 1000 en meer) heeft, zijn de emmers (fantoommappen) vereist om ervoor te zorgen dat de prestaties niet worden beïnvloed. Deze worden gegenereerd volgens een algoritme bij het importeren.

Deze emmers hebben de vorm van fantoommappen die aan uw catalogusstructuur worden geïntroduceerd, maar kunnen worden gevormd zodat zij niet duidelijk in openbare URLs zijn.

#### Middelen na verwerking naar een specifieke instantie verplaatsen {#offload-asset-post-processing-to-a-dedicated-instance}

In dit scenario worden twee auteur-instanties ingesteld:

1. Hoofd-auteur-instantie

   Hiermee importeert u productgegevens van PIM, waarop naverwerking voor de assetpaden is uitgeschakeld.

1. Speciale DAM-auteurinstantie

   Importeert en nabewerkt productactiva van PIM, en herhaalt deze dan terug naar de hoofdauteur instantie voor gebruik.

![&#x200B; diagram van de Architectuur &#x200B;](/help/sites-administering/assets/chlimage_1-8.png)

#### Alleen productgegevens importeren {#only-import-product-data}

Als producten geen te importeren elementen (afbeeldingen) bevatten, kunt u de productgegevens importeren zonder dat dit wordt beïnvloed door de naverwerking van het element.

![&#x200B; diagram van de Architectuur &#x200B;](/help/sites-administering/assets/chlimage_1-9.png)

#### Prestatietesten {#performance-testing}

Bij AEM eCommerce-implementaties moet rekening worden gehouden met prestatietests:

* Auteursomgeving:

  Achtergrondactiviteit (bijvoorbeeld importeren) kan plaatsvinden op hetzelfde moment als normale gebruikersactiviteit (bijvoorbeeld paginabewerking) en zelfs als front-end prestaties (in het algemeen) een hogere prioriteit krijgen, kunnen slechte prestaties van onlineauteurs leiden tot frustratie die een go-live beslissing kan blokkeren.

* Publicatieomgeving:

  Replicatie is een belangrijk proces om ervoor te zorgen dat de inhoud snel en betrouwbaar wordt gepubliceerd. Dit kan worden beïnvloed door de manier waarop de auteur de te publiceren inhoud groepeert.

* Voorkant:

  De combinatie van front-end en cache-invalidaties kan mogelijk leiden tot prestatieverrassingen. Door te testen voorkomt u deze problemen.

Merk op dat deze prestatietests kennis en analyse van uw doel vereisen:

* Inhoudsvolumes

   * Assets
   * Gelokaliseerde, I18-producten en SKU&#39;s

* Gebruikersactiviteit:

   * Bulkuitgave
   * Bulkpublicatie
   * Intensieve zoekverzoeken

* Achtergrondprocessen

   * Invoer
   * Synchronisatie-updates (bijvoorbeeld prijzen)

* Onderhoudsvereisten (back-up, Tar PM-optimalisatie, opschoning van datastore, enzovoort)

#### Prestaties - Diversen {#performance-miscellaneous}

Voor alle implementaties kunt u de volgende punten in acht nemen:

* Aangezien het product, de bewaareenheden en de categorieën talrijk kunnen zijn, probeer om het minste aantal knopen te gebruiken mogelijk om de inhoud te modelleren.

  Hoe meer knopen u hebt, hoe flexibeler uw inhoud is (bijvoorbeeld, parsys). Maar alles is een compromis en hebt u (standaard) individuele flexibiliteit nodig bij het manipuleren (bijvoorbeeld) van 30K-producten?

* Vermijd dubbel zoveel als u kunt (zie lokalisatie), of wanneer u doet, denk over hoeveel knopen uw duplicatie tot leidt.
* Probeer de inhoud zo veel mogelijk van tags te voorzien om de optimalisatie van de query voor te bereiden.

  Bijvoorbeeld:

  `/content/products/france/fr/shoe/reebok/pump/46 SKU`

  moet één tag per inhoudsniveau hebben (land, taal, categorie, merk, product). Zoeken naar

  `//element(*,my:Sku)[@country='france' and @language='fr'`

  en

  `@category='shoe' and @brand='reebok' and @product='pump']`

  wordt veel sneller dan zoeken naar

  `/jcr:root/content/france/fr/shoe/reebok/pump/element(*,my:Sku)`

* In uw technische stapel, plan factorized inhoudstoegangsmodel en de diensten. Dit is een algemene beste praktijk, maar is hier nog belangrijker, aangezien u, in optimalisatiefasen, toepassingsgeheime voorgeheugens voor gegevens kunt toevoegen die vaak worden gelezen (en dat u niet het bundelgeheime voorgeheugen met wilt vullen).

  Bijvoorbeeld, is het attributenbeheer vaak een goede kandidaat voor caching aangezien het gegevens betreft die door de invoer van producten worden bijgewerkt.
* Overweeg gebruik van [&#x200B; volmachtspagina&#39;s &#x200B;](#proxy-pages).

### Sectiepagina&#39;s catalogus {#catalog-section-pages}

De secties van de Catalogus verstrekken u, bijvoorbeeld:

* een inleiding (afbeelding en/of tekst) op de categorie; dit kan ook worden gebruikt voor banners en teasers om speciale aanbiedingen te promoten
* links naar de afzonderlijke producten van die categorie
* links naar de andere categorieën

![&#x200B; ecommerce_categoryrunning &#x200B;](/help/sites-administering/assets/ecommerce_categoryrunning.png)

### Productpagina&#39;s {#product-pages}

Productpagina&#39;s bevatten uitgebreide informatie over afzonderlijke producten. Dynamische updates van worden ook weerspiegeld, bijvoorbeeld prijswijzigingen die zijn geregistreerd op de eCommerce-engine.

De pagina&#39;s van het product zijn AEM pagina&#39;s die de **component van het Product** gebruiken; bijvoorbeeld, binnen het **het product van Commerce** malplaatje:

![&#x200B; ecommerce_nairobirunnersgreen &#x200B;](/help/sites-administering/assets/ecommerce_nairobirunnersgreen.png)

De component Product biedt:

* Algemene productinformatie, inclusief tekst en afbeeldingen.
* Prijsbepaling; dit wordt teruggewonnen van de eCommerce motor telkens als de pagina wordt getoond/verfrist.
* Informatie over productvarianten, bijvoorbeeld kleur en grootte.

Met deze informatie kan de verkoper het volgende selecteren wanneer hij een item aan zijn mandje toevoegt:

* Kleur- en formaatvarianten
* Aantal

#### Landingspagina&#39;s product {#product-landing-pages}

Dit zijn AEM pagina&#39;s die hoofdzakelijk statische informatie verstrekken; bijvoorbeeld, een inleiding en een overzicht met verbindingen aan de onderliggende productpagina&#39;s.

### Productcomponent {#product-component}

De **component van het Product** kan aan om het even welke pagina met een ouderpagina worden toegevoegd die de vereiste meta-gegevens (namelijk de wegen aan `cartPage` en `cartObject`) levert. In de demonstratielocatie, Geometrixx Outdoors, wordt dit geleverd door `UserInfo.jsp`.

De **component van het Product** kan ook volgens uw individuele vereisten worden aangepast.

### Proxypagina&#39;s {#proxy-pages}

Proxypagina&#39;s worden gebruikt om de structuur van de opslagplaats te vereenvoudigen en de opslagcapaciteit voor grote catalogi te optimaliseren.

Bij het maken van een catalogus worden per product tien knooppunten gebruikt, omdat dit afzonderlijke componenten bevat voor elk product dat u kunt bijwerken en aanpassen binnen AEM. Dit grote aantal knooppunten kan een probleem worden als uw catalogus honderden of zelfs duizenden producten bevat. Om problemen te voorkomen, kunt u uw catalogus maken met proxypagina&#39;s.

Proxypagina&#39;s gebruiken een structuur met twee knooppunten ( `cq:Page` en `jcr:content` ) die geen van de werkelijke productinhoud bevat. De inhoud wordt op verzoek gegenereerd door te verwijzen naar de productgegevens en de sjabloonpagina.

Er is echter sprake van een compromis. U kunt de productinformatie niet aanpassen binnen AEM, wordt een standaardsjabloon (gedefinieerd voor uw site) gebruikt.

>[!NOTE]
>
>Er zijn geen problemen als u een grote catalogus zonder proxypagina&#39;s importeert.
>
>U kunt op elk gewenst moment van de ene methode naar de andere converteren. U kunt ook een subsectie van uw catalogus omzetten.

## Promoties en vouchers {#promotions-and-vouchers}

### Vouchers {#vouchers}

Vouchers zijn een beproefde methode om kortingen aan te bieden om klanten aan te trekken voor het maken van een aankoop en/of het belonen van de loyaliteit van de klant.

* Levering aan vouchers:

   * Een vouchercode (die door de verkoper in de winkelwagen moet worden getypt).
   * Een voucherlabel (dat moet worden weergegeven nadat de gebruiker het in de winkelwagen heeft ingevoerd).
   * Een promotiepad (dat de actie definieert die de voucher toepast).

* De motoren van de buitenlandse handel kunnen bonnen ook leveren.

In AEM:

* Een voucher is een op pagina gebaseerde component die wordt gemaakt/bewerkt met de websiteconsole.
* De **component 0&rbrace; Voucher verstrekt:**

   * Een renderer voor voucherbeheer. Hier worden de vouchers weergegeven die zich momenteel in de kar bevinden.
   * De bewerkingsdialoogvensters (formulier) voor het beheren (toevoegen/verwijderen) van de vouchers.
   * De handelingen die vereist zijn voor het toevoegen/verwijderen van vouchers aan/uit de kar.

* Vouchers hebben geen eigen datum/tijd, maar gebruiken die van hun bovenliggende campagnes.

>[!NOTE]
>
>AEM gebruikt de termijn **Voucher**, is dit synoniem met de termijn **Coupon**.

### Aanbiedingen {#promotions}

Met promoties kunt u samen met vouchers scenario&#39;s maken zoals:

* Een bedrijf verstrekt douaneprijzen voor werknemers, die een handgemaakte lijst van gebruikers is.
* Langlopende klanten ontvangen kortingen op alle orders.
* Een verkoopprijs die wordt aangeboden over een welomschreven periode.
* Een klant ontvangt een voucher wanneer de vorige bestelling een bepaald bedrag overschrijdt.
* Een klant die *product-X* koopt wordt aangeboden een korting op *product-Y* (paarproducten).

Promoties worden niet door productinformatiemanagers onderhouden, maar door marketingmanagers:

* Een bevordering is een op pagina-gebaseerde component die met de console van Websites wordt gecreeerd/uitgegeven. &quot;
* Aanbod voor promoties:

   * Een prioriteit
   * Een pad voor promotiemandschappen

* U kunt promoties verbinden met een campagne om de aan/uit-datum of -tijden te definiëren.
* U kunt promoties aan een ervaring verbinden om hun segmenten te bepalen.
* Promoties die geen verband houden met een ervaring, worden niet op zichzelf afgegaan, maar kunnen nog steeds door een Voucher worden geactiveerd.
* De component Promotie bevat:

   * renderers en dialoogvensters voor bevorderingsbeheer
   * subcomponenten voor het teruggeven en het uitgeven configuratieparameters specifiek voor de promotiehandlers

In AEM zijn de bevorderingen ook geïntegreerd in [&#x200B; Campaign Management &#x200B;](/help/sites-authoring/personalization.md):

* a [&#x200B; campagne &#x200B;](/help/sites-authoring/personalization.md) specificeert de aan/uit tijden
* [&#x200B; ervaringen &#x200B;](/help/sites-authoring/personalization.md) *binnen* de campagne wordt gebruikt om activa (laserpagina&#39;s, bevorderingen, etc.) volgens het publiekssegment te groeperen zij beantwoorden aan

Een promotieactie kan worden uitgevoerd in een ervaring of rechtstreeks in de campagne:

* Als een bevordering in een ervaring wordt gehouden, dan kan het automatisch op een publiekssegment worden toegepast.

  In de geometrixx-outdoorvoorbeeldsite is de promotie bijvoorbeeld:

  `/content/campaigns/geometrixx-outdoors/big-spender/ordervalueover100/free-shipping`

  bevindt zich in een ervaring en wordt dus automatisch geactiveerd wanneer het segment ( `ordervalueover100` ) wordt opgelost.

* Als een bevordering niet binnen een ervaring verschijnt (slechts in de campagne), dan kan het niet automatisch op een publiek worden toegepast. Het kan echter nog steeds worden geactiveerd als de gebruiker een voucher in zijn winkelwagentje invoert en die voucher verwijst naar de promotie.

  Bijvoorbeeld:

  `/content/campaigns/geometrixx-outdoors/article/10-bucks-off`

  is buiten een ervaring en wordt dus nooit automatisch geactiveerd (dat wil zeggen: gebaseerd op segmentatie). Er wordt echter naar verwezen door de vouchers die te vinden zijn in verschillende ervaringen in de artikelcampagne. Als u deze boncodes in de winkelwagentje invoert, wordt de promotieactie geactiveerd.

>[!NOTE]
>
>[&#x200B; hybris bevorderingen &#x200B;](https://www.hybris.com/modules/promotion) en [&#x200B; hybris vouchers &#x200B;](https://www.hybris.com/en/modules/voucher) behandelen alles dat het winkelwagentje beïnvloedt en met het tarief verwant is. Promotie-specifieke marketing inhoud (zoals banners, enzovoort.) maakt geen deel uit van de hybris promotie.

## Personalization {#personalization}

### Klantenregistratie en -accounts {#customer-registration-and-accounts}

Wanneer een winkel zich registreert, moeten de rekeninggegevens worden gesynchroniseerd tussen AEM en de eCommerce-engine. Gevoelige gegevens worden onafhankelijk opgeslagen, maar profielen worden gedeeld:

![&#x200B; chlimage_1-10 &#x200B;](/help/sites-administering/assets/chlimage_1-10.png)

Het precieze mechanisme kan van het scenario afhangen:

1. De gebruikersaccounts bestaan in beide systemen:

   1. Geen actie vereist.

1. De gebruikersaccount bestaat alleen in AEM:

   1. De gebruiker wordt in de eCommerce-engine gemaakt met dezelfde account-id en een willekeurig wachtwoord dat in AEM wordt opgeslagen.
   1. Het willekeurige wachtwoord is noodzakelijk, aangezien AEM probeert om in de eCommerce motor op de eerste vraag (bijvoorbeeld, wanneer een productpagina wordt gevraagd en de eCommerce motor wordt van verwijzingen voorzien voor de prijs) te registreren. Omdat dit na AEM login gebeurt, is het wachtwoord niet beschikbaar.

1. De gebruikersaccount bestaat alleen in de eCommerce-engine:

   1. Het account wordt gemaakt in AEM met dezelfde account-id en hetzelfde wachtwoord.

Wanneer u een eCommerce-engine gebruikt, slaat AEM alleen de account-id en het wachtwoord op (optioneel een gebruikersgroep). Alle andere informatie wordt opgeslagen in de eCommerce-engine.

>[!NOTE]
>
>Wanneer u een eCommerce-engine gebruikt, moet u ervoor zorgen dat accounts die zijn gemaakt voor gebruikers die zich aanmelden bij een AEM-instantie, worden gerepliceerd (bijvoorbeeld als workflows) naar andere AEM die met die engine communiceren.
>
>Anders wordt bij deze andere AEM ook geprobeerd accounts te maken voor dezelfde gebruikers in de engine. Deze acties mislukken als er een `DuplicateUidException` afkomstig is van de engine.

### Aanmelden bij klant {#customer-sign-up}

Vaak is aanmelding vereist voor de winkelwagentje. Hiervoor is registratie (Account maken) vereist, zodat een klantspecifieke account kan worden gemaakt.

![&#x200B; chlimage_1-11 &#x200B;](/help/sites-administering/assets/chlimage_1-11.png)

>[!NOTE]
>
>Een anonieme winkelwagentje en afhandeling worden ook ondersteund.

### Aanmelden bij klant {#customer-sign-in}

Na aanmelding kan de winkels zich aanmelden met hun account, zodat hun acties kunnen worden bijgehouden en hun bestellingen kunnen worden uitgevoerd.

![&#x200B; chlimage_1-12 &#x200B;](/help/sites-administering/assets/chlimage_1-12.png)

### Single Sign-On {#single-sign-on}

Single Sign-On (SSO) wordt verstrekt, zodat de auteurs zowel in AEM als in het eCommerce systeem gekend zijn zonder het moeten binnen tweemaal aanmelden.

### myAccount {#myaccount}

Transactiegegevens van de eCommerce-engine worden gecombineerd met persoonlijke informatie over de winkelier. AEM gebruikt sommige van deze gegevens als profielgegevens. De actie van een formulier in AEM schrijft informatie terug naar de eCommerce-engine.

Er is een pagina waarop u eenvoudig uw accountgegevens kunt beheren. U kunt tot het toegang hebben door **Mijn Rekening** bij de bovenkant van een pagina van de Geometrixx te klikken, of door aan `/content/geometrixx-outdoors/en/user/account.html` te navigeren.

![&#x200B; chlimage_1-13 &#x200B;](/help/sites-administering/assets/chlimage_1-13.png)

### Adresboek {#address-book}

Uw site moet een selectie adressen opslaan, waaronder bezorging, facturering en alternatieve adressen. Dit kan worden uitgevoerd gebruikend vormen die op uw standaardadresformaat worden gebaseerd of u kunt de component van het Boek van het Adres gebruiken die door AEM wordt verstrekt.

Met deze component Adresboek kunt u:

* adressen in het boek bewerken
* selecteer een adres in het boek voor het verzendadres
* selecteer een adres uit het boek voor het factureringsadres

U kunt kiezen welk adres u als gebrek wilt.

De component van het adresboek is bereikbaar van de **Mijn pagina van de Rekening** door **Boek van het Adres** te klikken of door aan `/content/geometrixx-outdoors/en/user/account/address-book.html` te navigeren.

![&#x200B; chlimage_1-14 &#x200B;](/help/sites-administering/assets/chlimage_1-14.png)

U kunt **klikken toevoegt nieuw adres...** om een adres in uw adresboek toe te voegen. Het opent een vorm die u kunt invullen en dan **klikken voegt adres** toe.

>[!NOTE]
>
>U kunt verschillende adressen invoeren in uw adresboek.

Het adresboek wordt gebruikt wanneer u uw winkelwagen &quot;uitcheckt&quot;:

![&#x200B; chlimage_1-15 &#x200B;](/help/sites-administering/assets/chlimage_1-15.png)

Adressen blijven hieronder `user_home/profile/addresses` staan.
Voor Alison Parker, bijvoorbeeld, zou het onder /home/users/geometrixx/aparker@geometrixx.info/profile/adressen zijn

U kunt kiezen welk adres u als gebrek wilt, wordt deze informatie voortgeduurd in het profiel van de verkoopster eerder dan met het adres. De profieleigenschap `address.default` wordt ingesteld met het pad van het geselecteerde adres voor waarde.

### Klantspecifieke prijzen {#customer-specific-pricing}

De eCommerce-engine gebruikt de context (in feite de verkoopinformatie) om de prijs te bepalen die hij in zijn bezit heeft en geeft vervolgens de juiste informatie terug aan AEM.

## Winkelwagentje en bestellingen {#shopping-cart-and-orders}

Bij het winkelen bladert de winkelier door de productpagina&#39;s en selecteert hij items om deze in zijn winkelwagentje te plaatsen. Wanneer ze doorgaan met uitchecken, kan een bestelling worden geplaatst.

### Anonieme kopers {#anonymous-shoppers}

Een anonieme klant kan:

* Producten weergeven
* Producten aan hun winkelwagentje toevoegen
* Uitchecken uitvoeren om de bestelling te plaatsen

>[!NOTE]
>
>Afhankelijk van de configuratie van uw informatie van het instantieadres, of klantenregistratie, zou voorafgaand aan controle kunnen worden vereist.

### Geregistreerde kopers {#registered-shoppers}

Een geregistreerde klant kan:

* Aanmelden bij hun account
* Producten weergeven
* Producten aan hun winkelwagentje toevoegen
* Uitchecken uitvoeren om de bestelling te plaatsen
* Eerdere bestellingen weergeven en volgen

### Overzicht van winkelwagentje inhoud {#shopping-cart-content-overview}

Het winkelwagentje biedt:

* een overzicht van geselecteerde objecten
* koppelingen naar de productpagina&#39;s voor de geselecteerde items
* de mogelijkheid om:

   * het aantal/de hoeveelheid afzonderlijke items bijwerken
   * afzonderlijke items verwijderen

![&#x200B; ecommerce_shoppingcart &#x200B;](/help/sites-administering/assets/ecommerce_shoppingcart.png)

Het winkelwagentje wordt opgeslagen op basis van de gebruikte motor:

* AEM generiek slaat de kar op in een koekje.
* Bepaalde eCommerce-motoren kunnen de winkelwagen tijdens een sessie opslaan.

In beide gevallen blijven de items in het winkelwagentje (en kunnen ze worden hersteld) staan bij aanmelding/afmelding (maar alleen op dezelfde computer/browser). Bijvoorbeeld:

* bladeren als `anonymous` en producten toevoegen aan het winkelwagentje
* aanmelden als `Allison Parker` - De winkelwagen van Allison is leeg
* producten toevoegen aan het winkelwagentje van Allison
* afmelden - de winkelwagen toont de producten voor `anonymous`

* opnieuw aanmelden als `Allison Parker` - De producten van Allison worden hersteld

>[!NOTE]
>
>Een anonieme wagen kan alleen op dezelfde computer/browser worden hersteld.

>[!NOTE]
>
>Het wordt afgeraden het herstellen van de inhoud van het winkelwagentje te testen met de account `admin` , omdat dit in strijd kan zijn met de account van de eCommerce-engine (bijvoorbeeld hybris) van `admin` .

>[!NOTE]
>
>hybris kan worden geconfigureerd om hangende winkelwagentjes na een bepaalde periode te verwijderen .

Vóór de afhandeling worden prijswijzigingen weerspiegeld (in beide systemen) zodra ze zich voordoen.

### Ordergegevens {#order-information}

Afhankelijk van de implementatiegegevens van een bestelling in de eCommerce-engine of in de AEM, wordt deze informatie door AEM weergegeven.

Er worden verschillende gegevens opgeslagen, waaronder:

* **identiteitskaart van de Orde**

  Het referentienummer van de bestelling.

* **Geplaatste**

  De datum waarop de bestelling is geplaatst.

* **Status**

  De status van de bestelling, bijvoorbeeld Verzonden.

* **Valuta**

  De valuta van de order.

* **Punten van de Inhoud**

  Een lijst met geordende items.

* **Subtotal**

  De totale kosten van de bestelde objecten.

* **Belasting**

  Het bedrag van de verschuldigde belastingen op de bestelling.

* **Verschepend**

  Verzendkosten.

* **Totaal**

  De totale waarde van de bestelling; bestelde items, belastingen en verzendkosten.

* **Facturerend Adres**

  Het adres waarnaar de factuur moet worden verzonden.

* **Token van de Betaling**

  De betalingsmethode.

* **Status van de Betaling**

  De betalingsstatus.

* **Verzendadres**

  Het adres waarnaar de goederen moeten worden verzonden.

* **Verzendmethode**

  De methode van de scheepvaart, bijvoorbeeld land, zee of lucht.

* **Volgend Aantal**

  Elk trackingnummer dat door de verzendende onderneming wordt gebruikt.

* **het Volgen Verbinding**

  De koppeling die wordt gebruikt voor het bijhouden van de bestelling tijdens het verzenden.

>[!NOTE]
>
>Welke velden worden gebruikt in de wizard voor het maken van bestellingen, is afhankelijk van het feit of er een voor aanrakingen geoptimaliseerde basisstructuur is gedefinieerd voor de locatie. In het algemene voorbeeld vindt u de volgende informatie:
>`/etc/scaffolding/geometrixx-outdoors/order/jcr:content/cq:dialog`

Wanneer de orde binnen AEM de console van de Orde wordt gehouden toont het volgende voor elke orde:

* het aantal artikelen in de winkelwagen
* de totale waarde van de order
* op het moment dat de order werd geplaatst
* de status

![&#x200B; chlimage_1-16 &#x200B;](/help/sites-administering/assets/chlimage_1-16.png)

### Volgorde bijhouden {#order-tracking}

Nadat kopers een bestelling hebben geplaatst, keren ze vaak terug naar:

* De status van hun bestelling controleren
* Producten uit de bestelling verwijderen
* Producten aan de bestelling toevoegen

Na ontvangst van de levering van de bestelling willen kopers wellicht ook de geschiedenis zien van bestellingen die in een bepaalde periode zijn gedaan.

De eCommerce-engine beheert de naleving en tracering van bestellingen. De informatie kan worden getoond door AEM te gebruiken de component van de Geschiedenis van de Orde, die alle relevante details, met inbegrip van de toegepaste bonnen en promoties toont. Bijvoorbeeld:

![&#x200B; chlimage_1-17 &#x200B;](/help/sites-administering/assets/chlimage_1-17.png)

## Afhandeling {#checkout}

Afhandeling wordt geïmplementeerd met standaard AEM formulieren. Hierdoor kan de marketingmanager de ervaring met marketinginhoud aanpassen.

De eCommerce beheert vervolgens het afrekenproces met invoer uit de AEM formulieren.

### Betalingsbeveiliging {#payment-security}

Betalingsgegevens, waaronder creditcardgegevens, worden vaak beheerd door de eCommerce-engine. AEM geeft deze transactiegegevens door aan de motor (vanwaar deze vervolgens wordt doorgestuurd naar een betalingsverwerkingsdienst).

PGB-compatibiliteit (Payment Card Industry) kan worden bereikt.

### Bevestiging van bestelling {#confirmation-of-order}

De orde wordt bevestigd op het scherm en kan met het [&#x200B; orde volgen &#x200B;](#order-tracking) worden gevolgd.

## Zoeken {#search-features}

![&#x200B; chlimage_1-18 &#x200B;](/help/sites-administering/assets/chlimage_1-18.png)

Aangezien AEM standaardpagina&#39;s voor producten gebruikt, kunt u de standaardzoekcomponent gebruiken om een zoekpagina te maken.

Als u een grondiger implementatie nodig hebt, kunt u:

* Breid de standaardonderzoekscomponent met de functionaliteit uit die u nodig hebt.
* Implementeer de zoekmethode in uw `CommerceService` en gebruik vervolgens de zoekcomponent eCommerce op uw zoekpagina.

Wanneer u een eCommerce-engine gebruikt, kan de zoekfunctie-API voor eCommerce volledig worden geïmplementeerd in de eCommerce-oplossing, zodat u de zoekcomponent voor eCommerce kunt gebruiken die buiten het vak is opgegeven. Met de beperkte zoekopdracht kunt u zoeken in JCR en/of de engine:
