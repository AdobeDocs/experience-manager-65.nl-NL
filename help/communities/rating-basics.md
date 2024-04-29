---
title: Grondbeginselen van classificaties
description: Leer hoe leden van de gemeenschap die zich hebben aangemeld een functie op de website kunnen beoordelen met de Beoordelingscomponent, een subklasse van Tally.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 49456944-ff0d-4507-b3b8-143c90067573
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Grondbeginselen van classificaties {#rating-essentials}

De ratingcomponent, [tally](tally.md) subklasse, waarmee leden van de gemeenschap die zich hebben aangemeld een beoordeling kunnen geven voor een functie op de website.

Het plaatsen van meerdere instanties van een stemcomponent op dezelfde pagina is toegestaan. Elke instantie moet zijn geconfigureerd met een unieke `tally name` eigenschap.

Anonieme detachering van een rating wordt niet ondersteund. Sitebezoekers moeten zich slechts eenmaal registreren en aanmelden om deel te nemen aan een waardering. De ondertekende bezoeker (lid) kan zijn beoordeling op elk moment wijzigen.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td> social/tally/components/hbs/rating</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Ja - eigenschappen kunnen worden bewerkt in <i>ontwerp </i>mode</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.rating</td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td><p> /libs/social/tally/components/hbs/rating/rating.hbs<br /> /libs/social/tally/components/hbs/rating/display.hbs<br /> /libs/social/tally/components/hbs/rating/histogram.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/rating/clientlibs/ratingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td><p>Zie <a href="rating.md">Classificatie gebruiken</a></p> </td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Tally API&#39;s](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Eindpunten tellen](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot geposte waarderingen (UGC) {#accessing-posted-ratings-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1. [gemeenschappelijk archief](working-with-srp.md) voor UGC omvat programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

Zie:

* [Overzicht opslagbronprovider](srp.md) - introductie en overzicht van het gebruik in de opslagplaats.
* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-gebruiksmethoden en -voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - coderingsrichtlijnen.
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - het in kaart brengen van afgekeurde nutsmethodes aan huidige SRP nutsmethodes.
