---
title: Overzicht eCommerce
seo-title: Overzicht eCommerce
description: De algemene eCommerce van AEM is beschikbaar als deel van de standaardinstallatie en voorziet u van de volledige functionaliteit van het kader van de eCommerce.
seo-description: De algemene eCommerce van AEM is beschikbaar als deel van de standaardinstallatie en voorziet u van de volledige functionaliteit van het kader van de eCommerce.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
docset: aem65
translation-type: tm+mt
source-git-commit: 5d46836a8b7b66daa8f27bc6fad14319ab1f58a7

---


# Overzicht eCommerce{#ecommerce-overview}

De algemene eCommerce van AEM is beschikbaar als deel van een standaardinstallatie en voorziet u van de volledige functionaliteit van het kader van de eCommerce.

Adobe biedt twee versies van het Commerce Integration Framework:

|  | CIF on prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Ondersteunde AEM-versies | AEM on-prem of AMS 6.x | AEM AMS 6.4 en 6.5 |
| Terug | - AEM, Java <br> - Monolithische integratie, pre-build mapping (sjabloon)<br> - JCR-opslagplaats | - Magento <br>- Java en Javascript <br>- Geen gegevens van de Handel opgeslagen in de gegevensopslagplaats van JCR |
| Voorkant | Gerenderde pagina&#39;s op de AEM-server | Toepassing gemengde pagina (hybride rendering) |
| Productcatalogus | - Producimporteur, editor, caching in AEM <br>- Reguliere catalogi met AEM- of proxypagina&#39;s | - Geen product importeren <br>- Algemene sjablonen <br>- Gegevens op aanvraag via connector |
| Schaalbaarheid | - Kan maximaal een paar miljoen producten ondersteunen (afhankelijk van het gebruiksgeval) <br> - Caching op Dispatcher | - Geen volumebeperking <br>- Caching op Dispatcher of CDN |
| Gestandaardiseerd gegevensmodel | Nee | Ja, Magento GraphQL-schema |
| Beschikbaarheid | <br> Ja: - SAP Commerce Cloud (extensie die is bijgewerkt ter ondersteuning van AEM 6.4 en Hybris 5 (standaard) en compatibel blijft met Hybris 4 <br>- Salesforce Commerce Cloud (open-sourced voor aansluiting ter ondersteuning van AEM 6.4) | Ja via open bron via GitHub. <br> De Handel van Magento (Steunt Magento 2.3.2 (gebrek) en compatibel met Magento 2.3.1). |
| Wanneer gebruiken | Beperkte gebruiksgevallen: Voor scenario&#39;s waarbij kleine, statische catalogi mogelijk moeten worden geïmporteerd | Voorkeursoplossing in de meeste gebruikscategorieën |


## Andere implementaties implementeren {#deploying-other-implementations}

Voor AEM en Magento, gelieve te zien [AEM en Magento integratie](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md) gebruikend het Kader [van de Integratie van de](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html)Handel.

>[!NOTE]
>
>Voor informatie over concepten en het beheren van eCommerce implementaties, zie [het Beheer eCommerce](/help/sites-administering/ecommerce.md).
>
>Voor informatie over het uitbreiden van eCommerce-mogelijkheden, zie het [Ontwikkelen van eCommerce](/help/sites-developing/ecommerce.md).

