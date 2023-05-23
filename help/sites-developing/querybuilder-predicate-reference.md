---
title: Voorlopige naslaggids voor Query Builder
seo-title: Query Builder Predicate Reference
description: Volledige predikate verwijzing voor de Bouwer van de Vraag API.
seo-description: Complete predicate reference for the Query Builder API.
uuid: af0e269e-7d52-4032-b22e-801c7b5dccfa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
discoiquuid: 94a05894-743a-4ace-a292-bfee90ba9068
exl-id: 54b942f9-5dd9-4826-9a0a-028f2d7b8e41
source-git-commit: f97eb2e028263016131b0c86be5a0508ae4def9b
workflow-type: tm+mt
source-wordcount: '2371'
ht-degree: 0%

---

# Voorlopige naslaggids voor Query Builder{#query-builder-predicate-reference}

>[!CAUTION]
>
>De informatie op deze pagina is niet volledig.
>
>Zie de lijst onder **Beschikbare voorspellingen** op de Foutopsporingsconsole van de Bouwer van de Vraag; bijvoorbeeld :
>* [http://localhost:4502/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)
>
>Zie bijvoorbeeld:
>
>* [http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29](http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29)


## Algemeen {#general}

* [basis](#root)
* [groep](#group)
* [ordonneren](#orderby)

## Voorspellen {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [exclusief paden](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [fulltext](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [taal](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [hoofdmiddel](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [lidOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodenaam](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [pad](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [eigenschap](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [opgeslagen query](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [gelijkaardig](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [tag](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagzoeken](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### boolproperty {#boolproperty}

Komt overeen met de JCR BOOLEAN-eigenschappen. Accepteert alleen de waarden &quot; `true`&quot; en &quot; `false`&quot;. In het geval van &quot; `false`&quot;, komt deze overeen als de eigenschap de waarde &quot; `false`&quot; of als het überhaupt niet bestaat. Dit kan handig zijn om te controleren op Booleaanse markeringen die alleen zijn ingesteld wanneer deze zijn ingeschakeld.

De overgeërfde &quot; `operation`&quot; parameter heeft geen betekenis.

Ondersteunt facetextractie. Zal emmers leveren voor elk `true` of `false` waarde, maar alleen voor bestaande eigenschappen.

#### Eigenschappen {#properties}

* **boolproperty**
relatief pad naar eigenschap, bijvoorbeeld 
`myFeatureEnabled` of `jcr:content/myFeatureEnabled`

* **value**
waarde waarop de eigenschap moet worden gecontroleerd, &quot; 
`true`&quot; of &quot; `false`&quot;

### contentfragment {#contentfragment}

Hiermee beperkt u het resultaat tot inhoudsfragmenten.

Filteren wordt niet ondersteund.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-1}

* **contentfragment**
Deze kan met elke waarde worden gebruikt om te controleren op inhoudsfragmenten.

### dateComparison {#datecomparison}

Vergelijkt twee JCR DATE-eigenschappen met elkaar. Kan testen of ze gelijk, ongelijk, groter dan of groter dan of gelijk zijn.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

#### Eigenschappen {#properties-2}

* **property1**

   path to first date, eigenschap

* **property2**

   path to second date, eigenschap

* **bewerking**

   &quot; `equals`&quot; voor exacte overeenkomst, &quot; `!=`&quot; voor de vergelijking van ongelijkheid &quot; `greater`&quot; voor eigenschap1 groter dan eigenschap2, &quot; `>=`&quot; voor property1 groter dan of gelijk aan property2. De standaardwaarde is &quot; `equals`&quot;.

### daterange {#daterange}

Hiermee worden de JCR-DATE-eigenschappen vergeleken met een datum-/tijdinterval. Hierbij wordt de ISO8601-indeling gebruikt voor datums en tijden ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke vertegenwoordiging toe, zoals `YYYY-MM-DD`. U kunt de tijdstempel ook opgeven als het aantal milliseconden dat is verstreken sinds 1970 in de UTC-tijdzone, de unieke tijdnotatie.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Ondersteunt facetextractie. Zal emmers &quot;vandaag&quot;, &quot;deze week&quot;, &quot;deze maand&quot;, &quot;laatste 3 maanden&quot;, &quot;dit jaar&quot;, &quot;vorig jaar&quot; en &quot;eerder dan vorig jaar&quot; leveren.

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **eigenschap**

   relatief pad naar een `DATE` eigenschap, bijvoorbeeld `jcr:lastModified`

* **lowerBound**

   lagere datum gebonden aan check eigenschap for, bijvoorbeeld `2014-10-01`

* **lowerOperation**

   &quot; `>`&quot; (nieuwer) of &quot; `>=`&quot; (bij of hoger), van toepassing op `lowerBound`. De standaardwaarde is &quot; `>`&quot;.

* **upperBound**

   bovenaan gebonden om eigenschap te controleren voor, bijvoorbeeld `2014-10-01T12:15:00`

* **upperOperation**

   &quot; `<`&quot; (ouder) of &quot; `<=`&quot; (bij of ouder) `upperBound`. De standaardwaarde is &quot; `<`&quot;.

* **timeZone**

   Id van tijdzone die moet worden gebruikt wanneer deze niet wordt gegeven als een ISO-8601-datumtekenreeks. De standaardwaarde is de standaardtijdzone van het systeem.

### exclusief paden {#excludepaths}

Hiermee sluit u knooppunten uit van het resultaat wanneer het pad ervan overeenkomt met een reguliere expressie.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-4}

* **exclusief paden**

   reguliere expressie komt overeen met resultaatpaden, met uitzondering van overeenkomende paden uit het resultaat.

### fulltext {#fulltext}

Zoekt naar termen in de fullText-index.

Filteren wordt niet ondersteund.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-5}

* **fulltext**

   de zoekterm(en) voor fulltext

* **relPath**

   het relatieve pad naar de eigenschap of het subknooppunt. Deze eigenschap is optioneel.

### groep {#group}

Hiermee kunt u geneste voorwaarden maken. Groepen kunnen geneste groepen bevatten. Alles in een querybuilderquery bevindt zich impliciet in een hoofdgroep, die kan hebben `p.or` en `p.not` ook parameters.

Voorbeeld voor het afstemmen van een van beide eigenschappen op een waarde:

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Dit is conceptueel `(1_property` OF `2_property)`.

Voorbeeld voor geneste groepen:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Hiermee wordt gezocht naar de term &quot;**Beheer**&quot; binnen pagina&#39;s in `/content/geometrixx/en` of in activa `/content/dam/geometrixx`.

Dit is conceptueel `fulltext AND ( (path AND type) OR (path AND type) )`. Houd er rekening mee dat dergelijke OR-verbindingen goede indexen nodig hebben voor de prestaties.

#### Eigenschappen {#properties-6}

* **p.or**

   indien ingesteld op &quot; `true`&quot;, slechts één predikaat in de groep moet aanpassen. Dit is standaard &quot; `false`&quot;, wat betekent dat alles moet overeenkomen

* **p.not**

   indien ingesteld op &quot; `true`&quot;, wordt de groep genegeerd (standaard ingesteld op &quot; `false`&quot;)

* **&lt;predicate>**

   voegt geneste voorspellingen toe

* **N_&lt;predicate>**

   voegt meerdere geneste voorspellingen van hetzelfde moment toe, zoals `1_property, 2_property, ...`

### hasPermission {#haspermission}

Beperkt het resultaat tot punten waar de huidige zitting gespecificeerde heeft [JCR-bevoegdheden.](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **hasPermission**

   de door komma&#39;s gescheiden voorrechten van het JCR die de huidige gebruikerszitting ALLE voor de knoop in kwestie moet hebben; bijvoorbeeld `jcr:write`, `jcr:modifyAccessControl`

### taal {#language}

Hiermee zoekt u CQ-pagina&#39;s in een specifieke taal. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken, dat vaak de taal of landinstelling in een sitestructuur op hoofdniveau bevat.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Ondersteunt facetextractie. Zal emmers voor elke unieke taalcode verstrekken.

#### Eigenschappen {#properties-8}

* **taal**

   ISO-taalcode, bijvoorbeeld &quot; `de`&quot;

### hoofdmiddel {#mainasset}

Controleert of een knooppunt een DAM-hoofdmiddel is en geen subelement. Dit is eigenlijk elk knooppunt dat zich niet binnen een &#39;subassets&#39;-knooppunt bevindt. Dit controleert niet op de `dam:Asset` knooppunttype. Om dit te gebruiken predikaat, eenvoudig plaats &quot; `mainasset=true`&quot; of &quot; `mainasset=false`&quot; , zijn er geen eigenschappen meer.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Ondersteunt facetextractie. Twee emmers voor hoofd- en subactiva.

#### Eigenschappen {#properties-9}

* **hoofdmiddel**

   boolean, &quot; `true`&quot; voor de belangrijkste activa, &quot; `false`&quot; voor subactiva

### lidOf {#memberof}

Hiermee worden items gevonden die lid zijn van een specifieke [slingerbronverzameling](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html).

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken. Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-10}

* **lidOf**

   pad van Sling-bronverzameling

### nodenaam {#nodename}

Komt overeen met namen van JCR-knooppunten.

Ondersteunt facetextractie. Wordt gebruikt voor emmers voor elke unieke knooppuntnaam (bestandsnaam).

#### Eigenschappen {#properties-11}

* **nodenaam**

   nodennaampatroon dat jokertekens toestaat: `*` = een of geen teken, `?` = een teken, `[abc]` = alleen tekens tussen haakjes

### notexpired {#notexpired}

Komt overeen met items door te controleren of een JCR DATE-eigenschap groter of gelijk is aan de huidige servertijd. Hiermee kunt u een &quot; `expiresAt`&quot; Vergelijkbare datum, eigenschap en beperking tot alleen de eigenschappen die nog niet zijn verlopen ( `notexpired=true`) of die reeds zijn verlopen ( `notexpired=false`).

Filteren wordt niet ondersteund.

Ondersteunt facetextractie op dezelfde manier als de daterange predikaat.

#### Eigenschappen {#properties-12}

* **notexpired**

   boolean, &quot; `true`&quot; nog niet verstreken (datum in de toekomst of gelijk aan), &quot; `false`&quot; voor verlopen (datum in het verleden) (vereist)

* **eigenschap**

   relatief pad naar `DATE` te controleren eigenschap (vereist)

### ordonneren {#orderby}

Hiermee kunt u het resultaat sorteren. Als het opdracht geven door veelvoudige eigenschappen wordt vereist, moet dit voorspellen veelvoudige tijden toevoegen gebruikend het aantalprefix, zoals `1_orderby=first`, `2_oderby=second`.

#### Eigenschappen {#properties-13}

* **ordonneren**

   De JCR-eigenschapsnaam die wordt aangeduid door een regelafstand @, bijvoorbeeld `@jcr:lastModified` of `@jcr:content/jcr:title`of een andere voorspelling in de query, bijvoorbeeld `2_property`, waarop wordt gesorteerd

* **sorteren**

   sorteerrichting: &quot; `desc`&quot; voor aflopend of &quot; `asc`&quot; voor oplopend (standaard)

* **case**

   indien ingesteld op &quot; `ignore`&quot; het sorteren ongevoelig zal maken, wat betekent dat &quot;a&quot; vóór &quot;B&quot; komt; indien leeg of weggelaten, wordt onderscheid gemaakt tussen hoofdletters en kleine letters, wat betekent dat &quot;B&quot; voor &quot;a&quot; komt

### pad {#path}

Hiermee zoekt u in een bepaald pad.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-14}

