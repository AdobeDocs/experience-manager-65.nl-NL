---
title: Referentie workflowproces
description: Raadpleeg deze naslaggids voor workflows in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: a9de8ec6-6948-4643-89c3-62d9b1f6293a
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Referentie workflowproces{#workflow-process-reference}

AEM biedt verschillende processtappen die kunnen worden gebruikt voor het maken van workflowmodellen. De het processtappen van de douane kunnen ook voor taken worden toegevoegd die niet door de ingebouwde stappen worden behandeld (zie [ Creërend de Modellen van het Werkschema ](/help/sites-developing/workflows-models.md)).

## Proceskenmerken {#process-characteristics}

Voor elke processtap worden de volgende kenmerken beschreven.

### Java™ Class of ECMA Path {#java-class-or-ecma-path}

Processtappen worden gedefinieerd door een Java™-klasse of een ECMAScript.

* Voor de Java™-klasseprocessen wordt de volledig gekwalificeerde klassenaam opgegeven.
* Voor de ECMAScript-processen wordt het pad naar het script opgegeven.

### Payload {#payload}

De nuttige lading is de entiteit waarop een werkschemainstantie handelt. De payload wordt impliciet geselecteerd door de context waarbinnen een werkschemainstantie is begonnen.

Bijvoorbeeld, als een werkschema wordt toegepast op een AEM pagina *P* dan *P* van stap tot stap wordt overgegaan aangezien het werkschema vooruitgaat, met elke stap naar keuze handelend op *P* in één of andere manier.

In het meest voorkomende geval is de lading een JCR-knooppunt in de repository (bijvoorbeeld een AEM Pagina of Element). Een JCR-knooppuntlading wordt doorgegeven als een tekenreeks die een JCR-pad of een JCR-id (UUID) is. Soms kan de lading een bezit JCR (die als weg JCR wordt overgegaan), een URL, een binair voorwerp, of een generisch voorwerp Java™ zijn. De individuele processtappen die op de lading handelen zullen gewoonlijk een lading van een bepaald type verwachten, of verschillend afhankelijk van het ladingstype handelen. Voor elk hieronder beschreven proces wordt het verwachte ladingstype, indien van toepassing, beschreven.

### Argumenten {#arguments}

Sommige workflowprocessen accepteren argumenten die de beheerder opgeeft bij het instellen van de workflowstap.

De argumenten zijn ingegaan als één enkel koord in het **bezit van de Argumenten van het Proces** in de **ruit van Eigenschappen** van de werkschemaredacteur. Voor elk hieronder beschreven proces, wordt het formaat van het argumentkoord beschreven in een eenvoudige grammatica EBNF. De volgende code geeft bijvoorbeeld aan dat de argumenttekenreeks bestaat uit een of meer door komma&#39;s gescheiden paren, waarbij elk paar bestaat uit een naam (die een tekenreeks is) en een waarde, gescheiden door een dubbele dubbele dubbele punt:

```
    args := name '::' value [',' name '::' value]*
    name := /* A string */
    value := /* A string */
```


### Time-out {#timeout}

Na deze time-outperiode is de workflowstap niet meer operationeel. Sommige workflowprocessen respecteren de time-out, andere niet en worden genegeerd.

### Machtigingen {#permissions}

De sessie die aan de `WorkflowProcess` wordt doorgegeven, wordt ondersteund door de servicegebruiker voor de workflowprocesservice, die de volgende machtigingen heeft in de hoofdmap van de opslagplaats:

* `jcr:read`
* `rep:write`
* `jcr:versionManagement`
* `jcr:lockManagement`
* `crx:replicate`

Als die set machtigingen niet voldoende is voor uw `WorkflowProcess` -implementatie, moet deze een sessie met de vereiste machtigingen gebruiken.

De geadviseerde manier om dit te doen is een de dienstgebruiker te gebruiken die met de noodzakelijke, maar minimale, vereiste ondergroep van toestemmingen wordt gecreeerd.

>[!CAUTION]
>
>Als u een upgrade uitvoert vanaf een versie die ouder is dan AEM 6.2, moet u mogelijk uw implementatie bijwerken.
>
>In vorige versies, werd de admin zitting overgegaan tot de `WorkflowProcess` implementaties en kon dan volledige toegang tot de bewaarplaats hebben zonder het moeten specifieke ACLs bepalen.
>
>De toestemmingen worden nu bepaald zoals hierboven ([ Toestemmingen ](#permissions)). Net als de aanbevolen methode voor het bijwerken van uw implementatie.
>
>Een kortetermijnoplossing is ook beschikbaar voor achterwaartse compatibiliteitsdoeleinden wanneer codeveranderingen niet haalbaar zijn:
>
>* Gebruikend de Console van het Web ( `/system/console/configMgr` bepaal de plaats van de **Dienst van de Configuratie van het Werkschema van de Adobe Granite**
>
>* laat de **Verouderde Wijze van het Proces van het Werkschema** toe
>
>Dit keert terug naar het oude gedrag van het verstrekken van een adminsessie aan de `WorkflowProcess` implementatie en verleent opnieuw onbeperkte toegang tot de volledige bewaarplaats.

## Workflowbeheerprocessen {#workflow-control-processes}

De volgende processen voeren geen handelingen uit op inhoud. Zij dienen om het gedrag van het werkschema zelf te controleren.

### AbsoluteTimeAutoAdvancer (Absolute Time Auto Advancer) {#absolutetimeautoadvancer-absolute-time-auto-advancer}

Het `AbsoluteTimeAutoAdvancer` (Absolute AutoBevordering van de Tijd) proces gedraagt zich identiek aan **AutoAdvancer**, behalve dat het tijden uit op een bepaalde tijd en datum, in plaats van na een bepaalde tijdsduur.

* **Klasse Java™**: `com.adobe.granite.workflow.console.timeout.autoadvance.AbsoluteTimeAutoAdvancer`
* **Payload**: Geen.
* **Argumenten**: niets.
* **Onderbreking**: De tijden van het proces uit wanneer de vastgestelde tijd en de datum worden bereikt.

### AutoAdvancer (Auto Advancer) {#autoadvancer-auto-advancer}

Het `AutoAdvancer` -proces gaat automatisch door naar de volgende stap. Als er meer dan één mogelijke volgende stap (bijvoorbeeld is, als er OF gesplitst is) dan zal dit proces het werkschema langs de *standaardroute* vooruitgaan, als is gespecificeerd, anders zal het werkschema niet geavanceerd zijn.

* **Klasse Java™**: `com.adobe.granite.workflow.console.timeout.autoadvance.AutoAdvancer`

* **Payload**: Geen.
* **Argumenten**: niets.
* **Onderbreking**: De tijden van het proces uit na vastgestelde tijdsduur.

### ProcessAssembler (procesvergadering) {#processassembler-process-assembler}

Het `ProcessAssembler` -proces voert meerdere subprocessen opeenvolgend uit in één workflowstap. Als u `ProcessAssembler` wilt gebruiken, maakt u één stap van dit type in uw workflow en stelt u de argumenten ervan in om de namen en argumenten van de subprocessen aan te geven die u wilt uitvoeren.

* **Klasse Java™**: `com.day.cq.workflow.impl.process.ProcessAssembler`

* **Payload**: Een element DAM, AEM Pagina, of geen lading (hangt van vereisten van subprocessen af).
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

* **Onderbreking**: Eerbiedigd.

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
>Wijzig niets in het `/libs` -pad.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert, wordt overschreven (en dat deze kan worden overschreven wanneer u een hotfix of functiepakket toepast).

### delete {#delete}

Het item in het opgegeven pad wordt verwijderd.

* **weg ECMAScript**: `/libs/workflow/scripts/delete.ecma`

* **Payload**: De weg van JCR
* **Argumenten**: niets
* **Onderbreking**: Genegeerd

### nop {#noop}

Dit is het null-proces. Er wordt geen bewerking uitgevoerd, maar er wordt een foutopsporingsbericht geregistreerd.

* **weg ECMAScript**: `/libs/workflow/scripts/noop.ecma`

* **Payload**: niets
* **Argumenten**: niets
* **Onderbreking**: Genegeerd

### rule-false {#rule-false}

Dit is een null-proces dat `false` retourneert voor de `check()` -methode.

* **weg ECMAScript**: `/libs/workflow/scripts/rule-false.ecma`

* **Payload**: niets
* **Argumenten**: niets
* **Onderbreking**: Genegeerd

### monster {#sample}

Dit is een voorbeeld van een ECMAScript-proces.

* **weg ECMAScript**: `/libs/workflow/scripts/sample.ecma`

* **Payload**: niets
* **Argumenten**: niets
* **Onderbreking**: Genegeerd

### LockProcess {#lockprocess}

Vergrendelt de lading van de workflow.

* **Java™ klasse:** `com.day.cq.workflow.impl.process.LockProcess`

* **Payload:** JCR_PATH en JCR_UID
* **Argumenten:** niets
* **Onderbreking:** genegeerd

De stap heeft geen effect in de volgende omstandigheden:

* De lading is al vergrendeld
* Het payload-knooppunt bevat geen onderliggende node jcr:content

### UnlockProcess {#unlockprocess}

Ontgrendelt de lading van de workflow.

* **Java™ klasse:** `com.day.cq.workflow.impl.process.UnlockProcess`

* **Payload:** JCR_PATH en JCR_UID
* **Argumenten:** niets
* **Onderbreking:** genegeerd

De stap heeft geen effect in de volgende omstandigheden:

* De lading is al ontgrendeld
* Het payload-knooppunt bevat geen onderliggende node jcr:content

## Versionprocessen {#versioning-processes}

Het volgende proces voert een versie-verwante taak uit.

### CreateVersionProcess {#createversionprocess}

Hiermee maakt u een versie van de payload van de werkstroom (AEM pagina of DAM-element).

* **Java™ klasse**: `com.day.cq.wcm.workflow.process.CreateVersionProcess`

* **Payload**: Een weg JCR of UUID die naar een pagina of activa DAM verwijst
* **Argumenten**: niets
* **Onderbreking**: Eerbiedigd
