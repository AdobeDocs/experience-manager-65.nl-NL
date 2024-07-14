---
title: Opmerking toevoegen aan voorbeeldpagina
description: Leer hoe een instantie van het opmerkingssysteem van een website zijn resourceType moet plaatsen om het systeem van douanecommentaar te zijn en alle noodzakelijke cliëntbibliotheken te omvatten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: d4295a77-b931-4bc8-b3b4-eec42fdcfc56
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Opmerking toevoegen aan voorbeeldpagina  {#add-comment-to-sample-page}

Nu de componenten voor het aangepaste opmerkingensysteem in de toepassingsmap (/apps) staan, is het mogelijk om de uitgebreide component te gebruiken. De instantie van het opmerkingssysteem in een website die moet worden beïnvloed moet zijn resourceType plaatsen om het systeem van douanecommentaar te zijn en alle noodzakelijke cliëntbibliotheken te omvatten.

## Vereiste clients identificeren {#identify-required-clientlibs}

De clientbibliotheken die nodig zijn voor de stijl en werking van de standaardopmerkingen zijn ook nodig voor uitgebreide opmerkingen.

De [ Communautaire Gids van Componenten ](/help/communities/components-guide.md) identificeert de vereiste cliëntbibliotheken. Blader naar de Component Guide en bekijk de component Comments, bijvoorbeeld:

[ https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Let op de drie clientbibliotheken die nodig zijn voor het renderen en correct functioneren van Opmerkingen. Deze moeten worden omvat waar de uitgebreide Commentaren van verwijzingen worden voorzien, en de [ uitgebreide de cliëntbibliotheek van Commentaren ](/help/communities/extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![ commentaren-component1 ](assets/comments-component1.png)

### Aangepaste opmerkingen toevoegen aan een pagina {#add-custom-comments-to-a-page}

Aangezien er slechts één systeem van de Commentaar per pagina kan zijn, is het eenvoudiger om een steekproefpagina tot stand te brengen zoals die in het korte [ wordt beschreven een voorbeeldpagina ](/help/communities/create-sample-page.md) leerprogramma creëren.

Nadat u de component `Alt Comments` hebt gemaakt, opent u de ontwerpmodus en stelt u de componentgroep Custom beschikbaar zodat de component aan de pagina kan worden toegevoegd.

Voor de Commentaar om te verschijnen en behoorlijk te functioneren, moeten de cliëntbibliotheken voor Commentaren aan cliëntlibslist voor de pagina worden toegevoegd (zie [ Clientlibs voor de Componenten van Gemeenschappen ](/help/communities/clientlibs.md)).

#### Opmerkingen Clientlibs op voorbeeldpagina {#comments-clientlibs-on-sample-page}

![ commentaren-clientlibs-crxde ](assets/comments-clientlibs-crxde.png)

#### Auteur: Alt-opmerking op voorbeeldpagina {#author-alt-comment-on-sample-page}

![ alt-comment ](assets/alt-comment.png)

#### Auteur: knooppunt Voorbeeld van opmerkingen op pagina {#author-sample-page-comments-node}

U kunt het resourceType in CRXDE verifiëren door de eigenschappen van de commentaarknoop voor de steekproefpagina bij `/content/sites/sample/en/jcr:content/content/primary/comments` te bekijken.

![ verifieer-commentaar-crxde ](assets/verify-comment-crxde.png)

#### Publish-voorbeeldpagina {#publish-sample-page}

Nadat de douanecomponent aan de pagina wordt toegevoegd, is het ook noodzakelijk om (re) [ de pagina ](/help/communities/sites-console.md#publishing-the-site) te publiceren.

#### Publish: Alt-commentaar op voorbeeldpagina {#publish-alt-comment-on-sample-page}

Nadat u zowel de aangepaste toepassing als de voorbeeldpagina hebt gepubliceerd, kunt u een opmerking invoeren. Wanneer binnen ondertekend, of met a [ demogebruiker ](/help/communities/tutorials.md#demo-users) of admin, is het mogelijk om een commentaar te posten.

Hier aaron.mcdonald@mailinator.com vindt u een opmerking:

![ publish-alt-comment ](assets/publish-alt-comment.png)

![ publish-alt-comment1 ](assets/publish-alt-comment1.png)

Nu het lijkt of de uitgebreide component correct werkt met de standaardweergave, is het tijd om de weergave te wijzigen.
