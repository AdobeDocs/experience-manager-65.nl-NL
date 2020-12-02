---
title: Beste praktijken voor Vragen en het Indexeren
seo-title: Beste praktijken voor Vragen en het Indexeren
description: Dit artikel bevat richtlijnen voor het optimaliseren van indexen en query's.
seo-description: Dit artikel bevat richtlijnen voor het optimaliseren van indexen en query's.
uuid: 0609935a-4a72-4b8e-a28e-daede9fc05f4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 3f06f7a1-bdf0-4700-8a7f-1d73151893ba
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d
workflow-type: tm+mt
source-wordcount: '4618'
ht-degree: 0%

---


# Beste praktijken voor Vragen en het Indexeren{#best-practices-for-queries-and-indexing}

Samen met de overgang aan Eak in AEM 6, werden sommige belangrijke veranderingen aangebracht in de manier dat de vragen en de indexen worden beheerd. Onder Jasje 2 is alle inhoud standaard geïndexeerd en kan deze vrij worden opgevraagd. In eiken moeten indexen handmatig worden gemaakt onder het knooppunt `oak:index`. Een vraag kan zonder een index worden uitgevoerd, maar voor grote datasets, zal het zeer langzaam uitvoeren, of zelfs afbreken.

Dit artikel zal schetsen wanneer om indexen tot stand te brengen evenals wanneer zij niet nodig zijn, trucs vermijden gebruikend vragen wanneer zij niet noodzakelijk zijn, en uiteinden voor het optimaliseren van uw indexen en vragen om zo optimaal mogelijk te presteren.

Bovendien, zorg ervoor om de [documentatie van het Eik over het schrijven van vragen en indexen](/help/sites-deploying/queries-and-indexing.md) te lezen. Naast indexen die een nieuw concept in AEM 6 zijn, zijn er syntactische verschillen in vragen van het Eak die in overweging moeten worden genomen wanneer het migreren van code van een vorige AEM installatie.

## Wanneer moet u query&#39;s {#when-to-use-queries} gebruiken?

### Ontwerp opslagplaats en taxonomie {#repository-and-taxonomy-design}

Bij het ontwerpen van de taxonomie van een gegevensopslagruimte moeten verschillende factoren in aanmerking worden genomen. Dit zijn onder andere toegangsbeheer, lokalisatie, component- en pagina-eigenschapovererving.

Terwijl het ontwerpen van een taxonomie die deze zorgen richt, is het ook belangrijk om de &quot;draagbaarheid&quot;van het indexeren ontwerp te overwegen. In deze context is de verhandelbaarheid de mogelijkheid van een taxonomie die het mogelijk maakt inhoud voorspelbaar toegankelijk te maken op basis van het pad ervan. Dit zal voor een krachtiger systeem maken dat gemakkelijker is te handhaven dan één die veel uit te voeren vragen zal vereisen.

Bovendien, wanneer het ontwerpen van een taxonomie, is het belangrijk om te overwegen of het opdracht geven belangrijk is. Wanneer expliciete volgorde niet vereist is en een groot aantal knooppunten op hetzelfde niveau wordt verwacht, wordt de voorkeur gegeven aan het gebruik van een ongeordend knooppunttype zoals `sling:Folder` of `oak:Unstructured`. In gevallen waarin volgorde vereist is, zouden `nt:unstructured` en `sling:OrderedFolder` geschikter zijn.

### Vragen in componenten {#queries-in-components}

Aangezien de vragen één van de meer het belasten verrichtingen op een AEM systeem kunnen zijn, is het een goed idee om hen in uw componenten te vermijden. Als u meerdere query&#39;s hebt uitgevoerd telkens wanneer een pagina wordt gerenderd, kan dit vaak de prestaties van het systeem nadelig beïnvloeden. Er zijn twee strategieën die kunnen worden gebruikt om het uitvoeren van query&#39;s bij het renderen van componenten te voorkomen: **het doorlopen van knooppunten** en **het vooraf instellen van resultaten**.

#### Bezig met doorlopen knooppunten {#traversing-nodes}

Als de gegevensopslagplaats op een dergelijke manier wordt ontworpen dat vroegere kennis van de plaats van de vereiste gegevens toestaat, kan de code die deze gegevens van de noodzakelijke wegen terugwint worden opgesteld zonder het moeten vragen in werking stellen om het te vinden.

Een voorbeeld hiervan is het renderen van inhoud die binnen een bepaalde categorie past. Een manier is om de inhoud te ordenen met een categorie-eigenschap die kan worden gevraagd om een component te vullen die items in een categorie weergeeft.

Een betere benadering zou zijn om deze inhoud in een taxonomie door categorie te structureren zodat het manueel kan worden teruggewonnen.

Als de inhoud bijvoorbeeld wordt opgeslagen in een taxonomie die lijkt op:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

de `/content/myUnstructuredContent/parentCategory/childCategory` knoop kan eenvoudig worden teruggewonnen, zijn kinderen kunnen worden ontleed en worden gebruikt om de component terug te geven.

