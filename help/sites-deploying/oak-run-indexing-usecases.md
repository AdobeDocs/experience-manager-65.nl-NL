---
title: Oak-run.jar Indexing Use cases
description: Leer meer over de verschillende gebruikersgevallen voor het indexeren met het Oak-programma.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
noindex: true
exl-id: d25e3070-080a-4594-8fdb-9f09164135fc
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1380'
ht-degree: 0%

---

# Oak-run.jar Indexing Use cases{#oak-run-jar-indexing-use-cases}

Oak-in werking gestelde steunen het indexeren van gebruiksgevallen op de bevellijn zonder het moeten de uitvoering van deze gebruiksgevallen door middel van AEM JMX console organiseren.

De overkoepelende voordelen van het gebruik van de bevelbenadering van het eak-looppas.jar indexbevel voor het beheren van indexen van Oak zijn:

1. Oak-run index command verstrekt een nieuwe het indexeren toolset voor AEM 6.4.
1. Oak-run verkort tijd-aan-herdex die herindextijden op grotere bewaarplaatsen vermindert.
1. Oak-run vermindert het verbruik van bronnen tijdens het opnieuw indexeren in AEM, wat resulteert in over het algemeen betere systeemprestaties.
1. Oak-run biedt out-of-band herindexering, ondersteunende situaties waarin productie beschikbaar moet zijn, en kan geen onderhoud of downtime tolereren die anders vereist zijn om opnieuw te indexeren.

Secties hieronder bieden voorbeeldopdrachten. Oak-run index command ondersteunt alle NodeStore- en BlobStore-instellingen. De voorbeelden hieronder zijn rond montages die FileDataStore en SegmentNodeStore hebben.

## Hoofdlettergebruik 1 - Consistentiecontrole index {#usercase1indexconsistencycheck}

Dit is een gebruiksgeval met betrekking tot indexcorruptie. Soms was het niet mogelijk om te bepalen welke indexen corrupt zijn. Daarom heeft de Adobe instrumenten verstrekt die:

1. voert indexconsistentiecontroles op alle indexen uit en verstrekt een rapport waarop indexen geldig zijn en die ongeldig zijn;
1. De werktuigen zijn ook bruikbaar als AEM niet toegankelijk is;
1. Het is gebruiksvriendelijk.

U kunt controleren op beschadigde indexen door de bewerking `--index-consistency-check` uit te voeren:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Hiermee wordt een rapport gegenereerd in `indexing-result/index-consistency-check-report.txt` . Zie hieronder voor een voorbeeldrapport:

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

Voor het diagnostiseren van sommige gevallen rond de Adobe van vraagprestaties vereiste vaak bestaande indexdefinitie, op index betrekking hebbende statistieken van de klantenopstelling. Tot dusverre werd deze informatie verspreid over meerdere bronnen. Om het oplossen van problemen gemakkelijker te maken, heeft de Adobe tooling gecreeerd die zal:

1. Alle indexdefinitie in het systeem in één JSON-bestand dumpen.

1. Belangrijke statistieken uit bestaande indexen dumpen;

1. de inhoud van de pompindex voor offline analyse;

1. Is bruikbaar zelfs als AEM niet toegankelijk is

De bovenstaande bewerkingen kunnen nu worden uitgevoerd met de volgende opdrachten voor de bewerkingsindex:

* `--index-info` - Verzamelt en dumpt verschillende statistieken met betrekking tot de indexen

* `--index-definitions` - Verzamelt en dumpt indexdefinities

* `--index-dump` - Indexinhoud wordt gedumpt

Zie hieronder een voorbeeld van hoe de bevelen in de praktijk werken:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

De rapporten worden gegenereerd in `indexing-result/index-info.txt` en `indexing-result/index-definitions.json`

