---
title: Scores en Badges Essentials
description: Leer hoe leden van de gemeenschap worden geïdentificeerd en beloond door de functie voor scoren en badges van Adobe Experience Manager.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 470a382a-2aa7-449e-bf48-b5a804c5b114
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# Scores en Badges Essentials {#scoring-and-badges-essentials}

De AEM Communities-functie voor scoren en badges identificeert en beloont leden van de gemeenschap.

De details van het instellen van de functie worden beschreven op

* [Scores en badges van gemeenschappen](/help/communities/implementing-scoring.md)

Deze pagina bevat aanvullende technische gegevens:

* Procedure [een badge weergeven](#displaying-badges) als afbeelding of tekst
* Uitgebreid inschakelen [foutopsporing](#debug-log-for-scoring-and-badging)
* Procedure [toegang tot UGC](#ugc-for-scoring-and-badging) met betrekking tot scoring en badging

>[!CAUTION]
>
>De in CRXDE Lite zichtbare implementatiestructuur kan worden gewijzigd.

## Badges weergeven {#displaying-badges}

Of een badge als tekst of beeld wordt getoond wordt gecontroleerd op de cliëntkant in het malplaatje van GB.

Zoek bijvoorbeeld naar `this.isAssigned` in `/libs/social/forum/components/hbs/topic/list-item.hbs`:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

Indien waar (true) `isAssigned` Hiermee wordt aangegeven dat de badge is toegewezen aan een rol en dat de badge moet worden weergegeven als tekst.

Indien onwaar `isAssigned` Hiermee wordt aangegeven dat de badge is toegekend voor een behaalde score en dat de badge moet worden weergegeven als een afbeelding.

Wijzigingen in dit gedrag moeten worden aangebracht in een aangepast script (overschrijven of bedekken). Zie [Aanpassing aan clientzijde](/help/communities/client-customize.md).

## Foutopsporingslogboek voor score en Badging {#debug-log-for-scoring-and-badging}

Voor foutopsporing in scores en badging kunt u een aangepast logbestand instellen. De inhoud van dit logbestand kan dan aan de klantenondersteuning worden verstrekt als er problemen met de functie worden ondervonden.

Ga voor gedetailleerde instructies naar [Een aangepast logbestand maken](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

U kunt als volgt snel een logbestand instellen:

1. Toegang krijgen tot de **Adobe Experience Manager Web Console Log Support** bijvoorbeeld

   * https://localhost:4502/system/console/slinglog

1. Selecteren **Nieuwe logboekregistratie toevoegen**

   1. Selecteren `DEBUG` for **Logboekniveau**

   1. Voer een naam in voor **Logbestand** bijvoorbeeld

      * logs/scoring-debug.log

   1. Twee invoeren **Aanmelder** (klasse) items (gebruiken `+` pictogram)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`

   1. Selecteren **Opslaan**

![debug-scoring-log](assets/debug-scoring-log.png)

Logboekvermeldingen weergeven:

* Vanuit de webconsole

   * Onder de **Status** menu
   * Selecteren **Logbestanden**
   * Zoek naar uw naam van het Logdossier, zoals `scoring-debug`

* Op de lokale schijf van de server

   * Het logbestand bevindt zich op &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log

   * Bijvoorbeeld: `.../crx-quickstart/logs/scoring-debug.log`

![scoring-log](assets/scoring-log.png)

## UGC voor scores en Badging {#ugc-for-scoring-and-badging}

Het is mogelijk om UGC met betrekking tot het scoring en het aanbrengen van merktekens te bekijken wanneer gekozen SRP of JSRP of MSRP, maar niet ASRP is. (Als u deze termen niet kent, raadpleegt u [Opslag van communautaire inhoud](/help/communities/working-with-srp.md) en [Overzicht opslagbronprovider](/help/communities/srp.md).)

De beschrijvingen voor de toegang tot van het scoring en het merkingsgegeven gebruiken JSRP, aangezien UGC gemakkelijk toegankelijk is gebruikend [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

**JSRP bij auteur**: experimenteren in de auteursomgeving resulteert in UGC die alleen zichtbaar is vanuit de auteursomgeving.

**JSRP bij publicatie**: Als u tests uitvoert op de publicatieomgeving, is het ook nodig om toegang te krijgen tot CRXDE Lite met beheerdersrechten voor een publicatie-instantie. Als de publicatie-instantie wordt uitgevoerd in [productiemodus](/help/sites-administering/production-ready.md) (geen samplcontent run mode), is het nodig dat [CRXDE Lite inschakelen](/help/sites-administering/enabling-crxde-lite.md).

De basislocatie van UGC op JSRP is `/content/usergenerated/asi/jcr/`.

### API&#39;s voor scores en Badging {#scoring-and-badging-apis}

De volgende API&#39;s zijn beschikbaar voor gebruik:

* [com.adobe.cq.social.scoring.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html)
* [com.adobe.cq.social.badging.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html)

De recentste JavaDocs voor het geïnstalleerde eigenschappak zijn beschikbaar aan ontwikkelaars van de bewaarplaats van de Adobe. Zie [Maven gebruiken voor Gemeenschappen : JavaDocs](/help/communities/maven.md#javadocs).

**De locatie en de indeling van de UGC in de opslagplaats kunnen zonder waarschuwing worden gewijzigd**.

### Voorbeeld instellen {#example-setup}

De screenshots van dataopslaggegevens zijn afkomstig van het instellen van scoring en badging voor een forum op twee verschillende AEM sites:

1. Een AEM *with* een unieke id (een communitysite die is gemaakt met een wizard):

   * Met behulp van de site Aan de slag met zelfstudies (engineers) die tijdens de [aan de slag - zelfstudie](/help/communities/getting-started.md)
   * Zoek het knooppunt voor forumpagina

     `/content/sites/engage/en/forum/jcr:content`

   * Eigenschappen voor scoring en badges toevoegen

   ```
   scoringRules = [/libs/settings/community/scoring/rules/comments-scoring,
   /libs/settings/community/scoring/rules/forums-scoring]
   ```

   ```
   badgingRules =[/libs/settings/community/badging/rules/comments-scoring,
   /libs/settings/community/badging/rules/forums-scoring]
   ```

   * Zoek het knooppunt voor de forumcomponent

     `/content/sites/engage/en/forum/jcr:content/content/primary/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

   * Om badges weer te geven, voegt u eigenschap toe

     `allowBadges = true`

   * Een gebruiker ondertekent in, maakt een forumonderwerp en krijgt een bronzen badge toegewezen

1. Een AEM *zonder* een unieke id:

   * Met de [Community Components Guide](/help/communities/components-guide.md)
   * Zoek het knooppunt voor forumpagina

     `/content/community-components/en/forum/jcr:content`

   * Eigenschappen voor scoring en badges toevoegen

   ```
   scoringRules = [/libs/settings/community/scoring/rules/comments-scoring,
   /libs/settings/community/scoring/rules/forums-scoring]
   ```

   ```
   badgingRules =[/libs/settings/community/badging/rules/comments-badging,
   /libs/settings/community/badging/rules/forums-badging]
   ```

   * Zoek het knooppunt voor de forumcomponent

     `/content/community-components/en/forum/jcr:content/content/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

   * Om badges weer te geven, voegt u eigenschap toe

     `allowBadges = true`

   * Een gebruiker ondertekent in, maakt een forumonderwerp en krijgt een bronzen badge toegewezen

1. Aan een gebruiker wordt een moderatorbadge toegewezen via cURL:

   ```shell
   curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" https://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
   ```

   Aangezien een gebruiker twee bronzen badges heeft verdiend en een moderatorbadge heeft gekregen, verschijnt de gebruiker met zijn forumingang als volgt:

   ![moderator](assets/moderator.png)

>[!NOTE]
>
>In dit voorbeeld worden de volgende aanbevolen procedures niet gevolgd:
>
>* Namen van scores voor regels moeten globaal uniek zijn; ze mogen niet eindigen met dezelfde naam.
>
>  Een voorbeeld van wat *niet* om te doen:
>
>  /libs/settings/community/scoring/rules/site1/forums-scoring
>  /libs/settings/community/scoring/rules/site2/forums-scoring
>
>* Unieke badge-afbeeldingen maken voor verschillende AEM sites

### Toegang tot UGC-score {#access-scoring-ugc}

Gebruik van de [API&#39;s](#scoring-and-badging-apis) heeft de voorkeur.

Voor onderzoeksdoeleinden, gebruikend JSRP bijvoorbeeld, is de basisomslag die scores bevat

* `/content/usergenerated/asi/jcr/scoring`

De onderliggende node van `scoring` is de naam van de scoreregel. Daarom is het aan te raden om regelnamen op een server globaal uniek te scoren.

Voor de plaats van de Ingenieur van de Geometrixx, zijn de gebruiker, en hun score, in een weg die met de het scoren regelnaam, plaatsidentiteitskaart van de gemeenschap wordt geconstrueerd ( `engage-ba81p`), een unieke id en de id van de gebruiker:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Voor de Community Components-hulplijnsite bevinden de gebruiker en hun score zich in een pad dat is samengesteld met de naam van de scoreregel, een standaard-id ( `default-site`), een unieke id en de id van de gebruiker:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

De score wordt opgeslagen in de eigenschap `scoreValue_tl` die alleen een waarde mogen bevatten of indirect naar een atomicCounter mogen verwijzen.

![access-scoring-ugc](assets/access-scoring-ugc.png)

### Access Badging UGC {#access-badging-ugc}

Gebruik van de [API&#39;s](#scoring-and-badging-apis) heeft de voorkeur.

Voor onderzoeksdoeleinden, gebruikend JSRP bijvoorbeeld, is de basisomslag die informatie over toegewezen of toegekende badges bevat

* `/content/usergenerated/asi/jcr`

Wordt gevolgd door het pad naar het gebruikersprofiel en eindigt in een map met badges, zoals:

* `/home/users/community/w271OOup2Z4DjnOQrviv/profile/badges`

#### Toegewezen badge {#awarded-badge}

![bekroonde badging-ugc](assets/access-badging-ugc.png)

#### Toegewezen badge {#assigned-badge}

![toegewezen badge](assets/assigned-badge.png)

## Aanvullende informatie {#additional-information}

Een gesorteerde lijst met leden weergeven op basis van punten:

* [Leaderboard, functie](/help/communities/functions.md#leaderboard-function) voor opname in een community- of groepssjabloon.
* [Leaderboard-component](/help/communities/enabling-leaderboard.md), de aanbevolen component van de Leaderboard-functie, voor het ontwerpen van pagina&#39;s.
