---
title: API's voor toegang tot lettervarianten
description: API's detecteren en deze gebruiken om via programmacode toegang te krijgen tot letterinstanties in de AEM Forms-omgeving.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: 9d43d9d4-5487-416c-b641-e807227ac056
source-git-commit: 68a1edf5f62d7a988094fceb3f762504711dc2f1
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# API&#39;s voor toegang tot lettervarianten {#apis-to-access-letter-instances}

## Overzicht {#overview}

Met behulp van de interface Correspondentie maken van Correspondentiebeheer kunt u concepten van lopende letterinstanties opslaan en er zijn verzonden letterinstanties.

Het Beheer van de correspondentie voorziet u van APIs gebruiken die u de lijstinterface kunt bouwen om met voorgelegde brievenexemplaren of concepten te werken. De APIs lijst en open voorgelegde en ontwerp brieveninstanties van een agent, zodat de agent kon blijven werkend aan het ontwerp of voorgelegde brieveninstanties.

## Lettervarianten ophalen {#fetching-letter-instances}

Het Beheer van de correspondentie stelt APIs bloot om brieveninstanties door de dienst te halen LetterInstanceService.

| Methode | Beschrijving |
|--- |--- |
| getAllLetterInstances | Hiermee worden letterinstanties opgehaald op basis van de parameter voor invoerquery. Als u alle lettertypen wilt ophalen, geeft u de queryparameter door als null. |
| getLetterInstance | Hiermee wordt de opgegeven letter opgehaald op basis van letter-instantie-ID. |
| letterInstanceExists | Controleert of een LetterInstance door de opgegeven naam bestaat. |

>[!NOTE]
>
>LetterInstanceService is een dienst OSGI en zijn instantie kan worden teruggewonnen door @Reference in Klasse Java™ of sling.getService (LetterInstanceService) te gebruiken. Klasse ) in JSP.

### getAllLetterInstances gebruiken {#using-nbsp-getallletterinstances}

