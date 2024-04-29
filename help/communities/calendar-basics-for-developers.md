---
title: Essentiële elementen van agenda
description: Leer hoe u kunt werken met de functie Kalender in Experience Managers. De kalender steunt de identificatie van bevoorrechte gebruikersgroepen van leden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 069e379d-c6fd-49ca-b337-df6fd466e023
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Essentiële elementen van agenda {#calendar-essentials}

Deze pagina bevat essentiële informatie over het werken met de kalenderfunctie.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

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
   <td> <strong>sjablonen</strong></td>
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

* [Agenda-API&#39;s](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/api/package-summary.html)

* [Kalender-eindpunten](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Kalenderfunctie {#calendar-function}

Een community-sitestructuur die de [Kalenderfunctie](functions.md#calendar-function) heeft een `calendar` geconfigureerd. De functie Kalender ondersteunt het identificeren van een [geprivilegieerde gebruikersgroep](users.md#privileged-members-group).

### Toegang tot agendaberichten (UGC) {#accessing-calendar-posts-ugc}

Met ingang van AEM 6.1. [gemeenschappelijk archief](working-with-srp.md) voor UGC omvat programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

Zie:

* [Overzicht opslagbronprovider](srp.md) - overzicht van het gebruik van introducties en opslagplaatsen
* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-hulpprogrammamethoden en -voorbeelden
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - coderingsrichtlijnen
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - het in kaart brengen van afgekeurde nutsmethodes aan huidige SRP nutsmethodes
