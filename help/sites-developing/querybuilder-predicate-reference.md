---
title: Voorlopige naslaggids voor Query Builder
description: Volledige predikate verwijzing voor de Bouwer van de Vraag API.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
exl-id: 54b942f9-5dd9-4826-9a0a-028f2d7b8e41
solution: Experience Manager, Experience Manager Sites
feature: Developing,Search,Query Builder
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '2313'
ht-degree: 0%

---

# Voorlopige naslaggids voor Query Builder{#query-builder-predicate-reference}

>[!CAUTION]
>
>De informatie op deze pagina is niet volledig.
>
>Voor volledige informatie, zie de lijst onder **Beschikbare predikaten** op de Debugger van de Bouwer van de Vraag console; bijvoorbeeld, bij:
>* [ http://localhost:4502/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)
>
>Zie bijvoorbeeld:
>
>* [ http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29](http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29)

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
* [gelabeld](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagzoeken](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### boolproperty {#boolproperty}

Komt overeen met de JCR BOOLEAN-eigenschappen. Accepteert alleen de waarden &quot; `true`&quot; en &quot; `false`&quot;. Als &quot; `false`&quot;, komt dit overeen als de eigenschap de waarde &quot; `false`&quot; heeft of als deze helemaal niet bestaat. Dit kan handig zijn om te controleren op Booleaanse markeringen die alleen zijn ingesteld wanneer deze zijn ingeschakeld.

De overgeërfde parameter &quot; `operation`&quot; heeft geen betekenis.

Ondersteunt facetextractie. Verstrekt emmers voor elke `true` of `false` waarde, maar slechts voor bestaande eigenschappen.

#### Eigenschappen {#properties}

* **boolproperty**
Relatief pad naar eigenschap, bijvoorbeeld `myFeatureEnabled` of `jcr:content/myFeatureEnabled` .

* **waarde**
Waarde waarvoor de eigenschap moet worden gecontroleerd: &quot; `true`&quot; of &quot; `false`&quot;.

### contentfragment {#contentfragment}

Hiermee beperkt u het resultaat tot inhoudsfragmenten.

Filteren wordt niet ondersteund.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-1}

* **contentfragment**
Deze kan met elke waarde worden gebruikt om te controleren op inhoudsfragmenten.

### dateComparison {#datecomparison}

Vergelijkt twee JCR DATE-eigenschappen met elkaar. U kunt testen of ze gelijk, ongelijk, groter dan of groter dan of gelijk zijn.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt.

#### Eigenschappen {#properties-2}

* **property1**

  Eigenschap pad naar eerste datum.

* **property2**

  Pad naar tweede-datumeigenschap.

* **verrichting**

  &quot; `equals`&quot; voor exacte overeenkomst, &quot; `!=`&quot; voor ongelijkheidsvergelijking, &quot; `greater`&quot; voor eigenschap1 groter dan eigenschap2, &quot; `>=`&quot; voor eigenschap1 groter dan of gelijk aan eigenschap2. De standaardwaarde is &quot; `equals`&quot;.

### daterange {#daterange}

Hiermee worden de JCR-DATE-eigenschappen vergeleken met een datum-/tijdinterval. Dit gebruikt ISO8601
notatie voor datums en tijden ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke representaties toe, zoals `YYYY-MM-DD` . U kunt de tijdstempel ook opgeven als het aantal milliseconden dat is verstreken sinds 1970 in de UTC-tijdzone, de UNIX®-tijdnotatie.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Ondersteunt facetextractie. Verstrekt emmers &quot;vandaag&quot;, &quot;deze week&quot;, &quot;deze maand&quot;, &quot;laatste drie maanden&quot;, &quot;dit jaar&quot;, &quot;vorig jaar&quot; en &quot;vroeger dan vorig jaar&quot;.

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **bezit**

  Relatief pad naar een eigenschap `DATE` , bijvoorbeeld `jcr:lastModified` .

* **lowerBound**

  Lagere datum gebonden aan check eigenschap for, bijvoorbeeld `2014-10-01`.

* **lowerOperation**

  &quot; `>`&quot; (nieuwer) of &quot; `>=`&quot; (hoger of hoger) is van toepassing op de `lowerBound` . De standaardwaarde is &quot; `>`&quot;.

* **upperBound**

  Bovenaan gebonden om de eigenschap te controleren op, bijvoorbeeld, `2014-10-01T12:15:00` .

* **upperOperation**

  &quot; `<`&quot; (ouder) of &quot; `<=`&quot; (ouder of ouder), is van toepassing op `upperBound` . De standaardwaarde is &quot; `<`&quot;.

* **timeZone**

  Id van tijdzone die moet worden gebruikt wanneer deze niet wordt gegeven als een ISO-8601-datumtekenreeks. De standaardwaarde is de standaardtijdzone van het systeem.

### exclusief paden {#excludepaths}

Hiermee sluit u knooppunten uit van het resultaat wanneer het pad ervan overeenkomt met een reguliere expressie.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-4}