De volgende API vindt de brieveninstanties die op het vraagvoorwerp (zowel Voorgelegd als Ontwerp) worden gebaseerd. Als het queryobject null is, worden alle lettervarianten geretourneerd. Deze API retourneert een lijst met [LetterInstanceVO](https://helpx.adobe.com/aem-forms/6-2/javadocs/com/adobe/icc/dbforms/obj/LetterInstanceVO.html) objecten, die kunnen worden gebruikt voor het ophalen van aanvullende informatie over de letter.

**Syntaxis**: `List getAllLetterInstances(Query query) throws ICCException;`

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>query</td>
   <td>De queryparameter wordt gebruikt om een instantie Letter te zoeken/filteren. Hier ondersteunt de query alleen kenmerken/eigenschappen op hoofdniveau van het object. De vraag bestaat uit verklaringen en "attributeName"die in het voorwerp van de Verklaring wordt gebruikt zou de naam van het bezit in het de instantievoorwerp van de Brief moeten zijn.<br /> </td>
  </tr>
 </tbody>
</table>

#### Voorbeeld 1: alle lettervarianten van het type SUBMITTED ophalen {#example-fetch-all-the-letter-instances-of-type-submitted}

De volgende code retourneert de lijst met verzonden lettervarianten. Als u alleen concepten wilt ophalen, wijzigt u de instelling `LetterInstanceType.COMPLETE.name()` tot `LetterInstanceType.DRAFT.name().`

```java
@Reference
LetterInstanceService letterInstanceService;
Query query = new Query();

List<LetterInstanceVO> submittedLetterInstances = new ArrayList<LetterInstanceVO>();

Statement statementForInstanceType = new Statement();
statementForInstanceType.setAttributeName("letterInstanceType");
statementForInstanceType.setOperator(Operator.EQUALS);
statementForInstanceType.setAttributeValue(LetterInstanceType.COMPLETE.name());
query.addStatement(statementForInstanceType);
submittedLetterInstances = letterInstanceService.getAllLetterInstances(query);
```

#### Voorbeeld 2: Alle letterinstanties ophalen die door een gebruiker zijn ingediend en het type letter-instantie is DRAFT {#example-nbsp-fetch-all-the-letter-instances-submitted-by-a-user-and-letter-instance-type-is-draft}

De volgende code heeft veelvoudige verklaringen in de zelfde vraag om de resultaten te krijgen gefilterd op verschillende criteria zoals brieveninstantie die (attribuut door wordt voorgelegd) door een gebruiker wordt voorgelegd en het type van letterInstanceType is CONCFT.

```java
@Reference
LetterInstanceService letterInstanceService;

String submittedBy = "tglodman";
Query query = new Query();

List<LetterInstanceVO> submittedLetterInstances = new ArrayList<LetterInstanceVO>();

Statement statementForInstanceType = new Statement();
statementForInstanceType.setAttributeName("letterInstanceType");
statementForInstanceType.setOperator(Operator.EQUALS);
statementForInstanceType.setAttributeValue(LetterInstanceType.COMPLETE.name());
query.addStatement(statementForInstanceType);

Statement statementForSubmittedBy = new Statement();
statementForSubmittedBy .setAttributeName("submittedby");
statementForSubmittedBy .setOperator(Operator.EQUALS);
statementForSubmittedBy .setAttributeValue(submittedBy);
query.addStatement(statementForSubmittedBy );
submittedLetterInstances = letterInstanceService.getAllLetterInstances(query);
```

### getLetterInstance gebruiken {#using-nbsp-getletterinstance}

Haal de letter-instantie op die wordt aangegeven door de opgegeven letter-instantie-id. De waarde wordt null geretourneerd als de instantie-id niet overeenkomt.

**Syntaxis:** `public LetterInstanceVO getLetterInstance(String letterInstanceId) throws ICCException;`

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceId = "/content/apps/cm/letterInstances/1001/sampleLetterInstance";
LetterInstanceVO letterInstance = letterInstanceService.getLetterInstance(letterInstanceId );
```

### Controleren of LetterInstance bestaat {#verifying-if-letterinstance-exist}

Controleren of een instantie Letter bestaat met de opgegeven naam

**Syntaxis**: `public Boolean letterInstanceExists(String letterInstanceName) throws ICCException;`

| **Parameter** | **Beschrijving** |
|---|---|
| letterInstanceName | Naam van de instantie letter die u wilt controleren of deze bestaat. |

```java
@Reference
LetterInstanceService letterInstanceService;
String letterInstanceName = "sampleLetterInstance";
Boolean result = letterInstanceService.letterInstanceExists(letterInstanceName );
```

## Lettertypen openen {#opening-letter-instances}

Instantie letter kan van het type Verzonden of Concept zijn. Wanneer u beide lettertypen opent, worden verschillende gedragingen getoond:

* In het geval van een Ingediende letter wordt een PDF geopend die de letter vertegenwoordigt. De ingediende instantie van de Brief die op de server wordt voortgeduurd bevat ook dataXML &amp; verwerkte XDP, die kan worden gebruikt om een geval te verwezenlijken en verder te gebruiken zoals het creëren van een PDF/A.
* In het geval van een Conceptbrief-instantie wordt de aanmaakcorrespondentie-UI opnieuw geladen naar de exacte vorige status zoals deze was tijdens het maken van het concept

### Lettertypeinstantie concept openen  {#opening-draft-letter-instance-nbsp}

CCR UI steunt de parameter cmLetterInstanceId, die kan worden gebruikt om brief opnieuw te laden.

`https://[hostName]:[portNo]/[contextPath]//aem/forms/createcorrespondence.html?random=[randomNo]&cmLetterInstanceId=[letterInstanceId]`

>[!NOTE]
>
U hoeft de CMLetterId of cmLetterName/State/Version niet op te geven wanneer u een correspondentie opnieuw laadt, aangezien de verzonden gegevens al alle details bevatten over de correspondentie die opnieuw wordt geladen. RandomNo wordt gebruikt om browser geheim voorgeheugenkwesties te vermijden, kunt u een timestamp als willekeurig aantal gebruiken.

### Ingediende brief openen {#opening-submitted-letter-instance}

Verzonden PDF kan rechtstreeks worden geopend met de letter-instantie-id:

`https://[hostName]:[portNo]/[contextPath]/[letterInstanceId]`
