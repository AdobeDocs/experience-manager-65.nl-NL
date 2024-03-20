---
title: Elementeditorpagina's maken en configureren
description: Leer hoe u aangepaste pagina's in de Asset Editor kunt maken en meerdere middelen tegelijk kunt bewerken.
contentOwner: AG
role: User, Admin
feature: Developer Tools,Asset Management
exl-id: 53e310a9-c511-447a-91bd-8c5b2760dc03
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2068'
ht-degree: 0%

---

# Elementeditorpagina&#39;s maken en configureren {#creating-and-configuring-asset-editor-pages}

In dit document wordt het volgende beschreven:

* Waarom zou u aangepaste pagina&#39;s in de Editor van middelen maken?
* Pagina&#39;s in de Asset Editor maken en aanpassen. Dit zijn WCM-pagina&#39;s waarmee u metagegevens kunt weergeven en bewerken en acties kunt uitvoeren op het element.
* Meerdere elementen tegelijk bewerken.

<!-- TBD: Add UICONTROL tags. Need PM review. Flatten the structure a bit. Re-write to remove Geometrixx mentions and to adhere to 6.5 default samples. -->

>[!NOTE]
>
>Asset Share is beschikbaar als een open-source referentie-implementatie. Zie [Commentaar voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/). Het wordt niet officieel gesteund.

## Waarom de pagina&#39;s van de Redacteur van Activa creëren en vormen? {#why-create-and-configure-asset-editor-pages}

Digital Asset Management wordt in meer scenario&#39;s gebruikt. Bij de overgang van een kleinschalige oplossing voor een kleine gebruikersgroep professionele gebruikers - bijvoorbeeld fotografen of taxonomisten - naar grotere en meer gevarieerde gebruikersgroepen - zoals zakelijke gebruikers, WCM-auteurs en journalisten - is de krachtige gebruikersinterface van [!DNL Adobe Experience Manager Assets] kan te veel informatie verstrekken. Belanghebbenden vragen om specifieke gebruikersinterfaces of toepassingen voor toegang tot de digitale middelen die voor hen van belang zijn.

Deze asset-centric toepassingen kunnen eenvoudige fotogalerieën in een Intranet zijn waar de werknemers foto&#39;s van handelsshowbezoeken of een perscentrum in een openbaar-onder ogen ziende website kunnen uploaden. Asset-centric toepassingen kunnen ook worden uitgebreid tot complete oplossingen, zoals winkelwagentjes, kassa&#39;s en verificatieprocessen.

Het creëren van een middel-centric toepassing wordt een configuratieproces dat geen codering vereist, slechts kennis van gebruikersgroepen en hun behoeften en kennis van de meta-gegevens die worden gebruikt. Asset-centric toepassingen die zijn gemaakt met [!DNL Assets] zijn uitbreidbaar: met een matige codeerinspanning kunnen opnieuw bruikbare componenten voor het zoeken, weergeven en wijzigen van elementen worden gemaakt.

Een toepassing die op elementen is gericht in [!DNL Experience Manager] bestaat uit een pagina Asset Editor, die kan worden gebruikt voor een gedetailleerde weergave van een specifiek element. Een pagina van de Redacteur van Activa staat ook voor het uitgeven van meta-gegevens toe, op voorwaarde dat de gebruiker die tot de activa toegang heeft de noodzakelijke toestemmingen heeft.

<!--
## Create and configure an Asset Share page {#creating-and-configuring-an-asset-share-page}

You customize the DAM Finder functionality and create pages that have all the functionality you require, which are called Asset Share pages. To create an Asset Share page, you add the page using the Geometrixx Asset Share template and then you customize the actions users can perform on that page, determine how viewers see the assets, and decide how users can build their queries.

Here are some use cases for creating a customized Asset Share page:

* Press Center for Journalists.
* Image Search Engine for internal business users.
* Image Database for website users.
* Media Tagging Interface for metadata editors.

### Create an Asset Share page {#creating-an-asset-share-page}

