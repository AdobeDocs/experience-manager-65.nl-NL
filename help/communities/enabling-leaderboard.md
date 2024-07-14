---
title: Leaderboard-functie
description: Leer hoe u met de component Leaderboard kunt zien hoe leden binnen de gemeenschap communiceren door leden te rangschikken op basis van verdiende punten en expertise.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 8b4d56d9-ba73-4eda-9773-3daaa9237abe
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Leaderboard-functie {#leaderboard-feature}

## Inleiding {#introduction}

Met de component `Leaderboard` krijgt u inzicht in de manier waarop leden binnen de gemeenschap communiceren door leden te rangschikken op basis van verdiende punten (standaardscoring) of hun expertise (geavanceerde scoring).

Alvorens de leaderboard component op een pagina op te nemen, is het noodzakelijk om [ het Scoren Badges van Gemeenschappen te vormen ](/help/communities/implementing-scoring.md).

In dit gedeelte van de documentatie wordt het volgende beschreven:

* Toevoegend de `Leaderboard` component aan a [ communautaire plaats ](/help/communities/overview.md#community-sites).
* Configuration settings for the `Leaderboard` component.

### Een Leaderboard toevoegen aan een pagina {#adding-a-leaderboard-to-a-page}

Als u een component `Leaderboard` in de ontwerpmodus aan een pagina wilt toevoegen, zoekt u de component

* `Communities / Leaderboard`

En sleep het naar de juiste plaats op een pagina.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen ](/help/communities/basics.md).[

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![ leaderboard ](assets/leaderboard.png)

### Leaderboard configureren {#configuring-leaderboard}

Selecteer de geplaatste component `Leaderboard` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vorm-nieuw ](assets/configure-new.png)

![ vorm-leaderboard ](assets/configure-leaderboard.png)

#### Het tabblad Instellingen {#settings-tab}

Geef onder het tabblad **[!UICONTROL Settings]** op welke informatie met betrekking tot het lid wordt weergegeven:

* **Naam van de Vertoning**

  Een beschrijvende naam die voor het bord moet worden weergegeven en die de regels weergeeft die zijn geselecteerd voor het weergeven van badges en scores.
De standaardwaarde is `Leaderboard` als er niets is ingevoerd.

* **Badge**

  Als deze optie is ingeschakeld, wordt een kolom voor badge-pictogrammen opgenomen in het leaderboard.
De optie Standaard is uitgeschakeld.

* **Naam van de Badge**

  Als deze optie is ingeschakeld, wordt een kolom met de naam van de badge opgenomen in het leaderboard.
De optie Standaard is uitgeschakeld.

* **Gebruik Avatar**

  Als deze optie is ingeschakeld, wordt de avatarafbeelding van het lid opgenomen in het leaderboard, naast de naamkoppeling naar het profiel van het lid.
De optie Standaard is uitgeschakeld.

#### Regels, tabblad {#rules-tab}

Onder het **lusje van Regels**, de communautaire plaats, en zijn het scoren en het badging regels

* **Plaats van de Regel**

  (Vereist) Plaats waar de het Scoren/het Bedragen regel wordt gevormd.

* **het Scoren Regel**

  (Vereist) Specifieke regel die de scores genereert die moeten worden weergegeven.

* **het Badging Regel**

  (Vereist) Specifieke regel die de badge produceert om te tonen.

* **Limiet van de Vertoning**

  Aantal te tonen leden per pagina. De standaardwaarde is 10.

### Voorbeeld: Leaderboard van deelnemers {#example-participants-leaderboard}

Deze lederbordrapporten zijn het resultaat van het toepassen van elementaire scoringregels.

Configuratie van de component Leaderboard:

* Tabblad Instellingen:

   * Weergavenaam = `Participation Board`
   * `checked` :

      * Badge
      * Naam badge
      * Avatar gebruiken

* Regels, tabblad:

   * Locatie van regel = `/content/sites/<site name>/jcr:content`
   * Scoreregel = `/libs/settings/community/scoring/rules/forums-scoring`
   * Badging Rule = `/libs/settings/community/badging/rules//reference-badging`
   * Weergavelimiet = `10`

![ deelnemers-leider ](assets/participants-leaderboard.png)

### Voorbeeld: Leaderboard van experts {#example-experts-leaderboard}

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
   * Badging Rule = `/libs/settings/community/badging/rules/adv-forums-badging`
   * Weergavelimiet = `10`

![ expert-leaderboard ](assets/experts-leaderboard.png)

### Aanvullende informatie {#additional-information}

De meer informatie kan op de ](/help/communities/leaderboard.md) pagina van de Hoofdzaak van 0} worden gevonden Leaderboard {voor ontwikkelaars.[

De instructies voor het creëren van regels worden verstrekt op de [ Scoring van Gemeenschappen en de pagina van Badges ](/help/communities/implementing-scoring.md) voor beheerders.
