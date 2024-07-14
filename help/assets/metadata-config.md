---
title: Configuratie en beheer van metagegevensfunctionaliteit.
description: Configuratie en beleid van  [!DNL Experience Manager Assets]  functionaliteit met betrekking tot meta-gegevenstoevoeging en beheer.
contentOwner: AG
role: User, Admin
feature: Metadata
exl-id: 56c92b7f-e687-4ab5-a376-afa58bdb6ee0
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 3%

---

# Configuratie en beheer van de metagegevensfunctionaliteit in [!DNL Assets] {#config-metadata}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/metadata-profiles.html?lang=en) |
| AEM 6,5 | Dit artikel |

<!-- Scope of metadata articles:
* metadata.md: The scope of this article is basic metadata updates, changes, and so on, operations that end-users can do.
* metadata-concepts.md: All conceptual information. Minor instructions are OK but it is an FYI article about support and standards.
* metadata-config.md: New article. Contains all configuration and administration how-to info related to metadata of assets.
-->

[!DNL Adobe Experience Manager Assets] houdt metagegevens bij voor elk element. Het maakt het gemakkelijker om activa te categoriseren en te organiseren en het helpt mensen die naar een specifiek bezit zoeken. Met de mogelijkheid om metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van hun metagegevens. Met [!DNL Adobe Experience Manager Assets] kunnen beheerders de functionaliteit van metagegevens configureren en aanpassen om de standaardaanbieding voor Adoben te wijzigen.

## Metagegevensschema bewerken {#metadata-schema}

Voor details, zie [ de vormen van het meta-gegevensschema ](metadata-schemas.md#edit-metadata-schema-forms) uitgeven.

## Een aangepaste naamruimte registreren binnen [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten toevoegen binnen [!DNL Experience Manager] . Net zoals er vooraf gedefinieerde naamruimten zijn, zoals `cq` , `jcr` en `sling` , kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van XML.

1. Open de beheerpagina voor knooppunttypen `https://[aem_server]:[port]/crx/explorer/nodetypes/index.jsp` .
1. Als u de pagina voor naamruimtebeheer wilt openen, klikt u op **[!UICONTROL Namespaces]** boven aan de pagina.
1. Klik op **[!UICONTROL New]** onder aan de pagina om een naamruimte toe te voegen.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie. Geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id. Klik op **[!UICONTROL Save]**.

## Limieten configureren voor updates van bulkmetagegevens {#bulk-metadata-update-limit}

Om een ontkenning van de dienst (DOS) als situatie te verhinderen, beperkt [!DNL Enterprise Manager] het aantal parameters die in een het Verkopen verzoek worden gesteund. Wanneer u metagegevens van veel elementen in één keer bijwerkt, kunt u de limiet bereiken en worden de metagegevens niet bijgewerkt voor meer elementen. Enterprise Manager genereert de volgende waarschuwing in de logboeken:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Als u de limiet wilt wijzigen, opent u **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** en wijzigt u de waarde van **[!UICONTROL Maximum POST Parameters]** in de **[!UICONTROL Apache Sling Request Parameter Handling]** OSGi-configuratie.

## Metagegevensprofielen {#metadata-profiles}

Met een metagegevensprofiel kunt u standaardmetagegevens toepassen op elementen in een map. Maak een metagegevensprofiel en pas dit toe op een map. Elk element dat u later naar de map uploadt, overerft de standaardmetagegevens die u in het metagegevensprofiel hebt geconfigureerd.

### Een metagegevensprofiel toevoegen {#adding-a-metadata-profile}

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** en klik op **[!UICONTROL Create]** .
1. Voer bijvoorbeeld een titel in voor het profiel `Sample Metadata` en klik op **[!UICONTROL Create]** . De [!UICONTROL Edit Form] voor het metagegevensprofiel wordt weergegeven.

   ![ geef een meta-gegevensvorm ](assets/metadata-edit-form.png) uit

1. Klik op een component en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]** . Klik bijvoorbeeld op de component **[!UICONTROL Description]** en bewerk de eigenschappen ervan.

   ![ Vestiging van een component in meta-gegevensprofiel ](assets/metadata-profile-component-setting.png)

   Bewerk de volgende eigenschappen voor de component **[!UICONTROL Description]** :

   * **[!UICONTROL Field Label]**: De weergavenaam van de eigenschap metadata. Dit is alleen voor de gebruikersverwijzing.

   * **[!UICONTROL Map to Property]**: De waarde van deze eigenschap geeft het relatieve pad of de naam naar het knooppunt met middelen waar het in de opslagplaats is opgeslagen. De waarde moet altijd beginnen met `./` omdat dit aangeeft dat het pad zich onder het knooppunt van het element bevindt.

   ![ Kaart aan bezit dat in meta-gegevensprofiel ](assets/metadata-profile-setting-map-property.png) plaatst

   De waarde die u opgeeft voor **[!UICONTROL Map to property]** , wordt opgeslagen als een eigenschap onder het metagegevensknooppunt van het element. Als u bijvoorbeeld `./jcr:content/metadata/dc:desc` opgeeft als de naam van **[!UICONTROL Map to property]** , slaat [!DNL Assets] de waarde `dc:desc` op in het metagegevensknooppunt van het element. Adobe raadt u aan slechts één veld toe te wijzen aan een bepaalde eigenschap in het metagegevensschema. Anders wordt het laatst toegevoegde veld dat aan de eigenschap is toegewezen, door het systeem gekozen.

   * **[!UICONTROL Default Value]**: Gebruik deze eigenschap om een standaardwaarde voor de metagegevenscomponent toe te voegen. Als u bijvoorbeeld &quot;Mijn beschrijving&quot; opgeeft, wordt deze waarde toegewezen aan de eigenschap `dc:desc` bij het metagegevensknooppunt van het element.

   ![ plaats standaardbeschrijving in meta-gegevensprofiel ](assets/metadata-profile-setting-default-value.png)

   >[!NOTE]
   >
   >Als u een standaardwaarde toevoegt aan een nieuwe eigenschap metadata (die niet bestaat op het knooppunt `/jcr:content/metadata` ), worden de eigenschap en de waarde ervan standaard niet weergegeven op de pagina [!UICONTROL Properties] van het element. Als u de nieuwe eigenschap wilt weergeven op de pagina [!UICONTROL Properties] van de elementen, wijzigt u het bijbehorende schema.

