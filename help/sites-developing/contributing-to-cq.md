---
title: Bijdragen aan AEM
description: AEM wordt ontwikkeld op basis van beproefde methodologieën die algemeen worden toegepast in grote open-source-projecten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 43fb4fa3-269a-4635-b055-4b7d787da21f
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '2642'
ht-degree: 0%

---

# Bijdragen aan AEM{#contributing-to-aem}

## Ontwikkelingsmethode {#development-methodology}

AEM wordt ontwikkeld op basis van beproefde methodologieën die algemeen worden toegepast in grote open-source-projecten. Veel kernelementen in AEM technologiestapel worden in feite gehandhaafd als actieve open-source projecten, zoals Sling en Jackrabbit, die werden bijgedragen aan de Apache Software Foundation. Een belangrijk aspect van deze geest dat in AEM aanwezig is, is dat u wordt aangemoedigd om de beschikbare mailinglijsten en online forums voor directe interactie met het ontwikkelingsteam te gebruiken.

Als u aan componenten van AEM bijdraagt, vertrouwt u met AEM zoals u wanneer het bijdragen aan een open-bronproject, en communiceert met het bestaande kernteam zoals u zou wanneer u van plan bent om aan zulk een project bij te dragen.

## Vereiste ervaring {#required-experience}

Het HyperText Transfer Protocol (HTTP) is centraal bij alles wat we doen. Daarom alvorens tot AEM bij te dragen, zou u een diep inzicht in HTTP moeten hebben, idealiter in de mate waarin u uw eigen implementatie Java™ van een multithreaded server van HTTP met draad-pooling kunt schrijven. U zou ook een inzicht in HTTP/1.1 moeten hebben houdt-levend gedrag, en u zou een diepgaande kennis van server/cliënt-zijinteractie met JavaScript moeten hebben, in het bijzonder de asynchrone stijl van interactie die door AJAX wordt vertegenwoordigd.

Omdat de paginadynamiek en de interactieve inhoud zeer belangrijk voor de ervaring WM zijn, is het essentieel dat u een vrij diep inzicht in het Model van de Objecten van het Document en zijn potentieel voor programmatic manipulatie in reactie op gebeurtenissen hebt. U zou wat kennis, bijvoorbeeld, van DOM manipulatie in real time en belemmering-en-dalingsgedrag over veelvoudige browser documenten (bijvoorbeeld, het gebruiken van iframes) moeten hebben.

Op het hoogste niveau zou u een stevig inzicht in moeten hebben:

