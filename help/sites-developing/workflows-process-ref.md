---
title: Referentie workflowproces
seo-title: Referentie workflowproces
description: 'null'
seo-description: 'null'
uuid: de367aa8-4580-4810-b665-2a7b521e36ca
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: dbdf981f-791b-4ff7-8ca8-039d0bdc9c92
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Referentie workflowproces{#workflow-process-reference}

AEM biedt verschillende processtappen die kunnen worden gebruikt voor het maken van workflowmodellen. De het processtappen van de douane kunnen ook voor taken worden toegevoegd die niet door de ingebouwde stappen worden behandeld (zie het [Creëren van de Modellen](/help/sites-developing/workflows-models.md)van het Werkschema).

## Proceskenmerken {#process-characteristics}

Voor elke processtap worden de volgende kenmerken beschreven.

### Java Class of ECMA Path {#java-class-or-ecma-path}

Processtappen worden gedefinieerd door een Java-klasse of een ECMAScript.

* Voor de Java-klassenprocessen wordt de volledig gekwalificeerde klassenaam opgegeven.
* Voor de ECMAScript-processen wordt het pad naar het script opgegeven.

### Payload {#payload}

De nuttige lading is de entiteit waarop een werkschemainstantie handelt. De payload wordt impliciet geselecteerd door de context waarbinnen een werkschemainstantie is begonnen.

Als bijvoorbeeld een workflow wordt toegepast op een AEM-pagina *P* , wordt *P* van stap tot stap doorgegeven terwijl de workflow verder gaat, waarbij elke stap optioneel op *P* reageert.

In het meest voorkomende geval is de lading een JCR-knooppunt in de repository (bijvoorbeeld een AEM Page of Asset). Een JCR-knooppuntlading wordt doorgegeven als een tekenreeks die een JCR-pad of een JCR-id (UUID) is. In sommige gevallen kan de payload een JCR-eigenschap (doorgegeven als een JCR-pad), een URL, een binair object of een algemeen Java-object zijn. De individuele processtappen die op de lading handelen zullen gewoonlijk een lading van een bepaald type verwachten, of verschillend afhankelijk van het ladingstype handelen. Voor elk hieronder beschreven proces wordt het verwachte ladingstype, indien van toepassing, beschreven.

### Argumenten {#arguments}

Sommige workflowprocessen accepteren argumenten die de beheerder opgeeft bij het instellen van de workflowstap.

Argumenten worden als één tekenreeks ingevoerd in de eigenschap **Procesargumenten** in het deelvenster **Eigenschappen** van de werkstroomeditor. Voor elk hieronder beschreven proces, wordt het formaat van het argumentkoord beschreven in een eenvoudige grammatica EBNF. De volgende code geeft bijvoorbeeld aan dat de argumenttekenreeks bestaat uit een of meer door komma&#39;s gescheiden paren, waarbij elk paar bestaat uit een naam (een tekenreeks) en een waarde, gescheiden door een dubbele dubbele dubbele punt:

```
    args := name '::' value [',' name '::' value]*
    name := /* A string */
    value := /* A string */
```


### Timeout {#timeout}

Na deze time-outperiode is de workflowstap niet meer operationeel. Sommige workflowprocessen respecteren de time-out, andere niet en worden genegeerd.

### Permissions {#permissions}

De sessie die aan de gebruiker `WorkflowProcess` wordt doorgegeven, wordt ondersteund door de servicegebruiker voor de workflowprocesservice, die de volgende machtigingen heeft in de hoofdmap van de opslagplaats:

* `jcr:read`
* `rep:write`
* `jcr:versionManagement`
* `jcr:lockManagement`
* `crx:replicate`

Als die reeks toestemmingen voor uw `WorkflowProcess` implementatie niet voldoende is, dan moet het een zitting met de vereiste toestemmingen gebruiken.

De geadviseerde manier om dit te doen is een de dienstgebruiker te gebruiken die met de noodzakelijke, maar minimale, vereiste ondergroep van toestemmingen wordt gecreeerd.

>[!CAUTION]
>
>Als u een upgrade uitvoert vanaf een versie die ouder is dan AEM 6.2, moet u mogelijk uw implementatie bijwerken.
>
>In vorige versies, werd de admin zitting overgegaan tot de `WorkflowProcess` implementaties en kon dan volledige toegang tot de bewaarplaats hebben zonder het moeten specifieke ACLs bepalen.
>
>De machtigingen zijn nu gedefinieerd als hierboven ([machtigingen](#permissions)). Net als de aanbevolen methode voor het bijwerken van uw implementatie.
>
>Een kortetermijnoplossing is ook beschikbaar voor achterwaartse compatibiliteitsdoeleinden wanneer codeveranderingen niet haalbaar zijn:
>
>* De webconsole gebruiken ( `/system/console/configMgr` zoek de **Adobe Granite Workflow Configuration Service**
   >
   >
* de modus Verouderd **workflowproces inschakelen**
>
>
Dit zal terugkeren naar het oude gedrag van het verstrekken van een admin zitting aan de `WorkflowProcess` implementatie en zal onbeperkte toegang tot de volledige bewaarplaats opnieuw verlenen.

## Workflowbeheerprocessen {#workflow-control-processes}

De volgende processen voeren geen handelingen uit op inhoud. Ze dienen om het gedrag van de workflow zelf te bepalen.

### AbsoluteTimeAutoAdvancer (Absolute Time Auto Advancer) {#absolutetimeautoadvancer-absolute-time-auto-advancer}

Het `AbsoluteTimeAutoAdvancer` (Absolute Tijd AutoGeavanceerde) proces gedraagt zich identiek aan **AutoAdvancer**, behalve dat het bij een bepaalde tijd en datum, in plaats van na een bepaalde tijdsduur uitdraait.

* **Java-klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AbsoluteTimeAutoAdvancer`
* **Payload**: Geen.
* **Argumenten**: Geen.
* **Time-out**: Procestijden vervallen wanneer de ingestelde tijd en datum zijn bereikt.

### AutoAdvancer (Auto Advancer) {#autoadvancer-auto-advancer}

Het `AutoAdvancer` proces gaat automatisch door naar de volgende stap. Als er meer dan één mogelijke volgende stap (bijvoorbeeld, als er OF gesplitst is) is dan zal dit proces de werkschema langs de *standaardroute* vooruitgaan, als één is gespecificeerd, anders zal het werkschema niet geavanceerd zijn.

* **Java-klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AutoAdvancer`

* **Payload**: Geen.
* **Argumenten**: Geen.
* **Time-out**: Procestijden worden na ingestelde tijdsduur weergegeven.

### ProcessAssembler (procesvergadering) {#processassembler-process-assembler}

Het `ProcessAssembler` proces voert veelvoudige subprocessen opeenvolgend in één enkele werkschemastap uit. Als u de `ProcessAssembler`subprocessen wilt gebruiken, maakt u één stap van dit type in uw workflow en stelt u de argumenten ervan in om de namen en argumenten van de subprocessen aan te geven die u wilt uitvoeren.

* **Java-klasse**: `com.day.cq.workflow.impl.process.ProcessAssembler`

* **Payload**: Een DAM-element, AEM-pagina of geen payload (afhankelijk van de vereisten van subprocessen).
* **Argumenten**:

```
        args := arg [',' arg]
        arg := processname ['::' processargs]
        processname := /* A fully qualified Java Class or absolute
        repository path to an ECMAScript */
        processargs := processarg [';' processarg]*
        processarg := '[' nobracketprocessarg ']' | nobracketprocessarg
        nobracketprocessarg := listitem [':' listitem]*
        listitem := /* A string */
```

* **Time-out**: Eerbiedigd.

Bijvoorbeeld:

* Haal de metagegevens uit het element.
* Maak drie miniaturen van de drie opgegeven formaten.
* Maak een JPEG-afbeelding van het element, ervan uitgaande dat het element oorspronkelijk geen GIF of PNG is (in dat geval wordt geen JPEG gemaakt).
* Stel de datum van laatste wijziging in op het element.

```shell
com.day.cq.dam.core.process.ExtractMetadataProcess,
    com.day.cq.dam.core.process.CreateThumbnailProcess::[140:100];[48:48];[319:319:false],
    com.day.cq.dam.core.process.CreateWebEnabledImageProcess::dimension:1280:1280;mimetype:image/jpeg,
    com.day.cq.dam.core.process.AssetSetLastModifiedProcess
```

## Basisprocessen {#basic-processes}

De volgende processen voeren eenvoudige taken uit of dienen als voorbeelden.

>[!CAUTION]
>
>U ***mag*** niets in het `/libs` pad wijzigen.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

### delete {#delete}

Het item in het opgegeven pad wordt verwijderd.

* **ECMAScript-pad**: `/libs/workflow/scripts/delete.ecma`

* **Payload**: JCR-pad
* **Argumenten**:Geen
* **Time-out**:Genegeerd

### nop {#noop}

Dit is het null-proces. Het voert geen verrichting uit, maar registreert een zuivert bericht.

* **ECMAScript-pad**: `/libs/workflow/scripts/noop.ecma`

* **Payload**:Geen
* **Argumenten**:Geen
* **Time-out**:Genegeerd

### rule-false {#rule-false}

Dit is een ongeldig proces dat `false` op de `check()` methode terugkeert.

* **ECMAScript-pad**: `/libs/workflow/scripts/rule-false.ecma`

* **Payload**:Geen
* **Argumenten**:Geen
* **Time-out**:Genegeerd

### sample {#sample}

Dit is een voorbeeld van een ECMAScript-proces.

* **ECMAScript-pad**: `/libs/workflow/scripts/sample.ecma`

* **Payload**:Geen
* **Argumenten**:Geen
* **Time-out**:Genegeerd

### urlcaller {#urlcaller}

Dit is een eenvoudig workflowproces dat de opgegeven URL aanroept. Doorgaans wordt de URL een verwijzing naar een JSP (of ander servletequivalent) dat een eenvoudige taak uitvoert. Dit proces mag alleen tijdens de ontwikkeling en demonstraties worden gebruikt en niet in een productieomgeving. De argumenten specificeren URL, login en wachtwoord.

* **ECMAScript-pad**: `/libs/workflow/scripts/urlcaller.ecma`

* **Payload**:Geen
* **Argumenten**:

```
        args := url [',' login ',' password]
        url := /* The URL to be called */
        login := /* The login to access the URL */
        password := /* The password to access the URL */
```

Bijvoorbeeld: `http://localhost:4502/my.jsp, mylogin, mypassword`

* **Time-out**:Genegeerd

### LockProcess {#lockprocess}

Vergrendelt de lading van de workflow.

* **** Java, klasse: `com.day.cq.workflow.impl.process.LockProcess`

* **** Payload: JCR_PATH en JCR_UID
* **** Argumenten:Geen
* **** Time-out:Genegeerd

De stap heeft geen effect in de volgende omstandigheden:

* De lading is al vergrendeld
* Het payload-knooppunt bevat geen onderliggende node jcr:content

### UnlockProcess {#unlockprocess}

Ontgrendelt de lading van de workflow.

* **** Java, klasse: `com.day.cq.workflow.impl.process.UnlockProcess`

* **** Payload: JCR_PATH en JCR_UID
* **** Argumenten:Geen
* **** Time-out:Genegeerd

De stap heeft geen effect in de volgende omstandigheden:

* De lading is al ontgrendeld
* Het payload-knooppunt bevat geen onderliggende node jcr:content

## Versionprocessen {#versioning-processes}

Het volgende proces voert een versie-verwante taak uit.

### CreateVersionProcess {#createversionprocess}

Hiermee maakt u een nieuwe versie van de payload van de workflow (AEM-pagina of DAM-element).

* **Java-klasse**: `com.day.cq.wcm.workflow.process.CreateVersionProcess`

* **Payload**: Een JCR-pad of UUID die verwijst naar een pagina of DAM-element
* **Argumenten**:Geen
* **Time-out**: Eerbiedigd

