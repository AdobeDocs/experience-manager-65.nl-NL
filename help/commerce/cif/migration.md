---
title: Migratie naar de AEM Commerce Integration Framework (CIF)-invoegtoepassing
description: Hoe te om aan de AEM (CIF) toe:voegen-on van een oude versie te migreren.
exl-id: c6c0c2fc-6cfa-4c64-b3d8-7e428b2a4b2e
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Migratiehandleiding voor de invoegtoepassing Experience Manager {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de Experience Manager toe:voegen-op migratie moet bijwerken.

## CIF invoegtoepassing

CIF invoegtoepassing is beschikbaar voor AEM 6.5 via de [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en verstrekt de zelfde eigenschappen zoals CIF toe:voegen-aan voor as a Cloud Service Experience Manager.

Zie [Aan de slag met AEM Inhoud en Handel](getting-started.md).

Om projecten te steunen die CIF opstellen, verstrekt de Adobe [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components).

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet ondersteund door de CIF add-on. Gebruikend de CIF toe:voegen-op principes, zijn de product &amp; catalogusverzoeken via vraag in real time aan een externe handelsoplossing op bestelling. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [Magento open-source](https://business.adobe.com/products/magento/open-source.html).

## Ervaringen met AEM renderen in productcatalogus

Als u catalogusblauwdruk gebruikt in combinatie met klassieke CIF, moet u de workflow van de productcatalogus bijwerken. De CIF invoegtoepassing geeft nu direct ervaringen met productcatalogi weer met AEM catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Interactie voor gegevens en winkelen die niet in cache kunnen worden geplaatst

De cliënt-zijverzoeken voor niet cacheable gegevens en interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
