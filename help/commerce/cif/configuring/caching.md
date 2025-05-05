---
title: Caching en prestaties
description: Leer over de verschillende beschikbare configuraties om GraphQL en inhoud het in cache plaatsen toe te laten om de prestaties van uw handelsimplementatie te optimaliseren.
exl-id: ecce64bf-5960-4ddb-b6e3-dad401038c11
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
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

Wanneer het vormen caching voor componenten, moet de geheim voorgeheugennaam de naam van de **volmacht** componenten zijn die u in uw project bepaalt.

Alvorens de cliënt een verzoek van GraphQL verzendt, controleert het als dat **nauwkeurig** zelfde verzoek van GraphQL reeds in het voorgeheugen ondergebracht is en misschien de caching reactie terugkeert. Om overeen te komen, MOET de GraphQL- verzoek precies aanpassen, namelijk de vraag, verrichtingsnaam (als om het even welk), variabelen (als om het even welk) moeten allen aan het caching verzoek gelijk zijn, en ook alle kopballen van douaneHTTP die zouden kunnen worden geplaatst MOET het zelfde zijn. De Adobe Commerce `Store` -header MOET bijvoorbeeld overeenkomen.

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

Wanneer het overwegen van de [ opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) wordt gebruikt. Neem nota van het gebruik van de naam van de componentenvolmacht `venia/components/structure/navigation`, en **niet** de naam van de CIF navigatiecomponent (`core/cif/components/structure/navigation/v1/navigation`).

Caching voor andere componenten zou op projectbasis, gewoonlijk in coördinatie met caching moeten worden bepaald die op het niveau van Dispatcher wordt gevormd. Herinner dat er geen actieve ongeldigverklaring van deze geheime voorgeheugens is, zodat zou de caching duur zorgvuldig moeten worden geplaatst. Er zijn geen standaardwaarden die overeenkomen met alle mogelijke projecten en gebruiksgevallen. Zorg ervoor dat u een caching strategie op het projectniveau bepaalt die het best de vereisten van uw project aanpast.

## Dispatcher Caching {#dispatcher}

Het in cache plaatsen AEM pagina&#39;s of fragmenten in [ AEM Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL) is een beste praktijk voor om het even welk AEM project. Doorgaans is dit afhankelijk van validatietechnieken die ervoor zorgen dat inhoud die in AEM is gewijzigd, correct wordt bijgewerkt in de Dispatcher. Dit is een kernonderdeel van de cachestrategie voor AEM Dispatcher.

Naast zuivere AEM beheerde inhoud CIF een pagina kan typisch handelsgegevens tonen die dynamisch van Adobe Commerce via GraphQL wordt opgehaald. Hoewel de paginastructuur zelf misschien nooit verandert, kan de commerciële inhoud veranderen, bijvoorbeeld, als sommige productgegevens (zoals naam of prijs) in Adobe Commerce veranderen.

Om ervoor te zorgen dat de CIF pagina&#39;s voor een beperkte hoeveelheid tijd in AEM Dispatcher kunnen worden in het voorgeheugen ondergebracht, adviseren wij daarom het gebruik van [ Op tijd gebaseerde Invalidatie van het Geheime voorgeheugen ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL#configuring-time-based-cache-invalidation-enablettl) (die ook als op TTL-Gebaseerd caching wordt bekend) wanneer het in het voorgeheugen onderbrengen CIF pagina&#39;s in de AEM Dispatcher. Deze eigenschap kan in AEM met het gebruiken van het extra [ ACS AEM Commons ](https://adobe-consulting-services.github.io/acs-aem-commons/) pakket worden gevormd.

Met op TTL gebaseerde caching, bepaalt een ontwikkelaar typisch één of veelvoudige caching duur voor geselecteerde AEM pagina&#39;s. Dit zorgt ervoor dat CIF pagina&#39;s slechts in het voorgeheugen ondergebracht in AEM Dispatcher tot de gevormde duur zijn en dat de inhoud vaak zal worden bijgewerkt.

>[!NOTE]
>
>Hoewel gegevens aan de serverzijde door de AEM Dispatcher in de cache kunnen worden opgeslagen, worden in sommige CIF componenten zoals `product` , `productlist` en `searchresults` doorgaans altijd de productprijzen opnieuw opgehaald in een verzoek om een clientbrowser wanneer de pagina wordt geladen. Dit zorgt ervoor dat cruciale dynamische inhoud altijd wordt opgehaald bij het laden van een pagina.

## Aanvullende bronnen

- [ de opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia)
- [ GraphQL caching configuratie ](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [ AEM Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL)
