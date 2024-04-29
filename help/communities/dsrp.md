---
title: DSRP - Relational Database Storage Resource Provider
description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 15b3a594-efde-4702-9233-232ba1c7e5b0
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# DSRP - Relational Database Storage Resource Provider {#dsrp-relational-database-storage-resource-provider}

## Over DSRP {#about-dsrp}

Wanneer AEM Communities wordt gevormd om een relationele gegevensbestand als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker-geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [Kenmerken van SRP-opties](working-with-srp.md#characteristics-of-srp-options) en [Aanbevolen topologieën](topologies.md).

## Vereisten {#requirements}

* [MySQL](#mysql-configuration), een relationele database.
* [Apache Solr](#solr-configuration), een zoekplatform.

>[!NOTE]
>
>De standaardopslagconfiguratie wordt nu opgeslagen in conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) in plaats van `etc` pad (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt aangeraden de [migratiestappen](#zerodt-migration-steps) om de standaardprocedures naar behoren te laten werken.

## Configuratie van relationele database {#relational-database-configuration}

### MySQL-configuratie {#mysql-configuration}

Een installatie MySQL kan tussen enablement eigenschappen en gemeenschappelijke opslag (DSRP) binnen de zelfde verbindingspool worden gedeeld door verschillende gegevensbestand (schema) namen en ook verschillende verbindingen (server:haven) te gebruiken.

Voor installatie en configuratiedetails, zie [MySQL-configuratie voor DSRP](dsrp-mysql.md).

### Solr-configuratie {#solr-configuration}

Een Solr installatie kan tussen de knoopopslag (Oak) en gemeenschappelijke opslag (SRP) worden gedeeld door verschillende inzamelingen te gebruiken.

Als zowel de Oak als SRP inzamelingen intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productieomgevingen biedt de SolrCloud-modus betere prestaties dan de zelfstandige modus (één lokale Solr-instelling).

Voor installatie en configuratiedetails, zie [Solr Configuratie voor SRP](solr.md).

### DSRP selecteren {#select-dsrp}

De [Opslagconfiguratieconsole](srp-config.md) maakt het mogelijk de standaardopslagconfiguratie te selecteren, die aangeeft welke implementatie van SRP moet worden gebruikt.

Op auteur, om tot de console van de Configuratie van de Opslag toegang te hebben

* Aanmelden met beheerdersrechten
* Van de **hoofdmenu**

   * Selecteren **[!UICONTROL Tools]** (uit het linkerdeelvenster)
   * Selecteren **[!UICONTROL Communities]**
   * Selecteren **[!UICONTROL Storage Configuration]**

      * De resulterende locatie is bijvoorbeeld: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)

     >[!NOTE]
     >
     >De standaardopslagconfiguratie wordt nu opgeslagen in conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) in plaats van `etc` pad (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt aangeraden de [migratiestappen](#zerodt-migration-steps) om de standaardprocedures naar behoren te laten werken.

  ![dsrp-config](assets/dsrp-config.png)

* Selecteren **[!UICONTROL Database Storage Resource Provider (DSRP)]**
* **Databaseconfiguratie**

   * **[!UICONTROL JDBC datasource name]**

     De naam die aan MySQL verbinding wordt gegeven moet het zelfde zijn ingegaan in [JDBC OSGi-configuratie](dsrp-mysql.md#configurejdbcconnections)

     *default*: gemeenschappen

   * **[!UICONTROL Database name]**

     Naam die aan schema in wordt gegeven [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script) script

     *default*: gemeenschappen

* **SolrConfiguration**

   * **[Zookeeper](https://solr.apache.org/guide/6_6/using-zookeeper-to-manage-configuration-files.html) Host**

     Laat deze waarde leeg als Solr wordt uitgevoerd met de interne ZooKeeper. Anders, bij uitvoering in [SolrCloud-modus](solr.md#solrcloud-mode) met een externe ZooKeeper, plaats deze waarde aan URI voor ZooKeeper, zoals *my.server.com:80*

     *default*: *&lt;blank>*

   * **[!UICONTROL Solr URL]**

     *default*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr Collection]**

     *default*: collection1

* Selecteren **[!UICONTROL Submit]**.

### Nul stappen voor downtime migratie voor standaardconfiguratie {#zerodt-migration-steps}

Om ervoor te zorgen dat de standaardpagina [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) Voer de volgende stappen uit voor de werken zoals u had verwacht:

1. Naam van pad wijzigen bij `/etc/socialconfig` tot `/etc/socialconfig_old`, zodat de systeemconfiguratie terugvalt naar jsrp (gebrek).
1. Ga naar standaardpagina [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), waarin jsrp is geconfigureerd. Klik op de knop **[!UICONTROL submit]** knoop zodat de nieuwe standaardconfiguratieknoop bij wordt gecreeerd `/conf/global/settings/community/srpc`.
1. De gemaakte standaardconfiguratie verwijderen `/conf/global/settings/community/srpc/defaultconfiguration`.
1. De oude configuratie kopiëren `/etc/socialconfig_old/srpc/defaultconfiguration` in plaats van het verwijderde knooppunt (`/conf/global/settings/community/srpc/defaultconfiguration`) in de vorige stap.
1. De oude verwijderen `etc` node `/etc/socialconfig_old`.

## De configuratie publiceren {#publishing-the-configuration}

DSRP moet als gemeenschappelijke opslag op alle auteur worden geïdentificeerd en instanties publiceren.

De identieke configuratie beschikbaar stellen in de publicatieomgeving:

* Op auteur:

   * Navigeren van hoofdmenu naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]**
   * Dubbelklikken **[!UICONTROL Activate Tree]**
   * **Startpad**:

      * Bladeren naar `/etc/socialconfig/srpc/`

   * Zorgen `Only Modified` is niet geselecteerd.
   * Selecteren **[!UICONTROL Activate]**.

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak in de publicatieomgeving worden ingevoerd, gaat u naar:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Solr opnieuw indexeren voor DSRP {#reindexing-solr-for-dsrp}

Om DSRP Solr opnieuw te indexeren, volg de documentatie voor [opnieuw indexeren van MSRP](msrp.md#msrp-reindex-tool)Gebruik in plaats daarvan deze URL wanneer u opnieuw indexeert voor DSRP: **/services/social/datastore/rdb/rendex**

Bijvoorbeeld, zou een krullbevel om DSRP opnieuw te indexeren als dit kijken:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```
