---
title: Oak-query's en indexering
description: Leer hoe u indexen configureert in Adobe Experience Manager (AEM) 6.5.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/queries-and-indexing
feature: Configuring
exl-id: d9ec7728-84f7-42c8-9c80-e59e029840da
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '3034'
ht-degree: 0%

---

# Oak-query&#39;s en indexering{#oak-queries-and-indexing}

>[!NOTE]
>
>Dit artikel gaat over het vormen van indexen in AEM 6. Voor beste praktijken bij het optimaliseren van vraag en het indexeren prestaties, zie [Beste praktijken voor Vragen en het Indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

## Inleiding {#introduction}

In tegenstelling tot Jackrabbit 2 indexeert eik inhoud niet standaard. Aangepaste indexen moeten zo nodig worden gemaakt, net als bij traditionele relationele databases. Als er geen index voor een specifieke vraag is, worden vele knopen misschien overgestoken. De query werkt mogelijk nog wel, maar het is waarschijnlijk traag.

Als het Eak een vraag zonder een index ontmoet, wordt een bericht van het het niveaulogboek van WARN gedrukt:

```xml
*WARN* Traversed 1000 nodes with filter Filter(query=select ...) consider creating an index or changing the query
```

## Ondersteunde querytalen {#supported-query-languages}

De oak-query-engine ondersteunt de volgende talen:

* XPath (aanbevolen)
* SQL-2
* SQL (vervangen)
* JQOM

## Indexeertypen en kostenberekening {#indexer-types-and-cost-calculation}

Met de Apache Oak-gebaseerde backend kunnen verschillende indexen in de repository worden aangesloten.

Eén index is de **Eigenschappenindex**, waarvoor de indexdefinitie is opgeslagen in de dataopslag zelf.

Implementaties voor **Apache Lucene** en **Solr** zijn ook beschikbaar door gebrek, die allebei fulltext indexeren steunen.

De **Traversal Index** wordt gebruikt als er geen andere index beschikbaar is. Dit betekent dat de inhoud niet wordt geïndexeerd en de inhoudsknopen worden getransformeerd om gelijken aan de vraag te vinden.

Als de veelvoudige indexeerders voor een vraag beschikbaar zijn, schat elke beschikbare indexeerder de kosten om de vraag uit te voeren. Eak kiest vervolgens de indexeerder met de laagste geschatte kosten.

![chlimage_1-148](assets/chlimage_1-148.png)

Het bovenstaande diagram is een vertegenwoordiging op hoog niveau van het mechanisme van de vraaguitvoering van Apache Oak.

Eerst, wordt de vraag ontleed in een Abstracte Boom van de Syntaxis. Dan, wordt de vraag gecontroleerd en in SQL-2 getransformeerd die de inheemse taal voor de vragen van het Eak is.

Daarna, wordt elke index geraadpleegd om de kosten voor de vraag te schatten. Zodra dat wordt voltooid, worden de resultaten van de goedkoopste index teruggewonnen. Tot slot worden de resultaten gefilterd, zowel om ervoor te zorgen dat de huidige gebruiker toegang tot het resultaat heeft gelezen en dat het resultaat de volledige vraag aanpast.

## De indexen configureren {#configuring-the-indexes}

>[!NOTE]
>
>Voor een grote opslagplaats is het bouwen van een index een tijdrovende bewerking. Dit geldt zowel voor het eerste ontwerp van een index als voor het opnieuw indexeren (het opnieuw samenstellen van een index nadat de definitie is gewijzigd). Zie ook [Probleemoplossing voor Oak-indexen](/help/sites-deploying/troubleshooting-oak-indexes.md) en [Langzame indexering voorkomen](/help/sites-deploying/troubleshooting-oak-indexes.md#preventing-slow-re-indexing).

Als herindexering nodig is in grote opslagruimten, met name bij gebruik van MongoDB en voor full-text indexen, kunt u de tekst vooraf extraheren en eekuitvoering gebruiken om de eerste index te genereren en opnieuw te indexeren.

De indexen worden gevormd als knopen in de bewaarplaats onder **Eak:index** knooppunt.

Het type van de indexknoop moet zijn **eikel:QueryIndexDefinition.** Verschillende configuratieopties zijn beschikbaar voor elke index als knoopeigenschappen. Voor meer informatie, zie de configuratiedetails voor elk hieronder indexeertype.

### De eigenschappenindex {#the-property-index}

De index van het Bezit is nuttig voor vragen die bezitsbeperkingen hebben maar niet full-text zijn. Het kan worden gevormd door de hieronder procedure te volgen:

1. CRXDE openen door naar `http://localhost:4502/crx/de/index.jsp`
1. Een knooppunt maken onder **eiken:index**
1. De node een naam geven **PropertyIndex** en stel het knooppunttype in op **eak:QueryIndexDefinition**
1. Stel de volgende eigenschappen in voor het nieuwe knooppunt:

   * **type:**  `property` (van het type String)
   * **propertyNames :**  `jcr:uuid` (van het type Name)

   In dit voorbeeld wordt de index van `jcr:uuid` eigenschap, waarvan de taak is om de universeel unieke id (UUID) weer te geven van het knooppunt waaraan deze is gekoppeld.

1. Sla de wijzigingen op.

De index van het Bezit heeft de volgende configuratieopties:

* De **type** eigenschap geeft het type index aan en in dit geval moet deze worden ingesteld op **eigenschap**

* De **propertyNames** Deze eigenschap geeft de lijst aan met de eigenschappen die in de index zijn opgeslagen. Als de naam van het knooppunt ontbreekt, wordt deze gebruikt als een verwijzingswaarde voor de eigenschapnaam. In dit voorbeeld wordt **jcr:uuid** eigenschap waarvan de taak bestaat om de unieke id (UUID) van het bijbehorende knooppunt beschikbaar te maken, wordt toegevoegd aan de index.

* De **uniek** markering die, indien ingesteld op **true** voegt een unieke restrictie toe aan de eigenschapindex.

* De **declaringNodeTypes** Met eigenschap kunt u een bepaald knooppunttype opgeven waarop de index alleen van toepassing is.
* De **hergroeperen** markering die indien ingesteld op **true**, wordt een volledige inhoudsherdex geactiveerd.

### De geordende index {#the-ordered-index}

De geordende index is een uitbreiding van de index van het Bezit. Het is echter afgekeurd. Indexen van dit type moeten worden vervangen door [Eigenschappenindex van Lucene](#the-lucene-property-index).

### De index van volledige tekst met Lucene {#the-lucene-full-text-index}

Een volledige tekstindexeerfunctie op basis van Apache Lucene is beschikbaar in AEM 6.

Als een full-text index wordt gevormd, gebruiken alle vragen die een full-text voorwaarde hebben de full-text index, geen kwestie als er andere voorwaarden zijn die worden geïndexeerd, en geen kwestie als er een wegbeperking is.

Als geen full-text index wordt gevormd, dan werken de vragen met full-text voorwaarden niet zoals verwacht.

Omdat de index wordt bijgewerkt door middel van een asynchrone achtergrondthread, zijn sommige full-text onderzoeken niet beschikbaar voor een klein venster van tijd tot de achtergrondprocessen worden gebeëindigd.

U kunt een volledig-tekstindex van Lucene vormen door de hieronder procedure te volgen:

1. CRXDE openen en een knooppunt maken onder **eiken:index**.
1. De node een naam geven **LuceneIndex** en stel het knooppunttype in op **eak:QueryIndexDefinition**
1. Voeg de volgende eigenschappen toe aan het knooppunt:

   * **type:**  `lucene` (van het type String)
   * **async:**  `async` (van het type String)

1. Sla de wijzigingen op.

De index van Lucene heeft de volgende configuratieopties:

* De **type** eigenschap die het type index aangeeft, moet worden ingesteld op **luceen**
* De **asynchroon** eigenschap die moet worden ingesteld op **asynchroon**. Hiermee wordt het indexupdateproces naar een achtergrondthread verzonden.
* De **includePropertyTypes** eigenschap, die definieert welke subset van eigenschapstypen in de index worden opgenomen.
* De **excludePropertyNames** eigenschap die een lijst met namen van eigenschappen definieert - eigenschappen die moeten worden uitgesloten van de index.
* De **hergroeperen** markering die is ingesteld op **true**, wordt een volledige inhoudsherdex geactiveerd.

### Volledige tekst zoeken {#understanding-fulltext-search}

De documentatie in deze sectie is op Apache Lucene, Elasticsearch, en fullText indexen van PostSQL, SQLite, en MySQL, bijvoorbeeld van toepassing. Het volgende voorbeeld is voor AEM / Eak / Lucene.

<b>Te indexeren gegevens</b>

Het uitgangspunt is de gegevens die moeten worden geïndexeerd. Neem bijvoorbeeld de volgende documenten:

| <b>Document-id</b> | <b>Pad</b> | <b>Fulltext</b> |
| --- | --- | --- |
| 100 | /content/rubik | &quot;Rubik is een Fins merk.&quot; |
| 200 | /content/rubiksCube | &quot;De Rubiks kubus werd uitgevonden in 1974.&quot; |
| 300 | /content/cube | &quot;Een kubus is een driedimensionaal object.&quot; |


<b>Omgekeerde index</b>

Het indexeringsmechanisme verdeelt de volledige tekst in woorden genoemd &quot;tokens&quot;, en bouwt een index genoemd &quot;omgekeerde index&quot;. Deze index bevat de lijst met documenten waarin deze voor elk woord wordt weergegeven.

Korte, algemene woorden (ook wel &quot;stopwords&quot; genoemd) worden niet geïndexeerd. Alle tokens worden omgezet in kleine letters en stammen wordt toegepast.

Speciale tekens zoals *&quot;-&quot;* niet geïndexeerd.

| <b>Token</b> | <b>Document-id&#39;s</b> |
| --- | --- |
| 194 | ..., 200... |
| merk | ..., 100,... |
| kubus | ..., 200, 300,... |
| dimensie | 300 |
| afmaken | ..., 100,... |
| uitvinden | 200 |
| object | ..., 300,... |
| rubik | ..., 100, 200,... |

De lijst met documenten wordt gesorteerd. Dit is handig wanneer je vraagt.

<b>Zoeken</b>

Hieronder ziet u een voorbeeld van een query. Alle speciale tekens (zoals *&#39;*) vervangen door een spatie:

```
/jcr:root/content//element(\*; cq:Page)`[` jcr:contains('Rubik s Cube')`]`
```

De woorden worden op dezelfde manier verdeeld en gefilterd als bij het indexeren (woorden van één teken worden bijvoorbeeld verwijderd). In dit geval wordt gezocht naar:

```
+:fulltext:rubik +:fulltext:cube
```

De index raadpleegt de lijst met documenten voor die woorden. Als er veel documenten zijn, kan de lijst groot zijn. Stel bijvoorbeeld dat ze het volgende bevatten:


| <b>Token</b> | <b>Document-id&#39;s</b> |
| --- | --- |
| rubik | 10, 100, 200, 1000 |
| kubus | 30, 200, 300, 2000 |


Lucene draait heen en weer tussen de twee lijsten (of ronde lijnen) `n` lijsten, bij het zoeken naar `n` woorden):

* Lees in de &quot;rubik&quot; krijgt de eerste vermelding: er zijn er 10.
* Lees in de &quot;kubus&quot; krijgt het eerste item `>` = 10. 10 is niet gevonden, de volgende is 30.
* Lees in het &quot;rubik&quot; krijgt de eerste vermelding `>` = 30: 100.
* Lees in de &quot;kubus&quot; krijgt het eerste item `>` = 100 : 200 .
* Lees in het &quot;rubik&quot; krijgt de eerste vermelding `>` = 200. 200 is gevonden. Document 200 is dus een overeenkomst voor beide termen. Dit wordt onthouden.
* Lees in het &quot;rubik&quot; krijgt de volgende vermelding: 1000.
* Lees in de &quot;kubus&quot; krijgt het eerste item `>` = 1000 : 2000 .
* Lees in het &quot;rubik&quot; krijgt de eerste vermelding `>` = 2000: einde van de lijst.
* Tot slot kunt u ophouden met zoeken.

Het enige gevonden document dat beide termen bevat, is 200, zoals in het onderstaande voorbeeld:

| 200 | /content/rubiksCube | &quot;De Rubiks kubus werd uitgevonden in 1974.&quot; |
| --- | --- | --- |

Wanneer meerdere items worden gevonden, worden deze op score gesorteerd.

### De index van de eigenschap Lucene {#the-lucene-property-index}

Sinds **Eik 1.0.8**, Lucene kan worden gebruikt om indexen tot stand te brengen die bezitsbeperkingen impliceren die niet full-text zijn.

Om een index van het Bezit van de Luidspreker te bereiken, **fulltextEnabled** eigenschap moet altijd worden ingesteld op false.

Neem de volgende voorbeeldvraag:

```xml
select * from [nt:base] where [alias] = '/admin'
```

Om een Index van het Bezit van Lucene voor de bovengenoemde vraag te bepalen, kunt u de volgende definitie toevoegen door een knoop onder te creëren **`oak:index`:**

* **Naam:** `LucenePropertyIndex`
* **Type:** `oak:QueryIndexDefinition`

Voeg de volgende eigenschappen toe wanneer het knooppunt is gemaakt:

* **type:**

  ```xml
  lucene (of type String)
  ```

* **async:**

  ```xml
  async (of type String)
  ```

* **fulltextEnabled:**

  ```xml
  false (of type Boolean)
  ```

* **includePropertyNames:** `["alias"] (of type String)`

>[!NOTE]
>
>In vergelijking met de reguliere eigenschappenindex wordt de index van het Lucene-eigenschap altijd geconfigureerd in de asynchrone modus. De resultaten die door de index worden geretourneerd, weerspiegelen dus mogelijk niet altijd de meest actuele staat van de gegevensopslagruimte.

>[!NOTE]
>
>Voor meer specifieke informatie over de Index van het Bezit van de Luidspreker, zie [Documentatiepagina Apache Jackrabbit Oak Lucene](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Luceenanalysatoren {#lucene-analyzers}

Sinds versie 1.2.0 ondersteunt eik Lucene-analysatoren.

Analyzers worden zowel gebruikt wanneer een document, als bij vraagtijd wordt geïndexeerd. Een analysator controleert de tekst van gebieden en produceert een symbolische stroom. Luceenanalysatoren bestaan uit een reeks tokenizer- en filterklassen.

De analysatoren kunnen worden geconfigureerd via de `analyzers` node (type) `nt:unstructured`) in de `oak:index` definitie.

De standaardanalysator voor een index wordt gevormd in `default` onderliggend element van het knooppunt analyzers.

![chlimage_1-149](assets/chlimage_1-149.png)

>[!NOTE]
>
>Voor een lijst van beschikbare analysatoren, zie de API documentatie van de versie van Lucene u gebruikt.

#### De klasse Analyzer rechtstreeks opgeven {#specifying-the-analyzer-class-directly}

Als u een analysator in de doos wilt gebruiken, kunt u deze configureren volgens de onderstaande procedure:

1. Zoek de index waarmee u de analysator wilt gebruiken onder de `oak:index` knooppunt.

1. Onder de index maakt u een onderliggend knooppunt met de naam `default` van het type `nt:unstructured`.

1. Voeg een eigenschap toe aan het standaardknooppunt met de volgende eigenschappen:

   * **Naam:** `class`
   * **Type:** `String`
   * **Waarde:** `org.apache.lucene.analysis.standard.StandardAnalyzer`

   De waarde is de naam van de klasse analyzer die u wilt gebruiken.

   U kunt ook instellen dat de analysator wordt gebruikt met een specifieke lucene-versie door de optionele `luceneMatchVersion` string eigenschap. Een geldige syntaxis voor het gebruiken van het met Lucene 4.7 zou zijn:

   * **Naam:** `luceneMatchVersion`
   * **Type:** `String`
   * **Waarde:** `LUCENE_47`

   Indien `luceneMatchVersion` is niet opgegeven, gebruikt Oak de versie van Lucene waarmee het is verzonden.

1. Als u een stopwoordenbestand wilt toevoegen aan de analysatorconfiguraties, kunt u een knooppunt maken onder de `default` één met de volgende eigenschappen:

   * **Naam:** `stopwords`
   * **Type:** `nt:file`

#### Analysatoren maken door middel van compositie {#creating-analyzers-via-composition}

Analysatoren kunnen ook op basis van `Tokenizers`, `TokenFilters`, en `CharFilters`. U kunt dit doen door een analysator te specificeren en kindknopen van zijn facultatieve tokenizers en filters te creëren die in vermelde orde worden toegepast. Zie ook [https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema](https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema)

Bekijk deze knooppuntstructuur als voorbeeld:

* **Naam:** `analyzers`

   * **Naam:** `default`

      * **Naam:** `charFilters`
      * **Type:** `nt:unstructured`

         * **Naam:** `HTMLStrip`
         * **Naam:** `Mapping`

      * **Naam:** `tokenizer`

         * **Naam eigenschap:** `name`

            * **Type:** `String`
            * **Waarde:** `Standard`

      * **Naam:** `filters`
      * **Type:** `nt:unstructured`

         * **Naam:** `LowerCase`
         * **Naam:** `Stop`

            * **Naam eigenschap:** `words`

               * **Type:** `String`
               * **Waarde:** `stop1.txt, stop2.txt`

            * **Naam:** `stop1.txt`

               * **Type:** `nt:file`

            * **Naam:** `stop2.txt`

               * **Type:** `nt:file`

De naam van de filters, charFilters, en tokenizers wordt gevormd door de fabrieksachtervoegsels te verwijderen. Aldus:

* `org.apache.lucene.analysis.standard.StandardTokenizerFactory` wordt `standard`

* `org.apache.lucene.analysis.charfilter.MappingCharFilterFactory` wordt `Mapping`

* `org.apache.lucene.analysis.core.StopFilterFactory` wordt `Stop`

Om het even welke configuratieparameter die voor de fabriek wordt vereist wordt gespecificeerd als bezit van de knoop in kwestie.

Voor gevallen zoals het laden van stopwoorden waarbij inhoud van externe bestanden moet worden geladen, kan de inhoud worden opgegeven door een onderliggende node te maken van `nt:file` type voor het desbetreffende bestand.

### De zonne-index {#the-solr-index}

Het doel van de index Solr is full-text onderzoek maar het kan ook worden gebruikt om onderzoek door weg, bezitsbeperkingen, en primaire typebeperkingen te indexeren. Dit betekent dat de Solr-index in eikel kan worden gebruikt voor elk type JCR-query.

De integratie in AEM gebeurt op het niveau van de opslagplaats zodat Solr één van de mogelijke indexen is die in Oak kunnen worden gebruikt, de nieuwe opbergingsimplementatie die met AEM wordt verscheept.

Het kan worden gevormd om als verre server met de AEM instantie te werken.

### AEM configureren met één externe Solr-server {#configuring-aem-with-a-single-remote-solr-server}

AEM kan ook worden geconfigureerd om te werken met een externe Solr-serverinstantie:

1. Download en extraheer de nieuwste versie van Solr. Zie voor meer informatie over hoe u dit kunt doen de [Installatiedocumentatie van Apache Solr](https://solr.apache.org/guide/6_6/installing-solr.html).
1. Maak nu twee Solr-planken. U kunt dit doen door mappen te maken voor elk segment in de map waarin Solr is uitgepakt:

   * Voor de eerste gedeelde map maakt u de map:

   `<solrunpackdirectory>\aemsolr1\node1`

   * Voor de tweede schijf maakt u de map:

   `<solrunpackdirectory>\aemsolr2\node2`

1. Zoek de voorbeeldinstantie in het Solr-pakket. Het bevindt zich in een map met de naam &quot; `example`&quot; in de hoofdmap van het pakket.
1. Kopieer de volgende mappen van de voorbeeldinstantie naar de twee gedeelde mappen ( `aemsolr1\node1` en `aemsolr2\node2`):

   * `contexts`
   * `etc`
   * `lib`
   * `resources`
   * `scripts`
   * `solr-webapp`
   * `webapps`
   * `start.jar`

1. Een map maken met de naam &quot; `cfg`&quot; in elk van de twee gedeelde mappen.
1. Plaats uw Solr en Zookeeper configuratiedossiers in nieuw gecreeerd `cfg` mappen.

   >[!NOTE]
   >
   >Voor meer informatie over de configuratie Solr en ZooKeeper, raadpleeg [Solr Configuration-documentatie](https://cwiki.apache.org/confluence/display/solr/ConfiguringSolr) en de [Aan de slag met ZooKeeper](https://zookeeper.apache.org/doc/r3.1.2/zookeeperStarted.html).

1. Begin de eerste shard met steun ZooKeeper door naar `aemsolr1\node1` en het uitvoeren van de volgende opdracht:

   ```xml
   java -Xmx2g -Dbootstrap_confdir=./cfg/oak/conf -Dcollection.configName=myconf -DzkRun -DnumShards=2 -jar start.jar
   ```

1. De tweede delen starten door naar `aemsolr2\node2` en het uitvoeren van de volgende opdracht:

   ```xml
   java -Xmx2g -Djetty.port=7574 -DzkHost=localhost:9983 -jar start.jar
   ```

1. Nadat beide kaarten zijn begonnen, test dat alles in werking is door met de Solr interface bij te verbinden `http://localhost:8983/solr/#/`
1. AEM starten en naar de webconsole gaan op `http://localhost:4502/system/console/configMgr`
1. Stel de volgende configuratie in onder **Configuratie externe server van Oak Solr**:

   * HTTP-URL kiezen: `http://localhost:8983/solr/`

1. Kies **Externe zonne-energie** in de vervolgkeuzelijst onder **Eak Solr** serverprovider.

1. Ga naar CRXDE en login als Admin.
1. Een knooppunt maken met de naam **solrIndex** krachtens **eiken:index** en stel de volgende eigenschappen in:

   * **type:** solr (van het type String)
   * **async:** async (van het type String)
   * **redex:** true (van het type Boolean)

1. Sla de wijzigingen op.

#### Aanbevolen configuratie voor Solr {#recommended-configuration-for-solr}

Hieronder is een voorbeeld van een basisconfiguratie die met alle drie plaatsingen kan worden gebruikt Solr die in dit artikel worden beschreven. Het past de specifieke bezitsindexen aan die reeds in AEM aanwezig zijn; gebruik niet met andere toepassingen.

Om het behoorlijk te gebruiken, moet u de inhoud van het archief in de Solr Folder van het Huis direct plaatsen. Als er multi-knoopplaatsingen zijn, zou het direct onder de wortelomslag van elke knoop moeten gaan.

Aanbevolen Solr-configuratiebestanden

[Bestand ophalen](assets/recommended-conf.zip)

### Gereedschappen voor AEM indexeren {#aem-indexing-tools}

AEM 6.1 integreert ook twee indexerende hulpmiddelen in AEM 6.0 als deel van de Adobe Consulting Services Commons toolset:

1. **Query uitvoeren**, een hulpmiddel dat wordt ontworpen om beheerders te helpen begrijpen hoe de vragen worden uitgevoerd;
1. **Indexbeheer voor onak**, een gebruikersinterface voor het onderhouden van bestaande indexen.

Je kunt ze nu bereiken door naar **Gereedschappen - Bewerkingen - Dashboard - Diagnose** in het welkomstscherm AEM.

Zie voor meer informatie over het gebruik ervan de [Documentatie van het operatiedashboard](/help/sites-administering/operations-dashboard.md).

#### Eigenschapindexen maken met OSGi {#creating-property-indexes-via-osgi}

Het ACS-gemeenschappelijke pakket stelt ook configuraties OSGi bloot die kunnen worden gebruikt om bezitsindexen tot stand te brengen.

U kunt het van de Console van het Web toegang hebben door &quot;**Onjuiste eigenschappenindex**&quot;.

![chlimage_1-150](assets/chlimage_1-150.png)

### Problemen met indexering oplossen {#troubleshooting-indexing-issues}

Er kunnen zich situaties voordoen waarbij het uitvoeren van query&#39;s veel tijd in beslag neemt en de algemene responstijd van het systeem veel tijd in beslag neemt.

In dit deel wordt een aantal aanbevelingen gedaan over wat er moet gebeuren om de oorzaak van dergelijke problemen op te sporen en wordt advies gegeven over hoe deze problemen kunnen worden opgelost.

#### Foutopsporingsinfo voorbereiden voor analyse {#preparing-debugging-info-for-analysis}

De gemakkelijkste manier om de vereiste informatie voor de vraag te krijgen die door als [Het gereedschap Query uitvoeren](/help/sites-administering/operations-dashboard.md#explain-query). Dit laat u de nauwkeurige informatie verzamelen die nodig is om een langzame vraag te zuiveren zonder de behoefte om de informatie van het logboekniveau te raadplegen. Dit is wenselijk als u de vraag kent die wordt gezuiverd.

Als dit om welke reden dan ook niet mogelijk is, kunt u de indexerende logboeken in één enkel dossier verzamelen en het gebruiken om uw bepaald probleem problemen op te lossen.

#### Logboekregistratie inschakelen {#enable-logging}

Om registreren toe te laten, moet u toelaten **DEBUG** niveaulogboeken voor de categorieën die betrekking hebben op het indexeren van eikels en vragen. Deze categorieën zijn:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

De **com.day.cq.search** de categorie is slechts van toepassing als u het AEM verstrekte nut QueryBuilder gebruikt.

>[!NOTE]
>
>Het is belangrijk dat de logboeken slechts aan DEBUG voor de duur worden geplaatst de vraag u wilt problemen oplossen in werking wordt gesteld. Anders worden veel gebeurtenissen in de loop van de tijd gegenereerd in de logboeken. Wegens dit, zodra de vereiste logboeken worden verzameld schakelaar terug naar het niveau INFO registreren voor de bovengenoemde categorieën.

U kunt registreren toelaten door deze procedure te volgen:

1. Wijs uw browser aan `https://serveraddress:port/system/console/slinglog`
1. Klik op de knop **Nieuwe logboekregistratie toevoegen** in het onderste gedeelte van de console.
1. Voeg de bovenstaande categorieën toe aan de zojuist gemaakte rij. U kunt de **+** teken om meer dan één categorie aan één registreerapparaat toe te voegen.
1. Kies **DEBUG** van de **Logboekniveau** vervolgkeuzelijst.
1. Het uitvoerbestand instellen op `logs/queryDebug.log`. Hiermee worden alle DEBUG-gebeurtenissen samengevoegd in één logbestand.
1. Voer de query uit of geef de pagina weer die de query gebruikt die u wilt debuggen.
1. Zodra u de vraag hebt uitgevoerd, ga terug naar de registrerenconsole en verander het logboekniveau van pas gecreeerd registreerapparaat in **INFO**.

#### Indexconfiguratie {#index-configuration}

De manier de vraag wordt geëvalueerd wordt grotendeels beïnvloed door de indexconfiguratie. Het is belangrijk dat de indexconfiguratie wordt geanalyseerd of naar ondersteuning wordt gestuurd. U kunt de configuratie ophalen als een inhoudspakket of een JSON-uitvoering ophalen.

Gewoonlijk, wordt de het indexeren configuratie opgeslagen onder `/oak:index` in CRXDE kunt u de JSON-versie ophalen op:

`https://serveraddress:port/oak:index.tidy.-1.json`

Als de index op een andere plaats wordt gevormd, verander dienovereenkomstig de weg.

#### MBean-uitvoer {#mbean-output}

Soms is het nuttig om de output van op index betrekking hebbende MBans voor het zuiveren te verstrekken. U kunt dit doen door:

1. Ga naar de JMX-console op:
   `https://serveraddress:port/system/console/jmx`

1. Zoek naar de volgende MBans:

   * Lucene Index statistische gegevens
   * CopyOnRead-ondersteuningsstatistieken
   * Query-statistieken voor onak
   * IndexStats

1. Klik elk van de MBans zodat kunt u prestatiesstatistieken krijgen. Maak een schermafbeelding of noteer deze voor het geval dat een supportverzending nodig is.

U kunt de variant JSON van deze statistieken bij volgende URLs ook krijgen:

* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`

U kunt ook geconsolideerde JMX-uitvoer leveren via `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak.tidy.3.json`. Dit zou alle aan eik gerelateerde MBean-gegevens in JSON-indeling bevatten.

#### Overige details {#other-details}

U kunt extra details verzamelen helpen het probleem oplossen, zoals:

1. De eik-versie waarop de instantie wordt uitgevoerd. U kunt dit zien door CRXDE te openen en de versie in de rechterbenedenhoek van de welkomstpagina te bekijken, of door de versie van de `org.apache.jackrabbit.oak-core` bundel.
1. De Foutopsporingsoutput QueryBuilder van de lastige vraag. De debugger kan worden betreden bij: `https://serveraddress:port/libs/cq/search/content/querydebug.html`
