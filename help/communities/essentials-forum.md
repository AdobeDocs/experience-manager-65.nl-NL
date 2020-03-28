---
title: Essentiële elementen van forum
seo-title: Essentiële elementen van forum
description: Overzicht van forum
seo-description: Overzicht van forum
uuid: 68849582-8742-40be-9e7e-0b574ae38815
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 059c5bbe-07eb-4873-8157-2196df887b27
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Essentiële elementen van forum {#forum-essentials}

Deze pagina bevat de essentiële informatie voor het werken met de functie Forum.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceTypes</strong></td>
   <td>social/forum/components/hbs/forum<br /> social/forum/components/hbs/topic<br /> social/forum/components/hbs/post</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stemden<br /> cq.social.hbs.forum</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/forum/components/hbs/forum/forum.hbs<br /> /libs/social/forum/components/hbs/post/post.hbs<br /> /libs/social/forum/components/hbs/topic/topic.hbs<br /> /libs/social/forum/components/hbs/topic/list-item.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/forum/components/hbs/forum/clientlibs/forum.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="forum.md">Forum-functie</a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Forum-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/forum/client/api/package-summary.html)

* [Eindpunten van forum](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/forum/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Functie van forum {#forum-function}

Een community-sitestructuur die de functie [](functions.md#forum-function)Forum bevat, bevat een geconfigureerde `forum` component en instellingen die invloed hebben op de moderatie, codering en vertaling.

### Toegang tot forumberichten (UGC) {#accessing-forum-posts-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie Door de gebruiker gegenereerde inhoud [modereren](moderate-ugc.md).

Vanaf AEM 6.1 Communities omvat het gebruik van een [gemeenschappelijke opslag](working-with-srp.md) voor UGC programmatische toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP of JSRP).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

Zie:

* [Overzicht](srp.md) van Storage Resource Provider - Inleiding en overzicht van opslaggebruik
* [SRP en de Hoofdzaak](srp-and-ugc.md) UGC - de gebruiksmethodes van SRP en voorbeelden
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtlijnen
* [SocialUtils Refactoring](socialutils.md) - het Afgekeurde nutsmethodes van de Toewijzing aan huidige SRP nutsmethodes

