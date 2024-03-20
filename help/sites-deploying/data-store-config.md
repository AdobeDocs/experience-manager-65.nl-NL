---
title: Opslaan van knooppunten en gegevensopslag configureren in AEM 6
description: Leer hoe te om knoopopslag en gegevensopslag te vormen en hoe te om huisvuilinzameling van de gegevensopslag uit te voeren.
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: c1c90d6a-ee5a-487d-9a8a-741b407c8c06
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3476'
ht-degree: 0%

---

# Opslaan van knooppunten en gegevensopslag configureren in AEM 6{#configuring-node-stores-and-data-stores-in-aem}

## Inleiding {#introduction}

In Adobe Experience Manager (AEM) kunnen binaire gegevens onafhankelijk van de inhoudsknooppunten worden opgeslagen. De binaire gegevens worden opgeslagen in een gegevensopslag, terwijl de inhoudsknopen in een knoopopslag worden opgeslagen.

Zowel kunnen de gegevensopslag als de knoopopslag worden gevormd gebruikend configuratie OSGi. Elke configuratie OSGi wordt van verwijzingen voorzien gebruikend een blijvend herkenningsteken (PID).

## Configuratiestappen {#configuration-steps}

Om zowel de knoopopslag als de gegevensopslag te vormen, voer deze stappen uit:

1. Kopieer het JAR-bestand met de AEM QuickStart naar de installatiemap.
1. Een map maken `crx-quickstart/install` in de installatiemap.
1. Eerst, vorm de knoopopslag door een configuratiedossier met de naam van de optie van de knoopopslag te creëren u in wilt gebruiken `crx-quickstart/install` directory.

   Het bestand wordt bijvoorbeeld gebruikt in het archief met Document-knooppunten (dat de basis vormt voor AEM MongoMK-implementatie) `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`.

