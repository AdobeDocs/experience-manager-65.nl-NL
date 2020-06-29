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
source-git-commit: cf2733ecee5c74b79b85267191fbdf3cbce9c98b
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Badges-console {#badges-console}

## Info Badges {#about-badges}

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

![chlimage_1-123](assets/chlimage_1-123.png)

## Badge maken {#create-badge}

Een badge wordt gemaakt door het uploaden van een voldoende kleine afbeelding (72 dpi met een hoogte tussen 26 en 32 pixels) en het opgeven van een naam. De badge-afbeelding wordt opgeslagen in de opslagplaats in `/libs/settings/community/badging/images` en wordt automatisch gerepliceerd naar de publicatieomgeving.

Als het publicatiemilieu een landbouwbedrijf van uitgevers is, is het noodzakelijk om [gebruikerssynchronisatie](/help/communities/sync.md)te vormen.

![chlimage_1-124](assets/chlimage_1-124.png)

* **Afbeelding uploaden**

   (*Vereist*) Een badge-afbeelding met een aanbevolen grootte van 32 x 32 pixels bij 72 dpi in de JPEG- of PNG-indeling.

* **Naam**

   (*Vereist*) De badge name. Dit is de standaardnaam `Display Name` en de naam van het knooppunt in de repository. Als het knooppunt geen geldige naam voor een opslagplaats `Name` is, wordt het gewijzigd.

* **Weergavenaam**

   (*Optioneel*) De naam die voor de badge in de gebruikersinterface moet worden weergegeven. De standaardinstelling is de ongewijzigde tekst die voor de `Name`code wordt ingevoerd.

* **Beschrijving**

   (*Optioneel*) Een beschrijving van de badge.

## Additional Information {#additional-information}

Zie [Scores en Badges](/help/communities/implementing-scoring.md)voor meer informatie over het instellen van regels voor scoring en badges.

Zie [Ledenconsole](/help/communities/members.md)voor informatie over het beheren van badges voor leden.
