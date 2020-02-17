---
title: Overzicht van AEM-gemeenschappen
seo-title: Overzicht van AEM-gemeenschappen
description: Een overzicht van de functies en instellingen van AEM Communities
seo-description: Een overzicht van de functies en instellingen van AEM Communities
uuid: 14405847-36ae-4958-bdc6-d799ecd05f06
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 44374006-f711-4af8-a1fe-f89164f79581
docset: aem65
translation-type: tm+mt
source-git-commit: 70e6f2d8366456e5091b7b775dc40914948921ab

---


# Overzicht van AEM-gemeenschappen{#aem-communities-overview}

Met Adobe Experience Manager (AEM) Community&#39;s kunt u snel een onsite community-site maken die de prestaties verbetert, het sitebeheer verbetert en het converteren van sitebezoekers naar waardevolle leden van de community aanmoedigt.

Neem contact op met uw accountvertegenwoordiger voor informatie over licenties voor AEM-gemeenschappen en aanvullende licenties voor functies voor activering en Adobe Analytics.

## Functies van Gemeenschappen {#communities-features}

AEM Communities maakt het mogelijk een relatie te ontwikkelen met bezoekers van de site, die:

* **informeert** via blogs, vragen en antwoorden en gebeurtenissencalenders,
* **ophalen inzichten **via forums, opmerkingen en andere inhoud van de community, vaak UGC (door gebruikers gegenereerde inhoud) genoemd.
* Het maakt** matiging **door vertrouwde leden in het publicatiemilieu mogelijk,
* **sociale aanmelding **met Twitter en Facebook,
* **inlinevertaling** van communautaire inhoud,
* **oprichting van groepen van de gemeenschap *** van de gepubliceerde communautaire site,
* **scoring **om badges toe te kennen,
* **bestanden delen**,
* **meldingen **en **activiteitsstromen**,

* Hiermee kunt u andere geregistreerde leden **labelen** (@genoemd) in Door gebruiker gegenereerde inhoud om hun aandacht te vestigen.
* Ondersteunt **toetsenbordnavigatie** op machtigingscomponenten (bijvoorbeeld Catalog en Cursus afspelen, Toewijzingen, Bestandsbibliotheek).

De eigenschappen van gemeenschappen kunnen worden aangetoond gebruikend de [AEM demomachine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) die openbaar op GitHub.com of met de nieuwe Web.Retail verwijzingsimplementatie beschikbaar is.

## Communitysites {#community-sites}

Een gemeenschapssite is een AEM-site die is gemaakt met een eenvoudige wizard die resulteert in een website met veel algemene functies die vooraf zijn getelegrafeerd naar de site.

De wizard [Site maken](/help/communities/sites-console.md):

