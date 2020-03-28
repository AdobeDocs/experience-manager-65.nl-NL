---
title: Leaderboard-functie
seo-title: Leaderboard-functie
description: Een Leaderboard-component aan een pagina toevoegen
seo-description: Een Leaderboard-component aan een pagina toevoegen
uuid: c4633919-75d3-4bc7-830c-ef9c28cc1cba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 9045ce2e-a06d-4da5-9b83-56dd823007bb
docset: aem65
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Leaderboard-functie {#leaderboard-feature}

## Inleiding {#introduction}

De `Leaderboard` component biedt de mogelijkheid om inzicht te krijgen in de manier waarop leden binnen de gemeenschap met elkaar communiceren door leden te rangschikken op basis van verdiende punten (basisscore) of hun expertise (geavanceerde scoring).

Voordat de leaderboard-component op een pagina wordt geplaatst, moet u [Communities Scoring and Badges](/help/communities/implementing-scoring.md)configureren.

In deze sectie van de documentatie wordt beschreven

* De `Leaderboard` component toevoegen aan een [communitysite](/help/communities/overview.md#community-sites)
* Configuratie-instellingen voor de `Leaderboard` component

### Een Leaderboard toevoegen aan een pagina {#adding-a-leaderboard-to-a-page}

Als u een `Leaderboard` component aan een pagina wilt toevoegen in de ontwerpmodus, zoekt u de component

* `Communities / Leaderboard`

en sleep het naar de juiste plaats op een pagina.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er als volgt uit:

![chlimage_1-19](assets/chlimage_1-19.png)

### Leaderboard configureren {#configuring-leaderboard}

Selecteer de geplaatste `Leaderboard` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-20](assets/chlimage_1-20.png) ![chlimage_1-21](assets/chlimage_1-21.png)

#### Het tabblad Instellingen {#settings-tab}

Geef onder het tabblad **Instellingen** op welke informatie over het lid wordt weergegeven:

* **Weergavenaam**

   Een beschrijvende naam die voor het bord moet worden weergegeven en die de regels weergeeft die zijn geselecteerd voor het weergeven van badges en scores.
De standaardwaarde is `Leaderboard`, als er niets is ingevoerd.

* **Badge**

   Als deze optie is ingeschakeld, wordt een kolom voor badge-pictogrammen opgenomen in het leaderboard.
De optie Standaard is uitgeschakeld.

* **Naam badge**

   Als deze optie is ingeschakeld, wordt een kolom met de naam van de badge opgenomen in het leaderboard.
De optie Standaard is uitgeschakeld.

* **Avatar gebruiken**

   Als deze optie is ingeschakeld, wordt de avatarafbeelding van het lid opgenomen in het leaderboard, naast de naamkoppeling naar het profiel van het lid.
De optie Standaard is uitgeschakeld.

#### Regels, tabblad {#rules-tab}

Op het tabblad **Regels** vindt u de site van de gebruikersgemeenschap en de bijbehorende regels voor scoring en badging

* **Locatie van regel**

   (Vereist) Plaats waar de het Scoren/het Bedragen regel wordt gevormd.

* **Scoreregel**

   (Vereist) Specifieke regel die de scores genereert die moeten worden weergegeven.

* **Badgingregel**

   (Vereist) Specifieke regel die de badge produceert om te tonen.

* **Weergavelimiet**

   Aantal leden dat per pagina moet worden weergegeven. De standaardwaarde is 10.

### Voorbeeld: Lederboard van deelnemers {#example-participants-leaderboard}

Deze lederbordrapporten zijn het resultaat van het toepassen van elementaire scoringregels.

Configuratie van de component Leaderboard:

* Tabblad Instellingen:

   * Weergavenaam = `Participation Board`
   * `checked`:

      * Badge
      * Naam badge
      * Avatar gebruiken

* Regels, tabblad:

   * Locatie van regel = `/content/sites/communities/jcr:content`
   * Scoreregel = `/etc/community/scoring/rules/forums-scoring`
   * Badgingregel = `/etc/community/badging/rules/reference-badging`
   * Weergavelimiet = `10`

![chlimage_1-22](assets/chlimage_1-22.png)

### Voorbeeld: Expert Leaderboard {#example-experts-leaderboard}

Dit leaderboard-rapport is het resultaat van het toepassen van geavanceerde scoreregels.

Configuratie van de component Leaderboard:

* Tabblad Instellingen:

   * Weergavenaam = `Expertise Board`
   * `checked`:

      * Badge
      * Avatar gebruiken

* Regels, tabblad:

   * Locatie van regel = `/content/sites/communities/jcr:content`
   * Scoreregel = `/etc/community/scoring/rules/adv-forums-scoring`
   * Badgingregel = `/etc/community/badging/rules/adv-forums-badging`
   * Weergavelimiet = `10`

![chlimage_1-23](assets/chlimage_1-23.png)

### Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Leaderboard Essentials](/help/communities/leaderboard.md) voor ontwikkelaars.

Instructies voor het maken van regels worden gegeven op de pagina [Community Scoring and Badges](/help/communities/implementing-scoring.md) voor beheerders.
