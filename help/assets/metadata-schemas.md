---
title: Metagegevensschema's definiëren de indeling van de pagina met eigenschappen van metagegevens
description: Het metagegevensschema definieert de indeling van de pagina met eigenschappen en de eigenschappen van metagegevens die voor elementen worden weergegeven. Leer hoe u een aangepast metagegevensschema kunt maken, het schema voor metagegevens kunt bewerken en hoe u het schema voor metagegevens op elementen kunt toepassen.
contentOwner: AG
mini-toc-levels: 1
role: User,Admin
feature: Metadata
exl-id: 0dd322cd-ce97-4335-825d-71f72a5e438c
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3408'
ht-degree: 5%

---

# Metagegevensschema&#39;s {#metadata-schemas}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/metadata-schemas.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Organisaties beschikken over een metagegevensmodel dat de detectie, het gebruik, de interoperabiliteit, enzovoort van middelen verbetert. Correcte toepassing van metagegevens is onaantastbaar om workflows met metagegevens en processen te behouden. Om aan organisatie-brede meta-gegevensstrategie en normen te houden, kunt u meta-gegevensschema&#39;s gebruiken die gebruikers DAM helpen zich te richten. Met [!DNL Adobe Experience Manager] kunt u gemakkelijk en flexibel metagegevensschema&#39;s maken, onderhouden en toepassen.

In [!DNL Adobe Experience Manager Assets] bevatten schema&#39;s specifieke velden waarin specifieke informatie moet worden ingevuld. Het bevat ook lay-outinformatie om meta-gegevensgebieden op een gebruikersvriendelijke manier te tonen. Metagegevenseigenschappen zijn onder andere titel, beschrijving, MIME-typen, tags en meer. U kunt de [!UICONTROL Metadata Schema Forms] redacteur gebruiken om de bestaande schema&#39;s te wijzigen of douanemetagegevensschema&#39;s toe te voegen.

Ga als volgt te werk om de pagina met eigenschappen voor een element weer te geven en te bewerken:

