---
title: Bijdragen aan AEM
seo-title: Bijdragen aan AEM
description: AEM wordt ontwikkeld volgens beproefde methodologieën die algemeen worden toegepast in grote open-sourceprojecten
seo-description: AEM wordt ontwikkeld volgens beproefde methodologieën die algemeen worden toegepast in grote open-sourceprojecten
uuid: ffef60ae-8a9a-4c4b-8cbd-3cd72792a42e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f52402df-f6dc-4c62-82bc-cbce489b2b74
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Bijdragen aan AEM{#contributing-to-aem}

## Ontwikkelingsmethode {#development-methodology}

AEM wordt ontwikkeld volgens beproefde methodologieën die algemeen worden toegepast in grote open-sourceprojecten. Veel kernelementen in de technologiestapel van AEM worden in feite gehandhaafd als actieve open-bronprojecten, zoals Sling en Jackrabbit, die werden bijgedragen aan de Apache Software Foundation. Een belangrijk aspect van deze geest dat in AEM aanwezig is, is dat u wordt aangemoedigd om de beschikbare mailinglijsten en online forums voor directe interactie met het ontwikkelingsteam te gebruiken.

Als u aan componenten van AEM bijdraagt, zou u zich met AEM moeten vertrouwd maken zoals u wanneer het bijdragen aan een open-bronproject, en met het bestaande kernteam zou communiceren aangezien u zou wanneer u aan zulk een project zou willen bijdragen.

## Vereiste ervaring {#required-experience}

Het HyperText Transfer Protocol (HTTP) is centraal bij alles wat we doen. Daarom alvorens tot AEM bij te dragen, zou u een diep inzicht in HTTP moeten hebben, idealiter in die mate waarin u uw eigen implementatie van Java van een multithreaded server van HTTP met draad-pooling zou kunnen schrijven. U zou ook inzicht in HTTP/1.1 moeten hebben houdt-levend gedrag, en u zou een diepgaande kennis van server/cliënt-zijinteractie met JavaScript, vooral de asynchrone stijl van interactie moeten hebben die door AJAX wordt vertegenwoordigd.

Omdat de paginadynamiek en de interactieve inhoud zeer belangrijk voor de ervaring WM zijn, is het essentieel dat u een vrij diep inzicht in het Model van de Objecten van het Document en zijn potentieel voor programmatic manipulatie in reactie op gebeurtenissen hebt. U moet enige kennis hebben van bijvoorbeeld DOM-manipulatie en gedrag bij slepen en neerzetten in meerdere browserdocumenten (bijvoorbeeld met iframes).

Op het hoogste niveau zou u dan een stevig inzicht moeten hebben in:

* het [HTTP/1.1-protocol](https://www.ietf.org/rfc/rfc2616.txt)
* HTML (bij voorkeur [HTML5](https://dev.w3.org/html5/spec/Overview.html))
* Cascading Style Sheets
* Extensible Markup Language (XML)
* Asynchrone JavaScript- en XML-ontwerppatronen (AJAX)
* JavaScript Object Notation (JSON)
* het Document Object Model
* Stateful versus stateless interacties
* [Uniform Resource Identifiers](https://www.ietf.org/rfc/rfc2396.txt)
* Browsercookies
* en andere moderne concepten voor webontwikkeling

De technologiestapel van Adobe Experience Manager is gebaseerd op de [Apache Felix](https://felix.apache.org/) OSGI-container met het [Apache Sling](https://sling.apache.org/site/index.html) -webframework en sluit een Java Content Repository ([JCR](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/index.html)) in op basis van [Apache Jackrabbit](https://jackrabbit.apache.org/jcr-api.html). U moet vertrouwd raken met deze afzonderlijke projecten en met andere open-sourcecomponenten (zoals Apache Lucene) die worden gebruikt in het gebied waar u een bijdrage wilt leveren.

## Tribunale kennis {#tribal-knowledge}

Bepaalde concepten en leidende beginselen zijn diep verankerd in de cultuur van de voormalige Dag. Deze sectie bevat een aantal van de &quot;diepgebedde DNA-ingebedde&quot; problemen die u moet kennen.

### Alles is inhoud {#everything-is-content}

De inhoud bevat niet alleen alle gegevens die de webtoepassing blijvend maakt. De programmacode, bibliotheken, manuscripten, malplaatjes, HTML, CSS, beelden, en artefacten van alle soorten, om het even wat en alles wordt voortgeduurd in de Bewaarplaats van de Inhoud en ingevoerd/uitgevoerd in de vorm van pakketten via de Manager van het Pakket en het Aandeel van het Pakket.

### David&#39;s Model {#david-s-model}

De manier waarop inhoud in een Java Content Repository moet worden gemodelleerd, vereist een totaal andere manier van denken dan wat in de softwareindustrie voor gegevensmodellering in de relationele wereld gebruikelijk is. De JCR-manier is essentieel voor het lezen van elke nieuwkomer op het gebied van contentbeheer: [David&#39;s Model: Een handleiding voor het modelleren](https://wiki.apache.org/jackrabbit/DavidsModel)van inhoud.

### RESTfulness {#restfulness}

De REST-benadering is diep verankerd in wat we doen. Dit betekent onder andere dat stateful interacties moeten worden vermeden en dat URI&#39;s definitieve adressen zijn voor inhoud en services.

REST (REpresentational State Transfer) verwijst naar de software architecturale stijl waarop het World Wide Web is gebaseerd. Het beschrijft de belangrijkste elementen die het Web maken werken, en verstrekt zo een reeks principes voor hoe Web-based software zou moeten worden ontworpen. Bij het ontwerpen van een API die via het web moet worden gebruikt, is het daarom verstandig om deze &#39;best practices&#39; te volgen.

Omdat REST de leidende filosofie achter zoveel van wat wij doen is, moet u het van essentieel belang vinden om goed doordrongen te raken in de grondbeginselen van RESTful design. Een goede plek om te beginnen is met de dessertatie van [Roy Fielding](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

### Oplossing voor een aanvraag voor verzending {#sling-request-resolution}

Een belangrijk aspect om inzicht te krijgen in AEM is hoe binnenkomende aanvragen betrekking hebben op inhoud en toepassingsgedrag, hoe inhoud is gestructureerd in de inhoudsopslagplaats en waar AEM zoekt naar de toepassingslogica om de aanvraag af te handelen. Meer informatie over de Apache [Sling URL-decompositie](https://sling.apache.org/site/url-decomposition.html) en de manier waarop deze de REST-architecturale stijl en de stateless, cacheable en gelaagde systeembeperkingen afdwingt.

De belangrijkste aspecten die u moet begrijpen van de aanvraagresolutie van Apache Sling zijn hoe aanvragen primair worden toegewezen aan een specifieke bron in de inhoudsopslagplaats, hoe aanvullende eigenschappen van de aanvraag, samen met eigenschappen van deze inhoudsobjecten, bepalen welke toepassingscode wordt aangeroepen om de inhoud te renderen en hoe code in /apps code in /libs overschrijft.

### QuickStart {#quickstart}

Geen stap drie: Als u wilt installeren en uitvoeren, downloadt en dubbelklikt u gewoon op het QuickStart JAR-bestand. Er is geen stap drie. Voor extra optionele functies hoeft u alleen het juiste pakket te installeren vanuit Package Share.

Kleine snelstartgrootte: Houd het bestand QuickStart JAR minimaal. Maak slim, geoptimaliseerd gebruik van bibliotheken en verplaats optionele functionaliteit naar pakketdeling.

Snellere opstarttijd: Wanneer u een verandering aanbrengt die de starttijd zou kunnen beïnvloeden, zorg ervoor het korter, niet langer zal maken.

### Lean en Mean {#lean-and-mean}

We zijn voor code en projecten die licht, klein, snel en elegant zijn. &quot;Goed genoeg&quot; is niet goed genoeg.

Hergebruik van code: Onze OSGi-gebaseerde productarchivering en &quot;alles is inhoud&quot; filosofie betekent dat we ongewoon goede mogelijkheden hebben om code en artefacten opnieuw te gebruiken. We proberen zo veel mogelijk van dat feit te profiteren om functies mager en gemiddeld te houden.

Losse koppeling: We zijn voor losjes gekoppelde interacties boven strakke afhankelijkheden en &quot;ongewenste intimiteit&quot;. Met losse koppeling kunt u ook meer code hergebruiken.

### De demo niet breken {#don-t-break-the-demo}

Word vertrouwd met demoscripts en productfuncties die het vaakst in demo&#39;s worden getoond. Begrijp dat, op zijn minst, niets u zou moeten ooit een &quot;demo manuscript&quot;eigenschap breken. Het kernproduct moet altijd demo-klaar zijn, zelfs tijdens de ontwikkeling.

### Ontwerpen voor betrouwbaarheid {#design-for-reliability}

We streven ernaar om functies te ontwerpen en te coderen op faalveilige wijze, zodat (bijvoorbeeld) een probleem met één DOM-element er niet toe leidt dat een hele pagina niet wordt weergegeven. Met andere woorden: Maak dingen die fataal, fataal zouden moeten zijn. Laat alles overleven. Maak het product &#39;vergeven&#39;.

### Abnormal is the New Normal {#abnormal-is-the-new-normal}

Vertrouw niet op stophaken, zorg ervoor dat u opschoont bij het opstarten. Abnormale beëindiging is normale beëindiging.

`shutdown == kill -9 == power outage`

### Wees klaar voor elastische clustering {#be-ready-for-elastic-clustering}

Altijd klaar voor elastische groepering zijn, veronderstel altijd dat er zich het groeperen is. Als algemene regel, die aan alles zich in de inhoudsbewaarplaats houden betekent ingebouwde het groeperen steun.

### Ontwerpen voor achterwaartse Verenigbaarheid {#design-for-backward-compatibility}

Niets u zou de oude code van een klant moeten breken. Denk na slechts productcode `/libs` te bevatten die tijdens een verbetering kan worden bijgewerkt. De `/apps` sectie van de bewaarplaats is projectcode, en de `/etc` sectie bevat douaneconfiguraties die moeten worden bewaard. In het algemeen moet u niets overschrijven in `/apps`, `/content` en `/home`. Na een verbetering, zou oude projectcode, configuraties en inhoud moeten blijven functioneren zoals het allen vóór de verbetering deed.

Het ontwerpen voor achterwaartse verenigbaarheid zorgt ook dat de verbeteringservaring de eenvoud van de aanvankelijke installatie aanpast. U kunt AEM alleen stoppen, het QuickStart JAR-bestand vervangen en AEMagain starten. Dit is voldoende. Met een snel groeiende installatiebasis zal de efficiëntie van upgrades een steeds groter voordeel opleveren.

Bestaande API&#39;s kunnen en moeten worden gemarkeerd als afgekeurd wanneer ze nieuwer zijn, maar een betere functionaliteit vervangt ze, alle API&#39;s die in een vorige versie van 5.x openbaar zijn gemaakt, moeten functioneel blijven, omdat ze in de aangepaste toepassingscode kunnen worden gebruikt. Dergelijke API&#39;s moeten niet worden verwijderd.

Achterwaartse compatibiliteit moet ook in aanmerking worden genomen met het oog op de algemene consistentie van de inhoudstructuur en de gebruikerservaring.

## Basisconcepten {#core-concepts}

**Instantie** van auteur - Gewoonlijk, voor veiligheid, bestuur, en andere redenen, zal een productiesite instanties van AEM in auteur en Publish instanties verdelen. Raadpleeg de documentatie over AEM-instanties voor meer informatie over de implementatiearchitectuur (inclusief de instanties Auteur/Publiceren).

**Caching, het bakken, en het bakken** - Traditioneel, zijn de concepten bakken versus het bakken een belangrijk onderscheid tussen verschillende systemen van het Inhoudsbeheer van het Web. In CMS-jargon verwijst &quot;bakken&quot; naar het begrip &quot;vastleggen&quot; van gegevens aan statische bestanden tijdens de publicatietijd, terwijl &quot;fritten&quot; verwijst naar het concept van het verwerken van gegevens voor de uiteindelijke presentatie op aanvraag-tijd (d.w.z. net op tijd).

**Clustering en taakverdeling** - Om de beschikbaarheid te verhogen en de prestaties van een productieomgeving te verbeteren, is het gebruikelijk om meerdere instanties Auteur en/of Publiceren (in clusters) te combineren door deze beschikbaar te stellen aan verschillende groepen gebruikers of door ze in evenwicht te brengen met de werkbelasting achter een Dispatcher-configuratie.

Het is ook mogelijk om meerdere exemplaren van de opslagplaats voor inhoud te combineren om een JCR-oplossing met *hoge beschikbaarheid* te maken, die vervolgens kan worden geïntegreerd met uw AEM-oplossing om de bescherming tegen hardware- en softwarefout te maximaliseren. Zie [Aanbevolen Inzet](/help/sites-deploying/recommended-deploys.md#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter) voor meer informatie.

**Component** - In AEM is een component een objecttype, waarvan instanties doorgaans kunnen worden gemaakt door ze van bijvoorbeeld de Sidetrap te slepen en neer te zetten. Bijvoorbeeld, buiten-de-dooscomponenten die met AEM worden verscheept omvatten de de Tekst, Titel, Cloud van de Markering, Carousel, Beeld, en componenten van de Lijst, allen beschikbaar bij Sidetrap bij runtime.

**Inhoudszoeker** - In de ontwerpmodus is de Inhoudszoeker een speciaal deelvenster (frame) aan de linkerkant van de pagina dat, afhankelijk van het tabblad dat u boven selecteert, lijsten weergeeft met afbeeldingen, documenten, Flash-elementen, pagina&#39;s, alinea&#39;s of opslagplaatsen die u kunt slepen en neerzetten van de Inhoudszoeker naar de pagina waaraan u werkt (aan de rechterkant).

**Digitale middelen** - In AEM zijn digitale middelen (doorgaans) afbeeldingen en rich media-bestanden. Zie Werken met Digital Assets in DAM voor meer informatie.

**Dispatcher** - De Dispatcher is zowel een caching- als een taakverdelingsmechanisme en biedt bepaalde beveiligingswaarborgen.

**ExtJS-widgets** - De meeste gebruikersinterface-elementen in AEM maken gebruik van ExtJS, een externe widgetbibliotheek die in JavaScript is geschreven. ExtJS biedt krachtige, aanpasbare UI-widgets en een goed ontworpen en uitbreidbaar componentmodel.

**JCR, Java Content Repository** - De Java Content Repository Specification (JSR-283) biedt zowel een abstract gegevensmodel als een Application Programming Interface voor het realiseren van een enorm schaalbare NoSQL-gegevensopslagruimte waarin functies van een bestandssysteem en een objectdatabase worden gecombineerd. Hoewel u JSR-283 niet in detail hoeft te begrijpen, moet u de tijd nemen om vertrouwd te maken met de basismogelijkheden van JCR en het gegevensmodel dat eraan ten grondslag ligt, omdat JCR de filosofie &#39;alles is inhoud&#39; van AEM mogelijk maakt.

In wezen is JCR een systeem van knooppunten en eigenschappen, waarin knooppunten kunnen overerven van andere knooppunten en alle inhoud wordt opgeslagen als *eigenschapswaarden*. Naast de normale overerving maakt JCR een concept van &#39;mixin&#39;-knooppunten mogelijk, waarmee meerdere overervingen kunnen worden gemodelleerd.

JCR heeft een aantal vooraf bepaalde knooptypes en bezitstypes, maar over het algemeen is het typende systeem vrij flexibel, en (inderdaad) één van de sterke punten van JCR is dat het gestructureerde en ongestructureerde inhoud om met gelijk gemak toelaat worden opgeslagen/worden beheerd. Dat wil zeggen dat JCR zeer gestructureerde gegevens kan verwerken, maar ook willekeurige dynamische gegevensstructuren zonder schemabeperkingen kan verwerken.

De JavaDoc voor de Java API van JCR is [hier](http://jackrabbit.apache.org/jcr/jcr-api.html).

Voordat u probeert de JavaDoc- of JCR-specificatie zelf te lezen, kunt u [deze uitleg](/help/sites-developing/the-basics.md#java-content-repository) op hoog niveau van JCR bekijken zoals deze is geïmplementeerd door Adobe Experience Services.

**MSM (Multi-Site Manager)** - Met de MSM-functie van AEM kunnen klanten meertalige en multinationale inhoud verwerken, waardoor ze gecentraliseerde branding in evenwicht kunnen brengen met gelokaliseerde inhoud.

**OSGi** - OSGi is de op diensten-gebaseerde runtime technologie die de basis voor gemodulariseerde ontwikkeling van Java in AEM verstrekt. Het is een kader dat niet alleen een hoogst dynamische (en veilige) het klassen laden en uitvoeren milieu voor codemiddelen (die als bundels worden bekend), maar ook volledige controle over de zichtbaarheid en de levenscyclus van de diverse diensten verstrekt die door bundels worden blootgesteld. Een de dienstregister verstrekt een samenwerkingsmodel voor bundels dat levenscyclusdynamiek (en versievereisten) rekening houdt. OSGi lost veel van de problemen op die de toepassingsservers bedoeld waren om op te lossen, maar doet dit op een lichtgewicht, hoogst dynamische manier, die het mogelijk maken, bijvoorbeeld, de diensten op te warmen-opstellen (die de nieuwe code onmiddellijk beschikbaar maken zonder de server opnieuw te beginnen).

**Parsys, het Systeem** van de Paragraaf - het paragraafsysteem (parsys) is een samengestelde component die auteurs toestaat om componenten van verschillende types aan een pagina toe te voegen en andere paragraafcomponenten bevat. Elk alineatype wordt vertegenwoordigd als een component. Het alineasysteem zelf is ook een onderdeel dat de andere alineacomponenten bevat.

**Microkernel** - Elke werkruimte in de opslagplaats kan afzonderlijk worden geconfigureerd om de gegevens op te slaan via een specifieke microkernel (een klasse die het lezen en schrijven van de gegevens beheert). Op dezelfde manier kan de gegevensopslagruimte-brede versieopslag ook onafhankelijk worden gevormd om een bepaalde microkernel te gebruiken. Er is een aantal verschillende microkorrels beschikbaar waarmee gegevens in verschillende bestandsindelingen of relationele databases kunnen worden opgeslagen. (Er zijn bijvoorbeeld persistentiemanagers voor MongoDB, DB2 of Oracle) De standaard microkernel voor AEM is TarMK (zie verder hieronder).

**Publicatie-instantie** - Voor beveiliging, beheer en andere redenen deelt een productiesite doorgaans instanties van AEM op in instanties Auteur en Publiceren. Raadpleeg de documentatie over AEM-instanties voor meer informatie over de implementatiearchitectuur (inclusief de instanties Auteur/Publiceren).

**QuickStart** - In tegenstelling tot veel andere programma&#39;s installeert u AEM met behulp van één zelfuitpakkend JAR-bestand &quot;QuickStart&quot;. Wanneer u voor het eerst op het JAR-bestand dubbelklikt, wordt alles wat u nodig hebt automatisch geïnstalleerd. De QuickStart JAR omvat alle bestanden die vereist zijn voor de CRX-opslagplaats (inclusief beheerfaciliteiten), virtuele opslagservices, index- en zoekservices, workflowservices, beveiliging en een webserver, plus de CQ Servlet Engine (CQSE) en alle AEM-services. Er zijn geen andere bestanden om te installeren: De QuickStart is op zichzelf staand.

De eerste keer dat u de Quickstart start start, wordt op de achtergrond een volledige opslagplaats gemaakt die voldoet aan de JCR, wat enkele minuten kan duren. Na dit eerste opstarten zijn de volgende stappen veel sneller, aangezien de infrastructuur van de opslagplaats reeds is vastgelegd.

Vele opstartopties (zoals het actieve havenaantal en of de instantie AEM in kwestie een Publish instantie tegenover een instantie van de Auteur zou moeten zijn; en nog veel meer) kunt u beheren door de naam van het QuickStart-bestand op de juiste manier te wijzigen. Als u een lijst met opties op dit gebied wilt weergeven, voert u de JAR met &quot;-help&quot; uit op de opdrachtregel:

```shell
java -jar <quickstartfilename>.jar -help
```

**Replicatieagents** - Replicatieagents staan centraal in AEM als het mechanisme dat wordt gebruikt om inhoud van een auteur naar een publicatieomgeving te publiceren (activeren). inhoud uit de Dispatcher-cache verwijderen; door de gebruiker gegenereerde inhoud (bijvoorbeeld formulierinvoer) vanuit de publicatieomgeving terugsturen naar de auteur-omgeving.

**Basisstructuur** - Met basisstructuur kunt u een formulier (een basisblad) maken met velden die de gewenste structuur voor uw pagina&#39;s weerspiegelen. Met dit formulier kunt u eenvoudig pagina&#39;s maken op basis van deze structuur.

**Segmentatie** - bezoekers van de site hebben verschillende belangen en doelstellingen wanneer ze naar een site komen. Kennis van de doelstellingen van bezoekers en het vervullen van hun verwachtingen is een belangrijke voorwaarde voor online marketing. Segmentering helpt dit te bereiken door de details van een bezoeker te analyseren en te karakteriseren.

**Sidetrap** - De Sidetrap is een paletachtig zwevend venster dat op de bewerkbare pagina wordt weergegeven, waaruit nieuwe componenten kunnen worden gesleept en acties die op de pagina van toepassing zijn, kunnen worden uitgevoerd.

**Site Catalyst** - SiteCatalyst biedt marketers één locatie voor het meten, analyseren en optimaliseren van geïntegreerde gegevens van alle online initiatieven via meerdere marketingkanalen. U kunt Adobe SiteCatalyst gebruiken om gegevens van AEM-websites te analyseren.

**Tar Storage (TarMK)** - TarMK is het standaard persistentiesysteem in AEM. Hoewel AEM kan worden gevormd om een verschillend persistentiesysteem (zoals MongoDB) te gebruiken, heeft TarMK bepaalde voordelen in zoverre dat het prestaties-geoptimaliseerd voor typisch gebruik JCR (zo is zeer snel) is, een industrie-standaardgegevensformaat gebruikt, en kan snel en gemakkelijk worden gesteund.

**Sjabloon** - In AEM geeft een sjabloon een bepaald type pagina op. Hiermee wordt de structuur van een pagina gedefinieerd (terwijl doorgaans ook een miniatuurafbeelding en diverse eigenschappen worden opgegeven). U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens.

**Workflow** - Met het AEM-workflowsysteem kunt u geautomatiseerde processen maken waarbij pagina&#39;s of elementen worden gebruikt.
