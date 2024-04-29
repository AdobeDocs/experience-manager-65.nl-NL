---
title: Groepssjablonen
description: Leer hoe te om tot de console van de Malplaatjes van de Groep voor een reeks vooraf telegrafeerde pagina's en eigenschappen toegang te hebben die een communautaire plaats vormen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: aed2c3f2-1b5e-4065-8cec-433abb738ef5
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---

# Groepssjablonen {#group-templates}

De console van de Malplaatjes van de Groep is gelijkaardig aan [Sitesjablonen](/help/communities/sites.md) console. Beide zijn blauwdrukken voor een set vooraf bekabelde pagina&#39;s en functies die een gemeenschapssite vormen. Het verschil is dat een plaatsmalplaatje voor de belangrijkste gemeenschap is en een groepsmalplaatje voor een communautaire groep, een subcommunity die binnen de belangrijkste gemeenschap wordt genesteld.

Een community-groep is in een sitesjabloon opgenomen door de [Groepen, functie](/help/communities/functions.md#groups-function) (dit mag niet de eerste of enige functie in de sjabloon zijn).

Vanaf Gemeenschappen [functiepakket 1](/help/communities/deploy-communities.md#latestfeaturepack), is het mogelijk om groepen te nesten door de functie Groepen binnen een groepsmalplaatje te omvatten.

Zodra een actie wordt ondernomen om een communautaire groep tot stand te brengen, wordt het malplaatje van de groep (structuur) geselecteerd. De selectie hangt van af hoe de functie van Groepen toen toegevoegd aan het plaats of groepsmalplaatje werd gevormd.

>[!NOTE]
>
>De consoles voor het creëren van [communitysites](/help/communities/sites-console.md), [communitysjablonen](/help/communities/sites.md), [communitygroepsjablonen](/help/communities/tools-groups.md), en [communautaire functies](/help/communities/functions.md) zijn alleen bestemd voor gebruik in de ontwerpomgeving.

## Groep sjablonen {#group-templates-console}

Om de console van groepsmalplaatjes in het milieu van de Auteur van de AEM te bereiken:

* Selecteren **Gereedschappen | Gemeenschappen | Groepssjablonen,** van globale navigatie.

Deze console toont de malplaatjes waarvan een [community-site](/help/communities/sites-console.md) kunnen worden gemaakt en kunnen nieuwe groepssjablonen worden gemaakt.

![Sjabloon voor communautaire groepen](assets/groups-template.png)

## Groepssjabloon maken {#create-group-template}

Als u een groepssjabloon wilt gaan maken, selecteert u `Create`.

Zo wordt het deelvenster Site-editor weergegeven, dat drie subdeelvensters bevat:

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

Als u bijvoorbeeld een forum wilt, sleept u de forumfunctie uit de bibliotheek en zet deze onder de sjabloonbuilder neer. Dit resulteert in de dialoog van de forumconfiguratie die opent. Zie de [functies console](/help/communities/functions.md) voor informatie over de configuratievensters.

Ga verder met slepen en neerzetten van andere communityfuncties die gewenst zijn voor een subcommunity-site (groep) op basis van deze sjabloon.

![sleepfuncties](assets/dragfunctions.png)

Zodra alle gewenste functies in het gebied van de malplaatjebouwer zijn gelaten vallen en gevormd, uitgezocht **Opslaan** in de rechterbovenhoek.

## Groepssjabloon bewerken {#edit-group-template}

Bij het weergeven van groepen van gemeenschappen in de hoofdmap [Groep sjablonen, console](#group-templates-console), is het mogelijk een bestaande groepssjabloon te selecteren om te bewerken.

Het bewerken van een groepssjabloon heeft geen invloed op communitysites die al van de sjabloon zijn gemaakt. Het is mogelijk rechtstreeks [een communitysite bewerken](/help/communities/sites-console.md#modify-structure)In plaats daarvan de structuur.

Dit proces biedt dezelfde deelvensters als [een groepssjabloon maken](#create-group-template).
