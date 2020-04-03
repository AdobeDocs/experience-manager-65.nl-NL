---
title: Query Builder-API
seo-title: Query Builder-API
description: De functionaliteit van de Asset Share Query Builder wordt weergegeven via een Java API en een REST API.
seo-description: De functionaliteit van de Asset Share Query Builder wordt weergegeven via een Java API en een REST API.
uuid: 6928c3e9-96a1-44ad-9785-350d95f1869a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 7965b7ef-dec4-441a-a012-daf1d60df0fb
pagetitle: Query Builder API
tagskeywords: querybuilder
translation-type: tm+mt
source-git-commit: a491d4e9bd9ffc68c4ba7cac3149f48cf7576ee8

---


# Query Builder-API{#query-builder-api}

De functionaliteit van de [Asset Share Query Builder](/help/assets/assets-finder-editor.md) wordt weergegeven via een Java API en een REST API. In deze sectie worden deze API&#39;s beschreven.

De server-kant vraagbouwer ( [`QueryBuilder`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html)) zal een vraagbeschrijving goedkeuren, creeert en in werking stelt een vraag van XPath, naar keuze filter de resultaatreeks, en ook extractfacetten, indien gewenst.

De vraagbeschrijving is eenvoudig een reeks predikaten ([`Predicate`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/Predicate.html)). Voorbeelden zijn een voorspelling in volledige tekst, die overeenkomt met de functie in XPath. `jcr:contains()`

