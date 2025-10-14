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

De console van de Malplaatjes van de Groep is gelijkaardig aan de [&#x200B; console van de Malplaatjes van de Plaats &#x200B;](/help/communities/sites.md). Beide zijn blauwdrukken voor een set vooraf bekabelde pagina&#39;s en functies die een gemeenschapssite vormen. Het verschil is dat een plaatsmalplaatje voor de belangrijkste gemeenschap is en een groepsmalplaatje voor een communautaire groep, een subcommunity die binnen de belangrijkste gemeenschap wordt genesteld.

Een communautaire groep wordt opgenomen in een plaatsmalplaatje door de [&#x200B; functie van Groepen &#x200B;](/help/communities/functions.md#groups-function) (die niet eerste noch slechts functie in het malplaatje kan zijn) te omvatten.

Vanaf de Gemeenschappen [&#x200B; eigenschappak 1 &#x200B;](/help/communities/deploy-communities.md#latestfeaturepack), is het mogelijk om groepen te nesten door de functie van Groepen binnen een groepsmalplaatje te omvatten.

Zodra een actie wordt ondernomen om een communautaire groep tot stand te brengen, wordt het malplaatje van de groep (structuur) geselecteerd. De selectie hangt van af hoe de functie van Groepen toen toegevoegd aan het plaats of groepsmalplaatje werd gevormd.

>[!NOTE]
>
>De consoles voor de verwezenlijking van [&#x200B; communautaire plaatsen &#x200B;](/help/communities/sites-console.md), [&#x200B; communautaire plaatssjablonen &#x200B;](/help/communities/sites.md), [&#x200B; communautaire groepsmalplaatjes &#x200B;](/help/communities/tools-groups.md), en [&#x200B; communautaire functies &#x200B;](/help/communities/functions.md) zijn voor gebruik slechts in het auteursmilieu.

## Groep sjablonen {#group-templates-console}

Om de console van groepsmalplaatjes in het milieu van de Auteur van de AEM te bereiken:

* Selecteer **Hulpmiddelen | Gemeenschappen | De Malplaatjes van de groep,** van globale navigatie.

Deze console toont de malplaatjes waarvan de plaats van de a [&#x200B; gemeenschap &#x200B;](/help/communities/sites-console.md) kan worden gecreeerd en nieuwe groepsmalplaatjes om worden gecreeerd toestaat.

![&#x200B; Communautaire groepsmalplaatje &#x200B;](assets/groups-template.png)

## Groepssjabloon maken {#create-group-template}

Selecteer `Create` als u een groepssjabloon wilt gaan maken.

Zo wordt het deelvenster Site-editor weergegeven, dat drie subdeelvensters bevat:

### Basisinformatie {#basic-info}

![&#x200B; plaats-basis-info &#x200B;](assets/site-basic-info.png)

In het deelvenster Basisinformatie worden een naam, beschrijving en of de sjabloon is ingeschakeld of uitgeschakeld, geconfigureerd:

* **Nieuwe Naam van het Malplaatje van de Groep**

  De naam-id van de sjabloon.

* **Beschrijving**

  De sjabloonbeschrijving.

* **Gehandicapten/Toegelaten**

  Een schakeloptie die bepaalt of naar de sjabloon kan worden verwezen.

#### Miniatuur {#thumbnail}

![&#x200B; plaats-duimnagel &#x200B;](assets/site-thumbnail.png)

(Optioneel) Selecteer het pictogram Afbeelding uploaden om een miniatuur met de naam en beschrijving weer te geven aan makers van gemeenschapssites.

#### Structuur {#structure}

>[!CAUTION]
>
>Als het werken met AEM 6.1 Gemeenschappen FP4 of vroeger, voeg geen groepsfunctie aan een groepsmalplaatje toe.
>
>De genestelde groepeneigenschap is beschikbaar vanaf de Gemeenschappen [&#x200B; FP1 &#x200B;](/help/communities/communities.md#latestfeaturepack).
>
>Het is nog steeds niet toegestaan een functie Groepen toe te voegen als de eerste of enige functie in een sjabloon.

![&#x200B; de redacteur van het malplaatje van de Groep &#x200B;](assets/template-editor.png)

Als u communityfuncties wilt toevoegen, sleept u van de rechterkant naar links in de volgorde waarin de koppelingen in het sitemenu moeten worden weergegeven. Stijlen worden toegepast op de sjabloon tijdens het maken van de site.

Als u bijvoorbeeld een forum wilt, sleept u de forumfunctie uit de bibliotheek en zet deze onder de sjabloonbuilder neer. Dit resulteert in de dialoog van de forumconfiguratie die opent. Zie de [&#x200B; functieconsole &#x200B;](/help/communities/functions.md) voor informatie over de configuratievensters.

Ga verder met slepen en neerzetten van andere communityfuncties die gewenst zijn voor een subcommunity-site (groep) op basis van deze sjabloon.

![&#x200B; belemmeringsfuncties &#x200B;](assets/dragfunctions.png)

Zodra alle gewenste functies in het gebied van de malplaatjebouwer en gevormd zijn gelaten vallen, uitgezocht **sparen** in de hogere juiste hoek.

## Groepssjabloon bewerken {#edit-group-template}

Wanneer het bekijken van communautaire groepen in de belangrijkste [&#x200B; console van de Malplaatjes van de Groep &#x200B;](#group-templates-console), is het mogelijk om een bestaand groepsmalplaatje voor uit te geven te selecteren.

Het bewerken van een groepssjabloon heeft geen invloed op communitysites die al van de sjabloon zijn gemaakt. Het is mogelijk om direct [&#x200B; de structuur van een communautaire plaats &#x200B;](/help/communities/sites-console.md#modify-structure) in plaats daarvan uit te geven.

Dit proces verstrekt de zelfde panelen zoals [&#x200B; creërend een groepsmalplaatje &#x200B;](#create-group-template).
