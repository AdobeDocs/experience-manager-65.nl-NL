---
title: Opslaan van knooppunten en gegevensopslag configureren in AEM 6
description: Leer hoe te om knoopopslag en gegevensopslag te vormen en hoe te om huisvuilinzameling van de gegevensopslag uit te voeren.
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: c1c90d6a-ee5a-487d-9a8a-741b407c8c06
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: f96b178ae84b4b930b59e36d4994970682c53dbd
workflow-type: tm+mt
source-wordcount: '3461'
ht-degree: 0%

---

# Opslaan van knooppunten en gegevensopslag configureren in AEM 6{#configuring-node-stores-and-data-stores-in-aem}

## Inleiding {#introduction}

In Adobe Experience Manager (AEM) kunnen binaire gegevens onafhankelijk van de inhoudsknooppunten worden opgeslagen. De binaire gegevens worden opgeslagen in een gegevensopslag, terwijl de inhoudsknopen in een knoopopslag worden opgeslagen.

Zowel kunnen de gegevensopslag als de knoopopslag worden gevormd gebruikend configuratie OSGi. Elke configuratie OSGi wordt van verwijzingen voorzien gebruikend een blijvend herkenningsteken (PID).

## Configuratiestappen {#configuration-steps}

Om zowel de knoopopslag als de gegevensopslag te vormen, voer deze stappen uit:

1. Kopieer het JAR-bestand voor AEM quickstart naar de installatiemap.
1. Maak een map `crx-quickstart/install` in de installatiemap.
1. Eerst, vorm de knoopopslag door een configuratiedossier met de naam van de optie van de knoopopslag te creëren u in de `crx-quickstart/install` folder wilt gebruiken.

   Het bestand `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config` wordt bijvoorbeeld gebruikt in het archief met documentknooppunten (dat de basis vormt voor de AEM MongoMK-implementatie).