* **pad**

   padpatroon; afhankelijk van de exacte waarde, komt de volledige substructuur overeen (zoals bij toevoegen) `//*` in xpath, maar merk op dat dit niet het basispad bevat) (exact=false, standaard) of alleen een exact pad dat overeenkomt met, wat jokertekens kan bevatten ( `*`); als self is ingesteld, wordt de gehele substructuur, inclusief het basisknooppunt, doorzocht

* **exact**

   indien `exact` is waar/aan, moet de nauwkeurige weg aanpassen maar het kan eenvoudige vervangingen bevatten ( `*`), die gelijk zijn aan namen, maar niet &quot; `/`&quot;; als deze onwaar is (standaard), worden alle afstammingen opgenomen (optioneel)

* **plat**

   zoekt alleen de directe onderliggende objecten (zoals toevoegen &quot; `/*`&quot; in xpath) (alleen gebruikt als &quot; `exact`&#39; is niet waar, optioneel)

* **zelfzucht**

   zoekt de subtree maar omvat de basisknoop die als weg (geen vervangingen) wordt gegeven

### eigenschap {#property}

Komt overeen met de JCR-eigenschappen en hun waarden.

Ondersteunt facetextractie. Zal emmers verstrekken voor elke unieke eigenschapwaarde in de resultaten.

#### Eigenschappen {#properties-15}

* **eigenschap**

   relatief pad naar eigenschap, bijvoorbeeld `jcr:title`

* **value**

   waarde om eigenschap te controleren voor; volgt het JCR-eigenschapstype op tekenreeksconversies

* **N_value**

   gebruiken `1_value`, `2_value`, ... controleren op meerdere waarden (gecombineerd met `OR` standaard, met `AND` if en=true) (sinds 5.3)

* **en**

   ingesteld op true voor het combineren van meerdere waarden ( `N_value`) met EN (sinds 5.3)

* **bewerking**

   &quot;`equals`&quot; voor exacte overeenkomst (standaardwaarde), &quot; `unequals`&quot; voor de vergelijking van ongelijkheid &quot; `like`&quot; voor het gebruik van de `jcr:like` xpath, functie (optioneel), &quot; `not`&quot; voor geen overeenkomst (bijv. &quot;`not(@prop)`&quot; in xpath, value param will be ignored) of &quot; `exists`&quot; voor existentiecontrole (waarde kan waar zijn - eigenschap moet bestaan, standaardwaarde - of vals - zelfde als &quot; `not`&quot;)

* **diepte**

   aantal jokertekenniveaus waaronder de eigenschap/het relatieve pad kan bestaan (bijvoorbeeld `property=size depth=2` controleert node/size, node/&amp;ast;/size en node/&amp;ast;/&amp;ast;/size)

### rangeproperty {#rangeproperty}

Hiermee wordt een JCR-eigenschap vergeleken met een interval. Dit geldt voor eigenschappen met lineaire typen, zoals `LONG`, `DOUBLE` en `DECIMAL`. Voor `DATE` raadpleeg de daterange predikaat die de invoer van de datumnotatie heeft geoptimaliseerd.

U kunt een ondergrens en een bovengrens of slechts één van hen bepalen. De bewerking (bijv. &quot;kleiner dan&quot; of &quot;kleiner of gelijk aan&quot;) kan ook worden opgegeven voor de individuele ondergrens en bovengrens.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-16}

