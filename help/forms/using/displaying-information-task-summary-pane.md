---
title: Informatie weergeven in het deelvenster Taakoverzicht
description: In de werkruimte van AEM Forms, kan een ruit van het Overzicht van de Taak worden gevormd om de taak samen te vatten of een andere Web-pagina te tonen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 0b3087fe-a3fb-4eac-ad4b-c123526e8195
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Informatie weergeven in het deelvenster Taakoverzicht {#displaying-information-in-the-task-summary-pane}

Als u een taak opent in de AEM Forms-werkruimte, wordt in het deelvenster Taakoverzicht een overzicht van de taak weergegeven. Deze aanvullende en relevante informatie voor een taak voegt meer waarde toe aan de eindgebruiker van de AEM Forms-werkruimte.

In de werkruimte van AEM Forms kunt u een webpagina van uw keuze weergeven in het deelvenster Taakoverzicht. Een proces kan worden gecreeerd om een ruit van het Overzicht van de Taak te tonen gebruikend Workbench.

1. Creeer een Assign proces van de Taak in Workbench. Voor meer details over de verrichting van de Taak toewijzen, zie het onderwerp van de Verwijzing van de Dienst in [Workbench Help](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/).

   >[!NOTE]
   >
   >Als er een TaskSummary-URL bestaat, wordt de weergave Taakoverzicht standaard geopend in plaats van de formulierweergave. In dit geval wordt het formulier niet geopend in de gemaximaliseerde modus, zelfs niet als een gebruiker de optie &quot;Het formulier openen in de gemaximaliseerde modus&quot; in Taak toewijzen inschakelt.

1. Configureer het veld Taakoverzicht-URL. U kunt een letterlijke waarde, een sjabloon, een variabele of een XPath-expressie opgeven.
1. Hieronder ziet u een voorbeeld van het weergeven van de informatie op de pagina Taakoverzicht.

   * Aanmelden bij CRXDE Lite-omgeving bij `https://'[server]:[port]'/lc/crx/de`.
   * `Create a node`**SampleSummary** ` under `/content` with type `nt:ongestructureerd`. In the properties of this node, add `sling:resourceType` of type String and value `SampleSummary`. In the Access Control List of this node, add an entry for `PERM_WORKSPACE_USER` allowing `jcr:lezen` privileges.`
   * `Create a folder`**SampleSummary** krachtens `/apps`. In de lijst Toegangsbeheer van `/apps/SampleSummary`, een item toevoegen voor `PERM_WORKSPACE_USER` toestaan `jcr:readprivileges`.
   * `Create a file `html.esp` at `/apps/SampleSummary`. For example, add the following lines in `html.esp`.`

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

   * Stel de waarde van de taaksummiere URL in op `/lc/content/SampleSummary.html` in Taak toewijzen.
   * Wanneer de taak die bij deze stap Taak toewijzen hoort, wordt geopend in de AEM Forms-werkruimte, wordt `html.esp` om `/apps/SampleSummary` wordt weergegeven in het taakoverzichtsvenster.
