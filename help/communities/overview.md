---
title: AEM Communities - Overzicht
seo-title: AEM Communities - Overzicht
description: Een overzicht van AEM Communities-functies en -instellingen
seo-description: Een overzicht van AEM Communities-functies en -instellingen
uuid: 14405847-36ae-4958-bdc6-d799ecd05f06
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 44374006-f711-4af8-a1fe-f89164f79581
docset: aem65
translation-type: tm+mt
source-git-commit: 4533fa42fa3fa9f157d5ca8fee1251005b1d587e
workflow-type: tm+mt
source-wordcount: '1446'
ht-degree: 0%

---


# AEM Communities-overzicht {#aem-communities-overview}

Adobe Experience Manager (AEM) Communities biedt de mogelijkheid om snel een lokale community-site te maken die de prestaties verbetert, het sitebeheer verbetert en de conversie van sitebezoekers naar waardevolle leden van de community aanmoedigt.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Functies {#communities-features} van Gemeenschappen

AEM Communities maakt de ontwikkeling mogelijk van een relatie met bezoekers van de site, die:

* **** Informsthrough blogs, vragen en antwoorden, en gebeurtenissencalenders,
* Terwijl **inzichten** door forums, commentaren, en andere communautaire inhoud, vaak bedoeld als gebruiker geproduceerde inhoud (UGC).
* Het staat **moderatie** door vertrouwde op leden in toe publiceren milieu,
* **Social** Loginwith Twitter and Facebook,
* **Inline** vertaling van communautaire inhoud,
* **oprichting van communautaire groepen** op basis van de gepubliceerde communautaire site;
* **** Scoringto toekenningsbadges;
* **Bestanden delen**,
* **** meldingen en  **activiteitsstromen**;
* Hiermee staat u toe dat andere geregistreerde leden in Door gebruiker gegenereerde inhoud **taggen** (@vermeld) hun aandacht trekken.
* Ondersteunt **toetsenbordnavigatie** op componenten van enablement (bijvoorbeeld Catalog and Course Play, Assignment, File Library).

De eigenschappen van gemeenschappen kunnen worden aangetoond gebruikend [AEM demovermachine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) openbaar op GitHub.com of met de nieuwe Wij.Retail verwijzingsimplementatie beschikbaar.

## Community-sites {#community-sites}

Een communitysite is een AEM site die is gemaakt met een eenvoudige wizard die resulteert in een website met veel algemene functies die vooraf zijn getelegrafeerd naar de site.

De wizard [Site maken](/help/communities/sites-console.md):

* Verzamelt kenmerken van de site op basis van de geselecteerde [communitysjabloon](/help/communities/sites.md) die is:

   * gebouwd uit [communityfuncties](#community-functions)
   * optionele [community groups](#communitygroups)-functie

* Gebruikt te configureren instellingen:

   * matiging
   * aanmelden
   * vertalen

* Biedt essentiële functies:

   * Responsief ontwerp: gebruikt [Twitter-Bootstrap-thema](https://getbootstrap.com)

   * Aanmelden: zelfregistratie, [sociale aanmelding](/help/communities/social-login.md), gebruikersprofielen

      * Meldingen:
leden zien gebeurtenissen die voor hen relevant zijn, en door de gebruiker gegenereerde inhoud waar ze [@genoemd](/help/communities/overview.md#mentionssupport) zijn.

      * Berichten: leden kunnen berichten verzenden of ontvangen binnen de site van de gemeenschap .
      * Zoeken: de mogelijkheid om te zoeken op de site van de community.
      * Taalomschakeling: de mogelijkheid om een taal te selecteren voor een [meertalige site](/help/sites-administering/translation.md).

      * Beheer: toegang voor geautoriseerde leden tot de gematigde en beheerde gebruikers op de communautaire site .

* Hiermee verwijdert u veel ontwerpstappen op paginaniveau:

   * Branding: optionele upload van een bannerafbeelding voor weergave op alle pagina&#39;s van de gemeenschapssite
   * Navigatiemenu: er zijn navigatiekoppelingen beschikbaar voor de functies die zijn opgenomen in het sjabloon voor de communautaire site .

Als u snel een nieuwe communitysite wilt maken, gaat u naar [Aan de slag met AEM Communities](/help/communities/getting-started.md).

## Persistentie voor communautaire inhoud {#community-content-persistence}

Om de prestaties en synchronisatie van inhoud van de gebruikersgemeenschap te verbeteren, vereist AEM Communities een gemeenschappelijke opslag specifiek voor gebruiker geproduceerde inhoud (UGC) die tussen alle AEM (auteur en publiceer) instanties wordt gedeeld.

De communautaire inhoud wordt gemakkelijk betreden door de leverancier van het opslagmiddel (SRP), die een laag verstrekt om toegang van de onderliggende topologie te scheiden en een gemeenschappelijke opslag voor UGC steunt.

Ga voor meer informatie over de persistentie en aanbevolen implementaties van community-inhoud naar:

* [Community Content Storage](/help/communities/working-with-srp.md), waarin de beschikbare SRP-opslagopties voor UGC worden besproken.
* [De geadviseerde Topologieën](/help/communities/topologies.md), die topologieën bespreekt die op gebruiksgeval en keus SRP worden gebaseerd.
* [Bijwerken naar AEM 6.5-gemeenschappen](/help/communities/upgrade.md), die nuttige informatie verschaffen over UGC bij de overgang naar AEM 6.5.

## Communityconsoles {#communities-consoles}

In de auteursomgeving, verleent de globale navigatieconsole toegang tot [Communities console](/help/communities/consoles.md), die bevat:

* [](/help/communities/sites-console.md) Sitesconsole

   * Site maken
   * Site bewerken
   * Sitebeheer
   * [Community ](/help/communities/groups.md) Groupsconsole

* [](/help/communities/moderation.md) Moderationconsole

   * Algemene bulkmoderatie UI voor auteur en publicatiemilieu&#39;s.
   * Nieuwe filtercriteria.

* [Leden en ](/help/communities/members.md) groepsbeheerconsoles

   * Biedt de mogelijkheid om gebruikers aan de publicatiezijde (leden) te maken en te beheren vanuit de auteursomgeving.
   * Biedt de mogelijkheid om leden te verbieden.
   * Verstrekt de capaciteit om te creëren en te leiden publiceer-zij gebruikersgroepen (lidgroepen) van het auteursmilieu.

* [](/help/communities/reports.md) Rapportenconsole

   * Verstrekt de capaciteit om rapporten over taken, posten en meningen te produceren.

* [](/help/communities/resources.md) ResourceConsole

   * Verstrekt de capaciteit om enablement middelen en het leren wegen tot stand te brengen.
   * Verleent toegang tot rapporten over enablement middelen en het leren wegen.

De globale hulpmiddelenconsole verleent toegang tot de volgende hulpmiddelen van Gemeenschappen:

* [Site ](/help/communities/tools.md#sitetemplatesconsole) Templatesconsole

   * Sjablonen voor communitysites maken en beheren.

* [Group ](/help/communities/tools.md#grouptemplatesconsole) Templatesconsole

   * Creëer en beheer communitygroepssjablonen.

* [Community ](/help/communities/tools.md#communityfunctionsconsole) Functionsconsole

   * Creëer en beheer communityfuncties.

* [Storage ](/help/communities/tools.md#storageconfiguratonconsole) Configuration-console

   * Selecteer en vorm [common store](/help/communities/working-with-srp.md) voor de plaats.

* [Component Guide](/help/communities/components-guide.md)

   * Een voorbeeldsite, [Community Components](https://localhost:4502/editor.html/content/community-components/en.html), die een voorbeeld biedt van alle onderdelen van de Gemeenschappen met hun standaardconfiguratie en de mogelijkheid ermee te experimenteren.

## Sjablonen voor communautaire sites {#community-site-templates}

De creatie van de communautaire plaats is gebaseerd op selectie van een malplaatje van de communautaire plaats om een communautaire plaats snel te vestigen die van om het even welke steekproefplaats onafhankelijk is.

Een communitysitesjabloon, dat bestaat uit communityfuncties en communitygroepssjablonen, biedt de structuur voor een communitysite, zoals aanmeldingsgegevens, gebruikersprofielen, berichten, berichten, het menu van de site, zoeken, thema&#39;s en brandingfuncties.

Zie de [Sitesjabloonconsole](/help/communities/sites.md).

## Community-functies {#community-functions}

De kenmerken die van een gemeenschapservaring worden verwacht, zijn bekend. In AEM Communities zijn deze functies beschikbaar als bouwstenen, ook wel bekend als gemeenschapsfuncties.

Community-functies zijn normale AEM pagina&#39;s bevatten onderdelen die zijn samengevoegd tot een functie die gemakkelijk kan worden opgenomen in een sjabloon voor een community-site.

Zie [Community Functions console](/help/communities/functions.md).

## Communautaire groepen en groepssjablonen {#community-groups-and-group-templates}

De functie voor groepen van gemeenschappen is de mogelijkheid voor een subcommunity om dynamisch binnen een community-site te worden gemaakt door geautoriseerde gebruikers en leden van de community uit zowel de auteur- als de publicatieomgeving.

Vanuit de auteursomgeving kunnen communitygroepen (subgemeenschappen) worden gemaakt binnen een bestaande communitysite of worden genest binnen een bestaande groep, als de structuur van de sjabloon de functie [Groepen](/help/communities/functions.md#groups-function) bevat.

Voor het maken van een community-groep moet een communitygroepsjabloon worden geselecteerd die het ontwerp van de pagina(&#39;s) van de community-groep bevat. Wanneer een functie van Groepen aan een malplaatjestructuur wordt toegevoegd, wordt het gevormd om of één groepsmalplaatje te specificeren of een keus van malplaatjes te verstrekken op het tijdstip dat een nieuwe communautaire groep wordt gecreeerd.

Zie ook:

* [Sitegroepen ](/help/communities/groups.md) console voor het maken van subgemeenschappen in de auteursomgeving.
* [Groepeer sjabloonconsole ](/help/communities/tools-groups.md) voor het maken van sitestructuur voor groepen.
* [Aan de slag met AEM ](/help/communities/getting-started.md) gemeenschappen voor zelfstudie voor het snel maken van een gemeenschapssite met geneste groepen.

## Community-componenten {#community-components}

De [community-componenten](/help/communities/author-communities.md) waaruit een community-site is gemaakt, kunnen worden gebruikt om communautaire functies toe te voegen aan elke AEM site.

De [communitycomponentengids](/help/communities/components-guide.md) is beschikbaar voor interactieve exploratie van de componenten.

## Soorten gemeenschappen {#types-of-communities}

### Betrokkenheidsgemeenschap {#engagement-community}

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

Als u het gemak wilt ervaren om snel een nieuwe betrokkenheidscommunity te maken, gaat u naar [Aan de slag met AEM Communities](/help/communities/getting-started.md).

### Community {#enablement-community} inschakelen

Een enablement-gemeenschap is een community-site met functies voor online leren.

Functies van een machtigingsgemeenschap kunnen zijn:

* Alle functies van een [betrokkenheidscommunity](#engagement-community).
* de mogelijkheid om inhoud en leren toe te wijzen. middelen voor leden en leden.
* Ondersteunt SCORM-inhoud, zoals quizzen en tests.
* Tracering van de voltooiing van de taken.
* Toegang tot rapportage en analyses.
* De capaciteit om een gesprek over een het leren middel door forums, overseinen, commentaren en classificaties te hebben.

Een enablement gemeenschap kan worden gecreeerd wanneer [add-on van Enablement wordt gevormd](/help/communities/enablement.md), die extra vergunning voor gebruik in een productiemilieu vereist. Een plaats van de enablgemeenschap zal [toewijzingsfunctie](#community-functions) omvatten.

Als u wilt ervaren hoe eenvoudig het maken van een nieuwe enablement-community is, gaat u naar [Aan de slag met AEM Communities for Enablement](/help/communities/getting-started-enablement.md).

## AEM demomodus {#aem-demo-machine}

De [AEM demomachine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) beheert en voert demo&#39;s uit voor AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) en [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), die vaak meer opstelling dan eenvoudig vereisen QuickStart-instantie. De AEM demomachine zal extra [infrastructuur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) zoals MongoDB, Solr, MySQL, MPEG en e-mailservers installeren.

De AEM demomodus omvat:

* A [grafische gebruikersinterface](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-scripts met configureerbare [eigenschappen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) en [doelen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Te installeren pakketten.

De AEM Demo-machine is getest met succes met CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 en AEM 6.4 op Windows, Mac OS en Linux.

Voor AEM demo-machine is een geldige AEM vereist.

>[!NOTE]
>
>Bekijk een [video inleiding](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) aan de AEM machine van de Demo (13:26).

## AEM Communities-documentatie {#aem-communities-documentation}

* Bezoek [Gemeenschappen implementeren](deploy-communities.md) voor meer informatie over aanbevolen implementaties.
* Bezoek [Communitysites beheren](administer-landing.md) voor meer informatie over het maken van een communitysite, het toevoegen van communitygroepen, het configureren van sjablonen voor communitysites, het modereren van community-inhoud, het beheren van leden, het labelen, meldingen, scoring en badges.
* Bezoek [Developing Communities](communities.md) voor meer informatie over het SCF (Social Component Framework) en het aanpassen van onderdelen en functies van Gemeenschappen.
* Bezoek [Authoring Communities Components](author-communities.md) voor meer informatie over het schrijven en configureren van Community-componenten.

