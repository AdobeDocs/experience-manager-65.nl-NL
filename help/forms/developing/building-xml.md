---
title: Hoe te om de uitvoeren manuscriptdienst in AEM Forms op JEE Workbench te gebruiken om de gegevens van XML te bouwen?
description: De service Script uitvoeren in AEM Forms op JEE Workbench gebruiken om XML-gegevens te maken
source-git-commit: 730ae7cd6cd04eb6377b37eafe29db597e93cce3
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---

# De service Script uitvoeren in AEM Forms op JEE Workbench gebruiken om XML-gegevens te maken {#using-execute-script-service-forms-jee-workbench}

AEM Forms heeft veel XML nodig voor JEE Process Management-workflows, bijvoorbeeld: XML-informatie kan in een proces worden ingebouwd en naar een Flex-toepassing in AEM Forms worden verzonden op de JEE Workspace, voor systeeminstellingen worden gebruikt of voor het doorgeven van informatie van en naar formulieren. Er zijn veel gevallen waarin een AEM Forms on JEE-ontwikkelaar XML moet beheren. Dit vereist vaak dat de XML via een AEM Forms on JEE-proces wordt beheerd.

Wanneer u werkt met eenvoudige XML-instellingen, kunt u de `Set Value`-service gebruiken. Dit is een standaard AEM Forms op JEE-service. Deze dienst plaatst de waarde van één of meerdere gegevenspunten in het model van procesgegevens. Voor zeer eenvoudige voorwaardelijke logica &quot;als dit, dan dat&quot;scenario&#39;s, kan deze dienst het doel aanpassen.

Nochtans, in complexere situaties, is de Vastgestelde dienst van de Waarde niet zo efficiënt. In deze situaties, moet men op een robuustere reeks programmeringsbevelen, zoals die baseren die door een programmeertaal zoals Java worden verstrekt. Het gebruik van Java voor het maken van complexe XML kan veel eenvoudiger en duidelijker zijn dan het maken van een XML-document op basis van eenvoudige tekst in de service Waarde instellen. Bovendien is het gemakkelijker om voorwaardelijk programmeren in Java dan binnen de Vastgestelde dienst van de Waarde op te nemen.

## Het gebruiken van de Dienst van het Manuscript in een Proces uitvoeren {#using-execute-script-service-in-process}

Binnen de standaard AEM Forms on JEE services die beschikbaar zijn in AEM Forms op JEE Workbench, is de `Execute Script` service. Met deze service kunt u scripts uitvoeren in processen en kunt u de `executeScript`-bewerking uitvoeren om dit te doen.

### Creeer een Toepassing en een Proces met de Dienst van het Manuscript van de &quot;Uitvoeren&quot;die als Activiteit wordt bepaald {#create-an-application}

De algemene toepassing en procesverwezenlijking zijn buiten-van-werkingsgebied voor dit leerprogramma, maar omwille van deze instructie, hebben wij een toepassing genoemd &quot;DemoApplication02&quot;gecreeerd. Ervan uitgaande dat er al een toepassing is gemaakt, moeten we in deze toepassing een proces maken om de service executeScript aan te roepen. Een proces toevoegen aan de toepassing die de `Execute Script`-service bevat:

1. Klik met de rechtermuisknop op de toepassing en selecteer [!UICONTROL New]. Selecteer [!UICONTROL Process] in het vervolgkeuzemenu [!UICONTROL New]. Geef uw proces een naam, voeg indien nodig een beschrijving toe en selecteer het pictogram dat u wilt weergeven voor dit proces. In het kader van deze zelfstudie hebben we een proces gemaakt en het de naam `executeScriptDemoProcess` gegeven.
1. Definieer de beginpunten of kies de eenvoudige optie om de beginpunten later toe te voegen.
1. Het proces wordt nu gemaakt en wordt automatisch geopend in het venster [!UICONTROL Process Design]. Klik in dit venster op het pictogram Activiteitenkiezer boven aan het venster Process Design (Process Design) en sleep de nieuwe activiteit naar de zwembaan. Op dit punt wordt [!UICONTROL Define Activity Window] weergegeven (zie onderstaande afbeelding).
   ![Activiteit definiëren](assets/define-activity.jpg)
1. De service executeScript vindt u onder de set `Foundation` services. De naam van de Diensten maakt een lijst van het voorwerp als `Execute Script – 1.0` met de naam van de Verrichting `executeScript`. Klik om dit item te selecteren.
1. Dit proces moet nu worden gemaakt en het venster [!UICONTROL Process Properties] moet standaard in het linkerdeelvenster worden weergegeven.

