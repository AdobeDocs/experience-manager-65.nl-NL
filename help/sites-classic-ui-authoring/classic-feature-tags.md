---
title: Tags gebruiken
seo-title: Tags gebruiken
description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.
seo-description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.
uuid: 9799131f-4043-4022-a401-af8be93a1bf6
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: c117b9d1-e4ae-403f-8619-6e48d424a761
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Tags gebruiken{#using-tags}

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.

* Zie [Tags](/help/sites-administering/tags.md) beheren voor informatie over het maken en beheren van tags en over de inhoudstags die zijn toegepast.
* Zie [Tags toevoegen voor ontwikkelaars](/help/sites-developing/tags.md) voor informatie over het coderingsframework en voor het opnemen en uitbreiden van tags in aangepaste toepassingen.

## Tien redenen voor het gebruik van tags {#ten-reasons-to-use-tagging}

1. Inhoud ordenen: het labelen maakt het leven voor auteurs gemakkelijker aangezien zij inhoud snel en zonder moeite kunnen organiseren .
1. Tags organiseren: terwijl tags inhoud ordenen, ordenen hiërarchische taxonomieën/naamruimten tags.
1. Georganiseerde tags toepassen: met de mogelijkheid om codes en subcodes te maken, wordt het mogelijk volledige taxonomische systemen uit te drukken, met inbegrip van termen, subtermen en hun relaties. Zo kunt u een tweede (of derde) inhoudshiërarchie maken die parallel is aan de officiële inhoudshiërarchie.
1. Gecontroleerde labeling: U kunt de codering beheren door machtigingen toe te passen op tags en/of naamruimten om het maken en de toepassing van tags te beheren.
1. Flexibele tags: Tags hebben vele namen en gezichten: tags, taxonomie termen, categorieën, labels en nog veel meer. Zij zijn flexibel in hun inhoudsmodel en in de manier waarop zij kunnen worden gebruikt; bijvoorbeeld bij het schetsen van doeldemografie, het categoriseren en classificeren van inhoud of het creëren van een secundaire inhoudshiërarchie.
1. Verbeterd zoeken: De standaardzoekcomponent in AEM bevat over het algemeen gemaakte tags en toegepaste tags waarop filters kunnen worden toegepast om de resultaten te beperken tot de relevante waarden.
1. SEO inschakelen: tags die zijn toegepast als pagina-eigenschappen, worden automatisch weergegeven in de tags van de pagina, zodat deze zichtbaar zijn voor zoekprogramma&#39;s.
1. Eenvoudig, geavanceerd: U kunt eenvoudig tags maken op basis van een woord en een knop. Daarna kunt u een titel, beschrijving en een onbeperkt label toevoegen om meer semantiek aan de tag toe te voegen.
1. Kernconsistentie: het coderingssysteem is een kernonderdeel van AEM en wordt door alle AEM-mogelijkheden gebruikt om inhoud te categoriseren. Verder is de API voor codering beschikbaar voor ontwikkelaars die toepassingen met codering willen maken die toegang hebben tot dezelfde taxonomieën.
1. Combineert structuur en flexibiliteit: AEM is ideaal voor het werken met gestructureerde informatie, door het nesten van pagina&#39;s en wegen. Het is even krachtig wanneer het werken met ongestructureerde informatie, toe te schrijven aan de ingebouwde full-text onderzoek. Tags combineren de sterke punten van structuur en flexibiliteit.

Wanneer u de inhoudsstructuur voor een site en het metagegevensschema voor elementen ontwerpt, moet u rekening houden met de lichte en toegankelijke manier waarop u tags kunt toewijzen.

## Tags toepassen {#applying-tags}

In de auteursomgeving, kunnen de auteurs markeringen toepassen door tot de pagina eigenschappen toegang te hebben en één of meerdere markeringen in het gebied van **Markeringen/Trefwoorden** in te gaan.

Als u [vooraf gedefinieerde codes](/help/sites-administering/tags.md)wilt toepassen, gebruikt u in het venster **Pagina-eigenschappen** de `Tags/Keywords` veldkeuzelijst om een optie te selecteren in de lijst met toegestane codes voor de pagina. Het tabblad **Standaardcodes** is de standaardnaamruimte, wat betekent dat er geen `namespace-string:` voorvoegsel is voor de taxonomie.

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

De component [Tagwolk](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md#tag-cloud) (groep Algemeen) wordt gebruikt om een tagwolk aan een pagina toe te voegen.

## Zoeken op tags {#searching-on-tags}

U kunt tags zoeken in zowel de auteur- als de publicatieomgeving.

### Zoekcomponent gebruiken {#using-search-component}

Als u een [zoekcomponent](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md#search) aan een pagina toevoegt, beschikt u over een zoekfunctie die tags bevat en die in zowel de auteur- als de publicatieomgeving kan worden gebruikt.

![chlimage_1-3](assets/chlimage_1-3a.png)

