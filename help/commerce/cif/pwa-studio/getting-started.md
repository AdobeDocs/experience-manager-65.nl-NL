---
title: Aan de slag met AEM extensie voor PWA Studio
description: Leer hoe u een AEM headless Content- en Commerce-project met PWA Studio kunt implementeren.
topics: Commerce
feature: Commerce Integration Framework
exl-id: de7b8f05-b6b7-4105-84a5-940c16ebf2b4
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Aan de slag met AEM extensie voor PWA Studio {#getting-started-pwa}

PWA Studio kan naadloos worden geïntegreerd met Adobe Commerce via GraphQL en biedt onbeperkte mogelijkheden voor het maken van innovatieve en boeiende winkels en andere digitale ervaringen.

Inhoudsfragmenten zijn stukken inhoud met een vooraf gedefinieerde structuur waarmee ze zonder kop kunnen worden gebruikt als API in verschillende indelingen (bijvoorbeeld JSON, Markdown) en onafhankelijk kunnen worden weergegeven. Inhoudsfragmenten omvatten alle gegevenstypen en velden die voor GraphQL zijn vereist. Uw toepassing vraagt dan alleen wat er beschikbaar is en ontvangt wat er wordt verwacht. De flexibiliteit die ze bieden in termen van de structuur ervan maakt ze perfect voor gebruik op meerdere locaties en via meerdere kanalen.

U kunt de gewenste structuur eenvoudig ontwerpen met de Content Fragment Model Editor in Adobe Experience Manager. De belangrijkste uitdaging om de Fragments van de Inhoud van Adobe Experience Manager (of om het even welke andere gegevens) met uw toepassing van de PWA Studio te integreren is het halen van gegevens van veelvoudige eindpunten van GraphQL. De reden is dat uit de doos, PWA Studio met één enkel eindpunt van Adobe Commerce GraphQL werkt.

## Architectuur {#architecture}

![ PWA headless architectuur ](/help/commerce/cif/assets/pwa-studio/PWA-Studio_Architecture.png)

## PWA Studio instellen {#setup-pwa}

Aan opstelling volgt uw PWA Studio app, de documentatie van de PWA Studio van Adobe Commerce [ ](https://developer.adobe.com/commerce/pwa-studio/tutorials/).

Om PWA Studio met het eindpunt van GraphQL van AEM te verbinden, kunt u de [ AEM Uitbreiding voor PWA Studio ](https://github.com/adobe/aem-pwa-studio-extensions) gebruiken.

1. Ontdek de opslagplaats

1. Voeg de extensie toe als ontwikkelafhankelijkheid in de toepassing PWA Studio.

   ```javascript
   yarn add --dev file:{path-to-extension}/extension
   ```

1. Voeg de omslag van de Verbinding van Apollo aan uw toepassing van de PWA Studio toe. Breng de volgende wijzigingen aan in pwa-root/src/index.js:

   ```javascript
     import { linkWrapper } from '@adobe/pwa-studio-aem-cfm-blog-extension';
   
   // ...
   
   <Adapter apiBase={apiBase} apollo={{ link: linkWrapper(apolloLink) }} store={store}>
   ```

   U kunt meer details op de aanpassing van de Cliënt van Apollo in [ linkWrapper.js ](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/linkWrapper.js) vinden.

1. Als u de navigatiecomponent wilt uitbreiden met een blogbericht, voegt u de volgende aanpassingen toe aan pwa-root/local-intercept.js:

   ```javascript
   const addBlogToNavigation = require('@adobe/pwa-studio-aem-cfm-blog-extension/src/addBlogToNavigation');
   
   function localIntercept(targets) {
       addBlogToNavigation(targets);
   }    
   ```

   U kunt meer details over de aanpassing van de component van de Navigatie in [ addBlogToNavigation.js ](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/addBlogToNavigation.js) en in de [ documentatie van het Kader van de Uitbreidbaarheid ](https://developer.adobe.com/commerce/pwa-studio/guides/general-concepts/extensibility/) van PWA Studio vinden.

1. De Apollo-client verwacht het eindpunt van AEM GraphQL op `<https://pwa-studio/endpoint.js>` . Om het eindpunt aan deze plaats in kaart te brengen, pas de configuratie UPWARD van uw toepassing van de PWA Studio aan:
a. Aan `pwa-root/.env`, voeg de variabele AEM_CFM_GRAPHQL toe, en pas het aan uw AEM Punt van de Fragments GraphQL van de Inhoud aan.

   Voorbeeld: AEM_CFM_GRAPHQL=<http://localhost:4503/content/graphql/global>

   b. Voeg een proxyoplosser toe aan uw UPWARD-configuratie. Een voorbeeld-UPWARD-configuratie kan er als volgt uitzien:

```json
   response:
     resolver: conditional
     when:
       - matches: request.url.pathname
         pattern: ^/endpoint.json(/|$)
         use: aemProxy
     default: veniaResponse

   aemProxy:
     resolver: proxy
     target: env.AEM_CFM_GRAPHQL
     ignoreSSLErrors: true

   status: response.status
   headers: response.headers
   body: response.body
```

## AEM instellen {#setup-aem}

Volg de documentatie van de Fragmenten van de Inhoud van de AEM aan opstelling een eindpunt van GraphQL voor uw AEM project. Ook, in uw AEM project, voeg de volgende configuraties toe om uw toepassing van de PWA Studio toe te staan om tot het eindpunt van GraphQL toegang te hebben:

* Beleid voor het delen van bronnen tussen verschillende bronnen van Adoben (com.adobe.granite.cors.impl.CORSPopolicyImpl)

  Stel de eigenschap `allowedorigin` in op de volledige hostnaam van de PWA-toepassing.

  Voorbeeld: `<https://pwa-studio-test-vflyn.local.pwadev:9366>`

* Apache Sling Referrer-filter (org.apache.sling.security.impl.ReferrerFilter.cfg.json)

  Stel de eigenschap allow.hosts in op de hostnaam van uw PWA-toepassing.

  Voorbeeld: pwa-studio-test-vflyn.local.pwadev

Hier vindt u volledige voorbeelden van beide configuraties: <https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension/aem/config/src/main/content/jcr_root/apps/blog-demo/config> .

Om het eindpunt van GraphQL te tonen, stelde de Adobe sommige modellen van het Fragmentmodel van de steekproefinhoud en gegevens door middel van een inhoudspakket voor. Deze stukken werken samen met de React Components die van de uitbreiding van de PWA Studio wordt voorzien.

## Hoe wordt het gebruikt {#how-to-use}

Deze extensie wordt beschouwd als een voorbeeldimplementatie voor het tot stand brengen van een verbinding tussen een PWA Studio-toepassing en AEM om inhoud op te halen en weer te geven via GraphQL.

Afhankelijk van uw gebruiksscenario wilt u uw eigen aangepaste modellen voor inhoudsfragmenten maken die resulteren in een aangepast GraphQL-schema dat vervolgens door uw eigen React-componenten kan worden gebruikt.

Productie-instellingen kunnen in meerdere opzichten verschillen.

* U kunt één gefederaliseerd GraphQL-eindpunt hebben, waarbij AEM- en Adobe Commerce GraphQL-gegevens worden gecombineerd in plaats van dat de Apollo-client wordt aangepast.
* Uw toepassing van de PWA Studio kon het eindpunt URL van AEM GraphQL direct, zonder een volmacht met UPWARD gebruiken. De proxy kan ook naar een andere laag worden verplaatst (bijvoorbeeld CDN).
* De benadering past het beste voor u ook sterk afhankelijk van hoe u de toepassing van de PWA Studio aan het eind - gebruiker levert.

Deze extensie bevat twee voorbeelden.

### Blog {#blog}

Blogberichten weergeven op basis van bepaalde modellen van inhoudsfragmenten. Bovendien bevat het voorbeelden van hoe te om de cliënt van Apollo te vormen om met het AEM eindpunt van GraphQL te werken en hoe te om de navigatiecomponent in PWA Studio uit te breiden. Zie [ GitHub ](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension) voor meer details.

### PDP-verrijking {#pdp-enrichment}

Laat marketers toe om PDPs met extra inhoud gemakkelijk te verrijken die als Fragments van de Inhoud wordt beheerd. Zie [ GitHub ](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cif-product-page-extension) voor meer details.
