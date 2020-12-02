---
title: MySQL-configuratie voor DSRP
seo-title: MySQL-configuratie voor DSRP
description: Hoe te met de server te verbinden MySQL en het gegevensbestand te vestigen UGC
seo-description: Hoe te met de server te verbinden MySQL en het gegevensbestand te vestigen UGC
uuid: c058cc88-7ca2-4aed-9a36-b080e603f886
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: edc3043c-7ec4-4e4a-b008-95f1784f012e
translation-type: tm+mt
source-git-commit: 29f150215052d61c1e20d25b0c095ea6582e26f7
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# MySQL-configuratie voor DSRP {#mysql-configuration-for-dsrp}

MySQL is een relationele database die kan worden gebruikt om door gebruikers gegenereerde inhoud (UGC) op te slaan.

Deze instructies beschrijven hoe te met de server te verbinden MySQL en het gegevensbestand te vestigen UGC.

## Vereisten {#requirements}

* [Nieuwste Gemeenschappen, functiepakket](deploy-communities.md#latestfeaturepack)
* [JDBC-stuurprogramma voor MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Een relationele database:

   * [MySQL ](https://dev.mysql.com/downloads/mysql/) serverCommunity Server versie 5.6 of hoger

      * Kan op dezelfde host worden uitgevoerd als AEM of extern worden uitgevoerd
   * [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/)


## MySQL {#installing-mysql} installeren

[](https://dev.mysql.com/downloads/mysql/) MySQL moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

### Tabelnamen van kleine letters {#lower-case-table-names}

Aangezien SQL niet hoofdlettergevoelig is, is het voor hoofdlettergevoelige besturingssystemen nodig om de instelling voor kleine letters in te voeren voor alle tabelnamen.

Als u bijvoorbeeld alle tabelnamen met kleine letters wilt opgeven op een Linux-besturingssysteem:

* Bestand `/etc/my.cnf` bewerken
* Voeg in de sectie `[mysqld]` de volgende regel toe:

   `lower_case_table_names = 1`

### UTF8-tekenset {#utf-character-set}

Voor betere meertalige ondersteuning is het nodig de tekenset UTF8 te gebruiken.

Wijzig MySQL om UTF8 in te stellen als tekenset:

* mysql > SET NAMES &#39;utf8&#39;;

Wijzig de MySQL-database in de standaardwaarde voor UTF8:

* Bestand `/etc/my.cnf` bewerken
* Voeg in de sectie `[client]` de volgende regel toe:

   `default-character-set=utf8`

* Voeg in de sectie `[mysqld]` de volgende regel toe:

   `character-set-server=utf8`

## MySQL Workbench {#installing-mysql-workbench} installeren

MySQL Workbench biedt een UI voor het uitvoeren van SQL-scripts die het schema en de initiële gegevens installeren.

MySQL Workbench moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

## Community-verbinding {#communities-connection}

Als de MySQL Workbench voor het eerst wordt gestart, tenzij deze al voor andere doeleinden wordt gebruikt, worden er nog geen verbindingen weergegeven:

![chlimage_1-104](assets/chlimage_1-104.png)

### Nieuwe verbindingsinstellingen {#new-connection-settings}

1. Selecteer het pictogram `+` rechts van `MySQL Connections`.
1. Voer in het dialoogvenster `Setup New Connection` de waarden in die geschikt zijn voor uw platform

   Voor demonstratiedoeleinden, met de auteur AEM instantie en MySQL op de zelfde server:

   * Verbindingsnaam: `Communities`
   * Verbindingsmethode: `Standard (TCP/IP)`
   * Hostnaam: `127.0.0.1`
   * Gebruikersnaam: `root`
   * Wachtwoord: `no password by default`
   * Standaardschema: `leave blank`

1. Selecteer `Test Connection` om de verbinding met de actieve dienst te verifiëren MySQL

**Opmerkingen**:

* De standaardpoort is `3306`
* De gekozen Naam van de Verbinding is ingegaan als naam van de gegevensbron in [JDBC OSGi configuratie](#configurejdbcconnections)

#### Nieuwe verbinding Gemeenschappen {#new-communities-connection}

![chlimage_1-105](assets/chlimage_1-105.png)

## Database-instelling {#database-setup}

Open de verbinding van de Gemeenschappen om het gegevensbestand te installeren.

![chlimage_1-105](assets/chlimage_1-106.png)

### SQL-script ophalen {#obtain-the-sql-script}

Het SQL-script is afkomstig uit de AEM opslagplaats:

1. Bladeren naar CRXDE Lite

   * Bijvoorbeeld [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Selecteer de map /libs/social/config/datastore/dsrp/schema
1. `init-schema.sql` downloaden

   ![chlimage_1-107](assets/chlimage_1-107.png)

Eén methode voor het downloaden van het schema is:

* Selecteer de `jcr:content`-node voor het sql-bestand
* De waarde voor de eigenschap `jcr:data` is een weergavekoppeling

* Selecteer de weergavekoppeling om de gegevens in een lokaal bestand op te slaan

### De DSRP-database {#create-the-dsrp-database} maken

Voer de onderstaande stappen uit om de database te installeren. De standaardnaam van de database is `communities`.

Als de gegevensbestandnaam in het manuscript wordt veranderd, ben zeker om het in [JDBC config](#configurejdbcconnections) ook te veranderen.

#### Stap 1: SQL-bestand {#step-open-sql-file} openen

In MySQL Workbench

* Via het keuzemenu Bestand
* Selecteer gedownloade `init_schema.sql`

![chlimage_1-108](assets/chlimage_1-108.png)

#### Stap 2: SQL-script uitvoeren {#step-execute-sql-script}

Selecteer `lightening (flash) icon` in het Workbench-venster voor het bestand dat in Stap 1 wordt geopend om het script uit te voeren.

In de volgende afbeelding kan het `init_schema.sql`-bestand worden uitgevoerd:

![chlimage_1-189](assets/chlimage_1-109.png)

#### Vernieuwen {#refresh}

Zodra het manuscript wordt uitgevoerd, is het noodzakelijk om `SCHEMAS` sectie van `Navigator` te verfrissen om het nieuwe gegevensbestand te zien. Gebruik het vernieuwingspictogram rechts van &#39;SCHEMAS&#39;:

![chlimage_1-110](assets/chlimage_1-110.png)

## JDBC-verbinding {#configure-jdbc-connection} configureren

De configuratie OSGi voor **de Pool van Verbindingen JDBC van de Bevelen van de Dag** vormt de Bestuurder MySQL JDBC.

Alle publicatie- en auteur-AEM moeten verwijzen naar dezelfde MySQL-server.

Wanneer MySQL op een server verschillend van AEM loopt, moet server hostname in plaats van &quot;localhost&quot;in de schakelaar worden gespecificeerd JDBC.

* Op elke auteur en publiceer AEM instantie.
* Aangemeld met beheerdersrechten.
* Open de [webconsole](../../help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* `Day Commons JDBC Connections Pool` zoeken
* Selecteer het pictogram `+` om een nieuwe verbindingsconfiguratie tot stand te brengen.

   ![chlimage_1-111](assets/chlimage_1-111.png)

* Voer de volgende waarden in:

   * **[!UICONTROL JDBC driver class]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL JDBC connection URI]**:  `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

      Geef server op in plaats van localhost als MySQL-server niet hetzelfde is als &#39;deze&#39; AEM *Communities* is de standaardnaam van de database (schema).

   * **[!UICONTROL Username]**:  `root`

      Of ga gevormde Gebruikersnaam voor de server MySQL in, als niet &quot;wortel&quot;.

   * **[!UICONTROL Password]**:

      Wis dit gebied als geen wachtwoord voor MySQL wordt geplaatst,

      anders ga het gevormde wachtwoord voor de Gebruikersnaam MySQL in.

   * **[!UICONTROL Datasource name]**: naam die is ingevoerd voor de  [MySQL-verbinding](#new-connection-settings), bijvoorbeeld &#39;community&#39;.

* Selecteer **[!UICONTROL Save]**

