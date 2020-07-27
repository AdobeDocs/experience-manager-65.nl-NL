---
title: Standaardvalidatiefoutenberichten voor adaptieve formulieren
seo-title: Standaardvalidatiefoutenberichten voor adaptieve formulieren
description: Transformeer de foutberichten voor validatie van adaptieve formulieren naar de standaardnotatie met behulp van aangepaste fouthandlers
seo-description: Transformeer de foutberichten voor validatie van adaptieve formulieren naar de standaardnotatie met behulp van aangepaste fouthandlers
uuid: 0d1f9835-3e28-41d3-a3b1-e36d95384328
contentOwner: anujkapo
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
discoiquuid: ec062567-1c6b-497b-a1e7-1dbac2d60852
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---


# Standaardvalidatiefoutenberichten voor adaptieve formulieren {#standard-validation-error-messages}

Aangepaste formulieren valideren de invoer die u in velden opgeeft op basis van vooraf ingestelde validatiecriteria. De validatiecriteria verwijzen naar de aanvaardbare invoerwaarden voor velden in een adaptieve vorm. U kunt de validatiecriteria instellen op basis van de gegevensbron die u gebruikt bij het adaptieve formulier. Als u bijvoorbeeld RESTful-webservices gebruikt als gegevensbron, kunt u de validatiecriteria definiëren in een Swagger-definitiebestand.

Als de invoerwaarden aan de validatiecriteria voldoen, worden de waarden naar de gegevensbron verzonden. Anders wordt een foutbericht weergegeven in het aangepaste formulier.

Op dezelfde manier kunnen adaptieve formulieren nu worden geïntegreerd met aangepaste services om gegevensvalidaties uit te voeren. Als de invoerwaarden niet voldoen aan de validatiecriteria en het foutbericht dat de server retourneert, de standaardberichtindeling heeft, worden de foutberichten in het formulier op veldniveau weergegeven.

Als de invoerwaarden niet voldoen aan de validatiecriteria en het foutbericht voor servervalidatie niet in de standaardberichtindeling is, bieden de adaptieve formulieren een mechanisme om de foutberichten voor validatie om te zetten in een standaardnotatie, zodat ze op veldniveau in het formulier worden weergegeven. U kunt het foutbericht op een van de volgende twee manieren transformeren in de standaardindeling:

* Aangepaste fouthandler toevoegen bij het verzenden van aangepaste formulieren
* Voeg douanemanager toe om de actie van de Dienst aan te halen gebruikend de Redacteur van de Regel

In dit artikel wordt de standaardindeling beschreven voor de foutberichten voor validatie en de instructies voor het omzetten van de foutberichten van een aangepaste in de standaardindeling.

## Standaardberichtindeling voor validatiefouten {#standard-validation-message-format}

