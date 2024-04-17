---
title: Rapporten ontwikkelen
description: Adobe Experience Manager (AEM) biedt een selectie van standaardrapporten op basis van een rapportagekader
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 3891150e-9972-4bbc-ad61-7f46a1f9bbb4
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '5177'
ht-degree: 0%

---


# Rapporten ontwikkelen {#developing-reports}

Adobe Experience Manager (AEM) biedt een selectie van [standaardrapporten](/help/sites-administering/reporting.md) de meeste daarvan zijn gebaseerd op een rapportagekader .

Met behulp van het framework kunt u deze standaardrapporten uitbreiden of uw eigen, nieuwe rapporten ontwikkelen. Het rapportagekader sluit nauw aan bij de bestaande CQ5-concepten en -beginselen, zodat ontwikkelaars hun bestaande kennis van CQ5 kunnen gebruiken als springplank voor het opstellen van rapporten.

Voor de standaardrapporten die bij AEM worden geleverd:

* Deze verslagen zijn gebaseerd op het rapportagekader:

   * [Componentrapport](/help/sites-administering/reporting.md#component-report)
   * [Rapport Paginaactiviteit](/help/sites-administering/reporting.md#page-activity-report)
   * [Gebruikersrapport](/help/sites-administering/reporting.md#user-report)
   * [Rapport voor werkstroominstantie](/help/sites-administering/reporting.md#workflow-instance-report)

* De volgende verslagen zijn gebaseerd op individuele beginselen en kunnen daarom niet worden uitgebreid:

   * [Schijfgebruik](/help/sites-administering/reporting.md#disk-usage)
   * [Health Check](/help/sites-administering/reporting.md#health-check)
   * [Workflowrapport](/help/sites-administering/reporting.md#workflow-report)

>[!NOTE]
>
>De zelfstudie [Uw eigen rapport maken - een voorbeeld](#creating-your-own-report-an-example) toont ook hoeveel van de onderstaande beginselen kunnen worden gebruikt.
>
>U kunt ook naar de standaardrapporten verwijzen om andere voorbeelden van implementatie te zien.

>[!NOTE]
>
>In de volgende voorbeelden en definities wordt de volgende notatie gebruikt:
>
>* Elke regel definieert een knooppunt of een eigenschap waarbij:
>  `N:<name> [<nodeType>]` : Beschrijft een knooppunt met de naam van `<*name*>` en knooppunttype van `<*nodeType*>`*.*
>  `P:<name> [<propertyType]` : Beschrijft een eigenschap met de naam van `<*name*>` en een type eigenschap van `<*propertyType*>`.
>  `P:<name> = <value>` : Beschrijft een eigenschap `<name>` die moet worden ingesteld op de waarde van `<value>`.
>
>* De inspringing toont de hiërarchische gebiedsdelen tussen de knopen.
>* Items gescheiden door | geeft een lijst met mogelijke items aan, bijvoorbeeld typen of namen, bijvoorbeeld `String|String[]` betekent dat de eigenschap String of String kan zijn[].
>
>* `[]` geeft een array weer, zoals String[] of een array van knooppunten zoals in de [Query-definitie](#query-definition).
>
>Tenzij anders vermeld zijn de standaardtypes:
>
>* Nodes - `nt:unstructured`
>* Eigenschappen - `String`

## Rapportagekader {#reporting-framework}

Het rapportagekader werkt aan de volgende beginselen:

* Het is volledig gebaseerd op resultaatreeksen die door een vraag zijn teruggekeerd die door CQ5 wordt uitgevoerd QueryBuilder.
* De resultaatreeks bepaalt de gegevens die in het rapport worden getoond. Elke rij in de resultaatreeks beantwoordt aan een rij in de tabelmening van het rapport.
* De verrichtingen beschikbaar voor uitvoering op de resultaatreeks lijken op concepten RDBMS; hoofdzakelijk *groeperen* en *samenvoeging*.

* De meeste gegevens worden opgehaald en verwerkt op de server.
* De klant is alleen verantwoordelijk voor de weergave van de vooraf verwerkte gegevens. Alleen kleine verwerkingstaken (bijvoorbeeld het maken van koppelingen in celinhoud) worden op de client uitgevoerd.

Het rapportagekader (geïllustreerd door de structuur van een standaardrapport) gebruikt de volgende bouwstenen, die door de verwerkingswachtrij worden gevoed:

![chlimage_1-248](assets/chlimage_1-248.png)

### Rapportpagina {#report-page}

De rapportpagina is:

* Een standaard CQ5-pagina.
* Op basis van een [standaard CQ5-sjabloon, geconfigureerd voor het rapport](#report-template).

### Rapportbasis {#report-base}

De [`reportbase` component](#report-base-component) vormt de basis voor elk verslag omdat het:

* De definitie van de optie [query](#the-query-and-data-retrieval) dat de onderliggende resultaatset van gegevens levert.

* Het is een aangepast alineasysteem dat alle kolommen bevat ( `columnbase`) toegevoegd aan het verslag.
* Bepaalt welke grafiektypes beschikbaar zijn en die momenteel actief zijn.
* Bepaalt de Edit dialoogdoos, die de gebruiker toestaat om bepaalde aspecten van het rapport te vormen.

### Kolombasis {#column-base}

Elke kolom is een instantie van de [`columnbase` component](#column-base-component) dat:

* Is een paragraaf die door parsys wordt gebruikt ( `reportbase`) van het desbetreffende verslag.
* Hiermee wordt de koppeling naar de [onderliggende resultatenset](#the-query-and-data-retrieval). Met andere woorden, het definieert de specifieke gegevens waarnaar in deze resultaatset wordt verwezen, en hoe deze worden verwerkt.
* Hiermee behoudt u aanvullende definities, zoals de beschikbare aggregaten en filters, en eventuele standaardwaarden.

### De query en het ophalen van gegevens {#the-query-and-data-retrieval}

De query:

* Is gedefinieerd als onderdeel van het [`reportbase`](#report-base) component.
* Is gebaseerd op [CQ QueryBuilder](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/search/QueryBuilder.html).
* Haalt de gegevens op die als basis voor het rapport worden gebruikt. Elke rij van de resultaatreeks (lijst) is gebonden aan een knoop zoals teruggekeerd door de vraag. Specifieke informatie voor [afzonderlijke kolommen](#column-base-component) wordt vervolgens uit deze gegevensset opgehaald.

* Bestaat gewoonlijk uit:

   * Een hoofdpad.

     Hiermee wordt de substructuur van de gegevensopslagruimte aangegeven die moet worden doorzocht.

     Om de invloed op de prestaties tot een minimum te beperken, is het raadzaam (probeer) de query te beperken tot een specifieke substructuur van de repository. Het hoofdpad kan vooraf worden gedefinieerd in het dialoogvenster [rapportsjabloon](#report-template) of ingesteld door de gebruiker in de [Dialoogvenster Configuratie (Bewerken)](#configuration-dialog).

   * [Een of meer criteria](#query-definition).

     Deze worden opgelegd om de (aanvankelijke) resultaatreeks te produceren; zij omvatten, bijvoorbeeld, beperkingen op het knooptype, of bezitsbeperkingen.

**Het belangrijkste punt hier is dat elke enige knoop die in de resultaatreeks van de vraag wordt teruggekeerd wordt gebruikt om één enkele rij op het rapport (zo een 1:1 verhouding) te produceren.**

De ontwikkelaar moet ervoor zorgen dat de vraag die voor een rapport wordt bepaald een knoop terugkeert die aangewezen voor dat rapport wordt geplaatst. Nochtans, te hoeven de knoop zelf niet om alle vereiste informatie te houden, kan dit ook uit ouder en/of kindknopen worden afgeleid. De query die bijvoorbeeld wordt gebruikt voor de [Gebruikersrapport](/help/sites-administering/reporting.md#user-report) selecteert knooppunten op basis van het knooppunttype (in dit geval `rep:user`). Nochtans, nemen de meeste kolommen op dit rapport hun gegevens niet direct van deze knopen, maar van de kindknopen `profile`.

### Bezig met verwerken wachtrij {#processing-queue}

De [query](#the-query-and-data-retrieval) keert een resultaatreeks gegevens terug die als rijen op het rapport moeten worden getoond. Elke rij in de resultaatset wordt verwerkt (server-side), in [verschillende fasen](#phases-of-the-processing-queue), voordat deze naar de client wordt overgedragen voor weergave op het rapport.

Hierdoor is het mogelijk:

* Waarden extraheren en afleiden van de onderliggende resultaatset.

  U kunt bijvoorbeeld twee eigenschapswaarden als één waarde verwerken door het verschil tussen de twee waarden te berekenen.

* Oplossen van geëxtraheerde waarden. Dit kan op verschillende manieren worden gedaan.

  Paden kunnen bijvoorbeeld worden toegewezen aan een titel (zoals in de meer leesbare inhoud van de respectievelijke *jcr:titel* eigenschap).

* Filters toepassen op verschillende punten.
* Indien nodig samengestelde waarden maken.

  Bijvoorbeeld bestaande uit een tekst die aan de gebruiker wordt getoond, een waarde die voor het sorteren en een extra URL moet worden gebruikt die (op de cliëntkant) voor het creëren van een verbinding wordt gebruikt.

#### Workflow van de verwerkingswachtrij {#workflow-of-the-processing-queue}

De volgende workflow vertegenwoordigt de verwerkingswachtrij:

![chlimage_1-249](assets/chlimage_1-249.png)

#### Fasen van de Verwerkingswachtrij {#phases-of-the-processing-queue}

Waar de gedetailleerde stappen en elementen zijn:

1. Hiermee transformeert u de resultaten die door de [initiële query (rapportbase)](#query-definition) in de basisresultaatset met behulp van value extractors.

   De waarde-extractoren worden automatisch gekozen afhankelijk van de [kolomtype](#column-specific-definitions). Deze worden gebruikt voor het lezen van waarden van de onderliggende JCR-query en het maken van een resultaatset op basis daarvan; waarna verdere verwerking kan worden toegepast. Bijvoorbeeld voor `diff` type, leest de value extractor twee eigenschappen, berekent de enkele waarde die vervolgens aan de result set wordt toegevoegd. De waarde-extractors kunnen niet worden geconfigureerd.

1. Naar die oorspronkelijke resultaatset, met onbewerkte gegevens, [initiële filtering](#column-specific-definitions) (*ruw* fase) wordt toegepast.

1. Waarden zijn [voorbewerkt](#processing-queue); zoals gedefinieerd voor de *toepassen* fase.

1. [Filteren](#column-specific-definitions) (toegewezen aan de *voorbewerkt* fase) wordt uitgevoerd op de vooraf verwerkte waarden.

1. Waarden worden opgelost; volgens de [gedefinieerde oplosser](#processing-queue).
1. [Filteren](#column-specific-definitions) (toegewezen aan de *opgelost* phase) wordt uitgevoerd op de opgeloste waarden.

1. Gegevens zijn [gegroepeerd en samengevoegd](#column-specific-definitions).
1. Arraygegevens worden omgezet in een (op tekenreeks gebaseerde) lijst.

   Dit is een impliciete stap die een resultaat met meerdere waarden omzet in een lijst die kan worden weergegeven; het is vereist voor (niet-geaggregeerde) celwaarden die zijn gebaseerd op JCR-eigenschappen met meerdere waarden.

1. Waarden zijn opnieuw [voorbewerkt](#processing-queue); zoals gedefinieerd voor de *afterApply* fase.

1. Gegevens worden gesorteerd.
1. De verwerkte gegevens worden naar de client overgedragen.

>[!NOTE]
>
>De eerste query die de resultaatset van de basisgegevens retourneert, wordt gedefinieerd op de `reportbase` component.
>
>Andere elementen van de verwerkingswachtrij worden gedefinieerd in het dialoogvenster `columnbase` componenten.

## Constructie en configuratie van rapporten {#report-construction-and-configuration}

Het volgende is nodig om een rapport te construeren en te vormen:

* a [plaats voor de definitie van uw rapportcomponenten](#location-of-report-components)
* a [`reportbase` component](#report-base-component)
* één of meer, [`columnbase` componenten](#column-base-component)
* a [pagina-component](#page-component)
* a [rapportontwerp](#report-design)
* a [rapportsjabloon](#report-template)

### Locatie van rapportcomponenten {#location-of-report-components}

De standaardrapporteringscomponenten worden aangehouden onder `/libs/cq/reporting/components`.

Het wordt echter aanbevolen deze knooppunten niet bij te werken, maar zelf componentknooppunten te maken onder `/apps/cq/reporting/components` of, indien nodig, `/apps/<yourProject>/reports/components`.

Waar (als voorbeeld):

```
N:apps
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:components [sling:Folder]
```

Onder dit, creeert u de wortel voor uw rapport en onder dit, de component van de rapportbasis en de componenten van de kolombasis:

```
N:apps
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:components [sling:Folder]
                N:<reportname> [sling:Folder]
                        N:<reportname> [cq:Component]  // report base component
                        N:<columnname> [cq:Component]  // column base component
```

### Pagina-component {#page-component}

Een rapportpagina moet de `sling:resourceType` van `/libs/cq/reporting/components/reportpage`.

Een aangepaste pagina-component is niet nodig (gewoonlijk).

## Basiscomponent rapporteren {#report-base-component}

Elk rapporttype vereist een containercomponent die is afgeleid van `/libs/cq/reporting/components/reportbase`.

Deze component fungeert als container voor het rapport als geheel en biedt informatie voor:

* De [querydefinitie](#query-definition).
* An [(optioneel) dialoogvenster](#configuration-dialog) voor het vormen van het rapport.
* Alle [Grafieken](#chart-definitions) die in het verslag zijn opgenomen.

```
N:<reportname> [cq:Component]
    P:sling:resourceSuperType = "cq/reporting/components/reportbase"
    N:charting
    N:dialog [cq:Dialog]
    N:queryBuilder
```

### Query-definitie {#query-definition}

```xml
N:queryBuilder
    N:propertyConstraints
    [
        N:<name> // array of nodes (name irrelevant), each with the following properties:
            P:name
            P:value
    ]
    P:nodeTypes [String|String[]]
    P:mandatoryProperties [String|String[]
  ]
```

* `propertyConstraints`

  Hiermee beperkt u het resultaat dat is ingesteld tot knooppunten met specifieke eigenschappen met specifieke waarden. Als de veelvoudige beperkingen worden gespecificeerd, moet de knoop aan elk van hen (EN verrichting) voldoen.

  Bijvoorbeeld:

  ```
  N:propertyConstraints
   [
   N:0
   P:sling:resourceType
   P:foundation/components/textimage
   N:1
   P:jcr:modifiedBy
   P:admin
   ]
  ```

  Alles retourneren `textimage` componenten die het laatst zijn gewijzigd door de `admin` gebruiker.

* `nodeTypes`

  Wordt gebruikt om het resultaat te beperken tot de opgegeven knooppunttypen. U kunt meerdere knooppunttypen opgeven.

* `mandatoryProperties`

  Beperkt het resultaat dat is ingesteld tot knooppunten die *alles* de opgegeven eigenschappen. De waarde van de eigenschappen wordt niet verwerkt.

Alles is optioneel en kan zo nodig worden gecombineerd, maar u moet ten minste één element definiëren.

### Diagramdefinities {#chart-definitions}

```xml
N:charting
    N:settings
        N:active [cq:WidgetCollection]
        [
            N:<name> // array of nodes, each with the following property
                P:id   // must match the id of a child node of definitions
        ]
    N:definitions [cq:WidgetCollection]
    [
        N:<name> // array of nodes, each with the following properties
            P:id
            P:type
            // additional, chart type specific configurations
    ]
```

* `settings`

  Bevat definities voor de actieve grafieken.

   * `active`

     Aangezien er meerdere instellingen kunnen worden gedefinieerd, kunt u dit gebruiken om te definiëren welke momenteel actief zijn. Deze worden gedefinieerd door een array van knooppunten (er is geen verplichte naamgevingsconventie voor deze knooppunten, maar de standaardrapporten gebruiken vaak `0`, `1`.. `x`), elk met de volgende eigenschap:

      * `id`

        Identificatie voor de actieve diagrammen. Dit moet identiteitskaart van één van de grafiek aanpassen `definitions`.

* `definitions`

  Bepaalt de grafiektypes die potentieel voor het rapport beschikbaar zijn. De `definitions` wordt gespecificeerd door de `active` instellingen.

  De definities worden opgegeven met behulp van een array van knooppunten (vaak ook wel `0`, `1`.. `x`), elk met de volgende eigenschappen:

   * `id`

     De identificatie van het diagram.

   * `type`

     Het type beschikbare grafiek. Selecteren uit:

      * `pie`
Cirkeldiagram. Alleen gegenereerd op basis van huidige gegevens.

      * `lineseries`
Reeks lijnen (verbindende punten die de daadwerkelijke momentopnamen vertegenwoordigen). Alleen gegenereerd op basis van historische gegevens.

   * Er zijn aanvullende eigenschappen beschikbaar, afhankelijk van het diagramtype:

      * voor het diagramtype `pie`:

         * `maxRadius` ( `Double/Long`)

           De maximumstraal die voor het cirkeldiagram wordt toegestaan; daarom de maximumgrootte die voor de grafiek (zonder legenda) wordt toegestaan. Genegeerd als `fixedRadius` is gedefinieerd.

         * `minRadius` ( `Double/Long`)

           De minimale straal die is toegestaan voor het cirkeldiagram. Genegeerd als `fixedRadius` is gedefinieerd.

         * `fixedRadius` ( `Double/Long`) Hiermee definieert u een vaste straal voor het cirkeldiagram.

      * voor het diagramtype [`lineseries`](/help/sites-administering/reporting.md#display-limits):

         * `totals` ( `Boolean`)

           Waar (true) als een extra regel de **Totaal** worden weergegeven.
standaard: `false`

         * `series` ( `Long`)

           Aantal weer te geven lijnen/reeksen.
standaard: `9` (dit is ook het toegestane maximum)

         * `hoverLimit` ( `Long`)

           Maximumaantal geaggregeerde momentopnamen (punten die op elke horizontale lijn worden weergegeven en die verschillende waarden vertegenwoordigen) waarvoor pop-ups moeten worden weergegeven. Dat wil zeggen, wanneer de gebruiker de muis boven een bepaalde waarde of een bijbehorend label in de diagramlegenda houdt.

           standaard: `35` (Er worden dus helemaal geen pop-ups weergegeven als er meer dan 35 verschillende waarden van toepassing zijn voor de huidige diagraminstellingen).

           Er geldt een extra limiet van tien pop-ups die parallel kunnen worden weergegeven (er kunnen meerdere pop-ups worden weergegeven wanneer de muisaanwijzer op de legenda wordt geplaatst).

### Dialoogvenster Configuratie {#configuration-dialog}

Elk rapport kan een configuratiedialoog hebben, toestaand de gebruiker om diverse parameters voor het rapport te specificeren. Dit dialoogvenster is toegankelijk via het **Bewerken** als de rapportpagina is geopend.

Dit dialoogvenster is een standaard-CQ [dialoogvenster](/help/sites-developing/components-basics.md#dialogs) en kan als dusdanig worden gevormd (zie [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog) voor meer informatie ) .

Een voorbeelddialoogvenster kan er als volgt uitzien:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    jcr:primaryType="cq:Dialog"
    height="{Long}424">
    <items jcr:primaryType="cq:WidgetCollection">
        <props jcr:primaryType="cq:Panel">
            <items jcr:primaryType="cq:WidgetCollection">
                <title
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/title.infinity.json"
                    xtype="cqinclude"/>
                <description
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/description.infinity.json"
                    xtype="cqinclude"/>
                <rootPath
                    jcr:primaryType="cq:Widget"
                    fieldLabel="Root path"
                    name="./report/rootPath"
                    rootPath=""
                    rootTitle="Repository root"
                    xtype="pathfield"/>
                <processing
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/processing.infinity.json"
                    xtype="cqinclude"/>
                <scheduling
                    jcr:primaryType="cq:Widget"
                    path="/libs/cq/reporting/components/commons/scheduling.infinity.json"
                    xtype="cqinclude"/>
            </items>
        </props>
    </items>
</jcr:root>
```

Verschillende vooraf geconfigureerde componenten worden opgegeven. Naar deze componenten kan in het dialoogvenster worden verwezen met de `xtype` eigenschap met een waarde van `cqinclude`:

* **`title`**

  `/libs/cq/reporting/components/commons/title`

  Het gebied van de tekst om de rapporttitel te bepalen.

* **`description`**

  `/libs/cq/reporting/components/commons/description`

  Het gebied van de tekst om de rapportbeschrijving te bepalen.

* **`processing`**

  `/libs/cq/reporting/components/commons/processing`

  Selector voor de verwerkingsmodus van het rapport (gegevens handmatig/automatisch laden).

* **`scheduling`**

  `/libs/cq/reporting/components/commons/scheduling`

  Kiezer voor het plannen van momentopnamen voor de historische grafiek.

>[!NOTE]
>
>De componenten waarnaar wordt verwezen, moeten worden opgenomen met behulp van de `.infinity.json` achtervoegsel (zie voorbeeld hierboven).

### Hoofdpad {#root-path}

Ook, kan een wortelweg voor het rapport worden bepaald:

* **`rootPath`**

  Dit beperkt het rapport tot een bepaalde sectie (boom of subboom) van de bewaarplaats, die voor prestatiesoptimalisering wordt geadviseerd. Het hoofdpad wordt opgegeven door de `rootPath` eigendom van de `report` knoop van elke rapportpagina (die van het malplaatje bij paginaverwezenlijking wordt genomen).

  Deze kan worden gespecificeerd door:

   * de [rapportsjabloon](#report-template) (Als een vaste waarde of als standaardwaarde voor het configuratiedialoogvenster).
   * de gebruiker (met deze parameter)

## Basiscomponent kolom {#column-base-component}

Voor elk kolomtype is een component vereist die is afgeleid van `/libs/cq/reporting/components/columnbase`.

Een kolomcomponent definieert een combinatie van het volgende:

* De [Kolomspecifieke query](#column-specific-query) configuratie.
* De [Resolvers en voorbewerking](#resolvers-and-preprocessing).
* De [Kolomspecifieke definities](#column-specific-definitions) (zoals filters en aggregaten; `definitions` onderliggende node).
* [Standaardwaarden kolom](#column-default-values).
* De [Clientfilter](#client-filter) om de informatie voor vertoning uit de gegevens te halen die door de server zijn teruggekeerd.
* Een kolomcomponent moet ook een geschikt exemplaar van `cq:editConfig`. om de [Gebeurtenissen en handelingen](#events-and-actions) vereist.
* De configuratie voor [generieke kolommen](#generic-columns).

```
N:<columnname> [cq:Component]
    P:componentGroup
    P:jcr:title
    P:sling:resourceSuperType = "cq/reporting/components/columnbase"
    N:cq:editConfig [cq:EditConfig] // <a href="#events-and-actions">Events and Actions</a>
    N:defaults // <a href="#column-default-values">Column Default Values</a>
    N:definitions
      N:queryBuilder // <a href="#column-specific-query">Column Specific Query</a>
        P:property [String|String[]] // Column Specific Query
        P:subPath // Column Specific Query
        P:secondaryProperty [String|String[]] // Column Specific Query
        P:secondarySubPath // Column Specific Query
      N:data
        P:clientFilter [String] // <a href="#client-filter">Client Filter</a>
        P:resolver // <a href="#resolvers-and-preprocessing">Resolvers and Preprocessing</a>
        N:resolverConfig // Resolvers and Preprocessing
        N:preprocessing // Resolvers and Preprocessing
      P:type // <a href="#column-specific-definitions">Column Specific Definitions</a>
      P:groupable [Boolean] // Column Specific Definitions
      N:filters [cq:WidgetCollection] // Column Specific Definitions
      N:aggregates [cq:WidgetCollection] // Column Specific Definitions
```

Zie ook [Uw nieuwe rapport definiëren](#defining-your-new-report).

### Kolomspecifieke query {#column-specific-query}

Hiermee wordt de specifieke gegevensextractie gedefinieerd (op basis van de [resultaatset rapportgegevens](#the-query-and-data-retrieval)) voor gebruik in de afzonderlijke kolom.

```xml
N:definitions
    N:queryBuilder
        P:property [String|String[]]
        P:subPath
        P:secondaryProperty [String|String[]]
        P:secondarySubPath
```

* `property`

  Definieert de eigenschap die moet worden gebruikt voor het berekenen van de werkelijke celwaarde.

  Wanneer een eigenschap wordt gedefinieerd als String[]Er worden meerdere eigenschappen gescand (achter elkaar) om de werkelijke waarde te vinden.

  Als er bijvoorbeeld:

  `property = [ "jcr:lastModified", "jcr:created" ]`

  De corresponderende waarde-extractor (die hier wordt beheerd):

   * Controleert of er een jcr:lastModified-eigenschap beschikbaar is en zo ja, gebruik deze.
   * Als er geen eigenschap jcr:lastModified beschikbaar is, wordt in plaats daarvan de inhoud van jcr:created gebruikt.

* `subPath`

  Als het resultaat niet op de knoop is die door de vraag is teruggekeerd, `subPath` definieert waar de eigenschap zich bevindt.

* `secondaryProperty`

  Een tweede eigenschap die moet worden gebruikt voor het berekenen van de werkelijke celwaarde. Deze definitie wordt alleen gebruikt voor bepaalde kolomtypen (diff en sortable).

  Bijvoorbeeld, als er het Rapport van de Instanties van het Werkschema is, wordt het gespecificeerde bezit gebruikt om de daadwerkelijke waarde van het tijdverschil (in milliseconden) tussen begin en eindtijden op te slaan.

* `secondarySubPath`

  Vergelijkbaar met subpad, wanneer `secondaryProperty` wordt gebruikt.

Gewoonlijk alleen `property` wordt gebruikt.

### Clientfilter {#client-filter}

Het clientfilter extraheert de informatie die moet worden weergegeven uit de gegevens die door de server worden geretourneerd.

>[!NOTE]
>
>Dit filter wordt op de client uitgevoerd nadat de verwerking op de server volledig is uitgevoerd.

```xml
N:definitions
    N:data
        P:clientFilter [String]
```

De `clientFilter` is een JavaScript-functie die:

* als input, ontvangt één parameter; de gegevens die van de server (zo volledig preprocessing) zijn teruggekeerd
* als output, keert de gefilterde (verwerkte) waarde terug; de gegevens die uit de inputinformatie worden gehaald of worden afgeleid

In het volgende voorbeeld wordt het overeenkomende paginapad uit een deelpad geëxtraheerd:

```
function(v) {
    var sepPos = v.lastIndexOf('/jcr:content');
    if (sepPos < 0) {
        return v;
    }
    return v.substring(sepPos + '/jcr:content'.length, v.length);
}
```

### Resolvers en voorbewerking {#resolvers-and-preprocessing}

De [verwerkingswachtrij](#processing-queue) bepaalt de diverse oplosmiddelen en vormt preprocessing:

```xml
N:definitions
    N:data
        P:resolver
        N:resolverConfig
        N:preprocessing
            N:apply
            N:applyAfter
```

* `resolver`

  Definieert de oplosser die moet worden gebruikt. De volgende oplosmiddelen zijn beschikbaar:

   * `const`

     Wijst waarden toe aan andere waarden; dit wordt bijvoorbeeld gebruikt om constanten op te lossen zoals `en` aan de equivalente waarde `English`.

   * `default`

     De standaardoplosser. Dit is een nepoplosser die eigenlijk niets oplost.

   * `page`

     Hiermee wordt een padwaarde omgezet in het pad van de juiste pagina, nauwkeuriger naar de bijbehorende pagina `jcr:content` knooppunt. Bijvoorbeeld: `/content/.../page/jcr:content/par/xyz` is opgelost voor `/content/.../page/jcr:content`.

   * `path`

     Hiermee wordt een padwaarde omgezet door optioneel een subpad toe te voegen en de werkelijke waarde van een eigenschap van het knooppunt te nemen (zoals gedefinieerd door `resolverConfig`) op het opgeloste pad. Bijvoorbeeld een `path` van `/content/.../page/jcr:content` kan worden opgelost tot de inhoud van de `jcr:title` eigenschap, betekent dit dat een paginapad wordt omgezet naar de paginatitel.

   * `pathextension`

     Hiermee lost u een waarde op door een pad vooraf in te stellen en de werkelijke waarde van een eigenschap van het knooppunt op het opgeloste pad te nemen. Een waarde `de` kan worden voorafgegaan door een pad zoals `/libs/wcm/core/resources/languages`, waarbij de waarde wordt overgenomen van de eigenschap `language`om de landcode op te lossen `de` aan de taalbeschrijving `German`.

* `resolverConfig`

  Verstrekt definities voor resolver. Welke opties beschikbaar zijn, is afhankelijk van de `resolver` geselecteerd:

   * `const`

     Gebruik eigenschappen om de constanten voor het omzetten op te geven. De naam van de eigenschap definieert de constante die moet worden omgezet; de waarde van de eigenschap definieert de herstelde waarde.

     Een eigenschap met **Naam**= `1` en **Waarde** `=One` Hiermee wordt 1 naar 1 omgezet.

   * `default`

     Geen configuratie beschikbaar.

   * `page`

      * `propertyName` (optioneel)

        Definieert de naam van de eigenschap die moet worden gebruikt voor het omzetten van de waarde. Indien niet opgegeven, wordt de standaardwaarde van *jcr:titel* (de paginatitel) wordt gebruikt; voor de `page` resolver, dit betekent dat eerst het pad wordt omgezet naar het paginapad en vervolgens verder wordt omgezet naar de paginatitel.

   * `path`

      * `propertyName` (optioneel)

        Specifies the name of the property that should be used for resolving the value. Indien niet opgegeven, wordt de standaardwaarde van `jcr:title` wordt gebruikt.

      * `subPath` (optioneel)

        Deze eigenschap kan worden gebruikt om een achtervoegsel op te geven dat aan het pad moet worden toegevoegd voordat de waarde wordt omgezet.

   * `pathextension`

      * `path` (verplicht)

        Definieert het pad dat moet worden voorafgegaan.

      * `propertyName` (verplicht)

        Definieert de eigenschap op het omgezette pad waar de werkelijke waarde zich bevindt.

      * `i18n` (optioneel; type Boolean)

        Hiermee wordt bepaald of de waarde moet worden omgezet *geïnternationaliseerd* (dat wil zeggen, [Internationale services van CQ5](/help/sites-administering/tc-manage.md)).

* `preprocessing`

  Voorbewerking is optioneel en kan (afzonderlijk) aan de verwerkingsfasen worden gebonden *toepassen* of *applyAfter*:

   * `apply`

     De eerste voorbewerkingsfase ([stap 3 in de weergave van de verwerkingswachtrij](#processing-queue)).

   * `applyAfter`

     Toepassen na voorbewerken ([stap 9 in de weergave van de verwerkingswachtrij](#processing-queue)).

#### Resolvers {#resolvers}

De oplosmiddelen worden gebruikt om de vereiste informatie te halen. Voorbeelden van de verschillende oplosmiddelen zijn:

**Const**

Met het volgende wordt een constante waarde van `VersionCreated` naar de tekenreeks `New version created`.

Zie `/libs/cq/reporting/components/auditreport/typecol/definitions/data`.

```xml
N:data
    P:resolver=const
    N:resolverConfig
        P:VersionCreated="New version created"
```

**Pagina**

Hiermee wordt een padwaarde omgezet in de eigenschap jcr:description op het knooppunt jcr:content (child) van de bijbehorende pagina.

Zie `/libs/cq/reporting/components/compreport/pagecol/definitions/data`.

```xml
N:data
    P:resolver=page
    N:resolverConfig
        P:propertyName="jcr:description"
```

**Pad**

Met het volgende wordt een pad van `/content/.../page` de inhoud van de `jcr:title` eigenschap, betekent dit dat een paginapad wordt omgezet naar de paginatitel.

Zie `/libs/cq/reporting/components/auditreport/pagecol/definitions/data`.

```xml
N:data
    P:resolver=path
    N:resolverConfig
        P:propertyName="jcr:title"
        P:subPath="/jcr:content"
```

**Padextensie**

De volgende notatie voegt een waarde aan `de` met de padextensie `/libs/wcm/core/resources/languages`, neemt dan de waarde van het bezit `language`om de landcode op te lossen `de` aan de taalbeschrijving `German`.

Zie `/libs/cq/reporting/components/userreport/languagecol/definitions/data`.

```xml
N:data
    P:resolver=pathextension
    N:resolverConfig
        P:path="/libs/wcm/core/resources/languages"
        P:propertyName="language"
```

#### Voorbewerken {#preprocessing}

De `preprocessing` een definitie kan worden toegepast op:

* oorspronkelijke waarde:

  De voorbewerkingsdefinitie voor de oorspronkelijke waarde wordt opgegeven op `apply` en/of `applyAfter` rechtstreeks.

* waarde in geaggregeerde toestand:

  Indien nodig kan voor elke aggregatie een aparte definitie worden gegeven.

  Om expliciete voorbewerking voor geaggregeerde waarden te specificeren, moeten de definities van voorbewerking op een respectieve `aggregated` onderliggende node ( `apply/aggregated`, `applyAfter/aggregated`). Als expliciete voorbewerking voor verschillende aggregaten wordt vereist, is de preprocessing definitie op een kindknoop met de naam van het respectieve aggregaat (bijvoorbeeld `apply/aggregated/min/max` of andere aggregaten).

U kunt een van de volgende twee opties opgeven om tijdens de voorbehandeling te gebruiken:

* [patronen zoeken en vervangen](#preprocessing-find-and-replace-patterns)
Wanneer dit wordt gevonden, wordt het opgegeven patroon (dat wordt gedefinieerd als een reguliere expressie) vervangen door een ander patroon. Dit kan bijvoorbeeld worden gebruikt om een subtekenreeks van het origineel te extraheren.

* [gegevenstypeopmaakprogramma&#39;s](#preprocessing-data-type-formatters)

  Zet een numerieke waarde om in een relatieve tekenreeks; de waarde &quot;die een tijdsverschil van één uur vertegenwoordigt, wordt bijvoorbeeld omgezet in een tekenreeks zoals `1:24PM (1 hour ago)`.

Bijvoorbeeld:

```xml
N:definitions
    N:data
        N:preprocessing
            N:apply|applyAfter
                P:pattern         // regex
                P:replace         // replacement for regex
                // and/or
                P:format          // data type formatter
```

#### Voorbewerken - Patronen zoeken en vervangen {#preprocessing-find-and-replace-patterns}

Voor voorbewerken kunt u een `pattern` (gedefinieerd als een [reguliere expressie](https://en.wikipedia.org/wiki/Regular_expression) of regex) die zich bevindt en vervolgens wordt vervangen door de `replace` patroon:

* `pattern`

  De reguliere expressie die wordt gebruikt om een subtekenreeks te zoeken.

* `replace`

  De tekenreeks, of representatie van de tekenreeks, die wordt gebruikt als vervanging voor de oorspronkelijke tekenreeks. Dit vertegenwoordigt vaak een subtekenreeks van de tekenreeks die zich bevindt door de reguliere expressie `pattern`.

Een voorbeeldvervanging kan als worden verdeeld:

* Voor het knooppunt `definitions/data/preprocessing/apply` met de volgende twee eigenschappen:

   * `pattern`: `(.*)(/jcr:content)(/|$)(.*)`
   * `replace`: `$1`

* Een tekenreeks die aankomt als:

   * `/content/geometrixx/en/services/jcr:content/par/text`

* Verdeeld in vier secties:

   * `$1` - `(.*)` - `/content/geometrixx/en/services`
   * `$2` - `(/jcr:content)` - `/jcr:content`
   * `$3` - `(/|$)` - `/`
   * `$4` - `(.*)` - `par/text`

* En vervangen door de tekenreeks die wordt vertegenwoordigd door `$1`:

   * `/content/geometrixx/en/services`

#### voorbewerken - Formatters voor gegevenstypen {#preprocessing-data-type-formatters}

Deze formatters zetten een numerieke waarde in een relatieve koord om.

Dit kan bijvoorbeeld worden gebruikt voor een tijdkolom die `min`, `avg` en `max` aggregaten. Als `min`/ `avg`/ `max` aggregaten worden weergegeven als een *tijdsverschil* (bijvoorbeeld `10 days ago`), is een gegevensformatter vereist. Hiervoor wordt `datedelta` formatter wordt toegepast op `min`/ `avg`/ `max` geaggregeerde waarden. Indien een `count` aggregaat is ook beschikbaar, dit vereist geen formatter, evenals de originele waarde.

Momenteel zijn de beschikbare gegevenstypeformatters:

* `format`

  Formatter voor gegevenstype:

   * `duration`

     De duur is de tijdspanne tussen twee bepaalde data. Bijvoorbeeld het begin en einde van een werkstroomactie die één uur duurde, te beginnen bij 13/13/11 11:23u en één uur later te eindigen bij 13/11 12:23u.

     Een numerieke waarde (geïnterpreteerd als milliseconden) wordt omgezet in een duurtekenreeks, bijvoorbeeld `30000` is opgemaakt als * `30s`.*

   * `datedelta`

     Datadelta is de tijdspanwijdte tussen een datum in het verleden tot &quot;nu&quot;(zodat heeft het een verschillend resultaat als het rapport op een later punt in tijd wordt bekeken).

     De numerieke waarde (geïnterpreteerd als een tijdverschil in dagen) wordt omgezet in een relatieve datumtekenreeks. 1 is bijvoorbeeld een dag geleden opgemaakt.

In het volgende voorbeeld wordt `datedelta` opmaak voor `min` en `max` aggregaten:

```xml
N:definitions
    N:data
        N:preprocessing
            N:apply
                N:aggregated
                    N:min
                        P:format = "datedelta"
                    N:max
                        P:format = "datedelta"
```

### Kolomspecifieke definities {#column-specific-definitions}

De kolomspecifieke definities definiëren de filters en aggregaten die beschikbaar zijn voor die kolom.

```xml
N:definitions
    P:type
    P:groupable [Boolean]
    N:filters [cq:WidgetCollection]
    [
        N:<name> // array of nodes (names irrelevant) with the following properties:
            P:filterType
            P:id
            P:phase
    ]
    N:aggregates [cq:WidgetCollection]
    [
        N:<name> // array of nodes (names irrelevant) with the following properties:
            P:text
            P:type
    ]
```

* `type`

  De volgende opties zijn beschikbaar als standaardopties:

   * `string`
   * `number`
   * `int`
   * `date`
   * `diff`
   * `timeslot`

     Wordt gebruikt voor het extraheren van delen van een datum die nodig is voor aggregatie (bijvoorbeeld groep per jaar om gegevens voor elk jaar te verzamelen).

   * `sortable`

     Wordt gebruikt voor waarden die verschillende waarden gebruiken (zoals die uit verschillende eigenschappen zijn opgehaald) voor het sorteren en weergeven.

  Bovendien kan elk van de bovenstaande waarden worden gedefinieerd als een meerwaarde, bijvoorbeeld `string[]` definieert een array van tekenreeksen.

  De waarde-extractor wordt gekozen door het kolomtype. Als een waarde-extractor beschikbaar is voor een kolomtype, wordt deze extractor gebruikt. Anders wordt de standaardwaarde voor de extractor gebruikt.

  Een type kan (optioneel) een parameter nemen. Bijvoorbeeld: `timeslot:year` extraheert het jaar uit een datumveld. Typen met de bijbehorende parameters:

   * `timeslot` - De waarden zijn vergelijkbaar met de overeenkomstige constanten van `java.utils.Calendar`.

      * `timeslot:year` - `Calendar.YEAR`
      * `timeslot:month-of-year` - `Calendar.MONTH`
      * `timeslot:week-of-year` - `Calendar.WEEK_OF_YEAR`
      * `timeslot:day-of-month` - `Calendar.DAY_OF_MONTH`
      * `timeslot:day-of-week` - `Calendar.DAY_OF_WEEK`
      * `timeslot:day-of-year` - `Calendar.DAY_OF_YEAR`
      * `timeslot:hour-of-day` - `Calendar.HOUR_OF_DAY`
      * `timeslot:minute-of-hour` - `Calendar.MINUTE`

* `groupable`

  Bepaalt of het rapport door deze kolom kan worden gegroepeerd.

* `filters`

  Filterdefinities.

   * `filterType`

     Beschikbare filters zijn:

      * `string`

        Een op tekenreeks gebaseerd filter.

   * `id`

     Filter-id.

   * `phase`

     Beschikbare fasen:

      * `raw`

        Het filter wordt toegepast op onbewerkte gegevens.

      * `preprocessed`

        Het filter wordt toegepast op vooraf verwerkte gegevens.

      * `resolved`

        Het filter wordt toegepast op omgezette gegevens.

* `aggregates`

  Samengevoegde definities.

   * `text`

     De tekstnaam van het aggregaat. Indien `text` niet wordt gespecificeerd, dan neemt het de standaardbeschrijving van het aggregaat. Bijvoorbeeld: `minimum` wordt gebruikt voor de `min` aggregaat.

   * `type`

     Samengevoegde tekst. Beschikbare aggregaten zijn:

      * `count`

        Telt het aantal rijen.

      * `count-nonempty`

        Telt het aantal niet-lege rijen.

      * `min`

        De minimumwaarde wordt opgegeven.

      * `max`

        Dit levert de maximumwaarde op.

      * `average`

        Het levert de gemiddelde waarde op.

      * `sum`

        Het verstrekt de som alle waarden.

      * `median`

        De mediaanwaarde wordt weergegeven.

      * `percentile95`

        Gebruikt het 95e percentiel van alle waarden.

### Standaardwaarden kolom {#column-default-values}

Definieert standaardwaarden voor de kolom:

```xml
N:defaults
    P:aggregate
```

* `aggregate`

  Geldig `aggregate` waarden zijn gelijk aan die voor `type` krachtens `aggregates` (zie [Kolomspecifieke definities (definities - filters / aggregaten)](#column-specific-definitions) ).

### Gebeurtenissen en handelingen {#events-and-actions}

Edit Configuration definieert de gebeurtenissen die de listeners nodig hebben om te detecteren en de handelingen die moeten worden toegepast nadat deze gebeurtenissen hebben plaatsgevonden. Zie de [inleiding tot de ontwikkeling van onderdelen](/help/sites-developing/components.md) voor achtergrondinformatie.

De volgende waarden moeten worden gedefinieerd om ervoor te zorgen dat alle vereiste acties worden opgenomen in:

```xml
N:cq:editConfig [cq:EditConfig]
    P:cq:actions [String[]] = "insert", "delete"
    P:cq:dialogMode = "floating"
    P:cq:layout = "auto"
    N:cq:listeners [cq:EditListenersConfig]
        P:aftercreate = "REFRESH_INSERTED"
        P:afterdelete = "REFRESH_SELF"
        P:afteredit = "REFRESH_SELF"
        P:afterinsert = "REFRESH_INSERTED"
        P:aftermove = "REFRESH_SELF"
        P:afterremove = "REFRESH_SELF"
```

### Algemene kolommen {#generic-columns}

Generieke kolommen zijn een extensie waarbij (de meeste van) de kolomdefinities worden opgeslagen op de instantie van het kolomknooppunt (in plaats van op het componentknooppunt).

Zij gebruiken een (standaard) dialoogvakje dat u voor de individuele generische component kunt aanpassen. Dit dialoogvakje laat de rapportgebruiker de kolomeigenschappen op een generische kolom op de rapportpagina bepalen (gebruikend de menuoptie **Kolomeigenschappen...**).

Een voorbeeld hiervan is het **Algemeen** kolom van de **Gebruikersrapport**. Zie `/libs/cq/reporting/components/userreport/genericcol`.

Een kolom algemeen maken:

* Stel de `type` eigenschap van de kolom `definition` knooppunt naar `generic`.

  Zie `/libs/cq/reporting/components/userreport/genericcol/definitions`

* Een definitie van het dialoogvenster (standaard) opgeven onder de kolominstellingen `definition` knooppunt.

  Zie `/libs/cq/reporting/components/userreport/genericcol/definitions/dialog`

   * De velden van het dialoogvenster moeten naar dezelfde namen verwijzen als de overeenkomende componenteigenschap, inclusief het pad.

     Als u bijvoorbeeld het type algemene kolom configureerbaar wilt maken via het dialoogvenster, gebruikt u een veld met de naam van `./definitions/type`.

   * Eigenschappen die zijn gedefinieerd met de interface/het dialoogvenster hebben voorrang op eigenschappen die zijn gedefinieerd in het dialoogvenster `columnbase` component.

* Bepaal de Edit Configuratie.

  Zie `/libs/cq/reporting/components/userreport/genericcol/cq:editConfig`

* Gebruik standaard AEM methoden om (aanvullende) kolomeigenschappen te definiëren.

  Voor eigenschappen die op zowel de component als de kolominstanties worden bepaald, heeft de waarde op de kolominstantie belangrijkheid.

  De eigenschappen die beschikbaar zijn voor een algemene kolom zijn:

   * `jcr:title` - kolomnaam
   * `definitions/aggregates` - aggregaten
   * `definitions/filters` - filters
   * `definitions/type`- het type kolom (dit moet in het dialoogvenster worden gedefinieerd met een kiezer/keuzelijst of een verborgen veld)
   * `definitions/data/resolver` en `definitions/data/resolverConfig` (maar niet `definitions/data/preprocessing` of `.../clientFilter`) - de oplosser en configuratie
   * `definitions/queryBuilder` - de configuratie van de vraagbouwer
   * `defaults/aggregate` - het standaardaggregaat

  Als er een nieuw geval van de generische kolom op is **Gebruikersrapport** blijven de eigenschappen die in het dialoogvenster zijn gedefinieerd, behouden:

  `/etc/reports/userreport/jcr:content/report/columns/genericcol/settings/generic`

## Rapportontwerp {#report-design}

Het ontwerp bepaalt welke kolomtypes voor het creëren van een rapport beschikbaar zijn. Het definieert ook het alineasysteem waaraan de kolommen worden toegevoegd.

Adobe raadt u aan voor elk rapport een apart ontwerp te maken. Dat garandeert volledige flexibiliteit. Zie [Uw nieuwe rapport definiëren](#defining-your-new-report).

De standaardrapporteringscomponenten worden aangehouden onder `/etc/designs/reports`.

De locatie voor uw rapporten kan afhankelijk zijn van de locatie van uw componenten:

* `/etc/designs/reports/<yourReport>` geschikt is als het verslag onder `/apps/cq/reporting`

* `/etc/designs/<yourProject>/reports/<*yourReport*>` voor rapporten die gebruikmaken van de `/apps/<yourProject>/reports` patroon

Vereiste ontwerpeigenschappen zijn geregistreerd op `jcr:content/reportpage/report/columns` (bijvoorbeeld `/etc/designs/reports/<reportName>/jcr:content/reportpage/report/columns`):

* `components`

  Om het even welke componenten en/of componentengroepen die op het rapport worden toegestaan.

* `sling:resourceType`

  Eigenschap met waarde `cq/reporting/components/repparsys`.

Een voorbeeldontwerpfragment (dat uit het ontwerp van het componentenrapport wordt genomen) is:

```xml
<!-- ... -->
    <jcr:content
        jcr:primaryType="nt:unstructured"
        jcr:title="Component Report"
        sling:resourceType="wcm/core/components/designer">
        <reportpage jcr:primaryType="nt:unstructured">
            <report jcr:primaryType="nt:unstructured">
                <columns
                    jcr:primaryType="nt:unstructured"
                    sling:resourceType="cq/reporting/components/repparsys"
                    components="group:Component Report"/>
            </report>
        </reportpage>
    </jcr:content>
<!-- ... -->
```

U hoeft geen ontwerpen op te geven voor afzonderlijke kolommen. Beschikbare kolommen kunnen worden gedefinieerd in de ontwerpmodus.

>[!NOTE]
>
>Adobe raadt u aan de standaardrapportontwerpen niet te wijzigen. Dit om ervoor te zorgen dat u geen veranderingen verliest wanneer het bevorderen van of het installeren van hotfixes.
>
>Kopieer het rapport en het ontwerp als u een standaardrapport wilt aanpassen.

>[!NOTE]
>
>De standaardkolommen kunnen automatisch worden gecreeerd wanneer een rapport wordt gecreeerd. Deze worden in de sjabloon opgegeven.

## Rapportsjabloon {#report-template}

Elk rapporttype moet een malplaatje verstrekken. Deze zijn standaard [CQ-sjablonen](/help/sites-developing/templates.md) en kan als zodanig worden geconfigureerd.

De sjabloon moet:

* instellen `sling:resourceType` tot `cq/reporting/components/reportpage`

* het te gebruiken ontwerp aangeven
* een `report` onderliggende node die naar de container verwijst ( `reportbase`) met de `sling:resourceType` eigenschap

Een fragment van het voorbeeldmalplaatje (dat van het malplaatje van het componentenrapport wordt genomen) is:

```xml
<!-- ... -->
    <jcr:content
        cq:designPath="/etc/designs/reports/compreport"
        jcr:primaryType="cq:PageContent"
        sling:resourceType="cq/reporting/components/reportpage">
        <report
            jcr:primaryType="nt:unstructured"
            sling:resourceType="cq/reporting/components/compreport/compreport"/>
    </jcr:content>
<!-- .. -->
```

Een fragment van het voorbeeldmalplaatje, dat de definitie van de wortelweg (die van het malplaatje van het gebruikersrapport wordt genomen) toont, is:

```xml
<!-- ... -->
    <jcr:content
        cq:designPath="/etc/designs/reports/userreport"
        jcr:primaryType="cq:PageContent"
        sling:resourceType="cq/reporting/components/reportpage">
        <report
            jcr:primaryType="nt:unstructured"
            rootPath="/home/users"
            sling:resourceType="cq/reporting/components/compreport/compreport"/>
    </jcr:content>
<!-- .. -->
```

De standaardrapportagesjablonen worden aangehouden onder `/libs/cq/reporting/templates`.

Adobe raadt echter aan deze knooppunten niet bij te werken. Maak in plaats daarvan uw eigen componentknooppunten onder `/apps/cq/reporting/templates` of, indien nodig, `/apps/<yourProject>/reports/templates`.

Wanneer, als voorbeeld (zie ook [Locatie van rapportcomponenten](#location-of-report-components)):

```xml
N:apps
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:templates [sling:Folder]
```

Onder dit, creeer de wortel voor uw malplaatje:

```xml
N:apps
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:templates [sling:Folder]
                N:<reportname> [sling:Folder]
```

## Uw eigen rapport maken - een voorbeeld {#creating-your-own-report-an-example}

### Uw nieuwe rapport definiëren {#defining-your-new-report}

Om een rapport te bepalen, creeer en vorm:

1. De wortel voor uw rapportcomponenten.
1. De rapportbasiscomponent.
1. Een of meer basiscomponenten van kolommen.
1. Het rapportontwerp.
1. De wortel voor uw rapportmalplaatje.
1. Het rapportmalplaatje.

Om deze stappen te illustreren, bepaalt het volgende voorbeeld een rapport dat van alle configuraties OSGi binnen de bewaarplaats een lijst maakt. Dat wil zeggen, alle gevallen van de `sling:OsgiConfig` knooppunt.

>[!NOTE]
>
>Het kopiëren van een bestaand rapport, dan het aanpassen van de nieuwe versie, is een alternatieve methode.

1. Creeer de wortelknoop voor uw nieuw rapport.

   Bijvoorbeeld onder `/apps/cq/reporting/components/osgireport`.

   ```xml
   N:cq [nt:folder]
       N:reporting [sling:Folder]
           N:components [sling:Folder]
               N:osgireport [sling:Folder]
   ```

1. Bepaal uw rapportbasis. Bijvoorbeeld: `osgireport[cq:Component]` krachtens `/apps/cq/reporting/components/osgireport`.

   ```xml
   N:osgireport [sling:Folder]
       N:osgireport [cq:Component]
           P:sling:resourceSuperType [String] = "cq/reporting/components/reportbase"
           N:charting [nt:unstructured]
               N:settings [nt:unstructured]
                   N:active [cq:WidgetCollection]
                       N:0 [nt:unstructured]
                           P:id [String] = "pie"
                       N:1 [nt:unstructured]
                           P:id [String] = "lineseries"
               N:definitions [cq:WidgetCollections]
                   N:0 [nt:unstructured]
                       P:id [String] = "pie"
                       P:maxRadius [Long] = 180
                       P:type [String] = "pie"
                   N:1 [nt:unstructured]
                       P:id [String] = "lineseries"
                       P:type [String] = "lineseries"
           N:dialog [cq:Dialog]
               P:height [Long] = 424
               N:items [cq:WidgetCollection]
                   N:props [cq:Panel]
                       N:items [cq:WidgetCollection]
                           N:title [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/title.infinity.json"
                               P:xtype [String] = "cqinclude"
                           N:description [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/description.infinity.json"
                               P:xtype [String] = "cqinclude"
                           N:rootPath [cq:Widget]
                               P:fieldLabel [String] = "Root path"
                               P:name [String] = "./report/rootPath"
                               P:xtype [String] = "pathfield"
                           N:processing [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/processing.infinity.json"
                               P:xtype [String] = "cqinclude"
                           N:scheduling [cq:Widget]
                               P:path [String] = "/libs/cq/reporting/components/commons/scheduling.infinity.json"
                               P:xtype [String] = "cqinclude"
           N:queryBuilder [nt:unstructured]
               P:nodeTypes [String[]] = "sling:OsgiConfig"
   ```

   Dit bepaalt een component van de rapportbasis die:

   * zoekopdrachten naar alle knooppunten van het type `sling:OsgiConfig`
   * geeft beide weergaven `pie` en `lineseries` grafieken
   * verstrekt een dialoog voor de gebruiker om het rapport te vormen

1. Definieer de eerste kolomcomponent (columnBase). Bijvoorbeeld: `bundlecol[cq:Component]` krachtens `/apps/cq/reporting/components/osgireport`.

   ```xml
   N:osgireport [sling:Folder]
       N:bundlecol [cq:Component]
           P:componentGroup [String] = "OSGi Report"
           P:jcr:title = "Bundle"
           P:sling:resourceSuperType [String] = "cq/reporting/components/columnbase"
           N:cq:editConfig [cq:EditConfig]
               P:cq:actions [String[]] = "insert", "delete"
               P:cq:dialogMode [String] = "floating"
               P:cq:layout [String] = "auto"
               N:cq:listeners [cq:EditListenersConfig]
                   P:aftercreate [String] "REFRESH_INSERTED"
                   P:afterdelete [String] "REFRESH_SELF"
                   P:afteredit [String] "REFRESH_SELF"
                   P:afterinsert [String] "REFRESH_INSERTED"
                   P:aftermove [String] "REFRESH_SELF"
                   P:afterremove [String] "REFRESH_SELF"
           N:defaults [nt:unstructured]
               P:aggregate [String] = "count"
           N:definitions [nt:unstructured]
               P:groupable [Boolean] = false
               P:type [String] = "string"
               N:queryBuilder [nt:unstructured]
                   P:property [String] = "jcr:path"
   ```

   Hiermee wordt een component ColumnBase gedefinieerd:

   * zoekt naar en retourneert de waarde die het van de server ontvangt; in dit geval de eigenschap `jcr:path` voor elke `sling:OsgiConfig` node
   * verstrekt `count` aggregaat
   * is niet gegroepeerd
   * heeft de titel `Bundle` (kolomtitel in de tabel)
   * bevindt zich in de groep sidekick `OSGi Report`
   * Vernieuwingen bij opgegeven gebeurtenissen

   >[!NOTE]
   >
   >In dit voorbeeld zijn er geen definities van `N:data` en `P:clientFilter`. De reden hiervoor is dat de waarde die van de server wordt ontvangen, op een 1:1-basis wordt geretourneerd. Dit is het standaardgedrag.
   >
   >Dit is hetzelfde als de definities:
   >
   >```
   >N:data [nt:unstructured]
   >   P:clientFilter [String] = "function(v) { return v; }"
   >```
   >
   >Waar de functie gewoon de waarde retourneert die deze ontvangt.

1. Bepaal uw rapportontwerp. Bijvoorbeeld: `osgireport[cq:Page]` krachtens `/etc/designs/reports`.

   ```xml
   N:osgireport [cq:Page]
       N:jcr:content [nt:unstructured]
           P:jcr:title [String] = "OSGi report"
           P:sling:resourceType [String] = "wcm/core/components/designer"
           N:reportpage [nt:unstructured]
               N:report [nt:unstructured]
                   N:columns [nt:unstructured]
                       P:components [String] = "group:OSGi Report"
                       P:sling:resourceType [String] = "cq/reporting/components/repparsys"
   ```

1. Creeer de wortelknoop voor uw nieuw rapportmalplaatje.

   Bijvoorbeeld onder `/apps/cq/reporting/templates/osgireport`.

   ```xml
   N:cq [nt:folder]
       N:reporting [sling:Folder]
           N:templates [sling:Folder]
               N:osgireport [cq:Template]
   ```

1. Bepaal uw rapportmalplaatje. Bijvoorbeeld: `osgireport[cq:Template]` krachtens `/apps/cq/reporting/templates`.

   ```xml
   N:osgireport [cq:Template]
       P:allowedPaths [String[]] = "/etc/reports(/.*)?"
       P:jcr:description [String] = "Use this report generator to create an OSGi report."
       P:jcr:title [String] = "OSGi Report Template"
       P:ranking [Long] = 100
       P:shortTitle [String] = "OSGi Report"
       N:jcr:content [cq:PageContent]
           P:cq:designPath [String] = "/etc/designs/reports/osgireport"
           P:sling:resourceType [String] = "cq/reporting/components/reportpage"
           N:report [nt:unstructured]
               P:rootPath [String] = "/"
               P:sling:resourceType [String] = "cq/reporting/components/osgireport/osgireport"
       N:thumbnail.png [nt:file]
   ```

   Hiermee definieert u een sjabloon die:

   * definieert de `allowedPaths` voor de daaruit voortvloeiende verslagen - in het bovenstaande geval in de `/etc/reports`
   * biedt titels en beschrijvingen voor de sjabloon
   * verstrekt een duimnagelbeeld voor gebruik in de malplaatjelijst (de volledige definitie van dit knooppunt is hierboven niet vermeld - het is het gemakkelijkst om een geval van thumbnail.png van een bestaand rapport te kopiëren).

### Het creëren van een Instantie van Uw Nieuw Rapport {#creating-an-instance-of-your-new-report}

Een geval van uw nieuw rapport kan nu worden gecreeerd:

1. Open de **Gereedschappen** console.

1. Selecteren **Rapporten** in het linkerdeelvenster.
1. Vervolgens **Nieuw...** op de werkbalk. Een **Titel** en **Naam** selecteert u het nieuwe rapporttype (de **OSGi-rapportsjabloon**) in de lijst met sjablonen en klik vervolgens op **Maken**.
1. Uw nieuwe rapportexemplaar verschijnt in de lijst. Dubbelklik op deze optie om deze te openen.
1. Sleep een component (in dit voorbeeld: **Bundel** in de **OSGi-rapport** groep) van de sidekick om de eerste kolom te creëren en [begin de rapportdefinitie](/help/sites-administering/reporting.md#the-basics-of-report-customization).

   >[!NOTE]
   >
   >Aangezien dit voorbeeld geen groeperbare kolommen heeft, zijn de grafieken niet beschikbaar. Tekenreeksen weergeven `groupable` tot `true`:
   >
   >```
   >N:osgireport [sling:Folder]
   > N:bundlecol [cq:Component]
   > N:definitions [nt:unstructured]
   > P:groupable [Boolean] = true
   >```
   >

## Het vormen van de Diensten van het Kader van het Rapport {#configuring-the-report-framework-services}

Deze sectie beschrijft geavanceerde configuratieopties voor de diensten OSGi die het rapportkader uitvoeren.

Deze kunnen worden bekeken gebruikend het menu van de Configuratie van de Webconsole (beschikbaar bij `http://localhost:4502/system/console/configMgr`, bijvoorbeeld). Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

### Basisservice (CQ-rapportconfiguratie op de dag) {#basic-service-day-cq-reporting-configuration}

* **Tijdzone** definieert de historische gegevens voor de tijdzone waarvoor ze worden gemaakt. Dit moet ervoor zorgen dat de historische grafiek de zelfde gegevens voor elke gebruiker over de wereld toont.
* **Landinstelling** definieert de landinstelling waarmee moet worden gewerkt **Tijdzone** voor historische gegevens. De landinstelling wordt gebruikt om bepaalde landspecifieke kalenderinstellingen te bepalen (bijvoorbeeld of de eerste dag van een week zondag of maandag is).

* **Pad voor momentopname** bepaalt de wortelweg waar de momentopnamen voor historische grafieken worden opgeslagen.
* **Pad naar rapporten** bepaalt de weg waar de rapporten worden gevestigd. Dit wordt gebruikt door de momentopnameservice om de rapporten te bepalen om momentopnamen voor eigenlijk te nemen.
* **Dagelijkse momentopnamen** bepaalt het uur van elke dag wanneer de dagelijkse momentopnamen worden genomen. Het gespecificeerde uur is in lokale timezone van de server.
* **Uuropnamen** bepaalt de minuut van elk uur wanneer uurmomentopnamen worden genomen.
* **Rijen (max.)** Hiermee definieert u het maximum aantal rijen dat voor elke opname wordt opgeslagen. Deze waarde moet redelijkerwijs worden gekozen. Als het te hoog is, beïnvloedt dit de grootte van de gegevensopslagplaats, als te laag, kunnen de gegevens niet correct zijn wegens de manier waarop historische gegevens worden behandeld.
* **Gegevens uitfaden**, indien ingeschakeld, kunnen met behulp van de `fakedata` kiezer; indien uitgeschakeld, gebruikt u de `fakedata` genereert een uitzondering.

  Omdat de gegevens onecht zijn, moeten ze *alleen* worden gebruikt voor het testen en opsporen van fouten.

  Met de `fakedata` selector voltooit het rapport impliciet, zodat worden alle bestaande gegevens verloren. Gegevens kunnen handmatig worden hersteld, maar dit kan een tijdrovend proces zijn.

* **Opname-gebruiker** definieert een optionele gebruiker die kan worden gebruikt voor het maken van momentopnamen.

  In feite worden momentopnamen gemaakt voor de gebruiker die het rapport heeft voltooid. Er kunnen situaties zijn (bijvoorbeeld op een publicatiesysteem, waar deze gebruiker niet bestaat omdat zijn account niet is gerepliceerd) waarin u een fallback-gebruiker wilt opgeven die in plaats daarvan wordt gebruikt.

  Ook, zou het specificeren van een gebruiker een veiligheidsrisico kunnen opleggen.

* **Gebruiker van momentopnamen afdwingen**, indien ingeschakeld, worden alle momentopnamen gemaakt met de gebruiker die onder *Opname-gebruiker*. Dit kan ernstige gevolgen voor de beveiliging hebben als het niet correct wordt afgehandeld.

### Cacheinstellingen (CQ-rapportagecache dag) {#cache-settings-day-cq-reporting-cache}

* **Inschakelen** laat u het in cache plaatsen van rapportgegevens in- of uitschakelen. Het toelaten van het rapportgeheime voorgeheugen houdt rapportgegevens in geheugen tijdens verscheidene verzoeken. Dit kan de prestaties verhogen, maar leidt tot een hoger geheugengebruik en kan in extreme omstandigheden leiden tot situaties waarin onvoldoende geheugen beschikbaar is.
* **TTL** bepaalt de tijd (in seconden) waarvoor de rapportgegevens in het voorgeheugen worden opgeslagen. Een hoger getal verhoogt de prestaties, maar retourneert mogelijk ook onjuiste gegevens als de gegevens binnen de tijdsperiode veranderen.
* **Max. items** bepaalt het maximumaantal rapporten dat op om het even welk ogenblik in het voorgeheugen moet worden opgeslagen.

>[!NOTE]
>
>De rapportgegevens kunnen voor elke gebruiker en taal verschillend zijn. Daarom worden de rapportgegevens in het voorgeheugen ondergebracht per rapport, gebruiker, en taal. Dit betekent dat een **Max. items** waarde van `2` gegevens daadwerkelijk in cache plaatsen voor:
>
>* één rapport voor twee gebruikers met verschillende taalmontages
>* één gebruiker en twee rapporten
>
