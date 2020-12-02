---
title: Badges-console
seo-title: Badges-console
description: Met de console Gemeenschapsbadges kunt u aangepaste badges toevoegen die kunnen worden weergegeven voor leden die hun geld hebben verdiend (toegekend) of die een specifieke rol in de gemeenschap hebben (toegewezen)
seo-description: Met de console Gemeenschapsbadges kunt u aangepaste badges toevoegen die kunnen worden weergegeven voor leden die hun geld hebben verdiend (toegekend) of die een specifieke rol in de gemeenschap hebben (toegewezen)
uuid: 7103b133-ef3f-47d6-a2dc-4e6ff92e8fed
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 135b3077-5343-4888-858d-de5e9b1d4b04
docset: aem65
translation-type: tm+mt
source-git-commit: 548e19b0fc76ede8685ea938ed871fbdc8c3858f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Badges-console {#badges-console}

## Informatie over Badges {#about-badges}

De console van de Badges van de Gemeenschappen verstrekt de capaciteit om douanebadges toe te voegen die voor een lid kunnen worden getoond wanneer verdiend (toegekend) of wanneer zij een specifieke rol in de gemeenschap (toegewezen) nemen.

### Zichtbaarheid badge {#badge-visibility}

Badges die een lid van de gemeenschap verdient of toegewezen krijgt, worden samen met zijn naam en avatar op de volgende locaties weergegeven:

* Profielen
* [Forums](/help/communities/forum.md)
* [QnA](/help/communities/working-with-qna.md)
* [Leaderboards](/help/communities/enabling-leaderboard.md)
* [Ideatie](/help/communities/ideation-feature.md)

Navigeer in de ontwerpomgeving naar de Badges-console:

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Badges]**

Op deze console worden de badges weergegeven die momenteel beschikbaar zijn en waaruit nieuwe badges kunnen worden toegevoegd.

![badges-homepage](assets/badges-homepage.png)

## Badge {#create-badge} maken

Een badge wordt gemaakt door het uploaden van een voldoende kleine afbeelding (72 dpi met een hoogte tussen 26 en 32 pixels) en het opgeven van een naam. De badge-afbeelding wordt opgeslagen in de opslagplaats op `/libs/settings/community/badging/images` en wordt automatisch gerepliceerd naar de publicatieomgeving.

Als de publicatieomgeving een bedrijf van uitgevers is, is het nodig om [user sync](/help/communities/sync.md) te configureren.

![aanmaken](assets/create-badge.png)

* **Afbeelding uploaden**

   (*Required*) Een afbeelding met een badge met een aanbevolen grootte van 32 x 32 pixels bij 72 dpi in JPEG- of PNG-indeling.

* **Naam**

   (*Required*) De merknaam. Het is de standaard `Display Name` evenals de naam van de repository node. Als `Name` geen geldige naam voor een opslagplaats is, wordt deze gewijzigd.

* **Weergavenaam**

   (*Optioneel*) De naam die moet worden weergegeven voor de badge in de gebruikersinterface. Standaard is de ongewijzigde tekst die voor `Name` wordt ingevoerd.

* **Beschrijving**

   (*Optioneel*) Een beschrijving voor de badge.

## Aanvullende informatie {#additional-information}

Zie [Scores en Badges](/help/communities/implementing-scoring.md) voor meer informatie over het instellen van regels voor scoring en badging.

Zie [Ledenconsole](/help/communities/members.md) voor het beheren van badges voor leden.
