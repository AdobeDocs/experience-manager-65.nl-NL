---
title: Uitbreiding van workflowfunctionaliteit
description: Leer hoe u de functionaliteit van de Adobe Experience Manager-workflow kunt uitbreiden.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 9e205912-50a6-414a-b8d4-a0865269d0e0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3499'
ht-degree: 0%

---

# Uitbreiding van workflowfunctionaliteit{#extending-workflow-functionality}

Dit onderwerp beschrijft hoe te om de componenten van de douanestap voor uw werkschema&#39;s te ontwikkelen, toen hoe te programmatically met werkschema&#39;s in wisselwerking te staan.

Het maken van een aangepaste workflowstap omvat de volgende activiteiten:

* Ontwikkel de component van de werkschemastap.
* Voer de step functionaliteit als dienst OSGi of een manuscript ECMA uit.

U kunt [communiceren met uw workflows vanuit uw programma&#39;s en scripts](/help/sites-developing/workflows-program-interaction.md).

## Workflowstapcomponenten - De basisbeginselen {#workflow-step-components-the-basics}

Een workflowcomponent definieert de vormgeving en het gedrag van de stap bij het maken van workflowmodellen:

* De categorie en de stapnaam in het werkschemahulpje.
* De vormgeving van de stap in workflowmodellen.
* Het dialoogvenster Bewerken voor het configureren van componenteigenschappen.
* De service of het script dat wordt uitgevoerd bij uitvoering.

Zoals met [alle componenten](/help/sites-developing/components.md), worden componenten van workflowstappen overgenomen van de component die is opgegeven voor de component `sling:resourceSuperType` eigenschap. Het volgende diagram toont de hiërarchie van `cq:component` knooppunten die de basis vormen van alle workflowstapcomponenten. Het diagram bevat ook de **Processtap**, **Stap deelnemer**, en **Dynamische deelnemersstap** componenten, aangezien dit de gemeenschappelijkste (en fundamentele) uitgangspunt voor het ontwikkelen van de componenten van de douanestappen zijn.

![aem_wf_componentinherit](assets/aem_wf_componentinherit.png)

>[!CAUTION]
>
>U ***moet*** niets wijzigen in het dialoogvenster `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het bestaat in `/libs` krachtens `/apps`
>2. Breng wijzigingen aan in `/apps`

De `/libs/cq/workflow/components/model/step` component is de dichtstbijzijnde gangbare voorouder van de **Processtap**, **Stap deelnemer**, en **Dynamische deelnemersstap**, die alle de volgende items overerven:

* `step.jsp`

  De `step.jsp` wordt de titel van de step-component weergegeven wanneer deze aan een model wordt toegevoegd.

  ![wf-22-1](assets/wf-22-1.png)

* [cq:dialoogvenster](/help/sites-developing/developing-components.md#creating-and-configuring-a-dialog)

  Een dialoogvenster met de volgende tabbladen:

   * **Vaak**: voor het bewerken van de titel en beschrijving.
   * **Geavanceerd**: voor het bewerken van eigenschappen van e-mailmeldingen.

  ![wf-44](assets/wf-44.png) ![wf-45](assets/wf-45.png)

  >[!NOTE]
  >
  >Wanneer de tabbladen van het dialoogvenster Bewerken van een stapcomponent niet overeenkomen met deze standaardweergave, heeft de stapcomponent scripts, knoopeigenschappen of dialoogtabbladen gedefinieerd die deze overgeërfde tabbladen overschrijven.

### ECMA-scripts {#ecma-scripts}

De volgende objecten zijn beschikbaar (afhankelijk van het type stap) in ECMA-scripts:

* [WorkItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/WorkItem.html) workItem
* [WorkflowSession](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/WorkflowSession.html) workflowSession
* [WorkflowData](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/WorkflowData.html) workflowData
* `args`: array met de procesargumenten.

* `sling`: toegang tot andere osgi-diensten.
* `jcrSession`

### MetaDataMaps {#metadatamaps}

U kunt metagegevens over workflows gebruiken om de informatie die tijdens de levensduur van de workflow vereist is, voort te zetten. Een algemene vereiste voor workflowstappen is dat gegevens voor toekomstig gebruik in de workflow moeten worden behouden of dat de blijvend opgeslagen gegevens moeten worden opgehaald.

Er zijn drie typen objecten MetaDataMap - voor `Workflow`, `WorkflowData` en `WorkItem` objecten. Ze hebben allemaal hetzelfde doel: metagegevens opslaan.

Een WorkItem heeft zijn eigen MetaDataMap die slechts kan worden gebruikt terwijl dat werkpunt (bijvoorbeeld, stap) loopt.

Beide `Workflow` en `WorkflowData` metadatamaps worden over de gehele werkstroom gedeeld. In deze gevallen wordt het aanbevolen alleen de `WorkflowData` metagegevensoverzicht.

## Aangepaste workflowonderdelen maken {#creating-custom-workflow-step-components}

Componenten voor workflowstappen kunnen [gemaakt op dezelfde manier als een andere component](/help/sites-developing/components.md).

Om van één van de (bestaande) componenten van de basisstap over te erven, voeg het volgende bezit aan toe `cq:Component` knooppunt:

* Naam: `sling:resourceSuperType`
* Type: `String`
* Waarde: een van de volgende paden die wordt omgezet in een basiscomponent:

   * `cq/workflow/components/model/process`
   * `cq/workflow/components/model/participant`
   * `cq/workflow/components/model/dynamic_participant`

### De standaardtitel en -beschrijving opgeven voor instanties Step {#specifying-the-default-title-and-description-for-step-instances}

Gebruik de volgende procedure om standaardwaarden op te geven voor de **Titel** en **Beschrijving** velden op de **Vaak** tab.

>[!NOTE]
>
>De veldwaarden worden weergegeven op de stapinstantie wanneer aan beide volgende voorwaarden wordt voldaan:
>
>* In het dialoogvenster Bewerken van de stap worden de titel en de beschrijving opgeslagen op de volgende locaties: >
>* `./jcr:title`
>* `./jcr:description` locaties
>
>  Aan deze vereiste wordt voldaan wanneer in het dialoogvenster Bewerken het tabblad Algemeen wordt gebruikt dat `/libs/cq/flow/components/step/step` component implementeert.
>
>* De step-component of een voorouder van de component overschrijft de component niet `step.jsp` die de `/libs/cq/flow/components/step/step` component implementeert.

1. Onder de `cq:Component` knooppunt, voeg het volgende knooppunt toe:

   * Naam: `cq:editConfig`
   * Type: `cq:EditConfig`

   >[!NOTE]
   >
   >Voor meer informatie over de knoop cq:editConfig, zie [Het bewerkingsgedrag van een component configureren](/help/sites-developing/developing-components.md#configuring-the-edit-behavior).

1. Onder de `cq:EditConfig` knooppunt, voeg het volgende knooppunt toe:

   * Naam: `cq:formParameters`
   * Type: `nt:unstructured`

1. Toevoegen `String` eigenschappen van de volgende namen voor de `cq:formParameters` knooppunt:

   * `jcr:title`: De waarde vult de **Titel** van het **Vaak** tab.
   * `jcr:description`: De waarde vult de **Beschrijving** van het **Vaak** tab.

### Eigenschapwaarden opslaan in werkstroommetagegevens {#saving-property-values-in-workflow-metadata}

>[!NOTE]
>
>Zie [Gegevens behouden en openen](#persisting-and-accessing-data). Zie met name voor informatie over het benaderen van de eigenschapswaarde tijdens runtime [Dialoogvenstereigenschapswaarden openen bij uitvoering](#accessing-dialog-property-values-at-runtime).

De eigenschap name van `cq:Widget` Hiermee wordt het JCR-knooppunt opgegeven dat de waarde van de widget opslaat. Wanneer widgets in het dialoogvenster met workflowstapcomponenten waarden opslaan onder de `./metaData` node, de waarde wordt toegevoegd aan de workflow `MetaDataMap`.

Een tekstveld in een dialoogvenster is bijvoorbeeld een `cq:Widget` knooppunt met de volgende eigenschappen:

| Naam | Type | Waarde |
|---|---|---|
| `xtype` | `String` | `textarea` |
| `name` | `String` | `./metaData/subject` |
| `fieldLabel` | `String` | `Email Subject` |

De waarde die in dit tekstveld wordt opgegeven, wordt toegevoegd aan de instantie van de werkstroom ` [MetaDataMap](#metadatamaps)` en is gekoppeld aan de `subject` toets.

>[!NOTE]
>
>Wanneer de toets `PROCESS_ARGS`, is de waarde gemakkelijk beschikbaar in ECMA manuscriptimplementaties via `args` variabele. In dit geval is de waarde van de eigenschap name `./metaData/PROCESS_ARGS.`

### De stapimplementatie overschrijven {#overriding-the-step-implementation}

Elke component van de basisstap laat de ontwikkelaars van het werkschemamodel toe om de volgende zeer belangrijke eigenschappen in ontwerptijd te vormen:

* Processtap: de service of het ECMA-script dat bij uitvoering moet worden uitgevoerd.
* Stap van de deelnemer: identiteitskaart van de gebruiker die het geproduceerde het werkpunt wordt toegewezen.
* De dynamische Stap van de Deelnemer: De dienst of het manuscript ECMA dat identiteitskaart van de gebruiker selecteert die het het werkpunt wordt toegewezen.

Om de component voor gebruik in een specifiek werkschemascenario te concentreren, vorm de belangrijkste eigenschap in het ontwerp en verwijder de capaciteit voor modelontwikkelaars om het te veranderen.

1. Voeg onder het cq:component-knooppunt het volgende knooppunt toe:

   * Naam: `cq:editConfig`
   * Type: `cq:EditConfig`

   Voor meer informatie over de knoop cq:editConfig, zie [Het bewerkingsgedrag van een component configureren](/help/sites-developing/developing-components.md#configuring-the-edit-behavior).

1. Voeg onder het knooppunt cq:EditConfig het volgende knooppunt toe:

   * Naam: `cq:formParameters`
   * Type: `nt:unstructured`

1. Voeg een `String` eigenschap aan de `cq:formParameters` knooppunt. Het supertype van de component bepaalt de naam van het bezit:

   * Processtap `PROCESS`
   * Stap deelnemer: `PARTICIPANT`
   * Stap dynamische deelnemer: `DYNAMIC_PARTICIPANT`

1. Geef de waarde van de eigenschap op:

   * `PROCESS`: De weg aan het manuscript ECMA of PID van de dienst die het stapgedrag uitvoert.
   * `PARTICIPANT`: De id van de gebruiker aan wie het werkitem is toegewezen.
   * `DYNAMIC_PARTICIPANT`: De weg aan het manuscript ECMA of PID van de dienst die de gebruiker selecteert om het het werkpunt toe te wijzen.

1. Om de capaciteit van modelontwikkelaars te verwijderen om uw bezitswaarden te veranderen, vervang de dialoog van het componentensupertype.

### Forms en dialoogvensters toevoegen aan stappen van deelnemers {#adding-forms-and-dialogs-to-participant-steps}

Pas uw component van de deelnemersstap aan om eigenschappen te verstrekken die in worden gevonden [Stap voor deelnemer aan formulier](/help/sites-developing/workflows-step-ref.md#form-participant-step) en [Stap deelnemer van dialoogvenster](/help/sites-developing/workflows-step-ref.md#dialog-participant-step) componenten:

* Een formulier presenteren aan de gebruiker wanneer deze het gegenereerde werkitem opent.
* Presenteer een aangepast dialoogvenster aan de gebruiker wanneer deze het gegenereerde werkitem voltooit.

Voer de volgende procedure op uw nieuwe component uit (zie [Aangepaste workflowonderdelen maken](#creating-custom-workflow-step-components)):

1. Onder de `cq:Component` knooppunt, voeg het volgende knooppunt toe:

   * Naam: `cq:editConfig`
   * Type: `cq:EditConfig`

   Voor meer informatie over de knoop cq:editConfig, zie [Het bewerkingsgedrag van een component configureren](/help/sites-developing/components-basics.md#edit-behavior).

1. Voeg onder het knooppunt cq:EditConfig het volgende knooppunt toe:

   * Naam: `cq:formParameters`
   * Type: `nt:unstructured`

1. Als u een formulier wilt presenteren terwijl de gebruiker het werkitem opent, voegt u de volgende eigenschap toe aan de `cq:formParameters` knooppunt:

   * Naam: `FORM_PATH`
   * Type: `String`
   * Waarde: het pad dat wordt omgezet in het formulier

1. Als u een aangepast dialoogvenster wilt weergeven wanneer de gebruiker het werkitem heeft voltooid, voegt u de volgende eigenschap toe aan de `cq:formParameters` node

   * Naam: `DIALOG_PATH`
   * Type: `String`
   * Waarde: het pad dat wordt omgezet in het dialoogvenster

### Werking voor Workflowstap configureren {#configuring-the-workflow-step-runtime-behavior}

Onder de `cq:Component` knooppunt, toevoegen `cq:EditConfig` knooppunt. Hieronder ziet u een `nt:unstructured` node (moet een naam hebben `cq:formParameters`) en aan dat knooppunt de volgende eigenschappen toevoegen:

* Naam: `PROCESS_AUTO_ADVANCE`

   * Type: `Boolean`
   * Waarde:

      * wanneer ingesteld op `true` de workflow wordt in die stap uitgevoerd en vervolg - dit is standaard en ook aanbevolen
      * wanneer `false`, de workflow wordt uitgevoerd en gestopt; hiervoor is extra verwerking nodig, dus `true` wordt aanbevolen

* Naam: `DO_NOTIFY`

   * Type: `Boolean`
   * Waarde: geeft aan of e-mailmeldingen moeten worden verzonden voor stappen voor gebruikersdeelname (en gaat ervan uit dat de mailserver correct is geconfigureerd)

## Gegevens behouden en openen {#persisting-and-accessing-data}

### Gegevens behouden voor volgende workflowstappen {#persisting-data-for-subsequent-workflow-steps}

U kunt werkschemagegevens gebruiken om informatie voort te zetten die tijdens het leven van het werkschema - en tussen stappen wordt vereist. Een algemene vereiste voor workflowstappen is dat gegevens voor toekomstig gebruik behouden blijven of dat de blijvend gegevens uit eerdere stappen worden opgehaald.

De metagegevens van de workflow worden opgeslagen in een [`MetaDataMap`](#metadatamaps) object. De Java API biedt de [`Workflow.getWorkflowData`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/Workflow.html) methode om een [`WorkflowData`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkflowData.html) object dat het juiste `MetaDataMap` object. Dit `WorkflowData` `MetaDataMap` -object beschikbaar is voor de OSGi-service of het ECMA-script van een step-component.

#### Java {#java}

De methode voor het uitvoeren van het `WorkflowProcess` de uitvoering wordt goedgekeurd `WorkItem` object. Gebruik dit object om de `WorkflowData` object voor de huidige werkstroominstantie. In het volgende voorbeeld wordt een item aan de workflow toegevoegd `MetaDataMap` object en logt elk item vervolgens in. Het item (&quot;mijnsleutel&quot;, &quot;Mijn stapwaarde&quot;) is beschikbaar voor volgende stappen in de workflow.

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

De `graniteWorkItem` variable is the ECMA script representation of the current `WorkItem` Java-object. Daarom kunt u `graniteWorkItem` variabele voor het verkrijgen van de metagegevens van de workflow. Het volgende ECMA-script kan worden gebruikt om een **Processtap** om een item aan de workflow toe te voegen `MetaDataMap` en registreer elk item vervolgens. Deze items zijn vervolgens beschikbaar voor volgende stappen in de workflow.

>[!NOTE]
>
>De `metaData` De variabele die onmiddellijk beschikbaar voor het step manuscript is de meta-gegevens van de stap. De metagegevens van de stap verschillen van de metagegevens van de workflow.

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

De `MetaDataMap` Het object met workflowinstanties is handig voor het opslaan en ophalen van gegevens gedurende de gehele levensduur van de workflow. Voor de implementatie van workflowcomponenten, `MetaDataMap` is vooral nuttig om componentenbezitswaarden bij runtime terug te winnen.

>[!NOTE]
>
>Voor informatie over het configureren van het dialoogvenster met componenten om eigenschappen op te slaan als metagegevens over workflows raadpleegt u [Eigenschapwaarden opslaan in werkstroommetagegevens](#saving-property-values-in-workflow-metadata).

De workflow `MetaDataMap` is beschikbaar voor Java- en ECMA-scriptprocesimplementaties:

* In Java-implementaties van de WorkflowProcess-interface `args` parameter is `MetaDataMap` object voor de workflow.

* In ECMA manuscriptimplementaties, is de waarde beschikbaar gebruikend `args` en `metadata` variabelen.

### Voorbeeld: de argumenten van de processtapcomponent ophalen {#example-retrieving-the-arguments-of-the-process-step-component}

Het dialoogvenster Bewerken van het dialoogvenster **Processtap** bevat de **Argumenten** eigenschap. De waarde van **Argumenten** eigenschap wordt opgeslagen in de metagegevens van de workflow en is gekoppeld aan de eigenschap `PROCESS_ARGS` toets.

In het volgende diagram wordt de waarde van de **Argumenten** eigenschap is `argument1, argument2`:

![wf-24](assets/wf-24.png)

#### Java {#java-1}

De volgende Java-code is `execute` methode voor `WorkflowProcess` uitvoering. De methode registreert de waarde in de `args` `MetaDataMap` die verband houdt met de `PROCESS_ARGS` toets.

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

Het volgende ECMA-script wordt gebruikt als het proces voor het **Processtap**. Het registreert het aantal argumenten en de argumentwaarden:

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
>Voor een ander voorbeeld van het opslaan van componenteneigenschappen in werkschemagegevens, zie Voorbeeld: Creeer een Stap van de Werkstroom van het Registratieprogramma. In dit voorbeeld wordt een dialoogvenster weergegeven waarin de metagegevenswaarde wordt gekoppeld aan een andere sleutel dan PROCESS_ARGS.

### Scripts en procesargumenten {#scripts-and-process-arguments}

Binnen een script voor een **Processtap** component, argumenten zijn beschikbaar via `args` object.

Wanneer u een component met een aangepaste stap maakt, `metaData` is beschikbaar in een script. Dit object is beperkt tot één tekenreeksargument.

## Implementaties van processtappen ontwikkelen {#developing-process-step-implementations}

Wanneer de processtappen tijdens het proces van een werkschema zijn begonnen, verzenden de stappen een verzoek naar een dienst OSGi of voeren een manuscript ECMA uit. Ontwikkel de dienst of het manuscript ECMA dat de acties uitvoert die uw werkschema vereist.

>[!NOTE]
>
>Voor informatie over het associëren van uw component van de Stap van het Proces met de dienst of het manuscript, zie [Processtap](/help/sites-developing/workflows-step-ref.md#process-step) of [De stapimplementatie overschrijven](#overriding-the-step-implementation).

### Een processtap implementeren met een Java-klasse {#implementing-a-process-step-with-a-java-class}

Een processtap definiëren als een OSGI-servicecomponent (Java-bundel):

1. Maak de bundel en plaats deze in de OSGI-container. Raadpleeg de documentatie over het maken van een bundel met [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) of [Eclipse](/help/sites-developing/howto-projects-eclipse.md).

   >[!NOTE]
   >
   >De SDAB-component moet de `WorkflowProcess` interface met zijn `execute()` methode. Zie de voorbeeldcode hieronder.

   >[!NOTE]
   >
   >De pakketnaam moet worden toegevoegd aan de `<*Private-Package*>` van de `maven-bundle-plugin` configuratie.

1. Voeg het SCR bezit toe `process.label`  en stelt de waarde in die u nodig hebt. Dit zal de naam zijn die uw processtap zoals wanneer het gebruiken van generische wordt vermeld **Processtap** component. Zie het onderstaande voorbeeld.
1. In de **Modellen** de redacteur, voegt de processtap aan het werkschema toe gebruikend generisch **Processtap** component.
1. In het dialoogvenster Bewerken (van het dialoogvenster **Processtap**), ga naar de **Proces** en selecteert u de procesimplementatie.
1. Als u argumenten in uw code gebruikt, stelt u de **Procesargumenten**. Bijvoorbeeld: false.
1. Sla de wijzigingen op voor zowel de stap als het workflowmodel (linksboven in de modeleditor).

De methoden java, respectievelijk de klassen die de uitvoerbare Java-methode implementeren, worden geregistreerd als OSGI-services, waarmee u tijdens runtime op elk moment methoden kunt toevoegen.

De volgende component OSGI voegt de eigenschap toe `approved` naar het knooppunt met pagina-inhoud wanneer de laadbewerking een pagina is:

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

### ECMAScript gebruiken {#using-ecmascript}

Met ECMA-scripts kunnen scriptontwikkelaars processtappen implementeren. De scripts bevinden zich in de JCR-opslagplaats en worden daar uitgevoerd.

In de volgende tabel staan de variabelen die direct beschikbaar zijn voor het verwerken van scripts, waarmee toegang wordt verleend tot objecten van de Java API voor de workflow.

| Java-klasse | Naam scriptvariabele | Beschrijving |
|---|---|---|
| `com.adobe.granite.workflow.exec.WorkItem` | `graniteWorkItem` | De huidige step-instantie. |
| `com.adobe.granite.workflow.WorkflowSession` | `graniteWorkflowSession` | De workflowsessie van de huidige step-instantie. |
| `String[]` (bevat procesargumenten) | `args` | De step-argumenten. |
| `com.adobe.granite.workflow.metadata.MetaDataMap` | `metaData` | De metagegevens van de huidige step-instantie. |
| `org.apache.sling.scripting.core.impl.InternalScriptHelper` | `sling` | Biedt toegang tot de Sling-runtimeomgeving. |

Het volgende voorbeeldscript laat zien hoe u toegang krijgt tot het JCR-knooppunt dat de payload van de workflow vertegenwoordigt. De `graniteWorkflowSession` De variabele wordt aangepast aan een JCR-sessievariabele, die wordt gebruikt om het knooppunt op te halen uit het payload-pad.

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

Het volgende script controleert of de lading een afbeelding is ( `.png` ), maakt u er een zwart-witafbeelding van en slaat u deze op als een knooppunt op hetzelfde niveau.

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

1. Maak het script (bijvoorbeeld met CRXDE Lite) en sla het op in de onderstaande opslagplaats `//apps/workflow/scripts/`
1. Om een titel te specificeren die het manuscript in **Processtap** bewerken, voegt u de volgende eigenschappen toe aan het dialoogvenster `jcr:content` knooppunt van uw script:

   | Naam | Type | Waarde |
   |---|---|---|
   | `jcr:mixinTypes` | `Name[]` | `mix:title` |
   | `jcr:title` | `String` | De naam die moet worden weergegeven in het dialoogvenster Bewerken. |

1. Bewerk de **Processtap** en geeft u het script op dat moet worden gebruikt.

## Deelnemerkiezers ontwikkelen {#developing-participant-choosers}

U kunt deelnemerskiezers ontwikkelen voor **Dynamische deelnemersstap** componenten.

Wanneer een **Dynamische deelnemersstap** is gestart tijdens een werkstroom, moet de stap bepalen aan welke deelnemer het gegenereerde werkitem kan worden toegewezen. Hiervoor moet u een van de volgende stappen uitvoeren:

* verzendt een verzoek naar een dienst OSGi
* voert een manuscript ECMA uit om de deelnemer te selecteren

U kunt de dienst of een manuscript ontwikkelen ECMA dat de deelnemer volgens de vereisten van uw werkschema selecteert.

>[!NOTE]
>
>Voor informatie over het koppelen van uw **Dynamische deelnemersstap** component met de dienst of het manuscript, zie [Dynamische deelnemersstap](/help/sites-developing/workflows-step-ref.md#dynamic-participant-step) of [De stapimplementatie overschrijven](#persisting-and-accessing-data).

### Een kiezer voor deelnemers ontwikkelen met een Java-klasse {#developing-a-participant-chooser-using-a-java-class}

Een deelnemersstap definiëren als een OSGI-servicecomponent (Java-klasse):

1. De SDAB-component moet de `ParticipantStepChooser` interface met zijn `getParticipant()` methode. Zie de voorbeeldcode hieronder.

   Maak de bundel en plaats deze in de OSGI-container.

1. Voeg het SCR bezit toe `chooser.label` en stelt de waarde naar wens in. Dit is de naam die uw deelnemerkiezer in de lijst krijgt met **Dynamische deelnemersstap** component. Zie het voorbeeld:

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

1. In de **Modellen** de redacteur, voegt de dynamische deelnemersstap aan het werkschema toe gebruikend generisch **Dynamische deelnemersstap** component.
1. Selecteer in het dialoogvenster Bewerken de optie **Deelnemerkiezer** en selecteert u de gewenste implementatie.
1. Als u argumenten in uw code gebruikt, stelt u **Procesargumenten**. In dit voorbeeld: `/content/we-retail/de`.
1. Sla de wijzigingen op voor zowel de stap als het workflowmodel.

### Een kiezer voor deelnemers ontwikkelen met behulp van een ECMA-script {#developing-a-participant-chooser-using-an-ecma-script}

U kunt een manuscript tot stand brengen ECMA dat de gebruiker selecteert die het het werkpunt wordt toegewezen dat **Stap deelnemer** wordt gegenereerd. Het script moet een functie met de naam `getParticipant` dat vereist geen argumenten en retourneert een `String` die de id van een gebruiker of groep bevat.

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

1. Maak het script (bijvoorbeeld met CRXDE Lite) en sla het op in de onderstaande opslagplaats `//apps/workflow/scripts`
1. Om een titel te specificeren die het manuscript in **Processtap** bewerken, voegt u de volgende eigenschappen toe aan het dialoogvenster `jcr:content` knooppunt van uw script:

   | Naam | Type | Waarde |
   |---|---|---|
   | `jcr:mixinTypes` | `Name[]` | `mix:title` |
   | `jcr:title` | `String` | De naam die moet worden weergegeven in het dialoogvenster Bewerken. |

1. Bewerk de [Dynamische deelnemersstap](/help/sites-developing/workflows-step-ref.md#dynamic-participant-step) en geeft u het script op dat moet worden gebruikt.

## Workflowpakketten verwerken {#handling-workflow-packages}

[Workflowpakketten](/help/sites-authoring/workflows-applying.md#specifying-workflow-details-in-the-create-workflow-wizard) kan worden doorgegeven aan een workflow voor verwerking. Workflowpakketten bevatten verwijzingen naar bronnen zoals pagina&#39;s en elementen.

>[!NOTE]
>
>De volgende stappen in het workflowproces accepteren workflowpakketten voor activering van bulkpagina&#39;s:
>
>* [`com.day.cq.wcm.workflow.process.ActivatePageProcess`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/workflow/process/ActivatePageProcess.html)
>* [`com.day.cq.wcm.workflow.process.DeactivatePageProcess`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/workflow/process/DeactivatePageProcess.html)
>

U kunt workflowstappen ontwikkelen om de pakketbronnen te verkrijgen en deze te verwerken. De volgende leden van `com.day.cq.workflow.collection` bieden toegang tot workflowpakketten:

* `ResourceCollection`: Workflowpakketklasse.
* `ResourceCollectionUtil`: Gebruik deze operator om ResourceCollection-objecten op te halen.
* `ResourceCollectionManager`: Maakt en haalt verzamelingen op. Een implementatie wordt opgesteld als dienst OSGi.

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

## Voorbeeld: een aangepaste stap maken {#example-creating-a-custom-step}

Een gemakkelijke manier om uw eigen douanestap te beginnen te creëren is een bestaande stap van te kopiëren:

`/libs/cq/workflow/components/model`

### De basisstap maken {#creating-the-basic-step}

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

1. Plaats de gekopieerde stap vervolgens in de map /apps, bijvoorbeeld als:

   `/apps/cq/workflow/components/model/myCustomStep`

   Hier is het resultaat van onze voorbeeld aangepaste stap:

   ![wf-34](assets/wf-34.png)

   >[!CAUTION]
   >
   >Omdat in standaard UI, slechts de titel en niet de details niet op de kaart worden getoond, `details.jsp` is niet nodig zoals voor de klassieke redacteur UI.

1. Pas de volgende eigenschappen toe op het knooppunt:

   `/apps/cq/workflow/components/model/myCustomStep`

   **Eigenschappen van belang:**

   * `sling:resourceSuperType`

     Moet overerven van een bestaande stap.

     In dit voorbeeld overerven we van de basisstap bij `cq/workflow/components/model/step`, maar u kunt andere supertypen gebruiken zoals `participant`, `process`, enzovoort.

   * `jcr:title`

     Wordt de titel weergegeven wanneer de component in de stapbrowser wordt weergegeven (linkerdeelvenster van de werkstroommodeleditor).

   * `cq:icon`

     Wordt gebruikt om een [Koraal, pictogram](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) voor de stap.

   * `componentGroup`

     Moet een van de volgende items zijn:

      * Workflow voor samenwerking
      * DAM-workflow
      * Forms Workflow
      * Projecten
      * WCM-workflow
      * Workflow

   ![wf-35](assets/wf-35.png)

1. U kunt nu een workflowmodel openen voor bewerking. In de browser met stappen kunt u filteren om te zien **Mijn aangepaste stap**:

   ![wf-36](assets/wf-36.png)

   Slepen **Mijn aangepaste stap** op het model wordt de kaart weergegeven:

   ![wf-37](assets/wf-37.png)

   Indien niet `cq:icon` is gedefinieerd voor de stap, wordt een standaardpictogram weergegeven met de eerste twee letters van de titel. Bijvoorbeeld:

   ![wf-38](assets/wf-38.png)

#### Het bepalen van Stap vormt Dialoogvenster {#defining-the-step-configure-dialog}

Na [De basisstap maken](#creating-the-basic-step), definieert u de stap **Configureren** dialoog als volgt:

1. De eigenschappen op het knooppunt configureren `cq:editConfig` als volgt:

   **Eigenschappen van belang:**

   * `cq:inherit`

     Wanneer ingesteld op `true`overerft uw component step eigenschappen van de stap die u hebt opgegeven in `sling:resourceSuperType`.

   * `cq:disableTargeting`

     Stel dit naar wens in.

   ![wf-39](assets/wf-39.png)

1. De eigenschappen op het knooppunt configureren `cq:formsParameter` als volgt:

   **Eigenschappen van belang:**

   * `jcr:title`

     Hiermee stelt u de standaardtitel in voor de stapkaart in het modeloverzicht en in het dialoogvenster **Titel** van het **Mijn aangepaste - stapeigenschappen** configuratiedialoogvenster.

   * U kunt ook uw eigen aangepaste eigenschappen definiëren.

   ![wf-40](assets/wf-40.png)

1. De eigenschappen op het knooppunt configureren `cq:listeners`.

   De `cq:listener` Met de knooppunten en de bijbehorende eigenschappen kunt u gebeurtenishandlers instellen die reageren op gebeurtenissen in de UI-modeleditor voor aanraakbediening, zoals het slepen van een stap naar een modelpagina of het bewerken van stapeigenschappen.

   **Belangeneigenschappen:**

   * `afterMove: REFRESH_PAGE`
   * `afterdelete: CQ.workflow.flow.Step.afterDelete`
   * `afteredit: CQ.workflow.flow.Step.afterEdit`
   * `afterinsert: CQ.workflow.flow.Step.afterInsert`

   Deze configuratie is essentieel voor het goed functioneren van de redacteur. In de meeste gevallen mag deze configuratie niet worden gewijzigd.

   Instellen `cq:inherit` naar waar (op `cq:editConfig` knoop, zie hierboven) laat u deze configuratie erven, zonder het moeten het in uw stapdefinitie uitdrukkelijk omvatten. Als er geen overerving is, moet u dit knooppunt met de volgende eigenschappen en waarden toevoegen.

   In dit voorbeeld is de overerving geactiveerd, zodat we de `cq:listeners` en de stap functioneren nog steeds correct.

   ![wf-41](assets/wf-41.png)

1. U kunt nu een instantie van uw stap toevoegen aan een workflowmodel. Wanneer u **Configureren** de stap die u ziet:

   ![wf-42](assets/wf-42.png) ![wf-43](assets/wf-43.png)

#### Sampleopmaak die in dit voorbeeld wordt gebruikt {#sample-markup-used-in-this-example}

Opmaak voor een aangepaste stap wordt weergegeven in het dialoogvenster `.content.xml` van het basisknooppunt van de component. Het voorbeeld `.content.xml` wordt gebruikt voor dit voorbeeld:

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

De `_cq_editConfig.xml` in dit voorbeeld gebruikt voorbeeld:

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

De `_cq_dialog/.content.xml` in dit voorbeeld gebruikt voorbeeld:

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
>Hoewel AEM [moderniseringsinstrumenten](/help/sites-developing/modernization-tools.md) als u de dialoogvensters met klassieke UI-stappen wilt bijwerken naar de standaarddialoogvensters voor gebruikersinterface. Na de conversie zijn er nog enkele handmatige verbeteringen die in bepaalde gevallen in de dialoog kunnen worden aangebracht.
>
>* Als een bijgewerkt dialoogvenster leeg is, kunt u dialoogvensters bekijken in `/libs` die vergelijkbare functionaliteit hebben als voorbeelden van hoe u een oplossing kunt bieden. Bijvoorbeeld:
>
>* `/libs/cq/workflow/components/model`
>* `/libs/cq/workflow/components/workflow`
>* `/libs/dam/components`
>* `/libs/wcm/workflow/components/autoassign`
>* `/libs/cq/projects`
>
>  Bewerk niets in `/libs`en gebruik ze gewoon als voorbeelden. Als u een van de bestaande stappen wilt gebruiken, kopieert u deze naar `/apps` en bewerk ze daar.
