---
title: Voorlopige naslaggids voor Query Builder
description: Volledige predikate verwijzing voor de Bouwer van de Vraag API.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
exl-id: 54b942f9-5dd9-4826-9a0a-028f2d7b8e41
source-git-commit: 970e0a97d531d4cbae76119960972e54ef65dda0
workflow-type: tm+mt
source-wordcount: '2313'
ht-degree: 0%

---

# Voorlopige naslaggids voor Query Builder{#query-builder-predicate-reference}

>[!CAUTION]
>
>De informatie op deze pagina is niet volledig.
>
>Zie de lijst onder **Beschikbare voorspellingen** op de Foutopsporingsconsole van de Bouwer van de Vraag; bijvoorbeeld bij:
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
* [gelabeld](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagzoeken](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### boolproperty {#boolproperty}

Komt overeen met de JCR BOOLEAN-eigenschappen. Accepteert alleen de waarden &quot; `true`&quot; en &quot; `false`&quot;. Als &quot; `false`&quot;, komt overeen als de eigenschap de waarde &quot; `false`&quot; of als het überhaupt niet bestaat. Dit kan handig zijn om te controleren op Booleaanse markeringen die alleen zijn ingesteld wanneer deze zijn ingeschakeld.

De overgeërfde &quot; `operation`&quot; parameter heeft geen betekenis.

Ondersteunt facetextractie. Verstrekt emappen voor elk `true` of `false` waarde, maar alleen voor bestaande eigenschappen.

#### Eigenschappen {#properties}

* **boolproperty**
Relatief pad naar eigenschap, bijvoorbeeld `myFeatureEnabled` of `jcr:content/myFeatureEnabled`.

* **value**
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

* **bewerking**

  &quot; `equals`&quot; voor exacte overeenkomst, &quot; `!=`&quot; voor de vergelijking van ongelijkheid &quot; `greater`&quot; voor eigenschap1 groter dan eigenschap2, &quot; `>=`&quot; voor property1 groter dan of gelijk aan property2. De standaardwaarde is &quot; `equals`&quot;.

### daterange {#daterange}

Hiermee worden de JCR-DATE-eigenschappen vergeleken met een datum-/tijdinterval. Hierbij wordt de ISO8601-indeling gebruikt voor datums en tijden ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke vertegenwoordiging toe, zoals `YYYY-MM-DD`. U kunt de tijdstempel ook opgeven als het aantal milliseconden dat is verstreken sinds 1970 in de UTC-tijdzone, de UNIX®-tijdnotatie.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Ondersteunt facetextractie. Verstrekt emmers &quot;vandaag&quot;, &quot;deze week&quot;, &quot;deze maand&quot;, &quot;laatste drie maanden&quot;, &quot;dit jaar&quot;, &quot;vorig jaar&quot; en &quot;vroeger dan vorig jaar&quot;.

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **eigenschap**

  Relatief pad naar `DATE` eigenschap, bijvoorbeeld `jcr:lastModified`.

* **lowerBound**

  Lagere datum gebonden aan check eigenschap for, bijvoorbeeld `2014-10-01`.

* **lowerOperation**

  &quot; `>`&quot; (nieuwer) of &quot; `>=`&quot; (bij of hoger), van toepassing op `lowerBound`. De standaardwaarde is &quot; `>`&quot;.

* **upperBound**

  Bovenaan gebonden om eigenschap te controleren voor, bijvoorbeeld, `2014-10-01T12:15:00`.

* **upperOperation**

  &quot; `<`&quot; (ouder) of &quot; `<=`&quot; (bij of ouder), van toepassing op `upperBound`. De standaardwaarde is &quot; `<`&quot;.

* **timeZone**

  Id van tijdzone die moet worden gebruikt wanneer deze niet wordt gegeven als een ISO-8601-datumtekenreeks. De standaardwaarde is de standaardtijdzone van het systeem.

### exclusief paden {#excludepaths}

Hiermee sluit u knooppunten uit van het resultaat wanneer het pad ervan overeenkomt met een reguliere expressie.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-4}

