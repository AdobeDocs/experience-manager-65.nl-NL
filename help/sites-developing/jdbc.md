---
title: Verbinding maken met SQL-databases
seo-title: Verbinding maken met SQL-databases
description: Open een externe SQL-database zodat uw AEM-toepassingen kunnen communiceren met de gegevens
seo-description: Open een externe SQL-database zodat uw AEM-toepassingen kunnen communiceren met de gegevens
uuid: 0af0ed08-9487-4c37-87ce-049c9b4c1ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 11a11803-bce4-4099-9b50-92327608f37b
translation-type: tm+mt
source-git-commit: b3e1493811176271ead54bae55b1cd0cf759fe71

---


# Verbinding maken met SQL-databases{#connecting-to-sql-databases}

Open een externe SQL-database zodat uw CQ-toepassingen kunnen werken met de gegevens:

1. [Maak of verkrijg een OSGi-bundel die het JDBC-stuurprogrammapakket](#bundling-the-jdbc-database-driver)exporteert.
1. [Configureer een JDBC-leverancier](#configuring-the-jdbc-connection-pool-service)van gegevensbrongroepen.
1. [Haal een gegevensbronobject op en maak de verbinding in de code](#connecting-to-the-database).

## Het JDBC-databasestuurprogramma bundelen {#bundling-the-jdbc-database-driver}

Sommige gegevensbestandverkopers verstrekken bestuurders JDBC in een bundel OSGi, bijvoorbeeld [MySQL](https://www.mysql.com/downloads/connector/j/). Als het JDBC-stuurprogramma voor uw database niet beschikbaar is als OSGi-bundel, vraagt u het stuurprogramma JAR op en plaatst u deze in een OSGi-bundel. De bundel moet de pakketten uitvoeren die voor het in wisselwerking staan met de gegevensbestandserver worden vereist. De bundel moet ook de pakketten invoeren die het verwijzingen.

In het volgende voorbeeld wordt de [bundelplug-in voor Maven](https://felix.apache.org/site/apache-felix-maven-bundle-plugin-bnd.html) gebruikt om het HSQLDB-stuurprogramma in een OSGi-bundel te plaatsen. De POM geeft de plug-in de opdracht het bestand hsqldb.jar dat als een afhankelijkheid is geïdentificeerd, in te sluiten. Alle org.hsqldb-pakketten worden geëxporteerd.

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

* [Microsoft SQL Server](https://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=11774)
* [Oracle](https://www.oracle.com/technetwork/database/features/jdbc/index-091264.html)
* [IBM DB2](https://www-01.ibm.com/support/docview.wss?uid=swg27007053)

### De JDBC Connection Pool Service configureren {#configuring-the-jdbc-connection-pool-service}

Voeg een configuratie voor de dienst van de Pool van Verbindingen JDBC toe die de bestuurder JDBC gebruikt om gegevensbronvoorwerpen tot stand te brengen. Uw toepassingscode gebruikt deze service om het object te verkrijgen en verbinding te maken met de database.

JDBC-verbindingspool ( `com.day.commons.datasource.jdbcpool.JdbcPoolService`) is een fabrieksservice. Als u verbindingen vereist die verschillende eigenschappen, bijvoorbeeld read-only of lees-schrijftoegang gebruiken, creeer veelvoudige configuraties.

Bij het werken met CQ zijn er verschillende methoden om de configuratie-instellingen voor dergelijke services te beheren. zie het [Vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor volledige details.

De volgende eigenschappen zijn beschikbaar om een samengevoegde verbindingsdienst te vormen. De bezitsnamen zijn vermeld aangezien zij in de Console van het Web verschijnen. De corresponderende naam voor een `sling:OsgiConfig` knooppunt wordt tussen haakjes weergegeven. Voorbeelden van waarden worden weergegeven voor een HSQLDB-server en een database met een alias van `mydb`:

* JDBC-stuurprogramma-klasse ( `jdbc.driver.class`): De Java-klasse die moet worden gebruikt om de interface java.sql.Driver uit te voeren, bijvoorbeeld `org.hsqldb.jdbc.JDBCDriver`. Het gegevenstype is `String`.

* URI JDBC-verbinding ( `jdbc.connection.uri`): De URL van de database die moet worden gebruikt om de verbinding te maken, bijvoorbeeld `jdbc:hsqldb:hsql//10.36.79.223:9001/mydb`. De indeling van de URL moet geldig zijn voor gebruik met de methode getConnection van de klasse java.sql.DriverManager. Het gegevenstype is `String`.

* Gebruikersnaam ( `jdbc.username`): De gebruikersnaam die moet worden gebruikt voor verificatie met de databaseserver. Het gegevenstype is `String`.

* Wachtwoord ( `jdbc.password`): Het wachtwoord dat moet worden gebruikt voor verificatie van de gebruiker. Het gegevenstype is `String`.

* Validatiezoekopdracht ( `jdbc.validation.query`): De SQL-instructie die moet worden gebruikt om te controleren of de verbinding is gelukt, bijvoorbeeld `select 1 from INFORMATION_SCHEMA.SYSTEM_USERS`. Het gegevenstype is `String`.

* Standaard-lezen (default.readonly): Selecteer deze optie als u wilt dat de verbinding alleen-lezen toegang biedt. Het gegevenstype is `Boolean`.
* Standaard automatisch doorvoeren ( `default.autocommit`): Selecteer deze optie om afzonderlijke transacties te maken voor elke SQL-opdracht die naar de database wordt verzonden en elke transactie automatisch wordt toegewezen. Selecteer deze optie niet wanneer u transacties expliciet in de code uitvoert. Het gegevenstype is `Boolean`.

* Poolgrootte ( `pool.size`): Het aantal gelijktijdige verbindingen dat ter beschikking moet worden gesteld aan het gegevensbestand. Het gegevenstype is `Long`.

* Wachttijd pool ( `pool.max.wait.msec`): De hoeveelheid tijd voordat een verbindingsverzoek wordt verzonden. Het gegevenstype is `Long`.

* Naam gegevensbron ( `datasource.name`): De naam van deze gegevensbron. Het gegevenstype is `String`.

* Aanvullende serviceeigenschappen ( `datasource.svc.properties`): Een set naam-/waardeparen die u aan de verbindings-URL wilt toevoegen. Het gegevenstype is `String[]`.

De service van de JDBC-verbindingspool is een fabriek. Daarom als u een `sling:OsgiConfig` knoop gebruikt om de verbindingsdienst te vormen, moet de naam van de knoop de fabrieksdienst PID omvatten die door *`-alias`*. wordt gevolgd. De alias die u gebruikt moet uniek zijn voor alle configuratienamen voor die PID. De naam van een voorbeeldknooppunt is `com.day.commons.datasource.jdbcpool.JdbcPoolService-myhsqldbpool`.

![chlimage_1-7](assets/chlimage_1-7a.png)

### Verbinding maken met de database {#connecting-to-the-database}

In uw code van Java, gebruik de dienst DataSourcePool om een `javax.sql.DataSource` voorwerp voor de configuratie te verkrijgen die u creeerde. De dienst DataSourcePool verstrekt de `getDataSource` methode die een `DataSource` voorwerp voor een bepaalde gegevensbronnaam terugkeert. Als methodeargument, gebruik de waarde van het bezit van de Naam Datasource (of `datasource.name`) dat u voor de configuratie van de Pool van Verbindingen JDBC specificeerde.

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
>Als de methode getDataSource een uitzondering werpt omdat de gegevensbron niet wordt gevonden, zorg ervoor de de dienstconfiguratie van de Pool van Verbindingen correct is. Verifieer de bezitsnamen, de waarden, en de gegevenstypes.


>[!NOTE]
>
>Leer hoe te om een DataSourcePool in een bundel te injecteren OSGi, zie het [Injecteren van een Dienst DataSourcePool in een bundel](https://helpx.adobe.com/experience-manager/using/datasourcepool.html)van de Manager van de Ervaring OSGi van Adobe.