1. Bewerk het bestand en stel de configuratieopties in.
1. Maak een configuratiebestand met de PID van de gegevensopslagruimte die u wilt gebruiken. Bewerk het bestand om de configuratieopties in te stellen.

   >[!NOTE]
   >
   >Zie [Configuratie van knooppuntopslag](#node-store-configurations) en [Configuraties van gegevensopslag](#data-store-configurations) voor configuratieopties.

1. Start AEM.

## Configuratie van knooppuntopslag {#node-store-configurations}

>[!CAUTION]
>
>De nieuwere versies van Oak gebruiken een nieuwe noemende regeling en formaat voor OSGi configuratiedossiers. Het nieuwe naamgevingsschema vereist dat het configuratiebestand een naam krijgt **.config** en de nieuwe indeling vereist dat waarden worden ingevoerd en [hier gedocumenteerd](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format).
>
>Als u een upgrade uitvoert van een oudere versie van Eak, dient u een back-up te maken van de `crx-quickstart/install`map eerst. Na de upgrade herstelt u de inhoud van de map naar de bijgewerkte installatie en wijzigt u de extensie van de configuratiebestanden vanuit **.cfg** tot **.config**.
>
>Als u dit artikel leest ter voorbereiding op een upgrade van een **AEM 5,x** , dient u de [upgrade](https://experienceleague.adobe.com/docs/) documentatie eerst.

### Segmentknooppuntarchief {#segment-node-store}

De opslag van de segmentknoop is de basis van de implementatie TarMK van de Adobe in AEM6. Het gebruikt de `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` PID voor configuratie.

>[!CAUTION]
>
>De PID voor het archief met segmentknooppunten is gewijzigd van `org.apache.jackrabbit.oak.plugins.segment.SegmentNodeStoreService in previous versions` van AEM 6 `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` in AEM 6.3. Zorg ervoor u de noodzakelijke configuratieaanpassingen aanbrengt om deze verandering te weerspiegelen.

U kunt de volgende opties configureren:

* `repository.home`: Pad naar de thuislocatie van de gegevensopslagruimte waaronder aan de gegevensopslagruimte gerelateerde gegevens worden opgeslagen. Standaard worden segmentbestanden opgeslagen onder de `crx-quickstart/segmentstore` directory.

* `tarmk.size`: Maximale grootte van een segment in MB. Het standaardmaximum is 256 MB.
* `customBlobStore`: Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. De standaardwaarde is waar voor AEM 6.3 en latere versies. Vóór AEM 6.3 was de standaardwaarde false.

Hier volgt een voorbeeld `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` bestand:

```shell
#Path to repo
repository.home="crx-quickstart/repository"

#Max segment size
tarmk.size=I"256"

#Custom data store
customBlobStore=B"true"
```

#### Document Node Store {#document-node-store}

De opslag van de documentknoop is de basis van AEM implementatie MongoMK. Het gebruikt de `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService`* *PID. De volgende configuratieopties zijn beschikbaar:

* `mongouri`: De [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/) vereist om verbinding te maken met Mongo Database. De standaardwaarde is `mongodb://localhost:27017`

* `db`: Naam van de Mongo-database. De standaardwaarde is **Eik** ``. However, new AEM 6 installations use **aem-author** ``als de standaarddatabasenaam.

* `cache`: De cachegrootte in MB. Dit wordt verdeeld over diverse geheime voorgeheugens die in DocumentNodeStore worden gebruikt. De standaardwaarde is `256`

* `changesSize`: Grootte in MB van de afgetopte inzameling die in Mongo voor caching van de afdiff output wordt gebruikt. De standaardwaarde is `256`

* `customBlobStore`: Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. De standaardwaarde is `false`.

Hier volgt een voorbeeld `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config` bestand:

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
>Als u aangepaste gegevensopslag wilt inschakelen, moet u ervoor zorgen dat `customBlobStore` is ingesteld op `true` in het desbetreffende Node Store-configuratiebestand ([segmentknooppuntopslag](/help/sites-deploying/data-store-config.md#segment-node-store) of [archief van documentknooppunten](/help/sites-deploying/data-store-config.md#document-node-store)).

### Bestandsgegevensopslag {#file-data-store}

Dit is de uitvoering van [FileDataStore](https://jackrabbit.apache.org/api/trunk/org/apache/jackrabbit/core/data/FileDataStore.html) aanwezig in Jasje 2. Hiermee kunt u de binaire gegevens opslaan als normale bestanden in het bestandssysteem. Het gebruikt de `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore` PID.

Deze configuratieopties zijn beschikbaar:

* `repository.home`: Pad naar de thuislocatie van de gegevensopslagruimte waarin verschillende gegevensbestanden met betrekking tot de gegevensopslagruimte zijn opgeslagen. Standaard worden binaire bestanden opgeslagen onder `crx-quickstart/repository/datastore` directory

* `path`: Pad naar de map waarin de bestanden worden opgeslagen. Indien opgegeven, heeft deze voorrang op `repository.home` value

* `minRecordLength`: De minimale grootte in bytes van een bestand dat is opgeslagen in de gegevensopslag. Binaire inhoud die kleiner is dan deze waarde, wordt gealigneerd.

>[!NOTE]
>
>Wanneer u een NAS gebruikt om gedeelde opslagruimten voor bestandsgegevens op te slaan, moet u ervoor zorgen dat u alleen apparaten met hoge prestaties gebruikt om prestatieproblemen te voorkomen.

## Amazon S3 Data Store {#amazon-s-data-store}

AEM kunnen worden geconfigureerd om gegevens op te slaan in Amazon Simple Storage Service (S3). Het gebruikt de `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` PID voor configuratie.

>[!NOTE]
>
>AEM 6.5 ondersteunt het opslaan van gegevens in Amazon S3, maar de ondersteuning wordt niet uitgebreid tot het opslaan van gegevens in andere platforms, waarvan de leveranciers mogelijk hun eigen implementaties van Amazon S3 API&#39;s hebben.

Om de functionaliteit van de S3 gegevensopslag toe te laten, moet een eigenschappak dat de S3 Datastore Schakelaar bevat worden gedownload en worden geïnstalleerd. Ga naar de [Opslagplaats Adobe](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) en download de nieuwste versie van de 1.10.x-versies van het functiepakket (bijvoorbeeld com.adobe.granite.oak.s3connector-1.10.0.zip). U moet ook het nieuwste AEM servicepakket downloaden en installeren, zoals vermeld op het tabblad [AEM 6.5 Opmerkingen bij de release](/help/release-notes/release-notes.md) pagina.

>[!NOTE]
>
>Wanneer u AEM gebruikt met TarMK, worden binaire bestanden standaard opgeslagen in het dialoogvenster `FileDataStore`. Als u TarMK met de S3 Datastore wilt gebruiken, moet u AEM gebruiken `crx3tar-nofds` runmode, bijvoorbeeld:

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

1. Als AEM al is geconfigureerd voor de Tar- of MongoDB-opslag, verwijdert u bestaande configuratiebestanden uit de ***&lt;aem-install>***/*crx-quickstart*/*installeren* map voordat u verdergaat. De bestanden die moeten worden verwijderd, zijn:

   * `For MongoMK: org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`
   * `For TarMK: org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Ga terug naar de tijdelijke locatie waar het functiepakket is uitgepakt en kopieer de inhoud van de volgende map:

   * `jcr_root/libs/system/config`

   tot

   * `<aem-install>/crx-quickstart/install`

   Zorg ervoor u slechts de configuratiedossiers nodig door uw huidige configuratie kopieert. Voor zowel een speciale gegevensopslag als een gedeelde gegevensopslag kopieert u de `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` bestand.

   >[!NOTE]
   >
   >Voer in een clusterinstelling bovenstaande stappen uit op alle knooppunten van de cluster een voor een. Zorg ook dat u dezelfde S3-instellingen gebruikt voor alle knooppunten.

1. Bewerk het bestand en voeg de configuratieopties toe die nodig zijn voor de installatie.
1. Start AEM.

## Een upgrade uitvoeren naar een nieuwe versie van de 1.10.x S3-connector {#upgrading-to-a-new-version-of-the-s-connector}

Ga als volgt te werk om te upgraden naar een nieuwe versie van de 1.10.x S3-connector (bijvoorbeeld van 1.10.0 naar 1.10.4):

1. Stop de AEM instantie.

1. Navigeren naar `<aem-install>/crx-quickstart/install/15` in de AEM installatiemap en maak een back-up van de inhoud ervan.
1. Na de steun, schrap de oude versie van de S3 Schakelaar en zijn gebiedsdelen door alle jar dossiers in te schrappen `<aem-install>/crx-quickstart/install/15` map, bijvoorbeeld:

   * **eiken-blob-cloud-1.6.1.jar**
   * **aws-java-sdk-osgi-1.10.76.jar**

   >[!NOTE]
   >
   >De hierboven vermelde bestandsnamen worden alleen ter illustratie gebruikt.

1. Download de nieuwste versie van het 1.10.x-functiepakket via de [Opslagplaats Adobe](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/).
1. Pak de inhoud uit en ga vervolgens naar een aparte map `jcr_root/libs/system/install/15`.
1. De jar-bestanden kopiëren naar **&lt;aem-install>**/crx-quickstart/install/15 in de AEM installatiemap.
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
>De S3 schakelaar steunt zowel IAM gebruikersauthentificatie als IAM rolauthentificatie. Om IAM rolauthentificatie te gebruiken, laat weg `accessKey` en `secretKey` waarden uit het configuratiebestand. De S3 schakelaar zal dan aan [IAM-rol](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) toegewezen aan de instantie.

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
| s3Region | Regio waar de emmer zich bevindt. Zie dit [page](https://docs.aws.amazon.com/general/latest/gr/s3.html) voor meer informatie . | Regio waar AWS-instantie wordt uitgevoerd. | Nee. |
| socketTimeout | Stel in hoeveel tijd (in milliseconden) moet worden gewacht voordat gegevens via een gevestigde, open verbinding worden overgebracht en deze verbinding wordt gesloten. | 50000 | Nee. |
| stagingPurgeInterval | Het interval (in seconden) voor het leegmaken van voltooide uploads vanaf de testcache. | 300 | Nee. |
| stagingRetryInterval | Het interval (in seconden) om mislukte uploads opnieuw te proberen. | 600 | Nee. |
| stagingSplitPercentage | Het percentage van `cacheSize` te gebruiken voor het opvoeren van asynchrone uploads. | 10 | Nee. |
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
>De DataStore-implementaties van `S3DataStore`, `CachingFileDataStore` en `AzureDataStore` lokale bestandssysteemcaching ondersteunen. De `CachingFileDataStore` implementatie is nuttig wanneer DataStore op NFS (het Systeem van het Dossier van het Netwerk) is.

Wanneer u een upgrade uitvoert vanaf een oudere cacheimplementatie (vóór Eak 1.6), is er een verschil in de structuur van de cachemap van het lokale bestandssysteem. In de oude cachestructuur werden zowel de gedownloade als de geüploade bestanden rechtstreeks onder het cachepad geplaatst. De nieuwe structuur segregeert de downloads en uploadt en slaat hen in twee genoemde folders op `upload` en `download` onder cachepad. Het upgradeproces moet naadloos zijn en alle uploads die in behandeling zijn, moeten worden gepland voor uploaden en alle eerder gedownloade bestanden in de cache worden bij initialisatie in de cache geplaatst.

U kunt de cache ook offline upgraden met de `datastorecacheupgrade` opdracht van de eiken. Voor details over hoe te om het bevel uit te voeren, controleer [readme](https://svn.apache.org/repos/asf/jackrabbit/oak/trunk/oak-run/README.md) voor de eiken-loopmodule.

Het geheime voorgeheugen heeft een groottegrens en het kan worden gevormd door de cacheSize parameter te gebruiken.

#### Downloads {#downloads}

Het lokale geheime voorgeheugen wordt gecontroleerd op het verslag van het gevraagde dossier/blok alvorens tot het van DataStore toegang te hebben. Wanneer het geheime voorgeheugen de gevormde grens overschrijdt (zie `cacheSize` (parameter) wanneer u een bestand toevoegt aan de cache, worden sommige bestanden verwijderd om ruimte vrij te maken.

#### Asynchroon uploaden {#async-upload}

De cache ondersteunt asynchrone uploads naar de DataStore. De bestanden worden lokaal in het cachegeheugen (op het bestandssysteem) opgeslagen en het bestand wordt met een asynchrone taak geüpload. Het aantal asynchrone uploads wordt beperkt door de grootte van de opvoercache. De grootte van het het opvoeren geheime voorgeheugen wordt gevormd door te gebruiken `stagingSplitPercentage` parameter. Deze parameter bepaalt het percentage van geheim voorgeheugengrootte dat voor het opvoeren geheim voorgeheugen moet worden gebruikt. Bovendien wordt het percentage cachegeheugen dat beschikbaar is voor downloads berekend als **(100 - `stagingSplitPercentage`) &#42;`cacheSize`**.

De asynchrone uploads zijn multi-threaded en het aantal draden wordt gevormd door te gebruiken `uploadThreads` parameter.

De bestanden worden naar de hoofddownloadcache verplaatst nadat het uploaden is voltooid. Wanneer de grootte van de faseringscache groter is dan de limiet, worden de bestanden synchroon geüpload naar de DataStore totdat de vorige asynchrone uploads zijn voltooid en er weer ruimte beschikbaar is in de testcache. De geüploade bestanden worden verwijderd uit het parkeergebied door een periodieke taak waarvan het interval wordt geconfigureerd door de `stagingPurgeInterval` parameter.

De mislukte uploads (bijvoorbeeld, wegens een netwerkverstoring) worden gezet op een herprobeert rij en periodiek opnieuw geprobeerd. Het retry interval wordt gevormd door te gebruiken `stagingRetryInterval parameter`.

#### Bindloze replicatie configureren met Amazon S3 {#configuring-binaryless-replication-with-amazon-s}

Om binaryless replicatie met S3 te vormen, worden de volgende stappen vereist:

1. Installeer de auteur en publiceer instanties en zorg ervoor zij behoorlijk begonnen zijn.
1. Ga naar de montages van de replicatieagent, door een pagina te openen aan *https://localhost:4502/etc/replication/agents.author/publish.html*.
1. Druk op **Bewerken** in de **Instellingen** sectie.
1. Wijzig de **Serienummering** tekstoptie naar **Binair minder**.

1. De parameter &quot; `binaryless`= `true`&quot; in de vervoeruri. Na de wijziging moet de uri er ongeveer als volgt uitzien:

   *https://localhost:4503/bin/receive?sling:authRequestLogin=1&amp;binaryless=true*

1. Start alle auteur- en publicatieinstanties opnieuw om de wijzigingen van kracht te laten worden.

#### Een cluster maken met S3 en MongoDB {#creating-a-cluster-using-s-and-mongodb}

1. Pak CQ QuickStart uit met de volgende opdracht:

   `java -jar cq-quickstart.jar -unpack`

1. Nadat AEM is uitgepakt, maakt u een map in de installatiemap *crx-quickstart*/*installeren*.

1. Deze twee bestanden maken in het dialoogvenster `crx-quickstart` map:

   * *org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService*.*config*

   * *org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore*.*config*

   Nadat de bestanden zijn gemaakt, voegt u de benodigde configuratieopties toe.

1. Installeer de twee bundels die vereist zijn voor de opslag van S3-gegevens, zoals hierboven beschreven.
1. Controleer of MongoDB is geïnstalleerd en of `mongod` wordt uitgevoerd.
1. Begin AEM met de volgende opdracht:

   `java -Xmx1024m -jar cq-quickstart.jar -r crx3,crx3mongo`

1. Herhaal stap 1 tot en met 4 voor de tweede AEM.
1. Start de tweede AEM.

#### Een gedeelde gegevensopslag configureren {#configuring-a-shared-data-store}

1. Maak eerst het configuratiebestand van de gegevensopslagruimte op elke instantie die nodig is om de gegevensopslag te delen:

   * Als u een `FileDataStore`, maakt u een bestand met de naam `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` en plaatst deze in de `<aem-install>/crx-quickstart/install` map.

   * Als u S3 gebruikt als gegevensopslag, maakt u een bestand met de naam `rg.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` in de `<aem-install>/crx-quickstart/install` map als hierboven.

1. Wijzig de de configuratiedossiers van de gegevensopslag op elke instantie zodat richten zij aan de zelfde gegevensopslag. Zie voor meer informatie [dit artikel](/help/sites-deploying/data-store-config.md#data-store-configurations).
1. Als de instantie is gekloond van een bestaande server, moet u het `clusterId` van het nieuwe exemplaar door het recentste hulpmiddel van de eiken-looppas te gebruiken terwijl de bewaarplaats off-line is. De opdracht die u moet uitvoeren is:

   ```xml
   java -jar oak-run.jar resetclusterid < repository path | Mongo URI >
   ```

   >[!NOTE]
   >
   >Als een de knoopopslag van het Segment wordt gevormd, dan moet de bewaarplaatspad worden gespecificeerd. Standaard is het pad `<aem-install-folder>/crx-quickstart/repository/segmentstore.` Als een Document Nodeopslag wordt gevormd kunt u gebruiken [URI monoverbinding](https://docs.mongodb.org/manual/reference/connection-string/).

   >[!NOTE]
   >
   >Het gereedschap voor het uitvoeren van een eik kan worden gedownload van de volgende locatie:
   >
   >
   >[https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)
   >
   >
   >Welke versies van het gereedschap worden gebruikt, is afhankelijk van de eikversie die u gebruikt bij de AEM. Controleer de onderstaande lijst met versievereisten voordat u het gereedschap gebruikt:
   >
   >
   >
   >    * Voor eiken-versies **1.2.x** de eik gebruiken **1.2.12 of hoger**
   >    * Voor eiken-versies **nieuwer dan bovenstaande**, gebruikt u de versie van de eik-run die overeenkomt met de eik-kern van de AEM-installatie.
   >
   >

1. Ten slotte valideert u de configuratie. Om te valideren, zoekt u naar een uniek bestand dat aan de gegevensopslag is toegevoegd door elke opslagplaats die het deelt. De bestandsindeling is `repository-[UUID]`, waarbij de UUID een unieke id is van elke afzonderlijke opslagplaats.

   Daarom zou een juiste configuratie zo vele unieke dossiers moeten hebben aangezien er bewaarplaatsen zijn die de gegevensopslag delen.

   De bestanden worden anders opgeslagen, afhankelijk van de gegevensopslag:

   * Voor de `FileDataStore` de bestanden worden gemaakt onder het hoofdpad van de gegevensopslagmap.
   * Voor de `S3DataStore` de dossiers in de gevormde S3 emmer onder worden gecreeerd `META` map.

## Azure Data Store {#azure-data-store}

AEM kunnen worden geconfigureerd om gegevens op te slaan in de Azure-opslagservice van Microsoft®. Het gebruikt de `org.apache.jackrabbit.oak.plugins.blob.datastore.AzureDataStore.config` PID voor configuratie.

Om de functionaliteit van de Azure-gegevensopslag mogelijk te maken, moet een functiepakket met de Azure-connector worden gedownload en geïnstalleerd. Ga naar de [Opslagplaats Adobe](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.azureblobconnector/) en download de nieuwste versie van de 1.6.x-versies van het functiepakket (bijvoorbeeld com.adobe.granite.oak.azureblobconnector-1.6.3.zip).

>[!NOTE]
>
>Wanneer het gebruiken van AEM met TarMK, worden de binaire getallen opgeslagen door gebrek in FileDataStore. Als u TarMK wilt gebruiken met de Azure DataStore, moet u beginnen AEM met het `crx3tar-nofds` runmode, bijvoorbeeld:

```shell
java -jar <aem-jar-file>.jar -r crx3tar-nofds
```

Na het downloaden kunt u de Azure-connector als volgt installeren en configureren:

1. Pak de inhoud van het ZIP-bestand van het functiepakket uit naar een tijdelijke map.

1. Naar de tijdelijke map gaan en de inhoud van `jcr_root/libs/system/install` aan de `<aem-install>crx-quickstart/install` map.
1. Als AEM al is geconfigureerd voor de Tar- of MongoDB-opslag, verwijdert u bestaande configuratiebestanden uit de `/crx-quickstart/install` map voordat u verdergaat. De bestanden die moeten worden verwijderd, zijn:

   VoorMongoMK:

   `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

   Voor TarMK:

   `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Ga terug naar de tijdelijke locatie waar het functiepakket is uitgepakt en kopieer de inhoud van `jcr_root/libs/system/config` aan de `<aem-install>/crx-quickstart/install` map.
1. Bewerk het configuratiebestand en voeg de configuratieopties toe die nodig zijn voor uw installatie.
1. Start AEM.

U kunt het configuratiebestand gebruiken met de volgende opties:

* azureSas=&quot;&quot;: in versie 1.6.3 van de connector werd ondersteuning voor Azure Shared Access Signature (SAS) toegevoegd. **Als het configuratiebestand zowel SAS- als opslagreferenties bevat, heeft SAS prioriteit.** Voor meer informatie over SAS raadpleegt u de [officiële documentatie](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview). Zorg ervoor dat het teken &#39;=&#39; wordt genummerd als &#39;\=&#39;.

* azureBlobEndpoint=&quot;&quot;: Het Azure Blob Endpoint. Bijvoorbeeld https://&lt;storage-account>.blob.core.windows.net.
* accessKey=&quot;&quot;: de naam van de opslagaccount. Voor meer informatie over de Microsoft® Azure verificatiereferenties raadpleegt u de [officiële documentatie](https://azure.microsoft.com/en-us/documentation/articles/storage-create-storage-account).

* SECTKey=&quot;&quot;: de toegangstoets voor opslag. Zorg ervoor dat het teken &#39;=&#39; wordt genummerd als &#39;\=&#39;.
* container=&quot;&quot;: De naam van de Microsoft® Azure blob opslagcontainer. De container is een groepering van een set bollen. Lees voor meer informatie de [officiële documentatie](https://learn.microsoft.com/en-us/rest/api/storageservices/Naming-and-Referencing-Containers--Blobs--and-Metadata?redirectedfrom=MSDN).
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

1. Ga naar de JMX-console op *https://&lt;serveraddress:port>/system/console/jmx*
1. Zoeken naar **RepositoryManagement.** Als u de gegevensopslagbeheerder MBean hebt gevonden, klikt u erop om de beschikbare opties weer te geven.
1. Ga naar het einde van de pagina en klik op de knop **startDataStoreGC(booleaanse markeringOnly)** koppeling.
1. In het volgende dialoogvenster voert u `false` voor de `markOnly` parameter, klik vervolgens op **Invoeden**:

   ![chlimage_1-9](assets/chlimage_1-9.png)

   >[!NOTE]
   >
   >De `markOnly` parameter geeft aan of de sweep-fase van de opschoonfunctie wordt uitgevoerd.

## De Inzameling van de Winkel van gegevens voor een Gedeelde Opslag van Gegevens {#data-store-garbage-collection-for-a-shared-data-store}

>[!NOTE]
>
>Wanneer het uitvoeren van huisvuilinzameling in een gegroepeerde of gedeelde gegevensopslag, opstelling (met Mongo of Tar van het Segment) zou het logboek waarschuwingen over de onmogelijkheid kunnen tonen om bepaalde blob IDs te schrappen. Klob-id&#39;s die zijn verwijderd in een vorige opschoning, worden onjuist weergegeven door andere clusters of gedeelde knooppunten die geen informatie hebben over het verwijderen van id&#39;s. Dientengevolge, wanneer de huisvuilinzameling wordt uitgevoerd registreert het een waarschuwing wanneer het probeert om identiteitskaart te schrappen die reeds in de laatste looppas is geschrapt. Dit gedrag heeft geen invloed op prestaties of functionaliteit.

>[!NOTE]
>
>Als u een gedeelde datastore opstelling gebruikt en de inzameling van het datastore huisvuil wordt onbruikbaar gemaakt, kan het runnen van de Binaire schoonmaaktaak van Lucene plotseling de gebruikte schijfruimte verhogen. U kunt BlobTracker op alle auteur uitschakelen en instanties publiceren door het volgende te doen:
>
>1. Stop de AEM Instance.
>2. Voeg de `blobTrackSnapshotIntervalInSecs=L"0"` in de `crx-quickstart/install/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` bestand. Deze parameter vereist eik 1.12.0, 1.10.2 of later.
>3. Start de AEM opnieuw.

Met nieuwere versies van AEM, kan de inzameling van huisvuil van de gegevensopslag ook op gegevensopslag worden in werking gesteld die door meer dan één bewaarplaats wordt gedeeld. Voer de volgende stappen uit om de opschoonfunctie van gegevensopslaggegevens uit te voeren in een gedeelde gegevensopslag:

1. Zorg ervoor dat om het even welke onderhoudstaken die voor de inzameling van huisvuil van de gegevensopslag worden gevormd op alle bewaarplaats instanties onbruikbaar worden gemaakt die de gegevensopslag delen.
1. Voer de in [Binaire afvalophaling](/help/sites-deploying/data-store-config.md#data-store-garbage-collection) individueel **alles** gegevensopslaginstanties die de gegevensopslag delen. Zorg er echter voor dat u `true` voor de `markOnly` parameter voordat u op de knop Invoke klikt:

   ![chlimage_1-10](assets/chlimage_1-10.png)

1. Nadat u de bovenstaande procedure in alle gevallen hebt voltooid, voert u de opschoonfunctie van de gegevensopslagruimte opnieuw uit **alle** van de gevallen:

   1. Ga naar de JMX-console en selecteer de Repository Manager Mbean.
   1. Klik op de knop **Klik op startDataStoreGC (booleaanse markeringOnly)** koppeling.
   1. In het volgende dialoogvenster voert u `false` voor de `markOnly` opnieuw.

   Alle gevonden bestanden worden gesorteerd met behulp van de markeringsfase die voor is gebruikt en de overige bestanden die niet in de gegevensopslag worden gebruikt, worden verwijderd.