* **exclusief wegen**

  Gewone expressie die overeenkomt met resultaatpaden, exclusief overeenkomende paden uit het resultaat.

### fulltext {#fulltext}

Zoekt naar termen in de fullText-index.

Filteren wordt niet ondersteund.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-5}

* **fulltext**

  De zoektermen in fulltext.

* **relPath**

  Het relatieve pad naar de eigenschap of het subknooppunt. Deze eigenschap is optioneel.

### groep {#group}

Hiermee kunnen geneste voorwaarden worden gemaakt. Groepen kunnen geneste groepen bevatten. Alles in een query builder-query bevindt zich impliciet in een hoofdgroep, die ook `p.or` - en `p.not` -parameters kan hebben.

Voorbeeld voor het afstemmen van een van de twee eigenschappen op een waarde:

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Dit is conceptueel `(1_property` OR `2_property)` .

Voorbeeld voor geneste groepen:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Dit zoekt naar de termijn &quot;**Beheer**&quot;binnen pagina&#39;s in `/content/geometrixx/en` of in activa in `/content/dam/geometrixx`.

Dit is conceptueel `fulltext AND ( (path AND type) OR (path AND type) )` . Zulke OF verbindingen hebben goede indexen voor prestaties nodig.

#### Eigenschappen {#properties-6}

* **p.or**

  Indien ingesteld op &quot; `true`&quot;, mag slechts één voorspelling in de groep overeenkomen. Dit is standaard &quot; `false`&quot;, wat betekent dat alles moet overeenkomen

* **p.not**

  Indien ingesteld op &quot; `true`&quot;, wordt de groep genegeerd (standaard ingesteld op &quot; `false`&quot;).

* **&lt;preate>**

  Hiermee voegt u geneste voorvertoningen toe.

* **N_&lt;predicate>**

  Hiermee voegt u meerdere geneste voorspellen tegelijk toe, zoals `1_property, 2_property, ...` .

### hasPermission {#haspermission}

