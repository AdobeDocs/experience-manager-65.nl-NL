---
title: Uitbreiding van workflowfunctionaliteit
seo-title: Uitbreiding van workflowfunctionaliteit
description: Uitbreiding van workflowfunctionaliteit
seo-description: 'null'
uuid: 9f4ea2a8-8b21-4e7c-ac73-dd37d9ada111
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: f23408c3-6b37-4047-9cce-0cab97bb6c5c
translation-type: tm+mt
source-git-commit: 7035c19a109ff67655ee0419aa37d1723e2189cc
workflow-type: tm+mt
source-wordcount: '3587'
ht-degree: 1%

---


# Uitbreiding van workflowfunctionaliteit{#extending-workflow-functionality}

Dit onderwerp beschrijft hoe te om de componenten van de douanestap voor uw werkschema&#39;s te ontwikkelen, toen hoe te programmatically met werkschema&#39;s in wisselwerking te staan.

Het maken van een aangepaste workflowstap omvat de volgende activiteiten:

* Ontwikkel de component van de werkschemastap.
* Voer de step functionaliteit als dienst OSGi of een manuscript ECMA uit.

U kunt ook [communiceren met uw workflows vanuit uw programma&#39;s en scripts](/help/sites-developing/workflows-program-interaction.md).

## Workflowstapcomponenten - De basisbeginselen {#workflow-step-components-the-basics}

Een workflowcomponent definieert de vormgeving en het gedrag van de stap bij het maken van workflowmodellen:

* De categorie en de stapnaam in het werkschemahulpje.
* De vormgeving van de stap in workflowmodellen.
* Het dialoogvenster Bewerken voor het configureren van componenteigenschappen.
* De service of het script dat wordt uitgevoerd bij uitvoering.

Net als bij [alle componenten](/help/sites-developing/components.md) erven workflowstapcomponenten van de component die is opgegeven voor de eigenschap `sling:resourceSuperType`. Het volgende diagram toont de hiërarchie van `cq:component` knopen die de basis van alle componenten van de werkschemastap vormen. Het diagram bevat ook de **Processtap**, **Deelnemersstap** en **Dynamische deelnemersstap**, aangezien dit de meest gebruikelijke (en fundamentele) uitgangspunten zijn voor het ontwikkelen van componenten van aangepaste stappen.

![aem_wf_componentinherit](assets/aem_wf_componentinherit.png)

>[!CAUTION]
>
>U ***must*** verandert niets in `/libs` weg.
>
>Dit komt doordat de inhoud van `/libs` de volgende keer wordt overschreven dat u uw exemplaar bijwerkt (en dat kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen zoals het bestaat in `/libs` onder `/apps`
>2. Wijzigingen aanbrengen binnen `/apps`


De `/libs/cq/workflow/components/model/step` component is de dichtstbijzijnde gemeenschappelijke voorouder van **Process Step**, **Participant Step**, en **Dynamic Participant Step**, die allen de volgende punten erven:

* `step.jsp`

   Met het script `step.jsp` wordt de titel van de step-component weergegeven wanneer deze aan een model wordt toegevoegd.

   ![wf-22-1](assets/wf-22-1.png)

* [cq:dialoogvenster](/help/sites-developing/developing-components.md#creating-and-configuring-a-dialog)

   Een dialoogvenster met de volgende tabbladen:

   * **Vaak**: voor het bewerken van de titel en beschrijving.
   * **Geavanceerd**: voor het bewerken van eigenschappen voor e-mailmeldingen.

   ![wf-44](assets/wf-44.png) ![wf-45](assets/wf-45.png)

   >[!NOTE]
   >
   >Wanneer de tabbladen van het dialoogvenster Bewerken van een stapcomponent niet overeenkomen met deze standaardweergave, heeft de stapcomponent scripts, knoopeigenschappen of dialoogtabbladen gedefinieerd die deze overgeërfde tabbladen overschrijven.

### ECMA-scripts {#ecma-scripts}

De volgende objecten zijn beschikbaar (afhankelijk van het type stap) in ECMA-scripts:

* [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/WorkItem.html) WorkItemItem
* [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/WorkflowSession.html) WorkflowSessionworkflowSession
* [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/WorkflowData.html) WorkflowDataWorkflowData
* `args`: array met de procesargumenten.

* `sling`: toegang tot andere osgi - diensten.
* `jcrSession`

### MetaDataMaps {#metadatamaps}

U kunt metagegevens over workflows gebruiken om de informatie die tijdens de levensduur van de workflow vereist is, voort te zetten. Een algemene vereiste voor workflowstappen is dat gegevens voor toekomstig gebruik in de workflow moeten worden behouden of dat de blijvend opgeslagen gegevens moeten worden opgehaald.

Er zijn drie typen objecten MetaDataMap: voor objecten `Workflow`, `WorkflowData` en `WorkItem`. Ze hebben allemaal hetzelfde doel: metagegevens opslaan.

Een WorkItem heeft zijn eigen MetaDataMap die slechts kan worden gebruikt terwijl dat werkpunt (b.v. stap) loopt.

Zowel `Workflow` als `WorkflowData` metadatamaps worden over de volledige werkstroom gedeeld. In deze gevallen wordt aangeraden alleen de metagegevenstoewijzing `WorkflowData` te gebruiken.

## Aangepaste workflowstapcomponenten maken {#creating-custom-workflow-step-components}

Workflowstapcomponenten kunnen [op dezelfde manier worden gemaakt als andere componenten](/help/sites-developing/components.md).

Om van één van de (bestaande) componenten van de basisstap over te erven, voeg het volgende bezit aan `cq:Component` knoop toe:

* Naam: `sling:resourceSuperType`
* Type: `String`
* Waarde: Een van de volgende paden die wordt omgezet in een basiscomponent:

   * `cq/workflow/components/model/process`
   * `cq/workflow/components/model/participant`
   * `cq/workflow/components/model/dynamic_participant`

### De standaardtitel en -beschrijving opgeven voor instanties Stap {#specifying-the-default-title-and-description-for-step-instances}

Gebruik de volgende procedure om standaardwaarden voor **Title** en **Description** gebieden op **Common** tabel te specificeren.

>[!NOTE]
>
>De veldwaarden worden weergegeven op de stapinstantie wanneer aan beide volgende voorwaarden wordt voldaan:
>
>* In het dialoogvenster Bewerken van de stap worden de titel en beschrijving opgeslagen op de volgende locaties: >
>* `./jcr:title`
>* `./jcr:description` locaties

>
>  
Aan deze vereiste wordt voldaan wanneer het dialoogvenster Bewerken gebruikmaakt van het tabblad Algemeen dat de component `/libs/cq/flow/components/step/step` implementeert.
>
>* De step component of een voorouder van de component overschrijft niet het `step.jsp`-script dat de `/libs/cq/flow/components/step/step`-component implementeert.


1. Voeg onder het knooppunt `cq:Component` het volgende knooppunt toe:

   * Naam: `cq:editConfig`
   * Type: `cq:EditConfig`

   >[!NOTE]
   >
   >Voor meer informatie over de knoop cq:editConfig, zie [Vormend het Edit Gedrag van een Component](/help/sites-developing/developing-components.md#configuring-the-edit-behavior).

1. Voeg onder het knooppunt `cq:EditConfig` het volgende knooppunt toe:

   * Naam: `cq:formParameters`
   * Type: `nt:unstructured`

1. Voeg `String` eigenschappen van de volgende namen aan `cq:formParameters` knoop toe:

   * `jcr:title`: De waarde vult het  **** titelveld van het  **** tabblad Algemeen.
   * `jcr:description`: De waarde vult het  **** beschrijvingsveld van het  **** tabblad Algemeen.

### Eigenschapwaarden opslaan in werkstroommetagegevens {#saving-property-values-in-workflow-metadata}

>[!NOTE]
>
>Zie [Gegevens blijven behouden en openen](#persisting-and-accessing-data). Met name, voor informatie over de toegang tot van de bezitswaarde bij runtime, zie [Toegang tot de Waarden van het Bezit van de Dialoog bij Runtime](#accessing-dialog-property-values-at-runtime).

De eigenschap name van `cq:Widget`-items geeft het JCR-knooppunt op dat de waarde van de widget opslaat. Wanneer widgets in het dialoogvenster met workflowstapcomponenten waarden opslaan onder het knooppunt `./metaData`, wordt de waarde toegevoegd aan de workflow `MetaDataMap`.

Een tekstveld in een dialoogvenster is bijvoorbeeld een knooppunt `cq:Widget` met de volgende eigenschappen:

| Naam | Type | Waarde |
|---|---|---|
| `xtype` | `String` | `textarea` |
| `name` | `String` | `./metaData/subject` |
| `fieldLabel` | `String` | `Email Subject` |

De waarde die in dit tekstveld wordt opgegeven, wordt toegevoegd aan het ` [MetaDataMap](#metadatamaps)`-object van de werkstroominstantie en is gekoppeld aan de `subject`-toets.

>[!NOTE]
>
>Wanneer de sleutel `PROCESS_ARGS` is, is de waarde gemakkelijk beschikbaar in manuscriptimplementaties ECMA via `args` variabele. In dit geval is de waarde van de eigenschap name `./metaData/PROCESS_ARGS.`

### De stapimplementatie {#overriding-the-step-implementation} overschrijven

Elke component van de basisstap laat de ontwikkelaars van het werkschemamodel toe om de volgende zeer belangrijke eigenschappen in ontwerptijd te vormen:

* Processtap: De service of het ECMA-script dat bij uitvoering moet worden uitgevoerd.
* Stap deelnemer: De id van de gebruiker aan wie het gegenereerde werkitem is toegewezen.
* Stap dynamische deelnemer: De dienst of het manuscript ECMA dat identiteitskaart van de gebruiker selecteert die het het werkpunt wordt toegewezen.

Om de component voor gebruik in een specifiek werkschemascenario te concentreren, vorm de belangrijkste eigenschap in het ontwerp en verwijder de capaciteit voor modelontwikkelaars om het te veranderen.

1. Voeg onder het cq:component-knooppunt het volgende knooppunt toe:

   * Naam: `cq:editConfig`
   * Type: `cq:EditConfig`

   Voor meer informatie over de knoop cq:editConfig, zie [Vormend het Edit Gedrag van een Component](/help/sites-developing/developing-components.md#configuring-the-edit-behavior).

1. Voeg onder het knooppunt cq:EditConfig het volgende knooppunt toe:

   * Naam: `cq:formParameters`
   * Type: `nt:unstructured`

1. Voeg een `String` bezit aan `cq:formParameters` knoop toe. Het supertype van de component bepaalt de naam van het bezit:

   * Processtap: `PROCESS`
   * Stap deelnemer: `PARTICIPANT`
   * Stap dynamische deelnemer: `DYNAMIC_PARTICIPANT`

1. Geef de waarde van de eigenschap op:

   * `PROCESS`: Het pad naar het ECMA-script of de PID van de service die het stapgedrag implementeert.
   * `PARTICIPANT`: De id van de gebruiker aan wie het werkitem is toegewezen.
   * `DYNAMIC_PARTICIPANT`: Het pad naar het ECMA-script of de PID van de service die de gebruiker selecteert om het werkitem toe te wijzen.

1. Om de capaciteit van modelontwikkelaars te verwijderen om uw bezitswaarden te veranderen, vervang de dialoog van het componentensupertype.

### Forms en dialoogvensters toevoegen aan stappen {#adding-forms-and-dialogs-to-participant-steps}

Pas uw component van de deelnemersstap aan om eigenschappen te verstrekken die in [Stap van de Deelnemer van de Vorm ](/help/sites-developing/workflows-step-ref.md#form-participant-step) en [Stap van de Deelnemer van de Dialoog](/help/sites-developing/workflows-step-ref.md#dialog-participant-step) componenten worden gevonden:

* Een formulier presenteren aan de gebruiker wanneer deze het gegenereerde werkitem opent.
* Presenteer een aangepast dialoogvenster aan de gebruiker wanneer deze het gegenereerde werkitem voltooit.

Voer de volgende procedure op uw nieuwe component (zie [Creërend de Componenten van de Stap van de Werkstroom van de Douane](#creating-custom-workflow-step-components)) uit:

1. Voeg onder het knooppunt `cq:Component` het volgende knooppunt toe:

   * Naam: `cq:editConfig`
   * Type: `cq:EditConfig`

   Voor meer informatie over de knoop cq:editConfig, zie [Vormend het Edit Gedrag van een Component](/help/sites-developing/components-basics.md#edit-behavior).

1. Voeg onder het knooppunt cq:EditConfig het volgende knooppunt toe:

   * Naam: `cq:formParameters`
   * Type: `nt:unstructured`

1. Als u een formulier wilt presenteren terwijl de gebruiker het werkitem opent, voegt u de volgende eigenschap toe aan het knooppunt `cq:formParameters`:

   * Naam: `FORM_PATH`
   * Type: `String`
   * Waarde: Het pad dat wordt omgezet in het formulier

1. Als u een aangepast dialoogvenster wilt weergeven wanneer de gebruiker het werkitem voltooit, voegt u de volgende eigenschap toe aan de `cq:formParameters`-node

   * Naam: `DIALOG_PATH`
   * Type: `String`
   * Waarde: Het pad dat wordt omgezet in het dialoogvenster

### Het vormen van het Runtime van de Stap van het Werkschema Gedrag {#configuring-the-workflow-step-runtime-behavior}

Voeg onder het knooppunt `cq:Component` een knooppunt `cq:EditConfig` toe. Onder die een `nt:unstructured` knoop (moet worden genoemd `cq:formParameters`) toevoegen en aan die knoop voeg de volgende eigenschappen toe:

* Naam: `PROCESS_AUTO_ADVANCE`

   * Type: `Boolean`
   * Waarde:

      * wanneer ingesteld op `true`, wordt die stap uitgevoerd en verder - dit is standaard en ook aanbevolen
      * wanneer `false`, zal het werkschema lopen en ophouden; hiervoor is extra verwerkingstijd nodig, zodat `true` wordt aanbevolen

* Naam: `DO_NOTIFY`

   * Type: `Boolean`
   * Waarde: Hiermee wordt aangegeven of e-mailmeldingen moeten worden verzonden voor stappen voor gebruikersdeelname (en wordt ervan uitgegaan dat de mailserver correct is geconfigureerd)

## Behouden en toegang krijgen tot gegevens {#persisting-and-accessing-data}

### Gegevens behouden voor volgende workflowstappen {#persisting-data-for-subsequent-workflow-steps}

U kunt werkschemagegevens gebruiken om informatie voort te zetten die tijdens het leven van het werkschema - en tussen stappen wordt vereist. Een algemene vereiste voor workflowstappen is dat gegevens voor toekomstig gebruik behouden blijven of dat de blijvend gegevens uit eerdere stappen worden opgehaald.

De meta-gegevens van het werkschema worden opgeslagen in een [`MetaDataMap`](#metadatamaps) voorwerp. De Java API verstrekt [`Workflow.getWorkflowData`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/Workflow.html) methode om een [`WorkflowData`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkflowData.html) voorwerp terug te keren dat aangewezen `MetaDataMap` voorwerp verstrekt. Dit `WorkflowData` `MetaDataMap` voorwerp is beschikbaar aan de dienst OSGi of het manuscript ECMA van een step component.

#### Java {#java}

De uitvoeringsmethode van de `WorkflowProcess` implementatie wordt overgegaan tot `WorkItem` voorwerp. Gebruik dit object om het object `WorkflowData` voor de huidige werkstroominstantie op te halen. In het volgende voorbeeld wordt een item toegevoegd aan het werkstroomobject `MetaDataMap` en wordt elk item vervolgens in een logbestand opgenomen. Het item (&quot;mijnsleutel&quot;, &quot;Mijn stapwaarde&quot;) is beschikbaar voor volgende stappen in de workflow.

```java
public void execute(WorkItem item, WorkflowSession session, MetaDataMap args) throws WorkflowException {

    MetaDataMap wfd = item.getWorkflow().getWorkflowData().getMetaDataMap();

    wfd.put("mykey", "My Step Value");

    Set<String> keyset = wfd.keySet();
    Iterator<String> i = keyset.iterator();
    while (i.hasNext()){
     Object key = i.next();
     log.info("The workflow medata includes key {} and value {}",key.toString(),wfd.get(key).toString());
    }
}
```

#### ECMA-script {#ecma-script}

De `graniteWorkItem` variabele is de ECMA manuscriptvertegenwoordiging van het huidige `WorkItem` voorwerp van Java. Daarom kunt u de `graniteWorkItem` variabele gebruiken om de werkschemameta-gegevens te verkrijgen. Het volgende ECMA manuscript kan worden gebruikt om **Stap** van het Proces uit te voeren om een punt aan het werkschema `MetaDataMap` voorwerp toe te voegen en dan elk punt te registreren. Deze items zijn vervolgens beschikbaar voor volgende stappen in de workflow.

>[!NOTE]
>
>De `metaData` variabele die onmiddellijk beschikbaar voor het stapmanuscript is is de meta-gegevens van de stap. De metagegevens van de stap verschillen van de metagegevens van de workflow.

```
var currentDateInMillis = new Date().getTime();

graniteWorkItem.getWorkflowData().getMetaDataMap().put("hardcodedKey","theKey");

graniteWorkItem.getWorkflowData().getMetaDataMap().put("currentDateInMillisKey",currentDateInMillis);

var iterator = graniteWorkItem.getWorkflowData().getMetaDataMap().keySet().iterator();
while (iterator.hasNext()){
    var key = iterator.next();
    log.info("Workflow metadata key, value = " + key.toString() + ", " + graniteWorkItem.getWorkflowData().getMetaDataMap().get(key));
}
```

### Dialoogvenstereigenschapswaarden openen bij uitvoering {#accessing-dialog-property-values-at-runtime}

Het object `MetaDataMap` van workflowinstanties is handig voor het opslaan en ophalen van gegevens gedurende de gehele levensduur van de workflow. Voor implementaties van workflowstappen is `MetaDataMap` vooral handig voor het ophalen van componenteigenschapswaarden tijdens runtime.

>[!NOTE]
>
>Zie [Eigenschapwaarden opslaan in werkstroommetagegevens](#saving-property-values-in-workflow-metadata) voor informatie over het configureren van het dialoogvenster met componenten om eigenschappen op te slaan als werkstroommetagegevens.

De workflow `MetaDataMap` is beschikbaar voor Java- en ECMA-scriptprocesimplementaties:

* In Java-implementaties van de WorkflowProcess-interface is de `args`-parameter het `MetaDataMap`-object voor de workflow.

* In ECMA manuscriptimplementaties, is de waarde beschikbaar gebruikend `args` en `metadata` variabelen.

### Voorbeeld: De argumenten van de processtapcomponent {#example-retrieving-the-arguments-of-the-process-step-component} ophalen

Het dialoogvenster Bewerken van de component **Processtap** bevat de eigenschap **Argumenten**. De waarde van de eigenschap **Arguments** wordt opgeslagen in de metagegevens van de workflow en is gekoppeld aan de `PROCESS_ARGS`-toets.

In het volgende diagram is de waarde van de eigenschap **Arguments** `argument1, argument2`:

![wf-24](assets/wf-24.png)

#### Java {#java-1}

De volgende Java-code is de methode `execute` voor een `WorkflowProcess`-implementatie. De methode registreert de waarde in `args` `MetaDataMap` die met `PROCESS_ARGS` sleutel wordt geassocieerd.

```java
public void execute(WorkItem item, WorkflowSession session, MetaDataMap args) throws WorkflowException {
     if (args.containsKey("PROCESS_ARGS")){
      log.info("workflow metadata for key PROCESS_ARGS and value {}",args.get("PROCESS_ARGS","string").toString());
     }
    }
```

Wanneer een processtap wordt uitgevoerd die deze Java-implementatie gebruikt, bevat het logbestand de volgende vermelding:

```xml
16.02.2018 12:07:39.566 *INFO* [JobHandler: /var/workflow/instances/server0/2018-02-16/model_855140139900189:/content/we-retail/de] com.adobe.example.workflow.impl.process.LogArguments workflow metadata for key PROCESS_ARGS and value argument1, argument2
```

#### ECMA-script {#ecma-script-1}

Het volgende manuscript ECMA wordt gebruikt als proces voor **Stap van het Proces**. Het registreert het aantal argumenten en de argumentwaarden:

```
var iterator = graniteWorkItem.getWorkflowData().getMetaDataMap().keySet().iterator();
while (iterator.hasNext()){
    var key = iterator.next();
    log.info("Workflow metadata key, value = " + key.toString() + ", " + graniteWorkItem.getWorkflowData().getMetaDataMap().get(key));
}
log.info("hardcodedKey "+ graniteWorkItem.getWorkflowData().getMetaDataMap().get("hardcodedKey"));
log.info("currentDateInMillisKey "+ graniteWorkItem.getWorkflowData().getMetaDataMap().get("currentDateInMillisKey"));
```

>[!NOTE]
>
>In deze sectie wordt beschreven hoe u met argumenten voor processtappen werkt. De informatie is ook van toepassing op dynamische deelnemerselecties.

>[!NOTE]
>Zie Voorbeeld voor een ander voorbeeld van het opslaan van componenteigenschappen in workflowmetagegevens: Creeer een Stap van het Werkschema van de Logger. In dit voorbeeld wordt een dialoogvenster weergegeven waarin de metagegevenswaarde wordt gekoppeld aan een andere sleutel dan PROCESS_ARGS.

### Scripts en procesargumenten {#scripts-and-process-arguments}

Binnen een manuscript voor **De component van de Stap van het Proces**, zijn de argumenten beschikbaar door het `args` voorwerp.

Wanneer u een component met een aangepaste stap maakt, is het object `metaData` beschikbaar in een script. Dit object is beperkt tot één tekenreeksargument.

## Implementaties van processtappen ontwikkelen {#developing-process-step-implementations}

Wanneer de processtappen tijdens het proces van een werkschema zijn begonnen, verzenden de stappen een verzoek naar een dienst OSGi of voeren een manuscript ECMA uit. Ontwikkel de dienst of het manuscript ECMA dat de acties uitvoert die uw werkschema vereist.

>[!NOTE]
>
>Voor informatie over het associëren van uw component van de Stap van het Proces met de dienst of het manuscript, zie [Stap ](/help/sites-developing/workflows-step-ref.md#process-step) of [Het met voeten treden van de Implementatie van de Stap](#overriding-the-step-implementation).

### Een processtap implementeren met een Java-klasse {#implementing-a-process-step-with-a-java-class}

Een processtap definiëren als een OSGI-servicecomponent (Java-bundel):

1. Maak de bundel en plaats deze in de OSGI-container. Raadpleeg de documentatie over het maken van een bundel met [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) of [Eclipse](/help/sites-developing/howto-projects-eclipse.md).

   >[!NOTE]
   >
   >De component OSGI moet de `WorkflowProcess` interface met zijn `execute()` methode uitvoeren. Zie de voorbeeldcode hieronder.

   >[!NOTE]
   >
   >De pakketnaam moet worden toegevoegd aan de sectie `<*Private-Package*>` van de `maven-bundle-plugin` configuratie.

1. Voeg het SCR bezit `process.label` toe en plaats de waarde zoals u vereist. Dit zal de naam zijn die uw processtap zoals wanneer het gebruiken van generische **Stap van het Proces** component vermeld is. Zie het onderstaande voorbeeld.
1. Voeg in de **Modellen** redacteur, de processtap aan het werkschema toe gebruikend de generische **Stap van het Proces** component.
1. Ga in het bewerkingsdialoogvenster (van de **Processtap**) naar het tabblad **Proces** en selecteer uw procesimplementatie.
1. Als u argumenten in uw code gebruikt, plaats **Argumenten van het Proces**. Bijvoorbeeld: false.
1. Sla de wijzigingen op voor zowel de stap als het workflowmodel (linksboven in de modeleditor).

De methoden java, respectievelijk de klassen die de uitvoerbare Java-methode implementeren, worden geregistreerd als OSGI-services, waarmee u tijdens runtime op elk moment methoden kunt toevoegen.

De volgende component OSGI voegt de eigenschap `approved` toe aan het knooppunt page content wanneer de payload een pagina is:

```java
package com.adobe.example.workflow.impl.process;

import com.adobe.granite.workflow.WorkflowException;
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.WorkItem;
import com.adobe.granite.workflow.exec.WorkflowData;
import com.adobe.granite.workflow.exec.WorkflowProcess;
import com.adobe.granite.workflow.metadata.MetaDataMap;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;

import org.osgi.framework.Constants;

import javax.jcr.Node;
import javax.jcr.RepositoryException;
import javax.jcr.Session;

/**
 * Sample workflow process that sets an <code>approve</code> property to the payload based on the process argument value.
 */
@Component
@Service
public class MyProcess implements WorkflowProcess {

 @Property(value = "An example workflow process implementation.")
 static final String DESCRIPTION = Constants.SERVICE_DESCRIPTION;
 @Property(value = "Adobe")
 static final String VENDOR = Constants.SERVICE_VENDOR;
 @Property(value = "My Sample Workflow Process")
 static final String LABEL="process.label";

 private static final String TYPE_JCR_PATH = "JCR_PATH";

 public void execute(WorkItem item, WorkflowSession session, MetaDataMap args) throws WorkflowException {
  WorkflowData workflowData = item.getWorkflowData();
  if (workflowData.getPayloadType().equals(TYPE_JCR_PATH)) {
   String path = workflowData.getPayload().toString() + "/jcr:content";
   try {
    Session jcrSession = session.adaptTo(Session.class);
    Node node = (Node) jcrSession.getItem(path);
    if (node != null) {
     node.setProperty("approved", readArgument(args));
     jcrSession.save();
    }
   } catch (RepositoryException e) {
    throw new WorkflowException(e.getMessage(), e);
   }
  }
 }

 private boolean readArgument(MetaDataMap args) {
  String argument = args.get("PROCESS_ARGS", "false");
  return argument.equalsIgnoreCase("true");
 }
}
```

>[!NOTE]
>
>Als het proces drie keer in een rij mislukt, wordt een item in het Postvak In van de workflowbeheerder geplaatst.

### ECMAScript {#using-ecmascript} gebruiken

Met ECMA-scripts kunnen scriptontwikkelaars processtappen implementeren. De scripts bevinden zich in de JCR-opslagplaats en worden daar uitgevoerd.

In de volgende tabel staan de variabelen die direct beschikbaar zijn voor het verwerken van scripts, waarmee toegang wordt verleend tot objecten van de Java API voor de workflow.

| Java-klasse | Naam scriptvariabele | Beschrijving |
|---|---|---|
| `com.adobe.granite.workflow.exec.WorkItem` | `graniteWorkItem` | De huidige step-instantie. |
| `com.adobe.granite.workflow.WorkflowSession` | `graniteWorkflowSession` | De workflowsessie van de huidige step-instantie. |
| `String[]` (bevat procesargumenten) | `args` | De step-argumenten. |
| `com.adobe.granite.workflow.metadata.MetaDataMap` | `metaData` | De metagegevens van de huidige step-instantie. |
| `org.apache.sling.scripting.core.impl.InternalScriptHelper` | `sling` | Biedt toegang tot de Sling-runtimeomgeving. |

Het volgende voorbeeldscript laat zien hoe u toegang krijgt tot het JCR-knooppunt dat de payload van de workflow vertegenwoordigt. De `graniteWorkflowSession` variabele wordt aangepast aan een JCR zittingsvariabele, die wordt gebruikt om de knoop uit de nuttige ladingspad te verkrijgen.

```
var workflowData = graniteWorkItem.getWorkflowData();
if (workflowData.getPayloadType() == "JCR_PATH") {
    var path = workflowData.getPayload().toString();
    var jcrsession = graniteWorkflowSession.adaptTo(Packages.javax.jcr.Session);
    var node = jcrsession.getNode(path);
    if (node.hasProperty("approved")){
     node.setProperty("approved", args[0] == "true" ? true : false);
     node.save();
 }
}
```

Met het volgende script wordt gecontroleerd of de laadbewerking een afbeelding ( `.png`-bestand) is, wordt er een zwart-witafbeelding van gemaakt en opgeslagen als een knooppunt op hetzelfde niveau.

```
var workflowData = graniteWorkItem.getWorkflowData();
if (workflowData.getPayloadType() == "JCR_PATH") {
    var path = workflowData.getPayload().toString();
    var jcrsession = graniteWorkflowSession.adaptTo(Packages.javax.jcr.Session);
    var node = jcrsession.getRootNode().getNode(path.substring(1));
     if (node.isNodeType("nt:file") && node.getProperty("jcr:content/jcr:mimeType").getString().indexOf("image/") == 0) {
        var is = node.getProperty("jcr:content/jcr:data").getStream();
        var layer = new Packages.com.day.image.Layer(is);
        layer.grayscale();
                var parent = node.getParent();
                var gn = parent.addNode("grey" + node.getName(), "nt:file");
        var content = gn.addNode("jcr:content", "nt:resource");
                content.setProperty("jcr:mimeType","image/png");
                var cal = Packages.java.util.Calendar.getInstance();
                content.setProperty("jcr:lastModified",cal);
                var f = Packages.java.io.File.createTempFile("test",".png");
        var tout = new Packages.java.io.FileOutputStream(f);
        layer.write("image/png", 1.0, tout);
        var fis = new Packages.java.io.FileInputStream(f);
                content.setProperty("jcr:data", fis);
                parent.save();
        tout.close();
        fis.close();
        is.close();
        f.deleteOnExit();
    }
}
```

Het script gebruiken:

1. Maak het script (bijvoorbeeld met CRXDE Lite) en sla het op in de opslagplaats onder `/apps/myapp/workflow/scripts`
1. Als u een titel wilt opgeven die het script identificeert in het dialoogvenster **Processtap** bewerken, voegt u de volgende eigenschappen toe aan de `jcr:content`-node van uw script:

   | Naam | Type | Waarde |
   |---|---|---|
   | `jcr:mixinTypes` | `Name[]` | `mix:title` |
   | `jcr:title` | `String` | De naam die moet worden weergegeven in het dialoogvenster Bewerken. |

1. Bewerk de instantie **Processtap** en geef het te gebruiken script op.

## Deelnemerkiezers {#developing-participant-choosers} ontwikkelen

U kunt deelnemerkiezers ontwikkelen voor **Dynamische deelnemersstap** componenten.

Wanneer een **Dynamische Stap** component van de Deelnemer tijdens een werkschema is begonnen, moet de stap de deelnemer bepalen waaraan het geproduceerde het werkpunt kan worden toegewezen. Hiervoor moet u een van de volgende stappen uitvoeren:

* verzendt een verzoek naar een dienst OSGi
* voert een manuscript ECMA uit om de deelnemer te selecteren

U kunt de dienst of een manuscript ontwikkelen ECMA dat de deelnemer volgens de vereisten van uw werkschema selecteert.

>[!NOTE]
>
>Voor informatie over het associëren van uw **Dynamische Stap van de Deelnemer** component met de dienst of het manuscript, zie [Dynamische Stap van de Deelnemer](/help/sites-developing/workflows-step-ref.md#dynamic-participant-step) of [Het met voeten treden van de Implementatie van de Stap](#persisting-and-accessing-data).

### Een kiezer voor deelnemers ontwikkelen met een Java-klasse {#developing-a-participant-chooser-using-a-java-class}

Een deelnemersstap definiëren als een OSGI-servicecomponent (Java-klasse):

1. De component OSGI moet de `ParticipantStepChooser` interface met zijn `getParticipant()` methode uitvoeren. Zie de voorbeeldcode hieronder.

   Maak de bundel en plaats deze in de OSGI-container.

1. Voeg de SCR bezit `chooser.label` toe en plaats de waarde zoals vereist. Dit zal de naam zijn zoals uw deelnemerverkiezer, gebruikend de **Dynamische Stap** component van de Deelnemer wordt vermeld. Zie het voorbeeld:

   ```java
   package com.adobe.example.workflow.impl.process;
   
   import com.adobe.granite.workflow.WorkflowException;
   import com.adobe.granite.workflow.WorkflowSession;
   import com.adobe.granite.workflow.exec.ParticipantStepChooser;
   import com.adobe.granite.workflow.exec.WorkItem;
   import com.adobe.granite.workflow.exec.WorkflowData;
   import com.adobe.granite.workflow.metadata.MetaDataMap;
   
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   
   import org.osgi.framework.Constants;
   
   /**
    * Sample dynamic participant step that determines the participant based on a path given as argument.
    */
   @Component
   @Service
   
   public class MyDynamicParticipant implements ParticipantStepChooser {
   
    @Property(value = "An example implementation of a dynamic participant chooser.")
    static final String DESCRIPTION = Constants.SERVICE_DESCRIPTION;
       @Property(value = "Adobe")
       static final String VENDOR = Constants.SERVICE_VENDOR;
       @Property(value = "Dynamic Participant Chooser Process")
       static final String LABEL=ParticipantStepChooser.SERVICE_PROPERTY_LABEL;
   
       private static final String TYPE_JCR_PATH = "JCR_PATH";
   
       public String getParticipant(WorkItem workItem, WorkflowSession workflowSession, MetaDataMap args) throws WorkflowException {
           WorkflowData workflowData = workItem.getWorkflowData();
           if (workflowData.getPayloadType().equals(TYPE_JCR_PATH)) {
               String path = workflowData.getPayload().toString();
               String pathFromArgument = args.get("PROCESS_ARGS", String.class);
               if (pathFromArgument != null && path.startsWith(pathFromArgument)) {
                   return "admin";
               }
           }
           return "administrators";
       }
   }
   ```

1. Voeg in de **Modellen** redacteur, de dynamische deelnemersstap aan het werkschema toe gebruikend de generische **Dynamische Stap van de Deelnemer** component.
1. Selecteer in het dialoogvenster Bewerken het tabblad **Deelnemerkiezer** en selecteer de gewenste implementatie.
1. Als u argumenten in uw code gebruikt plaats **Argumenten van het Proces**. In dit voorbeeld: `/content/we-retail/de`.
1. Sla de wijzigingen op voor zowel de stap als het workflowmodel.

### Een kiezer voor deelnemers ontwikkelen met behulp van een ECMA-script {#developing-a-participant-chooser-using-an-ecma-script}

U kunt een manuscript tot stand brengen ECMA dat de gebruiker selecteert die het het werkpunt wordt toegewezen dat **Stap van de Deelnemer** produceert. Het script moet een functie met de naam `getParticipant` bevatten die geen argumenten vereist en een `String` retourneert die de id van een gebruiker of groep bevat.

Scripts bevinden zich in de JCR-opslagplaats en worden daar uitgevoerd.

De volgende tabel bevat een lijst met variabelen die directe toegang bieden tot Java-workflowobjecten in uw scripts.

| Java-klasse | Naam scriptvariabele |
|---|---|
| `com.adobe.granite.workflow.exec.WorkItem` | `graniteWorkItem` |
| `com.adobe.granite.workflow.WorkflowSession` | `graniteWorkflowSession` |
| `String[]` (bevat procesargumenten) | `args` |
| `com.adobe.granite.workflow.metadata.MetaDataMap` | `metaData` |
| `org.apache.sling.scripting.core.impl.InternalScriptHelper` | `sling` |

```
function getParticipant() {
    var workflowData = graniteWorkItem.getWorkflowData();
    if (workflowData.getPayloadType() == "JCR_PATH") {
        var path = workflowData.getPayload().toString();
        if (path.indexOf("/content/we-retail/de") == 0) {
            return "admin";
        } else {
            return "administrators";
        }
    }
}
```

1. Maak het script (bijvoorbeeld met CRXDE Lite) en sla het op in de opslagplaats onder `/apps/myapp/workflow/scripts`
1. Als u een titel wilt opgeven die het script identificeert in het dialoogvenster **Processtap** bewerken, voegt u de volgende eigenschappen toe aan de `jcr:content`-node van uw script:

   | Naam | Type | Waarde |
   |---|---|---|
   | `jcr:mixinTypes` | `Name[]` | `mix:title` |
   | `jcr:title` | `String` | De naam die moet worden weergegeven in het dialoogvenster Bewerken. |

1. Bewerk de [Dynamic Participant Step](/help/sites-developing/workflows-step-ref.md#dynamic-participant-step)-instantie en geef op welk script moet worden gebruikt.

## Workflowpakketten verwerken {#handling-workflow-packages}

[Workflowpakket ](/help/sites-authoring/workflows-applying.md#specifying-workflow-details-in-the-create-workflow-wizard) kan worden doorgegeven aan een workflow voor verwerking. Workflowpakketten bevatten verwijzingen naar bronnen zoals pagina&#39;s en elementen.

>[!NOTE]
>
>De volgende stappen in het workflowproces accepteren workflowpakketten voor activering van bulkpagina&#39;s:
>
>* [`com.day.cq.wcm.workflow.process.ActivatePageProcess`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/workflow/process/ActivatePageProcess.html)
>* [`com.day.cq.wcm.workflow.process.DeactivatePageProcess`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/workflow/process/DeactivatePageProcess.html)

>



U kunt workflowstappen ontwikkelen om de pakketbronnen te verkrijgen en deze te verwerken. De volgende leden van het `com.day.cq.workflow.collection`-pakket bieden toegang tot workflowpakketten:

* `ResourceCollection`: Workflowpakketklasse.
* `ResourceCollectionUtil`: Gebruik om voorwerpen terug te winnen ResourceCollection.
* `ResourceCollectionManager`: Hiermee maakt en haalt u verzamelingen op. Een implementatie wordt opgesteld als dienst OSGi.

In het volgende voorbeeld van de Java-klasse ziet u hoe u pakketbronnen kunt verkrijgen:

```java
package com.adobe.example;

import java.util.ArrayList;
import java.util.List;

import com.day.cq.workflow.WorkflowException;
import com.day.cq.workflow.WorkflowSession;
import com.day.cq.workflow.collection.ResourceCollection;
import com.day.cq.workflow.collection.ResourceCollectionManager;
import com.day.cq.workflow.collection.ResourceCollectionUtil;
import com.day.cq.workflow.exec.WorkItem;
import com.day.cq.workflow.exec.WorkflowData;
import com.day.cq.workflow.exec.WorkflowProcess;
import com.day.cq.workflow.metadata.MetaDataMap;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.osgi.framework.Constants;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import javax.jcr.Node;
import javax.jcr.PathNotFoundException;
import javax.jcr.RepositoryException;
import javax.jcr.Session;

@Component
@Service
public class LaunchBulkActivate implements WorkflowProcess {

 private static final Logger log = LoggerFactory.getLogger(LaunchBulkActivate.class);

 @Property(value="Bulk Activate for Launches")
  static final String PROCESS_NAME ="process.label";
 @Property(value="A sample workflow process step to support Launches bulk activation of pages")
 static final String SERVICE_DESCRIPTION = Constants.SERVICE_DESCRIPTION;

 @Reference
 private ResourceCollectionManager rcManager;
public void execute(WorkItem workItem, WorkflowSession workflowSession) throws Exception {
    Session session = workflowSession.getSession();
    WorkflowData data = workItem.getWorkflowData();
    String path = null;
    String type = data.getPayloadType();
    if (type.equals(TYPE_JCR_PATH) && data.getPayload() != null) {
        String payloadData = (String) data.getPayload();
        if (session.itemExists(payloadData)) {
            path = payloadData;
        }
    } else if (data.getPayload() != null && type.equals(TYPE_JCR_UUID)) {
        Node node = session.getNodeByUUID((String) data.getPayload());
        path = node.getPath();
    }

    // CUSTOMIZED CODE IF REQUIRED....

    if (path != null) {
        // check for resource collection
        ResourceCollection rcCollection = ResourceCollectionUtil.getResourceCollection((Node)session.getItem(path), rcManager);
        // get list of paths to replicate (no resource collection: size == 1
        // otherwise size >= 1
        List<String> paths = getPaths(path, rcCollection);
        for (String aPath: paths) {

            // CUSTOMIZED CODE....

        }
    } else {
        log.warn("Cannot process because path is null for this " + "workitem: " + workItem.toString());
    }
}

/**
 * helper
 */
private List<String> getPaths(String path, ResourceCollection rcCollection) {
    List<String> paths = new ArrayList<String>();
    if (rcCollection == null) {
        paths.add(path);
    } else {
        log.debug("ResourceCollection detected " + rcCollection.getPath());
        // this is a resource collection. the collection itself is not
        // replicated. only its members
        try {
            List<Node> members = rcCollection.list(new String[]{"cq:Page", "dam:Asset"});
            for (Node member: members) {
                String mPath = member.getPath();
                paths.add(mPath);
            }
        } catch(RepositoryException re) {
            log.error("Cannot build path list out of the resource collection " + rcCollection.getPath());
        }
    }
    return paths;
}
}
```

## Voorbeeld: Aangepaste stappen maken {#example-creating-a-custom-step}

Een gemakkelijke manier om uw eigen douanestap te beginnen te creëren is een bestaande stap van te kopiëren:

`/libs/cq/workflow/components/model`

### De basisstap {#creating-the-basic-step} maken

1. Maak het pad opnieuw onder /apps; bijvoorbeeld:

   `/apps/cq/workflow/components/model`

   De nieuwe mappen zijn van het type `nt:folder`:

   ```xml
   - apps
     - cq
       - workflow (nt:folder)
         - components (nt:folder)
           - model (nt:folder)
   ```

   >[!NOTE]
   >
   >Deze stap is niet van toepassing op de klassieke UI Model redacteur.

1. Plaats de gekopieerde stap vervolgens in de map /apps; zoals:

   `/apps/cq/workflow/components/model/myCustomStep`

   Hier is het resultaat van onze voorbeeld aangepaste stap:

   ![wf-34](assets/wf-34.png)

   >[!CAUTION]
   >
   >Omdat in standaard UI, slechts de titel en niet de details niet op de kaart worden getoond, `details.jsp` is niet nodig aangezien het voor de klassieke redacteur UI was.

1. Pas de volgende eigenschappen toe op het knooppunt:

   `/apps/cq/workflow/components/model/myCustomStep`

   **Eigenschappen van belang:**

   * `sling:resourceSuperType`

      Moet overerven van een bestaande stap.

      In dit voorbeeld overerven wij van de basisstap bij `cq/workflow/components/model/step`, maar u kunt andere super types zoals `participant`, `process`, enz. gebruiken.

   * `jcr:title`

      Wordt de titel weergegeven wanneer de component in de stapbrowser wordt weergegeven (linkerdeelvenster van de werkstroommodeleditor).

   * `cq:icon`

      Wordt gebruikt om een [koraalpictogram](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) voor de stap op te geven.

   * `componentGroup`

      Moet een van de volgende items zijn:

      * Workflow voor samenwerking
      * DAM-workflow
      * Forms Workflow
      * Projecten
      * WCM-workflow
      * Workflow

   ![wf-35](assets/wf-35.png)

1. U kunt nu een workflowmodel openen voor bewerking. In stappen kunt u browser filtreren om **Mijn Stap van de Douane** te zien:

   ![wf-34](assets/wf-36.png)

   Als u **Mijn aangepaste stap** op het model sleept, wordt de kaart weergegeven:

   ![wf-37](assets/wf-37.png)

   Als er geen `cq:icon` voor de stap is gedefinieerd, wordt een standaardpictogram weergegeven met de eerste twee letters van de titel. Bijvoorbeeld:

   ![wf-38](assets/wf-38.png)

#### Het bepalen van Stap vormt Dialoogvenster {#defining-the-step-configure-dialog}

Na [Creërend de BasisStap](#creating-the-basic-step), bepaal de stap **vorm** als volgt:

1. Configureer de eigenschappen op het knooppunt `cq:editConfig` als volgt:

   **Eigenschappen van belang:**

   * `cq:inherit`

      Wanneer ingesteld op `true`, erft uw step-component eigenschappen van de stap die u hebt opgegeven in `sling:resourceSuperType`.

   * `cq:disableTargeting`

      Stel dit naar wens in.
   ![wf-39](assets/wf-39.png)

1. Configureer de eigenschappen op het knooppunt `cq:formsParameter` als volgt:

   **Eigenschappen van belang:**

   * `jcr:title`

      Plaatst de standaardtitel op de step kaart in de modelkaart en in het **Title** gebied van **Mijn Douane - de configuratiedialoog van de Stap Eigenschappen**.

   * U kunt ook uw eigen aangepaste eigenschappen definiëren.

   ![wf-40](assets/wf-40.png)

1. Vorm de eigenschappen op de knoop `cq:listeners`.

   Met het knooppunt `cq:listener` en de bijbehorende eigenschappen kunt u gebeurtenishandlers instellen die reageren op gebeurtenissen in de UI-modeleditor met aanraakbediening. zoals het slepen van een stap naar een modelpagina of het bewerken van stapeigenschappen.

   **Belangeneigenschappen:**

   * `afterMove: REFRESH_PAGE`
   * `afterdelete: CQ.workflow.flow.Step.afterDelete`
   * `afteredit: CQ.workflow.flow.Step.afterEdit`
   * `afterinsert: CQ.workflow.flow.Step.afterInsert`

   Deze configuratie is essentieel voor het goed functioneren van de redacteur. In de meeste gevallen mag deze configuratie niet worden gewijzigd.

   Nochtans, staat het plaatsen `cq:inherit` aan waar (op de `cq:editConfig` knoop, zie hierboven) u toe om deze configuratie te erven, zonder het te moeten het uitdrukkelijk in uw stapdefinitie omvatten. Als er geen overerving is, moet u dit knooppunt met de volgende eigenschappen en waarden toevoegen.

   In dit voorbeeld is overerving geactiveerd zodat we het knooppunt `cq:listeners` kunnen verwijderen en de stap blijft correct.

   ![wf-41](assets/wf-41.png)

1. U kunt nu een instantie van uw stap toevoegen aan een workflowmodel. Wanneer u **Configure** de stap zult u de dialoog zien:

   ![wf-42](assets/wf-42.png) ![wf-43](assets/wf-43.png)

#### Sampleopmaak gebruikt in dit voorbeeld {#sample-markup-used-in-this-example}

Opmaak voor een aangepaste stap wordt weergegeven in het knooppunt `.content.xml` van de hoofdcomponent. Het voorbeeld `.content.xml` dat voor dit voorbeeld wordt gebruikt:

`/apps/cq/workflow/components/model/myCustomStep/.content.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:icon="bell"
    jcr:primaryType="cq:Component"
    jcr:title="My Custom Step"
    sling:resourceSuperType="cq/workflow/components/model/process"
    allowedParents="[*/parsys]"
    componentGroup="Workflow"/>
```

Het voorbeeld `_cq_editConfig.xml` dat in dit voorbeeld wordt gebruikt:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
    cq:disableTargeting="{Boolean}true"
    cq:inherit="{Boolean}true"
    jcr:primaryType="cq:EditConfig">
    <cq:formParameters
        jcr:primaryType="nt:unstructured"
        jcr:title="My Custom Step Card"
        SAMPLE_PROPERY="sample value"/>
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="CQ.workflow.flow.Step.afterDelete"
        afteredit="CQ.workflow.flow.Step.afterEdit"
        afterinsert="CQ.workflow.flow.Step.afterInsert"
        afterMove="REFRESH_PAGE"/>
</jcr:root>
```

Het voorbeeld `_cq_dialog/.content.xml` dat in dit voorbeeld wordt gebruikt:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
    jcr:primaryType="nt:unstructured"
    jcr:title="My Custom - Step Properties"
    sling:resourceType="cq/gui/components/authoring/dialog">
    <content
        jcr:primaryType="nt:unstructured"
        sling:resourceType="granite/ui/components/coral/foundation/tabs">
        <items jcr:primaryType="nt:unstructured">
            <common
                cq:hideOnEdit="true"
                jcr:primaryType="nt:unstructured"
                jcr:title="Common"
                sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns"/>
            <process
                cq:hideOnEdit="true"
                jcr:primaryType="nt:unstructured"
                jcr:title="Process"
                sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns"/>
            <mycommon
                jcr:primaryType="nt:unstructured"
                jcr:title="Common"
                sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                <items jcr:primaryType="nt:unstructured">
                    <columns
                        jcr:primaryType="nt:unstructured"
                        sling:resourceType="granite/ui/components/coral/foundation/container">
                        <items jcr:primaryType="nt:unstructured">
                            <title
                                jcr:primaryType="nt:unstructured"
                                sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                fieldLabel="Title"
                                name="./jcr:title"/>
                            <description
                                jcr:primaryType="nt:unstructured"
                                sling:resourceType="granite/ui/components/coral/foundation/form/textarea"
                                fieldLabel="Description"
                                name="./jcr:description"/>
                        </items>
                    </columns>
                </items>
            </mycommon>
            <advanced
                jcr:primaryType="nt:unstructured"
                jcr:title="Advanced"
                sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                <items jcr:primaryType="nt:unstructured">
                    <columns
                        jcr:primaryType="nt:unstructured"
                        sling:resourceType="granite/ui/components/coral/foundation/container">
                        <items jcr:primaryType="nt:unstructured">
                            <email
                                jcr:primaryType="nt:unstructured"
                                sling:resourceType="granite/ui/components/coral/foundation/form/checkbox"
                                fieldDescription="Notify user via email."
                                fieldLabel="Email"
                                name="./metaData/PROCESS_AUTO_ADVANCE"
                                text="Notify user via email."
                                value="true"/>
                        </items>
                    </columns>
                </items>
            </advanced>
        </items>
    </content>
</jcr:root>
```

>[!NOTE]
>
>Let op de algemene knooppunten en procesknooppunten in de dialoogdefinitie. Deze worden geërft van de processtap die wij als supertype voor onze douanestreep hebben gebruikt:
>
>`sling:resourceSuperType : cq/workflow/components/model/process`

>[!NOTE]
>
>Dialoogvensters van de klassieke UI-modeleditor werken nog steeds met de standaardinterface-editor met aanraakbediening.
>
>Hoewel AEM [moderniseringshulpmiddelen](/help/sites-developing/modernization-tools.md) heeft als u uw klassieke de stapdialogen van UI aan standaarddialogen wilt bevorderen UI. Na de conversie zijn er nog enkele handmatige verbeteringen die in bepaalde gevallen in de dialoog kunnen worden aangebracht.
>
>* Wanneer een geüpgrade dialoogvenster leeg is, kunt u dialoogvensters bekijken in `/libs` met vergelijkbare functionaliteit als voorbeelden van hoe u een oplossing kunt bieden. Bijvoorbeeld:
   >
   >
* `/libs/cq/workflow/components/model`
>* `/libs/cq/workflow/components/workflow`
>* `/libs/dam/components`
>* `/libs/wcm/workflow/components/autoassign`
>* `/libs/cq/projects`

>
>  
U moet niets in `/libs` wijzigen, eenvoudig gebruiken hen als voorbeelden. Als u een van de bestaande stappen wilt gebruiken, kopieert u deze naar `/apps` en wijzigt u ze daar.
