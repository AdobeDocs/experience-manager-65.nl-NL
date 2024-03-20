---
title: Assets Insights inschakelen via DTM
description: Leer hoe u Adobe Dynamic Tag Management (DTM) gebruikt om Assets Insights in te schakelen.
contentOwner: AG
role: User, Admin
feature: Asset Insights,Asset Reports
exl-id: 80e8f84e-3235-4212-9dcd-6acdb9067893
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Assets Insights inschakelen via DTM {#enable-asset-insights-through-dtm}

Adobe Dynamic Tag Management is een hulpmiddel waarmee u uw digitale marketingtools kunt activeren. Deze service wordt gratis aan Adobe Analytics-klanten aangeboden. U kunt de trackingcode aanpassen om CMS-oplossingen van derden in staat te stellen om Assets Insights te gebruiken, of u kunt DTM gebruiken om asset Insights-tags in te voegen. Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

>[!CAUTION]
>
>Adobe DTM is vervangen door [!DNL Adobe Experience Platform] en zal binnenkort [einde van leven](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). Adobe beveelt aan [gebruiken [!DNL Adobe Experience Platform] voor informatie over activa](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html).

Voer deze stappen uit om Elementeninzichten door DTM toe te laten.

1. Klik op het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Insights Configuration]**.
1. [Implementatie van Experience Managers configureren met DTM Cloud Service](/help/sites-administering/dtm.md)

   De API-token moet beschikbaar zijn wanneer u zich aanmeldt bij [https://dtm.adobe.com](https://dtm.adobe.com/) en bezoek **[!UICONTROL Account Settings]** in het gebruikersprofiel. Deze stap is niet vereist vanuit het oogpunt van Assets Insights, omdat de integratie van Experience Manager Sites met Assets Insights nog steeds in de werkzaamheden plaatsvindt.

1. Aanmelden bij [https://dtm.adobe.com](https://dtm.adobe.com/)en selecteert u, naar gelang van het geval, een onderneming.
1. Een bestaande webeigenschap maken of openen

   * Selecteer de **[!UICONTROL Web Properties]** en klikt u op **[!UICONTROL Add Property]**.

   * Werk de velden naar wens bij en klik op **[!UICONTROL Create Property]**. Zie [documentatie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

   ![Webeigenschap bewerken maken](assets/Create-edit-web-property.png)

1. In de **[!UICONTROL Rules]** tab, selecteert u **[!UICONTROL Page Load Rules]** in het navigatievenster en klik op **[!UICONTROL Create New Rule]**.

   ![chlimage_1-58](assets/chlimage_1-194.png)

1. Uitbreiden **[!UICONTROL JavaScript /Third Party Tags]**. Klik vervolgens op **[!UICONTROL Add New Script]** in de **[!UICONTROL Sequential HTML]** om het dialoogvenster Script te openen.

   ![chlimage_1-59](assets/chlimage_1-195.png)

1. Klik op het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.
1. Klikken **[!UICONTROL Insights Page Tracker]**, kopieert u de trackercode en plakt u deze in het dialoogvenster Script dat u in stap 6 hebt geopend. Sla de wijzigingen op.

   >[!NOTE]
   >
   >* `AppMeasurement.js` wordt verwijderd. Naar verwachting is het beschikbaar via het Adobe Analytics-hulpprogramma van DTM.
   >* De oproep tot `assetAnalytics.dispatcher.init()` wordt verwijderd. De functie wordt naar verwachting aangeroepen zodra het Adobe Analytics-hulpprogramma van DTM is voltooid.
   >* Afhankelijk van de locatie waar Assets Insights Page Tracker wordt gehost (bijvoorbeeld Experience Manager, CDN, enzovoort), kan de oorsprong van de scriptbron wijzigingen vereisen.
   >* In het geval van door Experience Managers gehoste paginanummering, moet de bron verwijzen naar een publicatie-instantie met de hostnaam van de verzenderinstantie.

1. Toegang `https://dtm.adobe.com`. Klikken **[!UICONTROL Overview]** in de webeigenschap en klik op **[!UICONTROL Add Tool]** of open een bestaande Adobe Analytics Tool. Tijdens het maken van het gereedschap kunt u instellen **[!UICONTROL Configuration Method]** tot **[!UICONTROL Automatic]**.

   ![Gereedschap Adobe Analytics toevoegen](assets/Add-Adobe-Analytics-Tool.png)

   Selecteer de gewenste opties voor het rapport Staging/Productie.

1. Uitbreiden **[!UICONTROL Library Management]** en ervoor zorgen dat **[!UICONTROL Load Library at]** is ingesteld op **[!UICONTROL Page Top]**.

   ![chlimage_1-61](assets/chlimage_1-197.png)

1. Uitbreiden **[!UICONTROL Customize Page Code]** en klik op **[!UICONTROL Open Editor]**.

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
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, for example, 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, for example, 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, for example, 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, for example, 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
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
   * De codeaanroepen `assetAnalytics.dispatcher.init()` na te gaan of `_satellite.getToolsByType('sc')[0].getS()` is geïnitialiseerd en `assetAnalytics,dispatcher.init` is beschikbaar. Daarom kunt u overslaan toevoegend het in stap 11.
   * Zoals aangegeven in opmerkingen binnen de code voor Inzichten van paginanummers (**[!UICONTROL Tools > Assets > Insights Page Tracker]**), wanneer Paginanummer geen `AppMeasurement` -object, zijn de eerste drie argumenten (RSID, Tracking Server en Visitor Namespace) irrelevant. Lege tekenreeksen worden doorgegeven om dit te markeren.\
     De resterende argumenten komen overeen met wat is geconfigureerd in de pagina voor Inzichten configureren (**[!UICONTROL Tools > Assets > Insights Configuration]**).
   * Het object AppMeasurement wordt opgehaald door te zoeken `satelliteLib` voor alle beschikbare SiteCatalyst-motoren. Als er meerdere tags zijn geconfigureerd, wijzigt u de index van de arraykiezer op de juiste manier. Items in de array worden geordend volgens de gereedschappen voor SiteCatalysts die beschikbaar zijn in de DTM-interface.

1. Sla het venster Code-editor op, sluit dit en sla de wijzigingen vervolgens op in de configuratie van het gereedschap.
1. In de **[!UICONTROL Approvals]** , keurt beide goedkeuringen goed die in behandeling zijn. De tag DTM kan worden ingevoegd in uw webpagina.
