---
title: Variabelen in AEM Forms-workflows
description: Maak een variabele, stel een waarde voor de variabele in en gebruik deze in AEM Forms Workflow-stappen.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: beb2b83e-e8db-40bb-915f-cb6ba3140947
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 704a815e961dc2c690e034a1b1cbe60800c643ae
workflow-type: tm+mt
source-wordcount: '2075'
ht-degree: 0%

---

# Variabelen in AEM Forms-workflows{#variables-in-aem-forms-workflows}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/variable-in-aem-workflows.html) |
| AEM 6.5 | Dit artikel |

Een variabele in een workflowmodel is een manier om een waarde op te slaan op basis van het gegevenstype. U kunt dan de naam van de variabele in om het even welke werkschemastap gebruiken om de waarde terug te winnen die in de variabele wordt opgeslagen. U kunt veranderlijke namen ook gebruiken om uitdrukkingen te bepalen voor het nemen van verpletterende besluiten.

In AEM-workflowmodellen kunt u het volgende doen:

* [ creeer een variabele ](../../forms/using/variable-in-aem-workflows.md#create-a-variable) van een gegevenstype dat op het informatietype wordt gebaseerd dat u in het wilt opslaan.
* [ plaats een waarde voor de variabele ](../../forms/using/variable-in-aem-workflows.md#set-a-variable) gebruikend de Vastgestelde Veranderlijke werkschemastap.
* [ gebruik veranderlijk ](../../forms/using/variable-in-aem-workflows.md#use-a-variable) in alle stappen van het Werkschema van AEM Forms om de opgeslagen waarde en in OF te winnen Splitsen en gaan stappen om een verpletterende uitdrukking te bepalen.

In de volgende video ziet u hoe u variabelen kunt maken, instellen en gebruiken in AEM-workflowmodellen:

<!-- FUTURE ERROR: YouTube and mp4 videos are not supported -->

[ de inleidende video van Variabelen ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_introduction_1_1.mp4)

De variabelen zijn een uitbreiding van de bestaande [ MetaDataMap ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) interface. U kunt [ MetaDataMap ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) in ECMAScript gebruiken om tot meta-gegevens toegang te hebben die gebruikend variabelen worden bewaard.

## Een variabele maken {#create-a-variable}

U maakt variabelen aan de hand van de sectie Variabelen die beschikbaar is in de assistent van het workflowmodel. AEM-workflowvariabelen ondersteunen de volgende gegevenstypen:

* **Primitieve gegevenstypes**: Lang, Dubbel, Van Boole, Datum, en Koord
* **Complexe gegevenstypes**: [ Document ](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemfd/docmanager/Document.html), [ XML ](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html), [ JSON ](https://static.javadoc.io/com.google.code.gson/gson/2.3/com/google/gson/JsonObject.html), en de Modelinstantie van Gegevens van de Vorm.

>[!NOTE]
>
>Workflows ondersteunen alleen de ISO8601-indeling voor variabelen van het type Date.

U vereist [ toe:voegen-op pakket van AEM Forms ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) voor de gegevenstypes van het Model van Document en van de Gegevens van de Vorm.  Gebruik het gegevenstype ArrayList om variabele verzamelingen te maken. U kunt een variabele ArrayList maken voor alle primitieve en complexe gegevenstypen. Maak bijvoorbeeld een variabele ArrayList en selecteer String als subtype om meerdere tekenreekswaarden op te slaan met de variabele.

Voer de volgende stappen uit om een variabele te maken:

1. Voor een instantie van AEM, navigeer aan Hulpmiddelen ![ ](/help/forms/using/assets/hammer.png) > Werkschema > Modellen.
1. Selecteer **[!UICONTROL Create]** en geef de titel en een optionele naam voor het workflowmodel op. Selecteer het model en selecteer **[!UICONTROL Edit]** .
1. Selecteer het Variabelepictogram dat beschikbaar is in de assistent van het workflowmodel en selecteer **[!UICONTROL Add Variable]** .

   ![ voeg Variabele ](assets/variables_add_variable_new.png) toe

1. Geef in het dialoogvenster Variabele toevoegen de naam op en selecteer het type variabele.
1. Selecteer het gegevenstype in de vervolgkeuzelijst **[!UICONTROL Type]** en geef de volgende waarden op:

   * Primitieve gegevenstype - Geef een optionele standaardwaarde voor de variabele op.
   * JSON of XML - Geef een optioneel JSON- of XML-schemapad op. Het systeem valideert het schemapad terwijl het in kaart brengen van en het opslaan van eigenschappen beschikbaar in dit schema aan een andere variabele.
   * Formuliergegevensmodel - Geef een formuliergegevensmodelpad op.
   * ArrayList - Geef een subtype op voor de verzameling.

1. Specificeer een facultatieve beschrijving voor de variabele en selecteer ![ done_icon ](assets/done_icon.png) om de veranderingen te bewaren. De variabele wordt weergegeven in de lijst die beschikbaar is in het linkerdeelvenster.

Houd rekening met de volgende werkwijzen wanneer u variabelen maakt:

* Maak zoveel variabelen als een workflow nodig heeft. Om databasemiddelen te besparen, moet u echter het minimale aantal vereiste variabelen gebruiken en moet u variabelen waar mogelijk opnieuw gebruiken.
* Variabelen zijn hoofdlettergevoelig. Zorg ervoor dat u in uw werkstroom naar variabelen verwijst met hetzelfde hoofdlettergebruik.
* Gebruik geen speciale tekens in de naam van een variabele

## Een variabele instellen {#set-a-variable}

Met de stap Variabele instellen kunt u de waarde van een variabele instellen en de volgorde definiëren waarin de waarden worden ingesteld. De variabele wordt ingesteld in de volgorde waarin de variabele-toewijzingen worden vermeld in de stap met de variabele-set.

Wijzigingen in waarden van variabelen zijn alleen van invloed op de instantie van het proces waarin de wijziging plaatsvindt. Wanneer bijvoorbeeld een werkstroom wordt gestart en variabele gegevens worden gewijzigd, hebben de wijzigingen alleen invloed op dat exemplaar van de werkstroom. De wijzigingen zijn niet van invloed op andere versies van de workflow die eerder zijn gestart of daarna worden gestart.

Afhankelijk van het gegevenstype van de variabele kunt u de volgende opties gebruiken om de waarde van een variabele in te stellen:

* **Letterlijk:** gebruik de optie wanneer u de nauwkeurige te specificeren waarde kent.

* **Uitdrukking:** gebruik de optie wanneer de te gebruiken waarde gebaseerd op een uitdrukking wordt berekend. De expressie wordt gemaakt in de beschikbare expressie-editor.

* **JSON de Nota van de Punt:** Gebruik de optie om een waarde van een JSON of FDM typevariabele terug te winnen.
* **XPATH:** gebruik de optie om een waarde van een het typevariabele van XML terug te winnen.

* **met betrekking tot nuttige lading:** gebruik de optie wanneer de waarde die aan variabele moet worden bewaard bij een weg met betrekking tot nuttige lading beschikbaar is.

* **Absolute weg:** gebruik de optie wanneer de waarde die aan variabele moet worden bewaard bij een absolute weg beschikbaar is.

U kunt ook specifieke elementen van een variabele van het type JSON of XML bijwerken met JSON-puntnotatie of XPATH-notatie.

### Toewijzing tussen variabelen toevoegen {#add-mapping-between-variables}

Voer de volgende stappen uit om toewijzingen tussen variabelen toe te voegen:

1. Selecteer op de pagina voor workflowbewerking het pictogram Stappen dat beschikbaar is in de assistent van het workflowmodel.
1. Sleep-en-daling de **Vastgestelde Veranderlijke** stap aan de werkschemaredacteur, selecteer de stap en selecteer ![ configure_icon ](assets/configure_icon.png) (vorm).
1. Selecteer **[!UICONTROL Mapping]** > **[!UICONTROL Add Mapping]** in het dialoogvenster Variabele instellen.
1. In de **Variabele van de Kaart** sectie, selecteer de variabele om gegevens op te slaan, selecteer de afbeeldingswijze, en specificeer een waarde om in de variabele op te slaan. De toewijzingsmodi variëren op basis van het type variabele.
1. Wijs meer variabelen toe om een betekenisvolle expressie te maken. Selecteer ![ done_icon ](assets/done_icon.png) om de veranderingen te bewaren.

### Voorbeeld 1: Vraag een XML-variabele naar een waarde voor een tekenreeksvariabele {#example-query-an-xml-variable-to-set-value-for-a-string-variable}

Selecteer een variabele van het type van XML om een dossier van XML op te slaan. Vraag de variabele van XML om de waarde voor een koordvariabele voor het bezit te plaatsen beschikbaar in het dossier van XML. Het gebruik **specificeert XPATH voor het veranderlijke** gebied van XML om het bezit te bepalen in de koordvariabele op te slaan.

In dit voorbeeld, selecteer de variabele van a **formdata** XML om het {**dossier op te slaan 2} cc-app.xml.** Vraag de **formdata** variabele om de waarde voor de **e-mailadres** koordvariabele te plaatsen om de waarde voor het **emailAddress** bezit op te slaan beschikbaar in het **cc-app.xml** dossier.

[ plaats veranderlijke video ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/set_variable_example1.mp4)

### Voorbeeld 2: een expressie gebruiken om waarde op te slaan op basis van andere variabelen {#example2}

Gebruik een expressie om de som van de variabelen te berekenen en sla het resultaat op in een variabele.

In dit voorbeeld, gebruik de uitdrukkingsredacteur om een uitdrukking te bepalen om de som van **activaKosten** en **evenwieamount** variabelen te berekenen en het resultaat in **totalvalue** variabele op te slaan.

<!-- FUTURE ERROR: YouTube and mp4 videos are not supported -->

[ de uitdrukkingsvideo van Variabelen ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_expression.mp4)

## Expressieeditor gebruiken {#use-expression-editor}

U gebruikt ook expressies om de waarde van een variabele in de runtime te berekenen. Variabelen bieden een expressie-editor om expressies te definiëren.

Met de expressie-editor kunt u:

* Stel de waarde van variabelen in met behulp van andere workflowvariabelen, getallen of wiskundige expressies.
* Werkstroomvariabelen, tekenreeksen, getallen of expressies gebruiken in een wiskundige expressie
* Voeg voorwaarden toe om waarden van variabelen in te stellen.
* Operatoren toevoegen tussen voorwaarden.

![ Redacteur van de Uitdrukking ](assets/variables_expression_editor_new.png)

De editor is gebaseerd op de regel voor aangepaste formulieren. De volgende wijzigingen zijn aangebracht. Regeleditor in variabelen:

* Biedt geen ondersteuning voor functies.
* Biedt geen interface voor het weergeven van een overzicht van regels
* Heeft geen code-editor.
* Hiermee wordt het in- en uitschakelen van de waarde van een object niet ondersteund.
* Hiermee wordt eigenschap instellen van een object niet ondersteund.
* Biedt geen ondersteuning voor het oproepen van een webservice.

Voor meer informatie, zie [ de aanpassingsredacteur van de vormenregel ](../../forms/using/rule-editor.md).

## Een variabele gebruiken {#use-a-variable}

U kunt variabelen gebruiken om input en output terug te winnen of het resultaat van een stap te bewaren. De werkstroomeditor bevat twee typen workflowstappen:

* Workflowstappen met ondersteuning voor variabelen
* Workflowstappen zonder ondersteuning voor variabelen

### Workflowstappen met ondersteuning voor variabelen {#workflow-steps-with-support-for-variables}

De stap Ga naar OF Splitsen en alle AEM Forms Workflowstappen ondersteunen variabelen.

#### OF stap Splitsen {#or-split-step}

Met de indeling OR wordt een splitsing in de workflow gemaakt, waarna slechts één vertakking actief is. Met deze stap kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren. U voegt workflowstappen naar wens toe aan elke vertakking.

U kunt het verpletteren van uitdrukking voor een tak bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

U kunt variabelen gebruiken om de verpletterende uitdrukking te bepalen gebruikend de uitdrukkingsredacteur. Voor meer informatie bij het gebruiken van het verpletteren van uitdrukkingen voor OF Gesplitste stap, zie [ OF stap Splitsen ](/help/sites-developing/workflows-step-ref.md#or-split).

In dit voorbeeld, alvorens de verpletterende uitdrukking te bepalen, gebruik [ voorbeeld 2 ](../../forms/using/variable-in-aem-workflows.md#example2) om de waarde voor de **totalvalue** variabele te plaatsen. Tak 1 is actief als de waarde van de **totalvalue** variabele groter is dan 50000. Op dezelfde manier kunt u een regel bepalen om Tak 2 actief te maken als de waarde van de **totalvalue** variabele minder dan 50000 is.

[ OF gespleten video ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_orsplit_example.mp4)

Op dezelfde manier selecteer een externe manuscriptweg of specificeer het manuscript ECMA voor het verpletteren van uitdrukkingen om de actieve tak te evalueren. Selecteer **[!UICONTROL Rename Branch]** om een alternatieve naam voor de vertakking op te geven.

Voor meer voorbeelden, zie [ een werkschemamodel ](../../forms/using/aem-forms-workflow.md#create-a-workflow-model) creëren.

#### Ga naar stap {#go-to-step}

De **Goto Stap** laat u de volgende stap in het werkschemamodel specificeren uit te voeren, afhankelijk van het resultaat van een verpletterende uitdrukking.

Gelijkaardig aan OF de Gesplitste stap, kunt u het verpletteren van uitdrukking voor stap bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

U kunt variabelen gebruiken om de verpletterende uitdrukking te bepalen gebruikend de uitdrukkingsredacteur. Voor meer informatie bij het gebruiken van het verpletteren van uitdrukkingen voor de stap Ga, zie [ Ga ](/help/sites-developing/workflows-step-ref.md#goto-step).

![ ga naar Regel ](assets/variables_goto_rule1_new.png)

In dit voorbeeld, specificeert de stap van het Ga de Toepassing van de Kaart van het Overzicht als volgende stap als de waarde voor de **genomen actie** variabele gelijk is aan **behoefte meer info**.

Voor meer voorbeelden bij het gebruiken van regeldefinitie in de Goto stap, zie [ Simulerend a voor lijn ](/help/sites-developing/workflows-step-ref.md#simulateforloop).

#### Forms-workflowgerichte stappen {#forms-workflow-centric-workflow-steps}

Alle AEM Forms Workflowstappen ondersteunen variabelen. Voor meer informatie, zie [ Forms-centric werkschema op OSGi ](../../forms/using/aem-forms-workflow-step-reference.md).

### Workflowstappen zonder ondersteuning voor variabelen {#workflow-steps-without-support-for-variables}

U kunt [ MetaDataMap ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) interface gebruiken om tot variabelen in werkschemastappen toegang te hebben die geen variabelen steunen.

#### De waarde van de variabele ophalen {#retrieve-the-variable-value}

Gebruik de volgende API&#39;s in het ECMA-script om waarden voor bestaande variabelen op te halen op basis van het gegevenstype:

| Gegevenstype variabele | API |
|---|---|
| Primitief (lang, dubbel, Boolean, datum en tekenreeks) | workItem.getWorkflowData().getMetaDataMap().get(variableName, type) |
| Document | Packages.com.adobe.aemfd.docmanager.Document = workItem.getWorkflowData().getMetaDataMap().get(&quot;docVar&quot;, Packages.com.adobe.aemfd.docmanager.Document.class); |
| XML | Packages.org.w3c.dom.Document xmlObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.org.w3c.dom.Document.class); |
| Formuliergegevensmodel | Packages.com.adobe.name.dermis.api.FormDataModelInstance fdmObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.adobe.aem.dermis.api.FormDataModelInstance.class); |
| JSON | Packages.com.google.get.JsonObject jsonObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.google.gson.JsonObject.class); |

U vereist [ toe:voegen-op pakket van AEM Forms ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) voor de veranderlijke gegevenstypes van het Model van Gegevens van het Document en van de Vorm.

**Voorbeeld**

Hiermee wordt de waarde van het gegevenstype String opgehaald met de volgende API:

```javascript
workItem.getWorkflowData().getMetaDataMap().get(accname, Packages.java.lang.String)
```

#### De waarde van de variabele bijwerken {#update-the-variable-value}

Gebruik de volgende API in het ECMA-script om de waarde van een variabele bij te werken:

```javascript
workItem.getWorkflowData().getMetaDataMap().put(variableName, value)
```

**Voorbeeld**

```javascript
workItem.getWorkflowData().getMetaDataMap().put(salary, 50000)
```

werkt de waarde voor de **salaris** variabele aan 50000 bij.

### Variabelen instellen om workflows aan te roepen {#apiinvokeworkflow}

U kunt een API gebruiken om variabelen in te stellen en deze door te geven om workflowinstanties aan te roepen.

[ workflowSession.startWorkflow ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html#startWorkflow-com.adobe.granite.workflow.model.WorkflowModel-com.adobe.granite.workflow.exec.WorkflowData-java.util.Map-) gebruikt model, wfData, en metaData als argumenten. Gebruik MetaDataMap om de waarde voor de variabele in te stellen.

In dit API, wordt de **variableName** variabele geplaatst aan **waarde** gebruikend metaData.put (variableName, waarde);

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

Initialiseer het **doc** documentvoorwerp aan een weg (&quot;a/b/c&quot;) en plaats de waarde van de **docVar** variabele aan de weg die in het documentvoorwerp wordt opgeslagen.

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

### Gevoelige gebruikersgegevens opslaan buiten JCR met behulp van workflowvariabelen {#jcr-independent-persistance}

Gegevens die met Forms Workflow worden verwerkt, kunnen vertrouwelijke gebruikersgegevens bevatten, zoals Persoonlijk identificeerbare gegevens en Gevoelige persoonlijke gegevens. De ondernemingen kunnen verkiezen om de gegevens op te slaan, die door diverse werkschemastappen (en overgegaan gebruikend werkschemariabelen), uit opslag JCR in een externe gegevensopslag worden verwerkt die door hen wordt bezeten en wordt beheerd. Meer over het voortbestaan werkschemagegevens in een externe opslag weten, zie [ Gebruikend werkschemariabelen voor klant bezeten datastores ](/help/sites-administering/workflows-administering.md#using-workflow-variables-customer-datastore).
[!DNL Adobe Experience Manager] verstrekt Werkschema API [ UserMetaDataPersistenceProvider ](https://github.com/adobe/workflow-variable-externalizer) om werkschemariabelen in externe Azure blob opslag op te slaan. Voor details over het gebruiken van API, zie [ het werkschemavariabelen van het Gebruik om gevoelige gegevens van parameters te bepalen en in externe gegevensopslag op te slaan ](/help/forms/using/aem-forms-workflow.md#externalize-wf-variables).

## Een variabele bewerken {#edit-a-variable}

1. Selecteer op de pagina voor de bewerkingsworkflow het pictogram Variabelen in de assistent van het workflowmodel. In het gedeelte Variabelen in het linkerdeelvenster worden alle bestaande variabelen weergegeven.
1. Selecteer ![ uitgeven ](assets/edit.png) (geef uit) pictogram naast de veranderlijke naam uit die u wilt uitgeven.
1. Bewerk de veranderlijke informatie en selecteer ![ done_icon ](assets/done_icon.png) om de veranderingen te bewaren. U kunt de velden **[!UICONTROL Name]** en **[!UICONTROL Type]** voor een variabele niet bewerken.

## Een variabele verwijderen {#delete-a-variable}

Voordat u de variabele verwijdert, verwijdert u alle referenties van de variabele uit de workflow. Zorg ervoor dat de variabele niet in de workflow wordt gebruikt.

Voer de volgende stappen uit om een variabele te verwijderen:

1. Selecteer op de pagina voor de bewerkingsworkflow het pictogram Variabelen in de assistent van het workflowmodel. In het gedeelte Variabelen in het linkerdeelvenster worden alle bestaande variabelen weergegeven.
1. Selecteer het pictogram Verwijderen naast de naam van de variabele die u wilt verwijderen.
1. Selecteer ![ done_icon ](assets/done_icon.png) om de variabele te bevestigen en te schrappen.

## Verwijzingen {#references}

Voor meer voorbeelden bij het gebruiken van variabelen in de stappen van het Werkschema van AEM Forms, zie [ Variabelen in de werkschema&#39;s van AEM ](https://helpx.adobe.com/experience-manager/kt/forms/using/authoring_variables_in_aem_forms-workflow1.html).
