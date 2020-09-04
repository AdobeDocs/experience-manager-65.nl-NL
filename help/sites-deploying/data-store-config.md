---
title: Opslaan van knooppunten en gegevensopslag configureren in AEM 6
seo-title: Opslaan van knooppunten en gegevensopslag configureren in AEM 6
description: Leer hoe te om knoopopslag en gegevensopslag te vormen en hoe te om huisvuilinzameling van de gegevensopslag uit te voeren.
seo-description: Leer hoe te om knoopopslag en gegevensopslag te vormen en hoe te om huisvuilinzameling van de gegevensopslag uit te voeren.
uuid: 1a58c0ba-1c32-4539-ad0d-0a27c8c4ff5e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: b97482f2-2791-4d14-ae82-388302d9eab3
docset: aem65
legacypath: /deploy/platform/data-store-config
translation-type: tm+mt
source-git-commit: f0ec3415ffef70c985828f17b32dc0d453c1ae7c
workflow-type: tm+mt
source-wordcount: '3427'
ht-degree: 0%

---


# Opslaan van knooppunten en gegevensopslag configureren in AEM 6{#configuring-node-stores-and-data-stores-in-aem}

## Inleiding {#introduction}

In Adobe Experience Manager (AEM) kunnen binaire gegevens onafhankelijk van de inhoudsknooppunten worden opgeslagen. De binaire gegevens worden opgeslagen in een gegevensopslag, terwijl de inhoudsknopen in een knoopopslag worden opgeslagen.

Zowel kunnen de gegevensopslag als de knoopopslag worden gevormd gebruikend configuratie OSGi. Elke configuratie OSGi wordt van verwijzingen voorzien gebruikend een blijvend herkenningsteken (PID).

## Configuratiestappen {#configuration-steps}

Om zowel de knoopopslag als de gegevensopslag te vormen, voer deze stappen uit:

1. Kopieer het JAR-bestand met de AEM QuickStart naar de installatiemap.
1. Maak een map `crx-quickstart/install` in de installatiemap.
1. Eerst, vorm de knoopopslag door een configuratiedossier met de naam van de optie van de knoopopslag te creëren u in de `crx-quickstart/install` folder wilt gebruiken.

   Het bestand wordt bijvoorbeeld gebruikt in het archief met Document-knooppunten (dat de basis vormt voor AEM MongoMK-implementatie) `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`.

