---
title: De pagina met taakdetails aanpassen
description: Hoe te om de pagina van taakdetails in de werkruimte van AEM Forms aan te passen om de standaardinformatie te wijzigen die over een taak wordt getoond.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 48c24442-22d2-4d1a-9462-0aba78340281
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# De pagina met taakdetails aanpassen {#customizing-the-task-details-page}

De pagina met taakdetails bevat informatie over een taak en de bijbehorende processen. U kunt de pagina met taakdetails echter aanpassen om informatie toe te voegen of te verwijderen.

U kunt de volgende informatie toevoegen aan de pagina met taakdetails:

* Informatie beschikbaar in het voorwerp JSON van een taak (de sectie van de Taak in [&#x200B; de werkruimte van AEM Forms JSON de Beschrijving van Objecten &#x200B;](/help/forms/using/html-workspace-json-object-description.md))
* Informatie beschikbaar in het voorwerp JSON van een procesinstantie (de instantiesectie van het Proces in [&#x200B; de werkruimte van AEM Forms JSON de Beschrijving van Objecten &#x200B;](/help/forms/using/html-workspace-json-object-description.md))

De pagina met taakdetails aanpassen:

1. Volg [&#x200B; Algemene stappen voor de werkruimte van AEM Forms aanpassing.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Om om het even welke extra informatie te tonen, voeg overeenkomstige zeer belangrijk-waardeparen aan het `translation.json` dossier bij `todo` blok > `details` blok > `app` blok > [`required` blok ] toe.

   Het [`required` blok ] verwijst naar beschikbare blokken, zoals het taakblok voor taakinformatie, procesblok voor procesinformatie, en het huidige-pendingtask blok voor hangende taakinformatie.

   Bijvoorbeeld, om informatie over de Selectie van de Route toe te voegen Vereist in de pagina van taakdetails, kunt u het volgende zeer belangrijk-waardepaar in het taakblok toevoegen:

   ```json
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >Voeg overeenkomstige sleutel-waardeparen voor alle gesteunde talen toe.

1. Kopieer `/libs/ws/js/runtime/templates/taskdetails.html` naar `/apps/ws/js/runtime/templates/taskdetails.html` .

   Voeg de nieuwe informatie toe aan `/apps/ws/js/runtime/templates/taskdetails.html`. Bijvoorbeeld:

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. Open /apps/ws/js/registry.js voor bewerking.

   Zoek en vervang `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` door `text!/lc/apps/ws/js/runtime/templates/taskdetails.html` .

>[!NOTE]
>
>Om de pagina van taakdetails met taken aan te passen die in het **1&rbrace; lusje van het Proces van het Begin van de werkruimte van AEM Forms worden gecreeerd, voeg de nieuwe informatie aan `/apps/ws/js/runtime/templates/startprocess.html` toe.**
>
>Om nieuwe stijlen voor de informatie toe te voegen die in de detailspagina wordt toegevoegd, wijzig het CSS dossier door de *sectie van de Veranderingen van het gebruikersinterface* in [&#x200B; Aanpassing van Workspace &#x200B;](changing-locale-user-interface.md) te gebruiken.
