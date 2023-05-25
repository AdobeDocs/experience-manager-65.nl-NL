---
title: GraphQL-query's optimaliseren
description: Leer hoe u uw GraphQL-query's kunt optimaliseren tijdens het filteren, pagineren en sorteren van uw Content Fragments in Adobe Experience Manager as a Cloud Service voor levering van inhoud zonder kop.
source-git-commit: 1481d613783089046b44d4652d38f7b4b16acc4d
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 0%

---


# GraphQL-query&#39;s optimaliseren {#optimizing-graphql-queries}

>[!NOTE]
>
>Overweeg voordat u deze optimaliseringsaanbevelingen toepast [Inhoudsfragmenten bijwerken voor pagineren en sorteren in GraphQL-filters](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md) voor de beste prestaties.

Op een AEM instantie met een hoog aantal Inhoudsfragmenten dat hetzelfde model deelt, kunnen vragen in de GraphQL-lijst kostbaar worden (in termen van bronnen).

De reden is dat *alles* fragmenten die een model delen dat wordt gebruikt binnen de GraphQL-query, moeten in het geheugen worden geladen. Dit kost zowel tijd als geheugen. Filteren, waardoor het aantal items in de (uiteindelijke) resultatenset kan worden verminderd, kan alleen worden toegepast **na** het laden van de volledige resultaatset in het geheugen.

Dit proces kan de indruk wekken dat zelfs kleine resultaatreeksen (kunnen) tot slechte prestaties leiden. In werkelijkheid wordt de vertraging echter veroorzaakt door de grootte van de oorspronkelijke resultaatset, aangezien deze intern moet worden afgehandeld voordat filters kunnen worden toegepast.

Om de prestaties en het geheugen te verminderen, moet deze aanvankelijke resultaatreeks zo klein mogelijk worden gehouden.

AEM biedt twee manieren om GraphQL-query&#39;s te optimaliseren:

