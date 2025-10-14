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

* [&#x200B; Gebruikend cliënt-Kant Bibliotheken &#x200B;](/help/sites-developing/clientlibs.md) die gebruiksdetails en het zuiveren hulpmiddelen verstrekt
* [&#x200B; Clientlibs voor SCF &#x200B;](/help/communities/client-customize.md#clientlibs) die nuttige informatie wanneer het aanpassen van componenten SCF verstrekt


## Waarom Clientlibs vereist zijn {#why-clientlibs-are-required}

Clientlibs zijn vereist voor het correct functioneren (JavaScript) en opmaken (CSS) van een component.

Wanneer er a [&#x200B; communautaire functie &#x200B;](/help/communities/functions.md) voor een eigenschap bestaat, zijn alle noodzakelijke componenten en configuraties, met inbegrip van de vereiste clientlibs, aanwezig in de communautaire plaats. Alleen als de auteurs extra componenten ter beschikking moeten hebben, moeten er extra clientlibs worden toegevoegd.

Wanneer de vereiste clientlibs ontbreken, [&#x200B; toevoegend een component van Gemeenschappen aan een pagina &#x200B;](/help/communities/author-communities.md) in de fouten van JavaScript en een onverwachte verschijning kon resulteren.

### Voorbeeld: Geplaatste revisies zonder Clientlibs {#example-placed-reviews-without-clientlibs}

![&#x200B; geplaatst-overzichten &#x200B;](assets/placed-reviews.png)

### Voorbeeld: Geplaatste revisies met clips {#example-placed-reviews-with-clientlibs}

![&#x200B; revisies-clientlibs &#x200B;](assets/reviews-clientlibs.png)

## Vereiste clients identificeren {#identifying-required-clientlibs}

De essentiële eigenschapinformatie voor ontwikkelaars identificeert de vereiste clientlibs.

Bovendien van een AEM instantie, die aan de [&#x200B; Communautaire Gids van Componenten &#x200B;](/help/communities/components-guide.md) doorbladert verleent toegang tot een lijst van cliëntlib categorieën die voor een component worden vereist.

Bijvoorbeeld, bij de bovenkant van de [&#x200B; pagina van Revisies &#x200B;](https://localhost:4502/content/community-components/en/reviews.html) de vereiste vermelde clientlibs zijn

* cq.ckeditor
* cq.social.hbs.reviews

![&#x200B; clientlibs-overzichten &#x200B;](assets/clientlibs-reviews.png)

## Vereiste clips toevoegen {#adding-required-clientlibs}

Wanneer u een Gemeenschapscomponent aan een pagina wilt toevoegen, moet u de vereiste clientlibs voor de component toevoegen als deze nog niet aanwezig is.

Gebruik [&#x200B; CRXDE|Lite &#x200B;](#using-crxde-lite) om een bestaande clientlibslist voor een communautaire plaatspagina te wijzigen.

Om een clientlib voor een communautaire plaats toe te voegen door [&#x200B; CRXDE Lite &#x200B;](/help/sites-developing/developing-with-crxde-lite.md) te gebruiken:

* Blader naar [&#x200B; https://&lt;server>:&lt;port>/crx/de &#x200B;](https://localhost:4502/crx/de).
* Zoek het knooppunt `clientlibslist` voor de pagina waaraan u de component wilt toevoegen:

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Selecteer knooppunt `clientlibslist` :

   * Zoek de eigenschap String [] `scg:requiredClientLibs` .
   * Selecteer de `Value` ervan zodat u toegang kunt krijgen tot het dialoogvenster String-array.

      * Schuif indien nodig omlaag.
      * Selecteer + om een nieuwe clientbibliotheek in te voeren.

         * Herhaal deze bewerking om meer clientbibliotheken toe te voegen.

         * Selecteer **O.K.**.

   * Selecteer **sparen allen**.

>[!NOTE]
>
>Als de site geen gemeenschapssite is, moet het bestaan of de locatie van de clientbibliotheken die voor de site worden gebruikt, worden gedetecteerd.

Gebruikend [&#x200B; Begonnen het Worden met AEM Communities &#x200B;](/help/communities/getting-started.md) voorbeeld, waar `site-name` ** is in dienst neemt, is dit hoe de clientliblist zou verschijnen als het toevoegen van de revisiecomponent:

![&#x200B; overzicht-component &#x200B;](assets/review-component.png)
