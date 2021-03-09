---
title: Voorlopige naslaggids voor Query Builder
seo-title: Voorlopige naslaggids voor Query Builder
description: Volledige predikate verwijzing voor de Bouwer van de Vraag API.
seo-description: Volledige predikate verwijzing voor de Bouwer van de Vraag API.
uuid: af0e269e-7d52-4032-b22e-801c7b5dccfa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
discoiquuid: 94a05894-743a-4ace-a292-bfee90ba9068
translation-type: tm+mt
source-git-commit: 7a96ff5cdd187291efe108d1171782bcbecfaeb0
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 2%

---


# Predicate Reference{#query-builder-predicate-reference} van de Bouwer van de vraag

## Algemeen {#general}

* [basis](#root)
* [groep](#group)
* [ordonneren](#orderby)

## Voorspeld {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [exclusief paden](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [fulltext](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [language](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [hoofdmiddel](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [lidOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodenaam](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [path](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [eigenschap](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [opgeslagen query](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [gelijkaardig](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [tag](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagzoeken](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### oolproperty {#boolproperty}

Komt overeen met de JCR BOOLEAN-eigenschappen. Accepteert alleen de waarden &quot; `true`&quot; en &quot; `false`&quot;. In het geval van &quot; `false`&quot;, zal het aanpassen als het bezit de waarde &quot; `false`&quot;heeft of als het helemaal niet bestaat. Dit kan handig zijn om te controleren op Booleaanse markeringen die alleen zijn ingesteld wanneer deze zijn ingeschakeld.

De overgeërfde parameter &quot; `operation`&quot; heeft geen betekenis.

Ondersteunt facetextractie. Wordt geleverd met emmers voor elke `true`- of `false`-waarde, maar alleen voor bestaande eigenschappen.

#### Eigenschappen {#properties}

* **relatief pad**
naar eigenschap, bijvoorbeeld 
`myFeatureEnabled` or `jcr:content/myFeatureEnabled`

* **value to check property for, &quot;**
 
`true`&quot; or &quot; `false`&quot;

### contentfragment {#contentfragment}

Hiermee beperkt u het resultaat tot inhoudsfragmenten.

Filteren wordt niet ondersteund.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-1}

* ****
contentFragmentIt kan met elke waarde worden gebruikt om te controleren op inhoudsfragmenten.

### dateComparison {#datecomparison}

Vergelijkt twee JCR DATE-eigenschappen met elkaar. Kan testen of ze gelijk, ongelijk, groter dan of groter dan of gelijk zijn.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

#### Eigenschappen {#properties-2}

* **property1**

   path to first date, eigenschap

* **property2**

   path to second date, eigenschap

* **operation**

   &quot;`equals`&quot;voor nauwkeurige gelijke, &quot;`!=`&quot;voor ongelijkheidsvergelijking, &quot;`greater`&quot;voor eigenschap1 groter dan eigenschap2, &quot;`>=`&quot;voor eigenschap1 groter dan of gelijk aan property2. De standaardwaarde is &quot;`equals`&quot;.

### daterange {#daterange}

Hiermee worden de JCR-DATE-eigenschappen vergeleken met een datum-/tijdinterval. Dit gebruikt ISO8601
notatie voor datums en tijden ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke vertegenwoordiging, zoals `YYYY-MM-DD` toe. U kunt de tijdstempel ook opgeven als het aantal milliseconden dat is verstreken sinds 1970 in de UTC-tijdzone, de unieke tijdnotatie.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Ondersteunt facetextractie. Zal emmers &quot;vandaag&quot;, &quot;deze week&quot;, &quot;deze maand&quot;, &quot;laatste 3 maanden&quot;, &quot;dit jaar&quot;, &quot;vorig jaar&quot; en &quot;eerder dan vorig jaar&quot; leveren.

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **eigenschap**

   relatief pad naar een eigenschap `DATE`, bijvoorbeeld `jcr:lastModified`

* **lowerBound**

   lagere datum gebonden aan controlebezit voor, bijvoorbeeld `2014-10-01`

* **lowerOperation**

   &quot; `>`&quot; (nieuwer) of &quot; `>=`&quot; (bij of hoger), is van toepassing op `lowerBound`. De standaardwaarde is &quot; `>`&quot;.

* **upperBound**

   bovenaan gebonden om eigenschap te controleren voor, bijvoorbeeld `2014-10-01T12:15:00`

* **upperOperation**

   &quot; `<`&quot; (ouder) of &quot; `<=`&quot; (op of ouder), is van toepassing op `upperBound`. De standaardwaarde is &quot; `<`&quot;.

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

Hiermee kunt u geneste voorwaarden maken. Groepen kunnen geneste groepen bevatten. Alles in een querybuilder-query bevindt zich impliciet in een hoofdgroep, die ook `p.or`- en `p.not`-parameters kan hebben.

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

Hiermee wordt gezocht naar de term &quot;**Management**&quot; op pagina&#39;s in `/content/geometrixx/en` of in elementen in `/content/dam/geometrixx`.

Dit is conceptueel `fulltext AND ( (path AND type) OR (path AND type) )`. Houd er rekening mee dat dergelijke OR-verbindingen goede indexen nodig hebben voor de prestaties.

#### Eigenschappen {#properties-6}

* **p.or**

   indien ingesteld op &quot; `true`&quot;, mag slechts één voorspelling in de groep overeenkomen. Dit is standaard &quot; `false`&quot;, wat betekent dat alles moet overeenkomen

* **p.not**

   indien ingesteld op &quot; `true`&quot;, wordt de groep genegeerd (standaard &quot; `false`&quot;)

* **&lt;predicate>**

   voegt geneste voorspellingen toe

* **N_&lt;predicate>**

   voegt meerdere geneste voorspellingen tegelijk toe, zoals `1_property, 2_property, ...`

### hasPermission {#haspermission}

Hiermee beperkt u het resultaat tot items waarvoor de huidige sessie de opgegeven [JCR-bevoegdheden heeft.](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **hasPermission**

   de door komma&#39;s gescheiden voorrechten van het JCR die de huidige gebruikerszitting ALLE voor de knoop in kwestie moet hebben; bijvoorbeeld `jcr:write`, `jcr:modifyAccessControl`

### language {#language}

Hiermee zoekt u CQ-pagina&#39;s in een specifieke taal. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken, dat vaak de taal of landinstelling in een sitestructuur op hoofdniveau bevat.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Ondersteunt facetextractie. Zal emmers voor elke unieke taalcode verstrekken.

#### Eigenschappen {#properties-8}

* **taal**

   ISO-taalcode, bijvoorbeeld &quot; `de`&quot;

### mainasset {#mainasset}

Controleert of een knooppunt een DAM-hoofdmiddel is en geen subelement. Dit is eigenlijk elk knooppunt dat zich niet binnen een &#39;subassets&#39;-knooppunt bevindt. Merk op dat dit niet het `dam:Asset` knooptype controleert. Als u deze voorspelling wilt gebruiken, stelt u eenvoudig &quot; `mainasset=true`&quot; of &quot; `mainasset=false`&quot; in, maar er zijn geen eigenschappen meer.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Ondersteunt facetextractie. Twee emmers voor hoofd- en subactiva.

#### Eigenschappen {#properties-9}

* **hoofdmiddel**

   boolean, &quot; `true`&quot; voor hoofdactiva, &quot; `false`&quot; voor subactiva

### memberOf {#memberof}

Vindt punten die lid van een specifieke [sling middelinzameling](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) zijn.

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

Komt overeen met items door te controleren of een JCR DATE-eigenschap groter of gelijk is aan de huidige servertijd. Dit kan worden gebruikt om &quot; `expiresAt`&quot;als datumbezit te controleren en zich tot slechts degenen te beperken die nog niet ( `notexpired=true`) zijn verlopen of die reeds ( `notexpired=false`) zijn verlopen.

Filteren wordt niet ondersteund.

Ondersteunt facetextractie op dezelfde manier als de daterange predikaat.

#### Eigenschappen {#properties-12}

* **notexpired**

   boolean, &quot; `true`&quot; for not expired yet (date in the future or equal), &quot; `false`&quot; for expired (date in the previous) (required)

* **eigenschap**

   relatief pad naar de eigenschap `DATE` die moet worden gecontroleerd (vereist)

### orderby {#orderby}

Hiermee kunt u het resultaat sorteren. Als het opdracht geven door veelvoudige eigenschappen wordt vereist, moet dit predikaat veelvoudige tijden worden toegevoegd gebruikend het aantalprefix, zoals `1_orderby=first`, `2_oderby=second`.

#### Eigenschappen {#properties-13}

* **ordonneren**

   De JCR-eigenschapnaam die wordt aangeduid door een regelafstand @, bijvoorbeeld `@jcr:lastModified` of `@jcr:content/jcr:title`, of een andere voorspelling in de query, bijvoorbeeld `2_property`, waarop moet worden gesorteerd

* **sorteren**

   sorteerrichting: &quot; `desc`&quot; voor aflopend of &quot; `asc`&quot; voor oplopend (standaard)

* **case**

   als deze waarde wordt ingesteld op &quot; `ignore`&quot;, worden sorteerhoofdletters en kleine letters ongevoelig, wat betekent dat &quot;a&quot; voor &quot;B&quot; komt; indien leeg of weggelaten, wordt onderscheid gemaakt tussen hoofdletters en kleine letters, wat betekent dat &quot;B&quot; voor &quot;a&quot; komt

### path {#path}

Hiermee zoekt u in een bepaald pad.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-14}

* **pad**

   padpatroon; afhankelijk van exact, of zal de volledige subboom (als het toevoegen `//*` in xpath, maar merk op dat dit niet het basisweg omvat) (exact=false, gebrek) of slechts een nauwkeurige weggelijken, die vervangingskaarten ( `*`) kunnen omvatten; als self is ingesteld, wordt de gehele substructuur, inclusief het basisknooppunt, doorzocht

* **exact**

   als `exact` waar/is, moet de nauwkeurige weg aanpassen, maar het kan eenvoudige vervangingen ( `*`) bevatten, die namen aanpassen, maar niet &quot; `/`&quot;; als deze onwaar is (standaard), worden alle afstammingen opgenomen (optioneel)

* **plat**

   zoekt alleen de directe onderliggende items (zoals &quot; `/*`&quot; in xpath toevoegen) (wordt alleen gebruikt als &#39; `exact`&#39; niet true is, optioneel).

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

   gebruik `1_value`, `2_value`, ... om te controleren op meerdere waarden (standaard gecombineerd met `OR`, met `AND` if en=true) (sinds 5.3)

* **and**

   ingesteld op true voor het combineren van meerdere waarden ( `N_value`) met AND (sinds 5.3)

* **bewerking**

   &quot;`equals`&quot; voor exacte overeenkomst (standaard), &quot;`unequals`&quot; voor ongelijkheidsvergelijking, &quot;`like`&quot; voor het gebruik van de `jcr:like` xpath-functie (optioneel), &quot; `not`&quot; voor geen overeenkomst (bijvoorbeeld &quot;`not(@prop)`&quot; in xpath, value param zal worden genegeerd) of &quot;`exists`&quot;voor existentiecontrole (de waarde kan waar zijn - het bezit moet bestaan, het gebrek - of vals - het zelfde als &quot;`not`&quot;)

* **diepte**

   aantal jokertekenniveaus onder welke de eigenschap/het relatieve pad kan bestaan (`property=size depth=2` controleert bijvoorbeeld knooppunt/grootte, knooppunt/&amp;ast;/size en knooppunt/&amp;ast;/&amp;ast;/&amp;ast;/size)

### rangeproperty {#rangeproperty}

Hiermee wordt een JCR-eigenschap vergeleken met een interval. Dit is van toepassing op eigenschappen met lineaire typen, zoals `LONG`, `DOUBLE` en `DECIMAL`. Voor `DATE` gelieve te zien daterange predikaat dat geoptimaliseerde gegeven van het datumformaat heeft.

U kunt een ondergrens en een bovengrens of slechts één van hen bepalen. De bewerking (bijv. &quot;kleiner dan&quot; of &quot;kleiner of gelijk aan&quot;) kan ook worden opgegeven voor de individuele ondergrens en bovengrens.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-16}

* **eigenschap**

   relatief pad naar eigenschap

* **lowerBound**

   ondergrens om eigenschap te controleren voor

* **lowerOperation**

   &quot; `>`&quot; (standaardwaarde) of &quot; `>=`&quot; is van toepassing op `lowerValue`

* **upperBound**

   bovenaan gebonden om eigenschap te controleren voor

* **upperOperation**

   &quot; `<`&quot; (standaardwaarde) of &quot; `<=`&quot; is van toepassing op `lowerValue`

* **decimal**

   &quot; `true`&quot; als de gecontroleerde eigenschap van het type Decimaal is

### relativedaterange {#relativedaterange}

Hiermee worden `JCR DATE`-eigenschappen vergeleken met een datum-/tijdinterval waarbij tijdverschuivingen ten opzichte van de huidige servertijd worden gebruikt. U kunt `lowerBound` en `upperBound` specificeren gebruikend of een millisecondenwaarde of de bugzilla syntaxis `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar). Voorvoegsel met &quot; `-`&quot; om een negatieve verschuiving vóór de huidige tijd aan te geven. Als u alleen `lowerBound` of `upperBound` opgeeft, wordt de andere waarde standaard ingesteld op 0, wat de huidige tijd betekent.

Bijvoorbeeld:

* `upperBound=1h` (en geen  `lowerBound`) zou iets selecteren in het volgende uur
* `lowerBound=-1d` (en geen  `upperBound`) selecteert iets in de afgelopen 24 uur
* `lowerBound=-6M` en  `upperBound=-3M` kiest u tussen 6 maanden en 3 maanden oud
* `lowerBound=-1500` en  `upperBound=5500` selecteert u in de toekomst alles tussen 1500 milliseconden in het verleden en 5500 milliseconden
* `lowerBound=1d` en  `upperBound=2d` zou overmorgen alles selecteren

Er wordt geen rekening gehouden met schrikkeljaren en alle maanden zijn 30 dagen.

Filteren wordt niet ondersteund.

Ondersteunt facetextractie op dezelfde manier als de daterange predikaat.

#### Eigenschappen {#properties-17}

* **upperBound**

   hogere datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie

* **lowerBound**

   lagere datumgebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie

### root {#root}

Hoofdvoorspelbare groep. Steunt alle eigenschappen van een groep en staat toe om globale vraagparameters te plaatsen.

De naam &quot;wortel&quot;wordt nooit gebruikt in een vraag, het is impliciet.

#### Eigenschappen {#properties-18}

* **p.offset**

   getal dat het begin van de resultatenpagina aangeeft, d.w.z. het aantal items dat moet worden overgeslagen

* **p.limit**

   getal dat het paginaformaat aangeeft

* **p.radenTotaal**

   aanbevolen: niet het volledige resultaattotaal berekenen dat kostbaar kan zijn; ofwel een getal dat het maximale totaal aangeeft dat moet worden geteld tot (bijvoorbeeld 1000, een getal dat gebruikers voldoende feedback geeft op de ruwe grootte en exacte getallen voor kleinere resultaten) of &quot; `true`&quot; om alleen te tellen tot het noodzakelijke minimum `p.offset` + `p.limit`

* **p.excerpt**

   Indien ingesteld op &quot; `true`&quot;, moet u het volledige tekstfragment in het resultaat opnemen

* **p.hits**

   (alleen voor de JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met de volgende standaardresultaten (uitbreidbaar via de service ResultHitWriter):

   * **eenvoudig**:

      minimale items zoals `path`, `title`, `lastmodified`, `excerpt` (indien ingesteld)

   * **volledig**:

      sling JSON rendering van het knooppunt, met `jcr:path` die het pad van de hit aangeeft: door gebrek enkel maakt een lijst van de directe eigenschappen van de knoop, omvat een diepere boom met `p.nodedepth=N`, met 0 betekenend de volledige, oneindige subtree; Voeg `p.acls=true` toe om de JCR-machtigingen van de huidige sessie op te nemen voor het opgegeven resultatenitem (toewijzingen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`)

   * **selectief**:

      alleen de eigenschappen die zijn opgegeven in `p.properties`. Dit is een spatie gescheiden (gebruik &quot;+&quot; in URL&#39;s) lijst met relatieve paden; als het relatieve pad een diepte > 1 heeft, worden deze weergegeven als onderliggende objecten; de speciale eigenschap jcr:path bevat het pad van de hit

### opgeslagen query {#savedquery}

Omvat alle predikaten van een persisted querybuilder vraag in de huidige vraag als subgroup predikaat.

Hiermee wordt geen extra query uitgevoerd, maar wordt de huidige query uitgebreid.

De vragen kunnen programmatically worden voortgeduurd gebruikend `QueryBuilder#storeQuery()`. De indeling kan ofwel een eigenschap van een tekenreeks met meerdere regels zijn, ofwel een `nt:file`-knooppunt dat de query als een tekstbestand in de Java-eigenschappenindeling bevat.

Biedt geen ondersteuning voor facetextractie voor de voorspelling van de opgeslagen query.

#### Eigenschappen {#properties-19}

* **opgeslagen query**

   pad naar de opgeslagen query (eigenschap String of knooppunt `nt:file`)

### vergelijkbaar {#similar}

Zoekopdracht op basis van overeenkomsten met gebruik van `rep:similar()` van JCR XPath.

Filteren wordt niet ondersteund. Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#properties-20}

* **gelijkaardig absolute weg aan de knoop waarvoor om gelijkaardige knopen te vinden**


* **relatieve**
locala-pad naar een afstammend knooppunt of 
`.` voor het huidige knooppunt (optioneel, standaard is &quot;  `.`&quot;)

### tag {#tag}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags door de titelpaden van tags op te geven.

Ondersteunt facetextractie. Hiermee geeft u emmers voor elke unieke tag op met behulp van het huidige pad voor de tagtitel.

#### Eigenschappen {#properties-21}

* **tag**

   titelpad van tag naar, bijvoorbeeld &quot;Eigenschappen van element: Oriëntatie / Liggend&quot;

* **N_value**

   gebruik `1_value`, `2_value`, ... om te controleren op meerdere tags (standaard gecombineerd met `OR`, met `AND` if en=true) (sinds 5.6)

* **eigenschap**

   eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;)

### tagid {#tagid}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags, door tag-id&#39;s op te geven.

Ondersteunt facetextractie. Hiermee geeft u emmers voor elke unieke tag op met de huidige tag-id.

#### Eigenschappen {#properties-22}

* **tagid**

   -tag-id die moet worden gezocht, bijvoorbeeld &quot; `properties:orientation/landscape`&quot;

* **N_value**

   gebruik `1_value`, `2_value`, ... om te controleren op meerdere tagids (standaard gecombineerd met `OR`, met `AND` if en=true) (sinds 5.6)

* **eigenschap**

   eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;)

