---
title: QnA Essentials
description: Leer de grondbeginselen van het werken met de vraag en de antwoorden (QnA) eigenschap van het Forum in de Gemeenschappen van Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: a7b295c1-cc9d-4881-8016-804b21fc1098
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

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
   <td> <a href="scf.md#add-or-include-a-communities-component"> omvatten </a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"> clientllibs </a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stemed<br /> cq.social.hbs.qna</td>
  </tr>
  <tr>
   <td> sjablonen</td>
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td>
  </tr>
  <tr>
   <td> css</td>
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td>
  </tr>
  <tr>
   <td> eigenschappen</td>
   <td>Zie {de Eigenschap van het Forum van 0} Q&amp;A </a><a href="working-with-qna.md"></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [&#x200B; QnA API &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [&#x200B; QnA Eindpunten &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### QnA-functie {#qna-function}

Een communautaire plaatsstructuur die de [&#x200B; functie QnA &#x200B;](functions.md#qna-function) omvat heeft een gevormde `QnA` component, en montages die moderatie en het etiketteren beïnvloeden. De functie QnA steunt het identificeren van a [&#x200B; bevoorrechte gebruikersgroep van het lidlid &#x200B;](users.md#privileged-members-group).

### Toegang tot berichten van het Forum QnA (UGC) {#accessing-qna-forum-posts-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [&#x200B; het Modereren van user-Generated Inhoud &#x200B;](moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [&#x200B; gemeenschappelijke opslag &#x200B;](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [&#x200B; Overzicht van de Leverancier van het Middel van de Opslag &#x200B;](srp.md) - inleiding en overzicht van het opslagruimtegebruik.
* [&#x200B; SRP en Hoofdzaak UGC &#x200B;](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [&#x200B; die tot UGC met SRP &#x200B;](accessing-ugc-with-srp.md) toegang hebben - codeerrichtlijnen.
* [&#x200B; SocialUtils Refactoring &#x200B;](socialutils.md) - verouderde nutsmethodes in kaart brengen aan huidige SRP nutsmethodes.
