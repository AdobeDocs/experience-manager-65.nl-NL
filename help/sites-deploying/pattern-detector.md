---
title: De complexiteit van upgrades beoordelen met de patroondetector
seo-title: De complexiteit van upgrades beoordelen met de patroondetector
description: Leer hoe u de patroondetector gebruikt om de complexiteit van de upgrade te beoordelen.
seo-description: Leer hoe u de patroondetector gebruikt om de complexiteit van de upgrade te beoordelen.
uuid: 84d0add9-3123-4188-9877-758911b1899f
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: b5607343-a13b-4520-a771-f1a555bfcc7b
docset: aem65
translation-type: tm+mt
source-git-commit: 9a4ae73c08657195da2741cccdb196bd7f7142c9
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 1%

---


# De complexiteit van upgrades beoordelen met de patroondetector{#assessing-the-upgrade-complexity-with-the-pattern-detector}

## Overzicht {#overview}

Met deze functie kunt u bestaande AEM controleren op hun upgradbaarheid door patronen in gebruik te detecteren die:

1. Overtreed bepaalde regels en wordt uitgevoerd op gebieden die door de upgrade worden beïnvloed of overschreven
1. Gebruik een AEM 6.x-functie of een API die niet achterwaarts compatibel is met AEM 6.5 en die na de upgrade mogelijk kan worden onderbroken.

Dit zou kunnen dienen als een beoordeling van de ontwikkelingsinspanningen die gepaard gaan met de opwaardering tot AEM 6.5.

## Instellen {#how-to-set-up}

De patroondetector wordt afzonderlijk vrijgegeven als [één pakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/pd-all-aem65) dat werkt aan elke bron AEM versies van 6.1 tot 6.5 voor AEM 6.5-upgrade. U kunt het programma installeren met [Package Manager](/help/sites-administering/package-manager.md).

## Het gebruik {#how-to-use}

>[!NOTE]
>
>Patroondetector kan worden uitgevoerd in elke omgeving, inclusief lokale ontwikkelingsinstanties. Om:
>
>* de detectiesnelheid verhogen
>* vertraging van bedrijfskritieke instanties vermijden


>tegelijkertijd wordt aanbevolen het programma uit te voeren **op testomgevingen** die zo dicht mogelijk bij productieomgevingen liggen op het gebied van gebruikerstoepassingen , inhoud en configuraties .
>
U kunt verschillende methoden gebruiken om de uitvoer van de patroondetector te controleren:

* **Via de Felix Inventory Console:**

1. Ga naar de AEM webconsole door naar *https://serveraddress:serverport/system/console/configMgr te bladeren*
1. Selecteer **Status - Patroondetector** , zoals in de onderstaande afbeelding wordt getoond:

   ![screenshot-2018-2-5pattern-detector](assets/screenshot-2018-2-5pattern-detector.png)

* **Via een reactieve, op tekst gebaseerde of reguliere JSON-interface**

* **Via een reactieve JSON-lijninterface, **dat een afzonderlijk JSON-document in elke regel genereert.

Beide methoden worden hieronder beschreven:

## Reactieve interface {#reactive-interface}

De reactieve interface maakt het mogelijk het rapport van de schending te verwerken zodra een vermoeden wordt vastgesteld.

De uitvoer is momenteel beschikbaar onder twee URL&#39;s:

1. Onbewerkte tekstinterface
1. JSON-interface

## Afhandeling van de interface Onbewerkte tekst {#handling-the-plain-text-interface}

De informatie in de uitvoer wordt opgemaakt als een reeks gebeurtenisitems. Er zijn twee kanalen - één voor het publiceren van schendingen en de tweede voor het publiceren van de huidige vooruitgang.

U kunt ze verkrijgen met de volgende opdrachten:

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep SUSPICION
```

De uitvoer ziet er als volgt uit:

```
2018-02-13T14:18:32.071+01:00 [SUSPICION] The pattern=ECU/extraneous.content.usage was found by detector=ContentAccessDetector with id=a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f message="Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid". More info at=https://www.adobe.com/go/aem6_EC
```

De voortgang kan worden gefilterd met de `grep` opdracht:

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep PROGRESS
```

Dit resulteert in de volgende uitvoer:

```
2018-02-13T14:19:26.909+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.5), analysed=45780/16 MB items, found=0 suspicions so far in period=PT5.005S (throughput=34667 items/sec)
2018-02-13T14:19:31.904+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.5), analysed=106050/39 MB items, found=0 suspicions so far in period=PT10S (throughput=23378 items/sec)
2018-02-13T14:19:35.685+01:00 [PROGRESS] Finished in period=PT13.782
```

## De JSON-interface afhandelen {#handling-the-json-interface}

Ook JSON kan worden verwerkt met het [JQ-gereedschap](https://stedolan.github.io/jq/) zodra het wordt gepubliceerd.

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == true)'
```

Met de uitvoer:

```
{
  "timestamp": "2018-02-13T14:20:18.894+01:00",
  "suspicion": true,
  "pattern": {
    "code": "ECU",
    "type": "extraneous.content.usage",
    "detective": "ContentAccessDetector",
    "moreInfo": "https://www.adobe.com/go/aem6_ECU"
  },
  "item": {
    "id": "a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f",
    "message": "Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid"
  }
}
```

De voortgang wordt om de 5 seconden gemeld en kan worden opgehaald door andere berichten uit te sluiten dan die welke als verdenking zijn gemarkeerd:

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == false)'
```

Met de uitvoer:

```
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:17.279+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.5"
    ]
  },
  "state": {
    "itemsAnalysed": 57209,
    "itemsAnalysedSize": "26 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT5.003S",
    "elapsedTimeMilliseconds": 5003,
    "itemsPerSecond": 36965
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:22.276+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.5"
    ]
  },
  "state": {
    "itemsAnalysed": 113194,
    "itemsAnalysedSize": "46 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT10S",
    "elapsedTimeMilliseconds": 10000,
    "itemsPerSecond": 24092
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:25.762+01:00",
  "type": "FINISHED",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.5"
    ]
  },
  "state": {
    "itemsAnalysed": 140744,
    "itemsAnalysedSize": "63 MB",
    "suspicionsFound": 1
  },
  "progress": {
    "elapsedTime": "PT13.486S",
    "elapsedTimeMilliseconds": 13486,
    "itemsPerSecond": 19907
  }
}
{
  "suspicion": false,
  "type": "SUMMARY",
  "suspicionsFound": 1,
  "totalTime": "PT13.487S"
}
```

>[!NOTE]
De aanbevolen methode is om de gehele uitvoer van krullen in het bestand op te slaan en deze vervolgens via `jq` of `grep` naar het type filterinformatie te verwerken.

## Detectiebereik {#scope}

Met de huidige patroondetector kunt u controleren:

* OSGi bundelt uitvoer en invoer wanverhouding
* De het verkopen middeltypes en supertypes (met onderzoek-weg inhoudsoverlays) gebruiken
* definities van eiken-indexen (compatibiliteit)
* VLT-pakketten (overmatig gebruik)
* rep:Compatibiliteit van gebruikersknooppunten (in de context van OAuth-configuratie)

>[!NOTE]
Houd er rekening mee dat patroondetector de waarschuwingen voor een upgrade nauwkeurig probeert te voorspellen. In sommige scenario&#39;s kan dit echter leiden tot onjuiste positieven.

