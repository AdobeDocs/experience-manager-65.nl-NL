---
title: Scriptondersteuning voor HTML5-formulieren
description: JavaScript, FormCalc-eigenschappen en andere methoden die worden ondersteund in HTML5 Forms.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
feature: HTML5 Forms
exl-id: bcb5afc5-2190-4269-aba2-63842db9df3f
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3916'
ht-degree: 0%

---

# Scriptondersteuning voor HTML5-formulieren {#scripting-support-for-html-forms}

JavaScript, FormCalc-eigenschappen en methoden die in HTML5-formulieren worden ondersteund, worden hieronder weergegeven:

## $event {#event}

<table>
 <tbody>
  <tr>
   <th>Eigenschap </th>
   <th>Beschrijving<br /> </th>
   <th>Uitzondering</th>
  </tr>
  <tr>
   <td><code>prevText</code></td>
   <td>Hiermee geeft u de inhoud van het veld op voordat deze wordt gewijzigd als reactie op de acties van een gebruiker. Deze waarde kan worden teruggeroepen, vergelijkbaar met een functie voor ongedaan maken.</td>
   <td><p>Werkt niet voor vervolgkeuzelijsten en keuzelijsten. <code>PrevText </code>werkt niet correct in de volgende gevallen:</p>
    <ul>
     <li>Bij het typen van bepaalde speciale tekentoetsen (bijvoorbeeld $ of , of &amp; of @ en meer) in numerieke velden op de iPad, en </li>
     <li>Voor het veld Datum (wanneer de datum door de kalender wordt ingevoerd).<br /> </li>
    </ul> <p>Het instellen van waarde via script wordt niet ondersteund.</p> </td>
  </tr>
  <tr>
   <td><code>target</code></td>
   <td>Hiermee wordt het object opgegeven waarop de gebeurtenis reageert.</td>
   <td>Het instellen van waarde via script wordt niet ondersteund.<br /> </td>
  </tr>
  <tr>
   <td><code>newtext</code></td>
   <td>Hiermee geeft u de inhoud van het veld op nadat deze is gewijzigd als reactie op handelingen van de gebruiker.</td>
   <td><p>De <code>newText</code> De eigenschap werkt niet goed voor de volgende gevallen:</p>
    <ul>
     <li>Bij het selecteren en vervangen van tekst</li>
     <li>Bij het verwijderen, kopiëren en plakken van tekst.</li>
     <li>Bij het typen van bepaalde speciale tekentoetsen (bijvoorbeeld $ of , of &amp; of @ en meer) in numerieke velden<br /> </li>
     <li>Bij gebruik van de combinatie shift+alfanumeriek. </li>
     <li>Bij het gebruik van datum-/tijdvelden.</li>
    </ul>
    <div>
      Het instellen van waarde via script wordt niet ondersteund.
    </div> </td>
  </tr>
  <tr>
   <td>wijzigen</td>
   <td>Hiermee wordt de waarde opgegeven die een gebruiker in een veld typt of plakt direct nadat de handeling is uitgevoerd. </td>
   <td><p>De eigenschap change werkt niet goed voor de volgende gevallen:</p>
    <ul>
     <li>Bij het selecteren en vervangen van tekst</li>
     <li>Bij het verwijderen, kopiëren en plakken van tekst.</li>
     <li>Bij het typen van bepaalde speciale tekentoetsen (bijvoorbeeld $ of , of &amp; of @ en meer) in numerieke velden<br /> </li>
     <li>Bij gebruik van de combinatie shift+alfanumeriek. </li>
     <li>Bij het gebruik van datum-/tijdvelden.</li>
    </ul> <p>Het instellen van waarde via script wordt niet ondersteund.</p> </td>
  </tr>
  <tr>
   <td>keydown</td>
   <td>Hiermee wordt bepaald of een gebruiker op een pijltoets drukt om een selectie te maken. Deze eigenschap is alleen beschikbaar voor keuzelijsten en vervolgkeuzelijsten.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>modifier</td>
   <td>Hiermee wordt bepaald of de modifier-toets (bijvoorbeeld Ctrl in Microsoft® Windows®) wordt ingedrukt wanneer een bepaalde gebeurtenis wordt uitgevoerd.</td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

