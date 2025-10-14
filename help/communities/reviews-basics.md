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

De recensies zijn een samengestelde component die op het systeem van de a [&#x200B; commentaren &#x200B;](essentials-comments.md) wordt gebaseerd die één of meerdere [&#x200B; classificatie &#x200B;](rating-basics.md) (tally) componenten bevat.

Anonieme terbeschikkingstelling van een revisie wordt niet ondersteund. Sitebezoekers moeten zich registreren en aanmelden om een revisie toe te voegen. De ondertekende bezoeker (lid) kan zijn beoordeling op elk ogenblik bijwerken.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

### Revisies {#reviews}

<table>
 <tbody>
  <tr>
   <td> <strong> resourceType </strong></td>
   <td>sociale/revisies/componenten/hbs/revisies</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Ja - de eigenschappen zijn editable op <i> ontwerp </i> wijze</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong> clientllibs </strong></a></td>
   <td>cq.social.hbs.reviews</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/reviews.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/review.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/status.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/toolbar.hbs</td>
  </tr>
  <tr>
   <td> <strong> css </strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/clientlibs/review.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="reviews.md"> Gebruikend Revisies </a></td>
  </tr>
 </tbody>
</table>

### Overzicht van revisie {#review-summary}

| **resourceType** | social/reviews/components/hbs/summary |
|---|---|
| [**inbegrepen**](scf.md#add-or-include-a-communities-component) | Ja - eigenschappen kunnen worden bewerkt in *design *mode |
| [**clientllibs**](client-customize.md#clientlibs-for-scf) | cq.social.hbs.reviews |
| **malplaatjes** | /libs/social/reviews/components/hbs/summary/summary.hbs |
| **css** | /libs/social/reviews/components/hbs/reviews/clientlibs/review.css |
| **eigenschappen** | Zie [&#x200B; Gebruikend Revisies &#x200B;](reviews.md) |

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [&#x200B; Overzicht API &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [&#x200B; Eindpunten van het Overzicht &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte recensies (UGC) {#accessing-posted-reviews-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [&#x200B; het Moderteren van Gebruiker Gegenereerde Inhoud &#x200B;](moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [&#x200B; gemeenschappelijke opslag &#x200B;](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [&#x200B; Overzicht van de Leverancier van het Middel van de Opslag &#x200B;](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [&#x200B; SRP en Hoofdzaak UGC &#x200B;](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [&#x200B; die tot UGC met SRP &#x200B;](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [&#x200B; SocialUtils Refactoring &#x200B;](socialutils.md) - de Afgekeurde nutsmethodes van de afbeelding aan huidige SRP hulpprogrammamethodes.
