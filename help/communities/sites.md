---
title: Sitesjablonen
description: Leer hoe te om tot de console van de Malplaatjes van de Plaats toegang te hebben om een communautaire plaats tot stand te brengen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 05a944a3-adb1-47b4-b4a5-15bac91c995e
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Sitesjablonen {#site-templates}

De console van de Malplaatjes van de Plaats is gelijkaardig aan de [ console van de Malplaatjes van de Groep ](tools-groups.md), die op functies van belang aan communautaire groepen wordt geconcentreerd.

>[!NOTE]
>
>De consoles voor de verwezenlijking van [ communautaire plaatsen ](sites-console.md), [ communautaire plaatssjablonen ](sites.md), [ communautaire groepsmalplaatjes ](tools-groups.md), en [ communautaire functies ](functions.md) zijn voor gebruik slechts in het auteursmilieu.

## Sitesjabloonconsole {#site-templates-console}

In het milieu van de Auteur, om de console van communautaire plaatsen te bereiken:

* Vanuit globale navigatie: **[!UICONTROL Tools > Communities > Site Templates]**

Deze console toont de malplaatjes waarvan de a [ communautaire plaats ](sites-console.md) kan worden gecreeerd en nieuwe plaatssjablonen om worden gecreeerd toe te laten.

![ plaats-malplaatje ](assets/site-template.png)

## Sitesjabloon maken {#create-site-template}

Selecteer `Create` als u een sitesjabloon wilt gaan maken.

Hiermee wordt het deelvenster Site-editor geopend dat drie subdeelvensters bevat:

### Basisinformatie {#basic-info}

![ plaats-malplaatje-basicinfo ](assets/site-template-basicinfo.png)

In het deelvenster Basisinformatie worden een naam, beschrijving en of de sjabloon is ingeschakeld of uitgeschakeld, geconfigureerd:

* **[!UICONTROL Community Site Template Name]**

  De naam-id van de sjabloon.

* **[!UICONTROL Community Site Template Description]**

  De sjabloonbeschrijving.

* **[!UICONTROL Disabled/Enabled]**

  Een schakeloptie die bepaalt of naar de sjabloon kan worden verwezen.

### Miniatuur {#thumbnail}

![ plaats-duimnagel ](assets/site-thumbnail.png)

(Optioneel) Selecteer het pictogram Afbeelding uploaden om een miniatuur weer te geven met de naam en beschrijving voor de makers van gemeenschapssites.

### Structuur {#structure}

![ plaats-structuur ](assets/site-structure.png)

Als u communityfuncties wilt toevoegen, sleept u van de rechterkant naar links in de volgorde waarin de koppelingen in het sitemenu moeten worden weergegeven. Stijlen worden toegepast op de sjabloon tijdens het maken van de site.

Als u bijvoorbeeld een homepage wilt, sleept u de functie Pagina uit de bibliotheek en zet u de pagina onder de sjabloonbuilder neer. Dit leidt tot het openen van het dialoogvenster voor paginaconfiguratie. Zie de [ functieconsole ](functions.md) voor informatie over de configuratievensters.

U kunt doorgaan met slepen en neerzetten van alle andere communityfuncties die voor een communitysite op basis van deze sjabloon zijn gewenst.

De paginafunctie biedt een lege pagina. Met de functie Groepen kunt u een groepssite (subcommunity) maken binnen de communitysite.

>[!CAUTION]
>
>De functie van Groepen moet *niet de eerste of enige* functie in de plaatsstructuur zijn.
>
>Om het even welke andere functie, zoals de [ paginafunctie ](functions.md#page-function), moet worden omvat en eerst vermeld.

![ plaats-redacteur ](assets/site-editor.png)

### Groepsjablonen voor groepfuncties {#group-templates-for-groups-function}

Wanneer het omvatten van een functie van Groepen in het plaatssjabloon, vereist de configuratie de specificatie van de keuzen van het groepsmalplaatje toegestaan wanneer een nieuwe groep in het publicatiemilieu wordt gecreeerd.

>[!CAUTION]
>
>De functie van Groepen moet *niet de eerste of enige* functie in de plaatsstructuur zijn.

![ plaats-functies ](assets/site-functions.png)

Door twee of meer groepsmalplaatjes te selecteren, wordt een keus verstrekt aan de groepsbeheerder wanneer eigenlijk het creëren van een groep in de gemeenschap.

![ plaats-functie ](assets/site-functions1.png)

## Sitesjabloon bewerken {#edit-site-template}

Wanneer het bekijken van plaatsmalplaatjes in de belangrijkste [ console van de Malplaatjes van de Plaats ](#site-templates-console), is het mogelijk om een bestaand plaatsmalplaatje voor uitgeven te selecteren.

Dit proces verstrekt de zelfde panelen zoals [ creërend een plaatsmalplaatje ](#create-site-template).
