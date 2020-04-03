---
title: Metagegevensschema's
description: Het metagegevensschema definieert de indeling van de pagina met eigenschappen en de eigenschappen van metagegevens die voor elementen worden weergegeven. Leer hoe u een aangepast metagegevensschema kunt maken, het schema voor metagegevens kunt bewerken en hoe u het schema voor metagegevens op elementen kunt toepassen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5cbaefd5a377db5aa9f8ba35371fe2a9cb638fa1

---


# Metadata schemas {#metadata-schemas}

In de Elementen van de Manager van de Ervaring van Adobe (AEM), bepaalt een meta-gegevensschema de lay-out van de eigenschappen pagina en de meta-gegevenseigenschappen die voor activa worden getoond die het bepaalde schema gebruiken. Tot de metagegevenseigenschappen behoren titel, beschrijving, MIME-typen, tags, enzovoort.

U kunt de redacteur van de Vormen van het Schema van Meta-gegevens gebruiken om bestaande schema&#39;s te wijzigen of douanemetagegevensschema&#39;s toe te voegen.

1. Als u de eigenschappenpagina voor een element wilt weergeven, klikt of tikt u op het pictogram Eigenschappen **[!UICONTROL van]** weergave in Snelle handelingen op het element in de kaartweergave.

   ![chlimage_1-34](assets/chlimage_1-170.png)

   U kunt ook het element selecteren in de gebruikersinterface en vervolgens op het pictogram **[!UICONTROL Eigenschappen]** op de werkbalk klikken of erop tikken.

   ![chlimage_1-35](assets/chlimage_1-171.png)

