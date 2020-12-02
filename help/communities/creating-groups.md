---
title: Communautaire groepen
seo-title: Communautaire groepen
description: Gebruikersgroepen maken
seo-description: Gebruikersgroepen maken
uuid: c677d23d-5edb-414c-9013-130c88c2ea52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d94708ee-ca6b-420c-9536-6889d752f9de
docset: aem65
translation-type: tm+mt
source-git-commit: 6337a57ea12f1e026f6c754a083307ce018a1c13
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Communautaire groepen {#community-groups}

De eigenschap van communautaire groepen is de capaciteit voor een subcommunity dynamisch om binnen een communautaire plaats door erkende gebruikers (leden van de gemeenschap en auteurs) van de publicatie en auteursmilieu&#39;s worden gecreeerd.

Deze mogelijkheid is aanwezig wanneer de functie [groups](/help/communities/functions.md#groups-function) aanwezig is in de [communitysite](/help/communities/sites-console.md)-structuur.

Een [communitygroepsjabloon](/help/communities/tools-groups.md) biedt het ontwerp van de communitygroeppagina wanneer een community-groep dynamisch wordt gemaakt.

Een of meer groepssjablonen worden geselecteerd voor de groepsfunctie wanneer de functie wordt toegevoegd aan de structuur van een gemeenschapssite of aan een sjabloon voor een gemeenschapssite. Deze lijst van groepsmalplaatjes wordt voorgesteld aan het lid of de auteur die dynamisch tot een nieuwe groep van binnen de communautaire plaats leidt.

## Nieuwe groep maken {#creating-a-new-group}

De capaciteit om een nieuwe communautaire groep tot stand te brengen baseert zich op het bestaan van een communautaire plaats die de groepsfunctie omvat, zoals die van [het Malplaatje van de Plaats van de Verwijzing ](/help/communities/sites.md) wordt gecreeerd.

De volgende voorbeelden gebruiken de communautaire die plaats van `Reference Site Template` wordt gecreeerd zoals die in [Aan de slag met AEM Communities](/help/communities/getting-started.md) wordt beschreven zelfstudie.

Dit is de pagina die bij publiceren laadt wanneer **Groepen** menupunt wordt geselecteerd:

![nieuwe groep](assets/new-group.png)

Als u het pictogram **Nieuwe groep** selecteert, wordt een dialoogvenster voor bewerken geopend.

Onder het **lusje van Montages**, verstrekt u de basiseigenschappen van de groep:

![groep-instellingen](assets/group-settings.png)

* **Groepsnaam**

   De titel van de groep die op de communitysite moet worden weergegeven.

* **Beschrijving**

   Een beschrijving van de groep die op de communitysite moet worden weergegeven.

* **Uitnodigen**

   Een lijst met leden die moeten worden uitgenodigd om deel te nemen aan de groep. Bij het zoeken naar vooraf bepaalde typen worden suggesties van leden van de gemeenschap geleverd die u wilt uitnodigen.

* **URL-naam groep**

   De naam voor de groepspagina die deel van URL wordt.

* **Groep openen**

   Als u `Open Group` selecteert, wordt aangegeven dat een anonieme sitebezoeker de inhoud kan weergeven. De selectie `Member Only Group` wordt opgeheven.

* **Groep alleen lid**

   Als u `Member Only Group` selecteert, wordt alleen aangegeven dat leden van de groep de inhoud kunnen weergeven en wordt `Open Group` uitgeschakeld.

Onder het tabblad **Sjabloon** is de mogelijkheid om
selecteer uit de lijst van communautaire groepsmalplaatjes die werden gespecificeerd toen de groepsfunctie in de structuur van de communautaire plaats of in een malplaatje van de communautaire plaats werd opgenomen.

![groepssjabloon](assets/group-template.png)

Onder het tabblad **Afbeelding** kunt u een afbeelding uploaden die u wilt weergeven voor de groep op de pagina Groepen van de communitysite. De afbeelding wordt op het standaardstijlblad vergroot tot 170 x 90 pixels.

![groepsafbeelding](assets/group-image.png)

Door **Create Groep** knoop te selecteren, worden de pagina&#39;s voor de groep gecreeerd gebaseerd op het gekozen malplaatje, en een gebruikersgroep wordt gecreeerd voor lidmaatschap en de pagina van Groepen zal worden bijgewerkt om de nieuwe subcommunity te tonen.

De pagina Groepen met een nieuwe subcommunity met de naam &quot;Focus Group&quot;, waarvoor een afbeeldingsminiatuur is geüpload, ziet er bijvoorbeeld als volgt uit (nog steeds aangemeld als beheerder van een communitygroep):

![groepspagina](assets/group-page.png)

Als u de koppeling `Focus Group` selecteert, wordt de pagina Focusgroep in de browser geopend. Deze pagina heeft een initiële weergave op basis van de gekozen sjabloon en bevat een submenu onder het menu van de hoofdsite van de community:

![open-group-page](assets/open-group-page.png)

### Component {#community-group-member-list-component} van lijst met leden van communautaire groep

De component `Community Group Member List` is bedoeld voor gebruik door ontwikkelaars van groepssjablonen.

### Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Community Group Essentials](/help/communities/essentials-groups.md) voor ontwikkelaars.

Voor andere informatie met betrekking tot communautaire groepen, bezoek [Beherende Gebruikers en Gebruikersgroepen](/help/communities/users.md).
