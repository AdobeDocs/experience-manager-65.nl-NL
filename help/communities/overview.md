---
title: AEM Communities - Overzicht
description: Leer meer over de basisbeginselen van de functies en instellingen van Adobe Experience Manager Communities.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
exl-id: d6243dff-a067-455c-a326-5f451f225efd
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 0%

---

# AEM Communities - Overzicht {#aem-communities-overview}

Met de gemeenschappen van Adobe Experience Manager (AEM) kunt u snel een lokale community-site maken die de prestaties verbetert, het sitebeheer verbetert en de conversie van sitebezoekers naar waardevolle leden van de community aanmoedigt.

## Functies van Gemeenschappen {#communities-features}

AEM Communities maakt de ontwikkeling mogelijk van een relatie met bezoekers van de site, die:

* **informeert** door blogs, Q&amp;A, en gebeurteniskalenders,
* Terwijl **inzichten** door forums, commentaren, en andere communautaire inhoud, die vaak als gebruiker-geproduceerde inhoud (UGC) wordt bedoeld.
* Het staat **matiging** door vertrouwde op leden in het milieu van Publish toe,
* **sociale login** met Twitter en Facebook,
* **Inline vertaling** van communautaire inhoud,
* **de groepsverwezenlijking van de Gemeenschap** van de gepubliceerde communautaire plaats,
* **Scoring** om badges toe te kennen,
* **Dossier delend**,
* **Meldingen** en **activiteitenstromen**,
* Staat **etiketterend** (@vermeld) andere geregistreerde leden in Gebruiker-Gegenereerde Inhoud toe, om hun aandacht te vestigen.

