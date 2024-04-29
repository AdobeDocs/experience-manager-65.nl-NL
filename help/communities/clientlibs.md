---
title: Clientlibs voor Community-componenten
description: Leer hoe u clientbibliotheken (clientlibs) aan de clientzijde aan een pagina toevoegt, zodat u gebruiksdetails kunt verzamelen en foutopsporingsgereedschappen kunt gebruiken voor de onderdelen van de Gemeenschappen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 94415926-a273-4f03-b7b6-57fdac12c741
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Clientlibs voor Community-componenten {#clientlibs-for-communities-components}

## Inleiding {#introduction}

In deze sectie van de documentatie wordt beschreven hoe u clientbibliotheken (clientlibs) aan een pagina voor Community-componenten kunt toevoegen.

Zie voor basisinformatie het volgende:

* [Client-Side bibliotheken gebruiken](/help/sites-developing/clientlibs.md) die gebruiksdetails en het zuiveren hulpmiddelen verstrekt
* [Clientlibs voor SCF](/help/communities/client-customize.md#clientlibs) die nuttige informatie verstrekt wanneer het aanpassen van componenten SCF


## Waarom Clientlibs vereist zijn {#why-clientlibs-are-required}

Clientlibs zijn vereist voor het correct functioneren (JavaScript) en opmaken (CSS) van een component.

Wanneer er een [gemeenschapsfunctie](/help/communities/functions.md) voor een eigenschap, zijn alle noodzakelijke componenten en configuraties, met inbegrip van de vereiste clientlibs, aanwezig in de communautaire plaats. Alleen als de auteurs extra componenten ter beschikking moeten hebben, moeten er extra clientlibs worden toegevoegd.

Wanneer de vereiste clientlibs ontbreken, [een onderdeel van een Gemeenschappen aan een pagina toevoegen](/help/communities/author-communities.md) kan resulteren in JavaScript-fouten en een onverwachte weergave.

### Voorbeeld: Geplaatste revisies zonder Clientlibs {#example-placed-reviews-without-clientlibs}

![geplaatste beoordelingen](assets/placed-reviews.png)

### Voorbeeld: Geplaatste revisies met clips {#example-placed-reviews-with-clientlibs}

![revisies-clientlibs](assets/reviews-clientlibs.png)

## Vereiste clients identificeren {#identifying-required-clientlibs}

De essentiële eigenschapinformatie voor ontwikkelaars identificeert de vereiste clientlibs.

Bovendien kunt u vanuit een AEM naar de [Community Components Guide](/help/communities/components-guide.md) biedt toegang tot een lijst met clientlib-categorieën die vereist zijn voor een component.

Bijvoorbeeld, bij de bovenkant van [Pagina Revisies](https://localhost:4502/content/community-components/en/reviews.html) de vereiste clientlibs worden vermeld

* cq.ckeditor
* cq.social.hbs.reviews

![clientlibs-reviews](assets/clientlibs-reviews.png)

## Vereiste clips toevoegen {#adding-required-clientlibs}

Wanneer u een Gemeenschapscomponent aan een pagina wilt toevoegen, moet u de vereiste clientlibs voor de component toevoegen als deze nog niet aanwezig is.

Gebruiken [CRXDE|Lite](#using-crxde-lite) om een bestaande clientlibslist voor een communautaire plaatspagina te wijzigen.

Een clientlib voor een communautaire plaats toevoegen door te gebruiken [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Bladeren naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de).
* Zoek de `clientlibslist` knooppunt voor de pagina waarop u de component wilt toevoegen:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Met `clientlibslist` geselecteerd knooppunt:

   * De tekenreeks zoeken[] eigenschap `scg:requiredClientLibs`.
   * Selecteer zijn `Value` zodat u toegang hebt tot het dialoogvenster String-array.

      * Schuif indien nodig omlaag.
      * Selecteer + om een nieuwe clientbibliotheek in te voeren.

         * Herhaal deze bewerking om meer clientbibliotheken toe te voegen.

         * Selecteren **OK**.

   * Selecteren **Alles opslaan**.

>[!NOTE]
>
>Als de site geen gemeenschapssite is, moet het bestaan of de locatie van de clientbibliotheken die voor de site worden gebruikt, worden gedetecteerd.

Met de [Aan de slag met AEM Communities](/help/communities/getting-started.md) voorbeeld, waarbij `site-name` is *aangaan*, is dit hoe de clientliblist zou verschijnen als het toevoegen van de revisiecomponent:

![revisie-component](assets/review-component.png)
