---
title: Gebruiksscenario's voor indexeren van eikenrun.jar
seo-title: Gebruiksscenario's voor indexeren van eikenrun.jar
description: Leer over de verschillende gebruikersgevallen voor het uitvoeren van indexering met het hulpmiddel van de Oak-looppas.
seo-description: Leer over de verschillende gebruikersgevallen voor het uitvoeren van indexering met het hulpmiddel van de Oak-looppas.
uuid: 3c50080d-1e0d-4886-8d37-269f06881eb4
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 084075b8-826d-4f27-9342-35f33368f24f
noindex: true
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---


# Gebruiksscenario&#39;s voor eik-run.jar Indexing{#oak-run-jar-indexing-use-cases}

De eiken-looppas steunt het indexeren gebruiksgevallen op de bevellijn zonder het moeten de uitvoering van deze gebruiksgevallen via AEM console JMX organiseren.

De overkoepelende voordelen van het gebruiken van de eak-looppas.jar de bevelbenadering van het indexbevel voor het beheren van indexen van het Eak zijn:

1. De opdracht Indexeren volgens einde biedt een nieuwe indexeringsgereedschapset voor AEM 6.4.
1. De eik-looppas vermindert tijd-aan-herdex die re-indextijden op grotere bewaarplaatsen vermindert.
1. Door de eik-run neemt het verbruik van bronnen af tijdens het opnieuw indexeren van AEM, wat resulteert in betere systeemprestaties.
1. Oak-run zorgt voor out-of-band re-indexering, ondersteunende situaties waarin productie beschikbaar moet zijn, en kan onderhoud of downtime die anders vereist is om opnieuw te indexeren, niet tolereren.

Secties hieronder bieden voorbeeldopdrachten. Indexopdrachten die worden uitgevoerd door een eikel, ondersteunen alle NodeStore- en BlobStore-instellingen. De voorbeelden hieronder zijn rond montages die FileDataStore en SegmentNodeStore hebben.

## Hoofdlettergebruik 1 - Indexconsistentiecontrole {#usercase1indexconsistencycheck}

Dit is een gebruiksgeval met betrekking tot indexcorruptie. In sommige gevallen kon niet worden vastgesteld welke indexen corrupt zijn. Daarom heeft Adobe instrumenten verstrekt die:

1. voert indexconsistentiecontroles op alle indexen uit en verstrekt een rapport waarop indexen geldig zijn en die ongeldig zijn;
1. De werktuigen zijn ook bruikbaar als AEM niet toegankelijk is;
1. Het is gebruiksvriendelijk.

