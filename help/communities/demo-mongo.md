---
title: MongoDB voor demo instellen
seo-title: MongoDB voor demo instellen
description: Hoe te opstelling MSRP voor één auteursinstantie en één publiceer instantie
seo-description: Hoe te opstelling MSRP voor één auteursinstantie en één publiceer instantie
uuid: d2035a9e-f05c-4f90-949d-7cdae9646750
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0b126218-b142-4d33-a28c-a91ab4fe99ac
translation-type: tm+mt
source-git-commit: 94bc3550a7e18b9203e7a0d495d195d7b798e012
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---


# MongoDB voor demo instellen {#how-to-setup-mongodb-for-demo}

## Inleiding {#introduction}

Dit leerprogramma beschrijft hoe te opstelling [MSRP](msrp.md) voor *één auteursinstantie* en *één te publiceren* instantie.

Met deze opstelling, is de communautaire inhoud toegankelijk van zowel auteur als publicatiemilieu&#39;s zonder het moeten voorwaarts of omgekeerd door:sturen gebruiker geproduceerde inhoud (UGC).

Deze configuratie is geschikt voor *niet-productieomgevingen* , zoals voor ontwikkeling en/of demonstratie.

**Een *productieomgeving*moet:**

* MongoDB uitvoeren met een replicaset
* SolrCloud gebruiken
* Meerdere uitgeversinstanties bevatten

## MongoDB {#mongodb}

### MongoDB installeren {#install-mongodb}

