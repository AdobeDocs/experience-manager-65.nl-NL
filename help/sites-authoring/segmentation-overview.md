---
title: Segmentering begrijpen tijdens het maken van een campagne
description: Segmentering is een belangrijke overweging bij het maken van een campagne.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: 61a5875f-ad09-4971-a886-b0d88e0c9967
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization,Integration
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Segmentering begrijpen{#understanding-segmentation}

Segmentering is een belangrijke overweging bij het maken van een campagne. Gewoonlijk moet u segmenten al hebben gedefinieerd voordat u uw campagne start.

De bezoekers van de plaats hebben verschillende belangen en doelstellingen wanneer zij aan een plaats komen. Kennis van deze doelstellingen en het voldoen aan de verwachtingen is een belangrijke succesfactor voor online marketing.

Segmentering helpt dit te bereiken door het volgende te analyseren en te karakteriseren:

* activiteiten op de website
* profiel
* activiteiten op andere websites

De inhoud kan vervolgens worden afgestemd op de behoeften en belangen van de bezoeker, afhankelijk van de segmenten die de bezoeker aanpast.

## Segmentatie gebruiken {#using-segmentation}

De segmenten worden bepaald in [ het Vormen Segmentatie ](/help/sites-administering/campaign-segmentation.md). Ze worden gebruikt om de werkelijke inhoud te sturen die door een specifiek doelpubliek wordt gezien.

## Gesegmenteerde terminologie {#segmentation-terminology}

Bij het bespreken van segmentatie wordt de volgende terminologie gebruikt:

**Bezoeker** - een bezoeker is een persoon die een website bezoekt. Het bezoek van die persoon begint gewoonlijk van een verwijzende pagina, dan gaat op één of meerdere paginameningen op uw eigen website over. Een gedragsprofiel kan worden gemaakt op basis van de details van het bezoek van die persoon.

**Gebruiker** - een gebruiker is een bezoeker die bij de website registreert om een rekeningsprofiel te ontvangen. Om hun profiel te genereren, bieden ze aanvullende identificatie, zoals een e-mailadres en geslacht. Er kan ook aanvullende informatie worden verzameld, zoals activiteiten in de gemeenschap en aankooppatronen, ook hier weer. Op basis van de informatie in het profiel kan een demografisch profiel worden gemaakt.

**Spoor** - een bezit is een kenmerk of een bezit van een bezoeker dat kan worden gebruikt om lidmaatschap in een specifiek segment te bepalen.

**Segment** - een segment is een inzameling van bezoekers die bepaalde eigenschappen delen. Segmenten moeten onderscheidend zijn, met een minimum aan overlapping met andere segmenten.

**de Behavioral Traits van het Gedrag** - De eigenschappen van het Gedrag zijn die op het gedrag van een bezoeker op de website betrekking hebben. Deze omvatten:

* Interesse op uw website, inclusief bezochte pagina&#39;s en aangekochte producten.
* Interesse op de verwijzende website; inclusief gebruikte zoektermen of aangeklikte advertenties.
* Belang op andere sites; bepaald met behulp van hulpmiddelen zoals Spyjax.
* loyaliteit van de bezoeker; duur van het bezoek, frequentie van de bezoeken.

**Demografische Beelden** - Deze zijn geselecteerde bevolkingskenmerken met inbegrip van:

* Leeftijd
* Inkomens
* Familie
* Burgerlijke staat
* Geslacht
* Locatie

**Afgeleide Beetjes** - sommige demografische eigenschappen zijn moeilijk te bepalen zonder registratie, maar kunnen worden afgeleid door gedrag en demografische eigenschappen te combineren.

Bijvoorbeeld, die verwijzende URL (als gedragseigenschap) met demografische gegevens (die van hulpmiddelen zoals [ worden verkregen Google Ad Planner ](https://www.google.com/adplanner/)) combineren staan plaatseigenaars toe om demografische kenmerken van hun bezoekers af te leiden.

**Subsegment** - een segment kan in verscheidene subsegmenten worden onderverdeeld. Dit wordt gedaan door extra eigenschappen te bepalen.

**de Pagina van het Taser** - een teaser pagina wordt geleid aan een specifiek publiek. Het bevat herbruikbare inhoud die in de teasalinea kan worden gebruikt.

**Campagne** - een campagne is een inzameling van laserpagina&#39;s en e-mailmarketing pagina&#39;s, zoals nieuwsbrieven of uitnodigingen. Een campagne wordt doorgaans gedurende een beperkte periode uitgevoerd en wordt vervangen door een andere campagne.

**Paragraaf van het Taser** - dit is een paragraaf die inhoud van een andere pagina afhankelijk van een selectiestrategie trekt. Deze selectiestrategie kan segmenten en campagnes in overweging nemen.

**Lijst** - een lijst wordt gehaald uit een segment van geregistreerde gebruikers. Bijvoorbeeld de locatie die wordt gebruikt om de inhoud van de teasalinea te sturen.

>[!NOTE]
>
>Zie [ Segmentatie ](/help/sites-administering/campaign-segmentation.md) voor verdere informatie over segmenten in Adobe Experience Manager.
