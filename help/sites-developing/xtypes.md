---
title: xtypes gebruiken (klassieke UI)
seo-title: xtypes gebruiken (klassieke UI)
description: Meer informatie over alle xtypes die beschikbaar zijn in AEM
seo-description: Meer informatie over alle xtypes die beschikbaar zijn in AEM
uuid: 6497caa4-2f9b-4f21-9023-88d485fd1d78
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: adb70b43-1b0b-4302-905a-c7612675dabb
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# xtypes gebruiken (klassieke UI){#using-xtypes-classic-ui}

Op deze pagina worden alle xtypes beschreven die beschikbaar zijn in Adobe Experience Manager (AEM).

In de taal ExtJS, is xtype een symbolische naam die aan een klasse wordt gegeven. U kunt de paragraaf &quot;Component XTypes&quot;van het [Overzicht van ExtJS 2](https://www.sencha.com/learn/overview-of-extjs-2) voor een gedetailleerde verklaring lezen over wat xtype is en hoe het kan worden gebruikt.

Raadpleeg de documentatie bij de [widget-API voor een volledige informatie over alle beschikbare widgets in AEM](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html).

Om te weten te komen waarin de componenten een bepaalde xtype in AEM worden gebruikt, kunt u de volgende vraag van Xpath in CRXDE gebruiken door &quot;checkbox&quot;met xtype te vervangen dat u geinteresseerd bent in:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Deze pagina beschrijft het gebruik van ExtJS xtypes binnen klassieke UI.
>
>Adobe raadt u aan de standaard, moderne [aanraakinterface](/help/sites-developing/touch-ui-concepts.md) te gebruiken op basis van de gebruikersinterface [van](/help/sites-developing/touch-ui-concepts.md#coral-ui) Coral en de gebruikersinterface [van](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components)Granite.

## xtypes {#xtypes}

Hieronder vindt u een lijst met de beschikbare typen in Adobe Experience Manager:

* aantekening

   [CQ.wcm.Annotatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Annotation)

   Het dialoogvenster is een speciaal venster met een formulier in de hoofdtekst en een knopgroep in de voettekst. Deze wordt doorgaans gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* arraystore

   [CQ.Ext.data.ArrayStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayStore)

   Vroeger bekend als &quot;SimpleStore&quot;.

   Kleine hulpklasse om het maken van [CQ.Ext.data.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)Stores van de gegevens van de Serie gemakkelijker te maken. Een ArrayStore wordt automatisch geconfigureerd met een [CQ.Ext.data.ArrayReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayReader).

* asseteditor

   [CQ.dam.AssetEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.AssetEditor)

   De Asset Editor die wordt gebruikt in DAM Admin.

* assetreferenceearchdialog

   [CQ.wcm.AssetReferenceSearchDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.AssetReferenceSearchDialog)

   Het dialoogvenster AssetReferenceSearchDialog is een dialoogvenster dat wordt weergegeven voor het geval een pagina naar elementen of tags verwijst.

* blueprintconfig

   [CQ.wcm.msm.BluprintConfig](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig)

   De BluprintConfig biedt een deelvenster om de actieve kopieën van een blauwdruk weer te geven en deze blauwdruk-eigenschappen te bewerken (activering voor synchroniseren en synchroniseren).

* blueprintstatus

   [CQ.wcm.msm.BluprintStatus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus)

   De BluprintStatus biedt een deelvenster voor het weergeven en bewerken van een blauwdruk en de bijbehorende relaties voor actieve kopieën. Bladeren gebeurt via een [CQ.wcm.msm.BlueprintStatus.Tree](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus.Tree)-editie via een [CQ.wcm.msm.BlueprintConfig](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig) en een [CQ.wcm.msm.LiveCopyProperties](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties).

* box

   [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent)

   Basisklasse voor elke [component](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component) waarvan de grootte als vak moet worden aangepast, met breedte en hoogte.

   BoxComponent biedt automatische aanpassingen van het kadermodel voor grootte en positionering en werkt correct binnen het rendermodel van de Component.

* browsedialoogvenster

   [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog)

   Met het dialoogvenster BrowseDialog kan de gebruiker door de opslagplaats bladeren om een pad te selecteren. Het wordt typisch gebruikt door een [BrowseField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField).

* browsefield

   [CQ.form.BrowseField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField)

   **Vervangen: Gebruik in[plaats hiervan CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField).**

* bulkeditor

   [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor)

   De BulkEditor biedt een zoekmachine en een raster om de zoekresultaten te bewerken.

   De BulkEditor moet in een HTML-formulier worden ingevoegd (vereist voor importfunctionaliteit). Dit werkt perfect met een [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* bulkeditorform

   [CQ.wcm.BulkEditorForm](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditorForm)

   Het BulkEditorForm biedt [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor) , omringd door een HTML-formulier. Dit is de zelfstandige versie van de [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor). HTML-formulier is vereist voor de knop Importeren.

* button

   [CQ.ext.Button](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button)

   Simple Button, klasse

* buttongroep

   [CQ.Ext.ButtonGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ButtonGroup)

   Container voor een groep knoppen.

* diagram

   [CQ.Ext.chart.Chart](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart)

   Het pakket CQ.Ext.chart biedt de mogelijkheid om gegevens te visualiseren met flash-opschriften. Elke grafiek bindt direct aan een CQ.Ext.data.Store toelatend automatische updates van de grafiek. Om de blik en het gevoel van een grafiek te veranderen, zie de [chartStyle](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) en [extraStyle](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) configuratieopties.

*  selectievakje

   [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox)

   Veld voor één selectievakje. Kan worden gebruikt als directe vervanging voor traditionele selectievakjes.

* checkbox-groep

   [CQ.Ext.form.CheckboxGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.CheckboxGroup)

   Een groeperingscontainer voor besturingselementen van [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox) .

* klamboe

   [CQ.form.ClearableComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ClearableComboBox)

   De ClearableComboBox is een niet-bewerkbare keuzelijst met invoervak met een trigger om de waarde ervan te wissen.

* kleurveld

   [CQ.form.ColorField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorField)

   Met het ColorField kan de gebruiker een hexadecimale kleurwaarde rechtstreeks invoeren of een [CQ.Ext.ColorMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorMenu)gebruiken.

* kleurlijst

   [CQ.form.ColorList](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorList)

   Met de ColorList kan de gebruiker een kleur kiezen in een bewerkbare lijst.

* colormenu

   [CQ.Ext.menu.ColorMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.ColorMenu)

   Een menu met een [component CQ.Ext.ColorPalette](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette) .

* kleurenpalet

   [CQ.Ext.ColorPalette](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette)

   Eenvoudige kleurenpaletklasse voor het kiezen van kleuren. Het palet kan worden gerenderd naar elke gewenste container.

* combo

   [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)

   Een combobox-besturingselement met ondersteuning voor automatisch aanvullen, extern laden, pagineren en vele andere functies.

   Een ComboBox werkt op vergelijkbare wijze als een traditioneel HTML &lt;select>-veld. Het verschil is dat als u het [valueField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)wilt verzenden, u een [hiddenName](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) moet opgeven om een verborgen invoer te maken.

* component

   [CQ.ext.Component](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component)

   Basisklasse voor alle Ext-componenten. Alle subklassen van Component kunnen deelnemen aan de automatische levenscyclus van de component Ext van creatie, rendering en vernietiging die wordt voorzien door de [klasse Container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) . De componenten kunnen aan een Container door de [punten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) config optie worden toegevoegd op het tijdstip dat de Container wordt gecreeerd.

* componentextractor

   [CQ.wcm.ComponentExtractor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ComponentExtractor)

   Met ComponentExtractor kan de gebruiker componenten van een website/pagina extraheren.

* componentselector

   [CQ.form.ComponentSelector](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentSelector)

   Een gegroepeerde, geordende selectie van beschikbare componenten.

* componentstijlen

   [CQ.form.ComponentStyles](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentStyles)

* compositefeld

   [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)

   Basisklasse voor op deelvensters gebaseerde, complexe formuliervelden die één formulierveld of een groep formuliervelden bevatten.

* container

   [CQ.ext.container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)

   Basisklasse voor elke [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent) die andere Componenten kan bevatten. Containers verwerken het basisgedrag van het bevatten van items, namelijk items toevoegen, invoegen en verwijderen.

   De meest gebruikte Containerklassen zijn [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel), [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) en [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel).

* contentfinder

   [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder)

   De ContentFinder is een gespecialiseerde [Viewport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport) met twee kolommen, die de daadwerkelijke Inhoudszoeker links en het Inhoudskader rechts bevat.

* contentfindertab

   [CQ.wcm.ContentFinderTab](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinderTab)

   ContentFinderTab is een speciaal deelvenster met functies die worden gebruikt in de tabdeelvensters van de [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder). Doorgaans bevat het een zoekformulier - het vak Query - en een gegevensweergave om de zoekopdracht weer te geven.

* cq.workflow.model.combo

   [CQ.wcm.WorkflowModelCombo](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelCombo)

   WorkflowModelCombo is een aangepaste [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) die een lijst van beschikbare werkschemamodellen toont.

* cq.workflow.model.selector

   [CQ.wcm.WorkflowModelSelector](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelSelector)

   De WorkflowModelSelector combineert een WorkflowModelCombo met een duimnagelbeeld van het werkschema, en knopen om werkschemamodellen tot stand te brengen en uit te geven.

* createsitewizard

   [CQ.wcm.CreateSiteWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateSiteWizard)

   De CreateSiteWizard is een geleidelijke tovenaar om (MSM) plaatsen tot stand te brengen.

* createversionaloogvenster

   [CQ.wcm.CreateVersionDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateVersionDialog)

   Het dialoogvenster CreateVersionDialog is een dialoogvenster waarin een nieuwe versie van een pagina kan worden gemaakt.

* customcontentPanel

   [CQ.CustomContentPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.CustomContentPanel)

   Het deelvenster CustomContentPanel is een speciaal soort deelvenster voor gebruik in [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog): De inhoud wordt opgehaald van en verzonden naar een andere URL dan de andere velden in het dialoogvenster.

* cyclus

   [CQ.Ext.CycleButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)

   Een gespecialiseerde SplitButton die een menu van [elementen CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem) bevat. De knop doorloopt automatisch elk menu-item bij klikken, waarbij de gebeurtenis [change](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton) van de knop (of de functie [changeHandler](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton) van de knop, indien beschikbaar, wordt aangeroepen) voor het actieve menu-item wordt opgevraagd.

* gegevensweergave

   [CQ.Ext.DataView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView)

   Een mechanisme voor het weergeven van gegevens met behulp van aangepaste lay-outsjablonen en opmaak. DataView gebruikt een [CQ.Ext.XTemplate](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.XTemplate) als zijn intern het malplaatjemechanisme, en is gebonden aan een [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) zodat aangezien de gegevens in de opslag veranderen de mening automatisch wordt bijgewerkt om op de veranderingen te wijzen.

* datefield

   [CQ.Ext.form.DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField)

   Verstrekt een gebied van de datuminput van [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker) dropdown en automatische datumbevestiging.

* datemenu

   [CQ.Ext.menu.DateMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)

   Een menu met een [component CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker) .

* datepicker

   [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker)

   Een kiezer voor de pop-updatum. Deze klasse wordt door de [klasse DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) gebruikt om bladeren en selectie van geldige datums toe te staan.

* datetime

   [CQ.form.DateTime](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DateTime)

   Met de DateTime kan de gebruiker een datum en tijd invoeren door [CQ.Ext.form.DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) en [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField)te combineren.

* dialoogvenster

   [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog)

   Het dialoogvenster is een speciaal venster met een formulier in de hoofdtekst en een knopgroep in de voettekst. Deze wordt doorgaans gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* dialogfieldset

   [CQ.form.DialogFieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DialogFieldSet)

   DialogFieldSet is een [FieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet) voor gebruik in [Dialogs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* directstore

   [CQ.Ext.data.DirectStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectStore)

   Kleine hulpklasse voor het maken van een [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) die is geconfigureerd met een [CQ.Ext.data.DirectProxy](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectProxy) en [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader) om interactie met een [CQ.Ext.Direct](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Direct) Server-side [provider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.direct.Provider) eenvoudiger te maken.

* displayfield

   [CQ.Ext.form.DisplayField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DisplayField)

   Een alleen-weergeven tekstveld dat niet is gevalideerd en niet is verzonden.

* bewerkbalk

   [CQ.wcm.EditBar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBar)

   De EditBar laat de gebruiker inhoud uitgeven gebruikend knopen op een bar.

   Hoewel EditBar hier niet wordt vermeld, heeft alle leden van [CQ.wcm.EditBase](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBase).

* editor

   [CQ.Ext.Editor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Editor)

   Een veld voor een basiseditor dat het weergeven/verbergen op aanvraag afhandelt en beschikt over ingebouwde logica voor grootte en gebeurtenisafhandeling.

* editorgrid

   [CQ.Ext.grid.EditorGridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)

   Deze klasse breidt de [Klasse](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) GridPanel uit om cel het uitgeven op geselecteerde [kolommen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column)te verstrekken. De editable kolommen worden gespecificeerd door een [redacteur](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) in de [kolomconfiguratie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column)te verstrekken.

* editrollover

   [CQ.wcm.EditRollover](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditRollover)

   Met de EditRollover kan de gebruiker inhoud bewerken door te dubbelklikken en worden meer bewerkhandelingen uitgevoerd via een contextmenu. Het bewerkbare gebied wordt aangegeven met een kader wanneer de muis over de inhoud beweegt.

* feedimporter

   [CQ.wcm.FeedImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FeedImporter)

   Met FeedImporter kan de gebruiker RSS- of Atom-feeds importeren en pagina&#39;s maken voor elke feed-invoer.

* field

   [CQ.Ext.form.Field](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Field)

   Basisklasse voor formuliervelden met standaardfuncties voor gebeurtenisafhandeling, -grootte, -afhandeling en andere functies.

* veldset

   [CQ.Ext.form.FieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet)

   Standaardcontainer die wordt gebruikt voor het groeperen van items binnen een [formulier](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FormPanel)....

* fileuploaddialogon

   [CQ.form.FileUploadDialogButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadDialogButton)

   Met FileUploadDialogButton wordt een knop gemaakt waarmee een nieuw dialoogvenster wordt geopend voor het uploaden van een bestand via FileUploadField. Kan worden gebruikt in bewerkingsdialoogvensters waar het uploaden in een afzonderlijk formulier moet plaatsvinden.

* fileuploadveld

   [CQ.form.FileUploadField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadField)

   Met FileUploadField kan de gebruiker één bestand selecteren dat moet worden geüpload.

* findreplacedialog

   [CQ.wcm.FindReplaceDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FindReplaceDialog)

   De FindReplaceDialog is een dialoog voor het vinden en het vervangen van tekenen in een pagina en zijn kindpagina&#39;s.

* flash

   [CQ.Ext.FlashComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.FlashComponent)

* raster

   [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)

   Deze klasse vertegenwoordigt de primaire interface van een component gebaseerd netcontrole om gegevens in een in tabelvorm formaat van rijen en kolommen te vertegenwoordigen.

* groupingstore

   [CQ.Ext.data.GroupingStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)

   Een gespecialiseerde opslagimplementatie die het groeperen van verslagen door één van de beschikbare gebieden voorziet. Dit wordt gewoonlijk gebruikt samen met een [CQ.Ext.grid.GroupingView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GroupingView) om het gegevensmodel voor een gegroepeerde GridPanel te bewijzen.

* hevige dialoog

   [CQ.wcm.HeavyMoveDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.HeavyMoveDialog)

   Het dialoogvenster HeavyMoveDialog is een dialoogvenster voor het verplaatsen van een pagina en de onderliggende pagina&#39;s, waarin ook wordt overwogen eerder geactiveerde pagina&#39;s opnieuw te activeren (&#39;zware&#39; verplaatsing).

* hidden

   [CQ.Ext.form.Hidden](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Hidden)

   Een verborgen basisveld voor het opslaan van verborgen waarden in formulieren die moeten worden doorgegeven aan het verzenden van het formulier.

* historieknop

   [CQ.HistoryButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.HistoryButton)

   HistoryButton is een kleine hulpklasse om rug en voorwaarts knopen gemakkelijk te verstrekken. Gewoonlijk zijn twee verwante instanties vereist: De voorwaartse knoopinstantie is een eenvoudige knoop verbonden aan de achterknoopinstantie die de geschiedenis behandelt.

* htmleditor

   [CQ.ext.form.htmlEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)

   Biedt een lichtgewichtcomponent van HTML Editor. Sommige werkbalkfuncties worden niet ondersteund door Safari en worden automatisch verborgen wanneer dat nodig is. Deze worden genoteerd in de config opties waar aangewezen.

   Op de werkbalkknoppen van de editor zijn knopinfo gedefinieerd in de eigenschap [buttonTips](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor) .

* iframedialoog

   [CQ.IframeDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframeDialog)

   Een dialoogvenster zonder opmaak waarin de inhoud van een iframe wordt weergegeven en waarin formulieren in iframes kunnen worden geplaatst.

* iframePanel

   [CQ.IframePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframePanel)

   Een deelvenster met een iframe. Hiermee kunt u gemakkelijk iframes maken, een gebeurtenis voor het laden van iframes maken en de inhoud van iframe eenvoudig openen.

* inlinetextfield

   [CQ.form.InlineTextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.InlineTextField)

   InlineField is een tekstveld dat als label wordt weergegeven wanneer de focus niet is gericht.

* jsonstore

   [CQ.Ext.data.JsonStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonStore)

   Kleine hulpklasse om het maken van [CQ.Ext.data.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)Stores van JSON-gegevens gemakkelijker te maken. Een JsonStore wordt automatisch geconfigureerd met een [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader).

* label

   [CQ.Ext.form.Label](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Label)

   Veld Standaardlabel.

* taalcopydialog

   [CQ.wcm.LanguageCopyDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LanguageCopyDialog)

   De LanguageCopyDialog is een dialoogvenster voor het kopiëren van taalbomen.

* koppelingencontrole

   [CQ.wcm.LinkChecker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LinkChecker)

   De LinkChecker is een hulpmiddel om externe verbindingen in een plaats te controleren.

* listview

   [CQ.Ext.list.ListView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView)

   CQ.Ext.list.ListView is een snelle en lichtgewichtimplementatie van een [Net](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) als mening.

* livecopyeigenschappen

   [CQ.wcm.msm.LiveCopyProperties](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties)

   LiveCopyProperties biedt een deelvenster voor het weergeven en bewerken van de eigenschappen van Live Copy (relatieovererving, synchronisatietrigger en synchronisatiehandelingen).

* lvbooleancolumn

   [CQ.Ext.list.BooleanColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.BooleanColumn)

   Een kolomdefinitieklasse die Booleaanse gegevensvelden rendert. Zie de [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) config optie van [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) voor meer details.

* lvcolumn

   [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)

   Deze klasse kapselt de gegevens van de kolomconfiguratie in die in de initialisering van een [ListView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView)moeten worden gebruikt.

* lvdatecolumn

   [CQ.Ext.list.DateColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn)

   Een kolomdefinitieklasse die een overgegaane datum volgens de standaardscène, of een gevormd [formaat](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn)teruggeeft. Zie de [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) config optie van [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) voor meer details.

* lvnumbercolumn

   [CQ.Ext.list.NumberColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)

   Een kolomdefinitieklasse die een numeriek gegevensveld weergeeft volgens een [notatietekenreeks](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn) . Zie de [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) config optie van [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column) voor meer details.

* mediabrowsedialoog

   [CQ.MediaBrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.MediaBrowseDialog)

   **Vervangen: Gebruik in plaats hiervan de[Content Finder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder)om te bladeren in media.**

   MediaBrowseDialog is een dialoog voor het doorbladeren van de media bibliotheek.

*  menu

   [CQ.Ext.menu.Menu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Menu)

   Een menuobject. Dit is de container waaraan u menu-items kunt toevoegen. Menu kan ook als basisklasse dienen wanneer u een gespecialiseerd menu wilt dat van een andere component (zoals [CQ.Ext.menu.DateMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu) bijvoorbeeld) wordt gebaseerd.

   Menu&#39;s kunnen [menu-items](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item)of algemene [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component)componenten bevatten.

* menubaseitem

   [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem)

   De basisklasse voor alle items die in menu&#39;s worden gerenderd. BaseItem biedt standaard rendering, geactiveerd statusbeheer en basisconfiguratieopties die door alle menucomponenten worden gedeeld.

* menuCheckitem

   [CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)

   Hiermee wordt een menu-item toegevoegd dat standaard een selectievakje bevat, maar dat ook deel kan uitmaken van een groep keuzerondjes.

* menuitem

   [CQ.Ext.menu.Item](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item)

   Een basisklasse voor alle menu-items die menu-gerelateerde functionaliteit vereisen (zoals submenu&#39;s) en die geen statische weergave-items zijn. Met Item wordt de basisfunctionaliteit van [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem) uitgebreid door menuspecifieke activering toe te voegen en op afhandeling te klikken.

* menuseparator

   [CQ.Ext.menu.Separator](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Separator)

   Voegt een scheidingsbalk toe aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Over het algemeen zult u één van deze door &quot;-&quot;in te gebruiken u aanroept om toe te voegen () of in uw punten config eerder dan direct tot stand te brengen zult toevoegen.

* menuTextem

   [CQ.Ext.menu.TextItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.TextItem)

   Voegt een statische teksttekenreeks toe aan een menu dat gewoonlijk wordt gebruikt als een kop- of groepsscheidingsteken.

* metadata

   [CQ.dam.form.Metadata](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.form.Metadata)

   Metagegevens bevatten een set velden waarmee de informatie wordt bepaald die nodig is voor een metagegevensveld, zoals bijvoorbeeld wordt gebruikt op pagina&#39;s voor middeleneditors.

   Deze biedt de volgende velden:

* multifield

   [CQ.form.MultiField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)

   Het MultiField is een bewerkbare lijst met formuliervelden voor het bewerken van eigenschappen met meerdere waarden.

* mvt

   [CQ.form.MVT](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MVT)

   Met de testcomponent Multivariate kunt u een set afbeeldingen definiëren en bewerken die als wisselende banners worden weergegeven. Klik door tariefstatistieken worden verzameld per banner.

* kennisgevingsvak

   [CQ.wcm.NotificationInbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.NotificationInbox)

   Met NotificationInbox kan de gebruiker zich abonneren op WCM-handelingen en meldingen beheren.

* nummerveld

   [CQ.Ext.form.NumberField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.NumberField)

   Numeriek tekstveld dat automatische toetsaanslag en numerieke validatie biedt.

* offlineimporteur

   [CQ.wcm.OfflineImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.OfflineImporter)

   De OfflineImporter is een programma voor het importeren en converteren van Microsoft Word-documenten naar AEM-pagina&#39;s. Met deze functie kan inhoud offline worden bewerkt met een tekstverwerker.

* eigenaarschap

   [CQ.form.OwnerDraw](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.OwnerDraw)

   De OwnerDraw kan aangepaste HTML-code bevatten (die u rechtstreeks hebt ingevoerd of via een URL hebt opgehaald).

* pagineren

   [CQ.Ext.PagingToolbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.PagingToolbar)

   Naarmate de hoeveelheid records toeneemt, neemt de tijd die de browser nodig heeft om deze weer te geven toe. Met paginering wordt de hoeveelheid gegevens die met de klant wordt uitgewisseld, verminderd.

* deelvenster

   [CQ.ext.panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel)

   Panel is een container die specifieke functionaliteit en structurele componenten heeft die van het de perfecte bouwsteen voor toepassing-georiënteerde gebruikersinterfaces maken.

   Deelvensters zijn vanwege hun overerving van [CQ.Ext.Container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container).

* paragraphreference

   [CQ.form.ParagraphReference](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ParagraphReference)

   In het veld Alineasereferentie kunt u door pagina&#39;s bladeren en een van de alinea&#39;s selecteren. Het bestaat uit een triggerveld en een gekoppeld alineafbladerdialoogvenster.

* password

   [CQ.form.Password](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Password)

   Het wachtwoord is vergelijkbaar met een [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField) , maar behoudt de waarde ervan als privé, zodat gebruikers gevoelige gegevens kunnen invoeren.

* padvoltooiing

   [CQ.form.PathCompletion](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathCompletion)

   **Vervangen: Gebruik in[plaats hiervan CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField).**

* padveld

   [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField)

   Het veld PathField is een invoerveld dat is ontworpen voor paden met padvoltooiing en een knop waarmee een [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog) kan worden geopend voor het bladeren in de opslagplaats van de server. U kunt ook door alinea&#39;s bladeren om geavanceerde koppelingen te genereren.

* vordering

   [CQ.Ext.ProgressBar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)

   Een bij te werken voortgangsbalkcomponent. De voortgangsbalk ondersteunt twee verschillende modi: handmatig en automatisch.

   In de handmatige modus bent u verantwoordelijk voor het weergeven, bijwerken (via [updateProgress](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)) en wissen van de voortgangsbalk, indien nodig vanuit uw eigen code. Deze methode is vooral geschikt wanneer u de voortgang wilt weergeven.

* eigenschappenraster

   [CQ.Ext.grid.PropertyGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyGrid)

   Een gespecialiseerde netimplementatie bedoeld om het traditionele bezitsnet zoals typisch gezien in ontwikkeling IDEs na te bootsen. Elke rij in het raster vertegenwoordigt een eigenschap van een object en de gegevens worden opgeslagen als een set naam-/waardeparen in [CQ.Ext.grid.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyRecord)PropertyRecords.

* propraster

   [CQ.PropertyGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.PropertyGrid)

   PropertyGrid is een algemeen raster dat wordt gebruikt voor het weergeven en bewerken van eigenschappen van objecten.

* quicktip

   [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip)

   @xtype quicktip A gespecialiseerde tooltip klasse voor tooltips die in prijsverhoging kunnen worden gespecificeerd en automatisch door de globale instantie [CQ.Ext.QuickTips](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTips) worden beheerd. Zie de QuickTips-klasseheader voor meer gebruiksdetails en voorbeelden.

* radio

   [CQ.Ext.form.Radio](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio)

   Veld voor één radio. Hetzelfde als Selectievakje, maar als handig hulpmiddel om het invoertype automatisch in te stellen. De groep keuzerondjes wordt automatisch door de browser afgehandeld als u elke radio in een groep dezelfde naam geeft.

* radiogroep

   [CQ.Ext.form.RadioGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.RadioGroup)

   Een groeperingscontainer voor [besturingselementen CQ.Ext.form.Radio](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio) .

* dialoogvenster

   [CQ.wcm.ReferencesDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ReferencesDialog)

   Het dialoogvenster ReferencesDialog is een dialoogvenster waarin verwijzingen op een pagina worden weergegeven.

* restauretreedialoog

   [CQ.wcm.RestoreTreeDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreTreeDialog)

   Het dialoogvenster RestoreTreeDialog is een dialoogvenster voor het herstellen van een vorige versie van een boomstructuur.

* terugzetdialoog

   [CQ.wcm.RestoreVersionDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreVersionDialog)

   Het dialoogvenster TerugzetversieDialog is een dialoogvenster voor het terugzetten van een vorige versie van een pagina.

* richtext

   [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText)

   RichText verstrekt een vormgebied voor het uitgeven van gestileerde tekstinformatie (rijke teksten).

   De component RichText biedt momenteel de volgende functies:

* rolloutplan

   [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan)

   Het rolloutPlan verstrekt een dialoog om de vooruitgang van de paginaloprijving te bekijken. RolloutPlan is begonnen door een [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard).

* rollout, wizard

   [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard)

   De tovenaar RolloutWizard verstrekt een tovenaar voor het opstellen van een pagina. RolloutWizard start een [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan).

* zoekveld

   [CQ.form.SearchField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SearchField)

   Het SearchField verstrekt een onderzoeksgebied dat de resultaten in een drop-down lijst verstrekt die voor het zoeken van de bewaarplaats kan worden gebruikt.

* selectie

   [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection)

   Met de selectie kan de gebruiker kiezen uit verschillende opties. De opties kunnen onderdeel zijn van de configuratie of worden geladen vanuit een JSON-reactie. De selectie kan worden weergegeven als vervolgkeuzelijst (selecteren) of als een keuzelijst met invoervak (selecteren plus item met vrije tekst).

* sidekick

   [CQ.wcm.Sidetrap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Sidekick)

   De Sidetrap is een zwevende hulp die de gebruiker algemene gereedschappen biedt voor het bewerken van pagina&#39;s.

* sitebeheerder

   [CQ.wcm.SiteAdmin](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteAdmin)

   SiteAdmin is een console die WCM beleidsfuncties verstrekt.

* importeur van sites

   [CQ.wcm.SiteImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteImporter)

   De SiteImporter laat de gebruiker volledige websites invoeren en aanvankelijke projecten tot stand brengen.

* sizefield

   [CQ.form.SizeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SizeField)

   Met SizeField kan de gebruiker de breedte en hoogte invoeren (bijvoorbeeld voor een afbeelding).

* schuifregelaar

   [CQ.Ext.Slider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Slider)

   Schuifregelaar die ondersteuning biedt voor verticale of horizontale oriëntatie, toetsenbordaanpassingen, configureerbare magnetisch uitlijnen, asklikken en animatie. Kan als een item aan elke container worden toegevoegd. Voorbeeld:...

* presentatie

   [CQ.form.Slideshow](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Slideshow)

   De diapresentatie bevat een component die kan worden gebruikt om een set afbeeldingen en afbeeldingstitels te definiëren en te bewerken die als een diapresentatie kunnen worden weergegeven.

   De component Presentatie is gebaseerd op de component [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage) .

* smartfile

   [CQ.form.SmartFile](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartFile)

   Het SmartFile-bestand is een intelligente uploader voor bestanden.

   Als een Flash-insteekmodule (versie >= 9) is geïnstalleerd, worden uploads uitgevoerd met behulp van de SWF-uploadbibliotheek die een handige manier biedt om uploads af te handelen.

* slimtimage

   [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage)

   De SmartImage is een intelligente uploader voor afbeeldingen. Het biedt gereedschappen voor het verwerken van een geüploade afbeelding, bijvoorbeeld een gereedschap voor het definiëren van afbeeldingen met hyperlinks en een functie voor het uitsnijden van afbeeldingen.

   De component is voornamelijk ontworpen voor gebruik op een apart tabblad in het dialoogvenster.

* spacer

   [CQ.ext.spacer](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Spacer)

   Wordt gebruikt om een grote ruimte in een lay-out te bieden.

* spinner

   [CQ.form.Spinner](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Spinner)

   De spinner is een triggerveld voor numerieke, datum- of tijdwaarden. De waarde kan worden verhoogd en verlaagd met de beschikbare triggers omhoog en omlaag, het schuifwiel of de toetsen.

* splitknop

   [CQ.Ext.SplitButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.SplitButton)

   Een gesplitste knop met een ingebouwde vervolgkeuzepijl die een gebeurtenis afzonderlijk van de standaardklikgebeurtenis van de knop kan starten. Dit wordt doorgaans gebruikt om een vervolgkeuzemenu weer te geven dat aanvullende opties biedt voor de primaire knopactie, maar elke aangepaste handler kan de arrowclick-implementatie leveren.

* statisch

   [CQ.Static](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Static)

   Static kan worden gebruikt om willekeurige tekst of HTML weer te geven.

* statistieken

   [CQ.wcm.Statistieken](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Statistics)

   De Statistieken tonen de paginamonpressies als grafiek. Met de widget kunt u een punt selecteren. De statistieken moeten dan worden weergegeven.

* winkel

   [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)

   De klasse Store kapselt een cliënt zijgeheime voorgeheugen van voorwerpen van het [Verslag](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Record) in die inputgegevens voor Componenten zoals [GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), [ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox), of [DataView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView)verstrekken.

* suggestfield

   [CQ.form.SuggestField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SuggestField)

   Het SuggestField verstrekt de gebruiker van suggesties die op zijn ingang worden gebaseerd.

* schakelaar

   [CQ.Switcher](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Switcher)

   De Schakelaar verstrekt een knoopgroep voor de kopbalbar in een console om tussen Websites, Digitale Activa, Hulpmiddelen, Werkschema, en Veiligheid te schakelen.

* tableedit

   [CQ.form.TableEdit](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit)

   **Vervangen: Gebruik in[plaats hiervan CQ.form.TableEdit2](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2).**

* tableedit2

   [CQ.form.TableEdit2](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2)

   TableEdit2 verstrekt een widget voor het creëren van lijsten.

* tabbladen

   [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel)

   Een eenvoudige tabcontainer. TabPanels kunnen voor lay-outdoeleinden precies als een standaard [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel) worden gebruikt, maar hebben ook speciale steun voor het bevatten van kindComponenten ([`items`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)).

* tags

   [CQ.tagging.TagInputField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tagging.TagInputField)

   ```
   CQ.tagging.TagInputField
   ```

   is een formulierwidget voor het invoeren van codes. Deze bevat een pop-upmenu waarin u een keuze kunt maken uit bestaande tags, waaronder automatisch aanvullen en een groot aantal andere functies.

* textarea

   [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea)

   Tekstveld met meerdere regels. Kan worden gebruikt als directe vervanging voor traditionele tekstgebieden, plus steun voor auto-resizing.

* textbutton

   [CQ.TextButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.TextButton)

   De TextButton biedt een tekstkoppeling met de mogelijkheden van een [CQ.Ext.Button](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button).

* textfield

   [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)

   Basistekstveld. Kan worden gebruikt als directe vervanging voor traditionele tekstinvoer, of als basisklasse voor meer geavanceerde invoerbesturingselementen (zoals [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea) en [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)).

* miniatuur

   [CQ.form.Thumbnail](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Thumbnail)

* tijdveld

   [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField)

   Biedt een invoerveld voor de tijd met een vervolgkeuzelijst en automatische tijdvalidatie. Voorbeeld:...

* tip

   [CQ.ext.tip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tip)

   @xtype tip Dit is de basisklasse voor [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip) en [CQ.Ext.Tooltip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tooltip) die de basislay-out en het plaatsen verstrekt die alle op uiteinde-gebaseerde klassen vereisen. Deze klasse kan direct voor eenvoudige, statisch-gepositioneerde uiteinden worden gebruikt.

* titleseparator

   [CQ.menu.TitleSeparator](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.menu.TitleSeparator)

   Voegt een scheidingsbalk toe aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Het scheidingsteken kan bovendien een titel dragen.

* toolbar

   [CQ.ext.toolbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Toolbar)

   Standaardwerkbalkklasse. Hoewel de werkbalk [`defaultType`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) voor werkbalken [`button`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button)is bedoeld, kunnen de werkbalkelementen (onderliggende items voor de werkbalkcontainer) vrijwel elk type component zijn. Werkbalkelementen kunnen expliciet worden gemaakt via hun constructors.

* tooltip

   [CQ.Ext.ToolTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ToolTip)

   Een standaard tooltip implementatie voor het verstrekken van extra informatie wanneer het hangen over een doelelement. @xtype tooltip.

* treuzelen

   [CQ.tree.TreeGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tree.TreeGrid)

   @xtype treegrid

* treepanel

   [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)

   TreePanel verstrekt boom-gestructureerde vertegenwoordiging UI van boom-gestructureerde gegevens.

   [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode)TreeNodes die aan TreePanel worden toegevoegd kan meta-gegevens bevatten die door uw toepassing in hun [attributenbezit](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode) worden gebruikt.

* trigger

   [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)

   Verstrekt een geschikte omslag voor TextFields die een klikbare trekkerknoop toevoegt (kijkt als een combobox door gebrek). De trigger heeft geen standaardhandeling, dus u moet een functie toewijzen om de activeringsklikhandler te implementeren door [onTriggerClick](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)te overschrijven. U kunt een TriggerField direct tot stand brengen, aangezien het precies als een combobox teruggeeft.

* uploadditioneel

   [CQ.UploadDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UploadDialog)

   Met het dialoogvenster UploadDialog kan de gebruiker bestanden uploaden naar de opslagplaats. Hiermee wordt een nieuw dialoogvenster UploadDialog gemaakt.

* userinfo

   [CQ.UserInfo](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UserInfo)

   Werkbalkitem om de huidige gebruikersnaam weer te geven en gebruikersacties zoals het bewerken van gebruikerseigenschappen en imitatie toe te staan.

* viewport

   [CQ.Ext.Viewport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport)

   Een gespecialiseerde container die het zichtbare toepassingsgebied vertegenwoordigt (viewport van browser).

   De Viewport geeft zichzelf aan het documentlichaam terug, en past zich automatisch aan de grootte van browser viewport aan en beheert venster resizing. Er kan slechts één Viewport zijn gemaakt.

* venster

   [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)

   Een speciaal deelvenster dat is bedoeld voor gebruik als toepassingsvenster. Vensters worden standaard zwevend, [resizable](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window), en [versleepbaar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) . Vensters kunnen worden [gemaximaliseerd](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) om viewport te vullen, aan hun vroegere grootte worden hersteld, en kunnen worden [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)geminimaliseerd.

* xmlstore

   [CQ.Ext.data.XmlStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlStore)

   Kleine hulpklasse om het maken van [CQ.Ext.data.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)Stores van de gegevens van XML gemakkelijker te maken. Een XMLStore wordt automatisch geconfigureerd met een [CQ.Ext.data.XmlReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlReader).

   **cqinclude** Pseudo xtype dat widgetdefinities van een verschillend pad in de repository bevat. Deze wordt meestal gebruikt in paginadialoogvensters. Er is geen werkelijke JavaScript-widgetklasse voor dit xtype. Het wordt verwerkt door de formatData() functie van de CQ.Util klasse. Zie dit kennisbankartikel voor meer informatie.
