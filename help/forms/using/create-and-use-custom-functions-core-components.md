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
* Ondersteuning voor moderne JavaScript-functies zoals verlaat- en pijlfuncties (ES10-ondersteuning)

Zorg ervoor dat u de [nieuwste formulierversie](https://github.com/adobe/aem-core-forms-components/tree/release/650) in uw AEM Forms Core-componentomgeving voor gebruik van de nieuwste functies in Aangepaste functies. </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | Dit artikel |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/create-and-use-custom-functions) |

## Inleiding

AEM Forms 6.5 bevat JavaScript-functies waarmee u complexe bedrijfsregels kunt definiëren met de regeleditor. Hoewel AEM Forms verschillende aangepaste functies biedt die niet in de box kunnen worden gebruikt, vereisen veel gebruiksgevallen het definiëren van uw eigen aangepaste functies die in meerdere formulieren kunnen worden gebruikt. Deze aangepaste functies verbeteren de mogelijkheden van formulieren door de bewerking en verwerking van ingevoerde gegevens in staat te stellen aan specifieke vereisten te voldoen. Bovendien kunnen hiermee het formuliergedrag dynamisch worden gewijzigd op basis van de vooraf gedefinieerde criteria.

### Gebruik van aangepaste functies {#uses-of-custom-function}

De voordelen van het gebruik van Aangepaste functies in Aangepaste Forms Core-componenten zijn:


* **Gegevens beheren**: Met aangepaste functies kunt u gegevens die zijn ingevoerd in de formuliervelden, beheren en verwerken.
* **Verwerking van gegevens**: Met aangepaste functies kunt u gegevens verwerken die zijn ingevoerd in de formuliervelden.
* **Validatie van gegevens**: Met aangepaste functies kunt u aangepaste controles uitvoeren op de invoer van formulieren en opgegeven foutberichten weergeven.
* **Dynamisch gedrag**: Met aangepaste functies kunt u het dynamische gedrag van uw formulieren bepalen op basis van specifieke omstandigheden. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt aangepaste functies gebruiken om te integreren met externe API&#39;s of services. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

Aangepaste functies zijn in wezen clientbibliotheken die in het JavaScript-bestand worden toegevoegd. Zodra u een Functie van de Douane creeert, wordt het beschikbaar in de regelredacteur voor selectie door de gebruiker in een Aangepast Vorm. De aangepaste functies worden geïdentificeerd door de JavaScript-annotaties in de regeleditor.

### Ondersteunde JavaScript-annotaties voor aangepaste functies {#js-annotations}

**JavaScript-annotaties bevatten metagegevens voor JavaScript-code**. Het bevat bijvoorbeeld opmerkingen die beginnen met specifieke symbolen. `/**` en `@`. De annotaties bevatten belangrijke informatie over functies, variabelen en andere elementen in de code. Het adaptieve formulier ondersteunt de volgende JavaScript-aantekeningen voor aangepaste functies:

#### Naam

De **Naam** wordt gebruikt om de douanefunctie in de regelredacteur van een Adaptief vorm te identificeren. De volgende syntaxis wordt gebruikt om een Functie van de Douane te noemen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`

>[!NOTE]
>`[functionName]` is de naam van de functie. Spaties zijn niet toegestaan.
>`<Function Name>` is de weergavenaam van de functie in de regeleditor van Adaptive Forms.
>Als de functienaam identiek is aan de naam van de functie zelf, kunt u weglaten `[functionName]` in de syntaxis.

#### Parameter

De **Parameter** is een lijst met argumenten die door aangepaste functies worden gebruikt. Een functie kan meerdere parameters ondersteunen. De volgende syntaxis wordt gebruikt om een parameter in een douanefunctie te bepalen:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`

  `{type}` vertegenwoordigt het parametertype. De toegestane parametertypen zijn:

   * tekenreeks: vertegenwoordigt één tekenreekswaarde.
   * getal: vertegenwoordigt één numerieke waarde.
   * boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
   * string[]: Vertegenwoordigt een array van tekenreekswaarden.
   * getal[]: Vertegenwoordigt een array van numerieke waarden.
   * boolean[]: Vertegenwoordigt een array van Booleaanse waarden.
   * date: vertegenwoordigt één datumwaarde.
   * date[]: Vertegenwoordigt een array met datumwaarden.
   * array: vertegenwoordigt een algemene array met waarden van verschillende typen.
   * object: vertegenwoordigt een formulierobject dat aan een aangepaste functie wordt doorgegeven in plaats van dat de waarde rechtstreeks wordt doorgegeven.
   * bereik: vertegenwoordigt het globals object, dat alleen-lezen variabelen bevat, zoals formulierinstanties, doelveldinstanties en methoden voor het uitvoeren van formulierwijzigingen binnen de aangepaste functies. Deze wordt gedeclareerd als de laatste parameter in de JavaScript-annotaties en is niet zichtbaar voor de regeleditor van een adaptief formulier. De bereikparameter benadert het object van het formulier of de component om de regel of gebeurtenis te activeren die vereist is voor formulierverwerking. Voor meer informatie over het object Globals en hoe het te gebruiken, [klik hier](/help/forms/using/create-and-use-custom-functions-core-components.md#field-and-global-scope-objects-in-custom-functions-support-field-and-global-objects)

Het parametertype is **niet hoofdlettergevoelig** en spaties zijn niet toegestaan in de parameternaam.

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
  `{type}` vertegenwoordigt het terugkeertype van de functie. De toegestane retourtypen zijn:
* tekenreeks: vertegenwoordigt één tekenreekswaarde.
* getal: vertegenwoordigt één numerieke waarde.
* boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
* string[]: Vertegenwoordigt een array van tekenreekswaarden.
* getal[]: Vertegenwoordigt een array van numerieke waarden.
* boolean[]: Vertegenwoordigt een array van Booleaanse waarden.
* date: vertegenwoordigt één datumwaarde.
* date[]: Vertegenwoordigt een array met datumwaarden.
* array: vertegenwoordigt een algemene array met waarden van verschillende typen.
* object: vertegenwoordigt een formulierobject in plaats van de waarde rechtstreeks.

Het terugkeertype is niet case-sensitive.

#### Persoonlijk

De aangepaste functie, gedeclareerd als private, komt niet voor in de lijst met aangepaste functies in de regeleditor van een adaptief formulier. Aangepaste functies zijn standaard openbaar. De syntaxis voor het declareren van een aangepaste functie als private is `@private`.

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

Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt deze door de functienaam in de regeleditor weergegeven. Het wordt echter aanbevolen JavaScript-aantekeningen op te nemen om de leesbaarheid van de aangepaste functies te verbeteren.


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

### Functie-expressie met verplichte JavaScript-aantekeningen of -opmerkingen

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

* **Onbewerkte teksteditor (IDE)**: Terwijl om het even welke duidelijke tekstredacteur kan werken, biedt een Geïntegreerde Milieu van de Ontwikkeling (winde) zoals de Code van Microsoft Visual Studio geavanceerde eigenschappen voor het gemakkelijker uitgeven aan.

* **Git:** Dit versiebeheersysteem is vereist voor het beheer van codewijzigingen. Als u deze niet hebt geïnstalleerd, kunt u deze downloaden van https://git-scm.com.


## Een aangepaste functie maken {#create-custom-function}

Stappen voor het maken van aangepaste functies zijn:
1. [Een bibliotheek aan de clientzijde maken met het AEM Project Archetype en een aangepaste functie toevoegen](#create-client-library-archetype)
OF
   [Aangepaste functies maken via CRXDE](#create-add-custom-function)
1. [Clientbibliotheek toevoegen aan een adaptief formulier](#add-client-library)
1. [Aangepaste functie gebruiken in een adaptief formulier](#use-custom-functions)


### Een clientbibliotheek maken met het AEM Project Archetype{#create-client-library-archetype}

U kunt aangepaste functies toevoegen door een clientbibliotheek toe te voegen aan het gemaakte project [met het AEM Project Archetype](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/using#getting-started).
Als u een bestaand project hebt <!--and have already the project structure as shown in the image below,--> u kunt rechtstreeks toevoegen [aangepaste functies](#create-add-custom-function) naar uw lokale project.

<!--![custom fuction folder structure](assets/custom-library-folder-structure.png)-->

Nadat u een Project van Archetype creeert of een bestaand project gebruikt, creeer een cliëntbibliotheek. Voer de volgende stappen uit om een clientbibliotheek te maken:

**Een clientbibliotheekmap toevoegen**

Nieuwe clientbibliotheekmap toevoegen aan uw [Projectmap AEM]Voer de volgende stappen uit:

1. Open de [Projectmap AEM] in een editor.

   ![aangepaste mapstructuur voor functies](assets/custom-library-folder-structure.png)

1. Zoeken `ui.apps`.
1. Nieuwe map toevoegen. Voeg bijvoorbeeld een map toe met de naam `experience-league`.
1. Navigeren naar `/experience-league/` en voeg een `ClientLibraryFolder`. Maak bijvoorbeeld een clientbibliotheekmap met de naam `customclientlibs`.

   Locatie is: `[AEM project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Bestanden en mappen toevoegen aan de map Client Library**

Voeg het volgende toe aan de toegevoegde omslag van de cliëntbibliotheek:

* `.content.xml` file
* `js.txt` file
* `js` map

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. In de `.content.xml` Voeg de volgende coderegels toe:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > U kunt elke naam kiezen voor `client library folder` en `categories` eigenschap.

1. In de `js.txt` Voeg de volgende coderegels toe:

   ```javascript
         #base=js
       function.js
   ```

1. In de `js` map, voeg het javascript-bestand toe als `function.js` Dit omvat de aangepaste functies:

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

![aangepaste mapstructuur voor functies](assets/custom-function-added-files.png)

**De nieuwe map opnemen in filter.xml**:

1. Ga naar de `/ui.apps/src/main/content/META-INF/vault/filter.xml` bestand in uw [AEMaaCS-projectmap].

1. Open het bestand en voeg de volgende regel aan het einde toe:

   `<filter root="/apps/experience-league" />`
1. Sla het bestand op.

   ![xml, filter aangepaste functies](assets/custom-function-filterxml.png)

1. Bouw de nieuw gecreëerde omslag van de cliëntbibliotheek aan uw AEM milieu door de stappen te volgen die in worden gegeven [Sectie Samenstellen](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype#how-to-build).

## Aangepaste functies maken en implementeren via CRXDE{#create-add-custom-function}

Als u de nieuwste invoegtoepassing voor AEM Forms en Forms gebruikt, kunt u een aangepaste functie maken via CRXDE om de nieuwste updates van aangepaste functies te gebruiken. Voer daartoe de volgende stappen uit:

<!--![custom fuction folder structure](assets/custom-library-folder-structure.png)-->


1. Aanmelden `http://server:port/crx/de/index.jsp#`.
1. Een map maken onder de `/apps` map. Maak bijvoorbeeld een map met de naam `experience-league`.
1. Sla uw wijzigingen op.
1. Ga naar de gemaakte map en maak een knooppunt van het type `cq:ClientLibraryFolder` als `clientlibs`.
1. Naar het nieuwe ontwerp navigeren `clientlibs` en voeg de `allowProxy` en `categories` eigenschappen:

   ![Eigenschappen van Custom Library-knooppunten](/help/forms/using/assets/customlibrary-catproperties.png)

   >[!NOTE]
   >
   > U kunt elke naam opgeven in plaats van `customfunctionsdemo`.

1. Sla uw wijzigingen op.

1. Een map maken met de naam `js` onder de `clientlibs` map.
1. Een JavaScript-bestand met de naam `functions.js` onder de `js` map.
1. Een bestand maken met de naam `js.txt` onder de `clientlibs` map.
1. Sla uw wijzigingen op.
De gemaakte mapstructuur ziet er als volgt uit:

   ![Map-structuur voor clientbibliotheek gemaakt](/help/forms/using/assets/clientlibrary_folderstructure.png)
1. Dubbelklik op de knop `functions.js` te openen. Het bestand bevat de code voor een aangepaste functie.
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

1. Opslaan `function.js`.
1. Navigeren naar `js.txt` en voeg de volgende code toe:

   ```javascript
       #base=js
       functions.js
   ```

1. Sla de `js.txt` bestand.

U kunt naar het volgende verwijzen [aangepaste functie](/help/forms/using/assets/customfunction.zip) map. Download en installeer deze map op uw AEM.

Nu kunt u de aangepaste functie in het adaptieve formulier gebruiken door de clientbibliotheek toe te voegen.

## Clientbibliotheek toevoegen in een adaptief formulier{#add-client-library}

Zodra u uw clientbibliotheek hebt geïmplementeerd in uw AEM Forms-omgeving, gebruikt u de mogelijkheden ervan in uw adaptieve formulier. De clientbibliotheek toevoegen aan uw adaptieve formulier

1. Open het formulier in de bewerkingsmodus. Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Edit]**.
1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op het pictogram Eigenschappen van de container van de hulplijn. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de **[!UICONTROL Basic]** en selecteert u de naam van de **[!UICONTROL client library category]** in de vervolgkeuzelijst (in dit geval selecteert u `customfunctionscategory`).

   ![De aangepaste clientbibliotheek van de functie toevoegen](/help/forms/using//assets/custom-function-category-name-core-component.png)

1. Klik op **[!UICONTROL Done]**.

Nu, kunt u een regel tot stand brengen om douanefuncties in de regelredacteur te gebruiken:

![De aangepaste clientbibliotheek van de functie toevoegen](/help/forms/using//assets/calculateage-customfunction.png)

Nu, begrijpen hoe te om een douanefunctie te vormen en te gebruiken gebruikend [De Invoke-service van de Rule Editor in AEM Forms 6.5](/help/forms/using/rule-editor-core-components.md#invoke-form-data-model-service-invoke)

## Aangepaste functie gebruiken in een adaptief formulier {#use-custom-functions}

In een adaptief formulier kunt u [Aangepaste functies in de regeleditor](/help/forms/using/rule-editor-core-components.md).
Voeg de volgende code toe aan het JavaScript-bestand (`Function.js` bestand) om de leeftijd te berekenen op basis van de geboortedatum (JJJJ-MM-DD). Een aangepaste functie maken als `calculateAge()` die de geboortedatum als input neemt en de leeftijd retourneert:

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

In het bovenstaande voorbeeld, wanneer de gebruiker de geboortedatum in de notatie (JJJJ-MM-DD) invoert, de aangepaste functie `calculateAge` wordt aangeroepen en retourneert de leeftijd.

![Aangepaste functie Leeftijd berekenen in Regeleditor](/help/forms/using/assets/custom-function-calculate-age.png)

Bekijk een voorbeeld van het formulier om te zien hoe de aangepaste functies worden geïmplementeerd via de regeleditor:

![Aangepaste functie Leeftijd berekenen in Voorvertoning van formulier in lijn-editor](/help/forms/using/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> U kunt naar het volgende verwijzen [aangepaste functies](/help/forms/using/assets/customfunctions.zip) map. Download en installeer deze map in uw AEM [Pakketbeheer](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager).

### Ondersteuning voor asynchrone functies in aangepaste functies {#support-of-async-functions}

De asynchrone douanefuncties verschijnen niet in de lijst van de regelredacteur. Het is echter mogelijk om asynchrone functies aan te roepen binnen aangepaste functies die zijn gemaakt met synchrone functie-expressies.

![Aangepaste functies synchroniseren en asynchroon](/help/forms/using/assets/workflow-for-sync-async-custom-fumction.png)

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

In het bovenstaande voorbeeld is de functie asyncFunction een `asynchronous function`. De toepassing voert een asynchrone bewerking uit door een `GET` verzoek om `https://petstore.swagger.io/v2/store/inventory`. Het wacht op de reactie met `await`parseert de responsinstantie als JSON met behulp van de `response.json()`en retourneert vervolgens de gegevens. De `callAsyncFunction` functie is een synchrone aangepaste functie die de `asyncFunction` en geeft de reactiegegevens weer in de console. Hoewel de `callAsyncFunction` De functie is synchroon, roept de asynchrone functie asynchrone asyncFunction aan en behandelt zijn resultaat met `then` en `catch` instructies.

Om zijn het werken te zien, laten wij een knoop toevoegen en een regel voor de knoop creëren die de asynchrone functie na een knoop klikt.

![regel maken voor asynchrone functie](/help/forms/using/assets/rule-for-async-funct.png)

Verwijs naar de illustratie van het consolevenster hieronder om aan te tonen dat wanneer de gebruiker klikt `Fetch` knop, de aangepaste functie `callAsyncFunction` wordt aangeroepen, die op zijn beurt een asynchrone functie aanroept `asyncFunction`. Inspect het consolevenster om de reactie op de knoop te bekijken klikt:

![Console-venster](/help/forms/using/assets/async-custom-funct-console.png)

Laten we eens kijken naar de functies van aangepaste functies.

## Verschillende functies voor Aangepaste functies

U kunt aangepaste functies gebruiken om aangepaste functies toe te voegen aan formulieren. Deze functies ondersteunen diverse mogelijkheden, zoals het werken met specifieke velden, het gebruik van globale velden of caching. Dankzij deze flexibiliteit kunt u formulieren aanpassen aan de vereisten van uw organisatie.

### Veld- en globale bereikobjecten in aangepaste functies {#support-field-and-global-objects}

Veldobjecten verwijzen naar de afzonderlijke componenten of elementen in een formulier, zoals tekstvelden, selectievakjes. Het object Globals bevat alleen-lezen variabelen, zoals formulierinstantie, doelveldinstantie en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies.

>[!NOTE]
>
> De `param {scope} globals` moet de laatste parameter zijn en deze wordt niet weergegeven in de regeleditor van een adaptief formulier.

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

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken met behulp van een `Contact Us` formulier met verschillende gebruiksmogelijkheden.

![Contactformulier](/help/forms/using/assets/contact-us-form.png)

#### **Hoofdletters gebruiken**: Een deelvenster tonen met de opdracht `SetProperty` regel

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) in, om het formulierveld in te stellen als `Required`.

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
> * U kunt de veldeigenschappen vormen gebruikend beschikbare eigenschappen die in worden gevestigd `[form-path]/jcr:content/guideContainer.model.json`.
> * Wijzigingen in het formulier met het `setProperty` De methode van het object Globals is asynchroon van aard en wordt niet weerspiegeld tijdens de uitvoering van de aangepaste functie.

In dit voorbeeld, bevestiging van `personaldetails` wordt weergegeven wanneer u op de knop klikt. Als er geen fouten worden gedetecteerd in het deelvenster, wordt een ander deelvenster `feedback` wordt zichtbaar als u op een knop klikt.

Laten we een regel maken voor de `Next` knop, waarmee het `personaldetails` en maakt het `feedback`  wordt weergegeven wanneer de gebruiker op de knop `Next` knop.

![Eigenschap instellen](/help/forms/using/assets/custom-function-set-property.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar de `personaldetails` wordt gevalideerd als u op het `Next` knop. In het geval dat alle velden binnen de `personaldetails` worden gevalideerd, `feedback` wordt zichtbaar.

![Voorvertoning van eigenschappenformulier instellen](/help/forms/using/assets/set-property-form-preview.png)

Als er fouten voorkomen in de velden van het `personaldetails` worden deze weergegeven op veldniveau wanneer u op het tabblad `Next` en de `feedback` blijft onzichtbaar.

![Voorvertoning van eigenschappenformulier instellen](/help/forms/using/assets/set-property-panel.png)

#### **Hoofdletters gebruiken**: Valideer het veld.

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) te valideren.

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
> Als er geen argument wordt doorgegeven in het dialoogvenster `validate()` , valideert het formulier.

In dit voorbeeld wordt een aangepast validatiepatroon toegepast op de `contact` veld. Gebruikers moeten een telefoonnummer invoeren dat begint met `10` gevolgd door `8` cijfers. Als de gebruiker een telefoonaantal ingaat dat niet met begint `10` of meer of minder dan `8` cijfers, verschijnt een bericht van de bevestigingsfout wanneer de knoop klikt:

![Validatiepatroon e-mailadres](/help/forms/using/assets/custom-function-validation-pattern.png)

De volgende stap bestaat uit het maken van een regel voor de `Next` knop waarmee het `contact` veld op de knop klikken.

![Validatiepatroon](/help/forms/using/assets/custom-function-validate.png)

Verwijs naar de illustratie hieronder om aan te tonen dat als de gebruiker een telefoonaantal ingaat dat niet met begint `10`verschijnt er een foutbericht op veldniveau:

![Validatiepatroon e-mailadres](/help/forms/using/assets/custom-function-validate-error-message.png)

Als de gebruiker een geldig telefoonnummer en alle velden in het dialoogvenster `personaldetails` worden gevalideerd, `feedback` verschijnt op het scherm:

![Validatiepatroon e-mailadres](/help/forms/using/assets/validate-form-preview-form.png)

#### **Hoofdletters gebruiken**: Een deelvenster opnieuw instellen

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) om het deelvenster opnieuw in te stellen.

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
> Als er geen argument wordt doorgegeven in het dialoogvenster `reset()` , valideert het formulier.

In dit voorbeeld wordt `personaldetails` deelvenster wordt opnieuw ingesteld wanneer u op de knop `Clear` knop. De volgende stap bestaat uit het maken van een regel voor de `Clear` knop waarmee het deelvenster opnieuw wordt ingesteld op de knop klikken.

![Knop Wissen](/help/forms/using/assets/custom-function-reset-field.png)

Zie de onderstaande afbeelding om aan te geven dat als de gebruiker op de knop `clear` de `personaldetails` voorinstellingen deelvenster:

![Formulier opnieuw instellen](assets/custom-function-reset-form.png)

#### **Hoofdletters gebruiken**: Een aangepast bericht weergeven op veldniveau en het veld markeren als ongeldig

U kunt de `markFieldAsInvalid()` gebruiken om een veld als ongeldig te definiëren en een aangepast foutbericht op veldniveau in te stellen. De `fieldIdentifier` waarde kan `fieldId`, of `field qualifiedName`, of `field dataRef`. De waarde van het genoemde object `option` kan `{useId: true}`, `{useQualifiedName: true}`, of `{useDataRef: true}`.
De syntaxis die wordt gebruikt om het veld als ongeldig te markeren en een aangepast bericht in te stellen, is:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) om aangepaste berichten op veldniveau in te schakelen.

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

De volgende stap bestaat uit het maken van een regel voor de `comments` veld:

![Veld markeren als ongeldig](/help/forms/using/assets/custom-function-invalid-field.png)

Zie de onderstaande demonstratie voor het weergeven van negatieve feedback in het dialoogvenster `comments` Het veld activeert de weergave van een aangepast bericht op veldniveau:

![Veld markeren als ongeldig voorbeeldformulier](/help/forms/using/assets/custom-function-invalidfield-form.png)

Als de gebruiker meer dan 15 tekens in het tekstvak Opmerkingen invoert, wordt het veld gevalideerd en wordt het formulier verzonden:

![Veld markeren als geldig voorbeeldformulier](/help/forms/using/assets/custom-function-validfield-form.png)


#### **Hoofdletters gebruiken**: Verzenden van gewijzigde gegevens naar de server

De volgende regel code:
`globals.functions.submitForm(globals.functions.exportData(), false);` wordt gebruikt om de formuliergegevens te verzenden na manipulatie.
* Het eerste argument betreft de gegevens die moeten worden ingediend.
* Het tweede argument geeft aan of het formulier moet worden gevalideerd voordat het wordt verzonden. Het is `optional` en instellen als `true` standaard.
* Het derde argument is de `contentType` van de indiening, die ook optioneel is met de standaardwaarde als `multipart/form-data`. De andere waarden kunnen `application/json` en `application/x-www-form-urlencoded`.

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) om de gemanipuleerde gegevens op de server te verzenden:

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

In dit voorbeeld, als de gebruiker de `comments` textbox leeg, de `NA` wordt bij het verzenden van het formulier naar de server verzonden.

Maak nu een regel voor de `Submit` knop voor het verzenden van gegevens:

![Gegevens verzenden](/help/forms/using/assets/custom-function-submit-data.png)

Raadpleeg de illustratie van de `console window` om aan te tonen dat de gebruiker de `comments` textbox leeg, vervolgens de waarde als `NA` wordt verzonden op de server:

![Gegevens verzenden in het consolevenster](/help/forms/using/assets/custom-function-submit-data-form.png)

U kunt het consolevenster ook inspecteren om de gegevens te bekijken die aan de server worden voorgelegd:

![Inspect-gegevens in het consolevenster](/help/forms/using/assets/custom-function-submit-data-console-data.png)

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

De adaptieve Forms voert caching voor douanefuncties uit om reactietijd te verbeteren terwijl het terugwinnen van de lijst van de douanefunctie in de regelredacteur. Een bericht als `Fetched following custom functions list from cache` in het dialoogvenster `error.log` bestand.

![aangepaste functie met cacheondersteuning](/help/forms/using/assets/custom-function-cache-error.png)

Als de aangepaste functies worden gewijzigd, wordt het in cache plaatsen ongeldig en wordt het geparseerd.

## Problemen oplossen {#troubleshooting}

* De gebruiker moet ervoor zorgen dat de [kerncomponent en specificatieversie worden ingesteld op de nieuwste versie](https://github.com/adobe/aem-core-forms-components/tree/release/650). Voor bestaande AEM projecten en formulieren zijn echter aanvullende stappen nodig:

   * Voor het AEM project moet de gebruiker alle instanties van `submitForm('custom:submitSuccess', 'custom:submitError')` with `submitForm()` en implementeert het project.

   * Voor bestaande formulieren moet de gebruiker, als de aangepaste verzendingsafhandelingen niet correct werken, de `submitForm` de regels inzake **Verzenden** gebruiken van de Redacteur van de Regel. Deze handeling vervangt de bestaande regel door `submitForm('custom:submitSuccess', 'custom:submitError')` with `submitForm()` in het formulier.


* Als het JavaScript-bestand met code voor aangepaste functies een fout bevat, worden de aangepaste functies niet vermeld in de regeleditor van een adaptief formulier. Als u de lijst met aangepaste functies wilt controleren, navigeert u naar de `error.log` bestand voor de fout. In het geval van een fout wordt de lijst met aangepaste functies leeg weergegeven:

  ![foutenlogbestand](/help/forms/using/assets/custom-function-list-error-file.png)

  Als er geen fout optreedt, wordt de aangepaste functie opgehaald en weergegeven in het dialoogvenster `error.log` bestand. Een bericht als `Fetched following custom functions list` in het dialoogvenster `error.log` bestand:

  ![foutenlogbestand met juiste aangepaste functie](/help/forms/using/assets/custom-function-list-fetched-in-error.png)

## Overwegingen

* De `parameter type` en `return type` ondersteunen `None`.

* De functies die niet worden ondersteund in de lijst met aangepaste functies zijn:
   * Generatorfuncties
   * Functies Async/Await
   * Methodedefinities
   * Methoden van Class
   * Standaardparameters
   * Rustparameters