1. Bewerk het bestand en stel de configuratieopties in.
1. Maak een configuratiebestand met de PID van de gegevensopslagruimte die u wilt gebruiken. Bewerk het bestand om de configuratieopties in te stellen.

   >[!NOTE]
   >
   >Zie {de Configuraties van de Opslag van 0} Knoop [&#128279;](#node-store-configurations) en [ Configuraties van de Opslag van Gegevens ](#data-store-configurations) voor configuratieopties.

1. Start AEM.

## Configuratie van knooppuntopslag {#node-store-configurations}

>[!CAUTION]
>
>De nieuwere versies van Oak gebruiken een nieuw noemend regeling en formaat voor OSGi configuratiedossiers. Het nieuwe noemende schema vereist dat het configuratiedossier **.config** wordt genoemd en het nieuwe formaat vereist dat de waarden worden getypt. Voor details zie [ het Apache Sling Provisioning Model en Apache SlingStart - het StandaardFormaat van de Configuratie ](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format).
>
>Als u van een oudere versie van Oak bevordert, zorg ervoor dat u eerst een steun van de `crx-quickstart/install` omslag maakt. Na de verbetering, herstel de inhoud van de omslag aan de promotieinstallatie en wijzig de uitbreiding van de configuratiedossiers van **.cfg** aan **.config**.

### Segmentknooppuntarchief {#segment-node-store}

De opslag van segmentknooppunten is de basis van de Adobe TarMK-implementatie in AEM6. De `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` PID wordt gebruikt voor configuratie.

>[!CAUTION]
>
>De PID voor het archief met segmentknooppunten is gewijzigd van `org.apache.jackrabbit.oak.plugins.segment.SegmentNodeStoreService in previous versions` van AEM 6 in `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` in AEM 6.3. Zorg ervoor u de noodzakelijke configuratieaanpassingen aanbrengt om deze verandering te weerspiegelen.

U kunt de volgende opties configureren:

* `repository.home`: pad naar de thuislocatie van de gegevensopslagruimte waaronder aan de gegevensopslagruimte gerelateerde gegevens worden opgeslagen. Segmentbestanden worden standaard opgeslagen onder de map `crx-quickstart/segmentstore` .

* `tarmk.size`: Maximale grootte van een segment in MB. Het standaardmaximum is 256 MB.
* `customBlobStore`: Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. De standaardwaarde is waar voor AEM 6.3 en latere versies. Vóór AEM 6.3 was de standaardwaarde false.

Hier volgt een voorbeeld van een `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` -bestand:

```shell
#Path to repo
repository.home="crx-quickstart/repository"

#Max segment size
tarmk.size=I"256"

#Custom data store
customBlobStore=B"true"
```

#### Document Node Store {#document-node-store}

De opslag van documentknooppunten is de basis van de AEM MongoMK-implementatie. Het gebruikt `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService`* *PID. De volgende configuratieopties zijn beschikbaar:

* `mongouri`: [ MongoURI ](https://docs.mongodb.org/manual/reference/connection-string/) wordt vereist om met het Gegevensbestand van Mongo te verbinden dat. De standaardwaarde is `mongodb://localhost:27017`

* `db`: naam van de Mongo-database. Het gebrek is **Oak** ``. However, new AEM 6 installations use **aem-author** `` als standaardgegevensbestandnaam.

* `cache`: De cachegrootte in MB. Dit wordt verdeeld over diverse geheime voorgeheugens die in DocumentNodeStore worden gebruikt. De standaardwaarde is `256`

* `changesSize`: Grootte in MB van de afgetopte inzameling die in Mongo voor caching van de diff output wordt gebruikt. De standaardwaarde is `256`

* `customBlobStore`: Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. De standaardwaarde is `false` .

Hier volgt een voorbeeld van een `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config` -bestand:

```shell
#Mongo server details
mongouri="mongodb://localhost:27017"

#Name of Mongo database to use
db="aem-author"

#Store binaries in custom BlobStore
customBlobStore=B"false"
```

## Configuraties van gegevensopslag {#data-store-configurations}

Wanneer het behandelen van groot aantal binaire getallen, adviseert men dat een externe gegevensopslag in plaats van de standaardknoopopslag wordt gebruikt om prestaties te maximaliseren.

Als uw project bijvoorbeeld veel media-elementen vereist, kunt u deze sneller opslaan onder de File of S3 Data Store dan ze rechtstreeks in een MongoDB op te slaan.

De File Data Store biedt betere prestaties dan MongoDB, en back-up- en herstelbewerkingen in Mongo zijn ook trager bij een groot aantal middelen.

De details over de verschillende gegevensopslag en configuraties worden hieronder beschreven.

>[!NOTE]
>
>Om de Opslag van douaneGegevens toe te laten, moet u ervoor zorgen dat `customBlobStore` aan `true` in het respectieve de configuratiedossier van de Opslag van de Knoop van de Knoop ([ de opslag van de segmentknoop ](/help/sites-deploying/data-store-config.md#segment-node-store) of [ opslag van de documentknoop ](/help/sites-deploying/data-store-config.md#document-node-store)) wordt geplaatst.

### Bestandsgegevensopslag {#file-data-store}

Dit is de implementatie van [ FileDataStore ](https://jackrabbit.apache.org/api/trunk/org/apache/jackrabbit/core/data/FileDataStore.html) huidig in Jackrabbit 2. Hiermee kunt u de binaire gegevens opslaan als normale bestanden in het bestandssysteem. De `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore` PID wordt gebruikt.

Deze configuratieopties zijn beschikbaar:

* `repository.home`: pad naar de thuislocatie van de gegevensopslagruimte waarin verschillende gegevensbestanden met betrekking tot de gegevensopslagruimte zijn opgeslagen. Binaire bestanden worden standaard opgeslagen onder de map `crx-quickstart/repository/datastore` .

* `path`: pad naar de map waarin de bestanden worden opgeslagen. Indien opgegeven heeft deze voorrang op de waarde `repository.home`

* `minRecordLength`: de minimale grootte in bytes van een bestand dat is opgeslagen in de gegevensopslag. Binaire inhoud die kleiner is dan deze waarde, wordt gealigneerd.

>[!NOTE]
>
>Wanneer u een NAS gebruikt om gedeelde opslagruimten voor bestandsgegevens op te slaan, moet u ervoor zorgen dat u alleen apparaten met hoge prestaties gebruikt om prestatieproblemen te voorkomen.

## Amazon S3 Data Store {#amazon-s-data-store}

AEM kan worden geconfigureerd om gegevens op te slaan in Amazon Simple Storage Service (S3). De `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` PID wordt gebruikt voor configuratie.

>[!NOTE]
>
>AEM 6.5 biedt ondersteuning voor het opslaan van gegevens in Amazon S3, maar de ondersteuning wordt niet uitgebreid tot het opslaan van gegevens op andere platformen, waarvan de leveranciers hun eigen implementaties van Amazon S3 API&#39;s hebben.

Om de functionaliteit van de S3 gegevensopslag toe te laten, moet een eigenschappak dat de S3 Datastore Schakelaar bevat worden gedownload en worden geïnstalleerd. Ga naar de [ Bewaarplaats van Adobe ](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) en download de recentste versie van 1.10.x versies van het eigenschappak (bijvoorbeeld, com.adobe.granite.oak.s3connector-1.10.0.zip). Ook, moet u het recentste de dienstpak van AEM downloaden en installeren zoals vermeld op [ AEM 6.5 de Nota&#39;s van de Versie ](/help/release-notes/release-notes.md) pagina.

>[!NOTE]
>
>Wanneer u AEM gebruikt met TarMK, worden binaire bestanden standaard opgeslagen in de `FileDataStore` . Als u TarMK wilt gebruiken met de S3 Datastore, moet u AEM starten met de runmode `crx3tar-nofds` , bijvoorbeeld:

```shell
java -jar <aem-jar-file>.jar -r crx3tar-nofds
```

Na het downloaden kunt u de S3-connector als volgt installeren en configureren:

1. Pak de inhoud van het ZIP-bestand van het functiepakket uit naar een tijdelijke map.

1. Ga naar de tijdelijke map en navigeer naar de volgende locatie:

   ```xml
   jcr_root/libs/system/install
   ```

   Alle inhoud van de bovenstaande locatie kopiëren naar `<aem-install>/crx-quickstart/install.`

1. Als AEM reeds wordt gevormd om met de opslag van Tar of MongoDB te werken, verwijder om het even welke bestaande configuratiedossiers van *** &lt;aem-install>**/*crx-quickstart*/ *installeer* omslag alvorens te werk te gaan. De bestanden die moeten worden verwijderd, zijn:

   * `For MongoMK: org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`
   * `For TarMK: org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Ga terug naar de tijdelijke locatie waar het functiepakket is uitgepakt en kopieer de inhoud van de volgende map:

   * `jcr_root/libs/system/config`

   tot

   * `<aem-install>/crx-quickstart/install`

   Zorg ervoor u slechts de configuratiedossiers nodig door uw huidige configuratie kopieert. Kopieer het `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` -bestand voor zowel een speciale gegevensopslag als een gedeelde gegevensopslag.

   >[!NOTE]
   >
   >Voer in een clusterinstelling bovenstaande stappen uit op alle knooppunten van de cluster een voor een. Zorg ook dat u dezelfde S3-instellingen gebruikt voor alle knooppunten.

1. Bewerk het bestand en voeg de configuratieopties toe die nodig zijn voor de installatie.
1. Start AEM.

## Een upgrade uitvoeren naar een nieuwe versie van de 1.10.x S3-connector {#upgrading-to-a-new-version-of-the-s-connector}

Ga als volgt te werk om te upgraden naar een nieuwe versie van de 1.10.x S3-connector (bijvoorbeeld van 1.10.0 naar 1.10.4):

1. Stop de AEM-instantie.

1. Navigeer naar `<aem-install>/crx-quickstart/install/15` in de installatiemap van AEM en maak een back-up van de inhoud ervan.
1. Na de steun, schrap de oude versie van de S3 Schakelaar en zijn gebiedsdelen door alle jar dossiers in de `<aem-install>/crx-quickstart/install/15` omslag te schrappen, bijvoorbeeld:

   * **eiken-blob-wolk-1.6.1.jar**
   * **aws-java-sdk-osgi-1.10.76.jar**

   >[!NOTE]
   >
   >De hierboven vermelde bestandsnamen worden alleen ter illustratie gebruikt.

1. Download de recentste versie van het 1.10.x eigenschappak van het [ Bewaarplaats van Adobe ](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/).
1. Pak de inhoud uit en ga vervolgens naar `jcr_root/libs/system/install/15` .
1. Kopieer de jar dossiers aan **&lt;aem-install>**/crx-quickstart/install/15 in de installatiemap van AEM.
1. Start AEM en controleer de verbindingsfunctionaliteit.

U kunt het configuratiebestand gebruiken met de opties die hieronder worden beschreven.

<!--
* accessKey: The AWS access key.
* secretKey: The AWS secret access key. **Note:** When the `accessKey` or `secretKey` is not specified then the [IAM role](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) is used for authentication.
* s3Bucket: The bucket name.
* s3Region: The bucket region.
* path: The path of the data store. The default is **&lt;AEM install folder&gt;/repository/datastore**
* minRecordLength: The minimum size of an object that should be stored in the data store. The minimum/default is **16KB.**
* maxCachedBinarySize: Binaries with size less than or equal to this size will be stored in memory cache. The size is in bytes. The default is **17408 **(17 KB).
* cacheSize: The size of the cache. The value is specified in bytes. The default is **64GB**.
* secret: Only to be used if using binaryless replication for shared datastore setup.
* stagingSplitPercentage: The percentage of cache size configured to be used for staging asynchronous uploads. The default value is **10**.
* uploadThreads: The number of uploads threads that are used for asynchronous uploads. The default value is **10**.
* stagingPurgeInterval: The interval in seconds for purging finished uploads from the staging cache. The default value is **300** seconds (5 minutes).
* stagingRetryInterval: The retry interval in seconds for failed uploads. The default value is **600** seconds (10 minutes).
-->

### Opties voor S3-connectorconfiguratiebestand {#s3-connector-configuration-file-options}

>[!NOTE]
>
>De S3 schakelaar steunt zowel IAM gebruikersauthentificatie als IAM rolauthentificatie. Als u IAM-rolverificatie wilt gebruiken, laat u de waarden `accessKey` en `secretKey` weg uit het configuratiebestand. De S3 schakelaar zal dan aan de [ IAM rol ](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) in gebreke blijven die aan de instantie wordt toegewezen.

| Sleutel | Beschrijving | Standaard | Vereist |
| --- | --- | --- | --- |
| accessKey | Toegang tot sleutel-id voor de IAM-gebruiker met toegang tot het emmertje. | | Ja, wanneer u geen IAM-rollen gebruikt. |
| geheimeKey | Geheime toegangstoets voor de IAM-gebruiker met toegang tot het emmertje. | | Ja, wanneer u geen IAM-rollen gebruikt. |
| cacheSize | De grootte (in bytes) van de lokale cache. | 64 GB | Nee. |
| connectionTimeout | Stel de hoeveelheid tijd in die moet worden gewacht (in milliseconden) voordat u de time-out verlaat wanneer u een verbinding maakt. | 10000 | Nee. |
| maxCachedBinarySize | Binaire bestanden met een grootte die kleiner is dan of gelijk is aan deze waarde (in bytes) worden opgeslagen in de geheugencache. | 17408 (17 kB) | Nee. |
| maxConnections | Stel het maximum aantal toegestane open HTTP-verbindingen in. | 50 | Nee. |
| maxErrorRetry | Stel het maximumaantal pogingen voor mislukte (opvraagbare) aanvragen in. | 3 | Nee. |
| minRecordlength | De minimale grootte van een object (in bytes) die moet worden opgeslagen in de gegevensopslag. | 16384 | Nee. |
| pad | Het lokale pad van de AEM datastore. | `crx-quickstart/repository/datastore` | Nee. |
| proxyHost | Stel de optionele proxyhost in waarmee de client verbinding maakt. | | Nee. |
| proxyPort | Stel de optionele proxypoort in waarmee de client verbinding maakt. | | Nee. |
| s3Bucket | Naam van het S3 emmertje. | | Ja |
| s3EndPoint | S3 REST API-eindpunt. | | Nee. |
| s3Region | Regio waar de emmer zich bevindt. Zie deze [ pagina ](https://docs.aws.amazon.com/general/latest/gr/s3.html) voor meer details. | Regio waar AWS-instantie wordt uitgevoerd. | Nee. |
| socketTimeout | Stel in hoeveel tijd (in milliseconden) moet worden gewacht voordat gegevens via een gevestigde, open verbinding worden overgebracht en deze verbinding wordt gesloten. | 50000 | Nee. |
| stagingPurgeInterval | Het interval (in seconden) voor het leegmaken van voltooide uploads vanaf de testcache. | 300 | Nee. |
| stagingRetryInterval | Het interval (in seconden) om mislukte uploads opnieuw te proberen. | 600 | Nee. |
| stagingSplitPercentage | Het percentage van `cacheSize` dat moet worden gebruikt voor het stapelen van asynchrone uploads. | 10 | Nee. |
| uploadThreads | Het aantal uploadthreads dat wordt gebruikt voor asynchrone uploads. | 10 | Nee. |
| writeThreads | Het aantal gezamenlijke draden die voor het schrijven via S3 Manager van de Overdracht worden gebruikt. | 10 | Nee. |

<!---
### Bucket region options {#bucket-region-options}

<table>
 <tbody>
  <tr>
   <td>US Standard</td>
   <td><code>us-standard</code></td>
  </tr>
  <tr>
   <td>US West</td>
   <td><code>us-west-2</code></td>
  </tr>
  <tr>
   <td>US West (Northern California)</td>
   <td><code>us-west-1</code></td>
  </tr>
  <tr>
   <td>EU (Ireland)<br /> </td>
   <td><code>EU</code></td>
  </tr>
  <tr>
   <td>Asia Pacific (Singapore)<br /> </td>
   <td><code>ap-southeast-1</code></td>
  </tr>
  <tr>
   <td>Asia Pacific (Sydney)<br /> </td>
   <td><code>ap-southeast-2</code></td>
  </tr>
  <tr>
   <td>Asia Pacific (Tokyo)</td>
   <td><code>ap-northeast-1</code></td>
  </tr>
  <tr>
   <td>South America (Sao Paolo)<br /> </td>
   <td><code>sa-east-1</code></td>
  </tr>
 </tbody>
</table>
-->

### DataStore in cache plaatsen {#data-store-caching}

>[!NOTE]
>
>De DataStore-implementaties van `S3DataStore` , `CachingFileDataStore` en `AzureDataStore` ondersteunen het in cache plaatsen van lokale bestandssystemen. De `CachingFileDataStore` -implementatie is nuttig wanneer de DataStore zich op NFS (Network File System) bevindt.

Wanneer u een upgrade uitvoert vanaf een oudere cache-implementatie (vóór Oak 1.6), is er een verschil in de structuur van de cachemap van het lokale bestandssysteem. In de oude cachestructuur werden zowel de gedownloade als de geüploade bestanden rechtstreeks onder het cachepad geplaatst. De nieuwe structuur segregeert de downloads en uploadt deze en slaat ze op in twee mappen met de naam `upload` en `download` onder het cachepad. Het upgradeproces moet naadloos zijn en alle uploads die in behandeling zijn, moeten worden gepland voor uploaden en alle eerder gedownloade bestanden in de cache worden bij initialisatie in de cache geplaatst.

U kunt de cache ook offline upgraden met behulp van de opdracht `datastorecacheupgrade` voor het uitvoeren van een eiken. Voor details op hoe te om het bevel uit te voeren, controleer [ readme ](https://svn.apache.org/repos/asf/jackrabbit/oak/trunk/oak-run/README.md) voor de eiken-looppas module.

Het geheime voorgeheugen heeft een groottegrens en het kan worden gevormd door de cacheSize parameter te gebruiken.

#### Downloads {#downloads}

Het lokale geheime voorgeheugen wordt gecontroleerd op het verslag van het gevraagde dossier/blok alvorens tot het van DataStore toegang te hebben. Wanneer de cache de geconfigureerde limiet overschrijdt (zie de parameter `cacheSize` ) terwijl een bestand in de cache wordt geplaatst, worden sommige bestanden uitgespoten om ruimte vrij te geven.

#### Asynchroon uploaden {#async-upload}

De cache ondersteunt asynchrone uploads naar de DataStore. De bestanden worden lokaal in het cachegeheugen (op het bestandssysteem) opgeslagen en het bestand wordt met een asynchrone taak geüpload. Het aantal asynchrone uploads wordt beperkt door de grootte van de opvoercache. De grootte van de testcache wordt geconfigureerd met de parameter `stagingSplitPercentage` . Deze parameter bepaalt het percentage van geheim voorgeheugengrootte dat voor het opvoeren geheim voorgeheugen moet worden gebruikt. Het percentage cache dat beschikbaar is voor downloads, wordt ook berekend als **(100 - `stagingSplitPercentage`) &#42;`cacheSize`** .

De asynchrone uploads zijn multi-threaded en het aantal draden wordt gevormd door de `uploadThreads` parameter te gebruiken.

De bestanden worden naar de hoofddownloadcache verplaatst nadat het uploaden is voltooid. Wanneer de grootte van de faseringscache groter is dan de limiet, worden de bestanden synchroon geüpload naar de DataStore totdat de vorige asynchrone uploads zijn voltooid en er weer ruimte beschikbaar is in de testcache. De geüploade bestanden worden uit het testgebied verwijderd door een periodieke taak waarvan het interval wordt geconfigureerd door de parameter `stagingPurgeInterval` .

De mislukte uploads (bijvoorbeeld, wegens een netwerkverstoring) worden gezet op een herprobeert rij en periodiek opnieuw geprobeerd. Het interval voor opnieuw proberen wordt gevormd door `stagingRetryInterval parameter` te gebruiken.

#### Bindloze replicatie configureren met Amazon S3 {#configuring-binaryless-replication-with-amazon-s}

Om binaryless replicatie met S3 te vormen, worden de volgende stappen vereist:

1. Installeer de auteur en publiceer instanties en zorg ervoor zij behoorlijk begonnen zijn.
1. Ga naar de montages van de replicatieagent, door een pagina aan *https://localhost:4502/etc/replication/agents.author/publish.html* te openen.
1. Druk **uitgeven** knoop in de **sectie van Montages**.
1. Verander de **typeoptie van de Serienummering** &lbrace;in **Binair minder**.

1. Voeg de parameter &quot; `binaryless`= `true`&quot; toe aan de transporturi. Na de wijziging moet de uri er ongeveer als volgt uitzien:

   *https://localhost:4503/bin/receive?sling:authRequestLogin=1&amp;binaryless=true*

1. Start alle auteur- en publicatieinstanties opnieuw om de wijzigingen van kracht te laten worden.

#### Een cluster maken met S3 en MongoDB {#creating-a-cluster-using-s-and-mongodb}

1. Pak CQ QuickStart uit met de volgende opdracht:

   `java -jar cq-quickstart.jar -unpack`

1. Nadat AEM is leeggemaakt, creeer een omslag binnen de installatiemap *crx-quickstart*/*installeert*.

1. Maak deze twee bestanden in de map `crx-quickstart` :

   * *org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService*.*config*

   * *org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore*.*config*

   Nadat de bestanden zijn gemaakt, voegt u de benodigde configuratieopties toe.

1. Installeer de twee bundels die vereist zijn voor de opslag van S3-gegevens, zoals hierboven beschreven.
1. Controleer of MongoDB is geïnstalleerd en of een instantie van `mongod` wordt uitgevoerd.
1. Start AEM met de volgende opdracht:

   `java -Xmx1024m -jar cq-quickstart.jar -r crx3,crx3mongo`

1. Herhaal stap 1 tot en met 4 voor de tweede AEM-instantie.
1. Start de tweede AEM-instantie.

#### Een gedeelde gegevensopslag configureren {#configuring-a-shared-data-store}

1. Maak eerst het configuratiebestand van de gegevensopslagruimte op elke instantie die nodig is om de gegevensopslag te delen:

   * Als u een `FileDataStore` gebruikt, maakt u een bestand met de naam `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` en plaatst u dit in de map `<aem-install>/crx-quickstart/install` .

   * Als u S3 gebruikt als gegevensopslagruimte, maakt u een bestand met de naam `rg.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` in de map `<aem-install>/crx-quickstart/install` , zoals hierboven.

1. Wijzig de de configuratiedossiers van de gegevensopslag op elke instantie zodat richten zij aan de zelfde gegevensopslag. Voor meer informatie, zie [ Configuraties van de Opslag van Gegevens ](/help/sites-deploying/data-store-config.md#data-store-configurations).
1. Als de instantie is gekloond vanaf een bestaande server, moet u de `clusterId` van de nieuwe instantie verwijderen met het nieuwste hulpprogramma voor het uitvoeren van een eiken terwijl de opslagplaats offline is. De opdracht die u moet uitvoeren is:

   ```xml
   java -jar oak-run.jar resetclusterid < repository path | Mongo URI >
   ```

   >[!NOTE]
   >
   >Als een de knoopopslag van het Segment wordt gevormd, dan moet de bewaarplaatspad worden gespecificeerd. Door gebrek, is de weg `<aem-install-folder>/crx-quickstart/repository/segmentstore.` als een de knoopopslag van het Document wordt gevormd u het Koord URI van de Verbinding van het a [ Mongo ](https://docs.mongodb.org/manual/reference/connection-string/) kunt gebruiken.

   >[!NOTE]
   >
   >U kunt het gereedschap Oak-run downloaden van de volgende locatie:
   >
   >
   >[ https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)
   >
   >
   >Afhankelijk van de Oak-versie die u gebruikt bij de AEM-installatie, moeten verschillende versies van het gereedschap worden gebruikt. Controleer de onderstaande lijst met versievereisten voordat u het gereedschap gebruikt:
   >
   >
   >
   >    * Voor de versies van Oak **1.2.x** gebruik Oak-looppas **1.2.12 of nieuwer**
   >    * Voor de versies van Oak **nieuwer dan hierboven**, gebruik de versie van Oak-looppas die de kern van Oak van uw installatie van AEM aanpast.
   >
   >

1. Ten slotte valideert u de configuratie. Om te valideren, zoekt u naar een uniek bestand dat aan de gegevensopslag is toegevoegd door elke opslagplaats die het deelt. De indeling van de bestanden is `repository-[UUID]` , waarbij de UUID een unieke id is van elke afzonderlijke gegevensopslagruimte.

   Daarom zou een juiste configuratie zo vele unieke dossiers moeten hebben aangezien er bewaarplaatsen zijn die de gegevensopslag delen.

   De bestanden worden anders opgeslagen, afhankelijk van de gegevensopslag:

   * Voor `FileDataStore` worden de bestanden gemaakt onder het hoofdpad van de gegevensopslagmap.
   * Voor `S3DataStore` worden de dossiers gecreeerd in de gevormde S3 emmer onder de `META` omslag.

## Azure Data Store {#azure-data-store}

AEM kan worden geconfigureerd om gegevens op te slaan in de Azure-opslagservice van Microsoft®. De `org.apache.jackrabbit.oak.plugins.blob.datastore.AzureDataStore.config` PID wordt gebruikt voor configuratie.

Om de functionaliteit van de Azure-gegevensopslag mogelijk te maken, moet een functiepakket met de Azure-connector worden gedownload en geïnstalleerd. Ga naar de [ Bewaarplaats van Adobe ](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.azureblobconnector/) en download de recentste versie van 1.6.x versies van het eigenschappak (bijvoorbeeld, com.adobe.granite.oak.azureblobconnector-1.6.3.zip).

>[!NOTE]
>
>Wanneer u AEM gebruikt met TarMK, worden binaire bestanden standaard opgeslagen in de FileDataStore. Als u TarMK wilt gebruiken met de Azure DataStore, moet u AEM starten met de runmode `crx3tar-nofds` , bijvoorbeeld:

```shell
java -jar <aem-jar-file>.jar -r crx3tar-nofds
```

Na het downloaden kunt u de Azure-connector als volgt installeren en configureren:

1. Pak de inhoud van het ZIP-bestand van het functiepakket uit naar een tijdelijke map.

1. Ga naar de tijdelijke map en kopieer de inhoud van `jcr_root/libs/system/install` naar de `<aem-install>crx-quickstart/install` -map.
1. Als AEM al is geconfigureerd voor de Tar- of MongoDB-opslag, verwijdert u eventuele bestaande configuratiebestanden uit de map `/crx-quickstart/install` voordat u verdergaat. De bestanden die moeten worden verwijderd, zijn:

   VoorMongoMK:

   `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

   Voor TarMK:

   `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Ga terug naar de tijdelijke locatie waar het functiepakket is uitgepakt en kopieer de inhoud van `jcr_root/libs/system/config` naar de map `<aem-install>/crx-quickstart/install` .
1. Bewerk het configuratiebestand en voeg de configuratieopties toe die nodig zijn voor uw installatie.
1. Start AEM.

U kunt het configuratiebestand gebruiken met de volgende opties:

* azureSas=&quot;&quot;: in versie 1.6.3 van de connector werd ondersteuning voor Azure Shared Access Signature (SAS) toegevoegd. **als zowel SAS als opslaggeloofsbrieven in het configuratiedossier bestaan, heeft SAS prioriteit.** voor meer informatie over SAS zie de [ officiële documentatie ](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview). Zorg ervoor dat het teken &#39;=&#39; wordt genummerd als &#39;\=&#39;.

* azureBlobEndpoint=&quot;&quot;: Het Azure Blob Endpoint. Bijvoorbeeld https://&lt;storage-account>.blob.core.windows.net.
* accessKey=&quot;&quot;: de naam van de opslagaccount. Voor meer details over Microsoft® Azure authentificatiegeloofsbrieven, zie de [ officiële documentatie ](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create).

* SECTKey=&quot;&quot;: de toegangstoets voor opslag. Zorg ervoor dat het teken &#39;=&#39; wordt genummerd als &#39;\=&#39;.
* container=&quot;&quot;: De naam van de Microsoft® Azure blob opslagcontainer. De container is een groepering van een set bollen. Voor extra details, lees de [ officiële documentatie ](https://learn.microsoft.com/en-us/rest/api/storageservices/Naming-and-Referencing-Containers--Blobs--and-Metadata?redirectedfrom=MSDN).
* maxConnections=&quot;&quot;: het gelijktijdige aantal gelijktijdige aanvragen per bewerking. De standaardwaarde is 1.
* maxErrorRetry=&quot;&quot;: aantal pogingen per aanvraag. De standaardwaarde is 3.
* socketTimeout=&quot;&quot;: het time-outinterval, in milliseconden, dat wordt gebruikt voor de aanvraag. De standaardwaarde is 5 minuten.

Naast de bovenstaande instellingen kunnen ook de volgende instellingen worden geconfigureerd:

* pad: het pad van de gegevensopslag. De standaardwaarde is `<aem-install>/repository/datastore.`
* RecordLength: de minimale grootte van een object dat in de gegevensopslag moet worden opgeslagen. De standaardwaarde is 16 kB.
* maxCachedBinarySize: binaire bestanden met een grootte kleiner dan of gelijk aan deze grootte worden opgeslagen in de geheugencache. De grootte is in bytes. De standaardwaarde is 17408 (17 kB).
* cacheSize: De grootte van de cache. De waarde wordt opgegeven in bytes. De standaardwaarde is 64 GB.
* geheim: slechts te gebruiken als het gebruiken van binaryless replicatie voor gedeelde datastore opstelling.
* stagingSplitPercentage: Het percentage cachegrootte dat wordt geconfigureerd voor het stapelen van asynchrone uploads. De standaardwaarde is 10.
* uploadThreads: Het aantal uploadthreads dat wordt gebruikt voor asynchrone uploads. De standaardwaarde is 10.
* stagingPurgeInterval: het interval in seconden voor het leegmaken van voltooide uploads vanuit de testcache. De standaardwaarde is 300 seconden (5 minuten).
* stagingRetryInterval: het interval voor opnieuw proberen in seconden voor mislukte uploads. De standaardwaarde is 600 seconden (10 minuten).

>[!NOTE]
>
>Alle instellingen moeten tussen aanhalingstekens worden geplaatst, bijvoorbeeld:

```shell
accessKey="ASDASDERFAERAER"
secretKey="28932hfjlkwdo8fufsdfas\=\="
```

## Opruiming voor dataopslag {#data-store-garbage-collection}

Het proces van de huisvuilinzameling van de gegevensopslag wordt gebruikt om het even welke ongebruikte dossiers in de gegevensopslag te verwijderen, waarbij waardevolle schijfruimte in het proces wordt vrijgemaakt.

U kunt de inzameling van het huisvuilopslag in werking stellen door:

1. Ga naar de console JMX in *https://&lt;serveradres:haven>/system/console/jmx*
1. Het zoeken naar **RepositoryManagement.** Als u de gegevensopslagbeheerder MBean hebt gevonden, klikt u erop om de beschikbare opties weer te geven.
1. De rol aan het eind van de pagina, en klikt **startDataStoreGC (booleaanse markOnly)** verbinding.
1. In de volgende dialoog, ga `false` voor de `markOnly` parameter in, dan klik **aanhalen**:

   ![ chlimage_1-9 ](assets/chlimage_1-9.png)

   >[!NOTE]
   >
   >De parameter `markOnly` geeft aan of de sweep-fase van de afvalophaling wordt uitgevoerd of niet.

## De Inzameling van de Winkel van gegevens voor een Gedeelde Opslag van Gegevens {#data-store-garbage-collection-for-a-shared-data-store}

>[!NOTE]
>
>Wanneer het uitvoeren van huisvuilinzameling in een gegroepeerde of gedeelde gegevensopslag, opstelling (met Mongo of Tar van het Segment) zou het logboek waarschuwingen over de onmogelijkheid kunnen tonen om bepaalde blob IDs te schrappen. Klob-id&#39;s die zijn verwijderd in een vorige opschoning, worden onjuist weergegeven door andere clusters of gedeelde knooppunten die geen informatie hebben over het verwijderen van id&#39;s. Dientengevolge, wanneer de huisvuilinzameling wordt uitgevoerd registreert het een waarschuwing wanneer het probeert om identiteitskaart te schrappen die reeds in de laatste looppas is geschrapt. Dit gedrag heeft geen invloed op prestaties of functionaliteit.

>[!NOTE]
>
>Als u een gedeelde datastore opstelling gebruikt en de inzameling van het datastore huisvuil wordt onbruikbaar gemaakt, kan het runnen van de Binaire schoonmaaktaak van Lucene plotseling de gebruikte schijfruimte verhogen. U kunt BlobTracker op alle auteur uitschakelen en instanties publiceren door het volgende te doen:
>
>1. Stop de AEM-instantie.
>2. Voeg de parameter `blobTrackSnapshotIntervalInSecs=L"0"` toe in het `crx-quickstart/install/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` -bestand. Voor deze parameter is Oak 1.12.0, 1.10.2 of hoger vereist.
>3. Start de AEM-instantie opnieuw.

Met nieuwere versies van AEM, kan de inzameling van huisvuil van de gegevensopslag ook op gegevensopslag worden in werking gesteld die door meer dan één bewaarplaats wordt gedeeld. Voer de volgende stappen uit om de opschoonfunctie van gegevensopslaggegevens uit te voeren in een gedeelde gegevensopslag:

1. Zorg ervoor dat om het even welke onderhoudstaken die voor de inzameling van huisvuil van de gegevensopslag worden gevormd op alle bewaarplaats instanties onbruikbaar worden gemaakt die de gegevensopslag delen.
1. Voer de stappen in werking die in [ worden vermeld Binaire Inzameling van het Afval ](/help/sites-deploying/data-store-config.md#data-store-garbage-collection) individueel op **alle** bewaarplaats instanties die de gegevensopslag delen. Zorg er echter voor dat u `true` voor de parameter `markOnly` opgeeft voordat u op de knop Invoke klikt:

   ![ chlimage_1-10 ](assets/chlimage_1-10.png)

1. Na de voltooiing van de bovengenoemde procedure op alle instanties, stel het huisvuil van de gegevensopslag opnieuw van **in werking om het even welk** van de instanties:

   1. Ga naar de JMX-console en selecteer de Repository Manager Mbean.
   1. Klik **startDataStoreGC (booleaanse markOnly)** verbinding.
   1. Voer in het volgende dialoogvenster nogmaals `false` in voor de parameter `markOnly` .

   Alle gevonden bestanden worden gesorteerd met behulp van de markeringsfase die voor is gebruikt en de overige bestanden die niet in de gegevensopslag worden gebruikt, worden verwijderd.
