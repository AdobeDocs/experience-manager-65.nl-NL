---
title: Aanbevolen procedures voor AEM Mobile On-demand Services
description: Meer informatie over de beste praktijken en richtlijnen die bevoegde ontwikkelaars van Adobe Experience Manager (AEM) helpen voor sites die sjablonen en componenten voor mobiele apps willen maken.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 63ceaba6-b796-4c13-a86d-f0609ec679c9
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---

# Aanbevolen procedures {#best-practices}

{{ue-over-mobile}}

Het maken van een AEM Mobile On-demand Services-app is niet hetzelfde als het rechtstreeks maken van een app in de shell Cordova (of PhoneGap). De ontwikkelaars zouden met moeten vertrouwd zijn:

* Plug-ins die worden ondersteund vanuit de verpakking en de specifieke plug-ins voor Adobe Experience Manager (AEM) Mobile.

>[!NOTE]
>
>Zie de volgende bronnen voor meer informatie over plug-ins:
>
>* [&#x200B; Gebruikend stop-ins Cordova in AEM Mobile &#x200B;](https://helpx.adobe.com/nl/digital-publishing-solution/help/cordova-api.html)
>* [&#x200B; Gebruikend AEM Mobile specifieke Cordova-Toegelaten stop-ins &#x200B;](https://helpx.adobe.com/nl/digital-publishing-solution/help/app-runtime-api.html)
>

* Sjablonen die plug-infunctionaliteit gebruiken, moeten zo worden geschreven dat ze nog steeds in de browser kunnen worden geschreven, zonder dat de plug-inbridge aanwezig is.

   * Bijvoorbeeld, zorg ervoor om op de *apparaat* functie te wachten alvorens te proberen om tot API van een stop toegang te hebben.

## Richtlijnen voor AEM ontwikkelaars {#guidelines-for-aem-developers}

De volgende richtlijnen helpen bevoegde AEM ontwikkelaars voor sites die sjablonen en componenten voor mobiele apps willen maken:

**Structuur AEM plaatsen malplaatjes om hergebruik en rekbaarheid aan te moedigen**

* Meerdere componentscriptbestanden verkiezen boven één monolithische

   * Verscheidene lege uitbreidingspunten worden verstrekt, zoals *customheaderlibs.html* en *customfooterlibs.html*, die de ontwikkelaar toestaan om het paginamalplaatje te veranderen terwijl het dupliceren van zo weinig kerncode mogelijk
   * De malplaatjes kunnen dan via het Sling *worden uitgebreid en worden aangepast het slingeren:resourceSuperType* mechanisme

* Rechtsom/HTML verkiezen boven JSP als sjabloontaal

   * Het gebruiken van dit moedigt een scheiding van code van prijsverhoging aan, biedt ingebouwde bescherming XSS, en heeft een meer vertrouwde syntaxis aan

**optimaliseer voor prestaties op apparaat**

* Artikelspecifiek script en stijlpagina&#39;s moeten worden opgenomen in de artikelpayload met behulp van de sjabloon voor het synchroniseren van dps-artikelinhoud
* Script- en stijlbladen die door meerdere artikelen worden gedeeld, moeten in gedeelde bronnen worden opgenomen via de sjabloon voor het synchroniseren van dps-HTMLResources-inhoud
* Verwijs niet naar externe manuscripten die teruggeven-blokkeren zijn

>[!NOTE]
>
>U kunt meer in detail over render-blokkerende externe manuscripten [&#x200B; hier &#x200B;](https://developers.google.com/speed/docs/insights/BlockingJS) leren.

**verkies app-specifieke cliënt-kant JS en CSS bibliotheken over web-specific**

* Overhead in bibliotheken zoals jQuery Mobile voorkomen om een enorme breedte aan apparaten en browsers af te handelen
* Wanneer een sjabloon wordt uitgevoerd in de webweergave van een app, hebt u controle over de platforms en versies die de app zal ondersteunen en over de kennis dat JavaScript-ondersteuning aanwezig is. Kies bijvoorbeeld Ionic (alleen de CSS) boven jQuery Mobile en Onsen UI boven Bootstrap.

>[!NOTE]
>
>Om meer diepgaand over jQuery mobiel te leren, klik [&#x200B; hier &#x200B;](https://jquerymobile.com/browser-support/1.4/).

**voorkeur microbibliotheken over volledig-stapel**

* De tijd die nodig is om de inhoud op het glas van het apparaat te krijgen, wordt vertraagd door elke bibliotheek waarvan uw artikelen afhankelijk zijn. Deze vertraging wordt vergroot wanneer een nieuwe webweergave wordt gebruikt om elk artikel te renderen. Elke bibliotheek moet dus opnieuw volledig worden geïnitialiseerd
* Als uw artikelen niet als SPA zijn samengesteld (apps met één pagina), hoeft u waarschijnlijk geen bibliotheek met volledige stapels zoals Angular op te nemen
* Voorkeur kleinere, enig-doelbibliotheken die helpen interactiviteit toevoegen uw pagina vereist, zoals [&#x200B; Fastclick &#x200B;](https://github.com/ftlabs/fastclick) of [&#x200B; Velocity.js &#x200B;](https://velocityjs.org)

**minimaliseer grootte van artikellading**

* Gebruik de kleinst mogelijke middelen die effectief de grootste viewport kunnen behandelen u, bij redelijke resolutie steunt
* Gebruik een hulpmiddel als *ImageOptim* op uw beelden zodat kunt u om het even welke overtollige meta-gegevens verwijderen

## Aan de slag {#getting-ahead}

Zie de volgende bronnen voor meer informatie over de andere twee rollen en verantwoordelijkheden:

* [Beheerder](/help/mobile/aem-mobile.md)
* [Auteur](/help/mobile/aem-mobile-on-demand.md)
