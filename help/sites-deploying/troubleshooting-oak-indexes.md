---
title: Probleemoplossing voor Oak-indexen
seo-title: Probleemoplossing voor Oak-indexen
description: Hoe te om langzaam opnieuw indexeren te ontdekken en te bevestigen.
seo-description: Hoe te om langzaam opnieuw indexeren te ontdekken en te bevestigen.
uuid: 6567ddae-128c-4302-b7e8-8befa66b1f43
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: ea70758f-6726-4634-bfb4-a957187baef0
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1486'
ht-degree: 0%

---


# Probleemoplossing voor oak-indexen{#troubleshooting-oak-indexes}

## Langzaam opnieuw indexeren {#slow-re-indexing}

AEM intern herindexeringsproces verzamelt gegevens in de opslagplaats en slaat deze op in Eak-indexen om het vragen van inhoud door prestaties te ondersteunen. In uitzonderlijke omstandigheden kan het proces langzaam of zelfs vastlopen. Deze pagina fungeert als gids voor het oplossen van problemen, zodat u kunt zien of de indexering langzaam verloopt, de oorzaak vindt en het probleem verhelpt.

Het is belangrijk om onderscheid te maken tussen opnieuw indexeren die een onterecht lange hoeveelheid tijd vergt, en opnieuw indexeren die een lange hoeveelheid tijd vergt omdat het enorme hoeveelheden inhoud indexeert. De tijd die nodig is om de inhoud te indexeren, wordt bijvoorbeeld geschaald met de hoeveelheid inhoud, zodat grote productieopslagplaatsen langer nodig hebben om opnieuw te indexeren dan kleine opslagplaatsen.

Zie [Beste praktijken op Vragen en het Indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md) voor extra informatie over wanneer en hoe te om inhoud opnieuw te indexeren.

## Eerste detectie {#initial-detection}

De eerste detectie trage indexering vereist het evalueren van `IndexStats` JMX MBans. Ga als volgt te werk voor de betreffende AEM instantie:

1. Open de webconsole en klik op het tabblad JMX of ga naar https://&lt;host>:&lt;port>/system/console/jmx (bijvoorbeeld [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
1. Navigeer naar `IndexStats` Monen.
1. Open `IndexStats` MBans voor &quot; `async`&quot;en &quot; `fulltext-async`&quot;.

1. Voor beide MBeans, controleer als **Done** timestamp en **LastIndexTime** timestamp minder dan 45 minuten van de huidige tijd zijn.

1. Voor één van beide MBean, als de tijdwaarde (**Done** of **LastIndexedTime**) groter is dan 45 minuten van de huidige tijd, dan ontbreekt de indexbaan of neemt te lang. Hierdoor worden de asynchrone indexen stabiel.

## De indexering wordt gepauzeerd na een gedwongen sluiting {#indexing-is-paused-after-a-forced-shutdown}

