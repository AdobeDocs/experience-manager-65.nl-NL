---
title: Hoe te om een AEM Forms op de servercluster van JEE te vormen en problemen op te lossen?
description: Leer hoe u een AEM Forms in een JEE-servercluster configureert en problemen oplost
exl-id: 230fc2f1-e6e5-4622-9950-dae9449ed3f6
source-git-commit: 1cdd15800548362ccdd9e70847d9df8ce93ee06e
workflow-type: tm+mt
source-wordcount: '4033'
ht-degree: 0%

---

# AEM Forms configureren en problemen oplossen in een JEE-servercluster {#configuring-troubleshooting-aem-forms-jee-server-cluster}

## Vereiste kennis {#prerequisites}

Kennis van AEM Forms op JEE-, JBoss-, WebSphere- en Webogic-toepassingsservers, Red Hat Linux, SUSE Linux, Microsoft Windows, IBM AIX of Sun Solaris-besturingssystemen, Oracle, IBM DB2 of SQL Server-databaseservers en webomgevingen.

## Gebruikersniveau {#user-level}

Geavanceerd

Een AEM Forms op de Cluster JEE is een topologie die wordt ontworpen om AEM Forms op JEE toe te laten veerkrachtig aan de mislukking van een clusterknoop zijn en systeemcapaciteit voorbij de mogelijkheden van één enkele knoop te schrapen. Een cluster combineert meerdere knooppunten tot één logisch systeem dat gegevens deelt en transacties toestaat om meerdere knooppunten in de uitvoering te omspannen. Een cluster is de meest algemene manier om AEM Forms op JEE te schalen, in die zin dat elke combinatie van services die elke combinatie van werklasten afhandelen, kan worden ondersteund. Een AEM Forms on JEE-cluster is niet noodzakelijkerwijs het beste geschikt voor alle typen implementaties, en in het bijzonder kan een niet-geclusterde serverarchitectuur met taakverdeling in veel gevallen geschikt zijn.

Het doel van dit document is om de specifieke configuratievereisten en potentiële probleemgebieden te bespreken u met AEM Forms op cluster JEE kunt ontmoeten.

## Wat zit er in een cluster? {#what-is-in-cluster}

De AEM Forms op JEE clusterknopen communiceren onder elkaar en delen informatie om de cluster als geheel toe te laten om één enkele verenigbare configuratie en toepassingsstaat te hebben. Het delen van informatie binnen de cluster gebeurt op verschillende manieren gelijktijdig die in verschillende contexten worden gebruikt. De basismethoden voor het delen van informatie worden in onderstaande afbeelding weergegeven:

![Toepassingsservercluster](assets/application-server-cluster.jpg)

### Toepassingsservercluster {#application-server-cluster}

Een AEM Forms op JEE-cluster is afhankelijk van de clusteringsmogelijkheden van de onderliggende toepassingsserver. De serverclusters van de toepassing laten de clusterconfiguratie toe om als geheel worden beheerd en verlenen de laag-vlakke clusterdiensten zoals het Noemen van Java en de Interface van de Folder (JNDI) die softwarecomponenten toelaten om elkaar binnen de cluster te vinden. De verfijning van clusterdiensten en de onderliggende technische gebiedsdelen de toepassingsserver is afhankelijk van de toepassingsserver. WebSphere en WebLogic beschikken over geavanceerde beheermogelijkheden voor clusters, terwijl JBoss een zeer basisbenadering heeft.

### GemFire-cache {#gemfire-cache}

De GemFire-cache is een verspreid cachemechanisme dat in elk clusterknooppunt wordt geïmplementeerd. De knopen vinden elkaar en bouwen één enkel logisch geheime voorgeheugen dat tussen de knopen coherent wordt gehouden. De knopen die elkaar vinden sluiten zich samen om één enkel notioneel geheime voorgeheugen te handhaven dat als wolk in Figuur 1 wordt getoond. In tegenstelling tot de GDS en de database, is de cache een louter fictieve entiteit. De werkelijke inhoud in de cache wordt opgeslagen in het geheugen en in de map `LC_TEMP` op elk van de clusterknooppunten.

### Database {#database}

De AEM Forms on JEE-database (die wordt geopend via de JDBC-gegevensbronnen IDP_DS, EDC_DS en anderen) wordt gedeeld door alle knooppunten van de cluster. De meeste permanente gegevens over de toestand van AEM Forms op JEE, zoals welke transacties worden uitgevoerd, de gebruikersgegevens die aan lopende transacties zijn gekoppeld, gegevens over hoe de systeeminstellingen zijn ingesteld, enzovoort, bevinden zich in deze database.

### Opslag van algemene documenten {#global-document-storage}

