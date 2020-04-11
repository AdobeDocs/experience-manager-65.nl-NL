---
title: CSS-stijlen maken voor HTML5-formulieren
seo-title: CSS-stijlen maken voor HTML5-formulieren
description: Leer hoe u de weergave van HTML5-formulieren wijzigt door de CSS-klasse te wijzigen die is gekoppeld aan het HTML-formulierelement.
seo-description: Leer hoe u de weergave van HTML5-formulieren wijzigt door de CSS-klasse te wijzigen die is gekoppeld aan het HTML-formulierelement.
uuid: 43c689b4-243c-43de-a8be-1eef10d75295
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: a8d986ab-2a4c-488b-957e-4606f7391bd3
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# CSS-stijlen maken voor HTML5-formulieren {#creating-css-styles-for-html-forms}

HTML5-uitvoering van een op XFA gebaseerde formuliersjabloon bestaat uit verschillende HTML-elementen. Deze elementen worden in een volgorde gerangschikt. Elk element heeft duidelijk gedefinieerde CSS-klassen. U kunt deze CSS-klasse gebruiken om de weergave van een element te selecteren en te wijzigen.

>[!NOTE]
>
>Wijzig in de CSS-klassen de waarde van de breedte, hoogte, randdikte, boven, links, rechts, onder, opvulling, marge en andere positie- en groottekenmerken niet. Als u de positie- en groottekenmerken wijzigt, verandert de indeling van het formulier.

## CSS-klassen voor elementen {#css-classes-nbsp-for-elements-nbsp}

Elk element bevat duidelijk gedefinieerde CSS-klassen. U kunt deze klassen wijzigen om de weergave van een element te wijzigen. Elk element, behalve het veld en draw-elementen, heeft twee CSS-klassen: de klasse Type en de klasse Name.

* De **klasse** Type vertegenwoordigt het type van het XFA gebied. U kunt de `type` klasse overschrijven om de stijlen van alle elementen van een bepaald type te wijzigen.

* De klasse **** Name komt overeen met de naam van het XFA-veld. U kunt de `name` klasse overschrijven om een aangepaste stijl te wijzigen en op een element toe te passen.

>[!NOTE]
>
>Sommige XFA-elementen hebben geen naam. Als u de stijlen van dergelijke componenten wilt wijzigen, wijzigt u alle componenten van dat specifieke type.

Voor pagina&#39;s die niet in de ontwerper van de Vormen van AEM worden genoemd, worden de pagina&#39;s in een vorm HTML5 genoemd in de stijgende orde van hun aantal. Voor een HTML5-formulier met twee pagina&#39;s krijgen de pagina&#39;s bijvoorbeeld de naam Pagina1, Pagina2.

## Veldelement {#field-element}

Het veldelement bevat twee geneste elementen: widget en bijschrift.

**Widget-element**

Het widgetelement bevat het interface-element voor interactie met gebruikers. De klasse heeft drie CSS-klassen:

* **Widget**: Elke widget heeft deze klasse.
* **naam**: Alle widgets die bij AEM worden geleverd, bevatten de widgetnaamklasse. Voor aangepaste widgets biedt de widgetontwikkelaar de widgetnaamklasse.
* **type**: Elke widget heeft een interface-element. Deze klasse definieert het type van het interface-element.

```xml
<!--field with caption-->
<div class="field numericfield NumericField3 ">
     <div class="caption">
        caption content
     </div>
     <div class="widget numericfieldwidget numericInput">
       widget content
     </div>
</div>

<!--field without caption-->
<div class="widget numericfieldwidget numericInput">
   widget content
</div>
```

Naast het type en de naamklasse bevat de veldcomponent ook een extra CSS-klasse met de naam **subtype**. Een subtype geeft aan welk type veld het is, bijvoorbeeld NumericField, DateField, TextField. U kunt de subtypeklasse overschrijven om de opmaak van alle velden met tekst en subtype te wijzigen.

## CSS-klassen voor verschillende componenten {#css-classes-for-different-components}

<table>
 <tbody>
  <tr>
   <td><strong>Component</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Naam</strong></td>
  </tr>
  <tr>
   <td>Pagina</td>
   <td>page</td>
   <td>Door gebruiker gedefinieerde naam<br /><br /> of pagina&lt;pageNumber&gt; (standaard)</td>
  </tr>
  <tr>
   <td>Inhoudsgebied</td>
   <td>inhoudsgebied</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Subformulier</td>
   <td>subform</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Uitsluitingsgroep</td>
   <td>uitsluiten</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Tekenen</td>
   <td>draw</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Veld</td>
   <td>field</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Bijschrift</td>
   <td>caption</td>
   <td>NA</td>
  </tr>
  <tr>
   <td>Widget</td>
   <td>widget</td>
   <td>De widgetontwikkelaar definieert dit (zie de tabel in de volgende sectie voor door de gebruiker gedefinieerde widgets)</td>
  </tr>
 </tbody>
</table>

## CSS-klassen voor verschillende velden {#css-classes-for-different-fields}

