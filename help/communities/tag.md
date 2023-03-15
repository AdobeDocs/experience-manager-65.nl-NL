---
title: Grondbeginselen van tags
seo-title: Tag Essentials
description: Overzicht van tags
seo-description: Tag overview
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
exl-id: 6e8af8cf-1239-46f9-b2fe-4aa80abc86ea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Grondbeginselen van tags {#tag-essentials}

Wanneer AEM Communities-componenten zijn geconfigureerd met codering ingeschakeld, kunnen communityleden de inhoud die ze plaatsen in de publicatieomgeving coderen.

De onderliggende infrastructuur voor tags die worden toegepast in de publicatieomgeving, is gelijk aan de infrastructuur voor tags die worden toegepast op inhoud in de ontwerpomgeving, zoals pagina&#39;s en elementen:

* Zie [Tags beheren](../../help/sites-administering/tags.md) en [Door gebruiker gegenereerde inhoud labelen](tag-ugc.md) (UGC) voor informatie over het maken en beheren van tags.

* Zie [Tags voor ontwikkelaars](../../help/sites-developing/tags.md) voor informatie over de [coderingskader](../../help/sites-developing/framework.md) alsmede tags opnemen en uitbreiden in [aangepaste toepassingen](../../help/sites-developing/building.md).

* Zie [Sociale tagcloud gebruiken](tagcloud.md) voor informatie aan auteurs over het toevoegen van een `social tag cloud` op een pagina om de tags te markeren die in de publicatieomgeving op UGC zijn toegepast.

* Zie [Tags toewijzen](tag-resources.md) voor informatie over het coderen van bronnen voor catalogi.

Tags voor UGC kunnen zijn ingeschakeld wanneer u een [community-site](sites-console.md#tagging) of een van de volgende kenmerken:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Bestandsbibliotheek](file-library.md)
* [Forum](forum.md)
* [QnA](working-with-qna.md)

## Essentiële elementen voor client-kant {#essentials-for-client-side}

### Sociale-tagcloud {#social-tag-cloud}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/commons/components/hbs/tagcloud</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.tagcloud</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="tagcloud.md">Sociale tagcloud gebruiken</a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [API voor sociale tags](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Sociaal tagbeheer](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

## Zoeken met tags {#tag-searching}

Vanaf [functiepakket 1](deploy-communities.md#latestfeaturepack) (FP1), wordt het zoeken van tags uitgevoerd gebruikend [titels labelen](../../help/sites-developing/framework.md#tag-characteristics).

Voorafgaand aan FP1, werd het onderzoek uitgevoerd gebruikend [tag id](../../help/sites-developing/framework.md#tagid).
