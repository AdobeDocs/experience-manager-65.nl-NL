---
title: SPA-blauwdruk
seo-title: SPA-blauwdruk
description: Dit document beschrijft het algemene, kader-onafhankelijke contract dat om het even welk kader van het KUUROORD zou moeten vervullen om editable componenten van het KUUROORD binnen AEM uit te voeren.
seo-description: Dit document beschrijft het algemene, kader-onafhankelijke contract dat om het even welk kader van het KUUROORD zou moeten vervullen om editable componenten van het KUUROORD binnen AEM uit te voeren.
uuid: 48f2d415-ec34-49dc-a8e1-6feb5a8a5bbe
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 04ac8203-320b-4671-aaad-6e1397b12b6f
docset: aem65
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '2112'
ht-degree: 0%

---


# SPA-blauwdruk{#spa-blueprint}

Om de auteur toe te laten om de AEM Redacteur van het KUUROORD te gebruiken om de inhoud van een KUUROORD uit te geven, zijn er vereisten die het KUUROORD moet vervullen, die in dit document worden beschreven.

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

## Inleiding {#introduction}

Dit document beschrijft het algemene contract dat om het even welk kader van het KUUROORD (d.w.z. het soort AEM steunlaag) zou moeten vervullen om editable componenten van het KUUROORD binnen AEM uit te voeren.

>[!NOTE]
>
>De volgende vereisten zijn frameonafhankelijk. Als aan deze vereisten wordt voldaan, kan een kader-specifieke laag worden verstrekt die uit modules, componenten, en de diensten wordt samengesteld.
>
>**Aan deze vereisten wordt reeds voldaan voor de React en Hoekige kaders in AEM.** De vereisten in deze blauwdruk zijn alleen relevant als u een ander kader voor gebruik met AEM wilt implementeren.

>[!CAUTION]
>
>Hoewel de mogelijkheden van het KUUROORD van AEM kader-onafhankelijk zijn, momenteel slechts worden het React en Hoekkader gesteund.

Om de auteur toe te laten om de AEM Redacteur van de Pagina te gebruiken om de gegevens uit te geven die door een Enige Kader van de Toepassing van de Pagina worden blootgesteld, moet een project de structuur van het model kunnen interpreteren die de semantische waarde van de gegevens vertegenwoordigt die voor een toepassing binnen de AEM bewaarplaats worden opgeslagen. Om dit doel te bereiken, worden twee raamwerk-agnostische bibliotheken verstrekt: de `PageModelManager` en de `ComponentMapping`.

### PageModelManager {#pagemodelmanager}

De `PageModelManager` bibliotheek wordt verstrekt als pakket NPM dat door een project van het KUUROORD moet worden gebruikt. Het begeleidt SPA en dient als manager van het gegevensmodel.

Namens het KUUROORD, onttrekt het de herwinning en het beheer van de structuur JSON die de daadwerkelijke inhoudsstructuur vertegenwoordigt. Het is ook verantwoordelijk voor het synchroniseren met het KUUROORD om het te laten weten wanneer het zijn componenten moet opnieuw teruggeven.

Zie het NPM-pakket [@adobe/aem-spa-page-model-manager](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager)

Wanneer het initialiseren van de `PageModelManager`app, laadt de bibliotheek eerst het verstrekte wortelmodel van de app (via parameter, meta-eigenschap, of huidige URL). Als in de bibliotheek wordt aangegeven dat het model van de huidige pagina geen deel uitmaakt van het hoofdmodel, wordt het opgehaald en opgenomen als het model van een onderliggende pagina.

![page_model_consolidatie](assets/page_model_consolidation.png)

### ComponentMapping {#componentmapping}

De `ComponentMapping` module wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor het KUUROORD om front-end componenten aan AEM middeltypes in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elke punten in het model bevatten een `:type` gebied dat een AEM middeltype blootstelt. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

#### Dynamisch model naar componenttoewijzing {#dynamic-model-to-component-mapping}

