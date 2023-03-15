---
title: Opslagelementen in AEM 6.5
seo-title: Storage Elements in AEM 6.5
description: Leer over de implementaties van de knoopopslag beschikbaar in AEM 6.5 en hoe te om de bewaarplaats te handhaven.
seo-description: Learn about the node storage implementations available in AEM 6.5 and how to maintain the repository.
uuid: 3b018830-c42e-48e0-9b6f-cd230b02d914
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0aa2c22f-32bb-4e50-8328-63ed73c0f19e
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
exl-id: 52437eb5-f9fb-4945-9950-5a1562fe878d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---

# Opslagelementen in AEM 6.5{#storage-elements-in-aem}

In dit artikel zullen wij het volgende behandelen:

* [Overzicht van opslag in AEM 6](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Behoud van de opslagplaats](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## Overzicht van opslag in AEM 6 {#overview-of-storage-in-aem}

Een van de belangrijkste wijzigingen in AEM 6 zijn de innovaties op het niveau van de opslagplaats.

Momenteel zijn er twee knoopopslagimplementaties beschikbaar in AEM6: Taaropslag en MongoDB-opslag.

### Teeropslag {#tar-storage}

#### Een nieuw geïnstalleerd AEM met Tar Storage uitvoeren {#running-a-freshly-installed-aem-instance-with-tar-storage}

>[!CAUTION]
>
>De PID voor de de knoopopslag van het Segment is veranderd van org.apache.jackrabbit.oak.**plug-ins**.segment.SegmentNodeStoreService in vorige versies van AEM 6 aan org.apache.jackrabbit.oak.segment.SegmentNodeStoreService in AEM 6.3. Zorg ervoor u de noodzakelijke configuratieaanpassingen aanbrengt om deze verandering te weerspiegelen.

Standaard gebruikt AEM 6 de Tar-opslag om knooppunten en binaire bestanden op te slaan met de standaardconfiguratieopties. Volg de onderstaande procedure om de opslaginstellingen handmatig te configureren:

1. Download de AEM 6 quickstart jar en plaats deze in een nieuwe map.
1. AEM uitpakken door uit te voeren:

   `java -jar cq-quickstart-6.jar -unpack`

1. Een map maken met de naam `crx-quickstart\install` in de installatiemap.

1. Een bestand maken met de naam `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg` in de nieuwe map.

1. Bewerk het bestand en stel de configuratieopties in. De volgende opties zijn beschikbaar voor de Opslag van de Knoop van het Segment, die de basis van AEM de opslagimplementatie van de Tar is:

   * `repository.home`: Pad naar de thuislocatie van de gegevensopslagruimte waarin verschillende gegevens met betrekking tot de gegevensopslagruimte worden opgeslagen. Standaard worden segmentbestanden opgeslagen onder de map crx-quickstart/segmentstore.
   * `tarmk.size`: Maximale grootte van een segment in MB. De standaardwaarde is 256 MB.

1. Start AEM.

### Mongo-opslag {#mongo-storage}

#### Een nieuw geïnstalleerd AEM-exemplaar uitvoeren met Mongo Storage {#running-a-freshly-installed-aem-instance-with-mongo-storage}

AEM 6 kan worden geconfigureerd voor gebruik met MongoDB-opslag door de onderstaande procedure te volgen:

1. Download de AEM 6 QuickStart jar en plaats deze in een nieuwe map.
1. AEM uitpakken door de volgende opdracht uit te voeren:

   `java -jar cq-quickstart-6.jar -unpack`

1. Controleer of MongoDB is geïnstalleerd en of `mongod` wordt uitgevoerd. Zie voor meer informatie [MongoDB installeren](https://docs.mongodb.org/manual/installation/).
1. Een map maken met de naam `crx-quickstart\install` in de installatiemap.
1. Vorm de knoopopslag door een configuratiedossier met de naam van de configuratie te creëren u in wilt gebruiken `crx-quickstart\install` directory.

   De Document Node Store (die de basis voor AEM MongoDB opslagimplementatie) is gebruikt een dossier genoemd `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.cfg`

1. Bewerk het bestand en stel de configuratieopties in. De volgende opties zijn beschikbaar:

   * `mongouri`: De [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/) vereist om verbinding te maken met de Mongo-database. De standaardwaarde is `mongodb://localhost:27017`
   * `db`: Naam van de Mongo-database. Standaard gebruiken nieuwe AEM 6 installaties **aem-auteur** als de databasenaam.
   * `cache`: De cachegrootte in MB. Dit wordt verdeeld over diverse geheime voorgeheugens die in DocumentNodeStore worden gebruikt. De standaardwaarde is 256.
   * `changesSize`: Grootte in MB van afgekapte inzameling die in Mongo wordt gebruikt voor caching van de diff output. De standaardwaarde is 256.
   * `customBlobStore`: Een Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. De standaardwaarde is false.

1. Maak een configuratiebestand met de PID van de gegevensopslagruimte die u wilt gebruiken en bewerk het bestand om de configuratieopties in te stellen. Zie voor meer informatie [Knooppuntenwinkels en gegevensopslag configureren](/help/sites-deploying/data-store-config.md).

1. Start de AEM 6-jar met een MongoDB-opslagback-end door deze uit te voeren:

   ```shell
   java -jar cq-quickstart-6.jar -r crx3,crx3mongo
   ```

   Wanneer **`-r`** is de achterste runmode. In dit voorbeeld begint het programma met ondersteuning voor MongoDB.

#### Transparante grote pagina&#39;s uitschakelen {#disabling-transparent-huge-pages}

Red Hat Linux gebruikt een algoritme van het geheugenbeheer genoemd Transparante Grote Pagina&#39;s (THP). Terwijl AEM fijnkorrelige leest en schrijft uitvoert, wordt THP geoptimaliseerd voor grote verrichtingen. Daarom wordt u aangeraden THP zowel op Tar- als op Mongo-opslag uit te schakelen. Voer de volgende stappen uit om het algoritme uit te schakelen:

1. Open de `/etc/grub.conf` in de teksteditor van uw keuze.
1. Voeg de volgende regel toe aan de **grub.conf** bestand:

   ```
   transparent_hugepage=never
   ```

1. Tot slot controleert u of de instelling van kracht is geworden door:

   ```
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Als THP is uitgeschakeld, moet de uitvoer van de bovenstaande opdracht als volgt zijn:

   ```
   always madvise [never]
   ```

>[!NOTE]
>
>Daarnaast kunt u ook de volgende bronnen raadplegen:
>
>* Voor meer informatie over transparante grote pagina&#39;s op Red Hat Linux raadpleegt u deze [artikel](https://access.redhat.com/solutions/46111).
>* Voor Linux-tuningtips raadpleegt u deze [artikel](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html).
>


## Behoud van de opslagplaats {#maintaining-the-repository}

Bij elke update van de opslagplaats wordt een nieuwe inhoudsrevisie gemaakt. Als gevolg hiervan neemt de grootte van de gegevensopslagruimte bij elke update toe. Om ongecontroleerde groei van opslagplaatsen te voorkomen, moeten oude revisies worden opgeschoond tot vrije schijfmiddelen. Deze onderhoudsfunctionaliteit wordt Revision Cleanup genoemd. Het correctiemechanisme van de Revisie zal schijfruimte terugwinnen door verouderde gegevens uit de bewaarplaats te verwijderen. Voor meer informatie over Revision Cleanup leest u de [Pagina Revisie opschonen](/help/sites-deploying/revision-cleanup.md).
