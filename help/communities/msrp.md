---
title: MSRP - MongoDB Storage Resource Provider
seo-title: MSRP - MongoDB Storage Resource Provider
description: AEM-gemeenschappen instellen om een relationele database te gebruiken als de algemene opslag
seo-description: AEM-gemeenschappen instellen om een relationele database te gebruiken als de algemene opslag
uuid: 9fc06d4f-a60f-4ce3-8586-bcc836aa7de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 048f7b30-20c3-4567-bd32-38cf2643cf39
translation-type: tm+mt
source-git-commit: f7e5afe46100db7837647ac89aaf58cf101143b0

---


# MSRP - MongoDB Storage Resource Provider {#msrp-mongodb-storage-resource-provider}

## Over MSRP {#about-msrp}

Wanneer de Gemeenschappen AEM wordt gevormd om MSRP als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [Kenmerken van Opties](working-with-srp.md#characteristics-of-srp-options) SRP en [Aanbevolen Topologieën](topologies.md).

## Vereisten {#requirements}

* [MongoDB](https://www.mongodb.org/):

   * Versie 2.6 of hoger
   * Het is niet nodig om mongo&#39;s te configureren of te sharding
   * Het gebruik van een [replicaset wordt sterk aanbevolen](#mongoreplicaset)
   * Kan op dezelfde host als AEM worden uitgevoerd of extern worden uitgevoerd

* [Apache Solr](https://lucene.apache.org/solr/):

   * Versie 4.10 of versie 5
   * Solr vereist Java 1.7 of hoger
   * Er is geen service nodig
   * Keuze van uitvoeringsmodi:
      * Standalone modus
      * [SolrCloud-modus](solr.md#solrcloud-mode) (aanbevolen voor productieomgevingen)
   * Keuze van meertalig zoeken (MLS)
      * [Standaard MLS installeren](solr.md#installing-standard-mls)
      * [Geavanceerde MLS installeren](solr.md#installing-advanced-mls)

## MongoDB-configuratie {#mongodb-configuration}

### Selecteer MSRP {#select-msrp}

De console [van de Configuratie van de](srp-config.md) Opslag staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

Op auteur, om tot de console van de Configuratie van de Opslag toegang te hebben:

* Selecteer in de globale navigatie **[!UICONTROL Gereedschappen]** > **[!UICONTROL Gemeenschappen]** > **[!UICONTROL Opslagconfiguratie]**.

![chlimage_1-28](assets/chlimage_1-28.png)

* MSRP ( **[!UICONTROL MongoDB Storage Resource Provider) selecteren]**
* **[!UICONTROL mongoDB-configuratie]**

   * **[!UICONTROL mongoDB URI]**

      *standaard*: mongodb://localhost/?maxPoolSize=10&amp;waitQueueMultiple=5&amp;readPreference=secondaryPreferred

   * **[!UICONTROL mongoDB-database]**

      *standaard*: gemeenschappen

   * **[!UICONTROL mongoDB UGC Collection]**

      *standaard*: content

   * **[!UICONTROL MongoDB-bijlage verzamelen]**

      *standaard*: bijlagen

* **[!UICONTROL SolrConfiguration]**

   * **[Zookeeper](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files)-host **

      Wanneer het lopen op wijze [SolrCloud met een externe ZooKeeper, plaats deze waarde aan](solr.md#solrcloud-mode) voor ZooKeeper, zoals `HOST:PORT` *my.server.com:2181*

      Voor een Samenvoegsel ZooKeeper, ga komma-gescheiden `HOST:PORT` waarden, zoals *gastheer1:2181, gastheer2:2181 in*

      Laat leeg als Solr in zelfstandige modus wordt uitgevoerd met de interne ZooKeeper.
      *Standaard*: *&lt;blank>*

      * **[!UICONTROL Solr URL]**De URL die wordt gebruikt om te communiceren met Solr in zelfstandige modus.
Leeg laten als deze wordt uitgevoerd in de SolrCloud-modus.
         *Standaard*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Solr Collection]**De Solr inzamelingsnaam.
         *Standaard*: verzameling1

* Selecteer **[!UICONTROL Verzenden]**

>[!NOTE]
>
>De database mongoDB, die standaard de naam heeft, `communities`mag niet worden ingesteld op de naam van een database die wordt gebruikt voor [knooppuntopslag of gegevensopslag](../../help/sites-deploying/data-store-config.md)(binair). Zie ook [Opslagelementen in AEM 6.5](../../help/sites-deploying/storage-elements-in-aem-6.md).


### MongoDB Replica-set {#mongodb-replica-set}

Voor de productieomgeving wordt het ten zeerste aanbevolen een replicaset in te stellen, een cluster van MongoDB-servers die master-slave-replicatie en geautomatiseerde failover implementeert.

Voor meer informatie over replicasets gaat u naar de documentatie van de [replicatie](https://docs.mongodb.org/manual/replication/) van MongoDB.

Als u met replicasets wilt werken en wilt leren hoe u verbindingen tussen toepassingen en MongoDB-instanties kunt definiëren, gaat u naar de documentatie bij URI-indeling [van](https://docs.mongodb.org/manual/reference/connection-string/) verbindingstekenreeks van MongoDB.

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

Voor productieomgevingen biedt de [SolrCloud-modus](solr.md#solrcloud-mode) betere prestaties dan de zelfstandige modus (één lokale Solr-instelling).

Voor configuratiedetails, zie de Configuratie van [Solr voor SRP](solr.md).

### Bijwerken {#upgrading}

Als bevordering van een vroegere die versie met MSRP wordt gevormd, zal het noodzakelijk zijn:

1. Voer de [upgrade naar AEM-gemeenschappen uit](upgrade.md)
1. Nieuwe Solr-configuratiebestanden installeren
   * Voor [standaard MLS](solr.md#installing-standard-mls)
   * Voor [geavanceerde MLS](solr.md#installing-advanced-mls)
1. Reindex MSRPSee sectie [MSRP Reindex Tool](#msrp-reindex-tool)

## De configuratie publiceren {#publishing-the-configuration}

MSRP moet als gemeenschappelijke opslag op alle auteur worden geïdentificeerd en instanties publiceren.

Meld u aan bij de auteur en voer de volgende stappen uit om de identieke configuratie beschikbaar te maken in de publicatieomgeving:

* Navigeer van hoofdmenu aan **[!UICONTROL Hulpmiddelen]** > **[!UICONTROL Verrichtingen]** > **[!UICONTROL Replicatie]**.
* Boomstructuur **[!UICONTROL activeren selecteren]**
* **[!UICONTROL Startpad]**:
   * Bladeren naar `/etc/socialconfig/srpc/`
* Selecteer **[!UICONTROL Activeren]**

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak worden ingevoerd in de publicatieomgeving, gaat u naar

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## MSRP opnieuw indexeren {#msrp-reindex-tool}

Er is een eindpunt van HTTP voor het opnieuw indexeren van Solr voor MSRP wanneer het installeren van nieuwe configuratiedossiers of het herstellen van een beschadigde index van Solr.

Met dit hulpmiddel, is MongoDB de bron van *waarheid* voor MSRP; Er hoeven alleen back-ups van MongoDB te worden gemaakt.

De volledige UGC-structuur kan opnieuw worden gedecodeerd, of alleen een specifieke substructuur, zoals opgegeven door de parameter *path *data.

Dit gereedschap kan vanaf de opdrachtregel worden uitgevoerd met cURL of een ander HTTP-gereedschap.

Wanneer het opnieuw indexeren, is er een compensatie tussen geheugen en prestaties die door de *batchSize *data parameter worden gecontroleerd, die specificeert hoeveel UGC- verslagen per partij opnieuw worden gedesdexeerd.

Een redelijke standaardwaarde is 5000:

* Als het geheugen een probleem is, geeft u een kleiner getal op
* Als snelheid een probleem is, geeft u een groter getal op om de snelheid te verhogen

### Gereedschap MSRP opnieuw indexeren uitvoeren met cURL-opdracht {#running-msrp-reindex-tool-using-curl-command}

Het volgende cURL bevel toont wat noodzakelijk voor een HTTP- verzoek is om UGC te herindexeren die in MSRP wordt opgeslagen.

De basisindeling is:

cURL -u *sign* -d *data* *redex-url*

*sign* = administrator-id:passwordFor, voorbeeld: admin:admin

*data* = &quot;batchSize=*size*&amp;path=*path&quot;*

*size* = hoeveel UGC-items opnieuw moeten worden geindexeerd per bewerking`/content/usergenerated/asi/mongo/`

*path* = de hoofdlocatie van de boomstructuur van UGC naar opnieuw indexeren

* Als u alle UGC opnieuw wilt indexeren, geeft u de waarde op van de `asipath`eigenschap van
   `/etc/socialconfig/srpc/defaultconfiguration`
* Als u de index wilt beperken tot UGC, geeft u een substructuur op van `asipath`

*herdex-url* = het eindpunt voor herindexering van SRP`http://localhost:4503/services/social/datastore/mongo/reindex`

>[!NOTE]
>
>Als u DSRP Solr [opnieuw](dsrp.md)dexeert, is URL **/services/social/datastore/rdb/reindex**


### Voorbeeld van MSRP-reindex {#msrp-reindex-example}

```shell
curl -s -u admin:admin -d 'batchSize=10000&path=/content/usergenerated/asi/mongo/' http://localhost:4503/services/social/datastore/mongo/reindex
```

## Hoe te om MSRP te demo {#how-to-demo-msrp}

Om MSRP voor een demonstratie of ontwikkelomgeving te plaatsen, zie [HowTo Opstelling MongoDB voor Demo](demo-mongo.md).

## Problemen oplossen {#troubleshooting}

### UGC niet zichtbaar in MongoDB {#ugc-not-visible-in-mongodb}

Zorg ervoor MSRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Standaard is de leverancier van de opslagbron JSRP.

Op alle auteur en publiceer AEM instanties, vernieuw de console [van de Configuratie van de](srp-config.md) Opslag of controleer de bewaarplaats AEM:

* In JCR, indien [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Bevat geen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) knoop, betekent het de opslagleverancier JSRP is.
   * Als de srpc knoop bestaat en knoop [standaardconfiguratie](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)bevat, zouden de eigenschappen van de standaardconfiguratie MSRP moeten bepalen om de standaardleverancier te zijn.

### UGC verdwijnt na upgrade {#ugc-disappears-after-upgrade}

Als een upgrade wordt uitgevoerd van een bestaande AEM Communities 6.0-locatie, moet een reeds bestaande UGC worden omgezet in overeenstemming met de structuur die vereist is voor de [SRP](srp.md) API na een upgrade naar AEM Communities 6.3.

Er is een open bronhulpmiddel beschikbaar op GitHub voor dit doel:

* [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

Het migratiehulpmiddel kan worden aangepast om UGC uit vroegere versies van AEM sociale gemeenschappen voor invoer in Gemeenschappen te exporteren AEM 6.1 of later.

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

Als u de fout wilt oplossen, moet u bij het volgen van de instructies voor het [installeren van de standaard-MLS](solr.md#installing-standard-mls):

* De XML-configuratiebestanden zijn naar de juiste Solr-locatie gekopieerd.
* Solr werd opnieuw begonnen nadat de nieuwe configuratiedossiers bestaande degenen vervingen.

### Beveiligde verbinding met MongoDB mislukt {#secure-connection-to-mongodb-fails}

Als een poging om een beveiligde verbinding te maken met de MongoDB-server mislukt als gevolg van een ontbrekende klassedefinitie, moet de MongoDB-stuurprogrammabundel, die beschikbaar is `mongo-java-driver`in de openbare gegevensopslagruimte, worden bijgewerkt.

1. Download het stuurprogramma van [https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar](https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar) (versie 2.13.2 of hoger).
1. Kopieer de bundel naar de map &quot;crx-quickstart/install&quot; voor een AEM-instantie.
1. Start de AEM-instantie opnieuw.

## Bronnen {#resources}

* [AEM met MongoDB](../../help/sites-deploying/aem-with-mongodb.md)
* [MongoDB-documentatie](https://docs.mongodb.org/)

