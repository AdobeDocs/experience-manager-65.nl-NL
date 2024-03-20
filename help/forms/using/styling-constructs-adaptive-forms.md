---
title: Constructies voor stijlen voor adaptieve formulieren
description: Met het LESS-framework kunt u de weergave van aangepaste formulieren aanpassen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 691608a6-be82-4d81-b876-427de997e5be
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2352'
ht-degree: 0%

---

# Constructies voor stijlen voor adaptieve formulieren{#styling-constructs-for-adaptive-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Vereisten {#prerequisites}

Kennis van CSS en het LESS-framework.

## Wat kan worden aangepast {#what-can-be-customized}

In het artikel worden openbaar beschikbare CSS-klassen van adaptieve formulieren vermeld. Met deze klassen kunt u diverse componenten van een adaptief formulier opmaken. De opmaak van ontwerpcomponenten, zoals dialoogvensters en statusbalken met waarschuwingen, valt buiten het bereik van dit artikel. Gebruik deze opmaakconstructies alleen om stijlen te maken (met CSS of Minder) wanneer u geen stijl kunt toepassen op componenten die [themaeditor](https://helpx.adobe.com/experience-manager/6-3/forms/using/themes.html).

## Stijlen in aangepaste formulieren aanpassen {#customizing-styles-in-adaptive-forms}

Het LESS-framework vereenvoudigt het gebruik van hoofdletters en kleine letters om stijlen in aangepaste formulieren aan te passen. Met het framework kunt u stijlen definiëren met behulp van een set variabelen en functies (mixins). Het LESS-framework helpt de grootte van de gebundelde code te reduceren en vergroot de herbruikbaarheid ervan.

U kunt aangepaste formulierstijlen op de volgende manieren aanpassen:

* Het thema wijzigen
* Stijl van component wijzigen

## Thema wijzigen {#changing-theme}

U kunt het thema van een adaptief formulier wijzigen om ervoor te zorgen dat de weergave ervan consistent is met de webpagina&#39;s waarop het adaptieve formulier is ingesloten.

Wijzigingen in de algemene weergave van het aangepaste formulier met CSS-eigenschappen maken doorgaans deel uit van themawijzigingen. Belangrijke wijzigingen in de lo &quot;ok and feel of the adaptive form, zoals wijzigingen in de lay-out en plaatsing van componenten, worden niet als themawijzigingen beschouwd.

Op basis van de laarzentrekker definieert de volgende set CSS-eigenschappen het thema van een webpagina:

* Achtergrondkleur
* Rand (type, kleur, dikte)
* Lettertypekleur
* Opvulling
* Marge
* Tekengrootte
* LineHeight

Momenteel zijn LESS-variabelen alleen voor deze eigenschappen van de verschillende elementen in een adaptieve vorm gedefinieerd.

## Componentstijl wijzigen {#changing-component-style}

U kunt de vormgeving, lay-out, positionering en zichtbaarheid van elementen wijzigen. U kunt deze taak uitvoeren door uw aangepaste CSS-bestanden te maken of bij te werken, zodat deze de opmaakconstructies bevatten die in dit artikel worden vermeld.

Als u een stijl wilt toepassen op een adaptief formulier, opent u het adaptieve formulier in voor bewerking, opent u eigenschappen van adaptieve formuliercontainer en geeft u het pad van het aangepaste CSS-bestand op op het tabblad Standaard. Standaardstijlconstructies van het adaptieve formulier die worden overschreven door de constructies in het bestand custom.css.

## Onderdelen {#components}

De componenten die in dit artikel worden besproken, hebben hun vooraf gedefinieerde CSS-klassen. U kunt de variabelen bewerken om de stijlen in de CSS-klassen te wijzigen. U kunt ook de gehele klasse herschrijven. In deze sectie worden de klassen binnen componenten en stijlen beschreven die u kunt wijzigen met behulp van variabelen.

## Containerstijl {#container-styling}

Een container is de bovenste component. Andere deelvensters en velden bevinden zich onder de containercomponent.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guideContainerNode</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Beschrijving variabelen</strong></p> </td>
   <td><p><strong>Beschrijving variabelen</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>container-bgColor</code></p> </td>
   <td><p>Achtergrondkleur van de container</p> </td>
  </tr>
  <tr>
   <td><p><code>container-padding</code></p> </td>
   <td><p>Opvulling voor de container</p> </td>
  </tr>
  <tr>
   <td><p><code>container-margin</code></p> </td>
   <td><p>Marge voor de container</p> </td>
  </tr>
  <tr>
   <td><p><code>container-fontColor</code></p> </td>
   <td><p>Fontkleur voor de container</p> </td>
  </tr>
 </tbody>
</table>

## Veldstijl {#field-styling}

Adaptieve formulieren bevatten verschillende typen velden. Elk veld heeft een unieke klassenaam, de naam van het veld. Het veld heeft ook een algemene klassenaam `guideFieldNode`.

Velden zijn labels, widgets, Help-beschrijving (zowel lange als korte beschrijving) en veldHelp-pictogrammen (vraagteken).

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guideFieldNode</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>field-padding</code><strong></strong></p> </td>
   <td><p>Opvulling voor het veld</p> </td>
  </tr>
  <tr>
   <td><p><code>field-error-font-color</code></p> </td>
   <td><p>Fontkleur van de foutmelding van het veld</p> </td>
  </tr>
  <tr>
   <td><p><code>field-error-font-size</code></p> </td>
   <td><p>Tekengrootte van foutbericht van veld</p> </td>
  </tr>
 </tbody>
</table>

## Labelstijl {#label-styling}

Het element HTML **label** gebruikt voor het veld bevat de klassen **left** of **top** afhankelijk van of het label zich boven of links bevindt.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guideFieldLabel</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>label-font-color</code></p> </td>
   <td><p>Fontkleur voor veldlabel</p> </td>
  </tr>
  <tr>
   <td><p><code>label-font-size</code></p> </td>
   <td><p>Fontgrootte voor het veldlabel</p> </td>
  </tr>
  <tr>
   <td><p><code>label-line-height</code></p> </td>
   <td>CSS-eigenschap voor regelhoogte voor het veldlabel </td>
  </tr>
  <tr>
   <td><p><code>label-font-weight</code></p> </td>
   <td>Eigenschappen voor CSS-lettertypegewicht voor het veldlabel </td>
  </tr>
  <tr>
   <td><p><code>label-margin</code></p> </td>
   <td><p>Marge voor het veldlabel</p> </td>
  </tr>
 </tbody>
</table>

De CSS-regels voor het label worden toegepast met behulp van de **guideFieldLabel** label. Als u een auteur bent, schrap deze regel om uw douaneveranderingen zichtbaar te maken.

## Widget-stijl {#widgets-styling}

Afhankelijk van het type, bevatten widgets ook klassen. Vaak bevatten widgets de `guideFieldWidget` klasse. De widgets die bij HTML worden geleverd, gebruiken doorgaans de standaardinvoer voor HTML-elementen en selecteren. De opmaak wordt dienovereenkomstig toegepast. U kunt een aangepaste widget niet opmaken door de variabelen te wijzigen.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guideFieldWidget</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen <code></code></strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-bg-color</code></p> </td>
   <td>Achtergrondkleur voor widgets (werkt niet voor selectievakjes en keuzerondjes)</td>
  </tr>
  <tr>
   <td><p><code>widgets-border-color</code></p> </td>
   <td><p>Randkleur voor de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border-thickness</code></p> </td>
   <td><p>Randgrootte voor de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border-radius</code></p> </td>
   <td><p>Randstraal voor de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border-type</code></p> </td>
   <td><p>Randtype voor de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widget-border-focus-type</code></p> </td>
   <td><p>Focustype voor widgetranden</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border</code></p> </td>
   <td><p>Geconsolideerde randstijl van widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-font-color</code></p> </td>
   <td><p>Kleur van de tekst in de widget</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-font-size</code></p> </td>
   <td><p>Grootte van de tekst in de widget</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-line-height</code></p> </td>
   <td>CSS-lijneigenschap voor de widget </td>
  </tr>
  <tr>
   <td><p><code>widgets-padding</code></p> </td>
   <td><p>CSS-opvullingseigenschap voor de widget</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-focus-border-color</code></p> </td>
   <td><p>Randkleur wanneer de widget de focus heeft</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-mandatory-border-color</code></p> </td>
   <td><p>Randkleur van de widget voor de verplichte velden</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-mandatory-bg-color</code></p> </td>
   <td><p>Achtergrondkleur van de widget voor de verplichte velden</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-disabled-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor de widget wanneer het veld is uitgeschakeld</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-disabled-font-color</code></p> </td>
   <td><p>Fontkleur voor de widget wanneer het veld is uitgeschakeld</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-disabled-border-color</code></p> </td>
   <td><p>Randkleur voor de widget wanneer het veld is uitgeschakeld</p> </td>
  </tr>
  <tr>
   <td><p><code>widget-height</code></p> </td>
   <td>Hoogte van de widget (werkt niet voor selectievakje en keuzerondje)</td>
  </tr>
  <tr>
   <td><p><code>checkbutton-height</code></p> </td>
   <td><p>Hoogte voor selectievakje en keuzerondje.</p> </td>
  </tr>
  <tr>
   <td><p><code>listboxwidget-height</code></p> </td>
   <td><p>Maximumhoogte voor een meerkeuzevervolgkeuzelijst</p> </td>
  </tr>
 </tbody>
</table>

### Beperkingen in widgetstijl {#limitations-in-widget-styling}

De opmaak voor velden met focus, verplicht en uitgeschakeld is beperkt met behulp van variabelen. U kunt de stijl echter wijzigen door de stijlen te overschrijven. Er wordt vooral een beperking met variabelen gegeven om het aantal variabelen te controleren. De beperking kan worden versoepeld als de verschijning van een gebied drastisch verandert omdat het in om het even welke staten is die eerder worden besproken.

## Help-beschrijving {#help-description}

Een auteur kan de inhoud van de Hulp in de gebieden specificeren gebruikend Korte en Lange beschrijvingscomponenten. Beide componenten hebben een gemeenschappelijke klasse `.guideHelpDescription` en een andere klasse `.long`/ `.short`, afhankelijk van het type beschrijving. De inhoud van de Hulp is ingesloten in een paragraafelement om het stileren van de beschrijving met voeten te treden. De beschrijving van de Help (zowel lang als kort) wordt gewijzigd met behulp van variabelen die beginnen met widgetshelp, zoals vermeld in de volgende tabel:

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-long-bg-color</code></p> </td>
   <td><p>Achtergrondkleur van de lange Help van de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-long-border-color</code></p> </td>
   <td><p>Randkleur van de lange Help van de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-long-border-indicator-color</code></p> </td>
   <td><p>Randkleur linkerindicator van de lange Help van de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-bg-color</code></p> </td>
   <td><p>Achtergrondkleur van de korte Help van widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-color</code></p> </td>
   <td><p>Fontkleur van de korte Help van de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-tooltip-bg-color</code></p> </td>
   <td><p>Achtergrondkleur van de Help van de korte knopinfo van de widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-tooltip-color</code></p> </td>
   <td><p>Fontkleur van de korte Help van de knopinfo van de widgets</p> </td>
  </tr>
 </tbody>
</table>

## Voorwaarden en bepalingen {#terms-and-conditions}

De Voorwaarden (TnC) `` ``) kunt u voorwaarden en bepalingen opgeven. U kunt de widget aanpassen met de variabelen die in de volgende tabel worden beschreven.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><code>tnc-unvisited</code></td>
   <td>Fontkleur van niet-bezochte tnc-koppeling.</td>
  </tr>
  <tr>
   <td><code>tnc-visited</code></td>
   <td>Tekenkleur van bezochte tnc-koppeling.</td>
  </tr>
 </tbody>
