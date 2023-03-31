---
title: AEM Communities - Overzicht
seo-title: AEM Communities Overview
description: Een overzicht van AEM Communities-functies en -instellingen
seo-description: An overview of AEM Communities features and setup
uuid: 14405847-36ae-4958-bdc6-d799ecd05f06
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 44374006-f711-4af8-a1fe-f89164f79581
docset: aem65
exl-id: d6243dff-a067-455c-a326-5f451f225efd
source-git-commit: 9f9f80eb4cb74b687c7fadd41d0f8ea4ee967865
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 0%

---

# AEM Communities - Overzicht {#aem-communities-overview}

Adobe Experience Manager (AEM) Communities biedt de mogelijkheid om snel een lokale community-site te maken die de prestaties verbetert, het sitebeheer verbetert en de conversie van sitebezoekers naar waardevolle leden van de community aanmoedigt.

## Functies van Gemeenschappen {#communities-features}

AEM Communities maakt de ontwikkeling mogelijk van een relatie met bezoekers van de site, die:

* **Informs** via blogs, vragen en antwoorden en gebeurtenissencalenders,
* while **inzichten opdoen** door forums, commentaren, en andere communautaire inhoud, die vaak als gebruiker wordt bedoeld geproduceerde inhoud (UGC).
* Het staat **matiging** door vertrouwde leden in de publicatieomgeving,
* **Sociale aanmelding** met Twitter en Facebook,
* **Inline-omzetting** van communautaire inhoud,
* **Communautaire groepen** van de gepubliceerde website van de gemeenschap,
* **Scores** het toekennen van badges,
* **Bestanden delen**,
* **Meldingen** en **activiteitsstromen**,
* Toestaan **labelen** (@vermeld) andere geregistreerde leden in Door gebruiker gegenereerde inhoud, om hun aandacht te vestigen.

De kenmerken van de Gemeenschappen kunnen worden aangetoond met behulp van de [AEM demo-machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) beschikbaar openbaar op GitHub.com of met de nieuwe Wij.Retail verwijzingsimplementatie.

## Communitysites {#community-sites}

Een communitysite is een AEM site die is gemaakt met een eenvoudige wizard die resulteert in een website met veel algemene functies die vooraf zijn getelegrafeerd naar de site.

De [wizard voor het maken van sites](/help/communities/sites-console.md):

