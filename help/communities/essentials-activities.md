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

Alle [ communautaire plaatsen ](/help/communities/overview.md#communitiessites) omvatten een pagina van het gebruikersprofiel voor het ondertekende in lid dat lidactiviteiten op de zelfde manier zal tonen.

## Concepten {#concepts}

Een *activiteitenstroom* is de lijst van recente activiteiten die door een lid of een lijst van recente activiteiten op één enkele draad van inhoud, zoals een forumonderwerp of blog worden uitgevoerd.

Een lid kan een activiteitenstroom volgen, door of een ander individu of inhoud te volgen.

A *nieuwsvoer* is een samenvoeging van de activiteitenstromen die door een lid in één enkele stroom worden gevolgd.

A *[sociale grafiek](/help/communities/essentials-socialgraph.md)* vangt de volgende verhoudingen van één lid aan een andere.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong> resourceType </strong></td>
   <td>sociale/activiteitsstromen/componenten/hbs/activiteitsstromen</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong> clientllibs </strong></a></td>
   <td>cq.social.hbs.activitystreams</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td>
  </tr>
  <tr>
   <td> <strong> css </strong></td>
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie {de Eigenschap van de Streams van 0} Activiteit </a><a href="/help/communities/activities.md"></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](/help/communities/client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [ Streams API van de Activiteit ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [ de Listener van de Streams van de Activiteit API ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Aanpassingen op de server](/help/communities/server-customize.md)

### Functie activiteitsstroom {#activity-stream-function}

Een communautaire plaatsstructuur die de [ functie van de Stream van de Activiteit ](/help/communities/functions.md#activity-stream-function) omvat, omvat een gevormde `activity streams` component.
