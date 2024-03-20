---
title: Voeg een aangepaste fouthandler toe in Adaptive Forms op basis van Core Components for AEM Adaptive Forms
description: AEM Forms verstrekt out-of-the-box succes en foutenmanagers voor een vorm gebruikend het REST eindpunt dat wordt gevormd om de externe dienst aan te halen. U kunt een standaardfouthandler en een aangepaste fouthandler toevoegen aan een AEM adaptief formulier.
keywords: Voeg een manager van de douanefout toe, voeg een standaardfoutenmanager toe, voeg een foutenmanager in vorm toe, gebruik de toepassing roept dienst van de redacteur om een douanefoutenmanager toe te voegen, regel redacteur te vormen om een manager van de douanefout toe te voegen, douanefoutafhandeling toe gebruikend regelredacteur
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 2118d77f-1314-48f1-88e3-e27dd8e9f17b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2251'
ht-degree: 0%

---

# Fouthandlers in Adaptive Forms (Core Components) {#error-handlers-in-adaptive-form}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/add-custom-error-handler-adaptive-forms-core-components.html) |
| AEM 6,5 | Dit artikel |

AEM Forms biedt offline succeshandlers en foutafhandelaars voor het verzenden van formulieren. Het biedt ook functie om functies van fouthandlers aan te passen. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een externe dienst gebruikend APIs wordt aangehaald, worden de gegevens overgebracht naar de server voor bevestiging, die een antwoord op de cliënt met informatie over het succes of de foutengebeurtenis voor de voorlegging terugkeert. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren. Met een fouthandler kunt u fouten of validatieproblemen die zijn opgetreden, beheren en weergeven.

![fout handler-workflow voor meer informatie over het toevoegen van een aangepaste fouthandler in formulieren](/help/forms/using/assets/error-handler-workflow.png)

De adaptieve Vorm bevestigt de input die u op gebieden verstrekt die op vooraf ingestelde bevestigingscriteria en controles op diverse fouten wordt gebaseerd door het REST eindpunt wordt gevormd om de externe dienst aan te halen. U kunt de validatiecriteria instellen op basis van de gegevensbron die u gebruikt met het adaptieve formulier. Als u bijvoorbeeld RESTful-webservices gebruikt als gegevensbron, kunt u de validatiecriteria definiëren in een Swagger-definitiebestand.

Als de invoerwaarden aan de validatiecriteria voldoen, worden de waarden naar de andere gegevensbron verzonden, geeft het adaptieve formulier een foutbericht weer met behulp van een fouthandler. Net als bij deze aanpak worden adaptieve Forms geïntegreerd met aangepaste fouthandlers voor het uitvoeren van gegevensvalidaties. Als de invoerwaarden niet voldoen aan de validatiecriteria, worden de foutberichten weergegeven op veldniveau in het adaptieve formulier. Dit gebeurt wanneer het foutbericht van de validatie dat door de server wordt geretourneerd, de standaardberichtindeling heeft.


## Gebruikt fouthandlers {#uses-of-error-handler}

Fouthandlers worden voor verschillende doeleinden gebruikt. Enkele toepassingen van de functies van de foutenmanager zijn hieronder vermeld:

* **Validatie uitvoeren**: De foutafhandeling begint met het valideren van gebruikersinvoer op basis van vooraf gedefinieerde regels of criteria. Wanneer gebruikers een adaptief formulier invullen, valideert de fouthandler de invoer om ervoor te zorgen dat deze voldoet aan de vereiste indeling, lengte of andere beperkingen.

* **Feedback in real time geven**: Wanneer een fout wordt gedetecteerd, geeft de fouthandler direct feedback aan de gebruiker, zoals inline foutberichten onder de bijbehorende formuliervelden. Met deze feedback kunnen gebruikers fouten opsporen en corrigeren zonder het formulier te hoeven verzenden en op een reactie te moeten wachten.


* **Foutberichten weergeven**: Wanneer bij het verzenden van een adaptief formulier een validatiefout optreedt, geeft de fouthandler een geschikt foutbericht weer. De foutberichten moeten duidelijk, beknopt en nauwkeurig zijn en de specifieke velden moeten benadrukken die aandacht behoeven.

* **Hiermee wordt het onjuiste veld gemarkeerd**: Om de aandacht van de gebruiker op de specifieke onjuiste gebieden te trekken, benadrukt de foutenmanager of onderscheidt visueel de overeenkomstige gebieden. Dit wordt uitgevoerd door de achtergrondkleur te wijzigen, een pictogram of rand toe te voegen of door andere visuele aanwijzingen die gebruikers helpen de fouten snel te vinden en aan te pakken.


