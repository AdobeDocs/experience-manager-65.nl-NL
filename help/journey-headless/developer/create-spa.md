---
title: Optioneel - Hoe kunt u toepassingen voor één pagina maken (SPA) met Adobe Experience Manager
description: In deze optionele vervolg van de Adobe Experience Manager (AEM) Headless Developer Journey leert u hoe AEM koploze levering kunt combineren met traditionele CMS-functies in volledige stapel en hoe u bewerkbare SPA kunt maken met AEM Editor-framework.
exl-id: 91eadda2-b881-4e4a-867f-8c5c54e8f8b4
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Developer
source-git-commit: 984c0a25ea84588b430b3d82ef26d747d4ae5a14
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 0%

---

# Procedure voor het maken van toepassingen voor één pagina (SPA) met AEM {#create-spa}

In deze facultatieve voortzetting van de [ AEM Headless Reis van de Ontwikkelaar, ](overview.md) leert u hoe Adobe Experience Manager (AEM) koploze levering met traditionele full-stack eigenschappen van CMS kan combineren en hoe u editable SPA tot stand kunt brengen gebruikend AEM het kader van de Redacteur van de SPA, en externe SPA kunt integreren, toelatend bewerkingsmogelijkheden zoals vereist.

## Het verhaal tot nu toe {#story-so-far}

Op dit punt, zou u de volledige [ Reis van de Ontwikkelaar van de Zwaartepunt AEM ](overview.md) moeten voltooien en de grondbeginselen van koploze levering in AEM begrijpen met inbegrip van het begrip van:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM eindeloze functies.
* Hoe te om Hoofdloze project te organiseren en te AEM.
* Hoe te om koploze inhoud in AEM te creëren.
* Hoe te om koploze inhoud in AEM terug te winnen en bij te werken.
* Hoe te om met een AEM Zwaardeloos project te leven.

Dus je bent nu ofwel met je eerste AEM Headless-project gaan wonen, of de kennis hebben om dat te doen. Gefeliciteerd!

