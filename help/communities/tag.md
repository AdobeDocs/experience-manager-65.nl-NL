---
title: Grondbeginselen van tags
description: Leer over wanneer de componenten van Gemeenschappen met toegelaten etiketteren worden gevormd, kunnen de communautaire leden inhoud etiketteren die zij in publicatiemilieu posten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 6e8af8cf-1239-46f9-b2fe-4aa80abc86ea
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Grondbeginselen van tags {#tag-essentials}

Wanneer AEM Communities-componenten zijn geconfigureerd met codering ingeschakeld, kunnen communityleden de inhoud die ze plaatsen in de publicatieomgeving coderen.

De onderliggende infrastructuur voor tags die worden toegepast in de publicatieomgeving, is gelijk aan de infrastructuur voor tags die worden toegepast op inhoud in de ontwerpomgeving, zoals pagina&#39;s en elementen:

* Zie [Tags beheren](../../help/sites-administering/tags.md) en [Door gebruiker gegenereerde inhoud labelen](tag-ugc.md) (UGC) voor informatie over het maken en beheren van tags.

* Zie [Tags voor ontwikkelaars](../../help/sites-developing/tags.md) voor informatie over de [coderingskader](../../help/sites-developing/framework.md) en tags opnemen en uitbreiden in [aangepaste toepassingen](../../help/sites-developing/building.md).

* Zie [Sociale tagcloud gebruiken](tagcloud.md) voor informatie over het toevoegen van een `social tag cloud` op een pagina om de tags te markeren die in de publicatieomgeving op UGC zijn toegepast.

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
   <td> <strong>sjablonen</strong></td>
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

* [API voor sociale tags](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Sociaal tagbeheer](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

## Zoeken met tags {#tag-searching}

Vanaf [functiepakket 1](deploy-communities.md#latestfeaturepack) (FP1), wordt het zoeken van tags uitgevoerd gebruikend [titels labelen](../../help/sites-developing/framework.md#tag-characteristics).

Vóór FP1 werd het onderzoek uitgevoerd gebruikend [tag id](../../help/sites-developing/framework.md#tagid).
