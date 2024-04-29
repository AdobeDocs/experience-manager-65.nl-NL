---
title: Essentiële elementen van gebruikersgroepen
description: Leer hoe geautoriseerde gebruikers de functie Gebruikersgroepen kunnen gebruiken om dynamisch een subcommunity binnen een communitysite te maken.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: f45ae7be-a500-463a-ab3e-81f281651a9d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Essentiële elementen van gebruikersgroepen  {#community-group-essentials}

De eigenschap van communautaire groepen is de capaciteit voor een subcommunity om dynamisch binnen een communautaire plaats door erkende gebruikers van de publicatie en auteursmilieu&#39;s worden gecreeerd.

Vanaf Gemeenschappen [functiepakket 1](deploy-communities.md#latestfeaturepack), kunnen groepen worden genest binnen andere groepen.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

### Lidlijst van communautaire groepen {#community-groups-member-list}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/group/components/hbs/communitygroupmembershipList</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.communitygroups</td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/communitygroupmemberlist.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/memberList.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="creating-groups.md">Communautaire groep</a></td>
  </tr>
 </tbody>
</table>

### Communautaire groepen {#community-groups}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociaal/groep/componenten/hbs/communitygroepen</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.communitygroups</td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td> /libs/social/group/components/hbs/communitygroups/communitygroups.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/communitygroups.css</td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Community Group API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/group/client/api/package-summary.html)

* [Eindpunten van groepen Gemeenschap](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/group/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Functie Groepen {#groups-function}

Een community-sitestructuur die een [Groepen, functie](functions.md#groups-function) ondersteunt de oprichting van nieuwe `community groups` vanuit de publicatie- en auteursomgevingen. De gemaakte community-groep bevat een `community groups member list` die de leden van de groep opsomt.

Een of meer [communitygroepsjablonen](tools-groups.md), die het ontwerp van de pagina&#39;s van de communautaire groep verstrekken, kan voor de functie van Groepen worden gevormd. Dit geldt wanneer de functie wordt toegevoegd aan een [sjabloon voor community-site](sites.md) of genest binnen een groepssjabloon van een gemeenschap.

Het opnemen van meerdere groepssjablonen resulteert in een keuze. Dat wil zeggen, de keuze van het ontwerp dat wordt voorgesteld aan de geautoriseerde gebruiker op het moment dat een community-groep wordt gemaakt voor de community-site. Zie de sectie over [communautaire groepen](creating-groups.md) voor auteurs.

### Geneste groepen {#nested-groups}

Vanaf Gemeenschappen [FP1](deploy-communities.md#latestfeaturepack), is het mogelijk dat een groepsfunctie wordt opgenomen in een groepssjabloon, zodat geneste groepen (subgemeenschappen) mogelijk zijn.

Wanneer een communautaire plaats of groepsmalplaatje de functie van Groepen omvat, is het mogelijk:

* Maak een subcommunity in de auteursomgeving.

* Maak een groep in de publicatieomgeving wanneer deze is geconfigureerd om deze toe te staan.

Wanneer u een groep maakt in de ontwerpomgeving, moet u eerst de communitysite publiceren en vervolgens de groep publiceren. Het publiceren van de communautaire plaats publiceert de pagina&#39;s van de groep, zonder de de lidgroepen van subcommunity te creëren waaraan ACLs wordt geplaatst. Een beperkte (geheime) groep kan dus zichtbaar zijn totdat de groep expliciet wordt gepubliceerd.

## Koppelingen en verwante informatie {#links-and-related-information}

* [Gebruikers en gebruikersgroepen beheren](users.md)
* [Console van groepen Gemeenschappen](groups.md)
* [Functie Groepen](functions.md#groups-function)
* [Groepssjablonen](tools-groups.md)
