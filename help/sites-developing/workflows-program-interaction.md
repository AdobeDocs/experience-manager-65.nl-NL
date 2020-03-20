---
title: Programmatische interactie met Workflows
seo-title: Programmatische interactie met Workflows
description: 'null'
seo-description: 'null'
uuid: a0f19fc6-b9bd-4b98-9c0e-fbf4f7383026
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: cb621332-a149-4f8d-9425-fd815b033c38
translation-type: tm+mt
source-git-commit: 7d2ba937710e5931356512b812a8b8fbe3a52072

---


# Programmatische interactie met Workflows{#interacting-with-workflows-programmatically}

Wanneer u uw workflows [aanpast en uitbreidt](/help/sites-developing/workflows-customizing-extending.md) , hebt u toegang tot workflowobjecten:

* [De Java API voor de workflow gebruiken](#using-the-workflow-java-api)
* [Workflowobjecten verkrijgen in ECMA-scripts](#obtaining-workflow-objects-in-ecma-scripts)
* [De REST-API voor workflows gebruiken](#using-the-workflow-rest-api)

## De Java API voor de workflow gebruiken {#using-the-workflow-java-api}

De workflow Java API bestaat uit het [`com.adobe.granite.workflow`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/package-summary.html) pakket en verschillende subpakketten. Het belangrijkste lid van de API is de `com.adobe.granite.workflow.WorkflowSession` klasse. De `WorkflowSession` klasse biedt toegang tot workflowobjecten tijdens het ontwerpen en uitvoeren:

* workflowmodellen
* werkartikelen
* workflowinstanties
* workflowgegevens
* postvakken

De klasse biedt ook verschillende methoden voor het ingrijpen in workflowlevenscycli.

De volgende tabel bevat koppelingen naar de referentiedocumentatie van verschillende belangrijke Java-objecten die moeten worden gebruikt wanneer programmatisch wordt gewerkt met workflows. De volgende voorbeelden demonstreren hoe u de klassenobjecten in code verkrijgt en gebruikt.

| Functies | Objecten |
|---|---|
| Een workflow openen | [`WorkflowSession`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html) |
| Een workflowinstantie uitvoeren en opvragen | [`Workflow`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/Workflow.html)</br>[`WorkItem`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkItem.html)</br>[`WorkflowData`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkflowData.html) |
| Een workflowmodel beheren | [`WorkflowModel`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowModel.html)</br>[`WorkflowNode`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowNode.html)</br>[`WorkflowTransition`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowTransition.html) |
| Informatie voor een knooppunt in de workflow (of niet) | [`WorkflowStatus`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) |

## Workflowobjecten verkrijgen in ECMA-scripts {#obtaining-workflow-objects-in-ecma-scripts}

Zoals beschreven in [Locating the Script](/help/sites-developing/the-basics.md#locating-the-script), biedt AEM (via Apache Sling) een ECMA-scriptengine die ECMA-scripts op de server uitvoert. De [`org.apache.sling.scripting.core.ScriptHelper`](https://sling.apache.org/apidocs/sling5/org/apache/sling/scripting/core/ScriptHelper.html) klasse is onmiddellijk beschikbaar aan uw manuscripten als `sling` variabele.

De `ScriptHelper` klasse biedt toegang tot het object `SlingHttpServletRequest` dat u kunt gebruiken om het `WorkflowSession` object uiteindelijk te verkrijgen. bijvoorbeeld:

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

## De REST-API voor workflows gebruiken {#using-the-workflow-rest-api}

De workflowconsole maakt intensief gebruik van de REST API; Deze pagina beschrijft dus de REST API voor workflows.

>[!NOTE]
>
>Met het opdrachtregelprogramma &#39;curl&#39; kunt u de REST-API voor workflowobjecten gebruiken om toegang te krijgen tot workflowobjecten en de levenscycli van instanties te beheren. De voorbeelden op deze pagina demonstreren het gebruik van de REST API via het curl opdrachtregelprogramma.

De volgende acties worden ondersteund met de REST API:

* een workflowservice starten of stoppen
* workflowmodellen maken, bijwerken of verwijderen
* [workflowinstanties starten, opschorten, hervatten of beëindigen](/help/sites-administering/workflows.md#workflow-status-and-actions)
* volledige of gedelegeerde werkitems

>[!NOTE]
>
>Met Firebug, een Firefox-extensie voor webontwikkeling, kunt u het HTTP-verkeer volgen wanneer de console wordt uitgevoerd. U kunt bijvoorbeeld de parameters en de waarden controleren die met een `POST` aanvraag naar de AEM-server worden verzonden.

Op deze pagina wordt aangenomen dat AEM wordt uitgevoerd op localhost op de poort `4502` en dat de installatiecontext &quot; `/`&quot; (root) is. Als dit niet het geval is voor uw installatie, moeten de URI&#39;s, waarop de HTTP-aanvragen van toepassing zijn, dienovereenkomstig worden aangepast.

De voor `GET` aanvragen ondersteunde rendering is de JSON-rendering. De URL&#39;s voor `GET` moeten de `.json` extensie hebben, bijvoorbeeld:

`http://localhost:4502/etc/workflow.json`

### Workflowinstanties beheren {#managing-workflow-instances}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502/etc/workflow/instances`

<table>
 <tbody>
  <tr>
   <td>HTTP-aanvraagmethode</td>
   <td>Acties</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Hier worden de beschikbare workflowinstanties weergegeven.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td><p>Hiermee wordt een nieuwe werkstroominstantie gemaakt. De parameters zijn:<br /> - <code>model</code>: de ID (URI) van het respectieve werkschemamodel<br /> - <code>payloadType</code>: met het type van de lading (bijvoorbeeld <code>JCR_PATH</code> of URL).<br /> De payload wordt als parameter verzonden <code>payload</code>. Een <code>201</code> (<code>CREATED</code>) reactie wordt teruggestuurd met een plaatsheader die URL van het nieuwe middel van de werkschemainstantie bevat.</p> </td>
  </tr>
 </tbody>
</table>

#### Een Werkstroominstantie beheren door de betreffende staat {#managing-a-workflow-instance-by-its-state}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502/etc/workflow/instances.{state}`

| HTTP-aanvraagmethode | Acties |
|---|---|
| `GET` | Hier worden de beschikbare workflowinstanties en hun statussen weergegeven ( `RUNNING`, `SUSPENDED`, `ABORTED` of `COMPLETED`) |

#### Een Werkstroominstantie beheren met de id {#managing-a-workflow-instance-by-its-id}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502/etc/workflow/instances/{id}`

<table>
 <tbody>
  <tr>
   <td>HTTP-aanvraagmethode</td>
   <td>Acties</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Haalt de gegevens van de instanties (definitie en metagegevens) op, inclusief de koppeling naar het respectievelijke workflowmodel.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Wijzigt de status van de instantie. De nieuwe status wordt verzonden als de parameter <code>state</code> en moet een van de volgende waarden hebben: <code>RUNNING</code>, <code>SUSPENDED</code>, of <code>ABORTED</code>.<br /> Als de nieuwe status niet bereikbaar is (bijvoorbeeld wanneer een afgesloten instantie wordt opgeschort), wordt een <code>409</code> (<code>CONFLICT</code>) reactie teruggestuurd naar de client.</td>
  </tr>
 </tbody>
</table>

### Workflowmodellen beheren {#managing-workflow-models}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502/etc/workflow/models`

<table>
 <tbody>
  <tr>
   <td>HTTP-aanvraagmethode</td>
   <td>Acties</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Hier worden de beschikbare workflowmodellen weergegeven.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Hiermee maakt u een nieuw workflowmodel. Als de parameter <code>title</code> wordt verzonden, wordt een nieuw model gecreeerd met de gespecificeerde titel. Als u een JSON-modeldefinitie als parameter koppelt, <code>model</code> wordt een nieuw workflowmodel gemaakt volgens de opgegeven definitie.<br /> Een <code>201</code> reactie (<code>CREATED</code>) wordt teruggestuurd met een plaatsheader die URL van het nieuwe werkschemamodel bevat.<br /> Dit gebeurt ook wanneer een modeldefinitie wordt gekoppeld als een bestandsparameter die <code>modelfile</code>wordt genoemd.<br /> In zowel de gevallen van de <code>model</code> als de <code>modelfile</code> <code>type</code> parameters, wordt een extra geroepen parameter vereist om het rangschikkingsformaat te bepalen. De nieuwe rangschikkingsformaten kunnen worden geïntegreerd gebruikend OSGI API. Er wordt een standaard JSON-serializer geleverd met de workflow-engine. Het type is JSON. Zie hieronder voor een voorbeeld van de opmaak.</td>
  </tr>
 </tbody>
</table>

Voorbeeld: in browser, `http://localhost:4502/etc/workflow/models.json` produceert een verzoek om een JSON reactie gelijkend op het volgende:

```
[
    {"uri":"/var/workflow/models/activationmodel"}
    ,{"uri":"/var/workflow/models/dam/adddamsize"}
    ,{"uri":"/var/workflow/models/cloudconfigs/dtm-reactor/library-download"}
    ,{"uri":"/var/workflow/models/ac-newsletter-workflow-simple"}
    ,{"uri":"/var/workflow/models/dam/dam-create-language-copy"}
    ,{"uri":"/var/workflow/models/dam/dam-create-and-translate-language-copy"}
    ,{"uri":"/var/workflow/models/dam-indesign-proxy"}
    ,{"uri":"/var/workflow/models/dam-xmp-writeback"}
    ,{"uri":"/var/workflow/models/dam-parse-word-documents"}
    ,{"uri":"/var/workflow/models/dam/process_subasset"}
    ,{"uri":"/var/workflow/models/dam/dam_set_last_modified"}
    ,{"uri":"/var/workflow/models/dam/dam-autotag-assets"}
    ,{"uri":"/var/workflow/models/dam/update_asset"}
    ,{"uri":"/var/workflow/models/dam/update_asset_offloading"}
    ,{"uri":"/var/workflow/models/dam/dam-update-language-copy"}
    ,{"uri":"/var/workflow/models/dam/update_from_lightbox"}
    ,{"uri":"/var/workflow/models/cloudservices/DTM_bundle_download"}
    ,{"uri":"/var/workflow/models/dam/dam_download_asset"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-encode-video"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-thumbnail-replacement"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail"}
    ,{"uri":"/var/workflow/models/newsletter_bounce_check"}
    ,{"uri":"/var/workflow/models/projects/photo_shoot_submission"}
    ,{"uri":"/var/workflow/models/projects/product_photo_shoot"}
    ,{"uri":"/var/workflow/models/projects/approval_workflow"}
    ,{"uri":"/var/workflow/models/prototype-01"}
    ,{"uri":"/var/workflow/models/publish_example"}
    ,{"uri":"/var/workflow/models/publish_to_campaign"}
    ,{"uri":"/var/workflow/models/screens/publish_to_author_bin"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_publish_to_youtube"}
    ,{"uri":"/var/workflow/models/projects/request_copy"}
    ,{"uri":"/var/workflow/models/projects/request_email"}
    ,{"uri":"/var/workflow/models/projects/request_landing_page"}
    ,{"uri":"/var/workflow/models/projects/request_launch"}
    ,{"uri":"/var/workflow/models/request_for_activation"}
    ,{"uri":"/var/workflow/models/request_for_deactivation"}
    ,{"uri":"/var/workflow/models/request_for_deletion"}
    ,{"uri":"/var/workflow/models/request_for_deletion_without_deactivation"}
    ,{"uri":"/var/workflow/models/request_to_complete_move_operation"}
    ,{"uri":"/var/workflow/models/reverse_replication"}
    ,{"uri":"/var/workflow/models/salesforce-com-export"}
    ,{"uri":"/var/workflow/models/scene7"}
    ,{"uri":"/var/workflow/models/scheduled_activation"}
    ,{"uri":"/var/workflow/models/scheduled_deactivation"}
    ,{"uri":"/var/workflow/models/screens/screens-update-asset"}
    ,{"uri":"/var/workflow/models/translation"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_remove_from_youtube"}
    ,{"uri":"/var/workflow/models/wcm-translation/create_language_copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/prepare_translation_project"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-i18n-dictionary"}
    ,{"uri":"/var/workflow/models/wcm-translation/sync_translation_job"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-language-copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/update_language_copy"}
]
```

#### Een specifiek workflowmodel beheren {#managing-a-specific-workflow-model}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502*{uri}*`

Waar `*{uri}*` is het pad naar het modelknooppunt in de repository.

<table>
 <tbody>
  <tr>
   <td>HTTP-aanvraagmethode</td>
   <td>Acties</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Haalt de <code>HEAD</code> versie van het model op (definitie en metagegevens).</td>
  </tr>
  <tr>
   <td><code>PUT</code></td>
   <td>Werkt de <code>HEAD</code> versie van het model bij (maakt een nieuwe versie).<br /> De volledige modeldefinitie voor de nieuwe versie van het model moet als geroepen parameter worden toegevoegd <code>model</code>. Bovendien is een <code>type</code> parameter nodig zoals wanneer het creëren van nieuwe modellen en moet de waarde hebben <code>JSON</code>.<br /> </td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Hetzelfde gedrag als bij PUT. Nodig omdat AEM-widgets geen <code>PUT</code> bewerkingen ondersteunen.</td>
  </tr>
  <tr>
   <td><code>DELETE</code></td>
   <td>Hiermee verwijdert u het model. Om firewall/volmachtskwesties op te lossen <code>POST</code> zal een die een <code>X-HTTP-Method-Override</code> kopbalingang met waarde bevat <code>DELETE</code> ook als <code>DELETE</code> verzoek worden goedgekeurd.</td>
  </tr>
 </tbody>
</table>

Voorbeeld: in browser, een verzoek om een `http://localhost:4502/var/workflow/models/publish_example.json` reactie terug te `json` keren die aan de volgende code gelijkaardig is:

```shell
{
  "id":"/var/workflow/models/publish_example",
  "title":"Publish Example",
  "version":"1.0",
  "description":"This example shows a simple review and publish process.",
  "metaData":
  {
    "multiResourceSupport":"true",
    "tags":"wcm,publish"
  },
  "nodes":
  [{
    "id":"node0",
    "type":"START",
    "title":"Start",
    "description":"The start node of the workflow.",
    "metaData":
    {
    }
  },
  {
    "id":"node1",
    "type":"PARTICIPANT",
    "title":"Validate Content",
    "description":"Validate the modified content.",
    "metaData":
    {
      "PARTICIPANT":"admin"
    }
  },
  {
    "id":"node2",
    "type":"PROCESS",
    "title":"Publish Content",
    "description":"Publish the modified content.",
    "metaData":
    {
      "PROCESS_AUTO_ADVANCE":"true",
      "PROCESS":"com.day.cq.wcm.workflow.process.ActivatePageProcess"
    }
  },
  {
    "id":"node3",
    "type":"END",
    "title":"End",
    "description":"The end node of the workflow.",
    "metaData":
    {
    }
  }],
  "transitions":
  [{
    "from":"node0",
    "to":"node1",
    "metaData":
    {
    }
  },
  {
    "from":"node1",
    "to":"node2",
    "metaData":
    {
    }
  },
  {
    "from":"node2",
    "to":"node3",
    "metaData":
    {
    }
  }
]}
```

#### Het beheren van een Model van het Werkschema door zijn Versie {#managing-a-workflow-model-by-its-version}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502/etc/workflow/models/{id}.{version}`

| HTTP-aanvraagmethode | Acties |
|---|---|
| `GET` | Haalt de gegevens van het model op in de opgegeven versie (indien aanwezig). |

### Invakken (gebruikers) beheren {#managing-user-inboxes}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502/bin/workflow/inbox`

<table>
 <tbody>
  <tr>
   <td>HTTP-aanvraagmethode</td>
   <td>Acties</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Maakt een lijst van de het werkpunten die in inbox van de gebruiker zijn, die door de de authentificatiekopballen van HTTP wordt geïdentificeerd.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Voltooit het het werkpunt de waarvan URI als parameter wordt verzonden <code>item</code> en gaat de volgens werkschemainstantie aan de volgende knoop(s) vooruit, die door de parameter wordt bepaald <code>route</code> of <code>backroute</code> in het geval van een stap terug.<br /> Als de parameter <code>delegatee</code> <code>item</code> wordt verzonden, wordt het het werkpunt dat door de parameter wordt geïdentificeerd afgevaardigd aan de gespecificeerde deelnemer.</td>
  </tr>
 </tbody>
</table>

#### Het beheren van een (Gebruiker) Inbox door identiteitskaart WorkItem {#managing-a-user-inbox-by-the-workitem-id}

De volgende HTTP-aanvraagmethoden zijn van toepassing op:

`http://localhost:4502/bin/workflow/inbox/{id}`

| HTTP-aanvraagmethode | Acties |
|---|---|
| `GET` | Haalt de gegevens (definitie en metagegevens) op van het Postvak IN `WorkItem` dat met de ID ervan wordt geïdentificeerd. |

## Voorbeelden {#examples}

### Hoe te om een Lijst van alle Lopende Werkschema&#39;s met hun IDs te krijgen {#how-to-get-a-list-of-all-running-workflows-with-their-ids}

Ga als volgt te werk om een lijst met alle actieve workflows op te halen:

`http://localhost:4502/etc/workflow/instances.RUNNING.json`

#### Hoe te om een Lijst van alle Lopende Werkschema&#39;s met hun identiteitskaart te krijgen - REST gebruikend krullen {#how-to-get-a-list-of-all-running-workflows-with-their-ids-rest-using-curl}

Voorbeeld met krullen:

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/instances.RUNNING.json
```

De resultaten `uri` kunnen als instantie `id` in andere opdrachten worden weergegeven. bijvoorbeeld:

```shell
[
    {"uri":"/etc/workflow/instances/server0/2017-03-08/request_for_activation_1"}
]
```

>[!NOTE]
>
>Deze `curl` opdracht kan met elke [workflowstatus](/help/sites-administering/workflows.md#workflow-status-and-actions) worden gebruikt in plaats van `RUNNING`.

### Hoe te om de Titel van het Werkschema te veranderen {#how-to-change-the-workflow-title}

Om de Titel **van het** Werkschema te veranderen die op het lusje van **Instanties** van de werkschemaconsole wordt getoond, verzend een `POST` bevel:

* to: `http://localhost:4502/etc/workflow/instances/{id}`

* met de volgende parameters:

   * `action`: de waarde ervan moet : `UPDATE`
   * `workflowTitle`: de titel van de workflow

#### Hoe te om de Titel van het Werkschema te veranderen - REST gebruikend krullen {#how-to-change-the-workflow-title-rest-using-curl}

Voorbeeld met krullen:

```shell
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/{id}

# for example
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
```

### Hoe te om van alle Modellen van het Werkschema een lijst te maken {#how-to-list-all-workflow-models}

Ga als volgt te werk om een lijst met alle beschikbare workflowmodellen op te halen:

`http://localhost:4502/etc/workflow/models.json`

#### Hoe te om van alle Modellen van het Werkschema een lijst te maken - REST gebruikend curl {#how-to-list-all-workflow-models-rest-using-curl}

Voorbeeld met krullen:

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/models.json
```

>[!NOTE]
>
>Zie ook Workflowmodellen [beheren](#managing-workflow-models).

### Een WorkflowSession-object verkrijgen {#obtaining-a-workflowsession-object}

De `com.adobe.granite.workflow.WorkflowSession` klasse kan worden aangepast vanuit een `javax.jcr.Session` object of een `org.apache.sling.api.resource.ResourceResolver` object.

#### Een WorkflowSession-object verkrijgen - Java {#obtaining-a-workflowsession-object-java}

Gebruik in een JSP-script (of Java-code voor een servlet-klasse) het HTTP-aanvraagobject om een `SlingHttpServletRequest` object te verkrijgen dat toegang biedt tot een `ResourceResolver` object. Pas het `ResourceResolver` object aan `WorkflowSession`.

```java
<%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false"
    import="com.adobe.granite.workflow.WorkflowSession,
  org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
%>
```

#### Een WorkflowSession-object verkrijgen - ECMA-script {#obtaining-a-workflowsession-object-ecma-script}

Gebruik de `sling` variabele om het `SlingHttpServletRequest` object te verkrijgen dat u gebruikt om een `ResourceResolver` object te verkrijgen. Pas het `ResourceResolver` object aan het `WorkflowSession` object aan.

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

### Workflowmodellen maken, lezen of verwijderen {#creating-reading-or-deleting-workflow-models}

In de volgende voorbeelden ziet u hoe u workflowmodellen kunt openen:

* De code voor Java en het manuscript ECMA gebruikt de `WorkflowSession.createNewModel` methode.
* De curl-opdracht geeft rechtstreeks toegang tot het model via de URL.

De gebruikte voorbeelden:

1. Maak een model (met de id `/var/workflow/models/mymodel/jcr:content/model`).
1. Verwijder het model.

>[!NOTE]
>
>Als u het model verwijdert, wordt de `deleted` eigenschap van het `metaData` onderliggende knooppunt van het model ingesteld op `true`.
>
>Verwijderen verwijdert het modelknooppunt niet.

Bij het maken van een nieuw model:

* De redacteur van het werkschemamodel vereist dat de modellen een specifieke hieronder knoopstructuur gebruiken `/var/workflow/models`. Het bovenliggende knooppunt van het model moet van het type zijn `cq:Page` met een `jcr:content` knooppunt met de volgende eigenschapswaarden:

   * `sling:resourceType`: `cq/workflow/components/pages/model`
   * `cq:template`: `/libs/cq/workflow/templates/model`
   Wanneer u een model creeert, moet u deze `cq:Page` knoop eerst tot stand brengen en zijn `jcr:content` knoop gebruiken als ouder van de modelknoop.

* Het `id` argument dat sommige methodes voor het identificeren van het model vereisen is de absolute weg van de modelknoop in de bewaarplaats:

   `/var/workflow/models/<*model_name>*/jcr:content/model`

   >[!NOTE]
   >
   >Zie [Hoe te om van alle modellen](#how-to-list-all-workflow-models)van het Werkschema een lijst te maken.

#### Workflowmodellen maken, lezen of verwijderen - Java {#creating-reading-or-deleting-workflow-models-java}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" import="com.adobe.granite.workflow.WorkflowSession,
                 com.adobe.granite.workflow.model.WorkflowModel,
             org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
/* Create the parent page */
String modelRepo = new String("/var/workflow/models");
String modelTemplate = new String ("/libs/cq/workflow/templates/model");
String modelName = new String("mymodel");
Page modelParent = pageManager.create(modelRepo, modelName, modelTemplate, "My workflow model");

/* create the model */
String modelId = new String(modelParent.getPath()+"/jcr:content/model")
WorkflowModel model = wfSession.createNewModel("Made using Java",modelId);

/* delete the model */
wfSession.deleteModel(modelId);
%>
```

#### Workflowmodellen maken, lezen of verwijderen - ECMA-script {#creating-reading-or-deleting-workflow-models-ecma-script}

```
var resolver = sling.getRequest().getResource().getResourceResolver();
var wfSession = resolver.adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
var pageManager = resolver.adaptTo(Packages.com.day.cq.wcm.api.PageManager);

//create the parent page node
var workflowPage = pageManager.create("/var/workflow/models", "mymodel", "/libs/cq/workflow/templates/model", "Created via ECMA Script");
var modelId = workflowPage.getPath()+ "/jcr:content/model";
//create the model
var model = wfSession.createNewModel("My Model", modelId);
//delete the model
var model = wfSession.deleteModel(modelId);
```

#### Een workflowmodel verwijderen - HERSTELLEN met curl {#deleting-a-workflow-model-rest-using-curl}

```shell
# deleting the model by its id
curl -u admin:admin -X DELETE http://localhost:4502/etc/workflow/models/{id}
```

>[!NOTE]
>
>Wegens het vereiste detailniveau, wordt de krulling niet praktisch geacht voor het creëren van en/of het lezen van een model.

### Systeemworkflows filteren bij het controleren van workflowstatus {#filtering-out-system-workflows-when-checking-workflow-status}

U kunt de [WorkflowStatus API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) gebruiken om informatie over de werkschemastatus van een knoop terug te winnen.

Verschillende methoden hebben de parameter:

`excludeSystemWorkflows`

Deze parameter kan zo worden ingesteld dat `true` wordt aangegeven dat systeemworkflows van de relevante resultaten moeten worden uitgesloten.

U [kunt de OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) van **Adobe Granite Workflow PayloadMapCache** bijwerken die de workflow opgeeft die `Models` moet worden beschouwd als systeemworkflows. De standaardworkflowmodellen (runtime) zijn:

* `/var/workflow/models/scheduled_activation/jcr:content/model`
* `/var/workflow/models/scheduled_deactivation/jcr:content/model`

### Stap van de Deelnemer van de auto-Geavanceerde na een Onderbreking {#auto-advance-participant-step-after-a-timeout}

Als u automatisch een stap **Deelnemer** wilt uitvoeren die niet binnen een vooraf bepaalde tijd is voltooid, kunt u:

1. Implementeer een OSGI-gebeurtenislistener om te luisteren naar het maken en wijzigen van taken.
1. Geef een time-out (deadline) op en maak vervolgens een geplande slingertaak die op dat moment moet worden uitgevoerd.
1. Schrijf een taakmanager die op de hoogte wordt gebracht wanneer de onderbreking verloopt en de baan teweegbrengt.

   Deze manager zal de vereiste actie op de taak nemen als de taak nog niet wordt voltooid

>[!NOTE]
>
>De te nemen maatregelen moeten duidelijk omschreven zijn om van deze aanpak gebruik te kunnen maken.

### Interactie met workflowinstanties {#interacting-with-workflow-instances}

Hieronder vindt u basisvoorbeelden van de wijze waarop u programmatisch kunt communiceren met workflowinstanties.

#### Interactie met workflowinstanties - Java {#interacting-with-workflow-instances-java}

```java
// starting a workflow
WorkflowModel model = wfSession.getModel(workflowId);
WorkflowData wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
Workflow[] workflows workflows = wfSession.getAllWorkflows();
Workflow workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### Interactie met workflowinstanties - ECMA-script {#interacting-with-workflow-instances-ecma-script}

```
// starting a workflow
var model = wfSession.getModel(workflowId);
var wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
var workflows = wfSession.getWorkflows(“RUNNING“);
var workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### Interactie met Workflowinstanties - REST gebruiken met curl {#interacting-with-workflow-instances-rest-using-curl}

* **Een workflow starten**

   ```shell
   # starting a workflow
   curl -d "model={id}&payloadType={type}&payload={payload}" http://localhost:4502/etc/workflow/instances
   
   # for example:
   curl -u admin:admin -d "model=/var/workflow/models/request_for_activation/jcr:content/model&payloadType=JCR_PATH&payload=/content/we-retail/us/en/products" http://localhost:4502/etc/workflow/instances
   ```

* **De instanties weergeven**

   ```shell
   # listing the instances
   curl -u admin:admin http://localhost:4502/etc/workflow/instances.json
   ```

   Hierin worden alle gevallen vermeld; bijvoorbeeld:

   ```shell
   [
       {"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_1"}
       ,{"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_2"}
   ]
   ```

   >[!NOTE]
   >
   >Zie [Hoe te om een Lijst van alle Lopende Workflows](#how-to-get-a-list-of-all-running-workflows-with-their-ids) met hun IDs voor het aanbieden van instanties met een specifieke status te krijgen.

* **Een workflow opschorten**

   ```shell
   # suspending a workflow
   curl -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **Een workflow hervatten**

   ```shell
   # resuming a workflow
   curl -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **Een werkstroominstantie beëindigen**

   ```shell
   # terminating a workflow
   curl -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

### Interactie met werkitems {#interacting-with-work-items}

Het volgende verstrekt basisvoorbeelden van hoe te (programmatisch) met het werkpunten in wisselwerking te staan.

#### Interactie met werkitems - Java {#interacting-with-work-items-java}

```java
// querying work items
WorkItem[] workItems = wfSession.getActiveWorkItems();
WorkItem workItem = wfSession.getWorkItem(id);

// getting routes
List<Route> routes = wfSession.getRoutes(workItem);

// delegating
Iterator<Participant> delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### Interactie met werkitems - ECMA-script {#interacting-with-work-items-ecma-script}

```
// querying work items
var workItems = wfSession.getActiveWorkItems();
var workItem = wfSession.getWorkItem(id);

// getting routes
var routes = wfSession.getRoutes(workItem);

// delegating
var delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### Interactie met werkitems - HERSTEL met krullen {#interacting-with-work-items-rest-using-curl}

* **Werkitems van de aanbieding in het Postvak IN**

   ```shell
   # listing the work items
   curl -u admin:admin http://localhost:4502/bin/workflow/inbox
   ```

   Details voor werkitems die zich momenteel in de Postvak IN bevinden, worden weergegeven. bijvoorbeeld:

   ```shell
   [{
       "uri_xss": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "uri": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "currentAssignee_xss": "workflow-administrators",
       "currentAssignee": "workflow-administrators",
       "startTime": 1519656289274,
       "payloadType_xss": "JCR_PATH",
       "payloadType": "JCR_PATH",
       "payload_xss": "/content/we-retail/es/es",
       "payload": "/content/we-retail/es/es",
       "comment_xss": "Process resource is null",
       "comment": "Process resource is null",
       "type_xss": "WorkItem",
       "type": "WorkItem"
     },{
       "uri_xss": "configuration/configure_analyticstargeting",
       "uri": "configuration/configure_analyticstargeting",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/securitychecklist",
       "uri": "configuration/securitychecklist",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/enable_collectionofanonymoususagedata",
       "uri": "configuration/enable_collectionofanonymoususagedata",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/configuressl",
       "uri": "configuration/configuressl",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     }
   ```

* **Werkitems delegeren**

   ```xml
   # delegating
   curl -d "item={item}&delegatee={delegatee}" http://localhost:4502/bin/workflow/inbox
   
   # for example:
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_act_1&delegatee=administrators" http://localhost:4502/bin/workflow/inbox
   ```

   >[!NOTE]
   >
   >De optie `delegatee` moet een geldige optie zijn voor de workflowstap.

* **Werkonderdelen voltooien of naar de volgende stap gaan**

   ```xml
   # retrieve the list of routes; the results will be similar to {"results":1,"routes":[{"rid":"233123169","label":"End","label_xss":"End"}]}
   http://localhost:4502/etc/workflow/instances/<path-to-the-workitem>.routes.json
   
   # completing or advancing to the next step; use the appropriate route ID (rid value) from the above list
   curl -d "item={item}&route={route}" http://localhost:4502/bin/workflow/inbox
   
   # for example:
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_activation_1&route=233123169" http://localhost:4502/bin/workflow/inbox
   ```

### Luisteren naar workflowgebeurtenissen {#listening-for-workflow-events}

Gebruik het OSGi-gebeurtenisframework om te luisteren naar gebeurtenissen die door de [ `com.adobe.granite.workflow.event.WorkflowEvent`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/event/WorkflowEvent.html) klasse worden gedefinieerd. Deze klasse biedt ook verschillende nuttige methoden om informatie over het onderwerp van de gebeurtenis te verkrijgen. De `getWorkItem` methode retourneert bijvoorbeeld het `WorkItem` object voor het werkitem dat bij de gebeurtenis is betrokken.

De volgende voorbeeldcode definieert een service die luistert naar workflowgebeurtenissen en taken uitvoert op basis van het type gebeurtenis.

```java
package com.adobe.example.workflow.listeners;

import org.apache.sling.event.jobs.JobProcessor;
import org.apache.sling.event.jobs.JobUtil;

import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;

import com.adobe.granite.workflow.event.WorkflowEvent;
import com.adobe.granite.workflow.exec.WorkItem;

/**
 * The <code>WorkflowEventCatcher</code> class listens to workflow events.
 */
@Component(metatype=false, immediate=true)
@Service(value=org.osgi.service.event.EventHandler.class)
public class WorkflowEventCatcher implements EventHandler, JobProcessor {

 @Property(value=com.adobe.granite.workflow.event.WorkflowEvent.EVENT_TOPIC)
 static final String EVENT_TOPICS = "event.topics";

 private static final Logger logger = LoggerFactory.getLogger(WorkflowEventCatcher.class);

 public void handleEvent(Event event) {
  JobUtil.processJob(event, this);
 }

 public boolean process(Event event) {
  logger.info("Received event of topic: " + event.getTopic());
  String topic = event.getTopic();

  try {
   if (topic.equals(WorkflowEvent.EVENT_TOPIC)) {
    WorkflowEvent wfevent = (WorkflowEvent)event;
    String eventType = wfevent.getEventType();
    String instanceId = wfevent.getWorkflowInstanceId();

    if (instanceId != null) {
     //workflow instance events
     if (eventType.equals(WorkflowEvent.WORKFLOW_STARTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_RESUMED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_SUSPENDED_EVENT)) {
      // your code comes here...
     } else if (
       eventType.equals(WorkflowEvent.WORKFLOW_ABORTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_COMPLETED_EVENT)) {
      // your code comes here...
     }
     // workflow node event
     if (eventType.equals(WorkflowEvent.NODE_TRANSITION_EVENT)) {
      WorkItem currentItem = (WorkItem) event.getProperty(WorkflowEvent.WORK_ITEM);
      // your code comes here...
     }
    }
   }
  } catch(Exception e){
   logger.debug(e.getMessage());
   e.printStackTrace();
  }
  return true;
 }
}
```

