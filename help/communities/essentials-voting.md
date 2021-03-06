---
title: Grondbeginselen van de stemming
seo-title: Grondbeginselen van de stemming
description: Overzicht van de stemcomponent
seo-description: Overzicht van de stemcomponent
uuid: ed0a771d-1c14-4fbf-ab6a-a028e5ee2e2a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 1a947a06-6a5c-4be9-b2fa-e5fa809ff3b8
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---


# Grondbeginselen van de stemming {#voting-essentials}

De stemcomponent, een [tally](tally.md) subklasse, is een nuttig hulpmiddel dat leden toestaat om een bepaald stuk van inhoud te schatten door eenvoudig omhoog of onderaan pijlen te selecteren om hun mening te wijzen.

Het plaatsen van meerdere instanties van een stemcomponent op dezelfde pagina is toegestaan; elke instantie moet met een uniek `tally name` bezit worden gevormd.

Anonieme stemplaatsing wordt niet ondersteund. De bezoekers van de site moeten zich slechts eenmaal registreren en aanmelden om aan de stemming deel te nemen. De ondertekenaar (lid) kan te allen tijde zijn stem wijzigen.

## Essentiële elementen voor client-side {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociaal/tally/onderdelen/hbs/stemming</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Ja - eigenschappen kunnen worden bewerkt in <i>ontwerpmodus </i>modus</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.voting</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td><p> /libs/social/tally/components/hbs/voting/voting.hbs<br /> /libs/social/tally/components/hbs/voting/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/voting/clientlibs/votingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td><p>Zie <a href="voting.md">Stemmen gebruiken</a></p> </td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Tally API&#39;s](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Eindpunten tellen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot Geposte Stemming (UGC) {#accessing-posted-voting-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1 Communities omvat het gebruik van een [common store](working-with-srp.md) voor UGC programmatische toegang tot UGC, ongeacht de gekozen opslagoptie (zoals ASRP, MSRP of JSRP).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

Zie:

* [Overzicht](srp.md)  van Storage Resource Provider - introductie en overzicht van het gebruik van opslagruimten.
* [SRP en de Hoofdzaak](srp-and-ugc.md)  van UGC - SRP nutsmethodes en voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - coderingsrichtlijnen.
* [SocialUtils Refactoring](socialutils.md)  - in kaart gebrachte vervangen nutsmethodes aan huidige SRP hulpprogrammamethodes.