1. Bewerk verschillende eigenschappen van metagegevens onder de verschillende tabbladen. U kunt het elementtype echter niet wijzigen op de eigenschappenpagina.

   ![u kunt elementtype niet wijzigen op het tabblad Standaard van de eigenschappen van elementen](assets/asset-properties-basic-tab.png)

   *Afbeelding: Het tabblad Standaard voor eigenschappen van elementen*


   Als u het MIME-type voor een element wilt wijzigen, gebruikt u een aangepast schema voor metagegevens of wijzigt u een bestaand formulier. Zie [Metagegevensschemaformulieren](/help/assets/metadata-schemas.md#edit-metadata-schema-forms) bewerken voor meer informatie. Als u het metagegevensschema voor een bepaald MIME-type wijzigt, worden de pagina-indeling van de eigenschappen voor elementen met het huidige MIME-type en alle elementsubtypen gewijzigd. Als u bijvoorbeeld een JPEG-schema wijzigt onder, wordt de indeling van metagegevens (eigenschappen van elementen) `default/image` alleen gewijzigd voor elementen met het MIME-type `image/jpeg`. Als u echter het standaardschema bewerkt, worden de wijzigingen doorgevoerd in de indeling van de metagegevens voor alle typen elementen.

1. To view a list of forms/templates, click the AEM logo and then navigate to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.

   ![chlimage_1-37](assets/chlimage_1-173.png)

   AEM verstrekt de volgende malplaatjes uit de doos:
   * **standaard**: Het basisschema voor metagegevens voor elementen.

      De volgende onderliggende formulieren nemen de eigenschappen van het standaardformulier over:

      1. **afbeelding**: Schema-formulier voor elementen met het MIME-type &#39;image&#39;, bijvoorbeeld `image/jpeg`, `image/png`enzovoort.

         Het &quot;afbeeldingsformulier&quot; heeft de volgende onderliggende formuliersjablonen:
         * **jpeg**: Schema voor activa met subtype `jpeg`.
         * **tiff**: Schema voor de activa met subtype `tiff`.
      1. **toepassing**: Schema-formulier voor elementen van het type MIME `application`, `application/pdf`bijvoorbeeld `application/zip`enzovoort.
         * **pdf**: Schema voor activa met subtype `pdf`.
      1. **video**: Schema-formulier voor elementen met het MIME-type `video`, zoals `video/avi`, `video/mp4`enzovoort.
   * **verzameling**: Schemaformulier voor verzamelingen.
   * **contentfragment:** Schemaformulier voor inhoudsfragmenten.
   * **formulieren**: Dit schema-formulier is gerelateerd aan [Adobe Experience Manager Forms](/help/forms/home.md).

>[!NOTE]
>
>Als u de onderliggende formulieren van een schema wilt weergeven, klikt of tikt u op de naam van het schema.

## Een metagegevensschema toevoegen {#add-a-metadata-schema-form}

1. Als u een aangepaste sjabloon aan de lijst wilt toevoegen, klikt u op **[!UICONTROL Maken]** op de werkbalk.

   >[!NOTE]
   >
   >Onbewerkte sjablonen hebben een vergrendelingspictogram. Als u een van de sjablonen aanpast, verdwijnt het vergrendelingspictogram voordat de sjabloon verdwijnt.

1. Voer in het dialoogvenster de titel van het schema-formulier in en klik vervolgens op **[!UICONTROL Maken]** om het maken van het formulier te voltooien.

   ![chlimage_1-38](assets/chlimage_1-174.png)

## Formulieren met metagegevensschema bewerken {#edit-metadata-schema-forms}

U kunt een nieuw of bestaand schema voor metagegevens bewerken. Het metagegevensschema bevat het volgende:

* Tabs
* Formulieritems in tabbladen.

U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagruimte.

U kunt nieuwe tabbladen of formulieritems toevoegen aan het metagegevensschemaformulier. De tabbladen en formulieritems die van het bovenliggende element zijn afgeleid, bevinden zich in de vergrendelde status. U kunt deze niet wijzigen op het niveau van het kind.

1. Schakel op de pagina Schemaformulieren het selectievakje vóór een formulier in en klik vervolgens op het pictogram Bewerken op de werkbalk.

   ![chlimage_1-39](assets/chlimage_1-175.png)

1. In the **[!UICONTROL Metadata Schema Editor]** page, customize the properties page of the asset by dragging one or more components from the list of component types in the **[!UICONTROL Build Form]** tab to the **[!UICONTROL Basic]** tab.

   ![Voeg componenten van de Vorm van de Bouwstijl aan de redacteur van het meta-gegevensschema toe om activaEigenschappen aan te passen](assets/metadata-schema-editor.png)


   *Afbeelding: Tabblad Standaard van editor voor metagegevensschema*

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **Instellingen** .

### Componenten op het tabblad Formulier samenstellen {#components-within-the-build-form-tab}

Op het tabblad **[!UICONTROL Formulier]** samenstellen worden formulieritems weergegeven die u in het schemaformulier gebruikt. Het tabblad **[!UICONTROL Instellingen]** bevat de kenmerken van elk item dat u selecteert op het tabblad **[!UICONTROL Formulier]** samenstellen. De volgende tabel bevat een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Formulier]** samenstellen:

| Componentnaam | Beschrijving |
|---|---|
| [!UICONTROL Sectiekop] | Voeg een sectiekopje toe voor een lijst met gangbare componenten. |
| [!UICONTROL Tekst met één regel] | Voeg een eigenschap voor één regel tekst toe. De eigenschap wordt opgeslagen als een tekenreeks. |
| [!UICONTROL Meerdere waardetekst] | Voeg een teksteigenschap voor meerdere waarden toe. Deze wordt opgeslagen als een tekenreeks-array. |
| [!UICONTROL Getal] | Voeg een getalcomponent toe. |
| [!UICONTROL Date] | Voeg een datumcomponent toe. |
| [!UICONTROL Vervolgkeuzelijst] | Voeg een vervolgkeuzelijst toe. |
| [!UICONTROL Standaardlabels] | Voeg een tag toe. |
| [!UICONTROL Slimme tags] | U kunt zoekmogelijkheden uitbreiden door automatisch metagegevenstags toe te voegen. |
| [!UICONTROL Verborgen veld] | Voeg een verborgen veld toe. Deze wordt als een POST-parameter verzonden wanneer het element wordt opgeslagen. |
| [!UICONTROL Door] | Voeg deze component toe om een lijst weer te geven met elementen waarnaar door het element wordt verwezen. |
| [!UICONTROL Verwijzing naar element] | Toevoegen om een lijst weer te geven met elementen die naar het element verwijzen. |
| [!UICONTROL Productverwijzingen] | Toevoegen om de lijst weer te geven met producten die aan het element zijn gekoppeld. |
| [!UICONTROL Waardering van activa] | Toevoegen aan weergaveopties voor het beoordelen van het element. |
| [!UICONTROL Contextuele metagegevens] | Toevoegen om de weergave van andere tabbladen met metagegevens in de eigenschappenpagina met elementen te besturen. |