### $host {#host}

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
   <th>Uitzondering</th>
  </tr>
  <tr>
   <td><code>apptype</code></td>
   <td>Retourneert het toepassingstype van de host. Alleen beschikbaar voor clienttoepassingen.</td>
   <td>Retourneert <code>HTML 5</code>.</td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>Retourneert de naam van de huidige toepassing.</td>
   <td>Retourneert de naam van de browser en de versie. In Chrome bijvoorbeeld wordt de geretourneerde waarde geretourneerd <code>Chrome &lt;version&gt;.</code></td>
  </tr>
  <tr>
   <td><code>numPages</code></td>
   <td>Retourneert het aantal pagina's in het document.</td>
   <td>Pagineringsbeleid voor HTML5-formulieren is niet hetzelfde als pagineringsbeleid voor PDF forms. De numPages-API kan dus in beide gevallen een andere waarde retourneren.</td>
  </tr>
  <tr>
   <td><code>platform</code></td>
   <td>Retourneert een tekenreeks die het platform vertegenwoordigt van de computer waarop het script wordt uitgevoerd.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>title</code></td>
   <td>Hiermee geeft u de titel van het document op. Deze optie is alleen beschikbaar voor clienttoepassingen.</td>
   <td>Er wordt een titel van een HTML-document in het formulier geretourneerd, in plaats van de titel van de metagegevens van het formulier, alsof er PDF forms zijn.</td>
  </tr>
  <tr>
   <td><code>version</code></td>
   <td>Retourneert een tekenreeks die het versienummer van de huidige toepassing vertegenwoordigt.</td>
   <td>Hiermee wordt de versie van het formulier geretourneerd.</td>
  </tr>
  <tr>
   <td><code>calculationsEnabled</code></td>
   <td>Hiermee wordt opgegeven of berekeningsscripts worden uitgevoerd.<br /> </td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>validationsEnabled</code></td>
   <td>Hiermee wordt opgegeven of validatiescripts worden uitgevoerd.<br /> </td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>pageUp</code></td>
   <td>Goes to the previous page.</td>
   <td>Voor HTML5-formulieren wordt niet hetzelfde pagineringsbeleid gevolgd als voor PDF-formulieren. De vorige pagina van een HTML5-formulier is dus anders dan de vorige pagina van een PDF-formulier.</td>
  </tr>
  <tr>
   <td><code>pageDown</code></td>
   <td>Hiermee gaat u naar de volgende pagina van een formulier. Gebruik de methode pageDown tijdens de runtime.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>setFocus</code></td>
   <td>Stelt de toetsenbordfocus in op het opgegeven veld. Het veld wordt opgegeven als een object of door de SOM-expressie van het veld. Deze optie is alleen beschikbaar voor clienttoepassingen.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>resetdata</code></td>
   <td>Hiermee herstelt u de standaardwaarden van de velden in een document.</td>
   <td>Hiermee wist u alle gegevens in een formulier met samengevoegde gegevens en herstelt u deze niet tot de standaardwaarden.</td>
  </tr>
  <tr>
   <td><code>messageBox</code></td>
   <td>Hiermee wordt een dialoogvenster op het scherm weergegeven. Deze optie is alleen beschikbaar voor clienttoepassingen</td>
   <td>Berichtvak van type Ja/Nee wordt geconverteerd naar OK/Annuleren. Berichtvenster met drie knoppen wordt niet ondersteund.</td>
  </tr>
  <tr>
   <td>currentPage</td>
   <td><p>Hiermee wordt de huidige actieve pagina van een document bij uitvoering ingesteld.</p> <p>De paginanummers beginnen bij 0, dus de eerste pagina van een document retourneert de waarde 0.</p> <p>De eigenschap currentPage is beschikbaar wanneer layout:ready op een client wordt uitgevoerd. De eigenschap is echter niet beschikbaar wanneer layout:ready wordt uitgevoerd op de server, omdat de eigenschap pas wordt uitgevoerd wanneer de formulierindeling wordt uitgevoerd.</p> </td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

### field {#field}