De ontwerper van de Vormen AEM steunt verschillende types van gebieden in een vorm zoals NumericField, DecimalField, en het Gebied van de Datum. Al deze velden in HTML bevatten de bovengenoemde CSS-klassen. Ze bevatten ook enkele extra klassen, afhankelijk van het type veld.

Aan elk veld is een widget gekoppeld die het interface-element vertegenwoordigt. De klassen van elk veld en de widgets die aan elk veld zijn gekoppeld, worden hieronder weergegeven.

<table>
 <tbody>
  <tr>
   <td><strong>Veldtype</strong></td>
   <td><strong>Subtype</strong></td>
   <td><strong>Widgetnaam</strong></td>
   <td><strong>Type widget</strong></td>
   <td><strong>HTML UI-tag</strong></td>
  </tr>
  <tr>
   <td>Knop<br type="_moz" /> </td>
   <td>NA</td>
   <td>xfaButton<br type="_moz" /> </td>
   <td>buttonfieldwidget<br type="_moz" /> </td>
   <td>input type=button<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>CheckButton<br type="_moz" /> </td>
   <td>checkbox, veld<br /> </td>
   <td>XfaCheckBox<br type="_moz" /> </td>
   <td>checkbox-widget<br type="_moz" /> </td>
   <td>invoertype=checkbox<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DateField<br type="_moz" /> </td>
   <td>datefield<br type="_moz" /> </td>
   <td>dateField<br type="_moz" /> </td>
   <td>datefieldwidget<br type="_moz" /> </td>
   <td>invoertype=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DateTimeField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfield-widget</td>
   <td>invoertype=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DecimalField<br type="_moz" /> </td>
   <td>numeriek veld<br type="_moz" /> </td>
   <td>numericInput<br type="_moz" /> </td>
   <td>numericfieldwidget<br type="_moz" /> </td>
   <td>invoertype=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DropDown<br type="_moz" /> </td>
   <td>choicelist<br type="_moz" /> </td>
   <td>dropDownListWidget<br type="_moz" /> </td>
   <td>choicelistwidget<br type="_moz" /> </td>
   <td>select</td>
  </tr>
  <tr>
   <td>ListBox<br type="_moz" /> </td>
   <td>choicelist<br type="_moz" /> </td>
   <td>listBoxWidget<br type="_moz" /> </td>
   <td>choicelistwidget<br type="_moz" /> </td>
   <td>ol</td>
  </tr>
  <tr>
   <td>NumericField<br type="_moz" /> </td>
   <td>numeriek veld<br type="_moz" /> </td>
   <td>numericInput<br type="_moz" /> </td>
   <td>numericfieldwidget<br type="_moz" /> </td>
   <td>invoertype=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>PasswordField<br type="_moz" /> </td>
   <td>wachtwoordveld<br type="_moz" /> </td>
   <td>defaultWidget<br type="_moz" /> </td>
   <td>wachtwoordwidget<br type="_moz" /> </td>
   <td>input type=password<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>RadioButton<br type="_moz" /> </td>
   <td>radioveld<br type="_moz" /> </td>
   <td>XfaCheckBox<br type="_moz" /> </td>
   <td>radiofieldwidget<br type="_moz" /> </td>
   <td>invoertype=radio<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>TextField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfield-widget<br type="_moz" /> </td>
   <td>invoertype=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>TimeField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfield-widget<br type="_moz" /> </td>
   <td>invoertype=text<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

## CSS-klassen voor verschillende Draw Elements {#css-classes-for-different-draw-elements}

Met de AEM Forms Designer kunt u statische tekenelementen, zoals tekst en afbeeldingen, invoegen. Voor elk tekenelement wordt een aparte CSS-klasse gekoppeld aan dat element. De lijst met CSS-klassen voor draw-elementen wordt hieronder weergegeven. Aan elk tekenelement is een tekenklasse gekoppeld.

| **Type tekenen** | **CSS-klasse** |
|---|---|
| Tekst | text |
| Afbeelding | image |
| Rechthoek | rectangle |
| Lijn | line |

## Andere delen van het formulier opmaken {#styling-other-parts-of-the-form}

Naast de weergave van UI-componenten in het HTML-formulier kunt u de stijl wijzigen van elementen zoals inline-fouten, inline-waarschuwingen en velden met validatiefouten.

`Styling Inline Errors`

Wanneer de validatie van een veld resulteert in een fout, wordt een inlinefout weergegeven wanneer het veld actief is. Als u de stijl van inlinefouten wilt wijzigen, overschrijft u de CSS-id- **foutmelding**.

`Styling Inline Warnings`

Wanneer de validatie van een veld resulteert in een waarschuwing, wordt een inlinewaarschuwing weergegeven wanneer het veld actief is. Als u de stijl van deze inline-waarschuwingen wilt wijzigen, overschrijft u de CSS-id- **waarschuwing**.

`Styling Fields with Validation Errors`

Wanneer de validatie voor een veld mislukt, verandert de stijl van de widget. Deze stijlwijziging wordt uitgevoerd door een CSS- **klassewidgetError** toe te passen op de widgetcomponent. Als u de standaardopmaak wilt wijzigen, overschrijft u de **klasse widgetError** .
