---
title: Richtlijnen voor hardwareaanpassing
description: Deze het rangschikken richtlijnen bieden een benadering van de hardwaremiddelen die worden vereist om een AEM project op te stellen.
exl-id: 5837ef4f-d4e0-49d7-a671-87d5547e0d98
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader
source-git-commit: 658e1f6e07fb1219ba186137eb8403bf85383723
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 0%

---

# Richtlijnen voor hardwareaanpassing{#hardware-sizing-guidelines}

Deze het rangschikken richtlijnen bieden een benadering van de hardwaremiddelen die worden vereist om een AEM project op te stellen. Het rangschikken van ramingen hangt van de architectuur van het project, de ingewikkeldheid van de oplossing, het verwachte verkeer, en de projectvereisten af. Deze gids helpt u om de hardwarebehoeften voor een specifieke oplossing te bepalen, of een hogere en lagere schatting voor de hardwarevereisten te vinden.

De volgende basisfactoren moeten in aanmerking worden genomen:

* **de snelheid van het Netwerk**

   * Netwerkvertraging
   * Beschikbare bandbreedte

* **Computationele snelheid**

   * Efficiëntie in cache
   * Verwacht verkeer
   * Complexiteit van sjablonen, toepassingen en componenten
   * Gelijktijdige auteurs
   * Complexiteit van de ontwerpbewerking (eenvoudige bewerking van inhoud, rollout van MSM enzovoort)

* **I/O prestaties**

   * Prestaties en efficiëntie van de bestands- of databaseopslag

* **Vaste Aandrijving**

   * minstens twee of drie keer groter dan de grootte van de repository