1. (Optioneel) Voeg op het tabblad **[!UICONTROL Build Form]** meer componenten toe aan [!UICONTROL Edit Form] en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]** . De volgende eigenschappen zijn beschikbaar op het tabblad **[!UICONTROL Build Form]** :

| Component | Eigenschappen |
| ----------------------------- | ----------------------------------------------------------------------- |
| [!UICONTROL Section Header] | Veldlabel, <br> Beschrijving |
| [!UICONTROL Single-Line Text] | Veld Label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Multi Value Text] | Veld Label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Number] | Veld Label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Date] | Veld Label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Standard Tags] | Veldlabel, <br> Toewijzen aan eigenschap, <br> Standaardwaarde, <br> Beschrijving |

1. Klik op **[!UICONTROL Done]**. Het metagegevensprofiel wordt toegevoegd aan de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]** . <br>

   ![ profiel van Meta-gegevens dat in de pagina van Profielen van Meta-gegevens wordt toegevoegd ](assets/MetadataProfiles-page.png)

### Een metagegevensprofiel kopiëren {#copying-a-metadata-profile}

1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** een metagegevensprofiel om er een kopie van te maken.

   ![ Kopieer een meta-gegevensprofiel ](assets/metadata-profile-edit-copy-option.png)

1. Klik op **[!UICONTROL Copy]** op de werkbalk.
1. Voer in het dialoogvenster **[!UICONTROL Copy Metadata Profile]** een titel in voor de nieuwe kopie van het metagegevensprofiel.
1. Klik op **[!UICONTROL Copy]**. De kopie van het metadataprofiel wordt weergegeven in de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]**.

   ![ een exemplaar van meta-gegevensprofiel dat in de pagina van Profielen van Meta-gegevens wordt toegevoegd ](assets/copy-metadata-profile.png)

### Een metagegevensprofiel verwijderen {#deleting-a-metadata-profile}