Beperkt het resultaat tot punten waar de huidige zitting de gespecificeerde [ voorrechten JCR heeft.](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **hasPermission**

  JCR-bevoegdheden die door komma&#39;s worden gescheiden en die ALLES voor de huidige gebruikerssessie moet hebben. Bijvoorbeeld `jcr:write` , `jcr:modifyAccessControl` .

### taal {#language}

Hiermee zoekt u CQ-pagina&#39;s in een specifieke taal. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken, dat vaak de taal of landinstelling in een site-structuur op hoofdniveau bevat.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt.

Ondersteunt facetextractie. Verstrekt emmers voor elke unieke taalcode.

#### Eigenschappen {#properties-8}

* **taal**

  ISO taalcode, bijvoorbeeld, &quot;`de`&quot;

### hoofdmiddel {#mainasset}

Controleert of een knooppunt een DAM-hoofdelement is en geen subelement. Dit is eigenlijk elk knooppunt dat zich niet binnen een &#39;subassets&#39;-knooppunt bevindt. Dit controleert niet op het knooppunttype `dam:Asset`. Als u deze voorspelling wilt gebruiken en &quot; `mainasset=true`&quot; of &quot; `mainasset=false`&quot; wilt instellen, zijn er geen eigenschappen meer.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt.

Steunt facetextractie en verstrekt twee emmers voor hoofd en subassets.

#### Eigenschappen {#properties-9}

* **mainasset**

  Boolean, &quot; `true`&quot; voor hoofdelementen, &quot; `false`&quot; voor subelementen.

### lidOf {#memberof}

Vindt punten die lid van een specifieke [ sling middelinzameling ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) zijn.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt. Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-10}

* **memberOf**

  Pad van Sling-bronverzameling.

### nodenaam {#nodename}

Komt overeen met namen van JCR-knooppunten.

Ondersteunt facetextractie. Verstrekt emmers voor elke unieke knoopnaam (filename).

#### Eigenschappen {#properties-11}

* **nodename**

  Naamnotatiepatroon waarbij jokertekens zijn toegestaan: `*` = willekeurig of geen teken, `?` = willekeurig teken, `[abc]` = alleen tekens tussen haakjes.

### notexpired {#notexpired}

Komt overeen met items door te controleren of een JCR DATE-eigenschap groter of gelijk is aan de huidige servertijd. Dit kan worden gebruikt om een &quot; `expiresAt`&quot;-achtige datumeigenschap in te schakelen en alleen de eigenschappen die nog niet zijn verlopen ( `notexpired=true` ) of die al zijn verlopen ( `notexpired=false` ).

Filteren wordt niet ondersteund.

Ondersteunt facetextractie op dezelfde manier als de daterange predikaat.

#### Eigenschappen {#properties-12}

* **notexpired**

  Boolean, &quot; `true`&quot; for not expired yet (date in the future or equal), &quot; `false`&quot; for expired (date in the past) (required).

* **bezit**

  Relatief pad naar de eigenschap `DATE` die moet worden gecontroleerd (vereist).

### ordonneren {#orderby}

Hiermee kunt u de resultaten sorteren. Als de volgorde door meerdere eigenschappen vereist is, moet deze voorspelling meerdere keren worden toegevoegd met behulp van het voorvoegsel number, zoals `1_orderby=first`, `2_oderby=second` .

#### Eigenschappen {#properties-13}

* **orderby**

  De JCR-eigenschapnaam die wordt aangeduid door een regelafstand @, bijvoorbeeld `@jcr:lastModified` of `@jcr:content/jcr:title` , of een andere voorspelling in de query, bijvoorbeeld `2_property` , waarop moet worden gesorteerd.

* **soort**

  Sorteer de richting &quot; `desc`&quot; voor aflopend of &quot; `asc`&quot; voor oplopend (standaard).

* **geval**

  Indien ingesteld op `ignore` , wordt het sorteren van hoofdletters en kleine letters ongevoelig, wat betekent dat &quot;a&quot; komt vóór &quot;B&quot;; als het sorteren leeg is of wordt weggelaten, is het sorteren hoofdlettergevoelig, wat betekent dat &quot;B&quot; komt vóór &quot;a&quot;

### pad {#path}

Hiermee zoekt u in een bepaald pad.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-14}

* **weg**

  Padpatroon. Afhankelijk van het exacte aantal komt ofwel de volledige subboomstructuur overeen (zoals `//*` wordt toegevoegd in xpath, maar dit omvat niet het basispad) (exact=false, standaard), ofwel alleen een exacte padovereenkomst, die jokertekens kan bevatten ( `*` ); als self is ingesteld, wordt de volledige substructuur, inclusief het basisknooppunt, doorzocht.

