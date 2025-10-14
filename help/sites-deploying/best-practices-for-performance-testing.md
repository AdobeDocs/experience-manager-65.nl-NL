---
title: Best practices voor het testen van prestaties
description: Leer meer over de algemene strategieën en methoden die worden gebruikt voor het testen van de prestaties en enkele gereedschappen die beschikbaar zijn om het proces te helpen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: fcac75e1-15c1-4a37-8d43-93c95267b903
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 8f638eb384bdca59fb6f4f8990643e64f34622ce
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 0%

---

# Best practices voor het testen van prestaties{#best-practices-for-performance-testing}

## Inleiding {#introduction}

Prestatietests vormen een belangrijk onderdeel van elke AEM-implementatie. Afhankelijk van de vereisten van de klant kunnen de prestaties worden getest op de publicatie-instanties, de auteur-instanties of beide.

In deze documentatie worden algemene strategieën en methodologieën beschreven voor het uitvoeren van prestatietests en een aantal van de hulpmiddelen die door Adobe beschikbaar worden gesteld om het proces te helpen. Tot slot lees een analyse van de hulpmiddelen die in AEM 6 beschikbaar zijn om met prestaties het stemmen, zowel vanuit een codeanalyse als perspectief van de systeemconfiguratie te helpen.

### Realiteit simuleren {#simulating-reality}

Wanneer het doen van prestatietests, zorg ervoor dat u een productiemilieu zo dicht mogelijk nastreeft. Hoewel een dergelijke taak vaak moeilijk kan zijn, is het noodzakelijk de nauwkeurigheid van deze tests te waarborgen. Wanneer het werken aan het ontwerpen van prestatietests, is het belangrijk om de volgende punten in overweging te nemen:

* Productie-achtige inhoud

Veel prestatiemetingen in AEM, zoals de tijd van de vraagreactie, kunnen door de grootte van de inhoud op het systeem worden beïnvloed. Het is belangrijk ervoor te zorgen dat de testomgeving zo dicht mogelijk een kopie van de productiegegevens heeft.

* Productiecode

De AEM-versie en de in productie genomen hotfixes moeten in de testomgeving hetzelfde zijn. Het is ook belangrijk om op de versie van de code te testen die aan productie wordt opgesteld.

* Productieachtige hardware en netwerkconfiguratie

De tests zijn zinloos zonder een omgeving die zoveel mogelijk op de productie lijkt. In het ideale geval moeten de hardwarespecificaties, de netwerkinterfaces, de taakverdelingsmechanismen en de CDN identiek zijn aan de productie in de testomgeving.

* Productiebelasting

Veel prestatieproblemen worden pas zichtbaar wanneer het systeem zwaar belast is. Goede prestatietests moeten de belasting simuleren die de productiesystemen op hun hoogtepunt hebben.

### Doelstellingen instellen {#setting-goals}

Voordat wordt begonnen met het testen van de prestaties, moeten niet-functionele eisen worden vastgesteld om de belasting- en responstijden te bepalen. Als u van een bestaand systeem migreert, zorg ervoor dat de reactietijden aan uw huidige productiewaarden gelijkaardig zijn. Voor lading, is het best om de huidige pieklading te nemen en te verdubbelen. Zo zorgt u ervoor dat de website goed kan blijven functioneren terwijl deze groeit.

### Gereedschappen {#tools}

Er zijn veel commercieel verkrijgbare hulpmiddelen voor het testen van prestaties op de markt. Wanneer het runnen van een lading die hulpmiddel produceert, is het belangrijk om ervoor te zorgen dat de computers die de tests uitvoeren voldoende netwerkbandbreedte hebben. Anders wordt, zodra de testmachine de grenzen van zijn verbinding bereikt, geen extra belasting opgewekt op de testomgeving.

#### Testgereedschappen {#testing-tools}

* Het hulpmiddel van de Dag van de Tough van Adobe **&#x200B;**&#x200B;kan worden gebruikt om lading op de instanties van AEM te produceren en prestatiesgegevens te verzamelen. Het technische team van Adobe AEM gebruikt het gereedschap voor het testen van de belasting van het AEM-product zelf. De scripts die op de Dag van de Hoek worden uitgevoerd, worden gevormd via bezitsdossiers en JMX XML- dossiers. Voor meer informatie, zie de [&#x200B; documentatie van de Dag van de Hoek &#x200B;](/help/sites-developing/tough-day.md).

