---
title: De pagina-exportfunctie
description: Leer hoe u de AEM Page Exporter gebruikt.
translation-type: tm+mt
source-git-commit: 6aee1506b54a932bae8f2521fce4488de7d2a52a
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---


# De pagina-exportfunctie{#the-page-exporter}

AEM kunt u een pagina exporteren als een volledige webpagina met afbeeldingen, `.js`- en `.css`-bestanden.

Nadat de configuratie is geconfigureerd, vraagt u een pagina-export vanuit uw browser door `html` te vervangen door `export.zip` in de URL. Hiermee wordt een archiefbestand (zip) gegenereerd dat de weergegeven pagina in HTML-indeling bevat, samen met de elementen waarnaar wordt verwezen. Alle paden op de pagina (bijvoorbeeld paden naar afbeeldingen) worden herschreven zodat ze verwijzen naar de bestanden die in het archief zijn opgenomen of naar de bronnen op de server. Het archiefbestand (zip) kan vervolgens vanuit uw browser worden gedownload.

>[!NOTE]
>
>Afhankelijk van uw browser en de instellingen is de download:
>* een archiefbestand (`<page-name>.export.zip`)
>* een map (`<page-name>`); het archiefbestand is al uitgebreid


## Een pagina {#exporting-a-page} exporteren

