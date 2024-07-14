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

Toepassingen op één pagina (SPA) kunnen de gebruiker een rijke, dynamische ervaring bieden die op vertrouwde manieren reageert en zich gedraagt, vaak net als een native toepassing. [ dit wordt bereikt door op de cliënt te vertrouwen om de inhoud te laden vooraan en dan het zware heffen van de behandeling van gebruikersinteractie ](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) te doen en zo de hoeveelheid communicatie nodig tussen de cliënt en de server te minimaliseren, makend app reactiever.

Dit kan echter leiden tot langere laadtijden, vooral als de SPA groot en rijk is aan inhoud. Om de laadtijden te optimaliseren, kan een deel van de inhoud op de server worden weergegeven. Met SSR (Server-Side Rendering) kunt u de eerste belasting van de pagina versnellen en vervolgens verdere rendering doorgeven aan de client.

## Wanneer gebruikt u SSR {#when-to-use-ssr}

SSR is niet vereist voor alle projecten. Hoewel AEM volledig JS SSR voor SPA steunt, beveelt de Adobe niet aan het systematisch voor elk project uit te voeren.

Wanneer u besluit SSR te implementeren, moet u eerst inschatten welke extra complexiteit, inspanning en kosten het toevoegen van SSR realistisch vertegenwoordigt voor het project, inclusief het langetermijnonderhoud. Een SSR-architectuur mag alleen worden gekozen wanneer de toegevoegde waarde duidelijk hoger is dan de geraamde kosten.

SSR verstrekt gewoonlijk één of andere waarde wanneer er duidelijk &quot;ja&quot;aan één van beiden van de volgende vragen is:

* **SEO:** Is SSR nog vereist voor uw plaats behoorlijk door de onderzoeksmotoren worden geïndexeerd die verkeer brengen? Vergeet niet dat de zoekmachine die als hoofdopzoekprogramma wordt gebruikt nu JS evalueert.
* **de Snelheid van de Pagina:** verstrekt SSR een meetbare snelheidsverbetering in milieu&#39;s in real-life en voegt aan de algemene gebruikerservaring toe?

Slechts wanneer minstens één van deze twee vragen met duidelijk &quot;ja&quot;voor uw project wordt beantwoord adviseert de Adobe het uitvoeren van SSR. In de volgende secties wordt beschreven hoe u dit kunt doen met Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-i-o-runtime}

