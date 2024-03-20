---
title: Tags gebruiken
description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 4b6c273c-560e-4330-b886-a02825d5aaa1
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Tags gebruiken{#using-tags}

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.

* Zie [Tags beheren](/help/sites-administering/tags.md) voor informatie over het maken en beheren van tags en waarop inhoudstags zijn toegepast.
* Zie [Tags voor ontwikkelaars](/help/sites-developing/tags.md) voor informatie over het etiketteringskader en het opnemen van en het uitbreiden van markeringen in douanetoepassingen.

## Tien redenen voor het gebruik van tags {#ten-reasons-to-use-tagging}

1. Inhoud ordenen: labelen maakt het voor auteurs gemakkelijker om inhoud snel en eenvoudig te organiseren.
1. Tags organiseren: terwijl de inhoud wordt gerangschikt, ordenen hiërarchische taxonomieën/naamruimten de tags.
1. Met diep georganiseerde tags: met de mogelijkheid om tags en subtags te maken, wordt het mogelijk om volledige taxonomische systemen uit te drukken, met inbegrip van termen, subtermen en hun relaties. Zo kunt u een tweede (of derde) inhoudshiërarchie maken die parallel is aan de officiële inhoudshiërarchie.
1. Gecontroleerde labeling: codering kan worden beheerd door machtigingen toe te passen op tags en/of naamruimten om het maken en de toepassing van tags te regelen.
1. Flexibele tags: tags hebben veel namen en gezichten: tags, taxonomie termen, categorieën, labels en nog veel meer. Ze zijn flexibel in hun inhoudsmodel en in de manier waarop ze kunnen worden gebruikt, bijvoorbeeld bij het beschrijven van doeldemografie, het categoriseren en classificeren van inhoud of het creëren van een secundaire inhoudshiërarchie.
1. Verbeterd zoeken: de standaardzoekcomponent in AEM bevat over het algemeen gemaakte tags en toegepaste tags waarop filters kunnen worden toegepast om de resultaten te beperken tot de relevante waarden.
1. SEO Inschakelen : tags die zijn toegepast als pagina-eigenschappen worden automatisch weergegeven in de tags van de pagina, zodat deze zichtbaar zijn voor zoekmachines.
1. Eenvoudig, geavanceerd: tags kunnen eenvoudig worden gemaakt op basis van een woord en de druk op een knop. Daarna kunt u een titel, beschrijving en een onbeperkt label toevoegen om meer semantiek aan de tag toe te voegen.
1. Basisconsistentie: het coderingssysteem is een kernonderdeel van AEM en wordt door alle AEM gebruikt om inhoud te categoriseren. Verder is de API voor codering beschikbaar voor ontwikkelaars die toepassingen met codering willen maken die toegang hebben tot dezelfde taxonomieën.
1. Combineert Structuur en flexibiliteit: AEM is ideaal voor het werken met gestructureerde informatie vanwege het nesten van pagina&#39;s en paden. Het is even krachtig wanneer het werken met ongestructureerde informatie, toe te schrijven aan de ingebouwde full-text onderzoek. Tags combineren de sterke punten van structuur en flexibiliteit.

Wanneer u de inhoudsstructuur voor een site en het metagegevensschema voor elementen ontwerpt, moet u rekening houden met de lichte en toegankelijke manier waarop u tags kunt toewijzen.

## Tags toepassen {#applying-tags}

In de auteursomgeving kunnen de auteurs markeringen toepassen door tot de pagina eigenschappen toegang te hebben en één of meerdere markeringen in te gaan in **Tags/trefwoorden** veld.

Toepassen [vooraf gedefinieerde tags](/help/sites-administering/tags.md)in de **Pagina-eigenschappen** het venster gebruiken `Tags/Keywords` het gebied trekkracht-onderaan om van de lijst van markeringen te selecteren die voor de pagina worden toegelaten. Tthe **Standaardlabels** tab is de standaardnaamruimte, wat betekent dat er geen `namespace-string:` voorafgegaan aan de taxonomie.

![chlimage_1-2](assets/chlimage_1-2a.png)

### Codes publiceren {#publishing-tags}

Net als bij pagina&#39;s kunt u het volgende uitvoeren op tags en naamruimten:

**Activeren**

* Afzonderlijke tags activeren.

  Net als bij pagina&#39;s moeten nieuwe tags worden geactiveerd voordat deze beschikbaar komen in de publicatieomgeving.

>[!NOTE]
>
>Wanneer u een pagina activeert, wordt automatisch een dialoogvenster geopend waarin u niet-geactiveerde tags die bij de pagina horen, kunt activeren.

**Deactiveren**

* Deactiveer de geselecteerde labels.

## Labelwolken {#tag-clouds}

Tagwolken tonen een wolk van markeringen, of voor de huidige pagina, de volledige website, of die het vaakst betreden. Labelwolken zijn een manier om de problemen te markeren die de gebruiker interesseert (geweest). De grootte van de tekst die wordt gebruikt om de tag weer te geven, is afhankelijk van het gebruik ervan.

De [Cloud labelen](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md#tag-cloud) wordt gebruikt om een tagwolk aan een pagina toe te voegen (groep Algemeen).

## Zoeken op tags {#searching-on-tags}

U kunt tags zoeken in zowel de auteur- als de publicatieomgeving.

### Zoekcomponent gebruiken {#using-search-component}

Een [component Zoeken](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md#search) op een pagina biedt een zoekfunctie die tags bevat en kan worden gebruikt in zowel de auteur- als de publicatieomgeving.

![chlimage_1-3](assets/chlimage_1-3a.png)
