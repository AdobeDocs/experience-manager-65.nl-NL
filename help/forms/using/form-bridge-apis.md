---
title: Form Bridge-API's voor HTML5-formulieren
description: Externe toepassingen maken via de FormBridge-API verbinding met het XFA Mobile-formulier. De API verzendt een FormBridgeInitialized-gebeurtenis in het bovenliggende venster.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: developer-reference
exl-id: b598ef47-49ff-4806-8cc7-4394aa068eaa
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# Form Bridge-API&#39;s voor HTML5-formulieren {#form-bridge-apis-for-html-forms}

Met de API&#39;s van Form Bridge kunt u een communicatiekanaal openen tussen een op XFA gebaseerde HTML5-formulieren en uw toepassingen. De API&#39;s van Form Bridge bevatten een **verbinden** API om de verbinding te maken.

De **verbinden** API accepteert een handler als argument. Nadat een verbinding tot stand is gebracht tussen een op XFA gebaseerd HTML5-formulier en een Form Bridge, wordt de greep aangeroepen.

U kunt de volgende voorbeeldcode gebruiken om de verbinding tot stand te brengen.

```javascript
// Example showing how to connect to FormBridge
window.addEventListener("FormBridgeInitialized",
                                function(event) {
                                    var fb = event.detail.formBridge;
                                    fb.connect(function() {
                                           //use form bridge functions
                         })
                            })
```

>[!NOTE]
>
>Zorg ervoor dat u een verbinding maakt voordat u het bestand formRuntime.jsp toevoegt.

## Beschikbare API voor Form Bridge  {#available-form-bridge-api-nbsp}

**getBridgeVersion()**

Hiermee wordt het versienummer van de scriptbibliotheek geretourneerd

* **Invoer**: Geen
* **Uitvoer**: Versienummer van de scriptbibliotheek
* **Fouten**: Geen

**isConnected()** Hiermee wordt gecontroleerd of de formulierstatus is geïnitialiseerd

* **Invoer**: Geen
* **Uitvoer**: **Waar** als de XFA-formulierstatus is geïnitialiseerd

* **Fouten**: Geen

**connect(handler, context)** Maakt een verbinding met FormBridge en voert de functie uit nadat de verbinding is gemaakt en de formulierstatus is geïnitialiseerd

* **Invoer**:

   * **handler**: Functie die moet worden uitgevoerd nadat Form Bridge is verbonden
   * **context**: Het object waarop de context (deze) van de component *handler* functie worden ingesteld.

* **Uitvoer**: Geen
* **Fout**: Geen

**getDataXML(opties)** Hiermee worden de huidige formuliergegevens in XML-indeling geretourneerd

* **Invoer:**

   * **opties:** JavaScript-object met de volgende eigenschappen:

      * **Fout**: functie Error Handler
      * **succes**: Handlerfunctie voor succesmeldingen. Deze functie wordt doorgegeven aan een object dat XML bevat in *data* eigenschap.
      * **context**: Het object waarop de context (deze) van de component *succes* function is set
      * **validationChecker**: Functie die moet worden aangeroepen om validatiefouten te controleren die van de server zijn ontvangen. Validatiefunctie wordt doorgegeven aan een array met fouttekenreeksen.
      * **formState**: De JSON-status van het XFA-formulier waarvoor gegevens-XML moet worden geretourneerd. Als deze optie niet is opgegeven, worden de gegevens-XML geretourneerd voor het momenteel gegenereerde formulier.

* **Uitvoer:** Geen
* **Fout:** Geen

**registerConfig(configName, config)** Registreert gebruikers-/poortspecifieke configuraties met FormBridge. Deze configuraties overschrijven de standaardconfiguraties. De gesteunde configuraties worden gespecificeerd in de config sectie.

* **Invoer:**

   * **configName:** Naam van de configuratie die moet worden overschreven

      * **widgetConfig:** Hiermee kan de gebruiker de standaardwidgets in het formulier overschrijven met aangepaste widgets. De configuratie wordt als volgt overschreven:

        *formBridge.registerConfig(&quot;widgetConfig&quot;:{/&amp;ast;configuration&amp;ast;/})*

      * **pagingConfig:** Hiermee kan de gebruiker het standaardgedrag negeren waarbij alleen de eerste pagina wordt weergegeven. De configuratie wordt als volgt overschreven:

        *window.formBridge.registerConfig(&quot;pagingConfig&quot;:{pagingDisabled: &lt;true false=&quot;&quot;>, krimpPageDisabled: &lt;true false=&quot;&quot;> }).*

      * **LoggingConfig:** Staat de gebruiker toe om het niveau van het registreren met voeten te treden, het registreren voor een categorie onbruikbaar te maken, of om de logboekconsole te tonen of naar server te verzenden. De configuratie kan als volgt worden overschreven:

     ```javascript
     formBridge.registerConfig{
       "LoggerConfig" : {
     {
     "on":`<true *| *false>`,
     "category":`<array of categories>`,
     "level":`<level of categories>`, "
     type":`<"console"/"server"/"both">`
     }
       }
     ```

      * **SubmitServiceProxyConfig:** Gebruikers toestaan verzendingen te registreren en proxyservices te registreren.

        ```javascript
        window.formBridge.registerConfig("submitServiceProxyConfig",
        {
        "submitServiceProxy" : "`<submitServiceProxy>`",
        "logServiceProxy": "`<logServiceProxy>`",
        "submitUrl" : "`<submitUrl>`"
        });
        ```

   * **config:** Waarde van de configuratie

* **Uitvoer:** Object met oorspronkelijke waarde van de configuratie in *data* eigenschap.

* **Fout:** Geen