* **eigenschap**

   relatief pad naar eigenschap

* **lowerBound**

   ondergrens om eigenschap te controleren voor

* **lowerOperation**

   &quot; `>`&quot; (standaardwaarde) of &quot; `>=`&quot;, is van toepassing op `lowerValue`

* **upperBound**

   bovenaan gebonden om eigenschap te controleren voor

* **upperOperation**

   &quot; `<`&quot; (standaardwaarde) of &quot; `<=`&quot;, is van toepassing op `lowerValue`

* **decimaal**

   &quot; `true`&quot; als de gecontroleerde eigenschap van het type Decimaal is

### relativedaterange {#relativedaterange}

Overeenkomsten `JCR DATE` eigenschappen op basis van een datum-/tijdinterval waarbij tijdverschuivingen ten opzichte van de huidige servertijd worden gebruikt. U kunt `lowerBound` en `upperBound` met een millisecondenwaarde of de bugzilla-syntaxis `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar). Voorvoegsel met &quot; `-`&quot; om een negatieve verschuiving vóór de huidige tijd aan te geven. Als u alleen `lowerBound` of `upperBound`, zal andere aan 0, die de huidige tijd betekent in gebreke blijven.

Bijvoorbeeld:

* `upperBound=1h` (en `lowerBound`) in de komende uren alles selecteren
* `lowerBound=-1d` (en `upperBound`) in de afgelopen 24 uur alles selecteren
* `lowerBound=-6M` en `upperBound=-3M` zou om het even wat 6 maanden tot 3 maanden oud selecteren
* `lowerBound=-1500` en `upperBound=5500` zou om het even wat tussen 1500 milliseconden in het verleden en 5500 milliseconden in de toekomst selecteren
* `lowerBound=1d` en `upperBound=2d` zou overmorgen alles selecteren

Er wordt geen rekening gehouden met schrikkeljaren en alle maanden zijn 30 dagen.

Filteren wordt niet ondersteund.

Ondersteunt facetextractie op dezelfde manier als de daterange predikaat.

#### Eigenschappen {#properties-17}

* **upperBound**

   hogere datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie

* **lowerBound**

   lagere datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie

### basis {#root}

Hoofdvoorspelbare groep. Steunt alle eigenschappen van een groep en staat toe om globale vraagparameters te plaatsen.

De naam &quot;wortel&quot;wordt nooit gebruikt in een vraag, het is impliciet.

#### Eigenschappen {#properties-18}

* **p.offset**

   getal dat het begin van de resultatenpagina aangeeft, d.w.z. het aantal items dat moet worden overgeslagen

* **p.limit**

   getal dat het paginaformaat aangeeft

* **p.radenTotaal**

   aanbevolen: niet het volledige resultaattotaal berekenen dat kostbaar kan zijn; hetzij een getal dat het maximale totaal aangeeft tot (bijvoorbeeld 1000, een getal dat gebruikers voldoende feedback geeft over de ruwe grootte en exacte getallen voor kleinere resultaten), of &quot; `true`&quot; om slechts tot het noodzakelijke minimum te tellen `p.offset` + `p.limit`

* **p.excerpt**

   indien ingesteld op &quot; `true`&quot;, moet u het volledige tekstfragment in het resultaat opnemen

* **p.hits**

   (alleen voor de JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met de volgende standaardresultaten (uitbreidbaar via de service ResultHitWriter):

   * **eenvoudig**:

      minimale objecten zoals `path`, `title`, `lastmodified`, `excerpt` (indien ingesteld)

   * **volledig**:

      sling JSON rendering van het knooppunt, met `jcr:path` het pad van de treffer aangeven: door gebrek maakt enkel een lijst van de directe eigenschappen van de knoop, omvat een diepere boom met `p.nodedepth=N`, waarbij 0 de gehele oneindige subboom betekent; toevoegen `p.acls=true` om de JCR-machtigingen van de huidige sessie op te nemen voor het opgegeven resultaatitem (toewijzingen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`)

   * **selectief**:

      alleen eigenschappen opgegeven in `p.properties`, dat een spatie gescheiden is (gebruik &quot;+&quot; in URL&#39;s) lijst met relatieve paden; als het relatieve pad een diepte > 1 heeft, worden deze weergegeven als onderliggende objecten; de speciale eigenschap jcr:path bevat het pad van de hit

### opgeslagen query {#savedquery}

Omvat alle predikaten van een persisted querybuilder vraag in de huidige vraag als subgroup predikaat.

Hiermee wordt geen extra query uitgevoerd, maar wordt de huidige query uitgebreid.

De vragen kunnen programmatically worden voortgeduurd gebruikend `QueryBuilder#storeQuery()`. De indeling kan een tekenreekseigenschap met meerdere regels of een `nt:file` knooppunt dat de query als een tekstbestand in Java-eigenschappen-indeling bevat.

Biedt geen ondersteuning voor facetextractie voor de voorspelling van de opgeslagen query.

#### Eigenschappen {#properties-19}

* **opgeslagen query**

   pad naar de opgeslagen query (eigenschap String of `nt:file` node)

### gelijkaardig {#similar}

Gelijksoortige zoekopdracht met JCR XPath `rep:similar()`.

Filteren wordt niet ondersteund. Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-20}