</table>

## Knop {#button}

Knoppen zijn ook widgets. Hun opmaak wijkt echter enigszins af van die van de widgets. In adaptieve vormen vormt een van de volgende vormen een knop:

* input[type = tekst]
* knop
* element with class.button

HTML code voor knop:

`<button type="button" >`

`<span class="iconButtonicon"></`

`span>`

`<span class="iconButtonlabel"></`

`span>`

`</button>`

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>iconButton-icon</code></p> </td>
   <td><p>Hiermee worden pictogrammen voor knoppen weergegeven</p> </td>
  </tr>
  <tr>
   <td><p><code>iconButton-label</code></p> </td>
   <td><p>Label/bijschrift van knop Stijlen</p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen <code></code></strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>button-border-size</code></p> </td>
   <td><p>Randgrootte voor de knoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-border-type</code></p> </td>
   <td><p>Type rand</p> </td>
  </tr>
  <tr>
   <td><p><code>button-padding</code></p> </td>
   <td><p>CSS-opvullingseigenschap voor de knop</p> </td>
  </tr>
  <tr>
   <td><p><code>button-font-size</code></p> </td>
   <td><p>Tekengrootte voor de knop</p> </td>
  </tr>
  <tr>
   <td><p><code>button-background-color</code></p> </td>
   <td><p>Achtergrondkleur voor de knop</p> </td>
  </tr>
  <tr>
   <td><p><code>button-font-color</code></p> </td>
   <td><p>Tekenkleur van knop</p> </td>
  </tr>
  <tr>
   <td><p><code>button-border-color</code></p> </td>
   <td><p>Randkleur van de knop</p> </td>
  </tr>
  <tr>
   <td><p><code>button-large-padding</code></p> </td>
   <td><p>Opvulling voor de grote knoppen (knoppen met klasse .buttonlarge)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-large-font-size</code></p> </td>
   <td><p>Tekengrootte voor grote knoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-small-padding</code></p> </td>
   <td><p>Opvulling voor kleine knoppen (knoppen met klasse .buttonsmall)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-small-font-size</code></p> </td>
   <td><p>Fontgrootte voor kleine knoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-info-background-color</code></p> </td>
   <td><p>Achtergrondkleur voor informatieve knoppen (knoppen met de klasse .buttoninformative)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-info-font-color</code></p> </td>
   <td><p>Fontkleur voor informatieknoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-info-border-color</code></p> </td>
   <td><p>Randkleur voor informatieknoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-warning-background-color</code></p> </td>
   <td><p>Achtergrondkleur voor waarschuwingsgestileerde knoppen (knoppen met waarschuwing voor klasse .buttoner)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-warning-font-color</code></p> </td>
   <td><p>Fontkleur voor opgemaakte waarschuwingsknoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-warning-border-color</code></p> </td>
   <td><p>Randkleur voor opgemaakte waarschuwingsknoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-alert-background-color</code></p> </td>
   <td><p>Achtergrondkleur voor waarschuwingsknoppen (knoppen met waarschuwing voor klasse .buttoner)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-alert-font-color</code></p> </td>
   <td><p>Fontkleur voor waarschuwingsknoppen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-alert-border-color</code></p> </td>
   <td><p>Randkleur voor waarschuwingsknoppen</p> </td>
  </tr>
 </tbody>