Controleren op beschadigde indexen kan worden uitgevoerd via `--index-consistency-check`-bewerking:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Hiermee wordt een rapport gegenereerd in `indexing-result/index-consistency-check-report.txt`. Zie hieronder voor een voorbeeldrapport:

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Voordelen {#uc1benefits}

Dit hulpmiddel kan nu door Steun en de Beheerder van het Systeem worden gebruikt om snel te bepalen welke indexen corrupt zijn en dan hen opnieuw te indexeren.

## Hoofdlettergebruik 2 - Indexstatistieken {#usecase2indexstatistics}

Voor het diagnostiseren van sommige gevallen rond de Adobe van vraagprestaties vereiste vaak bestaande indexdefinitie, op index betrekking hebbende statistieken van de klantenopstelling. Tot dusverre werd deze informatie verspreid over meerdere bronnen. Om het oplossen van problemen gemakkelijker te maken, heeft Adobe tooling gecreeerd die zal:

1. Alle indexdefinities in één JSON-bestand op het systeem dumpen.

1. Belangrijke statistieken uit bestaande indexen dumpen;

1. de inhoud van de pompindex voor offline analyse;

1. Wordt ook bruikbaar als AEM niet toegankelijk is

De bovenstaande bewerkingen kunnen nu worden uitgevoerd met de volgende opdrachten in de bewerkingsindex:

* `--index-info` - Verzamelt en dumpt diverse statistieken met betrekking tot indexen

* `--index-definitions` - Verzamelt en dumpt indexdefinities

* `--index-dump` - Dumpingindex-inhoud

Zie hieronder een voorbeeld van hoe de bevelen in de praktijk werken:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

De rapporten worden gegenereerd in `indexing-result/index-info.txt` en `indexing-result/index-definitions.json`

Bovendien worden de zelfde details verstrekt via de Console van het Web en zouden deel van de configuratie stortplaats zip uitmaken. Ze kunnen op de volgende locatie worden benaderd:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Voordelen {#uc2benefits}

Dit hulpmiddel laat het verzamelen van alle vereiste details met betrekking tot het indexeren of vraagkwesties toe snel en vermindert de tijd besteed in het halen van deze informatie.

## Hoofdlettergebruik 3 - opnieuw indexeren {#usecase3reindexing}

Afhankelijk van de [scenario&#39;s](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing), in sommige gevallen moet het opnieuw indexeren worden uitgevoerd. Momenteel wordt het opnieuw indexeren gedaan door de `reindex` vlag aan `true` in de knoop van de indexdefinitie via CRXDE of via het gebruikersinterface van de Manager van de Index te plaatsen. Nadat de markering is ingesteld, wordt het opnieuw indexeren asynchroon uitgevoerd.

Enkele punten die u wilt opmerken bij het opnieuw indexeren:

* Het opnieuw indexeren is veel langzamer bij `DocumentNodeStore`-instellingen in vergelijking met `SegmentNodeStore`-instellingen waarbij alle inhoud lokaal is;

* Met het huidige ontwerp, terwijl het opnieuw indexeren gebeurt wordt de async indexeer geblokkeerd en alle andere async indexen worden verouderd en krijgen geen update voor de duur van het indexeren. Daarom kunnen gebruikers, als het systeem in gebruik is, geen bijgewerkte resultaten zien;
* Bij de herindexering wordt de gehele gegevensopslagruimte doorkruist, wat een grote belasting kan betekenen voor de installatie van de AEM en zo van invloed kan zijn op de gebruikerservaring.
* Voor een `DocumentNodeStore` installatie waar het opnieuw indexeren een aanzienlijke hoeveelheid tijd zou kunnen vergen, als de verbinding aan het gegevensbestand van Mongo in het midden van de verrichting ontbreekt, zou het indexeren van kras opnieuw moeten worden begonnen;

* In sommige gevallen kan het opnieuw indexeren veel tijd in beslag nemen door het extraheren van tekst. Dit is vooral specifiek voor instellingen met veel PDF-bestanden, waar de tijd die aan tekstextractie wordt besteed invloed kan hebben op de indexatietijd.

Om deze doelstellingen te bereiken, ondersteunt de werkset Indexering volgens het eikenstel verschillende modi voor herindexering die naar wens kunnen worden gebruikt. De opdracht voor indexeren met eikenuitvoering biedt de volgende voordelen:

* **out-of-band herindexering**  - het opnieuw omdraaien van eiken kan los van een lopende AEM worden uitgevoerd en zo de impact op de AEM in gebruik nemen tot een minimum beperken;

* **opnieuw indexeren**  buiten de rijstrook - Het opnieuw indexeren vindt plaats zonder dat dit invloed heeft op indexeringsbewerkingen. Dit betekent dat de asynchrone indexeerder andere indexen kan blijven indexeren;

* **Vereenvoudigde herindexering voor DocumentNodeStore-installaties**  - Voor  `DocumentNodeStore` installaties kan opnieuw indexeren worden uitgevoerd met één opdracht die ervoor zorgt dat herindexering op de meest optimale manier wordt uitgevoerd.

* **Ondersteunt het bijwerken van indexdefinities en het introduceren van nieuwe indexdefinities**

### Opnieuw indexeren - DocumentNodeStore {#reindexdocumentnodestore}

Voor `DocumentNodeStore` installaties kan het opnieuw indexeren via één enkele eiken-loopbevel worden gedaan:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Dit biedt de volgende voordelen

* Minimale invloed op het uitvoeren van AEM instanties. De meeste leesbewerkingen kunnen worden uitgevoerd op secundaire servers en het uitvoeren van AEM caches heeft geen negatieve invloed op alle verplaatsingen die nodig zijn voor het opnieuw indexeren van de cache.
* Gebruikers kunnen ook een JSON van een nieuwe of bijgewerkte index opgeven via de optie `--index-definitions-file`.

### Opnieuw indexeren - SegmentNodeStore {#reindexsegmentnodestore}

Voor `SegmentNodeStore` installaties kan het opnieuw indexeren op één van de volgende manieren worden gedaan:

#### Online opnieuw indexeren - SegmentNodeStore {#onlinereindexsegmentnodestore}

Volg de gevestigde manier waar het opnieuw indexeren door `reindex` vlag te plaatsen wordt gedaan.

#### Online opnieuw indexeren - SegmentNodeStore - De AEM instantie wordt uitgevoerd {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

Voor `SegmentNodeStore` installaties slechts één proces heeft toegang tot segmentdossiers op read-write wijze. Daarom moeten bij sommige bewerkingen in de indexering van eikels aanvullende handmatige stappen worden gezet.

Dit zou het volgende inhouden:

1. Staptekst
1. Verbind `oak-run` met de zelfde bewaarplaats die door AEM op read-only wijze wordt gebruikt en voer het indexeren uit. Een voorbeeld van hoe u dit kunt bereiken:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Importeer ten slotte de gemaakte indexbestanden via de bewerking `IndexerMBean#importIndex` vanaf het pad waar de indexeringsbestanden zijn opgeslagen nadat de bovenstaande opdracht is uitgevoerd.

In dit scenario hoeft u de AEM server niet te stoppen of een nieuwe instantie in te stellen. Als indexering echter gepaard gaat met een verplaatsing van de hele opslagplaats, zou de I/O-belasting van de installatie toenemen, wat negatieve gevolgen zou hebben voor de prestaties bij uitvoering.

#### Online opnieuw indexeren - SegmentNodeStore - de AEM instantie is gesloten {#onlinereindexsegmentnodestoreaeminstanceisdown}

Voor `SegmentNodeStore` installaties kan het opnieuw indexeren via één enkele eiken-loopbevel worden gedaan. De AEM instantie moet echter worden afgesloten.

U kunt het opnieuw indexeren met het volgende bevel teweegbrengen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

Het verschil tussen deze aanpak en de hierboven beschreven aanpak is dat het maken van controlepunten en het importeren van indexen automatisch worden uitgevoerd. Het nadeel is dat AEM tijdens het proces moet omlaag zijn.

#### Opnieuw indexeren buiten bandbreedte - SegmentNodeStore {#outofbandreindexsegmentnodestore}

In dit geval kunt u opnieuw indexeren op een gekloonde instelling om de invloed op de actieve AEM te minimaliseren:

1. Een controlepunt maken via een JMX-bewerking. U kunt dit doen door naar [JMX Console](/help/sites-administering/jmx-console.md) te gaan en `CheckpointManager` te zoeken. Klik vervolgens op de **createCheckpoint(long p1)**-bewerking met een hoge waarde voor de vervaldatum in seconden (bijvoorbeeld **2592000**).
1. Kopieer de map `crx-quickstart` naar een nieuwe computer
1. Herindexeren uitvoeren via de opdracht Index uitvoeren

1. De gegenereerde indexbestanden kopiëren naar AEM server

1. Importeer de indexbestanden via JMX.

In dit geval wordt aangenomen dat de Data Store toegankelijk is voor een andere instantie die mogelijk niet mogelijk is als `FileDataStore` op een cloudoplossing zoals EBS wordt geplaatst. Dit sluit het scenario uit waarin `FileDataStore` ook wordt gekloond. Als de indexdefinitie fulltext indexeren niet uitvoert, dan wordt de toegang tot `DataStore` niet vereist.

## Hoofdlettergebruik 4 - Indexdefinities bijwerken {#usecase4updatingindexdefinitions}

Momenteel, kunt u veranderingen van de indexdefinitie via [ACS verschepen verzekeren Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) pakket. Hierdoor kunnen de indexdefinities worden verzonden via een inhoudspakket, waarvoor later opnieuw indexeren moet worden uitgevoerd door de markering `reindex` in te stellen op `true`.

Dit werkt goed voor kleinere installaties waar het opnieuw indexeren niet lang duurt. Voor zeer grote gegevensbanken zal het opnieuw indexeren echter in veel grotere tijd plaatsvinden. In dergelijke gevallen kunnen we nu de werkset voor indexen die op een eikel worden uitgevoerd, gebruiken.

Oak-looppas steunt nu het verstrekken van indexdefinities in formaat JSON en de verwezenlijking van index in out-of-band wijze waar geen veranderingen op een levende instantie worden uitgevoerd.

Het proces dat u voor dit gebruiksgeval moet overwegen is:

1. Een ontwikkelaar werkt de indexdefinities op een lokale instantie bij en genereert vervolgens een JSON-indexdefinitiebestand via de optie `--index-definitions`

1. De bijgewerkte JSON wordt vervolgens aan de systeembeheerder gegeven
1. De Beheerder van het systeem volgt de out-of-band benadering en bereidt de index op een verschillende installatie voor
1. Zodra dit wordt voltooid, zullen de geproduceerde indexdossiers op een lopende AEM installatie worden ingevoerd.

