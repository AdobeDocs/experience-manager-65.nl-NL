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

   * Voor iOS opent u `Capture.xcodeproj` in Xcode
   * Voor Android opent u het Android-project in Eclipse.
   * Voor Vensters, open `MWSWindows.sln` in Visual Studio.

1. Navigeer naar de map views en open het bestand `task.js` voor bewerking.

   * In Xcode, navigeer aan **Vangst > www > wsmobile > js > runtime > meningen** omslag.
   * In Verduistering, navigeer aan de **activa > www > wsmobile > js > runtime > meningen** omslag.
   * In Visual Studio, navigeer aan **MWSWindows > www > wsmobile > js > runtime > meningen** omslag.

   >[!NOTE]
   >
   >Het bestand task.js bevat de backboneweergave die is gekoppeld aan elke taak of elk beginpunt dat in de lijst met taken of beginpunten wordt vermeld.

1. Zoek in het bestand `task.js` naar de eigenschap events van de weergave.

   De eigenschap events is een kaart met elke vermelding in de indeling:

   `"EventName Selector": "Function"`

   Wanneer u een gebeurtenis van JavaScript genoemd `EventName` op een element activeert van de HTML dat door `Selector` wordt gespecificeerd, wordt `Function` geroepen.

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

1. Sla het `task.js` -bestand op en sluit het.
1. De AEM Forms-app ontwikkelen en uitvoeren. Nu kunt u een toepassing openen met een veegbeweging naar links en een veegbeweging naar rechts.

Op dezelfde manier kunt u ook wijzigingen aanbrengen in andere weergaven voor verschillende combinaties van bewegingen, HTML-elementen en functies.
