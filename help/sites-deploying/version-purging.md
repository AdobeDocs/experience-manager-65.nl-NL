---
title: Versie leegmaken
description: In dit artikel worden de beschikbare opties voor versiereiniging beschreven.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
exl-id: 6f0b1951-bdda-475f-b6c0-bc18de082b7c
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# Versie leegmaken{#version-purging}

In een standaardinstallatie maakt Adobe Experience Manager (AEM) een versie van een pagina of knooppunt wanneer u een pagina activeert nadat u de inhoud hebt bijgewerkt.

>[!NOTE]
>
>Als de inhoud niet wordt gewijzigd, wordt het bericht weergegeven dat de pagina is geactiveerd, maar er wordt geen nieuwe versie gemaakt.

U kunt op verzoek extra versies maken met de **Versioning** tabblad van het hulpwerkje. Deze versies worden opgeslagen in de opslagplaats en kunnen, indien nodig, worden hersteld.

Deze versies worden nooit gewist, zodat de grootte van de opslagplaats in tijd groeit en daarom moet worden beheerd.

AEM wordt geleverd met verschillende mechanismen om u te helpen uw opslagplaats te beheren:

* de [Versiebeheer](#version-manager)
Dit kan worden gevormd om oude versies te zuiveren wanneer de nieuwe versies worden gecreeerd.

* de [Purperen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) tool Dit wordt gebruikt als onderdeel van het bewaken en onderhouden van uw opslagplaats.
Het laat u tussenbeide komen om oude versies van een knoop, of een hiërarchie van knopen, volgens deze parameters te verwijderen:

   * Het maximumaantal versies dat in de gegevensopslagruimte moet worden bewaard.
Wanneer dit aantal wordt overschreden, wordt de oudste versie verwijderd.

   * De maximumleeftijd van versies die in de opslagplaats worden bewaard.
Wanneer de leeftijd van een versie deze waarde overschrijdt, wordt deze uit de opslagplaats verwijderd.

* de [Onderhoudstaken voor versiewissing](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). U kunt de onderhoudstaak van het Leegmaken van de Versie plannen om oude versies automatisch te schrappen. Dit minimaliseert daarom de noodzaak om handmatig de gereedschappen voor het wissen van versies te gebruiken.

>[!CAUTION]
>
>Als u de grootte van de opslagplaats wilt optimaliseren, voert u de versieopruimingstaak regelmatig uit. De taak zou buiten kantooruren moeten worden gepland wanneer er een beperkte hoeveelheid verkeer is.

## Versiebeheer {#version-manager}

Naast expliciete zuivering door het zuiveringshulpmiddel te gebruiken, kan de Manager van de Versie worden gevormd om oude versies te zuiveren wanneer de nieuwe versies worden gecreeerd.

Om de Manager van de Versie te vormen, [een configuratie maken](/help/sites-deploying/configuring-osgi.md) voor:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

De volgende opties zijn beschikbaar:

* `versionmanager.createVersionOnActivation` (Boolean, standaard: true) Geeft aan of een versie moet worden gemaakt wanneer pagina&#39;s worden geactiveerd.
Een versie wordt gecreeerd tenzij de replicatieagent wordt gevormd om de verwezenlijking van versies te onderdrukken, die door de Manager van de Versie wordt gerespecteerd.
Er wordt alleen een versie gemaakt als de activering plaatsvindt op een pad dat zich bevindt in `versionmanager.ivPaths` (zie hieronder).

* `versionmanager.ivPaths`(String[], standaard: `{"/"}`) Geeft de paden aan waarop impliciet versies worden gemaakt bij activering als `versionmanager.createVersionOnActivation` is ingesteld op true.

* `versionmanager.purgingEnabled` (Booleaanse waarde, standaard: false) Hiermee wordt gedefinieerd of leegmaken moet worden ingeschakeld wanneer nieuwe versies worden gemaakt.

* `versionmanager.purgePaths` (String[], standaard: {&quot;/content&quot;}) Hiermee geeft u op op welke paden naar purge versies moeten worden gebruikt wanneer nieuwe versies worden gemaakt.

* `versionmanager.maxAgeDays` (int, gebrek: 30) Bij versie zuivering, wordt om het even welke versie ouder dan de gevormde waarde verwijderd. Als de waarde kleiner is dan 1, wordt het leegmaken niet uitgevoerd op basis van de leeftijd van de versie.

* `versionmanager.maxNumberVersions` (int, standaard 5) Bij het opschonen van versies wordt elke versie die ouder is dan de n-de nieuwste versie verwijderd. Als de waarde kleiner is dan 1, wordt het leegmaken niet uitgevoerd op basis van het aantal versies.

* `versionmanager.minNumberVersions` (int, gebrek 0) het minimumaantal versies die ongeacht de leeftijd worden gehouden. Als de waarde is ingesteld op een waarde kleiner dan 1, blijft er geen minimumaantal versies behouden.

>[!NOTE]
>
>Het wordt niet aanbevolen om veel versies in de opslagplaats te houden. Dus wanneer u de versiereinigingsbewerking configureert, moet u er rekening mee houden dat u niet te veel versies van de opschoning wilt uitsluiten, anders wordt de grootte van de opslagplaats niet op de juiste wijze geoptimaliseerd. Als u een groot aantal versies door bedrijfsvereisten houdt, contacteer de steun van de Adobe om alternatieve manieren te vinden om de bewaarplaatgrootte te optimaliseren.

### Bewaaropties combineren {#combining-retention-options}

De opties die bepalen hoe versies behouden moeten blijven ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), kan worden gecombineerd afhankelijk van uw vereisten.

Als u bijvoorbeeld het maximumaantal versies definieert dat u wilt behouden EN de oudste versie die u wilt behouden:

* Instellen:

   * `maxNumberVersions` = 7

   * `maxAgeDays` = 30

* Met:

   * In de afgelopen 60 dagen zijn tien versies gemaakt
   * Drie van deze versies zijn in de afgelopen 30 dagen gemaakt

* Dit betekent dat:

   * De laatste drie versies blijven behouden

Als u bijvoorbeeld het maximum EN minimum aantal versies definieert dat behouden moet blijven EN de oudste versie die behouden moet blijven:

* Instellen:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Met:

   * Vijf versies werden 60 dagen geleden gemaakt

* Dit betekent dat:

   * Drie versies blijven behouden

## Versies wissen {#purge-versions-tool}

De [Purperen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) is bedoeld voor het verwijderen van de versies van een knooppunt of een hiërarchie van knooppunten in uw opslagplaats. Het belangrijkste doel is om u te helpen de grootte van uw opslagplaats te verminderen door oude versies van uw knopen te verwijderen.