To create an Asset Share page, you can either create it when you are working on web sites or from the digital asset manager.

>[!NOTE]
>
>By default, when you create an Asset Share page from **New** in the digital asset manager, an Asset viewer and Asset editor are automatically created for you.

To create an new Asset Share page in the **Websites** console:

1. In the **Websites** tab, navigate to the place where you want to create an asset share page and click **New**.

1. Select the **Asset Share** page and click **Create**. The new page is created and the asset share page is listed in the **Websites** tab.

![dam8](assets/dam8.png)

The basic page created using the Geometrixx DAM Asset Share template looks as follows:

![screen_shot_2012-04-18at115456am](assets/screen_shot_2012-04-18at115456am.png)

To customize your Asset Share page, you use elements from the sidekick and you also edit query builder properties. The page **Geometrixx Press Center** is a customized version of a page based on this template:

![screen_shot_2012-04-19at123048pm](assets/screen_shot_2012-04-19at123048pm.png)

To create an asset share page by way of the digital asset manager:

1. In the digital asset manager, in **New**, select **New Asset Share**.
1. In the **Title**, enter the name of the asset share page. If desired, enter a name for the URL.

   ![screen_shot_2012-04-19at23626pm](assets/screen_shot_2012-04-19at23626pm.png)

1. Double-click the asset share page to open it and configure the page.

   ![screen_shot_2012-04-19at24114pm](assets/screen_shot_2012-04-19at24114pm.png)

   By default, when you create an Asset Share page from **New**, an Asset viewer and Asset editor are automatically created for you.

#### Customize actions {#customizing-actions}

You can determine what actions users can perform on selected digital assets from a selection of predefined actions.

To add actions to the Asset Share page:

1. In the Asset Share page that you want to customize, click **Actions** in the sidekick.

The following actions are available:

 | Action | Description |
 |---|---|
 | [!UICONTROL Delete Action] | Users can delete the selected assets. |
 | [!UICONTROL Download Action] | Lets users download selected assets to their computers. |
 | [!UICONTROL Lightbox Action] | Saves assets to a "lightbox"   where you can perform other actions on them. This comes in handy when working   with assets across multiple pages. The lightbox can also be used as a   shopping cart for assets. |
 | [!UICONTROL Move Action] | Users can move the asset to another   location |
 | [!UICONTROL Tags Action] | Lets users add tags to selected assets |
 | [!UICONTROL View Asset Action] | Opens the asset in the Asset editor for   user manipulation. |

1. Drag the appropriate action to the **Actions** area on the page. Doing so creates a button that is used to execute that action.

![chlimage_1-159](assets/chlimage_1-387.png)

#### Determine how search results are presented {#determining-how-search-results-are-presented}

You determine how results are displayed from a predefined list of lenses.

To change how search results are viewed:

1. In the Asset Share page that you want to customize, click Search.

![chlimage_1](assets/assetshare3.png)

1. Drag the appropriate lens to the top center of the page. In the Press Center, the lenses are already available. Users press the appropriate lens icon to display search results as desired.

The following lenses are available:

| Lens | Description |
|---|---|
| **[!UICONTROL List Lens]** |Presents the assets in a list fashion with details. |
| **[!UICONTROL Mosaic Lens]** |Presents assets in a mosaic fashion. |

#### Mosaic Lens {#mosaic-lens}

![chlimage_1-160](assets/chlimage_1-388.png)

#### List Lens {#list-lens}

![chlimage_1-161](assets/chlimage_1-389.png)

#### Customize the Query Builder {#customizing-the-query-builder}

The query builder lets you enter search terms and create content for the Asset Share page. When you edit the query builder, you also get to determine how many search results are displayed per page, which asset editor opens when you double-click an asset, the path the query searches, and customizes nodetypes.

To customize the query builder:

1. In the Asset Share page that you want to customize, click **Edit** in the Query Builder. By default, the **General** tab opens.
1. Select the number of results per page, the path of the asset editor (if you have a customized asset editor) and the Actions title.

