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
source-git-commit: 2dad220d6593ed542816f8a97b0d4b44f0d57876

---


# SPA en rendering op de server{#spa-and-server-side-rendering}

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

>[!NOTE]
>
>AEM 6.5.1.0 of recenter wordt vereist om de server van het KUUROORD te gebruiken teruggevende eigenschappen zoals die in dit document worden beschreven.

## Overzicht {#overview}

De enige paginatoepassingen (SPAs) kunnen de gebruiker een rijke, dynamische ervaring aanbieden die op vertrouwde manieren reageert en gedraagt, vaak enkel als een inheemse toepassing. [Dit wordt bereikt door op de client te vertrouwen om de inhoud op voorgrond te laden en vervolgens de verwerking van gebruikersinteractie](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) zwaar op te heffen, zodat de benodigde hoeveelheid communicatie tussen de client en de server tot een minimum wordt beperkt, waardoor de app reactiever wordt.

Nochtans kan dit tot langere aanvankelijke ladingstijden leiden, vooral als SPA groot en rijk in zijn inhoud is. Om de laadtijden te optimaliseren, kan een deel van de inhoud op de server worden gerenderd. Met SSR (serverside rendering) kunt u de eerste belasting van de pagina versnellen en vervolgens verdere rendering doorgeven aan de client.

## Wanneer gebruikt u SSR {#when-to-use-ssr}

SSR is niet vereist voor alle projecten. Alhoewel AEM volledig JS SSR voor SPA steunt, adviseert Adobe niet het systematisch voor elk project uit te voeren.

Wanneer u besluit SSR te implementeren, moet u eerst inschatten welke extra complexiteit, inspanning en kosten het toevoegen van SSR realistisch vertegenwoordigt voor het project, inclusief het langetermijnonderhoud. Een SSR-architectuur mag alleen worden gekozen wanneer de toegevoegde waarde duidelijk hoger is dan de geraamde kosten.

SSR verstrekt gewoonlijk één of andere waarde wanneer er duidelijk &quot;ja&quot;aan één van beiden van de volgende vragen is:

* **** SEO: Is SSR eigenlijk nog vereist voor uw plaats om behoorlijk door de onderzoeksmotoren worden geïndexeerd die verkeer brengen? Vergeet niet dat de zoekmachine die als hoofdopzoekprogramma wordt gebruikt nu JS evalueert.
* **** Paginasnelheid: Biedt SSR een meetbare snelheidsverbetering in levensechte omgevingen en vergroot de algehele gebruikerservaring?

Alleen wanneer ten minste een van deze twee vragen met een duidelijk &quot;ja&quot; voor uw project wordt beantwoord, raadt Adobe aan SSR te implementeren. In de volgende secties wordt beschreven hoe u dit kunt doen met Adobe I/O Runtime.

## Adobe I/O-runtime {#adobe-i-o-runtime}

