---
title: Grondbeginselen van blogs
seo-title: Grondbeginselen van blogs
description: Blogoverzicht
seo-description: Blogoverzicht
uuid: 714cf70c-76a0-4be6-9163-a31ac6bd1643
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eece7b8f-6ccd-4037-8713-0cd36cfd9e73
docset: aem65
translation-type: tm+mt
source-git-commit: e74d39e63f8b3b5961ea2c31e0ef99c3ab8b06dd
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 1%

---


# Grondbeginselen van blogs {#blog-essentials}

Vanaf AEM 6.1 Communities is een blog een gemeenschapsactiviteit. Blogartikelen worden nu vanuit de publicatieomgeving gepost, waar eerder blogartikelen alleen in de auteursomgeving konden worden gemaakt en gepubliceerd.

Blogartikelen kunnen nu door elk lid van de gemeenschap worden gemaakt, tenzij ze beperkt zijn tot geprivilegieerde leden.

Deze pagina bevat de essentiële informatie voor het werken met de blogfunctie.

>[!NOTE]
>
>De onderliggende infrastructuur van de blogfunctie is de journaalfunctie.


## Essentiële elementen voor client-kant {#essentials-for-client-side}

De blogfunctie bestaat uit twee hoofdcomponenten die beschikbaar zijn door de functie [](/help/communities/functions.md#blog-function) Blog toe te voegen of door de componenten in de modus Schrijven aan een pagina toe te voegen.

### Blog {#blog}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/journaal/components/hbs/tijdschrift</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stemed<br /> cq.social.hbs.journaal</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>zie <a href="/help/communities/blog-feature.md">Blogfunctie</a></td>
  </tr>
 </tbody>
</table>

### Blog Sidebar {#blog-sidebar}

| **resourceType** | sociaal/journaal/componenten/hbs/zijbalk |
|---|---|
| [**inclusief **](/help/communities/scf.md#add-or-include-a-communities-component) | Nee |
| [**clientllibs **](/help/communities/clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **eigenschappen** | zie [Blogfunctie](/help/communities/blog-feature.md) |

* [Aanpassingen aan de clientzijde](/help/communities/client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Blog API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Blogeindpunten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Aanpassingen op de server](/help/communities/server-customize.md)

### Blogfunctie {#blog-function}

Een community-sitestructuur die de functie [](/help/communities/functions.md#blog-function) Blog bevat, heeft geconfigureerd `Blog` en `Blog Sidebar` componenten. De functie Blog steunt het identificeren van een [bevoorrechte gebruikersgroep](/help/communities/users.md#privileged-members-group)van het lid.

### Toegang tot blogberichten (UGC) {#accessing-blog-entries-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie Door de gebruiker gegenereerde inhoud [modereren](/help/communities/moderate-ugc.md).

Vanaf AEM 6.1 Communities omvat het gebruik van een [gemeenschappelijke opslag](/help/communities/working-with-srp.md) voor UGC programmatische toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP of JSRP).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

Zie :

* [Overzicht](/help/communities/srp.md) van Storage Resource Provider - introductie en overzicht van het gebruik van opslagruimten.
* [SRP en de Hoofdzaak](/help/communities/srp-and-ugc.md) UGC - SRP nutsmethodes en voorbeelden.
* [Toegang tot UGC met SRP](/help/communities/accessing-ugc-with-srp.md) - coderingsrichtlijnen.
* [SocialUtils Refactoring](/help/communities/socialutils.md) - het in kaart brengen verouderde nutsmethodes aan huidige SRP nutsmethodes.

## Primaire uitgever {#primary-publisher}

Wanneer de plaatsing een publicatielandbouwbedrijf is, is het noodzakelijk om een primaire uitgever te identificeren die voor te publiceren artikelen zal opiniepeilen.

Zie [Primaire uitgever](/help/communities/deploy-communities.md#primary-publisher) voor meer informatie.

## Rijke media toestaan {#allowing-rich-media}

Het AEM-platform blokkeert koppelingen van andere websites om XSS-aanvallen te voorkomen zoals beschreven in

* [Beveiligen tegen XSS (Cross-Site Scripting)](/help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Vanaf AEM 6.2, zijn de wijzigingen die eerder manueel moeten worden gemaakt inbegrepen in het standaard antiSamy configuratiedossier.

Rijke media wordt ingesloten in een blogartikel door het `Embed Media from External Sites` pictogram te selecteren:

![chlimage_1-471](assets/chlimage_1-471.png)

