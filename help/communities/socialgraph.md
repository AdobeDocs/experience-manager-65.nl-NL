---
title: Sociale grafiek gebruiken
description: Leer hoe u een volgende component toevoegt aan een pagina waarop leden van de gemeenschap die zich hebben aangemeld activiteiten kunnen volgen of kunnen worden gevolgd.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 2cd1436b-3727-4757-b28e-70756be78a4e
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Sociale grafiek gebruiken {#using-social-graph}

## Inleiding {#introduction}

De capaciteit voor een communautair lid om [ activiteiten ](activities.md) te volgen en te worden gevolgd wordt gevestigd door twee componenten: `Follow` en `Following`.

De component `Follow` moet aan een andere bron worden geassocieerd, en deze vereniging is reeds gevestigd voor communautaire leden en eigenschappen.

De component `Following` geeft alleen de leden weer die het huidige lid volgen of die door het huidige lid worden gevolgd. Deze sociale grafiek van de verhoudingen tussen leden is inbegrepen in het gebruikersprofiel dat voor a [ wordt gevestigd communautaire plaats ](overview.md#communitiessites).

## Volgende toevoegen aan een pagina {#adding-following-to-a-page}

Als u een component `Following` wilt toevoegen aan een pagina in de ontwerpmodus, zoekt u de component `Communities / Following` en sleept u deze naar de plaats op een pagina waar de sociale grafiek moet verschijnen.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen ](basics.md).[

Wanneer de [ vereiste cliënt-zijbibliotheken ](essentials-socialgraph.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Following` component verschijnt:

![ volgend ](assets/following.png)

## Configureren na {#configuring-following}

Op dit moment is het nodig om de eigenschap in te stellen om te bepalen of de component de `follows` -relatie of de `following` -relatie weergeeft.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de ](essentials-socialgraph.md) pagina van de Hoofdzaak van de Grafiek worden gevonden 0} Sociale.[
