---
title: De lijst met procesinstanties aanpassen
description: Hoe kan ik-eigenschappen aanpassen die in procesinstantie in de AEM Forms-werkruimte worden weergegeven.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b27ffe92-8491-43a0-bf42-613eb39a606e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# De lijst met procesinstanties aanpassen {#customizing-the-listing-of-process-instances}

De lijst met procesinstanties wordt weergegeven op het tabblad Tekstspatiëring van de AEM Forms-werkruimte.

In de lijst van procesinstanties, voor elke procesinstantie, toont de werkruimte van AEM Forms sommige eigenschappen van die instantie. De volgende eigenschappen zijn beschikbaar voor elke procesinstantie. Deze eigenschappen worden opgeslagen als attributen in het model van de procesinstantiecomponent en zijn beschikbaar voor gebruik in zijn mening en malplaatje.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>beschrijving</td>
   <td>Beschrijving van de procesinstantie.</td>
  </tr>
  <tr>
   <td>initiator</td>
   <td>Naam van initiator van de procesinstantie.</td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>Id van de initiator van de procesinstantie.</td>
  </tr>
  <tr>
   <td>processCompleteTime</td>
   <td>Tijdstempel wanneer het proces is voltooid.</td>
  </tr>
  <tr>
   <td>processInstanceId</td>
   <td>Id van de procesinstantie.</td>
  </tr>
  <tr>
   <td>processInstanceStatus</td>
   <td>0 = geïnitieerd<br /> 1 = Uitvoeren<br /> 2 = voltooid<br /> 3 = Voltooien<br /> 4 = beëindigd<br /> 5 = Beëindiging<br /> 6 = Opgeschort<br /> 7 = opschorting<br /> 8 = Ononderbroken</td>
  </tr>
  <tr>
   <td>processName</td>
   <td>Naam van het proces.</td>
  </tr>
  <tr>
   <td>processStartTime</td>
   <td>Tijdstempel wanneer het proces is gestart.</td>
  </tr>
  <tr>
   <td>processVariables</td>
   <td>Array van objecten met procesvariabelen. Elk procesvariabeleobject bevat <strong>name</strong> (naam van procesvariabele), <strong>value</strong> (waarde van de procesvariabele), en<strong> type</strong> (het type procesvariabele).</td>
  </tr>
 </tbody>
</table>

**Voorbeeld:**

Als u het dialoogvenster `description` eigenschap van de procesinstantie in de procesinstantiekaart, voert de volgende stappen uit.

1. Volg de [Algemene stappen voor aanpassing van de AEM Forms-werkruimte](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Ga als volgt te werk:

   1. Kopieer /libs/ws/js/runtime/templates/processinstance.html naar/apps/ws/js/runtime/templates/, als deze niet bestaat. Klikken **Alles opslaan**.
   1. Voeg procesbeschrijvingsdiv toe met klasse = &#39;processDescription&#39; inprocessinstance.html.

   ```jsp
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. Ga als volgt te werk:

   1. Open /apps/ws/js/registry.js voor bewerking.
   1. Zoeken en vervangen `text!/lc/libs/ws/js/runtime/templates/processinstance.html`with `text!/lc/`**apps**/ws/js/runtime/templates/processinstance.html.

1. Voor de bovenstaande wijzigingen is mogelijk een update van het CSS-bestand nodig door op de volgende manier een vermelding toe te voegen in de stijlpagina /apps/ws/css/newStyle.css:

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement and user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
