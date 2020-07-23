---
title: Scores en badges van gemeenschappen
seo-title: Scores en badges van gemeenschappen
description: Met scoring en badges in AEM Communities kunt u leden van de gebruikersgemeenschap identificeren en belonen
seo-description: Met scoring en badges in AEM Communities kunt u leden van de gebruikersgemeenschap identificeren en belonen
uuid: d73683df-a413-4b3c-869c-67568bfdfcf6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ea033bb9-cb92-4c93-855f-8c902999378c
docset: aem65
tagskeywords: scoring, badging, badges, gamification
translation-type: tm+mt
source-git-commit: a76707e16aa7054078bcfffe43476e4bd83d83e3
workflow-type: tm+mt
source-wordcount: '2897'
ht-degree: 1%

---


# Scores en badges van gemeenschappen {#communities-scoring-and-badges}

## Overzicht {#overview}

De functie AEM Communities scoren en badges biedt de mogelijkheid om leden van de gemeenschap te identificeren en te belonen.

De belangrijkste aspecten van scoring en badges zijn:

* [Wijs badges](#assign-and-revoke-badges) toe om de rol van een lid in de gemeenschap te identificeren.

* [Basistoekenning van toegangspasjes](#enable-scoring) aan de leden om hun deelname aan te moedigen (hoeveelheid geschapen inhoud).
* [Geavanceerde toekenning van badges](/help/communities/advanced.md) om leden te identificeren als experts (kwaliteit van de inhoud die is gemaakt).

**Let** op: het toewijzen van badges is [niet standaard](/help/communities/implementing-scoring.md#main-pars-text-237875536)ingeschakeld.

>[!CAUTION]
>
>De implementatiestructuur die zichtbaar is in CRXDE Lite kan worden gewijzigd zodra de interface beschikbaar is.


## Badges {#badges}

De badges worden onder de naam van een lid geplaatst om hun rol of hun status in de gemeenschap aan te geven. Badges kunnen als een afbeelding of als een naam worden weergegeven. Wanneer de naam als afbeelding wordt weergegeven, wordt deze opgenomen als alternatieve tekst voor toegankelijkheid.

Standaard bevinden badges zich in de dataopslag op

* `/libs/settings/community/badging/images`

Als ze op een andere locatie zijn opgeslagen, moeten ze door iedereen toegankelijk worden gelezen.

De badges zijn in de UGC verschillend wat betreft de vraag of zij volgens de regels werden toegewezen of verdiend. Momenteel worden toegewezen badges weergegeven als tekst en worden verdiende badges als een afbeelding weergegeven.

### Bandenbeheer-interface {#badge-management-ui}

De console [van de](/help/communities/badges.md) Badges van de Gemeenschappen biedt de capaciteit om douanebadges toe te voegen die voor een lid kunnen worden getoond wanneer verdiend (toegekend) of wanneer zij een specifieke rol in de gemeenschap (toegewezen) nemen.

### Toegewezen badges {#assigned-badges}

Op rollen gebaseerde badges worden door een beheerder toegewezen aan leden van de community op basis van hun rol in de community.

Toegewezen (en geawade) badges worden opgeslagen in geselecteerde [SRP](/help/communities/srp.md) en zijn niet direct toegankelijk. Totdat een GUI beschikbaar is, is het enige middel om op rol-gebaseerde badges toe te wijzen dit met code of cURL. Zie de sectie [Badges](#assign-and-revoke-badges)toewijzen en intrekken voor instructies voor cURL.

In de release zijn drie badges op basis van rollen opgenomen:

* **moderator**

   `/libs/settings/community/badging/images/moderator/jcr:content/moderator.png`

* **groepsbeheerder**

   `/libs/settings/community/badging/images/group-manager/jcr:content/group-manager.png`

* **geprivilegieerd lid**

   `/libs/settings/community/badging/images/privileged-member/jcr:content/privileged-member.png`

![chlimage_1-98](assets/chlimage_1-98.png)

### Toegewezen badges {#awarded-badges}

Op basis van beloningen ontvangen de leden van de gemeenschap een toegangspasje met een score op basis van regels die gelden voor hun activiteiten in de gemeenschap.

Om badges als beloning voor activiteit te kunnen weergeven, moeten er twee dingen gebeuren:

* Badging moet voor de eigenschapcomponent worden [toegelaten](#enableforcomponent) .
* De regels voor het noteren en markeren moeten worden [toegepast](#applytopage) op de pagina (of voorouder) waarop de component is geplaatst.

De release bevat drie beloningsbadges:

* **goud**

   `/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

* **zilver**

   `/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

* **brons**

   `/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

![chlimage_1-99](assets/chlimage_1-99.png)

>[!NOTE]
>
>Scoreregels kunnen worden geconfigureerd om negatieve punten toe te wijzen voor posten die als onjuist zijn gemarkeerd en beïnvloeden zo de score. Als een badge echter eenmaal is behaald, wordt deze niet automatisch verwijderd vanwege wijzigingen in de score- of scoringregel.
>
>Toegewezen badges kunnen op dezelfde wijze worden ingetrokken als toegewezen badges. Zie de sectie Badges [toewijzen en intrekken](#assign-and-revoke-badges) . De toekomstige verbeteringen zullen een UI omvatten om de badges van leden te beheren.


### Aangepaste badges {#custom-badges}

Aangepaste badges kunnen worden geïnstalleerd met de [Badges-console](/help/communities/badges.md) en kunnen worden toegewezen aan of opgegeven in badgingregels.

Wanneer deze vanaf de Badges-console zijn geïnstalleerd, worden aangepaste badges automatisch naar de publicatieomgeving gerepliceerd.

## Muziek inschakelen {#enable-scoring}

Scores is niet standaard ingeschakeld. De basisstappen voor het opzetten en mogelijk maken van scoring en toekenning van badges zijn:

* Identificeer regels voor het verdienen van punten ([het scoren regels](#scoring-rules)).
* Wijs voor punten die volgens de scoreregels zijn geaccumuleerd [badges](#badges) ([badgingregels](#badging-rules)) toe.

* [Pas de scoring- en badingregels toe op een communitysite](#apply-rules-to-content).
* [Enable badging for community features](#enable-badges-for-component).

Zie de sectie [Snelle test](#quick-test) om het scoren voor een gemeenschapssite in te schakelen met de standaardregels voor scoring en badging voor forums en opmerkingen.

### Regels toepassen op inhoud {#apply-rules-to-content}

Als u scoring en badges wilt inschakelen, voegt u de eigenschappen `scoringRules` en `badgingRules` aan elk knooppunt in de inhoudsstructuur voor de site toe.

Als de site al is gepubliceerd nadat alle regels zijn toegepast en componenten zijn ingeschakeld, publiceert u de site opnieuw.

De regels die op een badging-toegelaten component van toepassing zijn zijn die voor de huidige knoop of zijn voorvader.

Als het knooppunt van het type `cq:Page` (aanbevolen) is, voegt u met behulp van CRXDE|Lite de eigenschappen toe aan het `jcr:content` knooppunt.

| **Eigenschap** | **Type** | **Beschrijving** |
|---|---|---|
| badgingRules | Tekenreeks[] | een lijst met [badgingregels](#badging-rules) |
| scoringRules | Tekenreeks[] | een arraylijst met [scoreregels](#scoring-rules) |

>[!NOTE]
>
>Als een het scoren regel geen effect op het verlenen van badges lijkt te hebben, zorg ervoor de het scoren regel niet door het scoringRules bezit van de merkingsregel is geblokkeerd. Zie de sectie [Badgingregels](#badging-rules).


### Badges voor component inschakelen {#enable-badges-for-component}

De het scoren en het inkleuren regels zijn in feite slechts voor instanties van componenten die merkings door de componentenconfiguratie op [auteurswijze](/help/communities/author-communities.md)uit te geven hebben toegelaten.

Een booleaanse eigenschap, `allowBadges`schakelt de weergave van badges voor een componentinstantie in of uit. Het is configureerbaar in de [component geeft dialoog](/help/communities/author-communities.md) voor forum, QnA en commentaarcomponenten door een checkbox geëtiketteerd de Badges **van de** Vertoning uit.

#### Voorbeeld: allowBadges voor de componentinstantie Forum {#example-allowbadges-for-forum-component-instance}

![chlimage_1-100](assets/chlimage_1-100.png)

>[!NOTE]
>
>Elke component kan worden bedekt om badges weer te geven met behulp van de GB-code in forums, QnA en opmerkingen als voorbeeld.


## Scoreregels {#scoring-rules}

Scoreregels vormen de basis voor scoring met het oog op het toekennen van badges.

Heel eenvoudig, is elke het scoren regel een lijst van één of meerdere sub-regels. Scoreregels worden toegepast op de inhoud van de communautaire plaats om de regels te identificeren om toe te passen wanneer de badges worden toegelaten.

Scoreregels worden overgeërfd, maar niet additief. Bijvoorbeeld:

* Als page2 het scoren regel2 bevat en zijn voorouder page1 het scoren regel1 bevat.
* Een actie op een page2 component zal zowel rule1 als rule2 aanhalen.
* Indien beide regels toepasselijke subregels bevatten voor hetzelfde `topic/verb`:

   * Alleen de subregel van regel2 heeft invloed op de score.
   * De scores uit beide subregels worden niet bij elkaar opgeteld.

Wanneer er meer dan één scoreregel is, worden de scores afzonderlijk gehandhaafd voor elke regel.

Scoringsregels zijn knooppunten van het type `cq:Page` met eigenschappen op het `jcr:content` knooppunt die de lijst met subregels opgeven die deze definiëren.

Scores worden opgeslagen in SRP.

>[!NOTE]
>
>Beste praktijken: Geef elke scoreregel een unieke naam.
>
>Namen van scoreregelregels moeten globaal uniek zijn. ze mogen niet met dezelfde naam eindigen.
>
>Een voorbeeld van wat *niet* te doen:
>/libs/settings/community/scoring/rules/site1/forums-scoring
>/libs/settings/community/scoring/rules/site2/forums-scoring


### Subregels voor score {#scoring-sub-rules}

De scoringsubregels bevatten de eigenschappen die de waarden voor deelname aan de gemeenschap in detail beschrijven.

Elke scoring-subregel identificeert:

* Welke activiteiten worden getraceerd?
* Welke specifieke communautaire functie is hierbij betrokken?
* Hoeveel punten zijn er toegekend?

Standaard worden punten toegewezen aan het lid dat de handeling uitvoert, tenzij in de subregel wordt aangegeven dat de eigenaar van de inhoud de punten ( `forOwner`) ontvangt.

Elke subregel kan in een of meer scoreregels worden opgenomen.

De naam van de subregel volgt doorgaans het patroon van het gebruik van een *onderwerp* , *object* en *werkwoord*. Bijvoorbeeld:

* member-comment-create
* lid-ondervraagden

Subregels zijn knooppunten van type `cq:Page` met eigenschappen op zijn `jcr:content`knoop die de [werkwoorden en onderwerpen](#topics-and-verbs) specificeren.

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
     <li>een lijst van werkwoorden die in de versie worden gesteund is in de <a href="#topics-and-verbs">Onderwerpen en sectie van Verbs</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>topics</code></td>
   <td>Tekenreeks[]</td>
   <td>
    <ul>
     <li>facultatief; beperkt subregel tot componenten van de gemeenschap die door gebeurtenisonderwerpen worden geïdentificeerd</li>
     <li>indien gespecificeerd: waarde is een tekenreeks met meerdere waarden voor gebeurtenisonderwerpen</li>
     <li>een lijst van onderwerpen in de versie is in de <a href="#topics-and-verbs">Onderwerpen en sectie van Verbs</a></li>
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

In de release staan twee scoreregels voor de functie [](/help/communities/functions.md#forum-function) Forum (één voor het Forum en één voor de componenten Comments van de functie Forum):

1. /libs/settings/community/scoring/rules/comments-scoring

   * subRules[] =/libs/settings/community/scoring/rules/sub-rules/member-comment-create/libs/settings/community/scoring/rules/sub-rules/member-receive-say/libs/settings/community/scoring/rules/sub-rules/sub-rules/member-giving-say/libs/settings/community/scoring/rules/sub-rules/member-is moderated

1. /libs/settings/community/scoring/rules/forums-scoring

   * subRules[] =/libs/settings/community/scoring/rules/sub-rules/member-forum-create/libs/settings/community/scoring/rules/sub-rules/member-receive-say/libs/settings/community/scoring/rules/sub-rules/sub-rules/member-giving-Kies/libs/settings/community/scoring/rules/sub-rules/member-is moderated

**Opmerkingen:**

* Zowel `rules` als `sub-rules` knooppunten zijn van het type cq:Page.

* `subRules` is een attribuut van typeString[] op de `jcr:content` knoop van de regel.

* `sub-rules` kunnen worden gedeeld door verschillende scoreregels.
* `rules` moet zich bevinden op een locatie in de opslagplaats met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste sorteerregels activeren {#activating-custom-scoring-rules}

Wijzigingen of toevoegingen aan de in de ontwerpomgeving aangebrachte scoreregels of subregels moeten bij publicatie worden geïnstalleerd.

## Badgingregels {#badging-rules}

De regels van de Badging koppelen het scoring regels aan badges door te specificeren:

* Scoreregel.
* De score is nodig om een specifieke badge te ontvangen.

De regels van de Badging zijn knopen van type `cq:Page` met eigenschappen op zijn `jcr:content` knoop die het correleren van scoreregels aan scores en badges.

De regels voor badging bestaan uit een verplichte `thresholds` eigenschap die een geordende lijst is met scores die zijn toegewezen aan badges. De scores moeten in stijgende waarde worden bevolen. Bijvoorbeeld:

* `1|/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Er is een bronzen badge om 1 punt te verdienen.

* `60|/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

   * Een zilveren badge wordt toegekend wanneer 60 punten zijn opgebouwd.

* `80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

   * Een gouden badge wordt afgelegd wanneer 80 punten zijn verzameld.

De regels van de Badging zijn gepareerd met het scoring regels, die bepalen hoe de punten zich ophopen. Zie de sectie Regels [toepassen op inhoud](#apply-rules-to-content).

Het `scoringRules` bezit op een merkingsregel beperkt eenvoudig welke het schatten regels met die bepaalde merkingsregel kunnen worden geparineerd.

>[!NOTE]
>
>Beste praktijken: maak badge-afbeeldingen die uniek zijn voor elke AEM-site.


![chlimage_1-101](assets/chlimage_1-101.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Type</th>
   <th>Waarde Beschrijving</th>
  </tr>
  <tr>
   <td>drempelwaarden</td>
   <td>Tekenreeks[]</td>
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
   <td><em>(optioneel)</em> Hiermee wordt de scoring-engine aangeduid als "basic" of "advanced". Zie <a href="/help/communities/advanced.md">Geavanceerde scores en Badges</a>als u de geavanceerde scoring-engine wilt gebruiken. De standaardwaarde is "basic".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>Tekenreeks[]</td>
   <td>(<em>optioneel</em>) Een tekenreeks met meerdere waarden waarmee de merkingsregel wordt beperkt tot het scoren van gebeurtenissen die worden bepaald door de scoreregels</td>
  </tr>
 </tbody>
</table>

### Ingesloten Badgingregels {#included-badging-rules}

In de release zijn twee Badging Rules opgenomen die overeenkomen met de [forums en de regels voor het noteren van opmerkingen](#includedscoringrules).

* /libs/settings/community/badging/rules/comments-badging

* /libs/settings/community/badging/rules/forums-badging

**Opmerkingen:**

* `rules` knooppunten zijn van het type cq:Page.
* `rules` moet zich bevinden op een locatie in de opslagplaats met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste Badgingregels activeren {#activating-custom-badging-rules}

Wijzigingen of toevoegingen aan badgingregels of afbeeldingen die in de ontwerpomgeving zijn aangebracht, moeten bij publicatie worden geïnstalleerd.

## Badges toewijzen en intrekken {#assign-and-revoke-badges}

Badges kunnen aan leden worden toegewezen met behulp van de [ledenconsole](/help/communities/members.md#badges-tab) of via programmacode met behulp van cURL-opdrachten.

De volgende cURL-opdrachten tonen wat nodig is voor een HTTP-aanvraag voor het toewijzen en intrekken van badges. De basisindeling is:

cURL -i -X POST -H *header* -u *sign* -F *operation* -F *badge* *member-profile-url*

*header* = &quot;Accept:application/json&quot;aangepaste header om door te geven aan de server (vereist)

*sign* = beheerder-id:password bijvoorbeeld: admin:admin

*operation* = &quot;:operation=social:assignBadge&quot; OF &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath=*badge-image-file*&quot;

*badge-image-file* = de locatie van het afbeeldingsbestand met de badge in de opslagruimte, bijvoorbeeld: /libs/settings/community/badging/images/moderator/jcr:content/moderator.png

*member-profile-url* = het eindpunt voor het profiel van het lid op uitgeverij bijvoorbeeld: https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>The *member-profile-url*:
>
>* Kan naar een auteurinstantie verwijzen als de Dienst [van de](/help/communities/users.md#tunnel-service) Tunnel wordt toegelaten.
>* Kan een duistere, willekeurige naam zijn - zie [Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) met betrekking tot machtigbare id.

>



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

De instantie SocialEvent van een component registreert de gebeurtenissen zoals `actions` die voor een `topic`. De SocialEvent bevat een methode om een aan de actie `verb` gekoppeld item te retourneren. Er is een *n-1* relatie tussen `actions` en `verbs`.

Voor de geleverde communitycomponenten, beschrijven de volgende lijsten `verbs` die voor elk `topic` beschikbaar voor gebruik in [het scoren subrules](#scoring-sub-rules)worden bepaald.

>[!NOTE]
>
>Een nieuwe booleaanse eigenschap, `allowBadges`schakelt de weergave van badges voor een componentinstantie in of uit. Het zal configureerbaar in bijgewerkte [component zijn uitgeeft dialoogvensters](/help/communities/author-communities.md) door een checkbox geëtiketteerd de Badges **van de** Vertoning.


**[Agenda Component](/help/communities/calendar.md)**SocialEvent`topic`= com/adobe/cq/social/agenda

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een agendagebeurtenis |
| TOEVOEGEN | opmerkingen van leden over een agendagebeurtenis |
| BIJWERKEN | agendagebeurtenis of commentaar van lid wordt bewerkt |
| DELETE | agendagebeurtenis of commentaar van lid wordt verwijderd |

**[Opmerkingen Component](/help/communities/comments.md)**SocialEvent`topic`= com/adobe/cq/social/comment

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een opmerking |
| TOEVOEGEN | reactie van lid op opmerking |
| BIJWERKEN | commentaar van lid is bewerkt |
| DELETE | commentaar van lid is verwijderd |

**[File Library Component](/help/communities/file-library.md)**SocialEvent`topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een map |
| ATTACH | lid uploadt een bestand |
| BIJWERKEN | lid werkt een map of bestand bij |
| DELETE | lid verwijdert een map of bestand |

**[Forum Component](/help/communities/forum.md)**SocialEvent`topic`= com/adobe/cq/social/forum

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt forum-onderwerp |
| TOEVOEGEN | reacties van leden op forum onderwerp |
| BIJWERKEN | onderwerp of antwoord van lid wordt bewerkt |
| DELETE | forumonderwerp of antwoord van lid wordt verwijderd |

**[Journal Component](/help/communities/blog-feature.md)**SocialEvent`topic`= com/adobe/cq/social/journaal

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een blogartikel |
| TOEVOEGEN | commentaar van leden op blogartikel |
| BIJWERKEN | blogartikel of commentaar van lid wordt bewerkt |
| DELETE | blogartikel of commentaar van lid is verwijderd |

**[QnA Component](/help/communities/working-with-qna.md)**SocialEvent`topic`= com/adobe/cq/social/qna

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een QnA-vraag |
| TOEVOEGEN | lid maakt een QnA-antwoord |
| BIJWERKEN | Vraag of antwoord van lid wordt bewerkt |
| SELECT | het antwoord van lid is geselecteerd |
| SELECTEREN OPHEFFEN | het antwoord van het lid is gedeselecteerd |
| DELETE | Vraag of antwoord van lid wordt verwijderd |

**[Reviews Component](/help/communities/reviews.md)**SocialEvent`topic`= com/adobe/cq/social/review

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt beoordeling |
| BIJWERKEN | beoordeling door lid wordt bewerkt |
| DELETE | beoordeling door lid is verwijderd |

**[Beoordelingscomponent](/help/communities/rating.md)**SocialEvent`topic`= com/adobe/cq/social/tally/rating

| **Verb** | **Beschrijving** |
|---|---|
| WAARDERING TOEVOEGEN | de inhoud van het lid is opgegeven |
| RATING VERWIJDEREN | de inhoud van het lid is neergezet |

**[Stemcomponent](/help/communities/voting.md)**SocialEvent`topic`= com/adobe/cq/social/tally/stemrecht

| **Verb** | **Beschrijving** |
|---|---|
| STEMMING TOEVOEGEN | de inhoud van het lid is in stemming gebracht |
| STEMMING VERWIJDEREN | over de inhoud van het lid is gestemd |

**Moderation-enabled Components** SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschrijving** |
|---|---|
| DENKEN | inhoud van lid wordt geweigerd |
| VLAG ALS ONJUIST | inhoud van lid is gemarkeerd |
| ONGESCHIKTE LAG ALS ONJUIST | inhoud van lid is ongemarkeerd |
| ACCEPTEREN | de inhoud van het lid wordt goedgekeurd door moderator |
| SLUITEN | lid sluit commentaar op bewerkingen en reacties |
| OPENEN | opmerking opnieuw openen lid |

### Aangepaste componentgebeurtenissen {#custom-component-events}

Voor een aangepaste component wordt een SocialEvent geïnstantieerd om de gebeurtenissen van de component op te nemen zoals `actions` die voor een `topic`.

Om het scoren te steunen, zou SocialEvent de methode moeten met voeten treden `getVerb()` zodat een aangewezen voor elk `verb` wordt teruggekeerd `action`. De `verb` geretourneerde waarde voor een handeling kan een veelgebruikte (zoals `POST`) of een speciale waarde voor de component (zoals `ADD RATING`) zijn. Er is een *n-1* relatie tussen `actions` en `verbs`.

## Problemen oplossen {#troubleshooting}

### Badges worden niet weergegeven {#badges-are-not-appearing}

Als op de inhoud van de website wel scoring- en badingregels zijn toegepast, maar er geen badges worden gereserveerd voor enige activiteit, moet u ervoor zorgen dat badges zijn ingeschakeld voor de instantie van die component.

Zie Badges [inschakelen voor component](#enable-badges-for-component).

### Scoreregel heeft geen effect {#scoring-rule-has-no-effect}

Als op de inhoud van de website scoring- en badingregels zijn toegepast en badges worden toegekend voor bepaalde acties, maar niet voor andere, controleert u of de regel voor badging de scoringregels waarop deze van toepassing is, niet heeft beperkt.

Zie de `scoringRules` eigenschap van [Badging Rules](#badging-rules).

### Hoofdlettergevoelig (typ) {#case-sensitive-typo}

De meeste eigenschappen en waarden, met name de werkwoorden, zijn hoofdlettergevoelig. Bij gebruik in een scoringsubregel moeten de hoekpunten allemaal HOOFDLETTERS zijn.

Als de functie niet naar behoren werkt, controleert u of de gegevens correct zijn ingevoerd.

## Snel testen {#quick-test}

Het is mogelijk om snel scoring en badging te proberen met behulp van de site [Getting Started Tutorial](/help/communities/getting-started.md) (engineeren):

* Toegang tot CRXDE Lite op auteur.
* Blader naar de basispagina:

   * /content/sites/engc/nl/jcr:content

* Voeg de eigenschap badgingRules toe:

   * **Naam**: `badgingRules`
   * **Type**: `String`
   * Meerdere **selecteren**
   * Selecteer **Toevoegen**
   * Enter `/libs/settings/community/badging/rules/forums-badging`
   * Selecteer **+**
   * Enter `/libs/settings/community/badging/rules/comments-badging`
   * Selecteer **OK**

* Voeg de eigenschap scoringRules toe:

   * **Naam**: `scoringRules`
   * **Type**: `String`
   * Meerdere **selecteren**
   * Selecteer **Toevoegen**
   * Enter `/libs/settings/community/scoring/rules/forums-scoring`
   * Selecteer **+**
   * Enter `/libs/settings/community/scoring/rules/comments-scoring`
   * Selecteer **OK**

* Selecteer **Alles** opslaan.

![chlimage_1-102](assets/chlimage_1-102.png)

Zorg er daarna voor dat de forum- en commentaarcomponenten het weergeven van badges toestaan:

* Opnieuw met gebruik van CRXDE Lite.
* Bladeren naar de forumcomponent

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Voeg de Booleaanse eigenschap allowBadges toe, indien nodig, en zorg ervoor dat dit waar is.

   * **Naam**: `allowBadges`
   * **Type**: `Boolean`
   * **Waarde**: `true`

![chlimage_1-103](assets/chlimage_1-103.png)

Publiceer [](/help/communities/sites-console.md#publishing-the-site) vervolgens de communitysite opnieuw.

Tot slot:

* Blader naar de component in de publicatie-instantie.
* Aanmelden als lid van de gemeenschap (bijvoorbeeld: weston.mccall@dodgit.com/password).
* Plaats een nieuw forumonderwerp.
* De badge wordt alleen weergegeven als de pagina is vernieuwd.

   * Afmelden en aanmelden als een ander lid van de gemeenschap (bijvoorbeeld: aaron.mcdonald@mailinator.com/password).

* Selecteer het Forum.

Dit zou het lid van de gemeenschap een bronzen badge moeten verdienen die met hun forumpost zichtbaar is omdat de eerste drempel van de forums-badging regel een score van 1 is.

![bronzebadge](assets/bronzebadge.png)

## Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Scoring en Badges Essentials](/help/communities/configure-scoring.md) voor ontwikkelaars.

Zie [Geavanceerde scores en Badges](/help/communities/advanced.md)voor informatie over de geavanceerde scoring-engine.

De configureerbare Leaderboard- [component](/help/communities/enabling-leaderboard.md) en - [functie](/help/communities/functions.md#leaderboard-function) vereenvoudigt de weergave van leden en hun scores op een communitysite.