* **nauwkeurig**

  Als `exact` true/on is, moet het exacte pad overeenkomen, maar het kan eenvoudige jokertekens ( `*` ) bevatten, die identieke namen, maar niet &quot; `/` &quot;. Als het pad false is (standaard), worden alle afstammingen opgenomen (optioneel).

* **vlak**

  Hiermee zoekt u alleen de directe onderliggende elementen (zoals &quot; `/*`&quot; toevoegen in xpath) (alleen gebruikt als &#39; `exact`&#39; niet true is, optioneel).

* **zelf**

  Doorzoekt de substructuur maar neemt het basisknooppunt op dat als pad wordt opgegeven (geen jokertekens).

### eigenschap {#property}

Komt overeen met de JCR-eigenschappen en hun waarden.

Ondersteunt facetextractie. Verstrekt emmers voor elke unieke bezitswaarde in de resultaten.

#### Eigenschappen {#properties-15}

* **bezit**

  Relatief pad naar eigenschap, bijvoorbeeld `jcr:title` .

* **waarde**

  Waarde waarop de eigenschap moet worden gecontroleerd; volgt het eigenschapstype JCR op tekenreeksconversies.

* **N_value**

  Gebruik `1_value`, `2_value` , ... om te controleren op meerdere waarden (standaard gecombineerd met `OR` , met `AND` if en=true) (sinds 5.3).

* **en**

  Ingesteld op true voor het combineren van meerdere waarden ( `N_value`) met AND (sinds 5.3).

* **verrichting**

  &quot;`equals`&quot; voor exacte overeenkomst (standaardwaarde), &quot; `unequals`&quot; voor ongelijkheidsvergelijking, &quot; `like`&quot; voor het gebruik van de `jcr:like` xpath-functie (optioneel), &quot; `not` &quot; voor geen overeenkomst (bijvoorbeeld &quot;`not(@prop)`&quot; in xpath, value param wordt genegeerd) of &quot; `exists`&quot; voor controle op bestaan (waarde kan waar zijn - eigenschap moet bestaan, de standaardwaarde - of false - hetzelfde als &quot; `not`&quot;).

* **diepte**

  Aantal jokertekenniveaus waaronder de eigenschap/het relatieve pad kan bestaan (bijvoorbeeld `property=size depth=2` controleert knooppunt/grootte, knooppunt/&ast;/size en knooppunt/&ast;/&ast;/&ast;/size).

### rangeproperty {#rangeproperty}

Hiermee wordt een JCR-eigenschap vergeleken met een interval. Dit geldt voor eigenschappen met lineaire typen, zoals `LONG` , `DOUBLE` en `DECIMAL` . Zie voor `DATE` de daterange-voorspelling die geoptimaliseerde invoer voor de datumnotatie heeft.

U kunt een ondergrens en een bovengrens of slechts één van hen bepalen. De bewerking (bijvoorbeeld &quot;kleiner dan&quot; of &quot;kleiner of gelijk aan&quot;) kan ook afzonderlijk worden opgegeven voor de onderste en bovenste binding.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-16}

* **bezit**

  Relatief pad naar eigenschap.

* **lowerBound**

  Ondergrens om eigenschap te controleren voor.

* **lowerOperation**

  &quot; `>`&quot; (standaardwaarde) of &quot; `>=`&quot;, is van toepassing op `lowerValue`

* **upperBound**

  Bovengrens om de eigenschap te controleren op.

* **upperOperation**

  &quot; `<`&quot; (standaardwaarde) of &quot; `<=`&quot;, is van toepassing op `lowerValue`

* **decimaal**

  &quot; `true`&quot; als de gecontroleerde eigenschap van het type Decimaal is

### relativedaterange {#relativedaterange}

