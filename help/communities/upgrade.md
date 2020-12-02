---
title: Opwaarderen naar AEM 6.5 Gemeenschappen
seo-title: Opwaarderen naar AEM 6.5 Gemeenschappen
description: Hoe te om van een vroegere versie aan AEM 6.4 Gemeenschappen te bevorderen
seo-description: Hoe te om van een vroegere versie aan AEM 6.4 Gemeenschappen te bevorderen
uuid: 929c3892-1b3b-46a7-8e70-fa6864125911
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: abe5a998-bbe3-4a2b-bcf7-b490a8275219
docset: aem65
translation-type: tm+mt
source-git-commit: c190d5f223c85f6c49fea1391d8a3d2baff20192
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 0%

---


# Bijwerken naar AEM 6.5-gemeenschappen {#upgrading-to-aem-communities}

Afhankelijk van de topologie en de eigenschappen van elke plaats, kunnen de volgende acties noodzakelijk zijn wanneer bevordering aan AEM Communities 6.5 of het installeren van het recentste eigenschappak.

Deze sectie is specifiek voor Gemeenschappen en vormt een aanvulling op de informatie in [Bijwerken naar AEM 6.5](/help/sites-deploying/upgrade.md) (platform).

## Bijwerken vanaf AEM 6.1 of hoger {#upgrading-from-aem-or-later}

### Opnieuw indexeren Solr {#reindex-solr}

Wanneer het installeren van een nieuw de eigenschappak van Gemeenschappen op een plaatsing die met MSRP wordt gevormd, zal het noodzakelijk zijn:

1. Installeer het [nieuwste functiepakket](/help/communities/deploy-communities.md#latestfeaturepack).
1. Installeer de [nieuwste configuratiebestanden van Solr](/help/communities/msrp.md#upgrading).
1. MSRP opnieuw indexeren
zie sectie [MSRP Reindex Tool](/help/communities/msrp.md#msrp-reindex-tool).

### Enablement 2.0 {#enablement}

Vanaf AEM 6.3 slaan de enablement eigenschappen niet meer rapporteringsinformatie in MySQL op. De MySQL-afhankelijkheid is alleen beschikbaar voor het bijhouden van SCORM-inhoud.

Neem contact op met [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) voor hulp bij het migreren van inhoud uit Enablement 1.0.

## Bijwerken vanaf AEM 6.0 {#upgrading-from-aem}

Als bestaande UGC moet worden behouden, hangt de manier om dit te doen af van of de plaatsing opgeslagen UGC [on-premise](#on-premise-storage) of in [Adobe wolk](#adobe-cloud-storage).

### Adobe Cloud Storage {#adobe-cloud-storage}

Als de geüpgrade site is geconfigureerd voor het gebruik van de Adobe-cloudopslag, wordt deze mogelijk (onjuist) weergegeven alsof alle UGC is verloren omdat de SRP-methoden de reeds bestaande UGC op de oude locatie niet kunnen vinden.

Aldus, is er de capaciteit om ASRP op te dragen om `AEM 6.0 compatability-mode` te gebruiken om tot UGC toegang te hebben.

Voor alle AEM 6.3 auteur- en publicatieinstanties:

* Meld u aan met beheerdersrechten.
* Configureer [ASRP](/help/communities/asrp.md).
* Ga als volgt te werk om bestaande UGC zichtbaar te maken:

   * Blader naar de webconsole:

      * Bijvoorbeeld [https://&lt;host>:&lt;port>/system/console/configMgr](https://localhost:4502/system/console/configMgr)

      * Zoek **AEM Communities-hulpprogramma**-configuratie.
      * Selecteren om configuratievenster uit te vouwen:

         * *Uitschakelen* `Cloud Storage`

         * Selecteer **Opslaan**

      ![nutsbedrijven](assets/utilities.png)


### Opslag op locatie {#on-premise-storage}

Als de geüpgrade site geen cloudopslag heeft gebruikt, moet eventuele bestaande UGC worden omgezet om te voldoen aan de nieuwe structuur die in AEM 6.1 Communities is geïntroduceerd ter ondersteuning van de gemeenschappelijke opslag.

Voor dit doel, is een open bronmigratiehulpmiddel beschikbaar op GitHub:
[AEM Communities UGC-migratiehulpprogramma](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java API&#39;s {#java-apis}

Houd er rekening mee dat veel API&#39;s in verschillende pakketten zijn ondergebracht bij de opwaardering van AEM 6.0 sociale gemeenschappen naar AEM 6.3 Gemeenschappen. De meeste moeten gemakkelijk worden opgelost wanneer het gebruiken van winde voor aanpassing van de eigenschappen van Gemeenschappen.

Voor details op het afgekeurde pakket SocialUtils, bezoek [Refactoring SocialeUtils](/help/communities/socialutils.md).

Zie ook [Maven gebruiken voor Communities](/help/communities/maven.md).

### Geen JSP-componentsjablonen {#no-jsp-component-templates}

In het [social component framework](/help/communities/scf.md) (SCF) wordt de sjabloontaal [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) gebruikt in plaats van Java Server Pages (JSP) die vóór AEM 6.0 werd gebruikt.

In AEM 6.0 bleven de JSP componenten naast de nieuwe HBS kadercomponenten op dezelfde plaats, met de componenten HBS typisch gevestigd in subfolders genoemd &quot;hbs&quot;.

Vanaf AEM 6.1 werden de JSP-componenten volledig verwijderd. Voor Gemeenschappen, wordt het geadviseerd om al gebruik van componenten JSP met componenten SCF te vervangen.

## AEM Communities UGC-migratiehulpprogramma {#aem-communities-ugc-migration-tool}

Het [AEM Communities UGC-migratiehulpmiddel](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) is een opensource migratiehulpmiddel dat beschikbaar is op GitHub en dat kan worden aangepast om UGC uit eerdere versies van AEM sociale gemeenschappen te exporteren en in AEM Communities 6.1 of hoger te importeren.

Naast het bewegen van UGC van vroegere versies, is het ook mogelijk om het hulpmiddel te gebruiken om UGC van één [SRP](/help/communities/working-with-srp.md) naar een andere, zoals van MSRP aan DSRP te bewegen.

## Bijwerken vanaf AEM 5.6.1 of eerder {#upgrading-from-aem-or-earlier}

Conceptueel zijn er drie generaties gemeenschappen componenten:

**Gen 1**: Ruwweg CQ 5.4 door AEM 5.6.0, zijn dit de  **** collabcomponents die UGC in de lokale bewaarplaats gebruikend replicatie als middel om UGC over platforms te synchroniseren opsloeg. Andere verschillen betreffen de implementatie met behulp van JSP (Java Server Pages) en de blogfunctie die bestaat uit alleen ontwerpen in de auteursomgeving.

**Gen 2**: Van AEM 5.6.1 tot AEM 6.1 is dit een mengeling van  **** sociale  **** componenten. AEM 6.0 introduceerde het nieuwe [sociale componentenkader](/help/communities/scf.md) (SCF) en AEM 6.2 introduceerde een [gemeenschappelijke opslag UGC](/help/communities/working-with-srp.md) waar UGC wordt betreden gebruikend een [opslagmiddelleverancier](/help/communities/srp.md) (SRP).

**Gen 3**: Van AEM 6.2 voorwaarts, zijn er slechts  **** sociale componenten, die in SCF als componenten van Handlebars (HBS) worden uitgevoerd die een keus van SRP voor UGC vereisen.