Voor elk predikaat type, is er een beoordelaarcomponent ([`PredicateEvaluator`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) die weet hoe te om dat specifieke predikaat voor XPath, het filtreren, en facetextractie te behandelen. Het is zeer gemakkelijk om douanebeoordelaars tot stand te brengen, die door componenten OSGi runtime gestopt zijn.

De REST API biedt toegang tot exact dezelfde functies via HTTP, waarbij reacties worden verzonden in JSON.

>[!NOTE]
>
>De API van QueryBuilder wordt gebouwd gebruikend JCR API. U kunt ook een query uitvoeren op de JCR-API van Adobe Experience Manager vanuit een OSGi-bundel. Zie Adobe Experience Manager-gegevens [aanvragen met de JCR API](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html)voor meer informatie.

## Gem-sessie {#gem-session}

[AEM Gems](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-index.html) is een aantal technische diepgaande duiken in Adobe Experience Manager die door Adobe-experts worden geleverd. Deze zitting die aan de vraagbouwer wordt gewijd is zeer nuttig voor een overzicht en gebruik van het hulpmiddel.

>[!NOTE]
>
>Zie de AEM Gem-sessie [Zoekformulieren die gemakkelijk zijn gemaakt met de AEM querybuilder](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-search-forms-using-querybuilder.html) voor een gedetailleerd overzicht van de querybuilder.

## Voorbeeldquery&#39;s {#sample-queries}

Deze voorbeelden worden gegeven in de stijlnotatie Java-eigenschappen. Als u deze wilt gebruiken met de Java API, gebruikt u een Java `HashMap` zoals in het volgende API-voorbeeld.

Voor de `QueryBuilder` JSON-server bevat elk voorbeeld een koppeling naar uw lokale CQ-installatie (op de standaardlocatie, `http://localhost:4502`). U moet zich aanmelden bij uw CQ-exemplaar voordat u deze koppelingen kunt gebruiken.

>[!CAUTION]
>
>Standaard geeft de json servlet van de querybuilder maximaal 10 resultaten weer.
>
>Als u de volgende parameter toevoegt, kan de servlet alle queryresultaten weergeven:
>
>**`p.limit=-1`**

>[!NOTE]
>
>Als u de geretourneerde JSON-gegevens in uw browser wilt weergeven, kunt u een plug-in gebruiken, zoals JSONView voor Firefox.

### Alle resultaten retourneren {#returning-all-results}

De volgende query **retourneert tien resultaten** (of om precies te zijn een maximum van tien), maar informeert u over het **aantal treffers:** die daadwerkelijk beschikbaar zijn:

`http://localhost:4502/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=foundation/components/text&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=foundation/components/text
1_property.operation=like
orderby=path
```

Dezelfde query (met de parameter `p.limit=-1`) zal alle resultaten **** retourneren (dit kan een hoog getal zijn, afhankelijk van uw instantie):

`http://localhost:4502/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=foundation/components/text&1_property.operation=like&p.limit=-1&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=foundation/components/text
1_property.operation=like
p.limit=-1
orderby=path
```

### De resultaten retourneren met p.radenTotal {#using-p-guesstotal-to-return-the-results}

Het doel van de `p.guessTotal` parameter is om het juiste aantal resultaten te retourneren dat kan worden aangetoond door de minimale levensvatbare p.offset- en p.limit-waarden te combineren. Het voordeel van deze parameter is dat de prestaties van grote resultaatsets verbeterd zijn. Zo voorkomt u dat het volledige totaal wordt berekend (bijvoorbeeld door result.getSize() aan te roepen en de gehele resultaatset te lezen, volledig tot aan de OAK-engine en -index is geoptimaliseerd. Dit kan een significant verschil zijn wanneer er 100 duizenden resultaten zijn, zowel in uitvoeringstijd als in geheugengebruik.

Het nadeel van de parameter is dat gebruikers het exacte totaal niet zien. Maar u kunt een minimumaantal zoals p.radenTotal=1000 plaatsen zodat zal het altijd tot 1000 lezen, zodat krijgt u nauwkeurige totalen voor kleinere resultaatreeksen, maar als het meer dan dat is, kunt u slechts &quot;en meer&quot;tonen.

Voeg `p.guessTotal=true` aan de vraag toe hieronder om te zien hoe het werkt:

`http://localhost:4502/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=foundation/components/text&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=foundation/components/text
1_property.operation=like
p.guessTotal=true
orderby=path
```

De query retourneert de `p.limit` standaardwaarde van de `10` resultaten met een `0` offset:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

Vanaf AEM 6.0 SP2, kunt u een numerieke waarde ook gebruiken om tot een douanenummer van maximumresultaten te tellen. Gebruik dezelfde query als hierboven, maar wijzig de waarde van `p.guessTotal` in `50`:

`http://localhost:4502/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=foundation/components/text&1_property.operation=like&p.guessTotal=50&orderby=path`

Het zal een aantal de zelfde standaardgrens van 10 resultaten met een 0 compensatie terugkeren, maar zal slechts een maximum van 50 resultaten tonen:

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### Paginering uitvoeren {#implementing-pagination}

Door gebrek zou de Bouwer van de Vraag ook het aantal treffers verstrekken. Afhankelijk van de resultaatgrootte dit zou lang kunnen duren aangezien het bepalen van de nauwkeurige telling het controleren van elk resultaat voor toegangsbeheer impliceert. Meestal wordt het totaal gebruikt om paginering voor de eindgebruiker UI uit te voeren. Aangezien het bepalen van de nauwkeurige telling langzaam kan zijn, wordt geadviseerd om van de eigenschap te gebruiken radenTotal om de paginering uit te voeren.

De interface kan bijvoorbeeld de volgende benadering aanpassen:

* Krijg en toon de nauwkeurige telling van het aantal totale klappen ([SearchResult.getTotalMatches()](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/result/SearchResult.html#gettotalmatches) of totaal in de querybuilder.json reactie) zijn minder dan of gelijk aan 100;
* Reeks `guessTotal` aan 100 terwijl het maken van de vraag aan de Bouwer van de Vraag.

* De reactie kan het volgende resultaat hebben:

   * `total=43`, `more=false` - Geeft aan dat het totale aantal treffers 43 is. De interface kan tot tien resultaten als deel van de eerste pagina tonen en paginering voor de volgende drie pagina&#39;s verstrekken. U kunt deze implementatie ook gebruiken om een beschrijvende tekst weer te geven, zoals **&quot;43 resultaten gevonden&quot;**.
   * `total=100`, `more=true` - Geeft aan dat het totale aantal treffers groter is dan 100 en dat het exacte aantal niet bekend is. De interface kan maximaal tien pagina&#39;s weergeven als onderdeel van de eerste pagina en paginering voor de volgende tien pagina&#39;s bieden. U kunt dit ook gebruiken om tekst weer te geven zoals **&quot;meer dan 100 resultaten gevonden&quot;**. Aangezien de gebruiker naar de volgende pagina vraag gaat die aan de Bouwer van de Vraag wordt gemaakt zou de grens van `guessTotal` en ook van de `offset` en `limit` parameters verhogen.

`guessTotal` moet ook worden gebruikt in gevallen waarin de gebruikersinterface oneindig schuiven moet gebruiken om te voorkomen dat de Query Builder het exacte aantal treffers bepaalt.

### JAR-bestanden zoeken en deze bestellen, nieuwste eerst {#find-jar-files-and-order-them-newest-first}

`http://localhost:4502/bin/querybuilder.json?type=nt:file&nodename=*.jar&orderby=@jcr:content/jcr:lastModified&orderby.sort=desc`

```xml
type=nt:file
nodename=*.jar
orderby=@jcr:content/jcr:lastModified
orderby.sort=desc
```

### Alle pagina&#39;s zoeken en bestellen op laatst gewijzigd {#find-all-pages-and-order-them-by-last-modified}

`http://localhost:4502/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
```

### Alle pagina&#39;s zoeken en ze bestellen op laatst gewijzigd, maar aflopend {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://localhost:4502/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc]`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### fullText-zoekopdracht, geordend op score {#fulltext-search-ordered-by-score}

`http://localhost:4502/bin/querybuilder.json?fulltext=Management&orderby=@jcr:score&orderby.sort=desc`

```xml
fulltext=Management
orderby=@jcr:score
orderby.sort=desc
```

### Pagina&#39;s zoeken waaraan een bepaald label is toegekend {#search-for-pages-tagged-with-a-certain-tag}

&quot;http://localhost:4502/bin/querybuilder.json?type=cq:Page&amp;tagid=marketing:interest/product&amp;tagid.property=jcr:content/cq:tags&quot;

```xml
type=cq:Page
tagid=marketing:interest/product
tagid.property=jcr:content/cq:tags
```

Gebruik de `tagid` voorspelling zoals in het voorbeeld als u expliciete markering ID kent.

Gebruik de voorspelling `tag` voor het pad van de tagtitel (zonder spaties).

Omdat u in het vorige voorbeeld naar pagina&#39;s ( `cq:Page` knooppunten) zoekt, moet u het relatieve pad van dat knooppunt gebruiken voor de `tagid.property` voorspelling, namelijk `jcr:content/cq:tags`. De standaardinstelling `tagid.property` zou `cq:tags`.

### Zoeken onder meerdere paden (met groepen) {#search-under-multiple-paths-using-groups}

`http://localhost:4502/bin/querybuilder.json?fulltext=Management&group.1_path=/content/geometrixx/en/company/management&group.2_path=/content/geometrixx/en/company/bod&group.p.or=true`

```xml
fulltext=Management
group.p.or=true
group.1_path=/content/geometrixx/en/company/management
group.2_path=/content/geometrixx/en/company/bod
```

Deze vraag gebruikt een *groep* (genoemd &quot; `group`&quot;), die dienst doet om subexpressies binnen een vraag te afbakenen, veel zoals haakjes in meer standaardnota&#39;s doen. Bijvoorbeeld, zou de vorige vraag in een meer bekende stijl als kunnen worden uitgedrukt:

`"Management" and ("/content/geometrixx/en/company/management" or "/content/geometrixx/en/company/bod")`

In de groep in het voorbeeld wordt de `path` predikaat meerdere keren gebruikt. Om de twee instanties van predikaat te onderscheiden en tot orde te brengen (het opdracht geven wordt vereist voor sommige predikaten), moet u prefixen predikaten met *N* `_ where`*N *is de het opdracht geven index. In het vorige voorbeeld zijn de resulterende voorspellingen`1_path`en`2_path`.

De `p` in `p.or` is een speciaal scheidingsteken dat aangeeft dat wat volgt (in dit geval een `or`) een *parameter* van de groep is, in tegenstelling tot een subpredicaat van de groep, zoals `1_path`.

Als er geen voorspelling `p.or` wordt gegeven, dan zijn alle voorspellen ANDed samen, dat wil zeggen, elk resultaat moet aan alle voorspelling voldoen.

>[!NOTE]
>
>U kunt niet hetzelfde numerieke voorvoegsel in één query gebruiken, zelfs niet voor verschillende voorspellingen.

### Eigenschappen zoeken {#search-for-properties}

Hier zoekt u naar alle pagina&#39;s van een bepaalde sjabloon met behulp van de `cq:template` eigenschap:

`http://localhost:4502/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fapps%2fgeometrixx%2ftemplates%2fhomepage&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/apps/geometrixx/templates/homepage
```

Dit heeft het nadeel dat de `jcr:content` knooppunten van de pagina&#39;s, niet de pagina&#39;s zelf, worden geretourneerd. U kunt dit oplossen door op relatief pad te zoeken:

`http://localhost:4502/bin/querybuilder.json?property=jcr%3acontent%2fcq%3atemplate&property.value=%2fapps%2fgeometrixx%2ftemplates%2fhomepage&type=cq%3aPage`

```xml
type=cq:Page
property=jcr:content/cq:template
property.value=/apps/geometrixx/templates/homepage
```

### Meerdere eigenschappen zoeken {#search-for-multiple-properties}

Wanneer het gebruiken van het bezit voorspelt veelvoudige tijden, moet u de aantalprefixen opnieuw toevoegen:

`http://localhost:4502/bin/querybuilder.json?1_property=jcr%3acontent%2fcq%3atemplate&1_property.value=%2fapps%2fgeometrixx%2ftemplates%2fhomepage&2_property=jcr%3acontent%2fjcr%3atitle&2_property.value=English&type=cq%3aPage`

```xml
type=cq:Page
1_property=jcr:content/cq:template
1_property.value=/apps/geometrixx/templates/homepage
2_property=jcr:content/jcr:title
2_property.value=English
```

### Meerdere eigenschapswaarden zoeken {#search-for-multiple-property-values}

Om grote groepen te vermijden wanneer u naar veelvoudige waarden van een bezit ( `"A" or "B" or "C"`) wilt zoeken, kunt u veelvoudige waarden aan het `property` predikaat verstrekken:

`http://localhost:4502/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Products&property.2_value=Square&property.3_value=Events`

```xml
property=jcr:title
property.1_value=Products
property.2_value=Square
property.3_value=Events
```

Voor eigenschappen met meerdere waarden kunt u ook vereisen dat meerdere waarden overeenkomen met ( `"A" and "B" and "C"`):

`http://localhost:4502/bin/querybuilder.json?property=jcr%3atitle&property.and=true&property.1_value=test&property.2_value=foo&property.3_value=bar`

```xml
property=jcr:title
property.and=true
property.1_value=test
property.2_value=foo
property.3_value=bar
```

## Wat wordt geretourneerd, verfijnen {#refining-what-is-returned}

Door gebrek, zal QueryBuilder JSON Servlet een standaardreeks eigenschappen voor elke knoop in het onderzoeksresultaat (b.v. weg, naam, titel, enz.) terugkeren. Als u de controle wilt krijgen over de eigenschappen die worden geretourneerd, kunt u een van de volgende handelingen uitvoeren:

Opgeven

```
p.hits=full
```

In dat geval worden alle eigenschappen voor elk knooppunt opgenomen:

`http://localhost:4502/bin/querybuilder.json?p.hits=full&property=jcr%3atitle&property.value=Triangle`

```xml
property=jcr:title
property.value=Triangle
p.hits=full
```

Gebruiken

```
p.hits=selective
```

en geef de eigenschappen op waarin u wilt gaan werken

```
p.properties
```

gescheiden door een spatie:

`http://localhost:4502/bin/querybuilder.json?p.hits=selective&property=jcr%3atitle&property.value=Triangle`

[ `http://localhost:4502/bin/querybuilder.json?`](http://localhost:4502/bin/querybuilder.json?p.hits=selective&p.properties=sling%3aresourceType%20jcr%3aprimaryType&property=jcr%3atitle&property.value=Triangle) p.hits=selectieve&amp; [](http://localhost:4502/bin/querybuilder.json?p.hits=selective&p.nodedepth=5&p.properties=sling%3aresourceType%20jcr%3apath&property=jcr%3atitle&property.value=Triangle)p.properties=sling%3resourceType%20jcr%3aprimaryType&amp;property=jcr%3atitle&amp;property.value=Triangle

```xml
property=jcr:title
property.value=Triangle
p.hits=selective
p.properties=sling:resourceType jcr:primaryType
```

Een ander ding u kunt doen is kindknopen in de reactie omvatten QueryBuilder. Om dit te doen moet u specificeren

```
p.nodedepth=n
```

waar `n` is het aantal niveaus u de vraag wilt terugkeren. Merk op dat, om een kindknoop te zijn teruggekeerd, het door de eigenschappen selecteur moet worden gespecificeerd

```
p.hits=full
```

Voorbeeld:

`http://localhost:4502/bin/querybuilder.json?p.hits=full&p.nodedepth=5&property=jcr%3atitle&property.value=Triangle`

```xml
property=jcr:title
property.value=Triangle
p.hits=full
p.nodedepth=5
```

## Meer voorspellingen {#morepredicates}

Voor meer predikaten, zie de Predicate pagina [van de Verwijzing van de Bouwer van de](/help/sites-developing/querybuilder-predicate-reference.md)Vraag.

U kunt ook de [JavaDoc controleren op de `PredicateEvaluator` klassen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html). Javadoc voor deze klassen bevat de lijst met eigenschappen die u kunt gebruiken.

Het voorvoegsel van de klassenaam (bijvoorbeeld &quot; `similar`&quot; in [`SimilarityPredicateEvaluator`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)) is de *belangrijkste eigenschap* van de klasse. Dit bezit is ook de naam van predikaat aan gebruik in de vraag (in kleine letters).

Voor dergelijke belangrijkste eigenschappen, kunt u de vraag verkorten en &quot; `similar=/content/en`&quot;in plaats van de volledig - gekwalificeerde variant &quot; `similar.similar=/content/en`&quot; gebruiken. Het volledig gekwalificeerde formulier moet worden gebruikt voor alle niet-hoofdeigenschappen van een klasse.

## Voorbeeld API-gebruik van Query Builder {#example-query-builder-api-usage}

```java
   String fulltextSearchTerm = "Geometrixx";

    // create query description as hash map (simplest way, same as form post)
    Map<String, String> map = new HashMap<String, String>();

// create query description as hash map (simplest way, same as form post)
    map.put("path", "/content");
    map.put("type", "cq:Page");
    map.put("group.p.or", "true"); // combine this group with OR
    map.put("group.1_fulltext", fulltextSearchTerm);
    map.put("group.1_fulltext.relPath", "jcr:content");
    map.put("group.2_fulltext", fulltextSearchTerm);
    map.put("group.2_fulltext.relPath", "jcr:content/@cq:tags");

    // can be done in map or with Query methods
    map.put("p.offset", "0"); // same as query.setStart(0) below
    map.put("p.limit", "20"); // same as query.setHitsPerPage(20) below

    Query query = builder.createQuery(PredicateGroup.create(map), session);
    query.setStart(0);
    query.setHitsPerPage(20);

    SearchResult result = query.getResult();

    // paging metadata
    int hitsPerPage = result.getHits().size(); // 20 (set above) or lower
    long totalMatches = result.getTotalMatches();
    long offset = result.getStartIndex();
    long numberOfPages = totalMatches / 20;

    //Place the results in XML to return to client
    DocumentBuilderFactory factory =     DocumentBuilderFactory.newInstance();
    DocumentBuilder builder = factory.newDocumentBuilder();
    Document doc = builder.newDocument();

    //Start building the XML to pass back to the AEM client
    Element root = doc.createElement( "results" );
    doc.appendChild( root );

    // iterating over the results
    for (Hit hit : result.getHits()) {
       String path = hit.getPath();

      //Create a result element
      Element resultel = doc.createElement( "result" );
      root.appendChild( resultel );

      Element pathel = doc.createElement( "path" );
      pathel.appendChild( doc.createTextNode(path ) );
      resultel.appendChild( pathel );
    }
```

>[!NOTE]
>
>Leer hoe te om een bundel te bouwen OSGi die de API QueryBuilder gebruikt en die bundel OSGi binnen een toepassing van de Manager van de Ervaring van Adobe gebruikt, zie het [Creëren van de bundels OSGi van Adobe CQ die de](https://helpx.adobe.com/experience-manager/using/using-query-builder-api.html)API van de Bouwer van de Vraag gebruiken.

Dezelfde query die via HTTP wordt uitgevoerd met de Query Builder (JSON) Servlet:

`http://localhost:4502/bin/querybuilder.json?path=/content&type=cq:Page&group.p.or=true&group.1_fulltext=Geometrixx&group.1_fulltext.relPath=jcr:content&group.2_fulltext=Geometrixx&group.2_fulltext.relPath=jcr:content/@cq:tags&p.offset=0&p.limit=20`

## Vragen opslaan en laden {#storing-and-loading-queries}

U kunt query&#39;s opslaan in de opslagplaats, zodat u ze later kunt gebruiken. In `QueryBuilder` het bestand wordt de &quot; `storeQuery` methode met de volgende handtekening geleverd:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

Wanneer u de [ methode gebruikt, `QueryBuilder#storeQuery`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html#storequerycomdaycqsearchqueryjavalangstringbooleanjavaxjcrsession) wordt de gegeven methode opgeslagen in de repository als een bestand of als een eigenschap volgens de `Query` `createFile` argumentwaarde. In het volgende voorbeeld wordt getoond hoe u een pad opslaat `Query` als een bestand `/mypath/getfiles` :

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

Eerder opgeslagen query&#39;s kunnen vanaf de repository worden geladen met de [`QueryBuilder#loadQuery`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html#loadqueryjavalangstringjavaxjcrsession) methode:

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

Een bestand dat bijvoorbeeld naar het pad is `Query` opgeslagen, `/mypath/getfiles` kan door het volgende fragment worden geladen:

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## Testen en fouten opsporen {#testing-and-debugging}

Voor het spelen rond en het zuiveren querybuilder vragen, kunt u de debugger console gebruiken QueryBuilder bij

`http://localhost:4502/libs/cq/search/content/querydebug.html`

of anders de querybuilder json servlet op

`http://localhost:4502/bin/querybuilder.json?path=/tmp`

( `path=/tmp` is slechts een voorbeeld).

### Algemene aanbevelingen voor foutopsporing {#general-debugging-recommendations}

### Leg XPath voor uitleg beschikbaar via logboekregistratie {#obtain-explain-able-xpath-via-logging}

Verklaar **alle** vragen tijdens de ontwikkelingscyclus tegen de reeks van de doelindex.

* Laat de logboeken van de BUG voor QueryBuilder toe om onderliggende, verklaarbare vraag van XPath te verkrijgen

   * Ga naar https://&lt;serveradres>:&lt;serverpoort>/system/console/slinglog. Maak een nieuw logger voor `com.day.cq.search.impl.builder.QueryImpl` bij **DEBUG**.

* Zodra DEBUG voor de bovengenoemde klasse is toegelaten, zullen de logboeken XPath tonen dat door de Bouwer van de Vraag wordt geproduceerd.
* Kopieer de vraag van XPath van de logboekingang voor de bijbehorende vraag QueryBuilder, bijvoorbeeld:

   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "Geometrixx") or jcr:contains(jcr:content/@cq:tags, "Geometrixx"))]`

* Plak de vraag van XPath in [Verklaar Vraag](/help/sites-administering/operations-dashboard.md#explain-query) als XPath om het vraagplan te bekrachtigen

### Vraag verklaarbare XPath via debugger van de Bouwer van de Vraag {#obtain-explain-able-xpath-via-the-query-builder-debugger}

* Gebruik foutopsporing AEM QueryBuilder om een uitlegbare XPath-query te genereren:

Verklaar **alle** vragen tijdens de ontwikkelingscyclus tegen de reeks van de doelindex.

**Leg XPath voor uitleg beschikbaar via logboekregistratie**

* Laat de logboeken van de BUG voor QueryBuilder toe om onderliggende, verklaarbare vraag van XPath te verkrijgen

   * Ga naar https://&lt;serveradres>:&lt;serverpoort>/system/console/slinglog. Maak een nieuw logger voor `com.day.cq.search.impl.builder.QueryImpl` bij **DEBUG**.

* Zodra DEBUG voor de bovengenoemde klasse is toegelaten, zullen de logboeken XPath tonen dat door de Bouwer van de Vraag wordt geproduceerd.
* Kopieer de vraag van XPath van de logboekingang voor de bijbehorende vraag QueryBuilder, bijvoorbeeld:

   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "Geometrixx") or jcr:contains(jcr:content/@cq:tags, "Geometrixx"))]`

* Plak de vraag van XPath in [Verklaar Vraag](/help/sites-administering/operations-dashboard.md#explain-query) als XPath om het vraagplan te verkrijgen

**Vraag verklaarbare XPath via debugger van de Bouwer van de Vraag**

* Gebruik foutopsporing AEM QueryBuilder om een uitlegbare XPath-query te genereren:

![chlimage_1-66](assets/chlimage_1-66a.png)

1. Verstrek de vraag van de Bouwer van de Vraag in debugger van de Bouwer van de Vraag
1. De zoekopdracht uitvoeren
1. De gegenereerde XPath ophalen
1. Plak de vraag van XPath in Verklaar Vraag als XPath om het vraagplan te verkrijgen

>[!NOTE]
>
>De vragen van de niet-querybuilder (XPath, JCR-SQL2) kunnen direct aan Verklaar Vraag worden verstrekt.

Voor rundown op hoe te om vragen met QueryBuilder te zuiveren, zie de video hieronder.

>[!NOTE]
>
>[https://www.youtube.com/watch?v=BnyXjhRKYKc](https://www.youtube.com/watch?v=BnyXjhRKYKc)

## Foutopsporing in query&#39;s met logboekregistratie {#debugging-queries-with-logging}

>[!NOTE]
>
>De configuratie van de loggers wordt beschreven in de sectie [Creërend Uw Eigen Loggers en Schrijvers](/help/sites-deploying/configure-logging.md#creating-your-own-loggers-and-writers).

De logboekoutput (niveau INFO) van de implementatie van de vraagbouwer wanneer het uitvoeren van de vraag die in het Testen en het Zuiveren wordt beschreven:

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: limit=20, offset=0[
    {group=group: or=true[
        {1_fulltext=fulltext: fulltext=Geometrixx, relPath=jcr:content}
        {2_fulltext=fulltext: fulltext=Geometrixx, relPath=jcr:content/@cq:tags}
    ]}
    {path=path: path=/content}
    {type=type: type=cq:Page}
]
com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "Geometrixx") or jcr:contains(jcr:content/@cq:tags, "Geometrixx"))]
com.day.cq.search.impl.builder.QueryImpl no filtering predicates
com.day.cq.search.impl.builder.QueryImpl query execution took 69 ms
```

Als u een vraag gebruikend predikaat beoordelaars hebt die filter of die een douaneorde door comparator gebruiken, zal dit ook in de vraag worden vermeld:

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: [
    {nodename=nodename: nodename=*.jar}
    {orderby=orderby: orderby=@jcr:content/jcr:lastModified}
    {type=type: type=nt:file}
]
com.day.cq.search.impl.builder.QueryImpl custom order by comparator: jcr:content/jcr:lastModified
com.day.cq.search.impl.builder.QueryImpl XPath query: //element(*, nt:file)
com.day.cq.search.impl.builder.QueryImpl filtering predicates: {nodename=nodename: nodename=*.jar}
com.day.cq.search.impl.builder.QueryImpl query execution took 272 ms
```

## Javadoc-koppelingen {#javadoc-links}

| **Javadoc** | **Beschrijving** |
|---|---|
| [com.day.cq.search](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/package-summary.html) | Basic QueryBuilder en Query API |
| [com.day.cq.search.result](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/result/package-summary.html) | Resultaat-API |
| [com.day.cq.search.facets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/package-summary.html) | Facetten |
| [com.day.cq.search.facets.buckets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | Emmers (in facetten) |
| [com.day.cq.search.eval](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/package-summary.html) | Voorspelende evaluatoren |
| [com.day.cq.search.facets.extractors](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | Facet Extractor (voor beoordelaars) |
| [com.day.cq.search.writer](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/writer/package-summary.html) | JSON Result Hit Writer voor Querybuilder servlet (/bin/querybuilder.json) |

