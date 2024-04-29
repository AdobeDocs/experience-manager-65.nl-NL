---
title: Offlineindexering gebruiken om de downtime tijdens een upgrade te verminderen
description: Leer hoe u de methode voor het offline opnieuw indexeren kunt gebruiken om de downtime van het systeem te verminderen wanneer u een AEM upgrade uitvoert.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
feature: Upgrading
exl-id: 85bc041e-0ab1-42de-8bcc-c98a175d7494
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 0%

---

# Offlineindexering gebruiken om de downtime tijdens een upgrade te verminderen {#offline-reindexing-to-reduce-downtime-during-upgrades}

## Inleiding {#introduction}

Een van de belangrijkste uitdagingen bij het upgraden van Adobe Experience Manager is de downtime die aan de auteursomgeving is gekoppeld wanneer een upgrade op locatie wordt uitgevoerd. Inhoudsauteurs hebben tijdens een upgrade geen toegang tot de omgeving. Daarom is het wenselijk om de hoeveelheid tijd te minimaliseren het neemt om de verbetering uit te voeren. Voor grote opslagplaatsen, met name AEM Assets-projecten, die doorgaans grote gegevensopslagruimten en een hoog niveau van uploads per uur hebben, neemt het opnieuw indexeren van eiken een significant percentage van de upgradetijd in beslag.

