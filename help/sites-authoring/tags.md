---
title: Tags gebruiken
description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: 49f95b31-92cd-4124-8c0f-c9802099fd0b
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---


# Tags gebruiken {#using-tags}

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.

* Zie [Tags beheren](/help/sites-administering/tags.md) voor informatie over het maken en beheren van tags en waarop inhoudstags zijn toegepast.
* Zie [Tags voor ontwikkelaars](/help/sites-developing/tags.md) voor informatie over het etiketteringskader en het opnemen van en het uitbreiden van markeringen in douanetoepassingen.

## Tien redenen voor het gebruik van tags {#ten-reasons-to-use-tagging}

1. **Inhoud ordenen** - Tags maken auteurs het leven makkelijker omdat ze inhoud snel en zonder moeite kunnen organiseren.
1. **Tags ordenen** - Terwijl tags inhoud ordenen, ordenen hiërarchische taxonomieën/naamruimten tags.
1. **Georganiseerde tags toepassen** - Met de mogelijkheid om codes en subcodes te maken, wordt het mogelijk volledige taxonomische systemen uit te drukken, met inbegrip van termen, subtermen en hun relaties. Zo kunt u een tweede (of derde) inhoudshiërarchie maken die parallel is aan de officiële inhoudshiërarchie.
1. **Gecontroleerde labeling** - Tags kunnen worden ingesteld door machtigingen toe te passen op tags en/of naamruimten om het maken en de toepassing van tags te beheren.
1. **Flexibele tags** - Tags hebben vele namen en gezichten: tags, taxonomie termen, categorieën, labels en nog veel meer. Ze zijn flexibel in hun inhoudsmodel en in de manier waarop ze kunnen worden gebruikt, bijvoorbeeld bij het beschrijven van doeldemografie, het categoriseren en classificeren van inhoud of het creëren van een secundaire inhoudshiërarchie.
1. **Verbeterd zoeken** - De standaardzoekcomponent in AEM bevat over het algemeen gemaakte tags en toegepaste tags waarop filters kunnen worden toegepast om de resultaten te beperken tot de relevante waarden.
1. **SEO inschakelen** - Labels die als pagina-eigenschappen zijn toegepast, worden automatisch weergegeven in de tags van de pagina, zodat deze zichtbaar zijn voor zoekmachines.
1. **Eenvoudig, geavanceerd** - Tags kunnen eenvoudig worden gemaakt op basis van een woord en de druk op een knop. Daarna kunt u een titel, beschrijving en een onbeperkt label toevoegen om meer semantiek aan de tag toe te voegen.
1. **Consistentie van kern** - Het coderingssysteem is een kernonderdeel van AEM en wordt door alle AEM gebruikt om inhoud te categoriseren. Verder is de API voor codering beschikbaar voor ontwikkelaars die toepassingen met codering willen maken die toegang hebben tot dezelfde taxonomieën.
1. **Combineert structuur en flexibiliteit** - AEM is ideaal voor het werken met gestructureerde informatie, omdat pagina&#39;s en paden genest zijn. Het is even krachtig wanneer het werken met ongestructureerde informatie, toe te schrijven aan de ingebouwde full-text onderzoek. Tags combineren de sterke punten van structuur en flexibiliteit.

Wanneer u de inhoudsstructuur voor een site en het metagegevensschema voor elementen ontwerpt, moet u rekening houden met de lichte en toegankelijke manier waarop u tags kunt toewijzen.

## Tags toepassen {#applying-tags}

In de auteursomgeving kunnen de auteurs markeringen toepassen door tot de pagina eigenschappen toegang te hebben en één of meerdere markeringen in te gaan in **Tags/trefwoorden** veld.

Toepassen [vooraf gedefinieerde tags](/help/sites-administering/tags.md)in de **Pagina-eigenschappen** het venster gebruiken **Tags** en de **Labels selecteren** venster. De **Standaardlabels** tab is de standaardnaamruimte, wat betekent dat er geen `namespace-string:` voorafgegaan aan de taxonomie.

![Selecteer het venster van Markeringen; gebruik de knoop van X om de momenteel geselecteerde markeringen te schrappen](assets/chlimage_1-41.png)

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
