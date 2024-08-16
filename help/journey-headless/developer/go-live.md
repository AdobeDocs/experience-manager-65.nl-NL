---
title: Hoe u met uw headless toepassing kunt gaan werken
description: In dit deel van de AEM Headless Developer Journey leert u hoe u een toepassing zonder kop kunt implementeren.
exl-id: ec3356ef-9e60-4151-984d-3ebdab593b96
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin, Developer
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '1803'
ht-degree: 0%

---

# Hoe u met uw headless toepassing kunt gaan werken {#go-live}

In dit deel van de [ AEM Dagboek van de Ontwikkelaar van de Zwaartepunt ](overview.md), leer hoe te om een headless toepassing op te stellen levend.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [ hoe te om Uw Inhoud via AEM Assets APIs bij te werken ](update-your-content.md) leerde u hoe te om uw bestaande inhoud zonder kop in AEM via API bij te werken en u zou nu moeten:

* Begrijp de AEM Assets HTTP API.

Dit artikel bouwt verder op die grondbeginselen zodat u begrijpt hoe u uw eigen AEM headless project kunt voorbereiden om te leven.

## Doelstelling {#objective}

Met dit document krijgt u inzicht in de publicatiepijplijn zonder kop en in de prestatieaspecten die u moet kennen voordat u live gaat met uw toepassing.

* Meer informatie over de AEM SDK en de vereiste ontwikkelingstools
* Een lokale ontwikkelingstijd instellen om uw inhoud te simuleren voordat u live gaat
* Inhoudsreplicatie en basiskennis van AEM inhoud in cache
* De toepassing beveiligen en schalen voordat deze wordt gestart
* Prestaties bewaken en problemen met foutopsporing opsporen

## De AEM SDK {#the-aem-sdk}

De AEM SDK wordt gebruikt om aangepaste code te maken en in te voeren. Dit is het belangrijkste hulpmiddel dat u moet ontwikkelen en testen uw toepassing zonder kop alvorens te leven. Het bevat de volgende artefacten:

* De QuickStart-jar - een uitvoerbaar JAR-bestand dat kan worden gebruikt om een auteur- en een publicatie-instantie in te stellen
* Dispatcher-tools - de Dispatcher-module en de afhankelijkheden ervan voor Windows- en UNIX-systemen
* Java™ API Jar - De Java™ Jar/Maven Dependency die alle toegestane Java™ APIs blootstelt die kunnen worden gebruikt om tegen AEM te ontwikkelen
* Javadoc jar - de javadocs voor de Java™ API jar

## Aanvullende ontwikkelingsinstrumenten {#additional-development-tools}

Naast de AEM SDK hebt u aanvullende gereedschappen nodig die het ontwikkelen en testen van uw code en inhoud lokaal vergemakkelijken:

* Java™
* Git
* Apache Maven
* De Node.js-bibliotheek
* De IDE van uw keuze

Omdat AEM een Java™-toepassing is, moet u Java™ en de Java™ SDK installeren om de ontwikkeling van AEM as a Cloud Service te ondersteunen.

Git is wat u gebruikt om broncontrole te beheren en in de veranderingen in Cloud Manager te controleren en dan hen op te stellen aan een productie-instantie.

AEM gebruikt Apache Maven om projecten te bouwen die uit het AEM Maven Project archetype worden geproduceerd. Alle belangrijke IDEs verstrekt integratiesteun voor Maven.

Node.js is een runtimeomgeving van JavaScript die wordt gebruikt voor het werken met de front-end elementen van het `ui.frontend` subproject van een AEM project. Node.js wordt gedistribueerd met npm, die de facto de Manager van het Pakket Node.js is, die wordt gebruikt om de gebiedsdelen van JavaScript te beheren.

## Componenten van een AEM systeem in één oogopslag {#components-of-an-aem-system-at-a-glance}

Laten we nu eens kijken naar de onderdelen van een AEM omgeving.

Een volledige AEM omgeving bestaat uit een auteur, Publish en Dispatcher. Deze componenten worden ook beschikbaar gesteld in de lokale ontwikkelruntime, zodat u gemakkelijker een voorvertoning van uw code en inhoud kunt bekijken voordat u live gaat.

