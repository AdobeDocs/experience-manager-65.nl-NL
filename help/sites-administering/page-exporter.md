---
title: De pagina-exportfunctie
description: Leer hoe u de pagina-exportfunctie van Adobe Experience Manager (AEM) gebruikt.
exl-id: 15d08758-cf75-43c0-9818-98a579d64183
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# De pagina-exportfunctie{#the-page-exporter}

Met Adobe Experience Manager (AEM) kunt u een pagina exporteren als een volledige webpagina, inclusief afbeeldingen, `.js`, en `.css` bestanden.

Indien geconfigureerd, vraagt u een paginaexport van uw browser door `html` with `export.zip` in de URL. Hiermee wordt een archiefbestand (zip) gegenereerd dat de weergegeven pagina in HTML-indeling bevat, samen met de elementen waarnaar wordt verwezen. Alle paden op de pagina (bijvoorbeeld paden naar afbeeldingen) worden herschreven zodat ze verwijzen naar de bestanden die in het archief zijn opgenomen of naar de bronnen op de server. Het archiefbestand (zip) kan vervolgens vanuit uw browser worden gedownload.

>[!NOTE]
>
>Afhankelijk van uw browser en de instellingen is de download:
>
>* een archiefbestand (`<page-name>.export.zip`)
>* een map (`<page-name>`); het archiefbestand is al uitgevouwen

## Pagina&#39;s exporteren {#exporting-a-page}

