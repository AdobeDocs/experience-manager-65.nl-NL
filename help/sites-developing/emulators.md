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
feature: Developing
role: Developer
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 0%

---

# Emulators{#emulators}

{{ue-over-mobile}}

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
* De basiscomponent ervan bevindt zich op `/libs/wcm/emulator/components/base` .

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

* de div met id `cq-emulator` die de emulator als geheel vasthoudt en

* het div met id `cq-emulator-content` dat de viewport/screen/content area van het apparaat vertegenwoordigt waar de pagina-inhoud zich bevindt.

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

Wanneer de paginacomponent op de mobiele paginacomponent ( `/libs/wcm/mobile/components/page`) steunt, wordt de emulatorfunctionaliteit automatisch geïntegreerd in de pagina door het volgende mechanisme:

* De component voor mobiele pagina `head.jsp` bevat de daaraan gekoppelde emulator in de apparaatgroep (alleen in de auteursmodus) en de CSS-weergave van de apparaatgroep via:

  `deviceGroup.drawHead(pageContext);`

* De methode `DeviceGroup.drawHead(pageContext)` bevat de init-component van de emulator, dat wil zeggen roept de `init.html.jsp` van de emulatorcomponent aan. Als de emulatorcomponent geen eigen `init.html.jsp` heeft en afhankelijk is van de mobiele basemulator ( `wcm/mobile/components/emulators/base)` ), wordt het initescript van de mobiele basemulator aangeroepen ( `/libs/wcm/mobile/components/emulators/base/init.html.jsp` ).

* Het init-script van de Mobile base emulator definieert via JavaScript:

   * De configuratie voor alle emulators die voor de pagina zijn gedefinieerd (emulatorConfigs)
   * De emulatormanager die de functionaliteit van de emulator op de pagina integreert via:

     `emulatorMgr.launch(config)`;

     De emulatormanager wordt gedefinieerd door:

     `/libs/wcm/emulator/widgets/source/EmulatorManager.js`

#### Aangepaste mobiele emulator maken {#creating-a-custom-mobile-emulator}

Een aangepaste mobiele emulator maken:

1. Onder `/apps/myapp/components/emulators` maakt u de component `myemulator` (knooppunttype: `cq:Component` ).

1. Stel de eigenschap `sling:resourceSuperType` in op `/libs/wcm/mobile/components/emulators/base`

1. Definieer een CSS-clientbibliotheek met categorie `cq.wcm.mobile.emulator` voor de weergave van de emulator: naam = `css`, knooppunttype = `cq:ClientLibrary`

   U kunt bijvoorbeeld naar het knooppunt verwijzen `/libs/wcm/mobile/components/emulators/iPhone/css`

1. Definieer zo nodig een JS-clientbibliotheek, bijvoorbeeld om een specifieke insteekmodule te definiëren: name = js, knooppunttype = cq:ClientLibrary

   U kunt bijvoorbeeld naar het knooppunt verwijzen `/libs/wcm/mobile/components/emulators/base/js`

1. Als de emulator specifieke functies ondersteunt die worden gedefinieerd door plug-ins (zoals schuiven door aanrakingen), maakt u een configuratieknooppunt onder de emulator: name = `cq:emulatorConfig` , knooptype = `nt:unstructured` en voegt u de eigenschap toe die de plug-in definieert:

   * Naam = `canRotate`, Type = `Boolean`, Waarde = `true` : om de rotatiefunctionaliteit op te nemen.

   * Naam = `touchScrolling`, Type = `Boolean`, Waarde = `true` : om de functionaliteit voor schuiven met aanraakbediening op te nemen.

   U kunt meer functies toevoegen door uw eigen plug-ins te definiëren.
