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

Zie ook [&#x200B; Kenmerken van Opties SRP &#x200B;](working-with-srp.md#characteristics-of-srp-options) en [&#x200B; Aanbevolen Topologieën &#x200B;](topologies.md).

## Vereisten {#requirements}

* [&#x200B; MySQL &#x200B;](#mysql-configuration), een relationele gegevensbestand.
* [&#x200B; Apache Solr &#x200B;](#solr-configuration), een onderzoeksplatform.

>[!NOTE]
>
>De standaard opslagconfiguratie wordt nu opgeslagen in conf weg (`/conf/global/settings/community/srpc/defaultconfiguration`) in plaats van `etc` weg (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt geadviseerd om de [&#x200B; migratiestappen &#x200B;](#zerodt-migration-steps) te volgen om het werk standaard zoals verwacht te maken.

## Configuratie van relationele database {#relational-database-configuration}

### MySQL-configuratie {#mysql-configuration}

Een installatie MySQL kan tussen enablement eigenschappen en gemeenschappelijke opslag (DSRP) binnen de zelfde verbindingspool worden gedeeld door verschillende gegevensbestand (schema) namen en ook verschillende verbindingen (server:haven) te gebruiken.

Voor installatie en configuratiedetails, zie [&#x200B; Configuratie MySQL voor DSRP &#x200B;](dsrp-mysql.md).

### Solr-configuratie {#solr-configuration}

Een Solr installatie kan tussen de knoopopslag (Oak) en gemeenschappelijke opslag (SRP) worden gedeeld door verschillende inzamelingen te gebruiken.

Als zowel de Oak als SRP inzamelingen intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productieomgevingen biedt de SolrCloud-modus betere prestaties dan de zelfstandige modus (één lokale Solr-instelling).

Voor installatie en configuratiedetails, zie [&#x200B; Configuratie Solr voor SRP &#x200B;](solr.md).

### DSRP selecteren {#select-dsrp}

De [&#x200B; console van de Configuratie van de Opslag &#x200B;](srp-config.md) staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

Op auteur, om tot de console van de Configuratie van de Opslag toegang te hebben

* Aanmelden met beheerdersrechten
* Van het **belangrijkste menu**

   * Selecteer **[!UICONTROL Tools]** (in het linkerdeelvenster)
   * Selecteren **[!UICONTROL Communities]**
   * Selecteren **[!UICONTROL Storage Configuration]**

      * Als voorbeeld, is de resulterende plaats: [&#x200B; http://localhost:4502/communities/admin/defaultsrp &#x200B;](http://localhost:4502/communities/admin/defaultsrp)

     >[!NOTE]
     >
     >De standaardopslagconfiguratie wordt nu opgeslagen in conf weg (`/conf/global/settings/community/srpc/defaultconfiguration`)      in plaats van `etc` path (`/etc/socialconfig/srpc/defaultconfiguration`). U wordt geadviseerd om de [&#x200B; migratiestappen &#x200B;](#zerodt-migration-steps) te volgen om het werk standaard zoals verwacht te maken.

  ![&#x200B; dsrp-config &#x200B;](assets/dsrp-config.png)

* Selecteren **[!UICONTROL Database Storage Resource Provider (DSRP)]**
* **Configuratie van het Gegevensbestand**

   * **[!UICONTROL JDBC datasource name]**

     De naam die aan verbinding MySQL wordt gegeven moet het zelfde zijn zoals ingegaan in [&#x200B; configuratie JDBC OSGi &#x200B;](dsrp-mysql.md#configurejdbcconnections)

     *gebrek*: gemeenschappen

   * **[!UICONTROL Database name]**

     Naam die aan schema in [&#x200B; wordt gegeven init_schema.sql &#x200B;](dsrp-mysql.md#obtain-the-sql-script) manuscript

     *gebrek*: gemeenschappen

* **SolrConfiguration**

   * **[Zookeeper &#x200B;](https://solr.apache.org/guide/6_6/using-zookeeper-to-manage-configuration-files.html) Gastheer**

     Laat deze waarde leeg als Solr wordt uitgevoerd met de interne ZooKeeper. Elders, wanneer het lopen op [&#x200B; wijze SolrCloud &#x200B;](solr.md#solrcloud-mode) met een externe ZooKeeper, plaats deze waarde aan URI voor ZooKeeper, zoals *my.server.com:80*

     *gebrek*: *&lt;blank>*

   * **[!UICONTROL Solr URL]**

     *gebrek*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr Collection]**

     *gebrek*: collection1

* Selecteer **[!UICONTROL Submit]** .

### Nul stappen voor downtime migratie voor standaardconfiguratie {#zerodt-migration-steps}

Om ervoor te zorgen dat de standaardscheurpagina [&#x200B; http://localhost:4502/communities/admin/defaultsrp &#x200B;](http://localhost:4502/communities/admin/defaultsrp) zoals verwacht werkt, volg deze stappen:

1. Wijzig de naam van het pad op `/etc/socialconfig` in `/etc/socialconfig_old` , zodat de systeemconfiguratie terugvalt naar jsrp (standaard).
1. Ga naar standaardscheurpagina [&#x200B; http://localhost:4502/communities/admin/defaultsrp &#x200B;](http://localhost:4502/communities/admin/defaultsrp), waar jsrp wordt gevormd. Klik op de knop **[!UICONTROL submit]** , zodat er een nieuw standaardconfiguratieknooppunt wordt gemaakt op `/conf/global/settings/community/srpc` .
1. Verwijder de gemaakte standaardconfiguratie `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieer de oude configuratie `/etc/socialconfig_old/srpc/defaultconfiguration` in plaats van het verwijderde knooppunt (`/conf/global/settings/community/srpc/defaultconfiguration`) in de vorige stap.
1. Verwijder het oude `etc` knooppunt `/etc/socialconfig_old` .

## De configuratie publiceren {#publishing-the-configuration}

DSRP moet als gemeenschappelijke opslag op alle auteur worden geïdentificeerd en instanties publiceren.

De identieke configuratie beschikbaar stellen in de publicatieomgeving:

* Op auteur:

   * Ga van hoofdmenu naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]**
   * Dubbelklikken **[!UICONTROL Activate Tree]**
   * **Weg van het Begin**:

      * Bladeren naar `/etc/socialconfig/srpc/`

   * Zorg ervoor dat `Only Modified` niet is geselecteerd.
   * Selecteer **[!UICONTROL Activate]** .

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie betreffende *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, vaak ingegaan in publiceer milieu, bezoek:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Solr opnieuw indexeren voor DSRP {#reindexing-solr-for-dsrp}

Om DSRP Solr opnieuw te indexeren, volg de documentatie voor [&#x200B; opnieuw indexerend MSRP &#x200B;](msrp.md#msrp-reindex-tool), echter wanneer het opnieuw indexeren voor DSRP, gebruik in plaats daarvan dit URL: **/services/social/datastore/rdb/redex**

Bijvoorbeeld, zou een krullbevel om DSRP opnieuw te indexeren als dit kijken:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```