* het [&#x200B; HTTP/1.1 protocol &#x200B;](https://www.ietf.org/rfc/rfc2616.txt)
* HTML (bij voorkeur [&#x200B; HTML &#x200B;](https://html.spec.whatwg.org/))
* Cascading Style Sheets
* Extensible Markup Language (XML)
* Asynchrone JavaScript- en XML-ontwerppatronen (AJAX)
* JavaScript Object Notation (JSON)
* het Document Object Model
* Stateful versus stateless interacties
* [&#x200B; Uniform Middel Identifiers &#x200B;](https://www.ietf.org/rfc/rfc2396.txt)
* Browsercookies
* en andere moderne concepten voor webontwikkeling

De technologiestapel van Adobe Experience Manager is gebaseerd op [&#x200B; Apache Felix &#x200B;](https://felix.apache.org/documentation/index.html) container OSGI met [&#x200B; Apache Sling &#x200B;](https://sling.apache.org/index.html) Webkader en bedt een Bewaarplaats van de Inhoud Java™ ([&#x200B; JCR &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)) in die op [&#x200B; wordt gebaseerd Apache Jackrabbit &#x200B;](https://jackrabbit.apache.org/jcr/jcr-api.html). Maak kennis met deze afzonderlijke projecten en met andere open-source-componenten (bijvoorbeeld Apache Lucene) die worden gebruikt in het gebied waar u een bijdrage wilt leveren.

## Tribunale kennis {#tribal-knowledge}

Bepaalde concepten en leidende beginselen zijn diep verankerd in de cultuur van de voormalige Dag. Deze sectie bevat een aantal van de &quot;diep DNA-ingebedde&quot; problemen die u dient te kennen.

### Alles is inhoud {#everything-is-content}

De inhoud bevat niet alleen alle gegevens die de webtoepassing blijvend maakt. De programmacode, bibliotheken, manuscripten, malplaatjes, HTML, CSS, beelden, en artefacten van alle soorten, om het even wat, en alles wordt voortgeduurd in de Bewaarplaats van de Inhoud en ingevoerd/uitgevoerd in de vorm van pakketten via de Manager van het Pakket en het Aandeel van het Pakket.

### David&#39;s Model {#david-s-model}

Voor het modelleren van inhoud in een Java™ Content Repository is een totaal andere manier van denken nodig dan wat in de softwareindustrie gebruikelijk is voor het modelleren van gegevens in de relationele wereld. Essentiële lezing voor om het even welke nieuwkomer aan inhoudsbeheer de manier JCR is [&#x200B; Model van David: Een gids voor inhoud modelleren &#x200B;](https://wiki.apache.org/jackrabbit/DavidsModel).

### RESTfulness {#restfulness}

De REST-benadering is diep verankerd in wat we doen. Dit betekent onder andere dat stateful interacties moeten worden vermeden en dat URI&#39;s definitieve adressen zijn voor inhoud en services.

REST (REpresentational State Transfer) verwijst naar de software architecturale stijl waarop het World Wide Web is gebaseerd. Het beschrijft de belangrijkste elementen die het Web maken werken, en verstrekt zo een reeks principes voor hoe Web-based software zou moeten worden ontworpen. Bij het ontwerpen van een API die via het web moet worden gebruikt, is het daarom verstandig om deze &#39;best practices&#39; te volgen.

Omdat REST de leidende filosofie achter zoveel van wat wij doen is, moet u het van essentieel belang vinden om goed verdraaid te worden in de grondbeginselen van RESTful design. Een goede plaats om te beginnen is met [&#x200B; Roy Fielding &#x200B;](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

### Oplossing voor een aanvraag voor verzending {#sling-request-resolution}

Een belangrijk aspect om te begrijpen over AEM is hoe binnenkomende verzoeken betrekking hebben op inhoud en toepassingsgedrag, hoe inhoud is gestructureerd in de inhoudsopslagplaats en waar AEM zoekt naar de toepassingslogica om de aanvraag af te handelen. Leer over Apache [&#x200B; Sling URL decomposition &#x200B;](https://sling.apache.org/documentation/the-sling-engine/url-decomposition.html) en de manier het de architecturale stijl van het REST en zijn stateless, cacheable, en gelaagde systeembeperkingen afdwingt.

De belangrijkste aspecten die u moet begrijpen van de aanvraagresolutie van Apache Sling zijn hoe aanvragen primair worden toegewezen aan een specifieke bron in de inhoudsopslagplaats, hoe aanvullende eigenschappen van de aanvraag, samen met eigenschappen van deze inhoudsobjecten, bepalen welke toepassingscode wordt aangeroepen om de inhoud te renderen en hoe code in /apps code in /libs overschrijft.

### QuickStart {#quickstart}

Geen stap drie: als u wilt installeren en uitvoeren, downloadt en dubbelklikt u op het QuickStart JAR-bestand. Er is geen stap drie. Voor extra optionele functies hoeft u alleen het juiste pakket te installeren vanuit Package Share.

Kleine QuickStart-grootte: houd de grootte van het QuickStart JAR-bestand minimaal. Maak slim, geoptimaliseerd gebruik van bibliotheken en verplaats optionele functionaliteit naar Package Share.

Snellere opstarttijd: wanneer u een wijziging aanbrengt die de opstarttijd kan beïnvloeden, moet u ervoor zorgen dat deze korter wordt, niet langer.

### Lean en Mean {#lean-and-mean}

We zijn voor code en projecten die licht, klein, snel en elegant zijn. &quot;Goed genoeg&quot; is niet goed genoeg.

Hergebruik van code: Onze OSGi-gebaseerde productarchitectuur en de filosofie &quot;alles is inhoud&quot; betekenen dat we ongebruikelijk goede mogelijkheden hebben om code en artefacten opnieuw te gebruiken. We proberen zo veel mogelijk van dat feit te profiteren om functies mager en gemiddeld te houden.

Losse koppeling: we zijn voorstander van losjes gekoppelde interacties boven strakke afhankelijkheden en &quot;ongewenste intimiteit&quot;. Met losse koppeling kunt u ook meer code hergebruiken.

### De demo niet breken {#don-t-break-the-demo}

Word vertrouwd met demoscripts en productfuncties die het vaakst in demo&#39;s worden getoond. Begrijp dat niets u doet een &quot;demo manuscripteigenschap&quot;ooit zou moeten breken. Het kernproduct moet altijd demo-klaar zijn, zelfs tijdens de ontwikkeling.

### Ontwerpen voor betrouwbaarheid {#design-for-reliability}

We streven ernaar om functies te ontwerpen en te coderen zonder fouten, zodat (bijvoorbeeld) een probleem met één DOM-element er niet toe leidt dat een hele pagina niet wordt weergegeven. Met andere woorden: maak dingen die fataal, fataal zouden moeten zijn. Laat alles overleven. Maak het product &#39;vergeven&#39;.

### Abnormal is the New Normal {#abnormal-is-the-new-normal}

U moet opruimen bij het opstarten en niet afhankelijk zijn van de afsluithaken. Abnormale beëindiging is normale beëindiging.

`shutdown == kill -9 == power outage`

### Wees klaar voor elastische clustering {#be-ready-for-elastic-clustering}

Altijd klaar voor elastische groepering zijn; veronderstel altijd dat er zich het groeperen is. Over het algemeen betekent het naleven van alles wat zich in de inhoudsopslagplaats bevindt, geïntegreerde clusterondersteuning.

### Ontwerpen voor achterwaartse Verenigbaarheid {#design-for-backward-compatibility}

Niets u zou de oude code van een klant moeten breken. Neem alleen `/libs` in overweging om productcode te bevatten die tijdens een upgrade kan worden bijgewerkt. Het gedeelte `/apps` van de gegevensopslagruimte is projectcode en de sectie `/etc` bevat aangepaste configuraties die moeten worden behouden. In het algemeen mag u niets overschrijven in `/apps` , `/content` en `/home` . Na een verbetering, zou oude projectcode, configuraties, en inhoud moeten blijven functioneren aangezien het allen vóór de verbetering deed.

Het ontwerpen voor achterwaartse verenigbaarheid zorgt ook dat de verbeteringservaring de eenvoud van de aanvankelijke installatie aanpast. Het zou voldoende zijn om AEM te stoppen, het JAR-bestand voor QuickStart te vervangen en opnieuw AEM te starten. Met een snel groeiende installatiebasis is upgradeefficiëntie een steeds belangrijker voordeel.

Bestaande API&#39;s kunnen en moeten worden gemarkeerd als afgekeurd wanneer ze nieuwer zijn, maar een betere functionaliteit vervangt ze, alle API&#39;s die in een vorige versie van 5.x openbaar zijn gemaakt, moeten functioneel blijven, omdat ze in de aangepaste toepassingscode kunnen worden gebruikt. Dergelijke API&#39;s moeten niet worden verwijderd.

Achterwaartse compatibiliteit moet ook in aanmerking worden genomen met betrekking tot de algemene consistentie van de inhoudsstructuur en gebruikerservaring.

## Basisconcepten {#core-concepts}

**instantie van de Auteur** - typisch, voor veiligheid, bestuur, en andere redenen, verdeelt een productiesite instanties van AEM in de instanties van de Auteur en van Publish. Raadpleeg de documentatie over AEM instanties voor meer informatie over de implementatiearchitectuur (inclusief de instanties van Auteur/Publish).

**Caching, het bakken, en het bakken** - traditioneel, zijn de concepten bakken tegenover het bakken een belangrijk onderscheid tussen de verschillende Systemen van het Inhoudsbeheer van het Web. In CMS jargon verwijst &quot;bakken&quot; naar het concept van het toewijzen van gegevens aan statische bestanden tijdens de publicatietijd, terwijl &quot;fritten&quot; verwijst naar het concept van het verwerken van gegevens voor de uiteindelijke presentatie op aanvraag-tijd (dat wil zeggen net op tijd).

**het Groeperen en lading-in evenwicht brengen** - om beschikbaarheid te verhogen en de prestaties van een milieu van de Productie te verbeteren, is het gemeenschappelijk om veelvoudige Instanties van de Auteur en/of van Publish (in Clusters) te combineren, door of hen ter beschikking te stellen aan verschillende groepen gebruikers of door lading-in evenwicht brengend hen achter een configuratie van Dispatcher.

Het is ook mogelijk om veelvoudige instanties van de inhoudsbewaarplaats te combineren om a *high-availability* oplossing te creëren JCR, die dan met uw AEM oplossing kan worden geïntegreerd om bescherming tegen hardware en softwaremislukking te maximaliseren. Zie [&#x200B; Geadviseerde Inzet &#x200B;](/help/sites-deploying/recommended-deploys.md#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter) voor verdere informatie.

**Component** - in AEM, is een Component een objecten type, instanties waarvan over het algemeen door hen van, bijvoorbeeld, de Sidekick te slepen en te laten vallen kunnen worden gecreeerd. Bijvoorbeeld, buiten-de-dooscomponenten die met AEM worden verschepen omvatten de de Tekst, Titel, Cloud van de Markering, Carousel, Beeld, en componenten van de Lijst, allen beschikbaar bij de Sidekick bij runtime.

**de Vinder van de Inhoud** - op auteurswijze, is de Vinder van de Inhoud een speciaal paneel (kader) op de linkerkant van de pagina die, afhankelijk van het lusje u bij de bovenkant selecteert, lijsten van beelden, documenten, de activa van de Flash, pagina&#39;s, paragrafen, of opslagmiddelen toont die u van de Vinder van de Inhoud in de pagina kunt slepen u (op het recht) werkt.

**Digitale activa** - In AEM, zijn de Digitale Assets (typisch) beelden en rijke media dossiers. Zie Werken met Digital Assets in DAM voor meer informatie.

**Dispatcher** - Dispatcher is zowel een caching als lading-in evenwicht brengend hulpmiddel, en verstrekt bepaalde veiligheidswaarborgen.

**ExtJS widgets** - De meeste gebruiker-interface elementen in AEM gebruik ExtJS, die een derdewidgetbibliotheek is die in JavaScript wordt geschreven. ExtJS biedt krachtige, aanpasbare UI-widgets en een goed ontworpen en uitbreidbaar componentmodel.

**JCR, Java™ Content Repository** - de specificatie van de Bewaarplaats van de Inhoud Java™ (JSR-283) verstrekt zowel een abstract gegevensmodel als een Interface van de Programmering van de Toepassing voor het realiseren van een massief scalable gegevensbewaarplaats NoSQL die eigenschappen van een dossiersysteem en een objecten gegevensbestand combineert. Hoewel u JSR-283 niet in detail hoeft te begrijpen, moet u de tijd nemen om vertrouwd te maken met de basismogelijkheden van de JCR en het gegevensmodel dat eraan ten grondslag ligt, omdat JCR de filosofie van &quot;alles is inhoud&quot; van AEM mogelijk maakt.

In wezen, is JCR een systeem van knopen en eigenschappen, waarin de knopen van andere knopen kunnen erven en al inhoud wordt opgeslagen als bezit *waarden*. Naast de normale overerving biedt JCR ook een concept van &#39;mixin&#39;-knooppunten, waarmee meerdere overervingen kunnen worden gemodelleerd.

JCR heeft verscheidene vooraf bepaalde knooptypes en bezitstypes, maar over het algemeen is het typende systeem flexibel, en (inderdaad) één van de sterke punten van JCR is dat het gestructureerde en ongestructureerde inhoud om met gelijk gemak toelaat worden opgeslagen/worden beheerd. Dat wil zeggen dat JCR zeer gestructureerde gegevens kan verwerken, maar ook willekeurige dynamische gegevensstructuren zonder schemabeperkingen kan verwerken.

JavaDoc voor Java™ API van JCR is beschikbaar bij de [&#x200B; Stichting van de Software van Apache - JCR API &#x200B;](https://jackrabbit.apache.org/jcr/jcr-api.html).

Alvorens te proberen om JavaDoc of de specificatie JCR zelf te lezen, zou u [&#x200B; deze verklaring op hoog niveau &#x200B;](/help/sites-developing/the-basics.md#java-content-repository) van JCR kunnen bekijken zoals die door de Diensten van de Ervaring van de Adobe wordt uitgevoerd.

**Multisite Manager (MSM)** - De eigenschap MSM van AEM helpt klanten meertalige en multinationale inhoud behandelen, toelatend hen om gecentraliseerde branding met gelokaliseerde inhoud in evenwicht te brengen.

**OSGi** - OSGi is de op diensten-gebaseerde runtime technologie die de basis voor gemodulariseerde ontwikkeling Java™ in AEM verstrekt. Het is een kader dat niet alleen een hoogst dynamische (en veilige) het klassen laden en uitvoeren milieu voor codemiddelen (die als bundels worden bekend), maar ook volledige controle over de zichtbaarheid en de levenscyclus van de diverse diensten verstrekt die door bundels worden blootgesteld. Een de dienstregister verstrekt een samenwerkingsmodel voor bundels dat levenscyclusdynamiek (en versievereisten) rekening houdt. OSGi lost veel van de problemen op die de toepassingsservers bedoeld waren om op te lossen, maar doet dit op een lichtgewicht, hoogst dynamische manier, die het mogelijk maken, bijvoorbeeld, de diensten op te warmen-opstellen (die de nieuwe code onmiddellijk beschikbaar maken zonder de server opnieuw te beginnen).

**Parsys, Systeem van de Paragraaf** - het paragraafsysteem (parsys) is een samengestelde component die auteurs toestaat om componenten van verschillende types aan een pagina toe te voegen en andere paragraafcomponenten bevat. Elk alineatype wordt vertegenwoordigd als een component. Het alineasysteem zelf is ook een onderdeel dat de andere alineacomponenten bevat.

**Microkernel** - Elke werkruimte in de bewaarplaats kan afzonderlijk worden gevormd om zijn gegevens door een specifieke microkernel (een klasse op te slaan die het lezen en het schrijven van de gegevens beheert). Op dezelfde manier kan de gegevensopslagruimte-brede versieopslag ook onafhankelijk worden gevormd om een bepaalde microkernel te gebruiken. Er zijn verschillende microkorrels beschikbaar waarmee gegevens in verschillende bestandsindelingen of relationele databases kunnen worden opgeslagen. (Er zijn bijvoorbeeld persistentiemanagers voor MongoDB, DB2® of Oracle) De standaardmicrokernel voor AEM is TarMK (zie verder hieronder).

**instantie van Publish** - voor veiligheid, bestuur, en andere redenen, zal een productiesite instanties van AEM in de instanties van de Auteur en van Publish typisch verdelen. Raadpleeg de documentatie over AEM instanties voor meer informatie over de implementatiearchitectuur (inclusief de instanties van Auteur/Publish).

**QuickStart** - in tegenstelling tot vele andere programma&#39;s, installeert u AEM door één enkel &quot;Quickstart&quot;zelf-extracterend JAR dossier te gebruiken. Wanneer u voor het eerst op het JAR-bestand dubbelklikt, wordt alles wat u nodig hebt automatisch geïnstalleerd. De QuickStart JAR bevat alle bestanden die vereist zijn voor de CRX-opslagplaats (inclusief beheerfaciliteiten), virtuele opslagservices, index- en zoekservices, workflowservices, beveiliging en een webserver, plus de CQ Servlet Engine (CQSE) en alle AEM services. Er zijn geen andere bestanden om te installeren: de QuickStart is op zichzelf staand.

De eerste keer dat u de Quickstart start start, wordt op de achtergrond een volledige opslagplaats gemaakt die voldoet aan de JCR, wat enkele minuten kan duren. Na dit eerste opstarten zijn de volgende stappen veel sneller, aangezien de infrastructuur van de opslagplaats reeds is vastgelegd.

Vele opstartopties (zoals het actieve havenaantal en of de AEM instantie in kwestie een instantie van Publish tegenover een instantie van de Auteur zou moeten zijn; en veel meer) kunnen worden gecontroleerd door het dossier van QuickStart correct anders te noemen. Als u een lijst met opties op dit gebied wilt weergeven, voert u de JAR met &quot;-help&quot; uit op de opdrachtregel:

```shell
java -jar <quickstartfilename>.jar -help
```

**de agenten van de Replicatie** - de agenten van de Replicatie zijn centraal om als mechanisme te AEM dat aan de (activeer) inhoud van Publish van een auteur aan publiceer milieu wordt gebruikt; flush inhoud van het geheime voorgeheugen van Dispatcher; terugkeer user-generated inhoud (bijvoorbeeld, vorminput) van het milieu van Publish aan het milieu van de Auteur.

**Basisstructuur** - met steigers kunt u een vorm (een steigers) met gebieden tot stand brengen die op de structuur wijzen u voor uw pagina&#39;s wilt en dan deze vorm gebruiken om pagina&#39;s tot stand te brengen die op deze structuur worden gebaseerd.

**Segmentatie** - de bezoekers van de Plaats hebben verschillende belangen en doelstellingen wanneer zij aan een plaats komen. Kennis van de doelstellingen van bezoekers en het vervullen van hun verwachtingen is een belangrijke voorwaarde voor online marketing. Segmentering helpt dit te bereiken door de details van een bezoeker te analyseren en te karakteriseren.

**Sidekick** - de Sidekick is een palet-als drijvend venster dat op de editable pagina verschijnt, waarvan de nieuwe componenten kunnen worden gesleept en de acties die op de pagina van toepassing zijn kunnen worden uitgevoerd.

**Katalysator van de Plaats** - de SiteCatalyst verstrekt marketers één plaats om, geïntegreerde gegevens van alle online initiatieven over veelvoudige marketing kanalen te meten te analyseren en te optimaliseren. U kunt Adobe SiteCatalyst gebruiken om gegevens van AEM websites te analyseren.

**Opslag van de Tar (TarMK)** - TarMK is het standaardpersistentiesysteem in AEM. Hoewel AEM kan worden geconfigureerd om een ander persistentiesysteem te gebruiken (zoals MongoDB), heeft TarMK bepaalde voordelen omdat het prestatiegeoptimaliseerd is voor typische JCR-gebruiksscenario&#39;s (daarom snel), gebruikmaakt van een industriestandaard gegevensformaat en snel en eenvoudig back-ups kan maken.

**Malplaatje** - in AEM, specificeert een Malplaatje een bepaald type van pagina. Hiermee wordt de structuur van een pagina gedefinieerd (waarbij doorgaans ook een miniatuurafbeelding en diverse eigenschappen worden opgegeven). U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens.

**Werkschema** - het systeem van het Werkschema van de AEM staat voor verwezenlijking van geautomatiseerde processen toe die pagina&#39;s of activa impliceren.
