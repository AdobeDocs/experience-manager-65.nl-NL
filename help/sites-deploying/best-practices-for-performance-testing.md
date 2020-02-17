---
title: Best practices voor het testen van prestaties
seo-title: Best practices voor het testen van prestaties
description: In dit artikel worden de algemene strategieën en methoden beschreven die voor het testen van de prestaties worden gebruikt, alsmede enkele instrumenten die beschikbaar zijn om het proces te helpen.
seo-description: In dit artikel worden de algemene strategieën en methoden beschreven die voor het testen van de prestaties worden gebruikt, alsmede enkele instrumenten die beschikbaar zijn om het proces te helpen.
uuid: ab8720d6-b864-4d00-9e07-2e1699cfe7db
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 669018a0-f6ef-42b2-9c6f-83d7dd5a7095
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Best practices voor het testen van prestaties{#best-practices-for-performance-testing}

## Inleiding {#introduction}

Prestatietests vormen een belangrijk onderdeel van elke AEM-implementatie. Afhankelijk van de vereisten van de klant kunnen de prestaties worden getest op de publicatie-instanties, de auteur-instanties of beide.

In deze documentatie worden algemene strategieën en methoden beschreven voor het uitvoeren van prestatietests, alsmede enkele hulpprogramma&#39;s die Adobe beschikbaar stelt om u te helpen bij het proces. Tot slot zullen wij enkele hulpmiddelen analyseren die in AEM 6 beschikbaar zijn om met prestaties het stemmen, zowel vanuit een codeanalyse als perspectief van de systeemconfiguratie te helpen.

### Realiteit simuleren {#simulating-reality}

Wat het belangrijkst is wanneer het uitvoeren van prestatietests is ervoor te zorgen dat u een productiemilieu zo dicht mogelijk nastreeft. Hoewel dit vaak moeilijk kan zijn, is het absoluut noodzakelijk de nauwkeurigheid van deze tests te waarborgen. Wanneer het werken aan het ontwerpen van prestatietests, is het belangrijk om de volgende punten in overweging te nemen:

* Productie-achtige inhoud

Veel prestatiemetingen in AEM, zoals de tijd van de vraagreactie, kunnen door de grootte van de inhoud op het systeem worden beïnvloed. Het is belangrijk ervoor te zorgen dat de testomgeving zo dicht mogelijk een kopie van de productiegegevens heeft.

* Productiecode

De AEM-versie en hotfixes die in productie worden gebruikt, moeten in de testomgeving hetzelfde zijn. Het is ook belangrijk om op de versie van de code te testen die aan productie wordt opgesteld.

* Productieachtige hardware en netwerkconfiguratie

De tests zijn zinloos zonder een omgeving die zoveel mogelijk op de productie lijkt. In het ideale geval moeten de hardwarespecificaties, de netwerkinterfaces, de taakverdelingsmechanismen en de CDN identiek zijn aan de productie in de testomgeving.

* Productiebelasting

Veel prestatieproblemen worden pas zichtbaar wanneer het systeem zwaar belast is. Goede prestatietests moeten de belasting simuleren die de productiesystemen op hun hoogtepunt zullen beleven.

### Doelstellingen instellen {#setting-goals}

Voordat wordt begonnen met het testen van de prestaties, moeten niet-functionele eisen worden vastgesteld om de belasting- en responstijden te bepalen. Als u van een bestaand systeem migreert, zorg ervoor dat de reactietijd aan uw huidige productiewaarden gelijkaardig is. Voor lading, is het best om de huidige pieklading te nemen en te verdubbelen. Hierdoor kan de website goed blijven functioneren terwijl deze groeit.

### Opties {#tools}

Er zijn veel commercieel verkrijgbare hulpmiddelen voor het testen van prestaties op de markt. Wanneer het runnen van een lading die hulpmiddel produceert, is het belangrijk om ervoor te zorgen dat de computers die de tests uitvoeren voldoende netwerkbandbreedte hebben. Als de testmachine de grenzen van de verbinding bereikt, wordt geen extra belasting in de testomgeving gegenereerd.

#### Testgereedschappen {#testing-tools}

* Met het gereedschap **Hogere dag** van Adobe kunt u belasting genereren op AEM-instanties en prestatiegegevens verzamelen. Het AEM-engineeringteam van Adobe gebruikt het programma voor het testen van de belasting van het AEM-product zelf. De scripts die op de Dag van de Hoek worden uitgevoerd, worden gevormd via bezitsdossiers en JMX XML- dossiers. Raadpleeg de documentatie [van](/help/sites-developing/tough-day.md)Tough Day voor meer informatie.

* AEM verstrekt uit de dooshulpmiddelen om problematische vragen, verzoeken en foutenmeldingen snel te zien. Zie de sectie [Diagnosetools](/help/sites-administering/operations-dashboard.md#diagnosis-tools) in de documentatie van het vluchthandboek voor meer informatie.
* Apache biedt een product met de naam **JMeter** dat kan worden gebruikt voor prestatie- en belastingtests en functioneel gedrag. Het is open-sourcesoftware en vrij te gebruiken, maar heeft een kleinere functieset dan bedrijfsproducten en een steile leercurve. JMeter is te vinden op de website van Apache op [https://jmeter.apache.org/](https://jmeter.apache.org/)

* **Load Runner** is een testproduct voor het laden van bedrijfsniveau. Er is een gratis evaluatieversie beschikbaar. Meer informatie is te vinden op [https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview](https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview)

* U kunt ook gereedschappen voor laadtests op basis van cloud gebruiken, zoals [Neustar](https://www.neustar.biz/services/web-performance/load-testing) .
* Wanneer het gaat om het testen van mobiele of responsieve websites, moet een aparte set hulpmiddelen worden gebruikt. Ze werken door de netwerkbandbreedte te vertragen, waardoor langzamere mobiele verbindingen zoals 3G of EDGE worden gesimuleerd. Een van de meer gebruikte instrumenten is:

   * **[De Voorwaardiger](https://nshipster.com/network-link-conditioner/)**van de Verbinding van het netwerk - het verstrekt gemakkelijk om UI te gebruiken en werkt op een vrij laag niveau op de voorzien van een netwerkstapel. Het omvat versies voor OS X en iOS;[](https://nshipster.com/network-link-conditioner/)
   * [**Charles **](https://www.charlesproxy.com/)- een Web het zuiveren volmachtstoepassing die naast verscheidene andere toepassingen, netwerkthrottling verstrekt. Versies zijn beschikbaar voor Windows, OS X en Linux.[](https://www.charlesproxy.com/)

#### Optimalisatieprogramma&#39;s {#optimization-tools}

**Toezicht**

De documentatie van de Prestaties [van de](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance) Controle is een goede middel voor hulpmiddelen en methodes die kunnen worden gebruikt om kwestie en puntgebieden voor het stemmen te diagnostiseren.

**Modus voor ontwikkelaars in Touch UI**

Een van de nieuwe functies in de aanraakinterface van AEM 6 is de Developer Mode. Net zoals ontwerpers kunnen schakelen tussen bewerkings- en voorvertoningsmodi, kunnen ontwikkelaars overschakelen naar de modus voor ontwikkelaars in de gebruikersinterface om de rendertijd voor elk van de componenten op de pagina te zien en stacksporen van eventuele fouten te zien. Zie deze [CQ Gems-presentatie](https://docs.adobe.com/content/ddc/en/gems/aem-6-0-developer-mode.html)voor meer informatie over de modus Ontwikkelaar.

**Het gebruiken van rlog.jar om de verzoeklogboeken te lezen**

Voor een uitgebreidere analyse van de aanvraag logt een AEM-systeem aan, `rlog.jar` kunt u de door AEM gegenereerde `request.log` bestanden doorzoeken en sorteren. Dit jar-bestand wordt opgenomen in een AEM-installatie in de `/crx-quickstart/opt/helpers` map. Voor meer informatie over rlog hulpmiddel en het verzoeklogboek in het algemeen, zie de [Controle en het Onderhouden](/help/sites-deploying/monitoring-and-maintaining.md) documentatie.

**Het gereedschap Uitleg query**

Het [Uitdrukkelijke hulpmiddel](/help/sites-administering/operations-dashboard.md#explain-query) van de Vraag in Hulpmiddelen ACS AEM kan worden gebruikt om de indexen te bekijken die wanneer het runnen van een vraag worden gebruikt. Dit kan zeer nuttig zijn wanneer het optimaliseren van langzaam lopende vragen.

**PageSpeed-gereedschappen**

De PageSpeed-programma&#39;s van Google bieden een siteanalyse voor het volgen van de aanbevolen procedures voor paginaprestaties en een insteekmodule die naast de dispatcher op een Apache-instantie kan worden geïnstalleerd voor extra optimalisaties. Zie de website [PageSpeed Tools voor meer informatie](https://developers.google.com/speed/pagespeed/).

## Auteursomgeving {#author-environment}

### Tests uitvoeren {#performing-tests}

Voor het uitvoeren van prestatietests in de auteursomgeving is het nodig dat u de ervaring van productiefouteurs simuleert. Dit betekent dat de auteursinstallaties alle componenten, bundels OSGi, UI aanpassing, douaneindexes en andere toevoegingen moeten bevatten u voor de instanties van de productiesauteur op zijn plaats hebt.

Er zijn vele automatiseringskaders beschikbaar die voor prestaties en lading het testen worden ontworpen. Aangepaste scripts kunnen in deze gereedschappen worden opgenomen en vervolgens worden afgespeeld om een piekaantal auteurs te simuleren die tegelijkertijd vergelijkbare activiteiten voor het maken en activeren van inhoud uitvoeren. U wordt aangeraden het gereedschap Onvoldoende dag te gebruiken om activiteiten te simuleren, zoals het uploaden van duizenden elementen of het activeren van een groot aantal pagina&#39;s.

Voor de soorten milieu&#39;s die vereisten van zwaar activa laden of pagina creatie hebben is het noodzakelijk om hulpmiddelen zoals Dag te gebruiken om ervoor te zorgen dat het milieu efficiënt onder piekbelasting zal werken. [WebDAV](/help/sites-administering/webdav-access.md) is een hulpmiddel dat geen scripting vereist en kan ook worden gebruikt om grote hoeveelheden activa te laden.

#### Specifieke stappen van MongoDB {#mongodb-specific-steps}

Op systemen met MongoDB-backends biedt AEM verschillende [JMX](/help/sites-administering/jmx-console.md) MBans die moeten worden bewaakt tijdens het uitvoeren van belasting- of prestatietests:

* De **geconsolideerde Statistieken** van het Geheime voorgeheugen MBean. Het kan direct worden betreden door te gaan:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D6%2Cname%3D%22Consolidated+Cache+statistics%22%2Ctype%3D%22ConsolidatedCacheStats%22`

Voor het geheime voorgeheugen genoemd **document-Diff**, zou het klaptarief over moeten zijn `.90`. Als het raakpercentage lager is dan 90%, is het waarschijnlijk dat u de `DocumentNodeStoreService` configuratie moet wijzigen. Ondersteuning van Adobe-producten kan optimale instellingen voor uw omgeving aanbevelen.

* Het **oak Repository Statistics** Mbean. Het kan direct worden betreden door te gaan:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D16%2Cname%3D%22Oak+Repository+Statistics%22%2Ctype%3D%22RepositoryStats%22`

De **sectie ObservationQueueMaxLength** zal het aantal gebeurtenissen in de de observatierij van Oak over de laatste uren, notulen, seconden en weken tonen. Zoek het grootste aantal gebeurtenissen in de sectie &quot;per uur&quot;. Dit aantal moet met het `oak.observation.queue-length` plaatsen worden vergeleken die in de component **SlingRepositoryManager** in de console [](/help/sites-deploying/web-console.md)OSGi kan worden gevonden. Als het hoogste aantal dat voor de waarnemingswachtrij wordt weergegeven de `queue-length` instelling overschrijdt, neemt u contact op met de Technische Ondersteuning van Adobe voor hulp bij het verhogen van de instelling. De standaardinstelling is 1.000, maar de meeste implementaties moeten deze meestal verhogen tot 20.000 of 50.000.

## Publicatie-omgeving {#publish-environment}

### Tests uitvoeren {#performing-tests-1}

Het belangrijkste onderdeel van een implementatie dat moet worden onderworpen aan laadtests, is de eindgebruiker die wordt geconfronteerd met een publicatie- of verzendomgeving.

Automatische testtools van andere bedrijven kunnen worden gebruikt om de prestaties van de website te testen. Met deze gereedschappen kunt u stappen opnemen die gebruikers op de site doorlopen en een groot aantal van deze sessies tegelijk uitvoeren om het standaardladen van een productiewebsite te simuleren.

De meeste productiewebsites beschikken over optimalisaties, zoals caching door verzenders en een netwerk voor het leveren van inhoud. Bij het testen moet u ervoor zorgen dat deze optimalisaties ook beschikbaar zijn voor de testomgeving. Naast het controleren van reactietijden voor de eindgebruikers, moet u ook systeemmetriek op publicatieservers en verzenders controleren om ervoor te zorgen dat het systeem niet door hardwaremiddelen wordt beperkt.

Op een systeem dat geen hoog niveau van verpersoonlijking vereist, zou de verzender de meeste verzoeken in het voorgeheugen onderbrengen. Als gevolg hiervan moet de belasting op het publicatieexemplaar relatief vlak blijven. Als een hoog niveau van verpersoonlijking wordt vereist, wordt het geadviseerd om technologieën zoals iFrames of AJAX verzoeken voor de gepersonaliseerde inhoud te gebruiken zodat zoveel mogelijk verzender caching mogelijk wordt.

Voor basistests kan Apache Bench worden gebruikt om responstijden van webservers te meten en om belasting te creëren voor het meten van zaken zoals geheugenlekken. Zie het voorbeeld in de [monitoringdocumentatie](/help/sites-deploying/monitoring-and-maintaining.md#apache-bench)voor meer informatie.

## Problemen met prestaties oplossen {#troubleshooting-performance-issues}

Nadat u prestatietests op de auteur hebt uitgevoerd, moeten eventuele problemen worden onderzocht, gediagnosticeerd en opgelost. U kunt verschillende gereedschappen en technieken gebruiken bij het uitvoeren van analyses en het aanpakken van problemen:

* U kunt het logboek [van de Prestaties van het](/help/sites-administering/operations-dashboard.md#request-performance) Verzoek in het Dashboard van Verrichtingen inspecteren. Dit gereedschap kan worden gebruikt om aanvragen voor langzame pagina&#39;s te identificeren
* Langzame vragen analyseren met het gereedschap [Query-prestaties](/help/sites-administering/operations-dashboard.md#query-performance)

* Bekijk de foutlijst voor fouten of waarschuwingen. For more information, see [Logging](/help/sites-deploying/configure-logging.md)
* De hardwarebronnen van het systeem controleren, zoals geheugen en CPU-gebruik, schijf-I/O of netwerk-I/O. Deze middelen zijn vaak de oorzaken van prestatiesknelpunten
* Optimaliseer de architectuur van de pagina&#39;s en hoe zij worden gericht om het gebruik van URL parameters te minimaliseren om voor zoveel mogelijk caching mogelijk toe te staan
* Volg de documentatie over het optimaliseren van [prestaties](/help/sites-deploying/configuring-performance.md) en het afstemmen van [prestaties](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html)

* Als er problemen optreden bij het bewerken van bepaalde pagina&#39;s of componenten op auteur-instanties, gebruikt u de TouchUI-ontwikkelaarsmodus om de pagina in kwestie te inspecteren. Hierdoor wordt een uitsplitsing van elk inhoudsgebied op de pagina en de laadtijd gegenereerd
* Alle JS en CSS op de site miniaturen. Zie dit [blogbericht](https://blogs.adobe.com/foxes/enable-js-and-css-minification/)voor meer informatie over hoe u dit kunt doen.
* Elimineer ingesloten CSS en JS uit de componenten. Ze moeten worden opgenomen in en geminiatuurd op de bibliotheken aan de clientzijde om het aantal aanvragen te minimaliseren dat vereist is om de pagina weer te geven
* Gebruik browsergereedschappen zoals het tabblad Netwerk van Chrome om de serveraanvragen te inspecteren en te zien welke de langste aanvragen uitvoeren.

Als probleemgebieden zijn geïdentificeerd, kan de toepassingscode worden gecontroleerd op optimalisatie van de prestaties. Alle AEM-functies in de verpakking die niet correct werken, kunnen worden verwerkt met ondersteuning van Adobe.
