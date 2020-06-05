---
title: 'Metagegevensschema''s om de indeling van de pagina met eigenschappen van metagegevens te definiëren in [!DNL Adobe Experience Manager-middelen]. '
description: Het metagegevensschema definieert de indeling van de pagina met eigenschappen en de eigenschappen van metagegevens die voor elementen worden weergegeven. Leer hoe u een aangepast metagegevensschema kunt maken, het schema voor metagegevens kunt bewerken en hoe u het schema voor metagegevens op elementen kunt toepassen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 505ee267534b7b3de1f85fb6782b855dbf3c371d
workflow-type: tm+mt
source-wordcount: '2514'
ht-degree: 5%

---


# Metadata schemas {#metadata-schemas}

Organisaties beschikken over een metagegevensmodel dat de detectie, het gebruik, de interoperabiliteit enzovoort van middelen verbetert. Correcte toepassing van metagegevens is onaantastbaar voor het onderhouden van workflows en processen die zijn gebaseerd op metagegevens. Om aan organisatie-brede meta-gegevensstrategie en normen te houden, kunt u meta-gegevensschema&#39;s gebruiken die gebruikers DAM helpen zich te richten. [!DNL Adobe Experience Manager] biedt eenvoudige en flexibele methoden voor het maken, onderhouden en toepassen van metagegevensschema&#39;s.

In [!DNL Adobe Experience Manager Assets]de schema&#39;s staan specifieke velden waarin specifieke informatie moet worden ingevuld. Het bevat ook lay-outinformatie om meta-gegevensgebieden op een gebruikersvriendelijke manier te tonen. Metagegevenseigenschappen zijn onder andere titel, beschrijving, MIME-typen, tags en meer. U kunt de [!UICONTROL Metadata Schema Forms] redacteur gebruiken om de bestaande schema&#39;s te wijzigen of de schema&#39;s van douanemetagegevens toe te voegen.

Ga als volgt te werk om de pagina met eigenschappen voor een element weer te geven en te bewerken:

1. Klik op het **[!UICONTROL View Properties]** pictogram van Snelle handelingen op het element Elementen in de kaartweergave.

   ![Snelle acties voor elementblok](assets/chlimage_1-170.png)

   U kunt ook een element selecteren en vervolgens op het [!UICONTROL Properties] pictogram op de werkbalk klikken.

1. U kunt de verschillende bewerkbare eigenschappen van metagegevens bewerken onder de beschikbare tabbladen. U kunt het element echter niet wijzigen [!UICONTROL Type] op het [!UICONTROL Basic] tabblad Eigenschappen.

   ![Het tabblad Standaard van de eigenschappen van elementen, waarin het elementtype niet kan worden gewijzigd](assets/asset-properties-basic-tab.png)

*Afbeelding: Het tabblad Standaard voor elementen[!UICONTROL Properties].*

