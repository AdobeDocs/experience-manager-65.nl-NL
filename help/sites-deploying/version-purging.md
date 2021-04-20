---
title: Versie leegmaken
seo-title: Versie leegmaken
description: In dit artikel worden de beschikbare opties voor versiereiniging beschreven.
seo-description: In dit artikel worden de beschikbare opties voor versiereiniging beschreven.
uuid: a9fa25c7-e60e-4665-a726-99af9aac8f70
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: fb4d7337-7b94-430b-80d2-f1754f823c2b
docset: aem65
feature: Configuring
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# Versie opruimen{#version-purging}

In een standaardinstallatie AEM maakt een nieuwe versie van een pagina of knooppunt wanneer u een pagina activeert nadat u de inhoud hebt bijgewerkt.

>[!NOTE]
>
>Als er geen inhoudwijzigingen worden aangebracht, wordt het bericht weergegeven dat de pagina is geactiveerd, maar er wordt geen nieuwe versie gemaakt

U kunt extra versies op verzoek tot stand brengen gebruikend **Versioning** lusje van sidekick. Deze versies worden opgeslagen in de opslagplaats en kunnen indien nodig worden hersteld.

Deze versies worden nooit gewist, zodat de grootte van de opslagplaats na verloop van tijd zal groeien en daarom moet worden beheerd.

AEM wordt geleverd met verschillende mechanismen om u te helpen uw opslagplaats te beheren:

* de [Versiebeheer](#version-manager)
Dit kan worden gevormd om oude versies te zuiveren wanneer de nieuwe versies worden gecreeerd.

* het gereedschap [Versies wissen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool)
Dit wordt gebruikt als onderdeel van het bewaken en onderhouden van uw opslagplaats.
Het staat u toe om oude versies van een knoop, of een hiërarchie van knopen, volgens deze parameters in te grijpen:

   * Het maximumaantal versies dat in de gegevensopslagruimte moet worden bewaard.
Wanneer dit aantal wordt overschreden, wordt de oudste versie verwijderd.

   * De maximumleeftijd van versies die in de opslagplaats worden bewaard.
Wanneer de leeftijd van een versie deze waarde overschrijdt, wordt deze uit de opslagplaats verwijderd.

* de [onderhoudstaak voor versiezuivering](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). U kunt de onderhoudstaak van het Leegmaken van de Versie plannen om oude versies automatisch te schrappen. Dit minimaliseert daarom de noodzaak om handmatig de gereedschappen voor het wissen van versies te gebruiken.

>[!CAUTION]
>
>Om de grootte van de opslagplaats te optimaliseren, moet u de versiereinigingstaak regelmatig uitvoeren. De taak zou buiten kantooruren moeten worden gepland wanneer er een beperkte hoeveelheid verkeer is.

## Versiebeheer {#version-manager}

Naast expliciete zuivering door het zuiveringshulpmiddel te gebruiken, kan de Manager van de Versie worden gevormd om oude versies te zuiveren wanneer de nieuwe versies worden gecreeerd.

Om de Manager van de Versie te vormen, [creeer een configuratie](/help/sites-deploying/configuring-osgi.md) voor:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

De volgende opties zijn beschikbaar:

* `versionmanager.createVersionOnActivation` (Boolean, standaard: true) Geeft aan of een versie moet worden gemaakt wanneer pagina&#39;s worden geactiveerd.
Een versie wordt gecreeerd tenzij de replicatieagent wordt gevormd om de verwezenlijking van versies te onderdrukken, die door de Manager van de Versie wordt gerespecteerd.
Een versie wordt gecreeerd slechts als de activering op een weg gebeurt die in `versionmanager.ivPaths` (zie hieronder) bevat.

* `versionmanager.ivPaths`(Tekenreeks[], standaard:  `{"/"}`) Geeft de paden aan waarop versies impliciet worden gemaakt bij activering als deze  `versionmanager.createVersionOnActivation` zijn ingesteld op true.

* `versionmanager.purgingEnabled` (Boolean, standaard: false) Hiermee wordt gedefinieerd of leegmaken wordt ingeschakeld wanneer nieuwe versies worden gemaakt.

* `versionmanager.purgePaths` (Tekenreeks[], standaard: {&quot;/content&quot;}) Hiermee geeft u op op welke paden naar purge versies worden verplaatst wanneer nieuwe versies worden gemaakt.

* `versionmanager.maxAgeDays` (int, standaard: 30) Bij het opschonen van de versie worden alle versies ouder dan de geconfigureerde waarde verwijderd. Als de waarde kleiner is dan 1, wordt het leegmaken niet uitgevoerd op basis van de leeftijd van de versie.

* `versionmanager.maxNumberVersions` (int, standaard 5) Bij het opschonen van versies wordt elke versie die ouder is dan de n-de nieuwste versie verwijderd. Als de waarde kleiner is dan 1, wordt het leegmaken niet uitgevoerd op basis van het aantal versies.

* `versionmanager.minNumberVersions` (int, gebrek 0) het minimumaantal versies die ongeacht de leeftijd zullen worden gehouden. Als de waarde is ingesteld op een waarde kleiner dan 1, blijft er geen minimumaantal versies behouden.

>[!NOTE]
>
>Het wordt niet aanbevolen een groot aantal versies in de opslagplaats te bewaren. Bij het configureren van de verwijderbewerking van de versie dient u dus niet te veel versies uit te sluiten van de opschoning, anders wordt de grootte van de opslagplaats niet op de juiste wijze geoptimaliseerd. Als u een groot aantal versies bewaart vanwege zakelijke vereisten, neemt u contact op met de ondersteuning van Adobe om te zoeken naar andere manieren om de grootte van de opslagplaats te optimaliseren.

### Bewaaropties combineren {#combining-retention-options}

De opties die bepalen hoe versies moeten worden behouden ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), kunnen afhankelijk van uw vereisten worden gecombineerd.

Als u bijvoorbeeld het maximumaantal versies definieert dat u wilt behouden EN de oudste versie die u wilt behouden:

* Instellen:

   * `maxNumberVersions` = 7

   * `maxAgeDays` = 30

* Met:

   * 10 versies die in de afgelopen 60 dagen zijn gemaakt
   * 3 van de versies die in de afgelopen 30 dagen zijn gemaakt

* Betekent dat:

   * De laatste drie versies blijven behouden

Als u bijvoorbeeld het maximum EN minimum aantal versies definieert dat behouden moet blijven EN de oudste versie die behouden moet blijven:

* Instellen:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Met:

   * 5 versies die 60 dagen geleden zijn gemaakt

* Betekent dat:

   * Drie versies blijven behouden

## Versies wissen {#purge-versions-tool}

Het gereedschap [Versies wissen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) is bedoeld voor het verwijderen van de versies van een knooppunt of een hiërarchie van knooppunten in uw opslagplaats. Het belangrijkste doel is om u te helpen de grootte van uw opslagplaats te verminderen door oude versies van uw knopen te verwijderen.
