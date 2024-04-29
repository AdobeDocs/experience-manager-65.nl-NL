---
title: Geavanceerde scores en Badges
description: Leer hoe u geavanceerde scoring instelt, zodat u badges kunt toekennen om leden te identificeren als experts.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: d3bb6664-6c01-4bcf-840c-072fc491fc99
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# Geavanceerde scores en Badges{#advanced-scoring-and-badges}

## Overzicht {#overview}

Met geavanceerd scoren kunnen badges worden toegekend om leden te identificeren als experts. Bij geavanceerd zoeken worden punten toegewezen op basis van de hoeveelheid *en* kwaliteit van de inhoud die door een lid wordt gemaakt, terwijl bij elementaire scores punten worden toegewezen op basis van de hoeveelheid gemaakte inhoud.

Dit verschil is het gevolg van de scores die zijn gebruikt voor de berekening van de scores. De basisscoring-engine past eenvoudige wiskunde toe. De geavanceerde scoring-engine is een adaptief algoritme dat actieve leden belont die waardevolle en relevante inhoud leveren, afgeleid via de verwerking van natuurlijke talen (NLP) van een onderwerp.

Naast inhoudrelevantie, zijn de het scoren algoritmen rekenschap van lidactiviteiten, zoals het stemmen en percentage van antwoorden. Hoewel deze elementen in de standaardscoring kwantitatief worden opgenomen, worden ze bij geavanceerd scoren op algoritmische wijze gebruikt.

