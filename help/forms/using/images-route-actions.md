---
title: Afbeeldingen aanpassen die worden gebruikt in routehandelingen
description: Hoe-om de beelden aan te passen die in routeacties in de werkruimte van AEM Forms van het LiveCycle worden gebruikt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 687c6569-7189-4039-9c7a-bc29658a7756
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Afbeeldingen aanpassen die worden gebruikt in routehandelingen {#customize-images-used-in-route-actions}

Om de beelden aan te passen die in routeacties worden gebruikt, voer de stappen uit die in [ worden beschreven Algemene Stappen van aanpassing ](/help/forms/using/generic-steps-html-workspace-customization.md) door de stappen worden gevolgd die in dit artikel worden beschreven.

## Afbeeldingen voor routeacties {#images-for-route-actions}

1. Voeg de stijlen die afbeeldingen in de CSS definiëren toe op de volgende locatie voor de nieuwe routeacties:

   `/apps/ws/css/newStyle.css`

   Bijvoorbeeld: voeg een nieuwe stijl toe genoemd `myStyle1` zoals hieronder getoond en upload het beelddossier `myStyleIcon1.png` aan de `/apps/ws/image` omslag gebruikend een cliënt WebDAV.

   >[!NOTE]
   >
   >Voor meer informatie, zie [ Toegang WebDAV ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=nl-NL).

   >[!NOTE]
   >
   >Voorkeur om de stijlnaam te gebruiken om de naam van de routeactie te zijn.

   ```css
   .myStyle1{
   
           background-image: url('../images/myStyleIcon1.png');
   
       }
   ```

## Taaklijstactie pop-up {#task-list-task-action-popup}

1. Creeer pop-up de actie van de taaklijst, zie [ de werkruimtecode van AEM Forms bouwen ](introduction-customizing-html-workspace.md#building-html-workspace-code). Hiervoor moet het ontwikkelingspakket worden gebruikt.

1. Kopieer `/libs/ws/js/runtime/templates/task.html` naar `/apps/ws/js/runtime/templates/task.html` .

1. Als de naam van de CSS-stijl gelijk is aan de naam van de routeactie die van de server komt, wijzigt u de volgende code in `/apps/ws/js/runtime/templates/task.html` :

   ```jsp
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

1. Als de naam van de CSS-stijl afwijkt van de naam van de routeactie die van de server komt, wijzigt u de volgende code in `/apps/ws/js/runtime/templates/task.html` . Er wordt een stapel toegevoegd van de servervoorwaarden van `if-else` om de stijl toe te wijzen aan de naam van de routeactie.

```jsp
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

1. Kopieer `/libs/ws/js/runtime/templates/taskdetails.html` naar `/apps/ws/js/runtime/templates/taskdetails.html` .

1. Als de naam van de CSS-stijl gelijk is aan de naam van de routeactie die van de server komt, wijzigt u de volgende code in `/apps/ws/js/runtime/templates/taskdetails.html` :

   ```jsp
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

1. Als de naam van de CSS-stijl afwijkt van de naam van de routeactie die van de server komt, wijzigt u de volgende code in `/apps/ws/js/runtime/templates/taskdetails.html` . Er wordt een stapel met `if-else` servlet-voorwaarden toegevoegd om de stijl toe te wijzen aan de naam van de routeactie.

   ```jsp
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

1. Open `/apps/ws/js/registry.js` voor bewerking en zoek naar de volgende tekst:
   `"text!/lc/libs/ws/js/runtime/templates/taskdetails.html"`

1. Vervang de tekst door:
   `"text!/lc/apps/ws/js/runtime/templates/taskdetails.html"`
