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

De [Community Components Guide](/help/communities/components-guide.md) identificeert de vereiste clientbibliotheken. Blader naar de Component Guide en bekijk de component Comments, bijvoorbeeld:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Let op de drie clientbibliotheken die nodig zijn voor het renderen en correct functioneren van Opmerkingen. Deze moeten worden opgenomen wanneer naar de uitgebreide opmerkingen wordt verwezen, en de [uitgebreide clientbibliotheek met opmerkingen](/help/communities/extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![comments-component1](assets/comments-component1.png)

### Aangepaste opmerkingen toevoegen aan een pagina {#add-custom-comments-to-a-page}

Aangezien er slechts één opmerkingsysteem per pagina kan zijn, is het eenvoudiger om een voorbeeldpagina te maken zoals in de samenvatting wordt beschreven [een voorbeeldpagina maken](/help/communities/create-sample-page.md) zelfstudie.

Als u een aangepaste component hebt gemaakt, typt u de ontwerpmodus en stelt u de componentgroep Custom beschikbaar om de optie `Alt Comments` aan de pagina toe te voegen.

De opmerking wordt alleen weergegeven en werkt naar behoren als de clientbibliotheken voor opmerkingen worden toegevoegd aan de clientlibslist voor de pagina (zie [Clientlibs voor Community-componenten](/help/communities/clientlibs.md)).

#### Opmerkingen Clientlibs op voorbeeldpagina {#comments-clientlibs-on-sample-page}

![comments-clientlibs-crxde](assets/comments-clientlibs-crxde.png)

#### Auteur: Alt-opmerking op voorbeeldpagina {#author-alt-comment-on-sample-page}

![alt-comment](assets/alt-comment.png)

#### Auteur: knooppunt Voorbeeld van opmerkingen op pagina {#author-sample-page-comments-node}

U kunt het resourceType in CRXDE verifiëren door de eigenschappen van de commentaarknoop voor de steekproefpagina te bekijken bij `/content/sites/sample/en/jcr:content/content/primary/comments`.

![verify-comment-crxde](assets/verify-comment-crxde.png)

#### Voorbeeldpagina publiceren {#publish-sample-page}

Nadat de aangepaste component aan de pagina is toegevoegd, is het ook nodig (re) [de pagina publiceren](/help/communities/sites-console.md#publishing-the-site).

#### Publiceren: Alt-opmerking op voorbeeldpagina {#publish-alt-comment-on-sample-page}

Nadat u zowel de aangepaste toepassing als de voorbeeldpagina hebt gepubliceerd, kunt u een opmerking invoeren. Bij aanmelding met een van de [demo-gebruiker](/help/communities/tutorials.md#demo-users) Voor beheerders is het mogelijk om een opmerking te plaatsen.

Hier aaron.mcdonald@mailinator.com vindt u een opmerking:

![publish-alt-comment](assets/publish-alt-comment.png)

![publish-alt-comment1](assets/publish-alt-comment1.png)

Nu het lijkt of de uitgebreide component correct werkt met de standaardweergave, is het tijd om de weergave te wijzigen.
