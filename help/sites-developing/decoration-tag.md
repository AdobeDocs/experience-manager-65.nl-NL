---
title: Decoratietag
description: Wanneer een component in een webpagina wordt gerenderd, kan een HTML-element worden gegenereerd, waarbij de gerenderde component binnen zichzelf wordt verpakt. Voor ontwikkelaars biedt AEM duidelijke en eenvoudige logica die de decoratietags regelt die onderdelen bevatten.
exl-id: d049ebf1-7fa6-4d2c-86f9-b18e107092ea
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---

# Decoratietag{#decoration-tag}

Wanneer een component in een webpagina wordt gerenderd, kan een HTML-element worden gegenereerd, waarbij de gerenderde component binnen zichzelf wordt verpakt. Dit heeft hoofdzakelijk twee doelen:

* Een component kan alleen worden bewerkt wanneer deze is verpakt met een HTML-element.
* Het element wrapping wordt gebruikt om de klassen van HTML toe te passen die verstrekken:

   * indelingsgegevens
   * opmaakgegevens

Voor ontwikkelaars biedt AEM duidelijke en eenvoudige logica die de decoratietags regelt die onderdelen bevatten. Of en hoe de versietag wordt teruggegeven wordt bepaald door de combinatie twee factoren, die deze pagina in duiken:

* De component zelf kan zijn versietag met een reeks eigenschappen vormen.
* De manuscripten die componenten (HTL, JSP, verzender, etc.) omvatten kunnen de aspecten van de decoratietag met omvat parameters bepalen.

## Recommendations {#recommendations}

Hier zijn sommige algemene aanbevelingen van wanneer om het omslagelement te omvatten dat in het vermijden zou moeten helpen lopen in onverwachte kwesties:

* De aanwezigheid van het omvattende element mag niet verschillen tussen WCMModes (bewerkings- of voorvertoningsmodus), instanties (auteur of publicatie) of omgevingen (opmaken of productie), zodat de CSS en JavaScripts van de pagina in alle gevallen op dezelfde manier werken.
* Het omvattende element zou aan alle componenten moeten worden toegevoegd die editable zijn, zodat de paginaredacteur hen kan initialiseren en behoorlijk bijwerken.
* Voor niet-bewerkbare componenten kan het omvattende element worden vermeden als het geen bepaalde functie dient, zodat de resulterende markering niet onnodig wordt opgeblazen.

## Componentbesturingselementen {#component-controls}

De volgende eigenschappen en knopen kunnen op de componenten worden toegepast om het gedrag van hun versieringsmarkering te controleren:

* **`cq:noDecoration {boolean}`:** Deze eigenschap kan aan een component worden toegevoegd en een werkelijke waarde dwingt AEM geen omvattende elementen over de component te genereren.

* **`cq:htmlTag`node :** dit knooppunt kan worden toegevoegd onder een component en kan de volgende eigenschappen hebben:

   * **`cq:tagName {String}`:** dit kan worden gebruikt om een markering van douaneHTML te specificeren die voor het verpakken van de componenten in plaats van het standaardDIV element moet worden gebruikt.
   * **`class {String}`:** dit kan worden gebruikt om CSS klassennamen te specificeren die aan de omslag moeten worden toegevoegd.
   * Andere eigenschapnamen worden toegevoegd als HTML-kenmerken met dezelfde tekenreekswaarde als opgegeven.

## Scriptbesturingselementen {#script-controls}

