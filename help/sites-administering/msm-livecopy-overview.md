---
title: Console voor live kopiëren
seo-title: Console voor live kopiëren
description: Leer meer over de grondbeginselen van de Live Copy-overzichtsconsole.
seo-description: Leer meer over de grondbeginselen van de Live Copy-overzichtsconsole.
uuid: 6b1841ec-950e-455b-9b30-b5f5050a67b8
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 3763e985-7dd8-47fd-bfdf-2368b424c270
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Console voor live kopiëren{#live-copy-overview-console}

Met het overzicht **van** Live kopie kunt u:

* Overerving op een site weergeven/beheren:

   * De boomstructuur en de bijbehorende structuur van de live kopie samen met de overervingsstatus weergeven
   * de overervingsstatus wijzigen; onderbreek, hervat bijvoorbeeld
   * Vervagen en eigenschappen van actieve kopieën weergeven

* Uitrollen uitvoeren, acties

## Het Live Copy-overzicht openen {#opening-the-live-copy-overview}

U kunt het Live Copy-overzicht openen via het volgende:

* [Referenties in het zijpaneel van een blauwdrukpagina (Sites-console)](#opening-live-copy-overview-references-for-a-blueprint-page)
* [Eigenschappen van een blauwdrukpagina](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Overzicht van Live kopie openen - verwijzingen voor een vervagingspagina {#opening-live-copy-overview-references-for-a-blueprint-page}

Het overzicht **van** Actieve kopie kan worden geopend vanuit het zijpaneel **Referenties** van de **Sites** -console:

1. Navigeer in de **Sites** -console [naar de blauwdrukpagina en selecteer deze](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open het deelvenster **[Verwijzingen](/help/sites-authoring/basic-handling.md#references)**en selecteer **Actieve kopieën**.

   ![chlimage_1-359](assets/chlimage_1-359.png)

   >[!NOTE]
   >
   >U kunt Referenties ook eerst openen en vervolgens de blauwdruk selecteren.

1. Selecteer Overzicht **van** Actieve kopie om het overzicht van alle actieve kopieën met betrekking tot de geselecteerde blauwdruk weer te geven en te gebruiken.
1. Gebruik **Sluiten** om weg te gaan en aan de console van **Plaatsen** terug te keren.

### Live Copy-overzicht openen - Eigenschappen van een vervagingspagina {#opening-live-copy-overview-properties-of-a-blueprint-page}

Het overzicht **van** Actieve kopie kan worden geopend wanneer u de eigenschappen van een pagina met een blauwdruk bekijkt:

1. Open **Eigenschappen** voor de juiste blauwdrukpagina.
1. Open het tabblad **Vervagen** . De optie Overzicht **van** actieve kopie wordt weergegeven op de bovenste werkbalk:

   ![chlimage_1-360](assets/chlimage_1-360.png)

1. Selecteer Overzicht **van** Actieve kopie om het overzicht van alle actieve kopieën met betrekking tot de huidige blauwdruk weer te geven en te gebruiken.

   >[!NOTE]
   >
   >Zie voor meer informatie ook het [LiveCopy-statusbericht van het Knowledge Base-artikel - Up-to-date/Green/In Sync](https://helpx.adobe.com/experience-manager/kb/livecopy-status-message---up-to-date-green-in-sync.html).

1. Gebruik **Sluiten** om weg te gaan en aan de console van **Plaatsen** terug te keren.

## Het Live Copy-overzicht gebruiken {#using-the-live-copy-overview}

Het **Live Copy-overzicht** kan ook worden gebruikt om acties uit te voeren voor de actieve kopie:

1. Open het **Live Copy-overzicht**.
1. Selecteer de vereiste blauwdruk of pagina voor live kopiëren. De werkbalk wordt bijgewerkt en toont de beschikbare acties. Welke [acties](/help/sites-administering/msm.md#terms-used) beschikbaar zijn, is afhankelijk van de vraag of u een [blauwdruk](#actions-for-a-blueprint-page) of een pagina met [live kopieën](#actions-for-a-live-copy-page) selecteert:

### Handelingen voor een vervagingspagina {#actions-for-a-blueprint-page}

Wanneer u een blauwdrukpagina selecteert, zijn de volgende acties beschikbaar:

![chlimage_1-361](assets/chlimage_1-361.png)

* Bewerken

   * Open de pagina met de blauwdruk om deze te bewerken.

* [Uitrol](/help/sites-administering/msm.md#rollout-and-synchronize)

   * Voer een rollout uit om wijzigingen van de bron naar de livecopy te duwen.

### Handelingen voor een Live Copy-pagina {#actions-for-a-live-copy-page}

Wanneer u een pagina voor live kopiëren selecteert, zijn de volgende acties beschikbaar:

![chlimage_1-362](assets/chlimage_1-362.png)

* Bewerken

   * Open de pagina voor live kopiëren voor bewerken.

* [Relationistatiestatus](#relationship-status)

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

## Relationistatiestatus {#relationship-status}

De **console van de Status** van de Verhouding heeft twee lusjes die een waaier van functionaliteit verstrekken:

* [Relatie statusinformatie](#relationship-status-information)
* [Informatie over live kopiëren](#live-copy-information)

### Relatie statusinformatie {#relationship-status-information}

Dit tabblad bevat gedetailleerde informatie over de status van de relatie tussen de blauwdruk en de live kopie:

![chlimage_1-363](assets/chlimage_1-363.png)

### Informatie over live kopiëren {#live-copy-information}

Op dit tabblad kunt u de configuratie van de live kopie weergeven en bewerken:

![chlimage_1-364](assets/chlimage_1-364.png)

