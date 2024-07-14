---
title: Essentiële opmerkingen
description: Leer over het werken met het commentaarsysteem (de component van Commentaren) en het beheren van de gebruiker-geproduceerde inhoud (UGC) in de posten van communityleden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8b4034f7-2f97-45ad-96d4-51cfbeae5991
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Essentiële opmerkingen {#comments-essentials}

Deze pagina biedt de basisbeginselen van het werken met het opmerkingssysteem (commentaarcomponent) en opties voor het beheer van de door de gebruiker gegenereerde inhoud (UGC) die wordt geproduceerd wanneer leden opmerkingen of antwoorden plaatsen.

De commentaarcomponent vestigt een commentaarsysteem zodat elke afzonderlijke post door een commentaarcomponent (enkelvoudig) wordt vertegenwoordigd. Het is het opmerkingsysteem dat op de pagina is opgenomen. De afzonderlijke opmerkingen worden gemaakt wanneer deze worden aangeroepen.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong> resourceType </strong></td>
   <td> social/commons/components/hbs/comments</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Ja - de eigenschappen zijn editable op <i> ontwerp </i> wijze</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong> clientlibs </strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.comments<br /> cq.social.hbs.stemden</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td> /libs/social/commons/components/hbs/comments/comments.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong> CSS </strong></td>
   <td> /libs/social/commons/components/hbs/comments/clientlibs/commentsystem.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td> Zie <a href="comments.md"> Gebruikend Commentaren </a></td>
  </tr>
 </tbody>
</table>

[Aanpassingen aan de clientzijde](client-customize.md)

### Eén exemplaar per pagina {#one-instance-per-page}

Paginering en het gebruik van URL&#39;s voor het in cache plaatsen en koppelen vereisen dat de URL uniek is per opmerkingsysteem. Daarom is slechts één instantie van een opmerkingssysteem per pagina toegestaan.

Andere functies zijn al het opmerkingensysteem. Deze zijn:

* [Blog](blog-developer-basics.md)
* [Kalender](calendar-basics-for-developers.md)
* [Bestandsbibliotheek](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [QnA](qna-essentials.md)
* [Revisies](reviews-basics.md)

### Lijst met redenen voor vlag {#flag-reason-list}

De lijst met gemarkeerde redenen kan worden aangepast door een gemarkeerde redenlist.hbs aan uw app toe te voegen om te overschrijven wat zich in

* `/libs/social/commons/components/hbs/comments/comment/flagreasonlist.hbs`

Dit geldt voor alle componenten die een opmerkingsysteem uitbreiden.

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [ Commentaren API ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/comments/api/package-summary.html)

* [ Eindpunten van Commentaren ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/comments/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Toegang tot geposte opmerkingen (UGC) {#accessing-posted-comments-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [ het Modereren van user-Generated Inhoud ](moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [ gemeenschappelijke opslag ](working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [ Overzicht van de Leverancier van het Middel van de Opslag ](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [ SRP en Hoofdzaak UGC ](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [ SocialUtils Refactoring ](socialutils.md) - de Afgekeurde nutsmethodes van de afbeelding aan huidige SRP hulpprogrammamethodes.
