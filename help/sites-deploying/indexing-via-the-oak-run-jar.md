---
title: Indexering via de eiken-run-jar
description: Leer hoe u indexering uitvoert via de Oak-run Jar.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: dcec8c1b-13cc-486c-b1a4-62e6eb3184ad
source-git-commit: b9c164321baa3ed82ae87a97a325fcf0ad2f6ca0
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---

# Indexering via de eiken-run-jar {#indexing-via-the-oak-run-jar}

De eiken-looppas steunt alle indexerende gebruiksgevallen op de bevellijn zonder het moeten van JMX niveau werken. De voordelen van de &quot;eak-run&quot;-aanpak zijn:

1. Het is een nieuwe indexerende toolset voor AEM 6.4
1. Het vermindert tijd-aan-herindex die nuttige gevolgen re-indextijden op grotere bewaarplaatsen heeft
1. Het vermindert hulpmiddelverbruik tijdens het re-indexeren in AEM die in betere systeemprestaties voor andere AEM activiteiten resulteert
1. Oak-run biedt out-of-band ondersteuning: Als de productieomstandigheden u geen redex op productie instanties laten in werking stellen, kan een gekloonde milieu voor re-indexering worden gebruikt om kritieke prestatieseffect te vermijden.

Hieronder volgt een lijst met gebruiksgevallen die kunnen worden gebruikt bij het uitvoeren van indexeringsbewerkingen via de `oak-run` gebruiken.

## Consistentiecontroles index {#indexconsistencychecks}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Hoofdlettergebruik 1 - Consistentiecontrole index](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck).

* `oak-run.jar`bepaalt snel of de indexen van het Eik van Lucene corrupt zijn.
* Het is veilig om op een in gebruik AEM instantie voor consistentie te lopen controleniveaus 1 en 2.

![Consistentiecontroles index](assets/screen_shot_2017-12-14at135758.png)

## Indexstatistieken {#indexstatistics}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Hoofdlettergebruik 2 - Indexstatistieken](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics)

* `oak-run.jar` Hiermee plaatst u alle indexdefinities, belangrijke indexstatussen en indexinhoud voor offline analyse.
* Veilig om uit te voeren op een AEM.

![image2017-12-19_9-47-40](assets/image2017-12-19_9-47-40.png)

## Beslissingsstructuur voor opnieuw indexeren nadering {#reindexingapproachdecisiontree}

Dit diagram is een beslissingsboom voor wanneer om de diverse re-indexerende benaderingen te gebruiken.

![eik_-_rendexingwithoak-run](assets/oak_-_reindexingwithoak-run.png)

## MongoMK/RDMBMK opnieuw indexeren {#reindexingmongomk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Hoofdlettergebruik 3 - opnieuw indexeren](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### Voorvertoning van tekst voor SegmentNodeStore en DocumentNodeStore {#textpre-extraction}

[Tekstomloop vooraf](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) (een eigenschap die met AEM 6.3) heeft bestaan kan worden gebruikt om de tijd te verminderen om opnieuw te indexeren. De preextractie van de tekst kan met alle re-indexerende benaderingen worden gebruikt.

Afhankelijk van de `oak-run.jar` de indexerende benadering, zal er diverse stappen aan beide kanten van de Perform Reindex stap in het hieronder diagram zijn.

![Voorvertoning van tekst voor SegmentNodeStore en DocumentNodeStore](assets/4.png)

>[!NOTE]
>
>Oranje duidt activiteiten aan waarbij AEM zich in een onderhoudsvenster moeten bevinden.

### Online opnieuw indexeren voor MongoMK of RDBMK met behulp van eak-run.jar {#onlinere-indexingformongomk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Opnieuw indexeren - DocumentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

Dit is de geadviseerde methode voor het opnieuw indexeren van MongoMK (en RDBMK) AEM installaties. Er mag geen andere methode worden gebruikt.

Voer dit proces alleen uit tegen één AEM instantie in de cluster.

![Online opnieuw indexeren voor MongoMK of RDBMK met behulp van eak-run.jar](assets/5.png)

## TarMK opnieuw indexeren {#re-indexingtarmk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Opnieuw indexeren - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **Koude stand-byoverwegingen (TarMK)**

   * Er zijn geen speciale overwegingen voor Koude Reserve; De Cold Standby instanties synchroniseren verandert zoals gewoonlijk.

* **AEM-publicatiekoppelingen (publicatiekoppelingen voor AE moeten altijd TarMK zijn)**

   * Voor publicatielandbouwbedrijf moet het voor alle OF de stappen op één enkele uitvoeren publiceren en dan de opstelling voor anderen klonen (het nemen van alle gebruikelijke precaties wanneer het klonen AEM instanties; sling.id - moet hier iets aan koppelen)

