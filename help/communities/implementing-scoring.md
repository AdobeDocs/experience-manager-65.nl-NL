---
title: Scores en badges van gemeenschappen
seo-title: Scores en badges van gemeenschappen
description: Met AEM Communities scoring en badges kunt u leden van de gebruikersgemeenschap identificeren en belonen
seo-description: Met AEM Communities scoring en badges kunt u leden van de gebruikersgemeenschap identificeren en belonen
uuid: d73683df-a413-4b3c-869c-67568bfdfcf6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ea033bb9-cb92-4c93-855f-8c902999378c
docset: aem65
tagskeywords: scoring, badging, badges, gamification
translation-type: tm+mt
source-git-commit: 2daf00f17058de8b901848fcf1128a5ee9770368
workflow-type: tm+mt
source-wordcount: '2884'
ht-degree: 1%

---


# Scores en badges van gemeenschappen {#communities-scoring-and-badges}

## Overzicht {#overview}

Met de functie AEM Communities scoring en badges kunnen leden van de gemeenschap worden geïdentificeerd en beloond.

De belangrijkste aspecten van scoring en badges zijn:

* [Wijs ](#assign-and-revoke-badges) badgesto toe om de rol van een lid in de gemeenschap te identificeren.

* [Basis toekenning van ](#enable-scoring) badgesto-leden om hun deelname aan te moedigen (hoeveelheid geschapen inhoud).

* [Geavanceerde distributie van ](/help/communities/advanced.md) badgesto om leden te identificeren als experts (kwaliteit van de gemaakte inhoud).

**Het** vermelden van badges is  [niet standaard](/help/communities/implementing-scoring.md#main-pars-text-237875536) ingeschakeld.

>[!CAUTION]
>
>De implementatiestructuur die zichtbaar is in CRXDE Lite, kan worden gewijzigd zodra de interface beschikbaar is.

## Badges {#badges}

De badges worden onder de naam van een lid geplaatst om hun rol of hun status in de gemeenschap aan te geven. Badges kunnen als een afbeelding of als een naam worden weergegeven. Wanneer de naam als afbeelding wordt weergegeven, wordt deze opgenomen als alternatieve tekst voor toegankelijkheid.

Standaard bevinden badges zich in de dataopslag op

* `/libs/settings/community/badging/images`

Als ze op een andere locatie zijn opgeslagen, moeten ze door iedereen toegankelijk worden gelezen.

De badges zijn in de UGC verschillend wat betreft de vraag of zij volgens de regels werden toegewezen of verdiend. Momenteel worden toegewezen badges weergegeven als tekst en worden verdiende badges als een afbeelding weergegeven.

### Gebruikersinterface Badge Management {#badge-management-ui}

De Gemeenschappen [Badges console](/help/communities/badges.md) verstrekt de capaciteit om douanebadges toe te voegen die voor een lid kunnen worden getoond wanneer verdiend (toegekend) of wanneer zij een specifieke rol in de (toegewezen) gemeenschap op zich nemen.

### Toegewezen badges {#assigned-badges}

Op rollen gebaseerde badges worden door een beheerder toegewezen aan leden van de community op basis van hun rol in de community.

Toegewezen (en geawade) badges worden opgeslagen in de geselecteerde [SRP](/help/communities/srp.md) en zijn niet direct toegankelijk. Totdat een GUI beschikbaar is, is het enige middel om op rol-gebaseerde badges toe te wijzen dit met code of cURL. Voor cURL-instructies raadpleegt u de sectie [Badges toewijzen en intrekken](#assign-and-revoke-badges).

In de release zijn drie badges op basis van rollen opgenomen:

* **moderator**

   `/libs/settings/community/badging/images/moderator/jcr:content/moderator.png`

* **groepsbeheerder**

   `/libs/settings/community/badging/images/group-manager/jcr:content/group-manager.png`

* **geprivilegieerd lid**

   `/libs/settings/community/badging/images/privileged-member/jcr:content/privileged-member.png`

   ![toegewezen badges](assets/assigned-badges.png)

### Toegewezen badges {#awarded-badges}

Op basis van beloningen ontvangen de leden van de gemeenschap een toegangspasje met een score op basis van regels die gelden voor hun activiteiten in de gemeenschap.

Om badges als beloning voor activiteit te kunnen weergeven, moeten er twee dingen gebeuren:

* Badging moet [enabled](#enableforcomponent) voor de eigenschapcomponent zijn.
* De regels voor het noteren en het aanbrengen van merktekens moeten [worden toegepast](#applytopage) op de pagina (of de voorouder) waarop de component wordt geplaatst.

De release bevat drie beloningsbadges:

* **goud**

   `/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

* **zilver**

   `/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

* **brons**

   `/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   ![bekroonde badges](assets/awarded-badges.png)

>[!NOTE]
>
>Scoreregels kunnen worden geconfigureerd om negatieve punten toe te wijzen voor posten die als onjuist zijn gemarkeerd en beïnvloeden zo de score. Als een badge echter eenmaal is behaald, wordt deze niet automatisch verwijderd vanwege wijzigingen in de score- of scoringregel.
>
>Toegewezen badges kunnen op dezelfde wijze worden ingetrokken als toegewezen badges. Zie de sectie [Badges toewijzen en intrekken](#assign-and-revoke-badges). De toekomstige verbeteringen zullen een UI omvatten om de badges van leden te beheren.

### Aangepaste badges {#custom-badges}

Aangepaste badges kunnen worden geïnstalleerd met de [Badges-console](/help/communities/badges.md) en worden toegewezen aan of opgegeven in badgingregels.

Wanneer deze vanaf de Badges-console zijn geïnstalleerd, worden aangepaste badges automatisch naar de publicatieomgeving gerepliceerd.

## Muziek {#enable-scoring} inschakelen

Scores is niet standaard ingeschakeld. De basisstappen voor het opzetten en mogelijk maken van scoring en toekenning van badges zijn:

* Identificeer regels voor het verdienen van punten ([het scoren regels](#scoring-rules)).
* Wijs [badges](#badges) ([badgregels](#badging-rules)) toe voor punten die volgens scoringregels zijn geaccumuleerd.

* [Pas de scoring- en badingregels toe op een communitysite](#apply-rules-to-content).
* [Enable badging for community features](#enable-badges-for-component).

Zie de sectie [Snelle test](#quick-test) om het scoren voor een gemeenschapssite in te schakelen met de standaardregels voor scoring en badging voor forums en opmerkingen.

### Regels toepassen op inhoud {#apply-rules-to-content}

Als u scoring en badges wilt inschakelen, voegt u de eigenschappen `scoringRules` en `badgingRules` toe aan een willekeurig knooppunt in de inhoudsstructuur voor de site.

Als de site al is gepubliceerd nadat alle regels zijn toegepast en componenten zijn ingeschakeld, publiceert u de site opnieuw.

De regels die op een badging-toegelaten component van toepassing zijn zijn die voor de huidige knoop of zijn voorvader.

Als het knooppunt van het type `cq:Page` (aanbevolen) is, voegt u met behulp van CRXDE|Lite de eigenschappen toe aan het `jcr:content`-knooppunt.

| **Eigenschap** | **Type** | **Beschrijving** |
|---|---|---|
| badgingRules | Tekenreeks | een arraylijst met [badging rules](#badging-rules) |
| scoringRules | Tekenreeks | een arraylijst met [scoringregels](#scoring-rules) |

>[!NOTE]
>
>Als een het scoren regel geen effect op het verlenen van badges lijkt te hebben, zorg ervoor de het scoren regel niet door het scoringRules bezit van de merkingsregel is geblokkeerd. Zie de sectie [Badging Rules](#badging-rules).

### Badges voor component {#enable-badges-for-component} inschakelen

De het scoren en het inkleuren regels zijn in feite slechts voor instanties van componenten die merkings door de componentenconfiguratie in [auteurswijze ](/help/communities/author-communities.md) te uitgeven hebben toegelaten.

Een booleaanse eigenschap, `allowBadges`, schakelt de weergave van badges voor een componentinstantie in of uit. Het is configureerbaar in [component uitgeeft dialoog](/help/communities/author-communities.md) voor forum, QnA en commentaarcomponenten door een checkbox geëtiketteerd **de Badges van de Vertoning**.

#### Voorbeeld: allowBadges voor instantie van de component Forum {#example-allowbadges-for-forum-component-instance}

![enable-badges-component](assets/enable-badges-component.png)

>[!NOTE]
>
>Elke component kan worden bedekt om badges weer te geven met behulp van de GB-code in forums, QnA en opmerkingen als voorbeeld.

## Scoreregels {#scoring-rules}

Scoreregels vormen de basis voor scoring met het oog op het toekennen van badges.

Heel eenvoudig, is elke het scoren regel een lijst van één of meerdere sub-regels. Scoreregels worden toegepast op de inhoud van de communautaire plaats om de regels te identificeren om toe te passen wanneer de badges worden toegelaten.

Scoreregels worden overgeërfd, maar niet additief. Bijvoorbeeld:

* Als page2 het scoren regel2 bevat en zijn voorouder page1 het scoren regel1 bevat.
* Een actie op een page2 component zal zowel rule1 als rule2 aanhalen.
* Indien beide regels toepasselijke subregels voor dezelfde `topic/verb` bevatten:

   * Alleen de subregel van regel2 heeft invloed op de score.
   * De scores uit beide subregels worden niet bij elkaar opgeteld.

Wanneer er meer dan één scoreregel is, worden de scores afzonderlijk gehandhaafd voor elke regel.

Scoreregels zijn knooppunten van het type `cq:Page` met eigenschappen op zijn `jcr:content` knoop die de lijst van subregels specificeren die het bepalen.

Scores worden opgeslagen in SRP.

>[!NOTE]
>
>Beste praktijken: Geef elke scoreregel een unieke naam.
>
>Namen van scoreregelregels moeten globaal uniek zijn. ze mogen niet met dezelfde naam eindigen.
>
>Een voorbeeld van wat *not* moet doen:
>
>/libs/settings/community/scoring/rules/site1/forums-scoring
>/libs/settings/community/scoring/rules/site2/forums-scoring

### Subregels voor het sorteren {#scoring-sub-rules}

De scoringsubregels bevatten de eigenschappen die de waarden voor deelname aan de gemeenschap in detail beschrijven.

Elke scoring-subregel identificeert:

* Welke activiteiten worden getraceerd?
* Welke specifieke communautaire functie is hierbij betrokken?
* Hoeveel punten zijn er toegekend?

Standaard worden punten toegewezen aan het lid dat de handeling uitvoert, tenzij de subregel de eigenaar van de inhoud opgeeft als ontvangende punten ( `forOwner`).

Elke subregel kan in een of meer scoreregels worden opgenomen.

De naam van de subregel volgt typisch het patroon van het gebruiken van *subject*, *object* en *verb*. Bijvoorbeeld:

* member-comment-create
* lid-ondervraagden

Subregels zijn knooppunten van het type `cq:Page` met eigenschappen op zijn `jcr:content`knooppunt die [werkwoorden en onderwerpen](#topics-and-verbs) specificeren.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Type</th>
   <th> Waarde Beschrijving</th>
  </tr>
  <tr>
   <td><i><code>VERB</code></i></td>
   <td>Lang</td>
   <td>
    <ul>
     <li>vereist; het werkwoord correspondeert met een gebeurtenisactie</li>
     <li>er moet minstens één werkb-eigenschap zijn</li>
     <li>het werkwoord moet in alle HOOFDLETTERS worden ingevoerd</li>
     <li>er kunnen meerdere werkbalkeigenschappen zijn, maar geen duplicaten</li>
     <li>de waarde is de score die moet worden toegepast voor deze gebeurtenis</li>
     <li>de waarde kan positief of negatief zijn</li>
     <li>een lijst van werkwoorden die in de versie worden gesteund is in <a href="#topics-and-verbs">Onderwerpen en Verbs</a> sectie</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>topics</code></td>
   <td>Tekenreeks</td>
   <td>
    <ul>
     <li>facultatief; beperkt subregel tot componenten van de gemeenschap die door gebeurtenisonderwerpen worden geïdentificeerd</li>
     <li>indien gespecificeerd: waarde is een tekenreeks met meerdere waarden voor gebeurtenisonderwerpen</li>
     <li>Een lijst met onderwerpen in de release vindt u in de sectie <a href="#topics-and-verbs">Onderwerpen en Verbs</a></li>
     <li>Standaard is dit van toepassing op alle onderwerpen die aan het werkwoord of de werkwoorden zijn gekoppeld</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>forOwner</code></td>
   <td>Boolean</td>
   <td>
    <ul>
     <li>facultatief; niet van belang wanneer een lid handelt over de inhoud die hij bezit</li>
     <li>indien waar (true), score toepassen op de eigenaar van inhoud waarop wordt gehandeld</li>
     <li>Indien onwaar (false), score toepassen op een lid dat actie onderneemt</li>
     <li>default is false</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>scoringType</code></td>
   <td>Tekenreeks</td>
   <td>
    <ul>
     <li>facultatief; geeft de scores aan</li>
     <li>indien "basic", de scoring-engine op basis van de hoeveelheid
      <ul>
       <li>opgenomen in de release</li>
      </ul> </li>
     <li>geeft, indien "geavanceerd", de scores aan op basis van kwaliteit en hoeveelheid
      <ul>
       <li>vereist een <a href="/help/communities/advanced.md">extra pakket</a></li>
      </ul> </li>
     <li>default is "basic"</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Inclusief rangtelregels en subregels {#included-scoring-rules-and-sub-rules}

In de release zijn twee scoreregels opgenomen voor de functie [Forum Function](/help/communities/functions.md#forum-function) (een voor de componenten Forum en Comments van de functie Forum):

1. /libs/settings/community/scoring/rules/comments-scoring

   * subRules[] =
/libs/settings/community/scoring/rules/sub-rules/member-comment-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-voice
/libs/settings/community/scoring/rules/sub-rules/member-giving-voice
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

1. /libs/settings/community/scoring/rules/forums-scoring

   * subRules[] =
/libs/settings/community/scoring/rules/sub-rules/member-forum-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-voice
/libs/settings/community/scoring/rules/sub-rules/member-giving-voice
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

**Opmerkingen:**

* Zowel `rules` als `sub-rules` knooppunten zijn van het type cq:Page.

* `subRules` is een attribuut van type [] Stringon de  `jcr:content` knoop van de regel.

* `sub-rules` kunnen worden gedeeld door verschillende scoreregels.
* `rules` moet zich bevinden op een locatie in de opslagplaats met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste sorteerregels {#activating-custom-scoring-rules} activeren

Wijzigingen of toevoegingen aan de in de ontwerpomgeving aangebrachte scoreregels of subregels moeten bij publicatie worden geïnstalleerd.

## Badgingregels {#badging-rules}

De regels van de Badging koppelen het scoring regels aan badges door te specificeren:

* Scoreregel
* Score die nodig is om een specifieke badge te ontvangen

Badgingregels zijn knooppunten van het type `cq:Page` met eigenschappen op het `jcr:content`-knooppunt die correleren met scores en badges.

De regels voor badging bestaan uit een verplichte `thresholds` eigenschap die een geordende lijst is met scores die zijn toegewezen aan badges. De scores moeten in stijgende waarde worden bevolen. Bijvoorbeeld:

* `1|/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Er is een bronzen badge om 1 punt te verdienen.

* `60|/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

   * Een zilveren badge wordt toegekend wanneer 60 punten zijn opgebouwd.

* `80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

   * Een gouden badge wordt afgelegd wanneer 80 punten zijn verzameld.

De regels van de Badging zijn gepareerd met het scoring regels, die bepalen hoe de punten zich ophopen. Zie de sectie [Regels toepassen op inhoud](#apply-rules-to-content).

Het `scoringRules` bezit op een merkingsregel beperkt eenvoudig welke het schrapen regels met die bepaalde merkingsregel kunnen worden in paren gebracht.

>[!NOTE]
>
>Beste praktijken: maak badge-afbeeldingen die uniek zijn voor elke AEM site.

![badging-regel-configuratie](assets/badging-rule-configuration.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Type</th>
   <th>Waarde Beschrijving</th>
  </tr>
  <tr>
   <td>drempelwaarden</td>
   <td>Tekenreeks</td>
   <td><em>(vereist)</em> Een tekenreeks met meerdere waarden in de notatie 'number|path'
    <ul>
     <li>number = score</li>
     <li>| = de verticale lijn (U+007C)</li>
     <li>path = full path to badge image resource</li>
    </ul> De tekenreeksen moeten worden geordend, zodat de getallen in waarde toenemen en er geen lege ruimte tussen het getal en het pad wordt weergegeven.<br /> Voorbeeld:<br /> <code>80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png</code></td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>Tekenreeks</td>
   <td><em>(optioneel)</em> Hiermee wordt de scoring-engine aangeduid als "basic" of "advanced". Zie <a href="/help/communities/advanced.md">Geavanceerde scores en Badges</a> als u de geavanceerde scoring-engine wilt gebruiken. De standaardwaarde is "basic".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>Tekenreeks</td>
   <td>(<em>optioneel</em>) Een tekenreeks met meerdere waarden waarmee de merkingsregel wordt beperkt tot het scoren van gebeurtenissen die door de scoreregels worden geïdentificeerd</td>
  </tr>
 </tbody>
</table>

### Inclusief Badgingregels {#included-badging-rules}

In de release zijn twee Badging Rules opgenomen die overeenkomen met de [Forums and Comments Scoring Rules](#includedscoringrules).

* `/libs/settings/community/badging/rules/comments-badging`

* `/libs/settings/community/badging/rules/forums-badging`

**Opmerkingen:**

* `rules` knooppunten zijn van het type cq:Page.
* `rules` moet zich bevinden op een locatie in de opslagplaats met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste Badgingregels {#activating-custom-badging-rules} activeren

Wijzigingen of toevoegingen aan badgingregels of afbeeldingen die in de ontwerpomgeving zijn aangebracht, moeten bij publicatie worden geïnstalleerd.

## Badges toewijzen en intrekken {#assign-and-revoke-badges}

Badges kunnen aan leden worden toegewezen met behulp van de [ledenconsole](/help/communities/members.md#badges-tab) of via programmacode met behulp van cURL-opdrachten.

De volgende cURL-opdrachten tonen wat nodig is voor een HTTP-aanvraag voor het toewijzen en intrekken van badges. De basisindeling is:

cURL -i -X POST -H *header* -u *signin* -F *operation* -F *badge* *member-profile-url*

*header* = &quot;Accept:application/json&quot;, aangepaste header die wordt doorgegeven aan de server (vereist)

*sign* = administrator-id:password bijvoorbeeld: admin:admin

*operation* = &quot;:operation=social:assignBadge&quot; OF &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath=*badge-image-file*&quot;

*badge-image-file* = de locatie van het afbeeldingsbestand met de badge in de opslagplaats, bijvoorbeeld: /libs/settings/community/badging/images/moderator/jcr:content/moderator.png

*member-profile-url* = het eindpunt voor het profiel van het lid bij publiceren bijvoorbeeld: https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>De *member-profile-url*:
>
>* Kan naar een auteurinstantie verwijzen als [de Dienst van de Tunnel ](/help/communities/users.md#tunnel-service) wordt toegelaten.
>* Kan een duistere, willekeurige naam zijn - zie [Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) betreffende machtigbare id.


### Voorbeelden: {#examples}

#### Een moderatorbadge {#assign-a-moderator-badge} toewijzen

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### Een toegewezen zilversymbool {#revoke-an-assigned-silver-badge} intrekken

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

De instantie SocialEvent van een component registreert de gebeurtenissen als `actions` die voor `topic` voorkomen. De SocialEvent bevat een methode om een `verb` te retourneren die aan de handeling is gekoppeld. Er is een *n-1* verhouding tussen `actions` en `verbs`.

Voor de geleverde communitycomponenten, beschrijven de volgende tabellen `verbs` bepaald voor elke `topic` beschikbaar voor gebruik in [scoring subrules](#scoring-sub-rules).

>[!NOTE]
>
>Een nieuwe booleaanse eigenschap, `allowBadges`, schakelt de weergave van badges voor een componentinstantie in of uit. Het zal configureerbaar in bijgewerkte [component geven dialoogvensters](/help/communities/author-communities.md) door een checkbox geëtiketteerd **de Badges van de Vertoning** zijn.

**[Agenda](/help/communities/calendar.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/agenda

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een agendagebeurtenis |
| TOEVOEGEN | opmerkingen van leden over een agendagebeurtenis |
| BIJWERKEN | agendagebeurtenis of commentaar van lid wordt bewerkt |
| DELETE | agendagebeurtenis of commentaar van lid wordt verwijderd |

**[Opmerkingen](/help/communities/comments.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een opmerking |
| TOEVOEGEN | reactie van lid op opmerking |
| BIJWERKEN | commentaar van lid is bewerkt |
| DELETE | commentaar van lid is verwijderd |

**[File Library](/help/communities/file-library.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een map |
| ATTACH | lid uploadt een bestand |
| BIJWERKEN | lid werkt een map of bestand bij |
| DELETE | lid verwijdert een map of bestand |

**[Forum](/help/communities/forum.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt forum-onderwerp |
| TOEVOEGEN | reacties van leden op forum onderwerp |
| BIJWERKEN | onderwerp of antwoord van lid wordt bewerkt |
| DELETE | forumonderwerp of antwoord van lid wordt verwijderd |

**[Journal](/help/communities/blog-feature.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/Journal

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een blogartikel |
| TOEVOEGEN | commentaar van leden op blogartikel |
| BIJWERKEN | blogartikel of commentaar van lid wordt bewerkt |
| DELETE | blogartikel of commentaar van lid is verwijderd |

**[QnA](/help/communities/working-with-qna.md)**
ComponentSocialEvent  `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een QnA-vraag |
| TOEVOEGEN | lid maakt een QnA-antwoord |
| BIJWERKEN | Vraag of antwoord van lid wordt bewerkt |
| SELECT | het antwoord van lid is geselecteerd |
| SELECTEREN OPHEFFEN | het antwoord van het lid is gedeselecteerd |
| DELETE | Vraag of antwoord van lid wordt verwijderd |

**[Reviews](/help/communities/reviews.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/review

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt beoordeling |
| BIJWERKEN | beoordeling door lid wordt bewerkt |
| DELETE | beoordeling door lid is verwijderd |

**[Classificatie](/help/communities/rating.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally/rating

| **Verb** | **Beschrijving** |
|---|---|
| WAARDERING TOEVOEGEN | de inhoud van het lid is opgegeven |
| RATING VERWIJDEREN | de inhoud van het lid is neergezet |

**[Stemmen](/help/communities/voting.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally/steming

| **Verb** | **Beschrijving** |
|---|---|
| STEMMING TOEVOEGEN | de inhoud van het lid is in stemming gebracht |
| STEMMING VERWIJDEREN | over de inhoud van het lid is gestemd |

**Moderation-enabled**
ComponentsSocialEvent  `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschrijving** |
|---|---|
| DENKEN | inhoud van lid wordt geweigerd |
| VLAG ALS ONJUIST | inhoud van lid is gemarkeerd |
| ONGESCHIKTE LAG ALS ONJUIST | inhoud van lid is ongemarkeerd |
| ACCEPTEREN | de inhoud van het lid wordt goedgekeurd door moderator |
| SLUITEN | lid sluit commentaar op bewerkingen en reacties |
| OPENEN | opmerking opnieuw openen lid |

### Aangepaste componentgebeurtenissen {#custom-component-events}

Voor een douanecomponent, wordt een SocialEvent geconcretiseerd om de gebeurtenissen van de component als `actions` te registreren die voor `topic` voorkomen.

Ter ondersteuning van scoring moet de SocialEvent de methode `getVerb()` overschrijven, zodat de juiste `verb` voor elke `action` wordt geretourneerd. De `verb` die voor een handeling wordt geretourneerd, kan een handeling zijn die veel wordt gebruikt (zoals `POST`) of een instructie die is gespecialiseerd voor de component (zoals `ADD RATING`). Er is een *n-1* verhouding tussen `actions` en `verbs`.

## Problemen oplossen {#troubleshooting}

### Badges worden niet weergegeven {#badges-are-not-appearing}

Als op de inhoud van de website wel scoring- en badingregels zijn toegepast, maar er geen badges worden gereserveerd voor enige activiteit, moet u ervoor zorgen dat badges zijn ingeschakeld voor de instantie van die component.

Zie [Badges inschakelen voor component](#enable-badges-for-component).

### Scoreregel heeft geen effect {#scoring-rule-has-no-effect}

Als op de inhoud van de website scoring- en badingregels zijn toegepast en badges worden toegekend voor bepaalde acties, maar niet voor andere, controleert u of de regel voor badging de scoringregels waarop deze van toepassing is, niet heeft beperkt.

Zie de `scoringRules` eigenschap van [Badging Rules](#badging-rules).

### Hoofdlettergevoelig type {#case-sensitive-typo}

De meeste eigenschappen en waarden, met name de werkwoorden, zijn hoofdlettergevoelig. Bij gebruik in een scoringsubregel moeten de hoekpunten allemaal HOOFDLETTERS zijn.

Als de functie niet naar behoren werkt, controleert u of de gegevens correct zijn ingevoerd.

## Snelle test {#quick-test}

Het is mogelijk om snel scoring en badging te proberen met behulp van de [Aan de slag-zelfstudie](/help/communities/getting-started.md) (engageren) site:

* Toegang tot CRXDE Lite bij auteur.
* Blader naar de basispagina:

   * /content/sites/engc/nl/jcr:content

* Voeg de eigenschap badgingRules toe:

   * **Naam**:  `badgingRules`
   * **Type**:  `String`
   * Selecteer **Multi**
   * Selecteer **Toevoegen**
   * `/libs/settings/community/badging/rules/forums-badging` invoeren
   * Selecteer **+**
   * `/libs/settings/community/badging/rules/comments-badging` invoeren
   * Selecteer **OK**

* Voeg de eigenschap scoringRules toe:

   * **Naam**:  `scoringRules`
   * **Type**:  `String`
   * Selecteer **Multi**
   * Selecteer **Toevoegen**
   * `/libs/settings/community/scoring/rules/forums-scoring` invoeren
   * Selecteer **+**
   * `/libs/settings/community/scoring/rules/comments-scoring` invoeren
   * Selecteer **OK**

* Selecteer **Alles opslaan**.

![testhandtekenmerken](assets/test-scoring-badging.png)

Zorg er daarna voor dat de forum- en commentaarcomponenten het weergeven van badges toestaan:

* Opnieuw met CRXDE Lite.
* Bladeren naar de forumcomponent

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Voeg de Booleaanse eigenschap allowBadges toe, indien nodig, en zorg ervoor dat dit waar is.

   * **Naam**:  `allowBadges`
   * **Type**:  `Boolean`
   * **Waarde**:  `true`

![test-forum-component](assets/test-forum-component.png)

Vervolgens kunt u [de communitysite opnieuw publiceren](/help/communities/sites-console.md#publishing-the-site).

Tot slot:

* Blader naar de component in de publicatie-instantie.
* Aanmelden als lid van de gemeenschap (bijvoorbeeld: weston.mccall@dodgit.com/password).
* Plaats een nieuw forumonderwerp.
* De badge wordt alleen weergegeven als de pagina is vernieuwd.

   * Afmelden en aanmelden als een ander lid van de gemeenschap (bijvoorbeeld: aaron.mcdonald@mailinator.com/password).

* Selecteer het Forum.

Dit zou het lid van de gemeenschap een bronzen badge moeten verdienen die met hun forumpost zichtbaar is omdat de eerste drempel van de forums-badging regel een score van 1 is.

![bronzebadge](assets/bronzebadge.png)

## Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Scoring and Badges Essentials](/help/communities/configure-scoring.md) voor ontwikkelaars.

Zie [Geavanceerde scores en Badges](/help/communities/advanced.md) voor informatie over de geavanceerde scoring-engine.

Het configureerbare Leaderboard [component](/help/communities/enabling-leaderboard.md) en [function](/help/communities/functions.md#leaderboard-function) vereenvoudigt de weergave van leden en hun scores op een communitysite.
