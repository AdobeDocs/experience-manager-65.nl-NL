---
title: Tags gebruiken
seo-title: Tags gebruiken
description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren
seo-description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren
uuid: 5d922443-f924-426e-acf4-27dffd1053f6
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 9fb6d603-eb17-4192-bfa6-6c316f14ac7d
docset: aem65
translation-type: tm+mt
source-git-commit: 52cb99353ae33c8097b6b5bd29f6c040df30b42d
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 3%

---


# Tags gebruiken{#using-tags}

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.

* Zie [Tags beheren](/help/sites-administering/tags.md) voor informatie over het maken en beheren van tags en over de inhoudstags die zijn toegepast.
* Zie [Tags toevoegen voor ontwikkelaars](/help/sites-developing/tags.md) voor informatie over het coderingsframework en voor het opnemen en uitbreiden van tags in aangepaste toepassingen.

## Tien redenen voor het gebruik van codering {#ten-reasons-to-use-tagging}

1. **Inhoud**  ordenen - Etikettering maakt het leven voor auteurs gemakkelijker aangezien zij inhoud met weinig moeite kunnen snel organiseren.
1. **Tags**  organiseren - Terwijl tags inhoud ordenen, ordenen hiërarchische taxonomieën/naamruimten tags.
1. **Deply Organised Tags**  - Met de mogelijkheid om tags en subtags te maken, wordt het mogelijk om volledige taxonomische systemen uit te drukken, inclusief termen, subtermen en hun relaties. Zo kunt u een tweede (of derde) inhoudshiërarchie maken die parallel is aan de officiële inhoudshiërarchie.
1. **Gecontroleerde labeling**  - Tags kunnen worden beheerd door machtigingen toe te passen op tags en/of naamruimten om het maken en de toepassing van tags te regelen.
1. **Flexibele tags toepassen**  - Tags hebben veel namen en gezichten: tags, taxonomie termen, categorieën, labels en nog veel meer. Zij zijn flexibel in hun inhoudsmodel en in de manier waarop zij kunnen worden gebruikt; bijvoorbeeld bij het schetsen van doeldemografie, het categoriseren en classificeren van inhoud of het creëren van een secundaire inhoudshiërarchie.
1. **Verbeterd zoeken**  - De standaardzoekcomponent in AEM bevat over het algemeen gemaakte tags en toegepaste tags waarop filters kunnen worden toegepast om de resultaten te beperken tot de relevante waarden.
1. **SEO Inschakelen**  - tags die zijn toegepast als pagina-eigenschappen worden automatisch weergegeven in de tags van de pagina, zodat deze zichtbaar zijn voor zoekmachines.
1. **Eenvoudig, geavanceerd**  - U kunt eenvoudig tags maken op basis van een woord en de druk op een knop. Daarna kunt u een titel, beschrijving en een onbeperkt label toevoegen om meer semantiek aan de tag toe te voegen.
1. **Core Consistency**  - Het etiketteringssysteem is een kerncomponent van AEM en door alle AEM mogelijkheden gebruikt om inhoud te categoriseren. Verder is de API voor codering beschikbaar voor ontwikkelaars die toepassingen met codering willen maken die toegang hebben tot dezelfde taxonomieën.
1. **Combineert structuur en flexibiliteit**  - AEM is ideaal voor het werken met gestructureerde informatie, door het nesten van pagina&#39;s en paden. Het is even krachtig wanneer het werken met ongestructureerde informatie, toe te schrijven aan de ingebouwde full-text onderzoek. Tags combineren de sterke punten van structuur en flexibiliteit.

Wanneer u de inhoudsstructuur voor een site en het metagegevensschema voor elementen ontwerpt, moet u rekening houden met de lichte en toegankelijke manier waarop u tags kunt toewijzen.

## Labels {#applying-tags} toepassen

In de auteursomgeving, kunnen de auteurs markeringen toepassen door tot de paginaeigenschappen toegang te hebben en één of meerdere markeringen in het **Codes/Sleutelwoorden** gebied in te gaan.

Als u [vooraf gedefinieerde labels](/help/sites-administering/tags.md) wilt toepassen, gebruikt u in het venster **Pagina-eigenschappen** het veld **Codes** en het venster **Codes selecteren**. Het tabblad **Standaardtags** is de standaardnaamruimte, wat betekent dat er geen `namespace-string:` als voorvoegsel is voor de taxonomie.

![Selecteer het venster Codes. gebruik X knoop om de momenteel geselecteerde markeringen te schrappen](assets/chlimage_1-41.png)

### Codes {#publishing-tags} publiceren

Net als bij pagina&#39;s kunt u het volgende uitvoeren op tags en naamruimten:

**Activeren**

* Afzonderlijke tags activeren.

   Net als bij pagina&#39;s moeten nieuwe tags worden geactiveerd voordat deze beschikbaar komen in de publicatieomgeving.

>[!NOTE]
>
>Wanneer u een pagina activeert, wordt automatisch een dialoogvenster geopend waarin u niet-geactiveerde tags die bij de pagina horen, kunt activeren.

**Deactiveren**

* Deactiveer de geselecteerde labels.