* **exclusief paden**

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

Hiermee kunnen geneste voorwaarden worden gemaakt. Groepen kunnen geneste groepen bevatten. Alles in een query builder-query bevindt zich impliciet in een hoofdgroep, die kan `p.or` en `p.not` ook parameters.

Voorbeeld voor het afstemmen van een van de twee eigenschappen op een waarde:

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

Dit is conceptueel `fulltext AND ( (path AND type) OR (path AND type) )`. Zulke OF verbindingen hebben goede indexen voor prestaties nodig.

#### Eigenschappen {#properties-6}

* **p.or**

  Indien ingesteld op &quot; `true`&quot;, slechts één predikaat in de groep moet aanpassen. Dit is standaard &quot; `false`&quot;, wat betekent dat alles moet overeenkomen

* **p.not**

  Indien ingesteld op &quot; `true`&quot;, wordt de groep genegeerd (standaard ingesteld op &quot; `false`&quot;).

* **&lt;predicate>**

  Hiermee voegt u geneste voorvertoningen toe.

* **N_&lt;predicate>**

  Hiermee voegt u meerdere geneste voorvertoningen tegelijk toe, zoals `1_property, 2_property, ...`.

### hasPermission {#haspermission}

Beperkt het resultaat tot punten waar de huidige zitting gespecificeerde heeft [JCR-bevoegdheden.](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **hasPermission**

  JCR-bevoegdheden die door komma&#39;s worden gescheiden en die ALLES voor de huidige gebruikerssessie moet hebben. Bijvoorbeeld: `jcr:write`, `jcr:modifyAccessControl`.

### taal {#language}

Hiermee zoekt u CQ-pagina&#39;s in een specifieke taal. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken, dat vaak de taal of landinstelling in een site-structuur op hoofdniveau bevat.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt.

Ondersteunt facetextractie. Verstrekt emmers voor elke unieke taalcode.

#### Eigenschappen {#properties-8}

* **taal**

  ISO-taalcode, bijvoorbeeld &quot;`de`&quot;

### hoofdmiddel {#mainasset}

Controleert of een knooppunt een DAM-hoofdelement is en geen subelement. Dit is eigenlijk elk knooppunt dat zich niet binnen een &#39;subassets&#39;-knooppunt bevindt. Dit controleert niet op `dam:Asset` knooppunttype. Als u deze voorspelling wilt gebruiken, stelt u &quot; `mainasset=true`&quot; of &quot; `mainasset=false`&quot; , zijn er geen eigenschappen meer.

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt.

Steunt facetextractie en verstrekt twee emmers voor hoofd en subassets.

#### Eigenschappen {#properties-9}

* **hoofdmiddel**

  Boolean, &quot; `true`&quot; voor de belangrijkste activa, &quot; `false`&quot; voor subassets.

### lidOf {#memberof}

Hiermee worden items gevonden die lid zijn van een specifieke [slingerbronverzameling](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/org/apache/sling/resource/collection/ResourceCollection.html).

Dit is een voorspelling die alleen kan worden gefilterd en er kan geen zoekindex worden gebruikt. Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-10}

* **lidOf**

  Pad van Sling-bronverzameling.

### nodenaam {#nodename}

Komt overeen met namen van JCR-knooppunten.

Ondersteunt facetextractie. Verstrekt emmers voor elke unieke knoopnaam (filename).

#### Eigenschappen {#properties-11}

* **nodenaam**

  Naampatroon knooppunt dat jokertekens toestaat: `*` = een of geen teken, `?` = een teken, `[abc]` = alleen tekens tussen haakjes.

### notexpired {#notexpired}