</table>

## Vraagteken {#question-mark}

Voor widgets wordt een questionMark weergegeven wanneer een auteur een lange beschrijving toevoegt in de Help-inhoud. Het standaardpictogram in bootstrap wordt verstrekt gebruikt. Als u een aangepast pictogram wilt gebruiken, kunt u de opstartpictogrammen aanpassen.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guideHelpQuestionMark</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>questionmark-font-color</code></p> </td>
   <td><p>Kleur van het pictogram</p> </td>
  </tr>
  <tr>
   <td><p><code>questionmark-hover-font-color</code></p> </td>
   <td><p>Kleur van het pictogram wanneer de muis erop wordt geplaatst</p> </td>
  </tr>
 </tbody>
</table>

## Tabel {#table}

U kunt het kleurthema voor koptekst- en tekstrijen in een tabel wijzigen met de volgende variabelen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>table-header-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor de koptekstrij. De standaardwaarde is <code>#333</code>.<br /> </p> </td>
  </tr>
  <tr>
   <td><p><code>table-odd-row-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor de oneven tekstrij. De standaardwaarde is <code>rgb(255, 255, 255)</code>.</p> </td>
  </tr>
  <tr>
   <td><p><code>table-even-row-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor de even tekstrij. De standaardwaarde is <code>#eee</code>.</p> </td>
  </tr>
 </tbody>
