---
title: MSRP - MongoDB Storage Resource Provider
seo-title: MSRP - MongoDB Storage Resource Provider
description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
seo-description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
uuid: 9fc06d4f-a60f-4ce3-8586-bcc836aa7de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 048f7b30-20c3-4567-bd32-38cf2643cf39
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---


# MSRP - MongoDB Storage Resource Provider {#msrp-mongodb-storage-resource-provider}

## Info over MSRP {#about-msrp}

Wanneer AEM Communities wordt gevormd om MSRP als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [Kenmerken van SRP Options](working-with-srp.md#characteristics-of-srp-options) en [Recommended Topologies](topologies.md).

## Vereisten {#requirements}

* [MongoDB](https://www.mongodb.org/):

   * Versie 2.6 of hoger
   * Het is niet nodig om mongo&#39;s te configureren of te sharding
   * adviseert sterk gebruik van een [replica reeks](#mongoreplicaset)
   * Kan op dezelfde host worden uitgevoerd als AEM of extern worden uitgevoerd

* [Apache Solr](https://lucene.apache.org/solr/):

   * Solr versie 7.0
   * Solr vereist Java 1.7 of hoger
   * Er is geen service nodig
   * Keuze van uitvoeringsmodi:
      * Standalone modus
      * [SolrCloud-modus](solr.md#solrcloud-mode)  (aanbevolen voor productieomgevingen)
   * Keuze van meertalig zoeken (MLS):
      * [Standaard MLS installeren](solr.md#installing-standard-mls)
      * [Geavanceerde MLS installeren](solr.md#installing-advanced-mls)

## MongoDB-configuratie {#mongodb-configuration}

### Selecteer MSRP {#select-msrp}

Met de [Opslagconfiguratieconsole](srp-config.md) kunt u de standaardopslagconfiguratie selecteren, die aangeeft welke implementatie van SRP moet worden gebruikt.

Op auteur, om tot de console van de Configuratie van de Opslag toegang te hebben:

* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]** bij globale navigatie.

![msrp](assets/msrp.png)

* Selecteer **[!UICONTROL MongoDB Storage Resource Provider (MSRP)]**
* **[!UICONTROL mongoDB Configuration]**

   * **[!UICONTROL mongoDB URI]**

      *standaard*: mongodb://localhost/?maxPoolSize=10&amp;waitQueueMultiple=5&amp;readPreference=secondaryPreferred

   * **[!UICONTROL mongoDB Database]**

      *standaard*: gemeenschappen

   * **[!UICONTROL mongoDB UGC Collection]**

      *standaard*: content

   * **[!UICONTROL mongoDB Attachment Collection]**

      *standaard*: bijlagen

* **[!UICONTROL SolrConfiguration]**

   * **[](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files) ZookeeperHost**

      Wanneer het lopen op [wijze SolrCloud](solr.md#solrcloud-mode) met een externe ZooKeeper, plaats deze waarde aan `HOST:PORT` voor ZooKeeper, zoals *my.server.com:2181*

      Voor ZooKeeper Ensemble, ga komma-gescheiden `HOST:PORT` waarden, zoals *host1:2181,host2:2181* in

      Laat leeg als Solr in zelfstandige modus wordt uitgevoerd met de interne ZooKeeper.
      *Standaard*:  *&lt;blank>*

      * **[!UICONTROL Solr URL]**
De URL die wordt gebruikt om te communiceren met Solr in zelfstandige modus.
Leeg laten als deze wordt uitgevoerd in de SolrCloud-modus.

         *Standaard*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Solr Collection]**
De naam van de Solr-verzameling.

         *Standaard*: verzameling1

* Selecteer **[!UICONTROL Submit]**

>[!NOTE]
>
>De database mongoDB, die standaard de naam `communities` heeft, mag niet worden ingesteld op de naam van een database die wordt gebruikt voor [knooppuntopslag of gegevens (binair) winkels](../../help/sites-deploying/data-store-config.md). Zie ook [Opslagelementen in AEM 6.5](../../help/sites-deploying/storage-elements-in-aem-6.md).

### MongoDB Replica-set {#mongodb-replica-set}

Voor het productiemilieu, wordt het sterk geadviseerd om een replicaset, een cluster van servers te installeren MongoDB die primaire-secundaire replicatie en geautomatiseerde failover uitvoert.

Voor meer informatie over replicasets gaat u naar de [Replication](https://docs.mongodb.org/manual/replication/)-documentatie van MongoDB.

Als u met replicasets wilt werken en wilt leren hoe u verbindingen tussen toepassingen en MongoDB-instanties kunt definiëren, raadpleegt u de documentatie van MongoDB [Verbindingsreeks URI Format](https://docs.mongodb.org/manual/reference/connection-string/).

#### Voorbeeld-URL voor verbinding maken met een replicaset {#example-url-for-connecting-to-a-replica-set}

```shell
# Example url for:
# servers "mongoserver1", "mongoserver2", "mongoserver3"
# replica set 'rs0'
# port numbers only necessary if not default port 27017
mongodb://mongoserver1:<mongoport1>,mongoserver2:<mongoport2>,mongoserver3:<mongoport3>/?replicaSet=rs0&maxPoolSize=100&waitQueueMultiple=50&readPreference=secondaryPreferred
```

## Solr-configuratie {#solr-configuration}

Een installatie Solr kan tussen de knoopopslag (Eak) en gemeenschappelijke opslag (MSRP) worden gedeeld door verschillende inzamelingen te gebruiken.

Als zowel de Oak als de inzamelingen MSRP intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productieomgevingen biedt de [SolrCloud-modus](solr.md#solrcloud-mode) betere prestaties in vergelijking met de standalone modus (één lokale Solr-instelling).

Voor configuratiedetails, zie [Solr Configuratie voor SRP](solr.md).

### {#upgrading} bijwerken

Als bevordering van een vroegere die versie met MSRP wordt gevormd, zal het noodzakelijk zijn:

1. [upgrade uitvoeren naar AEM Communities](upgrade.md)
1. Nieuwe Solr-configuratiebestanden installeren
   * Voor [standaard MLS](solr.md#installing-standard-mls)
   * Voor [advanced MLS](solr.md#installing-advanced-mls)
1. MSRP opnieuw indexeren
Zie sectie [MSRP Reindex Tool](#msrp-reindex-tool)

## De configuratie {#publishing-the-configuration} publiceren

MSRP moet als gemeenschappelijke opslag op alle auteur worden geïdentificeerd en instanties publiceren.

Meld u aan bij de auteur en voer de volgende stappen uit om de identieke configuratie beschikbaar te maken in de publicatieomgeving:

* Navigeer van hoofdmenu aan **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]**.
* Selecteer **[!UICONTROL Activate Tree]**
* **[!UICONTROL Start Path]**:
   * Bladeren naar `/etc/socialconfig/srpc/`
* Selecteer **[!UICONTROL Activate]**

## Gebruikersgegevens {#managing-user-data} beheren

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, vaak ingevoerd in de publicatieomgeving, gaat u naar

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## MSRP-herindex {#msrp-reindex-tool}

Er is een eindpunt van HTTP voor het opnieuw indexeren van Solr voor MSRP wanneer het installeren van nieuwe configuratiedossiers of het herstellen van een beschadigde index van Solr.

Met dit hulpmiddel, is MongoDB de bron van *waarheid* voor MSRP; Er hoeven alleen back-ups van MongoDB te worden gemaakt.

De volledige UGC-structuur kan opnieuw worden gedecodeerd, of alleen een specifieke substructuur, zoals opgegeven door de parameter *path *data.

Dit gereedschap kan vanaf de opdrachtregel worden uitgevoerd met cURL of een ander HTTP-gereedschap.

Wanneer het opnieuw indexeren, is er een compensatie tussen geheugen en prestaties die door de *batchSize *data parameter worden gecontroleerd, die specificeert hoeveel UGC- verslagen per partij opnieuw worden gedesdexeerd.

Een redelijke standaardwaarde is 5000:

* Als het geheugen een probleem is, geeft u een kleiner getal op
* Als snelheid een probleem is, geeft u een groter getal op om de snelheid te verhogen

### Het Lopen Hulpmiddel van Herindex MSRP gebruikend bevel cURL {#running-msrp-reindex-tool-using-curl-command}

Het volgende cURL bevel toont wat noodzakelijk voor een HTTP- verzoek is om UGC te herindexeren die in MSRP wordt opgeslagen.

De basisindeling is:

cURL -u *signin* -d *data* *rendex-url*

*sign* = administrator-id:password Bijvoorbeeld: admin:admin

*data* = &quot;batchSize=*size*&amp;path=*path&quot;*

*size* = hoeveel UGC-items opnieuw moeten worden geindexeerd per bewerking 
`/content/usergenerated/asi/mongo/`

*path* = de hoofdlocatie van de boomstructuur van UGC naar opnieuw indexeren

* Als u alle UGC opnieuw wilt indexeren, geeft u de waarde op van de eigenschap `asipath`van
   `/etc/socialconfig/srpc/defaultconfiguration`
* Als u de index wilt beperken tot UGC, geeft u een substructuur op van `asipath`

*redex-url* = het eindpunt voor herindexering van SRP 
`http://localhost:4503/services/social/datastore/mongo/reindex`

>[!NOTE]
>
>Als u [opnieuw indexeert DSRP Solr](dsrp.md) bent, is URL **/services/social/datastore/rdb/reindex**

### Voorbeeld van MSRP-reindex {#msrp-reindex-example}

```shell
curl -s -u admin:admin -d 'batchSize=10000&path=/content/usergenerated/asi/mongo/' http://localhost:4503/services/social/datastore/mongo/reindex
```

## Hoe te om MSRP {#how-to-demo-msrp} te demo

Om MSRP voor een demonstratie of ontwikkelomgeving te plaatsen, zie [HowTo Opstelling MongoDB voor Demo](demo-mongo.md).

## Problemen oplossen {#troubleshooting}

### UGC niet zichtbaar in MongoDB {#ugc-not-visible-in-mongodb}

Zorg ervoor MSRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Standaard is de leverancier van de opslagbron JSRP.

Op alle auteur en publiceer AEM instanties, herzie [de console van de Configuratie van de Opslag](srp-config.md) of controleer de AEM bewaarplaats:

* In JCR, als [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Bevat geen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) knoop, het betekent de opslagleverancier JSRP is.
   * Als de srpc knoop bestaat en knoop [default configuration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) bevat, zouden de eigenschappen van de standaardconfiguratie MSRP moeten bepalen om de standaardleverancier te zijn.

### UGC verdwijnt na upgrade {#ugc-disappears-after-upgrade}

Als u een upgrade uitvoert vanaf een bestaande AEM Communities 6.0-site, moet een bestaande UGC worden omgezet om te voldoen aan de vereiste structuur voor de [SRP](srp.md)-API na een upgrade naar AEM Communities 6.3.

Er is een open bronhulpmiddel beschikbaar op GitHub voor dit doel:

* [AEM Communities UGC-migratiehulpprogramma](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

Het migratiehulpmiddel kan worden aangepast om UGC uit vroegere versies van AEM sociale gemeenschappen voor invoer in AEM Communities 6.1 of later uit te voeren.

### Fout: niet-gedefinieerde veldprovider_id {#error-undefined-field-provider-id}

Als de volgende fout in de logboeken wordt gezien, wijst het erop het Solr schemadossier niet behoorlijk wordt gevormd.

#### JsonMappingException: undefined field provider_id {#jsonmappingexception-undefined-field-provider-id}

```xml
Caused by: com.fasterxml.jackson.databind.JsonMappingException: undefined field provider_id
at com.fasterxml.jackson.databind.ser.DefaultSerializerProvider.serializeValue(DefaultSerializerProvider.java:129)
at com.fasterxml.jackson.databind.ObjectMapper.writeValue(ObjectMapper.java:1819)
at com.adobe.cq.social.scf.core.BaseSocialComponent.toJSONString(BaseSocialComponent.java:196)
... 124 common frames omitted
```

Om de fout op te lossen, wanneer het volgen van de instructies voor [Installing Standard MLS](solr.md#installing-standard-mls), zorg ervoor:

* De XML-configuratiebestanden zijn naar de juiste Solr-locatie gekopieerd.
* Solr werd opnieuw begonnen nadat de nieuwe configuratiedossiers bestaande degenen vervingen.

### Beveiligde verbinding met MongoDB mislukt {#secure-connection-to-mongodb-fails}

Als een poging om een beveiligde verbinding te maken met de MongoDB-server mislukt als gevolg van een ontbrekende klassedefinitie, moet de MongoDB-stuurprogrammabundel, `mongo-java-driver`, worden bijgewerkt, die beschikbaar is in de openbaar gemaakte opslagplaats.

1. Download het stuurprogramma van [https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar](https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar) (versie 2.13.2 of hoger).
1. Kopieer de bundel naar de map &quot;crx-quickstart/install&quot; voor een AEM.
1. Start de AEM opnieuw.

## Bronnen {#resources}

* [AEM met MongoDB](../../help/sites-deploying/aem-with-mongodb.md)
* [MongoDB-documentatie](https://docs.mongodb.org/)

