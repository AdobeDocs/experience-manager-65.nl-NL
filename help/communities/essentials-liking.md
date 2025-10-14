---
title: Belangrijkste elementen
description: Leer hoe u de component Liking gebruikt, een handig hulpmiddel waarmee leden een positief advies over bepaalde inhoud kunnen geven door het hartpictogram te selecteren.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
pagetitle: Liking Essentials
exl-id: ef314385-cd5c-411c-91df-83691a81c1bc
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Belangrijkste elementen {#liking-essentials}

De Liking component, a [&#x200B; tally &#x200B;](tally.md) subclass, is een nuttig hulpmiddel dat leden toestaat om een positieve mening over een bepaald stuk van inhoud te uiten door het hartpictogram eenvoudig te selecteren.

Het plaatsen van meerdere instanties van een koppelingscomponent op dezelfde pagina is toegestaan. Elke instantie moet zijn geconfigureerd met een unieke eigenschap `tally name` .

Anonieme post van een soortgelijk object wordt niet ondersteund. Sitebezoekers moeten zich registreren en aanmelden om deel te nemen aan een abonnement. De ondertekende bezoeker (lid) kan te allen tijde in- en uitschakelen.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong> resourceType </strong></td>
   <td>social/tally/components/hbs/liking</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Ja - de eigenschappen zijn editable op <i> ontwerp </i> wijze</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong> clientlibs </strong></a></td>
   <td> cq.social.hbs.liking</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td><p>Zie <a href="liking.md"> Gebruikend het Verschijnen </a></p> </td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [&#x200B; Tally APIs &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [&#x200B; Tally Endpoints &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot gebste stemmen (UGC) {#accessing-posted-voting-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [&#x200B; het Moderteren van Gebruiker Gegenereerde Inhoud &#x200B;](moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [&#x200B; gemeenschappelijke opslag &#x200B;](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [&#x200B; Overzicht van de Leverancier van het Middel van de Opslag &#x200B;](srp.md) - inleiding en overzicht van het opslagruimtegebruik.
* [&#x200B; SRP en Hoofdzaak UGC &#x200B;](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [&#x200B; die tot UGC met SRP &#x200B;](accessing-ugc-with-srp.md) toegang hebben - codeerrichtlijnen.
* [&#x200B; SocialUtils Refactoring &#x200B;](socialutils.md) - verouderde nutsmethodes in kaart brengen aan huidige SRP nutsmethodes.