#### De metagegevenscomponent bewerken {#edit-the-metadata-component}

Als u de eigenschappen van een metagegevenscomponent in het formulier wilt bewerken, klikt u op de component en bewerkt u alle eigenschappen of een subset van de volgende eigenschappen op het tabblad **[!UICONTROL Instellingen]** .

**Veldlabel**: De naam van de eigenschap metadata die wordt weergegeven op de eigenschappenpagina voor het element.

**Toewijzen aan eigenschap**: This property specifies the relative path/name to the asset node where it is saved in the CRX repository. Het begint met `./` omdat erop wijst dat de weg onder de knoop van het element is.

Hier volgen de geldige waarden voor deze eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metadataknooppunt van de asset opgeslagen als de eigenschap `dc:title`.

* `./jcr:created`: Geeft de JCR-eigenschap weer op het knooppunt van het element. Als u deze eigenschappen configureert op weergave-eigenschappen, raden wij aan deze te markeren als Bewerken uitschakelen, omdat deze beveiligd zijn. Otherwise, the error [!UICONTROL Asset(s) failed to modify] results when you save the asset&#39;s properties.

Om ervoor te zorgen dat de component correct in de vorm van het meta-gegevensschema wordt getoond, zou de bezitspad geen ruimten moeten omvatten.

**Tijdelijke aanduiding**: Gebruik deze eigenschap om relevante plaatsaanduidingstekst met betrekking tot de eigenschap metadata op te geven.

**Vereist**: Gebruik deze eigenschap om een eigenschap metadata als verplicht op de eigenschappenpagina te markeren.

**Bewerken** uitschakelen: Gebruik deze eigenschap om een eigenschap metadata onbewerkbaar te maken op de eigenschappenpagina.

**Leeg veld alleen**-lezen tonen: Mark this property to display a metadata property on the properties page even if it has no value. Wanneer een eigenschap metadata geen waarde heeft, wordt deze standaard niet vermeld op de eigenschappenpagina.

**Genummerde** lijst tonen: Gebruik deze eigenschap om een geordende keuzelijst weer te geven

**Keuzen**: Gebruik deze eigenschap om keuzen in een lijst op te geven

**Omschrijving** : Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.

**Klasse**: Objectklasse waaraan de eigenschap is gekoppeld.

**Verwijderen**: Klik op dit pictogram om een component uit het schema te verwijderen.

![chlimage_1-41](assets/chlimage_1-177.png)

>[!NOTE]
>
>De component Verborgen veld bevat deze kenmerken niet. In plaats daarvan bevat de klasse eigenschappen, zoals Naam, Waarde, Veldlabel en Beschrijving. De waarden voor de component Verborgen veld worden als een POST-parameter verzonden wanneer het element wordt opgeslagen. Deze wordt niet opgeslagen als metagegevens voor het element.

If you select the **[!UICONTROL Required]** option, you can search for assets missing mandatory metadata. Vouw in het deelvenster **[!UICONTROL Filters]** de voorspelling voor **[!UICONTROL metagegevensvalidatie]** uit en selecteer de optie **[!UICONTROL Ongeldig]** . In de zoekresultaten worden assets weergegeven waarvoor verplichte metadata ontbreken die u via het schemaformulier hebt geconfigureerd.

