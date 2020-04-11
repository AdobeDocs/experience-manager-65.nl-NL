---
title: Afbeeldingen aanpassen die worden gebruikt in routehandelingen
seo-title: Afbeeldingen aanpassen die worden gebruikt in routehandelingen
description: Hoe kan ik-om de afbeeldingen aan te passen die worden gebruikt in routehandelingen in de werkruimte van LiveCycle AEM-formulieren.
seo-description: Hoe kan ik-om de afbeeldingen aan te passen die worden gebruikt in routehandelingen in de werkruimte van LiveCycle AEM-formulieren.
uuid: 42608376-587e-4b57-a9d5-8f9ebd981426
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 10158c13-47b4-43e3-ac47-690f3cbab158
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Afbeeldingen aanpassen die worden gebruikt in routehandelingen {#customize-images-used-in-route-actions}

Als u de afbeeldingen wilt aanpassen die worden gebruikt in routehandelingen, voert u de stappen uit die worden beschreven in [Algemene stappen voor aanpassing](/help/forms/using/generic-steps-html-workspace-customization.md) , gevolgd door de stappen die in dit artikel worden beschreven.

## Afbeeldingen voor routeacties {#images-for-route-actions}

1. Voeg de stijlen die afbeeldingen in de CSS definiëren toe op de volgende locatie voor de nieuwe routeacties:

   `/apps/ws/css/newStyle.css`

   Bijvoorbeeld: Voeg een nieuwe stijl toe die `myStyle1`hieronder wordt weergegeven en upload het afbeeldingsbestand `myStyleIcon1.png` naar de map `/apps/ws/image`s met een WebDAV-client.

   >[!NOTE]
   >
   >Ga voor meer informatie over WebDAV-toegang naar [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

   >[!NOTE]
   >
   >Voorkeur om de stijlnaam te gebruiken om het zelfde als de naam van de routeactie te zijn.

   ```css
   .myStyle1{
   
           background-image: url('../images/myStyleIcon1.png');
   
       }
   ```

## Taaklijstactie pop-up {#task-list-task-action-popup}

1. Maak een pop-up met handelingen voor de takenlijst. Zie [Code](/help/forms/using/introduction-customizing-html-workspace.md#main-pars-heading-3)voor de werkruimte van AEM-formulieren maken. Hiervoor moet het ontwikkelingspakket worden gebruikt.

1. Kopiëren `/libs/ws/js/runtime/templates/task.html` naar `/apps/ws/js/runtime/templates/task.html`.

1. Als de naam van de CSS-stijl gelijk is aan de naam van de routeactie die van de server komt, wijzigt u de volgende code in `/apps/ws/js/runtime/templates/task.html`:

   ```
   <%if(routeList == null){%>
               <li>
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li>
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   
   To
   
   <%if(routeList == null){%>
               <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li class="<%= availableCommands.directCommands[i]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   ```

1. Als de naam van de CSS stijl van de naam van de routeactie die van de server komt verschillend is, wijzig de volgende code binnen `/apps/ws/js/runtime/templates/task.html`. Het voegt een stapel van de `if-else` servlet voorwaarden toe om de stijl met de naam van de routeactie in kaart te brengen.

```
<%if(routeList == null){%>
            <li>
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
            <li>
                <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
            </li>
            <%}%>
            <%}%>

To

<%if(routeList == null){%>
            <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
                <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                     <li class="myStyle1" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                     <li class="myStyle2" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}%>
            <%}%>
            <%}%>
```

## Taakdetails taakactie pop-up {#task-details-task-action-popup}

1. Kopiëren `/libs/ws/js/runtime/templates/taskdetails.html` naar `/apps/ws/js/runtime/templates/taskdetails.html`.

1. Als de naam van de CSS-stijl gelijk is aan de naam van de routeactie die van de server komt, wijzigt u de volgende code in `/apps/ws/js/runtime/templates/taskdetails.html`:

   ```
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                       <%}%>
   ```

1. Als de naam van de CSS stijl van de naam van de routeactie die van de server komt verschillend is, wijzig de volgende code binnen `/apps/ws/js/runtime/templates/taskdetails.html`. Het voegt een stapel van `if-else` servlet voorwaarden toe om de stijl met de naam van de routeactie in kaart te brengen.

   ```
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                   <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle1" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle2" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}%>
               <%}%>
   ```

1. Open `/apps/ws/js/registry.js` voor het uitgeven en zoek de volgende tekst:
   `"text!/lc/libs/ws/js/runtime/templates/taskdetails.html"`

1. Vervang de tekst door:
   `"text!/lc/apps/ws/js/runtime/templates/taskdetails.html"`
