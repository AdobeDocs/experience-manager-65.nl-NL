---
title: Problemen met trage query's oplossen
seo-title: Troubleshooting Slow Queries
description: Problemen met trage query's oplossen
seo-description: null
uuid: ad09546a-c049-44b2-99a3-cb74ee68f040
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: c01e42ff-e338-46e6-a961-131ef943ea91
exl-id: 3405cdd3-3d1b-414d-9931-b7d7b63f0a6f
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '2265'
ht-degree: 0%

---

# Problemen met trage query&#39;s oplossen{#troubleshooting-slow-queries}

## Trage query-classificaties {#slow-query-classifications}

Er zijn drie belangrijke classificaties van langzame vragen in AEM, die door strengheid worden vermeld:

1. **Vragen zonder index**

   * Zoekopdrachten die wel **niet** omzetten in een index en de inhoud van het JCR doorlopen om resultaten te verzamelen

1. **Slecht beperkte (of scoped) vragen**

   * Vragen die worden omgezet in een index, maar alle indexitems moeten doorlopen om resultaten te verzamelen

1. **Vraagstukken met een grote resultaatset**

   * Zoekopdrachten die een zeer groot aantal resultaten opleveren

De eerste 2 classificaties van vragen (index-minder en slecht beperkt) zijn langzaam, omdat zij de de vraagmotor van het Eak dwingen om elk te inspecteren **potentieel** result (content node of index entry) om te identificeren welke hoort in het **werkelijk** resultaatset.

Het inspecteren van elk mogelijk resultaat is de zogenaamde &quot;Traversing&quot;.

Aangezien elk potentieel resultaat moet worden geïnspecteerd, stijgen de kosten om de feitelijke resultaatreeks te bepalen lineair met het aantal potentiële resultaten.

Door querybeperkingen en tuning-indexen toe te voegen, kunnen de indexgegevens worden opgeslagen in een geoptimaliseerde indeling die snelle resultaten ophaalt en, vermindert of verwijdert u de behoefte aan lineaire inspectie van potentiële resultaatsets.

In AEM 6.3, door gebrek, wanneer een traversal van 100.000 wordt bereikt, ontbreekt de vraag en werpt een uitzondering. Deze grens bestaat niet door gebrek in AEM versies voorafgaand aan AEM 6.3, maar kan via de Montages OSGi van de Motor van de Vraag van het Jasje van de Vraag van Apache worden geplaatst en Bon QueryEngineSettings JMX (bezit LimitReads).

### Vragen zonder index detecteren {#detecting-index-less-queries}

#### Tijdens de ontwikkeling {#during-development}

Uitleggen **alles** vragen en zorg ervoor hun vraagplannen niet bevatten **/&amp;ast; doorlopen** uitleg. Voorbeeld dat queryplan doorloopt:

* **PLAN:** `[nt:unstructured] as [a] /* traverse "/content//*" where ([a].[unindexedProperty] = 'some value') and (isdescendantnode([a], [/content])) */`

#### Na de implementatie {#post-deployment}

* De `error.log` voor traversal query&#39;s zonder index:

   * `*INFO* org.apache.jackrabbit.oak.query.QueryImpl Traversal query (query without index) ... ; consider creating and index`
   * Dit bericht wordt slechts geregistreerd als geen index beschikbaar is, en als de vraag potentieel vele knopen oversteekt. De berichten worden niet geregistreerd als een index beschikbaar is, maar het bedrag aan het oversteken is klein, en zo snel.