Een gedwongen sluiting resulteert in AEM het opschorten van asynchrone indexering tot 30 minuten na het opnieuw beginnen, en vereist typisch nog 15 minuten om de eerste re-indexerende pas te voltooien, voor een totaal van ongeveer 45 minuten (die terug naar [Eerste Ontdekking](/help/sites-deploying/troubleshooting-oak-indexes.md#initial-detection) timeframe van 45 minuten). Als u vermoedt dat indexering is gepauzeerd na een geforceerde afsluiting:

1. Ten eerste, bepaal of de AEM instantie op gedwongen wijze werd afgesloten (het AEM proces werd met kracht gedood, of er een stroomuitval plaatsvond) en vervolgens opnieuw werd opgestart.

   * [AEM ](/help/sites-deploying/configure-logging.md) loggingingkan voor dit doel worden herzien.

1. Als de gedwongen sluiting optrad, na opnieuw beginnen, AEM automatisch het opnieuw indexeren voor maximaal 30 minuten opschort.
1. Wacht ongeveer 45 minuten op AEM om normale asynchrone indexeringsverrichtingen te hervatten.

## Te veel thread pool {#thread-pool-overloaded}

>[!NOTE]
>
>Voor AEM 6.1 moet [AEM 6.1 GFP 11](https://helpx.adobe.com/experience-manager/release-notes-aem-6-1-cumulative-fix-pack.html) zijn geïnstalleerd.

In uitzonderlijke omstandigheden, kan de draadpool die wordt gebruikt om asychronous indexing te beheren overbelast worden. Om het indexeren proces te isoleren, kan een draadpool worden gevormd om ander AEM werk te verhinderen met de capaciteit van het Eak om inhoud op geschikte wijze te indexeren. Om dit te doen, zou u moeten:

1. Definieer een nieuwe, geïsoleerde draadpool voor de Apache Sling Scheduler voor asynchrone indexering:

   * Navigeer in de betreffende AEM naar AEM OSGi Web Console>OSGi>Configuration>Apache Sling Scheduler of ga naar https://&lt;host>:&lt;port>/system/console/configMgr (bijvoorbeeld [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr))
   * Voeg een item aan het veld &quot;Toegestane threads&quot; toe met de waarde &quot;eikel&quot;.
   * Klik op Opslaan in de rechterbenedenhoek om de wijzigingen op te slaan.

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. Controleer of de nieuwe Apache Sling Scheduler-thread-pool is geregistreerd en wordt weergegeven in de Apache Sling Scheduler-webconsole.

   * Navigeer naar de AEM OSGi Web console>Status>Sling Scheduler of ga naar https://&lt;host>:&lt;port>/system/console/status-slingplanner (bijvoorbeeld [http://localhost:4502/system/console/status-slingscheduler](http://localhost:4502/system/console/status-slingscheduler))
   * Controleer of de volgende poolitems bestaan:

      * ApacheSlingoak
      * ApacheSlingdefault

   ![chlimage_1-120](assets/chlimage_1-120.png)

## De waarnemingswachtrij is vol {#observation-queue-is-full}

Als er te veel veranderingen en verplichtingen in korte tijd aan de repository worden aangebracht, kan de indexering vertraagd worden vanwege een volledige waarnemingswachtrij. Ten eerste bepalen of de waarnemingswachtrij vol is:

1. Ga naar de webconsole en klik op het tabblad JMX of ga naar https://&lt;host>:&lt;port>/system/console/jmx (bijvoorbeeld [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
1. Open de Statistieken MBean van de Bewaarplaats van de Eak en bepaal als om het even welke `ObservationQueueMaxLength` waarde groter is dan 10.000.

   * Bij normale bewerkingen moet deze maximumwaarde uiteindelijk altijd tot nul worden teruggebracht (met name in de sectie `per second`), zodat wordt gecontroleerd of de waarden voor de seconden van `ObservationQueueMaxLength` 0 zijn.
   * Als de waarden 10.000 of meer zijn en gestaag toenemen, geeft dit aan dat ten minste één (mogelijk meer) wachtrij niet kan worden verwerkt zodra nieuwe wijzigingen (vastleggingen) optreden.
   * Elke waarnemingswachtrij heeft een limiet (standaard ingesteld op 10.000) en als de wachtrij deze limiet bereikt, neemt de verwerking af.
   * Als u MongoMK gebruikt, neemt de snelheid van de interne cache van de eiken toe naarmate de lengte van de rijen toeneemt. Deze correlatie kan worden gezien in een verhoogde `missRate` voor het `DocChildren` geheime voorgeheugen in `Consolidated Cache` statistieken MBean.

1. Om te voorkomen dat de limieten van de waarnemingswachtrij worden overschreden, wordt aanbevolen:

   * Verlaag de constante snelheid van komma&#39;s. Korte punten in vastleggingen zijn aanvaardbaar, maar de constante snelheid moet worden verlaagd.
   * Vergroot de grootte van `DiffCache` zoals beschreven in [Tips voor het afstemmen van prestaties > Afstemmen van Mongo Storage > Grootte van documentcache](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html#main-pars_text_3).

## Een vast opnieuw indexeringsproces identificeren en corrigeren {#identifying-and-remediating-a-stuck-re-indexing-process}

Herindexering kan onder twee omstandigheden als &quot;volledig vastzitten&quot; worden beschouwd:

* Het opnieuw indexeren is zeer langzaam, tot het punt waar geen significante vooruitgang in logboekdossiers betreffende het aantal getransformeerde knopen wordt gemeld.

   * Bijvoorbeeld, als er geen berichten in de loop van een uur zijn, of als de vooruitgang zo langzaam is dat het een week of meer zal vergen om te beëindigen.

* Opnieuw indexeren blijft in een eindeloze lijn hangen als de herhaalde uitzonderingen in de logboekdossiers (bijvoorbeeld, `OutOfMemoryException`) in de het indexeren draad verschijnen. De herhaling van dezelfde uitzondering(en) in het logbestand geeft aan dat er wordt geprobeerd hetzelfde item herhaaldelijk te indexeren, maar dat dit probleem niet wordt opgelost.

Ga als volgt te werk om een vast opnieuw indexeringsproces te identificeren en te corrigeren:

1. Om de oorzaak van de vastgezette indexering te achterhalen, moeten de volgende gegevens worden verzameld:

   * Verzamel 5 notulen van draadstortplaats, één draadstortplaats om de 2 seconden.
   * [Stel het FOUTOPSPORINGSniveau en de logboeken voor de appanten](/help/sites-deploying/configure-logging.md) in.

      * *org.apache.jackrabbit.oak.plugins.index.AsyncIndexUpdate*
      * *org.apache.jackrabbit.oak.plugins.index.IndexUpdate*
   * Verzamel gegevens van async `IndexStats` MBean:

      * Navigeer naar AEM OSGi Webconsole>Main>JMX>IndexState>async

         of ga naar [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats)
   * Gebruik [de consolemodus van eak-run.jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) om de details van te verzamelen wat onder de knoop * `/:async`* bestaat.
   * Verzamel een lijst met controlepunten in de opslagplaats door `CheckpointManager` MBean te gebruiken:

      * AEM OSGi Webconsole>Main>JMX>CheckpointManager>listCheckpoints()

         of ga naar [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager)



1. Na het verzamelen van alle informatie die in Stap 1 wordt geschetst, begin AEM opnieuw.

   * Het opnieuw opstarten van AEM kan het probleem oplossen in geval van een hoge gelijktijdige belasting (overloop van de waarnemingswachtrij of iets dergelijks).
   * Als een nieuw begin het probleem niet oplost, open een kwestie met [Adobe de Zorg van de Klant ](https://helpx.adobe.com/marketing-cloud/contact-support.html) en verstrek alle informatie die in Stap 1 wordt verzameld.

## asynchrone re-indexering {#safely-aborting-asynchronous-re-indexing} veilig afbreken

Opnieuw indexeren kan veilig worden afgebroken (gestopt voordat het wordt voltooid) via `async, async-reindex`en f `ulltext-async` indexbanen ( `IndexStats` bonen). Raadpleeg voor meer informatie de documentatie bij Apache Oak op [How to Abort Reindexing](https://jackrabbit.apache.org/oak/docs/query/indexing.html#abort-reindex). Houd er daarnaast rekening mee dat:

* Het opnieuw indexeren van de eigenschappenindexen Lucene en Lucene kan worden afgebroken, omdat deze van nature asynchroon zijn.
* Het opnieuw indexeren van de indexen van het Bezit van de Eik kan slechts worden geaborteerd als het re-indexeren via `PropertyIndexAsyncReindexMBean` werd geïnitieerd.

Voer de volgende stappen uit om opnieuw indexeren veilig af te breken:

1. Identificeer de IndexStats MBean die de re-indexerende weg controleert die moet worden tegengehouden.

   * Navigeer naar de juiste IndexStats MBean via de JMX-console door naar AEM OSGi Web Console>Main>JMX of https://&lt;host>:&lt;port>/system/console/jmx te gaan (bijvoorbeeld [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
   * Open de IndexStats MBean op basis van de opnieuw indexerende weg die u wilt tegenhouden ( `async`, `async-reindex`, of `fulltext-async`)

      * Om de aangewezen weg en zo de IndexStats MBean instantie te identificeren, bekijk het &quot;async&quot;bezit van de Indexen van het Eak. De eigenschap &quot;async&quot; bevat de naam van het pad: `async`, `async-reindex` of `fulltext-async`.
      * De strook is ook beschikbaar door tot AEM Manager van de Index in de kolom &quot;Async&quot;toegang te hebben. Navigeer naar Operations>Diagnosis>Indexbeheer om Indexbeheer te openen.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Roep de opdracht `abortAndPause()` op de juiste `IndexStats` MBean aan.
1. Markeer de definitie van de eiken-index op de juiste wijze om te voorkomen dat de indexering wordt hervat wanneer de indexeringsstrook wordt hervat.

   * Bij het opnieuw indexeren van een **bestaande** index, plaats het herindexbezit aan vals

      * `/oak:index/someExistingIndex@reindex=false`
   * Of anders, voor een **new** index, of:

      * De eigenschap type instellen op uitgeschakeld

         * `/oak:index/someNewIndex@type=disabled`
      * of verwijder de indexdefinitie volledig

   Leg de wijzigingen vast in de opslagplaats wanneer deze zijn voltooid.

1. Tot slot hervat asychronous indexing on the aborted indexing lane.

   * In `IndexStats` MBean die `abortAndPause()` bevel in Stap 2 uitgeeft, haal `resume()`bevel aan.

## Traag opnieuw indexeren voorkomen {#preventing-slow-re-indexing}

Het is aan te bevelen om tijdens stille periodes (bijvoorbeeld, niet tijdens een grote inhoudspen), en ideaal tijdens onderhoudsvensters opnieuw te indexeren wanneer AEM lading gekend en gecontroleerd is. Zorg er ook voor dat de herindexering niet plaatsvindt tijdens andere onderhoudsactiviteiten.
