---
title: QnA Essentials
seo-title: QnA Essentials
description: Functie van forum met vragen en antwoorden
seo-description: Functie van forum met vragen en antwoorden
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
translation-type: tm+mt
source-git-commit: ca15258a5dc7ca99b6c9d6ae85e42c77a3802c87

---


# QnA Essentials {#qna-essentials}

Deze pagina bevat de essentiële informatie voor het werken met de functie voor vragen en antwoorden (QnA)-forums.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> resourceType</td>
   <td>social/qna/components/hbs/qnaforum</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">inclusief</a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stemden<br /> cq.social.hbs.qna</td>
  </tr>
  <tr>
   <td> templates</td>
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td>
  </tr>
  <tr>
   <td> css</td>
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td>
  </tr>
  <tr>
   <td> eigenschappen</td>
   <td>Zie <a href="working-with-qna.md">Functie Vragen en antwoorden-forum</a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [QnA API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [QnA-eindpunten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### QnA-functie {#qna-function}

Een communautaire plaatsstructuur die de functie [](functions.md#qna-function) QnA omvat zal een gevormde `QnA` component, evenals montages hebben die moderatie en het etiketteren beïnvloeden. De functie QnA steunt het identificeren van een [bevoorrechte gebruikersgroep](users.md#privileged-members-group)van het lid.

### Toegang tot berichten van het Forum QnA (UGC) {#accessing-qna-forum-posts-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie Door de gebruiker gegenereerde inhoud [modereren](moderate-ugc.md).

Vanaf AEM 6.1 Communities omvat het gebruik van een [gemeenschappelijke opslag](working-with-srp.md) voor UGC programmatische toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP of JSRP).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

Zie:

* [Overzicht](srp.md) van Storage Resource Provider - introductie en overzicht van het gebruik van opslagruimten.
* [SRP en de Hoofdzaak](srp-and-ugc.md) UGC - SRP nutsmethodes en voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - coderingsrichtlijnen.
* [SocialUtils Refactoring](socialutils.md) - het in kaart brengen verouderde nutsmethodes aan huidige SRP nutsmethodes.

