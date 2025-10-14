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

[&#x200B; het Vergelijken &#x200B;](essentials-liking.md) is een implementatie van een bondgenoot die eenvoudige vorm van het uitdrukken van een positieve mening is.

[&#x200B; het Stemmen &#x200B;](essentials-voting.md) is een implementatie van een bondgenoot die eenvoudige vorm van het uitdrukken van een positieve of negatieve mening is.

[&#x200B; Rating &#x200B;](rating-basics.md) is een implementatie van een bondgenoot die een stersysteem gebruikt om een waaier van meningen van positief tot negatief uit te drukken.

Vanaf AEM 6.1 is de opiniepeilingscomponent niet meer beschikbaar.

[&#x200B; Revisies &#x200B;](reviews-basics.md) is een component SCF die een hybride van [&#x200B; commentaren &#x200B;](essentials-comments.md) en [&#x200B; classificatie &#x200B;](rating-basics.md) is.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [&#x200B; Tally APIs &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [&#x200B; Tally Endpoints &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte Tallies (UGC) {#accessing-posted-tallies-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [&#x200B; het Moderteren van Gebruiker Gegenereerde Inhoud &#x200B;](moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [&#x200B; gemeenschappelijke opslag &#x200B;](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [&#x200B; Overzicht van de Leverancier van het Middel van de Opslag &#x200B;](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [&#x200B; SRP en Hoofdzaak UGC &#x200B;](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [&#x200B; die tot UGC met SRP &#x200B;](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [&#x200B; SocialUtils Refactoring &#x200B;](socialutils.md) - de Afgekeurde nutsmethodes van de afbeelding aan huidige SRP hulpprogrammamethodes.
