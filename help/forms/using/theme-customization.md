---
title: Aanpassing thema
description: Leer hoe u het thema van de AEM Forms-toepassing aanpast. U kunt de code van de HTML en CSS dossier aanpassen om organisatie-specifieke blik en mening te verstrekken.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 9b8c5933-b783-48f9-b463-15a01e06ee98
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Aanpassing thema {#theme-customization}

U kunt de HTML-code en het CSS-bestand aanpassen en zo een aparte organisatie-specifieke vormgeving geven voor de AEM Forms-app. U kunt bijvoorbeeld de achtergrondkleur en -hoogte van taken of Startpunten wijzigen. In het volgende voorbeeld worden instructies gegeven om te wijzigen:

* aanwijzingen weergeven in plaats van de beschrijving
* aantal weergaveroutes
* kleur achtergrondverloop

## Stappen {#steps}

1. Open uw project.

   * Voor iOS: open `Capture.xcodeproj` in Xcode
   * Voor Android opent u het Android-project in Eclipse.
   * Voor Windows: open `MWSWindows.sln` in Visual Studio.

1. Navigeer naar de map templates.

   * Navigeer in Xcode naar de **Vastleggen > www > wsmobile > js > runtime > templates** map.
   * Ga in Eclipse naar de knop **assets > www > wsmobile > js > runtime > templates** map.
   * In Visual Studio, navigeer aan **MWSWindows > www > wsmobile > js > runtime > templates** map.

1. Open de `template.html` bestand voor bewerking.
1. Zoek de volgende tekenreeks:

   ```jsp
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else
   ```

   Vervangen door `<%`.

1. Zoek de volgende code in het dialoogvenster `template.html` bestand:

   ```jsp
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Neem een opmerking op in de volgende regel en sla het bestand op.

   ```jsp
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Navigeer naar de css-map.

   * Navigeer in Xcode naar **Vastleggen > www > wsmobile > css**.
   * Blader in Eclipse naar **middelen > www > wsmobile > css**.
   * In Visual Studio, navigeer aan **MWSWindows > www > wsmobile > css**.

1. Open de `_style.css` bestand voor bewerking.
1. Voor achtergrondafbeelding wijzigt u `#323232` tot `#fff`.
1. Wijzigingen opslaan en sluiten `_style.css` bestand.
1. Open de AEM Forms-app.

   De AEM Forms-app geeft nu instructies weer in plaats van een beschrijving.
