---
title: Communautaire groepen
description: Leer hoe u met de functie Gebruikersgroepen dynamisch een subcommunity binnen een communitysite kunt maken door geautoriseerde gebruikers in Publiceren en Auteur.
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

Deze mogelijkheid is aanwezig wanneer de [group, functie](/help/communities/functions.md#groups-function) aanwezig is in het dialoogvenster [community-site](/help/communities/sites-console.md) structuur.

A [communitygroepsjabloon](/help/communities/tools-groups.md) verstrekt het ontwerp van de communautaire groepspagina wanneer een communautaire groep dynamisch wordt gecreeerd.

Een of meer groepssjablonen worden geselecteerd voor de groepsfunctie wanneer de functie wordt toegevoegd aan de structuur van een gemeenschapssite of aan een sjabloon voor een gemeenschapssite. Deze lijst van groepsmalplaatjes wordt voorgesteld aan het lid of de auteur die dynamisch tot een groep van binnen de communautaire plaats leidt.

## Een nieuwe groep maken {#creating-a-new-group}

Het vermogen om een communautaire groep tot stand te brengen baseert zich op het bestaan van een communautaire plaats die de groepenfunctie omvat, zoals die van [Sjabloon verwijzingssite](/help/communities/sites.md).

De volgende voorbeelden gebruiken de communitysite die is gemaakt op basis van de `Reference Site Template` zoals beschreven in de [Aan de slag met AEM Communities](/help/communities/getting-started.md) zelfstudie.

Dit is de pagina die wordt geladen bij publicatie wanneer de **Groepen** menu-item is geselecteerd:

![nieuwe groep](assets/new-group.png)

Wanneer u **Nieuwe groep** wordt geopend.

Onder de **Instellingen** tabblad geeft u de basisfuncties van de groep op:

![groep-instellingen](assets/group-settings.png)

* **Groepsnaam**

  De titel van de groep die u op de site van de community wilt weergeven. Gebruik geen onderstrepingstekens (_) en trefwoorden zoals bronnen en configuratie in de groepsnaam.

* **Beschrijving**

  Een beschrijving van de groep die op de communitysite moet worden weergegeven.

* **Uitnodigen**

  Een lijst met leden die moeten worden uitgenodigd voor de groep. De vooruit onderzoek verstrekt suggesties van communautaire leden om uit te nodigen.

* **URL-naam groep**

  De naam voor de groepspagina die deel van URL wordt.

* **Groep openen**

  Selecteren `Open Group` geeft aan dat een anonieme sitebezoeker de inhoud kan bekijken en de selectie ervan opheft `Member Only Group`.

* **Groep alleen lid**

  Selecteren `Member Only Group` geeft aan dat alleen leden van de groep de inhoud mogen weergeven en heft de selectie op `Open Group`.

Onder de **Sjabloon** kunt u kiezen uit de lijst met sjablonen voor groepen uit de gebruikersgemeenschap. Deze sjablonen zijn opgegeven wanneer de functie Groepen is opgenomen in de structuur van de site van de community of in een sjabloon voor een community-site.

![groepssjabloon](assets/group-template.png)

Onder de **Afbeelding** kunt u een afbeelding uploaden om deze voor de groep weer te geven op de pagina Groepen van de communautaire site. De standaardstijlpagina wijzigt de afbeelding in 170 x 90 pixels.

![groepsafbeelding](assets/group-image.png)

Door **Groep maken**, worden de pagina&#39;s voor de groep gemaakt op basis van de gekozen sjabloon, wordt een gebruikersgroep gemaakt voor lidmaatschap en wordt de pagina Groepen bijgewerkt om de nieuwe subcommunity weer te geven.

De pagina Groepen met een nieuwe subcommunity met de naam &quot;Focus Group&quot;, waarvoor een afbeeldingsminiatuur is geüpload, ziet er als volgt uit (nog steeds aangemeld als beheerder van een communitygroep):

![groepspagina](assets/group-page.png)

De `Focus Group` Met deze koppeling wordt de pagina Focus Group in de browser geopend, die een eerste weergave heeft op basis van de gekozen sjabloon, en een submenu bevat onder het menu van de hoofdsite van de community:

![open-group-page](assets/open-group-page.png)

### Component Lijst van leden van groep Gemeenschap {#community-group-member-list-component}

De `Community Group Member List` is bedoeld voor gebruik door ontwikkelaars van groepssjablonen.

### Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële elementen van gebruikersgroepen](/help/communities/essentials-groups.md) pagina voor ontwikkelaars.

Voor andere informatie over groepen van gemeenschappen gaat u naar [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md).
