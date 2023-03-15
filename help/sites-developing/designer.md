---
title: Ontwerpen en de Designer
seo-title: Designs and the Designer
description: U moet een ontwerp voor uw website maken en in AEM doet u dit met de Designer
seo-description: You will need to create a design for your website and in AEM, you do so by using the Designer
uuid: b880ab49-8bea-4925-9b7b-e911ebda14ee
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f9bcb6eb-1df4-4709-bcec-bef0931f797a
exl-id: c81c5910-b6c9-41bd-8840-a6782792701f
source-git-commit: adbdff9ff5b5bd8f5f6b22fb724a0e5273072de2
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Ontwerpen en de Designer{#designs-and-the-designer}

>[!CAUTION]
>
>In dit artikel wordt beschreven hoe u een website maakt op basis van de klassieke gebruikersinterface. Adobe raadt u aan de nieuwste AEM technologieën voor uw websites te gebruiken, zoals in detail wordt beschreven in het artikel [Aan de slag met het ontwikkelen van AEM Sites](/help/sites-developing/getting-started.md).

Met Designer kunt u een ontwerp voor uw website maken met de opdracht [Klassieke interface](/help/release-notes/touch-ui-features-status.md) in AEM.

>[!NOTE]
>
>Voor meer informatie over de toegankelijkheid van het Web, zie [AEM en de Web Accessibility Guidelines](/help/managing/web-accessibility.md).

## De Designer gebruiken {#using-the-designer}

Uw ontwerp kan in **ontwerpen** van de **Gereedschappen** tab:

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Hier kunt u de structuur maken die nodig is om het ontwerp op te slaan en vervolgens de trapsgewijze stijlpagina&#39;s en de vereiste afbeeldingen uploaden.

Ontwerpen worden opgeslagen onder `/apps/<your-project>`. Het pad naar het ontwerp dat voor een website moet worden gebruikt, wordt opgegeven met het `cq:designPath` eigendom van de `jcr:content` knooppunt.

![chlimage_1-74](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Alle wijzigingen die in de ontwerpmodus op een pagina zijn aangebracht, blijven behouden onder het ontwerpknooppunt van de site en worden automatisch toegepast op alle pagina&#39;s met hetzelfde ontwerp.

## Wat u nodig hebt {#what-you-will-need}

Om uw ontwerp te realiseren zult u nodig hebben:

**CSS** - In de CSS (Cascading Style Sheets) worden de opmaken van specifieke gebieden op uw pagina&#39;s gedefinieerd.
**Afbeeldingen** - Alle afbeeldingen die u gebruikt voor functies zoals achtergronden en knoppen.

### Overwegingen bij het ontwerpen van uw website {#considerations-when-designing-your-website}

Bij het ontwikkelen van een website wordt het ten zeerste aanbevolen om afbeeldingen en CSS-bestanden onder `/apps/<your-project>` zodat kunt u naar uw bronnen verwijzen op basis van het huidige ontwerp, zoals wordt beschreven in het volgende fragment.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

Het voorgaande voorbeeld biedt verschillende voordelen:

* Componenten kunnen een andere vormgeving hebben op basis van elke site en een ander ontwerppad gebruiken.
* U kunt de website opnieuw ontwerpen door het ontwerppad vanuit de hoofdmap van de site naar een ander knooppunt van de site te wijzen `design/v1` tot `design/v2.`

* `/etc/designs` en `/content` zijn de enige externe URL&#39;s die de browser ziet als bescherming van een externe gebruiker die zich zorgen maakt over wat er onder uw `/apps` boom. De bovenstaande URL-voordelen helpen uw systeembeheerder ook een betere beveiliging in te stellen, omdat u de blootstelling van de elementen aan een aantal verschillende locaties beperkt.
