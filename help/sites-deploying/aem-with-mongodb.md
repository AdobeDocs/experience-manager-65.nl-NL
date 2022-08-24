---
title: AEM met MongoDB
seo-title: AEM with MongoDB
description: Leer meer over de taken en overwegingen die nodig zijn voor een geslaagde AEM met de implementatie van MongoDB.
seo-description: Learn about the tasks and considerations needed for a successful AEM with MongoDB deployment.
uuid: 8028832d-10de-4811-a769-fab699c162ec
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: cd3b979f-53d4-4274-b4eb-a9533329192a
docset: aem65
exl-id: 70a39462-8584-4c76-a097-05ee436247b7
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '6496'
ht-degree: 0%

---

# AEM met MongoDB{#aem-with-mongodb}

Dit artikel is bedoeld om de kennis over taken en overwegingen te verbeteren die nodig zijn om Adobe Experience Manager met MongoDB succesvol te implementeren.

Voor meer informatie over de implementatie raadpleegt u de [Implementeren en onderhouden](/help/sites-deploying/deploy.md) van de documentatie.

## Wanneer gebruikt u MongoDB met AEM {#when-to-use-mongodb-with-aem}

MongoDB wordt doorgaans gebruikt voor het ondersteunen van AEM implementaties van auteurs, waarbij aan een van de volgende criteria wordt voldaan:

* Meer dan 1000 unieke gebruikers per dag;
* meer dan 100 gelijktijdige gebruikers;
* Hoge volumes paginabewerkingen;
* Grote rollouts of activeringen.

Bovenstaande criteria gelden alleen voor de auteur-instanties en niet voor publicatieinstanties die allemaal op TarMK moeten zijn gebaseerd. Het aantal gebruikers verwijst naar geverifieerde gebruikers, omdat instanties van auteurs geen ongeautoriseerde toegang toestaan.

Als niet aan de criteria wordt voldaan, dan wordt een actieve TarMK/standby plaatsing geadviseerd om beschikbaarheid te richten. Over het algemeen moet MongoDB worden overwogen in situaties waarin de schaalvereisten groter zijn dan wat met één hardwareonderdeel kan worden bereikt.

>[!NOTE]
>
>Aanvullende informatie over de grootte van auteur-instanties en de definitie van gelijktijdige gebruikers vindt u in de [Richtlijnen voor hardwareaanpassing](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel).

### Minimale MongoDB-implementatie voor AEM {#minimal-mongodb-deployment-for-aem}

Hieronder vindt u een minimale implementatie voor AEM op MongoDB. Voor eenvoud, zijn de SSL beëindiging en de componenten van de Volmacht van HTTP algemeen gemaakt. Het bestaat uit één MongoDB-replicaset, met één primaire en twee secondejaren.

![chlimage_1-4](assets/chlimage_1-4.png)

Een minimale implementatie vereist 3 `mongod` instanties die zijn geconfigureerd als een replicaset. Eén instantie wordt primair gekozen en de andere instanties zijn gedetacheerd, waarbij de verkiezing wordt beheerd door `mongod`. Aan elke instantie is een lokale schijf gekoppeld. Om de cluster in staat te stellen het laden te ondersteunen, wordt een minimale doorvoer van 12 MB/s met meer dan 3000 I/O-bewerkingen per seconde (IOPS) aanbevolen.

De AEM auteurs zijn verbonden met de `mongod` instanties, waarbij elke AEM auteur verbinding maakt met alle drie `mongod` instanties. Schrijven worden naar de primaire pagina verzonden en kunnen vanuit elk van de gevallen worden gelezen. Het verkeer wordt verdeeld gebaseerd op lading door een verzender aan om het even welke actieve AEM auteur instanties. De OAK-gegevensopslag is een `FileDataStore`en MongoDB-controle wordt geleverd door MMS of MongoDB Ops Manager, afhankelijk van de locatie van de implementatie. Het niveau van het werkende systeem en logboekcontrole wordt verstrekt door derdeoplossingen zoals Splunk of Ganglia.

In deze implementatie zijn alle componenten vereist voor een geslaagde implementatie. Bij ontbrekende componenten blijft de implementatie onfunctioneel.

### Besturingssystemen {#operating-systems}

Voor een lijst met ondersteunde besturingssystemen voor AEM 6 raadpleegt u de [Pagina Technische vereisten](/help/sites-deploying/technical-requirements.md).

### Omgevingen {#environments}

Gevirtualiseerde omgevingen worden ondersteund op voorwaarde dat er goede communicatie is tussen de verschillende technische teams die het project uitvoeren. Dit omvat het team dat AEM uitvoert, het team dat eigenaar is van het besturingssysteem en het team dat de gevirtualiseerde infrastructuur beheert.

Er zijn specifieke vereisten met betrekking tot de I/O-capaciteit van de MongoDB-instanties die moeten worden beheerd door het team dat de gevirtualiseerde omgeving beheert. Als in het project gebruik wordt gemaakt van een cloudimplementatie, zoals Amazon Web Services, moeten instanties over voldoende I/O-capaciteit en consistentie beschikken om de MongoDB-instanties te ondersteunen. Anders zullen de processen van MongoDB en de eiken bewaarplaats onbetrouwbaar en onregelmatig presteren.

In de gevirtualiseerde omgevingen heeft MongoDB specifieke I/O- en VM-configuraties nodig om ervoor te zorgen dat de opslagengine van MongoDB niet wordt verlamd door het beleid voor VMWare-brontoewijzing. Een geslaagde implementatie zal ervoor zorgen dat er geen barrières zijn tussen de verschillende teams en iedereen wordt ondertekend om de vereiste prestaties te leveren.

## Overwegingen voor hardware {#hardware-considerations}

### Opslag {#storage}

Om de lees- en schrijfdoorvoer te behalen voor de beste prestaties zonder de noodzaak van premature horizontale schaling, heeft MongoDB doorgaans SSD-opslag of -opslag nodig met dezelfde prestaties als SSD.

### RAM {#ram}

Voor MongoDB-versies 2.6 en 3.0 die de MMAP-opslagengine gebruiken, is het vereist dat de werkset van de database en de bijbehorende indexen in het RAM passen.

Onvoldoende RAM-geheugen leidt tot een aanzienlijke prestatievermindering. De grootte van de werkset en van de database is sterk afhankelijk van de toepassing. Hoewel sommige schattingen kunnen worden gemaakt, is de betrouwbaarste manier om te bepalen hoeveel RAM-geheugen nodig is, het bouwen van de AEM en het testen van de belasting.

Ter ondersteuning van het laadtestproces kan de volgende verhouding tussen werkset en totale databasegrootte worden aangenomen:

* 1:10 voor SSD-opslag
* 1:3 voor harde-schijfopslag

Dit betekent dat in het geval van SSD-implementaties 200 GB RAM vereist is voor een 2 TB-database.

Hoewel de zelfde beperkingen op de opslag WiredTiger motor in MongoDB 3.0 van toepassing zijn, is de correlatie tussen de het werk reeks, RAM en paginafouten niet zo sterk aangezien WiredTiger geen geheugenafbeelding op dezelfde manier gebruikt als de MMAP opslagmotor.

>[!NOTE]
>
>Adobe raadt aan de WiredTiger-opslagengine te gebruiken voor AEM 6.1-implementaties die MongoDB 3.0 gebruiken.

### Gegevensopslag {#data-store}