Het omslaggedrag verschilt echter afhankelijk van als [ HTML ](/help/sites-developing/decoration-tag.md#htl) of [ JSP ](/help/sites-developing/decoration-tag.md#jsp) wordt gebruikt om het element te omvatten.

### HTL {#htl}

In het algemeen kan het gedrag van de omslag in HTML als volgt worden samengevat:

* Geen omvattende DIV wordt standaard gerenderd (wanneer alleen `data-sly-resource="foo"` wordt uitgevoerd).
* Alle wcm-modi (uitgeschakeld, voorvertoning, bewerking op auteur en publiceren) worden op identieke wijze weergegeven.

Het gedrag van de omslag kan ook volledig worden geregeld.

* Het HTML-script heeft volledige controle over het resulterende gedrag van de omvattende tag.
* Componenteigenschappen (zoals `cq:noDecoration` en `cq:tagName` ) kunnen ook de tag wrapper definiëren.

Het is mogelijk om het gedrag van de omsluitende tags van HTML-scripts en de bijbehorende logica volledig te bepalen.

Voor verdere informatie over het ontwikkelen in HTML zie de [ documentatie HTML ](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=nl-NL).

#### Beslissingsboom {#decision-tree}

Deze beslissingsstructuur geeft een overzicht van de logica die het gedrag van de omsluitende tags bepaalt.

![ chlimage_1-75 ](assets/chlimage_1-75a.png)

#### Gevallen gebruiken {#use-cases}

In de volgende drie gebruiksgevallen ziet u voorbeelden van de manier waarop de labels van de omloop worden verwerkt. Ook ziet u hoe eenvoudig het is om het gewenste gedrag van de labels van de omloop te bepalen.

Alle volgende voorbeelden nemen de volgende inhoudsstructuur, en componenten aan:

```
/content/test/
  @resourceType = "test/components/one"
  child/
    @resourceType = "test/components/two"
```

```
/apps/test/components/
  one/
    one.html
  two/
    two.html
    cq:htmlTag/
      @cq:tagName = "article"
      @class = "component-two"
```

#### Hoofdlettergebruik 1: Een component opnemen voor hergebruik van code {#use-case-include-a-component-for-code-reuse}

Het meest gangbare geval is wanneer een component een andere component bevat om redenen van hergebruik van code. In dat geval is het niet de bedoeling dat de opgenomen component bewerkbaar is met een eigen werkbalk en dialoogvenster, zodat er geen omloop nodig is en de component `cq:htmlTag` wordt genegeerd. Dit kan als standaardgedrag worden beschouwd.

`one.html: <sly data-sly-resource="child"></sly>`

`two.html: Hello World!`

Resulterende uitvoer op `/content/test.html`:

**`Hello World!`**

Een voorbeeld zou een component zijn die een component van het kernbeeld omvat om een beeld te tonen, typisch in dat geval door een synthetisch middel te gebruiken, dat in het omvatten van een virtuele kindcomponent bestaat door tot gegeven-slim-middel een voorwerp van de Kaart over te gaan dat alle eigenschappen vertegenwoordigt die de component zou hebben.

#### Hoofdlettergebruik 2: een bewerkbare component opnemen {#use-case-include-an-editable-component}

Een ander veelvoorkomend geval van gebruik is wanneer de containercomponenten editable kindcomponenten, zoals een Container van de Lay-out omvatten. In dit geval heeft elk opgenomen onderliggend item een omloop nodig om de editor te laten werken (tenzij dit expliciet wordt uitgeschakeld met de eigenschap `cq:noDecoration` ).

Aangezien de inbegrepen component in dit geval een onafhankelijke component is, heeft het een omslagelement voor de redacteur nodig om te werken, en zijn lay-out en stijl te bepalen om toe te passen. Voor het activeren van dit gedrag is er de optie `decoration=true` .

`one.html: <sly data-sly-resource="${'child' @ decoration=true}"></sly>`

`two.html: Hello World!`

Resulterende uitvoer op `/content/test.html`:

**`<article class="component-two">Hello World!</article>`**

#### Hoofdlettergebruik 3: aangepast gedrag {#use-case-custom-behavior}

Er kan een aantal complexe gevallen zijn, die gemakkelijk kunnen worden verwezenlijkt door HTL de mogelijkheid te bieden om expliciet het volgende te verstrekken:

* **`decorationTagName='ELEMENT_NAME'`** De elementnaam van de omloop definiëren.
* **`cssClassName='CLASS_NAME'`** De CSS-klassenamen definiëren die erop moeten worden ingesteld.

`one.html: <sly data-sly-resource="${'child' @ decorationTagName='aside', cssClassName='child'}"></sly>`

`two.html: Hello World!`

Resulterende uitvoer `/content/test.html`:

**`<aside class="child">Hello World!</aside>`**

## JSP {#jsp}

Wanneer het omvatten van een component die `cq:includ` e of `sling:include` gebruikt, het standaardgedrag in AEM is div te gebruiken om het element te verpakken. Nochtans, kan dit verpakken op twee manieren worden aangepast:

* Geef AEM expliciet op om de component niet te laten omlopen met `cq:noDecoration` .
* Gebruik een aangepaste HTML-tag om de component te laten omlopen met `cq:htmlTag`/ `cq:tagName` of `decorationTagName` .

### Beslissingsboom {#decision-tree-1}

De volgende beslisboom illustreert hoe `cq:noDecoration`, `cq:htmlTag`, `cq:tagName` en `decorationTagName` het gedrag van de omslag beïnvloeden.

![ chlimage_1-3 ](assets/chlimage_1-3a.jpeg)
