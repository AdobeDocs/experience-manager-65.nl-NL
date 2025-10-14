---
title: De Bulk-editor ontwikkelen
description: Door tags toe te wijzen, kan inhoud worden gecategoriseerd en ingedeeld
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 8753aaab-959f-459b-bdb6-057cbe05d480
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1833'
ht-degree: 0%

---

# De Bulk-editor ontwikkelen{#developing-the-bulk-editor}

In deze sectie wordt beschreven hoe u het gereedschap Bulk-editor kunt ontwikkelen en hoe u de component Productlijst kunt uitbreiden. Deze component is gebaseerd op de Bulk-editor.

## Query-parameters voor de bulkeditor {#bulk-editor-query-parameters}

Wanneer het werken met de Redacteur van het Bulk, zijn er verscheidene vraagparameters die u aan URL kunt toevoegen om de Redacteur van het Bulk met een specifieke configuratie te roepen. Als u de Redacteur van het Bulk altijd met een bepaalde configuratie, bijvoorbeeld, zoals in de component van de Lijst van het Product wilt worden gebruikt, dan moet u `bulkeditor.jsp` (in /libs/wcm/core/components/bulkeditor) uitgeven of een component met de specifieke configuratie tot stand brengen. Wijzigingen die zijn aangebracht met behulp van queryparameters zijn niet permanent.

Als u bijvoorbeeld het volgende typt in de URL van uw browser:

`https://<servername><port_number>/etc/importers/bulkeditor.html?rootPath=/content/geometrixx/en&queryParams=geometrixx&initialSearch=true&hrp=true`

De vertoningen van de Redacteur van het Bulk zonder het **gebied van de Weg van de Wortel 1&rbrace; als hrp=true verbergt het gebied.** Met de parameter hrp=false wordt het veld weergegeven (de standaardwaarde).

Hieronder volgt een lijst met queryparameters voor de Bulk Editor:

>[!NOTE]
>
>Elke parameter kan een lange en een korte naam hebben. De lange naam voor het hoofdpad van de zoekopdracht is bijvoorbeeld `rootPath` , de korte naam is `rp` . Als de lange naam niet wordt bepaald, wordt korte gelezen van het verzoek.

<table>
 <tbody>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p> Parameter</p> <p>(lange naam/korte naam) <br /> </p> </td>
   <td> Tekst <br /> </td>
   <td> Beschrijving <br /> </td>
  </tr>
  <tr>
   <td> rootPath / rp <br /> </td>
   <td> String </td>
   <td> zoekhoofdpad</td>
  </tr>
  <tr>
   <td> queryParams / qp<br /> </td>
   <td> String</td>
   <td> zoekquery</td>
  </tr>
  <tr>
   <td> contentMode / cm<br /> </td>
   <td> Boolean</td>
   <td> wanneer waar, wordt de inhoudswijze toegelaten <br /> </td>
  </tr>
  <tr>
   <td> colsValue / cv<br /> </td>
   <td> String[]</td>
   <td> gezochte eigenschappen (gecontroleerde waarden van colsSelection weergegeven als checkboxes)</td>
  </tr>
  <tr>
   <td> extraCols / ec <br /> </td>
   <td> String[]</td>
   <td> extra gezochte eigenschappen (die in een komma-gescheiden tekstgebied worden getoond)</td>
  </tr>
  <tr>
   <td> initialSearch / is<br /> </td>
   <td> Boolean</td>
   <td> wanneer waar, wordt de vraag uitgevoerd op paginading <br /> </td>
  </tr>
  <tr>
   <td> colsSelection / cs<br /> </td>
   <td> String[]</td>
   <td> selectie van gezochte eigenschappen (weergegeven als selectievakjes)</td>
  </tr>
  <tr>
   <td> showGridOnly / sgo <br /> </td>
   <td> Boolean</td>
   <td> indien waar (true), alleen het raster en niet het deelvenster Zoeken <br /> </td>
  </tr>
  <tr>
   <td> searchPanelCollapsed / spc</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt het zoekvenster samengevouwen tijdens het laden</td>
  </tr>
  <tr>
   <td> hideRootPath / hrp</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt het veld van het hoofdpad verborgen</td>
  </tr>
  <tr>
   <td> hideQueryParams / hqp</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt het queryveld verborgen</td>
  </tr>
  <tr>
   <td> hideContentMode / hcm</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt het veld voor de inhoudsmodus verborgen</td>
  </tr>
  <tr>
   <td> hideColsSelection / hcs</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt het selectieveld voor kolommen verborgen</td>
  </tr>
  <tr>
   <td> hideExtraCols / hec</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt het veld Extra kolommen verborgen</td>
  </tr>
  <tr>
   <td> hideSearchButton</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de zoekknop verborgen</td>
  </tr>
  <tr>
   <td> hideSaveButton / hsavep</td>
   <td> Boolean</td>
   <td> indien true, wordt de knop Opslaan verborgen</td>
  </tr>
  <tr>
   <td> hideExportButton / hexpb</td>
   <td> Boolean</td>
   <td> indien true, wordt de knop Exporteren verborgen</td>
  </tr>
  <tr>
   <td> hideImportButton / hib</td>
   <td> Boolean</td>
   <td> indien true, wordt de knop Importeren verborgen</td>
  </tr>
  <tr>
   <td> hideResultNumber / hrn</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de tekst van het rasterzoekresultaatnummer verborgen</td>
  </tr>
  <tr>
   <td> hideInsertButton / hinsertB</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de knop voor het invoegen van het raster verborgen</td>
  </tr>
  <tr>
   <td> hideDeleteButton / hdelb</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de knop Rasterverwijdering verborgen</td>
  </tr>
  <tr>
   <td> hidePathCol / hpc</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de rasterkolom "pad" verborgen</td>
  </tr>
 </tbody>
