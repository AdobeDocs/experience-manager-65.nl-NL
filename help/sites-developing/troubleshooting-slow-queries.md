---
title: Problemen met trage query's oplossen
description: Leer hoe u in Adobe Experience Manager trage query's kunt oplossen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 3405cdd3-3d1b-414d-9931-b7d7b63f0a6f
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2237'
ht-degree: 0%

---

# Problemen met trage query&#39;s oplossen{#troubleshooting-slow-queries}

## Trage query-classificaties {#slow-query-classifications}

Er zijn drie belangrijke classificaties van langzame vragen in AEM, die door strengheid worden vermeld:

1. **index-minder vragen**

   * De vragen die **&#x200B;**&#x200B;niet oplossen aan een index en de inhoud van JCR doorlopen om resultaten te verzamelen

1. **Poortelijk beperkte (of scoped) vragen**

   * Vragen die tot een index worden opgelost, maar alle indexitems moeten doorlopen om resultaten te verzamelen

1. **Grote vraag van de resultaatreeks**

   * Zoekopdrachten die een groot aantal resultaten opleveren

De eerste twee classificaties van query&#39;s (indexloos en slecht beperkt) zijn traag. Zij zijn langzaam omdat zij de de vraagmotor van Oak dwingen om elk **potentieel** resultaat (inhoudsknoop of indexingang) te inspecteren om te identificeren welke in de **daadwerkelijke** resultaatreeks behoren.

Het inspecteren van elk mogelijk resultaat is de zogenaamde &quot;Traversing&quot;.

Aangezien elk potentieel resultaat moet worden geïnspecteerd, stijgen de kosten om de daadwerkelijke resultaatreeks te bepalen lineair met het aantal potentiële resultaten.

Door querybeperkingen en tuning-indexen toe te voegen, kunnen de indexgegevens worden opgeslagen in een geoptimaliseerde indeling die snelle resultaten ophaalt en, vermindert of verwijdert u de behoefte aan lineaire inspectie van potentiële resultaatsets.

In AEM 6.3, door gebrek, wanneer een traversal van 100.000 wordt bereikt, ontbreekt de vraag en werpt een uitzondering. Deze grens bestaat niet door gebrek in AEM versies vóór AEM 6.3, maar kan via de Montages OSGi van de Motor van de Vraag van het Jasje van Apache worden geplaatst van de Motor en van QueryEngineSettings JMX boon (bezit LimitReads).

### Vragen zonder index detecteren {#detecting-index-less-queries}

#### Tijdens de ontwikkeling {#during-development}

Verklaar **alle** vragen en zorg ervoor dat hun vraagplannen niet **bevatten/&ast; traverse** verklaring in hen. Voorbeeld dat queryplan doorloopt:

* **PLAN:** `[nt:unstructured] as [a] /* traverse "/content//*" where ([a].[unindexedProperty] = 'some value') and (isdescendantnode([a], [/content])) */`

#### Post-implementatie {#post-deployment}

* Controleer `error.log` voor indexloze traversal vragen:

   * `*INFO* org.apache.jackrabbit.oak.query.QueryImpl Traversal query (query without index) ... ; consider creating and index`
   * Dit bericht wordt slechts geregistreerd als geen index beschikbaar is, en als de vraag potentieel vele knopen oversteekt. De berichten worden niet geregistreerd als een index beschikbaar is, maar het bedrag aan het oversteken is klein, en zo snel.

