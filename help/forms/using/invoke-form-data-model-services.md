---
title: API om de service voor formuliergegevensmodellen aan te roepen vanuit adaptieve formulieren
description: Verklaart invokeWebServices API die u kunt gebruiken om Webdiensten aan te halen die in WSDL van binnen een adaptief vormgebied worden geschreven.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms,Foundation Components
exl-id: cf037174-3153-486f-85b1-c974cd5a1ace
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# API om de service voor formuliergegevensmodellen aan te roepen vanuit adaptieve formulieren {#api-to-invoke-form-data-model-service-from-adaptive-forms}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/using/create-an-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Overzicht {#overview}

Met AEM Forms kunnen auteurs van formulieren de invulervaring van formulieren verder vereenvoudigen en verbeteren door services aan te roepen die vanuit een adaptief formulierveld zijn geconfigureerd in een formuliergegevensmodel. Om de dienst van het gegevensmodel aan te halen, kunt u of een regel in de visuele redacteur tot stand brengen of JavaScript specificeren gebruikend `guidelib.dataIntegrationUtils.executeOperation` API in de coderedacteur van de [&#x200B; regelredacteur &#x200B;](/help/forms/using/rule-editor.md).

Dit document is gericht op het schrijven van een JavaScript met de API `guidelib.dataIntegrationUtils.executeOperation` om een service aan te roepen.

## De API gebruiken {#using-the-api}

De API van `guidelib.dataIntegrationUtils.executeOperation` roept een service aan vanuit een adaptief formulierveld. De API-syntaxis ziet er als volgt uit:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

De structuur van de API van `guidelib.dataIntegrationUtils.executeOperation` specificeert details over de de dienstverrichting. De syntaxis van de structuur ziet er als volgt uit.

```javascript
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

De API-structuur geeft de volgende details over de servicebewerking op.

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>operationInfo</code></td>
   <td>Structuur voor het opgeven van de modelidentificatie, de bewerkingstitel en de naam van de bewerking van het formulier</td>
  </tr>
  <tr>
   <td><code>formDataModelId</code></td>
   <td>Hiermee wordt het opslagpad naar het formuliergegevensmodel opgegeven, inclusief de naam ervan</td>
  </tr>
  <tr>
   <td><code>operationName</code></td>
   <td>Specificeert de naam van de uit te voeren de dienstverrichting</td>
  </tr>
  <tr>
   <td><code>inputs</code></td>
   <td>Hiermee worden een of meer formulierobjecten toegewezen aan de invoerargumenten voor de servicebewerking</td>
  </tr>
  <tr>
   <td><code>Outputs</code></td>
   <td>Hiermee wijst u een of meer formulierobjecten toe aan uitvoerwaarden van de servicebewerking om formuliervelden te vullen. <br /> </td>
  </tr>
  <tr>
   <td><code>success</code></td>
   <td>Retourneert waarden die zijn gebaseerd op de invoerargumenten voor de servicebewerking. Het is een facultatieve parameter die als callback functie wordt gebruikt.<br /> </td>
  </tr>
  <tr>
   <td><code>failure</code></td>
   <td>Toont een foutenmelding als de succesvolle callback functie er niet in slaagt om de outputwaarden te tonen die op de inputargumenten worden gebaseerd. Het is een facultatieve parameter die als callback functie wordt gebruikt.<br /> </td>
  </tr>
 </tbody>
</table>

## Voorbeeldscript om een service aan te roepen {#sample-script-to-invoke-a-service}

In het volgende voorbeeldscript wordt de `guidelib.dataIntegrationUtils.executeOperation` API gebruikt om de `getAccountById` -servicebewerking aan te roepen die in het `employeeAccount` -formuliergegevensmodel is geconfigureerd.

De bewerking `getAccountById` neemt de waarde in het `employeeID` -formulierveld op als invoer voor het argument `empId` en retourneert de werknemernaam, het accountnummer en het rekeningsaldo voor de corresponderende employee. De uitvoerwaarden worden ingevuld in de opgegeven formuliervelden. De waarde in het argument `name` wordt bijvoorbeeld ingevuld in het argument `fullName` form element and value for `accountNumber` in het formulierelement `account` .

```javascript
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```

## API gebruiken met callback-functie {#using-the-api-callback}

U kunt de service van het formuliergegevensmodel ook aanroepen met de API van `guidelib.dataIntegrationUtils.executeOperation` met een callback-functie. De API-syntaxis ziet er als volgt uit:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, callbackFunction)
```

De callback-functie kan `success` - en `failure` callback-functies hebben.

### Sampletcript van de steekproef met succes en mislukkingscallback functies {#callback-function-success-failure}

In het volgende voorbeeldscript wordt de `guidelib.dataIntegrationUtils.executeOperation` API gebruikt om de `GETOrder` -servicebewerking aan te roepen die in het `employeeOrder` -formuliergegevensmodel is geconfigureerd.

De bewerking `GETOrder` neemt de waarde in het `Order ID` formulierveld als invoer voor het argument `orderId` en retourneert de waarde voor het aantal orders in de callback-functie `success` .  Wanneer de callback-functie `success` niet het aantal orders retourneert, geeft de callback-functie `failure` het `Error occured` -bericht weer.

>[!NOTE]
>
>Als u de callback-functie `success` gebruikt, worden de uitvoerwaarden niet in de opgegeven formuliervelden ingevuld.

```javascript
var operationInfo = {
    "formDataModelId": "/content/dam/formsanddocuments-fdm/employeeOrder",
    "operationTitle": "GETOrder",
    "operationName": "GETOrder"
};
var inputs = {
    "orderId" : Order ID
};
var outputs = {};
var success = function (wsdlOutput, textStatus, jqXHR) {
order_quantity.value = JSON.parse(wsdlOutput).quantity;
 };
var failure = function(){
alert('Error occured');
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, success, failure);
```
