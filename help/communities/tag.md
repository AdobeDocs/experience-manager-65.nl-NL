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

---


# Grondbeginselen van tags {#tag-essentials}

Wanneer componenten van AEM Communities zijn geconfigureerd met ingeschakelde codering, kunnen leden van de community de inhoud die ze plaatsen, labelen in de publicatieomgeving.

De onderliggende infrastructuur voor tags die worden toegepast in de publicatieomgeving, is gelijk aan de infrastructuur voor tags die worden toegepast op inhoud in de ontwerpomgeving, zoals pagina&#39;s en elementen:

* Zie [Labels](../../help/sites-administering/tags.md) beheren en Door gebruiker gegenereerde inhoud [](tag-ugc.md) labelen (UGC) voor informatie over het maken en beheren van labels.

* Zie [Tags toevoegen voor ontwikkelaars](../../help/sites-developing/tags.md) voor meer informatie over het [coderingsframework](../../help/sites-developing/framework.md) en voor het opnemen en uitbreiden van tags in [aangepaste toepassingen](../../help/sites-developing/building.md).

* Zie [De cloud](tagcloud.md) met sociale tags gebruiken voor informatie aan auteurs over het toevoegen van een `social tag cloud` component aan een pagina om de tags te markeren die in de publicatieomgeving op UGC zijn toegepast.

* Zie Hulpbronnen [voor](tag-resources.md) tagging Enablement voor informatie over het labelen van bronnen voor catalogi.

Het coderen van UGC kan worden toegelaten wanneer het vormen van een [communautaire plaats](sites-console.md#tagging) of één van de volgende eigenschappen:

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

Vanaf [functiepak 1](deploy-communities.md#latestfeaturepack) (FP1) wordt het zoeken naar tags uitgevoerd met behulp van [labeltitels](../../help/sites-developing/framework.md#tag-characteristics).

Voorafgaand aan FP1, werd het onderzoek uitgevoerd gebruikend [markeringsids](../../help/sites-developing/framework.md#tagid).
