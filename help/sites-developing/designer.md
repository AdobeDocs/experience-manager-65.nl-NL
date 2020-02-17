---
title: Ontwerpen en de Designer
seo-title: Ontwerpen en de Designer
description: U moet een ontwerp voor uw website maken en in AEM doet u dat met de Designer
seo-description: U moet een ontwerp voor uw website maken en in AEM doet u dat met de Designer
uuid: b880ab49-8bea-4925-9b7b-e911ebda14ee
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f9bcb6eb-1df4-4709-bcec-bef0931f797a
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# Ontwerpen en de Designer{#designs-and-the-designer}

>[!CAUTION]
>
>In dit artikel wordt beschreven hoe u een website maakt op basis van de klassieke gebruikersinterface. Adobe raadt u aan de nieuwste AEM-technologieën voor uw websites te gebruiken, zoals gedetailleerd wordt beschreven in het artikel [Aan de slag met het ontwikkelen van AEM-sites](/help/sites-developing/getting-started.md).

U moet een ontwerp voor uw website maken en in AEM doet u dat met de Designer.

>[!NOTE]
>
>Zie [AEM en de Web Accessibility Guidelines](/help/managing/web-accessibility.md)voor meer informatie over webtoegankelijkheid.

## De Designer gebruiken {#using-the-designer}

Uw ontwerp kan worden gedefinieerd in het gedeelte **Ontwerpen** van het tabblad **Gereedschappen** :

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Hier kunt u de structuur maken die nodig is om het ontwerp op te slaan en vervolgens de trapsgewijze stijlpagina&#39;s en de vereiste afbeeldingen uploaden.

Ontwerpen worden opgeslagen onder `/etc/designs`. Het pad naar het ontwerp dat voor een website moet worden gebruikt, wordt opgegeven met de `cq:designPath` eigenschap van het `jcr:content` knooppunt.

![chlimage_1-74](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Alle wijzigingen die in de ontwerpmodus op een pagina zijn aangebracht, blijven behouden onder het ontwerpknooppunt van de site en worden automatisch toegepast op alle pagina&#39;s met hetzelfde ontwerp.

## Wat u nodig hebt {#what-you-will-need}

Om uw ontwerp te realiseren zult u nodig hebben:

**CSS** - In de CSS-stijlbladen worden de opmaken van specifieke gebieden op uw pagina&#39;s gedefinieerd.
**Afbeeldingen** - Alle afbeeldingen die u gebruikt voor functies zoals achtergronden en knoppen.

### Overwegingen bij het ontwerpen van uw website {#considerations-when-designing-your-website}

Wanneer u een website ontwikkelt, wordt het ten zeerste aanbevolen om afbeeldingen en CSS-bestanden onder op te slaan, `/etc/design/<project>` zodat u op basis van het huidige ontwerp naar uw bronnen kunt verwijzen, zoals in het volgende fragment wordt beschreven.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

Het voorgaande voorbeeld biedt verschillende voordelen:

* Componenten kunnen een andere vormgeving hebben op basis van elke site en een ander ontwerppad gebruiken.
* U kunt het ontwerp van de website eenvoudig opnieuw ontwerpen door het ontwerppad naar een ander knooppunt in de hoofdmap van de site van `design/v1` naar `design/v2.`

* `/etc/designs` en `/content` zijn de enige externe URL&#39;s die de browser ziet als bescherming van een externe gebruiker die nieuwsgierig wordt naar wat zich onder uw `/apps` structuur bevindt. De bovenstaande URL-voordelen helpen uw systeembeheerder ook een betere beveiliging in te stellen, omdat u de blootstelling van de elementen aan een aantal verschillende locaties beperkt.