<table>
 <tbody>
  <tr>
   <th><strong><span>Eigenschap</span></strong></th>
   <th><strong><span>Beschrijving<br /> </span></strong></th>
   <th><strong><span>Uitzondering</span></strong></th>
  </tr>
  <tr>
   <td><code>presence</code></td>
   <td>Controls the participation of the associated object in different phase of processing. Als het object een container is, neemt de inhoud van de container alle beperkingen over die dit besturingselement toepast.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>access</code></td>
   <td>Controls user access to the contents.</td>
   <td>Werkt niet voor de uitsluitingsgroep. Bovendien bieden HTML5-formulieren dezelfde behandeling voor niet-interactieve en beschermde objecten.<br /> </td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>An identifier that is used to identify this element in script expressions.</td>
   <td>HTML5-formulieren staan het instellen van de eigenschap name voor objecten niet toe. Het is alleen-lezen eigenschap voor HTML5-formulieren.</td>
  </tr>
  <tr>
   <td><code>value</code></td>
   <td>A content element that encloses a single unit of data content.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>rawValue</code></td>
   <td>Specifies the unformatted value for this field.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>formattedValue</code></td>
   <td>Specifies the formatted value for this field.</td>
   <td>Instelling <code>formattedValue</code> via script wordt niet ondersteund.</td>
  </tr>
  <tr>
   <td><code>editValue</code></td>
   <td>Specifies the edit value for this field.</td>
   <td>Instelling <code>editValue </code>via script wordt niet ondersteund.</td>
  </tr>
  <tr>
   <td><code>formatMessage</code></td>
   <td>Specifies the format validation message string for this field.</td>
   <td>Instelling <code>formatMessage </code>via script wordt niet ondersteund.</td>
  </tr>
  <tr>
   <td><code>fillcolor</code></td>
   <td>Specifies the background color value for this field. U moet de eigenschap border.fill.presence instellen op visible separately.</td>
   <td>De standaardkleur van het veld wordt niet correct geretourneerd.</td>
  </tr>
  <tr>
   <td><code>border</code></td>
   <td>Met het randobject wordt de rand rondom een object beschreven.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>ui</code></td>
   <td>Het ui-object bevat de gebruikersinterfacebeschrijving van een formulierobject.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>mandatory</code></td>
   <td>Specifies the nullTest value for the field.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>borderColor</code></td>
   <td>Specifies the border color value for this field. U moet de eigenschap border.edge.presence instellen op visible separately.</td>
   <td>De standaardrandkleur van het veld wordt niet correct geretourneerd.</td>
  </tr>
  <tr>
   <td><code>length</code></td>
   <td>Het aantal items in de lijst.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>addItem</code></td>
   <td>Hiermee worden nieuwe items aan het huidige veld toegevoegd.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>clearItem</code></td>
   <td>Hiermee worden alle items uit het veld verwijderd.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>boundItem</code></td>
   <td>Hiermee wordt de gebonden waarde van een specifiek weergaveitem van een vervolgkeuzelijst of keuzelijst opgehaald.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>execCalculate</code></td>
   <td>Executes the calculate script of the field.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>execValidate</code></td>
   <td>Executes the validate script of the field.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>execEvent</code></td>
   <td>Hiermee wordt het gebeurtenisscript van het object uitgevoerd.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>getItemState</code></td>
   <td>Hiermee wordt de selectiestatus van het opgegeven item geretourneerd</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>setItemState</code></td>
   <td>Hiermee wordt de selectiestatus van het opgegeven item ingesteld.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>getDisplayItem</code></td>
   <td>Hiermee wordt de itemweergavetekst voor de opgegeven itemindex opgehaald.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>getSaveItem</code></td>
   <td>Hiermee wordt de gegevenswaarde voor de opgegeven itemindex opgehaald.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>deleteItem</code></td>
   <td>Hiermee wordt het item bij de opgegeven index verwijderd.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><code>setItems</code></td>
   <td>Hiermee worden de opgegeven items in het huidige veld ingesteld. Bestaande items worden vervangen.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>h</td>
   <td>A measurement of the height for the layout.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>w</td>
   <td>A measurement specifying the width for the layout.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Hiermee wordt de x-coördinaat opgegeven van het ankerpunt van de container ten opzichte van de linkerbovenhoek van de bovenliggende container bij een gepositioneerde indeling.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Hiermee wordt de y-coördinaat opgegeven van het ankerpunt van een container ten opzichte van de linkerbovenhoek van de bovenliggende container bij een gepositioneerde indeling.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>bijschrift</td>
   <td>Met het bijschriftobject wordt een beschrijvend label beschreven dat aan een formulierontwerpobject is gekoppeld.<br /> </td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Met het object validate wordt de validatie van door de gebruiker opgegeven gegevens op een formulier beheerd. Het object validate kan meerdere malen worden geactiveerd tijdens de levensduur van een formulier.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>parentSubform</td>
   <td>Hiermee wordt het bovenliggende subformulier (pagina) van dit veld opgegeven.</td>
   <td>Retourneert altijd het bovenliggende subformulier in plaats van het eerste bovenliggende subformulier zonder bereik te retourneren.<br /> </td>
  </tr>
  <tr>
   <td>selectedIndex</td>
   <td>De index van het eerste geselecteerde item.</td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

## Formulier {#form}

| **Eigenschap** | **Beschrijving** | **Uitzondering** |
|---|---|---|
| formNodes | Retourneert een lijst met alle formuliermodelobjecten die zijn gebonden aan een opgegeven gegevensobject. |  |

## InstanceManager {#instancemanager}

| Eigenschap | Beschrijving |
|---|---|
| `name` | An identifier that is used to identify this element in script expressions. |
| `occur` | Beschrijft de beperkingen over het aantal toegestane instanties voor zijn insluitende container. |
| `min` | Geeft het minimale aantal instanties op dat kan worden geïnstantieerd. |
| `max` | Specifies the maximum number of instances that can be instantiated. |
| `count` | Specifies the current number of instances instantiated. |
| `setInstances` | Voegt de opgegeven subformulieren of subformuliersets toe of verwijdert deze uit dit knooppunt. |
| `addInstance` | Hiermee wordt een nieuw exemplaar van een subformulier of subformulierset toegevoegd aan dit knooppunt. |
| `removeInstance` | Hiermee verwijdert u een subformulier of subformulierset van dit knooppunt. |
| `moveInstance` | Hiermee wordt een onderliggend object van een formuliermodelobject verplaatst naar een andere opgegeven locatie in het formuliermodel. De overeenkomstige gegevens van het gegevensmodel voor het object worden ook verplaatst binnen het gegevensmodel. |
| `insertInstance` | Hiermee wordt een nieuw exemplaar van een subformulier of subformulierset toegevoegd aan dit knooppunt. |

## list {#list}

| Eigenschap | Beschrijving |
|---|---|
| `length` | Het aantal elementen in de lijst. |
| `item` | Een op nul gebaseerde index in de verzameling. |
| `append` | Hiermee wordt een knooppunt toegevoegd aan het einde van de lijst met knooppunten. |
| `remove` | Hiermee wordt een knooppunt uit de lijst met knooppunten verwijderd. |
| `insert` | Voegt een knoop vóór een specifieke knoop in de knooplijst in. |

## node {#node}