</table>

## Bestandsbijlage {#file-attachment}

Met de widget Bestandsbijlage van adaptieve formulieren kunt u bestanden uploaden. U kunt de widget ook aanpassen met de variabelen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemPadding</code></p> </td>
   <td><p>Opvulling voor de bestanden die worden weergegeven in de widget</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemBackground</code></p> </td>
   <td><p>Achtergrondkleur voor het bestanditem</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemBorderColor</code></p> </td>
   <td><p>Randkleur voor de bovenrand</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemColor</code></p> </td>
   <td><p>Fontkleur voor het bestandstitem</p> </td>
  </tr>
  <tr>
   <td><p><code>filePreviewIconColor</code></p> </td>
   <td><p>Kleur voor het voorvertoningspictogram (Bootstrap-pictogram) in de widget</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemCommentHeight</code></p> </td>
   <td><p>Hoogte van de opmerking voor het bestandspunt</p> </td>
  </tr>
 </tbody>
</table>

## Navigatorstijlen {#navigator-styles}

Er zijn vier typen navigatortabs. Deze omvatten lusjes op de linkerzijde, bovenkant, in de tovenaar en accordeon. Elke navigator heeft een andere klasse.

<table>
 <tbody>
  <tr>
   <td><p><strong>Naviagator</strong></p> </td>
   <td><p><strong>CSS-klasse</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>Accordion</code></p> </td>
   <td><p>.accordeonnavigators</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs on the left</code></p> </td>
   <td><p>.tab-navigators-vertical</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs on the top</code></p> </td>
   <td><p>.tab-navigators</p> </td>
  </tr>
  <tr>
   <td><p><code>Wizard</code></p> </td>
   <td><p>.wizard-navigators</p> </td>
  </tr>
 </tbody>