## Opmaak van reactie fout/fout {#failure-response-format}

In een adaptief formulier worden de fouten in een veld weergegeven als de foutberichten voor servervalidatie de volgende standaardindeling hebben.
De onderstaande code illustreert de bestaande structuur van de mislukkingsreactie:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]
        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
    }
```


Waarbij:

* `errorCausedBy` beschrijft de reden voor mislukking.
* `errors` vermelden de gekwalificeerde veldnaam van de velden waarvoor de validatiecriteria niet zijn nageleefd, samen met het foutbericht voor de validatie.
* `originCode` veld toegevoegd door AEM en bevat de http-statuscode geretourneerd door de externe service.
* `originMessage` veld toegevoegd door AEM en bevat de onbewerkte foutgegevens die door de externe service worden geretourneerd.

Met de verbeteringen in eigenschappen en verdere updates in de versies van AEM Forms, veranderde de bestaande structuur van de mislukkingsreactie in nieuw formaat dat op RFC7807 wordt gebaseerd, die achterwaarts compatibel met de bestaande structuur van de mislukkingsreactie is:

```javascript
    {
        "type": "SERVER_SIDE_VALIDATION/FORM_SUBMISSION/SERVICE_INVOCATION/FAILURE/VALIDATION_ERROR" (required)
        "title": "Server side validation failed/Third party service invocation failed" (optional)
        "detail": "" (optional)
        "instance": "" (optional)
        "validationErrors" : [ (required)
            {
                "fieldName":"<qualified fieldname of the field whose data sent is invalid>",
                "dataRef":<JSONPath (or XPath) of the data element which is invalid>
                "details": ["Error Message(s) for the field"] (required)
    
            }
        ],
        "originCode": <Origin http status code> (optional - if there is SERVER_SIDE_VALIDATION)
        "originMessage" : "<unstructured error message returned by service>" (optional - if there is SERVER_SIDE_VALIDATION)
    }
```


>[!NOTE]
>
> * Zorg ervoor dat de structuur van de foutreactie het volgende bevat: **fieldName** of **dataRef**.
> * Zorg ervoor dat de **ContentType** header is **application/problem+json**.

Waarbij:
* `type (required)` geeft het type fout aan. Dit kan een van de volgende waarden zijn:
   * `SERVER_SIDE_VALIDATION` Hiermee wordt een fout aangegeven als gevolg van validatie aan de serverzijde.
   * `FORM_SUBMISSION` Hiermee wordt een fout aangegeven tijdens het verzenden van het formulier
   * `SERVICE_INVOCATION` Hiermee wordt een fout aangegeven tijdens een aanroep van een externe service.
   * `FAILURE` geeft een algemene fout aan.
   * `VALIDATION_ERROR` Hiermee wordt een fout aangegeven als gevolg van een validatiefout.

* `title (optional)` bevat een titel of korte beschrijving van de fout.
* `detail (optional)` indien nodig aanvullende details over de fout geven.
* `instance (optional)` vertegenwoordigt een instantie of een herkenningsteken verbonden aan de mislukking en helpt in het volgen van of het identificeren van het specifieke voorkomen van de mislukking.
* `validationErrors (required)` bevat informatie over validatiefouten. Het bevat de volgende velden:
   * `fieldname` Hiermee wordt de gekwalificeerde veldnaam vermeld van de velden waarvoor de validatiecriteria zijn mislukt.
   * `dataRef` vertegenwoordigt het JSON-pad of XPath van de velden waarvoor de validatie is mislukt.
   * `details` bevat het foutbericht met het onjuiste veld.
* `originCode (optional)` veld toegevoegd door AEM en bevat de http-statuscode geretourneerd door de externe service
* `originMessage (optional)` veld toegevoegd door AEM en bevat de onbewerkte foutgegevens die door de externe service worden geretourneerd.

### Sample-indeling voor foutreactie {#sample-error-response-format}

Enkele opties om de foutreacties weer te geven zijn:

+++  Gebaseerd op de eigenschap Adaptive Form fieldName


* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
          {
              "type": "VALIDATION_ERROR",
              "validationErrors": [
              {
              "fieldName": "$form.PetId",
              "dataRef": "",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
          ]
          }
          ]}
  ```


+++


+++ Gebaseerd op de eigenschap Adaptive Form dataRef

* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
      {
          "type": "VALIDATION_ERROR",
          "validationErrors": [
          {
              "fieldName": "",
              "dataRef": "$.Pet.id",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
              ]
              }
      ]}
  ```

+++

## Vereisten {#prerequisites}

Voordat u de fouthandler in een Adaptive Forms gebruikt:

* [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](enable-adaptive-forms-core-components.md).
* Basiskennis voor [een aangepaste functie maken](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/adaptive-forms/custom-functions-aem-forms.html?lang=en#:~:text=AEM%20Forms%206.5%20introduced%20the,use%20them%20across%20multiple%20forms.).
* Installeer de nieuwste versie van [Apache Maven](https://maven.apache.org/download.cgi).

## Fouthandler toevoegen met gebruik van de Regel-editor {#add-error-handler-using-rule-editor}

Met de [Invoke-service van de Rule Editor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) , definieert u de validatiecriteria op basis van de gegevensbron die u gebruikt met het adaptieve formulier. Als u RESTful-webservices als gegevensbron gebruikt, kunt u de validatiecriteria definiëren in een bestand met definities van de Swagger. Door de functies van de foutenmanager en de Redacteur van de Regel in Aangepast Forms te gebruiken, kunt u fout behandeling effectief beheren en aanpassen. U bepaalt de voorwaarden gebruikend de Redacteur van de Regel en vormt de gewenste acties die moeten worden uitgevoerd wanneer de regel wordt teweeggebracht. Met Aangepast formulier worden de invoer die u invoert in velden gevalideerd op basis van vooraf ingestelde validatiecriteria. Als de invoerwaarden niet voldoen aan de validatiecriteria, worden de foutberichten in een adaptief formulier weergegeven op veldniveau.

>[!NOTE]
>
> * Om foutenmanagers met de Invoke van de Redacteur van de Regel de dienstactie te gebruiken, vorm Aangepast Forms met een model van vormgegevens.
> * Er wordt een standaardfouthandler geboden voor het weergeven van foutberichten op velden als de foutreactie in het standaardschema staat. U kunt de standaardfoutenmanager van de functie van de douaneformmanager ook roepen.

Gebruikend de Redacteur van de Regel, kunt u:

* [Standaardfouthandlerfunctie toevoegen](#add-default-errror-handler)
* [Aangepaste fouthandlerfunctie toevoegen](#add-custom-errror-handler)


### Standaardfouthandlerfunctie toevoegen {#add-default-errror-handler}

Een standaardfouthandler wordt ondersteund voor het weergeven van foutberichten in velden als de foutreactie in het standaardschema of bij een validatiefout op de server staat.
Als u wilt weten hoe u een standaardfouthandler gebruikt met de functie [Invoke-service van de Rule Editor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) handeling, neem een voorbeeld van een eenvoudig adaptief formulier met twee velden. **Huisdier-id** en **Naam huisdier** en gebruik een standaardfouthandler bij de **Huisdier-id** gebied om diverse fouten te controleren die door het REST eindpunt zijn teruggekeerd dat wordt gevormd om een externe dienst, bijvoorbeeld aan te halen, `200 - OK`,`404 - Not Found`, `400 - Bad Request`. Om een standaardfoutenmanager toe te voegen gebruikend de Actie van de Dienst van de Redacteur van de Regel Invoke, voer de volgende stappen uit:

1. Open een adaptief formulier in de ontwerpmodus, selecteer een formulieronderdeel en selecteer **[!UICONTROL Rule Editor]** om de regeleditor te openen.
1. Selecteren **[!UICONTROL Create]**.
1. Een voorwaarde maken in het dialoogvenster **Wanneer** van de regel. Bijvoorbeeld: **Wanneer[Naam van veld Dierenid]** is gewijzigd. Selecteren wordt gewijzigd in het menu **Frame selecteren** vervolgkeuzelijst.
1. In de **Vervolgens** sectie, selecteert u **[!UICONTROL Invoke Service]** van de **Handeling selecteren** vervolgkeuzelijst.
1. Selecteer een **Postservice** en de overeenkomstige gegevensbindingen van de **Invoer** sectie. Bijvoorbeeld om te bevestigen **Huisdier-id** selecteert u een **Postservice** als **GET /pet/{petId}** en selecteert u **Huisdier-id** in de **Invoer** sectie.
1. Selecteer de gegevensbindingen in het menu **Uitvoer** sectie. Selecteren **Naam huisdier** in de **Uitvoer** sectie.
1. Selecteren **[!UICONTROL Default Error Handler]** van de **Fouthandler** sectie.
1. Klik op **[!UICONTROL Done]**.

![een standaardfouthandler toevoegen voor veldvalidatiecontroles in een formulier](/help/forms/using/assets/default-error-handler.png)

Als resultaat van deze regel worden de waarden waarvoor u invoert **Huisdier-id** controleert validatie voor **Naam huisdier** het gebruiken van externe dienst die door het eindpunt van REST wordt aangehaald. Als de validatiecriteria op basis van de gegevensbron mislukken, worden de foutberichten weergegeven op veldniveau.

![Geef het standaardfoutbericht weer wanneer u een standaardfouthandler in een formulier toevoegt voor de verwerking van foutreacties](/help/forms/using/assets/default-error-message.png)

### Aangepaste fouthandlerfunctie toevoegen {#add-custom-errror-handler}

U kunt een aangepaste fouthandlerfunctie toevoegen om een aantal van de volgende handelingen uit te voeren:

* foutreacties verwerken die niet-standaard of standaardfoutreacties gebruiken. Het is belangrijk om op te merken dat deze niet-standaardfoutreacties niet voldoen aan de [standaardschema van foutreacties](#failure-response-format).
* verzendt analytische gebeurtenissen naar alle analytische platforms. Bijvoorbeeld Adobe Analytics.
* modaal dialoogvenster weergeven met foutberichten.

Naast de genoemde acties, kunnen de managers van de douanefout worden gebruikt om aangepaste functies uit te voeren die aan specifieke gebruikersvereisten voldoen.

De manager van de douanefout is een functie (de Bibliotheek van de Cliënt) die wordt ontworpen om aan fouten te antwoorden die door de externe dienst zijn teruggekeerd en een aangepaste reactie aan eind te leveren - gebruikers. Elke clientbibliotheek met annotatie `@errorHandler` wordt beschouwd als een aangepaste fouthandlerfunctie. Deze aantekening helpt de functie van de foutenmanager te identificeren die in `.js` bestand.

Als u wilt weten hoe u een aangepaste fouthandler maakt en gebruikt met de functie [De Invoke-service van de Rule Editor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) handeling, laten we een voorbeeld nemen van Adaptief formulier met twee velden. **Huisdier-id** en **Naam huisdier** en gebruik een aangepaste fouthandler bij het **Huisdier-id** gebied om diverse fouten te controleren die door het REST eindpunt zijn teruggekeerd dat wordt gevormd om een externe dienst, bijvoorbeeld aan te halen, `200 - OK`,`404 - Not Found`, `400 - Bad Request`.

Voer de volgende stappen uit om een aangepaste fouthandler toe te voegen en te gebruiken in een adaptief formulier:

1. [Een aangepaste fouthandler maken](#create-custom-error-message)
1. [Gebruik de Redacteur van de Regel om de manager van de douanefout te vormen](#use-custom-error-handler)

#### 1. Een aangepaste fouthandler maken {#create-custom-error-message}

Voer de volgende stappen uit om een aangepaste foutfunctie te maken:

1. Aanmelden `http://server:port/crx/de/index.jsp#`.
1. Een map maken onder de `/apps` map. Maak bijvoorbeeld een map met de naam `experience-league`.
1. Sla uw wijzigingen op.
1. Ga naar de gemaakte map en maak een knooppunt van het type `cq:ClientLibraryFolder` als `clientlibs`.
1. Naar het nieuwe ontwerp navigeren `clientlibs` en voeg de `allowProxy` en `categories` eigenschappen:

   ![Eigenschappen van Custom Library-knooppunten](/help/forms/using/assets/customlibrary-properties.png)

   >[!NOTE]
   >
   > U kunt elke naam opgeven in plaats van `customfunctionsdemo`.

