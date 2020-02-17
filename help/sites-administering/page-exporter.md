---
title: De pagina-exportfunctie
seo-title: De pagina-exportfunctie
description: Leer hoe u de AEM Page Exporter gebruikt.
seo-description: Leer hoe u de AEM Page Exporter gebruikt.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# De pagina-exportfunctie{#the-page-exporter}

Met AEM kunt u een pagina exporteren als een volledige webpagina met afbeeldingen, JS- en CSS-bestanden.

Wanneer het exporteren is geconfigureerd, vraagt u gewoon een pagina in uw browser aan door deze te vervangen door `html` `export.zip` in de URL en krijgt u een gecomprimeerde bestandsdownload met de gerenderde pagina in HTML-indeling en de bestanden waarnaar wordt verwezen. Alle paden op de pagina, bijvoorbeeld paden naar afbeeldingen, worden herschreven zodat ze verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.

## Een pagina exporteren {#exporting-a-page}

De volgende stappen beschrijven hoe te om een pagina uit te voeren, en veronderstellen dat een malplaatje van de de uitvoerconfiguratie voor uw plaats bestaat. Een configuratiesjabloon definieert de manier waarop een pagina wordt geëxporteerd en is specifiek voor uw site. Om een configuratiesjabloon te maken, raadpleegt u het [Creëren van een Configuratie van de Exporteur van de Pagina voor uw sectie van de Plaats](#creating-a-page-exporter-configuration-for-your-site) .

Een pagina exporteren:

1. Open de pagina in uw browser. Bijvoorbeeld:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Open het dialoogvenster Pagina-eigenschappen, selecteer het tabblad **Geavanceerd** en vouw de veldset **Exporteren** uit.

1. Klik op het vergrootpictogram en selecteer een configuratiesjabloon. Selecteer de **geometrixx** -sjabloon, aangezien dit de standaardsjabloon is voor de Geometrixx-site. Click **OK**.

1. Klik op **OK** om het dialoogvenster Pagina-eigenschappen te sluiten.
1. Vraag de pagina aan door deze te vervangen `html` door `export.zip` in de URL.

1. Download het `<page-name>.export.zip` bestand naar uw bestandssysteem.

1. Pak in uw bestandssysteem het bestand uit:

   * het pagina-html-bestand ( `<page-name>.html`) is hieronder beschikbaar `<unzip-dir>/<page-path>`
   * andere bronnen (.js-bestanden, .css-bestanden, afbeeldingen, ...) bevinden zich volgens de instellingen in de exportsjabloon. In dit voorbeeld zijn enkele bronnen hieronder `<unzip-dir>/etc`, enkele hieronder `<unzip-dir>/<page-path>`.

1. Open het pagina-HTML-bestand ( `<unzip-dir>/<page-path>.html`) in uw browser om de rendering te controleren.

## Een configuratie voor paginaexportters maken voor uw site {#creating-a-page-exporter-configuration-for-your-site}

De pagina-exportfunctie is gebaseerd op het Content Sync framework. De configuraties die beschikbaar zijn in het dialoogvenster Pagina-eigenschappen zijn configuratiesjablonen. Zij bepalen alle vereiste gebiedsdelen voor een pagina. Wanneer een paginauitvoer wordt teweeggebracht, wordt het configuratiesjabloon gebruikt en zowel de paginadad als de ontwerppad dynamisch toegepast op de configuratie. Het ZIP-bestand wordt vervolgens gemaakt met de standaardfunctionaliteit voor het synchroniseren van inhoud.

AEM sluit een aantal sjablonen in, waaronder:

* Een standaard om `/etc/contentsync/templates/default`. Deze sjabloon:

   * Is het fallback malplaatje wanneer geen configuratiemalplaatje in de bewaarplaats wordt gevonden.
   * Kan als basis voor een nieuw configuratiesjabloon dienen.

* Een die gewijd is aan de **Geometrixx** -site, op `/etc/contentsync/templates/geometrixx`. Deze sjabloon kan als voorbeeld worden gebruikt om een nieuwe sjabloon te maken.

Een configuratiesjabloon voor een pagina-exportfunctie maken:

1. In **CRXDE Lite**, creeer hieronder een knoop `/etc/contentsync/templates`:

   * Naam:bijv. `mysite`. De naam wordt weergegeven in het dialoogvenster Pagina-eigenschappen wanneer u de sjabloon voor het exporteren van pagina&#39;s kiest.
   * Type: `nt:unstructured`

1. Onder de malplaatjeknoop, hier geroepen `mysite`, creeer een knoopstructuur gebruikend de hieronder beschreven configuratieknopen.

### Configuratieknooppunten van pagina-exportfunctie {#page-exporter-configuration-nodes}

Het configuratiesjabloon bestaat uit een nodestructuur. Elk knooppunt heeft een `type` eigenschap die een specifieke handeling definieert in het aanmaakproces van het ZIP-bestand. Voor meer details over het typebezit, verwijs naar het Overzicht van configuratietypes in de het kaderpagina van de Synchronisatie van de Inhoud.

De volgende knopen kunnen worden gebruikt om een malplaatje van de de uitvoerconfiguratie te bouwen:

**paginaknooppunt** Het paginaknooppunt wordt gebruikt om de pagina-html naar het ZIP-bestand te kopiëren. Het heeft de volgende kenmerken:

* Is een verplicht knooppunt.
* Deze bevindt zich hieronder `/etc/contentsync/templates/<sitename>`.
* De naam is `page`.
* Het knooppunttype is `nt:unstructured`

Het `page` knooppunt heeft de volgende eigenschappen:

* Een `type` eigenschap ingesteld met de waarde `pages`.

* Het heeft geen `path` eigenschap omdat het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.

* De andere eigenschappen worden beschreven in het gedeelte Overzicht van configuratietypen van het Content Sync-framework.

**knooppunt** rewrite Het knooppunt rewrite definieert hoe de koppelingen in de geëxporteerde pagina worden herschreven. De herschreven koppelingen kunnen verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.

Raadpleeg de pagina Content Sync voor een volledige beschrijving van het `rewrite` knooppunt.

**ontwerpknooppunt** Het ontwerpknooppunt wordt gebruikt om het ontwerp te kopiëren dat voor de geëxporteerde pagina wordt gebruikt. Het heeft de volgende kenmerken:

* Is optioneel.
* Deze bevindt zich hieronder `/etc/contentsync/templates/<sitename>`.
* De naam is `design`.
* Het knooppunttype is `nt:unstructured`.

Het `design` knooppunt heeft de volgende eigenschappen:

* Een `type` eigenschap die op de waarde is ingesteld `copy`.

* Het heeft geen `path` eigenschap omdat het huidige paginapad dynamisch naar de configuratie wordt gekopieerd.

**algemeen knooppunt** Een algemeen knooppunt wordt gebruikt om bronnen zoals clientBPS .js- of CSS-bestanden naar het ZIP-bestand te kopiëren. Het heeft de volgende kenmerken:

* Is optioneel.
* Deze bevindt zich hieronder `/etc/contentsync/templates/<sitename>`.
* Heeft geen specifieke naam.
* Het knooppunttype is `nt:unstructured`.
* Bevat een `type` eigenschap en alle `type` verwante eigenschappen zoals gedefinieerd in de sectie Overzicht van configuratietypen van het Content Sync-framework.

Met het volgende configuratieknooppunt kopieert u bijvoorbeeld de bestanden geometrixx client.js naar het ZIP-bestand:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

De de configuratiesjabloon van de de paginauitvoer van **Geometrixx** toont u hoe een paginauitvoer kan worden gevormd. Als u de knooppuntstructuur van de sjabloon in uw browser wilt weergeven als een JPEG-indeling, vraagt u om de volgende URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Een aangepaste configuratie implementeren**

Aangezien u in de knoopstructuur kunt opgemerkt, heeft het malplaatje van de de paginatransformatie van **Geometrixx** een `logo` knoop met een `type` bezit dat aan `image`wordt geplaatst. Dit is een speciaal configuratietype dat is gemaakt om het afbeeldingslogo naar het ZIP-bestand te kopiëren. Om aan sommige specifieke vereisten te voldoen, kunt u een douanebezit moeten uitvoeren `type` : Raadpleeg hiervoor de sectie Een aangepaste update-handler implementeren in de pagina Content Sync.

## Een pagina programmatisch exporteren {#programmatically-exporting-a-page}

Als u een pagina programmatisch wilt exporteren, kunt u de [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI-service gebruiken. Met deze service kunt u:

* Exporteer een pagina en schrijf naar de HTTP-servletreactie.
* Exporteer een pagina en sla het ZIP-bestand op een specifieke locatie op.

De servlet die aan de `export` selecteur en de `zip` uitbreiding verbindend is gebruikt de dienst PageExporter.

## Problemen oplossen {#troubleshooting}

Als er een probleem optreedt met het downloaden van het ZIP-bestand, kunt u het `/var/contentsync` knooppunt in de opslagplaats verwijderen en de exportaanvraag opnieuw verzenden.

