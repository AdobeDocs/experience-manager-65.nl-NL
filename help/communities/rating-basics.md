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

De classificatiecomponent, a [&#x200B; tally &#x200B;](tally.md) subclass, staat binnen ondertekende communautaire leden toe om een eigenschap op de website te schatten.

Het plaatsen van meerdere instanties van een stemcomponent op dezelfde pagina is toegestaan. Elke instantie moet zijn geconfigureerd met een unieke eigenschap `tally name` .

Anonieme detachering van een rating wordt niet ondersteund. Sitebezoekers moeten zich slechts eenmaal registreren en aanmelden om deel te nemen aan een waardering. De ondertekende bezoeker (lid) kan zijn beoordeling op elk moment wijzigen.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong> resourceType </strong></td>
   <td> social/tally/components/hbs/rating</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Ja - de eigenschappen zijn editable op <i> ontwerp </i> wijze</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong> clientlibs </strong></a></td>
   <td> cq.social.hbs.rating</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td><p> /libs/social/tally/components/hbs/rating/rating.hbs<br /> /libs/social/tally/components/hbs/rating/display.hbs<br /> /libs/social/tally/components/hbs/rating/histogram.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/rating/clientlibs/ratingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td><p>Zie <a href="rating.md"> Gebruikend Classificatie </a></p> </td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [&#x200B; Tally APIs &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [&#x200B; Tally Endpoints &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot geposte waarderingen (UGC) {#accessing-posted-ratings-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [&#x200B; het Moderteren van Gebruiker Gegenereerde Inhoud &#x200B;](moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [&#x200B; gemeenschappelijke opslag &#x200B;](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [&#x200B; Overzicht van de Leverancier van het Middel van de Opslag &#x200B;](srp.md) - inleiding en overzicht van het opslagruimtegebruik.
* [&#x200B; SRP en Hoofdzaak UGC &#x200B;](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [&#x200B; die tot UGC met SRP &#x200B;](accessing-ugc-with-srp.md) toegang hebben - codeerrichtlijnen.
* [&#x200B; SocialUtils Refactoring &#x200B;](socialutils.md) - verouderde nutsmethodes in kaart brengen aan huidige SRP nutsmethodes.
