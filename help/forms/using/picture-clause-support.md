---
title: Ondersteuning voor afbeeldingsclausules voor HTML5-formulieren
description: HTML5-formulieren ondersteunen de XFA-afbeeldingsvoorwaarde voor de weergavewaarde en de opgemaakte waarde voor datum, tekst en numerieke symbolen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 5e344be7-46cd-4e1f-ae3a-1f89c645cffe
feature: HTML5 Forms,Mobile Forms
exl-id: 7f9c77c6-447a-407f-ae58-6735176dc99c
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Ondersteuning voor afbeeldingsclausules voor HTML5-formulieren {#picture-clause-support-for-html-forms}

HTML5-formulieren ondersteunen de XFA-afbeeldingsvoorwaarde voor de weergavewaarde en de opgemaakte waarde voor datum, tekst en numerieke symbolen. De volgende uitdrukkingen van de Beeldclausule worden gesteund:

* category (locale){picture-clause} | category (locale){picture-clause} | category (locale){picture-clause}
* category.subcategory{}

>[!NOTE]
>
>Op dit moment biedt Mobiles Forms geen ondersteuning voor de optie Beeld bewerken. Ook worden symbolen van de DateTime- en Time Picture-component niet ondersteund.

## Ondersteunde datumveldsymbolen {#supported-date-field-symbols}

Ondersteunde expressie voor Datumafbeeldingsvoorwaarde:

* date.long{}
* date.short{}
* date.medium{}
* date.full{}
* date.short{}
* date{date Picture Clause symbols}

>[!NOTE]
>
>Het standaardpatroon van een afbeeldingsvoorwaarde is het patroon {MMM D, YYYY} . Als er geen patroon wordt toegepast, wordt het standaardpatroon gebruikt.

<table>
 <tbody>
  <tr>
   <th><strong>Symbool</strong></th>
   <th>Interpretatie</th>
  </tr>
  <tr>
   <td>D</td>
   <td>Dag van de maand met 1 of 2 cijfers (1-31)</td>
  </tr>
  <tr>
   <td>DD</td>
   <td>Dag van de maand met 2 cijfers en een voorloopnul (01-31).<br /> </td>
  </tr>
  <tr>
   <td>M</td>
   <td>Maand van het jaar met 1 of 2 cijfers (1-12).<br /> </td>
  </tr>
  <tr>
   <td>MM</td>
   <td>Maand van het jaar met 2 cijfers en een voorloopnul (01-12).<br /> </td>
  </tr>
  <tr>
   <td>MMM</td>
   <td>Verkorte naam van de maand van de huidige landinstelling<br /> </td>
  </tr>
  <tr>
   <td>MMMM</td>
   <td>Volledige naam maand van huidige landinstelling<br /> </td>
  </tr>
  <tr>
   <td>EEA</td>
   <td>Verkorte weekdagnaam van de huidige landinstelling<br /> </td>
  </tr>
  <tr>
   <td>EEEE</td>
   <td>Volledige weekdagnaam van de huidige landinstelling<br /> </td>
  </tr>
  <tr>
   <td>JJ</td>
   <td>Jaar met twee cijfers, waarbij 00 = 2000, 29 = 2029, 30 = 1930 en 99 = 1999<br /> </td>
  </tr>
  <tr>
   <td>JJJJ</td>
   <td>Jaar met vier cijfers<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
> Het datumveld in HTML5 Forms biedt geen ondersteuning voor de `MM-YYYY` patroon in bewerkingsindeling. Het patroon wordt echter wel ondersteund in de weergave-indeling.

## Numerieke afbeeldingsclausule {#numeric-picture-clause}

HTML5-formulieren ondersteunen numerieke afbeeldingssymbolen. Er is echter een verschil in steun tussen PDF forms en HTML Forms.

In **PDF forms**, wordt een getal opgemaakt ongeacht het aantal symbolen in de afbeeldingscomponent

In **HTML Forms**, wordt een getal alleen opgemaakt als het getal cijfers bevat die kleiner zijn dan het aantal symbolen in de Fotocomponent.

**Voorbeeld**: Overweeg een afbeeldingsvoorwaarde: num{zzz,zzz,zz9}.

Het getal **10000** is opgemaakt als **10 000** zowel in HTML als in PDF forms.

Het getal 1000000 wordt opgemaakt als 1000.000 in PDF forms. In HTML Forms blijft het getal echter ongeformatteerd als 1000000.

Ondersteunde expressies voor de component Numeriek beeld in **HTML Forms** zijn:

* num.integer{}
* num.decimal{}
* num.currency{}
* num.percent{}
* num{Numeric Picture Clause Symbols}

<table>
 <tbody>
  <tr>
   <th><strong>Symbool</strong></th>
   <th><strong>Interpretatie</strong></th>
   <th>Invoer parseren</th>
  </tr>
  <tr>
   <td>9</td>
   <td><strong>Uitvoeropmaak</strong>: één cijfer. Of voor het cijfer nul als de invoergegevens leeg zijn of een spatie op de corresponderende positie.<br /> </td>
   <td>Eén cijfer</td>
  </tr>
  <tr>
   <td>Z</td>
   <td><strong>Uitvoeropmaak</strong>: één cijfer. Of voor een spatie als de invoergegevens leeg zijn, een spatie, of het nul cijfer in de overeenkomstige positie.<br /> </td>
   <td>Eén cijfer of spatie</td>
  </tr>
  <tr>
   <td>z</td>
   <td><strong>Uitvoeropmaak</strong>: één cijfer. Of voor niets als de invoergegevens leeg zijn, een spatie, of het nul cijfer in de overeenkomstige positie.<br /> </td>
   <td>Eén cijfer of niets</td>
  </tr>
  <tr>
   <td>E</td>
   <td><strong>Uitvoeropmaak</strong>: het exponentgedeelte van een drijvende-kommagetal dat bestaat uit het exponentiële symbool (E). gevolgd door een optioneel plus- of minteken. Wordt gevolgd door de exponentwaarde.<br /> </td>
   <td>Hetzelfde als voor uitvoeropmaak</td>
  </tr>
  <tr>
   <td>CR of cr<br /> </td>
   <td>Credit-symbool (CR) als het een negatief getal is. Anders niets.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>S of s<br /> </td>
   <td>Uitvoeropmaak: een minteken als het een negatief getal is. Anders spatie.<br /> </td>
   <td>Min teken als het getal negatief is. plusteken als het getal positief is</td>
  </tr>
  <tr>
   <td>V</td>
   <td>Decimale radix van de geldende landinstelling. De decimale radix mag worden geïmpliceerd bij het parseren van de invoer.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>v</td>
   <td>Decimale radix van de geldende landinstelling. De decimale radix mag worden geïmpliceerd bij het parseren van invoer en uitvoeropmaak.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>.</td>
   <td>Decimale radix van de geldende landinstelling.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>, (U+FF0C)</td>
   <td>Groeperingsscheidingsteken voor de geldende landinstelling</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>$ (U+FF04)</td>
   <td>Valutasymbool van de geldende landinstelling.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>% (U+FF05)</td>
   <td>Percentagesymbool van de geldende landinstelling.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>( (U+FF08)</td>
   <td>haakje openen als het getal negatief is. Anders spatie.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>) (U+FF09)</td>
   <td>Haakje rechts als het getal negatief is. Anders spatie.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>t</td>
   <td>Tabteken</td>
   <td><br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

## Clausule tekstafbeelding {#text-picture-clause}

HTML5-formulieren ondersteunen de volgende Text Picture-componentexpressies:

* text{text Picture clause symbols symbols}

| **Symbool** | **Interpretatie** |
|---|---|
| A | Eén alfabetisch teken. |
| X | Eén teken. |
| O | Eén alfanumeriek teken. |
| 0 (nul) | Eén alfanumeriek teken. |
| 9 | Eén cijfer. |
