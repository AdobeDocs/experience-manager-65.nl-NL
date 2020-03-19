---
title: Geavanceerde scores en Badges
seo-title: Geavanceerde scores en Badges
description: Geavanceerde scoring instellen
seo-description: Geavanceerde scoring instellen
uuid: 48caca57-43d3-4f2f-adf3-257428ba54d5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: eb3d5c37-8097-46de-8c4f-804ea723f1c5
docset: aem65
translation-type: tm+mt
source-git-commit: 974d58efa560b90234d5121a11bdb445c7bf94cf

---


# Geavanceerde scores en Badges{#advanced-scoring-and-badges}

## Overzicht {#overview}

Met geavanceerd scoren kunnen badges worden toegekend om leden te identificeren als experts. Bij geavanceerd scoren worden punten toegewezen op basis van de hoeveelheid ** en de kwaliteit van de inhoud die door een lid is gemaakt, terwijl bij elementaire scoring punten worden toegewezen op basis van de hoeveelheid gemaakte inhoud.

Dit verschil is het gevolg van de scores die zijn gebruikt voor de berekening van de scores. De basisscoring-engine past eenvoudige wiskunde toe. De geavanceerde scoring-engine is een adaptief algoritme dat actieve leden belont die waardevolle en relevante inhoud leveren, afgeleid via de verwerking van natuurlijke talen (NLP) van een onderwerp.

Naast inhoudrelevantie houden de scoringsalgoritmen rekening met lidactiviteiten, zoals het stemmen en het percentage antwoorden. Hoewel deze elementen in de standaardscoring kwantitatief worden opgenomen, worden ze bij geavanceerd scoren op algoritmische wijze gebruikt.

