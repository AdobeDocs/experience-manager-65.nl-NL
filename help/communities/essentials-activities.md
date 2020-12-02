---
title: Essentiële elementen activiteitsstroom
seo-title: Essentiële elementen activiteitsstroom
description: Lijst van recente activiteiten die door een lid of een lijst van recente activiteiten op één enkele draad van inhoud worden uitgevoerd
seo-description: Lijst van recente activiteiten die door een lid of een lijst van recente activiteiten op één enkele draad van inhoud worden uitgevoerd
uuid: 30c5ac08-0af0-4670-9d81-0beb5c93e00a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8714b456-527a-457b-82c4-21bd445dfd9c
docset: aem65
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Essentiële elementen activiteitsstroom {#activity-stream-essentials}

De activiteiten van een ondertekend lid van de gemeenschap, zoals het posten aan een forum of blog, worden verzameld in een stroom die op verschillende manieren door configuratie van de component van activiteitenstromen kan worden gefiltreerd en getoond.

De mogelijkheid om te volgen voegt nog een reeks activiteiten toe wanneer leden van de gemeenschap belangenverklaringen of andere leden van de gemeenschap volgen.

Alle [communitysites](/help/communities/overview.md#communitiessites) bevatten een gebruikersprofielpagina voor het ondertekende lid dat lidactiviteiten op dezelfde manier zal tonen.

## Concepten {#concepts}

Een *activiteitsstroom* is de lijst van recente activiteiten die door een lid of een lijst van recente activiteiten op één enkele draad van inhoud, zoals een forumonderwerp of blog worden uitgevoerd.

Een lid kan een activiteitenstroom volgen, door of een ander individu of inhoud te volgen.

Een *nieuwsfeed* is een samenvoeging van de activiteitenstromen die door een lid in één enkele stroom worden gevolgd.

A *[social graph](/help/communities/essentials-socialgraph.md)* vangt de volgende verhoudingen van één lid aan een andere.

## Essentiële elementen voor client-side {#essentials-for-client-side}

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
   <td> <strong>templates</strong></td>
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

* [Activity Streams Listener-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Aanpassingen op de server](/help/communities/server-customize.md)

### Functie activiteitsstroom {#activity-stream-function}

Een community-sitestructuur die de [Activiteitenstroomfunctie](/help/communities/functions.md#activity-stream-function) bevat, bevat een geconfigureerde `activity streams`-component.