1. Sla uw wijzigingen op.

1. Een map maken met de naam `js` onder de `clientlibs` map.
1. Een JavaScript-bestand met de naam `functions.js` onder de `js` map
1. Een bestand maken met de naam `js.txt` onder de `clientlibs` map.
1. Sla uw wijzigingen op.
De gemaakte mapstructuur ziet er als volgt uit:

   ![Map-structuur voor clientbibliotheek gemaakt](/help/forms/using/assets/customclientlibrary_folderstructure.png)
1. Dubbelklik op de knop `functions.js` te openen. Het bestand bevat de code voor aangepaste fouthandler.
Voeg de volgende code aan het dossier JavaScript toe om de reactie en kopballen te tonen, die van het de diensteindpunt van REST, in de browser console worden ontvangen.

   ```javascript
       /** 
       Custom Error handler
       * @name customErrorHandler Custom Error Handler Function
       * @errorHandler
       */
       function customErrorHandler(response, headers, globals)
       {
           console.log("Custom Error Handler processing start...");
           console.log("response:"+JSON.stringify(response));
           console.log("headers:"+JSON.stringify(headers));
           alert("CustomErrorHandler - Please enter valid PetId.")
           globals.invoke('defaultErrorHandler',response, headers)
           console.log("Custom Error Handler processing end...");
       }
   ```

   Om de standaardfoutenmanager van uw manager van de douanefout te roepen, wordt de volgende lijn van de steekproefcode gebruikt:
   `globals.invoke('defaultErrorHandler',response, headers) `

