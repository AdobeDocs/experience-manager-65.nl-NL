---
title: Gebeurtenissen van formulieren aanpassen
description: Als een gebruiker meer dan 60 seconden aan een veld doorgeeft, wordt een veldbezoek-gebeurtenis geactiveerd en worden de gegevens van het veld naar Adobe SiteCatalyst verzonden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
exl-id: d0280a15-5d0d-49cf-bce9-ad1c40530eae
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

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
   <td>opslaan</td>
   <td>formName, formTitle, formInstance, panelName, source</td>
  </tr>
  <tr>
   <td>indienen</td>
   <td>formName, formTitle, formInstance, source</td>
  </tr>
  <tr>
   <td>fout</td>
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

Als een gebruiker meer dan 60 seconden in een veld doorbrengt, wordt bij de standaardinstelling AEM het formulier een `fieldvisit` Deze gebeurtenis wordt geactiveerd en de gegevens van het veld worden naar Adobe Analytics verzonden. U kunt de basislijn voor het bijhouden van de veldtijd aanpassen bij AEM Forms Analytics Configuration op AEM Configuration-console (/system/console/configMgr) om de time-outlimiet te verhogen of te verlagen.

## De volgende gebeurtenissen aanpassen {#customizing-the-tracking-events}

U kunt de `trackEvent`functie beschikbaar in `/libs/afanalytics/js/custom.js` bestand om het bijhouden van gebeurtenissen aan te passen. Wanneer een gebeurtenis die wordt bijgehouden zich in een adaptieve vorm voordoet, `trackEvent`functie wordt aangeroepen. De `trackEvent` function accepteert twee parameters: `eventName`en `variableValueMap`.

U kunt de waarde evalueren van *eventName* en *variableValueMap* argumenten om het gedrag voor bijhouden van gebeurtenissen te wijzigen. U kunt er bijvoorbeeld voor kiezen om de gegevens naar de analytische server te verzenden nadat een aantal foutgebeurtenissen is opgetreden. U kunt ook de volgende aanpassingen uitvoeren:

* U kunt een drempeltijd instellen voordat u de gebeurtenis verzendt.
* U kunt bijvoorbeeld een status behouden waarin u kunt beslissen welke actie wordt uitgevoerd. *fieldVisit* plaatst een dummygebeurtenis op basis van het tijdstempel van de laatste gebeurtenis.
* U kunt de `pushEvent` functie om de gebeurtenis naar de analytische server te verzenden *.*

* U kunt ervoor kiezen om de gebeurtenis helemaal niet naar de analyseserver te duwen.

### Monster {#sample}

Geef in het volgende voorbeeld de naam *fout* gebeurtenis van elk *fieldName* wordt behouden. De gebeurtenis wordt alleen naar de analyseserver verzonden als er opnieuw een fout optreedt.

```javascript
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## De gebeurtenis panelvisit aanpassen {#customizing-the-panelvisit-event}

Bij de standaard AEM Forms-instelling wordt na elke 60 seconden gecontroleerd of het venster met het adaptieve formulier actief is. Als het venster actief is, wordt een `panelVisit`gebeurtenis wordt geactiveerd naar Adobe Analytics. Hiermee kunt u controleren of het document of formulier actief is en kunt u de tijd berekenen die aan het desbetreffende formulier of document is besteed.

>[!NOTE]
>
>De naam van de gebeurtenis die wordt gebruikt om activiteit op te halen en de tijd die wordt doorgebracht te berekenen is &quot;panelVisit&quot;. Deze gebeurtenis is anders dan de gebeurtenis die het deelvenster bezoeken in de bovenstaande tabel wordt weergegeven.

U kunt de functie planningHeartBeatCheck wijzigen die beschikbaar is in het dialoogvenster `/libs/afanalytics/js/custom.js` bestand om deze gebeurtenis te wijzigen of te stoppen die regelmatig naar Adobe Analytics wordt verzonden.
