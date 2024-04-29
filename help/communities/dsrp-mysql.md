---
title: MySQL-configuratie voor DSRP
description: Hoe te met de server te verbinden MySQL en het gegevensbestand te vestigen UGC
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: eafb60be-2963-4ac9-8618-50fd9bc6fe6c
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# MySQL-configuratie voor DSRP {#mysql-configuration-for-dsrp}

MySQL is een relationele database die kan worden gebruikt om door gebruikers gegenereerde inhoud (UGC) op te slaan.

Deze instructies beschrijven hoe te met de server te verbinden MySQL en het gegevensbestand te vestigen UGC.

## Vereisten {#requirements}

* [Nieuwste Gemeenschappen, functiepakket](deploy-communities.md#latestfeaturepack)
* [JDBC-stuurprogramma voor MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Een relationele database:

   * [MySQL-server](https://dev.mysql.com/downloads/mysql/) Community Server versie 5.6 of hoger

      * Kan op dezelfde host worden uitgevoerd als AEM of extern worden uitgevoerd

   * [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/)

## MySQL installeren {#installing-mysql}

[MySQL](https://dev.mysql.com/downloads/mysql/) moet worden gedownload en geïnstalleerd volgens de instructies voor het doelbesturingssysteem.

### Tabelnamen met kleine letters {#lower-case-table-names}

Aangezien SQL niet hoofdlettergevoelig is, is het voor hoofdlettergevoelige besturingssystemen nodig om de instelling voor kleine letters in te voeren voor alle tabelnamen.

Als u bijvoorbeeld alle tabelnamen met kleine letters wilt opgeven op een Linux-besturingssysteem:

* Bestand bewerken `/etc/my.cnf`
* In de `[mysqld]` de volgende regel toevoegen:

  `lower_case_table_names = 1`

### UTF8-tekenset {#utf-character-set}

Voor betere meertalige ondersteuning is het nodig de tekenset UTF8 te gebruiken.

Wijzig MySQL om UTF8 in te stellen als tekenset:

* mysql > SET NAMES &#39;utf8&#39;;

Wijzig de MySQL-database in de standaardwaarde voor UTF8:

* Bestand bewerken `/etc/my.cnf`
* In de `[client]` de volgende regel toevoegen:

  `default-character-set=utf8`

* In de `[mysqld]` de volgende regel toevoegen:

  `character-set-server=utf8`

## MySQL Workbench installeren {#installing-mysql-workbench}

MySQL Workbench biedt een UI voor het uitvoeren van SQL-scripts die het schema en de initiële gegevens installeren.

MySQL Workbench moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

## Community-verbinding {#communities-connection}

Als de MySQL Workbench voor het eerst wordt gestart, tenzij deze al voor andere doeleinden wordt gebruikt, worden er nog geen verbindingen weergegeven:

![mysqlconnection](assets/mysqlconnection.png)

### Nieuwe verbindingsinstellingen {#new-connection-settings}

1. Selecteer de `+` pictogram rechts van `MySQL Connections`.
1. In het dialoogvenster `Setup New Connection`Voer de waarden in die geschikt zijn voor uw platform

   Voor demonstratiedoeleinden, met de auteur AEM instantie en MySQL op de zelfde server:

   * Verbindingsnaam: `Communities`
   * Verbindingsmethode: `Standard (TCP/IP)`
   * Hostnaam: `127.0.0.1`
   * Gebruikersnaam: `root`
   * Wachtwoord: `no password by default`
   * Standaardschema: `leave blank`

1. Selecteren `Test Connection` om de verbinding aan de lopende dienst te verifiëren MySQL

**Notities**:

* De standaardpoort is `3306`
* De gekozen verbindingsnaam is ingevoerd als naam van de gegevensbron in [JDBC OSGi-configuratie](#configurejdbcconnections)

#### Nieuwe verbinding met Gemeenschappen {#new-communities-connection}

![communautaire verbinding](assets/community-connection.png)

## Database instellen {#database-setup}

Open de verbinding van de Gemeenschappen om het gegevensbestand te installeren.

![install-database](assets/install-database.png)

### Het SQL-script ophalen {#obtain-the-sql-script}

Het SQL-script is afkomstig uit de AEM opslagplaats:

1. Bladeren naar CRXDE Lite

   * Bijvoorbeeld: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Selecteer de map /libs/social/config/datastore/dsrp/schema
1. Downloaden `init-schema.sql`

   ![database-schema-crxde](assets/database-schema-crxde.png)

Eén methode voor het downloaden van het schema is:

* Selecteer de `jcr:content` knooppunt voor het sql-bestand
* Let op de waarde voor de `jcr:data` eigenschap is een weergavekoppeling

* Selecteer de weergavekoppeling om de gegevens in een lokaal bestand op te slaan

### De DSRP-database maken {#create-the-dsrp-database}

Voer de onderstaande stappen uit om de database te installeren. De standaardnaam van de database is `communities`.

Als de databasenaam in het script wordt gewijzigd, moet u deze ook wijzigen in het dialoogvenster [JDBC-configuratie](#configurejdbcconnections).

#### Stap 1: SQL-bestand openen {#step-open-sql-file}

In MySQL Workbench

* Selecteer in het keuzemenu Bestand de optie **[!UICONTROL Open SQL Script]** option
* Selecteer gedownloade `init_schema.sql` script

![select-sql-script](assets/select-sql-script.png)

#### Stap 2: SQL-script uitvoeren {#step-execute-sql-script}

Selecteer in het Workbench-venster voor het bestand dat in Stap 1 wordt geopend de optie `lightening (flash) icon` om het script uit te voeren.

In de volgende afbeelding worden de `init_schema.sql` bestand kan worden uitgevoerd:

![execute-sql-script](assets/execute-sql-script.png)

#### Vernieuwen {#refresh}

Zodra het manuscript wordt uitgevoerd, is het noodzakelijk om te verfrissen `SCHEMAS` van de `Navigator` om de nieuwe database te bekijken. Gebruik het vernieuwingspictogram rechts van &#39;SCHEMAS&#39;:

![vernieuwingsschema](assets/refresh-schema.png)

## JDBC-verbinding configureren {#configure-jdbc-connection}

De configuratie OSGi voor **Day Commons JDBC-verbindingspool** configureert het MySQL JDBC-stuurprogramma.

Alle publicatie- en auteur-AEM moeten verwijzen naar dezelfde MySQL-server.

Wanneer MySQL op een server verschillend van AEM loopt, moet server hostname in plaats van &quot;localhost&quot;in de schakelaar worden gespecificeerd JDBC.

* Op elke auteur en publiceer AEM instantie.
* Aangemeld met beheerdersrechten.
* Toegang krijgen tot de [webconsole](../../help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Zoek de `Day Commons JDBC Connections Pool`
* Selecteer de `+` pictogram om een verbindingsconfiguratie te creëren.

  ![configure-jdbc-connection](assets/configure-jdbc-connection.png)

* Voer de volgende waarden in:

   * **[!UICONTROL JDBC driver class]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL JDBC connection URI]**: `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

     Geef server op in plaats van localhost als MySQL-server niet hetzelfde is als &#39;deze&#39; AEM server *gemeenschappen* is de standaardnaam van de database (schema).

   * **[!UICONTROL Username]**: `root`

     Of ga gevormde Gebruikersnaam voor de server MySQL in, als niet &quot;wortel&quot;.

   * **[!UICONTROL Password]**:

     Wis dit gebied als geen wachtwoord voor MySQL wordt geplaatst,

     anders ga het gevormde wachtwoord voor de Gebruikersnaam MySQL in.

   * **[!UICONTROL Datasource name]**: naam ingevoerd voor de [MySQL-verbinding](#new-connection-settings), bijvoorbeeld &quot;gemeenschappen&quot;.

* Selecteren **[!UICONTROL Save]**
