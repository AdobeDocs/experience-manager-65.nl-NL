---
title: Grondbeginselen van Tally
description: Leer hoe Tally een abstracte klasse is die een standaardmethode verstrekt om terugkoppelen van leden over te verzamelen hoe zij specifieke producten en de diensten waarderen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 0b508df9-1a24-4728-a254-f913eeb9b391
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Grondbeginselen van Tally {#tally-essentials}

Tally is een abstracte klasse die een standaardmethode verstrekt om terugkoppelen van leden te verzamelen over hoe zij specifieke producten en de diensten waarderen. Anonieme feedback wordt niet ondersteund. Sitebezoekers moeten zich registreren en aanmelden om deel te nemen en zich aan te melden om hun feedback te wijzigen. De verplichting om zich aan te melden vergemakkelijkt de matiging en verhoogt de waarde van de feedback door meerdere posten te voorkomen.

Een aangepaste telcomponent kan worden gecreeerd door de abstracte tellingsklasse uit te breiden.

[Vergelijken](essentials-liking.md) is een uitvoering van de overeenkomst die een eenvoudige vorm is om een positief oordeel uit te spreken.

[Stemming](essentials-voting.md) is een uitvoering van een overeenkomst die een eenvoudige vorm van positief of negatief advies is.

[Classificatie](rating-basics.md) is een uitvoering van tally die een sterrenstelsel gebruikt om een reeks meningen van positief tot negatief uit te drukken.

Vanaf AEM 6.1 is de opiniepeilingscomponent niet meer beschikbaar.

[Revisies](reviews-basics.md) is een SCF-component die een hybride van [opmerkingen](essentials-comments.md) en [beoordeling](rating-basics.md).

## Essentiële elementen voor client-kant {#essentials-for-client-side}

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Tally API&#39;s](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Eindpunten tellen](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte Tallies (UGC) {#accessing-posted-tallies-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1. [gemeenschappelijk archief](working-with-srp.md) voor UGC omvat programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

Zie:

* [Overzicht opslagbronprovider](srp.md) - Inleiding en overzicht van het gebruik van de opslagplaats.
* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-gebruiksmethoden en -voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtsnoeren.
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - Afgekeurde hulpprogrammamethoden worden toegewezen aan de huidige SRP-hulpprogrammamethoden.
