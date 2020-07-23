---
title: Workflows toepassen op pagina's
seo-title: Workflows toepassen op pagina's
description: Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina's. het is ook mogelijk meerdere werkschema's toe te passen.
seo-description: Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina's. het is ook mogelijk meerdere werkschema's toe te passen.
uuid: 652d9a23-907d-43ad-9eef-7ab1d07918cd
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 6472dc94-96e0-4286-8f86-d85726cc843c
docset: aem65
translation-type: tm+mt
source-git-commit: 611743cc4144f99968845093b3903fe7df8bf9d9
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 12%

---


# Workflows toepassen op pagina&#39;s{#applying-workflows-to-pages}

Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina&#39;s. het is ook mogelijk meerdere werkstromen toe te passen .

Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.
U kunt elke workflow toepassen (waartoe u toegang hebt, zoals is toegewezen door uw AEM-beheerder).
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren.
* de workflow-lading; dit kan een of meer pagina&#39;s zijn.

Workflows kunnen worden gestart vanaf:

* [de Sites-console](#starting-a-workflow-from-the-sites-console).
* [bij het bewerken van een pagina, vanuit Pagina-informatie](#starting-a-workflow-from-the-page-editor).

>[!NOTE]
>
>Zie ook:
>
>* [Hoe te om werkschema&#39;s op activa](/help/assets/assets-workflow.md)toe te passen DAM.
>* [Werken met projectworkflows](/help/sites-authoring/projects-with-workflows.md).

>



>[!NOTE]
>
>AEM-beheerders kunnen workflows [starten met verschillende andere methoden](/help/sites-administering/workflows-starting.md).

## Een workflow starten vanuit de siteconsole {#starting-a-workflow-from-the-sites-console}

U kunt een workflow starten vanuit:

* [Kies de optie Maken op de werkbalk](#starting-a-workflow-from-the-sites-toolbar)Sites.
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

In beide gevallen moet u:

* [Geef de workflowdetails op in de wizard](#specifying-workflow-details-in-the-create-workflow-wizard)Workflow maken.

### Een workflow starten op de werkbalk Sites {#starting-a-workflow-from-the-sites-toolbar}

U kunt een workflow starten op de werkbalk van de **Sites** -console:

1. Navigeer naar de gewenste pagina en selecteer deze.

1. Met de optie **Maken** op de werkbalk kunt u nu **Workflow** selecteren.

   ![screen_shot_2019-03-06at121237pm](assets/screen_shot_2019-03-06at121237pm.png)

1. Met de wizard **Workflow** maken kunt u de workflowdetails [opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten vanuit de tijdlijn {#starting-a-workflow-from-the-timeline}

Vanuit de **tijdlijn** kunt u een workflow starten die op de geselecteerde bron moet worden toegepast.

1. [Selecteer de bron](/help/sites-authoring/basic-handling.md#viewingandselectingyourresources) en open [tijdlijn](/help/sites-authoring/basic-handling.md#timeline) (of open tijdlijn en selecteer de bron).
1. De pijlpunt door het commentaargebied kan worden gebruikt om het Werkschema **van het** Begin te onthullen:

   ![screen-shot_2019-03-05at120026](assets/screen-shot_2019-03-05at120026.png)

1. Met de wizard **Workflow** maken kunt u de workflowdetails [opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Workflowdetails opgeven in de wizard Workflow maken {#specifying-workflow-details-in-the-create-workflow-wizard}

Met de wizard **Workflow** maken kunt u de workflow selecteren en de vereiste details opgeven.

Nadat u de wizard **Workflow** maken hebt geopend vanuit:

* [Kies de optie Maken op de werkbalk](#starting-a-workflow-from-the-sites-toolbar)Sites.
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

U kunt details opgeven:

1. In de stap **Eigenschappen** worden de basisopties van de workflow gedefinieerd:

   * **Workflowmodel**
   * **Titel werkstroom**

      * U kunt een titel voor dit exemplaar specificeren, om u te helpen het in een later stadium identificeren.

   Afhankelijk van het workflowmodel zijn ook de volgende opties beschikbaar. Hierdoor kan het pakket dat als lading is gemaakt, worden bewaard nadat de workflow is voltooid.

   * **Workflowpakket behouden**
   * **Pakkettitel**

      * U kunt een titel voor het pakket opgeven om het te identificeren.
   >[!NOTE]
   >
   >De optie **Workflowpakket bijhouden** is beschikbaar wanneer de workflow is geconfigureerd voor ondersteuning van meerdere resources en er meerdere resources zijn geselecteerd.[](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support)

   Als u klaar bent, gebruikt u **Volgende** om door te gaan.

   ![wf-52](assets/wf-52.png)

1. In de stap **Bereik** kunt u selecteren:

   * **Voeg Inhoud** toe om de [padbrowser](/help/sites-authoring/author-environment-tools.md#path-browser) te openen en selecteer aanvullende bronnen. Klik in de browser op **Selecteren** of tik op Selecteren om de inhoud aan de werkstroominstantie toe te voegen.

   * Een bestaande bron voor het weergeven van extra handelingen:

      * **Neem onderliggende elementen** op om op te geven dat onderliggende elementen van die bron worden opgenomen in de workflow.
Er wordt een dialoogvenster geopend waarin u de selectie kunt verfijnen op basis van:

         * Alleen directe kinderen opnemen.
         * Alleen gewijzigde pagina&#39;s opnemen.
         * Alleen al gepubliceerde pagina&#39;s opnemen.

         Alle opgegeven onderliggende items worden toegevoegd aan de lijst met bronnen waarop de workflow van toepassing is.

      * **Selectie** verwijderen om die bron uit de workflow te verwijderen.

   ![wf-53](assets/wf-53.png)

   >[!NOTE]
   >
   >Als u aanvullende resources toevoegt, kunt u **Terug** gebruiken om de instelling voor **Workflowpakket behouden** aan te passen in de stap **Eigenschappen**.

1. Gebruik **Maken** om de wizard te sluiten en de instantie van de workflow te maken. Een bericht wordt getoond in de console van Plaatsen.

## Een workflow starten vanuit de Pagina-editor {#starting-a-workflow-from-the-page-editor}

Als u een pagina bewerkt, kunt u op de werkbalk **Pagina-informatie** selecteren. Het vervolgkeuzemenu heeft de optie **Start in Workflow**. Hiermee wordt een dialoogvenster geopend waarin u de vereiste workflow kunt opgeven, en desgewenst een titel:

![wf-54](assets/wf-54.png)
