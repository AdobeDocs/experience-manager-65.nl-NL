---
title: Algemene eCommerce beheren
seo-title: Algemene eCommerce beheren
description: De AEM generische oplossing verstrekt methodes om de handelsinformatie te beheren die binnen de bewaarplaats wordt gehouden.
seo-description: De AEM generische oplossing verstrekt methodes om de handelsinformatie te beheren die binnen de bewaarplaats wordt gehouden.
uuid: 8d2b02a6-0658-4957-a366-29a59350f3e8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 9167cbe2-2efb-422d-b58b-0c24b9476fe6
docset: aem65
translation-type: tm+mt
source-git-commit: 06d6696a5493f0e166e400bcd9a379b7be062c1e
workflow-type: tm+mt
source-wordcount: '3011'
ht-degree: 0%

---


# Algemene eCommerce beheren {#administering-generic-ecommerce}

De AEM generische oplossing verstrekt methodes om de handelsinformatie te beheren die binnen de bewaarplaats wordt gehouden (in tegenstelling tot het gebruiken van een externe e-commerce motor). Dit omvat:

* [Producten](/help/sites-administering/concepts.md#products)
* [Productvarianten](/help/sites-administering/concepts.md#product-variants)
* [Catalogus(s)](/help/sites-administering/concepts.md#catalogs)
* [Aanbiedingen](/help/sites-administering/concepts.md#promotions)
* [Vouchers](/help/sites-administering/concepts.md#vouchers)
* [Orders](/help/sites-administering/concepts.md#shopping-cart-and-orders)
* [Proxypagina&#39;s](/help/sites-administering/concepts.md#proxy-pages)

>[!NOTE]
>
>De standaard AEM installatie omvat de generieke implementatie van de eCommerce AEM (JCR).
>
>Dit is momenteel bedoeld voor demonstratiedoeleinden of als de basis voor een aangepaste implementatie volgens uw vereisten.

## Producten en productvariaties {#products-and-product-variations}

>[!NOTE]
>
>De volgende procedures zijn van toepassing op zowel producten als productvariaties.

Voordat u producten maakt, moet u een [substraat](/help/sites-authoring/scaffolding.md) definiëren. Hiermee geeft u de velden op die u nodig hebt om de producten te definiëren en hoe deze worden bewerkt.

Voor elk afzonderlijk producttype is een steiger nodig. Het geschikte substraat wordt met de producten geassocieerd door:

* path
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
>U kunt een nieuwe productdefinitie overal onder die zonder enige extra opstelling tot stand brengen.

### Producten {#importing-products} importeren

#### Producten importeren - Touch-geoptimaliseerde UI {#importing-products-touch-optimized-ui}

1. Navigeer naar de **Products** console, via **Commerce**.
1. Met de **Products**-console navigeert u naar de gewenste locatie.
1. Gebruik het **pictogram Producten importeren** om de wizard te openen.

   ![chlimage_1-1](do-not-localize/chlimage_1-13.png)

1. Geef het volgende op:

   * **Importeur**

      De importer voor de specifieke [commerceprovider](/help/sites-administering/concepts.md#commerce-providers), standaard `Geometrixx`.

   * **Bron**

      Het bestand dat u wilt importeren; u kunt de browser gebruiken om een bestand te selecteren.

   * **Incrementele import**

      Geef aan of dit een incrementele invoer is (in tegenstelling tot volledige invoer).
   >[!NOTE]
   >
   >De incrementele invoer (van de voorbeeldgeometrixx-outdoorimporteur) vindt plaats op productniveau.
   >
   >Een aangepaste importmodule kan zo worden gedefinieerd dat deze naar wens kan werken.

1. Selecteer **Volgende** om de producten in te voeren, zal een logboek van de genomen acties worden getoond.

   >[!NOTE]
   >
   >De producten worden geïmporteerd in of ten opzichte van de huidige locatie.

   >[!NOTE]
   >
   >Als u herhaaldelijk **Next** en **Back** gebruikt, worden de productdefinities herhaaldelijk geïmporteerd. Nochtans, aangezien zij zelfde SKUs hebben zal de informatie in de bewaarplaats eenvoudig worden beschreven.

1. Selecteer **Done** om de wizard te sluiten.

#### Producten importeren - Klassieke UI {#importing-products-classic-ui}

1. Met de **Tools**-console opent u de map **Commerce**.
1. Dubbelklik om de **Product Importer** te openen:

   ![chlimage_1-22](assets/chlimage_1-22.jpeg)

1. Geef het volgende op:

   * **Winkelnaam**

      Producten worden geïmporteerd naar:

      `/etc/commerce/products/<*store name*>/`

   * **Handelsprovider**

      De importer voor uw [commerceprovider](/help/sites-administering/concepts.md#commerce-providers); standaard Geometrixx.

   * **Bronbestand**

      De locatie in de opslagplaats van het bestand dat u wilt importeren.

   * **Incrementele import**

      Geef aan of dit een incrementele invoer is (in tegenstelling tot volledige invoer).

1. Klik **Producten importeren**.

### Productinformatie {#creating-product-information} maken

>[!NOTE]
>
>Het standaardproductbeheer is van fundamenteel belang, omdat de set Geometrixx-Outdoor-producten van fundamenteel belang is. De complexiteit is gebaseerd op het product [steigers](/help/sites-authoring/scaffolding.md), dus met uw eigen productsteigers is het mogelijk om geavanceerdere bewerkingen uit te voeren.

#### Productinformatie maken - Voor aanraking geoptimaliseerde interface {#creating-product-information-touch-optimized-ui}

1. Met de **Products**-console (via **Commerce**) navigeert u naar de gewenste locatie.
1. Gebruik het pictogram **Maken** om een van beide te selecteren (afhankelijk van de structuur en locatie):

   * **Product maken**
   * **Productvariatie maken**

   ![chlimage_1-14](do-not-localize/chlimage_1-14.png)

1. De wizard wordt geopend. Gebruik **Basic** en **Product Tabs** om de [productkenmerken](/help/sites-administering/concepts.md#product-attributes) voor het nieuwe product of de productvariant in te voeren.

   >[!NOTE]
   >
   >**** Titleand  **** SKUare het minimum wordt vereist om een product of een variant tot stand te brengen.

1. Selecteer **Maken** om de gegevens op te slaan.

>[!NOTE]
>
>Veel producten worden aangeboden in verschillende kleuren en/of grootten. De informatie over het basisproduct en de verwante productvarianten kan allebei van **Products** console worden beheerd.
>
>De producten en hun varianten worden opgeslagen als boomstructuur, is de productinformatie bij de bovenkant, met de varianten onderaan (deze structuur wordt afgedwongen door UI).

### Productinformatie {#editing-product-information} bewerken

>[!NOTE]
>
>De beelden van het product in geometrixx-outdoor worden gediend van:
>
>`/etc/commerce/products/...`
>
>Dit betekent dat ze standaard worden geblokkeerd door de [dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), dus zo nodig configureren.

#### Productinformatie bewerken - Voor aanraking geoptimaliseerde interface {#editing-product-information-touch-optimized-ui}

1. Met de **Products**-console (via **Commerce**) navigeert u naar de productinformatie.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het pictogram **Productgegevens weergeven**:

   ![chlimage_1-3](do-not-localize/chlimage_1-15.png)

1. De [productkenmerken](/help/sites-administering/concepts.md#product-attributes) worden weergegeven. Gebruik **Bewerken** en **Gereed** om wijzigingen aan te brengen.

### Productverwijzingen tonen {#showing-product-references}

#### Productreferenties tonen - Voor aanraking geoptimaliseerde interface {#showing-product-references-touch-optimized-ui}

1. Met de **Products**-console (via **Commerce**) navigeert u naar de productinformatie.
1. Open de secundaire rail voor Referenties met het pictogram:

   ![chlimage_1-4](do-not-localize/chlimage_1-16.png)

1. Selecteer het vereiste product. De secundaire rail wordt bijgewerkt en geeft de beschikbare referentietypen weer:

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Klik/tik op het referentietype (bijvoorbeeld productpagina&#39;s) om de lijst uit te vouwen.
1. Selecteer een specifieke verwijzing om de opties weer te geven:

   * Naar productpagina navigeren
   * Productpagina bewerken

   ![chlimage_1-89](assets/chlimage_1-89.png)

### Zoeken naar producten {#search-for-products}

1. Navigeer naar de **Products** console, via **Commerce**.
1. Open de secundaire rail voor Onderzoek met het pictogram:

   ![](do-not-localize/chlimage_1-17.png)

1. U kunt op verschillende manieren naar producten zoeken. U kunt slechts één of meerdere facetten voor een onderzoek gebruiken. De gevonden producten worden weergegeven:

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Als u op een product klikt of erop tikt, wordt het geopend. U kunt het ook publiceren of de productgegevens bekijken.

#### Zoeken {#extending-search} uitbreiden

U kunt een bestaand facet wijzigen of nieuwe facetten toevoegen met behulp van CRXDE Lite:

1. Ga naar:

   `http://localhost:4502/crx/de/index.jsp#/libs/commerce/gui/content/products/aside/items/search/items/searchpanel/facets`

1. U kunt bijvoorbeeld de grootten wijzigen die op de pagina met productzoekopdrachten worden weergegeven. Klik op het knooppunt `sizegroup`.
1. Klik `items` knoop, dan klik `propertypredicate` knoop.
1. U kunt `propertyValues` wijzigen. U kunt bijvoorbeeld XS of XXL toevoegen of een grootte verwijderen.
1. Klik **Alles opslaan** en navigeer naar de pagina met productzoekopdrachten. Uw wijzigingen worden weergegeven.

### Meerdere elementen {#multiple-assets}

U kunt meerdere elementen toevoegen aan de productcomponent en vervolgens het element opgeven dat op de productpagina wordt weergegeven.

>[!NOTE]
>
>Alles wat met meerdere middelen te maken heeft, wordt gedaan met de interface die geoptimaliseerd is voor Touch.

#### Meerdere elementen toevoegen {#adding-multiple-assets}

1. Navigeer naar de **Products** console, via **Commerce**.
1. Navigeer met de **Products**-console naar het vereiste product.

   >[!NOTE]
   >
   >U moet op productniveau zijn, niet op variantniveau.

1. Tik/klik op **Product-gegevens weergeven** pictogram met selectiemodus of snelle handelingen.
1. Tik op het pictogram Bewerken of klik op het pictogram Bewerken.
1. Schuif naar **Add**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Tik/klik **Toevoegen**. Er wordt een nieuwe plaatsaanduiding voor elementen weergegeven.
1. Door te tikken of te klikken op **Wijzigen **Hiermee opent u een dialoogvenster waarin u een element kunt kiezen.
1. Selecteer het element dat u wilt toevoegen.

   >[!NOTE]
   >
   >De elementen die u kunt selecteren, zijn afkomstig uit [Middelen](https://helpx.adobe.com/experience-manager/aem-previous-versions.html#assets).

1. Tik op het pictogram Gereed/klik op Gereed.

Er worden nu twee elementen in uw productcomponent opgeslagen. U kunt configureren welke op de productpagina wordt weergegeven. Dit werkt met een categoriesysteem. Eerst moet u een categorie toevoegen aan de afzonderlijke elementen:

1. Tik/klik **Productgegevens weergeven**.
1. Typ een **Middelencategorie** onder de elementen, bijvoorbeeld `cat1` en `cat2`.

   >[!NOTE]
   >
   >U kunt ook tags gebruiken voor categorieën.

1. Tik op het pictogram Gereed/klik op Gereed. U moet nu [rollout](#rolling-out-a-catalog) uw veranderingen.

Uw elementen in de productcomponent hebben nu een categorie. U kunt vormen welke categorie op drie verschillende niveaus zal worden getoond:

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
1. **De** productcomponent bewerken.
1. Typ de **Afbeeldingscategorie** die u hebt gekozen (bijvoorbeeld `cat1`).
1. Tik/klik **Done**. De pagina wordt vernieuwd en het juiste element moet worden weergegeven.

#### Catalogus {#catalog}

1. Navigeer naar de catalogus.
1. Tik/klik **Eigenschappen weergeven**.
1. Tik/klik **Bewerken**.
1. Tik/klik op het tabblad **Middelen**.
1. Typ de vereiste **Productcategorie**.
1. Tik/klik **Done**.
1. [](#rolling-out-a-catalog) Rolloutuw wijzigingen.

#### Productconsole {#products-console}

1. Navigeer met de **Products**-console naar het vereiste product.
1. Tik/klik **Productgegevens weergeven**.
1. Tik/klik **Bewerken**.
1. Typ a **Standaardelementcategorie**.
1. Tik/klik **Done**.
1. [](#rolling-out-a-catalog) Rolloutuw wijzigingen.

### Productinformatie {#publishing-unpublishing-product-information} publiceren/verwijderen

#### Publiceren/Publiceren van de Informatie van het Product - Touch-geoptimaliseerde UI {#publishing-unpublishing-product-information-touch-optimized-ui}

>[!NOTE]
>
>De productinformatie wordt vaak gepubliceerd via de pagina&#39;s die ernaar verwijzen. Wanneer u bijvoorbeeld pagina X publiceert met verwijzingen naar product Y, AEM u wordt gevraagd of u ook product Y wilt publiceren.
>
>In speciale gevallen ondersteunt AEM ook het rechtstreeks publiceren van de productgegevens.

1. Met de **Products**-console (via **Commerce**) navigeert u naar de productinformatie.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het pictogram **Publiceren** of **Publiceren** desgewenst:

   ![chlimage_1-6](do-not-localize/chlimage_1-18.png) ![chlimage_1-7](do-not-localize/chlimage_1-19.png)

   De productinformatie zal worden gepubliceerd of, indien van toepassing, niet gepubliceerd.

### Productfeed {#product-feed}

Dankzij de Search&amp;Promote-integratie kunt u:

* gebruik de eCommerce-API, onafhankelijk van de onderliggende structuur van de gegevensopslagruimte en het handelsplatform.
* hefboomwerking de eigenschap van de Schakelaar van de Index van Search&amp;Promote om een productvoer in formaat van XML te verstrekken.
* de functie voor afstandsbediening van Search&amp;Promote gebruiken om op aanvraag of geplande aanvragen van de productfeed uit te voeren
* feed generation voor verschillende Search&amp;Promote-accounts, geconfigureerd als cloudservices configuraties.

Lees [Productfeed](/help/sites-administering/product-feed.md) voor meer informatie.

### Gebeurtenishandler voor productupdates {#event-handler-for-product-updates}

Er is een gebeurtenishandler die een gebeurtenis registreert wanneer een product wordt toegevoegd, gewijzigd of verwijderd en wanneer een productpagina wordt toegevoegd, gewijzigd of verwijderd. Er zijn de volgende OSGi gebeurtenissen:

* `com/adobe/cq/commerce/pim/PRODUCT_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_DELETED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_DELETED`

Voor de gebeurtenissen `PRODUCT_*` wijst het pad naar het basisproduct in `/etc/commerce/products`. Voor de `PRODUCT_PAGE_*` gebeurtenissen, richt de weg aan `cq:Page` knoop.

U kunt hen in de Console van het Web in gebeurtenissen bekijken OSGI ( `/system/console/events`), bijvoorbeeld:

![](do-not-localize/chlimage_1-20.png)

>[!NOTE]
>
>Lees ook [Gebeurtenisafhandeling in AEM](https://blogs.adobe.com/experiencedelivers/experience-management/event_handling_incq/). [](https://blogs.adobe.com/experiencedelivers/experience-management/event_handling_incq/)

### Afbeelding met Toevoegen aan winkelwagentkoppelingen {#image-with-add-to-cart-links}

Met de component Afbeelding met Koppelingen toevoegen aan winkelwagentje kunt u snel een product aan het winkelwagentje toevoegen door een hotspot te maken die is gekoppeld aan een product in een afbeelding.

Als u op de hotspot klikt, wordt een dialoogvenster geopend waarin u de grootte en de hoeveelheid van het product kunt kiezen.

1. Navigeer naar de pagina waaraan u de component wilt toevoegen.
1. Sleep de component naar de pagina.
1. Sleep een afbeelding in de component vanuit de browser [assets](/help/sites-authoring/author-environment-tools.md#assets-browser).
1. U kunt:

   * Klik op de component en klik vervolgens op het pictogram Bewerken
   * langzaam dubbelklikken

1. Klik op het pictogram Volledig scherm.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Klik op het pictogram Startmap.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Klik op een van de vormpictogrammen.

   ![chlimage_1-29](do-not-localize/chlimage_1-21.png)

1. Wijzig en verplaats de vorm naar wens.
1. Klik op de vorm.
1. Als u op het bladerpictogram klikt, wordt de [Asset Picker](../assets/search-assets.md#assetpicker) geopend.

   >[!NOTE]
   >
   >U kunt ook rechtstreeks het productpad typen dat zich op productniveau moet bevinden, niet het variantniveau.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Klik tweemaal op het bevestigingspictogram en klik op Volledig scherm afsluiten.
1. Klik ergens op de pagina naast de component. De pagina moet worden vernieuwd en u ziet het volgende symbool in uw afbeelding:

   ![](do-not-localize/chlimage_1-22.png)

1. Schakel over naar de modus [preview](/help/sites-authoring/editing-content.md#previewingpagestouchoptimizedui).
1. Klik op + hotspot. Er wordt een dialoogvenster geopend waarin u de grootte en de hoeveelheid van het product kunt kiezen die u hebt ingevoerd in **Pad**.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Voer een grootte en een hoeveelheid in.
1. Klik op de knop Toevoegen aan winkelwagentje. Het dialoogvenster wordt gesloten.
1. Navigeer naar uw winkelwagentje. Het product moet hier zijn.

#### Configuratieopties {#configuration-options}

U kunt configureren hoe het dialoogvenster eruitziet wanneer u op de hotspot klikt:

1. Klik de component en klik vormen pictogram.

   ![chlimage_1-96](assets/chlimage_1-96.png)

1. Omlaag schuiven. Er is een **ADD TO CART** tabblad.

   ![chlimage_1-97](assets/chlimage_1-97.png)

1. Klik **TOEVOEGEN AAN KAART**. Er zijn 3 configuratieopties die u kunt gebruiken.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. Klik op het pictogram Gereed.

## Catalogi {#catalogs}

### Een catalogus {#generating-a-catalog} genereren

#### Catalogus genereren - Voor aanraking geoptimaliseerde interface {#generating-a-catalog-touch-optimized-ui}

>[!NOTE]
>
>De catalogus verwijst naar uw productgegevens.

Een catalogus genereren:

1. Open de Sites-console (bijvoorbeeld [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)).
1. Navigeer naar de locatie waar u de nieuwe pagina wilt maken.
1. Als u de lijst met opties wilt openen, gebruikt u het pictogram **Maken**:

   ![](do-not-localize/chlimage_1-23.png)

1. Selecteer **Catalogus maken** in de lijst en open de wizard Catalogus maken.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Navigeer naar de gewenste blauwdruk van de catalogus.
1. Tik/klik op **Selecteer** en tik/klik op de vereiste blauwdruk van de catalogus.
1. Tik/klik **Volgende**.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. Typ a **Title** en a **Name**.
1. Tik/klik op de knop **Maken**. De catalogus wordt gemaakt en er wordt een dialoogvenster geopend.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. Als u op **Done** klikt, keert u terug naar de Sites-console waar u de catalogus kunt zien.

   Als u op **Catalogus openen** klikt, wordt de catalogus geopend (bijvoorbeeld `http://localhost:4502/editor.html/content/test-catalog.html`).

#### Catalogus genereren - Klassieke UI {#generating-a-catalog-classic-ui}

>[!NOTE]
>
>De catalogus verwijst naar uw [Productgegevens](#products-and-product-variants).

1. Navigeer met de **Websites**-console naar uw **Catalogusblauwdruk** en vervolgens naar de basiscatalogus.

   Bijvoorbeeld:

   `http://localhost:4502/siteadmin#/content/catalogs/geometrixx-outdoors/base-catalog`

1. Maak een nieuwe pagina met de sjabloon **Sectie vervagen**.

   Bijvoorbeeld, `Swimwear`.

1. Open de nieuwe `Swimwear` pagina, dan klik **geef Blauwdruk** uit om **Eigenschappen** dialoog te openen, waar u **Producten** selectie kunt plaatsen.

   Open bijvoorbeeld het veld **Tags/Trefwoorden** om Activiteit te selecteren en vervolgens te zwemmen in de sectie Geometrixx-Buiten.

1. Klik **OK** om uw eigenschappen op te slaan. voorbeeldproducten worden weergegeven onder de **Productselectiecriteria** op de pagina Bladeren.
1. Klik op **Wijzigingen bij rollout...**, selecteer **Uitrolpagina en alle subpagina&#39;s**, dan klik **Volgende** dan **Uitvoer**. Wanneer de rollout is voltooid, wordt de **Status**-indicator weergegeven als groen.
1. U kunt nu **Close** klikken en de nieuwe catalogussectie controleren; bijvoorbeeld op en onder :

   `http://localhost:4502/cf#/content/geometrixx-outdoors/en/swimwear.html`

1. Klik nogmaals op **Vervaging bewerken** op de pagina Vervagen en open in het dialoogvenster **Eigenschappen** het tabblad **Gegenereerde pagina**. Selecteer in het lijstveld Banner de afbeelding die u wilt weergeven. bijvoorbeeld `summer.jpg`
1. Klik **OK** om uw eigenschappen op te slaan. bannergegevens worden weergegeven onder de **Productselectiecriteria** op de pagina Bladeren.
1. Deze nieuwe wijzigingen uitvoeren.

### Een catalogus {#rolling-out-a-catalog} uitrollen

#### Een catalogus uitvoeren - Voor aanraking geoptimaliseerde interface {#rolling-out-a-catalog-touch-optimized-ui}

Een catalogus uitrollen:

1. Navigeer aan de **console Catalogs**, via **Handel**.
1. Navigeer naar de catalogus die u wilt uitrollen.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het pictogram **Wijzigingen bij rollout**:

   ![](do-not-localize/chlimage_1-24.png)

1. Stel in de wizard de rollout zo nodig in en tik/klik op **Wijzigingen voor rollout**.
1. Er wordt een dialoogvenster geopend. Tik/klik **Done** wanneer het proces is voltooid.

#### Catalogus uitrollen - Klassieke UI {#rolling-out-a-catalog-classic-ui}

Een catalogus uitrollen:

1. Navigeer naar de catalogus die u wilt uitrollen. Bijvoorbeeld:

   `http://localhost:4502/cf#/content/catalogs/geometrixx-outdoors/base-catalog.html`

1. Klik **Wijzigingen bij rollout...**
1. Stel de rollout naar wens in.
1. Klik **Uitvoer**.

### Invoer van blauwdruk {#blueprint-importer}

#### Blauwdrukimportmodule - Voor aanraking geoptimaliseerde gebruikersinterface {#blueprint-importer-touch-optimized-ui}

1. Navigeer aan de **console Catalogs**, via **Handel**.
1. Navigeer naar de locatie waar u de blauwdruk van de catalogus wilt importeren.
1. Tik/klik op het pictogram **Vervagen importeren**.

   ![](do-not-localize/chlimage_1-13.png)

1. Selecteer in de wizard de gewenste bron en tik/klik op **Volgende**.

   ![chlimage_1-340](assets/chlimage_1-102.png)

1. Tik/klik **Done** zodra het importeren is voltooid.

#### Blauwdrukimportmodule - Klassieke UI {#blueprint-importer-classic-ui}

1. Navigeer met de **Tools**-console naar **Commerce**.

   Bijvoorbeeld:

   `http://localhost:4502/miscadmin#/etc/commerce`

1. Open de **Importer van de Blauwdruk van de Catalogus**.
1. Stel de gewenste importbewerking in.
1. Klik **Catalogusblauwdrukken importeren**.

## Promoties {#promotions}

### Promotie {#creating-a-promotion} maken

#### Aanbieding maken - Klassieke UI {#creating-a-promotion-classic-ui}

>[!NOTE]
>
>In het volgende voorbeeld wordt een speciale actie behandeld die rechtstreeks in een [campagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md) wordt gehouden. Deze wordt gebruikt voor vouchers.
>
>Een bevordering kan ook in [ervaring ](/help/sites-authoring/personalization.md) binnen een campagne zijn.
>
>Zie [Promoties en vouchers](#promotions-and-vouchers) voor meer informatie.

1. Open de console **Websites** van uw auteurinstantie.
1. Selecteer in het linkerdeelvenster de gewenste **Campagne**.
1. Klik op **Nieuw**, selecteer **Bevordering** malplaatje, dan specificeer **Titel** (en **Naam** indien vereist) voor uw nieuwe bon.
1. Klik **Maken**. De nieuwe pagina voor speciale acties wordt weergegeven in het rechtervenster.

1. Bewerk de **Eigenschappen** door:

   * het openen van de pagina, dan het klikken van de Edit knoop om het dialoogvenster van Eigenschappen te openen
   * het selecteren van de pagina in de console van Websites, dan gebruikend het contextmenu (gewoonlijk de juiste muisknoop) om **Eigenschappen te selecteren..** en open het dialoogvenster Eigenschappen

   Geef het **Promotietype**, **Korting Type**, **Korting Waarde** en andere velden op zoals vereist.

1. Klik **OK** om op te slaan.

1. Je kunt je speciale actie nu activeren, zodat kopers deze kunnen bekijken op het publicatieexemplaar.

## Vouchers {#vouchers}

### Een voucher {#creating-a-voucher} maken

#### Een voucher maken - klassieke gebruikersinterface {#creating-a-voucher-classic-ui}

1. Open de console **Websites** van uw auteurinstantie.
1. Selecteer in het linkerdeelvenster de gewenste **Campagne**.
1. Klik op **Nieuw**, selecteer **Voucher** malplaatje, dan specificeer **Titel** (en **Naam** indien vereist) voor uw nieuwe bon.
1. Klik **Maken**. De nieuwe voucherpagina wordt weergegeven in het rechterdeelvenster.

1. Open de nieuwe voucherpagina met een dubbelklik en klik op **Bewerken** om de informatie naar wens te configureren.
1. Klik **OK** om op te slaan.

1. U kunt de voucher nu activeren, zodat kopers deze kunnen gebruiken in hun winkelwagentjes op het publicatieexemplaar.

### Vouchers {#removing-vouchers} verwijderen

#### Vouchers verwijderen - Klassieke UI {#removing-vouchers-classic-ui}

Als u een voucher niet beschikbaar wilt maken voor klanten, kunt u:

* Deactiveer de voucher - deze blijft beschikbaar in de auteursomgeving zodat u deze later opnieuw kunt activeren.
* Verwijder het volledig.

Beide acties kunnen van **Websites** console worden gedaan.

### Vouchers {#modifying-vouchers} wijzigen

#### Vouchers wijzigen - Klassieke UI {#modifying-vouchers-classic-ui}

Als u de eigenschappen van een voucher of promotie wilt wijzigen, dubbelklikt u erop op de **Websites**-console en klikt u op **Bewerken**. Nadat u het bestand hebt opgeslagen, activeert u het zo dat de wijzigingen worden doorgevoerd in de publicatie-instantie(s).

### Vouchers toevoegen aan een winkelwagentje {#adding-vouchers-to-a-cart}

Als u gebruikers wilt toestaan vouchers aan hun winkelwagentjes toe te voegen, kunt u de ingebouwde **Vouchers**-component (categorie Handel) gebruiken. U moet dit toevoegen aan dezelfde pagina als waar de winkelwagen wordt weergegeven (maar dit is niet verplicht). De component vouchers is slechts een formulier waarin de gebruiker een vouchercode kan invoeren. Het is de winkelwagencomponent die de lijst met toegepaste vouchers en de korting daarop weergeeft.

Op de demo-site (Geometrixx Outdoors - Engels) ziet u het bonformulier op de cartpagina, onder het winkelwagentje zelf.

## Bestellingen {#orders}

>[!NOTE]
>
>Er zij op gewezen dat AEM buiten de box geen handelingen heeft die vereist zijn voor standaardfuncties met betrekking tot bestellingen, zoals het retourneren van handelswaar, het bijwerken van de status van de bestelling, het uitvoeren van de uitvoering en het genereren van pakslips. Het is hoofdzakelijk bedoeld als technologievoorproef.
>
>Het algemene orderbeheer in AEM is van essentieel belang gehouden; de velden in de wizard zijn afhankelijk van het subbestand :
>`/etc/scaffolding/geometrixx-outdoors/order/jcr:content/cq:dialog`
>
>Als u een aangepast subbestand maakt, kunt u meer ordergegevens opslaan.

>[!NOTE]
>
>De orderconsole stelt de informatie van de verkopersorde bloot, die nooit wordt gepubliceerd.
>
>De bestelgegevens van de klant staan in de directory&#39;s van de thuismap en worden weergegeven door de ordergeschiedenis voor hun account. Deze informatie wordt samen met de rest van hun thuismap gepubliceerd.

### Bestelgegevens maken {#creating-order-information}

#### Bestelgegevens maken - Voor aanraking geoptimaliseerde interface {#creating-order-information-touch-optimized-ui}

1. Met de **Bestellingen**-console navigeert u naar de gewenste locatie.
1. Met het pictogram **Maken** kunt u **Volgorde maken** selecteren.

   ![](do-not-localize/chlimage_1-14.png)

1. De wizard wordt geopend. Gebruik de tabbladen **Basic**, **Content**, **Payment** en **Fulfillment** om de [informatie over de nieuwe bestelling](/help/sites-administering/concepts.md#order-information) in te voeren.

1. Selecteer **Maken** om de gegevens op te slaan.

### Bewerkordergegevens {#editing-order-information}

#### Bewerkordergegevens - Voor aanraking geoptimaliseerde interface {#editing-order-information-touch-optimized-ui}

1. Met de console **Orders** navigeert u naar de volgorde.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer het pictogram **Order Data** weergeven:

   ![](do-not-localize/chlimage_1-15.png)

1. De [orderinformatie](/help/sites-administering/concepts.md#order-information) wordt weergegeven. Gebruik **Bewerken** en **Gereed** om wijzigingen aan te brengen.