* stelt eigenschappen van de plaats, die op het geselecteerde malplaatje [van de](/help/communities/sites.md) communautaire plaats wordt gebaseerd:

   * gebouwd uit [gemeenschapsfuncties](#community-functions)
   * optionele [community groups](#communitygroups) feature

* gebruikt instellingen om te configureren:

   * matiging
   * aanmelden
   * vertalen

* biedt essentiële kenmerken:

   * responsief ontwerp:
gebruikt [Twitter Bootstrap-thema&#39;s](https://getbootstrap.com)

   * login:
zelfregistratie, [sociale aanmelding](/help/communities/social-login.md), gebruikersprofielen

   * meldingen:
leden zien gebeurtenissen die voor hen van belang zijn en door gebruikers gegenereerde inhoud waar ze [@genoemd](/help/communities/overview.md#mentionssupport)zijn.

   * berichten:
leden kunnen berichten verzenden of ontvangen binnen de communautaire site
   * zoeken:
vermogen om te zoeken op de gemeenschapssite
   * taalomschakeling:
de mogelijkheid om een taal te selecteren voor een [meertalige site](/help/sites-administering/translation.md)

   * administratie:
toegang voor gemachtigde leden tot gematigde en beheerde gebruikers binnen de communautaire site

* Hiermee verwijdert u veel ontwerpstappen op paginaniveau:

   * branding:
optionele upload van een bannerafbeelding voor weergave op alle pagina&#39;s van de gemeenschapssite
   * navigatiemenu:
navigatiekoppelingen zijn beschikbaar voor de functies die zijn opgenomen in het sjabloon voor de communautaire site

Ga naar [Aan de slag met AEM-gemeenschappen](/help/communities/getting-started.md)om snel een nieuwe community-site te kunnen maken.

## Persistentie van communautaire inhoud {#community-content-persistence}

Om de prestaties en synchronisatie van inhoud van de gemeenschap te verbeteren, vereist de Gemeenschappen AEM een gemeenschappelijke opslag specifiek voor gebruiker geproduceerde inhoud (UGC) die tussen alle (auteur en publiceer) instanties AEM wordt gedeeld.

De communautaire inhoud wordt gemakkelijk betreden door de leverancier van het opslagmiddel (SRP), die een laag verstrekt om toegang van de onderliggende topologie te scheiden en een gemeenschappelijke opslag voor UGC steunt.

Ga voor meer informatie over de persistentie en aanbevolen implementaties van community-inhoud naar:

* [Community Content Storage](/help/communities/working-with-srp.md), waarin de beschikbare SRP-opslagopties voor UGC worden besproken.
* [De geadviseerde Topologieën](/help/communities/topologies.md), die topologieën bespreekt die op gebruiksgeval en keus SRP worden gebaseerd.
* [Upgrade naar AEM 6.5 Communities](/help/communities/upgrade.md), die nuttige informatie biedt over UGC bij de overgang naar AEM 6.5.

## Communityconsoles {#communities-consoles}

In het auteursmilieu, verleent de globale navigatieconsole toegang tot de console [van](/help/communities/consoles.md)Gemeenschappen, die bevat:

* [Sites](/help/communities/sites-console.md) -console

   * site maken
   * site bewerken
   * sitebeheer
   * [Community Group](/help/communities/groups.md) -console

* [Moderniseringsconsole](/help/communities/moderation.md)

   * algemene bulkmoderatie UI voor auteur en publicatiemilieu&#39;s
   * nieuwe filtercriteria

* [Leden en groepen](/help/communities/members.md) beheerconsoles

   * biedt de mogelijkheid gebruikers (leden) aan de serverzijde te maken en te beheren vanuit de ontwerpomgeving
   * biedt de mogelijkheid om leden te verbieden
   * biedt de mogelijkheid om publicatiezijgebruikersgroepen (lidgroepen) te maken en te beheren vanuit de auteursomgeving

* [Rapporten](/help/communities/reports.md) console

   * biedt de mogelijkheid rapporten te genereren over toewijzingen, posten en weergaven

* [Bronnen](/help/communities/resources.md) -console

   * verstrekt de capaciteit om enablement middelen en het leren wegen tot stand te brengen
   * verleent toegang tot rapporten over enablement middelen en het leren wegen

De globale hulpmiddelenconsole verleent toegang tot de volgende hulpmiddelen van Gemeenschappen:

* [Sitesjabloonconsole](/help/communities/tools.md#sitetemplatesconsole)

   * communitysjablonen maken en beheren

* [Groep sjablonen](/help/communities/tools.md#grouptemplatesconsole) , console

   * communitygroepssjablonen maken en beheren

* [Community Functions](/help/communities/tools.md#communityfunctionsconsole) console

   * communautaire functies maken en beheren

* [Opslagconfiguratie](/help/communities/tools.md#storageconfiguratonconsole) -console

   * selecteer en vorm de [gemeenschappelijke opslag](/help/communities/working-with-srp.md) voor de plaats

* [Component Guide](/help/communities/components-guide.md)

   * een voorbeeldsite, [Community Components](https://localhost:4502/editor.html/content/community-components/en.html), die een monster van alle onderdelen van de Gemeenschappen met hun standaardconfiguratie en de mogelijkheid biedt om hiermee te experimenteren

## Sjablonen voor communautaire sites {#community-site-templates}

De creatie van de communautaire plaats is gebaseerd op selectie van een malplaatje van de communautaire plaats om een communautaire plaats snel te vestigen die van om het even welke steekproefplaats onafhankelijk is.

Een communitysitesjabloon, dat bestaat uit communityfuncties en communitygroepssjablonen, biedt de structuur voor een communitysite, zoals aanmeldingsgegevens, gebruikersprofielen, berichten, berichten, het menu van de site, zoeken, thema&#39;s en brandingfuncties.

Zie de console [Sjablonen](/help/communities/sites.md)voor sites.

## Communautaire functies {#community-functions}

De kenmerken die van een gemeenschapservaring worden verwacht, zijn bekend. Met AEM-gemeenschappen zijn deze functies beschikbaar als bouwstenen, ook wel bekend als gemeenschapsfuncties.

Community-functies zijn normale AEM-pagina&#39;s die componenten bevatten die zijn samengevoegd tot een functie die eenvoudig kan worden opgenomen in een sjabloon voor een community-site.

Zie de [Community Functions console](/help/communities/functions.md).

## Communautaire groepen en groepssjablonen {#community-groups-and-group-templates}

De functie voor groepen van gemeenschappen is de mogelijkheid voor een subcommunity om dynamisch binnen een community-site te worden gemaakt door geautoriseerde gebruikers en leden van de community uit zowel de auteur- als de publicatieomgeving.

Vanuit de auteursomgeving kunnen communitygroepen (subgemeenschappen) worden gemaakt binnen een bestaande communitysite of worden genest binnen een bestaande groep, als de structuur van de sjabloon de functie [](/help/communities/functions.md#groups-function)Groepen bevat.

Voor het maken van een community-groep moet een communitygroepsjabloon worden geselecteerd die het ontwerp van de pagina(&#39;s) van de community-groep bevat. Wanneer een functie van Groepen aan een malplaatjestructuur wordt toegevoegd, wordt het gevormd om of één groepsmalplaatje te specificeren of een keus van malplaatjes te verstrekken op het tijdstip dat een nieuwe communautaire groep wordt gecreeerd.

Zie ook:

* [Sitegroepen console](/help/communities/groups.md) voor het maken van subgemeenschappen in de ontwerpomgeving
* [De console](/help/communities/tools-groups.md) van de Malplaatjes van de groep voor het creëren van plaatsstructuur voor groepen
* [Aan de slag met AEM-gemeenschappen](/help/communities/getting-started.md) voor zelfstudie voor het snel maken van een gemeenschapssite met geneste groepen

## Community-componenten {#community-components}

De [onderdelen](/help/communities/author-communities.md) van de community waaruit een site van de community is gemaakt, kunnen worden gebruikt om elementen van de Community aan elke AEM-site toe te voegen.

De [Community components guide](/help/communities/components-guide.md) is beschikbaar voor interactieve verkenning van de componenten.

## Soorten Gemeenschappen {#types-of-communities}

### Gemeenschap voor betrokkenheid {#engagement-community}

Een betrokkenheidsgemeenschap is een community-site die klanten aanmoedigt om te informeren, feedback te vragen en klanten in staat te stellen als leden van de community te communiceren.

Functies van een betrokkenheidsgemeenschap kunnen het volgende omvatten:

* aanmelden
* berichten
* forums
* opmerkingen
* beoordelingen
* ratings
* stemmen
* blogs
* groepen
* kalenders
* vertalen
* matiging
* meldingen
* scoring en badges
* analytische rapportage

Ga naar Aan de [slag met AEM-gemeenschappen](/help/communities/getting-started.md)om snel een nieuwe betrokkenheidsgemeenschap te kunnen maken.

### Enablement Community {#enablement-community}

Een enablement-gemeenschap is een community-site met functies voor online leren.

Functies van een machtigingsgemeenschap kunnen zijn:

* alle functies van een [betrokkenheidsgemeenschap](#engagement-community)
* capaciteit om inhoud en het leren middelen aan leden en lidgroepen toe te wijzen
* ondersteunt SCORM-inhoud, zoals quizzen en tests
* bijhouden van toewijzingsgegevens
* toegang tot rapportage en analyses
* de capaciteit om een gesprek over een het leren middel door forums, overseinen, commentaren en classificaties te hebben

Een enablement gemeenschap kan worden gecreeerd wanneer de toe:voegen- [functie Enablement wordt gevormd](/help/communities/enablement.md), die extra vergunning voor gebruik in een productiemilieu vereist. Een plaats van de enablgemeenschap zal de [toewijzingsfunctie](#community-functions)omvatten.

Ga naar Aan de [slag met AEM Communities for Enablement](/help/communities/getting-started-enablement.md)om te ervaren hoe eenvoudig het maken van een nieuwe enablement-gemeenschap is.

## AEM-demoestel {#aem-demo-machine}

De [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) beheert en voert demo&#39;s uit voor AEM [Plaatsen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Activa](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Gemeenschappen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)enForms, die vaak meer opstelling dan eenvoudig een instantie van QuickStart vereisen. De AEM Demo Machine zal extra [infrastructuur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) zoals MongoDB, Solr, MySQL, FFmpeg en e-mailservers installeren.

De AEM-demovernemingsmachine omvat:

* een [grafische gebruikersinterface](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Apache ANT-scripts met configureerbare [eigenschappen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) en [doelen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)

* te installeren pakketten

De AEM-demovernemingssysteem is getest met CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 en AEM 6.4 op Windows, Mac OS en Linux.

Voor AEM Demo Machine is een geldige AEM-licentie vereist.

>[!NOTE]
>
>Bekijk een [video-introductie](https://www.youtube.com/watch?v=zEE_zkR9fVQ&feature=youtu.be) van de AEM Demo-machine (13:26).

## Documentatie AEM-gemeenschappen {#aem-communities-documentation}

* Bezoek [Implementerende gemeenschappen](/help/communities/deploy-communities.md) voor meer informatie over aanbevolen implementaties.
* Ga naar [Communitysites](/help/communities/administer-landing.md) beheren voor meer informatie over het maken van een communitysite, het toevoegen van communitygroepen, het configureren van sjablonen voor communitysites, het modereren van community-inhoud, het beheren van leden, het labelen, meldingen, scoring en badges.
* Bezoek [Ontwikkelingsgemeenschappen](/help/communities/communities.md) voor meer informatie over het sociale-componentframework (SCF) en het aanpassen van onderdelen en functies van Gemeenschappen.
* Bezoek [Authoring Communities Components](/help/communities/author-communities.md) om te leren hoe u auteur kunt maken met en Community-componenten kunt configureren.