| Eigenschap | Beschrijving | Uitzondering |
|---|---|---|
| createNode | Hiermee wordt een nieuw knooppunt gemaakt op basis van een geldige klassenaam. | Geen |
| `isContainer` | Geeft aan of dit object een containerobject is. | Geen |
| `isNull` | Geeft aan of de huidige gegevenswaarde een null-waarde is. | Geen |
| `resolveNode` | Evalueert de opgegeven SOM-expressie, te beginnen met het huidige object in het XML-formulierobjectmodel, en retourneert de waarde van het object dat is opgegeven in de SOM-expressie. | Geen |
| `resolveNodes` | Evalueert de opgegeven SOM-expressie, te beginnen met het huidige object in het XML-formulierobjectmodel, en retourneert de waarde van het object dat is opgegeven in de SOM-expressie. | Geen |
| oneOfChild | Hiermee wordt een nieuw knooppunt gemaakt op basis van een geldige klassenaam. | Geen |
| getElement | Retourneert een opgegeven onderliggend object. | Geen |
| getAttribute | Hiermee wordt een opgegeven eigenschapswaarde opgehaald. | Geen |
| setAttribute | Hiermee wordt de waarde van een opgegeven eigenschap ingesteld. | Geen |

## model {#model}

| Eigenschap | Beschrijving | Uitzondering |
|---|---|---|
| NA | NA | NA |

## Subformulier {#subform}

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
   <th>Uitzondering</th>
  </tr>
  <tr>
   <td>instanceIndex</td>
   <td>Specifies the index of the object, relative to the other instantiated instances.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>execEvent</td>
   <td>Hiermee wordt het gebeurtenisscript van het object uitgevoerd.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>getInvalidObjects</td>
   <td>Retourneert een lijst met knooppunten in het subformulier (inclusief) die de validatietest niet hebben doorstaan.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>border</td>
   <td>Met het randobject wordt de rand rondom een object beschreven.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Specifies the border color value for this field. U moet de eigenschap border.edge.presence instellen op visible separately.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>h</td>
   <td>A measurement of the height for the layout.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>w</td>
   <td>A measurement specifying the width for the layout.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Hiermee wordt de x-coördinaat opgegeven van het ankerpunt van de container ten opzichte van de linkerbovenhoek van de bovenliggende container bij een gepositioneerde indeling.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Hiermee wordt de y-coördinaat opgegeven van het ankerpunt van een container ten opzichte van de linkerbovenhoek van de bovenliggende container bij een gepositioneerde indeling.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Met het object validate wordt de validatie van door de gebruiker opgegeven gegevens op een formulier beheerd. Het object validate kan meerdere malen worden geactiveerd tijdens de levensduur van een formulier.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>name</td>
   <td>An identifier that is used to identify this element in script expressions.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>aanwezigheid</td>
   <td>Hiermee geeft u de zichtbaarheid van een object op.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>toegang</td>
   <td>Controls user access to the contents of a container object, such as a subform.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>execValidate</td>
   <td>Hiermee wordt de index van een subformulier of subformulierset berekend op basis van de locatie ten opzichte van andere instanties van hetzelfde formulierobject.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>instanceManager</td>
   <td>Het instanceManager-object beheert het maken, verwijderen en verplaatsen van exemplaren van formuliermodelobjecten.<br /> </td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

### indienen {#submit}

| Eigenschap | Beschrijving |
|---|---|
| target | De URL waarnaar de gegevens worden verzonden. Het weglaten van dit attribuut impliceert de XFA verwerkingstoepassing URI gebruikend een product-specifieke techniek, zoals het toegang tot van product-specifieke informatie in het config voorwerp verkrijgt. |

## boom {#tree}

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
   <th>Uitzondering</th>
  </tr>
  <tr>
   <td>knooppunten</td>
   <td>Retourneert een lijst met alle onderliggende objecten van het huidige object.</td>
   <td>
    <ul>
     <li>Niet ondersteund voor xfa.nodes, desc</li>
     <li>Het aantal knooppunten dat voor PDF en HTML wordt gerapporteerd, is verschillend. </li>
    </ul> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Specifies the name of this node.</td>
   <td>Het instellen van de naam met scripts is niet toegestaan in HTML.</td>
  </tr>
  <tr>
   <td>parent</td>
   <td>Haalt het bovenliggende element voor dit knooppunt op.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>index</td>
   <td>Keert de positie van deze knoop in zijn inzameling van gelijkgenoemde, in-werkingsgebied, als-kind relatieknooppunten terug.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>somExpression</td>
   <td>Gets the SOM expression for this node.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>resolveNode</td>
   <td>Evalueert de opgegeven SOM-expressie, te beginnen met het huidige object in het XML-formulierobjectmodel, en retourneert de waarde van het object dat is opgegeven in de SOM-expressie.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>resolveNodes</td>
   <td>Evalueert de opgegeven SOM-expressie, te beginnen met het huidige object in het XML-formulierobjectmodel, en retourneert de waarde van het object dat is opgegeven in de SOM-expressie.</td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

## subformulierset {#subformset}

| Eigenschap | Beschrijving | Uitzondering |
|---|---|---|
| instanceManager | Het instanceManager-object beheert het maken, verwijderen en verplaatsen van exemplaren van formuliermodelobjecten. | Geen |

## content {#content}

| **Eigenschap** | **Beschrijving** | **Uitzondering** |
|---|---|---|
| isNull | Geeft aan of de huidige gegevenswaarde de null-waarde is. |  |

