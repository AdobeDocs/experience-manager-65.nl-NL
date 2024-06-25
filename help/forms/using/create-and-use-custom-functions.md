---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms,Core Components
exl-id: a328b4a8-e8dd-42a0-b73b-94e76c7692a8
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 0%

---


# Aangepaste functies in Adaptive Forms (Core Components)

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/create-and-use-custom-functions) |
| AEM 6,5 | Dit artikel |

## Inleiding

AEM Forms 6.5 introduceerde de capaciteit om functies te bepalen JavaScript die in het bepalen van complexe bedrijfsregels kunnen worden gebruikt gebruikend de regelredacteur. AEM Forms biedt een aantal van dergelijke aangepaste functies uit de verpakking, maar u hebt de behoefte om uw eigen aangepaste functies te definiëren en deze in meerdere formulieren te gebruiken.

De aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken om aan bepaalde vereisten te voldoen. Ze maken het ook mogelijk het formuliergedrag dynamisch te wijzigen op basis van vooraf gedefinieerde criteria.
In Adaptive Forms kunt u aangepaste functies gebruiken in het dialoogvenster [regel-editor van een adaptief formulier](/help/forms/using/rule-editor.md) specifieke validatieregels voor formuliervelden te maken.
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

* **Manipulatie van gegevens**: Aangepaste functies bewerken en verwerken de gegevens die in de formuliervelden zijn ingevoerd.
* **Validatie van gegevens**: Met aangepaste functies kunt u aangepaste controles uitvoeren op de invoer van formulieren en opgegeven foutberichten weergeven.
* **Dynamisch gedrag**: Met aangepaste functies kunt u het dynamische gedrag van uw formulieren bepalen op basis van specifieke omstandigheden. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt aangepaste functies gebruiken om te integreren met externe API&#39;s of services. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

## Ondersteunde JS-annotaties

Zorg ervoor dat de aangepaste functie die u schrijft, vergezeld gaat van de `jsdoc` boven het, voor het geval, hebt u douaneconfiguratie en beschrijving nodig. Er zijn meerdere manieren om een functie te declareren in `JavaScript,` Met opmerkingen kunt u de functies bijhouden. Zie voor meer informatie [usejsdoc.org](https://jsdoc.app/).

Ondersteund `jsdoc` tags:

* **Persoonlijk**
Syntaxis: `@private`
Een functie van het type private is niet opgenomen als een aangepaste functie.

* **Naam**
Syntaxis: `@name funcName <Function Name>`
Alternatief `,` u kunt gebruiken: `@function funcName <Function Name>` **of** `@func` `funcName <Function Name>`.
  `funcName` is de naam van de functie (geen spaties toegestaan).
  `<Function Name>` is de weergavenaam van de functie.

* **Lid**
Syntaxis: `@memberof namespace`
Koppelt een naamruimte aan de functie.

* **Parameter**
Syntaxis: `@param {type} name <Parameter Description>`
U kunt ook het volgende gebruiken: `@argument` `{type} name <Parameter Description>` **of** `@arg` `{type}` `name <Parameter Description>`.
Geeft parameters weer die door de functie worden gebruikt. Een functie kan meerdere parametertags hebben, één tag voor elke parameter in de volgorde waarin deze voorkomt.
  `{type}` vertegenwoordigt parametertype. Toegestane parametertypen zijn:

   1. string
   2. getal
   3. boolean
   4. bereik

  Bereik wordt gebruikt voor verwijzingen naar velden van een adaptief formulier. Wanneer in een formulier het laden is vertraagd, kunt u `scope` om de velden te openen. U kunt velden openen wanneer de velden worden geladen of als de velden algemeen zijn gemarkeerd.

  Alle andere parametertypen worden in een van de bovenstaande categorieën ingedeeld. Geen wordt niet ondersteund. Selecteer een van de bovenstaande typen. Typen zijn niet hoofdlettergevoelig. Spaties zijn niet toegestaan in de parameter `name`. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **Retourtype**
Syntaxis: `@return {type}`
U kunt ook `@returns {type}`.
Voegt informatie over de functie toe, zoals zijn doel.
{type} vertegenwoordigt het terugkeertype van de functie. Toegestane retourtypen zijn:

   1. string
   1. getal
   1. boolean

  Alle andere retourneringstypen worden in een van de bovenstaande categorieën ingedeeld. Geen wordt niet ondersteund. Selecteer een van de bovenstaande typen. Retourtypen zijn niet hoofdlettergevoelig.

* **Dit**
Syntaxis: `@this currentComponent`

  Gebruik @this om te verwijzen naar de component Adaptief formulier waarop de regel is geschreven.

  Het volgende voorbeeld is gebaseerd op de veldwaarde. In het volgende voorbeeld verbergt de regel een veld in het formulier. De `this` deel van `this.value` verwijst naar de onderliggende component Adaptief formulier waarop de regel is geschreven.

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

**Functie, instructie**

```javascript
function area(len) {
    return len*len;
}
```

Deze functie is opgenomen zonder `jsdoc` opmerkingen.

**Functie-expressie**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Functie-expressie en -instructie**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Functiedeclaratie als variabele**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Beperking: een aangepaste functie kiest alleen de eerste functiedeclaratie uit de lijst met variabelen, indien bijeengevoegd. U kunt functie-expressie gebruiken voor elke gedeclareerde functie.

**Functiedeclaratie als object**

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
1. Een JavaScript-bestand met de naam `functions.js` onder de `js` map
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

U kunt naar het volgende verwijzen [aangepaste functie](/help/forms/using/assets/customfunction.zip) map. Download en installeer deze map in uw AEM.

Nu kunt u de aangepaste functie in het adaptieve formulier gebruiken door de clientbibliotheek toe te voegen.

## Clientbibliotheek toevoegen in een adaptief formulier{#use-custom-function}

Zodra u de clientbibliotheek hebt geïmplementeerd in uw Forms CS-omgeving, gebruikt u de mogelijkheden van de clientbibliotheek in uw adaptieve formulier. De clientbibliotheek toevoegen aan uw adaptieve formulier

1. Open het formulier in de bewerkingsmodus. Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Edit]**.
1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op het pictogram Eigenschappen van de container van de hulplijn. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de **[!UICONTROL Basic]** en selecteert u de naam van de **[!UICONTROL client library category]** in de vervolgkeuzelijst (in dit geval selecteert u `customfunctionscategory`).

   ![De aangepaste clientbibliotheek van de functie toevoegen](/help/forms/using//assets/custom-function-category-name-core-component.png)

1. Klikken **[!UICONTROL Done]** .

Nu, kunt u een regel tot stand brengen om douanefuncties in de regelredacteur te gebruiken:

![De aangepaste clientbibliotheek van de functie toevoegen](/help/forms/using//assets/calculateage-customfunction.png)

Nu, begrijpen hoe te om een douanefunctie te vormen en te gebruiken gebruikend [De service Invoke van de Rule Editor in AEM Forms](/help//forms/using/rule-editor.md).
