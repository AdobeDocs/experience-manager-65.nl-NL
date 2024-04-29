---
title: Essentiële elementen activiteitsstroom
description: Lijst van recente activiteiten die door een lid of een lijst van recente activiteiten op één enkele draad van inhoud worden uitgevoerd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: d98bcbe4-3f80-49ec-b40c-417be0d97350
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Essentiële elementen activiteitsstroom {#activity-stream-essentials}

De activiteiten van een ondertekend lid van de gemeenschap, zoals het posten aan een forum of blog, worden verzameld in een stroom die op verschillende manieren door configuratie van de component van activiteitenstromen kan worden gefiltreerd en getoond.

De mogelijkheid om te volgen voegt nog een reeks activiteiten toe wanneer leden van de gemeenschap belangenverklaringen of andere leden van de gemeenschap volgen.

Alles [communitysites](/help/communities/overview.md#communitiessites) Neem een gebruikersprofielpagina op voor het aangemelde lid dat de activiteiten van leden op dezelfde manier weergeeft.

## Concepten {#concepts}

An *activiteitsstroom* is de lijst van recente activiteiten die door een lid worden uitgevoerd of een lijst van recente activiteiten op één enkele draad van inhoud, zoals een forum onderwerp of blog.

Een lid kan een activiteitenstroom volgen, door of een ander individu of inhoud te volgen.

A *nieuwsfeed* is een samenvoeging van de activiteitsstromen die door een lid in één enkele stroom worden gevolgd.

A *[sociale grafiek](/help/communities/essentials-socialgraph.md)* vangt de volgende verhoudingen van één lid aan een andere.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociale/activiteitsstromen/componenten/hbs/activiteitsstromen</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.activitystreams</td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="/help/communities/activities.md">Functie voor activiteitsstromen</a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](/help/communities/client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Activity Streams-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Listener-API voor activiteitsstromen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Aanpassingen op de server](/help/communities/server-customize.md)

### Functie activiteitsstroom {#activity-stream-function}

Een community-sitestructuur die de [Activiteitenstroomfunctie](/help/communities/functions.md#activity-stream-function)bevat een configuratie `activity streams` component.
