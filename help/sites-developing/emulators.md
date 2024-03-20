---
title: Emulators
description: AEM stelt auteurs in staat een pagina te bekijken in een emulator die de omgeving simuleert waarin een eindgebruiker de pagina zal bekijken
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
legacypath: /content/docs/en/aem/6-0/develop/mobile/emulators
exl-id: 009b7e2c-ac37-4acc-a656-0a34d3853dfd
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Emulators{#emulators}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Met Adobe Experience Manager (AEM) kunnen auteurs een pagina weergeven in een emulator die de omgeving simuleert waarin een eindgebruiker de pagina weergeeft, bijvoorbeeld op een mobiel apparaat of in een e-mailclient.

Het AEM emulatorframework:

* Verstrekt inhoud creatie binnen een gesimuleerde Gebruikersinterface (UI), bijvoorbeeld, een mobiel apparaat of een e-mailcliënt (die aan auteur nieuwsbrieven wordt gebruikt).
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
* Ondersteuning voor plug-ins (bijvoorbeeld de rotatie-insteekmodule voor mobiele apparaten).
* Is alleen actief op auteur.
* De basiscomponent bevindt zich op `/libs/wcm/emulator/components/base`.

### Hoe de emulator de inhoud transformeert {#how-the-emulator-transforms-the-content}

De emulator werkt door de inhoud van het lichaam van de HTML in emulator DIVs te verpakken. De volgende HTML-code:

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

* div met id `cq-emulator` de emulator als geheel vasthouden en

* div met id `cq-emulator-content` die de viewport/het scherm/het inhoudsgebied van het apparaat vertegenwoordigt waar de pagina-inhoud zich bevindt.

Nieuwe CSS-klassen worden ook toegewezen aan de nieuwe emulator-div: deze vertegenwoordigen de naam van de huidige emulator.

Plugins van een emulator kunnen de lijst met toegewezen CSS-klassen verder uitbreiden, zoals in het voorbeeld van de rotatie-insteekmodule, waarbij een klasse &quot;vertical&quot; of &quot;horizontal&quot; wordt ingevoegd, afhankelijk van de huidige rotatie van het apparaat.

Op deze manier kan de volledige weergave van de emulator worden bepaald door CSS-klassen te hebben die overeenkomen met de id&#39;s en CSS-klassen van de emulator div.

>[!NOTE]
>
>Aanbevolen wordt om de inhoud van het lichaam door de HTML van het project in één enkele div te verpakken, enkel zoals in het bovenstaande voorbeeld. Als de inhoud van het lichaam veelvoudige markeringen bevat, kunnen er onvoorspelbare resultaten zijn.

### Mobiele emulators {#mobile-emulators}

De bestaande mobiele emulators:

* Onder /libs/wcm/mobile/components/emulators.
* U kunt de JSON-server gebruiken op:

  http://localhost:4502/bin/wcm/mobile/emulators.json

Wanneer de paginacomponent op de mobiele paginacomponent ( `/libs/wcm/mobile/components/page`), wordt de emulatorfunctionaliteit automatisch in de pagina geïntegreerd via het volgende mechanisme:

* De component voor mobiele pagina `head.jsp` bevat de daaraan gekoppelde emulator van de apparaatgroep in de it-component (alleen in de auteursmodus) en de CSS-weergave van de apparaatgroep via:

  `deviceGroup.drawHead(pageContext);`

* De methode `DeviceGroup.drawHead(pageContext)` bevat de init-component van de emulator, dat wil zeggen roept de component `init.html.jsp` van de emulatorcomponent. Als de emulatorcomponent geen eigen component heeft `init.html.jsp` en baseert zich op de mobiele basis emulator ( `wcm/mobile/components/emulators/base)`, wordt het initescript van de mobiele basisemulator aangeroepen ( `/libs/wcm/mobile/components/emulators/base/init.html.jsp`).

* Het init-script van de Mobile Base-emulator definieert via JavaScript:

   * De configuratie voor alle emulators die voor de pagina zijn gedefinieerd (emulatorConfigs)
   * De emulatormanager die de functionaliteit van de emulator op de pagina integreert via:

     `emulatorMgr.launch(config)`;

     De emulatormanager wordt gedefinieerd door:

     `/libs/wcm/emulator/widgets/source/EmulatorManager.js`

#### Aangepaste mobiele emulator maken {#creating-a-custom-mobile-emulator}

Een aangepaste mobiele emulator maken:

1. Onder `/apps/myapp/components/emulators` de component maken `myemulator` (knooppunttype: `cq:Component`).

1. Stel de `sling:resourceSuperType` eigenschap aan `/libs/wcm/mobile/components/emulators/base`

1. Een CSS-clientbibliotheek met een categorie definiëren `cq.wcm.mobile.emulator` voor de vormgeving van de emulator: naam = `css`, knooppunttype = `cq:ClientLibrary`

   Als voorbeeld kunt u naar het knooppunt verwijzen `/libs/wcm/mobile/components/emulators/iPhone/css`

1. Definieer zo nodig een JS-clientbibliotheek, bijvoorbeeld om een specifieke insteekmodule te definiëren: name = js, knooppunttype = cq:ClientLibrary

   Als voorbeeld kunt u naar het knooppunt verwijzen `/libs/wcm/mobile/components/emulators/base/js`

1. Als de emulator specifieke functies ondersteunt die worden gedefinieerd door plug-ins (zoals schuiven door aanrakingen), maakt u een configuratieknooppunt onder de emulator: name = `cq:emulatorConfig`, knooppunttype = `nt:unstructured` en voeg de eigenschap toe die de insteekmodule definieert:

   * Naam = `canRotate`, Type = `Boolean`, Waarde = `true`: om de rotatiefunctie op te nemen.

   * Naam = `touchScrolling`, Type = `Boolean`, Waarde = `true`: om de functionaliteit voor aanraakschuiven op te nemen.

   U kunt meer functies toevoegen door uw eigen plug-ins te definiëren.
