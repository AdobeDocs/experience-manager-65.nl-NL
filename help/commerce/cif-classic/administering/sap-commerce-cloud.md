---
title: AEM gebruiken met SAP-Commerce Cloud
description: Leer hoe u Adobe Experience Manager met SAP-Commerce Cloud kunt gebruiken.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: c342f789-2ff7-4802-99c7-c3699218fe47
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 0%

---

# SAP-Commerce Cloud{#sap-commerce-cloud}

Na de installatie kunt u uw instantie configureren:

1. [&#x200B; vorm het Gefacceerde Onderzoek naar Geometrixx Outdoors &#x200B;](#configure-the-facetted-search-for-geometrixx-outdoors).
1. [&#x200B; vorm de Versie van de Catalogus &#x200B;](#configure-the-catalog-version).
1. [&#x200B; vorm de Structuur van de Invoer &#x200B;](#configure-the-import-structure).
1. [&#x200B; vorm de Attributen van het Product aan Lading &#x200B;](#configure-the-product-attributes-to-load).
1. [&#x200B; het Invoeren van de Gegevens van het Product &#x200B;](#importing-the-product-data).
1. [&#x200B; vorm de Importeur van de Catalogus &#x200B;](#configure-the-catalog-importer).
1. Gebruik [&#x200B; importeur om de catalogus &#x200B;](#catalog-import) in een specifieke plaats in AEM in te voeren.

## De beperkte zoekopdracht naar Geometrixx Outdoors configureren {#configure-the-facetted-search-for-geometrixx-outdoors}

>[!NOTE]
>
>Dit is niet nodig voor hybris 5.3.0.1 en hoger.

1. In uw browser, navigeer aan de **hybris beheersconsole** bij:

   [&#x200B; http://localhost:9001/hmc/hybris](http://localhost:9001/hmc/hybris)

1. Van sidebar, uitgezochte **Systeem**, toen **Onderzoek van het Facet**, toen **Config van het Onderzoek van het Facet**.
1. **Open Redacteur** voor de **Steekproef Solr Configuratie voor clothesecatalogus**.

1. Onder **de versies van de Catalogus** gebruik **voegt de versie van de Catalogus** toe om `outdoors-Staged` en `outdoors-Online` aan de lijst toe te voegen.
1. **sparen** de configuratie.
1. Open {de types van Punt 0} SOLR **om** SOLR toe te voegen sorteert **aan `ClothesVariantProduct`:**

   * relevantie (&quot;Relevance&quot;, score)
   * name-asc (&quot;Naam (oplopend)&quot;, naam)
   * name-desc (&quot;Name (descending)&quot;, name)
   * price-asc (&quot;Price (oplopend)&quot;, priceValue)
   * prijs-desc (&quot;Prijs (aflopend)&quot;, prijsWaarde)

   >[!NOTE]
   >
   >Selecteer `Create Solr sort` in het contextmenu (klik meestal met de rechtermuisknop).
   >
   >Voor Hybris 5.0.0 opent u het tabblad `Indexed Types` , dubbelklikt u op `ClothesVariantProduct` en vervolgens het tabblad `SOLR Sort` .

   ![&#x200B; chlimage_1-36 &#x200B;](/help/sites-administering/assets/chlimage_1-36a.png)

1. In het **Geïndexeerde Types** lusje, plaats het **Samengestelde Type** aan:

   `Product - Product`

1. In **Geïndexeerde Types** tabel, pas de **vragen van de Indexer** voor `full` aan:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}})
   ```

1. In **Geïndexeerde Types** tabel, pas de **vragen van de Indexer** voor `incremental` aan:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}}) AND {modifiedtime} <= ?lastIndexTime
   ```

1. In de **Geïndexeerde Types** tabel, pas het `category` facet aan. Dubbelklik de laatste ingang in de categorielijst om het **Geïndexeerde bezit** lusje te openen:

   >[!NOTE]
   >
   >Controleer of voor hybris 5.2 het kenmerk `Facet` in de tabel Eigenschappen is geselecteerd op basis van de onderstaande schermafbeelding:

   ![&#x200B; chlimage_1-37 &#x200B;](/help/sites-administering/assets/chlimage_1-37a.png) ![&#x200B; chlimage_1-38 &#x200B;](/help/sites-administering/assets/chlimage_1-38a.png)

1. Open het **lusje van de Montages van het Facet** en pas de gebiedswaarden aan:

   ![&#x200B; chlimage_1-39 &#x200B;](/help/sites-administering/assets/chlimage_1-39a.png)

1. **sparen** de veranderingen.
1. Nogmaals van **de types van Punt van het SOLR**, pas het `price` facet volgens de volgende screenshots aan. Zoals met `category`, klik `price` tweemaal om het **Geïndexeerde bezit** tabel te openen:

   ![&#x200B; chlimage_1-40 &#x200B;](/help/sites-administering/assets/chlimage_1-40a.png)

1. Open het **lusje van de Montages van het Facet** en pas de gebiedswaarden aan:

   ![&#x200B; chlimage_1-41 &#x200B;](/help/sites-administering/assets/chlimage_1-41a.png)

1. **sparen** de veranderingen.
1. Open **Systeem**, **Onderzoek van het Facet**, toen **tovenaar van de de verrichtingenverrichting van de Indexer**. Een ronjob starten:

   * **verrichting van de Indexer**: `full`
   * **Solr configuratie**: `Sample Solr Config for Clothes`

## De catalogusversie configureren {#configure-the-catalog-version}

De **versie van de Catalogus** ( `hybris.catalog.version`) die wordt ingevoerd kan voor de dienst worden gevormd OSGi:

**Dag CQ Commerce Hybris Configuratie**
( `com.adobe.cq.commerce.hybris.common.DefaultHybrisConfigurationService`)

**de versie van de Catalogus** wordt geplaatst aan of `Online` of `Staged` (het gebrek).

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor volledige details. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

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

Een dergelijke structuur wordt gemaakt door de OSGi-service `DefaultImportHandler` die de `ImportHandler` -interface implementeert. De importer zelf roept een importhandler op om producten, productvariaties, categorieën, elementen enzovoort te maken.

>[!NOTE]
>
>U kunt [&#x200B; dit proces aanpassen door uw eigen invoermanager &#x200B;](#configure-the-import-structure) uit te voeren.

De structuur die bij het importeren moet worden gegenereerd, kan worden geconfigureerd voor:

&quot;**Dag CQ Commerce Hybris Standaard de Handler van de Invoer**
`(com.adobe.cq.commerce.hybris.importer.DefaultImportHandler` )

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor volledige details. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

## De te laden productkenmerken configureren {#configure-the-product-attributes-to-load}

De reactiesparser kan worden gevormd om de eigenschappen en de attributen te bepalen die voor (variant) producten moeten worden geladen:

1. Vorm de bundel OSGi:

   **De Parser van de Reactie van de Standaard van Commerce van de Dag CQ &lbrace;**
(`com.adobe.cq.commerce.hybris.impl.importer.DefaultResponseParser`)

   Hier kunt u verschillende opties en kenmerken definiëren die nodig zijn voor laden en toewijzen.

   >[!NOTE]
   >
   >Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor volledige details. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

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
>In de hybris-implementatie (dat wil zeggen `geometrixx-outdoors/en_US` ) worden alleen product-id&#39;s en andere basisinformatie onder `/etc/commerce` opgeslagen.
>
>Telkens wanneer informatie over een product wordt aangevraagd, wordt verwezen naar de hybrisserver.

### Volledig importeren {#full-import}

1. Verwijder zo nodig alle bestaande productgegevens met behulp van CRXDE Lite.

   1. Navigeer naar de substructuur met de productgegevens:

      `/etc/commerce/products`

      Bijvoorbeeld:

      [`http://localhost:4502/crx/de/index.jsp#/etc/commerce/products`](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

   1. Verwijder het knooppunt dat de productgegevens bevat, bijvoorbeeld `outdoors` .
   1. **sparen allen** om de verandering voort te zetten.

1. Open de hybris-importmodule in AEM:

   `/etc/importers/hybris.html`

   Bijvoorbeeld:

   [&#x200B; http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Configureer de vereiste parameters, bijvoorbeeld:

   ![&#x200B; chlimage_1-42 &#x200B;](/help/sites-administering/assets/chlimage_1-42a.png)

1. Klik **de Catalogus van de Invoer** om de invoer te beginnen.

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

   [&#x200B; http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Werk in hybris de informatie over de desbetreffende producten bij.

1. Open de hybris-importmodule in AEM:

   `/etc/importers/hybris.html`

   Bijvoorbeeld:

   [&#x200B; http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Selecteer checkbox **Incrementele Invoer**.
1. Klik **de Catalogus van de Invoer** om de invoer te beginnen.

   Na voltooiing kunt u de gegevens controleren die in AEM onder worden bijgewerkt:

   ```
       /etc/commerce/products
   ```


### Uitdrukkelijke Update {#express-update}

Het importproces kan lang duren, zodat u als uitbreiding van de productsynchronisatie specifieke gebieden van de catalogus kunt selecteren voor een express update die handmatig wordt geactiveerd. Dit gebruikt de de uitvoervoer samen met de standaardattributenconfiguratie.

1. Controleer de informatie die in AEM voor de betrokken producten is opgeslagen, in de desbetreffende substructuur onder:

   `/etc/commerce/products`

   U kunt dit openen in CRXDE Lite, bijvoorbeeld:

   [&#x200B; http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Werk in hybris de informatie over de desbetreffende producten bij.

1. In hybris, voeg één of meerdere producten aan de Uitdrukkelijke Rij toe; bijvoorbeeld:

   ![&#x200B; chlimage_1-43 &#x200B;](/help/sites-administering/assets/chlimage_1-43a.png)

1. Open de hybris-importmodule in AEM:

   `/etc/importers/hybris.html`

   Bijvoorbeeld:

   [&#x200B; http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Selecteer checkbox **Uitdrukkelijke Update**.
1. Klik **de Catalogus van de Invoer** om de invoer te beginnen.

   Na voltooiing kunt u de gegevens controleren die in AEM onder worden bijgewerkt:

   ```
       /etc/commerce/products
   ```

## De importmodule voor catalogi configureren {#configure-the-catalog-importer}

De hybriscatalogus kan in AEM worden geïmporteerd, waarbij de batchimporter voor hybriscatalogi, -categorieën en -producten wordt gebruikt.

De parameters die door de importeur worden gebruikt, kunnen worden geconfigureerd voor:

**Dag CQ Commerce Hybris Catalogus Importer van de Catalogus**
( `com.adobe.cq.commerce.hybris.impl.importer.DefaultHybrisImporter`)

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor volledige details. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

## Catalogus importeren {#catalog-import}

Het hybris-pakket wordt geleverd met een catalogusimportmodule waarmee u de structuur van de eerste pagina kunt instellen.

Dit is beschikbaar op:

`http://localhost:4502/etc/importers/hybris.html`

![&#x200B; ecommerceimportconsole &#x200B;](/help/sites-administering/assets/ecommerceimportconsole.png)

De volgende informatie moet worden verstrekt:

* **opslag van de Basis**
De id van de basisopslag die in hybris is is geconfigureerd.

* **Catalogus**
De id van de te importeren catalogus.

* **Weg van de Wortel**
Het pad waarin de catalogus moet worden geïmporteerd.

## Een product uit de catalogus verwijderen {#removing-a-product-from-the-catalog}

Een of meer producten uit de catalogus verwijderen:

1. [&#x200B; vormt voor de dienst OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) **Dag CQ de Importeur van de Catalogus van de Hybris van Commerce**; zie ook [&#x200B; de Importeur van de Catalogus &#x200B;](#configure-the-catalog-importer) vormen.

   Activeer de volgende eigenschappen:

   * **laat productverwijdering** toe
   * **laat de verwijdering van productactiva** toe

   >[!NOTE]
   >
   >Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor volledige details. Zie ook de console voor een volledige lijst van configureerbare parameters en hun gebreken.

1. Initialiseer de importer door twee stijgende updates uit te voeren (zie {de Invoer van de Catalogus 0} [&#128279;](#catalog-import)):

   * De eerste runtime resulteert in een reeks gewijzigde producten - die in de logboeklijst worden vermeld.
   * Voor de tweede keer mogen geen producten worden bijgewerkt.

   >[!NOTE]
   >
   >De eerste importactie is het initialiseren van de productinformatie. Bij de tweede importbewerking wordt gecontroleerd of alles is bewerkt en of de productset klaar is.

1. Controleer de categoriepagina met het product dat u wilt verwijderen. De productdetails moeten zichtbaar zijn.

   De volgende categorie bevat bijvoorbeeld details van het Cajamara-product:

   [&#x200B; http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

1. Verwijder het product uit de hybrisconsole. Gebruik de optie **goedkeuringsstatus van de Verandering** om de status aan `unapproved` te plaatsen. Het product wordt uit het levend voer verwijderd.

   Bijvoorbeeld:

   * Open de pagina [&#x200B; http://localhost:9001/productcockpit](http://localhost:9001/productcockpit)
   * De catalogus selecteren `Outdoors Staged`
   * Zoeken naar `Cajamara`
   * Selecteer dit product en wijzig de goedkeuringsstatus in `unapproved`

1. Voer een andere stijgende update uit (zie {de Invoer van de Catalogus 0} [&#128279;](#catalog-import)).  In het logbestand wordt het verwijderde product weergegeven.
1. [&#x200B; Uitvoer &#x200B;](/help/commerce/cif-classic/administering/generic.md#rolling-out-a-catalog) de aangewezen catalogus. De product- en productpagina zijn uit AEM verwijderd.

   Bijvoorbeeld:

   * Openen:

     [&#x200B; http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris](http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris)

   * De catalogus van `Hybris Base` uitvoeren
   * Openen:

     [&#x200B; http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

   * Het `Cajamara` -product wordt verwijderd uit de categorie `Bike`

1. Het product opnieuw installeren:

   1. In hybris, plaats de goedkeuringsstatus terug naar **goedgekeurd**
   1. In AEM:

      1. een incrementele update uitvoeren
      1. de desbetreffende catalogus opnieuw uitvoeren
      1. De juiste categoriepagina vernieuwen

## Bedieningshistoriereis toevoegen aan de clientcontext {#add-order-history-trait-to-the-client-context}

Om ordegeschiedenis aan de [&#x200B; cliëntcontext &#x200B;](/help/sites-developing/client-context.md) toe te voegen:

1. Open de [&#x200B; pagina van het het ontwerpontwerp van de cliëntcontext &#x200B;](/help/sites-administering/client-context.md), door één van beiden:

   * Open een pagina voor het uitgeven, dan open de cliëntcontext gebruikend **CTRL-alt-c** (vensters) of **controle-optie-c** (Mac). Gebruik het potloodpictogram in de hoogste-linkerhoek van de cliëntcontext om **de pagina van het het ontwerpontwerp van de ClientContext** te openen.
   * Navigeer direct aan [&#x200B; http://localhost:4502/etc/clientcontext/default/content.html](http://localhost:4502/etc/clientcontext/default/content.html)

1. [&#x200B; voeg de **2&rbrace; component van de Geschiedenis van de Orde &#x200B;](/help/sites-administering/client-context.md#adding-a-property-component) aan** toe het Shopping Auto **niet component van de cliëntcontext.**
1. U kunt bevestigen dat de context van de client details van uw ordergeschiedenis weergeeft. Bijvoorbeeld:

   1. Open de [&#x200B; cliëntcontext &#x200B;](/help/sites-administering/client-context.md).
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
   >* Navigeer aan [&#x200B; http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html](http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html)
   >
   >  De campagne bestaat uit één ervaring.
   >
   >* Klik het segment ([&#x200B; http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html &#x200B;](http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html))
   >
   >* Het segment wordt gebouwd gebruikend het **spoor van het Bezit van de Geschiedenis van de orde 0&rbrace;.**
