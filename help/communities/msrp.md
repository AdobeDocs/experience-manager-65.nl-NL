---
title: MSRP - MongoDB Storage Resource Provider
description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 799d5ae1-caac-4c92-8835-696ad25de553
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 0%

---

# MSRP - MongoDB Storage Resource Provider {#msrp-mongodb-storage-resource-provider}

## Over MSRP {#about-msrp}

Wanneer AEM Communities wordt gevormd om MSRP als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [&#x200B; Kenmerken van Opties SRP &#x200B;](working-with-srp.md#characteristics-of-srp-options) en [&#x200B; Aanbevolen Topologieën &#x200B;](topologies.md).

## Vereisten {#requirements}

* [&#x200B; MongoDB &#x200B;](https://www.mongodb.org/):

   * Versie 2.6 of hoger
   * Het is niet nodig om mongo&#39;s te configureren of te sharding
   * Sterk adviseer gebruik van a [&#x200B; replica reeks &#x200B;](#mongoreplicaset)
   * Kan op dezelfde host worden uitgevoerd als AEM of extern worden uitgevoerd

* [&#x200B; Apache Solr &#x200B;](https://lucene.apache.org/solr/):

   * Solr versie 7.0
   * Solr vereist Java 1.7 of hoger
   * Er is geen service nodig
   * Keuze van uitvoeringsmodi:
      * Stand-alone modus
      * [&#x200B; wijze SolrCloud &#x200B;](solr.md#solrcloud-mode) (geadviseerd voor productiemilieu&#39;s)
   * Keuze van meertalig zoeken (MLS):
      * [Standaard MLS installeren](solr.md#installing-standard-mls)
      * [Geavanceerde MLS installeren](solr.md#installing-advanced-mls)

## MongoDB-configuratie {#mongodb-configuration}

### Selecteer MSRP {#select-msrp}

De [&#x200B; console van de Configuratie van de Opslag &#x200B;](srp-config.md) staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

Op auteur, om tot de console van de Configuratie van de Opslag toegang te hebben:

* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]** bij globale navigatie.

![&#x200B; msrp &#x200B;](assets/msrp.png)

* Selecteren **[!UICONTROL MongoDB Storage Resource Provider (MSRP)]**
* **[!UICONTROL mongoDB Configuration]**

   * **[!UICONTROL mongoDB URI]**

     *gebrek*: mongodb://localhost/?maxPoolSize=10&amp;waitQueueMultiple=5&amp;readPreference=secondaryPreferred

   * **[!UICONTROL mongoDB Database]**

     *gebrek*: gemeenschappen

   * **[!UICONTROL mongoDB UGC Collection]**

     *gebrek*: inhoud

   * **[!UICONTROL mongoDB Attachment Collection]**

     *gebrek*: gehechtheid

* **[!UICONTROL SolrConfiguration]**

   * **[Zookeeper &#x200B;](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files) Gastheer**

     Wanneer het lopen op [&#x200B; wijze SolrCloud &#x200B;](solr.md#solrcloud-mode) met een externe ZooKeeper, plaats deze waarde aan `HOST:PORT` voor ZooKeeper, zoals *my.server.com:2181*

     Voor een Samenvoegsel ZooKeeper, ga komma-gescheiden `HOST:PORT` waarden, zoals *host1 in:2181, host2:2181*

     Laat leeg als Solr in zelfstandige modus wordt uitgevoerd met de interne ZooKeeper.
     *Gebrek*: *&lt;blank>*

      * **[!UICONTROL Solr URL]**
De URL die wordt gebruikt om te communiceren met Solr in zelfstandige modus.
Leeg laten als u de SolrCloud-modus gebruikt.
        *Gebrek*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Solr Collection]**
De naam van de Solr-verzameling.
        *Gebrek*: collection1

* Selecteren **[!UICONTROL Submit]**

>[!NOTE]
>
>Het mongoDB gegevensbestand, dat aan de naam `communities` in gebreke blijft, zou niet aan de naam van een gegevensbestand moeten worden geplaatst dat voor [&#x200B; knoopopslag of gegevens (binair) opslag &#x200B;](../../help/sites-deploying/data-store-config.md) wordt gebruikt. Zie ook {de Elementen van de Opslag 0} in AEM 6.5 [&#128279;](../../help/sites-deploying/storage-elements-in-aem-6.md).

### MongoDB Replica-set {#mongodb-replica-set}

Voor het productiemilieu, wordt het sterk geadviseerd om een replicaset, een cluster van servers te installeren MongoDB die primaire-secundaire replicatie en geautomatiseerde failover uitvoert.

Om meer over replicasets te leren, bezoek de [&#x200B; documentatie van de Replicatie van MongoDB &#x200B;](https://docs.mongodb.org/manual/replication/).

Om met replicasets te werken en te leren hoe te om verbindingen tussen toepassingen en instanties te bepalen MongoDB, bezoek de [&#128279;](https://docs.mongodb.org/manual/reference/connection-string/) documentatie van het Formaat URI van het Koord van de Verbinding van MongoDB .

#### Voorbeeld-URL voor verbinding maken met een replicaset  {#example-url-for-connecting-to-a-replica-set}

```shell
# Example url for:
# servers "mongoserver1", "mongoserver2", "mongoserver3"
# replica set 'rs0'
# port numbers only necessary if not default port 27017
mongodb://mongoserver1:<mongoport1>,mongoserver2:<mongoport2>,mongoserver3:<mongoport3>/?replicaSet=rs0&maxPoolSize=100&waitQueueMultiple=50&readPreference=secondaryPreferred
```

## Solr-configuratie {#solr-configuration}

Een Solr installatie kan tussen de knoopopslag (Oak) en gemeenschappelijke opslag (MSRP) worden gedeeld door verschillende inzamelingen te gebruiken.

Als zowel de Oak als de inzamelingen MSRP intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productiemilieu&#39;s, [&#128279;](solr.md#solrcloud-mode) de wijze van SolrCloud  verstrekt betere prestaties over standalone wijze (enige, lokale opstelling Solr).

Voor configuratiedetails, zie [&#x200B; Configuratie Solr voor SRP &#x200B;](solr.md).

### Bijwerken {#upgrading}

Als bevordering van een vroegere die versie met MSRP wordt gevormd, zal het noodzakelijk zijn:

1. Voer de [&#x200B; verbetering aan AEM Communities &#x200B;](upgrade.md) uit
1. Nieuwe Solr-configuratiebestanden installeren
   * Voor [&#x200B; standaardMLS &#x200B;](solr.md#installing-standard-mls)
   * Voor [&#x200B; geavanceerde MLS &#x200B;](solr.md#installing-advanced-mls)
1. MSRP opnieuw indexeren
Zie sectie [&#x200B; MSRP het Hulpmiddel van de Reindex &#x200B;](#msrp-reindex-tool)

## De configuratie publiceren {#publishing-the-configuration}

MSRP moet als gemeenschappelijke opslag op alle auteur worden geïdentificeerd en instanties publiceren.

Meld u aan bij de auteur en voer de volgende stappen uit om de identieke configuratie beschikbaar te maken in de publicatieomgeving:

* Navigeer van hoofdmenu naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]** .
* Selecteren **[!UICONTROL Activate Tree]**
* **[!UICONTROL Start Path]** :
   * Bladeren naar `/etc/socialconfig/srpc/`
* Selecteren **[!UICONTROL Activate]**

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie betreffende *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, vaak ingegaan in publiceer milieu, bezoek

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## MSRP opnieuw indexeren {#msrp-reindex-tool}

Er is een eindpunt van HTTP voor het opnieuw indexeren van Solr voor MSRP wanneer het installeren van nieuwe configuratiedossiers of het herstellen van een beschadigde index van Solr.

Met dit hulpmiddel, is MongoDB de bron van *waarheid* voor MSRP; de steunen moeten slechts van MongoDB worden genomen.

De volledige UGC-structuur kan opnieuw worden gedecodeerd, of alleen een specifieke substructuur, zoals opgegeven door de parameter *path *data.

Dit gereedschap kan vanaf de opdrachtregel worden uitgevoerd met cURL of een ander HTTP-gereedschap.

Wanneer het opnieuw indexeren, is er een compensatie tussen geheugen en prestaties die door de *batchSize *data parameter worden gecontroleerd, die specificeert hoeveel UGC- verslagen per partij opnieuw worden gedesdexeerd.

Een redelijke standaardwaarde is 5000:

* Geef een kleiner getal op als het geheugen een probleem is
* Als snelheid een probleem is, geeft u een groter getal op om de snelheid te verhogen

### Gereedschap MSRP opnieuw indexeren uitvoeren met cURL-opdracht {#running-msrp-reindex-tool-using-curl-command}

Het volgende cURL bevel toont wat noodzakelijk voor een HTTP- verzoek is om UGC te herindexeren die in MSRP wordt opgeslagen.

De basisindeling is:

cURL - u *signaleert* - d *gegevens* *herdex-url*

*teken* = beheerder-identiteitskaart:wachtwoord
Bijvoorbeeld: admin:admin

*gegevens* = &quot;batchSize= *grootte* &amp;path= *weg&quot;*

*grootte* = hoeveel ingangen UGC aan herdex per verrichting
`/content/usergenerated/asi/mongo/`

*weg* = de wortelplaats van de boom van UGC aan herdex

* Om al UGC opnieuw te indexeren, specificeer de waarde van het `asipath` bezit van
  `/etc/socialconfig/srpc/defaultconfiguration`
* Als u de index wilt beperken tot UGC, geeft u een substructuur op van `asipath`

*herdex-url* = het eindpunt voor het opnieuw indexeren van SRP
`http://localhost:4503/services/social/datastore/mongo/reindex`

>[!NOTE]
>
>Als u [&#x200B; opnieuw indexeert DSRP Solr &#x200B;](dsrp.md) bent, is URL **/services/social/datastore/rdb/reindex**

### Voorbeeld van MSRP-reindex {#msrp-reindex-example}

```shell
curl -s -u admin:admin -d 'batchSize=10000&path=/content/usergenerated/asi/mongo/' http://localhost:4503/services/social/datastore/mongo/reindex
```

## Hoe te om MSRP te demo {#how-to-demo-msrp}

Om MSRP voor een demonstratie of ontwikkelomgeving te plaatsen, zie [&#x200B; HowTo Opstelling MongoDB voor Manifestatie &#x200B;](demo-mongo.md).

## Problemen oplossen {#troubleshooting}

### UGC niet zichtbaar in MongoDB {#ugc-not-visible-in-mongodb}

Zorg ervoor MSRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Standaard is de opslagbronprovider JSRP.

Voor alle auteur en publiceer AEM instanties, herzie de [&#x200B; console van de Configuratie van de Opslag &#x200B;](srp-config.md) of controleer de AEM bewaarplaats:

* In JCR, als [/etc/socialconfig &#x200B;](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Bevat geen [&#x200B; srpc &#x200B;](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) knoop, betekent het de opslagleverancier JSRP is.
   * Als de srpc knoop bestaat en knoop [&#x200B; standaardconfiguratie &#x200B;](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) bevat, zouden de eigenschappen van de standaardconfiguratie MSRP moeten bepalen om de standaardleverancier te zijn.

### UGC verdwijnt na upgrade {#ugc-disappears-after-upgrade}

Als de bevordering van een bestaande plaats van AEM Communities 6.0, om het even welk reeds bestaand UGC moet worden omgezet om in overeenstemming te zijn met de structuur die voor [&#x200B; wordt vereist SRP &#x200B;](srp.md) API na bevordering aan AEM Communities 6.3.

Er is een open bronhulpmiddel beschikbaar op GitHub voor dit doel:

* [&#x200B; het Hulpmiddel van de Migratie van AEM Communities UGC &#x200B;](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

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

Om de fout op te lossen, wanneer het volgen van de instructies voor [&#x200B; Installerend StandaardMLS &#x200B;](solr.md#installing-standard-mls), zorg ervoor:

* De XML-configuratiebestanden zijn naar de juiste Solr-locatie gekopieerd.
* Solr werd opnieuw begonnen nadat de nieuwe configuratiedossiers bestaande degenen vervingen.

### Beveiligde verbinding met MongoDB mislukt {#secure-connection-to-mongodb-fails}

Als een poging om een beveiligde verbinding te maken met de MongoDB-server mislukt als gevolg van een ontbrekende klassedefinitie, moet de MongoDB-stuurprogrammabundel `mongo-java-driver` worden bijgewerkt. Deze bundel is beschikbaar in de openbaar gemaakte opslagplaats.

1. Download de bestuurder van [&#x200B; https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar &#x200B;](https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar) (versie 2.13.2 of recenter).
1. Kopieer de bundel naar de map &quot;crx-quickstart/install&quot; voor een AEM.
1. Start de AEM opnieuw.

## Bronnen {#resources}

* [AEM met MongoDB](../../help/sites-deploying/aem-with-mongodb.md)
* [&#x200B; Documentatie MongoDB &#x200B;](https://docs.mongodb.org/)