* Bezoek de AEM [Query-prestaties](/help/sites-administering/operations-dashboard.md#query-performance) operatieconsole en [Uitleggen](/help/sites-administering/operations-dashboard.md#explain-query) langzame vragen die traversal of geen verklaringen van de indexvraag zoeken.

### Slecht beperkte query&#39;s detecteren {#detecting-poorly-restricted-queries}

#### Tijdens de ontwikkeling {#during-development-1}

Verklaar alle vragen en zorg ervoor zij aan een index oplossen die wordt afgestemd om de het bezitsbeperkingen van de vraag aan te passen.

* De ideale dekking van het vraagplan heeft `indexRules` voor alle bezitsbeperkingen, en minstens voor de strengste bezitsbeperkingen in de vraag.
* De vragen die resultaten sorteren, zouden aan een Index van het Bezit van Lucene met indexregels voor gesorteerd door eigenschappen moeten oplossen die plaatsen `orderable=true.`

#### De standaardinstelling `cqPageLucene` heeft geen indexregel voor `jcr:content/cq:tags` {#for-example-the-default-cqpagelucene-does-not-have-an-index-rule-for-jcr-content-cq-tags}

Voordat u de indexregel cq:tags toevoegt

* **cq:labels, indexregel**

   * Bestaat niet buiten het vak

* **Query Builder-query**

   ```js
   type=cq:Page
   property=jcr:content/cq:tags
   property.value=my:tag
   ```

* **Zoekplan**

   `[cq:Page] as [a] /* lucene:cqPageLucene(/oak:index/cqPageLucene) *:* where [a].[jcr:content/cq:tags] = 'my:tag' */`

Deze query wordt omgezet in de `cqPageLucene` index, maar omdat er geen eigenschapindex-regel bestaat voor `jcr:content` of `cq:tags`, wanneer deze beperking wordt beoordeeld, elke record in het `cqPageLucene` index wordt gecontroleerd om een gelijke te bepalen. Dit betekent dat als de index 1 miljoen bevat `cq:Page` knooppunten, dan worden 1 miljoen verslagen gecontroleerd om de resultaatreeks te bepalen.

Na het toevoegen van de regel cq:tags index

* **cq:labels, indexregel**

   ```js
   /oak:index/cqPageLucene/indexRules/cq:Page/properties/cqTags
   @name=jcr:content/cq:tags
   @propertyIndex=true
   ```

* **Query Builder-query**

   ```js
   type=cq:Page
   property=jcr:content/cq:tags
   property.value=myTagNamespace:myTag
   ```

* **Zoekplan**

   `[cq:Page] as [a] /* lucene:cqPageLucene(/oak:index/cqPageLucene) jcr:content/cq:tags:my:tag where [a].[jcr:content/cq:tags] = 'my:tag' */`

De toevoeging van indexRule voor `jcr:content/cq:tags` in de `cqPageLucene` index staat toe `cq:tags` gegevens die op geoptimaliseerde wijze moeten worden opgeslagen.

Wanneer een vraag met `jcr:content/cq:tags` De beperking wordt uitgevoerd, kan de index resultaten door waarde omhoog kijken. Dat betekent dat als 100 `cq:Page` knooppunten hebben `myTagNamespace:myTag` als waarde worden alleen die 100 resultaten geretourneerd en de andere 999.000 worden uitgesloten van de beperkende controles , waardoor de prestaties met een factor 10.000 worden verbeterd .

Natuurlijk, verminderen de verdere vraagbeperkingen de in aanmerking komende resultaatreeksen en optimaliseren verder de vraagoptimalisering.

Op dezelfde manier, zonder een extra indexregel voor `cq:tags` eigenschap, zelfs een fulltext-query met een beperking op `cq:tags` zou slecht presteren aangezien de resultaten van de index alle fullText gelijken zouden terugkeren. De beperking op cq:tags wordt erna gefilterd.

Een andere oorzaak van post-index-filtreren is de Lijsten van het Toegangsbeheer die vaak tijdens ontwikkeling worden gemist. Controleer of de query geen paden retourneert die ontoegankelijk zijn voor de gebruiker. Dit kan gewoonlijk door betere inhoudsstructuur samen met het verstrekken van relevante wegbeperking op de vraag worden gedaan.

Een nuttige manier om te identificeren als de index van Lucene veel resultaten terugkeert om een zeer kleine ondergroep als vraagresultaat terug te keren is het toelaten van logboeken DEBUG voor `org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex` en zie hoeveel documenten vanaf de index worden geladen. Het aantal uiteindelijke resultaten in vergelijking met het aantal geladen documenten mag niet onevenredig zijn. Zie voor meer informatie [Logboekregistratie](/help/sites-deploying/configure-logging.md).

#### Na de implementatie {#post-deployment-1}

* De `error.log` voor traversale zoekopdrachten:

   * `*WARN* org.apache.jackrabbit.oak.spi.query.Cursors$TraversingCursor Traversed ### nodes ... consider creating an index or changing the query`

* Bezoek de AEM [Query-prestaties](/help/sites-administering/operations-dashboard.md#query-performance) operatieconsole en [Uitleggen](/help/sites-administering/operations-dashboard.md#explain-query) langzame vragen die vraagplannen zoeken die vraagbezitsbeperkingen aan de regels van het indexbezit niet oplossen.

### Detecteren van query&#39;s voor grote resultaatsets {#detecting-large-result-set-queries}

#### Tijdens de ontwikkeling {#during-development-2}

Stel lage drempelwaarden in voor eak.queryLimitInMemory (bijv. 10000) en oak.queryLimitReads (bijv. 5000) en optimaliseer de dure vraag wanneer het raken van een UnsupportedOperationException die &quot;de vraag leest meer dan x knopen...&quot; zegt

Dit helpt middelintensieve vragen (d.w.z. te vermijden. niet ondersteund door een index of ondersteund door minder dekkende index). Bijvoorbeeld, zou een vraag die 1M knopen leest tot veel IO leiden, en negatief de algemene toepassingsprestaties beïnvloeden. Elke query die vanwege bovenstaande limieten mislukt, moet dus worden geanalyseerd en geoptimaliseerd.

#### Na de implementatie {#post-deployment-2}

* Controleer de logboeken voor vragen die de grote knoop traversal of grote het geheugenconsumptie van de heap veroorzaken: &quot;

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * De query optimaliseren om het aantal doorgelopen knooppunten te verminderen

* Controleer de logboeken voor vragen die het grote gebruik van het heapgeheugen teweegbrengen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimaliseer de vraag om het gebruik van het heapgeheugen te verminderen

Voor AEM 6.0 - 6.2 versies, kunt u de drempel voor knoopsverplaatsing via parameters JVM in het AEM startmanuscript aanpassen om grote vragen te verhinderen het milieu te overbelasten. De aanbevolen waarden zijn:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3, worden bovengenoemde 2 parameters vooraf gevormd door gebrek, en kunnen via OSGi QueryEngineSettings worden gewijzigd.

Meer informatie is beschikbaar onder: [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Afstemmen van queryprestaties {#query-performance-tuning}

Het motto van de optimalisering van vraagprestaties in AEM is:

**&quot;Hoe meer beperkingen, hoe beter.&quot;**

De volgende schetsen adviseren aanpassingen om vraagprestaties te verzekeren. Kies eerst de query, een minder opvallende activiteit en pas vervolgens, indien nodig, de indexdefinities aan.

### De queryinstructie aanpassen {#adjusting-the-query-statement}

AEM ondersteunt de volgende querytalen:

* Query Builder
* JCR-SQL2
* XPath

Het volgende voorbeeld gebruikt de Bouwer van de Vraag aangezien het de gemeenschappelijkste vraagtaal is die door AEM ontwikkelaars wordt gebruikt, nochtans zijn de zelfde principes van toepassing op JCR-SQL2 en XPath.

1. Voeg een nodetype beperking toe zodat lost de vraag aan een bestaande Index van het Bezit van Lucene op.

* **Niet-geoptimaliseerde query**

   ```js
   property=jcr:content/contentType
   property.value=article-page
   ```

* **Geoptimaliseerde query**

   ```js
   type=cq:Page
   property=jcr:content/contentType
   property.value=article-page
   ```

   Zoekopdrachten waarvoor geen nodetype-beperkende kracht AEM om de `nt:base` nodetype, dat elke knoop in AEM een subtype van is, effectief resulterend in geen nodetype beperking.

   Instelling `type=cq:Page` beperkt deze query tot alleen `cq:Page` knopen, en lost de vraag aan AEM cqPageLucene op, die de resultaten tot een ondergroep van knopen (slechts) beperkt `cq:Page` knooppunten) in AEM.

1. Pas de nodetype van de vraag beperking zo aan de vraag aan een bestaande Index van het Bezit van Lucene.

* **Niet-geoptimaliseerde query**

   ```js
   type=nt:hierarchyNode
   property=jcr:content/contentType
   property.value=article-page
   ```

* **Geoptimaliseerde query**

   ```js
   type=cq:Page
   property=jcr:content/contentType
   property.value=article-page
   ```

   `nt:hierarchyNode` is het bovenliggende nodetype van `cq:Page`, en `jcr:content/contentType=article-page` wordt alleen toegepast op `cq:Page` knooppunten via onze aangepaste toepassing. Deze query retourneert alleen `cq:Page` knooppunten waar `jcr:content/contentType=article-page`. Dit is echter een suboptimale beperking, omdat:

   * Andere knoop erft van `nt:hierarchyNode` (bijv. `dam:Asset`) onnodig toevoegen aan de reeks potentiële resultaten.
   * Er bestaat geen AEM index voor `nt:hierarchyNode`, maar er is een index voor `cq:Page`.
   Instelling `type=cq:Page` beperkt deze query tot alleen `cq:Page` knooppunten, en lost de vraag aan AEM cqPageLucene op, die de resultaten tot een ondergroep van knopen (slechts cq:de knopen van de Pagina) in AEM beperkt.

1. U kunt ook de eigenschapbeperking(en) aanpassen zodat de query wordt omgezet in een bestaande eigenschappenindex.

* **Niet-geoptimaliseerde query**

   ```js
   property=jcr:content/contentType
   property.value=article-page
   ```

* **Geoptimaliseerde query**

   ```js
   property=jcr:content/sling:resourceType
   property.value=my-site/components/structure/article-page
   ```

   De eigenschapsbeperking wijzigen van `jcr:content/contentType` (een aangepaste waarde) naar de bekende eigenschap `sling:resourceType` laat de vraag aan de bezitsindex oplossen `slingResourceType` waarmee alle inhoud wordt geïndexeerd `sling:resourceType`.

   De indexen van het bezit (in tegenstelling tot de Indexen van het Bezit van Lucene) worden het best gebruikt wanneer de vraag niet door nodetype ontdekt, en één enkele bezitsbeperking domineert de resultaatreeks.

1. Voeg de strengste padbeperking toe die mogelijk is voor de query. Voorkeur `/content/my-site/us/en` over `/content/my-site`, of `/content/dam` over `/`.

* **Niet-geoptimaliseerde query**

   ```js
   type=cq:Page
   path=/content
   property=jcr:content/contentType
   property.value=article-page
   ```

* **Geoptimaliseerde query**

   ```js
   type=cq:Page
   path=/content/my-site/us/en
   property=jcr:content/contentType
   property.value=article-page
   ```

   De padbeperking van `path=/content`tot `path=/content/my-site/us/en` Hiermee kunnen indexen het aantal indexitems verminderen dat moet worden geïnspecteerd. Wanneer de vraag de weg zeer goed kan beperken, voorbij enkel `/content` of `/content/dam`, controleert u of de index `evaluatePathRestrictions=true`.

   Notitie met `evaluatePathRestrictions` Hiermee wordt de indexgrootte verhoogd.

1. Vermijd, waar mogelijk, vraagfuncties/verrichtingen zoals: `LIKE` en `fn:XXXX` als hun kosten worden geschaald met het aantal op beperkingen gebaseerde resultaten.

* **Niet-geoptimaliseerde query**

   ```js
   type=cq:Page
   property=jcr:content/contentType
   property.operation=like
   property.value=%article%
   ```

* **Geoptimaliseerde query**

   ```js
   type=cq:Page
   fulltext=article
   fulltext.relPath=jcr:content/contentType
   ```

   De voorwaarde LIKE is traag om te evalueren omdat geen index kan worden gebruikt als de tekst met een vervanging (&quot;%...&quot;) begint. Jcr:contains condition staat het gebruiken van een fulltext index toe, en daarom verkiest. Dit vereist de opgeloste Index van het Bezit van Lucene om indexRule te hebben voor `jcr:content/contentType` with `analayzed=true`.

   Query-functies gebruiken als `fn:lowercase(..)` Het kan moeilijker zijn om te optimaliseren omdat er geen snellere equivalenten zijn (buiten complexere en opdringerige configuraties van de indexanalysator). Het is best om andere bereikbeperkingen te identificeren om de algemene vraagprestaties te verbeteren, die de functies vereisen om op de kleinste reeks potentiële resultaten te werken mogelijk.

1. ***Deze aanpassing is specifiek voor Query Builder en is niet van toepassing op JCR-SQL2 of XPath.***

   Gebruiken [adenTotaal van Query Builder](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results) wanneer de volledige reeks resultaten **niet** onmiddellijk nodig.

   * **Niet-geoptimaliseerde query**

      ```js
      type=cq:Page
      path=/content
      ```

   * **Geoptimaliseerde query**

      ```js
      type=cq:Page
      path=/content
      p.guessTotal=100
      ```
   Als de uitvoering van de query snel is maar het aantal resultaten groot is, blz. `guessTotal` is een kritieke optimalisering voor de vragen van de Bouwer van de Vraag.

   `p.guessTotal=100` instrueert de Bouwer van de Vraag om slechts de eerste 100 resultaten te verzamelen, en een booleaanse vlag te plaatsen die erop wijst als minstens één meer resultaten bestaan (maar niet hoeveel meer, aangezien het tellen van dit aantal in vertraging zou zijn). Deze optimalisatie is niet geschikt voor het gebruik van paginering of oneindig laden, waarbij alleen een subset met resultaten incrementeel wordt weergegeven.

## Bestaande indexafstemming {#existing-index-tuning}

1. Als de optimale query wordt omgezet in een index met eigenschappen, hoeft u niets meer te doen omdat Eigenschapindexen minimaal afstemmen.
1. Anders, zou de vraag aan een Index van het Bezit van Lucene moeten oplossen. Als geen index kan worden opgelost, sprong aan het Creëren van een nieuwe Index.
1. Converteer de query zo nodig naar XPath of JCR-SQL2.

   * **Query Builder-query**

      ```js
      query type=cq:Page
      path=/content/my-site/us/en
      property=jcr:content/contentType
      property.value=article-page
      orderby=@jcr:content/publishDate
      orderby.sort=desc
      ```

   * **XPath dat is gegenereerd op basis van query Builder**

      ```js
      /jcr:root/content/my-site/us/en//element(*, cq:Page)[jcr:content/@contentType = 'article-page'] order by jcr:content/@publishDate descending
      ```

1. XPath (of JCR-SQL2) opgeven voor [Generator voor eekindexdefinitie](https://oakutils.appspot.com/generate/index) om de geoptimaliseerde definitie van de Index van het Bezit van Lucene te produceren.

   **Gegenereerde definitie van eigenschappen van Luceen**

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

   1. Bepaal de plaats van de bestaande Index van het Bezit van Lucene die cq:Pagina behandelt (gebruikend de Manager van de Index). In dit geval: `/oak:index/cqPageLucene`.
   1. Identificeer de configuratiedelta tussen de geoptimaliseerde indexdefinitie (Stap 4) en de bestaande index (/eak:index/cqPageLucene), en voeg de ontbrekende configuraties van de geoptimaliseerde Index aan de bestaande indexdefinitie toe.
   1. Per AEM het Opnieuw indexeren Beste praktijken, of verfrist zich of herindexeert is in orde, gebaseerd op als de bestaande inhoud door deze verandering van de indexconfiguratie zal worden uitgevoerd.

## Een nieuwe index maken {#create-a-new-index}

1. Verifieer de vraag niet aan een bestaande Index van het Bezit van Lucene oplost. Als dit het geval is, raadpleegt u de bovenstaande sectie over afstemmen en de bestaande index.
1. Converteer de query zo nodig naar XPath of JCR-SQL2.

   * **Query Builder-query**

      ```js
      type=myApp:Author
      property=firstName
      property.value=ira
      ```

   * **XPath dat is gegenereerd op basis van query Builder**

      ```js
      //element(*, myApp:Page)[@firstName = 'ira']
      ```

1. XPath (of JCR-SQL2) opgeven voor [Generator voor eekindexdefinitie](https://oakutils.appspot.com/generate/index) om de geoptimaliseerde definitie van de Index van het Bezit van Lucene te produceren.

   **Gegenereerde definitie van eigenschappen van Luceen**

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

   Voeg de definitie van XML toe die door de Generator van de Definitie van de Index van de Eak voor de nieuwe index aan het AEM project wordt verstrekt dat de definities van de Index van het Eak (herinner, behandelt de indexdefinities van de Eik als code, aangezien de code van hen afhangt) beheert.

   Implementeer en test de nieuwe index volgens de gebruikelijke AEM ontwikkelingscyclus van de software en verifieer de vraag aan de index oplost en de vraag presteert is.

   Na de eerste implementatie van deze index, vult AEM de index met de vereiste gegevens.

## Wanneer zijn index-less en traversal vragen O.K.? {#when-index-less-and-traversal-queries-are-ok}

Door AEM flexibele inhoudarchitectuur is het moeilijk om te voorspellen en ervoor te zorgen dat de transformaties van inhoudsstructuren in de loop der tijd niet zullen evolueren om onaanvaardbaar groot te zijn.

Zorg er daarom voor dat indexen voldoen aan query&#39;s, behalve als de combinatie van padbeperking en geen beperkingen garandeert dat **er worden ooit minder dan 20 knooppunten doorkruist .**

## Hulpprogramma&#39;s voor query-ontwikkeling {#query-development-tools}

### Adobe ondersteund {#adobe-supported}

* **Foutopsporing voor Query Builder**

   * Een WebUI voor het uitvoeren van de vragen van de Bouwer van de Vraag en produceren ondersteunend XPath (voor gebruik in Verklaar de Generator van de Definitie van de Vraag of van de Index).
   * AEM op [/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)

* **CRXDE Lite - Query**

   * Een WebUI voor het uitvoeren van vragen XPath en JCR-SQL2.
   * AEM op [/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp) > Gereedschappen > Query...

* **[Query uitvoeren](/help/sites-administering/operations-dashboard.md#explain-query)**

   * Een dashboard van Verrichtingen van de AEM dat een gedetailleerde verklaring (het plan van de Vraag, vraagtijd, en # van resultaten) voor om het even welke bepaalde vraag XPATH of JCR-SQL2 verstrekt.

* **[Trage/populaire query&#39;s](/help/sites-administering/operations-dashboard.md#query-performance)**

   * Een dashboard AEM bewerkingen met de recente trage en populaire query&#39;s die zijn uitgevoerd op AEM.

* **[Indexbeheer](/help/sites-administering/operations-dashboard.md#the-index-manager)**

   * Een AEM Verrichtingen WebUI die de indexen op de AEM instantie tonen; Hiermee kunt u beter begrijpen welke indexen al bestaan en welke indexen kunnen worden gericht of aangevuld.

* **[Logboekregistratie](/help/sites-administering/operations-dashboard.md#log-messages)**

   * Logboekregistratie van Query Builder

      * `DEBUG @ com.day.cq.search.impl.builder.QueryImpl`
   * Logboek voor uitvoeren van query&#39;s

      * `DEBUG @ org.apache.jackrabbit.oak.query`


* **Apache Jackrabbit Query Engine Settings OSGi Config**

   * OSGi configuratie die mislukkingsgedrag voor het oversteken van vragen vormt.
   * AEM op [/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService](http://localhost:4502/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService)

* **NodeCounter JMX-boon**

   * JMX MBean gebruikt om het aantal knopen in inhoudbomen in AEM te schatten.
   * AEM op [/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter)

### Ondersteunde community {#community-supported}

* **[Generator voor eekindexdefinitie](https://oakutils.appspot.com/generate/index)**

   * Produceer optimale Index van het Bezit van de Geluidseigenschap van XPath of JCR-SQL2 vraagverklaringen.

* **[AEM Chrome-plug-in](https://chrome.google.com/webstore/detail/aem-chrome-plug-in/ejdcnikffjleeffpigekhccpepplaode?hl=en-US)**

   * De Webbrowser van Google Chrome uitbreiding die per-verzoeklogboekgegevens, met inbegrip van uitgevoerde vragen en hun vraagplannen, in browser de Dev hulpensconsole van hulpmiddelen blootstelt.
   * Vereisten [Sling Log Tracker 1.0.2+](https://sling.apache.org/downloads.cgi) worden geïnstalleerd en ingeschakeld op AEM.