</table>

Hieronder ziet u de HTML-code voor het tabnavigatorelement (vergelijkbaar met de tabbladen):

`<li>`

`<a>tab title</a>`

`</li>`

`Accordion navigator is an exception, it has following barebone`

`structure:`

`<div class="accordion.navigators">`

`<div>`

`<div class = "guideHeader">`

`<a>`

`<span class = "guideSummary" ></code>`

`........................... repeatable buttons, if the repeatable configuration is set ................................`

`<div class = "repeatableButtons">`

`<button name="Add" class="Add"/>`

`<button name="Remove" class="Remove"/>`

`</div>`

`</a>`

`</div>`

`................................ panel content ..................................`

`</div>`

`</div>`

U kunt de opmaak van de navigator wijzigen met CSS-regels die de elementen selecteren met **afstammeling** kiezers. Als u bijvoorbeeld een stijl voor tekstdecoratie wilt toevoegen aan het ankerlabel:

Tabnavigator bovenaan:

`.tab-navigators`

`li a {`

`text-decoration:`

`underline;`

`}`

`Tab navigator on left:`

`.tab-navigators-vertical`

`li a {`

`text-decoration:`

`underline;`

`}`

`Accordion navigator:`

`.accordion-navigators .guideHeader a .guideSummary {`

`text-decoration:`

`underline;`

`}`

`Wizard navigator:`

`.wizard-navigators`

`li a {`

`text-decoration:`

`underline;`

`}`

