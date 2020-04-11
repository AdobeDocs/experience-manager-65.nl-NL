---
title: Weergaveframework voor adaptieve en HTML5-formulieren
seo-title: Weergaveframework voor adaptieve en HTML5-formulieren
description: Met mobiele formulieren worden formuliersjablonen weergegeven als HTML5-formulieren. Deze formulieren gebruiken de bestanden jQuery, Backbone.js en Underscore.js voor de weergave en om scripts in te schakelen.
seo-description: Met mobiele formulieren worden formuliersjablonen weergegeven als HTML5-formulieren. Deze formulieren gebruiken de bestanden jQuery, Backbone.js en Underscore.js voor de weergave en om scripts in te schakelen.
uuid: 183b8d71-44fc-47bf-8cb2-1cf920ffd23a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 3c2a44a7-24e7-49ee-bf18-eab0e44efa42
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Weergaveframework voor adaptieve en HTML5-formulieren {#appearance-framework-for-adaptive-and-html-forms}

Forms (adaptieve formulieren en HTML5-formulieren) gebruiken [jQuery](https://jquery.com/)-, [Backbone.js](https://backbonejs.org/) - en [Underscore.js](https://underscorejs.org/) -bibliotheken voor weergave en scripts. De formulieren gebruiken ook de [jQuery UI](https://jqueryui.com/) - **widget** -architectuur voor alle interactieve elementen (zoals velden en knoppen) in het formulier. Met deze architectuur kunnen formulierontwikkelaars een uitgebreide set beschikbare jQuery-widgets en -plug-ins gebruiken in Forms. U kunt ook formulierspecifieke logica implementeren terwijl u gegevens vastlegt van gebruikers, zoals beperkingen voor leadDigits/trailDigits of afbeeldingsclausules. Formulierontwikkelaars kunnen aangepaste toepassingen maken en gebruiken om de ervaring op het gebied van gegevensvastlegging te verbeteren en gebruikersvriendelijker te maken.

Dit artikel is bedoeld voor ontwikkelaars met voldoende kennis van jQuery- en jQuery-widgets. Het biedt inzicht in het weergaveframework en stelt ontwikkelaars in staat een alternatieve weergave voor een formulierveld te maken.

Het weergaveframework is afhankelijk van verschillende opties, gebeurtenissen (triggers) en functies om gebruikersinteracties met het formulier vast te leggen en reageert op modelwijzigingen om de eindgebruiker te informeren. Daarnaast:

* Het framework biedt een set opties voor de weergave van een veld. Deze opties zijn sleutelwaardeparen en worden in twee categorieën verdeeld: algemene opties en veldtype-specifieke opties.
* De verschijning, als deel van het contract, brengt een reeks gebeurtenissen zoals binnen en uitgang teweeg.
* De vormgeving is vereist voor het implementeren van een set functies. Sommige functies komen vaak voor, andere zijn specifiek voor veldtypefuncties.

## Algemene opties {#common-options}

Hier volgen de ingestelde globale opties. Deze opties zijn beschikbaar voor elk veld.

<table>
 <tbody>
  <tr>
   <th>Eigenschap </th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>name</td>
   <td>Een id die wordt gebruikt om dit object of deze gebeurtenis op te geven in scriptexpressies. Deze eigenschap geeft bijvoorbeeld de naam van de hosttoepassing op.</td>
  </tr>
  <tr>
   <td>value</td>
   <td>Werkelijke waarde van het veld. </td>
  </tr>
  <tr>
   <td>displayValue</td>
   <td>Deze waarde van het veld wordt weergegeven. </td>
  </tr>
  <tr>
   <td>screenReaderText</td>
   <td>Schermlezers gebruiken deze waarde om informatie over het veld van commentaar te voorzien. Het formulier bevat de waarde en u kunt de waarde overschrijven.<br /> </td>
  </tr>
  <tr>
   <td>tabIndex</td>
   <td>De positie van het veld in de tabvolgorde van het formulier. Overschrijf de tabIndex alleen als u de standaardtabvolgorde van het formulier wilt wijzigen.</td>
  </tr>
  <tr>
   <td>role</td>
   <td>Rol van het element, bijvoorbeeld Kop of Tabel.</td>
  </tr>
  <tr>
   <td>height</td>
   <td>De hoogte van de widget. Deze wordt opgegeven in pixels. </td>
  </tr>
  <tr>
   <td>width</td>
   <td>De breedte van de widget. Deze wordt opgegeven in pixels.</td>
  </tr>
  <tr>
   <td>access</td>
   <td>Controls used to access the contents of a container object, such as a subform.</td>
  </tr>
  <tr>
   <td>paraStyles</td>
   <td>De paraeigenschap van een XFA-element voor de widget.</td>
  </tr>
  <tr>
   <td>dir</td>
   <td>De richting van de tekst. De mogelijke waarden zijn ltr (van links naar rechts) en rtl (van rechts naar links).</td>
  </tr>
 </tbody>
</table>

Naast deze opties biedt het framework andere opties die afhankelijk zijn van het type veld. De details voor de velden-specifieke opties worden hieronder vermeld.

### Interactie met formulierraamwerk {#interaction-with-forms-framework}

Voor interactie met formulierframework activeert een widget bepaalde gebeurtenissen zodat het formulierscript kan werken. Als de widget deze gebeurtenissen niet genereert, werken sommige scripts die in het formulier voor dat veld zijn geschreven, niet.

#### Gebeurtenissen geactiveerd door widget {#events-triggered-by-widget}

<table>
 <tbody>
  <tr>
   <th>Gebeurtenis </th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>XFA_ENTER_EVENT</td>
   <td>Deze gebeurtenis wordt geactiveerd wanneer het veld de focus heeft. Hiermee kan het script "enter" in het veld worden uitgevoerd. De syntaxis voor het activeren van de gebeurtenis is<br /> (widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_ENTER_EVENT)<br /> </td>
  </tr>
  <tr>
   <td>XFA_EXIT_EVENT</td>
   <td>Deze gebeurtenis wordt geactiveerd wanneer de gebruiker het veld verlaat. Hiermee kan de engine de waarde van het veld instellen en het script "exit" uitvoeren. De syntaxis voor het activeren van de gebeurtenis is<br /> (widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_EXIT_EVENT)<br /> </td>
  </tr>
  <tr>
   <td>XFA_CHANGE_EVENT</td>
   <td>Deze gebeurtenis wordt geactiveerd om de engine in staat te stellen het script "change" uit te voeren dat in het veld wordt geschreven. De syntaxis voor het activeren van de gebeurtenis is<br /> (widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_CHANGE_EVENT)<br /> </td>
  </tr>
  <tr>
   <td>XFA_CLICK_EVENT</td>
   <td>Deze gebeurtenis wordt geactiveerd wanneer op het veld wordt geklikt. het staat de motor toe om het "klikmanuscript in werking te stellen dat op het gebied wordt geschreven. De syntaxis voor het activeren van de gebeurtenis is<br /> (widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_CLICK_EVENT)<br /> </td>
  </tr>
 </tbody>
</table>

#### API&#39;s die door widget zijn geïmplementeerd {#apis-implemented-by-widget}

Het weergaveframework roept enkele functies van de widget aan die in de aangepaste widgets zijn geïmplementeerd. De widget moet de volgende functies implementeren:

<table>
 <tbody>
  <tr>
   <th>-functie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>focus: function()</td>
   <td>Hiermee wordt de focus op het veld geplaatst.</td>
  </tr>
  <tr>
   <td>klikken: function()</td>
   <td>Hiermee wordt de focus op het veld geplaatst en wordt XFA_CLICK_EVENT aangeroepen.</td>
  </tr>
  <tr>
   <td><p>markError:function(errorMessage, errorType)<br /> <br /><em>errorMessage: string </em>die de error<br /> <em>errorType vertegenwoordigt: string ("warning"/"error")</em></p> <p><strong>Opmerking</strong>: Alleen van toepassing op HTML5-formulieren.</p> </td>
   <td>Verzendt foutberichten en fouttype naar de widget. De widget geeft de fout weer.</td>
  </tr>
  <tr>
   <td><p>clearError: function()</p> <p><strong>Opmerking</strong>: Alleen van toepassing op HTML5-formulieren.</p> </td>
   <td>Wordt aangeroepen als de fouten in het veld zijn gecorrigeerd. De widget verbergt de fout.</td>
  </tr>
 </tbody>
</table>

## Specifieke opties voor het veldtype {#options-specific-to-type-of-field}

Alle aangepaste widgets moeten voldoen aan de bovenstaande specificaties. Als u de functies van verschillende velden wilt gebruiken, moet de widget voldoen aan de richtlijnen voor dat veld.

### TextEdit: Tekstveld {#textedit-text-field}

<table>
 <tbody>
  <tr>
   <th>Optie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>multiline</td>
   <td>True if the field supports enter a newline character, else false.</td>
  </tr>
  <tr>
   <td>maxChars</td>
   <td>Maximumaantal tekens dat in het veld kan worden ingevoerd.</td>
  </tr>
  <tr>
   <td><p>limitLengthToVisibleArea</p> <p><strong>Opmerking</strong>: Alleen van toepassing op HTML5-formulieren</p> </td>
   <td>Geeft het gedrag van een tekstveld op wanneer de breedte van de tekst de breedte van de widget overschrijdt.</td>
  </tr>
 </tbody>
</table>

### ChoiceList: DropDownList, ListBox {#choicelist-dropdownlist-listbox}

<table>
 <tbody>
  <tr>
   <th>Optie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>value<br /> </td>
   <td>Array met geselecteerde waarden.<br /> </td>
  </tr>
  <tr>
   <td>items<br /> </td>
   <td>Array met objecten die als opties moeten worden weergegeven. Elk object bevat twee eigenschappen -<br /> save: op te slaan waarde, weergave: waarde die moet worden weergegeven.<br /> <br /> </td>
  </tr>
  <tr>
   <td><p>bewerkbaar</p> <p><strong>Opmerking</strong>: Alleen van toepassing op HTML5-formulieren.<br /> </p> </td>
   <td>Als de waarde true is, wordt de aangepaste tekstinvoer ingeschakeld in de widget.<br /> </td>
  </tr>
  <tr>
   <td>displayValue<br /> </td>
   <td>Array met waarden die moeten worden weergegeven.<br /> </td>
  </tr>
  <tr>
   <td>multiselect<br /> </td>
   <td>True if multiple selections are allowed, else false.<br /> </td>
  </tr>
 </tbody>
</table>

#### API {#api}

<table>
 <tbody>
  <tr>
   <th>-functie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><p>addItem:<em> function(itemValues)<br /> itemValues: object met de weergave- en opslagwaarde <br /> {sDisplayVal: &lt;displayValue&gt;, sSaveVal: &lt;waarde opslaan&gt;</em></p> </td>
   <td>Hiermee wordt een item aan de lijst toegevoegd.</td>
  </tr>
  <tr>
   <td>deleteItem<em>: function(nIndex)<br /> nIndex: index van het item dat uit de lijst<br /> moet worden verwijderd </em><br /><br /> </td>
   <td>Hiermee verwijdert u een optie uit de lijst.</td>
  </tr>
  <tr>
   <td>clearItems:<code> function()</code></td>
   <td>Hiermee wist u alle opties uit de lijst.</td>
  </tr>
 </tbody>
</table>

### NumericEdit: NumericField, DecimalField {#numericedit-numericfield-decimalfield}

| Opties | Beschrijving |
|---|---|
| dataType | Tekenreeks die het gegevenstype van het veld vertegenwoordigt (geheel getal/decimaal). |
| leadDigits | Maximum aantal voorloopcijfers toegestaan in het decimale getal. |
| fracDigits | Maximum aantal breukcijfers toegestaan in het decimale getal. |
| nul | Tekenreeksrepresentatie van nul in landinstelling van het veld. |
| decimal | Tekenreeksrepresentatie van decimaal in landinstelling van veld. |

### CheckButton: RadioButton, CheckBox {#checkbutton-radiobutton-checkbox}

<table>
 <tbody>
  <tr>
   <th>Opties</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>values</td>
   <td><p>Array van waarden (aan/uit/neutraal).</p> <p>Het is een array van waarden voor de verschillende toestanden van de checkButton. values[0] is the value when the state is ON, values[1] is the value when the state is OFF,<br /> values[2] is the value when the state is NEUTRAL. De lengte van de waardenarray is gelijk aan de waarde van de statusoptie.<br /> </p> </td>
  </tr>
  <tr>
   <td>statussen</td>
   <td><p>Aantal toegestane staten. </p> <p>Twee voor adaptieve formulieren (Aan, Uit) en drie voor HTML5-formulieren (Aan, Uit, Neutraal).</p> </td>
  </tr>
  <tr>
   <td>state</td>
   <td><p>Huidige status van het element.</p> <p>Twee voor adaptieve formulieren (Aan, Uit) en drie voor HTML5-formulieren (Aan, Uit, Neutraal).</p> </td>
  </tr>
 </tbody>
</table>

### DateTimeEdit: (DateField) {#datetimeedit-datefield}

| Optie | Beschrijving |
|---|---|
| dagen | Gelokaliseerde naam van dagen voor dat veld. |
| maanden | Gelokaliseerde maandnamen voor dat veld. |
| nul | De gelokaliseerde tekst voor het getal 0. |
| clearText | De gelokaliseerde tekst voor wissen knop. |