Komt overeen met items door te controleren of een JCR DATE-eigenschap groter of gelijk is aan de huidige servertijd. Dit kan worden gebruikt om een &quot; `expiresAt`&quot; Vergelijkbare datum, eigenschap en beperking tot alleen de eigenschappen die nog niet zijn verlopen ( `notexpired=true`) of die reeds zijn verlopen ( `notexpired=false`).

Filteren wordt niet ondersteund.

Ondersteunt facetextractie op dezelfde manier als de daterange predikaat.

#### Eigenschappen {#properties-12}

* **notexpired**

  Boolean, &quot; `true`&quot; nog niet verstreken (datum in de toekomst of gelijk aan), &quot; `false`&quot; voor verlopen (datum in het verleden) (vereist).

* **eigenschap**

  Relatief pad naar de `DATE` te controleren eigenschap (vereist).

### ordonneren {#orderby}

Hiermee kunt u de resultaten sorteren. Als het opdracht geven door veelvoudige eigenschappen wordt vereist, moet dit predikaat veelvoudige tijden toevoegen gebruikend het aantalprefix, zoals `1_orderby=first`, `2_oderby=second`.

#### Eigenschappen {#properties-13}

* **ordonneren**

  De JCR-eigenschapsnaam die wordt aangegeven door een regelafstand @, bijvoorbeeld `@jcr:lastModified` of `@jcr:content/jcr:title`of een andere voorspelling in de query, bijvoorbeeld `2_property`, waarop wordt gesorteerd.

* **sorteren**

  Sorteerrichting: &quot; `desc`&quot; voor aflopend of &quot; `asc`&quot; voor oplopend (standaard).

* **case**

  Indien ingesteld op `ignore`, maakt het sorteren ongevoelig, wat betekent &quot;a&quot;komt vóór &quot;B&quot;; als leeg of weggelaten, is het sorteren hoofdlettergevoelig, wat betekent &quot;B&quot; komt vóór &quot;a&quot;

### pad {#path}

Hiermee zoekt u in een bepaald pad.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-14}

* **pad**

  Padpatroon. Afhankelijk van het exacte aantal komt de volledige subboomstructuur overeen (zoals bij toevoegen) `//*` in xpath, maar merk op dat dit niet het basispad bevat) (exact=false, standaard), of alleen een exacte padovereenkomst, die jokertekens kan bevatten ( `*`); als zelf is ingesteld, wordt de volledige substructuur, inclusief het basisknooppunt, doorzocht.

* **exact**

  Indien `exact` is waar/aan, moet de nauwkeurige weg aanpassen maar het kan eenvoudige vervangingen bevatten ( `*`), die gelijk zijn aan namen, maar niet &quot; `/`&quot;; als de waarde false is (standaard), worden alle afstammingen opgenomen (optioneel).