In deze sectie wordt beschreven hoe u het Oak-runtime-programma kunt gebruiken om de opslagplaats opnieuw te indexeren **voor** het uitvoeren van de verbetering, waarbij de hoeveelheid onderbreking tijdens de daadwerkelijke verbetering wordt verminderd. De voorgestelde stappen kunnen worden toegepast op [Lucene](https://jackrabbit.apache.org/oak/docs/query/lucene.html) indexen voor versies AEM 6.4 en hoger.

## Overzicht {#overview}

Nieuwe versies van de AEM brengen wijzigingen aan de indexdefinities van eikel aan aangezien de eigenschapreeks wordt uitgebreid. Wijzigingen in de indexen van het eik dwingen opnieuw indexeren wanneer u het AEM-exemplaar bijwerkt. Het opnieuw indexeren is duur voor middelenimplementaties omdat tekst in elementen (bijvoorbeeld tekst in een PDF-bestand) wordt geëxtraheerd en geïndexeerd. Bij MongoMK-opslagruimten blijven gegevens via het netwerk behouden, waardoor er meer tijd nodig is voor opnieuw indexeren.

Het probleem waarmee de meeste klanten tijdens een upgrade worden geconfronteerd, beperkt het downtime-venster. De oplossing is: **overslaan** de herindexeringsactiviteit tijdens de upgrade. Dit kan worden bereikt door de nieuwe indeces te creëren **voorafgaand** om de verbetering uit te voeren, dan eenvoudig invoerend hen tijdens de verbetering.

## Benadering {#approach}

![offline opnieuw indexeren-upgrade-tekst-extractie](assets/offline-reindexing-upgrade-process.png)

Het idee moet de index vóór de verbetering, tegen de indexdefinities van het doel AEM versie tot stand brengen gebruikend [Eak-run](/help/sites-deploying/indexing-via-the-oak-run-jar.md) gebruiken. In het bovenstaande diagram wordt de methode voor het offline opnieuw indexeren weergegeven.

Bovendien is dit de orde van de stappen zoals die in de benadering worden beschreven:

1. Tekst van binaire tekens wordt als eerste geëxtraheerd
2. Doelindexdefinities worden gemaakt
3. Offlineindexen worden gemaakt
4. De indexen worden dan ingevoerd tijdens het verbeteringsproces

### Tekst uitnemen {#text-extraction}

Om volledige indexering in AEM toe te laten, wordt de tekst van binaire getallen zoals PDF gehaald en aan de index toegevoegd. Dit is meestal een kostbare stap in het indexeringsproces. Tekstomloop is een optimaliseringsstap die vooral wordt aanbevolen voor het opnieuw indexeren van opslagplaatsen voor elementen, omdat er een groot aantal binaire bestanden wordt opgeslagen.

![offline opnieuw indexeren-upgrade-tekst-extractie](assets/offline-reindexing-upgrade-text-extraction.png)

Tekst van binaire bestanden die in het systeem zijn opgeslagen, kan met het gereedschap eikenuitvoering worden uitgepakt met de tikabibliotheek. Een kloon van de productiesystemen kan vóór verbetering worden genomen en voor dit tekstextractieproces worden gebruikt. Dit proces leidt dan tot de tekstopslag, door de volgende stappen te gaan:

**1. De gegevensopslagruimte doorlopen en de details van binaire bestanden verzamelen**

Met deze stap maakt u een CSV-bestand met een paar binaire getallen, die een pad en een blob-id bevatten.

Voer de onderstaande opdracht uit vanuit de map waar u de index wilt maken. In het onderstaande voorbeeld wordt uitgegaan van de thuismap van de repository.

```
java java -jar oak-run.jar tika <nodestore path> --fds-path <datastore path> --data-file text-extraction/oak-binary-stats.csv --generate
```

Wanneer `nodestore path` is de `mongo_ur` of `crx-quickstart/repository/segmentstore/`

Gebruik de `--fake-ds-path=temp` parameter in plaats van `–fds-path` het proces te versnellen.

**2. De binaire tekstwinkel die beschikbaar is in de bestaande index opnieuw gebruiken**

Pak de indexgegevens uit het bestaande systeem en extraheer de tekstwinkel.

U kunt de bestaande indexgegevens dumpen met de volgende opdracht:

```
java -jar oak-run.jar index <nodestore path> --fds-path=<datastore path> --index-dump
```

Wanneer `nodestore path` is de `mongo_ur` of `crx-quickstart/repository/segmentstore/`

Gebruik vervolgens de bovenstaande indexdump om de winkel te vullen:

```
java -jar oak-run.jar tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --index-dir ./indexing-result/index-dumps/<oak-index-name>/data populate
```

Wanneer `oak-index-name` Dit is de naam van de volledige tekstindex, bijvoorbeeld &#39;lucene&#39;.

**3. Voer het tekstextractieproces uit met behulp van de tika-bibliotheek voor de binaire getallen die in de bovenstaande stap zijn overgeslagen**

```
java -cp oak-run.jar:tika-app-1.21.jar org.apache.jackrabbit.oak.run.Main tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --fds-path <datastore path> extract
```

Wanneer `datastore path` is de weg aan de binaire gegevensopslag.

De gemaakte tekstopslag kan in de toekomst worden bijgewerkt en opnieuw worden gebruikt voor herindexeringsscenario&#39;s.

Raadpleeg voor meer informatie over het extractieproces van tekst de [Oak-run-documentatie](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html).

### Offline opnieuw indexeren {#offline-reindexing}

![offline opnieuw indexeren-upgrade-offline opnieuw indexeren](assets/offline-reindexing-upgrade-offline-reindexing.png)

Creeer offline de index van Lucene vóór de verbetering. Als het gebruiken van MongoMK, wordt het geadviseerd om het op één van de knopen te leiden MongoMk, aangezien dit netwerkoverheadkosten vermijdt.

Voer de volgende stappen uit om de index offline te maken:

**1. Eak-Lucene-indexdefinities genereren voor de AEM versie**

Zet de bestaande indexdefinities neer. Indexdefinities die zijn gewijzigd, zijn gegenereerd met behulp van de bundel van de graniet-opslagruimte van de doelversie AEM en de eak-run.

Om de indexdefinitie van te dumpen **bron** AEM instantie, voer deze opdracht uit:

>[!NOTE]
>
>Raadpleeg voor meer informatie over definities van dumping-indexen de [Oak-documentatie](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#async-index-data).

```
java -jar oak-run.jar index --fds-path <datastore path> <nodestore path> --index-definitions
```

Wanneer `datastore path` en `nodestore path` afkomstig zijn van **bron** AEM instantie.

Vervolgens genereert u indexdefinities op basis van de **target** AEM versie die de graniet-opslagbundel van de doelversie gebruikt.

```
java -cp oak-run.jar:bundle-com.adobe.granite.repository.jar org.apache.jackrabbit.oak.index.IndexDefinitionUpdater --in indexing-definitions_source.json --out merge-index-definitions_target.json --initializer com.adobe.granite.repository.impl.GraniteContent
```

>[!NOTE]
>
>Het maken van de bovenstaande indexdefinitie wordt alleen ondersteund door het `oak-run-1.12.0` versie en hoger. Het richten wordt gedaan gebruikend de bundel van de granietbewaarplaats `com.adobe.granite.repository-x.x.xx.jar`.

Met de bovenstaande stappen maakt u een JSON-bestand met de naam `merge-index-definitions_target.json` Dit is de indexdefinitie.

**2. Een controlepunt maken in de opslagplaats**

Een controlepunt maken in de productie **bron** AEM instantie met een lange levensduur. Dit moet gebeuren voordat de opslagplaats wordt gekloond.

Via JMX-console op `http://serveraddress:serverport/system/console/jmx`, ga naar `CheckpointMBean` en maak een controlepunt met een lang genoeg leven (bijvoorbeeld, 200 dagen). Hiervoor roept u `CheckpointMBean#createCheckpoint` with `17280000000` als het argument voor de levensduurduur in milliseconden.

Kopieer de zojuist gemaakte checkpoint-id en valideer de levensduur met JMX `CheckpointMBean#listCheckpoints`.

>[!NOTE]
>
>Dit controlepunt wordt verwijderd wanneer de index later wordt geïmporteerd.

Raadpleeg voor meer informatie [aanmaken controlepunt](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#out-of-band-create-checkpoint) in de documentatie van de eik.

**Offline indexeren uitvoeren voor de gegenereerde indexdefinities**

Lucene-herindexering kan offline worden uitgevoerd met behulp van een eik-run. Dit proces leidt tot indexgegevens in schijf onder `indexing-result/indexes`. Het doet het **niet** schrijven naar de opslagplaats en vereist dus niet dat de actieve AEM wordt gestopt. Het gemaakte tekstarchief wordt in dit proces gebruikt:

```
java -Doak.indexer.memLimitInMB=500 -jar oak-run.jar index <nodestore path> --reindex --doc-traversal-mode --checkpoint <checkpoint> --fds-path <datastore path> --index-definitions-file merge-index-definitions_target.json --pre-extracted-text-dir text-extraction/store

Sample <checkpoint> looks like r16c85700008-0-8
—fds-path: path to data store.
--pre-extracted-text-dir: Directory of pre-extracted text.
merge-index-definitions_target: JSON file having merged definitions for the target AEM instance. indexes in this file will be re-indexed.
```

Gebruik van de `--doc-traversal-mode` Deze parameter is handig bij MongoMK-installaties omdat de herindextijd hierdoor aanzienlijk wordt verbeterd doordat opslagruimteinhoud in een lokaal, plat bestand wordt gespoold. Er is echter meer schijfruimte nodig van tweemaal de grootte van de opslagplaats.

Als er MongoMK is, kan dit proces worden versneld als deze stap in een instantie dichter bij de instantie MongoDB wordt uitgevoerd. Als de looppas op de zelfde machine, netwerkoverheadkosten kan worden vermeden.

Aanvullende technische details zijn te vinden in het [documentatie voor indexering door eikenuitvoering](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html).

### Indexen importeren {#importing-indexes}

Met AEM 6.4 en nieuwere versies, heeft AEM de ingebouwde capaciteit om indexen van schijf op startopeenvolging in te voeren. De map `<repository>/indexing-result/indexes` wordt gecontroleerd op de aanwezigheid van indexgegevens tijdens het opstarten. U kunt de vooraf gemaakte index tijdens de [upgradeproces](in-place-upgrade.md#performing-the-upgrade) voordat u begint met de nieuwe versie van de **target** AEM. AEM importeert het in de opslagplaats en verwijdert het overeenkomstige controlepunt uit het systeem. Een herindex wordt dus volledig vermeden.

## Aanvullende tips en probleemoplossing {#troubleshooting}

Hieronder vindt u enkele nuttige tips en aanwijzingen voor het oplossen van problemen.

### Het effect op het systeem van de live productie verminderen {#reduce-the-impact-on-the-live-production-system}

U wordt aangeraden het productiesysteem te klonen en de offline index te maken met de kloon. Hierdoor worden mogelijke gevolgen voor het productiesysteem weggenomen. Het voor het importeren van indexen vereiste controlepunt moet echter aanwezig zijn in het productiesysteem. Daarom is het van essentieel belang dat u een controlepunt maakt voordat u de kloon gebruikt.

### Een runbook en proefversie voorbereiden {#prepare-a-runbook-and-trial-run}

Aanbevolen wordt een [runbook](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade-planning.html#building-the-upgrade-and-rollback-runbook) en voer een paar proeven uit alvorens de verbetering in productie in werking te stellen.

### Doc Traversal Mode with Offline Indexing {#doc-traversal-mode-with-offline-indexing}

Offlineindexering vereist meerdere traversals van de gehele repository. Met installaties MongoMK, wordt de bewaarplaats betreden over het netwerk die de prestaties van het indexeren proces beïnvloeden. Één optie moet het off-line indexeren proces op de replica in werking stellen MongoDB zelf die de netwerkoverheadkosten zal elimineren. Een andere optie is het gebruik van de modus doc traversal.

De de traversal wijze van Doc kan worden toegepast door de parameter van de bevellijn toe te voegen `—doc-traversal` aan het bevel-looppas voor off-line indexeren. In deze modus wordt een kopie van de gehele opslagplaats op de lokale schijf als een plat bestand gespaard en wordt het gebruikt om de indexering uit te voeren.
