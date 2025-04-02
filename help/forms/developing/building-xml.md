---
title: Hoe te om de uitvoeren manuscriptdienst in AEM Forms op JEE Workbench te gebruiken om de gegevens van XML te bouwen?
description: De service Script uitvoeren in AEM Forms op JEE Workbench gebruiken om XML-gegevens te maken
exl-id: 2ec57cd4-f41b-4e5c-849d-88ca3d2cfe19
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 361f0a5f2d1484cf594edfda73250c5690ed7cab
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---

# De service Script uitvoeren in AEM Forms op JEE Workbench gebruiken om XML-gegevens te maken {#using-execute-script-service-forms-jee-workbench}

AEM Forms heeft bijvoorbeeld veel XML-gegevens nodig voor JEE Process Management-workflows. XML-gegevens kunnen in een proces worden ingebouwd en naar een Flex-toepassing in AEM Forms op JEE Workspace worden verzonden, voor systeeminstellingen worden gebruikt of voor het doorgeven van informatie van en naar formulieren. Er zijn veel gevallen waarin een AEM Forms on JEE-ontwikkelaar XML moet beheren. Dit vereist vaak dat de XML via een AEM Forms on JEE-proces wordt beheerd.

Wanneer u werkt met eenvoudige XML-instellingen, kunt u de service `Set Value` gebruiken. Dit is een standaard AEM Forms op JEE-service. Deze dienst plaatst de waarde van één of meerdere gegevenspunten in het model van procesgegevens. Voor eenvoudige voorwaardelijke logica &quot;als dit, dan dat&quot;scenario&#39;s, kan deze dienst het doel aanpassen.

In complexere situaties is de service Waarde instellen echter niet zo effectief. In deze situaties moet u vertrouwen op een robuustere set programmeringsopdrachten, zoals die welke worden geleverd door een programmeertaal zoals Java™. Het gebruik van Java™ om complexe XML te maken kan veel eenvoudiger en duidelijker zijn dan het maken van een XML-document op basis van eenvoudige tekst in de service Waarde instellen. Bovendien is het gemakkelijker om voorwaardelijk programmeren in Java™ dan binnen de Vastgestelde dienst van de Waarde op te nemen.

## Het gebruiken van de Dienst van het Manuscript in een Proces uitvoeren {#using-execute-script-service-in-process}

Binnen de standaard AEM Forms on JEE services die beschikbaar zijn in AEM Forms op JEE Workbench, is de `Execute Script` -service. Met deze service kunt u scripts uitvoeren in processen en beschikt u over de bewerking `executeScript` om dat te doen.

### Creeer een Toepassing en een Proces met de Dienst van het Manuscript van de &quot;Uitvoeren&quot;die als Activiteit wordt bepaald {#create-an-application}

De algemene toepassing en het proces worden gemaakt buiten het bereik van deze zelfstudie, maar in het belang van deze instructie is een toepassing met de naam &quot;DemoApplication02&quot; gemaakt. Ervan uitgaande dat er al een toepassing is gemaakt, moet u in deze toepassing een proces maken om de service executeScript aan te roepen. U kunt als volgt een proces toevoegen aan de toepassing die de service `Execute Script` bevat:

1. Klik met de rechtermuisknop op de toepassing en selecteer **[!UICONTROL New]** . Selecteer **[!UICONTROL Process]** in het menu **[!UICONTROL New]** slide-out. Geef een naam op voor het proces, voeg desgewenst een beschrijving toe en selecteer het pictogram dat u wilt weergeven voor dit proces. In deze zelfstudie hebben we een proces gemaakt met de naam `executeScriptDemoProcess` .
1. Definieer de beginpunten of kies de eenvoudige optie om de beginpunten later toe te voegen.
1. Het proces wordt nu gemaakt en wordt automatisch geopend in het [!UICONTROL Process Design] -venster. Klik in dit venster op het pictogram Activiteitenkiezer boven aan het venster Process Design (Process Design) en sleep de nieuwe activiteit naar de zwembaan. Op dit punt wordt [!UICONTROL Define Activity Window] weergegeven (zie onderstaande afbeelding).
   ![ bepalen Activiteit ](assets/define-activity.jpg)
1. De service executeScript vindt u onder de set met services van `Foundation` . De naam van de Diensten maakt een lijst van het voorwerp als `Execute Script – 1.0` met de naam van de Verrichting `executeScript`. Klik om dit item te selecteren.
1. Dit proces moet nu worden gemaakt en het venster [!UICONTROL Process Properties] moet standaard in het linkerdeelvenster worden weergegeven.

#### Voeg een Manuscript aan het Proces met de Dienst van het Manuscript van de &quot;Uitvoeren&quot; toe {#add-script-to-process-with-execute-script}

Zodra het proces met de &quot;Uitvoeren de bepaalde activiteit van de Dienst van het Manuscript&quot;is gecreeerd, kan men dan een manuscript aan dit proces toevoegen. Een script toevoegen aan dit proces:

1. Navigeer naar het palet [!UICONTROL Process Properties] . Vouw in dit palet de sectie [!UICONTROL Input] uit en klik op het pictogram &quot;...&quot;.

