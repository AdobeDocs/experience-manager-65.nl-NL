---
title: Sociale grafiek gebruiken
seo-title: Sociale grafiek gebruiken
description: Een volgende component aan een pagina toevoegen
seo-description: Een volgende component aan een pagina toevoegen
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
translation-type: tm+mt
source-git-commit: 3296db289b2e2f4ca0d1981597ada6ca1310bd46

---


# Sociale grafiek gebruiken {#using-social-graph}

## Inleiding {#introduction}

De mogelijkheid voor een lid van de gemeenschap om zowel [activiteiten](activities.md) als follow-up te volgen, wordt door middel van twee componenten vastgesteld: `Follow` en `Following`.

De `Follow` component moet met een andere bron worden geassocieerd, en deze vereniging is reeds gevestigd voor communautaire leden en eigenschappen.

De `Following` component maakt een lijst eenvoudig van de leden die of het huidige lid volgen of door het huidige lid worden gevolgd. Deze sociale grafiek van de relaties tussen leden is opgenomen in het gebruikersprofiel dat voor een [gemeenschapssite](overview.md#communitiessites)is ingesteld.

## Volgende toevoegen aan een pagina {#adding-following-to-a-page}

Als u een `Following` component wilt toevoegen aan een pagina in de ontwerpmodus, zoekt u de component `Communities / Following` en sleept u deze naar de plaats op een pagina waar de sociale grafiek moet verschijnen.

Ga voor de benodigde informatie naar [Community Components Basics](basics.md).

Wanneer de [vereiste client-side bibliotheken](essentials-socialgraph.md#essentials-for-client-side) worden opgenomen, wordt de `Following` component als volgt weergegeven:

![chlimage_1-447](assets/chlimage_1-447.png)

## Configureren na {#configuring-following}

Momenteel, is het noodzakelijk om het bezit te plaatsen om te bepalen of de component de `follows` verhouding, of de `following` verhouding toont.

## Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Social Graph Essentials](essentials-socialgraph.md) voor ontwikkelaars.
