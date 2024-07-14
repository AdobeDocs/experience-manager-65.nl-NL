---
title: Communautaire groepen
description: Leer hoe u met de functie Gebruikersgroepen dynamisch een subcommunity binnen een communitysite kunt maken door geautoriseerde gebruikers in Publish en Auteur.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: edcda6cb-df47-4afe-8a9a-82d8e386fe05
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Communautaire groepen {#community-groups}

De eigenschap van communautaire groepen is de capaciteit voor een subcommunity om dynamisch binnen een communautaire plaats door erkende gebruikers (leden van de gemeenschap en auteurs) van de publicatie en auteursmilieu&#39;s worden gecreeerd.

Deze capaciteit is aanwezig wanneer de [ groepsfunctie ](/help/communities/functions.md#groups-function) in de [ communautaire plaats ](/help/communities/sites-console.md) structuur aanwezig is.

A [ malplaatje van de communautaire groep ](/help/communities/tools-groups.md) verstrekt het ontwerp van de pagina van de communautaire groep wanneer een communautaire groep dynamisch wordt gecreeerd.

Een of meer groepssjablonen worden geselecteerd voor de groepsfunctie wanneer de functie wordt toegevoegd aan de structuur van een gemeenschapssite of aan een sjabloon voor een gemeenschapssite. Deze lijst van groepsmalplaatjes wordt voorgesteld aan het lid of de auteur die dynamisch tot een groep van binnen de communautaire plaats leidt.

## Een nieuwe groep maken {#creating-a-new-group}

De capaciteit om een communautaire groep tot stand te brengen baseert zich op het bestaan van een communautaire plaats die de groepsfunctie omvat, zoals die van het [ Malplaatje van de Plaats van de Verwijzing ](/help/communities/sites.md) wordt gecreeerd.

De voorbeelden die volgen gebruiken de communautaire plaats die van `Reference Site Template` wordt gecreeerd zoals die in [ wordt beschreven Begonnen het Worden met AEM Communities ](/help/communities/getting-started.md) leerprogramma.

Dit is de pagina die op publiceert laadt wanneer het **1} menupunt van Groepen {wordt geselecteerd:**

![ nieuw-groep ](assets/new-group.png)

Wanneer u het **Nieuwe pictogram van de Groep** selecteert, geeft een dialoogdoos uit opent omhoog.

Onder het **lusje van Montages**, verstrekt u de basiseigenschappen van de groep:

![ groep-montages ](assets/group-settings.png)

* **de Naam van de Groep**

  De titel van de groep die u op de site van de community wilt weergeven. Gebruik geen onderstrepingstekens (_) en trefwoorden zoals bronnen en configuratie in de groepsnaam.

* **Beschrijving**

  Een beschrijving van de groep die op de communitysite moet worden weergegeven.

* **Uitnodigen**

  Een lijst met leden die moeten worden uitgenodigd voor de groep. De vooruit onderzoek verstrekt suggesties van communautaire leden om uit te nodigen.

* **de Naam van Groep URL**

  De naam voor de groepspagina die deel van URL wordt.

* **Open Groep**

  Als u `Open Group` selecteert, wordt aangegeven dat een anonieme sitebezoeker de inhoud kan bekijken en wordt de selectie van `Member Only Group` opgeheven.

* **Groep van het Lid slechts**

  Als u `Member Only Group` selecteert, wordt aangegeven dat alleen leden van de groep de inhoud mogen weergeven en wordt de selectie van `Open Group` opgeheven.

Onder het **Malplaatje** lusje, kunt u uit de lijst van communautaire groepsmalplaatjes selecteren. Deze sjablonen zijn opgegeven wanneer de functie Groepen is opgenomen in de structuur van de site van de community of in een sjabloon voor een community-site.

![ groep-malplaatje ](assets/group-template.png)

Onder het **lusje van het Beeld**, kunt u een beeld uploaden om voor de groep op de pagina van de Groepen van de communautaire plaats te tonen. De standaardstijlpagina wijzigt de afbeelding in 170 x 90 pixels.

![ groep-beeld ](assets/group-image.png)

Door **te selecteren creeer Groep**, worden de pagina&#39;s voor de groep gecreeerd gebaseerd op het gekozen malplaatje, en een gebruikersgroep wordt gecreeerd voor lidmaatschap en de pagina van Groepen wordt bijgewerkt om nieuwe subcommunity te tonen.

De pagina Groepen met een nieuwe subcommunity met de naam &quot;Focus Group&quot;, waarvoor een afbeeldingsminiatuur is geüpload, ziet er als volgt uit (nog steeds aangemeld als beheerder van een communitygroep):

![ groep-pagina ](assets/group-page.png)

Als u de koppeling `Focus Group` selecteert, wordt de pagina Focus Group in de browser geopend. Deze pagina heeft een initiële weergave op basis van de gekozen sjabloon en bevat een submenu onder het menu van de hoofdsite van de community:

![ open-groep-pagina ](assets/open-group-page.png)

### Component Lijst van leden van groep Gemeenschap {#community-group-member-list-component}

De component `Community Group Member List` is bedoeld voor gebruik door ontwikkelaars van groepssjablonen.

### Aanvullende informatie {#additional-information}

Meer informatie kan op de ](/help/communities/essentials-groups.md) pagina van de Hoofdzaak van de Groep van de Gemeenschap [ voor ontwikkelaars worden gevonden.

Voor andere informatie met betrekking tot communautaire groepen, bezoek [ het Leiden Gebruikers en de Groepen van de Gebruiker ](/help/communities/users.md).