![screen_shot_2012-04-23at15055pm](assets/screen_shot_2012-04-23at15055pm.png)

1. Click the **Paths** tab. Enter a path or multiple paths that the search will run. These paths are overwritten if the user uses the Paths predicate.

![screen_shot_2012-04-23at15150pm](assets/screen_shot_2012-04-23at15150pm.png)

1. Enter another node type, if desired.

1. In the **Query Builder URL** field, you can override or wrap the query builder and enter the new servlet URLs with the existing query builder component. In the **Feed URL** field, you can override the Feed URL as well.

![screen_shot_2012-04-23at15313pm](assets/screen_shot_2012-04-23at15313pm.png)

1. In the **Text** field, enter the text you want to appear for results and page numbers of results. Click **OK** when finished making changes.

![screen_shot_2012-04-23at15300pm](assets/screen_shot_2012-04-23at15300pm.png)

#### Add predicates {#adding-predicates}

Experience Manager Assets includes several predicates that you can add to the Asset Share page. These let your users further narrow searches. In some cases, they may override a query builder parameter (for example, the Path parameter).

To add predicates:

1. In the Asset Share page that you want to customize, click **Search**.

![assetshare3](assets/assetshare3.png)

1. Drag the appropriate predicates to the Asset Share page underneath the query builder. Doing so creates the appropriate fields.

![assetshare4](assets/assetshare4.png)

The following predicates are available:

| Predicate | Description |
|---|---|
| **[!UICONTROL Date Predicate]** |Lets users search for assets that were modified before and after certain dates. |
| **[!UICONTROL Options Predicate]** |The site owner can specify a property to search for (as in the property predicate, for example, cq:tags) and a content tree to populate the options from (for example, the tag tree). Doing so generates a list of options where the users can select the values (tags) that the selected property (tag property) should have. This predicate lets you build list controls like the list of tags, file types, image orientations, and so on. It is great for a fixed set of options. |
| **[!UICONTROL Path Predicate]** |Lets users define the path and subfolders, if desired. |
| **[!UICONTROL Property Predicate]** |The site owner specifies a property to search for, for example, tiff:ImageLength and the user can then enter a value, for example, 800. This returns all images that are 800 pixels high. Useful predicate if your property can have arbitrary values. |

For more information, see the [predicate Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/package-summary.html).

1. To configure the predicate further, double-click it. For example, when you open the Path Predicate, you need to assign the root path.

![screen_shot_2012-04-23at15640pm](assets/screen_shot_2012-04-23at15640pm.png)
-->

## Een pagina voor de Editor van middelen maken en configureren {#creating-and-configuring-an-asset-editor-page}

U kunt de Editor van middelen aanpassen om te bepalen hoe gebruikers de digitale elementen kunnen weergeven en bewerken. Hiertoe maakt u een pagina in de Editor van middelen en past u vervolgens de weergaven en acties aan die gebruikers op die pagina kunnen uitvoeren.

>[!NOTE]
>
>Als u aangepaste velden wilt toevoegen aan de DAM Asset Editor, voegt u nieuwe `cq:Widget` knooppunten naar `/apps/dam/content/asseteditors.`

### Een pagina voor de Editor van middelen maken {#creating-the-asset-editor-page}

Als u de pagina Asset Editor maakt, is het verstandig de pagina direct onder de pagina Asset Share te maken.

Een pagina voor de Editor van middelen maken:

1. In de **[!UICONTROL Websites]** , navigeert u naar de plaats waar u de pagina Asset Editor wilt maken en klikt u op **Nieuw**.
1. Selecteren **Geometrixx-itemeditor** en klik op **Maken**. De nieuwe pagina wordt gemaakt en de pagina wordt weergegeven in het dialoogvenster **Websites** tab.

![screen_shot_2012-04-23at15858pm](assets/screen_shot_2012-04-23at15858pm.png)

De basispagina die is gemaakt met de sjabloon Geometrixx Asset Editor ziet er als volgt uit:

