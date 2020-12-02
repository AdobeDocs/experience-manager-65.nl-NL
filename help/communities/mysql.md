---
title: MySQL-configuratie voor functies van Enablement
seo-title: MySQL-configuratie voor functies van Enablement
description: Uw MySQL-server verbinden
seo-description: Uw MySQL-server verbinden
uuid: e02d9404-de75-4fdb-896c-ea3f64f980a3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9222bc93-c231-4ac8-aa28-30d784a4ca3b
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 1%

---


# MySQL Configuration for Enablement Features {#mysql-configuration-for-enablement-features}

MySQL is een relationele database die voornamelijk wordt gebruikt voor het bijhouden en rapporteren van SCORM-gegevens voor actiemiddelen. Ingesloten tabellen zijn tabellen voor andere functies, zoals het bijhouden van een pauze/resume.

Deze instructies beschrijven hoe te met de server te verbinden MySQL, het enablement gegevensbestand te vestigen, en het gegevensbestand met aanvankelijke gegevens te bevolken.

## Vereisten {#requirements}

Voordat u MySQL voor de functie enablement van Communities configureert, moet u

* Installeer [MySQL server](https://dev.mysql.com/downloads/mysql/) Community Server versie 5.6:
   * Versie 5.7 wordt niet ondersteund voor SCORM.
   * Kan dezelfde server zijn als AEM instantie van de auteur.
* Installeer bij alle AEM het officiële [JDBC-stuurprogramma voor MySQL](deploy-communities.md#jdbc-driver-for-mysql).
* Installeer [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/).
* Installeer het [SCORM-pakket](enablement.md#scorm) op alle AEM.

## MySQL {#installing-mysql} installeren

MySQL moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

### Tabelnamen van kleine letters {#lower-case-table-names}

Aangezien SQL niet hoofdlettergevoelig is, is het voor hoofdlettergevoelige besturingssystemen nodig om de instelling voor kleine letters in te voeren voor alle tabelnamen.

Als u bijvoorbeeld alle tabelnamen met kleine letters wilt opgeven op een Linux-besturingssysteem:

* Bestand `/etc/my.cnf` bewerken
* Voeg in de sectie `[mysqld]` de volgende regel toe: `lower_case_table_names = 1`

### UTF8-tekenset {#utf-character-set}

Voor betere meertalige ondersteuning is het nodig de tekenset UTF8 te gebruiken.

Wijzig MySQL om UTF8 in te stellen als tekenset:
* mysql > SET NAMES &#39;utf8&#39;;

Wijzig de MySQL-database in de standaardwaarde voor UTF8:
* Bestand `/etc/my.cnf` bewerken
* Voeg in de sectie `[client]` het volgende toe: `default-character-set=utf8`
* Voeg in de sectie `[mysqld]` het volgende toe: `character-set-server=utf8`

## MySQL Workbench {#installing-mysql-workbench} installeren

MySQL Workbench biedt een UI voor het uitvoeren van SQL-scripts die het schema en de initiële gegevens installeren.

MySQL Workbench moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

## Verbinding {#enablement-connection} inschakelen

Als de MySQL Workbench voor het eerst wordt gestart, tenzij deze al voor andere doeleinden wordt gebruikt, worden er nog geen verbindingen weergegeven:

![mysqlconnection](assets/mysqlconnection.png)

### Nieuwe verbindingsinstellingen {#new-connection-settings}

1. Selecteer het plusteken (+) rechts van `MySQL Connections`.
1. In de dialoog `Setup New Connection`, ga waarden aangewezen voor uw platform voor demonstratiedoeleinden, met de auteur AEM instantie en MySQL op de zelfde server in:
   * Verbindingsnaam: `Enablement`
   * Verbindingsmethode: `Standard (TCP/IP)`
   * Hostnaam: `127.0.0.1`
   * Gebruikersnaam: `root`
   * Wachtwoord: `no password by default`
   * Standaardschema: `leave blank`
1. Selecteer `Test Connection` om de verbinding aan de lopende dienst te verifiëren MySQL.

**Opmerkingen**:
* De standaardpoort is `3306`.
* De gekozen `Connection Name` wordt ingevoerd als `datasource` naam in [JDBC OSGi configuratie](#configure-jdbc-connections).

#### Succesvolle verbinding {#successful-connection}

![mysqlconnection1](assets/mysqlconnection1.png)

#### Nieuwe schakelingsverbinding {#new-enablement-connection}

![mysqlconnection2](assets/mysqlconnection2.png)

## Database-instelling {#database-setup}

Bij het openen van de nieuwe verbinding Enablement, merk op dat er een testschema en standaardgebruikersrekeningen zijn.

![database instellen](assets/database-setup.png)

### SQL-scripts ophalen {#obtain-sql-scripts}

De SQL manuscripten worden verkregen gebruikend CRXDE Lite op de auteursinstantie. Het [SCORM-pakket](deploy-communities.md#scorm) moet worden geïnstalleerd:

1. Bladeren naar CRXDE Lite:
   * Bijvoorbeeld [http://localhost:4502/crx/de](http://localhost:4502/crx/de)
1. De map `/libs/social/config/scorm/` uitvouwen
1. `database_scormengine.sql` downloaden
1. `database_scorm_integration.sql` downloaden

![sqlscripts](assets/sqlscripts.png)

Eén methode voor het downloaden van het schema is:

* Selecteer de `jcr:content` knoop voor het sql dossier.
* Merk op de waarde voor het `jcr:data` bezit een meningsverbinding is.
* Selecteer de weergavekoppeling om de gegevens in een lokaal bestand op te slaan.

### SCORM-database {#create-scorm-database} maken

De toe te voegen SCORM-database is:

* name: `ScormEngineDB`
* gemaakt van scripts:
   * schema: `database_scormengine.sql`
   * gegevens: `database_scorm_integration.sql`
Voer de onderstaande stappen uit (
[openen](#step-open-sql-file),  [uitvoeren](#step-execute-sql-script)) om elk  [SQL-script](#obtain-sql-scripts)  te installeren. [Vernieuw indien nodig ](#refresh) om de resultaten van de uitvoering van het script te zien.

Installeer het schema voordat u de gegevens installeert.

>[!CAUTION]
>
>Als de databasenaam is gewijzigd, moet u deze correct opgeven in:
>
>* [JDBC-configuratie](#configure-jdbc-connections)
>* [SCORM-configuratie](#configure-scorm)


#### Stap 1: SQL-bestand {#step-open-sql-file} openen

In MySQL Workbench

* Via het keuzemenu Bestand
* Selecteer `Open SQL Script ...`
* Selecteer in deze volgorde een van de volgende opties:
   1. `database_scormengine.sql`
   1. `database_scorm_integration.sql`

![scrom-database](assets/scrom-database.png)

#### Stap 2: SQL-script uitvoeren {#step-execute-sql-script}

Selecteer `lightening (flash) icon` in het Workbench-venster voor het bestand dat in Stap 1 wordt geopend om het script uit te voeren.

Merk op dat de uitvoering van het `database_scormengine.sql` manuscript om het SCORM gegevensbestand tot stand te brengen een minuut kan vergen om te voltooien.

![scrom-database1](assets/scrom-database1.png)

#### Vernieuwen {#refresh}

Zodra de manuscripten worden uitgevoerd, is het noodzakelijk om `SCHEMAS` sectie van `Navigator` te verfrissen om het nieuwe gegevensbestand te zien. Gebruik het vernieuwingspictogram rechts van &#39;SCHEMAS&#39;:

![scrom-database2](assets/scrom-database2.png)

#### Resultaat: scormenginedb {#result-scormenginedb}

Na het installeren en vernieuwen van SCHEMAS, zal `scormenginedb` zichtbaar zijn.

![scrom-database3](assets/scrom-database3.png)

## JDBC-verbindingen configureren {#configure-jdbc-connections}

De configuratie OSGi voor **de Pool van Verbindingen JDBC van de Bevelen van de Dag** vormt de Bestuurder MySQL JDBC.

Alle publicatie- en auteur-AEM moeten verwijzen naar dezelfde MySQL-server.

Wanneer MySQL op een server verschillend van AEM loopt, moet server hostname in plaats van &quot;localhost&quot;in de schakelaar worden gespecificeerd JDBC (die [ScormEngine](#configurescormengineservice) config bevolkt).

* Op elke auteur en publiceer AEM instantie
* Aangemeld met beheerdersrechten
* Toegang tot de [webconsole](../../help/sites-deploying/configuring-osgi.md)
   * Bijvoorbeeld [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* `Day Commons JDBC Connections Pool` zoeken
* Selecteer het `+` pictogram om een nieuwe configuratie tot stand te brengen

   ![jdbcconnection1](assets/jdbcconnection1.png)

* Voer de volgende waarden in:
   * **[!UICONTROL JDBC driver class]**: `com.mysql.jdbc.Driver`
   * **DBC-verbindingsURIJ**:  `jdbc:mysql://localhost:3306/aem63reporting` Geef server op in plaats van localhost als MySQL-server niet hetzelfde is als &#39;this&#39;-AEM.
   * **[!UICONTROL Username]**: De wortel of gaat de gevormde Gebruikersnaam voor de server MySQL, als niet &quot;wortel&quot;in.
   * **[!UICONTROL Password]**: Wis dit gebied als geen wachtwoord dat voor MySQL wordt geplaatst, anders het gevormde wachtwoord voor de Gebruikersnaam MySQL ingaat.
   * **[!UICONTROL Datasource name]**: Naam die u hebt ingevoerd voor de  [MySQL-verbinding](#new-connection-settings), bijvoorbeeld &#39;enablement&#39;.
* Selecteer **[!UICONTROL Save]**.

## Muziek {#configure-scorm} configureren

### AEM Communities ScormEngine-service {#aem-communities-scormengine-service}

De configuratie OSGi voor **AEM Communities ScormEngine Service** vormt SCORM voor het gebruik van de MySQL-server door een enablement-gemeenschap.

Deze configuratie is aanwezig wanneer [SCORM package](deploy-communities.md#scorm-package) wordt geïnstalleerd.

Alle publicatie- en auteurinstanties verwijzen naar dezelfde MySQL-server.

Wanneer MySQL op een server verschillend van AEM loopt, moet server hostname in plaats van &quot;localhost&quot;in de Dienst worden gespecificeerd ScormEngine, die typisch van [JDBC Verbinding](#configure-jdbc-connections) config wordt bevolkt.

* Op elke auteur en publiceer AEM instantie
* Aangemeld met beheerdersrechten
* Toegang tot de [webconsole](../../help/sites-deploying/configuring-osgi.md)
   * Bijvoorbeeld [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* `AEM Communities ScormEngine Service` zoeken
* Het bewerkingspictogram selecteren

   ![chlimage_1-337](assets/chlimage_1-337.png)

* Verifieer de volgende parameterwaarden met [JDBC Verbinding](#configurejdbcconnectionspool) config verenigbaar zijn:
   * **[!UICONTROL JDBC connection URI]**:  `jdbc:mysql://localhost:3306/ScormEngineDB` ** ScormEngineDB is de standaarddatabasenaam in de SQL-scripts
   * **[!UICONTROL Username]**: Hoofdmap of voer de geconfigureerde gebruikersnaam voor de MySQL-server in als dit niet het geval is.
   * **[!UICONTROL Password]**: Wis dit gebied als geen wachtwoord dat voor MySQL wordt geplaatst, anders het gevormde wachtwoord voor de Gebruikersnaam MySQL ingaat
* Wat de volgende parameter betreft:
   * **[!UICONTROL Scorm User Password]**: NIET BEWERKEN

      Uitsluitend voor intern gebruik: Het is voor een speciale de dienstgebruiker die door AEM Communities wordt gebruikt om met de golfmotor te communiceren.
* Selecteer **[!UICONTROL Save]**

### Adobe graniet CSRF-filter {#adobe-granite-csrf-filter}

Om ervoor te zorgen dat de cursussen in- en uitgeschakeld werken in alle browsers, moet Mozilla worden toegevoegd als een gebruikersagent die niet door het CSRF-filter wordt gecontroleerd.

* Meld u aan bij de AEM publicatieinstantie met beheerdersrechten.
* Toegang tot de [webconsole](../../help/sites-deploying/configuring-osgi.md)
   * Bijvoorbeeld [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
* `Adobe Granite CSRF Filter` zoeken.
* Selecteer het bewerkingspictogram.

   ![jdbcconnection2](assets/jdbcconnection2.png)

* Selecteer het pictogram `[+]` om een Veilige Agent van de Gebruiker toe te voegen.
* Voer `Mozilla/*` in.
* Selecteer **[!UICONTROL Save]**.

