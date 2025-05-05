---
title: Algemene eCommerce beheren
description: De AEM generische oplossing verstrekt methodes om de handelsinformatie te beheren die binnen de bewaarplaats wordt gehouden.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
docset: aem65
exl-id: c29f6213-1df6-45af-91c8-14b255276d82
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '2907'
ht-degree: 0%

---

# Algemene eCommerce beheren {#administering-generic-ecommerce}

De generische oplossing van Adobe Experience Manager (AEM) verstrekt methodes om de handelsinformatie te beheren die binnen de bewaarplaats wordt gehouden (in tegenstelling tot het gebruiken van een externe e-commerce motor). Dit omvat:

* [Producten](/help/commerce/cif-classic/administering/concepts.md#products)
* [Productvarianten](/help/commerce/cif-classic/administering/concepts.md#product-variants)
* [Catalogi](/help/commerce/cif-classic/administering/concepts.md#catalogs)
* [Aanbiedingen](/help/commerce/cif-classic/administering/concepts.md#promotions)
* [Vouchers](/help/commerce/cif-classic/administering/concepts.md#vouchers)
* [Orders](/help/commerce/cif-classic/administering/concepts.md#shopping-cart-and-orders)
* [Proxypagina&#39;s](/help/commerce/cif-classic/administering/concepts.md#proxy-pages)

>[!NOTE]
>
>De standaard AEM installatie omvat de generieke implementatie van de eCommerce van de AEM (JCR).
>
>Dit is bedoeld voor demonstratiedoeleinden of als de basis voor een aangepaste implementatie volgens uw vereisten.

## Producten en productvariaties {#products-and-product-variations}

>[!NOTE]
>
>De volgende procedures zijn van toepassing op zowel producten als productvariaties.

Alvorens producten tot stand te brengen, bepaal a [ steigers ](/help/sites-authoring/scaffolding.md). Hiermee geeft u de velden op die u moet definiëren, de producten en hoe deze worden bewerkt.

Voor elk afzonderlijk producttype is een steiger nodig. Het geschikte substraat wordt met de producten geassocieerd door:

* pad
* het product kan verwijzen naar het substraat

>[!NOTE]
>
>De winkel Geometrixx-Buiten heeft één productsoort (en dus één enkel substraat):
>
>`/etc/scaffolding/geometrixx-outdoors`
>
>Het producttype Geometrixx-Buiten is actief op:
>
>`/etc/commerce/products/geometrixx-outdoors`
>
>U kunt een productdefinitie overal onder dat punt zonder enige extra opstelling tot stand brengen.

### Producten importeren {#importing-products}

#### Producten importeren - Voor aanraking geoptimaliseerde gebruikersinterface {#importing-products-touch-optimized-ui}

1. Navigeer aan de **Producten** console, via **Commerce**.
1. Gebruikend de **Producten** console navigeert aan de vereiste plaats.
1. Gebruik het **pictogram van de Producten van de Invoer** om de tovenaar te openen.

   ![ het pictogram van de Producten van de Invoer ](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. Geef het volgende op:

   * **Importeur**

     De importer voor de specifieke [ handelsleverancier ](/help/commerce/cif-classic/administering/concepts.md#commerce-providers), door gebrek `Geometrixx`.

   * **Source**

     Het bestand dat u wilt importeren; u kunt de browser gebruiken om een bestand te selecteren.

   * **Incrementele Invoer**

     Geef aan of dit een incrementele invoer is (in tegenstelling tot volledige invoer).

   >[!NOTE]
   >
   >De incrementele invoer (van de voorbeeldgeometrixx-outdoorimporteur) vindt plaats op productniveau.
   >
   >Een aangepaste importmodule kan zo worden gedefinieerd dat deze naar wens kan werken.

1. Selecteer **daarna** om de producten in te voeren, wordt een logboek van de genomen acties getoond.

   >[!NOTE]
   >
   >De producten worden geïmporteerd naar of ten opzichte van de huidige locatie.

   >[!NOTE]
   >
   >Het herhaaldelijk gebruiken van **daarna** en **terug** voert herhaaldelijk de productdefinities in. Nochtans, aangezien zij zelfde SKUs hebben, wordt de informatie die in de bewaarplaats bestaat overschreven.

1. Selecteer **Gedaan** om de tovenaar te sluiten.

#### Producten importeren - Klassieke UI {#importing-products-classic-ui}

1. Gebruikend de **console van Hulpmiddelen** opent de **Commerce** omslag.
1. Dubbelklik om de **Importeur van het Product** te openen:

   ![ Console van de Importeur van het Product ](/help/sites-administering/assets/chlimage_1-22.jpeg)

1. Geef het volgende op:

   * **Naam van de Opslag**

     Producten worden geïmporteerd naar:

     `/etc/commerce/products/<*store name*>/`

   * **Commerce Provider**

     Importeur voor uw [ handelsleverancier ](/help/commerce/cif-classic/administering/concepts.md#commerce-providers); door gebrek Geometrixx.

   * **het Dossier van Source**

     De locatie in de opslagplaats van het bestand dat u wilt importeren.

   * **Incrementele Invoer**

     Geef aan of dit een incrementele invoer is (in tegenstelling tot volledige invoer).

1. Klik **de Producten van de Invoer**.

### Productinformatie maken {#creating-product-information}

>[!NOTE]
>
>Het standaardproductbeheer is van fundamenteel belang, omdat de set Geometrixx-Outdoor-producten van fundamenteel belang is. De ingewikkeldheid is gebaseerd op het product [ steigers ](/help/sites-authoring/scaffolding.md), zodat met uw eigen productsteigers het mogelijk is om verfijnde het uitgeven te bereiken.

#### Productinformatie maken - Voor aanraking geoptimaliseerde gebruikersinterface {#creating-product-information-touch-optimized-ui}

1. Gebruikend de **Produkten** console (via **Commerce**) navigeert aan de vereiste plaats.
1. Gebruik **creeer** pictogram om één van beide (afhankelijk van de structuur en de plaats) te selecteren:

   * **creeer Product**
   * **creeer de Variatie van het Product**

   ![ plus-gevormd creeer pictogram ](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. De wizard wordt geopend. Gebruik de **Basis** en **Tabs van het Product** om de [ productattributen ](/help/commerce/cif-classic/administering/concepts.md#product-attributes) voor de nieuwe product of productvariant in te gaan.

   >[!NOTE]
   >
   >**Titel** en **SKU** is het minimum dat wordt vereist om een product of een variant tot stand te brengen.

1. Selecteer **creeer** om de informatie te bewaren.

>[!NOTE]
>
>Veel producten worden aangeboden in verschillende kleuren en/of grootten. De informatie over het basisproduct en de verwante productvarianten kunnen zowel van de **console van Producten** worden geleid.
>
>De producten en hun varianten worden opgeslagen als boomstructuur, is de productinformatie bij de bovenkant, met de varianten onderaan (deze structuur wordt afgedwongen door UI).

### Productinformatie bewerken {#editing-product-information}

>[!NOTE]
>
>De beelden van het product in geometrixx-outdoor worden gediend van:
>
>`/etc/commerce/products/...`
>
>Dit betekent dat, door gebrek, zij door [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) worden geblokkeerd, zo zonodig vormen.

#### Productinformatie bewerken - Voor aanraking geoptimaliseerde gebruikersinterface {#editing-product-information-touch-optimized-ui}

1. Gebruikend de **Produkten** console (via **Commerce**) navigeert aan uw productinformatie.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het **pictogram van de Gegevens van het Product van de Mening**:

   ![ pictogram van de de gegevensgegevens van het meningsproduct - informatiepictogram ](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. De [ productattributen ](/help/commerce/cif-classic/administering/concepts.md#product-attributes) worden getoond. Het gebruik **geeft** uit en **Gedaan** om het even welke veranderingen aan te brengen.

### Productverwijzingen tonen {#showing-product-references}

#### Productreferenties tonen - Voor aanraking geoptimaliseerde interface {#showing-product-references-touch-optimized-ui}

1. Gebruikend de **Produkten** console (via **Commerce**) navigeert aan uw productinformatie.
1. Open de secundaire rail voor Referenties met het pictogram:

   ![ dubbel pijlpictogram ](/help/sites-administering/do-not-localize/chlimage_1-16.png)

1. Selecteer het vereiste product - de secundaire spoorwegupdates, die u de beschikbare verwijzingstypen tonen:

   ![ productconsole met open verwijzingen ](/help/sites-administering/assets/chlimage_1-88.png)

1. Klik op het referentietype (bijvoorbeeld Productpagina&#39;s) om de lijst uit te vouwen.
1. Selecteer een specifieke referentie zodat u de opties kunt weergeven:

   * Naar productpagina navigeren
   * Productpagina bewerken

   ![ het verwijzingspaneel van de Console van Producten ](/help/sites-administering/assets/chlimage_1-89.png)

### Zoeken naar producten {#search-for-products}

1. Navigeer aan de **Producten** console, via **Commerce**.
1. Open de secundaire rail voor Onderzoek met het pictogram:

   ![ vergrootglaspictogram ](/help/sites-administering/do-not-localize/chlimage_1-17.png)

1. Er zijn verschillende facetten beschikbaar waarmee u naar producten kunt zoeken. U kunt slechts één of meerdere facetten voor een onderzoek gebruiken. De gevonden producten worden weergegeven:

   ![ gegevens van het Product in productconsole ](/help/sites-administering/assets/chlimage_1-90.png)

1. Als u op een product klikt of erop tikt, wordt het geopend. U kunt het ook publiceren of de productgegevens bekijken.

#### Zoeken uitbreiden {#extending-search}

U kunt een bestaand facet wijzigen of nieuwe facetten toevoegen met behulp van CRXDE Lite:

1. Navigeren naar:

   `http://localhost:4502/crx/de/index.jsp#/libs/commerce/gui/content/products/aside/items/search/items/searchpanel/facets`

1. U kunt bijvoorbeeld de grootten bewerken die op de pagina met productzoekopdrachten worden weergegeven. Klik op het knooppunt `sizegroup` .
1. Klik op `items` en vervolgens op `propertypredicate` node.
1. U kunt de `propertyValues` bewerken. U kunt bijvoorbeeld XS of XXL toevoegen of een grootte verwijderen.
1. Klik **sparen allen** en navigeer aan de pagina van het productonderzoek. Uw wijzigingen worden weergegeven.

### Multiple Assets {#multiple-assets}

U kunt meerdere elementen toevoegen aan de productcomponent en vervolgens het element opgeven dat op de productpagina moet worden weergegeven.

>[!NOTE]
>
>Alles wat met meerdere middelen te maken heeft, wordt gedaan met de interface die geoptimaliseerd is voor Touch.

#### Meerdere Assets&#39;s toevoegen {#adding-multiple-assets}

1. Navigeer aan de **Producten** console, via **Commerce**.
1. Gebruikend de **console van Producten**, navigeer aan het vereiste product.

   >[!NOTE]
   >
   >U moet op productniveau zijn, niet op variantniveau.

1. Selecteer het **pictogram van de Gegevens van het Product van de Mening** met selectiemodus of snelle acties.
1. Selecteer het pictogram Bewerken.
1. De rol aan **voegt** toe.

   ![ Toevoegend het screenshot van productgegevens ](/help/sites-administering/assets/chlimage_1-91.png)

1. Selecteer **toevoegen**. Er wordt een nieuwe plaatsaanduiding voor elementen weergegeven.
1. Het selecteren van **Verandering** opent een dialoogdoos die u een activa laat kiezen.
1. Selecteer het element dat u wilt toevoegen.

   >[!NOTE]
   >
   >De activa u kunt selecteren zijn van [ Assets ](/help/assets/assets.md).

1. Selecteer het pictogram Gereed.

Er worden nu twee elementen in uw productcomponent opgeslagen. U kunt configureren welke op de productpagina wordt weergegeven. Dit werkt met een categoriesysteem. Eerst moet u een categorie aan de afzonderlijke elementen toevoegen:

1. Selecteer **Gegevens van het Product van de Mening**.
1. Typ een **Categorie van Activa** onder de activa, bijvoorbeeld, `cat1` en `cat2`.

   >[!NOTE]
   >
   >U kunt ook tags gebruiken voor categorieën.

1. Selecteer het pictogram Gereed. U moet nu [ uitrol ](#rolling-out-a-catalog) uw veranderingen.

Uw elementen in de productcomponent hebben nu een categorie. U kunt vormen welke categorie op drie verschillende niveaus wordt getoond:

* [Productpagina](#product-page)
* [Catalogus](#catalog)
* [Productconsole](#products-console)

>[!NOTE]
>
>Als u geen categorieën instelt, wordt het eerste element weergegeven op de productpagina.

Het mechanisme voor het selecteren van de afbeelding die moet worden weergegeven, is als volgt:

1. Controleer of een categorie is ingesteld voor de productpagina.
1. Zo niet, controleer dan of een categorie is ingesteld voor de catalogus.
1. Zo niet, controleer dan of een categorie is ingesteld voor de productconsole.

>[!NOTE]
>
>Voor zowel het niveau van de Catalogus als het niveau van de Console van Producten, moet u uw veranderingen uitvoeren om de wijzigingen toe te passen en het verschil op de productpagina te zien.

#### Productpagina {#product-page}

1. Navigeer naar de productpagina.
1. **geef** de productcomponent uit.
1. Typ de **Categorie van het Beeld** die u ( `cat1` bijvoorbeeld) koos.
1. Selecteer **Gereed**. De pagina wordt vernieuwd en het juiste element moet worden weergegeven.

#### Catalogus  {#catalog}

1. Navigeer naar de catalogus.
1. Selecteer **Eigenschappen van de Mening**.
1. Selecteer **uitgeven**.
1. Selecteer het **Assets** lusje.
1. Typ de vereiste **Categorie van Activa van het Product**.
1. Selecteer **Gereed**.
1. [ Uitvoer ](#rolling-out-a-catalog) uw veranderingen.

#### Productconsole {#products-console}

1. Gebruikend de **console van Producten**, navigeer aan het vereiste Product.
1. Selecteer **Gegevens van het Product van de Mening**.
1. Selecteer **uitgeven**.
1. Typ a **Standaard de Categorie van Activa**.
1. Selecteer **Gereed**.
1. [ Uitvoer ](#rolling-out-a-catalog) uw veranderingen.

### Productinformatie publiceren/verwijderen {#publishing-unpublishing-product-information}

#### Publiceren/Publiceren van de Informatie van het Product - Touch-geoptimaliseerde UI {#publishing-unpublishing-product-information-touch-optimized-ui}

>[!NOTE]
>
>De productinformatie wordt vaak gepubliceerd via de pagina&#39;s die ernaar verwijzen. Wanneer u bijvoorbeeld pagina X publiceert die verwijst naar product Y, AEM u wordt gevraagd of u ook product Y wilt publiceren.
>
>In speciale gevallen ondersteunt AEM ook het rechtstreeks publiceren van de productgegevens.

1. Gebruikend de **Produkten** console (via **Commerce**) navigeert aan uw productinformatie.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het **Publish** of **unpublish** pictogram zoals vereist:

   ![ wereldpictogram ](/help/sites-administering/do-not-localize/chlimage_1-18.png) ![ wereldpictogram met een kruis - geen teken ](/help/sites-administering/do-not-localize/chlimage_1-19.png)

   De productinformatie wordt gepubliceerd of, indien van toepassing, niet gepubliceerd.

<!-- Search&Promote is end of life as of September 1, 2022 ### Product Feed {#product-feed} -->

<!-- Search&Promote is end of life as of September 1, 2022 The Search&Promote integration lets you: -->

<!-- Search&Promote is end of life as of September 1, 2022 * use the eCommerce API, independently of the underlying repository structure and commerce platform. -->
<!-- Search&Promote is end of life as of September 1, 2022 * use the Index Connector feature of Search&Promote to provide a product feed in XML format. -->
<!-- Search&Promote is end of life as of September 1, 2022 * use the Remote Control feature of Search&Promote to perform on-demand or scheduled requests of the product feed -->
<!-- Search&Promote is end of life as of September 1, 2022 * feed generation for different Search&Promote accounts, configured as cloud services configurations. -->

<!-- Search&Promote is end of life as of September 1, 2022 For more information, read [Product Feed](/help/sites-administering/product-feed.md). -->

### Gebeurtenishandler voor productupdates {#event-handler-for-product-updates}

Er is een gebeurtenishandler die een gebeurtenis registreert wanneer een product wordt toegevoegd, bewerkt of verwijderd en wanneer een productpagina wordt toegevoegd, bewerkt of verwijderd. Er zijn de volgende OSGi gebeurtenissen:

* `com/adobe/cq/commerce/pim/PRODUCT_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_DELETED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_DELETED`

Voor de gebeurtenissen `PRODUCT_*` wijst het pad naar het basisproduct in `/etc/commerce/products` . Voor de gebeurtenissen `PRODUCT_PAGE_*` wijst het pad naar het knooppunt `cq:Page` .

U kunt naar hen in de Console van het Web in gebeurtenissen OSGI ( `/system/console/events`) kijken, bijvoorbeeld:

![ Voorbeelden van de gebeurtenissen OSGI ](/help/sites-administering/do-not-localize/chlimage_1-20.png)

>[!NOTE]
>
>Lees ook [ Gebeurtenis behandeling in AEM ](https://blogs.adobe.com/experiencedelivers/experience-management/event_handling_incq/).

### Afbeelding met Koppelingen toevoegen aan winkelwagentje {#image-with-add-to-cart-links}

Met de component Afbeelding met Koppelingen toevoegen aan winkelwagentje kunt u snel een product aan het winkelwagentje toevoegen door een hotspot te maken die is gekoppeld aan een product in een afbeelding.

Als u op de hotspot klikt, wordt een dialoogvenster geopend waarin u de grootte en de hoeveelheid van het product kunt kiezen.

1. Navigeer naar de pagina waaraan u de component wilt toevoegen.
1. Sleep de component naar de pagina.
1. Sleep en laat vallen een beeld in de component van [ activa browser ](/help/sites-authoring/author-environment-tools.md#assets-browser).
1. U kunt:

   * Klik op de component en klik vervolgens op het pictogram Bewerken
   * langzaam dubbelklikken

1. Klik op het pictogram Volledig scherm.

   ![ fullscreen pictogram ](/help/sites-administering/assets/chlimage_1-92.png)

1. Klik op het pictogram Startmap.

   ![ pictogram van de lanceringskaart ](/help/sites-administering/assets/chlimage_1-93.png)

1. Klik op een van de vormpictogrammen.

   ![ vormpictogrammen ](/help/sites-administering/do-not-localize/chlimage_1-21.png)

1. Wijzig en verplaats de vorm naar wens.
1. Klik op de vorm.
1. Het klikken van het doorbladerpictogram opent de [ Plukker van Activa ](/help/assets/search-assets.md#assetpicker).

   >[!NOTE]
   >
   >U kunt ook rechtstreeks het productpad typen dat zich op productniveau moet bevinden, niet het variantniveau.

   ![ typeweg ](/help/sites-administering/assets/chlimage_1-94.png)

1. Klik tweemaal op het bevestigingspictogram en klik op Volledig scherm afsluiten.
1. Klik ergens op de pagina naast de component. De pagina moet worden vernieuwd en u ziet het volgende symbool in uw afbeelding:

   ![ plus symbool ](/help/sites-administering/do-not-localize/chlimage_1-22.png)

1. Schakelaar aan [ voorproef ](/help/sites-authoring/editing-content.md#previewingpagestouchoptimizedui) wijze.
1. Klik op + hotspot. Een dialoog opent waar u de grootte en de hoeveelheid van het product kunt kiezen u in **Weg** inging.

   ![ productvoorbeeld: poncho ](/help/sites-administering/assets/chlimage_1-95.png)

1. Voer een grootte en een hoeveelheid in.
1. Klik op de knop Toevoegen aan winkelwagentje. Het dialoogvenster wordt gesloten.
1. Navigeer naar uw winkelwagentje. Het product moet hier zijn.

#### Configuratieopties {#configuration-options}

U kunt configureren hoe het dialoogvenster eruitziet wanneer u op de hotspot klikt:

1. Klik de component en klik vormen pictogram.

   ![ vorm pictogram ](/help/sites-administering/assets/chlimage_1-96.png)

1. Omlaag schuiven. Er is **TOEVOEGEN AAN KAART** tabel.

   ![ voeg aan wortellusje toe ](/help/sites-administering/assets/chlimage_1-97.png)

1. Klik **TOEVOEGEN AAN KAART**. Er zijn drie configuratieopties die u kunt gebruiken.

   ![ configuratieopties ](/help/sites-administering/assets/chlimage_1-98.png)

1. Klik op het pictogram Gereed.

## Catalogi {#catalogs}

### Een catalogus genereren {#generating-a-catalog}

#### Een catalogus genereren - Voor aanraking geoptimaliseerde gebruikersinterface {#generating-a-catalog-touch-optimized-ui}

>[!NOTE]
>
>De catalogus verwijst naar de productgegevens.

Een catalogus genereren:

1. Open de console van Plaatsen (bijvoorbeeld, [ http://localhost:4502/sites.html/content ](http://localhost:4502/sites.html/content)).
1. Navigeer naar de locatie waar u de pagina wilt maken.
1. Om de optielijst te openen, gebruik **creeer** pictogram:

   ![ creeer-pictogram ](/help/sites-administering/do-not-localize/chlimage_1-23.png)

1. Van de lijst, creeer **Catalogus**. De wizard Catalogus maken wordt geopend.

   ![ creeer catalogustovenaar ](/help/sites-administering/assets/chlimage_1-99.png)

1. Navigeer naar de gewenste blauwdruk van de catalogus.
1. Selecteer **Uitgezochte** knoop en klik de vereiste Vervaging van de Catalogus.
1. Selecteer **daarna**.

   ![ tovenaar van cataloguseigenschappen ](/help/sites-administering/assets/chlimage_1-100.png)

1. Typ a **Titel** en a **Naam**.
1. Selecteer **creeer** knoop. De catalogus wordt gemaakt en er wordt een dialoogvenster geopend.

   ![ catalogus leidde tot dialoog ](/help/sites-administering/assets/chlimage_1-101.png)

1. Het selecteren van **Gedaan** knoop brengt u terug naar de console van Plaatsen waar u uw catalogus kunt zien.

   Tapping/het klikken van **Open de knoop van de Catalogus** opent uw catalogus (bijvoorbeeld, `http://localhost:4502/editor.html/content/test-catalog.html`).

#### Een catalogus genereren - klassieke gebruikersinterface {#generating-a-catalog-classic-ui}

>[!NOTE]
>
>De catalogusverwijzingen uw [ Gegevens van het Product ](#products-and-product-variants).

1. Gebruikend de **console Websites**, navigeer aan uw **Vervaging van de Catalogus**, toen de Catalogus van de Basis.

   Bijvoorbeeld:

   `http://localhost:4502/siteadmin#/content/catalogs/geometrixx-outdoors/base-catalog`

1. Creeer een pagina gebruikend het **malplaatje van de Vervaging van de Sectie**.

   Bijvoorbeeld `Swimwear` .

1. Open de nieuwe `Swimwear` pagina, dan klik **uitgeven Vervaging**. Het **de dialoogvakje van Eigenschappen** opent zodat kunt u opstelling de **Producten** selectie.

   Bijvoorbeeld, open het **Codes/Trefwoorden** gebied om Activiteit te selecteren, dan het zwemmen van de Geometrixx-Buiten sectie.

1. Klik **O.K.** zodat uw eigenschappen worden bewaard; de voorbeeldproducten worden getoond onder de **Criteria van de Selectie van het Product** op de blauwdrukpagina.
1. Klik **Veranderingen van de Uitvoer...**, selecteer **pagina van de Uitvoer en alle subpagina&#39;s**, dan klik **daarna** toen **Uitdraaiing**. Zodra de rollout met succes wordt voltooid, toont de **1&rbrace; indicator van de Status &lbrace;als groen.**
1. U kunt **dicht** nu klikken en de nieuwe catalogussectie controleren; bijvoorbeeld, op en onder:

   `http://localhost:4502/cf#/content/geometrixx-outdoors/en/swimwear.html`

1. Opnieuw van de pagina van blauwdrukken klikt **Bewerk Vervaging** en in de **Eigenschappen** dialoog open de **Gegenereerde Pagina** tabel. Selecteer in het lijstveld Banner de afbeelding die u wilt weergeven, bijvoorbeeld `summer.jpg`
1. Klik **O.K.** zodat worden uw eigenschappen bewaard; de bannerinformatie wordt getoond onder de **Criteria van de Selectie van het Product** op de blauwdrukpagina.
1. Deze nieuwe wijzigingen uitvoeren.

### Een catalogus uitrollen {#rolling-out-a-catalog}

#### Een catalogus implementeren - geoptimaliseerde gebruikersinterface met aanraakfuncties {#rolling-out-a-catalog-touch-optimized-ui}

Een catalogus uitrollen:

1. Navigeer aan de **console van Catalogi**, via **Commerce**.
1. Navigeer naar de catalogus die u wilt uitrollen.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het **pictogram van de Veranderingen van de Output**:

   ![ rollout ](/help/sites-administering/do-not-localize/chlimage_1-24.png)

1. In de tovenaar, plaats de rollout zoals nodig en klik dan **Veranderingen van de Uitvoer**.
1. Er wordt een dialoogvenster geopend. Selecteer **Gedaan** wanneer het proces wordt gebeëindigd.

#### Een catalogus uitrollen - klassieke gebruikersinterface {#rolling-out-a-catalog-classic-ui}

Een catalogus uitrollen:

1. Navigeer naar de catalogus die u wilt uitrollen. Bijvoorbeeld:

   `http://localhost:4502/cf#/content/catalogs/geometrixx-outdoors/base-catalog.html`

1. Klik **Veranderingen van de Uitvoer...**
1. Stel de rollout naar wens in.
1. Klik **Uitvoer**.

### Blauwdrukimportmodule {#blueprint-importer}

#### Blauwdrukimportmodule - Voor aanraking geoptimaliseerde gebruikersinterface {#blueprint-importer-touch-optimized-ui}

1. Navigeer aan de **console van Catalogi**, via **Commerce**.
1. Navigeer naar de locatie waar u de blauwdruk van de catalogus wilt importeren.
1. Selecteer het **pictogram van de Vervaging van de Invoer**.

   ![ het pictogram van de Blauwdrukken van de Invoer ](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. In de tovenaar, selecteer Source zoals vereist en klik **daarna**.

   ![ tovenaar van de blauwdruk ](/help/sites-administering/assets/chlimage_1-102.png)

1. Selecteer **Gedaan** wanneer de invoer wordt gebeëindigd.

#### Invoer van blauwdruk - klassieke gebruikersinterface {#blueprint-importer-classic-ui}

1. Gebruikend de **console van Hulpmiddelen**, navigeer aan **Commerce**.

   Bijvoorbeeld:

   `http://localhost:4502/miscadmin#/etc/commerce`

1. Open de **Importeur van het Vervagen van de Catalogus**.
1. Stel de gewenste importbewerking in.
1. Klik **de Vervaging van de Catalogus van de Invoer**.

## Aanbiedingen {#promotions}

### Een aanbieding maken {#creating-a-promotion}

#### Aanbieding maken - klassieke gebruikersinterface {#creating-a-promotion-classic-ui}

>[!NOTE]
>
>Het volgende voorbeeld behandelt een bevordering die direct in a [ wordt gehouden campagne ](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md), wordt dit gebruikt voor vouchers.
>
>Een bevordering kan ook in een [ ervaring ](/help/sites-authoring/personalization.md) binnen een campagne zijn.
>
>Voor meer informatie, zie [ Bevorderingen en Vouchers ](#promotions-and-vouchers).

1. Open de **console van Websites** van uw auteursinstantie.
1. In de linkerruit, selecteer uw vereiste **Campagne**.
1. Klik **Nieuw**, selecteer het **malplaatje van de Bevordering**, dan specificeer a **Titel** (en **Naam** indien nodig) voor uw nieuwe voucher.
1. Klik **creëren**. De nieuwe pagina voor speciale acties wordt weergegeven in het rechtervenster.

1. Bewerk **Eigenschappen** door één van beiden:

   * het openen van de pagina, dan het klikken van de Edit knoop om het dialoogvenster van Eigenschappen te openen
   * het selecteren van de pagina in de console van Websites, dan gebruikend het contextmenu (gewoonlijk de juiste muisknoop) om **Eigenschappen te selecteren...** en de eigenschappendialoog te openen.

   Specificeer het **Type van Bevordering**, **Type van Korting**, **Waarde van de Korting** en om het even welke andere gebieden zoals vereist.

1. Klik **O.K.** om te bewaren.

1. Je kunt je speciale actie nu activeren, zodat kopers deze kunnen bekijken op het publicatieexemplaar.

## Vouchers {#vouchers}

### Een voucher maken {#creating-a-voucher}

#### Een voucher maken - een klassieke gebruikersinterface {#creating-a-voucher-classic-ui}

1. Open de **console van Websites** van uw auteursinstantie.
1. In de linkerruit, selecteer uw vereiste **Campagne**.
1. Klik **Nieuw**, selecteer het **Voucher** malplaatje, dan specificeer a **Titel** (en **Naam** indien nodig) voor uw nieuwe voucher.
1. Klik **creëren**. De nieuwe voucherpagina wordt weergegeven in het rechterdeelvenster.

1. Open uw nieuwe voucherpagina met een dubbel-klik, dan klik **uitgeven** en vormen de informatie zoals vereist.
1. Klik **O.K.** om te bewaren.

1. U kunt de voucher nu activeren, zodat kopers deze kunnen gebruiken in hun winkelwagentjes op het publicatieexemplaar.

### Vouchers verwijderen {#removing-vouchers}

#### Vouchers verwijderen - Klassieke UI {#removing-vouchers-classic-ui}

Als u een voucher niet beschikbaar wilt maken voor klanten, kunt u:

* Deactiveer de voucher - deze blijft beschikbaar in de auteursomgeving zodat u deze later opnieuw kunt activeren.
* Verwijder het volledig.

Beide acties kunnen van de **&#x200B;**&#x200B;console van Websites worden gedaan.

### Vouchers wijzigen {#modifying-vouchers}

#### Vouchers wijzigen - Klassieke UI {#modifying-vouchers-classic-ui}

Om de eigenschappen van een voucher of een bevordering te veranderen, kunt u het op de **Websites** console tweemaal klikken en **klikken geeft** uit. Nadat u het bestand hebt opgeslagen, moet u het activeren zodat de wijzigingen worden doorgevoerd in de publicatie-instanties.

### Vouchers toevoegen aan een winkelwagen {#adding-vouchers-to-a-cart}

Om gebruikers toe te staan om vouchers aan hun wortels toe te voegen, kunt u de ingebouwde **component van Vouchers** (de categorie van Commerce) gebruiken. Voeg dit toe aan dezelfde pagina als waar het winkelwagentje wordt weergegeven (maar dit is niet verplicht). De component vouchers is slechts een formulier waarin de gebruiker een vouchercode kan invoeren. Het is de winkelwagencomponent die de lijst met toegepaste vouchers en de korting daarop weergeeft.

Op de demo-site (Geometrixx Outdoors - Engels) ziet u het bonformulier op de cartpagina, onder het winkelwagentje zelf.

## Orders {#orders}

>[!NOTE]
>
>Er zij op gewezen dat AEM buiten de box geen handelingen heeft die vereist zijn voor standaardfuncties met betrekking tot bestellingen, zoals het retourneren van handelswaar, het bijwerken van de status van de bestelling, het uitvoeren van de uitvoering en het genereren van pakslips. Het is hoofdzakelijk bedoeld als technologievoorproef.
>
>De generieke Order Management in AEM is standaard gehouden. De velden in de wizard zijn afhankelijk van het substraat:
>`/etc/scaffolding/geometrixx-outdoors/order/jcr:content/cq:dialog`
>
>Als u een aangepast subbestand maakt, kunt u meer ordegegevens opslaan.

>[!NOTE]
>
>De orderconsole stelt de informatie van de verkopersorde bloot, die nooit wordt gepubliceerd.
>
>De bestelgegevens van de klant staan in de directory&#39;s van de thuismap en worden weergegeven door de ordergeschiedenis voor hun account. Deze informatie wordt samen met de rest van hun thuismap gepubliceerd.

### Bestelgegevens maken {#creating-order-information}

#### Bestelgegevens maken - Voor aanraking geoptimaliseerde gebruikersinterface {#creating-order-information-touch-optimized-ui}

1. Gebruikend de **Orders** console navigeert aan de vereiste plaats.
1. Gebruik **creeer** pictogram om **te selecteren creeer Orde**.

   ![ plus-gevormd creeer pictogram ](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. De wizard wordt geopend. Gebruik de **Basis**, **Inhoud**, **Betaling**, en **de lusjes van de Vervulling** om de [ informatie over de nieuwe orde ](/help/commerce/cif-classic/administering/concepts.md#order-information) in te gaan.

1. Selecteer **creeer** om de informatie te bewaren.

### Bewerkingsordergegevens {#editing-order-information}

#### Bewerkordergegevens - Voor aanraking geoptimaliseerde interface {#editing-order-information-touch-optimized-ui}

1. Gebruikend de **Orders** console navigeert aan de orde.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het **pictogram van de Gegevens van de Orde van de Mening**:

   ![ informatiepictogram ](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. De [ ordeinformatie ](/help/commerce/cif-classic/administering/concepts.md#order-information) wordt getoond. Het gebruik **geeft** uit en **Gedaan** om het even welke veranderingen aan te brengen.

