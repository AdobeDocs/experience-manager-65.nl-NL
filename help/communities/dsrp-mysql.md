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

   * [MySQL Server](https://dev.mysql.com/downloads/mysql/) Community Server versie 5.6 of hoger

      * Kan op dezelfde host als AEM worden uitgevoerd of extern worden uitgevoerd
   * [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/)


## MySQL installeren {#installing-mysql}

[MySQL](https://dev.mysql.com/downloads/mysql/) moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

### Tabelnamen met kleine letters {#lower-case-table-names}

Aangezien SQL niet hoofdlettergevoelig is, is het voor hoofdlettergevoelige besturingssystemen nodig om de instelling voor kleine letters in te voeren voor alle tabelnamen.

Als u bijvoorbeeld alle tabelnamen met kleine letters wilt opgeven op een Linux-besturingssysteem:

* Bestand bewerken `/etc/my.cnf`
* Voeg de volgende regel toe aan de `[mysqld]` sectie:

   `lower_case_table_names = 1`

### UTF8-tekenset {#utf-character-set}

Voor betere meertalige ondersteuning is het nodig de tekenset UTF8 te gebruiken.

Wijzig MySQL om UTF8 in te stellen als tekenset:

* mysql > SET NAMES &#39;utf8&#39;;

Wijzig de MySQL-database in de standaardwaarde voor UTF8:

* Bestand bewerken `/etc/my.cnf`
* Voeg de volgende regel toe aan de `[client]` sectie:

   `default-character-set=utf8`

* Voeg de volgende regel toe aan de `[mysqld]` sectie:

   `character-set-server=utf8`

## MySQL Workbench installeren {#installing-mysql-workbench}

MySQL Workbench biedt een UI voor het uitvoeren van SQL-scripts die het schema en de initiële gegevens installeren.

MySQL Workbench moet worden gedownload en geïnstalleerd volgens de instructies voor het doel-besturingssysteem.

## Community-verbinding {#communities-connection}

Als de MySQL Workbench voor het eerst wordt gestart, tenzij deze al voor andere doeleinden wordt gebruikt, worden er nog geen verbindingen weergegeven:

![chlimage_1-104](assets/chlimage_1-104.png)

### Nieuwe verbindingsinstellingen {#new-connection-settings}

1. Selecteer het `+` pictogram rechts van `MySQL Connections`.
1. Voer in het dialoogvenster de waarden in die geschikt zijn voor uw platform `Setup New Connection`

   Voor demonstratiedoeleinden, met de auteurAEM instantie en MySQL op de zelfde server:

   * Verbindingsnaam: `Communities`
   * Verbindingsmethode: `Standard (TCP/IP)`
   * Hostnaam: `127.0.0.1`
   * Gebruikersnaam: `root`
   * Wachtwoord: `no password by default`
   * Standaardschema: `leave blank`

1. Selecteer `Test Connection` om de verbinding met de lopende dienst te verifiëren MySQL

**Opmerkingen**:

* De standaardpoort is `3306`
* De gekozen Naam van de Verbinding is ingegaan als datasource naam in configuratie [JDBC OSGi](#configurejdbcconnections)

#### Nieuwe verbinding met Gemeenschappen {#new-communities-connection}

![chlimage_1-105](assets/chlimage_1-105.png)

## Database instellen {#database-setup}

Open de verbinding van de Gemeenschappen om het gegevensbestand te installeren.

![chlimage_1-106](assets/chlimage_1-106.png)

### Het SQL-script ophalen {#obtain-the-sql-script}

Het SQL-script is afkomstig uit de AEM-opslagplaats:

1. Bladeren naar CRXDE Lite

   * Bijvoorbeeld: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Selecteer de map /libs/social/config/datastore/dsrp/schema
1. Downloaden `init-schema.sql`

   ![chlimage_1-107](assets/chlimage_1-107.png)

Eén methode voor het downloaden van het schema is:

* Het `jcr:content` knooppunt voor het sql-bestand selecteren
* De waarde van de `jcr:data` eigenschap is een weergavekoppeling

* Selecteer de weergavekoppeling om de gegevens in een lokaal bestand op te slaan

### De DSRP-database maken {#create-the-dsrp-database}

Voer de onderstaande stappen uit om de database te installeren. De standaardnaam van de database is `communities`.

Als de gegevensbestandnaam in het manuscript wordt veranderd, ben zeker om het in de [configuratie](#configurejdbcconnections)te veranderen JDBC.

#### Stap 1: SQL-bestand openen {#step-open-sql-file}

In MySQL Workbench

* Via het keuzemenu Bestand
* Selecteer gedownloade `init_schema.sql`

![chlimage_1-108](assets/chlimage_1-108.png)

#### Stap 2: SQL-script uitvoeren {#step-execute-sql-script}

Selecteer in het Workbench-venster voor het bestand dat in Stap 1 wordt geopend het bestand `lightening (flash) icon` dat u wilt uitvoeren.

In de volgende afbeelding kan het `init_schema.sql` bestand worden uitgevoerd:

![chlimage_1-109](assets/chlimage_1-109.png)

#### Vernieuwen {#refresh}

Zodra het manuscript wordt uitgevoerd, is het noodzakelijk om de `SCHEMAS` sectie van `Navigator` te verfrissen om het nieuwe gegevensbestand te zien. Gebruik het vernieuwingspictogram rechts van &#39;SCHEMAS&#39;:

![chlimage_1-110](assets/chlimage_1-110.png)

## JDBC-verbinding configureren {#configure-jdbc-connection}

De configuratie OSGi voor de Pool **van Verbindingen JDBC van de** Dag vormt de Bestuurder MySQL JDBC.

Alle publicatie- en auteur-AEM-instanties moeten verwijzen naar dezelfde MySQL-server.

Wanneer MySQL op een server verschillend van AEM loopt, moet de server hostname in plaats van &quot;localhost&quot;in de schakelaar worden gespecificeerd JDBC.

* Op elke auteur en publiceer AEM-instantie.
* Aangemeld met beheerdersrechten.
* Open de [webconsole](../../help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Zoek de `Day Commons JDBC Connections Pool`
* Selecteer het `+` pictogram om een nieuwe verbindingsconfiguratie tot stand te brengen.

   ![chlimage_1-111](assets/chlimage_1-111.png)

* Voer de volgende waarden in:

   * **[!UICONTROL JDBC driver class]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL JDBC connection URI]**: `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

      Geef server op in plaats van localhost als MySQL-server niet hetzelfde is als &#39;deze&#39; AEM- *servergemeenschappen* de standaarddatabasenaam (schema) is.

   * **[!UICONTROL Username]**: `root`

      Of ga gevormde Gebruikersnaam voor de server MySQL in, als niet &quot;wortel&quot;.

   * **[!UICONTROL Password]**:

      Wis dit gebied als geen wachtwoord voor MySQL wordt geplaatst,

      anders ga het gevormde wachtwoord voor de Gebruikersnaam MySQL in.

   * **[!UICONTROL Datasource name]**: naam die is ingevoerd voor de [MySQL-verbinding](#new-connection-settings), bijvoorbeeld &#39;community&#39;.

* Selecteer **[!UICONTROL Save]**

