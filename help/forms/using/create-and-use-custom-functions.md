---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
feature: Adaptive Forms, Foundation Components
role: Admin, User, Developer
exl-id: 14a52bc1-c1b4-4a12-b8e1-54523e5f30bd
source-git-commit: a0ef9925d1bcb84ea5bf733221875d0322cc6df1
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 0%

---

# Aangepaste functies in Adaptive Forms

## Inleiding

>[!NOTE]
>
> Aangepaste functies moeten compatibel zijn met ECMAScript 5 (ES5). Foundation Forms ondersteunt alleen ES5. Het gebruik van nieuwere ECMAScript-versies (ES6 en hoger) wordt niet ondersteund en kan leiden tot fouten of onverwacht gedrag.

AEM Forms 6.5 introduceerde de capaciteit om de functies van JavaScript te bepalen die in het bepalen van complexe bedrijfsregels kunnen worden gebruikt gebruikend de regelredacteur. AEM Forms biedt een aantal van dergelijke aangepaste functies uit de verpakking, maar u hebt de behoefte om uw eigen aangepaste functies te definiëren en deze in meerdere formulieren te gebruiken.

De aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken om aan bepaalde vereisten te voldoen. Ze maken het ook mogelijk het formuliergedrag dynamisch te wijzigen op basis van vooraf gedefinieerde criteria.
In Aanpassings Forms, kunt u douanefuncties binnen de [ regelredacteur van een Aangepaste Vorm ](/help/forms/using/rule-editor.md) gebruiken om specifieke bevestigingsregels voor vormgebieden tot stand te brengen.
Laten we begrijpen hoe een aangepaste functie wordt gebruikt waarbij gebruikers het e-mailadres invoeren. Bovendien moet het ingevoerde e-mailadres een specifieke notatie hebben (het bevat een &#39;@&#39;-symbool en een domeinnaam). Maak een aangepaste functie als &quot;ValidateEmail&quot;, die het e-mailadres als invoer gebruikt en waar retourneert als het geldig en anders onwaar is.

```javascript
function ValidateEmail(inputText)
{
    var email = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
    if(inputText.value.match(email))
        {
            alert("Valid email address!");
            return true;
        }
    else
    {
        alert("Invalid email address!");
        return false;
    }
}
```

In het bovenstaande voorbeeld wordt de aangepaste functie &quot;ValidateEmail&quot; aangeroepen om te controleren of het ingevoerde e-mailadres geldig is wanneer de gebruiker het formulier probeert te verzenden.

## Gebruik van aangepaste functies {#uses-of-custom-function}

De voordelen van het gebruik van aangepaste functies in Adaptive Forms zijn:

* **Manipulatie van gegevens**: De functies van de douane manipuleren en verwerken gegevens ingegaan in de vormengebieden.
* **Bevestiging van gegevens**: De functies van de douane laten u toe om douanecontroles op vorminput uit te voeren en gespecificeerde foutenmeldingen te verstrekken.
* **Dynamisch gedrag**: De functies van de douane staan u toe om het dynamische gedrag van uw vormen te controleren die op specifieke voorwaarden worden gebaseerd. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt douanefuncties gebruiken om met externe APIs of de diensten te integreren. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

## Ondersteunde JS-annotaties

Zorg ervoor dat de aangepaste functie die u schrijft, vergezeld gaat van de `jsdoc` hierboven, voor het geval dat u aangepaste configuratie en beschrijving nodig hebt. Er zijn meerdere manieren om een functie in `JavaScript,` te declareren en met opmerkingen kunt u de functies bijhouden. Voor meer informatie, zie [ usejsdoc.org ](https://jsdoc.app/).

Ondersteunde `jsdoc` -tags:

* **Privé**
Syntaxis: `@private`
Een functie van het type private is niet opgenomen als een aangepaste functie.

* **Naam**
Syntaxis: `@name funcName <Function Name>`
Alternatief `,` kunt u gebruiken: `@function funcName <Function Name>` **of** `@func` `funcName <Function Name>`.
  `funcName` is de naam van de functie (geen spaties toegestaan).
  `<Function Name>` is de weergavenaam van de functie.

* **Lid**
Syntaxis: `@memberof namespace`
Koppelt een naamruimte aan de functie.

* **Parameter**
Syntaxis: `@param {type} name <Parameter Description>`
U kunt ook het volgende gebruiken: `@argument` `{type} name <Parameter Description>` **of** `@arg` `{type}` `name <Parameter Description>` .
Geeft parameters weer die door de functie worden gebruikt. Een functie kan meerdere parametertags hebben, één tag voor elke parameter in de volgorde waarin deze voorkomt.
  `{type}` staat voor het parametertype. Toegestane parametertypen zijn:

   1. string
   2. getal
   3. boolean
   4. bereik

  Bereik wordt gebruikt voor verwijzingen naar velden van een adaptief formulier. Wanneer een formulier wazig laden gebruikt, kunt u `scope` gebruiken om de bijbehorende velden te openen. U kunt velden openen wanneer de velden worden geladen of als de velden algemeen zijn gemarkeerd.

  Alle andere parametertypen worden in een van de bovenstaande categorieën ingedeeld. Geen wordt niet ondersteund. Selecteer een van de bovenstaande typen. Typen zijn niet hoofdlettergevoelig. Spaties zijn niet toegestaan in de parameter `name` . `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **Type van Terugkeer**
Syntaxis: `@return {type}`
U kunt ook `@returns {type}` gebruiken.
Voegt informatie over de functie toe, zoals zijn doel.
  {type} staat voor het retourneringstype van de functie. Toegestane retourtypen zijn:

   1. string
   1. getal
   1. boolean

  Alle andere retourneringstypen worden in een van de bovenstaande categorieën ingedeeld. Geen wordt niet ondersteund. Selecteer een van de bovenstaande typen. Retourtypen zijn niet hoofdlettergevoelig.

* **dit**
Syntaxis: `@this currentComponent`

  Gebruik @this om te verwijzen naar de component Adaptief formulier waarop de regel is geschreven.

  Het volgende voorbeeld is gebaseerd op de veldwaarde. In het volgende voorbeeld verbergt de regel een veld in het formulier. Het `this` gedeelte van `this.value` verwijst naar de onderliggende component Adaptief formulier waarop de regel is geschreven.

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
  >Opmerkingen vóór aangepaste functie worden gebruikt voor overzicht. Samenvatting kan tot veelvoudige lijnen worden uitgebreid tot een markering wordt ontmoet. Beperk de grootte tot één voor een beknopte beschrijving in de regelbouwer.

## Ondersteunde typen functiedeclaratie {#function-declaration-supported-types}

**Verklaring van de Functie**

```javascript
function area(len) {
    return len*len;
}
```

Deze functie wordt opgenomen zonder `jsdoc` opmerkingen.

**Uitdrukking van de Functie**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Uitdrukking en Verklaring van de Functie**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Verklaring van de Functie als Variabele**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Beperking: een aangepaste functie kiest alleen de eerste functiedeclaratie uit de lijst met variabelen, indien bijeengevoegd. U kunt functie-expressie gebruiken voor elke gedeclareerde functie.

**de Verklaring van de Functie als Voorwerp**

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

## Aangepaste functie maken {#create-custom-function}

Voer de volgende stappen uit om een aangepaste functie te maken:

1. Meld u aan bij `http://server:port/crx/de/index.jsp#` .
1. Maak een map onder de map `/apps` . Maak bijvoorbeeld een map met de naam `experience-league` .
1. Sla uw wijzigingen op.
1. Navigeer naar de gemaakte map en maak een knooppunt van het type `cq:ClientLibraryFolder` as `clientlibs` .
1. Navigeer naar de nieuwe map `clientlibs` en voeg de eigenschappen `allowProxy` en `categories` toe:

   ![ de knoopeigenschappen van de Bibliotheek van de Douane ](/help/forms/using/assets/customlibrary-catproperties.png)

   >[!NOTE]
   >
   > U kunt elke naam opgeven in plaats van `customfunctionsdemo` .

1. Sla uw wijzigingen op.

1. Maak een map met de naam `js` onder de map `clientlibs` .
1. Een JavaScript-bestand met de naam `functions.js` maken in de map `js`
1. Maak een bestand met de naam `js.txt` onder de map `clientlibs` .
1. Sla uw wijzigingen op.
De gemaakte mapstructuur ziet er als volgt uit:

   ![ creeerde de Omslagstructuur van de Bibliotheek van de Cliënt ](/help/forms/using/assets/clientlibrary_folderstructure.png)
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

U kunt naar de volgende [ omslag van de douanefunctie ](/help/forms/using/assets/customfunction.zip) verwijzen. Download en installeer deze map in uw AEM-exemplaar.

Nu kunt u de aangepaste functie in het adaptieve formulier gebruiken door de clientbibliotheek toe te voegen.

## Clientbibliotheek toevoegen in een adaptief formulier{#use-custom-function}

Zodra u de clientbibliotheek hebt geïmplementeerd in uw Forms CS-omgeving, gebruikt u de mogelijkheden van de clientbibliotheek in uw adaptieve formulier. De clientbibliotheek toevoegen aan uw adaptieve formulier

1. Open het formulier in de bewerkingsmodus. Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Edit]** .
1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik op het pictogram Eigenschappen van de container van de hulplijn. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open het tabblad **[!UICONTROL Basic]** en selecteer de naam van de **[!UICONTROL client library category]** in de vervolgkeuzelijst (in dit geval selecteert u `customfunctionscategory` ).

   ![ Toevoegend de de cliëntbibliotheek van de douanefunctie ](/help/forms/using//assets/custom-function-category-name-core-component.png)

1. Klik op **[!UICONTROL Done]** .

Nu, kunt u een regel tot stand brengen om douanefuncties in de regelredacteur te gebruiken:

![ Toevoegend de de cliëntbibliotheek van de douanefunctie ](/help/forms/using//assets/calculateage-customfunction.png)

Nu, begrijpen wij hoe te om een douanefunctie te vormen en te gebruiken gebruikend de [ Invoke dienst van de Redacteur van de Regel in AEM Forms ](/help//forms/using/rule-editor.md).