* Bezoek de AEM [&#128279;](/help/sites-administering/operations-dashboard.md#query-performance) de verrichtingenconsole van de Prestaties van de Vraag 0&rbrace; &lbrace;en [ verklaar ](/help/sites-administering/operations-dashboard.md#explain-query) langzame vragen die traversal of geen verklaringen van de indexvraag zoeken.

### Slecht beperkte query&#39;s detecteren {#detecting-poorly-restricted-queries}

#### Tijdens de ontwikkeling {#during-development-1}

Verklaar alle vragen en zorg ervoor zij aan een index oplossen die wordt afgestemd om de het bezitsbeperkingen van de vraag aan te passen.

* De ideale dekking van het vraagplan heeft `indexRules` voor alle bezitsbeperkingen, en minstens voor de strengste bezitsbeperkingen in de vraag.
* Vraagt die resultaten sorteren, zou aan een Index van het Bezit van Lucene met indexregels voor gesorteerd door eigenschappen moeten oplossen die plaatsen `orderable=true.`

#### De standaardwaarde `cqPageLucene` heeft bijvoorbeeld geen indexregel voor `jcr:content/cq:tags` . {#for-example-the-default-cqpagelucene-does-not-have-an-index-rule-for-jcr-content-cq-tags}

Voordat u de indexregel cq:tags toevoegt

* **cq:de Regel van de TagsIndex**

   * Bestaat niet buiten het vak

* **de vraag van de Bouwer van de Vraag**

  ```js
  type=cq:Page
  property=jcr:content/cq:tags
  property.value=my:tag
  ```

* **Plan van de Vraag**

  `[cq:Page] as [a] /* lucene:cqPageLucene(/oak:index/cqPageLucene) *:* where [a].[jcr:content/cq:tags] = 'my:tag' */`

Deze query wordt omgezet in de `cqPageLucene` index, maar omdat er geen eigenschapindexregel bestaat voor `jcr:content` of `cq:tags`, wordt bij het evalueren van deze beperking elke record in de `cqPageLucene` index gecontroleerd om een overeenkomst te bepalen. Als de index 1 miljoen `cq:Page` knooppunten bevat, worden dus 1 miljoen records gecontroleerd om de resultatenset te bepalen.

Na het toevoegen van de regel cq:tags index

* **cq:de Regel van de TagsIndex**

  ```js
  /oak:index/cqPageLucene/indexRules/cq:Page/properties/cqTags
  @name=jcr:content/cq:tags
  @propertyIndex=true
  ```

* **de vraag van de Bouwer van de Vraag**

  ```js
  type=cq:Page
  property=jcr:content/cq:tags
  property.value=myTagNamespace:myTag
  ```

* **Plan van de Vraag**

  `[cq:Page] as [a] /* lucene:cqPageLucene(/oak:index/cqPageLucene) jcr:content/cq:tags:my:tag where [a].[jcr:content/cq:tags] = 'my:tag' */`

Door de toevoeging van indexRule voor `jcr:content/cq:tags` in de `cqPageLucene` index `cq:tags` kunnen gegevens op een geoptimaliseerde manier worden opgeslagen.

Wanneer een query met de `jcr:content/cq:tags` -beperking wordt uitgevoerd, kan de index de resultaten op waarde opzoeken. Dat betekent dat als 100 `cq:Page` knooppunten `myTagNamespace:myTag` als waarde hebben, alleen die 100 resultaten worden geretourneerd en de andere 999.000 worden uitgesloten van de beperkingscontroles, waardoor de prestaties met een factor 10.000 worden verbeterd.

Meer vraagbeperkingen verminderen de in aanmerking komende resultaatreeksen en optimaliseren de vraagoptimalisering verder.

En zonder een extra indexregel voor de eigenschap `cq:tags` zou zelfs een fullText-query met een beperking op `cq:tags` slecht presteren omdat de resultaten van de index alle fullText-overeenkomsten zouden retourneren. De beperking op cq:tags wordt erna gefilterd.

Een andere oorzaak van post-index-filtreren is de Lijsten van het Toegangsbeheer die vaak tijdens ontwikkeling worden gemist. Controleer of de query geen paden retourneert die ontoegankelijk zijn voor de gebruiker. Dit kan worden gedaan door betere inhoudsstructuur samen met het verstrekken van relevante wegbeperkingen op de vraag te doen.

Een nuttige manier om te identificeren als de index van Lucene vele resultaten terugkeert om een kleine ondergroep als vraagresultaat terug te keren, is het toelaten van logboeken DEBUG voor `org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex`. Zo kunt u zien hoeveel documenten uit de index worden geladen. Het aantal uiteindelijke resultaten in vergelijking met het aantal geladen documenten mag niet onevenredig zijn. Voor meer informatie, zie [ het Registreren ](/help/sites-deploying/configure-logging.md).

#### Post-implementatie {#post-deployment-1}

* Controleer `error.log` voor doorlopende vragen:

   * `*WARN* org.apache.jackrabbit.oak.spi.query.Cursors$TraversingCursor Traversed ### nodes ... consider creating an index or changing the query`

* Bezoek de AEM [&#128279;](/help/sites-administering/operations-dashboard.md#query-performance) verrichtingenconsole van de Prestaties van de Vraag 0&rbrace; &lbrace;en [ verklaar ](/help/sites-administering/operations-dashboard.md#explain-query) langzame vragen zoekend vraagplannen die vraagbezitsbeperkingen aan de regels van het indexbezit niet oplossen.

### Detecteren van query&#39;s voor grote resultaatsets {#detecting-large-result-set-queries}

#### Tijdens de ontwikkeling {#during-development-2}

Stel lage drempelwaarden in voor eak.queryLimitInMemory (bijvoorbeeld 10000) en oak.queryLimitReads (bijvoorbeeld 5000) en optimaliseer de dure query wanneer een UnsupportedOperationException wordt aangeraakt die zegt &quot;De query leest meer dan x nodes...&quot;

Door lage drempelwaarden in te stellen voorkomt u bronintensieve query&#39;s (dat wil zeggen, niet ondersteund door indexen of minder dekkende index). Bijvoorbeeld, zou een vraag die één miljoen knopen leest tot veel IO leiden, en negatief de algemene toepassingsprestaties beïnvloeden. Elke query die vanwege bovenstaande limieten mislukt, moet dus worden geanalyseerd en geoptimaliseerd.

#### Post-implementatie {#post-deployment-2}

* Controleer de logboeken voor vragen die de grote knoop traversal of grote het geheugenconsumptie van de heap teweegbrengen: &quot;

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * Optimaliseer de vraag zodat vermindert u het aantal getransformeerde knopen.

* Controleer de logboeken op vragen die het grote geheugengebruik van de heap veroorzaken:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimaliseer de vraag zodat vermindert u het gebruik van het heapgeheugen.

Voor AEM 6.0 - 6.2 versies, kunt u de drempel voor knoopsverplaatsing via parameters JVM in het AEM startmanuscript aanpassen om grote vragen te verhinderen het milieu te overbelasten. De aanbevolen waarden zijn:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3, worden de bovengenoemde twee parameters preconfigured door gebrek, en kunnen via OSGi QueryEngineSettings worden gewijzigd.

Meer informatie beschikbaar onder: [ https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Afstemmen van queryprestaties {#query-performance-tuning}

Het motto van de optimalisering van vraagprestaties in AEM is:

**&quot;Hoe meer beperkingen, hoe beter.&quot;**

De volgende schetsen adviseren aanpassingen om vraagprestaties te verzekeren. Kies eerst de query, een minder opvallende activiteit en pas vervolgens, indien nodig, de indexdefinities aan.

### De queryinstructie aanpassen {#adjusting-the-query-statement}

AEM ondersteunt de volgende querytalen:

* Query Builder
* JCR-SQL2
* XPath

Het volgende voorbeeld gebruikt de Bouwer van de Vraag omdat het de gemeenschappelijkste vraagtaal is die door AEM ontwikkelaars wordt gebruikt, nochtans zijn de zelfde principes van toepassing op JCR-SQL2 en XPath.

1. Voeg een nodetype beperking toe zodat lost de vraag aan een bestaande Index van het Bezit van Lucene op.

* **Niet geoptimaliseerde vraag**

  ```js
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Geoptimaliseerde vraag**

  ```js
  type=cq:Page
  property=jcr:content/contentType
  property.value=article-page
  ```

  Zoekopdrachten waarvoor geen nodetype-beperking geldt, AEM het type `nt:base` nodetype aan te nemen. Elk knooppunt in AEM is een subtype van dit type. Dit leidt in feite tot geen nodetype-beperking.

  Als u `type=cq:Page` instelt, wordt deze query beperkt tot alleen `cq:Page` nodes en wordt de query omgezet naar AEM cqPageLucene, waarbij de resultaten worden beperkt tot een subset van knooppunten (alleen `cq:Page` nodes) in AEM.

1. Pas de nodetype van de vraag beperking zo aan de vraag aan een bestaande Index van het Bezit van Lucene.

* **Niet geoptimaliseerde vraag**

  ```js
  type=nt:hierarchyNode
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Geoptimaliseerde vraag**

  ```js
  type=cq:Page
  property=jcr:content/contentType
  property.value=article-page
  ```

  `nt:hierarchyNode` is het bovenliggende knooptype van `cq:Page` . Ervan uitgaande dat `jcr:content/contentType=article-page` alleen via de aangepaste toepassing van de Adobe op `cq:Page` nodes wordt toegepast, retourneert deze query alleen `cq:Page` -knooppunten waar `jcr:content/contentType=article-page` voorkomt. Deze stroom is echter een suboptimale beperking, omdat:

   * Andere knooppunten overerven van `nt:hierarchyNode` (bijvoorbeeld `dam:Asset` ) dat onnodig aan de set met mogelijke resultaten wordt toegevoegd.
   * Er bestaat geen AEM-opgegeven index voor `nt:hierarchyNode` , maar er is wel een opgegeven index voor `cq:Page` .

  Door `type=cq:Page` in te stellen, beperkt u deze query tot alleen `cq:Page` nodes en wordt de query omgezet in AEM cqPageLucene, waarbij de resultaten worden beperkt tot een subset van knooppunten (alleen cq:Page-knooppunten) in AEM.

1. Of pas de eigenschapbeperkingen aan zodat de query wordt omgezet in een bestaande eigenschappenindex.

* **Niet geoptimaliseerde vraag**

  ```js
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Geoptimaliseerde vraag**

  ```js
  property=jcr:content/sling:resourceType
  property.value=my-site/components/structure/article-page
  ```

  Als u de eigenschapsbeperking wijzigt van `jcr:content/contentType` (een aangepaste waarde) in de bekende eigenschap `sling:resourceType` , kan de query worden uitgevoerd naar de eigenschapindex `slingResourceType` die alle inhoud indexeert op `sling:resourceType` .

  De indexen van het bezit (in tegenstelling tot de Indexen van het Bezit van Lucene) worden het best gebruikt wanneer de vraag niet door nodetype ontdekt, en één enkele bezitsbeperking domineert de resultaatreeks.

1. Voeg de strengste padbeperking toe die mogelijk is voor de query. Kies bijvoorbeeld de voorkeur `/content/my-site/us/en` over `/content/my-site` of `/content/dam` over `/` .

* **Niet geoptimaliseerde vraag**

  ```js
  type=cq:Page
  path=/content
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Geoptimaliseerde vraag**

  ```js
  type=cq:Page
  path=/content/my-site/us/en
  property=jcr:content/contentType
  property.value=article-page
  ```

  Door de padbeperking van `path=/content` naar `path=/content/my-site/us/en` te segmenteren, kunnen indexen het aantal indexitems verminderen dat moet worden geïnspecteerd. Wanneer de query het pad veel kan beperken, meer dan alleen `/content` of `/content/dam` , moet u ervoor zorgen dat de index `evaluatePathRestrictions=true` heeft.

  Als u `evaluatePathRestrictions` gebruikt, wordt de index groter.

1. Vermijd waar mogelijk queryfuncties en querybewerkingen zoals: `LIKE` en `fn:XXXX` als de kosten worden geschaald met het aantal op beperkingen gebaseerde resultaten.

* **Niet geoptimaliseerde vraag**

  ```js
  type=cq:Page
  property=jcr:content/contentType
  property.operation=like
  property.value=%article%
  ```

* **Geoptimaliseerde vraag**

  ```js
  type=cq:Page
  fulltext=article
  fulltext.relPath=jcr:content/contentType
  ```

  De voorwaarde LIKE is traag om te evalueren omdat geen index kan worden gebruikt als de tekst met een vervanging (&quot;%...&quot;) begint. Jcr:contains condition staat het gebruiken van een fulltext index toe, en daarom verkiest. Hiervoor moet de index van de geluideneigenschap resolveRule voor `jcr:content/contentType` met `analayzed=true` bevatten.

  Het gebruik van queryfuncties zoals `fn:lowercase(..)` is wellicht moeilijker te optimaliseren omdat er geen snellere equivalenten zijn (buiten complexere en opdringerige indexanalysatorconfiguraties). Het is best om andere bereikbeperkingen te identificeren om de algemene vraagprestaties te verbeteren, die de functies vereisen om op de kleinste reeks potentiële resultaten te werken mogelijk.

1. ***Deze aanpassing is specifiek van de Bouwer van de Vraag, en is niet op JCR-SQL2 of XPath van toepassing.***

   Het gebruik [ gokTotal van de Bouwer van de Vraag ](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results) wanneer de volledige reeks resultaten **niet** onmiddellijk nodig is.

   * **Niet geoptimaliseerde vraag**

     ```js
     type=cq:Page
     path=/content
     ```

   * **Geoptimaliseerde vraag**

     ```js
     type=cq:Page
     path=/content
     p.guessTotal=100
     ```

   Voor gevallen waarin de uitvoering van de query snel verloopt maar het aantal resultaten groot is, is p. `guessTotal` een essentiële optimalisatie voor query&#39;s van de Query Builder.

   `p.guessTotal=100` vertelt de Bouwer van de Vraag om slechts de eerste 100 resultaten te verzamelen. En als u een booleaanse vlag wilt instellen die aangeeft of ten minste één resultaat meer bestaat (maar niet hoeveel meer, want tellen van dit getal leidt tot vertraging). Deze optimalisatie is alleen geschikt voor het gebruik van paginering of oneindig laden, waarbij alleen een resultaatsubset incrementeel wordt weergegeven.

## Bestaande indexafstemming {#existing-index-tuning}

1. Als de optimale query wordt omgezet in een index met eigenschappen, hoeft u niets meer te doen omdat Eigenschapindexen minimaal afstelbaar zijn.
1. Anders, zou de vraag aan een Index van het Bezit van Lucene moeten oplossen. Als geen index kan worden opgelost, sprong aan het Creëren van een Index.
1. Converteer de query zo nodig naar XPath of JCR-SQL2.

   * **de vraag van de Bouwer van de Vraag**

     ```js
     query type=cq:Page
     path=/content/my-site/us/en
     property=jcr:content/contentType
     property.value=article-page
     orderby=@jcr:content/publishDate
     orderby.sort=desc
     ```

   * **XPath dat van de vraag van de Bouwer van de Vraag** wordt geproduceerd

     ```js
     /jcr:root/content/my-site/us/en//element(*, cq:Page)[jcr:content/@contentType = 'article-page'] order by jcr:content/@publishDate descending
     ```

1. Verstrek XPath (of JCR-SQL2) aan de Generator van de Definitie van de Index van Oak bij `https://oakutils.appspot.com/generate/index` zodat kunt u de geoptimaliseerde definitie van de Index van het Bezit van Lucene produceren. <!-- The above URL is 404 as of April 24, 2023 -->

   **Gegenereerde definitie van de Index van het Bezit van Lucene**

   ```xml
   - evaluatePathRestrictions = true
   - compatVersion = 2
   - type = "lucene"
   - async = "async"
   - jcr:primaryType = oak:QueryIndexDefinition
       + indexRules
       + cq:Page
           + properties
           + contentType
               - name = "jcr:content/contentType"
               - propertyIndex = true
           + publishDate
               - ordered = true
               - name = "jcr:content/publishDate"
   ```

1. Voeg de gegenereerde definitie handmatig samen in de bestaande index voor Lucene-eigenschappen op een additieve manier. Wees voorzichtig om bestaande configuraties niet te verwijderen aangezien zij kunnen worden gebruikt om aan andere vragen te voldoen.

   1. Zoek de bestaande index voor de Lucene-eigenschap die cq:Page bedekt (met Indexbeheer). In dit geval, `/oak:index/cqPageLucene`.
   1. Identificeer de configuratiedelta tussen de geoptimaliseerde indexdefinitie (Stap 4) en de bestaande index (/eak:index/cqPageLucene), en voeg de ontbrekende configuraties van de geoptimaliseerde Index aan de bestaande indexdefinitie toe.
   1. Conform AEM het Reindexeren Beste praktijken, of verfrist zich of herindexeert is in orde, gebaseerd op als de bestaande inhoud door deze verandering van de indexconfiguratie zou kunnen worden beïnvloed.

## Een nieuwe index maken {#create-a-new-index}

1. Verifieer dat de vraag niet aan een bestaande Index van het Bezit van Lucene oplost. Als dit het geval is, raadpleegt u de bovenstaande sectie over afstemmen en de bestaande index.
1. Converteer de query zo nodig naar XPath of JCR-SQL2.

   * **de vraag van de Bouwer van de Vraag**

     ```js
     type=myApp:Author
     property=firstName
     property.value=ira
     ```

   * **XPath dat van de vraag van de Bouwer van de Vraag** wordt geproduceerd

     ```js
     //element(*, myApp:Page)[@firstName = 'ira']
     ```

1. Verstrek XPath (of JCR-SQL2) aan de Generator van de Definitie van de Index van Oak bij `https://oakutils.appspot.com/generate/index` zodat kunt u de geoptimaliseerde definitie van de Index van het Bezit van Lucene produceren. <!-- The above URL is 404 as of April 24, 2023 -->

   **Gegenereerde definitie van de Index van het Bezit van Lucene**

   ```xml
   - compatVersion = 2
   - type = "lucene"
   - async = "async"
   - jcr:primaryType = oak:QueryIndexDefinition
       + indexRules
       + myApp:AuthorModel
           + properties
           + firstName
               - name = "firstName"
               - propertyIndex = true
   ```

1. Stel de geproduceerde definitie van de Index van het Bezit van Lucene op.

   Voeg de definitie van XML toe die door de Generator van de Definitie van de Index van Oak voor de nieuwe index aan het AEM project wordt verstrekt dat de indexdefinities van Oak beheert (herinner me, behandelt de indexdefinities van Oak als code, aangezien de code van hen afhangt).

   Implementeer en test de nieuwe index na de gebruikelijke AEM ontwikkelingscyclus van de software en controleer of de query naar de index wordt omgezet en of de query uitvoerbaar is.

   Bij de eerste implementatie van deze index worden AEM de vereiste gegevens in de index ingevuld.

## Wanneer zijn index-less en traversal vragen O.K.? {#when-index-less-and-traversal-queries-are-ok}

Door de AEM flexibele inhoudarchitectuur is het moeilijk te voorspellen en ervoor te zorgen dat traversals van inhoudsstructuren zich niet in de loop der tijd ontwikkelen om onaanvaardbaar groot te zijn.

Daarom zorg ervoor dat de indexen vragen tevredenstellen, behalve als de combinatie wegbeperking en nodetype beperking garandeert dat **minder dan 20 knopen ooit worden gepasseerd.**

## Hulpprogramma&#39;s voor query-ontwikkeling {#query-development-tools}

### Ondersteunde Adobe {#adobe-supported}

* **Debugger van de Bouwer van de Vraag**

   * Een WebUI voor het uitvoeren van de vragen van de Bouwer van de Vraag en produceren ondersteunend XPath (voor gebruik in Uitdrukkelijke Vraag of de Generator van de Definitie van de Index van Oak).
   * Op AEM in [ /libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)

* **CRXDE Lite - het Hulpmiddel van de Vraag**

   * Een WebUI voor het uitvoeren van vragen XPath en JCR-SQL2.
   * Op AEM bij [ /crx/de/index.jsp ](http://localhost:4502/crx/de/index.jsp) > Hulpmiddelen > Vraag..

* **[verklaart Vraag](/help/sites-administering/operations-dashboard.md#explain-query)**

   * Een dashboard van Verrichtingen van de AEM dat een gedetailleerde verklaring (het plan van de Vraag, vraagtijd, en # van resultaten) voor om het even welke bepaalde vraag XPATH of JCR-SQL2 verstrekt.

* **[Trage/Populaire Vragen](/help/sites-administering/operations-dashboard.md#query-performance)**

   * Een dashboard AEM bewerkingen met de recente trage en populaire query&#39;s die zijn uitgevoerd op AEM.

* **[Manager van de Index](/help/sites-administering/operations-dashboard.md#the-index-manager)**

   * Een AEM Verrichtingen WebUI die de indexen op de AEM instantie tonen; vergemakkelijkt het begrip welke indexen bestaan; kan worden gericht of worden verbeterd.

* **[het Registreren](/help/sites-administering/operations-dashboard.md#log-messages)**

   * Logboekregistratie van Query Builder

      * `DEBUG @ com.day.cq.search.impl.builder.QueryImpl`

   * Logboek voor uitvoeren van Oak-query

      * `DEBUG @ org.apache.jackrabbit.oak.query`

* **Apache de Montages OSGi Config van de Motor van de Vraag van het Jasje**

   * OSGi configuratie die mislukkingsgedrag voor het oversteken van vragen vormt.
   * Op AEM bij [/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService ](http://localhost:4502/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService)

* **NodeCounter JMX Mbean**

   * JMX MBean gebruikt om het aantal knopen in inhoudbomen in AEM te schatten.
   * Op AEM bij [ /system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter ](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter)

### Ondersteunde community {#community-supported}

* **Oak Index Definition Generator op`https://oakutils.appspot.com/generate/index`** <!-- The above URL is 404 as of April 24, 2023 -->

   * Produceer optimale Index van het Bezit van de Geluidseigenschap van XPath of JCR-SQL2 vraagverklaringen.

* **_AEM Chrome Plug-in_** <!-- For whatever reason, the URL to this extension was causing too many redirects when doing the request so it was removed entirely to get rid of the error; users can easily look up the extension in Google instead. DO NOT ADD THE URL AGAIN!-->

   * De _AEM Plug-in van Chrome_ is een het Webbrowser van Google Chrome uitbreiding die per-verzoeklogboekgegevens, met inbegrip van looppas vragen en hun vraagplannen, in de browser dev hulpmiddelenconsole blootstelt.
   * Vereist u om [ het Verschuiven Traceur 1.0.2+ van het Logboek ](https://sling.apache.org/downloads.cgi) op AEM te installeren en toe te laten.