## dataValue {#datavalue}

| **Eigenschap** | **Beschrijving** | **Uitzondering** |
|---|---|---|
| isNull | Geeft aan of de huidige gegevenswaarde de null-waarde is. |  |

## edge {#edge}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap </strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>kleur</td>
   <td>Met de kleureigenschap wordt een unieke kleur voor het patroonobject beschreven.</td>
   <td>
    <ul>
     <li>De standaardwaarde kan niet worden opgehaald. </li>
     <li>De wijzigingen worden weergegeven in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## vullen {#fill}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>kleur</td>
   <td>De kleureigenschappen definiëren een unieke vulkleur.</td>
   <td>
    <ul>
     <li>De standaardwaarde kan niet worden opgehaald. </li>
     <li>De wijzigingen worden weergegeven in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## lineair {#linear}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>kleur</td>
   <td>Met de eigenschap color wordt een unieke kleur beschreven voor een lineaire verloopvulling op een formulier.</td>
   <td>
    <ul>
     <li>De standaardwaarde kan niet worden opgehaald. </li>
     <li>De wijzigingen worden weergegeven in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## line {#line}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Met het randobject wordt een boog, lijn of één zijde van een rand of rechthoek beschreven.<br /> </td>
   <td>Kenmerken zoals kleur, uiteinde en meer worden niet ondersteund.<br /> </td>
  </tr>
 </tbody>
</table>

## patroon {#pattern}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>kleur</td>
   <td>Met de kleureigenschap wordt een unieke kleur voor het patroonobject beschreven. </td>
   <td>
    <ul>
     <li>De standaardwaarde kan niet worden opgehaald. </li>
     <li>De wijzigingen worden weergegeven in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## radiaal {#radial}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>kleur</td>
   <td>Met de eigenschap color wordt een unieke kleur voor het radiale object beschreven</td>
   <td>
    <ul>
     <li>De standaardwaarde kan niet worden opgehaald. </li>
     <li>De wijzigingen worden weergegeven in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## stipple {#stipple}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>kleur</td>
   <td>Met de eigenschap color wordt een unieke kleur voor het stipple-object beschreven.</td>
   <td>
    <ul>
     <li>De standaardwaarde kan niet worden opgehaald. </li>
     <li>De wijzigingen worden weerspiegeld in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## draw {#draw}

<table>
 <tbody>
  <tr>
   <td>Eigenschap</td>
   <td>Beschrijving</td>
   <td>Uitzondering</td>
  </tr>
  <tr>
   <td>ui</td>
   <td>Het ui-object bevat de gebruikersinterfacebeschrijving van een formulierobject.<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td>bijschrift</td>
   <td>Met het bijschriftobject wordt een beschrijvend label beschreven dat aan een formulierontwerpobject is gekoppeld.</td>
   <td> </td>
  </tr>
  <tr>
   <td>aanwezigheid</td>
   <td>Hiermee geeft u de zichtbaarheid van een object op.</td>
   <td> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Hiermee wordt een id opgegeven die kan worden gebruikt om dit object of deze gebeurtenis op te geven in scriptexpressies.</td>
   <td>Het instellen van de waarde tijdens de runtime wordt niet ondersteund</td>
  </tr>
  <tr>
   <td>value</td>
   <td>Het waardeobject omsluit één gegevensinhoudseenheid.<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

## hoek {#corner}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>kleur</td>
   <td>Met de kleureigenschap wordt een unieke kleur voor het hoekobject beschreven.</td>
   <td>
    <ul>
     <li>De standaardwaarde kan niet worden opgehaald. </li>
     <li>De wijzigingen worden weerspiegeld in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## checkButton {#checkbutton}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Het object border beschrijft de rand rondom het object checkButton. </td>
   <td>De wijzigingen worden weerspiegeld in het model en zijn beschikbaar voor scripts, maar worden niet gesynchroniseerd met HTML-elementen. De wijzigingen worden derhalve niet in de BU weergegeven.<br /> </td>
  </tr>
 </tbody>
</table>

## choiceList {#choicelist}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<br /> </strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Het randobject beschrijft de rand rondom het object choiceList.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## dateTimeEdit {#datetimeedit}

| **Eigenschap** | **Beschrijving** | **Uitzondering** |
|---|---|---|
| border | Het randobject beschrijft de rand rond het dateTimeEdit-object. |  |

## Afbeelding {#image}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>contentType</td>
   <td>Geeft het type inhoud aan in het document waarnaar wordt verwezen, uitgedrukt als een MIME-type.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>name<br /> </td>
   <td>An identifier that is used to identify this element in script expressions.</td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

## imageEdit {#imageedit}

| **Eigenschap** | **Beschrijving** | **Uitzondering** |
|---|---|---|
| border | Met het randobject wordt de rand rond het object imageEdit beschreven. |  |

## numericEdit {#numericedit}

| **Eigenschap** | **Beschrijving** | **Uitzondering** |
|---|---|---|
| border | Met het randobject wordt de rand rondom een object beschreven. | none |

## object {#object}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>className</td>
   <td>Bepaalt de naam van de klasse van dit object.<br /> </td>
   <td>none</td>
  </tr>
 </tbody>