1. Opslaan `function.js`.
1. Navigeren naar `js.txt` en voeg de volgende code toe:

   ```javascript
       #base=js
       functions.js
   ```

1. Sla de `js.txt` bestand.

Nu, begrijpen hoe te om een manager van de douanefout te vormen en te gebruiken gebruikend de Invoke van de Redacteur van de Regel dienst in AEM Forms.

#### 2. Gebruik de Redacteur van de Regel om de manager van de douanefout te vormen {#use-custom-error-handler}

Voordat u de aangepaste fouthandler implementeert in een adaptief formulier, moet u ervoor zorgen dat de naam van de clientbibliotheek in het dialoogvenster **[!UICONTROL Client Library Category]** wordt uitgelijnd met de naam die is opgegeven in de optie Categorieën van het dialoogvenster `.content.xml` bestand.

![De naam van de clientbibliotheek toevoegen in de configuratie van de adaptieve formuliercontainer](/help/forms/using/assets/client-library-category-name-core-component.png)

In dit geval wordt de naam van de clientbibliotheek opgegeven zoals `customfunctionsdemo` in de `.content.xml` bestand.

Als u een aangepaste fouthandler wilt gebruiken met de **[!UICONTROL Rule Editor's Invoke Service]** handeling:

1. Open een adaptief formulier in de ontwerpmodus, selecteer een formulieronderdeel en selecteer **[!UICONTROL Rule Editor]** om de regeleditor te openen.
1. Selecteren **[!UICONTROL Create]**.
1. Een voorwaarde maken in het dialoogvenster **Wanneer** van de regel. Bijvoorbeeld wanneer **[Naam van veld Dierenid]** is gewijzigd, selecteert u **is gewijzigd** van de **Frame selecteren** vervolgkeuzelijst.
1. In de **Vervolgens** sectie, selecteert u **[!UICONTROL Invoke Service]** van de **Handeling selecteren** vervolgkeuzelijst.
1. Selecteer een **Postservice** en de overeenkomstige gegevensbindingen van de **Invoer** sectie. Bijvoorbeeld om te bevestigen **Huisdier-id** selecteert u een **Postservice** als **GET /pet/{petId}** en selecteert u **Huisdier-id** in de **Invoer** sectie.
1. Selecteer de gegevensbindingen in het menu **Uitvoer** sectie. Selecteer bijvoorbeeld **Naam huisdier** in de **Uitvoer** sectie.
1. Selecteren **[!UICONTROL Custom Error Handler]** van de **[!UICONTROL Error Handler]** sectie.
1. Klik op **[!UICONTROL Done]**.

![Aangepaste fouthandler toevoegen aan een formulier voor het verwerken van reacties op fouten](/help/forms/using/assets/custom-error-handler.png)

Als resultaat van deze regel worden de waarden waarvoor u invoert **Huisdier-id** controleert validatie voor **Naam huisdier** het gebruiken van externe dienst die door het eindpunt van REST wordt aangehaald. Als de validatiecriteria op basis van de gegevensbron mislukken, worden de foutberichten weergegeven op veldniveau.

![Voeg een aangepaste fouthandler toe aan een formulier voor het verwerken van reacties op fouten](/help/forms/using/assets/custom-error-handler-message-core-component.png)

Open de browser console en controleer de reactie en de kopbal, die van het de diensteindpunt van REST, voor het bericht van de bevestigingsfout worden ontvangen.

De aangepaste fouthandlerfunctie is verantwoordelijk voor het uitvoeren van aanvullende acties, zoals het weergeven van een modaal dialoogvenster of het verzenden van een analysegebeurtenis, op basis van de foutreactie. Een aangepaste fouthandlerfunctie biedt de flexibiliteit om foutafhandeling af te stemmen op de specifieke gebruikersvereisten.

## Zie ook {#see-also}

* [Een op zichzelf staand adaptief formulier voor kerncomponenten maken](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Stijlen of thema&#39;s maken voor uw formulieren](/help/forms/using/create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)