### tagsearch {#tagsearch}

Zoekt naar inhoud gelabeld met een of meer tags door trefwoorden op te geven. Hiermee zoekt u eerst naar tags die deze trefwoorden bevatten in de titels en beperkt u het resultaat vervolgens tot alleen items die met deze trefwoorden zijn getagd.

Biedt geen ondersteuning voor facetextractie.

#### Eigenschappen {#Properties-1}

* **tagzoeken**

   trefwoord waarnaar moet worden gezocht in titels van tags

* **eigenschap**

   eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;)

* **lang**

   alleen in een bepaalde gelokaliseerde tagtitel zoeken (bijvoorbeeld &quot; `de`&quot;)

* **all**

   (bool) doorzoek volledige labeltekst, dus alle titels, beschrijving enz. (heeft voorrang op &quot;l `ang`&quot;)

### tekst {#type}

Hiermee beperkt u de resultaten tot een specifiek JCR-knooppunttype, zowel het primaire knooppunttype als het mixintype. Dit zal ook subtypes van dat knooptype vinden. Merk op dat de gegevensopslagplaats onderzoeksindexen de knooppunttypes voor efficiënte uitvoering moeten behandelen.

Ondersteunt facetextractie. Zal emmers voor elk uniek type in de resultaten verstrekken.

#### Eigenschappen {#Properties-2}

* **type**

   knooppunttype of mixin naam aan onderzoek naar, bijvoorbeeld `cq:Page`