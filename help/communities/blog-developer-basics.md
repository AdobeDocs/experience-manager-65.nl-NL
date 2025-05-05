---
title: Grondbeginselen van blogs
description: Leer hoe u de functie Blog aan een pagina kunt toevoegen, zodat leden van de gemeenschap die zich hebben aangemeld, blogartikelen kunnen plaatsen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 51f616e8-4aba-47f6-b948-d5147d84bbb6
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Grondbeginselen van blogs {#blog-essentials}

Vanaf AEM 6.1 Communities is een blog een gemeenschapsactiviteit. Blogartikelen worden nu vanuit de publicatieomgeving gepost, waar eerder blogartikelen alleen in de auteursomgeving konden worden gemaakt en gepubliceerd.

Blogartikelen kunnen nu door elk lid van de gemeenschap worden gemaakt, tenzij ze beperkt zijn tot geprivilegieerde leden.

Deze pagina bevat de essentiële informatie voor het werken met de blogfunctie.

>[!NOTE]
>
>De onderliggende infrastructuur van de blogfunctie is de journaalfunctie.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

De blogeigenschap is samengesteld uit twee belangrijkste componenten die beschikbaar zijn door de [ functie van Blog ](/help/communities/functions.md#blog-function) toe te voegen of door de componenten aan een pagina op auteur toe te voegen geeft wijze uit.

### Blog {#blog}

<table>
 <tbody>
  <tr>
   <td> <strong> resourceType </strong></td>
   <td>social/journaal/components/hbs/tijdschrift</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong> clientllibs </strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stemed<br /> cq.social.hbs.journaal</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td>
  </tr>
  <tr>
   <td> <strong> css </strong></td>
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>zie </a> de Eigenschap van 0&rbrace; Blog<a href="/help/communities/blog-feature.md"></td>
  </tr>
 </tbody>
</table>

### Blog Sidebar {#blog-sidebar}

| **resourceType** | sociaal/journaal/componenten/hbs/zijbalk |
|---|---|
| [**inbegrepen**](/help/communities/scf.md#add-or-include-a-communities-component) | Nee |
| [**clientllibs**](/help/communities/clientlibs.md) | cq.social.hbs.journal_sidebar |
| **malplaatjes** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **eigenschappen** | zie [&#128279;](/help/communities/blog-feature.md) de Eigenschap van 0&rbrace; Blog |

* [Aanpassingen aan de clientzijde](/help/communities/client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [ Blog API ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [ Blogeindpunten ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Aanpassingen op de server](/help/communities/server-customize.md)

### Blogfunctie {#blog-function}

Een communautaire plaatsstructuur die de [ functie Blog ](/help/communities/functions.md#blog-function) omvat heeft `Blog` en `Blog Sidebar` gevormde componenten. De functie Blog steunt het identificeren van a [ bevoorrechte gebruikersgroep van het lidlid ](/help/communities/users.md#privileged-members-group).

### Toegang tot blogberichten (UGC) {#accessing-blog-entries-ugc}

UGC moet worden gemoderniseerd met behulp van een van de standaardmethoden voor gematigdheid.
Zie [ het Moderteren van Gebruiker Gegenereerde Inhoud ](/help/communities/moderate-ugc.md).

Vanaf AEM 6.1 Gemeenschappen, omvat het gebruik van a [ gemeenschappelijke opslag ](/help/communities/working-with-srp.md) voor UGC programmatic toegang tot UGC ongeacht de gekozen opslagoptie (zoals ASRP, MSRP, of JSRP).

**de plaats en het formaat van UGC in de bewaarplaats zijn onderworpen aan verandering zonder waarschuwing**.

Zie:

* [ Overzicht van de Leverancier van het Middel van de Opslag ](/help/communities/srp.md) - inleiding en overzicht van het opslagruimtegebruik.
* [ SRP en Hoofdzaak UGC ](/help/communities/srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [ die tot UGC met SRP ](/help/communities/accessing-ugc-with-srp.md) toegang hebben - codeerrichtlijnen.
* [ SocialUtils Refactoring ](/help/communities/socialutils.md) - verouderde nutsmethodes in kaart brengen aan huidige SRP nutsmethodes.

## Primaire uitgever {#primary-publisher}

Wanneer de plaatsing een publicatielandbouwbedrijf is, is het noodzakelijk om een primaire uitgever te identificeren die voor te publiceren artikelen opiniepeilt.

Zie [ Primaire Uitgever ](/help/communities/deploy-communities.md#primary-publisher) voor meer details.

## Rijke media toestaan {#allowing-rich-media}

Het AEM platform blokkeert koppelingen van andere websites om XSS-aanvallen te voorkomen zoals beschreven in

* [Protect tegen XSS (Cross-Site Scripting)](/help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Vanaf AEM 6.2 worden de eerder vereiste wijzigingen die handmatig moeten worden aangebracht, opgenomen in het standaard AntiSamy-configuratiebestand.

Rijke media wordt ingesloten in een blogartikel door het pictogram `Embed Media from External Sites` te selecteren:

![ media ](assets/media-icon.png)