Daarom vereist de geavanceerde scoring-engine voldoende gegevens om de analyse zinvol te maken. De prestatiedrempel voor het worden van een expert wordt constant opnieuw geëvalueerd aangezien het algoritme voortdurend aan het volume en de kwaliteit van gecreeerde inhoud aanpast. Er is ook een concept van *verval* van oudere posten van een lid. Als een deskundige niet langer deelneemt aan het onderwerp waar hij of zij de status van deskundige heeft gekregen, kan hij of zij op een vooraf bepaald punt (zie de configuratie [van de](#configurable-scoring-engine)scoremotor) zijn of haar status als deskundige verliezen.

Geavanceerde scoring instellen is vrijwel hetzelfde als basisscoring:

* Basisregels en geavanceerde regels voor scoring en badging worden op dezelfde manier [toegepast op inhoud](/help/communities/implementing-scoring.md#apply-rules-to-content)

   * Basisregels en geavanceerde regels voor scoring en badging kunnen op dezelfde inhoud worden toegepast

* [Het toelaten van badges voor componenten](/help/communities/implementing-scoring.md#enable-badges-for-component) is generiek

De verschillen bij het instellen van de regels voor scoring en badging zijn:

* Configureerbare geavanceerde scores-engine
* Geavanceerde regels voor scoring:

   * `scoringType` instellen op `advanced`
   * vereist `stopwords`

* Geavanceerde regels voor badging:

   * `badgingType` instellen op `advanced`
   * `badgingLevels` vastgesteld op **aantal te gunnen deskundigen**
   * vereist `badgingPaths` serie van badges in plaats van drempels serie toewijzingspunten aan badges

>[!NOTE]
>
>Installeer het [Expert Identification-pakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg)om geavanceerde scoring- en badingmogelijkheden te gebruiken.

## Configureerbare scores-engine {#configurable-scoring-engine}

De geavanceerde het schrapen motor verstrekt een configuratie OSGi met parameters die het geavanceerde het schrapen algoritme beïnvloeden.

![chlimage_1-139](assets/chlimage_1-139.png)

* **Scoregewichten**

   Voor een onderwerp, specificeer het werkwoord dat de hoogste prioriteit zou moeten worden gegeven wanneer het berekenen van de score. Een of meer onderwerpen kunnen zijn ingegaan, maar beperkt tot **één werkwoord per onderwerp**. Zie [Onderwerpen en Verbs](/help/communities/implementing-scoring.md#topics-and-verbs).
Is ingevoerd zoals `topic,verb` met de vrijgekomen komma. Bijvoorbeeld:
   `/social/forum/hbs/social/forum\,ADD`
Het gebrek wordt geplaatst aan ADD werkwoord voor QnA en forumcomponenten.

* **Scorebereik**

   Het bereik voor geavanceerde scores wordt gedefinieerd door deze waarde (hoogst haalbare score) en 0 (laagste haalbare score).

   De standaardwaarde is 100, zodat het scorebereik 0-100 is.

* **Tijdsinterval van verval van entiteit**

   Deze parameter vertegenwoordigt het aantal uren waarna alle entiteitscores worden gedecayed. Dit is nodig als u oude inhoud niet meer wilt opnemen in scores voor een communitysite.

   De standaardwaarde is 216000 uur (~24 jaar).

* **De het scoren groeisnelheid** specificeert de score tussen 0 en het scoren waaier, waarwaarvoorbij de groei vertraagt om het aantal deskundigen te beperken.

   De standaardwaarde is 50.

## Geavanceerde scoreregels {#advanced-scoring-rules}

In de basisscoring is bekend hoeveel er nodig is om een badge te verdienen.

In de geavanceerde scoring wordt de hoeveelheid voortdurend aangepast op basis van de hoeveelheid kwaliteitsgegevens in het systeem. De scoring wordt voortdurend berekend op een manier die lijkt op een klokcurve.

Als een lid een expertisebadge heeft verdiend over een onderwerp dat niet meer actief is, bestaat de mogelijkheid dat het lid zijn badge verliest als gevolg van verval in de loop der tijd.

### scoringType {#scoringtype}

Een scoreregel is een set scoring-subregels, die elk de `scoringType`code declareren.

Als u de geavanceerde scoring-engine wilt aanroepen, `scoringType`moet u deze instellen op `advanced`.

Zie [Score-subregels](/help/communities/implementing-scoring.md#scoring-sub-rules).

![chlimage_1-140](assets/chlimage_1-140.png)

### Stopwoorden {#stopwords}

Het geavanceerde het scoren pakket installeert een configuratiemap die een stopwoordendossier bevat:

* `/etc/community/scoring/configuration/stopwords`

Het geavanceerde het scoren algoritme gebruikt de lijst van woorden in het chronwoordendossier om gemeenschappelijke Engelse woorden te identificeren die tijdens inhoudsverwerking worden genegeerd.

Er wordt geen wijziging van dit bestand verwacht.

Als het stopwoordenbestand ontbreekt, genereert het geavanceerde scoring-programma een fout.

## Geavanceerde spelregels {#advanced-badging-rules}

De geavanceerde eigenschappen van de merkingsregel verschillen van de [basiseigenschappen](/help/communities/implementing-scoring.md#badging-rules)van de merkingsregel.

In plaats van punten te koppelen aan een badge-afbeelding, is het alleen nodig om het toegestane aantal experts en het toe te kennen badge-image te identificeren.

![chlimage_1-141](assets/chlimage_1-141.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Type</th>
   <th>Waarde Beschrijving</th>
  </tr>
  <tr>
   <td>badgingPath</td>
   <td>Tekenreeks[]</td>
   <td><em>(Vereist)</em> Een tekenreeks met meerdere waarden voor badge-afbeeldingen tot het aantal badgingLevels. De wegen van het badge beeld moeten worden bevolen zodat eerste aan de hoogste deskundige wordt toegekend. Als er minder badges zijn dan aangegeven door badgingLevels, vult het laatste badge in de array de rest van de array in. Voorbeeld:<br /> <code>/etc/community/badging/images/expert-badge/jcr:content/expert.png</code></td>
  </tr>
  <tr>
   <td>badgingLevels</td>
   <td>Lang</td>
   <td><em>(Optioneel)</em> Hiermee geeft u de niveaus van deskundigheid op die moeten worden toegekend. Als er bijvoorbeeld een badge <code>expert </code>en een badge <code>almost expert</code> (twee badges) moeten zijn, moet de waarde worden ingesteld op 2. Het badgingLevel moet overeenkomen met het aantal deskundige badge-afbeeldingen dat voor de eigenschap badgingPath wordt vermeld. De standaardwaarde is 1.</td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>Tekenreeks</td>
   <td><em>(Vereist)</em> Hiermee wordt de scoring-engine aangeduid als "basis" of "geavanceerd". Ingesteld op "advanced" anders is de standaardwaarde "basic".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>Tekenreeks[]</td>
   <td><em>(Optioneel)</em> Een tekenreeks met meerdere waarden waarmee de badgingregel wordt beperkt tot het scoren van gebeurtenissen die worden aangeduid met de vermelde scoreregel(s).<br /> Voorbeeld:<br /> Standaard is <code>/etc/community/scoring/rules/adv-comments-scoring</code><br /> geen beperking.</td>
  </tr>
 </tbody>
</table>

## Opgenomen regels en badge {#included-rules-and-badge}

### Ingesloten badge {#included-badge}

In deze bètaversie is één beloning-gebaseerd deskundige badge opgenomen:

* `expert`

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-142](assets/chlimage_1-142.png)

Zorg ervoor dat het expertsymbool als beloning voor activiteit wordt weergegeven:

* `Badges` worden toegelaten voor de eigenschap, zoals een forum of component QnA.

* Geavanceerde regels voor scoring en badging worden toegepast op de pagina (of voorouder) waarop de component is geplaatst

Zie de basisinformatie voor:

* [Het toelaten van merktekens voor een component](/help/communities/implementing-scoring.md#enableforcomponent)
* [Toepassingsregels](/help/communities/implementing-scoring.md#applytopage)

### Inclusief rangtelregels en subregels {#included-scoring-rules-and-sub-rules}

In de bètaversie zijn twee geavanceerde scoreregels opgenomen voor de [forumfunctie](/help/communities/functions.md#forum-function) (één voor het forum en commentaarcomponenten van de forumfunctie):

1. `/etc/community/scoring/rules/adv-comments-scoring`

   * `subRules[] =
/etc/community/scoring/rules/sub-rules/adv-comments-rule
/etc/community/scoring/rules/sub-rules/adv-voting-rule-owner
/etc/community/scoring/rules/sub-rules/adv-voting-rule`

1. `/etc/community/scoring/rules/adv-forums-scoring`

   * `subRules[] =
/etc/community/scoring/rules/sub-rules/adv-forums-rule
/etc/community/scoring/rules/sub-rules/adv-comments-rule
/etc/community/scoring/rules/sub-rules/adv-voting-rule-owner`

**Opmerkingen:**

* Zowel `rules`als `sub-rules` knopen zijn van type `cq:Page`

* `subRules`is een attribuut van typeString[] op de knoop van de regel `jcr:content`

* `sub-rules` kunnen worden gedeeld door verschillende scoreregels

* `rules`moet zich bevinden op een opslagplaats met leesmachtigingen voor iedereen

   * Namen van regels moeten uniek zijn, ongeacht de locatie

### Ingesloten Badgingregels {#included-badging-rules}

In de release zijn twee geavanceerde regels voor het aanbrengen van een badge opgenomen die overeenkomen met de [geavanceerde forums en regels](#included-scoring-rules-and-sub-rules)voor het noteren van opmerkingen.

* `/etc/community/badging/rules/adv-comments-badging`
* `/etc/community/badging/rules/adv-forums-badging`

**Opmerkingen:**

* `rules` knooppunten zijn van het type cq:Page
* `rules` moet zich bevinden op een opslagplaats met leesmachtigingen voor iedereen

   * Namen van regels moeten uniek zijn, ongeacht de locatie

