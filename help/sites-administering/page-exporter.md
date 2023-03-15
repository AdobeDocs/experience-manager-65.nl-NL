---
title: De pagina-exportfunctie
description: Leer hoe u de AEM Page Exporter gebruikt.
exl-id: 15d08758-cf75-43c0-9818-98a579d64183
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---

# De pagina-exportfunctie{#the-page-exporter}

AEM kunt u een pagina exporteren als een volledige webpagina met afbeeldingen, `.js` en `.css` bestanden.

Nadat u de configuratie hebt geconfigureerd, vraagt u een pagina-export van uw browser door `html` with `export.zip` in de URL. Hiermee wordt een archiefbestand (zip) gegenereerd dat de weergegeven pagina in HTML-indeling bevat, samen met de elementen waarnaar wordt verwezen. Alle paden op de pagina (bijvoorbeeld paden naar afbeeldingen) worden herschreven zodat ze verwijzen naar de bestanden die in het archief zijn opgenomen of naar de bronnen op de server. Het archiefbestand (zip) kan vervolgens vanuit uw browser worden gedownload.

>[!NOTE]
>
>Afhankelijk van uw browser en de instellingen is de download:
>* een archiefbestand (`<page-name>.export.zip`)
>* een map (`<page-name>`); het archiefbestand is al uitgebreid


## Een pagina exporteren {#exporting-a-page}

