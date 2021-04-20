---
title: API om de service voor formuliergegevensmodellen aan te roepen vanuit adaptieve formulieren
seo-title: API om de service voor formuliergegevensmodellen aan te roepen vanuit adaptieve formulieren
description: Verklaart invokeWebServices API die u kunt gebruiken om Webdiensten aan te halen die in WSDL van binnen een adaptief vormgebied worden geschreven.
seo-description: Verklaart invokeWebServices API die u kunt gebruiken om Webdiensten aan te halen die in WSDL van binnen een adaptief vormgebied worden geschreven.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# API om formuliergegevensmodelservice aan te roepen vanuit adaptieve formulieren {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Overzicht {#overview}

Met AEM Forms kunnen auteurs van formulieren de invulervaring van formulieren verder vereenvoudigen en verbeteren door services aan te roepen die vanuit een adaptief formulierveld zijn geconfigureerd in een formuliergegevensmodel. Om een dienst van het gegevensmodel aan te halen, kunt u of een regel in de visuele redacteur tot stand brengen of een JavaScript specificeren gebruikend `guidelib.dataIntegrationUtils.executeOperation` API in de coderedacteur van [rule redacteur](/help/forms/using/rule-editor.md).

Dit document is gericht op het schrijven van een JavaScript met de `guidelib.dataIntegrationUtils.executeOperation`-API om een service aan te roepen.

## API {#using-the-api} gebruiken

De `guidelib.dataIntegrationUtils.executeOperation`-API roept een service aan vanuit een adaptief formulierveld. De API-syntaxis ziet er als volgt uit:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

De structuur van de `guidelib.dataIntegrationUtils.executeOperation` API specificeert details over de de dienstverrichting. De syntaxis van de structuur is als volgt.

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
   <td>Hiermee wijst u een of meer formulierobjecten toe aan uitvoerwaarden van de servicebewerking om formuliervelden te vullen<br /> </td>
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

## Voorbeeldscript om de service {#sample-script-to-invoke-a-service} aan te roepen

In het volgende voorbeeldscript wordt de `guidelib.dataIntegrationUtils.executeOperation`-API gebruikt om de `getAccountById`-servicebewerking aan te roepen die in het formuliergegevensmodel `employeeAccount` is geconfigureerd.

De bewerking `getAccountById` neemt de waarde in het formulierveld `employeeID` als invoer voor het argument `empId` en retourneert de werknemernaam, het accountnummer en het rekeningssaldo voor de corresponderende employee. De uitvoerwaarden worden ingevuld in de opgegeven formuliervelden. De waarde in het argument `name` wordt bijvoorbeeld ingevuld in het formulierelement `fullName` en de waarde voor het argument `accountNumber` in het formulierelement `account`.

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

## API gebruiken met callback functie {#using-the-api-callback}

U kunt de service van het formuliergegevensmodel ook aanroepen met de API `guidelib.dataIntegrationUtils.executeOperation` met een callback-functie. De API-syntaxis ziet er als volgt uit:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, callbackFunction)
```

De callback functie kan `success` en `failure` callback functies hebben.

### Sampletcript van de steekproef met succes en mislukkingscallback functies {#callback-function-success-failure}

In het volgende voorbeeldscript wordt de `guidelib.dataIntegrationUtils.executeOperation`-API gebruikt om de `GETOrder`-servicebewerking aan te roepen die in het formuliergegevensmodel `employeeOrder` is geconfigureerd.

De bewerking `GETOrder` neemt de waarde in het formulierveld `Order ID` als invoer voor het argument `orderId` en retourneert de waarde voor het aantal orders in de callback-functie `success`.  Als de `success` callback functie niet de orde hoeveelheid terugkeert, toont de `failure` callback functie `Error occured` bericht.

>[!NOTE]
>
> Als u de callback-functie `success` gebruikt, worden de uitvoerwaarden niet in de opgegeven formuliervelden ingevuld.

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
