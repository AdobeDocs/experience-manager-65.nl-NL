---
title: Indexering door middel van de Oak-run Jar
description: Leer hoe u indexering kunt uitvoeren met de Oak-run Jar.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: dcec8c1b-13cc-486c-b1a4-62e6eb3184ad
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Indexering door middel van de Oak-run Jar {#indexing-via-the-oak-run-jar}

Oak-run ondersteunt alle indexering van gebruiksgevallen op de opdrachtregel zonder dat deze vanaf JMX-niveau moeten werken. De voordelen van de &quot;eak-run&quot;-aanpak zijn:

1. Het is een nieuwe indexerende toolset voor AEM 6.4
1. Het vermindert tijd-aan-herindex die nuttige gevolgen herindextijden op grotere bewaarplaatsen heeft
1. Het vermindert het hulpbronnenverbruik tijdens het herindexeren van AEM, wat resulteert in betere systeemprestaties voor andere AEM
1. Oak-run biedt out-of-band ondersteuning: als de productieomstandigheden het niet mogelijk maken om opnieuw indexering uit te voeren op productie-instanties, kan een gekloonde omgeving worden gebruikt om opnieuw te rendexeren om een kritiek effect op de prestaties te voorkomen.

Hieronder volgt een lijst met gebruiksgevallen die kunnen worden gebruikt bij het uitvoeren van indexeringsbewerkingen met het gereedschap `oak-run` .

## Consistentiecontroles index {#indexconsistencychecks}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; Geval 1 van het Gebruik - de Controle van de Consistentie van de Index &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck).

* `oak-run.jar` bepaalt snel als de indexen van Lucene Oak corrupt zijn.
* Het is veilig om op een in gebruik AEM instantie voor consistentie te lopen controleniveaus 1 en 2.

![&#x200B; de Controles van de Consistentie van de Index &#x200B;](assets/screen_shot_2017-12-14at135758.png)

## Indexstatistieken {#indexstatistics}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; Geval 2 van het Gebruik - de Statistieken van de Index &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics)

* In `oak-run.jar` worden alle indexdefinities, belangrijke indexstatussen en indexinhoud voor offline analyse verwijderd.
* Veilig om uit te voeren op een AEM.

![&#x200B; image2017-12-19_9-47-40 &#x200B;](assets/image2017-12-19_9-47-40.png)

## Beslissingsstructuur voor opnieuw indexeren nadering {#reindexingapproachdecisiontree}

Dit diagram is een beslissingsstructuur voor wanneer de verschillende herindexeringsbenaderingen moeten worden gebruikt.

![&#x200B; eiak_redexingwithoak-looppas &#x200B;](assets/oak_-_reindexingwithoak-run.png)

## MongoMK/RDMBMK opnieuw indexeren {#reindexingmongomk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; Geval 3 van het Gebruik - het opnieuw indexeren &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### Voorvertoning van tekst voor SegmentNodeStore en DocumentNodeStore {#textpre-extraction}

[&#x200B; pre-extractie van de Tekst &#x200B;](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) (een eigenschap die met AEM 6.3) heeft bestaan kan worden gebruikt om de tijd te verminderen om opnieuw te indexeren. De preextractie van de tekst kan met alle het opnieuw indexeren benaderingen worden gebruikt.

Afhankelijk van de `oak-run.jar` indexeringsbenadering, zijn er diverse stappen op één van beide kant van de Uitvoeren Reindex stap in het hieronder diagram.

![&#x200B; Preextractie van de Tekst voor SegmentNodeStore en DocumentNodeStore &#x200B;](assets/4.png)

>[!NOTE]
>
>Oranje duidt activiteiten aan waarbij AEM zich in een onderhoudsvenster moeten bevinden.

### Onlinereïndexering voor MongoMK of RDBMK met behulp van eak-run.jar {#onlinere-indexingformongomk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; Reindex - DocumentNodeStore &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

Dit is de aanbevolen methode voor het opnieuw indexeren van MongoMK (en RDBMK) AEM installaties. Er mag geen andere methode worden gebruikt.

Voer dit proces alleen uit tegen één AEM instantie in de cluster.

![&#x200B; online opnieuw indexeren voor MongoMK of RDBMK gebruikend oak-run.jar &#x200B;](assets/5.png)

## TarMK opnieuw indexeren {#re-indexingtarmk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; opnieuw indexeren - SegmentNodeStore &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **Koude Standby overwegingen (TarMK)**

   * Er zijn geen speciale overwegingen voor Cold Standby; de instanties van de Reserve van de Koude veranderen de synchronisatie zoals gewoonlijk.

* **AEM de Bediende van Publish (de Bediende van Publish van AE zou altijd TarMK moeten zijn)**

   * Voor publiceer landbouwbedrijf, moet het voor allen worden gedaan OF de stappen op één enkele uitvoeren publiceert. Vervolgens kloont u de instellingen voor anderen (alle gebruikelijke voorzorgsmaatregelen nemen bij het klonen AEM instanties; sling.id - moet hier een koppeling maken naar iets).

### Online opnieuw indexeren voor TarMK {#onlinere-indexingfortarmk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; Online Reindex - SegmentNodeStore &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

Dit is de methode die vóór de introductie van de nieuwe indexeringsmogelijkheden van eak-run.jar wordt gebruikt. Dit gebeurt door de eigenschap `reindex=true` in te stellen op de Oak-index.

Deze benadering kan worden gebruikt als de tijd en prestatiesgevolgen aan index voor de klant aanvaardbaar zijn. Dit is vaak het geval voor kleine tot middelgrote AEM.

![&#x200B; Online re-Indexeren voor TarMK &#x200B;](assets/6.png)

### Online TarMK opnieuw indexeren met behulp van eak-run.jar {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; Online Reindex - SegmentNodeStore - de AEM Instantie loopt &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

Het online opnieuw indexeren van TarMK gebruikend oak-run.jar is sneller dan [&#x200B; Online die voor TarMK &#x200B;](#onlinere-indexingfortarmk) hierboven wordt beschreven opnieuw indexeren. Het vereist echter ook uitvoering tijdens een onderhoudsvenster, met de vermelding dat het venster korter is en dat er meer stappen nodig zijn om het opnieuw indexeren uit te voeren.

>[!NOTE]
>
>Oranje duidt op transacties waarbij AEM moeten worden uitgevoerd in een reserveperiode.

![&#x200B; online het Opnieuw indexeren TarMK gebruikend oak-run.jar &#x200B;](assets/7.png)

### Offline opnieuw indexeren TarMK met gebruik van eikenrun.jar {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; Online Reindex - SegmentNodeStore - de AEM Instantie is Zwijg &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

Offline opnieuw indexeren van TarMK is de eenvoudigste `oak-run.jar` gebaseerde benadering voor opnieuw indexeren van TarMK omdat hiervoor één `oak-run.jar` -opmerking nodig is. Het vereist echter dat de AEM-instantie wordt afgesloten.

>[!NOTE]
>
>Rood geeft bewerkingen aan waarbij AEM moet worden afgesloten.

![&#x200B; Offline het Opnieuw indexeren TarMK gebruikend eak-run.jar &#x200B;](assets/8.png)

### Out-of-band re-Indexing TarMK gebruikend oak-run.jar  {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [&#x200B; uit Band opnieuw indexeren - SegmentNodeStore &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

Buiten-de-band herindexeren minimaliseert het effect van het opnieuw indexeren op in-use AEM instanties.

>[!NOTE]
>
>Rood geeft bewerkingen aan waarbij AEM kan worden afgesloten.

![&#x200B; out-of-band re-Indexing TarMK gebruikend oak-run.jar &#x200B;](assets/9.png)

## Indexdefinities bijwerken {#updatingindexingdefinitions}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario, zie [&#x200B; Geval 4 van het Gebruik - het Bijwerken van de Definities van de Index &#x200B;](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions).

### Indexdefinities maken en bijwerken op TarMK met ACS Zorg voor index {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS verzekert Index is een gemeenschap-gesteund project, en niet door de Steun van de Adobe gesteund.

Hierdoor is het mogelijk om indexdefinitie voor verzending te definiëren via het inhoudspakket, wat later resulteert in opnieuw indexeren door de herindexmarkering in te stellen op `true` . Dit werkt voor kleinere instellingen waarbij het opnieuw indexeren niet lang duurt.

Voor meer info, zie [&#x200B; ACS de documentatie van de Index &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) voor details verzekeren.

### Indexdefinities maken en bijwerken op TarMK met behulp van eak-run.jar {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

Als het tijd- of prestatieeffect van het opnieuw indexeren met niet- `oak-run.jar` methodes te hoog is, kan de volgende `oak-run.jar` gebaseerde benadering worden gebruikt om de definities van de Index van Lucene in een op TarMK gebaseerde AEM te invoeren en opnieuw te indexeren.

![&#x200B; Creërend en Bijwerkend indexdefinities op TarMK gebruikend oak-run.jar &#x200B;](assets/10.png)

### Indexdefinities maken en bijwerken op MonogMK met gebruik van eikrun.jar {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

Als het tijd- of prestatieeffect van opnieuw indexeren met niet- `oak-run.jar` methoden te hoog is, kan de volgende `oak-run.jar` -gebaseerde benadering worden gebruikt om Lucene Index-definities te importeren en opnieuw te indexeren in AEM installaties die op MongoMK zijn gebaseerd.

![&#x200B; Creërend en het Bijwerken de Definities van de Index op MonogMK gebruikend oak-run.jar &#x200B;](assets/11.png)
