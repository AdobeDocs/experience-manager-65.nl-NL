---
title: Grondbeginselen van Tally
seo-title: Grondbeginselen van Tally
description: Overzicht van de klasse Tally
seo-description: Overzicht van de klasse Tally
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
translation-type: tm+mt
source-git-commit: 77d00c1d6e94b257aa0533ca88b5f9a12dba0054
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# Essentiële elementen tellen {#tally-essentials}

Tally is een abstracte klasse die een standaardmethode verstrekt om terugkoppelen van leden te verzamelen over hoe zij specifieke producten en de diensten waarderen. Anonieme feedback wordt niet ondersteund. De bezoeker van de site moet zich registreren en aanmelden om deel te nemen en zich aan te melden om zijn feedback te wijzigen. De verplichting om zich aan te melden vergemakkelijkt de matiging en verhoogt de waarde van de feedback door meerdere posten te voorkomen.

Een aangepaste telcomponent kan worden gecreeerd door de abstracte tellingsklasse uit te breiden.

[Op ](essentials-liking.md) dezelfde manier wordt de overeenkomst toegepast. Dat is een eenvoudige manier om een positief oordeel uit te spreken.

[De ](essentials-voting.md) stemming is een uitvoering van de overeenkomst, die een eenvoudige vorm is van het uiten van een positief of negatief advies.

[](rating-basics.md) Ratingis een implementatie van tally die een sterrenstelsel gebruikt voor het uiten van een reeks meningen van positief tot negatief.

Vanaf AEM 6.1 is de opiniepeilingscomponent niet meer beschikbaar.

[](reviews-basics.md) Reviewsis een SCF component die een hybride van  [](essentials-comments.md) commentaren en  [classificatie](rating-basics.md) is.

## Essentiële elementen voor client-side {#essentials-for-client-side}

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Tally API&#39;s](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Eindpunten tellen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte Tallies (UGC) {#accessing-posted-tallies-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1 Communities omvat het gebruik van een [common store](working-with-srp.md) voor UGC programmatische toegang tot UGC, ongeacht de gekozen opslagoptie (zoals ASRP, MSRP of JSRP).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

Zie:

* [Overzicht](srp.md)  van Storage Resource Provider - Inleiding en overzicht van het opslaggebruik.
* [SRP en de Hoofdzaak](srp-and-ugc.md)  van UGC - SRP nutsmethodes en voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md)  - Coderingsrichtlijnen.
* [SocialUtils Refactoring](socialutils.md)  - Afgekeurde nutsmethodes van de Afbeelding aan huidige SRP hulpprogrammamethodes.

