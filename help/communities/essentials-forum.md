---
title: Essentiële elementen van forum
description: Meer informatie over de basisbeginselen van het werken met de functie Forum in Adobe Experience Manager Communities.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 622cf6ca-f119-4310-ad14-537576bd6f6d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Essentiële elementen van forum {#forum-essentials}

Deze pagina bevat de essentiële informatie voor het werken met de functie Forum.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceTypes</strong></td>
   <td>sociaal/forum/componenten/hbs/forum<br /> sociaal/forum/componenten/hbs/onderwerp<br /> sociaal/forum/componenten/hbs/post</td>
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
   <td> <strong>sjablonen</strong></td>
   <td> /libs/social/forum/components/hbs/forum/forum.hbs<br /> /libs/social/forum/components/hbs/post/post.hbs<br /> /libs/social/forum/components/hbs/topic/topic.hbs<br /> /libs/social/forum/components/hbs/topic/list-item.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/forum/components/hbs/forum/clientlibs/forum.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="forum.md">Functie van forum</a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Forum-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/forum/client/api/package-summary.html)

* [Eindpunten van forum](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/forum/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Functie van forum {#forum-function}

Een community-sitestructuur die de [Forum, functie](functions.md#forum-function)bevat een configuratie `forum` en instellingen die invloed hebben op de moderatie, codering en vertaling.

### Toegang tot forumberichten (UGC) {#accessing-forum-posts-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door de gebruiker gegenereerde inhoud moderniseren](moderate-ugc.md).

Vanaf Adobe Experience Manager 6.1 Gemeenschappen wordt het gebruik van een [gemeenschappelijk archief](working-with-srp.md) voor UGC omvat programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

Zie:

* [Overzicht opslagbronprovider](srp.md) - Inleiding en overzicht van het gebruik van de opslagplaats.
* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-gebruiksmethoden en -voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtsnoeren.
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - Afgekeurde hulpprogrammamethoden worden toegewezen aan de huidige SRP-hulpprogrammamethoden.
