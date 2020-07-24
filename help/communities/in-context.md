---
title: In context Moderatie
seo-title: In context Moderatie
description: Hoe te om moderatoracties uit te voeren
seo-description: Hoe te om moderatoracties uit te voeren
uuid: 282a8bea-2822-4e5c-b9f4-4d9a5380d895
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ee104f6f-123b-4a6e-9031-849fc1318cc5
translation-type: tm+mt
source-git-commit: 917fceffb58883df83e96f60da4769046a18f3c0
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---


# In context Moderatie {#in-context-moderation}

Voor AEM Communities kan de moderatie door beheerders en vertrouwde op communautaire leden rechtstreeks op de gepubliceerde pagina worden uitgevoerd waar de communautaire inhoud werd gepost.

Wanneer het gebruiken van een [moderatieconsole](moderation.md), omvat de informatie die voor de inhoud wordt getoond een verbinding aan de gepubliceerde pagina om toegang tot extra beschikbare moderatieacties toe te staan wanneer het modereren in-context.

## Moderatiehandelingen {#moderation-actions}

Bezoek het moderatieoverzicht voor een beschrijving van [matigheidsacties](moderate-ugc.md#moderation-actions).

## Moderniseringsinterface {#moderation-ui}

UI die aan de moderator op wordt voorgesteld publiceert instantie is bevat binnen de dialoog voor het posten van en het beheren van gebruiker geproduceerde inhoud (UGC). De elementen van de gebruikersinterface worden bepaald door de status van de bezoeker van de site - of ze nu ...

1. Het lid dat de inhoud heeft gepost.
1. Een vertrouwde lidmoderator.
1. Een beheerder.
1. Aangemeld, maar geen beheerder, moderator of auteur van de inhoud.
1. Niet aangemeld.

## Voorbeeld {#example}

Met de [Geometrixx Engage](http://localhost:4503/content/sites/engage/en.html) -site die bij [Aan de slag met AEM Communities](getting-started.md)is gemaakt, is het mogelijk om snel een thread in een forum in te stellen waarop verschillende moderatieactiviteiten in de publicatieomgeving moeten worden uitgevoerd, zoals hieronder wordt weergegeven.

Aaron McDonald (aaron.mcdonald@mailinator.com) werd geïdentificeerd als een vertrouwd lid van de gemeenschap door hem toe te voegen aan de community-engact-moderators groep bij het maken van de site.

Rebekah Larsen (rebekah.larsen@trashymail.com) kan als lid van gemeenschap-in gesprek-ledengroep worden toegevoegd gebruikend de console [van](members.md)Leden.

Ga voor meer informatie over gebruikersgroepen in de gebruikersgemeenschap naar Gebruikers [beheren en Gebruikersgroepen](users.md).

### De forumberichten maken {#create-the-forum-posts}

* Aanmelden als Rebekah Larsen (rebekah.larsen@trashymail.com)

   * Forum selecteren
   * Nieuwe advertentie selecteren
   * Voer het onderwerp in

      Wanneer wijzigt u de nectar in Humming Bird Feeder

   * De hoofdtekst invoeren

      Ik heb niet veel succes gehad als ik elk jaar een kolietvoeders ophang. Ze lijken een dag of twee te komen, dan is dat het. Ik verander het eenmaal per week, is dat te lang? Moet ik het eerder veranderen?

   * Post selecteren
   * Afmelden selecteren

* Aanmelden als Aaron McDonald (aaron.mcdonald@mailinator.com)

   * Forum selecteren
   * Selecteer Meer lezen voor het onderwerp Hummingird
   * Opmerking invoeren voor reactie op bericht

      Ik verander de mijne eenmaal per week en ik krijg ze van mei tot oktober.

   * Reageren selecteren
   * Afmelden selecteren

* Aanmelden als Andrew Schaeffer (andrew.schaeffer@trashymail.com)

   * Forum selecteren
   * Selecteer Meer lezen voor het onderwerp Hummingird
   * Opmerking invoeren voor reactie op bericht

      Ik verkoop nectar en feeders - bezoek https://my.viral.url/

   * Reageren selecteren
   * Afmelden selecteren

### Anonieme sitebezoeker (#5) {#anonymous-site-visitor}

Hier volgt een weergave van het forum dat wordt weergegeven door een bezoeker van de site die niet is aangemeld (5).

Een anonieme bezoeker van de site kan alleen het forum bekijken, maar kan geen inhoud plaatsen en geen moderatieacties uitvoeren.

![bezoeker van het forum](assets/community-forum-visitor.png)

### Nieuw lid (#4) {#new-member}

Bij auteur, login als admin en voeg Boyd Larsen (boyd.larsen@dodgit.com) als nieuw lid van gemeenschap-in dienst nemend-lidgroep toe gebruikend de console [van](members.md)Leden, dan Logout.

Meld u bij het publiceren aan als Boyd Larsen en open de thread door deze te selecteren `Forum`en vervolgens `Read more` voor de nummervogel.

Opmerking:

* Boyd heeft niet deelgenomen aan het forum.
* Boyd kan niets verwijderen.
* Boyd is aangemeld en kan inhoud beantwoorden of markeren.

Laat Boyd Vlag selecteren om de inhoud te markeren die door Andrew is geplaatst.

Afmelden

![lid van het forum](assets/community-forum-member.png)

### Beheerder (#3) {#administrator}

Login als Beheerder (admin) en toegang tot de draad door Forum te selecteren, en dan meer voor een post te lezen.

Opmerking:

* Beheerders kunnen vlaggen, Verwijderen, Bewerken, Weigeren, Knippen, Sluiten, Vastzetten, Functie.
* Admin kan Beleid selecteren om tot de moderatieconsole toegang te hebben.

![community-admin-forum](assets/community-admin-forum.png)

Selecteer het menupunt van het Beleid om tot de [moderatieconsole](moderation.md) van publiceer milieu toegang te hebben.

Bericht dat, voor een beheerder, alle moderatable inhoud zichtbaar is, niet alleen inhoud van de Geometrixx de communautaire plaats van de Ingenieur van de Ingenieur.

Het zoekfilter is een sidepanel dat in- en uitschakelt.

Afmelden.

![moderatie-console-publish](assets/moderation-console-publish.png)

### Moderator van de Gemeenschap (#2) {#community-moderator}

Log in als Aaron McDonald (aaron.mcdonal@mailinator.com), een moderator van de gemeenschap, en open de thread door Forum te selecteren, en lees dan meer voor de bulgvogelpost.

Opmerking:

* Aaron kan zijn eigen post beantwoorden, verwijderen, bewerken of ontkennen.
* Aaron kan ook andere inhoud markeren/toestaan, beantwoorden, verwijderen, bewerken of weigeren.
* Aaron kan het forumonderwerp knippen om het naar een ander forum te verplaatsen waarvoor hij gematigd is.
* Aaron kan Beleid selecteren om tot de moderatieconsole toegang te hebben.

![gemeenschapsforum-moderator](assets/community-forum-moderator.png)

Selecteer het menupunt van het Beleid om tot de [moderatieconsole](moderation.md) van publiceer milieu toegang te hebben.

Bericht dat, voor een communautaire moderator, slechts moderatable inhoud van de Geometrixx de communautaire plaats van de Ingenieur zichtbaar is.

Merk op de communautaire moderator de zelfde opties heeft zoals de beheerder (het beeld is met onderzoek sidebar geknepen gesloten), maar geen toegang tot andere consoles AEM.

Afmelden.

![moderator-toegang](assets/moderator-access.png)

### Inhoudsauteur (#1) {#content-author}

Meld u aan als Rebekah Larsen (rebekah.larsen@mailinator.com), een lid van de gemeenschap dat de thread heeft gestart, en open de thread door Forum te selecteren en lees vervolgens meer voor de bulgvogelpost.

Opmerking:

* Rebekah kan haar eigen artikel verwijderen of bewerken.
* Rebekah kan ook reageren op andere inhoud of andere inhoud markeren.
* Rebekah heeft geen toegang tot de moderatieconsole.

![communityforum-auteur](assets/community-forum-author.png)

