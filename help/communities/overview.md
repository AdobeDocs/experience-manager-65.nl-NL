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

* **Informs** via blogs, vragen en antwoorden en gebeurtenissencalenders,
* while **inzichten ophalen** door forums, commentaren, en andere communautaire inhoud, die vaak als gebruiker-geproduceerde inhoud (UGC) wordt bedoeld.
* Het staat **matiging** door vertrouwde leden in de publicatieomgeving,
* **Sociale aanmelding** met Twitter en Facebook,
* **Inline-omzetting** van communautaire inhoud,
* **Communautaire groepen** van de gepubliceerde website van de gemeenschap,
* **Scores** het toekennen van badges,
* **Bestanden delen**,
* **Meldingen** en **activiteitsstromen**,
* Toestaan **labelen** (@vermeld) andere geregistreerde leden in Gebruiker-Gegenereerde Inhoud, om hun aandacht te vestigen.

De kenmerken van de Gemeenschappen kunnen met behulp van [AEM demo-machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) beschikbaar voor het publiek op GitHub.com of met de nieuwe `We.Retail` referentie-uitvoering.

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

   * Responsief ontwerp: gebruik [Thema&#39;s voor Bootstrap twitters](https://getbootstrap.com)

   * Aanmelden: zelfregistratie, [sociale aanmelding](/help/communities/social-login.md), gebruikersprofielen

      * Meldingen: leden zien gebeurtenissen die voor hen van belang zijn, en door gebruikers gegenereerde inhoud waar ze zijn [@referred](/help/communities/overview.md#mentionssupport).

      * Berichten: leden kunnen berichten verzenden of ontvangen binnen de communitysite.
      * Zoeken: zoekmogelijkheden op de site van de community.
      * Taalomschakeling: mogelijkheid om een taal voor een [meertalige site](/help/sites-administering/translation.md).

      * Beheer: toegang voor geautoriseerde leden tot gematigde en beheerde gebruikers binnen de site van de gemeenschap.

* Hiermee verwijdert u veel ontwerpstappen op paginaniveau:

   * Branding: optionele upload van een bannerafbeelding voor weergave op alle pagina&#39;s van de gemeenschapssite
   * Navigatiemenu: er zijn navigatiekoppelingen beschikbaar voor de functies die zijn opgenomen in de sjabloon voor de communautaire site.

Ga naar [Aan de slag met AEM Communities](/help/communities/getting-started.md).

## Persistentie van communautaire inhoud {#community-content-persistence}

Om de prestaties en synchronisatie van gemeenschapsinhoud te verbeteren, vereist AEM Communities een gemeenschappelijke opslag specifiek voor gebruiker-geproduceerde inhoud (UGC) die tussen alle AEM (auteur en publiceer) instanties wordt gedeeld.

De communautaire inhoud wordt gemakkelijk betreden door de leverancier van het opslagmiddel (SRP), die een laag verstrekt om toegang van de onderliggende topologie te scheiden en een gemeenschappelijke opslag voor UGC steunt.

Ga voor meer informatie over de persistentie en aanbevolen implementaties van community-inhoud naar:

* [Opslag van communautaire inhoud](/help/communities/working-with-srp.md)—bespreekt de beschikbare SRP opslagopties voor UGC.
* [Aanbevolen topologieën](/help/communities/topologies.md)—bespreekt topologieën die op gebruiksgeval en keus SRP worden gebaseerd.
* [Opwaarderen naar AEM 6.5 Gemeenschappen](/help/communities/upgrade.md)—biedt nuttige informatie over UGC bij de overgang naar AEM 6.5.

## Communityconsoles {#communities-consoles}

In de auteursomgeving biedt de globale navigatieconsole toegang tot de [Communityconsole](/help/communities/consoles.md), die het volgende bevat:

* [Sites](/help/communities/sites-console.md) console

   * Site maken
   * Site bewerken
   * Sitebeheer
   * [Communautaire groepen](/help/communities/groups.md) console

* [Moderatie](/help/communities/moderation.md) console

   * Gemeenschappelijke bulkmoderatie UI voor Auteur en Publish milieu&#39;s.
   * Nieuwe filtercriteria.

* [Leden en groepen](/help/communities/members.md) beheerconsoles

   * Hiermee kunt u gebruikers (leden) aan de publicatiezijde maken en beheren vanuit de ontwerpomgeving.
   * Hiermee kunt u leden verbieden.
   * Hiermee kunt u gebruikersgroepen (lidgroepen) aan de serverzijde maken en beheren.

* [Rapporten](/help/communities/reports.md) console

   * Hiermee kunt u rapporten genereren over toewijzingen, posten en weergaven.

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

   * een voorbeeldsite; [Community-componenten](https://localhost:4502/editor.html/content/community-components/en.html) verstrekt een steekproef van alle componenten van Gemeenschappen met hun standaardconfiguratie en de capaciteit om met hen te experimenteren.

## Sjablonen voor community-sites {#community-site-templates}

De creatie van de communautaire plaats is gebaseerd op selectie van een malplaatje van de communautaire plaats om snel een communautaire plaats te vestigen die van om het even welke steekproefplaats onafhankelijk is.

Een communitysitesjabloon, dat bestaat uit communityfuncties en communitygroepssjablonen, biedt de structuur voor een communitysite. Het omvat login, gebruikersprofielen, overseinen, plaatsmenu, onderzoek, thema, en branding eigenschappen.

Zie de [Sitesjabloonconsole](/help/communities/sites.md).

## Communautaire functies {#community-functions}

De kenmerken die van een gemeenschapservaring worden verwacht, zijn bekend. In AEM Communities zijn deze functies beschikbaar als bouwstenen, ook wel bekend als gemeenschapsfuncties.

Community-functies zijn normale AEM pagina&#39;s bevatten onderdelen die zijn samengevoegd tot een functie die gemakkelijk kan worden opgenomen in een sjabloon voor een community-site.

Zie de [Community Functions-console](/help/communities/functions.md).

## Communautaire groepen en groepssjablonen {#community-groups-and-group-templates}

De eigenschap van communautaire groepen is de capaciteit voor een subcommunity om dynamisch binnen een communautaire plaats door erkende gebruikers en communityleden van zowel de auteur als publicatiemilieu&#39;s worden gecreeerd.

Vanuit de auteursomgeving kunnen communitygroepen (subgemeenschappen) worden gemaakt binnen een bestaande communitysite of worden genest binnen een bestaande groep, als de structuur van de sjabloon de [Groepen, functie](/help/communities/functions.md#groups-function).

Voor het maken van een community-groep moet u een community-groepssjabloon selecteren die het ontwerp van de community-groepspagina&#39;s bevat. Wanneer een functie van Groepen aan een malplaatjestructuur wordt toegevoegd, wordt het gevormd om of één groepsmalplaatje te specificeren of een keus van malplaatjes te verstrekken op het tijdstip dat een nieuwe communautaire groep wordt gecreeerd.

Zie ook:

* [Sitegroepen, console](/help/communities/groups.md) voor het maken van subgemeenschappen in de auteursomgeving.
* [Groep sjablonen, console](/help/communities/tools-groups.md) voor het maken van sitestructuren voor groepen.
* [Aan de slag met AEM Communities](/help/communities/getting-started.md) voor zelfstudie waarmee u snel een site van een community kunt maken, met inbegrip van geneste groepen.

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

Ga voor het gemak om snel een betrokkenheidsgemeenschap te maken naar [Aan de slag met AEM Communities](/help/communities/getting-started.md).

## AEM demo-machine {#aem-demo-machine}

De [AEM demo-machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) beheert en voert demo&#39;s voor AEM uit [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Activa](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Gemeenschappen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) en [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), waarvoor vaak meer instellingen nodig zijn dan het starten van een QuickStart-instantie. De AEM demomachemachine stelt extra [infrastructuur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) zoals MongoDB-, Solr-, MySQL-, MPEG- en e-mailservers.

De AEM demomodus omvat:

* A [grafische gebruikersinterface](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-scripts met configureerbare [eigenschappen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) en [streefdoelen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Te installeren pakketten.

De AEM Demo-machine is getest met succes met CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 en AEM 6.4 op Windows, macOS en Linux®.

Voor AEM demo-machine is een geldige AEM vereist.

>[!NOTE]
>
>Een [video-introductie](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) naar de AEM demomachine (13:26).

## AEM Communities-documentatie {#aem-communities-documentation}

* Bezoek [Gemeenschappen inzetten](deploy-communities.md) waar u over geadviseerde plaatsingen kunt leren.
* Bezoek [Communitysites beheren](administer-landing.md) waar u kunt leren over het creëren van een communautaire plaats, het toevoegen van communautaire groepen, het vormen van de malplaatjes van de communautaire plaats, het modereren van communautaire inhoud, het beheren van leden, het etiketteren, berichten, het scoren, en badges.
* Bezoek [Ontwikkelingsgemeenschappen](communities.md) waar u over het sociale componentenkader (SCF) en het aanpassen van de componenten en de eigenschappen van de Gemeenschappen kunt leren.
* Bezoek [Componenten van Gemeenschappen ontwerpen](author-communities.md) waar u kunt leren om met te schrijven en de componenten van de Gemeenschappen te vormen.
