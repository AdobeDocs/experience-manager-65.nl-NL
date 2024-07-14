---
title: CSS-stijlen maken voor HTML5-formulieren
description: Leer hoe u de weergave van HTML5-formulieren wijzigt door de CSS-klasse te wijzigen die is gekoppeld aan het HTML-formulierelement.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: a8d986ab-2a4c-488b-957e-4606f7391bd3
feature: HTML5 Forms,Mobile Forms
exl-id: 8cc90ff7-284e-41cd-bfda-7fa09371e270
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 0%

---

# CSS-stijlen maken voor HTML5-formulieren {#creating-css-styles-for-html-forms}

HTML5-uitvoering van een op XFA gebaseerde formuliersjabloon bestaat uit verschillende HTML-elementen. Deze elementen worden in een volgorde gerangschikt. Elk element heeft duidelijk gedefinieerde CSS-klassen. U kunt deze CSS-klasse gebruiken om de weergave van een element te selecteren en te wijzigen.

>[!NOTE]
>
>Wijzig in de CSS-klassen de waarde van de breedte, hoogte, randdikte, boven, links, rechts, onder, opvulling, marge en andere positie- en groottekenmerken niet. Als u de positie- en groottekenmerken wijzigt, verandert de indeling van het formulier.

## CSS-klassen  voor elementen  {#css-classes-nbsp-for-elements-nbsp}

Elk element bevat duidelijk gedefinieerde CSS-klassen. U kunt deze klassen wijzigen om de weergave van een element te wijzigen. Elk element, behalve het veld en draw-elementen, heeft twee CSS-klassen: de klasse Type en de klasse Name.

* De **klasse van het Type** vertegenwoordigt het type van het XFA gebied. U kunt de klasse `type` overschrijven om de stijlen van alle elementen van een bepaald type te wijzigen.

* De **klasse van de Naam** beantwoordt aan de naam van het XFA gebied. U kunt de klasse `name` overschrijven om een aangepaste stijl te wijzigen en op een element toe te passen.

>[!NOTE]
>
>Sommige XFA-elementen hebben geen naam. Als u de stijlen van dergelijke componenten wilt wijzigen, wijzigt u alle componenten van dat specifieke type.

Voor pagina&#39;s die niet in de AEM Forms Designer zijn genoemd, worden pagina&#39;s in een HTML5-formulier in toenemende mate genummerd. Voor een HTML5-formulier met twee pagina&#39;s krijgen de pagina&#39;s bijvoorbeeld de naam Pagina1, Pagina2.

## Veldelement {#field-element}

Het veldelement bevat twee geneste elementen: widget en bijschrift.

**element Widget**

Het widgetelement bevat het interface-element voor interactie met gebruikers. De klasse heeft drie CSS-klassen:

* **Widget**: Elke widget heeft deze klasse.
* **naam**: Alle widgets die met AEM worden verscheept bevatten de widgetnaamklasse. Voor aangepaste widgets biedt de widgetontwikkelaar de widgetnaamklasse.
* **type**: Elke widget heeft een element van het gebruikersinterface. Deze klasse definieert het type van het interface-element.

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

Naast het type en de naamklasse, bevat de gebiedscomponent ook een extra CSS klasse genoemd **subtype**. Een subtype geeft aan welk type veld het is, bijvoorbeeld NumericField, DateField, TextField. U kunt de subtypeklasse overschrijven om de opmaak van alle velden van het type, subtype, te wijzigen.

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
   <td>Gebruiker-bepaalde naam <br /> of <br /> Pagina&lt;pageNumber&gt; (gebrek)</td>
  </tr>
  <tr>
   <td>Inhoudsgebied</td>
   <td>inhoudsgebied</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Subformulier</td>
   <td>subformulier</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Uitsluitingsgroep</td>
   <td>uitsluiten</td>
   <td>Door gebruiker gedefinieerde naam</td>
  </tr>
  <tr>
   <td>Draw</td>
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
   <td>bijschrift</td>
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