* **gelijkaardig**
absolute weg aan de knoop waarvoor om gelijkaardige knopen te vinden

* **lokaal**
een relatief pad naar een afstammend knooppunt of 
`.` voor het huidige knooppunt (optioneel, standaard is &quot; `.`&quot;)

### tag {#tag}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags door titelpaden voor tags op te geven.

Ondersteunt facetextractie. Hiermee geeft u emmers voor elke unieke tag op met behulp van het huidige pad voor de tagtitel.

#### Eigenschappen {#properties-21}

* **tag**

   titelpad van tag naar, bijvoorbeeld &quot;Eigenschappen van element: Oriëntatie / Liggend&quot;

* **N_value**

   gebruiken `1_value`, `2_value`, ... controleren op meerdere tags (gecombineerd met `OR` standaard, met `AND` if en=true) (sinds 5.6)

* **eigenschap**

   eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;)

### tagid {#tagid}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags, door tag-id&#39;s op te geven.

Ondersteunt facetextractie. Hiermee geeft u emmers voor elke unieke tag op met de huidige tag-id.

#### Eigenschappen {#properties-22}

* **tagid**

   tag-id die moet worden gezocht, bijvoorbeeld &quot; `properties:orientation/landscape`&quot;

* **N_value**

   gebruiken `1_value`, `2_value`, ... controleren op meerdere tags (gecombineerd met `OR` standaard, met `AND` if en=true) (sinds 5.6)

