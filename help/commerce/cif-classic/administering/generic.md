---
title: Algemene eCommerce beheren
seo-title: Administering generic eCommerce
description: De AEM generische oplossing verstrekt methodes om de handelsinformatie te beheren die binnen de bewaarplaats wordt gehouden.
seo-description: The AEM generic solution provides methods of managing the commerce information held within the repository.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
docset: aem65
exl-id: c29f6213-1df6-45af-91c8-14b255276d82
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '2979'
ht-degree: 0%

---

# Algemene eCommerce beheren {#administering-generic-ecommerce}

De AEM generische oplossing verstrekt methodes om de handelsinformatie te beheren die binnen de bewaarplaats wordt gehouden (in tegenstelling tot het gebruiken van een externe e-commerce motor). Dit omvat:

* [Producten](/help/commerce/cif-classic/administering/concepts.md#products)
* [Productvarianten](/help/commerce/cif-classic/administering/concepts.md#product-variants)
* [Catalogus(s)](/help/commerce/cif-classic/administering/concepts.md#catalogs)
* [Aanbiedingen](/help/commerce/cif-classic/administering/concepts.md#promotions)
* [Vouchers](/help/commerce/cif-classic/administering/concepts.md#vouchers)
* [Orders](/help/commerce/cif-classic/administering/concepts.md#shopping-cart-and-orders)
* [Proxypagina&#39;s](/help/commerce/cif-classic/administering/concepts.md#proxy-pages)

>[!NOTE]
>
>De standaard AEM installatie omvat de generieke implementatie van de eCommerce AEM (JCR).
>
>Dit is momenteel bedoeld voor demonstratiedoeleinden of als de basis voor een aangepaste implementatie volgens uw vereisten.

## Producten en productvariaties {#products-and-product-variations}

>[!NOTE]
>
>De volgende procedures zijn van toepassing op zowel producten als productvariaties.

Voordat u producten maakt, moet u een [steiger](/help/sites-authoring/scaffolding.md). Hiermee geeft u de velden op die u nodig hebt om de producten te definiëren en hoe deze worden bewerkt.

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
>U kunt een nieuwe productdefinitie overal onder die zonder enige extra opstelling tot stand brengen.

### Producten importeren {#importing-products}

#### Producten importeren - Voor aanraking geoptimaliseerde interface {#importing-products-touch-optimized-ui}

1. Ga naar de **Producten** console, via **Handel**.
1. Met de **Producten** navigeren naar de gewenste locatie.
1. Gebruik de **Producten importeren** om de wizard te openen.

   ![Pictogram Producten importeren](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. Geef het volgende op:

   * **Importeur**

     De importeur voor de specifieke [handelsprovider](/help/commerce/cif-classic/administering/concepts.md#commerce-providers)standaard `Geometrixx`.

   * **Bron**

     Het bestand dat u wilt importeren; u kunt de browser gebruiken om een bestand te selecteren.

   * **Incrementele import**

     Geef aan of dit een incrementele invoer is (in tegenstelling tot volledige invoer).

   >[!NOTE]
   >
   >De incrementele invoer (van de voorbeeldgeometrixx-outdoorimporteur) vindt plaats op productniveau.
   >
   >Een aangepaste importmodule kan zo worden gedefinieerd dat deze naar wens kan werken.

1. Selecteren **Volgende** voor de invoer van de producten zal een logboek van de genomen maatregelen worden weergegeven .

   >[!NOTE]
   >
   >De producten worden geïmporteerd in of ten opzichte van de huidige locatie.

   >[!NOTE]
   >
   >Herhaald gebruik **Volgende** en **Vorige** zal de productdefinities herhaaldelijk importeren. Nochtans, aangezien zij zelfde SKUs hebben zal de informatie in de bewaarplaats eenvoudig worden beschreven.

1. Selecteren **Gereed** om de wizard te sluiten.

#### Producten importeren - Klassieke UI {#importing-products-classic-ui}

1. Met de **Gereedschappen** de console opent **Handel** map.
1. Dubbelklik om het dialoogvenster **Producimporteur**:

   ![Console voor importeren van producten](/help/sites-administering/assets/chlimage_1-22.jpeg)

1. Geef het volgende op:

   * **Winkelnaam**

     Producten worden geïmporteerd naar:

     `/etc/commerce/products/<*store name*>/`

   * **Handelsprovider**

     De importer voor uw [handelsprovider](/help/commerce/cif-classic/administering/concepts.md#commerce-providers); standaard Geometrixx.

   * **Bronbestand**

     De locatie in de opslagplaats van het bestand dat u wilt importeren.

   * **Incrementele import**

     Geef aan of dit een incrementele invoer is (in tegenstelling tot volledige invoer).

1. Klikken **Producten importeren**.

### Productinformatie maken {#creating-product-information}

>[!NOTE]
>
>Het standaardproductbeheer is van fundamenteel belang, omdat de set Geometrixx-Outdoor-producten van fundamenteel belang is. De complexiteit is gebaseerd op het product [steigers](/help/sites-authoring/scaffolding.md)En dus is het met uw eigen productsteigers mogelijk om geavanceerdere bewerkingen uit te voeren.

#### Productinformatie maken - Voor aanraking geoptimaliseerde gebruikersinterface {#creating-product-information-touch-optimized-ui}

1. Met de **Producten** console (via **Handel**) navigeer naar de gewenste locatie.
1. Gebruik de **Maken** pictogram om een van beide te selecteren (afhankelijk van de structuur en locatie):

   * **Product maken**
   * **Productvariatie maken**

   ![Pictogram voor maken in de vorm van een plusteken](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. De wizard wordt geopend. Gebruik de **Basis** en **Tabs product** om de [productkenmerken](/help/commerce/cif-classic/administering/concepts.md#product-attributes) voor het nieuwe product of de nieuwe productvariant.

   >[!NOTE]
   >
   >**Titel** en **SKU** minimaal vereist zijn om een product of variant te maken.

1. Selecteren **Maken** om de gegevens op te slaan.

>[!NOTE]
>
>Veel producten worden aangeboden in verschillende kleuren en/of grootten. De informatie over het basisproduct en de desbetreffende productvarianten kan beide worden beheerd via de **Producten** console.
>
>De producten en hun varianten worden opgeslagen als boomstructuur, is de productinformatie bij de bovenkant, met de varianten onderaan (deze structuur wordt afgedwongen door UI).

### Productinformatie bewerken {#editing-product-information}

>[!NOTE]
>
>De beelden van het product in geometrixx-outdoor worden gediend van:
>
>`/etc/commerce/products/...`
>
>Dit betekent dat ze standaard worden geblokkeerd door de [verzender](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html), zo vorm zo zoals vereist.

#### Productinformatie bewerken - Voor aanraking geoptimaliseerde interface {#editing-product-information-touch-optimized-ui}

1. Met de **Producten** console (via **Handel**) navigeer naar de productinformatie.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer **Productgegevens weergeven** pictogram:

   ![pictogram met productgegevens weergeven - informatiepictogram](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. De [productkenmerken](/help/commerce/cif-classic/administering/concepts.md#product-attributes) wordt weergegeven. Gebruiken **Bewerken** en **Gereed** om wijzigingen aan te brengen.

### Productverwijzingen tonen {#showing-product-references}

#### Productreferenties tonen - Voor aanraking geoptimaliseerde interface {#showing-product-references-touch-optimized-ui}

1. Met de **Producten** console (via **Handel**) navigeer naar de productinformatie.
1. Open de secundaire rail voor Referenties met het pictogram:

   ![pictogram dubbele pijl](/help/sites-administering/do-not-localize/chlimage_1-16.png)

1. Selecteer het vereiste product. De secundaire rail wordt bijgewerkt en geeft de beschikbare referentietypen weer:

   ![productconsole met open verwijzingen](/help/sites-administering/assets/chlimage_1-88.png)

1. Klik/tik op het referentietype (bijvoorbeeld Productpagina&#39;s) om de lijst uit te vouwen.
1. Selecteer een specifieke verwijzing om de opties weer te geven:

   * Naar productpagina navigeren
   * Productpagina bewerken

   ![Referentiepaneel van de productconsole](/help/sites-administering/assets/chlimage_1-89.png)

### Zoeken naar producten {#search-for-products}

1. Ga naar de **Producten** console, via **Handel**.
1. Open de secundaire rail voor Onderzoek met het pictogram:

   ![vergrootglaspictogram](/help/sites-administering/do-not-localize/chlimage_1-17.png)

1. U kunt op verschillende manieren naar producten zoeken. U kunt slechts één of meerdere facetten voor een onderzoek gebruiken. De gevonden producten worden weergegeven:

   ![Productgegevens in productconsole](/help/sites-administering/assets/chlimage_1-90.png)

1. Als u op een product klikt of erop tikt, wordt het geopend. U kunt het ook publiceren of de productgegevens bekijken.

#### Zoeken uitbreiden {#extending-search}

U kunt een bestaand facet wijzigen of nieuwe facetten toevoegen met behulp van CRXDE Lite:

1. Ga naar:

   `http://localhost:4502/crx/de/index.jsp#/libs/commerce/gui/content/products/aside/items/search/items/searchpanel/facets`

1. U kunt bijvoorbeeld de grootten wijzigen die op de pagina met productzoekopdrachten worden weergegeven. Klik op de knop `sizegroup` knooppunt.
1. Klikken `items` knoop, dan klik `propertypredicate` knooppunt.
1. U kunt de `propertyValues`. U kunt bijvoorbeeld XS of XXL toevoegen of een grootte verwijderen.
1. Klikken **Alles opslaan** en navigeer naar de pagina met productzoekopdrachten. Uw wijzigingen worden weergegeven.

### Meerdere elementen {#multiple-assets}

U kunt meerdere elementen toevoegen aan de productcomponent en vervolgens het element opgeven dat op de productpagina wordt weergegeven.

>[!NOTE]
>
>Alles wat met meerdere middelen te maken heeft, wordt gedaan met de interface die geoptimaliseerd is voor Touch.

#### Meerdere elementen toevoegen {#adding-multiple-assets}

1. Ga naar de **Producten** console, via **Handel**.
1. Met de **Producten** naar het vereiste product te navigeren.

   >[!NOTE]
   >
   >U moet op productniveau zijn, niet op variantniveau.

1. Tikken/klikken **Productgegevens weergeven** met de selectiemodus of snelle handelingen.
1. Tik op het pictogram Bewerken of klik op het pictogram Bewerken.
1. Schuiven naar **Toevoegen**.

   ![Screenshot van productgegevens toevoegen](/help/sites-administering/assets/chlimage_1-91.png)

1. Tikken/klikken **Toevoegen**. Er wordt een nieuwe plaatsaanduiding voor elementen weergegeven.
1. Door te tikken of te klikken op **Wijzigen **Hiermee opent u een dialoogvenster waarin u een element kunt kiezen.
1. Selecteer het element dat u wilt toevoegen.

   >[!NOTE]
   >
   >De elementen die u kunt selecteren, zijn [Activa](/help/assets/assets.md).

1. Tik op het pictogram Gereed/klik op Gereed.

Er worden nu twee elementen in uw productcomponent opgeslagen. U kunt configureren welke op de productpagina wordt weergegeven. Dit werkt met een categoriesysteem. Eerst moet u een categorie toevoegen aan de afzonderlijke elementen:

1. Tikken/klikken **Productgegevens weergeven**.
1. Typ een **Middelencategorie** onder de activa, bijvoorbeeld `cat1` en `cat2`.

   >[!NOTE]
   >
   >U kunt ook tags gebruiken voor categorieën.

1. Tik op het pictogram Gereed/klik op Gereed. U moet nu [rollout](#rolling-out-a-catalog) uw wijzigingen.

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
1. **Bewerken** de productcomponent.
1. Typ de **Afbeeldingscategorie** je hebt gekozen ( `cat1` bijvoorbeeld).
1. Tikken/klikken **Gereed**. De pagina wordt vernieuwd en het juiste element moet worden weergegeven.

#### Catalogus  {#catalog}

1. Navigeer naar de catalogus.
1. Tikken/klikken **Eigenschappen weergeven**.
1. Tikken/klikken **Bewerken**.
1. Tik/klik op de knop **Activa** tab.
1. Typ het vereiste **Productcategorie**.
1. Tikken/klikken **Gereed**.
1. [Uitrol](#rolling-out-a-catalog) uw wijzigingen.

#### Productconsole {#products-console}

1. Met de **Producten** navigeer naar het vereiste product.
1. Tikken/klikken **Productgegevens weergeven**.
1. Tikken/klikken **Bewerken**.
1. Typ a **Standaardelementcategorie**.
1. Tikken/klikken **Gereed**.
1. [Uitrol](#rolling-out-a-catalog) uw wijzigingen.

### Productinformatie publiceren/verwijderen {#publishing-unpublishing-product-information}

#### Publiceren/Publiceren van de Informatie van het Product - Touch-geoptimaliseerde UI {#publishing-unpublishing-product-information-touch-optimized-ui}

>[!NOTE]
>
>De productinformatie wordt vaak gepubliceerd via de pagina&#39;s die ernaar verwijzen. Wanneer u bijvoorbeeld pagina X publiceert met verwijzingen naar product Y, AEM u wordt gevraagd of u ook product Y wilt publiceren.
>
>In speciale gevallen ondersteunt AEM ook het rechtstreeks publiceren van de productgegevens.

1. Met de **Producten** console (via **Handel**) navigeer naar de productinformatie.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer **Publiceren** of **Publiceren ongedaan maken** pictogram naar wens:

   ![wereldpictogram](/help/sites-administering/do-not-localize/chlimage_1-18.png) ![wereldpictogram met een kruisje - geen teken](/help/sites-administering/do-not-localize/chlimage_1-19.png)

   De productinformatie zal worden gepubliceerd of, indien van toepassing, niet gepubliceerd.

<!-- Search&Promote is end of life as of September 1, 2022 ### Product Feed {#product-feed} -->

<!-- Search&Promote is end of life as of September 1, 2022 The Search&Promote integration allows you to: -->

<!-- Search&Promote is end of life as of September 1, 2022 * use the eCommerce API, independently of the underlying repository structure and commerce platform. -->
<!-- Search&Promote is end of life as of September 1, 2022 * leverage the Index Connector feature of Search&Promote to provide a product feed in XML format. -->
<!-- Search&Promote is end of life as of September 1, 2022 * leverage the Remote Control feature of Search&Promote to perform on-demand or scheduled requests of the product feed -->
<!-- Search&Promote is end of life as of September 1, 2022 * feed generation for different Search&Promote accounts, configured as cloud services configurations. -->

<!-- Search&Promote is end of life as of September 1, 2022 For more information, read [Product Feed](/help/sites-administering/product-feed.md). -->

### Gebeurtenishandler voor productupdates {#event-handler-for-product-updates}

Er is een gebeurtenishandler die een gebeurtenis registreert wanneer een product wordt toegevoegd, gewijzigd of verwijderd en wanneer een productpagina wordt toegevoegd, gewijzigd of verwijderd. Er zijn de volgende OSGi gebeurtenissen:

* `com/adobe/cq/commerce/pim/PRODUCT_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_DELETED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_DELETED`

Voor de `PRODUCT_*` gebeurtenissen, wijst het pad naar het basisproduct in `/etc/commerce/products`. Voor de `PRODUCT_PAGE_*` gebeurtenissen, wijst het pad naar de `cq:Page` knooppunt.

U kunt hen in de Console van het Web in gebeurtenissen bekijken OSGI ( `/system/console/events`), bijvoorbeeld:

![Voorbeelden van OSGI-gebeurtenissen](/help/sites-administering/do-not-localize/chlimage_1-20.png)

>[!NOTE]
>
>Lees ook [Gebeurtenisafhandeling in AEM](https://blogs.adobe.com/experiencedelivers/experience-management/event_handling_incq/).

### Afbeelding met Koppelingen toevoegen aan winkelwagentje {#image-with-add-to-cart-links}

Met de component Afbeelding met Koppelingen toevoegen aan winkelwagentje kunt u snel een product aan het winkelwagentje toevoegen door een hotspot te maken die is gekoppeld aan een product in een afbeelding.

Als u op de hotspot klikt, wordt een dialoogvenster geopend waarin u de grootte en de hoeveelheid van het product kunt kiezen.

1. Navigeer naar de pagina waaraan u de component wilt toevoegen.
1. Sleep de component naar de pagina.
1. Sleep een afbeelding in de component vanuit de component [middelenbrowser](/help/sites-authoring/author-environment-tools.md#assets-browser).
1. U kunt:

   * Klik op de component en klik vervolgens op het pictogram Bewerken
   * langzaam dubbelklikken

1. Klik op het pictogram Volledig scherm.

   ![pictogram Volledig scherm](/help/sites-administering/assets/chlimage_1-92.png)

1. Klik op het pictogram Startmap.

   ![Startnerschap](/help/sites-administering/assets/chlimage_1-93.png)

1. Klik op een van de vormpictogrammen.

   ![vormpictogrammen](/help/sites-administering/do-not-localize/chlimage_1-21.png)

1. Wijzig en verplaats de vorm naar wens.
1. Klik op de vorm.
1. Als u op het bladerpictogram klikt, wordt het dialoogvenster [Asset Picker](/help/assets/search-assets.md#assetpicker).

   >[!NOTE]
   >
   >U kunt ook rechtstreeks het productpad typen dat zich op productniveau moet bevinden, niet het variantniveau.

   ![tekstpad](/help/sites-administering/assets/chlimage_1-94.png)

1. Klik tweemaal op het bevestigingspictogram en klik op Volledig scherm afsluiten.
1. Klik ergens op de pagina naast de component. De pagina moet worden vernieuwd en u ziet het volgende symbool in uw afbeelding:

   ![plus-symbool](/help/sites-administering/do-not-localize/chlimage_1-22.png)

1. Overschakelen op [voorvertoning](/help/sites-authoring/editing-content.md#previewingpagestouchoptimizedui) in.
1. Klik op + hotspot. Er wordt een dialoogvenster geopend waarin u de grootte en de hoeveelheid van het product kunt kiezen die u hebt ingevoerd **Pad**.

   ![productvoorbeeld: poncho](/help/sites-administering/assets/chlimage_1-95.png)

1. Voer een grootte en een hoeveelheid in.
1. Klik op de knop Toevoegen aan winkelwagentje. Het dialoogvenster wordt gesloten.
1. Navigeer naar uw winkelwagentje. Het product moet hier zijn.

#### Configuratieopties {#configuration-options}

U kunt configureren hoe het dialoogvenster eruitziet wanneer u op de hotspot klikt:

1. Klik de component en klik vormen pictogram.

   ![Configuratiepictogram](/help/sites-administering/assets/chlimage_1-96.png)

1. Omlaag schuiven. Er is een **TOEVOEGEN AAN KAART** tab.

   ![Toevoegen aan tabblad Kaart](/help/sites-administering/assets/chlimage_1-97.png)

1. Klikken **TOEVOEGEN AAN KAART**. Er zijn 3 configuratieopties die u kunt gebruiken.

   ![configuratieopties](/help/sites-administering/assets/chlimage_1-98.png)

1. Klik op het pictogram Gereed.

## Catalogi {#catalogs}

### Een catalogus genereren {#generating-a-catalog}

#### Een catalogus genereren - Voor aanraking geoptimaliseerde gebruikersinterface {#generating-a-catalog-touch-optimized-ui}

>[!NOTE]
>
>De catalogus verwijst naar uw productgegevens.

Een catalogus genereren:

1. Open de Sites-console (bijvoorbeeld [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)).
1. Navigeer naar de locatie waar u de nieuwe pagina wilt maken.
1. Als u de lijst met opties wilt openen, gebruikt u de optie **Maken** pictogram:

   ![create-icon](/help/sites-administering/do-not-localize/chlimage_1-23.png)

1. In de lijst selecteert u **Catalogus maken** wordt de wizard Catalogus maken geopend.

   ![wizard Catalogus maken](/help/sites-administering/assets/chlimage_1-99.png)

1. Navigeer naar de gewenste blauwdruk van de catalogus.
1. Tikken/klikken **Selecteren** en tik/klik op de gewenste blauwdruk van de catalogus.
1. Tikken/klikken **Volgende**.

   ![wizard Cataloguseigenschappen](/help/sites-administering/assets/chlimage_1-100.png)

1. Typ a **Titel** en **Naam**.
1. Tik/klik op de knop **Maken** knop. De catalogus wordt gemaakt en er wordt een dialoogvenster geopend.

   ![dialoogvenster Catalogus gemaakt](/help/sites-administering/assets/chlimage_1-101.png)

1. Tapping/klikken **Gereed** brengt u terug naar de console van Plaatsen waar u uw catalogus zult kunnen zien.

   Tapping/klikken **Catalogus openen** opent u uw catalogus (bijvoorbeeld `http://localhost:4502/editor.html/content/test-catalog.html`).

#### Een catalogus genereren - klassieke gebruikersinterface {#generating-a-catalog-classic-ui}

>[!NOTE]
>
>De catalogus verwijst naar uw [Productgegevens](#products-and-product-variants).

1. Met de **Websites** console, navigeer naar uw **Catalogusvervaging** en vervolgens de basiscatalogus.

   Bijvoorbeeld:

   `http://localhost:4502/siteadmin#/content/catalogs/geometrixx-outdoors/base-catalog`

1. Een nieuwe pagina maken met de opdracht **Sectie vervagen** sjabloon.

   Bijvoorbeeld, `Swimwear`.

1. De nieuwe openen `Swimwear` pagina, en klik vervolgens op **Vervaging bewerken** om de **Eigenschappen** waar u de **Producten** selectie.

   Open bijvoorbeeld de **Tags/trefwoorden** om Activiteit te selecteren, dan het Zwemmen van de Geometrixx-Buiten sectie.

1. Klikken **OK** om uw eigenschappen op te slaan; voorbeeldproducten worden onder de **Selectiecriteria voor producten** op de pagina Bladeren.
1. Klikken op **Wijzigingen in rollout...**, selecteert u **Uitrolpagina en alle subpagina&#39;s** en klik vervolgens op **Volgende** dan **Uitrol**. Als de rollout is voltooid, wordt de opdracht **Status** de indicator zal als groen worden getoond.
1. U kunt nu **Sluiten** en controleer de nieuwe sectie van de catalogus; bijvoorbeeld op en onder :

   `http://localhost:4502/cf#/content/geometrixx-outdoors/en/swimwear.html`

1. Klik nogmaals op de pagina Bladeringen **Vervaging bewerken** en in de **Eigenschappen** wordt geopend **Gegenereerde pagina** tab. Selecteer in het lijstveld Banner de afbeelding die u wilt weergeven. bijvoorbeeld: `summer.jpg`
1. Klikken **OK** om uw eigenschappen op te slaan; bannergegevens worden weergegeven onder de **Selectiecriteria voor producten** op de pagina Bladeren.
1. Deze nieuwe wijzigingen uitvoeren.

### Een catalogus uitrollen {#rolling-out-a-catalog}

#### Een catalogus implementeren - geoptimaliseerde gebruikersinterface met aanraakfuncties {#rolling-out-a-catalog-touch-optimized-ui}

Een catalogus uitrollen:

1. Ga naar de **Catalogi** console, via **Handel**.
1. Navigeer naar de catalogus die u wilt uitrollen.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer **Wijzigingen in rollout** pictogram:

   ![rollout](/help/sites-administering/do-not-localize/chlimage_1-24.png)

1. Stel in de wizard de rollout naar wens in en tik/klik op **Wijzigingen in rollout**.
1. Er wordt een dialoogvenster geopend. Tikken/klikken **Gereed** wanneer het proces is voltooid.

#### Een catalogus uitrollen - klassieke gebruikersinterface {#rolling-out-a-catalog-classic-ui}

Een catalogus uitrollen:

1. Navigeer naar de catalogus die u wilt uitrollen. Bijvoorbeeld:

   `http://localhost:4502/cf#/content/catalogs/geometrixx-outdoors/base-catalog.html`

1. Klikken **Wijzigingen in rollout...**
1. Stel de rollout naar wens in.
1. Klikken **Uitrol**.

### Blauwdrukimportmodule {#blueprint-importer}

#### Blauwdrukimportmodule - Voor aanraking geoptimaliseerde gebruikersinterface {#blueprint-importer-touch-optimized-ui}

1. Ga naar de **Catalogi** console, via **Handel**.
1. Navigeer naar de locatie waar u de blauwdruk van de catalogus wilt importeren.
1. Tik/klik op de knop **Blauwdrukken importeren** pictogram.

   ![Pictogram Blauwafdrukken importeren](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. Selecteer in de wizard de gewenste bron en tik/klik op **Volgende**.

   ![blauwdruk, wizard](/help/sites-administering/assets/chlimage_1-102.png)

1. Tikken/klikken **Gereed** zodra het importeren is voltooid.

#### Invoer van blauwdruk - klassieke gebruikersinterface {#blueprint-importer-classic-ui}

1. Met de **Gereedschappen** console, navigeren naar **Handel**.

   Bijvoorbeeld:

   `http://localhost:4502/miscadmin#/etc/commerce`

1. Open de **Importeren van catalogusvervaging**.
1. Stel de gewenste importbewerking in.
1. Klikken **Catalogusblauwdrukken importeren**.

## Aanbiedingen {#promotions}

### Een aanbieding maken {#creating-a-promotion}

#### Aanbieding maken - klassieke gebruikersinterface {#creating-a-promotion-classic-ui}

>[!NOTE]
>
>In het volgende voorbeeld wordt een promotie behandeld die rechtstreeks in een [campagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md), wordt dit gebruikt voor vouchers.
>
>Een promotie kan ook in een [ervaring](/help/sites-authoring/personalization.md) in een campagne.
>
>Zie voor meer informatie [Promoties en vouchers](#promotions-and-vouchers).

1. Open de **Websites** console van uw auteurinstantie.
1. Selecteer in het linkerdeelvenster de gewenste opties **Campagne**.
1. Klikken op **Nieuw**, selecteert u de **Aanbieding** sjabloon, geef vervolgens een **Titel** (en **Naam** indien vereist) voor uw nieuwe voucher.
1. Klikken **Maken**. De nieuwe pagina voor speciale acties wordt weergegeven in het rechtervenster.

1. Bewerk de **Eigenschappen** door:

   * het openen van de pagina, dan het klikken van de Edit knoop om het dialoogvenster van Eigenschappen te openen
   * het selecteren van de pagina in de console van Websites, dan gebruikend het contextmenu (gewoonlijk de juiste muisknoop) om te selecteren **Eigenschappen...** en opent u het dialoogvenster met eigenschappen

   Geef de **Type aanbieding**, **Type korting**, **Korting** en andere velden naar behoefte.

1. Klikken **OK** om op te slaan.

1. Je kunt je speciale actie nu activeren, zodat kopers deze kunnen bekijken op het publicatieexemplaar.

## Vouchers {#vouchers}

### Een voucher maken {#creating-a-voucher}

#### Een voucher maken - een klassieke gebruikersinterface {#creating-a-voucher-classic-ui}

1. Open de **Websites** console van uw auteurinstantie.
1. Selecteer in het linkerdeelvenster de gewenste opties **Campagne**.
1. Klikken op **Nieuw**, selecteert u de **Voucher** sjabloon, geef vervolgens een **Titel** (en **Naam** indien vereist) voor uw nieuwe voucher.
1. Klikken **Maken**. De nieuwe voucherpagina wordt weergegeven in het rechterdeelvenster.

1. Open de nieuwe voucherpagina met een dubbelklik en klik op **Bewerken** om de informatie te vormen zoals vereist.
1. Klikken **OK** om op te slaan.

1. U kunt de voucher nu activeren, zodat kopers deze kunnen gebruiken in hun winkelwagentjes op het publicatieexemplaar.

### Vouchers verwijderen {#removing-vouchers}

#### Vouchers verwijderen - Klassieke UI {#removing-vouchers-classic-ui}

Als u een voucher niet beschikbaar wilt maken voor klanten, kunt u:

* Deactiveer de voucher - deze blijft beschikbaar in de auteursomgeving zodat u deze later opnieuw kunt activeren.
* Verwijder het volledig.

Beide handelingen kunnen worden uitgevoerd via de **Websites** console.

### Vouchers wijzigen {#modifying-vouchers}

#### Vouchers wijzigen - Klassieke UI {#modifying-vouchers-classic-ui}

Als u de eigenschappen van een voucher of een promotie wilt wijzigen, dubbelklikt u erop in het dialoogvenster **Websites** console en klik op **Bewerken**. Nadat u het bestand hebt opgeslagen, activeert u het zo dat de wijzigingen worden doorgevoerd in de publicatie-instantie(s).

### Vouchers toevoegen aan een winkelwagen {#adding-vouchers-to-a-cart}

Als u gebruikers wilt toestaan vouchers aan hun winkelwagentjes toe te voegen, kunt u de ingebouwde **Vouchers** component (categorie Handel). U moet dit toevoegen aan dezelfde pagina als waar de winkelwagen wordt weergegeven (maar dit is niet verplicht). De component vouchers is slechts een formulier waarin de gebruiker een vouchercode kan invoeren. Het is de winkelwagencomponent die de lijst met toegepaste vouchers en de korting daarop weergeeft.

Op de demo-site (Geometrixx Outdoors - Engels) ziet u het bonformulier op de cartpagina, onder het winkelwagentje zelf.

## Orders {#orders}

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

#### Bestelgegevens maken - Voor aanraking geoptimaliseerde gebruikersinterface {#creating-order-information-touch-optimized-ui}

1. Met de **Orders** navigeren naar de gewenste locatie.
1. Gebruik de **Maken** pictogram om te selecteren **Volgorde maken**.

   ![Pictogram voor maken in de vorm van een plusteken](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. De wizard wordt geopend. Gebruik de **Basis**, **Inhoud**, **Betaling** en **Afhandeling** tabs om de [informatie over de nieuwe order](/help/commerce/cif-classic/administering/concepts.md#order-information).

1. Selecteren **Maken** om de gegevens op te slaan.

### Bewerkingsordergegevens {#editing-order-information}

#### Bewerkordergegevens - Voor aanraking geoptimaliseerde interface {#editing-order-information-touch-optimized-ui}

1. Met de **Orders** navigeren naar de volgorde.
1. Een van de volgende methoden gebruiken:

   * [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [selectiemodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Selecteer **Bestelgegevens weergeven** pictogram:

   ![informatiepictogram](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. De [ordergegevens](/help/commerce/cif-classic/administering/concepts.md#order-information) wordt weergegeven. Gebruiken **Bewerken** en **Gereed** om wijzigingen aan te brengen.

