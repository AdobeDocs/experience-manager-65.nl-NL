---
title: De Bulk-editor ontwikkelen
seo-title: De Bulk-editor ontwikkelen
description: Door tags toe te wijzen, kan inhoud worden gecategoriseerd en ingedeeld
seo-description: Door tags toe te wijzen, kan inhoud worden gecategoriseerd en ingedeeld
uuid: 3cd04c52-5bdb-47f6-9fa3-d7a4937e8e20
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: e9a1ff95-e88e-41f0-9731-9a59159b4653
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# De Bulk-editor ontwikkelen{#developing-the-bulk-editor}

Deze sectie beschrijft hoe te om het bulkredacteurshulpmiddel te ontwikkelen en hoe te om de component van de Lijst van het Product uit te breiden, die op de bulkredacteur gebaseerd is.

## Query-parameters voor de bulkeditor {#bulk-editor-query-parameters}

Wanneer het werken met de bulkredacteur, zijn er verscheidene vraagparameters die u aan URL kunt toevoegen om de bulkredacteur met een specifieke configuratie te roepen. Als u de bulkredacteur altijd met een bepaalde configuratie wilt worden gebruikt, bijvoorbeeld, zoals in de component van de Lijst van het Product, dan moet u bulkeditor.jsp (die in /libs/wcm/core/components/bulkeditor wordt gevestigd) wijzigen of een component met de specifieke configuratie tot stand brengen. Wijzigingen die zijn aangebracht met behulp van queryparameters zijn niet permanent.

Als u bijvoorbeeld het volgende in de URL van uw browser typt:

`https://<servername><port_number>/etc/importers/bulkeditor.html?rootPath=/content/geometrixx/en&queryParams=geometrixx&initialSearch=true&hrp=true`

de bulkredacteur toont zonder het gebied van de Weg **van de** Wortel aangezien hrp=true het gebied verbergt. Met de parameter hrp=false wordt het veld weergegeven (de standaardwaarde).

Hier volgt een lijst met de queryparameters voor bulkeditors:

>[!NOTE]
>
>Elke parameter kan een lange en een korte naam hebben. De lange naam voor het hoofdpad van de zoekopdracht is bijvoorbeeld `rootPath`de korte naam `rp`. Als de lange naam niet wordt bepaald, wordt korte gelezen van het verzoek.

<table>
 <tbody>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p> Parameter</p> <p>(lange naam / korte naam)<br /> </p> </td>
   <td> Type <br /> </td>
   <td> Beschrijving <br /> </td>
  </tr>
  <tr>
   <td> rootPath / rp<br /> </td>
   <td> Tekenreeks </td>
   <td> zoekhoofdpad</td>
  </tr>
  <tr>
   <td> queryParams / qp<br /> </td>
   <td> Tekenreeks</td>
   <td> zoekquery</td>
  </tr>
  <tr>
   <td> contentMode / cm<br /> </td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de inhoudsmodus ingeschakeld<br /> </td>
  </tr>
  <tr>
   <td> colsValue / cv<br /> </td>
   <td> Tekenreeks[]</td>
   <td> gezochte eigenschappen (gecontroleerde waarden van colsSelection weergegeven als checkboxes)</td>
  </tr>
  <tr>
   <td> extraCols / ec<br /> </td>
   <td> Tekenreeks[]</td>
   <td> extra gezochte eigenschappen (die in een komma-gescheiden tekstgebied worden getoond)</td>
  </tr>
  <tr>
   <td> initialSearch / is<br /> </td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de query uitgevoerd bij het laden van de pagina<br /> </td>
  </tr>
  <tr>
   <td> colsSelection / cs<br /> </td>
   <td> Tekenreeks[]</td>
   <td> selectie van gezochte eigenschappen (weergegeven als selectievakjes)</td>
  </tr>
  <tr>
   <td> showGridOnly / sgo<br /> </td>
   <td> Boolean</td>
   <td> indien waar (true), alleen het raster en niet het deelvenster Zoeken wordt weergegeven <br /> </td>
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
   <td> indien waar (true), wordt de knop Opslaan verborgen</td>
  </tr>
  <tr>
   <td> hideExportButton / hexpb</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de knop Exporteren verborgen</td>
  </tr>
  <tr>
   <td> hideImportButton / hib</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de knop Importeren verborgen</td>
  </tr>
  <tr>
   <td> hideResultNumber / hrn</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de tekst van het rasterzoekresultaat verborgen</td>
  </tr>
  <tr>
   <td> hideInsertButton / hinsertB</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de knop voor het invoegen van het raster verborgen</td>
  </tr>
  <tr>
   <td> hideDeleteButton / hdelb</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de knop voor het verwijderen van het raster verborgen</td>
  </tr>
  <tr>
   <td> hidePathCol / hpc</td>
   <td> Boolean</td>
   <td> indien waar (true), wordt de rasterkolom "pad" verborgen</td>
  </tr>
 </tbody>
