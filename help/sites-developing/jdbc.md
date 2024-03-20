---
title: Verbinding maken met SQL-databases
description: Open een externe SQL-database zodat uw AEM toepassingen met de gegevens kunnen werken
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 1082b2d7-2d1b-4c8c-a31d-effa403b21b2
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---

# Verbinding maken met SQL-databases{#connecting-to-sql-databases}

Open een externe SQL-database zodat uw CQ-toepassingen kunnen werken met de gegevens:

1. [Maak of verkrijg een OSGi-bundel die het JDBC-stuurprogrammapakket exporteert](#bundling-the-jdbc-database-driver).
1. [Een JDBC-aanbieder voor gegevensbrongroepen configureren](#configuring-the-jdbc-connection-pool-service).
1. [Haal een gegevensbronobject op en maak de verbinding in de code](#connecting-to-the-database).

## Het JDBC-databasestuurprogramma bundelen {#bundling-the-jdbc-database-driver}

Sommige gegevensbestandverkopers verstrekken bestuurders JDBC in een bundel OSGi, bijvoorbeeld, [MySQL](https://dev.mysql.com/downloads/connector/j/). Als het JDBC-stuurprogramma voor uw database niet beschikbaar is als OSGi-bundel, vraagt u het stuurprogramma JAR op en plaatst u deze in een OSGi-bundel. De bundel moet de pakketten uitvoeren die voor het in wisselwerking staan met de gegevensbestandserver worden vereist. De bundel moet ook de pakketten invoeren die het verwijzingen.

In het volgende voorbeeld wordt het [Plug-in voor bundel voor Maven](https://felix.apache.org/documentation/subprojects/apache-felix-maven-bundle-plugin-bnd.html) om het HSQLDB-stuurprogramma in een OSGi-bundel te plaatsen. De POM geeft de plug-in de opdracht het bestand hsqldb.jar dat als een afhankelijkheid is geïdentificeerd, in te sluiten. Alle org.hsqldb pakketten worden uitgevoerd.

De plug-in bepaalt automatisch welke pakketten u wilt importeren en geeft deze weer in het bestand MANIFEST.MF van de bundel. Als een van de pakketten niet beschikbaar is op de CQ-server, wordt de bundel niet gestart bij de installatie. Er zijn twee mogelijke oplossingen:

* Geef in de POM aan dat de verpakkingen optioneel zijn. Gebruik deze oplossing wanneer de verbinding JDBC eigenlijk niet de pakketleden vereist. Gebruik het element Import-Package om optionele pakketten aan te geven, zoals in het volgende voorbeeld:

  `<Import-Package>org.jboss.*;resolution:=optional,*</Import-Package>`
* Plaats de JAR-bestanden met de pakketten in een OSGi-bundel die de pakketten exporteert en implementeer de bundel. Gebruik deze oplossing wanneer de pakketleden tijdens code-uitvoering worden vereist.

Met kennis van de broncode kunt u bepalen welke oplossing u wilt gebruiken. U kunt ook een van beide oplossingen uitproberen en tests uitvoeren om de oplossing te valideren.

### POM dat hsqldb.jar bundelt {#pom-that-bundles-hsqldb-jar}

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>hsqldb-jdbc-driver-bundle</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <name>wrapper-bundle-hsqldb-driver</name>
  <url>www.adobe.com</url>
  <description>Exports the HSQL JDBC driver</description>
  <packaging>bundle</packaging>
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.felix</groupId>
        <artifactId>maven-bundle-plugin</artifactId>
        <version>1.4.3</version>
        <extensions>true</extensions>
        <configuration>
         <instructions>
            <Embed-Dependency>*</Embed-Dependency>
            <_exportcontents>org.hsqldb.*</_exportcontents>
          </instructions>
        </configuration>
      </plugin>
    </plugins>
  </build>
  <dependencies>
    <dependency>
      <groupId>hsqldb</groupId>
      <artifactId>hsqldb</artifactId>
      <version>2.2.9</version>
    </dependency>
  </dependencies>
</project>
```

Met de volgende koppelingen worden de downloadpagina&#39;s voor bepaalde populaire databaseproducten geopend:

* [Microsoft® SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
* [Oracle](https://www.oracle.com/database/technologies/appdev/jdbc-downloads.html)
* [IBM® DB2®](https://www.ibm.com/support/pages/download-db2-fix-packs-version-db2-linux-unix-and-windows)

### De JDBC Connection Pool Service configureren {#configuring-the-jdbc-connection-pool-service}

Voeg een configuratie voor de dienst van de Pool van Verbindingen JDBC toe die de bestuurder JDBC gebruikt om gegevensbronvoorwerpen tot stand te brengen. Uw toepassingscode gebruikt deze service om het object te verkrijgen en verbinding te maken met de database.

JDBC-verbindingspool ( `com.day.commons.datasource.jdbcpool.JdbcPoolService`) is een fabrieksservice. Als u verbindingen vereist die verschillende eigenschappen, bijvoorbeeld, read-only of read-write toegang gebruiken, creeer veelvoudige configuraties.

Wanneer het werken met CQ, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie.

De volgende eigenschappen zijn beschikbaar om een samengevoegde verbindingsdienst te vormen. De bezitsnamen zijn vermeld aangezien zij in de Console van het Web verschijnen. De corresponderende naam voor een `sling:OsgiConfig` knooppunt wordt tussen haakjes weergegeven. Voorbeeldwaarden worden weergegeven voor een HSQLDB-server en een database met een alias van `mydb`:

* JDBC-stuurprogramma, klasse ( `jdbc.driver.class`): De Java™-klasse waarmee de interface java.sql.Driver wordt geïmplementeerd, bijvoorbeeld `org.hsqldb.jdbc.JDBCDriver`. Het gegevenstype is `String`.

* JDBC-verbindingsURI ( `jdbc.connection.uri`): De URL van de database die moet worden gebruikt om de verbinding te maken, bijvoorbeeld `jdbc:hsqldb:hsql//10.36.79.223:9001/mydb`. De indeling van de URL moet geldig zijn voor gebruik met de methode getConnection van de klasse java.sql.DriverManager. Het gegevenstype is `String`.

* Gebruikersnaam ( `jdbc.username`): De gebruikersnaam die moet worden gebruikt voor verificatie met de databaseserver. Het gegevenstype is `String`.

* Wachtwoord ( `jdbc.password`): Het wachtwoord dat moet worden gebruikt voor verificatie van de gebruiker. Het gegevenstype is `String`.

* Validatiezoekopdracht ( `jdbc.validation.query`): De SQL-instructie die moet worden gebruikt om te controleren of de verbinding is gelukt, bijvoorbeeld `select 1 from INFORMATION_SCHEMA.SYSTEM_USERS`. Het gegevenstype is `String`.

* Alleen-lezen door standaard (default.readonly): selecteer deze optie als u wilt dat via de verbinding alleen-lezen toegang wordt verkregen. Het gegevenstype is `Boolean`.
* Standaard automatisch toewijzen ( `default.autocommit`): Selecteer deze optie om afzonderlijke transacties te maken voor elke SQL-opdracht die naar de database wordt verzonden en elke transactie automatisch wordt toegewezen. Selecteer deze optie niet wanneer u transacties expliciet in de code uitvoert. Het gegevenstype is `Boolean`.

* Pool Size ( `pool.size`): Het aantal gelijktijdige verbindingen dat ter beschikking van de database moet worden gesteld. Het gegevenstype is `Long`.

* Wachttijd pool ( `pool.max.wait.msec`): De hoeveelheid tijd voordat een verbindingsaanvraag wordt verzonden. Het gegevenstype is `Long`.

* Naam gegevensbron ( `datasource.name`): De naam van deze gegevensbron. Het gegevenstype is `String`.

* Aanvullende serviceeigenschappen ( `datasource.svc.properties`): Een set naam-/waardeparen die u aan de verbindings-URL wilt toevoegen. Het gegevenstype is `String[]`.

De service van de JDBC-verbindingspool is een fabriek. Daarom moet u een `sling:OsgiConfig` knoop om de verbindingsdienst te vormen, moet de naam van de knoop de fabrieksdienst PID omvatten die door wordt gevolgd *`-alias`*. De alias die u gebruikt moet uniek zijn voor alle configuratieknooppunten voor die PID. Een voorbeeldknooppuntnaam is `com.day.commons.datasource.jdbcpool.JdbcPoolService-myhsqldbpool`.

![chlimage_1-7](assets/chlimage_1-7a.png)

### Verbinding maken met de database {#connecting-to-the-database}

Gebruik in uw Java™-code de DataSourcePool-service om een `javax.sql.DataSource` object voor de configuratie die u hebt gemaakt. De dienst DataSourcePool verstrekt `getDataSource` methode die een `DataSource` -object voor een bepaalde gegevensbronnaam. Als methodeargument, gebruik de waarde van de Naam Datasource (of `datasource.name`) die u hebt opgegeven voor de configuratie van de JDBC-verbindingspool.

In het volgende voorbeeld verkrijgt JSP-code een instantie van de hsqldbds-gegevensbron, wordt een eenvoudige SQL-query uitgevoerd en wordt het aantal geretourneerde resultaten weergegeven.

#### JSP die een gegevensbestandraadpleging uitvoert {#jsp-that-performs-a-database-lookup}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false"%><%
%><%@ page import="com.day.commons.datasource.poolservice.DataSourcePool" %><%
%><%@ page import="javax.sql.DataSource" %><%
%><%@ page import="java.sql.Connection" %><%
%><%@ page import="java.sql.SQLException" %><%
%><%@ page import="java.sql.Statement" %><%
%><%@ page import="java.sql.ResultSet"%><%
%><html>
<cq:include script="head.jsp"/>
<body>
<%DataSourcePool dspService = sling.getService(DataSourcePool.class);
  try {
     DataSource ds = (DataSource) dspService.getDataSource("hsqldbds");
     if(ds != null) {
         %><p>Obtained the datasource!</p><%
         %><%final Connection connection = ds.getConnection();
          final Statement statement = connection.createStatement();
          final ResultSet resultSet = statement.executeQuery("SELECT * from INFORMATION_SCHEMA.SYSTEM_USERS");
          int r=0;
          while(resultSet.next()){
             r=r+1;
          }
          resultSet.close();
          %><p>Number of results: <%=r%></p><%
      }
   }catch (Exception e) {
        %><p>error! <%=e.getMessage()%></p><%
    }
%></body>
</html>
```

>[!NOTE]
>
>Als de methode getDataSource een uitzondering werpt omdat de gegevensbron niet wordt gevonden, zorg ervoor dat de de dienstconfiguratie van de Pool van Verbindingen correct is. Controleer de eigenschapnamen, waarden en gegevenstypen.
>

<!-- Link below redirects to the "Get started with AEM Sites - WKND tutorial"
>[!NOTE]
>
>To learn how to inject a DataSourcePool into an OSGi bundle, see [Injecting a DataSourcePool Service into an Adobe Experience Manager OSGi bundle](https://helpx.adobe.com/experience-manager/using/datasourcepool.html). -->