Als u het MIME-type voor een element wilt wijzigen, gebruikt u een aangepast schema voor metagegevens of wijzigt u een bestaand formulier. Zie [Metagegevensschemaformulieren](/help/assets/metadata-schemas.md#edit-metadata-schema-forms) bewerken voor meer informatie. Als u het metagegevensschema van een MIME-type wijzigt, wordt de indeling van de eigenschappenpagina voor de elementen en alle subtypen gewijzigd. Als u bijvoorbeeld een JPEG-schema wijzigt onder, wordt de indeling van metagegevens (eigenschappen van elementen) `default/image` alleen gewijzigd voor elementen met het MIME-type `image/jpeg`. Als u echter het standaardschema bewerkt, worden de wijzigingen doorgevoerd in de indeling van de metagegevens voor alle typen elementen.

## Metagegevensschema-formulieren {#default-metadata-schema-forms}

Als u een lijst met formulieren of sjablonen wilt weergeven, navigeert u in de [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.

[!DNL Experience Manager] Hier vindt u de volgende sjablonen voor metagegevensschema-formulieren.

| Sjablonen |  | Beschrijving |
|---|---|---|
| [!UICONTROL default] |  | Het basisschema voor metagegevens voor elementen. |
|  | De volgende onderliggende formulieren nemen de eigenschappen van het [!UICONTROL default] formulier over: |  |
|  | [!UICONTROL image] | Schema-formulier voor afbeeldingen van het MIME-type, zoals `image/jpeg` en `image/png`. <br> Het [!UICONTROL image] formulier heeft de volgende onderliggende formuliersjablonen: <ul><li> [!UICONTROL jpeg]: Schema voor activa met subtype [!UICONTROL jpeg].</li> <li>[!UICONTROL tiff]: Schema voor de elementen met subtype TIFF.</li></ul> |
|  | [!UICONTROL application] | Schema-formulier voor elementen met het MIME-type zoals `application/pdf` en `application/zip`. <br>[!UICONTROL pdf]: Schemaformulier voor elementen met subtype PDF. |
|  | [!UICONTROL video] | Schemaformulier voor video-elementen met het MIME-type, zoals `video/avi` en `video/mp4`. |
| [!UICONTROL collection] |  | Schemaformulier voor verzamelingen. |
| [!UICONTROL contentfragment] |  | [Schemaformulier voor inhoudsfragmenten](/help/sites-developing/customizing-content-fragments.md). |
| [!UICONTROL forms] |  | Dit schema-formulier is gerelateerd aan [Adobe Experience Manager Forms](/help/forms/home.md). |

<!-- 
TBD: Add dm_video child for the default form OOTB.
video doesn't contain any sub types as listed above OOTB.
application doesn't contain the sub type zip OOTB.
-->

>[!NOTE]
>
>Klik op de naam van het schema om de onderliggende formulieren van een schema weer te geven.

## Een metagegevensschema toevoegen {#add-a-metadata-schema-form}

Voer de volgende stappen uit om een metagegevensschema toe te voegen:

1. Als u een aangepaste sjabloon aan de lijst wilt toevoegen, klikt u op **[!UICONTROL Create]** de werkbalk.

   >[!NOTE]
   >
   >Er wordt een vergrendelingspictogram weergegeven met de onbewerkte sjablonen. Als u een sjabloon aanpast, wordt het vergrendelingspictogram niet weergegeven.

1. Geef in het dialoogvenster de titel van het schema op en klik **[!UICONTROL Create]** om het maken van het formulier te voltooien.

## Formulieren met metagegevensschema bewerken {#edit-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken. Het metagegevensschema bevat tabbladen en formulieritems binnen tabbladen. U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagruimte. U kunt tabs of formulieritems toevoegen aan het metagegevensschemaformulier. De tabbladen en formulieritems die van het bovenliggende element zijn afgeleid, bevinden zich in de vergrendelde status. U kunt deze niet wijzigen op het niveau van het kind.

1. Selecteer een formulier op de [!UICONTROL Metadata Schema Forms] pagina en klik op **[!UICONTROL Edit]** de werkbalk.

1. Pas op de **[!UICONTROL Metadata Schema Form Editor]** pagina het metagegevensformulier aan. Sleep de benodigde componenten van het **[!UICONTROL Build Form]** tabblad naar een van de tabbladen.

   ![Editor metagegevensschema om de pagina Eigenschappen van elementen aan te passen](assets/metadata-schema-editor.png)

   *Afbeelding: Een[!UICONTROL Metadata Schema Form Editor]pagina met beschikbare tabbladen.*

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het **[!UICONTROL Settings]** tabblad.

### Componenten op het [!UICONTROL Build Form] tabblad {#components-within-the-build-form-tab}

Het **[!UICONTROL Build Form]** tabblad bevat formulieritems die u in het schemaformulier gebruikt. Het **[!UICONTROL Settings]** tabblad bevat de kenmerken van elk item dat u op het **[!UICONTROL Build Form]** tabblad selecteert. De volgende tabel bevat een lijst met formulieritems die beschikbaar zijn op het **[!UICONTROL Build Form]** tabblad:

| Componentnaam | Beschrijving |
| -------------------------------- | ----------------------------------------------------------------------------------- |
| [!UICONTROL Section Header] | Voeg een sectiekopje toe voor een lijst met gangbare componenten. |
| [!UICONTROL Single Line Text] | Voeg een eigenschap voor één regel tekst toe. De eigenschap wordt opgeslagen als een tekenreeks. |
| [!UICONTROL Multi Value Text] | Voeg een teksteigenschap voor meerdere waarden toe. Deze wordt opgeslagen als een tekenreeks-array. |
| [!UICONTROL Number] | Voeg een getalcomponent toe. |
| [!UICONTROL Date] | Voeg een datumcomponent toe. |
| [!UICONTROL Dropdown] | Voeg een vervolgkeuzelijst toe. |
| [!UICONTROL Standard Tags] | Voeg een tag toe. |
| [!UICONTROL Smart Tags] | U kunt zoekmogelijkheden uitbreiden door automatisch metagegevenstags toe te voegen. |
| [!UICONTROL Hidden Field] | Voeg een verborgen veld toe. Deze wordt als een POST-parameter verzonden wanneer het element wordt opgeslagen. |
| [!UICONTROL Asset Referenced By] | Voeg deze component toe om een lijst weer te geven met elementen waarnaar door het element wordt verwezen. |
| [!UICONTROL Asset Referencing] | Toevoegen om een lijst weer te geven met elementen die naar het element verwijzen. |
| [!UICONTROL Products References] | Toevoegen om de lijst weer te geven met producten die aan het element zijn gekoppeld. |
| [!UICONTROL Asset Rating] | Toevoegen aan weergaveopties voor het beoordelen van het element. |
| [!UICONTROL Contextual Metadata] | Toevoegen om de weergave van andere tabbladen met metagegevens in de eigenschappenpagina met elementen te besturen. |

#### De metagegevenscomponent bewerken {#edit-the-metadata-component}

Als u de eigenschappen van een metagegevenscomponent in het formulier wilt bewerken, klikt u op de component om de volgende eigenschappen of een subset ervan op het **[!UICONTROL Settings]** tabblad te bewerken.

**Veldlabel**: De naam van de eigenschap metadata die wordt weergegeven op de eigenschappenpagina voor het element.

**Toewijzen aan eigenschap**: This property specifies the relative path to or name of the asset node where it is saved in the CRX repository. Het begint met `./` om aan te geven dat het pad zich onder het knooppunt van het element bevindt.

Hier volgen de geldige waarden voor deze eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metadataknooppunt van de asset opgeslagen als de eigenschap `dc:title`.

* `./jcr:created`: Hiermee slaat u de aanmaakdatum en -tijd van een element op. Het is een beschermde eigenschap. Als u deze eigenschappen configureert, kunt u deze het beste markeren als Uitschakelen, Bewerken.

Om ervoor te zorgen dat de component correct in de vorm van het meta-gegevensschema wordt getoond, zou de bezitspad geen ruimten moeten omvatten.

* **Tijdelijke aanduiding**: Gebruik deze eigenschap om relevante plaatsaanduidingstekst met betrekking tot de eigenschap metadata op te geven.
* **Vereist**: Gebruik deze eigenschap om een eigenschap metadata als verplicht op de eigenschappenpagina te markeren.
* **Bewerken** uitschakelen: Met deze eigenschap kunt u bewerkingen van een eigenschap op de eigenschappenpagina niet toestaan.
* **Leeg veld alleen**-lezen tonen: Mark this property to display a metadata property on the properties page even if it has no value. Wanneer een eigenschap metadata geen waarde heeft, wordt deze standaard niet vermeld op de eigenschappenpagina.
* **Genummerde** lijst tonen: Gebruik deze eigenschap om een geordende keuzelijst weer te geven.
* **Keuzen**: Gebruik deze eigenschap om keuzen in een lijst op te geven.
* **Omschrijving** : Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.
* **Klasse**: Objectklasse waaraan de eigenschap is gekoppeld.
* **Verwijderen**: Klik [!UICONTROL Delete] om een component uit het schemaformulier te verwijderen.

>[!NOTE]
>
>Deze kenmerken zijn niet opgenomen in de [!UICONTROL Hidden Field] component. In plaats daarvan bevat de klasse eigenschappen, zoals Naam, Waarde, Veldlabel en Beschrijving. De waarden voor de component Verborgen veld worden als een POST-parameter verzonden wanneer het element wordt opgeslagen. Deze wordt niet opgeslagen als metagegevens voor het element.

Als u de optie **[!UICONTROL Required]** selecteert, kunt u zoeken naar assets waarvoor verplichte metadata ontbreken. Vouw in het deelvenster **[!UICONTROL Filters]** het predicaat **[!UICONTROL Metadata Validation]** uit en selecteer de optie **[!UICONTROL Invalid]**. In de zoekresultaten worden assets weergegeven waarvoor verplichte metadata ontbreken die u via het schemaformulier hebt geconfigureerd.

![Ongeldige optie geselecteerd in het deelvenster Metagegevensvalidatie van het deelvenster Filters ](assets/chlimage_1-178.png)

Als u de component Contextuele metagegevens toevoegt aan een tabblad van een schemaformulier, wordt de component weergegeven als een lijst op de eigenschappenpagina van elementen waarop het specifieke schema wordt toegepast. De lijst bevat alle andere tabbladen, behalve het tabblad waarop u de component Contextuele metagegevens hebt toegepast. Momenteel biedt deze functie basisfunctionaliteit voor het beheren van de weergave van metagegevens op basis van de context.

![Tabellen met eigenschappen van elementen van de component Contextual Metadata](assets/chlimage_1-179.png)

Als u een tabblad in de eigenschappenpagina wilt weergeven naast het tabblad waarop de component Contextuele metagegevens is toegepast, selecteert u het tabblad in de lijst. Het tabblad wordt toegevoegd aan de pagina met eigenschappen.

![Het tabblad dat is geselecteerd in de lijst Contextual Metadata wordt weergegeven op de pagina met eigenschappen van elementen](assets/contextual-metadata-asset-properties.png)

*Afbeelding: Contextuele metagegevens op de pagina met eigenschappen van elementen.*

### Eigenschappen in JSON-bestand opgeven {#specify-properties-in-json-file}

In plaats van eigenschappen voor de opties op het tabblad **[!UICONTROL Settings]** op te geven, kunt u de opties in een JSON-bestand definiëren door overeenkomstige sleutel-waardeparen op te geven. Geef het pad van het JSON-bestand op in het veld **[!UICONTROL JSON Path]**.

#### Een tabblad toevoegen aan of verwijderen uit het schemaformulier {#adding-deleting-a-tab-in-the-schema-form}

Met de schema-editor kunt u een tabblad toevoegen of verwijderen. The default schema form includes the **[!UICONTROL Basic]**, **[!UICONTROL Advanced]** , **[!UICONTROL IPTC]**, and **[!UICONTROL IPTC Extension]** tabs.

![Standaardtabbladen in formulier voor metagegevensschema](assets/chlimage_1-181.png)

Klik `+` om een tabblad toe te voegen aan een schemaformulier. Standaard heeft het nieuwe tabblad de naam `Unnamed-1`. U kunt de naam wijzigen van het **[!UICONTROL Settings]** tabblad.

Klik `X` om een tabblad te verwijderen.

![Een tabblad toevoegen of verwijderen met de Editor voor een metagegevensschema](assets/chlimage_1-182.png)

## Formulieren met metagegevens verwijderen {#delete-metadata-schema-forms}

[!DNL Experience Manager] Hiermee kunt u alleen aangepaste schema-formulieren verwijderen. U kunt hiermee de standaardschema-formulieren/sjablonen niet verwijderen. U kunt echter alle aangepaste wijzigingen in deze formulieren verwijderen.

Als u een formulier wilt verwijderen, selecteert u een formulier en klikt u op Verwijderen.

>[!NOTE]
>
>* Nadat u aangepaste wijzigingen in een standaardformulier hebt verwijderd, verschijnt het vergrendelingspictogram opnieuw vóór de wijziging in de interface Metagegevensschema. Hiermee wordt aangegeven dat de standaardstatus van het formulier wordt hersteld.
>* U kunt de standaardschema-formulieren voor metagegevens niet verwijderen in [!DNL Assets].


## Schema-formulieren voor MIME-typen {#schema-forms-for-mime-types}

[!DNL Experience Manager] bevat standaardformulieren voor diverse MIME-typen uit het vak. U kunt echter aangepaste formulieren toevoegen voor elementen van verschillende MIME-typen.

### Nieuwe formulieren toevoegen voor MIME-typen {#add-new-forms-for-mime-types}

Maak een formulier onder het juiste formuliertype. For example, to add a template for the `image/png` subtype, create the form under the &quot;image&quot; forms. De titel voor het schemaformulier is de naam van het subtype. In dit geval is de titel `png`.

#### Een bestaande schemasjabloon gebruiken voor verschillende MIME-typen {#use-an-existing-schema-template-for-various-mime-types}

U kunt een bestaande sjabloon voor een ander MIME-type gebruiken. Gebruik het `image/jpeg` formulier bijvoorbeeld voor elementen van het type MIME `image/png`.

In dit geval maakt u een knooppunt in `/etc/dam/metadataeditor/mimetypemappings` de CRX-opslagplaats. Geef een naam voor het knooppunt op en definieer de volgende eigenschappen:

| Naam | Beschrijving | Type | Waarde |
|------|-------------|------|-------|
| `exposedmimetype` | Naam van het bestaande formulier dat moet worden toegewezen | `String` | `image/jpeg` |
| `mimetypes` | Lijst met MIME-typen die het formulier gebruiken dat is gedefinieerd in het `exposedmimetype` kenmerk | `String` | `image/png` |

[!DNL Assets] Hiermee worden de volgende MIME-typen en schema-formulieren toegewezen:

| Schema-formulier | MIME-typen |
| --------------------------- | --------------------------------------------------- |
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/aanverwante; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/aanverwante; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/aanverwante; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Toegang tot metagegevensschema&#39;s verlenen {#grant-access-to-metadata-schemas}

De functie Metagegevensschema is alleen beschikbaar voor beheerders. Beheerders kunnen echter toegang verlenen aan niet-beheerders door bepaalde machtigingen te wijzigen. Geef niet-beheerdergebruikers de machtigingen voor de `/conf` map op om deze te maken, te wijzigen en te verwijderen.

## Mapspecifieke metagegevens toepassen {#apply-folder-specific-metadata}

[!DNL Assets] Hiermee kunt u een variant van een metagegevensschema definiëren en dit toepassen op een specifieke map.

U kunt bijvoorbeeld een variant van het standaardmetagegevensschema definiëren en deze toepassen op een map. Wanneer u het gewijzigde schema toepast, wordt het oorspronkelijke standaardmetagegevensschema genegeerd dat op elementen in de map is toegepast.

Alleen elementen die zijn geüpload naar de map waarop dit schema is toegepast, komen overeen met de gewijzigde metagegevens die zijn gedefinieerd in het schema voor alternatieve metagegevens. [!DNL Assets] in andere mappen waarin het oorspronkelijke schema wordt toegepast, blijven de metagegevens die in het oorspronkelijke schema zijn gedefinieerd, behouden.

Metagegevensovererving door elementen is gebaseerd op het schema dat wordt toegepast op de map op het eerste niveau in de hiërarchie. Met andere woorden, als een map geen submappen bevat, nemen de elementen in de map de metagegevens over van het schema dat op de map is toegepast.

U kunt een ander schema toepassen bij de submap. De elementen in een submap overerven het metagegevensschema van de directe submap. Als er geen schema of hetzelfde schema op submapniveau wordt toegepast, nemen de elementen ervan het schema over van de bovenliggende map.

1. Navigeer in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**. De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Schakel het selectievakje in vóór een formulier, bijvoorbeeld het standaardmetagegevensformulier, en klik op het formulier **[!UICONTROL Copy]** en sla het op als een aangepast formulier. Geef bijvoorbeeld een aangepaste naam voor het formulier op `my_default`. U kunt ook een aangepast formulier maken.

1. Selecteer het **[!UICONTROL Metadata Schema Forms]** formulier op de `my_default` pagina en klik op **[!UICONTROL Edit]**.

1. Voeg op de **[!UICONTROL Metadata Schema Editor]** pagina een tekstveld toe aan het schema. Voeg bijvoorbeeld een veld met het label toe **[!UICONTROL Category]**.

   ![Tekstveld toegevoegd aan de formuliereditor voor metagegevensschema](assets/text-field-metadata-schema-editor.png)

   *Afbeelding: Tekstveld toegevoegd aan formuliereditor voor metagegevensschema.*

1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de **[!UICONTROL Metadata Schema Forms]** pagina.
1. Klik op **[!UICONTROL Apply to Folder(s)]** de werkbalk om de aangepaste metagegevens toe te passen op een map.

1. Selecteer de map waarop u het gewijzigde schema wilt toepassen en klik op **[!UICONTROL Apply]**.

   ![Map selecteren om metagegevensschema toe te passen](assets/chlimage_1-188.png)

1. Als op de map het andere metagegevensschema is toegepast, verschijnt er een waarschuwing dat u op het punt staat het bestaande metagegevensschema te overschrijven. Klik op **Overschrijven**.
1. Klik op **OK** om het succesbericht te sluiten.
1. Navigeer naar de map waarop u het gewijzigde metagegevensschema hebt toegepast.

## Verplichte metagegevens definiëren {#define-mandatory-metadata}

U kunt verplichte velden definiëren op mapniveau. Deze worden afgedwongen voor elementen die naar de map worden geüpload. Als u elementen uploadt met ontbrekende metagegevens voor de verplichte velden die u eerder hebt gedefinieerd, wordt in de kaartweergave een visuele indicatie voor ontbrekende metagegevens weergegeven.

>[!NOTE]
>
>Een metagegevensveld kan op basis van de waarde van een ander veld als verplicht worden gedefinieerd. In de kaartweergave wordt het waarschuwingsbericht over ontbrekende metagegevens voor dergelijke verplichte metagegevensvelden [!DNL Experience Manager] niet weergegeven.

1. Navigeer in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**. De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Sla het standaardmetagegevensformulier op als een aangepast formulier. Sla het bestand bijvoorbeeld op als `my_default`.

1. Bewerk het aangepaste formulier. Voeg een verplicht veld toe. Voeg bijvoorbeeld een **[!UICONTROL Category]** veld toe en maak het veld verplicht.

   ![Voeg een verplicht veld toe aan het metagegevensformulier door Vereist te selecteren op het tabblad Regels in de Formuliereditor voor metagegevensschema](assets/mandatory-field-metadata-schema-editor.png)

   *Afbeelding: Verplicht veld in formuliereditor voor metagegevensschema.*

1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de **[!UICONTROL Metadata Schema Forms]** pagina. Selecteer het formulier en klik vervolgens op **[!UICONTROL Apply to Folder(s)]** de werkbalk om de aangepaste metagegevens toe te passen op een map.

1. Navigeer naar de map en upload elementen met ontbrekende metagegevens voor het verplichte veld dat u aan het aangepaste formulier hebt toegevoegd. Op de kaartweergave van het element wordt een bericht voor de ontbrekende metagegevens van het verplichte veld weergegeven.

   ![Bericht waarin de verplichte metagegevens voor het uploaden van elementen in de map ontbreken in de weergave met de elementenkaart](assets/chlimage_1-192.png)

1. (Optioneel) Toegang `https://[aem_server]:[port]/system/console/components/`. Vorm en laat `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` component toe die door gebrek wordt onbruikbaar gemaakt. Stel een frequentie in waarmee de geldigheid van metagegevens over de elementen wordt [!DNL Experience Manager] gecontroleerd. Deze configuratie voegt een eigenschap toe `hasValidMetadata` aan `jcr:content` elementen. [!DNL Experience Manager] gebruikt deze eigenschap om de ongeldige elementen in een zoekresultaat te filteren. Als u na een controle een element toevoegt, wordt het element pas gemarkeerd met `hasValidMetadata` de volgende geplande controle. De elementen worden daarom pas na de volgende geplande controle in zoekfilters voor ongeldige metagegevens weergegeven.

   >[!CAUTION]
   >
   >De controles van de meta-gegevensbevestiging zijn middelintensief en kunnen de prestaties van uw systeem beïnvloeden. Plan de controles dienovereenkomstig. Als de server het laden niet aankan, probeert u deze taak uit te schakelen.

<!-- TBD: Add this method to find invalid metadata in the metadata.md article later when it is published as a top-level metadata article.
-->
