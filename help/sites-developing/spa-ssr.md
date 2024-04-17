---
title: SPA en rendering op de server
description: Meer informatie over SPA en rendering op de server in Adobe Experience Manager.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: a80bc883-e0f6-4714-bd28-108262f96d77
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1659'
ht-degree: 0%

---

# SPA en rendering op de server{#spa-and-server-side-rendering}

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA op kader-gebaseerde cliënt-zijteruggeven (bijvoorbeeld, Reageren of Angular) vereisen.

>[!NOTE]
>
>Adobe Experience Manager (AEM) 6.5.1.0 of hoger is vereist als u de SPA renderfuncties aan de serverzijde wilt gebruiken, zoals in dit document wordt beschreven.

## Overzicht {#overview}

Toepassingen op één pagina (SPA) kunnen de gebruiker een rijke, dynamische ervaring bieden die op vertrouwde manieren reageert en zich gedraagt, vaak net als een native toepassing. [Dit wordt bereikt door op de client te vertrouwen dat de inhoud op de voorgrond wordt geladen en vervolgens de interactie van de gebruiker intensief wordt afgehandeld](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) en zo de hoeveelheid communicatie die nodig is tussen de client en de server tot een minimum te beperken, waardoor de app reactiever wordt.

Dit kan echter leiden tot langere laadtijden, vooral als de SPA groot en rijk is aan inhoud. Om de laadtijden te optimaliseren, kan een deel van de inhoud op de server worden weergegeven. Met SSR (Server-Side Rendering) kunt u de eerste belasting van de pagina versnellen en vervolgens verdere rendering doorgeven aan de client.

## Wanneer gebruikt u SSR {#when-to-use-ssr}

SSR is niet vereist voor alle projecten. Hoewel AEM volledig JS SSR voor SPA steunt, beveelt de Adobe niet aan het systematisch voor elk project uit te voeren.

Wanneer u besluit SSR te implementeren, moet u eerst inschatten welke extra complexiteit, inspanning en kosten het toevoegen van SSR realistisch vertegenwoordigt voor het project, inclusief het langetermijnonderhoud. Een SSR-architectuur mag alleen worden gekozen wanneer de toegevoegde waarde duidelijk hoger is dan de geraamde kosten.

SSR verstrekt gewoonlijk één of andere waarde wanneer er duidelijk &quot;ja&quot;aan één van beiden van de volgende vragen is:

* **SEO:** Is SSR nog vereist voor uw plaats om behoorlijk door de onderzoeksmotoren worden geïndexeerd die verkeer brengen? Vergeet niet dat de zoekmachine die als hoofdopzoekprogramma wordt gebruikt nu JS evalueert.
* **Paginasnelheid:** Biedt SSR een meetbare snelheidsverbetering in levensechte omgevingen en vergroot de algehele gebruikerservaring?

Slechts wanneer minstens één van deze twee vragen met duidelijk &quot;ja&quot;voor uw project wordt beantwoord adviseert de Adobe het uitvoeren van SSR. In de volgende secties wordt beschreven hoe u dit kunt doen met Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-i-o-runtime}

