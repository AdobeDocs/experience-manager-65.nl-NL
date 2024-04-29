---
title: Opwaarderen naar AEM 6.5 Gemeenschappen
description: Hoe te om van een vroegere versie aan AEM 6.5 Gemeenschappen te bevorderen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: ea41d35c-967c-4606-b4ec-377e817902e4
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Opwaarderen naar AEM 6.5 Gemeenschappen {#upgrading-to-aem-communities}

Afhankelijk van de topologie en de eigenschappen van elke plaats, kunnen de volgende acties noodzakelijk zijn wanneer bevordering aan AEM Communities 6.5 of het installeren van het recentste eigenschappak.

Deze afdeling is specifiek voor de Gemeenschappen en vormt een aanvulling op de in [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md) (platform).

## Upgrade uitvoeren vanaf AEM 6.1 of hoger {#upgrading-from-aem-or-later}

### Opnieuw indexeren Solr {#reindex-solr}

Wanneer het installeren van een nieuw de eigenschappak van Gemeenschappen op een plaatsing die met MSRP wordt gevormd, zal het noodzakelijk zijn:

1. Installeer de [nieuwste functiepakket](/help/communities/deploy-communities.md#latestfeaturepack).
1. Installeer de [nieuwste configuratiebestanden van Solr](/help/communities/msrp.md#upgrading).
1. Opnieuw indexeren MSRP zie sectie [MSRP opnieuw indexeren](/help/communities/msrp.md#msrp-reindex-tool).

## Upgrade uitvoeren vanaf AEM 6.0 {#upgrading-from-aem}

Als reeds bestaande UGC moet worden behouden, dan hangt de middelen om dit te doen af van of de plaatsing opgeslagen UGC [op locatie](#on-premise-storage) of in de [Adobe cloud](#adobe-cloud-storage).

### Adobe Cloud Storage {#adobe-cloud-storage}

Als de geüpgrade site is geconfigureerd voor het gebruik van Adobe-cloud-opslag, kan deze (onjuist) worden weergegeven alsof alle UGC is verloren omdat de SRP-methoden de reeds bestaande UGC op de oude locatie niet kunnen vinden.

Aldus is er de capaciteit om ASRP te instrueren om te gebruiken `AEM 6.0 compatability-mode` toegang tot UGC.

Voor alle AEM 6.3 auteur- en publicatieinstanties:

* Meld u aan met beheerdersrechten.
* Configureren [ASRP](/help/communities/asrp.md).
* Ga als volgt te werk om bestaande UGC zichtbaar te maken:

   * Blader naar de webconsole:

      * Bijvoorbeeld: [https://&lt;host>:&lt;port>/system/console/configMgr](https://localhost:4502/system/console/configMgr)

      * Zoeken **AEM Communities-hulpprogramma** configuratie.
      * Selecteren om configuratievenster uit te vouwen:

         * *Uitschakelen* `Cloud Storage`

         * Selecteren **Opslaan**

     ![nutsbedrijven](assets/utilities.png)

### Opslag op locatie {#on-premise-storage}

Als de geüpgrade site geen cloudopslag heeft gebruikt, moet eventuele bestaande UGC worden omgezet om te voldoen aan de nieuwe structuur die in AEM 6.1 Communities is geïntroduceerd ter ondersteuning van de gemeenschappelijke opslag.

Voor dit doel, is een open bronmigratiehulpmiddel beschikbaar op GitHub:
[AEM Communities UGC-migratiehulpprogramma](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java API&#39;s {#java-apis}

Bij de opwaardering van AEM 6.0 sociale gemeenschappen naar AEM 6.3 Gemeenschappen zijn veel API&#39;s gereorganiseerd in verschillende pakketten. De meeste moeten gemakkelijk worden opgelost wanneer het gebruiken van winde voor aanpassing van de eigenschappen van Gemeenschappen.

Ga voor meer informatie over het verouderde pakket met sociale hulpmiddelen naar [Refactoring voor sociale hulpmiddelen](/help/communities/socialutils.md).

Zie ook [Maven gebruiken voor Gemeenschappen](/help/communities/maven.md).

### Geen JSP-componentsjablonen {#no-jsp-component-templates}

De [sociale component](/help/communities/scf.md) (SCF) gebruikt [HandlebarsJS](https://handlebarsjs.com/) (HBS) sjabloontaal in plaats van JSP (Java Server Pages) die vóór AEM 6.0 wordt gebruikt.

In AEM 6.0 bleven de JSP componenten naast de nieuwe HBS kadercomponenten op dezelfde plaats, met de componenten van GB typisch in subfolders genoemd &quot;hbs&quot;.

Vanaf AEM 6.1 werden de JSP-componenten volledig verwijderd. Voor Gemeenschappen, wordt het geadviseerd om al gebruik van componenten JSP met componenten SCF te vervangen.

## AEM Communities UGC-migratiehulpprogramma {#aem-communities-ugc-migration-tool}

De [AEM Communities UGC-migratiehulpprogramma](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) is een opensource migratiehulpmiddel, beschikbaar op GitHub, dat kan worden aangepast om UGC van vroegere versies van AEM sociale gemeenschappen uit te voeren en in AEM Communities 6.1 of later in te voeren.

Naast het bewegen van UGC van vroegere versies, is het ook mogelijk om het hulpmiddel te gebruiken om UGC van één te bewegen [SRP](/help/communities/working-with-srp.md) aan een andere, zoals van MSRP aan DSRP.

## Upgrade uitvoeren vanaf AEM 5.6.1 of lager {#upgrading-from-aem-or-earlier}

Conceptueel zijn er drie generaties gemeenschappen componenten:

**Gen 1**: Ruw CQ 5.4 tot en met AEM 5.6.0, dit zijn **collab** componenten die UGC in de lokale opslagplaats hebben opgeslagen gebruikend replicatie als middel om UGC over platforms te synchroniseren. Andere verschillen betreffen de implementatie met behulp van JSP (Java Server Pages) en de blogfunctie die bestaat uit alleen ontwerpen in de auteursomgeving.

**Gen 2**: Van AEM 5.6.1 tot en met AEM 6.1 is dit een mix van: **collab** en **sociaal** componenten. AEM 6.0 introduceert het nieuwe [sociale component](/help/communities/scf.md) (SCF) en AEM 6.2 [algemene UGC-opslag](/help/communities/working-with-srp.md) waar UGC wordt benaderd via een [opslagbronprovider](/help/communities/srp.md) (SRP).

**Gen 3**: Vanaf AEM 6.2 zijn er alleen **sociaal** componenten, die in SCF als componenten van Handlebars (HBS) worden uitgevoerd die een keus van SRP voor UGC vereisen.
