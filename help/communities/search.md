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

Wanneer het toevoegen van de capaciteit aan onderzoeksposten ingegaan door communautaire leden, die als gebruiker geproduceerde inhoud (UGC) worden bedoeld, zijn er twee componenten: [&#x200B; Onderzoek &#x200B;](#search) en [&#x200B; Resultaten van het Onderzoek &#x200B;](#search-results).

De pagina die de component `Search Results` bevat, ondersteunt zowel het zoeken als het weergeven van resultaten.

De pagina die de component `Search` bevat, biedt een plaats om een zoekopdracht te starten met resultaten die op de pagina `Search Results` worden weergegeven.

De zoekfunctie kan worden gebruikt met elke andere functie waarmee bezoekers en leden van de site inhoud kunnen bekijken.

## Zoeken {#search-features}

### Zoeken toevoegen aan een pagina {#add-search-to-a-page}

Als u een component `Search` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om `Communities / Search` te zoeken en naar de juiste plaats op een pagina te slepen. Voor het gebruik van `Search` is een tweede pagina vereist voor de `Search Results.`

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](basics.md).

Wanneer de vereiste bibliotheek aan de clientzijde, `cq.social.hbs.search`, wordt opgenomen, ziet u zo de `Search` -component.

![&#x200B; toe:voegen-onderzoek &#x200B;](assets/add-search.png)

### De toegevoegde zoekopdracht configureren {#configure-the-added-search}

Selecteer de geplaatste component `Search` die u wilt openen en selecteer het pictogram `Configure` waarmee het dialoogvenster Bewerken wordt geopend.

![&#x200B; confgirue &#x200B;](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Search Settings]** op hoe wordt gezocht in welke paden een query wordt ingevoerd door een bezoeker.

![&#x200B; onderzoek-montages &#x200B;](assets/search-settings.png)

* **[!UICONTROL Search Paths]**
Door zoekpaden toe te voegen met de knop Item toevoegen, is de zoekopdracht naar inhoud beperkt. Als voorbeeld, om het onderzoek tot een specifiek forum te beperken, selecteer een forumcomponent die binnen een pagina wordt geplaatst:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Result Page]**
De resultaten worden weergegeven op een aparte pagina die met de browser is opgegeven en die een pagina met de component `Search Results` bevat.

## Zoekresultaten {#search-results}

### Zoekresultaten toevoegen aan een pagina {#add-search-results-to-a-page}

Als u een component `Search Results` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Search Results`

en sleep het naar de juiste plaats op een pagina. In tegenstelling tot de zoekcomponent is geen tweede pagina nodig omdat de resultaten op dezelfde pagina worden weergegeven.

Als u Zoeken elders in de website gebruikt, is deze ene pagina met `Search Results` mogelijk geconfigureerd als de `Result Page` voor een of alle instanties van `Search` .

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](basics.md).

Wanneer de vereiste bibliotheek aan de clientzijde, `cq.social.hbs.search`, wordt opgenomen, ziet u zo de `Search Result` -component:

![&#x200B; onderzoek-resultaat &#x200B;](assets/search-result1.png)

### Het toegevoegde zoekresultaat configureren {#configure-the-added-search-result}

Selecteer de geplaatste component `Search Results` die u wilt openen en selecteer het pictogram `Configure` waarmee het dialoogvenster Bewerken wordt geopend.

![&#x200B; vormen &#x200B;](assets/configure-new.png)

Onder het tabblad **[!UICONTROL Search Result Settings]** kunt u opgeven welke paden in de zoekopdracht worden opgenomen wanneer een bezoeker een query invoert.

![&#x200B; onderzoek-resultaat-montages &#x200B;](assets/search-result-settings.png)

* **[!UICONTROL Search Results Per Page]**

  Bepaal het aantal onderwerpen/posten dat per pagina wordt getoond. De standaardwaarde is 10.

* **[!UICONTROL Search Paths]**

  Door zoekpaden toe te voegen met de knop Item toevoegen, is de zoekopdracht naar inhoud beperkt.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [&#x200B; Hoofdzaak van het Onderzoek &#x200B;](search-implementation.md) pagina voor ontwikkelaars worden gevonden.