Bovendien zijn er klassen om tabnavigators (zowel links als boven) op te maken op basis van het feit of ze geneste/onderliggende/subnavigators hebben.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>nested_true</code></p> </td>
   <td><p>Tabnavigators (links en boven) met geneste/onderliggende/subnavigators</p> </td>
  </tr>
  <tr>
   <td><p><code>nested_false</code></p> </td>
   <td><p>Tabnavigators (links en boven) die geen geneste/onderliggende/subnavigators hebben</p> </td>
  </tr>
 </tbody>
</table>

De klasse guideNavIcon biedt een standaardpictogram voor tabnavigators (zowel links als boven) en wizardnavigators.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guideNavIcon</code></p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>U kunt het pictogram voor een bepaalde navigator wijzigen door een CSS-klasse op te geven in het deelvenster tijdens het ontwerpen, bijvoorbeeld &lt;class_name>. U voegt een **&lt;class_name>_nav** voor het pictogram van de navigator.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><strong>Tabnavigatoren</strong></p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p><code>navigator-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor de gehele tabnavigator</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor de tab</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-font-color</code></p> </td>
   <td><p>Fontkleur voor tab</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-hover-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor tab bij aanwijzen</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-hover-font-color</code></p> </td>
   <td><p>Fontkleur voor de tab bij aanwijzen</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-active-bg-color</code></p> </td>
   <td><p>Achtergrondkleur wanneer het deelvenster de focus heeft (actief)</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-active-font-color</code></p> </td>
   <td><p>Fontkleur wanneer het deelvenster de focus heeft</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-completed-bg-color</code></p> </td>
   <td><p>Achtergrondkleur wanneer de voltooiingsexpressie van het deelvenster true retourneert</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-completed-font-color</code></p> </td>
   <td><p>Fontkleur wanneer de voltooiingsexpressie van het deelvenster true retourneert</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-stepped-bg-color</code></p> </td>
   <td>Achtergrondkleur wanneer het deelvenster één keer de focus heeft maar de voltooiingsexpressie false retourneert </td>
  </tr>
  <tr>
   <td><p><code>tabs-stepped-font-color</code></p> </td>
   <td>Fontkleur wanneer het deelvenster één keer de focus heeft maar de voltooiingsexpressie false retourneert </td>
  </tr>
  <tr>
   <td><p><code>tabs-border-color</code></p> </td>
   <td><p>Randkleur voor de tab</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-font-size</code></p> </td>
   <td><p>Fontgrootte voor de tab</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-padding</code></p> </td>
   <td><p>Opvulling voor de tab</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-margin</code></p> </td>
   <td><p>Marge voor het tabblad</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-vertical-margin</code></p> </td>
   <td><p>Marge voor de verticale tabbladen</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-border-thickness</code></p> </td>
   <td><p>Randgrootte voor de tabbladen</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-min-height</code></p> </td>
   <td><p>Minimumhoogte van de tabbladen</p> </td>
  </tr>
  <tr>
   <td><p><code>heirarichal-indent</code></p> </td>
   <td><p>Inspringing voor de geneste tabbladen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Wizard Navigators</strong></p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-navigator-bg-color</code></p> </td>
   <td>Achtergrondkleur voor volledige wizardnavigator</td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor de wizard</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-font-color</code></p> </td>
   <td><p>Lettertypekleur voor de wizard</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-active-bg-color</code></p> </td>
   <td><p>Achtergrondkleur wanneer het deelvenster de focus heeft (actief)</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-active-font-color</code></p> </td>
   <td><p>Fontkleur wanneer de focus op het deelvenster is gericht</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-completed-bg-color</code></p> </td>
   <td><p>Achtergrondkleur wanneer de voltooiingsexpressie van het deelvenster true retourneert</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-completed-font-color</code></p> </td>
   <td><p>Fontkleur wanneer de voltooiingsexpressie van het deelvenster true retourneert</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-stepped-bg-color</code></p> </td>
   <td>Achtergrondkleur wanneer het deelvenster één keer de focus heeft maar de voltooiingsexpressie false retourneert</td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-stepped-font-color</code></p> </td>
   <td><p>Fontkleur wanneer het deelvenster één keer de focus heeft maar als de voltooiingsexpressie false retourneert</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-border-color</code></p> </td>
   <td><p>Kleur voor de wizard</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-font-size</code></p> </td>
   <td><p>Fontgrootte voor de wizard</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-padding</code></p> </td>
   <td><p>Opvulling voor de wizard</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-border-thickness</code></p> </td>
   <td><p>Randgrootte voor de wizard</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-nav-bullet-border</code></p> </td>
   <td><p>Randkleur van het navigatoropsommingsteken van de wizard (bijschrift/label vooraf bevestigen)</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-progress-bg-color</code></p> </td>
   <td><p>Achtergrondkleur van de voortgangsbalk van de wizard Navigator</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-progress-color</code></p> </td>
   <td><p>Vulkleur voor de voortgangsbalk</p> </td>
  </tr>
  <tr>
   <td><p><strong>Accordeonnavigatoren</strong></p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p><code>accordion-tabs-padding</code></p> </td>
   <td><p>Opvulling voor accordeon</p> </td>
  </tr>
 </tbody>
