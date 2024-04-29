---
title: Badges-console
description: Met de console Gemeenschapsbadges kunt u aangepaste badges toevoegen die kunnen worden weergegeven voor leden die hun geld hebben verdiend (toegekend) of die een specifieke rol in de gemeenschap hebben (toegewezen)
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 50ed9ec4-ff04-4f9d-aefb-0837542a9455
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Badges-console {#badges-console}

## Info Badges {#about-badges}

Met de console Gemeenschapsbadges kunt u aangepaste badges toevoegen die voor een lid kunnen worden weergegeven wanneer het lid wordt verdiend (toegekend) of wanneer het een specifieke rol in de gemeenschap (toegewezen) op zich neemt.

### Zichtbaarheid badge {#badge-visibility}

De badges die een lid van de gemeenschap ontvangt, of toegewezen, verschijnen samen met zijn naam en avatar op de volgende plaatsen:

* Profielen
* [Forums](/help/communities/forum.md)
* [QnA](/help/communities/working-with-qna.md)
* [Leaderboards](/help/communities/enabling-leaderboard.md)
* [Ideatie](/help/communities/ideation-feature.md)

Navigeer in de ontwerpomgeving naar de Badges-console:

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Badges]**

Op deze console worden de badges weergegeven die momenteel beschikbaar zijn en waaruit nieuwe badges kunnen worden toegevoegd.

![badges-homepage](assets/badges-homepage.png)

## Badge maken {#create-badge}

Een badge wordt gemaakt door een voldoende kleine afbeelding (72 dpi met een hoogte tussen 26 en 32 pixels) te uploaden en een naam te geven. De badge-afbeelding wordt opgeslagen in de gegevensopslagruimte op `/libs/settings/community/badging/images` en wordt automatisch gerepliceerd naar de publicatieomgeving.

Als het publicatiemilieu een landbouwbedrijf van uitgevers is, is het noodzakelijk om te vormen [gebruikerssync](/help/communities/sync.md).

![aanmaken](assets/create-badge.png)

* **Afbeelding uploaden**

  (*Vereist*) Een badge-afbeelding met een aanbevolen formaat van 32 x 32 pixels bij 72 dpi in de indeling JPEG of PNG.

* **Naam**

  (*Vereist*) De badge name. Dit is de standaardwaarde `Display Name` en de naam van het knooppunt in de repository. Als de `Name` is geen geldige naam voor een opslagplaats. De naam is gewijzigd.

* **Weergavenaam**

  (*Optioneel*) De naam die voor de badge in de gebruikersinterface moet worden weergegeven. Standaard is de ongewijzigde tekst die is ingevoerd voor de `Name`.

* **Beschrijving**

  (*Optioneel*) Een beschrijving voor de badge.

## Aanvullende informatie {#additional-information}

Voor meer informatie over het instellen van regels voor scoring en badging raadpleegt u [Scores en badges](/help/communities/implementing-scoring.md).

Voor het beheren van badges voor leden raadpleegt u [Ledenconsole](/help/communities/members.md).
