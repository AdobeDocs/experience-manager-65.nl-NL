---
title: Overzicht eCommerce
description: AEM algemene eCommerce is beschikbaar als onderdeel van de standaardinstallatie en biedt u de volledige functionaliteit van het eCommerce-kader.
feature: Commerce Integration Framework
exl-id: 3567bd28-73aa-401a-8aa9-a62a99d2a613
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Overzicht eCommerce{#ecommerce-overview}

AEM algemene eCommerce is beschikbaar als onderdeel van een standaardinstallatie en biedt u de volledige functionaliteit van het eCommerce-kader.

Adobe biedt twee versies van het Commerce integration framework:

|                         | CIF op prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Ondersteunde AEM | AEM on-prem of AMS 6.x | AEM AMS 6.4 en 6.5 |
| Terug | - AEM, Java™ <br> - Monolithische integratie, pre-build-toewijzing (sjabloon)<br> - JCR-opslagplaats | - ADOBE COMMERCE <br>- Java en JavaScript <br>- Geen gegevens over handel opgeslagen in de gegevensopslagruimte van het GCO |
| Voorkant | Gerenderde pagina&#39;s AEM op de server | Toepassing gemengde pagina (hybride rendering) |
| Productcatalogus | - Producimporteur, redacteur, caching in AEM <br>- Gewone catalogi met AEM- of proxypagina&#39;s | - Geen producten importeren <br>- Algemene sjablonen <br>- Gegevens op aanvraag via connector |
| Schaalbaarheid | - Kan maximaal een paar miljoen producten ondersteunen (afhankelijk van het gebruiksgeval) <br> - Caching on Dispatcher | - Geen volumebeperking <br>- Caching op Dispatcher of CDN |
| Gestandaardiseerd gegevensmodel | Nee | Ja, Adobe Commerce GraphQL-schema |
| Beschikbaarheid | Ja:<br> - SAP-Commerce Cloud (extensie die wordt bijgewerkt ter ondersteuning van AEM 6.4 en Hybris 5 (standaard) en de compatibiliteit met Hybris 4 <br>- Salesforce-Commerce Cloud (connector open-sourced voor ondersteuning van AEM 6.4) | Ja via open bron via GitHub. <br> Adobe Commerce (ondersteunt 2.3.2 (standaard) en compatibel met 2.3.1). |
| Wanneer gebruiken | Beperkt gebruik: indien nodig statische catalogi importeren voor scenario&#39;s met een klein formaat | Voorkeursoplossing in de meeste gebruikscategorieën |


## Andere implementaties implementeren {#deploying-other-implementations}

Voor AEM en Adobe Commerce raadpleegt u [Integratie AEM en Adobe Commerce](/help/commerce/cif/integrating/magento.md) met de [Commerce integration framework](/help/commerce/cif/introduction.md).

>[!NOTE]
>
>Voor informatie over concepten en het beheren van eCommerce implementaties, zie [eCommerce beheren](/help/commerce/cif-classic/administering/ecommerce.md).
>
>Voor informatie over het uitbreiden van eCommerce-mogelijkheden raadpleegt u [Ontwikkeling van eCommerce](/help/commerce/cif-classic/developing/ecommerce.md).