* [Hybride filtering](#hybrid-filtering)
* [Paginering](#paging) (of paginering)

   * [Sorteren](#sorting) heeft niet rechtstreeks betrekking op optimalisatie, maar heeft wel betrekking op paginering

Elke benadering heeft zijn eigen gebruiksgevallen en beperkingen. In dit document vindt u informatie over het filteren en pagineren van hybride foto&#39;s, met enkele [best practices](#best-practices) om GraphQL-query&#39;s te optimaliseren.

## Hybride filtering {#hybrid-filtering}

Bij hybride filters wordt JCR-filtering gecombineerd met AEM filtering.

Het past een filter JCR (in de vorm van een vraagbeperking) toe alvorens het resultaat te laden dat in geheugen voor AEM het filtreren wordt geplaatst. Hierbij wordt de in het geheugen geladen resultatenset verminderd, aangezien het JCR-filter vooraf overbodige resultaten verwijdert.

>[!NOTE]
>
>Om technische redenen (bijvoorbeeld flexibiliteit, nesten van fragmenten), kan AEM niet het volledige filtreren aan JCR delegeren.

Met deze techniek blijft de flexibiliteit behouden die GraphQL-filters bieden, terwijl tegelijkertijd zoveel mogelijk filters worden gedelegeerd aan JCR.

## Paginering {#paging}

GraphQL in AEM ondersteunt twee typen paginering:

* [paginering op basis van limiet/verschuiving](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#list-offset-limit)
Dit type van paginering wordt gebruikt voor lijstvragen; deze vragen eindigen met 
`List`; bijvoorbeeld: `articleList`.
Als u dit wilt gebruiken, moet u de positie opgeven van het eerste item dat moet worden geretourneerd (de `offset`) en het aantal objecten dat moet worden geretourneerd (de `limit`, of paginaformaat).

* [cursorpaginering](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#paginated-first-after) (vertegenwoordiger `first`en `after`) Dit paginatype bevat een unieke id voor elk item; wordt ook wel de cursor genoemd.
In de vraag, specificeert u de curseur van het laatste punt van de vorige pagina, plus de paginagrootte (het maximumaantal punten dat moet worden teruggekeerd).

   Aangezien op curseur-gebaseerde paginering niet binnen de gegevensstructuren van op lijst-gebaseerde vragen past, heeft AEM geïntroduceerd `Paginated` type query; bijvoorbeeld: `articlePaginated`. De gebruikte gegevensstructuren en parameters volgen [GraphQL Cursor ConnectionSpecification](https://relay.dev/graphql/connections.htm).

   >[!NOTE]
   >
   >AEM biedt momenteel ondersteuning voor doorsturen van paginering (met `after`/`first` parameters).
   >
   >Achterwaartse paginering (gebruiken `before`/`last` parameters) wordt niet ondersteund.

## Sorteren {#sorting}

Sorteren kan alleen efficiënt zijn als alle sorteercriteria betrekking hebben op fragmenten op hoofdniveau.

Als de sorteervolgorde een of meer velden bevat die zich op een genest fragment bevinden, moeten alle fragmenten die het model op hoofdniveau delen, in het geheugen worden geladen. Deze stroom heeft een negatief effect op de prestaties.

>[!NOTE]
>
>Sorteren op velden op het hoogste niveau heeft ook een (zij het kleine) invloed op de prestaties.

## Best practices voor {#best-practices}

Het belangrijkste doel van alle optimalisaties is het verminderen van de aanvankelijke resultaatreeks. De hier vermelde beste praktijken verstrekken manieren om dit te doen. Zij kunnen (en moeten) worden gecombineerd.

### Alleen op eigenschappen op hoofdniveau filteren {#filter-top-level-properties-only}

Filteren op JCR-niveau werkt momenteel alleen voor fragmenten op hoofdniveau.

Als een filter de velden van een genest fragment aanpakt, moet AEM terugvallen naar het laden (in geheugen) van alle fragmenten die het onderliggende model delen.

U kunt dergelijke GraphQL-query&#39;s nog steeds optimaliseren door filterexpressies te combineren op velden van fragmenten op het hoogste niveau en op velden van geneste fragmenten met de opdracht [AND, operator](#logical-operations-in-filter-expressions).

### De inhoudsstructuur gebruiken {#use-content-structure}

In AEM wordt het als een goede praktijk beschouwd om de structuur van de gegevensopslagruimte te gebruiken om het bereik van de te verwerken inhoud te beperken.

Deze benadering toepassen op GraphQL-query&#39;s door een filter toe te passen op de `_path` veld van het fragment op hoofdniveau:

```graphql
{
  someList(filter: {
    _path: {
      _expressions: [ 
        {
          value: "/content/dam/some/sub/path/",
          _operator: STARTS_WITH
        }
      ]
    }
  }) {
    items {
      # ...
    }
  }
}
```

>[!NOTE]
>
>De navolgende `/` op `value` is vereist om de beste prestaties te behalen.

### Paginering gebruiken {#use-paging}

U kunt ook paginering gebruiken om de oorspronkelijke resultaatset te verkleinen. vooral als uw verzoeken geen het filtreren en het sorteren gebruiken.

Als u filtert of sorteert op geneste fragmenten, kunnen gepagineerde query&#39;s nog steeds traag zijn omdat AEM nog steeds grotere hoeveelheden fragmenten in het geheugen moet laden. Daarom als u het filtreren en het pagineren combineert, overweeg de regels voor het filtreren (zoals hierboven vermeld).

Voor pagineren is sorteren even belangrijk, omdat gepagineerde resultaten altijd worden gesorteerd - expliciet of impliciet.

Als u in de eerste plaats in slechts het terugwinnen van de eerste paar pagina&#39;s interesseert, is er geen significant verschil tussen het gebruiken van `...List` of `...Paginated` query&#39;s. Als uw toepassing echter meer dan één of twee pagina&#39;s wil lezen, moet u rekening houden met de `...Paginated` query&#39;s uitvoeren, aangezien deze vooral beter presteren bij de latere pagina&#39;s.

### Logische bewerkingen in filterexpressies {#logical-operations-in-filter-expressions}

Als u filtert op geneste fragmenten, kunt u nog steeds JCR-filtering toepassen door een bijbehorend filter op te geven voor een veld op hoofdniveau dat wordt gecombineerd met het `AND` operator.

Een typisch gebruik-geval moet het werkingsgebied van de vraag beperken gebruikend een filter op `_path` veld van het fragment op hoofdniveau. Vervolgens filtert u op aanvullende velden die zich op het bovenste niveau bevinden of op een genest fragment.

In dit geval worden de verschillende filterexpressies gecombineerd met `AND`. Daarom moet het filter op `_path` kan de oorspronkelijke resultaatset effectief beperken. Alle andere filters in velden op het hoogste niveau kunnen helpen om de oorspronkelijke resultaatset ook te reduceren, mits deze worden gecombineerd met `AND`.

Filterexpressies gecombineerd met `OR` kan niet worden geoptimaliseerd als het om geneste fragmenten gaat. Dergelijke `OR` expressies kunnen alleen worden geoptimaliseerd als *nee* geneste fragmenten zijn hierbij betrokken.

### Filteren op tekstvelden met meerdere regels wordt vermeden {#avoid-filtering-multiline-textfields}

De velden van een tekstveld met meerdere regels (html, markdown, plaintext, json) kunnen niet worden gefilterd via een JCR-query, omdat de inhoud van deze velden direct moet worden berekend.

Als u nog steeds moet filteren op een tekstveld met meerdere regels, kunt u de grootte van de oorspronkelijke resultaatset beperken door extra filterexpressies toe te voegen en deze te combineren `AND`. Het bereik beperken door te filteren op de `_path` het terrein is ook een goede aanpak .

### Filteren op virtuele velden vermijden {#avoid-filtering-virtual-fields}

Virtuele velden (de meeste velden beginnen met `_`) worden berekend terwijl een GraphQL-query wordt uitgevoerd en vallen daarom buiten het bereik van op JCR gebaseerde filtering.

Een belangrijke uitzondering is de `_path` veld, dat effectief kan worden gebruikt om de grootte van de oorspronkelijke resultaatset te beperken - als de inhoud dienovereenkomstig is gestructureerd (zie [De inhoudsstructuur gebruiken](#use-content-structure)).

### Filteren: Uitsluitingen {#filtering-exclusions}

Er zijn verschillende andere situaties waarin een filterexpressie niet op het JCR-niveau kan worden geëvalueerd (en daarom moet worden vermeden dat de beste prestaties worden bereikt):

* Filterexpressies op een `Float` waarde die de `_sensitiveness` filteroptie en waar `_sensitiveness` is ingesteld op een andere waarde dan `0.0` .

* Filterexpressies op een `String` waarde met behulp van de `_ignoreCase` filteroptie.

* Filteren op `null` waarden.

* Filters op arrays met `_apply: ALL_OR_EMPTY`.

* Filters op arrays met `_apply: INSTANCES`, `_instances: 0`.

* Filterexpressies met de `CONTAINS_NOT` operator.

* Filterexpressies op een `Calendar`, `Date`, of `Time` waarde die de `NOT_AT` operator.
