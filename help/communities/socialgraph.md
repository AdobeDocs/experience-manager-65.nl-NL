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

Het vermogen van een lid van de gemeenschap om te volgen [activiteiten](activities.md) en moet worden gevolgd door twee componenten: `Follow` en `Following`.

De `Follow` moet worden gekoppeld aan een andere hulpbron en deze associatie is al opgericht voor leden en functies van de gemeenschap .

De `Following` de component maakt een lijst eenvoudig van de leden die of het huidige lid volgen of door het huidige lid worden gevolgd. Deze sociale grafiek van de relaties tussen leden is opgenomen in het gebruikersprofiel dat is ingesteld voor een [community-site](overview.md#communitiessites).

## Volgende toevoegen aan een pagina {#adding-following-to-a-page}

Indien u een `Following` naar een pagina in de modus Schrijver, zoek de component `Communities / Following` en sleep het naar de juiste plaats op een pagina waarop de sociale grafiek moet worden weergegeven.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](basics.md).

Wanneer de [vereiste clientbibliotheken](essentials-socialgraph.md#essentials-for-client-side) worden opgenomen, is dit hoe `Following` wordt weergegeven:

![volgende](assets/following.png)

## Configureren na {#configuring-following}

Op dit moment moet de eigenschap worden ingesteld om te bepalen of de component de eigenschap `follows` of de `following` relatie.

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Grondbeginselen van sociale grafiek](essentials-socialgraph.md) pagina voor ontwikkelaars.
