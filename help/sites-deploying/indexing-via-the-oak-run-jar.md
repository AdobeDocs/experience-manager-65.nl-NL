---
title: Indexering via de eiken-run-jar
seo-title: Indexering via de eiken-run-jar
description: Leer hoe u indexering uitvoert via de Oak-run Jar.
seo-description: Leer hoe u indexering uitvoert via de Oak-run Jar.
uuid: 09a83ab9-92ec-4b55-8d24-2302f28fc2e4
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: c8a505ab-a075-47da-8007-43645a8c3ce5
translation-type: tm+mt
source-git-commit: 3f53945579eaf5de1ed0b071aa9cce30dded89f1

---


# Indexering via de eiken-run-jar {#indexing-via-the-oak-run-jar}

De eiken-looppas steunt alle indexerende gebruiksgevallen op de bevellijn zonder het moeten van JMX niveau werken. De voordelen van de &quot;eak-run&quot;-aanpak zijn:

1. Het is een nieuwe indexerende toolset voor AEM 6.4
1. Het vermindert tijd-aan-herdex die nuttige gevolgen re-indextijden op grotere bewaarplaatsen heeft
1. Het vermindert het verbruik van hulpbronnen tijdens het opnieuw indexeren in AEM, wat resulteert in betere systeemprestaties voor andere AEM-activiteiten
1. Oak-run biedt out-of-band ondersteuning: Als de productieomstandigheden het niet toestaan om op productieinstanties opnieuw te indexeren, kan een gekloonde milieu voor re-indexering worden gebruikt om kritieke prestatieseffect te vermijden.

Hieronder vindt u een lijst met gebruiksgevallen die kunnen worden gebruikt bij het uitvoeren van indexeringsbewerkingen via het `oak-run` gereedschap.

## Consistentiecontroles index {#indexconsistencychecks}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie Geval 1 van het [Gebruik - de Controle](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck)van de Consistentie van de Index.

* `oak-run.jar`bepaalt snel of de indexen van de luik beschadigd zijn.
* Het is veilig om op een in gebruik AEM instantie voor consistentie te lopen controleniveaus 1 en 2.

![screen_shot_2017-12-14at135758](assets/screen_shot_2017-12-14at135758.png)

## Indexstatistieken {#indexstatistics}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [Gebruik Geval 2 - de Statistieken van de Index](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics)

* `oak-run.jar` Hiermee plaatst u alle indexdefinities, belangrijke indexstatussen en indexinhoud voor offline analyse.
* Veilig om uit te voeren op een AEM-instantie in gebruik.

![image2017-12-19_9-47-40](assets/image2017-12-19_9-47-40.png)

## Beslissingsstructuur voor opnieuw indexeren nadering {#reindexingapproachdecisiontree}

Dit diagram is een beslissingsboom voor wanneer om de diverse re-indexerende benaderingen te gebruiken.

![eik_-_rendexingwithoak-run](assets/oak_-_reindexingwithoak-run.png)

## MongoMK/RDMBMK opnieuw indexeren {#reindexingmongomk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie Geval 3 van het [Gebruik - het opnieuw indexeren](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### Voorvertoning van tekst voor SegmentNodeStore en DocumentNodeStore {#textpre-extraction}

[De pre-extractie](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) van de tekst (een eigenschap die met AEM 6.3 heeft bestaan) kan worden gebruikt om de tijd aan re-index te verminderen. De preextractie van de tekst kan samen met alle re-indexerende benaderingen worden gebruikt.

Afhankelijk van de `oak-run.jar` indexeringsbenadering zullen er diverse stappen aan beide kanten van de Voer re-indexeringsstap in het hieronder diagram zijn.

![4](assets/4.png)

>[!NOTE]
>
>Oranje duidt activiteiten aan waarbij AEM zich in een onderhoudsvenster moet bevinden.

### Online opnieuw indexeren voor MongoMK of RDBMK met behulp van eak-run.jar {#onlinere-indexingformongomk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [Reindex - DocumentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

Dit is de aanbevolen methode voor het opnieuw indexeren van AEM-installaties van MongoMK (en RDBMK). Er mag geen andere methode worden gebruikt.

Dit proces moet slechts tegen één enkele instantie AEM in de cluster worden uitgevoerd.

![5](assets/5.png)