#### Voeg een Manuscript aan het Proces met de Dienst van het Manuscript van de &quot;Uitvoeren&quot; toe {#add-script-to-process-with-execute-script}

Zodra het proces met de &quot;Uitvoeren de bepaalde activiteit van de Dienst van het Manuscript&quot;is gecreeerd, kan men dan een manuscript aan dit proces toevoegen. Een script toevoegen aan dit proces:

1. Navigeer naar het palet [!UICONTROL Process Properties]. Vouw in dit palet de sectie [!UICONTROL Input] uit en klik op het pictogram &quot;...&quot;.

1. Schrijf uw script in het tekstvak dat wordt weergegeven. Wanneer het manuscript is geschreven druk O.K. (zie hieronder Figuur).
   ![Script uitvoeren](assets/execute-script.jpg)

## XML maken met de Scriptservice uitvoeren {#create-xml-execute-script-service}

Nadat een proces is gemaakt met de service Script uitvoeren, kunt u dit script gebruiken om XML te maken. Men zou de hieronder beschreven manuscripten in het tekstvakje schrijven dat in Add een Manuscript aan het Proces met de `Execute Script` sectie van de Dienst hierboven wordt beschreven.

**Informatie over de technologie van de Scriptservice uitvoeren**

Om te weten wat de capaciteiten en de beperkingen van de dienst van het Manuscript zijn, moet men de technologische onderbouwing van de dienst kennen. AEM Forms on JEE gebruikt de parser Apache Xerces Document Object Model (DOM) om XML-variabelen in processen te maken en op te slaan. Xerces is een Java-implementatie van de Document Object Model Specification van W3C; gedefinieerd [hier](https://dom.spec.whatwg.org/). De DOM-specificatie is een standaardmanier om XML te manipuleren die al sinds 1998 bestaat. De Java-implementatie van Xerces, Xerces-J, ondersteunt DOM Level 2 versie 1.0.

De Java-klassen die worden gebruikt voor het opslaan van XML-variabelen zijn:

* org.apache.xerces.dom.NodeImpl en

* org.apache.xerces.dom.DocumentImpl

DocumentImpl is een subklasse van NodeImpl, zodat kan worden verondersteld dat om het even welke procesvariabele van XML een afleiding NodeImpl is. U kunt de documentatie voor NodeImpl [hier](http://xerces.apache.org/xerces-j/apiDocs/org/apache/xerces/dom/NodeImpl.html) vinden.

**Een voorbeeld-XML-ontwerp met behulp van de Scriptservice uitvoeren**

Hier volgt een voorbeeld van het maken van XML in een service Script uitvoeren. Het proces heeft een variabele, knoop, die van type XML is. Het eindresultaat van deze activiteit zal een document van XML zijn. Wat dat document doet, of hoe het op het algemene proces van toepassing is is is buiten het werkingsgebied voor dit leerprogramma; uiteindelijk komt het neer op wat XML wordt vereist om in de algemene toepassing te doen. Zoals vermeld in de inleiding, kan XML voor vele doeleinden in AEM Forms op JEE vormen en processen worden gebruikt, is dit eenvoudig een verklaring van hoe te om de activiteit van het Manuscript van de Uitvoer te coderen om een eenvoudig document van XML uit te voeren.

Een eenvoudig Java-script voor het uitvoeren van XML zou er ongeveer als volgt uitzien:

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
>dat de bovengenoemde DOM-objecten in het script moeten worden geïmporteerd.

Het resultaat van dit eenvoudige script is een nieuw XML-document met een variabeleknooppunt dat is ingesteld op:

```xml
<resources>

<resource id="first item id" value="first item value"/>

</resources>
```

**Een iteratieve lus gebruiken om knooppunten toe te voegen aan de XML**

U kunt ook knooppunten toevoegen aan een bestaande XML-variabele in het proces. De variabele, node, bevat het object XML dat we zojuist hebben gemaakt.

```xml
Document document = patExecContext.getProcessDataValue("/process_data/node");

NodeList childNodes = document.getChildNodes();

int numChildren = childNodes.getLength();

for (int i = 0; i < numChildren; i++)

{

Node currentChild = childNodes.item(i);

if (currentChild.getNodeType() == Node.ELEMENT_NODE)

{

// found the top level node

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



