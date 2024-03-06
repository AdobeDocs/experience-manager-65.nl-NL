---
title: Pad naar uw eerste ervaring met AEM zonder kop
description: In dit deel van de AEM Headless Developer Journey zult u de stappen begrijpen voor het implementeren van uw eerste headless ervaring in AEM met planningsoverwegingen en leert u ook best practices om uw pad zo vloeiend mogelijk te maken.
exl-id: 64a87b6b-67ff-4d88-9dfb-c3e5de65bbe6
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '1951'
ht-degree: 0%

---

# Pad naar uw eerste ervaring met AEM zonder kop {#path-to-first-experience}

In dit deel van het [AEM Headless Developer Journey,](overview.md) u zult begrijpen hoe u uw eerste headless ervaring in AEM met planningsoverwegingen kunt implementeren en zult ook best practices leren om uw pad zo vloeiend mogelijk te maken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM zonder kop: [Aan de slag met AEM headless](getting-started.md) U leerde de basistheorie van wat een krantenloze CMS is en u zou nu moeten:

* Begrijp de grondbeginselen van AEM functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u moet voldoen om AEM functies zonder kop te gebruiken.
* Wees op de hoogte van AEM integratieniveaus zonder kop.
* U kunt uw project definiëren in termen van bereik.

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u hoe te om uw eigen AEM hoofdloze project voor te bereiden.

## Doelstelling {#objective}

Dit document helpt u de stappen begrijpen nodig om uw eerste project uit te voeren. Na het lezen moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen om zonder kop in AEM uit te voeren.
* Zorg dat u weet welke gereedschappen en AEM nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

## Vereisten {#requirements}

Voordat u doorgaat met dit document, moet u controleren of u het vorige document hebt gereviseerd in de AEM Headless Developer Journey. [Aan de slag met AEM headless](getting-started.md) zorg ervoor dat u:

* Voldoe aan de vermelde vereisten.
* Heb uw eigen projectdefinitie met inbegrip van werkingsgebied, rollen, en prestaties overwogen.

## Planning voor succes {#planning-for-success}

Als u uw eerste AEM project zonder kop wilt starten, moet u ervoor zorgen dat u een inhoudsmodel hebt dat de personalisatie en updates die u op al uw kanalen wilt maken, ondersteunt.

Afzonderlijk van AEM, wilt u ook ervoor zorgen u een juiste ontwikkelomgeving opstelling hebt als u een cliënt-zijtoepassing bouwt zodat kunt u uw cliënt tegen API vraag aan AEM testen.

### Inhoudsmodellen en API&#39;s definiëren {#defining-models}

U wilt een consistente ervaring opdoen en gepersonaliseerde campagnes over kanalen beheren, zodat u elk afzonderlijk kanaal en oppervlak kunt bekijken als een eigen specifieke inhoudsstructuur om aan te leveren. Nochtans heeft het hebben van elk kanaal zijn eigen inhoudsmodel uitdagend om te handhaven.

In plaats daarvan, zou u moeten nadenken hoe de inhoud op verschillende oppervlakten op het organiseren van beginsel zoals merk en producthiërarchieën, categorieën van goederen of oppervlakten, of stappen in de klantenreis wordt verwant. Als u bijvoorbeeld een reeks oppervlakken hebt die een specifiek merk auto&#39;s ondersteunen dat u maakt, kunt u beginnen met een inhoudsmodel voor algemene informatie die geldt voor de hele auto en vervolgens meer - specifieke elementen hebben, zoals de inhoud die nodig is wanneer de auto wordt gestart tot wanneer er serviceproblemen zijn. Een dergelijk model zal de overerving van de algemene inhoud van het automerk afdwingen en tegelijk verschuivingen mogelijk maken op basis van de specifieke context die nodig is. Het helpt ook bij het beheer in de toekomst van updates voor deze inhoud, aangezien u controle kunt afdwingen op basis van rollen zoals de algemene markator of productmanager voor het hele automerk tegenover een auteur die verantwoordelijk is voor de &quot;startervaring&quot;.

Zodra u het inhoudsmodel en de duidelijke mening op de diverse cliënten hebt moet de inhoud worden opgezocht aan, moet u ervoor zorgen de GraphQL/APIs verbonden aan de toegang tot van diverse van het inhoudsmodel aan alle cliënten worden gepubliceerd die deze inhoud nodig hebben. Er zijn verschillende opties voor de toegang tot bepaalde inhoud. U kunt om een specifiek stuk van inhoud verzoeken dat statisch is die caching van de inhoud en hogere prestaties toelaat. U kunt ook inhoud aanvragen die dynamisch wordt gegenereerd en waarvoor meer verwerkingstijd nodig is. Zorg ervoor dat de cliënten APIs gebruiken die voor hun bedrijfsbehoeften het meest efficiënt zijn.

## Inzicht krijgen in uw omgevingen {#understanding-environments}

Binnen AEM zijn er drie soorten omgevingen: ontwikkeling, staging en productie.

