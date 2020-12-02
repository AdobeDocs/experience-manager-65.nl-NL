---
title: De pagina met taakdetails aanpassen
seo-title: De pagina met taakdetails aanpassen
description: Hoe te om de pagina van taakdetails in de werkruimte van AEM Forms aan te passen om de standaardinformatie te wijzigen die over een taak wordt getoond.
seo-description: Hoe te om de pagina van taakdetails in de werkruimte van AEM Forms aan te passen om de standaardinformatie te wijzigen die over een taak wordt getoond.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# De pagina {#customizing-the-task-details-page} met taakdetails aanpassen

De pagina met taakdetails bevat informatie over een taak en de bijbehorende processen. U kunt de pagina met taakdetails echter aanpassen om informatie toe te voegen of te verwijderen.

U kunt de volgende informatie toevoegen aan de pagina met taakdetails:

* Informatie beschikbaar in het JSON-object van een taak (taaksectie in [AEM Forms-werkruimte JSON-objectbeschrijving](/help/forms/using/html-workspace-json-object-description.md))
* Informatie beschikbaar in het JSON-object van een procesinstantie (sectie Procesinstantie in [AEM Forms-werkruimte JSON-objectbeschrijving](/help/forms/using/html-workspace-json-object-description.md))

De pagina met taakdetails aanpassen:

1. Voer [Algemene stappen uit voor aanpassing van de AEM Forms-werkruimte.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Als u aanvullende informatie wilt weergeven, voegt u corresponderende sleutel-waardeparen toe aan het `translation.json`-bestand op `todo`block > `details`block > `app`block > [ `required`block].

   [ `required`block] verwijst naar beschikbare blokken, zoals het taakblok voor taakinformatie, procesblok voor procesinformatie, en het huidige-pendingtask blok voor lopende taakinformatie.

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
   >Voeg overeenkomstige sleutel-waarde paren voor alle gesteunde talen toe.

1. Kopieer `/libs/ws/js/runtime/templates/taskdetails.html` naar `/apps/ws/js/runtime/templates/taskdetails.html`.

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

   `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` doorzoeken en vervangen door `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Als u de pagina met taakdetails wilt aanpassen met taken die zijn gemaakt op het tabblad **Proces starten** van de AEM Forms-werkruimte, voegt u de nieuwe informatie toe aan `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Als u nieuwe stijlen wilt toevoegen voor de informatie die op de detailpagina is toegevoegd, wijzigt u het CSS-bestand met de sectie *Wijzigingen in de gebruikersinterface* in [Aanpassing werkruimte](changing-locale-user-interface.md).
