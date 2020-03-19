---
title: Toegang tot UGC met SRP
seo-title: Toegang tot UGC met SRP
description: Wanneer een plaats wordt gevormd om ASRP of MSRP te gebruiken, wordt daadwerkelijke UGC niet opgeslagen in de knoopopslag van AEM (JCR)
seo-description: Wanneer een plaats wordt gevormd om ASRP of MSRP te gebruiken, wordt daadwerkelijke UGC niet opgeslagen in de knoopopslag van AEM (JCR)
uuid: 30549f93-e370-4b8b-a35a-69e05884227e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 72d4022c-43ba-49e0-b94c-f2beabaef64d
docset: aem65
translation-type: tm+mt
source-git-commit: 974d58efa560b90234d5121a11bdb445c7bf94cf

---


# Toegang tot UGC met SRP {#accessing-ugc-with-srp}

## SRP {#about-srp}

Alle componenten en functies van AEM Communities zijn gebaseerd op het [sociale-componentframework (SCF)](/help/communities/scf.md), dat de API van SocialResourceProvider aanroept om toegang te krijgen tot alle door de gebruiker gegenereerde inhoud (UGC).

Alvorens een communautaire plaats wordt gecreeerd, moet de leverancier van het [opslagmiddel (SRP)](/help/communities/working-with-srp.md) worden gevormd om een implementatie te selecteren verenigbaar met de onderliggende [topologie](/help/communities/topologies.md). De implementatie SRP is gebaseerd op drie opslagopties:

1. [ASRP](/help/communities/asrp.md) - Opslag op aanvraag van Adobe
1. [MSRP](/help/communities/msrp.md) - MongoDB
1. [JSRP](/help/communities/jsrp.md) - JCR

## Informatie over UGC-opslag {#about-ugc-storage}

Wat belangrijk is om over opslag van UGC te weten is, wanneer een plaats wordt gevormd om ASRP of MSRP te gebruiken, wordt daadwerkelijke UGC niet opgeslagen in de [knoopopslag](/help/sites-deploying/data-store-config.md) van AEM (JCR).

Hoewel er knooppunten in JCR kunnen zijn die de UGC schaduw geven om nuttige metagegevens te verschaffen, moeten deze knooppunten niet worden verward met de werkelijke UGC.

Zie Overzicht [van Storage Resource Provider.](/help/communities/srp.md)

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

Verschillende SRPs kan verschillende inheemse vraagtalen hebben. Het wordt aanbevolen methoden uit het pakket [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) te gebruiken om de juiste querytaal uit te voeren.

Voor meer informatie, zie de Hoofdzaak van het [Onderzoek](/help/communities/search-implementation.md).

## Bronnen {#resources}

* [Community Content Storage](/help/communities/working-with-srp.md) - bespreekt de beschikbare SRP-keuzes voor een UGC-winkel
* [Overzicht](/help/communities/srp.md) van Storage Resource Provider - introductie en overzicht van opslaggebruik
* [SRP en de Hoofdzaak](/help/communities/srp-and-ugc.md) UGC - de gebruiksmethodes van SRP en voorbeelden
* [Hoofdzaak](/help/communities/search-implementation.md) zoeken - essentiële informatie voor het zoeken naar UGC
* [SocialUtils Refactoring](/help/communities/socialutils.md) - het in kaart brengen van afgekeurde nutsmethodes aan huidige SRP hulpprogrammamethodes

