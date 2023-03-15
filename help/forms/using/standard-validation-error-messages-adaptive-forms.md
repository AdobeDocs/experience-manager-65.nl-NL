---
title: Standaardvalidatiefoutenberichten voor adaptieve formulieren
seo-title: Standard validation error messages for adaptive forms
description: Transformeer de foutberichten voor validatie van adaptieve formulieren naar de standaardnotatie met behulp van aangepaste fouthandlers
seo-description: Transform the validation error messages for adaptive forms into standard format using custom error handlers
uuid: 0d1f9835-3e28-41d3-a3b1-e36d95384328
contentOwner: anujkapo
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
discoiquuid: ec062567-1c6b-497b-a1e7-1dbac2d60852
feature: Adaptive Forms
exl-id: 54a76d5c-d19b-4026-b71c-7b9e862874bc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 0%

---

# Standaardvalidatiefoutenberichten voor adaptieve formulieren {#standard-validation-error-messages}

Aangepaste formulieren valideren de invoer die u in velden opgeeft op basis van vooraf ingestelde validatiecriteria. De validatiecriteria verwijzen naar de aanvaardbare invoerwaarden voor velden in een adaptieve vorm. U kunt de validatiecriteria instellen op basis van de gegevensbron die u gebruikt bij het adaptieve formulier. Als u bijvoorbeeld RESTful-webservices gebruikt als gegevensbron, kunt u de validatiecriteria definiëren in een Swagger-definitiebestand.

Als de invoerwaarden aan de validatiecriteria voldoen, worden de waarden naar de gegevensbron verzonden. Anders wordt een foutbericht weergegeven in het adaptieve formulier.

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

1. Selecteer in de modus Aangepast formulier voor het schrijven van programmacode het object Form Container en tik op ![adaptieve formuliereigenschappen](assets/configure_icon.png) om de eigenschappen te openen.
1. In de **[!UICONTROL Submission]** eigenschappensectie, inschakelen **[!UICONTROL Use asynchronous submission]**.
1. Selecteren **[!UICONTROL Revalidate on server]** om de waarden van de invoervelden op de server vóór verzending te valideren.
1. Selecteer de handeling Verzenden:

   * Selecteren **[!UICONTROL Submit using Form Data Model]** en selecteer het juiste gegevensmodel als u RESTful-webservice gebruikt [formuliergegevensmodel](work-with-form-data-model.md) als gegevensbron.
   * Selecteren **[!UICONTROL Submit to REST endpoint]** en de **[!UICONTROL Redirect URL/Path]**, als u RESTful Webdiensten als gegevensbron gebruikt.

   ![adaptieve eigenschappen voor formulierverzending](assets/af_submission_properties.png)

1. Tikken ![Opslaan](assets/save_icon.png) om de eigenschappen op te slaan.

### Aangepaste fouthandler toevoegen bij het verzenden van aangepaste formulieren {#add-custom-error-handler-af-submission}

AEM Forms biedt offline succeshandlers en foutafhandelaars voor het verzenden van formulieren. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een formulier wordt verzonden, worden de gegevens voor validatie naar de server verzonden, die een reactie op de client retourneert met informatie over de gebeurtenis &#39;success&#39; of &#39;error&#39; voor de verzending. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren.

Voer de volgende stappen uit om aangepaste fouthandler toe te voegen bij het verzenden van aangepaste formulieren:

1. Open het adaptieve formulier in de ontwerpmodus, selecteer een willekeurig formulierobject en tik op <!--![Rule Editor](assets/af_edit_rules.png)--> om de regeleditor te openen.
1. Selecteren **[!UICONTROL Form]** in de structuur Formulierobjecten en tik op **[!UICONTROL Create]**.
1. Selecteren **[!UICONTROL Error in Submission]** in de vervolgkeuzelijst Gebeurtenis.
1. Schrijf een regel om de aangepaste foutstructuur om te zetten in de standaardfoutstructuur en tik op **[!UICONTROL Done]** om de regel op te slaan.

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

De `var som_map` Hiermee geeft u de SOM-expressie weer van de adaptieve formuliervelden die u wilt transformeren in de standaardindeling. U kunt de SOM-expressie van elk veld in een adaptief formulier weergeven door op het veld te tikken en **[!UICONTROL View SOM Expression]**.

Met deze aangepaste fouthandler worden de velden in het aangepaste formulier geconverteerd naar `var som_map` naar de standaardindeling voor foutberichten. Hierdoor worden de berichten met validatiefouten in het adaptieve formulier op veldniveau weergegeven.

## Voeg douanemanager toe gebruikend de Actie van de Dienst van het Oproepen

Voer de volgende stappen uit om fouthandler toe te voegen voor het omzetten van een aangepaste foutstructuur in de standaardfoutstructuur met behulp van [Regeleditor](rule-editor.md) Actie Service aanroepen:

1. Open het adaptieve formulier in de ontwerpmodus, selecteer een willekeurig formulierobject en tik op ![Regeleditor](assets/rule_editor_icon.png) om de regeleditor te openen.
1. Tik op **[!UICONTROL Create]**.
1. Een voorwaarde maken in het dialoogvenster **[!UICONTROL When]** van de regel. Als[Naam van veld] is gewijzigd. Selecteren **[!UICONTROL is changed]** van de **[!UICONTROL Select State]** vervolgkeuzelijst om deze voorwaarde te bereiken.
1. In de **[!UICONTROL Then]** sectie, selecteert u **[!UICONTROL Invoke Service]** van de **[!UICONTROL Select Action]** vervolgkeuzelijst.
1. Selecteer een postservice en de bijbehorende gegevensbindingen in het menu **[!UICONTROL Input]** sectie. Als u bijvoorbeeld wilt valideren **Naam**, **ID**, en **Status** in het adaptieve formulier selecteert u een Post-service (pet) en selecteert u pet.name, pet.id en pet.status in het dialoogvenster **[!UICONTROL Input]** sectie.

Als resultaat van deze regel worden de waarden opgegeven waarvoor u **Naam**, **ID**, en **Status** velden worden gevalideerd, zodra het in stap 2 gedefinieerde veld wordt gewijzigd en u het veld in het formulier verlaat.

1. Selecteren **[!UICONTROL Code Editor]** in de vervolgkeuzelijst Modus selecteren.
1. Tik op **[!UICONTROL Edit Code]**.
1. Verwijder de volgende regel uit de bestaande code:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
   ```

1. Schrijf een regel om de aangepaste foutstructuur om te zetten in de standaardfoutstructuur en tik op **[!UICONTROL Done]** om de regel op te slaan.
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

   De `var som_map` Hiermee geeft u de SOM-expressie weer van de adaptieve formuliervelden die u wilt transformeren in de standaardindeling. U kunt de SOM-expressie van elk veld in een adaptief formulier weergeven door op het veld te tikken en **[!UICONTROL View SOM Expression]** van **[!UICONTROL More Opions]** (...).

   Zorg ervoor dat u de volgende regel van de voorbeeldcode naar de aangepaste fouthandler kopieert:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   De API van executeOperation bevat de `null` en `errorHandler` parameters die zijn gebaseerd op de nieuwe aangepaste fouthandler.

   Met deze aangepaste fouthandler worden de velden in het aangepaste formulier geconverteerd naar `var som_map` naar de standaardindeling voor foutberichten. Hierdoor worden de berichten met validatiefouten in het adaptieve formulier op veldniveau weergegeven.
