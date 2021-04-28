---
title: Migratie naar de AEM Commerce Integration Framework (CIF)-invoegtoepassing
description: Hoe te om aan het AEM Kader van de Integratie van de Handel (CIF) toe:voegen-on van een oude versie te migreren
translation-type: tm+mt
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# De Gids van de migratie voor de Experience Manager toe:voegen-aan {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de Experience Manager toe:voegen-op migratie moet bijwerken.

## CIF-invoegtoepassing

De toe:voegen-on CIF is beschikbaar voor AEM 6.5 via [het portaal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en verstrekt de zelfde eigenschappen zoals de toe:voegen-on CIF voor Experience Manager als Cloud Service.

Zie [Aan de slag met AEM Inhoud en Handel](getting-started.md).

Om projecten te steunen die CIF opstellen, verstrekt Adobe [AEM de Componenten van de Kern van CIF](https://github.com/adobe/aem-core-cif-components).

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet ondersteund door de CIF-invoegtoepassing. Gebruikend de toe:voegen-op principes CIF, product &amp; catalogusverzoeken zijn op bestelling via vraag in real time aan een externe handeloplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [Magento open-source](https://magento.com/products/magento-open-source).

## Ervaringen met AEM renderen in productcatalogus

Als u catalogusblauwdruk gebruikt met Klassieke CIF, moet u de workflow van de productcatalogus bijwerken. De CIF-invoegtoepassing geeft productcataloguservaringen nu direct weer met behulp van AEM catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Interactie voor gegevens en winkelen die niet in cache kunnen worden geplaatst

De cliënt-zijverzoeken voor niet cacheable gegevens en de interactie (bijvoorbeeld toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
