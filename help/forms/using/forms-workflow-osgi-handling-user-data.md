---
title: Forms-gecentreerde workflows op OSGi | Gebruikersgegevens verwerken
description: Forms-gecentreerde workflows op OSGi | Gebruikersgegevens verwerken
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin
exl-id: fd0e17d7-c3e9-4dec-ad26-ed96a1881f42
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# Forms-gecentreerde workflows op OSGi | Gebruikersgegevens verwerken {#forms-centric-workflows-on-osgi-handling-user-data}

Met Forms-gerichte AEM-workflows kunt u real-world Forms-gecentreerde bedrijfsprocessen automatiseren. Workflows bestaan uit een reeks stappen die worden uitgevoerd in een volgorde die is opgegeven in het bijbehorende workflowmodel. Elke stap voert een specifieke actie uit zoals het toewijzen van een taak aan een gebruiker of het verzenden van een e-mailbericht. Workflows kunnen communiceren met middelen in de opslagplaats, gebruikersaccounts en services. Daarom kunnen werkstromen ingewikkelde activiteiten coördineren die om het even welk aspect van Experience Manager impliceren.

Een op formulieren gerichte workflow kan op een van de volgende manieren worden geactiveerd of gestart:

* Een toepassing verzenden vanuit AEM Postvak In
* Een toepassing indienen vanuit AEM [!DNL Forms] App
* Een adaptief formulier indienen
* Een controlemap gebruiken
* Een interactieve communicatie of een brief indienen

Voor meer informatie over Forms-centric AEM workflows en mogelijkheden raadpleegt u [Forms-centric workflow op OSGi](/help/forms/using/aem-forms-workflow.md).

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Wanneer een werkstroom wordt geactiveerd, wordt automatisch een laadbewerking voor de werkstroominstantie gegenereerd. Aan elke werkstroominstantie wordt een unieke instantie-id en een bijbehorende ladings-id toegewezen. De payload bevat de opslaglocaties voor gebruikers- en formuliergegevens die zijn gekoppeld aan een workflowexemplaar. Daarnaast worden concepten en historische gegevens voor een werkstroominstantie ook opgeslagen in de AEM opslagplaats.

De standaardopslagplaatsen waar lading, concepten, en geschiedenis van een werkschemainstantie verblijven zijn als volgt:

>[!NOTE]
>
>U kunt verschillende locaties configureren voor het opslaan van gegevens over de lading, het concept en de geschiedenis wanneer u een workflow of toepassing maakt. Als u de locaties wilt identificeren waar een workflow of toepassing gegevens heeft opgeslagen, raadpleegt u de workflow.

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><b>AEM 6,4 [!DNL Forms]</b></td>
   <td><b>AEM 6,3 [!DNL Forms]</b></td>
  </tr>
  <tr>
   <td><strong>Workflow <br /> instance</strong></td>
   <td>/var/workflow/instances/[server_id]/&lt;date&gt;/[workflow-instance]/</td>
   <td>/etc/workflow/instances/[server_id]/[date]/[workflow-instance]/</td>
  </tr>
  <tr>
   <td><strong>Payload</strong></td>
   <td>/var/fd/dashboard/payload/[server_id]/[date]/<br /> [payload-id]/</td>
   <td>/etc/fd/dashboard/payload/[server_id]/[date]/<br /> [payload-id]/</td>
  </tr>
  <tr>
   <td><strong>Concepten</strong></td>
   <td>/var/fd/dashboard/instances/[server_id]/<br /> [datum]/[werkstroominstantie]/concept/[werkitem]/</td>
   <td>/etc/fd/dashboard/instances/[server_id]/<br /> [datum]/[werkstroominstantie]/concept/[werkitem]/</td>
  </tr>
  <tr>
   <td><strong>Historie</strong></td>
   <td>/var/fd/dashboard/instances/[server_id]/<br /> [datum]/[werkstroom_instantie]/geschiedenis/</td>
   <td>/etc/fd/dashboard/instances/[server_id]/<br /> [datum]/[werkstroom_instantie]/geschiedenis/</td>
  </tr>
 </tbody>
</table>

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt gebruikersgegevens uit een werkstroominstantie in de gegevensopslagruimte openen en verwijderen. U kunt dit bereiken door de instantie-id te kennen van de werkstroominstantie die aan de gebruiker is gekoppeld. U kunt instantie-id van een werkstroominstantie vinden met behulp van de gebruikersnaam van de gebruiker die de werkstroominstantie heeft gestart of die de huidige ontvanger van de werkstroominstantie is.

U kunt de resultaten echter niet identificeren of dubbelzinnig weergeven wanneer u werkstromen identificeert die aan een aanvrager zijn gekoppeld in de volgende scenario&#39;s:

* **Workflow geactiveerd door een gecontroleerde map**: Een workflowinstantie kan niet worden geïdentificeerd met de initiator als de workflow wordt geactiveerd door een gecontroleerde map. In dit geval wordt de gebruikersinformatie gecodeerd in de opgeslagen gegevens.
* **Workflow gestart vanaf AEM publicatie-instantie**: Alle workflowinstanties worden gemaakt met behulp van een servicegebruiker wanneer adaptieve formulieren, interactieve communicatie of letters worden verzonden vanuit AEM publicatie-instantie. In deze gevallen wordt de gebruikersnaam van de aangemelde gebruiker niet vastgelegd in de gegevens van de workflowinstantie.

### Gebruikersgegevens openen {#access}

Voer de volgende stappen uit om gebruikersgegevens te identificeren en te benaderen die voor een workflowinstantie zijn opgeslagen:

