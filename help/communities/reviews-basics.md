---
title: Essentiële elementen van revisies
description: Leer hoe Revisies in AEM Communities een samengesteld onderdeel zijn op basis van een opmerkingensysteem dat een of meer beoordelingscomponenten (tellingen) bevat.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 91e0e245-a2f1-4bd7-b38f-7641fd94a547
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Essentiële elementen van revisies {#reviews-essentials}

Deze functie bestaat uit twee componenten die samenwerken: revisies en overzichtssamenvatting.

Revisies is een samengesteld onderdeel op basis van een [opmerkingssysteem](essentials-comments.md) die een of meer [beoordeling](rating-basics.md) (tally) componenten.

Anonieme terbeschikkingstelling van een revisie wordt niet ondersteund. Sitebezoekers moeten zich registreren en aanmelden om een revisie toe te voegen. De ondertekende bezoeker (lid) kan zijn beoordeling op elk ogenblik bijwerken.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

### Revisies {#reviews}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociale/revisies/componenten/hbs/revisies</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Ja - eigenschappen kunnen worden bewerkt in <i>ontwerp </i>mode</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.reviews</td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/reviews.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/review.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/status.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/toolbar.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/clientlibs/review.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="reviews.md">Revisies gebruiken</a></td>
  </tr>
 </tbody>
</table>

### Overzicht van revisie {#review-summary}

| **resourceType** | social/reviews/components/hbs/summary |
|---|---|
| [**inclusief**](scf.md#add-or-include-a-communities-component) | Ja - eigenschappen kunnen worden bewerkt in *design *mode |
| [**clientllibs**](client-customize.md#clientlibs-for-scf) | cq.social.hbs.reviews |
| **sjablonen** | /libs/social/reviews/components/hbs/summary/summary.hbs |
| **css** | /libs/social/reviews/components/hbs/reviews/clientlibs/review.css |
| **eigenschappen** | Zie [Revisies gebruiken](reviews.md) |

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [API voor revisie](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [Eindpunten controleren](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte recensies (UGC) {#accessing-posted-reviews-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1. [gemeenschappelijk archief](working-with-srp.md) voor UGC omvat programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

Zie:

* [Overzicht opslagbronprovider](srp.md) - Inleiding en overzicht van het gebruik van de opslagplaats.
* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-gebruiksmethoden en -voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtsnoeren.
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - Afgekeurde hulpprogrammamethoden worden toegewezen aan de huidige SRP-hulpprogrammamethoden.