De GDS (Global Document Storage) is een opslaggebied op basis van een bestandssysteem dat wordt gebruikt door Document Manager (klasse IDPDocument) in AEM Forms op JEE. In de GDS worden kortstondige en langlevende bestanden opgeslagen die toegankelijk moeten zijn voor alle knooppunten van de cluster.

### Overige items {#other-items}

Naast deze hoofdgedeelde bronnen zijn er andere items die een specifiek clustergedrag hebben, zoals Kwartz. Kwartz is een plannersubsysteem dat door AEM Forms op JEE wordt gebruikt, en het gebruikt gegevensbestandlijsten om zijn kennis van te houden wat is gepland en welke geplande activiteiten lopen. Kwartz moet voor installaties en clusters met één knooppunt anders worden geconfigureerd, en het gebruikt zijn activering van andere AEM Forms voor JEE-instellingen.

## Algemene configuratieproblemen {#common-configuration}

Een van de meest frustrerende dingen over het onderhouden of oplossen van problemen van een AEM Forms op cluster JEE is dat er geen enkele plaats is om positief te kijken om te bevestigen dat de cluster gezond is. Om te bevestigen dat alles goed in de cluster is neemt wat onderzoek en analyse, en er zijn verscheidene wijzen van mislukking voor clusterverrichting, afhankelijk van wat met de clusterconfiguratie verkeerd is. Het cijfer toont hieronder een slecht gevormde cluster waarin verscheidene gedeelde middelen incorrect worden gedeeld.

![Onjuist geconfigureerde cluster](assets/bad-configuration-cluster.png)

Interessant en belangrijk om in mening te houden is dat u met de manier vertrouwd moet zijn die het groeperen werkt en de soorten dingen om in een cluster te zoeken en te verifiëren, zelfs als u niet van plan bent om AEM Forms op JEE in een cluster in werking te stellen. Dit komt omdat sommige delen van AEM Forms op JEE hun aanwijzingen over het onjuist werken in een cluster kunnen nemen en het clustergedrag dat u niet verwacht, kunnen overnemen.

Zo wat met de het delen configuratie van hierboven Cijfer verkeerd is? In de volgende secties worden de problemen beschreven:

### (1) GemFire-clusterconfiguratie {#gemfire-cluster-configuration}

Verschillende dingen kunnen fout gaan met de &#39;Gemfire cache&#39;. Twee typische scenario&#39;s zijn:

* Nodes die elkaar zouden moeten kunnen vinden, kunnen dat niet.

* De knopen die niet worden verondersteld om worden gegroepeerd vinden elkaar en delen een geheim voorgeheugen wanneer zij niet zouden moeten.

Als u knopen hebt die u van plan bent te groeperen, is het essentieel dat zij elkaar op het netwerk vinden. Standaard doen ze dit door middel van multicast UDP-berichten. Elke knoop verzendt uitzendingsberichten reclame die het aanwezig is, en om het even welke knoop die zulk een bericht ontvangt begint met de andere knopen te spreken die het vindt. Dit soort methode van autodetectie is heel gebruikelijk, en veel soorten software en apparaten doen dit.

Één gemeenschappelijk probleem met autodiscovery is dat multicast berichten door het netwerk als deel van netwerkbeleid of wegens de regels van de softwarefirewall kunnen worden gefiltreerd, of eenvoudig niet over het netwerk kunnen leiden dat tussen knopen bestaat. Wegens de algemene moeilijkheid met het krijgen van autodiscovery UDP om in complexe netwerken te werken, is het gemeenschappelijke praktijk voor productielokaties om een alternatieve ontdekkingsmethode te gebruiken: TCP locators. Een algemene bespreking van de plaatsbepalers van TCP kan in de verwijzingen worden gevonden.

**Hoe weet ik of ik locators of UDP gebruik?**

De volgende JVM-eigenschappen bepalen de methode die de GemFire-cache gebruikt om andere knooppunten te zoeken.

Multicast-instellingen:

* `adobe.cache.multicast-port`: De multicast haven die wordt gebruikt om met andere leden van het verdeelde systeem te communiceren. Als deze aan nul wordt geplaatst, multicast is gehandicapt voor zowel lidontdekking als distributie.

* `gemfire.mcast-address` (optioneel): Overschrijft het standaard IP adres dat door Gemfire wordt gebruikt.

TCP Locator-instellingen:

* `adobe.cache.cluster-locators`: Het IP adres/de gastheernaam van de plaatsbepaler van TCP en de plaatsbepalerhaven van TCP voor alle plaatsbepalers die door systeemleden worden gebruikt om met lopende merktekens te communiceren.

De lijst moet alle locators omvatten die momenteel in gebruik zijn, en moet voor elk lid van het clustersysteem consequent worden gevormd.

Als de lijst van het Merkteken van TCP leeg is, worden de scènes niet gebruikt en in plaats daarvan wordt de multicast methode gebruikt.