De adaptieve formulieren geven de fouten op veldniveau weer als de foutberichten voor servervalidatie de volgende standaardnotatie hebben:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]

        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
}
```

Waar:

* `errorCausedBy` beschrijft de reden van mislukking
* `errors` de SOM-expressie vermelden van de velden waarvoor de validatiecriteria niet zijn nageleefd, samen met het foutbericht voor de validatie
* `originCode` bevat de foutcode die door de externe service wordt geretourneerd
* `originMessage` bevat de onbewerkte foutgegevens die door de externe service worden geretourneerd

## Aangepaste formulierverzending configureren om aangepaste handlers toe te voegen {#configure-adaptive-form-submission}

Als het foutbericht voor servervalidatie niet in de standaardindeling wordt weergegeven, kunt u asynchrone verzending inschakelen en een aangepaste fouthandler toevoegen bij het verzenden van het formulier om het bericht om te zetten in een standaardindeling.

### Asynchrone adaptieve formulierverzending configureren {#configure-asynchronous-adaptive-form-submission}

Voordat u een aangepaste handler toevoegt, moet u het adaptieve formulier configureren voor asynchrone verzending. Voer de volgende stappen uit:

1. Selecteer in de modus Aangepast formulier het object Form Container en tik op ![adaptieve formuliereigenschappen](assets/configure_icon.png) om de eigenschappen ervan te openen.
1. Schakel in de sectie **[!UICONTROL Submission]** Eigenschappen **[!UICONTROL Use asynchronous submission]**.
1. Selecteer deze optie **[!UICONTROL Revalidate on server]** om de waarden van de invoervelden op de server vóór verzending te valideren.
1. Selecteer de handeling Verzenden:

   * Selecteer **[!UICONTROL Submit using Form Data Model]** en selecteer het juiste gegevensmodel als u het op RESTful-webservice gebaseerde [formuliergegevensmodel](work-with-form-data-model.md) als gegevensbron gebruikt.
   * Selecteer **[!UICONTROL Submit to REST endpoint]** en specificeer **[!UICONTROL Redirect URL/Path]**, als u de Webdiensten RESTful als gegevensbron gebruikt.

   ![adaptieve eigenschappen voor formulierverzending](assets/af_submission_properties.png)

1. Tik op ![Opslaan](assets/save_icon.png) om de eigenschappen op te slaan.

### Aangepaste fouthandler toevoegen bij het verzenden van aangepaste formulieren {#add-custom-error-handler-af-submission}

AEM Forms bieden foutverwerkers voor het verzenden van formulieren die buiten de box vallen. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een formulier wordt verzonden, worden de gegevens voor validatie naar de server verzonden, die een reactie op de client retourneert met informatie over de gebeurtenis &#39;success&#39; of &#39;error&#39; voor de verzending. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren.

Voer de volgende stappen uit om aangepaste fouthandler toe te voegen bij het verzenden van aangepaste formulieren:

1. Open het aangepaste formulier in de ontwerpmodus, selecteer een willekeurig formulierobject en tik op <!--![Rule Editor](assets/af_edit_rules.png)--> om de regeleditor te openen.
1. Selecteer **[!UICONTROL Form]** in de structuur Formulierobjecten en tik op **[!UICONTROL Create]**.
1. Selecteer een optie **[!UICONTROL Error in Submission]** in de vervolgkeuzelijst Gebeurtenis.
1. Schrijf een regel om de aangepaste foutstructuur om te zetten in de standaardfoutstructuur en tik **[!UICONTROL Done]** om de regel op te slaan.

Hieronder volgt een voorbeeldcode voor het omzetten van een aangepaste foutstructuur in de standaardfoutstructuur:

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

De `var som_map` SOM-expressie van de adaptieve formuliervelden die u in de standaardindeling wilt omzetten. U kunt de SOM-expressie van elk veld in een adaptief formulier weergeven door op het veld te tikken en te selecteren **[!UICONTROL View SOM Expression]**.

Met deze aangepaste fouthandler worden de velden in het aangepaste formulier geconverteerd `var som_map` naar de standaardindeling voor foutberichten. Hierdoor worden de berichten met validatiefouten in het adaptieve formulier op veldniveau weergegeven.

## Voeg douanemanager toe gebruikend de Actie van de Dienst van het Oproepen

Voer de volgende stappen uit om foutenmanager toe te voegen om een structuur van de douanefout in de standaardfoutenstructuur om te zetten gebruikend de Actie van de Dienst van de [Redacteur van de Regel](rule-editor.md) Invoke:

1. Open het aangepaste formulier in de ontwerpmodus, selecteer een formulierobject en tik op ![Regeleditor](assets/rule_editor_icon.png) om de regeleditor te openen.
1. Tik op **[!UICONTROL Create]**.
1. Maak een voorwaarde in het **[!UICONTROL When]** gedeelte van de regel. Zo wordt[WhenName of field] gewijzigd. Selecteer deze voorwaarde **[!UICONTROL is changed]** in de **[!UICONTROL Select State]** vervolgkeuzelijst.
1. Selecteer in de **[!UICONTROL Then]** sectie een optie in de **[!UICONTROL Invoke Service]** **[!UICONTROL Select Action]** vervolgkeuzelijst.
1. Selecteer een Post-service en de bijbehorende gegevensbindingen in de **[!UICONTROL Input]** sectie. Als u bijvoorbeeld de velden **Naam**, **ID** en **Status** in het adaptieve formulier wilt valideren, selecteert u een Post-service (pet) en selecteert u pet.name, pet.id en pet.status in de **[!UICONTROL Input]** sectie.

Als gevolg van deze regel worden de waarden die u opgeeft voor de velden **Naam**, **ID** en **Status** gevalideerd zodra het veld dat is gedefinieerd in stap 2 is gewijzigd en u het veld in het formulier verlaat.

1. Selecteer een optie in de **[!UICONTROL Code Editor]** vervolgkeuzelijst Modus selecteren.
1. Tik op **[!UICONTROL Edit Code]**.
1. Verwijder de volgende regel uit de bestaande code:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
   ```

1. Schrijf een regel om de aangepaste foutstructuur om te zetten in de standaardfoutstructuur en tik **[!UICONTROL Done]** om de regel op te slaan.
Voeg bijvoorbeeld de volgende voorbeeldcode aan het einde toe om een aangepaste foutstructuur om te zetten in de standaardfoutstructuur:

   ```javascript
   var errorHandler = function(jqXHR, data) {
   var som_map = {
       "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
       "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
       "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
   };
   
   
   var errorJson = {};
   errorJson.errors = [];
   
   if (data) {
       if (data.originMessage) {
           var errorData;
           try {
               errorData = JSON.parse(data.originMessage);
           } catch (err) {
               // not in json format
           }
   
           if (errorData) {
               Object.keys(errorData).forEach(function(key) {
                   var som_key = som_map[key];
                   if (som_key) {
                       var error = {};
                       error.somExpression = som_key;
                       error.errorMessage = errorData[key];
                       errorJson.errors.push(error);
                   }
               });
           }
           window.guideBridge.handleServerValidationError(errorJson);
       } else {
           window.guideBridge.handleServerValidationError(data);
       }
     }
   };
   
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   De `var som_map` SOM-expressie van de adaptieve formuliervelden die u in de standaardindeling wilt omzetten. U kunt de SOM-expressie van elk veld in een adaptief formulier weergeven door op het veld te tikken en een optie te selecteren in het **[!UICONTROL View SOM Expression]** menu **[!UICONTROL More Opions]** (..).

   Zorg ervoor dat u de volgende regel van de voorbeeldcode naar de aangepaste fouthandler kopieert:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   De API voor executeOperation bevat de parameters `null` en `errorHandler` parameters die zijn gebaseerd op de nieuwe aangepaste fouthandler.

   Met deze aangepaste fouthandler worden de velden in het aangepaste formulier geconverteerd `var som_map` naar de standaardindeling voor foutberichten. Hierdoor worden de berichten met validatiefouten in het adaptieve formulier op veldniveau weergegeven.