Als u [ zeker bent dat uw project de implementatie van SSR ](/help/sites-developing/spa-ssr.md#when-to-use-ssr) vereist, is de geadviseerde oplossing van de Adobe Adobe I/O Runtime te gebruiken.

Raadpleeg de volgende secties voor meer informatie over Adobe I/O Runtime:

* [ https://developer.adobe.com/runtime/ ](https://developer.adobe.com/runtime/) - voor een overzicht van de dienst
* [ https://developer.adobe.com/runtime/docs/ ](https://developer.adobe.com/runtime/docs/) - voor gedetailleerde documentatie op het platform

In de volgende secties wordt beschreven hoe Adobe I/O Runtime kan worden gebruikt om SSR voor uw SPA in twee verschillende modellen te implementeren:

* [AEM-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#aem-driven-communication-flow)
* [Adobe I/O Runtime-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe raadt een aparte Adobe I/O Runtime-werkruimte aan per omgeving (werkgebied, proefperiode, testen, enzovoort). Dit staat voor typische patronen van de het levenscyclus van de systeemontwikkeling (SDLC) met verschillende versies van één enkele toepassing toe die aan verschillende milieu&#39;s worden opgesteld. Zie het document [ CI/CD voor de Toepassingen van App Builder van het Project ](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) voor meer informatie.
>
>Er is geen aparte werkruimte nodig per instantie (auteur, publiceren), tenzij er verschillen zijn in de runtimplementatie per instantietype.

## Configuratie van externe renderer {#remote-renderer-configuration}

AEM moet weten waar de op afstand gerenderde inhoud kan worden opgehaald. Ongeacht [ welk model u verkiest om voor SSR uit te voeren, ](#adobe-i-o-runtime), moet u specificeren om te AEM hoe te om tot deze verre teruggevende dienst toegang te hebben.

Dit wordt gedaan via de **RemoteContentRenderer - de dienst van OSGi van de Fabriek van de Configuratie**. Zoek naar het koord &quot;RemoteContentRenderer&quot;in de console van de Configuratie van de Console van het Web bij `http://<host>:<port>/system/console/configMgr`.

![ Configuratie van Renderer ](assets/rendererconfig.png)

De volgende velden zijn beschikbaar voor de configuratie:

* **het wegpatroon van de Inhoud** - Regelmatige uitdrukking om een gedeelte van de inhoud aan te passen, indien nodig
* **Verre eindpunt URL** - URL van het eindpunt dat voor het produceren van de inhoud verantwoordelijk is
   * Gebruik het beveiligde HTTPS-protocol als dit zich niet in het lokale netwerk bevindt.
* **Extra verzoekkopballen** - de Extra kopballen die aan het verzoek moeten worden toegevoegd dat naar het verre eindpunt wordt verzonden
   * Patroon: `key=value`
* **onderbreking van het Verzoek** - Verre onderbreking van het gastheerverzoek in milliseconden

>[!NOTE]
>
>Ongeacht als u verkiest om de [ AEM-gedreven communicatie stroom ](#aem-driven-communication-flow) of de [ Adobe I/O Runtime-gedreven stroom uit te voeren, ](#adobe-i-o-runtime-driven-communication-flow) u moet een verre configuratie van inhoudrenderer bepalen.
>
>Deze configuratie moet ook worden bepaald als u verkiest om een server van Node.js van de douane te gebruiken.](#using-node-js)[

>[!NOTE]
>
>Deze configuratie gebruikt [ Verre Renderer van de Inhoud, ](#remote-content-renderer) die extra uitbreiding en aanpassingsopties beschikbaar heeft.

## AEM-gestuurde communicatiestroom {#aem-driven-communication-flow}

Wanneer het gebruiken van SSR, omvat het [ werkschema van de componenteninteractie ](/help/sites-developing/spa-overview.md#workflow) van SPA in AEM een fase waarin de aanvankelijke inhoud van app op Adobe I/O Runtime wordt geproduceerd.

1. De browser vraagt om de SSR-inhoud van AEM.

1. AEM plaatst het model op Adobe I/O Runtime.

1. Adobe I/O Runtime retourneert de gegenereerde inhoud.

1. AEM dient de HTML die door Adobe I/O Runtime wordt geretourneerd via de HTML-sjabloon van de achtergrondpagina-component.

![ server-kant-teruggeven-cms-drivenaemnode-adobeio ](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

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
   <th><strong> als AEM </strong><br /> </th>
   <td>
    <ul>
     <li>AEM beheert waar nodig injectiebibliotheken</li>
     <li>Bronnen alleen behouden op AEM<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Mogelijk niet bekend met SPA ontwikkelaar <br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Bewegend aan SPA ontwikkelaars <br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-bronnen die door de toepassing worden vereist, zoals CSS en JavaScript, moeten door de AEM ontwikkelaar beschikbaar worden gesteld via de eigenschap <code><a href="/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet">allowProxy</a></code> <br /> </li>
     <li>De middelen moeten tussen AEM en Adobe I/O Runtime <br /> worden gesynchroniseerd </li>
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

* Reageren: [ https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [ https://github.com/adobe/aem-sample-we-retail-journal/blob/master/angular-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/angular-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Voor een simplistisch voorbeeld, zie [ Wij.Retail app van het Dagboek ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Het rendert de volledige kant van de toepassingsserver. Hoewel dit geen echt voorbeeld is, toont het wel wat nodig is om SSR uit te voeren.

>[!CAUTION]
>
>De {](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) app van het Dagboek 0} Wij.Retail is slechts voor demonstratiedoeleinden en gebruikt daarom Node.js als eenvoudig voorbeeld in plaats van geadviseerde Adobe I/O Runtime. [ Gebruik dit voorbeeld niet voor projectwerk.

>[!NOTE]
>
>Om het even welk AEM project zou [ AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat SPA projecten gebruikend React of Angular steunt en SPA SDK gebruikt.

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

De [ Verre Configuratie van Renderer van de Inhoud ](#remote-content-renderer-configuration) die wordt vereist om SSR met uw SPA in AEM tikken in een meer algemene het teruggeven dienst te gebruiken die kan worden uitgebreid en worden aangepast om aan uw behoeften te voldoen.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` is de dienst OSGi om inhoud terug te winnen die op een verre server, zoals van Adobe I/O wordt teruggegeven. De inhoud die naar de externe server wordt verzonden, is gebaseerd op de doorgegeven parameter request.

`RemoteContentRenderingService` kan worden geïnjecteerd door afhankelijkheid in een aangepast Sling-model of servlet wanneer aanvullende inhoudsmanipulatie vereist is.

Deze dienst wordt intern gebruikt door [ RemoteContentRendererRequestHandlerServlet ](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

`RemoteContentRendererRequestHandlerServlet` kan worden gebruikt om de verzoekconfiguratie programmatically te plaatsen. `DefaultRemoteContentRendererRequestHandlerImpl`, laat de verstrekte implementatie van de standaardverzoekmanager, u veelvoudige configuraties tot stand brengen OSGi om een plaats in de inhoudsstructuur aan een ver eindpunt in kaart te brengen.

Implementeer de interface `RemoteContentRendererRequestHandler` om een aangepaste aanvraaghandler toe te voegen. U moet de componenteigenschap `Constants.SERVICE_RANKING` instellen op een geheel getal dat groter is dan 100. Dit is de positie van de `DefaultRemoteContentRendererRequestHandlerImpl` .

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Vorm de Configuratie OSGi van de Standaardmanager {#configure-default-handler}

De configuratie van de standaardmanager moet worden gevormd zoals die in de sectie [ Verre Configuratie van de Renderer van de Inhoud ](#remote-content-renderer-configuration) wordt beschreven.

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

De servlets gebruiken de Verschuivende ModelExporter om de componentengegevens in series te vervaardigen. Standaard worden zowel `com.adobe.cq.export.json.ContainerExporter` als `com.adobe.cq.export.json.ComponentExporter` ondersteund als Sling Model-adapters. Indien nodig, kunt u klassen toevoegen die de aanvraag moet worden aangepast aan het gebruik van `RemoteContentRendererServlet` en het implementeren van `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses` . De extra klassen moeten `ComponentExporter` uitbreiden.