**Hoe kan ik controleren als mijn plaatsbepaler van TCP loopt?**

Ten eerste, als de plaatsbepalers van TCP in gebruik zijn, zou u uw plaatsbepalers moeten hebben van TCP die in het volgende bezit JVM op alle clusterknopen worden vermeld:

`-Dadobe.cache.cluster-locators=aix01.adobe.com[22345],aix02.adobe.com[22345]`

Het is niet nodig om de locators op de AEM Forms op JEE clusterknopen in werking te stellen-zij kunnen op andere systemen afzonderlijk van de cluster, indien gewenst worden in werking gesteld. Meer dan één systeem kan locators in werking stellen, en het wordt over het algemeen beschouwd beste praktijken om locators te hebben die in twee plaatsen tegen de mogelijkheid lopen dat één enkele mislukking van de scènes een probleem met clusterherstart zou kunnen veroorzaken. Op elk systeem dat locators in werking stelt, zou u moeten kunnen verifiëren dat zij gebruikend de volgende bevelen op die machines lopen:

`netstat -an | grep 22345`

De verwachte reactie zou als volgt moeten zijn:

`tcp 0 0 *.22345 *.* LISTEN`

Een andere verificatieopdracht is deze:

`ps -ef | grep gemfire`

De verwachte reactie moet er ongeveer als volgt uitzien:

`livecycl 331984 1 0 10:14:51 pts/0 0:03 java -cp ./gemfire.jar: -Dgemfire.license-type=production -Dlocators=localhost[22345] com.gemstone.gemfire.distributed.Locator 22345`

**Hoe zie ik welke knopen GemFire in de cluster denkt te zijn?**

GemFire produceert logboekinformatie die kan worden gebruikt om te bepalen welke clusterleden door het geheime voorgeheugen van GemFire zijn gevonden en worden goedgekeurd. Dit kan worden gebruikt om te verifiëren dat alle correcte clusterleden worden gevonden en dat geen extra of onjuiste ontdekking van de clusterknoop gebeurt. Het logbestand voor GemFire bevindt zich in de geconfigureerde AEM Forms in de tijdelijke map JEE:

`.../LC_TEMP/adobeZZ__123456/Caching/Gemfire.log`

De numerieke tekenreeks na `adobeZZ_` is uniek voor het serverknooppunt. U moet daarom zoeken in de feitelijke inhoud van de tijdelijke map. De twee tekens na `adobe` zijn afhankelijk van het servertype van de toepassing: hetzij `wl`, `jb`, of `ws`.

De volgende steekproeflogboeken tonen wat gebeurt wanneer een twee-knoopcluster zich vindt.

Voor de eerste knoop, AP-HP8:

```xml
[config 2011/08/05 09:28:09.143 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] This member, ap-hp8(4268):18763, is becoming group coordinator.
[info 2011/08/05 09:28:09.151 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Entered into membership in group GF6.5.1.17 with ID ap-hp8(4268)<v0>:18763/56449.
[info 2011/08/05 09:28:09.152 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Starting DistributionManager ap-hp8(4268)<v0>:18763/56449.
[info 2011/08/05 09:28:09.153 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Initial (membershipManager) view =  [ap-hp8(4268)<v0>:18763/56449]
[info 2011/08/05 09:28:09.153 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Admitting member <ap-hp8(4268)<v0>:18763/56449>. Now there are 1 non-admin member(s).
[info 2011/08/05 09:28:09.154 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] ap-hp8(4268)<v0>:18763/56449 is the elder and the only member.
[info 2011/08/05 09:28:09.163 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Did not hear back from any other system. I am the first one.
[info 2011/08/05 09:28:09.164 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] DistributionManager ap-hp8(4268)<v0>:18763/56449 started on 239.192.81.1[33456]. There were 0 other DMs. others: []
[info 2011/08/05 09:28:20.841 EDT GemfireCacheAdapter <Pooled Message Processor 1> tid=0xc4] New administration member detected at ap-hp7(2821)<v1>:19498/59136.
```

Op de andere knoop, AP-HP7:

```xml
[info 2011/08/05 09:28:09.830 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Attempting to join distributed system whose membership coordinator is ap-hp8(4268)<v0>:18763 using membership ID ap-hp7(2821):19498
[info 2011/08/05 09:28:10.058 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Entered into membership in group GF6.5.1.17 with ID ap-hp7(2821)<v1>:19498/59136.
[info 2011/08/05 09:28:10.059 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Starting DistributionManager ap-hp7(2821)<v1>:19498/59136.
[info 2011/08/05 09:28:10.060 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Initial (membershipManager) view =  [ap-hp8(4268)<v0>:18763/56449, ap-hp7(2821)<v1>:19498/59136]
[info 2011/08/05 09:28:10.060 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Admitting member <ap-hp8(4268)<v0>:18763/56449>. Now there are 1 non-admin member(s).
[info 2011/08/05 09:28:10.060 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Admitting member <ap-hp7(2821)<v1>:19498/59136>. Now there are 2 non-admin member(s).
[info 2011/08/05 09:28:10.128 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] DistributionManager ap-hp7(2821)<v1>:19498/59136 started on 239.192.81.1[33456]. There were 1 other DMs. others: [ap-hp8(4268)<v0>:18763/56449]
```

