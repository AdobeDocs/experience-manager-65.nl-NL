---
title: AEM gebruiken met SAP-Commerce Cloud
description: Leer hoe u Adobe Experience Manager met SAP-Commerce Cloud kunt gebruiken.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: c342f789-2ff7-4802-99c7-c3699218fe47
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 0%

---

# SAP-Commerce Cloud{#sap-commerce-cloud}

Na de installatie kunt u uw instantie configureren:

1. [De beperkte zoekopdracht naar Geometrixx Outdoors configureren](#configure-the-facetted-search-for-geometrixx-outdoors).
1. [De catalogusversie configureren](#configure-the-catalog-version).
1. [De importstructuur configureren](#configure-the-import-structure).
1. [De te laden productkenmerken configureren](#configure-the-product-attributes-to-load).
1. [De productgegevens importeren](#importing-the-product-data).
1. [De importmodule voor catalogi configureren](#configure-the-catalog-importer).
1. Gebruik de [Importeren om de catalogus te importeren](#catalog-import) naar een specifieke locatie in AEM.

## De beperkte zoekopdracht naar Geometrixx Outdoors configureren {#configure-the-facetted-search-for-geometrixx-outdoors}

>[!NOTE]
>
>Dit is niet nodig voor hybris 5.3.0.1 en hoger.

1. Navigeer in uw browser naar de **hybrusbeheerconsole** om:

   [http://localhost:9001/hmc/hybris](http://localhost:9001/hmc/hybris)

1. Selecteer in het zijpaneel de optie **Systeem** vervolgens **Facet zoeken** vervolgens **Config. met zoekopdrachten in facetten**.
1. **Editor openen** voor de **Sample Solr Configuration for clothescatalog**.

1. Onder **Catalogusversies** gebruiken **Catalogusversie toevoegen** toevoegen `outdoors-Staged` en `outdoors-Online` aan de lijst.
1. **Opslaan** de configuratie.
1. Openen **Soorten SOLR-item** toevoegen **SOLR Sorts** tot `ClothesVariantProduct`:

   * relevantie (&quot;Relevance&quot;, score)
   * name-asc (&quot;Naam (oplopend)&quot;, naam)
   * name-desc (&quot;Name (descending)&quot;, name)
   * price-asc (&quot;Price (oplopend)&quot;, priceValue)
   * prijs-desc (&quot;Prijs (aflopend)&quot;, prijsWaarde)

   >[!NOTE]
   >
   >Gebruik het contextmenu (meestal klikken met de rechtermuisknop) om `Create Solr sort`.
   >
   >Voor Hybris 5.0.0 opent u de `Indexed Types` tab, dubbelklikken `ClothesVariantProduct`, dan de tab `SOLR Sort`.

   ![chlimage_1-36](/help/sites-administering/assets/chlimage_1-36a.png)

1. In de **Geïndexeerde typen** tabblad, stelt u de **Samengesteld type** tot:

   `Product - Product`

1. In de **Geïndexeerde typen** tabblad, wijzigt u de **Indexeervragen** for `full`:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}})
   ```

1. In de **Geïndexeerde typen** tabblad, wijzigt u de **Indexeervragen** for `incremental`:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}}) AND {modifiedtime} <= ?lastIndexTime
   ```

1. In de **Geïndexeerde typen** tabblad, wijzigt u de `category` facet. Dubbelklik op het laatste item in de categorielijst om het dialoogvenster **Geïndexeerde eigenschap** tab:

   >[!NOTE]
   >
   >Controleer of bij hybris 5.2 de `Facet` wordt het kenmerk in de tabel Eigenschappen geselecteerd op basis van de onderstaande schermafbeelding:

   ![chlimage_1-37](/help/sites-administering/assets/chlimage_1-37a.png) ![chlimage_1-38](/help/sites-administering/assets/chlimage_1-38a.png)

1. Open de **Instellingen facet** en pas de veldwaarden aan:

   ![chlimage_1-39](/help/sites-administering/assets/chlimage_1-39a.png)

1. **Opslaan** de wijzigingen.
1. Opnieuw van **Soorten SOLR-item**, wijzigt u de `price` facet volgens de volgende schermafbeeldingen. Zoals met `category`, dubbelklikken `price` om de **Geïndexeerde eigenschap** tab:

   ![chlimage_1-40](/help/sites-administering/assets/chlimage_1-40a.png)

1. Open de **Instellingen facet** en pas de veldwaarden aan:

   ![chlimage_1-41](/help/sites-administering/assets/chlimage_1-41a.png)

1. **Opslaan** de wijzigingen.
1. Openen **Systeem**, **Facet zoeken** vervolgens **Wizard Indexeerbewerking**. Een ronjob starten:

   * **Indexeerbewerking**: `full`
   * **Solr-configuratie**: `Sample Solr Config for Clothes`

## De catalogusversie configureren {#configure-the-catalog-version}

De **Catalogusversie** ( `hybris.catalog.version`) die wordt ingevoerd kan voor de dienst worden gevormd OSGi:

**Configuratie bedrijfs-hybride van dagelijkse CQ-handel**
( `com.adobe.cq.commerce.hybris.common.DefaultHybrisConfigurationService`)

**Catalogusversie** is ingesteld op `Online` of `Staged` (de standaardwaarde).

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

De logboekoutput verstrekt terugkoppelen op de gecreeerde pagina&#39;s en de componenten en meldt potentiële fouten.

## De importstructuur configureren {#configure-the-import-structure}

Hieronder ziet u een voorbeeldstructuur (van elementen, pagina&#39;s en componenten) die standaard wordt gemaakt:

```shell
+ /content/dam/path/to/images
  + 12345.jpg (dam:Asset)
    + ...
  + ...
+ /content/site/en
  - cq:commerceProvider = "hybris"
  - cq:hybrisBaseStore = "basestore"
  - cq:hybrisCatalogId = "catalog"
  + category1 (cq:Page)
    + jcr:content (cq:PageContent)
      - jcr:title = "Category 1"
    + category11 (cq:Page)
      + jcr:content (cq:PageContent)
        - jcr:title = "Category 1.1"
      + 12345 (cq:Page)
        + jcr:content (cq:PageContent)
          + par
            + product (nt:unstructured)
              - cq:hybrisProductId = "12345"
              - sling:resourceType = "commerce/components/product"
              + image (nt:unstructured)
                - sling:resourceType = "commerce/components/product/image"
                - fileReference = "/content/dam/path/to/images/12345.jpg"
              + 12345.1-S (nt:unstructured)
                - cq:hybrisProductId = "12345.1-S"
                - sling:resourceType = "commerce/components/product"
                + image (nt:unstructured)
                  - sling:resourceType = "commerce/components/product/image"
                  - fileReference = "/content/dam/path/to/images/12345.1-S.jpg"
              + ...
```

Een dergelijke structuur wordt gecreëerd door de OSGi-dienst `DefaultImportHandler` die de `ImportHandler` interface. De importer zelf roept een importhandler op om producten, productvariaties, categorieën, elementen enzovoort te maken.

>[!NOTE]
>
>U kunt [dit proces aanpassen door uw eigen importhandler te implementeren](#configure-the-import-structure).

De structuur die bij het importeren moet worden gegenereerd, kan worden geconfigureerd voor:

&quot;**Day CQ Commerce Hybris, standaardimporthandler**
`(com.adobe.cq.commerce.hybris.importer.DefaultImportHandler`)

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

## De te laden productkenmerken configureren {#configure-the-product-attributes-to-load}

De reactiesparser kan worden gevormd om de eigenschappen en de attributen te bepalen die voor (variant) producten moeten worden geladen:

1. Vorm de bundel OSGi:

   **Day CQ Commerce Hybris Default Response Parser**
(`com.adobe.cq.commerce.hybris.impl.importer.DefaultResponseParser`)

   Hier kunt u verschillende opties en kenmerken definiëren die nodig zijn voor laden en toewijzen.

   >[!NOTE]
   >
   >Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

## De productgegevens importeren {#importing-the-product-data}

Er zijn verschillende manieren om de productgegevens te importeren. De productgegevens kunnen worden geïmporteerd bij de eerste installatie van de omgeving of nadat er wijzigingen zijn aangebracht in de hybrisgegevens:

* [Volledig importeren](#full-import)
* [Incrementele import](#incremental-import)
* [Uitdrukkelijke Update](#express-update)

Werkelijke productinformatie geïmporteerd uit hybris wordt in de gegevensopslagplaats bewaard onder:

`/etc/commerce/products`

De volgende eigenschappen geven het verband met hybris aan:

* `commerceProvider`
* `cq:hybrisCatalogId`
* `cq:hybrisProductID`

>[!NOTE]
>
>De hybris-implementatie (dat wil zeggen `geometrixx-outdoors/en_US`) slaat alleen product-id&#39;s en andere basisinformatie op onder `/etc/commerce`.
>
>Telkens wanneer informatie over een product wordt aangevraagd, wordt verwezen naar de hybrisserver.

### Volledig importeren {#full-import}

1. Verwijder zo nodig alle bestaande productgegevens met behulp van CRXDE Lite.

   1. Navigeer naar de substructuur met de productgegevens:

      `/etc/commerce/products`

      Bijvoorbeeld:

      [`http://localhost:4502/crx/de/index.jsp#/etc/commerce/products`](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

   1. Verwijder het knooppunt dat de productgegevens bevat, bijvoorbeeld `outdoors`.
   1. **Alles opslaan** om de wijziging voort te zetten.

1. Open de hybris-importmodule in AEM:

   `/etc/importers/hybris.html`

   Bijvoorbeeld:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Configureer de vereiste parameters, bijvoorbeeld:

   ![chlimage_1-42](/help/sites-administering/assets/chlimage_1-42a.png)

1. Klikken **Catalogus importeren** om het importeren te starten.

   Wanneer u klaar bent, kunt u de geïmporteerde gegevens verifiëren op:

   ```
       /etc/commerce/products/outdoors
   ```

   U kunt dit openen in CRXDE Lite, bijvoorbeeld:

   `[http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)`

### Incrementele import {#incremental-import}

1. Controleer de informatie die in AEM voor de betrokken producten is opgeslagen, in de desbetreffende substructuur onder:

   `/etc/commerce/products`

   U kunt dit openen in CRXDE Lite, bijvoorbeeld:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Werk in hybris de informatie over de desbetreffende producten bij.

1. Open de hybris-importmodule in AEM:

   `/etc/importers/hybris.html`

   Bijvoorbeeld:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Selecteren met het selectievakje **Incrementele import**.
1. Klikken **Catalogus importeren** om het importeren te starten.

   Na voltooiing kunt u de gegevens controleren die in AEM onder worden bijgewerkt:

   ```
       /etc/commerce/products
   ```


### Uitdrukkelijke Update {#express-update}

Het importproces kan lang duren, zodat u als uitbreiding van de productsynchronisatie specifieke gebieden van de catalogus kunt selecteren voor een express update die handmatig wordt geactiveerd. Dit gebruikt de de uitvoervoer samen met de standaardattributenconfiguratie.

1. Controleer de informatie die in AEM voor de betrokken producten is opgeslagen, in de desbetreffende substructuur onder:

   `/etc/commerce/products`

   U kunt dit openen in CRXDE Lite, bijvoorbeeld:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Werk in hybris de informatie over de desbetreffende producten bij.

1. In hybris, voeg één of meerdere producten aan de Uitdrukkelijke Rij toe; bijvoorbeeld:

   ![chlimage_1-43](/help/sites-administering/assets/chlimage_1-43a.png)

1. Open de hybris-importmodule in AEM:

   `/etc/importers/hybris.html`

   Bijvoorbeeld:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Selecteren met het selectievakje **Uitdrukkelijke Update**.
1. Klikken **Catalogus importeren** om het importeren te starten.

   Na voltooiing kunt u de gegevens controleren die in AEM onder worden bijgewerkt:

   ```
       /etc/commerce/products
   ```

## De importmodule voor catalogi configureren {#configure-the-catalog-importer}

De hybriscatalogus kan in AEM worden geïmporteerd, waarbij de batchimporter voor hybriscatalogi, -categorieën en -producten wordt gebruikt.

De parameters die door de importeur worden gebruikt, kunnen worden geconfigureerd voor:

**Dag CQ-handel Hybris-catalogus Importeren**
( `com.adobe.cq.commerce.hybris.impl.importer.DefaultHybrisImporter`)

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

## Catalogus importeren {#catalog-import}

Het hybris-pakket wordt geleverd met een catalogusimportmodule waarmee u de structuur van de eerste pagina kunt instellen.

Dit is beschikbaar op:

`http://localhost:4502/etc/importers/hybris.html`

![ecommerceimportconsole](/help/sites-administering/assets/ecommerceimportconsole.png)

De volgende informatie moet worden verstrekt:

* **Basisarchief**
De id van de basisopslag die in hybris is is geconfigureerd.

* **Catalogus**
De id van de te importeren catalogus.

* **Basispad**
Het pad waarin de catalogus moet worden geïmporteerd.

## Een product uit de catalogus verwijderen {#removing-a-product-from-the-catalog}

Een of meer producten uit de catalogus verwijderen:

1. [Vorm voor de dienst OSGi](/help/sites-deploying/configuring-osgi.md) **Dag CQ-handel Hybris-catalogus Importeren**; zie ook [De importmodule voor catalogi configureren](#configure-the-catalog-importer).

   Activeer de volgende eigenschappen:

   * **Productverwijdering inschakelen**
   * **Verwijderen van productelementen inschakelen**

   >[!NOTE]
   >
   >Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

1. Initialiseer de importer door twee incrementele updates uit te voeren (zie [Catalogus importeren](#catalog-import)):

   * De eerste runtime resulteert in een reeks gewijzigde producten - die in de logboeklijst worden vermeld.
   * Voor de tweede keer mogen geen producten worden bijgewerkt.

   >[!NOTE]
   >
   >De eerste importactie is het initialiseren van de productinformatie. Bij de tweede importbewerking wordt gecontroleerd of alles is bewerkt en of de productset klaar is.

1. Controleer de categoriepagina met het product dat u wilt verwijderen. De productdetails moeten zichtbaar zijn.

   De volgende categorie bevat bijvoorbeeld details van het Cajamara-product:

   [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

1. Verwijder het product uit de hybrisconsole. De optie gebruiken **Goedkeuringsstatus wijzigen** om de status in te stellen op `unapproved`. Het product wordt uit het levend voer verwijderd.

   Bijvoorbeeld:

   * De pagina openen [http://localhost:9001/productcockpit](http://localhost:9001/productcockpit)
   * De catalogus selecteren `Outdoors Staged`
   * Zoeken naar `Cajamara`
   * Selecteer dit product en wijzig de goedkeuringsstatus in `unapproved`

1. Nog een incrementele update uitvoeren (zie [Catalogus importeren](#catalog-import)). In het logbestand wordt het verwijderde product weergegeven.
1. [Uitrol](/help/commerce/cif-classic/administering/generic.md#rolling-out-a-catalog) de passende catalogus. De product- en productpagina zijn uit AEM verwijderd.

   Bijvoorbeeld:

   * Openen:

     [http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris](http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris)

   * De `Hybris Base` catalogus
   * Openen:

     [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

   * De `Cajamara` het product wordt uit de `Bike` categorie

1. Het product opnieuw installeren:

   1. Stel de goedkeuringsstatus in op hybris **goedgekeurd**
   1. In AEM:

      1. een incrementele update uitvoeren
      1. de desbetreffende catalogus opnieuw uitvoeren
      1. De juiste categoriepagina vernieuwen

## Bedieningshistoriereis toevoegen aan de clientcontext {#add-order-history-trait-to-the-client-context}

Orderhistorie toevoegen aan de [clientcontext](/help/sites-developing/client-context.md):

1. Open de [ontwerppagina voor clientcontext](/help/sites-administering/client-context.md)door:

   * Open een pagina om te bewerken en open de clientcontext met **Ctrl-Alt-c** (ramen) of **control-option-c** (Mac) Gebruik het potloodpictogram in de linkerbovenhoek van de clientcontext om **De pagina voor het ontwerpen van ClientContexten openen**.
   * Ga rechtstreeks naar [http://localhost:4502/etc/clientcontext/default/content.html](http://localhost:4502/etc/clientcontext/default/content.html)

1. [Voeg de **Orderhistorie** component](/help/sites-administering/client-context.md#adding-a-property-component) aan de **Winkelwagen** t component van de clientcontext.
1. U kunt bevestigen dat de context van de client details van uw ordergeschiedenis weergeeft. Bijvoorbeeld:

   1. Open de [clientcontext](/help/sites-administering/client-context.md).
   1. Voeg een item aan het winkelwagentje toe.
   1. Voltooi het afrekenen.
   1. Controleer de clientcontext.
   1. Voeg nog een item aan het winkelwagentje toe.
   1. Navigeer naar de uitcheckpagina:

      * De clientcontext geeft een overzicht van de ordergeschiedenis.
      * Het bericht &quot;U bent een terugkerende klant&quot; wordt weergegeven.

   >[!NOTE]
   >
   >Het bericht wordt gerealiseerd door:
   >
   >* Navigeren naar [http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html](http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html)
   >
   >  De campagne bestaat uit één ervaring.
   >
   >* Klik op het segment ([http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html](http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html))
   >
   >* Het segment wordt gebouwd gebruikend **Orderhistorie, eigenschap** eigenschap.
