---
title: API om de service voor formuliergegevensmodellen aan te roepen vanuit adaptieve formulieren
seo-title: API om de service voor formuliergegevensmodellen aan te roepen vanuit adaptieve formulieren
description: Verklaart invokeWebServices API die u kunt gebruiken om Webdiensten aan te halen die in WSDL van binnen een adaptief vormgebied worden geschreven.
seo-description: Verklaart invokeWebServices API die u kunt gebruiken om Webdiensten aan te halen die in WSDL van binnen een adaptief vormgebied worden geschreven.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# API om de service voor formuliergegevensmodellen aan te roepen vanuit adaptieve formulieren {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Overzicht {#overview}

Met AEM Forms kunnen auteurs van formulieren de invulervaring van formulieren verder vereenvoudigen en verbeteren door services aan te roepen die vanuit een adaptief formulierveld in een formuliergegevensmodel zijn geconfigureerd. Om de dienst van een gegevensmodel aan te halen, kunt u of een regel in de visuele redacteur tot stand brengen of een JavaScript specificeren gebruikend `guidelib.dataIntegrationUtils.executeOperation` API in de coderedacteur van de [regelredacteur](/help/forms/using/rule-editor.md).

In dit document wordt het schrijven van een JavaScript met de `guidelib.dataIntegrationUtils.executeOperation` API voor het oproepen van een service centraal gesteld.

## De API gebruiken {#using-the-api}

De `guidelib.dataIntegrationUtils.executeOperation` API roept een service aan vanuit een adaptief formulierveld. De API-syntaxis ziet er als volgt uit:

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

De API vereist de volgende parameters.

| Parameter | Beschrijving |
|---|---|
| `operationInfo` | Structuur voor het opgeven van de modelidentificatie, de bewerkingstitel en de naam van de bewerking van het formulier |
| `inputs` | Structuur om formulierobjecten op te geven waarvan de waarden worden ingevoerd voor de servicebewerking |
| `outputs` | Structuur voor het opgeven van formulierobjecten die worden gevuld met de waarden die door de servicebewerking worden geretourneerd |

De structuur van de `guidelib.dataIntegrationUtils.executeOperation` API geeft details over de servicebewerking op. De syntaxis van de structuur is als volgt.

```
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
   <td><code>forDataModelId</code></td>
   <td>Geef het pad van de gegevensopslagruimte naar het formuliergegevensmodel op, inclusief de naam ervan</td>
  </tr>
  <tr>
   <td><code>operationName</code></td>
   <td>Geef de naam op van de uit te voeren servicebewerking</td>
  </tr>
  <tr>
   <td><code>input</code></td>
   <td>Een of meer formulierobjecten toewijzen aan de invoerargumenten voor de servicebewerking</td>
  </tr>
  <tr>
   <td>Uitvoer</td>
   <td>Een of meer formulierobjecten toewijzen aan uitvoerwaarden van de servicebewerking om formuliervelden te vullen<br /> </td>
  </tr>
 </tbody>
</table>

## Voorbeeldscript om een service aan te roepen {#sample-script-to-invoke-a-service}

In het volgende voorbeeldscript wordt de `guidelib.dataIntegrationUtils.executeOperation` API gebruikt om de `getAccountById` servicebewerking aan te roepen die in het `employeeAccount` formuliergegevensmodel is geconfigureerd.

De `getAccountById` bewerking neemt de waarde in het `employeeID` formulierveld op als invoer voor het `empId` argument en retourneert de werknemernaam, het accountnummer en het rekeningssaldo voor de corresponderende employee. De uitvoerwaarden worden ingevuld in de opgegeven formuliervelden. De waarde in `name` argument wordt bijvoorbeeld ingevuld in het `fullName` formulierelement en de waarde voor het `accountNumber` argument in het `account` formulierelement.

```
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