1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** een profiel dat u wilt verwijderen.

1. Klik op **[!UICONTROL Delete Metadata Profiles]** op de werkbalk.
1. Klik in het dialoogvenster op **[!UICONTROL Delete]** om de verwijderbewerking te bevestigen. Het metagegevensprofiel wordt uit de lijst verwijderd.

<!-- TBD: Revisit to find out the correct config. and update these steps. When fixed, also o
These steps have been carried forward from old AEM versions. See https://helpx.adobe.com/experience-manager/6-2/assets/using/metadata-profiles.html#ApplyingaMetadataProfiletoFolders

### Configuration to apply a metadata profile globally {#apply-a-metadata-profile-globally}

In addition to applying a profile to a folder, you can also apply one globally so that any content uploaded into [!DNL Experience Manager] assets in any folder has the selected profile applied.

You can reprocess assets in a folder that already has an existing metadata profile that you later changed. See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets).

To apply a metadata profile globally, follow these steps:

* Navigate to `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` and apply the appropriate profile and click **[!UICONTROL Save]**.

  ![Apply metadata profile to a folder globally](assets/metadata-profile-folder-setting.png)

* In CRXDE Lite, navigate to the following node: `/content/dam/jcr:content`. Add the property `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` and click **[!UICONTROL Save All]**.

  ![See applied metadata profile to a folder in the JCR in CRXDE](assets/metadata-profile-folder-setting2.png)
-->

## Metagegevensschema voor een map {#folder-metadata-schema}

Met [!DNL Adobe Experience Manager Assets] kunt u metagegevensschema&#39;s maken voor middelenmappen, waarmee de lay-out en de metagegevens worden gedefinieerd die op de pagina&#39;s met mapeigenschappen worden weergegeven.

### Een schema voor mapmetagegevens toevoegen {#add-a-folder-metadata-schema-form}

Met de Forms-editor voor het schema Metagegevens van map kunt u metagegevensschema&#39;s voor mappen maken en bewerken.

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]** .
1. Klik op de pagina [!UICONTROL Folder Metadata Schema Forms] op **[!UICONTROL Create]** .
1. Geef een naam op voor het formulier en klik op **[!UICONTROL Create]** . Het nieuwe schema wordt weergegeven op de pagina [!UICONTROL Schema Forms] .

### Formulieren met metagegevens van mappen bewerken {#edit-folder-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken, dat het volgende bevat:

* Tabs
* Formulieritems in tabbladen.

U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagplaats. U kunt nieuwe tabbladen of formulieritems toevoegen aan het metagegevensschema.

1. Selecteer op de pagina Schema Forms het formulier dat u hebt gemaakt en selecteer vervolgens de optie **[!UICONTROL Edit]** op de werkbalk.
1. Klik op `+` in de pagina Editor van het metagegevensschema van de map om een tabblad aan het formulier toe te voegen. Als u de naam van het tabblad wilt wijzigen, klikt u op de standaardnaam en geeft u de nieuwe naam op onder **[!UICONTROL Settings]** .

   ![ custom_tab ](assets/custom_tab.png)

   Klik op `+` als u meer tabbladen wilt toevoegen. Klik op `X` op een tab om het te verwijderen.

1. Voeg op het actieve tabblad een of meer componenten toe vanaf het tabblad **[!UICONTROL Build Form]** .

   ![ adding_components ](assets/adding_components.png)

   Als u meerdere tabbladen maakt, klikt u op een bepaald tabblad om componenten toe te voegen.

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **[!UICONTROL Settings]** .

   Verwijder zo nodig een component van het tabblad **[!UICONTROL Settings]** .

   ![ configure_properties ](assets/configure_properties.png)

1. Als u de wijzigingen wilt opslaan, selecteert u **[!UICONTROL Save]** op de werkbalk.

#### Componenten om formulieren te maken {#components-to-build-forms}

Het tabblad **[!UICONTROL Build Form]** bevat formulieritems die u in het metagegevensschema van uw map gebruikt. Op het tabblad **[!UICONTROL Settings]** worden de kenmerken weergegeven voor elk item dat u selecteert op het tabblad **[!UICONTROL Build Form]** . Hier volgt een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Build Form]** :

