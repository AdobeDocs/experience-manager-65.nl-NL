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
source-git-commit: f7e5afe46100db7837647ac89aaf58cf101143b0

---


# MySQL-configuratie voor functies van Enablement {#mysql-configuration-for-enablement-features}

MySQL is een relationele database die voornamelijk wordt gebruikt voor het bijhouden en rapporteren van SCORM-gegevens voor actiemiddelen. Ingesloten tabellen zijn tabellen voor andere functies, zoals het bijhouden van een pauze/resume.

Deze instructies beschrijven hoe te met de server te verbinden MySQL, het enablement gegevensbestand te vestigen, en het gegevensbestand met aanvankelijke gegevens te bevolken.

## Vereisten {#requirements}

Voordat u MySQL voor de functie enablement van Communities configureert, moet u

* Installeer [MySQL Server](https://dev.mysql.com/downloads/mysql/) Community Server versie 5.6:
   * Versie 5.7 wordt niet ondersteund voor SCORM.
   * Kan dezelfde server zijn als de auteur van de AEM-instantie.
* Installeer bij alle AEM-instanties het officiële [JDBC-stuurprogramma voor MySQL](deploy-communities.md#jdbc-driver-for-mysql).
* Installeer [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/).
* Installeer het [SCORM-pakket](enablement.md#scorm)op alle AEM-instanties.

## MySQL installeren {#installing-mysql}

MySQL moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

### Tabelnamen met kleine letters {#lower-case-table-names}

Aangezien SQL niet hoofdlettergevoelig is, is het voor hoofdlettergevoelige besturingssystemen nodig om de instelling voor kleine letters in te voeren voor alle tabelnamen.

Als u bijvoorbeeld alle tabelnamen met kleine letters wilt opgeven op een Linux-besturingssysteem:

* Bestand bewerken `/etc/my.cnf`
* Voeg de volgende regel toe aan de `[mysqld]` sectie: `lower_case_table_names = 1`

### UTF8-tekenset {#utf-character-set}

Voor betere meertalige ondersteuning is het nodig de tekenset UTF8 te gebruiken.

Wijzig MySQL om UTF8 in te stellen als tekenset:
* mysql > SET NAMES &#39;utf8&#39;;

Wijzig de MySQL-database in de standaardwaarde voor UTF8:
* Bestand bewerken `/etc/my.cnf`
* In de `[client]` sectie toevoegen: `default-character-set=utf8`
* In de `[mysqld]` sectie toevoegen: `character-set-server=utf8`

## MySQL Workbench installeren {#installing-mysql-workbench}

MySQL Workbench biedt een UI voor het uitvoeren van SQL-scripts die het schema en de initiële gegevens installeren.

MySQL Workbench moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

## Enablement Connection {#enablement-connection}

Als de MySQL Workbench voor het eerst wordt gestart, tenzij deze al voor andere doeleinden wordt gebruikt, worden er nog geen verbindingen weergegeven:

![chlimage_1-327](assets/chlimage_1-327.png)

### Nieuwe verbindingsinstellingen {#new-connection-settings}

1. Selecteer het plusteken (+) rechts van `MySQL Connections`.
1. Voer in het dialoogvenster waarden in die geschikt zijn voor uw platform om demonstratiedoeleinden te maken, met de auteur AEM-instantie en MySQL op dezelfde server: `Setup New Connection`
   * Verbindingsnaam: `Enablement`
   * Verbindingsmethode: `Standard (TCP/IP)`
   * Hostnaam: `127.0.0.1`
   * Gebruikersnaam: `root`
   * Wachtwoord: `no password by default`
   * Standaardschema: `leave blank`
1. Selecteer `Test Connection` om de verbinding aan de lopende dienst te verifiëren MySQL.

**Opmerkingen**:
* De standaardpoort is `3306`.
* De `Connection Name` gekozen naam is ingegaan als `datasource` naam in [configuratie](#configure-jdbc-connections)JDBC OSGi.

#### Verbinding gelukt {#successful-connection}

![chlimage_1-328](assets/chlimage_1-328.png)

#### Nieuwe schakelingsverbinding {#new-enablement-connection}

![chlimage_1-329](assets/chlimage_1-329.png)

## Database instellen {#database-setup}

Bij het openen van de nieuwe verbinding Enablement, merk op dat er een testschema en standaardgebruikersrekeningen zijn.

![chlimage_1-330](assets/chlimage_1-330.png)

### SQL-scripts verkrijgen {#obtain-sql-scripts}

De SQL manuscripten worden verkregen gebruikend CRXDE Lite op de auteursinstantie. Het [SCORM-pakket](deploy-communities.md#scorm) moet zijn geïnstalleerd:

1. Bladeren naar CRXDE Lite:
   * Bijvoorbeeld: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)
1. De `/libs/social/config/scorm/` map uitvouwen
1. Downloaden `database_scormengine.sql`
1. Downloaden `database_scorm_integration.sql`

![chlimage_1-331](assets/chlimage_1-331.png)

Eén methode voor het downloaden van het schema is:

* Selecteer het `jcr:content`knooppunt voor het sql-bestand.
* De waarde voor de `jcr:data`eigenschap is een weergavekoppeling.
* Selecteer de weergavekoppeling om de gegevens in een lokaal bestand op te slaan.

### SCORM-database maken {#create-scorm-database}

De toe te voegen SCORM-database is:

* name: `ScormEngineDB`
* gemaakt van scripts:
   * schema: `database_scormengine.sql`
   * gegevens: Voer `database_scorm_integration.sql`de onderstaande stappen uit ([openen](#step-open-sql-file), [uitvoeren](#step-execute-sql-script)) om elk [SQL-script](#obtain-sql-scripts) te installeren. [Vernieuw](#refresh) indien nodig om de resultaten van de uitvoering van het script weer te geven.

Installeer het schema voordat u de gegevens installeert.

>[!CAUTION]
>
>Als de databasenaam is gewijzigd, moet u deze correct opgeven in:
>
>* [JDBC-configuratie](#configure-jdbc-connections)
>* [SCORM-configuratie](#configure-scorm)
>



#### Stap 1: SQL-bestand openen {#step-open-sql-file}

In MySQL Workbench

* Via het keuzemenu Bestand
* Selecteer `Open SQL Script ...`
* Selecteer in deze volgorde een van de volgende opties:
   1. `database_scormengine.sql`
   1. `database_scorm_integration.sql`

![chlimage_1-332](assets/chlimage_1-332.png)

#### Stap 2: SQL-script uitvoeren {#step-execute-sql-script}

Selecteer in het Workbench-venster voor het bestand dat in Stap 1 wordt geopend het bestand `lightening (flash) icon` dat u wilt uitvoeren.

De uitvoering van het `database_scormengine.sql` script voor het maken van de SCORM-database kan een minuut in beslag nemen.

![chlimage_1-333](assets/chlimage_1-333.png)

#### Vernieuwen {#refresh}

Zodra de manuscripten worden uitgevoerd, is het noodzakelijk om de `SCHEMAS` sectie van `Navigator` te verfrissen om het nieuwe gegevensbestand te zien. Gebruik het vernieuwingspictogram rechts van &#39;SCHEMAS&#39;:

![chlimage_1-334](assets/chlimage_1-334.png)

#### Resultaat: scormenginedb {#result-scormenginedb}

Na het installeren en vernieuwen van SCHEMAS, `scormenginedb` zal het zichtbaar zijn.

![chlimage_1-335](assets/chlimage_1-335.png)

## JDBC-verbindingen configureren {#configure-jdbc-connections}

De configuratie OSGi voor de Pool **van Verbindingen JDBC van de** Dag vormt de Bestuurder MySQL JDBC.

Alle publicatie- en auteur-AEM-instanties moeten verwijzen naar dezelfde MySQL-server.

Wanneer MySQL op een server verschillend van AEM loopt, moet server hostname in plaats van &quot;localhost&quot;in de schakelaar worden gespecificeerd JDBC (die de [ScormEngine](#configurescormengineservice) config bevolkt).

* Op elke auteur en publiceer AEM-instantie
* Aangemeld met beheerdersrechten
* De [webconsole openen](../../help/sites-deploying/configuring-osgi.md)
   * Bijvoorbeeld: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Zoek de `Day Commons JDBC Connections Pool`
* Selecteer het `+` pictogram om een nieuwe configuratie tot stand te brengen

![chlimage_1-336](assets/chlimage_1-336.png)

* Voer de volgende waarden in:
   * **[!UICONTROL JDBC-stuurprogrammaklasse]**: `com.mysql.jdbc.Driver`
   * **DBC-verbindingsURIJ **: Geef server op in plaats van localhost als MySQL-server niet hetzelfde is als &#39;deze&#39; AEM-server.`jdbc:mysql://localhost:3306/aem63reporting`
   * **[!UICONTROL Gebruikersnaam]**: De wortel of gaat de gevormde Gebruikersnaam voor de server MySQL, als niet &quot;wortel&quot;in.
   * **[!UICONTROL Wachtwoord]**: Wis dit gebied als geen wachtwoord dat voor MySQL wordt geplaatst, anders het gevormde wachtwoord voor de Gebruikersnaam MySQL ingaat.
   * **[!UICONTROL Naam]** gegevensbron: Naam die u hebt ingevoerd voor de [MySQL-verbinding](#new-connection-settings), bijvoorbeeld &#39;enablement&#39;.
* Selecteer **[!UICONTROL Opslaan]**.

## Muziek configureren {#configure-scorm}

### AEM Communities ScormEngine Service {#aem-communities-scormengine-service}

De configuratie OSGi voor de Dienst **van ScormEngine van** Gemeenschappen AEM vormt SCORM voor het gebruik van de server MySQL van een enablement gemeenschap.

Deze configuratie is aanwezig wanneer het [SCORM-pakket](deploy-communities.md#scorm-package) is geïnstalleerd.

Alle publicatie- en auteurinstanties verwijzen naar dezelfde MySQL-server.

Wanneer MySQL op een server verschillend van AEM loopt, moet server hostname in plaats van &quot;localhost&quot;in de Dienst worden gespecificeerd ScormEngine, die typisch van de [Verbinding](#configure-jdbc-connections) JDBC wordt bevolkt config.

* Op elke auteur en publiceer AEM-instantie
* Aangemeld met beheerdersrechten
* De [webconsole openen](../../help/sites-deploying/configuring-osgi.md)
   * Bijvoorbeeld: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Zoek de `AEM Communities ScormEngine Service`
* Het bewerkingspictogram selecteren
   ![chlimage_1-337](assets/chlimage_1-337.png)
* Verifieer de volgende parameterwaarden verenigbaar met de [Verbinding](#configurejdbcconnectionspool) JDBC config zijn:
   * **[!UICONTROL URI]** JDBC-verbinding: `jdbc:mysql://localhost:3306/ScormEngineDB` ScormEngineDB ** is de standaarddatabasenaam in de SQL-scripts
   * **[!UICONTROL Gebruikersnaam]**: Hoofdmap of voer de geconfigureerde gebruikersnaam voor de MySQL-server in als dit niet het geval is.
   * **[!UICONTROL Wachtwoord]**: Wis dit gebied als geen wachtwoord dat voor MySQL wordt geplaatst, anders het gevormde wachtwoord voor de Gebruikersnaam MySQL ingaat
* Wat de volgende parameter betreft:
   * **[!UICONTROL Wachtwoord]** voor scoregebruiker: NIET BEWERKEN

      Uitsluitend voor intern gebruik: Het is voor een speciale de dienstgebruiker die door Gemeenschappen AEM wordt gebruikt om met de vormmotor te communiceren.
* Selecteer **[!UICONTROL Opslaan]**

### Adobe Granite CSRF-filter {#adobe-granite-csrf-filter}

Om ervoor te zorgen dat de cursussen in- en uitgeschakeld werken in alle browsers, moet Mozilla worden toegevoegd als een gebruikersagent die niet door het CSRF-filter wordt gecontroleerd.

* Meld u aan bij de publicatie-instantie van AEM met beheerdersrechten.
* De [webconsole openen](../../help/sites-deploying/configuring-osgi.md)
   * Bijvoorbeeld: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
* Zoeken `Adobe Granite CSRF Filter`.
* Selecteer het bewerkingspictogram.

   ![chlimage_1-338](assets/chlimage_1-338.png)

* Selecteer het `[+]` pictogram om een veilige gebruikersagent toe te voegen.
* Enter `Mozilla/*`.
* Selecteer **[!UICONTROL Opslaan]**.

