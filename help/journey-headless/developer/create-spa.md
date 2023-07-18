---
title: Optioneel - Hoe kunt u toepassingen voor één pagina maken (SPA) met Adobe Experience Manager
description: In deze optionele vervolg van de Adobe Experience Manager (AEM) Headless Developer Journey leert u hoe AEM koploze levering kunt combineren met traditionele full-stack CMS-functies en hoe u bewerkbare SPA kunt maken met AEM Editor-framework.
exl-id: 91eadda2-b881-4e4a-867f-8c5c54e8f8b4
source-git-commit: d3c40d1452217983b01245ec1c81111a3c4e7295
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---

# Procedure voor het maken van toepassingen voor één pagina (SPA) met AEM {#create-spa}

In deze facultatieve voortzetting van de [AEM Headless Developer Journey,](overview.md) leert u hoe Adobe Experience Manager (AEM) koploze levering kan combineren met traditionele full-stack CMS-functies en hoe u bewerkbare SPA kunt maken met AEM Editor-framework, en externe SPA kunt integreren, waardoor bewerkingsmogelijkheden naar wens zijn.

## Het verhaal tot nu toe {#story-so-far}

Op dit punt had u het volledige [AEM Headless Developer Journey](overview.md) en begrijpen de grondbeginselen van de levering zonder kop in AEM, inclusief inzicht in:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM functies zonder kop.
* Hoe te om Hoofdloze project te organiseren en te AEM.
* Hoe te om koploze inhoud in AEM tot stand te brengen.
* Hoe te om koploze inhoud in AEM terug te winnen en bij te werken.
* Hoe te om met een AEM Zwaardeloos project te leven.

Dus je bent nu ofwel met je eerste AEM Headless-project gaan leven of alle kennis hebben die nodig is om dat te doen. Gefeliciteerd!