### Online opnieuw indexeren voor TarMK {#onlinere-indexingfortarmk}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Online opnieuw indexeren - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

Dit is de methode die vóór de introductie van de nieuwe indexeringsmogelijkheden van eak-run.jar wordt gebruikt. Hierbij wordt het `reindex=true` eigenschap op de index van de eik.

Deze benadering kan worden gebruikt als de tijd en prestatiesgevolgen aan index voor de klant aanvaardbaar zijn. Dit is vaak het geval voor kleine tot middelgrote AEM.

![Online opnieuw indexeren voor TarMK](assets/6.png)

### Online TarMK opnieuw indexeren met behulp van eak-run.jar {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Online opnieuw indexeren - SegmentNodeStore - De AEM-instantie wordt uitgevoerd](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

Het online opnieuw indexeren van TarMK gebruikend eak-run.jar is sneller dan [Online opnieuw indexeren voor TarMK](#onlinere-indexingfortarmk) hierboven beschreven. Het vereist echter ook uitvoering tijdens een onderhoudsvenster; met de vermelding dat het venster korter zal zijn, en meer stappen worden vereist om het re-indexeren uit te voeren.

>[!NOTE]
>
>Oranje duidt op transacties waarbij AEM moeten worden uitgevoerd in een reserveperiode.

![Online TarMK opnieuw indexeren met behulp van eak-run.jar](assets/7.png)

### Offline opnieuw indexeren TarMK met gebruik van eikenrun.jar {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Online opnieuw indexeren - SegmentNodeStore - de AEM instantie is gesloten](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

Offline opnieuw indexeren van TarMK is het eenvoudigst `oak-run.jar` gebaseerde re-indexing benadering voor TarMK aangezien het één enkele vereist `oak-run.jar` opmerking. Het vereist echter dat de AEM-instantie wordt afgesloten.

>[!NOTE]
>
>Rood geeft bewerkingen aan waarbij AEM moet worden afgesloten.

![Offline opnieuw indexeren TarMK met gebruik van eikenrun.jar](assets/8.png)

### Out-of-band re-Indexing TarMK gebruikend oak-run.jar  {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario raadpleegt u [Opnieuw indexeren buiten bandbreedte - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

Het opnieuw indexeren van out-of-band minimaliseert het effect van het opnieuw indexeren op de instanties van de in-gebruiks AEM.

>[!NOTE]
>
>Rood geeft bewerkingen aan waarbij AEM kan worden afgesloten.

![Out-of-band re-Indexing TarMK gebruikend oak-run.jar](assets/9.png)

## Indexdefinities bijwerken {#updatingindexingdefinitions}

>[!NOTE]
>
>Voor meer gedetailleerde informatie over dit scenario, zie [Hoofdlettergebruik 4 - Indexdefinities bijwerken](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions).

### Indexdefinities maken en bijwerken op TarMK met ACS Zorg voor index {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS verzekert Index een communautair gesteund project is, en niet door de Steun van Adobe wordt gesteund.

Zo kunt u de definitie van de verzendindex bepalen aan de hand van het inhoudspakket. Dit leidt er later toe dat de index opnieuw wordt geïndexeerd door de markering voor opnieuw indexeren in te stellen op `true`. Dit werkt voor kleinere instellingen waarbij het opnieuw indexeren niet lang duurt.

Zie voor meer informatie de [ACS garandeert indexdocumentatie](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) voor meer informatie.

### Indexdefinities maken en bijwerken op TarMK met behulp van eak-run.jar {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

Als de tijd of het effect van de prestaties van het opnieuw indexeren met niet-`oak-run.jar` de volgende methoden zijn te hoog: `oak-run.jar` De gebaseerde benadering kan worden gebruikt om de definities van de Index van Lucene in een op TarMK gebaseerde AEM in te voeren en opnieuw te indexeren.

![Indexdefinities maken en bijwerken op TarMK met behulp van eak-run.jar](assets/10.png)

### Indexdefinities maken en bijwerken op MonogMK met behulp van eak-run.jar {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

Als de tijd of het effect van de prestaties van het opnieuw indexeren met niet-`oak-run.jar` de volgende methoden zijn te hoog: `oak-run.jar` De gebaseerde benadering kan worden gebruikt om de definities van de Index van Lucene in op MongoMK gebaseerde AEM installaties in te voeren en opnieuw te indexeren.

![Indexdefinities maken en bijwerken op MonogMK met behulp van eak-run.jar](assets/11.png)
