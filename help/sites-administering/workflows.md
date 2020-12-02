---
title: Workflows beheren
seo-title: Workflows beheren
description: Leer hoe u workflows in AEM beheert.
seo-description: Leer hoe u workflows in AEM beheert.
uuid: d000a13c-97cb-4b1b-809e-6c3eb0d675e8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 4b09cd44-434e-4834-bc0d-c9c082a4ba5a
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---


# Workflows beheren{#administering-workflows}

Met workflows kunt u Adobe Experience Manager-activiteiten (AEM) automatiseren. Workflows:

* Bestaat uit een reeks stappen die in een specifieke volgorde worden uitgevoerd.

   * Elke stap voert een afzonderlijke activiteit uit; bijvoorbeeld wachten op invoer van de gebruiker, een pagina activeren of een e-mailbericht verzenden.

* Kan communiceren met middelen in de gegevensopslagruimte, gebruikersaccounts en AEM services.
* Kan ingewikkelde activiteiten coördineren die elk aspect van AEM omvatten.

De bedrijfsprocessen die uw organisatie heeft gevestigd kunnen als werkschema&#39;s worden vertegenwoordigd. Het publicatieproces van website-inhoud omvat bijvoorbeeld doorgaans stappen zoals goedkeuring en aftekening door verschillende belanghebbenden. Deze processen kunnen worden geïmplementeerd als AEM workflows en worden toegepast op inhoudspagina&#39;s en elementen.

* [Workflows starten](/help/sites-administering/workflows-starting.md)
* [Workflowinstanties beheren](/help/sites-administering/workflows-administering.md)
* [Toegang tot werkstromen beheren](/help/sites-administering/workflows-managing.md)

>[!NOTE]
>
>Zie voor meer informatie:
>
>* Workflows toepassen en deelnemen aan workflows: [Werken met Workflows](/help/sites-authoring/workflows.md).
>* Workflowmodellen maken en workflowfunctionaliteit uitbreiden: [Workflows ontwikkelen en uitbreiden](/help/sites-developing/workflows.md).
>* De prestaties verbeteren van workflows die gebruikmaken van aanzienlijke serverresources: [Gelijktijdige workflowverwerking](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing).

>



## Workflowmodellen en instanties {#workflow-models-and-instances}

[De ](/help/sites-developing/workflows.md#model) modellen van het werkschema in AEM zijn de vertegenwoordiging en de implementatie van bedrijfsprocessen:

* Doorgaans handelen ze op pagina&#39;s of elementen om een specifiek resultaat te bereiken.
* Deze pagina&#39;s en/of middelen worden de werkstroomlading genoemd.
* De modellen van het werkschema bestaan uit een reeks stappen die een specifieke taak uitvoeren.
* De lading wordt overgegaan van stap tot stap aangezien het werkschema vordert.

Wanneer een workflowmodel wordt gestart (uitgevoerd), wordt een workflowinstantie gemaakt. Een workflowmodel kan meerdere keren worden gestart, telkens wanneer een afzonderlijke werkstroominstantie wordt gegenereerd. Voor elke instantie worden de stappen uitgevoerd die in het workflowmodel worden gedefinieerd.

>[!CAUTION]
>
>De uitgevoerde stappen zijn die die door het werkschemamodel *op het tijdstip worden bepaald de instantie wordt geproduceerd*. Zie [Workflows ontwikkelen](/help/sites-developing/workflows.md#model) voor meer informatie.

De instanties van het werkschema vorderen door de volgende levenscyclus:

1. Het workflowmodel wordt gestart en er wordt een workflowinstantie gemaakt en uitgevoerd.

   1. De lading van de werkschemainstantie wordt geïdentificeerd wanneer het model wordt begonnen.
   1. De instantie is in feite een kopie van het model (zoals op het moment van het maken).
   1. AEM auteurs, beheerders of services kunnen workflowmodellen starten.

1. De eerste stap van het workflowmodel wordt uitgevoerd.
1. De stap is voltooid en de workflowengine gebruikt het model om te bepalen welke volgende stap moet worden uitgevoerd.
1. De volgende stappen in het workflowmodel worden uitgevoerd en voltooid.
1. Wanneer de laatste stap is voltooid, wordt de werkstroominstantie voltooid en daarom gearchiveerd.

Veel handige workflowmodellen worden AEM. Bovendien kunnen de ontwikkelaars in uw organisatie modellen van het douanewerkschema tot stand brengen, die aan de specifieke behoeften van uw bedrijfsprocessen worden aangepast.

## Workflowstappen {#workflow-steps}

Wanneer workflowstappen worden uitgevoerd, worden deze gekoppeld aan een workflowinstantie. De geschiedenis van een werkstroominstantie bevat informatie over elke stap die voor de instantie is uitgevoerd. Deze informatie is nuttig voor het onderzoeken van problemen die tijdens uitvoering voorkomen.

Een gebruiker of een service voert workflowstappen uit, afhankelijk van het type stap:

* Wanneer een gebruiker een stap uitvoert, worden zij toegewezen een het werkpunt dat in hun Inbox wordt geplaatst. De gebruiker is verantwoordelijk voor het handmatig voltooien van de stap, zodat de workflowinstantie verdergaat.
* Wanneer een service een stap uitvoert, gaat de workflowinstantie na voltooiing automatisch naar de volgende stap.

>[!NOTE]
>
>Als een fout voorkomt, zou de dienst/stapimplementatie gedrag voor een foutenscenario moeten behandelen. De workflow-engine zelf probeert de taak opnieuw uit, registreert vervolgens een fout en stopt de instantie.

## Workflowstatus en handelingen {#workflow-status-and-actions}

Een werkstroom kan een van de volgende status hebben:

* **UITVOEREN**: De werkstroominstantie wordt uitgevoerd.
* **VOLTOOID**: De werkstroominstantie is beëindigd.

* **GESCHORST**: De werkstroominstantie is opgeschort.
* **GEABORTEERD**: De werkstroominstantie is beëindigd.
* **STAAL**: Voor de voortgang van de werkstroominstantie moet een achtergrondtaak worden uitgevoerd, maar de taak kan niet in het systeem worden gevonden. Deze situatie kan zich voordoen wanneer er een fout optreedt bij het uitvoeren van de workflow.

>[!NOTE]
>
>Wanneer de uitvoering van een Stap van het Proces in fouten resulteert, verschijnt de stap in Inbox van de beheerder en de werkschemastatus is **RUNNING**.

Afhankelijk van de huidige status kunt u acties uitvoeren op het uitvoeren van workflowinstanties wanneer u moet ingrijpen in de normale voortgang van een workflowinstantie:

* **Onderbreken**: Hiermee wordt de uitvoering van de workflow tijdelijk gestopt. Opschorsen is handig in uitzonderlijke gevallen waarin u niet wilt dat de workflow wordt voortgezet, bijvoorbeeld voor onderhoud. Met Opschorting wijzigt u de status van de workflow in Opgeschort.
* **Hervatten**: Hiermee herstart u een stilgezette workflow op hetzelfde uitvoerpunt waar deze werd onderbroken, met dezelfde configuratie.
* **Beëindigen**: Beëindigt de workflowuitvoering en wijzigt de status in  **ABORTED**. Een afgebroken werkstroominstantie kan niet opnieuw worden gestart.

