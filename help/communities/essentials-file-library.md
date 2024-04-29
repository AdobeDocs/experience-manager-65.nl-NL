---
title: Essentiële elementen bestandsbibliotheek
description: Leer meer over de basisbeginselen van het werken met de functie Bestandsbibliotheek in Adobe Experience Manager Communities.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 6d653331-c1ce-4ccb-bb45-656b6413ac3e
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Essentiële elementen bestandsbibliotheek {#file-library-essentials}

Deze pagina bevat de basisinformatie voor het werken met de bestandsbibliotheekfunctie.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/filelibrary/components/hbs/filelibrary</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stemden<br /> cq.social.hbs.filelibrary</td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td> /libs/social/filelibrary/components/hbs/filelibrary/filelibrary.hbs<br /> /libs/social/filelibrary/components/hbs/folder/folder.hbs<br /> /libs/social/filelibrary/components/hbs/folder/item.hbs<br /> /libs/social/filelibrary/components/hbs/document/document.hbs<br /> /libs/social/filelibrary/components/hbs/document/item.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/filelibrary/components/hbs/filelibrary/clientlibs/filelibrary.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="file-library.md">Functie bestandsbibliotheek</a></td>
  </tr>
 </tbody>
</table>

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [API voor bestandsbibliotheek](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/filelibrary/client/api/package-summary.html)

* [Eindpunten bestandsbibliotheek](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/filelibrary/client/endpoints/package-summary.html)

* [Aanpassingen op de server](server-customize.md)

### Functie bestandsbibliotheek {#file-library-function}

Een community-sitestructuur die de [File Library, functie](functions.md#file-library-function)bevat een configuratie `file library` component.

### Opmerkingen benaderen die zijn gepost voor bestandsbibliotheken (UGC) {#accessing-comments-posted-for-file-libraries-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).

Met ingang van AEM 6.1. [gemeenschappelijk archief](working-with-srp.md) voor UGC omvat programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

Zie:

* [Overzicht opslagbronprovider](srp.md) - introductie en overzicht van het gebruik in de opslagplaats.
* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-gebruiksmethoden en -voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - coderingsrichtlijnen.
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - het in kaart brengen van afgekeurde nutsmethodes aan huidige SRP nutsmethodes.
