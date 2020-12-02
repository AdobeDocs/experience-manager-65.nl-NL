---
title: Gebeurtenissen van formulieren aanpassen
seo-title: Gebeurtenissen van formulieren aanpassen
description: Als een gebruiker meer dan 60 seconden aan een veld doorgeeft, wordt een veldbezoek-gebeurtenis geactiveerd en worden de gegevens van het veld naar Adobe SiteCatalyst verzonden.
seo-description: Als een gebruiker meer dan 60 seconden aan een veld doorgeeft, wordt een veldbezoek-gebeurtenis geactiveerd en worden de gegevens van het veld naar Adobe SiteCatalyst verzonden.
uuid: 2f790085-2f1a-45be-9a69-6100c76dcae0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 60d67c6b-5994-42ef-b159-ed6edf5cf9d4
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 1%

---


# Gebeurtenistracking van formulieren aanpassen {#customizing-form-event-tracking}

Uit het vak worden de volgende gebeurtenissen bijgehouden in een adaptieve vorm die geschikt is voor analyses:

<table>
 <tbody>
  <tr>
   <th>Gebeurtenis</th>
   <th>Beschikbare variabelen</th>
  </tr>
  <tr>
   <td>renderen</td>
   <td>formName, formTitle, formInstance, source</td>
  </tr>
  <tr>
   <td>opgeven</td>
   <td>formName, formTitle, formInstance, panelName, panelTitle</td>
  </tr>
  <tr>
   <td>save</td>
   <td>formName, formTitle, formInstance, panelName, source</td>
  </tr>
  <tr>
   <td>submit</td>
   <td>formName, formTitle, formInstance, source</td>
  </tr>
  <tr>
   <td>error</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td>
  </tr>
  <tr>
   <td>help</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td>
  </tr>
  <tr>
   <td>fieldVisit</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle<br /> </td>
  </tr>
  <tr>
   <td>panelVisit</td>
   <td>formName, formTitle, panelName, panelTitle</td>
  </tr>
 </tbody>
</table>

## Tijdslimiet {#customizing-the-field-visit-event-timeout} voor de gebeurtenis &quot;visit&quot; van het veld aanpassen

Als een gebruiker meer dan 60 seconden doorbrengt in een veld, wordt in de standaardinstelling AEM formulier een gebeurtenis `fieldvisit` geactiveerd en worden de gegevens van het veld verzonden naar Adobe Analytics. U kunt de basislijn voor het bijhouden van de veldtijd aanpassen bij AEM Forms Analytics Configuration op AEM Configuration-console (/system/console/configMgr) om de time-outlimiet te verhogen of te verlagen.

## De volgende gebeurtenissen aanpassen {#customizing-the-tracking-events}

U kunt de functie `trackEvent`beschikbaar in `/libs/afanalytics/js/custom.js` dossier wijzigen om gebeurtenis het volgen aan te passen. Wanneer een gebeurtenis die wordt bijgehouden zich in een adaptieve vorm voordoet, wordt de functie `trackEvent`aangeroepen. De functie `trackEvent` accepteert twee parameters: `eventName`en `variableValueMap`.

U kunt waarde van *eventName* en *variableValueMap* argumenten evalueren om het volgende gedrag van gebeurtenissen te veranderen. U kunt er bijvoorbeeld voor kiezen om de gegevens naar de analytische server te verzenden nadat een aantal foutgebeurtenissen is opgetreden. U kunt ook de volgende aanpassingen uitvoeren:

* U kunt een drempeltijd instellen voordat u de gebeurtenis verzendt.
* U kunt een staat handhaven om actie te besluiten, bijvoorbeeld, *fieldVisit* duwt een dummy gebeurtenis die op timestamp van de laatste gebeurtenis wordt gebaseerd.
* U kunt de functie `pushEvent` gebruiken om de gebeurtenis naar de analytische server *te verzenden.*

* U kunt ervoor kiezen om de gebeurtenis helemaal niet naar de analyseserver te duwen.

### Voorbeeld {#sample}

In het volgende voorbeeld wordt de status voor de *error*-gebeurtenis van elk *fieldName*-kenmerk behouden. De gebeurtenis wordt alleen naar de analyseserver verzonden als er opnieuw een fout optreedt.

```javascript
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## De panelgebeurtenis {#customizing-the-panelvisit-event} aanpassen

Bij de standaard AEM Forms-instelling wordt na elke 60 seconden gecontroleerd of het venster met het adaptieve formulier actief is. Als het venster actief is, wordt een `panelVisit`gebeurtenis geactiveerd naar Adobe Analytics. Hiermee kunt u controleren of het document of formulier actief is en kunt u de tijd berekenen die aan het desbetreffende formulier of document is besteed.

>[!NOTE]
>
>De naam van de gebeurtenis die wordt gebruikt om activiteit op te halen en de tijd die wordt doorgebracht te berekenen is &quot;panelVisit&quot;. Deze gebeurtenis is anders dan de gebeurtenis die het deelvenster bezoeken in de bovenstaande tabel wordt weergegeven.

U kunt de functie programHeartBeatCheck die beschikbaar is in het `/libs/afanalytics/js/custom.js`-bestand wijzigen om deze gebeurtenis die regelmatig naar Adobe Analytics wordt verzonden, te wijzigen of te stoppen.
