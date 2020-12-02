---
title: Workflowinstanties beheren
seo-title: Workflowinstanties beheren
description: Leer hoe u workflowinstanties beheert.
seo-description: Leer hoe u workflowinstanties beheert.
uuid: 81e53ef5-fe62-4ed4-b2d4-132aa986d5aa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: d9c96e7f-9416-48e1-a6af-47384f7bee92
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---


# Workflowinstanties beheren{#administering-workflow-instances}

De workflowconsole biedt verschillende gereedschappen voor het beheer van workflowinstanties om ervoor te zorgen dat deze naar behoren worden uitgevoerd.

>[!NOTE]
>
>De [JMX-console](/help/sites-administering/jmx-console.md#workflow-maintenance) biedt extra workflowonderhoudsbewerkingen.

Er zijn verschillende consoles beschikbaar voor het beheer van uw workflows. Gebruik [globale navigatie](/help/sites-authoring/basic-handling.md#global-navigation) om **Hulpmiddelen** ruit te openen, dan uitgezocht **Workflow**:

* **Modellen**: Workflowdefinities beheren
* **Instanties**: Doorlopende workflowinstanties weergeven en beheren
* **Launchers**: De manier beheren waarop workflows worden gestart
* **Archief**: De geschiedenis weergeven van workflows die zijn voltooid
* **Mislukt**: De geschiedenis weergeven van workflows die zijn voltooid met fouten

## De status van workflowinstanties controleren {#monitoring-the-status-of-workflow-instances}

1. Selecteer **Tools** met Navigatie en **Workflow**.
1. Selecteer **Instanties** om de lijst weer te geven met werkstroominstanties die momenteel worden uitgevoerd.

   ![wf-96](assets/wf-96.png)

1. Selecteer een specifiek punt, dan **Open Geschiedenis** om meer details te zien:

   ![wf-97](assets/wf-97.png)

## Het onderbreken, Hervatten, en het Eindigen van een Instantie van het Werkschema {#suspending-resuming-and-terminating-a-workflow-instance}

1. Selecteer **Tools** met Navigatie en **Workflow**.
1. Selecteer **Instanties** om de lijst weer te geven met werkstroominstanties die momenteel worden uitgevoerd.

   ![wf-96-1](assets/wf-96-1.png)

1. Selecteer een specifiek punt, dan gebruik **Terminate**, **Suspend**, of **hervatten**, zoals aangewezen; bevestiging en/of nadere bijzonderheden zijn vereist:

   ![wf-97-1](assets/wf-97-1.png)

## Gearchiveerde workflows weergeven {#viewing-archived-workflows}

1. Selecteer **Tools** met Navigatie en **Workflow**.
1. Selecteer **Archiveren** om de lijst met workflowinstanties weer te geven die met succes zijn voltooid.

   ![wf-98](assets/wf-98.png)

   >[!NOTE]
   >
   >De afbreekstatus wordt beschouwd als een succesvolle beëindiging aangezien het als resultaat van gebruikersactie voorkomt; bijvoorbeeld:
   >
   >* gebruik van de handeling **Terminate**
   >* als een pagina die onderworpen is aan een workflow (geforceerd) wordt verwijderd, wordt de workflow beëindigd


1. Selecteer een specifiek punt, dan **Open Geschiedenis** om meer details te zien:

   ![wf-99](assets/wf-99.png)

## Problemen met werkstroominstanties oplossen {#fixing-workflow-instance-failures}

Wanneer een werkschema ontbreekt, verstrekt AEM **Failures** console om u toe te staan om aangewezen actie te onderzoeken en te nemen zodra de originele oorzaak is behandeld:

* **Geen**
detailsHiermee wordt een venster geopend waarin de 
**Mislukkingsbericht**,  **** Stapel  **Stapel**.

* **Open**
HistorieHiermee geeft u details weer over de workflowgeschiedenis.

* **Opnieuw** StepExecutes de de componenteninstantie van de Stap van het Manuscript opnieuw. Gebruik de opdracht Stap opnieuw proberen nadat u de oorzaak van de oorspronkelijke fout hebt opgelost. U kunt bijvoorbeeld de stap opnieuw uitvoeren nadat u een fout in het script hebt opgelost dat door de processtap wordt uitgevoerd.
* **Beëindig de werkstroom als de fout een onherstelbare situatie voor het werkschema heeft veroorzaakt.** De workflow kan bijvoorbeeld afhankelijk zijn van omgevingsfactoren, zoals informatie in de opslagruimte die niet langer geldig is voor de werkstroominstantie.
* **Beëindigen en** Opnieuw proberenGelijkaardig aan  **** Terminateeg behalve dat wordt een nieuwe werkschemainstantie begonnen gebruikend de originele nuttige lading, de titel, en de beschrijving.

Om mislukkingen te onderzoeken, dan hervat of beëindigt het werkschema daarna, gebruik de volgende stappen:

1. Selecteer **Tools** met Navigatie en **Workflow**.
1. Selecteer **Failures** om de lijst weer te geven met workflowinstanties die niet met succes zijn voltooid.
1. Selecteer een specifiek item en voer de gewenste actie uit:

   ![wf-47](assets/wf-47.png)

## Regelmatig leegmaken van workflowinstanties {#regular-purging-of-workflow-instances}

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen.

Configureer **Adobe Granite Workflow Purge Configuration** om workflowinstanties te wissen volgens hun leeftijd en status. U kunt ook werkstroominstanties van alle modellen of van een specifiek model wissen.

U kunt ook meerdere configuraties van de service maken om workflowinstanties die aan verschillende criteria voldoen, leeg te maken. Maak bijvoorbeeld een configuratie die de instanties van een bepaald workflowmodel zuivert wanneer deze veel langer dan de verwachte tijd worden uitgevoerd. Maak een andere configuratie die alle voltooide workflows na een bepaald aantal dagen leegmaakt om de grootte van de opslagplaats te minimaliseren.

Om de dienst te vormen, kunt u [Webconsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of [een configuratie OSGi aan bewaarplaats toevoegen](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository). In de volgende tabel worden de eigenschappen beschreven die u voor een van beide methoden nodig hebt.

>[!NOTE]
>
>Voor het toevoegen van de configuratie aan de repository is de service-PID:
>
>`com.adobe.granite.workflow.purge.Scheduler`
>
>Omdat de service een fabrieksservice is, vereist de naam van de `sling:OsgiConfig`-node een achtervoegsel met id, bijvoorbeeld:
>
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table>
 <tbody>
  <tr>
   <th>Naam eigenschap (webconsole)</th>
   <th>OSGi Eigenschapnaam</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Taaknaam</td>
   <td>scheduledpurge.name</td>
   <td>Een beschrijvende naam voor de geplande leegloop.</td>
  </tr>
  <tr>
   <td>Workflowstatus</td>
   <td>scheduledpurge.workflowStatus</td>
   <td><p>De status van de werkstroominstanties die moeten worden gewist. De volgende waarden zijn geldig:</p>
    <ul>
     <li>VOLTOOID: Voltooide workflowinstanties worden gewist.</li>
     <li>UITVOEREN: Doorlopende workflowinstanties worden gewist.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Te wissen modellen</td>
   <td>scheduledpurge.modelIds</td>
   <td><p>De id van de workflowmodellen die moeten worden gewist. De id is het pad naar het modelknooppunt, bijvoorbeeld:<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model<br /> Geef geen waarde op om instanties van alle workflowmodellen leeg te maken.</p> <p>Als u meerdere modellen wilt opgeven, klikt u op + in de webconsole. </p> </td>
  </tr>
  <tr>
   <td>Werkstroomleeftijd</td>
   <td>scheduledpurge.daysold</td>
   <td>De leeftijd van de werkstroominstanties die moeten worden gewist, in dagen.</td>
  </tr>
 </tbody>
</table>

## De maximale grootte van het Postvak IN instellen {#setting-the-maximum-size-of-the-inbox}

U kunt de maximumgrootte van inbox plaatsen door **de Dienst van het Werkschema van de Adobe granite** te vormen, gebruikend [Webconsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of [voeg een configuratie OSGi aan de bewaarplaats](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) toe. De volgende lijst beschrijft het bezit dat u voor één van beide methode vormt.

>[!NOTE]
>
>Voor het toevoegen van de configuratie aan de repository is de service-PID:
>
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Naam eigenschap (webconsole) | OSGi Eigenschapnaam |
|---|---|
| Max. grootte van invoerquery | granite.workflow.inboxQuerySize |

