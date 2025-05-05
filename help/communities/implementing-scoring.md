---
title: Scores en badges van gemeenschappen
description: Met AEM Communities scoring en badges kunt u leden van de gebruikersgemeenschap identificeren en belonen
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
tagskeywords: scoring, badging, badges, gamification
role: Admin
exl-id: 4aa857f7-d111-4548-8f03-f6d6c27acf51
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2856'
ht-degree: 0%

---

# Scores en badges van gemeenschappen {#communities-scoring-and-badges}

## Overzicht {#overview}

Met de functie AEM Communities scoring en badges kunnen leden van de gemeenschap worden geïdentificeerd en beloond.

De belangrijkste aspecten van scoring en badges zijn:

* [ Wijs badges ](#assign-and-revoke-badges) toe om de rol van een lid in de gemeenschap te identificeren.

* [ Basis toewijst van badges ](#enable-scoring) aan leden om hun participatie (hoeveelheid gecreeerde inhoud) aan te moedigen.

* [ Geavanceerde toewijzing van badges ](/help/communities/advanced.md) om leden als deskundigen (kwaliteit van gecreeerde inhoud) te identificeren.

**Nota** dat het verlenen van badges [ niet door gebrek ](/help/communities/implementing-scoring.md#main-pars-text-237875536) wordt toegelaten.

>[!CAUTION]
>
>De implementatiestructuur die zichtbaar is in CRXDE Lite, kan worden gewijzigd zodra de interface beschikbaar is.

## Badges {#badges}

De badges worden onder de naam van een lid geplaatst om hun rol of hun status in de gemeenschap aan te geven. Badges kunnen als een afbeelding of als een naam worden weergegeven. Wanneer de naam als afbeelding wordt weergegeven, wordt deze opgenomen als alternatieve tekst voor toegankelijkheid.

Standaard bevinden badges zich in de volgende opslagplaats:

* `/libs/settings/community/badging/images`

Als ze op een andere locatie zijn opgeslagen, moeten ze door iedereen toegankelijk worden gelezen.

De badges worden in UGC gedifferentieerd, ongeacht of zij volgens de regels zijn toegewezen of verdiend. Momenteel worden toegewezen badges weergegeven als tekst en worden verdiende badges als een afbeelding weergegeven.

### Bandenbeheer-gebruikersinterface {#badge-management-ui}

De console van de Banden van Gemeenschappen [&#128279;](/help/communities/badges.md) laat u douanebadges toevoegen die voor een lid kunnen worden getoond wanneer verdiend (toegekend) of wanneer zij een specifieke rol in de (toegewezen) gemeenschap nemen.

### Toegewezen badges {#assigned-badges}

Op rollen gebaseerde badges worden door een beheerder toegewezen aan leden van de community op basis van hun rol in de community.

De toegewezen (en toegekende) badges worden opgeslagen in geselecteerde [ SRP ](/help/communities/srp.md) en zijn niet direct toegankelijk. Totdat een GUI beschikbaar is, is het enige middel om op rol-gebaseerde badges toe te wijzen dit met code of cURL. Voor cURL instructies, zie de sectie die [ wordt genoemd Wijs en trek Badges ](#assign-and-revoke-badges) terug.

In de release zijn drie badges op basis van rollen opgenomen:

* **moderator**
  `/libs/settings/community/badging/images/moderator/jcr:content/moderator.png`

* **groepsmanager**
  `/libs/settings/community/badging/images/group-manager/jcr:content/group-manager.png`

* **bevoorrecht lid**
  `/libs/settings/community/badging/images/privileged-member/jcr:content/privileged-member.png`

  ![ toegewezen-badges ](assets/assigned-badges.png)

### Toegewezen badges {#awarded-badges}

Op basis van beloningen ontvangen de leden van de gemeenschap een toegangspasje met een score op basis van regels die gelden voor hun activiteiten in de gemeenschap.

Om badges als beloning voor activiteit te laten verschijnen, moeten er twee dingen gebeuren:

* Het badging moet [&#128279;](#enableforcomponent) voor de eigenschapcomponent worden toegelaten.
* Het scoren en het merkteken de regels moeten [ worden toegepast ](#applytopage) op de pagina (of voorvader) waarop de component wordt geplaatst.

De release bevat drie beloningsbadges:

* **goud**
  `/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

* **zilver**
  `/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

* **bronze**
  `/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

  ![ verlenen-badges ](assets/awarded-badges.png)

>[!NOTE]
>
>Scoreregels kunnen worden geconfigureerd om negatieve punten toe te wijzen voor posten die als onjuist zijn gemarkeerd en beïnvloeden zo de score. Als een badge echter eenmaal is behaald, wordt deze niet automatisch verwijderd vanwege wijzigingen in de score- of scoringregel.
>
>Toegewezen badges kunnen op dezelfde wijze worden ingetrokken als toegewezen badges. Zie [ Wijs en trek Badges ](#assign-and-revoke-badges) sectie toe. De toekomstige verbeteringen zullen een UI omvatten om de badges van leden te beheren.

### Aangepaste badges {#custom-badges}

De badges van de douane kunnen worden geïnstalleerd gebruikend de [ console van Badges ](/help/communities/badges.md) en of toegewezen of in het badging regels gespecificeerd.

Wanneer deze vanaf de Badges-console zijn geïnstalleerd, worden aangepaste badges automatisch naar de publicatieomgeving gerepliceerd.

## Muziek inschakelen {#enable-scoring}

Scores is niet standaard ingeschakeld. De basisstappen voor het opzetten en mogelijk maken van scoring en toekenning van badges zijn:

* Identificeer regels voor het verdienen van punten ([ het scoren regels ](#scoring-rules)).
* Voor punten die per het schrapen regels worden verzameld, wijs [ badges ](#badges) toe ([ badging regels ](#badging-rules)).

* [ pas het scoring en het merkingsregels op een communautaire plaats ](#apply-rules-to-content) toe.
* [ laat het badging voor communautaire eigenschappen ](#enable-badges-for-component) toe.

Zie de [ Snelle sectie van de Test ](#quick-test) om het scoren voor een communautaire plaats toe te laten gebruikend het gebrek het scoren en het badging regels voor forums en commentaren.

### Regels toepassen op inhoud {#apply-rules-to-content}

Als u scoring en badges wilt inschakelen, voegt u de eigenschappen `scoringRules` en `badgingRules` toe aan elk knooppunt in de inhoudsstructuur voor de site.

Als de site al is gepubliceerd, publiceert u de site opnieuw nadat u alle regels hebt toegepast en componenten hebt ingeschakeld.

De regels die op een badging-toegelaten component van toepassing zijn zijn die voor de huidige knoop of zijn voorvader.

Als het knooppunt van het type `cq:Page` is (aanbevolen), voegt u met behulp van CRXDE|Lite de eigenschappen toe aan het `jcr:content` -knooppunt.

| **Bezit** | **Type** | **Beschrijving** |
|---|---|---|
| badgingRules | String | een matrixlijst van [ badging regels ](#badging-rules) |
| scoringRules | String | een serielijst van [ het scoren regels ](#scoring-rules) |

>[!NOTE]
>
>Als een het scoren regel geen effect op het verlenen van badges lijkt te hebben, zorg ervoor de het scoren regel niet door het scoringRules bezit van de merkingsregel is geblokkeerd. Zie de sectie genoemd [ het Badging Regels ](#badging-rules).

### Badges voor component inschakelen {#enable-badges-for-component}

De het scoren en het inkleuren regels zijn in feite slechts voor instanties van componenten die merkend hebben toegelaten door de componentenconfiguratie in [ auteurswijze ](/help/communities/author-communities.md) uit te geven.

Een Booleaanse eigenschap, `allowBadges` , schakelt de weergave van badges voor een componentinstantie in of uit. Het is configureerbaar in de [ component geeft dialoog ](/help/communities/author-communities.md) voor forum uit, QnA, en commentaarcomponenten door een checkbox geëtiketteerd **Badges van de Vertoning**.

#### Voorbeeld: allowBadges voor instantie van de component Forum {#example-allowbadges-for-forum-component-instance}

![ toe:laten-badges-component ](assets/enable-badges-component.png)

>[!NOTE]
>
>Elke component kan worden bedekt om badges weer te geven met behulp van de GB-code in forums, QnA en opmerkingen als voorbeeld.

## Scoreregels {#scoring-rules}

Scoreregels vormen de basis voor scoring bij het toekennen van badges.

Elke scoreregel is een lijst met een of meer subregels. Scoreregels worden toegepast op de inhoud van de communautaire plaats om de regels te identificeren om toe te passen wanneer de badges worden toegelaten.

Scoreregels worden overgeërfd, maar niet additief. Bijvoorbeeld:

* Als page2 het scoren regel2 bevat en zijn voorouder page1 het scoren regel1 bevat.
* Een actie op een page2 component roept zowel rule1 als rule2 aan.
* Als beide regels toepasselijke subregels voor hetzelfde bevatten `topic/verb` :

   * Alleen de subregel van rule2 beïnvloedt de score.
   * De scores van beide subregels worden niet toegevoegd.

Wanneer er meer dan één scoreregel is, worden de scores afzonderlijk gehandhaafd voor elke regel.

Scoreregels zijn knooppunten van het type `cq:Page` met eigenschappen op het knooppunt `jcr:content` die de lijst met subregels opgeven die deze definiëren.

Scores worden opgeslagen in SRP.

>[!NOTE]
>
>Beste praktijken: uniek noem elke het noteren regel.
>
>Namen van scores voor regels moeten globaal uniek zijn; ze mogen niet eindigen met dezelfde naam.
>
>Een voorbeeld van wat *niet* te doen:
>
>/libs/settings/community/scoring/rules/site1/forums-scoring
>/libs/settings/community/scoring/rules/site2/forums-scoring

### Subregels voor scores {#scoring-sub-rules}

De subregels voor scoring bevatten de eigenschappen die de waarden voor deelname aan de gemeenschap in detail beschrijven.

Elke scoring-subregel identificeert:

* Welke activiteiten worden getraceerd?
* Welke specifieke communautaire functie is hierbij betrokken?
* Hoeveel punten zijn er toegekend?

Standaard worden punten toegewezen aan het lid dat de handeling uitvoert, tenzij de subregel de eigenaar van de inhoud opgeeft als ontvangende punten ( `forOwner`).

Elke subregel kan in een of meer scoreregels worden opgenomen.

De naam van de onderregel volgt typisch het patroon van het gebruiken van a *onderwerp*, *voorwerp*, en *werkb*. Bijvoorbeeld:

* member-comment-create
* lid-ondervraagden

Subrules zijn knopen van type `cq:Page` met eigenschappen op zijn `jcr:content` knoop die [ werkwoorden en onderwerpen ](#topics-and-verbs) specificeren.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Type</th>
   <th> Beschrijving van waarde</th>
  </tr>
  <tr>
   <td><i><code>VERB</code></i></td>
   <td>Lang</td>
   <td>
    <ul>
     <li>vereist; het werkwoord komt overeen met een gebeurtenisactie</li>
     <li>er moet minstens één werkb-eigenschap zijn</li>
     <li>het werkwoord moet in alle HOOFDLETTERS worden ingevoerd</li>
     <li>er kunnen meerdere werkbalkeigenschappen zijn, maar geen duplicaten</li>
     <li>de waarde is de score die moet worden toegepast voor deze gebeurtenis</li>
     <li>de waarde kan positief of negatief zijn</li>
     <li>een lijst van werkwoorden die in de versie worden gesteund is in de <a href="#topics-and-verbs"> Onderwerpen en van Verbs </a> sectie</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>topics</code></td>
   <td>String</td>
   <td>
    <ul>
     <li>facultatief; beperkt onderregel tot communautaire componenten die door gebeurtenisonderwerpen worden geïdentificeerd</li>
     <li>if specified : value is multi-value string of event topics</li>
     <li>een lijst van onderwerpen in de versie is in de <a href="#topics-and-verbs"> Onderwerpen en Verbs </a> sectie</li>
     <li>standaard is van toepassing op alle onderwerpen verbonden aan werkwoorden</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>forOwner</code></td>
   <td>Boolean</td>
   <td>
    <ul>
     <li>facultatief; niet relevant wanneer een lid handelt over inhoud die hij bezit</li>
     <li>indien waar (true), score toepassen op de eigenaar van inhoud waarop wordt gehandeld</li>
     <li>Indien onwaar (false), score toepassen op een lid dat actie onderneemt</li>
     <li>default is false</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>scoringType</code></td>
   <td>String</td>
   <td>
    <ul>
     <li>facultatief; identificeert de scores motor</li>
     <li>indien "basic", de scoring-engine op basis van de hoeveelheid
      <ul>
       <li>opgenomen in de release</li>
      </ul> </li>
     <li>geeft, indien "geavanceerd", de scores aan op basis van kwaliteit en hoeveelheid
      <ul>
       <li>vereist een <a href="/help/communities/advanced.md"> extra pakket </a></li>
      </ul> </li>
     <li>default is "basic"</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Inclusief rangtelregels en subregels {#included-scoring-rules-and-sub-rules}

Omvat in de versie zijn twee het scoren regels voor de [ Functie van het Forum ](/help/communities/functions.md#forum-function) (elk voor het Forum en de componenten van Commentaren van de eigenschap van het Forum):

1. /libs/settings/community/scoring/rules/comments-scoring

   * subRules [] =
/libs/settings/community/scoring/rules/sub-rules/member-comment-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-voice
/libs/settings/community/scoring/rules/sub-rules/member-giving-voice
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

1. /libs/settings/community/scoring/rules/forums-scoring

   * subRules [] =
/libs/settings/community/scoring/rules/sub-rules/member-forum-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-voice
/libs/settings/community/scoring/rules/sub-rules/member-giving-voice
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

**Nota&#39;s:**

* Zowel `rules` als `sub-rules` knooppunten zijn van het type cq:Page.

* `subRules` is een attribuut van typeKoord [] op de 2&rbrace; knoop van de regel.`jcr:content`

* `sub-rules` kan worden gedeeld door verschillende scoreregels.
* `rules` moet zich op een repository locatie bevinden met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste sorteerregels activeren {#activating-custom-scoring-rules}

Wijzigingen of toevoegingen aan de in de ontwerpomgeving aangebrachte scoreregels of subregels moeten bij publicatie worden geïnstalleerd.

## Badgingregels {#badging-rules}

De regels van de Badging koppelen het scoring regels aan badges door te specificeren:

* Scoreregel
* Score nodig om een specifieke badge te krijgen

Badgingregels zijn knooppunten van het type `cq:Page` met eigenschappen op het `jcr:content` -knooppunt die correleren tussen scoreregels en scores en badges.

De regels voor badging bestaan uit een verplichte eigenschap `thresholds` die een geordende lijst is met scores die zijn toegewezen aan badges. De scores moeten in stijgende waarde worden bevolen. Bijvoorbeeld:

* `1|/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Een bronzen badge wordt toegekend om één punt te verdienen.

* `60|/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

   * Een zilveren badge wordt toegekend wanneer 60 punten zijn opgebouwd.

* `80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

   * Een gouden badge wordt toegekend wanneer 80 punten zijn verzameld.

De regels van de Badging zijn gepareerd met het scoring regels, die bepalen hoe de punten zich ophopen. Zie de sectie genoemd [ Regels op Inhoud ](#apply-rules-to-content) toepassen.

De eigenschap `scoringRules` op een badging-regel beperkt eenvoudig welke scoring-regels met die bepaalde badging-regel kunnen worden gekoppeld.

>[!NOTE]
>
>Tips en trucs: maak badge-afbeeldingen die uniek zijn voor elke AEM.

![ badging-regel-configuratie ](assets/badging-rule-configuration.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Type</th>
   <th>Beschrijving van waarde</th>
  </tr>
  <tr>
   <td>drempelwaarden</td>
   <td>String</td>
   <td><em> (vereist) </em> Een tekenreeks met meerdere waarden in de vorm 'number|path'
    <ul>
     <li>number = score</li>
     <li>| = het verticale lijnteken (U+007C)</li>
     <li>path = full path to badge image resource</li>
    </ul> De tekenreeksen moeten worden geordend, zodat de getallen in waarde toenemen en er geen lege ruimte tussen het getal en het pad wordt weergegeven.<br /> Voorbeeld:<br /> <code>80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png</code></td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>String</td>
   <td><em> (facultatief) </em> identificeert de het scoring motor als of "basis"of "geavanceerd". Als de geavanceerde het scoren motor wordt gewenst, zie <a href="/help/communities/advanced.md"> Geavanceerde het Scoreren en Badges </a>. De standaardwaarde is "basic".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>String</td>
   <td>(<em> facultatief </em>) een multi-waardekoord om de merkingsregel te beperken tot het schrapen van gebeurtenissen die door de het scoren regels worden geïdentificeerd</td>
  </tr>
 </tbody>
</table>

### Ingesloten Badgingregels {#included-badging-rules}

Omvat in de versie zijn twee het Badging Regels die aan de [ Forums en Commentaren het Scoren Regels ](#includedscoringrules) beantwoorden.

* `/libs/settings/community/badging/rules/comments-badging`

* `/libs/settings/community/badging/rules/forums-badging`

**Nota&#39;s:**

* `rules` -knooppunten zijn van het type cq:Page.
* `rules` moet zich op een repository locatie bevinden met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste Badgingregels activeren {#activating-custom-badging-rules}

Wijzigingen of toevoegingen aan badgingregels of afbeeldingen die in de ontwerpomgeving zijn aangebracht, moeten bij publicatie worden geïnstalleerd.

## Badges toewijzen en intrekken {#assign-and-revoke-badges}

De badges kunnen aan leden worden toegewezen die of de [ ledenconsole ](/help/communities/members.md#badges-tab) gebruiken of programmatically cURL bevelen gebruiken.

De volgende cURL-opdrachten tonen wat nodig is voor een HTTP-aanvraag voor het toewijzen en intrekken van badges. De basisindeling is:

cURL - i -X POST - H *kopbal* - u *signaleert* - F *verrichting* - F *badge* *lid-profiel-url*

*kopbal* = &quot;Accept:application/json&quot;
aangepaste header die aan de server moet worden doorgegeven (vereist)

*teken* = beheerder-identiteitskaart:wachtwoord
bijvoorbeeld admin:admin

*verrichting* = &quot;:operation=social:assignBadge&quot;OF &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath= *badge-image-file*&quot;

*badge-beeld-dossier* = de plaats van het dossier van het merkbeeld in de bewaarplaats
bijvoorbeeld /libs/settings/community/badging/images/moderator/jcr:content/moderator.png

*lid-profiel-url* = het eindpunt voor het profiel van het lid op publiceren
bijvoorbeeld https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>*lid-profiel-url*:
>
>* Kan naar een auteursinstantie verwijzen als de [ Dienst van de Tunnel ](/help/communities/users.md#tunnel-service) wordt toegelaten.
>* Kan een obscure, willekeurige naam zijn - zie [ Controlelijst van de Veiligheid ](/help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) betreffende machtigbare identiteitskaart.

### Voorbeelden: {#examples}

#### Een moderatorbadge toewijzen {#assign-a-moderator-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### Toegewezen zilverbadge intrekken {#revoke-an-assigned-silver-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:deleteBadge" -F "badgeContentPath=/libs/settings/community/badging/images/silver/jcr:content/silver.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

>[!NOTE]
>
>Het gebruik van cURL om badges toe te wijzen en in te trekken werkt voor elke badge-afbeelding, maar als deze is toegewezen in plaats van verdiend, worden ze gemarkeerd als toegewezen badges en dienovereenkomstig afgehandeld.

## Scores en badges voor aangepaste componenten {#scoring-and-badges-for-custom-components}

Het scoren en het merkteken de regels kunnen voor douanecomponenten worden gecreeerd door de gebeurtenisonderwerpen te associëren die voor de component met werkwoorden worden gecreeerd.

## Onderwerpen en werven {#topics-and-verbs}

Wanneer leden communiceren met functies van gemeenschappen, worden gebeurtenissen verzonden die asynchrone listeners, zoals meldingen en scoring, kunnen activeren.

De instantie SocialEvent van een component registreert de gebeurtenissen als `actions` die voor een `topic` voorkomen. De SocialEvent bevat een methode om een `verb` te retourneren die aan de handeling is gekoppeld. Er is een *n-1* verhouding tussen `actions` en `verbs`.

Voor de geleverde gemeenschappen componenten, beschrijven de volgende lijsten `verbs` die voor elk `topic` beschikbaar voor gebruik in [ het scoren subrules ](#scoring-sub-rules) worden bepaald.

>[!NOTE]
>
>Een nieuwe booleaanse eigenschap, `allowBadges` , schakelt de weergave van badges voor een componentinstantie in of uit. Het is configureerbaar in bijgewerkte [ component geeft dialogen ](/help/communities/author-communities.md) door een checkbox geëtiketteerd **Badges van de Vertoning** uit.

**[Component van de Kalender](/help/communities/calendar.md)**
SocialEvent `topic`= com/adobe/cq/social/agenda

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een kalendergebeurtenis |
| ADD | opmerkingen van leden over een agendagebeurtenis |
| BIJWERKEN | agendagebeurtenis of commentaar van lid wordt bewerkt |
| DELETE | agendagebeurtenis of commentaar van lid wordt verwijderd |

**[Component van Commentaren](/help/communities/comments.md)**
SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een opmerking |
| ADD | reactie van lid op opmerking |
| BIJWERKEN | commentaar van lid is bewerkt |
| DELETE | commentaar van lid is verwijderd |

**[de Component van de Bibliotheek van het Dossier](/help/communities/file-library.md)**
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een map |
| ATTACH | lid uploadt een bestand |
| BIJWERKEN | lid werkt een map of bestand bij |
| DELETE | lid verwijdert een map of bestand |

**[Component van het Forum](/help/communities/forum.md)**
SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt forum-onderwerp |
| ADD | reacties van leden op forum onderwerp |
| BIJWERKEN | onderwerp of antwoord van lid van forum wordt bewerkt |
| DELETE | forumonderwerp of antwoord van lid wordt verwijderd |

**[Component van het Dagboek](/help/communities/blog-feature.md)**
SocialEvent `topic`= com/adobe/cq/social/journaal

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een blogartikel |
| ADD | commentaar van leden op blogartikel |
| BIJWERKEN | blogartikel of commentaar van lid wordt bewerkt |
| DELETE | blogartikel of commentaar van lid is verwijderd |

**[Component QnA](/help/communities/working-with-qna.md)**
SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een QnA-vraag |
| ADD | lid maakt een antwoord op vraag |
| BIJWERKEN | Vraag of antwoord van lid wordt bewerkt |
| SELECT | het antwoord van lid is geselecteerd |
| SELECTEREN OPHEFFEN | het antwoord van het lid is gedeselecteerd |
| DELETE | Vraag of antwoord van lid wordt verwijderd |

**[Component van Revisies](/help/communities/reviews.md)**
SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt beoordeling |
| BIJWERKEN | beoordeling door lid wordt bewerkt |
| DELETE | beoordeling door lid is verwijderd |

**[de Component van de Classificatie](/help/communities/rating.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/rating

| **Verb** | **Beschrijving** |
|---|---|
| WAARDERING TOEVOEGEN | de inhoud van het lid is opgegeven |
| RATING VERWIJDEREN | de inhoud van het lid is neergezet |

**[Stemende Component](/help/communities/voting.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/stemgerechtigd

| **Verb** | **Beschrijving** |
|---|---|
| STEMMING TOEVOEGEN | de inhoud van het lid is in stemming gebracht |
| STEMMING VERWIJDEREN | over de inhoud van het lid is gestemd |

**moderatie-Toegelaten Componenten**
SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschrijving** |
|---|---|
| DENKEN | de inhoud van het lid wordt geweigerd |
| VLAG ALS ONJUIST | inhoud van lid is gemarkeerd |
| ONGESCHIKTE LAG ALS ONJUIST | inhoud van lid is ongemarkeerd |
| ACCEPTEREN | de inhoud van het lid wordt goedgekeurd door moderator |
| SLUITEN | lid sluit commentaar op bewerkingen en reacties |
| OPENEN | opmerking voor opnieuw openen lid |

### Aangepaste componentgebeurtenissen {#custom-component-events}

Voor een aangepaste component wordt een SocialEvent geïnstantieerd om de gebeurtenissen van de component op te nemen als `actions` die voor een `topic` voorkomen.

Voor ondersteuning van scoring moet de methode `getVerb()` worden overschreven door de SocialEvent, zodat de juiste `verb` wordt geretourneerd voor elke `action` methode. De `verb` die voor een actie wordt geretourneerd, kan een algemene instructie zijn (zoals `POST` ) of een speciale instructie voor de component (zoals `ADD RATING` ). Er is een *n-1* verhouding tussen `actions` en `verbs`.

## Problemen oplossen {#troubleshooting}

### Badges worden niet weergegeven {#badges-are-not-appearing}

Als op de inhoud van de website wel scoring- en badgingregels zijn toegepast, maar er geen badges worden toegekend voor activiteiten, moet u ervoor zorgen dat badges zijn ingeschakeld voor de instantie van die component.

Zie [ Badges voor Component ](#enable-badges-for-component) toelaten.

### Scoreregel heeft geen effect {#scoring-rule-has-no-effect}

Als op de inhoud van de website scoring- en badingregels zijn toegepast en badges worden toegekend voor bepaalde acties, maar niet voor andere, controleert u of de regel voor badging de scoringregels waarop deze van toepassing is, niet heeft beperkt.

Zie het `scoringRules` bezit van [ het Badging Regels ](#badging-rules).

### Hoofdlettergevoelig (typ) {#case-sensitive-typo}

De meeste eigenschappen en waarden, met name de werkwoorden, zijn hoofdlettergevoelig. Bij gebruik in een scoringsubregel moeten de hoekpunten allemaal HOOFDLETTERS zijn.

Als de functie niet naar behoren werkt, controleert u of de gegevens correct zijn ingevoerd.

## Snel testen {#quick-test}

Het is mogelijk om het scoren en het tekenen snel te proberen gebruikend [ Begonnen het Leerprogramma ](/help/communities/getting-started.md) (verbind) plaats:

* Toegang tot CRXDE Lite bij auteur.
* Blader naar de basispagina:

   * /content/sites/engc/nl/jcr:content

* Voeg de eigenschap badgingRules toe:

   * **Naam**: `badgingRules`
   * **Type**: `String`
   * Selecteer **Multi**
   * Selecteer **toevoegen**
   * Enter `/libs/settings/community/badging/rules/forums-badging`
   * Selecteren **+**
   * Enter `/libs/settings/community/badging/rules/comments-badging`
   * Selecteer **OK**

* Voeg de eigenschap scoringRules toe:

   * **Naam**: `scoringRules`
   * **Type**: `String`
   * Selecteer **Multi**
   * Selecteer **toevoegen**
   * Enter `/libs/settings/community/scoring/rules/forums-scoring`
   * Selecteren **+**
   * Enter `/libs/settings/community/scoring/rules/comments-scoring`
   * Selecteer **OK**

* Selecteer **sparen allen**.

![ test-scoring-badging ](assets/test-scoring-badging.png)

Zorg er daarna voor dat de forum- en commentaarcomponenten het weergeven van badges toestaan:

* Opnieuw met gebruik van CRXDE Lite.
* Bladeren naar de forumcomponent

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Voeg de Booleaanse eigenschap allowBadges toe, indien nodig, en zorg ervoor dat dit waar is.

   * **Naam**: `allowBadges`
   * **Type**: `Boolean`
   * **Waarde**: `true`

![ test-forum-component ](assets/test-forum-component.png)

Daarna, [ herpubliceer ](/help/communities/sites-console.md#publishing-the-site) de communautaire plaats.

Tot slot:

* Blader naar de component in de publicatie-instantie.
* Meld u aan als lid van de gemeenschap (bijvoorbeeld weston.mccall@dodgit.com / wachtwoord).
* Post: een nieuw forumonderwerp.
* De badge wordt alleen weergegeven als de pagina is vernieuwd.

   * Meld u af en meld u aan als een ander lid van de gemeenschap (bijvoorbeeld: aaron.mcdonald@mailinator.com/password).

* Selecteer het Forum.

Dit zou het lid van de gemeenschap een bronzen badge moeten verdienen die met hun forumpost zichtbaar is omdat de eerste drempel van de forums-badging regel een score van 1 is.

![ bronzebadge ](assets/bronzebadge.png)

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [ het Scoren van de Hoofdzaak van Badges ](/help/communities/configure-scoring.md) pagina voor ontwikkelaars worden gevonden.

Voor informatie over de geavanceerde het scoren motor, zie [ Geavanceerde het Scoreren en Badges ](/help/communities/advanced.md).

De configureerbare component van Leaderboard [&#128279;](/help/communities/enabling-leaderboard.md) en [ functie ](/help/communities/functions.md#leaderboard-function) vereenvoudigt de vertoning van leden en hun scores op een communautaire plaats.