Als u [vertrouwen erop dat uw project de implementatie van SSR vereist](/help/sites-developing/spa-ssr.md#when-to-use-ssr)De aanbevolen oplossing van Adobe is het gebruik van Adobe I/O Runtime.

Raadpleeg de volgende secties voor meer informatie over Adobe I/O Runtime:

* [https://developer.adobe.com/runtime/](https://developer.adobe.com/runtime/) - voor een overzicht van de dienst
* [https://developer.adobe.com/runtime/docs/](https://developer.adobe.com/runtime/docs/) - voor gedetailleerde documentatie op het platform

In de volgende secties wordt beschreven hoe Adobe I/O Runtime kan worden gebruikt om SSR voor uw SPA in twee verschillende modellen te implementeren:

* [AEM-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#aem-driven-communication-flow)
* [Adobe I/O Runtime-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe raadt een aparte Adobe I/O Runtime-werkruimte aan per omgeving (werkgebied, proefperiode, testen, enzovoort). Dit staat voor typische patronen van de het levenscyclus van de systeemontwikkeling (SDLC) met verschillende versies van één enkele toepassing toe die aan verschillende milieu&#39;s worden opgesteld. Zie het document [CI/CD voor de Toepassingen van de Bouwer van de Project](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) voor meer informatie .
>
>Er is geen aparte werkruimte nodig per instantie (auteur, publiceren), tenzij er verschillen zijn in de runtimplementatie per instantietype.

## Configuratie van externe renderer {#remote-renderer-configuration}

AEM moet weten waar de op afstand gerenderde inhoud kan worden opgehaald. Ongeacht [welk model u verkiest om voor SSR uit te voeren,](#adobe-i-o-runtime), moet u opgeven hoe u toegang AEM tot deze externe renderingsservice.

Dit gebeurt via de **RemoteContentRenderer - Configuratie in fabriek OSGi-service**. Zoek naar het koord &quot;RemoteContentRenderer&quot;in de console van de Configuratie van de Console van het Web bij `http://<host>:<port>/system/console/configMgr`.

![Rendererconfiguratie](assets/rendererconfig.png)

De volgende velden zijn beschikbaar voor de configuratie:

* **Inhoudspatroon** - Reguliere expressie die zo nodig overeenkomt met een deel van de inhoud
* **URL van extern eindpunt** - URL van het eindpunt dat verantwoordelijk is voor het genereren van de inhoud
   * Gebruik het beveiligde HTTPS-protocol als dit zich niet in het lokale netwerk bevindt.
* **Aanvullende aanvraagheaders** - Extra kopballen die aan het verzoek moeten worden toegevoegd dat naar het verre eindpunt wordt verzonden
   * Patroon: `key=value`
* **Verzoek om time-out** - Time-out externe hostaanvraag in milliseconden

>[!NOTE]
>
>Ongeacht of u ervoor kiest om het [AEM-gestuurde communicatiestroom](#aem-driven-communication-flow) of de [door Adobe I/O Runtime aangedreven stroom,](#adobe-i-o-runtime-driven-communication-flow) u moet een configuratie van een externe inhoudrenderer definiëren.
>
>Deze configuratie moet ook worden gedefinieerd als u ervoor kiest [gebruik een aangepaste Node.js-server.](#using-node-js)

>[!NOTE]
>
>Deze configuratie gebruikt de [Renderer voor externe inhoud,](#remote-content-renderer) waarvoor aanvullende opties voor extensie en aanpassing beschikbaar zijn.

## AEM-gestuurde communicatiestroom {#aem-driven-communication-flow}

Als u SSR gebruikt, wordt [interactieworkflow voor componenten](/help/sites-developing/spa-overview.md#workflow) SPA in AEM omvat een fase waarin de initiële inhoud van de app op Adobe I/O Runtime wordt gegenereerd.

1. De browser vraagt om de SSR-inhoud van AEM.

1. AEM plaatst het model op Adobe I/O Runtime.

1. Adobe I/O Runtime retourneert de gegenereerde inhoud.

1. AEM dient de HTML die door Adobe I/O Runtime wordt geretourneerd via de HTML-sjabloon van de achtergrondpagina-component.

![server-side rendering-cms-drivenaemnode-adobeio](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

## Adobe I/O Runtime-gestuurde communicatiestroom {#adobe-i-o-runtime-driven-communication-flow}

In de vorige sectie worden de standaard en aanbevolen implementatie beschreven van rendering op de server met betrekking tot SPA in AEM, waarbij AEM de overvulling en het serveren van inhoud uitvoert.

Alternatief, kan SSR worden uitgevoerd zodat Adobe I/O Runtime voor bootstrapping verantwoordelijk is, effectief omkeerend de communicatie stroom.

Beide modellen zijn geldig en worden ondersteund door AEM. Men moet echter eerst de voor- en nadelen van elk model in overweging nemen voordat men een bepaald model toepast.

<table>
 <tbody>
  <tr>
   <th><strong>Bootstrapping</strong></th>
   <th><strong>Voordelen</strong></th>
   <th><strong>Nadelen</strong></th>
  </tr>
  <tr>
   <th><strong>AEM</strong><br /> </th>
   <td>
    <ul>
     <li>AEM beheert waar nodig injectiebibliotheken</li>
     <li>Bronnen alleen behouden op AEM<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Mogelijk niet bekend bij SPA ontwikkelaar<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>SPA ontwikkelaars meer bekend<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-bronnen die door de toepassing worden vereist, zoals CSS en JavaScript, moeten door de AEM ontwikkelaar beschikbaar worden gesteld via de <code><a href="/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet">allowProxy</a></code> eigenschap<br /> </li>
     <li>Bronnen moeten worden gesynchroniseerd tussen AEM en Adobe I/O Runtime<br /> </li>
     <li>Om het ontwerpen van de SPA mogelijk te maken, is mogelijk een proxyserver voor Adobe I/O Runtime nodig</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planning voor SSR {#planning-for-ssr}

Slechts een deel van een toepassing moet serverzijde worden teruggegeven. Het algemene voorbeeld is de inhoud die boven de voud wordt weergegeven bij de eerste keer dat de pagina wordt geladen, wordt weergegeven op de server. Dit bespaart tijd door aan de cliënt, reeds teruggegeven inhoud te leveren. Terwijl de gebruiker met de SPA communiceert, wordt de extra inhoud door de client gerenderd.

Wanneer u rendering op de server wilt implementeren voor uw SPA, moet u controleren welke delen van de app u nodig hebt.

## Een SPA ontwikkelen met behulp van SSR {#developing-an-spa-using-ssr}

SPA componenten kunnen door de client (in de browser) of de server worden gerenderd. Bij rendering op de server zijn browsereigenschappen zoals venstergrootte en -locatie niet aanwezig. Daarom moeten SPA componenten isomorf zijn, waarbij er geen aanname is over waar ze worden gerenderd.

Als u SSR wilt gebruiken, implementeert u uw code in AEM en op Adobe I/O Runtime, die verantwoordelijk is voor de rendering op de server. De meeste code zijn hetzelfde, maar serverspecifieke taken verschillen.

## SSR voor SPA in AEM {#ssr-for-spas-in-aem}

SSR voor SPA in AEM vereist Adobe I/O Runtime, dat wordt opgeroepen voor het renderen van de zijde van de toepassingsinhoudsserver. Binnen de HTML van de app wordt een resource op Adobe I/O Runtime aangeroepen om de inhoud te renderen.

Net zoals AEM de Angular- en Reactie-SPA-frameworks buiten de box ondersteunt, wordt rendering op de server ook ondersteund voor Angular- en Reactie-apps. Zie de NPM documentatie voor beide kaders voor verdere details.

* Reageren: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/angular-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/angular-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Zie voor een simplistisch voorbeeld [We.Retail Journal-app](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Het rendert de volledige kant van de toepassingsserver. Hoewel dit geen echt voorbeeld is, toont het wel wat nodig is om SSR uit te voeren.

>[!CAUTION]
>
>De [We.Retail Journal-app](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) is alleen bedoeld voor demonstratiedoeleinden en gebruikt daarom Node.js als eenvoudig voorbeeld in plaats van de aanbevolen Adobe I/O Runtime. Gebruik dit voorbeeld niet voor projectwerk.

>[!NOTE]
>
>Voor elk AEM project moet het [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html), die SPA projecten steunt die React of Angular gebruiken en SPA SDK gebruikt.

## Node.js gebruiken {#using-node-js}

Adobe I/O Runtime is de aanbevolen oplossing voor de implementatie van SSR voor SPA in AEM.

Voor on-premesis AEM instanties, is het ook mogelijk om SSR uit te voeren gebruikend een douaneinstantie Node.js op de zelfde manier zoals hierboven beschreven. Hoewel dit door Adobe wordt gesteund, wordt het niet geadviseerd.

>[!NOTE]
>
>Node.js wordt niet ondersteund voor op Adobe gehoste AEM instanties.

>[!NOTE]
>
>Als SSR via Node.js moet worden geïmplementeerd, raadt de Adobe een aparte instantie Node.js aan voor elke AEM omgeving (auteur, publicatie, werkgebied, enzovoort).

## Renderer voor externe inhoud {#remote-content-renderer}

De [Configuratie renderfunctie voor externe inhoud](#remote-content-renderer-configuration) die vereist is om SSR met uw SPA te gebruiken in AEM tikken op een meer algemene renderservice die kan worden uitgebreid en aangepast aan uw behoeften.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` is de dienst OSGi om inhoud terug te winnen die op een verre server, zoals van Adobe I/O wordt teruggegeven. De inhoud die naar de externe server wordt verzonden, is gebaseerd op de doorgegeven parameter request.

`RemoteContentRenderingService` kan door gebiedsinversie in of een douaneSling model of servlet worden geïnjecteerd wanneer de extra inhoudsmanipulatie wordt vereist.

Deze dienst wordt intern gebruikt door [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

De `RemoteContentRendererRequestHandlerServlet` kan worden gebruikt om programmatically de verzoekconfiguratie te plaatsen. `DefaultRemoteContentRendererRequestHandlerImpl`, laat de verstrekte implementatie van de standaardverzoekmanager, u veelvoudige configuraties OSGi tot stand brengen om een plaats in de inhoudsstructuur aan een ver eindpunt in kaart te brengen.

Om een manager van het douaneverzoek toe te voegen, voer uit `RemoteContentRendererRequestHandler` interface. Zorg ervoor dat u de `Constants.SERVICE_RANKING` componenteigenschap instellen op een geheel getal hoger dan 100. Dit is de positie van de component `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Vorm de Configuratie OSGi van de Standaardmanager {#configure-default-handler}

De configuratie van de standaardmanager moet worden gevormd zoals die in de sectie wordt beschreven [Configuratie renderfunctie voor externe inhoud](#remote-content-renderer-configuration).

### Renderergebruik van externe inhoud {#usage}

Om een servlet te hebben halen en wat inhoud terug te keren die in de pagina kan worden ingespoten:

1. Zorg ervoor dat uw externe server toegankelijk is.
1. Voeg een van de volgende fragmenten toe aan de HTML-sjabloon van een AEM component.
1. Naar keuze, creeer of wijzig de configuraties OSGi.
1. Door de inhoud van uw site bladeren

Gewoonlijk is de HTML-sjabloon van een paginacomponent de belangrijkste ontvanger van een dergelijke functie.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Vereisten {#requirements}

De servlets gebruiken de Verschuivende ModelExporter om de componentengegevens in series te vervaardigen. Standaard worden beide `com.adobe.cq.export.json.ContainerExporter` en `com.adobe.cq.export.json.ComponentExporter` worden ondersteund als Sling Model-adapters. Indien nodig kunt u klassen toevoegen waaraan de aanvraag moet worden aangepast om de opdracht `RemoteContentRendererServlet` en de uitvoering van de `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. De extra klassen moeten de `ComponentExporter`.
