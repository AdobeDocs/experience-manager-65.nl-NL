---
title: Sitesjablonen
seo-title: Sitesjablonen
description: Hoe te om tot de console van de Malplaatjes van de Plaats toegang te hebben
seo-description: Hoe te om tot de console van de Malplaatjes van de Plaats toegang te hebben
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# Sitesjablonen {#site-templates}

De console van de Malplaatjes van de Plaats is zeer gelijkaardig aan [de console van de Malplaatjes van de Groep ](tools-groups.md), die op functies van belang voor communautaire groepen wordt geconcentreerd.

>[!NOTE]
>
>De consoles voor het maken van [communitysites](sites-console.md), [communitysitesjablonen](sites.md), [communitygroepssjablonen](tools-groups.md) en [communityfuncties](functions.md) zijn alleen bedoeld voor gebruik in de auteursomgeving.

## Sitesjabloonconsole {#site-templates-console}

In het auteursmilieu, om de console van communautaire plaatsen te bereiken:

* Vanuit globale navigatie: **[!UICONTROL Tools > Communities > Site Templates]**

Deze console toont de malplaatjes waarvan een [communityplaats](sites-console.md) kan worden gecreeerd en nieuwe plaatssjablonen om worden gecreeerd toe te staan.

![site-sjabloon](assets/site-template.png)

## Sitjabloon maken {#create-site-template}

Selecteer `Create` om een nieuwe sitesjabloon te gaan maken.

Hiermee wordt het deelvenster Site-editor weergegeven met drie subdeelvensters:

### Basisinformatie {#basic-info}

![site-template-basicinfo](assets/site-template-basicinfo.png)

In het deelvenster Basisinformatie worden een naam, beschrijving en of de sjabloon is ingeschakeld of uitgeschakeld, geconfigureerd:

* **[!UICONTROL Community Site Template Name]**

   De naam-id van de sjabloon.

* **[!UICONTROL Community Site Template Description]**

   De sjabloonbeschrijving.

* **[!UICONTROL Disabled/Enabled]**

   Een schakeloptie die bepaalt of naar de sjabloon kan worden verwezen.

### Miniatuur {#thumbnail}

![siteminiatuur](assets/site-thumbnail.png)

(Optioneel) Selecteer het pictogram Afbeelding uploaden om een miniatuur met de naam en beschrijving weer te geven aan makers van gemeenschapssites.

### Structuur {#structure}

![sitestructuur](assets/site-structure.png)

Als u communityfuncties wilt toevoegen, sleept u van de rechterkant naar links in de volgorde waarin de koppelingen in het sitemenu moeten worden weergegeven. Stijlen worden toegepast op de sjabloon tijdens het maken van de site.

Als u bijvoorbeeld een homepage wilt, sleept u de functie Pagina uit de bibliotheek en zet u de pagina onder de sjabloonbuilder neer. Hierdoor wordt het dialoogvenster voor paginaconfiguratie geopend. Zie [functies console](functions.md) voor informatie over de configuratievensters.

U kunt doorgaan met slepen en neerzetten van alle andere communityfuncties die voor een communitysite op basis van deze sjabloon zijn gewenst.

De paginafunctie biedt een lege pagina. De groepsfunctie biedt de mogelijkheid om een groepssite (subcommunity) binnen de communitysite te maken.

>[!CAUTION]
>
>De groepsfunctie moet *niet* eerst of de enige functie *in de sitestructuur zijn.*
>
>Elke andere functie, zoals de [paginafunctie](functions.md#page-function), moet worden opgenomen en als eerste worden vermeld.

![site-editor](assets/site-editor.png)

### Groepsjablonen voor groepsfuncties {#group-templates-for-groups-function}

Wanneer het omvatten van een groepsfunctie in het plaatssjabloon, vereist de configuratie de specificatie van de keuzen van het groepsmalplaatje toegestaan wanneer een nieuwe groep in het publicatiemilieu wordt gecreeerd.

>[!CAUTION]
>
>De functie Groepen moet *niet* eerst zijn *noch de enige functie* in de sitestructuur.

![locatiefuncties](assets/site-functions.png)

Door twee of meer groepsmalplaatjes te selecteren, wordt een keus verstrekt aan de groepsbeheerder wanneer eigenlijk het creëren van een nieuwe groep in de gemeenschap.

![plaatsfunctie](assets/site-functions1.png)

## Sitesjabloon bewerken {#edit-site-template}

Als u sitesjablonen weergeeft in de hoofdconsole [Sitesjablonen](#site-templates-console), is het mogelijk een bestaande sitesjabloon te selecteren om te bewerken.

Dit proces biedt dezelfde deelvensters als [het maken van een sitesjabloon](#create-site-template).
