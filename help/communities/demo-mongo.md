---
title: MongoDB instellen voor demo
description: Hoe te opstelling MSRP voor één auteursinstantie en één publiceer instantie
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 7e257b34-a0f5-47db-b1a9-e26333c287d9
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# MongoDB instellen voor demo {#how-to-setup-mongodb-for-demo}

## Inleiding {#introduction}

Dit leerprogramma beschrijft hoe te opstelling [ MSRP ](msrp.md) voor *één auteur* instantie en *één publiceren* instantie.

Met deze opstelling, is de communautaire inhoud toegankelijk van zowel auteur als publicatiemilieu&#39;s zonder het moeten voorwaarts of omgekeerd repliceren user-generated inhoud (UGC).

Deze configuratie is geschikt voor *niet-productie* milieu&#39;s zoals voor ontwikkeling en/of demonstratie.

**a *productie* milieu zou moeten:**

* MongoDB uitvoeren met een replicaset
* SolrCloud gebruiken
* Meerdere uitgeversinstanties bevatten

## MongoDB {#mongodb}

### MongoDB installeren {#install-mongodb}

* Download MongoDB van [ https://www.mongodb.com/](https://www.mongodb.com/)

   * Keuze van besturingssysteem:

      * Linux®
      * Mac 10.8
      * Windows 7

   * Keuze van versie:

      * Gebruik minimaal versie 2.6

* Basisconfiguratie

   * Volg de installatie-instructies van MongoDB.
   * Configureer voor monniken:

      * Het is niet nodig mongo&#39;s te configureren of te verschepen.

   * De geïnstalleerde map van MongoDB heet &lt;mongo-install>.
   * Het gedefinieerde pad naar de gegevensmap wordt &lt;mongo-dbpath> genoemd.

* MongoDB kan op dezelfde host worden uitgevoerd als AEM of extern worden uitgevoerd.

### MongoDB starten {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath &lt;mongo-dbpath>

Dit begint een server MongoDB gebruikend standaardhaven 27017.

* Gebruik voor Mac een hogere limiet met de beginmarkering &#39;ulimit -n 2048&#39;

>[!NOTE]
>
>Als MongoDB *na* AEM is begonnen, **nieuw begin** alle **AEM** instanties zodat verbinden zij behoorlijk met MongoDB.

### Optie voor demoproductie: Set MongoDB Replica instellen {#demo-production-option-setup-mongodb-replica-set}

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

* Solr van de download van [ Apache Lucene ](https://archive.apache.org/dist/lucene/solr/):

   * Geschikt voor elk besturingssysteem.
   * Solr versie 7.0.
   * Solr vereist Java™ 1.7 of hoger.

* Basisconfiguratie

   * Volg &#39;voorbeeld&#39; Solr instellen.
   * Er is geen service nodig.
   * De geïnstalleerde map Solr heet &lt;solr-install>.

### Solr voor AEM Communities configureren {#configure-solr-for-aem-communities}

Om een inzameling Solr voor MSRP voor demo te vormen, zijn er twee te nemen besluiten (selecteer de verbindingen aan belangrijkste documentatie voor details):

1. Solr van de looppas in standalone of [ wijze SolrCloud ](msrp.md#solrcloudmode).
1. Installeer [ standaard ](msrp.md#installingstandardmls) of [ geavanceerd ](msrp.md#installingadvancedmls) meertalig onderzoek (MLS).

### Zelfstandige zonne-energie {#standalone-solr}

De methode voor het uitvoeren van Solr kan verschillen, afhankelijk van de versie en wijze van installatie. De [ Solr verwijzingsgids ](https://archive.apache.org/dist/lucene/solr/ref-guide/) is de gebiedende documentatie.

Voor het gemak, gebruikend versie 4.10 als voorbeeld, begin Solr op standalone wijze:

* cd naar &lt;solrinstall>/example
* Java™ -jar start.jar

Dit proces begint een Solr server van HTTP gebruikend standaardhaven 8983. U kunt naar de Solr Console bladeren om een Solr console voor het testen te krijgen.

* standaard de console van Solr: [ http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Als Solr Console niet beschikbaar is, controleer de logboeken onder &lt;solrinstall>/example/logs. Kijk of SOLR probeert te binden aan een specifieke hostname die niet kan worden opgelost (bijvoorbeeld &quot;user-macbook-pro&quot;).
>
Als dat het geval is, werkt u het `etc/hosts` -bestand bij met een nieuw item voor deze hostnaam (bijvoorbeeld 127.0.0.1 user-macbook-pro) en geeft u het bestand de juiste naam.

### SolrCloud {#solrcloud}

Start solr met:

* `java -Dbootstrap_confdir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar`

## MongoDB identificeren als een gemeenschappelijke winkel {#identify-mongodb-as-common-store}

Start de auteur en publiceer AEM indien nodig.

Als AEM actief was voordat MongoDB werd gestart, moeten de AEM instanties opnieuw worden gestart.

Volg de instructies op de belangrijkste documentatiepagina: [ MSRP - MongoDB Gemeenschappelijke Opslag ](msrp.md)

## Testen {#test}

Als u de algemene opslag van MongoDB wilt testen en verifiëren, plaatst u een opmerking op de publicatieinstantie en bekijkt u deze op de auteurinstantie. U ziet de UGC in MongoDB en Solr:

1. Voor publiceer instantie, doorblader aan de [ Communautaire pagina van de Gids van Componenten ](http://localhost:4503/content/community-components/en/comments.html) en selecteer de component van Commentaren.
1. Meld u aan om een opmerking te plaatsen:
1. Typ tekst in het tekstinvoervak voor opmerkingen en klik op **[!UICONTROL Post]**

   ![ post-commentaar ](assets/post-comment.png)

1. Eenvoudig bekijk de commentaar op de [ auteursinstantie ](http://localhost:4502/content/community-components/en/comments.html) (waarschijnlijk nog ondertekend binnen als admin/admin).

   ![ mening-commentaar ](assets/view-comment.png)

   Nota: Terwijl er knopen JCR onder *azipath* op auteur zijn, zijn deze knopen voor het kader SCF. De werkelijke UGC bevindt zich niet in de JCR, maar in de MongoDB.

1. De UGC in mongodb weergeven **[!UICONTROL Communities]** > **[!UICONTROL Collections]** > **[!UICONTROL Content]**

   ![ ugc-content ](assets/ugc-content.png)

1. De UGC in Solr weergeven:

   * Blader naar het dashboard Solr: [ http://localhost:8983/solr/ ](http://localhost:8983/solr/).
   * Gebruiker `core selector` selecteert `collection1` .
   * Selecteer `Query` .
   * Selecteer `Execute Query` .

   ![ ugc-solr ](assets/ugc-solr.png)

## Problemen oplossen {#troubleshooting}

### Geen UGC weergegeven {#no-ugc-appears}

1. Controleer of MongoDB op de juiste wijze is geïnstalleerd en uitgevoerd.

1. Zorg ervoor dat MSRP is gevormd om de standaardleverancier te zijn:

   * Voor alle auteur en publiceer AEM instanties, herzie de [ console van de Configuratie van de Opslag ](srp-config.md), of controleer de AEM bewaarplaats:

   * In JCR, als [/etc/socialconfig ](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/) geen [ srpc ](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) knoop bevat, betekent het dat de opslagleverancier JSRP is.
   * Als de srpc knoop bestaat en knoop [ standaardconfiguratie ](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) bevat, zouden de eigenschappen van de standaardconfiguratie MSRP moeten bepalen om de standaardleverancier te zijn.

1. Zorg ervoor dat AEM opnieuw begonnen was nadat MSRP selecteerde.
