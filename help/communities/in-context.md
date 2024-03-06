---
title: In context Moderatie
description: Leer hoe beheerders en vertrouwde leden van de gemeenschap moderatoracties in de Gemeenschappen van Adobe Experience Manager kunnen uitvoeren.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 47b3c19c-5228-4b72-b78c-7ed71b308921
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# In context Moderatie {#in-context-moderation}

Voor AEM Communities kan de moderatie rechtstreeks door beheerders en leden van een vertrouwde gemeenschap worden uitgevoerd op de gepubliceerde pagina waar de community-inhoud is geplaatst.

Wanneer u een [moderatieconsole](moderation.md)De informatie die voor de inhoud wordt weergegeven, bevat een koppeling naar de gepubliceerde pagina om toegang te verlenen tot extra moderniseringsacties die beschikbaar zijn wanneer de inhoud in de context wordt gematigd.

## Moderatiehandelingen {#moderation-actions}

Bezoek het moderatieoverzicht voor een beschrijving van [matigingsmaatregelen](moderate-ugc.md#moderation-actions).

## Moderniseringsinterface {#moderation-ui}

UI die aan de moderator op wordt voorgesteld publiceert instantie is bevat binnen de dialoog voor het posten van en het beheren van user-generated inhoud (UGC). De elementen van de gebruikersinterface worden bepaald door de status van de bezoeker van de site - of ze nu ...

1. Het lid dat de inhoud heeft gepost.
1. Een vertrouwde lidmoderator.
1. Een beheerder.
1. Aangemeld, maar geen beheerder, moderator of auteur van de inhoud.
1. Niet aangemeld.

## Voorbeeld {#example}

Met de [Geometrixx inschakelen](http://localhost:4503/content/sites/engage/en.html) site gemaakt bij [Aan de slag met AEM Communities](getting-started.md), is het mogelijk een thread op te zetten in een forum waarop diverse moderniseringsactiviteiten in de publicatieomgeving kunnen worden uitgevoerd. Zie hieronder.

Aaron McDonald (`aaron.mcdonald@mailinator.com`) werd geïdentificeerd als een vertrouwd lid van de gemeenschap door hem toe te voegen aan de groep van moderatoren in de gemeenschap bij het maken van de site.

Rebekah Larsen (`rebekah.larsen@trashymail.com`) kan worden toegevoegd als lid van een gemeenschap-gespreksgroep die [Ledenconsole](members.md).

Ga voor meer informatie over gebruikersgroepen uit de gebruikersgemeenschap naar [Gebruikers en gebruikersgroepen beheren](users.md).

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

Een anonieme bezoeker van de site kan alleen het forum bekijken, maar mag geen inhoud plaatsen en geen moderatiehandelingen uitvoeren.

![bezoeker van het communityforum](assets/community-forum-visitor.png)

### Nieuw lid (#4) {#new-member}

Meld u bij de auteur aan als beheerder en voeg Boyd Larsen (boyd.larsen@dodgit.com) toe als een nieuw lid van de groep met deelnemers aan de gebruikersgemeenschap met behulp van de [Ledenconsole](members.md)en logout.

Bij publiceren, login als Boyd Larsen en toegang tot de draad door te selecteren `Forum`en vervolgens `Read more` voor de bulgvogelpost.

Opmerking:

* Boyd heeft niet deelgenomen aan het forum.
* Boyd kan niets verwijderen.
* Boyd is aangemeld en kan inhoud beantwoorden of markeren.

Laat Boyd Vlag selecteren om de inhoud te markeren die door Andrew is geplaatst.

Afmelden

![lid van het communautair forum](assets/community-forum-member.png)

### Beheerder (#3) {#administrator}

Login als Beheerder (admin) en toegang tot de draad door Forum te selecteren, en dan meer voor een post te lezen.

Opmerking:

* Beheerders kunnen vlaggen, Verwijderen, Bewerken, Weigeren, Knippen, Sluiten, Vastzetten, Functie.
* Admin kan Beleid selecteren om tot de moderatieconsole toegang te hebben.

![community-admin-forum](assets/community-admin-forum.png)

Selecteer het menupunt van het Beleid zodat kunt u tot [moderatieconsole](moderation.md) uit de publicatieomgeving.

Bericht dat, voor een beheerder, alle moderatable inhoud zichtbaar is, niet alleen inhoud van de de communautaire plaats van de Modus van de Geometrixx.

Het zoekfilter is een zijpaneel dat tussen open en gesloten schakelt.

Afmelden.

![moderatie-console-publish](assets/moderation-console-publish.png)

### Moderator van de Gemeenschap (#2) {#community-moderator}

Log in als Aaron McDonald (`aaron.mcdonal@mailinator.com`), een moderator van de gemeenschap, en toegang tot de draad door Forum te selecteren, en dan gelezen meer voor de kolibrieppost.

Opmerking:

* Aaron kan zijn eigen post beantwoorden, verwijderen, bewerken of ontkennen.
* Aaron kan ook andere inhoud markeren/toestaan, beantwoorden, verwijderen, bewerken of weigeren.
* Aaron kan het forumonderwerp knippen om het naar een ander forum te verplaatsen waarvoor hij gematigd is.
* Aaron kan Beleid selecteren om tot de moderatieconsole toegang te hebben.

![gemeenschapsforum-moderator](assets/community-forum-moderator.png)

Selecteer het menupunt van het Beleid zodat kunt u tot [moderatieconsole](moderation.md) uit de publicatieomgeving.

Bericht dat, voor een communautaire moderator, slechts moderatable inhoud van de de communautaire plaats van de Modus van de Geometrixx is zichtbaar.

Merk op dat de communautaire moderator de zelfde opties zoals de beheerder heeft (het beeld is met onderzoek sidebar geknepen gesloten), maar geen toegang tot andere AEM consoles.

Afmelden.

![moderatortoegang](assets/moderator-access.png)

### Inhoudsauteur (#1) {#content-author}

Aanmelden als Rebekah Larsen (`rebekah.larsen@mailinator.com`), een lid van de gemeenschap die de draad begon, en toegang tot de draad door Forum te selecteren, en dan gelezen meer voor de het kolieren post.

Opmerking:

* Rebekah kan haar eigen artikel verwijderen of bewerken.
* Rebekah kan ook reageren op andere inhoud of andere inhoud markeren.
* Rebekah heeft geen toegang tot de moderatieconsole.

![communityforum-auteur](assets/community-forum-author.png)