**Wat als GemFire knooppunten vindt die het niet zou moeten?**

Elke afzonderlijke cluster die een collectief netwerk deelt zou een afzonderlijke reeks plaatsbepalers van TCP moeten gebruiken, als de plaatsbepalers van TCP worden gebruikt, of een afzonderlijk UDP havenaantal als de multicastconfiguratie UDP wordt gebruikt. Aangezien UDP autodiscovery de standaardconfiguratie voor AEM Forms op JEE is, en de zelfde standaardhaven, 33456, in gebruik door veelvoudige clusters kan zijn, is het mogelijk dat clusters die niet zouden moeten proberen om mee te delen onverwacht dit-bijvoorbeeld, de productie en clusters QA afzonderlijk zouden moeten blijven, maar met elkaar via UDP multicast kunnen verbinden.

De gemeenschappelijkste situatie wanneer u dubbele havens in een netwerk zou kunnen ontdekken waaraan GemFire zich incorrect het groeperen is tijdens laarzentrekker van een cluster. Wat u kunt vinden is dat het laarzentrekkerproces zonder duidelijke oorzaak ontbreekt. Typisch, worden de fouten zoals dit gezien:

```xml
Caused by: com.ibm.ejs.container.UnknownLocalException: nested exception is: com.adobe.pof.schema.ObjectTypeNotFoundException: Object Type: dsc.sc_service_configuration not found.
                at com.adobe.pof.schema.POFDefaultDomain.getObjectType(POFDefaultDomain.java:93)
                at com.adobe.idp.dsc.initializer.DSCInitializerBean.serviceConfigAuditAttributeExists(DSCInitializerBean.java:225)
                at com.adobe.idp.dsc.initializer.DSCInitializerBean.installSchema(DSCInitializerBean.java:186)
                at com.adobe.idp.dsc.initializer.DSCInitializerBean.bootstrap(DSCInitializerBean.java:94)
                at com.adobe.idp.dsc.initializer.EJSLocalStatelessDSCInitializerBeanLocalEJB_7bb34e85.bootstrap(Unknown Source)
                at com.adobe.livecycle.bootstrap.bootstrappers.DSCBootstrapper.bootstrap(DSCBootstrapper.java:68)
```

In dit geval, werkt bootstrapper met GemFire om tot de vereiste lijsten toegang te hebben, en er is een inconsistentie tussen de lijsten die door JDBC worden betreden en de caching lijstinformatie die door GemFire wordt teruggekeerd, die uit een verschillende cluster met een verschillend onderliggende gegevensbestand komt.

Hoewel een dubbele haven vaak tijdens laarzentrekker zal duidelijk worden, is het mogelijk voor deze situatie om later omhoog te tonen, wanneer een cluster na zijn neer wordt hervat wanneer laarzentrekker van de andere cluster voorkwam, of wanneer de netwerkconfiguratie wordt veranderd om clusters te maken die eerder, voor multicast doeleinden, aan elkaar zichtbaar waren.

Om deze situaties te diagnostiseren, is het best om de logboeken van GemFire te bekijken en zorgvuldig te overwegen of slechts de verwachte knopen worden gevonden. Om het probleem te verhelpen, moet het

`adobe.cache.multicast-port`

een andere waarde in een van beide clusters.

### 2) GDS delen {#gds-sharing}

Het delen van GDS wordt gevormd buiten AEM Forms op JEE zelf, op O/S niveau, waar u voor de zelfde gedeelde folderstructuur moet schikken om aan alle clusterknopen beschikbaar te zijn. Op Windows-typesystemen wordt dit gewoonlijk bereikt door een bestandsdeling in te stellen van het ene knooppunt naar het andere of van een extern bestandssysteem zoals een NAS-apparaat naar alle knooppunten. Op UNIX-systemen wordt het delen van GDS doorgaans uitgevoerd via het delen van NFS-bestanden, opnieuw van de ene node naar de andere of van een NAS-apparaat.

Een mogelijke foutmodus voor de cluster is als dit externe bestandsgedeelte niet beschikbaar wordt of als er subtiele problemen optreden. Een verre onderstel zou wegens netwerkproblemen, veiligheidsmontages of onjuiste configuratie kunnen ontbreken. Een systeem reboot kan configuratieveranderingen veroorzaken die dagen of weken van tevoren worden aangebracht om van kracht te worden, en dit kan verrassingen veroorzaken.