1. Bewerk het bestand en stel de configuratieopties in.
1. Maak een configuratiebestand met de PID van de gegevensopslagruimte die u wilt gebruiken. Bewerk het bestand om de configuratieopties in te stellen.

   >[!NOTE]
   >
   >Zie [Node Store Configurations](#node-store-configurations) en [Data Store Configurations](#data-store-configurations) voor configuratieopties.

1. Start AEM.

## Configuratie van knooppuntopslag {#node-store-configurations}

>[!CAUTION]
>
>De nieuwere versies van Oak gebruiken een nieuwe noemende regeling en formaat voor OSGi configuratiedossiers. De nieuwe noemende regeling vereist dat het configuratiedossier wordt genoemd **.config** en het nieuwe formaat vereist waarden worden getypt en hier [wordt](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format)gedocumenteerd.
>
>Als u een upgrade uitvoert van een oudere versie van Eak, dient u eerst een back-up van de `crx-quickstart/install`map te maken. Na de verbetering, herstel de inhoud van de omslag aan de promotieinstallatie en wijzig de uitbreiding van de configuratiedossiers van **.cfg** aan **.config**.
>
>Als u dit artikel leest ter voorbereiding op een upgrade van een **AEM 5.x** -installatie, dient u eerst de [upgrade](https://docs.adobe.com/content/docs/en/aem/6-0/deploy/upgrade.html) -documentatie te raadplegen.

### Segmentknooppuntarchief {#segment-node-store}

De opslag van de segmentknoop is de basis van implementatie TarMK in Adobe AEM6. Het gebruikt `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` PID voor configuratie.

>[!CAUTION]
>
>PID voor de de knoopopslag van het Segment is veranderd van `org.apache.jackrabbit.oak.plugins.segment.SegmentNodeStoreService in previous versions` AEM 6 in `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` in AEM 6.3. Zorg ervoor u de noodzakelijke configuratieaanpassingen aanbrengt om deze verandering te weerspiegelen.

U kunt de volgende opties configureren:

* `repository.home`: Pad naar huis van de opslagplaats waaronder gegevens met betrekking tot de opslagplaats worden opgeslagen. Standaard worden segmentbestanden opgeslagen onder de `crx-quickstart/segmentstore` map.

* `tarmk.size`: Maximale grootte van een segment in MB. Het standaardmaximum is 256 MB.
* `customBlobStore`: Een Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. De standaardwaarde is waar voor AEM 6.3 en latere versies. Vóór AEM 6.3 was de standaardwaarde false.

Hier volgt een voorbeeldbestand `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` :

```shell
#Path to repo
repository.home="crx-quickstart/repository"

#Max segment size
tarmk.size=I"256"

#Custom data store
customBlobStore=B"true"
```

#### Document Node Store {#document-node-store}

De opslag van de documentknoop is de basis van AEM implementatie MongoMK. Het gebruikt `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService`* *PID. De volgende configuratieopties zijn beschikbaar:

* `mongouri`: De [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/) die is vereist om verbinding te maken met de Mongo-database. The default is `mongodb://localhost:27017`

* `db`: Naam van de Mongo-database. De standaardinstelling is **Eak** ``. However, new AEM 6 installations use **aem-author** ``als de standaarddatabasenaam.

* `cache`: De cachegrootte in MB. Dit wordt verdeeld over diverse geheime voorgeheugens die in DocumentNodeStore worden gebruikt. The default is `256`

* `changesSize`: Grootte in MB van afgekapte inzameling die in Mongo wordt gebruikt voor caching van de diff output. The default is `256`

* `customBlobStore`: Een Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. The default is `false`.

Hier volgt een voorbeeldbestand `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config` :

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

Als uw project bijvoorbeeld een groot aantal media-elementen vereist, kunt u deze sneller openen dan ze rechtstreeks in een MongoDB opslaan als u ze onder de File- of S3 Data Store opslaat.

De File Data Store biedt betere prestaties dan MongoDB, en back-up- en herstelbewerkingen in Mongo zijn ook trager bij een groot aantal middelen.

De details over de verschillende gegevensopslag en configuraties worden hieronder beschreven.

>[!NOTE]
>
>Om de Opslag van douaneGegevens toe te laten, moet u ervoor zorgen dat `customBlobStore` wordt geplaatst aan `true` in het respectieve de configuratiedossier van de Opslag van de Knoop van de Knoop (de opslag[van de](/help/sites-deploying/data-store-config.md#segment-node-store) segmentknoop of de opslag [van de](/help/sites-deploying/data-store-config.md#document-node-store)documentknoop).

### Bestandsgegevensopslag {#file-data-store}

Dit is de implementatie van [FileDataStore](https://jackrabbit.apache.org/api/2.8/org/apache/jackrabbit/core/data/FileDataStore.html) in Jackrabbit 2. Hiermee kunt u de binaire gegevens opslaan als normale bestanden in het bestandssysteem. De `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore` PID wordt gebruikt.

Deze configuratieopties zijn beschikbaar:

* `repository.home`: Pad naar de thuislocatie van de gegevensopslagruimte waarin verschillende gegevens met betrekking tot de gegevensopslagruimte worden opgeslagen. Binaire bestanden worden standaard opgeslagen onder de `crx-quickstart/repository/datastore` directory

* `path`: Pad naar de map waarin de bestanden worden opgeslagen. Indien opgegeven heeft deze voorrang op de `repository.home` waarde

* `minRecordLength`: De minimale grootte in bytes van een bestand dat is opgeslagen in de gegevensopslag. Binaire inhoud die kleiner is dan deze waarde, wordt gealigneerd.

>[!NOTE]
>
>Wanneer u een NAS gebruikt om gedeelde opslagruimten voor bestandsgegevens op te slaan, moet u ervoor zorgen dat u alleen apparaten met hoge prestaties gebruikt om prestatieproblemen te voorkomen.

## Amazon S3 Data Store {#amazon-s-data-store}

AEM kunnen worden geconfigureerd om gegevens op te slaan in Amazon Simple Storage Service (S3). Het gebruikt `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` PID voor configuratie.

Om de S3 functionaliteit van de gegevensopslag toe te laten, moet een eigenschappak dat de S3 Schakelaar van de Datastore bevat worden gedownload en worden geïnstalleerd. Ga naar de [Adobe Repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/) en download de nieuwste versie van de 1.10.x-versie van het functiepakket (bijvoorbeeld com.adobe.granite.oak.s3connector-1.10.0.zip). Bovendien moet u ook het nieuwste AEM servicepack downloaden en installeren, zoals vermeld op de pagina Opmerkingen bij de release van [AEM 6.5](/help/release-notes/sp-release-notes.md) .

>[!NOTE]
>
>Wanneer het gebruiken van AEM met TarMK, zullen de binaire getallen door gebrek in `FileDataStore`worden opgeslagen. Om TarMK met S3 Datastore te gebruiken, moet u beginnen AEM gebruikend `crx3tar-nofds` runmode, bijvoorbeeld:

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

1. Als AEM al is geconfigureerd voor de Tar- of MongoDB-opslag, verwijdert u eventuele bestaande configuratiebestanden uit de map ***&lt;aem-install>**/*crx-quickstart*/*install* voordat u verdergaat. De bestanden die moeten worden verwijderd, zijn:

   * `For MongoMK: org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`
   * `For TarMK: org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Ga terug naar de tijdelijke locatie waar het functiepakket is uitgepakt en kopieer de inhoud van de volgende map:

   * `jcr_root/libs/system/config`

   tot

   * `<aem-install>/crx-quickstart/install`

   Zorg ervoor u slechts de configuratiedossiers nodig door uw huidige configuratie kopieert. Kopieer het `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` bestand voor zowel een speciale gegevensopslag als een gedeelde gegevensopslag.

   >[!NOTE]
   >
   >Voer in een clusterinstelling bovenstaande stappen uit op alle knooppunten van de cluster een voor een. Zorg er ook voor dat u dezelfde S3-instellingen gebruikt voor alle knooppunten.

1. Bewerk het bestand en voeg de configuratieopties toe die nodig zijn voor de installatie.
1. Start AEM.

### Een upgrade uitvoeren naar een nieuwe versie van de 1.10.x S3-connector {#upgrading-to-a-new-version-of-the-x-s-connector}

Voer de volgende stappen uit als u wilt upgraden naar een nieuwe versie van de 1.10.x S3-connector (bijvoorbeeld van 1.10.0 naar 1.10.4):

1. Stop de AEM instantie.

1. Navigeer naar `<aem-install>/crx-quickstart/install/15` in de installatiemap AEM en maak een back-up van de inhoud ervan.
1. Na de steun, schrap de oude versie van S3 Schakelaar en zijn gebiedsdelen door alle jar dossiers in de `<aem-install>/crx-quickstart/install/15` omslag, bijvoorbeeld te schrappen:

   * **eiken-blob-cloud-1.6.1.jar**
   * **aws-java-sdk-osgi-1.10.76.jar**

   >[!NOTE]
   >
   >De hierboven weergegeven bestandsnamen worden alleen ter illustratie gebruikt en zijn niet definitief.

1. Download de nieuwste versie van het 1.8.x-functiepakket van de [Adobe Repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/).
1. Pak de inhoud uit en ga naar een aparte map. `jcr_root/libs/system/install/15`
1. Kopieer de jar-bestanden naar **&lt;aem-install>**/crx-quickstart/install/15 in de installatiemap AEM.
1. Start AEM en controleer de verbindingsfunctionaliteit.

U kunt het configuratiebestand gebruiken met de volgende opties:

* accessKey: De toegangssleutel van AWS.
* geheimaand: De sleutel voor toegang tot het AWS-geheim. **Opmerking:** Alternatief, kunnen de rollen [](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) IAM voor authentificatie worden gebruikt. Als u IAM rollen gebruikt moet u niet meer het specificeren `accessKey` en `secretKey`.

* s3Bucket: De naam van het emmertje.
* s3Region: Het emmergebied.
* pad: Het pad van de gegevensopslag. De standaardinstelling is **&lt;AEM installatiemap>/repository/datastore**
* minRecordLength: De minimale grootte van een object dat in de gegevensopslag moet worden opgeslagen. De minimum/standaard is **16KB.**
* maxCachedBinarySize: Binaire bestanden met een grootte kleiner dan of gelijk aan deze grootte worden opgeslagen in de geheugencache. De grootte is in bytes. De standaardwaarde is **17408 **(17 KB).

* cacheSize: De grootte van de cache. De waarde wordt opgegeven in bytes. De standaardwaarde is **64 GB**.
* geheim: Slechts te gebruiken als het gebruiken van binaryless replicatie voor gedeelde datastore opstelling.
* stagingSplitPercentage: Het percentage van geheim voorgeheugengrootte die wordt gevormd om voor het opvoeren van asynchrone uploads te worden gebruikt. De standaardwaarde is **10**.
* uploadThreads: Het aantal uploadthreads dat wordt gebruikt voor asynchrone uploads. De standaardwaarde is **10**.
* stagingPurgeInterval: Het interval in seconden voor het leegmaken van voltooide uploads uit het opvoeren geheime voorgeheugen. De standaardwaarde is **300** seconden (5 minuten).
* stagingRetryInterval: Het interval voor opnieuw proberen in seconden voor mislukte uploads. De standaardwaarde is **600** seconden (10 minuten).

### Opties voor Emmergebied {#bucket-region-options}

<table>
 <tbody>
  <tr>
   <td>US Standard</td>
   <td><code>us-standard</code></td>
  </tr>
  <tr>
   <td>VS West</td>
   <td><code>us-west-2</code></td>
  </tr>
  <tr>
   <td>US West (Noord-Californië)</td>
   <td><code>us-west-1</code></td>
  </tr>
  <tr>
   <td>EU (Ierland)<br /> </td>
   <td><code>EU</code></td>
  </tr>
  <tr>
   <td>Azië in de Stille Oceaan (Singapore)<br /> </td>
   <td><code>ap-southeast-1</code></td>
  </tr>
  <tr>
   <td>Asia Pacific (Sydney)<br /> </td>
   <td><code>ap-southeast-2</code></td>
  </tr>
  <tr>
   <td>Azië, Stille Oceaan (Tokio)</td>
   <td><code>ap-northeast-1</code></td>
  </tr>
  <tr>
   <td>Zuid-Amerika (Sao Paolo)<br /> </td>
   <td><code>sa-east-1</code></td>
  </tr>
 </tbody>
</table>

**DataStore in cache plaatsen**

>[!NOTE]
>
>De DataStore-implementaties van het in cache plaatsen van lokale bestandssystemen `S3DataStore`, `CachingFileDataStore` en `AzureDataStore` ondersteunen dit. De `CachingFileDataStore` implementatie is nuttig wanneer DataStore op NFS (het Systeem van het Dossier van het Netwerk) is.


Wanneer u een upgrade uitvoert vanaf een oudere cacheimplementatie (vóór Eak 1.6), is er een verschil in de structuur van de cachemap van het lokale bestandssysteem. In de oude cachestructuur werden zowel de gedownloade als de geüploade bestanden rechtstreeks onder het cachepad geplaatst. De nieuwe structuur segregeert de downloads en uploadt en bewaart hen in twee folders genoemd `upload` en `download` onder geheim voorgeheugenweg. Het upgradeproces moet naadloos zijn en alle uploads die in behandeling zijn, moeten worden gepland voor uploaden en alle eerder gedownloade bestanden in de cache worden bij initialisatie in de cache geplaatst.

U kunt het geheime voorgeheugen ook offline bevorderen door het bevel van eiken-looppas te gebruiken. `datastorecacheupgrade` Voor details op hoe te om het bevel uit te voeren, controleer [readme](https://svn.apache.org/repos/asf/jackrabbit/oak/trunk/oak-run/README.md) voor de eiken-looppas module.

Het geheime voorgeheugen heeft een groottegrens en het kan worden gevormd door de cacheSize parameter te gebruiken.

**Downloads**

Het lokale geheime voorgeheugen zal op het verslag van het gevraagde dossier/blok worden gecontroleerd alvorens tot het van DataStore toegang te hebben. Wanneer de cache de geconfigureerde limiet overschrijdt (zie de `cacheSize` parameter) terwijl een bestand in de cache wordt geplaatst, worden enkele bestanden naar de herstelruimte uitgepakt.

**Asynchroon uploaden**

De cache ondersteunt asynchrone uploads naar de DataStore. De bestanden worden lokaal in het cachegeheugen (op het bestandssysteem) opgeslagen en het bestand wordt met een asynchrone taak geüpload. Het aantal asynchrone uploads wordt beperkt door de grootte van het opvoeringsgeheime voorgeheugen. De grootte van het het opvoeren geheime voorgeheugen wordt gevormd door de `stagingSplitPercentage` parameter te gebruiken. Deze parameter bepaalt het percentage van geheim voorgeheugengrootte dat voor het opvoeren geheim voorgeheugen moet worden gebruikt. Bovendien wordt het percentage cache dat beschikbaar is voor downloads berekend als **(100 -`stagingSplitPercentage`) *`cacheSize`**.

De asynchrone uploads zijn multi-threaded en het aantal draden wordt gevormd door de `uploadThreads` parameter te gebruiken.

De bestanden worden naar de hoofddownloadcache verplaatst nadat het uploaden is voltooid. Wanneer de grootte van de faseringscache groter is dan de limiet, worden de bestanden synchroon geüpload naar de DataStore totdat de vorige asynchrone uploads zijn voltooid en er weer ruimte beschikbaar is in de testcache. De geüploade bestanden worden uit het parkeergebied verwijderd door een periodieke taak waarvan het interval door de `stagingPurgeInterval` parameter wordt geconfigureerd.

De mislukte uploads (bijvoorbeeld, wegens een netwerkverstoring) worden gezet op een herprobeert rij en periodiek opnieuw geprobeerd. Het retry interval wordt gevormd door te gebruiken `stagingRetryInterval parameter`.

#### Bindloze replicatie configureren met Amazon S3 {#configuring-binaryless-replication-with-amazon-s}

Om binaryless replicatie met S3 te vormen, worden de volgende stappen vereist:

1. Installeer de auteur en publiceer instanties en zorg ervoor zij behoorlijk begonnen zijn.
1. Ga naar de montages van de replicatieagent, door een pagina aan *https://localhost:4502/etc/replication/agents.author/publish.html* te openen.
1. Druk op de knop **Bewerken** in de sectie **Instellingen** .
1. Wijzig de optie Type **serienummering** in **Binair minder**.

1. Voeg de parameter &quot; `binaryless`= `true`&quot; toe in de vervoeruri. Na de wijziging moet de uri er ongeveer als volgt uitzien:

   *https://localhost:4503/bin/receive?sling:authRequestLogin=1&amp;binaryless=true*

1. Start alle auteur- en publicatieinstanties opnieuw om de wijzigingen van kracht te laten worden.

#### Een cluster maken met S3 en MongoDB {#creating-a-cluster-using-s-and-mongodb}

1. Pak CQ QuickStart uit met de volgende opdracht:

   `java -jar cq-quickstart.jar -unpack`

1. Nadat AEM is uitgepakt, creeer een omslag binnen de installatiemap *crx-quickstart*/*install*.

1. Maak deze twee bestanden in de `crx-quickstart` map:

   * *org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService*.*config*

   * *org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore*.*config*

   Nadat de bestanden zijn gemaakt, voegt u de benodigde configuratieopties toe.

1. Installeer de twee bundels die vereist zijn voor de opslag van S3-gegevens, zoals hierboven beschreven.
1. Zorg ervoor dat MongoDB is geïnstalleerd en dat een exemplaar van `mongod` wordt uitgevoerd.
1. Begin AEM met de volgende opdracht:

   `java -Xmx1024m -XX:MaxPermSize=256M -jar cq-quickstart.jar -r crx3,crx3mongo`

1. Herhaal stap 1 tot en met 4 voor de tweede AEM.
1. Start de tweede AEM.

#### Een gedeelde gegevensopslag configureren {#configuring-a-shared-data-store}

1. Maak eerst het configuratiebestand van de gegevensopslagruimte voor elke instantie die nodig is om de gegevensopslag te delen:

   * Als u een `FileDataStore`bestand gebruikt, maakt u een bestand met de naam `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` en plaatst u het in de `<aem-install>/crx-quickstart/install` map.

   * Als u S3 gebruikt als gegevensopslagruimte, maakt u een bestand met de naam of `rg.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` in de bovenstaande `<aem-install>/crx-quickstart/install` map.

1. Wijzig de de configuratiedossiers van de gegevensopslag op elke instantie om aan de zelfde gegevensopslag te richten. Zie [dit artikel](/help/sites-deploying/data-store-config.md#data-store-configurations)voor meer informatie.
1. Als de instantie is gekloond van een bestaande server, moet u de versie `clusterId` van de nieuwe instantie verwijderen door het recentste eiken-loophulpmiddel te gebruiken terwijl de bewaarplaats off-line is. De opdracht die u moet uitvoeren is:

   ```xml
   java -jar oak-run.jar resetclusterid < repository path | Mongo URI >
   ```

   >[!NOTE]
   >
   >Als een de knoopopslag van het Segment wordt gevormd dan moet de bewaarplaatspad worden gespecificeerd. Standaard is het pad `<aem-install-folder>/crx-quickstart/repository/segmentstore.` Als een Document Node Store wordt geconfigureerd, kunt u een [Mongo Connection String URI](https://docs.mongodb.org/manual/reference/connection-string/)gebruiken.

   >[!NOTE]
   >
   >Het gereedschap voor het uitvoeren van een eik kan worden gedownload van de volgende locatie:
   >
   >
   >[https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)
   >
   >
   >Houd er rekening mee dat verschillende versies van het gereedschap moeten worden gebruikt, afhankelijk van de eikenversie die u gebruikt bij de AEM installatie. Controleer de onderstaande lijst met versievereisten voordat u het gereedschap gebruikt:
   >
   >
   >
   >    * Gebruik voor Eak-versies **1.2.x** de Oak-run **1.2.12 of hoger**
   >    * Gebruik voor eikenversies die **nieuwer zijn dan de bovenstaande** versie de versie van de eik-run die overeenkomt met de eik-kern van de AEM-installatie.


1. Ten slotte valideert u de configuratie. Hiervoor moet u zoeken naar een uniek bestand dat aan de gegevensopslag is toegevoegd door elke opslagplaats die de gegevensopslag deelt. De indeling van de bestanden is `repository-[UUID]`waarbij de UUID een unieke id is van elke afzonderlijke opslagplaats.

   Daarom zou een juiste configuratie zo vele unieke dossiers moeten hebben aangezien er bewaarplaatsen zijn die de gegevensopslag delen.

   De bestanden worden anders opgeslagen, afhankelijk van de gegevensopslag:

   * Voor `FileDataStore` de bestanden worden bestanden gemaakt onder het hoofdpad van de opslagmap voor gegevens.
   * Voor `S3DataStore` de dossiers worden gecreeerd in het gevormde S3 emmertje onder de `META` omslag.

## Azure Data Store {#azure-data-store}

AEM kunnen worden geconfigureerd om gegevens op te slaan in de Azure-opslagservice van Microsoft. Het gebruikt `org.apache.jackrabbit.oak.plugins.blob.datastore.AzureDataStore.config` PID voor configuratie.

Om de functionaliteit van de Azure Data Store mogelijk te maken, moet een functiepakket met de Azure Connector worden gedownload en geïnstalleerd. Ga naar de [Adobe Repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.azureblobconnector/) en download de nieuwste versie van de 1.6.x-versies van het functiepakket (bijvoorbeeld com.adobe.granite.oak.azureblobconnector-1.6.3.zip).

>[!NOTE]
>
>Wanneer het gebruiken van AEM met TarMK, zullen de binaire getallen door gebrek in FileDataStore worden opgeslagen. Als u TarMK wilt gebruiken met de Azure DataStore, moet u AEM beginnen met de `crx3tar-nofds` runmode, bijvoorbeeld:

```shell
java -jar <aem-jar-file>.jar -r crx3tar-nofds
```

Na het downloaden kunt u de Azure-connector als volgt installeren en configureren:

1. Pak de inhoud van het ZIP-bestand van het functiepakket uit naar een tijdelijke map.

1. Ga naar de tijdelijke map en kopieer de inhoud van `jcr_root/libs/system/install` de map naar de `<aem-install>crx-quickstart/install` map.
1. Als AEM al is geconfigureerd voor de Tar- of MongoDB-opslag, verwijdert u eventuele bestaande configuratiebestanden uit de `/crx-quickstart/install` map voordat u verdergaat. De bestanden die moeten worden verwijderd, zijn:

   VoorMongoMK:

   `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

   Voor TarMK:

   `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Keer terug naar de tijdelijke plaats waar het eigenschappak is gehaald en kopieer de inhoud van `jcr_root/libs/system/config` aan de `<aem-install>/crx-quickstart/install` omslag.
1. Bewerk het configuratiebestand en voeg de configuratieopties toe die nodig zijn voor uw installatie.
1. Start AEM.

U kunt het configuratiebestand gebruiken met de volgende opties:

* azureSas=&quot;&quot;: In versie 1.6.3 van de connector werd ondersteuning voor Azure Shared Access Signature (SAS) toegevoegd. **Als het configuratiebestand zowel SAS- als opslagreferenties bevat, heeft SAS prioriteit.** Raadpleeg de [officiële documentatie](https://docs.microsoft.com/en-us/azure/storage/common/storage-dotnet-shared-access-signature-part-1)voor meer informatie over SAS. Zorg ervoor dat het teken &#39;=&#39; wordt genummerd als &#39;\=&#39;.

* azureBlobEndpoint=&quot;&quot;: Het Azure Blob Endpoint. Bijvoorbeeld https://&lt;storage-account>.blob.core.windows.net.
* accessKey=&quot;&quot;: De naam van de opslagaccount. Raadpleeg de [officiële documentatie](https://azure.microsoft.com/en-us/documentation/articles/storage-create-storage-account)voor meer informatie over de verificatiereferenties van Microsoft Azure.

* geheimakey=&quot;&quot;: De toegangstoets voor opslag. Zorg ervoor dat het teken &#39;=&#39; wordt genummerd als &#39;\=&#39;.
* container=&quot;&quot;: De naam van de Microsoft Azure-opslagcontainer. De container is een groepering van een set bollen. Lees de [officiële documentatie](https://msdn.microsoft.com/en-us/library/dd135715.aspx)voor meer informatie.
* maxConnections=&quot;&quot;: Het gelijktijdige aantal gelijktijdige aanvragen per bewerking. De standaardwaarde is 1.
* maxErrorRetry=&quot;&quot;: Aantal pogingen per verzoek. De standaardwaarde is 3.
* socketTimeout=&quot;&quot;: Het time-outinterval, in milliseconden, dat voor de aanvraag wordt gebruikt. De standaardwaarde is 5 minuten.

Naast de bovenstaande instellingen kunnen ook de volgende instellingen worden geconfigureerd:

* pad: Het pad van de gegevensopslag. The default is `<aem-install>/repository/datastore.`
* RecordLength: De minimale grootte van een object dat in de gegevensopslag moet worden opgeslagen. De standaardwaarde is 16KB.
* maxCachedBinarySize: Binaire bestanden met een grootte kleiner dan of gelijk aan deze grootte worden opgeslagen in de geheugencache. De grootte is in bytes. De standaardwaarde is 17408 (17 kB).
* cacheSize: De grootte van de cache. De waarde wordt opgegeven in bytes. De standaardwaarde is 64 GB.
* geheim: Slechts te gebruiken als het gebruiken van binaryless replicatie voor gedeelde datastore opstelling.
* stagingSplitPercentage: Het percentage van geheim voorgeheugengrootte die wordt gevormd om voor het opvoeren van asynchrone uploads te worden gebruikt. De standaardwaarde is 10.
* uploadThreads: Het aantal uploadthreads dat wordt gebruikt voor asynchrone uploads. De standaardwaarde is 10.
* stagingPurgeInterval: Het interval in seconden voor het leegmaken van voltooide uploads uit het opvoeren geheime voorgeheugen. De standaardwaarde is 300 seconden (5 minuten).
* stagingRetryInterval: Het interval voor opnieuw proberen in seconden voor mislukte uploads. De standaardwaarde is 600 seconden (10 minuten).

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

1. Ga naar de JMX-console op *https://&lt;serveradres:poort>/system/console/jmx*
1. Zoeken naar **RepositoryManagement.** Als u de gegevensopslagbeheerder MBean hebt gevonden, klikt u erop om de beschikbare opties weer te geven.
1. Blader naar het einde van de pagina en klik op de koppeling **startDataStoreGC(booleaanse markOnly)** .
1. Voer in het volgende dialoogvenster `false` de parameter in en klik op `markOnly` Invoke ****:

   ![chlimage_1-9](assets/chlimage_1-9.png)

   >[!NOTE]
   >
   >De `markOnly` parameter geeft aan of de sweep-fase van de afvalophaling wordt uitgevoerd of niet.

## De Inzameling van de Winkel van gegevens voor een Gedeelde Opslag van Gegevens {#data-store-garbage-collection-for-a-shared-data-store}

>[!NOTE]
>
>Wanneer het uitvoeren van huisvuilinzameling in een gegroepeerde of gedeelde opstelling van de gegevensopslag (met Mongo of Tar van het Segment) zou het logboek waarschuwingen over de onmogelijkheid kunnen tonen om bepaalde blob IDs te schrappen. Dit gebeurt omdat de blob IDs die in een vorige huisvuilinzameling worden geschrapt verkeerd opnieuw van verwijzingen wordt voorzien door andere cluster of gedeelde knopen die geen informatie over de schrappingen van identiteitskaart hebben. Dientengevolge, wanneer de huisvuilinzameling wordt uitgevoerd registreert het een waarschuwing wanneer het probeert om identiteitskaart te schrappen die reeds in de laatste looppas is geschrapt. Dit gedrag heeft geen invloed op prestaties of functionaliteit.

Met nieuwere versies van AEM, kan de inzameling van huisvuil van de gegevensopslag ook op gegevensopslag worden in werking gesteld die door meer dan één bewaarplaats wordt gedeeld. Voer de volgende stappen uit om de opschoning van gegevens op te slaan in een gedeelde gegevensopslag te kunnen uitvoeren:

1. Zorg ervoor dat om het even welke onderhoudstaken die voor de inzameling van huisvuil van de gegevensopslag worden gevormd op alle bewaarplaats instanties onbruikbaar worden gemaakt die de gegevensopslag delen.
1. Voer de stappen die in [Binary Garbage Collection](/help/sites-deploying/data-store-config.md#data-store-garbage-collection) individueel worden vermeld op **alle** gegevensopslaginstanties uit die de gegevensopslag delen. Zorg er echter voor dat u `true` voor de `markOnly` parameter invoert voordat u op de knop Invoke klikt:

   ![chlimage_1-10](assets/chlimage_1-10.png)

1. Nadat u de bovenstaande procedure in alle gevallen hebt voltooid, voert u de opschoonfunctie van het gegevensarchief opnieuw uit **een** van de volgende exemplaren:

   1. Ga naar de JMX-console en selecteer de Repository Manager Mbean.
   1. Klik op de **link Click startDataStoreGC(booleaanse markOnly)** .
   1. Voer in het volgende dialoogvenster nogmaals `false` voor de `markOnly` parameter in.

   Hiermee worden alle gevonden bestanden gesorteerd met behulp van de markeringsfase die voor is gebruikt en worden de overige bestanden die niet in de gegevensopslag worden gebruikt, verwijderd.

