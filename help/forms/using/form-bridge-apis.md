---
title: Bridge-API's van formulier voor HTML5-formulieren
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

# Bridge-API&#39;s van formulier voor HTML5-formulieren {#form-bridge-apis-for-html-forms}

Met de API&#39;s van Form Bridge kunt u een communicatiekanaal openen tussen een op XFA gebaseerde HTML 5-formulieren en uw toepassingen. De vorm Bridge APIs verstrekt a **verbindt** API om de verbinding tot stand te brengen.

**verbind** API keurt een manager als argument goed. Nadat een verbinding tot stand is gebracht tussen op XFA gebaseerde HTML5-vorm en Form Bridge, wordt de greep aangeroepen.

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

## Beschikbaar formulier Bridge API  {#available-form-bridge-api-nbsp}

**getBridgeVersion ()**

Hiermee wordt het versienummer van de scriptbibliotheek geretourneerd

* **Input**: niets
* **Output**: Het aantal van de Versie van de bibliotheek Scripting
* **Fouten**: niets

**isConnected ()** controleert als de Staat van de Vorm is geïnitialiseerd

* **Input**: niets
* **Output**: **Waar** als de XFA Staat van de Vorm is geïnitialiseerd

* **Fouten**: niets

**verbindt (manager, context)** maakt een verbinding aan FormBridge en voert de functie uit nadat de verbinding wordt gemaakt en de Staat van de Vorm is geïnitialiseerd

* **Input**:

   * **manager**: Functie om uit te voeren nadat de Vorm Bridge wordt aangesloten
   * **context**: Het voorwerp waaraan de context (dit) van de *manager* functie wordt geplaatst.

* **Output**: niets
* **Fout**: niets

**getDataXML (opties)** keert de huidige vormgegevens in het Formaat van XML terug

* **Input:**

   * **opties:** Voorwerp van JavaScript die volgende eigenschappen bevatten:

      * **Fout**: De functie van de manager van de fout
      * **succes**: De handlerfunctie van het Succes. Deze functie wordt overgegaan een voorwerp dat XML in *gegevens* bezit bevat.
      * **context**: Het voorwerp waaraan de context (dit) van de *succes* functie wordt geplaatst
      * **validationChecker**: Functie aan vraag om bevestigingsfouten te controleren die van de server worden ontvangen. Validatiefunctie wordt doorgegeven aan een array met fouttekenreeksen.
      * **formState**: De JSON staat van de Vorm XFA waarvoor gegevens XML moet zijn teruggekeerd. Als deze optie niet is opgegeven, worden de gegevens-XML geretourneerd voor het momenteel gegenereerde formulier.

* **Output:** niets
* **Fout:** niets

**registerConfig (configName, config)** registreert gebruiker/portaal specifieke configuraties met FormBridge. Deze configuraties overschrijven de standaardconfiguraties. De gesteunde configuraties worden gespecificeerd in de config sectie.

* **Input:**

   * **configName:** Naam van de configuratie om met voeten te treden

      * **widgetConfig:** staat de gebruiker toe om het gebrek widgets in de vorm met douanewidgets met voeten te treden. De configuratie wordt als volgt overschreven:

        *formBridge.registerConfig (&quot;widgetConfig&quot;:{/&ast;configuration&ast;/})*

      * **pagingConfig:** staat de gebruiker toe om het standaardgedrag met voeten te treden om slechts de eerste pagina terug te geven. De configuratie wordt als volgt overschreven:

        *window.formBridge.registerConfig (&quot;pagingConfig&quot;:{pagingDisabled: &lt;true | false>, shrinkPageDisabled: &lt;true | false> }).*

      * **LoggingConfig:** staat de gebruiker toe om het niveau van het registreren met voeten te treden, het registreren voor een categorie onbruikbaar te maken, of om de logboekconsole te tonen of naar server te verzenden. De configuratie kan als volgt worden overschreven:

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

      * **SubmitServiceProxyConfig:** staat de gebruikers toe om voorlegging en de logger de volmachtsdiensten te registreren.

        ```javascript
        window.formBridge.registerConfig("submitServiceProxyConfig",
        {
        "submitServiceProxy" : "`<submitServiceProxy>`",
        "logServiceProxy": "`<logServiceProxy>`",
        "submitUrl" : "`<submitUrl>`"
        });
        ```

   * **config:** Waarde van de configuratie

* **Output:** Voorwerp dat originele waarde van de configuratie in *gegevens* bezit bevat.

