---
title: Grondbeginselen van Community-componenten
seo-title: Communities Components Basics
description: Functies van Gemeenschappen toevoegen aan AEM sites in bewerkingsmodus en componenten configureren
seo-description: Add Communities features to AEM sites in edit mode and configure components
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
exl-id: eb5ce76a-bf28-4540-bc2d-3b5ecb8286f2
source-git-commit: 4dbbcc41757843d3b2d5a3bbb2656ef587e83d2c
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 1%

---

# Grondbeginselen van Community-componenten {#communities-components-basics}

## Overzicht {#overview}

In het gedeelte dat wordt geschreven in de documentatie wordt beschreven hoe u de functies van een Gemeenschappen toevoegt aan AEM sites in de bewerkingsmodus van de auteur en hoe u componentconfiguraties beschrijft.

Componenten kunnen worden onderzocht met behulp van een AEM en de interactieve [Community Components Guide](components-guide.md).

## Toegang tot onderdelen van Gemeenschappen {#accessing-communities-components}

Als tijdens het ontwerpen van pagina-inhoud de onderliggende sjabloon wijzigingen toestaat in het ontwerp van de pagina, is het mogelijk om componenten in te schakelen die nog niet beschikbaar zijn in de browser met componenten als onderdeel van het siteontwerp.

De beschikbare onderdelen van de Gemeenschappen worden vermeld [hier](author-communities.md#available-communities-components).

>[!NOTE]
>
>Voor algemene ontwerpinformatie bekijkt u de [snelle handleiding voor het ontwerpen van pagina&#39;s](../../help/sites-authoring/qg-page-authoring.md).
>
>Als u niet bekend bent met AEM, kunt u de documentatie raadplegen op [basisbehandeling](../../help/sites-authoring/basic-handling.md).

### Ontwerpmodus invoeren {#entering-design-mode}

Indien een **Gemeenschappen** component wordt niet gevonden in componenten browser (sidekick), zal het noodzakelijk zijn om binnen te gaan `Design Mode` om andere communautaire componenten toe te voegen. [Vereiste clientbibliotheken](#required-clientlibs) (clientlibs) moet mogelijk ook worden toegevoegd.

Zie voor meer informatie [Componenten configureren in ontwerpmodus](../../help/sites-authoring/default-components-designmode.md).

Hieronder vindt u afbeeldingen van het selecteren van een paar onderdelen van de Gemeenschappen en het weergeven hiervan in de browser met componenten:

![componentontwerp](assets/component-design.png)

De geselecteerde componenten zijn nu beschikbaar in de componentenbrowser:

![component-design1](assets/component-design1.png)

## Vereiste clientlibs {#required-clientlibs}

[Bibliotheken op de client](../../help/sites-developing/clientlibs.md) (clientlibs) zijn vereist voor het correct functioneren (JavaScript) en opmaken (CSS) van een component.

Wanneer u een Community-component aan een pagina toevoegt, als het resultaat een fout of een onverwachte weergave is, voegt u eerst de vereiste clientlibs voor de Community-component toe. Zie voor meer informatie [Clientlibs voor Community-componenten](clientlibs.md).

### Voorbeeld: Aanvankelijk geplaatste revisies zonder clientbibliotheken... {#example-initially-placed-reviews-without-client-libraries}

![clientlibs1](assets/clientlibs1.png)

### ... En met clientbibliotheken {#and-with-client-libraries}

![clientlibs2](assets/clientlibs2.png)

## Tags {#tagging}

Veel functies van een Community kunnen zo worden geconfigureerd dat leden inhoud die is ingevoerd (gepost) in de publicatieomgeving kunnen labelen.

Als het etiketteren wordt toegestaan, kan de configuratie van de communautaire plaats worden geplaatst om de namespaces te beperken die aan leden in het publicatiemilieu worden voorgesteld. Zie de [Community Sites-console](sites-console.md#tagging).

Functies die codering mogelijk maken: [blog](blog-feature.md), [kalender](calendar.md), [bestandsbibliotheek](file-library.md), [forum](forum.md)

Functies die tags gebruiken: [zoeken](search.md), [social tag-cloud](tagcloud.md)

Voor ontwerpinformatie:

* [Tags gebruiken](../../help/sites-authoring/tags.md)

Voor administratieve informatie:

* Tagnaamruimten maken (taxonomie): [Tags beheren](../../help/sites-administering/tags.md)
* Configuratie van community-site: zie [TAGS](sites-console.md#tagging)
* [Door gebruiker gegenereerde inhoud labelen](../../help/sites-authoring/tags.md)

Voor informatie over ontwikkelaars:

* [Kader voor tags AEM](../../help/sites-developing/framework.md)
* [Grondbeginselen van tags](tag.md)
