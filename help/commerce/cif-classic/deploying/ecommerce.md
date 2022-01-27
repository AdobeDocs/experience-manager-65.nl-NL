---
title: Overzicht eCommerce
seo-title: eCommerce Overview
description: AEM algemene eCommerce is beschikbaar als onderdeel van de standaardinstallatie en biedt u de volledige functionaliteit van het eCommerce-kader.
seo-description: AEM generic eCommerce is available as part of the standard installation and provides you with the full functionality of the eCommerce framework.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
docset: aem65
feature: Commerce Integration Framework
exl-id: 3567bd28-73aa-401a-8aa9-a62a99d2a613
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Overzicht eCommerce{#ecommerce-overview}

AEM algemene eCommerce is beschikbaar als onderdeel van een standaardinstallatie en biedt u de volledige functionaliteit van het eCommerce-kader.

Adobe verstrekt twee versies van het Kader van de Integratie van de Handel:

|  | CIF on prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Ondersteunde AEM | AEM on-prem of AMS 6.x | AEM AMS 6.4 en 6.5 |
| Terug | - AEM, Java <br> - Monolithische integratie, pre-build-toewijzing (sjabloon)<br> - JCR-opslagplaats | - Adobe Commerce <br>- Java en JavaScript <br>- Geen gegevens over handel opgeslagen in de gegevensopslagruimte van het GCO |
| Voorkant | Gerenderde pagina&#39;s AEM op de server | Toepassing gemengde pagina (hybride rendering) |
| Productcatalogus | - Producimporteur, redacteur, caching in AEM <br>- Gewone catalogi met AEM- of proxypagina&#39;s | - Geen producten importeren <br>- Algemene sjablonen <br>- Gegevens op aanvraag via connector |
| Schaalbaarheid | - Kan maximaal een paar miljoen producten ondersteunen (afhankelijk van het gebruiksgeval) <br> - Caching on Dispatcher | - Geen volumebeperking <br>- Caching op Dispatcher of CDN |
| Gestandaardiseerd gegevensmodel | Nee | Ja, Adobe Commerce GraphQL-schema |
| Beschikbaarheid | Ja:<br> - SAP Commerce Cloud (extensie die wordt bijgewerkt ter ondersteuning van AEM 6.4 en Hybris 5 (standaard) en die compatibel blijft met Hybris 4 <br>- Salesforce Commerce Cloud (connector open-sourced voor ondersteuning van AEM 6.4) | Ja via open bron via GitHub. <br> Adobe Commerce (ondersteunt 2.3.2 (standaard) en compatibel met 2.3.1). |
| Wanneer gebruiken | Beperkte gebruiksgevallen: Voor scenario&#39;s waarbij kleine, statische catalogi mogelijk moeten worden geïmporteerd | Voorkeursoplossing in de meeste gebruikscategorieën |


## Andere implementaties implementeren {#deploying-other-implementations}

Voor AEM en Adobe Commerce raadpleegt u [Integratie AEM en Adobe Commerce](/help/commerce/cif/integrating/magento.md) met de [Kader voor integratie in de handel](/help/commerce/cif/introduction.md).

>[!NOTE]
>
>Voor informatie over concepten en het beheren van eCommerce implementaties, zie [eCommerce beheren](/help/commerce/cif-classic/administering/ecommerce.md).
>
>Voor informatie over het uitbreiden van eCommerce-mogelijkheden raadpleegt u [Ontwikkeling van eCommerce](/help/commerce/cif-classic/developing/ecommerce.md).
