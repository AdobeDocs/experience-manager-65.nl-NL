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
translation-type: tm+mt
source-git-commit: efa6c7be93908b2f264da4689caa9c02912c0f0a
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Clientlibs voor Community-componenten {#clientlibs-for-communities-components}

## Inleiding {#introduction}

In deze sectie van de documentatie wordt beschreven hoe u clientbibliotheken (clientlibs) aan een pagina voor Community-componenten kunt toevoegen.

Voor basisinformatie gaat u naar :

* [Clientzijbibliotheken](/help/sites-developing/clientlibs.md) gebruiken die zowel gebruiksdetails als foutopsporingsgereedschappen bieden
* [Clientlibs voor SCF](/help/communities/client-customize.md#clientlibs) die nuttige informatie wanneer het aanpassen van componenten SCF verstrekt
* [Blog: AEM-clientbibliotheken, zoals in het voorbeeld wordt uitgelegd](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Waarom Clientlibs vereist zijn {#why-clientlibs-are-required}

Clientlibs zijn vereist voor het correct functioneren (JavaScript) en opmaken (CSS) van een component.

Wanneer er een [communautaire functie](/help/communities/functions.md) voor een eigenschap bestaat, zullen alle noodzakelijke componenten en configuraties, met inbegrip van de vereiste clientlibs, in de communautaire plaats aanwezig zijn. Alleen als de auteurs extra componenten ter beschikking moeten hebben, moeten er extra clientlibs worden toegevoegd.

Wanneer de vereiste clientlibs ontbreken, kan het [toevoegen van een Community-component aan een pagina](/help/communities/author-communities.md) leiden tot JavaScript-fouten en een onverwachte weergave.

### Voorbeeld: Geplaatste revisies zonder Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-426](assets/chlimage_1-426.png)

### Voorbeeld: Geplaatste revisies met clips {#example-placed-reviews-with-clientlibs}

![chlimage_1-427](assets/chlimage_1-427.png)

## Vereiste clients identificeren {#identifying-required-clientlibs}

De essentiële eigenschapinformatie voor ontwikkelaars identificeert de vereiste clientlibs.

Bovendien, van een instantie AEM, die aan de Gids [van Componenten van de](/help/communities/components-guide.md) Gemeenschap doorbladert verleent toegang tot een lijst van cliëntlib categorieën voor een component worden vereist.

Bijvoorbeeld helemaal boven aan de pagina [](https://localhost:4502/content/community-components/en/reviews.html) Revisies worden de vereiste clientlibs weergegeven

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Vereiste clips toevoegen {#adding-required-clientlibs}

Wanneer u een Gemeenschapscomponent aan een pagina wilt toevoegen, moet u de vereiste clientlibs voor de component toevoegen als deze nog niet aanwezig is.

Gebruik [CRXDE|Lite](#using-crxde-lite) om een bestaande cliëntlibslist voor een communautaire plaatspagina te wijzigen.

Om een clientlib voor een communautaire plaats toe te voegen gebruikend [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Blader naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de).
* Zoek het `clientlibslist` knooppunt voor de pagina waaraan u de component wilt toevoegen:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Selecteer `clientlibslist` knooppunt:

   * Zoek de eigenschap String[] `scg:requiredClientLibs`.
   * Selecteer het `Value` item om het dialoogvenster String-array te openen.

      * Schuif indien nodig omlaag.
      * Selecteer + om een nieuwe clientbibliotheek in te voeren.

         * Herhaal deze bewerking om meer clientbibliotheken toe te voegen.

         * Selecteer **OK**.
   * Selecteer **Alles** opslaan.


>[!NOTE]
>
>Als de site geen gemeenschapssite is, moet het bestaan of de locatie van de clientbibliotheken die voor de site worden gebruikt, worden gedetecteerd.


Gebruikend het [Begonnen worden met het voorbeeld van AEM Communities](/help/communities/getting-started.md) , waar `site-name` is *geëngageerd*, is dit hoe cliëntliblist zou verschijnen als het toevoegen van de revisiecomponent:

![chlimage_1-247](assets/chlimage_1-247.png)

