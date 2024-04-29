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

* [Badges toewijzen](#assign-and-revoke-badges) de rol van een lid in de gemeenschap te bepalen .

* [Basistoekenning van badges](#enable-scoring) aan de leden om hun deelname aan te moedigen (hoeveelheid geschapen inhoud).

* [Geavanceerde toekenning van badges](/help/communities/advanced.md) leden te identificeren als deskundigen (kwaliteit van de inhoud die is gemaakt).

**Opmerking** de toekenning van badges [standaard niet ingeschakeld](/help/communities/implementing-scoring.md#main-pars-text-237875536).

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

De Gemeenschappen [Badges console](/help/communities/badges.md) Hiermee kunt u aangepaste badges toevoegen die voor een lid kunnen worden weergegeven wanneer het lid wordt verdiend (toegekend) of wanneer het een specifieke rol in de community (toegewezen) op zich neemt.

### Toegewezen badges {#assigned-badges}

Op rollen gebaseerde badges worden door een beheerder toegewezen aan leden van de community op basis van hun rol in de community.

Toegewezen (en gegunde) badges worden opgeslagen in de geselecteerde [SRP](/help/communities/srp.md) en niet rechtstreeks toegankelijk zijn. Totdat een GUI beschikbaar is, is het enige middel om op rol-gebaseerde badges toe te wijzen dit met code of cURL. Zie de sectie over cURL-instructies [Badges toewijzen en intrekken](#assign-and-revoke-badges).

In de release zijn drie badges op basis van rollen opgenomen:

* **moderator**
  `/libs/settings/community/badging/images/moderator/jcr:content/moderator.png`

* **groepsbeheerder**
  `/libs/settings/community/badging/images/group-manager/jcr:content/group-manager.png`

* **bevoorrecht lid**
  `/libs/settings/community/badging/images/privileged-member/jcr:content/privileged-member.png`

  ![toegewezen badges](assets/assigned-badges.png)

### Toegewezen badges {#awarded-badges}

Op basis van beloningen ontvangen de leden van de gemeenschap een toegangspasje met een score op basis van regels die gelden voor hun activiteiten in de gemeenschap.

Om badges als beloning voor activiteit te laten verschijnen, moeten er twee dingen gebeuren:

* Badging moet [enabled](#enableforcomponent) voor de component feature.
* Scorebord en badgregels moeten [toegepast](#applytopage) op de pagina (of voorouder) waarop de component is geplaatst.

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
>Toegewezen badges kunnen op dezelfde wijze worden ingetrokken als toegewezen badges. Zie de [Badges toewijzen en intrekken](#assign-and-revoke-badges) sectie. De toekomstige verbeteringen zullen een UI omvatten om de badges van leden te beheren.

### Aangepaste badges {#custom-badges}

Aangepaste badges kunnen worden geïnstalleerd met de [Badges console](/help/communities/badges.md) en toegewezen of opgegeven in badgingregels.

Wanneer deze vanaf de Badges-console zijn geïnstalleerd, worden aangepaste badges automatisch naar de publicatieomgeving gerepliceerd.

## Muziek inschakelen {#enable-scoring}

Scores is niet standaard ingeschakeld. De basisstappen voor het opzetten en mogelijk maken van scoring en toekenning van badges zijn:

* Regels identificeren voor het verdienen van punten ([scèneregels](#scoring-rules)).
* Voor punten die per scoreregels worden geaccumuleerd, wijst u [badges](#badges) ([spelregels](#badging-rules)).

* [De regels voor scoring en badges toepassen op een gemeenschapssite](#apply-rules-to-content).
* [Naamgeving voor community-functies inschakelen](#enable-badges-for-component).

Zie de [Snel testen](#quick-test) om het scoren voor een communautaire site mogelijk te maken met de standaardregels voor scoring en badging voor forums en opmerkingen.

### Regels toepassen op inhoud {#apply-rules-to-content}

Voeg de eigenschappen toe om scoring en badges in te schakelen `scoringRules` en `badgingRules` naar een knooppunt in de inhoudsstructuur voor de site.

Als de site al is gepubliceerd, publiceert u de site opnieuw nadat u alle regels hebt toegepast en componenten hebt ingeschakeld.

De regels die op een badging-toegelaten component van toepassing zijn zijn die voor de huidige knoop of zijn voorvader.

Als het knooppunt van het type is `cq:Page` (aanbevolen), dan met CRXDE|Lite de eigenschappen aan zijn toevoegen `jcr:content` knooppunt.

| **Eigenschap** | **Type** | **Beschrijving** |
|---|---|---|
| badgingRules | String | een arraylijst met [spelregels](#badging-rules) |
| scoringRules | String | een arraylijst met [scèneregels](#scoring-rules) |

>[!NOTE]
>
>Als een het scoren regel geen effect op het verlenen van badges lijkt te hebben, zorg ervoor de het scoren regel niet door het scoringRules bezit van de merkingsregel is geblokkeerd. Zie de sectie met de titel [Badgingregels](#badging-rules).

### Badges voor component inschakelen {#enable-badges-for-component}

De regels voor inschalen en insluiten zijn alleen van toepassing op instanties van componenten die intekenen hebben ingeschakeld door de componentconfiguratie te bewerken in [ontwerpmodus](/help/communities/author-communities.md).

Een Booleaanse eigenschap, `allowBadges`schakelt u de weergave van badges voor een componentinstantie in of uit. Het is configureerbaar in [dialoogvenster voor bewerken van componenten](/help/communities/author-communities.md) voor forum, QnA, en commentaarcomponenten door een checkbox geëtiketteerd **Badges weergeven**.

#### Voorbeeld: allowBadges voor instantie van de component Forum {#example-allowbadges-for-forum-component-instance}

![enable-badges-component](assets/enable-badges-component.png)

>[!NOTE]
>
>Elke component kan worden bedekt om badges weer te geven met behulp van de GB-code in forums, QnA en opmerkingen als voorbeeld.

## Scoreregels {#scoring-rules}

Scoreregels vormen de basis voor scoring bij het toekennen van badges.

Elke scoreregel is een lijst met een of meer subregels. Scoreregels worden toegepast op de inhoud van de communautaire plaats om de regels te identificeren om toe te passen wanneer de badges worden toegelaten.

Scoreregels worden overgeërfd, maar niet additief. Bijvoorbeeld:

* Als page2 het scoren regel2 bevat en zijn voorouder page1 het scoren regel1 bevat.
* Een actie op een page2 component roept zowel rule1 als rule2 aan.
* Als beide regels toepasselijke subregels bevatten voor hetzelfde `topic/verb`:

   * Alleen de subregel van rule2 beïnvloedt de score.
   * De scores van beide subregels worden niet toegevoegd.

Wanneer er meer dan één scoreregel is, worden de scores afzonderlijk gehandhaafd voor elke regel.

Scoreregels zijn knooppunten van het type `cq:Page` met eigenschappen `jcr:content` knooppunt dat de lijst met subregels opgeeft die deze definiëren.

Scores worden opgeslagen in SRP.

>[!NOTE]
>
>Beste praktijken: uniek noem elke het noteren regel.
>
>Namen van scores voor regels moeten globaal uniek zijn; ze mogen niet eindigen met dezelfde naam.
>
>Een voorbeeld van wat *niet* om te doen:
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

De naam van de subregel volgt doorgaans het patroon van het gebruik van een *onderwerp*, *object*, en *werkwoord*. Bijvoorbeeld:

* member-comment-create
* lid-ondervraagden

Subregels zijn knooppunten van het type `cq:Page` met eigenschappen `jcr:content`knooppunt dat de [werkwoorden en onderwerpen](#topics-and-verbs) .

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
     <li>een lijst met in de release ondersteunde werkwoorden vindt u in de <a href="#topics-and-verbs">Onderwerpen en werven</a> sectie</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>topics</code></td>
   <td>String</td>
   <td>
    <ul>
     <li>facultatief; beperkt onderregel tot communautaire componenten die door gebeurtenisonderwerpen worden geïdentificeerd</li>
     <li>if specified : value is multi-value string of event topics</li>
     <li>een lijst met onderwerpen in de release staat in de <a href="#topics-and-verbs">Onderwerpen en werven</a> sectie</li>
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
       <li>vereist een <a href="/help/communities/advanced.md">extra pakket</a></li>
      </ul> </li>
     <li>default is "basic"</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Inclusief rangtelregels en subregels {#included-scoring-rules-and-sub-rules}

In de release zijn twee scoreregels opgenomen voor de [Functie van forum](/help/communities/functions.md#forum-function) (elk voor de onderdelen Forum en Opmerkingen van het Forum):

1. /libs/settings/community/scoring/rules/comments-scoring

   * subRules[] = /libs/settings/community/scoring/rules/sub-rules/member-comment-create/libs/settings/community/scoring/rules/sub-rules/member-receive-say/libs/settings/community/scoring/rules/sub-rules/sub-rules/member-giving-stemen/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

1. /libs/settings/community/scoring/rules/forums-scoring

   * subRules[] = /libs/settings/community/scoring/rules/sub-rules/member-forum-create/libs/settings/community/scoring/rules/sub-rules/member-receive-say/libs/settings/community/scoring/rules/sub-rules/sub-rules/member-giving-stemen/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

**Opmerkingen:**

* Beide `rules` en `sub-rules` knooppunten zijn van het type cq:Page.

* `subRules` is een kenmerk van het type String[] over de regels `jcr:content` knooppunt.

* `sub-rules` kunnen worden gedeeld door verschillende scoreregels.
* `rules` moet zich op een opslagplaats bevinden met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste sorteerregels activeren {#activating-custom-scoring-rules}

Wijzigingen of toevoegingen aan de in de ontwerpomgeving aangebrachte scoreregels of subregels moeten bij publicatie worden geïnstalleerd.

## Badgingregels {#badging-rules}

De regels van de Badging koppelen het scoring regels aan badges door te specificeren:

* Scoreregel
* Score nodig om een specifieke badge te krijgen

Badgingregels zijn knooppunten van het type `cq:Page` met eigenschappen `jcr:content` knooppunt dat de correlatie heeft tussen de scoreregels en scores en badges.

De regels voor het aanbrengen van een kenteken bestaan uit een verplicht `thresholds` eigenschap die een geordende lijst is met scores die aan badges zijn toegewezen. De scores moeten in stijgende waarde worden bevolen. Bijvoorbeeld:

* `1|/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Een bronzen badge wordt toegekend om één punt te verdienen.

* `60|/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

   * Een zilveren badge wordt toegekend wanneer 60 punten zijn opgebouwd.

* `80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

   * Een gouden badge wordt toegekend wanneer 80 punten zijn verzameld.

De regels van de Badging zijn gepareerd met het scoring regels, die bepalen hoe de punten zich ophopen. Zie de sectie met de titel [Regels toepassen op inhoud](#apply-rules-to-content).

De `scoringRules` het bezit op een merkingsregel beperkt eenvoudig welke het schatten regels met die bepaalde merkingsregel kunnen worden geparineerd.

>[!NOTE]
>
>Tips en trucs: maak badge-afbeeldingen die uniek zijn voor elke AEM.

![badging-regel-configuratie](assets/badging-rule-configuration.png)

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
   <td><em>(vereist)</em> Een tekenreeks met meerdere waarden van het formulier 'number|path'
    <ul>
     <li>number = score</li>
     <li>| = het verticale lijnteken (U+007C)</li>
     <li>path = full path to badge image resource</li>
    </ul> De tekenreeksen moeten worden geordend, zodat de getallen in waarde toenemen en er geen lege ruimte tussen het getal en het pad wordt weergegeven.<br /> Voorbeeld:<br /> <code>80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png</code></td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>String</td>
   <td><em>(optioneel)</em> Hiermee wordt de scoring-engine aangeduid als "basic" of "advanced". Als de geavanceerde scoring-engine gewenst is, raadpleegt u <a href="/help/communities/advanced.md">Geavanceerde scores en Badges</a>. De standaardwaarde is "basic".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>String</td>
   <td>(<em>optioneel</em>) Een tekenreeks met meerdere waarden waarmee de merkingsregel wordt beperkt tot het scoren van gebeurtenissen die worden bepaald door de scoreregels</td>
  </tr>
 </tbody>
</table>

### Ingesloten Badgingregels {#included-badging-rules}

In de release zijn twee Badging Rules opgenomen die overeenkomen met de [Scoreregels voor forums en opmerkingen](#includedscoringrules).

* `/libs/settings/community/badging/rules/comments-badging`

* `/libs/settings/community/badging/rules/forums-badging`

**Opmerkingen:**

* `rules` knooppunten zijn van het type cq:Page.
* `rules` moet zich op een opslagplaats bevinden met leesmachtigingen voor iedereen.

   * Regelnamen moeten uniek zijn, ongeacht de locatie.

### Aangepaste Badgingregels activeren {#activating-custom-badging-rules}

Wijzigingen of toevoegingen aan badgingregels of afbeeldingen die in de ontwerpomgeving zijn aangebracht, moeten bij publicatie worden geïnstalleerd.

## Badges toewijzen en intrekken {#assign-and-revoke-badges}

De badges kunnen aan de leden worden toegewezen met behulp van de [ledenconsole](/help/communities/members.md#badges-tab) of programmatisch met cURL-opdrachten.

De volgende cURL-opdrachten tonen wat nodig is voor een HTTP-aanvraag voor het toewijzen en intrekken van badges. De basisindeling is:

cURL -i -X POST -H *header* -u *handtekening* -F *bewerking* -F *badge* *member-profile-url*

*header* = &quot;Accept:application/json&quot;, aangepaste header die wordt doorgegeven aan de server (vereist)

*handtekening* = beheerder-id:wachtwoord, bijvoorbeeld admin:admin

*bewerking* = &quot;:operation=social:assignBadge&quot; OF &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath=*badge-image-file*&quot;

*badge-image-file* = de locatie van het bestand met de badge-afbeelding in de opslagplaats, bijvoorbeeld /libs/settings/community/badging/images/moderator/jcr:content/moderator.png

*member-profile-url* = het eindpunt voor het profiel van het lid op publiceren bijvoorbeeld, https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>De *member-profile-url*:
>
>* Kan verwijzen naar een instantie van de auteur als de [Tunnelservice](/help/communities/users.md#tunnel-service) is ingeschakeld.
>* Kan een duistere, willekeurige naam zijn - zie [Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) met betrekking tot toegestane id.

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

De instantie SocialEvent van een component registreert de gebeurtenissen als `actions` die voor een `topic`. De SocialEvent bevat een methode om een `verb` aan de handeling is gekoppeld. Er is een *n-1* relatie tussen `actions` en `verbs`.

Voor de geleverde community-componenten worden in de volgende tabellen de volgende `verbs` gedefinieerd voor elk `topic` beschikbaar in [scores instellen](#scoring-sub-rules).

>[!NOTE]
>
>Een nieuwe booleaanse eigenschap, `allowBadges`schakelt u de weergave van badges voor een componentinstantie in of uit. Het is configureerbaar in bijgewerkt [dialoogvensters voor bewerken van componenten](/help/communities/author-communities.md) via een selectievakje met label **Badges weergeven**.

**[Kalendercomponent](/help/communities/calendar.md)**
SocialEvent `topic`= com/adobe/cq/social/agenda

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een kalendergebeurtenis |
| ADD | opmerkingen van leden over een agendagebeurtenis |
| BIJWERKEN | agendagebeurtenis of commentaar van lid wordt bewerkt |
| DELETE | agendagebeurtenis of commentaar van lid wordt verwijderd |

**[Component Opmerkingen](/help/communities/comments.md)**
SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een opmerking |
| ADD | reactie van lid op opmerking |
| BIJWERKEN | commentaar van lid is bewerkt |
| DELETE | commentaar van lid is verwijderd |

**[Bestandsbibliotheekcomponent](/help/communities/file-library.md)**
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een map |
| ATTACH | lid uploadt een bestand |
| BIJWERKEN | lid werkt een map of bestand bij |
| DELETE | lid verwijdert een map of bestand |

**[Forum-component](/help/communities/forum.md)**
SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt forum-onderwerp |
| ADD | reacties van leden op forum onderwerp |
| BIJWERKEN | onderwerp of antwoord van lid van forum wordt bewerkt |
| DELETE | forumonderwerp of antwoord van lid wordt verwijderd |

**[Journal-component](/help/communities/blog-feature.md)**
SocialEvent `topic`= com/adobe/cq/social/journaal

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een blogartikel |
| ADD | commentaar van leden op blogartikel |
| BIJWERKEN | blogartikel of commentaar van lid wordt bewerkt |
| DELETE | blogartikel of commentaar van lid is verwijderd |

**[QnA-component](/help/communities/working-with-qna.md)**
SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt een QnA-vraag |
| ADD | lid maakt een antwoord op vraag |
| BIJWERKEN | Vraag of antwoord van lid wordt bewerkt |
| SELECT | het antwoord van lid is geselecteerd |
| SELECTEREN OPHEFFEN | het antwoord van het lid is gedeselecteerd |
| DELETE | Vraag of antwoord van lid wordt verwijderd |

**[Component Reviews](/help/communities/reviews.md)**
SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschrijving** |
|---|---|
| POST | lid maakt beoordeling |
| BIJWERKEN | beoordeling door lid wordt bewerkt |
| DELETE | beoordeling door lid is verwijderd |

**[Beoordelingscomponent](/help/communities/rating.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/rating

| **Verb** | **Beschrijving** |
|---|---|
| WAARDERING TOEVOEGEN | de inhoud van het lid is opgegeven |
| RATING VERWIJDEREN | de inhoud van het lid is neergezet |

**[Stemcomponent](/help/communities/voting.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/stemgerechtigd

| **Verb** | **Beschrijving** |
|---|---|
| STEMMING TOEVOEGEN | de inhoud van het lid is in stemming gebracht |
| STEMMING VERWIJDEREN | over de inhoud van het lid is gestemd |

**Componenten met moderatie**
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

Voor een aangepaste component wordt een SocialEvent geïnstantieerd om de gebeurtenissen van de component op te nemen als `actions` die voor een `topic`.

Voor ondersteuning van scoring moet de methode SocialEvent worden overschreven `getVerb()` zodat `verb` is geretourneerd voor elk `action`. De `verb` De geretourneerde waarde voor een handeling kan een veelgebruikte handeling zijn (zoals `POST`) of een voor de component gespecialiseerde instantie (zoals `ADD RATING`). Er is een *n-1* relatie tussen `actions` en `verbs`.

## Problemen oplossen {#troubleshooting}

### Badges worden niet weergegeven {#badges-are-not-appearing}

Als op de inhoud van de website wel scoring- en badgingregels zijn toegepast, maar er geen badges worden toegekend voor activiteiten, moet u ervoor zorgen dat badges zijn ingeschakeld voor de instantie van die component.

Zie [Badges voor component inschakelen](#enable-badges-for-component).

### Scoreregel heeft geen effect {#scoring-rule-has-no-effect}

Als op de inhoud van de website scoring- en badingregels zijn toegepast en badges worden toegekend voor bepaalde acties, maar niet voor andere, controleert u of de regel voor badging de scoringregels waarop deze van toepassing is, niet heeft beperkt.

Zie de `scoringRules` eigenschap van [Badgingregels](#badging-rules).

### Hoofdlettergevoelig (typ) {#case-sensitive-typo}

De meeste eigenschappen en waarden, met name de werkwoorden, zijn hoofdlettergevoelig. Bij gebruik in een scoringsubregel moeten de hoekpunten allemaal HOOFDLETTERS zijn.

Als de functie niet naar behoren werkt, controleert u of de gegevens correct zijn ingevoerd.

## Snel testen {#quick-test}

Het is mogelijk om snel scoring en badge te proberen met de [Zelfstudie Aan de slag](/help/communities/getting-started.md) site :

* Toegang tot CRXDE Lite bij auteur.
* Blader naar de basispagina:

   * /content/sites/engc/nl/jcr:content

* Voeg de eigenschap badgingRules toe:

   * **Naam**: `badgingRules`
   * **Type**: `String`
   * Selecteren **Multi**
   * Selecteren **Toevoegen**
   * Enter `/libs/settings/community/badging/rules/forums-badging`
   * Selecteren **+**
   * Enter `/libs/settings/community/badging/rules/comments-badging`
   * Selecteren **OK**

* Voeg de eigenschap scoringRules toe:

   * **Naam**: `scoringRules`
   * **Type**: `String`
   * Selecteren **Multi**
   * Selecteren **Toevoegen**
   * Enter `/libs/settings/community/scoring/rules/forums-scoring`
   * Selecteren **+**
   * Enter `/libs/settings/community/scoring/rules/comments-scoring`
   * Selecteren **OK**

* Selecteren **Alles opslaan**.

![testhandtekenmerken](assets/test-scoring-badging.png)

Zorg er daarna voor dat de forum- en commentaarcomponenten het weergeven van badges toestaan:

* Opnieuw met gebruik van CRXDE Lite.
* Bladeren naar de forumcomponent

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Voeg de Booleaanse eigenschap allowBadges toe, indien nodig, en zorg ervoor dat dit waar is.

   * **Naam**: `allowBadges`
   * **Type**: `Boolean`
   * **Waarde**: `true`

![test-forum-component](assets/test-forum-component.png)

Volgende, [herpubliceren](/help/communities/sites-console.md#publishing-the-site) de site van de gemeenschap.

Tot slot:

* Blader naar de component in de publicatie-instantie.
* Meld u aan als lid van de gemeenschap (bijvoorbeeld weston.mccall@dodgit.com / wachtwoord).
* Plaats een nieuw forumonderwerp.
* De badge wordt alleen weergegeven als de pagina is vernieuwd.

   * Meld u af en meld u aan als een ander lid van de gemeenschap (bijvoorbeeld: aaron.mcdonald@mailinator.com/password).

* Selecteer het Forum.

Dit zou het lid van de gemeenschap een bronzen badge moeten verdienen die met hun forumpost zichtbaar is omdat de eerste drempel van de forums-badging regel een score van 1 is.

![bronzebadge](assets/bronzebadge.png)

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Scores en Badges Essentials](/help/communities/configure-scoring.md) pagina voor ontwikkelaars.

Zie voor informatie over de geavanceerde scoring-engine [Geavanceerde scores en Badges](/help/communities/advanced.md).

Het configureerbare Leaderboard [component](/help/communities/enabling-leaderboard.md) en [function](/help/communities/functions.md#leaderboard-function) vereenvoudigt de weergave van leden en hun scores op een community-site.
