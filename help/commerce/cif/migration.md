---
title: Migratie naar de AEM Commerce Integration Framework (CIF)-invoegtoepassing
description: Hoe te om aan het AEM Kader van de Integratie van de Handel (CIF) toe:voegen-on van een oude versie te migreren
translation-type: tm+mt
source-git-commit: d92a635d41cf1b14e109c316bd7264cf7d45a9fe
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Migratiehandleiding voor de invoegtoepassing Experience Manager {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de Experience Manager toe:voegen-op migratie moet bijwerken.

## CIF-invoegtoepassing

De toe:voegen-on CIF is beschikbaar voor AEM 6.5 via [het portaal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en verstrekt de zelfde eigenschappen zoals de toe:voegen-on CIF voor Experience Manager als Cloud Service.

Zie [Aan de slag met AEM Inhoud en Handel](getting-started.md).

Om projecten te steunen die CIF Adobe opstellen verstrekken [AEM de Componenten van de Kern van CIF](https://github.com/adobe/aem-core-cif-components).

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet ondersteund door de CIF-invoegtoepassing. Gebruikend de toe:voegen-op principes CIF, product &amp; catalogusverzoeken zijn op bestelling via vraag in real time aan een externe handeloplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [Magento open-source](https://magento.com/products/magento-open-source).

## De catalogus van het product ervaart met AEM teruggeven

Als u catalogusblauwdruk gebruikt met Klassieke CIF, moet u de workflow van de productcatalogus bijwerken. De CIF-invoegtoepassing geeft productcataloguservaringen nu direct weer met behulp van AEM catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Niet-cacheable gegevens en winkelinteractie

De cliënt-zijverzoeken voor niet cacheable gegevens en interactie (b.v. toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