Voor details over hoe het dynamische model aan componentenafbeelding in het KUUROORD Javascript SDK voor AEM voorkomt zie het artikel [Dynamisch Model aan de Afbeelding van de Component voor SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

### Framework-specifieke laag {#framework-specific-layer}

Voor elk front-end framework moet een derde laag worden geïmplementeerd. Deze derde bibliotheek is verantwoordelijk voor de interactie met de onderliggende bibliotheken en biedt een reeks goed geïntegreerde en gebruiksvriendelijke ingangspunten voor de interactie met het gegevensmodel.

In de rest van dit document worden de vereisten van deze specifieke laag van het intermediaire kader beschreven en wordt ernaar gestreefd onafhankelijk van het framework te zijn. Door de volgende vereisten na te leven, kan een kader-specifieke laag voor de projectcomponenten worden verstrekt om met de onderliggende bibliotheken in wisselwerking te staan die het gegevensmodel leiden.

## Algemene concepten {#general-concepts}

### Paginamodel {#page-model}

De inhoudsstructuur van de pagina wordt opgeslagen in AEM. Het model van de pagina wordt gebruikt om de componenten van het KUUROORD in kaart te brengen en te concretiseren. De ontwikkelaars van het KUUROORD creëren componenten SPA die zij aan AEM componenten in kaart brengen. Om dit te doen, gebruiken zij het middeltype (of weg aan de AEM component) als unieke sleutel.

De componenten van het KUUROORD moeten synchroon met het paginamodel zijn en met om het even welke veranderingen in zijn inhoud dienovereenkomstig worden bijgewerkt. Een patroon dat gebruikmaakt van dynamische componenten, moet worden gebruikt om direct componenten te instantiëren volgens de opgegeven structuur van het paginamodel.

### Meta-velden {#meta-fields}

Het paginamodel maakt gebruik van de JSON Model Exporter, die zelf is gebaseerd op de [Sling Model](https://sling.apache.org/documentation/bundles/models.html) API. De exporteerbare slingmodellen stellen de volgende lijst van gebieden bloot om de onderliggende bibliotheken toe te laten het gegevensmodel interpreteren:

* `:type`: Type van de AEM (gebrek = middeltype)
* `:children`: Hierarchische onderliggende elementen van de huidige bron. Onderliggende items maken geen deel uit van de binneninhoud van de huidige bron (vindt u bij items die een pagina vertegenwoordigen)
* `:hierarchyType`: Het hiërarchische type van een bron. Het paginatype `PageModelManager` wordt momenteel ondersteund

* `:items`: Bronnen voor onderliggende inhoud van de huidige bron (geneste structuur, alleen aanwezig op containers)
* `:itemsOrder`: Ordered list of the children. Het JSON-toewijzingsobject garandeert de volgorde van de velden niet. Door zowel de kaart als de huidige array te hebben, heeft de consument van de API de voordelen van beide structuren
* `:path`: Inhoudspad van een item (aanwezig op items die een pagina vertegenwoordigen)

Zie ook [Aan de slag met AEM Content Services.](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html)

### Framework-Specific Module {#framework-specific-module}

Het scheiden van zorgen helpt de uitvoering van het project te vergemakkelijken. Daarom moet een npm-specifiek pakket worden verstrekt. Dit pakket is verantwoordelijk voor het samenvoegen en blootstellen van de basismodules, de diensten, en de componenten. Deze componenten moeten de logica van het gegevensmodelbeheer inkapselen en toegang tot de gegevens verlenen de component van het project verwacht. De module is ook verantwoordelijk voor het tijdelijk blootstellen van nuttige ingangspunten van de onderliggende bibliotheken.

Om de interoperabiliteit van de bibliotheken te bevorderen, adviseert Adobe de kader-specifieke module om de volgende bibliotheken te bundelen. Indien nodig, kan de laag onderliggende APIs inkapselen en aanpassen alvorens hen aan het project bloot te stellen.

* [@adobe/aem-spa-page-model-manager](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager)
* [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

#### Implementaties {#implementations}

#### Reageren {#react}

npm-module: [@adobe/aem-response-editable-components](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### Hoekig {#angular}

npm-module: binnenkort beschikbaar

## Belangrijkste services en componenten {#main-services-and-components}

De volgende entiteiten moeten worden uitgevoerd overeenkomstig de specifieke richtsnoeren voor elk kader. Op basis van de kaderarchitectuur kan de implementatie sterk variëren, maar de beschreven functies moeten worden verstrekt.

### De modelprovider {#the-model-provider}

De componenten van het project moeten toegang tot de fragmenten van een model aan een ModelLeverancier delegeren. De ModelLeverancier is dan verantwoordelijk voor het luisteren naar veranderingen die aan het gespecificeerde fragment van het model worden aangebracht en keert het bijgewerkte model aan de het delegeren component terug.

Hiervoor moet de modelprovider zich registreren bij de ` [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager)`. Dan wanneer een verandering voorkomt ontvangt het en gaat de bijgewerkte gegevens tot de het delegeren component over. Door overeenkomst, wordt het bezit ter beschikking gesteld aan de het delegeren component die het fragment van model zal dragen genoemd `cqModel`. De implementatie is vrij om deze eigenschap aan de component te leveren, maar moet aspecten zoals de integratie met raamarchitectuur, ontdekkbaarheid en gebruiksgemak in overweging nemen.

### De HTML-decorator van de component {#the-component-html-decorator}

De componentdecorator is verantwoordelijk voor het versieren van de buitenste HTML van het element van elke componentinstanties met een reeks gegevenskenmerken en klassennamen die door de Pagina-editor worden verwacht.

#### Componentdeclaratie {#component-declaration}

De volgende meta-gegevens moeten aan het buitenelement van HTML worden toegevoegd dat door de component van het project wordt geproduceerd. Hiermee kan de Pagina-editor de corresponderende bewerkingsconfiguratie ophalen.

* `data-cq-data-path`: Pad naar de bron ten opzichte van de `jcr:content`

#### Bewerkbaarheidsverklaring en plaatsaanduiding {#editing-capability-declaration-and-placeholder}

De volgende meta- gegevens en klassennamen moeten aan het buitenelement van HTML worden toegevoegd dat door de component van het project wordt geproduceerd. Hiermee kan de Pagina-editor gerelateerde functies bieden.

* `cq-placeholder`: Klassenaam die de tijdelijke aanduiding voor een leeg onderdeel aanduidt
* `data-emptytext`: Label dat door de overlay moet worden weergegeven wanneer een componentinstantie leeg is

**Plaatsaanduiding voor lege componenten**

Elke component moet worden uitgebreid met een functionaliteit waarmee het buitenste HTML-element wordt versierd met gegevenskenmerken en klassennamen die specifiek zijn voor plaatsaanduidingen en verwante overlays wanneer de component wordt geïdentificeerd als leeg.

**Informatie over de lege ruimte van een component**

* Is de component logisch leeg?
* Wat moet het label zijn dat door de overlay wordt weergegeven wanneer de component leeg is?

### Container {#container}

Een container is een component die onderliggende componenten bevat en rendert. Om dit te doen, herhaalt de container over `:itemsOrder`, `:items` en `:children` eigenschappen van zijn model.

De container haalt dynamisch de onderliggende componenten op uit de opslagruimte van de ` [ComponentMapping](/help/sites-developing/spa-blueprint.md#componentmapping)` bibliotheek. De container breidt vervolgens de onderliggende component uit met de mogelijkheden van de ModelProvider en instantieert deze ten slotte.

### Pagina {#page}

De `Page` component breidt de `Container` component uit. Een container is een component die is bedoeld om onderliggende componenten, waaronder onderliggende pagina&#39;s, te bevatten en te renderen. Om dit te doen, herhaalt de container over `:itemsOrder`, `:items`, en `:children` eigenschappen van zijn model. De `Page` component krijgt dynamisch de kindcomponenten van de opslag van de [bibliotheek ComponentMapping](/help/sites-developing/spa-blueprint.md#componentmapping) . De instantie `Page` is verantwoordelijk voor het instantiëren van onderliggende componenten.

### Responsief raster {#responsive-grid}

De component Responsief raster is een container. Het bevat een specifieke variant van de ModelLeverancier die zijn kolommen vertegenwoordigt. Het responsieve Net en zijn kolommen zijn verantwoordelijk voor het versieren van het buitenste element van HTML van de component van het project met de specifieke klassennamen in het model.

De component Responsief raster moet vooraf worden toegewezen aan de AEM tegenhanger omdat deze component complex is en zelden wordt aangepast.

#### Specifieke modelvelden {#specific-model-fields}

* `gridClassNames:` Klassenamen opgegeven voor het responsieve raster
* `columnClassNames:` Klassenamen opgegeven voor de responsieve kolom

Zie ook de npm-bron [@adobe/aem-response-editable-components#srccomponentsresponsivegridjsx](https://www.npmjs.com/package/@adobe/aem-react-editable-components#srccomponentsresponsivegridjsx)

#### Plaatsaanduiding van het reponsieve raster {#placeholder-of-the-reponsive-grid}

De component van het KUUROORD wordt in kaart gebracht aan een grafische container zoals het Responsieve Net en moet virtuele kindplaceholder toevoegen wanneer de inhoud wordt authored. Wanneer de inhoud van het KUUROORD door de Redacteur van de Pagina wordt ontworpen, wordt die inhoud ingebed in de redacteur gebruikend iframe en het `data-cq-editor` attribuut wordt toegevoegd aan de documentknoop van die inhoud. Wanneer het `data-cq-editor` kenmerk aanwezig is, moet de container een HTMLElement bevatten om het gebied te vertegenwoordigen waarmee de auteur communiceert bij het invoegen van een nieuwe component in de pagina.

Bijvoorbeeld:

```
<div data-cq-data-path={"path/to/the/responsivegrid/*"} className="new section aem-Grid-newComponent"/>
```

>[!NOTE]
>
>De klassenamen die in het voorbeeld worden gebruikt, worden momenteel vereist door de pagina-editor.
>
>* `"new section"`: Geeft aan dat het huidige element de tijdelijke aanduiding van de container is
>* `"aem-Grid-newComponent"`: Hiermee wordt de component genormaliseerd voor het ontwerpen van de lay-out

>



#### Componenttoewijzing {#component-mapping}

De onderliggende [`Component Mapping`](/help/sites-developing/spa-blueprint.md#componentmapping) bibliotheek en zijn `MapTo` functie kunnen worden ingekapseld en worden uitgebreid om de functionaliteiten met betrekking tot te verstrekken uitgeeft configuratie die naast de huidige componentenklasse wordt verstrekt.

```
const EditConfig = {

    emptyLabel: 'My Component',

    isEmpty: function() {
        return !this.props || !this.props.cqModel || this.props.cqModel.isEmpty;
    }
};

class MyComponent extends Component {

    render() {
        return <div className={'my-component'}></div>;
    }
}

MapTo('component/resource/path')(MyComponent, EditConfig);
```

In de bovengenoemde implementatie, wordt de projectcomponent uitgebreid met de leegheidsfunctionaliteit alvorens wordt geregistreerd in de opslag van de Afbeelding van de [Component](/help/sites-developing/spa-blueprint.md#componentmapping) . Dit wordt gedaan door de [`ComponentMapping`](/help/sites-developing/spa-blueprint.md#componentmapping) bibliotheek in te kapselen en uit te breiden om de steun van het `EditConfig` configuratievoorwerp te introduceren:

```
/**
 * Configuration object in charge of providing the necessary data expected by the page editor to initiate the authoring. The provided data will be decorating the associated component
 *
 * @typedef {{}} EditConfig
 * @property {String} [dragDropName]       If defined, adds a specific class name enabling the drag and drop functionality
 * @property {String} emptyLabel           Label to be displayed by the placeholder when the component is empty. Optionally returns an empty text value
 * @property {function} isEmpty            Should the component be considered empty. The function is called using the context of the wrapper component giving you access to the component model
 */

/**
 * Map a React component with the given resource types. If an {@link EditConfig} is provided the <i>clazz</i> is wrapped to provide edition capabilities on the AEM Page Editor
 *
 * @param {string[]} resourceTypes                      - List of resource types for which to use the given <i>clazz</i>
 * @param {class} clazz                                 - Class to be instantiated for the given resource types
 * @param {EditConfig} [editConfig]                     - Configuration object for enabling the edition capabilities
 * @returns {class}                                     - The resulting decorated Class
 */
ComponentMapping.map = function map (resourceTypes, clazz, editConfig) {};
```

## Slinken met de paginaeditor {#contract-with-the-page-editor}

De projectcomponenten moeten minstens de volgende gegevensattributen produceren om de redacteur toe te staan om met hen in wisselwerking te staan.

* `data-cq-data-path`: Relatief pad van de component zoals opgegeven door de `PageModel` (bv. `"root/responsivegrid/image"`). Dit kenmerk mag niet aan pagina&#39;s worden toegevoegd.

Samengevat, om door de paginaredacteur als editable te worden geïnterpreteerd, moet een projectcomponent het volgende contract in acht nemen:

* Verstrek de verwachte attributen om een front eindcomponenteninstantie aan een AEM middel te associëren.
* Verstrek de verwachte reeks attributen en klassennamen die de verwezenlijking van lege placeholders toelaat.
* Geef de verwachte klassenamen op, zodat u elementen kunt slepen en neerzetten.

### Typische HTML-elementstructuur {#typical-html-element-structure}

Het volgende fragment illustreert de typische HTML-representatie van een pagina-inhoudstructuur. Hier volgen enkele belangrijke punten:

* Het responsieve rasterelement bevat vooraf ingestelde klassenamen `aem-Grid--`
* Het responsieve kolomelement bevat vooraf ingestelde klassenamen `aem-GridColumn--`
* Een responsief raster dat ook de kolom van een bovenliggend raster is, wordt omlopen, zoals de twee vorige voorvoegsels, worden niet op hetzelfde element weergegeven
* Elementen die overeenkomen met bewerkbare bronnen hebben een `data-cq-data-path` eigenschap. Zie het [Contract met de sectie van de Redacteur](#contract-wtih-the-page-editor) van de Pagina van dit document.

```
<div data-cq-data-path="/content/page">
    <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
        <div class="aem-container aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/content/page/jcr:content/root/responsivegrid">
            <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
                <div class="cmp-image cq-dd-image aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/root/responsivegrid/image">
                    <img src="/content/we-retail-spa-sample/react/jcr%3acontent/root/responsivegrid/image.img.jpeg/1512113734019.jpeg">
                </div>
            </div>
        </div>
    </div>
</div>
```

## Navigatie en routering {#navigation-and-routing}

App bezit het verpletteren. De front-end ontwikkelaar moet eerst een component van de Navigatie (in kaart gebracht aan een AEM navigatiecomponent) uitvoeren. Deze component zou URL-koppelingen renderen die moeten worden gebruikt in combinatie met een reeks routes die fragmenten van inhoud weergeven of verbergen.

De onderliggende [ bibliotheek en zijn `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) ` [ModelRouter](/help/sites-developing/spa-routing.md)` module (die door gebrek wordt toegelaten) zijn de oorzaak van het pre-halen en het verlenen van toegang tot het model verbonden aan een bepaald middelweg.

De twee entiteiten hebben betrekking op het begrip van het verpletteren maar het ` [ModelRouter](/help/sites-developing/spa-routing.md)` is slechts verantwoordelijk voor het hebben van het ` [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager)` geladen met een gegevensmodel dat synchroon met de huidige toepassingsstaat wordt gestructureerd.

Zie het artikelSPA Model dat voor meer informatie verplettert [](/help/sites-developing/spa-routing.md) .

## SPA in actie {#spa-in-action}

Zie hoe een eenvoudig KUUROORD werkt en met een KUUROORD zelf experimenteert door aan het document [die met KUUROORDs in AEM](/help/sites-developing/spa-getting-started-react.md)worden begonnen verder te gaan.

## Meer informatie {#further-reading}

Voor meer informatie over SPAs in AEM, zie de volgende documenten:

* [Het Authoring Overzicht](/help/sites-developing/spa-overview.md) van SPA voor een overzicht van SPAs in AEM en het communicatie model
* [Begonnen het worden met SPAs in AEM](/help/sites-developing/spa-getting-started-react.md) voor een gids aan een eenvoudige SPA en hoe het werkt