Vanwege de beperkingen van de MongoDB-werkset wordt sterk aanbevolen dat de gegevensopslag onafhankelijk van de MongoDB wordt onderhouden. In de meeste omgevingen `FileDataStore` gebruik te maken van een NAS die voor alle AEM beschikbaar is. Voor situaties waarin de Amazon Web Services wordt gebruikt, is er ook een `S3 DataStore`. Als om het even welke reden de gegevensopslag binnen MongoDB wordt gehandhaafd, zou de grootte van de datastore aan de totale gegevensbestandgrootte moeten worden toegevoegd en de werksetberekeningen dienovereenkomstig worden aangepast. Dit kan betekenen dat u aanzienlijk meer RAM-geheugen ter beschikking moet stellen om de prestaties te handhaven zonder paginafouten.

## Bewaking {#monitoring}

Controle is van essentieel belang voor een succesvolle uitvoering van het project. Hoewel het met voldoende kennis van zaken mogelijk is om AEM op MongoDB zonder controle in werking te stellen, wordt die kennis gewoonlijk gevonden in ingenieurs die voor elke sectie van de plaatsing worden gespecialiseerd.

Hierbij gaat het doorgaans om een O&amp;O-engineer die werkt aan de Apache Oak Core en een MongoDB-specialist.

Zonder controle op alle niveaus zal gedetailleerde kennis van de codebasis worden vereist om kwesties te diagnostiseren. Met toezicht en passende richtsnoeren voor de belangrijkste statistieken zullen de implementatieteams adequaat kunnen reageren op anomalieën.

Hoewel het mogelijk is opdrachtregelprogramma&#39;s te gebruiken om een snelle momentopname van de werking van een cluster te krijgen, is het vrijwel onmogelijk dat in real-time op veel hosts gebeurt. Met opdrachtregelprogramma&#39;s wordt zelden meer dan een paar minuten historische informatie gegeven en is geen kruiscorrelatie tussen verschillende typen meetgegevens mogelijk. Een korte periode van langzame achtergrond `mongod` Voor synchronisatie is een aanzienlijke handmatige inspanning vereist om de correlatie tussen I/O te herstellen. Wacht of te veel schrijfniveaus naar een gedeelde opslagbron van een ogenschijnlijk niet-aangesloten virtuele machine.

### MongoDB Cloud Manager {#mongodb-cloud-manager}

MongoDB Cloud Manager is een gratis service die wordt aangeboden door MongoDB en waarmee u de instanties van MongoDB kunt controleren en beheren. Het biedt een weergave in real-time van de prestaties en gezondheid van de MongoDB-cluster. Het beheert zowel clouds als privégehoste instanties op voorwaarde dat de instantie de controleserver van Cloud Manager kan bereiken.

Het vereist een agent die op de instantie MongoDB wordt geïnstalleerd die met de controleserver verbindt. Er zijn 3 niveaus van de agent:

* Een automatiseringsagent die alles op de MongoDB-server volledig kan automatiseren,
* Een controleagent die de `mongod` instantie,
* Een back-upagent die geplande back-ups van de gegevens kan uitvoeren.

Hoewel het gebruik van Cloud Manager voor onderhoudsautomatisering van een MongoDB-cluster veel routinetaken eenvoudiger maakt, is dit niet nodig en wordt het ook niet gebruikt voor back-up. Wanneer u Cloud Manager kiest om te controleren, is bewaking echter vereist.

