---
title: xtypes gebruiken (klassieke UI)
description: Meer informatie over alle xtypes die beschikbaar zijn in Adobe Experience Manager
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
exl-id: 06ca4e6d-9ab7-4c5b-905c-07c448632f2b
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '3865'
ht-degree: 0%

---

# xtypes gebruiken (klassieke UI){#using-xtypes-classic-ui}

Deze pagina beschrijft alle xtypes die bij Adobe Experience Manager (AEM) beschikbaar zijn.

In de taal ExtJS, is xtype een symbolische naam die aan een klasse wordt gegeven. U kunt de &quot;Component XTypes&quot;paragraaf van het [ Overzicht van ExtJS 2 ](https://www.sencha.com/learn/overview-of-extjs-2) voor een gedetailleerde verklaring lezen over wat een xtype is en hoe het kan worden gebruikt.

Voor volledige informatie over alle beschikbare widgets in AEM, zie de [ widget API documentatie ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html).

Om te weten te komen waarin de componenten een bepaalde xtype in AEM worden gebruikt, kunt u de volgende vraag Xpath in CRXDE gebruiken door &quot;checkbox&quot;met xtype te vervangen dat u in geinteresseerd bent:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Deze pagina beschrijft het gebruik van ExtJS xtypes binnen klassieke UI.
>
>De Adobe adviseert dat u standaard, modern, [ aanraking-toegelaten UI ](/help/sites-developing/touch-ui-concepts.md) gebruikt die op [ Koraal UI ](/help/sites-developing/touch-ui-concepts.md#coral-ui) wordt gebaseerd en [ graniet UI ](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Hieronder ziet u de beschikbare xtypes in Adobe Experience Manager:

* annotatie

  [ CQ.wcm.Annotation ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Annotation)

  Het dialoogvenster is een speciaal venster met een formulier in de hoofdtekst en een knopgroep in de voettekst. Deze wordt gewoonlijk gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* arraystore

  [ CQ.Ext.data.ArrayStore ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayStore)

  Vroeger bekend als &quot;SimpleStore&quot;.

  Kleine helperklasse om het creëren van [ CQ.Ext.data.Store ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) van de gegevens van de Serie gemakkelijker te maken. Een ArrayStore wordt automatisch gevormd met a [ CQ.Ext.data.ArrayReader ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayReader).

* asseteditor

  [ CQ.dam.AssetEditor ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.AssetEditor)

  De Asset Editor die wordt gebruikt in DAM Admin.

* assetreferenceearchdialog

  [ CQ.wcm.AssetReferenceSearchDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.AssetReferenceSearchDialog)

  Het dialoogvenster AssetReferenceSearchDialog is een dialoogvenster dat wordt weergegeven voor het geval een pagina naar elementen of tags verwijst.

* blueprintconfig

  [ CQ.wcm.msm.BlueprintConfig ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig)

  De BluprintConfig biedt een deelvenster om de actieve kopieën van een blauwdruk weer te geven en deze blauwdruk-eigenschappen te bewerken (activering voor synchroniseren en synchroniseren).

* blueprintstatus

  [ CQ.wcm.msm.BlueprintStatus ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus)

  De BluprintStatus biedt een deelvenster voor het weergeven en bewerken van een blauwdruk en de bijbehorende relaties voor actieve kopieën. Het doorbladeren wordt gedaan door a [ CQ.wcm.msm.BlueprintStatus.Tree ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus.Tree), uitgave door a [ CQ.wcm.msm.BlueprintConfig ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig) en a [ CQ.wcm.msm.LiveCopyProperties ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties).

* box

  [ CQ.Ext.BoxComponent ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent)

  De klasse van de basis voor om het even welke [ Component ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component) die als doos moet worden gerangschikt, gebruikend breedte en hoogte.

  BoxComponent biedt automatische aanpassingen van het kadermodel voor grootte en positionering en werkt correct binnen het rendermodel van de Component.

* browsedialoogvenster

  [ CQ.BrowseDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog)

  Met het dialoogvenster BrowseDialog kan de gebruiker door de opslagplaats bladeren om een pad te selecteren. Het wordt typisch gebruikt door a [ BrowseField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField).

* browsefield

  [ CQ.form.BrowseField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField)

  **Afgekeurd: Gebruik [ CQ.form.PathField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField) in plaats daarvan**

* bulkeditor

  [ CQ.wcm.BulkEditor ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor)

  De BulkEditor biedt een zoekmachine en een raster om de zoekresultaten te bewerken.

  De BulkEditor moet in een HTML-formulier worden ingevoegd (vereist voor importfunctionaliteit). Dit werkt perfect met a [ CQ.Dialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* bulkeditorform

  [ CQ.wcm.BulkEditorForm ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditorForm)

  BulkEditorForm verstrekt [ CQ.wcm.BulkEditor ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor) omringd door een vorm van HTML. Dit is de standalone versie van [ CQ.wcm.BulkEditor ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor), de vorm van HTML wordt vereist voor de invoerknoop.

* knop

  [ CQ.ext.Button ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button)

  Simple Button, klasse

* buttongroep

  [ CQ.Ext.ButtonGroup ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ButtonGroup)

  Container voor een groep knoppen.

* diagram

  [ CQ.Ext.chart.Chart ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart)

  Het pakket CQ.Ext.chart biedt de mogelijkheid om gegevens te visualiseren met flash-gebaseerde grafieken. Elke grafiek bindt direct aan een CQ.Ext.data.Store toelatend automatische updates van de grafiek. Om de blik en het gevoel van een grafiek te veranderen, zie [ chartStyle ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) en [ extraStyle ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) config opties.

* selectievakje

  [ CQ.Ext.form.Checkbox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox)

  Veld voor één selectievakje. Kan worden gebruikt als directe vervanging voor traditionele selectievakjes.

* checkbox-groep

  [ CQ.Ext.form.CheckboxGroup ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.CheckboxGroup)

  Een groeperende container voor [ CQ.Ext.form.Checkbox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox) controles.

* klamboe

  [ CQ.form.ClearableComboBox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ClearableComboBox)

  De ClearableComboBox is een niet-bewerkbare keuzelijst met invoervak met een trigger om de waarde ervan te wissen.

* kleurveld

  [ CQ.form.ColorField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorField)

  Het ColorField laat de gebruiker een waarde van de kleurenhexuitdraai of het gebruiken van a [ CQ.Ext.ColorMenu ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorMenu) ingaan.

* kleurlijst

  [ CQ.form.ColorList ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorList)

  Met de ColorList kan de gebruiker een kleur kiezen in een bewerkbare lijst.

* colormenu

  [ CQ.Ext.menu.ColorMenu ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.ColorMenu)

  Een menu dat a [ CQ.Ext.ColorPalette ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette) Component bevat.

* kleurenpalet

  [ CQ.Ext.ColorPalette ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette)

  Eenvoudige kleurenpaletklasse voor het kiezen van kleuren. Het palet kan worden gerenderd naar elke gewenste container.

* combo

  [ CQ.Ext.form.ComboBox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)

  Een combobox-besturingselement met ondersteuning voor automatisch aanvullen, extern laden, pagineren en vele andere functies.

  Een ComboBox werkt op een vergelijkbare manier als een traditioneel HTML &lt;select>-veld. Het verschil is dat om [ valueField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) voor te leggen, moet u a [ hiddenName ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) specificeren om een verborgen input tot stand te brengen.

* component

  [ CQ.ext.Component ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component)

  Basisklasse voor alle Ext-componenten. Alle subklassen van Component kunnen aan de geautomatiseerde Ext componentenlevenscyclus van verwezenlijking, het teruggeven, en vernietiging deelnemen die door de [ klasse van de Container ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) wordt verstrekt. De componenten kunnen aan een Container door de [ punten ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) worden toegevoegd config optie op het tijdstip dat de Container wordt gecreeerd.

* componentextractor

  [ CQ.wcm.ComponentExtractor ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ComponentExtractor)

  Met ComponentExtractor kan de gebruiker componenten van een website/pagina extraheren.

* componentselector

  [ CQ.form.ComponentSelector ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentSelector)

  Een gegroepeerde, geordende selectie van beschikbare componenten.

* componentstijlen

  [ CQ.form.ComponentStyles ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentStyles)

* compositefeld

  [ CQ.form.CompositeField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)

  Basisklasse voor op deelvensters gebaseerde, complexe formuliervelden die één formulierveld of een groep formuliervelden bevatten.

* container

  [ CQ.Ext.Container ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)

  De klasse van de basis voor om het even welk [ CQ.Ext.BoxComponent ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent) die andere Componenten kan bevatten. Containers verwerken het basisgedrag van het bevatten van items, namelijk items toevoegen, invoegen en verwijderen.

  De meest algemeen gebruikte klassen van de Container zijn [ CQ.Ext.Panel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel), [ CQ.Ext.Window ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window), en [ CQ.Ext.TabPanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel).

* contentfinder

  [ CQ.wcm.ContentFinder ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder)

  ContentFinder is een gespecialiseerde twee-kolom [ Viewport ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport) die de daadwerkelijke Vinder van de Inhoud op de linkerzijde en het Kader van de Inhoud op het recht bevat.

* contentfindertab

  [ CQ.wcm.ContentFinderTab ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinderTab)

  ContentFinderTab is een gespecialiseerd paneel dat eigenschappen verstrekt die in de lusjepanelen van [ worden gebruikt CQ.wcm.ContentFinder ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder). Doorgaans bevat het een zoekformulier - het vak Query - en een gegevensweergave om de zoekopdracht weer te geven.

* cq.workflow.model.combo

  [ CQ.wcm.WorkflowModelCombo ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelCombo)

  WorkflowModelCombo is een aangepaste [ CQ.Ext.form.ComboBox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) die een lijst van beschikbare werkschemamodellen toont.

* cq.workflow.model.selector

  [ CQ.wcm.WorkflowModelSelector ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelSelector)

  De WorkflowModelSelector combineert een WorkflowModelCombo met een duimnagelbeeld van het werkschema, en knopen om werkschemamodellen tot stand te brengen en uit te geven.

* createsitewizard

  [ CQ.wcm.CreateSiteWizard ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateSiteWizard)

  De CreateSiteWizard is een geleidelijke tovenaar om (MSM) plaatsen tot stand te brengen.

* createversionaloogvenster

  [ CQ.wcm.CreateVersionDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateVersionDialog)

  Het dialoogvenster CreateVersionDialog is een dialoogvenster waarin een versie van een pagina kan worden gemaakt.

* customcontentPanel

  [ CQ.CustomContentPanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.CustomContentPanel)

  CustomContentPanel is een speciaal paneel voor gebruik in [ CQ.Dialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog): Zijn inhoud wordt teruggewonnen van en voorgelegd aan een verschillende URL dan de andere gebieden in de dialoog.

* cyclus

  [ CQ.Ext.CycleButton ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)

  Een gespecialiseerde SplitButton die een menu van [ CQ.Ext.menu.CheckItem ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem) elementen bevat. De knoop cycli automatisch door elk menupunt op klik, die de 1} gebeurtenis van de verandering van de knoop [ opheffen {of de 2} changeHandler ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton) functie van de knoop roepen {, indien verstrekt) voor het actieve menupunt.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)[

* gegevensweergave

  [ CQ.Ext.DataView ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView)

  Een mechanisme voor het weergeven van gegevens met behulp van aangepaste lay-outsjablonen en opmaak. DataView gebruikt een [ CQ.Ext.XTemplate ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.XTemplate) als zijn intern het malplaatjemechanisme, en gebonden aan [ CQ.Ext.data.Store ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) zodat aangezien de gegevens in de opslag veranderen de mening automatisch wordt bijgewerkt om op de veranderingen te wijzen.

* datefield

  [ CQ.Ext.form.DateField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField)

  Verstrekt een gebied van de datuminput van a [ CQ.Ext.DatePicker ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker) dropdown en automatische datumbevestiging.

* datemenu

  [ CQ.Ext.menu.DateMenu ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)

  Een menu dat een {](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker) Component 0} CQ.Ext.DatePicker bevat.[

* datepicker

  [ CQ.Ext.DatePicker ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker)

  Een kiezer voor de pop-updatum. Deze klasse wordt gebruikt door de [ ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) klasse DateField om het doorbladeren en de selectie van geldige data toe te staan.

* datetime

  [ CQ.form.DateTime ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DateTime)

  DateTime laat de gebruiker een datum en een tijd ingaan door [ CQ.Ext.form.DateField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) en [ CQ.Ext.form.TimeField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField) te combineren.

* dialoogvenster

  [ CQ.Dialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog)

  Het dialoogvenster is een speciaal venster met een formulier in de hoofdtekst en een knopgroep in de voettekst. Deze wordt gewoonlijk gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* dialogfieldset

  [ CQ.form.DialogFieldSet ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DialogFieldSet)

  DialogFieldSet is a [ FieldSet ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet) voor gebruik in [ Dialogi ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* directstore

  [ CQ.Ext.data.DirectStore ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectStore)

  Kleine helperklasse om tot een [ CQ.Ext.data.Store ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) te leiden die met [ CQ.Ext.data.DirectProxy ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectProxy) en [ CQ.Ext.data.JsonReader ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader) wordt gevormd om interactie met een [ CQ.Ext.Direct ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Direct) Server-kant [ gemakkelijker te maken ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.direct.Provider).

* displayfield

  [ CQ.Ext.form.DisplayField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DisplayField)

  Een alleen-weergeven tekstveld dat niet is gevalideerd en niet is verzonden.

* bewerkbalk

  [ CQ.wcm.EditBar ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBar)

  De EditBar laat de gebruiker inhoud uitgeven gebruikend knopen op een bar.

  Hoewel hier niet vermeld, heeft EditBar alle leden van [ CQ.wcm.EditBase ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBase).

* editor

  [ CQ.ext.Editor ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Editor)

  Een veld voor een basiseditor dat het weergeven/verbergen op aanvraag afhandelt en beschikt over ingebouwde logica voor grootte en gebeurtenisafhandeling.

* editorgrid

  [ CQ.Ext.grid.EditorGridPanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)

  Deze klasse breidt de [ Klasse GridPanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) uit om cel het uitgeven op geselecteerde [ kolommen ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column) te verstrekken. De editable kolommen worden gespecificeerd door een [ redacteur ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) in de [ kolomconfiguratie ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column) te verstrekken.

* editrollover

  [ CQ.wcm.EditRollover ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditRollover)

  Met de EditRollover kan de gebruiker inhoud bewerken door te dubbelklikken en worden meer bewerkhandelingen uitgevoerd via een contextmenu. Het bewerkbare gebied wordt aangegeven met een kader wanneer de muis over de inhoud beweegt.

* feedimporter

  [ CQ.wcm.FeedImporter ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FeedImporter)

  Met FeedImporter kan de gebruiker RSS- of Atom-feeds importeren en pagina&#39;s maken voor elke feed-invoer.

* field

  [ CQ.Ext.form.Field ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Field)

  Basisklasse voor formuliervelden met standaardfuncties voor gebeurtenisafhandeling, -grootte, -afhandeling en andere functies.

* veldset

  [ CQ.Ext.form.FieldSet ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet)

  De standaard container die voor het groeperen van punten binnen a [ wordt gebruikt vorm ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FormPanel).

* fileuploaddialogon

  [ CQ.form.FileUploadDialogButton ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadDialogButton)

  Met FileUploadDialogButton wordt een knop gemaakt waarmee een nieuw dialoogvenster wordt geopend voor het uploaden van een bestand via FileUploadField. Kan worden gebruikt in bewerkingsdialoogvensters waar het uploaden in een afzonderlijk formulier moet plaatsvinden.

* fileuploadveld

  [ CQ.form.FileUploadField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadField)

  Met FileUploadField kan de gebruiker één bestand selecteren dat moet worden geüpload.

* findreplacedialog

  [ CQ.wcm.FindReplaceDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FindReplaceDialog)

  De FindReplaceDialog is een dialoog voor het vinden en het vervangen van tekenen in een pagina en zijn kindpagina&#39;s.

* flash

  [ CQ.Ext.FlashComponent ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.FlashComponent)

* raster

  [ CQ.Ext.grid.GridPanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)

  Deze klasse vertegenwoordigt de primaire interface van een op component-gebaseerd netcontrole om gegevens in een tabelvorm formaat van rijen en kolommen te vertegenwoordigen.

* groupingstore

  [ CQ.Ext.data.GroupingStore ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)

  Een gespecialiseerde opslagimplementatie die het groeperen van verslagen door één van de beschikbare gebieden voorziet. Dit wordt gebruikt met [ CQ.Ext.grid.GroupingView ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GroupingView) om het gegevensmodel voor een gegroepeerde GridPanel te bewijzen.

* hevige dialoog

  [ CQ.wcm.HeavyMoveDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.HeavyMoveDialog)

  Het dialoogvenster HeavyMoveDialog is een dialoogvenster voor het verplaatsen van een pagina en de onderliggende pagina&#39;s, waarin ook wordt overwogen eerder geactiveerde pagina&#39;s opnieuw te activeren (&#39;zware&#39; verplaatsing).

* verborgen

  [ CQ.Ext.form.Hidden ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Hidden)

  Een verborgen basisveld voor het opslaan van verborgen waarden in formulieren die moeten worden doorgegeven aan het verzenden van het formulier.

* historieknop

  [ CQ.HistoryButton ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.HistoryButton)

  HistoryButton is een kleine hulpklasse om rug en voorwaarts knopen gemakkelijk te verstrekken. Meestal zijn twee verwante instanties vereist: de voorwaartse knopinstantie is een eenvoudige knop die is gekoppeld aan de achtergrondknopinstantie die de geschiedenis afhandelt.

* htmleditor

  [ CQ.Ext.form.HtmlEditor ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)

  Biedt een lichte HTML Editor-component. Sommige werkbalkfuncties worden niet ondersteund door Safari en worden automatisch verborgen wanneer dat nodig is. Deze worden genoteerd in de config opties waar aangewezen.

  De de toolbarknopen van de redacteur hebben tooltips die in het [ worden bepaald buttonTips ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor) bezit.

* iframedialoog

  [ CQ.IframeDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframeDialog)

  Een dialoogvenster zonder opmaak waarin de inhoud van een iframe wordt weergegeven en waarin formulieren in iframes kunnen worden geplaatst.

* iframePanel

  [ CQ.IframePanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframePanel)

  Een deelvenster met een iframe. Hiermee kunt u gemakkelijk iframes maken, een gebeurtenis voor het laden van iframes maken en de inhoud van iframe eenvoudig openen.

* inlinetextfield

  [ CQ.form.InlineTextField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.InlineTextField)

  InlineField is een tekstveld dat als label wordt weergegeven wanneer de focus niet is gericht.

* jsonstore

  [ CQ.Ext.data.JsonStore ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonStore)

  Kleine helperklasse om het creëren van [ CQ.Ext.data.Store ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) van gegevens te maken JSON gemakkelijker. Een JsonStore wordt automatisch gevormd met a [ CQ.Ext.data.JsonReader ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader).

* label

  [ CQ.Ext.form.Label ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Label)

  Veld Standaardlabel.

* taalcopydialog

  [ CQ.wcm.LanguageCopyDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LanguageCopyDialog)

  De LanguageCopyDialog is een dialoogvenster voor het kopiëren van taalbomen.

* koppelingencontrole

  [ CQ.wcm.LinkChecker ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LinkChecker)

  De LinkChecker is een hulpmiddel om externe verbindingen in een plaats te controleren.

* listview

  [ CQ.Ext.list.ListView ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView)

  CQ.Ext.list.ListView is een snelle en licht-gewichtimplementatie van a [ Net-als ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) mening.

* livecopyeigenschappen

  [ CQ.wcm.msm.LiveCopyProperties ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties)

  LiveCopyProperties biedt een deelvenster voor het weergeven en bewerken van de eigenschappen van Live Copy (relatieovererving, synchronisatietrigger en synchronisatiehandelingen).

* lvbooleancolumn

  [ CQ.Ext.list.BooleanColumn ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.BooleanColumn)

  Een kolomdefinitieklasse die Booleaanse gegevensvelden rendert. Zie [ xtype ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) config optie van [ CQ.Ext.list.Column ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) voor meer details.

* lvcolumn

  [ CQ.Ext.list.Column ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)

  Deze klasse kapselt kolomconfiguratiegegevens in die in initialisatie van a [ moeten worden gebruikt ListView ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView).

* lvdatecolumn

  [ CQ.Ext.list.DateColumn ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn)

  Een de definitieklasse van de Kolom die een overgegaan datum volgens de standaardscène, of a gevormde [ formaat ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn) teruggeeft. Zie [ xtype ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) config optie van [ CQ.Ext.list.Column ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) voor meer details.

* lvnumbercolumn

  [ CQ.Ext.list.NumberColumn ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)

  Een de definitieklasse van de Kolom die een numeriek gegevensgebied volgens a [ formaat ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn) koord teruggeeft. Zie [ xtype ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) config optie van [ CQ.Ext.list.Column ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) voor meer details.

* mediabrowsedialoog

  [ CQ.MediaBrowseDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.MediaBrowseDialog)

  **Afgekeurd: Gebruik [ de Vinder van de Inhoud ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder) om media in plaats daarvan te doorbladeren.**

  MediaBrowseDialog is een dialoog voor het doorbladeren van de media bibliotheek.

* menu

  [ CQ.Ext.menu.Menu ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Menu)

  Een menuobject. Dit is de container waaraan u menu-items kunt toevoegen. Het menu kan ook als basisklasse dienen wanneer u een gespecialiseerd die menu van een andere component (zoals [ CQ.Ext.menu.DateMenu ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu) bijvoorbeeld) wordt gebaseerd.

  De menu&#39;s kunnen of [ menupunten ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item), of algemene [ Component ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component) s bevatten.

* menubaseitem

  [ CQ.Ext.menu.BaseItem ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem)

  De basisklasse voor alle items die in menu&#39;s worden gerenderd. BaseItem verstrekt gebrek die, geactiveerd staatsbeheer, en de opties van de basisconfiguratie teruggeeft door alle menucomponenten worden gedeeld.

* menuCheckitem

  [ CQ.Ext.menu.CheckItem ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)

  Hiermee wordt een menu-item toegevoegd dat standaard een selectievakje bevat, maar dat ook deel kan uitmaken van een groep keuzerondjes.

* menuitem

  [ CQ.Ext.menu.Item ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item)

  Een basisklasse voor alle menu-items die menu-gerelateerde functionaliteit vereisen (zoals submenu&#39;s) en die geen statische weergave-items zijn. Het punt breidt de basisfunctionaliteit van [ CQ.Ext.menu.BaseItem ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem) door menu-specifieke activering toe te voegen en behandeling te klikken uit.

* menuseparator

  [ CQ.Ext.menu.Separator ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Separator)

  Voegt een scheidingsbalk toe aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Over het algemeen, voegt u één van deze toe door &quot;-&quot;te gebruiken in u roept om toe te voegen () of in uw punten config eerder dan direct tot stand te brengen.

* menuTextem

  [ CQ.Ext.menu.TextItem ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.TextItem)

  Voegt een statische teksttekenreeks toe aan een menu dat wordt gebruikt als een kop- of groepsscheidingsteken.

* metagegevens

  [ CQ.dam.form.Metadata ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.form.Metadata)

  Metagegevens bevatten een set velden waarmee de informatie wordt bepaald die nodig is voor een metagegevensveld, zoals bijvoorbeeld wordt gebruikt op pagina&#39;s in de Editor van middelen.

  Deze biedt de volgende velden:

* multifield

  [ CQ.form.MultiField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)

  Het MultiField is een bewerkbare lijst met formuliervelden voor het bewerken van eigenschappen met meerdere waarden.

* mvt

  [ CQ.form.MVT ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MVT)

  Met de Multivariate Testing-component kunt u een set afbeeldingen definiëren en bewerken die als wisselende banners worden weergegeven. Klik door tariefstatistieken worden verzameld per banner.

* kennisgevingsvak

  [ CQ.wcm.NotificationInbox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.NotificationInbox)

  Met NotificationInbox kan de gebruiker zich abonneren op WCM-handelingen en meldingen beheren.

* nummerveld

  [ CQ.Ext.form.NumberField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.NumberField)

  Numeriek tekstveld dat automatische toetsaanslag en numerieke validatie biedt.

* offlineimporteur

  [ CQ.wcm.OfflineImporter ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.OfflineImporter)

  De OfflineImporter is een programma voor het importeren en converteren van Microsoft® Word-documenten naar AEM pagina&#39;s. Met deze functie kan inhoud offline worden bewerkt met een tekstverwerker.

* eigenaarschap

  [ CQ.form.OwnerDraw ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.OwnerDraw)

  De OwnerDraw kan aangepaste HTML-code bevatten (die rechtstreeks wordt ingevoerd of wordt opgehaald via een URL).

* pagineren

  [ CQ.Ext.PagingToolbar ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.PagingToolbar)

  Naarmate het aantal records toeneemt, neemt de tijd die de browser nodig heeft om deze weer te geven toe. Met paginering wordt de hoeveelheid gegevens die met de klant wordt uitgewisseld, verminderd.

* deelvenster

  [ CQ.ext.Panel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel)

  Panel is een container die specifieke functionaliteit en structurele componenten heeft die van het de perfecte bouwsteen voor toepassing-georiënteerde gebruikersinterfaces maken.

  De panelen zijn, door hun overerving van [ CQ.Ext.Container ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container).

* paragraphreference

  [ CQ.form.ParagraphReference ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ParagraphReference)

  In het veld Alineasereferentie kunt u door pagina&#39;s bladeren en een van de alinea&#39;s selecteren. Het bestaat uit een triggerveld en een gekoppeld alineascherm.

* password

  [ CQ.form.Password ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Password)

  Het wachtwoord is als a [ CQ.Ext.form.TextField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField) maar houdt zijn waarde privé, toestaand gebruikers om gevoelige gegevens in te gaan.

* padvoltooiing

  [ CQ.form.PathCompletion ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathCompletion)

  **Afgekeurd: Gebruik [ CQ.form.PathField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField) in plaats daarvan**

* padveld

  [ CQ.form.PathField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField)

  PathField is een inputgebied dat voor wegen met wegvoltooiing en een knoop wordt ontworpen om a [ CQ.BrowseDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog) te openen voor het doorbladeren van de serverbewaarplaats. U kunt ook door alinea&#39;s bladeren om geavanceerde koppelingen te genereren.

* vordering

  [ CQ.Ext.ProgressBar ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)

  Een bij te werken voortgangsbalkcomponent. De voortgangsbalk ondersteunt twee verschillende modi: handmatig en automatisch.

  Op handwijze, bent u verantwoordelijk voor het tonen, het bijwerken (via [ updateProgress ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)) en het ontruimen van de vooruitgangsbar zoals nodig van uw eigen code. Deze methode is vooral geschikt wanneer u de voortgang wilt weergeven.

* eigenschappenraster

  [ CQ.Ext.grid.PropertyGrid ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyGrid)

  Een gespecialiseerde netimplementatie bedoeld om het traditionele bezitsnet zoals typisch gezien in ontwikkeling IDEs na te bootsen. Elke rij in het net vertegenwoordigt een bezit van één of ander voorwerp, en het gegeven wordt opgeslagen als reeks naam/waardeparen in ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyRecord) CQ.Ext.grid.PropertyRecord.[

* propraster

  [ CQ.PropertyGrid ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.PropertyGrid)

  PropertyGrid is een algemeen raster dat wordt gebruikt voor het weergeven en bewerken van eigenschappen van objecten.

* quicktip

  [ CQ.Ext.QuickTip ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip)

  @xtype quicktip A gespecialiseerde tooltip klasse voor tooltips die in prijsverhoging kunnen worden gespecificeerd en automatisch door de globale {](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTips) instantie 0} CQ.Ext.QuickTips worden geleid. [ Zie de QuickTips-klasseheader voor meer gebruiksdetails en voorbeelden.

* radio

  [ CQ.Ext.form.Radio ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio)

  Veld voor één radio. Hetzelfde als Selectievakje, maar als handig hulpmiddel om het invoertype automatisch in te stellen. De groep keuzerondjes wordt automatisch door de browser afgehandeld als u elke radio in een groep dezelfde naam geeft.

* radiogroep

  [ CQ.Ext.form.RadioGroup ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.RadioGroup)

  Een groeperingscontainer voor [ CQ.Ext.form.Radio ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio) controles.

* dialoogvenster verwijzingen

  [ CQ.wcm.ReferencesDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ReferencesDialog)

  Het dialoogvenster ReferencesDialog is een dialoogvenster waarin verwijzingen op een pagina worden weergegeven.

* restauretreedialoog

  [ CQ.wcm.RestoreTreeDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreTreeDialog)

  Het dialoogvenster RestoreTreeDialog is een dialoogvenster voor het herstellen van een vorige versie van een boomstructuur.

* terugzetdialoog

  [ CQ.wcm.RestoreVersionDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreVersionDialog)

  Het dialoogvenster TerugzetversieDialog is een dialoogvenster voor het terugzetten van een vorige versie van een pagina.

* richtext

  [ CQ.form.RichText ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText)

  RichText verstrekt een vormgebied voor het uitgeven van gestileerde tekstinformatie (rijke teksten).

  De component RichText biedt momenteel de volgende functies:

* rolloutplan

  [ CQ.wcm.msm.RolloutPlan ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan)

  Het rolloutPlan verstrekt een dialoog om de vooruitgang van de paginaloprijving te bekijken. RolloutPlan is begonnen door a [ CQ.wcm.msm.RolloutWizard ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard).

* rollout, wizard

  [ CQ.wcm.msm.RolloutWizard ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard)

  De tovenaar RolloutWizard verstrekt een tovenaar voor het opstellen van een pagina. RolloutWizard begint a [ CQ.wcm.msm.RolloutPlan ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan).

* zoekveld

  [ CQ.form.SearchField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SearchField)

  Het SearchField verstrekt een onderzoeksgebied dat de resultaten in een drop-down lijst verstrekt die voor het zoeken van de bewaarplaats kan worden gebruikt.

* selectie

  [ CQ.form.Selection ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection)

  Met de selectie kan de gebruiker kiezen uit verschillende opties. De opties kunnen onderdeel zijn van de configuratie of worden geladen vanuit een JSON-reactie. De selectie kan worden weergegeven als vervolgkeuzelijst (selecteren) of als een keuzelijst met invoervak (selecteren plus item met vrije tekst).

* sidekick

  [ CQ.wcm.Sidekick ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Sidekick)

  De Sidekick is een zwevende hulp die de gebruiker algemene gereedschappen biedt voor paginabewerking.

* sitebeheerder

  [ CQ.wcm.SiteAdmin ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteAdmin)

  SiteAdmin is een console die WCM beleidsfuncties verstrekt.

* importeur van sites

  [ CQ.wcm.SiteImporter ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteImporter)

  De SiteImporter laat de gebruiker volledige websites invoeren en aanvankelijke projecten tot stand brengen.

* sizefield

  [ CQ.form.SizeField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SizeField)

  Met SizeField kan de gebruiker de breedte en hoogte invoeren (bijvoorbeeld voor een afbeelding).

* schuifregelaar

  [ CQ.Ext.Slider ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Slider)

  Schuifregelaar die ondersteuning biedt voor verticale of horizontale oriëntatie, toetsenbordaanpassingen, configureerbare magnetisch uitlijnen, asklikken en animatie. Kan als een item aan elke container worden toegevoegd. Voorbeeld: ...

* presentatie

  [ CQ.form.Slideshow ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Slideshow)

  De diapresentatie bevat een component die kan worden gebruikt om een set afbeeldingen en afbeeldingstitels te definiëren en te bewerken die als een diapresentatie kunnen worden weergegeven.

  De component Slideshow is gebaseerd op de {](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage) component 0} CQ.form.SmartImage.[

* smartfile

  [ CQ.form.SmartFile ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartFile)

  Het SmartFile-bestand is een intelligente uploader voor bestanden.

  Als een Flash-insteekmodule (versie >= 9) is geïnstalleerd, worden uploads uitgevoerd met behulp van de SWF-uploadbibliotheek die een handige manier biedt om uploads af te handelen.

* slimtimage

  [ CQ.form.SmartImage ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage)

  De SmartImage is een intelligente uploader voor afbeeldingen. Het biedt gereedschappen voor het verwerken van een geüploade afbeelding, bijvoorbeeld een gereedschap voor het definiëren van afbeeldingen met hyperlinks en een functie voor het uitsnijden van afbeeldingen.

  De component is ontworpen voor gebruik op een afzonderlijk dialoogtabblad.

* spacer

  [ CQ.ext.Spacer ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Spacer)

  Wordt gebruikt om een grote ruimte in een lay-out te bieden.

* spinner

  [ CQ.form.Spinner ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Spinner)

  De spinner is een triggerveld voor numerieke, datum- of tijdwaarden. De waarde kan worden verhoogd en verlaagd met de beschikbare triggers omhoog en omlaag, het schuifwiel of de toetsen.

* splitknop

  [ CQ.Ext.SplitButton ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.SplitButton)

  Een gesplitste knop met een ingebouwde vervolgkeuzepijl die een gebeurtenis afzonderlijk van de standaardklikgebeurtenis van de knop kan starten. Dit wordt doorgaans gebruikt om een vervolgkeuzemenu weer te geven dat aanvullende opties biedt voor de primaire knopactie, maar elke aangepaste handler kan de arrowclick-implementatie leveren.

* static

  [ CQ.Static ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Static)

  Static kan worden gebruikt om willekeurige tekst of HTML weer te geven.

* statistieken

  [ CQ.wcm.Statistics ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Statistics)

  De Statistieken tonen de paginamonpressies als grafiek. Met de widget kunt u een periode selecteren waarvoor de statistieken moeten worden weergegeven.

* winkel

  [ CQ.Ext.data.Store ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)

  De klasse van de Opslag kapselt een cliënt-zijgeheime voorgeheugen van [ Verslag ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Record) voorwerpen in die inputgegevens voor Componenten zoals [ GridPanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), [ ComboBox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox), of [ DataView ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView) verstrekken.

* suggestfield

  [ CQ.form.SuggestField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SuggestField)

  Het SuggestField verstrekt de gebruiker van suggesties die op hun ingang worden gebaseerd.

* schakelaar

  [ CQ.Switcher ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Switcher)

  De Schakelaar verstrekt een knoopgroep voor de kopbalbar in een console om tussen Websites, Digitale Assets, Hulpmiddelen, Workflow, en Veiligheid te schakelen.

* tableedit

  [ CQ.form.TableEdit ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit)

  **Afgekeurd: Gebruik [ CQ.form.TableEdit2 ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2) in plaats daarvan.**

* tableedit2

  [ CQ.form.TableEdit2 ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2)

  TableEdit2 verstrekt een widget voor het creëren van lijsten.

* tabbladen

  [ CQ.Ext.TabPanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel)

  Een eenvoudige tabcontainer. TabPanels kunnen precies als standaard [ CQ.Ext.Panel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel) voor lay-outdoeleinden worden gebruikt, maar hebben ook speciale steun voor het bevatten van kindComponenten ([`items` ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)).

* tags

  [ CQ.tagging.TagInputField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tagging.TagInputField)

  ```
  CQ.tagging.TagInputField
  ```

  is een formulierwidget voor het invoeren van codes. Deze bevat een pop-upmenu waarin u een keuze kunt maken uit bestaande tags, waaronder automatisch aanvullen en een groot aantal andere functies.

* textarea

  [ CQ.Ext.form.TextArea ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea)

  Tekstveld met meerdere regels. Kan worden gebruikt als directe vervanging voor traditionele tekstgebieden, plus steun voor auto-resizing.

* textbutton

  [ CQ.TextButton ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.TextButton)

  TextButton verstrekt een tekstverbinding met de mogelijkheden van a [ CQ.Ext.Button ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button).

* textfield

  [ CQ.Ext.form.TextField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)

  Basistekstveld. Kan als directe vervanging voor traditionele tekstinput worden gebruikt, of als basisklasse voor verfijnde inputcontroles (als [ CQ.Ext.form.TextArea ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea) en [ CQ.Ext.form.ComboBox ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)).

* miniatuur

  [ CQ.form.Thumbnail ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Thumbnail)

* tijdveld

  [ CQ.Ext.form.TimeField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField)

  Biedt een invoerveld voor de tijd met een vervolgkeuzelijst en automatische tijdvalidatie. Voorbeeld: ...

* tip

  [ CQ.ext.Tip ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tip)

  @xtype uiteinde Dit is de basisklasse voor [ CQ.Ext.QuickTip ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip) en [ CQ.Ext.Tooltip ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tooltip) die de basislay-out en het plaatsen verstrekt die alle op uiteinde-gebaseerde klassen vereisen. Deze klasse kan direct voor eenvoudige, statisch gepositioneerde uiteinden worden gebruikt.

* titleseparator

  [ CQ.menu.TitleSeparator ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.menu.TitleSeparator)

  Voegt een scheidingsbalk toe aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Het scheidingsteken kan ook een titel bevatten.

* werkbalk

  [ CQ.ext.Toolbar ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Toolbar)

  Basisklasse van de werkbalk. Hoewel [`defaultType` ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) voor Toolbar [`button` ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button) is, kunnen de elementen van de Toolbar (kindpunten voor de Toolbar container) vrijwel om het even welk type van Component zijn. Werkbalkelementen kunnen expliciet worden gemaakt via hun constructors.

* knopinfo

  [ CQ.Ext.ToolTip ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ToolTip)

  Een standaard tooltip implementatie voor het verstrekken van extra informatie wanneer het hangen over een doelelement. @xtype tooltip.

* treuzelen

  [ CQ.tree.TreeGrid ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tree.TreeGrid)

  @xtype treegrid

* treepanel

  [ CQ.Ext.tree.TreePanel ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)

  TreePanel verstrekt boom-gestructureerde vertegenwoordiging UI van boom-gestructureerde gegevens.

  [ TreeNode ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode) wordt toegevoegd aan TreePanel kan meta-gegevens bevatten die door uw toepassing in hun [ worden gebruikt attributen ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode) bezit.

* trigger

  [ CQ.Ext.form.TriggerField ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)

  Verstrekt een geschikte omslag voor TextFields die een klikbare trekkerknoop toevoegt (kijkt als een combobox door gebrek). De trekker heeft geen standaardactie, zodat moet u een functie toewijzen om de trekker uit te voeren klikt manager door [ onTriggerClick ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField) met voeten te treden. U kunt een TriggerField direct tot stand brengen, aangezien het precies als een combobox teruggeeft.

* uploadditioneel

  [ CQ.UploadDialog ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UploadDialog)

  Met het dialoogvenster UploadDialog kan de gebruiker bestanden uploaden naar de opslagplaats. Hiermee wordt een nieuw dialoogvenster UploadDialog gemaakt.

* userinfo

  [ CQ.UserInfo ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UserInfo)

  Werkbalkitem om de huidige gebruikersnaam weer te geven en gebruikersacties zoals het bewerken van gebruikerseigenschappen en imitatie toe te staan.

* viewport

  [ CQ.Ext.Viewport ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport)

  Een gespecialiseerde container die het zichtbare toepassingsgebied vertegenwoordigt (viewport van browser).

  De Viewport geeft zichzelf aan het documentlichaam terug, en past zich automatisch aan de grootte van browser viewport aan en beheert venster resizing. Er kan slechts één Viewport zijn gemaakt.

* venster

  [ CQ.ext.Window ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)

  Een speciaal deelvenster dat is bedoeld voor gebruik als toepassingsvenster. De vensters worden gedreven, [ resizable ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window), en [ draggable ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) door gebrek. De vensters kunnen [ worden gemaximaliseerd ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) om viewport te vullen, aan hun vroegere grootte wordt hersteld, en kunnen [ worden geminimaliseerd ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) d.

* xmlstore

  [ CQ.Ext.data.XmlStore ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlStore)

  Kleine helperklasse om het creëren van [ CQ.Ext.data.Store ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) van de gegevens van XML gemakkelijker te maken. Een XmlStore wordt automatisch gevormd met a [ CQ.Ext.data.XmlReader ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlReader).

  **cqinclude** Pseudo xtype dat widgetdefinities van een verschillende weg in de bewaarplaats omvat. Deze wordt meestal gebruikt in paginadialoogvensters. Er is geen werkelijke JavaScript-widget-klasse voor dit xtype. Het wordt verwerkt door de formatData() functie van de CQ.Util klasse. Zie dit kennisbankartikel voor meer informatie.
