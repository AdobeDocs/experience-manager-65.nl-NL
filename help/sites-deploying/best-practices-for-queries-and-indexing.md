---
title: Beste praktijken voor Vragen en het Indexeren
description: Dit artikel bevat richtlijnen voor het optimaliseren van indexen en query's.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 6dfaa14d-5dcf-4e89-993a-8d476a36d668
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '4520'
ht-degree: 0%

---

# Beste praktijken voor Vragen en het Indexeren{#best-practices-for-queries-and-indexing}

Samen met de overgang aan Oak in AEM 6, werden sommige belangrijke veranderingen aangebracht in de manier dat de vragen en de indexen worden beheerd. Onder Jasje 2 werd alle inhoud standaard geïndexeerd en kon er vrij om worden gevraagd. In Oak moeten indexen handmatig worden gemaakt onder het knooppunt `oak:index` . Een vraag kan zonder een index worden uitgevoerd, maar voor grote datasets, zal het langzaam lopen, of zelfs afbreken.

Dit artikel schetst wanneer om indexen tot stand te brengen en wanneer zij niet nodig zijn, trucs om het gebruiken van vragen te vermijden wanneer zij niet noodzakelijk zijn, en uiteinden voor het optimaliseren van uw indexen en vragen om zo optimaal mogelijk te presteren.

Ook, zorg ervoor om de [ documentatie van Oak te lezen bij het schrijven van vragen en indexen ](/help/sites-deploying/queries-and-indexing.md). Naast indexen die een nieuw concept in AEM 6 zijn, zijn er syntactische verschillen in de vragen van Oak die in overweging moeten worden genomen wanneer het migreren van code van een vorige AEM installatie.

## Wanneer moet u query&#39;s gebruiken? {#when-to-use-queries}

### Opslagplaats en Taxonomie-ontwerp {#repository-and-taxonomy-design}

Bij het ontwerpen van de taxonomie van een gegevensopslagruimte moeten verschillende factoren in aanmerking worden genomen. Dit zijn onder andere toegangsbeheer, lokalisatie, component en overerving van pagina-eigenschappen.

Terwijl het ontwerpen van een taxonomie die deze zorgen richt, is het ook belangrijk om de &quot;draagbaarheid&quot;van het indexeren ontwerp te overwegen. In deze context is de verhandelbaarheid de mogelijkheid van een taxonomie die het mogelijk maakt inhoud voorspelbaar toegankelijk te maken op basis van het pad ervan. Dit zal voor een krachtiger systeem maken dat gemakkelijker is te handhaven dan één die het runnen van vele vragen vereist.

Ook, wanneer het ontwerpen van een taxonomie, is het belangrijk om te overwegen of het opdracht geven belangrijk is. In gevallen waarin expliciete volgorde niet vereist is en veel knooppunten op hetzelfde niveau worden verwacht, heeft de voorkeur voor het gebruik van een niet-geordend knooppunttype zoals `sling:Folder` of `oak:Unstructured` . In gevallen waarin volgorde vereist is, zijn `nt:unstructured` en `sling:OrderedFolder` geschikter.

### Zoekopdrachten in componenten {#queries-in-components}

Omdat de vragen één van de meer het belasten verrichtingen op een AEM systeem kunnen zijn, is het een goed idee om hen in uw componenten te vermijden. Als u meerdere query&#39;s hebt uitgevoerd telkens wanneer een pagina wordt gerenderd, kan dit vaak de prestaties van het systeem nadelig beïnvloeden. Er zijn twee strategieën die kunnen worden gebruikt om het uitvoeren van vragen te vermijden wanneer het teruggeven van componenten: **het oversteken van knopen** en **het prefetching resultaten**.

#### Doorlopende knooppunten {#traversing-nodes}

Als de gegevensopslagplaats op een dergelijke manier wordt ontworpen dat vroegere kennis van de plaats van de vereiste gegevens toestaat, kan de code die deze gegevens van de noodzakelijke wegen terugwint worden opgesteld zonder het moeten vragen in werking stellen om het te vinden.

Een voorbeeld hiervan is het renderen van inhoud die binnen een bepaalde categorie past. Een manier is om de inhoud te ordenen met een categorie-eigenschap die kan worden gevraagd om een component te vullen die items in een categorie weergeeft.

Een betere benadering zou zijn om deze inhoud in een taxonomie door categorie te structureren zodat het manueel kan worden teruggewonnen.

Als de inhoud bijvoorbeeld wordt opgeslagen in een taxonomie die lijkt op:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

Het knooppunt `/content/myUnstructuredContent/parentCategory/childCategory` kan eenvoudig worden opgehaald, de onderliggende knooppunten kunnen worden geparseerd en gebruikt om de component te renderen.

Wanneer u te maken hebt met een kleine of homogene resultaatset, kan het bovendien sneller zijn om de gegevensopslagruimte te doorlopen en de vereiste knooppunten te verzamelen in plaats van een query te maken om dezelfde resultatenset te retourneren. In het algemeen moeten vragen worden vermeden wanneer dat mogelijk is.

