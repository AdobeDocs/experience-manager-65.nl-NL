---
title: Grondbeginselen van de stemming
description: Leer hoe u de component Stemmen gebruikt waarmee leden een bepaald stuk inhoud kunnen beoordelen door pijlen omhoog of omlaag te selecteren om hun mening aan te geven.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: e8ff751f-404a-498d-8e90-62a13ab593ff
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Grondbeginselen van de stemming {#voting-essentials}

De stemcomponent, a [tally](tally.md) subklasse, is een nuttig hulpmiddel dat leden toestaat om een bepaald stuk van inhoud te schatten door eenvoudig pijlen omhoog of onderaan te selecteren om hun mening te wijzen.

Het plaatsen van meerdere instanties van een stemcomponent op dezelfde pagina is toegestaan. Elke instantie moet zijn geconfigureerd met een unieke `tally name` eigenschap.

Anonieme stemplaatsing wordt niet ondersteund. Sitebezoekers moeten zich slechts eenmaal registreren en aanmelden om deel te nemen aan het stemmen. De ondertekende bezoeker (lid) kan te allen tijde hun stem wijzigen.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociaal/tally/onderdelen/hbs/stemming</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Ja - eigenschappen kunnen worden bewerkt in <i>ontwerp </i>mode</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.voting</td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
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

* [Tally API&#39;s](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Eindpunten tellen](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot gebste stemmen (UGC) {#accessing-posted-voting-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1. [gemeenschappelijk archief](working-with-srp.md) voor UGC omvat programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

Zie:

* [Overzicht opslagbronprovider](srp.md) - introductie en overzicht van het gebruik in de opslagplaats.
* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-gebruiksmethoden en -voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - coderingsrichtlijnen.
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - het in kaart brengen van afgekeurde nutsmethodes aan huidige SRP nutsmethodes.
