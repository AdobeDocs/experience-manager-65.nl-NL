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

Adobe Experience Manager (AEM) verstrekt een selectie van [ standaardrapporten ](/help/sites-administering/reporting.md) de meesten zijn gebaseerd op een rapporteringskader.

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
>Het leerprogramma [ Creërend Uw Eigen Rapport - een Voorbeeld ](#creating-your-own-report-an-example) toont ook hoeveel van de hieronder principes kunnen worden gebruikt.
>
>U kunt ook naar de standaardrapporten verwijzen om andere voorbeelden van implementatie te zien.

>[!NOTE]
>
>In de volgende voorbeelden en definities wordt de volgende notatie gebruikt:
>
>* Elke regel definieert een knooppunt of een eigenschap waarbij:
>  `N:<name> [<nodeType>]` : Beschrijft een knoop met de naam van `<*name*>` en knooptype van `<*nodeType*>`*.*
>  `P:<name> [<propertyType]` : Beschrijft een eigenschap met de naam `<*name*>` en een eigenschapstype `<*propertyType*>` .
>  `P:<name> = <value>` : Beschrijft een eigenschap `<name>` die moet worden ingesteld op de waarde van `<value>` .
>
>* De inspringing toont de hiërarchische gebiedsdelen tussen de knopen.
>* Items gescheiden door | duidt een lijst van mogelijke punten aan; bijvoorbeeld, types of namen; bijvoorbeeld, `String|String[]` betekent dat het bezit of Koord of Koord [] kan zijn.
>
>* `[]` toont een serie; zoals Koord [] of een serie van knopen zoals in de [ Definitie van de Vraag ](#query-definition).
>
>Tenzij anders vermeld zijn de standaardtypes:
>
>* Knooppunten - `nt:unstructured`
>* Eigenschappen - `String`

## Rapportagekader {#reporting-framework}

Het rapportagekader werkt aan de volgende beginselen:

* Het is volledig gebaseerd op resultaatreeksen die door een vraag zijn teruggekeerd die door CQ5 wordt uitgevoerd QueryBuilder.
* De resultaatreeks bepaalt de gegevens die in het rapport worden getoond. Elke rij in de resultaatreeks beantwoordt aan een rij in de tabelmening van het rapport.
* De verrichtingen beschikbaar voor uitvoering op de resultaatreeks lijken op concepten RDBMS; hoofdzakelijk *groeperend* en *samenvoeging*.

* De meeste gegevens worden opgehaald en verwerkt op de server.
* De klant is alleen verantwoordelijk voor de weergave van de vooraf verwerkte gegevens. Alleen kleine verwerkingstaken (bijvoorbeeld het maken van koppelingen in celinhoud) worden op de client uitgevoerd.

Het rapportagekader (geïllustreerd door de structuur van een standaardrapport) gebruikt de volgende bouwstenen, die door de verwerkingswachtrij worden gevoed:

![ chlimage_1-248 ](assets/chlimage_1-248.png)

### Rapportpagina {#report-page}

De rapportpagina is:

* Een standaard CQ5-pagina.
* Gebaseerd op a [ standaardCQ5 malplaatje, dat voor het rapport ](#report-template) wordt gevormd.

### Rapportbasis {#report-base}

De [`reportbase` component ](#report-base-component) vormt de basis van om het even welk rapport omdat het:

* Behoudt de definitie van de [ vraag ](#the-query-and-data-retrieval) die de onderliggende resultaatreeks gegevens levert.

* Het is een aangepast alineasysteem dat alle kolommen ( `columnbase`) bevat die aan het rapport zijn toegevoegd.
* Bepaalt welke grafiektypes beschikbaar zijn en die momenteel actief zijn.
* Bepaalt de Edit dialoogdoos, die de gebruiker toestaat om bepaalde aspecten van het rapport te vormen.

### Kolombasis {#column-base}

Elke kolom is een geval van de [`columnbase` component ](#column-base-component) die:

* Is een paragraaf, die door parsys ( `reportbase`) van het respectieve rapport wordt gebruikt.
* Bepaalt de verbinding aan de [ onderliggende resultaatreeks ](#the-query-and-data-retrieval). Met andere woorden, het definieert de specifieke gegevens waarnaar in deze resultaatset wordt verwezen, en hoe deze worden verwerkt.
* Hiermee behoudt u aanvullende definities, zoals de beschikbare aggregaten en filters, en eventuele standaardwaarden.

### De query en het ophalen van gegevens {#the-query-and-data-retrieval}

De query:

* Is gedefinieerd als onderdeel van de component [`reportbase`](#report-base) .
* Is gebaseerd op [ CQ QueryBuilder ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/search/QueryBuilder.html).
* Haalt de gegevens op die als basis voor het rapport worden gebruikt. Elke rij van de resultaatreeks (lijst) is gebonden aan een knoop zoals teruggekeerd door de vraag. De specifieke informatie voor [ individuele kolommen ](#column-base-component) wordt dan gehaald uit deze gegevensreeks.

* Bestaat gewoonlijk uit:

   * Een hoofdpad.

     Hiermee wordt de substructuur van de gegevensopslagruimte aangegeven die moet worden doorzocht.

     Om de invloed op de prestaties tot een minimum te beperken, is het raadzaam (probeer) de query te beperken tot een specifieke substructuur van de repository. De wortelweg kan of vooraf bepaald in het [ rapportmalplaatje ](#report-template) zijn of door de gebruiker in de [ Configuratie (geef uit) dialoogdoos ](#configuration-dialog) worden geplaatst.

   * [ Één of meerdere criteria ](#query-definition).

     Deze worden opgelegd om de (aanvankelijke) resultaatreeks te produceren; zij omvatten, bijvoorbeeld, beperkingen op het knooptype, of bezitsbeperkingen.

**het belangrijkste punt hier is dat elke enige knoop die in de resultaatreeks van de vraag is teruggekeerd wordt gebruikt om één enkele rij op het rapport (zo een 1:1 verhouding) te produceren.**

De ontwikkelaar moet ervoor zorgen dat de vraag die voor een rapport wordt bepaald een knoop terugkeert die aangewezen voor dat rapport wordt geplaatst. Nochtans, te hoeven de knoop zelf niet om alle vereiste informatie te houden, kan dit ook uit ouder en/of kindknopen worden afgeleid. Bijvoorbeeld, selecteert de vraag die voor het [ Rapport van de Gebruiker ](/help/sites-administering/reporting.md#user-report) wordt gebruikt knopen die op het knooptype (in dit geval `rep:user` worden gebaseerd). De meeste kolommen in dit rapport nemen hun gegevens echter niet rechtstreeks van deze knooppunten over, maar van de onderliggende knooppunten `profile` .

### Bezig met verwerken wachtrij {#processing-queue}

De [ vraag ](#the-query-and-data-retrieval) keert een resultaatreeks gegevens terug die als rijen op het rapport moeten worden getoond. Elke rij in de resultaatreeks wordt verwerkt (server-kant), in [ verscheidene fasen ](#phases-of-the-processing-queue), alvorens wordt overgebracht naar de cliënt voor vertoning op het rapport.

Hierdoor is het mogelijk:

* Waarden extraheren en afleiden van de onderliggende resultaatset.

  U kunt bijvoorbeeld twee eigenschapswaarden als één waarde verwerken door het verschil tussen de twee waarden te berekenen.

* Oplossen van geëxtraheerde waarden. Dit kan op verschillende manieren worden gedaan.

  Bijvoorbeeld, kunnen de wegen aan een titel (zoals in de meer mens-leesbare inhoud van respectieve *jcr worden in kaart gebracht:titel* bezit).

* Filters toepassen op verschillende punten.
* Indien nodig samengestelde waarden maken.

  Bijvoorbeeld bestaande uit een tekst die aan de gebruiker wordt getoond, een waarde die voor het sorteren en een extra URL moet worden gebruikt die (op de cliëntkant) voor het creëren van een verbinding wordt gebruikt.

#### Workflow van de verwerkingswachtrij {#workflow-of-the-processing-queue}

De volgende workflow vertegenwoordigt de verwerkingswachtrij:

![ chlimage_1-249 ](assets/chlimage_1-249.png)

#### Fasen van de Verwerkingswachtrij {#phases-of-the-processing-queue}

Waar de gedetailleerde stappen en elementen zijn:

1. Transformeert de resultaten die door de [ aanvankelijke vraag (reportbase) ](#query-definition) zijn teruggekeerd in de basisresultaatreeks gebruikend waardeextractors.

   De extractors van de waarde worden automatisch gekozen afhankelijk van het [ kolomtype ](#column-specific-definitions). Deze worden gebruikt voor het lezen van waarden van de onderliggende JCR-query en het maken van een resultaatset op basis daarvan; waarna verdere verwerking kan worden toegepast. Voor het type `diff` leest de value extractor bijvoorbeeld twee eigenschappen en berekent deze de enkele waarde die vervolgens aan de resultatenset wordt toegevoegd. De waarde-extractors kunnen niet worden geconfigureerd.

1. Aan die aanvankelijke resultaatreeks, die ruwe gegevens bevatten, [ aanvankelijke het filtreren ](#column-specific-definitions) (*ruwe* fase) wordt toegepast.

1. De waarden zijn [ preprocessing ](#processing-queue); zoals die voor *worden bepaald* fase van toepassing is.

1. [ het Filtreren ](#column-specific-definitions) (die aan de *wordt toegewezen preprocessing* fase) wordt uitgevoerd op de vooraf verwerkte waarden.

1. De waarden worden opgelost; volgens [ bepaalde resolver ](#processing-queue).
1. [ het Filtreren ](#column-specific-definitions) (die aan de *wordt toegewezen* fase) wordt uitgevoerd op de opgeloste waarden.

1. Het gegeven is [ gegroepeerd en samengevoegd ](#column-specific-definitions).
1. Arraygegevens worden omgezet in een (op tekenreeks gebaseerde) lijst.

   Dit is een impliciete stap die een resultaat met meerdere waarden omzet in een lijst die kan worden weergegeven; het is vereist voor (niet-geaggregeerde) celwaarden die zijn gebaseerd op JCR-eigenschappen met meerdere waarden.

1. De waarden zijn opnieuw [ preprocessing ](#processing-queue); zoals bepaald voor *afterApply* fase.

1. Gegevens worden gesorteerd.
1. De verwerkte gegevens worden naar de client overgedragen.

>[!NOTE]
>
>De eerste query die de resultaatset van de basisgegevens retourneert, wordt gedefinieerd voor de component `reportbase` .
>
>Andere elementen van de verwerkingswachtrij worden gedefinieerd voor de `columnbase` -componenten.

## Constructie en configuratie van rapporten {#report-construction-and-configuration}

Het volgende is nodig om een rapport te construeren en te vormen:

* a [ plaats voor de definitie van uw rapportcomponenten ](#location-of-report-components)
* a [`reportbase` component ](#report-base-component)
* één, of meerdere, [`columnbase` componenten ](#column-base-component)
* a [ paginacomponent ](#page-component)
* a [ rapportontwerp ](#report-design)
* a [ rapportmalplaatje ](#report-template)

### Locatie van rapportcomponenten {#location-of-report-components}

De standaardrapporteringscomponenten worden gehouden onder `/libs/cq/reporting/components`.

U wordt echter aangeraden deze knooppunten niet bij te werken, maar zelf componentknooppunten te maken onder `/apps/cq/reporting/components` of, indien beter, onder `/apps/<yourProject>/reports/components` .

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

Een rapportpagina moet de `sling:resourceType` van `/libs/cq/reporting/components/reportpage` gebruiken.

Een aangepaste pagina-component is niet nodig (gewoonlijk).

## Basiscomponent rapporteren {#report-base-component}

Elk rapporttype vereist een containercomponent die van `/libs/cq/reporting/components/reportbase` wordt afgeleid.

Deze component fungeert als container voor het rapport als geheel en biedt informatie voor:

* De [ vraagdefinitie ](#query-definition).
* Een [ (facultatieve) dialoog ](#configuration-dialog) voor het vormen van het rapport.
* Om het even welke [ Helden ](#chart-definitions) die met het rapport worden geïntegreerd.

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

  Retourneert alle `textimage` -componenten die het laatst door de `admin` -gebruiker zijn gewijzigd.

* `nodeTypes`

  Wordt gebruikt om het resultaat te beperken tot de opgegeven knooppunttypen. U kunt meerdere knooppunttypen opgeven.

* `mandatoryProperties`

  Beperkt het resultaat dat aan knopen wordt geplaatst die *alle* de gespecificeerde eigenschappen hebben. De waarde van de eigenschappen wordt niet verwerkt.

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

     Aangezien er meerdere instellingen kunnen worden gedefinieerd, kunt u dit gebruiken om te definiëren welke momenteel actief zijn. Deze worden gedefinieerd door een array van knooppunten (er is geen verplichte naamgevingsconventie voor deze knooppunten, maar in de standaardrapporten wordt vaak `0`, `1` gebruikt.. `x`), met elk de volgende eigenschap:

      * `id`

        Identificatie voor de actieve diagrammen. Dit moet overeenkomen met de id van een van de diagrammen `definitions` .

* `definitions`

  Bepaalt de grafiektypes die potentieel voor het rapport beschikbaar zijn. De `definitions` die moet worden gebruikt, wordt opgegeven door de `active` -instellingen.

  De definities worden opgegeven met behulp van een array met knooppunten (ook hier `0` , `1` . `x`), elk met de volgende eigenschappen:

   * `id`

     De identificatie van het diagram.

   * `type`

     Het type beschikbare grafiek. Selecteren uit:

      * `pie`
Cirkeldiagram. Alleen gegenereerd op basis van huidige gegevens.

      * `lineseries`
Reeks lijnen (verbindende punten die de daadwerkelijke momentopnamen vertegenwoordigen). Alleen gegenereerd op basis van historische gegevens.

   * Er zijn aanvullende eigenschappen beschikbaar, afhankelijk van het diagramtype:

      * voor het diagramtype `pie` :

         * `maxRadius` ( `Double/Long`)

           De maximumstraal die voor het cirkeldiagram wordt toegestaan; daarom de maximumgrootte die voor de grafiek (zonder legenda) wordt toegestaan. Genegeerd als `fixedRadius` is gedefinieerd.

         * `minRadius` ( `Double/Long`)

           De minimale straal die is toegestaan voor het cirkeldiagram. Genegeerd als `fixedRadius` is gedefinieerd.

         * `fixedRadius` ( `Double/Long`)
Hiermee definieert u een vaste straal voor het cirkeldiagram.

      * voor het diagramtype [`lineseries`](/help/sites-administering/reporting.md#display-limits) :

         * `totals` ( `Boolean`)

           Waar als een extra lijn die **toont Totaal** zou moeten worden getoond.
default: `false`

         * `series` ( `Long`)

           Aantal weer te geven lijnen/reeksen.
standaard: `9` (dit is ook het toegestane maximum)

         * `hoverLimit` ( `Long`)

           Maximumaantal geaggregeerde momentopnamen (punten die op elke horizontale lijn worden weergegeven en die verschillende waarden vertegenwoordigen) waarvoor pop-ups moeten worden weergegeven. Dat wil zeggen, wanneer de gebruiker de muis boven een bepaalde waarde of een bijbehorend label in de diagramlegenda houdt.

           standaard: `35` (dat wil zeggen dat er helemaal geen pop-ups worden weergegeven als er meer dan 35 verschillende waarden van toepassing zijn voor de huidige diagraminstellingen).

           Er geldt een extra limiet van tien pop-ups die parallel kunnen worden weergegeven (er kunnen meerdere pop-ups worden weergegeven wanneer de muisaanwijzer op de legenda wordt geplaatst).

### Dialoogvenster Configuratie {#configuration-dialog}

Elk rapport kan een configuratiedialoog hebben, toestaand de gebruiker om diverse parameters voor het rapport te specificeren. Deze dialoog is toegankelijk door **uitgeven** knoop wanneer de rapportpagina open is.

Dit dialoogvenster is een standaardCQ [ dialoog ](/help/sites-developing/components-basics.md#dialogs) en kan als dusdanig worden gevormd (zie [ CQ.Dialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog) voor meer informatie).

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

Er zijn verschillende vooraf geconfigureerde componenten opgegeven. Naar deze componenten kan in het dialoogvenster worden verwezen door de eigenschap `xtype` met de waarde `cqinclude` te gebruiken:

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
>De componenten waarnaar wordt verwezen, moeten worden opgenomen met het achtervoegsel `.infinity.json` (zie voorbeeld hierboven).

### Hoofdpad {#root-path}

Ook, kan een wortelweg voor het rapport worden bepaald:

* **`rootPath`**

  Dit beperkt het rapport tot een bepaalde sectie (boom of subboom) van de bewaarplaats, die voor prestatiesoptimalisering wordt geadviseerd. Het hoofdpad wordt opgegeven door de eigenschap `rootPath` van het knooppunt `report` van elke rapportpagina (die bij het maken van de pagina uit de sjabloon wordt gehaald).

  Deze kan worden gespecificeerd door:

   * het [ rapportmalplaatje ](#report-template) (of als vaste waarde of als standaardwaarde voor de configuratiedialoog).
   * de gebruiker (met deze parameter)

## Basiscomponent kolom {#column-base-component}

Voor elk kolomtype is een component vereist die is afgeleid van `/libs/cq/reporting/components/columnbase` .

Een kolomcomponent definieert een combinatie van het volgende:

* De [ Kolom Specifieke configuratie van de Vraag ](#column-specific-query).
* De [ Resolvers en Preprocessing ](#resolvers-and-preprocessing).
* De [ Kolom Specifieke Definities ](#column-specific-definitions) (zoals filters en aggregaten; `definitions` kindknoop).
* [ Standaardwaarden van de Kolom ](#column-default-values).
* De [ Filter van de Cliënt ](#client-filter) om de informatie voor vertoning van de gegevens te halen die door de server zijn teruggekeerd.
* Een kolomcomponent moet ook een geschikte instantie van `cq:editConfig` bieden. om de [ vereiste Gebeurtenissen en Acties ](#events-and-actions) te bepalen.
* De configuratie voor [ generische kolommen ](#generic-columns).

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

Zie ook [ die Uw Nieuw Rapport ](#defining-your-new-report) bepalen.

### Kolomspecifieke query {#column-specific-query}

Dit bepaalt de specifieke gegevensextractie (van de [ reeks van het het resultaatresultaat van rapportgegevens ](#the-query-and-data-retrieval)) voor gebruik in de individuele kolom.

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

  Als een bezit als Koord [] wordt bepaald, worden de veelvoudige eigenschappen gescand (in opeenvolging) om de daadwerkelijke waarde te vinden.

  Als er bijvoorbeeld:

  `property = [ "jcr:lastModified", "jcr:created" ]`

  De corresponderende waarde-extractor (die hier wordt beheerd):

   * Controleert of er een jcr:lastModified-eigenschap beschikbaar is en zo ja, gebruik deze.
   * Als er geen eigenschap jcr:lastModified beschikbaar is, wordt in plaats daarvan de inhoud van jcr:created gebruikt.

* `subPath`

  Als het resultaat zich niet op de knoop bevindt die door de vraag is teruggekeerd, bepaalt `subPath` waar het bezit wordt gevestigd.

* `secondaryProperty`

  Een tweede eigenschap die moet worden gebruikt voor het berekenen van de werkelijke celwaarde. Deze definitie wordt alleen gebruikt voor bepaalde kolomtypen (diff en sortable).

  Bijvoorbeeld, als er het Rapport van de Instanties van het Werkschema is, wordt het gespecificeerde bezit gebruikt om de daadwerkelijke waarde van het tijdverschil (in milliseconden) tussen begin en eindtijden op te slaan.

* `secondarySubPath`

  Gelijkaardig aan subPath, wanneer `secondaryProperty` wordt gebruikt.

Doorgaans wordt alleen `property` gebruikt.

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

De [ verwerkingsrij ](#processing-queue) bepaalt diverse resolvers en vormt preprocessing:

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

     Wijst waarden toe aan andere waarden. Dit wordt bijvoorbeeld gebruikt om constanten zoals `en` op te lossen naar de equivalente waarde `English` .

   * `default`

     De standaardoplosser. Dit is een nepoplosser die eigenlijk niets oplost.

   * `page`

     Hiermee wordt een padwaarde omgezet in het pad van de juiste pagina, nauwkeuriger naar het corresponderende knooppunt `jcr:content` . `/content/.../page/jcr:content/par/xyz` wordt bijvoorbeeld omgezet in `/content/.../page/jcr:content` .

   * `path`

     Hiermee lost u een padwaarde op door optioneel een subpad toe te voegen en de werkelijke waarde op te nemen vanuit een eigenschap van het knooppunt (zoals gedefinieerd door `resolverConfig` ) bij het omgezette pad. Een `path` van `/content/.../page/jcr:content` kan bijvoorbeeld worden omgezet in de inhoud van de eigenschap `jcr:title` , wat betekent dat een paginapad wordt omgezet in de paginatitel.

   * `pathextension`

     Hiermee lost u een waarde op door een pad vooraf in te stellen en de werkelijke waarde van een eigenschap van het knooppunt op het opgeloste pad te nemen. Een waarde `de` kan bijvoorbeeld worden voorafgegaan door een pad, zoals `/libs/wcm/core/resources/languages` , dat de waarde van de eigenschap `language` neemt, om de landcode `de` op te lossen naar de taalbeschrijving `German` .

* `resolverConfig`

  Verstrekt definities voor resolver. Welke opties beschikbaar zijn, is afhankelijk van de geselecteerde `resolver` optie:

   * `const`

     Gebruik eigenschappen om de constanten voor het omzetten op te geven. De naam van de eigenschap definieert de constante die moet worden omgezet; de waarde van de eigenschap definieert de herstelde waarde.

     Bijvoorbeeld, lost een bezit met **Naam**= `1` en **Waarde** `=One` 1 aan Één op.

   * `default`

     Geen configuratie beschikbaar.

   * `page`

      * `propertyName` (optioneel)

        Definieert de naam van de eigenschap die moet worden gebruikt voor het omzetten van de waarde. Als gespecificeerd niet, wordt de standaardwaarde van *jcr:title* (de paginatitel) gebruikt; voor `page` resolver, betekent dit dat eerst de weg aan de paginappad wordt opgelost, dan verder opgelost aan de paginatitel.

   * `path`

      * `propertyName` (optioneel)

        Specifies the name of the property that should be used for resolving the value. Als deze niet wordt opgegeven, wordt de standaardwaarde van `jcr:title` gebruikt.

      * `subPath` (optioneel)

        Deze eigenschap kan worden gebruikt om een achtervoegsel op te geven dat aan het pad moet worden toegevoegd voordat de waarde wordt omgezet.

   * `pathextension`

      * `path` (verplicht)

        Definieert het pad dat moet worden voorafgegaan.

      * `propertyName` (verplicht)

        Definieert de eigenschap op het omgezette pad waar de werkelijke waarde zich bevindt.

      * `i18n` (optioneel; type Boolean)

        Bepaalt of de opgeloste waarde ** zou moeten zijn geïnternationaliseerd (namelijk gebruikend [ de internationaliseringsdiensten van CQ5 ](/help/sites-administering/tc-manage.md)).

* `preprocessing`

  Het preprocessing is facultatief en kan (afzonderlijk) aan de verwerkingsfasen *worden gebonden* of *applyAfter* van toepassing zijn:

   * `apply`

     De aanvankelijke preverwerkingsfase ([ stap 3 in de vertegenwoordiging van de verwerkingsrij ](#processing-queue)).

   * `applyAfter`

     Pas na preprocessing ([ stap 9 in de vertegenwoordiging van de verwerkingsrij ](#processing-queue)) toe.

#### Resolvers {#resolvers}

De oplosmiddelen worden gebruikt om de vereiste informatie te halen. Voorbeelden van de verschillende oplosmiddelen zijn:

**Const**

In het volgende voorbeeld wordt een constante waarde van `VersionCreated` omgezet in de tekenreeks `New version created` .

Zie `/libs/cq/reporting/components/auditreport/typecol/definitions/data` .

```xml
N:data
    P:resolver=const
    N:resolverConfig
        P:VersionCreated="New version created"
```

**Pagina**

Hiermee wordt een padwaarde omgezet in de eigenschap jcr:description op het knooppunt jcr:content (child) van de bijbehorende pagina.

Zie `/libs/cq/reporting/components/compreport/pagecol/definitions/data` .

```xml
N:data
    P:resolver=page
    N:resolverConfig
        P:propertyName="jcr:description"
```

**Weg**

In het volgende voorbeeld wordt een pad van `/content/.../page` naar de inhoud van de eigenschap `jcr:title` omgezet. Dit betekent dat een paginapad wordt omgezet naar de paginatitel.

Zie `/libs/cq/reporting/components/auditreport/pagecol/definitions/data` .

```xml
N:data
    P:resolver=path
    N:resolverConfig
        P:propertyName="jcr:title"
        P:subPath="/jcr:content"
```

**Uitbreiding van de Weg**

In het volgende voorbeeld wordt een waarde `de` toegevoegd met de padextensie `/libs/wcm/core/resources/languages` en wordt de waarde opgehaald uit de eigenschap `language` om de landcode `de` op te lossen naar de taalbeschrijving `German` .

Zie `/libs/cq/reporting/components/userreport/languagecol/definitions/data` .

```xml
N:data
    P:resolver=pathextension
    N:resolverConfig
        P:path="/libs/wcm/core/resources/languages"
        P:propertyName="language"
```

#### Voorbewerken {#preprocessing}

De definitie `preprocessing` kan worden toegepast op:

* oorspronkelijke waarde:

  De voorbewerkingsdefinitie voor de oorspronkelijke waarde wordt op `apply` en/of `applyAfter` direct opgegeven.

* waarde in geaggregeerde toestand:

  Indien nodig kan voor elke aggregatie een aparte definitie worden gegeven.

  Als u expliciete voorbewerking voor geaggregeerde waarden wilt opgeven, moeten de voorbewerkingsdefinities zich op een respectievelijke `aggregated` onderliggende node ( `apply/aggregated` , `applyAfter/aggregated` ) bevinden. Als expliciete voorbewerking voor verschillende aggregaten is vereist, bevindt de voorbewerkingsdefinitie zich op een onderliggende node met de naam van het desbetreffende aggregaat (bijvoorbeeld `apply/aggregated/min/max` of andere aggregaten).

U kunt een van de volgende twee opties opgeven om tijdens de voorbehandeling te gebruiken:

* [ vind en vervang patronen ](#preprocessing-find-and-replace-patterns)
Wanneer dit wordt gevonden, wordt het opgegeven patroon (dat wordt gedefinieerd als een reguliere expressie) vervangen door een ander patroon. Dit kan bijvoorbeeld worden gebruikt om een subtekenreeks van het origineel te extraheren.

* [gegevenstypeopmaakprogramma&#39;s](#preprocessing-data-type-formatters)

  Zet een numerieke waarde om in een relatieve tekenreeks. De waarde &quot;die een tijdsverschil van één uur vertegenwoordigt, wordt bijvoorbeeld omgezet in een tekenreeks zoals `1:24PM (1 hour ago)` .

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

Voor preprocessing kunt u a `pattern` (die als a [ wordt bepaald regelmatige uitdrukking ](https://en.wikipedia.org/wiki/Regular_expression) of regex) specificeren die wordt gevestigd en dan door het `replace` patroon wordt vervangen:

* `pattern`

  De reguliere expressie die wordt gebruikt om een subtekenreeks te zoeken.

* `replace`

  De tekenreeks, of representatie van de tekenreeks, die wordt gebruikt als vervanging voor de oorspronkelijke tekenreeks. Dit vertegenwoordigt vaak een subtekenreeks van de tekenreeks die zich bevindt door de reguliere expressie `pattern` .

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

* En vervangen door de tekenreeks die wordt vertegenwoordigd door `$1` :

   * `/content/geometrixx/en/services`

#### voorbewerken - Formatters voor gegevenstypen {#preprocessing-data-type-formatters}

Deze formatters zetten een numerieke waarde in een relatieve koord om.

Dit kan bijvoorbeeld worden gebruikt voor een tijdkolom waarin `min` -, `avg` - en `max` -aggregaten zijn toegestaan. Aangezien `min`/ `avg`/ `max` aggregaten als a *tijdverschil* (bijvoorbeeld, `10 days ago`) worden getoond, vereisen zij een gegevens formatter. Hiervoor wordt een `datedelta` formatter toegepast op de `min`/ `avg`/ `max` geaggregeerde waarden. Als er ook een `count` aggregaat beschikbaar is, is hiervoor geen opmaakfunctie nodig, net als voor de oorspronkelijke waarde.

Momenteel zijn de beschikbare gegevenstypeformatters:

* `format`

  Formatter voor gegevenstype:

   * `duration`

     De duur is de tijdspanne tussen twee bepaalde data. Bijvoorbeeld het begin en einde van een werkstroomactie die één uur duurde, te beginnen bij 13/13/11 11:23u en één uur later te eindigen bij 13/11 12:23u.

     Een numerieke waarde (geïnterpreteerd als milliseconden) wordt omgezet in een duurtekenreeks. `30000` wordt bijvoorbeeld opgemaakt als * `30s` .*

   * `datedelta`

     Datadelta is de tijdspanwijdte tussen een datum in het verleden tot &quot;nu&quot;(zodat heeft het een verschillend resultaat als het rapport op een later punt in tijd wordt bekeken).

     De numerieke waarde (geïnterpreteerd als een tijdverschil in dagen) wordt omgezet in een relatieve datumtekenreeks. 1 is bijvoorbeeld een dag geleden opgemaakt.

In het volgende voorbeeld wordt `datedelta` opmaak voor `min` - en `max` aggregaten gedefinieerd:

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

  Bovendien kan elk van de bovenstaande opties worden gedefinieerd als een meerwaarde, bijvoorbeeld: `string[]` definieert een array met tekenreeksen.

  De waarde-extractor wordt gekozen door het kolomtype. Als een waarde-extractor beschikbaar is voor een kolomtype, wordt deze extractor gebruikt. Anders wordt de standaardwaarde voor de extractor gebruikt.

  Een type kan (optioneel) een parameter nemen. `timeslot:year` extraheert bijvoorbeeld het jaar uit een datumveld. Typen met de bijbehorende parameters:

   * `timeslot` - De waarden zijn vergelijkbaar met de overeenkomstige constanten van `java.utils.Calendar` .

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

     De tekstnaam van het aggregaat. Als `text` niet wordt gespecificeerd, dan neemt het de standaardbeschrijving van het aggregaat. `minimum` wordt bijvoorbeeld gebruikt voor het `min` aggregaat.

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

  Geldige `aggregate` waarden zijn het zelfde als voor `type` onder `aggregates` (zie [ de Specifieke Definities van de Kolom (definities - filters/aggregaten) ](#column-specific-definitions)).

### Gebeurtenissen en handelingen {#events-and-actions}

Edit Configuration definieert de gebeurtenissen die de listeners nodig hebben om te detecteren en de handelingen die moeten worden toegepast nadat deze gebeurtenissen hebben plaatsgevonden. Zie de [ inleiding aan componentenontwikkeling ](/help/sites-developing/components.md) voor achtergrondinformatie.

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

Zij gebruiken een (standaard) dialoogvakje dat u voor de individuele generische component kunt aanpassen. Dit dialoogvakje laat de rapportgebruiker de kolomeigenschappen van een generische kolom op de rapportpagina bepalen (gebruikend de eigenschappen van de Kolom van de menuoptie **..**).

Een voorbeeld is de **Algemene** kolom van het **Rapport van de Gebruiker**. Zie `/libs/cq/reporting/components/userreport/genericcol` .

Een kolom algemeen maken:

* Stel de eigenschap `type` van het knooppunt `definition` van de kolom in op `generic` .

  Zie `/libs/cq/reporting/components/userreport/genericcol/definitions`

* Geef een definitie van het dialoogvenster (standaard) op onder het knooppunt `definition` van de kolom.

  Zie `/libs/cq/reporting/components/userreport/genericcol/definitions/dialog`

   * De velden van het dialoogvenster moeten naar dezelfde namen verwijzen als de overeenkomende componenteigenschap, inclusief het pad.

     Als u bijvoorbeeld het type algemene kolom configureerbaar wilt maken via het dialoogvenster, gebruikt u een veld met de naam `./definitions/type` .

   * Eigenschappen die zijn gedefinieerd met de interface/het dialoogvenster hebben voorrang op eigenschappen die zijn gedefinieerd voor de component `columnbase` .

* Bepaal de Edit Configuratie.

  Zie `/libs/cq/reporting/components/userreport/genericcol/cq:editConfig`

* Gebruik standaard AEM methoden om (aanvullende) kolomeigenschappen te definiëren.

  Voor eigenschappen die op zowel de component als de kolominstanties worden bepaald, heeft de waarde op de kolominstantie belangrijkheid.

  De eigenschappen die beschikbaar zijn voor een algemene kolom zijn:

   * `jcr:title` - kolomnaam
   * `definitions/aggregates` - aggregaten
   * `definitions/filters` - filters
   * `definitions/type`- het type van de kolom (dit moet in het dialoogvenster worden gedefinieerd met een kiezer/keuzelijst of een verborgen veld)
   * `definitions/data/resolver` en `definitions/data/resolverConfig` (maar niet `definitions/data/preprocessing` of `.../clientFilter`) - de oplosser en configuratie
   * `definitions/queryBuilder` - de configuratie van de querybuilder
   * `defaults/aggregate` - het standaardaggregaat

  Als er een nieuw geval van de generische kolom op het **Rapport van de Gebruiker** is, worden de eigenschappen die met de dialoog worden bepaald voortgeduurd onder:

  `/etc/reports/userreport/jcr:content/report/columns/genericcol/settings/generic`

## Rapportontwerp {#report-design}

Het ontwerp bepaalt welke kolomtypes voor het creëren van een rapport beschikbaar zijn. Het definieert ook het alineasysteem waaraan de kolommen worden toegevoegd.

Adobe raadt u aan voor elk rapport een apart ontwerp te maken. Dat garandeert volledige flexibiliteit. Zie [ het bepalen van Uw Nieuw Rapport ](#defining-your-new-report).

De standaardrapporteringscomponenten worden gehouden onder `/etc/designs/reports`.

De locatie voor uw rapporten kan afhankelijk zijn van de locatie van uw componenten:

* `/etc/designs/reports/<yourReport>` is geschikt als het rapport zich onder `/apps/cq/reporting` bevindt

* `/etc/designs/<yourProject>/reports/<*yourReport*>` voor rapporten met het patroon `/apps/<yourProject>/reports`

De vereiste ontwerpeigenschappen worden geregistreerd op `jcr:content/reportpage/report/columns` (bijvoorbeeld `/etc/designs/reports/<reportName>/jcr:content/reportpage/report/columns` ):

* `components`

  Om het even welke componenten en/of componentengroepen die op het rapport worden toegestaan.

* `sling:resourceType`

  Eigenschap met waarde `cq/reporting/components/repparsys` .

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

Elk rapporttype moet een malplaatje verstrekken. Dit zijn standaard [ CQ Malplaatjes ](/help/sites-developing/templates.md) en kunnen als dusdanig worden gevormd.

De sjabloon moet:

* Stel de `sling:resourceType` in op `cq/reporting/components/reportpage`

* het te gebruiken ontwerp aangeven
* een onderliggende node van `report` maken die naar de container ( `reportbase` )-component met de eigenschap `sling:resourceType` verwijst

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

De standaardrapportagesjablonen worden onder `/libs/cq/reporting/templates` bewaard.

Adobe raadt echter aan deze knooppunten niet bij te werken. Maak in plaats daarvan uw eigen componentknooppunten onder `/apps/cq/reporting/templates` of, indien beter, onder `/apps/<yourProject>/reports/templates` .

Waar, als voorbeeld (zie ook [ Plaats van de Componenten van het Rapport ](#location-of-report-components)):

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

Om deze stappen te illustreren, bepaalt het volgende voorbeeld een rapport dat van alle configuraties OSGi binnen de bewaarplaats een lijst maakt. Dat wil zeggen, alle instanties van het knooppunt `sling:OsgiConfig` .

>[!NOTE]
>
>Het kopiëren van een bestaand rapport, dan het aanpassen van de nieuwe versie, is een alternatieve methode.

1. Creeer de wortelknoop voor uw nieuw rapport.

   Bijvoorbeeld onder `/apps/cq/reporting/components/osgireport` .

   ```xml
   N:cq [nt:folder]
       N:reporting [sling:Folder]
           N:components [sling:Folder]
               N:osgireport [sling:Folder]
   ```

1. Bepaal uw rapportbasis. Bijvoorbeeld `osgireport[cq:Component]` onder `/apps/cq/reporting/components/osgireport` .

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
   * geeft zowel `pie` - als `lineseries` -diagrammen weer
   * verstrekt een dialoog voor de gebruiker om het rapport te vormen

1. Definieer de eerste kolomcomponent (columnBase). Bijvoorbeeld `bundlecol[cq:Component]` onder `/apps/cq/reporting/components/osgireport` .

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

   * zoekt naar en retourneert de waarde die het van de server ontvangt; in dit geval de eigenschap `jcr:path` voor elke `sling:OsgiConfig` -node
   * bevat het `count` aggregaat
   * is niet gegroepeerd
   * heeft de titel `Bundle` (kolomtitel binnen de tabel)
   * bevindt zich in de sidekick-groep `OSGi Report`
   * Vernieuwingen bij opgegeven gebeurtenissen

   >[!NOTE]
   >
   >In dit voorbeeld zijn er geen definities van `N:data` en `P:clientFilter` . De reden hiervoor is dat de waarde die van de server wordt ontvangen, op een 1:1-basis wordt geretourneerd. Dit is het standaardgedrag.
   >
   >Dit is hetzelfde als de definities:
   >
   >```
   >N:data [nt:unstructured]
   >   P:clientFilter [String] = "function(v) { return v; }"
   >```
   >
   >Waar de functie gewoon de waarde retourneert die deze ontvangt.

1. Bepaal uw rapportontwerp. Bijvoorbeeld `osgireport[cq:Page]` onder `/etc/designs/reports` .

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

   Bijvoorbeeld onder `/apps/cq/reporting/templates/osgireport` .

   ```xml
   N:cq [nt:folder]
       N:reporting [sling:Folder]
           N:templates [sling:Folder]
               N:osgireport [cq:Template]
   ```

1. Bepaal uw rapportmalplaatje. Bijvoorbeeld `osgireport[cq:Template]` onder `/apps/cq/reporting/templates` .

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

   * definieert de `allowedPaths` voor de resulterende rapporten - in het bovenstaande geval ergens onder `/etc/reports`
   * biedt titels en beschrijvingen voor de sjabloon
   * verstrekt een duimnagelbeeld voor gebruik in de malplaatjelijst (de volledige definitie van dit knooppunt is hierboven niet vermeld - het is het gemakkelijkst om een geval van thumbnail.png van een bestaand rapport te kopiëren).

### Het creëren van een Instantie van Uw Nieuw Rapport {#creating-an-instance-of-your-new-report}

Een geval van uw nieuw rapport kan nu worden gecreeerd:

1. Open de **console van Hulpmiddelen**.

1. Selecteer **Rapporten** in de linkerruit.
1. Dan **Nieuw...** van de toolbar. Bepaal a **Titel** en **Naam**, selecteer uw nieuw rapporttype (het **Sjabloon van het Rapport OSGi**) van de lijst van malplaatjes, dan klik **creeert**.
1. Uw nieuwe rapportexemplaar verschijnt in de lijst. Dubbelklik op deze optie om deze te openen.
1. Sleep een component (voor dit voorbeeld, **Bundel** in de **OSGi Groep van het Rapport**) van sidekick om de eerste kolom tot stand te brengen en [ begin de rapportdefinitie ](/help/sites-administering/reporting.md#the-basics-of-report-customization).

   >[!NOTE]
   >
   >Aangezien dit voorbeeld geen groeperbare kolommen heeft, zijn de grafieken niet beschikbaar. Als u grafieken wilt zien, stelt u `groupable` in op `true` :
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

U kunt deze weergeven via het menu Configuratie van de webconsole (bijvoorbeeld beschikbaar in `http://localhost:4502/system/console/configMgr` ). Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

### Basisservice (CQ-rapportconfiguratie op de dag) {#basic-service-day-cq-reporting-configuration}

* **Tijdzone** bepaalt de historische gegevens van de tijdzone waarvoor wordt gecreeerd. Dit moet ervoor zorgen dat de historische grafiek de zelfde gegevens voor elke gebruiker over de wereld toont.
* **bepaalt de Plaats van 0} {de scène die met** Tijdzone **voor historische gegevens moet worden gebruikt.** De landinstelling wordt gebruikt om bepaalde landspecifieke kalenderinstellingen te bepalen (bijvoorbeeld of de eerste dag van een week zondag of maandag is).

* **de weg van de Momentopname** bepaalt de wortelweg waar de momentopnamen voor historische grafieken worden opgeslagen.
* **Weg aan rapporten** bepaalt de weg waar de rapporten worden gevestigd. Dit wordt gebruikt door de momentopnameservice om de rapporten te bepalen om momentopnamen voor eigenlijk te nemen.
* **Dagelijkse momentopnamen** bepaalt het uur van elke dag wanneer de dagelijkse momentopnamen worden genomen. Het gespecificeerde uur is in lokale timezone van de server.
* **Uur momentopnamen** bepaalt de minuut van elk uur wanneer de uurmomentopnamen worden genomen.
* **Rijen (maximum)** bepaalt het maximumaantal rijen die voor elke momentopname worden opgeslagen. Deze waarde moet redelijkerwijs worden gekozen. Als het te hoog is, beïnvloedt dit de grootte van de gegevensopslagplaats, als te laag, kunnen de gegevens niet correct zijn wegens de manier waarop historische gegevens worden behandeld.
* **gegevens van de Vervaging**, als toegelaten, kunnen de valse historische gegevens worden gecreeerd door de `fakedata` selecteur te gebruiken; als gehandicapt, dan het gebruik van de `fakedata` selecteur een uitzondering werpt.

  Omdat het gegeven vals is, moet het *slechts* voor het testen en het zuiveren doeleinden worden gebruikt.

  Als u de kiezer van `fakedata` gebruikt, wordt het rapport impliciet voltooid, zodat alle bestaande gegevens verloren gaan. Gegevens kunnen handmatig worden hersteld, maar dit kan een tijdrovend proces zijn.

* **gebruiker van de Momentopname** bepaalt een facultatieve gebruiker die voor het nemen van momentopnamen kan worden gebruikt.

  In feite worden momentopnamen gemaakt voor de gebruiker die het rapport heeft voltooid. Er kunnen situaties zijn (bijvoorbeeld op een publicatiesysteem, waar deze gebruiker niet bestaat omdat zijn account niet is gerepliceerd) waarin u een fallback-gebruiker wilt opgeven die in plaats daarvan wordt gebruikt.

  Ook, zou het specificeren van een gebruiker een veiligheidsrisico kunnen opleggen.

* **afdwingen momentopname gebruiker**, als toegelaten, worden alle momentopnamen genomen met de gebruiker die onder *wordt gespecificeerd de gebruiker van de Momentopname*. Dit kan ernstige gevolgen voor de beveiliging hebben als het niet correct wordt afgehandeld.

### Cacheinstellingen (CQ-rapportagecache dag) {#cache-settings-day-cq-reporting-cache}

* **laat** toe laat u het in het voorgeheugen onderbrengen van rapportgegevens toe of onbruikbaar maken. Het toelaten van het rapportgeheime voorgeheugen houdt rapportgegevens in geheugen tijdens verscheidene verzoeken. Dit kan de prestaties verhogen, maar leidt tot een hoger geheugengebruik en kan in extreme omstandigheden leiden tot situaties waarin onvoldoende geheugen beschikbaar is.
* **TTL** bepaalt de tijd (in seconden) waarvoor het rapportgegeven in de cache wordt geplaatst. Een hoger getal verhoogt de prestaties, maar retourneert mogelijk ook onjuiste gegevens als de gegevens binnen de tijdsperiode veranderen.
* **Max ingangen** bepaalt het maximumaantal rapporten dat in het voorgeheugen onder moet worden gebracht op om het even welk ogenblik.

>[!NOTE]
>
>De rapportgegevens kunnen voor elke gebruiker en taal verschillend zijn. Daarom worden de rapportgegevens in het voorgeheugen ondergebracht per rapport, gebruiker, en taal. Dit betekent dat a **Max ingangen** waarde van `2` eigenlijk gegevens voor één van beiden in de cache plaatst:
>
>* één rapport voor twee gebruikers met verschillende taalmontages
>* één gebruiker en twee rapporten
>
