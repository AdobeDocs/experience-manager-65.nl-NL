---
title: Richtlijnen voor hardwareaanpassing
seo-title: Richtlijnen voor hardwareaanpassing
description: Deze het rangschikken richtlijnen bieden een benadering van de hardwaremiddelen die worden vereist om een AEM project op te stellen.
seo-description: Deze het rangschikken richtlijnen bieden een benadering van de hardwaremiddelen die worden vereist om een AEM project op te stellen.
uuid: 395f9869-17c4-4b9b-99f8-d35a44dd6256
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 8893306f-4bc0-48eb-8448-36d0214caddf
docset: aem65
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae
workflow-type: tm+mt
source-wordcount: '2832'
ht-degree: 0%

---


# Richtlijnen voor hardwareaanpassing{#hardware-sizing-guidelines}

Deze het rangschikken richtlijnen bieden een benadering van de hardwaremiddelen die worden vereist om een AEM project op te stellen. Het rangschikken van ramingen hangt van de architectuur van het project, de ingewikkeldheid van de oplossing, het verwachte verkeer en de projectvereisten af. Deze gids helpt u om de hardwarebehoeften voor een specifieke oplossing te bepalen, of een hogere en lagere schatting voor de hardwarevereisten te vinden.

De belangrijkste factoren die in aanmerking moeten worden genomen zijn (in deze volgorde):

* **Netwerksnelheid**

   * Netwerkvertraging
   * Beschikbare bandbreedte

* **Rekensnelheid**

   * Efficiëntie in cache
   * Verwacht verkeer
   * Complexiteit van sjablonen, toepassingen en componenten
   * Gelijktijdige auteurs
   * Complexiteit van de ontwerpbewerking (eenvoudige bewerking van inhoud, MSM-uitrol, enz.)

* **I/O-prestaties**

   * Prestaties en efficiëntie van de bestands- of databaseopslag

* **Vaste schijf**

   * minstens twee of drie keer groter dan de grootte van de repository