* **de dienst van de Auteur** is waar de interne gebruikers, inhoud creëren leiden en voorproef.

* **de dienst van Publish** wordt beschouwd als het &quot;Levende&quot;milieu en is typisch wat eind - gebruikers met in wisselwerking staan. Inhoud wordt na bewerking en goedkeuring op de service Auteur gedistribueerd (gerepliceerd) naar de Publish-service. Het meest gangbare implementatiepatroon met AEM toepassingen zonder kop is dat de productieversie van de toepassing verbinding maakt met een AEM Publish-service.

* **Dispatcher** is een statische Webserver die met de module van Dispatcher van de AEM wordt uitgebreid. Webpagina&#39;s die door de instantie publish worden gemaakt, worden in het cachegeheugen opgeslagen om de prestaties te verbeteren.

## De workflow voor lokale ontwikkeling {#the-local-development-workflow}

Het lokale ontwikkelingsproject is gebaseerd op Apache Maven en gebruikt Git voor broncontrole. Om het project bij te werken, kunnen de ontwikkelaars hun aangewezen geïntegreerde ontwikkelomgeving, zoals Verduistering, de Code van Visual Studio, of IntelliJ, onder anderen gebruiken.

Als u code- of inhoudsupdates wilt testen die door uw toepassing zonder kop worden opgenomen, implementeert u de updates in de lokale AEM-runtime. Deze omvatten lokale instanties van de AEM auteur en publicatieservices.

Let op het verschil tussen de verschillende componenten in de lokale AEM runtime, want het is belangrijk dat u de updates test op de plaatsen waar ze het belangrijkst zijn. Test bijvoorbeeld de inhoud van updates op de auteur of test nieuwe code op de publicatie-instantie.

In een productiesysteem zullen een Dispatcher en een http Apache-server altijd voor een AEM publicatie-instantie zitten. Zij verlenen caching en de veiligheidsdiensten voor het AEM systeem, zodat is het uiterst belangrijk om code en inhoudsupdates tegen Dispatcher eveneens te testen.

## Een lokale voorvertoning van uw code en inhoud weergeven in de lokale ontwikkelomgeving {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Om uw AEM project zonder kop voor te bereiden op de lancering, zorg ervoor dat alle samenstellende delen van uw project goed functioneren.

Om dat te doen, moet u alles samenvoegen: code, inhoud, en configuratie, en het testen in een lokale ontwikkelomgeving voor ga levende bereidheid.

De lokale ontwikkelomgeving bestaat uit drie hoofdgebieden:

1. Het AEM Project - bevat alle douanecode, configuratie, en inhoud de AEM ontwikkelaars zullen werken aan
1. Lokale AEM Runtime - lokale versies van de AEM auteur en publiceer de diensten die worden gebruikt om code van het AEM project op te stellen
1. De lokale Dispatcher Runtime - een lokale versie van de Apache htttpd-webserver die de Dispatcher-module bevat

Nadat de lokale ontwikkelomgeving is ingesteld, kunt u inhoud die in de React-app wordt gebruikt, simuleren door een statische Node-server lokaal te implementeren.

