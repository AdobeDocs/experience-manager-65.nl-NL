---
title: Opwaarderen naar AEM 6.5-gemeenschappen
seo-title: Opwaarderen naar AEM 6.5-gemeenschappen
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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Opwaarderen naar AEM 6.5-gemeenschappen{#upgrading-to-aem-communities}

Afhankelijk van de topologie en de eigenschappen van elke plaats, kunnen de volgende acties noodzakelijk zijn wanneer bevordering aan Gemeenschappen AEM 6.5 of het installeren van het recentste eigenschappak.

Deze sectie is specifiek voor Gemeenschappen en vormt een aanvulling op de informatie die wordt verstrekt in [Upgraden naar AEM 6.5](/help/sites-deploying/upgrade.md) (platform).

## Upgrade uitvoeren vanaf AEM 6.1 of hoger {#upgrading-from-aem-or-later}

### Opnieuw indexeren Solr {#reindex-solr}

Wanneer het installeren van een nieuw de eigenschappak van Gemeenschappen op een plaatsing die met MSRP wordt gevormd, zal het noodzakelijk zijn

1. installeer het [recentste eigenschappak](/help/communities/deploy-communities.md#latestfeaturepack)
1. installeer de [recentste Solr config- dossiers](/help/communities/msrp.md#upgrading)
1. herdex MSRPsee sectie [MSRP Reindex Tool](/help/communities/msrp.md#msrp-reindex-tool)

### Enablement 2.0 {#enablement}

Vanaf AEM 6.3, slaan de enablement eigenschappen niet meer rapporteringsinformatie in MySQL op. De MySQL-afhankelijkheid is alleen beschikbaar voor het bijhouden van SCORM-inhoud.

Neem contact op met de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) voor hulp bij het migreren van inhoud uit Enablement 1.0.

## Upgrade uitvoeren vanaf AEM 6.0 {#upgrading-from-aem}

Als bestaande UGC moet worden behouden, hangt de manier om dit te doen af van of de plaatsing [op-gebouw](#on-premise-storage) UGC of in de [wolk](#adobe-cloud-storage)van Adobe opslaat.

### Adobe Cloud Storage {#adobe-cloud-storage}

Als de geüpgrade site is geconfigureerd voor gebruik van Adobe-cloudopslag, wordt deze mogelijk (onjuist) weergegeven alsof alle UGC is verloren omdat de SRP-methoden de bestaande UGC op de oude locatie niet kunnen vinden.

Aldus, is er de capaciteit om ASRP op te dragen om `AEM 6.0 compatability-mode` tot UGC toegang te hebben.

Voor alle auteur- en publicatiefuncties van AEM 6.3

* aanmelden met beheerdersrechten
* vorm [ASRP](/help/communities/asrp.md)
* Ga als volgt te werk om bestaande UGC zichtbaar te maken:

   * naar de webconsole bladeren

      * bijvoorbeeld [https://&lt;host>:&lt;port>/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * Configuratie van hulpprogramma&#39;s voor **AEM-gemeenschappen** zoeken
   * selecteren om configuratievenster uit te breiden

      * *uncheck ***`Cloud Storage`**

      * Selecteer **Opslaan**


![chlimage_1-176](assets/chlimage_1-176.png)

### Opslag op locatie {#on-premise-storage}

Als de geüpgrade site geen cloudopslag gebruikte, moet eventuele bestaande UGC worden omgezet om te voldoen aan de nieuwe structuur die is geïntroduceerd in AEM 6.1 Communities ter ondersteuning van de gemeenschappelijke opslag.

Voor dit doel, is een open bronmigratiehulpmiddel beschikbaar op GitHub:
UGC-migratiehulpprogramma voor[AEM-gemeenschappen](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java API&#39;s {#java-apis}

Houd er rekening mee dat veel API&#39;s zijn gereorganiseerd in verschillende pakketten wanneer ze worden opgewaardeerd van AEM 6.0 sociale gemeenschappen naar AEM 6.3 Communities. De meeste moeten gemakkelijk worden opgelost wanneer het gebruiken van winde voor aanpassing van de eigenschappen van Gemeenschappen.

Voor details op het verouderde pakket SocialUtils, bezoek Refactoring [SocialUtils](/help/communities/socialutils.md).

Zie ook [Maven gebruiken voor Gemeenschappen](/help/communities/maven.md).

### Geen JSP-componentsjablonen {#no-jsp-component-templates}

Het [sociale componentenkader](/help/communities/scf.md) (SCF) gebruikt de [Sjabloontaal HandlebarsJS](https://www.handlebarsjs.com/) (HBS) in plaats van Java Server Pages (JSP) die vóór AEM 6.0 wordt gebruikt.

In AEM 6.0 bleven de JSP componenten naast de nieuwe HBS kadercomponenten op dezelfde plaats, met de componenten HBS die typisch in subfolders worden gevestigd genoemd &quot;hbs&quot;.

Vanaf AEM 6.1 werden de JSP componenten volledig verwijderd. Voor Gemeenschappen, wordt het geadviseerd om al gebruik van componenten JSP met componenten SCF te vervangen.

## AEM Communities UGC Migration Tool {#aem-communities-ugc-migration-tool}

Het [AEM Communities UGC-migratiehulpmiddel](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) is een opensource-migratiehulpmiddel dat beschikbaar is op GitHub en dat kan worden aangepast om UGC uit eerdere versies van AEM Social Communities te exporteren en in AEM Communities 6.1 of hoger te importeren.

Naast het bewegen van UGC van vroegere versies, is het ook mogelijk om het hulpmiddel te gebruiken om UGC van één [SRP](/help/communities/working-with-srp.md) naar een andere, zoals van MSRP aan DSRP te bewegen.

## Upgrade uitvoeren vanaf AEM 5.6.1 of eerder {#upgrading-from-aem-or-earlier}

Conceptueel zijn er drie generaties gemeenschappen componenten:

**Gen 1** : grofweg CQ 5.4 door AEM 5.6.0 - dit zijn de componenten van het **collab** die UGC in de lokale bewaarplaats gebruikend replicatie als middel om UGC over platforms te synchroniseren opslaagde. Andere verschillen betreffen de implementatie met behulp van JSP (Java Server Pages) en de blogfunctie die bestaat uit alleen ontwerpen in de auteursomgeving.

**Gen 2** : van AEM 5.6.1 tot en met AEM 6.1 - dit is een combinatie van **collab** en **sociale** componenten. AEM 6.0 introduceerde het nieuwe [sociale componentenkader](/help/communities/scf.md) (SCF) en AEM 6.2 introduceerde een [gemeenschappelijke opslag](/help/communities/working-with-srp.md) UGC waar UGC wordt betreden gebruikend een [opslagmiddelleverancier](/help/communities/srp.md) (SRP).

**Gen 3** : van AEM 6.2 voorwaarts, zijn er slechts **sociale** componenten, die in SCF als componenten van Handlebars (HBS) worden uitgevoerd een keus van SRP voor UGC vereisen.
