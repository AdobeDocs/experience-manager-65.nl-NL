---
title: Trackingtabellen aanpassen
seo-title: Trackingtabellen aanpassen
description: Hoe te om de vertoning van de details van gebruikersprocessen in de taaklijst aan te passen die in het volgende lusje van de werkruimte van AEM Forms wordt getoond.
seo-description: Hoe te om de vertoning van de details van gebruikersprocessen in de taaklijst aan te passen die in het volgende lusje van de werkruimte van AEM Forms wordt getoond.
uuid: 13d6ebf2-99d5-434f-85f9-b0cba5f5751a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: bb7a6e9f-4f28-4d97-8a0c-949259fd6857
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 1%

---


# Trackingtabellen aanpassen{#customize-tracking-tables}

Het volgende lusje in de werkruimte van AEM Forms wordt gebruikt om de details van procesinstanties te tonen waarin de het programma geopende gebruiker betrokken is. Als u de volgende tabellen wilt weergeven, selecteert u eerst een procesnaam in het linkerdeelvenster om de lijst met exemplaren in het middelste venster weer te geven. Selecteer een procesinstantie om een takenlijst te zien die door deze instantie in de juiste ruit wordt geproduceerd. Standaard geven de tabelkolommen de volgende taakkenmerken weer (het bijbehorende kenmerk in het taakmodel staat tussen haakjes):

* ID ( `taskId`)
* Naam ( `stepName`)
* Instructies ( `instructions`)
* Geselecteerde actie ( `selectedRoute`)
* Aanmaaktijd ( `createTime`)
* Voltooiingstijd ( `completeTime`)
* Eigenaar ( `currentAssignment.queueOwner`)

De resterende kenmerken in het taakmodel die beschikbaar zijn voor weergave in de taaktabel zijn:

<table>
 <tbody>
  <tr>
   <td><p>actionInstanceId</p> </td>
   <td><p>isOpenFullScreen</p> </td>
   <td><p>reminderCount</p> </td>
  </tr>
  <tr>
   <td><p>classOfTask</p> </td>
   <td><p>isOwner</p> </td>
   <td><p>routeList</p> </td>
  </tr>
  <tr>
   <td><p>consultGroupId</p> </td>
   <td><p>isRouteSelectionRequired</p> </td>
   <td><p>savedFormCount</p> </td>
  </tr>
  <tr>
   <td><p>contentType</p> </td>
   <td><p>isShowAttachments</p> </td>
   <td><p>serializedImageTicket</p> </td>
  </tr>
  <tr>
   <td><p>createTime</p> </td>
   <td><p>isStartTask</p> </td>
   <td><p>serviceName</p> </td>
  </tr>
  <tr>
   <td><p>creationId</p> </td>
   <td><p>isVisible</p> </td>
   <td><p>serviceTitle</p> </td>
  </tr>
  <tr>
   <td><p>currentAssignment</p> </td>
   <td><p>nextReminder</p> </td>
   <td><p>showACLActions</p> </td>
  </tr>
  <tr>
   <td><p>deadline</p> </td>
   <td><p>numForms</p> </td>
   <td><p>showDirectActions</p> </td>
  </tr>
  <tr>
   <td><p>beschrijving</p> </td>
   <td><p>numFormsToBeSaved</p> </td>
   <td><p>status</p> </td>
  </tr>
  <tr>
   <td><p>displayName</p> </td>
   <td><p>outOfOfficeUserId</p> </td>
   <td><p>summaryUrl</p> </td>
  </tr>
  <tr>
   <td><p>forwardGroupId</p> </td>
   <td><p>outOfOfficeUserName</p> </td>
   <td><p>supportsSave</p> </td>
  </tr>
  <tr>
   <td><p>isApprovalUI</p> </td>
   <td><p>priority</p> </td>
   <td><p>taskACL</p> </td>
  </tr>
  <tr>
   <td><p>isCustomUI</p> </td>
   <td><p>processInstanceId</p> </td>
   <td><p>taskFormType</p> </td>
  </tr>
  <tr>
   <td><p>isDefaultImage</p> </td>
   <td><p>processInstanceStatus</p> </td>
   <td><p>taskUserInfo</p> </td>
  </tr>
  <tr>
   <td><p>isLocked</p> </td>
   <td><p>processVariables</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p>isMustOpenToComplete</p> </td>
   <td><p>readerSubmitOptions</p> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Voor de volgende aanpassingen in de takenlijst, moet u semantische veranderingen in de broncode doen. Zie [Inleiding tot het Aanpassen van de werkruimte](/help/forms/using/introduction-customizing-html-workspace.md) van AEM Forms voor hoe u semantische veranderingen kunt aanbrengen gebruikend werkruimte SDK en een geminificeerde pakket van de veranderde bron bouwen.

