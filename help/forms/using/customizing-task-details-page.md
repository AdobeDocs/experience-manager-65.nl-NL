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

* Informatie beschikbaar in het JSON-object van een taak (taaksectie in [JSON-objectbeschrijving in de AEM Forms-werkruimte](/help/forms/using/html-workspace-json-object-description.md))
* Informatie beschikbaar in het JSON-object van een procesinstantie (sectie Procesinstantie in [JSON-objectbeschrijving in de AEM Forms-werkruimte](/help/forms/using/html-workspace-json-object-description.md))

De pagina met taakdetails aanpassen:

1. Volgen [Algemene stappen voor aanpassing van de AEM Forms-werkruimte.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Als u aanvullende informatie wilt weergeven, voegt u de corresponderende sleutel-waardeparen toe aan de `translation.json` bestand bij `todo`blok > `details`blok > `app`blok > [`required`blok].

   De [`required`blok] verwijst naar beschikbare blokken, zoals het taakblok voor taakinformatie, procesblok voor procesinformatie, en het huidige het taakblok voor lopende taakinformatie.

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

1. Kopiëren `/libs/ws/js/runtime/templates/taskdetails.html` tot `/apps/ws/js/runtime/templates/taskdetails.html`.

   Nieuwe informatie toevoegen aan `/apps/ws/js/runtime/templates/taskdetails.html`. Bijvoorbeeld:

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

   Zoeken en vervangen `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` with `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Als u de pagina met taakdetails wilt aanpassen met taken die zijn gemaakt in het dialoogvenster **Proces starten** tabblad van de AEM Forms-werkruimte, voegt u de nieuwe informatie toe aan `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Als u nieuwe stijlen wilt toevoegen voor de informatie die op de detailpagina is toegevoegd, wijzigt u het CSS-bestand met de opdracht *Wijzigingen in gebruikersinterface* sectie in [Aanpassing werkruimte](changing-locale-user-interface.md).
