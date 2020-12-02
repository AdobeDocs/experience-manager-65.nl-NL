---
title: Essentiële elementen van revisies
seo-title: Essentiële elementen van revisies
description: Samenvattingscomponenten van revisies en revisies
seo-description: Samenvattingscomponenten van revisies en revisies
uuid: 540c106e-ee3b-4261-82b2-a909d254dbf7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 62669a9d-2107-4644-a4bf-143d0ac148b3
translation-type: tm+mt
source-git-commit: 62f2a11491e427a13cecae75c225ed41a44783cd
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Essentiële elementen van revisies {#reviews-essentials}

Deze functie bestaat uit twee componenten die samenwerken: Overzicht van beoordelingen en beoordelingen bekijken.

Revisies is een samengesteld onderdeel op basis van een [opmerkingssysteem](essentials-comments.md) dat een of meer [rating](rating-basics.md) (tally)-componenten bevat.

Anonieme publicatie van een revisie wordt niet ondersteund. Sitebezoekers moeten zich registreren en aanmelden om een revisie toe te voegen. De ondertekende bezoeker (lid) kan zijn beoordeling op elk ogenblik bijwerken.

## Essentiële elementen voor client-side {#essentials-for-client-side}

### Revisies {#reviews}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociale/revisies/componenten/hbs/revisies</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Ja - eigenschappen kunnen worden bewerkt in <i>ontwerpmodus </i>modus</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.reviews</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
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

* [API voor revisie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [Eindpunten controleren](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte Revisies (UGC) {#accessing-posted-reviews-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1 Communities omvat het gebruik van een [common store](working-with-srp.md) voor UGC programmatische toegang tot UGC, ongeacht de gekozen opslagoptie (zoals ASRP, MSRP of JSRP).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

Zie:

* [Overzicht](srp.md)  van Storage Resource Provider - Inleiding en overzicht van het opslaggebruik.
* [SRP en de Hoofdzaak](srp-and-ugc.md)  van UGC - SRP nutsmethodes en voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md)  - Coderingsrichtlijnen.
* [SocialUtils Refactoring](socialutils.md)  - Afgekeurde nutsmethodes van de Afbeelding aan huidige SRP hulpprogrammamethodes.

