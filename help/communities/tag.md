---
title: Grondbeginselen van tags
seo-title: Grondbeginselen van tags
description: Overzicht van tags
seo-description: Overzicht van tags
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Grondbeginselen van tag {#tag-essentials}

Wanneer AEM Communities-componenten zijn geconfigureerd met codering ingeschakeld, kunnen communityleden de inhoud die ze plaatsen in de publicatieomgeving coderen.

De onderliggende infrastructuur voor tags die worden toegepast in de publicatieomgeving, is gelijk aan de infrastructuur voor tags die worden toegepast op inhoud in de ontwerpomgeving, zoals pagina&#39;s en elementen:

* Zie [Tags beheren](../../help/sites-administering/tags.md) en [Door gebruiker gegenereerde inhoud coderen](tag-ugc.md) (UGC) voor informatie over het maken en beheren van tags.

* Zie [Tags toevoegen voor ontwikkelaars](../../help/sites-developing/tags.md) voor informatie over het [tagging framework](../../help/sites-developing/framework.md) en het opnemen en uitbreiden van tags in [aangepaste toepassingen](../../help/sites-developing/building.md).

* Zie [De cloud van de sociale tag gebruiken](tagcloud.md) voor informatie voor auteurs over het toevoegen van een `social tag cloud`-component aan een pagina om de tags te markeren die in de publicatieomgeving op UGC zijn toegepast.

* Zie [Tags toewijzen Bronnen](tag-resources.md) voor informatie over het labelen van bronnen voor catalogi.

Het coderen van UGC kan worden toegelaten wanneer het vormen van een [communityplaats](sites-console.md#tagging) of één van de volgende eigenschappen:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Bestandsbibliotheek](file-library.md)
* [Forum](forum.md)
* [QnA](working-with-qna.md)

## Essentiële elementen voor client-side {#essentials-for-client-side}

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

## Zoeken naar tags {#tag-searching}

Vanaf [functiepak 1](deploy-communities.md#latestfeaturepack) (FP1) wordt het zoeken naar tags uitgevoerd met behulp van [tagtitels](../../help/sites-developing/framework.md#tag-characteristics).

Voorafgaand aan FP1, werd het onderzoek uitgevoerd gebruikend [markering ids](../../help/sites-developing/framework.md#tagid).