</table>

### Een op Bulk Editor gebaseerde component ontwikkelen: de component Productlijst {#developing-a-bulk-editor-based-component-the-product-list-component}

Deze sectie verstrekt een overzicht van hoe te om de bulkredacteur te gebruiken en geeft een beschrijving van de bestaande component Geometrixx die op de bulkredacteur wordt gebaseerd: de component Productlijst.

Met de component Productlijst kunnen gebruikers een tabel met gegevens weergeven en bewerken. U kunt bijvoorbeeld de component Productlijst gebruiken om producten in een catalogus te vertegenwoordigen. De informatie wordt weergegeven in een standaard HTML-tabel en alle bewerkingen worden uitgevoerd in het dialoogvenster **Bewerken** , dat een BulkEditor-widget bevat. (Deze Bulk-editor is precies hetzelfde als de editor die u kunt openen via /etc/importers/bulkeditor.html of via het menu Gereedschappen). De component van de Lijst van het Product is gevormd voor specifieke, beperkte bulkredacteursfunctionaliteit. Elk deel van de bulkredacteur (of componenten die uit de bulkredacteur worden afgeleid) kan worden gevormd.

Met de bulkeditor kunt u de rijen toevoegen, wijzigen, verwijderen, filteren en exporteren, wijzigingen opslaan en een set rijen importeren. Elke rij wordt opgeslagen als een knoop onder de de componenteninstantie van de Lijst van het Product zelf. Elke cel is een eigenschap van elk knooppunt. Dit is een ontwerpkeuze die eenvoudig kan worden gewijzigd. U kunt knooppunten bijvoorbeeld ergens anders in de opslagplaats opslaan. De rol van de vraagserver is de lijst van de knopen terug te keren aan vertoning; het zoekpad wordt gedefinieerd als een instantie van de productlijst.

De broncode van de component Product List is beschikbaar in de gegevensopslagruimte op /apps/geometrixx/components/productlist en bestaat uit verschillende onderdelen, zoals alle AEM-componenten:

