---
title: Deelnemen aan workflows
seo-title: Deelnemen aan workflows
description: Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert. De werkstroom selecteert een gebruiker of groep om de activiteit uit te voeren en wijst een het werkpunt aan die persoon of groep toe.
seo-description: Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert. De werkstroom selecteert een gebruiker of groep om de activiteit uit te voeren en wijst een het werkpunt aan die persoon of groep toe.
uuid: 04dcc8f2-dc11-430f-b0ae-47ef2cb069a2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 1d7a4889-82c5-4096-8567-8f66215a8458
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 4%

---


# Deelnemen aan workflows{#participating-in-workflows}

Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert. De werkstroom selecteert een gebruiker of groep om de activiteit uit te voeren en wijst een het werkpunt aan die persoon of groep toe.

## Uw werkitems verwerken {#processing-your-work-items}

U kunt de volgende handelingen uitvoeren om een werkitem te verwerken:

* **Voltooid**

   U kunt een item voltooien zodat de workflow naar de volgende stap kan gaan.

* **Delegeren**

   Als een stap aan u is toegewezen, maar om het even welke reden u geen actie kunt ondernemen, kunt u de stap aan een andere gebruiker of een groep delegeren.

   De gebruikers die voor delegatie beschikbaar zijn hangen af van wie het het werkpunt werd toegewezen:

   * Als het het werkpunt aan een groep werd toegewezen, zijn de groepsleden beschikbaar.
   * Als het het werkpunt aan een groep werd toegewezen en dan aan een gebruiker werd gedelegeerd, zijn de groepsleden en de groep beschikbaar.
   * Als het het werkpunt aan één enkele gebruiker werd toegewezen, kan het het werkpunt niet worden afgevaardigd.

* **Stap terug**

   Als u ontdekt dat een stap, of een reeks stappen, moet worden herhaald kunt u achteruit stappen. Op deze manier kunt u een stap selecteren die eerder in de workflow is opgetreden voor opwerking. De werkstroom keert aan de stap terug u specificeert, dan gaat van daar te werk.

## Deelnemen aan een workflow {#participating-in-a-workflow}

### Meldingen van toegewezen workflowhandelingen {#notifications-of-assigned-workflow-actions}

Wanneer u een werkitem wordt toegewezen (bijvoorbeeld **Inhoud goedkeuren**), worden verschillende waarschuwingen en/of meldingen weergegeven:

* De **Status** kolom van de console van Websites wijst erop wanneer een pagina in een werkschema is:

   ![workflowstatus-1](assets/workflowstatus-1.png)

* Wanneer u, of een groep die u tot behoort, een het werkpunt als deel van een werkschema wordt toegewezen, verschijnt het het werkpunt in uw Inbox van het Werkschema van de AEM.

   ![workflowinbox](assets/workflowinbox.png)

### Een deelnemersstap {#completing-a-participant-step} voltooien

Nadat u de aangegeven actie hebt uitgevoerd, kunt u het werkitem voltooien, zodat de workflow kan worden voortgezet. Voer de volgende procedure uit om het werkitem te voltooien.

1. Selecteer de workflowstap en klik op de knop **Voltooien** in de bovenste navigatiebalk.
1. Selecteer **Volgende stap** in het dialoogvenster dat wordt weergegeven; dat wil zeggen, de volgende stap die moet worden uitgevoerd. In een vervolgkeuzelijst worden alle geschikte doelen weergegeven. U kunt ook een **opmerking** invoeren.

   ![workflowvoltooid](assets/workflowcomplete.png)

   Het aantal vermelde stappen is afhankelijk van het ontwerp van het workflowmodel.

1. Klik **OK** om de handeling te bevestigen.

### Een deelnemersstap {#delegating-a-participant-step} delegeren

Gebruik de volgende procedure om een het werkpunt te delegeren.

1. Klik op de knop **Delegeren** in de bovenste navigatiebalk.
1. In de dialoog, gebruik de drop-down lijst om **Gebruiker** te selecteren om het het werkpunt aan te delegeren. U kunt ook een **Opmerking** toevoegen.

   ![workflowgedelegeerde](assets/workflowdelegate.png)

1. Klik **OK** om de handeling te bevestigen.

### Stap terug op een Stap van de Deelnemer {#performing-step-back-on-a-participant-step} uitvoeren

Gebruik de volgende procedure om terug te gaan.

1. Klik op de knop Stap terug in de bovenste navigatiebalk.
1. Selecteer in het dialoogvenster dat wordt weergegeven de optie Vorige stap; dat wil zeggen, de volgende stap uitvoeren - ook al is het een stap die eerder in de workflow plaatsvindt. In een vervolgkeuzelijst worden alle geschikte doelen weergegeven.

   ![screen_shot_2018-08-10at155325](assets/screen_shot_2018-08-10at155325.jpg)

1. Klik op OK om de handeling te bevestigen.

