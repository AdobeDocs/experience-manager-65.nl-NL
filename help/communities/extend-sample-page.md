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
source-git-commit: d38395b8f845686492a26329bb732a41f79c85c4
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# Opmerking toevoegen aan voorbeeldpagina {#add-comment-to-sample-page}

Nu de componenten voor het aangepaste opmerkingensysteem in de toepassingsmap (/apps) staan, is het mogelijk om de uitgebreide component te gebruiken. De instantie van het opmerkingssysteem in een website die moet worden beïnvloed moet zijn resourceType plaatsen om het systeem van douanecommentaar te zijn en alle noodzakelijke cliëntbibliotheken te omvatten.

## Vereiste clients identificeren {#identify-required-clientlibs}

De clientbibliotheken die nodig zijn voor de stijl en werking van de standaardopmerkingen zijn ook nodig voor uitgebreide opmerkingen.

De [Community Components Guide](/help/communities/components-guide.md) identificeert de vereiste clientbibliotheken. Blader naar de Component Guide en bekijk de component Comments, bijvoorbeeld:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Let op de drie clientbibliotheken die nodig zijn voor het renderen en correct functioneren van Opmerkingen. Deze moeten worden opgenomen waar naar de uitgebreide opmerkingen wordt verwezen en in de clientbibliotheek ](/help/communities/extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`) van [extended Comments.

![comments-component1](assets/comments-component1.png)

### Aangepaste opmerkingen toevoegen aan een pagina {#add-custom-comments-to-a-page}

Aangezien er slechts één systeem van de Commentaar per pagina kan zijn, is het eenvoudiger om een steekproefpagina tot stand te brengen zoals die in het korte [Create a Sample Page](/help/communities/create-sample-page.md) leerprogramma wordt beschreven.

Nadat u een aangepaste component hebt gemaakt, voert u de ontwerpmodus in en stelt u de componentgroep Custom beschikbaar zodat de component `Alt Comments` aan de pagina kan worden toegevoegd.

De opmerking wordt alleen weergegeven en werkt naar behoren als de clientbibliotheken voor opmerkingen worden toegevoegd aan de clientlibslist voor de pagina (zie [Clientlibs for Communities Components](/help/communities/clientlibs.md)).

#### Opmerkingen Clientlibs op voorbeeldpagina {#comments-clientlibs-on-sample-page}

![comments-clientlibs-crxde](assets/comments-clientlibs-crxde.png)

#### Auteur: Alt-commentaar op voorbeeldpagina {#author-alt-comment-on-sample-page}

![alt-comment](assets/alt-comment.png)

#### Auteur: Opmerkingen op voorbeeldpagina {#author-sample-page-comments-node}

U kunt het resourceType in CRXDE verifiëren door de eigenschappen van de commentaarknoop voor de steekproefpagina bij `/content/sites/sample/en/jcr:content/content/primary/comments` te bekijken.

![verify-comment-crxde](assets/verify-comment-crxde.png)

#### Voorbeeldpagina publiceren {#publish-sample-page}

Nadat de aangepaste component aan de pagina is toegevoegd, is het ook nodig om [de pagina](/help/communities/sites-console.md#publishing-the-site) te publiceren.

#### Publiceren: Alt-commentaar op voorbeeldpagina {#publish-alt-comment-on-sample-page}

Nadat u zowel de aangepaste toepassing als de voorbeeldpagina hebt gepubliceerd, kunt u een opmerking invoeren. Als u bent aangemeld met een [demo-gebruiker](/help/communities/tutorials.md#demo-users) of beheerder, is het mogelijk om een opmerking te plaatsen.

Hier aaron.mcdonald@mailinator.com vindt u een opmerking:

![publish-alt-comment](assets/publish-alt-comment.png)

![publish-alt-comment1](assets/publish-alt-comment1.png)

Nu het lijkt of de uitgebreide component correct werkt met de standaardweergave, is het tijd om de weergave te wijzigen.