**Wat zou er gebeuren als een NFS-share niet in de configuratie wordt opgenomen?**

Op UNIX, kan de manier dat de steunen NFS aan de folderstructuur worden in kaart gebracht voor een duidelijk bruikbare GDS folder om beschikbaar te zijn, zelfs als het bedrag ontbreekt. Overweeg:

* NAS-server: Gedeelde NFS-map /u01/iapply/livecycle_gds
* Knooppunt 1: een koppelingspunt naar de gedeelde map (gehost op de DB-server) die hier is te vinden: /u01/iapply/livecycle_gds
* Knooppunt 2: een koppelingspunt naar de gedeelde map (gehost op de DB-server) die hier is te vinden: /u01/iapply/livecycle_gds

* LCES geeft het pad naar GDS aan: /u01/iapply/livecycle_gds

Als de montage op Node 1 ontbreekt, zal de folderstructuur nog een weg /u01/iapply/livecycle_gds aan het lege koppelingspunt bevatten, en de knoop zal schijnen correct te lopen. Maar aangezien de inhoud GDS niet eigenlijk met de andere knoop wordt gedeeld, zal de cluster niet behoorlijk werken. Dit kan en doet zich voor, en het resultaat is dat de cluster op mysterieuze manieren faalt.

De beste praktijken moeten dingen schikken zodat het Linux onderstelpunt niet als wortel van GDS wordt gebruikt, maar in plaats daarvan wordt één of andere folder binnen het gebruikt als wortel GDS:

* Als u een NFS-server hebt, heeft deze mogelijk een map: /some/storage/lc_cluster_dev/LC_GDS
* En op uw clusterknooppunt hebt u een koppelpunt: /u01/iapply/shared
* Nfs_server koppelen: /some/storage/lc_cluster_dev/u01/iapply/shared
* Wijs uw GDS aan /u01/iapply/shared/LC_GDS

Nu als om één of andere reden het bedrag niet slaagt, bevat het kale onderstelpunt geen folder LC_GDS en uw cluster zal voorspelbaar ontbreken, aangezien het geen GDS bij allen kan vinden.

**Hoe kan ik verifiëren dat alle knopen zelfde GDS zien en toestemmingen hebben?**

De verificatie van GDS-toegang en delen kan het best worden uitgevoerd door elk van de knooppunten als interactieve gebruiker te benaderen, via SSH of telnet naar UNIX-knooppunten of via een externe desktop naar Windows-systemen. U zou aan de gevormde GDS folder of het dossiersysteem op elke knoop moeten kunnen navigeren en testdossiers van elke knoop tot stand brengen die in alle andere knopen zichtbaar zijn.

Let op de gebruikersnaam waaronder AEM Forms op JEE werkt. Bij de kant-en-klare installaties van Windows is dit als een lokale beheerder. Op UNIX, kan het als specifieke de dienstgebruiker zijn die in het startmanuscript of in de configuratie van de toepassingsserver wordt gevormd. Het is belangrijk dat deze gebruikers-id GDS-bestanden op alle knooppunten op dezelfde manier kan maken en manipuleren.

Bij UNIX-systemen worden in NFS-configuraties vaak de basiseigendom of basistoegangsrechten voor bestanden en objecten wantrouwd. Als u de toepassingsserver als wortelgebruiker in werking stelt, belangrijkste vindt u dat u opties op de server NFS, de knoop moet specificeren die de dossiers, of allebei koppelen om bilaterale toegang en controle van dossiers toe te staan die door één knoop worden gecreeerd en door een andere worden betreden.

### (3) Gegevensdeling {#database-sharing}

Een cluster werkt alleen correct als dezelfde database wordt gedeeld door alle clusterleden. De mogelijkheden om dit verkeerd te doen zijn ruwweg:

* het per ongeluk anders instellen van IDP_DS, EDC_DS, AdobeDefaultSA_DS of andere vereiste gegevensbronnen op afzonderlijke clusterknooppunten, zodat de knooppunten naar verschillende databases wijzen.
* per ongeluk meerdere afzonderlijke knooppunten instellen om een database te delen wanneer dat niet het geval is.

Afhankelijk van uw toepassingsserver, kan het natuurlijk zijn dat de verbinding JDBC bij een clusterwerkingsgebied wordt bepaald, zodat de verschillende definities niet mogelijk op verschillende knopen zijn. Op Jreliëf, echter, is het volledig mogelijk om dingen opstelling zodat een gegevensbron, zoals IDP_DS, aan één gegevensbestand op knoop 1 richt, maar aan iets anders op knoop 2 wijst.