| Componentnaam | Beschrijving |
|---|---|
| [!UICONTROL Section Header] | Voeg een sectiekopje toe voor een lijst met gangbare componenten. |
| [!UICONTROL Single Line Text] | Voeg een teksteigenschap voor één regel toe. De eigenschap wordt opgeslagen als een tekenreeks. |
| [!UICONTROL Multi Value Text] | Voeg een teksteigenschap voor meerdere waarden toe. Deze wordt opgeslagen als een tekenreeks-array. |
| [!UICONTROL Number] | Voeg een getalcomponent toe. |
| [!UICONTROL Date] | Voeg een datumcomponent toe. |
| [!UICONTROL Dropdown] | Voeg een vervolgkeuzelijst toe. |
| [!UICONTROL Standard Tags] | Voeg een tag toe. |
| [!UICONTROL Hidden Field] | Voeg een verborgen veld toe. Deze wordt als een POST-parameter verzonden wanneer het element wordt opgeslagen. |

#### Formulieritems bewerken {#editing-form-items}

Als u de eigenschappen van formulieritems wilt bewerken, klikt u op de component en bewerkt u alle of een subset van de volgende eigenschappen op het tabblad **[!UICONTROL Settings]** .

**[!UICONTROL Field Label]**: De naam van de eigenschap metadata die wordt weergegeven op de pagina met eigenschappen voor de map.