* **plat**

  Hiermee doorzoekt u alleen de directe onderliggende items (zoals u &quot; `/*`&quot; in xpath) (alleen gebruikt als &quot; `exact`&#39; is niet waar, optioneel).

* **zelfzucht**

  Doorzoekt de substructuur maar neemt het basisknooppunt op dat als pad wordt opgegeven (geen jokertekens).

### eigenschap {#property}

Komt overeen met de JCR-eigenschappen en hun waarden.

Ondersteunt facetextractie. Verstrekt emmers voor elke unieke bezitswaarde in de resultaten.

#### Eigenschappen {#properties-15}

* **eigenschap**

  Relatief pad naar eigenschap, bijvoorbeeld `jcr:title`.

* **value**

  Waarde waarop de eigenschap moet worden gecontroleerd; volgt het eigenschapstype JCR op tekenreeksconversies.

* **N_value**

  Gebruiken `1_value`, `2_value`, ... om te controleren op meerdere waarden (gecombineerd met `OR` standaard, met `AND` if and=true) (sinds 5.3).

* **en**

  Ingesteld op true voor het combineren van meerdere waarden ( `N_value`) met EN (sinds 5.3).

* **bewerking**

  &quot;`equals`&quot; voor exacte overeenkomst (standaardwaarde), &quot; `unequals`&quot; voor de vergelijking van ongelijkheid &quot; `like`&quot; voor het gebruik van de `jcr:like` xpath, functie (optioneel), &quot; `not`&quot; voor geen overeenkomst (bijvoorbeeld &quot;`not(@prop)`&quot; in xpath, value param is genegeerd) of &quot; `exists`&quot; voor existentiecontrole (waarde kan waar zijn - eigenschap moet bestaan, standaardwaarde - of vals - zelfde als &quot; `not`&quot;).

* **diepte**

  Aantal jokertekenniveaus waaronder de eigenschap/het relatieve pad kan bestaan (bijvoorbeeld `property=size depth=2` check node/size, node/&amp;ast;/size en node/&amp;ast;/&amp;ast;/size).

### rangeproperty {#rangeproperty}

Hiermee wordt een JCR-eigenschap vergeleken met een interval. Dit geldt voor eigenschappen met lineaire typen, zoals `LONG`, `DOUBLE`, en `DECIMAL`. Voor `DATE`, zie daterange predikaat dat geoptimaliseerde datumaandultaatinput heeft.

U kunt een ondergrens en een bovengrens of slechts één van hen bepalen. De bewerking (bijvoorbeeld &quot;kleiner dan&quot; of &quot;kleiner of gelijk aan&quot;) kan ook afzonderlijk worden opgegeven voor de onderste en bovenste binding.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-16}

* **eigenschap**

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

Overeenkomsten `JCR DATE` eigenschappen op basis van een datum-/tijdinterval waarbij tijdverschuivingen ten opzichte van de huidige servertijd worden gebruikt. U kunt `lowerBound` en `upperBound` met een millisecondenwaarde of de bugzilla-syntaxis `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar). Voorvoegsel met &quot; `-`&quot; om een negatieve verschuiving vóór de huidige tijd aan te geven. Als u alleen `lowerBound` of `upperBound`De andere is standaard ingesteld op 0, wat de huidige tijd betekent.

Bijvoorbeeld:

* `upperBound=1h` (en `lowerBound`) in de komende uren alles selecteren
* `lowerBound=-1d` (en `upperBound`) in de afgelopen 24 uur alles selecteren
* `lowerBound=-6M` en `upperBound=-3M` zou om het even wat 6 maanden tot 3 maanden oud selecteren
* `lowerBound=-1500` en `upperBound=5500` selecteert u in de toekomst alles tussen 1500 milliseconden in het verleden en 5500 milliseconden
* `lowerBound=1d` en `upperBound=2d` zou overmorgen alles selecteren

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

* **p.radenTotaal**

  Aanbevolen: vermijd het berekenen van het volledige resultaattotaal, wat kostbaar kan zijn; ofwel een getal dat het maximale totaal aangeeft dat moet worden geteld tot (bijvoorbeeld 1000, een getal dat gebruikers voldoende feedback geeft over de ruwe grootte en exacte getallen voor kleinere resultaten) of &quot; `true`&quot; om slechts tot het noodzakelijke minimum te tellen `p.offset` + `p.limit`.

* **p.excerpt**

  Indien ingesteld op &quot; `true`&quot;, neemt u het volledige tekstfragment op in het resultaat.

* **p.hits**

  (alleen voor de JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met de volgende standaardresultaten (uitbreidbaar via de service ResultHitWriter):

   * **eenvoudig**:

     Minimale objecten zoals `path`, `title`, `lastmodified`, `excerpt` (indien ingesteld).

   * **volledig**:

     Sling JSON rendering van het knooppunt, met `jcr:path` die op de weg wijzen van de slag: door gebrek maakt enkel een lijst van de directe eigenschappen van de knoop, omvat een diepere boom met `p.nodedepth=N`, waarbij 0 staat voor de gehele, oneindige substructuur; toevoegen `p.acls=true` om de JCR-machtigingen van de huidige sessie op te nemen voor het opgegeven resultaatitem (toewijzingen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).

   * **selectief**:

     Alleen eigenschappen opgegeven in `p.properties`, dat een spatie gescheiden is (gebruik &quot;+&quot; in URL&#39;s), lijst met relatieve paden; als het relatieve pad een diepte > 1 heeft, worden deze weergegeven als onderliggende objecten; de speciale eigenschap jcr:path bevat het pad van de hit

### opgeslagen query {#savedquery}

Omvat alle predikaten van een persisted vraag van de vraagbouwer in de huidige vraag als subgroup predikaat.

Hiermee wordt geen extra query uitgevoerd, maar wordt de huidige query uitgebreid.

De vragen kunnen programmatically worden voortgeduurd gebruikend `QueryBuilder#storeQuery()`. De indeling kan een tekenreekseigenschap met meerdere regels of een `nt:file` knooppunt dat de query als een tekstbestand in Java™-eigenschappenindeling bevat.

