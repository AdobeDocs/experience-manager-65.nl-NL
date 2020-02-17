---
title: DSRP - Relational Database Storage Resource Provider
seo-title: DSRP - Relational Database Storage Resource Provider
description: AEM-gemeenschappen instellen om een relationele database te gebruiken als de algemene opslag
seo-description: AEM-gemeenschappen instellen om een relationele database te gebruiken als de algemene opslag
uuid: f364e7da-ee54-4ab2-a630-7ec9239005ac
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d23acb18-6761-4290-9e7a-a434582791bd
translation-type: tm+mt
source-git-commit: b7c790681034e9950aa43738310f7af8b1dd0085

---


# DSRP - Relational Database Storage Resource Provider {#dsrp-relational-database-storage-resource-provider}

## Over DSRP {#about-dsrp}

Wanneer de Gemeenschappen AEM wordt gevormd om een relationele gegevensbestand als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [Kenmerken van Opties](working-with-srp.md#characteristics-of-srp-options) SRP en [Aanbevolen Topologieën](topologies.md).

## Vereisten {#requirements}

* [MySQL](#mysql-configuration), een relationele database
* [Apache Solr](#solr-configuration), een zoekplatform

>[!NOTE]
>
>De standaardopslagconfiguratie wordt nu opgeslagen in conf-pad(`/conf/global/settings/community/srpc/defaultconfiguration`) in plaats van enz.-pad (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt aangeraden de [migratiestappen](#zerodt-migration-steps) te volgen om de standaardprocedures naar behoren te laten werken.


## Configuratie van relationele database {#relational-database-configuration}

### MySQL-configuratie {#mysql-configuration}

Een installatie MySQL kan tussen enablement eigenschappen en gemeenschappelijke opslag (DSRP) binnen de zelfde verbindingspool worden gedeeld door verschillende gegevensbestand (schema) namen en ook verschillende verbindingen (server:haven) te gebruiken.

Voor installatie en configuratiedetails, zie Configuratie [MySQL voor DSRP](dsrp-mysql.md).

### Solr-configuratie {#solr-configuration}

Een Solr installatie kan tussen de knoopopslag (Oak) en gemeenschappelijke opslag (SRP) worden gedeeld door verschillende inzamelingen te gebruiken.

Als zowel de Oak als SRP inzamelingen intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productieomgevingen biedt de SolrCloud-modus betere prestaties dan de zelfstandige modus (één lokale Solr-instelling).

Voor installatie en configuratiedetails, zie de Configuratie van [Solr voor SRP](solr.md).

### DSRP selecteren {#select-dsrp}

De console [van de Configuratie van de](srp-config.md) Opslag staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

Op auteur, om tot de console van de Configuratie van de Opslag toegang te hebben

* Aanmelden met beheerdersrechten
* Vanuit het **hoofdmenu**

   * Selecteer **[!UICONTROL Gereedschappen]** (in het linkerdeelvenster)
   * Selecteer **[!UICONTROL Gemeenschappen]**
   * Opslagconfiguratie **[!UICONTROL selecteren]**

      * De resulterende locatie is bijvoorbeeld: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)
      >[!NOTE]
      >
      >De standaardopslagconfiguratie wordt nu opgeslagen in conf-pad(`/conf/global/settings/community/srpc/defaultconfiguration`) in plaats van enz.-pad (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt aangeraden de [migratiestappen](#zerodt-migration-steps) te volgen om de standaardprocedures naar behoren te laten werken.

![chlimage_1-128](assets/chlimage_1-128.png)

* DSRP ( **[!UICONTROL Database Storage Resource Provider) selecteren]**
* **Databaseconfiguratie**

   * **[!UICONTROL JDBC-gegevensbronnaam]**

      De naam die aan verbinding MySQL wordt gegeven moet het zelfde zijn zoals ingegaan in configuratie [JDBC OSGi](dsrp-mysql.md#configurejdbcconnections)

      *standaard*: gemeenschappen

   * **[!UICONTROL Databasenaam]**

      Naam die aan schema in [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script) manuscript wordt gegeven

      *standaard*: gemeenschappen

* **SolrConfiguration**

   * **[Zookeeper](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files)-host **

      Laat deze waarde leeg als Solr wordt uitgevoerd met de interne ZooKeeper. Anders, wanneer het lopen op wijze [SolrCloud met externe ZooKeeper, plaats deze waarde aan URI voor ZooKeeper, zoals](solr.md#solrcloud-mode) *my.server.com:80*

      *standaard*: *&lt;blank>*

   * **[!UICONTROL Solr URL]**

      *standaard*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr Collection]**

      *standaard*: verzameling1

* Selecteer **[!UICONTROL Verzenden]**.

### Nul stappen voor downtime migratie voor standaardconfiguratie {#zerodt-migration-steps}

Ga als volgt te werk om ervoor te zorgen dat de standaardpagina [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) naar behoren werkt:

1. Wijzig de naam van het pad bij `/etc/socialconfig` aan `/etc/socialconfig_old`, zodat de systeemconfiguratie terugvalt naar jsrp (standaard).
1. Ga naar standaardpagina [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), waar jsrp wordt gevormd. Klik op de knop **[!UICONTROL Verzenden]** , zodat er een nieuw standaardconfiguratieknooppunt wordt gemaakt `/conf/global/settings/community/srpc`.
1. Verwijder de gemaakte standaardconfiguratie `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieer de oude configuratie `/etc/socialconfig_old/srpc/defaultconfiguration` in plaats van het verwijderde knooppunt (`/conf/global/settings/community/srpc/defaultconfiguration`) in de vorige stap.
1. Verwijder het oude knooppunt etc `/etc/socialconfig_old`.

## De configuratie publiceren {#publishing-the-configuration}

DSRP moet als gemeenschappelijke opslag op alle auteur worden geïdentificeerd en instanties publiceren.

De identieke configuratie beschikbaar stellen in de publicatieomgeving:

* Op auteur:

   * Navigeer van hoofdmenu aan **[!UICONTROL Hulpmiddelen > Verrichtingen > Replicatie]**
   * Dubbelklik op Boomstructuur **activeren **
   * **Startpad:**

      * Bladeren naar `/etc/socialconfig/srpc/`
   * Zorg ervoor `Only Modified` dat deze optie niet is geselecteerd.
   * Selecteer **[!UICONTROL Activeren]**


## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak worden ingevoerd in de publicatieomgeving, gaat u naar

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Solr opnieuw indexeren voor DSRP {#reindexing-solr-for-dsrp}

Als u DSRP Solr opnieuw wilt indexeren, volgt u de documentatie voor het opnieuw [indexeren van MSRP](msrp.md#msrp-reindex-tool), maar gebruikt u in plaats daarvan deze URL wanneer u opnieuw indexeert voor DSRP: **/services/social/datastore/rdb/rendex**

Bijvoorbeeld, zou een krullbevel om DSRP opnieuw te indexeren als dit kijken:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```