![chlimage_1-42](assets/chlimage_1-178.png)

Als u de component Contextuele metagegevens toevoegt aan een tabblad van een schemaformulier, wordt de component weergegeven als een lijst op de eigenschappenpagina van elementen waarop het specifieke schema wordt toegepast. De lijst bevat alle andere tabbladen, behalve het tabblad waarop u de component Contextuele metagegevens hebt toegepast. Momenteel biedt deze functie basisfunctionaliteit voor het beheren van de weergave van metagegevens op basis van de context.

![chlimage_1-43](assets/chlimage_1-179.png)

Als u een tabblad in de eigenschappenpagina wilt weergeven naast het tabblad waarop de component Contextuele metagegevens is toegepast, selecteert u het tabblad in de lijst. Het tabblad wordt toegevoegd aan de pagina met eigenschappen.

![Selecteer een tabblad in de lijst met contextafhankelijke metagegevens om weer te geven op de eigenschappenpagina](assets/contextual-metadata-asset-properties.png)

*Afbeelding: Contextafhankelijke metagegevens in de pagina met eigenschappen van elementen*

### Eigenschappen in JSON-bestand opgeven {#specify-properties-in-json-file}

Instead of specifying properties for the options in the **[!UICONTROL Settings]** tab, you can define the options in a JSON file by specifying corresponding key-value pairs. Specify the path of the JSON file in the **[!UICONTROL JSON Path]** field.

#### Een tabblad toevoegen aan of verwijderen uit het schemaformulier {#adding-deleting-a-tab-in-the-schema-form}

Met de schema-editor kunt u een tabblad toevoegen of verwijderen. Het standaardschema bevat standaard de tabbladen **[!UICONTROL Standaard]**, **[!UICONTROL Geavanceerd]** , **[!UICONTROL IPTC]** en **[!UICONTROL IPTC-extensie]** .

![chlimage_1-45](assets/chlimage_1-181.png)

Klik `+` om een nieuw tabblad toe te voegen aan een schemaformulier. Standaard heeft het nieuwe tabblad de naam `Unnamed-1`. U kunt de naam wijzigen op het tabblad **[!UICONTROL Instellingen]** .

Klik `X` om een tabblad te verwijderen.

![chlimage_1-46](assets/chlimage_1-182.png)

## Formulieren met metagegevens verwijderen {#delete-metadata-schema-forms}

Met AEM kunt u alleen aangepaste schema-formulieren verwijderen. U kunt hiermee de standaardschema-formulieren/sjablonen niet verwijderen. U kunt echter alle aangepaste wijzigingen in deze formulieren verwijderen.

Als u een formulier wilt verwijderen, selecteert u een formulier en klikt u op het pictogram voor verwijderen.

![chlimage_1-47](assets/chlimage_1-183.png)
<!--![chlimage_1-47](assets/chlimage_1-177.png) -->
>[!NOTE]
>
>Nadat u aangepaste wijzigingen in een standaardformulier hebt verwijderd, verschijnt het vergrendelingspictogram opnieuw vóór de aangepaste wijzigingen in het schema voor metagegevens om aan te geven dat de standaardstatus van het formulier is hersteld.

>[!NOTE]
>
>U kunt de metagegevensschema-formulieren uit het vak niet verwijderen in AEM Assets.

## Schema-formulieren voor MIME-typen {#schema-forms-for-mime-types}

AEM Assets biedt standaardformulieren voor verschillende MIME-typen uit het vak. U kunt echter aangepaste formulieren toevoegen voor elementen van verschillende MIME-typen.

### Nieuwe formulieren toevoegen voor MIME-typen {#add-new-forms-for-mime-types}

Maak een nieuw formulier onder het juiste formuliertype. Als u bijvoorbeeld een nieuwe sjabloon voor het subtype **image/png** wilt toevoegen, maakt u het formulier onder de &quot;image&quot;-formulieren. De titel voor het schemaformulier is de naam van het subtype. In dit geval is de titel &quot;png.**&quot;**

