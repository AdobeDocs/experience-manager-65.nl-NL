---
title: Best practices voor het testen van prestaties
seo-title: Best Practices for Performance Testing
description: In dit artikel worden de algemene strategieën en methoden beschreven die voor het testen van de prestaties worden gebruikt, alsmede enkele instrumenten die beschikbaar zijn om het proces te helpen.
seo-description: This article outlines the overall strategies and methodologies used for performance testing as well as some of the tools that are available to assist in the process.
uuid: ab8720d6-b864-4d00-9e07-2e1699cfe7db
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 669018a0-f6ef-42b2-9c6f-83d7dd5a7095
exl-id: fcac75e1-15c1-4a37-8d43-93c95267b903
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '1898'
ht-degree: 0%

---

# Best practices voor het testen van prestaties{#best-practices-for-performance-testing}

## Inleiding {#introduction}

Het testen van prestaties is een belangrijk deel van om het even welke AEM plaatsing. Afhankelijk van de vereisten van de klant kunnen de prestaties worden getest op de publicatie-instanties, de auteur-instanties of beide.

In deze documentatie worden algemene strategieën en methodologieën voor het uitvoeren van prestatietests beschreven, alsmede enkele instrumenten die door Adobe beschikbaar worden gesteld om het proces te ondersteunen. Tot slot zullen wij enkele hulpmiddelen analyseren die in AEM 6 beschikbaar zijn om met prestaties het stemmen, zowel vanuit een codeanalyse als perspectief van de systeemconfiguratie te helpen.

### Realiteit simuleren {#simulating-reality}

Wat het belangrijkst is wanneer het uitvoeren van prestatietests is ervoor te zorgen dat u een productiemilieu zo dicht mogelijk nastreeft. Hoewel dit vaak moeilijk kan zijn, is het absoluut noodzakelijk de nauwkeurigheid van deze tests te waarborgen. Wanneer het werken aan het ontwerpen van prestatietests, is het belangrijk om de volgende punten in overweging te nemen:

* Productie-achtige inhoud

Veel prestatiemetingen in AEM, zoals de tijd van de vraagreactie, kunnen door de grootte van de inhoud op het systeem worden beïnvloed. Het is belangrijk ervoor te zorgen dat de testomgeving zo dicht mogelijk een kopie van de productiegegevens heeft.

* Productiecode

De AEM versie en hotfixes die in productie worden ingezet, moeten in de testomgeving hetzelfde zijn. Het is ook belangrijk om op de versie van de code te testen die aan productie wordt opgesteld.

* Productieachtige hardware en netwerkconfiguratie

De tests zijn zinloos zonder een omgeving die zoveel mogelijk op de productie lijkt. In het ideale geval moeten de hardwarespecificaties, de netwerkinterfaces, de taakverdelingsmechanismen en de CDN identiek zijn aan de productie in de testomgeving.

* Productiebelasting

Veel prestatieproblemen worden pas zichtbaar wanneer het systeem zwaar belast is. Goede prestatietests moeten de belasting simuleren die de productiesystemen op hun hoogtepunt zullen beleven.

### Doelstellingen instellen {#setting-goals}

Voordat wordt begonnen met het testen van de prestaties, moeten niet-functionele eisen worden vastgesteld om de belasting- en responstijden te bepalen. Als u van een bestaand systeem migreert, zorg ervoor dat de reactietijd aan uw huidige productiewaarden gelijkaardig is. Voor lading, is het best om de huidige pieklading te nemen en te verdubbelen. Hierdoor kan de website goed blijven functioneren terwijl deze groeit.

### Gereedschappen {#tools}

Er zijn veel commercieel verkrijgbare hulpmiddelen voor het testen van prestaties op de markt. Wanneer het runnen van een lading die hulpmiddel produceert, is het belangrijk om ervoor te zorgen dat de computers die de tests uitvoeren voldoende netwerkbandbreedte hebben. Als de testmachine de grenzen van de verbinding bereikt, wordt geen extra belasting in de testomgeving gegenereerd.

#### Testgereedschappen {#testing-tools}

