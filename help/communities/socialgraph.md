---
title: Sociale grafiek gebruiken
seo-title: Using Social Graph
description: Een volgende component aan een pagina toevoegen
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: 2cd1436b-3727-4757-b28e-70756be78a4e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Sociale grafiek gebruiken {#using-social-graph}

## Inleiding {#introduction}

Het vermogen van een lid van de gemeenschap om te volgen [activiteiten](activities.md) en op deze wijze worden twee componenten vastgesteld : `Follow` en `Following`.

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