* Download MongoDB van [https://www.mongodb.org/](https://www.mongodb.org/)

   * Keuze van besturingssysteem:

      * Linux
      * Mac 10.8
      * Windows 7
   * Keuze van versie:

      * Gebruik minimaal versie 2.6


* Basisconfiguratie

   * Volg de installatie-instructies van MongoDB.
   * Configureer voor monniken:

      * Het is niet nodig mongo&#39;s te configureren of te verschepen.
   * De geïnstalleerde map MongoDB wordt &lt;mongo-install> genoemd.
   * Het gedefinieerde pad naar de gegevensdirectory wordt &lt;mongo-dbpath> genoemd.


* MongoDB kan op dezelfde host worden uitgevoerd als AEM of extern worden uitgevoerd.

### MongoDB starten {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath &lt;mongo-dbpath>

Hiermee wordt een MongoDB-server gestart met de standaardpoort 27017.

* Voor Mac: verhoog de limiet met beginmarkering &#39;ulimit -n 2048&#39;

>[!NOTE]
>
>Als MongoDB wordt gestart *na* AEM, **start** u alle **AEM** instanties opnieuw zodat ze op de juiste wijze verbinding maken met MongoDB.


### Optie voor demoproductie: MongoDB-replicaset instellen {#demo-production-option-setup-mongodb-replica-set}

De volgende opdrachten zijn een voorbeeld van het instellen van een replicaset met 3 knooppunten op localhost:

* `bin/mongod --port 27017 --dbpath data --replSet rs0&`
* `bin/mongo`

   * `cfg = {"_id": "rs0","version": 1,"members": [{"_id": 0,"host": "127.0.0.1:27017"}]}`
   * `rs.initiate(cfg)`

* `bin/mongod --port 27018 --dbpath data1 --replSet rs0&`
* `bin/mongod --port 27019 --dbpath data2 --replSet rs0&`
* `bin/mongo`

   * `rs.add("127.0.0.1:27018")`
   * `rs.add("127.0.0.1:27019")`
   * `rs.status()`

## Solr {#solr}

### Solo installeren {#install-solr}

* Download Solr van [Apache Lucene](https://archive.apache.org/dist/lucene/solr/):

   * Geschikt voor elk besturingssysteem.
   * Solr versie 7.0.
   * Solr vereist Java 1.7 of hoger.

* Basisconfiguratie

   * Volg &#39;voorbeeld&#39; Solr instellen.
   * Er is geen service nodig.
   * De geïnstalleerde map Solr wordt &lt;solr-install> genoemd.

### Solr voor AEM Communities configureren {#configure-solr-for-aem-communities}

Om een inzameling Solr voor MSRP voor demo te vormen, zijn er twee te nemen besluiten (selecteer de verbindingen aan belangrijkste documentatie voor details):

1. Solr uitvoeren in zelfstandige of [SolrCloud-modus](msrp.md#solrcloudmode).
1. Installeer [standaard](msrp.md#installingstandardmls) of [geavanceerd](msrp.md#installingadvancedmls) meertalig onderzoek (MLS).

### Zelfstandige Solr {#standalone-solr}

De methode voor het uitvoeren van Solr kan verschillen, afhankelijk van de versie en wijze van installatie. De [Solr verwijzingsgids](https://archive.apache.org/dist/lucene/solr/ref-guide/) is de gebiedende documentatie.

Voor het gemak, gebruikend versie 4.10 als voorbeeld, begin Solr op standalone wijze:

* cd naar &lt;solrinstall>/example
* java -jar start.jar

Hierdoor wordt een Solr HTTP-server gestart met de standaardpoort 8983. U kunt naar de Solr Console bladeren om een Solr console voor het testen te krijgen.

* standaard solr-console: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Als Solr Console niet beschikbaar is, controleer de logboeken onder &lt;solrinstall>/example/logs. Kijk of SOLR probeert te binden aan een specifieke hostname die niet kan worden opgelost (bijvoorbeeld &quot;user-macbook-pro&quot;).
Als dat het geval is, werkt u het etc/hosts-bestand bij met een nieuwe vermelding voor deze hostnaam (bijvoorbeeld 127.0.0.1 user-macbook-pro) en start Solr op de juiste wijze.


### SolrCloud {#solrcloud}

U kunt een eenvoudige solrCloud-instelling (geen productie) uitvoeren door solr te starten met:

* `java -Dbootstrap_confdir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar`

## MongoDB identificeren als een gemeenschappelijke winkel {#identify-mongodb-as-common-store}

Start de auteur en publiceer AEM indien nodig.

Als AEM actief was voordat MongoDB werd gestart, moeten de AEM instanties opnieuw worden gestart.

Volg de instructies op de hoofddocumentatiepagina: [MSRP - MongoDB Common Store](msrp.md)

## Testen {#test}

Als u de algemene opslag van MongoDB wilt testen en verifiëren, plaatst u een opmerking op de publicatieinstantie en bekijkt u deze op de auteurinstantie, en bekijkt u de UGC in MongoDB en Solr:

1. Blader in het publicatieexemplaar naar de pagina [Community Components Guide](http://localhost:4503/content/community-components/en/comments.html) en selecteer de component Comments.
1. Meld u aan om een opmerking te plaatsen:
1. Typ tekst in het tekstinvoervak voor opmerkingen en klik op **[!UICONTROL Post]**

   ![chlimage_1-191](assets/chlimage_1-191.png)

1. U kunt de opmerking gewoon weergeven op de [auteurinstantie](http://localhost:4502/content/community-components/en/comments.html) (waarschijnlijk nog steeds aangemeld als admin/admin).

   ![chlimage_1-192](assets/chlimage_1-192.png)

   Opmerking: terwijl er knopen JCR onder *asipath* op auteur zijn, zijn deze voor het kader SCF. De werkelijke UGC bevindt zich niet in de JCR, maar in de MongoDB.

1. UGC weergeven in mongodb **[!UICONTROL Communities]** > **[!UICONTROL Collections]** > **[!UICONTROL Content]**

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. De UGC in Solr weergeven:

   * Bladeren naar Solr-dashboard: [http://localhost:8983/solr/](http://localhost:8983/solr/)
   * Gebruiker `core selector` om te selecteren `collection1`
   * Selecteer `Query`
   * Selecteer `Execute Query`

   ![chlimage_1-194](assets/chlimage_1-194.png)

## Problemen oplossen {#troubleshooting}

### Geen UGC weergegeven {#no-ugc-appears}

1. Controleer of MongoDB op de juiste wijze is geïnstalleerd en uitgevoerd.

1. Zorg ervoor MSRP is gevormd om de standaardleverancier te zijn:

   * Voor alle auteur en publiceer AEM instanties, herzie de console van de Configuratie van de [Opslag](srp-config.md)

   Of controleer de AEM opslagplaats:

   * In JCR, indien [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Bevat geen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) knoop, betekent het de opslagleverancier JSRP is
   * Als de srpc knoop bestaat en knoop [standaardconfiguratie](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)bevat, zouden de eigenschappen van de standaardconfiguratie MSRP moeten bepalen om de standaardleverancier te zijn


1. Zorg ervoor dat AEM opnieuw is gestart nadat MSRP is geselecteerd.
