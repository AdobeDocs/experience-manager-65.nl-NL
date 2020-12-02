---
title: Bewegingsaanpassing
seo-title: Bewegingsaanpassing
description: De bewegingen in uw AEM Forms-app aanpassen
seo-description: De bewegingen in uw AEM Forms-app aanpassen
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Bewegingsaanpassing {#gesture-customization}

U kunt de gebaren van de AEM Forms-app aanpassen om een aparte methode voor het werken met de app te bieden. U kunt bijvoorbeeld nieuwe bewegingen toevoegen om een taak of beginpunt te openen of te sluiten.

## Bewegingen aanpassen in AEM Forms-app {#to-customize-gestures-in-aem-forms-app}

In de AEM Forms-app wordt met de veegbeweging links een nieuwe taak of beginpunt geopend en met de veegbeweging rechts niets. In het volgende voorbeeld worden stappen beschreven voor het openen van een nieuwe taak of beginpunt voor het uitvoeren van de rechterveegbeweging in de AEM Forms-app.

1. Open uw project.

   * Voor iOS opent u `Capture.xcodeproj` in Xcode
   * Voor Android opent u het Android-project in Eclipse.
   * Voor Vensters, open `MWSWindows.sln` in Visual Studio.

1. Navigeer naar de map views en open het bestand `task.js` voor bewerking.

   * Navigeer in Xcode naar de map **Vastleggen > www > wsmobile > js > runtime > views**.
   * Navigeer in Eclipse naar de map **assets > www > wsmobile > js > runtime > views**.
   * Navigeer in Visual Studio naar de map **MWSWindows > www > wsmobile > js > runtime > views**.

   >[!NOTE]
   >
   >Het bestand task.js bevat de backboneweergave die is gekoppeld aan elke taak of elk beginpunt dat in de lijst met taken of beginpunten wordt vermeld.

1. Zoek in het bestand `task.js` naar de eigenschap events van de weergave.

   De eigenschap events is een kaart met elke vermelding in de indeling:

   `"EventName Selector": "Function"`

   Wanneer u een JavaScript-gebeurtenis met de naam `EventName`activeert op een HTML-element dat is opgegeven door `Selector`, wordt `Function`aangeroepen.

1. Zoeken

   * &quot;tap.taskContentArea&quot;: &quot;onTaskClick&quot;,

      &quot;tap.taskOpenArea&quot;: &quot;onTaskClick&quot;,

      &quot;tik.task-content&quot;: &quot;onTaskClick&quot;,

      &quot;tap.last_empty_div&quot;: &quot;onTaskClick&quot;,
   en vervangen door

   * &quot;swipe.taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe.taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;veeggebaar.task-content&quot;: &quot;onTaskClick&quot;,

      &quot;veeggebaar.last_empty_div&quot;: &quot;onTaskClick&quot;,


1. Sla het `task.js`-bestand op en sluit het.
1. De AEM Forms-app ontwikkelen en uitvoeren. Nu kunt u een toepassing openen met een veegbeweging naar links en een veegbeweging naar rechts.

Op dezelfde manier kunt u ook wijzigingen aanbrengen in andere weergaven voor verschillende combinaties van bewegingen, HTML-elementen en functies.
