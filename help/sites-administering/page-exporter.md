---
title: De pagina-exportfunctie
description: Leer hoe u de AEM Page Exporter gebruikt.
translation-type: tm+mt
source-git-commit: c152cf4bf8cf19e0fa7b328241ced753fa42f7a4
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---


# De pagina-exportfunctie{#the-page-exporter}

Met AEM kunt u een pagina exporteren als een volledige webpagina met afbeeldingen `.js` en `.css` bestanden.

Nadat de configuratie is geconfigureerd, vraagt u een pagina-export van uw browser door deze te vervangen `html` door `export.zip` in de URL. Hiermee wordt een archiefbestand (zip) gegenereerd dat de weergegeven pagina in HTML-indeling bevat, samen met de elementen waarnaar wordt verwezen. Alle paden op de pagina (bijvoorbeeld paden naar afbeeldingen) worden herschreven zodat ze verwijzen naar de bestanden die in het archief zijn opgenomen of naar de bronnen op de server. Het archiefbestand (zip) kan vervolgens vanuit uw browser worden gedownload.

>[!NOTE]
>
>Afhankelijk van uw browser en de instellingen is de download:
>* een archiefbestand (`<page-name>.export.zip`)
>* een map (`<page-name>`); het archiefbestand is al uitgebreid


## Een pagina exporteren {#exporting-a-page}