Bovendien, wanneer u met een kleine of homogene resultaatreeks te maken hebt, kan het sneller zijn om de bewaarplaats over te steken en de vereiste knopen te verzamelen, eerder dan het ontwerpen van een vraag om de zelfde resultaatreeks terug te keren. In het algemeen moeten vragen worden vermeden wanneer dat mogelijk is.

#### Resultaten vooraf instellen {#prefetching-results}

Soms staan de inhoud of de vereisten rond de component het gebruik van knoopverkeer als methode om de vereiste gegevens terug te winnen niet toe. In deze gevallen, moeten de vereiste vragen worden uitgevoerd alvorens de component wordt teruggegeven zodat de optimale prestaties voor het eind - gebruiker wordt gewaarborgd.

Als de resultaten die voor de component worden vereist op het ogenblik kunnen worden berekend dat het wordt geschreven en er geen verwachting is dat de inhoud zal veranderen, kan de vraag worden uitgevoerd wanneer de auteur montages in de dialoog toepast.

Als de gegevens of de inhoud regelmatig zullen veranderen, kan de vraag op een programma of via een luisteraar voor updates aan de onderliggende gegevens worden uitgevoerd. Vervolgens kunnen de resultaten naar een gedeelde locatie in de opslagplaats worden geschreven. Om het even welke componenten die deze gegevens nodig hebben kunnen dan de waarden van deze enige knoop trekken zonder het moeten een vraag bij runtime uitvoeren.

## Zoekoptimalisatie {#query-optimization}

