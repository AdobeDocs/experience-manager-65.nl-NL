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

* Zie [ het Beheer Markeringen ](../../help/sites-administering/tags.md) en [ het Tags toevoegen van Gebruiker Gegenereerde Inhoud ](tag-ugc.md) (UGC) voor informatie over het creëren van en het beheren van markeringen.

* Zie [ Tags voor Ontwikkelaars ](../../help/sites-developing/tags.md) voor informatie over het [ etiketterende kader ](../../help/sites-developing/framework.md) en het omvatten van en het uitbreiden van markeringen in [ douanetoepassingen ](../../help/sites-developing/building.md).

* Zie [ Gebruikend de Wolk van de Sociale Markering ](tagcloud.md) voor informatie voor auteurs op hoe te om een `social tag cloud` component aan een pagina toe te voegen om de markeringen te benadrukken die op UGC in het publicatiemilieu worden toegepast.

Het etiketteren van UGC kan worden toegelaten wanneer het vormen van a [ communautaire plaats ](sites-console.md#tagging) of één van de volgende eigenschappen:

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
   <td> <strong> resourceType </strong></td>
   <td>social/commons/components/hbs/tagcloud</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong> clientllibs </strong></a></td>
   <td>cq.social.hbs.tagcloud</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong> css </strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="tagcloud.md"> Gebruikend de Wolk van de Sociale Markering </a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [ de Cloud API van de Sociale Markering ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [ Sociale Manager van de Markering ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

## Zoeken met tags {#tag-searching}

Vanaf [ eigenschappak 1 ](deploy-communities.md#latestfeaturepack) (FP1), wordt het zoeken van de markering uitgevoerd gebruikend [ markeringstitels ](../../help/sites-developing/framework.md#tag-characteristics).

Vóór FP1, werd het onderzoek uitgevoerd gebruikend [ markeringsids ](../../help/sites-developing/framework.md#tagid).