Om een meer diepgaande blik te krijgen bij vestiging een lokale ontwikkelomgeving en alle gebiedsdelen nodig voor inhoudsvoorproef, zie {de documentatie van de Plaatsing van de 0} Productie ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/overview.html).[

## Uw AEM toepassing zonder koppen voorbereiden voor Go-Live {#prepare-your-aem-headless-application-for-golive}

<!-- Start of CDN Review -->

Nu is het tijd om uw AEM toepassing zonder koppen klaar te maken voor de introductie, door de onderstaande aanbevolen procedures te volgen.

### Beveilig uw toepassing zonder koppen voordat u de toepassing start {#secure-and-scale-before-launch}

1. Bereid [ Authentificatie ](/help/sites-developing/headless/graphql-api/graphql-authentication-content-fragments.md) voor uw verzoeken van GraphQL voor

### Modelstructuur versus GraphQL-uitvoer {#structure-vs-output}

* Maak geen query&#39;s die meer dan 15 kB aan JSON uitvoeren (gecomprimeerd gzip). Lange JSON-bestanden zijn bronintensief, zodat de clienttoepassing kan parseren.
* Vermijd meer dan vijf geneste niveaus van fragmenthiërarchieën. Met extra niveaus kunnen auteurs van inhoud de gevolgen van hun wijzigingen moeilijk in overweging nemen.
* Gebruik multiobject query&#39;s in plaats van query&#39;s met afhankelijkheidshiërarchieën binnen de modellen te modelleren. Hierdoor is meer flexibiliteit op de lange termijn mogelijk om de JSON-uitvoer te herstructureren zonder dat u veel wijzigingen in de inhoud hoeft aan te brengen.

### CDN-hoogte-breedteverhouding in cache maximaliseren {#maximize-cdn}

* Gebruik geen directe GraphQL-query&#39;s, tenzij u live-inhoud vanaf het oppervlak aanvraagt.
   * Gebruik waar mogelijk doorlopende query&#39;s.
   * Verstrek CDN TTL boven 600 seconden zodat CDN hen kan in het voorgeheugen onderbrengen.
   * AEM kan het effect van een modelwijziging op bestaande query&#39;s berekenen.
* Splits JSON-bestanden/GraphQL-query&#39;s tussen lage en hoge wijzigingssnelheid voor inhoud om het clientverkeer naar CDN te verminderen en een hogere TTL toe te wijzen. Zo minimaliseert u de CDN die de JSON opnieuw valideert met de oorspronkelijke server.
* Als u de inhoud van de CDN actief ongeldig wilt maken, gebruikt u Zacht wissen. Hierdoor kan de CDN de inhoud opnieuw downloaden zonder dat een cache-fout optreedt.

>[!NOTE]
>
>Zie [ Extra Middelen ](#additional-resources) voor meer informatie over CDN en caching.

### Verbeter de tijd om inhoud zonder kop te downloaden {#improve-download-time}

* Zorg ervoor dat HTTP-clients HTTP/2 gebruiken.
* Zorg ervoor dat HTTP-clients de headeraanvraag voor gzip accepteren.
* Minimaliseer het aantal domeinen dat wordt gebruikt om JSON te hosten en referenced artefacten.
* Vernieuw bronnen met `Last-modified-since` .
* Gebruik `_reference` -uitvoer in JSON-bestand om elementen te downloaden zonder dat u volledige JSON-bestanden hoeft te parseren.

<!-- End of CDN Review -->

## Distribueren naar productie {#deploy-to-production}

Het opstellen aan Productie kan afhangen van of u a *traditionele* AEM instantie hebt die het gebruiken van Maven opstelt, of op Adobe Managed Services (AMS) en daarom het gebruiken van Cloud Manager is.

## Distribueren naar productie met Maven {#deploy-to-production-maven}

Voor a *traditionele* plaatsing (niet-AMS) gebruikend Gemaakt, zie het [ WKND Leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html#build) voor een overzicht.

## Distribueren naar productie met Cloud Manager {#deploy-to-production-cloud-manager}

Als u een klant van AMS gebruikend Cloud Manager bent, nadat u ervoor zorgt dat alles wordt getest en behoorlijk werkt, kunt u uw codeupdates aan a [ gecentraliseerde bewaarplaats van de it in Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/git-integration.html) duwen.

Nadat de updates aan Cloud Manager zijn geupload, stel hen in om het gebruiken van [ Cloud Manager te AEM CI/CD pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-deployment.html).

<!-- Cannot find a parallel link -->
<!--
You can start deploying your code by using the Cloud Manager CI/CD pipeline, which is covered extensively - see the [Overview](/help/implementing/deploying/overview.md) to start.
-->

## Prestatiebewaking {#performance-monitoring}

Voor gebruikers die de beste ervaring hebben wanneer ze de toepassing zonder AEM gebruiken, is het belangrijk dat u de belangrijkste prestatiewaarden in de gaten houdt, zoals hieronder wordt beschreven:

* Voorvertoning- en productieversies van de app valideren
* Verifieer AEM statuspagina&#39;s voor huidige de status van de de dienstbeschikbaarheid
* Toegang tot prestatierapporten
   * Leveringsprestaties
      * De servers van de oorsprong - aantal vraag, foutentarieven, cpu laadt, loonladingsverkeer
   * Auteursprestaties
      * Aantal gebruikers, aanvragen en laden controleren
* Toepassings- en ruimtespecifieke prestatierapporten openen
   * Als de server is geactiveerd, controleert u of de algemene meetwaarden groen/oranje/rood zijn en identificeert u vervolgens specifieke toepassingsproblemen
   * Open dezelfde rapporten die hierboven zijn gefilterd naar app of space (bijvoorbeeld Photoshop-bureaublad, paywall)
   * Logbestand-API&#39;s van Splunk gebruiken voor toegang tot service- en toepassingsprestaties
   * Neem contact op met de Klantenondersteuning als er andere problemen zijn.

## Problemen oplossen {#troubleshooting}

### Foutopsporing {#debugging}

Volg deze beste praktijken als algemene benadering van het zuiveren:

* Functionaliteit en prestaties valideren met de voorvertoningsversie van de toepassing
* Functionaliteit en prestaties valideren met de productieversie van de toepassing
* Valideren met de JSON-voorvertoning van de Content Fragment Editor
* Als u wilt controleren of er problemen optreden met de clienttoepassing of levering, controleert u de JSON in de clienttoepassing
* Als u wilt controleren of er problemen zijn met inhoud of AEM in cache, inspecteert u de JSON met GraphQL

### Een probleem aanmelden met ondersteuning {#logging-a-bug-with-support}

Voer de volgende stappen uit als u een bug efficiënt wilt aanmelden bij Support voor het geval u meer hulp nodig hebt:

* Indien nodig screenshots van het probleem nemen
* Een manier documenteren om het probleem te reproduceren
* Documenteer de inhoud waarmee de uitgave wordt gereproduceerd
* Logboek een kwestie door het portaal van de Steun van de AEM met de aangewezen prioriteit

## De reis eindigt - of wel? {#journey-ends}

Gefeliciteerd! U hebt de AEM Headless Developer Journey voltooid! U zou nu een inzicht moeten hebben in:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM eindeloze functies.
* Hoe te om Hoofdloze project te organiseren en te AEM.
* Hoe te om koploze inhoud in AEM te creëren.
* Hoe te om koploze inhoud in AEM terug te winnen en bij te werken.
* Hoe te om met een AEM Zwaardeloos project te leven.
* Wat moet u doen nadat de go-live is voltooid.

U hebt uw eerste AEM Headless-project al gestart of u hebt nu alle kennis om dat te doen. Geweldig werk!

### Toepassingen met één pagina verkennen {#explore-spa}

Het is echter niet nodig om de koploze winkels in AEM te stoppen. In het [ Begonnen deel van de reis ](getting-started.md#integration-levels), besprak het hoe AEM niet alleen hoofdloze levering en traditionele full-stack modellen steunt, maar ook hybride modellen die de voordelen van allebei combineren.

Als dit soort flexibiliteit iets is u voor uw project nodig hebt, ga aan het facultatieve, extra deel van de reis verder, [ hoe te om Enige Toepassingen van de Pagina (SPA) met AEM tot stand te brengen.](create-spa.md)

## Aanvullende bronnen {#additional-resources}

* [ AEM het Ontwikkelen Gids ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/the-basics.html)

* [ WKND Leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

* [ Cloud Manager voor AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)

* CDN-cache

   * [ Controlerend een CDN Geheime voorgeheugen ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html#controlling-a-cdn-cache)

   * Het vormen van [ CDN Rewriter ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html) (*onderzoek naar CDN Rewriter*)

* [Inleiding tot AEM als een CMS zonder kop](/help/sites-developing/headless/introduction.md)
* [ AEM het Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ Tutorials voor Zwaartepunt in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