* **Fout:** niets

**hideFields (fieldArray)** verbergt de gebieden waarvan de SOM uitdrukkingen in fieldArray worden verstrekt. Hiermee wordt de eigenschap presence van de opgegeven velden ingesteld op onzichtbaar

* **Input:**

   * **fieldArray:** Serie van Sommige uitdrukkingen voor de te verbergen gebieden

* **Output:** niets
* **Fout:** niets

**showFields (fieldArray)** toont de gebieden waarvan de SOM uitdrukkingen in fieldArray worden verstrekt. Hiermee wordt de aanwezigheidseigenschap van de opgegeven velden ingesteld op visible

* **Input:**

   * **fieldArray:** Serie van Sommige uitdrukkingen voor de te tonen gebieden

* **Output:** niets
* **Fout:** niets

**hideSubmitButtons ()** verbergt alle voorlegt knopen in de vorm

* **Input**: niets
* **Output**: niets
* **Fout**: Throws uitzondering als de Staat van de Vorm niet wordt geïnitialiseerd

**getFormState ()** keert JSON terug die de Staat van de Vorm vertegenwoordigt

* **Input:** niets
* **Output:** Voorwerp dat JSON bevat die de huidige Staat van de Vorm in *gegevens* bezit vertegenwoordigen.

* **Fout:** niets

**restoreFormState (opties)** herstelt de Staat van de Vorm van de verstrekte JSON staat in het optievoorwerp. De status wordt toegepast en succes- of fouthandlers worden aangeroepen nadat de bewerking is voltooid

* **Input:**

   * **Opties:** Voorwerp van JavaScript dat volgende eigenschappen bevat:

      * **Fout**: De functie van de manager van de fout
      * **succes**: De handlerfunctie van het Succes
      * **context**: Het voorwerp waaraan de context (dit) van de *succes* functie wordt geplaatst
      * **formState**: De staat JSON van de vorm. Het formulier wordt teruggezet naar de JSON-status.

* **Output:** niets
* **Fout:** niets

**setFocus (sommige)** plaatst nadruk op het gebied dat in de Som uitdrukking wordt gespecificeerd

* **Input:** Som uitdrukking van het gebied waarop om nadruk te plaatsen
* **Output:** niets
* **Fout:** gooit een uitzondering als er een onjuiste uitdrukking van het Som is

**setFieldValue (som, waarde)** plaatst de waarde van de gebieden voor de bepaalde uitdrukkingen van de Vorm

* **Input:**

   * **som:** Serie die enkele uitdrukkingen van het gebied bevat. The som expression to set value of the fields.
   * **waarde:** Serie die waarden bevatten die aan SOM uitdrukkingen beantwoorden die in a **worden verstrekt sommige** serie. Als het gegevenstype van de waarde niet hetzelfde is als het fieldType, wordt de waarde niet gewijzigd.

* **Output:** niets
* **Fout:** duikt een Uitzondering als er een onjuiste uitdrukking van het SOM is

**getFieldValue (som)** keert de waarde van de gebieden voor de bepaalde uitdrukkingen van de Vorm terug

* **Input:** Serie die enkele uitdrukkingen van de gebieden bevat waarvan waarde moet worden teruggewonnen
* **Output:** Voorwerp dat het resultaat als Serie in **gegevens** bezit bevat.

* **Fout:** niets

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

**getFieldProperties (som, bezit)** wint de lijst van waarden voor het bepaalde bezit van de gebieden terug die in Som uitdrukkingen worden gespecificeerd

* **Input:**

   * **som:** Serie die enkele uitdrukkingen voor de gebieden bevat
   * **bezit**: Naam van het bezit de waarvan waarde wordt vereist

* **Output:** Voorwerp dat het resultaat als Serie in *gegevens* bezit bevat

* **Fout:** niets

**setFieldProperties (som, bezit, waarden)** plaatst de waarde van het bepaalde bezit voor alle gebieden die in de Vormen uitdrukkingen worden gespecificeerd

* **Input:**

   * **som:** Serie die enkele uitdrukkingen van de gebieden bevat waarvan waarde moet worden geplaatst
   * **bezit**: Bezit de waarvan waarde moet worden geplaatst
   * **waarde:** Serie die waarden van het bepaalde bezit voor gebieden bevat die in de uitdrukkingen van Som worden gespecificeerd

* **Output:** niets
* **Fout:** niets

## Voorbeeld van gebruik van formulier-Bridge API {#sample-usage-of-form-bridge-api}

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
