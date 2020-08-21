---
title: Activiteitendensen
seo-title: Activiteitendensen
description: Een component Community Activity List aan een pagina toevoegen
seo-description: Een component Community Activity List aan een pagina toevoegen
uuid: 316aabf7-01a5-46da-be59-70c206eb6a3d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 4a0debdd-acb9-4646-80bb-fec66fae4088
docset: aem65
translation-type: tm+mt
source-git-commit: c190d5f223c85f6c49fea1391d8a3d2baff20192
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 1%

---


# Activiteitendensen {#activity-trends}

## Inleiding {#introduction}

De `Community Activity List` component biedt de mogelijkheid om trending information betreffende posten en weergaven door leden toe te voegen, alsook publicaties en weergaven van inhoud.

In het document wordt beschreven:

* De `Community Activity List` component toevoegen aan een [communitysite](/help/communities/overview.md#community-sites).

* De montages van de configuratie voor de `Community Activity List` component.

### Vereiste {#requirement}

Gegevens voor de `Community Activity List` website zijn alleen beschikbaar wanneer Adobe Analytics een licentie heeft en geconfigureerd voor de communitysite.

Zie [Analytics Configuration for Communities Features](/help/communities/analytics.md).

### Een communautaire activiteitenlijst toevoegen aan een pagina {#adding-a-community-activity-list-to-a-page}

Als u een `Community Activity List` component aan een pagina wilt toevoegen in de ontwerpmodus, zoekt u de component

* `Communities / Community Activity List`

en sleep het naar de juiste plaats op een pagina.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![gemeenschapsactiviteit](assets/community-activity.png)

### Lijst met communautaire activiteiten configureren  {#configuring-community-activity-list}

Selecteer de geplaatste `Community Activity List` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![vormen](assets/configure-new.png)

Geef op het tabblad **Opmerkingen** op of en hoe opmerkingen voor geüploade bestanden worden weergegeven:

![eigenschappen](assets/activity-list-properties.png)

* **Type**

   Geef op of gegevens met betrekking tot leden van de gebruikersgemeenschap of door de gebruiker gegenereerde inhoud (UGC) moeten worden weergegeven.

   Selecteer  vanuit:

   * `Members`
   * `Content`

   Standaard is dit `Members`.

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

   Standaard is dit `Total`.

* **Contextpad**

   Verstrekt de capaciteit om de activiteit tot een ondergroep van de plaats, zoals een specifieke Blog uit te breiden.
Standaard is dit de hele community-site.

* **Samenvoeging aantal leden**

   Wanneer deze optie is uitgeschakeld, worden alleen de bovenste posts geteld. Als de context bijvoorbeeld de hoofdpagina is (de standaardinstelling), `Activity Type` `Posts` wordt bij een van deze gebeurtenissen nooit enige activiteit weergegeven, omdat het niet mogelijk is inhoud naar de hoofdpagina te posten. Wanneer deze optie is ingeschakeld, worden de tellingen op alle afstammende pagina&#39;s opgenomen.
Standaard is ingeschakeld.

### Voorbeeldpagina met 4 componenten {#example-page-with-components}

**Configuratie van bovenste bezoekers** : Type = Leden, Type activiteit = Weergaven

**Configuratie van belangrijkste contribuanten** : Type = Leden, Type activiteit = Posten

**Configuratie van de bovenste inhoud** : Type = Inhoud, Type activiteit = Weergaven

**Trending Content** config: Type = Inhoud, Type activiteit = Post

![componenten](assets/activity-list-components.png)