</table>

## rechthoek {#rectangle}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Met het randobject wordt een boog, lijn of één zijde van een rand of rechthoek beschreven.<br /> </td>
   <td>Kenmerken zoals kleur, uiteinde en meer worden niet ondersteund.</td>
  </tr>
 </tbody>
</table>

## textEdit {#textedit}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Met het randobject wordt de rand rondom een object beschreven.<br /> </td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

## exclGroup {#exclgroup}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>layout</td>
   <td>Geeft aan welke indelingsstrategie door dit object moet worden gebruikt.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>border</td>
   <td>Hiermee geeft u de rand rondom dit veld op.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>verplicht</td>
   <td>Specifies the nullTest value for the field.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Specifies the border color value for this field.A border must be defined before you can change the color by scripting.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>borderWidth</td>
   <td>Specifies the border width for this field.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>h</td>
   <td>A measurement of the height for the layout.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>transient</td>
   <td>Hiermee wordt opgegeven of de verwerkende toepassing de waarde van de uitsluitingsgroep moet opslaan als onderdeel van een formulierverzending of opslagbewerking.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>w</td>
   <td>A measurement specifying the width for the layout.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Hiermee wordt de x-coördinaat opgegeven van het ankerpunt van de container ten opzichte van de linkerbovenhoek van de bovenliggende container bij een gepositioneerde indeling.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Hiermee wordt de y-coördinaat opgegeven van het ankerpunt van een container ten opzichte van de linkerbovenhoek van de bovenliggende container bij een gepositioneerde indeling.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>bijschrift</td>
   <td>Met het bijschriftobject wordt een beschrijvend label beschreven dat aan een formulierontwerpobject is gekoppeld.<br /> </td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Met het object validate wordt de validatie van door de gebruiker opgegeven gegevens op een formulier beheerd. Het object validate kan meerdere malen worden geactiveerd tijdens de levensduur van een formulier.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>dataNode</td>
   <td>Hiermee wordt het gegevensknooppunt opgehaald waaraan een formulierknooppunt wordt gebonden na het samenvoegen.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>aanwezigheid</td>
   <td>Hiermee geeft u de zichtbaarheid van een object op.</td>
   <td> </td>
  </tr>
  <tr>
   <td>toegang</td>
   <td>Controls user access to the contents of a container object, such as a subform.</td>
   <td>Voor afzonderlijke items in de uitzondering wordt altijd open geretourneerd. </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Hiermee wordt een id opgegeven die kan worden gebruikt om dit object of deze gebeurtenis op te geven in scriptexpressies.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>leden</td>
   <td>Geef de leden van de uitsluitingsgroep op. </td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>selectedMember</td>
   <td>Retourneert het geselecteerde lid van een uitsluitingsgroep.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>execCalculate</td>
   <td>Hiermee worden alle scripts in de gebeurtenis calculate van het opgegeven object en alle onderliggende objecten uitgevoerd.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>berekenen</td>
   <td>Het object calculate bestuurt de berekening van de waarde van een veld.<br /> </td>
   <td>Geen</td>
  </tr>
 </tbody>
</table>

## boog {#arc}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<strong></strong></strong></td>
   <td><strong>Beschrijving<strong></strong></strong></td>
   <td><strong>Uitzondering<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Met het randobject wordt een boog, lijn of één zijde van een rand of rechthoek beschreven.<br /> </td>
   <td>Kenmerken zoals kleur, uiteinde en meer worden niet ondersteund. </td>
  </tr>
 </tbody>
</table>

## border {#border}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<strong></strong></strong></td>
   <td><strong>Beschrijving<strong></strong></strong></td>
   <td><strong>Uitzondering<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Met het randobject wordt een boog, lijn of één zijde van een rand of rechthoek beschreven.<br /> </td>
   <td>Kenmerken zoals kleur, uiteinde en meer worden niet ondersteund. </td>
  </tr>
 </tbody>
</table>