</table>

### Een op Bulk Editor gebaseerde component ontwikkelen: de component Productlijst {#developing-a-bulk-editor-based-component-the-product-list-component}

Deze sectie biedt een overzicht van het gebruik van de Bulk-editor en een beschrijving van de bestaande Geometrixx-component op basis van de Bulk-editor: de component Productlijst.

Met de component Productlijst kunnen gebruikers een tabel met gegevens weergeven en bewerken. U kunt bijvoorbeeld de component Productlijst gebruiken om producten in een catalogus te vertegenwoordigen. De informatie wordt voorgesteld in een standaard HTML lijst en om het even welk uitgeven wordt uitgevoerd in **geeft** dialoogdoos uit, die een widget BulkEditor bevat. (Deze Bulk-editor is hetzelfde als de editor die beschikbaar is via /etc/importers/bulkeditor.html of via het menu Gereedschappen.) De component van de Lijst van het Product is gevormd voor specifieke, beperkte functionaliteit van de Redacteur van het Bulk. Elk deel van de Redacteur van het Bulk (of componenten die uit de Redacteur van het Bulk worden afgeleid) kan worden gevormd.

Met de Bulk-editor kunt u de rijen toevoegen, wijzigen, verwijderen, filteren en exporteren, wijzigingen opslaan en een set rijen importeren. Elke rij wordt opgeslagen als een knoop onder de de componenteninstantie van de Lijst van het Product zelf. Elke cel is een eigenschap van elk knooppunt. Dit is een ontwerpkeuze die eenvoudig kan worden gewijzigd. U kunt knooppunten bijvoorbeeld ergens anders in de opslagplaats opslaan. De rol van de vraagserver is de lijst van de knopen terug te keren om te tonen; het onderzoekspad wordt bepaald als instantie van de Lijst van het Product.

De broncode van de component Product List is beschikbaar in de gegevensopslagruimte op /apps/geometrixx/components/productlist en bestaat uit verschillende onderdelen, zoals alle Adobe Experience Manager-componenten (AEM):

