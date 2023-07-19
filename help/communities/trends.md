---
title: Activiteitendensen
seo-title: Activity Trends
description: Een component Community Activity List aan een pagina toevoegen
seo-description: Adding a Community Activity List component to a page
uuid: 316aabf7-01a5-46da-be59-70c206eb6a3d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 4a0debdd-acb9-4646-80bb-fec66fae4088
docset: aem65
exl-id: 2a4297e4-2d88-4fa6-8fea-3fea06753605
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 1%

---

# Activiteitendensen {#activity-trends}

## Inleiding {#introduction}

De `Community Activity List` biedt de mogelijkheid om trendinformatie toe te voegen over posten en weergaven door leden, alsmede over posten en weergaven van inhoud.

In het document wordt beschreven:

* Het toevoegen van `Community Activity List` component aan een [community-site](/help/communities/overview.md#community-sites).

* De montages van de configuratie voor de `Community Activity List` component.

### Vereiste {#requirement}

Gegevens voor de `Community Activity List` is alleen beschikbaar als Adobe Analytics een licentie heeft en geconfigureerd voor de community-site.

Zie [Analytische configuratie voor functies van Gemeenschappen](/help/communities/analytics.md).

### Een communautaire activiteitenlijst toevoegen aan een pagina {#adding-a-community-activity-list-to-a-page}

Als u een `Community Activity List` naar een pagina in de modus Schrijver, zoek de component

* `Communities / Community Activity List`

en sleep het naar de juiste plaats op een pagina.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![gemeenschapsactiviteit](assets/community-activity.png)

### Lijst met communautaire activiteiten configureren  {#configuring-community-activity-list}

Selecteer de geplaatste `Community Activity List` te openen en de component te selecteren `Configure` wordt het dialoogvenster Bewerken geopend.

![vormen](assets/configure-new.png)

Onder de **Opmerkingen** , geeft u op of en hoe opmerkingen voor geüploade bestanden worden weergegeven:

![eigenschappen](assets/activity-list-properties.png)

* **Type**

  Geef op of gegevens met betrekking tot leden van de gebruikersgemeenschap of door de gebruiker gegenereerde inhoud (UGC) moeten worden weergegeven.

  Selecteer  vanuit:

   * `Members`
   * `Content`

  Standaard is `Members`.

* **Weergavetitel**

  Een beschrijvende titel die boven de gegevens wordt weergegeven, zoals `Trending Content`.
Standaard is geen titel.

* **Aantal weergeven**

  Het aantal aan te bieden items.
De standaardwaarde is 10.

* **Type activiteit**

  Selecteer een van de volgende opties:

   * `Views`(paginabezoeken)
   * `Posts`(maken van UGC)
   * `Follows`
   * `Likes`

  Standaard zijn weergaven.

* **Tijdsperiode**

  Selecteer een van de volgende opties:

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

  Standaard is `Total`.

* **Contextpad**

  Verstrekt de capaciteit om de activiteit tot een ondergroep van de plaats, zoals een specifieke Blog uit te breiden.
Standaard is dit de hele community-site.

* **Samenvoeging aantal leden**

  Wanneer deze optie is uitgeschakeld, worden alleen de bovenste posts geteld. Als de context bijvoorbeeld de hoofdpagina is (de standaardinstelling), `Activity Type` van `Posts` geen activiteit tonen omdat inhoud niet op de hoofdpagina kan worden geplaatst. Wanneer deze optie is ingeschakeld, worden de tellingen op alle afstammende pagina&#39;s opgenomen.
Standaard is ingeschakeld.

### Voorbeeldpagina met 4 componenten {#example-page-with-components}

**Topbezoekers** config: Type = Leden, Type activiteit = Weergaven

**Belangrijkste bijdragers** config: Type = Leden, Type activiteit = Posten

**Bovenste inhoud** config: Type = Inhoud, Type activiteit = Weergaven

**Trend Content** config: Type = Inhoud, Type activiteit = Post

![componenten](assets/activity-list-components.png)