In de volgende stappen wordt beschreven hoe u een pagina exporteert en wordt ervan uitgegaan dat er een exportsjabloon voor uw site bestaat. Een exportsjabloon definieert de manier waarop een pagina wordt geëxporteerd en is specifiek voor uw site. Als u een exportsjabloon wilt maken, raadpleegt u [Een configuratie voor paginaexportters maken voor uw site](#creating-a-page-exporter-configuration-for-your-site).

Een pagina exporteren:

1. Ga naar de gewenste pagina in het dialoogvenster **Sites** console.

1. Selecteer de pagina en open vervolgens de knop **Eigenschappen** in.

1. Selecteer de **Geavanceerd** tab.

1. Breid uit **Exporteren** te selecteren.
Selecteer de vereiste sjabloon voor uw site en bevestig vervolgens met **OK**.

1. Selecteren **Opslaan en sluiten** om het dialoogvenster Pagina-eigenschappen te sluiten.

1. De pagina voor export aanvragen en het achtervoegsel vervangen `html` with `export.zip` in de URL.

   Bijvoorbeeld:
   * localhost:4502/content/we-retail/language-masters/en.html

   Wordt benaderd door:
   * localhost:4502/content/we-retail/language-masters/en.export.zip

1. Download het archiefbestand naar uw bestandssysteem.

1. Pak het bestand desgewenst uit in uw bestandssysteem. Als deze is uitgevouwen, ziet u een map met dezelfde naam als de geselecteerde pagina. Deze map bevat:

   * de submap `content`, de basis van een reeks submappen die het pad naar de pagina in de opslagplaats weerspiegelen

      * binnen deze structuur is er het HTML-bestand voor de geselecteerde pagina (`<page-name>.html`)

   * overige middelen (`.js` bestanden, `.css` bestanden, afbeeldingen, enzovoort) bevinden zich volgens de instellingen in de exportsjabloon

1. Open het HTML-bestand van de pagina (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) in uw browser, zodat u de rendering kunt controleren.

## Een configuratie voor paginaexportters maken voor uw site {#creating-a-page-exporter-configuration-for-your-site}

De pagina-exportfunctie is gebaseerd op de [Content Sync-framework](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/contentsync/package-summary.html). De configuraties die in **Pagina-eigenschappen** dialoogvensters zijn exportsjablonen die de vereiste afhankelijkheden voor een pagina definiëren.

Wanneer het exporteren van een pagina wordt geactiveerd, wordt naar de exportsjabloon verwezen. Zowel het paginapad als het ontwerppad worden dynamisch toegepast. Het ZIP-bestand wordt vervolgens gemaakt met de standaardfunctionaliteit voor het synchroniseren van inhoud.

Een uit-van-de-doos AEM installatie omvat een standaardmalplaatje onder `/etc/contentsync/templates/default`.

* Deze sjabloon is de fallback-sjabloon wanneer er geen exportsjabloon wordt gevonden in de repository.

* De `default` het malplaatje toont u hoe een paginauitvoer kan worden gevormd, zodat kan als basis voor een nieuw de uitvoermalplaatje dienen.

* Als u de knooppuntstructuur van de sjabloon in uw browser wilt weergeven als JSON-indeling, vraagt u de volgende URL op:
  `http://localhost:4502/etc/contentsync/templates/default.json`

De eenvoudigste methode om een sjabloon voor het exporteren van pagina&#39;s te maken is:

* kopieer de `default` sjabloon,

* een nieuwe naam toewijzen die geschikt is voor uw site;

* Voer vervolgens de vereiste updates uit.

Een volledig nieuwe sjabloon maken:

1. In **CRXDE Lite**, maak hieronder een knooppunt `/etc/contentsync/templates`:

   * `Name`: een naam die geschikt is voor uw site, bijvoorbeeld `<mysite>`. De naam wordt weergegeven in het dialoogvenster Pagina-eigenschappen wanneer u de sjabloon voor het exporteren van pagina&#39;s kiest.

   * `Type`: `nt:unstructured`

2. Onder het sjabloonknooppunt dat hier wordt aangeroepen `mysite`, maakt u een knooppuntstructuur met behulp van de hieronder beschreven configuratieknooppunten.

## Een paginamarittersjabloon activeren voor uw pagina&#39;s {#activating-a-page-exporter-configuration-for-your-pages}

Wanneer uw malplaatje wordt gevormd, maak het beschikbaar:

1. In CRXDE navigeer aan de vereiste pagina in `/content` vertakking. Dit kan een afzonderlijke pagina zijn, of de basispagina van een substructuur.

1. Op de `jcr:content` knooppunt van de pagina, maakt u de eigenschap:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: pad naar de sjabloon, bijvoorbeeld: `/etc/contentsync/templates/mysite`

### Configuratieknooppunten van pagina-exporteur {#page-exporter-configuration-nodes}

De sjabloon bestaat uit een knooppuntstructuur, omdat deze de [Content Sync-framework](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/contentsync/package-summary.html). Elk knooppunt heeft een `type` eigenschap die een specifieke handeling definieert in het aanmaakproces van het ZIP-bestand.

<!-- For more details about the type property, see the Overview of configuration types section in the Content Sync framework page.
-->

De volgende knooppunten kunnen worden gebruikt om een exportsjabloon te maken:

* `page`
Het paginaknooppunt wordt gebruikt om pagina html aan het ZIP dossier te kopiëren. Het heeft de volgende kenmerken:

   * Een verplicht knooppunt.
   * Vergrendeld onder `/etc/contentsync/templates/<mysite>`.
   * Gedefinieerd met de eigenschap `Name`instellen op `page`.
   * Node type is `nt:unstructured`

  De `page` node heeft de volgende eigenschappen:

   * A `type` eigenschap ingesteld met de waarde `pages`.

   * Het heeft geen `path` eigenschap als het huidige paginapad dynamisch naar de configuratie gekopieerd.
  <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
Het knooppunt rewrite definieert hoe de koppelingen in de geëxporteerde pagina worden herschreven. De herschreven koppelingen kunnen verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.
  <!-- See the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
Het ontwerpknooppunt wordt gebruikt om het ontwerp te kopiëren dat voor de geëxporteerde pagina wordt gebruikt. Het heeft de volgende kenmerken:

   * Optioneel.
   * Vergrendeld onder `/etc/contentsync/templates/<mysite>`.
   * Gedefinieerd met de eigenschap `Name` instellen op `design`.
   * Node type is `nt:unstructured`.

  De `design` node heeft de volgende eigenschappen:

   * A `type` eigenschap ingesteld op de waarde `copy`.

   * Het heeft geen `path` eigenschap, aangezien het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.

* `generic`
Een generisch knooppunt wordt gebruikt om bronnen als clientlibs te kopiëren `.js` of `.css` naar het ZIP-bestand. Het heeft de volgende kenmerken:

   * Optioneel.
   * Vergrendeld onder `/etc/contentsync/templates/<mysite>`.
   * Geen specifieke naam.
   * Node type is `nt:unstructured`.
   * Heeft een `type` eigendom en `type` verwante eigenschappen. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

  De volgende configuratieknooppunt kopieert bijvoorbeeld de `mysite.clientlibs.js` bestanden naar het ZIP-bestand:

  ```xml
  "mysite.clientlibs.js": {
      "extension": "js",
      "type": "clientlib",
      "path": "/etc/designs/mysite/clientlibs",
      "jcr:primaryType": "nt:unstructured"
  }
  ```

**Een aangepaste configuratie implementeren**

Aangepaste configuraties zijn ook mogelijk.

<!--
As you may have noticed in the node structure, the **Geometrixx** page export template has a `logo` node with a `type` property set to `image`. This is a special configuration type that has been created to copy the image logo to the zip file. 
-->

Om aan bepaalde specifieke vereisten te voldoen, voert u een [aangepaste update-handler](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/contentsync/handler/package-summary.html).

<!-- To meet some specific requirements, you may need to implement a custom `type` property. To do so, see the Implementing a custom update handler section in the Content Sync page.
-->

## Pagina&#39;s programmatisch exporteren {#programmatically-exporting-a-page}

Als u een pagina programmatisch wilt exporteren, kunt u de opdracht [PageExporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI-dienst. Met deze service kunt u:

* Exporteer een pagina en schrijf naar de HTTP-servletreactie.
* Exporteer een pagina en sla het ZIP-bestand op een specifieke locatie op.

De servlet die aan `export` en de `zip` gebruikt de PageExporter-service.

## Problemen oplossen {#troubleshooting}

Als u een probleem ondervindt met het downloaden van het ZIP-bestand, kunt u het `/var/contentsync` in de gegevensopslagruimte en het exportverzoek opnieuw verzenden.