Voor meer informatie over MongoDB Cloud Manager raadpleegt u de [MongoDB-documentatie](https://docs.cloud.mongodb.com/).

### MongoDB Ops Manager {#mongodb-ops-manager}

MongoDB Ops Manager is dezelfde software als de MongoDB Cloud Manager. Zodra geregistreerd, kan de Manager van Ops plaatselijk in een privé gegevenscentrum of op een andere laptop of Desktopmachine worden gedownload en worden geïnstalleerd. Het gebruikt een lokale gegevensbestand MongoDB om gegevens op te slaan en op precies de zelfde manier als Manager van de Wolk met de beheerde servers mee te delen. Als u veiligheidsbeleid hebt dat een controleagent verhindert, zou de Manager van Ops MongoDB moeten worden gebruikt.

### Bewaking van besturingssystemen {#operating-system-monitoring}

Controle op besturingssysteemniveau is vereist om een AEM MongoDB-cluster uit te voeren.

Ganglia is een goed voorbeeld van een dergelijk systeem en biedt een beeld van het bereik en de details van de vereiste informatie die verder gaat dan elementaire gezondheidsmaatstaven zoals CPU, laadgemiddelde en vrije schijfruimte. Om problemen te diagnostiseren, is informatie op een lager niveau, zoals de niveaus van de entropiepool, I/O wachtende cpu, de contactdozen in staat FIN_WAIT2 vereist.

### Logaggregatie {#log-aggregation}

Bij een cluster met meerdere servers is centrale logboekaggregatie een vereiste voor een productiesysteem. De software zoals Splunk steunt logboeksamenvoeging en staat teams toe om de patronen van gedrag van de toepassing te analyseren zonder het moeten de logboeken manueel verzamelen.

## Controlelijsten {#checklists}

Deze sectie behandelt diverse stappen die u zou moeten nemen om ervoor te zorgen dat uw AEM en plaatsingen MongoDB behoorlijk opstelling alvorens uw project te uitvoeren zijn.

### Netwerk {#network}

1. Eerst, zorg ervoor dat alle gastheren een DNS ingang hebben
1. Alle gastheren zouden door hun DNS ingang van alle andere routable gastheren moeten oplosbaar zijn
1. Alle MongoDB-hosts zijn routeerbaar voor alle andere MongoDB-hosts in dezelfde cluster
1. MongoDB-hosts kunnen pakketten doorsturen naar MongoDB Cloud Manager en de andere controleservers
1. AEM Servers kunnen pakketten naar alle MongoDB-servers leiden
1. De latentie van het pakket tussen om het even welke AEM server en om het even welke server MongoDB is kleiner dan twee milliseconden, zonder pakketverlies en een standaarddistributie van één milliseconde of minder.
1. Zorg ervoor dat er niet meer dan twee hop tussen een AEM en een MongoDB-server is
1. Er zijn niet meer dan twee hop tussen twee MongoDB-servers
1. Er zijn geen routers hoger dan OSI Niveau 3 tussen om het even welke kernservers (MongoDB of AEM of om het even welke combinatie).
1. Als trunking van VLAN of om het even welke vorm van netwerk het een tunnel graven wordt gebruikt, moet het aan de controles van de pakketlatentie voldoen.

### AEM {#aem-configuration}

#### Knooppuntwinkelconfiguratie {#node-store-configuration}

De AEM instanties moeten worden gevormd om AEM met MongoMK te gebruiken. De basis van de MongoMK-implementatie in AEM is de Document Node Store.

Voor meer informatie hoe te om de Opslag van de Knoop te vormen, zie [Knooppuntwinkels en gegevensopslagruimten configureren in AEM](/help/sites-deploying/data-store-config.md).

Hieronder ziet u een voorbeeld van de configuratie van de Document Node Store voor een minimale implementatie van MongoDB:

```xml
# org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config
#MongoDB server details
mongodburi=mongodb://aem:aempassword@mongodbserver1.customer.com:27000,mongodbserver2.customer.com:27000

#Name of MongoDB database to use
db=aem

#Store binaries in custom BlobStore e.g. FileDataStore
customBlobStore=true

cache=2048
blobCacheSize=1024
```

Waar:

* `mongodburi`
Dit is de MongoDB-server waarmee AEM verbinding moet maken. Verbindingen worden gemaakt met alle bekende leden van de standaardreplicaset. Als MongoDB Cloud Manager wordt gebruikt, is de serverbeveiliging ingeschakeld. Daarom moet de verbindingstekenreeks een geschikte gebruikersnaam en wachtwoord bevatten. Niet-zakelijke versies van MongoDB ondersteunen alleen gebruikersnaam- en wachtwoordverificatie. Voor meer informatie over de syntaxis van de verbindingstekenreeks raadpleegt u de [documentatie](https://docs.mongodb.org/manual/reference/connection-string/).

* `db`
De naam van de database. De standaardwaarde voor AEM is 
`aem-author`.

* `customBlobStore`
Als de plaatsing binaire getallen in het gegevensbestand opslaat, zullen zij deel van de het werk reeks uitmaken. Daarom wordt aangeraden om geen binaire bestanden in MongoDB op te slaan, waarbij een andere datastore wordt uitgevoerd als een 
`FileSystem` datastore op een NAS.

* `cache`
De cachegrootte in megabytes. Dit wordt verdeeld over verschillende caches die worden gebruikt in de 
`DocumentNodeStore`. De standaardwaarde is 256 MB. Eak-leesprestaties zullen echter baat hebben bij een groter cachegeheugen.

* `blobCacheSize`
Veelgebruikte blobs kunnen door AEM in de cache worden geplaatst om te voorkomen dat ze opnieuw uit de gegevensopslag worden opgehaald. Dit heeft meer invloed op de prestaties, met name wanneer u lobs opslaat in de MongoDB-database. Alle op bestandssysteem gebaseerde gegevensopslagsystemen profiteren van de schijfcache op besturingssysteemniveau.

#### Configuratie gegevensopslag {#data-store-configuration}

De gegevensopslag wordt gebruikt om bestanden op te slaan die groter zijn dan een drempel. Onder die drempel worden bestanden als eigenschappen opgeslagen in het Document Node Store. Als de `MongoBlobStore` wordt gebruikt, wordt een specifieke inzameling gecreeerd in MongoDB om de vlekken op te slaan. Deze verzameling draagt bij aan de `mongod` -instantie, en vereist dat `mongod` heeft meer RAM om prestatieproblemen te voorkomen. Daarom wordt aanbevolen de `MongoBlobStore` voor productieimplementaties en -gebruik `FileDataStore` ondersteund door een NAS die onder alle AEM instanties wordt gedeeld. Omdat de cache op het niveau van het besturingssysteem efficiënt is voor het beheren van bestanden, moet de minimale grootte van een bestand op schijf dicht bij de blokgrootte van de schijf worden ingesteld, zodat het bestandssysteem efficiënt wordt gebruikt en veel kleine documenten niet buitensporig bijdragen aan de werkset van de `mongod` -instantie.

Hier volgt een standaardconfiguratie voor een minimale AEM implementatie met MongoDB:

```xml
# org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config
# The minimum size of an object that should be stored in this data store.
minRecordLength=4096
path=/datastore
maxCachedBinarySize=4096
cacheSizeInMB=128
```

Waar:

* `minRecordLength`
Grootte in bytes. Binaire bestanden met een grootte die kleiner is dan of gelijk is aan deze grootte, worden opgeslagen in het Document Node Store. In plaats van de id van de blob op te slaan, wordt de inhoud van het binaire bestand opgeslagen. Voor binaire getallen groter dan deze grootte wordt identiteitskaart van binair getal opgeslagen als bezit van het Document in de knooppuntinzameling, en het lichaam van binair getal wordt opgeslagen in 
`FileDataStore` op schijf. 4096 bytes is een typische blokgrootte van het dossiersysteem.

* `path`
Het pad naar de hoofdmap van de gegevensopslag. Voor een MongoMK-implementatie moet dit een gedeeld bestandssysteem zijn dat beschikbaar is voor alle AEM. Gewoonlijk wordt een NAS-server (Network Attached Storage) gebruikt. Voor cloudimplementaties zoals Amazon Web Services: 
`S3DataFileStore` is ook beschikbaar.

* `cacheSizeInMB`
De totale grootte van de binaire cache in Megabytes. Het wordt gebruikt om binaire bestanden in het cachegeheugen op te slaan die kleiner zijn dan de 
`maxCacheBinarySize` instellen.

* `maxCachedBinarySize`
De maximumgrootte in bytes van een binaire caching in het binaire geheime voorgeheugen. Als een gegevensopslag op basis van een bestandssysteem wordt gebruikt, wordt het niet aanbevolen hoge waarden te gebruiken voor de cache van de gegevensopslag, aangezien de binaire bestanden al in de cache zijn opgeslagen door het besturingssysteem.

#### De queryhint uitschakelen {#disabling-the-query-hint}

Men adviseert dat u de vraagwenk onbruikbaar maakt die met alle vragen wordt verzonden door het bezit toe te voegen

`-Doak.mongo.disableIndexHint=true`

bij het starten van AEM. Op deze manier zal MongoDB de meest geschikte index berekenen die op interne statistieken moet worden gebruikt.

Als de vraagwenk niet gehandicapt is, zal om het even welke prestaties het stemmen van indexen geen invloed op de prestaties van AEM hebben.

#### Blijvende cache inschakelen voor MongoMK {#enable-persistent-cache-for-mongomk}

Het wordt aanbevolen een permanente cacheconfiguratie in te schakelen voor MongoDB-implementaties, zodat omgevingen met hoge I/O-leesprestaties een maximale snelheid hebben. Zie voor meer informatie de [Jackrabbit Oak-documentatie](https://jackrabbit.apache.org/oak/docs/nodestore/persistent-cache.html).

## Optimalisatie van MongoDB-besturingssystemen {#mongodb-operating-system-optimizations}

### Ondersteuning van besturingssystemen {#operating-system-support}

MongoDB 2.6 gebruikt een in geheugen toegewezen opslagengine die gevoelig is voor bepaalde aspecten van het systeembeheer tussen RAM en schijf. De vraag en gelezen Prestaties van de instantie MongoDB baseert zich op het vermijden of het elimineren van langzame I/O verrichtingen die vaak als paginafouten worden bedoeld. Dit zijn paginafouten die van toepassing zijn op de `mongod` in het bijzonder. Ze mogen niet worden verward met paginafouten op besturingssysteemniveau.

Voor snelle verrichting zou het gegevensbestand MongoDB slechts tot gegevens moeten toegang hebben die reeds in RAM zijn. De gegevens waartoe het toegang moet krijgen, bestaan uit indexen en gegevens. Deze verzameling indexen en gegevens wordt de werkset genoemd. Als de werkset groter is dan de beschikbare RAM-geheugen, moet MongoDB die gegevens vanaf een schijf met I/O-kosten inpakken, zodat andere gegevens die al in het geheugen staan, worden verwijderd. Als de verwijdering ertoe leidt dat gegevens opnieuw worden geladen van schijfpaginafouten zullen de fouten domineren en de prestaties zullen verminderen. Als de werkset dynamisch en variabel is, worden er meer paginafouten gegenereerd om bewerkingen te ondersteunen.

MongoDB wordt uitgevoerd op een aantal besturingssystemen, waaronder een groot aantal verschillende Linux-kleuren, Windows en Mac OS. Zie [https://docs.mongodb.com/manual/installation/#supported-platforms](https://docs.mongodb.com/manual/installation/#supported-platforms) voor meer informatie. Afhankelijk van de keuze van het besturingssysteem heeft MongoDB verschillende aanbevelingen voor het niveau van het besturingssysteem. Er is gedocumenteerd op [https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration](https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration) en hier samengevat voor het gemak.

#### Linux {#linux}

* Schakel transparante kleurtonen en foutopsporing uit. Zie [Instellingen voor transparante grote pagina&#39;s](https://docs.mongodb.com/manual/tutorial/transparent-huge-pages/) voor meer informatie .
* [De voorinstellingen aanpassen](https://docs.mongodb.com/manual/administration/production-notes/#readahead) op de apparaten die uw gegevensbestanddossiers opslaan om uw gebruiksgeval aan te passen.

   * Als de werkset van de MMAPv1-opslagengine groter is dan het beschikbare RAM en het toegangspatroon van het document willekeurig is, kunt u het aflezen naar 32 of 16 verkleinen. U kunt verschillende instellingen evalueren om een optimale waarde te vinden waarmee het geheugen op de site wordt gemaximaliseerd en het aantal paginafouten wordt verminderd.
   * Voor de WiredTiger-opslagengine stelt u deze in op 0, ongeacht het type opslagmedium (draaien, SSD, enz.). Over het algemeen gebruikt u de aanbevolen instelling voor het aflezen van voorkeuren, tenzij tests een meetbaar, herhaalbaar en betrouwbaar voordeel opleveren bij een hogere aflezing. [Ondersteuning voor MongoDB Professional](https://docs.mongodb.com/manual/administration/production-notes/#readahead) kan advies en begeleiding op configuraties zonder het nulbereik bieden.

* Schakel het afgestelde gereedschap uit als u RHEL 7 / CentOS 7 in een virtuele omgeving uitvoert.
* Wanneer RHEL 7 / CentOS 7 in een virtuele omgeving wordt uitgevoerd, roept het afgestemde hulpmiddel automatisch een prestatiesprofiel aan dat uit prestatiesproductie wordt afgeleid, dat automatisch de lezingsmontages aan 4MB plaatst. Dit kan de prestaties negatief beïnvloeden.
* Gebruik de noop- of deadline schijfplanners voor SSD-stations.
* Gebruik de noop schijfplanner voor gevirtualiseerde aandrijving in gast VMs.
* NUMA uitschakelen of vm.zone_reclaim_mode instellen op 0 en uitvoeren [monniken](https://docs.mongodb.com/manual/administration/production-notes/#readahead) instanties met knooppunt interleave. Zie: [MongoDB- en NUMA-hardware](https://docs.mongodb.com/manual/administration/production-notes/#readahead) voor meer informatie .

* Pas de grenswaarden op uw hardware aan uw gebruiksscenario aan. Indien meerdere [monniken](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) of [mongos](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos) exemplaren worden uitgevoerd onder dezelfde gebruiker, de grenswaarden dienovereenkomstig schalen. Zie: [UNIX-instellingen voor limiet](https://docs.mongodb.com/manual/reference/ulimit/) voor meer informatie .

* Noatitie gebruiken voor de [dbPath](https://docs.mongodb.com/manual/reference/configuration-options/#storage.dbPath) koppelpunt.
* Configureer voldoende bestandshandgrepen (fs.file-max), de limiet voor de pid van de kernel (kernel.pid_max) en de maximale threads per proces (kernel.threads-max) voor uw implementatie. Voor grote systemen bieden de volgende waarden een goed uitgangspunt:

   * fs.file-max waarde van 98000,
   * kernel.pid_max waarde 64000,
   * andkernel.threads-max waarde van 64000

* Zorg ervoor dat er wisselruimte is geconfigureerd op uw systeem. Raadpleeg de documentatie bij het besturingssysteem voor meer informatie over de juiste grootte.
* Zorg ervoor dat het systeem standaardTCP keylive correct wordt geplaatst. Een waarde van 300 biedt vaak betere prestaties voor replicasets en gedeelde clusters. Zie: [Heeft de keyletime van TCP invloed op de Plaatsingen MongoDB?](https://docs.mongodb.com/manual/faq/diagnostics/#faq-keepalive) in de Veelgestelde Vragen voor meer informatie.

#### Windows {#windows}

* Overweeg het onbruikbaar maken NTFS &quot;laatste toegangstijd&quot;updates. Dit is gelijk aan het uitschakelen van atime op Unix-achtige systemen.

### WiredTiger {#wiredtiger}

Vanaf MongoDB 3.2 is de standaard opslagengine voor MongoDB de WiredTiger-opslagengine. Deze engine beschikt over een aantal robuuste en schaalbare functies die deze veel geschikter maken voor algemene databasewerklasten die overal ter wereld liggen. In de volgende secties worden deze functies beschreven.

#### Documentniveau gelijktijdig {#document-level-concurrency}

WiredTiger gebruikt document-vlakke gelijktijdig controle voor schrijfverrichtingen. Dientengevolge, kunnen de veelvoudige cliënten verschillende documenten van een inzameling tezelfdertijd wijzigen.

Voor de meeste lees en schrijf verrichtingen, gebruikt WiredTiger optimistische gelijktijdig controle. WiredTiger gebruikt slechts intent sloten bij de globale, gegevensbestand en inzamelingsniveaus. Wanneer de opslagengine conflicten tussen twee bewerkingen detecteert, treedt er een schrijfconflict op waardoor MongoDB deze bewerking op transparante wijze opnieuw probeert. Sommige globale bewerkingen, meestal kortstondige bewerkingen met meerdere databases, vereisen nog steeds een algemene &#39;instance-wide&#39; vergrendeling.

Voor sommige andere bewerkingen, zoals het neerzetten van een verzameling, is nog steeds een exclusieve databasevergrendeling vereist.

#### Momentopnamen en controlepunten {#snapshots-and-checkpoints}

WiredTiger gebruikt MultiVersion Concurrency Control (MVCC). Aan het begin van een verrichting, verstrekt WiredTiger een punt-in-tijd momentopname van de gegevens aan de transactie. Een momentopname stelt een verenigbare mening van de in-geheugengegevens voor.

Wanneer het schrijven aan schijf, schrijft WiredTiger alle gegevens in een momentopname aan schijf op een verenigbare manier over alle gegevensdossiers. De now- [duurzaam](https://docs.mongodb.com/manual/reference/glossary/#term-durable) gegevens fungeren als controlepunt in de gegevensbestanden. Het controlepunt zorgt ervoor dat de gegevensdossiers tot en met het laatste controlepunt verenigbaar zijn; controlepunten kunnen dus fungeren als herstelpunten.

MongoDB configureert WiredTiger om controlepunten tot stand te brengen (d.w.z. de momentopnamegegevens aan schijf te schrijven) met intervallen van 60 seconden of 2 gigabytes dagboekgegevens.

Tijdens het schrijven van een nieuw controlepunt, is het vorige controlepunt nog geldig. Als zodanig, zelfs als MongoDB beëindigt of een fout ontmoet terwijl het schrijven van een nieuw controlepunt, bij nieuw begin, kan MongoDB van het laatste geldige controlepunt terugkrijgen.

Het nieuwe controlepunt wordt toegankelijk en permanent wanneer de de meta-gegevenslijst van WiredTiger automatisch wordt bijgewerkt om naar het nieuwe controlepunt te verwijzen. Zodra het nieuwe controlepunt toegankelijk is, bevrijdt WiredTiger pagina&#39;s van de oude controlepunten.

Werken met WiredTiger, zelfs zonder [journalistiek](https://docs.mongodb.com/manual/reference/glossary/#term-durable), kan MongoDB herstellen vanaf het laatste controlepunt; nochtans, om veranderingen terug te krijgen die na het laatste controlepunt worden aangebracht, looppas met [journalistiek](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Dagboek {#journal}

WiredTiger gebruikt een write-ahead transactielogboek in combinatie met [controlepunten](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-checkpoints) om de duurzaamheid van de gegevens te waarborgen.

Het journaal WiredTiger zet alle gegevenswijzigingen tussen controlepunten voort. Als MongoDB tussen controlepunten weggaat, gebruikt het dagboek om alle gegevens opnieuw te spelen die sinds het laatste controlepunt worden gewijzigd. Voor informatie over de frequentie waarmee MongoDB de dagboekgegevens aan schijf schrijft, zie [Journalaliseringsproces](https://docs.mongodb.com/manual/core/journaling/#journal-process).

Het tijdschrift WiredTiger wordt gecomprimeerd met het [snappel](https://docs.mongodb.com/manual/core/journaling/#journal-process) compressiebibliotheek. Als u een alternatief compressiealgoritme of geen compressie wilt opgeven, gebruikt u de opdracht [storage.wiredTiger.engineConfig.journaalCompressor](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.journalCompressor) instellen.

Zie voor meer informatie: [Journalating met WiredTiger](https://docs.mongodb.com/manual/core/journaling/#journaling-wiredtiger).

>[!NOTE]
>
>De minimumgrootte van het logboekverslag voor WiredTiger is 128 bytes. Als een logboekverslag 128 bytes of kleiner is, comprimeert WiredTiger niet dat verslag.
>
>U kunt het journaling onbruikbaar maken door te plaatsen [storage.journal.enabled](https://docs.mongodb.com/manual/reference/configuration-options/#storage.journal.enabled) naar false, wat de overhead van het bijhouden van het journaal kan verminderen.
>
>Voor [standalone](https://docs.mongodb.com/manual/reference/glossary/#term-standalone) instanties, betekent het niet gebruiken van het dagboek dat u sommige gegevenswijzigingen zult verliezen wanneer MongoDB onverwacht tussen controlepunten weggaat. Voor leden van [replica-sets](https://docs.mongodb.com/manual/reference/glossary/#term-replica-set), kan het replicatieproces voldoende duurzame garanties bieden.

#### Compressie {#compression}

Met WiredTiger biedt MongoDB ondersteuning voor compressie voor alle verzamelingen en indexen. Compressie minimaliseert opslaggebruik ten koste van extra CPU.

Standaard gebruikt WiredTiger blokcompressie met de [snappel](https://docs.mongodb.com/manual/reference/glossary/#term-snappy) compressiebibliotheek voor alle verzamelingen en [voorvoegselcompressie](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) voor alle indexen.

Voor verzamelingen, blokcompressie met [zlib](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) is ook beschikbaar. Als u een alternatief compressiealgoritme of geen compressie wilt opgeven, gebruikt u de opdracht [storage.wiredTiger.collectionConfig.blockCompressor](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) instellen.

Voor indexen uitschakelen [voorvoegselcompressie](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression), gebruikt u de [storage.wiredTiger.indexConfig.prefixCompression](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.indexConfig.prefixCompression) instellen.

De montages van de compressie zijn ook configureerbaar op een per-inzameling en per-indexbasis tijdens inzameling en indexverwezenlijking. Zie [Opties voor opslagengine opgeven](https://docs.mongodb.com/manual/reference/method/db.createCollection/#create-collection-storage-engine-options) en [db.collection.createIndex() storageEngine](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/#createindex-options) optie.

Voor de meeste werklasten zijn de standaardinstellingen voor compressie een goede balans tussen de efficiëntie van de opslag en de verwerkingsvereisten.

Het tijdschrift WiredTiger wordt ook door gebrek samengeperst. Voor informatie over dagboekcompressie, zie [Dagboek](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Geheugengebruik {#memory-use}

Met WiredTiger gebruikt MongoDB zowel de interne cache van WiredTiger als de cache van het bestandssysteem.

Beginnend in 3.4, zal het interne geheime voorgeheugen WiredTiger, door gebrek, het grootste van één van beiden gebruiken:

* 50% van RAM min 1 GB, of
* 256 MB

Standaard gebruikt WiredTiger de compressie van het Snapy-blok voor alle verzamelingen en de compressie van het voorvoegsel voor alle indexen. De standaardwaarden voor compressie kunnen globaal worden geconfigureerd en kunnen ook per verzameling en per index worden ingesteld tijdens het maken van verzamelingen en indexen.

De verschillende vertegenwoordiging wordt gebruikt voor gegevens in het interne geheime voorgeheugen WiredTiger tegenover het formaat op schijf:

* De gegevens in het bestandssysteemcachegeheugen zijn gelijk aan de schijfindeling, inclusief de voordelen van compressie voor gegevensbestanden. De cache van het bestandssysteem wordt door het besturingssysteem gebruikt om de I/O van de schijf te verminderen.

De indexen die in het interne geheime voorgeheugen WiredTiger worden geladen hebben een verschillende gegevensvertegenwoordiging aan het formaat op schijf, maar kunnen nog voordeel van de compressie van de indexprefix nemen om het gebruik van RAM te verminderen.

Met compressie van indexvoorvoegsel worden algemene voorvoegsels van geïndexeerde velden gededupliceerd.

De gegevens van de inzameling in het interne geheime voorgeheugen WiredTiger zijn niet samengeperst en gebruiken een verschillende vertegenwoordiging van het formaat op schijf. Blokcompressie kan aanzienlijke opslagbesparingen op de schijf opleveren, maar gegevens moeten niet gecomprimeerd zijn om door de server te worden gemanipuleerd.

Via het filesystem geheime voorgeheugen, gebruikt MongoDB automatisch al vrij geheugen dat niet door het geheime voorgeheugen WiredTiger of door andere processen wordt gebruikt.

Om de grootte van het interne geheime voorgeheugen WiredTiger aan te passen, zie [storage.wiredTiger.engineConfig.cacheSizeGB](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.cacheSizeGB) en [—wiredTigerCacheSizeGB](https://docs.mongodb.com/manual/reference/program/mongod/#cmdoption-wiredtigercachesizegb). Vermijd het verhogen van de interne cachegrootte WiredTiger boven zijn standaardwaarde.

### NUMA {#numa}

Met niet-Uniform Memory Access (NUMA) kan een kernel bepalen hoe geheugen wordt toegewezen aan de processorkernen. Hoewel dit probeert om geheugentoegang voor kernen sneller te maken die ervoor zorgen dat zij tot de vereiste gegevens kunnen toegang hebben, mengt NUMA zich in MMAP die extra latentie introduceert aangezien leest niet kan worden voorspeld. Daarom moet NUMA worden uitgeschakeld voor de `mongod` op alle besturingssystemen die over de nodige mogelijkheden beschikken.

In wezen wordt het geheugen van een NUMA-architectuur aangesloten op de CPU en worden de CPU&#39;s aangesloten op een bus. In een architectuur SMP of UMA, wordt het geheugen verbonden met de bus en door cpu&#39;s gedeeld. Wanneer een draad geheugen op NUMA cpu toewijst het het volgens een beleid. Standaard wordt geheugen toegewezen dat aan de lokale CPU van de thread is gekoppeld, tenzij er geen vrije processor is. Op dat moment wordt geheugen van een vrije CPU tegen hogere kosten gebruikt. Zodra toegewezen, beweegt het geheugen zich niet tussen cpu&#39;s. De toewijzing wordt uitgevoerd door een beleid dat van de ouderdraad wordt geërft, die uiteindelijk de draad is die het proces begon.

In vele gegevensbestanden die de machine als multi-core uniforme geheugenarchitectuur zien, leidt dit tot eerste volledige cpu en de secundaire vulling van cpu later, vooral als een centrale draad voor de toewijzing van geheugenbuffers verantwoordelijk is. De oplossing is het beleid van NUMA van de belangrijkste draad te veranderen die wordt gebruikt om te beginnen `mongod` proces.

Dit kan worden gedaan door het volgende bevel in werking te stellen:

```shell
numactl --interleaved=all <mongod> -f config
```

Dit beleid wijst geheugen in een ronde weg over alle knopen van cpu toe die een gelijke distributie over alle knopen verzekeren. Er wordt geen optimale toegang tot het geheugen gegenereerd, zoals bij systemen met meerdere CPU-hardware. Ongeveer de helft van de geheugenbewerkingen zal langzamer en over de bus plaatsvinden, maar `mongod` is niet op optimale wijze naar NUMA geschreven, zodat het een redelijk compromis is.

### NUMA-problemen {#numa-issues}

Als de `mongod` het proces is gestart vanaf een andere locatie dan de `/etc/init.d` map, is het waarschijnlijk dat deze niet wordt gestart met het juiste NUMA-beleid. Afhankelijk van het standaardbeleid kunnen er problemen optreden. Dit komt omdat de verschillende Linux-installatieprogramma&#39;s voor pakketbeheer voor MongoDB ook een service installeren met configuratiebestanden die zich bevinden in `/etc/init.d` die de hierboven beschreven stap uitvoeren. Als u MongoDB rechtstreeks vanuit een archief installeert en uitvoert ( `.tar.gz`) moet u handmatig mongod onder de `numactl` proces.

>[!NOTE]
>
>Voor meer informatie over het beschikbare beleid NUMA raadpleegt u de [numerieke documentatie](https://linux.die.net/man/8/numactl).

Het MongoDB-proces zal zich anders gedragen in het kader van verschillende toewijzingsbeleidslijnen:

```

```

* `-membind=<nodes>`
Alleen toewijzen op de vermelde knooppunten. Mongod wijst geen geheugen toe op vermelde knooppunten en gebruikt mogelijk niet alle beschikbare geheugen.

* `-cpunodebind=<nodes>`
Alleen uitvoeren op de knooppunten. Mongod wordt alleen uitgevoerd op de opgegeven knooppunten en gebruikt alleen geheugen dat beschikbaar is op die knooppunten.

* `-physcpubind=<nodes>`
Alleen uitvoeren op vermelde CPU&#39;s (kernen). Mongod wordt alleen uitgevoerd op de CPU&#39;s die worden vermeld en gebruikt alleen geheugen dat beschikbaar is op die CPU&#39;s.

* `--localalloc`
Wijs altijd geheugen op de huidige knoop toe, maar gebruik alle knopen de draadlooppas. Als één draad toewijzing uitvoert, dan slechts zal het geheugen beschikbaar aan die cpu worden gebruikt.

* `--preferred=<node>`
Geeft de voorkeur aan toewijzing aan een knooppunt, maar valt terug naar andere knooppunten als het voorkeurknooppunt vol is. U kunt een relatieve notatie gebruiken voor het definiëren van een knooppunt. Ook, lopen de draden op alle knopen.

Een deel van het beleid kan ertoe leiden dat minder dan al beschikbaar RAM wordt gegeven aan `mongod` proces. In tegenstelling tot MySQL voorkomt MongoDB actief paginering op besturingssysteemniveau, en dus ook de `mongod` minder geheugen beschikbaar.

#### Wisselen {#swapping}

Wegens de geheugenintensieve aard van gegevensbestanden, moet de uitwisseling van het niveau van het werkende systeem worden onbruikbaar gemaakt. Met het MongoDB-proces voorkomt u dat het ontwerp wordt verwisseld.

#### Externe bestandssystemen {#remote-filesystems}

Externe bestandssystemen, zoals NFS, worden niet aanbevolen voor interne gegevensbestanden van MongoDB (de bestanden van de modelprocesdatabase), omdat deze te veel latentie introduceren. Dit mag niet worden verward met het gedeelde bestandssysteem dat vereist is voor de opslag van Oak Blob&#39;s (FileDataStore), waar NFS wordt aanbevolen.

#### Vooruit lezen {#read-ahead}

Lees-vooruit moet worden aangepast zodat wanneer een pagina wordt geplakt in het gebruik van een willekeurige leesbewerking, overbodige blokken niet van de schijf worden gelezen, wat leidt tot onnodig verbruik van I/O-bandbreedte.

### Linux-vereisten {#linux-requirements}

#### Minimale kernelversies {#minimum-kernel-versions}

* **2.6.23.** for `ext4` filesystems

* **2.6.25.** for `xfs` filesystems

#### Aanbevolen instellingen voor databaseschijven {#recommended-settings-for-database-disks}

**atijd uitschakelen**

Het wordt aanbevolen `atime` wordt uitgeschakeld voor de schijven die de databases zullen bevatten.

**De NOOP-schijfplanner instellen**

U kunt dit doen door:

Eerst, controlerend de I/O planner die momenteel wordt geplaatst. Dit kan worden gedaan door het volgende bevel in werking te stellen:

```shell
cat /sys/block/sdg/queue/scheduler
```

Als de reactie `noop` er is niets dat u verder hoeft te doen .

Als NOOP niet de I/O planner is die opstelling is, kunt u het veranderen door te lopen:

```shell
echo noop > /sys/block/sdg/queue/scheduler
```

**De waarde voor Vooraf lezen aanpassen**

Aanbevolen wordt een waarde van 32 te gebruiken voor de schijven waarop MongoDB-databases worden uitgevoerd. Dit komt neer op 16 kilobytes. U kunt dit instellen door het volgende uit te voeren:

```shell
sudo blockdev --setra <value> <device>
```

#### NTP inschakelen {#enable-ntp}

Zorg ervoor u NTP hebt geïnstalleerd en lopend op de machine die de gegevensbestanden MongoDB ontvangt. U kunt de toepassing bijvoorbeeld installeren met Yum package Manager op een CentOS-computer:

```shell
sudo yum install ntp
```

Nadat het NTP daemon is geïnstalleerd en met succes is begonnen, kunt u het driftdossier voor de tijdcompensatie van uw server controleren.

#### Transparante grote pagina&#39;s uitschakelen {#disable-transparent-huge-pages}

Red Hat Linux gebruikt een algoritme van het geheugenbeheer genoemd Transparante Grote Pagina&#39;s (THP). Het wordt aanbevolen dit uit te schakelen als u het besturingssysteem gebruikt voor databasewerklasten.

U kunt deze uitschakelen door de onderstaande procedure te volgen:

1. Open de `/etc/grub.conf` in de teksteditor van uw keuze.
1. Voeg de volgende regel toe aan het bestand grub.conf:

   ```xml
   transparent_hugepage=never
   ```

1. Tot slot controleert u of de instelling van kracht is geworden door:

   ```shell
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Als THP is uitgeschakeld, moet de uitvoer van de bovenstaande opdracht als volgt zijn:

   ```xml
   always madvise [never]
   ```

>[!NOTE]
>
>Voor meer informatie over transparante grote pagina&#39;s raadpleegt u deze [artikel](https://access.redhat.com/solutions/46111).

#### NUMA uitschakelen {#disable-numa}

In de meeste installaties waar NUMA is ingeschakeld, schakelt de MongoDB-daemon deze automatisch uit als deze als service wordt uitgevoerd vanuit de `/etc/init.d` map.

Waar dit niet het geval is, kunt u NUMA op een per procesniveau onbruikbaar maken. Voer de volgende opdrachten uit om het uit te schakelen:

```shell
numactl --interleave=all <path_to_process>
```

Wanneer `<path_to_process>` is de weg naar het monnikeproces.

Schakel vervolgens streekophaling uit door:

```shell
echo 0 > /proc/sys/vm/zone_reclaim_mode
```

#### Kneep de instellingen voor de limiet voor het mondige proces {#tweak-the-ulimit-settings-for-the-mongod-process}

Linux staat voor configureerbare controle over de toewijzing van middelen via toe `ulimit` gebruiken. Dit kan op een gebruiker of op een per procesbasis worden gedaan.

U wordt aangeraden de limiet voor het mongoproces in te stellen op basis van de [Door MongoDB aanbevolen instellingen voor limiet](https://docs.mongodb.org/manual/reference/ulimit/#recommended-ulimit-settings).

#### I/O-prestaties van MongoDB testen {#test-mongodb-i-o-performance}

MongoDB biedt een hulpprogramma met de naam `mongoperf` die is ontworpen om I/O-prestaties te testen. U wordt aangeraden dit te gebruiken om de prestaties te testen van al uw MongoDB-instanties waaruit uw infrastructuur bestaat.

Voor informatie over het gebruik `mongoperf`, bekijk de [MongoDB-documentatie](https://docs.mongodb.org/manual/reference/program/mongoperf/).

>[!NOTE]
>
>Let op: `mongoperf` is ontworpen als een indicator voor de prestaties van MongoDB op het platform waarop het wordt uitgevoerd. Daarom mogen de resultaten niet als definitief worden beschouwd voor de prestaties van een productiesysteem.
>
>Voor nauwkeuriger prestatiesresultaten kunt u complementaire tests met uitvoeren `fio` Linux.

**Leesprestaties testen op de virtuele machines die uw implementatie vormen**

Nadat u het hulpmiddel hebt geïnstalleerd, schakelaar aan de MongoDB gegevensbestandfolder om de tests in werking te stellen. Start vervolgens de eerste test door deze uit te voeren `mongoperf`met deze configuratie:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true}" | mongoperf
```

De gewenste uitvoer zou tot twee gigabytes per seconde (2GB/s) en 500.000 IOPS moeten bereiken die bij 32 draden voor alle instanties MongoDB lopen.

Voer een tweede test uit, dit keer met in geheugen toegewezen bestanden, door de `mmf:true` parameter:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true,mmf:true}" | mongoperf
```

De uitvoer van de tweede test moet aanzienlijk hoger zijn dan die van de eerste, wat de prestaties van de geheugenoverdracht aangeeft.

>[!NOTE]
>
>Controleer bij het uitvoeren van de tests de I/O-gebruiksstatistieken voor de virtuele machines in kwestie in uw besturingssysteem. Als ze waarden aangeven die lager zijn dan 100 procent voor I/O lezen, kan er een probleem zijn met uw virtuele machine.

**De schrijfprestaties van de primaire MongoDB-instantie testen**

Controleer vervolgens de I/O-schrijfprestaties van de primaire MongoDB-instantie door deze uit te voeren `mongoperf` uit de MongoDB-databasemap met dezelfde instellingen:

```shell
echo "{nThreads:32,fileSizeMB:1000,w:true}" | mongoperf
```

De gewenste output zou 12 megabytes per seconde moeten zijn en rond 3000 IOPS, met weinig variatie tussen het aantal draden bereiken.

## Stappen voor gevirtualiseerde omgevingen {#steps-for-virtualised-environments}

### VMWare {#vmware}

Als u WMWare ESX gebruikt om uw gevirtualiseerde milieu&#39;s te beheren en op te stellen, zorg ervoor u de volgende montages van de ESX console uitvoert om verrichting MongoDB aan te passen:

1. Geheugenballon uitschakelen
1. Het geheugen vooraf toewijzen en reserveren voor de virtuele machines die de MongoDB-databases zullen hosten
1. Gebruik I/O-controle van opslag om voldoende I/O toe te wijzen aan de `mongod` proces.
1. Garandeer CPU-bronnen van de computers die als host fungeren voor MongoDB door de instelling [CPU-reservering](https://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.vmadmin.doc_41/vsp_vm_guide/configuring_virtual_machines/t_allocate_cpu_resources.html)

1. Overweeg om ParaVirtual I/O-stuurprogramma&#39;s te gebruiken. Voor meer informatie over hoe te om dit te doen, controleer dit [knowledgebase, artikel](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1010398).

### Amazon Web Services {#amazon-web-services}

Raadpleeg voor meer informatie over het instellen van MongoDB met Amazon Web Services de [AWS-integratie configureren](https://docs.cloud.mongodb.com/tutorial/configure-aws-settings/) artikel op de MongoDB-website.

## MongoDB beveiligen voor implementatie {#securing-mongodb-before-deployment}

Deze advertentie bekijken op [MongoDB veilig implementeren](https://blogs.adobe.com/security/2015/07/securely-deploying-mongodb-3-0.html) voor advies over hoe te om de configuratie van uw gegevensbestanden vóór plaatsing te beveiligen.

## Dispatcher {#dispatcher}

### Het besturingssysteem kiezen voor de Dispatcher {#choosing-the-operating-system-for-the-dispatcher}

Voor een correcte implementatie van MongoDB moet het besturingssysteem dat de dispatcher host, worden uitgevoerd **Apache httpd** **versie 2.4 of hoger.**

Ook, zorg ervoor dat alle bibliotheken die in uw bouwstijl worden gebruikt bijgewerkt zijn om veiligheidsimplicaties te minimaliseren.

### Dispatcher Configuration {#dispatcher-configuration}

Een typische configuratie van de Verzender zal tussen tien tot twintig keer meer de verzoekproductie van één enkele AEM instantie dienen.

Aangezien de Dispatcher voornamelijk staatloos is, kan deze eenvoudig horizontaal worden geschaald. In sommige plaatsingen, moeten de auteurs van de toegang tot van bepaalde middelen worden beperkt. Daarom wordt u ten zeerste aangeraden een dispatcher te gebruiken bij de auteur.

Wanneer AEM zonder dispatcher wordt uitgevoerd, moet SSL-beëindiging en taakverdeling door een andere toepassing worden uitgevoerd. Dit is vereist omdat sessies affiniteit moeten hebben met de AEM instantie waarop ze zijn gemaakt, een concept dat sticky connections wordt genoemd. Het doel hiervan is ervoor te zorgen dat updates van de inhoud minimale latentie vertonen.

Controleer de [Documentatie van Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) voor meer informatie over hoe te om het te vormen.

### Aanvullende configuratie {#additional-configuration}

#### Vaste verbindingen {#sticky-connections}

Vaste verbindingen zorgen ervoor dat gepersonaliseerde pagina&#39;s en zittingsgegevens voor één gebruiker allen op de zelfde instantie van AEM samengesteld zijn. Dit gegeven wordt opgeslagen op de instantie, zodat zullen de verdere verzoeken van de zelfde gebruiker aan de zelfde instantie terugkeren.

Het wordt aanbevolen dat kleverige verbindingen zijn ingeschakeld voor alle binnenlagen die aanvragen naar de AEM instanties routeren, waardoor latere verzoeken om hetzelfde AEM te bereiken, worden aangemoedigd. Dit zal helpen latentie minimaliseren die anders merkbaar is wanneer de inhoud tussen instanties wordt bijgewerkt.

#### Lange vervaldatum {#long-expires}

Inhoud die wordt verzonden van een AEM dispatcher, heeft standaard de koppen Laatst gewijzigd en Etag, zonder aanduiding van de vervaldatum van de inhoud. Hoewel dit ervoor zorgt dat de gebruikersinterface altijd de recentste versie van het middel krijgt, betekent het ook dat browser een GET verrichting zal uitvoeren om te controleren of is het middel veranderd. Dit kan leiden tot meerdere aanvragen waarop het HTTP-antwoord 304 is (Niet gewijzigd), afhankelijk van het laden van de pagina. Voor middelen die gekend om niet te verlopen zijn, verloopt het plaatsen van een kopbal en het verwijderen van de laatste-Gewijzigde en kopballen ETag zullen ertoe leiden dat de inhoud in het voorgeheugen wordt opgeslagen en geen verdere updateverzoeken om worden gemaakt tot de datum in de kopbal van Verloopt wordt voldaan.

Nochtans, betekent het gebruiken van deze methode dat er geen redelijke manier is om het middel te veroorzaken om in browser te verlopen alvorens de kopbal verloopt. Om dit te verlichten, kan HtmlClientLibraryManager worden gevormd om onveranderlijke URLs voor cliëntbibliotheken te gebruiken.

Deze URL&#39;s worden gegarandeerd niet gewijzigd. Wanneer de hoofdtekst van de bron in de URL verandert, worden de wijzigingen automatisch doorgevoerd in de URL, zodat de browser de juiste versie van de bron aanvraagt.

De standaardconfiguratie voegt een selecteur aan HtmlClientLibraryManager toe. Als kiezer wordt de bron in de dispatcher in het cachegeheugen opgeslagen met de kiezer intact. Deze kiezer kan ook worden gebruikt om het juiste vervalgedrag te garanderen. De standaardkiezer volgt de `lc-.*?-lc` patroon. De volgende Apache httpd-configuratierichtlijnen zorgen ervoor dat alle aanvragen die overeenkomen met dat patroon, een geschikte vervaltijd krijgen.

```xml
Header set Expires "Tue, 20 Jan 2037 04:20:42 GMT" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header set Cache-Control "public, no-transform, max-age=267840000" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset ETag "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Last-Modified "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Pragma "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
```

#### Geen schuine streep {#no-sniff}

Wanneer inhoud zonder inhoudstype wordt verzonden, proberen veel browsers het type inhoud te raden door de eerste paar bytes van de inhoud te lezen. Dit heet &#39;snuiven&#39;. Door te niveren ontstaat een kwetsbaarheid voor beveiliging, omdat gebruikers die naar de opslagplaats kunnen schrijven, schadelijke inhoud zonder inhoudstype kunnen uploaden.

Daarom is het raadzaam een `no-sniff` aan bronnen die door de verzender worden aangeleverd. De verzender slaat de koppen echter niet in de cache op. Dit betekent dat voor alle inhoud die vanuit het lokale bestandssysteem wordt aangeboden, het inhoudstype wordt bepaald door de extensie in plaats van de oorspronkelijke header van het inhoudstype van de AEM server van oorsprong.

Geen sniff kan veilig worden toegelaten als de Webtoepassing gekend om nooit caching middelen zonder een dossiertype te dienen.

U kunt Geen Sniff met inbegrip van toelaten:

```xml
Header set X-Content-Type-Options "nosniff"
```

Deze kan ook selectief worden ingeschakeld:

```xml
RewriteCond %{REQUEST_URI} \.(?:js|jsonp)$ [OR]
RewriteCond %{QUERY_STRING} (callback|jsonp|cb)=\w+
RewriteRule .* - [E=jsonp_request:1]
Header set X-Content-Type-Options "nosniff"  env=jsonp_request
Header setifempty Content-Type application/javascript env=jsonp_request
```

#### Beveiligingsbeleid voor inhoud {#content-security-policy}

Met de standaardinstellingen voor verzenders kunt u een beveiligingsbeleid voor inhoud openen, ook wel CSP genoemd. Hierdoor kan een pagina bronnen laden van alle domeinen waarop het standaardbeleid van de browsersandbox van toepassing is.

Het is wenselijk om te beperken waar de middelen van kunnen worden geladen om ladingscode in de motor te vermijden javascript van onbetrouwbare of niet geverifieerde buitenlandse servers.

CSP staat voor het verfijnen van beleid toe. In een complexe toepassing moeten CSP-headers echter zorgvuldig worden ontwikkeld, omdat beleid dat te restrictief is, onderdelen van de gebruikersinterface kan doorbreken.

>[!NOTE]
>
>Zie voor meer informatie over hoe dit werkt de [OWASP-pagina over beveiligingsbeleid voor inhoud](https://www.owasp.org/index.php/Content_Security_Policy).

### Grootte wijzigen {#sizing}

Zie voor meer informatie over het instellen van de grootte de [Richtlijnen voor hardwareaanpassing](/help/managing/hardware-sizing-guidelines.md).

### Optimalisatie van MongoDB-prestaties {#mongodb-performance-optimization}

Voor algemene informatie over de prestaties van MongoDB raadpleegt u [De prestaties van MongoDB analyseren](https://docs.mongodb.org/manual/administration/analyzing-mongodb-performance/).

## Bekende beperkingen {#known-limitations}

### Gelijktijdige installaties {#concurrent-installations}

Hoewel het gelijktijdige gebruik van meerdere AEM instanties met één database wordt ondersteund door MongoMK, zijn gelijktijdige installaties niet mogelijk.

Als u dit wilt omzeilen, moet u eerst de installatie uitvoeren met één lid en de andere leden toevoegen nadat de eerste installatie is voltooid.

### Lengte paginanaam {#page-name-length}

Als AEM wordt uitgevoerd op een implementatie van de persistentiebeheersoftware van MongoMK, [paginanamen mogen maximaal 150 tekens bevatten.](/help/sites-authoring/managing-pages.md)

>[!NOTE]
>
>[Raadpleeg de documentatie van MongoDB](https://docs.mongodb.com/manual/reference/limits/) om uzelf ook vertrouwd te maken met de bekende beperkingen en drempels van MongoDB zelf.
