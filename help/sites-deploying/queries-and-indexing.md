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
>Dit artikel gaat over het vormen van indexen in AEM 6. Voor beste praktijken bij het optimaliseren van vraag en het indexeren prestaties, zie [ Beste praktijken voor Vragen en het Indexeren ](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

## Inleiding {#introduction}

In tegenstelling tot Jackrabbit 2 indexeert Oak inhoud niet standaard. Aangepaste indexen moeten zo nodig worden gemaakt, net als bij traditionele relationele databases. Als er geen index voor een specifieke vraag is, worden vele knopen misschien overgestoken. De query werkt mogelijk nog wel, maar het is waarschijnlijk traag.

Als Oak een query zonder index tegenkomt, wordt een logbericht op WARN-niveau afgedrukt:

```xml
*WARN* Traversed 1000 nodes with filter Filter(query=select ...) consider creating an index or changing the query
```

## Ondersteunde querytalen {#supported-query-languages}

De Oak-query-engine ondersteunt de volgende talen:

* XPath (aanbevolen)
* SQL-2
* SQL (vervangen)
* JQOM

## Indexeertypen en kostenberekening {#indexer-types-and-cost-calculation}

Met de op Apache Oak gebaseerde backend kunnen verschillende indexen op de repository worden aangesloten.

Één indexeerder is de **Index van het Bezit**, waarvoor de indexdefinitie in de bewaarplaats zelf wordt opgeslagen.

De uitvoeringen voor **Lucene van Apache** en **zonne** zijn ook beschikbaar door gebrek, die allebei fullText indexeren steunen.

De **Traversal Index** wordt gebruikt als geen andere indexeerder beschikbaar is. Dit betekent dat de inhoud niet wordt geïndexeerd en de inhoudsknopen worden getransformeerd om gelijken aan de vraag te vinden.

Als de veelvoudige indexeerders voor een vraag beschikbaar zijn, schat elke beschikbare indexeerder de kosten om de vraag uit te voeren. Oak kiest vervolgens de index met de laagste geschatte kosten.

![ chlimage_1-148 ](assets/chlimage_1-148.png)

Het bovenstaande diagram is een weergave op hoog niveau van het mechanisme voor het uitvoeren van query&#39;s van Apache Oak.

Eerst, wordt de vraag ontleed in een Abstracte Boom van de Syntaxis. Dan, wordt de vraag gecontroleerd en in SQL-2 omgezet die de inheemse taal voor de vragen van Oak is.

Daarna, wordt elke index geraadpleegd om de kosten voor de vraag te schatten. Zodra dat wordt voltooid, worden de resultaten van de goedkoopste index teruggewonnen. Tot slot worden de resultaten gefilterd, zowel om ervoor te zorgen dat de huidige gebruiker toegang tot het resultaat heeft gelezen en dat het resultaat de volledige vraag aanpast.

## De indexen configureren {#configuring-the-indexes}

>[!NOTE]
>
>Voor een grote opslagplaats is het bouwen van een index een tijdrovende bewerking. Dit geldt zowel voor het eerste ontwerp van een index als voor het opnieuw indexeren (het opnieuw samenstellen van een index nadat de definitie is gewijzigd). Zie ook [ Indexen van Oak van het Oplossen van problemen ](/help/sites-deploying/troubleshooting-oak-indexes.md) en [ Preventing Trage het opnieuw indexeren ](/help/sites-deploying/troubleshooting-oak-indexes.md#preventing-slow-re-indexing).

Als herindexering nodig is in grote opslagruimten, met name bij gebruik van MongoDB en voor full-text indexen, kunt u de tekst vooraf extraheren en eekuitvoering gebruiken om de eerste index te genereren en opnieuw te indexeren.

De indexen worden gevormd als knopen in de bewaarplaats onder **Oak:index** knoop.

Het type van de indexknoop moet **zijn:QueryIndexDefinition.** Voor elke index zijn diverse configuratieopties beschikbaar als knoopeigenschappen. Voor meer informatie, zie de configuratiedetails voor elk hieronder indexeertype.

### De eigenschappenindex {#the-property-index}

De index van het Bezit is nuttig voor vragen die bezitsbeperkingen hebben maar niet full-text zijn. Het kan worden gevormd door de hieronder procedure te volgen:

1. CRXDE openen via `http://localhost:4502/crx/de/index.jsp`
1. Creeer een knoop onder **eik:index**
1. Noem de knoop **PropertyIndex**, en plaats het knooptype aan **eak:QueryIndexDefinition**
1. Stel de volgende eigenschappen in voor het nieuwe knooppunt:

   * **type:** `property` (van typeKoord)
   * **propertyNames:** `jcr:uuid` (van typeNaam)

   In dit voorbeeld wordt de eigenschap `jcr:uuid` geïndexeerd. De functie hiervan is om de universeel unieke id (UUID) weer te geven van het knooppunt waaraan de eigenschap is gekoppeld.

1. Sla de wijzigingen op.

De index van het Bezit heeft de volgende configuratieopties:

* Het **type** bezit specificeert het type van index, en in dit geval moet het aan **bezit** worden geplaatst

* Het **propertyNames** bezit wijst op de lijst van de eigenschappen die in de index worden opgeslagen. Als de naam van het knooppunt ontbreekt, wordt deze gebruikt als een verwijzingswaarde voor de eigenschapnaam. In dit voorbeeld, wordt het **jcr:uuid** bezit de waarvan baan het unieke herkenningsteken (UUID) van zijn knoop moet blootstellen toegevoegd aan de index.

* De **unieke** vlag die, als reeks aan **waar** een uniqueness beperking op de bezitsindex toevoegt.

* Het **declaringNodeTypes** bezit laat u een bepaald knooptype specificeren dat de index slechts op van toepassing is.
* De **herdex** vlag die als reeks aan **waar**, een volledige inhoudsherdex teweegbrengt.

### De geordende index {#the-ordered-index}

De geordende index is een uitbreiding van de index van het Bezit. Het is echter afgekeurd. De indexen van dit type moeten met de [ Index van het Bezit van Lucene ](#the-lucene-property-index) worden vervangen.

### De index van volledige tekst met Lucene {#the-lucene-full-text-index}

Een volledige tekstindexeerfunctie op basis van Apache Lucene is beschikbaar in AEM 6.

Als een full-text index wordt gevormd, gebruiken alle vragen die een full-text voorwaarde hebben de full-text index, geen kwestie als er andere voorwaarden zijn die worden geïndexeerd, en geen kwestie als er een wegbeperking is.

Als geen full-text index wordt gevormd, dan werken de vragen met full-text voorwaarden niet zoals verwacht.

Omdat de index wordt bijgewerkt door middel van een asynchrone achtergrondthread, zijn sommige full-text onderzoeken niet beschikbaar voor een klein venster van tijd tot de achtergrondprocessen worden gebeëindigd.

U kunt een volledig-tekstindex van Lucene vormen door de hieronder procedure te volgen:

1. Open CRXDE en creeer een knoop onder **eiken:index**.
1. Noem de knoop **LuceneIndex** en plaats het knooptype aan **eak:QueryIndexDefinition**
1. Voeg de volgende eigenschappen toe aan het knooppunt:

   * **type:** `lucene` (van typeKoord)
   * **async:** `async` (van typeKoord)

1. Sla de wijzigingen op.

De index van Lucene heeft de volgende configuratieopties:

* Het **type** bezit dat het type van index specificeert moet aan **lucene** worden geplaatst
* Het **async** bezit dat aan **async** moet worden geplaatst. Hiermee wordt het indexupdateproces naar een achtergrondthread verzonden.
* Het **includePropertyTypes** bezit, dat bepaalt welke ondergroep van bezitstypes inbegrepen in de index zijn.
* Het **excludePropertyNames** bezit dat een lijst van bezitsnamen - eigenschappen bepaalt die van de index zouden moeten worden uitgesloten.
* De **herdex** vlag die wanneer geplaatst aan **waar**, een volledige inhoudsherdex teweegbrengt.

### Volledige tekst zoeken {#understanding-fulltext-search}

De documentatie in deze sectie is op Apache Lucene, Elasticsearch, en fullText indexen van PostSQL, SQLite, en MySQL, bijvoorbeeld van toepassing. Het volgende voorbeeld is voor AEM / Oak / Lucene.

<b> Te indexeren Gegevens </b>

Het uitgangspunt is de gegevens die moeten worden geïndexeerd. Neem bijvoorbeeld de volgende documenten:

| <b> identiteitskaart van het Document </b> | <b> Weg </b> | <b> Fulltext </b> |
| --- | --- | --- |
| 100 | /content/rubik | &quot;Rubik is een Fins merk.&quot; |
| 200 | /content/rubiksCube | &quot;De Rubiks kubus werd uitgevonden in 1974.&quot; |
| 300 | /content/cube | &quot;Een kubus is een driedimensionaal object.&quot; |


<b> Omgekeerde index </b>

Het indexeringsmechanisme verdeelt de volledige tekst in woorden genoemd &quot;tokens&quot;, en bouwt een index genoemd &quot;omgekeerde index&quot;. Deze index bevat de lijst met documenten waarin deze voor elk woord wordt weergegeven.

Korte, algemene woorden (ook wel &quot;stopwords&quot; genoemd) worden niet geïndexeerd. Alle tokens worden omgezet in kleine letters en stammen wordt toegepast.

Speciale karakters zoals *&quot;-&quot;* worden niet geïndexeerd.

| <b> Symbolisch </b> | <b> Document IDs </b> |
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

<b> zoekend </b>

Hieronder ziet u een voorbeeld van een query. Merk op dat alle speciale karakters (zoals *&quot;*) met een ruimte werden vervangen:

```
/jcr:root/content//element(\*; cq:Page)`[` jcr:contains('Rubik s Cube')`]`
```

De woorden worden op dezelfde manier verdeeld en gefilterd als bij het indexeren (woorden van één teken worden bijvoorbeeld verwijderd). In dit geval wordt gezocht naar:

```
+:fulltext:rubik +:fulltext:cube
```

De index raadpleegt de lijst met documenten voor die woorden. Als er veel documenten zijn, kan de lijst groot zijn. Stel bijvoorbeeld dat ze het volgende bevatten:


| <b> Symbolisch </b> | <b> Document IDs </b> |
| --- | --- |
| rubik | 10, 100, 200, 1000 |
| kubus | 30, 200, 300, 2000 |


Luceen draait heen en weer tussen de twee lijsten (of ronde-robin `n` lijsten, wanneer het zoeken naar `n` woorden):

* Lees in de &quot;rubik&quot; krijgt de eerste vermelding: er zijn er 10.
* Lees in de &#39;kubus&#39; krijgt de eerste vermelding `>` = 10. 10 is niet gevonden, de volgende is 30.
* Lees in het &quot;rubik&quot; krijgt de eerste vermelding `>` = 30: 100.
* Lees in de &#39;kubus&#39; krijgt de eerste vermelding `>` = 100: er wordt 200 gevonden.
* Lees in het rubik krijgt de eerste vermelding `>` = 200. 200 is gevonden. Document 200 is dus een overeenkomst voor beide termen. Dit wordt onthouden.
* Lees in het &quot;rubik&quot; krijgt de volgende vermelding: 1000.
* Lees in de &quot;kubus&quot; krijgt de eerste vermelding `>` = 1000: vindt 2000.
* Lees in het rubik krijgt de eerste vermelding `>` = 2000: einde van de lijst.
* Tot slot kunt u ophouden met zoeken.

Het enige gevonden document dat beide termen bevat, is 200, zoals in het onderstaande voorbeeld:

| 200 | /content/rubiksCube | &quot;De Rubiks kubus werd uitgevonden in 1974.&quot; |
| --- | --- | --- |

Wanneer meerdere items worden gevonden, worden deze op score gesorteerd.

### De index van de eigenschap Lucene {#the-lucene-property-index}

Sinds **Oak 1.0.8**, kan Lucene worden gebruikt om indexen tot stand te brengen die bezitsbeperkingen impliceren die niet full-text zijn.

Om een Index van het Bezit van Lucene te bereiken, moet het **fulltextEnabled** bezit altijd aan vals worden geplaatst.

Neem de volgende voorbeeldvraag:

```xml
select * from [nt:base] where [alias] = '/admin'
```

Om een Index van het Bezit van Lucene voor de bovengenoemde vraag te bepalen, kunt u de volgende definitie toevoegen door een knoop onder **`oak:index`te creëren:**

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
>Voor specifiekere informatie over de Index van het Bezit van Lucene, zie [ Apache Jackrabbit Oak Lucene documentatiepagina ](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Luceenanalysatoren {#lucene-analyzers}

Sinds versie 1.2.0 ondersteunt Oak Lucene-analysatoren.

Analyzers worden zowel gebruikt wanneer een document, als bij vraagtijd wordt geïndexeerd. Een analysator controleert de tekst van gebieden en produceert een symbolische stroom. Luceenanalysatoren bestaan uit een reeks tokenizer- en filterklassen.

De analysatoren kunnen worden geconfigureerd via het knooppunt `analyzers` (van het type `nt:unstructured` ) binnen de definitie `oak:index` .

De standaardanalysator voor een index wordt gevormd in het `default` kind van de analysetknoop.

![ chlimage_1-149 ](assets/chlimage_1-149.png)

>[!NOTE]
>
>Voor een lijst van beschikbare analysatoren, zie de API documentatie van de versie van Lucene u gebruikt.

#### De klasse Analyzer rechtstreeks opgeven {#specifying-the-analyzer-class-directly}

Als u een analysator in de doos wilt gebruiken, kunt u deze configureren volgens de onderstaande procedure:

1. Zoek de index waarmee u de analysator wilt gebruiken onder het knooppunt `oak:index` .

1. Maak onder de index een onderliggend knooppunt met de naam `default` van het type `nt:unstructured` .

1. Voeg een eigenschap toe aan het standaardknooppunt met de volgende eigenschappen:

   * **Naam:** `class`
   * **Type:** `String`
   * **Waarde:** `org.apache.lucene.analysis.standard.StandardAnalyzer`

   De waarde is de naam van de klasse analyzer die u wilt gebruiken.

   U kunt de analysator ook instellen voor gebruik met een specifieke lucene versie door de optionele eigenschap `luceneMatchVersion` string te gebruiken. Een geldige syntaxis voor het gebruiken van het met Lucene 4.7 zou zijn:

   * **Naam:** `luceneMatchVersion`
   * **Type:** `String`
   * **Waarde:** `LUCENE_47`

   Als `luceneMatchVersion` niet wordt verstrekt, gebruikt Oak de versie van Lucene het met wordt verscheept.

1. Als u een stopwoordenbestand wilt toevoegen aan de analysatorconfiguraties, kunt u onder `default` een knooppunt maken met de volgende eigenschappen:

   * **Naam:** `stopwords`
   * **Type:** `nt:file`

#### Analysatoren maken door middel van compositie {#creating-analyzers-via-composition}

Analyzers kunnen ook worden samengesteld op basis van `Tokenizers` , `TokenFilters` en `CharFilters` . U kunt dit doen door een analysator te specificeren en kindknopen van zijn facultatieve tokenizers en filters te creëren die in vermelde orde worden toegepast. Zie ook [ https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema](https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema)

Bekijk deze knooppuntstructuur als voorbeeld:

* **Naam:** `analyzers`

   * **Naam:** `default`

      * **Naam:** `charFilters`
      * **Type:** `nt:unstructured`

         * **Naam:** `HTMLStrip`
         * **Naam:** `Mapping`

      * **Naam:** `tokenizer`

         * **de Naam van het Bezit:** `name`

            * **Type:** `String`
            * **Waarde:** `Standard`

      * **Naam:** `filters`
      * **Type:** `nt:unstructured`

         * **Naam:** `LowerCase`
         * **Naam:** `Stop`

            * **naam van het Bezit:** `words`

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

Voor gevallen zoals het laden van stopwoorden waarbij inhoud van externe bestanden moet worden geladen, kan de inhoud worden opgegeven door een onderliggend knooppunt van het type `nt:file` voor het desbetreffende bestand te maken.

### De zonne-index {#the-solr-index}

Het doel van de index Solr is full-text onderzoek maar het kan ook worden gebruikt om onderzoek door weg, bezitsbeperkingen, en primaire typebeperkingen te indexeren. Dit betekent dat de Solr-index in Oak kan worden gebruikt voor elk type JCR-query.

De integratie in AEM gebeurt op het niveau van de opslagplaats zodat Solr één van de mogelijke indexen is die in Oak kunnen worden gebruikt, de nieuwe opbergingsimplementatie die met AEM wordt verscheept.

Het kan worden gevormd om als verre server met de AEM instantie te werken.

### AEM configureren met één externe Solr-server {#configuring-aem-with-a-single-remote-solr-server}

AEM kan ook worden geconfigureerd om te werken met een externe Solr-serverinstantie:

1. Download en extraheer de nieuwste versie van Solr. Voor meer informatie over hoe te om dit te doen, zie de [ documentatie van de Installatie van Apache Solr ](https://solr.apache.org/guide/6_6/installing-solr.html).
1. Maak nu twee Solr-planken. U kunt dit doen door mappen te maken voor elk segment in de map waarin Solr is uitgepakt:

   * Voor de eerste gedeelde map maakt u de map:

   `<solrunpackdirectory>\aemsolr1\node1`

   * Voor de tweede schijf maakt u de map:

   `<solrunpackdirectory>\aemsolr2\node2`

1. Zoek de voorbeeldinstantie in het Solr-pakket. Deze bevindt zich in de map &quot; `example`&quot; in de hoofdmap van het pakket.
1. Kopieer de volgende mappen van de voorbeeldinstantie naar de twee gedeelde mappen ( `aemsolr1\node1` en `aemsolr2\node2` ):

   * `contexts`
   * `etc`
   * `lib`
   * `resources`
   * `scripts`
   * `solr-webapp`
   * `webapps`
   * `start.jar`

1. Maak in elk van de twee gedeelde mappen een map met de naam &quot; `cfg`&quot;.
1. Plaats uw Solr en Zookeeper configuratiedossiers in de pas gecreëerde `cfg` omslagen.

   >[!NOTE]
   >
   >Voor meer info over de configuratie van Solr en ZooKeeper, raadpleeg de [ documentatie van de Configuratie van Solr ](https://cwiki.apache.org/confluence/display/solr/ConfiguringSolr) en [ ZooKeeper die Begonnen Gids ](https://zookeeper.apache.org/doc/r3.1.2/zookeeperStarted.html) worden.

1. Begin eerste shard met steun ZooKeeper door naar `aemsolr1\node1` te gaan en het volgende bevel in werking te stellen:

   ```xml
   java -Xmx2g -Dbootstrap_confdir=./cfg/oak/conf -Dcollection.configName=myconf -DzkRun -DnumShards=2 -jar start.jar
   ```

1. Start de tweede delen door naar `aemsolr2\node2` te gaan en de volgende opdracht uit te voeren:

   ```xml
   java -Xmx2g -Djetty.port=7574 -DzkHost=localhost:9983 -jar start.jar
   ```

1. Nadat beide kaarten zijn gestart, test u of alles in gebruik is door verbinding te maken met de Solr-interface op `http://localhost:8983/solr/#/`
1. AEM starten en naar de webconsole gaan op `http://localhost:4502/system/console/configMgr`
1. Plaats de volgende configuratie onder **de verre serverconfiguratie van Oak Solr**:

   * Kies HTTP-URL: `http://localhost:8983/solr/`

1. Kies **Verre Solr** in de drop-down lijst onder **Oak Solr** serverleverancier.

1. Ga naar CRXDE en login als Admin.
1. Creeer een knoop genoemd **solrIndex** onder **eik:index**, en plaats de volgende eigenschappen:

   * **type:** solr (van typeKoord)
   * **async:** async (van typeKoord)
   * **herdex:** waar (van type Boolean)

1. Sla de wijzigingen op.

#### Aanbevolen configuratie voor Solr {#recommended-configuration-for-solr}

Hieronder is een voorbeeld van een basisconfiguratie die met alle drie plaatsingen kan worden gebruikt Solr die in dit artikel worden beschreven. Het past de specifieke bezitsindexen aan die reeds in AEM aanwezig zijn; gebruik niet met andere toepassingen.

Om het behoorlijk te gebruiken, moet u de inhoud van het archief in de Solr Folder van het Huis direct plaatsen. Als er multi-knoopplaatsingen zijn, zou het direct onder de wortelomslag van elke knoop moeten gaan.

Aanbevolen Solr-configuratiebestanden

[Bestand ophalen](assets/recommended-conf.zip)

### Gereedschappen voor AEM indexeren {#aem-indexing-tools}

AEM 6.1 integreert ook twee indexerende hulpmiddelen aanwezig in AEM 6.0 als deel van Adobe Consulting Services Commons toolset:

1. **verklaar Vraag**, een hulpmiddel dat wordt ontworpen om beheerders te helpen begrijpen hoe de vragen worden uitgevoerd;
1. **de Manager van de Index van Oak**, een Gebruikersinterface van het Web voor het handhaven van bestaande indexen.

U kunt hen nu bereiken door naar **Hulpmiddelen te gaan - Verrichtingen - Dashboard - Diagnose** van het AEM Welkomstscherm.

Voor meer informatie over hoe te om hen te gebruiken, zie de [ documentatie van het Dashboard van Verrichtingen ](/help/sites-administering/operations-dashboard.md).

#### Eigenschapindexen maken met OSGi {#creating-property-indexes-via-osgi}

Het ACS-gemeenschappelijke pakket stelt ook configuraties OSGi bloot die kunnen worden gebruikt om bezitsindexen tot stand te brengen.

U kunt tot het van de Console van het Web toegang hebben door naar &quot;**te zoeken verzeker de Index van het Bezit van Oak**&quot;.

![ chlimage_1-150 ](assets/chlimage_1-150.png)

### Problemen met indexering oplossen {#troubleshooting-indexing-issues}

Er kunnen zich situaties voordoen waarbij het uitvoeren van query&#39;s veel tijd in beslag neemt en de algemene responstijd van het systeem veel tijd in beslag neemt.

In dit deel wordt een aantal aanbevelingen gedaan over wat er moet gebeuren om de oorzaak van dergelijke problemen op te sporen en wordt advies gegeven over hoe deze problemen kunnen worden opgelost.

#### Foutopsporingsinfo voorbereiden voor analyse {#preparing-debugging-info-for-analysis}

De gemakkelijkste manier om de vereiste informatie voor de vraag te krijgen die in werking wordt gesteld is als [ verklaart het hulpmiddel van de Vraag ](/help/sites-administering/operations-dashboard.md#explain-query). Dit laat u de nauwkeurige informatie verzamelen die nodig is om een langzame vraag te zuiveren zonder de behoefte om de informatie van het logboekniveau te raadplegen. Dit is wenselijk als u de vraag kent die wordt gezuiverd.

Als dit om welke reden dan ook niet mogelijk is, kunt u de indexerende logboeken in één enkel dossier verzamelen en het gebruiken om uw bepaald probleem problemen op te lossen.

#### Logboekregistratie inschakelen {#enable-logging}

Om registreren toe te laten, moet u **DEBUG** niveaulogboeken voor de categorieën toelaten die betrekking hebben op Oak indexeren en vragen. Deze categorieën zijn:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

De **com.day.cq.search** categorie is slechts van toepassing als u het AEM verstrekte nut QueryBuilder gebruikt.

>[!NOTE]
>
>Het is belangrijk dat de logboeken slechts aan DEBUG voor de duur worden geplaatst de vraag u wilt problemen oplossen in werking wordt gesteld. Anders worden veel gebeurtenissen in de loop van de tijd gegenereerd in de logboeken. Wegens dit, zodra de vereiste logboeken worden verzameld schakelaar terug naar het niveau INFO registreren voor de bovengenoemde categorieën.

U kunt registreren toelaten door deze procedure te volgen:

1. De browser naar `https://serveraddress:port/system/console/slinglog` verwijzen
1. Klik **toevoegen nieuwe Logger** knoop in het lagere deel van de console.
1. Voeg de bovenstaande categorieën toe aan de zojuist gemaakte rij. U kunt het **+** teken gebruiken om meer dan één categorie aan één enkel registreerapparaat toe te voegen.
1. Kies **DEBUG** van het **niveau van het Logboek** drop-down lijst.
1. Stel het uitvoerbestand in op `logs/queryDebug.log` . Hiermee worden alle DEBUG-gebeurtenissen samengevoegd in één logbestand.
1. Voer de query uit of geef de pagina weer die de query gebruikt die u wilt debuggen.
1. Zodra u de vraag hebt uitgevoerd, ga terug naar de registrerenconsole en verander het logboekniveau van pas gecreëerde registreerapparaat in **INFO**.

#### Indexconfiguratie {#index-configuration}

De manier de vraag wordt geëvalueerd wordt grotendeels beïnvloed door de indexconfiguratie. Het is belangrijk dat de indexconfiguratie wordt geanalyseerd of naar ondersteuning wordt gestuurd. U kunt de configuratie ophalen als een inhoudspakket of een JSON-uitvoering ophalen.

Gewoonlijk, wordt de het indexeren configuratie opgeslagen onder de `/oak:index` knoop in CRXDE, kunt u de versie JSON bij krijgen:

`https://serveraddress:port/oak:index.tidy.-1.json`

Als de index op een andere plaats wordt gevormd, verander dienovereenkomstig de weg.

#### MBean-uitvoer {#mbean-output}

Soms is het nuttig om de output van op index betrekking hebbende MBans voor het zuiveren te verstrekken. U kunt dit doen door:

1. Ga naar de JMX-console op:
   `https://serveraddress:port/system/console/jmx`

1. Zoek naar de volgende MBans:

   * Lucene Index statistische gegevens
   * CopyOnRead-ondersteuningsstatistieken
   * Oak Query Statistics
   * IndexStats

1. Klik elk van de MBans zodat kunt u prestatiesstatistieken krijgen. Maak een schermafbeelding of noteer deze voor het geval dat een supportverzending nodig is.

U kunt de variant JSON van deze statistieken bij volgende URLs ook krijgen:

* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`

U kunt ook geconsolideerde JMX-uitvoer leveren via `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak.tidy.3.json` . Dit omvat alle Oak-gerelateerde MBean-gegevens in JSON-indeling.

#### Overige details {#other-details}

U kunt extra details verzamelen helpen het probleem oplossen, zoals:

1. De Oak-versie waarop uw exemplaar wordt uitgevoerd. U kunt dit zien door CRXDE te openen en de versie in de rechterbenedenhoek van de welkomstpagina te bekijken, of door de versie van de `org.apache.jackrabbit.oak-core` -bundel te controleren.
1. De Foutopsporingsoutput QueryBuilder van de lastige vraag. De foutopsporing is toegankelijk via: `https://serveraddress:port/libs/cq/search/content/querydebug.html`