Waarom leest u deze extra, optionele voortzetting van de reis? Vergelijkbaar, herinnert u eraan dat in [ Begonnen ](getting-started.md#integration-levels), er een korte bespreking over was hoe AEM niet alleen hoofdloze levering en traditionele full-stack modellen steunt, maar ook hybride modellen kan steunen die de voordelen van allebei combineren. Hoewel niet het traditionele model zonder kop, kunnen dergelijke hybride modellen ongekende flexibiliteit aan bepaalde projecten aanbieden.

Dit artikel bouwt op uw kennis van AEM Headless voort door diepgaand te onderzoeken hoe u uw eigen single-page toepassingen (SPA) kunt tot stand brengen die in AEM editable zijn. Op deze manier kunt u inhoud maken en deze zonder problemen leveren aan een SPA, maar dat SPA bewerkbaar blijft in AEM.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe Toepassingen van één pagina worden ontwikkeld gebruikend het kader van AEM SPA Redacteur. Nadat u dit document hebt gelezen, moet u:

* Begrijp de basisfunctie van de SPA Editor.
* Zorg dat u weet aan welke vereisten een volledig bewerkbare SPA voor AEM moet voldoen.
* Begrijp hoe externe SPA in AEM kunnen worden geïntegreerd.
* Begrijp hoe rendering op de server al dan niet moet worden geïmplementeerd.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verschillende vereisten voordat u met SPA begint te werken in AEM.

### Kennis {#knowledge}

* Ervaring op het gebied van ontwikkeling die SPA maakt met React of Angular
* Basisvaardigheden AEM het creëren van de Fragmenten van de Inhoud en het gebruiken van de redacteur
* Ben zeker om het document [ te herzien Kopieer en Zwaartepunt in AEM ](/help/sites-developing/headful-headless.md) om de diverse niveaus van SPA mogelijke integratie te begrijpen.

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA (optioneel, afhankelijk van het gekozen integratiemodel)
* Projectarchetype AEM

## Wat is een SPA? {#what-is-a-spa}

Een toepassing van één pagina (SPA) verschilt van een conventionele pagina in die zin dat deze op client wordt weergegeven en vooral door JavaScript wordt aangedreven, afhankelijk van Ajax-aanroepen om gegevens te laden en de pagina dynamisch bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die asynchroon worden geladen, afhankelijk van gebruikersinteractie met de pagina.

Hierdoor is het minder nodig pagina&#39;s te vernieuwen en wordt de gebruiker een ervaring geboden die naadloos, snel is en meer lijkt op een native app-ervaring.

Met de AEM SPA Editor kunnen front-end ontwikkelaars SPA maken die in een AEM site kunnen worden geïntegreerd, zodat de auteurs van de inhoud de SPA inhoud net zo gemakkelijk kunnen bewerken als elke andere AEM.

## Waarom een SPA? {#why-spa}

Door sneller, vloeiend en meer als een native toepassing te zijn, wordt een SPA een aantrekkelijke ervaring, niet alleen voor de bezoeker van de webpagina, maar ook voor marketers en ontwikkelaars, vanwege de aard van de manier waarop SPA werkt.

Voor een volledige beschrijving van SPA en waarom u hen zou gebruiken, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Hoe AEM handgrepen SPA

Bij het ontwikkelen van toepassingen voor één pagina op AEM wordt ervan uitgegaan dat de ontwikkelaar aan de voorzijde de aanbevolen standaardprocedures voor het maken van een SPA in acht neemt. Als front-end ontwikkelaar, als u deze algemene beste praktijken en een paar AEM-specifieke principes volgt, zal uw SPA met AEM en zijn inhoud-creatie mogelijkheden functioneel zijn.

* **Portability** - zoals met om het even welke componenten, zouden de SPA componenten moeten worden gebouwd om zo draagbaar mogelijk te zijn. De SPA moet met draagbare en herbruikbare onderdelen worden gebouwd.
* **AEM de Structuur van de Plaats van de Stations** - de front-end ontwikkelaar leidt tot componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **Dynamische Rendering** - allen zou het teruggeven dynamisch moeten zijn.
* **Dynamisch Verpletteren** - de SPA is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt die op het worden gebaseerd. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Voor een volledige beschrijving van hoe AEM handvatten SPA, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## De AEM SPA Editor {#aem-spa-editor}

De plaatsen die gebruikend gemeenschappelijke SPA zoals React en Angular worden gebouwd laden hun inhoud via dynamische JSON en verstrekken niet de structuur van de HTML die voor de AEM Redacteur van de Pagina noodzakelijk is om bewerkingscontroles te kunnen plaatsen.

Om het bewerken van SPA binnen AEM mogelijk te maken, is een toewijzing tussen de JSON-uitvoer van de SPA en het inhoudsmodel in de AEM opslagplaats nodig om wijzigingen in de inhoud op te slaan.

SPA ondersteuning in AEM introduceert een dunne JS-laag die communiceert met de SPA JS-code wanneer deze wordt geladen in de Pagina-editor waarmee gebeurtenissen kunnen worden verzonden en de locatie voor de bewerkingsbesturingselementen kan worden geactiveerd om in-context bewerken mogelijk te maken. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort omdat de inhoud van de SPA door als Diensten van de Inhoud moet worden geladen.

Voor een volledige beschrijving van de AEM SPARedacteur, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Bestaande SPA aanpassen {#existing-spas}

Als u een bestaande SPA hebt, AEM ondersteuning voor het insluiten ervan in AEM, zodat deze zichtbaar is voor de auteurs van de inhoud in de AEM Editor. Dit kan handig zijn om de inhoud die ze maken, weer te geven via Content Fragments in de context van de eindtoepassing waarin deze wordt gebruikt.

Bovendien kunt u met slechts kleine wijzigingen bepaalde bewerkingsmogelijkheden voor de externe SPA inschakelen in de AEM Editor.

Met de component RemotePage kan een externe SPA in AEM worden weergegeven.

Voor een volledige beschrijving van hoe te om een externe SPA editable in AEM te maken, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Volgende functies {#what-is-next}

Als u wilt beginnen met het ontwikkelen van uw eigen SPA voor AEM, bekijkt u de volgende documenten:

* [SPA WKND-zelfstudie](/help/sites-developing/spa-wknd.md)
* [Aan de slag met Reageren](/help/sites-developing/spa-getting-started-react.md)
* [Aan de slag met Angular](/help/sites-developing/spa-getting-started-angular.md)

Als u een bestaande SPA moet aanpassen om het in AEM te gebruiken, herzie de volgende documenten:

* [De RemotePage-component](/help/sites-developing/spa-remote-page.md)
* [Een externe SPA bewerken in AEM](/help/sites-developing/spa-edit-external.md)

Zie hieronder voor [ extra middelen ](#additional-resources) die u dieper in SPA onderwerpen in AEM kunnen nemen.

## Aanvullende bronnen {#additional-resources}

Hieronder vindt u een aantal aanvullende bronnen die dieper ingaan op bepaalde concepten die in dit document worden genoemd.

* [ Kopieerbaar en Hoofdloos in AEM ](/help/sites-developing/headful-headless.md) - een beschrijving van de verschillende leveringsmodellen beschikbaar in AEM
* [SPA Inleiding en Analyse.](/help/sites-developing/spa-walkthrough.md) - Een goede inleiding tot SPA in AEM
* [ het Ontwikkelen SPA voor AEM ](/help/sites-developing/spa-architecture.md) - Richtlijnen op hoe te om SPA voor AEM te ontwikkelen
* [ SPA het Overzicht van de Redacteur ](/help/sites-developing/spa-overview.md) - Details van hoe de Redacteur van de SPA werkt
* [ SPA de Documenten van de Verwijzing ](/help/sites-developing/spa-reference-materials.md) - de verwijzingen van JavaScript API en verbindingen aan de open-bron AEM projecten GitHub SPA
* [ Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) - hoe te om de Fragmenten van de Inhoud tot stand te brengen
* [ AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) - Geweven malplaatje dat tot een minimaal, best-practices-gebaseerd project van Adobe Experience Manager (AEM) als uitgangspunt voor uw website leidt
