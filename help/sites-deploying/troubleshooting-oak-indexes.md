---
title: Probleemoplossing voor Oak-indexen
description: Leer hoe u kunt vaststellen of indexering traag is, de oorzaak kunt achterhalen en het probleem kunt oplossen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 85981463-189c-4f50-9d21-1d2f734b960a
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 0%

---

# Probleemoplossing voor Oak-indexen{#troubleshooting-oak-indexes}

## Langzaam opnieuw indexeren  {#slow-re-indexing}

AEM intern herindexeringsproces verzamelt gegevens in de gegevensopslagruimte en slaat deze op in eiken-indexen ter ondersteuning van het opvragen van inhoud door uitvoerders. In uitzonderlijke omstandigheden kan het proces langzaam of zelfs vastlopen. Deze pagina fungeert als gids voor het oplossen van problemen, zodat u kunt zien of de indexering langzaam verloopt, de oorzaak vindt en het probleem verhelpt.

Het is belangrijk om onderscheid te maken tussen opnieuw indexeren die een onredelijk lange hoeveelheid tijd vergt, en opnieuw indexeren die een lange hoeveelheid tijd vergt omdat het enorme hoeveelheden inhoud indexeert. De tijd die nodig is om de inhoud te indexeren, wordt bijvoorbeeld geschaald met de hoeveelheid inhoud. Het duurt dus langer om grote productieopslagplaatsen opnieuw te indexeren dan kleine opslagplaatsen.

Zie de [Beste praktijken op Vragen en het Indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md) voor aanvullende informatie over wanneer en hoe inhoud opnieuw moet worden geindexeerd.

## Aanvankelijke detectie {#initial-detection}

De initiële detectie vertraagt de indexering vereist dat de `IndexStats` JMX MBeans. Ga als volgt te werk voor de betreffende AEM instantie:

1. Open de webconsole en klik op het tabblad JMX of ga naar https://&lt;host>:&lt;port>/system/console/jmx (bijvoorbeeld [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
1. Ga naar de `IndexStats` Bonen.
1. Open de `IndexStats` MBeans voor &quot; `async`&quot; en &quot; `fulltext-async`&quot;.

1. Voor beide MBeans, controleer als **Gereed** tijdstempel en **LastIndexTime** de tijdstempel is minder dan 45 minuten van de huidige tijd.

1. Voor één van beide MBean, als de tijdwaarde (**Gereed** of **LastIndexedTime**) is meer dan 45 minuten van de huidige tijd, dan ontbreekt de indexbaan of neemt te lang. Dit probleem veroorzaakt de asynchrone indexen om stabiel te zijn.

## De indexering wordt gepauzeerd na een gedwongen sluiting {#indexing-is-paused-after-a-forced-shutdown}

