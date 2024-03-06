---
title: Bijdragen aan AEM
description: AEM wordt ontwikkeld op basis van beproefde methodologieën die algemeen worden toegepast in grote open-source-projecten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 43fb4fa3-269a-4635-b055-4b7d787da21f
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '2635'
ht-degree: 0%

---

# Bijdragen aan AEM{#contributing-to-aem}

## Ontwikkelingsmethode {#development-methodology}

AEM wordt ontwikkeld op basis van beproefde methodologieën die algemeen worden toegepast in grote open-source-projecten. Veel kernelementen in AEM technologiestapel worden in feite gehandhaafd als actieve open-sourceprojecten, zoals Sling en Jackrabbit, die werden bijgedragen aan de Apache Software Foundation. Een belangrijk aspect van deze geest dat in AEM aanwezig is, is dat u wordt aangemoedigd om de beschikbare mailinglijsten en online forums voor directe interactie met het ontwikkelingsteam te gebruiken.

Als u aan componenten van AEM bijdraagt, vertrouwt u met AEM zoals u wanneer het bijdragen aan een open-bronproject, en communiceert met het bestaande kernteam zoals u zou wanneer u van plan bent om aan zulk een project bij te dragen.

## Vereiste ervaring {#required-experience}

Het HyperText Transfer Protocol (HTTP) is centraal bij alles wat we doen. Daarom alvorens tot AEM bij te dragen, zou u een diep inzicht in HTTP moeten hebben, idealiter in de mate waarin u uw eigen implementatie Java™ van een multithreaded server van HTTP met draad-pooling kunt schrijven. U zou ook een inzicht in het gedrag van HTTP/1.1 moeten hebben het houden-Levend, en u zou een diepgaande kennis van server/cliënt-zijinteractie met JavaScript moeten hebben, in het bijzonder de asynchrone stijl van interactie die door AJAX wordt vertegenwoordigd.

Omdat de paginadynamiek en de interactieve inhoud zeer belangrijk voor de ervaring WM zijn, is het essentieel dat u een vrij diep inzicht in het Model van de Objecten van het Document en zijn potentieel voor programmatic manipulatie in reactie op gebeurtenissen hebt. U zou wat kennis, bijvoorbeeld, van DOM manipulatie in real time en belemmering-en-dalingsgedrag over veelvoudige browser documenten (bijvoorbeeld, het gebruiken van iframes) moeten hebben.

Op het hoogste niveau zou u een stevig inzicht in moeten hebben:

* de [HTTP/1.1-protocol](https://www.ietf.org/rfc/rfc2616.txt)
* HTML (bij voorkeur [HTML 5](https://html.spec.whatwg.org/))
* Cascading Style Sheets
* Extensible Markup Language (XML)
* Asynchrone JavaScript- en XML-ontwerppatronen (AJAX)
* JavaScript Object Notation (JSON)
* het Document Object Model
* Stateful versus stateless interacties
* [Uniform Resource Identifiers](https://www.ietf.org/rfc/rfc2396.txt)
* Browsercookies
* en andere moderne concepten voor webontwikkeling

De technologiestapel van Adobe Experience Manager is gebaseerd op de [Apache Felix](https://felix.apache.org/documentation/index.html) OSGI-container met de [Apache Sling](https://sling.apache.org/index.html) webframework en sluit een Java™ Content Repository in ([JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)) gebaseerd op [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/jcr-api.html). Maak kennis met deze afzonderlijke projecten en met andere open-source-componenten (bijvoorbeeld Apache Lucene) die worden gebruikt in het gebied waar u een bijdrage wilt leveren.

## Tribunale kennis {#tribal-knowledge}

Bepaalde concepten en leidende beginselen zijn diep verankerd in de cultuur van de voormalige Dag. Deze sectie bevat een aantal van de &quot;diep DNA-ingebedde&quot; problemen die u dient te kennen.

### Alles is inhoud {#everything-is-content}

De inhoud bevat niet alleen alle gegevens die de webtoepassing blijvend maakt. De programmacode, bibliotheken, manuscripten, malplaatjes, HTML, CSS, beelden, en artefacten van alle soorten, om het even wat, en alles wordt voortgeduurd in de Bewaarplaats van de Inhoud en ingevoerd/uitgevoerd in de vorm van pakketten via de Manager van het Pakket en het Aandeel van het Pakket.

### David&#39;s Model {#david-s-model}

Voor het modelleren van inhoud in een Java™ Content Repository is een totaal andere manier van denken nodig dan wat in de softwareindustrie gebruikelijk is voor het modelleren van gegevens in de relationele wereld. Essentieel lezen voor elke nieuwkomer voor contentbeheer op de JCR-manier is [David&#39;s Model: Een gids voor het modelleren van inhoud](https://wiki.apache.org/jackrabbit/DavidsModel).

### RESTfulness {#restfulness}

De REST-benadering is diep verankerd in wat we doen. Dit betekent onder andere dat stateful interacties moeten worden vermeden en dat URI&#39;s definitieve adressen zijn voor inhoud en services.

REST (REpresentational State Transfer) verwijst naar de software architecturale stijl waarop het World Wide Web is gebaseerd. Het beschrijft de belangrijkste elementen die het Web maken werken, en verstrekt zo een reeks principes voor hoe Web-based software zou moeten worden ontworpen. Bij het ontwerpen van een API die via het web moet worden gebruikt, is het daarom verstandig om deze &#39;best practices&#39; te volgen.

Omdat REST de leidende filosofie achter zoveel van wat wij doen is, moet u het van essentieel belang vinden om goed verdraaid te worden in de grondbeginselen van RESTful design. Een goede plek om te beginnen is met [Roy Fielding](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

### Oplossing voor een aanvraag voor verzending {#sling-request-resolution}

Een belangrijk aspect om te begrijpen over AEM is hoe binnenkomende verzoeken betrekking hebben op inhoud en toepassingsgedrag, hoe inhoud is gestructureerd in de inhoudsopslagplaats en waar AEM zoekt naar de toepassingslogica om de aanvraag af te handelen. Meer informatie over de Apache [URL-decompositie instellen](https://sling.apache.org/documentation/the-sling-engine/url-decomposition.html) en de manier waarop het de architecturale stijl REST en zijn stateless, cacheable, en gelaagde systeembeperkingen handhaaft.

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

Niets u zou de oude code van een klant moeten breken. Alleen overwegen `/libs` om productcode te bevatten die tijdens een verbetering kan worden bijgewerkt. De `/apps` deel van de gegevensopslagruimte bestaat uit projectcode en de `/etc` bevat aangepaste configuraties die moeten worden behouden. In het algemeen moet u niets overschrijven in `/apps`, `/content`, en `/home`. Na een verbetering, zou oude projectcode, configuraties, en inhoud moeten blijven functioneren aangezien het allen vóór de verbetering deed.

Het ontwerpen voor achterwaartse verenigbaarheid zorgt ook dat de verbeteringservaring de eenvoud van de aanvankelijke installatie aanpast. Het zou voldoende zijn om AEM te stoppen, het JAR-bestand voor QuickStart te vervangen en opnieuw AEM te starten. Met een snel groeiende installatiebasis is upgradeefficiëntie een steeds belangrijker voordeel.

Bestaande API&#39;s kunnen en moeten worden gemarkeerd als afgekeurd wanneer ze nieuwer zijn, maar een betere functionaliteit vervangt ze, alle API&#39;s die in een vorige versie van 5.x openbaar zijn gemaakt, moeten functioneel blijven, omdat ze in de aangepaste toepassingscode kunnen worden gebruikt. Dergelijke API&#39;s moeten niet worden verwijderd.

Achterwaartse compatibiliteit moet ook in aanmerking worden genomen met betrekking tot de algemene consistentie van de inhoudsstructuur en gebruikerservaring.

## Basisconcepten {#core-concepts}

**Instantie van auteur** - Gewoonlijk worden instanties van AEM door een productiesite om beveiligings-, bestuurs- en andere redenen opgedeeld in instanties van Auteurs en Publiceren. Voor meer informatie over plaatsingsarchitectuur (met inbegrip van auteur/publiceer instanties), zie documentatie over AEM Instanties.

**Caching, fritten en bakken** - Traditioneel zijn de concepten bakken versus fritten een belangrijk onderscheid tussen verschillende systemen voor het beheer van webinhoud. In CMS-jargon verwijst &quot;bakken&quot; naar het concept van het toewijzen van gegevens aan statische bestanden tijdens de publicatietijd, terwijl &quot;fritten&quot; verwijst naar het concept van het verwerken van gegevens voor de uiteindelijke presentatie op aanvraag-tijd (dat wil zeggen net op tijd).

**Clustering en taakverdeling** - Om de beschikbaarheid te verhogen en de prestaties van een productieomgeving te verbeteren, is het gebruikelijk om meerdere instanties Auteur en/of Publiceren (in clusters) te combineren, door deze beschikbaar te stellen aan verschillende groepen gebruikers of door ze in evenwicht te brengen achter een Dispatcher-configuratie.

Het is ook mogelijk om meerdere instanties van de opslagplaats voor inhoud te combineren om een *hoge beschikbaarheid* JCR-oplossing, die vervolgens met uw AEM-oplossing kan worden geïntegreerd om de bescherming tegen hardware- en softwarestoringen te maximaliseren. Zie [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter) voor nadere informatie.

**Component** - In AEM is een component een objecttype, waarvan instanties doorgaans kunnen worden gemaakt door ze van bijvoorbeeld de Sidekick te slepen en neer te zetten. Bijvoorbeeld, buiten-de-dooscomponenten die met AEM worden verschepen omvatten de de Tekst, Titel, Cloud van de Markering, Carousel, Beeld, en componenten van de Lijst, allen beschikbaar bij de Sidekick bij runtime.

**Inhoudzoeker** - In de ontwerpmodus is de Content Finder een speciaal deelvenster (frame) aan de linkerkant van de pagina dat, afhankelijk van het tabblad dat u boven selecteert, lijsten weergeeft met afbeeldingen, documenten, elementen van de Flash, pagina&#39;s, alinea&#39;s of opslagplaatsen die u vanuit de Content Finder kunt slepen en neerzetten op de pagina waaraan u werkt (aan de rechterkant).

**Digitale middelen** - In AEM zijn digitale elementen (doorgaans) afbeeldingen en rich media-bestanden. Zie Werken met Digital Assets in DAM voor meer informatie.

**Dispatcher** - De verzender is zowel een caching als lading-in evenwicht brengend hulpmiddel, en verstrekt bepaalde veiligheidswaarborgen.

**ExtJS-widgets** - De meeste gebruikersinterface-elementen in AEM gebruiken ExtJS, een externe widgetbibliotheek die in JavaScript is geschreven. ExtJS biedt krachtige, aanpasbare UI-widgets en een goed ontworpen en uitbreidbaar componentmodel.

**JCR, Java™ Content Repository** - De Java™ Content Repository Specification (JSR-283) biedt zowel een abstract gegevensmodel als een Application Programming Interface voor het realiseren van een enorm schaalbare NoSQL-gegevensopslagruimte waarin functies van een bestandssysteem en een objectdatabase worden gecombineerd. Hoewel u JSR-283 niet in detail hoeft te begrijpen, moet u de tijd nemen om vertrouwd te maken met de basismogelijkheden van de JCR en het gegevensmodel dat eraan ten grondslag ligt, omdat JCR de filosofie van &quot;alles is inhoud&quot; van AEM mogelijk maakt.

In wezen is JCR een systeem van knooppunten en eigenschappen, waarin knooppunten kunnen overerven van andere knooppunten en alle inhoud wordt opgeslagen als eigenschap *waarden*. Naast de normale overerving biedt JCR ook een concept van &#39;mixin&#39;-knooppunten, waarmee meerdere overervingen kunnen worden gemodelleerd.

JCR heeft verscheidene vooraf bepaalde knooptypes en bezitstypes, maar over het algemeen is het typende systeem flexibel, en (inderdaad) één van de sterke punten van JCR is dat het gestructureerde en ongestructureerde inhoud om met gelijk gemak toelaat worden opgeslagen/worden beheerd. Dat wil zeggen dat JCR zeer gestructureerde gegevens kan verwerken, maar ook willekeurige dynamische gegevensstructuren zonder schemabeperkingen kan verwerken.

De JavaDoc voor de Java™-API van JCR is [hier](https://jackrabbit.apache.org/jcr/jcr-api.html).

Voordat u probeert de JavaDoc- of JCR-specificatie zelf te lezen, is het verstandig [deze verklaring op hoog niveau](/help/sites-developing/the-basics.md#java-content-repository) van JCR zoals geïmplementeerd door Adobe Experience Services.

**MSM (Multi-Site Manager)** - De MSM-functie van AEM helpt klanten meertalige en multinationale content te verwerken, waardoor ze gecentraliseerde branding in evenwicht kunnen brengen met gelokaliseerde content.

**OSGi** - OSGi is de op diensten-gebaseerde runtime technologie die de basis voor gemoduleerde ontwikkeling Java™ in AEM verstrekt. Het is een kader dat niet alleen een hoogst dynamische (en veilige) het klassen laden en uitvoeren milieu voor codemiddelen (die als bundels worden bekend), maar ook volledige controle over de zichtbaarheid en de levenscyclus van de diverse diensten verstrekt die door bundels worden blootgesteld. Een de dienstregister verstrekt een samenwerkingsmodel voor bundels dat levenscyclusdynamiek (en versievereisten) rekening houdt. OSGi lost veel van de problemen op die de toepassingsservers bedoeld waren om op te lossen, maar doet dit op een lichtgewicht, hoogst dynamische manier, die het mogelijk maken, bijvoorbeeld, de diensten op te warmen-opstellen (die de nieuwe code onmiddellijk beschikbaar maken zonder de server opnieuw te beginnen).

**Parsys, alineasysteem** - Het paragraafsysteem (parsys) is een samengestelde component die auteurs toestaat om componenten van verschillende types aan een pagina toe te voegen en andere paragraafcomponenten bevat. Elk alineatype wordt vertegenwoordigd als een component. Het alineasysteem zelf is ook een onderdeel dat de andere alineacomponenten bevat.

**Microkernel** - Elke werkruimte in de opslagplaats kan afzonderlijk worden geconfigureerd om de gegevens op te slaan via een specifieke microkernel (een klasse die het lezen en schrijven van de gegevens beheert). Op dezelfde manier kan de gegevensopslagruimte-brede versieopslag ook onafhankelijk worden gevormd om een bepaalde microkernel te gebruiken. Er zijn verschillende microkorrels beschikbaar waarmee gegevens in verschillende bestandsindelingen of relationele databases kunnen worden opgeslagen. (Er zijn bijvoorbeeld persistentiemanagers voor MongoDB, DB2® of Oracle) De standaardmicrokernel voor AEM is TarMK (zie verder hieronder).

**Instantie publiceren** - Voor beveiliging, bestuur en andere redenen deelt een productiesite instanties van AEM doorgaans op in instanties Auteur en Publiceren. Voor meer informatie over plaatsingsarchitectuur (met inbegrip van auteur/publiceer instanties), zie documentatie over AEM Instanties.

**QuickStart** - In tegenstelling tot veel andere programma&#39;s installeert u AEM met behulp van één zelfuitpakkend JAR-bestand met de naam QuickStart. Wanneer u voor het eerst op het JAR-bestand dubbelklikt, wordt alles wat u nodig hebt automatisch geïnstalleerd. De QuickStart JAR bevat alle bestanden die vereist zijn voor de CRX-opslagplaats (inclusief beheerfaciliteiten), virtuele opslagservices, index- en zoekservices, workflowservices, beveiliging en een webserver, plus de CQ Server Engine (CQSE) en alle AEM services. Er zijn geen andere bestanden om te installeren: de QuickStart is op zichzelf staand.

De eerste keer dat u de Quickstart start start, wordt op de achtergrond een volledige opslagplaats gemaakt die voldoet aan de JCR, wat enkele minuten kan duren. Na dit eerste opstarten zijn de volgende stappen veel sneller, aangezien de infrastructuur van de opslagplaats reeds is vastgelegd.

Vele opstartopties (zoals het actieve havenaantal en of de AEM instantie in kwestie een Publish instantie tegenover een instantie van de Auteur zou moeten zijn; en veel meer) kunnen worden gecontroleerd door het dossier van QuickStart correct anders te noemen. Als u een lijst met opties op dit gebied wilt weergeven, voert u de JAR met &quot;-help&quot; uit op de opdrachtregel:

```shell
java -jar <quickstartfilename>.jar -help
```

**Replication-agents** - De agenten van de replicatie zijn centraal om als mechanisme te AEM dat wordt gebruikt om inhoud van een auteur aan een publicatiemilieu te publiceren (te activeren); inhoud van het geheime voorgeheugen van de Verzender te spoelen; door de gebruiker geproduceerde inhoud (bijvoorbeeld, vorminput) van het Publish milieu aan het milieu van de Auteur terug te keren.

**Basisstructuur** - Met een basisstructuur kunt u een formulier (een basisblad) maken met velden die de gewenste structuur voor uw pagina&#39;s weerspiegelen. Met dit formulier kunt u eenvoudig pagina&#39;s maken op basis van deze structuur.

**Segmentering** - bezoekers van de site hebben verschillende belangen en doelstellingen wanneer ze naar een site komen. Kennis van de doelstellingen van bezoekers en het vervullen van hun verwachtingen is een belangrijke voorwaarde voor online marketing. Segmentering helpt dit te bereiken door de details van een bezoeker te analyseren en te karakteriseren.

**Sidekick** - De Sidekick is een paletachtig zwevend venster dat op de bewerkbare pagina wordt weergegeven, waaruit nieuwe componenten kunnen worden gesleept en acties die op de pagina van toepassing zijn, kunnen worden uitgevoerd.

**Site Catalyst** - SiteCatalyst biedt marketers één plaats om geïntegreerde gegevens van alle online initiatieven via meerdere marketingkanalen te meten, te analyseren en te optimaliseren. U kunt Adobe SiteCatalyst gebruiken om gegevens van AEM websites te analyseren.

**Tar Storage (TarMK)** - TarMK is het standaard persistentiesysteem in AEM. Hoewel AEM kan worden geconfigureerd om een ander persistentiesysteem te gebruiken (zoals MongoDB), heeft TarMK bepaalde voordelen omdat het prestatiegeoptimaliseerd is voor typische JCR-gebruiksscenario&#39;s (daarom snel), gebruikmaakt van een industriestandaard gegevensformaat en snel en eenvoudig back-ups kan maken.

**Sjabloon** - In AEM geeft een sjabloon een bepaald type pagina op. Hiermee wordt de structuur van een pagina gedefinieerd (waarbij doorgaans ook een miniatuurafbeelding en diverse eigenschappen worden opgegeven). U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens.

**Workflow** - Het AEM workflowsysteem maakt het mogelijk geautomatiseerde processen te maken waarbij pagina&#39;s of elementen worden gebruikt.