Bovendien worden de zelfde details verstrekt door middel van de Console van het Web en zouden deel van de configuratiedumpit zip uitmaken. Ze kunnen op de volgende locatie worden benaderd:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Voordelen {#uc2benefits}

Dit hulpmiddel laat het verzamelen van alle vereiste details met betrekking tot het indexeren of vraagkwesties toe snel en vermindert de tijd besteed in het halen van deze informatie.

## Hoofdlettergebruik 3 - opnieuw indexeren {#usecase3reindexing}

Afhankelijk van de [ scenario&#39;s ](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing), soms, moet het opnieuw indexeren worden uitgevoerd. Op dit moment wordt opnieuw indexeren uitgevoerd door de markering `reindex` in te stellen op `true` in het indexdefinitieknooppunt via CRXDE of via de gebruikersinterface van Indexbeheer. Nadat de markering is ingesteld, wordt het opnieuw indexeren asynchroon uitgevoerd.

Enkele punten die u wilt opmerken bij het opnieuw indexeren:

* Het opnieuw indexeren gaat veel langzamer bij `DocumentNodeStore` -instellingen dan bij `SegmentNodeStore` -instellingen waarbij alle inhoud lokaal is.

* Met het huidige ontwerp, terwijl het opnieuw indexeren gebeurt, wordt async indexer geblokkeerd en alle andere async indexen worden verouderd en niet bijgewerkt tijdens het indexeren. Daarom kunnen gebruikers, als het systeem in gebruik is, geen bijgewerkte resultaten zien;
* Bij de herindexering wordt de gehele gegevensopslagruimte doorkruist, wat een grote belasting kan betekenen voor de installatie van de AEM en zo van invloed kan zijn op de gebruikerservaring.
* Voor een `DocumentNodeStore` -installatie waarbij het opnieuw indexeren aanzienlijk kan duren als de verbinding met de Mongo-database halverwege de bewerking mislukt, moet de indexering opnieuw van voren af aan worden gestart.

* Soms kan het opnieuw indexeren veel tijd in beslag nemen door het extraheren van tekst. Dit is specifiek voor instellingen met veel PDF-bestanden, waarbij de tijd die aan tekstextractie wordt besteed invloed kan hebben op de indexatietijd.

Om deze doelstellingen te bereiken, steunt het werktuig-looppas van de indexindex verschillende wijzen voor het opnieuw indexeren die kunnen worden gebruikt zoals vereist. De opdracht voor indexeren met eikenuitvoering biedt de volgende voordelen:

* **out-of-band het opnieuw indexeren** - het eik-looppas het opnieuw indexeren kan afzonderlijk van een lopende AEM opstelling worden gedaan en zo, minimaliseert het het effect op de AEM instantie die in gebruik is;

* **out-of-lane het opnieuw indexeren** - het opnieuw indexeren vindt plaats zonder het beïnvloeden van indexerende verrichtingen. Dit betekent dat de asynchrone indexeerder andere indexen kan blijven indexeren;

* **Vereenvoudigde herdex voor installaties DocumentNodeStore** - voor `DocumentNodeStore` installaties, kan het opnieuw indexeren met één enkel bevel worden gedaan dat ervoor zorgt dat het opnieuw indexeren op de meest optimale manier wordt gedaan;

* **Steunt het bijwerken van indexdefinities en het introduceren van nieuwe indexdefinities**

### Opnieuw indexeren - DocumentNodeStore {#reindexdocumentnodestore}

Voor `DocumentNodeStore` -installaties kan opnieuw indexeren worden uitgevoerd met één enkele opdracht voor het uitvoeren van een eiken:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Dit biedt de volgende voordelen:

* Minimale invloed op het uitvoeren van AEM instanties. De meeste leest kan van secundaire servers worden gedaan en het lopen AEM de geheime voorgeheugens worden niet nadelig beïnvloed wegens al die traversal die voor het opnieuw indexeren wordt vereist;
* Gebruikers kunnen ook een JSON van een nieuwe of bijgewerkte index opgeven via de optie `--index-definitions-file` .

### Opnieuw indexeren - SegmentNodeStore {#reindexsegmentnodestore}

Voor `SegmentNodeStore` -installaties kan opnieuw indexeren op een van de volgende manieren worden uitgevoerd:

#### Online opnieuw indexeren - SegmentNodeStore {#onlinereindexsegmentnodestore}

Voer de markering `reindex` in op de gebruikelijke manier waarop opnieuw indexeren wordt uitgevoerd.

#### Online opnieuw indexeren - SegmentNodeStore - De AEM-instantie wordt uitgevoerd {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

Voor `SegmentNodeStore` -installaties heeft slechts één proces toegang tot segmentbestanden in de modus lezen-schrijven. Daarom moeten er voor sommige bewerkingen in de indexering van eikels handmatige extra stappen worden gezet.

Dit zou het volgende inhouden:

1. Staptekst
1. Verbind `oak-run` met de zelfde bewaarplaats die door AEM op read-only wijze wordt gebruikt en voer het indexeren uit. Een voorbeeld van hoe u dit kunt bereiken:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Ten slotte importeert u de gemaakte indexbestanden via de `IndexerMBean#importIndex` -bewerking vanaf het pad waar de indexeringsbestanden zijn opgeslagen nadat de bovenstaande opdracht is uitgevoerd.

In dit scenario, moet u niet de server van de AEM tegenhouden of om het even welke nieuwe instantie verstrekken. Als indexering echter gepaard gaat met een verplaatsing van de hele opslagplaats, zou de I/O-belasting van de installatie toenemen, wat negatieve gevolgen zou hebben voor de prestaties bij uitvoering.

#### Online opnieuw indexeren - SegmentNodeStore - de AEM instantie is gesloten {#onlinereindexsegmentnodestoreaeminstanceisdown}

Voor `SegmentNodeStore` -installaties kan opnieuw indexeren worden uitgevoerd met één enkele opdracht voor het uitvoeren van een eiken. De AEM instantie moet echter worden afgesloten.

U kunt het opnieuw indexeren met het volgende bevel teweegbrengen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

Het verschil tussen deze aanpak en de hierboven beschreven aanpak is dat het maken van controlepunten en het importeren van indexen automatisch worden uitgevoerd. Het nadeel is dat AEM tijdens het proces omlaag moet zijn.

#### Opnieuw indexeren buiten bandbreedte - SegmentNodeStore {#outofbandreindexsegmentnodestore}

In dit geval kunt u opnieuw indexeren op een gekloonde instelling om de invloed op de actieve AEM te minimaliseren:

1. Een controlepunt maken door middel van een JMX-bewerking. U kunt dit doen door naar de [ Console JMX ](/help/sites-administering/jmx-console.md) te gaan en naar `CheckpointManager` te zoeken. Dan, klik **createCheckpoint (lange p1)** verrichting die een hoge waarde voor afloop in seconden gebruikt (bijvoorbeeld, **2592000**).
1. Kopieer de map `crx-quickstart` naar een nieuwe computer
1. Herindexeren uitvoeren met de opdracht Indexeren op einde

1. De gegenereerde indexbestanden kopiëren naar AEM server

1. Importeer de indexbestanden via JMX.

In dit geval wordt aangenomen dat de Data Store toegankelijk is voor een andere instantie die mogelijk niet mogelijk is als `FileDataStore` wordt geplaatst op een opslagoplossing in de cloud, zoals EBS. Dit sluit het scenario uit waarin `FileDataStore` ook wordt gekloond. Als in de indexdefinitie geen fullText-indexering wordt uitgevoerd, is toegang tot `DataStore` niet vereist.

## Hoofdlettergebruik 4 - Indexdefinities bijwerken {#usecase4updatingindexdefinitions}

Momenteel, kunt u de veranderingen van de indexdefinitie als [ ACS verschepen verzekeren het pakket van de Index ](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html). Hierdoor kunnen de indexdefinities worden verzonden door middel van een inhoudspakket, waarvoor later opnieuw indexeren moet worden uitgevoerd door de markering `reindex` in te stellen op `true` .

Dit werkt goed voor kleinere installaties waar het opnieuw indexeren niet lang duurt. Voor grote gegevensbanken gebeurt herindexering echter veel langer. In dergelijke gevallen kunnen we nu de werkset voor indexen die op een eikel worden uitgevoerd, gebruiken.

Oak-run biedt nu ondersteuning voor het opgeven van indexdefinities in JSON-indeling en het maken van index in out-of-band modus, waarbij geen wijzigingen worden uitgevoerd op een live instantie.

Voor dit gebruiksgeval moet u rekening houden met het volgende:

1. Een ontwikkelaar werkt de indexdefinities bij voor een lokale instantie en genereert vervolgens een JSON-indexdefinitiebestand met de optie `--index-definitions`

1. De bijgewerkte JSON wordt vervolgens aan de systeembeheerder gegeven
1. Systeembeheerder volgt de out-of-band-benadering en bereidt de index voor op een andere installatie
1. Nadat dit wordt voltooid, worden de geproduceerde indexdossiers ingevoerd op een lopende AEM installatie.
