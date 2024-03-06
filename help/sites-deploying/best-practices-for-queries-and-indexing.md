---
title: Beste praktijken voor Vragen en het Indexeren
description: Dit artikel bevat richtlijnen voor het optimaliseren van indexen en query's.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 6dfaa14d-5dcf-4e89-993a-8d476a36d668
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '4518'
ht-degree: 0%

---

# Beste praktijken voor Vragen en het Indexeren{#best-practices-for-queries-and-indexing}

Samen met de overgang aan Eak in AEM 6, werden sommige belangrijke veranderingen aangebracht in de manier dat de vragen en de indexen worden beheerd. Onder Jasje 2 werd alle inhoud standaard geïndexeerd en kon er vrij om worden gevraagd. In eiken moeten indexen handmatig worden gemaakt onder de optie `oak:index` knooppunt. Een vraag kan zonder een index worden uitgevoerd, maar voor grote datasets, zal het langzaam lopen, of zelfs afbreken.

Dit artikel schetst wanneer om indexen tot stand te brengen en wanneer zij niet nodig zijn, trucs om het gebruiken van vragen te vermijden wanneer zij niet noodzakelijk zijn, en uiteinden voor het optimaliseren van uw indexen en vragen om zo optimaal mogelijk te presteren.

Lees ook de [Documentatie bij het schrijven van query&#39;s en indexen is onduidelijk](/help/sites-deploying/queries-and-indexing.md). Naast indexen die een nieuw concept in AEM 6 zijn, zijn er syntactische verschillen in vragen van het Eak die in overweging moeten worden genomen wanneer het migreren van code van een vorige AEM installatie.

## Wanneer moet u query&#39;s gebruiken? {#when-to-use-queries}

### Opslagplaats en Taxonomie-ontwerp {#repository-and-taxonomy-design}

Bij het ontwerpen van de taxonomie van een gegevensopslagruimte moeten verschillende factoren in aanmerking worden genomen. Dit zijn onder andere toegangsbeheer, lokalisatie, component en overerving van pagina-eigenschappen.

Terwijl het ontwerpen van een taxonomie die deze zorgen richt, is het ook belangrijk om de &quot;draagbaarheid&quot;van het indexeren ontwerp te overwegen. In deze context is de verhandelbaarheid de mogelijkheid van een taxonomie die het mogelijk maakt inhoud voorspelbaar toegankelijk te maken op basis van het pad ervan. Dit zal voor een krachtiger systeem maken dat gemakkelijker is te handhaven dan één die het runnen van vele vragen vereist.

Ook, wanneer het ontwerpen van een taxonomie, is het belangrijk om te overwegen of het opdracht geven belangrijk is. In gevallen waar expliciete het opdracht geven niet wordt vereist en vele sibling knopen worden verwacht, wordt het verkieslijk om een ongeordend knooptype zoals te gebruiken `sling:Folder` of `oak:Unstructured`. In gevallen waarin bestelling vereist is, `nt:unstructured`, en `sling:OrderedFolder` zijn geschikter.

### Zoekopdrachten in componenten {#queries-in-components}

Omdat de vragen één van de meer het belasten verrichtingen op een AEM systeem kunnen zijn, is het een goed idee om hen in uw componenten te vermijden. Als u meerdere query&#39;s hebt uitgevoerd telkens wanneer een pagina wordt gerenderd, kan dit vaak de prestaties van het systeem nadelig beïnvloeden. Er zijn twee strategieën die kunnen worden gebruikt om het uitvoeren van query&#39;s bij het renderen van componenten te voorkomen: **knooppunten doorlopen** en **Prefetingresultaten**.

#### Doorlopende knooppunten {#traversing-nodes}

Als de gegevensopslagplaats op een dergelijke manier wordt ontworpen dat vroegere kennis van de plaats van de vereiste gegevens toestaat, kan de code die deze gegevens van de noodzakelijke wegen terugwint worden opgesteld zonder het moeten vragen in werking stellen om het te vinden.

Een voorbeeld hiervan is het renderen van inhoud die binnen een bepaalde categorie past. Een manier is om de inhoud te ordenen met een categorie-eigenschap die kan worden gevraagd om een component te vullen die items in een categorie weergeeft.

Een betere benadering zou zijn om deze inhoud in een taxonomie door categorie te structureren zodat het manueel kan worden teruggewonnen.

Als de inhoud bijvoorbeeld wordt opgeslagen in een taxonomie die lijkt op:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

De `/content/myUnstructuredContent/parentCategory/childCategory` de knoop kan eenvoudig worden teruggewonnen, zijn kinderen kunnen worden ontleed en worden gebruikt om de component terug te geven.

Wanneer u te maken hebt met een kleine of homogene resultaatset, kan het bovendien sneller zijn om de gegevensopslagruimte te doorlopen en de vereiste knooppunten te verzamelen in plaats van een query te maken om dezelfde resultatenset te retourneren. In het algemeen moeten vragen worden vermeden wanneer dat mogelijk is.

#### Voorkeursresultaten {#prefetching-results}

Soms staan de inhoud of de vereisten rond de component het gebruik van knoopverkeer als methode om de vereiste gegevens terug te winnen niet toe. In deze gevallen, moeten de vereiste vragen worden uitgevoerd alvorens de component wordt teruggegeven zodat de optimale prestaties voor het eind - gebruiker wordt gewaarborgd.

Als de resultaten die voor de component worden vereist op het ogenblik kunnen worden berekend dat het wordt geschreven en er geen verwachting is dat de inhoud zal veranderen, kan de vraag worden uitgevoerd wanneer de auteur montages in de dialoog toepast.

Als de gegevens of de inhoud regelmatig zullen veranderen, kan de vraag op een programma of via een luisteraar voor updates aan de onderliggende gegevens worden uitgevoerd. Vervolgens kunnen de resultaten naar een gedeelde locatie in de opslagplaats worden geschreven. Om het even welke componenten die deze gegevens nodig hebben kunnen dan de waarden van deze enige knoop trekken zonder het moeten een vraag bij runtime uitvoeren.

## Zoekopdrachtoptimalisatie {#query-optimization}

Wanneer het runnen van een vraag die geen index gebruikt, worden de waarschuwingen geregistreerd betreffende knoop traversal. Als dit een vraag is die vaak zal lopen, creeer een index. Om te bepalen welke index een bepaalde vraag gebruikt, [Het gereedschap Query uitvoeren](/help/sites-administering/operations-dashboard.md#explain-query) wordt aanbevolen. Voor extra informatie, kan het registreren van de FOUTOPSPORING voor de relevante onderzoek APIs worden toegelaten.

>[!NOTE]
>
>Nadat u een indexdefinitie hebt gewijzigd, moet de index opnieuw worden samengesteld (opnieuw worden gedestilleerd). Afhankelijk van de grootte van de index kan het enige tijd duren om deze te voltooien.

Wanneer het runnen van complexe vragen, kunnen er gevallen zijn waarin het onderbreken van de vraag in veelvoudige kleinere vragen en het aansluiten van de gegevens door code nadat het feit krachtiger is. De aanbeveling voor deze gevallen is om de prestaties van de twee benaderingen te vergelijken om te bepalen welke optie beter zou zijn voor het betrokken gebruiksgeval.

AEM staat het schrijven van vragen op één van drie manieren toe:

* Via de [QueryBuilder-API&#39;s](/help/sites-developing/querybuilder-api.md) (aanbevolen)
* XPath gebruiken (aanbevolen)
* SQL2 gebruiken

Terwijl alle vragen in SQL2 alvorens worden in werking gesteld worden omgezet, is de overheadkosten van vraagomzetting minimaal en zo, zal de grootste zorg wanneer het kiezen van een vraagtaal leesbaarheid en comfortniveau van het ontwikkelingsteam zijn.

>[!NOTE]
>
>Wanneer het gebruiken van QueryBuilder, bepaalt het de resultaattelling door gebrek, die in Oak langzamer in vergelijking met vorige versies van Jasjes is. Om dit te compenseren, kunt u [gulTotal, parameter](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results).

### Het gereedschap Uitleg query {#the-explain-query-tool}

Zoals met om het even welke vraagtaal, moet de eerste stap aan het optimaliseren van een vraag begrijpen hoe het zal lopen. Als u deze activiteit wilt inschakelen, kunt u de [Het gereedschap Query uitvoeren](/help/sites-administering/operations-dashboard.md#explain-query) die deel uitmaakt van het vluchthandboek. Met dit hulpmiddel, kan een vraag binnen worden gestopt en worden verklaard. Een waarschuwing wordt getoond als de vraag kwesties met een grote bewaarplaats en runtime en de indexen zal veroorzaken die worden gebruikt. Het gereedschap kan ook een lijst met trage en populaire query&#39;s laden die vervolgens kunnen worden uitgelegd en geoptimaliseerd.

### FOUTOPSPORING VOOR VRAGEN {#debug-logging-for-queries}

Om wat extra informatie te krijgen over hoe Eak kiest welke te gebruiken index en hoe de vraagmotor eigenlijk een vraag uitvoert, a **DEBUG** de registrerenconfiguratie kan voor de volgende pakketten worden toegevoegd:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

Zorg ervoor om dit registreerapparaat te verwijderen wanneer u het zuiveren van uw vraag hebt gebeëindigd. Het neigt naar een grote hoeveelheid activiteit en kan uiteindelijk uw schijf vullen met logboekdossiers.

Zie voor meer informatie over hoe u dit kunt doen de [Registratiedocumentatie](/help/sites-deploying/configure-logging.md).

### Indexstatistieken {#index-statistics}

Lucene registreert een boon JMX die details over geïndexeerde inhoud met inbegrip van de grootte en het aantal documenten in elk van de indexen zal verstrekken.

U kunt dit bereiken door toegang te krijgen tot de JMX Console op `https://server:port/system/console/jmx`

Nadat u zich hebt aangemeld bij de JMX-console, kunt u zoeken naar **Lucene Index Statistieken** om het te vinden. Andere indexstatistieken zijn te vinden in het **IndexStats** MBean.

Voor vraagstatistieken, bekijk genoemde MBean **Query-statistieken voor onak**.

Als u met een gereedschap als [Luke](https://code.google.com/archive/p/luke/), moet u de console van het Eak gebruiken om de index van `NodeStore` naar een bestandssysteemmap. Voor instructies over hoe te om dit te doen, lees [Lucene-documentatie](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

U kunt de indexen in uw systeem ook in JSON-indeling extraheren. Om dit te doen, moet u toegang hebben `https://server:port/oak:index.tidy.-1.json`

### Zoeklimieten {#query-limits}

**Tijdens de ontwikkeling**

Lage drempelwaarden instellen voor `oak.queryLimitInMemory` (bijvoorbeeld 10000) en eikenhout. `queryLimitReads` (bijvoorbeeld, 5000) en optimaliseer de dure vraag wanneer het raken van een UnsupportedOperationException die &quot;de vraag lezen meer dan x knopen...&quot; zegt

Dit helpt middelintensieve vragen (d.w.z. niet gesteund door om het even welke index of gesteund door minder het behandelen index) te vermijden. Bijvoorbeeld, zou een vraag die 1 miljoen knopen leest tot verhoogde I/O leiden, en negatief de algemene toepassingsprestaties beïnvloeden. Elke query die vanwege bovenstaande limieten mislukt, moet worden geanalyseerd en geoptimaliseerd.

#### **Na de implementatie** {#post-deployment}

* Controleer de logboeken voor vragen die de grote knoop traversal of grote het geheugenconsumptie van de heap teweegbrengen: &quot;

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * De query optimaliseren om het aantal doorgelopen knooppunten te verminderen

* Controleer de logboeken voor vragen die het grote gebruik van het heapgeheugen teweegbrengen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimaliseer de vraag om het gebruik van het heapgeheugen te verminderen

Voor AEM 6.0 - 6.2 versies, kunt u de drempel voor knoopsverplaatsing via parameters JVM in het AEM startmanuscript aanpassen om grote vragen te verhinderen het milieu te overbelasten.

De aanbevolen waarden zijn:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3, zijn de bovengenoemde twee parameters preconfigured uit-van-de-doos, en kunnen via OSGi QueryEngineSettings worden voortgeduurd.

Meer informatie is beschikbaar onder: [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Tips voor het maken van efficiënte indexen {#tips-for-creating-efficient-indexes}

### Moet ik een index maken? {#should-i-create-an-index}

De eerste vraag die u moet stellen bij het maken of optimaliseren van indexen is of deze voor een bepaalde situatie vereist zijn. Als u de vraag in kwestie slechts één of slechts af en toe en bij een off-piek tijd voor het systeem door een partijproces gaat in werking stellen, kan het beter zijn om geen index bij allen tot stand te brengen.

Nadat u een index hebt gemaakt, moet de index ook worden bijgewerkt telkens wanneer de geïndexeerde gegevens worden bijgewerkt. Aangezien dit prestatiesimplicaties voor het systeem draagt, zouden indexen slechts moeten worden gecreeerd wanneer zij worden vereist.

Bovendien zijn indexen alleen nuttig als de gegevens in de index uniek genoeg zijn om ze te rechtvaardigen. Overweeg een index in een boek en de onderwerpen die het behandelt. Wanneer het indexeren van een reeks onderwerpen in een tekst, gewoonlijk zullen er honderden of duizenden ingangen zijn, die u aan een ondergroep van pagina&#39;s laat snel springen om de informatie snel te vinden die u zoekt. Als die index slechts twee of drie items bevat, die u elk op honderden pagina&#39;s aanwijzen, is de index niet nuttig. Hetzelfde concept geldt voor database-indexen. Als er slechts een paar unieke waarden zijn, is de index niet nuttig. Een index kan echter ook te groot worden om nuttig te zijn. Om indexstatistieken te bekijken, zie [Indexstatistieken](/help/sites-deploying/best-practices-for-queries-and-indexing.md#index-statistics) hierboven.

### Luidens- of eigenschapsindexen? {#lucene-or-property-indexes}

Lucene-indexen werden geïntroduceerd in Oak 1.0.9 en bieden krachtige optimalisaties voor de eigenschapsindexen die werden geïntroduceerd bij de eerste introductie van AEM 6. Wanneer u besluit of u Lucene-indexen of eigenschapsindexen wilt gebruiken, moet u rekening houden met het volgende:

* Lucene-indexen bieden veel meer functies dan eigenschapindexen. Een eigenschapindex kan bijvoorbeeld slechts één eigenschap indexeren, terwijl een Lucene-index er veel kan bevatten. Voor meer informatie over alle eigenschappen beschikbaar in de indexen van Lucene, raadpleeg [documentatie](https://jackrabbit.apache.org/oak/docs/query/lucene.html).
* Lucene-indexen zijn asynchroon. Hoewel dit een aanzienlijke prestatieverhoging biedt, kan het ook een vertraging veroorzaken tussen wanneer gegevens naar de gegevensopslagplaats worden geschreven en wanneer de index wordt bijgewerkt. Als het essentieel is om vragen te hebben 100% nauwkeurige resultaten terugkeren, zou een bezitsindex worden vereist.
* Door asynchroon te zijn, kunnen de indexen van Lucene geen uniciteitsbeperkingen afdwingen. Als dit wordt vereist, dan moet een bezitsindex op zijn plaats worden gebracht.

In het algemeen, wordt het geadviseerd u de indexen van Lucene tenzij er een dwingende behoefte is om bezitsindexen te gebruiken zodat u de voordelen van hogere prestaties en flexibiliteit kunt bereiken.

### Solr Indexering {#solr-indexing}

AEM ondersteunt standaard ook Solr-indexering. Dit wordt gebruikt om volledige tekstonderzoek te steunen, maar het kan ook worden gebruikt om om het even welk type van vraag te steunen JCR. Solr zou moeten worden overwogen wanneer de AEM instanties niet de capaciteit van cpu hebben om het aantal vragen te behandelen die in onderzoek intensieve plaatsingen zoals onderzoek gedreven websites met een hoog aantal gezamenlijke gebruikers worden vereist. Alternatief, kan Solr in een op kruipper-gebaseerde benadering worden uitgevoerd om enkele meer geavanceerde eigenschappen van het platform te gebruiken.

Solr indexen kunnen worden gevormd om ingebed op de AEM server voor ontwikkelingsmilieu&#39;s in werking te stellen of aan een verre instantie kunnen worden geoffload om onderzoeksscalability op de productie en het opvoeren milieu&#39;s te verbeteren. Hoewel het offloaden van onderzoek scalability verbetert, introduceert het latentie en wegens dit, wordt niet geadviseerd tenzij vereist. Voor meer informatie over hoe te om de integratie van Solr te vormen en hoe te om de indexen van Solr tot stand te brengen zie [Oak- en indexeringsdocumentatie](/help/sites-deploying/queries-and-indexing.md#the-solr-index).

>[!NOTE]
>
>Terwijl het nemen van de geïntegreerde Solr onderzoeksbenadering zou voor het ontladen van indexeren aan een Solr server toestaan. Als de geavanceerdere eigenschappen van de server van Solr door een op kruipper-gebaseerde benadering worden gebruikt, wordt het extra configuratiewerk vereist.

Het nadeel aan het nemen van deze benadering is dat terwijl door gebrek, AEM vragen ACLs respecteren en zo resultaten verbergen die een gebruiker geen toegang tot heeft, het externaliseren van onderzoek aan een Solr server zal deze eigenschap niet steunen. Als de zoekactie op deze manier extern moet worden uitgevoerd, moet er extra op worden gelet dat de gebruikers geen resultaten krijgen die ze niet zouden moeten zien.

Mogelijke gebruiksgevallen waarin deze aanpak passend kan zijn, zijn gevallen waarin zoekgegevens uit meerdere bronnen moeten worden samengevoegd. U hebt bijvoorbeeld een site die wordt gehost op AEM en een tweede site die wordt gehost op een extern platform. Solr zou kunnen worden gevormd om de inhoud van beide plaatsen te kruipen en hen op te slaan in een bijeengevoegde index. Op die manier kunnen zoekopdrachten naar andere sites worden uitgevoerd.

### Ontwerpoverwegingen {#design-considerations}

De documentatie van het Eak voor indexen van de Luik maakt een lijst van verscheidene overwegingen om te maken wanneer het ontwerpen van indexen:

* Als de query andere padbeperkingen gebruikt, gebruikt u `evaluatePathRestrictions`. Dit staat de vraag toe om de ondergroep van resultaten onder de gespecificeerde weg terug te keren en dan hen te filtreren die op de vraag worden gebaseerd. Anders, zoekt de vraag naar alle resultaten die de vraagparameters in de bewaarplaats aanpassen en dan filter hen die op de weg worden gebaseerd.
* Als de query sortering gebruikt, een expliciete eigenschapdefinitie voor de gesorteerde eigenschap hebben en instellen `ordered` tot `true` daarvoor. Hierdoor kunnen de resultaten als zodanig worden geordend in de index en worden kostbare sorteerbewerkingen tijdens de uitvoering van de query opgeslagen.

* Plaats alleen wat nodig is in de index. Als u overbodige functies of eigenschappen toevoegt, neemt de index toe en vertraagt de prestaties.
* In een bezitsindex, zou het hebben van een unieke bezitsnaam helpen de grootte op een index verminderen, maar voor indexen Lucene, gebruik van `nodeTypes` en `mixins` moet worden gezorgd voor coherente indexen. Een specifieke vraag stellen `nodeType` of `mixin` zal beter presteren dan vragen `nt:base`. Bij het gebruik van deze methode definieert u `indexRules` voor de `nodeTypes` in kwestie.

* Als uw vragen slechts onder bepaalde wegen worden in werking gesteld, dan creeer die indexen onder die wegen. Indexen hoeven niet in de hoofdmap van de opslagplaats te wonen.
* Gebruik één index wanneer alle eigenschappen die worden geïndexeerd verwant zijn om Lucene toe te staan om zo vele bezitsbeperkingen te evalueren mogelijk native. Ook, zal een vraag slechts één index gebruiken, zelfs wanneer het uitvoeren van een toetreden.

### CopyOnRead {#copyonread}

Wanneer de `NodeStore` wordt opgeslagen ver, een geroepen optie `CopyOnRead` kan worden ingeschakeld. De optie zorgt ervoor dat de externe index naar het lokale bestandssysteem wordt geschreven wanneer deze wordt gelezen. Dit kan helpen prestaties voor vragen verbeteren die vaak tegen deze verre indexen in werking worden gesteld.

Dit kan in de console OSGi onder de console worden gevormd **LuceneIndexProvider** service en is standaard ingeschakeld vanaf Eak 1.0.13.

### Indexen verwijderen {#removing-indexes}

Wanneer u een index verwijdert, wordt het altijd aanbevolen de index tijdelijk uit te schakelen door het `type` eigenschap aan `disabled` en voer tests uit om te controleren of uw toepassing correct werkt voordat u de toepassing daadwerkelijk verwijdert. Een index wordt niet bijgewerkt als deze is uitgeschakeld, zodat de index mogelijk niet de juiste inhoud heeft als deze opnieuw wordt ingeschakeld en opnieuw moet worden ingesteld.

Nadat een bezitsindex op een instantie TarMK wordt verwijderd, moet de compensatie in werking worden gesteld om het even welke schijfruimte terug te winnen die in gebruik was. Voor indexen van Lucene, leeft de daadwerkelijke indexinhoud in BlobStore, zodat zou een inzameling van het huisvuil van de gegevensopslag worden vereist.

Wanneer u een index op een MongoDB-instantie verwijdert, zijn de verwijderingskosten evenredig met het aantal knooppunten in de index. Aangezien het schrappen van een grote index problemen kan veroorzaken, is de geadviseerde benadering om de index onbruikbaar te maken en het slechts tijdens een onderhoudsvenster te schrappen, gebruikend een hulpmiddel zoals **eik-mongo.js**. Merk op dat deze benadering niet voor regelmatige knoopinhoud zou moeten worden gebruikt aangezien het gegevensinconsistenties kan introduceren.

>[!NOTE]
>
>Zie voor meer informatie over eikenmongo.js de [Sectie Opdrachtregelgereedschappen](https://jackrabbit.apache.org/oak/docs/command_line.html) van de eiken-documentatie.

### Het JCR-query-controleblad {#jcrquerycheatsheet}

Ter ondersteuning van de creatie van efficiënte JCR-query&#39;s en indexdefinities [JCR-query - Cheat Sheet](assets/JCR_query_cheatsheet-v1.1.pdf) kan tijdens de ontwikkeling worden gedownload en gebruikt als referentie. Het bevat steekproefvragen voor QueryBuilder, XPath, en SQL-2, die veelvoudige scenario&#39;s behandelen die zich verschillend in termen van vraagprestaties gedragen. Het verstrekt ook aanbevelingen voor om indexen van het Eak te bouwen of aan te passen. De inhoud van dit Cheat Sheet is van toepassing op AEM 6.5 en AEM as a Cloud Service.

## Opnieuw indexeren {#re-indexing}

In deze sectie worden de **alleen** aanvaardbare redenen om de indexen van de eik opnieuw te indexeren.

Buiten de hieronder uiteengezette redenen wordt het starten van een nieuwe indexering van eiken wel **niet** gedrag wijzigen of problemen oplossen en de belasting op AEM onnodig verhogen.

Herindexering van de eiken-indexen moet worden vermeden, tenzij een reden in de onderstaande tabellen wordt vermeld.

>[!NOTE]
>
>Voordat u de onderstaande tabellen raadpleegt om te bepalen of herindexering nuttig is, **altijd** verifiëren:
>
>* de vraag correct is
>* de query wordt omgezet in de verwachte index (met [Query uitvoeren](/help/sites-administering/operations-dashboard.md#diagnosis-tools))
>* het indexeringsproces is voltooid
>

### Wijzigingen in indexconfiguratie onderbreken {#oak-index-configuration-changes}

De enige aanvaardbare niet-errende voorwaarden voor het opnieuw indexeren van de indexen van de eikel zijn als de configuratie van een index van de eikel is veranderd.

*Herindexering moet altijd worden benaderd met de nodige aandacht voor de impact ervan op AEM algehele prestaties en moet worden uitgevoerd tijdens perioden van lage activiteit of onderhoudsvensters.*

De volgende details en resoluties zijn mogelijk:

* [Wijziging van indexdefinitie van eigenschap](#property-index-definition-change)
* [Wijziging van de definitie van Lucene-index](#lucene-index-definition-change)

#### Wijziging van indexdefinitie van eigenschap {#property-index-definition-change}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [eigenschapsindexen](https://jackrabbit.apache.org/oak/docs/query/property-index.html)

* Symptomen:

   * Nodes existing before to property index&#39;s definition update missing from results

* Hoe te om te verifiëren:

   * Bepaal of er ontbrekende knooppunten zijn gemaakt/gewijzigd vóór de implementatie van de bijgewerkte indexdefinitie.
   * Controleer de `jcr:created` of `jcr:lastModified` eigenschappen van ontbrekende knooppunten tegen de gewijzigde tijd van de index

* Hoe oplossen:

   * [Opnieuw indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-re-index) de lucene-index
   * U kunt ook op de ontbrekende knooppunten tikken (een goedaardige schrijfbewerking uitvoeren)

      * Vereist handmatige aanrakingen of aangepaste code
      * De set ontbrekende knooppunten moet bekend zijn
      * Vereist het veranderen van om het even welke bezit op de knoop

#### Wijziging van de definitie van Lucene-index {#lucene-index-definition-change}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [lucene-indexen](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten
   * De zoekresultaten weerspiegelen niet het verwachte gedrag van de indexdefinitie
   * Het plan van de vraag rapporteert geen verwachte output die op indexdefinitie wordt gebaseerd

* Hoe te om te verifiëren:

   * Verifieer dat de indexdefinitie gebruikend de statistieken JMX Mbean van de Index (LuceneIndex), methode werd veranderd `diffStoredIndexDefinition`.

* Hoe oplossen:

   * Oak-versies vóór 1.6:

      * [Opnieuw indexeren](#how-to-re-index) de lucene-index

   * Oak-versies 1.6+

      * Als de wijzigingen de bestaande inhoud niet beïnvloeden, hoeft u alleen de inhoud te vernieuwen

         * [Vernieuwen](https://jackrabbit.apache.org/oak/docs/query/lucene.html#stored-index-definition) de lucene-index door instellen [eak:queryIndexDefinition]@refresh=true

      * Anders, [hergroeperen](#how-to-re-index) de lucene-index

         * Opmerking: de indexstatus van de laatste goede herindexering (of eerste indexering) wordt gebruikt totdat een nieuwe herindexering wordt geactiveerd.

### Erkende en uitzonderlijke situaties {#erring-and-exceptional-situations}

In de volgende tabel worden de enige aanvaardbare fouten en uitzonderlijke situaties beschreven waarin het opnieuw indexeren van de eiken-indexen het probleem oplost.

Als er een probleem optreedt met AEM die niet aan de onderstaande criteria voldoen, doet u het volgende **niet** indexen opnieuw indexeren, omdat dit het probleem niet zal oplossen.

De volgende details en resoluties zijn mogelijk:

* [Binair Lucene-indexbestand ontbreekt](#lucene-index-binary-is-missing)
* [Binair Lucene-index is beschadigd](#lucene-index-binary-is-corrupt)

#### Binair Lucene-indexbestand ontbreekt {#lucene-index-binary-is-missing}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [lucene-indexen](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten

* Hoe te om te verifiëren:

   * Het dossier van het foutenlogboek bevat een uitzondering die een binair getal van de index van Lucene zegt mist

* Hoe oplossen:

   * Een doorlopende controle in de repository uitvoeren, bijvoorbeeld:

     [http://localhost:4502/system/console/repositorycheck](http://localhost:4502/system/console/repositorycheck)

     het doorlopen van de gegevensopslagruimte bepaalt of andere binaire bestanden (behalve lucene-bestanden) ontbreken

   * Als binaire getallen anders dan lucene-indexen ontbreken, kunt u terugzetten vanaf een back-up
   * Anders, [hergroeperen](#how-to-re-index) *alles* lucene-indexen
   * Opmerking:

     Deze voorwaarde is indicatief van een misconfigured datastore die in OM HET EVEN WELK binair getal (bijvoorbeeld, activa binaries) kan resulteren om te gaan missen.

     In dit geval herstelt u de laatst bekende goede versie van de opslagplaats om alle ontbrekende binaire bestanden te herstellen.

#### Binair Lucene-index is beschadigd {#lucene-index-binary-is-corrupt}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [lucene-indexen](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten

* Hoe te om te verifiëren:

   * De `AsyncIndexUpdate` (om de vijf seconden) zal met een uitzondering in error.log ontbreken:

     `...a Lucene index file is corrupt...`

* Hoe oplossen:

   * Verwijder de lokale kopie van de index van de lucene

      1. AEM stoppen
      1. Verwijder de lokale kopie van de lucene-index op `crx-quickstart/repository/index`
      1. AEM opnieuw starten

   * Als dit het probleem niet oplost, en `AsyncIndexUpdate` er blijven dan nog uitzonderingen bestaan :

      1. [Opnieuw indexeren](#how-to-re-index) de foutindex
      1. Ook een bestand [Ondersteuning voor Adobe](https://helpx.adobe.com/support.html) kaartje

### Opnieuw indexeren {#how-to-re-index}

>[!NOTE]
>
>In AEM 6.5 [eak-run.jar is de ENLY gesteunde methode](/help/sites-deploying/indexing-via-the-oak-run-jar.md#reindexingapproachdecisiontree) voor opnieuw indexeren op MongoMK- of RDBMK-opslagruimten.

#### Eigenschapindexen opnieuw indexeren {#re-indexing-property-indexes}

* Gebruiken [eak-run.jar](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) om de eigenschapsindex opnieuw te indexeren
* De eigenschap async-redex instellen op true op de index van de eigenschap

   * `[oak:queryIndexDefinition]@reindex-async=true`

* Indexeer de eigenschapindex asynchroon met de webconsole via de **PropertyIndexAsyncReindex** MBean;

  bijvoorbeeld:

  [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex)

#### indexen van eigenschappen van Lucene opnieuw indexeren {#re-indexing-lucene-property-indexes}

* Gebruiken [eak-run.jar naar redex](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) de index van het bezit van Lucene.
* Stel de eigenschap async-redex in op true op de index van de eigenschap lucene

   * `[oak:queryIndexDefinition]@reindex-async=true`

>[!NOTE]
>
>In de voorgaande sectie worden de aanwijzingen voor het opnieuw indexeren van de eik in een overzicht gegeven en in een kader geplaatst van de [Apache Oak-documentatie](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) in de context van AEM.

### Tekstvoorextractie van binaire tekens {#text-pre-extraction-of-binaries}

De preextractie van de tekst is het proces om tekst uit binaire getallen, direct uit de Opslag van Gegevens via een geïsoleerd proces, te halen en te verwerken, en direct blootstellend de gehaalde tekst aan verdere re/indexeringen van Eak indexen.

* Het vooraf uitpakken van eikentekst wordt aanbevolen voor het opnieuw/indexeren van Lucene-indexen in opslagruimten met grote volumes bestanden (binaire bestanden) die extraheerbare tekst bevatten (bijvoorbeeld PDF, Word Docs, PPT&#39;s, TXT, enzovoort) die in aanmerking komen voor full-text zoeken via geïmplementeerde Oak-indexen, bijvoorbeeld `/oak:index/damAssetLucene`.
* De pre-extractie van de tekst komt slechts het re/indexeren van indexen van Lucene, en NIET de bezitsindexen van het Eik ten goede, aangezien de bezitsindexen geen tekst uit binaire getallen halen.
* De preextractie van tekst heeft een groot positief effect wanneer de full-text herindexering van tekst-zware binaire getallen (PDF, Doc, TXT, etc.), terwijl een bewaarplaats van beelden niet de zelfde efficiency zal genieten aangezien de beelden geen extractable tekst bevatten.
* Bij het vooraf extraheren van tekst wordt tekst die betrekking heeft op volledige tekst, op een extra efficiënte manier geëxtraheerd en wordt deze op een extra efficiënte manier aan het opnieuw indexeren/opnieuw indexeren van de eik blootgesteld.

#### Wanneer kan de tekstvoorextractie worden gebruikt? {#when-can-text-pre-extraction-be-used}

Een **bestaand** lucene-index met binaire extractie ingeschakeld

* Verwerking opnieuw indexeren **alles** kandidaatinhoud in de opslagplaats; wanneer de binaire getallen waaruit volledige tekst wordt geëxtraheerd talrijk of complex zijn, wordt een grotere rekenlast voor het uitvoeren van extractie met volledige tekst op AEM geplaatst. De pre-extractie van de tekst beweegt het &quot;computer dure werk&quot;van tekst-extractie in een geïsoleerd proces dat tot AEM Opslag van Gegevens direct toegang heeft, vermijdend overheadkosten en middelgeschil in AEM.

Ondersteuning van de invoering van een **new** lucene index aan AEM met binaire extractie ingeschakeld

* Wanneer een nieuwe index (met binaire toegelaten extractie) in AEM wordt opgesteld, indexeert het Eak automatisch alle kandidaatinhoud op de volgende async full-text indexlooppas. Om dezelfde redenen die in bovenstaande overweging worden beschreven, kan dit leiden tot een te zware belasting bij AEM.

#### Wanneer kan de voorextractie van tekst NIET worden gebruikt? {#when-can-text-pre-extraction-not-be-used}

Tekstomloop kan niet worden gebruikt voor nieuwe inhoud die aan de opslagplaats wordt toegevoegd, en is ook niet nodig.

Nieuwe inhoud wordt toegevoegd aan de repository zal automatisch en incrementeel geïndexeerd worden door het async full-text indexeringsproces (standaard elke 5 seconden).

Onder normale verrichting van AEM, bijvoorbeeld, zal het uploaden van Activa via het Web UI of programmatic ingest van Activa, AEM automatisch en incrementeel full-text index de nieuwe binaire inhoud. Aangezien de hoeveelheid gegevens incrementeel en relatief klein is (ongeveer de hoeveelheid gegevens die in 5 seconden aan de opslagplaats kan worden gepresteerd), kan AEM de full-text extractie uit de binaire getallen uitvoeren tijdens het indexeren zonder de algemene systeemprestaties te beïnvloeden.

#### Vereisten voor het gebruik van tekstvoorextractie {#prerequisites-to-using-text-pre-extraction}

* U zult opnieuw indexeren een lucene index die full-text binaire extractie uitvoert of een nieuwe index opstelt die full-text indexbinaire getallen van bestaande inhoud zal uitvoeren
* De inhoud (binaire bestanden) waaruit tekst vooraf kan worden geëxtraheerd, moet zich in de opslagplaats bevinden
* Een onderhoudsvenster voor het genereren van het CSV-bestand EN voor het uitvoeren van de laatste nieuwe configuratie
* Eak-versie: 1.0.18+, 1.2.3+
* [eak-run.jar](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)versie 1.7.4+
* Een bestandssysteemmap/-share voor het opslaan van geëxtraheerde tekst die toegankelijk is via de indexering AEM instanties

   * De OSGi-config van de preextractie van de Tekst vereist een weg van het dossiersysteem aan de gehaalde tekstdossiers, zodat moeten zij direct van de AEM instantie (lokale aandrijving of het dossier delen onderstel) toegankelijk zijn

#### Voorvertoning van tekst uitvoeren {#how-to-perform-text-pre-extraction}

>[!NOTE]
>
>***De hieronder beschreven opdrachten voor eak-run.jar worden volledig opgesomd bij [https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html)***
>
>Het bovenstaande diagram en de onderstaande stappen dienen als toelichting en aanvulling op de technische tekstvoorbereidingsstappen die in de Apache Oak-documentatie worden beschreven.

![Tekstomloop voorafgaand aan extractie](assets/chlimage_1-139.png)

**Lijst met vooraf te extraheren inhoud genereren**

*Voer stap 1(a-b) uit tijdens een onderhoudsvenster/periode voor weinig gebruik wanneer de Node Store tijdens deze bewerking wordt doorlopen, wat een aanzienlijke belasting van het systeem kan veroorzaken.*

1 bis. Uitvoeren `oak-run.jar --generate` om een lijst met knooppunten te maken waarvan de tekst vooraf wordt uitgepakt.

1 ter. Lijst met knooppunten (1a) wordt als CSV-bestand opgeslagen in het bestandssysteem

De hele Node Store wordt elke keer doorlopen (zoals opgegeven door de paden in de opdracht eikenuitvoering) `--generate` wordt uitgevoerd en een **new** CSV-bestand wordt gemaakt. Het CSV-bestand is **niet** hergebruikt tussen discrete uitvoeringen van het tekstvoorbehandelingsproces (stappen 1 - 2).

**Tekst vooraf uitpakken naar bestandssysteem**

*Stap 2 (a-c) kan tijdens normale verrichting van AEM worden uitgevoerd is het slechts met de Opslag van Gegevens in wisselwerking staat.*

2 bis. Uitvoeren `oak-run.jar --tika` om tekst voor de binaire knopen vooraf te halen die in het CSV- dossier worden opgesomd in (1b) wordt geproduceerd

2 ter. Het proces dat in (2a) wordt in werking gesteld heeft toegang tot binaire knopen die in CSV in de Opslag van Gegevens worden bepaald direct, en haalt tekst uit.

2 quater. Geëxtraheerde tekst wordt in het bestandssysteem opgeslagen in een indeling die instelbaar is door het omschakelingsproces van de eik (3a)

De vooraf geëxtraheerde tekst wordt in de CSV geïdentificeerd door de binaire vingerafdruk. Als het binaire bestand hetzelfde is, kan dezelfde vooraf geëxtraheerde tekst worden gebruikt in AEM instanties. Aangezien AEM Publiceren doorgaans een subset van AEM Auteur is, kan de vooraf geëxtraheerde tekst van AEM Auteur vaak ook worden gebruikt om de publicatie opnieuw te AEM (ervan uitgaande dat de AEM Publiceren bestandssysteemtoegang heeft tot de geëxtraheerde tekstbestanden).

Aan vooraf geëxtraheerde tekst kan stapsgewijs worden toegevoegd. De voorextractie van tekst slaat de extractie van eerder geëxtraheerde binaire bestanden over. Het is daarom aan te raden om vooraf geëxtraheerde tekst te behouden voor het geval dat in de toekomst opnieuw tekst moet worden geëxtraheerd (ervan uitgaande dat de geëxtraheerde inhoud niet prohibitief groot is). Als dit het geval is, evalueert het Zijden van de inhoud in het tussentijdse stadium, aangezien de tekst goed samenperst).

**Indexen van eikenhout opnieuw indexeren, volledige tekst betrekken uit geëxtraheerde tekstbestanden**

*Herindexering uitvoeren (stappen 3a-b) tijdens een onderhouds-/gebruiksduur wanneer de Node Store tijdens deze operatie wordt doorgespoeld, wat een aanzienlijke belasting voor het systeem kan veroorzaken.*

3 bis. [Opnieuw indexeren](#how-to-re-index) van Lucene-indexen wordt in AEM aangeroepen.

3 ter. De Apache Jackrabbit Oak DataStore PreExtractedTextProvider OSGi config (geconfigureerd om te wijzen naar de uitgenomen tekst via een bestandssysteempad) geeft Oak de opdracht om volledige tekst uit de geëxtraheerde bestanden te betrekken en vermijdt rechtstreeks het bewerken en bewerken van de gegevens die in de opslagplaats zijn opgeslagen.
