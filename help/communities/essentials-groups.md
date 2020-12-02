---
title: Essentiële elementen van gebruikersgroepen
seo-title: Essentiële elementen van gebruikersgroepen
description: Communitysites dynamisch maken
seo-description: Communitysites dynamisch maken
uuid: 168e7aeb-6e9a-468d-8ac4-274007cea252
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4f85cd3c-5158-4f23-abe2-7e375fd0c8d4
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# Essentiële elementen van communautaire groepen {#community-group-essentials}

De eigenschap van communautaire groepen is de capaciteit voor een subcommunity dynamisch om binnen een communautaire plaats door erkende gebruikers van de publicatie en auteursmilieu&#39;s worden gecreeerd.

Vanaf Communities [feature pack 1](deploy-communities.md#latestfeaturepack) is het mogelijk dat groepen worden genest binnen andere groepen

## Essentiële elementen voor client-side {#essentials-for-client-side}

### Lidlijst van communautaire groepen {#community-groups-member-list}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/group/components/hbs/communitygrouplidlist</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.communitygroups</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/communitygroupmemberlist.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/memberList.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="creating-groups.md">Community Group</a></td>
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

* [Community Group API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/group/client/api/package-summary.html)

* [Eindpunten van groepen Gemeenschap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/group/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Groepeert functie {#groups-function}

Een community-sitestructuur die een functie [Groepen](functions.md#groups-function) bevat, ondersteunt het maken van nieuwe `community groups` vanuit de publicatie- en auteursomgevingen. De gemaakte community-groep bevat een `community groups member list`-component die de leden van de groep vermeldt.

Een of meer [communitygroepssjablonen](tools-groups.md), die het ontwerp van de communitygroeppagina(&#39;s) bieden, kunnen worden geconfigureerd voor de functie Groepen wanneer de functie wordt toegevoegd aan een [communitysjabloon](sites.md) of genest binnen een communitygroepsjabloon.

Het opnemen van veelvoudige communautaire groepsmalplaatjes resulteert in een keus van ontwerp dat aan de erkende gebruiker op het tijdstip wordt voorgesteld een nieuwe communautaire groep voor de communautaire plaats wordt gecreeerd, zoals aangetoond in de sectie over [communitygroepen](creating-groups.md) voor auteurs.

### Geneste groepen {#nested-groups}

Vanaf de Gemeenschappen [FP1](deploy-communities.md#latestfeaturepack), is het mogelijk dat een functie van Groepen binnen een groepsmalplaatje wordt opgenomen, zodat genestelde groepen (subgemeenschappen) wordt toegestaan.

Wanneer een communautaire plaats of groepsmalplaatje de functie van Groepen omvat, is het mogelijk:

* Maak een subcommunity in de auteursomgeving.

* Maak een groep in de publicatieomgeving wanneer deze is geconfigureerd om deze toe te staan.

Wanneer u een groep maakt in de ontwerpomgeving, moet u eerst de communitysite publiceren en vervolgens de groep publiceren. Het publiceren van de communautaire plaats zal de pagina&#39;s van de groep publiceren, zonder de subcommunity&#39;s lidgroepen tot stand te brengen waaraan ACLs wordt geplaatst. Een beperkte (geheime) groep kan dus zichtbaar zijn totdat de groep expliciet wordt gepubliceerd.

## Koppelingen en verwante informatie {#links-and-related-information}

* [Gebruikers en gebruikersgroepen beheren](users.md)
* [Console van groepen Gemeenschappen](groups.md)
* [Functie Groepen](functions.md#groups-function)
* [Groepssjablonen](tools-groups.md)