In de volgende stappen wordt beschreven hoe u een pagina exporteert en wordt ervan uitgegaan dat er een exportsjabloon voor uw site bestaat. Een exportsjabloon definieert de manier waarop een pagina wordt geëxporteerd en is specifiek voor uw site. Als u een exportsjabloon wilt maken, raadpleegt u de sectie [Een configuratie van een paginaexporteur maken voor uw site](#creating-a-page-exporter-configuration-for-your-site) .

Een pagina exporteren:

1. Navigeer naar de vereiste pagina in de **Sites** -console.

1. Selecteer de pagina en open het dialoogvenster **Eigenschappen** .

1. Selecteer het tabblad **Geavanceerd** .

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

   * de submap `content`, de hoofdmap van een reeks submappen die het pad naar de pagina in de opslagplaats weerspiegelen

      * binnen deze structuur is er het HTML-bestand voor de geselecteerde pagina (`<page-name>.html`)
   * andere bronnen (`.js` bestanden, `.css` bestanden, afbeeldingen, enz.) worden geplaatst volgens de instellingen in de exportsjabloon


1. Open het pagina-HTML-bestand (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) in uw browser om de rendering te controleren.

## Een configuratie voor paginaexportters maken voor uw site {#creating-a-page-exporter-configuration-for-your-site}

De pagina-exportfunctie is gebaseerd op het [Content Sync framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html). De configuraties die beschikbaar zijn in het dialoogvenster **Pagina-eigenschappen** zijn exportsjablonen die de vereiste afhankelijkheden voor een pagina definiëren.

Wanneer een pagina-export wordt geactiveerd, wordt naar de exportsjabloon verwezen en worden zowel het paginapad als het ontwerppad dynamisch toegepast. Het ZIP-bestand wordt vervolgens gemaakt met de standaardfunctionaliteit voor het synchroniseren van inhoud.

Een uit-van-de-doos installatie AEM omvat een standaardmalplaatje onder `/etc/contentsync/templates/default`.

* Deze sjabloon is de fallback-sjabloon wanneer er geen exportsjabloon wordt gevonden in de repository.

* Het `default` malplaatje toont u hoe een paginauitvoer kan worden gevormd, zodat kan als basis voor een nieuw de uitvoermalplaatje dienen.

* Als u de knooppuntstructuur van de sjabloon in uw browser wilt weergeven als JSON-indeling, vraagt u de volgende URL op:
   `http://localhost:4502/etc/contentsync/templates/default.json`

De eenvoudigste methode om een nieuwe sjabloon voor het exporteren van pagina&#39;s te maken is:

* de `default` sjabloon kopiëren;

* een nieuwe naam toewijzen die geschikt is voor uw site;

* Voer vervolgens de vereiste updates uit.

Een volledig nieuwe sjabloon maken:

1. In **CRXDE Lite**, creeer hieronder een knoop `/etc/contentsync/templates`:

   * `Name`: een naam die geschikt is voor uw site; bijvoorbeeld `<mysite>`. De naam wordt weergegeven in het dialoogvenster Pagina-eigenschappen wanneer u de sjabloon voor het exporteren van pagina&#39;s kiest.

   * `Type`: `nt:unstructured`

2. Onder de malplaatjeknoop, hier geroepen `mysite`, creeer een knoopstructuur gebruikend de hieronder beschreven configuratieknopen.

## Een paginamarittersjabloon activeren voor uw pagina&#39;s {#activating-a-page-exporter-configuration-for-your-pages}

Zodra uw malplaatje is gevormd moet u het ter beschikking stellen:

1. Navigeer in CRXDE naar de vereiste pagina in de `/content` vertakking.

1. Maak de eigenschap op het `jcr:content` knooppunt van de pagina:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: pad naar de sjabloon; bijvoorbeeld: `/etc/contentsync/templates/mysite`

### Configuratieknooppunten van pagina-exportfunctie {#page-exporter-configuration-nodes}

De sjabloon bestaat uit een knooppuntstructuur, aangezien deze het [Content Sync framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html)gebruikt.  Elk knooppunt heeft een `type` eigenschap die een specifieke handeling definieert in het aanmaakproces van het ZIP-bestand.

<!-- For more details about the type property, refer to the Overview of configuration types section in the Content Sync framework page.
-->

De volgende knooppunten kunnen worden gebruikt om een exportsjabloon te maken:

* `page`
Het paginaknooppunt wordt gebruikt om de pagina-html naar het ZIP-bestand te kopiëren. Het heeft de volgende kenmerken:

   * Is een verplicht knooppunt.
   * Deze bevindt zich hieronder `/etc/contentsync/templates/<mysite>`.
   * Wordt gedefinieerd met de eigenschap `Name`ingesteld op `page`.
   * Het knooppunttype is `nt:unstructured`

   Het `page` knooppunt heeft de volgende eigenschappen:

   * Een `type` eigenschap ingesteld met de waarde `pages`.

   * Het heeft geen `path` eigenschap omdat het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.

   <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
Het knooppunt rewrite definieert hoe de koppelingen in de geëxporteerde pagina worden herschreven. De herschreven koppelingen kunnen verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.
   <!-- Please refer to the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
Het ontwerpknooppunt wordt gebruikt om het ontwerp te kopiëren dat voor de geëxporteerde pagina wordt gebruikt. Het heeft de volgende kenmerken:

   * Is optioneel.
   * Deze bevindt zich hieronder `/etc/contentsync/templates/<mysite>`.
   * Wordt gedefinieerd met de eigenschap `Name` ingesteld op `design`.
   * Het knooppunttype is `nt:unstructured`.

   Het `design` knooppunt heeft de volgende eigenschappen:

   * Een `type` eigenschap die op de waarde is ingesteld `copy`.

   * Deze eigenschap heeft geen `path` eigenschap, omdat het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.


* `generic`
Een generisch knooppunt wordt gebruikt om bronnen als clientlibs te kopiëren 
`.js` of `.css` bestanden naar het ZIP-bestand. Het heeft de volgende kenmerken:

   * Is optioneel.
   * Deze bevindt zich hieronder `/etc/contentsync/templates/<mysite>`.
   * Heeft geen specifieke naam.
   * Het knooppunttype is `nt:unstructured`.
   * Bevat een `type` eigenschap en `type` verwante eigenschappen. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

   Met het volgende configuratieknooppunt kopieert u bijvoorbeeld de `mysite.clientlibs.js` bestanden naar het ZIP-bestand:

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

Om aan sommige specifieke vereisten te voldoen, kunt u een manager [van de](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/handler/package-summary.html)douaneverupdate moeten uitvoeren.

<!-- To meet some specific requirements, you may need to implement a custom `type` property: to do so, refer to the Implementing a custom update handler section in the Content Sync page.
-->

## Een pagina programmatisch exporteren {#programmatically-exporting-a-page}

Als u een pagina programmatisch wilt exporteren, kunt u de [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI-service gebruiken. Met deze service kunt u:

* Exporteer een pagina en schrijf naar de HTTP-servletreactie.
* Exporteer een pagina en sla het ZIP-bestand op een specifieke locatie op.

De servlet die aan de `export` selecteur en de `zip` uitbreiding verbindend is gebruikt de dienst PageExporter.

## Problemen oplossen {#troubleshooting}

Als er een probleem optreedt met het downloaden van het ZIP-bestand, kunt u het `/var/contentsync` knooppunt in de opslagplaats verwijderen en de exportaanvraag opnieuw verzenden.
