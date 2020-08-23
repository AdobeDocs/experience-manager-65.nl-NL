---
title: Aangepaste weergaven maken in HTML5-formulieren
seo-title: Aangepaste weergaven maken in HTML5-formulieren
description: U kunt aangepaste widgets aansluiten op een mobiele Forms. U kunt bestaande jQuery-widgets uitbreiden of uw eigen aangepaste widgets ontwikkelen.
seo-description: U kunt aangepaste widgets aansluiten op een mobiele Forms. U kunt bestaande jQuery-widgets uitbreiden of uw eigen aangepaste widgets ontwikkelen.
uuid: a9013c3d-20c7-45c9-be24-8e9d4525eff8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 17a86543-30d3-4e16-a373-67b46d551da9
docset: aem65
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---


# Aangepaste weergaven maken in HTML5-formulieren{#create-custom-appearances-in-html-forms}

U kunt aangepaste widgets aansluiten op een mobiele Forms. U kunt bestaande jQuery-widgets uitbreiden of uw eigen aangepaste widgets ontwikkelen met het raamwerk voor weergaven. De XFA-engine gebruikt verschillende widgets. Zie [Weergaveframework voor adaptieve formulieren en HTML5-formulieren](/help/forms/using/introduction-widgets.md) voor meer informatie.

![Een voorbeeld van de standaard- en aangepaste widget](assets/custom-widgets.jpg)

Een voorbeeld van de standaard- en aangepaste widget

## Aangepaste widgets integreren met HTML5-formulieren {#integrating-custom-widgets-with-html-forms}

### Een profiel maken  {#create-a-profile-nbsp}

U kunt een profiel maken of een bestaand profiel kiezen om een aangepaste widget toe te voegen. Zie Aangepast profiel [maken voor meer informatie over het maken van profielen](/help/forms/using/custom-profile.md).

### Een widget maken {#create-a-widget}

HTML5-formulieren bieden een implementatie van het widgetframework dat kan worden uitgebreid om nieuwe widgets te maken. De implementatie bestaat uit een *abstracte widget* voor jQuery die kan worden uitgebreid om een nieuwe widget te schrijven. De nieuwe widget kan alleen functioneel worden gemaakt door de hieronder vermelde functies uit te breiden of te overschrijven.

<table>
 <tbody>
  <tr>
   <td>Functie/klasse</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td>renderen</td>
   <td>De renderfunctie retourneert het jQuery-object voor het standaard HTML-element van de widget. Het standaard-HTML-element moet van het brandpunttype zijn. Bijvoorbeeld &lt;a&gt;, &lt;input&gt; en &lt;li&gt;. Het geretourneerde element wordt gebruikt als $userControl. Als $userControl de bovengenoemde beperking specificeert, dan werken de functies van de klasse AbstractWidget zoals verwacht, anders vereisen sommige gemeenschappelijke APIs (nadruk, klik) veranderingen. </td>
  </tr>
  <tr>
   <td>getEventMap</td>
   <td>Retourneert een kaart voor het converteren van HTML-gebeurtenissen naar XFA-gebeurtenissen. <br /> {<br /> vervagen: XFA_EXIT_EVENT,<br /> }<br /> In dit voorbeeld wordt getoond dat de vervaging een HTML-gebeurtenis is en dat XFA_EXIT_EVENT corresponderende XFA-gebeurtenis is. </td>
  </tr>
  <tr>
   <td>getOptionsMap</td>
   <td>Retourneert een kaart die gedetailleerde informatie bevat over de handeling die moet worden uitgevoerd bij wijziging van een optie. De sleutels zijn de opties die aan widget worden verstrekt en de waarden zijn de functies die worden geroepen wanneer een verandering in die optie wordt ontdekt. De widget biedt handlers voor alle algemene opties (behalve value en displayValue)</td>
  </tr>
  <tr>
   <td>getCommitValue</td>
   <td>Het widgetframework laadt de functie wanneer de waarde van de widget wordt opgeslagen in het XFAModel (bijvoorbeeld bij afsluitgebeurtenis van een textField). De implementatie moet de waarde retourneren die is opgeslagen in de widget. De handler krijgt de nieuwe waarde voor de optie.</td>
  </tr>
  <tr>
   <td>showValue</td>
   <td>Standaard wordt in XFA bij Enter de rawValue van het veld weergegeven. Deze functie wordt aangeroepen om de rawValue aan de gebruiker te tonen. </td>
  </tr>
  <tr>
   <td>showDisplayValue</td>
   <td>Standaard wordt in XFA bij afsluitgebeurtenis de formattedValue van het veld weergegeven. Deze functie wordt geroepen om formattedValue aan de gebruiker te tonen. </td>
  </tr>
 </tbody>
</table>

Als u uw eigen widget wilt maken, neemt u in het hierboven gemaakte profiel verwijzingen op van het JavaScript-bestand dat overschreven functies en nieuw toegevoegde functies bevat. De *sliderNumericFieldWidget* is bijvoorbeeld een widget voor numerieke velden. Als u de widget in uw profiel in de koptekstsectie wilt gebruiken, neemt u de volgende regel op:

```javascript
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### Aangepaste widget registreren met XFA Scripting Engine  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

Wanneer de aangepaste widgetcode gereed is, registreert u de widget met de scriptengine met behulp van de `registerConfig`API voor [Form Bridge](/help/forms/using/form-bridge-apis.md). Het neemt widgetConfigObject als input.

```javascript
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

De widgetconfiguratie wordt aangeboden als een JSON-object (een verzameling sleutelwaardeparen), waarbij de sleutel de velden identificeert en de waarde de widget vertegenwoordigt die met deze velden moet worden gebruikt. Een voorbeeldconfiguratie ziet er als volgt uit:

```
*{*

*“identifier1” : “customwidgetname”,
“identifier2” : “customwidgetname2”,
..
}*
```

waarbij &quot;id&quot; een jQuery CSS-kiezer is die een bepaald veld, een set velden van een bepaald type of alle velden vertegenwoordigt. In het volgende voorbeeld wordt de waarde van de id in verschillende gevallen weergegeven:

| Type id | Id | Beschrijving |
|---|---|---|
| Specifiek veld met naam van veld | Id:&quot;div.fieldName&quot; | Alle velden met de naam &#39;veldnaam&#39; worden weergegeven met de widget. |
| Alle velden van het type ‘type’ (waarbij het type NumericField, DateField enzovoort is).: | Id: &quot;div.type&quot; | Voor Tijdveld en DateTimeField is het type tekstveld omdat deze velden niet worden ondersteund. |
| Alle velden | Id: &quot;div.field&quot; |  |