De ontwikkelomgevingen (u kunt meerdere omgevingen hebben) zijn een veilige plek om te experimenteren en ideeën uit te proberen. Tijdens de beginfase van het project, adviseert de Adobe het gebruiken van de ontwikkelomgevingen om variaties van inhoudsmodellen te proberen en te zien die de voorgenomen output voor de oppervlakten verstrekken.

De het opvoeren omgeving voor hoofdloze projecten wordt gebruikt voor het bevestigen van nieuwe AEM productreleases alvorens zij aan productie uitrollen. Een bijgewerkte lijst van de modellen van de productie inhoud daar en een ondergroep van de inhoud houden, zodat kunt u teruggegeven dossiers JSON hebben om van hen te vergelijken nog de zelfde output verstrekken, aangezien u veranderingen aanbrengt of de AEM versie veranderingen introduceert

Productie is de plaats waar inhoudsauteurs hun werkelijke inhoud maken en beheren. Modelwijzigingen in de productie moeten met zorg en met achterwaartse compatibiliteit worden uitgevoerd.

Tijdens de ontwikkelingsfase wordt u aangeraden met een ontwikkelings- en testomgeving te werken. Als u overschakelt naar het testen van de prestaties, wilt u overschakelen naar de productieomgeving.

### Samenwerking tussen ontwikkelaars en makers van inhoud {#cooperation}

Ontwikkelaars hebben een AEM ontwikkelomgeving nodig die is ingesteld met de populaire inhoudsmodellen. De ontwikkelaar ontwikkelt de client die inhoud vanuit AEM headless zal verbruiken terwijl de makers van de inhoud de inhoud nog steeds maken. Daarom zijn de API-definities heel belangrijk. Door de AEM SDK te gebruiken, kan de ontwikkelaar een testhaak tot stand brengen zodat de cliënt en de eenheidstests kunnen worden gecreeerd om ervoor te zorgen de cliënt de inhoud behoorlijk kan teruggeven.

Inhoudsauteurs maken inhoud op basis van de inhoudsmodellen die zijn gedefinieerd in de testomgeving. Met het ontwerpgereedschap voor inhoudsfragmenten zou de auteur een inhoudsfragment maken of een bestaand inhoudsfragment bewerken. Alvorens het te publiceren, kan de auteur voorproef hoe het in de cliënt door met de ontwikkelaar te werken om het inhoudsmodel op ontwikkeling te duwen of opstelling een ontwikkelaarmilieu enkel voor auteurs aan voorproef hoe het in de cliënt zou kijken.

## Instellen {#setup}

