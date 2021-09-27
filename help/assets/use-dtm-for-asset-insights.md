---
title: Assets Insights inschakelen via DTM
description: Leer hoe u DTM (Adobe Dynamic Tag Management) gebruikt om Elementen in te schakelen.
contentOwner: AG
role: User, Admin
feature: Asset Insights,Asset Reports
exl-id: 80e8f84e-3235-4212-9dcd-6acdb9067893
source-git-commit: afc72fb6b324cf2e0ad8168f783d9c1a6f96c614
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# Assets Insights inschakelen via DTM {#enable-asset-insights-through-dtm}

Adobe Dynamisch tagbeheer is een programma waarmee u uw digitale marketingtools kunt activeren. Deze service wordt gratis aan Adobe Analytics-klanten aangeboden. U kunt de trackingcode aanpassen om CMS-oplossingen van derden in staat te stellen om Assets Insights te gebruiken, of u kunt DTM gebruiken om asset Insights-tags in te voegen. Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

>[!CAUTION]
>
>Adobe DTM is vervangen door [!DNL Adobe Experience Platform] en zal binnenkort [einde van levensduur](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f) bereiken. Adobe raadt u aan [gebruik [!DNL Adobe Experience Platform] voor elementinzichten](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html) te gebruiken.

Voer deze stappen uit om Elementeninzichten door DTM toe te laten.

1. Klik op het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Insights Configuration]**.
1. [Implementatie van Experience Managers configureren met DTM Cloud Service](/help/sites-administering/dtm.md)

   De API-token moet beschikbaar zijn wanneer u zich aanmeldt bij [https://dtm.adobe.com](https://dtm.adobe.com/) en **[!UICONTROL Account Settings]** bezoekt in het gebruikersprofiel. Deze stap is niet vereist vanuit het standpunt van Activa Insights, omdat de integratie van Experience Manager Sites met Assets Insights nog steeds in de werkzaamheden plaatsvindt.

1. Meld u aan bij [https://dtm.adobe.com](https://dtm.adobe.com/) en selecteer een bedrijf.
1. Een bestaande webeigenschap maken of openen

   * Selecteer de tab **[!UICONTROL Web Properties]** en klik op **[!UICONTROL Add Property]**.

   * Werk de velden naar wens bij en klik op **[!UICONTROL Create Property]**. Zie [documentatie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

   ![Webeigenschap bewerken maken](assets/Create-edit-web-property.png)

1. Selecteer op het tabblad **[!UICONTROL Rules]** **[!UICONTROL Page Load Rules]** in het navigatiegebied en klik op **[!UICONTROL Create New Rule]**.

   ![chlimage_1-58](assets/chlimage_1-194.png)

1. **[!UICONTROL JavaScript /Third Party Tags]** uitbreiden. Klik vervolgens op **[!UICONTROL Add New Script]** op het tabblad **[!UICONTROL Sequential HTML]** om het dialoogvenster Script te openen.

   ![chlimage_1-59](assets/chlimage_1-195.png)

1. Klik op het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.
1. Klik **[!UICONTROL Insights Page Tracker]**, kopieer de spoorcode, en kleef het dan in de dialoog van het Manuscript u in stap 6 opende. Sla de wijzigingen op.

   >[!NOTE]
   >
   >* `AppMeasurement.js` wordt verwijderd. Naar verwachting is het beschikbaar via het Adobe Analytics-hulpprogramma van DTM.
   >* De vraag aan `assetAnalytics.dispatcher.init()` wordt verwijderd. De functie wordt naar verwachting aangeroepen zodra het Adobe Analytics-hulpprogramma van DTM is voltooid.
   >* Afhankelijk van de locatie waar Assets Insights Page Tracker wordt gehost (bijvoorbeeld Experience Manager, CDN enzovoort), kan de oorsprong van de scriptbron wijzigingen vereisen.
   >* In het geval van door Experience Managers gehoste paginanummering, moet de bron verwijzen naar een publicatie-instantie met de hostnaam van de verzenderinstantie.


1. Ga naar `https://dtm.adobe.com`. Klik **[!UICONTROL Overview]** in het Web bezit en klik **[!UICONTROL Add Tool]** of open een bestaand Hulpmiddel van Adobe Analytics. Tijdens het maken van het gereedschap kunt u **[!UICONTROL Configuration Method]** instellen op **[!UICONTROL Automatic]**.

   ![Gereedschap Adobe Analytics toevoegen](assets/Add-Adobe-Analytics-Tool.png)

   Selecteer de gewenste opties voor het rapport Staging/Productie.

1. Vouw **[!UICONTROL Library Management]** uit en controleer of **[!UICONTROL Load Library at]** is ingesteld op **[!UICONTROL Page Top]**.

   ![chlimage_1-61](assets/chlimage_1-197.png)

1. Vouw **[!UICONTROL Customize Page Code]** uit en klik op **[!UICONTROL Open Editor]**.

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

   * De regel voor het laden van pagina&#39;s in DTM bevat alleen de code `pagetracker.js`. Alle `assetAnalytics`-velden worden beschouwd als overschrijvingen voor standaardwaarden. Deze zijn niet standaard vereist.
   * De code roept `assetAnalytics.dispatcher.init()` na ervoor te zorgen dat `_satellite.getToolsByType('sc')[0].getS()` wordt geïnitialiseerd en `assetAnalytics,dispatcher.init` beschikbaar is. Daarom kunt u overslaan toevoegend het in stap 11.
   * Zoals aangegeven in opmerkingen in de code voor Paginanummering met inzichten (**[!UICONTROL Tools > Assets > Insights Page Tracker]**), zijn de eerste drie argumenten (RSID, Tracking Server en Naamruimte bezoeker) irrelevant wanneer Paginanummering geen `AppMeasurement`-object maakt. Lege tekenreeksen worden doorgegeven om dit te markeren.\
      De resterende argumenten beantwoorden aan wat in de pagina van de Configuratie van Inzichten (**[!UICONTROL Tools > Assets > Insights Configuration]**) wordt gevormd.
   * Het object AppMeasurement wordt opgehaald door `satelliteLib` te vragen voor alle beschikbare SiteCatalyst engines. Als er meerdere tags zijn geconfigureerd, wijzigt u de index van de arraykiezer op de juiste manier. Items in de array worden geordend volgens de SiteCatalyst-gereedschappen die beschikbaar zijn in de DTM-interface.

1. Sla het venster Code-editor op, sluit dit en sla de wijzigingen vervolgens op in de configuratie van het gereedschap.
1. Goedkeuren beide goedkeuringen die in behandeling zijn op het tabblad **[!UICONTROL Approvals]**. De tag DTM kan worden ingevoegd in uw webpagina.