* HTML-rendering: wordt de rendering uitgevoerd in een JSP-bestand (/apps/geometrixx/components/productlist/productlist.jsp). JSP leest subnodes van de huidige component van de Lijst van het Product en toont elk van hen als rij van een HTML- lijst.
* Het dialoogvenster Bewerken waarin u de configuratie van de Bulk-editor definieert. Configureer het dialoogvenster zodat dit voldoet aan de behoeften van de component: beschikbare kolommen en mogelijke acties die worden uitgevoerd op het raster of op de zoekopdracht. Zie de eigenschappen [van de de](#bulk-editor-configuration-properties) bulkredaconfiguratie voor informatie over alle configuratieeigenschappen.

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

### Eigenschappen van Bulkeditor {#bulk-editor-configuration-properties}

Elk deel van de bulkredacteur kan worden gevormd. De volgende lijst maakt een lijst van alle configuratieeigenschappen voor de bulkredacteur.

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
   <td>True to enable content mode: eigenschappen worden gelezen op jcr:content node en niet op search result node</td>
  </tr>
  <tr>
   <td>colsValue</td>
   <td>Gezochte eigenschappen (gecontroleerde waarden van colsSelection weergegeven als checkboxes)</td>
  </tr>
  <tr>
   <td>extraCols</td>
   <td>Extra gezochte eigenschappen (weergegeven in een door komma's gescheiden tekstveld)</td>
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
     <li>readOnly: waar (true) om waarde niet te kunnen wijzigen </li>
     <li>selectievakje: true om alle cellen van de kolom als selectievakjes te definiëren (waarden true/false) </li>
     <li>forcePosition: gehele waarde om op te geven waar de kolom in het raster moet worden geplaatst (tussen 0 en het aantal kolommen-1)<p><br /> </p> </li>
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

De bulkredacteur heeft drie kolomconfiguraties:

* CSS-klassenaam van cel (cellCls): een CSS klassennaam die aan elke cel van de gevormde kolom wordt toegevoegd.
* Celstijl (cellStyle): een HTML-stijl die aan elke cel van de geconfigureerde kolom wordt toegevoegd.
* Alleen-lezen (alleen-lezen): read only wordt geplaatst voor elke cel van de gevormde kolom.

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

**Selectievakje**

Als het checkbox configuratiebezit aan waar wordt geplaatst, worden alle cellen van de kolom teruggegeven als checkboxes. Een selectievakje verzendt **true** naar de server Save servlet, anders **false** . In het koptekstmenu kunt u ook alles **** selecteren of niets **** selecteren. Deze opties worden ingeschakeld als de geselecteerde koptekst de koptekst van een kolom in het selectievakje is.

In het eerste voorbeeld bevat de selectiekolom alleen selectievakjes als checkbox=&quot;true&quot;.

**Geforceerde positie**

Met de metagegevens voor geforceerde positie kunt u opgeven waar de kolom in het raster wordt geplaatst: 0 is de eerste plaats en &lt;aantal kolommen>-1 is de laatste positie. Eventuele andere waarden worden genegeerd.

In het eerste voorbeeld is de selectiekolom de eerste kolom als forcePosition=&quot;0&quot;.

### Query-server {#query-servlet}

Standaard is de Query-server te vinden op `/libs/wcm/core/components/bulkeditor/json.java`. U kunt een ander pad configureren om de gegevens op te halen.

De servlet van de Vraag werkt als volgt: het ontvangt een vraag GQL en de kolommen om terug te keren, verwerkt de resultaten, en verzendt de resultaten terug naar de bulkredacteur als stroom JSON.

In het de componentengeval van de Lijst van het Product, zijn de twee parameters die naar servlet van de Vraag worden verzonden als volgt:

*  query: &quot;path:/content/geometrixx/nl/customer/jcr:content/par/productlist Cube&quot;
* kolommen: &quot;Selection,ProductId,ProductName,Color,CatalogCode,SellingSku&quot;

en de geretourneerde JSON-stream is als volgt:

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

In de standaardconfiguratie van de bulkredacteur is elke rij een knoop en de weg van deze knoop wordt opgeslagen in het rijverslag. De bulkredacteur houdt het verband tussen de rij en de knoop door de jcr weg. Wanneer een gebruiker het raster bewerkt, wordt een lijst met alle wijzigingen gemaakt. Wanneer een gebruiker op **Opslaan** klikt, wordt een POST-query verzonden naar elk pad met de bijgewerkte eigenschappen. Dit is de basis van het Sling-concept en het werkt goed als elke cel een eigenschap van het knooppunt is. Maar als servlet van de Vraag wordt uitgevoerd om overervingsberekening uit te voeren, kan dit model niet als bezit werken dat door servlet van de Vraag is teruggekeerd kan van een andere knoop worden geërft.

Het serverconcept Opslaan is dat de wijzigingen niet rechtstreeks naar elk knooppunt worden gepost, maar naar één servlet die de opslagtaak uitvoert. Dit geeft servlet de mogelijkheid om de wijzigingen te analyseren en de eigenschappen op de juiste knoop te bewaren.

Elke bijgewerkte eigenschap wordt in de volgende indeling naar de servlet verzonden:

* Parameternaam: &lt;jcr path>/&lt;property name>

   Voorbeeld: /content/geometrixx/nl/products/jcr:content/par/productlist/1258674859000/SellingSku

* Waarde: &lt;value>

   Voorbeeld: 12123

servlet moet weten waar het catalogCode bezit wordt opgeslagen.

Een standaard Save servlet implementatie is beschikbaar in /libs/wcm/bulkeditor/save/POST.jsp en wordt gebruikt in de component van de Lijst van het Product. Alle parameters van de aanvraag (met de indeling &lt;jcr path>/&lt;property name>) worden gebruikt en eigenschappen op knooppunten worden geschreven met de JCR API. Er wordt ook een knooppunt gemaakt als deze niet bestaan (raster ingevoegde rijen).

De standaardcode zou niet moeten worden gebruikt aangezien het is wat de server native (POST op &lt;jcr weg>/&lt;property name>) uitvoert en daarom slechts een goed uitgangspunt voor de bouw van sparen servlet is die een model van de bezitsovererving zal beheren.
