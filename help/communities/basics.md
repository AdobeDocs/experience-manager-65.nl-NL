---
title: Grondbeginselen van Community-componenten
seo-title: Grondbeginselen van Community-componenten
description: Functies van Gemeenschappen toevoegen aan AEM sites in bewerkingsmodus en componenten configureren
seo-description: Functies van Gemeenschappen toevoegen aan AEM sites in bewerkingsmodus en componenten configureren
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
translation-type: tm+mt
source-git-commit: c77a353d43a3a6f33dffecf0b4e7672ed3e2dd3f
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---


# Grondbeginselen van Community-componenten {#communities-components-basics}

## Overzicht {#overview}

In het gedeelte dat wordt geschreven in de documentatie wordt beschreven hoe u de functies van een Gemeenschappen toevoegt aan AEM sites in de bewerkingsmodus van de auteur en hoe u componentconfiguraties beschrijft.

Componenten kunnen worden onderzocht met behulp van een AEM en de interactieve [Community Components-handleiding](components-guide.md).

## Toegang tot onderdelen van Gemeenschappen {#accessing-communities-components}

Als tijdens het ontwerpen van pagina-inhoud de onderliggende sjabloon wijzigingen toestaat in het ontwerp van de pagina, is het mogelijk om componenten in te schakelen die nog niet beschikbaar zijn in de browser met componenten als onderdeel van het siteontwerp.

De beschikbare communautaire componenten zijn [hier](author-communities.md#available-communities-components)vermeld.

>[!NOTE]
>
>Voor algemene ontwerpinformatie raadpleegt u de [handleiding voor het maken van pagina](../../help/sites-authoring/qg-page-authoring.md)&#39;s.
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over de [basisafhandeling](../../help/sites-authoring/basic-handling.md).


### Ontwerpmodus invoeren {#entering-design-mode}

Als een **Community** -component niet wordt gevonden in de Componentbrowser (sidekick), moet u andere Community-componenten invoeren `Design Mode` om deze toe te voegen. [De vereiste clientbibliotheken](#required-clientlibs) (clientlibs) moeten mogelijk ook worden toegevoegd.

Zie Componenten [configureren in Ontwerpmodus](../../help/sites-authoring/default-components-designmode.md)voor meer informatie.

Hieronder vindt u afbeeldingen van het selecteren van een paar onderdelen van de Gemeenschappen en het weergeven hiervan in de browser met componenten:

![componentontwerp](assets/component-design.png)

De geselecteerde componenten zijn nu beschikbaar in de componentenbrowser:

![component-design1](assets/component-design1.png)

## Vereiste clientlibs {#required-clientlibs}

[Clientzijbibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) zijn vereist voor het goed functioneren (JavaScript) en het opmaken (CSS) van een component.

Wanneer u een Community-component aan een pagina toevoegt, als het resultaat een fout of een onverwachte weergave is, voegt u eerst de vereiste clientlibs voor de Community-component toe. Zie Clientlibs [voor Community Components](clientlibs.md)voor meer informatie.

### Voorbeeld: Aanvankelijk geplaatste revisies zonder clientbibliotheken... {#example-initially-placed-reviews-without-client-libraries}

![clientlibs1](assets/clientlibs1.png)

### ... En met clientbibliotheken {#and-with-client-libraries}

![clientlibs2](assets/clientlibs2.png)

## Tags {#tagging}

Veel functies van een Community kunnen zo worden geconfigureerd dat leden inhoud die is ingevoerd (gepost) in de publicatieomgeving kunnen labelen.

Als het etiketteren wordt toegestaan, kan de configuratie van de communautaire plaats worden geplaatst om de namespaces te beperken die aan leden in het publicatiemilieu worden voorgesteld. Zie de [Community Sites-console](sites-console.md#tagging).

Functies die codering mogelijk maken: [blog](blog-feature.md), [agenda](calendar.md), [bestandsbibliotheek](file-library.md), [forum](forum.md)

Functies die tags gebruiken: [catalogus](catalog.md), [zoeken](search.md), cloud met [sociale tags](tagcloud.md)

Voor ontwerpinformatie:

* [Tags gebruiken](../../help/sites-authoring/tags.md)

Voor administratieve informatie:

* Tagnaamruimten maken (taxonomie): [Tags beheren](../../help/sites-administering/tags.md)
* Configuratie van community-site: zie [TAGS](sites-console.md#tagging)
* [Door gebruiker gegenereerde inhoud labelen](../../help/sites-authoring/tags.md)
* [Tags toewijzen](tag-resources.md)

Voor informatie over ontwikkelaars:

* [Kader voor tags AEM](../../help/sites-developing/framework.md)
* [Grondbeginselen van tags](tag.md)

