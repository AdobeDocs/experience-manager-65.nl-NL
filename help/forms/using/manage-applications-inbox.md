---
title: Forms-toepassingen en -taken beheren in AEM Postvak In
description: Met AEM Inbox kunt u op Forms gerichte workflows starten door toepassingen in te dienen en taken te beheren.
contentOwner: vishgupt
topic-tags: document_services, publish
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: 8d17194b-8baf-4878-b3ae-d351a056aebf
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---

# Forms-toepassingen en -taken beheren in AEM Postvak In{#manage-forms-applications-and-tasks-in-aem-inbox}

Een van de vele manieren om een Forms-centric workflow te starten of activeren is via toepassingen in AEM Inbox. Als u een Forms-workflow als toepassing beschikbaar wilt maken in Inbox, maakt u een workflowtoepassing. Ga voor meer informatie over workflowtoepassingen en andere manieren om Forms-workflows te starten naar [Een Forms-centric workflow starten op OSGi](../../forms/using/aem-forms-workflow.md#launch).

Daarnaast consolideert AEM Inbox meldingen en taken van verschillende AEM, waaronder Forms-workflows. Wanneer een formulierwerkstroom met een taakstap Toewijzen wordt geactiveerd, wordt de bijbehorende toepassing weergegeven als een taak in het Postvak In van de ontvanger. Als de toegewezen persoon een groep is, wordt de taak in het Postvak In van alle groepsleden weergegeven totdat een persoon de taak aanvraagt of delegeert.

De gebruikersinterface van Inbox verstrekt lijst en kalendermeningen om taken te bekijken. U kunt ook de weergave-instellingen configureren. U kunt taken filteren op basis van verschillende parameters. Zie voor meer informatie over weergave en filters [Uw Postvak IN](/help/sites-authoring/inbox.md).

Samenvattend kunt u met Inbox een toepassing maken en toegewezen taken beheren.

>[!NOTE]
>
>U moet lid van de werkstroom-gebruikers groep zijn om AEM Inbox te kunnen gebruiken.

## Toepassing maken {#create-application}

1. Ga naar AEM Postvak IN op https://&#39;[server]:[poort]&#39;/aem/inbox.
1. Selecteer in de gebruikersinterface van het Postvak IN de optie **[!UICONTROL Create > Application]**. De pagina Selecteer toepassing wordt weergegeven.
1. Selecteer een toepassing en klik op **[!UICONTROL Create]**. Het adaptieve formulier dat aan de toepassing is gekoppeld, wordt geopend. Vul de gegevens in het adaptieve formulier in en selecteer **[!UICONTROL Submit]**. De bijbehorende workflow wordt gestart en er wordt een taak gemaakt in het Postvak In van de ontvanger.

## Taken beheren {#manage-tasks}

Wanneer een Forms-workflow wordt geactiveerd en u bent een ontvanger of onderdeel van de groep waaraan u bent toegewezen, wordt een taak weergegeven in uw Postvak In. U kunt taakdetails bekijken en beschikbare acties op de taak van binnen Inbox uitvoeren.

### Vorderingen of gedelegeerde taken {#claim-or-delegate-tasks}

De taken die aan een groep worden toegewezen verschijnen in Inbox van alle groepsleden. Om het even welk groepslid kan die taak beweren of het aan een ander groepslid delegeren. Daartoe:

1. Selecteer deze optie om de miniatuur van de taak te selecteren. Opties voor het openen of delegeren van de taak worden bovenaan weergegeven.

   ![selecteren-taak](assets/select-task.png)

1. Voer een van de volgende handelingen uit:

   * Als u de taak wilt delegeren, selecteert u **[!UICONTROL Delegate]**. Het dialoogvenster Item delegeren wordt geopend. Selecteer een gebruiker, voeg desgewenst een opmerking toe en selecteer **[!UICONTROL OK]**.

   ![gedelegeerde](assets/delegate.png)

   * Selecteer **[!UICONTROL Open]**. Het dialoogvenster Toewijzen aan zelf wordt geopend. Selecteren **[!UICONTROL Proceed]** om de taak op te eisen. De geclaimde taak wordt met u weergegeven als de toegewezen persoon in uw Postvak IN.

   ![vordering](assets/claim.png)

### Details weergeven en handelingen uitvoeren voor taken {#view-details-and-perform-actions-on-tasks}

Wanneer u een taak opent, kunt u taakdetails bekijken en beschikbare acties uitvoeren. De acties die beschikbaar zijn voor een taak worden gedefinieerd in de taakstap Toewijzen van de bijbehorende Forms-workflow.

1. Selecteer deze optie om de miniatuur van de taak te selecteren. Opties voor het openen of delegeren van de geselecteerde taak worden bovenaan weergegeven.
1. Selecteren **Openen** om taakdetails te bekijken. De gedetailleerde taakweergave wordt geopend. In deze weergave kunt u taakdetails weergeven en aan de taak werken.

   >[!NOTE]
   >
   >Als een taak aan een groep wordt toegewezen, moet u beweren het in gedetailleerde mening kan openen.

![taakdetails](assets/task-details.png)

De gedetailleerde taakmening omvat de volgende secties:

* Taakdetails
* Formulier
* Workflowdetails
* Werkbalk Handelingen

#### Taakdetails {#task-details}

In de sectie Taakdetails wordt informatie over de taak weergegeven. De weergegeven informatie is afhankelijk van de configuratie-instellingen van de [Taakstap toewijzen](/help/sites-developing/workflows-step-ref.md) in de workflow. In het bovenstaande voorbeeld worden de beschrijving, de status, de begindatum en de workflow weergegeven die voor de taak worden gebruikt. U kunt ook een bestand aan de taak koppelen.

#### Formulier {#form}

Op het tabblad Formulier in het hoofdinhoudsgebied worden het verzonden formulier en eventuele bijlagen op veldniveau weergegeven.

#### Workflowdetails {#workflow-details}

Het tabblad Workflowdetails bovenaan geeft de voortgang van de taak in verschillende fasen van de workflow weer. Het toont voltooide, huidige, en hangende stadia voor de taak. De fasen van een workflow worden gedefinieerd in het dialoogvenster [Taakstap toewijzen](/help/sites-developing/workflows-step-ref.md) van de bijbehorende workflow.

Bovendien geeft het tabblad de taakgeschiedenis weer voor elk voltooid werkgebied in de workflow. U kunt **[!UICONTROL View Details]** voor een voltooide fase om details over die fase te kennen. Er worden opmerkingen, formulier- en taakbijlagen, status, begin- en einddatums enzovoort over de taak weergegeven.

![workflowdetails](assets/workflow-details.png)

#### Werkbalk Handelingen {#actions-toolbar}

Op de werkbalk Handelingen staan alle beschikbare opties voor de taak. Terwijl sparen, het Terugstellen, en de Delegatie standaardacties zijn, worden andere beschikbare acties gevormd in [Taakstap toewijzen](/help/sites-developing/workflows-step-ref.md). In het bovenstaande voorbeeld worden Goedkeuren en Afwijzen geconfigureerd in de workflow.

Terwijl u aan de taak werkt, gaat het verder in de workflow.

### Voltooide taken weergeven {#view-completed-tasks}

AEM In Postvak In worden alleen actieve taken weergegeven. Voltooide taken worden niet in de lijst weergegeven. U kunt echter Inbox-filters gebruiken om taken te filteren op basis van verschillende parameters, zoals taaktype, status en begin- en einddatum. Voltooide taken weergeven:

1. Selecteer in AEM Postvak IN de optie ![aan de zijkant schakelen1](assets/toggle-side-panel1.png) om de filterkiezer te openen.
1. Selecteren **[!UICONTROL Task Status]** accordeon en selecteer **[!UICONTROL Complete]**. Alle voltooide taken worden weergegeven.

   ![filter](assets/filter.png)

1. Selecteer een taak en klik op **[!UICONTROL Open]**.

De taak wordt geopend om het document of het adaptieve formulier weer te geven dat aan de taak is gekoppeld. Voor een adaptief formulier wordt het alleen-lezen adaptieve formulier of het bijbehorende PDF-document met record weergegeven, zoals geconfigureerd op het tabblad Formulier/Document van het dialoogvenster [Workflowstap Toewijzen](/help/sites-developing/workflows-step-ref.md).

In de sectie met taakdetails wordt informatie weergegeven zoals de ondernomen actie, taakstatus, begindatum en einddatum.

![voltooide taak](assets/completed-task.png)

De **[!UICONTROL Workflow Details]** wordt elke stap van de workflow weergegeven. Selecteren **[!UICONTROL View details]** voor een stap voor gedetailleerde informatie.

![voltooid-taak-werkschema](assets/completed-task-workflow.png)

## Problemen oplossen {#troubleshooting-workflows}

### Kan geen items weergeven die gerelateerd zijn aan AEM workflow in AEM inbox {#unable-to-see-aem-worklow-items}

Een eigenaar van een workflowmodel kan geen items met betrekking tot AEM workflow in AEM inbox weergeven. Om het probleem op te lossen, voegt u de onderstaande indexen toe aan uw AEM opslagplaats en maakt u de index opnieuw.

1. Gebruik een van de volgende methoden om indexen toe te voegen:

   * De volgende knooppunten maken in CRX DE op `/oak:index/workflowDataLucene/indexRules/granite:InboxItem/properties` met de respectieve eigenschappen zoals gespecificeerd in de volgende tabel:

     | Knooppunt | Eigenschap | Type |
     |---|---|---|
     | sharedWith | sharedWith | TEKENREEKS |
     | vergrendeld | vergrendeld | BOOLEAN |
     | geretourneerd | geretourneerd | BOOLEAN |
     | allowInboxSharing | allowInboxSharing | BOOLEAN |
     | allowExplicitSharing | allowExplicitSharing | BOOLEAN |


   * Implementeer de indices door middel van een AEM pakket. U kunt een [AEM Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en) project om een implementeerbaar AEM pakket te maken. Gebruik de volgende steekproefcode om indexen aan een project van het type van AEM toe te voegen Archetype:

   ```Java
      .property("sharedWith", "sharedWith").type(TYPENAME_STRING).propertyIndex()
      .property("locked", "locked").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("returned", "returned").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowInboxSharing", "allowInboxSharing").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowExplicitSharing", "allowExplicitSharing").type(TYPENAME_BOOLEAN).propertyIndex()
   ```

1. [Een index voor eigenschappen maken en instellen op true](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html#the-property-index).

1. Na het configureren van indices in CRX DE of het implementeren via een pakket, [de gegevensopslagplaats opnieuw indexeren](https://helpx.adobe.com/in/experience-manager/kb/HowToCheckLuceneIndex.html#Completelyrebuildtheindex).

https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html
