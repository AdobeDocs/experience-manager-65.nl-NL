---
title: Belangrijkste elementen
seo-title: Belangrijkste elementen
description: Overzicht van Liking-component
seo-description: Overzicht van Liking-component
uuid: 89f16859-c901-4090-8e16-363b95c508de
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f176c42b-b16b-42c9-af22-4b6421de5a90
pagetitle: Liking Essentials
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---


# Liking Essentials {#liking-essentials}

De koppelende component, een [tally](tally.md) subklasse, is een nuttig hulpmiddel dat leden toestaat om een positieve mening over een bepaald stuk van inhoud te uiten door het hartpictogram eenvoudig te selecteren.

Het plaatsen van meerdere instanties van een koppelingscomponent op dezelfde pagina is toegestaan. elke instantie moet met een uniek `tally name` bezit worden gevormd.

Anonieme post van een soortgelijk object wordt niet ondersteund. Sitebezoekers moeten zich registreren en aanmelden om deel te nemen aan een abonnement. De ondertekende bezoeker (lid) kan te allen tijde in- en uitschakelen.

## Essentiële elementen voor client-side {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/tally/components/hbs/liking</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Ja - eigenschappen kunnen worden bewerkt in <i>ontwerpmodus </i>modus</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.liking</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td><p>Zie <a href="liking.md">Koppeling gebruiken</a></p> </td>
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

