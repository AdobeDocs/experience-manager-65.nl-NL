---
title: API's die worden gebruikt in de AEM Forms-werkruimte
description: Publieke Java&trade en JavaScript API's en methoden van de werkruimte van AEM Forms van het LiveCycle, beschikbaar voor aanpassing en automatisering.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 9034f73a-83f3-498e-b6a6-ad6577aa1a3a
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 0%

---

# API&#39;s die worden gebruikt in de AEM Forms-werkruimte {#apis-used-in-aem-forms-workspace}

De volgende API&#39;s worden gebruikt in de AEM Forms-werkruimte.

<table>
 <tbody>
  <tr>
   <td><strong>JavaScript-methode</strong></td>
   <td><strong>Servicenaam</strong></td>
   <td><strong>API-naam</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>getgroups</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getgroups</td>
   <td>Hiermee zoekt u groepen. er wordt een lijst geretourneerd van alle groepen als er niets is opgegeven. Anders worden groepen met de opgegeven naam geretourneerd.</td>
  </tr>
  <tr>
   <td>getUsersAndgroups</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersAndgroups</td>
   <td>Hiermee doorzoekt u gebruikers en groepen. Het keert een lijst van alle gebruikers en groepen terug als niets specificeerde, anders gebruikers en groepen met gespecificeerde naam terugkeert.</td>
  </tr>
  <tr>
   <td>prepareForSubmit</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>prepareForSubmit</td>
   <td>Deze wordt aangeroepen voordat een formulier wordt verzonden via DocumentSubmitServlet. De taak-id wordt ingesteld in een sessievariabele (samen met een verlooptijd) die tijdens de eigenlijke verzending wordt opgehaald.</td>
  </tr>
  <tr>
   <td>submitTask</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>indienen</td>
   <td>Het verzendt het documentvoorwerp verbonden aan een taak (en verzendt beurtelings proces).</td>
  </tr>
  <tr>
   <td>getRootEndpointCategories</td>
   <td>ProcessManagementStartService</td>
   <td>getRootEndpointCategories</td>
   <td>Hiermee worden alle hoofdcategorieën opgehaald die aanwezig zijn op de server.</td>
  </tr>
  <tr>
   <td>getDirectChildCategories</td>
   <td>ProcessManagementStartService</td>
   <td>getDirectChildCategories2</td>
   <td>Het haalt alle directe kinderen voor een categorie.</td>
  </tr>
  <tr>
   <td>getAllStartpoints</td>
   <td>ProcessManagementStartService</td>
   <td>getAllStartpoints</td>
   <td>Hiermee worden alle startpunten opgehaald die onder alle categorieën op de server aanwezig zijn.</td>
  </tr>
  <tr>
   <td>invokeStartpoint</td>
   <td>ProcessManagementStartService</td>
   <td>invokeStartpoint</td>
   <td>Dit roept een Startpunt aan en leidt tot een taak die aan een startpunt beantwoordt</td>
  </tr>
  <tr>
   <td>getAllTasks</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableTasks</td>
   <td>Het haalt alle taken die worden gecreeerd en door:sturen of geraadpleegd, opgeslagen, toegewezen, toegewezen, en bewaard voor de het programma geopende gebruiker.</td>
  </tr>
  <tr>
   <td>getTask</td>
   <td>ProcessManagementTaskService</td>
   <td>getTask</td>
   <td>Het haalt een specifieke taak op.</td>
  </tr>
  <tr>
   <td>renderTask</td>
   <td>ProcessManagementTaskService</td>
   <td>renderen</td>
   <td>Er wordt een taak gegenereerd en er wordt informatie geretourneerd die nodig is om het formulier weer te geven, zoals formulier-URL, formuliertype, gegevens-URL, indien nodig.</td>
  </tr>
  <tr>
   <td>submitWithBeforeData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithBeforeData</td>
   <td>Het keert het resultaat van TaskManager toe:zenden API gebruikend de resultaatsleutel.</td>
  </tr>
  <tr>
   <td>submitWithData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithData</td>
   <td>De formuliergegevens (doorgegeven als tekenreeks) die aan de taak zijn gekoppeld, worden met de verzendAPI van TaskManager verzonden. Deze wordt gebruikt voor Flex-formulieren die de verzend-API van TaskManager niet aanroepen.</td>
  </tr>
  <tr>
   <td>opslaan</td>
   <td>ProcessManagementTaskService</td>
   <td>opslaan</td>
   <td>Er wordt een taak opgeslagen op de server.</td>
  </tr>
  <tr>
   <td>complete</td>
   <td>ProcessManagementTaskService</td>
   <td>complete</td>
   <td>Het voltooit een taak en de taak wordt overgegaan tot de volgende stap volgens procesontwerp.</td>
  </tr>
  <tr>
   <td>getAttachment</td>
   <td>ProcessManagementTaskService</td>
   <td>getAttachment</td>
   <td>Er wordt een URL van een bijlage geretourneerd waar de bijlage beschikbaar is.</td>
  </tr>
  <tr>
   <td>getAllAttachments</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableAttachments</td>
   <td>Alle bijlagen en notities worden opgehaald voor een taak.</td>
  </tr>
  <tr>
   <td>delen</td>
   <td>ProcessManagementTaskService</td>
   <td>delen</td>
   <td>Het deelt een taak met een andere gebruiker. Een andere gebruiker kan de taak opeisen en wordt eigenaar van de taak.</td>
  </tr>
  <tr>
   <td>doorsturen</td>
   <td>ProcessManagementTaskService</td>
   <td>doorsturen</td>
   <td>Een taak wordt doorgestuurd naar een andere gebruiker.</td>
  </tr>
  <tr>
   <td>consulteren</td>
   <td>ProcessManagementTaskService</td>
   <td>consulteren</td>
   <td>Het raadpleegt een taak met een andere gebruiker.</td>
  </tr>
  <tr>
   <td>vordering</td>
   <td>ProcessManagementTaskService</td>
   <td>vordering</td>
   <td>Het beweert een taak die in een gedeelde rij beschikbaar is.</td>
  </tr>
  <tr>
   <td>ontgrendelen</td>
   <td>ProcessManagementTaskService</td>
   <td>ontgrendelen</td>
   <td>Het ontgrendelt een taak.</td>
  </tr>
  <tr>
   <td>vergrendelen</td>
   <td>ProcessManagementTaskService</td>
   <td>vergrendelen</td>
   <td>Het vergrendelt een taak en de taak kan niet worden opgeëist door een andere gebruiker als deze wordt gedeeld.</td>
  </tr>
  <tr>
   <td>afwijzen</td>
   <td>ProcessManagementTaskService</td>
   <td>afwijzen</td>
   <td>Het keert een taak aan de vorige eigenaar van de taak terug.</td>
  </tr>
  <tr>
   <td>opgeven</td>
   <td>ProcessManagementTaskService</td>
   <td>opgeven</td>
   <td>Er wordt een taak verwijderd.</td>
  </tr>
  <tr>
   <td>setVisibility</td>
   <td>ProcessManagementTaskService</td>
   <td>setVisibility</td>
   <td>Het plaatst zicht van een taak. Als de zichtbaarheid is ingesteld op false, is de taak achteraf niet zichtbaar voor de gebruiker.</td>
  </tr>
  <tr>
   <td>getUsers</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsers</td>
   <td>Het wordt gebruikt voor het zoeken van gebruikers. Hiermee worden alle gebruikers geretourneerd als er geen naam is opgegeven of als gebruikers met een opgegeven naam worden geretourneerd.</td>
  </tr>
  <tr>
   <td>getUsersInGroup</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersInGroupByName</td>
   <td>Alle gebruikers in een groep worden geretourneerd.</td>
  </tr>
  <tr>
   <td>GrantQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>GrantQueueAccess</td>
   <td>Het verleent toegang van de het programma geopende rij van de gebruiker aan een gespecificeerde gebruiker. Het is eigenlijk het delen van je eigen wachtrij met een andere gebruiker.</td>
  </tr>
  <tr>
   <td>requestQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>requestQueueAccess</td>
   <td>Het maakt het toegangsverzoek van een rij van een gespecificeerde gebruiker voor de het programma geopende gebruiker. Als de gebruiker het verzoek goedkeurt, wordt de rij van de gebruiker gedeeld met het programma geopende gebruiker.</td>
  </tr>
  <tr>
   <td>getGrantedUsers</td>
   <td>ProcessManagementQueueService</td>
   <td>getGrantedUsers</td>
   <td>Het keert alle gebruikers terug die toegang tot de rij van de het programma geopende gebruiker hebben.</td>
  </tr>
  <tr>
   <td>getUsersForAccessibleQueues</td>
   <td>ProcessManagementQueueService</td>
   <td>getUsersForAccessibleQueues</td>
   <td>Hiermee worden alle gebruikers geretourneerd waarvan de wachtrij toegankelijk is voor een gebruiker.</td>
  </tr>
  <tr>
   <td>revokeQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>revokeQueueAccess</td>
   <td>Het verwijdert een gebruiker uit de lijst van gebruikers die toegang tot de rij van de het programma geopende gebruiker hebben.</td>
  </tr>
  <tr>
   <td>removeQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>removeQueueAccess</td>
   <td>Het verwijdert een gebruiker uit de lijst van gebruikers de waarvan rij voor de het programma geopende gebruiker toegankelijk is.</td>
  </tr>
  <tr>
   <td>getAllQueues<br /> </td>
   <td>ProcessManagementQueueService<br /> </td>
   <td>getAllQueues<br /> </td>
   <td>Het krijgt alle rijen (eigen, gedeelde, en groepsrijen) toegankelijk voor de het programma geopende gebruiker.<br /> </td>
  </tr>
  <tr>
   <td>getOutOfOfficeSettings</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>getOutOfOfficeSettings</td>
   <td>Het krijgt de montages van buiten-van-bureau van een gebruiker.</td>
  </tr>
  <tr>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>Het bewaart de uit-van-bureaumontages van een gebruiker.</td>
  </tr>
  <tr>
   <td>getAllProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getAllProcesses</td>
   <td>Het keert een lijst van alle processen terug.</td>
  </tr>
  <tr>
   <td>getParticipatedProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getParticipatedProcesses</td>
   <td>Het keert een lijst van alle procesnamen terug die door de het programma geopende gebruiker worden deelgenomen.</td>
  </tr>
  <tr>
   <td>getProcessInstance<br /> </td>
   <td>ProcessManagementProcessService<br /> </td>
   <td>getProcessInstance<br /> </td>
   <td>Er worden details van een procesinstantie opgehaald.<br /> </td>
  </tr>
  <tr>
   <td>getProcessInstances</td>
   <td>ProcessManagementQueryService</td>
   <td>getProcessInstances</td>
   <td>Hiermee worden alle procesinstanties voor een proces opgehaald.</td>
  </tr>
  <tr>
   <td>getPendingTasksForProcessInstance</td>
   <td>ProcessManagementQueryService</td>
   <td>getPendingTasksForProcessInstance</td>
   <td>Er worden taken in behandeling voor een procesinstantie.</td>
  </tr>
  <tr>
   <td>getTasksForProcessInstance</td>
   <td>ProcessManagementQueryService</td>
   <td>getTasksForProcessInstance</td>
   <td>Het krijgt alle taken voor een procesinstantie.</td>
  </tr>
  <tr>
   <td>getAllSearchTemplates</td>
   <td>ProcessManagementQueryService</td>
   <td>getAllSearchTemplates</td>
   <td>Er wordt een lijst met alle zoeksjablonen geretourneerd.</td>
  </tr>
  <tr>
   <td>getTemplate</td>
   <td>ProcessManagementQueryService</td>
   <td>getTemplate</td>
   <td>Inhoud wordt geretourneerd voor een zoeksjabloon.</td>
  </tr>
  <tr>
   <td>findTasksJson<br /> </td>
   <td>ProcessManagementQueryService</td>
   <td>findTasksJson</td>
   <td>Het zoekt en keert alle taken terug die aan alle voorwaarden van een onderzoeksmalplaatje voldoen.</td>
  </tr>
  <tr>
   <td>getAssignmentForTask</td>
   <td>ProcessManagementTaskService</td>
   <td>getAssignmentForTask</td>
   <td>Het krijgt alle taken voor een taak. Als een gebruiker bijvoorbeeld een taak doorstuurt of consulteert met een andere gebruiker, is dit een toewijzing voor een taak.</td>
  </tr>
  <tr>
   <td>deleteAttachment </td>
   <td>TaskManagerService</td>
   <td>deleteAttachment</td>
   <td>Hiermee wordt een bijlage verwijderd.</td>
  </tr>
  <tr>
   <td>initialiseren</td>
   <td>ProcessManagementClientSessionService</td>
   <td>initialiseren</td>
   <td>Zo nodig wordt de bewering verlengd. Hiermee wordt de gebruiker geverifieerd. Stelt sessieparameters in voor server-/clientinformatie. Retourneert gebruikersinformatie en opiniepeilingsinterval.</td>
  </tr>
  <tr>
   <td>getTasksForDirectReports</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getTasksForDirectReports</td>
   <td>Het keert alle taken van directe rapporten van de het programma geopende manager terug.</td>
  </tr>
  <tr>
   <td>getTaskOfDirectReport<br /> </td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getDirectReportTask</td>
   <td>Het keert een taak van een gespecificeerd direct rapport van de het programma geopende manager terug.</td>
  </tr>
  <tr>
   <td>forwardTaskOfDirectReport</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>forwardTaskOfDirectReport</td>
   <td>Het stuurt een taak van een direct rapport naar een andere gebruiker door.</td>
  </tr>
  <tr>
   <td>ignoreTaskOfDirectReport</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>ignoreTaskOfDirectReport</td>
   <td>Het keert een taak van een direct rapport aan de vorige gebruiker terug.</td>
  </tr>
  <tr>
   <td>getProperty</td>
   <td>WorkspacePropertyService</td>
   <td>getProperty</td>
   <td>Het krijgt een bezit van de Werkruimte voor een gebruiker.</td>
  </tr>
  <tr>
   <td>removeProperty</td>
   <td>WorkspacePropertyService</td>
   <td>delete</td>
   <td>Het verwijdert een bezit van de Werkruimte voor een gebruiker.</td>
  </tr>
  <tr>
   <td>getProperties</td>
   <td>WorkspacePropertyService</td>
   <td>getPropertiesAsMap</td>
   <td>Hiermee worden alle Workspace-eigenschappen voor een gebruiker geretourneerd.</td>
  </tr>
  <tr>
   <td>setProperty</td>
   <td>WorkspacePropertyService</td>
   <td>setProperty</td>
   <td>Hiermee wordt een eigenschap Workspace voor een gebruiker ingesteld.</td>
  </tr>
  <tr>
   <td>getCurrentUserImageUrl</td>
   <td>ProcessManagementClientSessionService</td>
   <td>getCurrentUserImageUrl</td>
   <td>De URL van de afbeelding van de gebruiker wordt opgehaald voor de aangemelde gebruiker.</td>
  </tr>
  <tr>
   <td>getUserImageUrl</td>
   <td>ProcessManagementClientSessionService</td>
   <td>getUserImageUrl</td>
   <td>De URL van de afbeelding van de gebruiker wordt voor de opgegeven gebruiker opgehaald.</td>
  </tr>
  <tr>
   <td>uploadNote</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadNote</td>
   <td>Er wordt een notitie op de server geüpload voor een taak.</td>
  </tr>
  <tr>
   <td>uploadRMAToServer (het wordt ook direct geroepen van HTML malplaatje)<br /> </td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadAttachment</td>
   <td>Er wordt een bijlage geüpload naar de server voor een taak.</td>
  </tr>
  <tr>
   <td>getImageURL (ook rechtstreeks aangeroepen vanuit de HTML-sjabloon)</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>getImage</td>
   <td>Het krijgt het beeld voor een proces.</td>
  </tr>
 </tbody>
</table>