Daarom vereist de geavanceerde scoring-engine voldoende gegevens om de analyse zinvol te maken. De prestatiedrempel voor het worden van een expert wordt constant opnieuw geëvalueerd aangezien het algoritme voortdurend aan het volume en de kwaliteit van gecreeerde inhoud aanpast. Er is ook een concept *verval* van oudere posten van een lid. Indien een deskundige niet langer deelneemt aan het onderwerp waar hij of zij de status van deskundige heeft verworven, op een vooraf bepaald tijdstip (zie [configuratie van scores](#configurable-scoring-engine)) kunnen zij hun status als deskundige verliezen.

Geavanceerde scoring instellen is vrijwel hetzelfde als basisscoring:

* De basis en de geavanceerde het scoren en merkingsregels zijn [toegepast op inhoud](/help/communities/implementing-scoring.md#apply-rules-to-content) op dezelfde wijze.

   * Op dezelfde inhoud kunnen de basisregels en de geavanceerde regels voor scoring en badging worden toegepast.

* [Badges voor componenten inschakelen](/help/communities/implementing-scoring.md#enable-badges-for-component) is algemeen.

De verschillen bij het instellen van de regels voor scoring en badging zijn:

* Configureerbare geavanceerde scores-engine
* Geavanceerde regels voor scoring:

   * `scoringType` instellen op `advanced`
   * Vereisten `stopwords`

* Geavanceerde regels voor badging:

   * `badgingType` instellen op `advanced`
   * `badgingLevels` instellen op **aantal toe te kennen deskundigen**
   * Vereisten `badgingPaths` array van badges in plaats van drempelwaarden wijst array-mapping naar badges.

>[!NOTE]
>
>Als u geavanceerde mogelijkheden voor scoring en badging wilt gebruiken, installeert u de [Expert Identification-pakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq610%2Fsocial%2Ffeaturepack%2Fcq-social-expert-identification-pkg).

## Configureerbare scores-engine {#configurable-scoring-engine}

De geavanceerde het schrapen motor verstrekt een configuratie OSGi met parameters die het geavanceerde het schrapen algoritme beïnvloeden.

![geavanceerde scoring-engine](assets/advanced-scoring-engine.png)

* **Scoregewichten**

  Voor een onderwerp, specificeer het werkwoord dat de hoogste prioriteit zou moeten worden gegeven wanneer het berekenen van de score. Een of meer onderwerpen kunnen worden ingevoerd, maar zijn beperkt tot **één werkwoord per onderwerp**. Zie [Onderwerpen en werven](/help/communities/implementing-scoring.md#topics-and-verbs).
Ingevoerd als `topic,verb` met de komma ontsnapt. Bijvoorbeeld:
  `/social/forum/hbs/social/forum\,ADD`
Het gebrek wordt geplaatst aan ADD werkwoord voor QnA en forumcomponenten.

* **Scorebereik**

  Het bereik voor geavanceerde scores wordt gedefinieerd door deze waarde (maximale score) en 0 (laagste haalbare score).

  De standaardwaarde is 100, zodat het scorebereik 0-100 is.

* **Tijdsinterval van verval van entiteit**

  Deze parameter vertegenwoordigt het aantal uren waarna alle entiteitscores worden gedecayed. Dit is nodig als u oude inhoud niet meer wilt opnemen in scores voor een communitysite.

  De standaardwaarde is 216000 uur (~24 jaar).

* **Toename van scores**
Dit specificeert de score tussen 0-scoring waaier, waarvoorbij de groei vertraagt om het aantal deskundigen te beperken.

  De standaardwaarde is 50.

## Geavanceerde scoreregels {#advanced-scoring-rules}

In de basisscoring is bekend hoeveel er nodig is om een badge te verdienen.

In de geavanceerde scoring wordt de hoeveelheid voortdurend aangepast op basis van de hoeveelheid kwaliteitsgegevens in het systeem. De scoring wordt voortdurend berekend op een manier die lijkt op een klokcurve.

Als een lid een expertisebadge heeft verdiend over een onderwerp dat niet meer actief is, bestaat de mogelijkheid dat het lid zijn badge verliest als gevolg van verval in de loop der tijd.

### scoringType {#scoringtype}

Een scoreregel is een set subregels voor scores, die elk het volgende declareren `scoringType`.

Als u de geavanceerde scoring-engine wilt aanroepen, `scoringType`moet worden ingesteld op `advanced`.

Zie [Subregels voor scores](/help/communities/implementing-scoring.md#scoring-sub-rules).

![geavanceerd scoretype](assets/advanced-scoring-type.png)

### Stopwoorden {#stopwords}

Het geavanceerde het scoren pakket installeert een configuratiemap die een stopwoordendossier bevat:

* `/libs/settings/community/scoring/configuration/stopwords`

Het geavanceerde het scoren algoritme gebruikt de lijst van woorden in het chronwoordendossier om gemeenschappelijke Engelse woorden te identificeren die tijdens inhoudsverwerking worden genegeerd.

Er wordt geen wijziging van dit bestand verwacht.

Als het stopwoordenbestand ontbreekt, geeft het geavanceerde scoring-programma een fout.

## Geavanceerde Badgingregels {#advanced-badging-rules}

De eigenschappen van de geavanceerde badging-regel verschillen van [basiseigenschappen van insigningsregels](/help/communities/implementing-scoring.md#badging-rules).

In plaats van punten te koppelen aan een badge-afbeelding, is het alleen nodig om het toegestane aantal experts en het toe te kennen badge-image te identificeren.

![geavanceerde merkregels](assets/advanced-badging-rules.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Type</th>
   <th>Beschrijving van waarde</th>
  </tr>
  <tr>
   <td>badgingPath</td>
   <td>String[]</td>
   <td><em>(Vereist)</em> Een tekenreeks met meerdere waarden voor badge-afbeeldingen tot het aantal badgingLevels. De wegen van het badge beeld moeten worden bevolen zodat wordt de eerste toegekend aan de hoogste deskundige. Als er minder badges zijn dan aangegeven door badgingLevels, vult het laatste badge in de array de rest van de array in. Voorbeeld:<br /> <code>/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png</code></td>
  </tr>
  <tr>
   <td>badgingLevels</td>
   <td>Lang</td>
   <td><em>(Optioneel)</em> Hiermee geeft u de niveaus van deskundigheid op die moeten worden toegekend. Als er bijvoorbeeld een <code>expert </code>en <code>almost expert</code> (twee badges), moet de waarde worden ingesteld op 2. Het badgingLevel moet overeenkomen met het aantal deskundige badge-afbeeldingen dat voor de eigenschap badgingPath wordt vermeld. De standaardwaarde is 1.</td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>String</td>
   <td><em>(Vereist)</em> Hiermee wordt de scoring-engine aangeduid als "basic" of "advanced". Ingesteld op "advanced" anders is de standaardwaarde "basic".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>String[]</td>
   <td><em>(Optioneel)</em> Een tekenreeks met meerdere waarden om de merkingsregel te beperken tot het noteren van gebeurtenissen die worden geïdentificeerd door een of meer scoreregels.<br /> Voorbeeld:<br /> <code>/libs/settings/community/scoring/rules/adv-comments-scoring</code><br /> Standaard is geen beperking.</td>
  </tr>
 </tbody>
</table>

## Opgenomen regels en badge {#included-rules-and-badge}

### Ingesloten badge {#included-badge}

In deze bètaversie is één beloning-gebaseerd deskundige badge opgenomen:

* `expert`

  `/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png`

![deskundige-badge](assets/included-badge.png)

Zorg ervoor dat het expertsymbool als beloning voor activiteit wordt weergegeven:

* `Badges` worden toegelaten voor de eigenschap, zoals een forum of component QnA.

* Geavanceerde regels voor scoring en badging worden toegepast op de pagina (of voorouder) waarop de component is geplaatst

Zie de basisinformatie voor:

* [Het toelaten van merktekens voor een component](/help/communities/implementing-scoring.md#enableforcomponent)
* [Toepassingsregels](/help/communities/implementing-scoring.md#applytopage)

### Inclusief rangtelregels en subregels {#included-scoring-rules-and-sub-rules}

In de bètaversie zijn twee geavanceerde scoringregels opgenomen voor de [forumfunctie](/help/communities/functions.md#forum-function) (elk voor het forum en de commentaarcomponenten van het forum):

1. `/libs/settings/community/scoring/rules/adv-comments-scoring`

   ```
   subRules[] =
   /libs/settings/community/scoring/rules/sub-rules/adv-comments-rule
   /libs/settings/community/scoring/rules/sub-rules/adv-voting-rule-owner
   /libs/settings/community/scoring/rules/sub-rules/adv-voting-rule
   ```

1. `/libs/settings/community/scoring/rules/adv-forums-scoring`

   ```
   subRules[] =
   /libs/settings/community/scoring/rules/sub-rules/adv-forums-rule
   /libs/settings/community/scoring/rules/sub-rules/adv-comments-rule
   /libs/settings/community/scoring/rules/sub-rules/adv-voting-rule-owner
   ```

**Opmerkingen:**

* Beide `rules` en `sub-rules` knooppunten zijn van het type `cq:Page`.
* `subRules` is een kenmerk van het type String`[]` over de regels `jcr:content` knooppunt.
* `sub-rules` kunnen worden gedeeld door verschillende scoreregels.
* `rules` moet zich op een opslagplaats bevinden met leesmachtigingen voor iedereen.
* Regelnamen moeten uniek zijn, ongeacht de locatie.

### Ingesloten Badgingregels {#included-badging-rules}

In de release zijn twee geavanceerde regels voor badging opgenomen die overeenkomen met de [geavanceerde forums en regels voor het maken van scores voor opmerkingen](#included-scoring-rules-and-sub-rules).

* `/libs/settings/community/badging/rules/adv-comments-badging`
* `/libs/settings/community/badging/rules/adv-forums-badging`

**Opmerkingen:**

* `rules` knooppunten zijn van het type cq:Page.
* `rules` moet zich op een opslagplaats bevinden met leesmachtigingen voor iedereen.
* Regelnamen moeten uniek zijn, ongeacht de locatie.
