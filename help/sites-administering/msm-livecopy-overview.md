---
title: Console voor live kopiëren
description: Leer meer over de grondbeginselen van de Live Copy-overzichtsconsole.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
feature: Multi Site Manager
exl-id: 0c3488bd-5f32-4956-882c-93326a45b379
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Console voor live kopiëren{#live-copy-overview-console}

Het **Levende Overzicht van het Exemplaar** laat u toe:

* Overerving op een site weergeven/beheren:

   * De boomstructuur en de bijbehorende structuur van de live kopie samen met de overervingsstatus weergeven
   * Wijzig de overervingsstatus, bijvoorbeeld de status Opschorten, Hervatten
   * Vervagen en eigenschappen van actieve kopieën weergeven

* Uitrollen uitvoeren, acties

## Het Live Copy-overzicht openen {#opening-the-live-copy-overview}

U kunt het Live Copy-overzicht openen via het volgende:

* [Referenties in het zijpaneel van een blauwdrukpagina (Sites-console)](#opening-live-copy-overview-references-for-a-blueprint-page)
* [Eigenschappen van een blauwdrukpagina](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Overzicht van Live kopie openen - verwijzingen voor een vervagingspagina {#opening-live-copy-overview-references-for-a-blueprint-page}

Het **Levende Overzicht van het Exemplaar** kan van het **3} zijpaneel van Verwijzingen van de** Sites **console worden geopend:**

1. In de **console van Plaatsen**, [ navigeer aan uw blauwdruk pagina en selecteer het ](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open het **[paneel van Verwijzingen](/help/sites-authoring/basic-handling.md#references)** en selecteer **Levende Exemplaren**.

   ![ het paneel van Verwijzingen - Levende exemplaren ](assets/chlimage_1-359.png)

   >[!NOTE]
   >
   >U kunt Referenties ook eerst openen en vervolgens de blauwdruk selecteren.

1. Selecteer **Levend Overzicht van het Exemplaar** om het overzicht van alle levende exemplaren met betrekking tot de geselecteerde blauwdruk te tonen en te gebruiken.
1. Het gebruik **dicht** om weg te gaan en aan de **console van Plaatsen** terug te keren.

### Live Copy-overzicht openen - Eigenschappen van een vervagingspagina {#opening-live-copy-overview-properties-of-a-blueprint-page}

Het **Levende Overzicht van het Exemplaar** kan worden geopend wanneer het bekijken van eigenschappen van een blauwdrukpagina:

1. Open **Eigenschappen** voor de aangewezen blauwdrukpagina.
1. Open het **lusje van de Vervaging** - de **Levende optie van het Overzicht van het Exemplaar** wordt getoond in de hoogste toolbar:

   ![ lusje van de Vervaging - het Levende Overzicht van het Exemplaar ](assets/chlimage_1-360.png)

1. Selecteer **Levend Overzicht van het Exemplaar** om het overzicht van alle levende exemplaren met betrekking tot de huidige blauwdruk te tonen en te gebruiken.

   >[!NOTE]
   >
   >Voor verdere details zie ook het artikel van de Kennisbank [ Livecopy statusbericht - Up-to-date/Green/In Synchronisatie ](https://helpx.adobe.com/experience-manager/kb/livecopy-status-message---up-to-date-green-in-sync.html).

1. Het gebruik **dicht** om weg te gaan en aan de **console van Plaatsen** terug te keren.

## Het Live Copy-overzicht gebruiken {#using-the-live-copy-overview}

Het **Levende Overzicht van het Exemplaar** kan ook worden gebruikt om acties op het levende exemplaar uit te voeren:

1. Open het **Levende Overzicht van het Exemplaar**.
1. Selecteer de vereiste blauwdruk of pagina voor live kopiëren. De werkbalk wordt bijgewerkt en toont de beschikbare acties. De [ beschikbare acties ](/help/sites-administering/msm.md#terms-used) hangen van af of u a [ blauwdruk ](#actions-for-a-blueprint-page) of [ levende exemplaar ](#actions-for-a-live-copy-page) pagina selecteert:

### Handelingen voor een vervagingspagina {#actions-for-a-blueprint-page}

Wanneer u een blauwdrukpagina selecteert, zijn de volgende acties beschikbaar:

![ Geselecteerde Vervaging - beschikbare acties ](assets/chlimage_1-361.png)

* Bewerken

   * Open de pagina met de blauwdruk om deze te bewerken.

* [Uitrol](/help/sites-administering/msm.md#rollout-and-synchronize)

   * Voer een rollout uit om wijzigingen van de bron naar de livecopy te duwen.

### Handelingen voor een Live Copy-pagina {#actions-for-a-live-copy-page}

Wanneer u een pagina voor live kopiëren selecteert, zijn de volgende acties beschikbaar:

![ Levende geselecteerde exemplaarpagina van het exemplaar - beschikbare acties ](assets/chlimage_1-362.png)

* Bewerken

   * Open de pagina voor live kopiëren voor bewerken.

* [Relatie status](#relationship-status)

   * Informatie weergeven over de status en overerving.

* [Synchroniseren](/help/sites-administering/msm.md#rollout-and-synchronize)

   * Synchroniseer een live kopie om wijzigingen van de bron naar de livecopy over te brengen.

* [Herstellen](/help/sites-administering/msm-livecopy.md#resetting-a-live-copy-page)

   * Stel een live kopieerpagina opnieuw in om alle overervingsannuleringen te verwijderen en de pagina terug te brengen naar dezelfde status als de bronpagina.

* [Onderbreken](/help/sites-administering/msm.md#suspending-and-cancelling-inheritance-and-synchronization)

   * Hiermee deactiveert u tijdelijk de live relatie tussen een live kopie en de bijbehorende blauwdrukpagina.

* [Hervatten](/help/sites-administering/msm-livecopy.md#resuming-inheritance-for-a-page)

   * Met Hervatten kunt u een geschorste relatie herstellen.

* [Loskoppelen](/help/sites-administering/msm.md#detaching-a-live-copy)

   * Hiermee verwijdert u permanent de live relatie tussen een live kopie en de bijbehorende blauwdrukpagina.

## Relatie status {#relationship-status}

De **console van de Status van de Verhouding** heeft twee lusjes die een waaier van functionaliteit verstrekken:

* [Relatie statusinformatie](#relationship-status-information)
* [Informatie over live kopiëren](#live-copy-information)

### Relatie statusinformatie {#relationship-status-information}

Dit tabblad bevat gedetailleerde informatie over de status van de relatie tussen de blauwdruk en de live kopie:

![ de statusinformatie van de Verhouding ](assets/chlimage_1-363.png)

### Informatie over live kopiëren {#live-copy-information}

Op dit tabblad kunt u de configuratie van de live kopie weergeven en bewerken:

![ Levende exemplaarinformatie ](assets/chlimage_1-364.png)
