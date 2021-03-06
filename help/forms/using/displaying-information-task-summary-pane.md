---
title: Informatie weergeven in het deelvenster Taakoverzicht
seo-title: Informatie weergeven in het deelvenster Taakoverzicht
description: In de werkruimte van AEM Forms, kan een ruit van het Overzicht van de Taak worden gevormd om de taak samen te vatten of een andere Web-pagina te tonen.
seo-description: In de werkruimte van AEM Forms, kan een ruit van het Overzicht van de Taak worden gevormd om de taak samen te vatten of een andere Web-pagina te tonen.
uuid: 2fcc3d9f-0ec2-4250-8dc1-9746fd72ea60
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 90d0f584-b598-4b21-85d7-31da5f13d404
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Informatie weergeven in het venster Taakoverzicht {#displaying-information-in-the-task-summary-pane}

Als u een taak opent in de AEM Forms-werkruimte, wordt in het deelvenster Taakoverzicht een overzicht van de taak weergegeven. Deze aanvullende en relevante informatie voor een taak voegt meer waarde toe aan de eindgebruiker van de AEM Forms-werkruimte.

In de werkruimte van AEM Forms kunt u een webpagina van uw keuze weergeven in het deelvenster Taakoverzicht. Een proces kan worden gecreeerd om een ruit van het Overzicht van de Taak te tonen gebruikend Workbench.

1. Maak een taakproces toewijzen in Workbench. Voor meer details over de verrichting van de Taak toewijzen, zie het onderwerp van de Verwijzing van de Dienst in [Workbench Help](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/).

   >[!NOTE]
   >
   >Als er een TaskSummary-URL bestaat, wordt de weergave Taakoverzicht standaard geopend in plaats van de formulierweergave. In dit geval wordt het formulier niet geopend in de gemaximaliseerde modus, zelfs niet als een gebruiker de optie &quot;Het formulier openen in de gemaximaliseerde modus&quot; in Taak toewijzen inschakelt.

1. Configureer het veld Taakoverzicht-URL. U kunt een letterlijke waarde, een sjabloon, een variabele of een XPath-expressie opgeven.
1. Hieronder ziet u een voorbeeld van het weergeven van de informatie op de pagina Taakoverzicht.

   * Meld u aan bij de CRXDE Lite-omgeving op `https://'[server]:[port]'/lc/crx/de`.
   * `Create a node`**SampleSummary** ` under `/` with type `content:`. In the properties of this node, add `unstructuresling:` of type String and value ``. In the Access Control List of this node, add an entry for `resourceTypeSampleSummaryPERM_WORKSPACE_` allowing `USERjcr:read` privileges.`
   * `Create a folder`**** SampleSummaryunder  `/apps`. In de Lijst van het Toegangsbeheer van `/apps/SampleSummary`, voeg een ingang voor `PERM_WORKSPACE_USER` toe die `jcr:readprivileges` toestaat.
   * `Create a file `html.esp` at `/apps/`. For example, add the following lines in `SampleSummaryhtml.esp`.`

   ```html
   <html>
       <body>
           <h1>Sample Summary</h1>
           <br/>
           <p>Hello Sir!
               <br/>
               This is sample summary page for this task.
           </p>
       </body>
   </html>
   ```

   * Plaats de waarde van taak summiere url als `/lc/content/SampleSummary.html` in de stap van de Taak toewijzen.
   * Wanneer de taak verbonden aan deze Assign stap van de Taak in de werkruimte van AEM Forms wordt geopend, `html.esp` bij `/apps/SampleSummary` wordt teruggegeven in de ruit van het taakoverzicht.