**hideFields(fieldArray)** Hiermee worden de velden verborgen waarvan de SOM-expressies worden opgegeven in de fieldArray. Hiermee wordt de eigenschap presence van de opgegeven velden ingesteld op onzichtbaar

* **Invoer:**

   * **fieldArray:** Array van SOM-expressies voor de te verbergen velden

* **Uitvoer:** Geen
* **Fout:** Geen

**showFields(fieldArray)** Hiermee worden de velden weergegeven waarvan de SOM-expressies worden opgegeven in de fieldArray. Hiermee wordt de aanwezigheidseigenschap van de opgegeven velden ingesteld op visible

* **Invoer:**

   * **fieldArray:** Array van SOM-expressies voor de velden die moeten worden weergegeven

* **Uitvoer:** Geen
* **Fout:** Geen

**hideSubmitButtons()** Hiermee verbergt u alle verzendknoppen in het formulier

* **Invoer**: Geen
* **Uitvoer**: Geen
* **Fout**: Hiermee wordt een uitzondering gegenereerd als de formulierstatus niet is geïnitialiseerd

**getFormState()** Hiermee wordt de JSON geretourneerd die de formulierstatus vertegenwoordigt

* **Invoer:** Geen
* **Uitvoer:** Object met JSON dat de huidige formulierstatus in vertegenwoordigt *data* eigenschap.

* **Fout:** Geen

**restoreFormState(options)** Hiermee wordt de formulierstatus hersteld vanaf de opgegeven JSON-status in het object options. De status wordt toegepast en succes- of fouthandlers worden aangeroepen nadat de bewerking is voltooid

* **Invoer:**

   * **Opties:** JavaScript-object met de volgende eigenschappen:

      * **Fout**: functie Error Handler
      * **succes**: Handlerfunctie Succes
      * **context**: Het object waarop de context (deze) van de component *succes* function are set
      * **formState**: JSON-status van het formulier. Het formulier wordt teruggezet naar de JSON-status.

* **Uitvoer:** Geen
* **Fout:** Geen

**setFocus (som)** Hiermee wordt de focus ingesteld op het veld dat is opgegeven in de SOM-expressie

* **Invoer:** Enkele expressie van het veld waarop de focus moet worden ingesteld
* **Uitvoer:** Geen
* **Fout:** Genereert een uitzondering als er een onjuiste SOM-expressie is

**setFieldValue (som, value)** Hiermee wordt de waarde ingesteld van de velden voor de opgegeven SOM-expressies

* **Invoer:**

   * **som:** Array met enkele expressies van het veld. The som expression to set value of the fields.
   * **waarde:** Array die waarden bevat die overeenkomen met SOM-expressies die zijn opgegeven in een **som** array. Als het gegevenstype van de waarde niet hetzelfde is als het fieldType, wordt de waarde niet gewijzigd.

* **Uitvoer:** Geen
* **Fout:** Genereert een uitzondering als er een onjuiste SOM-expressie is

**getFieldValue (som)** Hiermee wordt de waarde van de velden voor de opgegeven SOM-expressies geretourneerd

* **Invoer:** Array met enkele expressies van velden waarvan de waarde moet worden opgehaald
* **Uitvoer:** Object dat het resultaat bevat als Array in **data** eigenschap.

* **Fout:** Geen

### Voorbeeld van getFieldValue()-API {#example-of-nbsp-getfieldvalue-api}

```JavaScript
var a =  formBridge.getFieldValue("xfa.form.form1.Subform1.TextField");
if(a.errors) {
    var err;
     while((err = a.getNextMessage()) != null)
               alert(a.message)
} else {
   alert(a.data[0])
}
```

**getFieldProperties(som, property)** Hiermee wordt de lijst met waarden opgehaald voor de opgegeven eigenschap van de velden die zijn opgegeven in SOM-expressies

* **Invoer:**

   * **som:** Array met SOM-expressies voor de velden
   * **eigenschap**: Naam van de eigenschap waarvan de waarde is vereist

* **Uitvoer:** Object dat het resultaat bevat als Array in *data* eigenschap

* **Fout:** Geen

**setFieldProperties(som, property, values)** Hiermee wordt de waarde van de opgegeven eigenschap ingesteld voor alle velden die in de SOM-expressies zijn opgegeven

* **Invoer:**

   * **som:** Array met enkele expressies van velden waarvan de waarde moet worden ingesteld
   * **eigenschap**: Eigenschap waarvan de waarde moet worden ingesteld
   * **waarde:** Array met waarden van de opgegeven eigenschap voor velden die zijn opgegeven in SOM-expressies

* **Uitvoer:** Geen
* **Fout:** Geen

## Voorbeeld van gebruik van Form Bridge-API {#sample-usage-of-form-bridge-api}

```JavaScript
// Example 1: FormBridge.restoreFormState
  function loadFormState() {
    var suc = function(obj) {
             //success
            }
    var err = function(obj) {
           while(var t = obj.getNextMessage()) {
         $("#errorDiv").append("<div>"+t.message+"</div>");
           }
           }
        var _formState = // load form state from storage
    formBridge.restoreFormState({success:suc,error:err,formState:_formState}); // not passing a context means that this will be formBridge itself. Validation errors will be checked.
  }

//--------------------------------------------------------------------------------------------------

//Example 2: FormBridge.submitForm
  function SubmitForm() {
    var suc = function(obj) {
             var data = obj.data;
         // submit the data to a url;
            }
    var err = function(obj) {
           while(var t = obj.getNextMessage()) {
         $("#errorDiv").append("<div>"+t.message+"</div>");
           }
           }
    formBridge.submitForm({success:suc,error:err}); // not passing a context means that this will be formBridge itself. Validation errors will be checked.
  }
```