## $layout {#layout}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Uitzondering</strong></td>
  </tr>
  <tr>
   <td>h</td>
   <td>Hiermee wordt de hoogte van een formulierontwerpobject bepaald.<br /> </td>
   <td>
    <ul>
     <li>De eigenschap Hoogte (h) wordt niet ondersteund voor paginagebied en inhoudsgebied. </li>
     <li>Parameter 'Verschuiving vanaf eerste inhoudsgebied waarop het XFA-formulierobject plaatsvindt' wordt niet ondersteund.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>w</td>
   <td>Hiermee wordt de breedte van een formulierontwerpobject bepaald.</td>
   <td>
    <ul>
     <li>De eigenschap width (w) wordt niet ondersteund voor paginagebied en inhoudsgebied. </li>
     <li>Parameter 'Verschuiving vanaf eerste inhoudsgebied waarop het XFA-formulierobject plaatsvindt' wordt niet ondersteund.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>x</td>
   <td>Hiermee wordt de x-coördinaat bepaald van een formulierontwerpobject ten opzichte van het bovenliggende object.</td>
   <td>
    <ul>
     <li>x-coördinaat (x)-eigenschap wordt niet ondersteund voor paginagebied en inhoudsgebied. </li>
     <li>Parameter 'Verschuiving vanaf eerste inhoudsgebied waarop het XFA-formulierobject plaatsvindt' wordt niet ondersteund.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>y</td>
   <td>Hiermee wordt de y-coördinaat bepaald van een formulierontwerpobject ten opzichte van het bovenliggende object.</td>
   <td>
    <ul>
     <li>y-coördinaat (y)-eigenschap wordt niet ondersteund voor paginagebied en inhoudsgebied. </li>
     <li>Parameter 'Verschuiving vanaf eerste inhoudsgebied waarop het XFA-formulierobject plaatsvindt' wordt niet ondersteund.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>pagecount</td>
   <td>Hiermee bepaalt u het aantal pagina's van het huidige formulier.</td>
   <td>
    <ul>
     <li>layout.pageCount() methode retourneert verschillende waarden voor PDF- en HTML-formulieren.</li>
     <li>Bij het verlagen van het aantal pagina's door een object te verbergen, retourneert de methode abspagecount een onjuiste waarde.<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>pagecontent</td>
   <td>Hiermee worden typen formulierontwerpobjecten opgehaald van een opgegeven pagina van een formulier.</td>
   <td>Geen</td>
  </tr>
  <tr>
   <td>absPageCount</td>
   <td>Hiermee bepaalt u het aantal pagina's van het huidige formulier.</td>
   <td>
    <ul>
     <li>layout.pageCount() methode retourneert verschillende waarden voor PDF- en HTML-formulieren.</li>
     <li>Bij het verlagen van het aantal pagina's door een object te verbergen, retourneert de methode abspagecount een onjuiste waarde.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## items {#items}

| **Eigenschap** | **Beschrijving** | **Uitzondering** |
|---|---|---|
| aanwezigheid | Hiermee geeft u de zichtbaarheid van een object op. | Geen |

## FormCalc {#formcalc}

FormCalc is een XFA-specifieke taal voor het maken van centrische logica en berekeningen op basis van e-formulieren. FormCalcalculation biedt een krachtige verzameling functies voor het maken van constructies.

### Ondersteunde functies van FormCalc {#formcalc-supported-functions}

### Ondersteuning voor FormCalc-expressies {#formcalc-expression-support}

<table>
 <tbody>
  <tr>
   <td><strong>Categorie </strong></td>
   <td><strong>Beschrijving </strong></td>
   <td><strong>Monster </strong></td>
  </tr>
  <tr>
   <td>Eenvoudige expressie</td>
   <td>Toevoegen, verwijderen, vermenigvuldigen, verdelen en ronde haakjes</td>
   <td>(a+b)*3</td>
  </tr>
  <tr>
   <td>Variabele-declaratie</td>
   <td>Een variabele definiëren</td>
   <td>var a<br /> var a=3<br /> a=3</td>
  </tr>
  <tr>
   <td>Logische expressie</td>
   <td>
    <ul>
     <li>Logica (en/of)</li>
     <li>Vergelijking (groter/kleiner/gelijk)</li>
    </ul> </td>
   <td>A of 1<br /> 1 &lt;&gt; 2<br /> A NE B<br /> A of 1<br /> 1 &lt;&gt; 2<br /> A NE B</td>
  </tr>
  <tr>
   <td>If-expressie</td>
   <td><br type="_moz" /> </td>
   <td>if (a&gt;b) dan 2 endif</td>
  </tr>
  <tr>
   <td>while</td>
   <td><br type="_moz" /> </td>
   <td>while (i lt 5) do i = i + 1 endwhile</td>
  </tr>
  <tr>
   <td>for</td>
   <td><br type="_moz" /> </td>
   <td>voor i = 100 tot 1 <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>voor elke</td>
   <td><br type="_moz" /> </td>
   <td>voor elke i in (1, 2, 3) <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>functiedeclaratie</td>
   <td>Een aangepaste functie definiëren in FormCalc</td>
   <td>func foo(n) do var f = n endfunc</td>
  </tr>
 </tbody>
</table>

### Acrobat API-ondersteuning {#acrobat-api-support}

1. **Rekenkundige functies**

   1. Abs()
   1. Avg()
   1. Ceil()
   1. Count()
   1. Floor()
   1. Max()
   1. Min()
   1. Mod()
   1. Round()
   1. Sum()

1. **Wetenschappelijke functies**

   1. Acos()
   1. Asin()
   1. Atan()
   1. Atan2()
   1. Cos()
   1. Sin()
   1. tan()
   1. Exp()
   1. Log()
   1. Pow()
   1. sqrt()
   1. Deg2Rad()
   1. Rad2Deg()
   1. Pi()

1. **Financiële functies**

   1. apr()
   1. Cterm()
   1. fv()
   1. ipmt()
   1. Npv()
   1. Pmt()
   1. pmt()
   1. pv()
   1. Rate()
   1. Term()

1. **Logische functies**

   1. Choose()
   1. if()
   1. Oneof()
   1. Within()

1. **Reeksfuncties**

   1. At()
   1. Concat()
   1. Left()
   1. Len()
   1. Lower()
   1. Ltrim()
   1. Replace()
   1. Right()
   1. Rtrim()
   1. Space()
   1. Stuff()
   1. Substr()
   1. Upper()
   1. WordNum()

1. **Datum en tijd**

   1. Date()
   1. num2date()
   1. DateFmt()

