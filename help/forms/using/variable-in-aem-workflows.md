---
title: Variabelen in AEM Forms-workflows
seo-title: Variabelen in AEM Forms-workflows
description: Maak een variabele, stel een waarde voor de variabele in en gebruik deze in AEM Forms-workflowstappen.
seo-description: Maak een variabele, stel een waarde voor de variabele in en gebruik deze in AEM Forms-workflowstappen.
uuid: 634a75c4-4899-478f-9e5d-a870f5efa583
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: cbf4e35a-7905-44ab-ab68-fb443443f02d
docset: aem65
translation-type: tm+mt
source-git-commit: 252dac988c8256cf99ee8487feb937d5345ed797
workflow-type: tm+mt
source-wordcount: '2101'
ht-degree: 0%

---


# Variabelen in AEM Forms-workflows{#variables-in-aem-forms-workflows}

Een variabele in een workflowmodel is een manier om een waarde op te slaan op basis van het gegevenstype. U kunt dan de naam van de variabele in om het even welke werkschemastap gebruiken om de waarde terug te winnen die in de variabele wordt opgeslagen. U kunt veranderlijke namen ook gebruiken om uitdrukkingen te bepalen voor het nemen van verpletterende besluiten.

In AEM workflowmodellen kunt u:

* [Maak een ](../../forms/using/variable-in-aem-workflows.md#create-a-variable) variabele van een gegevenstype op basis van het gegevenstype dat u in de variabele wilt opslaan.
* [Stel een waarde voor de variabele in ](../../forms/using/variable-in-aem-workflows.md#set-a-variable) met de workflowstap Variabele instellen.
* [Gebruik de variabele ](../../forms/using/variable-in-aem-workflows.md#use-a-variable) in alle de werkschemastappen van AEM Forms om de opgeslagen waarde terug te winnen en in OF Splitsen en Goto stappen om een verpletterende uitdrukking te bepalen.

In de volgende video ziet u hoe u variabelen kunt maken, instellen en gebruiken in AEM workflowmodellen:

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_introduction_1_1.mp4)

Variabelen zijn een uitbreiding van de bestaande [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html)-interface. U kunt [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) in ECMAScript gebruiken om tot meta-gegevens toegang te hebben die gebruikend variabelen worden bewaard.

## Een variabele {#create-a-variable} maken

U maakt variabelen aan de hand van de sectie Variabelen die beschikbaar is in de assistent van het workflowmodel. AEM werkstroomvariabelen ondersteunen de volgende gegevenstypen:

* **Primitieve gegevenstypen**: Long, Double, Boolean, Date en String
* **Complexe gegevenstypen**:  [Document](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemfd/docmanager/Document.html),  [XML](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html),  [JSON](https://static.javadoc.io/com.google.code.gson/gson/2.3/com/google/gson/JsonObject.html) en Formuliergegevensmodel.

>[!NOTE]
>
>Workflows ondersteunen alleen de ISO8601-indeling voor variabelen van het type Date.

U hebt [AEM Forms add-on package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) nodig voor de gegevenstypen Document- en Formuliergegevensmodel.  Het gegevenstype ArrayList van het gebruik om veranderlijke inzamelingen tot stand te brengen. U kunt een variabele ArrayList maken voor alle primitieve en complexe gegevenstypen. Maak bijvoorbeeld een variabele ArrayList en selecteer String als subtype om meerdere tekenreekswaarden op te slaan met de variabele.

Voer de volgende stappen uit om een variabele te maken:

1. Navigeer op een AEM naar Extra ![](/help/forms/using/assets/hammer.png) > Workflow > Modellen.
1. Tik **[!UICONTROL Create]** en geef de titel en een optionele naam voor het workflowmodel op. Selecteer het model en tik **[!UICONTROL Edit]**.
1. Tik op het pictogram Variabelen dat beschikbaar is in de assistent van het workflowmodel en tik **[!UICONTROL Add Variable]**.

   ![Variabele toevoegen](assets/variables_add_variable_new.png)

1. Geef in het dialoogvenster Variabele toevoegen de naam op en selecteer het type variabele.
1. Selecteer het gegevenstype in de vervolgkeuzelijst **[!UICONTROL Type]** en geef de volgende waarden op:

   * Primitieve gegevenstype - Geef een optionele standaardwaarde voor de variabele op.
   * JSON of XML - Geef een optioneel JSON- of XML-schemapad op. Het systeem valideert het schemapad terwijl het in kaart brengen van en het opslaan van eigenschappen beschikbaar in dit schema aan een andere variabele.
   * Formuliergegevensmodel - Geef een formuliergegevensmodelpad op.
   * ArrayList - Geef een subtype op voor de verzameling.

1. Geef een optionele beschrijving voor de variabele op en tik ![done_icon](assets/done_icon.png) om de wijzigingen op te slaan. De variabele wordt weergegeven in de lijst die beschikbaar is in het linkerdeelvenster.

Houd rekening met de volgende werkwijzen wanneer u variabelen maakt:

* Maak zoveel variabelen als een workflow nodig heeft. Om databasemiddelen te besparen, moet u echter het minimale aantal vereiste variabelen gebruiken en moet u variabelen waar mogelijk opnieuw gebruiken.
* Variabelen zijn hoofdlettergevoelig. Zorg ervoor dat u in uw werkstroom naar variabelen verwijst met hetzelfde hoofdlettergebruik.
* Gebruik geen speciale tekens in de naam van een variabele

## Een variabele {#set-a-variable} instellen

Met de stap Variabele instellen kunt u de waarde van een variabele instellen en de volgorde definiëren waarin de waarden worden ingesteld. De variabele wordt ingesteld in de volgorde waarin de variabele-toewijzingen worden vermeld in de stap met de variabele-set.

Wijzigingen in waarden van variabelen zijn alleen van invloed op de instantie van het proces waarin de wijziging plaatsvindt. Wanneer bijvoorbeeld een workflow wordt gestart en variabele gegevens worden gewijzigd, hebben de wijzigingen alleen invloed op dat exemplaar van de workflow. De wijzigingen zijn niet van invloed op andere versies van de workflow die eerder zijn gestart of daarna worden gestart.

Afhankelijk van het gegevenstype van de variabele kunt u de volgende opties gebruiken om de waarde van een variabele in te stellen:

* **Letterlijk:** gebruik de optie wanneer u precies weet welke waarde u moet opgeven.

* **Expressie:** gebruik de optie wanneer de te gebruiken waarde wordt berekend op basis van een expressie. De expressie wordt gemaakt in de beschikbare expressie-editor.

* **JSON-puntnotatie:** gebruik de optie om een waarde op te halen uit een JSON- of FDM-tekstvariabele.
* **XPATH:** Gebruik de optie om een waarde van een variabele van het type XML op te halen.

* **Relatief ten opzichte van nuttige lading:** Gebruik de optie wanneer de waarde die aan variabele moet worden bewaard bij een weg met betrekking tot lading beschikbaar is.

* **Absoluut pad:** gebruik de optie wanneer de waarde die moet worden opgeslagen in de variabele beschikbaar is op een absoluut pad.

U kunt ook specifieke elementen van een variabele van het type JSON of XML bijwerken met JSON-puntnotatie of XPATH-notatie.

### Toewijzing toevoegen tussen variabelen {#add-mapping-between-variables}

Voer de volgende stappen uit om toewijzingen tussen variabelen toe te voegen:

1. Tik op de pagina voor workflowbewerking op het pictogram Stappen dat beschikbaar is in de assistent van het workflowmodel.
1. Sleep de stap **Variabele instellen** naar de werkstroomeditor en zet deze neer. Tik op de stap en selecteer ![configure_icon](assets/configure_icon.png) (Configureren).
1. Selecteer **[!UICONTROL Mapping]** > **[!UICONTROL Add Mapping]** in het dialoogvenster Variabele instellen.
1. Selecteer in de sectie **Variabele toewijzen** de variabele die u wilt opslaan, selecteer de toewijzingsmodus en geef een waarde op die u in de variabele wilt opslaan. De toewijzingsmodi variëren op basis van het type variabele.
1. Wijs meer variabelen toe om een betekenisvolle expressie te maken. Tik ![done_icon](assets/done_icon.png) om de wijzigingen op te slaan.

### Voorbeeld 1: Vraag een variabele van XML om waarde voor een koordvariabele {#example-query-an-xml-variable-to-set-value-for-a-string-variable} te plaatsen

Selecteer een variabele van het type van XML om een dossier van XML op te slaan. Vraag de variabele van XML om de waarde voor een koordvariabele voor het bezit te plaatsen beschikbaar in het dossier van XML. Gebruik **Geef XPATH op voor het veld XML variable** om de eigenschap te definiëren die in de tekenreeksvariabele moet worden opgeslagen.

In dit voorbeeld selecteert u een XML-variabele **formdata** om het bestand **cc-app.xml** op te slaan. Vraag de **formdata** variabele om de waarde voor **emailaddress** koordvariabele te plaatsen om de waarde voor **emailAddress** bezit op te slaan beschikbaar in **cc-app.xml** dossier.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/set_variable_example1.mp4 "Waarde van een variabele instellen")

### Voorbeeld 2: Een expressie gebruiken om waarde op te slaan op basis van andere variabelen {#example2}

Gebruik een expressie om de som van de variabelen te berekenen en sla het resultaat op in een variabele.

In dit voorbeeld gebruikt u de expressie-editor om een expressie te definiëren waarmee de som van **assetscost** en **balanceamount** variabelen wordt berekend en slaat u het resultaat op in **totalvalue** variable.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_expression.mp4)

## Expressieeditor {#use-expression-editor} gebruiken

U gebruikt ook expressies om de waarde van een variabele in de runtime te berekenen. Variabelen bieden een expressie-editor om expressies te definiëren.

Met de expressie-editor kunt u:

* Stel de waarde van variabelen in met behulp van andere workflowvariabelen, getallen of wiskundige expressies.
* Werkstroomvariabelen, tekenreeksen, getallen of expressies gebruiken in een wiskundige expressie
* Voeg voorwaarden toe om waarden van variabelen in te stellen.
* Operatoren toevoegen tussen voorwaarden.

![Expressieeditor](assets/variables_expression_editor_new.png)

De editor is gebaseerd op de regel voor aangepaste formulieren. De volgende wijzigingen zijn aangebracht. Regeleditor in variabelen:

* Biedt geen ondersteuning voor functies.
* Biedt geen interface voor het weergeven van een overzicht van regels
* Heeft geen code-editor.
* Hiermee wordt het in- en uitschakelen van de waarde van een object niet ondersteund.
* Hiermee wordt het instellen van de eigenschap van een object niet ondersteund.
* Het aanroepen van een webservice wordt niet ondersteund.

Zie [regel voor aangepaste formulieren](../../forms/using/rule-editor.md) voor meer informatie.

## Een variabele {#use-a-variable} gebruiken

U kunt variabelen gebruiken om input en output terug te winnen of het resultaat van een stap te bewaren. De werkstroomeditor bevat twee typen workflowstappen:

* Workflowstappen met ondersteuning voor variabelen
* Workflowstappen zonder ondersteuning voor variabelen

### Workflowstappen met ondersteuning voor variabelen {#workflow-steps-with-support-for-variables}

De stap Ga naar OF Splitsen en alle AEM Forms-workflowstappen ondersteunen variabelen.

#### OF stap {#or-split-step} splitsen

Met de indeling OR wordt een splitsing in de workflow gemaakt, waarna slechts één vertakking actief is. Met deze stap kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren. U voegt workflowstappen naar wens toe aan elke vertakking.

U kunt het verpletteren van uitdrukking voor een tak bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

U kunt variabelen gebruiken om de verpletterende uitdrukking te bepalen gebruikend de uitdrukkingsredacteur. Voor meer informatie bij het gebruiken van het verpletteren van uitdrukkingen voor OF Gesplitste stap, zie [OF stap ](/help/sites-developing/workflows-step-ref.md#or-split) Splitsen.

In dit voorbeeld, alvorens de verpletterende uitdrukking te bepalen, gebruik [example 2](../../forms/using/variable-in-aem-workflows.md#example2) om de waarde voor **totalvalue** variabele te plaatsen. Tak 1 is actief als de waarde van **totalvalue** variabele groter is dan 50000. Op dezelfde manier kunt u een regel bepalen om Tak 2 actief te maken als de waarde van **totalvalue** variabele minder dan 50000 is.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_orsplit_example.mp4)

Op dezelfde manier selecteer een externe manuscriptweg of specificeer het manuscript ECMA voor het verpletteren van uitdrukkingen om de actieve tak te evalueren. Tik **[!UICONTROL Rename Branch]** om een alternatieve naam voor de vertakking op te geven.

Zie [Een workflowmodel maken](../../forms/using/aem-forms-workflow.md#create-a-workflow-model) voor meer voorbeelden.

#### Ga naar stap {#go-to-step}

**Goto Step** staat u toe om de volgende stap in het uit te voeren werkschemamodel te specificeren, afhankelijk van het resultaat van een verpletterende uitdrukking.

Gelijkaardig aan OF de Gesplitste stap, kunt u het verpletteren van uitdrukking voor stap bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

U kunt variabelen gebruiken om de verpletterende uitdrukking te bepalen gebruikend de uitdrukkingsredacteur. Voor meer informatie bij het gebruiken van het verpletteren van uitdrukkingen voor de stap van de Ga, zie [Ga Stap](/help/sites-developing/workflows-step-ref.md#goto-step).

![Ga naar regel](assets/variables_goto_rule1_new.png)

In dit voorbeeld geeft de stap Ga naar de toepassing Creditcard controleren op als de volgende stap als de waarde voor de variabele **action** gelijk is aan **Need more info**.

Voor meer voorbeelden bij het gebruiken van regeldefinitie in de stap van het Goto, zie [Simulerend a voor lijn](/help/sites-developing/workflows-step-ref.md#simulateforloop).

#### Forms-workflowgerichte workflowstappen {#forms-workflow-centric-workflow-steps}

Alle AEM Forms-workflowstappen ondersteunen variabelen. Zie [Forms-centric workflow op OSGi](../../forms/using/aem-forms-workflow-step-reference.md) voor meer informatie.

### Workflowstappen zonder ondersteuning voor variabelen {#workflow-steps-without-support-for-variables}

U kunt [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) interface gebruiken om tot variabelen in werkschemastappen toegang te hebben die geen variabelen steunen.

#### De waarde {#retrieve-the-variable-value} van de variabele ophalen

Gebruik de volgende API&#39;s in het ECMA-script om waarden voor bestaande variabelen op te halen op basis van het gegevenstype:

| Gegevenstype variabele | API |
|---|---|
| Primitief (lang, dubbel, Boolean, datum en tekenreeks) | workItem.getWorkflowData().getMetaDataMap().get(variableName, type) |
| Document | Packages.com.adobe.aemfd.docmanager.Document = workItem.getWorkflowData().getMetaDataMap().get(&quot;docVar&quot;, Packages.com.adobe.aemfd.docmanager.Document.class); |
| XML | Packages.org.w3c.dom.Document xmlObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.org.w3c.dom.Document.class); |
| Formuliergegevensmodel | Packages.com.adobe.name.dermis.api.FormDataModelInstance fdmObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.adobe.aem.dermis.api.FormDataModelInstance.class); |
| JSON | Packages.com.google.get.JsonObject jsonObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.google.gson.JsonObject.class); |

U hebt [AEM Forms add-on package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) nodig voor de gegevenstypen van de variabelen Document and Form Data Model.

**Voorbeeld**

Hiermee wordt de waarde van het gegevenstype String opgehaald met de volgende API:

```javascript
workItem.getWorkflowData().getMetaDataMap().get(accname, Packages.java.lang.String)
```

#### Waarde variabele {#update-the-variable-value} bijwerken

Gebruik de volgende API in het ECMA-script om de waarde van een variabele bij te werken:

```javascript
workItem.getWorkflowData().getMetaDataMap().put(variableName, value)
```

**Voorbeeld**

```javascript
workItem.getWorkflowData().getMetaDataMap().put(salary, 50000)
```

werkt de waarde voor **salary** variabele aan 50000 bij.

### Variabelen instellen om workflows {#apiinvokeworkflow} aan te roepen

U kunt een API gebruiken om variabelen in te stellen en door te geven om workflowinstanties aan te roepen.

[workflowSession.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html#startWorkflow-com.adobe.granite.workflow.model.WorkflowModel-com.adobe.granite.workflow.exec.WorkflowData-java.util.Map-) startWorkflowuses model, wfData en metaData als argumenten. Gebruik MetaDataMap om de waarde voor de variabele in te stellen.

In deze API wordt de **variableName** variabele geplaatst aan **value** gebruikend metaData.put(variableName, value);

```javascript
import com.adobe.granite.workflow.model.WorkflowModel;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import com.adobe.aemfd.docmanager.Document;

/*Assume that you already have a workflowSession and modelId along with the payloadType and payload*/
WorkflowData wfData = workflowSession.newWorkflowData(payloadType, payload);
MetaDataMap metaData = wfData.getMetaDataMap();
metaData.put(variableName, value); //Create a variable "variableName" in your workflow model
WorkflowModel model = workflowSession.getModel(modelId);
workflowSession.startWorkflow(model, wfData, metaData);
```

**Voorbeeld**

Initialiseer het **doc**-documentobject naar een pad (&quot;a/b/c&quot;) en stel de waarde van de variabele **docVar** in op het pad dat is opgeslagen in het documentobject.

```javascript
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.WorkflowData;
import com.adobe.granite.workflow.model.WorkflowModel;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import com.adobe.aemfd.docmanager.Document;

/*This example assumes that you already have a workflowSession and modelId along with the payloadType and payload */
WorkflowData wfData = workflowSession.newWorkflowData(payloadType, payload);
MetaDataMap metaData = wfData.getMetaDataMap();
Document doc = new Document("/a/b/c");// initialize a document object
metaData.put("docVar",doc); //Assuming that you have created a variable "docVar" of type Document in your workflow model
WorkflowModel model = workflowSession.getModel(modelId);
workflowSession.startWorkflow(model, wfData, metaData);
```

## Een variabele {#edit-a-variable} bewerken

1. Tik op de pagina voor de bewerkingsworkflow op het pictogram Variabelen in de assistent van het workflowmodel. In het gedeelte Variabelen in het linkerdeelvenster worden alle bestaande variabelen weergegeven.
1. Tik op het pictogram ![edit](assets/edit.png) (Edit) naast de variabelenaam die u wilt bewerken.
1. Bewerk de variabelegegevens en tik ![done_icon](assets/done_icon.png) om de wijzigingen op te slaan. U kunt de velden **[!UICONTROL Name]** en **[!UICONTROL Type]** voor een variabele niet bewerken.

## Een variabele {#delete-a-variable} verwijderen

Voordat u de variabele verwijdert, verwijdert u alle referenties van de variabele uit de workflow. Zorg ervoor dat de variabele niet in de workflow wordt gebruikt.

Voer de volgende stappen uit om een variabele te verwijderen:

1. Tik op de pagina voor de bewerkingsworkflow op het pictogram Variabelen in de assistent van het workflowmodel. In het gedeelte Variabelen in het linkerdeelvenster worden alle bestaande variabelen weergegeven.
1. Tik op het pictogram Verwijderen naast de naam van de variabele die u wilt verwijderen.
1. Tik ![done_icon](assets/done_icon.png) om de variabele te bevestigen en te verwijderen.

## Verwijzingen {#references}

Raadpleeg [Variabelen in AEM workflows](https://helpx.adobe.com/experience-manager/kt/forms/using/authoring_variables_in_aem_forms-workflow1.html) voor meer voorbeelden over het gebruik van variabelen in AEM Forms-workflowstappen.
