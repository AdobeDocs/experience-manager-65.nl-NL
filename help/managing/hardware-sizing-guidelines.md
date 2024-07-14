---
title: Richtlijnen voor hardwareaanpassing
description: Deze het rangschikken richtlijnen bieden een benadering van de hardwaremiddelen die worden vereist om een AEM project op te stellen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
docset: aem65
exl-id: 5837ef4f-d4e0-49d7-a671-87d5547e0d98
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '2830'
ht-degree: 0%

---

# Richtlijnen voor hardwareaanpassing{#hardware-sizing-guidelines}

Deze het rangschikken richtlijnen bieden een benadering van de hardwaremiddelen die worden vereist om een AEM project op te stellen. Het rangschikken van ramingen hangt van de architectuur van het project, de ingewikkeldheid van de oplossing, het verwachte verkeer, en de projectvereisten af. Deze gids helpt u om de hardwarebehoeften voor een specifieke oplossing te bepalen, of een hogere en lagere schatting voor de hardwarevereisten te vinden.

De volgende basisfactoren moeten in aanmerking worden genomen:

* **de snelheid van het Netwerk**

   * Netwerkvertraging
   * Beschikbare bandbreedte

* **Computationele snelheid**

   * Efficiëntie in cache
   * Verwacht verkeer
   * Complexiteit van sjablonen, toepassingen en componenten
   * Gelijktijdige auteurs
   * Complexiteit van de ontwerpbewerking (eenvoudige bewerking van inhoud, rollout van MSM enzovoort)

* **I/O prestaties**

   * Prestaties en efficiëntie van de bestands- of databaseopslag

* **Vaste Aandrijving**

   * minstens twee of drie keer groter dan de grootte van de repository

