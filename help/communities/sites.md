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

De console van de Malplaatjes van de Plaats is gelijkaardig aan de [&#x200B; console van de Malplaatjes van de Groep &#x200B;](tools-groups.md), die op functies van belang aan communautaire groepen wordt geconcentreerd.

>[!NOTE]
>
>De consoles voor de verwezenlijking van [&#x200B; communautaire plaatsen &#x200B;](sites-console.md), [&#x200B; communautaire plaatssjablonen &#x200B;](sites.md), [&#x200B; communautaire groepsmalplaatjes &#x200B;](tools-groups.md), en [&#x200B; communautaire functies &#x200B;](functions.md) zijn voor gebruik slechts in het auteursmilieu.

## Sitesjabloonconsole {#site-templates-console}

In het milieu van de Auteur, om de console van communautaire plaatsen te bereiken:

* Vanuit globale navigatie: **[!UICONTROL Tools > Communities > Site Templates]**

Deze console toont de malplaatjes waarvan de a [&#x200B; communautaire plaats &#x200B;](sites-console.md) kan worden gecreeerd en nieuwe plaatssjablonen om worden gecreeerd toe te laten.

![&#x200B; plaats-malplaatje &#x200B;](assets/site-template.png)

## Sitesjabloon maken {#create-site-template}

Selecteer `Create` als u een sitesjabloon wilt gaan maken.

Hiermee wordt het deelvenster Site-editor geopend dat drie subdeelvensters bevat:

### Basisinformatie {#basic-info}

![&#x200B; plaats-malplaatje-basicinfo &#x200B;](assets/site-template-basicinfo.png)

In het deelvenster Basisinformatie worden een naam, beschrijving en of de sjabloon is ingeschakeld of uitgeschakeld, geconfigureerd:

* **[!UICONTROL Community Site Template Name]**

  De naam-id van de sjabloon.

* **[!UICONTROL Community Site Template Description]**

  De sjabloonbeschrijving.

* **[!UICONTROL Disabled/Enabled]**

  Een schakeloptie die bepaalt of naar de sjabloon kan worden verwezen.

### Miniatuur {#thumbnail}

![&#x200B; plaats-duimnagel &#x200B;](assets/site-thumbnail.png)

(Optioneel) Selecteer het pictogram Afbeelding uploaden om een miniatuur weer te geven met de naam en beschrijving voor de makers van gemeenschapssites.

### Structuur {#structure}

![&#x200B; plaats-structuur &#x200B;](assets/site-structure.png)

Als u communityfuncties wilt toevoegen, sleept u van de rechterkant naar links in de volgorde waarin de koppelingen in het sitemenu moeten worden weergegeven. Stijlen worden toegepast op de sjabloon tijdens het maken van de site.

Als u bijvoorbeeld een homepage wilt, sleept u de functie Pagina uit de bibliotheek en zet u de pagina onder de sjabloonbuilder neer. Dit leidt tot het openen van het dialoogvenster voor paginaconfiguratie. Zie de [&#x200B; functieconsole &#x200B;](functions.md) voor informatie over de configuratievensters.

U kunt doorgaan met slepen en neerzetten van alle andere communityfuncties die voor een communitysite op basis van deze sjabloon zijn gewenst.

De paginafunctie biedt een lege pagina. Met de functie Groepen kunt u een groepssite (subcommunity) maken binnen de communitysite.

>[!CAUTION]
>
>De functie van Groepen moet *niet de eerste of enige* functie in de plaatsstructuur zijn.
>
>Om het even welke andere functie, zoals de [&#x200B; paginafunctie &#x200B;](functions.md#page-function), moet worden omvat en eerst vermeld.

![&#x200B; plaats-redacteur &#x200B;](assets/site-editor.png)

### Groepsjablonen voor groepfuncties {#group-templates-for-groups-function}

Wanneer het omvatten van een functie van Groepen in het plaatssjabloon, vereist de configuratie de specificatie van de keuzen van het groepsmalplaatje toegestaan wanneer een nieuwe groep in het publicatiemilieu wordt gecreeerd.

>[!CAUTION]
>
>De functie van Groepen moet *niet de eerste of enige* functie in de plaatsstructuur zijn.

![&#x200B; plaats-functies &#x200B;](assets/site-functions.png)

Door twee of meer groepsmalplaatjes te selecteren, wordt een keus verstrekt aan de groepsbeheerder wanneer eigenlijk het creëren van een groep in de gemeenschap.

![&#x200B; plaats-functie &#x200B;](assets/site-functions1.png)

## Sitesjabloon bewerken {#edit-site-template}

Wanneer het bekijken van plaatsmalplaatjes in de belangrijkste [&#x200B; console van de Malplaatjes van de Plaats &#x200B;](#site-templates-console), is het mogelijk om een bestaand plaatsmalplaatje voor uitgeven te selecteren.

Dit proces verstrekt de zelfde panelen zoals [&#x200B; creërend een plaatsmalplaatje &#x200B;](#create-site-template).
