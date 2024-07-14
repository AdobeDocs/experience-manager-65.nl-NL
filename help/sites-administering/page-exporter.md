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

Met Adobe Experience Manager (AEM) kunt u een pagina exporteren als een volledige webpagina, inclusief afbeeldingen, `.js` - en `.css` -bestanden.

Wanneer dit is geconfigureerd, vraagt u een pagina-export vanuit uw browser door `html` te vervangen door `export.zip` in de URL. Hiermee wordt een archiefbestand (zip) gegenereerd dat de weergegeven pagina in HTML-indeling bevat, samen met de elementen waarnaar wordt verwezen. Alle paden op de pagina (bijvoorbeeld paden naar afbeeldingen) worden herschreven zodat ze verwijzen naar de bestanden die in het archief zijn opgenomen of naar de bronnen op de server. Het archiefbestand (zip) kan vervolgens vanuit uw browser worden gedownload.

>[!NOTE]
>
>Afhankelijk van uw browser en de instellingen is de download:
>
>* een archiefbestand (`<page-name>.export.zip`)
>* een map (`<page-name>`); het archiefbestand is al uitgevouwen

## Pagina&#39;s exporteren {#exporting-a-page}

In de volgende stappen wordt beschreven hoe u een pagina exporteert en wordt ervan uitgegaan dat er een exportsjabloon voor uw site bestaat. Een exportsjabloon definieert de manier waarop een pagina wordt geëxporteerd en is specifiek voor uw site. Om een uitvoermalplaatje tot stand te brengen, zie [ Creërend een Configuratie van de Exporteur van de Pagina voor uw Plaats ](#creating-a-page-exporter-configuration-for-your-site).

Een pagina exporteren:

1. Navigeer aan de vereiste pagina in de **console van Plaatsen**.

1. Selecteer de pagina, dan open de **dialoog van Eigenschappen**.

1. Selecteer het **Geavanceerde** lusje.

1. Vouw het **gebied van de Uitvoer** uit om een uitvoermalplaatje te selecteren.
Selecteer het vereiste malplaatje voor uw plaats, dan bevestig met **O.K.**.

1. Selecteer **sparen &amp; dicht** om de dialoog van de pagina eigenschappen te sluiten.

1. Vraag de pagina voor export aan en vervang het achtervoegsel `html` door `export.zip` in de URL.

   Bijvoorbeeld:
   * localhost:4502/content/we-retail/language-masters/en.html

   Wordt benaderd door:
   * localhost:4502/content/we-retail/language-masters/en.export.zip

1. Download het archiefbestand naar uw bestandssysteem.

1. Pak het bestand desgewenst uit in uw bestandssysteem. Als deze is uitgevouwen, ziet u een map met dezelfde naam als de geselecteerde pagina. Deze map bevat:

   * de submap `content` , de hoofdmap van een reeks submappen die het pad naar de pagina in de opslagplaats weerspiegelen

      * binnen deze structuur is er het HTML-bestand voor de geselecteerde pagina (`<page-name>.html`)

   * andere bronnen (`.js` bestanden, `.css` bestanden, afbeeldingen, enzovoort) bevinden zich volgens de instellingen in de exportsjabloon

1. Open het pagina-HTML-bestand (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) in uw browser zodat u de rendering kunt controleren.

## Een configuratie voor paginaexportters maken voor uw site {#creating-a-page-exporter-configuration-for-your-site}

De paginaexporteur is gebaseerd op het [ kader van de Synchronisatie van de Inhoud ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/contentsync/package-summary.html). De configuraties die in de **dialoog van de Eigenschappen van de Pagina** beschikbaar zijn zijn de uitvoermalplaatjes die de vereiste gebiedsdelen voor een pagina bepalen.

Wanneer het exporteren van een pagina wordt geactiveerd, wordt naar de exportsjabloon verwezen. Zowel het paginapad als het ontwerppad worden dynamisch toegepast. Het ZIP-bestand wordt vervolgens gemaakt met de standaardfunctionaliteit voor het synchroniseren van inhoud.

Een installatie buiten de AEM bevat een standaardsjabloon onder `/etc/contentsync/templates/default` .

* Deze sjabloon is de fallback-sjabloon wanneer er geen exportsjabloon wordt gevonden in de repository.

* De sjabloon `default` laat zien hoe een pagina-export kan worden geconfigureerd, zodat deze als basis kan dienen voor een nieuwe exportsjabloon.

* Als u de knooppuntstructuur van de sjabloon in uw browser wilt weergeven als JSON-indeling, vraagt u de volgende URL op:
  `http://localhost:4502/etc/contentsync/templates/default.json`

De eenvoudigste methode om een sjabloon voor het exporteren van pagina&#39;s te maken is:

* de `default` -sjabloon kopiëren,

* een nieuwe naam toewijzen die geschikt is voor uw site;

* Voer vervolgens de vereiste updates uit.

Een volledig nieuwe sjabloon maken:

1. In **CRXDE Lite**, creeer een knoop onder `/etc/contentsync/templates`:

   * `Name`: een naam die geschikt is voor uw site, bijvoorbeeld `<mysite>` . De naam wordt weergegeven in het dialoogvenster Pagina-eigenschappen wanneer u de sjabloon voor het exporteren van pagina&#39;s kiest.

   * `Type`: `nt:unstructured`

2. Onder het sjabloonknooppunt, dat hier `mysite` wordt genoemd, maakt u een knooppuntstructuur met behulp van de hieronder beschreven configuratieknooppunten.

## Een paginamarittersjabloon activeren voor uw pagina&#39;s {#activating-a-page-exporter-configuration-for-your-pages}

Wanneer uw malplaatje wordt gevormd, maak het beschikbaar:

1. Navigeer in CRXDE naar de vereiste pagina in de `/content` vertakking. Dit kan een afzonderlijke pagina zijn, of de basispagina van een substructuur.

1. Maak de eigenschap op het knooppunt `jcr:content` van de pagina:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: pad naar de sjabloon, bijvoorbeeld: `/etc/contentsync/templates/mysite`

### Configuratieknooppunten van pagina-exporteur {#page-exporter-configuration-nodes}

Het malplaatje bestaat uit een knoopstructuur, aangezien het het [ kader van de Synchronisatie van de Inhoud ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/contentsync/package-summary.html) gebruikt. Elk knooppunt heeft een eigenschap `type` die een specifieke handeling definieert in het aanmaakproces van het ZIP-bestand.

<!-- For more details about the type property, see the Overview of configuration types section in the Content Sync framework page.
-->

De volgende knooppunten kunnen worden gebruikt om een exportsjabloon te maken:

* `page`
Het paginaknooppunt wordt gebruikt om pagina html aan het ZIP dossier te kopiëren. Het heeft de volgende kenmerken:

   * Een verplicht knooppunt.
   * Onder `/etc/contentsync/templates/<mysite>` weergegeven.
   * Gedefinieerd met de eigenschap `Name` ingesteld op `page` .
   * Het knooppunttype is `nt:unstructured`

  Het knooppunt `page` heeft de volgende eigenschappen:

   * Een eigenschap `type` ingesteld met de waarde `pages` .

   * De eigenschap heeft geen eigenschap `path` omdat het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.
  <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
Het knooppunt rewrite definieert hoe de koppelingen in de geëxporteerde pagina worden herschreven. De herschreven koppelingen kunnen verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.
  <!-- See the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
Het ontwerpknooppunt wordt gebruikt om het ontwerp te kopiëren dat voor de geëxporteerde pagina wordt gebruikt. Het heeft de volgende kenmerken:

   * Optioneel.
   * Onder `/etc/contentsync/templates/<mysite>` weergegeven.
   * Gedefinieerd met de eigenschap `Name` ingesteld op `design` .
   * Het knooppunttype is `nt:unstructured` .

  Het knooppunt `design` heeft de volgende eigenschappen:

   * Een eigenschap `type` ingesteld op de waarde `copy` .

   * De eigenschap heeft geen eigenschap `path` omdat het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.

* `generic`
Een algemeen knooppunt wordt gebruikt om bronnen zoals clientlibs `.js` - of `.css` -bestanden naar het ZIP-bestand te kopiëren. Het heeft de volgende kenmerken:

   * Optioneel.
   * Onder `/etc/contentsync/templates/<mysite>` weergegeven.
   * Geen specifieke naam.
   * Het knooppunttype is `nt:unstructured` .
   * Heeft een eigenschap `type` en `type` verwante eigenschappen. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

  Het volgende configuratieknooppunt kopieert bijvoorbeeld de `mysite.clientlibs.js` -bestanden naar het ZIP-bestand:

  ```xml
  "mysite.clientlibs.js": {
      "extension": "js",
      "type": "clientlib",
      "path": "/etc/designs/mysite/clientlibs",
      "jcr:primaryType": "nt:unstructured"
  }
  ```

**Uitvoerend een Configuratie van de Douane**

Aangepaste configuraties zijn ook mogelijk.

<!--
As you may have noticed in the node structure, the **Geometrixx** page export template has a `logo` node with a `type` property set to `image`. This is a special configuration type that has been created to copy the image logo to the zip file. 
-->

Om aan sommige specifieke vereisten te voldoen, voer de manager van de a [ douaneverupdate ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/contentsync/handler/package-summary.html) uit.

<!-- To meet some specific requirements, you may need to implement a custom `type` property. To do so, see the Implementing a custom update handler section in the Content Sync page.
-->

## Pagina&#39;s programmatisch exporteren {#programmatically-exporting-a-page}

Om een pagina programmatically uit te voeren, kunt u de [ PageExporter ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) dienst gebruiken OSGI. Met deze service kunt u:

* Exporteer een pagina en schrijf naar de HTTP-servletreactie.
* Exporteer een pagina en sla het ZIP-bestand op een specifieke locatie op.

De servlet die aan de `export` selecteur en de `zip` uitbreiding is gebonden gebruikt de dienst PageExporter.

## Problemen oplossen {#troubleshooting}

Als er een probleem optreedt met het downloaden van het ZIP-bestand, kunt u het knooppunt `/var/contentsync` in de gegevensopslagruimte verwijderen en de exportaanvraag opnieuw verzenden.