* **Geheugen**

   * Grootte van website (aantal content-object, pagina&#39;s en gebruikers)
   * Aantal gebruikers/sessies dat tegelijkertijd actief is

## Architectuur {#architecture}

Een standaardinstelling voor AEM bestaat uit een auteur en een publicatieomgeving. Deze omgevingen hebben verschillende vereisten met betrekking tot de onderliggende hardwaregrootte en systeemconfiguratie. De gedetailleerde overwegingen voor beide milieu&#39;s worden beschreven in het [ auteursmilieu ](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) en [ publiceren milieu ](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations) secties.

In een typisch projectopstelling, hebt u verscheidene milieu&#39;s waarop aan de fasen van het werkgebiedproject:

* **het milieu van de Ontwikkeling**
Nieuwe functies ontwikkelen of belangrijke wijzigingen aanbrengen. De beste praktijken moeten werken gebruikend een ontwikkelomgeving per ontwikkelaar (lokale installaties op hun persoonlijke systemen).

* **de testmilieu van de Auteur**
Wijzigingen verifiëren. Het aantal testomgevingen kan variëren afhankelijk van de projectvereisten (bijvoorbeeld, apart voor QA, integratietests of gebruikeracceptatietests).

* **de testmilieu van Publish**
Hoofdzakelijk voor het testen van gevallen waarin gebruik wordt gemaakt van sociale samenwerking en/of de interactie tussen auteur en meerdere publicatie-instanties.

* **het productiemilieu van de Auteur**
Voor auteurs om inhoud te bewerken.

* **Publish productiemilieu**
Gepubliceerde inhoud bedienen.

Bovendien kunnen de omgevingen variëren, variërend van een systeem met één server en een toepassingsserver tot een zeer geschaalde set van multi-server, multi-CPU geclusterde instanties. De Adobe adviseert dat u een afzonderlijke computer voor elk productiesysteem gebruikt en dat u geen andere toepassingen op deze computers in werking stelt.

## Algemene overwegingen voor hardwaregrootte {#generic-hardware-sizing-considerations}

In de volgende secties wordt uitgelegd hoe u de hardwarevereisten kunt berekenen, rekening houdend met verschillende overwegingen. Voor grote systemen, stelt de Adobe voor dat u een eenvoudige reeks interne benchmarktests op een verwijzingsconfiguratie uitvoert.

Optimalisering van prestaties is een fundamentele taak die moet worden uitgevoerd voordat benchmarking voor een specifiek project kan worden uitgevoerd. Zorg ervoor om het advies toe te passen dat in de [ documentatie van de Optimalisering van Prestaties ](/help/sites-deploying/configuring-performance.md) wordt verstrekt alvorens om het even welke benchmarktests uit te voeren en hun resultaten voor om het even welke hardware rangschikkende berekeningen te gebruiken.

De vereisten voor het aanpassen van de hardwaregrootte voor gevallen van geavanceerd gebruik moeten gebaseerd zijn op een gedetailleerde prestatiebeoordeling van het project. Kenmerken van gevallen van geavanceerd gebruik waarvoor uitzonderlijke hardwarebronnen nodig zijn, zijn onder meer combinaties van:

* hoge lading/doorvoer van inhoud
* uitgebreid gebruik van aangepaste code, aangepaste workflows of softwarebibliotheken van derden
* integratie met niet-ondersteunde externe systemen

## Schijfruimte/vaste schijf {#disk-space-hard-drive}

De vereiste schijfruimte hangt sterk af van zowel het volume als het type van uw webtoepassing. In de berekeningen moet rekening worden gehouden met het volgende:

* de hoeveelheid en grootte van pagina&#39;s, elementen en andere opslagplaatsen-opgeslagen entiteiten zoals werkschema&#39;s, profielen, etc.
* de geschatte frequentie van inhoudwijzigingen en dus het maken van contentversies
* het volume van DAM-activa die worden gegenereerd
* de algemene groei van de inhoud in de loop der tijd

De schijfruimte wordt onophoudelijk gecontroleerd tijdens Online, en Off-line, de Opruiming van de Revisie. Als de beschikbare schijfruimte onder een kritieke waarde daalt, wordt het proces geannuleerd. De kritieke waarde is 25% van de huidige schijfvoetafdruk van de opslagplaats en kan niet worden geconfigureerd. Adobe raadt aan de schijf ten minste twee of drie keer groter te maken dan de opslagplaats, inclusief de geschatte groei.

### Virtualisatie {#virtualization}

AEM werkt goed in gevirtualiseerde omgevingen, maar er kunnen factoren zijn zoals CPU of I/O die niet rechtstreeks kunnen worden gelijkgesteld met fysieke hardware. Een aanbeveling is om een hogere I/O-snelheid (in het algemeen) te kiezen, aangezien dit doorgaans een kritieke factor is. Benchmarking van uw omgeving is nodig om precies te begrijpen welke bronnen vereist zijn.

### Parallelisatie van AEM instanties {#parallelization-of-aem-instances}

**de Veiligheid van het Kort**

Een faalveilige website wordt opgesteld op minstens twee afzonderlijke systemen. Als één systeem afbreekt, kan een ander systeem overnemen en zo de systeemmislukking compenseren.

**de middelen van het Systeem scalability**

Terwijl alle systemen actief zijn, zijn er betere computerprestaties beschikbaar. Die extra prestaties hoeven niet lineair te zijn met het aantal clusterknooppunten, aangezien de relatie sterk afhankelijk is van de technische omgeving. Zie [ documentatie van de Cluster ](/help/sites-deploying/recommended-deploys.md) voor meer informatie.

De schatting van het aantal clusterknooppunten dat nodig is, is gebaseerd op de basisvereisten en de specifieke gebruiksgevallen van het specifieke webproject:

* Vanuit het perspectief van mislukken-veiligheid, is het noodzakelijk om, voor alle milieu&#39;s te bepalen hoe kritieke mislukking en de tijd van de mislukkingscompensatie is gebaseerd op hoe lang het voor een clusterknoop vergt om terug te krijgen.
* Voor het aspect van scalability, is het aantal schrijfverrichtingen fundamenteel de belangrijkste factor. Het in evenwicht brengen van de lading kan voor verrichtingen worden gevestigd die tot het systeem slechts toegang hebben om gelezen verrichtingen te verwerken; zie [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL) voor details.

### Hardware Recommendations {#hardware-recommendations}

Gewoonlijk kunt u voor uw auteursomgeving dezelfde hardware gebruiken als voor uw het publiceren milieu wordt geadviseerd. Websiteverkeer is doorgaans lager bij ontwerpsystemen, maar de efficiëntie van de cache is lager. De fundamentele factor hierbij is echter het aantal auteurs dat parallel werkt, en het soort acties dat in het systeem wordt ondernomen. Over het algemeen is AEM clustering (van de auteursomgeving) het meest effectief bij het schalen van leesbewerkingen; met andere woorden, een AEM cluster schaalt goed met auteurs die elementaire bewerkingsbewerkingen uitvoeren.

## Aanvullende gebruiksspecifieke berekeningen {#additional-use-case-specific-calculations}

Naast de berekening voor een standaardwebtoepassing, moet u rekening houden met specifieke factoren voor de volgende gebruiksgevallen. De berekende waarden moeten aan de standaardberekening worden toegevoegd.

### Assets-specifieke overwegingen {#assets-specific-considerations}

Voor een uitgebreide verwerking van digitale elementen zijn geoptimaliseerde hardwarebronnen nodig. De belangrijkste factoren zijn de beeldgrootte en de maximale doorvoer van verwerkte afbeeldingen.

Wijs minstens 16GB van hoop toe en vorm het [!UICONTROL DAM Update Asset] werkschema om het [ Camera Raw pakket ](/help/assets/camera-raw.md) voor het opnemen van ruwe beelden te gebruiken.

>[!NOTE]
>
>Een hogere doorvoer van afbeeldingen betekent dat de computerbronnen gelijke tred moeten kunnen houden met de I/O van het systeem en omgekeerd. Als workflows bijvoorbeeld worden gestart door het importeren van afbeeldingen, kan het uploaden van veel afbeeldingen via WebDAV een achterstand in workflows veroorzaken.
>
>Het gebruik van afzonderlijke schijven voor TarPM, gegevensopslag en zoekindex kan helpen het I/O-gedrag van het systeem te optimaliseren (het is echter doorgaans verstandig om de zoekindex lokaal te houden).

>[!NOTE]
>
>Zie ook de [ Gids van de Prestaties van Assets ](/help/sites-deploying/assets-performance-sizing.md).

### Beheer van meerdere sites {#multi-site-manager}

Het hulpmiddelverbruik wanneer het gebruiken van AEM MSM op een auteursmilieu hangt sterk van de specifieke gebruiksgevallen af. Basisfactoren zijn:

* Aantal actieve kopieën
* Frequentie van rollouts
* De uit te rollen inhoudsboomgrootte
* Verbonden functionaliteit van de rollout-acties

Het testen van het geplande gebruiksgeval met een representatief inhoudsuittreksel kan u helpen uw begrip van het middelgebruik verbeteren. Als u de resultaten met de geplande productie extrapoleert, kunt u de extra middelen beoordelen die voor AEM MSM worden vereist.

Zorg ook voor auteurs die parallel werken. Zij zullen prestaties bijwerkingen gevolgen waarnemen als AEM MSM gebruiksgevallen meer middelen dan gepland verbruiken.

### Overwegingen bij AEM Communities-grootte {#aem-communities-sizing-considerations}

AEM sites die AEM Communities-functies (communitysites) bevatten, ervaren veel interactie van sitebezoekers (leden) in de publicatieomgeving.

De rangschikkingsoverwegingen voor een communautaire plaats hangen van de verwachte interactie door communautaire leden af en of optimale prestaties voor paginacontent van hoger belang is.

Door de gebruiker gegenereerde inhoud (UGC) wordt apart van de pagina-inhoud opgeslagen. Terwijl het AEM platform een knoopopslag gebruikt die plaatsinhoud van auteur aan publicatie herhaalt, gebruikt AEM Communities één enkele, gemeenschappelijke opslag voor UGC die nooit wordt herhaald.

Voor de opslag UGC, is het noodzakelijk om een leverancier van het opslagmiddel (SRP) te kiezen, die de gekozen plaatsing beïnvloedt.
Zie

* [Opslag van communautaire inhoud](/help/communities/working-with-srp.md)
* [Aanbevolen topologieën voor Gemeenschappen](/help/communities/topologies.md)