Als u zeker [bent dat voor uw project de implementatie van SSR](/help/sites-developing/spa-ssr.md#when-to-use-ssr)is vereist, kunt u het beste Adobe I/O-runtime gebruiken.

Ga voor meer informatie over Adobe I/O Runtime naar

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - voor een overzicht van de dienst
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - voor gedetailleerde documentatie op het platform

In de volgende secties wordt gedetailleerd beschreven hoe Adobe I/O Runtime kan worden gebruikt om SSR voor uw SPA in twee verschillende modellen uit te voeren:

* [AEM-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#aem-driven-communication-flow)
* [Adobe I/O Runtime-gestuurde communicatiestroom](/help/sites-developing/spa-ssr.md#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe raadt een aparte Adobe I/O Runtime-instantie aan voor elke AEM-omgeving (auteur, publicatie, werkgebied, enz.).

## AEM-gestuurde communicatiestroom {#aem-driven-communication-flow}

Wanneer u SSR gebruikt, bevat de workflow [voor](/help/sites-developing/spa-overview.md#workflow) componentinteractie van SPA&#39;s in AEM een fase waarin de initiële inhoud van de app wordt gegenereerd in Adobe I/O-runtime.

1. De browser vraagt de SSR-inhoud op van AEM.

1. AEM publiceert het model naar Adobe I/O Runtime.

1. Adobe I/O Runtime keert de geproduceerde inhoud terug.

1. AEM dient de HTML die door Adobe I/O Runtime via het malplaatje van HTML van de achterste paginacomponent is teruggekeerd.

![server-side rendering-cms-drivenaemnode-adobeio](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

## Adobe I/O Runtime-gestuurde communicatiestroom {#adobe-i-o-runtime-driven-communication-flow}

De vorige sectie beschrijft de standaard en geadviseerde implementatie van server zijteruggeven met betrekking tot SPAs in AEM, waar AEM bootstrapping en het dienen van inhoud uitvoert.

Alternatief, kan SSR worden uitgevoerd zodat de Runtime van Adobe I/O van Adobe voor bootstrapping verantwoordelijk is, effectief omkeerend de communicatie stroom.

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
     <li>De middelen moeten slechts op AEM worden gehandhaafd<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Mogelijk onbekend aan ontwikkelaar van SPA<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Vertrouwelijker aan ontwikkelaars van het KUUROORD<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-bronnen die door de toepassing worden vereist, zoals CSS en JavaScript, moeten door de AEM-ontwikkelaar beschikbaar worden gesteld via de <code><a href="/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet">allowProxy</a></code> eigenschap<br /> </li>
     <li>Bronnen moeten worden gesynchroniseerd tussen AEM en Adobe I/O Runtime<br /> </li>
     <li>Om het ontwerpen van het KUUROORD toe te laten, kan een volmachtsserver voor Runtime van Adobe I/O noodzakelijk zijn</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planning voor SSR {#planning-for-ssr}

Over het algemeen hoeft slechts een deel van een toepassing aan serverzijde te worden gerenderd. Het algemene voorbeeld is de inhoud die boven de voud wordt weergegeven wanneer de pagina voor het eerst wordt geladen en op de server wordt weergegeven. Dit bespaart tijd door aan de cliënt, reeds teruggegeven inhoud te leveren. Aangezien de gebruiker met het KUUROORD in wisselwerking staat, wordt de extra inhoud teruggegeven door de cliënt.

Aangezien u overweegt het uitvoeren van server zijhet teruggeven voor uw SPA, moet u controleren voor welke delen van app het noodzakelijk zal zijn.

## Het ontwikkelen van een SPA die SSR gebruikt {#developing-an-spa-using-ssr}

De componenten van het KUUROORD zouden door de cliënt (in browser) of serverkant kunnen worden teruggegeven. Bij rendering op de server zijn browsereigenschappen zoals venstergrootte en -locatie niet aanwezig. Daarom zouden de componenten van het KUUROORD isomorf moeten zijn, die geen veronderstelling maken over waar zij zullen worden teruggegeven.

Als u SSR wilt gebruiken, moet u uw code zowel in AEM als in Adobe I/O Runtime implementeren, die verantwoordelijk is voor de rendering aan de serverzijde. De meeste code zijn hetzelfde, maar serverspecifieke taken verschillen.

## SSR voor SPA’s in AEM {#ssr-for-spas-in-aem}

SSR voor SPA&#39;s in AEM vereist Adobe I/O-runtime, die wordt aangeroepen voor het renderen van de zijde van de toepassingsinhoudsserver. Binnen de HTML van de app wordt een resource in Adobe I/O Runtime aangeroepen om de inhoud te renderen.

Net zoals AEM de Hoekse en Reacte kaders van het KUUROORD buiten de doos steunt, wordt de server zijrendering ook gesteund voor Hoekige en Reacte apps. Zie de NPM documentatie voor beide kaders voor verdere details.

* Reageren: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Hoek: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Voor een simplistisch voorbeeld raadpleegt u de app [](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)We.Retail Journal. Het rendert de volledige kant van de toepassingsserver. Hoewel dit geen echt voorbeeld is, toont het wel wat nodig is om SSR uit te voeren.

>[!CAUTION]
>
>De app [](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) We.Retail Journal is alleen bedoeld als demonstratie en gebruikt daarom Node.js als eenvoudig voorbeeld in plaats van de aanbevolen Adobe I/O-runtime. Dit voorbeeld zou niet voor om het even welk projectwerk moeten worden gebruikt.

>[!NOTE]
>
>Alle projecten van het KUUROORD op AEM zouden op [Maven Archetype voor Kit](https://github.com/adobe/aem-spa-project-archetype)van de Aanzet van het KUUROORD moeten worden gebaseerd.

## Node.js gebruiken {#using-node-js}

Adobe I/O Runtime is de geadviseerde oplossing voor het uitvoeren SSR voor SPAs in AEM.

Voor AEM-instanties ter plaatse is het ook mogelijk SSR te implementeren met een aangepaste Node.js-instantie op dezelfde manier als hierboven beschreven. Hoewel dit wordt ondersteund door Adobe, wordt dit niet aanbevolen.

>[!NOTE]
>
>Node.js wordt niet ondersteund voor door Adobe gehoste AEM-instanties.

>[!NOTE]
>
>Als SSR via Node.js moet worden geïmplementeerd, raadt Adobe een aparte instantie Node.js aan voor elke AEM-omgeving (auteur, publicatie, werkgebied, enz.).
