---
title: Workflows starten
seo-title: Workflows starten
description: Leer hoe u workflows in AEM start.
seo-description: Leer hoe u workflows in AEM start.
uuid: 0648d335-ecce-459d-95fd-3d4d76181b32
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: e9ab4796-a050-40de-b073-af7d33cff009
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 1%

---


# Workflows starten{#starting-workflows}

Wanneer u workflows beheert, kunt u deze op verschillende manieren starten:

* Handmatig:

   * Van een [Werkstroommodel](#workflow-models).
   * Een workflowpakket gebruiken voor [batchverwerking](#workflow-packages-for-batch-processing).

* Automatisch:

   * Als reactie op wijzigingen in knooppunten; [een Launcher](#workflows-launchers) gebruiken.

>[!NOTE]
>
>Andere methoden zijn ook beschikbaar voor auteurs; zie voor nadere bijzonderheden :
>
>* [Workflows toepassen op pagina&#39;s](/help/sites-authoring/workflows-applying.md)
>* [Workflows toepassen op DAM-elementen](/help/assets/assets-workflow.md)
>* [AEM Forms](https://helpx.adobe.com/aem-forms/6-2/aem-workflows-submit-process-form.html)
>* [Omzettingsprojecten](/help/sites-administering/tc-manage.md)

>



## Workflowmodellen {#workflow-models}

U kunt een werkschema [beginnen op één van de modellen](/help/sites-administering/workflows.md#workflow-models-and-instances) die op de console van de Modellen van het Werkschema worden vermeld. De enige verplichte informatie is de lading, hoewel een titel en/of commentaar ook kan worden toegevoegd.

## Workflows Launchers {#workflows-launchers}

De Workflow Launcher controleert wijzigingen in de inhoudsopslagruimte om workflows te starten afhankelijk van de locatie en het type bron van het gewijzigde knooppunt.

Met de **Launcher** kunt u:

* Zie de workflows die al zijn gestart voor specifieke knooppunten.
* Selecteer een workflow die moet worden gestart wanneer een bepaald knooppunt/knooppunttype is gemaakt/gewijzigd/verwijderd.
* Verwijder een bestaande werkstroom-aan-knoop verhouding.

Voor elk knooppunt kan een startprogramma worden gemaakt. Wijzigingen in bepaalde knooppunten leiden echter niet tot workflows. Als u knooppunten wijzigt die onder de volgende paden liggen, worden workflows niet gestart:

* `/var/workflow/instances`
* Om het even welk werkschema-inbox knoop die overal in `/home/users` tak wordt gevestigd
* `/tmp`
* `/var/audit`
* `/var/classes`
* `/var/eventing`
* `/var/linkchecker`
* `/var/mobile`
* `/var/statistics`

   * Uitzondering: Wijzigingen in knooppunten onder `/var/statistics/tracking` *do* zorgen ervoor dat workflows worden gestart.

De standaardinstallatie bevat verschillende definities. Deze worden gebruikt voor taken op het gebied van digitaal middelenbeheer en sociale samenwerking:

![wf-100](assets/wf-100.png)

## Workflowpakketten voor batchverwerking {#workflow-packages-for-batch-processing}

Workflowpakketten zijn pakketten die kunnen worden doorgegeven aan een workflow als een payload voor verwerking, zodat meerdere bronnen kunnen worden verwerkt.

Een workflowpakket:

* bevat koppelingen naar een set bronnen (zoals pagina&#39;s, elementen).
* bevat pakketinformatie zoals de aanmaakdatum, de gebruiker die het pakket heeft gemaakt en een korte beschrijving.
* wordt gedefinieerd met behulp van een gespecialiseerde paginasjabloon; op deze pagina&#39;s kan de gebruiker de bronnen in het pakket opgeven.
* kan meerdere keren worden gebruikt.
* kan door de gebruiker worden gewijzigd (voeg of verwijder middelen toe) terwijl de werkschemainstantie eigenlijk loopt.

## Een workflow starten vanuit de modellenconsole {#starting-a-workflow-from-the-models-console}

1. Navigeer naar de **Modellen** console met **Tools**, **Workflow**, dan **Models**.
1. Selecteer de werkstroom (volgens de consolemening); U kunt ook Zoeken (linksboven) gebruiken als dat nodig is:

   ![wf-103](assets/wf-103.png)

   >[!NOTE]
   >
   >De indicator **[Transient](/help/sites-developing/workflows.md#transient-workflows)** toont werkschema&#39;s waarvoor de werkschemageschiedenis niet zal worden voortgeduurd.

1. Selecteer **Workflow starten** op de werkbalk.
1. Het dialoogvenster Werkstroom uitvoeren wordt geopend, zodat u het volgende kunt opgeven:

   * **Payload**

      Dit kan een pagina, knooppunt, element, pakket zijn, naast andere bronnen.

   * **Titel**

      Een optionele titel waarmee dit exemplaar kan worden geïdentificeerd.

   * **Opmerking**

      Een optionele opmerking waarmee u details van dit exemplaar kunt aangeven.
   ![wf-104](assets/wf-104.png)

## Een opstartconfiguratie maken {#creating-a-launcher-configuration}

1. Navigeer naar de **Workflow Launchers**-console met **Tools**, **Workflow** en **Launchers**.
1. Selecteer **Maken** en **Startpagina toevoegen** om het dialoogvenster te openen:

   ![wf-105](assets/wf-105.png)

   * **Type gebeurtenis**

      Het gebeurtenistype dat de workflow start:

      * Gemaakt
      * Gewijzigd
      * Verwijderd
   * **notetype**

      Het type knooppunt waarop de workflow wordt gestart.

   * **Pad**

      Het pad waarop de workflow wordt gestart.

   * **Run-modus(s)**

      Het type server waarop de workflow wordt gestart. Selecteer **Auteur**, **Publiceren** of **Auteur en publiceren**.

   * **Voorwaarden**

      Een lijst met voorwaarden voor knoopwaarden die, wanneer geëvalueerd, bepalen of de workflow wordt gestart. De volgende voorwaarde zorgt er bijvoorbeeld voor dat de workflow wordt gestart wanneer het knooppunt een eigenschapnaam met de waarde Gebruiker heeft:

      name==User

   * **Functies**

      Een lijst met functies die moeten worden ingeschakeld. Selecteer de gewenste functie(s) met de keuzelijst.

   * **Uitgeschakelde functies**

   Een lijst met functies die moeten worden uitgeschakeld. Selecteer de gewenste functie(s) met de keuzelijst.

   * **Workflowmodel**

      De workflow die moet worden gestart wanneer het gebeurtenistype zich voordoet op Nodetype en/of Path onder de gedefinieerde Voorwaarde.

   * **Beschrijving**

      Uw eigen tekst om de startconfiguratie te beschrijven en te identificeren.

   * **Activeren**

      Bepaalt of de workflow wordt gestart:

      * Selecteer **Inschakelen** om workflows te starten wanneer aan de configuratie-eigenschappen wordt voldaan.
      * Selecteer **Uitschakelen** wanneer de workflow niet moet worden uitgevoerd (zelfs niet wanneer aan de configuratie-eigenschappen wordt voldaan).
   * **Lijst uitsluiten**

      Hiermee worden JCR-gebeurtenissen opgegeven die moeten worden uitgesloten (negeren) wanneer wordt bepaald of een workflow moet worden geactiveerd.

      Deze lanceereigenschap is een door komma&#39;s gescheiden lijst met items: &quot;

      * `property-name` negeert om het even welke  `jcr` gebeurtenis die op de gespecificeerde bezitsnaam teweegbracht. &quot;
      * `event-user-data:<*someValue*>` Hiermee wordt elke gebeurtenis genegeerd die  `*<someValue*`>  `user-data` via de  [ `ObservationManager` API] heeft ingesteld (https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/observation/ObservationManager.html#setUserData(java.lang.String).

      Bijvoorbeeld:

      `jcr:lastModified,dc:modified,dc:format,jcr:lastModifiedBy,imageMap,event-user-data:changedByWorkflowProcess`

      Deze functie kan worden gebruikt om wijzigingen te negeren die door een ander workflowproces worden veroorzaakt door het uitsluitingsitem toe te voegen:

      `event-user-data:changedByWorkflowProcess`





1. Selecteer **Maken** om de draagtas te maken en terug te keren naar de console.

   Zodra de juiste gebeurtenis plaatsvindt, wordt de starter geactiveerd en wordt de workflow gestart.

## Een opstartconfiguratie beheren {#managing-a-launcher-configuration}

Nadat u uw lanceringsconfiguratie hebt gecreeerd kunt u de zelfde console gebruiken om de instantie te selecteren, dan **Eigenschappen van de Mening** (en hen uit te geven) of **Schrapping**.