Vergelijkt `JCR DATE` eigenschappen met een datum-/tijdinterval met tijdverschuivingen ten opzichte van de huidige servertijd. U kunt `lowerBound` en `upperBound` opgeven met een millisecondenwaarde of de bugzilla-syntaxis `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uur, vier dagen, vijf weken, zes maanden, zeven jaar). Voorvoegsel met &quot; `-`&quot; om een negatieve verschuiving vóór de huidige tijd aan te geven. Als u alleen `lowerBound` of `upperBound` opgeeft, wordt de andere standaard ingesteld op 0, wat de huidige tijd betekent.

Bijvoorbeeld:

* `upperBound=1h` (en geen `lowerBound` ) selecteert de afbeelding in het volgende uur
* `lowerBound=-1d` (en geen `upperBound` ) selecteert niets in de afgelopen 24 uur
* `lowerBound=-6M` en `upperBound=-3M` selecteert elke 6 maanden tot 3 maanden oud
* `lowerBound=-1500` en `upperBound=5500` selecteert in het vervolg iets tussen 1500 milliseconden en 5500 milliseconden
* `lowerBound=1d` en `upperBound=2d` zouden overmorgen iets selecteren

Het neemt schrikkeljaren niet in overweging en alle maanden zijn 30 dagen.

Filteren wordt niet ondersteund.

Ondersteunt facetextractie op dezelfde manier als de daterange predikaat.

#### Eigenschappen {#properties-17}

* **upperBound**

  Bovenste datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie.

* **lowerBound**

  Lagere datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie.

### basis {#root}

Hoofdvoorspelbare groep. Steunt alle eigenschappen van een groep en laat u globale vraagparameters plaatsen.

De naam &quot;wortel&quot;wordt nooit gebruikt in een vraag, het is impliciet.

#### Eigenschappen {#properties-18}

* **p.offset**

  Het getal dat het begin van de resultatenpagina aangeeft, dat wil zeggen het aantal items dat moet worden overgeslagen.

* **p.limit**

  Het getal dat het paginaformaat aangeeft.

* **p.radenTotal**

  Aanbevolen: vermijd het berekenen van het volledige resultaattotaal, wat kostbaar kan zijn. Ofwel een getal dat het maximale totaal aangeeft dat moet worden geteld tot (bijvoorbeeld 1000, een getal dat gebruikers voldoende feedback geeft op de ruwe grootte en exacte getallen voor kleinere resultaten), ofwel &quot; `true`&quot; om alleen te tellen tot het minimaal noodzakelijke `p.offset` + `p.limit` .

* **p.excerpt**

  Indien ingesteld op &quot; `true`&quot;, neemt u het volledige tekstfragment op in het resultaat.

* **p.hits**

  (alleen voor de JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met de volgende standaardresultaten (uitbreidbaar via de service ResultHitWriter):

   * **eenvoudig**:

     Minimale items zoals `path` , `title` , `lastmodified` en `excerpt` (indien ingesteld).

   * **volledig**:

     JSON-rendering van het knooppunt splitsen, met `jcr:path` die het pad van de hit aangeeft: standaard worden alleen de directe eigenschappen van het knooppunt weergegeven, inclusief een diepere structuur met `p.nodedepth=N` , die 0 staat voor de gehele, oneindige substructuur; voeg `p.acls=true` toe om de JCR-machtigingen van de huidige sessie voor het opgegeven resultaatitem op te nemen (toewijzingen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove` = &rbrace;).

   * **selectief**:

     Alleen de eigenschappen die zijn opgegeven in `p.properties` , dat een spatie is die is gescheiden (gebruik &quot;+&quot; in URL&#39;s) in de lijst met relatieve paden; als het relatieve pad een diepte heeft > 1, worden deze vertegenwoordigd als onderliggende objecten; de speciale eigenschap jcr:path bevat het pad van de hit

### opgeslagen query {#savedquery}

Omvat alle predikaten van een persisted vraag van de vraagbouwer in de huidige vraag als subgroup predikaat.

Hiermee wordt geen extra query uitgevoerd, maar wordt de huidige query uitgebreid.

Query&#39;s kunnen met programmacode worden voortgezet met `QueryBuilder#storeQuery()` . De indeling kan een eigenschap van een tekenreeks met meerdere regels zijn of een knooppunt `nt:file` dat de query als een tekstbestand in de Java™-eigenschappenindeling bevat.

Biedt geen ondersteuning voor facetextractie voor de voorspelling van de opgeslagen query.

#### Eigenschappen {#properties-19}

* **opgeslagen vraag**

  Pad naar de opgeslagen query (eigenschap String of knooppunt `nt:file` ).

### gelijkaardig {#similar}

Gelijksoortige zoekopdracht met JCR XPath `rep:similar()`.

Filteren wordt niet ondersteund. Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-20}