* Elementen van de site samenstellen op basis van de geselecteerde [sjabloon voor community-site](/help/communities/sites.md) dat wil zeggen:

   * gemaakt van [communautaire functies](#community-functions)
   * optioneel [communautaire groepen](#communitygroups) functie

* Gebruikt te configureren instellingen:

   * matiging
   * aanmelden
   * vertalen

* Biedt essentiële functies:

   * Responsief ontwerp: gebruik [Twitter-thema&#39;s voor Bootstrap](https://getbootstrap.com)

   * Aanmelden: zelfregistratie, [sociale aanmelding](/help/communities/social-login.md), gebruikersprofielen

      * Meldingen: leden zien gebeurtenissen die voor hen van belang zijn en door gebruikers gegenereerde inhoud waar zij zijn [@referred](/help/communities/overview.md#mentionssupport).

      * Berichten: leden kunnen berichten verzenden of ontvangen binnen de site van de gemeenschap .
      * Zoeken: de mogelijkheid om te zoeken op de site van de community.
      * Taalomschakeling: de mogelijkheid om een taal te selecteren voor een [meertalige site](/help/sites-administering/translation.md).

      * Beheer: toegang voor geautoriseerde leden tot de gematigde en beheerde gebruikers op de communautaire site .

* Hiermee verwijdert u veel ontwerpstappen op paginaniveau:

   * Branding: optionele upload van een bannerafbeelding voor weergave op alle pagina&#39;s van de gemeenschapssite
   * Navigatiemenu: er zijn navigatiekoppelingen beschikbaar voor de functies die zijn opgenomen in het sjabloon voor de communautaire site .

Ga naar [Aan de slag met AEM Communities](/help/communities/getting-started.md).

## Persistentie van communautaire inhoud {#community-content-persistence}

Om de prestaties en synchronisatie van inhoud van de gebruikersgemeenschap te verbeteren, vereist AEM Communities een gemeenschappelijke opslag specifiek voor gebruiker geproduceerde inhoud (UGC) die tussen alle AEM (auteur en publiceer) instanties wordt gedeeld.

De communautaire inhoud wordt gemakkelijk betreden door de leverancier van het opslagmiddel (SRP), die een laag verstrekt om toegang van de onderliggende topologie te scheiden en een gemeenschappelijke opslag voor UGC steunt.

Ga voor meer informatie over de persistentie en aanbevolen implementaties van community-inhoud naar:

* [Opslag van communautaire inhoud](/help/communities/working-with-srp.md), waarin de beschikbare SRP-opslagopties voor UGC worden besproken.
* [Aanbevolen topologieën](/help/communities/topologies.md), die topologieën bespreekt die op gebruiksgeval en keus SRP worden gebaseerd.
* [Opwaarderen naar AEM 6.5 Gemeenschappen](/help/communities/upgrade.md), die nuttige informatie over UGC verstrekt wanneer het bewegen naar AEM 6.5.

## Communityconsoles {#communities-consoles}

In de auteursomgeving biedt de globale navigatieconsole toegang tot de [Communityconsole](/help/communities/consoles.md), die het volgende bevat:

* [Sites](/help/communities/sites-console.md) console

   * Site maken
   * Site bewerken
   * Sitebeheer
   * [Communautaire groepen](/help/communities/groups.md) console

* [Moderatie](/help/communities/moderation.md) console

   * Algemene bulkmoderatie UI voor auteur en publicatiemilieu&#39;s.
   * Nieuwe filtercriteria.

* [Leden en groepen](/help/communities/members.md) beheerconsoles

   * Biedt de mogelijkheid om gebruikers aan de publicatiezijde (leden) te maken en te beheren vanuit de auteursomgeving.
   * Biedt de mogelijkheid om leden te verbieden.
   * Verstrekt de capaciteit om te creëren en te leiden publiceer-zij gebruikersgroepen (lidgroepen) van het auteursmilieu.

* [Rapporten](/help/communities/reports.md) console

   * Verstrekt de capaciteit om rapporten over taken, posten en meningen te produceren.

De globale hulpmiddelenconsole verleent toegang tot de volgende hulpmiddelen van Gemeenschappen:

* [Sitesjablonen](/help/communities/tools.md#sitetemplatesconsole) console

   * Sjablonen voor communitysites maken en beheren.

* [Groepssjablonen](/help/communities/tools.md#grouptemplatesconsole) console

   * Creëer en beheer communitygroepssjablonen.

* [Communautaire functies](/help/communities/tools.md#communityfunctionsconsole) console

   * Creëer en beheer communityfuncties.

* [Opslagconfiguratie](/help/communities/tools.md#storageconfiguratonconsole) console

   * Selecteer en vorm de [gemeenschappelijk archief](/help/communities/working-with-srp.md) voor de site.

* [Component Guide](/help/communities/components-guide.md)

   * een voorbeeldsite; [Community-componenten](https://localhost:4502/editor.html/content/community-components/en.html), die een steekproef van alle communautaire componenten met hun standaardconfiguratie en de capaciteit verstrekt om met hen te experimenteren.

## Sjablonen voor communautaire sites {#community-site-templates}

De creatie van de communautaire plaats is gebaseerd op selectie van een malplaatje van de communautaire plaats om een communautaire plaats snel te vestigen die van om het even welke steekproefplaats onafhankelijk is.

Een communitysitesjabloon, dat bestaat uit communityfuncties en communitygroepssjablonen, biedt de structuur voor een communitysite, zoals aanmeldingsgegevens, gebruikersprofielen, berichten, berichten, het menu van de site, zoeken, thema&#39;s en brandingfuncties.

Zie de [Sitesjabloonconsole](/help/communities/sites.md).

## Communautaire functies {#community-functions}

De kenmerken die van een gemeenschapservaring worden verwacht, zijn bekend. In AEM Communities zijn deze functies beschikbaar als bouwstenen, ook wel bekend als gemeenschapsfuncties.

Community-functies zijn normale AEM pagina&#39;s bevatten onderdelen die zijn samengevoegd tot een functie die gemakkelijk kan worden opgenomen in een sjabloon voor een community-site.

Zie de [Community Functions-console](/help/communities/functions.md).

## Communautaire groepen en groepssjablonen {#community-groups-and-group-templates}

De functie voor groepen van gemeenschappen is de mogelijkheid voor een subcommunity om dynamisch binnen een community-site te worden gemaakt door geautoriseerde gebruikers en leden van de community uit zowel de auteur- als de publicatieomgeving.

Vanuit de auteursomgeving kunnen communitygroepen (subgemeenschappen) worden gemaakt binnen een bestaande communitysite of worden genest binnen een bestaande groep, als de structuur van de sjabloon de [Groepen, functie](/help/communities/functions.md#groups-function).

Voor het maken van een community-groep moet een communitygroepsjabloon worden geselecteerd die het ontwerp van de pagina(&#39;s) van de community-groep bevat. Wanneer een functie van Groepen aan een malplaatjestructuur wordt toegevoegd, wordt het gevormd om of één groepsmalplaatje te specificeren of een keus van malplaatjes te verstrekken op het tijdstip dat een nieuwe communautaire groep wordt gecreeerd.

Zie ook:

* [Sitegroepen, console](/help/communities/groups.md) voor het creëren van subgemeenschappen in de auteursomgeving.
* [Groep sjablonen, console](/help/communities/tools-groups.md) voor het maken van een sitestructuur voor groepen.
* [Aan de slag met AEM Communities](/help/communities/getting-started.md) voor zelfstudie voor het snel maken van een community-site met geneste groepen.

## Community-componenten {#community-components}

De [communautaire componenten](/help/communities/author-communities.md) Van waaruit een communautaire plaats wordt gebouwd kan worden gebruikt om de eigenschappen van Gemeenschappen aan om het even welke AEM Plaats toe te voegen.

De [Community-componentengids](/help/communities/components-guide.md) is beschikbaar voor interactieve verkenning van de componenten.

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

Ga voor het gemak om snel een nieuwe betrokkenheidsgemeenschap te maken naar [Aan de slag met AEM Communities](/help/communities/getting-started.md).

## AEM demo-machine {#aem-demo-machine}

De [AEM demo-machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) beheert en voert demo&#39;s voor AEM uit [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Activa](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Gemeenschappen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) en [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), waarvoor vaak meer instellingen nodig zijn dan het starten van een QuickStart-instantie. De AEM Demo-machine stelt aanvullende instellingen in [infrastructuur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) zoals MongoDB-, Solr-, MySQL-, MPEG- en e-mailservers.

De AEM demomodus omvat:

* A [grafische gebruikersinterface](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-scripts met configureerbare [eigenschappen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) en [streefdoelen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Te installeren pakketten.

De AEM Demo-machine is met succes getest met CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 en AEM 6.4 op Windows, MacOS en Linux.

Voor AEM demo-machine is een geldige AEM vereist.

>[!NOTE]
>
>Een [video-introductie](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) naar de AEM demomachine (13:26).

## AEM Communities-documentatie {#aem-communities-documentation}

* Bezoek [Gemeenschappen inzetten](deploy-communities.md) voor meer informatie over aanbevolen implementaties.
* Bezoek [Communitysites beheren](administer-landing.md) om over het creëren van een communautaire plaats te leren, toevoegend communautaire groepen, vormend de malplaatjes van de communautaire plaats, het modereren van communautaire inhoud, het beheren van leden, het etiketteren, berichten, het scoren, en badges.
* Bezoek [Ontwikkelingsgemeenschappen](communities.md) voor meer informatie over het raamwerk voor sociale componenten (SCF) en het aanpassen van onderdelen en functies van Gemeenschappen.
* Bezoek [Componenten van Gemeenschappen ontwerpen](author-communities.md) om te leren om met te schrijven en de componenten van de Gemeenschappen te vormen.
