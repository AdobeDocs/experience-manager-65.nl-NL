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
   <td> <strong> resourceType </strong></td>
   <td>sociaal/kalender/onderdelen/hbs/kalender</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong> clientllibs </strong></a></td>
   <td>cq.social.hbs.calendar</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/calendar.hbs</td>
   <td> </td>
  </tr>
  <tr>
   <td> <strong> css </strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/clientlibs/css/calendar.css<br /> /libs/social/calendar/components/hbs/calendar/clientlibs/css/jqueryui.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>zie <a href="calendar.md"> Gebruikend Kalenders </a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [ Kalender APIs ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/api/package-summary.html)

* [ Eindpunten van de Kalender ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Kalenderfunctie {#calendar-function}

Een communautaire plaatsstructuur die de [ functie van de Kalender ](functions.md#calendar-function) omvat heeft een `calendar` gevormde component. De functie van de Kalender steunt het identificeren van a [ bevoorrechte groep van de lidgebruiker ](users.md#privileged-members-group).

### Toegang tot agendaberichten (UGC) {#accessing-calendar-posts-ugc}

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [ gemeenschappelijke opslag ](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [ Overzicht van de Leverancier van het Middel van de Opslag ](srp.md) - inleiding en overzicht van het opslagruimtegebruik
* [ SRP en Hoofdzaak UGC ](srp-and-ugc.md) - de gebruiksmethodes en voorbeelden van SRP
* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - codeerrichtlijnen
* [ SocialUtils die ](socialutils.md) Refactoring - in kaart gebrachte nutsmethodes aan huidige SRP hulpprogrammamethodes
