---
title: Ontwerpen en de Designer
description: Leer hoe u een ontwerp voor uw website en in AEM maakt met de Designer.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: c81c5910-b6c9-41bd-8840-a6782792701f
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Ontwerpen en de Designer{#designs-and-the-designer}

>[!CAUTION]
>
>In dit artikel wordt beschreven hoe u een website maakt op basis van de klassieke gebruikersinterface. De Adobe adviseert gebruikend de recentste AEM technologieën voor uw websites zoals die in detail in artikel [ worden beschreven Begonnen het Ontwikkelen van AEM Sites ](/help/sites-developing/getting-started.md).

Designer wordt gebruikt om een ontwerp voor uw website tot stand te brengen gebruikend [ Klassieke UI ](/help/release-notes/touch-ui-features-status.md) in AEM.

>[!NOTE]
>
>Voor meer informatie over de toegankelijkheid van het Web, zie [ AEM en de Richtlijnen van de Toegankelijkheid van het Web ](/help/managing/web-accessibility.md).

## De Designer gebruiken {#using-the-designer}

Uw ontwerp kan in de **ontwerpen** sectie van de **Hulpmiddelen** tabel worden bepaald:

![ screen_shot_2012-02-01at30237pm ](assets/screen_shot_2012-02-01at30237pm.png)

Hier kunt u de structuur maken die nodig is om het ontwerp op te slaan en vervolgens de trapsgewijze stijlpagina&#39;s en de vereiste afbeeldingen uploaden.

Ontwerpen worden opgeslagen onder `/apps/<your-project>` . Het pad naar het ontwerp dat voor een website moet worden gebruikt, wordt opgegeven met de eigenschap `cq:designPath` van het knooppunt `jcr:content` .

![ chlimage_1-74 ](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Alle wijzigingen die in de ontwerpmodus op een pagina zijn aangebracht, blijven behouden onder het ontwerpknooppunt van de site en worden automatisch toegepast op alle pagina&#39;s met hetzelfde ontwerp.

## Wat u nodig hebt {#what-you-will-need}

Om uw ontwerp te realiseren zult u nodig hebben:

**CSS** - De Cascading Bladen van de Stijl bepalen de formaten van specifieke gebieden op uw pagina&#39;s.
**Beelden** - om het even welke beelden die u voor eigenschappen zoals achtergronden, knopen gebruikt.

### Overwegingen bij het ontwerpen van uw website {#considerations-when-designing-your-website}

Wanneer u een website ontwikkelt, wordt het ten zeerste aanbevolen om afbeeldingen en CSS-bestanden op te slaan onder `/apps/<your-project>` , zodat u op basis van het huidige ontwerp kunt verwijzen naar uw bronnen, zoals in het volgende fragment wordt beschreven.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

Het voorgaande voorbeeld biedt verschillende voordelen:

* Componenten kunnen een andere vormgeving hebben op basis van elke site en een ander ontwerppad gebruiken.
* U kunt de website opnieuw ontwerpen door het ontwerppad naar een ander knooppunt in de hoofdmap van de site te verplaatsen van `design/v1` naar `design/v2.` .

* `/etc/designs` en `/content` zijn de enige externe URL&#39;s die de browser ziet als beveiliging voor een externe gebruiker die nieuwsgierig wordt naar wat zich onder de `/apps` -structuur bevindt. De bovenstaande URL-voordelen helpen uw systeembeheerder ook om een betere beveiliging in te stellen, omdat u de blootstelling van de elementen aan een aantal verschillende locaties beperkt.
