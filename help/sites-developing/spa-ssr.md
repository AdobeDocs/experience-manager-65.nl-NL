---
title: SPA en rendering op de server
seo-title: SPA en rendering op de server
description: 'null'
seo-description: 'null'
uuid: 27e26e3f-65d4-4069-b570-58b8b9e2a1ae
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 844e5c96-2a18-4869-b4c8-2fb9efe0332a
docset: aem65
translation-type: tm+mt
source-git-commit: 41e30a668c8c02f2c43e509ed708c4b9fa39a269
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 0%

---


# SPA en rendering op de server{#spa-and-server-side-rendering}

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA kader gebaseerde cliënt-zijteruggeven (b.v. Reageren of Angular) vereisen.

>[!NOTE]
>
>AEM 6.5.1.0 of hoger is vereist om de SPA renderfuncties aan de serverzijde te kunnen gebruiken zoals in dit document wordt beschreven.

## Overzicht {#overview}

Toepassingen op één pagina (SPA) kunnen de gebruiker een rijke, dynamische ervaring bieden die op vertrouwde manieren reageert en zich gedraagt, vaak net als een native toepassing. [Dit wordt bereikt door op de client te vertrouwen om de inhoud op voorhand te laden en vervolgens de verwerking van ](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) gebruikersinteractie intensief op te heffen, zodat de benodigde hoeveelheid communicatie tussen de client en de server tot een minimum wordt beperkt, waardoor de app reactiever wordt.

Dit kan echter leiden tot langere laadtijden, vooral als de SPA groot en rijk is aan inhoud. Om de laadtijden te optimaliseren, kan een deel van de inhoud op de server worden gerenderd. Met SSR (serverside rendering) kunt u de eerste belasting van de pagina versnellen en vervolgens verdere rendering doorgeven aan de client.

## Wanneer moet u SSR {#when-to-use-ssr} gebruiken?

SSR is niet vereist voor alle projecten. Hoewel AEM volledig JS SSR voor SPA steunt, adviseert Adobe niet het systematisch voor elk project uit te voeren.

Wanneer u besluit SSR te implementeren, moet u eerst inschatten welke extra complexiteit, inspanning en kosten het toevoegen van SSR realistisch vertegenwoordigt voor het project, inclusief het langetermijnonderhoud. Een SSR-architectuur mag alleen worden gekozen wanneer de toegevoegde waarde duidelijk hoger is dan de geraamde kosten.

SSR verstrekt gewoonlijk één of andere waarde wanneer er duidelijk &quot;ja&quot;aan één van beiden van de volgende vragen is:

* **SEO:** Is SSR eigenlijk nog vereist om uw plaats behoorlijk te worden geïndexeerd door de onderzoeksmotoren die verkeer brengen? Vergeet niet dat de zoekmachine die als hoofdopzoekprogramma wordt gebruikt nu JS evalueert.
* **Paginasnelheid:** Biedt SSR een meetbare snelheidsverbetering in levensechte omgevingen en vergroot de algehele gebruikerservaring?

Slechts wanneer minstens één van deze twee vragen met duidelijk &quot;ja&quot;voor uw project wordt beantwoord adviseert Adobe het uitvoeren van SSR. In de volgende secties wordt beschreven hoe u dit kunt doen met Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-i-o-runtime}

