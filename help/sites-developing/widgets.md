---
title: Widgets gebruiken en uitbreiden (klassieke UI)
seo-title: Using and Extending Widgets (Classic UI)
description: AEM webinterface gebruikt AJAX en andere moderne browsertechnologieën om WYSIWYG-bewerking en -opmaak van inhoud door auteurs rechtstreeks op de webpagina mogelijk te maken
seo-description: AEM's web-based interface uses AJAX and other modern browser technologies to enable WYSIWYG editing and formatting of content by authors right on the web page
uuid: eb3da415-cbef-4766-a28e-837e238a4156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 7b234f1f-4470-4de1-a3c3-ab19e5e001ad
docset: aem65
exl-id: 56a9591c-cd78-42e8-a5d7-6b48581d6af6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '4934'
ht-degree: 0%

---

# Widgets gebruiken en uitbreiden (klassieke UI){#using-and-extending-widgets-classic-ui}

>[!NOTE]
>
>Deze pagina beschrijft het gebruik van widgets in de klassieke gebruikersinterface, die in AEM 6.4 is afgekeurd.
>
>Adobe raadt u aan de moderne [interface met aanraakbediening](/help/sites-developing/touch-ui-concepts.md) gebaseerd op [Koraalinterface](/help/sites-developing/touch-ui-concepts.md#coral-ui) en [Graniet-interface](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

Adobe Experience Manager-webinterface gebruikt AJAX en andere moderne browsertechnologieën om WYSIWYG-bewerking en -opmaak van inhoud door auteurs rechtstreeks op de webpagina mogelijk te maken.

Adobe Experience Manager (AEM) gebruikt de [ExtJS](https://www.sencha.com/) Widget-bibliotheek, die de zeer gepolijste elementen van de gebruikersinterface biedt die in alle belangrijkste browsers werken en het maken van gebruikersinterface van desktopniveau mogelijk maken.

Deze widgets zijn opgenomen in AEM en kunnen, naast het gebruik door AEM zelf, worden gebruikt door elke website die met AEM is gemaakt.

Voor een volledige verwijzing naar alle beschikbare widgets in AEM kunt u verwijzen naar de [API-documentatie voor widget](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html) of aan de [lijst van bestaande xtypes](/help/sites-developing/xtypes.md). Daarnaast zijn er veel voorbeelden beschikbaar van het gebruik van het ExtJS-framework op de [Sencha](https://www.sencha.com/products/extjs/examples/) , de eigenaar van het raamwerk.

Deze pagina biedt inzicht in het gebruik en uitbreiden van widgets. Hierin wordt eerst beschreven hoe u [clientcode op een pagina opnemen](#including-the-client-sided-code-in-a-page). Vervolgens worden enkele voorbeeldcomponenten beschreven die zijn gemaakt om een aantal basistoepassingen en -extensies te illustreren. Deze componenten zijn beschikbaar in de **ExtJS-widgets gebruiken** pakket op **Pakket delen**.

Het pakket bevat voorbeelden van:

* [Standaarddialoogvensters](#basic-dialogs) gemaakt met kant-en-klare widgets.
* [Dynamische dialoogvensters](#dynamic-dialogs) gemaakt met kant-en-klare widgets en aangepaste javascript-logica.
* Dialoogvensters gebaseerd op [aangepaste widgets](#custom-widgets).
* A [deelvenster met boomstructuur](#tree-overview) een JCR-structuur onder een bepaald pad weergeven.
* A [rasterdeelvenster](#grid-overview) gegevens weergeven in tabelvorm.

>[!NOTE]
>
>De klassieke gebruikersinterface van Adobe Experience Manager is gebaseerd op [ExtJS 3.4.0](https://extjs.cachefly.net/ext-3.4.0/docs/).

## De code aan de clientzijde opnemen in een pagina {#including-the-client-sided-code-in-a-page}

JavaScript- en stijlbladcode aan clientzijde moet in een clientbibliotheek worden geplaatst.

Een clientbibliotheek maken:

1. Hieronder een knooppunt maken `/apps/<project>` met de volgende eigenschappen:

   * name=&quot;clientlib&quot;
   * jcr:mixinTypes=&quot;[mix:vergrendelbaar]&quot;
   * jcr:primaryType=&quot;cq:ClientLibraryFolder&quot;
   * sling:resourceType=&quot;widgets/clientlib&quot;
   * categorieën=&quot;[&lt;category-name>]&quot;
   * afhankelijkheden=&quot;[cq.widgets]&quot;

   `Note: <category-name> is the name of the custom library (e.g. "cq.extjstraining") and is used to include the library on the page.`

1. Onder `clientlib` de `css` en `js` mappen (nt:folder).

1. Onder `clientlib` de `css.txt` en `js.txt` bestanden (nt:bestanden). Deze .txt-bestanden bevatten de bestanden die in de bibliotheek zijn opgenomen.

1. Bewerken `js.txt`: moet beginnen met &#39; `#base=js`&quot;, gevolgd door de lijst van bestanden die door de CQ-clientbibliotheekservice worden samengevoegd, bijvoorbeeld:

   ```
   #base=js
    components.js
    exercises.js
    CustomWidget.js
    CustomBrowseField.js
    InsertTextPlugin.js
   ```

1. Bewerken `css.txt`: moet beginnen met &#39; `#base=css`&quot;, gevolgd door de lijst van bestanden die door de CQ-clientbibliotheekservice worden samengevoegd, bijvoorbeeld:

   ```
   #base=css
    components.css
   ```

1. Onder de `js` , plaatst u de javascript-bestanden die bij de bibliotheek horen.

1. Onder de `css` map, plaats de `.css` bestanden en de bronnen die door de CSS-bestanden worden gebruikt (bv. `my_icon.png`).

>[!NOTE]
>
>Het hanteren van de hierboven beschreven opmaakmodellen is optioneel.

De clientbibliotheek opnemen in de jsp voor de paginacomponent:

* om zowel javascript-code als stijlpagina&#39;s op te nemen:
   `<ui:includeClientLib categories="<category-name1>, <category-name2>, ..."/>`
waarbij 
`<category-nameX>` is de naam van de bibliotheek aan de clientzijde.

* alleen javascript-code opnemen:
   `<ui:includeClientLib js="<category-name>"/>`

Zie voor meer informatie de beschrijving van de [&lt;ui:includeclientlib>](/help/sites-developing/taglib.md#lt-ui-includeclientlib) tag.

In sommige gevallen mag een clientbibliotheek alleen beschikbaar zijn in de modus Schrijver en moet deze worden uitgesloten in de publicatiemodus. Dit kan als volgt worden bereikt:

```xml
    if (WCMMode.fromRequest(request) != WCMMode.DISABLED) {
        %><ui:includeClientLib categories="cq.collab.blog"/><%
    }
```

### Aan de slag met de voorbeelden {#getting-started-with-the-samples}

Installeer het pakket met de naam **ExtJS-widgets gebruiken** in een lokale AEM en maak een voorbeeldpagina waarin de componenten worden opgenomen. Daartoe:

1. Download het pakket met de naam **ExtJS-widgets gebruiken (v01)** van Package Share en installeer het pakket. Het leidt tot het project `extjstraining` onder `/apps` in de repository.
1. Neem de clientbibliotheek met de scripts (js) en het stijlblad (css) op in de koptag van de geometrixx page jsp, aangezien u de voorbeeldcomponenten opneemt op een nieuwe pagina van de pagina **Geometrixx** vertakking: in **CRXDE Lite** het bestand openen `/apps/geometrixx/components/page/headlibs.jsp` en voeg de `cq.extjstraining` categorie `<ui:includeClientLib>` label als volgt:
   `%><ui:includeClientLib categories="apps.geometrixx-main, cq.extjstraining"/><%`
1. Een nieuwe pagina maken in het dialoogvenster **Geometrixx** vertakking onder `/content/geometrixx/en/products` en noem het **ExtJS-widgets gebruiken**.
1. Ga in ontwerpwijze en voeg alle componenten van de geroepen groep toe **ExtJS-widgets gebruiken** aan het ontwerp van Geometrixx
1. Ga terug in bewerkingsmodus: de onderdelen van de groep **ExtJS-widgets gebruiken** zijn beschikbaar in de Sidetrap.

>[!NOTE]
>
>De voorbeelden op deze pagina zijn gebaseerd op de inhoud van het Geometrixx-voorbeeld, die niet meer wordt verzonden met AEM, en die is vervangen door We.Retail. Zie het document [We.Retail Reference Implementation](/help/sites-developing/we-retail.md#we-retail-geometrixx) voor het downloaden en installeren van Geometrixx.

### Standaarddialoogvensters {#basic-dialogs}

Dialoogvensters worden doorgaans gebruikt om inhoud te bewerken, maar kunnen ook alleen informatie weergeven. Een gemakkelijke manier om een volledig dialoogvenster weer te geven, is om toegang te krijgen tot de representatie in json-indeling. U doet dit door de browser op te vragen:

`https://localhost:4502/<path-to-dialog>.-1.json`

De eerste component van de **ExtJS-widgets gebruiken** groep in de Sidetrap wordt **1. Grondbeginselen van dialoogvensters** en bevat vier basisdialoogvensters die zijn samengesteld met widgets die buiten de box vallen en zonder aangepaste javascript-logica. De dialoogvensters worden hieronder opgeslagen `/apps/extjstraining/components/dialogbasics`. De basisdialoogvensters zijn:

* het volledige dialoogvenster ( `full` knooppunt): er wordt een venster weergegeven met drie tabbladen, die elk twee tekstvelden hebben.
* Het dialoogvenster Eén deelvenster ( `singlepanel` knooppunt): er wordt een venster weergegeven met 1 tab die 2 tekstvelden heeft.
* Het dialoogvenster Meerdere deelvensters ( `multipanel` knooppunt): de weergave is hetzelfde als het dialoogvenster Volledig, maar het is anders opgebouwd.
* het dialoogvenster Ontwerpen( `design` knooppunt): er wordt een venster weergegeven met twee tabbladen. De eerste tab heeft een tekstveld, een vervolgkeuzemenu en een inklapbaar tekstgebied. Het tweede tabblad bevat een veldset met 4 tekstvelden en een inklapbaar veld met 2 tekstvelden.

Inclusief de **1. Grondbeginselen van dialoogvensters** component in de voorbeeldpagina:

1. Voeg de **1. Grondbeginselen van dialoogvensters** naar de voorbeeldpagina van de **ExtJS-widgets gebruiken** in de **Sidetrap**.
1. De component geeft een titel, tekst en een **EIGENSCHAPPEN** koppeling: Klik op de koppeling om de eigenschappen van de alinea weer te geven die in de repository zijn opgeslagen. Klik nogmaals op de koppeling om de eigenschappen te verbergen.

De component wordt als volgt weergegeven:

![chlimage_1-60](assets/chlimage_1-60.png)

#### Voorbeeld 1: Volledig dialoogvenster {#example-full-dialog}

De **Volledig** wordt een venster weergegeven met drie tabbladen, die elk twee tekstvelden hebben. Dit is het standaarddialoogvenster van het dialoogvenster **Grondbeginselen van dialoogvensters** component. De kenmerken zijn:

* Wordt gedefinieerd door een knooppunt: knooppunttype = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`.
* Geeft 3 tabbladen weer (knooppunttype = `cq:Panel`).
* Elke tab heeft twee tekstvelden (knooppunttype = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wordt gedefinieerd door het knooppunt:
   `/apps/extjstraining/components/dialogbasics/full`
* Wordt in JSON-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/full.-1.json`

Het dialoogvenster wordt als volgt weergegeven:

![screen_shot_2012-01-31at45411pm](assets/screen_shot_2012-01-31at45411pm.png)

#### Voorbeeld 2: Dialoogvenster Eén venster {#example-single-panel-dialog}

De **Eén deelvenster** wordt een venster weergegeven met één tabblad dat twee tekstvelden heeft. De kenmerken zijn:

* Geeft 1 tab weer (knooppunttype = `cq:Dialog`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`)
* De tab heeft twee tekstvelden (knooppunttype = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`)
* Wordt gedefinieerd door het knooppunt:
   `/apps/extjstraining/components/dialogbasics/singlepanel`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/singlepanel.-1.json`
* Eén voordeel ten opzichte van **Volledig dialoogvenster** is dat er minder configuratie nodig is.
* Aanbevolen gebruik: voor eenvoudige dialoogvensters die informatie weergeven of slechts een paar velden bevatten.

Het dialoogvenster Eén deelvenster gebruiken:

1. Het dialoogvenster van het dialoogvenster **Grondbeginselen van dialoogvensters** met de **Eén deelvenster** dialoogvenster:
   1. In **CRXDE Lite**, verwijdert u het knooppunt: `/apps/extjstraining/components/dialogbasics/dialog`
   1. Klikken **Alles opslaan** om de wijzigingen op te slaan.
   1. Kopieer het knooppunt: `/apps/extjstraining/components/dialogbasics/singlepanel`
   1. Plak het gekopieerde knooppunt hieronder: `/apps/extjstraining/components/dialogbasics`
   1. Selecteer het knooppunt: `/apps/extjstraining/components/dialogbasics/Copy of singlepanel`en hernoemen `dialog`.
1. Bewerk de component: het dialoogvenster wordt als volgt weergegeven:

![screen_shot_2012-01-31at45952pm](assets/screen_shot_2012-01-31at45952pm.png)

#### Voorbeeld 3: Dialoogvenster Meerdere deelvensters {#example-multi-panel-dialog}

De **Meerdere deelvensters** wordt dezelfde weergave weergegeven als het dialoogvenster **Volledig** , maar anders samengesteld. De kenmerken zijn:

* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`).
* Geeft 3 tabbladen weer (knooppunttype = `cq:Panel`).
* Elke tab heeft twee tekstvelden (knooppunttype = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wordt gedefinieerd door het knooppunt:
   `/apps/extjstraining/components/dialogbasics/multipanel`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/multipanel.-1.json`
* Eén voordeel ten opzichte van **Volledig dialoogvenster** is dat het een vereenvoudigde structuur heeft.
* Aanbevolen gebruik: voor dialoogvensters met meerdere tabbladen.

Het dialoogvenster Meerdere deelvensters gebruiken:

1. Het dialoogvenster van het dialoogvenster **Grondbeginselen van dialoogvensters** met de **Meerdere deelvensters** dialoogvenster: volgt u de beschreven stappen voor de [Voorbeeld 2: Dialoogvenster Eén venster](#example-single-panel-dialog)
1. Bewerk de component: het dialoogvenster wordt als volgt weergegeven:

![screen_shot_2012-01-31at50119pm](assets/screen_shot_2012-01-31at50119pm.png)

#### Voorbeeld 4: Rich Dialog {#example-rich-dialog}

De **Rich** wordt een venster met twee tabbladen weergegeven. De eerste tab heeft een tekstveld, een vervolgkeuzemenu en een inklapbaar tekstgebied. Het tweede tabblad bevat een veldset met vier tekstvelden en een set opvouwbare velden met twee tekstvelden. De kenmerken zijn:

* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Geeft 2 tabbladen weer (knooppunttype = `cq:Panel`).
* Het eerste tabblad bevat een ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)` widget met een ` [textfield](/help/sites-developing/xtypes.md#textfield)` en ` [selection](/help/sites-developing/xtypes.md#selection)` widget met 3 opties en een inklapbaar object ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)` met een ` [textarea](/help/sites-developing/xtypes.md#textarea)` widget.
* Het tweede tabblad bevat een ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)` widget met 4 ` [textfield](/help/sites-developing/xtypes.md#textfield)` widgets en een inklapbaar `dialogfieldset` met 2 ` [textfield](/help/sites-developing/xtypes.md#textfield)` widgets.
* Wordt gedefinieerd door het knooppunt:
   `/apps/extjstraining/components/dialogbasics/rich`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/rich.-1.json`

Als u de opdracht **Rich** dialoogvenster:

1. Het dialoogvenster van het dialoogvenster **Grondbeginselen van dialoogvensters** met de **Rich** dialoogvenster: volgt u de beschreven stappen voor de [Voorbeeld 2: Dialoogvenster Eén venster](#example-single-panel-dialog)
1. Bewerk de component: het dialoogvenster wordt als volgt weergegeven:

![screen_shot_2012-01-31at50429pm](assets/screen_shot_2012-01-31at50429pm.png) ![screen_shot_2012-01-31at50519pm](assets/screen_shot_2012-01-31at50519pm.png)

### Dynamische dialoogvensters {#dynamic-dialogs}

De tweede component van de **ExtJS-widgets gebruiken** groep in de Sidetrap wordt **2. Dynamische dialoogvensters** en bevat drie dynamische dialoogvensters die zijn samengesteld met widgets die niet in de verpakking staan, en **met aangepaste javascript-logica**. De dialoogvensters worden hieronder opgeslagen `/apps/extjstraining/components/dynamicdialogs`. De dynamische dialoogvensters zijn:

* het dialoogvenster Tabs wisselen ( `switchtabs` knooppunt): er wordt een venster weergegeven met twee tabbladen. Het eerste tabblad bevat een keuzerondje met drie opties: als een optie is geselecteerd, wordt een tabblad weergegeven dat betrekking heeft op de optie. Het tweede tabblad bevat twee tekstvelden.
* het Arbitrage dialoogvenster ( `arbitrary` knooppunt): er wordt een venster weergegeven met één tab. Het tabblad bevat een veld voor het neerzetten of uploaden van een element en een veld dat informatie weergeeft over de pagina die het element bevat en over het element als ernaar wordt verwezen.
* het dialoogvenster Velden in-/uitschakelen ( `togglefield` knooppunt): er wordt een venster weergegeven met één tab. De tab heeft een selectievakje: wanneer deze is ingeschakeld, wordt een veldset met twee tekstvelden weergegeven.

Als u de opdracht **2. Dynamische dialoogvensters** component op de voorbeeldpagina:

1. Voeg de **2. Dynamische dialoogvensters** naar de voorbeeldpagina van de **ExtJS-widgets gebruiken** in de **Sidetrap**.
1. De component geeft een titel, tekst en een **EIGENSCHAPPEN** koppeling: Klik om de eigenschappen van de alinea weer te geven die in de repository zijn opgeslagen. Klik nogmaals om de eigenschappen te verbergen.

De component wordt als volgt weergegeven:

![chlimage_1-61](assets/chlimage_1-61.png)

#### Voorbeeld 1: Dialoogvenster Tabs wisselen {#example-switch-tabs-dialog}

De **Tabs wisselen** wordt een venster met twee tabbladen weergegeven. Het eerste tabblad bevat een keuzerondje met drie opties: als een optie is geselecteerd, wordt een tabblad weergegeven dat betrekking heeft op de optie. Het tweede tabblad bevat twee tekstvelden.

De belangrijkste kenmerken zijn:

* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Geeft 2 tabbladen weer (knooppunttype = `cq:Panel`): 1 selectietab. is het tweede tabblad afhankelijk van de selectie op het eerste tabblad (3 opties).
* Bevat 3 optionele tabbladen (knooppunttype = `cq:Panel`), heeft elk twee tekstvelden (knooppunttype = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`). Er wordt slechts één optioneel tabblad tegelijk weergegeven.
* Wordt gedefinieerd door de `switchtabs` knooppunt bij:
   `/apps/extjstraining/components/dynamicdialogs/switchtabs`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/switchtabs.-1.json`

De logica wordt als volgt geïmplementeerd via gebeurtenislisteners en javascript-code:

* Het knooppunt Dialoogvenster heeft een &quot; `beforeshow`&quot; listener die alle optionele tabbladen verbergt voordat het dialoogvenster wordt weergegeven:
   `beforeshow="function(dialog){Ejst.x2.manageTabs(dialog.items.get(0));}"`

   `dialog.items.get(0)` Hiermee krijgt u het deelvenster met tabbladen dat het selectievenster en de drie optionele deelvensters bevat.
* De `Ejst.x2` object wordt gedefinieerd in het dialoogvenster `exercises.js` bestand op:
   `/apps/extjstraining/clientlib/js/exercises.js`
* In de `Ejst.x2.manageTabs()` als de waarde van `index` is -1, zijn alle optionele tabbladen verborgen (ik ga van 1 naar 3).
* Het selectietabblad heeft twee listeners: een tab die het geselecteerde tabblad weergeeft wanneer het dialoogvenster wordt geladen (&quot; `loadcontent`&quot; (gebeurtenis) en een item dat het geselecteerde tabblad weergeeft wanneer de selectie wordt gewijzigd (&quot; `selectionchanged`&quot; (gebeurtenis):
   `loadcontent="function(field,rec,path){Ejst.x2.showTab(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.showTab(field);}"`
* In de `Ejst.x2.showTab()` methode:
   `field.findParentByType('tabpanel')` Hiermee wordt het deelvenster met tabbladen opgehaald dat alle tabbladen bevat ( `field` staat voor de selectiewidget)
   `field.getValue()` Hiermee wordt de waarde van de selectie opgehaald, bijvoorbeeld: tab2
   `Ejst.x2.manageTabs()` geeft het geselecteerde tabblad weer.
* Elk optioneel tabblad bevat een listener die het tabblad &quot; `render`&quot; gebeurtenis:
   `render="function(tab){Ejst.x2.hideTab(tab);}"`
* In de `Ejst.x2.hideTab()` methode:
   `tabPanel` is het deelvenster met tabbladen dat alle tabbladen bevat
   `index` is de index van het optionele tabblad
   `tabPanel.hideTabStripItem(index)` verbergt de tab

Het wordt als volgt weergegeven:

![screen_shot_2012-02-01at114745am](assets/screen_shot_2012-02-01at114745am.png)

#### Voorbeeld 2: Willekeurig dialoogvenster {#example-arbitrary-dialog}

Heel vaak wordt de inhoud van de onderliggende component in een dialoogvenster weergegeven. Het hier beschreven dialoogvenster, genaamd **Instelbaar** wordt de inhoud van een andere component opgehaald.

De **Instelbaar** wordt een venster met één tab weergegeven. De tab heeft twee velden: een om een element te plaatsen of te uploaden en een element dat informatie over de pagina met het element en over het element weergeeft als er naar wordt verwezen.

De belangrijkste kenmerken zijn:

* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Geeft 1 widget van tabbladen weer (knooppunttype = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) met 1 paneel (knooppunttype = `cq:Panel`)
* Het deelvenster heeft een widget voor een slim bestand (knooppunttype = `cq:Widget`, xtype = ` [smartfile](/help/sites-developing/xtypes.md#smartfile)`) en een ownerdraw-widget (knooppunttype = `cq:Widget`, xtype = ` [ownerdraw](/help/sites-developing/xtypes.md#ownerdraw)`)
* Wordt gedefinieerd door de `arbitrary` knooppunt bij:
   `/apps/extjstraining/components/dynamicdialogs/arbitrary`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/arbitrary.-1.json`

De logica wordt als volgt geïmplementeerd via gebeurtenislisteners en javascript-code:

* De ownerdraw-widget heeft een &quot; `loadcontent`&quot; listener die informatie weergeeft over de pagina die de component bevat en het element waarnaar wordt verwezen door de widget voor het slimme bestand wanneer de inhoud wordt geladen:
   `loadcontent="function(field,rec,path){Ejst.x2.showInfo(field,rec,path);}"`

   `field` wordt ingesteld met het eigentekenobject
   `path` wordt ingesteld met het inhoudspad van de component (bijvoorbeeld: /content/geometrixx/nl/products/triangle/ui-tutorial/jcr:content/par/dynamicdialogs)
* De `Ejst.x2` object wordt gedefinieerd in het dialoogvenster `exercises.js` bestand op:
   `/apps/extjstraining/clientlib/js/exercises.js`
* In de `Ejst.x2.showInfo()` methode:
   `pagePath` is het pad van de pagina die de component bevat
   `pageInfo` geeft de pagina-eigenschappen in de json-indeling aan
   `reference` is het pad van het element waarnaar wordt verwezen
   `metadata` vertegenwoordigt de metagegevens van het element in json-indeling
   `ownerdraw.getEl().update(html);` Hiermee wordt de gemaakte HTML weergegeven in het dialoogvenster

Als u de opdracht **Instelbaar** dialoogvenster:

1. Het dialoogvenster van het dialoogvenster **Dynamisch dialoogvenster** met de **Instelbaar** dialoogvenster: volgt u de beschreven stappen voor de [Voorbeeld 2: Dialoogvenster Eén venster](#example-single-panel-dialog)
1. Edit the component: the dialog displays as follows:

![](assets/screen_shot_2012-02-01at115300am.png)

#### Example 3: Toggle Fields Dialog {#example-toggle-fields-dialog}

De **Velden in-/uitschakelen** wordt een venster met één tab weergegeven. De tab heeft een selectievakje: wanneer deze is ingeschakeld, wordt een veldset met twee tekstvelden weergegeven.

De belangrijkste kenmerken zijn:

* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Geeft 1 widget van tabbladen weer (knooppunttype = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#textpanel)`) met 1 paneel (knooppunttype = `cq:Panel`).
* Het deelvenster heeft een widget selectie/selectievakje (knooppunttype = `cq:Widget`, xtype = ` [selection](/help/sites-developing/xtypes.md#selection)`, type = ` [checkbox](/help/sites-developing/xtypes.md#checkbox)`) en een inklapbaar dialogfieldset-widget (knooppunttype = `cq:Widget`, xtype = ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)`) die standaard verborgen is, met 2 tekstveldobjecten (knooppunttype = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wordt gedefinieerd door de `togglefields` knooppunt bij:
   `/apps/extjstraining/components/dynamicdialogs/togglefields`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/togglefields.-1.json`

De logica wordt als volgt geïmplementeerd via gebeurtenislisteners en javascript-code:

* het selectietabblad heeft twee listeners: die de dialogfieldset weergeeft wanneer de inhoud wordt geladen (&quot; `loadcontent`&quot; (gebeurtenis) en een gebeurtenis die de dialogfieldset weergeeft wanneer de selectie wordt gewijzigd (&quot; `selectionchanged`&quot; (gebeurtenis):
   `loadcontent="function(field,rec,path){Ejst.x2.toggleFieldSet(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.toggleFieldSet(field);}"`
* De `Ejst.x2` object wordt gedefinieerd in het dialoogvenster `exercises.js` bestand op:
   `/apps/extjstraining/clientlib/js/exercises.js`
* In de `Ejst.x2.toggleFieldSet()` methode:
   `box` is het selectieobject
   `panel` Dit is het deelvenster met de selectie en de widgets voor de dialogfieldset
   `fieldSet` is het dialogfieldset-object
   `show` is de waarde van de selectie (true of false) op basis van &#39; `show`&#39; De dialogfieldset wordt al dan niet weergegeven

Als u de opdracht **Velden in-/uitschakelen** dialoogvenster:

1. Het dialoogvenster van het dialoogvenster **Dynamisch dialoogvenster** met de **Velden in-/uitschakelen** dialoogvenster: volgt u de beschreven stappen voor de [Voorbeeld 2: Dialoogvenster Eén venster](#example-single-panel-dialog)
1. Bewerk de component: het dialoogvenster wordt als volgt weergegeven:

![screen_shot_2012-02-01at115518am](assets/screen_shot_2012-02-01at115518am.png)

### Aangepaste widgets {#custom-widgets}

De widgets uit de doos die bij AEM worden geleverd, moeten de meeste gevallen van gebruik bestrijken. Het kan echter soms nodig zijn om een aangepaste widget te maken die voldoet aan een projectspecifieke vereiste. Aangepaste widgets kunnen worden gemaakt door bestaande widgets uit te breiden. Om u te helpen met dergelijke aanpassingen aan de slag te gaan, **ExtJS-widgets gebruiken** Het pakket bevat drie dialoogvensters die drie verschillende aangepaste widgets gebruiken:

* Het dialoogvenster Meerdere velden ( `multifield` node) geeft een venster weer met één tab. De tab heeft een aangepaste widget met meerdere velden die twee velden heeft: een vervolgkeuzemenu met twee opties en een tekstveld. Omdat het gebaseerd is op het uit-van-de-doos `multifield` widget (die alleen een tekstveld heeft), heeft deze alle functies van de `multifield` widget.
* Het dialoogvenster Bladeren in structuur ( `treebrowse` knooppunt) geeft een venster weer met één tabblad dat een widget voor padbrowsers bevat: wanneer u op de pijl klikt, wordt een venster geopend waarin u door een hiërarchie kunt bladeren en een item kunt selecteren. Het pad van het item wordt vervolgens toegevoegd aan het padveld en wordt voortgezet wanneer het dialoogvenster wordt gesloten.
* een op plug-in gebaseerd dialoogvenster van de teksteditor ( `rteplugin` node) die een aangepaste knop toevoegt aan de Rich Text Editor om aangepaste tekst in te voegen in de hoofdtekst. Het bestaat uit een `richtext` widget (RTE) en van een douaneeigenschap die door het mechanisme van de stop van RTE wordt toegevoegd.

De aangepaste widgets en de insteekmodule zijn opgenomen in de component **3. Aangepaste widgets** van de **ExtJS-widgets gebruiken** pakket. Deze component opnemen in de voorbeeldpagina:

1. Voeg de **3. Aangepaste widgets** naar de voorbeeldpagina van de **ExtJS-widgets gebruiken** in de **Sidetrap**.
1. De component geeft een titel, wat tekst en **EIGENSCHAPPEN** koppeling, de eigenschappen van de alinea die in de opslagplaats zijn opgeslagen. Als u nogmaals klikt, worden de eigenschappen verborgen.
De component wordt als volgt weergegeven:

![chlimage_1-62](assets/chlimage_1-62.png)

#### Voorbeeld 1: Aangepaste widget voor meerdere velden {#example-custom-multifield-widget}

De **Aangepast multiveld** op widget gebaseerd dialoogvenster toont een venster met één tab. De tab heeft een aangepaste widget met meerdere velden die, in tegenstelling tot de standaard widget met één veld, twee velden heeft: een vervolgkeuzemenu met twee opties en een tekstveld.

De **Aangepast multiveld** dialoogvenster op basis van widget:

* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Geeft 1 widget van tabbladen weer (knooppunttype = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) met een deelvenster (knooppunttype = `cq:Widget`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`).
* Het deelvenster bevat een `multifield` widget (knooppunttype = `cq:Widget`, xtype = ` [multifield](/help/sites-developing/xtypes.md#multifield)`).
* De `multifield` widget heeft een fieldconfig (knooppunttype = `nt:unstructured`, xtype = `ejstcustom`, optionsProvider = `Ejst.x3.provideOptions`) die is gebaseerd op het aangepaste xtype &#39; `ejstcustom`&quot;:
   * &#39; `fieldconfig`&#39; is een configuratieoptie van de ` [CQ.form.MultiField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)` object.
   * &#39; `optionsProvider`&#39; is een configuratie van de `ejstcustom` widget. Deze is ingesteld met de `Ejst.x3.provideOptions` methode die wordt gedefinieerd in `exercises.js` om:
      `/apps/extjstraining/clientlib/js/exercises.js`
en retourneert twee opties.
* Wordt gedefinieerd door de `multifield` knooppunt bij:
   `/apps/extjstraining/components/customwidgets/multifield`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/customwidgets/multifield.-1.json`

De aangepaste multifield-widget (xtype = `ejstcustom`):

* Is een JavaScript-object dat wordt aangeroepen `Ejst.CustomWidget`.
* Is gedefinieerd in de `CustomWidget.js` javascript-bestand op:
   `/apps/extjstraining/clientlib/js/CustomWidget.js`
* Hiermee breidt u de ` [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)` widget.
* Bevat 3 velden: `hiddenField` (TextField), `allowField` (ComboBox) en `otherField` (TextField)
* Overschrijvingen `CQ.Ext.Component#initComponent` om de drie velden toe te voegen:
   * `allowField` is een [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection) object van het type &#39;select&#39;. optionsProvider is een configuratie van het Selection-object die wordt geïnstantieerd met de optionsProvider-configuratie van de CustomWidget die is gedefinieerd in het dialoogvenster
   * `otherField` is een [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField) object
* Hiermee overschrijft u de methoden `setValue`, `getValue` en `getRawValue` van [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField) om de waarde van CustomWidget met de indeling in te stellen en op te halen:
   `<allowField value>/<otherField value>, e.g.: 'Bla1/hello'`.
* `ejstcustom`
   `CQ.Ext.reg('ejstcustom', Ejst.CustomWidget);`

****

![screen_shot_2012-02-01at115840am](assets/screen_shot_2012-02-01at115840am.png)

#### Voorbeeld 2: Aangepaste Edge-widget {#example-custom-treebrowse-widget}

De aangepaste **Treebrowse** Op widget gebaseerd dialoogvenster geeft een venster weer met één tabblad dat een aangepast pad bevat voor de browserwidget: wanneer u op de pijl klikt, wordt een venster geopend waarin u door een hiërarchie kunt bladeren en een item kunt selecteren. Het pad van het item wordt vervolgens toegevoegd aan het padveld en wordt voortgezet wanneer het dialoogvenster wordt gesloten.

Het dialoogvenster Aangepaste browse:

* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Geeft 1 widget van tabbladen weer (knooppunttype = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) met een deelvenster (knooppunttype = `cq:Widget`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`).
* Het deelvenster heeft een aangepaste widget (knooppunttype = `cq:Widget`, xtype = `ejstbrowse`)
* Wordt gedefinieerd door de `treebrowse` knooppunt bij:
   `/apps/extjstraining/components/customwidgets/treebrowse`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/customwidgets/treebrowse.-1.json`

De aangepaste widget voor browsers (xtype = `ejstbrowse`):

* Is een JavaScript-object dat wordt aangeroepen `Ejst.CustomWidget`.
* Is gedefinieerd in de `CustomBrowseField.js` javascript-bestand op:
   `/apps/extjstraining/clientlib/js/CustomBrowseField.js`
* Uitbreidingen ` [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)`.
* Hiermee definieert u een bladervenster met de naam `browseWindow`.
* Overschrijvingen ` [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)#onTriggerClick` om het bladervenster te tonen wanneer de pijl wordt geklikt.
* Definieert een [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel) object:
   * Het krijgt zijn gegevens door servlet te roepen die bij wordt geregistreerd `/bin/wcm/siteadmin/tree.json`.
   * De basis is &quot; `apps/extjstraining`&quot;.
* Definieert een `window` object ( ` [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)`):
   * Gebaseerd op het vooraf gedefinieerde deelvenster.
   * Heeft een **OK** die de waarde van het geselecteerde pad instelt en het deelvenster verbergt.
* Het venster is verankerd onder de **Pad** veld.
* Het geselecteerde pad wordt van het bladerveld naar het venster doorgegeven `show` gebeurtenis.
* Registreert zichzelf als &#39; `ejstbrowse`&#39; xtype:
   `CQ.Ext.reg('ejstbrowse', Ejst.CustomBrowseField);`

Als u de opdracht **Aangepaste Treebrowse** dialoogvenster op basis van widget:

1. Het dialoogvenster van het dialoogvenster **Aangepaste widgets** met de **Aangepaste Treebrowse** dialoogvenster: volgt u de beschreven stappen voor de [Voorbeeld 2: Dialoogvenster Eén venster](#example-single-panel-dialog)
1. Bewerk de component: het dialoogvenster wordt als volgt weergegeven:

![screen_shot_2012-02-01at120104pm](assets/screen_shot_2012-02-01at120104pm.png)

#### Voorbeeld 3: Insteekmodule Rich Text Editor (RTE) {#example-rich-text-editor-rte-plug-in}

De **Insteekmodule Rich Text Editor (RTE)** Het dialoogvenster is gebaseerd op een dialoogvenster van de Rich Text Editor met een aangepaste knop waarmee u aangepaste tekst tussen vierkante haakjes kunt invoegen. De aangepaste tekst kan worden geparseerd door bepaalde logica aan serverzijde (niet geïmplementeerd in dit voorbeeld), bijvoorbeeld door tekst toe te voegen die op het opgegeven pad is gedefinieerd:

De **RTE-insteekmodule** gebaseerd dialoogvenster:

* Wordt gedefinieerd door het knooppunt rteplugin op:
   `/apps/extjstraining/components/customwidgets/rteplugin`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/customwidgets/rteplugin.-1.json`
* De `rtePlugins` node heeft een onderliggende node `inserttext` (knooppunttype = `nt:unstructured`) genoemd naar de plug-in. Het heeft een eigenschap genaamd `features`, die bepaalt welke van de plugin eigenschappen beschikbaar aan RTE zijn.

De RTE-plug-in:

* Is een JavaScript-object dat wordt aangeroepen `Ejst.InsertTextPlugin`.
* Is gedefinieerd in de `InsertTextPlugin.js` javascript-bestand op:
   `/apps/extjstraining/clientlib/js/InsertTextPlugin.js`
* Hiermee breidt u de ` [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)` object.
* De volgende methoden definiëren de ` [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)` -object en worden overschreven in de implementerende plug-in:
   * `getFeatures()` retourneert een array met alle functies die de plug-in beschikbaar stelt.
   * `initializeUI()` voegt de nieuwe knoop aan de toolbar van RTE toe.
   * `notifyPluginConfig()` geeft de titel en de tekst weer wanneer de knop wordt aangeroepen.
   * `execute()` wordt aangeroepen wanneer op de knop wordt geklikt en de insteekactie wordt uitgevoerd: er wordt een venster weergegeven waarin de tekst wordt gedefinieerd die moet worden opgenomen.
* `insertText()` voegt tekst in met behulp van het bijbehorende dialoogobject `Ejst.InsertTextPlugin.Dialog` (zie hierna).
* `executeInsertText()` wordt opgeroepen door `apply()` methode van de dialoog, die wordt teweeggebracht wanneer **OK** wordt geklikt.
* Registreert zichzelf als &#39; `inserttext`&#39;plug-in:
   `CQ.form.rte.plugins.PluginRegistry.register("inserttext", Ejst.InsertTextPlugin);`
* de `Ejst.InsertTextPlugin.Dialog` wordt het dialoogvenster gedefinieerd dat wordt geopend wanneer op de insteekmodule wordt geklikt. Het dialoogvenster bestaat uit een deelvenster, een formulier, een tekstveld en 2 knoppen (**OK** en **Annuleren**).

Als u de opdracht **Insteekmodule Rich Text Editor (RTE)** gebaseerd dialoogvenster:

1. Het dialoogvenster van het dialoogvenster **Aangepaste widgets** met de **Insteekmodule Rich Text Editor (RTE)** gebaseerd dialoogvenster: volgt u de beschreven stappen voor de [Voorbeeld 2: Dialoogvenster Eén venster](#example-single-panel-dialog)
1. Bewerk de component.
1. Klik op het laatste pictogram aan de rechterkant (het pictogram met vier pijlen). Voer een pad in en klik op **OK**: Het pad wordt tussen haakjes weergegeven ([ ]).
1. Klikken **OK** om de Rich Text Editor te sluiten.

De **Insteekmodule Rich Text Editor (RTE)** Het dialoogvenster ziet er als volgt uit:

![screen_shot_2012-02-01at120254pm](assets/screen_shot_2012-02-01at120254pm.png)

>[!NOTE]
>
>*[]*

### Tree Overview {#tree-overview}

De out-of-the-box ` [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)` -object biedt een gestructureerde UI-representatie van gegevens met boomstructuur. ****`TreePanel` Het venster zelf kan worden gekoppeld of losgekoppeld. In dit voorbeeld is de vensterlogica ingesloten in de JSP-component tussen &lt;script>&lt;/script> -tags.

Als u de opdracht **Overzicht van boomstructuur** aan de steekproefpagina:

1. Voeg de **4. Overzicht van boomstructuur** naar de voorbeeldpagina van de **ExtJS-widgets gebruiken** in de **Sidetrap**.
1. De component wordt weergegeven:
   * een titel, met tekst
   * a **EIGENSCHAPPEN** koppeling: Klik om de eigenschappen van de alinea weer te geven die in de repository zijn opgeslagen. Klik nogmaals om de eigenschappen te verbergen.
   * een zwevend venster met een boomrepresentatie van de repository, die kan worden uitgebreid.

De component wordt als volgt weergegeven:

![screen_shot_2012-02-01at120639pm](assets/screen_shot_2012-02-01at120639pm.png)

De component Overzicht van de Boom:

* Wordt gedefinieerd bij:
   `/apps/extjstraining/components/treeoverview`

* In het dialoogvenster kunt u de grootte van het venster instellen en het venster koppelen/ontkoppelen (zie de details hieronder).

The component jsp:

* Haalt de breedte, hoogte en gedokte eigenschappen op van de repository.
* Geeft enige tekst weer over de gegevensindeling van het boomoverzicht.
* Hiermee sluit u de vensterlogica in de jsp van de component tussen javascript-tags in.
* Wordt gedefinieerd bij:
   `apps/extjstraining/components/treeoverview/content.jsp`

De javascript-code die is ingesloten in de jsp van de component:

* Definieert een `tree` door te proberen een structuurvenster van de pagina op te halen.
* Als het venster met de boomstructuur niet bestaat, `treePanel` ([CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)) is gemaakt:
   * `treePanel` bevat de gegevens die worden gebruikt om het venster te maken.
   * De gegevens worden teruggewonnen door servlet te roepen die bij wordt geregistreerd:
      `/bin/wcm/siteadmin/tree.json`
* De `beforeload` listener zorgt ervoor dat het aangeklikte knooppunt wordt geladen.
* De `root` object stelt het pad in `apps/extjstraining` als de hoofdstructuur van de boom.
* `tree` ( ` [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)`) wordt ingesteld op basis van de vooraf gedefinieerde `treePanel`en wordt weergegeven met:
   `tree.show();`
* Als het venster al bestaat, wordt het weergegeven op basis van de breedte, hoogte en gedokte eigenschappen die zijn opgehaald uit de opslagplaats.

Het dialoogvenster Component:

* Geeft 1 tab met 2 velden weer om de grootte (breedte en hoogte) van het venster met het overzicht van de structuur in te stellen en 1 veld om het venster te koppelen/ontkoppelen
* Wordt gedefinieerd door een knooppunt (knooppunttype = `cq:Dialog`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`).
* Het deelvenster heeft een widget Deelveld sizefield (knooppunttype = `cq:Widget`, xtype = ` [sizefield](/help/sites-developing/xtypes.md#sizefield)`) en een selectiewidget (knooppunttype = `cq:Widget`, xtype = ` [selection](/help/sites-developing/xtypes.md#selection)`, type = `radio`) met 2 opties (true/false)
* Wordt gedefinieerd door het dialoogknooppunt op:
   `/apps/extjstraining/components/treeoverview/dialog`
* Wordt in json-indeling weergegeven door het volgende aan te vragen:
   `https://localhost:4502/apps/extjstraining/components/treeoverview/dialog.-1.json`
* Hieronder wordt weergegeven:

![screen_shot_2012-02-01at120745pm](assets/screen_shot_2012-02-01at120745pm.png)

### Rasteroverzicht {#grid-overview}

Een deelvenster Raster vertegenwoordigt gegevens in tabelvorm van rijen en kolommen. Het bestaat uit:

* Winkel: het model met de gegevensrecords (rijen).
* Kolommodel: de kolomsamenstelling.
* Weergave: kapselt het gebruikersinterface in.
* Selectiemodel: het selectiegedrag.

De component Rasteroverzicht die is opgenomen in de **ExtJS-widgets gebruiken** Het pakket toont hoe u gegevens in tabelvorm kunt weergeven:

* In voorbeeld 1 worden statische gegevens gebruikt.
* In voorbeeld 2 worden gegevens gebruikt die uit de gegevensopslagruimte zijn opgehaald.

De component Rasteroverzicht opnemen in de voorbeeldpagina:

1. Voeg de **5. Rasteroverzicht** naar de voorbeeldpagina van de **ExtJS-widgets gebruiken** in de **Sidetrap**.
1. De component wordt weergegeven:
   * een titel met tekst
   * a **EIGENSCHAPPEN** koppeling: Klik om de eigenschappen van de alinea weer te geven die in de repository zijn opgeslagen. Klik nogmaals om de eigenschappen te verbergen.
   * een zwevend venster met gegevens in tabelvorm.

De component wordt als volgt weergegeven:

![screen_shot_2012-02-01at121109pm](assets/screen_shot_2012-02-01at121109pm.png)

#### Voorbeeld 1: Standaardraster {#example-default-grid}

In zijn versie van de doos, **Rasteroverzicht** geeft een venster weer met statische gegevens in tabelvorm. In dit voorbeeld wordt de logica op twee manieren ingesloten in de jsp van de component:

* the generic logic is defined between &lt;script>&lt;/script> tags
* the specific logic is available in a separate .js file and is linked to in the jsp. This setup enables to easily switch between the two logic (static/dynamic) by commenting the desired &lt;script> tags.

The Grid Overview component:

* Is defined at:
   `/apps/extjstraining/components/gridoverview`
* In dit dialoogvenster kunt u de grootte van het venster instellen en het venster koppelen/ontkoppelen.

The component jsp:

* Haalt de breedte, hoogte en gedokte eigenschappen op van de repository.
* Geeft wat tekst weer als inleiding op de gegevensindeling van het rasteroverzicht.
* Verwijst naar javascript-code die het GridPanel-object definieert:
   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script>`

   `defaultgrid.js` bepaalt sommige statische gegevens als basis voor het voorwerp GridPanel.
* Hiermee wordt javascript-code ingesloten tussen javascript-tags die het Window-object definiëren dat het GridPanel-object gebruikt.
* Wordt gedefinieerd bij:
   `apps/extjstraining/components/gridoverview/content.jsp`

De javascript-code die is ingesloten in de jsp van de component:

* Definieert de `grid` -object door te proberen de venstercomponent van de pagina op te halen:
   `var grid = CQ.Ext.getCmp("<%= node.getName() %>-grid");`
* Indien `grid` bestaat niet, a [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) object ( `gridPanel`) wordt gedefinieerd door het aanroepen van de `getGridPanel()` methode (zie hieronder). Deze methode is gedefinieerd in `defaultgrid.js`.
* `grid` is een ` [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)` object, gebaseerd op het vooraf gedefinieerde GridPanel, en wordt weergegeven: `grid.show();`
* Indien `grid` al bestaat, wordt deze weergegeven op basis van de breedte, hoogte en gedokte eigenschappen die zijn opgehaald uit de opslagplaats.

Het javascript-bestand ( `defaultgrid.js`) waarnaar wordt verwezen in de component jsp definieert de `getGridPanel()` methode die wordt aangeroepen door het script dat is ingesloten in de JSP en die een ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` object, op basis van statische gegevens. De logica is als volgt:

* `myData` is een array van statische gegevens die zijn opgemaakt als een tabel van 5 kolommen en 4 rijen.
* `store` is een `CQ.Ext.data.Store` object dat verbruikt `myData`.
* `store` wordt geladen in het geheugen:
   `store.load();`
* `gridPanel` is een ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` object dat verbruikt `store`:
   * de kolombreedten worden altijd opnieuw proportioneel:
      `forceFit: true`
   * u kunt slechts één rij tegelijk selecteren:
      `singleSelect:true`

#### Voorbeeld 2: Zoekraster van verwijzing {#example-reference-search-grid}

Wanneer u het pakket installeert, `content.jsp` van de **Rasteroverzicht** geeft een raster weer dat is gebaseerd op statische gegevens. Het is mogelijk om de component te wijzigen om een raster met de volgende kenmerken weer te geven:

* Bevat drie kolommen.
* Is gebaseerd op gegevens die van de bewaarplaats door een servlet te roepen worden teruggewonnen.
* De cellen van de laatste kolom kunnen worden bewerkt. De waarde blijft bestaan in een `test` eigenschap onder het knooppunt dat wordt gedefinieerd door het pad dat in de eerste kolom wordt weergegeven.

Zoals eerder uitgelegd in de sectie, krijgt het vensterobject zijn ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` object aanroepen `getGridPanel()` in de `defaultgrid.js` bestand bij `/apps/extjstraining/components/gridoverview/defaultgrid.js`. De **Grid overzichtscomponent **verstrekt een verschillende implementatie voor `getGridPanel()` methode, gedefinieerd in de `referencesearch.js` bestand bij `/apps/extjstraining/components/gridoverview/referencesearch.js`. Door het .js dossier te schakelen dat in component jsp van verwijzingen wordt voorzien, zal het net op gegevens worden gebaseerd die van de bewaarplaats worden teruggewonnen.

Van .js dossier schakelen dat in component jsp van verwijzingen wordt voorzien:

1. In **CRXDE Lite** in de `content.jsp` bestand van de component, de regel met het `defaultgrid.js` zodat het er als volgt uitziet:
   `<!-- script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script-->`
1. Verwijder de opmerking uit de regel met de `referencesearch.js` zodat het er als volgt uitziet:
   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/referencesearch.js"></script>`
1. Sla de wijzigingen op.
1. Vernieuw de voorbeeldpagina.

De component wordt als volgt weergegeven:

![screen_shot_2012-02-01at121429pm](assets/screen_shot_2012-02-01at121429pm.png)

De javascript-code waarnaar in de component jsp wordt verwezen ( `referencesearch.js`) definieert de `getGridPanel()` methode geroepen van component jsp en keert een ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` object, op basis van gegevens die dynamisch uit de gegevensopslagruimte worden opgehaald. De logica in `referencesearch.js` bepaalt sommige dynamische gegevens als basis voor GridPanel:

* `reader` is een ` [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader)`-object dat de servlet-reactie in json-indeling voor 3 kolommen leest.
* `cm` is een ` [CQ.Ext.grid.ColumnModel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel)` object voor 3 kolommen.
De kolomcellen van de &quot;Test&quot;kunnen worden uitgegeven aangezien zij met een redacteur worden bepaald:
   `editor: new [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)({})`
* de kolommen kunnen worden gesorteerd:
   `cm.defaultSortable = true;`
* `store` is een ` [CQ.Ext.data.GroupingStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)` object:
   * het krijgt zijn gegevens door servlet te roepen die bij &quot; wordt geregistreerd `/bin/querybuilder.json`&quot; met een paar parameters die worden gebruikt om de query te filteren
   * zij is gebaseerd op `reader`, vooraf gedefinieerd
   * de tabel wordt gesorteerd volgens de &quot;**jcr:pad**&#39; kolom in oplopende volgorde
* `gridPanel` is een ` [CQ.Ext.grid.EditorGridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)` object dat kan worden bewerkt:
   * het is gebaseerd op de vooraf gedefinieerde `store` en op het kolommodel `cm`
   * u kunt slechts één rij tegelijk selecteren:
      `sm: new [CQ.Ext.grid.RowSelectionModel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.RowSelectionModel)({singleSelect:true})`
   * de `afteredit` listener zorgt ervoor dat na een cel in de map &quot;**Testen**&quot; kolom is bewerkt:
      * de eigenschap &#39; `test`&#39; van het knooppunt op het pad dat wordt gedefinieerd door &quot;**jcr:pad**&quot; column wordt ingesteld in de repository met de waarde van de cel
      * als de POST is gelukt, wordt de waarde toegevoegd aan de `store` object, anders wordt het geweigerd
