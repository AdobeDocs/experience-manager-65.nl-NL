---
title: Metagegevensschema van map
description: Leer hoe u een metagegevensschema voor middelenmappen maakt in AEM Assets
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
uuid: bf8d066c-0f23-4d18-9ce9-860fa505dea2
discoiquuid: 23009e50-a026-4823-8e4c-7a313a11b38c
docset: aem65
translation-type: tm+mt
source-git-commit: 62cc3282f8d8bc77f072de1d027484bd93efa38a

---


# Metagegevensschema van map {#folder-metadata-schema}

Met Adobe Experience Manager (AEM)-middelen kunt u metagegevensschema&#39;s voor middelenmappen maken, waarmee de lay-out en de metagegevens worden gedefinieerd die worden weergegeven in pagina&#39;s met eigenschappen van mappen.

## Een schema voor metagegevens van een map toevoegen {#add-a-folder-metadata-schema-form}

Met de editor voor Mapmetagegevensschemaformulieren kunt u metagegevensschema&#39;s voor mappen maken en bewerken.

1. Tik/klik op het AEM-logo en ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]** > **[!UICONTROL Metagegevensschema&#39;s]** van map.
1. Tik op of klik op **[!UICONTROL Maken]** op de pagina Metagegevensschema-formulierformulieren.
1. Geef een naam voor het formulier op en tik op of klik op **[!UICONTROL Maken]**. De nieuwe schemavorm wordt vermeld op de pagina van de Vormen van het Schema.

## Formulieren met metagegevens van mappen bewerken {#edit-folder-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken, dat het volgende bevat:

* Tabs
* Formulieritems in tabbladen.

U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagruimte. U kunt nieuwe tabbladen of formulieritems toevoegen aan het metagegevensschemaformulier.

1. Selecteer op de pagina Schema-formulieren het formulier dat u hebt gemaakt en tik op het pictogram **[!UICONTROL Bewerken]** of klik op de werkbalk.
1. Tik op de pagina Editor van het metagegevensschema van de map `+` om een tabblad aan het formulier toe te voegen. Als u de naam van het tabblad wilt wijzigen, tikt u op de standaardnaam of klikt u erop en geeft u de nieuwe naam op onder **[!UICONTROL Instellingen]**.

   ![custom_tab](assets/custom_tab.png)

   Tik op `+`om meer tabbladen toe te voegen. Tik `X` op een tabblad om het te verwijderen.

1. Voeg op het actieve tabblad een of meer componenten toe vanaf het tabblad **[!UICONTROL Formulier]** samenstellen.

   ![adding_components](assets/adding_components.png)

   Als u meerdere tabbladen maakt, tikt of klikt u op een bepaald tabblad om componenten toe te voegen.

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **[!UICONTROL Instellingen]** .

   Verwijder zo nodig een component van het tabblad **[!UICONTROL Instellingen]** .

   ![configure_properties](assets/configure_properties.png)

1. Tik/klik op **[!UICONTROL Opslaan]** op de werkbalk om de wijzigingen op te slaan.

### Componenten om formulieren te maken {#components-to-build-forms}

Het tabblad **[!UICONTROL Formulier]** samenstellen bevat formulieritems die u in het metagegevensschema van uw map gebruikt. Op het tabblad **[!UICONTROL Instellingen]** worden de kenmerken weergegeven voor elk item dat u selecteert op het tabblad **[!UICONTROL Formulier]** samenstellen. Hier volgt een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Formulier]** samenstellen:

| Componentnaam | Beschrijving |
|---|---|
| [!UICONTROL Sectiekop] | Voeg een sectiekopje toe voor een lijst met gangbare componenten. |
| [!UICONTROL Tekst met één regel] | Voeg een teksteigenschap voor één regel toe. De eigenschap wordt opgeslagen als een tekenreeks. |
| [!UICONTROL Meerdere waardetekst] | Voeg een teksteigenschap voor meerdere waarden toe. Deze wordt opgeslagen als een tekenreeks-array. |
| [!UICONTROL Getal] | Voeg een getalcomponent toe. |
| [!UICONTROL Date] | Voeg een datumcomponent toe. |
| [!UICONTROL Vervolgkeuzelijst] | Voeg een vervolgkeuzelijst toe. |
| [!UICONTROL Standaardlabels] | Voeg een tag toe. |
| [!UICONTROL Verborgen veld] | Voeg een verborgen veld toe. Deze wordt als een POST-parameter verzonden wanneer het element wordt opgeslagen. |

### Formulieritems bewerken {#editing-form-items}

Als u de eigenschappen van formulieritems wilt bewerken, tikt u op de component of klikt u op de component en bewerkt u alle eigenschappen of een subset van de volgende eigenschappen op het tabblad **[!UICONTROL Instellingen]** .

**[!UICONTROL Veldlabel]**: De naam van de eigenschap metadata die wordt weergegeven op de eigenschappenpagina voor de map.