In de volgende stappen wordt beschreven hoe u een pagina exporteert en wordt ervan uitgegaan dat er een exportsjabloon voor uw site bestaat. Een exportsjabloon definieert de manier waarop een pagina wordt geëxporteerd en is specifiek voor uw site. Om een uitvoermalplaatje tot stand te brengen verwijs naar [Creërend een Configuratie van de Exporter van de Pagina voor uw Plaats](#creating-a-page-exporter-configuration-for-your-site) sectie.

Een pagina exporteren:

1. Navigeer naar de vereiste pagina in de console **Sites**.

1. Selecteer de pagina en open vervolgens het dialoogvenster **Eigenschappen**.

1. Selecteer het tabblad **Geavanceerd**.

1. Vouw het veld **Exporteren** uit om een exportsjabloon te selecteren.
Selecteer de vereiste sjabloon voor uw site en bevestig vervolgens met **OK**.

1. Selecteer **Opslaan en sluiten** om het dialoogvenster Pagina-eigenschappen te sluiten.

1. Vraag de pagina voor export aan en vervang het achtervoegsel `html` door `export.zip` in de URL.

   Bijvoorbeeld:
   * localhost:4502/content/we-retail/language-masters/en.html

   Wordt benaderd via:
   * localhost:4502/content/we-retail/language-masters/en.export.zip


1. Download het archiefbestand naar uw bestandssysteem.

1. Pak het bestand desgewenst uit in uw bestandssysteem. Nadat de map is uitgevouwen, krijgt deze dezelfde naam als de geselecteerde pagina. Deze map bevat:

   * de submap `content`, die de basis is van een reeks submappen die het pad naar de pagina in de opslagplaats weerspiegelen

      * binnen deze structuur is er het HTML-bestand voor de geselecteerde pagina (`<page-name>.html`)
   * andere bronnen (`.js` bestanden, `.css` bestanden, afbeeldingen, enz.) worden geplaatst volgens de instellingen in de exportsjabloon


1. Open het pagina-HTML-bestand (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) in uw browser om de rendering te controleren.

## Een configuratie voor paginaexportters maken voor uw site {#creating-a-page-exporter-configuration-for-your-site}

De pagina-exportfunctie is gebaseerd op het [Content Sync framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html). De configuraties die beschikbaar zijn in het dialoogvenster **Pagina-eigenschappen** zijn exportsjablonen die de vereiste afhankelijkheden voor een pagina definiëren.

Wanneer een pagina-export wordt geactiveerd, wordt naar de exportsjabloon verwezen en worden zowel het paginapad als het ontwerppad dynamisch toegepast. Het ZIP-bestand wordt vervolgens gemaakt met de standaardfunctionaliteit voor het synchroniseren van inhoud.

Een uit-van-de-doos AEM installatie omvat een standaardmalplaatje onder `/etc/contentsync/templates/default`.

* Deze sjabloon is de fallback-sjabloon wanneer er geen exportsjabloon wordt gevonden in de repository.

* Het `default` malplaatje toont u hoe een paginauitvoer kan worden gevormd, zodat kan als basis voor een nieuw de uitvoermalplaatje dienen.

* Als u de knooppuntstructuur van de sjabloon in uw browser wilt weergeven als JSON-indeling, vraagt u de volgende URL op:
   `http://localhost:4502/etc/contentsync/templates/default.json`

De eenvoudigste methode om een nieuwe sjabloon voor het exporteren van pagina&#39;s te maken is:

* de `default`-sjabloon kopiëren,

* een nieuwe naam toewijzen die geschikt is voor uw site;

* Voer vervolgens de vereiste updates uit.

Een volledig nieuwe sjabloon maken:

1. Maak in **CRXDE Lite** een knooppunt onder `/etc/contentsync/templates`:

   * `Name`: een naam die geschikt is voor uw site; bijvoorbeeld  `<mysite>`. De naam wordt weergegeven in het dialoogvenster Pagina-eigenschappen wanneer u de sjabloon voor het exporteren van pagina&#39;s kiest.

   * `Type`: `nt:unstructured`

2. Onder de malplaatjeknoop, genoemd hier `mysite`, creeer een knoopstructuur gebruikend de hieronder beschreven configuratieknopen.

## Een sjabloon voor pagina-exportters activeren voor uw pagina&#39;s {#activating-a-page-exporter-configuration-for-your-pages}

Zodra uw malplaatje is gevormd moet u het ter beschikking stellen:

1. Navigeer in CRXDE naar de vereiste pagina in de `/content` vertakking. Dit kan een afzonderlijke pagina zijn, of de hoofdpagina van een substructuur.

1. Maak de eigenschap op het knooppunt `jcr:content` van de pagina:
   * `Name`:  `cq:exportTemplate`
   * `Type`:  `String`
   * `Value`: pad naar de sjabloon; bijvoorbeeld:  `/etc/contentsync/templates/mysite`

### Configuratieknooppunten van pagina-exportter {#page-exporter-configuration-nodes}

De sjabloon bestaat uit een knooppuntstructuur, aangezien deze het [Content Sync framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html) gebruikt.  Elk knooppunt heeft een eigenschap `type` die een specifieke handeling definieert in het aanmaakproces van het ZIP-bestand.

<!-- For more details about the type property, refer to the Overview of configuration types section in the Content Sync framework page.
-->

De volgende knooppunten kunnen worden gebruikt om een exportsjabloon te maken:

* `page`
Het paginaknooppunt wordt gebruikt om de pagina-html naar het ZIP-bestand te kopiëren. Het heeft de volgende kenmerken:

   * Is een verplicht knooppunt.
   * Wordt onder `/etc/contentsync/templates/<mysite>` geplaatst.
   * Wordt gedefinieerd met de eigenschap `Name`ingesteld op `page`.
   * Het knooppunttype is `nt:unstructured`

   Het knooppunt `page` heeft de volgende eigenschappen:

   * Een eigenschap `type` ingesteld met de waarde `pages`.

   * Het heeft geen `path` bezit aangezien het huidige paginapad dynamisch aan de configuratie wordt gekopieerd.

   <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
Het knooppunt rewrite definieert hoe de koppelingen in de geëxporteerde pagina worden herschreven. De herschreven koppelingen kunnen verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.
   <!-- Please refer to the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
Het ontwerpknooppunt wordt gebruikt om het ontwerp te kopiëren dat voor de geëxporteerde pagina wordt gebruikt. Het heeft de volgende kenmerken:

   * Is optioneel.
   * Wordt onder `/etc/contentsync/templates/<mysite>` geplaatst.
   * Wordt gedefinieerd met de eigenschap `Name` ingesteld op `design`.
   * Het knooppunttype is `nt:unstructured`.

   Het knooppunt `design` heeft de volgende eigenschappen:

   * Een eigenschap `type` ingesteld op de waarde `copy`.

   * Het heeft geen `path` bezit, aangezien het huidige paginadad dynamisch aan de configuratie wordt gekopieerd.


* `generic`
Een generisch knooppunt wordt gebruikt om bronnen als clientlibs te kopiëren 
`.js` of  `.css` bestanden naar het ZIP-bestand. Het heeft de volgende kenmerken:

   * Is optioneel.
   * Wordt onder `/etc/contentsync/templates/<mysite>` geplaatst.
   * Heeft geen specifieke naam.
   * Het knooppunttype is `nt:unstructured`.
   * Heeft een `type` eigenschap en `type` gerelateerde eigenschappen. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

   Met het volgende configuratieknooppunt worden bijvoorbeeld de `mysite.clientlibs.js`-bestanden naar het ZIP-bestand gekopieerd:

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

Om aan sommige specifieke vereisten te voldoen, kunt u [douane updatemanager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/handler/package-summary.html) moeten uitvoeren.

<!-- To meet some specific requirements, you may need to implement a custom `type` property: to do so, refer to the Implementing a custom update handler section in the Content Sync page.
-->

## Een pagina {#programmatically-exporting-a-page} programmatisch exporteren

Als u een pagina programmatisch wilt exporteren, kunt u de service [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI gebruiken. Met deze service kunt u:

* Exporteer een pagina en schrijf naar de HTTP-servletreactie.
* Exporteer een pagina en sla het ZIP-bestand op een specifieke locatie op.

De servlet die aan `export` selecteur en `zip` uitbreiding verbindt gebruikt de dienst PageExporter.

## Problemen oplossen {#troubleshooting}

Als er een probleem optreedt met het downloaden van het ZIP-bestand, kunt u het `/var/contentsync`-knooppunt in de gegevensopslagruimte verwijderen en het exportverzoek opnieuw verzenden.
