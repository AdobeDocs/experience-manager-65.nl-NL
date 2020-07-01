---
title: Scores en Badges Essentials
seo-title: Scores en Badges Essentials
description: Overzicht van de functie Scores en Badges
seo-description: Overzicht van de functie Scores en Badges
uuid: 6e3af071-04e8-4dc1-977a-0da711b72961
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 628b6dcd-8b1c-4166-8fc2-843baa86ac1c
docset: aem65
translation-type: tm+mt
source-git-commit: 56c2e6b55964ea5f3e180b17bd2a244882aa62ea
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---


# Scores en Badges Essentials {#scoring-and-badges-essentials}

De functie AEM Communities scoren en badges biedt de mogelijkheid om leden van de gemeenschap te identificeren en te belonen.

De details van het instellen van de functie worden beschreven op

* [Scores en badges van gemeenschappen](/help/communities/implementing-scoring.md)

Deze pagina bevat aanvullende technische gegevens:

* Een badge [als afbeelding of tekst](#displaying-badges) weergeven
* Hoe te om uitgebreide [zuivert registreren aan te zetten](#debug-log-for-scoring-and-badging)
* Hoe te om tot UGC [met betrekking tot het scoring en het badging](#ugc-for-scoring-and-badging) toegang te hebben

>[!CAUTION]
>
>De implementatiestructuur die zichtbaar is in CRXDE Lite kan worden gewijzigd.

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

Indien waar (true), geeft isAssigned aan dat de badge voor een rol is toegewezen en dat de badge als tekst moet worden weergegeven.

Indien onwaar (false), wordt bij Toewijzen aangegeven dat de badge is toegekend voor een verdiende score en dat het badge moet worden weergegeven als een afbeelding.

Wijzigingen in dit gedrag moeten worden aangebracht in een aangepast script (overschrijven of bedekken). Zie Aanpassing aan [clientzijde](/help/communities/client-customize.md).

## Foutopsporingslogboek voor score en Badging {#debug-log-for-scoring-and-badging}

Voor foutopsporing in scores en badging kan een aangepast logbestand worden ingesteld. De inhoud van dit logbestand kan dan aan de klantenondersteuning worden verstrekt als er problemen met de functie worden ondervonden.

Voor gedetailleerde instructies gaat u naar [Een aangepast logbestand](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file)maken.

U kunt als volgt snel een logbestand instellen:

1. Toegang tot de Steun **van het Logboek van de Console van het Web van de** Adobe Experience Manager, bijvoorbeeld

   * https://localhost:4502/system/console/slinglog

1. Selecteer **Nieuwe logboekregistratie toevoegen**

   1. Selecteren `DEBUG` voor **logniveau**

   1. Geef bijvoorbeeld een naam op voor het **logbestand**

      * logs/scoring-debug.log
   1. Twee **Logger** -items (klasse) invoeren (met `+` pictogram)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Selecteer **Opslaan**



![chlimage_1-248](assets/chlimage_1-248.png)

Logboekvermeldingen weergeven:

* Vanuit de webconsole

   * Onder het menu **Status**
   * Logbestanden **selecteren**
   * Zoek naar uw naam van het Logdossier, zoals `scoring-debug`

* Op de lokale schijf van de server

   * Het logbestand bevindt zich op &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log

   * Bijvoorbeeld, `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC voor scores en Badging {#ugc-for-scoring-and-badging}

Het is mogelijk om UGC met betrekking tot het scoring en het aanbrengen van merktekens te bekijken wanneer gekozen SRP of JSRP of MSRP, maar niet ASRP is. (Als u niet bekend bent met deze termen, raadpleegt u het overzicht [](/help/communities/working-with-srp.md) Community Content Storage [en](/help/communities/srp.md)Storage Resource Provider.)

In de beschrijvingen voor toegang tot scoring- en merkgegevens wordt JSRP gebruikt, omdat de UGC gemakkelijk toegankelijk is met [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

**JSRP bij auteur**: experimenteren in de auteursomgeving resulteert in UGC die alleen zichtbaar is vanuit de auteursomgeving.

**JSRP bij publicatie**: Op dezelfde wijze, als het testen op het publicatiemilieu, zal het noodzakelijk zijn om tot CRXDE Lite met administratieve voorrechten op een te publiceren instantie toegang te hebben. Als de publicatie-instantie wordt uitgevoerd in de [productiemodus](/help/sites-administering/production-ready.md) (geen samplcontent runmode), is het nodig om CRXDE Lite [in te](/help/sites-administering/enabling-crxde-lite.md)schakelen.

De basislocatie van UGC op JSRP is `/content/usergenerated/asi/jcr/`.

### API&#39;s voor scores en Badging {#scoring-and-badging-apis}

De volgende API&#39;s zijn beschikbaar voor gebruik:

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

De nieuwste JavaDocs voor het geïnstalleerde functiepakket zijn beschikbaar voor ontwikkelaars in de opslagplaats van Adobe. Zie [Maven gebruiken voor Gemeenschappen: Javadocs](/help/communities/maven.md#javadocs).

**De locatie en indeling van de UGC in de opslagplaats kunnen zonder waarschuwing** worden gewijzigd.

### Voorbeeld instellen {#example-setup}

De schermafbeeldingen van gegevensopslagruimte zijn afkomstig van het instellen van scoring en badging voor een forum op twee verschillende AEM-sites:

1. Een AEM-site *met* een unieke id (een site die is gemaakt met een wizard):

   * De Aan de slag-zelfstudie (Inschakelen) gebruiken die tijdens de [Aan de slag-zelfstudie is gemaakt](/help/communities/getting-started.md)
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

   * Eigenschap toevoegen aan weergaveknoppen

      `allowBadges = true`

   * Een gebruiker ondertekent in, maakt een forumonderwerp en krijgt een bronzen badge toegewezen


1. Een AEM-site *zonder* unieke id:

   * De hulplijn [Community-componenten gebruiken](/help/communities/components-guide.md)
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

   * Eigenschap toevoegen aan weergaveknoppen

      `allowBadges = true`

   * Een gebruiker ondertekent in, maakt een forumonderwerp en krijgt een bronzen badge toegewezen


1. Aan een gebruiker wordt een moderatorbadge toegewezen via cURL:

   ```shell
   curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" https://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
   ```

   Aangezien een gebruiker twee bronzen badges heeft verdiend en een moderatorbadge heeft gekregen, is dit hoe de gebruiker met hun forumingang verschijnt.

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>In dit voorbeeld worden de volgende aanbevolen procedures niet gevolgd:
>
>* Namen van scoreregelregels moeten globaal uniek zijn. ze mogen niet met dezelfde naam eindigen.
   >  Een voorbeeld van wat *niet* te doen:
   >  /libs/settings/community/scoring/rules/site1/forums-scoring
   >  /libs/settings/community/scoring/rules/site2/forums-scoring
   >
   >
* Unieke badge-afbeeldingen maken voor verschillende AEM-sites
>



### Toegang tot UGC-score {#access-scoring-ugc}

Het gebruik van de [API&#39;s](#scoring-and-badging-apis) heeft de voorkeur.

Voor onderzoeksdoeleinden, gebruikend JSRP bijvoorbeeld, is de basisomslag die scores bevat

* `/content/usergenerated/asi/jcr/scoring`

De onderliggende node van `scoring` is de naam van de scoreregel. Daarom is het verstandig om regelnamen op een server globaal uniek te scoren.

Voor de site Geometrixx Engage bevinden de gebruiker en hun score zich in een pad dat is geconstrueerd met de naam van de scoreregel, de site-id van de community ( `engage-ba81p`), een unieke id en de id van de gebruiker:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Voor de Community Components-hulplijnsite bevinden de gebruiker en hun score zich in een pad dat is samengesteld met de naam van de scoreregel, een standaard-id ( `default-site`), een unieke id en de id van de gebruiker:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

De score wordt opgeslagen in de eigenschap `scoreValue_tl` die direct alleen een waarde kan bevatten of onrechtstreeks naar een atomicCounter kan verwijzen.

![chlimage_1-251](assets/chlimage_1-251.png)

### Access Badging UGC {#access-badging-ugc}

Het gebruik van de [API&#39;s](#scoring-and-badging-apis) heeft de voorkeur.

Voor onderzoeksdoeleinden, gebruikend JSRP bijvoorbeeld, is de basisomslag die informatie over toegewezen of toegekende badges bevat

* `/content/usergenerated/asi/jcr`

Wordt gevolgd door het pad naar het gebruikersprofiel en eindigt in een map met badges, zoals:

* `/home/users/community/w271OOup2Z4DjnOQrviv/profile/badges`

#### Toegewezen badge {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### Toegewezen badge {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## Additional Information {#additional-information}

Een gesorteerde lijst met leden weergeven op basis van punten:

* [Leaderboard-functie](/help/communities/functions.md#leaderboard-function) voor opname in een community-site of groepssjabloon.
* [Leaderboard-component](/help/communities/enabling-leaderboard.md), de aanbevolen component van de Leaderboard-functie, voor het ontwerpen van pagina&#39;s.

