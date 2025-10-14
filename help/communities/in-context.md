---
title: In context Moderatie
description: Leer hoe beheerders en vertrouwde leden van de gemeenschap moderatoracties in de Gemeenschappen van Adobe Experience Manager kunnen uitvoeren.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 47b3c19c-5228-4b72-b78c-7ed71b308921
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# In context Moderatie {#in-context-moderation}

Voor AEM Communities kan de moderatie rechtstreeks door beheerders en leden van een vertrouwde gemeenschap worden uitgevoerd op de gepubliceerde pagina waar de community-inhoud is geplaatst.

Wanneer het gebruiken van de matigingsconsole van a [&#128279;](moderation.md), omvat de informatie die voor de inhoud wordt getoond een verbinding aan de gepubliceerde pagina om toegang tot extra beschikbare moderatieacties toe te staan wanneer het modereren in-context.

## Moderatiehandelingen {#moderation-actions}

Bezoek het moderatieoverzicht voor een beschrijving van [&#x200B; moderatieacties &#x200B;](moderate-ugc.md#moderation-actions).

## Moderniseringsinterface {#moderation-ui}

UI die aan de moderator op wordt voorgesteld publiceert instantie is bevat binnen de dialoog voor het posten van en het beheren van user-generated inhoud (UGC). De elementen van de gebruikersinterface worden bepaald door de status van de bezoeker van de site - of ze nu ...

1. Het lid dat de inhoud heeft gepost.
1. Een vertrouwde lidmoderator.
1. Een beheerder.
1. Aangemeld, maar geen beheerder, moderator of auteur van de inhoud.
1. Niet aangemeld.

## Voorbeeld {#example}

Gebruikend de [&#128279;](http://localhost:4503/content/sites/engage/en.html) gemaakte plaats van de Bouw van 0&rbrace; Geometrixx &lbrace;wanneer [&#x200B; Begonnen het worden met AEM Communities &#x200B;](getting-started.md), is het mogelijk aan opstelling een draad in een forum waarop om diverse matigingsactiviteiten in het milieu van Publish te ervaren.  Zie hieronder.

Aaron McDonald (`aaron.mcdonald@mailinator.com`) werd geïdentificeerd als vertrouwd gemeenschapslid door hem toe te voegen aan de gemeenschap-in gesprek-moderatorgroep toen het creëren van de plaats.

Rebekah Larsen (`rebekah.larsen@trashymail.com`) kan als lid van gemeenschap-in dienst neemt-leden groep worden toegevoegd gebruikend de [&#x200B; console van Leden &#x200B;](members.md).

Voor meer op communautaire gebruikersgroepen, bezoek [&#x200B; het Leiden Gebruikers en de Groepen van de Gebruiker &#x200B;](users.md).

### De forumberichten maken {#create-the-forum-posts}

* Aanmelden als Rebekah Larsen (rebekah.larsen@trashymail.com)

   * Forum selecteren
   * Nieuwe Post selecteren
   * Voer het onderwerp in

     Wanneer wijzigt u de nectar in Humming Bird Feeder

   * De hoofdtekst invoeren

     Ik heb niet veel succes gehad als ik elk jaar een kolietvoeders ophang. Ze lijken een dag of twee te komen, dan is dat het. Ik verander het eenmaal per week, is dat te lang? Moet ik het eerder veranderen?

   * Post selecteren
   * Afmelden selecteren

* Aanmelden als Aaron McDonald (aaron.mcdonald@mailinator.com)

   * Forum selecteren
   * Selecteer Meer lezen voor het onderwerp Hummingird
   * Voer de opmerking in voor Post Reply

     Ik verander de mijne eenmaal per week en ik krijg ze van mei tot oktober.

   * Reageren selecteren
   * Afmelden selecteren

* Aanmelden als Andrew Schaeffer (andrew.schaeffer@trashymail.com)

   * Forum selecteren
   * Selecteer Meer lezen voor het onderwerp Hummingird
   * Voer de opmerking in voor Post Reply

     Ik verkoop nectar en feeders - bezoek https://my.viral.url/

   * Reageren selecteren
   * Afmelden selecteren

### Anonieme sitebezoeker (#5) {#anonymous-site-visitor}

Hier volgt een weergave van het forum dat wordt weergegeven door een bezoeker van de site die niet is aangemeld (5).

Een anonieme bezoeker van de site kan alleen het forum bekijken, maar mag geen inhoud plaatsen en geen moderatiehandelingen uitvoeren.

![&#x200B; gemeenschap-forum-bezoeker &#x200B;](assets/community-forum-visitor.png)

### Nieuw lid (#4) {#new-member}

Op auteur, login als admin en voeg Boyd Larsen (boyd.larsen@dodgit.com) als nieuw lid van gemeenschap-in dienst nemend-leden groep toe gebruikend de [&#x200B; console van Leden &#x200B;](members.md), dan logout.

Meld u bij het publiceren aan als Boyd Larsen en open de thread door `Forum` te selecteren en vervolgens `Read more` voor de nummervogel.

Opmerking:

* Boyd heeft niet deelgenomen aan het forum.
* Boyd kan niets verwijderen.
* Boyd is aangemeld en kan inhoud beantwoorden of markeren.

Laat Boyd Vlag selecteren om de inhoud te markeren die door Andrew is geplaatst.

Afmelden

![&#x200B; gemeenschap-forum-lid &#x200B;](assets/community-forum-member.png)

### Beheerder (#3) {#administrator}

Login als Beheerder (admin) en toegang tot de draad door Forum te selecteren, en dan meer voor een post te lezen.

Opmerking:

* Beheerders kunnen vlaggen, Verwijderen, Bewerken, Weigeren, Knippen, Sluiten, Vastzetten, Functie.
* Admin kan Beleid selecteren om tot de moderatieconsole toegang te hebben.

![&#x200B; gemeenschap-admin-forum &#x200B;](assets/community-admin-forum.png)

Selecteer het menupunt van het Beleid zodat kunt u tot de [&#x200B; moderatieconsole &#x200B;](moderation.md) van het milieu van Publish toegang hebben.

Bericht dat, voor een beheerder, alle moderatable inhoud zichtbaar is, niet alleen inhoud van de de communautaire plaats van de Modus van de Geometrixx.

Het zoekfilter is een zijpaneel dat tussen open en gesloten schakelt.

Afmelden.

![&#x200B; moderatie-console-publiceer &#x200B;](assets/moderation-console-publish.png)

### Moderator van de Gemeenschap (#2) {#community-moderator}

Log in als Aaron McDonald (`aaron.mcdonal@mailinator.com`), een moderator van de gemeenschap, en open de draad door Forum te selecteren, en lees dan meer voor de kolibrieppost.

Opmerking:

* Aaron kan zijn eigen post beantwoorden, verwijderen, bewerken of ontkennen.
* Aaron kan ook andere inhoud markeren/toestaan, beantwoorden, verwijderen, bewerken of weigeren.
* Aaron kan het forumonderwerp knippen om het naar een ander forum te verplaatsen waarvoor hij gematigd is.
* Aaron kan Beleid selecteren om tot de moderatieconsole toegang te hebben.

![&#x200B; gemeenschap-forum-moderator &#x200B;](assets/community-forum-moderator.png)

Selecteer het menupunt van het Beleid zodat kunt u tot de [&#x200B; moderatieconsole &#x200B;](moderation.md) van het milieu van Publish toegang hebben.

Bericht dat, voor een communautaire moderator, slechts moderatable inhoud van de de communautaire plaats van de Modus van de Geometrixx is zichtbaar.

Merk op dat de communautaire moderator de zelfde opties zoals de beheerder heeft (het beeld is met onderzoek sidebar geknepen gesloten), maar geen toegang tot andere AEM consoles.

Afmelden.

![&#x200B; moderator-toegang &#x200B;](assets/moderator-access.png)

### Inhoudsauteur (#1) {#content-author}

Meld u aan als Rebekah Larsen (`rebekah.larsen@mailinator.com`), een lid van de gemeenschap dat de thread heeft gestart, en open de thread door Forum te selecteren en lees vervolgens meer voor de bulgvogelpost.

Opmerking:

* Rebekah kan haar eigen artikel verwijderen of bewerken.
* Rebekah kan ook reageren op andere inhoud of andere inhoud markeren.
* Rebekah heeft geen toegang tot de moderatieconsole.

![&#x200B; gemeenschap-forum-auteur &#x200B;](assets/community-forum-author.png)