* HTML-rendering: de rendering wordt uitgevoerd in een JSP-bestand (/apps/geometrixx/components/productlist/productlist.jsp). JSP leest subnodes van de huidige component van de Lijst van het Product en toont elk van hen als rij van een lijst van HTML.
* Het dialoogvenster Bewerken waarin u de configuratie van de Bulk-editor definieert. Configureer het dialoogvenster zodat het voldoet aan de behoeften van de component: beschikbare kolommen en mogelijke acties die op het raster of op de zoekopdracht worden uitgevoerd. Zie [&#x200B; de configuratieeigenschappen van de Redacteur van het Bulk &#x200B;](#bulk-editor-configuration-properties) voor informatie over alle configuratieeigenschappen.

Hier volgt een XML-weergave van de subknooppunten van het dialoogvenster:

```xml
        <editor
            jcr:primaryType="cq:Widget"
            colsSelection="[ProductId,ProductName,Color,CatalogCode,SellingSku]"
            colsValue="[ProductId,ProductName,Color,CatalogCode,SellingSku]"
            contentMode="false"
            exportURL="/etc/importers/bulkeditor/export.tsv"
            extraCols="Selection"
            hideColsSelection="false"
            hideContentMode="true"
            hideDeleteButton="false"
            hideExportButton="false"
            hideExtraCols="true"
            hideImportButton="false"
            hideInsertButton="false"
            hideMoveButtons="false"
            hidePathCol="true"
            hideRootPath="true"
            hideSaveButton="false"
            hideSearchButton="false"
            importURL="/etc/importers/bulkeditor/import"
            initialSearch="true"
            insertedResourceType="geometrixx/components/productlist/sku"
            queryParams=""
            queryURL="/etc/importers/bulkeditor/query.json"
            saveURL="/etc/importers/bulkeditor/save"
            xtype="bulkeditor">
            <saveButton
                jcr:primaryType="nt:unstructured"
                text="Save modifications"/>
            <searchButton
                jcr:primaryType="nt:unstructured"
                text="Apply filter"/>
            <queryParamsInput
                jcr:primaryType="nt:unstructured"
                fieldDescription="Enter here your filters"
                fieldLabel="Filters"/>
            <searchPanel
                jcr:primaryType="nt:unstructured"
                height="200">
                <defaults
                    jcr:primaryType="nt:unstructured"
                    labelWidth="150"/>
            </searchPanel>
            <grid
                jcr:primaryType="nt:unstructured"
                height="275"/>
            <store jcr:primaryType="nt:unstructured">
                <sortInfo
                    jcr:primaryType="nt:unstructured"
                    direction="ASC"
                    field="CatalogCode"/>
            </store>
            <colModel
                jcr:primaryType="nt:unstructured"
                width="150"/>
            <colsMetadata jcr:primaryType="nt:unstructured">
                <Selection
                    jcr:primaryType="nt:unstructured"
                    checkbox="true"
                    forcedPosition="0"
                    headerText=""/>
                <ProductId
                    jcr:primaryType="nt:unstructured"
                    cellCls="productlist-cell-productid"
                    headerText="Product Id"/>
                <ProductName
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #FFCC99;"
                    headerText="Product Name"/>
                <CatalogCode
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #EDEDED;"
                    headerText="Catalog Code"/>
                <Color jcr:primaryType="nt:unstructured">
                    <editor
                        jcr:primaryType="nt:unstructured"
                        store="[Blue,Red,Yellow]"
                        triggerAction="all"
                        typeAhead="true"
                        xtype="combo"/>
                </Color>
                <SellingSku
                    jcr:primaryType="nt:unstructured"
                    headerText="Sku Id"/>
            </colsMetadata>
        </editor>
```

### Eigenschappen van de Bulkeditor {#bulk-editor-configuration-properties}

Elk deel van de Redacteur van het Bulk kan worden gevormd. De volgende lijst maakt een lijst van alle configuratieeigenschappen voor de Redacteur van het Bulk.

<table>
 <tbody>
  <tr>
   <td>Eigenschapnaam</td>
   <td>Definitie</td>
  </tr>
  <tr>
   <td>rootPath</td>
   <td>Hoofdpad zoeken</td>
  </tr>
  <tr>
   <td>queryParams</td>
   <td>Zoekquery</td>
  </tr>
  <tr>
   <td>contentMode</td>
   <td>True to enable content mode: properties are read on jcr:content node and not on search result node</td>
  </tr>
  <tr>
   <td>colsValue</td>
   <td>Gezocht eigenschappen (controleerden waarden van colsSelection die als checkboxes worden getoond)</td>
  </tr>
  <tr>
   <td>extraCols</td>
   <td>Extra gezochte eigenschappen (weergegeven in een komma-gescheiden tekstveld)</td>
  </tr>
  <tr>
   <td>initialSearch</td>
   <td>True to perform query on page load</td>
  </tr>
  <tr>
   <td>colsSelection</td>
   <td>Selectie van gezochte eigenschappen (weergegeven als selectievakjes)</td>
  </tr>
  <tr>
   <td>showGridOnly</td>
   <td>True om alleen het raster en niet het zoekdeelvenster weer te geven (vergeet niet om de initialSearch in te stellen op true)</td>
  </tr>
  <tr>
   <td>searchPanelCollapsed</td>
   <td>Waar (true) om het zoekdeelvenster samen te vouwen, standaard</td>
  </tr>
  <tr>
   <td>hideRootPath</td>
   <td>Veld van hoofdpad verbergen</td>
  </tr>
  <tr>
   <td>hideQueryParams</td>
   <td>Zoekveld verbergen</td>
  </tr>
  <tr>
   <td>hideContentMode</td>
   <td>Veld inhoudsmodus verbergen</td>
  </tr>
  <tr>
   <td>hideColsSelection</td>
   <td>Selectieveld Kleuren verbergen</td>
  </tr>
  <tr>
   <td>hideExtraCols</td>
   <td>Extra kolommen verbergen, veld</td>
  </tr>
  <tr>
   <td>hideSearchButton</td>
   <td>Zoekknop verbergen</td>
  </tr>
  <tr>
   <td>hideSaveButton</td>
   <td>Knop Opslaan verbergen</td>
  </tr>
  <tr>
   <td>hideExportButton</td>
   <td>De knop Exporteren verbergen</td>
  </tr>
  <tr>
   <td>hideImportButton</td>
   <td>Knop Importeren verbergen</td>
  </tr>
  <tr>
   <td>hideResultNumber</td>
   <td>Tekst van het rasterzoekresultaatnummer verbergen</td>
  </tr>
  <tr>
   <td>hideInsertButton</td>
   <td>Knop voor rasterinvoeging verbergen</td>
  </tr>
  <tr>
   <td>hideDeleteButton</td>
   <td>Knop Raster verwijderen verbergen</td>
  </tr>
  <tr>
   <td>hidePathCol</td>
   <td>Rasterkolom "pad" verbergen</td>
  </tr>
  <tr>
   <td>queryURL</td>
   <td>Pad naar queryserver</td>
  </tr>
  <tr>
   <td>exportURL</td>
   <td>Pad naar exportserver</td>
  </tr>
  <tr>
   <td>importURL</td>
   <td>Pad naar importservlet</td>
  </tr>
  <tr>
   <td>insertResourceType</td>
   <td>Het type van middel dat aan knoop wordt toegevoegd wanneer een rij wordt opgenomen</td>
  </tr>
  <tr>
   <td>saveButton</td>
   <td>Knopwidgetconfiguratie opslaan</td>
  </tr>
  <tr>
   <td>searchButton</td>
   <td>Widget-config voor zoekknop</td>
  </tr>
  <tr>
   <td>exportButton</td>
   <td>Knopwidget configureren</td>
  </tr>
  <tr>
   <td>importButton</td>
   <td>Knopwidgetconfiguratie importeren</td>
  </tr>
  <tr>
   <td>searchPanel</td>
   <td>Widget-configuratie van deelvenster Zoeken</td>
  </tr>
  <tr>
   <td>raster</td>
   <td>Configuratie van rasterwidget</td>
  </tr>
  <tr>
   <td>winkel</td>
   <td>Winkelconfiguratie</td>
  </tr>
  <tr>
   <td>colModel</td>
   <td>Configuratie van rasterkolommodel</td>
  </tr>
  <tr>
   <td>rootPathInput</td>
   <td>config van hoofdpad-widget</td>
  </tr>
  <tr>
   <td>queryParamsInput</td>
   <td>queryParams-widget config</td>
  </tr>
  <tr>
   <td>contentModeInput</td>
   <td>contentMode widget config</td>
  </tr>
  <tr>
   <td>colsSelectionInput</td>
   <td>colsSelection widget config</td>
  </tr>
  <tr>
   <td>extraColsInput</td>
   <td>ExtraCols-widget config</td>
  </tr>
  <tr>
   <td>colsMetadata</td>
   <td>Configuratie van kolommetagegevens. Mogelijke eigenschappen zijn (toegepast op alle cellen van de kolom): <br />
    <ul>
     <li>cellStyle: html-stijl </li>
     <li>cellCls: css, klasse </li>
     <li>readOnly: true om waarde niet te kunnen wijzigen </li>
     <li>selectievakje: true om alle cellen van de kolom als selectievakjes te definiëren (waarden true/false) </li>
     <li>forcePosition: geheel getal om aan te geven waar de kolom in het raster moet worden geplaatst (tussen 0 en het aantal kolommen-1)<p><br /> </p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Configuratie van kolommetagegevens {#columns-metadata-configuration}

U kunt voor elke kolom vormen:

* weergave-eigenschappen: html-stijl, CSS-klasse en alleen-lezen

* een selectievakje
* een geforceerde positie

CSS- en alleen-lezen kolommen

De Bulkeditor heeft drie kolomconfiguraties:

* CSS-klassenaam van cel (cellCls): een CSS-klassenaam die aan elke cel van de geconfigureerde kolom wordt toegevoegd.
* Celstijl (cellStyle): een HTML-stijl die aan elke cel van de geconfigureerde kolom wordt toegevoegd.
* Alleen-lezen (readOnly): alleen-lezen wordt ingesteld voor elke cel van de geconfigureerde kolom.

De configuratie moet als volgt worden gedefinieerd:

```
"colsMetadata": {
"Column name": {
     "cellStyle": "html style",
     "cellCls": "CSS class",
     "readOnly": true/false
}
}
```

Het volgende voorbeeld is te vinden in de component productlist (/apps/geometrixx/components/productlist/dialog/items/editor/colsMetadata):

```xml
            <colsMetadata jcr:primaryType="nt:unstructured">
                <Selection
                    jcr:primaryType="nt:unstructured"
                    checkbox="true"
                    forcedPosition="0"
                    headerText=""/>
                <ProductId
                    jcr:primaryType="nt:unstructured"
                    cellCls="productlist-cell-productid"
                    headerText="Product Id"/>
                <ProductName
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #FFCC99;"
                    headerText="Product Name"/>
                <CatalogCode
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #EDEDED;"
                    headerText="Catalog Code"/>
                <Color jcr:primaryType="nt:unstructured">
                    <editor
                        jcr:primaryType="nt:unstructured"
                        store="[Blue,Red,Yellow]"
                        triggerAction="all"
                        typeAhead="true"
                        xtype="combo"/>
                </Color>
                <SellingSku
                    jcr:primaryType="nt:unstructured"
                    headerText="Sku Id"/>
            </colsMetadata>
```

**Checkbox**

Als het checkbox configuratiebezit aan waar wordt geplaatst, worden alle cellen van de kolom teruggegeven als checkboxes. Een gecontroleerd vakje verzendt **waar** naar de server sparen servlet, **vals** anders. In het kopbalmenu, kunt u allen **ook selecteren of** niets **selecteren.** Deze opties worden ingeschakeld als de geselecteerde koptekst de koptekst van een kolom in het selectievakje is.

In het eerste voorbeeld bevat de selectiekolom alleen selectievakjes als checkbox=&quot;true&quot;.

**Geforceerde positie**

Met de metagegevens voor geforceerde positie kunt u opgeven waar de kolom in het raster wordt geplaatst: 0 is de eerste plaats en &lt;aantal kolommen>-1 is de laatste positie. Eventuele andere waarden worden genegeerd.

In het eerste voorbeeld is de selectiekolom de eerste kolom met de notatie forcePosition=&quot;0&quot;.

### Query-server {#query-servlet}

Standaard kunt u de Query-server vinden op `/libs/wcm/core/components/bulkeditor/json.java` . U kunt een ander pad configureren om de gegevens op te halen.

Het servlet van de Vraag werkt als volgt: het ontvangt een vraag GQL en de kolommen om terug te keren, verwerkt de resultaten, en verzendt de resultaten terug naar de Redacteur van het Bulk als stroom JSON.

In het de componentengeval van de Lijst van het Product, zijn de twee parameters die naar servlet van de Vraag worden verzonden als volgt:

* query: &quot;path:/content/geometrixx/nl/customer/jcr:content/par/productlist Cube&quot;
* kolommen: &quot;Selection,ProductId,ProductName,Color,CatalogCode,SellingSku&quot;

De JSON-stream wordt als volgt geretourneerd:

```
{
  "hits": [{
      "jcr:path": "/content/geometrixx/en/products/jcr:content/par/productlist/1258674828905",
      "ProductId": "21",
      "ProductName": "Cube",
      "Color": "Blue",
      "CatalogCode": "43244",
      "SellingSku": "32131"
    }
  ],
  "results": 1
}
```

Elke hit komt overeen met één knooppunt en de bijbehorende eigenschappen en wordt weergegeven als een rij in het raster.

U kunt de server van de Vraag uitbreiden om een complex overervingsmodel terug te keren of knopen terug te keren die op een specifieke logische plaats worden opgeslagen. De server van de Vraag kan worden gebruikt om het even welk soort complexe berekening te doen. Het raster kan vervolgens rijen weergeven die een aggregaat zijn van verschillende knooppunten in de repository. De wijziging en het opslaan van deze rijen moeten in dat geval door sparen Servlet worden beheerd.

### Servlet opslaan {#save-servlet}

In de standaardconfiguratie van de Redacteur van het Meerdere is elke rij een knoop en de weg van deze knoop wordt opgeslagen in het rijverslag. De Bulk-editor zorgt ervoor dat de koppeling tussen de rij en het knooppunt door het jcr-pad wordt verbroken. Wanneer een gebruiker het raster bewerkt, wordt een lijst met alle wijzigingen gemaakt. Wanneer een gebruiker **sparen** klikt, wordt een vraag van de POST verzonden naar elke weg met de bijgewerkte eigenschappen waarden. Dit is de basis van het Sling-concept en het werkt goed als elke cel een eigenschap van het knooppunt is. Maar als servlet van de Vraag wordt uitgevoerd om overervingsberekening uit te voeren, kan dit model niet als bezit werken dat door servlet van de Vraag is teruggekeerd kan van een andere knoop worden geërft.

Het serverconcept Opslaan is dat de wijzigingen niet rechtstreeks naar elk knooppunt worden gepost, maar naar één servlet die de opslagtaak uitvoert. Dit geeft servlet de mogelijkheid om de wijzigingen te analyseren en de eigenschappen op de juiste knoop te bewaren.

Elke bijgewerkte eigenschap wordt in de volgende indeling naar de servlet verzonden:

* Parameternaam: &lt;jcr path>/&lt;naam eigenschap>

  Voorbeeld: /content/geometrixx/nl/products/jcr:content/par/productlist/1258674859000/SellingSku

* Waarde: &lt;value>

  Voorbeeld: 12123

servlet moet weten waar het catalogCode bezit wordt opgeslagen.

Een standaard Save servlet implementatie is beschikbaar in /libs/wcm/bulkeditor/save/POST.jsp en wordt gebruikt in de component van de Lijst van het Product. Alle parameters van de aanvraag (met de indeling &lt;jcr path>/&lt;property name>) worden gebruikt en eigenschappen op knooppunten worden geschreven met de JCR API. Er wordt ook een knooppunt gemaakt als deze niet bestaan (raster ingevoegde rijen).

Gebruik de standaardcode niet zo omdat deze bijwerkt wat de server zelf doet (een POST op &lt;jcr path>/&lt;property name>) en daarom slechts een goed uitgangspunt is voor het samenstellen van een Save-servlet die een eigenschapoverervingsmodel kan beheren.
