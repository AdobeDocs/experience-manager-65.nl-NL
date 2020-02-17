---
title: Emulators
seo-title: Emulators
description: Met AEM kunnen auteurs een pagina weergeven in een emulator die de omgeving simuleert waarin een eindgebruiker de pagina zal bekijken
seo-description: Met AEM kunnen auteurs een pagina weergeven in een emulator die de omgeving simuleert waarin een eindgebruiker de pagina zal bekijken
uuid: ee1496a5-be68-4318-b5ce-b11c41e4485c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: c51fca81-5dfc-4838-9672-acb6de62778b
legacypath: /content/docs/en/aem/6-0/develop/mobile/emulators
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Emulators{#emulators}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Met Adobe Experience Manager (AEM) kunnen auteurs een pagina weergeven in een emulator die de omgeving simuleert waarin een eindgebruiker de pagina zal bekijken, bijvoorbeeld op een mobiel apparaat of in een e-mailclient.

Het AEM-emulatorframework:

* Verstrekt inhoud creatie binnen een gesimuleerde Gebruikersinterface (UI), bijvoorbeeld een mobiel apparaat of een e-mailcliënt (die aan auteur nieuwsbrieven wordt gebruikt).
* Hiermee past u de pagina-inhoud aan op basis van de gesimuleerde interface.
* Hiermee kunt u aangepaste emulators maken.

>[!CAUTION]
>
>Deze functie wordt alleen ondersteund in de klassieke gebruikersinterface.

## Kenmerken van emulators {#emulators-characteristics}

Een emulator:

* Is gebaseerd op ExtJS.
* Werkt op de pagina DOM.
* De weergave ervan wordt geregeld via CSS.
* Biedt ondersteuning voor plug-ins (bijvoorbeeld de rotatieplug-in van het mobiele apparaat).
* Is alleen actief op auteur.
* De basiscomponent staat op `/libs/wcm/emulator/components/base`.

### Hoe de emulator de inhoud transformeert {#how-the-emulator-transforms-the-content}

De emulator werkt door de inhoud van de HTML-hoofdtekst om te zetten in emulator DIV&#39;s. De volgende HTML-code:

```xml
<body>
<div id="wrapper" class="page mobilecontentpage ">
    <div class="topnav mobiletopnav">
    ...
    </div>
    ...
</div>
</body>
```

wordt na het starten van de emulator omgezet in de volgende HTML-code:

```xml
<body>
 <div id="cq-emulator-toolbar">
 ...
 </div>
 <div id="cq-emulator-wrapper">
  <div id="cq-emulator-device">
   <div class=" android vertical" id="cq-emulator">
    ...
    <div class=" android vertical" id="cq-emulator-content">
     ...
     <div id="wrapper" class="page mobilecontentpage">
     ...
     </div>
     ...
    </div>
   </div>
  </div>
 </div>
 ...
</body>
```

Er zijn twee div-tags toegevoegd:

* de div met id `cq-emulator` die de emulator als geheel vasthoudt en

* het div met id die de viewport/screen/content area van het apparaat vertegenwoordigt waar de pagina-inhoud zich bevindt. `cq-emulator-content`

Nieuwe CSS-klassen worden ook toegewezen aan de nieuwe emulator-div: ze vertegenwoordigen de naam van de huidige emulator.

Plugins van een emulator kunnen de lijst met toegewezen CSS-klassen verder uitbreiden, zoals in het voorbeeld van de rotatie-insteekmodule, waarbij een klasse &quot;vertical&quot; of &quot;horizontal&quot; wordt ingevoegd, afhankelijk van de huidige rotatie van het apparaat.

Op deze manier kan de volledige weergave van de emulator worden bepaald door CSS-klassen te hebben die overeenkomen met de id&#39;s en CSS-klassen van de emulator div.

>[!NOTE]
>
>Het is raadzaam de inhoud van het lichaam in een enkel div-element te plaatsen in de HTML van het project, net als in het bovenstaande voorbeeld. Als de inhoud van het lichaam veelvoudige markeringen bevat, kunnen er onvoorspelbare resultaten zijn.

### Mobiele emulators {#mobile-emulators}

De bestaande mobiele emulators:

* Onder /libs/wcm/mobile/components/emulators.
* U kunt de JSON-server gebruiken op:

   http://localhost:4502/bin/wcm/mobile/emulators.json

Wanneer de paginacomponent op de mobiele paginacomponent ( `/libs/wcm/mobile/components/page`) steunt, wordt de emulatorfunctionaliteit automatisch geïntegreerd in de pagina door het volgende mechanisme:

* De component Mobile page `head.jsp` bevat de daaraan gekoppelde emulator in de apparaatgroep (alleen in de auteursmodus) en de rendering van CSS van de apparaatgroep via:

   `deviceGroup.drawHead(pageContext);`

* De methode `DeviceGroup.drawHead(pageContext)` omvat de init-component van de emulator, dat wil zeggen roept de component `init.html.jsp` van de emulator aan. Als de emulatorcomponent geen eigen component heeft `init.html.jsp` en afhankelijk is van de mobiele basisemulator ( `wcm/mobile/components/emulators/base)`wordt het initescript van de mobiele basisemulator aangeroepen ( `/libs/wcm/mobile/components/emulators/base/init.html.jsp`).

* Het initescript van de mobiele basismededinger bepaalt door Javascript:

   * De configuratie voor alle emulators die voor de pagina zijn gedefinieerd (emulatorConfigs)
   * De emulatormanager die de functionaliteit van de emulator op de pagina integreert via:

      `emulatorMgr.launch(config)`;

      De emulatormanager wordt gedefinieerd door:

      `/libs/wcm/emulator/widgets/source/EmulatorManager.js`

#### Aangepaste mobiele emulator maken {#creating-a-custom-mobile-emulator}

Een aangepaste mobiele emulator maken:

1. Maak hieronder `/apps/myapp/components/emulators` de component `myemulator` (knooppunttype): `cq:Component`).

1. De `sling:resourceSuperType` eigenschap instellen op `/libs/wcm/mobile/components/emulators/base`

1. Definieer een CSS-clientbibliotheek met een categorie `cq.wcm.mobile.emulator` voor de weergave van de emulator: name = `css`, node type = `cq:ClientLibrary`

   Als voorbeeld kunt u naar het knooppunt verwijzen `/libs/wcm/mobile/components/emulators/iPhone/css`

1. Definieer zo nodig een JS-clientbibliotheek, bijvoorbeeld om een specifieke insteekmodule te definiëren: name = js, knooptype = cq:ClientLibrary

   Als voorbeeld kunt u naar het knooppunt verwijzen `/libs/wcm/mobile/components/emulators/base/js`

1. Als de emulator specifieke functies ondersteunt die worden gedefinieerd door plug-ins (zoals aanraakschuiven), maakt u een configuratieknooppunt onder de emulator: name = `cq:emulatorConfig`, node type = `nt:unstructured` en voeg de eigenschap toe die de plug-in definieert:

   * Naam = `canRotate`, Type = `Boolean`, Waarde = `true`: om de rotatiefunctie op te nemen.

   * Naam = `touchScrolling`, Type = `Boolean`, Waarde = `true`: om de functionaliteit voor aanraakschuiven op te nemen.
   U kunt meer functies toevoegen door uw eigen plug-ins te definiëren.

