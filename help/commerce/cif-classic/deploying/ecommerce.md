---
title: Overzicht eCommerce
description: AEM algemene eCommerce is beschikbaar als onderdeel van de standaardinstallatie en biedt u de volledige functionaliteit van het eCommerce-kader.
feature: Commerce Integration Framework
exl-id: 3567bd28-73aa-401a-8aa9-a62a99d2a613
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
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
| Terug | - AEM, Java™ <br> - Monolithische integratie, pre-bouwstijltoewijzing (malplaatje) <br> - bewaarplaats JCR | - Adobe Commerce <br> - Java en JavaScript <br> - Geen Commerce-gegevens opgeslagen in de JCR-opslagplaats |
| Voorkant | Gerenderde pagina&#39;s AEM op de server | Toepassing gemengde pagina (hybride rendering) |
| Productcatalogus | - Producimporteur, editor, caching in AEM <br> - Normale catalogi met AEM- of proxypagina&#39;s | - Geen product importeren <br> - Algemene sjablonen <br> - Gegevens op aanvraag via connector |
| Schaalbaarheid | - Kan maximaal een paar miljoen producten ondersteunen (afhankelijk van het gebruik) <br> - Caching op Dispatcher | - Geen volumebeperking <br> - Caching op Dispatcher of CDN |
| Gestandaardiseerd gegevensmodel | Nee | Ja, Adobe Commerce GraphQL-schema |
| Beschikbaarheid | Ja:<br> - de Commerce Cloud van SAP (Uitbreiding bijgewerkt om AEM 6.4 en Hybris 5 (gebrek) te steunen en handhaaft verenigbaarheid met Hybris 4 <br> - Commerce Cloud Salesforce (Verbinding open-sourced om AEM 6.4 te steunen) | Ja via open bron via GitHub. <br> Adobe Commerce (ondersteunt 2.3.2 (standaard) en compatibel met 2.3.1). |
| Wanneer gebruiken | Beperkt gebruik: indien nodig statische catalogi importeren voor scenario&#39;s met een klein formaat | Voorkeursoplossing in de meeste gebruikscategorieën |


## Andere implementaties implementeren {#deploying-other-implementations}

Voor AEM en Adobe Commerce, zie [ AEM en de integratie van Adobe Commerce ](/help/commerce/cif/integrating/magento.md) gebruikend het [ Commerce integration framework ](/help/commerce/cif/introduction.md).

>[!NOTE]
>
>Voor informatie over concepten en het beheren van eCommerce implementaties, zie [ Administering eCommerce ](/help/commerce/cif-classic/administering/ecommerce.md).
>
>Voor informatie over het uitbreiden van eCommerce mogelijkheden, zie [ Ontwikkelend eCommerce ](/help/commerce/cif-classic/developing/ecommerce.md).