**[!UICONTROL Toewijzen aan eigenschap]**: This property specifies the relative path of the folder node in the CRX repository where it is saved. Het begint met &quot;**./**&quot;. Dit geeft aan dat het pad zich onder het knooppunt van de map bevindt.

Hier volgen de geldige waarden voor deze eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metagegevensknooppunt van de map opgeslagen als de eigenschap `dc:title`.

* `./jcr:created`: Geeft de JCR-eigenschap op het knooppunt van de map weer. Als u deze eigenschappen configureert in CRXDE, raadt Adobe u aan ze te markeren als Uitschakelen, omdat ze zijn beveiligd. Anders treedt de fout &#39; `Asset(s) failed to modify`&#39; op wanneer u de eigenschappen van het element opslaat.

Neem geen spatie op in het eigenschapspad om ervoor te zorgen dat de component correct wordt weergegeven in het schema voor metagegevens.

**[!UICONTROL JSON-pad]**: Gebruik deze optie om het pad van het JSON-bestand op te geven waarin u sleutelwaardeparen voor opties opgeeft.

**[!UICONTROL Tijdelijke aanduiding]**: Gebruik deze eigenschap om relevante plaatsaanduidingstekst met betrekking tot de eigenschap metadata op te geven.

**[!UICONTROL Keuzen]**: Gebruik deze eigenschap om keuzen in een lijst op te geven.

**[!UICONTROL Omschrijving]**: Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.

**[!UICONTROL Klasse]**: Objectklasse waaraan de eigenschap is gekoppeld.

## Formulieren met metagegevens van mappen verwijderen {#delete-folder-metadata-schema-forms}

U kunt de schemaformulieren van de omslagmeta-gegevens van de pagina van de Vormen van het Schema van Meta-gegevens schrappen. Als u een formulier wilt verwijderen, selecteert u het en tikt of klikt u op het pictogram Verwijderen op de werkbalk.

![delete_form](assets/delete_form.png)

## Een schema voor metagegevens van mappen toewijzen {#assign-a-folder-metadata-schema}

U kunt een schema van omslagmeta-gegevens aan een omslag of van de pagina van de Vormen van het Schema van Meta-gegevens van de Omslag toewijzen of wanneer het creëren van een omslag.

Als u een metagegevensschema voor een map configureert, wordt het pad naar het schema opgeslagen in de `folderMetadataSchema` eigenschap van het mapknooppunt onder.*/jcr:content*.

### Wijs aan een schema van de pagina van het Schema van Meta-gegevens van de Omslag toe {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Tik/klik op het AEM-logo en ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]**> **[!UICONTROL Metagegevensschema&#39;s]** van map.
1. Selecteer op de pagina Formulieren schema met metagegevens van map het schema dat u op een map wilt toepassen.
1. Tik op de werkbalk of klik op **[!UICONTROL Toepassen op map(pen)]**.

1. Selecteer de map waarop u het schema wilt toepassen en klik op **[!UICONTROL Toepassen]**. Als er al een metagegevensschema op de map is toegepast, verschijnt er een waarschuwingsbericht dat u het bestaande metagegevensschema wilt overschrijven. Tik/klik op **[!UICONTROL Overschrijven]**.
1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.

   ![folder_properties](assets/folder_properties.png)

   Tik op het tabblad Metagegevens van **[!UICONTROL map of klik op het tabblad Metagegevens]** van de map om de velden met metagegevens van de map weer te geven.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Een schema toewijzen bij het maken van een map {#assign-a-schema-when-creating-a-folder}

U kunt een schema van omslagmeta-gegevens toewijzen wanneer het creëren van een omslag. Als het systeem ten minste één schema voor metagegevens van mappen bevat, wordt een extra lijst weergegeven in het dialoogvenster Map **** maken. U kunt het gewenste schema selecteren. Standaard is geen schema geselecteerd.

1. Tik in de gebruikersinterface van AEM Assets op **[!UICONTROL Maken]** of klik op de werkbalk.
1. Geef een titel en naam voor de map op.
1. Selecteer het gewenste schema in de lijst Metagegevensschema van map. Tik vervolgens op **[!UICONTROL Maken]** of klik op Maken.

   ![select_schema](assets/select_schema.png)

1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.
1. Tik op het tabblad Metagegevens van **[!UICONTROL map of klik op het tabblad Metagegevens]** van de map om de velden met metagegevens van de map weer te geven.

## Het schema voor metagegevens van de map gebruiken {#use-the-folder-metadata-schema}

Open de eigenschappen voor een omslag die met een schema van omslagmeta-gegevens wordt gevormd. Het tabblad Metagegevens **[!UICONTROL van]** map wordt weergegeven op de pagina met eigenschappen van de map. Selecteer dit tabblad om het schema van de mapmetagegevens weer te geven.

Voer waarden voor metagegevens in de verschillende velden in en tik op **[!UICONTROL Opslaan]** of klik op Opslaan om de waarden op te slaan. De waarden die u opgeeft, worden opgeslagen in het mapknooppunt in de CRX-opslagruimte.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)

