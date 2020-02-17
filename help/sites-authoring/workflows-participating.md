---
title: Deelnemen aan workflows
seo-title: Deelnemen aan workflows
description: Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert.
seo-description: Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert.
uuid: 15d56bcc-1e84-4cc0-8b71-7fb906cd7ff7
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: f170613c-329e-446b-9ac3-350615f1bfb6
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50

---


# Deelnemen aan workflows{#participating-in-workflows}

Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert. De werkstroom selecteert een gebruiker of groep om de activiteit uit te voeren en wijst een het werkpunt aan die persoon of groep toe. De gebruiker ontvangt een melding en kan vervolgens de juiste actie ondernemen:

* [Meldingen weergeven](#notifications-of-available-workflow-actions)
* [Een deelnemersstap voltooien](#completing-a-participant-step)
* [Een deelnemersstap delegeren](#delegating-a-participant-step)
* [Stap terug op een Stap van de Deelnemer uitvoeren](#performing-step-back-on-a-participant-step)
* [Open een workflowitem om details weer te geven (en om handelingen uit te voeren)](#opening-a-workflow-item-to-view-details-and-take-actions)
* [Bekijk de Werkstroom Payload (Meerdere Middelen)](#viewing-the-workflow-payload-multiple-resources)

## Meldingen van beschikbare workflowacties {#notifications-of-available-workflow-actions}

Wanneer u een tijdelijk onderdeel hebt toegewezen (bijvoorbeeld Inhoud **** goedkeuren), worden verschillende waarschuwingen en/of meldingen weergegeven:

* De [meldingsindicator](/help/sites-authoring/inbox.md) (werkbalk) wordt verhoogd:

   ![](do-not-localize/wf-57.png)

* Het object wordt aangeboden in het [Postvak](/help/sites-authoring/inbox.md)van je bericht:

   ![wf-58](assets/wf-58.png)

* Wanneer u de pagina-editor gebruikt, wordt de statusbalk weergegeven:

   * de naam van de workflow(en) die op de pagina wordt toegepast; bijvoorbeeld Verzoek om activering.
   * Alle handelingen die beschikbaar zijn voor de huidige gebruiker voor de huidige stap van de workflow. bijvoorbeeld Voltooid, Delegeren, Details weergeven.
   * Het aantal werkstromen dat op de pagina van toepassing is. U kunt:

      * Gebruik de pijlen links/rechts om door de statusinformatie van de verschillende workflows te navigeren.
      * Klik/tik op het daadwerkelijke aantal om een drop-down lijst van alle toepasselijke werkschema&#39;s te openen, dan selecteer het werkschema u in de statusbar wilt tonen.
   ![wf-59](assets/wf-59.png)

   >[!NOTE]
   >
   >De statusbalk is alleen zichtbaar voor gebruikers met workflowbevoegdheden. bijvoorbeeld leden van de `workflow-users` groep.
   >
   >
   >Handelingen worden weergegeven wanneer de huidige gebruiker rechtstreeks betrokken is bij de huidige stap van de workflow.

* Wanneer de **tijdlijn** is geopend voor de bron, wordt de workflowstap weergegeven. Wanneer u op de waarschuwingsbanner klikt of tikt, worden ook de beschikbare acties weergegeven:

   ![screen-shot_2019-03-05at120453](assets/screen-shot_2019-03-05at120453.png)

### Een deelnemersstap voltooien {#completing-a-participant-step}

U kunt een item voltooien zodat de workflow naar de volgende stap kan gaan.

Op deze actie kunt u aangeven:

* **Volgende stap**: de volgende te nemen stap; u kunt uit een lijst selecteren die wordt verstrekt
* **Opmerking**: indien vereist

U kunt een deelnemersstap uitvoeren vanuit:

* [Inbox](#completing-a-participant-step-inbox)
* [De Pagina-editor](#completing-a-participant-step-page-editor)
* [Tijdlijn](#completing-a-participant-step-timeline)
* wanneer u een workflowitem [opent om details](#opening-a-workflow-item-to-view-details-and-take-actions)weer te geven.

#### Een deelnemersstap voltooien - Postvak IN {#completing-a-participant-step-inbox}

Voer de volgende procedure uit om het werkitem te voltooien:

1. Open het **[AEM-vak](/help/sites-authoring/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Voltooid** op de werkbalk.
1. Het dialoogvenster **Werkitem** voltooien wordt geopend. Selecteer de **Volgende Stap** van de drop-down selecteur en voeg een **Commentaar** toe indien nodig.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een stap voor een deelnemer voltooien - Pagina-editor {#completing-a-participant-step-page-editor}

Voer de volgende procedure uit om het werkitem te voltooien:

1. Open de [pagina voor bewerking](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Selecteer **Voltooien** in de statusbalk boven in het scherm.
1. Het dialoogvenster **Werkitem** voltooien wordt geopend. Selecteer de **Volgende Stap** van de drop-down selecteur en voeg een **Commentaar** toe indien nodig.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een deelnemersstap voltooien - tijdlijn {#completing-a-participant-step-timeline}

U kunt ook de tijdlijn gebruiken om een stap te voltooien en uit te voeren:

1. Selecteer de gewenste pagina en open de **tijdlijn** (of open **tijdlijn** en selecteer de pagina):

   ![screen-shot_2019-03-05at120744](assets/screen-shot_2019-03-05at120744.png)

1. Klik of tik op de waarschuwingsbanner om beschikbare handelingen weer te geven. Selecteer **Geavanceerd**:

   ![screen-shot_2019-03-05at120453-1](assets/screen-shot_2019-03-05at120453-1.png)

1. Afhankelijk van de workflow kunt u de volgende stap selecteren:

   ![screen-shot_2019-03-05at120905](assets/screen-shot_2019-03-05at120905.png)

1. Selecteer **Geavanceerd** om de handeling te bevestigen.

### Een deelnemersstap delegeren {#delegating-a-participant-step}

Als een stap aan u is toegewezen, maar om het even welke reden u geen actie kunt ondernemen, kunt u de stap aan een andere gebruiker of een groep delegeren.

De gebruikers die voor delegatie beschikbaar zijn hangen af van wie het het werkpunt werd toegewezen:

* Als het het werkpunt aan een groep werd toegewezen, zijn de groepsleden beschikbaar.
* Als het het werkpunt aan een groep werd toegewezen en dan aan een gebruiker werd afgevaardigd, zijn de groepsleden en de groep beschikbaar.
* Als het het werkpunt aan één enkele gebruiker werd toegewezen, kan het het werkpunt niet worden afgevaardigd.

Op deze actie kunt u aangeven:

* **Gebruiker**: de gebruiker u aan wilt delegeren; u kunt uit een lijst selecteren die wordt verstrekt
* **Opmerking**: indien vereist

U kunt een deelnemersstap delegeren vanuit:

* [Inbox](#delegating-a-participant-step-inbox)
* [De Pagina-editor](#delegating-a-participant-step-page-editor)
* [Tijdlijn](#delegating-a-participant-step-timeline)
* wanneer u een workflowitem [opent om details](#opening-a-workflow-item-to-view-details-and-take-actions)weer te geven.

#### Een deelnemersstap delegeren - Postvak IN {#delegating-a-participant-step-inbox}

Gebruik de volgende procedure om een het werkpunt te delegeren:

1. Open het **[AEM-vak](/help/sites-authoring/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Delegeren** op de werkbalk.
1. Het dialoogvenster wordt geopend. Geef de **gebruiker** op in de keuzelijst (dit kan ook een groep zijn) en voeg zo nodig een **opmerking** toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een deelnemersstap delegeren - Pagina-editor {#delegating-a-participant-step-page-editor}

Gebruik de volgende procedure om een het werkpunt te delegeren:

1. Open de [pagina voor bewerking](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Selecteer **Delegeren** in de statusbalk bovenaan.
1. Het dialoogvenster wordt geopend. Geef de **gebruiker** op in de keuzelijst (dit kan ook een groep zijn) en voeg zo nodig een **opmerking** toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een deelnemersstap delegeren - tijdlijn {#delegating-a-participant-step-timeline}

U kunt de tijdlijn ook gebruiken om een stap te delegeren en/of toe te wijzen:

1. Selecteer de gewenste pagina en open de **tijdlijn** (of open de **tijdlijn** en selecteer de pagina).
1. Klik of tik op de waarschuwingsbanner om beschikbare handelingen weer te geven. Selecteer Toewijzing **wijzigen**:

   ![screen-shot_2019-03-05at120453-2](assets/screen-shot_2019-03-05at120453-2.png)

1. Geef een nieuwe ontvanger op:

   ![screen-shot_2019-03-05at121025](assets/screen-shot_2019-03-05at121025.png)

1. Selecteer **Toewijzen** om de handeling te bevestigen.

### Stap terug op een Stap van de Deelnemer uitvoeren {#performing-step-back-on-a-participant-step}

Als u ontdekt dat een stap, of een reeks stappen, moet worden herhaald kunt u achteruit stappen. Op deze manier kunt u een stap selecteren die eerder in de workflow is opgetreden voor opwerking. De werkstroom keert aan de stap terug u specificeert, dan gaat van daar te werk.

Op deze actie kunt u aangeven:

* **Vorige stap**: de stap waarop moet worden teruggezet; u kunt uit een lijst selecteren die wordt verstrekt
* **Opmerking**: indien vereist

U kunt stap terug op een deelnemersstap van één van beiden uitvoeren:

* [Inbox](#performing-step-back-on-a-participant-step-inbox)
* [De Pagina-editor](#performing-step-back-on-a-participant-step-page-editor)
* [Tijdlijn](#performing-step-back-on-a-participant-step-timeline)
* wanneer u een workflowitem [opent om details](#opening-a-workflow-item-to-view-details-and-take-actions)weer te geven.

#### Het uitvoeren van Stap terug op een Stap van de Deelnemer - Inbox {#performing-step-back-on-a-participant-step-inbox}

Gebruik de volgende procedure om terug te gaan:

1. Open het **[AEM-vak](/help/sites-authoring/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Stap terug** om het dialoogvenster te openen.

1. Geef de **vorige stap** op en voeg zo nodig een **opmerking** toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Stap terug uitvoeren op een Stap van de Deelnemer - de Redacteur van de Pagina {#performing-step-back-on-a-participant-step-page-editor}

Gebruik de volgende procedure om terug te gaan:

1. Open de [pagina voor bewerking](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Selecteer **Stap terug** van de statusbar bij de bovenkant.
1. Geef de **vorige stap** op en voeg zo nodig een **opmerking** toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Stap terug uitvoeren op een Stap van de Deelnemer - Chronologie {#performing-step-back-on-a-participant-step-timeline}

U kunt de tijdlijn ook gebruiken om terug te gaan (stap) naar een vorige stap:

1. Selecteer de gewenste pagina en open de **tijdlijn** (of open de **tijdlijn** en selecteer de pagina).
1. Klik of tik op de waarschuwingsbanner om beschikbare handelingen weer te geven. Selecteer **Terugdraaien**:

   ![screen-shot_2019-03-05at121131](assets/screen-shot_2019-03-05at121131.png)

1. Geef de stap op waarnaar de workflow moet terugkeren:

   ![screen-shot_2019-03-05at121158](assets/screen-shot_2019-03-05at121158.png)

1. Selecteer **Terugdraaien** om de actie te bevestigen.

### Een workflowitem openen om details weer te geven (en handelingen uit te voeren) {#opening-a-workflow-item-to-view-details-and-take-actions}

Bekijk details van het werkstroomonderdeel en voer de juiste handelingen uit.

De workflowdetails worden weergegeven op tabbladen en de juiste acties zijn beschikbaar op de werkbalk:

* **WORKITEM** , tabblad:

   ![wf-72](assets/wf-72.png)

* **Tabblad WORKFLOW-INFO** :

   ![wf-73](assets/wf-73.png)

   Als [de Stages](/help/sites-developing/workflows.md#workflow-stages) van het Werkschema voor het model zijn gevormd, kunt u de vooruitgang volgens deze zien:

   ![wf-107](assets/wf-107.png)

* **Tabblad Opmerkingen** :

   ![wf-75](assets/wf-75.png)

U kunt de details van het werkitem openen vanuit:

* [Inbox](#performing-step-back-on-a-participant-step-inbox)
* [De Pagina-editor](#performing-step-back-on-a-participant-step-page-editor)

#### Workflow Details openen - Postvak IN {#opening-workflow-details-inbox}

U opent als volgt een workflowitem en bekijkt de details:

1. Open het **[AEM-vak](/help/sites-authoring/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Openen** om de informatielusjes te openen.

1. Selecteer zo nodig de gewenste actie, geef details op en bevestig deze met **OK** (of **Annuleren**).
1. Gebruik **Opslaan** of **Annuleren** om af te sluiten.

#### Workflow Details openen - Pagina-editor {#opening-workflow-details-page-editor}

U opent als volgt een workflowitem en bekijkt de details:

1. Open de [pagina voor bewerking](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing).
1. Selecteer Details **van de** Mening van de statusbar om de informatielusjes te openen.

1. Selecteer zo nodig de gewenste actie, geef details op en bevestig deze met **OK** (of **Annuleren**).
1. Gebruik **Opslaan** of **Annuleren** om af te sluiten.

### Het bekijken van de Payload van het Werkschema (Veelvoudige Middelen) {#viewing-the-workflow-payload-multiple-resources}

U kunt details van de lading bekijken verbonden aan de werkschemainstantie. In eerste instantie worden de bronnen in het pakket weergegeven, waarna u de afzonderlijke pagina&#39;s kunt weergeven.

Om de lading, en middelen, van de werkschemainstantie te bekijken:

1. Open het **[AEM-vak](/help/sites-authoring/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Payload** weergeven op de werkbalk om het dialoogvenster te openen.

   Aangezien een workflowpakket slechts een verzameling aanwijzers naar paden in de repository is, kunt u de items hier toevoegen/verwijderen/wijzigen om aan te passen wat er in het workflowpakket naar wordt verwezen. Met de component **Brondefinitie** kunt u nieuwe items toevoegen.

   ![wf-78](assets/wf-78.png)

1. U kunt de koppelingen gebruiken om de afzonderlijke pagina&#39;s te openen.