* **Geheugen**

   * Grootte van website (aantal content-object, pagina&#39;s en gebruikers)
   * Aantal gebruikers/sessies dat tegelijkertijd actief is

## Architectuur {#architecture}

Een standaardinstelling voor AEM bestaat uit een auteur en een publicatieomgeving. Deze omgevingen hebben verschillende vereisten met betrekking tot de onderliggende hardwaregrootte en systeemconfiguratie. De gedetailleerde overwegingen voor beide milieu&#39;s worden beschreven in het [ auteursmilieu ](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) en [ publiceren milieu ](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations) secties.

In een typisch projectopstelling, hebt u verscheidene milieu&#39;s waarop aan de fasen van het werkgebiedproject:

* **het milieu van de Ontwikkeling**
Nieuwe functies ontwikkelen of belangrijke wijzigingen aanbrengen. De beste praktijken moeten werken gebruikend een ontwikkelomgeving per ontwikkelaar (lokale installaties op hun persoonlijke systemen).

* **de testmilieu van de Auteur**
Wijzigingen verifiëren. Het aantal testomgevingen kan variëren afhankelijk van de projectvereisten (bijvoorbeeld, apart voor QA, integratietests of gebruikeracceptatietests).

* **de testmilieu van Publish**
Hoofdzakelijk voor het testen van gevallen waarin gebruik wordt gemaakt van sociale samenwerking en/of de interactie tussen auteur en meerdere publicatie-instanties.

* **het productiemilieu van de Auteur**
Voor auteurs om inhoud te bewerken.

* **Publish productiemilieu**
Gepubliceerde inhoud bedienen.

Bovendien kunnen de omgevingen variëren, variërend van een systeem met één server en een toepassingsserver tot een zeer geschaalde set van multi-server, multi-CPU geclusterde instanties. De Adobe adviseert dat u een afzonderlijke computer voor elk productiesysteem gebruikt en dat u geen andere toepassingen op deze computers in werking stelt.

## Algemene overwegingen voor hardwaregrootte {#generic-hardware-sizing-considerations}

In de volgende secties wordt uitgelegd hoe u de hardwarevereisten kunt berekenen, rekening houdend met verschillende overwegingen. Voor grote systemen, stelt de Adobe voor dat u een eenvoudige reeks interne benchmarktests op een verwijzingsconfiguratie uitvoert.

Optimalisering van prestaties is een fundamentele taak die moet worden uitgevoerd voordat benchmarking voor een specifiek project kan worden uitgevoerd. Zorg ervoor om het advies toe te passen dat in de [ documentatie van de Optimalisering van Prestaties ](/help/sites-deploying/configuring-performance.md) wordt verstrekt alvorens om het even welke benchmarktests uit te voeren en hun resultaten voor om het even welke hardware rangschikkende berekeningen te gebruiken.

De vereisten voor het aanpassen van de hardwaregrootte voor gevallen van geavanceerd gebruik moeten gebaseerd zijn op een gedetailleerde prestatiebeoordeling van het project. Kenmerken van gevallen van geavanceerd gebruik waarvoor uitzonderlijke hardwarebronnen nodig zijn, zijn onder meer combinaties van:

* hoge lading/doorvoer van inhoud
* uitgebreid gebruik van aangepaste code, aangepaste workflows of softwarebibliotheken van derden
* integratie met niet-ondersteunde externe systemen

### Schijfruimte/vaste schijf {#disk-space-hard-drive}

De vereiste schijfruimte hangt sterk af van zowel het volume als het type van uw webtoepassing. In de berekeningen moet rekening worden gehouden met het volgende:

* de hoeveelheid en grootte van pagina&#39;s, elementen en andere opslagplaatsen-opgeslagen entiteiten zoals werkschema&#39;s, profielen, etc.
* de geschatte frequentie van inhoudwijzigingen en dus het maken van contentversies
* het volume van DAM-activa die worden gegenereerd
* de algemene groei van de inhoud in de loop der tijd

De schijfruimte wordt onophoudelijk gecontroleerd tijdens Online, en Off-line, de Opruiming van de Revisie. Als de beschikbare schijfruimte onder een kritieke waarde daalt, wordt het proces geannuleerd. De kritieke waarde is 25% van de huidige schijfvoetafdruk van de opslagplaats en kan niet worden geconfigureerd. Adobe raadt aan de schijf ten minste twee of drie keer groter te maken dan de opslagplaats, inclusief de geschatte groei.

Overweeg een installatie van redundante arrays van onafhankelijke schijven (RAID, bijvoorbeeld RAID10) voor gegevensredundantie.

>[!NOTE]
>
>De tijdelijke directory van een productie-instantie moet minstens 6 GB beschikbare ruimte hebben.

#### Virtualisatie {#virtualization}

AEM werkt goed in gevirtualiseerde omgevingen, maar er kunnen factoren zijn zoals CPU of I/O die niet rechtstreeks kunnen worden gelijkgesteld met fysieke hardware. Een aanbeveling is om een hogere I/O-snelheid (in het algemeen) te kiezen, aangezien dit doorgaans een kritieke factor is. Benchmarking van uw omgeving is nodig om precies te begrijpen welke bronnen vereist zijn.

#### Parallelisatie van AEM instanties {#parallelization-of-aem-instances}

**de Veiligheid van het Kort**

Een faalveilige website wordt opgesteld op minstens twee afzonderlijke systemen. Als één systeem afbreekt, kan een ander systeem overnemen en zo de systeemmislukking compenseren.

**de middelen van het Systeem scalability**

Terwijl alle systemen actief zijn, zijn er betere computerprestaties beschikbaar. Die extra prestaties hoeven niet lineair te zijn met het aantal clusterknooppunten, aangezien de relatie sterk afhankelijk is van de technische omgeving. Zie [ documentatie van de Cluster ](/help/sites-deploying/recommended-deploys.md) voor meer informatie.

De schatting van het aantal clusterknooppunten dat nodig is, is gebaseerd op de basisvereisten en de specifieke gebruiksgevallen van het specifieke webproject:

* Vanuit het perspectief van mislukken-veiligheid, is het noodzakelijk om, voor alle milieu&#39;s te bepalen hoe kritieke mislukking en de tijd van de mislukkingscompensatie is gebaseerd op hoe lang het voor een clusterknoop vergt om terug te krijgen.
* Voor het aspect van scalability, is het aantal schrijven verrichtingen fundamenteel de belangrijkste factor; zie [ Auteurs die in Parallel ](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel) voor het auteursmilieu en [ Sociale Collaboration ](/help/managing/hardware-sizing-guidelines.md#socialcollaborationspecificconsiderations) voor het publicatiemilieu werken. Het in evenwicht brengen van de lading kan voor verrichtingen worden gevestigd die tot het systeem slechts toegang hebben om gelezen verrichtingen te verwerken; zie [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) voor details.

## Omgevingsspecifieke berekeningen van auteur {#author-environment-specific-calculations}

Voor benchmarkingdoeleinden heeft de Adobe enkele benchmarktests ontwikkeld voor op zichzelf staande auteur-instanties.

* **Benchmark test 1**
Bereken de maximale doorvoer van een laadprofiel waarbij gebruikers een eenvoudige bewerking voor het maken van een pagina uitvoeren boven op een basisbelasting van 300 bestaande pagina&#39;s die allemaal van gelijke aard zijn. De betrokken stappen waren het aanmelden bij de site, het maken van een pagina met een SWF en een afbeelding/tekst, het toevoegen van een tagcloud en het vervolgens activeren van de pagina.

   * **Resultaat**
De maximumproductie voor een eenvoudige oefening van de paginaareproductie zoals hierboven-beschouwd als één transactie-wordt gevonden om 1730 transacties/uur te zijn.

* **Benchmark test 2**
Bereken de maximale doorvoer wanneer het laadprofiel bestaat uit het maken van nieuwe pagina&#39;s (10%), het wijzigen van een bestaande pagina (80%) en het maken van een opeenvolgende pagina (10%). De complexiteit van de pagina&#39;s blijft dezelfde als in het profiel van benchmarktest 1. De basiswijziging van de pagina wordt uitgevoerd door een afbeelding toe te voegen en de tekstinhoud te wijzigen. Ook hier werd de oefening uitgevoerd boven op een basislast van 300 pagina&#39;s met dezelfde complexiteit als in benchmarktest 1.

   * **Resultaat**
De maximumproductie voor een dergelijk scenario van de mengselverrichting werd gevonden om 3252 transacties per uur te zijn.

>[!NOTE]
>
>De productiesnelheid maakt geen onderscheid tussen transactietypen binnen een laadprofiel. De benadering die wordt gebruikt om productie te meten zorgt ervoor dat een vast aandeel van elk type van transactie in de werklast wordt opgenomen.

Uit bovenstaande twee tests blijkt duidelijk dat de productie varieert naargelang het type activiteit. Gebruik de activiteiten in uw omgeving als basis voor het aanpassen van de grootte van uw systeem. U krijgt betere productie met minder intensieve acties zoals wijzigen (wat ook gemeenschappelijker is).

### Caching {#caching}

In de auteursomgeving is de caching efficiency typisch veel lager, omdat de veranderingen in de website frequenter zijn en ook de inhoud hoogst interactief en gepersonaliseerd is. Met de Dispatcher kunt u AEM bibliotheken, JavaScript, CSS-bestanden en lay-outafbeeldingen in cache plaatsen. Hierdoor worden sommige aspecten van het ontwerpproces versneld. Wanneer u de webserver configureert om ook headers in te stellen voor het in cache plaatsen van de browser op deze bronnen, wordt het aantal HTTP-aanvragen verminderd en wordt de systeemresponsiviteit verbeterd zoals de auteurs ervaren.

### Auteurs die parallel werken {#authors-working-in-parallel}

In de auteursomgeving zijn het aantal auteurs die parallel werken en de lading hun interactie aan het systeem toevoegen de belangrijkste beperkende factoren. Daarom adviseert de Adobe dat u uw systeem schrapt dat op de gedeelde productie van gegevens wordt gebaseerd.

Voor dergelijke scenario&#39;s, stelde de Adobe benchmarktests op een twee knoop gedeeld-niets cluster van auteursinstanties in werking.

* **Benchmark test 1a**
Met een actief-actief delen-niets cluster van 2 auteursinstanties, bereken de maximumproductie met een ladingsprofiel waar de gebruikers eenvoudig uitvoeren creeer paginamotie bovenop een basislading van 300 bestaande pagina&#39;s, allen van gelijkaardige aard.

   * **Resultaat**
De maximumproductie voor een eenvoudige oefening van de paginaaremaak, zoals hierboven-beschouwd als één transactie-wordt gevonden om 2016 transacties/uur te zijn. Dit is een stijging van ongeveer 16% in vergelijking met een standalone auteur instantie voor dezelfde benchmarktest.

* **Benchmark test 2b**
Met een actief-actief delen-niets cluster van 2 auteursinstanties, bereken de maximumproductie wanneer het ladingsprofiel een mengeling van verse paginverwezenlijking (10%), wijziging van een bestaande pagina (80%) en verwezenlijking en wijziging van een pagina in opeenvolgende (10%) heeft. De complexiteit van de pagina blijft dezelfde als in het profiel van benchmarktest 1. De basiswijziging van de pagina wordt uitgevoerd door een afbeelding toe te voegen en de tekstinhoud te wijzigen. De oefening werd opnieuw uitgevoerd boven op een basislast van 300 pagina&#39;s van complexiteit, zoals gedefinieerd in benchmarktest 1.

   * **Resultaat**
De maximale doorvoer voor een dergelijk scenario met gemengde transacties bleek 6288 transacties per uur te zijn. Dit is een stijging van ongeveer 93% in vergelijking met een standalone auteur instantie voor dezelfde benchmarktest.

>[!NOTE]
>
>De productiesnelheid maakt geen onderscheid tussen transactietypen binnen een laadprofiel. De benadering die wordt gebruikt om productie te meten zorgt ervoor dat een vast aandeel van elk type van transactie in de werklast wordt opgenomen.

Uit de bovenstaande twee tests blijkt duidelijk dat AEM schaalbaar is voor auteurs die elementaire bewerkingen met AEM uitvoeren. Over het algemeen is AEM het meest effectief bij het schalen van leesbewerkingen.

Op een typische website, gebeurt het meeste creatie tijdens de projectfase. Nadat de website live is gegaan, gooit het aantal auteurs die parallel werken doorgaans naar een lager (operationele modus) gemiddelde.

U kunt het aantal computers (of CPU&#39;s) dat vereist is voor de ontwerpomgeving als volgt berekenen:

`n = numberOfParallelAuthors / 30`

Deze formule kan als algemene richtlijn voor het schrapen van cpu&#39;s dienen wanneer de auteurs basishandelingen met AEM uitvoeren. Hierbij wordt ervan uitgegaan dat het systeem en de toepassing zijn geoptimaliseerd. De formule is echter niet geldig voor geavanceerde functies zoals MSM of Assets (zie de onderstaande secties).

Zie ook [ Parallelization ](/help/managing/hardware-sizing-guidelines.md#parallelization-of-aem-instances) en [ Optimalisering van Prestaties ](/help/sites-deploying/configuring-performance.md).

### Hardware Recommendations {#hardware-recommendations}

Gewoonlijk kunt u voor uw auteursomgeving dezelfde hardware gebruiken als voor uw het publiceren milieu wordt geadviseerd. Websiteverkeer is doorgaans lager bij ontwerpsystemen, maar de efficiëntie van de cache is lager. De fundamentele factor hierbij is echter het aantal auteurs dat parallel werkt, en het soort acties dat in het systeem wordt ondernomen. Over het algemeen is AEM clustering (van de auteursomgeving) het meest effectief bij het schalen van leesbewerkingen; met andere woorden, een AEM cluster schaalt goed met auteurs die elementaire bewerkingsbewerkingen uitvoeren.

De benchmarktests bij Adobe werden uitgevoerd met het Red Hat® 5.5-besturingssysteem, dat werd uitgevoerd op een Hewlett-Packard ProLiant DL380 G5-hardwareplatform met de volgende configuratie:

* Twee Quad Core Intel Xeon® X5450 CPU&#39;s met 3,00 GHz
* 8 GB RAM
* Broadcom NetXtreme II BCM5708 Gigabit Ethernet
* HP Smart Array RAID-controller, 256 MB cache
* Twee 146 GB SAS-schijven (10.000 rpm), geconfigureerd als een RAID0-stripe-set
* SPEC CINT2006 Rate benchmark score is 110

AEM instanties werden uitgevoerd met een minimale heapgrootte van 256M, een maximale heapgrootte van 1024M.

## Publish-milieuspecifieke berekeningen {#publish-environment-specific-calculations}

### Efficiëntie en verkeer in cache {#caching-efficiency-and-traffic}

Efficiëntie van de cache is van cruciaal belang voor de snelheid van de website. In de volgende tabel wordt aangegeven hoeveel pagina&#39;s per seconde een geoptimaliseerd AEM kan verwerken met een reverse-proxy, zoals de Dispatcher:

| Cacheverhouding | Pagina&#39;s/s (piek) | Miljoen pagina&#39;s/dag (gemiddeld) |
|---|---|---|
| 100% | 1000 - 2000 | 35-70 |
| 99% | 910 | 32 |
| 95% | 690 | 25 |
| 90% | 520 | 18 |
| 60% | 220 | 8 |
| 0% | 100 | 3,5 |

>[!CAUTION]
>
>Disclaimer: de getallen zijn gebaseerd op een standaardhardwareconfiguratie en kunnen variëren afhankelijk van de specifieke gebruikte hardware.

De cacheratio is het percentage pagina&#39;s dat de Dispatcher kan retourneren zonder toegang te hebben tot AEM. 100% geeft aan dat de Dispatcher alle verzoeken beantwoordt, 0% betekent dat AEM elke pagina berekent.

### Complexiteit van sjablonen en toepassingen {#complexity-of-templates-and-applications}

Als u complexe sjablonen gebruikt, AEM meer tijd nodig om een pagina te renderen. Dit heeft geen invloed op pagina&#39;s die uit de cache zijn genomen, maar de paginagrootte is nog steeds relevant als u de totale responstijd in aanmerking neemt. Het weergeven van een complexe pagina kan eenvoudig tien keer langer duren dan het weergeven van een eenvoudige pagina.

### Formule {#formula}

Met de volgende formule kunt u een schatting berekenen van de totale complexiteit van uw AEM oplossing:

`complexity = applicationComplexity + ((1-cacheRatio) * templateComplexity)`

Op basis van de complexiteit kunt u als volgt bepalen hoeveel servers (of CPU-cores) u nodig hebt voor de publicatieomgeving:

`n = (traffic * complexity / 1000 ) * activations`

De variabelen in de vergelijking zijn als volgt:

<table>
 <tbody>
  <tr>
   <td>verkeer</td>
   <td>Het verwachte piekverkeer per seconde. U kunt dit schatten als het aantal pagina-hits per dag gedeeld door 35'000.</td>
  </tr>
  <tr>
   <td>applicationComplexity</td>
   <td><p>Gebruik 1 voor een eenvoudige toepassing, 2 voor een complexe toepassing of een tussenliggende waarde:</p>
    <ul>
     <li>1 - een volledig anonieme, inhoudgeoriënteerde site</li>
     <li>1.1 - een volledig anonieme, inhoudgeoriënteerde site met klantgerichte/doelpersonalisatie</li>
     <li>1.5 - een op inhoud georiënteerde plaats met zowel anonieme als het programma geopende secties, cliënt-kant/het personalisatie van het Doel</li>
     <li>1.7 - voor een content-oriented plaats met zowel anonieme als het programma geopende secties, cliënt-kant/Doel verpersoonlijking en wat gebruiker-geproduceerde inhoud</li>
     <li>2 - waar voor de gehele site aanmeldingsgegevens nodig zijn, met intensief gebruik van door de gebruiker gegenereerde inhoud en verschillende personalisatietechnieken</li>
    </ul> </td>
  </tr>
  <tr>
   <td>cacheRatio</td>
   <td>Het percentage pagina's dat afkomstig is uit de Dispatcher-cache. Gebruik 1 als alle pagina's uit het cachegeheugen komen, of 0 als elke pagina door AEM wordt berekend.</td>
  </tr>
  <tr>
   <td>templateComplexiteit</td>
   <td>Gebruik een waarde tussen 1 en 10 om de complexiteit van je templates aan te geven. Hogere getallen duiden op complexere sjablonen, waarbij de waarde 1 wordt gebruikt voor sites met gemiddeld 10 componenten per pagina, de waarde 5 voor een gemiddelde paginaconcentratie van 40 componenten en 10 voor een gemiddelde van meer dan 100 componenten.</td>
  </tr>
  <tr>
   <td>activering</td>
   <td>Het aantal gemiddelde activeringen (replicatie van pagina's met gemiddelde grootte en middelen van de auteur naar de publicatielaag) per uur gedeeld door x, waarbij x het aantal activeringen is dat op een systeem zonder neveneffecten op de prestaties wordt uitgevoerd voor andere taken die door het systeem worden verwerkt. U kunt een pessimistische aanvankelijke waarde zoals x ook vooraf bepalen = 100.<br /> </td>
  </tr>
 </tbody>
</table>

Als u een complexere website hebt, hebt u ook krachtigere webservers nodig, zodat AEM een verzoek binnen een aanvaardbare tijd kan beantwoorden.

* Complexiteit onder 4:
   * 1024 MB JVM RAM &#42;
   * Low to mid-performance CPU

* Complexiteit tussen 4 en 8:
   * 2048 MB JVM RAM &#42;
   * Midden tot krachtige CPU

* Complexiteit boven 8:
   * 4096 MB JVM RAM &#42;
   * Krachtige CPU

>[!NOTE]
>
>&#42; Reserve genoeg RAM voor uw werkend systeem naast het geheugen dat voor uw JVM wordt vereist.

## Aanvullende gebruiksspecifieke berekeningen {#additional-use-case-specific-calculations}

Naast de berekening voor een standaardwebtoepassing, moet u rekening houden met specifieke factoren voor de volgende gebruiksgevallen. De berekende waarden moeten aan de standaardberekening worden toegevoegd.

### Assets-specifieke overwegingen {#assets-specific-considerations}

Voor een uitgebreide verwerking van digitale elementen zijn geoptimaliseerde hardwarebronnen nodig. De belangrijkste factoren zijn de beeldgrootte en de maximale doorvoer van verwerkte afbeeldingen.

Wijs minstens 16GB van hoop toe en vorm het [!UICONTROL DAM Update Asset] werkschema om het [ Camera Raw pakket ](/help/assets/camera-raw.md) voor het opnemen van ruwe beelden te gebruiken.

>[!NOTE]
>
Een hogere doorvoer van afbeeldingen betekent dat de computerbronnen gelijke tred moeten kunnen houden met de I/O van het systeem en omgekeerd. Als workflows bijvoorbeeld worden gestart door het importeren van afbeeldingen, kan het uploaden van veel afbeeldingen via WebDAV een achterstand in workflows veroorzaken.
>
Het gebruik van afzonderlijke schijven voor TarPM, gegevensopslag en zoekindex kan helpen het I/O-gedrag van het systeem te optimaliseren (het is echter doorgaans verstandig om de zoekindex lokaal te houden).

>[!NOTE]
>
Zie ook de [ Gids van de Prestaties van Assets ](/help/sites-deploying/assets-performance-sizing.md).

### Beheer van meerdere sites {#multi-site-manager}

Het hulpmiddelverbruik wanneer het gebruiken van AEM MSM op een auteursmilieu hangt sterk van de specifieke gebruiksgevallen af. Basisfactoren zijn:

* Aantal actieve kopieën
* Frequentie van rollouts
* De uit te rollen inhoudsboomgrootte
* Verbonden functionaliteit van de rollout-acties

Het testen van het geplande gebruiksgeval met een representatief inhoudsuittreksel kan u helpen uw begrip van het middelgebruik verbeteren. Als u de resultaten met de geplande productie extrapoleert, kunt u de extra middelen beoordelen die voor AEM MSM worden vereist.

Zorg ook voor auteurs die parallel werken. Zij zullen prestaties bijwerkingen gevolgen waarnemen als AEM MSM gebruiksgevallen meer middelen dan gepland verbruiken.

### Overwegingen voor AEM Communities-formaat {#aem-communities-sizing-considerations}

AEM sites die AEM Communities-functies (communitysites) bevatten, ervaren veel interactie van sitebezoekers (leden) in de publicatieomgeving.

De rangschikkingsoverwegingen voor een communautaire plaats hangen van de verwachte interactie door communautaire leden af en of optimale prestaties voor paginacontent van hoger belang is.

Door de gebruiker gegenereerde inhoud (UGC) wordt apart van de pagina-inhoud opgeslagen. Terwijl het AEM platform een knoopopslag gebruikt die plaatsinhoud van auteur aan publicatie herhaalt, gebruikt AEM Communities één enkele, gemeenschappelijke opslag voor UGC die nooit wordt herhaald.

Voor de opslag UGC, is het noodzakelijk om een leverancier van het opslagmiddel (SRP) te kiezen, die de gekozen plaatsing beïnvloedt.
Zie

* [Opslag van communautaire inhoud](/help/communities/working-with-srp.md)
* [Aanbevolen topologieën voor Gemeenschappen](/help/communities/topologies.md)
