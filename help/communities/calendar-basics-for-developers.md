---
title: Essentiële elementen van agenda
seo-title: Essentiële elementen van agenda
description: Overzicht van de functie Kalender
seo-description: Overzicht van de functie Kalender
uuid: 14ff7a83-b2a7-4f7e-8ee7-88f336329a1a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 88932a3c-ba7f-47ba-9e0b-206755c2d42e
translation-type: tm+mt
source-git-commit: 82affd528f2526384b319fe89082e0f574ab5855
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 1%

---


# Essentiële elementen voor kalender {#calendar-essentials}

Deze pagina bevat essentiële informatie over het werken met de kalenderfunctie.

## Essentiële elementen voor client-side {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociaal/kalender/onderdelen/hbs/kalender</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.calendar</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/calendar.hbs</td>
   <td> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/clientlibs/css/calendar.css<br /> /libs/social/calendar/components/hbs/calendar/clientlibs/css/jqueryui.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>zie <a href="calendar.md">Kalenders gebruiken</a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Agenda-API&#39;s](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/calendar/client/api/package-summary.html)

* [Kalender-eindpunten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/calendar/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Kalenderfunctie {#calendar-function}

Een community-sitestructuur die de [Kalenderfunctie](functions.md#calendar-function) bevat, heeft een geconfigureerde `calendar`-component. De functie van de Kalender steunt het identificeren van een [bevoorrechte gebruikersgroep](users.md#privileged-members-group).

### Toegang tot agendaberichten (UGC) {#accessing-calendar-posts-ugc}

Met ingang van AEM 6.1 Communities omvat het gebruik van een [common store](working-with-srp.md) voor UGC programmatische toegang tot UGC, ongeacht de gekozen opslagoptie (zoals ASRP, MSRP of JSRP).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

Zie:

* [Overzicht](srp.md)  van Storage Resource Provider - inleiding en overzicht van opslaggebruik
* [SRP en de Hoofdzaak](srp-and-ugc.md)  UGC - SRP nutsmethodes en voorbeelden
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - coderingsrichtlijnen
* [SocialUtils Refactoring](socialutils.md)  - in kaart gebrachte vervangen nutsmethodes aan huidige SRP hulpprogrammamethodes