Biedt geen ondersteuning voor facetextractie voor de voorspelling van de opgeslagen query.

#### Eigenschappen {#properties-19}

* **opgeslagen query**

  Pad naar de opgeslagen query (eigenschap String of `nt:file` knooppunt).

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

* **tag**

  Titelpad van tag om bijvoorbeeld te zoeken naar &quot;Eigenschappen van element: oriëntatie / liggend&quot;.

* **N_value**

  Gebruiken `1_value`, `2_value`, ... om te controleren op meerdere tags (gecombineerd met `OR` standaard, met `AND` if and=true) (sinds 5.6).

* **eigenschap**

  Eigenschap (of relatief pad naar eigenschap) die moet worden bekeken (standaard &quot; `cq:tags`&quot;)

### gelabeld {#tagid}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags, door tag-id&#39;s op te geven.

Ondersteunt facetextractie. Verschaft emmers voor elke unieke tag met behulp van de huidige tag-id.

#### Eigenschappen {#properties-22}

* **gelabeld**

  Label-id zodat u bijvoorbeeld naar &quot; `properties:orientation/landscape`&quot;.

* **N_value**

  Gebruiken `1_value`, `2_value`, ... om te controleren op meerdere tags (gecombineerd met `OR` standaard, met `AND` if and=true) (sinds 5.6).

* **eigenschap**

  Eigenschap (of relatief pad naar eigenschap) die moet worden bekeken (standaard &quot; `cq:tags`&quot;).

### tagzoeken {#tagsearch}

Zoekt naar inhoud gelabeld met een of meer tags door trefwoorden op te geven. Hiermee wordt eerst gezocht naar tags die deze trefwoorden in hun titels bevatten, en vervolgens wordt het resultaat beperkt tot alleen items die met deze trefwoorden zijn getagd.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#Properties-1}

* **tagzoeken**

  Trefwoord dat moet worden gezocht in tagtitels.

* **eigenschap**

  Eigenschap (of relatief pad naar eigenschap) die moet worden bekeken (standaard) `cq:tags`).

* **lang**

  Alleen een bepaalde gelokaliseerde tagtitel zoeken (bijvoorbeeld `de`).

* **alles**

  (bool) Zoek volledige labeltekst, dat wil zeggen alle titels, beschrijving enzovoort. Heeft voorrang op &quot;l `ang`&quot;.

### type {#type}

Hiermee beperkt u de resultaten tot een specifiek JCR-knooppunttype, zowel het primaire knooppunttype als het mixintype. Dit vindt ook subtypes van dat knooptype. In de zoekindexen van de opslagplaats moeten de knooppunttypen worden opgenomen voor een efficiënte uitvoering.

Ondersteunt facetextractie. Verstrekt emmers voor elk uniek type in de resultaten.

#### Eigenschappen {#Properties-2}

* **type**

  Node-type- of mixingnaam die u wilt zoeken, bijvoorbeeld `cq:Page`.
