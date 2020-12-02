---
title: Productfeed
seo-title: Productfeed
description: Meer informatie over de AEM Productfeed.
seo-description: Meer informatie over de AEM Productfeed.
uuid: 99eb9bdc-2717-45d4-9203-6394b7d7ddc6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 1f920892-c52e-42ca-900c-2c7ab3c503b3
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 1%

---


# Productfeed {#product-feed}

AEM integreert met [Search&amp;Promote](https://www.adobe.com/solutions/testing-targeting/searchandpromote.html) en staat u toe:

* gebruik de eCommerce-API, onafhankelijk van de onderliggende structuur van de gegevensopslagruimte en het handelsplatform.
* hefboomwerking de eigenschap van de Schakelaar van de Index van Search&amp;Promote om een productvoer in formaat van XML te verstrekken.
* de functie voor afstandsbediening van Search&amp;Promote gebruiken om op aanvraag of geplande aanvragen van de productfeed uit te voeren
* feed generation voor verschillende Search&amp;Promote-accounts, geconfigureerd als cloudservices configuraties.

U moet een geldig account hebben en de verbinding met Search&amp;Promote[ configureren. ](/help/sites-administering/search-and-promote.md#configuring-the-connection-to-search-promote) U moet ook verifiëren dat u correcte [gegevenscentrum](/help/sites-administering/search-and-promote.md#configuring-the-data-center) gebruikt en ervoor zorgen dat **Verre server URI **wordt gevormd.

## De productfeed {#set-up-the-product-feed} instellen

U moet eerst een hoofdmap van de website en een id-kenmerk invoeren. Dit doet u als volgt:

1. Navigeer naar de configuratie van de Search&amp;Promote.
1. Klik op **[!UICONTROL Edit]**.
1. Klik op het tabblad **[!UICONTROL Index Connector Feed Configuration]**.
1. Voer de **[!UICONTROL Web site root]** en **[!UICONTROL Identifier attribute]** in.

   >[!NOTE]
   >
   >De **[!UICONTROL Web site root]** is de basis van uw eCommerce-website, bijvoorbeeld `/content/geometrixx-outdoors/en`.
   >
   >De eigenschap **[!UICONTROL Identifier attribute]** is een JCR-eigenschap die het product op unieke wijze identificeert: `identifier`.

1. Klik op **[!UICONTROL OK]**.

Vervolgens moet u ook twee configuraties in de webconsole bewerken voordat u productfeeds kunt genereren.

### Het vormen van de de Producten Crawler van de Producten van de Dag CQ voor Geometrixx {#configuring-the-day-cq-search-promote-products-crawler-implementation-for-geometrixx}

1. Navigeer naar [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Klik op **[!UICONTROL Day CQ Search&Promote products crawler implementation for Geometrixx]**.
1. Geef het rekeningnummer op van de Search&amp;Promote waarmee deze kruipper is gekoppeld. Het zal worden gebruikt om omhoog de configuratie van de wolkendiensten te kijken die door deze kruipper wordt gebruikt.
1. Klik op **[!UICONTROL Save]**.

### Het vormen van de Dag CQ de Producenten van de Diervoeders van de Search&amp;Promote voor Geometrixx {#configuring-the-day-cq-search-promote-products-feed-generator-for-geometrixx}

1. Navigeer naar [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Klik op **[!UICONTROL Day CQ Search&Promote products feed generator for Geometrixx]**.
1. Geef het rekeningnummer op van de Search&amp;Promote waarmee deze generator is gekoppeld. Het zal worden gebruikt om de configuratie van de wolkendiensten op te zoeken die door deze generator wordt gebruikt.
1. Klik op **[!UICONTROL Save]**.

## De productfeed {#schedule-the-product-feed} plannen

Om geplande voedergeneratie toe te laten, moet u een planner voor het vormen.
Een planner wordt gevormd als kindconfiguratie van uw specifieke de dienstenconfiguratie van de wolk van de Search&amp;Promote.

1. Navigeer naar de configuratie van de Search&amp;Promote.
1. Klik **[!UICONTROL +]** naast **[!UICONTROL Scheduler configuration]**.
1. Voer een **[!UICONTROL Title]** in die herkenbaar is voor auteurs van pagina&#39;s en een unieke **[!UICONTROL Name]**.
1. Klik op **[!UICONTROL Create]**. Er wordt een dialoogvenster geopend.

   ![chlimage_1-108](assets/chlimage_1-108a.png)

1. Voer de **[!UICONTROL Remote Control Password]** in. Dit is het wachtwoord dat u in uw zoek&amp;Pronotaccount hebt geconfigureerd.

   >[!NOTE]
   >
   >Dit is niet het wachtwoord voor uw Search&amp;Promote-account. U kunt dit wachtwoord vinden en wijzigen door u aan te melden bij uw Search&amp;Promote-account en naar **[!UICONTROL Index]** en **[!UICONTROL Remote control]** te gaan.

1. Schakel **[!UICONTROL Enable schedule]** in.
1. Selecteer een **[!UICONTROL Schedule]**. Het is het eigenlijke schema voor de productie van diervoeders.
1. Schakel **[!UICONTROL On-demand indexing]** in of niet. Deze functie wordt gebruikt om de index van de Search&amp;Promote handmatig aan te roepen. Als **[!UICONTROL Request full products feed]** wordt gecontroleerd, zal Search&amp;Promote om een volledige productvoer verzoeken. Anders wordt een basisproductfeed aangevraagd.

   >[!NOTE]
   >
   >De indexerende eigenschap op bestelling maakt gebruik van de eigenschap van de Verre Controle van Search&amp;Promote. Wanneer een verre indexering wordt geroepen, zal het indexeren niet onmiddellijk beginnen, maar een indexerend verzoek zal aan Search&amp;Promote worden gepost gebruikend de eigenschap van de afstandsbediening.

1. Klik op **[!UICONTROL OK]**.

Nu u alles hebt geconfigureerd, kunt u een XML-pagina met alle producten onder de geconfigureerde hoofdmap van de website zien: [http://localhost:4502/etc/commerce/searchpromote/feed/full](http://localhost:4502/etc/commerce/searchpromote/feed/full).