* **eigenschap**

   eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;)

### tagzoeken {#tagsearch}

Zoekt naar inhoud gelabeld met een of meer tags door trefwoorden op te geven. Hiermee zoekt u eerst naar tags die deze trefwoorden bevatten in de titels en beperkt u het resultaat vervolgens tot alleen items die met deze trefwoorden zijn getagd.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#Properties-1}

* **tagzoeken**

   trefwoord waarnaar moet worden gezocht in titels van tags

* **eigenschap**

   eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;)

* **lang**

   om alleen in een bepaalde gelokaliseerde tagtitel te zoeken (bijvoorbeeld &quot; `de`&quot;)

* **alles**

   (bool) doorzoek volledige labeltekst, dus alle titels, beschrijving enz. (heeft voorrang op &quot;l `ang`&quot;)

### type {#type}

Hiermee beperkt u de resultaten tot een specifiek JCR-knooppunttype, zowel het primaire knooppunttype als het mixintype. Dit zal ook subtypes van dat knooptype vinden. Merk op dat de gegevensopslagplaats onderzoeksindexen de knooppunttypes voor efficiënte uitvoering moeten behandelen.

Ondersteunt facetextractie. Zal emmers voor elk uniek type in de resultaten verstrekken.

#### Eigenschappen {#Properties-2}

* **type**

   knooppunttype of mixin naam aan onderzoek naar, bijvoorbeeld `cq:Page`
