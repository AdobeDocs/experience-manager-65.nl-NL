---
title: Oak-query's en indexering
seo-title: Oak-query's en indexering
description: Leer hoe u indexen in AEM configureert.
seo-description: Leer hoe u indexen in AEM configureert.
uuid: a1233d2e-1320-43e0-9b18-cd6d1eeaad59
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 492741d5-8d2b-4a81-8f21-e621ef3ee685
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/queries-and-indexing
translation-type: tm+mt
source-git-commit: b01f6d3726fd6aa06ffedaf10dfde9526479a2a3
workflow-type: tm+mt
source-wordcount: '2880'
ht-degree: 0%

---


# Oak-query&#39;s en indexering{#oak-queries-and-indexing}

>[!NOTE]
>
>Dit artikel gaat over het vormen van indexen in AEM 6. Voor beste praktijken bij het optimaliseren van vraag en het indexeren prestaties, zie [Beste praktijken voor Vragen en het Indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

## Inleiding {#introduction}

In tegenstelling tot Jackrabbit 2 indexeert eik inhoud niet standaard. Aangepaste indexen moeten waar nodig worden gemaakt, net als bij traditionele relationele databases. Als er geen index voor een specifieke vraag is, misschien zullen vele knopen worden gepasseerd. De query werkt mogelijk nog wel, maar is waarschijnlijk erg traag.

Als het Eak een vraag zonder een index ontmoet, wordt een bericht van het het niveaulogboek van WARN gedrukt:

```xml
*WARN* Traversed 1000 nodes with filter Filter(query=select ...) consider creating an index or changing the query
```

## Ondersteunde querytalen {#supported-query-languages}

De oak-query-engine ondersteunt de volgende talen:

* XPath (aanbevolen)
* SQL-2
* SQL (afgekeurd)
* JQOM

## Indexeertypen en kostenberekening {#indexer-types-and-cost-calculation}

Met de op Apache Oak gebaseerde backend kunnen verschillende indexen in de repository worden aangesloten.

Eén index is de **eigenschappenindex**, waarvoor de indexdefinitie wordt opgeslagen in de opslagplaats zelf.

Implementaties voor **Apache Lucene** en **Solr** zijn ook standaard beschikbaar, die allebei fullText indexing steunen.

De **traversal-index** wordt gebruikt als er geen andere index beschikbaar is. Dit betekent dat de inhoud niet wordt geïndexeerd en de inhoudsknopen worden getransformeerd om gelijken aan de vraag te vinden.

Als de veelvoudige indexeerders voor een vraag beschikbaar zijn, schat elke beschikbare indexeerder de kosten om de vraag uit te voeren. Eak kiest vervolgens de indexeerder met de laagste geschatte kosten.

![chlimage_1-148](assets/chlimage_1-148.png)

Het bovenstaande diagram is een representatie op hoog niveau van het mechanisme voor het uitvoeren van query&#39;s voor Apache Oak.

Eerst, wordt de vraag ontleed in een Abstracte Boom van de Syntaxis. Dan, wordt de vraag gecontroleerd en in SQL-2 getransformeerd die de inheemse taal voor de vragen van het Eak is.

Daarna, wordt elke index geraadpleegd om de kosten voor de vraag te schatten. Zodra dat wordt voltooid, worden de resultaten van de goedkoopste index teruggewonnen. Tot slot worden de resultaten gefilterd, zowel om ervoor te zorgen dat de huidige gebruiker leestoegang tot het resultaat heeft en dat het resultaat de volledige vraag aanpast.

## De indexen configureren {#configuring-the-indexes}

>[!NOTE]
>
>Voor een grote opslagplaats is het bouwen van een index een tijdrovende bewerking. Dit geldt zowel voor het eerste ontwerp van een index als voor het opnieuw indexeren (het opnieuw samenstellen van een index nadat de definitie is gewijzigd). Zie ook [het Oplossen van problemen](/help/sites-deploying/troubleshooting-oak-indexes.md) Oak Indexes en het [Voorkomen van langzaam re-indexeren](/help/sites-deploying/troubleshooting-oak-indexes.md#preventing-slow-re-indexing).

Als herindexering nodig is in zeer grote opslagplaatsen, met name bij gebruik van MongoDB en voor fullText-indexen, kunt u de tekst vooraf extraheren en eekuitvoering gebruiken om de eerste index te genereren en opnieuw te indexeren.

Indexen worden geconfigureerd als knooppunten in de opslagplaats onder het knooppunt **oak:index** .

Het type van de indexknoop moet **eak zijn:QueryIndexDefinition.** Verschillende configuratieopties zijn beschikbaar voor elke index als knoopeigenschappen. Voor meer informatie, zie de configuratiedetails voor elk hieronder indexeertype.

### De eigenschappenindex {#the-property-index}

De index van het Bezit is over het algemeen nuttig voor vragen die bezitsbeperkingen hebben maar niet full-text zijn. Het kan worden gevormd door de hieronder procedure te volgen:

1. CRXDE openen door naar `http://localhost:4502/crx/de/index.jsp`
1. Een nieuw knooppunt maken onder **Eak:index**
1. Geef het knooppunt **PropertyIndex** een naam en stel het knooppunttype in op **eak:QueryIndexDefinition**
1. Stel de volgende eigenschappen in voor het nieuwe knooppunt:

   * **type:**  `property` (van het type String)
   * **propertyNames :**  `jcr:uuid` (van het type Name)
   In dit voorbeeld wordt de `jcr:uuid` eigenschap geïndexeerd, waarvan de taak is om de universeel unieke id (UUID) weer te geven van het knooppunt waaraan deze is gekoppeld.

1. Sla de wijzigingen op.

De index van het Bezit heeft de volgende configuratieopties:

* De eigenschap **type** geeft het type index op en in dit geval moet deze worden ingesteld op **eigenschap**

* De **eigenschap propertyNames** geeft de lijst aan met de eigenschappen die in de index worden opgeslagen. Als het ontbreekt, zal de knoopnaam als waarde van de bezitsnaam van de naam worden gebruikt. In dit voorbeeld wordt de eigenschap **jcr:uuid** , waarvan de taak is om de unieke id (UUID) van het knooppunt beschikbaar te maken, toegevoegd aan de index.

* De **unieke** markering die, als ingesteld op **true** , een unieke restrictie toevoegt aan de eigenschapindex.

* Met de eigenschap **declaringNodeTypes** kunt u een bepaald knooppunttype opgeven waarop de index alleen van toepassing is.
* De **rendex** -markering die, indien ingesteld op **true**, een volledige inhoudsherdex activeert.

### De geordende index {#the-ordered-index}

De geordende index is een uitbreiding van de index van het Bezit. Het is echter afgekeurd. Indexen van dit type moeten met de Index [van het Bezit van](#the-lucene-property-index)Lucene worden vervangen.

### De index van volledige tekst met Lucene {#the-lucene-full-text-index}

Een volledige tekstindex op basis van Apache Lucene is beschikbaar in AEM 6.

Als een full-text index wordt gevormd, dan gebruiken alle vragen die een full-text voorwaarde hebben de full-text index, geen kwestie als er andere voorwaarden zijn die worden geïndexeerd, en geen kwestie als er een wegbeperking is.

Als geen full-text index wordt gevormd, dan zullen de vragen met full-text voorwaarden niet zoals verwacht werken.

Omdat de index via een asynchrone achtergronddraad wordt bijgewerkt, zullen sommige full-text onderzoeken voor een klein venster van tijd niet beschikbaar zijn tot de achtergrondprocessen worden gebeëindigd.

U kunt een volledig-tekstindex van Lucene vormen, door de hieronder procedure te volgen:

1. Open CRXDE en creeer een nieuw knooppunt onder **eikel:index**.
1. Geef het knooppunt **LuceneIndex** een naam en stel het knooppunttype in op **eak:QueryIndexDefinition**
1. Voeg de volgende eigenschappen toe aan het knooppunt:

   * **type:**  `lucene` (van het type String)
   * **async:**  `async` (van het type String)

1. Sla de wijzigingen op.

De index van Lucene heeft de volgende configuratieopties:

* De eigenschap **type** die het type index opgeeft, moet worden ingesteld op **luceen**
* De eigenschap **async** die moet worden ingesteld op **async**. Hiermee wordt het indexupdateproces naar een achtergrondthread verzonden.
* De eigenschap **includePropertyTypes** definieert welke subset van eigenschapstypen in de index wordt opgenomen.
* De eigenschap **excludePropertyNames** definieert een lijst met namen van eigenschappen - eigenschappen die moeten worden uitgesloten van de index.
* De **rendex** -markering die, wanneer ingesteld op **true**, zorgt voor een nieuwe index van de volledige inhoud.

### De index van de eigenschap Lucene {#the-lucene-property-index}

Sinds **Eak 1.0.8**, kan Lucene worden gebruikt om indexen tot stand te brengen die bezitsbeperkingen impliceren die niet full-text zijn.

Om een Index van het Bezit van Lucene te bereiken moet het **fulltextEnabled** bezit altijd aan vals worden geplaatst.

Neem de volgende voorbeeldvraag:

```xml
select * from [nt:base] where [alias] = '/admin'
```

Om een Index van het Bezit van Lucene voor de bovengenoemde vraag te bepalen, kunt u de volgende definitie toevoegen door een nieuwe knoop onder **eikel te creëren:index:**

* **Naam:** `LucenePropertyIndex`
* **Type:** `oak:QueryIndexDefinition`

Voeg de volgende eigenschappen toe wanneer het knooppunt is gemaakt:

* **type:**

   ```
   lucene (of type String)
   ```

* **async:**

   ```
   async (of type String)
   ```

* **fulltextEnabled:**

   ```
   false (of type Boolean)
   ```

* **includePropertyNames:** `["alias"] (of type String)`

>[!NOTE]
>
>In vergelijking met de reguliere eigenschappenindex wordt de index van het Lucene-eigenschap altijd geconfigureerd in de asynchrone modus. De resultaten die door de index worden geretourneerd, weerspiegelen dus mogelijk niet altijd de meest actuele staat van de gegevensopslagruimte.

>[!NOTE]
>
>Voor specifiekere informatie over de Index van het Bezit van Lucene, zie de de documentatiepagina [van het Jasje van de](https://jackrabbit.apache.org/oak/docs/query/lucene.html)Apache Oak Lucene.

### Luceenanalysatoren {#lucene-analyzers}

Sinds versie 1.2.0 ondersteunt eik Lucene-analysatoren.

Analyzers worden zowel gebruikt wanneer een document, als bij vraagtijd wordt geïndexeerd. Een analysator controleert de tekst van gebieden en produceert een symbolische stroom. Luceenanalysatoren bestaan uit een reeks tokenizer- en filterklassen.

De analysatoren kunnen worden geconfigureerd via het `analyzers` knooppunt (van het type `nt:unstructured`) binnen de `oak:index` definitie.

De standaardanalysator voor een index wordt gevormd in het `default` kind van de analysetknoop.

![chlimage_1-149](assets/chlimage_1-149.png)

>[!NOTE]
>
>Raadpleeg de API-documentatie van de Lucene-versie die u gebruikt voor een lijst met beschikbare analysators.

#### De klasse Analyzer rechtstreeks opgeven {#specifying-the-analyzer-class-directly}

Als u een analysator in de doos wilt gebruiken, kunt u deze configureren volgens de onderstaande procedure:

1. Zoek de index waarmee u de analysator wilt gebruiken onder het `oak:index` knooppunt.

1. Maak onder de index een onderliggend knooppunt met de naam `default` van het type `nt:unstructured`.

1. Voeg een eigenschap toe aan het standaardknooppunt met de volgende eigenschappen:

   * **Naam:** `class`
   * **Type:** `String`
   * **Waarde:** `org.apache.lucene.analysis.standard.StandardAnalyzer`
   De waarde is de naam van de klasse Analyzer die u wilt gebruiken.

   U kunt de analysator ook plaatsen om met een specifieke lucene versie te gebruiken door het facultatieve `luceneMatchVersion` koordbezit te gebruiken. Een geldige synthax voor gebruik met Lucene 4.7 zou zijn:

   * **Naam:** `luceneMatchVersion`
   * **Type:** `String`
   * **Waarde:** `LUCENE_47`
   Als `luceneMatchVersion` deze optie niet is opgegeven, zal Oak de versie van Lucene gebruiken die bij het product is meegeleverd.

1. Als u een stopwoordenbestand wilt toevoegen aan de configuraties van de analysator, kunt u een nieuw knooppunt onder het `default` knooppunt maken met de volgende eigenschappen:

   * **Naam:** `stopwords`
   * **Type:** `nt:file`

#### Analysatoren maken via compositie {#creating-analyzers-via-composition}

Analysatoren kunnen ook worden samengesteld op basis van `Tokenizers`, `TokenFilters` en `CharFilters`. U kunt dit doen door een analysator te specificeren en kindknopen van zijn facultatieve tokenizers en filters te creëren die in vermelde orde zullen worden toegepast. Zie ook [https://wiki.apache.org/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema](https://wiki.apache.org/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema)

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





De naam van de filters, charFilters en tokenizers wordt gevormd door de fabrieksachtervoegsels te verwijderen. Aldus:

* `org.apache.lucene.analysis.standard.StandardTokenizerFactory` wordt `standard`

* `org.apache.lucene.analysis.charfilter.MappingCharFilterFactory` wordt `Mapping`

* `org.apache.lucene.analysis.core.StopFilterFactory` wordt `Stop`

Elke configuratieparameter die voor de fabriek vereist is, wordt opgegeven als eigenschap van de desbetreffende code.

Voor gevallen zoals het laden van stopwoorden waarbij inhoud van externe bestanden moet worden geladen, kan de inhoud worden opgegeven door een onderliggend knooppunt van het `nt:file` type voor het bestand in kwestie te maken.

### De zonne-index {#the-solr-index}

Het doel van de Solr-index is voornamelijk zoeken in volledige tekst, maar het kan ook worden gebruikt om zoekopdrachten op pad, eigenschapsbeperkingen en beperkingen van primaire typen te indexeren. Dit betekent de Solr index in Oak voor om het even welk type van vraag JCR kan worden gebruikt.

De integratie in AEM vindt plaats op het niveau van de opslagplaats, zodat Solr een van de mogelijke indexen is die kunnen worden gebruikt in Oak, de nieuwe implementatie van de opslagplaats die met AEM wordt geleverd.

Het kan worden gevormd om als ingebedde server met de instantie van AEM, of als verre server te werken.

### AEM configureren met een ingesloten Solr-server {#configuring-aem-with-an-embedded-solr-server}

>[!CAUTION]
>
>Gebruik geen ingesloten Solr-server in een productieomgeving. Het mag alleen in een ontwikkelingsomgeving worden gebruikt.

AEM kan met een ingebedde server van de Solr worden gebruikt die via de Console van het Web kan worden gevormd. In dit geval wordt de Solr-server uitgevoerd in dezelfde JVM als de AEM-instantie waarin deze is ingesloten.

U kunt de ingesloten Solr-server configureren door:

1. Ga naar de webconsole op `https://serveraddress:4502/system/console/configMgr`
1. Zoek naar &quot;**Oak Solr serverleverancier**&quot;.
1. Druk op de bewerkknop en stel in het volgende venster het servertype in op **Ingesloten Solr** in de vervolgkeuzelijst.

1. Vervolgens bewerkt u &quot;**Ingesloten serverconfiguratie** van eikenhout oplossen&quot; en maakt u een configuratie. Ga naar de [Apache Solr-website](https://lucene.apache.org/solr/documentation.html)voor meer informatie over de configuratieopties.

   >[!NOTE]
   >
   >De configuratie Solr home directory (solr.home.path) zoekt naar een map met dezelfde naam in de AEM-installatiemap.

1. Open CRXDE en meld u aan als Admin.
1. Voeg een knooppunt met de naam **solrlndex** van het type **eak:QueryIndexDefinition** toe onder **eikel:index** met de volgende eigenschappen:

   * **type:** `solr`(van het type String)
   * **async:** `async`(van het type String)
   * **redex:** `true`(van het type Boolean)

1. Sla de wijzigingen op.

### AEM configureren met één externe Solr-server {#configuring-aem-with-a-single-remote-solr-server}

AEM kan ook worden gevormd om met een verre serverinstantie van Solr te werken:

1. Download en extraheer de nieuwste versie van Solr. Raadpleeg de documentatie bij de installatie van [Apache Solr voor meer informatie over hoe u dit kunt doen](https://cwiki.apache.org/confluence/display/solr/Installing+Solr).
1. Maak nu twee Solr-planken. U kunt dit doen door mappen te maken voor elke schijf in de map waarin Solr is geüpload:

   * Voor de eerste gedeelde map maakt u de map:
   `<solrunpackdirectory>\aemsolr1\node1`

   * Voor de tweede schijf maakt u de map:
   `<solrunpackdirectory>\aemsolr2\node2`

1. Zoek de voorbeeldinstantie in het Solr-pakket. De map bevindt zich gewoonlijk in de hoofdmap van het pakket, de map &quot; `example`&quot;.
1. Kopieer de volgende mappen van de voorbeeldinstantie naar de twee gedeelde mappen ( `aemsolr1\node1` en `aemsolr2\node2`):

   * `contexts`
   * `etc`
   * `lib`
   * `resources`
   * `scripts`
   * `solr-webapp`
   * `webapps`
   * `start.jar`

1. Maak in elk van de twee gedeelde mappen een nieuwe map met de naam &quot; `cfg`&quot;.
1. Plaats uw Solr en Zookeeper configuratiedossiers in de pas gecreëerde `cfg` omslagen.

   >[!NOTE]
   >
   >Voor meer informatie over de configuratie van Solr en ZooKeeper, raadpleeg de documentatie [van de Configuratie](https://wiki.apache.org/solr/ConfiguringSolr) Solr en [ZooKeeper die Begonnen Gids](https://zookeeper.apache.org/doc/r3.1.2/zookeeperStarted.html)wordt.

1. Begin eerste shard met steun ZooKeeper door naar het volgende bevel te gaan `aemsolr1\node1` en in werking te stellen:

   ```xml
   java -Xmx2g -Dbootstrap_confdir=./cfg/oak/conf -Dcollection.configName=myconf -DzkRun -DnumShards=2 -jar start.jar
   ```

1. Begin tweede shard door naar het volgende bevel te gaan `aemsolr2\node2` en in werking te stellen:

   ```xml
   java -Xmx2g -Djetty.port=7574 -DzkHost=localhost:9983 -jar start.jar
   ```

1. Nadat beide kaarten zijn begonnen, test dat alles in werking is door met de Solr interface bij te verbinden `http://localhost:8983/solr/#/`
1. AEM starten en naar de webconsole gaan op `http://localhost:4502/system/console/configMgr`
1. Stel de volgende configuratie in bij de externe serverconfiguratie **van** Oak Solr:

   * HTTP-URL kiezen: `http://localhost:8983/solr/`

1. Kies **Verre Solr** in de drop-down lijst onder de **Leverancier van de Server van de Solr** van de Eak.

1. Ga naar CRXDE en meld u aan als Admin.
1. Maak een nieuw knooppunt met de naam **solrIndex** onder **eikel:index** en stel de volgende eigenschappen in:

   * **type:** solr (van het type String)
   * **async:** async (van het type String)
   * **redex:** true (van het type Boolean)

1. Sla de wijzigingen op.

#### Aanbevolen configuratie voor Solr {#recommended-configuration-for-solr}

Hieronder is een voorbeeld van een basisconfiguratie die met alle drie plaatsingen kan worden gebruikt Solr die in dit artikel worden beschreven. De toegewezen eigenschapsindexen die al in AEM aanwezig zijn, worden bij het programma gevoegd en mogen niet met andere toepassingen worden gebruikt.

om het behoorlijk te gebruiken, moet u de inhoud van het archief in de Solr Folder van het Huis direct plaatsen. In het geval van multi-knoopplaatsingen, zou het direct onder de wortelomslag van elke knoop moeten gaan.

Aanbevolen Solr-configuratiebestanden

[Bestand ophalen](assets/recommended-conf.zip)

### AEM-indexgereedschappen {#aem-indexing-tools}

AEM 6.1 integreert ook twee indexeringsgereedschappen in AEM 6.0 als onderdeel van de gemeenschappelijke toolset van Adobe Consulting Services:

1. **Verklaar Vraag**, een hulpmiddel dat wordt ontworpen om beheerders te helpen begrijpen hoe de vragen worden uitgevoerd;
1. **De Manager** van de Index van het eiken, een Gebruikersinterface van het Web voor het handhaven van bestaande indexen.

U kunt deze nu bereiken door naar **Gereedschappen - Bewerkingen - Dashboard - Diagnose** te gaan vanuit het AEM-welkomstscherm.

Raadpleeg de documentatie bij het [vluchthandboek](/help/sites-administering/operations-dashboard.md)voor meer informatie over het gebruik ervan.

#### Eigenschapindexen maken via OSGi {#creating-property-indexes-via-osgi}

Het ACS-gemeenschappelijke pakket stelt ook configuraties OSGi bloot die kunnen worden gebruikt om bezitsindexen tot stand te brengen.

U kunt het van de Console van het Web tot toegang hebben door &quot;te zoeken **verzekeren de Index** van het Bezit van het Eak&quot;.

![chlimage_1-150](assets/chlimage_1-150.png)

### Problemen met indexering oplossen {#troubleshooting-indexing-issues}

Er kunnen zich situaties voordoen waarbij het uitvoeren van query&#39;s veel tijd in beslag neemt en de algemene responstijd van het systeem veel tijd in beslag neemt.

In dit deel wordt een aantal aanbevelingen gedaan over wat er moet gebeuren om de oorzaak van dergelijke kwesties te achterhalen en wordt advies gegeven over hoe deze problemen kunnen worden opgelost.

#### Foutopsporingsinfo voorbereiden voor analyse {#preparing-debugging-info-for-analysis}

De gemakkelijkste manier om vereiste informatie voor de vraag te krijgen die wordt uitgevoerd is via het [Uitdrukkelijke hulpmiddel](/help/sites-administering/operations-dashboard.md#explain-query)van de Vraag. Dit zal u toelaten om de nauwkeurige informatie te verzamelen die nodig is om een langzame vraag te zuiveren zonder de behoefte om de informatie van het logboekniveau te raadplegen. Dit is wenselijk als u de vraag kent die wordt gezuiverd.

Als dit om welke reden dan ook niet mogelijk is, kunt u de indexerende logboeken in één enkel dossier verzamelen en het gebruiken om uw bepaald probleem problemen op te lossen.

#### Logboekregistratie inschakelen {#enable-logging}

Om het registreren toe te laten, moet u **DEBUG** niveaulogboeken voor de categorieën toelaten die op het indexeren van eikel en vragen betrekking hebben. Deze categorieën zijn:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

De categorie **com.day.cq.search** is alleen van toepassing als u het AEM-hulpprogramma dat u hebt opgegeven, gebruikt.

>[!NOTE]
>
>Het is belangrijk dat de logboeken slechts aan DEBUG voor de duur worden geplaatst de vraag u wilt problemen oplossen wordt uitgevoerd, anders zal een grote hoeveelheid gebeurtenissen in de logboeken in tijd worden geproduceerd. Wegens dit, zodra de vereiste logboeken worden verzameld schakelaar terug naar het niveau INFO registreren voor de bovengenoemde categorieën.

U kunt registreren toelaten door deze procedure te volgen:

1. Wijs uw browser aan `https://serveraddress:port/system/console/slinglog`
1. Klik de **Add nieuwe knoop van het Logboek** in het lagere deel van de console.
1. Voeg de bovenstaande categorieën toe aan de zojuist gemaakte rij. Met het **+** -teken kunt u meerdere categorieën toevoegen aan één logger.
1. Kies **DEBUG** in de vervolgkeuzelijst **Logniveau** .
1. Stel het uitvoerbestand in op `logs/queryDebug.log`. Hierdoor worden alle DEBUG-gebeurtenissen samengevoegd tot één logbestand.
1. Voer de query uit of geef de pagina weer die de query gebruikt die u wilt debuggen.
1. Zodra u de vraag hebt uitgevoerd, ga terug naar de registrerenconsole en verander het logboekniveau van nieuw gecreeerd registreerapparaat in **INFO**.

#### Indexconfiguratie {#index-configuration}

De manier de vraag wordt geëvalueerd wordt grotendeels beïnvloed door de indexconfiguratie. Het is belangrijk om de indexconfiguratie te krijgen om worden geanalyseerd of naar steun worden verzonden. U kunt de configuratie ophalen als een inhoudspakket of een JSON-uitvoering ophalen.

Aangezien in de meeste gevallen, de het indexeren configuratie onder de `/oak:index` knoop in CRXDE wordt opgeslagen, kunt u de versie JSON bij krijgen:

`https://serveraddress:port/oak:index.tidy.-1.json`

Als de index op een andere plaats wordt gevormd, verander dienovereenkomstig de weg.

#### MBean-uitvoer {#mbean-output}

In sommige gevallen is het nuttig om de output van index verwante MBans voor het zuiveren te verstrekken. U kunt dit doen door:

1. Ga naar de JMX-console op:
   `https://serveraddress:port/system/console/jmx`

1. Zoek naar de volgende MBans:

   * Lucene Index statistische gegevens
   * CopyOnRead-ondersteuningsstatistieken
   * Query-statistieken voor onak
   * IndexStats

1. Klik elk van de netten MB om de prestatiesstatistieken te krijgen. Maak een schermafbeelding of noteer deze als verzending ter ondersteuning vereist is.

U kunt de variant JSON van deze statistieken bij volgende URLs ook krijgen:

* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`

U kunt ook geconsolideerde JMX-uitvoer opgeven via `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak.tidy.3.json`. Dit zou alle aan eik gerelateerde MBean-gegevens in JSON-indeling bevatten.

#### Overige details {#other-details}

U kunt extra details verzamelen helpen het probleem oplossen, zoals:

1. De eikversie waarop uw instantie wordt uitgevoerd. U kunt dit zien door CRXDE te openen en de versie in de lagere juiste hoek van de welkomstpagina te bekijken, of door de versie van de `org.apache.jackrabbit.oak-core` bundel te controleren.
1. De Foutopsporingsoutput QueryBuilder van de lastige vraag. De debugger kan worden betreden bij: `https://serveraddress:port/libs/cq/search/content/querydebug.html`

