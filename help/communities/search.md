---
title: Zoekfunctie
description: Zoeken toevoegen en configureren aan een Community-site
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: e252b0e5-a2f8-468e-ac8c-951a5b0f2e32
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Zoekfunctie {#search-feature}

De zoekfunctie werkt met verschillende andere functies, zoals forums, om inhoud te kunnen zoeken.

Wanneer het toevoegen van de capaciteit aan onderzoeksposten ingegaan door communautaire leden, die als gebruiker geproduceerde inhoud (UGC) worden bedoeld, zijn er twee componenten: [Zoeken](#search) en [Zoekresultaten](#search-results).

De pagina die de `Search Results` ondersteunt zowel het zoeken als de weergave van resultaten.

De pagina die de `Search` biedt een plaats om een zoekopdracht te starten met de resultaten die worden weergegeven op het tabblad `Search Results` pagina.

De zoekfunctie kan worden gebruikt met elke andere functie waarmee bezoekers en leden van de site inhoud kunnen bekijken.

## Zoeken {#search-features}

### Zoeken toevoegen aan een pagina {#add-search-to-a-page}

Als u een `Search` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van `Communities / Search` en sleep het naar de juiste plaats op een pagina. Gebruik van `Search` vereist een tweede pagina voor de `Search Results.`

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](basics.md).

Wanneer de vereiste clientbibliotheek `cq.social.hbs.search`, wordt opgenomen, is dit hoe `Search` wordt weergegeven.

![add-search](assets/add-search.png)

### De toegevoegde zoekopdracht configureren {#configure-the-added-search}

Selecteer de geplaatste `Search` te openen en te selecteren `Configure` wordt het dialoogvenster Bewerken geopend.

![samenkomen](assets/configure-new.png)

Onder de **[!UICONTROL Search Settings]** , geeft u op hoe wordt gezocht in welke paden een query wordt ingevoerd door een bezoeker.

![zoekinstellingen](assets/search-settings.png)

* **[!UICONTROL Search Paths]**
Door zoekpaden toe te voegen met de knop Item toevoegen, is de zoekopdracht naar inhoud beperkt. Als voorbeeld, om het onderzoek tot een specifiek forum te beperken, selecteer een forumcomponent die binnen een pagina wordt geplaatst:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Result Page]**
De resultaten worden weergegeven op een aparte pagina die u in de browser hebt opgegeven om een pagina te selecteren die de `Search Results` component.

## Zoekresultaten {#search-results}

### Zoekresultaten toevoegen aan een pagina {#add-search-results-to-a-page}

Als u een `Search Results` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Search Results`

en sleep het naar de juiste plaats op een pagina. In tegenstelling tot de zoekcomponent is geen tweede pagina nodig omdat de resultaten op dezelfde pagina worden weergegeven.

Als u Zoeken elders op de website gebruikt, wordt deze pagina geleverd met `Search Results` kan worden geconfigureerd als `Result Page` voor een of alle gevallen `Search`.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](basics.md).

Wanneer de vereiste clientbibliotheek `cq.social.hbs.search`, wordt opgenomen, is dit hoe `Search Result` wordt weergegeven:

![zoekresultaat](assets/search-result1.png)

### Het toegevoegde zoekresultaat configureren {#configure-the-added-search-result}

Selecteer de geplaatste `Search Results` te openen en te selecteren `Configure` wordt het dialoogvenster Bewerken geopend.

![vormen](assets/configure-new.png)

Onder de **[!UICONTROL Search Result Settings]** kunt u opgeven welke paden in de zoekopdracht moeten worden opgenomen wanneer een bezoeker een query invoert.

![search-result-settings](assets/search-result-settings.png)

* **[!UICONTROL Search Results Per Page]**

  Bepaal het aantal onderwerpen/posten dat per pagina wordt getoond. De standaardwaarde is 10.

* **[!UICONTROL Search Paths]**

  Door zoekpaden toe te voegen met de knop Item toevoegen, is de zoekopdracht naar inhoud beperkt.

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële zoekopdrachten](search-implementation.md) pagina voor ontwikkelaars.