</table>

## Opmaak deelvenster {#panel-styling}

Een deelvenster bevat een optionele werkbalk en de bijbehorende inhoud.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guidePanelNode</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>panel-background-color</code></p> </td>
   <td><p>Achtergrondkleur voor deelvenster</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-font-size</code></p> </td>
   <td><p>Tekengrootte voor de deelvenstertekst</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-font-color</code></p> </td>
   <td><p>Lettertypekleur voor de deelvenstertekst<br /> </p> </td>
  </tr>
  <tr>
   <td><p><code>panel-padding</code></p> </td>
   <td><p>Opvulling binnen het deelvenster</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-description-font-size</code></p> </td>
   <td><p>Fontgrootte van paneelbeschrijving</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-description-padding</code></p> </td>
   <td><p>Opvulling van de beschrijving van het deelvenster</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-help-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor Help van deelvenster</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-help-border-indicator-color</code></p> </td>
   <td><p>Randkleur voor het deelvenster aangeven</p> </td>
  </tr>
 </tbody>
</table>

Het knooppunt van het deelvenster is onderverdeeld in navigators en inhoud. Daar `` `` is geen afzonderlijke stijlcomponent voor de inhoud. De beschreven variabelen worden toegepast op de navigator en de inhoud.

Het bovenste deelvenster (RootPanel) heeft deze klasse niet.

## Mobiele stijl {#mobile-styling}

## Kopbalk {#header-bar}

Deze variabelen beïnvloeden de kopbalbar die op een mobiel apparaat of kleine het schermapparaten zichtbaar is die paneeltitel en volgende en achternavigators bevatten.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>guide-header-bar</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>headerbar-background-color</code></p> </td>
   <td><p>Achtergrondkleur voor de koptekstbalk</p> </td>
  </tr>
  <tr>
   <td><p><code>headerbar-font-color</code></p> </td>
   <td><p>Fontkleur voor de tekst in de koptekstbalk</p> </td>
  </tr>
  <tr>
   <td><p><code>headerbar-padding</code></p> </td>
   <td><p>Opvulling voor koptekstbalk</p> </td>
  </tr>
 </tbody>
</table>

## Schuifindicator {#scroll-indicator}

Deze variabelen zijn van invloed op de schuifindicator. Dit is een oranje pijl die wordt weergegeven op een mobiel apparaat of een klein scherm. Een schuifindicator geeft aan dat er inhoud is buiten het zichtbare gedeelte van het scherm. U kunt omlaag schuiven om het te zien. Wanneer u het einde van de inhoud hebt bereikt, verdwijnt de pijl.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>mobileScrollIndicator</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorBottom</code></p> </td>
   <td><p>Vaste positie van schuifindicator vanaf onderkant</p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorRight</code></p> </td>
   <td><p>Vaste positie van schuifindicator van rechts</p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorWidth</code></p> </td>
   <td><p>Breedte van schuifindicator</p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorHeight</code></p> </td>
   <td><p>Hoogte van schuifindicator</p> </td>
  </tr>
 </tbody>