#### Voorkeursresultaten {#prefetching-results}

Soms staan de inhoud of de vereisten rond de component het gebruik van knoopverkeer als methode om de vereiste gegevens terug te winnen niet toe. In deze gevallen, moeten de vereiste vragen worden uitgevoerd alvorens de component wordt teruggegeven zodat de optimale prestaties voor het eind - gebruiker wordt gewaarborgd.

Als de resultaten die voor de component worden vereist op het ogenblik kunnen worden berekend dat het wordt geschreven en er geen verwachting is dat de inhoud zal veranderen, kan de vraag worden uitgevoerd wanneer de auteur montages in de dialoog toepast.

Als de gegevens of de inhoud regelmatig zullen veranderen, kan de vraag op een programma of via een luisteraar voor updates aan de onderliggende gegevens worden uitgevoerd. Vervolgens kunnen de resultaten naar een gedeelde locatie in de opslagplaats worden geschreven. Om het even welke componenten die deze gegevens nodig hebben kunnen dan de waarden van deze enige knoop trekken zonder het moeten een vraag bij runtime uitvoeren.

## Zoekopdrachtoptimalisatie {#query-optimization}

Wanneer het runnen van een vraag die geen index gebruikt, worden de waarschuwingen geregistreerd betreffende knoop traversal. Als dit een vraag is die vaak zal lopen, creeer een index. Om te bepalen welke index een bepaalde vraag gebruikt, wordt het [ Uitleg hulpmiddel van de Vraag ](/help/sites-administering/operations-dashboard.md#explain-query) geadviseerd. Voor extra informatie, kan het registreren van de FOUTOPSPORING voor de relevante onderzoek APIs worden toegelaten.

>[!NOTE]
>
>Nadat u een indexdefinitie hebt gewijzigd, moet de index opnieuw worden samengesteld (opnieuw worden gedestilleerd). Afhankelijk van de grootte van de index kan het enige tijd duren om deze te voltooien.

Wanneer het runnen van complexe vragen, kunnen er gevallen zijn waarin het onderbreken van de vraag in veelvoudige kleinere vragen en het aansluiten van de gegevens door code nadat het feit krachtiger is. De aanbeveling voor deze gevallen is om de prestaties van de twee benaderingen te vergelijken om te bepalen welke optie beter zou zijn voor het betrokken gebruiksgeval.

AEM staat het schrijven van vragen op één van drie manieren toe:

* Via [ QueryBuilder APIs ](/help/sites-developing/querybuilder-api.md) (geadviseerd)
* XPath gebruiken (aanbevolen)
* SQL2 gebruiken

Terwijl alle vragen in SQL2 alvorens worden in werking gesteld worden omgezet, is de overheadkosten van vraagomzetting minimaal en zo, zal de grootste zorg wanneer het kiezen van een vraagtaal leesbaarheid en comfortniveau van het ontwikkelingsteam zijn.

>[!NOTE]
>
>Wanneer het gebruiken van QueryBuilder, bepaalt het de resultaattelling door gebrek, die in Oak langzamer is dan vorige versies van Jackrabbit. Om dit te compenseren, kunt u de [ radenTotal parameter ](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results) gebruiken.

### Het gereedschap Uitleg query {#the-explain-query-tool}

Zoals met om het even welke vraagtaal, moet de eerste stap aan het optimaliseren van een vraag begrijpen hoe het zal lopen. Om deze activiteit toe te laten, kunt u het [ Uitleg hulpmiddel van de Vraag ](/help/sites-administering/operations-dashboard.md#explain-query) gebruiken dat deel van het Dashboard van Verrichtingen uitmaakt. Met dit hulpmiddel, kan een vraag binnen worden gestopt en worden verklaard. Een waarschuwing wordt getoond als de vraag kwesties met een grote bewaarplaats en runtime en de indexen zal veroorzaken die worden gebruikt. Het gereedschap kan ook een lijst met trage en populaire query&#39;s laden die vervolgens kunnen worden uitgelegd en geoptimaliseerd.

### FOUTOPSPORING VOOR VRAGEN {#debug-logging-for-queries}

Om wat extra informatie over te krijgen hoe Oak kiest welke te gebruiken index en hoe de vraagmotor eigenlijk een vraag uitvoert, a **DEBUG** registrerenconfiguratie kan voor de volgende pakketten worden toegevoegd:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

Zorg ervoor om dit registreerapparaat te verwijderen wanneer u het zuiveren van uw vraag hebt gebeëindigd. Het neigt naar een grote hoeveelheid activiteit en kan uiteindelijk uw schijf vullen met logboekdossiers.

Voor meer informatie over hoe te om dit te doen, zie de [ het Registreren documentatie ](/help/sites-deploying/configure-logging.md).

### Indexstatistieken {#index-statistics}

Lucene registreert een boon JMX die details over geïndexeerde inhoud met inbegrip van de grootte en het aantal documenten in elk van de indexen zal verstrekken.

U kunt dit bereiken door de JMX-console te openen op `https://server:port/system/console/jmx`

Zodra u aan de console JMX wordt het programma geopend, voer een onderzoek naar **Statistieken van de Index van Lucene** uit om het te vinden. Andere indexstatistieken kunnen in **worden gevonden IndexStats** MBean.

Voor vraagstatistieken, bekijk de genoemde MBean **Statistieken van de Vraag van Oak**.

Als u in uw indexen zou willen graven gebruikend een hulpmiddel als [ Luke ](https://code.google.com/archive/p/luke/), moet u de console van Oak gebruiken om de index van `NodeStore` aan een folder van het filesystem te dumpen. Voor instructies op hoe te om dit te doen, lees de [ documentatie van Lucene ](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

U kunt de indexen in uw systeem ook in JSON-indeling extraheren. Hiervoor hebt u toegang tot `https://server:port/oak:index.tidy.-1.json` nodig

### Zoeklimieten {#query-limits}

**tijdens Ontwikkeling**

Stel lage drempelwaarden in voor `oak.queryLimitInMemory` (bijvoorbeeld 10000) en Oak. `queryLimitReads` (bijvoorbeeld 5000) en optimaliseer de dure vraag wanneer het raken van een UnsupportedOperationException die &quot;de vraag lezen meer dan x knopen...&quot; zegt

Dit helpt middelintensieve vragen (d.w.z. niet gesteund door om het even welke index of gesteund door minder het behandelen index) te vermijden. Bijvoorbeeld, zou een vraag die 1 miljoen knopen leest tot verhoogde I/O leiden, en negatief de algemene toepassingsprestaties beïnvloeden. Elke query die vanwege bovenstaande limieten mislukt, moet worden geanalyseerd en geoptimaliseerd.

#### **Post-Plaatsing** {#post-deployment}

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

Meer informatie beschikbaar onder: [ https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Tips voor het maken van efficiënte indexen {#tips-for-creating-efficient-indexes}

### Moet ik een index maken? {#should-i-create-an-index}

De eerste vraag die u moet stellen bij het maken of optimaliseren van indexen is of deze voor een bepaalde situatie vereist zijn. Als u de vraag in kwestie slechts één of slechts af en toe en bij een off-piek tijd voor het systeem door een partijproces gaat in werking stellen, kan het beter zijn om geen index bij allen tot stand te brengen.

Nadat u een index hebt gemaakt, moet de index ook worden bijgewerkt telkens wanneer de geïndexeerde gegevens worden bijgewerkt. Aangezien dit prestatiesimplicaties voor het systeem draagt, zouden indexen slechts moeten worden gecreeerd wanneer zij worden vereist.

Bovendien zijn indexen alleen nuttig als de gegevens in de index uniek genoeg zijn om ze te rechtvaardigen. Overweeg een index in een boek en de onderwerpen die het behandelt. Wanneer het indexeren van een reeks onderwerpen in een tekst, gewoonlijk zullen er honderden of duizenden ingangen zijn, die u aan een ondergroep van pagina&#39;s laat snel springen om de informatie snel te vinden die u zoekt. Als die index slechts twee of drie items bevat, die u elk op honderden pagina&#39;s aanwijzen, is de index niet nuttig. Hetzelfde concept geldt voor database-indexen. Als er slechts een paar unieke waarden zijn, is de index niet nuttig. Een index kan echter ook te groot worden om nuttig te zijn. Om indexstatistieken te bekijken, zie ](/help/sites-deploying/best-practices-for-queries-and-indexing.md#index-statistics) hierboven Statistieken van 0} Index.[

### Luidens- of eigenschapsindexen? {#lucene-or-property-indexes}

Lucene-indexen werden geïntroduceerd in Oak 1.0.9 en bieden krachtige optimalisaties voor de eigenschapsindexen die werden geïntroduceerd bij de eerste introductie van AEM 6. Wanneer u besluit of u Lucene-indexen of eigenschapsindexen wilt gebruiken, moet u rekening houden met het volgende:

* Lucene-indexen bieden veel meer functies dan eigenschapindexen. Een eigenschapindex kan bijvoorbeeld slechts één eigenschap indexeren, terwijl een Lucene-index er veel kan bevatten. Voor meer informatie over alle eigenschappen beschikbaar in de indexen van Lucene, raadpleeg de [ documentatie ](https://jackrabbit.apache.org/oak/docs/query/lucene.html).
* Lucene-indexen zijn asynchroon. Hoewel dit een aanzienlijke prestatieverhoging biedt, kan het ook een vertraging veroorzaken tussen wanneer gegevens naar de gegevensopslagplaats worden geschreven en wanneer de index wordt bijgewerkt. Als het essentieel is om vragen te hebben 100% nauwkeurige resultaten terugkeren, zou een bezitsindex worden vereist.
* Door asynchroon te zijn, kunnen de indexen van Lucene geen uniciteitsbeperkingen afdwingen. Als dit wordt vereist, dan moet een bezitsindex op zijn plaats worden gebracht.

In het algemeen, wordt het geadviseerd u de indexen van Lucene tenzij er een dwingende behoefte is om bezitsindexen te gebruiken zodat u de voordelen van hogere prestaties en flexibiliteit kunt bereiken.

### Solr Indexering {#solr-indexing}

AEM ondersteunt standaard ook Solr-indexering. Dit wordt gebruikt om volledige tekstonderzoek te steunen, maar het kan ook worden gebruikt om om het even welk type van vraag te steunen JCR. Solr zou moeten worden overwogen wanneer de AEM instanties niet de capaciteit van cpu hebben om het aantal vragen te behandelen die in onderzoek intensieve plaatsingen zoals onderzoek gedreven websites met een hoog aantal gezamenlijke gebruikers worden vereist. Alternatief, kan Solr in een op kruipper-gebaseerde benadering worden uitgevoerd om enkele meer geavanceerde eigenschappen van het platform te gebruiken.

Solr indexen kunnen worden gevormd om ingebed op de AEM server voor ontwikkelingsmilieu&#39;s in werking te stellen of aan een verre instantie kunnen worden geoffload om onderzoeksscalability op de productie en het opvoeren milieu&#39;s te verbeteren. Hoewel het offloaden van onderzoek scalability verbetert, introduceert het latentie en wegens dit, wordt niet geadviseerd tenzij vereist. Voor meer informatie over hoe te om de Solr integratie te vormen en hoe te om zonne indexen tot stand te brengen zie de [ Vragen van Oak en het Indexeren documentatie ](/help/sites-deploying/queries-and-indexing.md#the-solr-index).

>[!NOTE]
>
>Terwijl het nemen van de geïntegreerde Solr onderzoeksbenadering zou voor het ontladen van indexeren aan een Solr server toestaan. Als de geavanceerdere eigenschappen van de server van Solr door een op kruipper-gebaseerde benadering worden gebruikt, wordt het extra configuratiewerk vereist.

Het nadeel aan het nemen van deze benadering is dat terwijl door gebrek, AEM vragen ACLs respecteren en zo resultaten verbergen die een gebruiker geen toegang tot heeft, het externaliseren van onderzoek aan een Solr server zal deze eigenschap niet steunen. Als de zoekactie op deze manier extern moet worden uitgevoerd, moet er extra op worden gelet dat de gebruikers geen resultaten krijgen die ze niet zouden moeten zien.

Mogelijke gebruiksgevallen waarin deze aanpak passend kan zijn, zijn gevallen waarin zoekgegevens uit meerdere bronnen moeten worden samengevoegd. U hebt bijvoorbeeld een site die wordt gehost op AEM en een tweede site die wordt gehost op een extern platform. Solr zou kunnen worden gevormd om de inhoud van beide plaatsen te kruipen en hen op te slaan in een bijeengevoegde index. Op die manier kunnen zoekopdrachten naar andere sites worden uitgevoerd.

### Ontwerpoverwegingen {#design-considerations}

De documentatie van Oak voor de indexen van Lucene maakt een lijst van verscheidene overwegingen om te maken wanneer het ontwerpen van indexen:

* Gebruik `evaluatePathRestrictions` als de query andere padbeperkingen gebruikt. Dit staat de vraag toe om de ondergroep van resultaten onder de gespecificeerde weg terug te keren en dan hen te filtreren die op de vraag worden gebaseerd. Anders, zoekt de vraag naar alle resultaten die de vraagparameters in de bewaarplaats aanpassen en dan filter hen die op de weg worden gebaseerd.
* Als de query sortering gebruikt, heeft deze een expliciete eigenschapdefinitie voor de gesorteerde eigenschap en stelt deze `ordered` in op `true` . Hierdoor kunnen de resultaten als zodanig worden geordend in de index en worden kostbare sorteerbewerkingen tijdens de uitvoering van de query opgeslagen.

* Plaats alleen wat nodig is in de index. Als u overbodige functies of eigenschappen toevoegt, neemt de index toe en vertraagt de prestaties.
* In een eigenschapindex zou het hebben van een unieke eigenschapnaam helpen om de grootte op een index te reduceren, maar voor Lucene-indexen moeten `nodeTypes` en `mixins` worden gebruikt om consistente indexen te verkrijgen. Het opvragen van een specifieke `nodeType` of `mixin` zal krachtiger zijn dan het opvragen van `nt:base` . Definieer `indexRules` voor de `nodeTypes` in kwestie wanneer u deze methode gebruikt.

* Als uw vragen slechts onder bepaalde wegen worden in werking gesteld, dan creeer die indexen onder die wegen. Indexen hoeven niet in de hoofdmap van de opslagplaats te wonen.
* Gebruik één index wanneer alle eigenschappen die worden geïndexeerd verwant zijn om Lucene toe te staan om zo vele bezitsbeperkingen te evalueren mogelijk native. Ook, zal een vraag slechts één index gebruiken, zelfs wanneer het uitvoeren van een toetreden.

### CopyOnRead {#copyonread}

Wanneer de `NodeStore` extern is opgeslagen, kan een optie met de naam `CopyOnRead` worden ingeschakeld. De optie zorgt ervoor dat de externe index naar het lokale bestandssysteem wordt geschreven wanneer deze wordt gelezen. Dit kan helpen prestaties voor vragen verbeteren die vaak tegen deze verre indexen in werking worden gesteld.

Dit kan in de console OSGi onder de **dienst worden gevormd LuceneIndexProvider** en door gebrek zoals van Oak 1.0.13 toegelaten.

### Indexen verwijderen {#removing-indexes}

Wanneer u een index verwijdert, wordt het altijd aanbevolen de index tijdelijk uit te schakelen door de eigenschap `type` in te stellen op `disabled` en te testen of de toepassing correct werkt voordat deze daadwerkelijk wordt verwijderd. Een index wordt niet bijgewerkt als deze is uitgeschakeld, zodat de index mogelijk niet de juiste inhoud heeft als deze opnieuw wordt ingeschakeld en opnieuw moet worden ingesteld.

Nadat een bezitsindex op een instantie TarMK wordt verwijderd, moet de compensatie in werking worden gesteld om het even welke schijfruimte terug te winnen die in gebruik was. Voor indexen van Lucene, leeft de daadwerkelijke indexinhoud in BlobStore, zodat zou een inzameling van het huisvuil van de gegevensopslag worden vereist.

Wanneer u een index op een MongoDB-instantie verwijdert, zijn de verwijderingskosten evenredig met het aantal knooppunten in de index. Aangezien het schrappen van een grote index problemen kan veroorzaken, moet de geadviseerde benadering de index onbruikbaar maken en het slechts tijdens een onderhoudsvenster schrappen, gebruikend een hulpmiddel zoals **eak-mongo.js**. Merk op dat deze benadering niet voor regelmatige knoopinhoud zou moeten worden gebruikt aangezien het gegevensinconsistenties kan introduceren.

>[!NOTE]
>
>Voor meer informatie over eak-mongo.js, zie de [ sectie van de Hulpmiddelen van de Lijn van het Bevel ](https://jackrabbit.apache.org/oak/docs/command_line.html) van de documentatie van Oak.

### Het JCR-query-controleblad {#jcrquerycheatsheet}

Om de verwezenlijking van efficiënte vragen JCR en indexdefinities te steunen, is het [ JCR- Cheat Sheet van de Vraag ](assets/JCR_query_cheatsheet-v1.1.pdf) beschikbaar voor download en gebruik als verwijzing tijdens ontwikkeling. Het bevat steekproefvragen voor QueryBuilder, XPath, en SQL-2, die veelvoudige scenario&#39;s behandelen die zich verschillend in termen van vraagprestaties gedragen. Het verstrekt ook aanbevelingen voor om indexen van Oak te bouwen of aan te passen. De inhoud van dit Cheat Sheet is van toepassing op AEM 6.5 en AEM as a Cloud Service.

## Opnieuw indexeren {#re-indexing}

Deze sectie schetst **slechts** aanvaardbare redenen om de indexen van Oak opnieuw te indexeren.

Buiten de hieronder geschetste redenen, in werking stellend herindexen van de indexen van Oak **** verandert gedrag niet of lost kwesties op, en verhoogt onnodig ladingen op AEM.

Herindexering van Oak-indexen moet worden vermeden, tenzij daarvoor in onderstaande tabellen een reden is opgegeven.

>[!NOTE]
>
>Voorafgaand aan het raadplegen van de lijsten hieronder om te bepalen als het opnieuw indexeren nuttig is, **** verifieert altijd:
>
>* de vraag correct is
>* de vraag lost aan de verwachte index op (gebruikend [ Verklaar Vraag ](/help/sites-administering/operations-dashboard.md#diagnosis-tools))
>* het indexeringsproces is voltooid
>

### Wijzigingen in Oak-indexconfiguratie {#oak-index-configuration-changes}

De enige aanvaardbare niet-foutcondities voor het opnieuw indexeren van Oak-indexen zijn als de configuratie van een Oak-index is gewijzigd.

*het opnieuw indexeren zou altijd met juiste overweging op zijn effect aan het AEM van algemene prestaties moeten worden gericht, en tijdens periodes van lage activiteit of onderhoudsvensters worden uitgevoerd.*

De volgende details en resoluties zijn mogelijk:

* [Wijziging van indexdefinitie van eigenschap](#property-index-definition-change)
* [Wijziging van de definitie van Lucene-index](#lucene-index-definition-change)

#### Wijziging van indexdefinitie van eigenschap {#property-index-definition-change}

* Is van toepassing op/if:

   * Alle Oak-versies
   * Slechts [ bezitsindexen ](https://jackrabbit.apache.org/oak/docs/query/property-index.html)

* Symptomen:

   * Nodes existing before to property index&#39;s definition update missing from results

* Hoe te om te verifiëren:

   * Bepaal of er ontbrekende knooppunten zijn gemaakt/gewijzigd vóór de implementatie van de bijgewerkte indexdefinitie.
   * Controleer de eigenschappen `jcr:created` of `jcr:lastModified` van ontbrekende knooppunten op basis van de gewijzigde tijd van de index

* Hoe oplossen:

   * [ herindexeer ](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-re-index) de luceenindex
   * U kunt ook op de ontbrekende knooppunten tikken (een goedaardige schrijfbewerking uitvoeren)

      * Vereist handmatige aanrakingen of aangepaste code
      * De set ontbrekende knooppunten moet bekend zijn
      * Vereist het veranderen van om het even welke bezit op de knoop

#### Wijziging van de definitie van Lucene-index {#lucene-index-definition-change}

* Is van toepassing op/if:

   * Alle Oak-versies
   * Slechts [ lucene indexen ](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten
   * De zoekresultaten weerspiegelen niet het verwachte gedrag van de indexdefinitie
   * Het plan van de vraag rapporteert geen verwachte output die op indexdefinitie wordt gebaseerd

* Hoe te om te verifiëren:

   * Verifieer dat de indexdefinitie gebruikend de statistieken JMX Mbean van de Index (LuceneIndex), methode `diffStoredIndexDefinition` werd veranderd.

* Hoe oplossen:

   * Oak-versies ouder dan 1.6:

      * [ herindexeer ](#how-to-re-index) de luceenindex

   * Oak 1.6+

      * Als de wijzigingen de bestaande inhoud niet beïnvloeden, hoeft u alleen de inhoud te vernieuwen

         * [ verfrist zich ](https://jackrabbit.apache.org/oak/docs/query/lucene.html#stored-index-definition) de lucene index door [ te plaatsen:queryIndexDefinition ]@refresh=true

      * Anders, [ herdex ](#how-to-re-index) de lucene index

         * Opmerking: de indexstatus van de laatste goede herindexering (of eerste indexering) wordt gebruikt totdat een nieuwe herindexering wordt geactiveerd.

### Erkende en uitzonderlijke situaties {#erring-and-exceptional-situations}

In de volgende tabel worden de enige aanvaardbare fouten en uitzonderlijke situaties beschreven waarin het probleem wordt opgelost door de indexen van Oak opnieuw te indexeren.

Als een kwestie op AEM wordt ervaren die niet de hieronder geschetste criteria aanpast, **** geen indexen herindexeert, aangezien het niet de kwestie zal oplossen.

De volgende details en resoluties zijn mogelijk:

* [Binair Lucene-indexbestand ontbreekt](#lucene-index-binary-is-missing)
* [Binair Lucene-index is beschadigd](#lucene-index-binary-is-corrupt)

#### Binair Lucene-indexbestand ontbreekt {#lucene-index-binary-is-missing}

* Is van toepassing op/if:

   * Alle Oak-versies
   * Slechts [ lucene indexen ](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten

* Hoe te om te verifiëren:

   * Het dossier van het foutenlogboek bevat een uitzondering die een binair getal van de index van Lucene zegt mist

* Hoe oplossen:

   * Een doorlopende controle in de repository uitvoeren, bijvoorbeeld:

     [ http://localhost:4502/system/console/repositorycheck](http://localhost:4502/system/console/repositorycheck)

     het doorlopen van de gegevensopslagruimte bepaalt of andere binaire bestanden (behalve lucene-bestanden) ontbreken

   * Als binaire getallen anders dan lucene-indexen ontbreken, kunt u terugzetten vanaf een back-up
   * Anders, [ herdex ](#how-to-re-index) *alle* lucene indexen
   * Opmerking:

     Deze voorwaarde is indicatief van een misconfigured datastore die in OM HET EVEN WELK binair getal (bijvoorbeeld, activa binaries) kan resulteren om te gaan missen.

     In dit geval herstelt u de laatst bekende goede versie van de opslagplaats om alle ontbrekende binaire bestanden te herstellen.

#### Binair Lucene-index is beschadigd {#lucene-index-binary-is-corrupt}

* Is van toepassing op/if:

   * Alle Oak-versies
   * Slechts [ lucene indexen ](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptomen:

   * Lucene-index bevat geen verwachte resultaten

* Hoe te om te verifiëren:

   * `AsyncIndexUpdate` (om de vijf seconden) zal mislukken met een uitzondering in error.log:

     `...a Lucene index file is corrupt...`

* Hoe oplossen:

   * Verwijder de lokale kopie van de index van de lucene

      1. AEM stoppen
      1. Verwijder de lokale kopie van de lucene-index op `crx-quickstart/repository/index`
      1. AEM opnieuw starten

   * Als dit het probleem niet verhelpt en de uitzonderingen `AsyncIndexUpdate` blijven bestaan:

      1. [ herindexeer ](#how-to-re-index) de foutenindex
      1. Ook dossier een ](https://helpx.adobe.com/support.html) kaartje van de Steun van de Adobe 0} {[

### Opnieuw indexeren {#how-to-re-index}

>[!NOTE]
>
>In AEM 6.5, [ oak-run.jar is de ENIGE gesteunde methode ](/help/sites-deploying/indexing-via-the-oak-run-jar.md#reindexingapproachdecisiontree) voor het opnieuw indexeren op de bewaarplaatsen MongoMK of RDBMK.

#### Eigenschapindexen opnieuw indexeren {#re-indexing-property-indexes}

* Gebruik [ eak-run.jar ](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) om de bezitsindex opnieuw te indexeren
* De eigenschap async-redex instellen op true op de index van de eigenschap

   * `[oak:queryIndexDefinition]@reindex-async=true`

* Opnieuw indexeert de bezitsindex asynchroon gebruikend de Console van het Web via **PropertyIndexAsyncReindex** MBean;

  bijvoorbeeld:

  [ http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex)

#### indexen van eigenschappen van Lucene opnieuw indexeren {#re-indexing-lucene-property-indexes}

* Gebruik [ eak-run.jar om ](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) de index van het Bezit van Lucene opnieuw te indexeren.
* Stel de eigenschap async-redex in op true op de index van de eigenschap lucene

   * `[oak:queryIndexDefinition]@reindex-async=true`

>[!NOTE]
>
>De voorafgaande sectie vat en kaders de Oak opnieuw indexerende begeleiding van de [ documentatie van Apache Oak ](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) in de context van AEM samen.

### Tekstvoorextractie van binaire tekens {#text-pre-extraction-of-binaries}

De preextractie van de tekst is het proces om tekst uit binaire getallen, direct uit de Opslag van Gegevens door middel van een geïsoleerd proces te halen en direct blootstellend de gehaalde tekst aan verdere re-indexeringen van Oak indexen.

* Voorextractie van Oak-tekst wordt aanbevolen voor het opnieuw/indexeren van Lucene-indexen in opslagruimten met grote volumes bestanden (binaire bestanden) die extraheerbare tekst bevatten (bijvoorbeeld PDF, Word Docs, PPT&#39;s, TXT, enzovoort) die in aanmerking komen voor full-text zoekopdrachten via geïmplementeerde Oak-indexen, bijvoorbeeld `/oak:index/damAssetLucene` .
* De pre-extractie van de tekst komt slechts het re/indexeren van indexen van Lucene, en NIET Oak bezitsindexen ten goede, aangezien de bezitsindexen geen tekst uit binaire getallen halen.
* De preextractie van tekst heeft een groot positief effect wanneer de full-text herindexering van tekst-zware binaire getallen (PDF, Doc, TXT, etc.), terwijl een bewaarplaats van beelden niet de zelfde efficiency zal genieten aangezien de beelden geen extractable tekst bevatten.
* Bij het vooraf extraheren van tekst wordt tekst met volledige tekst op een extra efficiënte manier geëxtraheerd en wordt deze tekst op een extra efficiënte manier aan het Oak-proces voor het opnieuw indexeren en opnieuw gebruiken aangeboden.

#### Wanneer kan de tekstvoorextractie worden gebruikt? {#when-can-text-pre-extraction-be-used}

Het opnieuw indexeren van een **bestaande** lucene index met binaire toegelaten extractie

* Het opnieuw indexeren van verwerking **alle** kandidaatinhoud in de bewaarplaats; wanneer binaries om full-text uit te halen talrijk of complex zijn, wordt een verhoogde computerbelasting aan uitvoerbare full-text extractie geplaatst op AEM. De pre-extractie van de tekst beweegt het &quot;computer dure werk&quot;van tekst-extractie in een geïsoleerd proces dat tot AEM Opslag van Gegevens direct toegang heeft, vermijdend overheadkosten en middelgeschil in AEM.

Het steunen van de plaatsing van a **nieuwe** lucene index aan AEM met binaire toegelaten extractie

* Wanneer een nieuwe index (met binaire toegelaten extractie) in AEM wordt opgesteld, indexeert Oak automatisch alle kandidaatinhoud op de volgende async full-text indexlooppas. Om dezelfde redenen die in bovenstaande overweging worden beschreven, kan dit leiden tot een te zware belasting bij AEM.

#### Wanneer kan de voorextractie van tekst NIET worden gebruikt? {#when-can-text-pre-extraction-not-be-used}

Tekstomloop kan niet worden gebruikt voor nieuwe inhoud die aan de opslagplaats wordt toegevoegd, en is ook niet nodig.

Nieuwe inhoud wordt toegevoegd aan de repository zal automatisch en incrementeel geïndexeerd worden door het async full-text indexeringsproces (standaard elke 5 seconden).

Onder normale verrichting van AEM, bijvoorbeeld, zal het uploaden van Assets via het Web UI of programmatic ingest van Assets, AEM automatisch en incrementeel full-text index de nieuwe binaire inhoud. Aangezien de hoeveelheid gegevens incrementeel en relatief klein is (ongeveer de hoeveelheid gegevens die in 5 seconden aan de opslagplaats kan worden gepresteerd), kan AEM de full-text extractie uit de binaire getallen uitvoeren tijdens het indexeren zonder de algemene systeemprestaties te beïnvloeden.

#### Vereisten voor het gebruik van tekstvoorextractie {#prerequisites-to-using-text-pre-extraction}

* U zult opnieuw indexeren een lucene index die full-text binaire extractie uitvoert of een nieuwe index opstelt die full-text indexbinaire getallen van bestaande inhoud zal uitvoeren
* De inhoud (binaire bestanden) waaruit tekst vooraf kan worden geëxtraheerd, moet zich in de opslagplaats bevinden
* Een onderhoudsvenster voor het genereren van het CSV-bestand EN voor het uitvoeren van de laatste nieuwe configuratie
* Oak-versie: 1.0.18+, 1.2.3+
* [ eak-run.jar ](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/) versie 1.7.4+
* Een bestandssysteemmap/-share voor het opslaan van geëxtraheerde tekst die toegankelijk is via de indexering AEM instanties

   * De OSGi-config van de preextractie van de Tekst vereist een weg van het dossiersysteem aan de gehaalde tekstdossiers, zodat moeten zij direct van de AEM instantie (lokale aandrijving of het dossier delen onderstel) toegankelijk zijn

#### Voorvertoning van tekst uitvoeren {#how-to-perform-text-pre-extraction}

>[!NOTE]
>
>***de eik-looppas.jar bevelen hieronder worden geschetst worden volledig opgesomd in [ https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html ](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html)***
>
>Het bovenstaande diagram en de onderstaande stappen dienen als toelichting en aanvulling op de technische tekstvoorbereidingsstappen die in de documentatie van Apache Oak worden beschreven.

![ de pre-extractieprocesstroom van de Tekst ](assets/chlimage_1-139.png)

**produceer lijst van inhoud aan preextract**

*Stap 1 van de Looppas (a-b) tijdens een onderhoudsvenster/laag-gebruiksperiode aangezien de Opslag van de Knoop tijdens deze verrichting wordt overgestoken, die significante lading op het systeem kan veroorzaken.*

1 bis. Voer `oak-run.jar --generate` uit om een lijst met knooppunten te maken waarvan de tekst vooraf wordt uitgepakt.

1 ter. Lijst met knooppunten (1a) wordt als CSV-bestand opgeslagen in het bestandssysteem

De volledige opslag van de Knoop wordt overgestoken (zoals die door de wegen in het eiken-in werking stellen bevel) wordt gespecificeerd telkens als `--generate` wordt uitgevoerd, en a **nieuw** CSV dossier wordt gecreeerd. Het Csv- dossier wordt **niet** opnieuw gebruikt tussen discrete uitvoeringen van het proces van de tekstvoorwinning (Stappen 1 - 2).

**preextract tekst aan dossiersysteem**

*Stap 2 (a-c) kan tijdens normale verrichting van AEM worden uitgevoerd is het slechts met de Opslag van Gegevens in wisselwerking staat.*

2 bis. Voer `oak-run.jar --tika` uit om tekst voor de binaire knooppunten die zijn opgesomd in het CSV-bestand dat is gegenereerd in (1b), vooraf te extraheren

2 ter. Het proces dat in (2a) wordt in werking gesteld heeft toegang tot binaire knopen die in CSV in de Opslag van Gegevens worden bepaald direct, en haalt tekst uit.

2 quater. Geëxtraheerde tekst wordt opgeslagen op een bestandssysteem in een indeling die instelbaar is door het Oak-herindexeringsproces (3a)

De vooraf geëxtraheerde tekst wordt in de CSV geïdentificeerd door de binaire vingerafdruk. Als het binaire bestand hetzelfde is, kan dezelfde vooraf geëxtraheerde tekst worden gebruikt in AEM instanties. Aangezien AEM Publish doorgaans een subset van AEM auteur is, kan de vooraf geëxtraheerde tekst van AEM auteur vaak ook worden gebruikt om Publish opnieuw te indexeren (ervan uitgaande dat de AEM Publish toegang heeft tot het bestandssysteem van de geëxtraheerde tekstbestanden).

Aan vooraf geëxtraheerde tekst kan stapsgewijs worden toegevoegd. De voorextractie van tekst slaat de extractie van eerder geëxtraheerde binaire bestanden over. Het is daarom aan te raden om vooraf geëxtraheerde tekst te behouden voor het geval dat in de toekomst opnieuw tekst moet worden geëxtraheerd (ervan uitgaande dat de geëxtraheerde inhoud niet prohibitief groot is). Als dit het geval is, evalueert het Zijden van de inhoud in het tussentijdse stadium, aangezien de tekst goed samenperst).

**opnieuw indexeert de indexen van Oak, die full-text van de Geëxtraheerde dossiers van de Tekst** betrekken

*Looppas die (Stappen 3a-b) opnieuw indexeert tijdens een onderhoud/laag-gebruiksperiode aangezien de Opslag van de Knoop tijdens deze verrichting wordt overgestoken, die significante lading op het systeem kan veroorzaken.*

3 bis. [ opnieuw indexeert ](#how-to-re-index) van de indexen van Lucene wordt aangehaald in AEM.

3 ter. De Apache Jackrabbit Oak DataStore PreExtractedTextProvider OSGi config (geconfigureerd om te wijzen naar de uitgenomen tekst via een bestandssysteempad) geeft Oak de opdracht om volledige tekst uit de uitgenomen bestanden te betrekken en vermijdt direct het raken en verwerken van de gegevens die zijn opgeslagen in de opslagplaats.
