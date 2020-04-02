---
title: Rapporten ontwikkelen
seo-title: Rapporten ontwikkelen
description: AEM verstrekt een selectie van standaardverslagen die op een rapporteringskader worden gebaseerd
seo-description: AEM verstrekt een selectie van standaardverslagen die op een rapporteringskader worden gebaseerd
uuid: 1b406d15-bd77-4531-84c0-377dbff5cab2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 50fafc64-d462-4386-93af-ce360588d294
translation-type: tm+mt
source-git-commit: ea6da2b75cce4052211fb8f0793f1f380eb85a20

---


# Rapporten ontwikkelen{#developing-reports}

AEM biedt een selectie van [standaardverslagen](/help/sites-administering/reporting.md) , waarvan de meeste gebaseerd zijn op een rapportagekader.

Met behulp van het framework kunt u deze standaardrapporten uitbreiden of uw eigen, volledig nieuwe rapporten ontwikkelen. Het rapportagekader sluit nauw aan bij de bestaande CQ5-concepten en -beginselen, zodat ontwikkelaars hun bestaande kennis van CQ5 kunnen gebruiken als springplank voor het opstellen van rapporten.

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
>De zelfstudie Uw eigen rapport [maken - Een voorbeeld](#creating-your-own-report-an-example) laat ook zien hoeveel van de onderstaande principes kunnen worden gebruikt.
>
>U kunt ook naar de standaardrapporten verwijzen om andere voorbeelden van implementatie te zien.

>[!NOTE]
>
>In de volgende voorbeelden en definities wordt de volgende notatie gebruikt:
>
>* Elke regel definieert een knooppunt of een eigenschap waarbij:
   >
   >  
* `N:<name> [<nodeType>]`
   >
   >     
   Beschrijft een knoop met de naam van `<*name*>` en knooptype van `<*nodeType*>`*.*
   >
   >  
* `P:<name> [<propertyType]`
   >
   >     
   Beschrijft een bezit met de naam van `<*name*>` en een bezitstype van `<*propertyType*>`.
   >
   >  
* `P:<name> = <value>`
   >
   >     
   Beschrijft een bezit `<name>` dat aan de waarde van moet worden geplaatst `<value>`.
   >
   >
* De inspringing toont de hiërarchische gebiedsdelen tussen de knopen.
>* Items gescheiden door| een lijst van mogelijke artikelen; bijvoorbeeld typen of namen:
>
>  
Bijvoorbeeld `String|String[]` betekent dat de eigenschap String of String[]kan zijn.
>
>* `[]` een array weergeeft; zoals String[] of een array van knooppunten, zoals in de [Query Definition](#query-definition).
>
>
Tenzij anders vermeld zijn de standaardtypes:
>
>* Nodes - `nt:unstructured`
>* Eigenschappen - `String`


## Rapportagekader {#reporting-framework}

Het rapportagekader werkt aan de volgende beginselen:

* Het is volledig gebaseerd op resultaatreeksen die door een vraag zijn teruggekeerd die door CQ5 wordt uitgevoerd QueryBuilder.
* De resultaatreeks bepaalt de gegevens die in het rapport worden getoond. Elke rij in de resultaatreeks beantwoordt aan een rij in de tabelmening van het rapport.
* De verrichtingen beschikbaar voor uitvoering op de resultaatreeks lijken op concepten RDBMS; voornamelijk *groepering* en *aggregatie*.

* De meeste gegevensherwinning en verwerking worden gedaan serverzijde.
* De klant is alleen verantwoordelijk voor de weergave van de vooraf verwerkte gegevens. Alleen kleine verwerkingstaken (bijvoorbeeld het maken van koppelingen in celinhoud) worden aan de clientzijde uitgevoerd.

Het rapportagekader (geïllustreerd door de structuur van een standaardrapport) gebruikt de volgende bouwstenen, die door de verwerkingswachtrij worden gevoed:

![chlimage_1-248](assets/chlimage_1-248.png)

### Rapportpagina {#report-page}

De rapportpagina:

* Is een standaard CQ5-pagina.
* Is gebaseerd op een [standaardCQ5 malplaatje, dat voor het rapport](#report-template)wordt gevormd.

### Rapportbasis {#report-base}

De [ component `reportbase`](#report-base-component) vormt de basis voor elk verslag zoals het:

* Houdt de definitie van de [vraag](#the-query-and-data-retrieval) die de onderliggende resultaatreeks gegevens levert.

* Is een aangepast paragraafsysteem dat alle kolommen ( `columnbase`) zal bevatten aan het rapport worden toegevoegd.
* Bepaalt welke grafiektypes beschikbaar zijn en die momenteel actief zijn.
* Bepaalt de Edit dialoog, die de gebruiker toestaat om bepaalde aspecten van het rapport te vormen.

### Kolombasis {#column-base}

Elke kolom is een instantie van de [ component `columnbase`](#column-base-component) die:

* Is een paragraaf, die door parsys ( `reportbase`) van het respectieve rapport wordt gebruikt.
* Bepaalt de verbinding aan de [onderliggende resultaatreeks](#the-query-and-data-retrieval); Hiermee worden de specifieke gegevens gedefinieerd waarnaar in deze resultaatset wordt verwezen, en hoe deze worden verwerkt.
* bevat aanvullende definities; zoals de beschikbare aggregaten en filters, samen met standaardwaarden.

### De query en het ophalen van gegevens {#the-query-and-data-retrieval}

De query:

* Is gedefinieerd als onderdeel van de [`reportbase`](#report-base) component.
* Is gebaseerd op [CQ QueryBuilder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html).
* Haalt de gegevens op die als basis voor het rapport worden gebruikt. Elke rij van de resultaatreeks (lijst) is gebonden aan een knoop zoals teruggekeerd door de vraag. Vervolgens wordt specifieke informatie voor [afzonderlijke kolommen](#column-base-component) uit deze gegevensset geëxtraheerd.

* Bestaat gewoonlijk uit:

   * Een hoofdpad.

      Hiermee wordt de substructuur van de gegevensopslagruimte aangegeven die moet worden doorzocht.

      Om de invloed op de prestaties tot een minimum te beperken, is het raadzaam om de query te (proberen) beperken tot een specifieke subboomstructuur van de repository. De wortelweg kan of vooraf bepaald in het [rapportmalplaatje](#report-template) of door de gebruiker in de [Configuratie (uitgeven) dialoog](#configuration-dialog)worden geplaatst.

   * [Een of meer criteria](#query-definition).

      Deze worden opgelegd om de (oorspronkelijke) resultaatreeks te produceren; ze omvatten bijvoorbeeld beperkingen op het knooppunttype of eigenschapbeperkingen.

**Het belangrijkste punt hier is dat elke enige knoop die in de resultaatreeks van de vraag wordt teruggekeerd wordt gebruikt om één enkele rij op het rapport (zo een 1:1 verhouding) te produceren.**

De ontwikkelaar moet ervoor zorgen dat de vraag die voor een rapport wordt bepaald een knoop terugkeert die aangewezen voor dat rapport wordt geplaatst. Nochtans, te hoeven de knoop zelf niet alle vereiste informatie te houden, kan dit ook uit ouder en/of kindknopen worden afgeleid. Bijvoorbeeld, selecteert de vraag die voor het Rapport [van de](/help/sites-administering/reporting.md#user-report) Gebruiker wordt gebruikt knopen die op het knooptype (in dit geval `rep:user`) worden gebaseerd. Nochtans, nemen de meeste kolommen op dit rapport hun gegevens niet direct van deze knopen, maar van de kindknopen `profile`.

### Bezig met verwerken van wachtrij {#processing-queue}

De [vraag](#the-query-and-data-retrieval) keert een resultaatreeks gegevens terug die als rijen op het rapport moeten worden getoond. Elke rij in de resultaatreeks wordt verwerkt (server-kant), in [verscheidene fasen](#phases-of-the-processing-queue), alvorens wordt overgebracht naar de cliënt voor vertoning op het rapport.

Hierdoor is het mogelijk:

* Waarden extraheren en afleiden van de onderliggende resultatenset.

   U kunt bijvoorbeeld twee eigenschapswaarden als één waarde verwerken door het verschil tussen de twee waarden te berekenen.

* Oplossen van geëxtraheerde waarden; dit kan op verschillende manieren gebeuren .

   Paden kunnen bijvoorbeeld worden toegewezen aan een titel (zoals in de meer leesbare inhoud van de respectievelijke eigenschap *jcr:title* ).

* Filters toepassen op verschillende punten.
* Indien nodig samengestelde waarden maken.

   Bijvoorbeeld bestaande uit een tekst die aan de gebruiker wordt getoond, een waarde die voor het sorteren en een extra URL moet worden gebruikt die (op de cliëntkant) voor het creëren van een verbinding wordt gebruikt.

#### Workflow van de verwerkingswachtrij {#workflow-of-the-processing-queue}

De volgende workflow vertegenwoordigt de verwerkingswachtrij:

![chlimage_1-249](assets/chlimage_1-249.png)

#### Fasen van de Verwerkingswachtrij {#phases-of-the-processing-queue}

Waar de gedetailleerde stappen en elementen zijn:

1. Transformeert de resultaten die door de [aanvankelijke vraag (reportbase)](#query-definition) zijn teruggekeerd in de basisresultaatreeks gebruikend waardeextractors.

   De extractoren van de waarde worden automatisch gekozen afhankelijk van het [kolomtype](#column-specific-definitions). Deze worden gebruikt voor het lezen van waarden van de onderliggende JCR-query en het maken van een resultaatset op basis daarvan. waarna verdere verwerking kan worden toegepast. Voor het `diff` type, leest de waardeextractor bijvoorbeeld twee eigenschappen, berekent de enkele waarde die vervolgens aan de resultatenset wordt toegevoegd. De waarde-extractors kunnen niet worden geconfigureerd.

1. Op die aanvankelijke resultaatreeks, die ruwe gegevens bevat, wordt het [aanvankelijke filtreren](#column-specific-definitions) (*ruwe* fase) toegepast.

1. Waarden worden [vooraf verwerkt](#processing-queue); zoals gedefinieerd voor de *toepassingsfase* .

1. [Filteren](#column-specific-definitions) (toegewezen aan de *vooraf verwerkte* fase) wordt uitgevoerd op de vooraf verwerkte waarden.

1. Waarden worden opgelost; volgens de [gedefinieerde oplosser](#processing-queue).
1. [Filteren](#column-specific-definitions) (toegewezen aan de *opgeloste* fase) wordt uitgevoerd op de opgeloste waarden.

1. Gegevens worden [gegroepeerd en samengevoegd](#column-specific-definitions).
1. Arraygegevens worden omgezet in een (op tekenreeks gebaseerde) lijst.

   Dit is een impliciete stap die een resultaat met meerdere waarden omzet in een lijst die kan worden getoond; deze is vereist voor (niet-geaggregeerde) celwaarden die zijn gebaseerd op JCR-eigenschappen met meerdere waarden.

1. De waarden worden opnieuw [vooraf verwerkt](#processing-queue); zoals gedefinieerd voor de *fase afterApply* .

1. Gegevens worden gesorteerd.
1. De verwerkte gegevens worden naar de client overgedragen.

>[!NOTE]
>
>De aanvankelijke vraag die de resultaatreeks van basisgegevens terugkeert wordt bepaald op de `reportbase` component.
>
>Andere elementen van de verwerkingsrij worden bepaald op de `columnbase` componenten.

## Constructie en configuratie van rapporten {#report-construction-and-configuration}

Het volgende is nodig om een rapport te construeren en te vormen:

* een [plaats voor de definitie van uw rapportcomponenten](#location-of-report-components)
* een [`reportbase` component](#report-base-component)
* een of meer [ `columnbase` componenten](#column-base-component)
* een [paginacomponent](#page-component)
* een [rapportontwerp](#report-design)
* een [rapportsjabloon](#report-template)

### Locatie van rapportcomponenten {#location-of-report-components}

De standaardrapporteringscomponenten worden aangehouden onder `/libs/cq/reporting/components`.

Het wordt echter ten zeerste aanbevolen deze knooppunten niet bij te werken, maar zelf componentknooppunten te maken onder `/apps/cq/reporting/components` of, indien dit meer aangewezen is, `/apps/<yourProject>/reports/components`.

Waar (als voorbeeld):

```
N:apps
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:components [sling:Folder]
```

Onder dit creeert u de wortel voor uw rapport en onder dit, de component van de rapportbasis en de componenten van de kolombasis:

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

Een aangepaste pagina-component is in de meeste gevallen niet nodig.

## Basiscomponent rapporteren {#report-base-component}

Elk rapporttype vereist een containercomponent die van wordt afgeleid `/libs/cq/reporting/components/reportbase`.

Deze component fungeert als container voor het rapport als geheel en biedt informatie voor:

* De [querydefinitie](#query-definition).
* Een [(facultatieve) dialoog](#configuration-dialog) voor het vormen van het rapport.
* Alle [grafieken](#chart-definitions) die in het verslag zijn opgenomen.

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

   Kan worden gebruikt om het resultaat te beperken dat is ingesteld op knooppunten met specifieke eigenschappen met specifieke waarden. Als de veelvoudige beperkingen worden gespecificeerd, moet de knoop aan elk van hen (EN verrichting) voldoen.

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

   Retourneert alle `textimage` componenten die het laatst door de `admin` gebruiker zijn gewijzigd.

* `nodeTypes`

   Wordt gebruikt om het resultaat te beperken tot de opgegeven knooppunttypen. U kunt meerdere knooppunttypen opgeven.

* `mandatoryProperties`

   Kan worden gebruikt om het resultaat te beperken dat is ingesteld op knooppunten die *alle* opgegeven eigenschappen hebben. Er wordt geen rekening gehouden met de waarde van de eigenschappen.

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

      Aangezien er meerdere instellingen kunnen worden gedefinieerd, kunt u dit gebruiken om te definiëren welke momenteel actief zijn. Deze worden bepaald door een serie van knopen (er is geen verplichte noemende overeenkomst voor deze knopen, maar de standaardrapporten gebruiken vaak `0`, `1`.. `x`), elk met de volgende eigenschap:

      * `id`

         Identificatie voor de actieve diagrammen. Dit moet identiteitskaart van één van de grafiek aanpassen `definitions`.

* `definitions`

   Bepaalt de grafiektypes die potentieel voor het rapport beschikbaar zijn. De `definitions` `active` instellingen bepalen welk item moet worden gebruikt.

   De definities worden opgegeven met behulp van een array met knooppunten (ook weer vaak `0`, `1`.. `x`), elk met de volgende eigenschappen:

   * `id`

      De kaart-identificatie.

   * `type`

      Het type grafiek dat beschikbaar is. Selecteren uit:

      * `pie`
Cirkeldiagram. Alleen gegenereerd op basis van huidige gegevens.

      * `lineseries`
Reeks lijnen (verbindende punten die de daadwerkelijke momentopnamen vertegenwoordigen). Alleen gegenereerd op basis van historische gegevens.
   * Er zijn aanvullende eigenschappen beschikbaar, afhankelijk van het diagramtype:

      * voor het diagramtype `pie`:

         * `maxRadius` ( `Double/Long`)

            De maximale straal die voor het cirkeldiagram is toegestaan; daarom de maximumgrootte die voor de grafiek (zonder legenda) wordt toegestaan. Genegeerd als `fixedRadius` is gedefinieerd.

         * `minRadius` ( `Double/Long`)

            De minimale straal die is toegestaan voor het cirkeldiagram. Genegeerd als `fixedRadius` is gedefinieerd.

         * `fixedRadius` ( `Double/Long`)Hiermee definieert u een vaste straal voor het cirkeldiagram.
      * voor het diagramtype [`lineseries`](/help/sites-administering/reporting.md#display-limits):

         * `totals` ( `Boolean`)

            True if an additional line displaying the **Total** should be displayed.
standaardwaarde: `false`

         * `series` ( `Long`)

            Aantal weer te geven lijnen/reeksen.
standaard: `9` (dit is ook het toegestane maximum)

         * `hoverLimit` ( `Long`)

            Maximum aantal samengevoegde momentopnamen (punten die op elke horizontale lijn worden getoond, die verschillende waarden vertegenwoordigen) waarvoor popups moeten worden getoond, d.w.z. wanneer de gebruiker muis-over op een specifieke waarde of een overeenkomstig etiket in de grafieklegende doet.

            standaard: `35` (Er worden dus helemaal geen popups weergegeven als meer dan 35 verschillende waarden van toepassing zijn voor de huidige diagraminstellingen).

            Er geldt een extra limiet van 10 pop-ups die parallel kunnen worden weergegeven (meerdere pop-ups kunnen worden weergegeven wanneer de muisaanwijzer op de legenda wordt geplaatst).



### Configuratiedialoogvenster {#configuration-dialog}

Elk rapport kan een configuratiedialoog hebben, toestaand de gebruiker om diverse parameters voor het rapport te specificeren. Dit dialoogvenster is toegankelijk via de knop **Bewerken** wanneer de rapportpagina is geopend.

Dit dialoogvenster is een standaard CQ- [dialoogvenster](/help/sites-developing/components-basics.md#dialogs) en kan als zodanig worden geconfigureerd (zie [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog) voor meer informatie).

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

Verschillende vooraf geconfigureerde componenten worden geleverd; U kunt hier in het dialoogvenster naar verwijzen met de `xtype` eigenschap met de waarde `cqinclude`:

* **`title`**

   `/libs/cq/reporting/components/commons/title`

   TextField om de rapporttitel te bepalen.

* **`description`**

   `/libs/cq/reporting/components/commons/description`

   Textarea om de rapportbeschrijving te bepalen.

* **`processing`**

   `/libs/cq/reporting/components/commons/processing`

   Selector voor de verwerkingsmodus van het rapport (gegevens handmatig/automatisch laden).

* **`scheduling`**

   `/libs/cq/reporting/components/commons/scheduling`

   Kiezer voor het plannen van momentopnamen voor de historische grafiek.

>[!NOTE]
>
>De componenten waarnaar wordt verwezen, moeten worden opgenomen met behulp van het `.infinity.json` achtervoegsel (zie voorbeeld hierboven).

### Hoofdpad {#root-path}

Bovendien kan een wortelweg voor het rapport worden bepaald:

* **`rootPath`**

   Dit beperkt het rapport tot een bepaalde sectie (boom of subboom) van de bewaarplaats, die voor prestatiesoptimalisering wordt geadviseerd. Het wortelweg wordt gespecificeerd door het `rootPath` bezit van de `report` knoop van elke rapportpagina (die van het malplaatje op paginaverwezenlijking wordt genomen).

   Deze kan worden gespecificeerd door:

   * het [rapportmalplaatje](#report-template) (of als vaste waarde of als standaardwaarde voor de configuratiedialoog).
   * de gebruiker (met deze parameter)

## Basiscomponent kolom {#column-base-component}

Voor elk kolomtype is een component vereist die is afgeleid van `/libs/cq/reporting/components/columnbase`.

Een kolomcomponent definieert een combinatie van het volgende:

* De [kolomspecifieke configuratie van de Vraag](#column-specific-query) .
* De [Resolvers en Preprocessing](#resolvers-and-preprocessing).
* de [kolomspecifieke definities](#column-specific-definitions) (zoals filters en aggregaten; `definitions` onderliggende node).
* [Standaardwaarden](#column-default-values)kolom.
* Het filter [](#client-filter) Client extraheert de informatie die moet worden weergegeven op basis van de gegevens die door de server worden geretourneerd.
* Bovendien moet een kolomcomponent een geschikt exemplaar van `cq:editConfig`leveren. om de vereiste [gebeurtenissen en handelingen](#events-and-actions) te definiëren.
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

Zie ook [Uw nieuw rapport](#defining-your-new-report)definiëren.

### Kolomspecifieke query {#column-specific-query}

Hiermee definieert u de specifieke gegevensextractie (uit de resultaatset [van de](#the-query-and-data-retrieval)rapportgegevens) voor gebruik in de afzonderlijke kolom.

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

   Als eigenschap wordt gedefinieerd als String[] , worden meerdere eigenschappen gescand (in volgorde) om de werkelijke waarde te vinden.

   Bijvoorbeeld in het geval van:

   `property = [ "jcr:lastModified", "jcr:created" ]`

   De overeenkomstige waarde-extractor (die hier in controle is) zal:

   * Controleer of er een eigenschap jcr:lastModified beschikbaar is en gebruik deze als dat zo is.
   * Als er geen eigenschap jcr:lastModified beschikbaar is, wordt in plaats daarvan de inhoud van jcr:created gebruikt.

* `subPath`

   Als het resultaat niet op de knoop wordt gevestigd die door de vraag is teruggekeerd, `subPath` bepaalt waar het bezit eigenlijk wordt gevestigd.

* `secondaryProperty`

   Definieert een tweede eigenschap die ook moet worden gebruikt voor het berekenen van de werkelijke celwaarde; dit wordt alleen gebruikt voor bepaalde kolomtypen ( diff en sortable ) .

   Bijvoorbeeld, in het geval van het Rapport van de Instanties van het Werkschema, wordt het gespecificeerde bezit gebruikt om de daadwerkelijke waarde van het tijdverschil (in milliseconden) tussen begin en eindtijden op te slaan.

* `secondarySubPath`

   Gelijkaardig aan subPath, wanneer `secondaryProperty` wordt gebruikt.

In de meeste gevallen `property` zal alleen worden gebruikt.

### Clientfilter {#client-filter}

Het clientfilter extraheert de informatie die moet worden weergegeven, uit de gegevens die door de server worden geretourneerd.

>[!NOTE]
>
>Dit filter wordt aan clientzijde uitgevoerd nadat de verwerking op de volledige server is toegepast.

```xml
N:definitions
    N:data
        P:clientFilter [String]
```

`clientFilter` wordt gedefinieerd als een JavaScript-functie die:

* als input één parameter ontvangt; de gegevens die door de server worden geretourneerd (dus volledig vooraf verwerkt)
* als output, retourneert de gefilterde (verwerkte) waarde; de gegevens die uit de inputinformatie zijn gehaald of afgeleid

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

De [verwerkingsrij](#processing-queue) bepaalt diverse oplosmiddelen en vormt preprocessing:

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

      Wijst waarden toe aan andere waarden; Dit wordt bijvoorbeeld gebruikt om constanten zoals `en` de equivalente waarde op te lossen `English`.

   * `default`

      De standaardoplosser. Dit is een nepoplosser die eigenlijk niets oplost.

   * `page`

      Hiermee wordt een padwaarde omgezet in het pad van de desbetreffende pagina. nauwkeuriger, aan de overeenkomstige `jcr:content` knoop. bijvoorbeeld, `/content/.../page/jcr:content/par/xyz` wordt omgezet in `/content/.../page/jcr:content`.

   * `path`

      Hiermee lost u een padwaarde op door optioneel een subpad toe te voegen en de werkelijke waarde van een eigenschap van het knooppunt (zoals gedefinieerd door `resolverConfig`) op te nemen bij het omgezette pad. Zo `path` kan bijvoorbeeld een `/content/.../page/jcr:content` van de twee worden omgezet in de inhoud van de `jcr:title` eigenschap. Dit betekent dat een paginapad wordt omgezet in de paginatitel.

   * `pathextension`

      Hiermee lost u een waarde op door een pad vooraf in te stellen en de werkelijke waarde te nemen vanuit een eigenschap van het knooppunt op het opgeloste pad. Een waarde `de` kan bijvoorbeeld worden voorafgegaan door een pad, bijvoorbeeld `/libs/wcm/core/resources/languages`door de waarde van de eigenschap te nemen `language`, om de landcode `de` op te lossen naar de taalbeschrijving `German`.

* `resolverConfig`

   Verstrekt definities voor resolver; de beschikbare opties zijn afhankelijk van de `resolver` geselecteerde opties:

   * `const`

      Gebruik eigenschappen om de constanten voor het omzetten op te geven. De naam van de eigenschap definieert de constante die moet worden opgelost. De waarde van de eigenschap definieert de omgezette waarde.

      Een eigenschap met **Name**= `1` en **Value** zullen bijvoorbeeld 1 tot 1 oplossen `=One` .

   * `default`

      Geen configuratie beschikbaar.

   * `page`

      * `propertyName` (optioneel)

         Definieert de naam van de eigenschap die moet worden gebruikt voor het omzetten van de waarde. Indien niet opgegeven, wordt de standaardwaarde van *jcr:title* (de paginatitel) gebruikt; voor de `page` oplosser betekent dit dat eerst het pad wordt omgezet naar het paginapad en vervolgens verder wordt omgezet naar de paginatitel.
   * `path`

      * `propertyName` (optioneel)

         Specifies the name of the property that should be used for resolving the value. Indien niet opgegeven, wordt de standaardwaarde van `jcr:title` gebruikt.

      * `subPath` (optioneel)

         Deze eigenschap kan worden gebruikt om een achtervoegsel op te geven dat aan het pad moet worden toegevoegd voordat de waarde wordt omgezet.
   * `pathextension`

      * `path` (mandatory)

         Definieert het pad dat moet worden voorafgegaan.

      * `propertyName` (mandatory)

         Definieert de eigenschap op het omgezette pad waar de werkelijke waarde zich bevindt.

      * `i18n` (facultatief; type Boolean)

         Hiermee wordt bepaald of de opgeloste waarde moet worden *geïnternationaliseerd* (d.w.z. met behulp van de [CQ5-internationalisatieservices](/help/sites-administering/tc-manage.md)).



* `preprocessing`

   Voorbewerking is optioneel en kan (afzonderlijk) aan de verwerkingsfasen worden gebonden en *toegepast* of *applyAfter*:

   * `apply`

      De eerste voorbewerkingsfase ([stap 3 in de weergave van de verwerkingswachtrij](#processing-queue)).

   * `applyAfter`

      Toepassen na voorbehandeling ([stap 9 in de weergave van de verwerkingswachtrij](#processing-queue)).

#### Resolvers {#resolvers}

De oplosmiddelen worden gebruikt om de vereiste informatie te halen. Voorbeelden van de verschillende oplosmiddelen zijn:

**Const**

Hieronder wordt een contantwaarde van `VersionCreated` naar de tekenreeks omgezet `New version created`.

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

In het volgende voorbeeld wordt een pad naar `/content/.../page` de inhoud van de `jcr:title` eigenschap omgezet. Dit betekent dat een paginapad wordt omgezet naar de paginatitel.

Zie `/libs/cq/reporting/components/auditreport/pagecol/definitions/data`.

```xml
N:data
    P:resolver=path
    N:resolverConfig
        P:propertyName="jcr:title"
        P:subPath="/jcr:content"
```

**Padextensie**

In het volgende voorbeeld wordt een waarde `de` met de padextensie toegevoegd `/libs/wcm/core/resources/languages`en wordt de waarde van de eigenschap opgehaald `language`om de landcode `de` op te lossen in de taalbeschrijving `German`.

Zie `/libs/cq/reporting/components/userreport/languagecol/definitions/data`.

```xml
N:data
    P:resolver=pathextension
    N:resolverConfig
        P:path="/libs/wcm/core/resources/languages"
        P:propertyName="language"
```

#### Voorbewerken {#preprocessing}

De `preprocessing` definitie kan worden toegepast op:

* oorspronkelijke waarde:

   De voorbewerkingsdefinitie voor de oorspronkelijke waarde wordt opgegeven op `apply` en/of `applyAfter` rechtstreeks.

* waarde in geaggregeerde toestand:

   Indien nodig kan voor elke aggregatie een aparte definitie worden gegeven.

   Om expliciete voorbewerking voor samengevoegde waarden te specificeren, moeten de preverwerkingsdefinities op een respectieve `aggregated` kindknoop ( `apply/aggregated`, `applyAfter/aggregated`) verblijven. Als expliciete voorbewerking voor verschillende aggregaten wordt vereist, wordt de preverwerkingsdefinitie gevestigd op een kindknoop met de naam van het respectieve aggregaat (bijvoorbeeld `apply/aggregated/min/max` of andere aggregaten).

U kunt een van de volgende twee opties opgeven om tijdens de voorbehandeling te gebruiken:

* [zoek- en vervangingspatronen](#preprocessing-find-and-replace-patterns)Wanneer deze worden gevonden, wordt het opgegeven patroon (dat wordt gedefinieerd als een reguliere expressie) vervangen door een ander patroon. Dit kan bijvoorbeeld worden gebruikt om een subtekenreeks van het origineel te extraheren.

* [gegevenstypeopmaakprogramma&#39;s](#preprocessing-data-type-formatters)

   Zet een numerieke waarde om in een relatieve tekenreeks; de waarde &quot;die een tijdsverschil van 1 uur vertegenwoordigt, wordt bijvoorbeeld omgezet in een tekenreeks zoals `1:24PM (1 hour ago)`.

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

Voor preprocessing kunt u een `pattern` (gedefinieerd als een [reguliere expressie](https://en.wikipedia.org/wiki/Regular_expression) of regex) opgeven die zich bevindt en vervolgens wordt vervangen door het `replace` patroon:

* `pattern`

   De reguliere expressie die wordt gebruikt om een subtekenreeks te zoeken.

* `replace`

   De tekenreeks, of representatie van de tekenreeks, die wordt gebruikt als vervanging voor de oorspronkelijke tekenreeks. Vaak vertegenwoordigt dit een subtekenreeks van de tekenreeks die zich door de reguliere expressie bevindt `pattern`.

Een voorbeeldvervanging kan als worden verdeeld:

* Voor het knooppunt `definitions/data/preprocessing/apply` met de volgende twee eigenschappen:

   * `pattern`: `(.*)(/jcr:content)(/|$)(.*)`
   * `replace`: `$1`

* Een tekenreeks die aankomt als:

   * `/content/geometrixx/en/services/jcr:content/par/text`

* Wordt opgedeeld in vier secties:

   * `$1` - `(.*)` - `/content/geometrixx/en/services`
   * `$2` - `(/jcr:content)` - `/jcr:content`
   * `$3` - `(/|$)` - `/`
   * `$4` - `(.*)` - `par/text`

* En vervangen door de tekenreeks die wordt vertegenwoordigd door `$1`:

   * `/content/geometrixx/en/services`

#### voorbewerken - Formatters voor gegevenstypen {#preprocessing-data-type-formatters}

Deze formatters zetten een numerieke waarde in een relatieve koord om.

Dit kan bijvoorbeeld worden gebruikt voor een tijdkolom die aggregaten toestaat `min`, `avg` en `max` . Als `min`/ `avg`/ `max` aggregaten worden weergegeven als een *tijdverschil* (bijvoorbeeld `10 days ago`), is een gegevensformatter vereist. Hiervoor wordt een `datedelta` formatter toegepast op de `min`/ `avg`/ `max` geaggregeerde waarden. Als er ook een `count` aggregaat beschikbaar is, is hiervoor geen opmaakfunctie nodig. De oorspronkelijke waarde wordt ook niet ondersteund.

Momenteel zijn de beschikbare gegevenstypeformatters:

* `format`

   Formatter voor gegevenstypen:

   * `duration`

      De duur is de tijdspanne tussen twee bepaalde data. Bijvoorbeeld het begin en einde van een werkstroomactie die 1 uur heeft geduurd, te beginnen op 13/13/11 11:23u en eindigend één uur later op 13/11 12:23u.

      Het zet een numerieke waarde (die als milliseconden wordt geïnterpreteerd) in een duurkoord om; is bijvoorbeeld `30000` opgemaakt als * `30s`.*

   * `datedelta`

      Datadelta is de tijdspanwijdte tussen een datum in het verleden tot &quot;nu&quot;(zodat zal het een verschillend resultaat hebben als het rapport op een later punt in tijd wordt bekeken).

      De numerieke waarde (geïnterpreteerd als een tijdverschil in dagen) wordt omgezet in een relatieve datumtekenreeks. 1 is bijvoorbeeld opgemaakt als 1 dag geleden.

In het volgende voorbeeld wordt `datedelta` opmaak voor `min` en `max` aggregaten gedefinieerd:

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

      Wordt gebruikt voor waarden die verschillende waarden gebruiken (zoals overgenomen uit verschillende eigenschappen) voor het sorteren en weergeven.
   Daarnaast. een van de bovenstaande punten kan worden gedefinieerd als meerwaarden; definieert bijvoorbeeld `string[]` een array met tekenreeksen.

   De waarde-extractor wordt gekozen door het kolomtype. Als een waarde-extractor beschikbaar is voor een kolomtype, wordt deze extractor gebruikt. Anders wordt de standaardwaarde voor de extractor gebruikt.

   Een type kan (optioneel) een parameter nemen. Extraheert bijvoorbeeld het jaar uit een datumveld. `timeslot:year` Typen met de bijbehorende parameters:

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

         Filter wordt toegepast op onbewerkte gegevens.

      * `preprocessed`

         Filter wordt toegepast op vooraf verwerkte gegevens.

      * `resolved`

         Filter wordt toegepast op omgezette gegevens.


* `aggregates`

   Samengevoegde definities.

   * `text`

      De tekstnaam van het aggregaat. Indien `text` niet gespecificeerd, dan zal het de standaardbeschrijving van het aggregaat nemen; bijvoorbeeld , `minimum` zal voor het `min` aggregaat worden gebruikt .

   * `type`

      Samengevoegde tekst. Beschikbare aggregaten zijn:

      * `count`

         Telt het aantal rijen.

      * `count-nonempty`

         Telt het aantal niet-lege rijen.

      * `min`

         Geeft de minimumwaarde op.

      * `max`

         Geeft de maximumwaarde op.

      * `average`

         Verstrekt de gemiddelde waarde.

      * `sum`

         Verschaft de som van alle waarden.

      * `median`

         Geeft de mediaanwaarde.

      * `percentile95`

         Neemt het 95e percentiel van alle waarden.

### Standaardwaarden kolom {#column-default-values}

Hiermee definieert u standaardwaarden voor de kolom:

```xml
N:defaults
    P:aggregate
```

* `aggregate`

   Geldige `aggregate` waarden zijn dezelfde als voor `type` onder `aggregates` (zie [Kolomspecifieke Definities (definities - filters / aggregaten)](#column-specific-definitions) ).

### Gebeurtenissen en handelingen {#events-and-actions}

Edit Configuration definieert de gebeurtenissen die de listeners nodig hebben om te detecteren en de handelingen die moeten worden toegepast nadat deze gebeurtenissen hebben plaatsgevonden. Zie de [inleiding aan componentenontwikkeling](/help/sites-developing/components.md) voor achtergrondinformatie.

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

Zij gebruiken een (standaard) dialoog, dat u aanpast, voor de individuele generische component. Dit dialoogvenster staat de rapportgebruiker toe om de kolomeigenschappen van een generische kolom op de rapportpagina te bepalen (gebruikend de eigenschappen van de **Kolom van de menuoptie...**).

Een voorbeeld is de **Algemene** kolom van het **Rapport** van de Gebruiker; zie `/libs/cq/reporting/components/userreport/genericcol`.

Een kolom algemeen maken:

* Stel de `type` eigenschap van het `definition` knooppunt van de kolom in op `generic`.

   Zie `/libs/cq/reporting/components/userreport/genericcol/definitions`

* Geef een definitie van het dialoogvenster (standaard) op onder het `definition` knooppunt van de kolom.

   Zie `/libs/cq/reporting/components/userreport/genericcol/definitions/dialog`

   * De velden van het dialoogvenster moeten naar dezelfde namen verwijzen als de bijbehorende componenteigenschap (inclusief het pad).

      Als u bijvoorbeeld het type algemene kolom configureerbaar wilt maken via het dialoogvenster, gebruikt u een veld met de naam `./definitions/type`.

   * Eigenschappen die zijn gedefinieerd met de interface/het dialoogvenster hebben voorrang op eigenschappen die zijn gedefinieerd voor de `columnbase` component.

* Bepaal de Edit Configuratie.

   Zie `/libs/cq/reporting/components/userreport/genericcol/cq:editConfig`

* Gebruik standaard AEM-methoden om (aanvullende) kolomeigenschappen te definiëren.

   Merk op dat voor eigenschappen die op zowel de component als de kolominstanties worden bepaald, de waarde op de kolominstantie belangrijkheid neemt.

   De eigenschappen die beschikbaar zijn voor een algemene kolom zijn:

   * `jcr:title` - kolomnaam
   * `definitions/aggregates` - aggregaten
   * `definitions/filters` - filters
   * `definitions/type`- het type kolom (dit moet in het dialoogvenster worden gedefinieerd met een kiezer/keuzelijst of een verborgen veld)
   * `definitions/data/resolver` en `definitions/data/resolverConfig` (maar niet `definitions/data/preprocessing` of `.../clientFilter`) - de oplosser en configuratie
   * `definitions/queryBuilder` - de configuratie van de vraagbouwer
   * `defaults/aggregate` - het standaardaggregaat
   In het geval van een nieuw geval van de generische kolom op het Rapport **van de** Gebruiker worden de eigenschappen die met de dialoog worden bepaald voortgeduurd onder:

   `/etc/reports/userreport/jcr:content/report/columns/genericcol/settings/generic`

## Rapportontwerp {#report-design}

Het ontwerp bepaalt welke kolomtypes voor het creëren van een rapport beschikbaar zijn. Het definieert ook het alineasysteem waaraan de kolommen worden toegevoegd.

U wordt sterk geadviseerd om een individueel ontwerp voor elk rapport tot stand te brengen. Dit zorgt voor volledige flexibiliteit. Zie ook [Uw nieuw rapport](#defining-your-new-report)definiëren.

De standaardrapporteringscomponenten worden aangehouden onder `/etc/designs/reports`.

De locatie voor uw rapporten kan afhankelijk zijn van de locatie van uw componenten:

* `/etc/designs/reports/<yourReport>` geschikt is als het rapport zich onderaan bevindt `/apps/cq/reporting`

* `/etc/designs/<yourProject>/reports/<*yourReport*>` voor rapporten die het `/apps/<yourProject>/reports` patroon gebruiken

De vereiste ontwerpeigenschappen worden geregistreerd op `jcr:content/reportpage/report/columns` (bijvoorbeeld `/etc/designs/reports/<reportName>/jcr:content/reportpage/report/columns`):

* `components`

   Om het even welke componenten en/of componentengroepen die op het rapport worden toegestaan.

* `sling:resourceType`

   Eigenschap met waarde `cq/reporting/components/repparsys`.

Een voorbeeldontwerpfragment (dat is ontleend aan het ontwerp van het componentenrapport) is:

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
>U wordt aangeraden geen wijzigingen aan te brengen in de standaardrapportontwerpen. Dit om ervoor te zorgen dat u geen veranderingen verliest wanneer het bevorderen van of het installeren van hotfixes.
>
>Kopieer het rapport en het ontwerp als u een standaardrapport wilt aanpassen.

>[!NOTE]
>
>De standaardkolommen kunnen automatisch worden gecreeerd wanneer een rapport wordt gecreeerd. Deze worden in de sjabloon opgegeven.

## Rapportsjabloon {#report-template}

Elk rapporttype moet een malplaatje verstrekken. Dit zijn standaard [CQ-sjablonen](/help/sites-developing/templates.md) en kunnen als zodanig worden geconfigureerd.

De sjabloon moet:

* instellen `sling:resourceType` op `cq/reporting/components/reportpage`

* het te gebruiken ontwerp
* een `report` onderliggende node maken die via de `reportbase`eigenschap naar de container-component ( `sling:resourceType` ) verwijst

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

Het wordt echter ten zeerste aanbevolen deze knooppunten niet bij te werken, maar zelf componentknooppunten te maken onder `/apps/cq/reporting/templates` of, indien dit meer aangewezen is, `/apps/<yourProject>/reports/templates`.

Waar, als voorbeeld (zie ook [Plaats van de Componenten](#location-of-report-components)van het Rapport):

```xml
N:apps
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:templates [sling:Folder]
```

Onder dit maakt u de basis voor uw sjabloon:

```xml
N:apps
    N:cq [nt:folder]
        N:reporting|reports [sling:Folder]
            N:templates [sling:Folder]
                N:<reportname> [sling:Folder]
```

## Uw eigen rapport maken - een voorbeeld {#creating-your-own-report-an-example}

### Uw nieuwe rapport definiëren {#defining-your-new-report}

Om een nieuw rapport te bepalen moet u creëren en vormen:

1. De wortel voor uw rapportcomponenten.
1. De rapportbasiscomponent.
1. Een of meer basiscomponenten van kolommen.
1. Het rapportontwerp.
1. De wortel voor uw rapportmalplaatje.
1. Het rapportmalplaatje.

Om deze stappen te illustreren, bepaalt het volgende voorbeeld een rapport dat van alle configuraties OSGi binnen de bewaarplaats een lijst maakt; d.w.z. alle instanties van het `sling:OsgiConfig` knooppunt.

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

1. Bepaal uw rapportbasis. Bijvoorbeeld `osgireport[cq:Component]` onder `/apps/cq/reporting/components/osgireport`.

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
   * geeft zowel `pie` als `lineseries` grafieken weer
   * verstrekt een dialoog voor de gebruiker om het rapport te vormen

1. Definieer de eerste kolomcomponent (columnBase). Bijvoorbeeld `bundlecol[cq:Component]` onder `/apps/cq/reporting/components/osgireport`.

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

   Dit bepaalt een kolombasiscomponent die:

   * zoekt naar en retourneert de waarde die het van de server ontvangt; in dit geval, het bezit `jcr:path` voor elke `sling:OsgiConfig` knoop
   * levert het `count` aggregaat
   * is niet gegroepeerd
   * heeft de titel `Bundle` (kolomtitel binnen de tabel)
   * bevindt zich in de groep sidekick `OSGi Report`
   * Vernieuwingen bij opgegeven gebeurtenissen
   >[!NOTE]
   >
   >In dit voorbeeld zijn er geen definities van `N:data` en `P:clientFilter`. De reden hiervoor is dat de waarde die van de server wordt ontvangen, op een 1:1-basis wordt geretourneerd. Dit is het standaardgedrag.
   >
   >Dit is hetzelfde als de definities:
   >
   >
   ```
   >N:data [nt:unstructured]
   >   P:clientFilter [String] = "function(v) { return v; }"
   >```
   >
   >Waar de functie gewoon de waarde retourneert die deze ontvangt.

1. Bepaal uw rapportontwerp. Bijvoorbeeld `osgireport[cq:Page]` onder `/etc/designs/reports`.

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

1. Bepaal uw rapportmalplaatje. Bijvoorbeeld `osgireport[cq:Template]` onder `/apps/cq/reporting/templates`.

   ```xml
   N:osgireport [cq:Template]
       P:allowedPaths [String[]] = "/etc/reports(/.*)?"
       P:jcr:description [String] = "Use this report generator to create a new OSGi report."
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

   * bepaalt de `allowedPaths` voor de resulterende rapporten - in bovenstaand geval `/etc/reports`
   * biedt titels en beschrijvingen voor de sjabloon
   * verstrekt een duimnagelbeeld voor gebruik in de malplaatjelijst (de volledige definitie van dit knooppunt is hierboven niet vermeld - het is het gemakkelijkst om een geval van thumbnail.png van een bestaand rapport te kopiëren).

### Het creëren van een Instantie van Uw Nieuw Rapport {#creating-an-instance-of-your-new-report}

Een geval van uw nieuw rapport kan nu worden gecreeerd:

1. Open de **console van Hulpmiddelen** .

1. Selecteer **Rapporten** in de linkerruit.
1. Dan **Nieuw...** op de werkbalk. Bepaal een **Titel** en een **Naam**, selecteer uw nieuw rapporttype (het Malplaatje **van het Rapport** OSGi) van de lijst van malplaatjes, dan klik **creëren**.
1. Uw nieuwe rapportexemplaar zal in de lijst verschijnen. Dubbelklik hierop om te openen.
1. Sleep een component (voor dit voorbeeld, **Bundel** in de **OSGi groep van het Rapport** ) van sidekick om de eerste kolom tot stand te brengen en de rapportdefinitie [te](/help/sites-administering/reporting.md#the-basics-of-report-customization)beginnen.

   >[!NOTE]
   >
   >Aangezien dit voorbeeld geen groeperbare kolommen heeft, zijn de grafieken niet beschikbaar. Als u grafieken wilt zien, stelt u `groupable` in op `true`:
   >
   >
   ```
   >N:osgireport [sling:Folder]
   > N:bundlecol [cq:Component]
   > N:definitions [nt:unstructured]
   > P:groupable [Boolean] = true
   >```

## Het vormen van de Diensten van het Kader van het Rapport {#configuring-the-report-framework-services}

Deze sectie beschrijft geavanceerde configuratieopties voor de diensten OSGi die het rapportkader uitvoeren.

Deze kunnen worden bekeken gebruikend het menu van de Configuratie van de Webconsole (beschikbaar bijvoorbeeld bij `http://localhost:4502/system/console/configMgr`). Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie het [Vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

### Basisservice (CQ-rapportconfiguratie op de dag) {#basic-service-day-cq-reporting-configuration}

* **De tijdzone** bepaalt de historische gegevens van timezone voor wordt gecreeerd. Dit moet ervoor zorgen dat de historische grafiek de zelfde gegevens voor elke gebruiker over de wereld toont.
* **Landinstelling** definieert de landinstelling die moet worden gebruikt in combinatie met de **tijdzone** voor historische gegevens. De landinstelling wordt gebruikt om bepaalde landspecifieke kalenderinstellingen te bepalen (bijvoorbeeld of de eerste dag van een week zondag of maandag is).

* **Het pad** voor momentopnamen definieert het hoofdpad waar momentopnamen voor historische grafieken worden opgeslagen.
* **Het pad naar rapporten** definieert het pad waar rapporten zich bevinden. Dit wordt gebruikt door de momentopnameservice om de rapporten te bepalen om momentopnamen voor eigenlijk te nemen.
* **Dagelijkse momentopnamen** bepalen het uur van elke dag wanneer de dagelijkse momentopnamen worden genomen. Het opgegeven uur bevindt zich in de lokale tijdzone van de server.
* **Uurmomentopnamen** bepalen de minuut van elk uur wanneer uurmomentopnamen worden genomen.
* **De rijen (maximum)** bepalen het maximumaantal rijen die voor elke momentopname worden opgeslagen. Deze waarde moet redelijkerwijs worden gekozen; als het te hoog is, zal dit de grootte van de gegevensopslagruimte beïnvloeden, als het te laag is, kunnen gegevens niet accuraat zijn vanwege de manier waarop historische gegevens worden verwerkt.
* **Gegevens** van de mislukking, indien toegelaten, kunnen de valse historische gegevens worden gecreeerd door de `fakedata` selecteur te gebruiken; als deze optie is uitgeschakeld, genereert het gebruik van de `fakedata` kiezer een uitzondering.

   Aangezien de gegevens vals zijn moet het *slechts* voor het testen en het zuiveren doeleinden worden gebruikt.

   Het gebruiken van de `fakedata` selecteur zal impliciet het rapport beëindigen, zodat zullen alle bestaande gegevens worden verloren; gegevens kunnen handmatig worden hersteld, maar dit kan een tijdrovend proces zijn.

* **De gebruiker** van de momentopname bepaalt een facultatieve gebruiker die voor het nemen van momentopnamen kan worden gebruikt.

   In feite worden momentopnamen gemaakt voor de gebruiker die het rapport heeft voltooid. Er kunnen situaties zijn (bijvoorbeeld op een publicatiesysteem, waar deze gebruiker niet bestaat omdat zijn account niet is gerepliceerd) waarin u een fallback-gebruiker wilt opgeven die in plaats daarvan wordt gebruikt.

   Bovendien kan het opgeven van een gebruiker een beveiligingsrisico inhouden.

* **De gebruiker** van de momentopname afdwingen, indien toegelaten, zullen alle momentopnamen met de gebruiker worden genomen die onder de gebruiker van de *Momentopname wordt gespecificeerd*. Dit kan ernstige gevolgen hebben voor de veiligheid als het niet correct wordt behandeld.

### Cacheinstellingen (CQ-rapportagecache dag) {#cache-settings-day-cq-reporting-cache}

* **Laat toe** u toe om het caching van rapportgegevens toe te laten of onbruikbaar te maken. Het toelaten van het rapportgeheime voorgeheugen zal rapportgegevens in geheugen tijdens verscheidene verzoeken houden. Dit kan de prestaties verhogen, maar zal leiden tot een hoger geheugengebruik en kan in extreme omstandigheden leiden tot een gebrek aan geheugen.
* **TTL** bepaalt de tijd (in seconden) waarvoor de rapportgegevens in het voorgeheugen onder worden gebracht. Een hoger getal zal de prestaties verhogen, maar kan ook onjuiste gegevens retourneren als de gegevens binnen de tijdsperiode veranderen.
* **Max. items** definiëren het maximumaantal rapporten dat tegelijkertijd in de cache moet worden opgeslagen.

>[!NOTE]
>
>De rapportgegevens kunnen voor elke gebruiker en taal verschillend zijn. Daarom worden de rapportgegevens in het voorgeheugen ondergebracht per rapport, gebruiker en taal. Dit betekent dat een **Max ingangswaarde** van `2` eigenlijk gegevens voor één van beiden in cache plaatst:
>
>* één rapport voor twee gebruikers met verschillende taalmontages
>* één gebruiker en twee rapporten
>



