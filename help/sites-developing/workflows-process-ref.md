---
title: Referentie workflowproces
description: Raadpleeg deze naslaggids voor workflows in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: a9de8ec6-6948-4643-89c3-62d9b1f6293a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Referentie workflowproces{#workflow-process-reference}

AEM biedt verschillende processtappen die kunnen worden gebruikt voor het maken van workflowmodellen. De processtappen van de douane kunnen ook voor taken worden toegevoegd die niet door de ingebouwde stappen worden behandeld (zie [Workflowmodellen maken](/help/sites-developing/workflows-models.md)).

## Proceskenmerken {#process-characteristics}

Voor elke processtap worden de volgende kenmerken beschreven.

### Java™ Class of ECMA Path {#java-class-or-ecma-path}

Processtappen worden gedefinieerd door een Java™-klasse of een ECMAScript.

* Voor de Java™-klasseprocessen wordt de volledig gekwalificeerde klassenaam opgegeven.
* Voor de ECMAScript-processen wordt het pad naar het script opgegeven.

### Payload {#payload}

De nuttige lading is de entiteit waarop een werkschemainstantie handelt. De payload wordt impliciet geselecteerd door de context waarbinnen een werkschemainstantie is begonnen.

Als bijvoorbeeld een workflow wordt toegepast op een AEM pagina *P* dan *P* wordt van stap tot stap doorgegeven terwijl de workflow wordt uitgevoerd, waarbij elke stap optioneel wordt uitgevoerd *P* in zekere zin .

In het meest voorkomende geval is de lading een JCR-knooppunt in de repository (bijvoorbeeld een AEM Pagina of Element). Een JCR-knooppuntlading wordt doorgegeven als een tekenreeks die een JCR-pad of een JCR-id (UUID) is. Soms kan de lading een bezit JCR (die als weg JCR wordt overgegaan), een URL, een binair voorwerp, of een generisch voorwerp Java™ zijn. De individuele processtappen die op de lading handelen zullen gewoonlijk een lading van een bepaald type verwachten, of verschillend afhankelijk van het ladingstype handelen. Voor elk hieronder beschreven proces wordt het verwachte ladingstype, indien van toepassing, beschreven.

### Argumenten {#arguments}

Sommige workflowprocessen accepteren argumenten die de beheerder opgeeft bij het instellen van de workflowstap.

Argumenten worden als één tekenreeks ingevoerd in het dialoogvenster **Procesargumenten** eigenschap in de **Eigenschappen** van de werkstroomeditor. Voor elk hieronder beschreven proces, wordt het formaat van het argumentkoord beschreven in een eenvoudige grammatica EBNF. De volgende code geeft bijvoorbeeld aan dat de argumenttekenreeks bestaat uit een of meer door komma&#39;s gescheiden paren, waarbij elk paar bestaat uit een naam (die een tekenreeks is) en een waarde, gescheiden door een dubbele dubbele dubbele punt:

```
    args := name '::' value [',' name '::' value]*
    name := /* A string */
    value := /* A string */
```


### Time-out {#timeout}

Na deze time-outperiode is de workflowstap niet meer operationeel. Sommige workflowprocessen respecteren de time-out, andere niet en worden genegeerd.

### Machtigingen {#permissions}

De sessie die aan de `WorkflowProcess` wordt gesteund door de de dienstgebruiker voor de dienst van het werkschemaproces, die de volgende toestemmingen bij de wortel van de bewaarplaats heeft:

* `jcr:read`
* `rep:write`
* `jcr:versionManagement`
* `jcr:lockManagement`
* `crx:replicate`

Als die set machtigingen niet voldoende is voor uw `WorkflowProcess` de implementatie, dan moet het een zitting met de vereiste toestemmingen gebruiken.

De geadviseerde manier om dit te doen is een de dienstgebruiker te gebruiken die met de noodzakelijke, maar minimale, vereiste ondergroep van toestemmingen wordt gecreeerd.

>[!CAUTION]
>
>Als u een upgrade uitvoert vanaf een versie die ouder is dan AEM 6.2, moet u mogelijk uw implementatie bijwerken.
>
>In vorige versies werd de beheersessie doorgegeven aan de `WorkflowProcess` implementaties en konden volledige toegang tot de bewaarplaats dan hebben zonder het moeten specifieke ACLs bepalen.
>
>De machtigingen zijn nu gedefinieerd als hierboven ([Machtigingen](#permissions)). Net als de aanbevolen methode voor het bijwerken van uw implementatie.
>
>Een kortetermijnoplossing is ook beschikbaar voor achterwaartse compatibiliteitsdoeleinden wanneer codeveranderingen niet haalbaar zijn:
>
>* De webconsole gebruiken ( `/system/console/configMgr` zoek de **Adobe Granite Workflow Configuration Service**
>
>* de **Verouderde modus van workflowproces**
>
>Hiermee wordt het oude gedrag van het opgeven van een beheersessie voor de `WorkflowProcess` en opnieuw onbeperkte toegang te verlenen tot de gehele gegevensopslagruimte.

## Workflowbeheerprocessen {#workflow-control-processes}

De volgende processen voeren geen handelingen uit op inhoud. Zij dienen om het gedrag van het werkschema zelf te controleren.

### AbsoluteTimeAutoAdvancer (Absolute Time Auto Advancer) {#absolutetimeautoadvancer-absolute-time-auto-advancer}

De `AbsoluteTimeAutoAdvancer` (Absolute Tijd AutoGeavanceerde) processen gedraagt zich identiek aan **AutoAdvancer**, behalve dat het op een bepaalde tijd en datum in plaats van na een bepaalde tijdsduur vervalt.

* **Java™-klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AbsoluteTimeAutoAdvancer`
* **Payload**: Geen.
* **Argumenten**: Geen.
* **Time-out**: Procestijden vervallen wanneer de ingestelde tijd en datum zijn bereikt.

### AutoAdvancer (Auto Advancer) {#autoadvancer-auto-advancer}

De `AutoAdvancer` wordt de workflow automatisch naar de volgende stap verplaatst. Als er meerdere mogelijke volgende stappen zijn (bijvoorbeeld als er een OF-splitsing is), wordt de workflow in de *standaardroute*, als er een is opgegeven, anders wordt de workflow niet verder ontwikkeld.

* **Java™-klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AutoAdvancer`

* **Payload**: Geen.
* **Argumenten**: Geen.
* **Time-out**: Procestijden verlopen na ingestelde tijdsduur.

### ProcessAssembler (procesvergadering) {#processassembler-process-assembler}

De `ProcessAssembler` het proces voert veelvoudige subprocessen opeenvolgend in één enkele werkschemastap uit. Als u de opdracht `ProcessAssembler`, maakt u één stap van dit type in uw workflow en stelt u de argumenten ervan in om de namen en argumenten van de subprocessen aan te geven die u wilt uitvoeren.

* **Java™-klasse**: `com.day.cq.workflow.impl.process.ProcessAssembler`

* **Payload**: Een DAM-element, AEM pagina of geen lading (afhankelijk van de vereisten van subprocessen).
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

* **Time-out**: Met respect.

Bijvoorbeeld:

* Haal de metagegevens uit het element.
* Maak drie miniaturen van de drie opgegeven formaten.
* Maak een JPEG-afbeelding van het element, ervan uitgaande dat het element oorspronkelijk geen GIF of PNG is (in welk geval er geen JPEG wordt gemaakt).
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
>Wijzig niets in de `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven dat u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

### delete {#delete}

Het item in het opgegeven pad wordt verwijderd.

* **ECMAScript-pad**: `/libs/workflow/scripts/delete.ecma`

* **Payload**: JCR-pad
* **Argumenten**: Geen
* **Time-out**: genegeerd

### nop {#noop}

Dit is het null-proces. Er wordt geen bewerking uitgevoerd, maar er wordt een foutopsporingsbericht geregistreerd.

* **ECMAScript-pad**: `/libs/workflow/scripts/noop.ecma`

* **Payload**: Geen
* **Argumenten**: Geen
* **Time-out**: genegeerd

### rule-false {#rule-false}

Dit is een null-proces dat retourneert `false` op de `check()` methode.

* **ECMAScript-pad**: `/libs/workflow/scripts/rule-false.ecma`

* **Payload**: Geen
* **Argumenten**: Geen
* **Time-out**: genegeerd

### monster {#sample}

Dit is een voorbeeld van een ECMAScript-proces.

* **ECMAScript-pad**: `/libs/workflow/scripts/sample.ecma`

* **Payload**: Geen
* **Argumenten**: Geen
* **Time-out**: genegeerd

### LockProcess {#lockprocess}

Vergrendelt de lading van de workflow.

* **Java™-klasse:** `com.day.cq.workflow.impl.process.LockProcess`

* **Payload:** JCR_PATH en JCR_UID
* **Argumenten:** Geen
* **Time-out:** Genegeerd

De stap heeft geen effect in de volgende omstandigheden:

* De lading is al vergrendeld
* Het payload-knooppunt bevat geen onderliggende node jcr:content

### UnlockProcess {#unlockprocess}

Ontgrendelt de lading van de workflow.

* **Java™-klasse:** `com.day.cq.workflow.impl.process.UnlockProcess`

* **Payload:** JCR_PATH en JCR_UID
* **Argumenten:** Geen
* **Time-out:** Genegeerd

De stap heeft geen effect in de volgende omstandigheden:

* De lading is al ontgrendeld
* Het payload-knooppunt bevat geen onderliggende node jcr:content

## Versionprocessen {#versioning-processes}

Het volgende proces voert een versie-verwante taak uit.

### CreateVersionProcess {#createversionprocess}

Hiermee maakt u een versie van de payload van de werkstroom (AEM pagina of DAM-element).

* **Java™-klasse**: `com.day.cq.wcm.workflow.process.CreateVersionProcess`

* **Payload**: Een JCR-pad of UUID die verwijst naar een pagina of DAM-element
* **Argumenten**: Geen
* **Time-out**: Met respect
