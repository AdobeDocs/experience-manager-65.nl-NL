---
title: Opmerking toevoegen aan voorbeeldpagina
seo-title: Opmerking toevoegen aan voorbeeldpagina
description: Aangepaste opmerkingen toevoegen aan een pagina
seo-description: Aangepaste opmerkingen toevoegen aan een pagina
uuid: ab258960-6de2-4943-80a7-e72904c0fd8e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a5040371-3bc2-43bc-a103-7175c4c6252d
docset: aem65
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Opmerking toevoegen aan voorbeeldpagina {#add-comment-to-sample-page}

Nu de componenten voor het aangepaste opmerkingensysteem in de toepassingsmap (/apps) staan, is het mogelijk om de uitgebreide component te gebruiken. De instantie van het opmerkingssysteem in een website die moet worden beïnvloed moet zijn resourceType plaatsen om het systeem van douanecommentaar te zijn en alle noodzakelijke cliëntbibliotheken te omvatten.

## Vereiste clients identificeren {#identify-required-clientlibs}

De clientbibliotheken die nodig zijn voor de stijl en werking van de standaardopmerkingen zijn ook nodig voor uitgebreide opmerkingen.

De [Community Components Guide](/help/communities/components-guide.md) identificeert de vereiste clientbibliotheken. Blader naar de Component Guide en bekijk de component Comments, bijvoorbeeld:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Let op de drie clientbibliotheken die nodig zijn voor het renderen en correct functioneren van Opmerkingen. Deze moeten worden opgenomen waar naar de uitgebreide opmerkingen wordt verwezen en in de [uitgebreide clientbibliotheek](/help/communities/extend-create-components.md#create-a-client-library-folder) van opmerkingen ( `apps.custom.comments`).

![chlimage_1-79](assets/chlimage_1-79.png)

### Aangepaste opmerkingen toevoegen aan een pagina {#add-custom-comments-to-a-page}

Aangezien er slechts één opmerkingsysteem per pagina kan zijn, is het eenvoudiger om een voorbeeldpagina te maken zoals beschreven in de korte zelfstudie Een voorbeeldpagina [](/help/communities/create-sample-page.md) maken.

Nadat u de component hebt gemaakt, opent u de ontwerpmodus en stelt u de componentgroep Aangepast beschikbaar, zodat de `Alt Comments` component aan de pagina kan worden toegevoegd.

De opmerking wordt alleen weergegeven en werkt naar behoren als de clientbibliotheken voor opmerkingen worden toegevoegd aan de clientlibslist voor de pagina (zie [Clientlibs voor Community Components](/help/communities/clientlibs.md)).

#### Opmerkingen Clientlibs op voorbeeldpagina {#comments-clientlibs-on-sample-page}

![Opmerkingen Clientlibs op voorbeeldpagina](assets/chlimage_1-80.png)

#### Auteur: Alt-commentaar op voorbeeldpagina {#author-alt-comment-on-sample-page}

![Alt-commentaar op voorbeeldpagina](assets/chlimage_1-81.png)

#### Auteur: Opmerkingsknooppunt voor voorbeeldpagina {#author-sample-page-comments-node}

U kunt resourceType in CRXDE verifiëren door de eigenschappen van de commentaarknoop voor de steekproefpagina bij te bekijken `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-82](assets/chlimage_1-82.png)

#### Voorbeeldpagina publiceren {#publish-sample-page}

Nadat de aangepaste component aan de pagina is toegevoegd, moet de pagina [ook (opnieuw) worden](/help/communities/sites-console.md#publishing-the-site)gepubliceerd.

#### Publiceren: Alt-commentaar op voorbeeldpagina {#publish-alt-comment-on-sample-page}

Nadat u zowel de aangepaste toepassing als de voorbeeldpagina hebt gepubliceerd, kunt u een opmerking invoeren. Als u zich hebt aangemeld, kunt u een opmerking plaatsen met een [demogebruiker](/help/communities/tutorials.md#demo-users) of beheerder.

Hier aaron.mcdonald@mailinator.com vindt u een opmerking:

![chlimage_1-83](assets/chlimage_1-83.png) ![chlimage_1-84](assets/chlimage_1-84.png)

Nu het lijkt of de uitgebreide component correct werkt met de standaardweergave, is het tijd om de weergave te wijzigen.