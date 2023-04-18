---
title: Aanbevolen procedures voor AEM Mobile On-demand Services
description: Leer over beste praktijken en richtlijnen die ervaren AEM ontwikkelaars voor plaatsen, die mobiele toepassingsmalplaatjes en componenten willen bouwen.
uuid: 7733c8b1-a88c-455c-8080-f7add4205b92
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a0647696-72c3-409b-85ba-9275d8f99cff
exl-id: 63ceaba6-b796-4c13-a86d-f0609ec679c9
source-git-commit: a2fd3c0c1892ac648c87ca0dec440e22144c37a2
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Best practices voor {#best-practices}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

Het maken van een AEM Mobile On-demand Services-app is anders dan het rechtstreeks maken van een app in de shell Cordova (of PhoneGap). De ontwikkelaars zouden met moeten vertrouwd zijn:

* Insteekmodules die uit de doos evenals de AEM Mobile specifieke stop- ins worden gesteund.

>[!NOTE]
>
>Zie de volgende bronnen voor meer informatie over plug-ins:
>
>* [Cordova-plug-ins gebruiken in AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/cordova-api.html)
>* [AEM Mobile-plug-ins gebruiken die geschikt zijn voor Cordova](https://helpx.adobe.com/digital-publishing-solution/help/app-runtime-api.html)
>


* Sjablonen die plug-infunctionaliteit gebruiken, moeten zo worden geschreven dat ze nog steeds ontwerpbaar zijn in de browser, zonder dat de plug-inbridge aanwezig is.

   * Zorg er bijvoorbeeld voor dat u wacht op de knop *deviceready* voordat u probeert toegang te krijgen tot de API van een plug-in.

## Richtlijnen voor AEM ontwikkelaars {#guidelines-for-aem-developers}

De volgende richtlijnen helpen ervaren AEM ontwikkelaars voor sites die sjablonen en componenten voor mobiele apps willen maken:

**Sjablonen voor AEM sites structureren om hergebruik en uitbreidbaarheid aan te moedigen**

* Meerdere componentscriptbestanden verkiezen boven één monolithische scriptbestand

   * Er wordt een aantal lege extensiepunten opgegeven, zoals *customheaderlibs.html* en *customfooterlibs.html*, waarmee de ontwikkelaar het paginasjabloon kan wijzigen terwijl zo weinig mogelijk kerncode wordt gedupliceerd
   * Sjablonen kunnen vervolgens worden uitgebreid en aangepast via Sling *sling:resourceSuperType* mechanisme

* Rechtsom/HTML verkiezen boven JSP als sjabloontaal

   * Het gebruiken van dit moedigt een scheiding van code van prijsverhoging aan, biedt ingebouwde bescherming XSS, en heeft een meer vertrouwde syntaxis aan

**Optimaliseren voor prestaties op het apparaat**

* Artikelspecifiek script en stijlpagina&#39;s moeten worden opgenomen in de artikellading, met gebruik van de sjabloon voor het synchroniseren van de inhoud van het dps-artikel
* Script en stijlpagina&#39;s die door meerdere artikelen worden gedeeld, moeten in gedeelde bronnen worden opgenomen via de sjabloon voor het synchroniseren van dps-HTMLResources-inhoud
* Verwijs niet naar externe manuscripten die teruggeven-blokkeren zijn

>[!NOTE]
>
>U kunt meer in detail leren over render-blokkerende externe manuscripten [hier](https://developers.google.com/speed/docs/insights/BlockingJS).

**Voorkeur voor app-specifieke client JS- en CSS-bibliotheken boven webspecifieke bibliotheken**

* Overhead in bibliotheken zoals jQuery Mobile voorkomen om een enorme breedte aan apparaten en browsers af te handelen
* Wanneer een sjabloon wordt uitgevoerd in de webweergave van een app, hebt u controle over de platformen en versies die de toepassing zal ondersteunen, en over de kennis dat JavaScript-ondersteuning aanwezig is. Kies bijvoorbeeld Ionic (misschien alleen de CSS) boven jQuery Mobile en Onsen UI boven Bootstrap.

>[!NOTE]
>
>Voor meer informatie over jQuery Mobile klikt u op [hier](https://jquerymobile.com/browser-support/1.4/).

**De voorkeur geven aan microbibliotheken via volledige stapel**

* De tijd die nodig is om de inhoud op het glas van het apparaat te krijgen, wordt vertraagd door elke bibliotheek waarvan uw artikelen afhankelijk zijn. Deze vertraging wordt vergroot wanneer een nieuwe webweergave wordt gebruikt om elk artikel te renderen. Elke bibliotheek moet dus opnieuw volledig worden geïnitialiseerd
* Als uw artikelen niet als SPA zijn samengesteld (apps met één pagina), hoeft u waarschijnlijk geen volledige stapelbibliotheek zoals Angular op te nemen
* Voorkeur voor kleinere bibliotheken voor één doel om de interactiviteit toe te voegen die uw pagina nodig heeft, zoals [Snelklikken](https://github.com/ftlabs/fastclick) of [Snelheid.js](https://velocityjs.org)

**Grootte van artikellading minimaliseren**

* Gebruik de kleinst mogelijke middelen die effectief de grootste viewport kunnen behandelen u, bij redelijke resolutie zult steunen
* Een gereedschap gebruiken als *ImageOptim* in uw afbeeldingen om eventuele overtollige metagegevens te verwijderen

## Aan de slag {#getting-ahead}

Zie de volgende bronnen voor meer informatie over de andere twee rollen en verantwoordelijkheden:

* [Beheerder](/help/mobile/aem-mobile.md)
* [Auteur](/help/mobile/aem-mobile-on-demand.md)
