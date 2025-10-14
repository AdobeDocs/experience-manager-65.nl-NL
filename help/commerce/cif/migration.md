---
title: Migratie naar de invoegtoepassing AEM Commerce integration framework (CIF)
description: Migreren naar de AEM Commerce integration framework-invoegtoepassing (CIF) vanuit een oude versie.
exl-id: c6c0c2fc-6cfa-4c64-b3d8-7e428b2a4b2e
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: b4056a4c1483dc8dcedc3c0f8f6b42f8dead0847
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Migratiehandleiding voor de Experience Manager-invoegtoepassing {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de Experience Manager-add-on migratie moet bijwerken.

## CIF-invoegtoepassing

CIF toe:voegen-op is beschikbaar voor AEM 6.5 via het [&#x200B; portaal van de Distributie van de Software &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=commerce*&amp;2_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3Aversion&amp;2_group.propertyvalues.operation=equals&amp;2_group.propertyvalues.0_values=target-version%3Aem%2F6-5&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc layout=list&amp;p.offset=0&amp;p.limit=16). Het is compatibel en biedt dezelfde functies als de CIF-invoegtoepassing voor Experience Manager as a Cloud Service.

Zie [&#x200B; Begonnen het worden met de Inhoud van AEM en Commerce &#x200B;](getting-started.md).

Om projecten te steunen die CIF opstellen, verstrekt Adobe {de Componenten van de Kern van 0} AEM CIF [&#128279;](https://github.com/adobe/aem-core-cif-components).

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet ondersteund door de invoegtoepassing CIF. Gebruikend de toe:voegen-op principes van CIF, zijn de product &amp; catalogusverzoeken op bestelling via vraag in real time aan een externe handelsoplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [&#x200B; open-source van Magento &#x200B;](https://business.adobe.com/products/magento/open-source.html).

## Ervaringen met productcatalogus met AEM-rendering

Als u catalogusblauwdruk gebruikt met Classic CIF, moet u de workflow voor de productcatalogus bijwerken. De invoegtoepassing CIF geeft nu direct ervaringen met productcatalogi weer met AEM-catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Interactie voor gegevens en winkelen die niet in cache kunnen worden geplaatst

De cliënt-zijverzoeken voor niet cacheable gegevens en de interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