* **Geheugen**

   * Grootte van website (aantal content-object, pagina&#39;s en gebruikers)
   * Aantal gebruikers/sessies dat tegelijkertijd actief is

## Architectuur {#architecture}

Een standaardinstelling voor AEM bestaat uit een auteur en een publicatieomgeving. Deze omgevingen hebben verschillende vereisten met betrekking tot de onderliggende hardwaregrootte en systeemconfiguratie. Gedetailleerde overwegingen voor beide omgevingen worden beschreven in de secties [auteursomgeving](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) en [publicatieomgeving](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations).

In een typisch projectopstelling, hebt u verscheidene milieu&#39;s waarop aan de fasen van het werkgebiedproject:

* **Ontwikkelomgeving**
Nieuwe functies ontwikkelen of belangrijke wijzigingen aanbrengen. De beste praktijken moeten werken gebruikend een ontwikkelomgeving per ontwikkelaar (gewoonlijk lokale installaties op hun persoonlijke systemen).

* **Testomgeving auteur**
om wijzigingen te controleren. Het aantal testomgevingen kan variëren afhankelijk van de projectvereisten (bijvoorbeeld, apart voor QA, integratietests of gebruikeracceptatietests).

* **Publiceer testomgevingPrimair voor het testen van gebruiksgevallen voor sociale samenwerking en/of de interactie tussen auteur en meerdere publicatieinstanties.**


* **Productomgeving auteur**
Voor auteurs om inhoud te bewerken.

* **Publiceer**
productieomgevingVoor gepubliceerde inhoud.

Bovendien kunnen de omgevingen variëren, variërend van een systeem met één server en een toepassingsserver tot een zeer geschaalde set van multi-server, multi-CPU geclusterde instanties. Wij adviseren dat u een afzonderlijke computer voor elk productiesysteem gebruikt en dat u geen andere toepassingen op deze computers in werking stelt.

## Algemene overwegingen voor hardwaregrootte {#generic-hardware-sizing-considerations}

In de volgende secties wordt uitgelegd hoe u de hardwarevereisten kunt berekenen, rekening houdend met verschillende overwegingen. Voor grote systemen stellen wij voor dat u een eenvoudige reeks interne benchmarktests op een verwijzingsconfiguratie uitvoert.

Optimalisering van prestaties is een fundamentele taak die moet worden uitgevoerd voordat benchmarking voor een specifiek project kan worden uitgevoerd. Pas het advies in de documentatie [Prestatieoptimalisatie](/help/sites-deploying/configuring-performance.md) toe voordat u benchmarktests uitvoert en de resultaten gebruikt voor berekeningen voor het aanpassen van de hardwaregrootte.

De vereisten voor het aanpassen van de hardwaregrootte voor gevallen van geavanceerd gebruik moeten gebaseerd zijn op een gedetailleerde prestatiebeoordeling van het project. Kenmerken van gevallen van geavanceerd gebruik waarvoor uitzonderlijke hardwarebronnen nodig zijn, zijn onder meer combinaties van:

* hoge inhoudslading / doorvoer
* uitgebreid gebruik van aangepaste code, aangepaste workflows of softwarebibliotheken van derden
* integratie met niet-ondersteunde externe systemen

### Schijfruimte/ Vaste schijf {#disk-space-hard-drive}

De vereiste schijfruimte hangt sterk af van zowel het volume als het type van uw webtoepassing. Bij de berekeningen moet rekening worden gehouden met:

* de hoeveelheid en grootte van pagina&#39;s, elementen en andere in de opslagplaats opgeslagen entiteiten zoals workflows, profielen, enz.
* de geschatte frequentie van inhoudwijzigingen en dus het maken van contentversies
* het volume van DAM-activa die worden gegenereerd
* de algemene groei van de inhoud in de loop der tijd

De schijfruimte wordt onophoudelijk gecontroleerd tijdens Online, en Off-line, de Opruiming van de Revisie. Als de beschikbare schijfruimte onder een kritieke waarde daalt, wordt het proces geannuleerd. De kritieke waarde is 25% van de huidige schijfvoetafdruk van de opslagplaats en kan niet worden geconfigureerd. Het wordt aanbevolen de schijf minstens twee of drie keer groter te maken dan de grootte van de opslagplaats, inclusief de geschatte groei.

Overweeg een installatie van redundante arrays van onafhankelijke schijven (RAID, bijvoorbeeld RAID10) voor gegevensredundantie.

>[!NOTE]
>
>De tijdelijke directory van een productie-instantie moet minstens 6 GB beschikbare ruimte hebben.

#### Virtualisatie {#virtualization}

AEM werkt goed in gevirtualiseerde omgevingen, maar er kunnen factoren zijn zoals CPU of I/O die niet rechtstreeks kunnen worden gelijkgesteld met fysieke hardware. Een aanbeveling is om een hogere I/O-snelheid (in het algemeen) te kiezen, aangezien dit in de meeste gevallen een cruciale factor is. Benchmarking van uw omgeving is nodig om precies te begrijpen welke bronnen nodig zijn.

#### Parallelisatie van AEM instanties {#parallelization-of-aem-instances}

**Misbruikszekerheid**

Een faalveilige website wordt opgesteld op minstens twee afzonderlijke systemen. Als één systeem afbreekt, kan een ander systeem overnemen en zo de systeemmislukking compenseren.

**Schaalbaarheid van systeembronnen**

Terwijl alle systemen actief zijn, zijn er betere computerprestaties beschikbaar. Die extra prestaties zijn niet noodzakelijkerwijs lineair met het aantal clusterknooppunten, aangezien de relatie sterk afhankelijk is van de technische omgeving; raadpleeg de [Clusterdocumentatie](/help/sites-deploying/recommended-deploys.md) voor meer informatie.

De schatting van het aantal clusterknooppunten dat nodig is, is gebaseerd op de basisvereisten en de specifieke gebruiksgevallen van het specifieke webproject:

* Vanuit het perspectief van misluk-veiligheid is het noodzakelijk om, voor alle milieu&#39;s te bepalen hoe kritieke mislukking en de tijd van de mislukkingscompensatie is gebaseerd op hoe lang het voor een clusterknoop vergt om terug te krijgen.
* Voor het aspect schaalbaarheid is het aantal schrijfbewerkingen in wezen de belangrijkste factor; zie [Auteurs die parallel werken](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel) voor de auteursomgeving en [Sociale Samenwerking](/help/managing/hardware-sizing-guidelines.md#socialcollaborationspecificconsiderations) voor het publicatiemilieu. Er kan een taakverdeling worden vastgesteld voor bewerkingen die alleen toegang hebben tot het systeem om leesbewerkingen te verwerken; zie [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) voor meer informatie.

## Omgevingsspecifieke berekeningen van auteur {#author-environment-specific-calculations}

Voor benchmarkingdoeleinden heeft Adobe enkele benchmarktests ontwikkeld voor op zichzelf staande auteur-instanties.

* **Benchmarktest 1**
Berekent de maximale doorvoer van een laadprofiel waarbij gebruikers een eenvoudige bewerking voor het maken van pagina&#39;s uitvoeren boven op een basisbelasting van 300 bestaande pagina&#39;s, allemaal van vergelijkbare aard. De betrokken stappen waren het aanmelden bij de site, het maken van een pagina met een SWF-bestand en een afbeelding/tekst, het toevoegen van een tagcloud en het vervolgens activeren van de pagina.

   * ****
ResultMaximum-doorvoer voor een eenvoudige oefening voor het maken van pagina&#39;s zoals hierboven (beschouwd als één transactie) bleek 1730 transacties/uur te zijn.

* **Benchmarktest 2**
Bereken de maximale doorvoer wanneer het laadprofiel bestaat uit een combinatie van het maken van een nieuwe pagina (10%), het wijzigen van een bestaande pagina (80%) en het maken van een opeenvolgende pagina (10%). De complexiteit van de pagina&#39;s blijft dezelfde als in het profiel van benchmarktest 1. De basiswijziging van de pagina wordt uitgevoerd door een afbeelding toe te voegen en de tekstinhoud te wijzigen. Ook hier werd de oefening uitgevoerd boven op een basislast van 300 pagina&#39;s met dezelfde complexiteit als in benchmarktest 1.

   * **De**
output ResultMaximum voor zulk een scenario van de mengelingsverrichting werd gevonden om 3252 transacties per uur te zijn.

>[!NOTE]
>
>De productiesnelheid maakt geen onderscheid tussen transactietypen binnen een laadprofiel. De benadering die wordt gebruikt om productie te meten zorgt ervoor dat een vast aandeel van elk type van transactie in de werklast wordt opgenomen.

Uit bovenstaande twee tests blijkt duidelijk dat de productie varieert naargelang het type activiteit. Gebruik de activiteiten in uw omgeving als basis voor het aanpassen van de grootte van uw systeem. U krijgt betere productie met minder intensieve acties zoals wijzigen (wat ook gemeenschappelijker is).

### {#caching}

In de auteursomgeving is de caching efficiency typisch veel lager, omdat de veranderingen in de website frequenter zijn en ook de inhoud hoogst interactief en gepersonaliseerd. Met behulp van de verzender kunt u AEM bibliotheken, JavaScripts, CSS-bestanden en lay-outafbeeldingen in cache plaatsen. Hierdoor worden sommige aspecten van het ontwerpproces versneld. Als u de webserver configureert om extra headers in te stellen voor het in cache plaatsen van de browser op deze bronnen, wordt het aantal HTTP-aanvragen verminderd en wordt de systeemresponsiviteit van de auteurs verbeterd.

### Auteurs die parallel {#authors-working-in-parallel} werken

In de auteursomgeving zijn het aantal auteurs die parallel werken en de lading hun interactie aan het systeem toevoegen de belangrijkste beperkende factoren. Daarom adviseren wij dat u uw systeem schrapt dat op de gedeelde productie van gegevens wordt gebaseerd.

Voor dergelijke scenario&#39;s voert Adobe benchmarktests uit op een twee knooppunten die geen cluster van auteursinstanties delen.

* **Benchmarktest 1**
aMet een actief-actief delen-niets cluster van 2 auteursinstanties, bereken de maximumproductie met een ladingsprofiel waar de gebruikers eenvoudig uitvoeren creeer paginamoeoefening bovenop een basislading van 300 bestaande pagina&#39;s, allen van gelijkaardige aard.

   * **De**
output ResultMaximum voor een eenvoudige oefening van de paginaverwezenlijking, zoals hierboven, (beschouwd als één transactie) wordt gevonden om 2016 transacties/uur te zijn. Dit is een stijging van ongeveer 16% in vergelijking met een standalone auteur instantie voor dezelfde benchmarktest.

* **Benchmarktest 2**
bMet een actief-actief delen-niets cluster van 2 auteurinstanties, bereken de maximumproductie wanneer het ladingsprofiel een mengeling van verse paginaconcreatie (10%), wijziging van een bestaande pagina (80%) en verwezenlijking en wijziging een pagina in opeenvolgende (10%) heeft. De complexiteit van de pagina blijft dezelfde als in het profiel van benchmarktest 1. De basiswijziging van de pagina wordt uitgevoerd door een afbeelding toe te voegen en de tekstinhoud te wijzigen. De oefening werd opnieuw uitgevoerd boven op een basislast van 300 pagina&#39;s van complexiteit, zoals gedefinieerd in benchmarktest 1.

   * **De**
output ResultMaximum voor zulk een gemengd verrichtingsscenario werd gevonden om 6288 transacties/uur te zijn. Dit is een stijging van ongeveer 93% in vergelijking met een standalone auteur instantie voor dezelfde benchmarktest.

>[!NOTE]
>
>De productiesnelheid maakt geen onderscheid tussen transactietypen binnen een laadprofiel. De benadering die wordt gebruikt om productie te meten zorgt ervoor dat een vast aandeel van elk type van transactie in de werklast wordt opgenomen.

Uit de bovenstaande twee tests blijkt duidelijk dat AEM schaalbaar is voor auteurs die elementaire bewerkingen met AEM uitvoeren. Over het algemeen is AEM het meest effectief bij het schalen van leesbewerkingen.

Op een typische website, gebeurt het meeste creatie tijdens de projectfase. Nadat de website live is gegaan, gooit het aantal auteurs die parallel werken doorgaans naar een lager (operationele modus) gemiddelde.

U kunt het aantal computers (of CPU&#39;s) dat vereist is voor de ontwerpomgeving als volgt berekenen:

`n = numberOfParallelAuthors / 30`

Deze formule kan als algemene richtlijn voor het schrapen van cpu&#39;s dienen wanneer de auteurs basishandelingen met AEM uitvoeren. Hierbij wordt ervan uitgegaan dat het systeem en de toepassing zijn geoptimaliseerd. De formule geldt echter niet voor geavanceerde functies zoals MSM of Elementen (zie de onderstaande secties).

Zie ook de aanvullende opmerkingen over [Parallelization](/help/managing/hardware-sizing-guidelines.md#parallelization-of-aem-instances) en [Prestaties optimaliseren](/help/sites-deploying/configuring-performance.md).

### Hardware-Recommendations {#hardware-recommendations}

Gewoonlijk kunt u voor uw auteursomgeving dezelfde hardware gebruiken als voor uw het publiceren milieu wordt geadviseerd. Websiteverkeer is doorgaans veel lager op ontwerpsystemen, maar de efficiëntie van de cache is ook lager. De fundamentele factor hierbij is echter het aantal auteurs dat parallel werkt, en het soort acties dat in het systeem wordt ondernomen. In het algemeen is AEM clustering (van de auteursomgeving) het meest effectief bij het schalen van leesbewerkingen; met andere woorden , een AEM cluster kan goed worden geschaald met auteurs die elementaire bewerkingen uitvoeren .

De benchmarktests bij Adobe zijn uitgevoerd met het RedHat 5.5-besturingssysteem, dat wordt uitgevoerd op een Hewlett-Packard ProLiant DL380 G5-hardwareplatform met de volgende configuratie:

* Twee Quad Core Intel Xeon X5450 CPU&#39;s met 3,00 GHz
* 8 GB RAM
* Broadcom NetXtreme II BCM5708 Gigabit Ethernet
* HP Smart Array RAID-controller, 256 MB cache
* Twee 146 GB SAS-schijven (10.000 rpm) geconfigureerd als een RAID0-stripe-set
* SPEC CINT2006 Rate benchmark score is 110

AEM instanties werden uitgevoerd met een minimale heapgrootte van 256M, een maximale heapgrootte van 1024M.

## Omgevingsspecifieke berekeningen {#publish-environment-specific-calculations} publiceren

### Efficiëntie en verkeer {#caching-efficiency-and-traffic} in cache plaatsen

Efficiëntie van de cache is van cruciaal belang voor de snelheid van de website. In de volgende tabel wordt aangegeven hoeveel pagina&#39;s per seconde een geoptimaliseerd AEM kan verwerken met een reverse-proxy, zoals de verzender:

| Cacheverhouding | Pagina&#39;s/s (piek) | Miljoen pagina&#39;s/dag (gemiddeld) |
|---|---|---|
| 100% | 1000 - 2000 | 35-70 |
| 99% | 910 | 32 |
| 95% | 690 | 25 |
| 90% | 520 | 18 |
| 60% | 220 | 8 |
| 0% | 100 | 3.5 |

>[!CAUTION]
>
>Disclaimer: De nummers zijn gebaseerd op een standaardhardwareconfiguratie en kunnen variëren afhankelijk van de gebruikte hardware.

De cacheratio is het percentage pagina&#39;s dat de verzender kan retourneren zonder toegang te hebben tot AEM. 100% geeft aan dat de verzender alle aanvragen beantwoordt, 0% betekent dat elke pagina AEM wordt berekend.

### Complexiteit van sjablonen en toepassingen {#complexity-of-templates-and-applications}

Als u complexe sjablonen gebruikt, heeft AEM meer tijd nodig om een pagina te renderen. Dit heeft geen invloed op pagina&#39;s die uit de cache zijn genomen, maar de paginagrootte is nog steeds relevant als u de totale responstijd in aanmerking neemt. Het weergeven van een complexe pagina kan eenvoudig tien keer langer duren dan het weergeven van een eenvoudige pagina.

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
   <td>Het verwachte piekverkeer per seconde. U kunt dit schatten als het aantal pagina-hits per dag gedeeld door 35.000.</td>
  </tr>
  <tr>
   <td>applicationComplexity</td>
   <td><p>Gebruik 1 voor een eenvoudige toepassing, 2 voor een complexe toepassing of een tussenliggende waarde:</p>
    <ul>
     <li>1 - een volledig anonieme, inhoudgeoriënteerde site</li>
     <li>1.1 - een volledig anonieme, inhoudgeoriënteerde site met klantgerichte/doelpersonalisatie</li>
     <li>1.5 - een op inhoud georiënteerde plaats met zowel anonieme als het programma geopende secties, cliënt-kant/de verpersoonlijking van het Doel</li>
     <li>1.7 - voor een content-oriented plaats met zowel anonieme als het programma geopende secties, cliënt-kant/Doel verpersoonlijking en wat gebruiker-geproduceerde inhoud</li>
     <li>2 - waar de hele site aanmelding vereist, met uitgebreid gebruik van door gebruikers gegenereerde inhoud en diverse personalisatietechnieken</li>
    </ul> </td>
  </tr>
  <tr>
   <td>cacheRatio</td>
   <td>Het percentage pagina's dat afkomstig is uit de verzendingscache. Gebruik 1 als alle pagina's uit het cachegeheugen komen of 0 als elke pagina door AEM wordt berekend.</td>
  </tr>
  <tr>
   <td>templateComplexiteit</td>
   <td>Gebruik een waarde tussen 1 en 10 om de complexiteit van uw sjablonen aan te geven. Hogere getallen duiden op complexere sjablonen, waarbij de waarde 1 wordt gebruikt voor sites met gemiddeld 10 componenten per pagina, de waarde 5 voor een gemiddelde paginaconcentratie van 40 componenten en 10 voor een gemiddelde van meer dan 100 componenten.</td>
  </tr>
  <tr>
   <td>activering</td>
   <td>Het aantal gemiddelde activeringen (replicatie van pagina's met gemiddelde grootte en middelen van de auteur naar de publicatielaag) per uur gedeeld door x, waarbij x het aantal activeringen is dat op een systeem zonder neveneffecten op de prestaties wordt uitgevoerd voor andere taken die door het systeem worden verwerkt. U kunt een pessimistische aanvankelijke waarde zoals x = 100 ook vooraf bepalen.<br /> </td>
  </tr>
 </tbody>
</table>

Als u een complexere website hebt, hebt u ook krachtigere webservers nodig, zodat AEM een verzoek binnen een aanvaardbare tijd kan beantwoorden.

* Complexiteit onder 4:
・ 1024 MB JVM RAM*
・ Lage tot middelkrachtige CPU

* Complexiteit tussen 4 en 8:
・ 2048 MB JVM RAM*
・ Midden tot krachtige CPU

* Complexiteit boven 8:
・ 4096 MB JVM RAM*
・ Krachtige tot krachtige CPU

>[!NOTE]
>
>* Reserve genoeg RAM voor uw werkend systeem naast het geheugen dat voor uw JVM wordt vereist.

## Aanvullende gebruiksspecifieke berekeningen {#additional-use-case-specific-calculations}

Naast de berekening voor een standaardwebtoepassing moet u wellicht rekening houden met specifieke factoren voor de volgende gebruiksgevallen. De berekende waarden worden toegevoegd aan de standaardberekening.

### Elementspecifieke overwegingen {#assets-specific-considerations}

Voor een uitgebreide verwerking van digitale elementen zijn geoptimaliseerde hardwarebronnen nodig. De belangrijkste factoren zijn de beeldgrootte en de maximale doorvoer van verwerkte afbeeldingen.

Wijs minstens 16 GB heap toe en configureer de [!UICONTROL DAM Update Asset]-workflow om het [Camera Raw pakket](/help/assets/camera-raw.md) te gebruiken voor de inname van Raw-afbeeldingen.

>[!NOTE]
Een hogere doorvoer van afbeeldingen betekent dat de computerbronnen gelijke tred moeten kunnen houden met de I/O van het systeem en omgekeerd. Als workflows bijvoorbeeld worden gestart door het importeren van afbeeldingen, kan het uploaden van veel afbeeldingen via WebDAV een achterstand in workflows veroorzaken.
Het gebruik van afzonderlijke schijven voor TarPM, gegevensopslag en zoekindex kan helpen om het I/O-gedrag van het systeem te optimaliseren (het is echter doorgaans verstandig om de zoekindex lokaal te houden).

>[!NOTE]
Zie ook de [Prestatiehandleiding voor bedrijfsmiddelen](/help/sites-deploying/assets-performance-sizing.md).

### Beheer van meerdere sites {#multi-site-manager}

Het hulpmiddelverbruik wanneer het gebruiken van AEM MSM op een auteursmilieu hangt sterk van de specifieke gebruiksgevallen af. Basisfactoren zijn:

* Aantal actieve kopieën
* Frequentie van rollouts
* De uit te rollen inhoudsboomgrootte
* Verbonden functionaliteit van de rollout-acties

Het testen van het geplande gebruiksgeval met een representatief inhoudsuittreksel kan u helpen uw begrip van het middelgebruik verbeteren. Als u de resultaten met de geplande productie extrapoleert, kunt u de extra middelen beoordelen die voor AEM MSM worden vereist.

Houd er ook rekening mee dat auteurs die parallel werken, nadelige gevolgen voor de prestaties zullen waarnemen als AEM MSM-gebruiksgevallen meer middelen verbruiken dan gepland.

### Overwegingen voor AEM Communities-formaat {#aem-communities-sizing-considerations}

AEM sites die AEM Communities-functies (communitysites) bevatten, ervaren veel interactie van sitebezoekers (leden) in de publicatieomgeving.

De rangschikkingsoverwegingen voor een communautaire plaats hangen van de verwachte interactie door communautaire leden af en of optimale prestaties voor paginacontent van hoger belang is.

Door de gebruiker gegenereerde inhoud (UGC) wordt apart van de pagina-inhoud opgeslagen. Terwijl het AEM platform een knoopopslag gebruikt die plaatsinhoud van auteur aan publicatie herhaalt, gebruikt AEM Communities één enkele, gemeenschappelijke opslag voor UGC die nooit wordt herhaald.

Voor de opslag UGC, is het noodzakelijk om een leverancier van het opslagmiddel (SRP) te kiezen, die de gekozen plaatsing beïnvloedt.
Zie

* [Opslag van communautaire inhoud](/help/communities/working-with-srp.md)
* [Aanbevolen topologieën voor Gemeenschappen](/help/communities/topologies.md)