1. Ga bij AEM auteurinstantie naar `https://'[server]:[port]'/crx/de` en navigeer naar **[!UICONTROL Tools > Query]**.

   Selecteren **[!UICONTROL SQL2]** van de **[!UICONTROL Type]** vervolgkeuzelijst.

1. Voer afhankelijk van de beschikbare informatie een van de volgende query&#39;s uit:

   * Voer het volgende uit als de werkstroominitiator bekend is:

   `SELECT &ast; FROM [cq:Workflow] AS s WHERE ISDESCENDANTNODE([path-to-workflow-instances]) and s.[initiator]='*initiator-ID*'`

   * Voer het volgende uit als de gebruiker van wie u gegevens vindt de huidige werkschema toegewezen is:

   `SELECT &ast; FROM [cq:WorkItem] AS s WHERE ISDESCENDANTNODE([path-to-workflow-instances]) and s.[assignee]='*assignee-id*'`

   De query retourneert de locatie van alle werkstroominstanties voor de opgegeven werkstroominitiator of de huidige werkstroomontvanger.

   De volgende query retourneert bijvoorbeeld twee pad naar workflowinstanties van het dialoogvenster `/var/workflow/instances` knooppunt waarvan de werkstroominitiator `srose`.

   ![workflow-instance](assets/workflow-instance.png)

1. Ga naar een pad voor workflowinstanties dat door de query wordt geretourneerd. De statuseigenschap geeft de huidige status van de werkstroominstantie weer.

   ![status](assets/status.png)

1. Navigeer in het knooppunt voor workflowinstanties naar `data/payload/`. De `path` eigenschap slaat het pad naar de payload voor de werkstroominstantie op. U kunt naar het pad navigeren om toegang te krijgen tot gegevens die zijn opgeslagen in de payload.

   ![payload-path](assets/payload-path.png)

1. Navigeer naar de locaties voor concepten en historie voor de workflowinstantie.

   Bijvoorbeeld:

   `/var/fd/dashboard/instances/server0/2018-04-09/_var_workflow_instances_server0_2018-04-09_basicmodel_54/draft/`

   `/var/fd/dashboard/instances/server0/2018-04-09/_var_workflow_instances_server0_2018-04-09_basicmodel_54/history/`

1. Herhaal stap 3 - 5 voor alle werkstroominstanties die door de query in stap 2 zijn geretourneerd.

   >[!NOTE]
   >
   >AEM [!DNL Forms] de app slaat ook gegevens op in de offlinemodus. Het is mogelijk dat gegevens voor een werkstroominstantie lokaal worden opgeslagen op individuele apparaten en worden verzonden naar de [!DNL Forms] wanneer de toepassing synchroniseert met de server.

### Gebruikersgegevens verwijderen {#delete-user-data}

U moet een AEM beheerder zijn om gebruikersgegevens uit workflowinstanties te verwijderen door de volgende stappen uit te voeren:

1. Volg de instructies in [Gebruikersgegevens openen](/help/forms/using/forms-workflow-osgi-handling-user-data.md#access) en nemen nota van het volgende :

   * Paden naar werkstroominstanties die aan de gebruiker zijn gekoppeld
   * Status van de workflowinstanties
   * Paden naar ladingen voor de workflowinstanties
   * Paden naar concepten en historie voor workflowinstanties

1. Voer deze stap uit voor workflowinstanties in **UITVOEREN**, **GESCHORST**, of **STAAL** status:

   1. Ga naar `https://'[server]:[port]'/aem/start.html` en aanmelden met beheerdersreferenties.
   1. Navigeren naar **[!UICONTROL Tools > Workflow> Instances]**.
   1. Selecteer relevante workflowinstanties voor de gebruiker en selecteer **[!UICONTROL Terminate]** om actieve exemplaren te beëindigen.

      Zie voor meer informatie over het werken met workflowinstanties [Workflowinstanties beheren](/help/sites-administering/workflows-administering.md).

1. Ga naar [!DNL CRXDE Lite] -console, navigeert u naar het payload-pad voor een workflowinstantie en verwijdert u de `payload` knooppunt.
1. Navigeer naar het pad naar concepten voor een werkstroominstantie en verwijder de `draft` knooppunt.
1. Navigeer naar het historiepad voor een werkstroominstantie en verwijder de `history` knooppunt.
1. Navigeer naar het pad van de workflowinstantie voor een workflowinstantie en verwijder de `[workflow-instance-ID]` knooppunt voor de workflow.

   >[!NOTE]
   >
   >Als u het knooppunt voor workflowinstanties verwijdert, wordt de instantie van de workflow voor alle workflowdeelnemers verwijderd.

1. Herhaal stap 2 - 6 voor alle workflowinstanties die voor een gebruiker zijn geïdentificeerd.
1. Offline concept- en verzendgegevens van AEM identificeren en verwijderen [!DNL Forms] buiten het werkstroomprogramma om verzenden naar de server te voorkomen.

U kunt API&#39;s ook gebruiken om knooppunten en eigenschappen te openen en te verwijderen. Zie de volgende documenten voor meer informatie.

* [Programmatoegang tot het AEM JCR](/help/sites-developing/access-jcr.md)
* [Knooppunten en eigenschappen verwijderen](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/10_Writing.html#10.9%20Removing%20Nodes%20and%20Properties)
* [API-referentie](https://helpx.adobe.com/experience-manager/6-3/sites-developing/reference-materials/javadoc/overview-summary.html)
