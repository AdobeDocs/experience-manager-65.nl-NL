---
title: RDBMS-ondersteuning in AEM 6.4
seo-title: RDBMS-ondersteuning in AEM 6.4
description: Leer over de relationele steun van de gegevensbestandpersistentie in AEM 6.4 en de beschikbare configuratieopties.
seo-description: Leer over de relationele steun van de gegevensbestandpersistentie in AEM 6.4 en de beschikbare configuratieopties.
uuid: c8422b0d-c6df-488d-bb6a-af92c9afda50
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 6a754d42-da30-4c2f-8b9c-369e1f1f92b5
docset: aem65
translation-type: tm+mt
source-git-commit: 38ef8fc8d80009c8ca79aca9e45cf10bd70e1f1e

---


# RDBMS-ondersteuning in AEM 6.4{#rdbms-support-in-aem}

## Overzicht {#overview}

Ondersteuning voor relationele databasedruk in AEM wordt geïmplementeerd met behulp van Document Microkernel. De Document Microkernel is de basis die ook wordt gebruikt voor de implementatie van MongoDB-persistentie.

Deze API bestaat uit een Java API die is gebaseerd op de API van Mongo Java. Er wordt ook een implementatie van een BlobStore-API geleverd. Standaard worden klodders opgeslagen in de database.

Raadpleeg de documentatie bij [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) en [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) voor meer informatie over de implementatiedetails.

>[!NOTE]
>
>Er wordt ook ondersteuning voor **PostgreSQL 9.4** geboden, maar alleen voor demo-doeleinden. Het zal niet beschikbaar voor productiemilieu&#39;s zijn.

## Ondersteunde databases {#supported-databases}

Voor meer informatie over het niveau van de Relationele Steun van het Gegevensbestand in AEM, gelieve de pagina [van de](/help/sites-deploying/technical-requirements.md)Technische Eisen te zien.

## Configuratiestappen {#configuration-steps}

De bewaarplaats wordt gecreeerd door de dienst te vormen `DocumentNodeStoreService` OSGi. Naast MongoDB is de toepassing uitgebreid met ondersteuning voor relationele databasepersistentie.

Om het te werken, moet een gegevensbron met AEM worden gevormd. Dit gebeurt via het `org.apache.sling.datasource.DataSourceFactory.config` bestand. De bestuurders JDBC voor het respectieve gegevensbestand moeten afzonderlijk als bundels OSGi binnen de lokale configuratie worden verstrekt.

Voor stappen voor het maken van OSGi-bundels voor JDBC-stuurprogramma&#39;s raadpleegt u deze [documentatie](https://sling.apache.org/documentation/bundles/datasource-providers.html#convert-driver-jars-to-bundle) op de Apache Sling-website.

Nadat de bundels zijn geïnstalleerd, volgt u de onderstaande stappen om AEM te configureren met RDB-persistentie:

1. Zorg ervoor dat de databasedaemon is gestart en dat u een actieve database hebt voor gebruik met AEM.
1. Kopieer AEM 6.3 jar in de installatiemap.
1. Maak een map met de naam `crx-quickstart\install` in de installatiemap.
1. Configureer de opslag van de documentnode door een configuratiebestand met de volgende naam in de `crx-quickstart\install` map te maken:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Vorm de gegevensbron en de parameters JDBC door een ander configuratiedossier met de volgende naam in de `crx-quickstart\install` omslag te creëren:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >Voor gedetailleerde informatie over de gegevensbronconfiguratie voor elke gesteunde gegevensbestand, zie de Opties [van de Configuratie van de](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options)Gegevensbron.

1. Bereid de JDBC OSGi-bundels voor die met AEM moeten worden gebruikt:

   1. Maak in de `crx-quickstart/install` map een map met de naam `9`.

   1. Plaats de jar JDBC in de nieuwe omslag.

1. Start AEM ten slotte met de `crx3` en de `crx3rdb` runmodi:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Configuratieopties gegevensbron {#data-source-configuration-options}

De configuratie `org.apache.sling.datasource.DataSourceFactory-oak.config` OSGi wordt gebruikt om de parameters te vormen nodig voor communicatie tussen AEM en de laag van de gegevensbestandpersistentie.

De volgende configuratieopties zijn beschikbaar:

* `datasource.name:` De naam van de gegevensbron. The default is `oak`.

* `url:` De URL-tekenreeks van de database die moet worden gebruikt met JDBC. Elk databasetype heeft een eigen URL-tekenreeksindeling. Zie [URL-tekenreeksindelingen](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) hieronder voor meer informatie.

* `driverClassName:` De naam van de JDBC-stuurprogrammaklasse. Dit verschilt afhankelijk van de database die u wilt gebruiken en vervolgens van het stuurprogramma dat nodig is om verbinding met de database te maken. Hieronder ziet u de klassenamen voor alle databases die door AEM worden ondersteund:

   * `org.postgresql.Driver` voor PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` voor DB2;
   * `oracle.jdbc.OracleDriver` voor Oracle;
   * `com.mysql.jdbc.Driver` voor MySQL en MariaDB (experimenteel);
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` voor Microsoft SQL Server (experimenteel).

* `username:` De gebruikersnaam waaronder de database wordt uitgevoerd.

* `password:` Het databasewachtwoord.

### Opmaak URL-tekenreeks {#url-string-formats}

Afhankelijk van het databasetype dat moet worden gebruikt, wordt in de configuratie van de gegevensbron een andere indeling voor de URL-tekenreeks gebruikt. Hieronder volgt een lijst met indelingen voor de databases die momenteel door AEM worden ondersteund:

* `jdbc:postgresql:databasename` voor PostgreSQL;
* `jdbc:db2://localhost:port/databasename` voor DB2;
* `jdbc:oracle:thin:localhost:port:SID` voor Oracle;
* `jdbc:mysql://localhost:3306/databasename` voor MySQL en MariaDB (experimenteel);
* `jdbc:sqlserver://localhost:1453;databaseName=name` voor Microsoft SQL Server (experimenteel).

## Bekende beperkingen {#known-limitations}

Hoewel het gelijktijdige gebruik van meerdere AEM-instanties met één database wordt ondersteund door RDBMS-persistentie, zijn gelijktijdige installaties niet mogelijk.

Als u dit wilt omzeilen, moet u eerst de installatie uitvoeren met één lid en de andere leden toevoegen nadat de eerste installatie is voltooid.

