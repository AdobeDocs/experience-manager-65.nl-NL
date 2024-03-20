---
title: Workflows toepassen op inhoudspagina's
description: Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina's. Het is ook mogelijk om meerdere workflows toe te passen.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: e00da2b3-046a-4d93-aed0-07dd8c66899f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 5%

---

# Workflows toepassen op pagina&#39;s{#applying-workflows-to-pages}

Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina&#39;s. Het is ook mogelijk om meerdere workflows toe te passen.

Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.
U kunt elke workflow toepassen (waartoe u toegang hebt, zoals is toegewezen door uw AEM-beheerder).
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren.
* De nuttige werkstroom. Dit kunnen een of meer pagina&#39;s zijn.

Workflows kunnen worden gestart vanaf:

* [de Sites-console](#starting-a-workflow-from-the-sites-console).
* [bij het bewerken van een pagina, uit paginagegevens](#starting-a-workflow-from-the-page-editor).

>[!NOTE]
>
>Zie ook:
>
>* [Workflows toepassen op DAM-elementen](/help/assets/assets-workflow.md).
>* [Werken met projectworkflows](/help/sites-authoring/projects-with-workflows.md).
>

>[!NOTE]
>
>AEM beheerders kunnen [workflows starten met verschillende andere methoden](/help/sites-administering/workflows-starting.md).

## Een workflow starten vanuit de siteconsole {#starting-a-workflow-from-the-sites-console}

U kunt een workflow starten vanuit:

* [De optie Maken op de werkbalk Sites](#starting-a-workflow-from-the-sites-toolbar).
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

In beide gevallen moet u:

* [Geef de workflowdetails op in de wizard Workflow maken](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten op de werkbalk Sites {#starting-a-workflow-from-the-sites-toolbar}

U kunt een workflow starten op de werkbalk van het dialoogvenster **Sites** console:

1. Navigeer naar de gewenste pagina en selecteer deze.

1. Van de **Maken** in de werkbalk die u nu kunt selecteren **Workflow**.

   ![screen_shot_2019-03-06at121237pm](assets/screen_shot_2019-03-06at121237pm.png)

1. De **Workflow maken** wizard helpt u [de workflowdetails opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten vanuit de tijdlijn {#starting-a-workflow-from-the-timeline}

Van de **Tijdlijn** u kunt een workflow starten die op de geselecteerde bron moet worden toegepast.

1. [Selecteer de bron](/help/sites-authoring/basic-handling.md#viewingandselectingyourresources) en open [Tijdlijn](/help/sites-authoring/basic-handling.md#timeline) (U kunt Tijdlijn openen en vervolgens de bron selecteren).
1. De pijlpunt op het veld Opmerking kan worden gebruikt om **Workflow starten**:

   ![screen-shot_2019-03-05at120026](assets/screen-shot_2019-03-05at120026.png)

1. De **Workflow maken** wizard helpt u [de workflowdetails opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Workflowdetails opgeven in de wizard Workflow maken {#specifying-workflow-details-in-the-create-workflow-wizard}

De **Workflow maken** De wizard helpt u de workflow te selecteren en de vereiste details op te geven.

Na het openen van de **Workflow maken** wizard van:

* [De optie Maken op de werkbalk Sites](#starting-a-workflow-from-the-sites-toolbar).
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

U kunt details specificeren:

1. In de **Eigenschappen** De basisopties van de workflow worden nu gedefinieerd:

   * **Workflowmodel**
   * **Titel werkstroom**

      * U kunt een titel voor dit exemplaar specificeren, om u te helpen het in een later stadium identificeren.

   Afhankelijk van het workflowmodel zijn ook de volgende opties beschikbaar. Hierdoor kan het pakket dat als lading is gemaakt, worden bewaard nadat de workflow is voltooid.

   * **Workflowpakket behouden**
   * **Pakkettitel**

      * U kunt een titel voor het pakket opgeven om het te identificeren.

   >[!NOTE]
   >
   >De **Workflowpakket behouden** Deze optie is beschikbaar wanneer de workflow is geconfigureerd voor [Ondersteuning voor meerdere bronnen](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) en er zijn meerdere bronnen geselecteerd.

   Na voltooiing gebruiken **Volgende** om verder te gaan.

   ![wf-52](assets/wf-52.png)

1. In de **Toepassingsgebied** stap die u kunt selecteren:

   * **Inhoud toevoegen** om de [padbrowser](/help/sites-authoring/author-environment-tools.md#path-browser) en selecteer aanvullende bronnen; klik in de browser op **Selecteren** om de inhoud aan de werkstroominstantie toe te voegen.

   * Een bestaande bron voor het weergeven van extra handelingen:

      * **Inclusief onderliggende items** om te specificeren dat de kinderen van die bron in het werkschema zullen worden omvat.
Er wordt een dialoogvenster geopend waarin u de selectie kunt verfijnen op basis van:

         * Alleen directe kinderen opnemen.
         * Alleen gewijzigde pagina&#39;s opnemen.
         * Alleen al gepubliceerde pagina&#39;s opnemen.

        Alle opgegeven onderliggende items worden toegevoegd aan de lijst met bronnen waarop de workflow van toepassing is.

      * **Selectie verwijderen** om die bron uit de workflow te verwijderen.

   ![wf-53](assets/wf-53.png)

   >[!NOTE]
   >
   >Als u aanvullende resources toevoegt, kunt u **Terug** gebruiken om de instelling voor **Workflowpakket behouden** aan te passen in de stap **Eigenschappen**.

1. Gebruiken **Maken** om de wizard te sluiten en de instantie van de workflow te maken. Een bericht wordt getoond in de console van Plaatsen.

## Een workflow starten vanuit de Pagina-editor {#starting-a-workflow-from-the-page-editor}

Als u een pagina bewerkt, kunt u **Pagina-informatie** op de werkbalk. Het vervolgkeuzemenu heeft de optie **Starten in workflow**. Hiermee wordt een dialoogvenster geopend waarin u de vereiste workflow kunt opgeven, zo nodig met een titel:

![wf-54](assets/wf-54.png)
