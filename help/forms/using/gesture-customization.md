---
title: Bewegingsaanpassing
description: Leer hoe u de bewegingen in de AEM Forms-app aanpast. U kunt de bewegingen aanpassen om een verschillende manier van interactie met de toepassing te bieden.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 6debb1a7-7889-4fdd-87c7-ecb87cc0b1f5
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Bewegingsaanpassing {#gesture-customization}

U kunt de gebaren van de AEM Forms-app aanpassen om een aparte methode voor het werken met de app te bieden. U kunt bijvoorbeeld nieuwe bewegingen toevoegen om een taak of beginpunt te openen of te sluiten.

## Bewegingen aanpassen in de AEM Forms-app {#to-customize-gestures-in-aem-forms-app}

In de AEM Forms-app wordt met de veegbeweging links een nieuwe taak of een nieuw beginpunt geopend, terwijl met de veegbeweging rechts niets wordt gedaan. In het volgende voorbeeld worden stappen beschreven voor het openen van een nieuwe taak of beginpunt voor het uitvoeren van de rechterveegbeweging in de AEM Forms-app.

1. Open uw project.

   * Voor iOS: open `Capture.xcodeproj` in Xcode
   * Voor Android opent u het Android-project in Eclipse.
   * Voor Windows: open `MWSWindows.sln` in Visual Studio.

1. Navigeer naar de map views en open de `task.js` bestand voor bewerking.

   * Navigeer in Xcode naar de **Vastleggen > www > wsmobile > js > runtime > views** map.
   * Ga in Eclipse naar de knop **assets > www > wsmobile > js > runtime > views** map.
   * In Visual Studio, navigeer aan **MWSWindows > www > wsmobile > js > runtime > views** map.

   >[!NOTE]
   >
   >Het bestand task.js bevat de backboneweergave die is gekoppeld aan elke taak of elk beginpunt dat in de lijst met taken of beginpunten wordt vermeld.

1. In de `task.js` bestand, zoekt u naar de eigenschap events van de weergave.

   De eigenschap events is een kaart met elke vermelding in de indeling:

   `"EventName Selector": "Function"`

   Wanneer u een JavaScript-gebeurtenis activeert met de naam `EventName`op een HTML-element dat is opgegeven door `Selector`de `Function`wordt aangeroepen.

1. Zoeken

   * &quot;select.taskContentArea&quot; : &quot;onTaskClick&quot;,

     &quot;select.taskOpenArea&quot; : &quot;onTaskClick&quot;,

     &quot;select.task-content&quot; : &quot;onTaskClick&quot;,

     &quot;select.last_empty_div&quot; : &quot;onTaskClick&quot;,

   en vervangen door

   * &quot;vepe.taskContentArea&quot; : &quot;onTaskClick&quot;,

     &quot;vepe.taskOpenArea&quot; : &quot;onTaskClick&quot;,

     &quot;swipe.task-content&quot; : &quot;onTaskClick&quot;,

     &quot;vepe.last_empty_div&quot; : &quot;onTaskClick&quot;,

1. Opslaan en het dialoogvenster sluiten `task.js` bestand.
1. De AEM Forms-app ontwikkelen en uitvoeren. Nu kunt u een toepassing openen met een veegbeweging naar links en een veegbeweging naar rechts.

Op dezelfde manier kunt u ook wijzigingen aanbrengen in andere weergaven voor verschillende combinaties van bewegingen, HTML-elementen en functies.