#### Een bestaande schemasjabloon gebruiken voor verschillende MIME-typen {#use-an-existing-schema-template-for-various-mime-types}

U kunt een bestaande sjabloon voor een ander MIME-type gebruiken. Gebruik het `image/jpeg` formulier bijvoorbeeld voor elementen van het type MIME `image/png`.

In dit geval maakt u een nieuw knooppunt in `/etc/dam/metadataeditor/mimetypemappings` de CRX-opslagplaats. Geef een naam voor het knooppunt op en definieer de volgende eigenschappen:

| Naam | Beschrijving | Type | Waarde |
|---|---|---|---|
| `exposedmimetype` | Naam van het bestaande formulier dat moet worden toegewezen | `String` | `image/jpeg` |
| `mimetypes` | Lijst met MIME-typen die het formulier gebruiken dat is gedefinieerd in het `exposedmimetype` kenmerk | `String` | `image/png` |

AEM-elementen wijzen de volgende MIME-typen en schema-formulieren toe:

| Schema-formulier | MIME-typen |
|---|---|
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

De functie Metagegevensschema is alleen beschikbaar voor beheerders. Beheerders kunnen echter wel toegang verlenen aan niet-beheerders door bepaalde machtigingen te wijzigen. De niet-beheerder moet beschikken over machtigingen voor het maken, wijzigen en verwijderen van de `/conf` map.

## Mapspecifieke metagegevens toepassen {#apply-folder-specific-metadata}

Met AEM-elementen kunt u een variant van een metagegevensschema definiëren en dit toepassen op een specifieke map.

U kunt bijvoorbeeld een variant van het standaardmetagegevensschema definiëren en deze toepassen op een map. Wanneer u het gewijzigde schema toepast, wordt het oorspronkelijke standaardmetagegevensschema genegeerd dat op elementen in de map is toegepast.

Alleen elementen die zijn geüpload naar de map waarop dit schema is toegepast, voldoen aan de gewijzigde metagegevens die zijn gedefinieerd in het metagegevensschema voor de variant.

Elementen in andere mappen waarop het oorspronkelijke schema is toegepast, voldoen nog steeds aan de metagegevens die in het oorspronkelijke schema zijn gedefinieerd.

Metagegevensovererving door elementen is gebaseerd op het schema dat wordt toegepast op de map op het eerste niveau in de hiërarchie. Met andere woorden, als een map geen submappen bevat, nemen de elementen in de map de metagegevens over van het schema dat op de map is toegepast.

Als de map een submap heeft, nemen de elementen in de submap de metagegevens over van het schema dat op submapniveau wordt toegepast als een ander schema op submapniveau wordt toegepast. Als echter geen schema of hetzelfde schema wordt toegepast op submapniveau, overerven de submapelementen de metagegevens van het schema dat is toegepast op het niveau van de bovenliggende map.

1. Klik op het AEM-logo en navigeer naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]** > **[!UICONTROL Metagegevensschema&#39;s]**. De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Schakel het selectievakje in vóór een formulier, bijvoorbeeld het standaardmetagegevensformulier, en klik op het pictogram Kopiëren of tik op het pictogram en sla het op als een aangepast formulier. Geef bijvoorbeeld een aangepaste naam voor het formulier op `my_default`. U kunt ook een aangepast formulier maken.
   ![chlimage_1-184](assets/chlimage_1-184.png)

1. Selecteer het **[!UICONTROL formulier op de pagina]** Metagegevensschema-formulieren `my_default` en klik op het pictogram **[!UICONTROL Bewerken]** .

   ![chlimage_1-49](assets/chlimage_1-185.png)

1. Voeg op de pagina **[!UICONTROL Metadata Schema Editor]** een tekstveld toe aan het schema. Voeg bijvoorbeeld een veld met de **[!UICONTROL categorie]** Label toe.

   ![een tekstveld toevoegen aan een formuliereditor voor metagegevens](assets/text-field-metadata-schema-editor.png)

   *Afbeelding: Tekstveld toegevoegd aan formuliereditor voor metagegevensschema*

1. Click **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]** .
1. Klik/tik op **[!UICONTROL Toepassen op map(pen)]** op de werkbalk om de aangepaste metagegevens toe te passen op een map.

   ![chlimage_1-51](assets/chlimage_1-187.png)