![assetshare5](assets/assetshare5.png)

Als u de pagina Asset Editor wilt aanpassen, gebruikt u elementen van de assistent. De pagina Asset Editor die wordt geopend via de **Geometrixx Press Center** is een aangepaste versie van een pagina die op deze sjabloon is gebaseerd:

![assetshare6](assets/assetshare6.png)

#### Een Asset Editor instellen om te openen vanaf een pagina voor het delen van elementen {#setting-which-asset-editor-opens-from-an-asset-share-page}

Nadat u de aangepaste pagina Asset Editor hebt gemaakt, dient u ervoor te zorgen dat de elementen op de aangepaste pagina Editor worden geopend wanneer u dubbelklikt op elementen die met Delen van element zijn aangepast.

De pagina Asset Editor instellen:

1. Klik op de pagina Asset Share op **Bewerken** naast de Query Builder.

![screen_shot_2012-04-23at20123pm](assets/screen_shot_2012-04-23at20123pm.png)

1. Klik op de knop **Algemeen** als deze nog niet is geselecteerd.

1. In de **Pad van de Asset Editor** Voer het pad naar de Asset Editor in waarin de pagina Asset Share elementen moet openen en klik op **OK**.

![screen_shot_2012-04-23at21653pm](assets/screen_shot_2012-04-23at21653pm.png)

#### Elementbewerkingscomponenten toevoegen {#adding-asset-editor-components}

U bepaalt welke functionaliteit een Redacteur van Activa door componenten aan de pagina toe te voegen heeft.

Elementbewerkingscomponenten toevoegen:

1. Selecteer op de pagina Asset Editor die u wilt aanpassen **Asset Editor** in het hulpje. Alle beschikbare componenten van de Asset Editor worden weergegeven.

>[!NOTE]
>
>Wat u kunt aanpassen, hangt af van welke componenten beschikbaar zijn. Als u componenten wilt inschakelen, gaat u naar de ontwerpmodus en selecteert u de onderdelen die u wilt inschakelen.

1. Sleep de componenten van het hulpstuk aan de Redacteur van Activa en maak om het even welke veranderingen in de de dialoogvakjes van de componentendialoog aan. De componenten worden beschreven in de volgende lijst en in de gedetailleerde instructies beschreven die volgen.

>[!NOTE]
>
>Bij het ontwerpen van de pagina Asset Editor maakt u componenten die alleen-lezen of bewerkbaar zijn. Gebruikers weten dat een veld kan worden bewerkt als een afbeelding van een potlood in die component wordt weergegeven. Standaard worden de meeste componenten ingesteld als alleen-lezen.

| Component | Beschrijving |
|---|---|
| **[!UICONTROL Metadata Form]en[!UICONTROL Metadata Text Field]** | Hiermee kunt u aanvullende metagegevens aan een element toevoegen en een handeling op dat element uitvoeren, zoals verzenden. |
| **[!UICONTROL Sub Assets]** | Hiermee kunt u subelementen aanpassen. |
| **Tags** | Gebruikers kunnen tags selecteren en aan een element toevoegen. |
| **[!UICONTROL Thumbnail]** | Toont een duimnagel van het element, zijn filename, en laat u een afwisselende tekst toevoegen. U kunt ook hier de acties in de Asset Editor toevoegen. |
| **[!UICONTROL Title]** | Hiermee geeft u de titel van het element weer, die kan worden aangepast. |

![screen_shot_2012-04-23at2743pm](assets/screen_shot_2012-04-23at22743pm.png)

#### Metagegevensformulier en tekstveld - De component Metagegevens weergeven configureren {#metadata-form-and-text-field-configuring-the-view-metadata-component}

