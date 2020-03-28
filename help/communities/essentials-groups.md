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
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Essentiële elementen van gebruikersgroepen {#community-group-essentials}

De eigenschap van communautaire groepen is de capaciteit voor een subcommunity dynamisch om binnen een communautaire plaats door erkende gebruikers van de publicatie en auteursmilieu&#39;s worden gecreeerd.

Met ingang van [kenmerkpakket 1](deploy-communities.md#latestfeaturepack)van de Gemeenschappen is het mogelijk dat groepen in andere groepen worden genest

## Essentiële elementen voor client-kant {#essentials-for-client-side}

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
   <td> <strong>templates</strong></td>
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

### Functie Groepen {#groups-function}

Een community-sitestructuur die een functie [](functions.md#groups-function) Groepen bevat, ondersteunt het maken van nieuwe sites `community groups` vanuit de publicatie- en auteursomgevingen. De gemaakte community-groep bevat een `community groups member list` component waarin de leden van de groep worden vermeld.

Één of meerdere malplaatjes [van de](tools-groups.md)communautaire groep, die het ontwerp van de pagina(s) van de communautaire groep verstrekken, kunnen voor de functie van Groepen worden gevormd wanneer de functie aan een malplaatje [van de](sites.md) communautaire plaats wordt toegevoegd of binnen een malplaatje van de communautaire groep wordt genesteld.

Het opnemen van veelvoudige communautaire groepsmalplaatjes resulteert in een keus van ontwerp dat aan de erkende gebruiker wordt voorgesteld op het ogenblik dat een nieuwe communautaire groep voor de communautaire plaats wordt gecreeerd, zoals aangetoond in de sectie over [communautaire groepen](creating-groups.md) voor auteurs.

### Geneste groepen {#nested-groups}

Met ingang van het Communautair [KP1](deploy-communities.md#latestfeaturepack)is het mogelijk dat een groepsfunctie wordt opgenomen in een groepssjabloon, zodat geneste groepen (subgemeenschappen) kunnen worden opgenomen.

Wanneer een communautaire plaats of groepsmalplaatje de functie van Groepen omvat, is het mogelijk om

* Subcommunity maken in de ontwerpomgeving
* Creeer een groep in het publicatiemilieu, wanneer gevormd om het toe te staan

Wanneer u een groep maakt in de ontwerpomgeving, moet u eerst de communitysite publiceren en vervolgens de groep publiceren. Het publiceren van de communautaire plaats zal de pagina&#39;s van de groep publiceren, zonder de subcommunity&#39;s lidgroepen tot stand te brengen waaraan ACLs wordt geplaatst. Een beperkte (geheime) groep kan dus zichtbaar zijn totdat de groep expliciet wordt gepubliceerd.

## Koppelingen en verwante informatie {#links-and-related-information}

* [Gebruikers en gebruikersgroepen beheren](users.md)
* [Console van groepen Gemeenschappen](groups.md)
* [Functie Groepen](functions.md#groups-function)
* [Groepssjablonen](tools-groups.md)

