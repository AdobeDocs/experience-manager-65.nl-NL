---
title: Leaderboard-functie
seo-title: Leaderboard Feature
description: Een Leaderboard-component aan een pagina toevoegen
seo-description: Adding a Leaderboard component to a page
uuid: c4633919-75d3-4bc7-830c-ef9c28cc1cba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 9045ce2e-a06d-4da5-9b83-56dd823007bb
docset: aem65
exl-id: 8b4d56d9-ba73-4eda-9773-3daaa9237abe
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Leaderboard-functie {#leaderboard-feature}

## Inleiding {#introduction}

De `Leaderboard` de component biedt de mogelijkheid om een idee te krijgen van de manier waarop leden binnen de gemeenschap met elkaar communiceren door leden te rangschikken op basis van verdiende punten (basisscore) of hun deskundigheid (geavanceerde scoring).

Voordat u de leaderboard-component op een pagina plaatst, moet u [Scores en badges van gemeenschappen](/help/communities/implementing-scoring.md).

In dit gedeelte van de documentatie wordt het volgende beschreven:

* Het toevoegen van `Leaderboard` component aan een [community-site](/help/communities/overview.md#community-sites).
* De montages van de configuratie voor de `Leaderboard` component.

### Een Leaderboard toevoegen aan een pagina {#adding-a-leaderboard-to-a-page}

Als u een `Leaderboard` naar een pagina in de modus Schrijver, zoek de component

* `Communities / Leaderboard`

en sleep het naar de juiste plaats op een pagina.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![leaderboard](assets/leaderboard.png)

### Leaderboard configureren {#configuring-leaderboard}

Selecteer de geplaatste `Leaderboard` te openen en de component te selecteren `Configure` wordt het dialoogvenster Bewerken geopend.

![configure-new](assets/configure-new.png)

![configuratieleider](assets/configure-leaderboard.png)

#### Het tabblad Instellingen {#settings-tab}

Onder de **[!UICONTROL Settings]** tabblad, geeft u op welke informatie met betrekking tot het lid wordt weergegeven:

* **Weergavenaam**

   Een beschrijvende naam die voor het bord moet worden weergegeven en die de regels weergeeft die zijn geselecteerd voor het weergeven van badges en scores.
Standaard is `Leaderboard`, als er niets is ingevoerd.

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

Onder de **Regels** tab, de site van de community en de bijbehorende regels voor scoring en badging

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

   * Locatie van regel = `/content/sites/<site name>/jcr:content`
   * Scoreregel = `/libs/settings/community/scoring/rules/forums-scoring`
   * Badgingregel = `/libs/settings/community/badging/rules//reference-badging`
   * Weergavelimiet = `10`

![deelnemerslijst](assets/participants-leaderboard.png)

### Voorbeeld: Expert Leaderboard {#example-experts-leaderboard}

Dit leaderboard-rapport is het resultaat van het toepassen van geavanceerde scoreregels.

Configuratie van de component Leaderboard:

* Tabblad Instellingen:

   * Weergavenaam = `Expertise Board`
   * `checked`:

      * Badge
      * Avatar gebruiken

* Regels, tabblad:

   * Locatie van regel = `/content/sites/<site name>/jcr:content`
   * Scoreregel = `/libs/settings/community/scoring/rules/adv-forums-scoring`
   * Badgingregel = `/libs/settings/community/badging/rules/adv-forums-badging`
   * Weergavelimiet = `10`

![deskundigenpanel](assets/experts-leaderboard.png)

### Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële elementen op Leaderboard](/help/communities/leaderboard.md) pagina voor ontwikkelaars.

De instructies voor het creëren van regels worden verstrekt op [Scores en badges van gemeenschappen](/help/communities/implementing-scoring.md) pagina voor beheerders.