</table>

## Mobiele vaste werkbalkspecifieke variabelen {#mobile-fixed-toolbar-layout-specific-variables}

Deze variabelen in de volgende tabel zijn van invloed op de vaste indeling van de mobiele werkbalk.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-klasse </strong></p> </td>
   <td><p><code>mobileToolbar</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarBottom</code></p> </td>
   <td><p>Vaste positie van werkbalk, op mobiel apparaat, van onderkant</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarTop</code></p> </td>
   <td><p>Vaste positie van werkbalk op mobiel apparaat, van boven naar boven</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarLeft</code></p> </td>
   <td><p>Vaste positie van werkbalk, op mobiel apparaat, van links</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarRight</code></p> </td>
   <td><p>Vaste positie van werkbalk, op mobiel apparaat, van rechts</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileButtonIconTopMargin</code></p> </td>
   <td><p>Vaste positie van pictogram knoppen van werkbalk, van boven</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileButtonIconWidth</code></p> </td>
   <td><p>Breedte van pictogram knoppen van werkbalk op mobiel apparaat</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileButtonIconHeight</code></p> </td>
   <td><p>Hoogte van knoppen op mobiele apparaten</p> </td>
  </tr>
  <tr>
   <td><p><code>mobilefixedtoolbarbgcolor</code></p> </td>
   <td><p>Achtergrondkleur van werkbalk op mobiel apparaat</p> </td>
  </tr>
 </tbody>
</table>

## Themaspecifieke variabele {#theme-specific-variable}

De **Eenvoudige inschrijving** thema op /etc/clientlibs/fd/af/guidetheme/simpleEnrollment en de categorie `guide.theme.simpleEnrollment` ook een aantal variabelen invoeren. Als u een thema wilt creëren dat eenvoudige inschrijving verbetert, kunt u de volgende &quot;extra variabelen gebruiken:

<table>
 <tbody>
  <tr>
   <td><p><strong>Variabelen </strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>button-focus-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor knop bij focus</p> </td>
  </tr>
  <tr>
   <td><p><code>button-hover-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor knop bij aanwijzen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-radius</code></p> </td>
   <td><p>Straal van knop</p> </td>
  </tr>
  <tr>
   <td><p><code>navigation-button-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor navigatieknoppen (achter/na)</p> </td>
  </tr>
  <tr>
   <td><p><code>navigation-button-bg-hover-color</code></p> </td>
   <td><p>Achtergrondkleur voor navigatieknoppen (achter/na) bij aanwijzen</p> </td>
  </tr>
  <tr>
   <td><p><code>initial-nav-color</code></p> </td>
   <td><p>Achtergrondkleur voor wizardnavigators en overeenkomstige vooruitgangsbar, wanneer eerst teruggegeven.</p> </td>
  </tr>
  <tr>
   <td><p><code>active-nav-color</code></p> </td>
   <td>Achtergrondkleur voor huidige/actieve wizardnavigator en bijbehorende voortgangsbalk </td>
  </tr>
  <tr>
   <td><p><code>visited-nav-color</code></p> </td>
   <td><p>Achtergrondkleur voor wizardnavigators en overeenkomstige vooruitgangsbar, die zijn bezocht.</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-bifercating-border-color</code></p> </td>
   <td><p>Randkleurbifurcatie-container in navigators en deelvenster</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-navigator-separator-color</code></p> </td>
   <td><p>Tabbladen voor tabbladen die aan de linkerkant worden gescheiden door kleur van de onderrand (tabnavigators).</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-child-nav-bg-color</code></p> </td>
   <td><p>Achtergrondkleur voor geneste/onderliggende/subnavigators van navigator</p> </td>
  </tr>
 </tbody>
</table>