Het metagegevensformulier is een formulier met een begin- en eindactie. Tussen haakjes voert u in **Tekst** velden. Zie [Forms](/help/sites-authoring/default-components-foundation.md#form-component) voor meer informatie over het werken met formulieren.

1. Een startactie maken door op **Bewerken** in het gebied Start van het formulier. U kunt desgewenst een titel voor een vak invoeren. Standaard is de titel van het vak **Metagegevens**. Schakel het selectievakje Clientvalidatie in als u de JavaScript-clientcode voor validatie wilt genereren.

![screen_shot_2012-04-23at22911pm](assets/screen_shot_2012-04-23at22911pm.png)

1. Een actie Einde maken door op **Bewerken** in het gebied Einde van het formulier. U kunt bijvoorbeeld een **[!UICONTROL Submit]** optie om gebruikers toe te staan hun meta-gegevensveranderingen voor te leggen. U kunt desgewenst een **Herstellen** optie waarmee de metagegevens worden teruggezet naar de oorspronkelijke staat.

![screen_shot_2012-04-23at23138pm](assets/screen_shot_2012-04-23at23138pm.png)

1. In tussen de **Begin formulier** en de **Einde formulier** Sleep Metagegevenstekstvelden naar het formulier. Gebruikers vullen metagegevens in deze tekstvelden in. Deze kunnen worden verzonden of een andere actie uitvoeren.

1. Dubbelklik bijvoorbeeld op de veldnaam. **Titel** om het metagegevensveld te openen en wijzigingen aan te brengen. In de **Algemeen** tabblad van het **Component bewerken** , definieert u bijvoorbeeld de naamruimte en het veldlabel en type. `dc:title`.

![screen_shot_2012-04-23at23305pm](assets/screen_shot_2012-04-23at23305pm.png)

Zie [Elementen aanpassen en uitbreiden](/help/assets/extending-assets.md) voor informatie over het wijzigen van de naamruimten in het metagegevensformulier.

1. Klik op de knop **Restricties** tab. Hier kunt u selecteren of een veld vereist is en zo nodig beperkingen toevoegen.

![screen_shot_2012-04-23at23435pm](assets/screen_shot_2012-04-23at23435pm.png)

1. Klik op de knop **Weergave** tab. Hier kunt u een nieuwe breedte en een nieuw aantal rijen voor het meta-gegevensgebied ingaan. Selecteer de **Veld is alleen-lezen** Schakel het selectievakje in om gebruikers de metagegevens te laten bewerken.

![screen_shot_2012-04-23at23446pm](assets/screen_shot_2012-04-23at23446pm.png)

Hieronder ziet u een voorbeeld van een metagegevensformulier met verschillende velden:

![metagegevens](assets/chlimage_1-390.png)

Op de pagina Asset Editor kunnen gebruikers vervolgens waarden invoeren in de metagegevensvelden (als deze bewerkbaar zijn) en de eindactie uitvoeren (bijvoorbeeld door de wijzigingen te verzenden).

#### Subactiva {#sub-assets}

In de component Subelementen kunt u subelementen weergeven en selecteren. U kunt bepalen welke namen onder de [hoofdmiddel](/help/assets/assets.md#what-are-digital-assets) en subactiva.

Dubbelklik op de component Subelementen zodat u het dialoogvenster Subelementen kunt openen waarin u de titels voor het hoofdelement en eventuele subelementen kunt wijzigen. De standaardwaarden worden onder het desbetreffende veld weergegeven.

![screen_shot_2012-04-23at23907pm](assets/screen_shot_2012-04-23at23907pm.png)

Hieronder ziet u een voorbeeld van een onderdeel van een subelement dat is gevuld:

![screen_shot_2012-04-23at24442pm](assets/screen_shot_2012-04-23at24442pm.png)

Als u bijvoorbeeld een subelement selecteert, ziet u hoe de component de juiste pagina weergeeft en hoe de titel van het vak verandert van Subelementen in Siblings.

![screen_shot_2012-04-23at24552pm](assets/screen_shot_2012-04-23at24552pm.png)

#### Tags {#tags}

De component Tags is een component waarin gebruikers bestaande tags aan een element kunnen toewijzen. Hierdoor kunnen gebruikers de elementen later ordenen en ophalen. U kunt van deze component alleen-lezen maken, zodat gebruikers geen codes kunnen toevoegen, maar alleen deze weergeven.

![screen_shot_2012-04-23at25031pm](assets/screen_shot_2012-04-23at25031pm.png)

Dubbelklik op de component Tags, zodat u het dialoogvenster Codes kunt openen waarin u desgewenst de titel van Codes kunt wijzigen en waarin u de toegewezen naamruimten kunt selecteren. Als u dit veld bewerkbaar wilt maken, wist u het dialoogvenster **[!UICONTROL Hide Edit]** selectievakje. Standaard zijn codes bewerkbaar.

![screen_shot_2012-04-23at24731pm](assets/screen_shot_2012-04-23at24731pm.png)

Als gebruikers tags kunnen bewerken, kunnen ze op het potlood klikken om tags toe te voegen door deze te selecteren in het vervolgkeuzemenu Codes.

![screen_shot_2012-04-23at25150pm](assets/screen_shot_2012-04-23at25150pm.png)

Hier volgt een gevulde component Tags:

![screen_shot_2012-04-23at25244pm](assets/screen_shot_2012-04-23at25244pm.png)

#### Miniatuur {#thumbnail}

In het element Miniatuur wordt de geselecteerde miniatuur weergegeven (bij veel van de indelingen wordt de miniatuur automatisch geëxtraheerd). Bovendien geeft de component de bestandsnaam weer, en [acties die u kunt wijzigen](/help/assets/assets-finder-editor.md#adding-asset-editor-actions).

![screen_shot_2012-04-23at25452pm](assets/screen_shot_2012-04-23at25452pm.png)

Dubbelklik op de miniatuurcomponent zodat u het dialoogvenster met miniaturen kunt openen waarin u de alt-tekst kunt wijzigen. Standaard wordt de alt-tekst van de miniatuur ingesteld op **Klik om te downloaden** activa.

![screen_shot_2012-04-23at25604pm](assets/screen_shot_2012-04-23at25604pm.png)

Hieronder ziet u een voorbeeld van een gevulde miniatuurcomponent:

![screen_shot_2012-04-23at34815pm](assets/screen_shot_2012-04-23at34815pm.png)

#### Titel {#title}

In de component Title worden de titel van het element en een beschrijving weergegeven.

Standaard bevindt het bestand zich in de modus Alleen-lezen, zodat gebruikers het bestand niet kunnen bewerken. Als u de component bewerkbaar wilt maken, dubbelklikt u op de component en wist u de **Knop Bewerken verbergen** selectievakje. Voer bovendien een titel in voor meerdere elementen.

![screen_shot_2012-04-23at35100pm](assets/screen_shot_2012-04-23at35100pm.png)

Als de titel kan worden bewerkt, kunt u een titel en een beschrijving toevoegen door op het potlood te klikken om het dialoogvenster **Eigenschappen van element** venster. Bovendien kunt u het element in- en uitschakelen door de datum en tijd te selecteren.

Bij het bewerken van de [!UICONTROL Title], kunnen gebruikers de **Titel**, **Beschrijving** en voert u **Aan** en **Uit-tijden** om het actief in- en uit te schakelen.

![screen_shot_2012-04-23at35241pm](assets/screen_shot_2012-04-23at35241pm.png)

Hier volgt een voorbeeld van een gevulde component Title:

![chlimage_1-164](assets/chlimage_1-392.png)

#### Acties in de Asset Editor toevoegen {#adding-asset-editor-actions}

U kunt bepalen welke handelingen gebruikers op geselecteerde digitale elementen kunnen uitvoeren op basis van een selectie vooraf gedefinieerde handelingen.

Handelingen toevoegen aan de pagina Asset Editor:

1. Klik op de pagina Asset Editor die u wilt aanpassen **Asset Editor** in het hulpje.

![screen_shot_2012-04-23at35515pm](assets/screen_shot_2012-04-23at35515pm.png)

De volgende acties zijn beschikbaar:

| Handeling | Beschrijving |
|---|---|
| [!UICONTROL Download] | Hiermee kunnen gebruikers geselecteerde elementen downloaden naar hun computers. |
| [!UICONTROL Editors] | Gebruikers kunnen een afbeelding bewerken (interactief bewerken) |
| [!UICONTROL Lightbox] | Hiermee slaat u elementen op in een &#39;lichtbak&#39; waar u andere handelingen op kunt uitvoeren. Dit is handig wanneer u met elementen op meerdere pagina&#39;s werkt. |
| [!UICONTROL Locking] | Hiermee kunnen gebruikers een element vergrendelen. Deze functionaliteit is niet standaard ingeschakeld en moet zijn ingeschakeld in de lijst met componenten. |
| [!UICONTROL References] | Klik hierop om te tonen op welke pagina&#39;s het element wordt gebruikt. |
| [!UICONTROL Versioning] | Hiermee kunt u versies van een element maken en herstellen. |

1. Sleep de gewenste actie naar de **Handelingen** op de pagina. Er wordt een optie gemaakt waarmee de handeling wordt uitgevoerd die op de pagina wordt gesleept.

![chlimage_1-165](assets/chlimage_1-393.png)

## Elementen bewerken via de pagina Asset Editor {#multi-editing-assets-with-the-asset-editor-page}

Met [!DNL Experience Manager Assets]kunt u meerdere elementen tegelijk wijzigen. Nadat u de elementen hebt geselecteerd, kunt u tegelijkertijd tags en metagegevens wijzigen.

Elementen bewerken via de pagina Asset Editor:

1. De Geometrixx openen **Press Center** pagina:
   `https://localhost:4502/content/geometrixx/en/company/press.html`

1. Selecteer de elementen:

   * in Windows: `Ctrl + click` elk element.
   * op Mac: `Cmd + click` elk element.

   U selecteert een reeks elementen door op het eerste element te klikken en vervolgens `Shift + click` het laatste activum.

1. Klikken **Metagegevens bewerken** in de **Handelingen** veld (linkergedeelte van de pagina).
1. De Geometrixx **Midden-middeleneditor openen** wordt geopend in een nieuw tabblad. De metagegevens van de elementen worden als volgt weergegeven:

   * Een label-dat niet op alle activa maar slechts op slechts enkelen van toepassing is - wordt getoond in cursief.
   * Een label dat op alle elementen van toepassing is, wordt met een normaal lettertype weergegeven.
   * Andere metagegevens dan labels: de waarde van het veld wordt alleen weergegeven als deze voor alle geselecteerde elementen gelijk is.

1. Klikken **Downloaden** om een ZIP-bestand te downloaden dat de elementen van de oorspronkelijke uitvoeringen bevat.
1. Klik op de optie Tags bewerken naast de optie **Tags** veld.

   * Een tag die niet van toepassing is op alle elementen, maar alleen op een paar elementen, heeft een grijze achtergrond.
   * Een tag die op alle elementen van toepassing is, heeft een witte achtergrond.

   U kunt:

   * Klikken `x` om de tag voor alle elementen te verwijderen.
   * Klikken `+` om de tag aan alle elementen toe te voegen.
   * Klik op de knop **pijl** en selecteer een tag om een nieuwe tag aan alle elementen toe te voegen.

   Klikken **OK** om de wijzigingen in het formulier te schrijven. De doos naast **Tags** wordt automatisch gecontroleerd.

1. Bewerk het veld Beschrijving. Stel deze bijvoorbeeld in op:

   `This is a common description`

   Wanneer een veld wordt bewerkt, overschrijft de waarde de bestaande waarden van de geselecteerde elementen wanneer het formulier wordt verzonden.

   Opmerking: het vak naast het veld wordt automatisch ingeschakeld wanneer het veld wordt bewerkt.

1. Klikken **Metagegevens bijwerken** het formulier verzenden en de wijzigingen voor alle elementen opslaan.

   Opmerking: alleen de geselecteerde metagegevens worden gewijzigd.
