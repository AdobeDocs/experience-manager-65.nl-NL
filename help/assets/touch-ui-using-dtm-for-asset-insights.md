---
title: Asset Insights inschakelen via DTM
description: Leer hoe u DTM (Adobe Dynamic Tag Management) gebruikt om Asset Insights in te schakelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: abc4821ec3720969bf1c2fb068744c07477aca46

---


# Asset Insights inschakelen via DTM {#enable-asset-insights-through-dtm}

Het dynamische Beheer van de Markering van Adobe is een hulpmiddel dat uw digitale marketing hulpmiddelen activeert. Deze service wordt gratis geleverd aan klanten van Adobe Analytics.

Hoewel u uw trackingcode kunt aanpassen om CMS-oplossingen van derden in staat te stellen Asset Insights te gebruiken, raadt Adobe u aan DTM te gebruiken om labels voor Asset Insights in te voegen.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

Voer deze stappen uit om Asset Insights in te schakelen via DTM.

1. Tik/klik op het AEM-logo en ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]** > **[!UICONTROL Inzichtsconfiguratie]**.
1. [AEM-instantie configureren met DTM Cloud Service](/help/sites-administering/dtm.md)

   De API-token moet beschikbaar zijn wanneer u zich aanmeldt bij [https://dtm.adobe.com](https://dtm.adobe.com/) en **[!UICONTROL Accountinstellingen]** bezoekt via het pictogram Profiel. Deze stap is niet vereist vanuit het oogpunt van Asset Insights, omdat de integratie van AEM-sites met Asset Insights nog in de werkzaamheden plaatsvindt.

1. Meld u aan bij [https://dtm.adobe.com](https://dtm.adobe.com/)en selecteer een bedrijf.
1. Een bestaande webeigenschap maken/openen

   * Selecteer het tabblad **[!UICONTROL Webeigenschappen]** en tik op Eigenschap **** toevoegen/klik op Eigenschappen toevoegen.

   * Werk de velden naar wens bij en tik op Eigenschap **** maken/klik op Eigenschap maken. Zie [documentatie](https://helpx.adobe.com/experience-manager/using/dtm.html).
   ![Webeigenschap bewerken maken](assets/Create-edit-web-property.png)

1. Selecteer op het tabblad **[!UICONTROL Regels]** de optie Regels **[!UICONTROL voor het laden van]** pagina in het navigatievenster en tik op Nieuwe regel **** maken of klik op Nieuwe regelmaken.

   ![chlimage_1-58](assets/chlimage_1-194.png)

1. Vouw **[!UICONTROL JavaScript-/tags]** van derden uit. Tik vervolgens op Nieuw script **** toevoegen of klik op het tabblad **[!UICONTROL Opeenvolgende HTML]** om het dialoogvenster Script te openen.

   ![chlimage_1-59](assets/chlimage_1-195.png)

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools > Assets]**.
1. Tik/klik op **[!UICONTROL Insights Page Tracker]**, kopieer de trackercode en plak deze vervolgens in het scriptdialoogvenster dat u in stap 6 hebt geopend. Sla de wijzigingen op.

   >[!NOTE]
   >
   > * `AppMeasurement.js` wordt verwijderd. Het is waarschijnlijk beschikbaar via het hulpprogramma Adobe Analytics van DTM.
   > * De aanroep van `assetAnalytics.dispatcher.init`() wordt verwijderd. De functie wordt naar verwachting aangeroepen zodra het hulpprogramma Adobe Analytics van DTM volledig is geladen.
   > * Afhankelijk van de locatie waar Asset Insights Page Tracker wordt gehost (bijvoorbeeld AEM, CDN enzovoort), kan de oorsprong van de scriptbron wijzigingen vereisen.
   > * In het geval van door AEM gehoste paginanummering, moet de bron verwijzen naar een publicatie-instantie met de hostnaam van de verzender-instantie.


1. Ga naar `https://dtm.adobe.com`. Klik op **[!UICONTROL Overzicht]** in de webeigenschap en klik op Gereedschap **** Toevoegen of open een bestaand hulpprogramma voor Adobe Analytics. Tijdens het creëren van het hulpmiddel, kunt u de Methode **[!UICONTROL van de]** Configuratie aan **[!UICONTROL Automatisch]** plaatsen.

   ![Gereedschap Adobe Analytics toevoegen](assets/Add-Adobe-Analytics-Tool.png)

   Selecteer de gewenste opties voor het rapport Staging/Productie.

1. Vouw **[!UICONTROL Bibliotheekbeheer]** uit en zorg ervoor dat Bibliotheek **[!UICONTROL laden bij]** is ingesteld op **[!UICONTROL Bovenkant]** pagina.

   ![chlimage_1-61](assets/chlimage_1-197.png)

1. Vouw **[!UICONTROL Paginacode]** aanpassen uit en klik of tik op **[!UICONTROL Editor]** openen.

   ![chlimage_1-62](assets/chlimage_1-198.png)

1. Plak de volgende code in het venster:

   ```Java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, please include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * De regel voor het laden van pagina&#39;s in DTM bevat alleen de `pagetracker.js` code. Alle `assetAnalytics` velden worden beschouwd als overschrijvingen voor standaardwaarden. Deze zijn niet standaard vereist.
   * De codevraag `assetAnalytics.dispatcher.init()` na het ervoor zorgen dat `_satellite.getToolsByType('sc')[0].getS()` wordt geïnitialiseerd en beschikbaar `assetAnalytics,dispatcher.init` is. Daarom kunt u overslaan toevoegend het in stap 11.
   * Zoals aangegeven in opmerkingen in de code van Insights Page Tracker (**[!UICONTROL Tools > Assets > Insights Page Tracker]**), zijn de eerste drie argumenten (RSID, Tracking Server en Visitor Namespace) irrelevant wanneer Paginanummering geen `AppMeasurement` object maakt. Lege tekenreeksen worden doorgegeven om dit te markeren.\
      De resterende argumenten komen overeen met wat is geconfigureerd op de pagina Inzichten configureren (**[!UICONTROL Opties > Middelen > Inzichten configureren]**).
   * Het object AppMeasurement wordt opgehaald door te zoeken `satelliteLib` naar alle beschikbare SiteCatalyst-engines. Als er meerdere tags zijn geconfigureerd, wijzigt u de index van de arraykiezer op de juiste manier. Items in de array worden geordend volgens de SiteCatalyst-gereedschappen die beschikbaar zijn in de DTM-interface.

1. Sla het venster Code-editor op, sluit dit en sla de wijzigingen vervolgens op in de configuratie van het gereedschap.
1. Geef op het tabblad **[!UICONTROL Goedkeuringen]** beide goedkeuringen die in behandeling zijn goed. De tag DTM kan worden ingevoegd in uw webpagina. Zie DTM [integreren in aangepaste paginasjablonen](https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template/)voor meer informatie over het invoegen van DTM-tags in webpagina&#39;s.
