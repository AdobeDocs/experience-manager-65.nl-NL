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

[ het Vergelijken ](essentials-liking.md) is een implementatie van een bondgenoot die eenvoudige vorm van het uitdrukken van een positieve mening is.

[ het Stemmen ](essentials-voting.md) is een implementatie van een bondgenoot die eenvoudige vorm van het uitdrukken van een positieve of negatieve mening is.

[ Rating ](rating-basics.md) is een implementatie van een bondgenoot die een stersysteem gebruikt om een waaier van meningen van positief tot negatief uit te drukken.

Vanaf AEM 6.1 is de opiniepeilingscomponent niet meer beschikbaar.

[ Revisies ](reviews-basics.md) is een component SCF die een hybride van [ commentaren ](essentials-comments.md) en [ classificatie ](rating-basics.md) is.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [ Tally APIs ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [ Tally Endpoints ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte Tallies (UGC) {#accessing-posted-tallies-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [ het Moderteren van Gebruiker Gegenereerde Inhoud ](moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [ gemeenschappelijke opslag ](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [ Overzicht van de Leverancier van het Middel van de Opslag ](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [ SRP en Hoofdzaak UGC ](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [ SocialUtils Refactoring ](socialutils.md) - de Afgekeurde nutsmethodes van de afbeelding aan huidige SRP hulpprogrammamethodes.