* AEM biedt de vakgereedschappen uit om snel problematische query&#39;s, verzoeken en foutberichten weer te geven. Voor meer informatie, zie de [&#x200B; sectie van Hulpmiddelen van de Diagnose &#x200B;](/help/sites-administering/operations-dashboard.md#diagnosis-tools) van de documentatie van het Dashboard van Verrichtingen.
* Apache verstrekt een product genoemd **JMeter** dat voor prestaties en lading het testen, en functioneel gedrag kan worden gebruikt. Het is open-sourcesoftware en vrij te gebruiken, maar heeft een kleinere functieset dan bedrijfsproducten en een steile leercurve. JMeter kan op de website van Apache in [&#x200B; https://jmeter.apache.org/ &#x200B;](https://jmeter.apache.org/) worden gevonden

* Het laden van de website testende hulpmiddelen zoals [&#x200B; Vercara &#x200B;](https://vercara.com/website-performance-management) kan ook worden gebruikt.
* Bij het testen van mobiele of responsieve websites moet een aparte set gereedschappen worden gebruikt. Ze werken door de netwerkbandbreedte te vertragen, waardoor langzamere mobiele verbindingen zoals 3G of EDGE worden gesimuleerd. Tot de meer gebruikte gereedschappen behoren onder meer:

   * **[Voorwaardiger van de Verbinding van het Netwerk &#x200B;](https://nshipster.com/network-link-conditioner/)** - het verstrekt gemakkelijk om UI te gebruiken en werkt op een vrij laag niveau op de voorzien van een netwerkstapel. Dit omvat versies voor OS X en iOS;
   * [**Karel** &#x200B;](https://www.charlesproxy.com/) - een Web het zuiveren volmachtstoepassing die naast verscheidene andere toepassingen, netwerkthrottling verstrekt. Versies zijn beschikbaar voor Windows, OS X en Linux®.

#### Optimalisatieprogramma&#39;s {#optimization-tools}

**Controle**

De [&#x200B; documentatie van de Prestaties van de Controle &#x200B;](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance) is een goed middel voor hulpmiddelen en methodes die kunnen worden gebruikt om kwestie en puntgebieden voor het stemmen te diagnostiseren.

**de Wijze van de Ontwikkelaar in Aanraak UI**

Een van de nieuwe functies in de aanraakinterface van AEM 6 is de Developer Mode. Net zoals ontwerpers kunnen schakelen tussen bewerkings- en voorvertoningsmodi, kunnen ontwikkelaars overschakelen naar de modus voor ontwikkelaars in de gebruikersinterface. Zo kunt u de rendertijd voor elk van de componenten op de pagina zien en stacksporen van fouten zien. Voor meer informatie over ontwikkelaarwijze, zie deze [&#x200B; CQ Gems presentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html?lang=nl-NL).

**Gebruikend rlog.jar om de verzoeklogboeken** te lezen

Voor een uitgebreidere analyse van de aanvraag kunt u `rlog.jar` gebruiken om de `request.log` -bestanden te doorzoeken en te sorteren die AEM genereert. Dit jar-bestand wordt opgenomen in een AEM-installatie in de map `/crx-quickstart/opt/helpers` . Voor meer informatie over logboekhulpmiddel en het verzoeklogboek over het algemeen, zie [&#x200B; Controle en het Onderhouden van &#x200B;](/help/sites-deploying/monitoring-and-maintaining.md) documentatie.

**het Uitleg Hulpmiddel van de Vraag**

Het [&#x200B; Verklaar hulpmiddel van de Vraag &#x200B;](/help/sites-administering/operations-dashboard.md#explain-query) in ACS AEM Tools kan worden gebruikt om de indexen te bekijken die wanneer het runnen van een vraag worden gebruikt. Dit hulpmiddel is nuttig wanneer het optimaliseren van langzaam lopende vragen.

**PageSpeed Hulpmiddelen**

De Google PageSpeed-gereedschappen bieden een siteanalyse die voldoet aan de aanbevolen procedures voor paginaprestaties en een insteekmodule die naast de Dispatcher op een Apache-instantie kan worden geïnstalleerd voor extra optimalisaties.
Zie de [&#x200B; Website van Hulpmiddelen PageSpeed &#x200B;](https://developers.google.com/speed).

## Auteursomgeving {#author-environment}

### Tests uitvoeren {#performing-tests}

Als u de prestaties wilt testen in de auteursomgeving, is het nodig dat u de ervaring van productieauteurs simuleert. Namelijk moeten de auteursinstallaties alle componenten, bundels OSGi, aanpassing UI, douaneindexen, en om het even welke andere toevoegingen bevatten u op zijn plaats voor de instanties van de productiauteur hebt.

Er zijn vele automatiseringskaders beschikbaar die voor prestaties en lading het testen worden ontworpen. Aangepaste scripts kunnen in deze gereedschappen worden opgenomen en vervolgens worden afgespeeld om een piekaantal auteurs te simuleren die tegelijkertijd vergelijkbare activiteiten voor het maken en activeren van inhoud uitvoeren. U wordt aangeraden het gereedschap Onvoldoende dag te gebruiken om activiteiten te simuleren, zoals het uploaden van duizenden elementen of het activeren van een groot aantal pagina&#39;s.

Voor de soorten milieu&#39;s die vereisten van zwaar activa laden of pagina creatie hebben, is het noodzakelijk om hulpmiddelen zoals de Dag van de Stevige te gebruiken. Dit zorgt ervoor dat de omgeving efficiënt werkt bij piekbelasting. [&#x200B; WebDAV &#x200B;](/help/sites-administering/webdav-access.md) is een hulpmiddel dat geen scripting vereist en kan ook worden gebruikt om grote hoeveelheden activa te laden.

#### Specifieke stappen van MongoDB {#mongodb-specific-steps}

Op systemen met de steunen MongoDB, verstrekt AEM verscheidene [&#x200B; JMX &#x200B;](/help/sites-administering/jmx-console.md) MBeans die moeten worden gecontroleerd wanneer het uitvoeren van lading of prestatietests:

* De **Geconsolideerde Statistieken van het Geheime voorgeheugen** MBean. Het kan direct worden betreden door te gaan:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D6%2Cname%3D%22Consolidated+Cache+statistics%22%2Ctype%3D%22ConsolidatedCacheStats%22`

Voor het geheime voorgeheugen genoemd **document-Afschuiving**, zou het slagtarief over `.90` moeten zijn. Als de raaksnelheid lager is dan 90%, is het waarschijnlijk dat u de `DocumentNodeStoreService` -configuratie moet bewerken. Ondersteuning van Adobe-producten kan optimale instellingen voor uw omgeving aanbevelen.

* De **Statistieken van de Bewaarplaats van Oak** boon. Het kan direct worden betreden door te gaan:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D16%2Cname%3D%22Oak+Repository+Statistics%22%2Ctype%3D%22RepositoryStats%22`

De **ObservationQueueMaxLength** sectie toont het aantal gebeurtenissen in de de observatierij van Oak over de laatste uren, notulen, seconden, en weken. Zoek het grootste aantal gebeurtenissen in de sectie &quot;per uur&quot;. Vergelijk dit getal met de instelling `oak.observation.queue-length` . Als het hoogste getal dat voor de waarnemingswachtrij wordt weergegeven, de instelling `queue-length` overschrijdt:

1. Maak een bestand met de naam: `com.adobe.granite.repository.impl.SlingRepositoryManager.cfg` dat de parameter bevat `oak.observation.queue‐length=50000`
1. Plaats de toepassing onder de map /crx-quickstart/install.

>[!NOTE]
>Zie [&#x200B; AEM 6.x | Tips voor afstemmen van prestaties &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=nl-NL)

De standaardinstelling is 10.000, maar de meeste implementaties moeten deze verhogen tot 20.000 of 50.000.

## Publicatie-omgeving {#publish-environment}

### Tests uitvoeren {#performing-tests-1}

Het belangrijkste onderdeel van een inzet dat moet worden onderworpen aan een belastingstests is de eindgebruiker die voor publicatie of Dispatcher-omgeving staat.

U kunt geautomatiseerde testtools van andere bedrijven gebruiken om de prestaties van de website te testen. Met deze gereedschappen kunt u stappen opnemen die gebruikers op de site doorlopen en een groot aantal van deze sessies tegelijk uitvoeren om het standaardladen van een productiewebsite te simuleren.

De meeste productiewebsites hebben optimalisaties, zoals Dispatcher caching en een netwerk voor het leveren van inhoud. Zorg er tijdens het testen voor dat deze optimalisaties ook voor de testomgeving beschikbaar zijn. Naast het controleren van reactietijden voor de eindgebruikers, controleert u de meetgegevens van het systeem op de publicatieservers en de verzenders om ervoor te zorgen dat het systeem niet door hardwarebronnen wordt beperkt.

Op een systeem dat geen hoog niveau van verpersoonlijking vereist, zou Dispatcher de meeste verzoeken in het voorgeheugen onder moeten brengen. Als gevolg hiervan moet de belasting op het publicatieexemplaar relatief vlak blijven. Als een hoog niveau van verpersoonlijking wordt vereist, wordt het geadviseerd om technologieën zoals iFrames of AJAX verzoeken om de gepersonaliseerde inhoud te gebruiken om zoveel mogelijk Dispatcher caching toe te staan.

Voor basistests kan Apache Bench worden gebruikt om responstijden van webservers te meten en om belasting te creëren voor het meten van zaken zoals geheugenlekken. Zie het voorbeeld in de [&#x200B; documentatie van de Controle &#x200B;](/help/sites-deploying/monitoring-and-maintaining.md#apache-bench).

## Problemen met prestaties oplossen {#troubleshooting-performance-issues}

Nadat u prestatietests op de auteur hebt uitgevoerd, moeten eventuele problemen worden onderzocht, gediagnosticeerd en opgelost. U kunt verschillende gereedschappen en technieken gebruiken bij het uitvoeren van analyses en het aanpakken van problemen:

* U kunt het [&#x200B; logboek van de Prestaties van het Verzoek &#x200B;](/help/sites-administering/operations-dashboard.md#request-performance) in het Dashboard van Verrichtingen inspecteren. Dit gereedschap kan worden gebruikt om aanvragen voor langzame pagina&#39;s te identificeren
* Analyseer langzame lopende vragen met het [&#x200B; hulpmiddel van de Prestaties van de Vraag &#x200B;](/help/sites-administering/operations-dashboard.md#query-performance)

* Bekijk het foutenlogboek voor fouten of waarschuwingen. Voor meer informatie, zie [&#x200B; het Registreren &#x200B;](/help/sites-deploying/configure-logging.md).
* Hardwarebronnen van het systeem controleren, zoals geheugen- en CPU-gebruik, schijf-I/O of netwerk-I/O. Deze middelen zijn vaak de oorzaken van prestatiesknelpunten.
* Optimaliseer de architectuur van de pagina&#39;s en hoe zij worden gericht om het gebruik van URL parameters te minimaliseren om voor zoveel mogelijk caching mogelijk toe te staan.
* Volg de [&#x200B; Optimalisering van Prestaties &#x200B;](/help/sites-deploying/configuring-performance.md) en [&#x200B; het stemmen van Prestaties uiteinden &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=nl-NL) documentatie.

* Als er problemen optreden bij het bewerken van bepaalde pagina&#39;s of componenten op auteur-instanties, gebruikt u de TouchUI-ontwikkelaarsmodus om de pagina in kwestie te inspecteren. Dit geeft een indeling van elk inhoudsgebied op de pagina en de laadtijd.
* Alle JS en CSS op de site miniaturen. Zie dit [&#x200B; blogbericht &#x200B;](https://blogs.adobe.com/foxes/enable-js-and-css-minification/).
* Elimineer ingesloten CSS en JS uit de componenten. Ze moeten worden opgenomen in en geminiateerd bij de bibliotheken aan de clientzijde om het aantal aanvragen te minimaliseren dat vereist is om de pagina weer te geven.
* Om de serververzoeken te inspecteren en te zien welke het langst nemen, gebruik browser hulpmiddelen zoals het lusje van het Netwerk van Chrome.

Als probleemgebieden zijn geïdentificeerd, kan de toepassingscode worden gecontroleerd op optimalisatie van de prestaties. Alle AEM-functies in de verpakking die niet correct werken, kunnen worden verwerkt met ondersteuning voor Adobe.
