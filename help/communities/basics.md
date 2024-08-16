---
title: Grondbeginselen van Community-componenten
description: Functies van Gemeenschappen toevoegen aan AEM sites in bewerkingsmodus en componenten configureren
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: eb5ce76a-bf28-4540-bc2d-3b5ecb8286f2
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Grondbeginselen van Community-componenten {#communities-components-basics}

## Overzicht {#overview}

In het gedeelte dat wordt geschreven in de documentatie wordt beschreven hoe u de functies van een Gemeenschappen toevoegt aan AEM sites in de modus Bewerken van de auteur en hoe u componentconfiguraties beschrijft.

De componenten kunnen worden onderzocht gebruikend een AEM instantie en de interactieve [ gids van de Componenten van de Gemeenschap ](components-guide.md).

## Toegang tot onderdelen van Gemeenschappen {#accessing-communities-components}

Als tijdens het ontwerpen van pagina-inhoud de onderliggende sjabloon wijzigingen toestaat in het ontwerp van de pagina, is het mogelijk om componenten in te schakelen die nog niet beschikbaar zijn in de browser met componenten als onderdeel van het siteontwerp.

Zie de lijst onder [ Beschikbare Componenten van Gemeenschappen ](author-communities.md#available-communities-components).

>[!NOTE]
>
>Voor algemene auteursinformatie, bekijk de [ snelle gids aan auteurspagina&#39;s ](../../help/sites-authoring/qg-page-authoring.md).
>
>Als niet vertrouwd met AEM, bekijk de documentatie over [ basisbehandeling ](../../help/sites-authoring/basic-handling.md).

### Ontwerpmodus invoeren {#entering-design-mode}

Als de component van a **Gemeenschappen** niet in componenten browser (sidekick) wordt gevonden, zal het noodzakelijk zijn `Design Mode` binnen te gaan om andere componenten van Gemeenschappen toe te voegen. [ Vereiste cliënt-zijbibliotheken ](#required-clientlibs) (clientlibs) kunnen ook moeten worden toegevoegd.

Voor details, zie [ Vormende Componenten op de Wijze van het Ontwerp ](../../help/sites-authoring/default-components-designmode.md).

Hieronder vindt u afbeeldingen van het selecteren van een paar onderdelen van de Gemeenschappen en het weergeven hiervan in de browser met componenten:

![ component-ontwerp ](assets/component-design.png)

De geselecteerde componenten zijn nu beschikbaar in de componentenbrowser:

![ component-design1 ](assets/component-design1.png)

## Vereiste clientlibs {#required-clientlibs}

[ cliënt-zijbibliotheken ](../../help/sites-developing/clientlibs.md) (clientlibs) worden vereist voor het juiste functioneren (JavaScript) en het stileren (CSS) van een component.

Wanneer u een Community-component aan een pagina toevoegt, als het resultaat een fout of een onverwachte weergave is, moet u eerst de vereiste clientlibs voor de Community-component toevoegen. Voor details, zie [ Clientlibs voor de Componenten van Gemeenschappen ](clientlibs.md).

### Voorbeeld: oorspronkelijk geplaatste revisies zonder clientbibliotheken... {#example-initially-placed-reviews-without-client-libraries}

![ clientlibs1 ](assets/clientlibs1.png)

### ... En met clientbibliotheken {#and-with-client-libraries}

![ clientlibs2 ](assets/clientlibs2.png)

## Tags {#tagging}

Veel functies van een Community kunnen zo worden geconfigureerd dat leden inhoud die is ingevoerd (gepost) in de publicatieomgeving kunnen labelen.

Als het etiketteren wordt toegestaan, kan de configuratie van de communautaire plaats worden geplaatst om de namespaces te beperken die aan leden in het publicatiemilieu worden voorgesteld. Zie de [ console van Plaatsen Gemeenschap ](sites-console.md#tagging).

Eigenschappen die het etiketteren toestaan: [ blog ](blog-feature.md), [ kalender ](calendar.md), [ dossierbibliotheek ](file-library.md), [ forum ](forum.md)

Eigenschappen die markeringen gebruiken: [ onderzoek ](search.md), [ sociale markeringswolk ](tagcloud.md)

Voor ontwerpinformatie:

* [Tags gebruiken](../../help/sites-authoring/tags.md)

Voor administratieve informatie:

* Creërend markeringsnamespaces (taxonomie): [ het Beheer Markeringen ](../../help/sites-administering/tags.md)
* Configuratie van de communautaire Plaats: zie [ TAGING ](sites-console.md#tagging)
* [Door gebruiker gegenereerde inhoud labelen](../../help/sites-authoring/tags.md)

Voor informatie over ontwikkelaars:

* [Kader voor tags AEM](../../help/sites-developing/framework.md)
* [Grondbeginselen van tags](tag.md)
