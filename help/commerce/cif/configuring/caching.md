---
title: Caching en prestaties
description: Leer over de verschillende beschikbare configuraties om GrafiekQL en inhoudcaching toe te laten om de prestaties van uw handelsimplementatie te optimaliseren.
translation-type: tm+mt
source-git-commit: d92a635d41cf1b14e109c316bd7264cf7d45a9fe
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 2%

---

# Caching &amp; Prestaties {#caching}

## Component &amp; GraphQL Response Caching {#graphql}

De AEM CIF Core Components hebben reeds ingebouwde steun voor caching GraphQL reacties voor individuele componenten. Deze eigenschap kan worden gebruikt om het aantal graafQL achterste vraag door een grote factor te verminderen. Een efficiënte caching kan vooral voor het herhalen van vragen zoals het terugwinnen van de categorieboom voor een navigatiecomponent of het halen van alle beschikbare samenvoegingen/facetwaarden worden bereikt die op de productonderzoek en categoriepagina&#39;s worden getoond.

Voor de AEM componenten van de Kern van CIF, wordt het in cache plaatsen gevormd op componentenbasis, zodat is het mogelijk om te controleren als (en hoe lang) de verzoeken/de reacties GraphQL voor elke component in het voorgeheugen worden opgeslagen. Het is ook mogelijk om het caching gedrag voor de diensten te bepalen OSGi gebruikend de cliënt GraphQL.

### Configuratie

Zodra gevormd voor een bepaalde component, begint het geheime voorgeheugen het opslaan van vragen GraphQL en reacties zoals die door elke ingang van de geheim voorgeheugenconfiguratie worden bepaald. De grootte van het geheime voorgeheugen en de caching duur van elke ingang moeten op een projectbasis worden bepaald, afhankelijk bijvoorbeeld van hoe vaak de catalogusgegevens zouden kunnen veranderen, hoe kritiek het is dat een component altijd de recentste mogelijke gegevens, enz. toont. Merk op dat er geen geheim voorgeheugenongeldigverklaring is, zo zorgvuldig wanneer het plaatsen van de geheim voorgeheugenduur is.

Wanneer het vormen caching voor componenten, moet de geheim voorgeheugennaam de naam van **proxy** componenten zijn die u in uw project bepaalt.

Alvorens de cliënt een verzoek GraphQL verzendt, zal het controleren of dat **exact** het zelfde verzoek GraphQL reeds in het voorgeheugen ondergebracht is en zal misschien de caching reactie terugkeren. Om aan elkaar te passen, MOET het verzoek GraphQL precies aanpassen, namelijk de vraag, verrichtingsnaam (als om het even welk), variabelen (als om het even welk) moeten allen aan het caching verzoek gelijk zijn, en ook alle kopballen van douaneHTTP die zouden kunnen worden geplaatst MOET het zelfde zijn. De koptekst Magento `Store` MOET bijvoorbeeld overeenkomen.

### Voorbeelden

Wij adviseren dat om wat caching voor de onderzoeksdienst te vormen die alle beschikbare samenvoegingen/facetwaarden haalt die op het productonderzoek en categoriepagina&#39;s worden getoond. Deze waarden veranderen gewoonlijk slechts wanneer een nieuw attribuut bijvoorbeeld aan producten wordt toegevoegd, zodat kan de duur voor deze geheim voorgeheugeningang &quot;groot&quot;zijn als de reeks productattributen niet vaak verandert. Terwijl dit project-specifiek is, adviseren wij waarden van een paar minuten in projectontwikkelingsfasen en een paar uren op stabiele productiesystemen.

Dit wordt typisch gevormd met de volgende geheim voorgeheugeningang:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Een ander voorbeeldscenario waar de eigenschap GraphQl in het voorgeheugen onderbrengend wordt geadviseerd om te worden gebruikt is de navigatiecomponent omdat het de zelfde vraag GraphQL op alle pagina&#39;s verzendt. In dit geval wordt de cachevermelding doorgaans ingesteld op:

```
venia/components/structure/navigation:true:10:600
```

wanneer wordt overwogen [Venia Reference store](https://github.com/adobe/aem-cif-guides-venia) wordt gebruikt. Noteer het gebruik van de naam van de componentproxy `venia/components/structure/navigation` en **not** de naam van de CIF-navigatiecomponent (`core/cif/components/structure/navigation/v1/navigation`).

Caching voor andere componenten zou op een projectbasis, gewoonlijk in coördinatie met caching moeten worden bepaald die op het niveau van de Verzender wordt gevormd. Herinner dat er geen actieve ongeldigverklaring van deze geheime voorgeheugens is, zodat zou de caching duur zorgvuldig moeten worden geplaatst. Er zijn geen standaardwaarden voor één grootte die overeenkomen met alle mogelijke projecten en gebruiksgevallen. Zorg ervoor dat u een caching strategie op het projectniveau bepaalt die het best de vereisten van uw project aanpast.

## In cache plaatsen {#dispatcher}

Het in cache plaatsen van AEM pagina&#39;s of fragmenten in de [AEM Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html) is een aanbevolen werkwijze voor elk AEM project. Doorgaans is dit afhankelijk van validatietechnieken die ervoor zorgen dat inhoud die in AEM is gewijzigd, correct wordt bijgewerkt in de Dispatcher. Dit is een kernelement van de strategie voor het in cache plaatsen van AEM Dispatcher.

Naast zuivere AEM beheerde inhoud CIF kan een pagina commerciële gegevens typisch tonen die dynamisch van Magento via GraphQL wordt gehaald. Hoewel de paginastructuur zelf misschien nooit verandert, kan de commerciële inhoud veranderen, bijvoorbeeld, als sommige productgegevens (naam, prijs, enz.) in Magento veranderen.

Om ervoor te zorgen dat de CIF- pagina&#39;s voor een beperkte hoeveelheid tijd in de AEM verzender kunnen worden in het voorgeheugen ondergebracht, adviseren wij daarom het gebruik van [Op tijd gebaseerde Invalidation van het Geheime voorgeheugen](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-time-based-cache-invalidation-enablettl) (ook genoemd als op TTL-Gebaseerd caching) wanneer het in het voorgeheugen onderbrengen van CIF pagina&#39;s in de AEM Verzender. Deze eigenschap kan in AEM met het gebruiken van het extra [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) pakket worden gevormd.

Met op TTL gebaseerde caching, bepaalt een ontwikkelaar typisch één of veelvoudige caching duur voor geselecteerde AEM pagina&#39;s. Dit zorgt ervoor dat de pagina&#39;s CIF slechts in het voorgeheugen onder in de AEM verzender tot de gevormde duur worden gebracht en dat de inhoud vaak zal worden bijgewerkt.

>[!NOTE]
>
>Hoewel gegevens aan de serverzijde in de cache kunnen worden opgeslagen door de AEM, halen bepaalde CIF-componenten zoals `product`, `productlist` en `searchresults` doorgaans altijd de productprijzen opnieuw op in een verzoek aan de clientbrowser wanneer de pagina wordt geladen. Dit zorgt ervoor dat cruciale dynamische inhoud altijd wordt opgehaald bij het laden van een pagina.

## Aanvullende bronnen

- [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Configuratie van GraphQL-caching](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [AEM Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html)
