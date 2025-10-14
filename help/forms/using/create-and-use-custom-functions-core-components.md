---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
content-type: reference
feature: Adaptive Forms, Core Components
role: Admin, User, Developer
exl-id: 00073e3a-f1b5-4c42-9fea-4a14b8a22c81
source-git-commit: 7f1283898cbeebdedb7bdea6f0a8d9db567617ee
workflow-type: tm+mt
source-wordcount: '3377'
ht-degree: 0%

---

# Aangepaste functies in Adaptive Forms Core Components

In dit artikel wordt beschreven hoe u aangepaste functies maakt met de nieuwste adaptieve Form Core-component, die de nieuwste functies heeft, zoals:

* Caching, functie voor aangepaste functies
* Algemene bereikobjecten en veldobjecten ondersteunen aangepaste functies
* Ondersteuning voor moderne JavaScript-functies, zoals verlaat- en pijlfuncties (ES10-ondersteuning)

Zorg ervoor om de [&#x200B; recentste vormversie &#x200B;](https://github.com/adobe/aem-core-forms-components/tree/release/650) op uw milieu van de Component van de Kern van AEM Forms te plaatsen om de recentste eigenschappen in de Functies van de Douane te gebruiken. </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | Dit artikel |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/create-and-use-custom-functions) |

## Inleiding

AEM Forms 6.5 omvat de functies van JavaScript die u toestaan om complexe bedrijfsregels te bepalen door de regeleditor te gebruiken. Hoewel AEM Forms verschillende aangepaste functies biedt die niet in de box kunnen worden gebruikt, vereisen veel gebruiksgevallen het definiëren van uw eigen aangepaste functies die in meerdere formulieren kunnen worden gebruikt. Deze aangepaste functies verbeteren de mogelijkheden van formulieren door de bewerking en verwerking van ingevoerde gegevens in staat te stellen aan specifieke vereisten te voldoen. Bovendien kunnen hiermee het formuliergedrag dynamisch worden gewijzigd op basis van de vooraf gedefinieerde criteria.

### Gebruik van aangepaste functies {#uses-of-custom-function}

De voordelen van het gebruik van Aangepaste functies in Aangepaste Forms Core-componenten zijn:


* **het Leiden gegevens**: De functies van de douane leiden en verwerken gegevens ingegaan in de vormengebieden.
* **Verwerking van gegevens**: De functies van de douane verwerken gegevens ingegaan in de vormgebieden.
* **Bevestiging van gegevens**: De functies van de douane laten u toe om douanecontroles op vorminput uit te voeren en gespecificeerde foutenmeldingen te verstrekken.
* **Dynamisch gedrag**: De functies van de douane staan u toe om het dynamische gedrag van uw vormen te controleren die op specifieke voorwaarden worden gebaseerd. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt douanefuncties gebruiken om met externe APIs of de diensten te integreren. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

Aangepaste functies zijn in wezen clientbibliotheken die in het JavaScript-bestand worden toegevoegd. Zodra u een Functie van de Douane creeert, wordt het beschikbaar in de regelredacteur voor selectie door de gebruiker in een Aangepast Vorm. De douanefuncties worden geïdentificeerd door de aantekeningen van JavaScript in de regelredacteur.

### Ondersteunde JavaScript-annotaties voor aangepaste functies {#js-annotations}

**de aantekeningen van JavaScript verstrekken meta-gegevens voor code van JavaScript**. Het bevat opmerkingen die beginnen met specifieke symbolen, bijvoorbeeld `/**` en `@` . De annotaties bevatten belangrijke informatie over functies, variabelen en andere elementen in de code. Het adaptieve formulier ondersteunt de volgende JavaScript-annotaties voor aangepaste functies:

#### Naam

De **Naam** wordt gebruikt om de douanefunctie in de regelredacteur van een Adaptieve vorm te identificeren. De volgende syntaxis wordt gebruikt om een Functie van de Douane te noemen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`

>[!NOTE]
>`[functionName]` is de naam van de functie. Spaties zijn niet toegestaan.
>`<Function Name>` is de weergavenaam van de functie in de regeleditor van Adaptive Forms.
>Als de functienaam identiek is aan de naam van de functie zelf, kunt u `[functionName]` weglaten uit de syntaxis.

#### Parameter

De **Parameter** is een lijst van argumenten die door douanefuncties worden gebruikt. Een functie kan meerdere parameters ondersteunen. De volgende syntaxis wordt gebruikt om een parameter in een douanefunctie te bepalen:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`

  `{type}` staat voor het parametertype. De toegestane parametertypen zijn:

   * tekenreeks: vertegenwoordigt één tekenreekswaarde.
   * getal: vertegenwoordigt één numerieke waarde.
   * boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
   * string []: Geeft een array van tekenreekswaarden aan.
   * getal []: vertegenwoordigt een array van numerieke waarden.
   * boolean [] : vertegenwoordigt een array van Booleaanse waarden.
   * date: vertegenwoordigt één datumwaarde.
   * date []: Vertegenwoordigt een serie van datumwaarden.
   * array: vertegenwoordigt een algemene array met waarden van verschillende typen.
   * object: vertegenwoordigt een formulierobject dat aan een aangepaste functie wordt doorgegeven in plaats van dat de waarde rechtstreeks wordt doorgegeven.
   * bereik: vertegenwoordigt het globals object, dat alleen-lezen variabelen bevat, zoals formulierinstanties, doelveldinstanties en methoden voor het uitvoeren van formulierwijzigingen binnen de aangepaste functies. Deze wordt gedeclareerd als de laatste parameter in de JavaScript-annotaties en is niet zichtbaar voor de regeleditor van een adaptief formulier. De bereikparameter benadert het object van het formulier of de component om de regel of gebeurtenis te activeren die vereist is voor formulierverwerking. Voor verdere informatie over het voorwerp van Globals en hoe te om het te gebruiken, [&#x200B; klik hier &#x200B;](/help/forms/using/create-and-use-custom-functions-core-components.md#field-and-global-scope-objects-in-custom-functions-support-field-and-global-objects)

Het type van Parameter is **niet case-sensitive** en de ruimten worden niet toegestaan in de parameternaam.

`<Parameter Description>` bevat details over het doel van de parameter. Het kan meerdere woorden hebben.

<!--

**Optional Parameters**
By default, all parameters are mandatory. You can define a parameter as optional by either adding `=` after the parameter type or enclosing the parameter name in `[]`. Parameters defined as optional in JavaScript annotations are displayed as optional in the rule editor.
To define a variable as an optional parameter, you can use the any of the following syntaxes:
  
* `@param {type=} Input1`

In the above line of code, `Input1` is an optional parameter without any default value. To declare optional parameter with default value:

`@param {string=<value>} input1`
        
`input1` as an optional parameter with the default value set to `value`. 

* `@param {type} [Input1]`

In the above line of code, `Input1` is an optional parameter without any default value. To declare optional parameter with default value:

`@param {array} [input1=<value>]`

    `input1` is an optional parameter of array type with the default value set to `value`. 
    Ensure that the parameter type is enclosed in curly brackets {} and the parameter name is enclosed in square brackets []. 

Consider the following code snippet, where input2 is defined as an optional parameter:

```javascript

        /**
         * optional parameter function
         * @name OptionalParameterFunction
         * @param {string} input1 
         * @param {string=} input2 
         * @return {string}
        */
        function OptionalParameterFunction(input1, input2) {
        let result = "Result: ";
        result += input1;
        if (input2 !== null) {
            result += " " + input2;
        }
        return result;
        }
```

The following illustration displays using the `OptionalParameterFunction` csutom function in the rule editor:

![Optional or required parameters ](/help/forms/using/assets/optional-default-params.png)

You can save the rule without specifying a value for required parameters, but the rule is not executed and displays a warning message as:

![incomplete rule warning](/help/forms/using/assets/incomplete-rule.png)

When user leaves the optional parameter empty, then the "Undefined" value is passed to the custom function for the optional parameter.

To learn more about how to define optional parameters in JSDocs, [click here](https://jsdoc.app/tags-param).

-->

#### Retourtype

Het retourneringstype geeft het type waarde op dat de aangepaste functie na de uitvoering retourneert. De volgende syntaxis wordt gebruikt om een terugkeertype in een douanefunctie te bepalen:

* `@return {type}`
* `@returns {type}`
  `{type}` staat voor het retourneringstype van de functie. De toegestane retourtypen zijn:
* tekenreeks: vertegenwoordigt één tekenreekswaarde.
* getal: vertegenwoordigt één numerieke waarde.
* boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
* string []: Geeft een array van tekenreekswaarden aan.
* getal []: vertegenwoordigt een array van numerieke waarden.
* boolean [] : vertegenwoordigt een array van Booleaanse waarden.
* date: vertegenwoordigt één datumwaarde.
* date []: Vertegenwoordigt een serie van datumwaarden.
* array: vertegenwoordigt een algemene array met waarden van verschillende typen.
* object: vertegenwoordigt een formulierobject in plaats van de waarde rechtstreeks.

Het terugkeertype is niet case-sensitive.

#### Persoonlijk

De aangepaste functie, gedeclareerd als private, komt niet voor in de lijst met aangepaste functies in de regeleditor van een adaptief formulier. Aangepaste functies zijn standaard openbaar. De syntaxis voor het declareren van een aangepaste functie als private is `@private` .

<!--
#### Member

  Syntax: `@memberof namespace`
  Attaches a namespace to the function.
-->

<!--

#### This

   Syntax: `@this currentComponent`

   Use @this to refer to the Adaptive Form component on which the rule is written. 
  
   The following example is based on the field value. In the following example, the rule hides a field in the form. The `this` portion of `this.value` refers to underlying Adaptive Form component, on which the rule is written.

   ```
      /**
      * @function myTestFunction
      * @this currentComponent
      * @param {scope} scope in which code inside function will be executed.
      */
      myTestFunction = function (scope) {
         if(this.value == "O"){
               scope.age.visible = true;
         } else {
            scope.age.visible = false;
         }
      }

   ```

    >[!NOTE]
    >
    >Comments before custom function are used for summary. Summary can extend to multiple lines until a tag is encountered. Limit the size to a single for a concise description in the rule builder.

-->

<!--

## Function declaration supported types {#function-declaration-supported-types}

**Function Statement**

```javascript
function area(len) {
    return len*len;
}
```

This function is included without `jsdoc` comments.

**Function Expression**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Function Expression and Statement**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Function Declaration as Variable**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Limitation: custom function picks only the first function declaration from the variable list, if together. You can use function expression for every function declared.

**Function Declaration as Object**

```javascript
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```
-->

## Richtlijnen tijdens het maken van aangepaste functies {#considerations}

Om van de douanefuncties in de regelredacteur een lijst te maken, kunt u om het even welke volgende formaten gebruiken:

### Functie-instructie met of zonder jsdoc-opmerkingen

U kunt een aangepaste functie maken met of zonder jsdoc-opmerkingen.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```

Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt deze door de functienaam in de regeleditor weergegeven. Het wordt echter aanbevolen JavaScript-annotaties op te nemen om de leesbaarheid van de aangepaste functies te verbeteren.


### Pijlfunctie met verplichte JavaScript-annotaties of -opmerkingen

U kunt een aangepaste functie maken met een syntaxis voor een pijlfunctie:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} a parameter description
    * @param {string=} b parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
    /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;
    
```

Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt de aangepaste functie niet vermeld in de regeleditor van een adaptief formulier.

### Functie-expressie met verplichte JavaScript-annotaties of -commentaar

Als u aangepaste functies wilt weergeven in de regeleditor van een adaptief formulier, maakt u aangepaste functies in de volgende indeling:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} input1 parameter description
    * @param {string=} input2 parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt de aangepaste functie niet vermeld in de regeleditor van een adaptief formulier.

### Vereisten om een aangepaste functie te maken

Voordat u een aangepaste functie aan uw Adaptive Forms gaat toevoegen, moet u controleren of de volgende Software op uw computer is geïnstalleerd:

* **Onbewerkte Redacteur van de Tekst (winde)**: Terwijl om het even welke duidelijke tekstredacteur kan werken, biedt een Geïntegreerde Milieu van de Ontwikkeling (winde) zoals de Code van Microsoft Visual Studio geavanceerde eigenschappen voor het gemakkelijkere uitgeven aan.

* **Git:** Dit systeem van de versiecontrole wordt vereist voor het beheren van codeveranderingen. Als u deze niet hebt geïnstalleerd, kunt u deze downloaden van https://git-scm.com.


## Een aangepaste functie maken {#create-custom-function}

Stappen voor het maken van aangepaste functies zijn:
1. [&#x200B; creeer een bibliotheek van de cliëntkant gebruikend het AEM Archetype van het Project en voeg een douanefunctie toe &#x200B;](#create-client-library-archetype)
OF
   [&#x200B; creeer douanefuncties door CRXDE &#x200B;](#create-add-custom-function)
1. [Clientbibliotheek toevoegen aan een adaptief formulier](#add-client-library)
1. [Aangepaste functie gebruiken in een adaptief formulier](#use-custom-functions)


### Een clientbibliotheek maken met het AEM Project Archetype{#create-client-library-archetype}

U kunt douanefuncties toevoegen door een cliëntbibliotheek aan het gecreeerde project toe te voegen [&#x200B; gebruikend het AEM Archetype van het Project &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/developing/archetype/using#getting-started).
Als u een bestaand project <!--and have already the project structure as shown in the image below,--> hebt kunt u [&#x200B; douanefuncties &#x200B;](#create-add-custom-function) aan uw lokaal project direct toevoegen.

<!--![custom fuction folder structure](assets/custom-library-folder-structure.png)-->

Nadat u een Project van Archetype creeert of een bestaand project gebruikt, creeer een cliëntbibliotheek. Voer de volgende stappen uit om een clientbibliotheek te maken:

**voeg een Omslag van de Bibliotheek van de Cliënt toe**

Om nieuwe omslag van de cliëntbibliotheek aan uw [ AEM projectfolder ] toe te voegen, volg de stappen:

1. Open de [ AEM projectfolder ] in een redacteur.

   ![&#x200B; de omslagstructuur van de douanefunctie &#x200B;](assets/custom-library-folder-structure.png)

1. Zoek `ui.apps` .
1. Nieuwe map toevoegen. Voeg bijvoorbeeld een map toe met de naam `experience-league` .
1. Navigeer naar de map `/experience-league/` en voeg een `ClientLibraryFolder` toe. Maak bijvoorbeeld een clientbibliotheekmap met de naam `customclientlibs` .

   Locatie is: `[AEM project directory]/ui.apps/src/main/content/jcr_root/apps/`

**voegt dossiers en omslagen aan de omslag van de Bibliotheek van de Cliënt toe**

Voeg het volgende toe aan de toegevoegde omslag van de cliëntbibliotheek:

* `.content.xml` -bestand
* `js.txt` -bestand
* `js` -map

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Voeg in `.content.xml` de volgende coderegels toe:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > U kunt een willekeurige naam kiezen voor de eigenschappen `client library folder` en `categories` .

1. Voeg in `js.txt` de volgende coderegels toe:

   ```javascript
         #base=js
       function.js
   ```

1. Voeg in de map `js` het javascript-bestand toe als `function.js` dat de aangepaste functies bevat:

   ```javascript
   /**
       * Calculates Age
       * @name calculateAge
       * @param {object} field
       * @return {string} 
   */
   
   function calculateAge(field) {
   var dob = new Date(field);
   var now = new Date();
   
   var age = now.getFullYear() - dob.getFullYear();
   var monthDiff = now.getMonth() - dob.getMonth();
   
   if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
   age--;
   }
   
   return age;
   }
   ```

1. Sla de bestanden op.

![&#x200B; de omslagstructuur van de douanefunctie &#x200B;](assets/custom-function-added-files.png)

**omvat de nieuwe omslag in filter.xml**:

1. Navigeer aan het `/ui.apps/src/main/content/META-INF/vault/filter.xml` dossier in uw [ AEMaaCS projectfolder ].

1. Open het bestand en voeg de volgende regel aan het einde toe:

   `<filter root="/apps/experience-league" />`
1. Sla het bestand op.

   ![&#x200B; de filter xml van de douanefunctie &lbrace;](assets/custom-function-filterxml.png)

1. Bouw de pas gecreëerde omslag van de cliëntbibliotheek aan uw AEM milieu door de stappen te volgen die in [&#x200B; worden gegeven hoe te sectie &#x200B;](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype#how-to-build) bouwen.

## Aangepaste functies maken en implementeren via CRXDE{#create-add-custom-function}

Als u de nieuwste invoegtoepassing voor AEM Forms en Forms gebruikt, kunt u een aangepaste functie maken via CRXDE om de nieuwste updates van aangepaste functies te gebruiken. Voer daartoe de volgende stappen uit:

<!--![custom fuction folder structure](assets/custom-library-folder-structure.png)-->


1. Meld u aan bij `http://server:port/crx/de/index.jsp#` .
1. Maak een map onder de map `/apps` . Maak bijvoorbeeld een map met de naam `experience-league` .
1. Sla uw wijzigingen op.
1. Navigeer naar de gemaakte map en maak een knooppunt van het type `cq:ClientLibraryFolder` as `clientlibs` .
1. Navigeer naar de nieuwe map `clientlibs` en voeg de eigenschappen `allowProxy` en `categories` toe:

   ![&#x200B; de knoopeigenschappen van de Bibliotheek van de Douane &#x200B;](/help/forms/using/assets/customlibrary-catproperties.png)

   >[!NOTE]
   >
   > U kunt elke naam opgeven in plaats van `customfunctionsdemo` .

1. Sla uw wijzigingen op.

1. Maak een map met de naam `js` onder de map `clientlibs` .
1. Maak een JavaScript-bestand met de naam `functions.js` onder de map `js` .
1. Maak een bestand met de naam `js.txt` onder de map `clientlibs` .
1. Sla uw wijzigingen op.
De gemaakte mapstructuur ziet er als volgt uit:

   ![&#x200B; creeerde de Omslagstructuur van de Bibliotheek van de Cliënt &#x200B;](/help/forms/using/assets/clientlibrary_folderstructure.png)
1. Dubbelklik op het `functions.js` -bestand om de editor te openen. Het bestand bevat de code voor een aangepaste functie.
Voeg de volgende code toe aan het JavaScript-bestand om de leeftijd te berekenen op basis van de geboortedatum (JJJJ-MM-DD).

   ```javascript
       /**
            * Calculates Age
            * @name calculateAge 
            * @return {string} 
       */
   
       function calculateAge(dateOfBirthString) {
       var dob = new Date(dateOfBirthString);
       var now = new Date();
   
       var age = now.getFullYear() - dob.getFullYear();
       var monthDiff = now.getMonth() - dob.getMonth();
   
       if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
       age--;
       }
   
       return age;
       }
   ```

1. Opslaan `function.js` .
1. Navigeer naar `js.txt` en voeg de volgende code toe:

   ```javascript
       #base=js
       functions.js
   ```

1. Sla het `js.txt` -bestand op.

U kunt naar de volgende [&#x200B; omslag van de douanefunctie &#x200B;](/help/forms/using/assets/customfunction.zip) verwijzen. Download en installeer deze map op uw AEM.

Nu kunt u de aangepaste functie in het adaptieve formulier gebruiken door de clientbibliotheek toe te voegen.

## Clientbibliotheek toevoegen in een adaptief formulier{#add-client-library}

Zodra u uw clientbibliotheek hebt geïmplementeerd in uw AEM Forms-omgeving, gebruikt u de mogelijkheden ervan in uw adaptieve formulier. De clientbibliotheek toevoegen aan uw adaptieve formulier

1. Open het formulier in de bewerkingsmodus. Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Edit]** .
1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik op het pictogram Eigenschappen van de container van de hulplijn. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open het tabblad **[!UICONTROL Basic]** en selecteer de naam van de **[!UICONTROL client library category]** in de vervolgkeuzelijst (in dit geval selecteert u `customfunctionscategory` ).

   ![&#x200B; Toevoegend de de cliëntbibliotheek van de douanefunctie &#x200B;](/help/forms/using//assets/custom-function-category-name-core-component.png)

1. Klik op **[!UICONTROL Done]**.

Nu, kunt u een regel tot stand brengen om douanefuncties in de regelredacteur te gebruiken:

![&#x200B; Toevoegend de de cliëntbibliotheek van de douanefunctie &#x200B;](/help/forms/using//assets/calculateage-customfunction.png)

Nu, begrijpen wij hoe te om een douanefunctie te vormen en te gebruiken gebruikend de [&#x200B; Invoke dienst van de Redacteur van de Regel in AEM Forms 6.5 &#x200B;](/help/forms/using/rule-editor-core-components.md#invoke-form-data-model-service-invoke)

## Aangepaste functie gebruiken in een adaptief formulier {#use-custom-functions}

In een AanpassingsVorm, kunt u [&#x200B; Functies van de Douane binnen de regelredacteur &#x200B;](/help/forms/using/rule-editor-core-components.md) gebruiken.
Voeg de volgende code toe aan het JavaScript-bestand (`Function.js` ) om de leeftijd te berekenen op basis van de geboortedatum (JJJJ-MM-DD). Maak een aangepaste functie als `calculateAge()` die de geboortedatum als invoer neemt en de leeftijd retourneert:

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

In het bovenstaande voorbeeld wordt de aangepaste functie `calculateAge` aangeroepen en wordt de leeftijd geretourneerd wanneer de gebruiker de geboortedatum in de notatie invoert (JJJJ-MM-DD).

![&#x200B; berekent de aangepaste functie van de Leeftijd in de Redacteur van de Regel &#x200B;](/help/forms/using/assets/custom-function-calculate-age.png)

Bekijk een voorbeeld van het formulier om te zien hoe de aangepaste functies worden geïmplementeerd via de regeleditor:

![&#x200B; berekent de aangepaste functie van de Leeftijd in de Voorproef van de Vorm van de Redacteur van de Regel &#x200B;](/help/forms/using/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> U kunt naar de volgende [&#x200B; omslag van douanefuncties &#x200B;](/help/forms/using/assets/customfunctions.zip) verwijzen. Download en installeer deze omslag in uw AEM instantie gebruikend de [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager).

### Ondersteuning voor asynchrone functies in aangepaste functies {#support-of-async-functions}

De asynchrone douanefuncties verschijnen niet in de lijst van de regelredacteur. Het is echter mogelijk om asynchrone functies aan te roepen binnen aangepaste functies die zijn gemaakt met synchrone functie-expressies.

![&#x200B; Synchronisatie en async douanefunctie &#x200B;](/help/forms/using/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> Het voordeel van het aanroepen van asynchrone functies in aangepaste functies is dat asynchrone functies gelijktijdige uitvoering van meerdere taken mogelijk maken, met het resultaat van elke functie die binnen de aangepaste functies wordt gebruikt.

Bekijk de code hieronder om te zien hoe we asynchrone functies kunnen aanroepen met behulp van aangepaste functies:

```javascript
    
    async function asyncFunction() {
    const response = await fetch('https://petstore.swagger.io/v2/store/inventory');
    const data = await response.json();
    return data;
    }

    /**
    * callAsyncFunction
    * @name callAsyncFunction callAsyncFunction
    */
    function callAsyncFunction() {
    asyncFunction()
        .then(responseData => {
        console.log('Response data:', responseData);
        })
        .catch(error => {
         console.error('Error:', error);
    });
}
```

In het bovenstaande voorbeeld is de functie asyncFunction een `asynchronous function` . De toepassing voert een asynchrone bewerking uit door een `GET` -aanvraag in te dienen bij `https://petstore.swagger.io/v2/store/inventory` . Het wacht op de reactie met `await`, parseert de hoofdtekst van de reactie met JSON met de `response.json()` en retourneert de gegevens. De functie `callAsyncFunction` is een synchrone aangepaste functie die de functie `asyncFunction` aanroept en de reactiegegevens in de console weergeeft. Hoewel de functie `callAsyncFunction` synchroon is, roept deze de asynchrone functie asynchrone functie asyncFunction aan en verwerkt deze het resultaat met `then` - en `catch` -instructies.

Om zijn het werken te zien, laten wij een knoop toevoegen en een regel voor de knoop creëren die de asynchrone functie na een knoop klikt.

![&#x200B; creërend regel voor async functie &#x200B;](/help/forms/using/assets/rule-for-async-funct.png)

Raadpleeg de illustratie van het onderstaande consolevenster om aan te tonen dat wanneer de gebruiker op de knop `Fetch` klikt, de aangepaste functie `callAsyncFunction` wordt aangeroepen, die op zijn beurt een asynchrone functie `asyncFunction` aanroept. Inspect het consolevenster om de reactie op de knoop te bekijken klikt:

![&#x200B; venster van de Console &#x200B;](/help/forms/using/assets/async-custom-funct-console.png)

Laten we eens kijken naar de functies van aangepaste functies.

## Verschillende functies voor Aangepaste functies

U kunt aangepaste functies gebruiken om aangepaste functies toe te voegen aan formulieren. Deze functies ondersteunen diverse mogelijkheden, zoals het werken met specifieke velden, het gebruik van globale velden of caching. Dankzij deze flexibiliteit kunt u formulieren aanpassen aan de vereisten van uw organisatie.

### Veld- en globale bereikobjecten in aangepaste functies {#support-field-and-global-objects}

Veldobjecten verwijzen naar de afzonderlijke componenten of elementen in een formulier, zoals tekstvelden, selectievakjes. Het object Globals bevat alleen-lezen variabelen, zoals formulierinstantie, doelveldinstantie en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies.

>[!NOTE]
>
> `param {scope} globals` moet de laatste parameter zijn en wordt niet weergegeven in de regeleditor van een adaptief formulier.

<!-- Let us look at the following code snippet:

```JavaScript
   
    /**
    * updateDateTime
    * @name updateDateTime
    * @param {object} field
    * @param {scope} globals
    */
    function updateDateTime(field, globals) {
    // Accessing the Date object from the global scope
    var currentDate = new Date();
    // Formatting the date and time
    var formattedDateTime = currentDate.toLocaleString();
    // Updating the field value with the formatted date and time using setProperty.
    globals.functions.setProperty(field, {value: formattedDateTime});
    }
```

In the above code snippet, a custom function named `updateDateTime` takes parameters such as a field object and a global object. The field represents the textbox object where the formatted date and time value is displayed within the form. -->

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken met behulp van een `Contact Us` -formulier met behulp van verschillende gebruiksmogelijkheden.

![&#x200B; Vorm van het Contact ons &#x200B;](/help/forms/using/assets/contact-us-form.png)

#### **Geval van het Gebruik**: toon een paneel gebruikend de `SetProperty` regel

Voeg de volgende code in de douanefunctie toe zoals die in [&#x200B; wordt verklaard creeer-douane-functie &#x200B;](#create-custom-function) sectie, om het vormgebied als `Required` te plaatsen.

```javascript
    
    /**
    * enablePanel
    * @name enablePanel
    * @param {object} field1
    * @param {object} field2
    * @param {scope} globals 
    */

    function enablePanel(field1,field2, globals)
    {
       if(globals.functions.validate(field1).length === 0)
       {
       globals.functions.setProperty(field2, {visible: true});
       }
    }
```

>[!NOTE]
>
> * U kunt de veldeigenschappen vormen gebruikend de beschikbare eigenschappen die in `[form-path]/jcr:content/guideContainer.model.json` worden gevestigd.
> * Wijzigingen die u met de methode `setProperty` van het object Globals in het formulier aanbrengt, zijn asynchroon van aard en worden niet doorgevoerd tijdens het uitvoeren van de aangepaste functie.

In dit voorbeeld wordt de validatie van het deelvenster `personaldetails` uitgevoerd wanneer u op de knop klikt. Als er geen fouten worden gedetecteerd in het deelvenster, wordt een ander deelvenster, het deelvenster `feedback` , weergegeven wanneer u op de knop klikt.

Laten we een regel voor de knop `Next` maken, die het deelvenster `personaldetails` valideert en het deelvenster `feedback` zichtbaar maakt wanneer de gebruiker op de knop `Next` klikt.

![&#x200B; plaats Bezit &#x200B;](/help/forms/using/assets/custom-function-set-property.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar het deelvenster `personaldetails` wordt gevalideerd wanneer u op de knop `Next` klikt. Als alle velden in de `personaldetails` worden gevalideerd, wordt het deelvenster `feedback` weergegeven.

![&#x200B; plaats de Voorproef van de Vorm van het Bezit &#x200B;](/help/forms/using/assets/set-property-form-preview.png)

Als er fouten voorkomen in de velden van het deelvenster `personaldetails` , worden deze in het veld weergegeven wanneer op de knop `Next` wordt geklikt. Het deelvenster `feedback` blijft dan onzichtbaar.

![&#x200B; plaats de Voorproef van de Vorm van het Bezit &#x200B;](/help/forms/using/assets/set-property-panel.png)

#### **Geval van het Gebruik**: Valideer het gebied.

Voeg de volgende code in de douanefunctie toe zoals die in [&#x200B; wordt verklaard creeer-douane-functie &#x200B;](#create-custom-function) sectie, om het gebied te bevestigen.

```javascript
    /**
    * validateField
    * @name validateField
    * @param {object} field
    * @param {scope} globals
    */
    function validateField(field,globals)
    {
    
        globals.functions.validate(field);
    
    }   
```

>[!NOTE]
>
> Als er geen argument wordt doorgegeven in de functie `validate()` , wordt het formulier gevalideerd.

In dit voorbeeld wordt een aangepast validatiepatroon toegepast op het veld `contact` . Gebruikers moeten een telefoonnummer invoeren dat begint met `10` gevolgd door `8` cijfers. Als de gebruiker een telefoonnummer invoert dat niet begint met `10` of meer of minder dan `8` cijfers bevat, verschijnt er een foutbericht bij de klik op de knop:

![&#x200B; Patroon van de Bevestiging van het E-mailAdres &#x200B;](/help/forms/using/assets/custom-function-validation-pattern.png)

De volgende stap bestaat uit het maken van een regel voor de knop `Next` die het veld `contact` in het klikveld valideert.

![&#x200B; Patroon van de Bevestiging &#x200B;](/help/forms/using/assets/custom-function-validate.png)

Verwijs naar de illustratie hieronder om aan te tonen dat als de gebruiker een telefoonaantal ingaat dat niet met `10` begint, een foutenmelding op het gebiedsniveau verschijnt:

![&#x200B; Patroon van de Bevestiging van het E-mailAdres &#x200B;](/help/forms/using/assets/custom-function-validate-error-message.png)

Als de gebruiker een geldig telefoonnummer invoert en alle velden in het deelvenster `personaldetails` zijn gevalideerd, wordt het deelvenster `feedback` op het scherm weergegeven:

![&#x200B; Patroon van de Bevestiging van het E-mailAdres &#x200B;](/help/forms/using/assets/validate-form-preview-form.png)

#### **Geval van het Gebruik**: Herstel een paneel

Voeg de volgende code in de douanefunctie toe zoals die in [&#x200B; wordt verklaard creeer-douane-functie &#x200B;](#create-custom-function) sectie, om het paneel terug te stellen.

```javascript
    /**
    * resetField
    * @name  resetField
    * @param {string} input1
    * @param {object} field
    * @param {scope} globals 
    */
    function  resetField(field,globals)
    {
    
        globals.functions.reset(field);
    
    }
```

>[!NOTE]
>
> Als er geen argument wordt doorgegeven in de functie `reset()` , wordt het formulier gevalideerd.

In dit voorbeeld wordt het deelvenster `personaldetails` opnieuw ingesteld wanneer u op de knop `Clear` klikt. In de volgende stap wordt een regel gemaakt voor de knop `Clear` die het deelvenster opnieuw instelt wanneer op de knop wordt geklikt.

![&#x200B; Duidelijke knoop &#x200B;](/help/forms/using/assets/custom-function-reset-field.png)

Zie de onderstaande afbeelding om weer te geven dat als de gebruiker op de knop `clear` klikt, het deelvenster `personaldetails` opnieuw wordt ingesteld:

![&#x200B; Vorm van het Terugstellen &#x200B;](assets/custom-function-reset-form.png)

#### **Geval van het Gebruik**: Om douanebericht op het gebiedsniveau te tonen en het gebied als ongeldig te merken

Met de functie `markFieldAsInvalid()` kunt u een veld definiëren als ongeldig en een aangepast foutbericht instellen op veldniveau. De `fieldIdentifier` -waarde kan `fieldId` , `field qualifiedName` of `field dataRef` zijn. De waarde van het object met de naam `option` kan `{useId: true}` , `{useQualifiedName: true}` of `{useDataRef: true}` zijn.
De syntaxis die wordt gebruikt om het veld als ongeldig te markeren en een aangepast bericht in te stellen, is:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Voeg de volgende code in de douanefunctie toe zoals die in [&#x200B; wordt verklaard creeer-douane-functie &#x200B;](#create-custom-function) sectie, om douanebericht op het gebiedsniveau toe te laten.

```javascript
    /**
    * customMessage
    * @name customMessage
    * @param {object} field
    * @param {scope} globals 
    */
    function customMessage(field, globals) {
    const minLength = 15;
    const comments = field.$value.trim();
    if (comments.length < minLength) {
        globals.functions.markFieldAsInvalid(field.$id, "Comments must be at least 15 characters long.", { useId: true });
    }
}
```

In dit voorbeeld wordt een aangepast bericht weergegeven op veldniveau als de gebruiker minder dan 15 tekens invoert in het tekstvak Opmerkingen.

In de volgende stap wordt een regel voor het veld `comments` gemaakt:

![&#x200B; gebied van het Teken als Ongeldig &#x200B;](/help/forms/using/assets/custom-function-invalid-field.png)

Zie de onderstaande demonstratie om te tonen dat het invoeren van negatieve feedback in het veld `comments` de weergave van een aangepast bericht op veldniveau activeert:

![&#x200B; gebied van het Teken als Ongeldige vorm van de Voorproef &#x200B;](/help/forms/using/assets/custom-function-invalidfield-form.png)

Als de gebruiker meer dan 15 tekens in het tekstvak Opmerkingen invoert, wordt het veld gevalideerd en wordt het formulier verzonden:

![&#x200B; gebied van het Teken als geldige vorm van de Voorproef &#x200B;](/help/forms/using/assets/custom-function-validfield-form.png)


#### **Geval van het Gebruik**: Verzend veranderde gegevens aan de server

De volgende regel code:
`globals.functions.submitForm(globals.functions.exportData(), false);` wordt gebruikt om de formuliergegevens te verzenden na manipulatie.
* Het eerste argument betreft de gegevens die moeten worden ingediend.
* Het tweede argument geeft aan of het formulier moet worden gevalideerd voordat het wordt verzonden. Deze is `optional` en wordt standaard ingesteld op `true` .
* Het derde argument is de `contentType` van de verzending, die ook optioneel is met de standaardwaarde `multipart/form-data` . De andere waarden kunnen `application/json` en `application/x-www-form-urlencoded` zijn.

Voeg de volgende code in de douanefunctie toe zoals die in [&#x200B; wordt verklaard creeer-douane-functie &#x200B;](#create-custom-function) sectie, om de gemanipuleerde gegevens bij de server voor te leggen:

```javascript
    /**
    * submitData
    * @name submitData
    * @param {object} field
    * @param {scope} globals 
    */
    function submitData(globals)
    {
    
    var data = globals.functions.exportData();
    if(!data.comments) {
    data.comments = 'NA';
    }
    console.log('After update:{}',data);
    globals.functions.submitForm(data, false);
    }
```

In dit voorbeeld wordt `NA` verzonden naar de server wanneer de gebruiker het tekstvak `comments` leeg laat.

Maak nu een regel voor de knop `Submit` die gegevens verzendt:

![&#x200B; legt gegevens &#x200B;](/help/forms/using/assets/custom-function-submit-data.png) voor

Raadpleeg de illustratie van de onderstaande `console window` om aan te tonen dat als de gebruiker het `comments` textbox leeg laat, de waarde zoals `NA` wordt verzonden op de server:

![&#x200B; legt gegevens bij het consolevenster voor &#x200B;](/help/forms/using/assets/custom-function-submit-data-form.png)

U kunt het consolevenster ook inspecteren om de gegevens te bekijken die aan de server worden voorgelegd:

![&#x200B; gegevens van Inspect bij het consolevenster &#x200B;](/help/forms/using/assets/custom-function-submit-data-console-data.png)

<!--

#### **Use Case**: Display form submission and failure messages for custom submit action 

Add the following line of code as explained in the [create-custom-function ](#create-custom-function) section, to customize the submission or failure message for form submissions and display the form submission messages in a modal box:

```javascript
/**
 * Handles the success response after a form submission.
 *
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitSuccessHandler(globals) {
    var event = globals.event;
    var submitSuccessResponse = event.payload.body;
    var form = globals.form;

    if (submitSuccessResponse) {
        if (submitSuccessResponse.redirectUrl) {
            window.location.href = encodeURI(submitSuccessResponse.redirectUrl);
        } else if (submitSuccessResponse.thankYouMessage) {
            showModal("success", submitSuccessResponse.thankYouMessage);
        }
    }
}

/**
 * Handles the error response after a form submission.
 *
 * @param {string} customSubmitErrorMessage - The custom error message.
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitErrorHandler(customSubmitErrorMessage, globals) {
    showModal("error", customSubmitErrorMessage);
}
function showModal(type, message) {
    // Remove any existing modals
    var existingModal = document.getElementById("modal");
    if (existingModal) {
        existingModal.remove();
    }

    // Create the modal dialog
    var modal = document.createElement("div");
    modal.setAttribute("id", "modal");
    modal.setAttribute("class", "modal");

    // Create the modal content
    var modalContent = document.createElement("div");
    modalContent.setAttribute("class", "modal-content");

    // Create the modal header
    var modalHeader = document.createElement("div");
    modalHeader.setAttribute("class", "modal-header");
    modalHeader.innerHTML = "<h2>" + (type === "success" ? "Thank You" : "Error") + "</h2>";

    // Create the modal body
    var modalBody = document.createElement("div");
    modalBody.setAttribute("class", "modal-body");
    modalBody.innerHTML = "<p class='" + type + "-message'>" + message + "</p>";

    // Create the modal footer
    var modalFooter = document.createElement("div");
    modalFooter.setAttribute("class", "modal-footer");

    // Create the close button
    var closeButton = document.createElement("button");
    closeButton.setAttribute("class", "close-button");
    closeButton.innerHTML = "Close";
    closeButton.onclick = function() {
        modal.remove();
    };

    // Append the elements to the modal content
    modalFooter.appendChild(closeButton);
    modalContent.appendChild(modalHeader);
    modalContent.appendChild(modalBody);
    modalContent.appendChild(modalFooter);

    // Append the modal content to the modal
    modal.appendChild(modalContent);

    // Append the modal to the document body
    document.body.appendChild(modal);
}
```

In this example, when the user uses the `customSubmitSuccessHandler` and `customSubmitErrorHandler` custom functions, the success and failure messages are displayed in a modal. The JavaScript function `showModal(type, message)` is used to dynamically create and display a modal dialog box on a screen.

Now, create a rule for successful form submission:

![Form submission success](/help/forms/using/assets/form-submission-success.png)

Refer to the illustration below to demonstrate that when the form is submitted successfully, the success message is displayed in a modal:

![Form submission success message](/help/forms/using/assets/form-submission-success-message.png )
 
Similarly, let us create a rule for failed form submissions:

![Form submission fail](/help/forms/using/assets/form-submission-fail.png)

Refer to the illustration below to demonstrate that when the form submission fails, the error message is displayed in a modal:

![Form submission fail message](/help/forms/using/assets/form-submission-fail-message.png )

To display form submission success and failure in a default manner, the `Default submit Form Success Handler` and `Default submit Form Error Handler` functions are available out of the box.

In case, the custom submit action fails to perform as expected in existing AEM projects or forms, refer to the [troubleshooting](#troubleshooting) section.

-->

## Ondersteuning voor caching van aangepaste functies

De adaptieve Forms voert caching voor douanefuncties uit om reactietijd te verbeteren terwijl het terugwinnen van de lijst van de douanefunctie in de regelredacteur. Er verschijnt een bericht als `Fetched following custom functions list from cache` in het `error.log` -bestand.

![&#x200B; douanefunctie met geheim voorgeheugensteun &#x200B;](/help/forms/using/assets/custom-function-cache-error.png)

Als de aangepaste functies worden gewijzigd, wordt het in cache plaatsen ongeldig en wordt het geparseerd.

## Problemen oplossen {#troubleshooting}

* De gebruiker moet ervoor zorgen dat de [&#x200B; kerncomponent en specificatieversie aan de recentste versie &#x200B;](https://github.com/adobe/aem-core-forms-components/tree/release/650) worden geplaatst. Voor bestaande AEM projecten en formulieren zijn echter aanvullende stappen nodig:

   * Voor het AEM project moet de gebruiker alle instanties van `submitForm('custom:submitSuccess', 'custom:submitError')` vervangen door `submitForm()` en het project implementeren.

   * Voor bestaande vormen, als de managers van de douanevoorlegging niet correct functioneren, moet de gebruiker de `submitForm` regel op **openen en bewaren** knoop gebruikend de Redacteur van de Regel. Deze handeling vervangt de bestaande regel van `submitForm('custom:submitSuccess', 'custom:submitError')` door `submitForm()` in het formulier.


* Als het JavaScript-bestand met code voor aangepaste functies een fout bevat, worden de aangepaste functies niet vermeld in de regeleditor van een adaptief formulier. Als u de lijst met aangepaste functies wilt controleren, navigeert u naar het `error.log` -bestand voor de fout. In het geval van een fout wordt de lijst met aangepaste functies leeg weergegeven:

  ![&#x200B; dossier van het foutenlogboek &#x200B;](/help/forms/using/assets/custom-function-list-error-file.png)

  Als er geen fout optreedt, wordt de aangepaste functie opgehaald en in het `error.log` -bestand weergegeven. Er verschijnt een bericht als `Fetched following custom functions list` in het `error.log` -bestand:

  ![&#x200B; dossier van het foutenlogboek met juiste douanefunctie &#x200B;](/help/forms/using/assets/custom-function-list-fetched-in-error.png)

## Overwegingen

* De `parameter type` en `return type` bieden geen ondersteuning voor `None` .

* De functies die niet worden ondersteund in de lijst met aangepaste functies zijn:
   * Generatorfuncties
   * Functies Async/Await
   * Methodedefinities
   * Methoden van Class
   * Standaardparameters
   * Rustparameters