## TarMK opnieuw indexeren {#re-indexingtarmk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [Reindex - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **Koude stand-byoverwegingen (TarMK)**

   * Er wordt geen speciale aandacht besteed aan koude stand-by; De Cold Standby-instanties synchroniseren de wijzigingen op de gebruikelijke manier.

* **AEM-publicatiekoppelingen (publicatiekoppelingen voor AE moeten altijd TarMK zijn)**

   * Voor publicatielandbouwbedrijf moet het voor alle OF de stappen op één enkele uitvoeren publiceren en dan de opstelling voor anderen klonen (het nemen van alle gebruikelijke precaties wanneer het klonen van AEM instanties; sling.id - moet hier iets aan koppelen)

### Online opnieuw indexeren voor TarMK {#onlinere-indexingfortarmk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [Online Reindex - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

Dit is de methode die wordt gebruikt vóór de implementatie van de nieuwe indexeringsmogelijkheden van eak-run.jar. Dit kan worden gedaan door de `reindex=true` eigenschap in te stellen op de eiken-index.

Deze benadering kan worden gebruikt als de tijd en prestatiesgevolgen aan index voor de klant aanvaardbaar zijn. Dit geldt vaak voor kleine tot middelgrote AEM-installaties.

![6](assets/6.png)

### Online TarMK opnieuw indexeren met behulp van eak-run.jar {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [Online Reindex - SegmentNodeStore - de Instantie AEM loopt](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

Het online opnieuw indexeren van TarMK is sneller dan Online TarkMK die hierboven wordt beschreven opnieuw indexeert. Nochtans, vereist het ook uitvoering tijdens een onderhoudsvenster, met de methode dat het venster korter zal zijn, en meer stappen worden vereist om het re-indexeren uit te voeren.

>[!NOTE]
>
>Oranje duidt op transacties waarbij AEM moet worden uitgevoerd in een onderhoudsperiode.

![7](assets/7.png)

### Offline opnieuw indexeren TarMK met gebruik van eikenrun.jar {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [Online Opnieuw indexeren - SegmentNodeStore - de Instantie AEM is gesloten](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

Offline opnieuw indexeren van TarMK is de eenvoudigste `oak-run.jar` gebaseerde re-indexerende benadering voor TarMK aangezien het één enkele `oak-run.jar` commentaar vereist. De AEM-instantie moet echter worden afgesloten.

>[!NOTE]
>
>Met rood worden bewerkingen aangegeven waarbij AEM moet worden afgesloten.

![8](assets/8.png)

### Out-of-band re-Indexing TarMK gebruikend oak-run.jar {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie betreffende dit scenario, zie [uit Band opnieuw indexeren - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

Het opnieuw indexeren van out-of-band minimaliseert het effect van het opnieuw indexeren op in-use AEM instanties.

>[!NOTE]
>
>Met rood worden bewerkingen aangegeven waarbij AEM kan worden afgesloten.

![9](assets/9.png)

## Indexdefinities bijwerken {#updatingindexingdefinitions}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario, zie Geval 4 van het [Gebruik - het Bijwerken van de Definities](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions)van de Index.

### Indexdefinities maken en bijwerken op TarMK met ACS Zorg voor index {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS Zorg ervoor dat Index een door de gemeenschap ondersteund project is en niet door de ondersteuning van Adobe wordt ondersteund.

Zo kan de definitie van de verzendindex worden gedefinieerd via een inhoudspakket, wat later leidt tot een nieuwe index via de herindexmarkering op `true`. Dit werkt voor kleinere instellingen waarbij het opnieuw indexeren niet lang duurt.

Voor meer informatie, zie [ACS verzekert de documentatie](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) van de Index voor details.

### Indexdefinities maken en bijwerken op TarMK met behulp van eak-run.jar {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

Als het tijd- of prestatieseffect van het opnieuw indexeren met niet- `oak-run.jar` methodes te hoog is, kan de volgende `oak-run.jar` gebaseerde benadering worden gebruikt om de definities van de Index van Lucene in een op TarMK gebaseerde AEM installatie in te voeren en opnieuw te indexeren.

![10](assets/10.png)

### Indexdefinities maken en bijwerken op MonogMK met behulp van eak-run.jar {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

Als het tijd- of prestatieeffect van het opnieuw indexeren met niet- `oak-run.jar` methodes te hoog is, kan de volgende `oak-run.jar` gebaseerde benadering worden gebruikt om de definities van de Index van Lucene in op MongoMK gebaseerde AEM installaties in te voeren en opnieuw te indexeren.

![11](assets/11.png)

