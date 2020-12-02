---
title: Groepssjablonen
seo-title: Groepssjablonen
description: Hoe te om tot de console van de Malplaatjes van de Groep toegang te hebben
seo-description: Hoe te om tot de console van de Malplaatjes van de Groep toegang te hebben
uuid: 4cf20c91-32b0-4051-a98d-44e4eb50a231
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e9bfbbce-93fc-455c-a2f7-4ee44e63c03f
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---


# Groepssjablonen {#group-templates}

De console van de Malplaatjes van de Groep is gelijkaardig aan [Sitesjablonen](/help/communities/sites.md) console. Beide zijn blauwdrukken voor een set vooraf bekabelde pagina&#39;s en functies die een gemeenschapssite vormen. Het verschil is dat een plaatsmalplaatje voor de belangrijkste gemeenschap is en een groepsmalplaatje voor een communautaire groep, een subgemeenschap die binnen de belangrijkste gemeenschap wordt genesteld.

Een community-groep wordt opgenomen in een sitesjabloon door de functie [Groepen](/help/communities/functions.md#groups-function) (die niet de eerste of enige functie in de sjabloon mag zijn) op te nemen.

Vanaf Communities [feature pack 1](/help/communities/deploy-communities.md#latestfeaturepack), is het mogelijk om groepen te nesten door de functie Groepen op te nemen in een groepssjabloon.

Wanneer een actie wordt ondernomen om een nieuwe communautaire groep tot stand te brengen, wordt het malplaatje (de structuur) van de groep geselecteerd. De selectie hangt van af hoe de functie van Groepen toen toegevoegd aan het plaats of groepsmalplaatje werd gevormd.

>[!NOTE]
>
>De consoles voor het maken van [communitysites](/help/communities/sites-console.md), [communitysitesjablonen](/help/communities/sites.md), [communitygroepssjablonen](/help/communities/tools-groups.md) en [communityfuncties](/help/communities/functions.md) zijn alleen bedoeld voor gebruik in de auteursomgeving.

## Console {#group-templates-console} voor groepssjablonen

Om de console van groepsmalplaatjes in het milieu van de Auteur te bereiken AEM:

* **Gereedschappen selecteren | Gemeenschappen | Groepsjablonen,** van globale navigatie.

Deze console toont de malplaatjes waarvan een [communityplaats](/help/communities/sites-console.md) kan worden gecreeerd en nieuwe groepsmalplaatjes om worden gecreeerd toe.

![Template voor communautaire groepen](assets/groups-template.png)

## Groepssjabloon maken {#create-group-template}

Selecteer `Create` om een nieuwe groepssjabloon te gaan maken.

Hiermee wordt het deelvenster Site-editor weergegeven met drie subdeelvensters:

### Basisinformatie {#basic-info}

![site-basic-info](assets/site-basic-info.png)

In het deelvenster Basisinformatie worden een naam, beschrijving en of de sjabloon is ingeschakeld of uitgeschakeld, geconfigureerd:

* **Nieuwe naam groepssjabloon**

   De naam-id van de sjabloon.

* **Beschrijving**

   De sjabloonbeschrijving.

* **Uitgeschakeld/Ingeschakeld**

   Een schakeloptie die bepaalt of naar de sjabloon kan worden verwezen.

#### Miniatuur {#thumbnail}

![siteminiatuur](assets/site-thumbnail.png)

(Optioneel) Selecteer het pictogram Afbeelding uploaden om een miniatuur met de naam en beschrijving weer te geven aan makers van gemeenschapssites.

#### Structuur {#structure}

>[!CAUTION]
>
>Als het werken met AEM 6.1 Gemeenschappen FP4 of vroeger, voeg geen groepsfunctie aan een groepsmalplaatje toe.
>
>De functie Geneste groepen is beschikbaar vanaf de Gemeenschappen [FP1](/help/communities/communities.md#latestfeaturepack).
>
>Het is nog steeds niet toegestaan een functie Groepen toe te voegen als de eerste of enige functie in een sjabloon.

![Sjablooneditor groeperen](assets/template-editor.png)

Als u communityfuncties wilt toevoegen, sleept u van de rechterkant naar links in de volgorde waarin de koppelingen in het sitemenu moeten worden weergegeven. Stijlen worden toegepast op de sjabloon tijdens het maken van de site.

Als u bijvoorbeeld een forum wilt, sleept u de forumfunctie uit de bibliotheek en zet u de functie neer onder de sjabloonbuilder. Dit zal in de dialoog van de forumconfiguratie resulteren die. Zie [functies console](/help/communities/functions.md) voor informatie over de configuratievensters.

Ga verder met slepen en neerzetten van andere communityfuncties die gewenst zijn voor een subcommunity-site (groep) die op deze sjabloon is gebaseerd.

![sleepfuncties](assets/dragfunctions.png)

Nadat alle gewenste functies in het sjabloonbuildergebied zijn neergezet en geconfigureerd, selecteert u **Opslaan** in de rechterbovenhoek.

## Groepssjabloon bewerken {#edit-group-template}

Wanneer het bekijken van communautaire groepen in de belangrijkste [console van de Malplaatjes van de Groep](#group-templates-console), is het mogelijk om een bestaand groepsmalplaatje voor uitgeven te selecteren.

Het bewerken van een groepssjabloon heeft geen invloed op communitysites die al van de sjabloon zijn gemaakt. In plaats daarvan kunt u direct [de structuur van een communitysite](/help/communities/sites-console.md#modify-structure) bewerken.

Dit proces verstrekt de zelfde panelen zoals [creërend een groepsmalplaatje](#create-group-template).
