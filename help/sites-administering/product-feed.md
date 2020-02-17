---
title: Productfeed
seo-title: Productfeed
description: Meer informatie over de AEM-productfeed.
seo-description: Meer informatie over de AEM-productfeed.
uuid: 99eb9bdc-2717-45d4-9203-6394b7d7ddc6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 1f920892-c52e-42ca-900c-2c7ab3c503b3
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# Productfeed {#product-feed}

AEM integreert met [zoek&amp;promoten](https://www.adobe.com/solutions/testing-targeting/searchandpromote.html) en biedt de volgende mogelijkheden:

* gebruik de eCommerce-API, onafhankelijk van de onderliggende structuur van de gegevensopslagruimte en het handelsplatform.
* hefboomwerking de eigenschap van de Schakelaar van de Index van Onderzoek&amp;Promote om een productvoer in formaat van XML te verstrekken.
* hefboomwerking de Verre eigenschap van Controle van Onderzoek&amp;Promote om op bestelling of geplande verzoeken van de productvoer uit te voeren
* feed-generatie voor verschillende zoek&amp;Promote accounts, geconfigureerd als configuraties met cloudservices.

U moet een geldig account hebben en de verbinding [configureren om te zoeken en te promoten](/help/sites-administering/search-and-promote.md#configuring-the-connection-to-search-promote). U moet ook verifiëren dat u het correcte [gegevenscentrum](/help/sites-administering/search-and-promote.md#configuring-the-data-center) gebruikt en ervoor zorgen dat **Verre server URI **wordt gevormd.

## De productfeed instellen {#set-up-the-product-feed}

U moet eerst een hoofdmap van de website en een id-kenmerk invoeren. Dit doet u als volgt:

1. Navigeer naar uw zoek&amp;promoconfiguratie.
1. Click **[!UICONTROL Edit]**.
1. Klik op het tabblad Configuratie **[!UICONTROL van feed-]** indexaansluiting.
1. Voer de hoofdmap **[!UICONTROL en het kenmerk]** **[!UICONTROL Id van de]** website in.

   >[!NOTE]
   >
   >De hoofdmap **[!UICONTROL van de]** website eCommerce is bijvoorbeeld de basis van uw website `/content/geometrixx-outdoors/en`.
   >
   >Het kenmerk **[!UICONTROL Identifier]** is een JCR-eigenschap die het product op unieke wijze identificeert: `identifier`.

1. Click **[!UICONTROL OK]**.

Vervolgens moet u ook twee configuraties in de webconsole bewerken voordat u productfeeds kunt genereren.

### De dag-CQ-zoekfunctie configureren en de implementatie van Producten crawler voor Geometrixx bevorderen {#configuring-the-day-cq-search-promote-products-crawler-implementation-for-geometrixx}

1. Ga naar [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Klik op **[!UICONTROL Dag CQ om producten te doorzoeken en de implementatie van Geometrixx]** te bevorderen.
1. Geef het accountnummer op waarnaar deze kruipler wordt gekoppeld. Het zal worden gebruikt om omhoog de configuratie van de wolkendiensten te kijken die door deze kruipper wordt gebruikt.
1. Click **[!UICONTROL Save]**.

### De dag-CQ-zoekfunctie configureren en producten in feed-Generator voor Geometrixx promoten {#configuring-the-day-cq-search-promote-products-feed-generator-for-geometrixx}

1. Ga naar [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Klik op **[!UICONTROL CQ-zoekopdracht&amp;Productfeed-generator voor Geometrixx]** opwaarderen.
1. Geef het account-nummer op waarnaar deze generator is gekoppeld. Het zal worden gebruikt om de configuratie van de wolkendiensten op te zoeken die door deze generator wordt gebruikt.
1. Click **[!UICONTROL Save]**.

## De productfeed plannen {#schedule-the-product-feed}

Om geplande voedergeneratie toe te laten, moet u een planner voor het vormen.
Een planner wordt gevormd als kindconfiguratie van uw specifieke zoek&amp;promote de configuratie van de wolkendiensten.

1. Navigeer naar uw zoek&amp;promoconfiguratie.
1. Klik **[!UICONTROL +]** naast de configuratie **[!UICONTROL van de]** Planner.
1. Voer een **[!UICONTROL titel]** in die herkenbaar is voor auteurs van een pagina en een unieke **[!UICONTROL naam]**.
1. Klik op **[!UICONTROL Maken]**. Er wordt een dialoogvenster geopend.

   ![chlimage_1-108](assets/chlimage_1-108a.png)

1. Voer het wachtwoord voor **[!UICONTROL afstandsbediening]** in. Dit is het wachtwoord dat u in uw zoek&amp;Pronotaccount hebt geconfigureerd.

   >[!NOTE]
   >
   >Dit is niet het wachtwoord voor uw account voor zoeken en promoten. U kunt dit wachtwoord vinden en wijzigen door u aan te melden bij uw account Zoeken&amp;Promoten en naar **[!UICONTROL Index]** en vervolgens naar de **[!UICONTROL afstandsbediening]** te gaan.

1. Schakel het selectievakje **[!UICONTROL Tijdschema]** inschakelen in.
1. Selecteer een **[!UICONTROL schema]**. Het is het eigenlijke schema voor de productie van diervoeders.
1. Schakel de indexering op **[!UICONTROL aanvraag]** in. Deze functie wordt gebruikt om de index voor zoeken en bevorderen handmatig aan te roepen. Als volledige **[!UICONTROL productfeed]** aanvragen is ingeschakeld, vraagt Search&amp;Promote om een volledige productfeed. Anders wordt een basisproductfeed aangevraagd.

   >[!NOTE]
   >
   >De indexerende eigenschap op bestelling maakt gebruik van de eigenschap van de Controle van de Verre van Onderzoek &amp; bevorderen. Wanneer een externe indexering wordt aangeroepen, wordt de indexering niet onmiddellijk gestart, maar wordt een indexeringsaanvraag naar Zoeken&amp;Promoten gepost met de functie voor afstandsbediening.

1. Click **[!UICONTROL OK]**.

Nu u alles hebt geconfigureerd, kunt u een XML-pagina met alle producten onder de geconfigureerde hoofdmap van de website zien: [http://localhost:4502/etc/commerce/searchpromote/feed/full](http://localhost:4502/etc/commerce/searchpromote/feed/full).
