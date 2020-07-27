---
title: Aanpassing thema
seo-title: Aanpassing thema
description: Het thema van uw app voor AEM Forms aanpassen.
seo-description: Het thema van uw app voor AEM Forms aanpassen.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Aanpassing thema {#theme-customization}

U kunt de HTML-code en het CSS-bestand aanpassen en zo een duidelijk organisatiespecifiek uiterlijk geven aan de AEM Forms-app. U kunt bijvoorbeeld de achtergrondkleur en -hoogte van taken of Startpunten wijzigen. In het volgende voorbeeld worden instructies gegeven om te wijzigen:

* aanwijzingen weergeven in plaats van de beschrijving
* aantal weergaveroutes
* kleur achtergrondverloop

## Stappen {#steps}

1. Open uw project.

   * Voor iOS openen `Capture.xcodeproj` in Xcode
   * Voor Android opent u het Android-project in Eclipse.
   * Voor Vensters, open `MWSWindows.sln` in Visual Studio.

1. Navigeer naar de map templates.

   * Navigeer in Xcode naar de map **Vastleggen > www > wsmobile > js > runtime > templates** .
   * Navigeer in Eclipse naar de map **Assets > www > wsmobile > js > runtime > templates** .
   * Navigeer in Visual Studio naar de map **MWSWindows > www > wsmobile > js > runtime > templates** .

1. Open het `template.html` bestand om het te bewerken.
1. Zoek de volgende tekenreeks:

   ```jsp
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else
   ```

   Vervang het door `<%`.

1. Zoek de volgende code in het `template.html` bestand:

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
   * Navigeer in Eclipse naar **elementen > www > wsmobile > css**.
   * Navigeer in Visual Studio naar **MWSWindows > www > wsmobile > css**.

1. Open het `_style.css` bestand om het te bewerken.
1. Wijzig `#323232` de optie Achtergrondafbeelding in `#fff`.
1. Sla de wijzigingen op en sluit het `_style.css` bestand.
1. Open de app AEM Forms.

   In de app AEM Forms worden nu instructies weergegeven in plaats van een beschrijving.
