---
title: Gebeurtenissen van formulieren aanpassen
seo-title: Gebeurtenissen van formulieren aanpassen
description: Als een gebruiker meer dan 60 seconden aan een veld doorgeeft, wordt een gebeurtenis FieldVisit geactiveerd en worden de gegevens van het veld naar Adobe SiteCatalyst verzonden.
seo-description: Als een gebruiker meer dan 60 seconden aan een veld doorgeeft, wordt een gebeurtenis FieldVisit geactiveerd en worden de gegevens van het veld naar Adobe SiteCatalyst verzonden.
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


# Gebeurtenissen van formulieren aanpassen {#customizing-form-event-tracking}

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

## Tijdslimiet voor de gebeurtenis &#39;visit&#39; van het veld aanpassen {#customizing-the-field-visit-event-timeout}

Als een gebruiker in de standaard AEM-formulierinstelling meer dan 60 seconden doorbrengt in een veld, wordt een `fieldvisit` gebeurtenis geactiveerd en worden de gegevens van het veld naar Adobe Analytics verzonden. U kunt de de tijd volgende basislijn van het Gebied aanpassen onder de Configuratie van AEM Forms Analytics bij de console van de Configuratie AEM (/system/console/configMgr) om de onderbrekingsgrens te verhogen of te verminderen.

## De volgende gebeurtenissen aanpassen {#customizing-the-tracking-events}

U kunt de `trackEvent`functie wijzigen die beschikbaar is in `/libs/afanalytics/js/custom.js` het bestand om de gebeurtenis te volgen. Wanneer een gebeurtenis die wordt bijgehouden zich in een adaptieve vorm voordoet, wordt de `trackEvent`functie aangeroepen. De `trackEvent` functie accepteert twee parameters: `eventName`en `variableValueMap`.

U kunt de waarde van *eventName* - en *variableValueMap* -argumenten evalueren om het gedrag voor bijhouden van gebeurtenissen te wijzigen. U kunt er bijvoorbeeld voor kiezen om de gegevens naar de analytische server te verzenden nadat een aantal foutgebeurtenissen is opgetreden. U kunt ook de volgende aanpassingen uitvoeren:

* U kunt een drempeltijd instellen voordat u de gebeurtenis verzendt.
* U kunt een staat handhaven om actie te besluiten, bijvoorbeeld, *fieldVisit* duwt een dummygebeurtenis die op timestamp van de laatste gebeurtenis wordt gebaseerd.
* U kunt de `pushEvent` functie gebruiken om de gebeurtenis naar de analytische server te verzenden *.*

* U kunt ervoor kiezen om de gebeurtenis helemaal niet naar de analyseserver te duwen.

### Voorbeeld {#sample}

In het volgende voorbeeld blijft de status voor de *foutgebeurtenis* van elk *fieldName* -kenmerk behouden. De gebeurtenis wordt alleen naar de analyseserver verzonden als er opnieuw een fout optreedt.

```javascript
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## De gebeurtenis panelvisit aanpassen {#customizing-the-panelvisit-event}

Bij de standaardinstelling AEM Forms wordt na elke 60 seconden gecontroleerd of het venster met het adaptieve formulier actief is. Als het venster actief is, wordt een `panelVisit`gebeurtenis geactiveerd naar Adobe Analytics. Hiermee kunt u controleren of het document of formulier actief is en kunt u de tijd berekenen die aan het desbetreffende formulier of document is besteed.

>[!NOTE]
>
>De naam van de gebeurtenis die wordt gebruikt om activiteit op te halen en de tijd die wordt doorgebracht te berekenen is &quot;panelVisit&quot;. Deze gebeurtenis is anders dan de gebeurtenis die wordt weergegeven in de bovenstaande tabel voor het bezoek van het deelvenster.

U kunt de functie planningHeartBeatCheck die beschikbaar is in het `/libs/afanalytics/js/custom.js` bestand aanpassen om deze gebeurtenis die regelmatig naar Adobe Analytics wordt verzonden, te wijzigen of te stoppen.