<table>
 <tbody>
  <tr>
   <td><strong>API</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Afwijking</strong></td>
  </tr>
  <tr>
   <td>console.println()</td>
   <td>Deze acrobat-API zet de uitvoer op de JavaScript-console neer.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.alert()</td>
   <td>Deze acrobat API verstuurt een waarschuwingsbericht via JavaScript popup.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.beep()</td>
   <td>Hiermee wordt door het systeem een geluid afgespeeld.</td>
   <td>Er wordt geen actie uitgevoerd.</td>
  </tr>
  <tr>
   <td>app.execDialog()</td>
   <td>Hiermee wordt een modaal dialoogvenster voor de gebruiker weergegeven. De modale dialoogvensters moeten door de gebruiker worden gesloten voordat de hosttoepassing rechtstreeks opnieuw kan worden gebruikt.</td>
   <td>Er wordt geen actie uitgevoerd.<br /> </td>
  </tr>
  <tr>
   <td>app.launchURL()</td>
   <td>Hiermee wordt een URL gestart in een browservenster.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setInterval()</td>
   <td>Hiermee worden een JavaScript-script en een tijdsperiode opgegeven. Het script wordt uitgevoerd telkens wanneer de punt vervalt. De geretourneerde waarde van deze methode moet in een JavaScript-variabele worden opgeslagen. Anders, is het intervalvoorwerp onderworpen aan huisvuilinzameling, die de klok zou veroorzaken om te stoppen. Om de periodieke uitvoering te eindigen, ga het teruggekeerde intervalvoorwerp tot clearInterval over.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setTimeOut()</td>
   <td>Hiermee worden een JavaScript-script en een tijdsperiode opgegeven. Het script wordt slechts eenmaal uitgevoerd, nadat de punt is verstreken. De geretourneerde waarde van deze methode moet in een JavaScript-variabele worden gehouden. Anders is het time-outobject onderhevig aan opschoning, waardoor de klok zou stoppen. Als u de time-outgebeurtenis wilt annuleren, geeft u het geretourneerde time-outobject door aan clearTimeOut.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.clearInterval()</td>
   <td>Annuleert een eerder geregistreerd interval dat aanvankelijk door de setInterval methode wordt geplaatst.</td>
   <td>In HTML5-formulieren werkt de API niet correct.</td>
  </tr>
  <tr>
   <td>app.clearTimeOut()</td>
   <td>Annuleert een eerder geregistreerd onderbreking. Een dergelijk interval wordt aanvankelijk ingesteld door setTimeOut.</td>
   <td>In HTML5-formulieren werkt de API niet correct.<br /> </td>
  </tr>
  <tr>
   <td>app.eval()</td>
   <td>Hiermee wordt een bepaald script uitgevoerd.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.activeDocs</td>
   <td>Een array met het object Doc voor elk actief document. Als er geen documenten actief zijn, retourneert activeDocs niets. Dit houdt in dat het dezelfde werking heeft als d = new Array(0) in kern-JavaScript.</td>
   <td>Retourneert een lege array voor HTML5-formulieren.</td>
  </tr>
  <tr>
   <td>app.calculate</td>
   <td>Indien true (de standaardwaarde), kunnen berekeningen worden uitgevoerd. Als de waarde false is, zijn berekeningen niet toegestaan.</td>
   <td>Altijd waar voor HTML5 Forms.</td>
  </tr>
  <tr>
   <td>app.constants</td>
   <td>Een omvattend object voor het bevatten van verschillende constante waarden. Deze eigenschap retourneert momenteel een object met één eigenschap, uitlijnen.</td>
   <td>HTML5-formulieren retourneren een leeg uitlijningsobject.</td>
  </tr>
  <tr>
   <td>app.focusRect</td>
   <td>Hiermee schakelt u de focusrechthoek in of uit. De focusrechthoek bestaat uit de stippellijn met een zwakke punt rond knoppen, selectievakjes, keuzerondjes en handtekeningen om aan te geven dat het formulierveld de toetsenbordfocus heeft. Bij de waarde true wordt de focusrechthoek ingeschakeld.</td>
   <td>Altijd waar voor HTML5-formulieren.</td>
  </tr>
  <tr>
   <td>app.formsVersion</td>
   <td>Het versienummer van de viewer voor formulieren. Controleer deze eigenschap om te bepalen of objecten, eigenschappen of methoden in nieuwere versies van de software beschikbaar zijn als u achterwaartse compatibiliteit in uw scripts wilt behouden.</td>
   <td>11.001 altijd.</td>
  </tr>
  <tr>
   <td>app.language</td>
   <td>De taal van de actieve Acrobat-viewer.</td>
   <td>Altijd ENU voor HTML5-formulieren.</td>
  </tr>
 </tbody>
</table>

## Ondersteunde XFA-gebeurtenissen {#supported-xfa-events}

De volgende client-side XFA-gebeurtenissen worden ondersteund:

* Initialiseren
* Valideren
* Berekenen
* Klikken
* Enter
* Afsluiten
* Wijzigen
* ValidationState

>[!NOTE]
>
>HTML5-formulieren worden weergegeven op de client (browser). Client-kant gebruiken **validate** en **berekenen** scripts in plaats van serverscripts.
