---
title: Clientlibs voor Community-componenten
seo-title: Clientlibs voor Community-componenten
description: Clientbibliotheken voor gemeenschappen
seo-description: Clientbibliotheken voor gemeenschappen
uuid: d2a9f986-96cf-4ee8-81e6-36a96f45ddcb
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 68ce47c8-a03f-40d6-a7f3-2cc64aee0594
docset: aem65
exl-id: 94415926-a273-4f03-b7b6-57fdac12c741
source-git-commit: 1d334c42088342954feb34f6179dc5b134f81bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Clientlibs voor Community-componenten {#clientlibs-for-communities-components}

## Inleiding {#introduction}

In deze sectie van de documentatie wordt beschreven hoe u clientbibliotheken (clientlibs) aan een pagina voor Community-componenten kunt toevoegen.

Voor basisinformatie gaat u naar :

* [Clientzijbibliotheken gebruiken die ](/help/sites-developing/clientlibs.md) gebruiksdetails en foutopsporingsgereedschappen bieden
* [Clientlibs voor ](/help/communities/client-customize.md#clientlibs) SCFwhich verstrekt nuttige informatie wanneer het aanpassen van componenten SCF


## Waarom Clientlibs vereist zijn {#why-clientlibs-are-required}

Clientlibs zijn vereist voor het correct functioneren (JavaScript) en opmaken (CSS) van een component.

Wanneer er een [communautaire functie](/help/communities/functions.md) voor een eigenschap bestaat, zullen alle noodzakelijke componenten en configuraties, met inbegrip van de vereiste clientlibs, in de communautaire plaats aanwezig zijn. Alleen als de auteurs extra componenten ter beschikking moeten hebben, moeten er extra clientlibs worden toegevoegd.

Wanneer de vereiste clientlibs ontbreken, [kan het toevoegen van een communautaire component aan een pagina ](/help/communities/author-communities.md) in fouten javascript evenals een onverwachte verschijning resulteren.

### Voorbeeld: Geplaatste revisies zonder Clientlibs {#example-placed-reviews-without-clientlibs}

![geplaatste revisies](assets/placed-reviews.png)

### Voorbeeld: Geplaatste revisies met clips {#example-placed-reviews-with-clientlibs}

![revisies-clientlibs](assets/reviews-clientlibs.png)

## Vereiste clients identificeren {#identifying-required-clientlibs}

De essenti??le eigenschapinformatie voor ontwikkelaars identificeert de vereiste clientlibs.

Bovendien, van een AEM instantie, die aan [Communautaire Gids van Componenten ](/help/communities/components-guide.md) doorbladert verleent toegang tot een lijst van cli??ntlib categorie??n die voor een component worden vereist.

Bijvoorbeeld helemaal boven aan de pagina [Revisies](https://localhost:4502/content/community-components/en/reviews.html) worden de vereiste clientlibs weergegeven

* cq.ckeditor
* cq.social.hbs.reviews

![clientlibs-reviews](assets/clientlibs-reviews.png)

## Vereiste clips toevoegen {#adding-required-clientlibs}

Wanneer u een Gemeenschapscomponent aan een pagina wilt toevoegen, moet u de vereiste clientlibs voor de component toevoegen als deze nog niet aanwezig is.

Gebruik [CRXDE|Lite](#using-crxde-lite) om een bestaande cli??ntlibslist voor een communautaire plaatspagina te wijzigen.

Een clientlib voor een communitysite toevoegen met [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Blader naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de).
* Zoek het knooppunt `clientlibslist` voor de pagina waaraan u de component wilt toevoegen:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Selecteer `clientlibslist`-knooppunt:

   * Zoek de eigenschap String[] `scg:requiredClientLibs`.
   * Selecteer `Value` om het dialoogvenster String-array te openen.

      * Schuif indien nodig omlaag.
      * Selecteer + om een nieuwe clientbibliotheek in te voeren.

         * Herhaal deze bewerking om meer clientbibliotheken toe te voegen.

         * Selecteer **OK**.
   * Selecteer **Alles opslaan**.


>[!NOTE]
>
>Als de site geen gemeenschapssite is, moet het bestaan of de locatie van de clientbibliotheken die voor de site worden gebruikt, worden gedetecteerd.

Gebruikend [Aan de slag met AEM Communities](/help/communities/getting-started.md) voorbeeld, waar `site-name` *engageren* is, is dit hoe cli??ntliblist zou verschijnen als het toevoegen van de revisiecomponent:

![revisie-component](assets/review-component.png)
