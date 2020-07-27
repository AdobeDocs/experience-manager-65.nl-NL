---
title: Aangepaste formulieren maken met JSON-schema
seo-title: Aangepaste formulieren maken met JSON-schema
description: Adaptieve formulieren kunnen het JSON-schema als formuliermodel gebruiken, zodat u bestaande JSON-schema's kunt gebruiken om adaptieve formulieren te maken.
seo-description: Adaptieve formulieren kunnen het JSON-schema als formuliermodel gebruiken, zodat u bestaande JSON-schema's kunt gebruiken om adaptieve formulieren te maken.
uuid: bdeaeae8-65a3-4c46-b27d-fe68481e31f1
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 375ba8fc-3152-4564-aec5-fcff2a95cf4c
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 2%

---


# Aangepaste formulieren maken met JSON-schema{#creating-adaptive-forms-using-json-schema}

## Vereisten {#prerequisites}

Voor het ontwerpen van een adaptief formulier met behulp van een JSON-schema als formuliermodel is basiskennis van JSON-schema vereist. Het wordt aanbevolen de volgende inhoud vóór dit artikel te lezen.

* [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md)
* [JSON Schema](https://json-schema.org/)

## Een JSON-schema gebruiken als formuliermodel  {#using-a-json-schema-as-form-model}

AEM Forms ondersteunen het maken van een adaptief formulier met een bestaand JSON-schema als formuliermodel. Dit JSON-schema vertegenwoordigt de structuur waarin gegevens worden geproduceerd of verbruikt door het back-end systeem in uw organisatie. Het JSON-schema dat u gebruikt, moet voldoen aan de [v4-specificaties](https://json-schema.org/draft-04/schema).

De belangrijkste kenmerken van het gebruik van een JSON-schema zijn:

* De structuur van JSON wordt als een structuur weergegeven op het tabblad Inhoudszoeker in de ontwerpmodus voor een adaptief formulier. U kunt elementen slepen van de JSON-hiërarchie naar het aangepaste formulier.
* U kunt het formulier vooraf invullen met JSON dat voldoet aan het bijbehorende schema.
* Bij verzending worden de gegevens die door de gebruiker zijn ingevoerd, verzonden als JSON die wordt uitgelijnd met het bijbehorende schema.

Een JSON-schema bestaat uit eenvoudige en complexe elementtypen. De elementen hebben attributen die regels aan het element toevoegen. Wanneer deze elementen en kenmerken naar een adaptief formulier worden gesleept, worden ze automatisch toegewezen aan de bijbehorende adaptieve formuliercomponent.

Deze toewijzing van JSON-elementen met adaptieve formuliercomponenten is als volgt:

```json
"birthDate": {
              "type": "string",
              "format": "date",
              "pattern": "date{DD MMMM, YYYY}",
              "aem:affKeyword": [
                "DOB",
                "Date of Birth"
              ],
              "description": "Date of birth in DD MMMM, YYYY",
              "aem:afProperties": {
                "displayPictureClause": "date{DD MMMM, YYYY}",
                "displayPatternType": "date{DD MMMM, YYYY}",
                "validationPatternType": "date{DD MMMM, YYYY}",
                "validatePictureClause": "date{DD MMMM, YYYY}",
                "validatePictureClauseMessage": "Date must be in DD MMMM, YYYY format."
              }
```

<table>
 <tbody>
  <tr>
   <th><strong>JSON-element, -eigenschappen of -kenmerken</strong></th>
   <th><strong>Aangepast formulieronderdeel</strong></th>
  </tr>
  <tr>
   <td><p>Tekenreekseigenschappen met de beperking enum en enumNames.</p> <p>Syntaxis,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td>
   <td><p>Onderdeel vervolgkeuzelijst:</p>
    <ul>
     <li>Waarden die worden vermeld in enumNames, worden weergegeven in het keuzemenu.</li>
     <li>Waarden die in de opsomming staan, worden gebruikt voor de berekening.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Tekenreekseigenschap met indelingsbeperking. Bijvoorbeeld e-mail en datum.</p> <p>Syntaxis,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td>
   <td>
    <ul>
     <li>E-mailcomponent wordt toegewezen wanneer het type tekenreeks en indeling e-mail is.</li>
     <li>TextBox-component met validatie wordt toegewezen wanneer het type tekenreeks en notatie hostnaam is.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>{</p> <p>"type": "string",</p> <p>}</p> </td>
   <td><br /> <br /> Tekstveld<br /> <br /> <br /> </td>
  </tr>
  <tr>
   <td>number, eigenschap<br /> </td>
   <td>Numeriek veld met subtype ingesteld op zwevend<br /> </td>
  </tr>
  <tr>
   <td>integer, eigenschap<br /> </td>
   <td>Numeriek veld met subtype ingesteld op geheel getal<br /> </td>
  </tr>
  <tr>
   <td>boolean, eigenschap<br /> </td>
   <td>Switch<br /> </td>
  </tr>
  <tr>
   <td>objecteigenschap<br /> </td>
   <td>Deelvenster<br /> </td>
  </tr>
  <tr>
   <td>array, eigenschap</td>
   <td>Herhaalbaar deelvenster met min en max. gelijk aan minItems respectievelijk maxItems. Alleen homogene arrays worden ondersteund. De itembeperking moet dus een object zijn en geen array.<br /> </td>
  </tr>
 </tbody>
</table>

### Algemene schemaeigenschappen {#common-schema-properties}

Het adaptieve formulier gebruikt informatie die beschikbaar is in het JSON-schema om elk gegenereerd veld in kaart te brengen. Met name:

* De eigenschap title fungeert als label voor de adaptieve formuliercomponenten.
* De eigenschap description wordt ingesteld als lange beschrijving voor een adaptieve formuliercomponent.
* De standaardeigenschap fungeert als de beginwaarde van een adaptief formulierveld.
* De eigenschap maxLength wordt ingesteld als het kenmerk maxlength van de tekstveldcomponent.
* De eigenschappen minimum, maximum, ExclusiveMinimum en ExclusiveMaximum worden gebruikt voor de component Numeric box.
* Als u een bereik voor de component DatePicker wilt ondersteunen, worden aanvullende JSON-schemaeigenschappen minDate en maxDate opgegeven.
* De eigenschappen minItems en maxItems worden gebruikt om het aantal items/velden te beperken dat kan worden toegevoegd aan of verwijderd uit een deelvenstercomponent.
* Met de eigenschap readOnly wordt het kenmerk Alleen-lezen van een adaptieve formuliercomponent ingesteld.
* De vereiste eigenschap markeert het adaptieve formulierveld als verplicht, terwijl in het geval van een paneel (waarbij type object is) de uiteindelijke JSON-gegevens velden hebben met een lege waarde die overeenkomt met dat object.
* De eigenschap pattern wordt ingesteld als het validatiepatroon (reguliere expressie) in adaptieve vorm.
* De extensie van het JSON-schemabestand moet .schema.json blijven. Bijvoorbeeld &lt;filename>.schema.json.

## Voorbeeld JSON-schema {#sample-json-schema}

Hier is een voorbeeld van een JSON-schema.

```json
{
 "$schema": "https://json-schema.org/draft-04/schema#",
 "definitions": {
  "employee": {
   "type": "object",
   "properties": {
    "userName": {
     "type": "string"
    },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
     "type": "string",
     "format": "email"
    },
    "language": {
     "type": "string"
    },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
    },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
   },
   "required": [
    "userName",
    "dateOfBirth",
    "language"
   ]
  },
  "personalDetails": {
   "type": "object",
   "properties": {
    "GeneralDetails": {
     "$ref": "#/definitions/GeneralDetails"
    },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "projectDetails": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```

### Herbruikbare schemadefinities {#reusable-schema-definitions}

De sleutels van de definitie worden gebruikt om herbruikbare schema&#39;s te identificeren. De herbruikbare schemadefinities worden gebruikt om fragmenten tot stand te brengen. Het is gelijkaardig aan het identificeren van complexe types in XSD. Hieronder volgt een voorbeeld van een JSON-schema met definities:

```json
{
  "$schema": "https://json-schema.org/draft-04/schema#",

  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },

  "type": "object",

  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

In het bovenstaande voorbeeld wordt een klantrecord gedefinieerd, waarbij elke klant zowel een verzendadres als een factuuradres heeft. De structuur van beide adressen is zelfde-adressen heeft een straatadres, een stad en een staat— zodat is het een goed idee om de adressen niet te dupliceren. Het maakt het toevoegen en schrappen van gebieden voor om het even welke toekomstige veranderingen gemakkelijk.

## Velden vooraf configureren in JSON-schemadefinitie {#pre-configuring-fields-in-json-schema-definition}

Met de eigenschap **aem:afProperties** kunt u het JSON-schemaveld vooraf configureren en toewijzen aan een aangepaste formuliercomponent. Hieronder ziet u een voorbeeld:

```json
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

## Scripts of expressies configureren voor formulierobjecten  {#configure-scripts-or-expressions-for-form-objects}

JavaScript is de expressietaal van adaptieve formulieren. Alle expressies zijn geldige JavaScript-expressies en gebruiken API&#39;s van het scriptmodel voor aangepaste formulieren. U kunt formulierobjecten vooraf configureren om een expressie [op een formuliergebeurtenis te](../../forms/using/adaptive-form-expressions.md) evalueren.

Met de eigenschap aaem:afproperties kunt u aangepaste formulierexpressies of scripts vooraf configureren voor adaptieve formuliercomponenten. Wanneer bijvoorbeeld de gebeurtenis initialize wordt geactiveerd, stelt de onderstaande code de waarde van het telefoonveld in en drukt een waarde af op het logbestand:

```json
"telephone": {
  "type": "string",
  "pattern": "/\\d{10}/",
  "aem:affKeyword": ["phone", "telephone","mobile phone", "work phone", "home phone", "telephone number", "telephone no", "phone number"],
  "description": "Telephone Number",
  "aem:afProperties" : {
    "sling:resourceType" : "fd/af/components/guidetelephone",
    "guideNodeClass" : "guideTelephone",
    "events": {
      "Initialize" : "this.value = \"1234567890\"; console.log(\"ef:gh\") "
    }
  }
}
```

U moet lid zijn van de gebruikersgroep [voor](/help/forms/using/forms-groups-privileges-tasks.md) formulieren om scripts of expressies voor formulierobjecten te configureren. In de onderstaande tabel staan alle scriptgebeurtenissen die worden ondersteund voor een adaptieve formuliercomponent.

<table>
 <tbody>
  <tr>
   <th><strong></strong>Component \ Event</th>
   <th>initialize <br /> </th>
   <td>Berekenen</td>
   <td>Zichtbaarheid</td>
   <td>Valideren</td>
   <td>Ingeschakeld</td>
   <td>Waarde vastleggen</td>
   <td>Klik op </td>
   <td>Opties</td>
  </tr>
  <tr>
   <td>Tekstveld</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeriek veld</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numerieke stap</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Keuzerondje</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Telefoon</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Overschakelen</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Knop</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
  </tr>
  <tr>
   <td>Selectievakje</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Vervolgkeuzelijst</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Afbeeldingskeuze</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Datuminvoerveld</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Datumkiezer</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>E-mail</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Bestandsbijlage</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Afbeelding</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Tekenen</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Deelvenster</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Sommige voorbeelden van het gebruik van gebeurtenissen in een JSON verbergen een gebied bij initialize gebeurtenis en vormen waarde van een ander gebied bij waarde begaan gebeurtenis. Zie [Aangepaste formulierexpressies](../../forms/using/adaptive-form-expressions.md)voor gedetailleerde informatie over het maken van expressies voor scriptgebeurtenissen.

Hier volgt een voorbeeld van de JSON-code voor bovengenoemde voorbeelden.

### Veld verbergen bij initialisatiegebeurtenis {#hiding-a-field-on-initialize-event}

```json
"name": {
    "type": "string",
    "aem:afProperties": {
        "events" : {
            "Initialize" : "this.visible = false;"
        }
    }
}
```

#### Waarde van een ander veld configureren bij gebeurtenis value commit {#configure-value-of-another-field-on-value-commit-event}

```json
"Income": {
    "type": "object",
    "properties": {
        "monthly": {
            "type": "number",
            "aem:afProperties": {
                "events" : {
                    "Value Commit" : "IncomeYearly.value = this.value * 12;"
                }
            }
        },
        "yearly": {
            "type": "number",
            "aem:afProperties": {
                "name": "IncomeYearly"
            }
        }
    }
}
```

## Acceptabele waarden voor een adaptieve formuliercomponent beperken {#limit-acceptable-values-for-an-adaptive-form-component}

U kunt de volgende beperkingen toevoegen aan JSON-schemaelementen om de waarden te beperken die acceptabel zijn voor een adaptieve formuliercomponent:

<table>
 <tbody>
  <tr>
   <td><p><strong> Schema, eigenschap</strong></p> </td>
   <td><p><strong>Gegevenstype</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
   <td><p><strong>Component</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>maximum</code></p> </td>
   <td><p>Tekenreeks</p> </td>
   <td><p>Hiermee geeft u de bovengrens voor numerieke waarden en datums op. Standaard wordt de maximumwaarde opgenomen.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap<br /> </li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minimum</code></p> </td>
   <td><p>Tekenreeks</p> </td>
   <td><p>Hiermee geeft u de ondergrens voor numerieke waarden en datums op. Standaard wordt de minimumwaarde opgenomen.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMaximum</code></p> </td>
   <td><p>Boolean</p> </td>
   <td><p>Indien waar (true), moet de numerieke waarde of datum die in de component van het formulier is opgegeven, kleiner zijn dan de numerieke waarde of datum die voor de eigenschap maximum is opgegeven.</p> <p>Indien onwaar, moet de numerieke waarde of datum die in de component van de vorm wordt gespecificeerd minder dan of gelijk aan de numerieke waarde of de datum zijn die voor het maximumbezit wordt gespecificeerd.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMinimum</code></p> </td>
   <td><p>Boolean</p> </td>
   <td><p>Indien waar (true), moet de numerieke waarde of datum die in de component van het formulier is opgegeven, groter zijn dan de numerieke waarde of datum die voor de eigenschap minimum is opgegeven.</p> <p>Indien onwaar, moet de numerieke waarde of datum die in de component van de vorm wordt gespecificeerd groter zijn dan of gelijk aan de numerieke waarde of de datum die voor het minimumbezit wordt gespecificeerd.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minLength</code></p> </td>
   <td><p>Tekenreeks</p> </td>
   <td><p>Hiermee wordt het minimale aantal tekens opgegeven dat in een component is toegestaan. De minimumlengte moet gelijk zijn aan of groter zijn dan nul.</p> </td>
   <td>
    <ul>
     <li>Tekstvak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxLength</code></td>
   <td>Tekenreeks</td>
   <td>Hiermee wordt het maximale aantal tekens opgegeven dat in een component is toegestaan. De maximumlengte moet gelijk zijn aan of groter zijn dan nul.</td>
   <td>
    <ul>
     <li>Tekstvak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>Tekenreeks</p> </td>
   <td><p>Hiermee geeft u de volgorde van de tekens op. Een component accepteert de tekens als de tekens overeenkomen met het opgegeven patroon.</p> <p>De eigenschap pattern verwijst naar het validatiepatroon van de overeenkomstige adaptieve formuliercomponent.</p> </td>
   <td>
    <ul>
     <li>Alle componenten voor adaptieve formulieren die zijn toegewezen aan een XSD-schema </li>
    </ul> </td>
  </tr>
  <tr>
   <td>maxItems</td>
   <td>Tekenreeks</td>
   <td>Geeft het maximale aantal items in een array op. De maximale items moeten gelijk zijn aan of groter zijn dan nul.</td>
   <td> </td>
  </tr>
  <tr>
   <td>minItems</td>
   <td>Tekenreeks</td>
   <td>Geeft het minimale aantal items in een array op. De minimale items moeten gelijk zijn aan of groter zijn dan nul.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Niet-ondersteunde constructies  {#non-supported-constructs}

De volgende JSON-schemaconstructies worden niet ondersteund door adaptieve formulieren:

* Null-tekst
* Unietypen zoals alle, en
* OneOf, anyOf, allOf, and not
* Alleen homogene arrays worden ondersteund. De itembeperking moet dus een object zijn en geen array.

## Veelgestelde vragen {#frequently-asked-questions}

**Waarom kan ik geen afzonderlijke elementen van een subformulier (structuur gegenereerd van een complex type) slepen voor herhaalbare subformulieren (waarden voor minOccurs of maxOccurs zijn groter dan 1)?**

In een herhaalbaar subformulier moet u het volledige subformulier gebruiken. Als u alleen selectieve velden wilt, gebruikt u de volledige structuur en verwijdert u de ongewenste velden.

**Ik heb een lange complexe structuur in de Inhoudszoeker. Hoe kan ik een specifiek element vinden?**

U hebt twee opties:

* Door de boomstructuur schuiven
* Gebruik het vak Zoeken om een element te zoeken

**Wat moet de extensie van het JSON-schemabestand zijn?**

De extensie van het JSON-schemabestand moet .schema.json zijn. Bijvoorbeeld &lt;filename>.schema.json.