1. Selecteer de map waarop u het gewijzigde schema wilt toepassen en klik op **[!UICONTROL Toepassen]**.

   ![chlimage_1-52](assets/chlimage_1-188.png)

1. Als op de map het andere metagegevensschema is toegepast, verschijnt er een waarschuwing dat u op het punt staat het bestaande metagegevensschema te overschrijven. Klik op **Overschrijven**.
1. Klik op **OK** om het succesbericht te sluiten.
1. Navigeer naar de map waarop u het gewijzigde metagegevensschema hebt toegepast.

## Verplichte metagegevens definiëren {#define-mandatory-metadata}

U kunt verplichte velden definiëren op mapniveau. Deze worden afgedwongen voor elementen die naar de map worden geüpload. Als u elementen uploadt met ontbrekende metagegevens voor de verplichte velden die u eerder hebt gedefinieerd, wordt een visuele indicatie voor ontbrekende metagegevens weergegeven in de weergave Kaart.

>[!NOTE]
>
>Een metagegevensveld kan op basis van de waarde van een ander veld als verplicht worden gedefinieerd. In de kaartweergave geeft AEM geen waarschuwingsbericht weer over ontbrekende metagegevens voor dergelijke verplichte metagegevensvelden.

1. Klik op het AEM-logo en navigeer naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]** > **[!UICONTROL Metagegevensschema&#39;s]**. De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Sla het standaardmetagegevensformulier op als een aangepast formulier. Sla het bestand bijvoorbeeld op als `my_default`.

   ![chlimage_1-53](assets/chlimage_1-189.png)

1. Bewerk het aangepaste formulier. Voeg een verplicht veld toe. Voeg bijvoorbeeld een veld **[!UICONTROL Categorie]** toe en maak het veld verplicht.

   ![veld toevoegen aan het metagegevensformulier en Vereist selecteren op het tabblad Regels om dit verplicht te maken](assets/mandatory-field-metadata-schema-editor.png)

   *Afbeelding: Verplicht veld in formuliereditor voor metagegevens*

1. Click **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]** . Selecteer het formulier en klik of tik op **[!UICONTROL Toepassen op map(pen)]** op de werkbalk om de aangepaste metagegevens toe te passen op een map.

   ![chlimage_1-55](assets/chlimage_1-191.png)

1. Navigeer naar de map en upload elementen met ontbrekende metagegevens voor het verplichte veld dat u aan het aangepaste formulier hebt toegevoegd. Er wordt een bericht voor de ontbrekende metagegevens van het verplichte veld weergegeven in de kaartweergave van het element.

   ![chlimage_1-56](assets/chlimage_1-192.png)

1. (Optioneel) Toegang `https://[server]:[port]/system/console/components/`. Vorm en laat `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` component toe die door gebrek wordt onbruikbaar gemaakt. Stel een frequentie in waarmee AEM controleert of metagegevens over de elementen geldig zijn.

   Deze configuratie voegt een eigenschap toe `hasValidMetadata` aan `jcr:content` elementen. Met deze eigenschap kan AEM resultaten in een zoekopdracht filteren.

   >[!NOTE]
   >
   >Als een element wordt toegevoegd na de geplande controle, wordt het element pas gemarkeerd met `hasValidMetadata` de volgende geplande controle. De elementen worden niet weergegeven in tussenliggende zoekresultaten.

   >[!CAUTION]
   >
   >De controles van de meta-gegevensbevestiging zijn middelintensief en kunnen de prestaties van uw systeem beïnvloeden. Plan de controles dienovereenkomstig. Als de server het laden niet aankan, probeert u deze taak uit te schakelen.