Wanneer het runnen van een vraag die geen index gebruikt, zullen de waarschuwingen betreffende knoop traversal worden geregistreerd. Als dit een vraag is die vaak zal worden in werking gesteld, zou een index moeten worden gecreeerd. Om te bepalen welke index een bepaalde vraag gebruikt, [wordt het hulpmiddel van de Vraag ](/help/sites-administering/operations-dashboard.md#explain-query) geadviseerd om te verklaren. Voor extra informatie, kan het registreren van de FOUTOPSPORING voor de relevante onderzoek APIs worden toegelaten.

>[!NOTE]
>
>Nadat u een indexdefinitie hebt gewijzigd, moet de index opnieuw worden samengesteld (opnieuw worden gedesdexeerd). Afhankelijk van de grootte van de index kan het enige tijd duren om deze te voltooien.

Wanneer het runnen van complexe vragen, kunnen er gevallen zijn waarin het onderbreken van de vraag in veelvoudige kleinere vragen en het aansluiten van de gegevens door code nadat het feit krachtiger is. De aanbeveling voor deze gevallen is om de prestaties van de twee benaderingen te vergelijken om te bepalen welke optie beter zou zijn voor het betrokken gebruiksgeval.

AEM staat het schrijven van vragen op één van drie manieren toe:

* Via de [QueryBuilder-API&#39;s](/help/sites-developing/querybuilder-api.md) (aanbevolen)
* XPath gebruiken (aanbevolen)
* SQL2 gebruiken

Terwijl alle vragen in SQL2 alvorens worden in werking gesteld worden omgezet, is de overheadkosten van vraagomzetting minimaal en zo, zal de grootste zorg wanneer het kiezen van een vraagtaal leesbaarheid en comfortniveau van het ontwikkelingsteam zijn.

>[!NOTE]
>
>Wanneer het gebruiken van QueryBuilder, zal het de resultaattelling door gebrek bepalen, die in Oak langzamer is dan vorige versies van Jackrabbit. Om dit te compenseren, kunt u [radenTotal parameter](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results) gebruiken.

### Het gereedschap Query uitvoeren {#the-explain-query-tool}

Zoals met om het even welke vraagtaal, moet de eerste stap aan het optimaliseren van een vraag begrijpen hoe het zal worden uitgevoerd. Om deze activiteit toe te laten, kunt u [het hulpmiddel van de Vraag ](/help/sites-administering/operations-dashboard.md#explain-query) gebruiken die deel van het Dashboard van Verrichtingen uitmaakt. Met dit hulpmiddel, kan een vraag binnen worden gestopt en worden verklaard. Een waarschuwing zal worden getoond als de vraag kwesties met een grote bewaarplaats evenals uitvoeringstijd en de indexen zal veroorzaken die zullen worden gebruikt. Het gereedschap kan ook een lijst met trage en populaire query&#39;s laden die vervolgens kunnen worden uitgelegd en geoptimaliseerd.

### FOUTOPSPORING VOOR VRAGEN {#debug-logging-for-queries}

Om wat extra informatie over te krijgen hoe Eak kiest welke te gebruiken index en hoe de vraagmotor eigenlijk een vraag uitvoert, kan een **DEBUG** registrerenconfiguratie voor de volgende pakketten worden toegevoegd:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

Zorg ervoor om dit registreerapparaat te verwijderen wanneer u het zuiveren van uw vraag hebt gebeëindigd aangezien het veel activiteit zal uitvoeren en uw schijf met logboekdossiers uiteindelijk kan vullen.

Raadpleeg de [Logboekdocumentatie](/help/sites-deploying/configure-logging.md) voor meer informatie over hoe u dit kunt doen.

### Indexstatistieken {#index-statistics}

Lucene registreert een boon JMX die details over geïndexeerde inhoud met inbegrip van de grootte en het aantal documenten in elk van de indexen zal verstrekken.

U kunt het bereiken door tot de Console van JMX bij `https://server:port/system/console/jmx` toegang te hebben

Zodra u aan de console JMX wordt het programma geopend, voer een onderzoek naar **Statistieken van de Index van Lucene** uit om het te vinden. Andere indexstatistieken kunnen in **IndexStats** MBean worden gevonden.

Voor vraagstatistieken, neem een blik bij MBean genoemd **de Statistieken van de Vraag van het Eak**.

Als u in uw indexen zou willen graven gebruikend een hulpmiddel zoals [Luke](https://code.google.com/p/luke/), zult u de console van het Eak moeten gebruiken om de index van `NodeStore` aan een folder van het filesystem te dumpen. Lees de [Lucene-documentatie](https://jackrabbit.apache.org/oak/docs/query/lucene.html) voor instructies over hoe u dit doet.

U kunt de indexen in uw systeem ook in JSON-indeling extraheren. Hiervoor hebt u toegang nodig tot `https://server:port/oak:index.tidy.-1.json`

### Zoeklimieten {#query-limits}

**Tijdens de ontwikkeling**

Lage drempelwaarden instellen voor `oak.queryLimitInMemory` (bijv. 10000) en eiken. `queryLimitReads` (bijv. 5000) en optimaliseer de dure vraag wanneer het raken van een UnsupportedOperationException die &quot;de vraag leest meer dan x knopen...&quot; zegt

Dit helpt middelintensieve vragen (d.w.z. te vermijden. niet ondersteund door een index of ondersteund door minder dekkende index). Bijvoorbeeld, zou een vraag die 1 miljoen knopen leest tot verhoogde I/O leiden, en negatief de algemene toepassingsprestaties beïnvloeden. Elke query die vanwege bovenstaande limieten mislukt, moet worden geanalyseerd en geoptimaliseerd.

#### **Na de implementatie** {#post-deployment}

* Controleer de logboeken voor vragen die de grote knoop traversal of grote het geheugenconsumptie van de heap veroorzaken: &quot;

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * De query optimaliseren om het aantal doorgelopen knooppunten te verminderen

* Controleer de logboeken voor vragen die het grote gebruik van het heapgeheugen teweegbrengen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimaliseer de vraag om het gebruik van het heapgeheugen te verminderen

Voor AEM 6.0 - 6.2 versies, kunt u de drempel voor knoopsverplaatsing via parameters JVM in het AEM startmanuscript aanpassen om grote vragen te verhinderen het milieu te overbelasten.

De aanbevolen waarden zijn:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3, zijn bovengenoemde 2 parameters preconfigured OOTB, en kunnen via OSGi QueryEngineSettings worden voortgeduurd.

Meer informatie is beschikbaar onder: [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Tips voor het maken van efficiënte indexen {#tips-for-creating-efficient-indexes}

### Moet ik een index maken? {#should-i-create-an-index}

De eerste vraag die u moet stellen bij het maken of optimaliseren van indexen is of ze echt nodig zijn voor een bepaalde situatie. Als u de vraag in kwestie slechts één of slechts af en toe en bij een off-piek tijd voor het systeem door een partijproces gaat in werking stellen, kan het beter zijn om geen index bij allen tot stand te brengen.

Nadat u een index hebt gemaakt, moet de index ook worden bijgewerkt telkens wanneer de geïndexeerde gegevens worden bijgewerkt. Aangezien dit prestatiesimplicaties voor het systeem draagt, zouden de indexen slechts moeten worden gecreeerd wanneer zij eigenlijk worden vereist.

Bovendien zijn indexen alleen nuttig als de gegevens in de index uniek genoeg zijn om ze te rechtvaardigen. Overweeg een index in een boek en de onderwerpen die het behandelt. Wanneer het indexeren van een reeks onderwerpen in een tekst, gewoonlijk zullen er honderden of duizenden ingangen zijn, die u toestaan om aan een ondergroep van pagina&#39;s snel te springen om de informatie snel te vinden die u zoekt. Als die index slechts twee of drie items bevat, die elk naar honderden pagina&#39;s verwijzen, is de index niet erg nuttig. Hetzelfde concept geldt voor database-indexen. Als er slechts een paar unieke waarden zijn, zal de index niet erg nuttig zijn. Een index kan echter ook te groot worden om nuttig te zijn. Om indexstatistieken te bekijken, zie [Indexstatistieken](/help/sites-deploying/best-practices-for-queries-and-indexing.md#index-statistics) hierboven.

### Luidens- of eigenschapsindexen? {#lucene-or-property-indexes}

Lucene-indexen werden geïntroduceerd in Oak 1.0.9 en bieden krachtige optimalisaties voor de eigenschapsindexen die werden geïntroduceerd bij de eerste introductie van AEM 6. Wanneer u besluit of u Lucene-indexen of eigenschapsindexen wilt gebruiken, moet u rekening houden met het volgende:

* Lucene-indexen bieden veel meer functies dan eigenschapindexen. Een eigenschapindex kan bijvoorbeeld slechts één eigenschap indexeren, terwijl een Lucene-index er veel kan bevatten. Raadpleeg de [documentatie](https://jackrabbit.apache.org/oak/docs/query/lucene.html) voor meer informatie over alle functies die beschikbaar zijn in Lucene-indexen.
* Lucene-indexen zijn asynchroon. Hoewel dit een aanzienlijke prestatieverhoging biedt, kan het ook een vertraging veroorzaken tussen wanneer gegevens naar de gegevensopslagplaats worden geschreven en wanneer de index wordt bijgewerkt. Als het essentieel is om vragen te hebben 100% nauwkeurige resultaten terugkeren, zou een bezitsindex worden vereist.
* Door asynchroon te zijn, kunnen de indexen van Lucene geen uniciteitsbeperkingen afdwingen. Als dit wordt vereist, dan zal een bezitsindex op zijn plaats moeten worden gebracht.

In het algemeen, wordt het geadviseerd u de indexen van Lucene tenzij er een dwingende behoefte is om bezitsindexen te gebruiken zodat u de voordelen van hogere prestaties en flexibiliteit kunt bereiken.

### Solr-indexering {#solr-indexing}

AEM biedt standaard ook ondersteuning voor Solr-indexering. Dit wordt hoofdzakelijk gebruikt om volledige tekstonderzoek te steunen, maar het kan ook worden gebruikt om om het even welk type van vraag te steunen JCR. Solr zou moeten worden overwogen wanneer de AEM instanties niet de capaciteit van cpu hebben om het aantal vragen te behandelen die in onderzoek intensieve plaatsingen zoals onderzoek gedreven websites met een hoog aantal gezamenlijke gebruikers worden vereist. Ook, kan Solr in een op crawler gebaseerde benadering worden uitgevoerd om sommige van de geavanceerdere eigenschappen van het platform te gebruiken.

Solr indexen kunnen worden gevormd om ingebed op de AEM server voor ontwikkelingsmilieu&#39;s in werking te stellen of aan een verre instantie kunnen worden geoffload om onderzoeksscalability op de productie en het opvoeren milieu&#39;s te verbeteren. Hoewel het offloaden van onderzoek scalability zal verbeteren, zal het latentie introduceren en daarom, wordt niet geadviseerd tenzij vereist. Voor meer informatie over hoe te om de integratie van Solr te vormen en hoe te om de indexen van Solr tot stand te brengen zie [Oak- Vragen en het Indexeren documentatie](/help/sites-deploying/queries-and-indexing.md#the-solr-index).

>[!NOTE]
>
>Terwijl het nemen van de geïntegreerde Solr onderzoeksbenadering zou voor het ontladen van indexeren aan een Solr server toestaan. Als de geavanceerdere eigenschappen van de server van Solr door een kruipende gebaseerde benadering worden gebruikt, zal het extra configuratiewerk worden vereist. Headwire heeft een [open bronschakelaar](https://www.aemsolrsearch.com/#/) gecreeerd om deze types van implementaties te versnellen.

Het nadeel aan het nemen van deze benadering is dat terwijl door gebrek, AEM vragen ACLs zullen respecteren en zo resultaten verbergen die een gebruiker geen toegang tot heeft, het externaliseren van onderzoek aan een Solr server zal niet deze eigenschap steunen. Als de zoekactie op deze manier extern moet worden uitgevoerd, moet er extra op worden gelet dat de gebruikers geen resultaten krijgen die ze niet zouden moeten zien.

Mogelijke gebruiksgevallen waarin deze aanpak passend kan zijn, zijn gevallen waarin zoekgegevens uit meerdere bronnen moeten worden samengevoegd. U hebt bijvoorbeeld een site die wordt gehost op AEM en een tweede site die wordt gehost op een extern platform. Solr zou kunnen worden gevormd om de inhoud van beide plaatsen te kruipen en hen op te slaan in een bijeengevoegde index. Op die manier kunnen zoekopdrachten naar andere sites worden uitgevoerd.

### Ontwerpoverwegingen {#design-considerations}

De documentatie van het Eak voor indexen van de Luik maakt een lijst van verscheidene overwegingen om te maken wanneer het ontwerpen van indexen:

* Als de vraag verschillende wegbeperkingen gebruikt, gebruik `evaluatePathRestrictions`. Hierdoor kan de query de subset van resultaten retourneren onder het opgegeven pad en deze vervolgens filteren op basis van de query. Anders, zal de vraag naar alle resultaten zoeken die de vraagparameters in de bewaarplaats aanpassen en dan hen filtreren die op de weg worden gebaseerd.
* Als de vraag het sorteren gebruikt, heb een expliciete bezitsdefinitie voor het gesorteerde bezit en reeks `ordered` aan `true` voor het. Hierdoor kunnen de resultaten als zodanig worden geordend in de index en worden kostbare sorteerbewerkingen tijdens de uitvoering van de query opgeslagen.

* Plaats alleen wat nodig is in de index. Als u overbodige functies of eigenschappen toevoegt, neemt de index toe en vertraagt de prestaties.
* In een bezitsindex, zou het hebben van een unieke bezitsnaam helpen de grootte op een index verminderen, maar voor indexen van Lucene, zou het gebruik van `nodeTypes` en `mixins` moeten worden gemaakt om samenhangende indexen te bereiken. Het opvragen van een specifieke `nodeType` of `mixin` zal uitvoeriger zijn dan het opvragen van `nt:base`. Wanneer u deze methode gebruikt, definieert u `indexRules` voor de `nodeTypes` in kwestie.

* Als uw vragen slechts onder bepaalde wegen worden in werking gesteld, dan creeer die indexen onder die wegen. Indexen hoeven niet in de hoofdmap van de opslagplaats te wonen.
* Men adviseert om één enkele index te gebruiken wanneer alle eigenschappen die worden geïndexeerd verwant zijn om Lucene toe te staan om zo vele bezitsbeperkingen te evalueren mogelijk native. Bovendien, zal een vraag slechts één index gebruiken, zelfs wanneer het uitvoeren van zich aansluiten.

### CopyOnRead {#copyonread}

In gevallen waarin `NodeStore` ver wordt opgeslagen, kan een optie genoemd `CopyOnRead` worden toegelaten. De optie zorgt ervoor dat de externe index naar het lokale bestandssysteem wordt geschreven wanneer deze wordt gelezen. Dit kan helpen prestaties voor vragen verbeteren die vaak tegen deze verre indexen in werking worden gesteld.

Dit kan in de console OSGi onder de **dienst worden gevormd LuceneIndexProvider** en door gebrek met ingang van Oak 1.0.13 toegelaten.

### Indexen {#removing-indexes} verwijderen

Wanneer het verwijderen van een index, wordt het altijd geadviseerd om de index tijdelijk onbruikbaar te maken door het `type` bezit aan `disabled` te plaatsen en het testen te doen om ervoor te zorgen dat uw toepassing correct functioneert alvorens het eigenlijk te schrappen. Een index wordt niet bijgewerkt terwijl deze is uitgeschakeld, zodat deze mogelijk niet de juiste inhoud heeft als deze opnieuw wordt ingeschakeld en opnieuw moet worden gedesdeerd.

Nadat een bezitsindex op een instantie TarMK wordt verwijderd, zal de compensatie moeten in werking worden gesteld om het even welke schijfruimte terug te winnen die in gebruik was. Voor indexen van Lucene, leeft de daadwerkelijke indexinhoud in BlobStore, zodat zou een inzameling van het huisvuil van de gegevensopslag worden vereist.

Wanneer u een index op een MongoDB-instantie verwijdert, zijn de verwijderingskosten evenredig met het aantal knooppunten in de index. Aangezien het schrappen van een grote index problemen kan veroorzaken, is de geadviseerde benadering de index onbruikbaar te maken en het slechts tijdens een onderhoudsvenster te schrappen, gebruikend een hulpmiddel zoals **eak-mongo.js**. Houd er rekening mee dat deze aanpak niet moet worden gebruikt voor inhoud van gewone knooppunten, omdat dit leidt tot inconsistenties in de gegevens.

>[!NOTE]
>
>Raadpleeg de sectie [Opdrachtregelgereedschappen](https://jackrabbit.apache.org/oak/docs/command_line.html) van de documentatie bij Eak voor meer informatie over eak-mongo.js.

## {#re-indexing} opnieuw indexeren

Deze sectie schetst **only** aanvaardbare redenen om indexen van het Eak opnieuw te indexeren.

Buiten de hieronder geschetste redenen, zal het in werking stellen van re-indexen van eik indexen **niet** gedrag veranderen of kwesties oplossen, en onnodig lading op AEM verhogen.

Herindexering van de eiken-indexen moet worden vermeden, tenzij in onderstaande tabellen een motivering wordt gegeven.

>[!NOTE]
>
>Voordat u de onderstaande tabellen raadpleegt om te bepalen of indexering opnieuw moet worden toegepast, is** altijd **controleren:
>
>* de vraag correct is
>* de vraag lost aan de verwachte index op (gebruikend [verklaar Vraag](/help/sites-administering/operations-dashboard.md#diagnosis-tools))
>* het indexeringsproces is voltooid

>



### Wijzigingen in indexconfiguratie van ongewenste indexen {#oak-index-configuration-changes}

De enige aanvaardbare voorwaarden voor het opnieuw indexeren van eiken-indexen zijn als de configuratie van een eiken-index is gewijzigd.

*Herindexering moet altijd met de nodige aandacht worden benaderd voor het effect ervan op AEM algehele prestaties en moet worden uitgevoerd tijdens perioden van lage activiteit of onderhoudsvensters.*

De volgende details en resoluties zijn mogelijk:

* [Wijziging van indexdefinitie van eigenschap](#property-index-definition-change)
* [Wijziging van de definitie van Lucene-index](#lucene-index-definition-change)

#### Wijziging van indexdefinitie van eigenschap {#property-index-definition-change}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [eigenschapindexen](https://jackrabbit.apache.org/oak/docs/query/property-index.html)

* Symptomen:

   * Nodes existing before to property index&#39;s definition update missing from results

* Hoe te om te verifiëren:

   * Bepaal of er ontbrekende knooppunten zijn gemaakt/gewijzigd vóór de implementatie van de bijgewerkte indexdefinitie.
   * Verifieer `jcr:created` of `jcr:lastModified` eigenschappen van om het even welke ontbrekende knopen tegen de gewijzigde tijd van de index

* Hoe oplossen:

   * [De lucene-index opnieuw ](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-re-index) indexeren
   * U kunt ook op de ontbrekende knooppunten tikken (een goedaardige schrijfbewerking uitvoeren)

      * Vereist handmatige aanrakingen of aangepaste code
      * De set ontbrekende knooppunten moet bekend zijn
      * Vereist het veranderen van om het even welke bezit op de knoop

#### Wijziging van de definitie van de Lucentisindex {#lucene-index-definition-change}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [lucene-indexen](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten
   * De zoekresultaten weerspiegelen niet het verwachte gedrag van de indexdefinitie
   * Het plan van de vraag rapporteert geen verwachte output die op indexdefinitie wordt gebaseerd

* Hoe te om te verifiëren:

   * Verifieer de indexdefinitie werd veranderd gebruikend de statistieken van de Index van Lucene JMX Mbean (LuceneIndex), methode `diffStoredIndexDefinition`.

* Hoe oplossen:

   * Oak-versies vóór 1.6:

      * [De lucene-index opnieuw ](#how-to-re-index) indexeren
   * Oak-versies 1.6+

      * Als bestaande inhoud niet door de wijzigingen wordt gewijzigd, hoeft u alleen de inhoud te vernieuwen

         * [De lucene-index ](https://jackrabbit.apache.org/oak/docs/query/lucene.html#stored-index-definition) vernieuwen door een  [fout in te stellen:queryIndexDefinition]@refresh=true
      * Anders, [re-index](#how-to-re-index) de luceenindex

         * Opmerking: De indexstaat van het laatste goede re-indexeren (of aanvankelijke indexeren) zal worden gebruikt tot een nieuwe re-indexering wordt teweeggebracht



### Erkende en uitzonderlijke situaties {#erring-and-exceptional-situations}

In de volgende tabel worden de enige aanvaardbare fouten en uitzonderlijke situaties beschreven waarin het opnieuw indexeren van eiken-indexen het probleem zal oplossen.

Als er een probleem optreedt bij AEM die niet aan de onderstaande criteria voldoen, kunt u **geen indexen opnieuw indexeren, omdat dit het probleem niet verhelpt.**

De volgende details en resoluties zijn mogelijk:

* [Binair Lucene-indexbestand ontbreekt](#lucene-index-binary-is-missing)
* [Binair Lucene-index is beschadigd](#lucene-index-binary-is-corrupt)

#### Binair bestand Lucene-index ontbreekt {#lucene-index-binary-is-missing}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [lucene-indexen](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten

* Hoe te om te verifiëren:

   * Het dossier van het foutenlogboek bevat een uitzondering die een binair getal van de index van Lucene zegt mist

* Hoe oplossen:

   * een doorlopende controle van de gegevensopslagplaats uitvoeren; bijvoorbeeld:

      [http://localhost:4502/system/console/repositorycheck](http://localhost:4502/system/console/repositorycheck)

      het doorlopen van de gegevensopslagruimte bepaalt of andere binaire bestanden (behalve lucene-bestanden) ontbreken

   * Als binaire getallen anders dan lucene-indexen ontbreken, kunt u terugzetten vanaf een back-up
   * Anders [re-index](#how-to-re-index) *all* lucene-indexen
   * Opmerking:

      Deze voorwaarde is indicatief van een misconfigured datastore die in OM HET EVEN WELK binair getal (bijvoorbeeld kan resulteren. binaire elementen) om te ontbreken.

      In dit geval herstelt u de laatst bekende goede versie van de opslagplaats om alle ontbrekende binaire bestanden te herstellen.

#### Binair Lucene-indexbestand is beschadigd {#lucene-index-binary-is-corrupt}

* Is van toepassing op/if:

   * Alle eiken versies
   * Alleen [lucene-indexen](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten

* Hoe te om te verifiëren:

   * `AsyncIndexUpdate` (om de 5s) zal met een uitzondering in error.log ontbreken:

      `...a Lucene index file is corrupt...`

* Hoe oplossen:

   * Verwijder de lokale kopie van de index van de lucene

      1. AEM stoppen
      1. Verwijder de lokale kopie van de lucene-index op `crx-quickstart/repository/index`
      1. AEM opnieuw starten
   * Als dit de kwestie niet oplost, en de `AsyncIndexUpdate` uitzonderingen blijven dan bestaan:

      1. [De foutindex opnieuw ](#how-to-re-index) indexeren
      1. Ook een [Adobe Support](https://helpx.adobe.com/support.html)-ticket indienen


### {#how-to-re-index} opnieuw indexeren

>[!NOTE]
>
>In AEM 6.5 is [eak-run.jar de ENIGE ondersteunde methode](/help/sites-deploying/indexing-via-the-oak-run-jar.md#reindexingapproachdecisiontree) voor het opnieuw indexeren op MongoMK- of RDBMK-repositories.

#### Eigenschapindexen opnieuw indexeren {#re-indexing-property-indexes}

* Gebruik [eak-run.jar](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) om de index van de eigenschap opnieuw te indexeren
* De eigenschap async-redex instellen op true op de index van de eigenschap

   * `[oak:queryIndexDefinition]@reindex-async=true`

* Wijzig de index van de eigenschap asynchroon met de webconsole via **PropertyIndexAsyncReindex** MBean.

   bijvoorbeeld:

   [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex)

#### De indexen van het Bezit van Lucene {#re-indexing-lucene-property-indexes} opnieuw indexeren

* Gebruik [eak-run.jar aan re-index](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) de index van het Bezit van Lucene.
* Stel de eigenschap async-redex in op true op de index van de eigenschap lucene

   * `[oak:queryIndexDefinition]@reindex-async=true`

>[!NOTE]
>
>In de voorgaande sectie wordt een overzicht gegeven van de aanwijzingen voor het opnieuw indexeren van de eiken in de [Apache Oak-documentatie](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) in de context van AEM.

### Tekstomloop van binaire tekens {#text-pre-extraction-of-binaries}

De preextractie van de tekst is het proces om tekst uit binaire getallen, direct uit de Opslag van Gegevens via een geïsoleerd proces, te halen en te verwerken, en direct blootstellend de gehaalde tekst aan verdere re/indexeringen van Eak indexen.

* Het vooraf uitpakken van eikentekst wordt aanbevolen voor het opnieuw/indexeren van Lucene-indexen in opslagruimten met grote volumes bestanden (binaire bestanden) die extraheerbare tekst bevatten (bijvoorbeeld PDF&#39;s, Word Docs, PPT&#39;s, TXT, enz.) die in aanmerking komen voor full-text onderzoek via geïmplementeerde eiken-indexen; bijvoorbeeld `/oak:index/damAssetLucene`.
* De pre-extractie van de tekst zal slechts het re/indexeren van indexen Lucene, en NIET de bezitsindexen van het Eak ten goede komen, aangezien de bezitsindexen geen tekst uit binaire getallen halen.
* De preextractie van tekst heeft een groot positief effect wanneer het volledig-tekst re-indexeren van tekst-zware binaire getallen (PDF, Doc, TXT, enz.), waar als bewaarplaats van beelden niet de zelfde efficiency zal genieten aangezien de beelden geen extractable tekst bevatten.
* Bij het vooraf extraheren van tekst wordt tekst die betrekking heeft op zoeken in volledige tekst op een extra efficiënte manier geëxtraheerd en wordt de tekst op een extra efficiënte manier aan het opnieuw/indexeren van de eik blootgesteld, zodat de tekst extra efficiënt kan worden geconsumeerd.

#### Wanneer kan de tekstvoorextractie worden gebruikt? {#when-can-text-pre-extraction-be-used}

Het opnieuw indexeren van een **bestaande** luceenindex met binaire toegelaten extractie

* Verwerking opnieuw indexeren **alle** kandidaatinhoud in de opslagplaats; wanneer de binaire getallen waaruit volledige tekst kan worden geëxtraheerd talrijk of complex zijn, wordt een grotere rekenlast voor het extraheren van volledige tekst op AEM geplaatst. De pre-extractie van de tekst beweegt het &quot;computer dure werk&quot;van tekst-extractie in een geïsoleerd proces dat tot AEM Opslag van Gegevens direct toegang heeft, vermijdend overheadkosten en middelgeschil in AEM.

Ondersteuning voor de implementatie van een **new**-luceenindex om te AEM met binaire extractie ingeschakeld

* Wanneer een nieuwe index (met binaire toegelaten extractie) in AEM wordt opgesteld, indexeert het Eak automatisch alle kandidaatinhoud op de volgende async full-text indexlooppas. Om dezelfde redenen die hierboven bij het opnieuw indexeren worden beschreven, kan dit leiden tot een te grote belasting bij AEM.

#### Wanneer kan de voorextractie van tekst NIET worden gebruikt? {#when-can-text-pre-extraction-not-be-used}

Tekstomloop kan niet worden gebruikt voor nieuwe inhoud die aan de opslagplaats wordt toegevoegd, en is ook niet nodig.

Nieuwe inhoud wordt toegevoegd aan de dataopslag zal natuurlijk en incrementeel door het async full-text indexeren proces (door gebrek, om de 5 seconden) worden geïndexeerd.

Onder normale verrichting van AEM, bijvoorbeeld het uploaden van Activa via het Web UI of programmatic ingest van Activa, zal AEM automatisch en incrementeel full-text index de nieuwe binaire inhoud. Aangezien de hoeveelheid gegevens incrementeel en relatief klein is (ongeveer de hoeveelheid gegevens die in 5 seconden aan de opslagplaats kan worden gepresteerd), kan AEM de full-text extractie uit de binaire getallen uitvoeren tijdens het indexeren zonder de algemene systeemprestaties te beïnvloeden.

#### Vereisten voor het gebruik van tekstvoorextractie {#prerequisites-to-using-text-pre-extraction}

* U zult een lucene index opnieuw indexeren die full-text binaire extractie uitvoert of een nieuwe index opstelt die full-text indexbinaire indexboeken van bestaande inhoud zal uitvoeren
* De inhoud (binaire bestanden) waaruit tekst vooraf kan worden geëxtraheerd, moet zich in de opslagplaats bevinden
* Een onderhoudsvenster voor het genereren van het CSV-bestand EN voor het opnieuw indexeren van de bestanden
* Oak-versie: 1.0.18+, 1.2.3+
* [eak-run.](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)jarversion 1.7.4+
* Een bestandssysteemmap/-share om geëxtraheerde tekst op te slaan die toegankelijk is via de instantie(s) AEM indexeren

   * De OSGi-config van de preextractie van de Tekst vereist een weg van het dossiersysteem aan de gehaalde tekstdossiers, zodat moeten zij direct van de AEM instantie (lokale aandrijving of het dossier delen onderstel) toegankelijk zijn

#### Uitpakken van tekst {#how-to-perform-text-pre-extraction} uitvoeren

>[!NOTE]
>
>***De hieronder beschreven opdrachten voor eak-run.jar worden volledig opgesomd op  [https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html)***
>
>Het bovenstaande diagram en de onderstaande stappen dienen als toelichting en aanvulling op de technische tekstvoorbereidingsstappen die in de Apache Oak-documentatie worden beschreven.

![Tekstomloop voorafgaand aan extractie](assets/chlimage_1-139.png)

**Lijst met vooraf te extraheren inhoud genereren**

*Stap 1 a-b) uitvoeren tijdens een onderhoudsvenster/periode van laag gebruik wanneer de Node Store tijdens deze bewerking wordt doorgespoeld, wat een aanzienlijke belasting van het systeem kan veroorzaken.*

1 bis. `oak-run.jar --generate` uitvoeren om een lijst met knooppunten te maken waarvan de tekst vooraf wordt geëxtraheerd.

1 ter. Lijst met knooppunten (1a) wordt als CSV-bestand opgeslagen in het bestandssysteem

Merk op dat de volledige opslag van de Knoop (zoals die door de wegen in het eiken-loopbevel wordt gespecificeerd) telkens als `--generate` wordt uitgevoerd, en een **new** CSV dossier wordt gecreeerd. Het CSV-bestand wordt **niet** opnieuw gebruikt tussen discrete uitvoeringen van het tekstvoorwinningsproces (stappen 1 - 2).

**Tekst vooraf uitpakken naar bestandssysteem**

*Stap 2 (a-c) kan tijdens normale verrichting van AEM worden uitgevoerd is het slechts met de Opslag van Gegevens in wisselwerking staat.*

2 bis. `oak-run.jar --tika` uitvoeren om tekst voor de binaire knopen vooraf te halen die in het CSV- dossier worden opgesomd in (1b) wordt geproduceerd

2 ter. Het proces dat in (2a) wordt in werking gesteld heeft toegang tot binaire knopen die in CSV in de Opslag van Gegevens worden bepaald direct, en haalt tekst uit.

2 quater.  Geëxtraheerde tekst wordt opgeslagen op een bestandssysteem in een indeling die instelbaar is door het opnieuw indexeren van de eik (3a)

De vooraf geëxtraheerde tekst wordt in de CSV geïdentificeerd door de binaire vingerafdruk. Als het binaire bestand hetzelfde is, kan dezelfde vooraf geëxtraheerde tekst worden gebruikt in AEM instanties. Aangezien AEM-publicatie doorgaans een subset van AEM-auteur is, kan de vooraf geëxtraheerde tekst van AEM-auteur vaak ook worden gebruikt om AEM-publicatie opnieuw te indexeren (ervan uitgaande dat de AEM-publicatie bestandssysteemtoegang heeft tot de geëxtraheerde tekstbestanden).

Aan vooraf geëxtraheerde tekst kan stapsgewijs worden toegevoegd. De voorextractie van tekst slaat de extractie van eerder geëxtraheerde binaire bestanden over. Het is daarom aan te raden om vooraf geëxtraheerde tekst te behouden voor het geval dat in de toekomst opnieuw indexering moet worden uitgevoerd (ervan uitgaande dat de geëxtraheerde inhoud niet prohibitief groot is). Als dit het geval is, evalueert het Zijden van de inhoud in het tussentijdse stadium, aangezien de tekst goed samenperst).

**Eak-indexen opnieuw indexeren, volledige tekst uit geëxtraheerde tekstbestanden betrekken**

*Herindexering uitvoeren (stappen 3a-b) tijdens een onderhouds-/gebruiksduur wanneer de Node Store tijdens deze bewerking wordt doorgespoten, wat een aanzienlijke belasting voor het systeem kan veroorzaken.*

3 bis. [Opnieuw ](#how-to-re-index) indexeren van Lucene-indexen wordt aangeroepen in AEM

3 ter. De Apache Jackrabbit Oak DataStore PreExtractedTextProvider OSGi config (geconfigureerd om te wijzen naar de uitgenomen tekst via een bestandssysteempad) geeft Oak de opdracht om volledige tekst uit de geëxtraheerde bestanden te betrekken en vermijdt rechtstreeks het bewerken en bewerken van de gegevens die in de opslagplaats zijn opgeslagen.

