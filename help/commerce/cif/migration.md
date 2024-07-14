---
title: Migratie naar het AEM Commerce integration framework (CIF)
description: Hoe te om aan de AEM (CIF) toe:voegen-on van een oude versie te migreren.
exl-id: c6c0c2fc-6cfa-4c64-b3d8-7e428b2a4b2e
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Migratiehandleiding voor de invoegtoepassing Experience Manager {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de Experience Manager toe:voegen-op migratie moet bijwerken.

## CIF invoegtoepassing

CIF toe:voegen-op is beschikbaar voor AEM 6.5 via het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en verstrekt de zelfde eigenschappen zoals CIF toe:voegen-aan voor Experience Manager as a Cloud Service.

Zie [ Begonnen het worden met AEM Inhoud en Commerce ](getting-started.md).

Om projecten te steunen die CIF opstellen, verstrekt de Adobe [ AEM CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components).

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet ondersteund door de CIF add-on. Gebruikend de CIF toe:voegen-op principes, zijn de product &amp; catalogusverzoeken via vraag in real time aan een externe handelsoplossing op bestelling. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [ Magento open-source ](https://business.adobe.com/products/magento/open-source.html).

## Ervaringen met AEM renderen in productcatalogus

Als u catalogusblauwdruk gebruikt in combinatie met klassieke CIF, moet u de workflow van de productcatalogus bijwerken. De CIF invoegtoepassing geeft nu direct ervaringen met productcatalogi weer met AEM catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Interactie voor gegevens en winkelen die niet in cache kunnen worden geplaatst

De cliënt-zijverzoeken voor niet cacheable gegevens en de interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
