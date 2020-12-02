---
title: DSRP - Relational Database Storage Resource Provider
seo-title: DSRP - Relational Database Storage Resource Provider
description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
seo-description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
uuid: f364e7da-ee54-4ab2-a630-7ec9239005ac
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d23acb18-6761-4290-9e7a-a434582791bd
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 0%

---


# DSRP - Relational Database Storage Resource Provider {#dsrp-relational-database-storage-resource-provider}

## Informatie over DSRP {#about-dsrp}

Wanneer AEM Communities wordt gevormd om een relationele gegevensbestand als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [Kenmerken van SRP Options](working-with-srp.md#characteristics-of-srp-options) en [Recommended Topologies](topologies.md).

## Vereisten {#requirements}

* [MySQL](#mysql-configuration), een relationele database.
* [Apache Solr](#solr-configuration), een zoekplatform.

>[!NOTE]
>
>De standaardopslagconfiguratie wordt nu opgeslagen in conf-pad (`/conf/global/settings/community/srpc/defaultconfiguration`) in plaats van enz.-pad (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt geadviseerd om [migratiestappen](#zerodt-migration-steps) te volgen om gebreken zoals verwacht te maken werken.

## Configuratie van relationele database {#relational-database-configuration}

### MySQL-configuratie {#mysql-configuration}

Een installatie MySQL kan tussen enablement eigenschappen en gemeenschappelijke opslag (DSRP) binnen de zelfde verbindingspool worden gedeeld door verschillende gegevensbestand (schema) namen en ook verschillende verbindingen (server:haven) te gebruiken.

Voor installatie en configuratiedetails, zie [Configuratie MySQL voor DSRP](dsrp-mysql.md).

### Solr-configuratie {#solr-configuration}

Een Solr installatie kan tussen de knoopopslag (Oak) en gemeenschappelijke opslag (SRP) worden gedeeld door verschillende inzamelingen te gebruiken.

Als zowel de Oak als SRP inzamelingen intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productieomgevingen biedt de SolrCloud-modus betere prestaties dan de zelfstandige modus (één lokale Solr-instelling).

Voor installatie en configuratiedetails, zie [Solr Configuratie voor SRP](solr.md).

### Selecteer DSRP {#select-dsrp}

Met de [Opslagconfiguratieconsole](srp-config.md) kunt u de standaardopslagconfiguratie selecteren, die aangeeft welke implementatie van SRP moet worden gebruikt.

Op auteur, om tot de console van de Configuratie van de Opslag toegang te hebben

* Aanmelden met beheerdersrechten
* Vanuit het **hoofdmenu**

   * Selecteer **[!UICONTROL Tools]** (in het linkerdeelvenster)
   * Selecteer **[!UICONTROL Communities]**
   * Selecteer **[!UICONTROL Storage Configuration]**

      * De resulterende locatie is bijvoorbeeld: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)
      >[!NOTE]
      >
      >De standaardopslagconfiguratie wordt nu opgeslagen in conf-pad (`/conf/global/settings/community/srpc/defaultconfiguration`)      in plaats van pad enz (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt geadviseerd om [migratiestappen](#zerodt-migration-steps) te volgen om gebreken zoals verwacht te maken werken.
   ![dsrp-config](assets/dsrp-config.png)

* Selecteer **[!UICONTROL Database Storage Resource Provider (DSRP)]**
* **Databaseconfiguratie**

   * **[!UICONTROL JDBC datasource name]**

      De naam die aan verbinding MySQL wordt gegeven moet het zelfde zijn zoals ingegaan in [JDBC OSGi configuratie](dsrp-mysql.md#configurejdbcconnections)

      *standaard*: gemeenschappen

   * **[!UICONTROL Database name]**

      Naam gegeven aan schema in [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script) manuscript

      *standaard*: gemeenschappen

* **SolrConfiguration**

   * **[](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files) ZookeeperHost**

      Laat deze waarde leeg als Solr wordt uitgevoerd met de interne ZooKeeper. Als u anders in de modus [SolrCloud](solr.md#solrcloud-mode) met een externe ZooKeeper uitvoert, stelt u deze waarde in op de URI voor de ZooKeeper, zoals *my.server.com:80*

      *standaard*:  *&lt;blank>*

   * **[!UICONTROL Solr URL]**

      *standaard*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr Collection]**

      *standaard*: verzameling1

* Selecteer **[!UICONTROL Submit]**.

### Nul stappen voor downtime migratie voor standaard {#zerodt-migration-steps}

Ga als volgt te werk om ervoor te zorgen dat de standaardpagina [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) naar behoren werkt:

1. Wijzig de naam van het pad bij `/etc/socialconfig` in `/etc/socialconfig_old`, zodat de systeemconfiguratie terugvalt naar jsrp (standaard).
1. Ga naar standaardschrp pagina [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), waar jsrp wordt gevormd. Klik **[!UICONTROL submit]** knoop zodat de nieuwe standaardconfiguratieknooppunt bij `/conf/global/settings/community/srpc` wordt gecreeerd.
1. Verwijder de gemaakte standaardconfiguratie `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieer de oude configuratie `/etc/socialconfig_old/srpc/defaultconfiguration` in plaats van het verwijderde knooppunt (`/conf/global/settings/community/srpc/defaultconfiguration`) in de vorige stap.
1. Verwijder het oude knooppunt etc. `/etc/socialconfig_old`.

## De configuratie {#publishing-the-configuration} publiceren

DSRP moet als gemeenschappelijke opslag op alle auteur worden geïdentificeerd en instanties publiceren.

De identieke configuratie beschikbaar stellen in de publicatieomgeving:

* Op auteur:

   * Navigeer van hoofdmenu aan **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]**
   * Dubbelklikken **[!UICONTROL Activate Tree]**
   * **Startpad**:

      * Bladeren naar `/etc/socialconfig/srpc/`
   * Zorg ervoor dat `Only Modified` niet is geselecteerd.
   * Selecteer **[!UICONTROL Activate]**.


## Gebruikersgegevens {#managing-user-data} beheren

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak in publicatieomgeving worden ingevoerd, gaat u naar:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Solr opnieuw indexeren voor DSRP {#reindexing-solr-for-dsrp}

Als u DSRP Solr opnieuw wilt indexeren, volgt u de documentatie voor [het opnieuw indexeren van MSRP](msrp.md#msrp-reindex-tool), echter wanneer het opnieuw indexeren voor DSRP, gebruik in plaats daarvan deze URL: **/services/social/datastore/rdb/rendex**

Bijvoorbeeld, zou een krullbevel om DSRP opnieuw te indexeren als dit kijken:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```