1. Klik op de optie **[!UICONTROL View Properties]** van de snelle handelingen op het element element in de kaartweergave. Alternatief, selecteer een activa en klik dan **[!UICONTROL Properties]** ![&#x200B; meningseigenschappen &#x200B;](assets/do-not-localize/info-circle-icon.png) van de toolbar.

1. U kunt de verschillende bewerkbare eigenschappen van metagegevens bewerken onder de beschikbare tabbladen. U kunt het element [!UICONTROL Type] echter niet wijzigen op het tabblad [!UICONTROL Basic] met eigenschappen.

   ![&#x200B; Basis lusje van activaEigenschappen, waar activa type niet kan worden veranderd &#x200B;](assets/asset-properties-basic-tab.png)

   *Cijfer: Basis lusje op activa [!UICONTROL Properties].*

   Zorg ervoor dat slechts één eigenschap aan een veld wordt toegewezen terwijl u het metagegevensschema maakt of bewerkt.

   Als u het MIME-type voor een element wilt wijzigen, gebruikt u een aangepast schema voor metagegevens of wijzigt u een bestaand formulier. Zie [&#x200B; Forms van het Schema van Meta-gegevens &#x200B;](#edit-metadata-schema-forms) voor meer informatie uitgeven. Als u het metagegevensschema van een MIME-type wijzigt, wordt de indeling van de eigenschappenpagina voor de elementen en alle subtypen gewijzigd. Als u bijvoorbeeld een JPEG-schema wijzigt onder `default/image` , wordt alleen de indeling van metagegevens (eigenschappen van elementen) gewijzigd voor elementen met het MIME-type `image/jpeg` . Als u echter het standaardschema bewerkt, worden de wijzigingen doorgevoerd in de indeling van de metagegevens voor alle typen elementen.

## Metagegevensschema-formulieren {#default-metadata-schema-forms}

Als u een lijst met formulieren of sjablonen wilt weergeven, navigeert u in de interface van [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .

[!DNL Experience Manager] bevat de volgende sjablonen voor metagegevensschema-formulieren.

| Sjablonen | | Beschrijving |
|---|---|---|
| [!UICONTROL default] | | Het basisschema voor metagegevens voor elementen. |
| | De volgende onderliggende formulieren nemen de eigenschappen van het [!UICONTROL default] -formulier over: | |
| | <ul><li>[!UICONTROL dm_video]</li></ul> | Schema voor Dynamic Media-video&#39;s. |
| | <ul><li>[!UICONTROL image]</li></ul> | Schema voor afbeeldingen van het MIME-type, zoals `image/jpeg` en `image/png` . <br> Het [!UICONTROL image] -formulier heeft de volgende onderliggende formuliersjablonen: <ul><li> [!UICONTROL jpeg]: schema voor elementen met subtype [!UICONTROL jpeg] .</li> <li>[!UICONTROL tiff]: schema voor de elementen met subtype TIFF.</li></ul> |
| | <ul><li>[!UICONTROL application]</li></ul> | Schema-formulier voor elementen met het MIME-type, zoals `application/pdf` en `application/zip` . <br>[!UICONTROL pdf]: Schema voor elementen met subtype PDF. |
| | <ul><li>[!UICONTROL video]</li></ul> | Schema-formulier voor video-elementen van het type MIME, zoals `video/avi` en `video/mp4` . |
| [!UICONTROL collection] | | Schema voor verzamelingen. |
| [!UICONTROL contentfragment] | | [&#x200B; vorm van het Schema voor inhoudsfragmenten &#x200B;](/help/sites-developing/customizing-content-fragments.md). |
| [!UICONTROL forms] | | Deze schemavorm heeft op [&#x200B; Adobe Experience Manager Forms &#x200B;](/help/forms/using/introduction-aem-forms.md) betrekking. |
| [!UICONTROL ugc_contentfragment] | | Schemaformulier voor door de gebruiker gegenereerde inhoudsonderdelen en elementen die via sociale media in de Experience Manager zijn geïntegreerd. |

>[!NOTE]
>
>Klik op de naam van het schema om de onderliggende formulieren van een schema weer te geven.

## Een metagegevensschema toevoegen {#add-a-metadata-schema-form}

Ga als volgt te werk om een metagegevensschemaformulier toe te voegen:

1. Als u een aangepaste sjabloon aan de lijst wilt toevoegen, klikt u op **[!UICONTROL Create]** op de werkbalk.

   >[!NOTE]
   >
   >Er wordt een vergrendelingssymbool weergegeven met de onbewerkte sjablonen. Als u een malplaatje aanpast, is het niet gesloten ![&#x200B; slot gesloten &#x200B;](assets/do-not-localize/lock_closed_icon.svg).

1. Geef in het dialoogvenster de titel van het schema op en klik op **[!UICONTROL Create]** om het maken van het formulier te voltooien.

## Formulieren met metagegevensschema bewerken {#edit-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken. Het metagegevensschema bevat tabbladen en formulieritems binnen tabbladen. U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagplaats. U kunt tabs of formulieritems toevoegen aan het metagegevensschema. De tabbladen en formulieritems die van het bovenliggende element zijn afgeleid, bevinden zich in de vergrendelde status. U kunt deze niet wijzigen op het niveau van het kind.

1. Selecteer een formulier op de [!UICONTROL Metadata Schema Forms] -pagina en klik op **[!UICONTROL Edit]** in de werkbalk.

1. Pas het metagegevensformulier aan op de pagina **[!UICONTROL Metadata Schema Form Editor]** . Sleep de benodigde componenten van de tab **[!UICONTROL Build Form]** naar een van de tabbladen.

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **[!UICONTROL Settings]** .

### Componenten op het tabblad [!UICONTROL Build Form] {#components-within-the-build-form-tab}

Het tabblad **[!UICONTROL Build Form]** bevat formulieritems die u in het schemaformulier gebruikt. Het tabblad **[!UICONTROL Settings]** bevat de kenmerken van elk item dat u selecteert op het tabblad **[!UICONTROL Build Form]** . De volgende tabel bevat een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Build Form]** :

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

Als u de eigenschappen van een metagegevenscomponent in het formulier wilt bewerken, klikt u op de component om de volgende eigenschappen (of een subset ervan) op het tabblad **[!UICONTROL Settings]** geheel of gedeeltelijk te bewerken. Het wordt aanbevolen slechts één veld toe te wijzen aan een bepaalde eigenschap in het metagegevensschema. Anders wordt het laatst toegevoegde veld dat aan de eigenschap is toegewezen, door het systeem gekozen.

**Etiket van het Gebied**: De naam van het meta-gegevensbezit dat op de eigenschappen pagina voor de activa wordt getoond.

**Kaart aan Bezit**: Dit bezit specificeert de relatieve weg aan of naam van de activaknoop waar het in de bewaarplaats van CRX wordt bewaard. Het begint met `./` om aan te geven dat het pad zich onder het knooppunt van het element bevindt.

Hier volgen voorbeelden van geldige waarden voor een eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metadataknooppunt van de asset opgeslagen als de eigenschap `dc:title`.

* `./jcr:created`: slaat de aanmaakdatum en -tijd van een element op. Het is een beschermde eigenschap. Als u deze eigenschappen configureert, wordt u aangeraden deze te markeren als Uitschakelen en bewerken. Anders treedt de fout &quot;Wijzigen van asset(s)&quot; op wanneer u de eigenschappen van de asset opslaat.

Om ervoor te zorgen dat de component correct in de vorm van het meta-gegevensschema wordt getoond, zou de bezitspad geen ruimten moeten omvatten.

* **Placeholder**: Gebruik dit bezit om relevante placeholder tekst betreffende het meta-gegevensbezit te specificeren.
* **Vereist**: Gebruik dit bezit om een meta-gegevensbezit als verplicht op de eigenschappen pagina te merken.
* **maak** onbruikbaar uit: Gebruik dit bezit om het even welke uitgeeft aan een bezit op de eigenschappen pagina niet toe te staan.
* **toon Leeg Gebied in Gelezen slechts**: Teken dit bezit om een meta-gegevensbezit op de eigenschappen pagina te tonen zelfs als het geen waarde heeft. Wanneer een eigenschap metadata geen waarde heeft, wordt deze standaard niet vermeld op de eigenschappenpagina.
* **toon geordende lijst**: Gebruik dit bezit om een geordende lijst van keuzen te tonen.
* **Keuzen**: Gebruik dit bezit om keuzen in een lijst te specificeren.
* **Beschrijving**: Gebruik dit bezit om een korte beschrijving voor de meta-gegevenscomponent toe te voegen.
* **Klasse**: De klasse van objecten het bezit wordt geassocieerd met.
* **Schrapping**: Klik [!UICONTROL Delete] om een component van de schemavorm te schrappen.

>[!NOTE]
>
>De component [!UICONTROL Hidden Field] bevat deze kenmerken niet. In plaats daarvan bevat de klasse eigenschappen, zoals Naam, Waarde, Veldlabel en Beschrijving. De waarden voor de component Verborgen veld worden als een POST-parameter verzonden wanneer het element wordt opgeslagen. Deze wordt niet opgeslagen als metagegevens voor het element.

Als u de optie **[!UICONTROL Required]** selecteert, kunt u zoeken naar assets waarvoor verplichte metadata ontbreken. Vouw in het deelvenster **[!UICONTROL Filters]** het predicaat **[!UICONTROL Metadata Validation]** uit en selecteer de optie **[!UICONTROL Invalid]**. In de zoekresultaten worden assets weergegeven waarvoor verplichte metadata ontbreken die u via het schemaformulier hebt geconfigureerd.

![&#x200B; Optie die in het predikaat van de Bevestiging van Meta-gegevens van het paneel van Filters wordt geselecteerd &#x200B;](assets/invalid-metadata-predicate.png)

Als u de component Contextuele metagegevens toevoegt aan een tabblad van een schemaformulier, wordt de component weergegeven als een lijst op de eigenschappenpagina van elementen waarop het specifieke schema wordt toegepast. De lijst bevat alle andere tabbladen, behalve het tabblad waarop u de component Contextuele metagegevens hebt toegepast. Momenteel biedt deze functie basisfunctionaliteit voor het beheren van de weergave van metagegevens op basis van de context.

![&#x200B; Contextafhankelijke de lijst van meta-gegevenscomponenten van activa eigenschappen &#x200B;](assets/metadata-contextual-component-list.png)

Als u een tabblad in de eigenschappenpagina wilt weergeven naast het tabblad waarop de component Contextuele metagegevens is toegepast, selecteert u het tabblad in de lijst. Het tabblad wordt toegevoegd aan de pagina met eigenschappen.

![&#x200B; het lusje dat op contextuele meta-gegevenslijst wordt geselecteerd wordt getoond op de pagina van activa eigenschappen &#x200B;](assets/contextual-metadata-asset-properties.png)

*Cijfer: Contextafhankelijke meta-gegevens in activa eigenschappen pagina.*

### Eigenschappen in JSON-bestand opgeven {#specify-properties-in-json-file}

In plaats van eigenschappen voor de opties op het tabblad **[!UICONTROL Settings]** op te geven, kunt u de opties in een JSON-bestand definiëren door overeenkomstige sleutel-waardeparen op te geven. Geef het pad van het JSON-bestand op in het veld **[!UICONTROL JSON Path]**.

#### Een tabblad toevoegen aan of verwijderen uit het schemaformulier {#adding-deleting-a-tab-in-the-schema-form}

Met de schema-editor kunt u een tabblad toevoegen of verwijderen. Het standaardschema bevat de tabbladen **[!UICONTROL Basic]** , **[!UICONTROL Advanced]** , **[!UICONTROL IPTC]** en **[!UICONTROL IPTC Extension]** .

Klik op `+` om een tabblad toe te voegen aan een schemaformulier. Standaard heeft het nieuwe tabblad de naam `Unnamed-1` . U kunt de naam wijzigen via het tabblad **[!UICONTROL Settings]** . Klik op `X` om een tab te verwijderen.

![&#x200B; voeg of schrap een lusje toe gebruikend de Redacteur van het Schema van Meta-gegevens &#x200B;](assets/metadata-schema-form-new-tab.png)

## Trapsgewijze metagegevens {#cascading-metadata}

Wanneer gebruikers de metagegevens van een element vastleggen, verschaffen ze informatie in de verschillende beschikbare velden. U kunt specifieke metagegevensvelden of veldwaarden weergeven die afhankelijk zijn van de opties die in de andere velden zijn geselecteerd. Een dergelijke voorwaardelijke weergave van metagegevens wordt trapsgewijze metagegevens genoemd. Met andere woorden, u kunt een afhankelijkheid maken tussen een bepaald metagegevensveld/een bepaalde waarde en een of meer velden en/of hun waarden.

Gebruik schema&#39;s voor metagegevens om regels voor de weergave van trapsgewijze metagegevens te definiëren. Als uw metagegevensschema bijvoorbeeld een elementtypeveld bevat, kunt u een relevante set velden definiëren die moet worden weergegeven op basis van het type element dat de gebruiker selecteert.

>[!CAUTION]
>
>Cascading metadata wordt niet ondersteund voor Content Fragments.

Hier volgen enkele gebruiksgevallen waarvoor u trapsgewijze metagegevens kunt definiëren:

* Indien een gebruikerslocatie is vereist, relevante plaatsnaam weergeven op basis van de keuze van het land en de staat van de gebruiker.
* Laad relevante merknamen in een lijst op basis van de door de gebruiker gekozen productcategorie.
* Schakel de zichtbaarheid van een bepaald veld in of uit op basis van de waarde die in een ander veld is opgegeven. Geef bijvoorbeeld afzonderlijke velden voor het verzendadres weer als de gebruiker de verzending op een ander adres wil laten uitvoeren.
* Wijs een veld aan als verplicht op basis van de waarde die in een ander veld is opgegeven.
* Opties wijzigen die voor een bepaald veld worden weergegeven op basis van de waarde die in een ander veld is opgegeven.
* Stel de standaardwaarde voor metagegevens in een bepaald veld in op basis van de waarde die in een ander veld is opgegeven.

### Metagegevens met trapsgewijze opmaak configureren in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Overweeg een scenario waarin u trapsgewijze metagegevens wilt weergeven op basis van het geselecteerde type element. Enkele voorbeelden

* Geef voor een video toepasselijke velden weer, zoals indeling, codec, duur, enzovoort.
* Voor een Word- of PDF-document geeft u velden weer, zoals het aantal pagina&#39;s, de auteur, enzovoort.

Geef de copyrightinformatie, ongeacht het gekozen elementtype, weer als een verplicht veld.

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .
1. Selecteer op de pagina **[!UICONTROL Schema Forms]** een schema en klik vervolgens op **[!UICONTROL Edit]** in de werkbalk om het schema te bewerken.

   ![&#x200B; select_form &#x200B;](assets/select_form.png)

1. (Optioneel) Maak in de Schema-editor voor metagegevens een veld dat u wilt conditionaliseren. Geef een naam- en eigenschapspad op het tabblad **[!UICONTROL Settings]** op.

   Als u een tabblad wilt maken, klikt u op `+` om een tabblad toe te voegen en voegt u vervolgens een metagegevensveld toe.

   ![&#x200B; add_tab &#x200B;](assets/add_tab.png)

1. Voeg een vervolgkeuzeveld toe voor het elementtype. Geef een naam- en eigenschapspad op het tabblad **[!UICONTROL Settings]** op. Voeg een optionele beschrijving toe.

   ![&#x200B; asset_type_field &#x200B;](assets/asset_type_field.png)

1. Sleutelwaardeparen zijn de opties die aan een gebruiker van een formulier worden verstrekt. U kunt de sleutel-waardeparen of manueel of van een JSON- dossier verstrekken.

   * Als u de waarden handmatig wilt opgeven, selecteert u **[!UICONTROL Add Manually]** , klikt u op **[!UICONTROL Add Choice]** en geeft u de optietekst en -waarde op. U kunt bijvoorbeeld de elementtypen Video, PDF, Word en Afbeelding opgeven.

   * Als u de waarden van een JSON-bestand dynamisch wilt ophalen, selecteert u **[!UICONTROL Add Through JSON Path]** en geeft u het pad van het JSON-bestand op. [!DNL Experience Manager] haalt de sleutel-waardeparen in real time op wanneer het formulier aan de gebruiker wordt getoond.

   Beide opties sluiten elkaar uit. U kunt de opties niet importeren uit een JSON-bestand en handmatig bewerken.

   ![&#x200B; add_choice &#x200B;](assets/add_choice.png)

   >[!NOTE]
   >
   >Wanneer u een JSON-bestand toevoegt, worden de sleutel-waardeparen niet weergegeven in de Schema-editor voor metagegevens, maar wel in het gepubliceerde formulier.

   >[!NOTE]
   >
   >Als u keuzen toevoegt en op het veld Vervolgkeuzelijst klikt, wordt de interface vervormd en worden de keuzen niet meer verwijderd. Klik niet op de vervolgkeuzelijst totdat u de wijzigingen opslaat. Sla het schema op en open het opnieuw om door te gaan met bewerken als dit probleem zich voordoet.

1. (Optioneel) Voeg de andere vereiste velden toe. U kunt bijvoorbeeld de indeling, codec en duur van de video met het elementtype opgeven.

   Op dezelfde manier voegt u afhankelijke velden toe voor andere elementtypen. Voeg bijvoorbeeld het aantal velden en de auteur van de pagina toe voor documentelementen, zoals PDF- en Word-bestanden.

   ![&#x200B; video_dependent_fields &#x200B;](assets/video_dependent_fields.png)

1. Als u een afhankelijkheid wilt maken tussen het elementtypeveld en andere velden, kiest u het afhankelijke veld en opent u het tabblad **[!UICONTROL Rules]** .

   ![&#x200B; select_dependentfield &#x200B;](assets/select_dependentfield.png)

1. Kies onder **[!UICONTROL Requirement]** de optie **[!UICONTROL Required, based on new rule]**.
1. Klik op **[!UICONTROL Add Rule]** en kies het veld **[!UICONTROL Asset Type]** om een afhankelijkheid te maken. Kies ook de veldwaarde waarop u de afhankelijkheid wilt maken. Kies in dit geval **[!UICONTROL Video]**. Klik op **[!UICONTROL Done]** om de wijzigingen op te slaan.

   ![&#x200B; define_rule &#x200B;](assets/define_rule.png)

   >[!NOTE]
   >
   >U kunt regels gebruiken voor vervolgkeuzelijsten met handmatig vooraf gedefinieerde waarden. Vervolgkeuzemenu&#39;s met geconfigureerd JSON-pad kunnen niet worden gebruikt met regels die vooraf gedefinieerde waarden gebruiken om voorwaarden toe te passen. Als de waarden bij uitvoering vanuit JSON worden geladen, is het niet mogelijk een vooraf gedefinieerde regel toe te passen.

1. Kies onder **[!UICONTROL Visibility]** de optie **[!UICONTROL Visible, based on new rule]**.

1. Klik op **[!UICONTROL Add Rule]** en kies het veld **[!UICONTROL Asset Type]** om een afhankelijkheid te maken. Kies ook de veldwaarde waarop u de afhankelijkheid wilt maken. Kies in dit geval **[!UICONTROL Video]**. Klik op **[!UICONTROL Done]** om de wijzigingen op te slaan.

   ![&#x200B; define_visibilityrule &#x200B;](assets/define_visibilityrule.png)

   >[!NOTE]
   >
   >Als u op een witruimte klikt (of op een andere plaats dan de waarden), worden de waarden opnieuw ingesteld. Als dit gebeurt, selecteert u de waarden opnieuw.

   >[!NOTE]
   >
   >U kunt de voorwaarde **[!UICONTROL Requirement]** en de voorwaarde **[!UICONTROL Visibility]** onafhankelijk van elkaar toepassen.

1. Maak op dezelfde manier een afhankelijkheid tussen de waarde Video in het veld Type element en andere velden, zoals Codec en Duur.
1. Herhaal de stappen om documentelementen (PDF en Word) in het veld [!UICONTROL Asset Type] en velden zoals [!UICONTROL Page Count] en [!UICONTROL Author] afhankelijk te maken.
1. Klik op **[!UICONTROL Save]**. Pas het metagegevensschema toe op een map.

1. Navigeer naar de map waarop u het metagegevensschema hebt toegepast en open de pagina met eigenschappen van een element. Afhankelijk van uw keuze in het veld Type element worden relevante trapsgewijze metagegevensvelden weergegeven.

   ![&#x200B; Cascading meta-gegevens voor Video activa &#x200B;](assets/video_asset.png)

   *Cijfer: Cascading metadata voor een video.*

   ![&#x200B; Cascading meta-gegevens voor documentactiva &#x200B;](assets/doc_type_fields.png)

   *Cijfer: Cascading metadata voor een document.*

## Formulieren met metagegevens verwijderen {#delete-metadata-schema-forms}

Met [!DNL Experience Manager] kunt u alleen aangepaste schema-formulieren verwijderen. U kunt hiermee de standaardschema-formulieren/sjablonen niet verwijderen. U kunt echter alle aangepaste wijzigingen in deze formulieren verwijderen.

Als u een formulier wilt verwijderen, selecteert u een formulier en klikt u op Verwijderen.

>[!NOTE]
>
>* Nadat u douaneveranderingen in een standaardvorm schrapt, sluit het slot ![&#x200B; gesloten &#x200B;](assets/do-not-localize/lock_closed_icon.svg) opnieuw verschijnt vóór de vorm. Hiermee wordt aangegeven dat de standaardstatus van het formulier wordt hersteld.
>* U kunt de standaardformulieren voor het metagegevensschema niet verwijderen in [!DNL Assets] .

## Schema-formulieren voor MIME-typen {#schema-forms-for-mime-types}

[!DNL Experience Manager] bevat standaardformulieren voor verschillende MIME-typen uit het vak. U kunt echter aangepaste formulieren toevoegen voor elementen van verschillende MIME-typen.

### Nieuwe formulieren toevoegen voor MIME-typen {#add-new-forms-for-mime-types}

Maak een formulier onder het juiste formuliertype. Als u bijvoorbeeld een sjabloon voor het subtype `image/png` wilt toevoegen, maakt u het formulier onder de &quot;afbeeldingsformulieren&quot;. De titel voor het schemaformulier is de naam van het subtype. In dit geval is de titel `png` .

#### Een bestaande schemasjabloon gebruiken voor verschillende MIME-typen {#use-an-existing-schema-template-for-various-mime-types}

U kunt een bestaande sjabloon voor een ander MIME-type gebruiken. Gebruik bijvoorbeeld het formulier `image/jpeg` voor elementen van het MIME-type `image/png` .

In dit geval maakt u een knooppunt op `/etc/dam/metadataeditor/mimetypemappings` in de CRX-opslagplaats. Geef een naam voor het knooppunt op en definieer de volgende eigenschappen:

| Naam | Beschrijving | Type | Waarde |
|------|-------------|------|-------|
| `exposedmimetype` | Naam van het bestaande formulier dat moet worden toegewezen | `String` | `image/jpeg` |
| `mimetypes` | Lijst met MIME-typen die het formulier gebruiken dat is gedefinieerd in het kenmerk `exposedmimetype` | `String` | `image/png` |

[!DNL Assets] wijst de volgende MIME-typen en schema-formulieren toe:

| Schema | MIME-typen |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Toegang tot metagegevensschema&#39;s verlenen {#grant-access-to-metadata-schemas}

De functie Metagegevensschema is alleen beschikbaar voor beheerders. Beheerders kunnen echter toegang verlenen aan niet-beheerders door bepaalde machtigingen te wijzigen. Geef niet-beheerders de machtigingen voor de map `/conf` op voor het maken, wijzigen en verwijderen van machtigingen.

## Mapspecifieke metagegevens toepassen {#apply-folder-specific-metadata}

Met [!DNL Assets] kunt u een variant van een metagegevensschema definiëren en dit toepassen op een specifieke map.

U kunt bijvoorbeeld een variant van het standaardmetagegevensschema definiëren en deze toepassen op een map. Wanneer u het gewijzigde schema toepast, wordt het oorspronkelijke standaardmetagegevensschema genegeerd dat op elementen in de map is toegepast.

Alleen elementen die zijn geüpload naar de map waarop dit schema is toegepast, komen overeen met de gewijzigde metagegevens die zijn gedefinieerd in het schema voor alternatieve metagegevens. [!DNL Assets] in andere mappen waar het oorspronkelijke schema wordt toegepast, blijven de metagegevens die zijn gedefinieerd in het oorspronkelijke schema in acht nemen.

Metagegevensovererving door elementen is gebaseerd op het schema dat wordt toegepast op de map op het hoogste niveau in de hiërarchie. Hetzelfde schema wordt toegepast op of overgeërfd door de submappen. Als een ander schema op submapniveau wordt toegepast, stopt de overerving.

1. Navigeer in de interface van [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** . De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Schakel het selectievakje in vóór een formulier, bijvoorbeeld het standaardmetagegevensformulier, en klik op **[!UICONTROL Copy]** en sla het op als een aangepast formulier. Geef een aangepaste naam voor het formulier op, bijvoorbeeld `my_default` . U kunt ook een aangepast formulier maken.

1. Selecteer op de pagina **[!UICONTROL Metadata Schema Forms]** het `my_default` -formulier en klik vervolgens op **[!UICONTROL Edit]** .

1. Voeg op de pagina **[!UICONTROL Metadata Schema Editor]** een tekstveld toe aan het schema. Voeg bijvoorbeeld een veld met het label **[!UICONTROL Category]** toe.

   ![&#x200B; gebied van de Tekst dat aan de Redacteur van de Vorm van het Schema van Meta-gegevens wordt toegevoegd &#x200B;](assets/text-field-metadata-schema-editor.png)

   *Cijfer: Het gebied van de tekst dat aan de redacteur van de de vormvorm van het meta-gegevensschema wordt toegevoegd.*

1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]** .
1. Klik op **[!UICONTROL Apply to Folder(s)]** op de werkbalk om de aangepaste metagegevens toe te passen op een map.

1. Selecteer de map waarop u het gewijzigde schema wilt toepassen en klik op **[!UICONTROL Apply]** .

   ![&#x200B; Uitgezochte omslag om het Schema van Meta-gegevens toe te passen &#x200B;](assets/metadata-schema-select-folder.png)

1. Als op de map het andere metagegevensschema is toegepast, verschijnt er een waarschuwing dat u het bestaande metagegevensschema wilt overschrijven. Klik **overschrijven**.
1. Klik **O.K.** om het succesbericht te sluiten.
1. Navigeer naar de map waarop u het gewijzigde metagegevensschema hebt toegepast.

## Verplichte metagegevens definiëren {#define-mandatory-metadata}

U kunt verplichte velden definiëren op mapniveau. Deze worden afgedwongen voor elementen die naar de map worden geüpload. Als u elementen uploadt met ontbrekende metagegevens voor de verplichte velden die u eerder hebt gedefinieerd, wordt in de kaartweergave een visuele indicatie voor ontbrekende metagegevens weergegeven.

>[!NOTE]
>
>Een metagegevensveld kan op basis van de waarde van een ander veld als verplicht worden gedefinieerd. In de kaartweergave geeft [!DNL Experience Manager] geen waarschuwingsbericht weer over ontbrekende metagegevens voor dergelijke verplichte metagegevensvelden.

1. Navigeer in de interface van [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** . De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Sla het standaardmetagegevensformulier op als een aangepast formulier. Sla het bestand bijvoorbeeld op als `my_default` .

1. Bewerk het aangepaste formulier. Voeg een verplicht veld toe. Voeg bijvoorbeeld een veld **[!UICONTROL Category]** toe en maak het veld verplicht.

   ![&#x200B; voeg verplicht gebied aan meta-gegevensvorm toe door Vereist in het lusje van Regels in de Redacteur van de Vorm van het Schema van Meta-gegevens te selecteren &#x200B;](assets/mandatory-field-metadata-schema-editor.png)

   *Cijfer: Verplicht gebied in de redacteur van de de vormvorm van meta-gegevensschema.*

1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]** . Selecteer het formulier en klik op **[!UICONTROL Apply to Folder(s)]** op de werkbalk om de aangepaste metagegevens toe te passen op een map.

1. Navigeer naar de map en upload elementen met ontbrekende metagegevens voor het verplichte veld dat u aan het aangepaste formulier hebt toegevoegd. Op de kaartweergave van het element wordt een bericht voor de ontbrekende metagegevens van het verplichte veld weergegeven.

   ![&#x200B; Bericht voor ontbrekende verplichte meta-gegevens op de mening van de activakaart bij het uploaden van activa in omslag &#x200B;](assets/metadata-missing-info-card-view.png)

1. (Optioneel) Toegang `https://[aem_server]:[port]/system/console/components/` . Configureer en schakel `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` in die standaard is uitgeschakeld. Stel een frequentie in waarmee [!DNL Experience Manager] controleert of metagegevens over de elementen geldig zijn. Deze configuratie voegt een eigenschap `hasValidMetadata` toe aan `jcr:content` elementen. [!DNL Experience Manager] gebruikt deze eigenschap om de ongeldige elementen in een zoekresultaat te filteren. Als u na een controle een element toevoegt, wordt het element pas bij de volgende geplande controle gemarkeerd met `hasValidMetadata` . De elementen worden daarom pas na de volgende geplande controle in zoekfilters voor ongeldige metagegevens weergegeven.

   >[!CAUTION]
   >
   >De controles van de meta-gegevensbevestiging zijn middelintensief en kunnen de prestaties van uw systeem beïnvloeden. Plan de controles dienovereenkomstig. Als de server het laden niet aankan, probeert u deze taak uit te schakelen.

<!-- TBD: Add this method to find invalid metadata in the metadata.md article later when it is published as a top-level metadata article.
-->