**[!UICONTROL Map to Property]**: Deze eigenschap geeft het relatieve pad aan van het mapknooppunt in de CRX-opslagplaats waar het wordt opgeslagen. Het begint met &quot;**./**&quot;, wat aangeeft dat het pad zich onder het knooppunt van de map bevindt.

Hier volgen de geldige waarden voor deze eigenschap:

* `./jcr:content/metadata/dc:title`: slaat de waarde op in het metagegevensknooppunt van de map als de eigenschap `dc:title` .

* `./jcr:created`: geeft de JCR-eigenschap op het knooppunt van de map weer. Als u deze eigenschappen in CRXDE vormt, adviseert de Adobe dat u hen als onbruikbaar maakt uitgeeft markeert, omdat zij beschermd zijn. Anders treedt de fout &#39; `Asset(s) failed to modify`&#39; op wanneer u de eigenschappen van het element opslaat.

Neem geen spatie op in het eigenschapspad om ervoor te zorgen dat de component correct wordt weergegeven in het schema voor metagegevens.

**[!UICONTROL JSON Path]**: gebruik deze optie om het pad van het JSON-bestand op te geven, waarin u sleutelwaardeparen voor opties opgeeft.

**[!UICONTROL Placeholder]**: gebruik deze eigenschap om relevante plaatsaanduidingstekst op te geven met betrekking tot de eigenschap metadata.

**[!UICONTROL Choices]**: Gebruik deze eigenschap om keuzen in een lijst op te geven.

**[!UICONTROL Description]**: Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.

**[!UICONTROL Class]**: Object-klasse waaraan de eigenschap is gekoppeld.

### Formulieren met metagegevens van mappen verwijderen {#delete-folder-metadata-schema-forms}

U kunt de schemaformulieren van de omslagmeta-gegevens van het Schema Forms van de Meta-gegevens van de Omslag schrappen pagina. Als u een formulier wilt verwijderen, selecteert u het formulier en klikt u op de werkbalk op de optie Verwijderen.

![ delete_form ](assets/delete_form.png)

### Een schema voor metagegevens van mappen toewijzen {#assign-a-folder-metadata-schema}

U kunt een schema van omslagmeta-gegevens aan een omslag of van de pagina van Forms van het Schema van Meta-gegevens van de Omslag toewijzen of wanneer het creëren van een omslag.

Als u een metagegevensschema voor een map configureert, wordt het pad naar het schemaformulier opgeslagen in de eigenschap `folderMetadataSchema` van het mapknooppunt onder `./jcr:content` .

#### Wijs aan een schema van de pagina van het Schema van Meta-gegevens van de Omslag toe {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]** .
1. Selecteer op de pagina Forms van het schema Metagegevens map het schema dat u op een map wilt toepassen.
1. Klik **[!UICONTROL Apply to Folder(s)]** op de werkbalk.

1. Selecteer de map waarop u het schema wilt toepassen en klik op **[!UICONTROL Apply]** . Als er al een metagegevensschema op de map is toegepast, verschijnt er een waarschuwingsbericht dat u het bestaande metagegevensschema wilt overschrijven. Klik op **[!UICONTROL Overwrite]**.
1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.

   ![ folder_properties ](assets/folder_properties.png)

   Klik op de tab **[!UICONTROL Folder Metadata]** om de velden met metagegevens van de map weer te geven.

   ![ folder_metadata_properties ](assets/folder_metadata_properties.png)

#### Een schema toewijzen bij het maken van een map {#assign-a-schema-when-creating-a-folder}

U kunt een schema van omslagmeta-gegevens toewijzen wanneer het creëren van een omslag. Als het systeem ten minste één schema voor metagegevens van de map bevat, wordt een extra lijst weergegeven in het dialoogvenster **[!UICONTROL Create Folder]** . U kunt het gewenste schema selecteren. Standaard is geen schema geselecteerd.

1. Klik in de gebruikersinterface van [!DNL Experience Manager Assets] op **[!UICONTROL Create]** op de werkbalk.
1. Geef een titel en naam voor de map op.
1. Selecteer het gewenste schema in de lijst Metagegevensschema van map. Klik vervolgens op **[!UICONTROL Create]** .

   ![ select_schema ](assets/select_schema.png)

1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.
1. Klik op de tab **[!UICONTROL Folder Metadata]** om de velden met metagegevens van de map weer te geven.

### Het schema voor metagegevens van de map gebruiken {#use-the-folder-metadata-schema}

Open de eigenschappen voor een map die met een mapmetadataschema is geconfigureerd. Er wordt een tabblad **[!UICONTROL Folder Metadata]** weergegeven in de map [!UICONTROL Properties] pagina. Selecteer dit tabblad om het formulier van het mapmetadataschema weer te geven.

Voer waarden voor metagegevens in de verschillende velden in en klik op **[!UICONTROL Save]** om de waarden op te slaan. De waarden die u opgeeft, worden opgeslagen in het mapknooppunt in de CRX-opslagplaats.

![ folder_metadata_properties-1 ](assets/folder_metadata_properties-1.png)

## Tips en beperkingen {#best-practices-limitations}

* Registreer de naamruimten eerst om metagegevens in aangepaste naamruimten te importeren.
* De eigenschappenkiezer geeft eigenschappen weer die in schema-editors en zoekformulieren worden gebruikt. Eigenschapkiezer kiest geen eigenschappen voor metagegevens uit een element.
* U kunt al bestaande metagegevensprofielen hebben sinds de upgrade naar [!DNL Experience Manager] 6.5. Als u na de upgrade een dergelijk profiel toepast in de map [!UICONTROL Properties] op het tabblad [!UICONTROL Metadata Profiles] , worden de formuliervelden voor metagegevens niet weergegeven. Als u echter een nieuw metagegevensprofiel toepast, worden de formuliervelden weergegeven, maar niet beschikbaar zoals u had verwacht. Er gaat geen functionaliteit verloren, maar als u de (niet-beschikbare) formuliervelden wilt zien, bewerkt en slaat u de bestaande metagegevensprofielen op.

>[!MORELIKETHIS]
>
>* [ concepten van Meta-gegevens en begrip ](metadata-concepts.md).
>* [ geeft meta-gegevenseigenschappen van veelvoudige inzamelingen ](manage-collections.md#editing-collection-metadata-in-bulk) uit.
>* [ de invoer en de uitvoer van Meta-gegevens in Experience Manager Assets ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/metadata-import-export.html).
>* [ Profielen om meta-gegevens, beelden, en video&#39;s ](processing-profiles.md) te verwerken.
>* [ Beste praktijken om uw digitale activa te organiseren om verwerkingsprofielen ](/help/assets/organize-assets.md) te gebruiken.
>* [ XMP terug ](/help/assets/xmp-writeback.md).
