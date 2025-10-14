---
title: RDBMS-ondersteuning in AEM 6.4
description: Leer over de relationele steun van de gegevensbestandpersistentie in AEM 6.4 en de beschikbare configuratieopties.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
feature: Administering
exl-id: 1e34c5ca-9e08-4b2a-901c-ab28aeb4a807
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# RDBMS-ondersteuning in AEM 6.4{#rdbms-support-in-aem}

## Overzicht {#overview}

Ondersteuning voor relationele databasedruk in AEM wordt geïmplementeerd via Document Microkernel. De Document Microkernel is de basis die ook wordt gebruikt voor de implementatie van MongoDB-persistentie.

Deze API bestaat uit een Java API die is gebaseerd op de API van Mongo Java. Er wordt ook een implementatie van een BlobStore-API geleverd. Standaard worden klodders opgeslagen in de database.

Voor meer informatie over de implementatiedetails, zie [&#x200B; RDBDocumentStore &#x200B;](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) en [&#x200B; RDBBlobStore &#x200B;](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) documentatie.

>[!NOTE]
>
>De steun voor **PostgreSQL 9.4** wordt ook verstrekt, maar slechts voor demodoeleinden. Het zal niet beschikbaar voor productiemilieu&#39;s zijn.

## Ondersteunde databases {#supported-databases}

Voor meer informatie over het niveau van de Relationele steun van het Gegevensbestand in AEM, zie de [&#x200B; pagina van Technische Vereisten &#x200B;](/help/sites-deploying/technical-requirements.md).

## Configuratiestappen {#configuration-steps}

De gegevensopslagruimte wordt gemaakt door de `DocumentNodeStoreService` OSGi-service te configureren. Naast MongoDB is de toepassing uitgebreid met ondersteuning voor relationele databasepersistentie.

Om het te werken, moet een gegevensbron met AEM worden gevormd. Dit gebeurt via het `org.apache.sling.datasource.DataSourceFactory.config` -bestand. De bestuurders JDBC voor het respectieve gegevensbestand moeten afzonderlijk als bundels OSGi binnen de lokale configuratie worden verstrekt.

Voor stappen bij het creëren van bundels OSGi voor bestuurders JDBC, zie deze [&#x200B; documentatie &#x200B;](https://sling.apache.org/documentation/bundles/datasource-providers.html#convert-driver-jars-to-bundle) op de website van Apache Sling.

Nadat de bundels zijn geïnstalleerd, volgt u de onderstaande stappen om AEM te configureren met RDB-persistentie:

1. Zorg ervoor dat de databasdaemon is gestart en dat u een actieve database hebt voor gebruik met AEM.
1. Kopieer de AEM 6.3 jar in de installatiemap.
1. Maak een map met de naam `crx-quickstart\install` in de installatiemap.
1. Configureer de opslag van de documentnode door een configuratiebestand met de volgende naam in de map `crx-quickstart\install` te maken:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Configureer de gegevensbron en de JDBC-parameters door een ander configuratiebestand met de volgende naam in de map `crx-quickstart\install` te maken:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`

   >[!NOTE]
   >
   >Voor gedetailleerde informatie over de gegevensbronconfiguratie voor elk gesteund gegevensbestand, zie [&#x200B; de Opties van de Configuratie van Source van Gegevens &#x200B;](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. Bereid daarna de bundels JDBC OSGi voor die met AEM moeten worden gebruikt:

   1. Maak in de map `crx-quickstart/install` een map met de naam `9` .

   1. Plaats de jar JDBC in de nieuwe omslag.

1. Start ten slotte AEM met de runmodi `crx3` en `crx3rdb` :

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Source-configuratieopties voor gegevens {#data-source-configuration-options}

De `org.apache.sling.datasource.DataSourceFactory-oak.config` configuratie OSGi wordt gebruikt om de parameters te vormen nodig voor communicatie tussen AEM en de laag van de gegevensbestandpersistentie.

De volgende configuratieopties zijn beschikbaar:

* `datasource.name:` De naam van de gegevensbron. De standaardwaarde is `oak` .

* `url:` De URL-tekenreeks van de database die moet worden gebruikt met JDBC. Elk databasetype heeft een eigen URL-tekenreeksindeling. Voor meer info, zie {de Formaten van het Koord van 0} URL [&#128279;](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) hieronder.

* `driverClassName:` De naam van de JDBC-stuurprogrammaklasse. Dit verschilt afhankelijk van de database die u wilt gebruiken en vervolgens van het stuurprogramma dat nodig is om verbinding met de database te maken. Hieronder ziet u de klassenamen voor alle databases die worden ondersteund door AEM:

   * `org.postgresql.Driver` voor PostSQL;
   * `com.ibm.db2.jcc.DB2Driver` voor DB2;
   * `oracle.jdbc.OracleDriver` voor Oracle;
   * `com.mysql.jdbc.Driver` voor MySQL en MariaDB (experimenteel);
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` voor Microsoft SQL Server (experimenteel).

* `username:` De gebruikersnaam waaronder de database wordt uitgevoerd.

* `password:` Het databasewachtwoord.

### Opmaak URL-tekenreeks {#url-string-formats}

Afhankelijk van het databasetype dat moet worden gebruikt, wordt in de configuratie van de gegevensbron een andere indeling voor de URL-tekenreeks gebruikt. Hieronder volgt een lijst met indelingen voor de databases die momenteel AEM ondersteunen:

* `jdbc:postgresql:databasename` voor PostSQL;
* `jdbc:db2://localhost:port/databasename` voor DB2;
* `jdbc:oracle:thin:localhost:port:SID` voor Oracle;
* `jdbc:mysql://localhost:3306/databasename` voor MySQL en MariaDB (experimenteel);
* `jdbc:sqlserver://localhost:1453;databaseName=name` voor Microsoft SQL Server (experimenteel).

## Bekende beperkingen {#known-limitations}

Hoewel gelijktijdig gebruik van meerdere AEM instanties met één database wordt ondersteund door RDBMS-persistentie, zijn gelijktijdige installaties niet mogelijk.

Als u dit wilt omzeilen, moet u eerst de installatie uitvoeren met één lid en de andere leden toevoegen nadat de eerste installatie is voltooid.
