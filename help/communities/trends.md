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

Met de component `Community Activity List` kunt u trending-informatie over posts en weergaven door leden en posts en weergaven van inhoud toevoegen.

In het document wordt beschreven:

* De `Community Activity List`-component toevoegen aan een [communitysite](/help/communities/overview.md#community-sites).

* De montages van de configuratie voor `Community Activity List` component.

### Vereiste {#requirement}

Gegevens voor de `Community Activity List` zijn alleen beschikbaar wanneer Adobe Analytics een licentie heeft en is geconfigureerd voor de communitysite.

Zie [Analyseconfiguratie voor Gemeenschappen-functies](/help/communities/analytics.md).

### Een communautaire activiteitenlijst toevoegen aan een pagina {#adding-a-community-activity-list-to-a-page}

Als u een `Community Activity List`-component wilt toevoegen aan een pagina in de ontwerpmodus, zoekt u de component

* `Communities / Community Activity List`

en sleep het naar de juiste plaats op een pagina.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](/help/communities/basics.md).

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![gemeenschapsactiviteit](assets/community-activity.png)

### Lijst met communautaire activiteiten configureren {#configuring-community-activity-list}

Selecteer de geplaatste `Community Activity List` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![vormen](assets/configure-new.png)

Geef onder het tabblad **Opmerkingen** op of en hoe opmerkingen voor geüploade bestanden worden weergegeven:

![eigenschappen](assets/activity-list-properties.png)

* **Type**

   Geef op of gegevens met betrekking tot leden van de gebruikersgemeenschap of door de gebruiker gegenereerde inhoud (UGC) moeten worden weergegeven.

   Selecteer  vanuit:

   * `Members`
   * `Content`

   De standaardwaarde is `Members`.

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

   De standaardwaarde is `Total`.

* **Contextpad**

   Verstrekt de capaciteit om de activiteit tot een ondergroep van de plaats, zoals een specifieke Blog uit te breiden.
Standaard is dit de hele community-site.

* **Samenvoeging aantal leden**

   Wanneer deze optie is uitgeschakeld, worden alleen de bovenste posts geteld. Als de context bijvoorbeeld de hoofdpagina is (de standaardinstelling), wordt bij een `Activity Type` van `Posts` nooit enige activiteit weergegeven omdat het niet mogelijk is inhoud op de hoofdpagina te plaatsen. Wanneer deze optie is ingeschakeld, worden de tellingen op alle afstammende pagina&#39;s opgenomen.
Standaard is ingeschakeld.

### Voorbeeld van pagina met 4 componenten {#example-page-with-components}

**Top** Visitorsconfig: Type = Leden, Type activiteit = Weergaven

**Top** Contributorsconfig: Type = Leden, Type activiteit = Posten

**Top** Contentconfig: Type = Inhoud, Type activiteit = Weergaven

**Trending** Contentconfig: Type = Inhoud, Type activiteit = Post

![componenten](assets/activity-list-components.png)

