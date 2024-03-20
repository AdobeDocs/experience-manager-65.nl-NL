---
title: Caching en prestaties
description: Leer over de verschillende beschikbare configuraties om GraphQL en inhoud het in cache plaatsen toe te laten om de prestaties van uw handelsimplementatie te optimaliseren.
exl-id: ecce64bf-5960-4ddb-b6e3-dad401038c11
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Caching en prestaties {#caching}

## Component &amp; GraphQL Response Caching {#graphql}

De AEM CIF Core Components hebben al ingebouwde ondersteuning voor het in cache plaatsen van GraphQL-reacties voor afzonderlijke componenten. Deze functie kan worden gebruikt om het aantal GraphQL backend vraag met een grote factor te verminderen. Een efficiënte caching kan vooral voor het herhalen van vragen zoals het terugwinnen van de categorieboom voor een navigatiecomponent of het halen van alle beschikbare samenvoegingen/facetwaarden worden bereikt die op de productonderzoek en categoriepagina&#39;s worden getoond.

Voor de AEM CIF de Componenten van de Kern, wordt het in cache plaatsen gevormd op componentenbasis, zodat is het mogelijk om te controleren als (en hoe lang) de verzoeken/de reacties van GraphQL voor elke component in het voorgeheugen worden opgeslagen. Het is ook mogelijk om het caching gedrag voor de diensten te bepalen OSGi gebruikend de cliënt van GraphQL.

### Configuratie

Zodra gevormd voor een bepaalde component, begint het geheime voorgeheugen GraphQL vragen en antwoorden zoals die door elke ingang van de geheim voorgeheugenconfiguratie worden bepaald op te slaan. De grootte van het geheime voorgeheugen en de in het voorgeheugen onderbrengingsduur van elke ingang moeten op een projectbasis worden bepaald, afhankelijk bijvoorbeeld, op hoe vaak de catalogusgegevens zouden kunnen veranderen, hoe kritiek het is dat een component altijd de recentste mogelijke gegevens toont, etc. Merk op dat er geen geheim voorgeheugenongeldigverklaring is, zodat ben zorgvuldig wanneer het plaatsen van de geheim voorgeheugenduur.

Wanneer het vormen caching voor componenten, moet de geheim voorgeheugennaam de naam van zijn **proxy** componenten die u in uw project definieert.

Voordat de client een GraphQL-aanvraag verzendt, wordt gecontroleerd of **exact** dezelfde GraphQL-aanvraag is al in de cache opgeslagen en retourneert mogelijk de in de cache opgeslagen reactie. Om overeen te komen, MOET de GraphQL- verzoek precies aanpassen, namelijk de vraag, verrichtingsnaam (als om het even welk), variabelen (als om het even welk) moeten allen aan het caching verzoek gelijk zijn, en ook alle kopballen van douaneHTTP die zouden kunnen worden geplaatst MOET het zelfde zijn. De Adobe Commerce `Store` koptekst MOET overeenkomen.

### Voorbeelden

Wij adviseren dat om wat caching voor de onderzoeksdienst te vormen die alle beschikbare samenvoegingen/facetwaarden haalt die op het productonderzoek en categoriepagina&#39;s worden getoond. Deze waarden veranderen doorgaans alleen wanneer een nieuw kenmerk bijvoorbeeld wordt toegevoegd aan producten, zodat de duur voor deze cachevermelding &quot;groot&quot; kan zijn als de set met productkenmerken niet vaak wordt gewijzigd. Hoewel dit projectspecifiek is, beveelt de Adobe waarden aan van een paar minuten in projectontwikkelingsfasen en een paar uur in stabiele productiesystemen.

Dit wordt typisch gevormd met de volgende geheim voorgeheugeningang:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Een ander voorbeeldscenario waar de eigenschap GraphQl in het voorgeheugen onderbrengend wordt geadviseerd om te worden gebruikt is de navigatiecomponent omdat het de zelfde vraag van GraphQL op alle pagina&#39;s verzendt. In dit geval wordt de cachevermelding doorgaans ingesteld op:

```
venia/components/structure/navigation:true:10:600
```

Bij het overwegen van de [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) wordt gebruikt. Let op het gebruik van de naam van de componentproxy `venia/components/structure/navigation`, en **niet** de naam van de CIF navigatiecomponent (`core/cif/components/structure/navigation/v1/navigation`).

Caching voor andere componenten zou op een projectbasis, gewoonlijk in coördinatie met caching moeten worden bepaald die op het niveau van de Verzender wordt gevormd. Herinner dat er geen actieve ongeldigverklaring van deze geheime voorgeheugens is, zodat zou de caching duur zorgvuldig moeten worden geplaatst. Er zijn geen standaardwaarden die overeenkomen met alle mogelijke projecten en gebruiksgevallen. Zorg ervoor dat u een caching strategie op het projectniveau bepaalt die het best de vereisten van uw project aanpast.

## Caching van Dispatcher {#dispatcher}

Pagina&#39;s of fragmenten in cache AEM in het deelvenster [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) is een beste praktijk voor om het even welk AEM project. Doorgaans is dit afhankelijk van validatietechnieken die ervoor zorgen dat inhoud die in AEM is gewijzigd, correct wordt bijgewerkt in de Dispatcher. Dit is een kernelement van de strategie voor het in cache plaatsen van AEM Dispatcher.

Naast zuivere AEM beheerde inhoud CIF een pagina kan typisch handelsgegevens tonen die dynamisch van Adobe Commerce via GraphQL wordt opgehaald. Hoewel de paginastructuur zelf misschien nooit verandert, kan de commerciële inhoud veranderen, bijvoorbeeld, als sommige productgegevens (zoals naam of prijs) in Adobe Commerce veranderen.

Om ervoor te zorgen dat CIF pagina&#39;s gedurende een beperkte periode in de AEM Dispatcher in cache kunnen worden opgeslagen, raden we u daarom aan om het volgende te doen: [Op tijd gebaseerde invalidatie van cache](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-time-based-cache-invalidation-enablettl) (ook wel op TTL gebaseerd in cache plaatsen genoemd) wanneer het in cache plaatsen van CIF pagina&#39;s in de AEM Dispatcher. Deze functie kan worden geconfigureerd in AEM met de extra [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) pakket.

Met op TTL gebaseerde caching, bepaalt een ontwikkelaar typisch één of veelvoudige caching duur voor geselecteerde AEM pagina&#39;s. Dit zorgt ervoor dat CIF pagina&#39;s slechts in het voorgeheugen ondergebracht in de AEM Dispatcher tot de gevormde duur zijn en dat de inhoud vaak zal worden bijgewerkt.

>[!NOTE]
>
>Hoewel gegevens aan de serverzijde door de AEM Dispatcher in het cachegeheugen kunnen worden opgeslagen, zijn er enkele CIF `product`, `productlist`, en `searchresults` componenten halen doorgaans altijd de productprijzen opnieuw op in een browserverzoek aan de clientzijde wanneer de pagina wordt geladen. Dit zorgt ervoor dat cruciale dynamische inhoud altijd wordt opgehaald bij het laden van een pagina.

## Aanvullende bronnen

- [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [GraphQL-cacheconfiguratie](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)