Als u &lt;a0/ zeker bent dat uw project de implementatie van SSR1/> vereist, is de aanbevolen Adobe Adobe I/O Runtime te gebruiken.[](/help/sites-developing/spa-ssr.md#when-to-use-ssr)

Ga voor meer informatie over Adobe I/O Runtime naar

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - voor een overzicht van de service
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - voor gedetailleerde documentatie op het platform

In de volgende secties wordt beschreven hoe Adobe I/O Runtime kan worden gebruikt om SSR voor uw SPA in twee verschillende modellen te implementeren:

* [AEM-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#aem-driven-communication-flow)
* [Adobe I/O Runtime-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe raadt een aparte Adobe I/O Runtime-instantie aan voor elke AEM omgeving (auteur, publicatie, werkgebied, enz.).

## Configuratie externe renderer {#remote-renderer-configuration}

AEM moet weten waar de op afstand gerenderde inhoud kan worden opgehaald. Ongeacht [welk model u verkiest om voor SSR uit te voeren, ](#adobe-i-o-runtime) u zult moeten specificeren om tot deze verre teruggevende dienst AEM toegang te hebben.

Dit wordt gedaan via **RemoteContentRenderer - de Dienst OSGi van de Fabriek van de Configuratie**. Zoek naar het koord &quot;RemoteContentRenderer&quot;in de console van de Configuratie van de Console van het Web bij `http://<host>:<port>/system/console/configMgr`.

![Rendererconfiguratie](assets/rendererconfig.png)

De volgende velden zijn beschikbaar voor de configuratie:

* **Patroon**  inhoudspad - Reguliere expressie voor afstemming van een deel van de inhoud, indien nodig
* **Het verre eindpunt URL**  - URL van het eindpunt dat voor het produceren van de inhoud verantwoordelijk is
   * Gebruik het beveiligde HTTPS-protocol als dit zich niet in het lokale netwerk bevindt.
* **Extra verzoekkopballen**  - de Extra kopballen die aan het verzoek moeten worden toegevoegd dat naar het verre eindpunt wordt verzonden
   * Patroon: `key=value`
* **Time-out**  aanvragen - Time-out externe hostaanvraag in milliseconden

>[!NOTE]
>
>Ongeacht of u ervoor kiest om [AEM-gedreven communicatie stroom](#aem-driven-communication-flow) of [Adobe I/O Runtime-gedreven stroom uit te voeren, ](#adobe-i-o-runtime-driven-communication-flow) moet u een verre configuratie van inhoudrenderer bepalen.
>
>Deze configuratie moet ook worden bepaald als u om [een server van douaneNode.js kiest te gebruiken.](#using-node-js)

>[!NOTE]
>
>Deze configuratie gebruikt [De Verre Renderer van de Inhoud,](#remote-content-renderer) die extra uitbreiding en aanpassingsopties beschikbaar heeft.

## AEM-gestuurde communicatiestroom {#aem-driven-communication-flow}

Wanneer u SSR gebruikt, bevat de [workflow voor componentinteractie](/help/sites-developing/spa-overview.md#workflow) van SPA in AEM een fase waarin de initiële inhoud van de app wordt gegenereerd op Adobe I/O Runtime.

1. De browser vraagt om de SSR-inhoud van AEM.

1. AEM plaatst het model op Adobe I/O Runtime.

1. Adobe I/O Runtime retourneert de gegenereerde inhoud.

1. AEM dient de HTML die door Adobe I/O Runtime wordt geretourneerd via de HTML-sjabloon van de backend page component.

![server-side rendering-cms-drivenaemnode-adobeio](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

## Adobe I/O Runtime-gestuurde communicatiestroom {#adobe-i-o-runtime-driven-communication-flow}

In de vorige sectie worden de standaard en aanbevolen implementatie van rendering aan serverzijde beschreven met betrekking tot SPA in AEM, waarbij AEM de overvulling en weergave van inhoud uitvoert.

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
   <th><strong>via AEM</strong><br /> </th>
   <td>
    <ul>
     <li>AEM beheert waar nodig injectiebibliotheken</li>
     <li>Alleen bronnen hoeven op AEM<br /> te worden onderhouden </li>
    </ul> </td>
   <td>
    <ul>
     <li>Mogelijk niet bekend met SPA ontwikkelaar<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Meer vertrouwd voor SPA ontwikkelaars<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-bronnen die door de toepassing worden vereist, zoals CSS en JavaScript, moeten door de AEM ontwikkelaar beschikbaar worden gesteld via de eigenschap <code><a href="/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet">allowProxy</a></code><br /> </li>
     <li>Bronnen moeten worden gesynchroniseerd tussen AEM en Adobe I/O Runtime<br /> </li>
     <li>Om het ontwerpen van de SPA mogelijk te maken, is mogelijk een proxyserver voor Adobe I/O Runtime nodig</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planning voor SSR {#planning-for-ssr}

Over het algemeen hoeft slechts een deel van een toepassing aan serverzijde te worden gerenderd. Het algemene voorbeeld is de inhoud die boven de voud wordt weergegeven wanneer de pagina voor het eerst wordt geladen en op de server wordt weergegeven. Dit bespaart tijd door aan de cliënt, reeds teruggegeven inhoud te leveren. Terwijl de gebruiker met de SPA communiceert, wordt de extra inhoud door de client gerenderd.

Wanneer u rendering aan de serverzijde voor uw SPA implementeert, moet u controleren welke onderdelen van de app nodig zijn.

## Een SPA ontwikkelen met behulp van SSR {#developing-an-spa-using-ssr}

SPA componenten kunnen door de client (in de browser) of de server worden gerenderd. Bij rendering op de server zijn browsereigenschappen zoals venstergrootte en -locatie niet aanwezig. Daarom moeten SPA componenten isomorf zijn, waarbij er geen aanname is over waar ze worden gerenderd.

Als u SSR wilt gebruiken, moet u uw code zowel in AEM als op Adobe I/O Runtime implementeren, die verantwoordelijk is voor de rendering aan de serverzijde. De meeste code zijn hetzelfde, maar serverspecifieke taken verschillen.

## SSR voor SPA in AEM {#ssr-for-spas-in-aem}

SSR voor SPA in AEM vereist Adobe I/O Runtime, dat wordt opgeroepen voor het renderen van de zijde van de toepassingsinhoudsserver. Binnen de HTML van de app wordt een resource op Adobe I/O Runtime aangeroepen om de inhoud te renderen.

Net zoals AEM de Angular- en Reactie-SPA-frameworks buiten de box ondersteunt, wordt rendering aan de serverzijde ook ondersteund voor Angular- en React-apps. Zie de NPM documentatie voor beide kaders voor verdere details.

* Reageren: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Raadpleeg voor een simplistisch voorbeeld de [We.Retail Journal app](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Het rendert de volledige kant van de toepassingsserver. Hoewel dit geen echt voorbeeld is, toont het wel wat nodig is om SSR uit te voeren.

>[!CAUTION]
>
>De [We.Retail Journal app](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) is alleen bedoeld als demonstratie en gebruikt daarom Node.js als eenvoudig voorbeeld in plaats van de aanbevolen Adobe I/O Runtime. Dit voorbeeld zou niet voor om het even welk projectwerk moeten worden gebruikt.

>[!NOTE]
>
>Om het even welk AEM project zou hefboomwerking [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html), dat SPA projecten gebruikend React of Angular steunt en hefboomwerkingen de SPA SDK gebruikt.

## Node.js {#using-node-js} gebruiken

Adobe I/O Runtime is de aanbevolen oplossing voor de implementatie van SSR voor SPA in AEM.

Voor on-premesis AEM instanties, is het ook mogelijk om SSR uit te voeren gebruikend een douaneinstantie Node.js op de zelfde manier zoals hierboven beschreven. Hoewel dit door Adobe wordt gesteund, wordt het niet geadviseerd.

>[!NOTE]
>
>Node.js wordt niet ondersteund voor door Adobe gehoste AEM instanties.

>[!NOTE]
>
>Als SSR via Node.js moet worden geïmplementeerd, raadt Adobe een aparte instantie Node.js aan voor elke AEM omgeving (auteur, publicatie, werkgebied, enz.).

## Renderer voor externe inhoud {#remote-content-renderer}

De [Configuratie van de Renderer van de Verre Inhoud](#remote-content-renderer-configuration) die wordt vereist om SSR met uw SPA in AEM tikken in een meer algemene het teruggeven dienst te gebruiken die kan worden uitgebreid en worden aangepast om aan uw behoeften te voldoen.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` is de dienst OSGi om inhoud terug te winnen die op een verre server, zoals van Adobe I/O wordt teruggegeven. De inhoud die naar de externe server wordt verzonden, is gebaseerd op de doorgegeven parameter request.

`RemoteContentRenderingService` kan door gebiedsinversie in of een douaneSling model of servlet worden geïnjecteerd wanneer de extra inhoudsmanipulatie wordt vereist.

Deze service wordt intern gebruikt door de [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

`RemoteContentRendererRequestHandlerServlet` kan worden gebruikt om de verzoekconfiguratie programmatically te plaatsen. `DefaultRemoteContentRendererRequestHandlerImpl`, staat de verstrekte implementatie van de standaardverzoekmanager, u toe om veelvoudige configuraties tot stand te brengen OSGi om een plaats in de inhoudsstructuur aan een ver eindpunt in kaart te brengen.

Om een manager van het douaneverzoek toe te voegen, voer de `RemoteContentRendererRequestHandler` interface uit. Zorg ervoor dat u de componenteigenschap `Constants.SERVICE_RANKING` instelt op een geheel getal dat groter is dan 100. Dit is de positie van `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Vorm de Configuratie OSGi van de Standaardmanager {#configure-default-handler}

De configuratie van de standaardmanager moet worden gevormd zoals die in de sectie [Verre Configuratie van de Renderer van de Inhoud](#remote-content-renderer-configuration) wordt beschreven.

### Gebruik van externe inhoudrenderer {#usage}

Om een servlet te hebben halen en wat inhoud terug te keren die in de pagina kan worden ingespoten:

1. Controleer of uw externe server toegankelijk is.
1. Voeg een van de volgende fragmenten toe aan de HTML-sjabloon van een AEM component.
1. Naar keuze, creeer of wijzig de configuraties OSGi.
1. Door de inhoud van uw site bladeren

Gewoonlijk is de HTML-sjabloon van een paginacomponent de belangrijkste ontvanger van een dergelijke functie.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Vereisten {#requirements}

De servers maken gebruik van de Sling Model Exporter om de componentgegevens te serialiseren. Standaard worden zowel `com.adobe.cq.export.json.ContainerExporter` als `com.adobe.cq.export.json.ComponentExporter` ondersteund als Sling Model-adapters. Indien nodig, kunt u klassen toevoegen die het verzoek zou moeten worden aangepast aan het gebruiken van `RemoteContentRendererServlet` en het uitvoeren van `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. De extra klassen moeten `ComponentExporter` uitbreiden.