1. Schrijf uw script in het tekstvak dat wordt weergegeven. Wanneer het manuscript is geschreven, druk O.K. (zie hieronder Figuur).
   ![ voert Manuscript ](assets/execute-script.jpg) uit

## XML maken met de Scriptservice uitvoeren {#create-xml-execute-script-service}

Nadat een proces is gemaakt met de service Script uitvoeren, kunt u dit script gebruiken om XML te maken. U kunt de scripts schrijven die hieronder worden beschreven in het tekstvak dat wordt beschreven in het gedeelte Een script toevoegen aan het proces met de sectie `Execute Script` Service hierboven.

>[!NOTE]
>
> Als de JAVA-scriptcode langer is dan 10 regels, wordt het aanbevolen de code toe te voegen aan aangepaste DSC&#39;s (Document Service Components) in plaats van deze rechtstreeks in het proces te schrijven. Aangepaste DSC&#39;s verbeteren het onderhoud, de herbruikbaarheid en de prestaties door de workflows lichtgewicht te houden. Verwijzen naar deze componenten in werkschema&#39;s verzekert betere uitvoeringsefficiency en verhindert potentiële vertragingen die door het verwerken van grote codeblokken binnen het werkschema worden veroorzaakt.


**Ongeveer de Uitvoeren Technologie van de Dienst van het Manuscript**

Om te weten wat de capaciteiten en de beperkingen van de dienst van het Manuscript zijn, moet men de technologische steunen van de dienst kennen. AEM Forms on JEE gebruikt de parser Apache Xerces Document Object Model (DOM) om XML-variabelen in processen te maken en op te slaan. De middelen zijn een implementatie Java™ van het ModelSpecificatie van de Objecten van het Document van W3C [ ](https://dom.spec.whatwg.org/). De DOM-specificatie is een standaardmanier om XML te manipuleren die al sinds 1998 bestaat. De Java™-implementatie van Xerces, Xerces-J, ondersteunt DOM Level 2 versie 1.0.

De klassen Java™ die worden gebruikt om XML-variabelen op te slaan zijn:

* org.apache.xerces.dom.NodeImpl en

* org.apache.xerces.dom.DocumentImpl

DocumentImpl is een subklasse van NodeImpl, zodat kan worden verondersteld dat om het even welke procesvariabele van XML een afleiding NodeImpl is. Zie de documentatie van [ NodeImpl ](https://xerces.apache.org/xerces-j/apiDocs/org/apache/xerces/dom/NodeImpl.html) voor meer details.

**de BemonsteringsXML creatie die de Uitvoeren Dienst van het Manuscript gebruikt**

Hier volgt een voorbeeld van het maken van XML in een service Script uitvoeren. Het proces heeft een veranderlijke knoop die van type XML is. Het resultaat van deze activiteit is een XML-document. Wat dat document doet, of hoe het op het algemene proces van toepassing is is is buiten bereik voor deze zelfstudie; uiteindelijk komt het neer op wat XML in de algemene toepassing moet doen. Zoals vermeld in de inleiding, kan XML voor vele doeleinden in AEM Forms op JEE vormen en processen worden gebruikt, is dit eenvoudig een verklaring van hoe te om de activiteit van het Manuscript van de Uitvoer te coderen om een eenvoudig document van XML uit te voeren.

Een eenvoudige JavaScript voor het uitvoeren van XML zou er ongeveer als volgt uitzien:

```xml
import org.apache.xerces.dom.DocumentImpl;

import org.w3c.dom.Document;

import org.w3c.dom.Element;



Document document = new DocumentImpl();

Element topLevelResources = document.createElement("resources");

Element resource = document.createElement("resource");

resource.setAttribute("id", "first item id");

resource.setAttribute("value", "first item value");

topLevelResources.appendChild(resource);

document.appendChild(topLevelResources);

patExecContext.setProcessDataValue("/process_data/node", document);
```

>[!NOTE]
>
>De eerder vermelde DOM-objecten moeten in het script worden geïmporteerd.

Het resultaat van dit eenvoudige script is een nieuw XML-document met een knooppunt met variabele die is ingesteld op:

```xml
<resources>

<resource id="first item id" value="first item value"/>

</resources>
```

**Gebruikend een Herhalende lijn om Knooppunten aan XML toe te voegen**

U kunt ook knooppunten toevoegen aan een bestaande XML-variabele in het proces. De variabele, node, bevat het XML-object dat is gemaakt.

```xml
Document document = patExecContext.getProcessDataValue("/process_data/node");

NodeList childNodes = document.getChildNodes();

int numChildren = childNodes.getLength();

for (int i = 0; i < numChildren; i++)

{

Node currentChild = childNodes.item(i);

if (currentChild.getNodeType() == Node.ELEMENT_NODE)

{

// found the top-level node

Element newResource = document.createElement("resource");

newResource.setAttribute("id", "second item id");

newResource.setAttribute("value", "second item value");

currentChild.appendChild(newResource);

break;

}

}

patExecContext.setProcessDataValue("/process_data/node", document);
The variable node in the XML is now set to:

<resources> 

<resource id="first item id" value="first item value"/> 

<resource id="second item id" value="second item value"/> 

</resources>
```
