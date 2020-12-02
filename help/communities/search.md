---
title: Zoekfunctie
seo-title: Zoekfunctie
description: Zoeken toevoegen en configureren aan een Community-site
seo-description: Zoeken toevoegen en configureren aan een Community-site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
translation-type: tm+mt
source-git-commit: 6ab91667ad668abf80ccf1710966169b3a187928
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---


# Zoekfunctie {#search-feature}

De zoekfunctie werkt met verschillende andere functies, zoals forums, om inhoud te kunnen zoeken.

Wanneer het toevoegen van de capaciteit aan onderzoeksposten ingegaan door communautaire leden, die als gebruiker geproduceerde inhoud (UGC) worden bedoeld, zijn er twee componenten: [Zoeken](#search) en [Zoekresultaten](#search-results).

De pagina met de component `Search Results` ondersteunt zowel het zoeken als het weergeven van resultaten.

De pagina die de `Search` component omvat verstrekt een plaats om een onderzoek met resultaten te lanceren die op `Search Results` pagina verschijnen.

De zoekfunctie kan worden gebruikt met elke andere functie waarmee bezoekers en leden van de site inhoud kunnen bekijken.

## Zoeken {#search-features}

### Zoekopdracht toevoegen aan een pagina {#add-search-to-a-page}

Als u een `Search`-component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om `Communities / Search` te zoeken en deze naar de juiste plaats op een pagina te slepen. Voor het gebruik van `Search` is een tweede pagina vereist voor `Search Results.`

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](basics.md).

Wanneer de vereiste bibliotheek aan de clientzijde, `cq.social.hbs.search`, wordt opgenomen, ziet de `Search` component er zo uit.

![add-search](assets/add-search.png)

### De toegevoegde zoekopdracht configureren {#configure-the-added-search}

Selecteer de geplaatste `Search` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![samenkomen](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Search Settings]** op hoe de paden worden doorzocht wanneer een query door een bezoeker wordt ingevoerd.

![zoekinstellingen](assets/search-settings.png)

* **[!UICONTROL Search Paths]**
Door zoekpaden toe te voegen met de knop Item toevoegen, is de zoekopdracht naar inhoud beperkt. Als voorbeeld, om het onderzoek tot een specifiek forum te beperken, selecteer een forumcomponent die binnen een pagina wordt geplaatst:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Result Page]**
De resultaten worden weergegeven op een aparte pagina die u in de browser hebt opgegeven om een pagina met de 
`Search Results` component.

## Zoekresultaten {#search-results}

### Zoekresultaten toevoegen aan een pagina {#add-search-results-to-a-page}

Als u een `Search Results`-component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Search Results`

en sleep het naar de juiste plaats op een pagina. In tegenstelling tot de zoekcomponent is geen tweede pagina nodig omdat de resultaten op dezelfde pagina worden weergegeven.

Als u Zoeken elders in de website gebruikt, kan deze ene pagina met `Search Results` worden geconfigureerd als `Result Page` voor een of alle exemplaren van `Search`.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](basics.md).

Wanneer de vereiste bibliotheek aan de clientzijde, `cq.social.hbs.search`, wordt opgenomen, ziet u zo de `Search Result` component:

![zoekresultaat](assets/search-result1.png)

### Het toegevoegde zoekresultaat configureren {#configure-the-added-search-result}

Selecteer de geplaatste `Search Results` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![vormen](assets/configure-new.png)

Onder **[!UICONTROL Search Result Settings]** tabel, is het mogelijk om te specificeren welke wegen in het onderzoek inbegrepen zijn wanneer een vraag door een bezoeker wordt ingegaan.

![search-result-settings](assets/search-result-settings.png)

* **[!UICONTROL Search Results Per Page]**

   Bepaal het aantal onderwerpen/posten dat per pagina wordt getoond. De standaardwaarde is 10.

* **[!UICONTROL Search Paths]**

   Door zoekpaden toe te voegen met de knop Item toevoegen, is de zoekopdracht naar inhoud beperkt.

## Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Doorzoekfuncties](search-implementation.md) voor ontwikkelaars.
