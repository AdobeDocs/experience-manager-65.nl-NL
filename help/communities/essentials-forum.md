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
   <td> <strong> resourceTypes </strong></td>
   <td>social/forum/components/hbs/forum<br /> social/forum/components/hbs/topic<br /> social/forum/components/hbs/post</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong> clientllibs </strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stemed<br /> cq.social.hbs.forum</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td> /libs/social/forum/components/hbs/forum/forum.hbs<br /> /libs/social/forum/components/hbs/post/post.hbs<br /> /libs/social/forum/components/hbs/topic/topic.hbs<br /> /libs/social/forum/components/hbs/topic/list-item.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong> css </strong></td>
   <td> /libs/social/forum/components/hbs/forum/clientlibs/forum.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie {de Eigenschap van 0} Forum </a><a href="forum.md"></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [ Forum API ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/forum/client/api/package-summary.html)

* [ Eindpunten van het Forum ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/forum/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Functie van forum {#forum-function}

Een communautaire plaatsstructuur die de [ functie van het Forum ](functions.md#forum-function) omvat, omvat een gevormde `forum` component, en montages die moderatie, het etiketteren, en vertaling beïnvloeden.

### Toegang tot forumberichten (UGC) {#accessing-forum-posts-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [ het Modereren van user-Generated Inhoud ](moderate-ugc.md).

Vanaf Adobe Experience Manager 6.1 Communities, omvat het gebruik van a [ gemeenschappelijke opslag ](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [ Overzicht van de Leverancier van het Middel van de Opslag ](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [ SRP en Hoofdzaak UGC ](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [ SocialUtils Refactoring ](socialutils.md) - de Afgekeurde nutsmethodes van de afbeelding aan huidige SRP hulpprogrammamethodes.