Waarom leest u deze extra, optionele voortzetting van de reis? Waarschijnlijk herinnert u zich dat in de [Aan de slag](getting-started.md#integration-levels) we hebben kort besproken hoe AEM niet alleen de levering zonder kop en traditionele full-stack modellen ondersteunt, maar ook hybride modellen die de voordelen van beide combineren. Hoewel niet het traditionele model zonder kop, kunnen dergelijke hybride modellen ongekende flexibiliteit aan bepaalde projecten aanbieden.

Dit artikel bouwt op uw kennis van AEM Headless voort door diepgaand te onderzoeken hoe u uw eigen single-page toepassingen (SPA) kunt tot stand brengen die in AEM editable zijn. Op deze manier kunt u inhoud maken en deze zonder problemen leveren aan een SPA, maar dat SPA bewerkbaar blijft in AEM.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe Toepassingen van één pagina worden ontwikkeld gebruikend het kader van de AEM SPA van de Redacteur. Nadat u dit document hebt gelezen, moet u:

* Begrijp de basisfunctie van de SPA Editor.
* Zorg dat u weet aan welke vereisten een volledig bewerkbare SPA voor AEM moet voldoen.
* Begrijp hoe externe SPA in AEM kunnen worden geïntegreerd.
* Begrijp hoe rendering op de server al dan niet moet worden geïmplementeerd.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verschillende vereisten voordat u met SPA begint te werken in AEM.

### Kennis {#knowledge}

* Ervaring op het gebied van ontwikkeling die SPA maakt met React of Angular
* Basisvaardigheden AEM het creëren van de Fragmenten van de Inhoud en het gebruiken van de redacteur
* Controleer of u het document wilt reviseren [Hoofdletters en headless in AEM](/help/sites-developing/headful-headless.md) inzicht te krijgen in de verschillende niveaus van SPA mogelijke integratie.

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA (optioneel, afhankelijk van het gekozen integratiemodel)
* Projectarchetype AEM

## Wat is een SPA? {#what-is-a-spa}

Een toepassing van één pagina (SPA) verschilt van een conventionele pagina in die zin dat deze wordt weergegeven op de client en voornamelijk door JavaScript wordt aangedreven. Hierbij wordt uitgegaan van Ajax-aanroepen om gegevens te laden en de pagina dynamisch bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die asynchroon worden geladen, afhankelijk van gebruikersinteractie met de pagina.

Hierdoor is het minder nodig pagina&#39;s te vernieuwen en wordt de gebruiker een ervaring geboden die naadloos, snel is en meer lijkt op een native app-ervaring.

Met de AEM SPA Editor kunnen front-end ontwikkelaars SPA maken die in een AEM site kunnen worden geïntegreerd, zodat de auteurs van de inhoud de SPA inhoud net zo gemakkelijk kunnen bewerken als elke andere AEM.

## Waarom een SPA? {#why-spa}

Door sneller, vloeiend en meer als een native toepassing te zijn, wordt een SPA een aantrekkelijke ervaring, niet alleen voor de bezoeker van de webpagina, maar ook voor marketers en ontwikkelaars, vanwege de aard van de manier waarop SPA werkt.

Voor een volledige beschrijving van SPA en waarom u deze zou gebruiken, raadpleegt u de [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## Hoe AEM handgrepen SPA

Bij het ontwikkelen van toepassingen voor één pagina op AEM wordt ervan uitgegaan dat de ontwikkelaar aan de voorzijde de beste werkwijzen volgt bij het maken van een SPA. Als u als front-end ontwikkelaar deze algemene best practices en een paar AEM-specifieke principes volgt, zal uw SPA functioneren met AEM en zijn mogelijkheden voor het schrijven van inhoud.

* **Overdraagbaarheid** - De onderdelen van de SPA moeten zo draagbaar mogelijk zijn, net als alle andere onderdelen. De SPA moet met draagbare en herbruikbare onderdelen worden gebouwd.
* **Sitestructuur AEM stations** - De front-end ontwikkelaar maakt componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **Dynamische rendering** - Alle rendering moet dynamisch zijn.
* **Dynamische routering** - De SPA is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt gebaseerd op het. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Voor een volledige beschrijving van hoe AEM handvatten SPA, zie [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## De AEM SPA Editor {#aem-spa-editor}

De plaatsen die gebruikend gemeenschappelijke SPA zoals React en Angular worden gebouwd laden hun inhoud via dynamische JSON en verstrekken niet de structuur van de HTML die noodzakelijk voor de AEM Redacteur van de Pagina is om bewerkingscontroles te kunnen plaatsen.

Om het bewerken van SPA binnen AEM mogelijk te maken, is een toewijzing tussen de JSON-uitvoer van de SPA en het inhoudsmodel in de AEM opslagplaats nodig om wijzigingen in de inhoud op te slaan.

SPA ondersteuning in AEM introduceert een dunne JS-laag die communiceert met de SPA JS-code wanneer deze wordt geladen in de Pagina-editor waarmee gebeurtenissen kunnen worden verzonden en de locatie voor de bewerkingsbesturingselementen kan worden geactiveerd om in-context bewerken mogelijk te maken. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort omdat de inhoud van de SPA door als Diensten van de Inhoud moet worden geladen.

Voor een volledige beschrijving van de AEM SPA Editor raadpleegt u de [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## Bestaande SPA aanpassen {#existing-spas}

Als u een bestaande SPA hebt, AEM ondersteuning voor het insluiten ervan in AEM, zodat deze zichtbaar is voor de auteurs van de inhoud in de AEM Editor. Dit kan handig zijn om de inhoud die ze maken, weer te geven via Content Fragments in de context van de eindtoepassing waarin deze wordt gebruikt.

Bovendien kunt u met slechts kleine wijzigingen bepaalde bewerkingsmogelijkheden voor de externe SPA inschakelen in de AEM Editor.

Met de component RemotePage kan een externe SPA in AEM worden weergegeven.

Voor een volledige beschrijving van hoe u een externe SPA bewerkbaar kunt maken in AEM, raadpleegt u de [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## Volgende functies {#what-is-next}

Als u wilt beginnen met het ontwikkelen van uw eigen SPA voor AEM, bekijkt u de volgende documenten:

* [SPA WKND-zelfstudie](/help/sites-developing/spa-wknd.md)
* [Aan de slag met Reageren](/help/sites-developing/spa-getting-started-react.md)
* [Aan de slag met Angular](/help/sites-developing/spa-getting-started-angular.md)

Als u een bestaande SPA moet aanpassen om het in AEM te gebruiken, herzie de volgende documenten:

* [De RemotePage-component](/help/sites-developing/spa-remote-page.md)
* [Een externe SPA bewerken in AEM](/help/sites-developing/spa-edit-external.md)

Zie hieronder voor [extra middelen](#additional-resources) dat kan u dieper op SPA onderwerpen in AEM brengen.

## Aanvullende bronnen {#additional-resources}

Hieronder vindt u een aantal aanvullende bronnen die dieper ingaan op bepaalde concepten die in dit document worden genoemd.

* [Hoofdletters en headless in AEM](/help/sites-developing/headful-headless.md) - Een beschrijving van de verschillende leveringsmodellen die in AEM beschikbaar zijn
* [SPA Inleiding en Analyse.](/help/sites-developing/spa-walkthrough.md) - Een goede inleiding tot SPA in AEM
* [SPA ontwikkelen voor AEM](/help/sites-developing/spa-architecture.md) - Richtsnoeren voor de ontwikkeling van SPA voor AEM
* [Overzicht SPA Editor](/help/sites-developing/spa-overview.md) - Bijzonderheden over de werking van de SPA Editor
* [Rendering op de server](/help/sites-developing/spa-ssr.md) - Hoe te om SSR voor AEM SPA te vormen
* [Referentiedocumenten SPA](/help/sites-developing/spa-reference-materials.md) - JavaScript API verwijzingen en verbindingen aan de open bron AEM SPA projecten GitHub
* [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) - Inhoudsfragmenten maken
* [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) - Gemaakt sjabloon dat een minimaal, op best practices gebaseerd Adobe Experience Manager-project (AEM) maakt als startpunt voor uw website