Een gedwongen sluiting resulteert in AEM het opschorten van asynchrone indexering tot 30 minuten na het opnieuw beginnen. Het duurt meestal nog 15 minuten om de eerste herindexeringspas af te ronden, voor een totaal van ongeveer 45 minuten (terugkoppelen naar de [Aanvankelijke detectie](/help/sites-deploying/troubleshooting-oak-indexes.md#initial-detection) tijdsbestek van 45 minuten). Als indexeren wordt gepauzeerd na een gedwongen sluiting:

1. Bepaal eerst of de AEM instantie geforceerd is afgesloten (het AEM proces is met kracht gedood of er is een stroomstoring opgetreden) en begin later opnieuw.

   * [AEM](/help/sites-deploying/configure-logging.md) kunnen voor dit doel worden herzien.

1. Als de gedwongen sluiting optrad, na het opnieuw opstarten, AEM automatisch het opnieuw indexeren gedurende maximaal 30 minuten op.
1. Wacht ongeveer 45 minuten op AEM om normale asynchrone indexeringsverrichtingen te hervatten.

## Thread pool overloaded {#thread-pool-overloaded}

>[!NOTE]
>
>Voor AEM 6.1 moet u ervoor zorgen dat [AEM 6.1 GVB 11](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html) is geïnstalleerd.

In uitzonderlijke omstandigheden, kan de draadpool die wordt gebruikt om asynchrone indexering te beheren overbelast worden. Om het indexeren proces te isoleren, kan een draadpool worden gevormd om ander AEM werk te verhinderen met de capaciteit van het Eak om inhoud op geschikte wijze te indexeren. Voer in dergelijke gevallen de volgende handelingen uit:

1. Definieer een nieuwe, geïsoleerde draadpool voor de Apache Sling Scheduler voor asynchrone indexering:

   * Navigeer in de betreffende AEM naar AEM OSGi Web Console>OSGi>Configuration>Apache Sling Scheduler of ga naar https://&lt;host>:&lt;port>/system/console/configMgr (bijvoorbeeld [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr))
   * Voeg een item aan het veld &quot;Toegestane threads&quot; toe met de waarde &quot;eikel&quot;.
   * Klik op **Opslaan** rechtsonder.

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. Controleer of de nieuwe Apache Sling Scheduler-thread-pool is geregistreerd en wordt weergegeven in de webconsole van Apache Sling Scheduler-status.

   * Navigeer naar de AEM OSGi Webconsole>Status>Sling Scheduler of ga naar https://&lt;host>:&lt;port>/system/console/status-slingplanner (bijvoorbeeld [http://localhost:4502/system/console/status-slingscheduler](http://localhost:4502/system/console/status-slingscheduler))
   * Controleer of de volgende poolitems aanwezig zijn:

      * ApacheSlingoak
      * ApacheSlingdefault

   ![chlimage_1-120](assets/chlimage_1-120.png)

## De waarnemingswachtrij is vol {#observation-queue-is-full}

Als er te veel veranderingen en verplichtingen in korte tijd aan de gegevensopslagplaats worden aangebracht, kan de indexering worden vertraagd vanwege een volledige waarnemingswachtrij. Bepaal eerst of de waarnemingswachtrij vol is:

1. Ga naar de webconsole en klik op het tabblad JMX of ga naar https://&lt;host>:&lt;port>/system/console/jmx (bijvoorbeeld [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
1. Open de Statistieken van de Bewaarplaats van de Eak MB en bepaal als om het even welk `ObservationQueueMaxLength` waarde is groter dan 10.000.

   * Bij normale bewerkingen moet deze maximumwaarde uiteindelijk altijd tot nul worden teruggebracht (met name in de `per second` ) om te controleren of de `ObservationQueueMaxLength`s seconden metriek is 0.
   * Als de waarden 10.000 of meer zijn en gestaag toenemen, geeft dit aan dat ten minste één (mogelijk meer) wachtrij niet kan worden verwerkt zodra nieuwe wijzigingen (vastleggingen) optreden.
   * Elke waarnemingswachtrij heeft een limiet (standaard ingesteld op 10.000) en als de wachtrij deze limiet bereikt, neemt de verwerking af.
   * Als u MongoMK gebruikt, neemt de snelheid van de interne cache van de eiken toe naarmate de lengte van de rijen toeneemt. Deze correlatie kan gezien worden in een verhoogde `missRate` voor de `DocChildren` in de cache `Consolidated Cache` statistieken MBean.

1. Om te voorkomen dat de limieten van de waarnemingswachtrij worden overschreden, wordt aanbevolen:

   * Verlaag de constante snelheid van komma&#39;s. Korte pieken in vastleggingen zijn aanvaardbaar, maar de constante snelheid moet worden verlaagd.
   * De grootte van de `DiffCache` zoals beschreven in [Tips voor het afstemmen van prestaties > Mongo Storage Tuning > Documentcache-grootte](/help/sites-deploying/configuring-performance.md).

## Een vast herindexeringsproces identificeren en corrigeren {#identifying-and-remediating-a-stuck-re-indexing-process}

Herindexering kan onder twee omstandigheden als &quot;volledig vastzitten&quot; worden beschouwd:

* Het opnieuw indexeren is langzaam, tot het punt waar geen significante vooruitgang in logboekdossiers betreffende het aantal getransformeerde knopen wordt gemeld.

   * Bijvoorbeeld, als er geen berichten in de loop van een uur zijn, of als de vooruitgang zo langzaam is dat het een week of meer duurt om te beëindigen.

* Het opnieuw indexeren blijft in een eindeloze lijn hangen als de herhaalde uitzonderingen in de logboekdossiers verschijnen (bijvoorbeeld `OutOfMemoryException`) in de indexeringsthread. De herhaling van één of meerdere zelfde uitzonderingen in het logboek, wijst op Eak pogingen om het zelfde ding herhaaldelijk te indexeren, maar op de zelfde kwestie ontbreekt.

Ga als volgt te werk om een vast opnieuw indexeringsproces te identificeren en te repareren:

1. Om de oorzaak van het vastlopen van indexering te identificeren, moet de volgende informatie worden verzameld:

   * Verzamel 5 notulen van draadstortplaats, één draadstortplaats om de 2 seconden.
   * [FOUTOPSPORINGSNIVEAU en logboeken voor de kandidaten instellen](/help/sites-deploying/configure-logging.md).

      * *org.apache.jackrabbit.oak.plugins.index.AsyncIndexUpdate*
      * *org.apache.jackrabbit.oak.plugins.index.IndexUpdate*

   * Gegevens verzamelen van de async `IndexStats` MBean:

      * Navigeer naar AEM OSGi Webconsole>Main>JMX>IndexState>async

        of ga naar [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats)

   * Gebruiken [de consolemodus van eak-run.jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) om de details te verzamelen van wat er onder de * bestaat `/:async`* node.
   * Een lijst met controlepunten in de opslagplaats verzamelen met de `CheckpointManager` MBean:

      * AEM OSGi Webconsole>Main>JMX>CheckpointManager>listCheckpoints()

        of ga naar [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager)

1. Na het verzamelen van alle informatie die in Stap 1 wordt geschetst, begin AEM opnieuw.

   * Het opnieuw opstarten van AEM kan het probleem oplossen als er een hoge gelijktijdige belasting is (overloop van de waarnemingswachtrij of iets dergelijks).
   * Als het probleem niet wordt opgelost door opnieuw opstarten, opent u een probleem met [Klantenservice Adoben](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support) en verstrekt alle informatie die in Stap 1 wordt verzameld.

## Asynchrone herindexering veilig afbreken {#safely-aborting-asynchronous-re-indexing}

Opnieuw indexeren kan veilig worden afgebroken (gestopt voordat het wordt voltooid) via het dialoogvenster `async, async-reindex`en f `ulltext-async` indexeringsstroken ( `IndexStats` bonen). Raadpleeg voor meer informatie de documentatie bij Apache Oak op [Opnieuw indexeren afbreken](https://jackrabbit.apache.org/oak/docs/query/indexing.html#abort-reindex). Overweeg ook het volgende:

* Het opnieuw indexeren van de indexen van het Bezit van Lucene en van Lucene kan worden geaborteerd aangezien zij van nature asynchroon zijn.
* Het opnieuw indexeren van de indexen van het eiken-Bezit kan slechts worden geaborteerd als het opnieuw indexeren via `PropertyIndexAsyncReindexMBean`.

Voer de volgende stappen uit om opnieuw indexeren veilig af te breken:

1. Identificeer de IndexStats MBean die de het opnieuw indexeren weg controleert die moet worden tegengehouden.

   * Navigeer naar de juiste IndexStats MBean via de JMX-console door naar AEM OSGi Web Console>Main>JMX of https:// te gaan&lt;host>:&lt;port>/system/console/jmx (bijvoorbeeld [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
   * Open de IndexStats MBean op basis van het opnieuw indexeren pad dat u wilt stoppen ( `async`, `async-reindex`, of `fulltext-async`)

      * Om de aangewezen weg en zo de IndexStats MBean instantie te identificeren, bekijk het &quot;async&quot;bezit van de Indexen van het Eak. De eigenschap &quot;async&quot; bevat de naam van het pad: `async`, `async-reindex`, of `fulltext-async`.
      * De strook is ook beschikbaar door tot AEM Manager van de Index in de kolom &quot;Async&quot;toegang te hebben. Navigeer naar Operations>Diagnosis>Indexbeheer om Indexbeheer te openen.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. De `abortAndPause()` de juiste `IndexStats` MBean.
1. Markeer de definitie van de eiken-index op de juiste wijze om te voorkomen dat het indexeren van de rijstrook wordt hervat.

   * Bij het opnieuw indexeren van een **bestaand** index, stel de eigenschap voor opnieuw indexeren in op false

      * `/oak:index/someExistingIndex@reindex=false`

   * Of anders, voor een **new** index, ofwel:

      * De eigenschap type instellen op uitgeschakeld

         * `/oak:index/someNewIndex@type=disabled`

      * of verwijder de indexdefinitie volledig

   Leg de wijzigingen vast in de opslagplaats wanneer deze zijn voltooid.

1. Tot slot hervat asynchrone indexering op de geaborteerde indexerende weg.

   * In de `IndexStats` MBean die de `abortAndPause()` bevel in Stap 2, haalt het `resume()`gebruiken.

## Langzaam opnieuw indexeren voorkomen {#preventing-slow-re-indexing}

Het is het beste om opnieuw te indexeren tijdens rustige perioden (bijvoorbeeld niet tijdens een grote inname van inhoud), en idealiter tijdens onderhoudsvensters wanneer AEM lading bekend en gecontroleerd is. Zorg er ook voor dat de herkoppeling niet plaatsvindt tijdens andere onderhoudsactiviteiten.
