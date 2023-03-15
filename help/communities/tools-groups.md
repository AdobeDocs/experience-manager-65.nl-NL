---
title: Groepssjablonen
seo-title: Group Templates
description: Hoe te om tot de console van de Malplaatjes van de Groep toegang te hebben
seo-description: How to access the Group Templates console
uuid: 4cf20c91-32b0-4051-a98d-44e4eb50a231
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e9bfbbce-93fc-455c-a2f7-4ee44e63c03f
docset: aem65
role: Admin
exl-id: aed2c3f2-1b5e-4065-8cec-433abb738ef5
source-git-commit: ed11891c27910154df1bfec6225aecd8a9245bff
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Groepssjablonen {#group-templates}

De console van de Malplaatjes van de Groep is gelijkaardig aan [Sitesjablonen](/help/communities/sites.md) console. Beide zijn blauwdrukken voor een set vooraf bekabelde pagina&#39;s en functies die een gemeenschapssite vormen. Het verschil is dat een plaatsmalplaatje voor de belangrijkste gemeenschap is en een groepsmalplaatje voor een communautaire groep, een subgemeenschap die binnen de belangrijkste gemeenschap wordt genesteld.

Een community-groep is in een sitesjabloon opgenomen door de [Groepen, functie](/help/communities/functions.md#groups-function) (dit mag niet de eerste of enige functie in de sjabloon zijn).

Vanaf Gemeenschappen [functiepakket 1](/help/communities/deploy-communities.md#latestfeaturepack), is het mogelijk om groepen te nesten door de functie Groepen binnen een groepsmalplaatje te omvatten.

Wanneer een actie wordt ondernomen om een nieuwe communautaire groep tot stand te brengen, wordt het malplaatje (de structuur) van de groep geselecteerd. De selectie hangt van af hoe de functie van Groepen toen toegevoegd aan het plaats of groepsmalplaatje werd gevormd.

>[!NOTE]
>
>De consoles voor het creëren van [communitysites](/help/communities/sites-console.md), [communitysjablonen](/help/communities/sites.md), [communitygroepsjablonen](/help/communities/tools-groups.md) en [communautaire functies](/help/communities/functions.md) zijn alleen bestemd voor gebruik in de ontwerpomgeving.

## Groep sjablonen {#group-templates-console}

Om de console van groepsmalplaatjes in het milieu van de Auteur te bereiken AEM:

* Selecteren **Gereedschappen | Gemeenschappen | Groepssjablonen,** van globale navigatie.

Deze console toont de malplaatjes waarvan een [community-site](/help/communities/sites-console.md) kunnen worden gemaakt en kunnen nieuwe groepssjablonen worden gemaakt.

![Template voor communautaire groepen](assets/groups-template.png)

## Groepssjabloon maken {#create-group-template}

Selecteer `Create`.

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
>De functie Geneste groepen is beschikbaar vanaf Gemeenschappen [FP1](/help/communities/communities.md#latestfeaturepack).
>
>Het is nog steeds niet toegestaan een functie Groepen toe te voegen als de eerste of enige functie in een sjabloon.

![Sjablooneditor groeperen](assets/template-editor.png)

Als u communityfuncties wilt toevoegen, sleept u van de rechterkant naar links in de volgorde waarin de koppelingen in het sitemenu moeten worden weergegeven. Stijlen worden toegepast op de sjabloon tijdens het maken van de site.

Als u bijvoorbeeld een forum wilt, sleept u de forumfunctie uit de bibliotheek en zet u de functie neer onder de sjabloonbuilder. Dit zal in de dialoog van de forumconfiguratie resulteren die. Zie de [functies console](/help/communities/functions.md) voor informatie over de configuratievensters.

Ga verder met slepen en neerzetten van andere communityfuncties die gewenst zijn voor een subcommunity-site (groep) die op deze sjabloon is gebaseerd.

![sleepfuncties](assets/dragfunctions.png)

Zodra alle gewenste functies in het gebied van de malplaatjebouwer zijn gelaten vallen en gevormd, uitgezocht **Opslaan** in de rechterbovenhoek.

## Groepssjabloon bewerken {#edit-group-template}

Bij het weergeven van groepen van gemeenschappen in de hoofdmap [Groep sjablonen, console](#group-templates-console), is het mogelijk een bestaande groepssjabloon te selecteren om te bewerken.

Het bewerken van een groepssjabloon heeft geen invloed op communitysites die al van de sjabloon zijn gemaakt. Het is mogelijk rechtstreeks [een communitysite bewerken](/help/communities/sites-console.md#modify-structure)In plaats daarvan de structuur.

Dit proces biedt dezelfde deelvensters als [een groepssjabloon maken](#create-group-template).