Voordat u aan de slag gaat met headless in AEM, moet u ervoor zorgen dat alle vereiste functies zijn ingeschakeld. In deze sectie wordt beschreven wat er nodig is. De daadwerkelijke stappen om deze stappen te verwezenlijken worden later gedetailleerd in [AEM Headless Developer Journey.](#overview.md)

U kunt ook optioneel de [extra middelen](#additional-resources) voor meer informatie over de afzonderlijke onderwerpen .

### Configuratie {#configuration}

1. Inhoudsfragmenten inschakelen
1. GraphQL inschakelen
1. De Headless SDK instellen

## Uw eerste AEM headless-app implementeren

Dit is een overzicht van wat nodig is om uw eerste app zonder koppen te implementeren met AEM om uw inhoud te leveren. Hoe u deze stappen uitvoert, wordt in latere delen van de Headless Developer Journey gedetailleerd beschreven.

1. Modellen voor inhoudsfragmenten maken
1. Inhoudsfragmenten maken
1. Query-inhoud uitvoeren met GraphQL

## Aanbevolen procedures {#best-practices}

Een project zonder kop is niet alleen succesvol vanwege de geïmplementeerde technologie, maar ook vanwege goede planning en projectbestuur. Hier volgt een aantal aanbevolen procedures voor auteurs en ontwikkelaars van inhoud om hiermee rekening te houden wanneer u uw project plant.

### Uw inhoud ordenen {#organizing-content}

* Maak uw structuur zo complex als nodig maar houd deze zo eenvoudig mogelijk. Eenvoudigere inhoudsstructuren helpen het beheer van inhoud te stroomlijnen en de systeemprestaties te verbeteren.
* Prioriteit geven aan het hergebruik van inhoud in uw strategie. Maak submodellen en inhoudsverwijzingen die opnieuw kunnen worden gebruikt op meerdere modellen en kanalen op een hoger niveau.
* Maak inhoudsstructuren zo duidelijk mogelijk, zodat de auteurs van de inhoud snel kunnen leren en zich kunnen aanpassen aan ontwerptaken.
* Als u toegangsbeperkingen hebt, probeert u het inhoudsmodel uit te lijnen met de toegangsvereisten.
* Wanneer u toegangsvereisten hebt, zouden zij uw inhoudshiërarchie moeten drijven. Groepeer de inhoud die door dezelfde groep personen wordt bewerkt.
* Groepeer vergelijkbare inhoud in een map.
   * Het is waarschijnlijker dat een auteur van inhoud bestaande inhoud kopieert en plakt om nieuwe inhoud te maken. Als u dit in dezelfde map doet, wordt het efficiënter.
   * AEM staat toe dat modellen per map worden ingesteld, zodat de **Nieuw maken** tonen alleen de modellen die op die locatie worden ondersteund.
* Het maken van nieuwe inhoudsfragmenten in de In-line Content Fragment Editor kan worden vereenvoudigd als de hoofdmap is ingesteld in het model. Dan moet de arts geen plaats kiezen, maar enkel een naam verstrekken en kan beginnen de nieuwe verwijzing uit te geven.

### Inhoud ontwerpen {#authoring}

* Voor kanaalspecifieke versies van uw inhoud kunt u overwegen variaties in inhoudsfragmenten te gebruiken. Variaties worden gesynchroniseerd met de inhoudstramien om het beheer van inhoudswijzigingen te stroomlijnen.
* Andere producenten van inhoud uitnodigen om inhoud te beoordelen en feedback te geven met annotaties en opmerkingen, die beschikbaar zijn in de fragmenteditor van de inhoud en globaal zijn voor fragmenten in de Admin Console van inhoudsfragmenten.
* Houd de zaken met zo weinig mogelijk verplichte elementen in beweging. Verplichte elementen kunnen de workflow blokkeren.

### Globale inhoud ontwerpen {#localization}

* Vaststellen van regels en bestuur voor het vertalen van inhoud. Om systeemlading te verminderen, vertaal als asynchroon proces dat in langere intervallen kan worden in werking gesteld. Zorg ervoor dat u tijd hebt voor de kwaliteitscontrole voor lokalisatie en voor het corrigeren van fouten.
* Maak gebruik van alle mogelijkheden die uw vertaaltechnologie biedt en die u kunt integreren met AEM, zoals vertaalgeheugen.
* Begrijp als rijke media inhoud, zoals beelden en video&#39;s, localisatie vereist.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen om zonder kop in AEM uit te voeren.
* Zorg dat u weet welke gereedschappen en AEM nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

Wij willen dat u op deze grondkennis voortbouwt om de kracht en de flexibiliteit van AEM Headless volledig te begrijpen zodat u ervan kunt profiteren voor uw eigen projecten. Hiervoor hebt u opties.

### Kies uw eigen avontuur {#choose-your-path}

Wat uw het leren stijl ook moge zijn, de Adobe wil dat u slaagt als u aan de slag gaat met uw AEM headless project.

* Als u liever wilt doorgaan **meer informatie over concepten zonder kop en AEM technologieën zonder kop**, moet u doorgaan met uw AEM zonder kop als u het document opnieuw bekijkt [Hoe te om Uw Inhoud als Modellen van de Inhoud te modelleren AEM](model-your-content.md) waar u leert hoe u de inhoudsstructuur in AEM modelleert.
* Als u liever **leren door te doen**, kunt u naar de [Aan de slag met AEM praktische zelfstudie zonder hoofd](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) waar u rechtstreeks in AEM Zwaardeloze ontwikkeling door een eenvoudig project zult springen om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden naar het volgende gedeelte van de ontwikkeling zonder kop te gaan door het document te bekijken [Hoe te om uw inhoud als AEM inhoudsmodellen te modelleren,](model-your-content.md) hieronder volgen enkele aanvullende , optionele bronnen die dieper ingaan op bepaalde in dit document genoemde concepten , maar die niet nodig zijn om verder te gaan op de weg zonder kop .

* [AEM doorsnedenloze vertaalreis](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een ruim inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient en hoe u deze kunt vertalen.
* [Headless Development voor AEM Sites](/help/sites-developing/headless/introduction.md) - Een korte inleiding om de ontwikkelaar van AEM Headless te oriënteren met de noodzakelijke eigenschappen
* [Tutorials zonder kop AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - Gebruik deze praktische zelfstudies om te verkennen hoe u de verschillende opties kunt gebruiken om inhoud aan eindpunten zonder kop met AEM te leveren en te kiezen wat bij u past.
* [Beheer van inhoud zonder koppen met GraphQL API&#39;s](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses) - Volg deze cursus voor een overzicht van de GraphQL API die in AEM is geïmplementeerd. Verificatie via AdobeID is vereist.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql) - Dit GitHub-project bevat voorbeeldtoepassingen die AEM GraphQL API&#39;s markeren.
* [Aan de slag met koploze gids](/help/sites-developing/headless/introduction.md#getting-started) - Een snelle inleiding tot AEM functies zonder kop voor gebruikers die al bekend zijn met AEM.
* [Modellen voor inhoudsfragmenten maken](/help/assets/content-fragments/content-fragments-models.md) - Technische documentatie over modellen van inhoudsfragmenten
* [Inhoudsfragmenten maken](/help/assets/content-fragments/content-fragments.md) - Technische documentatie over inhoudsfragmenten
* [Query-inhoud uitvoeren met GraphQL](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) - Technische documentatie over de GraphQL API
* De [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