Het omgekeerde probleem is eigenlijk gemeenschappelijker-dat is, een situatie waar de veelvoudige standalone (of cluster) AEM Forms op knopen JEE per ongeluk bij het zelfde schema richten wanneer zij niet bedoeld zijn aan. Dit gebeurt het vaakst wanneer DBA onbewust één enkele AEM Forms op de verbindingsinformatie van het gegevensbestand JEE aan zowel DEV als QA opstellingsteams geeft, realiserend geen van hen dat de instanties DEV en QA afzonderlijke gegevensbestanden vereisen.

## Toepassingsservercluster {#application-server-cluster-1}

Voor een geslaagde AEM Forms in JEE-cluster is het van essentieel belang dat de toepassingsserver correct wordt geconfigureerd en uitgevoerd als een cluster. In WebSphere en Weblogic is dit een eenvoudig, goed gedocumenteerd proces. In Jreliëf, is de clusterconfiguratie een beetje meer hands-on, en het verzekeren van de knopen wordt gevormd om als cluster te handelen en in feite vinden en met elkaar communiceren kan een uitdaging zijn. JBoss baseert zich intern op JGroups, die UDP multicast gebruikt om met peer knopen te vinden en te coördineren, en sommige problemen die met GemFire worden vermeld kunnen voorkomen, zoals knopen die elkaar niet vinden wanneer zij zouden moeten, of het vinden van elkaar vinden wanneer zij niet zouden moeten.

Referenties:

* [Hoge beschikbaarheid van bedrijfsservices via JBoss-clusters](https://docs.jboss.org/jbossas/jboss4guide/r4/html/cluster.chapt.html)

* [Oracle WebLogic Server - Clusters gebruiken](https://docs.oracle.com/cd/E12840_01/wls/docs103/pdf/cluster.pdf)

### Hoe controleer ik dat JBoss correct zich groepeert? {#check-jboss-clustering}

Wanneer JBoss begint, aangezien de clusterleden worden ontdekt, worden de het niveauberichten van INFO over de knoop die tot de cluster toetreden geregistreerd aan het logboekdossier/de console.

Als een clusternaam via bevel-lijn -g optie bij looppas werd gespecificeerd, zult u berichten gelijkend op het volgende zien:

```xml
GMS: address is 10.36.34.44:55200 (cluster=QE_cluster)
GMS: address is 10.36.34.44:55200 (cluster=QE_cluster-HAPartitionCache)
and ones like:

[org.jboss.ha.framework.interfaces.HAPartition.QE_cluster] (JBoss System Threads(1)-3) Number of cluster members: 1
2011-07-14 11:34:03,072 INFO  [org.jboss.ha.framework.interfaces.HAPartition.QE_cluster] (JBoss System Threads(1)-3) Other members: 0
2011-07-14 11:34:03,138 INFO  [org.jboss.cache.RPCManagerImpl] (main) Received new cluster view: [10.36.34.44:55200|0] [10.36.34.44:55200]
2011-07-14 11:34:03,139 INFO  [org.jboss.cache.RPCManagerImpl] (main) Cache local address is 10.36.34.44:55200
```

### Kwartzplanner {#quartz-scheduler}

AEM Forms over JEE&#39;s gebruik van de interne Kwartplanner in een cluster is meestal bedoeld om automatisch de globale clusterconfiguratie van AEM Forms op JEE in het algemeen te volgen. Er is, echter een insect, #2794033, die de automatische clusterconfiguratie van Kwartz veroorzaakt om te ontbreken als de merktekens van TCP voor Gemfire in plaats van multicast autodiscovery worden gebruikt. In dit geval, zal Kwartz verkeerd lopen op een nonclustered wijze. Hierdoor worden patstellingen en gegevensbeschadiging in de tabellen van het Kwartz gemaakt. De bijwerkingen zijn erger in versie 8.2.x dan 9.0, omdat Kwartz niet zo veel wordt gebruikt, maar er nog steeds is.

Voor dit probleem zijn de volgende correcties beschikbaar: 8.2.1.2 QF2.143 en 9.0.0.2 QF2.44.

Er is ook een tijdelijke oplossing, die beide eigenschappen moet instellen:

* `-Dadobe.cache.cluster.locators=xxx`

* `-Dadobe.cache.cluster-locators=xxx`

Bij de ene instelling wordt een punt tussen &quot;cluster&quot; en &quot;locators&quot; gebruikt en bij de andere een afbreekstreepje. Dit is gemakkelijk uit te voeren en minder riskant dan het toepassen van een softwareflard, maar het impliceert kunstmatig het creëren van een verwarrend extra, naamloos configuratieplaatsen.

### Hoe controleer ik dat Kwartz als één enkele knoop of cluster loopt? {#check-quartz}

Om te bepalen hoe Kwartz zich heeft gevormd, moet u de berichten bekijken die door AEM Forms op de dienst van de Planner JEE tijdens opstarten worden geproduceerd. Deze berichten worden geproduceerd bij ernst INFO, en het kan noodzakelijk zijn om het logboekniveau aan te passen en opnieuw te beginnen om de berichten te verkrijgen. In de AEM Forms op JEE startopeenvolging, begint de initialisering van het Kwartz met de volgende lijn:

INFO `[com.adobe.idp.scheduler.SchedulerServiceImpl]` IDPSchedulerService onLoad
Het is belangrijk om van deze eerste lijn in de logboeken de plaats te bepalen omdat sommige toepassingsservers Kwartz ook gebruiken, en hun instanties van Kwartz zouden niet met de instantie moeten worden verward die door AEM Forms op de dienst van de Planner JEE wordt gebruikt. Dit is de aanwijzing dat de dienst van de Planner begint, en de lijnen die het volgen zullen u vertellen of het of niet op gegroepeerde wijze behoorlijk begint. Verscheidene berichten verschijnen in deze opeenvolging, en het is het laatste &quot;begonnen&quot;bericht dat onthult hoe Kwartz wordt gevormd:

Hier wordt de naam van het Kwartz-exemplaar gegeven: `IDPSchedulerService_$_ap-hp8.ottperflab.adobe.com1312883903975`. De naam van de instantie van het Kwartz van de planner zal altijd met het koord `IDPSchedulerService_$_` beginnen. Het koord dat aan het eind van dit wordt toegevoegd vertelt u al dan niet Kwartz op gegroepeerde wijze loopt. De lange unieke die herkenningsteken van hostname van de knoop en een lange koord van cijfers, hier `ap-hp8.ottperflab.adobe.com1312883903975` wordt geproduceerd, wijst erop dat het in een cluster werkt. Als het als één enkele knoop werkt, dan zal het herkenningsteken een twee cijferaantal, &quot;20&quot;zijn:

INFO `[org.quartz.core.QuartzScheduler]` Scheduler `IDPSchedulerService_$_20` is gestart.
Deze controle moet op alle clusterknopen afzonderlijk worden gedaan, aangezien de planner van elke knoop onafhankelijk bepaalt of om op clusterwijze te werken.

### Welke problemen ontstaan er als Kwartz in de verkeerde modus wordt uitgevoerd? {#quartz-running-in-wrong-mode}

Als het Kwartz opstelling is om als één enkele knoop in werking te stellen, maar eigenlijk in een cluster loopt en het delen van de gegevensbestandlijsten van Kwartz met andere knopen, zal dit in onbetrouwbare verrichting van de dienst van de Planner van AEM Forms op JEE resulteren en zal gewoonlijk vergezeld gaan van gegevensbestandblokkeringen. Dit is een typisch stapelspoor dat u in deze situatie zou kunnen zien:

```xml
[1/20/11 10:40:57:584 EST] 00000035 ErrorLogger   E org.quartz.core.ErrorLogger schedulerError An error occured while marking executed job complete. job= 'Asynchronous.TaskFormDataSaved:12955380518320.5650479324757354'
 org.quartz.JobPersistenceException: Couldn't remove trigger: ORA-00060: deadlock detected while waiting for resource  [See nested exception: java.sql.SQLException: ORA-00060: deadlock detected while waiting for resource ]
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.removeTrigger(JobStoreSupport.java:1405)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.triggeredJobComplete(JobStoreSupport.java:2888)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport$38.execute(JobStoreSupport.java:2872)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport$40.execute(JobStoreSupport.java:3628)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.executeInNonManagedTXLock(JobStoreSupport.java:3662)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.executeInNonManagedTXLock(JobStoreSupport.java:3624)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.triggeredJobComplete(JobStoreSupport.java:2868)
        at org.quartz.core.QuartzScheduler.notifyJobStoreJobComplete(QuartzScheduler.java:1698)
        at org.quartz.core.JobRunShell.run(JobRunShell.java:273)
        at org.quartz.simpl.SimpleThreadPool$WorkerThread.run(SimpleThreadPool.java:529)
Caused by: java.sql.SQLException: ORA-00060: deadlock detected while waiting for resource
```

### Hoe synchroniseer ik systeemklokken in een cluster? {#ynchronize-system-clocks-cluster}

Een cluster werkt alleen probleemloos als de klokken op alle clusterknooppunten nauwkeurig zijn gesynchroniseerd. Dit kan niet voldoende met de hand worden gedaan en moet worden gedaan door een of andere vorm van tijdsynchronisatiedienst die zeer regelmatig loopt. De klokken op alle knopen moeten binnen een seconde van elkaar zijn. De beste praktijken dicteren dat niet alleen de clusterknopen, maar ook de ladingsbalancer, gegevensbestandserver, de server GDS NAS, en om het even welke andere componenten allen worden gesynchroniseerd.

De tijdsynchronisatie van vensters neigt naar het domeincontrolemechanisme. De systemen van UNIX kunnen het gebruiken van NTP aan een verschillende tijdbron synchroniseren. Het is beter als alle systemen—zowel de AEM Forms op JEE-knooppunten als andere systeemcomponenten—indien mogelijk met dezelfde bron synchroniseren.

Zelfs in de meest tijdelijke testomgevingen is het absoluut niet voldoende om de klokken handmatig in te stellen op de knooppunten. Handmatig het plaatsen van de klokken zal niet nauwkeurige genoeg synchronisatie geven, en de klokken op de twee knopen zullen onvermijdelijk met betrekking tot elkaar drijven, zelfs over een periode van enkel een dag. Een actief mechanisme van de tijdsynchronisatie is essentieel aan betrouwbare clusterverrichting.

### Balans laden {#load-balancer}

Een typisch vereiste voor een cluster die gebruikers-interactieve diensten verleent is een HTTP ladingsverdeler die HTTP- verzoeken over de cluster zal verdelen. Als u een taakverdelingsmechanisme met een AEM Forms on JEE-cluster kunt gebruiken, moet u het volgende configureren:

* zittingsvastheid

* URL-herschrijfregels

* health check van knooppunt

### Wat moet ik doen met mijn Load Balancer health check functie? {#load-balancer-health-check}

Sommige taakverdelingsmechanismen kunnen worden geconfigureerd om een periodieke health check uit te voeren op de knooppunten die in evenwicht zijn met de belasting. Doorgaans is dit een URL naar een toepassingsfunctie waartoe het taakverdelingsmechanisme toegang probeert te krijgen. Als de lading slaagt, dan wordt de knoop verondersteld om gezond te zijn en in de lading het in evenwicht brengen reeks gehouden. Als de URL niet kan worden geladen, wordt ervan uitgegaan dat het knooppunt niet correct is en uit de set wordt verwijderd. Doorgaans is de URL van de health check verbonden met de AEM Forms op de JEE AdminUI-aanmeldingspagina. Dit is geen ideale health check voor een clusterlid en het is beter om een kortstondig proces te implementeren en de REST API-URL te gebruiken als de health check-functie.

## Tijdelijk bestandspad en vergelijkbare clusterinstellingen {#temporary-file-path-cluster-settings}

Bepaalde instellingen voor bestandspaden in AEM Forms op JEE worden in de hele cluster ingesteld en hebben op elk knooppunt dezelfde effectieve instelling, maar worden onafhankelijk van elk knooppunt geïnterpreteerd om naar lokale bestanden te verwijzen. De belangrijkste aandachtspunten zijn de padinstellingen voor lettertypen en de instellingen voor tijdelijke mappen. Ga naar het scherm AdminUI Core Configurations (Home > Settings > Core System > Core Configurations)

De volgende instellingen moeten worden gecontroleerd:

1. Locatie van tijdelijke map
1. Locatie van de map Adobe Server Fonts
1. Locatie van de map Customer Fonts
1. Locatie van de map System Fonts
1. Locatie van het configuratiebestand van Data Services

De cluster heeft slechts één enkele weg die voor elk van deze configuratiemontages plaatst. De locatie van de Temp-directory kan bijvoorbeeld `/home/project/QA2/LC_TEMP` zijn. In een cluster, is het noodzakelijk dat elke knoop eigenlijk dit bepaalde weg toegankelijk heeft. Als een knooppunt het verwachte tijdelijke bestandspad heeft en een ander knooppunt niet, werkt het knooppunt dat niet correct.

Hoewel deze bestanden en paden kunnen worden gedeeld tussen de knooppunten of afzonderlijk of op externe bestandssystemen, is het doorgaans aan te raden dat het lokale kopieën zijn van de schijfopslag van het lokale knooppunt.

Met name het tijdelijke mappad mag niet worden gedeeld tussen knooppunten. Een procedure vergelijkbaar met de procedure die wordt beschreven voor de verificatie van de GDS moet worden gebruikt om te controleren of de tijdelijke map niet wordt gedeeld: Ga naar elke knoop, creeer een tijdelijk dossier in de weg die door weg het plaatsen wordt vermeld, en verifieer dan dat de andere knopen niet het dossier delen. Het tijdelijke mappad moet, indien mogelijk, verwijzen naar de lokale schijfopslag op elk knooppunt en moet worden gecontroleerd.

Voor elk van de wegmontages, zorg ervoor dat de weg eigenlijk bestaat en van elke knoop in de cluster toegankelijk is, gebruikend de efficiënte gebruiksidentiteit waaronder AEM Forms op JEE loopt. De inhoud van de fontmap moet leesbaar zijn. De tijdelijke map moet lezen, schrijven en besturen toestaan.