De AEM Forms Designer ondersteunt verschillende typen velden in een formulier, zoals NumericField, DecimalField en Date Field. Al deze velden in HTML bevatten de bovengenoemde CSS-klassen. Ze bevatten ook enkele extra klassen, afhankelijk van het type veld.

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
   <td>Knop <br type="_moz" /> </td>
   <td>NA</td>
   <td>xfaButton <br type="_moz" /> </td>
   <td>buttonfieldwidget <br type="_moz" /> </td>
   <td>input type=button <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>CheckButton <br type="_moz" /> </td>
   <td>checkbox field <br /> </td>
   <td>XfaCheckBox <br type="_moz" /> </td>
   <td>checkboxFieldWidget <br type="_moz" /> </td>
   <td>input type=checkbox <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DateField <br type="_moz" /> </td>
   <td>datefield <br type="_moz" /> </td>
   <td>dateField<br type="_moz" /> </td>
   <td>datefieldwidget <br type="_moz" /> </td>
   <td>input type=text <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DateTimeField <br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfield-widget</td>
   <td>input type=text <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DecimalField <br type="_moz" /> </td>
   <td>numericfield <br type="_moz" /> </td>
   <td>numericInput <br type="_moz" /> </td>
   <td>numericfieldwidget <br type="_moz" /> </td>
   <td>input type=text <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DropDown<br type="_moz" /> </td>
   <td>choicelist <br type="_moz" /> </td>
   <td>dropDownListWidget <br type="_moz" /> </td>
   <td>choicelistwidget <br type="_moz" /> </td>
   <td>selecteren</td>
  </tr>
  <tr>
   <td>ListBox<br type="_moz" /> </td>
   <td>choicelist <br type="_moz" /> </td>
   <td>listBoxWidget <br type="_moz" /> </td>
   <td>choicelistwidget <br type="_moz" /> </td>
   <td>ol</td>
  </tr>
  <tr>
   <td>NumericField <br type="_moz" /> </td>
   <td>numericfield <br type="_moz" /> </td>
   <td>numericInput <br type="_moz" /> </td>
   <td>numericfieldwidget <br type="_moz" /> </td>
   <td>input type=text <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>PasswordField <br type="_moz" /> </td>
   <td>wachtwoordveld <br type="_moz" /> </td>
   <td>defaultWidget <br type="_moz" /> </td>
   <td>wachtwoordwidget <br type="_moz" /> </td>
   <td>input type=password <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>RadioButton <br type="_moz" /> </td>
   <td>radiofield <br type="_moz" /> </td>
   <td>XfaCheckBox <br type="_moz" /> </td>
   <td>radiofieldwidget <br type="_moz" /> </td>
   <td>input type=radio <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>TextField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textFieldWidget <br type="_moz" /> </td>
   <td>input type=text <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>TimeField <br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textFieldWidget <br type="_moz" /> </td>
   <td>input type=text <br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

## CSS-klassen voor verschillende Draw Elements {#css-classes-for-different-draw-elements}

Met AEM Forms Designer kunt u statische tekenelementen, zoals tekst en afbeeldingen, invoegen. Voor elk tekenelement wordt een aparte CSS-klasse gekoppeld aan dat element. De lijst met CSS-klassen voor draw-elementen wordt hieronder weergegeven. Aan elk tekenelement is een tekenklasse gekoppeld.

| **Type van Draw** | **CSS klasse** |
|---|---|
| Tekst | text |
| Afbeelding | image |
| Rechthoek | rechthoek |
| Lijn | line |

## Andere delen van het formulier opmaken {#styling-other-parts-of-the-form}

Naast de weergave van UI-componenten in het HTML-formulier kunt u de stijl van elementen zoals inline-fouten, inline-waarschuwingen en velden met validatiefouten wijzigen.

`Styling Inline Errors`

Wanneer de validatie van een veld resulteert in een fout, wordt een inlinefout weergegeven wanneer het veld actief is. Om de stijl van gealigneerde fouten te veranderen, vervang CSS identiteitskaart **fout-msg**.

`Styling Inline Warnings`

Wanneer de validatie van een veld resulteert in een waarschuwing, wordt een inlinewaarschuwing weergegeven wanneer het veld actief is. Om de stijl van deze gealigneerde waarschuwingen te veranderen, vervang CSS identiteitskaart **waarschuwing-msg**.

`Styling Fields with Validation Errors`

Wanneer de validatie voor een veld mislukt, verandert de stijl van de widget. Deze stijlverandering wordt gedaan door een CSS klasse **widgetError** op de widgetcomponent toe te passen. Om het standaard stileren te wijzigen, treedt **widgetError** klasse met voeten.
