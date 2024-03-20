---
title: RDBMS-ondersteuning in AEM 6.4
description: Leer over de relationele steun van de gegevensbestandpersistentie in AEM 6.4 en de beschikbare configuratieopties.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: 1e34c5ca-9e08-4b2a-901c-ab28aeb4a807
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# RDBMS-ondersteuning in AEM 6.4{#rdbms-support-in-aem}

## Overzicht {#overview}

Ondersteuning voor relationele databasedruk in AEM wordt geïmplementeerd via Document Microkernel. De Document Microkernel is de basis die ook wordt gebruikt voor de implementatie van MongoDB-persistentie.

Deze API bestaat uit een Java API die is gebaseerd op de API van Mongo Java. Er wordt ook een implementatie van een BlobStore-API geleverd. Standaard worden klodders opgeslagen in de database.

Voor meer informatie over de implementatiedetails raadpleegt u de [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) en [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) documentatie.

>[!NOTE]
>
>Ondersteuning voor **PostgreSQL 9.4** wordt ook verstrekt, maar alleen voor demo-doeleinden. Het zal niet beschikbaar voor productiemilieu&#39;s zijn.

## Ondersteunde databases {#supported-databases}

Voor meer informatie over het niveau van de Relationele Steun van het Gegevensbestand in AEM, zie [Pagina Technische vereisten](/help/sites-deploying/technical-requirements.md).

## Configuratiestappen {#configuration-steps}

De opslagplaats wordt gemaakt door de configuratie van de `DocumentNodeStoreService` OSGi-service. Naast MongoDB is de toepassing uitgebreid met ondersteuning voor relationele databasepersistentie.

Om het te werken, moet een gegevensbron met AEM worden gevormd. Dit gebeurt via de `org.apache.sling.datasource.DataSourceFactory.config` bestand. De bestuurders JDBC voor het respectieve gegevensbestand moeten afzonderlijk als bundels OSGi binnen de lokale configuratie worden verstrekt.

Voor stappen bij het creëren van bundels OSGi voor bestuurders JDBC, zie dit [documentatie](https://sling.apache.org/documentation/bundles/datasource-providers.html#convert-driver-jars-to-bundle) op de Apache Sling-website.

Nadat de bundels zijn geïnstalleerd, volgt u de onderstaande stappen om AEM te configureren met RDB-persistentie:

1. Zorg ervoor dat de databasdaemon is gestart en dat u een actieve database hebt voor gebruik met AEM.
1. Kopieer de AEM 6.3 jar in de installatiemap.
1. Een map maken met de naam `crx-quickstart\install` in de installatiemap.
1. Vorm de opslag van de documentknoop door een configuratiedossier met de volgende naam in te creëren `crx-quickstart\install` map:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Vorm de gegevensbron en de parameters JDBC door een ander configuratiedossier met de volgende naam in te creëren `crx-quickstart\install` map:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`

   >[!NOTE]
   >
   >Voor gedetailleerde informatie over de gegevensbronconfiguratie voor elke gesteunde gegevensbestand, zie [Configuratieopties gegevensbron](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. Bereid daarna de bundels JDBC OSGi voor die met AEM moeten worden gebruikt:

   1. In de `crx-quickstart/install` map, een map maken met de naam `9`.

   1. Plaats de jar JDBC in de nieuwe omslag.

1. Ten slotte begint u AEM met de `crx3` en `crx3rdb` runmodi:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Configuratieopties gegevensbron {#data-source-configuration-options}

De `org.apache.sling.datasource.DataSourceFactory-oak.config` De configuratie OSGi wordt gebruikt om de parameters te vormen nodig voor communicatie tussen AEM en de laag van de gegevensbestandpersistentie.

De volgende configuratieopties zijn beschikbaar:

* `datasource.name:` De naam van de gegevensbron. De standaardwaarde is `oak`.

* `url:` De URL-tekenreeks van de database die moet worden gebruikt met JDBC. Elk databasetype heeft een eigen URL-tekenreeksindeling. Zie voor meer informatie [Opmaak URL-tekenreeks](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) hieronder.

* `driverClassName:` De naam van de JDBC-stuurprogrammaklasse. Dit verschilt afhankelijk van de database die u wilt gebruiken en vervolgens van het stuurprogramma dat nodig is om verbinding met de database te maken. Hieronder ziet u de klassenamen voor alle databases die worden ondersteund door AEM:

   * `org.postgresql.Driver` voor PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` voor DB2;
   * `oracle.jdbc.OracleDriver` voor Oracle;
   * `com.mysql.jdbc.Driver` voor MySQL en MariaDB (experimenteel);
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` voor Microsoft SQL Server (experimenteel).

* `username:` De gebruikersnaam waaronder de database wordt uitgevoerd.

* `password:` Het databasewachtwoord.

### Opmaak URL-tekenreeks {#url-string-formats}

Afhankelijk van het databasetype dat moet worden gebruikt, wordt in de configuratie van de gegevensbron een andere indeling voor de URL-tekenreeks gebruikt. Hieronder volgt een lijst met indelingen voor de databases die momenteel AEM ondersteunen:

* `jdbc:postgresql:databasename` voor PostgreSQL;
* `jdbc:db2://localhost:port/databasename` voor DB2;
* `jdbc:oracle:thin:localhost:port:SID` voor Oracle;
* `jdbc:mysql://localhost:3306/databasename` voor MySQL en MariaDB (experimenteel);
* `jdbc:sqlserver://localhost:1453;databaseName=name` voor Microsoft SQL Server (experimenteel).

## Bekende beperkingen {#known-limitations}

Hoewel gelijktijdig gebruik van meerdere AEM instanties met één database wordt ondersteund door RDBMS-persistentie, zijn gelijktijdige installaties niet mogelijk.

Als u dit wilt omzeilen, moet u eerst de installatie uitvoeren met één lid en de andere leden toevoegen nadat de eerste installatie is voltooid.
