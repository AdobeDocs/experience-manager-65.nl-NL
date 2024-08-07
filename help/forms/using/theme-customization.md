---
title: Aanpassing thema
description: Leer hoe u het thema van de AEM Forms-toepassing aanpast. U kunt de code van de HTML en CSS dossier aanpassen om organisatie-specifieke blik en mening te verstrekken.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 9b8c5933-b783-48f9-b463-15a01e06ee98
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
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

   * Voor iOS opent u `Capture.xcodeproj` in Xcode
   * Voor Android opent u het Android-project in Eclipse.
   * Voor Vensters, open `MWSWindows.sln` in Visual Studio.

1. Navigeer naar de map templates.

   * In Xcode, navigeer aan **Vangst > www > wsmobile > js > runtime > malplaatjes** omslag.
   * In Verduistering, navigeer aan de **activa > www > wsmobile > js > runtime > malplaatjes** omslag.
   * In Visual Studio, navigeer aan **MWSWindows > www > wsmobile > js > runtime > malplaatjes** omslag.

1. Open het `template.html` -bestand om het te bewerken.
1. Zoek de volgende tekenreeks:

   ```jsp
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else
   ```

   Vervang deze door `<%` .

1. Zoek de volgende code in het `template.html` -bestand:

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

   * In Xcode, navigeer aan **Vangst > www > wsmobile > css**.
   * In Verduistering, navigeer aan **activa > www > wsmobile > css**.
   * In Visual Studio, navigeer aan **MWSWindows > www > wsmobile > css**.

1. Open het `_style.css` -bestand om het te bewerken.
1. Wijzig `#323232` in `#fff` voor de achtergrondafbeelding.
1. Sla de wijzigingen op en sluit het `_style.css` -bestand.
1. Open de AEM Forms-app.

   De AEM Forms-app geeft nu instructies weer in plaats van een beschrijving.
