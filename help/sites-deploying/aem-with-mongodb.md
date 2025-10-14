---
title: Adobe Experience Manager met MongoDB
description: Meer informatie over de taken en overwegingen die nodig zijn voor een geslaagde implementatie van Adobe Experience Manager met MongoDB.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: 70a39462-8584-4c76-a097-05ee436247b7
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 8f638eb384bdca59fb6f4f8990643e64f34622ce
workflow-type: tm+mt
source-wordcount: '6216'
ht-degree: 0%

---

# Adobe Experience Manager met MongoDB{#aem-with-mongodb}

Dit artikel heeft tot doel de kennis over de taken en overwegingen te verbeteren die nodig zijn om AEM (Adobe Experience Manager) met MongoDB succesvol te implementeren.

Voor meer op plaatsing betrekking hebbende informatie, raadpleeg [&#x200B; het Opstellen en het Onderhouden &#x200B;](/help/sites-deploying/deploy.md) sectie van de documentatie.

## Wanneer gebruikt u MongoDB met AEM {#when-to-use-mongodb-with-aem}

MongoDB wordt doorgaans gebruikt voor ondersteuning van implementaties van AEM-auteurs waarbij aan een van de volgende criteria wordt voldaan:

* Meer dan 1000 unieke gebruikers per dag;
* meer dan 100 gelijktijdige gebruikers;
* Hoge volumes paginabewerkingen;
* Grote rollouts of activeringen.

Bovenstaande criteria gelden alleen voor de auteur-instanties en niet voor publicatieinstanties die allemaal op TarMK moeten zijn gebaseerd. Het aantal gebruikers verwijst naar geverifieerde gebruikers, omdat instanties van auteurs geen ongeautoriseerde toegang toestaan.

Als niet aan de criteria wordt voldaan, dan wordt een actieve TarMK/standby plaatsing geadviseerd om beschikbaarheid te richten. Over het algemeen moet MongoDB worden overwogen in situaties waarin de schaalvereisten groter zijn dan wat met één hardwareonderdeel kan worden bereikt.

>[!NOTE]
>
>De extra informatie bij het rangschikken van auteursinstanties en de definitie van gezamenlijke gebruikers kan in de [&#x200B; Hardware worden gevonden rangschikt Richtlijnen &#x200B;](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel).

### Minimale MongoDB-implementatie voor AEM {#minimal-mongodb-deployment-for-aem}

Hieronder vindt u een minimale implementatie voor AEM op MongoDB. Voor eenvoud, zijn de SSL beëindiging en de componenten van de Volmacht van HTTP algemeen gemaakt. Het bestaat uit één MongoDB-replicaset, met één primaire en twee secondejaren.

![&#x200B; chlimage_1-4 &#x200B;](assets/chlimage_1-4.png)

Voor een minimale implementatie zijn drie `mongod` -instanties vereist die zijn geconfigureerd als een replicaset. Eén instantie wordt primair geselecteerd en de andere instanties zijn secundaire instanties, waarbij de selectie wordt beheerd door `mongod` . Aan elke instantie is een lokale schijf gekoppeld. De cluster kan de belasting dus ondersteunen, een minimale doorvoer van 12 MB per seconde met meer dan 3000 I/O-bewerkingen per seconde (IOPS) wordt aanbevolen.

De AEM-auteurs hebben verbinding met de `mongod` -instanties, waarbij elke AEM-auteur verbinding maakt met alle drie `mongod` -instanties. Schrijven worden naar de primaire pagina verzonden en kunnen vanuit elk van de gevallen worden gelezen. Het verkeer wordt verdeeld gebaseerd op lading door een Dispatcher aan om het even welke actieve de auteur van AEM instanties. De Oak-gegevensopslag is een `FileDataStore` -controle en MongoDB-controle wordt door MMS of MongoDB Ops Manager geboden, afhankelijk van de locatie van de implementatie. Het niveau van het werkende systeem en logboekcontrole wordt verstrekt door derdeoplossingen zoals Splunk of Ganglia.

In deze implementatie zijn alle componenten vereist voor een geslaagde implementatie. Ontbrekende componenten laten de implementatie niet-functioneel.

### Besturingssystemen {#operating-systems}

Voor een lijst van gesteunde werkende systemen voor AEM 6, zie de [&#x200B; pagina van Technische Vereisten &#x200B;](/help/sites-deploying/technical-requirements.md).

### Omgevingen {#environments}

Gevirtualiseerde omgevingen worden ondersteund op voorwaarde dat er goede communicatie is tussen de verschillende technische teams die het project uitvoeren. Tot deze ondersteuning behoren het team dat AEM uitvoert, het team dat eigenaar is van het besturingssysteem en het team dat de gevirtualiseerde infrastructuur beheert.

Er zijn specifieke vereisten voor de I/O-capaciteit van de MongoDB-instanties die moeten worden beheerd door het team dat de gevirtualiseerde omgeving beheert. Als het project een cloudimplementatie gebruikt, zoals Amazon Web Services, moeten instanties zijn voorzien van voldoende I/O-capaciteit en consistentie om de MongoDB-instanties te ondersteunen. Anders functioneren de MongoDB-processen en de Oak-opslagplaats onbetrouwbaar en onregelmatig.

In gevirtualiseerde omgevingen heeft MongoDB specifieke I/O- en VM-configuraties nodig om ervoor te zorgen dat de opslagengine van MongoDB niet wordt belemmerd door VMWare-beleid voor brontoewijzing. Een geslaagde implementatie zorgt ervoor dat er geen barrières zijn tussen de verschillende teams en iedereen is aangemeld om de vereiste prestaties te leveren.

## Overwegingen voor hardware {#hardware-considerations}

### Opslag {#storage}

Om de lees- en schrijfdoorvoer te behalen voor de beste prestaties zonder de behoefte aan premature horizontale schaling, vereist MongoDB doorgaans SSD-opslag of -opslag met prestaties die gelijk zijn aan SSD.

### RAM {#ram}

Voor MongoDB-versies 2.6 en 3.0 die de MMAP-opslagengine gebruiken, is het vereist dat de werkset van de database en de bijbehorende indexen in het RAM passen.

Onvoldoende RAM leidt tot een aanzienlijke prestatievermindering. De grootte van de werkset en van de database is sterk afhankelijk van de toepassing. Hoewel sommige schattingen kunnen worden gemaakt, is de betrouwbaarste manier om te bepalen hoeveel RAM nodig is, het bouwen van de AEM-toepassing en het testen van de belasting.

Ter ondersteuning van het laadtestproces kan de volgende verhouding tussen werkset en totale databasegrootte worden aangenomen:

* 1:10 voor SSD-opslag
* 1:3 voor harde-schijfopslag

Deze verhoudingen betekenen dat voor SSD-implementaties 200 GB RAM vereist is voor een database van 2 TB.

Hoewel de zelfde beperkingen op de opslag WiredTiger motor in MongoDB 3.0 van toepassing zijn, is de correlatie tussen de het werk reeks, RAM, en paginafouten niet zo sterk. WiredTiger gebruikt geheugentoewijzing niet op dezelfde manier als de MMAP-opslagengine.

>[!NOTE]
>
>Adobe raadt aan de WiredTiger-opslagengine te gebruiken voor AEM 6.1-implementaties die MongoDB 3.0 gebruiken.

### Gegevensopslag {#data-store}

Vanwege de beperkingen van de MongoDB-werkset wordt aanbevolen de gegevensopslag onafhankelijk van de MongoDB te houden. In de meeste omgevingen moet u een `FileDataStore` gebruiken met een NAS die beschikbaar is voor alle AEM-instanties. Voor situaties waarin de Amazon Web Services wordt gebruikt, is er ook een `S3 DataStore` . Als om het even welke reden, de gegevensopslag binnen MongoDB wordt gehandhaafd, zou de grootte van de datastore aan de totale gegevensbestandgrootte moeten worden toegevoegd, en de werksetberekeningen zouden geschikt worden aangepast. Deze grootte kan betekenen dat u meer RAM-geheugen moet inrichten om de prestaties te handhaven zonder paginafouten.

## Bewaking {#monitoring}

Toezicht is van essentieel belang voor een succesvolle uitvoering van het project. Met voldoende kennis van zaken is het mogelijk om AEM op MongoDB uit te voeren zonder controle. Nochtans, wordt die kennis gewoonlijk gevonden in ingenieurs die voor elke sectie van de plaatsing worden gespecialiseerd.

Bij deze gespecialiseerde kennis gaat het doorgaans om een O&amp;O-engineer die werkt aan de Apache Oak Core en een MongoDB-specialist.

Zonder controle op alle niveaus, wordt gedetailleerde kennis van de codebasis vereist om kwesties te diagnostiseren. Met toezicht en passende richtsnoeren voor de belangrijkste statistieken kunnen de implementatieteams adequaat reageren op anomalieën.

Terwijl het mogelijk is om bevel-lijn hulpmiddelen te gebruiken om een snelle momentopname van de verrichting van een cluster te krijgen, is het doen van dat in echt - tijd over vele gastheren bijna onmogelijk. Met opdrachtregelprogramma&#39;s wordt zelden meer dan een paar minuten historische informatie gegeven en is geen kruiscorrelatie mogelijk tussen verschillende typen metriek. Een korte periode van trage `mongod` synchronisatie op de achtergrond vereist een aanzienlijke handmatige inspanning om te correleren met I/O-wachttijden of buitensporige schrijfniveaus naar een gedeelde opslagbron van een ogenschijnlijk niet-aangesloten virtuele machine.

### MongoDB Cloud Manager {#mongodb-cloud-manager}

MongoDB Cloud Manager is een gratis service die wordt aangeboden door MongoDB en die controle en beheer van MongoDB-instanties mogelijk maakt. Het biedt een weergave in real-time van de prestaties en gezondheid van de MongoDB-cluster. Het beheert zowel clouds als privégehoste instanties op voorwaarde dat de instantie de Cloud Manager-controleserver kan bereiken.

Het vereist een agent die op de instantie MongoDB wordt geïnstalleerd die met de controleserver verbindt. Er zijn drie niveaus van de agent:

* Een automatiseringsagent die alles op de MongoDB-server volledig kan automatiseren,
* Een bewakingsagent die de instantie `mongod` kan controleren;
* Een back-upagent die geplande back-ups van de gegevens kan uitvoeren.

Hoewel het gebruik van Cloud Manager voor onderhoudsautomatisering van een MongoDB-cluster veel routinetaken eenvoudiger maakt, is dit niet nodig en wordt het ook niet gebruikt voor back-up. Wanneer u een Cloud Manager kiest om te controleren, is bewaking echter vereist.

Voor meer informatie betreffende MongoDB Cloud Manager, raadpleeg de [&#x200B; documentatie MongoDB &#x200B;](https://docs.cloud.mongodb.com/).

### MongoDB Ops Manager {#mongodb-ops-manager}

MongoDB Ops Manager is dezelfde software als de MongoDB Cloud Manager. Zodra geregistreerd, kan de Manager van Ops plaatselijk in een privé gegevenscentrum of op een andere laptop of Desktopmachine worden gedownload en worden geïnstalleerd. Het gebruikt een lokale gegevensbestand MongoDB om gegevens op te slaan en op de zelfde manier als Cloud Manager met de beheerde servers te communiceren. Als u veiligheidsbeleid hebt dat een controleagent verhindert, zou de Manager van Ops MongoDB moeten worden gebruikt.

### Besturingssysteem controleren {#operating-system-monitoring}

Controle op besturingssysteemniveau is vereist om een AEM MongoDB-cluster uit te voeren.

Ganglia is een goed voorbeeld van een dergelijk systeem en biedt een beeld van het bereik en de details van de vereiste informatie die verder gaat dan elementaire gezondheidsmaatstaven zoals CPU, het laadgemiddelde en vrije schijfruimte. Om problemen te diagnostiseren, is informatie op een lager niveau, zoals entropiepoolniveaus, CPU I/O-wachttijd, sockets in FIN_WAIT2-status vereist.

### Logaggregatie {#log-aggregation}

Bij een cluster met meerdere servers is centrale logboekaggregatie een vereiste voor een productiesysteem. De software zoals Splunk steunt logboeksamenvoeging en staat teams toe om de patronen van gedrag van de toepassing te analyseren zonder het moeten de logboeken manueel verzamelen.

## Controlelijsten {#checklists}

In deze sectie worden diverse stappen beschreven die u moet uitvoeren om ervoor te zorgen dat uw AEM- en MongoDB-implementaties correct zijn ingesteld voordat u uw project implementeert.

### Netwerk {#network}

1. Eerst, zorg ervoor dat alle gastheren een DNS ingang hebben
1. Alle gastheren zouden door hun DNS ingang van alle andere routable gastheren moeten oplosbaar zijn
1. Alle MongoDB-hosts zijn routeerbaar voor alle andere MongoDB-hosts in dezelfde cluster
1. MongoDB-hosts kunnen pakketten naar MongoDB Cloud Manager en de andere controleservers verzenden
1. AEM Servers kunnen pakketten naar alle MongoDB-servers leiden
1. De pakketvertraging tussen elke AEM-server en elke MongoDB-server is kleiner dan twee milliseconden, zonder pakketverlies en een standaarddistributie van 1 millisecond of minder.
1. Zorg ervoor dat er niet meer dan twee hop is tussen een AEM en een MongoDB-server
1. Er zijn niet meer dan twee hop tussen twee MongoDB-servers
1. Er zijn geen routers hoger dan OSI Niveau 3 tussen om het even welke kernservers (MongoDB of AEM of om het even welke combinatie).
1. Als trunking van VLAN of om het even welke vorm van netwerk het een tunnel graven wordt gebruikt, moet het aan de controles van de pakketlatentie voldoen.

### AEM-configuratie {#aem-configuration}

#### Knooppuntwinkelconfiguratie {#node-store-configuration}

De AEM-instanties moeten zo zijn geconfigureerd dat ze AEM met MongoMK gebruiken. De basis van de MongoMK-implementatie in AEM is de Document Node Store.

Voor meer informatie hoe te om de Opslag van de Knoop te vormen, zie [&#x200B; het Vormen de Opslag van de Knoop en de Opslag van Gegevens in AEM &#x200B;](/help/sites-deploying/data-store-config.md).

Hieronder ziet u een voorbeeld van de configuratie van de Document Node Store voor een minimale implementatie van MongoDB:

```xml
# org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config
#MongoDB server details
mongodburi=mongodb://aem:aempassword@mongodbserver1.customer.com:27000,mongodbserver2.customer.com:27000

#Name of MongoDB database to use
db=aem

#Store binaries in custom BlobStore for example, FileDataStore
customBlobStore=true

cache=2048
blobCacheSize=1024
```

Waarbij:

* `mongodburi`
De MongoDB-server waarmee AEM verbinding moet maken. Verbindingen worden gemaakt met alle bekende leden van de standaardreplicaset. Als MongoDB Cloud Manager wordt gebruikt, is de serverbeveiliging ingeschakeld. Daarom moet de verbindingstekenreeks een geschikte gebruikersnaam en wachtwoord bevatten. Niet-zakelijke versies van MongoDB ondersteunen alleen gebruikersnaam- en wachtwoordverificatie. Voor meer informatie over de syntaxis van het verbindingskoord, raadpleeg de [&#x200B; documentatie &#x200B;](https://docs.mongodb.org/manual/reference/connection-string/).

* `db`
De naam van de database. De standaardwaarde voor AEM is `aem-author` .

* `customBlobStore`
Als de plaatsing binaire getallen in het gegevensbestand opslaat, maken zij deel uit van de het werk reeks. Daarom wordt aangeraden binaire bestanden niet in MongoDB op te slaan, bij voorkeur een alternatieve datastore zoals een `FileSystem` datastore op een NAS.

* `cache`
De cachegrootte in megabytes. Deze ruimte wordt verdeeld over verschillende caches die worden gebruikt in de `DocumentNodeStore` . De standaardwaarde is 256 MB. Oak leest echter prestatievoordelen van een groter cachegeheugen.

* `blobCacheSize`
Veelgebruikte blobs kunnen door AEM in de cache worden geplaatst om te voorkomen dat ze opnieuw uit de gegevensopslag worden opgehaald. Dit heeft meer invloed op de prestaties, vooral wanneer u klodders opslaat in de MongoDB-database. Alle gegevensopslagsystemen op bestandssysteem profiteren van de schijfcache op besturingssysteemniveau.

#### Configuratie gegevensopslag {#data-store-configuration}

De gegevensopslag wordt gebruikt om bestanden op te slaan die groter zijn dan een drempel. Onder die drempel worden bestanden als eigenschappen opgeslagen in het Document Node Store. Als `MongoBlobStore` wordt gebruikt, wordt een specifieke inzameling gecreeerd in MongoDB om de vlekken op te slaan. Deze verzameling draagt bij aan de werkset van de instantie `mongod` en vereist dat `mongod` meer RAM heeft om prestatieproblemen te voorkomen. Daarom is het raadzaam `MongoBlobStore` niet te gebruiken voor productieimplementaties en het gebruik `FileDataStore` , ondersteund door een NAS die door alle AEM-instanties wordt gedeeld. Omdat de cache op besturingssysteemniveau efficiënt is voor het beheren van bestanden, moet de minimale grootte van een bestand op schijf dicht bij de blokgrootte van de schijf worden ingesteld. Dit zorgt ervoor dat het bestandssysteem efficiënt wordt gebruikt en dat veel kleine documenten niet buitensporig bijdragen aan de werkset van de instantie `mongod` .

Hier volgt een standaardconfiguratie voor gegevensopslag voor een minimale AEM-implementatie met MongoDB:

```xml
# org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config
# The minimum size of an object that should be stored in this data store.
minRecordLength=4096
path=/datastore
maxCachedBinarySize=4096
cacheSizeInMB=128
```

Waarbij:

* `minRecordLength`
Grootte in bytes. Binaire bestanden met een grootte die kleiner is dan of gelijk is aan deze grootte, worden opgeslagen in het Document Node Store. In plaats van de id van de blob op te slaan, wordt de inhoud van het binaire bestand opgeslagen. Met binaire getallen die groter zijn dan deze grootte, wordt identiteitskaart van binair getal opgeslagen als bezit van het Document in de knooppuntinzameling. En, wordt het lichaam van het binaire getal opgeslagen in `FileDataStore` op schijf. 4096 bytes is een typische blokgrootte van het dossiersysteem.

* `path`
Het pad naar de hoofdmap van de gegevensopslag. Voor een MongoMK-implementatie moet dit pad een gedeeld bestandssysteem zijn dat beschikbaar is voor alle AEM-instanties. Gewoonlijk wordt een NAS-server (Network Attached Storage) gebruikt. Voor cloudimplementaties zoals Amazon Web Services is `S3DataFileStore` ook beschikbaar.

* `cacheSizeInMB`
De totale grootte van de binaire cache in Megabytes. Deze wordt gebruikt om binaire bestanden met een cache te plaatsen die kleiner is dan de instelling `maxCacheBinarySize` .

* `maxCachedBinarySize`
De maximumgrootte in bytes van een binaire caching in het binaire geheime voorgeheugen. Als een op een bestandssysteem gebaseerde gegevensopslag wordt gebruikt, wordt het niet aanbevolen hoge waarden te gebruiken voor de cache van de gegevensopslag, aangezien de binaire bestanden al in de cache zijn opgeslagen door het besturingssysteem.

#### De queryhint uitschakelen {#disabling-the-query-hint}

U wordt aangeraden de queryhint die met alle query&#39;s wordt verzonden, uit te schakelen door de eigenschap `-Doak.mongo.disableIndexHint=true` toe te voegen wanneer u AEM start. Dit zorgt ervoor dat MongoDB de meest geschikte index berekent die op interne statistieken moet worden gebruikt.

Als de queryhint niet is uitgeschakeld, heeft het afstemmen van indexen op de prestaties van AEM geen invloed.

#### Blijvende cache inschakelen voor MongoMK {#enable-persistent-cache-for-mongomk}

Het wordt aanbevolen een permanente cacheconfiguratie in te schakelen voor MongoDB-implementaties om de snelheid te maximaliseren voor omgevingen met hoge I/O-leesprestaties. Voor meer details, zie de [&#x200B; documentatie van Jackrabbit Oak &#x200B;](https://jackrabbit.apache.org/oak/docs/nodestore/persistent-cache.html).

## Optimalisatie van MongoDB-besturingssystemen {#mongodb-operating-system-optimizations}

### Ondersteuning van besturingssystemen {#operating-system-support}

MongoDB 2.6 gebruikt een in geheugen toegewezen opslagengine die gevoelig is voor bepaalde aspecten van het systeembeheer tussen RAM en schijf. De vraag en gelezen Prestaties van de instantie MongoDB baseert zich op het vermijden of het elimineren van langzame I/O verrichtingen die vaak als paginafouten worden bedoeld. Dit zijn vooral paginafouten die van toepassing zijn op het `mongod` -proces. Let op het verschil met paginafouten op besturingssysteemniveau.

Voor snelle verrichting, zou het gegevensbestand MongoDB slechts tot gegevens moeten toegang hebben die reeds in RAM zijn. De gegevens waartoe het toegang moet krijgen, bestaan uit indexen en gegevens. Deze verzameling indexen en gegevens wordt de werkset genoemd. Als de werkset groter is dan de beschikbare RAM-geheugen, moet MongoDB die gegevens vanaf een schijf met I/O-kosten inpakken, zodat andere gegevens die al in het geheugen staan, worden verwijderd. Als de verwijdering ertoe leidt dat gegevens van schijf worden opnieuw geladen, nemen de paginafouten en de prestaties af. Wanneer de werkset dynamisch en variabel is, worden er meer paginafouten gegenereerd om bewerkingen te ondersteunen.

MongoDB wordt uitgevoerd op verschillende besturingssystemen, waaronder een groot aantal Linux®-kleuren, Windows en macOS. Zie [&#x200B; https://docs.mongodb.com/manual/installation/#supported-platforms &#x200B;](https://docs.mongodb.com/manual/installation/#supported-platforms) voor extra details. Afhankelijk van de keuze van het besturingssysteem heeft MongoDB verschillende aanbevelingen voor het niveau van het besturingssysteem. Er zijn gedocumenteerd in [&#x200B; https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration &#x200B;](https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration) en hier samengevat voor gemak.

#### Linux® {#linux}

* Schakel de transparante kleurtonen en foutopsporing uit. Zie [&#x200B; de Transparante Montages van de Pagina&#39;s van de Groot &#x200B;](https://docs.mongodb.com/manual/tutorial/transparent-huge-pages/) voor meer informatie.
* [&#x200B; pas de readahead montages &#x200B;](https://docs.mongodb.com/manual/administration/production-notes/#readahead) op de apparaten aan die uw gegevensbestanddossiers opslaan zodat u uw gebruiksgeval past.

   * Als de werkset van de MMAPv1-opslagengine groter is dan het beschikbare RAM en het toegangspatroon van het document willekeurig is, kunt u het aflezen naar 32 of 16 verkleinen. U kunt verschillende instellingen evalueren, zodat u een optimale waarde kunt vinden voor een zo groot mogelijk geheugen en een lager aantal paginafouten.
   * Voor de opslag WiredTiger motor, reeks opnieuw gelezen aan 0 ongeacht opslagmedia type (het draaien, SSD, etc.). Over het algemeen gebruikt u de aanbevolen instelling voor het aflezen van voorkeuren, tenzij tests een meetbaar, herhaalbaar en betrouwbaar voordeel opleveren bij een hogere aflezing. [&#x200B; de Professionele Steun van MongoDB &#x200B;](https://docs.mongodb.com/manual/administration/production-notes/#readahead) kan advies en begeleiding op non-zero readahead configuraties verstrekken.

* Schakel het afgestelde gereedschap uit als u RHEL 7 / CentOS 7 in een virtuele omgeving uitvoert.
* Wanneer RHEL 7/CentOS 7 in een virtuele milieu in werking wordt gesteld, roept het afgestemde hulpmiddel automatisch een prestatiesprofiel aan dat uit prestatiesproductie wordt afgeleid, die automatisch de lezingsmontages aan 4 MB plaatst. Deze instelling kan negatieve gevolgen hebben voor de prestaties.
* Gebruik de noop- of deadline schijfplanners voor SSD-stations.
* Gebruik de noop schijfplanner voor gevirtualiseerde aandrijving in gast VMs.
* Maak NUMA onbruikbaar of reeks `vm.zone_reclaim_mode` aan 0 en stel [&#x200B; mongoinstanties &#x200B;](https://docs.mongodb.com/manual/administration/production-notes/#readahead) met knoop interleave in werking. Zie: [&#x200B; MongoDB en Hardware NUMA &#x200B;](https://docs.mongodb.com/manual/administration/production-notes/#readahead) voor meer informatie.

* Pas de grenswaarden op de hardware aan, zodat deze passen bij uw gebruiksscenario. Als de veelvoudige [&#x200B; mongoon &#x200B;](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) of [&#x200B; mongo &#x200B;](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos) instanties onder de zelfde gebruiker lopen, schaal dienovereenkomstig de grenswaarden. Zie: [&#x200B; UNIX® ulimit Montages &#x200B;](https://docs.mongodb.com/manual/reference/ulimit/) voor meer informatie.

* De naam van het gebruik voor het [&#x200B; dbPath &#x200B;](https://docs.mongodb.com/manual/reference/configuration-options/#storage.dbPath) koppelingspunt.
* Configureer voldoende bestandshandgrepen (fs.file-max), de limiet voor de pid van de kernel (kernel.pid_max) en de maximale threads per proces (kernel.threads-max) voor uw implementatie. Voor grote systemen bieden de volgende waarden een goed startpunt:

   * fs.file-max waarde van 98000,
   * kernel.pid_max waarde 64000,
   * andkernel.threads-max waarde van 64000

* Zorg ervoor dat er wisselruimte is geconfigureerd op uw systeem. Raadpleeg de documentatie bij het besturingssysteem voor meer informatie over de juiste grootte.
* Zorg ervoor dat het systeem standaardTCP keylive correct wordt geplaatst. Een waarde van 300 biedt vaak betere prestaties voor replicasets en gedeelde clusters. Zie: [&#x200B; beïnvloedt keyletime van TCP de Inzet MongoDB?](https://docs.mongodb.com/manual/faq/diagnostics/#faq-keepalive) in Veelgestelde vragen voor meer informatie.

#### Windows {#windows}

* Overweeg het onbruikbaar maken NTFS &quot;laatste toegangstijd&quot;updates. Deze instelling is hetzelfde als het uitschakelen van atime op Unix-achtige systemen.

### WiredTiger {#wiredtiger}

Vanaf MongoDB 3.2 is de standaard opslagengine voor MongoDB de WiredTiger-opslagengine. Deze engine biedt enkele robuuste en schaalbare functies die het veel geschikter maken voor algemene databasewerklasten. In de volgende secties worden deze functies beschreven.

#### Documentniveau gelijktijdig {#document-level-concurrency}

WiredTiger gebruikt document-vlakke gelijktijdig controle voor schrijfverrichtingen. Hierdoor kunnen meerdere clients verschillende documenten van een verzameling tegelijk wijzigen.

Voor de meeste lees en schrijf verrichtingen, gebruikt WiredTiger optimistische gelijktijdig controle. WiredTiger gebruikt slechts intent sloten bij globale, gegevensbestand, en inzamelingsniveaus. Wanneer de opslagengine conflicten tussen twee bewerkingen detecteert, treedt er een schrijfconflict op waardoor MongoDB deze bewerking op transparante wijze opnieuw probeert. Voor sommige globale bewerkingen, meestal kortstondige bewerkingen met meerdere databases, is nog steeds een algemene vergrendeling voor de hele instantie vereist.

Voor sommige andere bewerkingen, zoals het neerzetten van een verzameling, is nog steeds een exclusieve databasevergrendeling vereist.

#### Momentopnamen en controlepunten {#snapshots-and-checkpoints}

WiredTiger gebruikt MultiVersion Concurrency Control (MVCC). Aan het begin van een verrichting, verstrekt WiredTiger een punt-in-tijd momentopname van de gegevens aan de transactie. Een momentopname stelt een verenigbare mening van de in-geheugengegevens voor.

Wanneer het schrijven aan schijf, schrijft WiredTiger alle gegevens in een momentopname aan schijf op een verenigbare manier over alle gegevensdossiers. De nu - [&#x200B; duurzame &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-durable) gegevens handelen als controlepunt in de gegevensdossiers. Het controlepunt zorgt ervoor dat de gegevensdossiers tot en met het laatste controlepunt verenigbaar zijn. Dit betekent dat controlepunten kunnen fungeren als herstelpunten.

MongoDB configureert WiredTiger om controlepunten (namelijk schrijven de momentopnamegegevens aan schijf) met intervallen van 60 seconden of 2 GB van dagboekgegevens tot stand te brengen.

Tijdens het schrijven van een nieuw controlepunt, is het vorige controlepunt nog geldig. Als zodanig, zelfs als MongoDB beëindigt of een fout ontmoet terwijl het schrijven van een nieuw controlepunt, bij nieuw begin, kan MongoDB van het laatste geldige controlepunt terugkrijgen.

Het nieuwe controlepunt wordt toegankelijk en permanent wanneer de de meta-gegevenslijst van WiredTiger automatisch wordt bijgewerkt om naar het nieuwe controlepunt te verwijzen. Zodra het nieuwe controlepunt toegankelijk is, bevrijdt WiredTiger pagina&#39;s van de oude controlepunten.

Gebruikend WiredTiger, zelfs zonder [&#x200B; het journaling &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-durable), kan MongoDB van het laatste controlepunt terugkrijgen; nochtans, om veranderingen terug te krijgen die na het laatste controlepunt worden aangebracht, looppas met [&#x200B; het journaling &#x200B;](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Dagboek {#journal}

WiredTiger gebruikt een schrijven-vooruit combinatie van de transactieopening van een sessie met [&#x200B; controlepunten &#x200B;](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-checkpoints) om gegevensduurzaamheid te verzekeren.

Het journaal WiredTiger zet alle gegevenswijzigingen tussen controlepunten voort. Als MongoDB tussen controlepunten weggaat, gebruikt het dagboek om alle gegevens opnieuw te spelen die sinds het laatste controlepunt worden gewijzigd. Voor informatie over de frequentie waarmee MongoDB de dagboekgegevens aan schijf schrijft, zie [&#x200B; het Journaling Proces &#x200B;](https://docs.mongodb.com/manual/core/journaling/#journal-process).

Het dagboek WiredTiger wordt samengeperst gebruikend de [&#x200B; snappy &#x200B;](https://docs.mongodb.com/manual/core/journaling/#journal-process) compressiebibliotheek. Om een afwisselend compressiealgoritme of geen compressie te specificeren, gebruik [&#x200B; storage.wiredTiger.engineConfig.JournalCompressor &#x200B;](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.journalCompressor) het plaatsen.

Zie [&#x200B; het Journaling met WiredTiger &#x200B;](https://docs.mongodb.com/manual/core/journaling/#journaling-wiredtiger).

>[!NOTE]
>
>De minimumgrootte van het logboekverslag voor WiredTiger is 128 bytes. Als een logboekverslag 128 bytes of kleiner is, comprimeert WiredTiger niet dat verslag.
>
>U kunt het journaling onbruikbaar maken door [&#x200B; storage.journal.enabled &#x200B;](https://docs.mongodb.com/manual/reference/configuration-options/#storage.journal.enabled) aan vals te plaatsen, die de overheadkosten van het handhaven van het dagboek kan verminderen.
>
>Voor [&#x200B; standalone &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-standalone) instanties, die niet het dagboek gebruiken betekent dat u sommige gegevenswijzigingen verliest wanneer MongoDB onverwacht tussen controlepunten weggaat. Voor leden van [&#x200B; replicasets &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-replica-set), kan het replicatieproces voldoende duurzaamheidsgaranties verstrekken.

#### Compressie {#compression}

Met WiredTiger biedt MongoDB ondersteuning voor compressie voor alle verzamelingen en indexen. Compressie minimaliseert opslaggebruik ten koste van extra CPU.

Door gebrek, gebruikt WiredTiger blokcompressie met de [&#x200B; snappy &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-snappy) compressiebibliotheek voor alle inzamelingen en [&#x200B; prefixcompressie &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) voor alle indexen.

Voor inzamelingen, blokcompressie met [&#x200B; zlib &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) is ook beschikbaar. Om een afwisselend compressiealgoritme of geen compressie te specificeren, gebruik [&#x200B; storage.wiredTiger.collectionConfig.blockCompressor &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) plaatsen.

Voor indexen, om [&#x200B; prefixcompressie &#x200B;](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) onbruikbaar te maken, gebruik [&#x200B; storage.wiredTiger.indexConfig.prefixCompression &#x200B;](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.indexConfig.prefixCompression) het plaatsen.

De montages van de compressie zijn ook configureerbaar op een per-inzameling en per-indexbasis tijdens inzameling en indexverwezenlijking. Zie [&#x200B; de Opties van de Motor van de Opslag specificeren &#x200B;](https://docs.mongodb.com/manual/reference/method/db.createCollection/#create-collection-storage-engine-options) en [&#x200B; db.collection.createIndex () storageEngine &#x200B;](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/#createindex-options) optie.

Voor de meeste werklasten zijn de standaardinstellingen voor compressie een goede balans tussen de efficiëntie van de opslag en de verwerkingsvereisten.

Het tijdschrift WiredTiger wordt ook door gebrek samengeperst. Voor informatie over dagboekcompressie, zie [&#x200B; Dagboek &#x200B;](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Geheugengebruik {#memory-use}

Met WiredTiger gebruikt MongoDB zowel de interne cache van WiredTiger als de cache van het bestandssysteem.

Beginnend in 3.4, gebruikt het interne geheime voorgeheugen WiredTiger, door gebrek, het grootste van of:

* 50% van RAM min 1 GB, of
* 256 MB

Standaard gebruikt WiredTiger de compressie van het Snapy-blok voor alle verzamelingen en de compressie van het voorvoegsel voor alle indexen. De standaardwaarden voor compressie kunnen globaal worden geconfigureerd en kunnen ook per verzameling en per index worden ingesteld tijdens het maken van verzamelingen en indexen.

De verschillende vertegenwoordiging wordt gebruikt voor gegevens in het interne geheime voorgeheugen WiredTiger tegenover in het on-disk formaat:

* De gegevens in de bestandssysteemcache zijn gelijk aan de schijfindeling, inclusief de voordelen van compressie voor gegevensbestanden. De cache van het bestandssysteem wordt door het besturingssysteem gebruikt om de I/O van de schijf te verminderen.

De indexen die in het interne geheime voorgeheugen WiredTiger worden geladen hebben een verschillende gegevensvertegenwoordiging aan het formaat op schijf, maar kunnen nog voordeel van de compressie van de indexprefix nemen om het gebruik van RAM te verminderen.

Met compressie van indexvoorvoegsel worden algemene voorvoegsels van geïndexeerde velden verwijderd.

De gegevens van de inzameling in het interne geheime voorgeheugen WiredTiger zijn niet samengeperst en gebruiken een verschillende vertegenwoordiging van het formaat op schijf. Blokcompressie kan aanzienlijke opslagbesparingen op de schijf opleveren, maar gegevens moeten niet gecomprimeerd zijn om door de server te worden gemanipuleerd.

Via het filesystem geheime voorgeheugen, gebruikt MongoDB automatisch al vrij geheugen dat niet door het geheime voorgeheugen WiredTiger of door andere processen wordt gebruikt.

Om de grootte van het interne geheime voorgeheugen WiredTiger aan te passen, zie [&#x200B; storage.wiredTiger.engineConfig.cacheSizeGB &#x200B;](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.cacheSizeGB) en [&#x200B; - wiredTigerCacheSizeGB &#x200B;](https://docs.mongodb.com/manual/reference/program/mongod/#cmdoption-wiredtigercachesizegb). Vermijd het verhogen van de interne cachegrootte WiredTiger boven zijn standaardwaarde.

### NUMA {#numa}

Met NUMA (Non-Uniform Memory Access) kan een kernel bepalen hoe geheugen wordt toegewezen aan de processorkernen. Hoewel dit proces probeert om geheugentoegang voor kernen sneller te maken die ervoor zorgen dat zij tot de vereiste gegevens kunnen toegang hebben, mengt NUMA zich in MMAP die extra latentie introduceert aangezien leest niet kan worden voorspeld. Het gevolg is dat NUMA moet worden uitgeschakeld voor het `mongod` -proces op alle besturingssystemen die hiervoor geschikt zijn.

In wezen wordt het geheugen van een NUMA-architectuur aangesloten op de CPU en worden de CPU&#39;s aangesloten op een bus. In een SMP of een architectuur UMA, wordt het geheugen verbonden met de bus en door cpu&#39;s gedeeld. Wanneer een draad geheugen op NUMA CPU toewijst, wijst het volgens een beleid toe. Standaard wordt geheugen toegewezen dat is gekoppeld aan de lokale CPU van de verbinding, tenzij er geen vrije verbinding is. Op dat moment wordt geheugen van een gratis CPU tegen hogere kosten gebruikt. Nadat het geheugen is toegewezen, wordt het niet verplaatst tussen CPU&#39;s. De toewijzing wordt uitgevoerd door een beleid dat van de ouderdraad wordt geërft, die uiteindelijk de draad is die het proces begon.

In veel databases die de computer zien als een multicore, uniforme geheugenarchitectuur, leidt dit scenario ertoe dat de eerste CPU volledig wordt en de tweede CPU-opvulling later. Het is vooral waar als een centrale draad voor het toewijzen van geheugenbuffers verantwoordelijk is. De oplossing is het beleid van NUMA van de belangrijkste draad te veranderen die wordt gebruikt om het `mongod` proces te beginnen door het volgende bevel in werking te stellen:

```shell
numactl --interleaved=all <mongod> -f config
```

Dit beleid wijst geheugen in een ronde weg over alle knopen van CPU toe die een gelijke verdeling over alle knopen verzekeren. Er wordt geen optimale toegang tot het geheugen gegenereerd, zoals bij systemen met meerdere CPU-hardware. Ongeveer de helft van de geheugenbewerkingen verloopt langzamer en op de bus, maar `mongod` is niet zodanig geschreven dat NUMA optimaal kan worden benut. Het is dus een redelijk compromis.

### NUMA-problemen {#numa-issues}

Als het `mongod` proces van een plaats buiten de `/etc/init.d` omslag is begonnen, is het waarschijnlijk dat het niet met het correcte beleid NUMA is begonnen. Afhankelijk van wat het standaardbeleid is, kunnen zich problemen voordoen. De reden hiervoor is dat de verschillende Linux® Package Manager-installatieprogramma&#39;s voor MongoDB ook een service met configuratiebestanden in `/etc/init.d` installeren die de hierboven beschreven stap uitvoeren. Als u MongoDB rechtstreeks vanuit een archief ( `.tar.gz` ) installeert en uitvoert, moet u het bestand handmatig onder het `numactl` -proces uitvoeren.

>[!NOTE]
>
>Voor meer informatie over het beschikbare beleid van NUMA, raadpleeg de [&#x200B; numerieke documentatie &#x200B;](https://linux.die.net/man/8/numactl).

Het MongoDB-proces gedraagt zich anders in het kader van verschillende toewijzingsbeleid:

```

```

* `-membind=<nodes>`
Alleen toewijzen op de vermelde knooppunten. Mongod wijst geen geheugen toe op vermelde knooppunten en gebruikt mogelijk niet al het beschikbare geheugen.

* `-cpunodebind=<nodes>`
Alleen op de knooppunten uitvoeren. Mongod wordt alleen uitgevoerd op de opgegeven knooppunten en gebruikt alleen geheugen dat beschikbaar is op die knooppunten.

* `-physcpubind=<nodes>`
Alleen uitvoeren op vermelde CPU&#39;s (cores). Mongod voert alleen de CPU&#39;s uit die worden vermeld en gebruikt alleen het geheugen dat beschikbaar is voor die CPU&#39;s.

* `--localalloc`
Wijs altijd geheugen op de huidige knoop toe, maar gebruik alle knopen de draadlooppas. Als één draad een toewijzing uitvoert, dan slechts wordt het geheugen beschikbaar aan die CPU gebruikt.

* `--preferred=<node>`
Geeft de voorkeur aan toewijzing aan een knooppunt, maar valt terug naar andere knooppunten als het voorkeurknooppunt vol is. U kunt een relatieve notatie gebruiken voor het definiëren van een knooppunt. Ook, lopen de draden op alle knopen.

Sommige beleidsregels kunnen ertoe leiden dat minder dan alle beschikbare RAM-geheugen wordt toegewezen aan het `mongod` -proces. In tegenstelling tot MySQL vermijdt MongoDB actief paginering op besturingssysteemniveau, waardoor het `mongod` -proces mogelijk minder geheugen krijgt dat beschikbaar lijkt.

#### Wisselen {#swapping}

Wegens de geheugenintensieve aard van gegevensbestanden, moet de uitwisseling van het niveau van het werkende systeem worden onbruikbaar gemaakt. Met het MongoDB-proces vermijdt u verwisselingen per ontwerp.

#### Externe bestandssystemen {#remote-filesystems}

Externe bestandssystemen, zoals NFS, worden niet aanbevolen voor interne gegevensbestanden van MongoDB (de bestanden van de modelprocesdatabase), omdat deze te veel latentie introduceren. Let op het verschil met het gedeelde bestandssysteem dat vereist is voor de opslag van Oak Blob&#39;s (FileDataStore), waarbij NFS wordt aanbevolen.

#### Vooruit lezen {#read-ahead}

Tune Read forward zodat wanneer een pagina binnen gebruikend een willekeurig gelezen wordt gepagineerd, de onnodige blokken niet van de schijf worden gelezen. Dergelijke resultaten betekenen een onnodig gebruik van I/O-bandbreedte.

### Linux®-vereisten {#linux-requirements}

#### Minimale kernelversies {#minimum-kernel-versions}

* **2.6.23** voor `ext4` filesystems

* **2.6.25** voor `xfs` filesystems

#### Aanbevolen instellingen voor databaseschijven {#recommended-settings-for-database-disks}

**draai van atime**

Het wordt aanbevolen `atime` uit te schakelen voor de schijven die de databases bevatten.

**plaats de NOOP schijfplanner**

Ga als volgt te werk:

Eerst, controlerend de I/O planner die door het volgende bevel in werking te stellen wordt geplaatst:

```shell
cat /sys/block/sdg/queue/scheduler
```

Als de reactie `noop` is, hoeft u niets meer te doen.

Als NOOP niet de I/O planner is die opstelling is, kunt u het veranderen door te lopen:

```shell
echo noop > /sys/block/sdg/queue/scheduler
```

**pas gelezen vooruit waarde** aan

Het wordt aanbevolen de waarde 32 te gebruiken voor de schijven waarop MongoDB-databases worden uitgevoerd. Deze waarde bedraagt 16 kB. U kunt dit als volgt instellen:

```shell
sudo blockdev --setra <value> <device>
```

#### NTP inschakelen {#enable-ntp}

Zorg ervoor u NTP hebt geïnstalleerd en lopend op de machine die de gegevensbestanden MongoDB ontvangt. U kunt de toepassing bijvoorbeeld installeren met Yum Package Manager op een CentOS-computer:

```shell
sudo yum install ntp
```

Nadat het NTP daemon is geïnstalleerd en met succes is begonnen, kunt u het driftdossier voor de tijdcompensatie van uw server controleren.

#### Transparante grote pagina&#39;s uitschakelen {#disable-transparent-huge-pages}

Red Hat® Linux® gebruikt een algoritme voor geheugenbeheer met de naam Transparent Huge Pages (THP). Het wordt aanbevolen dit uit te schakelen als u het besturingssysteem gebruikt voor databasewerklasten.

U kunt deze uitschakelen door de onderstaande procedure te volgen:

1. Open het bestand `/etc/grub.conf` in de teksteditor van uw keuze.
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
>Voor meer informatie over Transparante Grote Pagina&#39;s, raadpleeg het volgende artikel van het Red Hat® Klantenportaal: [&#x200B; gebruiken, controleren, en onbruikbaar maken transparante gezoempagina&#39;s in de Onderneming Linux 6, 7 en 8 van Red Hat?](https://access.redhat.com/solutions/46111).

#### NUMA uitschakelen {#disable-numa}

In de meeste installaties waar NUMA is ingeschakeld, schakelt de MongoDB-daemon deze automatisch uit als deze als service wordt uitgevoerd vanuit de map `/etc/init.d` .

Als dit niet het geval is, kunt u NUMA op een per procesniveau onbruikbaar maken. Voer de volgende opdrachten uit om het uit te schakelen:

```shell
numactl --interleave=all <path_to_process>
```

Waar `<path_to_process>` het pad naar het monnikeproces is.

Schakel vervolgens streekophaling uit door:

```shell
echo 0 > /proc/sys/vm/zone_reclaim_mode
```

#### Kneep de instellingen voor de limiet voor het mondige proces {#tweak-the-ulimit-settings-for-the-mongod-process}

Met Linux® kunt u de toewijzing van bronnen configureerbaar maken via de opdracht `ulimit` . Deze configuratie kan op een gebruiker of op een per procesbasis worden gedaan.

Het wordt geadviseerd dat u grens voor het mongoproces volgens [&#x200B; MongoDB geadviseerde onbeperkt Montages &#x200B;](https://docs.mongodb.org/manual/reference/ulimit/#recommended-ulimit-settings) vormt.

#### I/O-prestaties van MongoDB testen {#test-mongodb-i-o-performance}

MongoDB biedt een hulpprogramma met de naam `mongoperf` dat is ontworpen om I/O-prestaties te testen. U wordt aangeraden dit te gebruiken om de prestaties te testen van al uw MongoDB-instanties waaruit uw infrastructuur bestaat.

Voor informatie over hoe te om `mongoperf` te gebruiken, bekijk de [&#x200B; documentatie MongoDB &#x200B;](https://docs.mongodb.org/manual/reference/program/mongoperf/).

>[!NOTE]
>
>`mongoperf` is een indicator van de prestaties van MongoDB op het platform dat het in werking wordt gesteld. Bijgevolg mogen de resultaten niet als definitief worden beschouwd voor de prestaties van een productiesysteem.
>
>Voor nauwkeurigere prestatiesresultaten kunt u complementaire tests uitvoeren met het `fio` Linux® hulpmiddel.

**Test leest prestaties op de virtuele machines die omhoog uw plaatsing** maken

Nadat u het hulpmiddel hebt geïnstalleerd, schakelaar aan de MongoDB gegevensbestandfolder om de tests in werking te stellen. Dan, begin de eerste test door `mongoperf` met deze configuratie in werking te stellen:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true}" | mongoperf
```

De gewenste uitvoer zou tot twee gigabytes per seconde (2 GB/s) en 500.000 IOPS moeten bereiken die bij 32 draden voor alle instanties MongoDB lopen.

Voer een tweede test uit, dit keer met gebruik van in geheugen toegewezen bestanden, door de parameter `mmf:true` in te stellen:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true,mmf:true}" | mongoperf
```

De uitvoer van de tweede test moet aanzienlijk hoger zijn dan die van de eerste, wat de prestaties van de geheugenoverdracht aangeeft.

>[!NOTE]
>
>Controleer bij het uitvoeren van de tests de I/O-gebruiksstatistieken voor de virtuele machines in kwestie in uw besturingssysteem. Als ze waarden aangeven die lager zijn dan 100 procent voor I/O lezen, kan er een probleem zijn met uw virtuele machine.

**Test schrijven prestaties van de primaire instantie MongoDB**

Controleer vervolgens de I/O-schrijfprestaties van de primaire MongoDB-instantie door `mongoperf` uit te voeren vanuit de MongoDB-databasemap met dezelfde instellingen:

```shell
echo "{nThreads:32,fileSizeMB:1000,w:true}" | mongoperf
```

De gewenste output zou 12 megabytes per seconde moeten zijn en rond 3000 IOPS, met weinig variatie tussen het aantal draden bereiken.

## Stappen voor virtuele omgevingen {#steps-for-virtualised-environments}

### VMWare {#vmware}

Als u WMWare ESX gebruikt om uw gevirtualiseerde milieu&#39;s te beheren en op te stellen, zorg ervoor u de volgende montages van de ESX console uitvoert om verrichting MongoDB aan te passen:

1. Geheugenballon uitschakelen
1. Het geheugen vooraf toewijzen en reserveren voor de virtuele machines die de MongoDB-databases hosten
1. Gebruik Storage I/O Control om voldoende I/O toe te wijzen aan het `mongod` -proces.
1. Garandeer de middelen van CPU van de machines die MongoDB ontvangen door [&#x200B; Reservering van CPU &#x200B;](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.hostclient.doc/GUID-6C9023B2-3A8F-48EB-8A36-44E3D14958F6.html?hWord=N4IghgNiBc4RB7AxmALgUwAQGEAKBVTAJ3QGcEBXIpMkAXyA) te plaatsen

1. Overweeg om ParaVirtual I/O-stuurprogramma&#39;s te gebruiken. <!-- URL is a 404 See [knowledgebase article](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1010398).-->

### Amazon Web Services {#amazon-web-services}

Voor documentatie op hoe te opstelling MongoDB met Amazon Web Services, controleer het [&#x200B; vormt de 1&rbrace; artikel van de Integratie van AWS op de website MongoDB.](https://www.mongodb.com/docs/cloud-manager/tutorial/configure-aws-integration/)

## MongoDB beveiligen voor implementatie {#securing-mongodb-before-deployment}

Zie deze post op [&#x200B; veilig plaatsend MongoDB &#x200B;](https://blogs.adobe.com/security/2015/07/securely-deploying-mongodb-3-0.html) voor advies over hoe te om de configuratie van uw gegevensbestanden vóór plaatsing te beveiligen.

## Dispatcher {#dispatcher}

### Het besturingssysteem kiezen voor de Dispatcher {#choosing-the-operating-system-for-the-dispatcher}

Om uw plaatsing goed te dienen MongoDB, het werkende systeem dat de gastheren Dispatcher **Apache httpd** **versie 2.4 of hoger moeten in werking stellen.**

Ook, zorg ervoor dat alle bibliotheken die in uw bouwstijl worden gebruikt bijgewerkt zijn om veiligheidsimplicaties te minimaliseren.

### Dispatcher-configuratie {#dispatcher-configuration}

Een standaard Dispatcher configuratie dient tussen de tien en twintig keer zo veel als de vereiste doorvoer van één AEM-instantie.

Omdat de Dispatcher geen status heeft, kan deze eenvoudig horizontaal worden geschaald. In sommige plaatsingen, moeten de auteurs van de toegang tot van bepaalde middelen worden beperkt. U wordt aangeraden een Dispatcher met de auteur-instanties te gebruiken.

Als u AEM uitvoert zonder Dispatcher, moet SSL worden afgesloten en moet de taakverdeling door een andere toepassing worden uitgevoerd. Dit is vereist omdat sessies affiniteit moeten hebben met de AEM-instantie waarop ze zijn gemaakt, een concept dat sticky connections wordt genoemd. De reden hiervoor is dat updates van de inhoud minimale vertraging vertonen.

Controleer de [&#x200B; documentatie van Dispatcher &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-dispatcher/using/dispatcher) voor meer informatie over hoe te om het te vormen.

### Aanvullende configuratie {#additional-configuration}

#### Vaste verbindingen {#sticky-connections}

Vaste verbindingen zorgen ervoor dat gepersonaliseerde pagina&#39;s en sessiegegevens voor één gebruiker allemaal op dezelfde instantie van AEM zijn samengesteld. Dit gegeven wordt opgeslagen op de instantie, zodat de verdere verzoeken van de zelfde gebruiker aan de zelfde instantie terugkeren.

Het wordt aanbevolen dat kleverige verbindingen zijn ingeschakeld voor alle binnenlagen die aanvragen naar de AEM-instanties routeren, waardoor latere verzoeken om hetzelfde AEM-exemplaar te bereiken worden aangemoedigd. Zo minimaliseert u de latentie die anders opvalt wanneer de inhoud tussen instanties wordt bijgewerkt.

#### Lange vervaldatum {#long-expires}

Standaard heeft inhoud die vanuit een AEM Dispatcher wordt verzonden, Laatst gewijzigd en Etag-kopteksten, zonder aanduiding van de vervaldatum van de inhoud. Deze stroom zorgt ervoor dat de gebruikersinterface altijd de recentste versie van het middel krijgt. Het betekent ook dat de browser een GET-bewerking uitvoert om te zien of de resource is gewijzigd. Dit kan leiden tot meerdere aanvragen waarop het HTTP-antwoord 304 (Niet gewijzigd) is, afhankelijk van het laden van de pagina. Voor middelen die niet verlopen, het plaatsen van een kopbal Verloopt en het verwijderen van de laatste-Gewijzigde en kopballen ETag veroorzaken de inhoud om in het voorgeheugen onder te brengen. En, worden geen verdere updateverzoeken gemaakt tot de datum in de kopbal van Verlopen wordt voldaan.

Nochtans, betekent het gebruiken van deze methode dat er geen redelijke manier is om het middel te veroorzaken om in browser te verlopen alvorens de kopbal verloopt. Om deze workflow te beperken, kan de HTMLClientLibraryManager worden geconfigureerd om onveranderlijke URL&#39;s voor clientbibliotheken te gebruiken.

Deze URL&#39;s worden gegarandeerd niet gewijzigd. Wanneer de hoofdtekst van de bron in de URL verandert, worden de wijzigingen doorgevoerd in de URL die ervoor zorgt dat de browser de juiste versie van de bron opvraagt.

De standaardconfiguratie voegt een selecteur aan HtmlClientLibraryManager toe. Als kiezer wordt de bron in het cachegeheugen opgeslagen in de Dispatcher met de kiezer intact. Deze kiezer kan ook worden gebruikt om het juiste vervalgedrag te garanderen. De standaardkiezer volgt het patroon `lc-.*?-lc` . De volgende Apache httpd-configuratierichtlijnen zorgen ervoor dat alle aanvragen die overeenkomen met dat patroon, een geschikte vervaltijd krijgen.

```xml
Header set Expires "Tue, 20 Jan 2037 04:20:42 GMT" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header set Cache-Control "public, no-transform, max-age=267840000" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset ETag "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Last-Modified "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Pragma "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
```

#### Geen flauw {#no-sniff}

Wanneer inhoud zonder inhoudstype wordt verzonden, proberen veel browsers het type inhoud te raden door de eerste paar bytes van de inhoud te lezen. Deze methode wordt &#39;snuiven&#39; genoemd. Door te niveren ontstaat een kwetsbaarheid voor beveiliging, omdat gebruikers die naar de opslagplaats kunnen schrijven, schadelijke inhoud zonder inhoudstype kunnen uploaden.

Daarom is het raadzaam een header `no-sniff` toe te voegen aan bronnen die door de Dispatcher worden aangeleverd. De Dispatcher slaat echter geen headers in de cache op. Als zodanig betekent dit dat voor inhoud die vanuit het lokale bestandssysteem wordt aangeboden, het inhoudstype wordt bepaald door de extensie in plaats van de oorspronkelijke header van het inhoudstype van de AEM-server van oorsprong.

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

De standaard Dispatcher-instellingen staan een open Content Security Policy toe, ook wel CSP genoemd. Met deze instellingen kan een pagina bronnen laden van alle domeinen waarvoor het standaardbeleid van de browsersandbox geldt.

Het is wenselijk om te beperken waar de middelen van kunnen worden geladen om het laden van code in de motor van JavaScript van onbetrouwbare of niet geverifieerde buitenlandse servers te vermijden.

CSP staat voor het verfijnen van beleid toe. In een complexe toepassing, echter, moeten de kopballen CSP met zorg worden ontwikkeld aangezien het beleid dat te restrictief is delen van het gebruikersinterface kan breken.

>[!NOTE]
>
>Voor meer informatie over hoe dit werk, zie de [&#x200B; Pagina van OWASP over het Beleid van de Veiligheid van de Inhoud &#x200B;](https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html).

### Grootte {#sizing}

Voor meer informatie bij het rangschikken van, zie de [&#x200B; Hardware die Richtlijnen rangschikt &#x200B;](/help/managing/hardware-sizing-guidelines.md).

### Optimalisatie van MongoDB-prestaties {#mongodb-performance-optimization}

Voor generische informatie over prestaties MongoDB, zie [&#x200B; Analyserend Prestaties MongoDB &#x200B;](https://docs.mongodb.org/manual/administration/analyzing-mongodb-performance/).

## Bekende beperkingen {#known-limitations}

### Gelijktijdige installaties {#concurrent-installations}

Hoewel het gelijktijdige gebruik van meerdere AEM-instanties met één database wordt ondersteund door MongoMK, worden gelijktijdige installaties niet ondersteund.

Om dit probleem te verhelpen, dient u de installatie eerst uit te voeren met één lid en de andere leden toe te voegen nadat de eerste installatie is voltooid.

### Lengte paginanaam {#page-name-length}

Als AEM op een persistentiebeheerplaatsing MongoMK loopt, [&#x200B; paginanamen zijn beperkt tot 150 karakters.](/help/sites-authoring/managing-pages.md)

>[!NOTE]
>
>Zie de [&#x200B; documentatie MongoDB &#x200B;](https://docs.mongodb.com/manual/reference/limits/) zodat kunt u met de bekende beperkingen en de drempels van MongoDB vertrouwd maken.