* Adobe **Dag** kan worden gebruikt om belasting te genereren op AEM instanties en prestatiegegevens te verzamelen. Adobe gebruikt het gereedschap om het AEM zelf te testen. De scripts die op de Dag van de Hoek worden uitgevoerd, worden gevormd via bezitsdossiers en JMX XML- dossiers. Zie voor meer informatie de [Tough Day-documentatie](/help/sites-developing/tough-day.md).

* AEM verstrekt uit de vakhulpmiddelen om problematische vragen, verzoeken en foutenmeldingen snel te zien. Zie voor meer informatie de [Diagnosemiddelen](/help/sites-administering/operations-dashboard.md#diagnosis-tools) sectie van de documentatie van het vluchthandboek.
* Apache levert een product genaamd **JMeter** die kunnen worden gebruikt voor prestatie- en belastingtests en functioneel gedrag. Het is open-sourcesoftware en vrij te gebruiken, maar heeft een kleinere functieset dan bedrijfsproducten en een steile leercurve. JMeter is te vinden op de website van Apache op [https://jmeter.apache.org/](https://jmeter.apache.org/)

* **Runner laden** is een belastingstestproduct voor bedrijven. Er is een gratis evaluatieversie beschikbaar. Meer informatie vindt u op [https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview](https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview)

* Gereedschappen voor het testen van taken op basis van cloud, zoals [Neustar](https://www.neustar.biz/services/web-performance/load-testing) kan ook worden gebruikt.
* Wanneer het gaat om het testen van mobiele of responsieve websites, moet een aparte set hulpmiddelen worden gebruikt. Ze werken door de netwerkbandbreedte te vertragen, waardoor langzamere mobiele verbindingen zoals 3G of EDGE worden gesimuleerd. Een van de meer gebruikte instrumenten is:

   * **[Netwerkkoppelingsvoorwaarde](https://nshipster.com/network-link-conditioner/)** - het verstrekt gemakkelijk om UI te gebruiken en werkt op vrij laag niveau op de voorzien van een netwerkstapel. Dit omvat versies voor OS X en iOS;
   * [**Charles**](https://www.charlesproxy.com/) - een proxytoepassing voor foutopsporing op het web die naast verschillende andere toepassingen netwerkvertraging biedt. Versies zijn beschikbaar voor Windows, OS X en Linux.

#### Optimalisatieprogramma&#39;s {#optimization-tools}

**Bewaking**

De [Monitorprestaties](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance) documentatie is een goede bron voor hulpmiddelen en methodes die kunnen worden gebruikt om kwestie en puntgebieden voor het stemmen te diagnostiseren.

**Modus voor ontwikkelaars in Touch UI**

Een van de nieuwe functies in de aanraakinterface van AEM 6 is de Developer Mode. Net zoals ontwerpers kunnen schakelen tussen bewerkings- en voorvertoningsmodi, kunnen ontwikkelaars overschakelen naar de modus voor ontwikkelaars in de gebruikersinterface om de rendertijd voor elk van de componenten op de pagina te zien en stacksporen van eventuele fouten te zien. Voor meer informatie over ontwikkelaarwijze, zie dit [CQ Gems-presentatie](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html?lang=en).

**Het gebruiken van rlog.jar om de verzoeklogboeken te lezen**

Voor een uitgebreidere analyse van de aanvraag wordt een AEM systeem aangemeld. `rlog.jar` kan worden gebruikt om door te zoeken en te sorteren `request.log` bestanden die AEM genereren. Dit jar-bestand wordt samen met een AEM-installatie opgenomen in het dialoogvenster `/crx-quickstart/opt/helpers` map. Voor meer informatie over het hulpmiddel van het logboek en het verzoeklogboek in het algemeen, zie [Toezicht en onderhoud](/help/sites-deploying/monitoring-and-maintaining.md) documentatie.

**Het gereedschap Uitleg query**

De [Het gereedschap Query uitvoeren](/help/sites-administering/operations-dashboard.md#explain-query) in ACS AEM Hulpmiddelen kunnen worden gebruikt om de indexen te bekijken die wanneer het runnen van een vraag worden gebruikt. Dit kan zeer nuttig zijn wanneer het optimaliseren van langzaam lopende vragen.

**PageSpeed-gereedschappen**

De Google PageSpeed-gereedschappen bieden een siteanalyse die voldoet aan de aanbevolen procedures voor paginaprestaties en een insteekmodule die naast de dispatcher op een Apache-instantie kan worden geïnstalleerd voor extra optimalisaties. Zie voor meer informatie de [PaginaSpeed Tools-website](https://developers.google.com/speed/pagespeed/).

## Auteursomgeving {#author-environment}

### Tests uitvoeren {#performing-tests}

Voor het uitvoeren van prestatietests in de auteursomgeving is het nodig dat u de ervaring van productiefouteurs simuleert. Dit betekent dat de auteursinstallaties alle componenten, bundels OSGi, UI aanpassing, douaneindexes en andere toevoegingen moeten bevatten u voor de instanties van de productiesauteur op zijn plaats hebt.

Er zijn vele automatiseringskaders beschikbaar die voor prestaties en lading het testen worden ontworpen. Aangepaste scripts kunnen in deze gereedschappen worden opgenomen en vervolgens worden afgespeeld om een piekaantal auteurs te simuleren die tegelijkertijd vergelijkbare activiteiten voor het maken en activeren van inhoud uitvoeren. U wordt aangeraden het gereedschap Onvoldoende dag te gebruiken om activiteiten te simuleren, zoals het uploaden van duizenden elementen of het activeren van een groot aantal pagina&#39;s.

Voor de soorten milieu&#39;s die vereisten van zwaar activa laden of pagina creatie hebben is het noodzakelijk om hulpmiddelen zoals Dag te gebruiken om ervoor te zorgen dat het milieu efficiënt onder piekbelasting zal werken. [WebDAV](/help/sites-administering/webdav-access.md) is een hulpmiddel dat geen scripting vereist en kan ook worden gebruikt om grote hoeveelheden activa te laden.

#### Specifieke stappen van MongoDB {#mongodb-specific-steps}

Op systemen met MongoDB-backends biedt AEM verschillende [JMX](/help/sites-administering/jmx-console.md) MBeans die moeten worden bewaakt wanneer het uitvoeren van lading of prestatietests:

* De **Geconsolideerde cachestatistieken** MBean. Het kan direct worden betreden door te gaan:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D6%2Cname%3D%22Consolidated+Cache+statistics%22%2Ctype%3D%22ConsolidatedCacheStats%22`

Voor de genoemde cache **Document-Diff**, moet het percentage treffers worden overschreden `.90`. Als de raaksnelheid lager is dan 90%, is het waarschijnlijk dat u de `DocumentNodeStoreService` configuratie. Ondersteuning van Adobe-producten kan optimale instellingen voor uw omgeving aanbevelen.

* De **Statistieken opslagplaats eik** Bon. Het kan direct worden betreden door te gaan:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D16%2Cname%3D%22Oak+Repository+Statistics%22%2Ctype%3D%22RepositoryStats%22`

De **ObservationQueueMaxLength** wordt het aantal gebeurtenissen in de waarnemingswachtrij van Oak gedurende de laatste uren, minuten, seconden en weken weergegeven. Zoek het grootste aantal gebeurtenissen in de sectie &#39;per uur&#39;. Dit getal moet worden vergeleken met het `oak.observation.queue-length` instellen. Als het hoogste getal dat voor de waarnemingswachtrij wordt weergegeven, groter is dan `queue-length` instellen:

1. Maak een bestand met de naam: `com.adobe.granite.repository.impl.SlingRepositoryManager.cfg` met de parameter `oak.observation.queue‐length=50000`
1. Plaats de toepassing onder de map /crx-quickstart/install.

>[!NOTE]
>Zie ook het KB-artikel over [AEM 6,x | Tips voor afstemmen van prestaties](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html)

De standaardinstelling is 10.000, maar de meeste implementaties moeten deze meestal verhogen tot 20.000 of 50.000.

## Publicatie-omgeving {#publish-environment}

### Tests uitvoeren {#performing-tests-1}

Het belangrijkste onderdeel van een implementatie dat moet worden onderworpen aan laadtests, is de eindgebruiker die wordt geconfronteerd met een publicatie- of verzendomgeving.

Automatische testtools van andere bedrijven kunnen worden gebruikt om de prestaties van de website te testen. Met deze gereedschappen kunt u stappen opnemen die gebruikers op de site doorlopen en een groot aantal van deze sessies tegelijk uitvoeren om het standaardladen van een productiewebsite te simuleren.

De meeste productiewebsites beschikken over optimalisaties, zoals caching door verzenders en een netwerk voor het leveren van inhoud. Bij het testen moet u ervoor zorgen dat deze optimalisaties ook beschikbaar zijn voor de testomgeving. Naast het controleren van reactietijden voor de eindgebruikers, moet u ook systeemmetriek op publicatieservers en verzenders controleren om ervoor te zorgen dat het systeem niet door hardwaremiddelen wordt beperkt.

Op een systeem dat geen hoog niveau van verpersoonlijking vereist, zou de verzender de meeste verzoeken in het voorgeheugen onderbrengen. Als gevolg hiervan moet de belasting op het publicatieexemplaar relatief vlak blijven. Als een hoog niveau van verpersoonlijking wordt vereist, wordt het geadviseerd om technologieën zoals iFrames of AJAX verzoeken om de gepersonaliseerde inhoud te gebruiken om zoveel mogelijk verzender caching toe te staan.

Voor basistests kan Apache Bench worden gebruikt om responstijden van webservers te meten en om belasting te creëren voor het meten van zaken zoals geheugenlekken. Zie het voorbeeld in het dialoogvenster [Controledocumentatie](/help/sites-deploying/monitoring-and-maintaining.md#apache-bench).

## Problemen met prestaties oplossen {#troubleshooting-performance-issues}

Nadat u prestatietests op de auteur hebt uitgevoerd, moeten eventuele problemen worden onderzocht, gediagnosticeerd en opgelost. U kunt verschillende gereedschappen en technieken gebruiken bij het uitvoeren van analyses en het aanpakken van problemen:

* U kunt de [Logbestand voor toepassingsprestaties aanvragen](/help/sites-administering/operations-dashboard.md#request-performance) in het vectordashboard. Dit gereedschap kan worden gebruikt om aanvragen voor langzame pagina&#39;s te identificeren
* Analyseer langzame lopende vragen met [Query-prestaties, gereedschap](/help/sites-administering/operations-dashboard.md#query-performance)

* Bekijk de foutlijst voor fouten of waarschuwingen. Zie voor meer informatie [Logboekregistratie](/help/sites-deploying/configure-logging.md)
* De hardwarebronnen van het systeem controleren, zoals geheugen en CPU-gebruik, schijf-I/O of netwerk-I/O. Deze middelen zijn vaak de oorzaken van prestatiesknelpunten
* Optimaliseer de architectuur van de pagina&#39;s en hoe zij worden gericht om het gebruik van URL parameters te minimaliseren om voor zoveel mogelijk caching mogelijk toe te staan
* Volg de [Optimalisatie van prestaties](/help/sites-deploying/configuring-performance.md) en [Tips voor afstemmen van prestaties](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) documentatie

* Als er problemen optreden bij het bewerken van bepaalde pagina&#39;s of componenten op auteur-instanties, gebruikt u de TouchUI-ontwikkelaarsmodus om de pagina in kwestie te inspecteren. Hierdoor wordt een uitsplitsing van elk inhoudsgebied op de pagina en de laadtijd gegenereerd
* Alle JS en CSS op de site miniaturen. Zie deze voor meer informatie over hoe u dit kunt doen [blogbericht](https://blogs.adobe.com/foxes/enable-js-and-css-minification/).
* Elimineer ingesloten CSS en JS uit de componenten. Ze moeten worden opgenomen in en geminiatuurd op de bibliotheken aan de clientzijde om het aantal aanvragen te minimaliseren dat vereist is om de pagina weer te geven
* Gebruik browsergereedschappen, zoals het tabblad Netwerk van Chrome, om de serveraanvragen te inspecteren en te zien welke de langste aanvragen uitvoeren.

Als probleemgebieden zijn geïdentificeerd, kan de toepassingscode worden gecontroleerd op optimalisatie van de prestaties. Om het even welke uit de doos AEM eigenschappen die niet behoorlijk presteren kunnen met de Steun van de Adobe worden behandeld.
