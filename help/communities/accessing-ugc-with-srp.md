---
title: Toegang tot UGC met SRP
description: Wanneer een plaats wordt gevormd om ASRP of MSRP te gebruiken, wordt daadwerkelijke UGC niet opgeslagen in AEM knoopopslag (JCR)
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 1157366f-2cc5-46e4-8ec6-e66fe5d0a0f6
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Toegang tot UGC met SRP {#accessing-ugc-with-srp}

## SRP {#about-srp}

Alle AEM Communities-componenten en -functies zijn gebaseerd op de [Sociaal-componentkader (SCF)](/help/communities/scf.md), die de API SocialResourceProvider aanroept om toegang te krijgen tot alle door de gebruiker gegenereerde inhoud (UGC).

Voordat een communitysite wordt gemaakt, moet u [Storage Resource Provider (SRP)](/help/communities/working-with-srp.md) moet worden geconfigureerd om een implementatie te selecteren die consistent is met de onderliggende [topologie](/help/communities/topologies.md). De implementatie SRP is gebaseerd op drie opslagopties:

1. [ASRP](/help/communities/asrp.md) - Adobe op aanvraag
1. [MSRP](/help/communities/msrp.md) - MongoDB
1. [JSRP](/help/communities/jsrp.md) - JCR

## Informatie over UGC-opslag {#about-ugc-storage}

Wat belangrijk is om over opslag van UGC te weten is, wanneer een plaats wordt gevormd om ASRP of MSRP te gebruiken, wordt daadwerkelijke UGC niet opgeslagen in AEM [knooppuntopslag](/help/sites-deploying/data-store-config.md) (JCR).

Hoewel er knooppunten in JCR kunnen zijn die de UGC schaduw geven om nuttige metagegevens te verschaffen, moeten deze knooppunten niet worden verward met de werkelijke UGC.

Zie [Overzicht opslagbronprovider.](/help/communities/srp.md)

## Beste praktijken {#best-practice}

Wanneer het ontwikkelen van douanecomponenten, zouden de ontwikkelaars aan code onafhankelijk van de huidige gekozen topologie moeten zorgvuldig zijn, waarbij flexibiliteit behouden blijft om zich aan een nieuwe topologie in de toekomst te bewegen.

### Stel dat JCR niet beschikbaar is {#assume-jcr-not-available}

Methoden die specifiek zijn voor het JCR moeten worden vermeden.

Te gebruiken methoden:

* Sling API (Sling Resource)

   * Ga er niet van uit dat er JCR-knooppunten zijn

* OSGi Events

   * Ga er niet van uit dat er JCR-gebeurtenissen zijn

* [SocialResourceUtilities](/help/communities/socialutils.md#socialresourceutilities-package)
* [SCFUtilities](/help/communities/socialutils.md#scfutilities-package)

Methoden om te voorkomen:

* Knooppunt-API
* JCR-gebeurtenissen
* werkstroomstartprogramma&#39;s (die gebruikmaken van JCR-gebeurtenissen)

### Zoekverzamelingen gebruiken {#use-search-collections}

Verschillende SRPs kan verschillende inheemse vraagtalen hebben. Gebruik methoden van het menu [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) pakket om de aangewezen vraagtaal in werking te stellen.

Zie voor meer informatie [Essentiële zoekopdrachten](/help/communities/search-implementation.md).

## Bronnen {#resources}

* [Opslag van communautaire inhoud](/help/communities/working-with-srp.md) - bespreekt de beschikbare keuzen SRP voor een gemeenschappelijk opslag UGC
* [Overzicht opslagbronprovider](/help/communities/srp.md) - overzicht van het gebruik van introducties en opslagplaatsen
* [SRP en UGC Essentials](/help/communities/srp-and-ugc.md) - SRP-hulpprogrammamethoden en -voorbeelden
* [Essentiële zoekopdrachten](/help/communities/search-implementation.md) - essentiële informatie voor het doorzoeken van UGC
* [Refactoring voor sociale hulpmiddelen](/help/communities/socialutils.md) - het in kaart brengen van afgekeurde nutsmethodes aan huidige SRP nutsmethodes
