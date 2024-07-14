---
title: Product Cockpit
description: Werken met productwakken die een verenigd overzicht van gekoppelde productcatalogi en bijbehorende inhoud bieden.
exl-id: 05ef2604-1d52-4397-a696-0b64717cc3cc
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Product Cockpit {#product-cockpit}

## Overzicht {#overview}

Het productpakket biedt een uniform overzicht van gekoppelde productcatalogi en de bijbehorende inhoud. Alle bijbehorende inhoud bevat koppelingen waarmee u deze snel vanuit de cockpit kunt openen.

De gefaseerde productgegevens omvatten om het even welke mutatie in de toekomst zoals nieuwe categorieën, producten, of bijgewerkte eigenschappen.

>[!NOTE]
>
>De term productcatalogus is uitwisselbaar met handels opslag, opslagmening, en gelijkaardige uitdrukkingen.

## Configuratie {#configuration}

Productcatalogi moeten in AEM worden geconfigureerd. Zie [ het vormen opslag en catalogi ](/help/commerce/cif/getting-started.md#catalog) voor meer informatie.

Voor het inschakelen van niet-gefaseerde catalogusfuncties is verificatie vereist. Zie [ Begonnen het Worden ](/help/commerce/cif/getting-started.md) voor meer informatie.

>[!NOTE]
>
>De gefaseerde cataloguseigenschappen zijn slechts beschikbaar met Adobe Commerce en derdeschakelaars die op teken-gebaseerde authentificatie steunen.

## De productcockpit openen {#opening-product-cockpit}

De eenvoudigste manier om toegang te krijgen tot de Product Cockpit is via het menu &#39;Commerce&#39; in AEM hoofdmenu. Het is ook mogelijk Omnsearch (search for Commerce) of open `https://<yourAEMInstance>/commerce.html` te gebruiken.

![ AEM menu ](/help/commerce/cif/assets/aem-menu.png)

## Bladeren door productcatalogi {#browsing-product-catalogs}

De productcockpit is hiërarchisch geordend volgens de structuur van de productcatalogus. Het eerste niveau toont het cataloguswortelniveau van alle gevormde productcatalogi met inbegrip van meta-informatie van de handels achterkant.

![ Gevormde catalogi ](/help/commerce/cif/assets/catalog-overview.png)

Als u op een categorie klikt, worden de onderliggende items van de categorie waarop u klikt, geladen.

![ kinderen van de Categorie ](/help/commerce/cif/assets/catalog-category-children.png)

Als u op een product klikt, worden productvariaties geladen, indien beschikbaar.

![ de variaties van het Product ](/help/commerce/cif/assets/catalog-product-variation.png)

>[!NOTE]
>
>De catalogusgegevens van het product in AEM zijn gegevens die in echt - tijd via het gevormde handelseindpunt worden teruggewonnen. Er worden geen productcatalogusgegevens opgeslagen in AEM.

## Productcatalogi zoeken {#searching-product-catalog}

In het linkerfiltertabblad vindt u een zoekopdracht in volledige tekst over de volledige productcatalogus om snel producten te zoeken.

![ onderzoek ](/help/commerce/cif/assets/search-cockpit.png)

## Bladeren door gefaseerde productcatalogus {#staged-product-catalogs}

Standaard worden in de productcockpit de catalogusgegevens van het live product weergegeven. Met de &quot;STAGED CATALOG&quot; in het linkerfiltertabblad wordt de productcatalogus voor een geselecteerde datum geladen.

![ gefaseerde catalogus ](/help/commerce/cif/assets/staged-cockpit.png)

## Eigenschappen van productcatalogus {#catalog-properties}

Als u op het eigenschappenpictogram van een product of categorie klikt, wordt de eigenschappenweergave van het geselecteerde object geopend. De open eigenschappen van een productvariant zijn gelijk aan het openen van de belangrijkste producteigenschappen.

### Commerce Tabs {#tabs}

De algemene en variantlusjes tonen vooraf bepaalde handelseigenschappen die uit de handelskorend achterste komen. Deze gegevens (inclusief varianten) is read-only gegevens in AEM aangezien het systeem van verslag de handelsafstand is. Het tabblad Variant wordt alleen weergegeven voor producten met varianten en bevat een lijst met alle varianten.

![ cataloguseigenschappen ](/help/commerce/cif/assets/catalog-properties.png)

### Tabs Inhoud AEM {#content-tabs}

Op deze tabbladen, gegroepeerd op AEM inhoudstypen (Experience Fragments, Content Fragments, Associated Assets), wordt AEM inhoud weergegeven die aan het commerceobject is gekoppeld. Met de handeling Details weergeven wordt een nieuw browsertabblad met de geselecteerde inhoud geopend.

![ inhoudseigenschappen ](/help/commerce/cif/assets/content-properties.png)