## Tabelkolommen en hun volgorde wijzigen {#changing-table-columns-and-their-order}

1. Om de taakattributen te wijzigen die in de lijst en hun orde worden getoond, vorm het dossier /ws/js/runtime/templates/processinstancehistory.html:

   ```html
   <table>
       <thead>
           <tr>
               <!-- put the column headings in order here, for example-->
               <th><%= $.t('history.fixedTaskTableHeader.taskName')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskInstructions')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskRoute')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskCreateTime')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskCompleteTime')%></th>
           </tr>
       </thead>
   </table>
   ```

   ```html
   <table>
       <tbody>
           <%_.each(obj, function(task){%>
           <tr>
               <!-- Put the task attributes in the order of headings, for example -->
               <td><%= task.stepName %></td>
               <td><%= task.instructions %></td>
               <td><%= !task.selectedRoute?'':(task.selectedRoute=='null'?'Default':task.selectedRoute) %></td>
               <td><%= task.createTime?task.formattedCreateTime:'' %></td>
               <td><%= task.completeTime? task.formattedCompleteTime:'' %></td>
           </tr>
           <%});%>
       </tbody>
   </table>
   ```

## Een tabel bijhouden sorteren {#sorting-a-tracking-table}

U kunt als volgt de tabel met de takenlijst sorteren wanneer u op de kolomkop klikt:

1. Registreer een klikmanager voor `.fixedTaskTableHeader th` in het dossier `js/runtime/views/processinstancehistory.js`.

   ```javascript
   events: {
       //other handlers
       "click .fixedTaskTableHeader th": "onTaskTableHeaderClick",
       //other handlers
   }
   ```

   Roep in de handler de `onTaskTableHeaderClick` functie van `js/runtime/util/history.js`.

   ```javascript
   onTaskTableHeaderClick: function (event) {
           history.onTaskTableHeaderClick(event);
   }
   ```

1. Maak de `TaskTableHeaderClick` methode beschikbaar in `js/runtime/util/history.js`.

   De methode zoekt het taakkenmerk van de gebeurtenis click, sorteert de taaklijst van dat kenmerk en geeft de taaktabel weer met de gesorteerde taaklijst.

   Sorteren gebeurt met behulp van de Backbone-sorteerfunctie in de taaklijstverzameling door een vergelijkingsfunctie op te geven.

   ```javascript
       return {
           //other methods
           onTaskTableHeaderClick  : onTaskTableHeaderClick,
           //other methods
       };
   ```

   ```javascript
   onTaskTableHeaderClick = function (event) {
           var target = $(event.target),
            comparator,
               attribute;
           if(target.hasClass('taskName')){
            attribute = 'stepName';
           } else if(target.hasClass('taskInstructions')){
               attribute = 'instructions';
           } else if(target.hasClass('taskRoute')){
               attribute = 'selectedRoute';
           } else if(target.hasClass('taskCreateTime')){
               attribute = 'createTime';
           } else if(target.hasClass('taskCompleteTime')){
               attribute = 'completeTime';
           }
           taskList.comparator = function (task) {
            return task.get(attribute);
           };
           taskList.sort();
           render();
       };
   ```