In de volgende stappen wordt beschreven hoe u een pagina exporteert en wordt ervan uitgegaan dat er een exportsjabloon voor uw site bestaat. Een exportsjabloon definieert de manier waarop een pagina wordt geëxporteerd en is specifiek voor uw site. Als u een exportsjabloon wilt maken, raadpleegt u de [Een configuratie voor paginaexportters maken voor uw site](#creating-a-page-exporter-configuration-for-your-site) sectie.

Een pagina exporteren:

1. Ga naar de gewenste pagina in het dialoogvenster **Sites** console.

1. Selecteer de pagina en open vervolgens de **Eigenschappen** .

1. Selecteer **Geavanceerd** tab.

1. Breid uit **Exporteren** veld om een exportsjabloon te selecteren.
Selecteer de vereiste sjabloon voor uw site en bevestig vervolgens met **OK**.

1. Selecteren **Opslaan en sluiten** om het dialoogvenster Pagina-eigenschappen te sluiten.

1. De pagina voor export aanvragen en het achtervoegsel vervangen `html` with `export.zip` in de URL.

   Bijvoorbeeld:
   * localhost:4502/content/we-retail/language-masters/en.html

   Wordt benaderd via:
   * localhost:4502/content/we-retail/language-masters/en.export.zip


1. Download het archiefbestand naar uw bestandssysteem.

1. Pak het bestand desgewenst uit in uw bestandssysteem. Nadat de map is uitgevouwen, krijgt deze dezelfde naam als de geselecteerde pagina. Deze map bevat:

   * de submap `content`, de basis van een reeks submappen die het pad naar de pagina in de opslagplaats weerspiegelen

      * binnen deze structuur is er het HTML-bestand voor de geselecteerde pagina (`<page-name>.html`)
   * overige middelen (`.js` bestanden, `.css` bestanden, afbeeldingen enz.) worden geplaatst volgens de instellingen in de exportsjabloon


1. Open het HTML-bestand van de pagina (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) in uw browser om de rendering te controleren.

## Een configuratie voor paginaexportters maken voor uw site {#creating-a-page-exporter-configuration-for-your-site}

De pagina-exportfunctie is gebaseerd op de [Content Sync-framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html). De configuraties die beschikbaar zijn in de **Pagina-eigenschappen** dialoogvensters zijn exportsjablonen die de vereiste afhankelijkheden voor een pagina definiëren.

Wanneer een pagina-export wordt geactiveerd, wordt naar de exportsjabloon verwezen en worden zowel het paginapad als het ontwerppad dynamisch toegepast. Het ZIP-bestand wordt vervolgens gemaakt met de standaardfunctionaliteit voor het synchroniseren van inhoud.

Een uit-van-de-doos AEM installatie omvat een standaardmalplaatje onder `/etc/contentsync/templates/default`.

* Deze sjabloon is de fallback-sjabloon wanneer er geen exportsjabloon wordt gevonden in de repository.

* De `default` het malplaatje toont u hoe een paginauitvoer kan worden gevormd, zodat kan als basis voor een nieuw de uitvoermalplaatje dienen.

* Als u de knooppuntstructuur van de sjabloon in uw browser wilt weergeven als JSON-indeling, vraagt u de volgende URL op:
   `http://localhost:4502/etc/contentsync/templates/default.json`

De eenvoudigste methode om een nieuwe sjabloon voor het exporteren van pagina&#39;s te maken is:

* kopiëren `default` sjabloon,

* een nieuwe naam toewijzen die geschikt is voor uw site;

* Voer vervolgens de vereiste updates uit.

Een volledig nieuwe sjabloon maken:

1. In **CRXDE Lite**, maak hieronder een knooppunt `/etc/contentsync/templates`:

   * `Name`: een naam die geschikt is voor uw site; bijvoorbeeld: `<mysite>`. De naam wordt weergegeven in het dialoogvenster Pagina-eigenschappen wanneer u de sjabloon voor het exporteren van pagina&#39;s kiest.

   * `Type`: `nt:unstructured`

2. Onder het sjabloonknooppunt dat hier wordt aangeroepen `mysite`, maakt u een knooppuntstructuur met de hieronder beschreven configuratieknooppunten.

## Een paginamarittersjabloon activeren voor uw pagina&#39;s {#activating-a-page-exporter-configuration-for-your-pages}

Zodra uw malplaatje is gevormd moet u het ter beschikking stellen:

1. In CRXDE navigeer aan de vereiste pagina in `/content` vertakking. Dit kan een afzonderlijke pagina zijn, of de hoofdpagina van een substructuur.

1. Op de `jcr:content` knooppunt van de pagina maakt de eigenschap:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: pad naar de sjabloon; bijvoorbeeld: `/etc/contentsync/templates/mysite`

### Configuratieknooppunten van pagina-exportfunctie {#page-exporter-configuration-nodes}

De sjabloon bestaat uit een knooppuntstructuur, omdat deze de [Content Sync-framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html).  Elk knooppunt heeft een `type` eigenschap die een specifieke handeling definieert in het aanmaakproces van het ZIP-bestand.

<!-- For more details about the type property, refer to the Overview of configuration types section in the Content Sync framework page.
-->

De volgende knooppunten kunnen worden gebruikt om een exportsjabloon te maken:

* `page`
Het paginaknooppunt wordt gebruikt om de pagina-html naar het ZIP-bestand te kopiëren. Het heeft de volgende kenmerken:

   * Is een verplicht knooppunt.
   * bevindt zich hieronder `/etc/contentsync/templates/<mysite>`.
   * Is gedefinieerd met de eigenschap `Name`instellen op `page`.
   * Het knooppunttype is `nt:unstructured`

   De `page` node heeft de volgende eigenschappen:

   * A `type` eigenschap ingesteld met de waarde `pages`.

   * Het heeft geen `path` eigenschap als het huidige paginapad dynamisch naar de configuratie gekopieerd.

   <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
Het knooppunt rewrite definieert hoe de koppelingen in de geëxporteerde pagina worden herschreven. De herschreven koppelingen kunnen verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.
   <!-- Please refer to the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
Het ontwerpknooppunt wordt gebruikt om het ontwerp te kopiëren dat voor de geëxporteerde pagina wordt gebruikt. Het heeft de volgende kenmerken:

   * Is optioneel.
   * bevindt zich hieronder `/etc/contentsync/templates/<mysite>`.
   * Is gedefinieerd met de eigenschap `Name` instellen op `design`.
   * Het knooppunttype is `nt:unstructured`.

   De `design` node heeft de volgende eigenschappen:

   * A `type` eigenschap ingesteld op de waarde `copy`.

   * Het heeft geen `path` eigenschap, aangezien het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.


* `generic`
Een generisch knooppunt wordt gebruikt om bronnen als clientlibs te kopiëren 
`.js` of `.css` naar het ZIP-bestand. Het heeft de volgende kenmerken:

   * Is optioneel.
   * bevindt zich hieronder `/etc/contentsync/templates/<mysite>`.
   * Heeft geen specifieke naam.
   * Het knooppunttype is `nt:unstructured`.
   * Heeft een `type` eigendom en `type` verwante eigenschappen. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

   De volgende configuratieknooppunten kopiëren bijvoorbeeld de `mysite.clientlibs.js` bestanden naar het ZIP-bestand:

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

Om aan sommige specifieke vereisten te voldoen, kunt u moeten uitvoeren [aangepaste update-handler](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/handler/package-summary.html).

<!-- To meet some specific requirements, you may need to implement a custom `type` property: to do so, refer to the Implementing a custom update handler section in the Content Sync page.
-->

## Een pagina programmatisch exporteren {#programmatically-exporting-a-page}

Als u een pagina programmatisch wilt exporteren, kunt u de opdracht [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI-dienst. Met deze service kunt u:

* Exporteer een pagina en schrijf naar de HTTP-servletreactie.
* Exporteer een pagina en sla het ZIP-bestand op een specifieke locatie op.

De servlet die aan `export` en de `zip` gebruikt de PageExporter-service.

## Problemen oplossen {#troubleshooting}

Als u een probleem ondervindt met het downloaden van het ZIP-bestand, kunt u het `/var/contentsync` in de gegevensopslagruimte en het exportverzoek opnieuw verzenden.