* **gelijkaardig**
Absoluut pad naar het knooppunt waarvoor vergelijkbare knooppunten moeten worden gevonden.

* **lokaal**
Een relatief pad naar een afstammend knooppunt of `.` voor het huidige knooppunt (optioneel, standaard is &quot; `.`&quot;).

### tag {#tag}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags door titelpaden voor tags op te geven.

Ondersteunt facetextractie. Verschaft emmers voor elke unieke tag, waarbij het huidige pad voor de tagtitel wordt gebruikt.

#### Eigenschappen {#properties-21}

* **markering**

  Titelpad van tag om bijvoorbeeld te zoeken naar &quot;Eigenschappen van element: oriëntatie / liggend&quot;.

* **N_value**

  Gebruik `1_value`, `2_value` , ... om te controleren op meerdere tags (standaard gecombineerd met `OR` , met `AND` if en=true) (sinds 5.6).

* **bezit**

  Eigenschap (of relatief pad naar eigenschap) die moet worden bekeken (standaard &quot; `cq:tags`&quot;)

### gelabeld {#tagid}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags, door tag-id&#39;s op te geven.

Ondersteunt facetextractie. Verschaft emmers voor elke unieke tag met behulp van de huidige tag-id.

#### Eigenschappen {#properties-22}

* **tagid**

  Label id zodat u bijvoorbeeld naar &quot; `properties:orientation/landscape`&quot; kunt zoeken.

* **N_value**

  Gebruik `1_value`, `2_value` , ... om te controleren op meerdere tags (standaard gecombineerd met `OR` , met `AND` if en=true) (sinds 5.6).

* **bezit**

  Eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;).

### tagzoeken {#tagsearch}

Zoekt naar inhoud gelabeld met een of meer tags door trefwoorden op te geven. Hiermee wordt eerst gezocht naar tags die deze trefwoorden in hun titels bevatten, en vervolgens wordt het resultaat beperkt tot alleen items die met deze trefwoorden zijn getagd.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#Properties-1}

* **tagsearch**

  Trefwoord dat moet worden gezocht in tagtitels.

* **bezit**

  Eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard `cq:tags`).

* **lang**

  Als u alleen in een bepaalde gelokaliseerde tagtitel wilt zoeken (bijvoorbeeld `de` ).

* **allen**

  (bool) Zoek volledige labeltekst, dat wil zeggen alle titels, beschrijving enzovoort. Heeft voorrang op &quot;l `ang`&quot;.

### type {#type}

Hiermee beperkt u de resultaten tot een specifiek JCR-knooppunttype, zowel het primaire knooppunttype als het mixintype. Dit vindt ook subtypes van dat knooptype. In de zoekindexen van de opslagplaats moeten de knooppunttypen worden opgenomen voor een efficiënte uitvoering.

Ondersteunt facetextractie. Verstrekt emmers voor elk uniek type in de resultaten.

#### Eigenschappen {#Properties-2}

* **type**

  Node type of mixin naam aan onderzoek naar, bijvoorbeeld, `cq:Page`.
