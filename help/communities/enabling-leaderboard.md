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
source-git-commit: 6720d5a0fdf1facc0b10011ec306dffbb31f4ac5
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---


# Leaderboard-functie {#leaderboard-feature}

## Inleiding {#introduction}

De `Leaderboard` component verstrekt de capaciteit om een idee van te verkrijgen hoe de leden binnen de gemeenschap interactie door leden volgens verdiende punten (basis het scoren) of hun deskundigheid (geavanceerde het scoren) te rangschikken.

Voordat de leaderboard-component op een pagina wordt opgenomen, moet u [Communityscores en Badges](/help/communities/implementing-scoring.md) configureren.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De `Leaderboard`-component toevoegen aan een [communitysite](/help/communities/overview.md#community-sites).
* De montages van de configuratie voor `Leaderboard` component.

### Leaderboard toevoegen aan een pagina {#adding-a-leaderboard-to-a-page}

Als u een `Leaderboard`-component wilt toevoegen aan een pagina in de ontwerpmodus, zoekt u de component

* `Communities / Leaderboard`

en sleep het naar de juiste plaats op een pagina.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](/help/communities/basics.md).

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![chlimage_1-8](assets/chlimage_1-8.png)

### Leaderboard {#configuring-leaderboard} configureren

Selecteer de geplaatste `Leaderboard` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![chlimage_1-9](assets/chlimage_1-9.png)

![chlimage_1-10](assets/chlimage_1-10.png)

#### Tabblad Instellingen {#settings-tab}

Geef onder het tabblad **[!UICONTROL Settings]** op welke informatie met betrekking tot het lid wordt weergegeven:

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

Onder het **Regels** lusje, de communautaire plaats, en zijn het schrapen en het badgen regels

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
   * Badging Rule = `/libs/settings/community/badging/rules//reference-badging`
   * Weergavelimiet = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

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

![chlimage_1-12](assets/chlimage_1-12.png)

### Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Leaderboard Essentials](/help/communities/leaderboard.md) voor ontwikkelaars.

Instructies voor het maken van regels vindt u op de pagina [Community Scoring and Badges](/help/communities/implementing-scoring.md) voor beheerders.