De eigenschappen van de gemeenschappen kunnen worden aangetoond gebruikend de [&#x200B; AEM machine van de Demo &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) openbaar op GitHub.com of met de nieuwe `We.Retail` verwijzingsimplementatie beschikbaar.

## Communitysites {#community-sites}

Een communitysite is een AEM site die is gemaakt met een eenvoudige wizard die resulteert in een website met veel algemene functies die vooraf zijn getelegrafeerd naar de site.

De [&#x200B; tovenaar van de plaatsverwezenlijking &#x200B;](/help/communities/sites-console.md):

* Verzamelt eigenschappen van de plaats, die op het geselecteerde [&#x200B; malplaatje van de communautaire plaats &#x200B;](/help/communities/sites.md) wordt gebaseerd die is:

   * gebouwd van [&#x200B; communautaire functies &#x200B;](#community-functions)
   * facultatieve [&#x200B; communautaire groepen &#x200B;](#communitygroups) eigenschap

* Gebruikt te configureren instellingen:

   * matiging
   * aanmelden
   * vertalen

* Biedt essentiële functies:

   * Het responsieve ontwerp: gebruikt [&#x200B; de thema&#39;s van de Bootstrap van de Twitter &#x200B;](https://getbootstrap.com)

   * Login: zelfregistratie, [&#x200B; sociale login &#x200B;](/help/communities/social-login.md), gebruikersprofielen

      * Meldingen:
leden zien gebeurtenissen die voor hen relevant zijn, en door de gebruiker gegenereerde inhoud waar zij [@genoemd &#x200B;](/help/communities/overview.md#mentionssupport) zijn.

      * Berichten: leden kunnen berichten verzenden of ontvangen binnen de communitysite.
      * Zoeken: zoekmogelijkheden op de site van de community.
      * Taalomschakeling: capaciteit om een taal voor a [&#x200B; meertalige plaats &#x200B;](/help/sites-administering/translation.md) te selecteren.

      * Beheer: toegang voor geautoriseerde leden tot gematigde en beheerde gebruikers binnen de site van de gemeenschap.

* Hiermee verwijdert u veel ontwerpstappen op paginaniveau:

   * Branding: optionele upload van een bannerafbeelding voor weergave op alle pagina&#39;s van de gemeenschapssite
   * Navigatiemenu: er zijn navigatiekoppelingen beschikbaar voor de functies die zijn opgenomen in de sjabloon voor de communautaire site.

Om het gemak te ervaren om snel een communautaire plaats tot stand te brengen, bezoek [&#x200B; Begonnen het worden met AEM Communities &#x200B;](/help/communities/getting-started.md).

## Persistentie van communautaire inhoud {#community-content-persistence}

Om de prestaties en synchronisatie van gemeenschapsinhoud te verbeteren, vereist AEM Communities een gemeenschappelijke opslag specifiek voor gebruiker-geproduceerde inhoud (UGC) die tussen alle AEM (auteur en publiceer) instanties wordt gedeeld.

De communautaire inhoud wordt gemakkelijk betreden door de leverancier van het opslagmiddel (SRP), die een laag verstrekt om toegang van de onderliggende topologie te scheiden en een gemeenschappelijke opslag voor UGC steunt.

Ga voor meer informatie over de persistentie en aanbevolen implementaties van community-inhoud naar:

* [&#x200B; Communautaire Opslag van de Inhoud &#x200B;](/help/communities/working-with-srp.md) - bespreekt de beschikbare opslagopties SRP voor UGC.
* [&#x200B; geadviseerde Topologieën &#x200B;](/help/communities/topologies.md) - bespreekt topologieën die op gebruiksgeval en keus SRP worden gebaseerd.
* [&#x200B; Bevorderend aan AEM 6.5 Gemeenschappen &#x200B;](/help/communities/upgrade.md) - verstrekt nuttige informatie betreffende UGC wanneer het bewegen naar AEM 6.5.

## Communityconsoles {#communities-consoles}

In het auteursmilieu, verleent de globale navigatieconsole toegang tot de [&#x200B; console van Gemeenschappen &#x200B;](/help/communities/consoles.md), die bevat:

* [&#x200B; Sites &#x200B;](/help/communities/sites-console.md) console

   * Site maken
   * Site bewerken
   * Sitebeheer
   * [&#128279;](/help/communities/groups.md) console van de Groepen van 0&rbrace; Gemeenschap &lbrace;

* [&#128279;](/help/communities/moderation.md) console van 0&rbrace; Moderatie

   * Gemeenschappelijke bulkmoderatie UI voor de milieu&#39;s van de Auteur en van Publish.
   * Nieuwe filtercriteria.

* [&#x200B; Leden en Groepen &#x200B;](/help/communities/members.md) beheersconsoles

   * Hiermee kunt u gebruikers (leden) aan de publicatiezijde maken en beheren vanuit de ontwerpomgeving.
   * Hiermee kunt u leden verbieden.
   * Hiermee kunt u gebruikersgroepen (lidgroepen) aan de serverzijde maken en beheren.

* [&#x200B; Rapporten &#x200B;](/help/communities/reports.md) console

   * Hiermee kunt u rapporten genereren over toewijzingen, posten en weergaven.

De globale hulpmiddelenconsole verleent toegang tot de volgende hulpmiddelen van Gemeenschappen:

* [&#x200B; Sjablonen van de Plaats &#x200B;](/help/communities/tools.md#sitetemplatesconsole) console

   * Sjablonen voor communitysites maken en beheren.

* [&#128279;](/help/communities/tools.md#grouptemplatesconsole) console van de Malplaatjes van 0&rbrace; Groep

   * Creëer en beheer communitygroepssjablonen.

* [&#x200B; Communautaire Functies &#x200B;](/help/communities/tools.md#communityfunctionsconsole) console

   * Creëer en beheer communityfuncties.

* [&#128279;](/help/communities/tools.md#storageconfiguratonconsole) console van de Configuratie van de Opslag 0&rbrace;

   * Selecteer en vorm de [&#x200B; gemeenschappelijke opslag &#x200B;](/help/communities/working-with-srp.md) voor de plaats.

* [Component Guide](/help/communities/components-guide.md)

   * Een steekproefplaats, [&#x200B; Communautaire Componenten &#x200B;](https://localhost:4502/editor.html/content/community-components/en.html) verstrekt een steekproef van alle componenten van Gemeenschappen met hun standaardconfiguratie en de capaciteit om met hen te experimenteren.

## Sjablonen voor community-sites {#community-site-templates}

De creatie van de communautaire plaats is gebaseerd op selectie van een malplaatje van de communautaire plaats om snel een communautaire plaats te vestigen die van om het even welke steekproefplaats onafhankelijk is.

Een communitysitesjabloon, dat bestaat uit communityfuncties en communitygroepssjablonen, biedt de structuur voor een communitysite. Het omvat login, gebruikersprofielen, overseinen, plaatsmenu, onderzoek, thema, en branding eigenschappen.

Zie de [&#x200B; console van de Malplaatjes van de Plaats &#x200B;](/help/communities/sites.md).

## Communautaire functies {#community-functions}

De kenmerken die van een gemeenschapservaring worden verwacht, zijn bekend. In AEM Communities zijn deze functies beschikbaar als bouwstenen, ook wel bekend als gemeenschapsfuncties.

Community-functies zijn normale AEM pagina&#39;s bevatten onderdelen die zijn samengevoegd tot een functie die gemakkelijk kan worden opgenomen in een sjabloon voor een community-site.

Zie de [&#x200B; communautaire console van Functies &#x200B;](/help/communities/functions.md).

## Communautaire groepen en groepssjablonen {#community-groups-and-group-templates}

De eigenschap van communautaire groepen is de capaciteit voor een subcommunity om dynamisch binnen een communautaire plaats door erkende gebruikers en communityleden van zowel de auteur als publicatiemilieu&#39;s worden gecreeerd.

Van het auteursmilieu, kunnen de communautaire groepen (subCommunities) binnen een bestaande communautaire plaats worden gecreeerd of binnen een bestaande groep worden genesteld, wanneer de structuur van het malplaatje de [&#x200B; functie van Groepen &#x200B;](/help/communities/functions.md#groups-function) bevat.

Voor het maken van een community-groep moet u een community-groepssjabloon selecteren die het ontwerp van de community-groepspagina&#39;s bevat. Wanneer een functie van Groepen aan een malplaatjestructuur wordt toegevoegd, wordt het gevormd om of één groepsmalplaatje te specificeren of een keus van malplaatjes te verstrekken op het tijdstip dat een nieuwe communautaire groep wordt gecreeerd.

Zie ook:

* [&#x200B; console van de Groepen van de Plaats &#x200B;](/help/communities/groups.md) voor het creëren van subgemeenschap in het auteursmilieu.
* [&#x200B; console van de Malplaatjes van de Groep &#x200B;](/help/communities/tools-groups.md) voor het creëren van plaatsstructuren voor groepen.
* [&#x200B; Begonnen het Worden met AEM Communities &#x200B;](/help/communities/getting-started.md) voor leerprogramma voor snel het creëren van een communautaire plaats met inbegrip van genestelde groepen.

## Community-componenten {#community-components}

De [&#x200B; communautaire componenten &#x200B;](/help/communities/author-communities.md) waarvan een communautaire plaats wordt gebouwd kan worden gebruikt om de eigenschappen van Gemeenschappen aan om het even welke AEM Plaats toe te voegen.

De [&#x200B; communautaire componentengids &#x200B;](/help/communities/components-guide.md) is beschikbaar voor interactieve exploratie van de componenten.

## Gemeenschap voor betrokkenheid {#engagement-community}

Een betrokkenheidsgemeenschap is een community-site die klanten aanmoedigt om te informeren, feedback te vragen en klanten in staat te stellen als leden van de community te communiceren.

Functies van een betrokkenheidsgemeenschap kunnen het volgende omvatten:

* Aanmelden
* Berichten
* Forums
* Opmerkingen
* Revisies
* Waarderingen
* Stemming
* Blogs
* Groepen
* Kalenders
* Vertaling
* Moderatie
* Meldingen
* Scores en badges
* Analyserapportage

Om het gemak te ervaren om snel een betrokkenheidsgemeenschap tot stand te brengen, bezoek [&#x200B; Begonnen het worden met AEM Communities &#x200B;](/help/communities/getting-started.md).

## AEM demo-machine {#aem-demo-machine}

De [&#x200B; AEM machine van de Demo &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) beheert en stelt demo&#39;s voor AEM [&#x200B; Plaatsen &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [&#x200B; Assets &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [&#x200B; Gemeenschappen &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [&#x200B; Apps &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) en [&#x200B; Forms &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) in werking, die vaak meer opstelling dan eenvoudig het lanceren van een instantie QuickStart vereisen. De machine van de AEMDemo plaatst omhoog extra [&#x200B; infrastructuur &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) zoals MongoDB, Solr, MySQL, Mpeg, en e-mailservers.

De AEM demomodus omvat:

* A [&#x200B; grafisch gebruikersinterface &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache WIL manuscripten met configureerbare [&#x200B; eigenschappen &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) en [&#x200B; doelstellingen &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Te installeren pakketten.

De AEM Demo-machine is getest met succes met CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 en AEM 6.4 op Windows, macOS en Linux®.

Voor AEM demo-machine is een geldige AEM vereist.

>[!NOTE]
>
>Bekijk a [&#x200B; videoinleiding &#x200B;](https://www.youtube.com/watch?v=zEE_zkR9fVQ&feature=youtu.be) aan de machine van de AEM (13:26).

## AEM Communities-documentatie {#aem-communities-documentation}

* Bezoek [&#x200B; het Opstellen van Gemeenschappen &#x200B;](deploy-communities.md) waar u over geadviseerde plaatsingen kunt leren.
* Bezoek [&#x200B; het Beheer Plaatsen van Gemeenschappen &#x200B;](administer-landing.md) waar u over het creëren van een communautaire plaats kunt leren, toevoegend communautaire groepen, vormend communautaire plaatssjablonen, het modereren van communautaire inhoud, het beheren van leden, het etiketteren, berichten, het scoren, en badges.
* Bezoek [&#x200B; het Ontwikkelen van Gemeenschappen &#x200B;](communities.md) waar u over het sociale componentenkader (SCF) en het aanpassen van de componenten en de eigenschappen van Gemeenschappen kunt leren.
* Bezoek [&#x200B; Authoring Communities Components &#x200B;](author-communities.md) waar u kunt leren hoe u met componenten van Gemeenschappen ontwerpt en deze configureert.
